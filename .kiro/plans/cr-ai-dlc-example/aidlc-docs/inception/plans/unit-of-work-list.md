# Unit of Work List

## 1. Overview
Document này liệt kê tất cả các Units of Work (UoW) cho dự án. Mỗi UoW là một đơn vị công việc nhỏ có thể hoàn thành trong một Bolt (vài giờ đến vài ngày).

**Generated from Requirements**: [Links to requirement docs]  
**Last Updated**: [Date]

---

## 2. UoW Summary

| UoW ID | Title | Priority | Dependencies | Estimated Effort | Status |
|--------|-------|----------|--------------|-----------------|---------|
| UoW-001 | Setup project infrastructure | Must Have | None | 4h | Not Started |
| UoW-002 | Implement user authentication | Must Have | UoW-001 | 8h | Not Started |
| UoW-003 | Create data models | Must Have | UoW-001 | 6h | Not Started |
| UoW-004 | Build API endpoints | Must Have | UoW-002, UoW-003 | 12h | Not Started |

---

## 3. Bolt Planning

### Bolt 1: Foundation (Day 1)
**Goal**: Setup infrastructure và core architecture

**UoWs**:
- UoW-001: Setup project infrastructure
- UoW-003: Create data models

**Total Effort**: 10 hours  
**Team**: 2 developers

---

### Bolt 2: Authentication (Day 2)
**Goal**: Implement user management

**UoWs**:
- UoW-002: Implement user authentication

**Total Effort**: 8 hours  
**Team**: 1 developer

---

### Bolt 3: Core Features (Day 3-4)
**Goal**: Build main functionality

**UoWs**:
- UoW-004: Build API endpoints
- UoW-005: Create frontend components

**Total Effort**: 20 hours  
**Team**: 2 developers

---

## 4. Detailed UoW Descriptions

### UoW-001: Setup Project Infrastructure
**Priority**: Must Have  
**Estimated Effort**: 4 hours

**Objective**:
Setup development environment, CI/CD, and project structure

**Tasks**:
- [ ] Initialize Git repository
- [ ] Setup monorepo structure (if applicable)
- [ ] Configure linting & formatting (ESLint, Prettier)
- [ ] Setup testing framework (Jest, Vitest, etc.)
- [ ] Configure TypeScript/build tools
- [ ] Setup CI/CD pipeline (GitHub Actions)
- [ ] Create Docker development environment
- [ ] Setup environment variables template

**Acceptance Criteria**:
- [ ] Repository created with standard structure
- [ ] All developers can run project locally
- [ ] CI pipeline runs tests on PR
- [ ] Linting enforced on commit

**Dependencies**: None

**Assigned To**: [Developer Name]

**Technical Notes**:
- Use [Framework/Library] version X.Y.Z
- Follow [Company] coding standards

---

### UoW-002: Implement User Authentication
**Priority**: Must Have  
**Estimated Effort**: 8 hours

**Objective**:
Build secure user authentication system

**Tasks**:
- [ ] Design User schema/model
- [ ] Implement user registration endpoint
- [ ] Implement login endpoint with JWT
- [ ] Add password hashing (bcrypt)
- [ ] Implement token refresh mechanism
- [ ] Add rate limiting
- [ ] Write unit tests (>80% coverage)
- [ ] Write integration tests
- [ ] Document API endpoints

**Acceptance Criteria**:
- [ ] Users can register with email/password
- [ ] Users can login and receive JWT token
- [ ] Tokens expire after 1 hour
- [ ] Refresh tokens work correctly
- [ ] Rate limiting prevents brute force (5 attempts/15min)
- [ ] All tests pass
- [ ] API documentation updated

**Dependencies**: 
- UoW-001: Project infrastructure must be ready

**Assigned To**: [Developer Name]

**Technical Notes**:
- Use JWT with HS256 algorithm
- Store refresh tokens in database
- Implement middleware for auth checking

**Related Requirements**: FR-001, FR-002, NFR-SEC-001

---

### UoW-003: Create Data Models
**Priority**: Must Have  
**Estimated Effort**: 6 hours

**Objective**:
Define all database entities and relationships

**Tasks**:
- [ ] Design ER diagram
- [ ] Create User model
- [ ] Create Transaction model
- [ ] Create Account model
- [ ] Define relationships and foreign keys
- [ ] Add indexes for performance
- [ ] Write database migrations
- [ ] Seed test data
- [ ] Document data dictionary

