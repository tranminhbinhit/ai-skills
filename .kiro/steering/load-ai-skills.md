---
inclusion: auto
---

# Load AI Context for Kiro

## Always Read Before Task Execution

When working on any task, always read these files first:

1. **Project Context**: `.ai/context/project-context.md`
   - Understand installed skills
   - Know project structure
   - Check available capabilities

2. **Skill Routing**: `.ai/routing/skill-routing.md`
   - Learn skill selection rules
   - Understand routing policies
   - Check domain-specific mappings

---

## Kiro Skill Locations

Kiro loads skills from:
- **Installed Skills**: `.kiro/skills/`
- **Agent Skills**: `.agents/skills/`
- **Custom Skills**: `.ai/skills/`

---

## Skill Selection Flow

```
User Request
    ↓
Read .ai/routing/skill-routing.md
    ↓
Determine Domain (Frontend/Backend/Database/DevOps/SDLC)
    ↓
Check Selection Policy (AUTO/PREFERRED/FORCED/EXCLUSIVE)
    ↓
Load Appropriate Skill(s)
    ↓
Execute Task
```
