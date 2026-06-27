# Skills Organization Plan for Multi-Domain Repository

## Current State Analysis

### Problems Identified
1. **No domain grouping** - All skills flat in `.agents/skills/`
2. **Inconsistent sources** - Mix of GitHub repos with overlapping content
3. **skills-lock.json chaos** - Skills from same repo scattered
4. **Duplicate functionality** - Multiple skills doing similar things
5. **No clear taxonomy** - Hard to find relevant skills

### Current Skills Inventory (15 total)

| Skill | Source Repo | Domain | Status |
|-------|-------------|--------|--------|
| ai-dlc-orchestrator | local | workflow | ✅ Keep |
| angular-developer | angular/skills | frontend | ✅ Keep |
| angular-new-app | angular/skills | frontend | ✅ Keep |
| baseline-ui | ibelick/ui-skills | frontend | ✅ Keep |
| book-study | sanyuan0704/code-review-expert | documentation | ⚠️ Review |
| code-review-expert | sanyuan0704/code-review-expert | quality | ✅ Keep |
| fixing-accessibility | ibelick/ui-skills | quality | ✅ Keep |
| fixing-metadata | ibelick/ui-skills | quality | ✅ Keep |
| fixing-motion-performance | ibelick/ui-skills | quality | ✅ Keep |
| pdf | anthropics/skills | documentation | ✅ Keep |
| sigma | sanyuan0704/code-review-expert | documentation | ⚠️ Review |
| skill-forge | sanyuan0704/code-review-expert | meta | ✅ Keep |
| skill-review | sanyuan0704/code-review-expert | meta | ✅ Keep |
| ui-skills-root | ibelick/ui-skills | frontend | ⚠️ Consolidate |
| wiki-ingest | sanyuan0704/code-review-expert | documentation | ⚠️ Review |

### Missing Framework Skills (Installed but not in lock)
From file tree scan:
- django-developer (backend/python)
- express-developer (backend/nodejs)
- fastapi-developer (backend/python)
- fastify-developer (backend/nodejs)
- graphql-expert (backend/api)
- mongodb-expert (database/nosql)
- nestjs-developer (backend/nodejs)
- postgresql-expert (database/sql)
- prisma-expert (database/orm)
- redis-expert (database/cache)

---

## Proposed Organization Structure

### Domain-Based Taxonomy

```
.kiro/skills/
├── frontend/                          # Web frontend technologies
│   ├── angular/                       # Angular framework family
│   │   ├── angular-developer/
│   │   └── angular-new-app/
│   └── ui/                            # UI components & patterns
│       ├── baseline-ui/
│       ├── fixing-accessibility/
│       ├── fixing-metadata/
│       ├── fixing-motion-performance/
│       └── ui-skills-root/            # Umbrella for UI skills
│
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
│
├── database/                          # Data layer
│   ├── sql/                           # SQL databases
│   │   └── postgresql-expert/
│   ├── nosql/                         # NoSQL databases
│   │   ├── mongodb-expert/
│   │   └── redis-expert/
│   └── orm/                           # ORMs & data access
│       └── prisma-expert/
│
├── quality/                           # Code quality & testing
│   ├── code-review/
│   │   └── code-review-expert/
│   └── accessibility/                 # Already covered in frontend/ui/
│
├── documentation/                     # Content creation
│   ├── pdf/
│   ├── book-study/
│   ├── sigma/                         # Educational content
│   └── wiki-ingest/
│
├── meta/                              # Skills about skills
│   ├── skill-forge/
│   └── skill-review/
│
└── workflow/                          # Process & orchestration
    └── ai-dlc-orchestrator/
```

### Physical Storage (unchanged)

```
.agents/skills/                        # Actual files (from GitHub/local)
├── angular-developer/
├── baseline-ui/
├── [all other skills...]
└── ...

.kiro/skills/{domain}/{skill}/         # Junction links (Windows) or symlinks (Unix)
```

---

## Migration Steps

### Phase 1: Create Domain Structure (NOW)

Create domain folders:
```bash
mkdir -p .kiro/skills/frontend/angular
mkdir -p .kiro/skills/frontend/ui
mkdir -p .kiro/skills/backend/nodejs
mkdir -p .kiro/skills/backend/python
mkdir -p .kiro/skills/backend/api
mkdir -p .kiro/skills/database/sql
mkdir -p .kiro/skills/database/nosql
mkdir -p .kiro/skills/database/orm
mkdir -p .kiro/skills/quality/code-review
mkdir -p .kiro/skills/documentation
mkdir -p .kiro/skills/meta
mkdir -p .kiro/skills/workflow
```

### Phase 2: Create Junction Links/Symlinks

