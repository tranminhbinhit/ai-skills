# BRD: AI-DLC Framework - Bộ Khung Phát Triển Phần Mềm Hướng AI

## 1. Tổng Quan Dự Án

### 1.1 Giới Thiệu
AI-DLC (AI Development Life Cycle) là một bộ khung phát triển phần mềm hiện đại, tận dụng AI làm cộng tác viên chính trong toàn bộ vòng đời phát triển. Framework này định nghĩa cấu trúc, quy trình và công cụ để xây dựng phần mềm nhanh hơn, chất lượng cao hơn thông qua sự kết hợp AI và con người.

**Tham khảo:** https://viblo.asia/p/ai-native-development-ai-dlc-core-framework-giai-phau-mot-vong-doi-phat-trien-thuan-ai-QyJKz7oM4Me

### 1.2 Mục Tiêu Kinh Doanh
- Rút ngắn thời gian phát triển từ tuần xuống giờ/ngày
- Tăng chất lượng code và tài liệu thông qua AI
- Tạo ra quy trình chuẩn hóa có thể tái sử dụng
- Đảm bảo tính liên tục và truy vết của ngữ cảnh dự án
- Tối ưu hóa sự phối hợp giữa AI và con người

### 1.3 Phạm Vi Dự Án
Framework bao gồm:
- Cấu trúc thư mục chuẩn cho AI-DLC
- Template và mẫu tài liệu cho các giai đoạn
- Quy trình làm việc (workflow) chi tiết
- Hướng dẫn sử dụng và best practices
- Ví dụ mẫu có thể áp dụng ngay

---

## 2. Triết Lý Cốt Lõi

### 2.1 Nguyên Tắc Hoạt Động
**AI là Cộng Tác Viên, Không Phải Công Cụ**

1. **AI lập kế hoạch chủ động**: AI đặt câu hỏi làm rõ, đề xuất giải pháp
2. **Con người ra quyết định**: Dựa trên bối cảnh kinh doanh và kinh nghiệm
3. **AI thực thi**: Sau khi có xác nhận, AI implement theo kế hoạch

### 2.2 Vai Trò Phân Định
| Vai Trò | AI | Con Người |
|---------|-----|-----------|
| Phân tích yêu cầu | Chuyển đổi ý tưởng thành specs | Xác thực và bổ sung |
| Thiết kế | Đề xuất architecture & design patterns | Quyết định cuối cùng |
| Coding | Generate code & tests | Review và điều chỉnh |
| Documentation | Tạo tài liệu tự động | Kiểm tra và phê duyệt |
| Deployment | Tạo IaC scripts | Giám sát và xác nhận |

---

## 3. Ba Giai Đoạn Của AI-DLC

### 3.1 Giai Đoạn Khởi Tạo (Inception)
**Mục đích:** Chuyển đổi ý tưởng kinh doanh thành yêu cầu chi tiết

**Đầu vào:**
- Vision document (tài liệu tầm nhìn)
- Business requirements (yêu cầu kinh doanh)
- External specifications (OpenAPI, GraphQL schemas, etc.)

**AI thực hiện:**
- Phân tích và đặt câu hỏi làm rõ
- Tạo user stories và use cases
- Định nghĩa functional & non-functional requirements
- Lập kế hoạch Unit of Work (UoW)
- Tạo application design drafts

**Con người tham gia:**
- Team Building sessions để validate
- Trả lời clarification questions
- Approve requirements và plans

**Đầu ra:**
```
inception/
├── requirements/
│   ├── functional-requirements.md
│   ├── non-functional-requirements.md
│   └── user-stories.md
├── application-design/
│   ├── system-context.md
│   ├── architecture-overview.md
│   └── tech-stack.md
└── plans/
    ├── unit-of-work-list.md
    └── bolt-schedule.md
```

### 3.2 Giai Đoạn Xây Dựng (Construction)
**Mục đích:** Biến thiết kế thành code chạy được

**Đầu vào:**
- Validated requirements từ Inception
- Architecture decisions
- Design specifications

**AI thực hiện:**
- Đề xuất logical architecture
- Tạo domain models
- Generate source code
- Viết unit tests & integration tests
- Tạo API documentation

**Con người tham gia:**
- Team Assembly để làm rõ technical decisions
- Code review
- Architecture validation
- Integration testing

**Đầu ra:**
```
construction/
├── units-of-work/
│   ├── uow-001-user-authentication.md
│   ├── uow-002-data-layer.md
│   └── uow-003-api-endpoints.md
├── architecture/
│   ├── component-diagram.md
│   ├── domain-model.md
│   └── api-design.md
└── implementation-notes/
    ├── tech-decisions.md
    └── patterns-used.md
```

### 3.3 Giai Đoạn Vận Hành (Operations)
**Mục đích:** Triển khai và vận hành hệ thống

**Đầu vào:**
- Completed codebase
- Architecture documentation
- Deployment requirements

