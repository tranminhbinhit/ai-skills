# AI Skills for Hybrid Multi-Agent Development

> **Bộ kỹ năng chuẩn hóa cho phát triển phần mềm theo AI-DLC, hỗ trợ đồng thời nhiều AI agents mà không thiếu skills**

Dự án này tập hợp và chuẩn hóa các skills cần thiết để phát triển phần mềm theo phương pháp **AI Development Life Cycle (AI-DLC)**. Cho phép tổ chức chạy **hybrid nhiều AI agents** (Kiro, Claude Code, Cursor, Codex CLI, Gemini) với cùng một bộ skills, đảm bảo tính nhất quán và đồng bộ trong quá trình phát triển.

---

## 🎯 Mục Đích

### 1. Phát Triển Theo AI-DLC
Hỗ trợ đầy đủ các giai đoạn của AI Development Life Cycle:
- **Inception** (Khởi tạo): Requirements, Architecture Design
- **Construction** (Xây dựng): Implementation, Testing, Review
- **Operations** (Vận hành): Deployment, Monitoring

### 2. Hybrid Multi-Agent
Cho phép sử dụng **đồng thời nhiều AI agents** trong cùng một dự án:
- **Kiro** - Main development & orchestration
- **Claude Code** - Code generation & refactoring
- **Cursor** - In-editor assistance
- **Codex CLI** - Command-line workflows
- **Gemini CLI** - Alternative agent support

### 3. Tập Hợp Skills Chuẩn
Cung cấp **bộ skills hoàn chỉnh** cho toàn bộ software development lifecycle:
- Frontend (Angular, Design, UX)
- Code Quality (Review, Testing)
- SDLC (AI-DLC Orchestrator)
- _(Mở rộng)_ Backend, Database, DevOps

---

## 📦 Installed Skills (7 Skills)

### Frontend Development (4 skills)
| Skill | Purpose | Triggers |
|-------|---------|----------|
| **angular-developer** | Angular components, forms, routing, signals, testing | Angular, component, form, routing, RxJS |
| **angular-new-app** | Create new Angular applications | ng new, create app, scaffold |
| **frontend-design** | Visual design, typography, color palette, distinctive UI | visual design, typography, layout, aesthetic |
| **web-design-guidelines** | UI/UX review, accessibility audit | review UI, accessibility, UX audit |

### Code Quality (2 skills)
| Skill | Purpose | Triggers |
|-------|---------|----------|
| **code-review-expert** | Code review, SOLID principles, security scan | code review, SOLID, security, git diff |
| **skill-review** | Skill structure audit, quality validation | review skill, audit skill, skill quality |

### SDLC (1 skill)
| Skill | Purpose | Triggers |
|-------|---------|----------|
| **ai-dlc-orchestrator** | AI-DLC workflow orchestration (Inception/Construction/Operations) | AI-DLC, Inception, UoW, requirements |

---

## 🚀 Quick Start

### 1. Cài Đặt Skills

```bash
# Angular skills
npx skills add https://github.com/angular/skills

# Design & UX skills
npx skills add https://github.com/anthropics/skills --skill frontend-design
npx skills add https://github.com/vercel-labs/agent-skills --skill web-design-guidelines

# Code quality skills
npx skills add https://github.com/sanyuan0704/sanyuan-skills --skill code-review-expert
npx skills add https://github.com/sanyuan0704/sanyuan-skills --skill skill-review
```

### 2. Cập Nhật Routing (One Command)

```
Hãy cập nhật các skill chưa có vào danh sách skill route
```

AI sẽ tự động:
- Scan installed skills
- Update 6 documentation files
- Verify consistency
- Report results

### 3. Bắt Đầu Sử Dụng

**AUTO Mode** (Recommended):
```
Create user-profile component in Angular with reactive forms
```
→ AI tự động chọn `angular-developer`

