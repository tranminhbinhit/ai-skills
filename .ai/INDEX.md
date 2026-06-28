# AI Skills Documentation Index

Chỉ mục tổng hợp tất cả tài liệu về AI Skills trong dự án.

---

## 📚 Quick Navigation

### 🚀 Getting Started
1. **[README.md](../README.md)** - Overview, AI-DLC, multi-agent setup
2. **[PROMPTS.md](../PROMPTS.md)** - Usage examples & management templates
3. **[QUICK-REFERENCE.md](./QUICK-REFERENCE.md)** - Cheat sheet, one-page guide

### 📋 Core Documentation
4. **[project-context.md](./context/project-context.md)** - Installed skills registry
5. **[skill-routing.md](./routing/skill-routing.md)** - Skill routing rules & policies

### 🔧 Configuration Files
6. **[skills-lock.json](../skills-lock.json)** - Version tracking & metadata
7. **[.kiro/steering/load-ai-skills.md](../.kiro/steering/load-ai-skills.md)** - Kiro config
8. **[AGENTS.md](../AGENTS.md)** - Codex CLI config
9. **[CLAUDE.md](../CLAUDE.md)** - Claude Code config
10. **[GEMINI.md](../GEMINI.md)** - Gemini CLI config
11. **[.cursor/rules/load-ai.md](../.cursor/rules/load-ai.md)** - Cursor config

### 📊 Summary & Updates
12. **[SKILLS-UPDATE-SUMMARY.md](./SKILLS-UPDATE-SUMMARY.md)** - Latest update summary
13. **[REFACTOR-SUMMARY.md](./REFACTOR-SUMMARY.md)** - Initial refactor summary

### 🛠️ Maintenance & Templates
14. **[ADD-NEW-SKILL.md](./ADD-NEW-SKILL.md)** - Standard process for adding new skills
15. **[AGENT-RULES.md](./AGENT-RULES.md)** - Agent assignment rules (Kiro=plan, Codex=code)

---

## 📖 Documentation by Purpose

### For New Users
**Start here:**
1. Read **README.md** - Understand AI-DLC and multi-agent setup
2. Read **PROMPTS.md** - Learn how to use skills
3. Try AUTO mode first - Let AI choose the right skill

**Example first prompt:**
```
"Create user-profile component in Angular with reactive forms"
```

---

### For Skill Users

