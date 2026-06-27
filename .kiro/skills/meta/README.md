# Meta Skills

Skills for creating and managing other skills

**Total:** 2 skills

## Skills in This Domain

- **skill-forge** (`skill-forge`)
- **skill-review** (`skill-review`)

## How to Use

Skills auto-activate when Kiro detects relevant keywords in your queries.

**Example queries:**
- Frontend: "create an Angular component", "fix accessibility issues"
- Backend: "setup Express server", "create FastAPI endpoint"
- Database: "design PostgreSQL schema", "MongoDB aggregation"
- Quality: "review this code", "check SOLID principles"

## Adding New Skills

To add a new skill to this domain:

```bash
# Install from GitHub
npx skills add {org}/{repo} --skill {skill-name}

# Create junction link (Windows)
mklink /J ".kiro\skills\meta\{subdomain}\{skill-name}" "..\..\..\.agents\skills\{skill-name}"

# Update skills-lock.json with domain metadata
```

---

*Last updated: 2026-06-27*
