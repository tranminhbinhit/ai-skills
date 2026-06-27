# AI Development Repository

## 🎯 Repository Overview

This repository contains **26 production-ready skills** organized across **7 domains** to accelerate AI-assisted development. Skills are auto-discovered by Kiro based on keywords - no manual configuration needed.

### Key Statistics
- **26 skills installed** (15 locked, 11 pending lock)
- **7 domains**: Frontend, Backend, Database, Quality, Documentation, Meta, Workflow
- **3 skill sources**: GitHub repos (24), Local (2)
- **100+ reference files** organized by domain

---

## 📁 Repository Structure

### AI-DLC Framework
```
.kiro/
├── plans/
│   ├── QUICKSTART.md           # Khởi động sử dụng
│   ├── readme.md               # Hướng dẫn AI-DLC
│   └── cr-ai-dlc-example/      # Plan mẫu
│
├── skills/                     # 26 skills organized by domain
│   ├── readme.md               # Skills management guide
│   ├── frontend/               # 7 frontend skills
│   │   ├── angular/            # Angular framework
│   │   ├── ui/                 # UI components (5 skills)
│   │   └── design/
│   │       └── ui-ux-pro-max/  # Comprehensive design system (~90 files)
│   ├── backend/                # 6 backend skills
│   ├── database/               # 5 database skills
│   ├── quality/                # 1 quality skill
│   ├── documentation/          # 4 doc skills
│   ├── meta/                   # 2 meta skills
│   └── workflow/               # 1 workflow skill
│
└── steering/
    └── core/
        ├── ai-agent.md         # AI agent management
        └── ai-dlc-workflow.md  # AI-DLC workflow
```

### Skills Documentation
```
document/
├── quick-install-guide.md              # 🔥 Start here
├── skills-roadmap.md                   # 32 planned skills
├── skills-vs-steering-architecture.md  # Architecture rationale
└── steering-management-summary.md      # Restructure summary
```

---

## 🎨 Installed Skills (26 Total)

### Frontend (7 skills) ✅
**Angular Framework:**
- **angular-developer** - Angular components, services, routing, signals
- **angular-new-app** - Scaffold new Angular applications

**UI Components & Quality:**
- **baseline-ui** - Modern UI components & interactions
- **fixing-accessibility** - WCAG compliance & a11y fixes
- **fixing-metadata** - SEO & Open Graph metadata
- **fixing-motion-performance** - Animation & motion optimization
- **ui-skills-root** - Umbrella skill for UI patterns

### Backend (6 skills) ⚠️
**Node.js Frameworks:**
- **express-developer** - Express.js REST API development
- **fastify-developer** - Fastify high-performance framework
- **nestjs-developer** - NestJS architecture & dependency injection

**Python Frameworks:**
- **django-developer** - Django ORM, admin, templates
- **fastapi-developer** - FastAPI async endpoints & Pydantic

**API Design:**
- **graphql-expert** - GraphQL schema, resolvers, queries

### Database (5 skills) ⚠️
- **postgresql-expert** - PostgreSQL design & queries (SQL)
- **mongodb-expert** - MongoDB schema & aggregation (NoSQL)
- **redis-expert** - Redis caching & pub/sub (NoSQL)
- **prisma-expert** - Prisma ORM & migrations (ORM)

### Quality (1 skill) ✅
- **code-review-expert** - Senior-level reviews (SOLID, security, performance)

### Documentation (4 skills) ✅
- **pdf** - PDF generation & processing
- **book-study** - Educational content creation
- **sigma** - Teaching & pedagogy patterns
- **wiki-ingest** - Knowledge base & wiki management

### Meta (2 skills) ✅
- **skill-forge** - Create new skills
- **skill-review** - Validate skill quality

### Workflow (1 skill) ✅
- **ai-dlc-orchestrator** - AI-DLC project workflow

### Legacy (1 skill)
- **ui-ux-pro-max** - Comprehensive design system (~90 files, to migrate)

**Status Legend:**
- ✅ Fully locked with version hash
- ⚠️ Installed but pending lock (11 skills need sync)

---

## 🤖 How Skills Work

Skills auto-activate based on keywords in your prompts. No manual configuration needed.

