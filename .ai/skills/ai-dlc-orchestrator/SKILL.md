---
name: ai-dlc-orchestrator
description: "Orchestrates AI-DLC (AI Development Life Cycle) workflow. Use when starting new projects, working through Inception, Construction, or Operations phases, creating requirements, architecture, epics, user stories, tasks, Unit of Work plans, Bolt prompts, or coordinating subsystem skills across design, frontend, backend, quality, testing, and DevOps."
---

## Always Read

Before starting any task, read these context files:
- `../../context/project-context.md` - Project structure and installed skills
- `../../routing/skill-routing.md` - Skill routing and selection policies

---

# AI-DLC Orchestrator

## Skill Integration & Subsystems

This orchestrator can **automatically integrate skills** based on subsystem needs without specifying individual skills.

### Available Skill Subsystems

When planning tasks, specify subsystems instead of individual skills:

| Subsystem | Includes Skills | Use For |
|-----------|-----------------|---------|
| **design** | frontend-design, web-design-guidelines | UI/UX design, visual identity, accessibility audit |
| **frontend** | angular-developer, angular-new-app | Frontend implementation, components, routing |
| **backend** | _(To be installed)_ backend skills | API, services, database integration |
| **quality** | code-review-expert, skill-review | Code review, SOLID check, security scan |
| **testing** | _(To be installed)_ test skills | Unit tests, integration tests, E2E |
| **devops** | _(To be installed)_ devops skills | Docker, CI/CD, deployment |

### Subsystem Usage in Tasks

Instead of:
```
Mode=FORCED
Skills: frontend-design, web-design-guidelines, angular-developer
```

Use:
```
Subsystems: design, frontend
```

AI-DLC will automatically load appropriate skills from each subsystem.

---

# AI-DLC Orchestrator

This skill guides you through the AI Development Life Cycle (AI-DLC) workflow, a structured approach to building software where AI and humans collaborate as partners.

## Core Philosophy

You are a **collaborator**, not just a code generator:
1. **Proactively ask clarifying questions** before implementing
2. **Propose solutions** and wait for human approval
3. **Document all decisions** and rationale
4. **Execute after confirmation**

## When to Activate This Skill

Activate this skill when:
- User says "start new project" or "create project using AI-DLC"
- Working in `.kiro/plans/` directory structure
- User mentions "inception", "construction", "operations", "UoW", or "Bolt"
- Asked to follow AI-DLC workflow

## Workflow Overview

```
Vision → Inception → Construction → Operations
```

Each phase has specific responsibilities and outputs.

---

## Phase 1: INCEPTION (Khởi Tạo)

### Your Responsibilities

1. **Analyze Input Documents**
   - Read `.kiro/plans/{project-id}/inputs/vision-document.md`
   - Read any API specs, mockups, or references in `inputs/`

2. **Ask Clarification Questions**
   - Create `.kiro/plans/{project-id}/aidlc-docs/inception/requirements/clarification-qa.md`
   - Use this format:
   ```markdown
   ## Q1: [Clear, specific question]
   **Context**: [Why this matters]
   **Options Considered**: [If applicable]
   **Your Input Needed**: [What specifically you need to know]
   ```

3. **Generate Requirements** (after clarifications answered)
   - `functional-requirements.md`: What the system does
   - `non-functional-requirements.md`: Quality attributes (performance, security, etc.)
   - `user-stories.md`: User-facing scenarios with acceptance criteria

4. **Create Application Design**
   - `application-design/system-context.md`: High-level architecture
   - `application-design/tech-stack.md`: Technology choices with rationale
   - `application-design/architecture-overview.md`: Components and their relationships

5. **Break Down Into Units of Work**
   - `plans/unit-of-work-list.md`: List all UoWs with priorities
   - `plans/bolt-schedule.md`: Group UoWs into Bolts (time-boxed iterations)

### Inception Checklist

Before moving to Construction, verify:
- [ ] All clarification questions answered by human
- [ ] Functional requirements reviewed and approved
- [ ] Non-functional requirements reviewed and approved
- [ ] User stories validated
- [ ] Architecture design approved
- [ ] UoW list created and prioritized
- [ ] Human explicitly says "proceed to construction"

### Example Flow

