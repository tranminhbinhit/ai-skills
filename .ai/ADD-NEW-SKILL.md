# Add New Skill - Standard Process

Document này hướng dẫn AI agent cách cập nhật toàn bộ hệ thống khi có skill mới được cài đặt.

---

## 🎯 Mục Đích

Khi user nói: **"Hãy cập nhật các skill chưa có vào danh sách skill route"**

AI agent sẽ:
1. Scan `.kiro/skills/` directory
2. So sánh với `.ai/routing/skill-routing.md`
3. Tự động cập nhật tất cả files cần thiết
4. Đảm bảo 100% consistency

---

## 📋 Checklist - Files Cần Update

Khi thêm skill mới, **PHẢI** update các files sau theo thứ tự:

### Bước 1: Scan & Identify (Tự động)
```bash
# Scan installed skills
ls -la .kiro/skills/

# Read existing routing
cat .ai/routing/skill-routing.md

# Identify missing skills
# (Skills có trong .kiro/skills/ nhưng KHÔNG có trong routing)
```

### Bước 2: Read Skill Metadata (Tự động)
Với mỗi skill mới, đọc file SKILL.md để lấy:
```yaml
name: <skill-name>
description: <what it does>
triggers: <keywords that trigger this skill>
domain: <frontend/backend/quality/sdlc/etc>
```

### Bước 3: Update Files (Theo Template)

#### ✅ File 1: `.ai/context/project-context.md`

**Location**: `## Installed Skills Registry` table

**Template**:
```markdown
| Nhóm | Skill | Location | Dùng khi nào |
|---|---|---|---|
| <Domain> | <skill-name> | `.kiro/skills/<skill-name>/` | <use-case-summary> |
```

**Update also**:
- `## Quick Reference` section
- `## Skill Installation Status` count

---

#### ✅ File 2: `.ai/routing/skill-routing.md`

**Location**: `## Installed Skills` section

**Template**:
```markdown
### <Domain Category>
**Skill**: `<skill-name>`  
**Location**: `.kiro/skills/<skill-name>/`  
**Trigger when**: <keyword1>, <keyword2>, <keyword3>, ...
```

**Location**: `## Routing Rules by Domain` section

**Template**:
```markdown
### <Domain Name>
Nếu task liên quan đến <keywords>:
- **Ưu tiên skill**: `<skill-name>`
- [Additional notes if needed]
```

---

#### ✅ File 3: `skills-lock.json`

**Location**: `skills` object

**Template**:
```json
"<skill-name>": {
  "name": "<skill-name>",
  "version": "<version>",
  "location": ".kiro/skills/<skill-name>/",
  "source": "<github-repo-url>",
  "sourceType": "github",
  "skillPath": "skills/<skill-name>/SKILL.md",
  "license": "<license>",
  "author": "<author>",
  "description": "<full-description>",
  "domain": "<domain>",
  "triggers": [
    "<trigger1>",
    "<trigger2>",
    "<trigger3>"
  ],
  "installedAt": "<current-date>",
  "computedHash": "<hash-from-lock>"
}
```

**Location**: `domains` object

Add skill to appropriate domain array:
```json
"<domain>": [
  "existing-skill",
  "<new-skill-name>"
]
```

---

#### ✅ File 4: `readme.md`

**Location**: `## 📦 Installed Skills` section

**Template**:
```markdown
### <Domain> (<count> skills)
<number>. **<skill-name>** - <short-description>
```

**Location**: `## 🎯 Skill Routing` table

**Template**:
```markdown
| Domain | Keywords | Skill |
|--------|----------|-------|
| **<Domain>** | <keywords> | `<skill-name>` |
```

---

#### ✅ File 5: `Promt-example.md`

**Add examples for the new skill**:

**Location**: `## 🎯 AUTO Mode` section

**Template**:
```markdown
### <Domain Category>

\`\`\`
<Example prompt that would trigger this skill>
\`\`\`
→ Tự động load: `<skill-name>`
```

**Location**: Add to other modes (FORCED, EXCLUSIVE) if relevant

---

#### ✅ File 6: `.ai/INDEX.md`

**Location**: `## 📦 Installed Skills Reference` table

**Template**:
```markdown
| Need | Skill | Doc Link |
|------|-------|----------|
| <use-case> | <skill-name> | [SKILL.md](../.kiro/skills/<skill-name>/SKILL.md) |
```

---

## 🤖 Automated Prompt Template

User chỉ cần nói:

```
Hãy cập nhật các skill chưa có vào danh sách skill route
```

