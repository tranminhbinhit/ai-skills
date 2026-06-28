# Gemini CLI Agent Configuration

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

## Gemini CLI Skill Locations

Gemini CLI loads skills from:
- **Context Files**: Project root
- **Installed Agent Skills**: `.agents/skills/`
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