**Using Skills:**
- **AUTO mode examples**: See [PROMPTS.md](../PROMPTS.md#auto-mode-tự-động-chọn-skill)
- **FORCED mode examples**: See [PROMPTS.md](../PROMPTS.md#forced-mode-chỉ-định-skills-cụ-thể)
- **EXCLUSIVE mode examples**: See [PROMPTS.md](../PROMPTS.md#exclusive-mode-chỉ-dùng-1-skill-duy-nhất)

**Troubleshooting:**
- Skill not loading? → See [README.md Troubleshooting](../README.md#-troubleshooting)
- Wrong skill loaded? → Use FORCED or EXCLUSIVE mode
- Multiple skills conflict? → Check [skill-routing.md](./routing/skill-routing.md)

---

### For Developers

**Understanding the System:**
1. **Architecture**: See [project-context.md Structure](./context/project-context.md#project-structure)
2. **Routing Logic**: See [skill-routing.md](./routing/skill-routing.md)
3. **Version Control**: See [skills-lock.json](../skills-lock.json)

**Adding New Skills:**
1. **Standard Process**: See [ADD-NEW-SKILL.md](./ADD-NEW-SKILL.md)
2. **Prompt Templates**: See [PROMPTS.md](../PROMPTS.md)
3. **Simple Command**: `"Hãy cập nhật các skill chưa có vào danh sách skill route"`

**Quick Add Process:**
```
1. Install: npx skills add <repo-url> --skill <skill-name>
2. Prompt: "Hãy cập nhật các skill chưa có vào danh sách skill route"
3. Done! AI auto-updates all 6 required files
```

---

### For AI Agents

**On Startup:**
1. Read agent config file (AGENTS.md, CLAUDE.md, etc.)
2. Load [project-context.md](./context/project-context.md) - Know what skills exist
3. Load [skill-routing.md](./routing/skill-routing.md) - Understand routing rules

**On Task Execution:**
1. Parse user request
2. Identify domain keywords
3. Check routing rules in [skill-routing.md](./routing/skill-routing.md)
4. Determine mode (AUTO/PREFERRED/FORCED/EXCLUSIVE)
5. Load appropriate skill(s)
6. Execute task

---

## 🗂️ Documentation Structure

```
.
├── readme.md                         📚 Main documentation
├── Promt-example.md                  💡 Usage examples (30+)
│
├── .ai/                              🎯 AI Context Hub
│   ├── INDEX.md                      📑 This file
│   ├── context/
│   │   └── project-context.md        📋 Skills registry
│   ├── routing/
│   │   └── skill-routing.md          🔀 Routing rules
│   ├── skills/
│   │   └── ai-dlc-orchestrator/      🚀 Custom SDLC skill
│   ├── SKILLS-UPDATE-SUMMARY.md      📊 Latest update
│   └── REFACTOR-SUMMARY.md           📝 Initial refactor
│
├── .kiro/
│   ├── skills/                       📦 7 installed skills
│   │   ├── angular-developer/
│   │   ├── angular-new-app/
│   │   ├── frontend-design/
│   │   ├── web-design-guidelines/
│   │   ├── code-review-expert/
│   │   └── skill-review/
│   └── steering/
│       └── load-ai-skills.md         🤖 Kiro config
│
├── AGENTS.md                         💻 Codex CLI config
├── CLAUDE.md                         🧠 Claude Code config
├── GEMINI.md                         💎 Gemini CLI config
├── .cursor/rules/load-ai.md          🖱️  Cursor config
│
└── skills-lock.json                  🔒 Version tracking
```

---

## 📦 Installed Skills Reference

### Quick Lookup

| Need | Skill | Doc Link |
|------|-------|----------|
| Angular development | angular-developer | [SKILL.md](../.kiro/skills/angular-developer/SKILL.md) |
| Create Angular app | angular-new-app | [SKILL.md](../.kiro/skills/angular-new-app/SKILL.md) |
| Visual design | frontend-design | [SKILL.md](../.kiro/skills/frontend-design/SKILL.md) |
| UI/UX review | web-design-guidelines | [SKILL.md](../.kiro/skills/web-design-guidelines/SKILL.md) |
| Code review | code-review-expert | [SKILL.md](../.kiro/skills/code-review-expert/SKILL.md) |
| Skill review | skill-review | [SKILL.md](../.kiro/skills/skill-review/SKILL.md) |
| AI-DLC workflow | ai-dlc-orchestrator | [SKILL.md](./skills/ai-dlc-orchestrator/SKILL.md) |

---

## 🎯 Common Tasks

### Task: Create Angular Component
**Docs**: [readme.md](../readme.md#-quick-start)  
**Examples**: [Promt-example.md](../Promt-example.md#frontend-angular-development)  
**Skill**: angular-developer

### Task: Design UI
**Docs**: [readme.md](../readme.md#-quick-start)  
**Examples**: [Promt-example.md](../Promt-example.md#frontend-design)  
**Skill**: frontend-design

### Task: Review Code
**Docs**: [readme.md](../readme.md#-quick-start)  
**Examples**: [Promt-example.md](../Promt-example.md#code-quality--review)  
**Skill**: code-review-expert

### Task: Create New Project with AI-DLC
**Docs**: [readme.md](../readme.md#-quick-start)  
**Examples**: [Promt-example.md](../Promt-example.md#sdlc--project-management)  
**Skill**: ai-dlc-orchestrator

---

## 🔍 Search by Topic

### Angular
- [angular-developer SKILL.md](../.kiro/skills/angular-developer/SKILL.md)
- [angular-new-app SKILL.md](../.kiro/skills/angular-new-app/SKILL.md)
- [Examples in Promt-example.md](../Promt-example.md#frontend-angular-development)
- [Routing rules](./routing/skill-routing.md#frontend-angular)

### Design
- [frontend-design SKILL.md](../.kiro/skills/frontend-design/SKILL.md)
- [web-design-guidelines SKILL.md](../.kiro/skills/web-design-guidelines/SKILL.md)
- [Examples in Promt-example.md](../Promt-example.md#frontend-design)
- [Routing rules](./routing/skill-routing.md#frontend-design--ux)

### Code Quality
- [code-review-expert SKILL.md](../.kiro/skills/code-review-expert/SKILL.md)
- [skill-review SKILL.md](../.kiro/skills/skill-review/SKILL.md)
- [Examples in Promt-example.md](../Promt-example.md#code-quality--review)
- [Routing rules](./routing/skill-routing.md#code-quality--review)

### Project Management
- [ai-dlc-orchestrator SKILL.md](./skills/ai-dlc-orchestrator/SKILL.md)
- [Examples in Promt-example.md](../Promt-example.md#sdlc--project-management)
- [Routing rules](./routing/skill-routing.md#sdlc--project-management)

---

## 📊 Statistics

**Total Skills**: 7  
**Frontend**: 4 (Angular x2, Design x2)  
**Quality**: 2 (Code Review x2)  
**SDLC**: 1 (AI-DLC)

**Documentation Coverage**: 100%  
**Example Coverage**: 100%  
**Routing Coverage**: 100%

**Total Examples**: 30+  
**Usage Modes**: 4 (AUTO, PREFERRED, FORCED, EXCLUSIVE)  
**Supported Agents**: 5 (Kiro, Codex, Claude, Cursor, Gemini)

---

## 🔗 External Resources

### Skill Sources
- **Angular**: https://github.com/angular/skills
- **Anthropic**: https://github.com/anthropics/skills
- **Vercel**: https://github.com/vercel-labs/agent-skills
- **Sanyuan**: https://github.com/sanyuan0704/sanyuan-skills

### Installation
See [readme.md Installation](../readme.md#-installation)

---

## 📅 Last Updated

**Date**: 2026-06-28  
**Version**: 1.0.0  
**Skills**: 7 installed  
**Coverage**: 100%

---

## 💡 Tips

### For Best Results:
1. ✅ Start with AUTO mode - Let AI choose
2. ✅ Use FORCED when you need specific skills
3. ✅ Use EXCLUSIVE for single-skill tasks
4. ✅ Check examples in Promt-example.md
5. ✅ Read skill SKILL.md for detailed guidance

### Avoid:
1. ❌ Mixing too many domains in one prompt (split into multiple)
2. ❌ Vague requests without domain keywords
3. ❌ Using EXCLUSIVE with multi-domain tasks

---

## 🆘 Help & Support

**Problem**: Can't find what you need?  
**Solution**: Use this navigation tree:

```
What do you want to do?
├─ Learn basics → readme.md
├─ See examples → Promt-example.md
├─ Understand skills → project-context.md
├─ Understand routing → skill-routing.md
├─ Configure agent → AGENTS.md, CLAUDE.md, etc.
├─ Add new skill → readme.md#maintenance
└─ Troubleshoot → readme.md#troubleshooting
```

**Still stuck?** Check the specific skill's SKILL.md file.

---

## 🎉 You're Ready!

All documentation is in place. Start using skills:

```bash
# Simple AUTO mode
"Create Angular component"

# With control
Mode=FORCED
Skills: angular-developer, code-review-expert

# Single skill only
ONLY use skill: code-review-expert
```

Happy coding! 🚀
