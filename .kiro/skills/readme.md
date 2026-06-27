# Skills Management

## Overview

This repository uses Kiro's skills system to organize domain expertise. Skills are discovered automatically via `discloseContext` tool - no manual declaration needed.

## Architecture (Updated 2026-06-27)

**Clear Separation:**
- **Skills** (`.kiro/skills/`) = Domain knowledge + tools + references
- **Steering** (`.kiro/steering/core/`) = Cross-cutting workflows only (2 files)

All skill-specific knowledge stays in skills folders. Steering is minimal.

## Skills Location

```
.kiro/skills/                          ← Organized by domain (junction/symlinks)
├── frontend/                          # Web frontend technologies
│   ├── angular/                       # Angular framework family
│   │   ├── angular-developer/
│   │   └── angular-new-app/
│   └── ui/                            # UI components & patterns
│       ├── baseline-ui/
│       ├── fixing-accessibility/
│       ├── fixing-metadata/
│       ├── fixing-motion-performance/
│       └── ui-skills-root/
├── backend/                           # Server-side development
│   ├── nodejs/                        # Node.js frameworks
│   │   ├── express-developer/
│   │   ├── fastify-developer/
│   │   └── nestjs-developer/
│   ├── python/                        # Python frameworks
│   │   ├── django-developer/
│   │   └── fastapi-developer/
│   └── api/                           # API design patterns
│       └── graphql-expert/
├── database/                          # Data layer technologies
│   ├── sql/
│   │   └── postgresql-expert/
│   ├── nosql/
│   │   ├── mongodb-expert/
│   │   └── redis-expert/
│   └── orm/
│       └── prisma-expert/
├── quality/                           # Code quality & testing
│   └── code-review/
│       └── code-review-expert/
├── documentation/                     # Content creation
│   ├── pdf/
│   ├── book-study/
│   ├── sigma/
│   └── wiki-ingest/
├── meta/                              # Skills about skills
│   ├── skill-forge/
│   └── skill-review/
├── workflow/                          # Process & orchestration
│   └── ai-dlc-orchestrator/
└── web/                               # Legacy: to be migrated
    └── ui-ux-pro-max/                 # Design, brand, UI/UX (~90 files)

.agents/skills/                        ← Physical storage (GitHub skills)
skills-lock.json                       ← Version control v2 (domain-aware)
```

**Windows:** `.kiro/skills/{domain}/` uses junction links pointing to `.agents/skills/`  
**Unix/Mac:** `.kiro/skills/{domain}/` uses symbolic links pointing to `.agents/skills/`

---

## 🎯 Current Skills (25 total)

### Frontend (7 skills)

#### Angular Framework
1. **angular-developer** - Angular development expertise  
   📍 `.kiro/skills/frontend/angular/angular-developer/`  
   🔗 Source: angular/skills

2. **angular-new-app** - Create new Angular apps  
   📍 `.kiro/skills/frontend/angular/angular-new-app/`  
   🔗 Source: angular/skills

#### UI Components & Quality
3. **baseline-ui** - Modern UI components & interactions  
   📍 `.kiro/skills/frontend/ui/baseline-ui/`  
   🔗 Source: ibelick/ui-skills

4. **fixing-accessibility** - WCAG compliance & a11y fixes  
   📍 `.kiro/skills/frontend/ui/fixing-accessibility/`  
   🔗 Source: ibelick/ui-skills

5. **fixing-metadata** - SEO & Open Graph metadata  
   📍 `.kiro/skills/frontend/ui/fixing-metadata/`  
   🔗 Source: ibelick/ui-skills

6. **fixing-motion-performance** - Animation & motion optimization  
   📍 `.kiro/skills/frontend/ui/fixing-motion-performance/`  
   🔗 Source: ibelick/ui-skills

7. **ui-skills-root** - Umbrella skill for UI patterns  
   📍 `.kiro/skills/frontend/ui/ui-skills-root/`  
   🔗 Source: ibelick/ui-skills

### Backend (6 skills)

#### Node.js Frameworks
8. **express-developer** - Express.js backend development  
   📍 `.kiro/skills/backend/nodejs/express-developer/`  
   ⚠️ Status: Installed (not locked)

9. **fastify-developer** - Fastify framework expertise  
   📍 `.kiro/skills/backend/nodejs/fastify-developer/`  
   ⚠️ Status: Installed (not locked)