**FORCED Mode** (Control):
```
Mode=FORCED
Skills: angular-developer, code-review-expert

Task: Implement shopping cart and review code
```

**EXCLUSIVE Mode** (Single skill):
```
ONLY use skill: ai-dlc-orchestrator

Create Inception phase for booking-system project
```

---

## 🏗️ AI-DLC Workflow Support

### Phase 1: Inception (Khởi Tạo)

**Skill**: `ai-dlc-orchestrator`

```
Create new project "e-commerce-platform" using AI-DLC workflow.

Include:
- Vision analysis
- Requirements (functional & non-functional)
- User stories
- Architecture design
- Unit of Work breakdown
```

**Output**:
- `.kiro/plans/{project}/inputs/vision-document.md`
- `.kiro/plans/{project}/aidlc-docs/inception/requirements/`
- `.kiro/plans/{project}/aidlc-docs/inception/application-design/`
- `.kiro/plans/{project}/aidlc-docs/inception/plans/unit-of-work-list.md`

---

### Phase 2: Construction (Xây Dựng)

**Skills**: Multiple skills theo domain

```
Mode=FORCED
Skills: 
- angular-new-app          # Create application
- angular-developer        # Implement features
- frontend-design          # Design UI
- code-review-expert       # Review code

Task:
Based on UoW-001 from Inception phase, implement:
1. Create Angular app structure
2. Design landing page
3. Implement components
4. Review implementation
```

**Workflow**:
```
For each Unit of Work:
  1. Plan → 2. Implement → 3. Test → 4. Review → 5. Integrate
```

---

### Phase 3: Operations (Vận Hành)

**Skill**: `ai-dlc-orchestrator` + DevOps skills

```
ONLY use skill: ai-dlc-orchestrator

Create deployment plan for e-commerce-platform:
- Infrastructure as Code
- CI/CD pipeline
- Monitoring setup
- Deployment checklist
```

**Output**:
- `.kiro/plans/{project}/aidlc-docs/operations/infrastructure/`
- `.kiro/plans/{project}/aidlc-docs/operations/deployment/`
- `.kiro/plans/{project}/aidlc-docs/operations/monitoring/`

---

## 🤖 Hybrid Multi-Agent Setup

### Cấu Trúc Tập Trung

```
.
├── .ai/                          # 🎯 Context Hub (Shared by all agents)
│   ├── context/
│   │   └── project-context.md    # What skills are installed
│   ├── routing/
│   │   └── skill-routing.md      # How to route to skills
│   └── skills/
│       └── ai-dlc-orchestrator/  # Custom SDLC skill
│
├── .kiro/skills/                 # 📦 Installed skills (7 skills)
│   ├── angular-developer/
│   ├── angular-new-app/
│   ├── frontend-design/
│   ├── web-design-guidelines/
│   ├── code-review-expert/
│   └── skill-review/
│
├── Agent Configs                 # 🤖 Multi-agent support
│   ├── AGENTS.md                 # Codex CLI
│   ├── CLAUDE.md                 # Claude Code
│   ├── GEMINI.md                 # Gemini CLI
│   ├── .kiro/steering/load-ai-skills.md  # Kiro
│   └── .cursor/rules/load-ai.md          # Cursor
│
├── Documentation                 # 📚 Usage docs
│   ├── README.md                 # This file
│   ├── PROMPTS.md                # Usage examples & templates
│   └── skills-lock.json          # Version tracking
```

### Lợi Ích Của Cấu Trúc Tập Trung

✅ **Consistency** - Tất cả agents sử dụng cùng bộ skills  
✅ **Sync** - Một lần update, tất cả agents đều biết  
✅ **Flexibility** - Dễ dàng chuyển đổi giữa các agents  
✅ **No Duplication** - Không cần maintain skills riêng cho từng agent  

---

## 🎯 Usage Modes

### AUTO Mode (Default)
AI tự động chọn skill dựa trên domain keywords trong prompt.

