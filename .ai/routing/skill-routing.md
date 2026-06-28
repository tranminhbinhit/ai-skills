# Skill Routing

Luôn đọc file này trước khi chọn skill.

---

## Installed Skills

### Frontend Angular
**Skill**: `angular-developer`  
**Location**: `.agents/skills/angular-developer/`  
**Trigger when**: Angular, component, page, form, route, RxJS, signal, UI, npm build frontend, TypeScript

**Skill**: `angular-new-app`  
**Location**: `.agents/skills/angular-new-app/`  
**Trigger when**: Create new Angular application, scaffold new project, ng new

### Frontend Design & Review
**Skill**: `frontend-design`  
**Location**: `.agents/skills/frontend-design/`  
**Trigger when**: Visual design, UI design, typography, color palette, layout, aesthetic direction, distinctive design, design system

**Skill**: `web-design-guidelines`  
**Location**: `.agents/skills/web-design-guidelines/`  
**Trigger when**: Review UI, check accessibility, audit design, review UX, check site against best practices, web guidelines

### Advanced Design & Creative
**Skill**: `ui-ux-pro-max`  
**Location**: `.ai/skills/ui-ux-pro-max/`  
**Trigger when**: Design intelligence, UX guidelines, UI palettes, typography, chart choices, technology-stack UI recommendations

**Skill**: `design`  
**Location**: `.ai/skills/design/`  
**Trigger when**: Logo design, corporate identity program, CIP, icons, social images, design mockups, brand identity, creative design workflows

**Skill**: `banner-design`  
**Location**: `.ai/skills/banner-design/`  
**Trigger when**: Social media banners, ads, website hero banners, print banners, creative assets

**Skill**: `ui-styling`  
**Location**: `.ai/skills/ui-styling/`  
**Trigger when**: Tailwind CSS, shadcn/ui, Radix UI, accessible components, dark mode, themes, responsive styling

**Skill**: `brand`  
**Location**: `.ai/skills/brand/`  
**Trigger when**: Brand voice, visual identity, messaging framework, brand guidelines, brand consistency, asset management

**Skill**: `slides`  
**Location**: `.ai/skills/slides/`  
**Trigger when**: Strategic HTML presentations, Chart.js slides, slide layouts, copywriting formulas, responsive presentations

**Skill**: `design-system`  
**Location**: `.ai/skills/design-system/`  
**Trigger when**: Design tokens, token architecture, component specifications, CSS variables, design-system slides

**Skill**: `ui-ux-pro-max-skill`  
**Location**: `.ai/skills/ui-ux-pro-max-skill/`  
**Trigger when**: Discovering or routing within the bundled UI/UX Pro Max suite. Prefer the focused child skills above when the task intent is clear.

### Code Quality & Review
**Skill**: `code-review-expert`  
**Location**: `.agents/skills/code-review-expert/`  
**Trigger when**: Code review, review git changes, SOLID principles, security scan, architecture review, git diff analysis

**Skill**: `skill-review`  
**Location**: `.agents/skills/skill-review/`  
**Trigger when**: Review skill, audit skill, skill quality, check my skill, evaluate skill, skill lint, validate skill

### SDLC & Project Management
**Skill**: `ai-dlc-orchestrator`  
**Location**: `.ai/skills/ai-dlc-orchestrator/`  
**Trigger when**: New project, Inception, Construction, Operations, UoW, Bolt, AI-DLC workflow, requirements, architecture design

---

## Routing Rules by Domain

### Frontend Angular
Nếu task liên quan đến Angular, component, page, form, route, RxJS, signal, UI, npm build frontend:
- **Ưu tiên skill**: `angular-developer`
- Nếu tạo mới Angular app: `angular-new-app`

### Frontend Design & UX
Nếu task liên quan đến visual design, UI design, typography, color, layout, aesthetic:
- **Ưu tiên skill**: `frontend-design`
- Nếu review UI/UX hoặc accessibility: `web-design-guidelines`
- Nếu cần design intelligence/palette/font/UX database: `ui-ux-pro-max`
- Nếu cần Tailwind/shadcn/ui implementation: `ui-styling`
- Nếu cần design system/tokens/component specs: `design-system`
- Nếu cần brand/logo/banner/slides/social assets: `brand`, `design`, `banner-design`, hoặc `slides`

