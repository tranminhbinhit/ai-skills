# Domain Model

## 1. Overview
Document này mô tả domain model - các entities, relationships và business logic của hệ thống.

**Last Updated**: [Date]  
**Related**: [Links to architecture docs]

---

## 2. Domain Overview

### 2.1 Bounded Contexts
[Nếu sử dụng Domain-Driven Design]

**Context 1: User Management**
- Entities: User, Role, Permission
- Purpose: Handle authentication, authorization

**Context 2: Transaction Processing**
- Entities: Transaction, Account, Payment
- Purpose: Handle business transactions

---

## 3. Core Entities

### 3.1 Entity: User
**Description**: Represents system users

**Attributes**:
| Attribute | Type | Required | Default | Validation |
|-----------|------|----------|---------|------------|
| id | UUID | Yes | auto | - |
| email | String | Yes | - | Valid email format |
| passwordHash | String | Yes | - | Bcrypt hash |
| firstName | String | Yes | - | Max 100 chars |
| lastName | String | Yes | - | Max 100 chars |
| status | Enum | Yes | 'active' | active, inactive, suspended |
| createdAt | DateTime | Yes | now() | - |
| updatedAt | DateTime | Yes | now() | - |

**Relationships**:
- Has many: Transaction
- Has many: Session
- Belongs to many: Role (through UserRole)

**Business Rules**:
- Email must be unique
- Cannot delete user with active transactions
- Password must meet complexity requirements

**Methods/Behaviors**:
```typescript
class User {
  validatePassword(password: string): boolean
  hasPermission(permission: string): boolean
  deactivate(): void
  resetPassword(): string
}
```

---

### 3.2 Entity: Transaction
**Description**: Represents financial transactions

**Attributes**:
| Attribute | Type | Required | Default | Validation |
|-----------|------|----------|---------|------------|
| id | UUID | Yes | auto | - |
| userId | UUID | Yes | - | Foreign key to User |
| amount | Decimal(10,2) | Yes | - | > 0 |
| currency | String | Yes | 'USD' | ISO 4217 code |
| type | Enum | Yes | - | debit, credit |
| status | Enum | Yes | 'pending' | pending, completed, failed |
| description | Text | No | null | Max 500 chars |
| createdAt | DateTime | Yes | now() | - |
| completedAt | DateTime | No | null | - |

**Relationships**:
- Belongs to: User
- Has one: PaymentMethod

**Business Rules**:
- Amount must be positive
- Cannot modify completed transactions
- Failed transactions can be retried max 3 times

**State Machine**:
```
pending → processing → completed
   ↓           ↓
failed ← ── ←  ↓
```

---

### 3.3 Entity: [Other Entity]
[Repeat structure above for each entity]

---

## 4. Value Objects

### 4.1 Value Object: Money
**Description**: Represents monetary value with currency

```typescript
class Money {
  constructor(
    public readonly amount: number,
    public readonly currency: string
  ) {}
  
  add(other: Money): Money {
    if (this.currency !== other.currency) {
      throw new Error('Currency mismatch');
    }
    return new Money(this.amount + other.amount, this.currency);
  }
  
  multiply(factor: number): Money {
    return new Money(this.amount * factor, this.currency);
  }
}
```

---

### 4.2 Value Object: Email
**Description**: Validated email address

```typescript
class Email {
  constructor(private readonly value: string) {
    this.validate();
  }
  
  private validate(): void {
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!emailRegex.test(this.value)) {
      throw new Error('Invalid email format');
    }
  }
  
  toString(): string {
    return this.value;
  }
}
```

---

## 5. Aggregates

### 5.1 Aggregate Root: Order
**Description**: Order aggregate containing order items

**Root Entity**: Order  
**Child Entities**: OrderItem  
**Invariants**:
- Order total must equal sum of order items
- Cannot add items to completed order

```typescript
class Order {
  private items: OrderItem[] = [];
  private status: OrderStatus;
  
  addItem(item: OrderItem): void {
    if (this.status === 'completed') {
      throw new Error('Cannot modify completed order');
    }
    this.items.push(item);
  }
  
  calculateTotal(): Money {
    return this.items.reduce(
      (sum, item) => sum.add(item.getSubtotal()),
      new Money(0, 'USD')
    );
  }
}
```

---

## 6. Entity Relationship Diagram

```
User (1) ──── (N) Transaction
  │
  └──── (N) Session
  │
  └──── (M):(N) Role
        
Transaction (N) ──── (1) PaymentMethod

Order (1) ──── (N) OrderItem
```

**Legend**:
- (1): One
- (N): Many
- (M):(N): Many-to-Many

---

## 7. Domain Services

### 7.1 Service: PaymentProcessor
**Responsibility**: Coordinate payment processing across entities

**Methods**:
```typescript
class PaymentProcessor {
  processPayment(transaction: Transaction): Promise<PaymentResult> {
    // 1. Validate transaction
    // 2. Call payment gateway
    // 3. Update transaction status
    // 4. Create receipt
  }
  
  refundPayment(transactionId: UUID): Promise<RefundResult> {
    // Refund logic
  }
}
```

---

### 7.2 Service: UserAuthentication
**Responsibility**: Handle authentication logic

```typescript
class UserAuthentication {
  authenticate(email: Email, password: string): Promise<User> {
    // Authentication logic
  }
  
  createSession(user: User): Session {
    // Session creation
  }
}
```

---

## 8. Domain Events

### 8.1 Event: UserRegistered
**Triggered when**: New user completes registration

**Payload**:
```typescript
interface UserRegisteredEvent {
  userId: UUID;
  email: string;
  registeredAt: DateTime;
}
```

**Handlers**:
- Send welcome email
- Create default user preferences
- Log audit event

---

### 8.2 Event: TransactionCompleted
**Triggered when**: Transaction reaches completed status

**Payload**:
```typescript
interface TransactionCompletedEvent {
  transactionId: UUID;
  userId: UUID;
  amount: Money;
  completedAt: DateTime;
}
```

**Handlers**:
- Send confirmation email
- Update account balance
- Trigger analytics event

---

## 9. Business Rules & Invariants

### Global Invariants
1. **Rule 1**: User email must be unique across the system
2. **Rule 2**: Transaction amount must always be positive
3. **Rule 3**: Completed transactions are immutable

### Context-Specific Rules

**User Management Context**:
- Users must have at least one role
- Cannot delete admin if it's the last admin

**Transaction Context**:
- Total transaction amount per day cannot exceed limit
- Refund amount cannot exceed original transaction amount

---

## 10. Domain Model Glossary

| Term | Definition |
|------|------------|
| Aggregate | Cluster of domain objects treated as a single unit |
| Entity | Object with unique identity |
| Value Object | Immutable object without identity |
| Domain Service | Operation that doesn't belong to any entity |
| Domain Event | Something that happened in the domain |

---

## Change Log
| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [Date] | AI + Team | Initial domain model |
| 1.1 | [Date] | [Name] | Added Order aggregate |