**Example**:
```
"Create Angular component" → angular-developer
"Design homepage" → frontend-design
"Review code" → code-review-expert
```

**When to use**: Hầu hết các trường hợp, trust AI để chọn skill phù hợp.

---

### FORCED Mode
Chỉ định chính xác skills cần sử dụng.

**Example**:
```
Mode=FORCED
Skills: angular-developer, code-review-expert

Task: Implement user authentication and review for security
```

**When to use**: Cần control chính xác skills nào được load.

---

### EXCLUSIVE Mode
Chỉ dùng **một** skill duy nhất, không load thêm skills khác.

**Example**:
```
ONLY use skill: code-review-expert

Review changes in apps/customer-web for security issues
```

**When to use**: Task chỉ thuộc về 1 domain cụ thể, không muốn mix skills.

---

### PREFERRED Mode
Agent ưu tiên skills khi detect domain keywords.

**Example**:
```
Task: Review Angular code for SOLID violations

→ AI detects: "Angular" + "review" 
→ Loads: angular-developer + code-review-expert
```

**When to use**: Tự động, không cần chỉ định mode.

---

## 📋 AI-DLC Real-World Example

### Complete Workflow: Building "Task Management App"

#### Step 1: Inception Phase
```
ONLY use skill: ai-dlc-orchestrator

Create new project "task-management-app" using AI-DLC workflow.

Requirements:
- Users can create, edit, delete tasks
- Task categories and priorities
- Due dates and reminders
- Team collaboration
- Real-time updates
```

**AI Output**:
- Vision analysis
- 15 functional requirements
- 8 non-functional requirements
- 10 user stories
- Architecture design (Angular + Firebase)
- 6 Units of Work

---

#### Step 2: Construction - UoW 001 (Setup)
```
Mode=FORCED
Skills: angular-new-app, ai-dlc-orchestrator

Task: Execute UoW-001: Project Setup
- Create Angular 19 app with SSR
- Setup project structure
- Configure Firebase
- Setup routing
```

---

#### Step 3: Construction - UoW 002 (Design)
```
ONLY use skill: frontend-design

Based on requirements, design:
- Task list view (board/list modes)
- Task detail modal
- Category management
- User dashboard

Target: Clean, productive, not generic.
```

---

#### Step 4: Construction - UoW 003 (Implementation)
```
Mode=FORCED
Skills: angular-developer, frontend-design

Task: Implement task list component
- Data binding with signals
- Drag-and-drop support
- Filter and search
- Apply design from UoW-002
```

---

#### Step 5: Construction - UoW 004 (Review)
```
ONLY use skill: code-review-expert

Review all changes for UoW-003:
- SOLID violations
- Security issues (XSS, auth)
- Performance concerns
- Code smells
```

---

#### Step 6: Repeat for UoW 005-006
Continue Construction phase cho các UoWs còn lại.

---

#### Step 7: Operations
```
ONLY use skill: ai-dlc-orchestrator

Create deployment plan:
- Firebase Hosting setup
- CI/CD with GitHub Actions
- Environment configuration
- Monitoring with Firebase Analytics
- Rollback procedures
```

---

## 🌐 Multi-Agent Collaboration Scenarios

### Scenario 1: Kiro Orchestrates, Claude Implements

**Kiro** (Planning):
```
ONLY use skill: ai-dlc-orchestrator

Create Inception phase for "booking-system"
```

**Claude Code** (Implementation):
```
Mode=FORCED
Skills: angular-developer, frontend-design

Implement UoW-003 based on Inception docs in .kiro/plans/booking-system/
```

**Benefit**: Kiro plans, Claude codes. Clear separation of concerns.

---

### Scenario 2: Cursor for Quick Edits, Kiro for Review

**Cursor** (In-editor):
```
ONLY use skill: angular-developer

Add loading state to user-profile component
```

**Kiro** (Review):
```
ONLY use skill: code-review-expert

Review latest changes for security and SOLID principles
```

