# Prompt Examples & Templates

Hướng dẫn toàn diện về cách sử dụng skills và manage skill system trong dự án.

---

## 📖 Table of Contents

1. [Usage Examples](#-usage-examples) - Cách sử dụng skills
2. [Management Templates](#-management-templates) - Quản lý skills
3. [Quick Reference](#-quick-reference) - Tham khảo nhanh

---

# 🎯 USAGE EXAMPLES

## AUTO Mode (Tự động chọn skill)

### Frontend Angular Development

```
Tạo component user-profile trong Angular với:
- Form để edit thông tin user
- Validation với reactive forms
- Integration với user service
```
→ Tự động load: `angular-developer`

```
Create a new Angular 19 application called "task-manager" 
with SSR, routing, and Tailwind CSS
```
→ Tự động load: `angular-new-app`

---

### Frontend Design

```
Design a landing page for a premium coffee subscription service.
Target audience: urban millennials who value craft and sustainability.
Make it distinctive, not generic.
```
→ Tự động load: `frontend-design`

```
Review the UI accessibility of my dashboard component.
Check against Web Interface Guidelines.
```
→ Tự động load: `web-design-guidelines`

---

### Code Quality & Review

```
Review code changes in the latest commit.
Focus on security, SOLID principles, and architecture.
```
→ Tự động load: `code-review-expert`

```
Review my new skill "database-helper".
Check structure, description quality, and token efficiency.
```
→ Tự động load: `skill-review`

---

### SDLC & Project Management

```
Create a new project using AI-DLC workflow.
Project: E-commerce platform with inventory management.
```
→ Tự động load: `ai-dlc-orchestrator`

---

## PREFERRED Mode (Ưu tiên skill theo domain)

### Example 1: Frontend Development với Angular

```
Task: Implement user authentication flow
Domain: Angular frontend

Expected skills: angular-developer
```
→ Agent detect "Angular" → Load `angular-developer`

---

### Example 2: Visual Design

```
Task: Create homepage design for fitness app
Focus: Typography, color palette, distinctive layout

Expected skills: frontend-design
```
→ Agent detect "design", "typography" → Load `frontend-design`

---

## FORCED Mode (Chỉ định skills cụ thể)

### Example 1: Angular Development + AI-DLC Workflow

```
Mode=FORCED
Skills:
- angular-new-app
- ai-dlc-orchestrator

Task:
Create new Angular project "inventory-system" following AI-DLC workflow.
Start with Inception phase to gather requirements.
```

---

### Example 2: Design + Review

```
Mode=FORCED
Skills:
- frontend-design
- web-design-guidelines

Task:
Design a checkout page, then review it for accessibility compliance.
```

---

### Example 3: Full Stack với Review

```
Mode=FORCED
Skills:
- angular-developer
- code-review-expert

Task:
1. Implement shopping cart component
2. Review the implementation for SOLID violations
```

---

## EXCLUSIVE Mode (Chỉ dùng 1 skill duy nhất)

### Example 1: Pure Angular Work

```
ONLY use skill: angular-developer

Do not load any other skill.

Task:
Refactor user-profile component to use signals instead of RxJS BehaviorSubject.
Update all dependent components.
```

---

### Example 2: Pure Code Review

```
ONLY use skill: code-review-expert

Do not load any other skill.

Task:
Review changes in apps/customer-web.
Focus on security vulnerabilities and P0/P1 issues only.
```

---

### Example 3: Pure Design Work

```
ONLY use skill: frontend-design

Do not load any other skill.

Task:
Create visual design for pricing page.
Focus on typography hierarchy and color psychology.
Do not implement code.
```

---

### Example 4: AI-DLC Only

```
ONLY use skill: ai-dlc-orchestrator

Do not load any other skill.

Task:
Create Inception phase documents for "booking-system" project.
Include requirements, user stories, and UoW breakdown.
```

---

## Combined Skills Examples

### Example 1: Full Frontend Flow

```
Mode=FORCED
Skills:
- angular-new-app
- angular-developer
- frontend-design
- code-review-expert

Task:
1. Create new Angular app "portfolio"
2. Design landing page with distinctive visual identity
3. Implement the design in Angular
4. Review code for quality and security
```

---

### Example 2: Design → Implement → Review

```
Phase 1 (Design):
ONLY use skill: frontend-design
Create dashboard design for SaaS analytics platform.

Phase 2 (Implement):
ONLY use skill: angular-developer
Implement the dashboard design in Angular with real data binding.

Phase 3 (Review):
ONLY use skill: code-review-expert
Review implementation for SOLID principles and security.

Phase 4 (Accessibility):
ONLY use skill: web-design-guidelines
Check accessibility compliance.
```

---

# 🛠️ MANAGEMENT TEMPLATES

## Add New Skills

### Template 1: Auto-detect và update tất cả (Most Common)

```
Hãy cập nhật các skill chưa có vào danh sách skill route
```

**AI sẽ làm**:
1. Scan `.kiro/skills/` directory
2. Compare với `.ai/routing/skill-routing.md`
3. Identify missing skills
4. Update 6 files cho mỗi skill
5. Verify consistency
6. Report results

---

### Template 2: Specify skills cần update

```
Hãy cập nhật các skill chưa có vào danh sách skill route

Skills cần update:
- <skill-name-1>
- <skill-name-2>
- <skill-name-3>
```

---

### Template 3: Verify trước khi update

```
Check if all installed skills are documented.
List any missing skills.
```

**AI sẽ response**:
```
Installed: X skills
Documented: Y skills
Missing: Z skills
  - skill-1
  - skill-2
  
Would you like me to add them?
```

---

## Check Skill Status

### Check installed skills
```
List all installed skills in .kiro/skills/
```

### Check documented skills
```
List all skills currently in .ai/routing/skill-routing.md
```

### Find missing skills
```
Compare installed skills vs documented skills.
Show which skills are missing from documentation.
```

### Verify consistency
```
Verify all documented skills appear in all required files:
- project-context.md
- skill-routing.md
- skills-lock.json
- readme.md
- PROMPTS.md
- INDEX.md

Report any inconsistencies.
```

---

## Add Specific Skill

### Add single skill
```
Add "<skill-name>" to skill routing documentation.

Read skill metadata from: .kiro/skills/<skill-name>/SKILL.md
Update all required files.
```

### Add multiple skills
```
Add these skills to routing documentation:
1. <skill-name-1>
2. <skill-name-2>
3. <skill-name-3>

For each skill:
- Read metadata from SKILL.md
- Update all required files
- Add usage examples
```

---

## Update Existing Skill

### Update skill metadata
```
Skill "<skill-name>" has been updated.

Please:
1. Re-read .kiro/skills/<skill-name>/SKILL.md
2. Update description in all documentation files
3. Update triggers/keywords if changed
4. Verify consistency
```

### Update skill examples
```
Add more usage examples for "<skill-name>" in PROMPTS.md

Include examples for:
- AUTO mode
- FORCED mode
- EXCLUSIVE mode
```

---

## Remove Skill

```
Skill "<skill-name>" has been uninstalled.

Please:
1. Remove from project-context.md
2. Remove from skill-routing.md
3. Remove from skills-lock.json
4. Remove from readme.md
5. Remove from PROMPTS.md
6. Remove from INDEX.md
7. Update skill counts
```

---

## Generate Reports

### Coverage report
```
Generate a coverage report:
- How many skills installed?
- How many skills documented?
- Coverage percentage
- List any gaps
```

### Domain distribution
```
Show skill distribution by domain:
- Frontend: X skills
- Backend: Y skills
- Quality: Z skills
- SDLC: Y skills
```

### Documentation completeness
```
For each skill, verify:
- Has description in project-context.md
- Has routing rules in skill-routing.md
- Has metadata in skills-lock.json
- Has examples in PROMPTS.md
- Listed in readme.md
- Listed in INDEX.md

Report completeness percentage.
```

---

## Maintenance Tasks

### Sync all documentation
```
Ensure all skill documentation is in sync:
1. Verify skill lists match across all files
2. Verify skill counts are correct
3. Verify skill names are consistent
4. Fix any inconsistencies found
```

### Update skill counts
```
Count installed skills and update counts in:
- project-context.md
- readme.md

Ensure counts match everywhere.
```

---

## Search & Find

### Find skills by domain
```
List all skills in "<domain>" domain.
Show their names, locations, and descriptions.
```

### Find skills by keyword
```
Find all skills that trigger on keyword: "<keyword>"
List them with their full trigger lists.
```

### Find skills by use case
```
Which skills should I use for: "<use-case-description>"?

Recommend:
1. Primary skill
2. Secondary skills (if needed)
3. Usage mode (AUTO/FORCED/EXCLUSIVE)
```

---

# 📚 QUICK REFERENCE

## Mode Selection

| Use Case | Mode | Example |
|----------|------|---------|
| General task với clear domain | AUTO | "Create Angular component" |
| Specific skills needed | FORCED | Mode=FORCED, Skills: A, B, C |
| Single skill only | EXCLUSIVE | ONLY use skill: X |
| Multi-phase different domains | Sequential EXCLUSIVE | Phase 1: ONLY skill A, Phase 2: ONLY skill B |

---

## Most Used Prompts

### 1️⃣ Add new skills
```
Hãy cập nhật các skill chưa có vào danh sách skill route
```

### 2️⃣ Check status
```
Check if all installed skills are documented
```

### 3️⃣ Use skill (AUTO)
```
<natural language task description>
```

### 4️⃣ Use skill (FORCED)
```
Mode=FORCED
Skills: skill-name-1, skill-name-2
Task: <description>
```

### 5️⃣ Use skill (EXCLUSIVE)
```
ONLY use skill: skill-name
Task: <description>
```

---

## Tips for Effective Prompts

### ✅ DO:

1. **Rõ ràng về domain**:
   ```
   ✅ "Create Angular component with reactive forms"
   ❌ "Create a form"
   ```

2. **Specify mode khi cần control**:
   ```
   ✅ Mode=FORCED, Skills: angular-developer, code-review-expert
   ❌ (không chỉ định mode, có thể load thêm skills không cần)
   ```

3. **Use EXCLUSIVE khi chỉ cần 1 skill**:
   ```
   ✅ ONLY use skill: code-review-expert
   ❌ Mode=FORCED, Skills: code-review-expert (vẫn có thể load thêm)
   ```

### ❌ DON'T:

1. **Không mix domain khi dùng EXCLUSIVE**
2. **Không overload AUTO mode với quá nhiều tasks**
3. **Không vague về yêu cầu**

---

## Learning Path

### Beginner: Start with AUTO
```
1. "Create new Angular app" (AUTO)
2. "Add user list component" (AUTO)
3. "Review my code" (AUTO)
```

### Intermediate: Use FORCED for control
```
Mode=FORCED
Skills: angular-developer, frontend-design
Task: Create product catalog with distinctive visual design
```

### Advanced: Sequential EXCLUSIVE for precision
```
Step 1: ONLY use skill: ai-dlc-orchestrator
Step 2: ONLY use skill: frontend-design
Step 3: ONLY use skill: angular-developer
Step 4: ONLY use skill: code-review-expert
```

---

## Decision Tree

```
User Request
    ↓
Clear domain mentioned?
    ↓ Yes → AUTO mode
    ↓ No
    ↓
Multiple domains needed?
    ↓ Yes → FORCED mode
    ↓ No
    ↓
Single specific task?
    ↓ Yes → EXCLUSIVE mode
    ↓
Complex multi-phase?
    ↓ Yes → Break into sequential EXCLUSIVE
```

---

## Support

Nếu skill không được load như mong đợi:

1. Check `.ai/routing/skill-routing.md` - routing rules
2. Check `.ai/context/project-context.md` - installed skills
3. Use FORCED or EXCLUSIVE mode để control chính xác
4. Review prompt để đảm bảo domain keywords rõ ràng

---

## Documentation Links

- **Main Docs**: [readme.md](./readme.md)
- **Skill Routing**: [.ai/routing/skill-routing.md](./.ai/routing/skill-routing.md)
- **Add New Skill**: [.ai/ADD-NEW-SKILL.md](./.ai/ADD-NEW-SKILL.md)
- **Quick Reference**: [.ai/QUICK-REFERENCE.md](./.ai/QUICK-REFERENCE.md)
- **Full Index**: [.ai/INDEX.md](./.ai/INDEX.md)