**AI thực hiện:**
- Tạo Infrastructure as Code (IaC)
- Setup CI/CD pipelines
- Tạo monitoring & logging configs
- Generate deployment scripts
- Viết operational runbooks

**Con người tham gia:**
- Giám sát deployment process
- Validate infrastructure security
- Monitor production systems
- Handle incidents

**Đầu ra:**
```
operations/
├── infrastructure/
│   ├── terraform/
│   ├── kubernetes/
│   └── docker-compose.yml
├── deployment/
│   ├── deployment-plan.md
│   ├── rollback-procedures.md
│   └── smoke-tests.md
└── monitoring/
    ├── alerts-config.yaml
    └── dashboard-setup.md
```

---

## 4. Thuật Ngữ Mới

### 4.1 Bolt (Thay vì Sprint)
- Chu kỳ làm việc ngắn: vài giờ đến vài ngày
- Cường độ cao, tập trung vào một UoW
- Kết thúc khi deliverable được hoàn thành

### 4.2 Unit of Work (Thay vì Epic/Story)
- Đơn vị công việc nhỏ, có thể hoàn thành trong 1 Bolt
- Độc lập và có thể kiểm thử
- Có input và output rõ ràng

### 4.3 Context Repository
- Lưu trữ toàn bộ ngữ cảnh dự án trong repo
- Giúp AI có đầy đủ context giữa các sessions
- Version control cho decisions và rationale

---

## 5. Cấu Trúc Thư Mục Chuẩn

```
project-root/
├── .kiro/
│   ├── plans/
│   │   └── {PROJECT-ID}/
│   │       ├── brd.md                          # Business Requirements Document
│   │       ├── inputs/                         # Tài liệu đầu vào
│   │       │   ├── vision-document.md
│   │       │   ├── api-specs/
│   │       │   │   └── *.yaml, *.json
│   │       │   └── external-docs/
│   │       │
│   │       └── aidlc-docs/                     # Tài liệu AI-DLC
│   │           │
│   │           ├── inception/                   # Giai đoạn Khởi tạo
│   │           │   ├── requirements/
│   │           │   │   ├── functional-requirements.md
│   │           │   │   ├── non-functional-requirements.md
│   │           │   │   ├── user-stories.md
│   │           │   │   └── clarification-qa.md
│   │           │   │
│   │           │   ├── application-design/
│   │           │   │   ├── system-context.md
│   │           │   │   ├── architecture-overview.md
│   │           │   │   ├── tech-stack.md
│   │           │   │   └── design-decisions.md
│   │           │   │
│   │           │   └── plans/
│   │           │       ├── unit-of-work-list.md
│   │           │       ├── bolt-schedule.md
│   │           │       └── resource-allocation.md
│   │           │
│   │           ├── construction/                # Giai đoạn Xây dựng
│   │           │   ├── units-of-work/
│   │           │   │   ├── uow-001-*.md
│   │           │   │   ├── uow-002-*.md
│   │           │   │   └── uow-template.md
│   │           │   │
│   │           │   ├── architecture/
│   │           │   │   ├── component-diagram.md
│   │           │   │   ├── domain-model.md
│   │           │   │   ├── data-model.md
│   │           │   │   └── api-design.md
│   │           │   │
│   │           │   └── implementation-notes/
│   │           │       ├── tech-decisions.md
│   │           │       ├── patterns-used.md
│   │           │       └── refactoring-log.md
│   │           │
│   │           └── operations/                  # Giai đoạn Vận hành
│   │               ├── infrastructure/
│   │               │   ├── terraform/
│   │               │   ├── kubernetes/
│   │               │   ├── docker/
│   │               │   └── infrastructure-design.md
│   │               │
│   │               ├── deployment/
│   │               │   ├── deployment-plan.md
│   │               │   ├── rollback-procedures.md
│   │               │   ├── smoke-tests.md
│   │               │   └── release-notes-template.md
│   │               │
│   │               └── monitoring/
│   │                   ├── alerts-config.yaml
│   │                   ├── dashboard-setup.md
│   │                   ├── logging-strategy.md
│   │                   └── incident-response.md
│   │
│   └── steering/                                # Quy tắc và hướng dẫn
│       ├── ai-dlc-workflow.md
│       ├── coding-standards.md
│       └── review-checklist.md
│
├── src/                                         # Source code
├── tests/                                       # Tests
└── docs/                                        # Documentation công khai
```

---

## 6. Quy Trình Làm Việc (Workflow)

### 6.1 Khởi Đầu Dự Án Mới
1. Tạo thư mục dự án trong `.kiro/plans/{PROJECT-ID}/`
2. Tạo `inputs/vision-document.md` với ý tưởng ban đầu
3. AI phân tích và tạo `brd.md`
4. Team review và approve BRD