**Acceptance Criteria**:
- [ ] All models defined with proper types
- [ ] Relationships correctly established
- [ ] Migrations run successfully
- [ ] Can seed database with test data
- [ ] Data dictionary documented

**Dependencies**: 
- UoW-001: Project infrastructure

**Assigned To**: [Developer Name]

**Technical Notes**:
- Use [ORM] (Prisma, TypeORM, etc.)
- Follow naming conventions: snake_case for DB, camelCase for code
- Add timestamps (created_at, updated_at) to all tables

**Related Requirements**: FR-003, FR-004

---

### UoW-004: Build API Endpoints
**Priority**: Must Have  
**Estimated Effort**: 12 hours

**Objective**:
Implement REST API for core features

**Tasks**:
- [ ] Design API structure (routes, controllers)
- [ ] Implement CRUD for resource A
- [ ] Implement CRUD for resource B
- [ ] Add input validation (Zod/Joi)
- [ ] Add error handling middleware
- [ ] Implement pagination
- [ ] Implement filtering & sorting
- [ ] Write OpenAPI/Swagger documentation
- [ ] Write integration tests
- [ ] Add request logging

**Acceptance Criteria**:
- [ ] All endpoints functional
- [ ] Input validation working
- [ ] Proper error responses (4xx, 5xx)
- [ ] Pagination works (limit, offset)
- [ ] Swagger UI accessible at /api/docs
- [ ] Integration tests pass
- [ ] Response times < 200ms

**Dependencies**: 
- UoW-002: Authentication (for protected routes)
- UoW-003: Data models

**Assigned To**: [Developer Name]

**Technical Notes**:
- Follow RESTful conventions
- Use consistent error format
- Implement HATEOAS links if applicable

**Related Requirements**: FR-005, FR-006, NFR-PERF-001

---

### UoW-005: Create Frontend Components
**Priority**: Must Have  
**Estimated Effort**: 16 hours

**Objective**:
Build reusable UI components

**Tasks**:
- [ ] Setup component library structure
- [ ] Create design system tokens
- [ ] Build authentication forms (Login, Register)
- [ ] Build dashboard layout
- [ ] Build data table component
- [ ] Build form components
- [ ] Add form validation
- [ ] Implement responsive design
- [ ] Add accessibility features (ARIA)
- [ ] Write component tests (React Testing Library)
- [ ] Document components (Storybook)

**Acceptance Criteria**:
- [ ] All components render correctly
- [ ] Forms validate user input
- [ ] Responsive on mobile, tablet, desktop
- [ ] Accessible (keyboard navigation, screen readers)
- [ ] Component tests pass
- [ ] Storybook docs complete

**Dependencies**: 
- UoW-004: API endpoints (for data fetching)

**Assigned To**: [Developer Name]

**Technical Notes**:
- Use [React/Vue/Angular]
- Follow atomic design principles
- Use CSS-in-JS or Tailwind

**Related Requirements**: FR-007, NFR-USA-001

---

## 5. UoW Template (For Creating New UoWs)

```markdown
### UoW-XXX: [Title]
**Priority**: Must Have | Should Have | Nice to Have  
**Estimated Effort**: [X hours/days]

**Objective**:
[What this UoW achieves]

**Tasks**:
- [ ] Task 1
- [ ] Task 2

**Acceptance Criteria**:
- [ ] Criteria 1
- [ ] Criteria 2

**Dependencies**: 
- [None | UoW-XXX]

**Assigned To**: [Name]

**Technical Notes**:
[Implementation notes, tech choices, patterns to use]

**Related Requirements**: [FR-XXX, NFR-XXX]
```

---

## 6. UoW Status Tracking

### Not Started
- UoW-006, UoW-007, UoW-008

### In Progress
- UoW-002 (50% complete)

### Blocked
- UoW-004 (Waiting for UoW-002 completion)

### Done
- UoW-001 ✓

---

## 7. Dependency Graph

```
UoW-001 (Foundation)
   ├─→ UoW-002 (Auth)
   │      └─→ UoW-004 (API)
   │             └─→ UoW-005 (Frontend)
   └─→ UoW-003 (Data Models)
          └─→ UoW-004 (API)
```

---

## 8. Risk Assessment

| UoW ID | Risk | Mitigation |
|--------|------|------------|
| UoW-002 | Security vulnerabilities | Security review, penetration testing |
| UoW-004 | Performance issues | Load testing, caching strategy |

---

## Change Log
| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [Date] | AI + Team | Initial UoW breakdown |
| 1.1 | [Date] | [Name] | Split UoW-004 into smaller units |
