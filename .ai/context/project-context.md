# Project Context

## Installed Skills Registry

| Nhóm | Skill | Location | Dùng khi nào |
|---|---|---|---|
| Frontend | angular-developer | `.agents/skills/angular-developer/` | Angular components, forms, routing, signals, RxJS, UI, testing, CLI |
| Frontend | angular-new-app | `.agents/skills/angular-new-app/` | Create new Angular application, scaffold project |
| Frontend | frontend-design | `.agents/skills/frontend-design/` | Visual design, typography, palette, layout, distinctive UI, aesthetic direction |
| Frontend | web-design-guidelines | `.agents/skills/web-design-guidelines/` | UI review, accessibility audit, UX compliance, best practices check |
| Quality | code-review-expert | `.agents/skills/code-review-expert/` | Code review, SOLID principles, security scan, git diff analysis |
| Quality | skill-review | `.agents/skills/skill-review/` | Skill quality audit, skill validation, skill structure review |
| SDLC | ai-dlc-orchestrator | `.ai/skills/ai-dlc-orchestrator/` | AI-DLC workflow, Inception, Construction, Operations, UoW, requirements |
| Design | ui-ux-pro-max | `.ai/skills/ui-ux-pro-max/` | Design intelligence, palettes, typography, UX guidelines, stack-specific UI guidance |
| Design | design | `.ai/skills/design/` | Logo, CIP, icon, social image, slide, banner, and brand identity workflows |
| Design | banner-design | `.ai/skills/banner-design/` | Social, ads, website hero, and print banner design |
| Design | ui-styling | `.ai/skills/ui-styling/` | Tailwind, shadcn/ui, accessible UI implementation, themes, responsive layouts |
| Design | brand | `.ai/skills/brand/` | Brand voice, visual identity, messaging, asset management, brand consistency |
| Design | slides | `.ai/skills/slides/` | Strategic HTML presentations, Chart.js slides, responsive slide layouts |
| Design | design-system | `.ai/skills/design-system/` | Design tokens, component specs, token architecture, design-system slides |
| Design | ui-ux-pro-max-skill | `.ai/skills/ui-ux-pro-max-skill/` | Bundle index for discovering the UI/UX Pro Max skill suite |

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

### Advanced Design
- **Design Intelligence**: Use `ui-ux-pro-max`
- **Brand & Identity**: Use `brand`, `design`, or `design-system`
- **Banners & Slides**: Use `banner-design` or `slides`
- **UI Styling**: Use `ui-styling`

---

## Skill Installation Status

✅ **Installed** (15 skills):
1. **angular-developer** - Angular development
2. **angular-new-app** - Angular project creation
3. **frontend-design** - Visual design & typography
4. **web-design-guidelines** - UI/UX review & accessibility
5. **code-review-expert** - Code review & security scan
6. **skill-review** - Skill quality audit
7. **ai-dlc-orchestrator** - AI-DLC workflow
8. **ui-ux-pro-max** - Design intelligence database
9. **design** - Comprehensive design workflows
10. **banner-design** - Multi-format banner design
11. **ui-styling** - Tailwind and shadcn/ui styling
12. **brand** - Brand identity and messaging
13. **slides** - Strategic HTML presentations
14. **design-system** - Design tokens and component specs
15. **ui-ux-pro-max-skill** - UI/UX Pro Max bundle index

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
│       ├── ai-dlc-orchestrator/  # AI-DLC workflow skill
│       ├── ui-ux-pro-max/        # Symlink to UI/UX design intelligence skill
│       ├── design/               # Symlink to comprehensive design skill
│       ├── banner-design/        # Symlink to banner design skill
│       ├── ui-styling/           # Symlink to UI styling skill
│       ├── brand/                # Symlink to brand skill
│       ├── slides/               # Symlink to slides skill
│       ├── design-system/        # Symlink to design system skill
│       └── ui-ux-pro-max-skill/  # Source bundle for UI/UX skills
│
├── .agents/                      # Codex CLI installed skills
│   └── skills/
│       ├── angular-developer/    # Angular development
│       ├── angular-new-app/      # Angular scaffolding
│       ├── frontend-design/      # Visual design
│       ├── web-design-guidelines/ # UI/UX review
│       ├── code-review-expert/   # Code review
│       └── skill-review/         # Skill audit
│
├── .kiro/                        # Kiro agent configuration
│   ├── skills/                   # Compatibility symlinks to .agents/skills
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

- Installed skills for Codex live in `.agents/skills/`
- `.kiro/skills/` keeps compatibility symlinks for Kiro
- Skills in `.ai/skills/` are custom/project-specific skills and direct-child symlinks to custom skill bundles
- Skill routing is centralized in `.ai/routing/skill-routing.md`
- All skills should reference this context file for coordination
- Use `npx skills add <repo-url> --skill <skill-name>` to install new skills
