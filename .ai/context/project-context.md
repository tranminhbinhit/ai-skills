# Project Context

## Installed Skills Registry

| Nhóm | Skill | Location | Dùng khi nào |
|---|---|---|---|
| Frontend | angular-developer | `.kiro/skills/angular-developer/` | Angular components, forms, routing, signals, RxJS, UI, testing, CLI |
| Frontend | angular-new-app | `.kiro/skills/angular-new-app/` | Create new Angular application, scaffold project |
| Frontend | frontend-design | `.kiro/skills/frontend-design/` | Visual design, typography, palette, layout, distinctive UI, aesthetic direction |
| Frontend | web-design-guidelines | `.kiro/skills/web-design-guidelines/` | UI review, accessibility audit, UX compliance, best practices check |
| Quality | code-review-expert | `.kiro/skills/code-review-expert/` | Code review, SOLID principles, security scan, git diff analysis |
| Quality | skill-review | `.kiro/skills/skill-review/` | Skill quality audit, skill validation, skill structure review |
| SDLC | ai-dlc-orchestrator | `.ai/skills/ai-dlc-orchestrator/` | AI-DLC workflow, Inception, Construction, Operations, UoW, requirements |

---

## Quick Reference

### Frontend Development
- **New Angular App**: Use `angular-new-app`
- **Angular Code**: Use `angular-developer`
- **Visual Design**: Use `frontend-design`
- **UI/UX Review**: Use `web-design-guidelines`

### Code Quality & Review
- **Code Review**: Use `code-review-expert`
- **Skill Review**: Use `skill-review`

### Project Management
- **AI-DLC Workflow**: Use `ai-dlc-orchestrator`
- **Requirements & Planning**: Use `ai-dlc-orchestrator`

---

## Skill Installation Status

✅ **Installed** (7 skills):
1. **angular-developer** - Angular development
2. **angular-new-app** - Angular project creation
3. **frontend-design** - Visual design & typography
4. **web-design-guidelines** - UI/UX review & accessibility
5. **code-review-expert** - Code review & security scan
6. **skill-review** - Skill quality audit
7. **ai-dlc-orchestrator** - AI-DLC workflow

⏳ **To Be Installed**:
- Backend Node.js skill (API, Express, NestJS)
- Database PostgreSQL skill (Schema, Prisma, migrations)
- DevOps Docker/CI/CD skill (Deployment, containers)

---

## Project Structure

```
.
├── .ai/                          # AI context và custom skills
│   ├── context/
│   │   └── project-context.md    # File này
│   ├── routing/
│   │   └── skill-routing.md      # Skill routing rules
│   └── skills/                   # Custom skills
│       └── ai-dlc-orchestrator/  # AI-DLC workflow skill
│
├── .kiro/                        # Kiro agent configuration
│   ├── skills/                   # Installed skills
│   │   ├── angular-developer/    # Angular development
│   │   ├── angular-new-app/      # Angular scaffolding
│   │   ├── frontend-design/      # Visual design
│   │   ├── web-design-guidelines/ # UI/UX review
│   │   ├── code-review-expert/   # Code review
│   │   └── skill-review/         # Skill audit
│   ├── steering/                 # Steering files
│   └── plans/                    # AI-DLC projects
│
└── skills-lock.json              # Skill version lock file
```

---

## Usage Guidelines

1. **Always read** `.ai/routing/skill-routing.md` before selecting skills
2. **Check installed skills** in this file to know what's available
3. **Follow skill selection policy** (AUTO, PREFERRED, FORCED, EXCLUSIVE)
4. **Don't modify installed skills** without explicit permission

---

## Notes

- Skills in `.kiro/skills/` are installed via npx skills add command
- Skills in `.ai/skills/` are custom/project-specific skills
- Skill routing is centralized in `.ai/routing/skill-routing.md`
- All skills should reference this context file for coordination
- Use `npx skills add <repo-url> --skill <skill-name>` to install new skills