# Design Skills

Design, branding, and UX expertise for creating professional user interfaces.

**Total:** 1 skill (comprehensive)

## Skills in This Domain

- **ui-ux-pro-max** (`frontend/design/ui-ux-pro-max`)
  - Comprehensive design system knowledge (~90 files)
  - Brand guidelines and color systems
  - Typography and layout patterns
  - UI components and styling
  - UX best practices
  - Design tokens and variables
  - Includes data files (CSV) and Python tools

## Content Structure

```
ui-ux-pro-max/
├── SKILL.md              # Main skill definition
├── references/           # Knowledge base (~60 MD files)
│   ├── banner-design/    # Banner and hero designs
│   ├── brand/            # Brand guidelines
│   ├── design/           # Core design principles
│   ├── design-system/    # Design system docs
│   ├── slides/           # Presentation templates
│   └── ui-styling/       # Styling guides
├── data/                 # Design data (~15 CSV files)
│   ├── colors.csv        # Color palettes
│   ├── typography.csv    # Font combinations
│   ├── icons.csv         # Icon libraries
│   ├── google-fonts.csv  # Font references
│   └── ...
└── scripts/              # Python tools (3 files)
    ├── core.py           # Core utilities
    ├── design_system.py  # Design system tools
    └── search.py         # Search functionality
```

## How to Use

This skill auto-activates when Kiro detects design-related keywords:

**Example queries:**
- "create a color palette"
- "design a landing page"
- "brand guidelines for my app"
- "what fonts work well together?"
- "design system for my project"
- "create a banner design"

## Key Features

### Brand & Identity
- Color theory and palette generation
- Typography systems
- Logo and brand guidelines
- Visual identity principles

### Design Systems
- Component libraries
- Design tokens
- Spacing and layout grids
- Responsive design patterns

### UI Components
- Buttons, forms, cards
- Navigation patterns
- Modal and overlay designs
- Data visualization

### UX Guidelines
- User research principles
- Interaction patterns
- Accessibility considerations
- Mobile-first design

## Data Files

The skill includes curated datasets:

| File | Purpose |
|------|---------|
| colors.csv | Color palettes and combinations |
| typography.csv | Font pairings and hierarchies |
| icons.csv | Icon library references |
| google-fonts.csv | Google Fonts catalog |
| design.csv | General design patterns |
| landing.csv | Landing page templates |
| charts.csv | Data visualization patterns |
| ux-guidelines.csv | UX best practices |

## Python Tools

Automation scripts for design workflows:

- `core.py` - Core utility functions
- `design_system.py` - Design system generators
- `search.py` - Search design references

## Integration with Other Skills

**Works well with:**
- `baseline-ui` (UI components)
- `fixing-accessibility` (A11y compliance)
- `fixing-metadata` (SEO & OG images)
- `angular-developer` (Apply designs to Angular)

**Complements:**
- All frontend skills benefit from design guidance
- Backend skills for branding API docs
- Documentation skills for styled docs

## Migration Notes

This skill was migrated from `.kiro/skills/web/ui-ux-pro-max/` to `frontend/design/` on 2026-06-27 as part of the skills reorganization project.

---

## Adding More Design Skills

To add additional design skills to this subdomain:

```bash
# Install from GitHub
npx skills add {org}/{repo} --skill {design-skill-name}

# Create junction link (Windows)
mklink /J ".kiro\skills\frontend\design\{skill-name}" "..\..\..\.agents\skills\{skill-name}"

# Update skills-lock.json with domain: "frontend", subdomain: "design"
```

---

*Last updated: 2026-06-27*
