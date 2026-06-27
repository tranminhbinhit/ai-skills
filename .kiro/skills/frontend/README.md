# Frontend Skills

Web frontend technologies including Angular framework and UI components

**Total:** 7 skills across 2 subdomains

## Skills in This Domain

- **angular-developer** (`angular\angular-developer`)
- **angular-new-app** (`angular\angular-new-app`)
- **baseline-ui** (`ui\baseline-ui`)
- **fixing-accessibility** (`ui\fixing-accessibility`)
- **fixing-metadata** (`ui\fixing-metadata`)
- **fixing-motion-performance** (`ui\fixing-motion-performance`)
- **ui-skills-root** (`ui\ui-skills-root`)

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
mklink /J ".kiro\skills\frontend\{subdomain}\{skill-name}" "..\..\..\.agents\skills\{skill-name}"

# Update skills-lock.json with domain metadata
```

---

*Last updated: 2026-06-27*