AI sẽ tự động:

### Step 1: Scan & Compare
```bash
# List installed skills
INSTALLED=$(ls .kiro/skills/)

# List documented skills
DOCUMENTED=$(grep "**Skill**:" .ai/routing/skill-routing.md | awk '{print $2}')

# Find missing
MISSING=$(comm -23 <(echo "$INSTALLED" | sort) <(echo "$DOCUMENTED" | sort))
```

### Step 2: For Each Missing Skill
```bash
# Read skill metadata
SKILL_NAME=$(grep "^name:" .kiro/skills/$SKILL/SKILL.md | cut -d: -f2)
DESCRIPTION=$(grep "^description:" .kiro/skills/$SKILL/SKILL.md | cut -d: -f2)

# Extract triggers (analyze description for keywords)
# Determine domain (based on description/triggers)
```

### Step 3: Update All Files
Update files theo templates ở trên, section by section.

### Step 4: Verify
- Check all 6 files updated
- Check consistency (same skill-name everywhere)
- Check count matches (e.g., 7 skills → all files say 7)

---

## 📝 Example: Adding "pdf-processor" Skill

Assume we have `.kiro/skills/pdf-processor/SKILL.md`:
```yaml
name: pdf-processor
description: Process PDF documents, extract text, analyze structure
triggers: PDF, document processing, text extraction
domain: document-processing
```

### Updates Required:

**1. project-context.md**:
```markdown
| Document Processing | pdf-processor | `.kiro/skills/pdf-processor/` | PDF extraction, document analysis |
```

**2. skill-routing.md**:
```markdown
### Document Processing
**Skill**: `pdf-processor`  
**Location**: `.kiro/skills/pdf-processor/`  
**Trigger when**: PDF, document processing, text extraction, analyze PDF
```

**3. skills-lock.json**:
```json
"pdf-processor": {
  "name": "pdf-processor",
  "version": "1.0",
  "location": ".kiro/skills/pdf-processor/",
  "source": "https://github.com/anthropics/skills",
  "sourceType": "github",
  "skillPath": "skills/pdf-processor/SKILL.md",
  "description": "Process PDF documents, extract text, analyze structure",
  "domain": "document-processing",
  "triggers": ["PDF", "document processing", "text extraction"],
  "installedAt": "2026-06-28T00:00:00.000Z"
}
```

**4. readme.md**:
```markdown
### Document Processing (1 skill)
8. **pdf-processor** - PDF extraction and analysis
```

**5. Promt-example.md**:
```markdown
### Document Processing

\`\`\`
Extract text from annual-report.pdf and summarize key findings
\`\`\`
→ Tự động load: `pdf-processor`
```

**6. INDEX.md**:
```markdown
| PDF processing | pdf-processor | [SKILL.md](../.kiro/skills/pdf-processor/SKILL.md) |
```

---

## 🎯 Validation Checklist

Sau khi update, verify:

- [ ] Skill appears in project-context.md registry table
- [ ] Skill appears in project-context.md Quick Reference
- [ ] Skill count updated in project-context.md
- [ ] Skill documented in skill-routing.md Installed Skills
- [ ] Routing rule added in skill-routing.md Routing Rules
- [ ] Skill metadata in skills-lock.json
- [ ] Skill added to domain array in skills-lock.json
- [ ] Skill listed in readme.md Installed Skills
- [ ] Skill added to readme.md routing table
- [ ] Examples added to Promt-example.md
- [ ] Skill in INDEX.md reference table
- [ ] All skill names consistent across files
- [ ] Skill count matches in all files

---

## 🔄 Batch Update Process

Nếu có **nhiều skills** cần update cùng lúc:

### Single Prompt:
```
Hãy cập nhật các skill chưa có vào danh sách skill route

Skills cần update:
1. <skill-1>
2. <skill-2>
3. <skill-3>
```

### AI sẽ:
1. Scan tất cả skills trong list
2. Đọc metadata của từng skill
3. Update ALL 6 files cho TẤT CẢ skills
4. Verify consistency
5. Report kết quả

---

## 📊 Domain Categories

Khi thêm skill mới, xác định domain phù hợp:

| Domain | Description | Example Skills |
|--------|-------------|----------------|
| **frontend** | UI frameworks, components | angular-developer, react-builder |
| **frontend-design** | Visual design, UI/UX | frontend-design |
| **frontend-review** | UI/UX auditing | web-design-guidelines |
| **backend** | API, services, middleware | nodejs-api, nestjs-expert |
| **database** | Schema, queries, ORM | postgresql-expert, prisma-helper |
| **quality** | Code review, testing | code-review-expert, test-engineer |
| **devops** | CI/CD, deployment | docker-expert, k8s-deployer |
| **sdlc** | Project management, workflow | ai-dlc-orchestrator |
| **document-processing** | PDF, Word, text extraction | pdf-processor |
| **data-analysis** | Data processing, analytics | data-analyzer |

Nếu domain chưa tồn tại → Tạo domain category mới.

---

## 🚨 Common Mistakes to Avoid

❌ **DON'T**:
1. Update một file mà quên files khác
2. Dùng skill-name không consistent
3. Quên update skill count
4. Bỏ qua domain mapping trong skills-lock.json
5. Không add examples vào Promt-example.md

✅ **DO**:
1. Update TẤT CẢ 6 files
2. Maintain exact skill-name everywhere
3. Update counts in project-context.md và readme.md
4. Add to domains array in skills-lock.json
5. Provide at least 1 example in Promt-example.md

---

## 💡 Smart Prompt Examples

### Example 1: Simple Update
```
User: Hãy cập nhật các skill chưa có vào danh sách skill route

AI:
1. Scanning .kiro/skills/...
2. Found 2 new skills: pdf-processor, test-engineer
3. Reading metadata...
4. Updating 6 files...
5. ✅ Done! Added 2 skills to all documentation.
```

### Example 2: Specific Skills
```
User: Add these skills to routing:
- pdf-processor
- test-engineer
- docker-expert

AI:
1. Reading skill metadata...
2. Updating project-context.md...
3. Updating skill-routing.md...
4. Updating skills-lock.json...
5. Updating readme.md...
6. Updating Promt-example.md...
7. Updating INDEX.md...
8. ✅ All 3 skills documented!
```

### Example 3: Verify Only
```
User: Check if all installed skills are documented

AI:
Installed: 10 skills
Documented: 7 skills
Missing: 3 skills
  - pdf-processor
  - test-engineer
  - docker-expert

Would you like me to add them?
```

---

## 📦 Template Structure Summary

```
NEW SKILL
    ↓
Read SKILL.md
    ↓
Extract: name, description, triggers, domain
    ↓
Update 6 Files:
    ├── .ai/context/project-context.md      (Registry + Quick Ref + Count)
    ├── .ai/routing/skill-routing.md        (Installed + Routing Rules)
    ├── skills-lock.json                    (Metadata + Domain Array)
    ├── readme.md                           (Skills List + Routing Table)
    ├── Promt-example.md                    (Usage Examples)
    └── .ai/INDEX.md                        (Reference Table)
    ↓
Verify Consistency
    ↓
✅ Done!
```

---

## 🎓 For AI Agents

Khi nhận prompt: **"Hãy cập nhật các skill chưa có vào danh sách skill route"**

Execute this workflow:

```python
# 1. Scan
installed_skills = list_directory(".kiro/skills/")
documented_skills = extract_skills_from_routing()
missing_skills = installed_skills - documented_skills

# 2. For each missing skill
for skill in missing_skills:
    # Read metadata
    metadata = read_skill_md(f".kiro/skills/{skill}/SKILL.md")
    
    # 3. Update files
    update_project_context(skill, metadata)
    update_skill_routing(skill, metadata)
    update_skills_lock_json(skill, metadata)
    update_readme(skill, metadata)
    update_prompt_examples(skill, metadata)
    update_index(skill, metadata)

# 4. Verify
verify_consistency()
verify_counts()

# 5. Report
print(f"✅ Added {len(missing_skills)} skills to all documentation")
```

---

## ✅ Success Criteria

Update thành công khi:

1. ✅ All missing skills added to 6 files
2. ✅ Skill names consistent across all files
3. ✅ Skill counts match everywhere
4. ✅ At least 1 example per skill
5. ✅ Domain properly categorized
6. ✅ Triggers/keywords documented
7. ✅ Routing rules clear and specific

---

## 📞 Quick Reference

**Single Prompt**:
```
Hãy cập nhật các skill chưa có vào danh sách skill route
```

**Files to Update**:
1. `.ai/context/project-context.md`
2. `.ai/routing/skill-routing.md`
3. `skills-lock.json`
4. `readme.md`
5. `Promt-example.md`
6. `.ai/INDEX.md`

**Verify**:
- Consistency ✅
- Counts match ✅
- Examples added ✅

**Done!** 🎉