### Frontend Skills
| Keywords | Activates | Use For |
|----------|-----------|---------|
| angular, component, directive | angular-developer | Angular development |
| new app, create angular | angular-new-app | Scaffold Angular apps |
| button, modal, interaction | baseline-ui | Modern UI components |
| accessibility, a11y, WCAG | fixing-accessibility | Accessibility fixes |
| metadata, SEO, Open Graph | fixing-metadata | SEO & social tags |
| animation, performance, motion | fixing-motion-performance | Animation optimization |

### Backend Skills
| Keywords | Activates | Use For |
|----------|-----------|---------|
| express, middleware, REST API | express-developer | Express.js development |
| fastify, fast api, node | fastify-developer | Fastify framework |
| nestjs, dependency injection | nestjs-developer | NestJS architecture |
| django, ORM, admin | django-developer | Django framework |
| fastapi, pydantic, async | fastapi-developer | FastAPI development |
| graphql, schema, resolver | graphql-expert | GraphQL APIs |

### Database Skills
| Keywords | Activates | Use For |
|----------|-----------|---------|
| postgresql, postgres, SQL | postgresql-expert | PostgreSQL queries |
| mongodb, mongo, document | mongodb-expert | MongoDB schema |
| redis, cache, pub/sub | redis-expert | Redis caching |
| prisma, ORM, migration | prisma-expert | Prisma ORM |

### Other Skills
| Keywords | Activates | Use For |
|----------|-----------|---------|
| review, code quality, SOLID | code-review-expert | Code reviews |
| pdf, report, document | pdf | PDF processing |
| ai-dlc, inception, construction | ai-dlc-orchestrator | Project workflow |
| design, brand, ui/ux | ui-ux-pro-max | Design system |

---

## 📋 Next Steps & Priorities

### 🔴 Urgent (Week 1)
1. **Lock Backend/Database Skills** - Run sync script to update skills-lock.json for 11 unlocked skills
2. **Test All Skills** - Verify each skill activates with example prompts
3. **Update Documentation** - Ensure all READMEs reflect current state

### 🟡 Medium Priority (Weeks 2-4)
1. **Migrate ui-ux-pro-max** - Move from `web/` to `frontend/design/` domain
2. **Expand Roadmap** - Plan additional skills for DevOps, Mobile, Testing domains
3. **Performance Review** - Optimize large skill files, improve auto-discovery speed

### 🟢 Future Enhancements (Month 2+)
1. **Add DevOps Domain** - Docker, Kubernetes, CI/CD skills
2. **Mobile Development** - React Native, Flutter skills
3. **Advanced Testing** - E2E, performance, security testing skills

See [`document/skills-roadmap.md`](document/skills-roadmap.md) for detailed implementation plan.

---

## 🏗️ Architecture Overview

### Domains Structure (7 Domains)
```
.kiro/skills/
├── frontend/          # Web frontend (7 skills)
│   ├── angular/       # Angular framework
│   ├── ui/            # UI components & quality
│   └── design/        # Design systems
├── backend/           # Server-side (6 skills)
│   ├── nodejs/        # Express, Fastify, NestJS
│   ├── python/        # Django, FastAPI
│   └── api/           # GraphQL
├── database/          # Data layer (5 skills)
│   ├── sql/           # PostgreSQL
│   ├── nosql/         # MongoDB, Redis
│   └── orm/           # Prisma
├── quality/           # Code quality (1 skill)
│   └── code-review/   # Code review expert
├── documentation/     # Content (4 skills)
│   ├── pdf/
│   ├── book-study/
│   ├── sigma/
│   └── wiki-ingest/
├── meta/              # Skills tools (2 skills)
│   ├── skill-forge/
│   └── skill-review/
└── workflow/          # Process (1 skill)
    └── ai-dlc-orchestrator/
```

### Storage Pattern
- **`.kiro/skills/{domain}/`** - Junction/symlinks organized by domain
- **`.agents/skills/`** - Physical storage for GitHub-sourced skills
- **`skills-lock.json`** - Version lock with domain metadata (v2)

### Design Principles
1. **Skills-first architecture** - All domain knowledge in skills
2. **Minimal steering** - Only 2 cross-cutting workflow files
3. **Domain-driven organization** - Group by technology domain
4. **Auto-discovery** - Kiro detects skills via keywords automatically
5. **Separation of concerns** - Workflows vs domain expertise

Read more: [`document/skills-vs-steering-architecture.md`](document/skills-vs-steering-architecture.md)

---

## 📚 Documentation Index

