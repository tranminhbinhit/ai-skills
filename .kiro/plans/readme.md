# AI-DLC Framework Example

Bộ khung phát triển phần mềm theo hướng AI Development Life Cycle (AI-DLC).

## Giới Thiệu

AI-DLC là một phương pháp phát triển phần mềm hiện đại, tận dụng AI làm cộng tác viên chính trong toàn bộ vòng đời phát triển. Framework này giúp:

- ⚡ Rút ngắn thời gian phát triển từ **tuần xuống giờ/ngày**
- 🎯 Tăng chất lượng code và tài liệu
- 📋 Tạo quy trình chuẩn hóa có thể tái sử dụng
- 🔄 Đảm bảo tính liên tục của ngữ cảnh dự án

## Cấu Trúc Dự Án

```
├── .kiro/
│   ├── plans/
│   │   └── cr-ai-dlc-example/          # Dự án mẫu
│   │       ├── brd.md                  # Business Requirements Document
│   │       ├── inputs/                 # Tài liệu đầu vào
│   │       │   └── vision-document.md
│   │       └── aidlc-docs/             # Tài liệu AI-DLC
│   │           ├── inception/          # Giai đoạn Khởi tạo
│   │           │   ├── requirements/
│   │           │   ├── application-design/
│   │           │   └── plans/
│   │           ├── construction/       # Giai đoạn Xây dựng
│   │           │   ├── units-of-work/
│   │           │   ├── architecture/
│   │           │   └── implementation-notes/
│   │           └── operations/         # Giai đoạn Vận hành
│   │               ├── infrastructure/
│   │               ├── deployment/
│   │               └── monitoring/
│   └── steering/                       # Quy tắc và hướng dẫn
│       └── ai-dlc-workflow.md
└── readme.md
```

## Ba Giai Đoạn AI-DLC

### 1️⃣ Inception (Khởi Tạo)
- AI chuyển đổi ý tưởng thành requirements chi tiết
- Con người validate và approve
- Output: Requirements, User Stories, Application Design, Unit of Work List

### 2️⃣ Construction (Xây Dựng)
- AI implement code, tests, và documentation
- Con người review và guide decisions
- Output: Working code với tests và docs đầy đủ

### 3️⃣ Operations (Vận Hành)
- AI tạo IaC, CI/CD, monitoring configs
- Con người giám sát deployment
- Output: Deployed system với full observability

## Bắt Đầu Sử Dụng

### 🚀 Cách 1: Sử Dụng AI-DLC Skill (Khuyến Nghị)

**Skill đã được cài đặt!** AI sẽ tự động hướng dẫn bạn qua toàn bộ quy trình.

Chỉ cần nói:
```
"Use ai-dlc-orchestrator skill to create a new project called task-management"
```

Hoặc:
```
"Create new project using AI-DLC for e-commerce platform"
```

**AI sẽ tự động:**
1. ✅ Tạo cấu trúc dự án
2. ✅ Yêu cầu bạn điền Vision Document
3. ✅ Đặt câu hỏi làm rõ
4. ✅ Generate Requirements + Design
5. ✅ Implement từng UoW với tests
6. ✅ Deploy infrastructure

**Bạn chỉ cần:**
- Trả lời questions
- Review và approve
- Monitor tiến độ

---

### 🛠️ Cách 2: Thủ Công (Manual)

1. **Copy template structure**:
```bash
cp -r .kiro/plans/cr-ai-dlc-example .kiro/plans/your-project-id
```

2. **Điền Vision Document**:
Mở `.kiro/plans/your-project-id/inputs/vision-document.md`

3. **Nói với AI**: 
```
"Read vision document at .kiro/plans/your-project-id/ and start Inception phase"
```

AI sẽ tiếp tục theo quy trình AI-DLC từ đó.

## Documents Quan Trọng

### Cho Người Dùng Mới
1. [`brd.md`](.kiro/plans/cr-ai-dlc-example/brd.md) - Đọc đầu tiên để hiểu toàn bộ framework
2. [`.kiro/steering/ai-dlc-workflow.md`](.kiro/steering/ai-dlc-workflow.md) - Quy trình làm việc chi tiết

