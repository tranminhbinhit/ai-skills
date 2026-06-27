# User Stories

## 1. Overview
Document này chứa các user stories được viết theo format chuẩn Agile.

**Format**: As a [role], I want to [action], so that [benefit]

**Last Updated**: [Date]  
**Status**: Draft | Review | Approved

---

## 2. Epic 1: [Epic Name]

### Story 1.1: [Story Title]
**ID**: US-001  
**Priority**: Must Have | Should Have | Nice to Have  
**Story Points**: [1, 2, 3, 5, 8, 13]

**User Story**:
```
As a [user role],
I want to [perform action],
So that [achieve benefit].
```

**Acceptance Criteria**:
```gherkin
Scenario: [Scenario name]
  Given [initial context]
  When [action occurs]
  Then [expected outcome]
  
Scenario: [Another scenario]
  Given [context]
  And [additional context]
  When [action]
  Then [outcome]
  And [additional outcome]
```

**Technical Notes**:
- Implementation considerations
- API endpoints needed
- Data model changes

**Dependencies**:
- US-XXX: [Related story]
- External: [External dependency]

**Definition of Done**:
- [ ] Code completed and reviewed
- [ ] Unit tests written (> 80% coverage)
- [ ] Integration tests passed
- [ ] Documentation updated
- [ ] Acceptance criteria verified
- [ ] Deployed to staging

---

### Story 1.2: [Story Title]
**ID**: US-002  
[Repeat structure above]

---

## 3. Epic 2: [Epic Name]

### Story 2.1: [Story Title]
**ID**: US-003  
[Continue...]

---

## 4. User Personas

### Persona 1: [Name - Role]
**Demographics**:
- Age: [Range]
- Technical skill: [Beginner/Intermediate/Advanced]
- Usage frequency: [Daily/Weekly/Monthly]

**Goals**:
- Goal 1: ...
- Goal 2: ...

**Pain Points**:
- Pain 1: ...
- Pain 2: ...

**User Journey**:
1. Step 1 in their workflow
2. Step 2 in their workflow

**Related Stories**: US-001, US-003, US-005

---

### Persona 2: [Name - Role]
[Repeat structure above]

---

## 5. Story Mapping

```
User Activities
    ↓
User Tasks (Epics)
    ↓
User Stories
    ↓
Details & Subtasks
```

### Activity: [Main User Activity]

**Epic 1: [Task]**
- US-001 (Must Have)
- US-002 (Must Have)
- US-003 (Should Have)

**Epic 2: [Task]**
- US-004 (Must Have)
- US-005 (Nice to Have)

---

## 6. Backlog Prioritization

### Sprint 1 / Bolt 1 (Must Have)
1. US-001: [Title] - [Story Points]
2. US-002: [Title] - [Story Points]
3. US-004: [Title] - [Story Points]

**Total**: [X] story points

---

### Sprint 2 / Bolt 2 (Should Have)
1. US-003: [Title] - [Story Points]
2. US-006: [Title] - [Story Points]

**Total**: [Y] story points

---

### Backlog (Nice to Have)
- US-005: [Title]
- US-007: [Title]

---

## 7. Detailed Story Examples

### US-001: User Login
**Priority**: Must Have  
**Story Points**: 5

**User Story**:
```
As a registered user,
I want to log in to the system using my email and password,
So that I can access my personal dashboard and data.
```

**Acceptance Criteria**:
```gherkin
Scenario: Successful login
  Given I am on the login page
  And I have a valid account
  When I enter my email "user@example.com"
  And I enter my password "SecurePass123!"
  And I click the "Login" button
  Then I should be redirected to the dashboard
  And I should see a welcome message "Welcome back, John!"
  
Scenario: Invalid credentials
  Given I am on the login page
  When I enter invalid credentials
  And I click the "Login" button
  Then I should see an error message "Invalid email or password"
  And I should remain on the login page
  
Scenario: Account locked after multiple failures
  Given I have failed login 5 times
  When I attempt to login again
  Then I should see "Account locked. Contact support."
  And I should receive an email notification
```

**Technical Notes**:
- Use JWT for session management
- Implement rate limiting: 5 attempts per 15 minutes
- Hash passwords with bcrypt
- API endpoint: POST /api/v1/auth/login

**UI Mockup**: [Link to Figma]

**Dependencies**:
- User registration (US-000) must be completed first
- Email service configured

**Definition of Done**:
- [ ] Login form implemented with validation
- [ ] Backend authentication service created
- [ ] Rate limiting implemented
- [ ] Unit tests: 85% coverage
- [ ] Integration tests for happy path and error cases
- [ ] Security review passed
- [ ] Documentation updated (API docs, user guide)

---

### US-002: View Transaction History
**Priority**: Must Have  
**Story Points**: 3

**User Story**:
```
As a logged-in user,
I want to view my transaction history,
So that I can track my past activities and expenses.
```

**Acceptance Criteria**:
```gherkin
Scenario: View paginated transaction list
  Given I am logged in
  When I navigate to the "Transactions" page
  Then I should see my 20 most recent transactions
  And transactions should be sorted by date (newest first)
  And each transaction shows: date, amount, type, status
  
Scenario: Filter transactions by date range
  Given I am on the transactions page
  When I select date range "Last 30 days"
  And I click "Apply"
  Then I should see only transactions from the last 30 days
  
Scenario: Search transactions
  Given I am on the transactions page
  When I enter "coffee" in the search box
  Then I should see transactions containing "coffee" in description
```

**Technical Notes**:
- Implement pagination (20 items per page)
- Add indexes on user_id and created_at
- API endpoint: GET /api/v1/transactions?page=1&limit=20&from=date&to=date

**Dependencies**:
- Transaction data model (US-001)
- Login functionality (US-001)

---

## 8. Story Template (For Quick Copy)

```markdown
### US-XXX: [Story Title]
**Priority**: Must Have | Should Have | Nice to Have  
**Story Points**: [1, 2, 3, 5, 8]

**User Story**:
As a [role],
I want to [action],
So that [benefit].

**Acceptance Criteria**:
- [ ] Criteria 1
- [ ] Criteria 2

**Technical Notes**:
- Note 1

**Dependencies**:
- None | US-XXX

**Definition of Done**:
- [ ] Code completed
- [ ] Tests written
- [ ] Reviewed and merged
```

---

## 9. Traceability Matrix

| Story ID | Epic | Functional Req | Priority | Status | Sprint/Bolt |
|----------|------|---------------|----------|---------|-------------|
| US-001 | User Management | FR-001 | Must Have | Done | Bolt 1 |
| US-002 | Transactions | FR-005 | Must Have | In Progress | Bolt 1 |
| US-003 | Reporting | FR-010 | Should Have | Todo | Bolt 2 |

---

## Change Log
| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [Date] | AI + Team | Initial stories created |
| 1.1 | [Date] | Team | Added US-007, US-008 |
