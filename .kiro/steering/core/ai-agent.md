# Available Skills in This Repo

Repo này có **25 skills** được tổ chức theo **7 domains** ✅

## Domains Overview

### 1. Frontend (7 skills) ✅
- **angular/**: angular-developer, angular-new-app
- **ui/**: baseline-ui, fixing-accessibility, fixing-metadata, fixing-motion-performance, ui-skills-root

### 2. Backend (6 skills) ✅
- **nodejs/**: express-developer, fastify-developer, nestjs-developer
- **python/**: django-developer, fastapi-developer
- **api/**: graphql-expert

### 3. Database (5 skills) ✅
- **sql/**: postgresql-expert
- **nosql/**: mongodb-expert, redis-expert
- **orm/**: prisma-expert

### 4. Quality (1 skill) ✅
- **code-review/**: code-review-expert

### 5. Documentation (4 skills) ✅
- pdf, book-study, sigma, wiki-ingest

### 6. Meta (2 skills) ✅
- skill-forge, skill-review

### 7. Workflow (1 skill) ✅
- ai-dlc-orchestrator

## How Skills Work

Skills tự động activate khi Kiro detect keywords trong user query.

**Examples:**
- "angular component" → `angular-developer` activates
- "review this code" → `code-review-expert` activates
- "mongodb schema" → `mongodb-expert` activates
- "create PDF" → `pdf` skill activates

Không cần khai báo thủ công - Kiro auto-discover via `discloseContext` tool.

## Skills Location

```
.kiro/skills/               ← Organized by domain (junction links)
├── frontend/
│   ├── angular/            ← 2 skills
│   └── ui/                 ← 5 skills
├── backend/
│   ├── nodejs/             ← 3 skills
│   ├── python/             ← 2 skills
│   └── api/                ← 1 skill
├── database/
│   ├── sql/                ← 1 skill
│   ├── nosql/              ← 2 skills
│   └── orm/                ← 1 skill
├── quality/code-review/    ← 1 skill
├── documentation/          ← 4 skills
├── meta/                   ← 2 skills
└── workflow/               ← 1 skill

.agents/skills/             ← Physical storage (from GitHub/local)
```

**Junction links** (Windows) point from `.kiro/skills/{domain}/` to `.agents/skills/`

## Migration Status ✅

✅ **Migration Complete** (2026-06-27)
- ✅ Domain structure created (7 domains)
- ✅ 25 skills organized and linked
- ✅ skills-lock.json updated to v2
- ✅ All links verified working
- ✅ Duplicates removed

See `.kiro/skills/readme.md` for detailed documentation.