### Templates Sẵn Sàng Sử Dụng
- [`vision-document.md`](.kiro/plans/cr-ai-dlc-example/inputs/vision-document.md)
- [`user-stories.md`](.kiro/plans/cr-ai-dlc-example/aidlc-docs/inception/requirements/user-stories.md)
- [`functional-requirements.md`](.kiro/plans/cr-ai-dlc-example/aidlc-docs/inception/requirements/functional-requirements.md)
- [`non-functional-requirements.md`](.kiro/plans/cr-ai-dlc-example/aidlc-docs/inception/requirements/non-functional-requirements.md)
- [`unit-of-work-list.md`](.kiro/plans/cr-ai-dlc-example/aidlc-docs/inception/plans/unit-of-work-list.md)
- [`uow-template.md`](.kiro/plans/cr-ai-dlc-example/aidlc-docs/construction/units-of-work/uow-template.md)
- [`domain-model.md`](.kiro/plans/cr-ai-dlc-example/aidlc-docs/construction/architecture/domain-model.md)
- [`deployment-plan.md`](.kiro/plans/cr-ai-dlc-example/aidlc-docs/operations/deployment/deployment-plan.md)

## Thuật Ngữ Mới

| Thuật Ngữ Cũ | Thuật Ngữ AI-DLC | Giải Thích |
|--------------|------------------|------------|
| Sprint | **Bolt** | Chu kỳ ngắn hơn (giờ/ngày thay vì tuần) |
| Epic/Story | **Unit of Work (UoW)** | Đơn vị công việc nhỏ, hoàn thành trong 1 Bolt |
| Backlog | **UoW List** | Danh sách các units of work được prioritize |
| Documentation | **Context Repository** | Toàn bộ context lưu trong repo cho AI |

## Best Practices

### Cho AI
- ✅ Luôn đọc requirements trước khi code
- ✅ Generate tests cùng với code
- ✅ Document mọi decisions
- ✅ Đặt clarification questions sớm

### Cho Con Người  
- ✅ Review nhanh (1-2 giờ) để maintain momentum
- ✅ Provide clear, specific feedback
- ✅ Keep all context in repository
- ✅ Trust but verify AI's work

### Cho Team
- ✅ Daily sync 15 phút
- ✅ Version control everything
- ✅ Single source of truth trong repo
- ✅ Regular retrospectives

## Ví Dụ Workflow

```bash
# Day 1: Inception
1. Write vision-document.md
2. AI generates requirements + user stories
3. Team reviews và approves
4. AI creates UoW list và prioritizes

# Day 2-4: Construction  
1. AI picks UoW-001
2. AI creates detailed design
3. Team approves approach
4. AI implements code + tests
5. Team reviews và merges
6. Repeat for UoW-002, 003...

# Day 5: Operations
1. AI creates IaC configs
2. AI sets up CI/CD
3. Team reviews security
4. AI deploys to staging
5. Team validates
6. Deploy to production
```

## Lợi Ích

- 🚀 **Tốc độ**: 5-10x nhanh hơn traditional development
- 📊 **Chất lượng**: Code coverage cao, documentation đầy đủ
- 🔍 **Truy vết**: Mọi decision được documented
- 🎓 **Onboarding**: Dễ dàng cho members mới
- 🎯 **Consistency**: Quy trình chuẩn hóa

## Tài Liệu Tham Khảo

- [AI-DLC Core Framework (Viblo)](https://viblo.asia/p/ai-native-development-ai-dlc-core-framework-giai-phau-mot-vong-doi-phat-trien-thuan-ai-QyJKz7oM4Me)
- [C4 Model for Software Architecture](https://c4model.com/)
- [Architecture Decision Records](https://adr.github.io/)

## Contributing

Contributions are welcome! Vui lòng:
1. Fork repo
2. Tạo feature branch
3. Commit changes
4. Push và create PR

## License

[MIT License](LICENSE)

## Contact

Nếu có câu hỏi, vui lòng tạo issue hoặc liên hệ maintainers.

---

**Happy AI-DLC Development! 🚀🤖**
