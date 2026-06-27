# Steering Files Management Guide

## Architecture Decision (2026-06-27)

**Steering files ONLY for cross-cutting workflows.** Skill-specific knowledge moved to `.kiro/skills/`.

## Cấu trúc tổ chức

```
.kiro/steering/
├── README.md                    # Hướng dẫn này (minimal)
├── STEERING-INDEX.md            # Index (deprecated, check skills instead)
│
└── core/                        # Cross-cutting workflow files ONLY
    ├── ai-agent.md              # AI agents management (applies to all skills)
    └── ai-dlc-workflow.md       # AI-DLC workflow (applies to all projects)
```

**Skill-specific knowledge** is in:
```
.kiro/skills/
├── web/
│   └── ui-ux-pro-max/
│       ├── SKILL.md
│       ├── references/          # 90+ domain knowledge files HERE
│       │   ├── design/
│       │   ├── brand/
│       │   ├── design-system/
│       │   ├── slides/
│       │   ├── banner-design/
│       │   └── ui-styling/
│       ├── data/
│       └── scripts/
├── backend/                     # Future: fastify/, nestjs/, etc.
├── database/                    # Future: postgres/, mongodb/, etc.
└── mobile/                      # Future: react-native/, flutter/, etc.
```

## Quy tắc tổ chức

### 1. Separation of Concerns

**`.kiro/steering/core/`** - Cross-cutting workflows only:
- `ai-dlc-workflow.md` - Applies to all projects regardless of tech stack
- `ai-agent.md` - Agent management applies to all domains

**`.kiro/skills/{domain}/{skill}/`** - Domain-specific knowledge:
- Each skill has SKILL.md + references/ + scripts/
- Grouped by domain: web/, backend/, database/, mobile/, quality/
- Skills are self-contained with all their knowledge

### 2. Core vs Skill-specific
- **Core steering** (`.kiro/steering/core/`): Workflow files that apply across ALL skills and projects
- **Skill knowledge** (`.kiro/skills/`): Domain expertise, references, data files specific to one skill

### 3. When to Add to Steering vs Skills

**Add to `.kiro/steering/core/`** only if:
- Applies to ALL projects (web, backend, mobile, etc.)
- Is a workflow/process, not domain knowledge
- Examples: git workflow, coding standards, AI-DLC process

**Add to `.kiro/skills/{domain}/{skill}/`** if:
- Specific to one technology/domain (React, Node.js, Postgres, etc.)
- Contains domain knowledge, best practices, references
- Has scripts, data files, templates
- Examples: UI/UX patterns, database schemas, API design

### 4. Auto-inclusion Strategy
Kiro auto-discovers and activates skills via `discloseContext` tool based on keywords in user queries.

Steering files in `core/` are always included.

## Quản lý khi thêm skill mới

### Khi install skill mới từ GitHub:

**Skill knowledge → `.kiro/skills/{domain}/{skill}/`**
```bash
# Skill auto-installs to .kiro/skills/{domain}/{skill}/
# All references, data, scripts stay in skill folder
# NO files go to .kiro/steering/
```

**Only add to `.kiro/steering/core/`** if:
- It's a cross-project workflow (like ai-dlc-workflow.md)
- Applies to ALL domains, not just one skill

### Khi tạo skill local:

1. Tạo folder: `.kiro/skills/{domain}/{skill-name}/`
2. Tạo `SKILL.md` với metadata
3. Tạo `references/` cho knowledge base
4. Tạo `scripts/` nếu cần automation
5. Update `skills-lock.json`
6. **DO NOT** add anything to `.kiro/steering/` unless it's cross-cutting workflow

## Best Practices

### ✅ DO:
- Keep steering minimal - only cross-cutting workflows
- Put skill knowledge in `.kiro/skills/{domain}/{skill}/`
- Group skills by domain (web/, backend/, database/)
- Keep SKILL.md concise, details in references/

### ❌ DON'T:
- Put skill-specific knowledge in `.kiro/steering/`
- Duplicate knowledge across skills
- Hardcode paths in steering files
- Git ignore skill files (they need version control)

## Monitoring & Cleanup

### Check active files:
```bash
# Core workflows only
ls .kiro/steering/core/

# Skill knowledge
ls .kiro/skills/frontend/design/ui-ux-pro-max/references/
```

### Archive unused skills:
```bash
# Move entire skill to archive
mkdir -p .kiro/skills/archived/
mv .kiro/skills/web/{unused-skill}/ .kiro/skills/archived/
```

## Statistics (After Restructure)

| Category | Files in Steering | Files in Skills | Status |
|----------|------------------|-----------------|--------|
| Core workflows | 2 | - | ✅ Active |
| UI/UX Pro Max | 0 | ~90 | ✅ Restructured |
| Angular | 0 | ~5 | ✅ Active |
| Planned skills | 0 | TBD | 📋 Roadmap |
| **Total** | **2** | **~95** | - |

**Before restructure:** 90+ files in `.kiro/steering/` (unmanageable)
**After restructure:** 2 core files in `.kiro/steering/`, all skill knowledge in `.kiro/skills/` (clean separation)

## Troubleshooting

### Issue: Too many steering files active cùng lúc
**Solution**: Config `inclusion: manual` cho non-essential references

### Issue: Skill conflicts (duplicate functionality)
**Solution**: Consolidate vào single skill family, dùng sub-skills

### Issue: Slow context loading
**Solution**: 
- Move large data files ra khỏi steering/
- Dùng external references (URLs)
- Split large SKILL.md thành references/

---

**Last updated**: 2025-06-27  
**Maintained by**: AI Development Team