**Benefit**: Fast iteration with Cursor, thorough review with Kiro.

---

### Scenario 3: Round-Robin Different Agents

```
Phase 1 - Gemini: Create requirements
Phase 2 - Claude: Design UI
Phase 3 - Cursor: Implement features
Phase 4 - Kiro: Review and optimize
Phase 5 - Codex: Deploy
```

**Benefit**: Use each agent's strengths, consistent skills across all.

---

## 🔧 Skill Management

### Add New Skill

```bash
# 1. Install
npx skills add <repo-url> --skill <skill-name>

# 2. Update documentation (AI auto-updates 6 files)
"Hãy cập nhật các skill chưa có vào danh sách skill route"

# 3. Verify
"Check if all installed skills are documented"
```

**Files Auto-Updated**:
1. `.ai/context/project-context.md` - Registry
2. `.ai/routing/skill-routing.md` - Routing rules
3. `skills-lock.json` - Metadata
4. `README.md` - This file
5. `PROMPTS.md` - Examples
6. `.ai/INDEX.md` - Navigation

---

### Remove Skill

```bash
# 1. Uninstall
npx skills remove <skill-name>

# 2. Update documentation
"Skill '<skill-name>' has been uninstalled. 
Remove from all documentation and update counts."
```

---

### Check Coverage

```
Show skill documentation coverage report
```

**Output**:
```
Installed: 7 skills
Documented: 7 skills
Coverage: 100%

All skills properly documented ✅
```

---

## 📚 Documentation

### Core Documents
- **[README.md](./README.md)** _(This file)_ - Overview, AI-DLC, multi-agent
- **[PROMPTS.md](./PROMPTS.md)** - Usage examples & management templates
- **[.ai/ADD-NEW-SKILL.md](./.ai/ADD-NEW-SKILL.md)** - Detailed add skill process
- **[.ai/QUICK-REFERENCE.md](./.ai/QUICK-REFERENCE.md)** - One-page cheat sheet

### Context & Routing
- **[.ai/context/project-context.md](./.ai/context/project-context.md)** - Skill registry
- **[.ai/routing/skill-routing.md](./.ai/routing/skill-routing.md)** - Routing rules
- **[skills-lock.json](./skills-lock.json)** - Version tracking

### Agent Configs
- **[AGENTS.md](./AGENTS.md)** - Codex CLI
- **[CLAUDE.md](./CLAUDE.md)** - Claude Code
- **[GEMINI.md](./GEMINI.md)** - Gemini CLI
- **[.kiro/steering/load-ai-skills.md](./.kiro/steering/load-ai-skills.md)** - Kiro
- **[.cursor/rules/load-ai.md](./.cursor/rules/load-ai.md)** - Cursor

### Navigation
- **[.ai/INDEX.md](./.ai/INDEX.md)** - Complete documentation index

---

## 🎓 Learning Path

### Beginner (Day 1)
1. Read this README
2. Read [PROMPTS.md](./PROMPTS.md) - Usage Examples section
3. Try AUTO mode: `"Create Angular component"`
4. Check [.ai/QUICK-REFERENCE.md](./.ai/QUICK-REFERENCE.md)

### Intermediate (Week 1)
1. Learn FORCED mode for multi-skill tasks
2. Practice with [PROMPTS.md](./PROMPTS.md) examples
3. Try AI-DLC workflow for small project
4. Switch between different AI agents

### Advanced (Month 1)
1. Use EXCLUSIVE mode for precise control
2. Manage skills: add, update, remove
3. Orchestrate multi-agent workflows
4. Customize skills for your team

---

## 🔍 Troubleshooting

### Skill not loading

**Problem**: AI doesn't load expected skill

**Solution**:
1. Check `.ai/routing/skill-routing.md` - Are triggers correct?
2. Check `.ai/context/project-context.md` - Is skill installed?
3. Use FORCED or EXCLUSIVE mode to specify

