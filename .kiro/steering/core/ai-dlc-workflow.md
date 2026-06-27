---
title: AI-DLC Workflow Guide
description: Quy trình làm việc chuẩn cho AI Development Life Cycle
inclusion: always
---

# AI-DLC Workflow Guide

## Mục Đích
Document này hướng dẫn cách làm việc với AI theo quy trình AI-DLC trong dự án.

---

## Workflow Tổng Quan

```
Vision → Inception → Construction → Operations → Continuous Improvement
   ↓         ↓            ↓              ↓              ↓
 Input    Requirements   Code         Deploy        Monitor
          & Design                                  & Learn
```

---

## Giai Đoạn 1: Inception (Khởi Tạo)

### Vai Trò AI
1. **Đọc và phân tích** vision document và inputs
2. **Đặt câu hỏi làm rõ** trong `clarification-qa.md`
3. **Tạo requirements**:
   - Functional requirements
   - Non-functional requirements
   - User stories
4. **Đề xuất application design**
5. **Phân rã thành Units of Work**

### Vai Trò Con Người
1. **Trả lời clarification questions**
2. **Review và validate** requirements
3. **Approve** application design
4. **Prioritize** UoW list

### Output Checkpoint
- [ ] Functional requirements approved
- [ ] Non-functional requirements approved
- [ ] User stories validated
- [ ] Architecture design approved
- [ ] UoW list prioritized

---

## Giai Đoạn 2: Construction (Xây Dựng)

### Workflow cho Mỗi UoW

#### Step 1: UoW Planning
**AI làm**:
- Đọc UoW từ `unit-of-work-list.md`
- Tạo detailed UoW document trong `construction/units-of-work/`
- Đề xuất technical design
- Break down thành tasks

**Con người làm**:
- Review technical design
- Clarify requirements
- Approve approach

#### Step 2: Implementation
**AI làm**:
- Generate code theo design
- Implement tests (unit + integration)
- Update documentation
- Follow coding standards trong `.kiro/steering/coding-standards.md`

**Con người làm**:
- Monitor progress
- Answer questions
- Review code incrementally

#### Step 3: Verification
**AI làm**:
- Run tests
- Check linting/formatting
- Verify acceptance criteria
- Run build

**Con người làm**:
- Manual testing
- Security review
- Performance check

#### Step 4: Integration
**AI làm**:
- Create pull request
- Document changes
- Update UoW status to "Done"

**Con người làm**:
- Final code review
- Merge to main

### Output Checkpoint cho Mỗi UoW
- [ ] Code implemented
- [ ] Tests written (>80% coverage)
- [ ] Tests passing
- [ ] Code reviewed
- [ ] Documentation updated
- [ ] UoW marked as Done

---

## Giai Đoạn 3: Operations (Vận Hành)

### Vai Trò AI
1. **Tạo Infrastructure as Code**:
   - Docker/Kubernetes configs
   - Terraform/CloudFormation
2. **Setup CI/CD pipeline**
3. **Tạo monitoring configs**
4. **Generate deployment scripts**
5. **Viết deployment plan**

### Vai Trò Con Người
1. **Review security** của infrastructure
2. **Validate deployment plan**
3. **Execute deployment** (hoặc approve auto-deploy)
4. **Monitor** production

### Output Checkpoint
- [ ] Infrastructure code reviewed
- [ ] CI/CD pipeline working
- [ ] Monitoring configured
- [ ] Deployment plan approved
- [ ] Successfully deployed to staging
- [ ] Successfully deployed to production

---

## Best Practices

### Cho AI (Auto-reminders)
- [ ] Luôn đọc related requirements trước khi code
- [ ] Generate tests cùng với code
- [ ] Document decisions trong implementation notes
- [ ] Update traceability matrix
- [ ] Ask clarification questions sớm
- [ ] Follow project coding standards

### Cho Con Người
- [ ] Review AI output trong vòng 1-2 giờ (để maintain momentum)
- [ ] Provide clear, specific feedback
- [ ] Update context documents when requirements change
- [ ] Participate actively trong Team Building/Assembly
- [ ] Trust but verify AI's work

