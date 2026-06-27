# Steering Files Index (Deprecated Structure)

> **IMPORTANT:** Steering structure changed on 2026-06-27  
> Most content moved to `.kiro/skills/` - This index is for reference only

---

## New Architecture

**Steering files now minimal** - only 2 cross-cutting workflow files in `.kiro/steering/core/`:

| File | Purpose |
|------|---------|
| `ai-dlc-workflow.md` | AI-DLC project workflow (applies to all domains) |
| `ai-agent.md` | AI agent management (applies to all skills) |

**All skill knowledge moved to** `.kiro/skills/{domain}/{skill}/`:
- UI/UX Pro Max: ~90 files → `.kiro/skills/frontend/design/ui-ux-pro-max/references/`
- Angular skills: ~5 files → `.agents/skills/angular-*/`
- Future skills: grouped by domain (backend/, database/, mobile/, etc.)

---

## Current Steering Structure

```
.kiro/steering/
├── README.md              # Management guide (updated)
├── STEERING-INDEX.md      # This file (deprecated)
└── core/                  # Only 2 files
    ├── ai-agent.md
    └── ai-dlc-workflow.md
```

**Before restructure:** 90+ files in steering (unmanageable)  
**After restructure:** 2 files in steering, ~100+ organized in skills

---

## Migrated Content (2026-06-27)

All UI/UX Pro Max content moved from `.kiro/steering/` to `.kiro/skills/frontend/design/ui-ux-pro-max/references/`:

### Design Family (moved)
- ~~`.kiro/steering/design/`~~ → `.kiro/skills/frontend/design/ui-ux-pro-max/references/design/`
- ~~`.kiro/steering/brand/`~~ → `.kiro/skills/frontend/design/ui-ux-pro-max/references/brand/`
- ~~`.kiro/steering/design-system/`~~ → `.kiro/skills/frontend/design/ui-ux-pro-max/references/design-system/`
- ~~`.kiro/steering/slides/`~~ → `.kiro/skills/frontend/design/ui-ux-pro-max/references/slides/`
- ~~`.kiro/steering/banner-design/`~~ → `.kiro/skills/frontend/design/ui-ux-pro-max/references/banner-design/`
- ~~`.kiro/steering/ui-styling/`~~ → `.kiro/skills/frontend/design/ui-ux-pro-max/references/ui-styling/`

### Core Files (moved)
- ~~`.kiro/steering/ai-agent.md`~~ → `.kiro/steering/core/ai-agent.md`
- ~~`.kiro/steering/ai-dlc-workflow.md`~~ → `.kiro/steering/core/ai-dlc-workflow.md`

---

## Historical Statistics (Before Restructure)

| Category | Skills | Files | Scripts | Data Files |
|----------|--------|-------|---------|------------|
| Core | 2 | 2 | 0 | 0 |
| Design Family | 6 | ~60 | 9 | ~50 |
| UI/UX | 1 | ~20 | 3 | ~30 |
| Angular | 2 | ~5 | 0 | 0 |
| **Total** | **11** | **~90** | **12** | **~80** |

---

## New Statistics (After Restructure)

| Location | Files | Purpose |
|----------|-------|---------|
| `.kiro/steering/core/` | 2 | Cross-cutting workflows only |
| `.kiro/skills/frontend/design/ui-ux-pro-max/` | ~90 | UI/UX domain knowledge |
| `.agents/skills/angular-*` | ~10 | Angular framework skills |
| `.agents/skills/ai-dlc-*` | ~5 | Workflow orchestration |
| **Total** | **~107** | - |

---

## For Current File Locations

**See:** `.kiro/skills/readme.md` for updated skills organization

**Skills by domain:**
- Web: `.kiro/skills/web/`
- Backend: `.kiro/skills/backend/` (planned)
- Database: `.kiro/skills/database/` (planned)
- Mobile: `.kiro/skills/mobile/` (planned)
- Quality: `.kiro/skills/quality/` (planned)
- DevOps: `.kiro/skills/devops/` (planned)

---

*This index kept for historical reference only*  
*Last updated: 2026-06-27*  
*New structure: Skills-first, steering-minimal*
