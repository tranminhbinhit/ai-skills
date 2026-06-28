# UoW-XXX: [Unit of Work Title]

**Status**: 🔵 Not Started | 🟡 In Progress | 🟢 Done | 🔴 Blocked  
**Priority**: Must Have | Should Have | Nice to Have  
**Bolt**: Bolt X  
**Estimated Effort**: [X hours/days]  
**Actual Effort**: [Y hours]  
**Assigned To**: [Developer Name]  
**Last Updated**: [Date]

---

## 1. Objective
[Mô tả rõ ràng mục tiêu của UoW này - what will be achieved]

---

## 2. Context & Background
### 2.1 Why This UoW?
[Giải thích tại sao UoW này cần thiết, business value]

### 2.2 Related Requirements
- **Functional**: FR-XXX, FR-YYY
- **Non-Functional**: NFR-XXX
- **User Stories**: US-XXX

---

## 3. Scope

### 3.1 In Scope
- Item 1: ...
- Item 2: ...

### 3.2 Out of Scope
- Item 1: ...
- Item 2: ...

---

## 4. Tasks Breakdown

### Phase 1: Design & Planning
- [ ] Review requirements and clarify ambiguities
- [ ] Design component/module architecture
- [ ] Create technical design document
- [ ] Get design approval from tech lead

### Phase 2: Implementation
- [ ] Task 1: [Description]
  - Subtask 1.1
  - Subtask 1.2
- [ ] Task 2: [Description]
- [ ] Task 3: [Description]

### Phase 3: Testing
- [ ] Write unit tests (target: >80% coverage)
- [ ] Write integration tests
- [ ] Manual testing of key scenarios
- [ ] Performance testing (if applicable)

### Phase 4: Documentation & Review
- [ ] Update API documentation
- [ ] Update README/code comments
- [ ] Code review by peer
- [ ] Address review feedback

### Phase 5: Deployment & Verification
- [ ] Merge to main branch
- [ ] Deploy to staging
- [ ] Run smoke tests
- [ ] Verify in production (if applicable)

---

## 5. Acceptance Criteria

### Functional Criteria
- [ ] Criteria 1: Given [context], when [action], then [result]
- [ ] Criteria 2: ...
- [ ] Criteria 3: ...

### Technical Criteria
- [ ] Code follows project coding standards
- [ ] Unit test coverage >= 80%
- [ ] All tests pass in CI/CD
- [ ] No security vulnerabilities (linting checks)
- [ ] Performance meets NFR requirements

### Documentation Criteria
- [ ] API endpoints documented (if applicable)
- [ ] Code comments for complex logic
- [ ] README updated with setup instructions

---

## 6. Dependencies

### Upstream Dependencies (Must be done first)
- [ ] UoW-XXX: [Title] - Status: [Done/In Progress]
- [ ] External dependency: [Description]

### Downstream Dependencies (Blocked by this UoW)
- UoW-YYY: [Title]

---

## 7. Technical Design

### 7.1 Architecture Overview
[Diagram hoặc mô tả architecture]

```
Component A → Component B → Database
     ↓
Component C
```

### 7.2 Key Components
**Component 1: [Name]**
- Responsibility: ...
- Key methods/functions: ...

**Component 2: [Name]**
- Responsibility: ...

### 7.3 Data Model
[Describe entities, schemas, or data structures]

```typescript
interface User {
  id: string;
  name: string;
  email: string;
}
```

### 7.4 API Design (if applicable)
**Endpoint**: `POST /api/v1/resource`

**Request**:
```json
{
  "field1": "value",
  "field2": 123
}
```

**Response**:
```json
{
  "id": "uuid",
  "status": "success"
}
```

### 7.5 Technology Stack
- Language: [TypeScript, Python, etc.]
- Framework: [Express, FastAPI, etc.]
- Libraries: [List key libraries]
- Database: [PostgreSQL, MongoDB, etc.]

---

## 8. Implementation Notes

### 8.1 Key Decisions
**Decision 1**: [What was decided]
- Rationale: [Why this was chosen]
- Alternatives considered: [What else was considered]

**Decision 2**: [What was decided]
- Rationale: ...

### 8.2 Design Patterns Used
- Pattern 1: [e.g., Repository Pattern]
- Pattern 2: [e.g., Factory Pattern]

### 8.3 Code Locations
- Main implementation: `src/modules/[module]/`
- Tests: `tests/unit/[module]/`
- Configuration: `config/[file].ts`

---

## 9. Testing Strategy

### 9.1 Unit Tests
**Test Coverage Target**: 80%+

**Key Test Cases**:
1. Test case 1: [Description]
2. Test case 2: [Description]

### 9.2 Integration Tests
1. Test scenario 1: [End-to-end flow]
2. Test scenario 2: [Error handling]

### 9.3 Manual Testing Checklist
- [ ] Happy path: [Scenario]
- [ ] Error case 1: [Scenario]
- [ ] Edge case: [Scenario]

---

## 10. Risks & Mitigations

| Risk | Probability | Impact | Mitigation Strategy |
|------|------------|---------|---------------------|
| Risk 1: [Description] | High/Med/Low | High/Med/Low | [How to handle] |
| Risk 2: [Description] | ... | ... | ... |

---

## 11. Questions & Clarifications

**Q1**: [Question raised during implementation]  
**A1**: [Answer/Resolution] - [Date, by whom]

**Q2**: [Question]  
**A2**: [Answer]

---

## 12. Progress Log

| Date | Hours | Activity | Notes |
|------|-------|----------|-------|
| 2024-01-15 | 2h | Initial design | Created architecture diagram |
| 2024-01-16 | 4h | Implemented core logic | Completed Task 1, 2 |
| 2024-01-17 | 3h | Testing | Unit tests at 85% coverage |

**Total Time Logged**: [X hours]

---

## 13. Review & Sign-off

### Code Review
- **Reviewer**: [Name]
- **Date**: [Date]
- **Status**: Approved | Changes Requested
- **Comments**: [Feedback summary]

### Technical Lead Approval
- **Approver**: [Name]
- **Date**: [Date]
- **Status**: Approved | Rejected

---

## 14. Post-Implementation Notes

### 14.1 What Went Well
- Point 1
- Point 2

### 14.2 Challenges Faced
- Challenge 1: [How it was resolved]
- Challenge 2: [How it was resolved]

### 14.3 Lessons Learned
- Lesson 1
- Lesson 2

### 14.4 Technical Debt Created
- [ ] Debt item 1: [Description, why it was necessary, plan to address]
- [ ] Debt item 2: [Description]

---

## 15. Related Links
- Pull Request: [Link]
- Issue/Ticket: [Link]
- Design Document: [Link]
- API Documentation: [Link]

---

## Appendix: Code Snippets

### Key Code Sample 1
```typescript
// Core implementation
function processData(input: Data): Result {
  // Logic here
}
```

### Key Code Sample 2
```typescript
// Test example
describe('processData', () => {
  it('should handle valid input', () => {
    // Test implementation
  });
});
```