**Windows (use cmd):**
```cmd
REM Frontend - Angular
mklink /J ".kiro\skills\frontend\angular\angular-developer" ".agents\skills\angular-developer"
mklink /J ".kiro\skills\frontend\angular\angular-new-app" ".agents\skills\angular-new-app"

REM Frontend - UI
mklink /J ".kiro\skills\frontend\ui\baseline-ui" ".agents\skills\baseline-ui"
mklink /J ".kiro\skills\frontend\ui\fixing-accessibility" ".agents\skills\fixing-accessibility"
mklink /J ".kiro\skills\frontend\ui\fixing-metadata" ".agents\skills\fixing-metadata"
mklink /J ".kiro\skills\frontend\ui\fixing-motion-performance" ".agents\skills\fixing-motion-performance"
mklink /J ".kiro\skills\frontend\ui\ui-skills-root" ".agents\skills\ui-skills-root"

REM Backend - Node.js
mklink /J ".kiro\skills\backend\nodejs\express-developer" ".agents\skills\express-developer"
mklink /J ".kiro\skills\backend\nodejs\fastify-developer" ".agents\skills\fastify-developer"
mklink /J ".kiro\skills\backend\nodejs\nestjs-developer" ".agents\skills\nestjs-developer"

REM Backend - Python
mklink /J ".kiro\skills\backend\python\django-developer" ".agents\skills\django-developer"
mklink /J ".kiro\skills\backend\python\fastapi-developer" ".agents\skills\fastapi-developer"

REM Backend - API
mklink /J ".kiro\skills\backend\api\graphql-expert" ".agents\skills\graphql-expert"

REM Database - SQL
mklink /J ".kiro\skills\database\sql\postgresql-expert" ".agents\skills\postgresql-expert"

REM Database - NoSQL
mklink /J ".kiro\skills\database\nosql\mongodb-expert" ".agents\skills\mongodb-expert"
mklink /J ".kiro\skills\database\nosql\redis-expert" ".agents\skills\redis-expert"

REM Database - ORM
mklink /J ".kiro\skills\database\orm\prisma-expert" ".agents\skills\prisma-expert"

REM Quality
mklink /J ".kiro\skills\quality\code-review\code-review-expert" ".agents\skills\code-review-expert"

REM Documentation
mklink /J ".kiro\skills\documentation\pdf" ".agents\skills\pdf"
mklink /J ".kiro\skills\documentation\book-study" ".agents\skills\book-study"
mklink /J ".kiro\skills\documentation\sigma" ".agents\skills\sigma"
mklink /J ".kiro\skills\documentation\wiki-ingest" ".agents\skills\wiki-ingest"

REM Meta
mklink /J ".kiro\skills\meta\skill-forge" ".agents\skills\skill-forge"
mklink /J ".kiro\skills\meta\skill-review" ".agents\skills\skill-review"

REM Workflow
mklink /J ".kiro\skills\workflow\ai-dlc-orchestrator" ".agents\skills\ai-dlc-orchestrator"
```

**Unix/Mac (use bash):**
```bash
# Similar but use ln -s instead
ln -s ../../../.agents/skills/angular-developer .kiro/skills/frontend/angular/angular-developer
# ... etc
```

### Phase 3: Update skills-lock.json

Add domain metadata to each skill:
```json
{
  "version": 1,
  "domains": {
    "frontend": ["angular", "ui"],
    "backend": ["nodejs", "python", "api"],
    "database": ["sql", "nosql", "orm"],
    "quality": ["code-review"],
    "documentation": [],
    "meta": [],
    "workflow": []
  },
  "skills": {
    "angular-developer": {
      "source": "angular/skills",
      "sourceType": "github",
      "domain": "frontend",
      "subdomain": "angular",
      "skillPath": "angular-developer/SKILL.md",
      "computedHash": "dc0d00affef561cd0181f5e2c38723fe645a1ecef591655d2b03ad95685812c9"
    }
    // ... etc
  }
}
```

### Phase 4: Update Documentation

1. Update `.kiro/skills/readme.md` with new structure
2. Update `.kiro/steering/core/ai-agent.md` with skill list
3. Create domain-specific README files

---

## Best Practices for Multi-Domain Repo

### 1. Domain Boundaries
- **Frontend**: UI, components, client-side logic
- **Backend**: APIs, business logic, server-side
- **Database**: Data modeling, queries, migrations
- **Quality**: Testing, review, security, accessibility
- **Documentation**: Content creation, diagrams, reports
- **Meta**: Skills for managing skills
- **Workflow**: Cross-cutting processes (AI-DLC, CI/CD)

### 2. Skill Naming Convention
```
{domain}/{subdomain?}/{skill-name}/
```
Examples:
- `frontend/angular/angular-developer/`
- `backend/nodejs/nestjs-developer/`
- `database/sql/postgresql-expert/`
- `workflow/ai-dlc-orchestrator/`

