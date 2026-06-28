# Agent Assignment Rules

Quy tắc phân công công việc cho các AI agents trong AI-DLC workflow.

---

## 🎯 Default Agent Assignments

### Kiro (Planning & Analysis)
**Role**: Orchestrator, Planner, Reviewer

**Responsibilities**:
- Run AI-DLC Orchestrator
- Inception phase (requirements, architecture)
- Create Unit of Work breakdown
- Create execution tasks
- Review & quality control
- Final integration

**Skills Used**:
- ai-dlc-orchestrator (primary)
- code-review-expert
- skill-review

**Tasks**:
- ✅ Analyze vision documents
- ✅ Generate requirements
- ✅ Create architecture design
- ✅ Break down into UoWs
- ✅ Create execution tasks
- ✅ Review code quality
- ✅ Coordinate between agents

---

### Codex (Code Execution)
**Role**: Implementation Specialist

**Responsibilities**:
- Execute implementation tasks
- Write production code
- Implement features
- Fix bugs
- Refactor code

**Skills Used**:
- Subsystem-specific skills (design, frontend, backend)
- Auto-loaded based on task subsystems

**Tasks**:
- ✅ Execute tasks in `construction/execution-tasks/`
- ✅ Implement features
- ✅ Write tests
- ✅ Follow coding standards
- ✅ Update task status to "done"

---

### Claude Code (Alternative Executor)
**Role**: Code Generation & Refactoring

**Responsibilities**:
- Alternative to Codex
- Can replace Codex for execution tasks
- Good for complex refactoring

**Skills Used**:
- Same as Codex
- Subsystem-specific skills

**Tasks**:
- ✅ Execute tasks (alternative to Codex)
- ✅ Complex refactoring
- ✅ Pattern implementation

---

### Cursor (In-Editor Support)
**Role**: Quick Edits & Fixes

**Responsibilities**:
- Small, focused changes
- Bug fixes
- Quick implementations
- In-editor assistance

**Skills Used**:
- Contextual skills based on file type

**Tasks**:
- ✅ Quick bug fixes
- ✅ Small feature additions
- ✅ Code formatting
- ✅ Simple refactoring

---

### Gemini (Optional Support)
**Role**: Alternative Executor

**Responsibilities**:
- Can replace any executor
- Experimental features
- Alternative approach

**Skills Used**:
- All available skills

**Tasks**:
- ✅ Alternative execution path
- ✅ Second opinion on design
- ✅ Experimental implementations

---

## 📋 Workflow Assignments

### Phase 1: Inception
```
Agent: Kiro
Skill: ai-dlc-orchestrator

Tasks:
1. Read vision document
2. Create clarification-qa.md
3. Wait for answers
4. Generate requirements
5. Create architecture design
6. Break into UoWs
7. Create execution tasks
```

---

### Phase 2: Construction

#### Planning (Kiro)
```
Agent: Kiro
Skill: ai-dlc-orchestrator

Tasks:
1. For each UoW:
   - Create detailed UoW document
   - Identify subsystems needed
   - Break into execution tasks
   - Create task files in construction/execution-tasks/
2. Wait for approval
```

#### Execution (Codex)
```
Agent: Codex
Subsystems: (auto from task file)

Tasks:
1. Read execution task file
2. Load required subsystems
3. Implement according to spec
4. Write tests
5. Mark criteria as done
6. Update task status to "done"
7. Move to next task
```

#### Review (Kiro)
```
Agent: Kiro
Skills: code-review-expert

Tasks:
1. Review all completed tasks
2. Check SOLID principles
3. Security scan
4. Verify acceptance criteria
5. Approve or request changes
```

---

### Phase 3: Operations
```
Agent: Kiro
Skill: ai-dlc-orchestrator

Tasks:
1. Create infrastructure code
2. Setup CI/CD pipeline
3. Configure monitoring
4. Create deployment plan
```

---

## 🔄 Task Execution Flow

### Standard Flow

```
1. Kiro (Planning)
   → Create UoW
   → Break into execution tasks
   → Create task files

2. Codex (Execution)
   → Read task file
   → Load subsystems
   → Implement
   → Write tests
   → Mark done

3. Kiro (Review)
   → Review code
   → Check quality
   → Approve/reject

4. Repeat for all tasks
```

---

### Task File Format

Location: `.kiro/plans/{project}/construction/execution-tasks/uow-{N}/task-{M}-{name}.md`

```markdown
# Task: {task-name}

**UoW**: UoW-{N}  
**Subsystems**: design, frontend  
**Status**: pending  
**Assigned Agent**: codex  
**Created**: 2024-01-15  
**Updated**: 2024-01-15  

## Description
{What needs to be done}

## Subsystem Skills
- design: frontend-design, web-design-guidelines
- frontend: angular-developer

## Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Tests written and passing
- [ ] Code follows standards

## Technical Notes
{Any technical considerations}

## Dependencies
- Task-1 must be done first
- API contract from backend team

## Execution Log

### 2024-01-15 14:00 - Codex
Started implementation...

### 2024-01-15 15:30 - Codex
Completed implementation. Tests passing.

## Done Checklist
- [ ] All acceptance criteria met
- [ ] Tests passing (coverage >80%)
- [ ] Code reviewed
- [ ] Documentation updated

## Status: ✅ DONE
Completed by: codex
Completed at: 2024-01-15 15:30
Reviewed by: kiro
Approved at: 2024-01-15 16:00
```

---

## 🎯 Agent Selection Logic