10. **nestjs-developer** - NestJS architecture & patterns  
    📍 `.kiro/skills/backend/nodejs/nestjs-developer/`  
    ⚠️ Status: Installed (not locked)

#### Python Frameworks
11. **django-developer** - Django framework development  
    📍 `.kiro/skills/backend/python/django-developer/`  
    ⚠️ Status: Installed (not locked)

12. **fastapi-developer** - FastAPI async framework  
    📍 `.kiro/skills/backend/python/fastapi-developer/`  
    ⚠️ Status: Installed (not locked)

#### API Design
13. **graphql-expert** - GraphQL schema & resolvers  
    📍 `.kiro/skills/backend/api/graphql-expert/`  
    ⚠️ Status: Installed (not locked)

### Database (5 skills)

#### SQL
14. **postgresql-expert** - PostgreSQL design & queries  
    📍 `.kiro/skills/database/sql/postgresql-expert/`  
    ⚠️ Status: Installed (not locked)

#### NoSQL
15. **mongodb-expert** - MongoDB schema & aggregation  
    📍 `.kiro/skills/database/nosql/mongodb-expert/`  
    ⚠️ Status: Installed (not locked)

16. **redis-expert** - Redis caching & pub/sub  
    📍 `.kiro/skills/database/nosql/redis-expert/`  
    ⚠️ Status: Installed (not locked)

#### ORM
17. **prisma-expert** - Prisma ORM & migrations  
    📍 `.kiro/skills/database/orm/prisma-expert/`  
    ⚠️ Status: Installed (not locked)

### Quality (1 skill)

18. **code-review-expert** - Senior-level code reviews (SOLID, security, performance)  
    📍 `.kiro/skills/quality/code-review/code-review-expert/`  
    🔗 Source: sanyuan0704/code-review-expert

### Documentation (4 skills)

19. **pdf** - PDF generation & processing  
    📍 `.kiro/skills/documentation/pdf/`  
    🔗 Source: anthropics/skills

20. **book-study** - Educational content creation  
    📍 `.kiro/skills/documentation/book-study/`  
    🔗 Source: sanyuan0704/code-review-expert

21. **sigma** - Teaching & pedagogy patterns  
    📍 `.kiro/skills/documentation/sigma/`  
    🔗 Source: sanyuan0704/code-review-expert

22. **wiki-ingest** - Knowledge base & wiki management  
    📍 `.kiro/skills/documentation/wiki-ingest/`  
    🔗 Source: sanyuan0704/code-review-expert

### Meta (2 skills)

23. **skill-forge** - Create new skills  
    📍 `.kiro/skills/meta/skill-forge/`  
    🔗 Source: sanyuan0704/code-review-expert

24. **skill-review** - Validate skill quality  
    📍 `.kiro/skills/meta/skill-review/`  
    🔗 Source: sanyuan0704/code-review-expert

### Workflow (1 skill)

25. **ai-dlc-orchestrator** - AI-DLC project workflow  
    📍 `.kiro/skills/workflow/ai-dlc-orchestrator/`  
    🔗 Source: local

### Legacy (to be migrated)

**ui-ux-pro-max** - Comprehensive design system (~90 files)  
📍 `.kiro/skills/frontend/design/ui-ux-pro-max/`  
✅ Migrated to `frontend/design/` domain

---

## ✅ Recently Installed (All skills from hot list)

All 3 recommended skills are now installed:

1. ✅ **ui-skills** (ibelick/ui-skills) - 5 UI skills active
2. ✅ **pdf** (anthropics/skills) - PDF processing active
3. ✅ **code-review-expert** (sanyuan0704/code-review-expert) - 5 skills active

---

## 📋 Planned Skills (29)

See `document/skills-roadmap.md` for detailed roadmap with 15-week implementation plan (includes Phase 0 for ready skills).

### Backend Development (4)
- [ ] nodejs-developer
- [ ] nodejs-new-app
- [ ] api-design
- [ ] microservices-architect

### Database & Data (5)
- [ ] database-design
- [ ] sql-expert
- [ ] database-migration
- [ ] nosql-expert
- [ ] orm-expert

### Documentation (3)
- [ ] technical-writer
- [ ] diagram-generator
- [ ] api-documentation

### Code Quality (5)
- [ ] code-reviewer
- [ ] refactoring-expert
- [ ] test-engineer
- [ ] performance-optimizer
- [ ] security-auditor

### DevOps (6)
- [ ] docker-expert
- [ ] kubernetes-deployer
- [ ] cicd-engineer
- [ ] infrastructure-as-code
- [ ] monitoring-observability
- [ ] cloud-architect

