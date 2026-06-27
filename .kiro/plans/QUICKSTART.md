# AI-DLC Quick Start Guide

## 🎯 Bắt Đầu Ngay (2 phút)

### Bước 1: Kích hoạt Skill
Nói với AI:
```
"Use ai-dlc-orchestrator skill to create a new project called [tên-dự-án]"
```

**Ví dụ:**
```
"Use ai-dlc-orchestrator skill to create a new project called task-management-app"
```

### Bước 2: Điền Vision Document
AI sẽ tạo template và yêu cầu bạn điền:
- **Problem**: Vấn đề gì cần giải quyết?
- **Users**: Ai sẽ sử dụng?
- **Features**: Tính năng chính là gì?
- **Success**: Làm sao biết thành công?

### Bước 3: Trả Lời Questions
AI sẽ đặt 5-10 câu hỏi làm rõ. Trả lời ngắn gọn:
```
Q: Should users be able to share tasks?
A: Yes, users can share tasks with team members via email invite.
```

### Bước 4: Review & Approve
AI tạo requirements. Bạn review:
```
"Requirements look good. Proceed to application design."
```

### Bước 5: Let AI Work!
AI sẽ:
- ✅ Create architecture design
- ✅ Break into Units of Work
- ✅ Implement code + tests
- ✅ Deploy infrastructure

Bạn chỉ cần review và approve theo từng bước!

---

## 📋 Checklist Nhanh

**Inception Phase:**
- [ ] Vision document filled
- [ ] Questions answered
- [ ] Requirements approved
- [ ] Architecture approved
- [ ] UoW list prioritized

**Construction Phase:**
- [ ] Each UoW designed
- [ ] Code + tests implemented
- [ ] Code reviewed
- [ ] All tests passing

**Operations Phase:**
- [ ] Infrastructure reviewed
- [ ] Deployed to staging
- [ ] Deployed to production

---

## 🎬 Example Session

```
👤 You: "Use ai-dlc-orchestrator skill to create a new project called blog-platform"

🤖 AI: "Creating AI-DLC project structure for blog-platform...
      Structure created at .kiro/plans/blog-platform/
      
      I've placed a vision-document.md template. Please fill in:
      1. Problem statement
      2. Target users  
      3. Key features
      4. Success criteria
      
      Let me know when ready!"

👤 You: "Done. Vision document filled."

🤖 AI: "Thank you. I've read the vision. Before generating requirements,
      I have 6 clarification questions in clarification-qa.md:
      
      Q1: Should users be able to comment on posts?
      Q2: What authentication methods? (Email/password, OAuth, both?)
      Q3: Should posts support markdown or rich text editor?
      ...
      
      Please answer when ready."

👤 You: "Answered all questions."

🤖 AI: "Perfect! Generating:
      ✓ Functional requirements (14 features)
      ✓ Non-functional requirements  
      ✓ User stories (12 stories, 4 epics)
      
      Please review in inception/requirements/
      
      Key features identified:
      - User authentication & profiles
      - Create/edit/publish posts
      - Comments & likes
      - Admin dashboard
      
      Once approved, I'll create the application design."

👤 You: "Approved. Continue."

🤖 AI: "Creating application design...
      ✓ Tech stack: Node.js + Express + PostgreSQL + React
      ✓ Architecture: RESTful API + SPA
      ✓ 6 Units of Work identified
      
      Estimated timeline: 3-4 Bolts (days)
      
      Ready to start Construction phase?"

👤 You: "Yes, start with UoW-001"

🤖 AI: "Starting UoW-001: Setup Project Infrastructure
      
      Tasks:
      ✓ Git repository initialized
      ✓ Monorepo structure created
      ✓ TypeScript + ESLint configured
      ✓ Docker dev environment ready
      ✓ CI/CD pipeline created
      
      All tests passing ✓ (23 tests, 95% coverage)
      
      UoW-001 complete. Review?"

👤 You: "Looks good. Continue with UoW-002."

[Process continues...]
```

---

## 💡 Pro Tips

1. **Be Specific in Vision**: More detail = fewer clarification rounds
2. **Quick Reviews**: Review within 1-2 hours to maintain momentum  
3. **Ask Questions**: If anything unclear, ask AI to explain
4. **Trust the Process**: Let AI handle details, you focus on decisions
5. **Keep Context**: All decisions stay in repo for future reference

---

## 🆘 Troubleshooting

**Q: AI không theo đúng quy trình?**
A: Nói: "Follow AI-DLC workflow as defined in .kiro/steering/ai-dlc-workflow.md"

**Q: Muốn skip một bước?**
A: Không nên skip! Mỗi bước cung cấp context cho bước sau.

**Q: Muốn pause và resume sau?**
A: Khi trở lại, nói: "Check AI-DLC project status and continue where we left off"

**Q: Code quality không đạt?**
A: Tạo `.kiro/steering/coding-standards.md` với standards cụ thể.

---

## 📚 Next Steps

Sau khi quen với quy trình:
- Đọc [BRD chi tiết](cr-ai-dlc-example/brd.md)
- Xem [Workflow guide](.kiro/steering/ai-dlc-workflow.md)
- Tùy chỉnh templates cho team

**Happy Building! 🚀**