```bash
# You say:
"I've read the vision document. Before creating requirements, 
I have 5 clarification questions. Let me create clarification-qa.md..."

# After human answers:
"Thank you for the clarifications. I'll now generate:
1. Functional requirements (15 requirements identified)
2. Non-functional requirements (security, performance, etc.)
3. User stories (8 stories across 3 epics)

This will take ~5 minutes. Proceed?"

# After approval:
"Requirements generated. Please review:
- functional-requirements.md
- non-functional-requirements.md  
- user-stories.md

Once approved, I'll create the application design."
```

---

## Phase 2: CONSTRUCTION (Xây Dựng)

### Your Responsibilities

For each Unit of Work:

#### Step 1: UoW Planning
1. Read next UoW from `unit-of-work-list.md`
2. Copy `construction/units-of-work/uow-template.md`
3. Create detailed UoW document: `uow-{number}-{title}.md`
4. Fill in:
   - Objective
   - Technical design
   - **Subsystems needed** (design, frontend, backend, quality)
   - Tasks breakdown
   - Acceptance criteria
   - Dependencies

**Wait for human approval before coding**

#### Step 2: Task Breakdown & Execution
1. **Break UoW into execution tasks**
2. Create task files in `construction/execution-tasks/uow-{N}/`
3. Each task file format:
   ```markdown
   # Task: {task-name}
   **UoW**: UoW-{N}
   **Subsystems**: design, frontend
   **Status**: pending | in-progress | done
   **Assigned Agent**: kiro | codex | claude | cursor
   
   ## Description
   {what needs to be done}
   
   ## Acceptance Criteria
   - [ ] Criterion 1
   - [ ] Criterion 2
   
   ## Execution Log
   {agent logs progress here}
   
   ## Done
   - [ ] All criteria met
   - [ ] Tests passing
   - [ ] Code reviewed
   ```

4. **Execute tasks in sequence**
5. **Mark done** when task completed

#### Step 3: Implementation
1. For each execution task:
   - Load subsystems (auto-selects skills)
   - Generate code according to the design
   - **Immediately write tests** (unit + integration)
   - Follow coding standards
   - Document complex logic
   - Update task status to "done"

2. When all tasks done:
   - Mark UoW as done
   - Update `unit-of-work-list.md`

#### Step 4: Verification
1. Run tests: Ensure >80% coverage
2. Run linting/formatting checks
3. Build the project
4. Verify all acceptance criteria met
5. **If any fail, fix before proceeding**

#### Step 5: Integration
1. Document changes in UoW file
2. Update `unit-of-work-list.md` status to "Done"
3. Create summary of changes
4. **Wait for human code review**

### Construction Rules

**DO:**
- ✅ Read related requirements before coding
- ✅ Generate tests alongside code
- ✅ Ask questions if requirements unclear
- ✅ Document technical decisions
- ✅ Verify acceptance criteria before marking done

**DON'T:**
- ❌ Start coding without approved design
- ❌ Skip tests "to be faster"
- ❌ Make architectural decisions without discussion
- ❌ Mark UoW as done without verification
- ❌ Assume requirements - always clarify

### Example Flow

```bash
# You say:
"Starting UoW-001: Setup Project Infrastructure

I've created the detailed UoW document with:
- Tech stack: Node.js, TypeScript, Express, PostgreSQL
- Project structure with monorepo setup
- Docker development environment
- CI/CD with GitHub Actions

Please review uow-001-setup-infrastructure.md. 
Approve to proceed with implementation?"

# After approval:
"Implementing... (8 tasks)
✓ Initialized Git repository
✓ Created monorepo structure
✓ Configured TypeScript + ESLint
✓ Setup Jest testing framework
✓ Created Docker compose for dev
✓ Setup GitHub Actions CI
✓ Created environment template
✓ Added README with setup instructions

All tests passing ✓ (45 tests, 92% coverage)
Linting passed ✓
Build successful ✓

UoW-001 ready for review."
```

---

## Phase 3: OPERATIONS (Vận Hành)

### Your Responsibilities

1. **Infrastructure as Code**
   - Create `operations/infrastructure/` configs
   - Docker, Kubernetes, or cloud-specific (AWS, GCP, Azure)
   - Follow security best practices

2. **CI/CD Pipeline**
   - Automated testing on PR
   - Automated deployment to staging
   - Manual approval gate for production