---

### Wrong skill loaded

**Problem**: AI loads incorrect skill

**Solution**:
1. Make prompt more specific: "Angular component" not "component"
2. Use EXCLUSIVE mode: `ONLY use skill: angular-developer`
3. Check routing rules for conflicts

---

### Skills out of sync

**Problem**: Different agents see different skills

**Solution**:
```
Ensure all skill documentation is in sync across all files
```

All agents read from `.ai/` - should always be consistent.

---

### Documentation incomplete

**Problem**: Missing examples or routing rules

**Solution**:
```
Hãy cập nhật các skill chưa có vào danh sách skill route
```

AI will scan and update all missing documentation.

---

## 🚀 Roadmap

### Current (v1.0)
- ✅ 7 skills installed and documented
- ✅ Frontend (Angular, Design, UX)
- ✅ Code Quality (Review, Testing)
- ✅ SDLC (AI-DLC Orchestrator)
- ✅ 5 AI agents supported
- ✅ 100% documentation coverage

### Next (v1.1)
- [ ] Backend skills (Node.js, Express, NestJS)
- [ ] Database skills (PostgreSQL, Prisma)
- [ ] DevOps skills (Docker, CI/CD)
- [ ] Testing skills (Jest, Vitest, Playwright)
- [ ] API skills (REST, GraphQL, OpenAPI)

### Future (v2.0)
- [ ] Team collaboration features
- [ ] Custom skill templates
- [ ] Skill marketplace
- [ ] Analytics & insights
- [ ] AI-DLC templates library

---

## 📞 Support & Contributing

### Get Help
- Check [PROMPTS.md](./PROMPTS.md) for examples
- Read [.ai/QUICK-REFERENCE.md](./.ai/QUICK-REFERENCE.md)
- See [.ai/INDEX.md](./.ai/INDEX.md) for navigation

### Add New Skills
See [.ai/ADD-NEW-SKILL.md](./.ai/ADD-NEW-SKILL.md) for detailed process.

Quick version:
```bash
# 1. Install
npx skills add <repo-url> --skill <skill-name>

# 2. Update docs
"Hãy cập nhật các skill chưa có vào danh sách skill route"
```

### Report Issues
- Skill not working? Check documentation first
- Documentation unclear? Open issue
- New skill needed? Suggest in issues

---

## 📄 License

Skills have individual licenses. See `skills-lock.json` or each skill's SKILL.md.

This repository structure and documentation: MIT License

---

## 🙏 Credits

**Skills from**:
- **Angular Team** - angular-developer, angular-new-app
- **Anthropic** - frontend-design
- **Vercel** - web-design-guidelines
- **Sanyuan0704** - code-review-expert, skill-review

**Framework**:
- **AI-DLC Orchestrator** - Custom (Local)

**Inspiration**:
- AI-DLC methodology for software development
- Multi-agent orchestration patterns
- Skill-based AI agent architecture

---

## ✨ Why This Project?

### Problem
- Different AI agents need different skill setups
- Hard to maintain consistency across agents
- No standard approach for AI-DLC workflow
- Skills not shareable between agents

### Solution
- **Centralized skill registry** (`.ai/`)
- **Universal routing system** (`.ai/routing/`)
- **Multi-agent support** (5 agents, 1 skill set)
- **AI-DLC orchestration** (Built-in workflow skill)

### Result
- ✅ One skill set, multiple agents
- ✅ Consistent development experience
- ✅ AI-DLC workflow supported
- ✅ Easy to add/remove/update skills
- ✅ 100% documentation coverage

---

**Ready to build with AI-DLC?** 🚀

Start here: [PROMPTS.md](./PROMPTS.md) → Try AUTO mode → Explore AI-DLC workflow

---

_Last updated: 2026-06-28 | Version: 1.0.0 | Skills: 7 | Agents: 5 | Coverage: 100%_