| Document | Purpose | Status |
|----------|---------|--------|
| [`.kiro/skills/readme.md`](.kiro/skills/readme.md) | Complete skills catalog & management | ✅ Current |
| [`.kiro/steering/README.md`](.kiro/steering/README.md) | Minimal steering guide (2 files only) | ✅ Current |
| [`.kiro/plans/readme.md`](.kiro/plans/readme.md) | AI-DLC workflow documentation | ✅ Current |
| [`document/skills-roadmap.md`](document/skills-roadmap.md) | Future skills implementation plan | 📋 Planned |
| [`document/skills-vs-steering-architecture.md`](document/skills-vs-steering-architecture.md) | Architecture decision rationale | ✅ Current |
| [`document/steering-management-summary.md`](document/steering-management-summary.md) | Restructure summary (2026-06-27) | ✅ Current |
| [`skills-lock.json`](skills-lock.json) | Skills version lock (v2, domain-aware) | ⚠️ Needs sync |

---

## 🚀 Quick Start Guide

### For End Users (Get Coding in 5 Minutes)

1. **Test Installed Skills**
   ```bash
   # In Kiro, try these prompts:
   "create an angular component for user profile"      # → angular-developer
   "review this code for SOLID principles"             # → code-review-expert  
   "generate a PDF invoice"                            # → pdf
   "fix accessibility issues in this component"        # → fixing-accessibility
   ```

2. **Learn AI-DLC Workflow**
   - Read [`.kiro/plans/QUICKSTART.md`](.kiro/plans/QUICKSTART.md)
   - Try example project in `.kiro/plans/cr-ai-dlc-example/`

3. **Explore Skills**
   - See [`.kiro/skills/readme.md`](.kiro/skills/readme.md) for full skill catalog
   - Check [`document/skills-roadmap.md`](document/skills-roadmap.md) for future additions

### For Contributors (Extend the Repository)

1. **Understand Architecture**
   - Read [`document/skills-vs-steering-architecture.md`](document/skills-vs-steering-architecture.md)
   - Review skills-lock.json structure (v2, domain-aware)

2. **Add New Skills**
   ```bash
   # Option 1: Install from GitHub
   npx skills add https://github.com/{org}/{repo}
   
   # Option 2: Create local skill
   mkdir -p .kiro/skills/{domain}/{skill-name}
   # Follow template in .kiro/skills/readme.md
   ```

3. **Submit Changes**
   - Update skills-lock.json
   - Update documentation (this readme + .kiro/skills/readme.md)
   - Test skill activation with example prompts
   - Create PR with clear description

---

## 📊 Repository Statistics

### Skills by Domain
| Domain | Installed | Locked | Pending Lock | Coverage |
|--------|-----------|--------|--------------|----------|
| Frontend | 7 | 7 | 0 | ✅ 100% |
| Backend | 6 | 0 | 6 | ⚠️ 0% |
| Database | 5 | 0 | 5 | ⚠️ 0% |
| Quality | 1 | 1 | 0 | ✅ 100% |
| Documentation | 4 | 4 | 0 | ✅ 100% |
| Meta | 2 | 2 | 0 | ✅ 100% |
| Workflow | 1 | 1 | 0 | ✅ 100% |
| **TOTAL** | **26** | **15** | **11** | **58%** |

### Skills by Source
| Source Type | Count | Examples |
|-------------|-------|----------|
| GitHub | 24 | angular/skills, ibelick/ui-skills, anthropics/skills |
| Local | 2 | ai-dlc-orchestrator, ui-ux-pro-max |

### Steering Files (Minimal by Design)
| Location | Files | Purpose |
|----------|-------|---------|
| `.kiro/steering/core/` | 2 | Cross-cutting workflows only |
| `.kiro/skills/` | 100+ | All domain knowledge |

**Before restructure:** 90+ files in steering (unmanageable)  
**After restructure:** 2 workflow files, clean separation of concerns

---

## 🔍 Repository Metadata

**Version:** 2.0 (Post-restructure)  
**Last Updated:** 2026-06-27  
**Total Skills:** 26 installed (15 locked, 11 pending)  
**Total Domains:** 7 (Frontend, Backend, Database, Quality, Documentation, Meta, Workflow)  
**Architecture:** Skills-first, steering-minimal approach  
**Skills Lock Version:** v2 (domain-aware)

**Maintainer:** AI Development Team  
**License:** See individual skill licenses in respective SKILL.md files