3. **Monitoring & Observability**
   - Logging configuration
   - Metrics collection
   - Alerting rules
   - Dashboard setup

4. **Deployment Plan**
   - Create detailed `operations/deployment/deployment-plan.md`
   - Include rollback procedures
   - Smoke test checklist

### Operations Checklist

- [ ] Infrastructure code created
- [ ] CI/CD pipeline configured
- [ ] Monitoring setup complete
- [ ] Deployment plan written and reviewed
- [ ] Security review passed
- [ ] Successfully deployed to staging
- [ ] Smoke tests passed
- [ ] Human approves production deployment

### Example Flow

```bash
# You say:
"All UoWs completed. Moving to Operations phase.

I'll create:
1. Docker + Kubernetes configs
2. GitHub Actions CI/CD pipeline  
3. Prometheus + Grafana monitoring
4. Deployment plan with rollback procedures

Starting with infrastructure code..."

# After creation:
"Infrastructure ready for review:
- operations/infrastructure/kubernetes/ (deployment, service, ingress)
- operations/infrastructure/docker/ (multi-stage Dockerfile)
- .github/workflows/ci-cd.yml (test + deploy pipeline)
- operations/monitoring/ (Prometheus alerts, Grafana dashboards)

Please review security aspects before I proceed with deployment plan."
```

---

## Communication Patterns

### Asking Clarification Questions

**Good:**
```
Q: Should user authentication support OAuth providers?
Context: The vision mentions "secure login" but doesn't specify auth methods.
Options Considered:
1. Email/password only (simpler, but less convenient)
2. Email/password + OAuth (Google, GitHub)
3. OAuth only (modern, but requires fallback)
Your Input: Which option fits the target users and timeline?
```

**Bad:**
```
Q: What about auth?
```

### Documenting Decisions

Always document in `implementation-notes/tech-decisions.md`:

```markdown
**Decision**: Use PostgreSQL instead of MongoDB
**Date**: 2024-01-15
**Rationale**: 
- Need strong consistency for financial transactions
- Complex relationships require JOIN operations
- Team has more PostgreSQL experience
**Alternatives Considered**: MongoDB (rejected due to transaction requirements)
**Trade-offs**: 
- Gain: ACID guarantees, better for relational data
- Lose: Some flexibility in schema evolution
```

---

## Quality Gates

### Gate 1: After Inception
**STOP if:**
- Clarification questions unanswered
- Requirements not approved
- Architecture not approved

**Only proceed when human says: "Requirements approved, proceed to construction"**

### Gate 2: After Each UoW
**STOP if:**
- Tests not passing
- Coverage <80%
- Acceptance criteria not met
- Human hasn't reviewed code

**Only proceed when human says: "UoW approved, continue"**

### Gate 3: Before Production Deployment
**STOP if:**
- Security review incomplete
- Staging tests failed
- Deployment plan not approved

**Only proceed when human says: "Deploy to production"**

---

## Context Awareness

### Always Check These Files First

1. **Project structure**:
   ```bash
   .kiro/plans/{project-id}/
   ├── brd.md                    # Read first
   ├── inputs/
   │   └── vision-document.md    # Read second
   └── aidlc-docs/
       ├── inception/            # Phase 1 outputs
       ├── construction/         # Phase 2 outputs
       └── operations/           # Phase 3 outputs
   ```

2. **Steering files**:
   - `.kiro/steering/ai-dlc-workflow.md` - Process guidance
   - `.kiro/steering/coding-standards.md` - Code style (if exists)

3. **Current phase state**:
   - Check which documents exist to determine current phase
   - Check UoW status in `unit-of-work-list.md`

### Maintain Context

- Update documents as you progress
- Keep change logs current
- Cross-reference between documents (use relative links)
- Update traceability matrices

---

## Templates and Shortcuts

### Starting New Project

```bash
# When user says "create new project with AI-DLC":

1. Check if project structure exists:
   - If yes: "Project structure found. Continue from [detected phase]?"
   - If no: "I'll create the project structure."

2. Create structure:
   mkdir -p .kiro/plans/{project-id}/{inputs,aidlc-docs/{inception,construction,operations}}

3. Copy templates:
   - Copy vision-document.md template to inputs/
   - Ask user to fill it in

4. Say: "Project structure ready. Please fill in vision-document.md, 
   then I'll start the Inception phase."
```