### Frontend (3)
- [ ] react-developer
- [ ] ui-ux-developer (separate from ui-ux-pro-max)
- [ ] frontend-performance

### Management (3)
- [ ] agile-coach
- [ ] tech-lead
- [ ] product-analyst

---

## 🚀 How to Add New Skill

### Option 1: Install from GitHub

```bash
# Install skill (auto-manages .agents/skills/ and .kiro/skills/)
npx skills add https://github.com/{org}/{repo}

# For specific skill in multi-skill repo:
npx skills add https://github.com/{org}/{repo} --skill {skill-name}

# Updates skills-lock.json automatically
```

### Option 2: Create Local Skill

```bash
# 1. Create in appropriate domain folder
mkdir -p .kiro/skills/{domain}/{skill-name}

# 2. Create SKILL.md
cat > .kiro/skills/{domain}/{skill-name}/SKILL.md << 'EOF'
---
name: skill-name
description: Brief description
keywords: keyword1, keyword2, keyword3
license: MIT
metadata:
  author: Your Name
  version: '1.0'
---

# Skill Name

## When to Use
[Describe when this skill activates]

## Core Capabilities
[List main features]
EOF

# 3. Add references/ folder if needed
mkdir -p .kiro/skills/{domain}/{skill-name}/references

# 4. Update skills-lock.json (manual entry for local skills)
```

### Checklist After Adding Skill

- [ ] Skill files created/downloaded
- [ ] Update `skills-lock.json`
- [ ] Update this readme (Current Skills section)
- [ ] Test activation: mention skill keywords in Kiro
- [ ] Verify skill shows in `discloseContext` tool list
- [ ] Document any special setup requirements

---

## 🔧 Skill Structure

### Remote Skill (from GitHub)
```
.agents/skills/{skill-name}/
├── SKILL.md                    ← Main content
├── references/                 ← Knowledge base (optional)
│   ├── topic-1.md
│   └── topic-2.md
├── data/                       ← Datasets (optional)
└── scripts/                    ← Tools (optional)

.kiro/skills/{domain}/{skill-name} → Junction/symlink to above
```

### Local Skill
```
.kiro/skills/{domain}/{skill-name}/
├── SKILL.md                    ← Main content
├── references/                 ← Knowledge base
├── data/                       ← Datasets
└── scripts/                    ← Tools
```

### Domain Organization

Group skills by domain to manage complexity:

| Domain | Purpose | Example Skills |
|--------|---------|----------------|
| `web/` | Frontend, UI/UX, web tech | ui-ux-pro-max, react-developer |
| `backend/` | Server-side, APIs | nodejs-developer, api-design |
| `database/` | Data modeling, queries | postgres-expert, mongodb-expert |
| `mobile/` | Mobile development | react-native, flutter |
| `quality/` | Testing, review, security | test-engineer, code-reviewer |
| `devops/` | Infrastructure, deployment | docker-expert, k8s-deployer |
| Root level | Workflow, management | ai-dlc-orchestrator |

---

## 📝 Skill Format Template

```markdown
---
name: skill-name
description: One-line description
keywords: keyword1, keyword2, keyword3
license: MIT
metadata:
  author: Author Name
  version: '1.0'
---

# Skill Name

Brief introduction of what this skill does.

## When to Use

- User mentions [specific keywords]
- Working with [specific file types]
- Task involves [specific scenarios]

## Core Capabilities

1. Capability 1
2. Capability 2
3. Capability 3

## Best Practices

- Practice 1
- Practice 2

## Quick Reference

| Task | Command/Pattern |
|------|-----------------|
| Task 1 | `example` |

## References

- [Link 1](url)
- [Link 2](url)
```

---

## 🔍 How Kiro Discovers Skills

1. **Scan** `.kiro/skills/` and `.agents/skills/` for SKILL.md files
2. **Read** `skills-lock.json` for metadata
3. **Parse** frontmatter in SKILL.md for keywords
4. **List** in `discloseContext` tool as available skills
5. **Auto-activate** when keywords detected in user query

**No manual declaration needed** - skills auto-discovered by Kiro.

---

## 🔧 Steering vs Skills

After restructure (2026-06-27):

### Steering (`.kiro/steering/core/`) - Minimal, cross-cutting only
- `ai-dlc-workflow.md` - Project workflow (applies to all domains)
- `ai-agent.md` - Agent management (applies to all skills)

**Total: 2 files**

