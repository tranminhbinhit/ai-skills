# Quick Reference Card

Cheat sheet nhanh cho việc quản lý skills.

---

## 🎯 Single Command to Add New Skills

```
Hãy cập nhật các skill chưa có vào danh sách skill route
```

**AI sẽ tự động**:
- ✅ Scan `.kiro/skills/` để tìm skills mới
- ✅ Đọc metadata từ SKILL.md của mỗi skill
- ✅ Update 6 files cần thiết
- ✅ Verify consistency
- ✅ Report kết quả

---

## 📋 6 Files Được Auto-Update

Khi run command trên, AI sẽ update:

1. **`.ai/context/project-context.md`**
   - Installed Skills Registry table
   - Quick Reference section
   - Skill Installation Status count

2. **`.ai/routing/skill-routing.md`**
   - Installed Skills section
   - Routing Rules by Domain

3. **`skills-lock.json`**
   - skills object (metadata)
   - domains array (categorization)

4. **`readme.md`**
   - Installed Skills list
   - Skill Routing table

5. **`Promt-example.md`**
   - Usage examples (AUTO mode minimum)

6. **`.ai/INDEX.md`**
   - Quick lookup table

---

## 🔄 Complete Workflow

### Step 1: Install Skill
```bash
npx skills add <repo-url> --skill <skill-name>
```

### Step 2: Update Documentation (ONE COMMAND)
```
Hãy cập nhật các skill chưa có vào danh sách skill route
```

### Step 3: Verify (Optional)
```
Check if all installed skills are documented
```

### Done! ✅

---

## 📊 Common Commands

### Check Status
```
Check if all installed skills are documented
```

### Update Missing
```
Hãy cập nhật các skill chưa có vào danh sách skill route
```

### Sync All
```
Ensure all skill documentation is in sync
```

### Coverage Report
```
Show skill documentation coverage report
```

---

## 🎓 Skill Usage Modes

### AUTO Mode (Default)
```
"Create Angular component"
```
→ AI auto-selects appropriate skill

### FORCED Mode
```
Mode=FORCED
Skills: skill-1, skill-2
Task: <description>
```
→ AI uses only specified skills

### EXCLUSIVE Mode
```
ONLY use skill: skill-name
Task: <description>
```
→ AI uses only that one skill

---

## 📁 File Locations

| File | Purpose |
|------|---------|
| `.ai/context/project-context.md` | Skills registry |
| `.ai/routing/skill-routing.md` | Routing rules |
| `skills-lock.json` | Version tracking |
| `readme.md` | Main docs |
| `Promt-example.md` | Usage examples |
| `.ai/INDEX.md` | Navigation index |

---

## 🚀 Most Used Prompts

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

## 📚 Documentation Links

**For New Users**:
- [README.md](../README.md) - AI-DLC & multi-agent setup
- [PROMPTS.md](../PROMPTS.md) - Usage examples & templates

**For Developers**:
- [ADD-NEW-SKILL.md](./ADD-NEW-SKILL.md) - How to add skills
- [PROMPTS.md](../PROMPTS.md) - Management templates

**For Understanding**:
- [project-context.md](./context/project-context.md) - What skills exist
- [skill-routing.md](./routing/skill-routing.md) - How routing works

---

## 🎯 Quick Tips

✅ **DO**:
- Use single command: `"Hãy cập nhật..."`
- Let AI auto-detect and update
- Verify after bulk operations

❌ **DON'T**:
- Manually edit 6 files
- Update files inconsistently
- Forget to verify

---

## 💡 Remember

**One command does it all**:
```
Hãy cập nhật các skill chưa có vào danh sách skill route
```

That's it! AI handles the rest. 🎉