### 3. Cross-Domain Skills
If a skill applies to multiple domains:
- Option A: Place in most relevant domain
- Option B: Create in root and reference from both
- Option C: Split into domain-specific sub-skills

Example: `api-testing` could be `backend/api/api-testing/` or `quality/api-testing/`

### 4. Skill Dependencies
Document in SKILL.md frontmatter:
```yaml
---
name: nestjs-developer
domain: backend/nodejs
dependencies:
  - typescript-expert
  - nodejs-developer
  - express-developer (optional)
---
```

### 5. Consolidation Rules

**Consolidate when:**
- Multiple skills from same GitHub repo with similar purpose
- Overlapping keywords and capabilities
- One skill is subset of another

**Examples to consolidate:**
- `ui-skills-root` + `baseline-ui` → Single `ui-components` skill
- `fixing-*` skills → Single `frontend-quality` skill with sub-sections

**Keep separate when:**
- Different GitHub sources with distinct approaches
- Clearly different use cases
- Different target audiences (beginner vs expert)

---

## Maintenance Guidelines

### Adding New Skills

1. **Determine domain**: Which domain does this belong to?
2. **Check for duplicates**: Similar skills already exist?
3. **Install to .agents/skills/**: `npx skills add {repo}`
4. **Create junction/symlink**: Link to appropriate `.kiro/skills/{domain}/`
5. **Update skills-lock.json**: Add domain metadata
6. **Update documentation**: Add to readme and domain index

### Removing Skills

1. **Check dependencies**: Any other skills depend on it?
2. **Archive first**: Move to `.agents/skills/archived/`
3. **Remove junction/symlink**: Delete from `.kiro/skills/`
4. **Update skills-lock.json**: Remove entry
5. **Update documentation**: Remove from lists

### Reviewing Skills

Quarterly review checklist:
- [ ] Is skill still actively used? (check activation logs)
- [ ] Is skill up to date? (check source repo)
- [ ] Are there newer alternatives?
- [ ] Should consolidate with related skills?
- [ ] Should split into smaller skills?

---

## Migration Checklist

### Pre-Migration
- [ ] Backup current `.kiro/skills/` and `skills-lock.json`
- [ ] Document all current skill locations
- [ ] Identify skills to consolidate
- [ ] Plan domain taxonomy

### Migration
- [ ] Create domain folder structure
- [ ] Create all junction links/symlinks
- [ ] Update skills-lock.json with domain metadata
- [ ] Test skill activation (mention keywords)
- [ ] Verify all skills show in `discloseContext`

### Post-Migration
- [ ] Update all documentation
- [ ] Create domain README files
- [ ] Add skill discovery documentation
- [ ] Train team on new structure
- [ ] Monitor for broken links

### Validation
```bash
# Check all junction links exist
ls -la .kiro/skills/frontend/angular/
ls -la .kiro/skills/backend/nodejs/

# Verify skills-lock.json is valid JSON
cat skills-lock.json | jq '.'

# Test skill activation in Kiro
# Type: "show available skills"
# Type: "use angular-developer skill"
```

---

## Expected Benefits

### Before Migration
- ❌ 15+ skills in flat structure
- ❌ Hard to find relevant skills
- ❌ Duplicate/overlapping skills
- ❌ No clear taxonomy
- ❌ Difficult to maintain

### After Migration
- ✅ Clear domain separation (7 domains)
- ✅ Easy to navigate and discover
- ✅ Consolidated related skills
- ✅ Scalable to 100+ skills
- ✅ Maintainable and documented

---

## Timeline

| Phase | Duration | Tasks |
|-------|----------|-------|
| Phase 0: Planning | 1 hour | Read this doc, understand structure |
| Phase 1: Create folders | 15 min | mkdir commands |
| Phase 2: Create links | 30 min | Junction/symlink creation |
| Phase 3: Update lock file | 30 min | Add domain metadata |
| Phase 4: Documentation | 1 hour | Update all README files |
| Phase 5: Validation | 30 min | Test everything works |
| **Total** | **~3.5 hours** | Complete migration |

---

## Future Roadmap

### Short Term (Next 2 weeks)
1. Complete migration to domain structure
2. Consolidate duplicate skills
3. Add missing skills from framework categories
4. Document each domain with README

### Medium Term (Next month)
1. Add domain-specific templates
2. Create skill dependency graph
3. Implement skill versioning strategy
4. Add automated tests for skill activation

### Long Term (Next quarter)
1. Expand to 50+ skills
2. Create skill marketplace/catalog
3. Implement skill analytics (usage tracking)
4. Build skill recommendation engine

---

*Created: 2026-06-27*  
*Purpose: Reorganize skills for multi-domain enterprise repository*
