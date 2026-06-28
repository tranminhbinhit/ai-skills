#  Promts mẫu
## Promts mẫu khi đã mapping skill vào các route skill của ai agent
    Review code thay đổi trong apps/customer-web.
    Kiểm tra build, coding convention, unit test và security issue.
## Ép skill
    Task: Review code apps/customer-web.
    Hãy tham khảo skill-routing và ưu tiên các frontend skills phù hợp.

## Ép skill theo mode 
Mode=FORCED

Skills:
- frontend-component
- frontend-unit-test

Task:
Create customer profile page.


## Chỉ định skill
ONLY use skill:
frontend-angular-review

Do not load any other skill.
Review changes in apps/customer-web.


# Xây dựng lại skill toàn bộ cho hệ thống

## xây dựng mới cấu trúc bên dưới

.ai/
    context/
        project.md
        architecture.md

    routing/
        skill-routing.md
        Link các skill install, skill custom

    skills/ Các skills custom vd ai-dlc-orchestrator


## THêm mới hoặc bổ sung trong root skill của các ai agent với nội dung như sau
Always read:

../../.ai/context/project-context.md
../../.ai/routing/skill-routing.md

## Tạo hoặc thêm mới theo url "Url Skill"

Mapping cho toàn bộ skill của các agent theo format  cập nhật vào từng file skill nếu có 1 skill mới hoặc cập nhật vào skill nếu chưa install


| Agent       | Skill                                | Steering/Instruction | Url Skill
| ----------- | ------------------------------------ | -------------------- |
| Kiro        | `.kiro/skills`                       | `.kiro/steering`     |  .kiro/steering/load-ai.md
| Codex CLI   | `.agent/skills`                      | `AGENTS.md`          | AGENTS.md
| Claude Code | `.claude/commands`, `.claude/skills` | `CLAUDE.md`          | CLAUDE.md
| Cursor      | Rules                                | `.cursor/rules`      | .cursor/rules/load-ai.md
| Gemini CLI  | context file                         | `GEMINI.md`          | GEMINI.md

sinh skill-lock.json tuong ung