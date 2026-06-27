# Skills Dependencies Map

This document maps dependencies and relationships between skills.

## Dependency Types

1. **Hard Dependency**: Skill A requires Skill B to function
2. **Soft Dependency**: Skill A benefits from Skill B but can work without it
3. **Complementary**: Skills work well together
4. **Alternative**: Skills solve similar problems with different approaches

---

## Frontend Skills Dependencies

### angular-developer
- **Soft Dependencies**: 
  - `code-review-expert` (for reviewing Angular code)
  - `fixing-accessibility` (Angular a11y best practices)
- **Complementary Skills**:
  - `angular-new-app` (creates projects that angular-developer works on)

### angular-new-app
- **Hard Dependencies**: None
- **Complementary Skills**:
  - `angular-developer` (develops apps created by this skill)

### baseline-ui
- **Soft Dependencies**:
  - `fixing-accessibility` (ensure UI components are accessible)
  - `fixing-motion-performance` (optimize animations)
- **Complementary Skills**:
  - All UI skills work together

### fixing-accessibility
- **Applies To**: All frontend skills
- **Complementary Skills**:
  - `baseline-ui`, `ui-skills-root`

### fixing-metadata
- **Applies To**: All frontend skills
- **Complementary Skills**: Frontend SEO skills

### fixing-motion-performance
- **Soft Dependencies**:
  - `baseline-ui` (UI components with animations)
- **Complementary Skills**: Frontend performance skills

### ui-skills-root
- **Contains**: Umbrella for UI skills
- **Related**: All `frontend/ui/` skills

---

## Backend Skills Dependencies

### express-developer
- **Soft Dependencies**:
  - Database skills (postgresql-expert, mongodb-expert)
  - `graphql-expert` (if building GraphQL APIs)
  - `code-review-expert` (code review)
- **Alternatives**: `fastify-developer`, `nestjs-developer`

### fastify-developer
- **Soft Dependencies**:
  - Database skills
  - `graphql-expert`
  - `code-review-expert`
- **Alternatives**: `express-developer`, `nestjs-developer`

### nestjs-developer
- **Soft Dependencies**:
  - Database skills
  - `graphql-expert` (NestJS has excellent GraphQL support)
  - `prisma-expert` (common pairing)
  - `code-review-expert`
- **Alternatives**: `express-developer`, `fastify-developer`