### 6.2 Inception Phase Workflow
1. **AI**: Đọc inputs, tạo clarification questions
2. **Team**: Trả lời questions trong `clarification-qa.md`
3. **AI**: Generate requirements documents
4. **Team**: Review và validate requirements
5. **AI**: Tạo application design và plans
6. **Team**: Approve và move to Construction

### 6.3 Construction Phase Workflow
1. **AI**: Chọn UoW từ plan, tạo detailed design
2. **Team**: Review design trong Team Assembly
3. **AI**: Implement code + tests
4. **Team**: Code review và merge
5. **Repeat** cho các UoW tiếp theo
6. **Integration**: AI tích hợp các UoW
7. **Team**: Acceptance testing

### 6.4 Operations Phase Workflow
1. **AI**: Tạo IaC và deployment scripts
2. **Team**: Review security và infrastructure
3. **AI**: Setup CI/CD và monitoring
4. **Team**: Validate và approve deployment
5. **AI**: Execute deployment
6. **Team**: Monitor và verify

---

## 7. Templates và Mẫu

### 7.1 Vision Document Template
```markdown
# Vision Document: {Project Name}

## Problem Statement
Mô tả vấn đề cần giải quyết...

## Target Users
Ai sẽ sử dụng hệ thống...

## Key Features
1. Feature 1
2. Feature 2

## Success Criteria
Định nghĩa thành công...

## Constraints
Các ràng buộc kỹ thuật, thời gian, ngân sách...
```

### 7.2 Unit of Work Template
```markdown
# UoW-{ID}: {Title}

## Objective
Mục tiêu của unit of work này...

## Input Dependencies
- Requirements từ inception
- Các UoW dependencies

## Tasks
1. [ ] Task 1
2. [ ] Task 2

## Acceptance Criteria
- [ ] Criteria 1
- [ ] Criteria 2

## Technical Notes
Ghi chú kỹ thuật...

## Estimated Effort
X hours/days

## Status
[ ] Not Started | [ ] In Progress | [ ] Done
```

---

## 8. Lợi Ích và ROI

### 8.1 Lợi Ích
- **Tốc độ**: 5-10x nhanh hơn quy trình truyền thống
- **Chất lượng**: Code được test tốt hơn, tài liệu đầy đủ
- **Truy vết**: Toàn bộ decisions được document
- **Onboarding**: Dễ dàng cho members mới hiểu dự án
- **Consistency**: Quy trình chuẩn hóa trên toàn team

### 8.2 Metrics Đo Lường
- Time to market: từ ý tưởng đến production
- Code coverage: % test coverage
- Documentation completeness: % features có docs
- Team satisfaction: feedback từ developers

---

## 9. Best Practices

### 9.1 Cho AI
- Luôn đặt clarification questions trước khi implement
- Document rationale cho mọi technical decisions
- Generate tests cùng với code
- Update documentation khi code changes

### 9.2 Cho Con Người
- Review AI output kỹ càng, đặc biệt security
- Provide clear, detailed feedback
- Keep context repository updated
- Participate actively trong Team Building/Assembly

### 9.3 Cho Team
- Daily sync để align progress
- Weekly retrospective để improve process
- Maintain single source of truth trong repo
- Version control everything

---

## 10. Roadmap và Phát Triển

### Phase 1: Foundation (Hiện tại)
- [x] Define framework structure
- [x] Create BRD
- [ ] Create all templates
- [ ] Setup example project

### Phase 2: Tooling
- [ ] CLI tools để init projects
- [ ] AI prompts library
- [ ] Validation scripts

### Phase 3: Integration
- [ ] IDE extensions
- [ ] CI/CD templates
- [ ] Monitoring dashboards

---

## 11. Tài Liệu Tham Khảo

- [AI-DLC Core Framework Article](https://viblo.asia/p/ai-native-development-ai-dlc-core-framework-giai-phau-mot-vong-doi-phat-trien-thuan-ai-QyJKz7oM4Me)
- [Architecture Decision Records](https://adr.github.io/)
- [C4 Model for Software Architecture](https://c4model.com/)

---

## Phụ Lục

### A. Glossary
- **Bolt**: Chu kỳ phát triển ngắn (giờ/ngày)
- **UoW**: Unit of Work - đơn vị công việc
- **IaC**: Infrastructure as Code
- **Team Building**: Buổi họp validate ở Inception
- **Team Assembly**: Buổi họp làm rõ kỹ thuật ở Construction

### B. FAQ
**Q: AI-DLC khác Agile như thế nào?**
A: AI-DLC tận dụng AI để tự động hóa nhiều tasks, rút ngắn chu kỳ từ tuần xuống giờ/ngày.

**Q: Có cần AI tool gì để sử dụng?**
A: Có thể dùng Claude, GPT-4, hoặc các AI code assistants khác.

**Q: Có phù hợp với mọi loại dự án?**
A: Phù hợp nhất với dự án vừa/nhỏ, greenfield projects. Large legacy systems cần adapt.