### Code Quality & Review
Nếu task liên quan đến code review, security scan, SOLID principles, git diff:
- **Ưu tiên skill**: `code-review-expert`
- Nếu review skill structure: `skill-review`

### Backend Node.js
Nếu task liên quan đến API, controller, service, middleware, validation, auth:
- **Ưu tiên skill**: *[Chưa cài đặt - sẽ bổ sung khi có]*

### Database
Nếu task liên quan đến PostgreSQL, schema, migration, static data, category key value:
- **Ưu tiên skill**: *[Chưa cài đặt - sẽ bổ sung khi có]*

### DevOps
Nếu task liên quan đến Docker, Vercel, CI/CD, env, build, deploy:
- **Ưu tiên skill**: *[Chưa cài đặt - sẽ bổ sung khi có]*

### SDLC & Project Management
Nếu task liên quan đến Epic, User Story, Task, Unit of Work, Plan, AI-DLC workflow:
- **Ưu tiên skill**: `ai-dlc-orchestrator`

---

## Nguyên tắc chọn skill

1. **Không tự ý sửa/move skill đã install** - Chỉ đọc và sử dụng
2. **Chỉ đọc skill phù hợp với ngữ cảnh** - Tránh load quá nhiều skills
3. **Nếu task thuộc nhiều nhóm** - Chọn skill chính trước, sau đó dùng skill phụ
4. **Nếu không chắc** - Đọc description của các skill trước khi chọn
5. **Không dùng tất cả skill cùng lúc** - Chỉ load skills cần thiết

---

## Skill Selection Policy

### AUTO (Default)
- Tự động chọn skill dựa trên ngữ cảnh task
- Dùng khi user không chỉ định skill cụ thể
- Ưu tiên skill theo bảng routing ở trên

### PREFERRED
- Dùng khi user đề cập domain cụ thể
- Example: "Review Angular code" → auto load `angular-developer`

### FORCED
- Chỉ dùng skills được chỉ định rõ ràng
- Example: 
  ```
  Mode=FORCED
  Skills: angular-developer, angular-new-app
  Task: Create customer profile page
  ```

### EXCLUSIVE (ONLY)
- Chỉ dùng một skill duy nhất, không load thêm
- Example:
  ```
  ONLY use skill: angular-developer
  Do not load any other skill.
  Review changes in apps/customer-web.
  ```

---

## Agent-Specific Mappings

| Agent       | Skills Location              | Steering/Instruction   | Load Config File |
|-------------|------------------------------|------------------------|------------------|
| Kiro        | `.kiro/skills`, `.agents/skills`, `.ai/skills` | `.kiro/steering` | `.kiro/steering/load-ai-skills.md` |
| Codex CLI   | `.agents/skills`, `.ai/skills` | `AGENTS.md`            | `AGENTS.md` |
| Claude Code | `.claude/commands`, `.claude/skills`, `.agents/skills`, `.ai/skills` | `CLAUDE.md` | `CLAUDE.md` |
| Cursor      | `.cursor/rules`, `.agents/skills`, `.ai/skills` | `.cursor/rules` | `.cursor/rules/load-ai-skills.md` |
| Gemini CLI  | project root, `.agents/skills`, `.ai/skills` | `GEMINI.md` | `GEMINI.md` |

---

## Examples

### Example 1: Auto Selection
```
User: "Review code changes in apps/customer-web"
Agent: Detects "apps/customer-web" → Frontend domain
      → Loads skill: angular-developer
```

### Example 2: Preferred Selection
```
User: "Create a new Angular component for user profile"
Agent: Detects "Angular component" → Frontend Angular domain
      → Loads skill: angular-developer
```

### Example 3: Forced Mode
```
User: 
Mode=FORCED
Skills: angular-developer, ai-dlc-orchestrator
Task: Start new Angular project with AI-DLC workflow

Agent: Loads only: angular-developer, ai-dlc-orchestrator
```

### Example 4: Exclusive Mode
```
User:
ONLY use skill: ai-dlc-orchestrator
Do not load any other skill.
Create project inception phase for task-management-app.

Agent: Loads only: ai-dlc-orchestrator
```