### By Task Type

| Task Type | Primary Agent | Backup Agent |
|-----------|---------------|--------------|
| Analysis & Planning | Kiro | - |
| Requirements | Kiro | - |
| Architecture Design | Kiro | - |
| UoW Breakdown | Kiro | - |
| Task Creation | Kiro | - |
| Code Implementation | Codex | Claude Code |
| Feature Development | Codex | Claude Code |
| Bug Fixes (small) | Cursor | Codex |
| Bug Fixes (complex) | Codex | Claude Code |
| Refactoring | Codex | Claude Code |
| Code Review | Kiro | - |
| Testing | Codex | Claude Code |
| Infrastructure | Kiro | Codex |
| Deployment | Kiro | - |

---

### By Subsystem

| Subsystem | Primary Agent | Skills Loaded |
|-----------|---------------|---------------|
| design | Codex | frontend-design, web-design-guidelines |
| frontend | Codex | angular-developer, angular-new-app |
| backend | Codex | _(to be installed)_ backend skills |
| quality | Kiro | code-review-expert, skill-review |
| testing | Codex | _(to be installed)_ test skills |
| devops | Kiro | _(to be installed)_ devops skills |

---

## 💡 Usage Examples

### Example 1: Create New Project

```
# User prompt (to Kiro)
Create new project "e-commerce" using AI-DLC workflow

# Kiro executes
- ai-dlc-orchestrator skill
- Creates project structure
- Inception phase
- Creates UoWs
- Creates execution tasks

# Then tells user
"Project structure ready. 12 execution tasks created.
Run each task with Codex to implement."
```

---

### Example 2: Execute Task

```
# User prompt (to Codex)
Execute task: construction/execution-tasks/uow-001/task-1-create-homepage.md

# Codex executes
- Reads task file
- Sees: Subsystems: design, frontend
- Auto-loads: frontend-design, angular-developer
- Implements homepage
- Writes tests
- Updates task status to "done"
```

---

### Example 3: Review Code

```
# User prompt (to Kiro)
Review all completed tasks in UoW-001

# Kiro executes
- code-review-expert skill
- Reviews all task implementations
- Checks SOLID, security
- Approves or requests changes
```

---

## 📝 Configuration

### Default Configuration

Location: `.kiro/plans/{project}/aidlc-docs/agent-config.json`

```json
{
  "agents": {
    "planning": "kiro",
    "execution": "codex",
    "review": "kiro",
    "quickFixes": "cursor"
  },
  "subsystems": {
    "design": ["frontend-design", "web-design-guidelines"],
    "frontend": ["angular-developer", "angular-new-app"],
    "backend": [],
    "quality": ["code-review-expert", "skill-review"],
    "testing": [],
    "devops": []
  },
  "workflow": {
    "autoAssignTasks": true,
    "requireApproval": true,
    "autoMarkDone": false
  }
}
```

---

### Custom Configuration

Override defaults per project:

```json
{
  "agents": {
    "planning": "kiro",
    "execution": "claude",  // Use Claude instead of Codex
    "review": "kiro",
    "quickFixes": "cursor"
  }
}
```

---

## 🚀 Quick Start

### Step 1: Planning (Kiro)
```
Kiro: Create new AI-DLC project "my-app"
```

### Step 2: Execution (Codex)
```
Codex: Execute next pending task in my-app
```

### Step 3: Review (Kiro)
```
Kiro: Review completed tasks in my-app
```

### Step 4: Repeat
```
Repeat Step 2-3 until all tasks done
```

---

## 🔧 Advanced Usage

### Override Agent for Specific Task

In task file:
```markdown
**Assigned Agent**: claude  // Override default (codex)
```

### Execute All Tasks Automatically

```
Codex: Execute all pending tasks in UoW-001
Auto-mode: true
```

### Parallel Execution

```
# Terminal 1
Codex: Execute task-1

# Terminal 2
Claude: Execute task-2

# Tasks must be independent
```

---

## 📊 Progress Tracking

### View Project Status

```
Kiro: Show AI-DLC project status for "my-app"

Output:
- Phase: Construction
- UoWs: 5 total, 2 done, 1 in-progress, 2 pending
- Tasks: 25 total, 15 done, 3 in-progress, 7 pending
- Completion: 60%
```

### View Task Status

```
Kiro: List all pending tasks in "my-app"

Output:
- task-8-implement-auth.md (UoW-002) - pending
- task-9-setup-database.md (UoW-002) - pending
- task-15-create-dashboard.md (UoW-003) - pending
```

---

## 🎯 Best Practices

### For Kiro (Planning)
1. ✅ Create detailed UoW documents
2. ✅ Break into small, atomic tasks
3. ✅ Specify subsystems clearly
4. ✅ Define acceptance criteria
5. ✅ Review all completed work

### For Codex (Execution)
1. ✅ Read task file completely
2. ✅ Follow technical notes
3. ✅ Write tests immediately
4. ✅ Update execution log
5. ✅ Mark done only when all criteria met

### For Cursor (Quick Fixes)
1. ✅ Small, focused changes only
2. ✅ Don't break existing code
3. ✅ Update task log
4. ✅ Keep changes minimal

---

## 📚 Reference

- **AI-DLC Workflow**: See `.kiro/steering/ai-dlc-workflow.md`
- **Skill Subsystems**: See `.ai/routing/skill-routing.md`
- **Task Templates**: See `.kiro/plans/templates/`

---

_Version: 1.0 | Last Updated: 2026-06-28_