### django-developer
- **Soft Dependencies**:
  - `postgresql-expert` (Django's preferred database)
  - `code-review-expert`
- **Alternatives**: `fastapi-developer`

### fastapi-developer
- **Soft Dependencies**:
  - Database skills
  - `code-review-expert`
- **Alternatives**: `django-developer`

### graphql-expert
- **Soft Dependencies**:
  - Backend framework skills (express, nestjs, fastapi)
  - Database skills
- **Complementary Skills**: All backend + database skills

---

## Database Skills Dependencies

### postgresql-expert
- **Complementary Skills**:
  - `prisma-expert` (Prisma works great with PostgreSQL)
  - Backend framework skills
  - `code-review-expert`
- **Alternatives**: `mongodb-expert` (different data model)

### mongodb-expert
- **Complementary Skills**:
  - Backend framework skills (Express, FastAPI, NestJS)
  - `code-review-expert`
- **Alternatives**: `postgresql-expert` (different data model)

### redis-expert
- **Use Case**: Caching, pub/sub, sessions
- **Complementary Skills**:
  - All backend skills (Redis as cache layer)
  - Database skills (Redis as cache for primary DB)

### prisma-expert
- **Soft Dependencies**:
  - `postgresql-expert` (or other DB skills)
  - Backend framework skills
- **Complementary Skills**:
  - `nestjs-developer` (common pairing)
  - `code-review-expert`

---

## Quality Skills Dependencies

### code-review-expert
- **Applies To**: ALL skills
- **Universal**: Can review any code domain
- **Complementary Skills**: Every skill benefits from code review

---

## Documentation Skills Dependencies

### pdf
- **Hard Dependencies**: None
- **Use Cases**: Generate reports, invoices, documentation
- **Complementary Skills**: 
  - Backend skills (PDF generation in APIs)
  - Documentation skills

### book-study
- **Hard Dependencies**: None
- **Use Cases**: Educational content creation
- **Complementary Skills**:
  - `sigma` (teaching methodology)
  - `wiki-ingest` (knowledge organization)

### sigma
- **Hard Dependencies**: None
- **Use Cases**: Teaching and pedagogy
- **Complementary Skills**:
  - `book-study` (content creation)
  - All technical skills (teaching technical topics)

### wiki-ingest
- **Hard Dependencies**: None
- **Use Cases**: Knowledge base management
- **Complementary Skills**:
  - `book-study`, `sigma` (organizing learning materials)

---

## Meta Skills Dependencies

### skill-forge
- **Hard Dependencies**: None
- **Use Cases**: Creating new skills
- **Complementary Skills**:
  - `skill-review` (validate created skills)

### skill-review
- **Hard Dependencies**: None
- **Use Cases**: Review skill quality
- **Complementary Skills**:
  - `skill-forge` (review newly created skills)
  - `code-review-expert` (similar review mindset)

---

## Workflow Skills Dependencies

### ai-dlc-orchestrator
- **Hard Dependencies**: None (framework-agnostic)
- **Applies To**: ALL projects
- **Complementary Skills**: 
  - ALL skills (orchestrates development across all domains)
  - Especially: `code-review-expert`, documentation skills

---

## Common Skill Combinations

### Full-Stack Web App (MEAN/MERN)
- `angular-developer` or `baseline-ui` (frontend)
- `express-developer` or `nestjs-developer` (backend)
- `mongodb-expert` (database)
- `redis-expert` (caching)
- `code-review-expert` (quality)
- `ai-dlc-orchestrator` (workflow)

### Full-Stack Web App (PERN/PEAN)
- `angular-developer` (frontend)
- `express-developer` or `nestjs-developer` (backend)
- `postgresql-expert` (database)
- `prisma-expert` (ORM)
- `redis-expert` (caching)
- `code-review-expert` (quality)

### Modern Node.js API
- `nestjs-developer` or `fastify-developer` (framework)
- `graphql-expert` (API design)
- `postgresql-expert` + `prisma-expert` (data layer)
- `redis-expert` (caching)
- `code-review-expert` (quality)

### Python Web API
- `fastapi-developer` or `django-developer` (framework)
- `postgresql-expert` or `mongodb-expert` (database)
- `redis-expert` (caching)
- `pdf` (report generation)
- `code-review-expert` (quality)

### Frontend Only
- `angular-developer` or `baseline-ui` (framework)
- `fixing-accessibility` (a11y)
- `fixing-metadata` (SEO)
- `fixing-motion-performance` (performance)
- `code-review-expert` (quality)

### Documentation Project
- `pdf` (PDF generation)
- `book-study` (content structure)
- `sigma` (teaching methodology)
- `wiki-ingest` (knowledge organization)

### Skill Development
- `skill-forge` (create skills)
- `skill-review` (validate skills)
- `code-review-expert` (code quality)

---

## Skill Activation Patterns

### Auto-Activation by Keywords

Skills activate automatically when keywords detected:

| Skill | Keywords |
|-------|----------|
| angular-developer | angular, component, directive, @Input, @Output, ng |
| express-developer | express, middleware, router, app.get, app.post |
| nestjs-developer | nestjs, @Controller, @Injectable, @Module |
| mongodb-expert | mongodb, mongoose, collection, aggregation |
| postgresql-expert | postgresql, postgres, sql, SELECT, CREATE TABLE |
| code-review-expert | review, code review, SOLID, security, refactor |
| pdf | pdf, generate pdf, report |

### Manual Activation

When you need specific skill:
```
"use angular-developer skill to create a component"
"activate code-review-expert to review this code"
"use pdf skill to generate report"
```

---

## Conflict Resolution

### When Multiple Skills Could Apply

**Scenario**: Creating a Node.js API

Multiple skills could activate:
- `express-developer` (Express.js)
- `fastify-developer` (Fastify)
- `nestjs-developer` (NestJS)

**Resolution**: 
1. Kiro asks: "Which framework? Express, Fastify, or NestJS?"
2. User specifies, Kiro activates correct skill
3. Or user explicitly: "use nestjs-developer"

### Complementary Activation

Some queries activate multiple skills:

**Query**: "Create an Angular app with accessibility"
- Activates: `angular-developer` + `fixing-accessibility`

**Query**: "Review this Express API code"
- Activates: `express-developer` + `code-review-expert`

**Query**: "Build a NestJS API with PostgreSQL and Prisma"
- Activates: `nestjs-developer` + `postgresql-expert` + `prisma-expert`

---

## Skill Upgrade Paths

### Learning Progression

**Beginner → Intermediate → Advanced**

1. **Frontend**:
   - Start: `baseline-ui` (basic components)
   - Intermediate: `angular-developer` (framework)
   - Advanced: `fixing-accessibility` + `fixing-motion-performance`

2. **Backend**:
   - Start: `express-developer` (simple API)
   - Intermediate: `fastify-developer` (performance-focused)
   - Advanced: `nestjs-developer` (enterprise architecture)

3. **Database**:
   - Start: Choose `mongodb-expert` OR `postgresql-expert`
   - Intermediate: Add `redis-expert` (caching)
   - Advanced: Add `prisma-expert` (advanced ORM)

4. **Full-Stack**:
   - Start: Frontend + Backend skill
   - Intermediate: + Database + Code Review
   - Advanced: + All quality/performance skills + AI-DLC workflow

---

## Future Dependencies (Planned Skills)

When new skills are added, update this map:

- **Docker/Kubernetes skills** → Will depend on backend/database skills
- **Testing skills** → Will apply to all domains
- **Security skills** → Will apply to all domains
- **Performance skills** → Will apply to all domains
- **CI/CD skills** → Will apply to all domains

---

*Last updated: 2026-06-27*  
*Update this file when adding/removing skills or discovering new relationships*