### Cho Team
- [ ] Daily sync (15 min) để align
- [ ] Keep all context in repository (không dùng external docs)
- [ ] Version control everything
- [ ] Document all decisions
- [ ] Maintain single source of truth

---

## Communication Protocols

### Clarification Questions Format
```markdown
**Q**: [Clear, specific question]
**Context**: [Why this matters, what you've considered]
**Options**: [If applicable, list options considered]
```

### Decision Documentation Format
```markdown
**Decision**: [What was decided]
**Rationale**: [Why this was chosen]
**Alternatives Considered**: [What else was evaluated]
**Trade-offs**: [What we gain/lose]
**Date**: [When decided]
**Participants**: [Who was involved]
```

---

## Quality Gates

### Gate 1: After Inception
**Cannot proceed to Construction unless**:
- All clarification questions answered
- Requirements reviewed and approved
- Application design approved
- UoW list created and prioritized

### Gate 2: After Each UoW
**Cannot mark UoW as Done unless**:
- Acceptance criteria met
- Tests passing (>80% coverage)
- Code reviewed
- Documentation updated

### Gate 3: Before Deployment
**Cannot deploy unless**:
- All UoWs completed
- Integration tests passing
- Security scan passed
- Deployment plan approved
- Rollback plan ready

---

## Context Preservation

### What to Store in Repository
- All planning documents
- All requirements and specs
- All design decisions
- All clarification Q&A
- All implementation notes
- All architecture diagrams (as code or markdown)

### What NOT to Store
- Sensitive credentials (use env vars)
- Large binary files (use Git LFS or external storage)
- IDE-specific settings (unless team standard)

---

## Continuous Improvement

### After Each Bolt
**Retrospective Questions**:
1. What went well?
2. What could be improved?
3. What actions should we take?

**Update**:
- This workflow document if process changes
- Coding standards if new patterns emerge
- Templates if better formats found

### Metrics to Track
- Time from vision to production
- Number of clarification rounds needed
- Test coverage %
- Deployment frequency
- Rollback rate

---

## Quick Reference Commands

### For AI
```markdown
# Start new UoW
1. Read `.kiro/plans/{project}/aidlc-docs/inception/plans/unit-of-work-list.md`
2. Copy `.kiro/plans/{project}/aidlc-docs/construction/units-of-work/uow-template.md`
3. Create `uow-{number}-{title}.md`
4. Fill in all sections
5. Request review

# Complete UoW
1. Verify all acceptance criteria
2. Run tests
3. Update documentation
4. Mark status as Done in unit-of-work-list.md
5. Create PR
```

### For Humans
```markdown
# Review AI output
1. Read the proposed changes
2. Check against requirements
3. Provide feedback in comments
4. Approve or request changes

# Update requirements
1. Edit appropriate .md file in `inception/requirements/`
2. Document reason for change
3. Update change log
4. Notify AI to re-read
```

---

## Troubleshooting

### Issue: AI không hiểu requirement
**Solution**:
- Add more context to vision document
- Answer clarification questions with examples
- Reference similar features implemented before

### Issue: Too many clarification questions
**Solution**:
- Improve initial vision document detail
- Add reference documents to `inputs/`
- Include API specs, mockups, examples

### Issue: Code quality không đạt
**Solution**:
- Update coding standards in `.kiro/steering/coding-standards.md`
- Provide specific examples in review comments
- Add automated linting rules

---

## Templates & Shortcuts

### Quick Start New Project
```bash
# Copy template structure
cp -r .kiro/plans/cr-ai-dlc-example .kiro/plans/{new-project-id}

# Fill in vision document
vim .kiro/plans/{new-project-id}/inputs/vision-document.md

# AI: Start inception phase
# Human: Review and approve
```

---

## Change Log
| Version | Date | Changes |
|---------|------|---------|
| 1.0 | [Date] | Initial workflow guide |