### Resuming Work

```bash
# When returning to an existing project:

1. Analyze current state:
   - Read BRD and vision
   - Check which phase documents exist
   - Check UoW status if in Construction

2. Report status:
   "Project Status:
   - Phase: Construction (Bolt 2)
   - Completed: UoW-001 ✓, UoW-002 ✓
   - In Progress: UoW-003 (50%)
   - Remaining: UoW-004, UoW-005
   
   Continue with UoW-003?"
```

---

## Troubleshooting

### Issue: Requirements unclear
**Action:**
1. Don't assume - ask specific clarification questions
2. Reference similar features if available
3. Propose options with trade-offs

### Issue: Technical blocker
**Action:**
1. Document the blocker in UoW
2. Propose alternative approaches
3. Explain impact on timeline/scope
4. Wait for decision

### Issue: Tests failing
**Action:**
1. Analyze error messages
2. Fix the issue
3. Re-run tests
4. **Never skip or mark as "to be fixed later"**

---

## Best Practices

1. **Be proactive but not presumptuous**
   - Ask questions early
   - Propose solutions
   - Wait for approval on big decisions

2. **Document everything**
   - Every decision gets documented
   - Every clarification gets recorded
   - Every UoW gets detailed notes

3. **Maintain quality**
   - Tests are mandatory, not optional
   - >80% coverage is minimum
   - Security is always reviewed

4. **Communicate clearly**
   - Use structured formats
   - Provide context with questions
   - Summarize before long operations

5. **Respect the process**
   - Don't skip phases
   - Don't skip quality gates
   - Don't assume approvals

---

## Quick Commands Reference

### For You (AI)

**Start Inception:**
```
1. Read inputs/vision-document.md
2. Create clarification-qa.md
3. Wait for answers
4. Generate requirements (functional, non-functional, user-stories)
5. Create application design
6. Create unit-of-work-list.md
7. Wait for approval
```

**Start UoW:**
```
1. Read unit-of-work-list.md - find next UoW
2. Copy uow-template.md → uow-{N}-{title}.md
3. Fill in detailed design
4. Wait for approval
5. Implement code + tests
6. Verify (tests, linting, build)
7. Update UoW status
8. Wait for code review
```

**Deploy:**
```
1. Create infrastructure code
2. Create CI/CD pipeline
3. Create monitoring configs
4. Write deployment-plan.md
5. Deploy to staging
6. Run smoke tests
7. Wait for production approval
8. Deploy to production
```

---

## Example Session

```
User: "Create a new project for a task management app using AI-DLC"

You: "I'll set up a new AI-DLC project. First, I'll create the structure...
[Creates .kiro/plans/task-management-app/]

Structure created. I've placed a vision-document.md template in inputs/.
Please fill in:
- Problem statement (what problem does this solve?)
- Target users (who will use this?)
- Key features (what should it do?)
- Success criteria (how do we measure success?)

Once done, I'll begin the Inception phase."

User: "Done. Here's the vision document."

You: "Thank you. I've read the vision document. Before generating 
requirements, I have 6 clarification questions in clarification-qa.md:

Q1: Should tasks support subtasks/hierarchies?
Q2: What's the priority system? (High/Med/Low or 1-5?)
Q3: Should users be able to share tasks with others?
[...]

Please answer when ready."

User: "Answered all questions."

You: "Perfect. I'll now generate:
1. Functional requirements (~12 features identified)
2. Non-functional requirements (performance, security, scalability)
3. User stories (~10 stories across 3 epics)

This will take about 5 minutes. Proceed?"

User: "Yes"

You: [Generates documents]
"Requirements complete. Please review:
- inception/requirements/functional-requirements.md (FR-001 to FR-012)
- inception/requirements/non-functional-requirements.md
- inception/requirements/user-stories.md (US-001 to US-010)

Key highlights:
- Core features: Create/edit/delete tasks, assign users, filter/search
- Performance: API response <200ms, support 1000 concurrent users
- Security: JWT auth, RBAC, encrypted data

Once approved, I'll create the application design."

[Process continues through Construction and Operations...]
```

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2024 | Initial AI-DLC Orchestrator skill |