### Skills (`.kiro/skills/`) - All domain knowledge
- frontend/design/ui-ux-pro-max/ - ~90 files (design, brand, UI references)
- angular-developer/, angular-new-app/, ai-dlc-orchestrator/ - ~5 files each
- Future skills grouped by domain

**Total: ~100+ files, organized by domain**

**See:** `.kiro/steering/README.md` for steering management details

---

## 🐛 Troubleshooting

### Skill not showing in Kiro
- [ ] Check SKILL.md has valid frontmatter with keywords
- [ ] Verify skills-lock.json entry exists
- [ ] Check file is in `.kiro/skills/` or `.agents/skills/`
- [ ] Restart Kiro or reconnect MCP servers

### Skill not activating
- [ ] Verify keywords in frontmatter match user input
- [ ] Check skill listed in `discloseContext` tool
- [ ] Try explicit: "use {skill-name} skill"

### Junction link broken (Windows)
```bash
# Recreate junction link
cmd /c mklink /J ".kiro\skills\{domain}\{skill}" ".agents\skills\{skill}"
```

### Too many files in one skill
- Break into sub-skills with clear domains
- Use references/ folder for knowledge organization
- Keep SKILL.md concise, details in references/

---

## 📊 Skills Statistics

| Domain | Installed | Locked | Not Locked | Coverage |
|--------|-----------|--------|------------|----------|
| Frontend | 7 | 7 | 0 | ✅ 100% |
| Backend | 6 | 0 | 6 | ⚠️ 0% |
| Database | 5 | 0 | 5 | ⚠️ 0% |
| Quality | 1 | 1 | 0 | ✅ 100% |
| Documentation | 4 | 4 | 0 | ✅ 100% |
| Meta | 2 | 2 | 0 | ✅ 100% |
| Workflow | 1 | 1 | 0 | ✅ 100% |
| **TOTAL** | **26** | **15** | **11** | **58%** |

### Status Breakdown
- **Locked (15)**: Registered in skills-lock.json with hash
- **Not Locked (11)**: Installed but missing skills-lock.json entry
  - Need to run: `npx skills sync` to update lock file

### Priority Actions
1. 🔴 **Urgent**: Lock 11 backend/database skills (run sync script)
2. 🟡 **Medium**: Migrate ui-ux-pro-max to frontend/design/
3. 🟢 **Low**: Add devops domain skills (planned)

---

## 🎯 Quick Start - Migration Required

### Step 1: Run Migration Script (5 minutes)

Your skills are installed but not organized. Run migration:

**Windows (PowerShell):**
```powershell
cd .kiro/skills
.\migrate-skills-structure.ps1 -DryRun  # Preview changes
.\migrate-skills-structure.ps1           # Apply changes
```

**Unix/Mac (Bash):**
```bash
cd .kiro/skills
chmod +x migrate-skills-structure.sh
./migrate-skills-structure.sh --dry-run  # Preview changes
./migrate-skills-structure.sh            # Apply changes
```

### Step 2: Sync skills-lock.json

```bash
# Update lock file with new domain structure
cp skills-lock-updated.json skills-lock.json

# Or manually sync (if tool available)
npx skills sync
```

### Step 3: Test Your Skills

```bash
# Verify skills are organized by domain
ls .kiro/skills/frontend/angular/
ls .kiro/skills/backend/nodejs/
ls .kiro/skills/database/sql/

# Test in Kiro
# Type: "show me available skills"
# Type: "use angular-developer skill"
# Type: "review this code with code-review-expert"
```

---

## 🎯 Additional Skills to Install

### For Web/Frontend Projects
```bash
npx skills add https://github.com/vercel-labs/agent-skills --skill web-design-guidelines
npx skills add https://github.com/anthropics/skills --skill frontend-design
```

### For Backend Projects
```bash
# Coming soon - check skills-roadmap.md for planned skills
```

### For DevOps
```bash
# Coming soon - check skills-roadmap.md for planned skills
```

---

## 📚 Related Documentation

- `document/skills-roadmap.md` - Detailed 14-week implementation plan
- `document/skills-vs-steering-architecture.md` - Architecture decision rationale
- `document/steering-management-summary.md` - Restructure summary
- `skills-lock.json` - Skills version lock (like package-lock.json)
- `.kiro/steering/README.md` - Minimal steering management
- Root `readme.md` - Project overview

---

*Last updated: 2026-06-27*  
*Architecture: Skills-first, steering-minimal approach*
