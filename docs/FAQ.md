# 常见问题 (FAQ)

## 📚 基础问题

### Q: 这个项目是什么？

**A**: 这是一个基于 Claude Code 的面试求职管理系统，帮助您：
- 导入和管理简历
- 为不同公司创建定制化简历
- 分析职位描述（JD）
- 准备面试
- 模拟真实面试场景

### Q: 需要什么前置条件？

**A**: 您需要安装 [Claude Code](https://code.claude.com)：

```bash
npm install -g @anthropic-ai/claude-code
```

### Q: 是否需要数据库？

**A**: 不需要！系统使用纯 JSON + Markdown 存储，零依赖。

---

## 📄 简历相关

### Q: 支持哪些简历格式？

**A**: 支持三种格式：
- ✅ **Markdown** (`.md`) - 最推荐，解析最准确
- ✅ **PDF** (`.pdf`)
- ✅ **Word** (`.docx`)

### Q: 如何导入简历？

**A**: 使用 `/resume/import` 命令：

```bash
/resume/import /path/to/your/resume.md
```

### Q: 导入简历后需要手动调整吗？

**A**: 建议检查并补充：
- 电话号码格式
- 项目链接
- 认证证书信息
- 系统可能未能识别的内容

### Q: 可以为不同公司创建不同简历吗？

**A**: 可以！使用 `/resume/variant <company>` 为每个公司创建定制简历：

```bash
/resume/variant google
/resume/variant meta
/resume/variant amazon
```

---

## 🏢 公司和 JD 相关

### Q: 如何添加公司信息？

**A**: 使用 `/company/add` 命令：

```bash
/company/add google
```

系统会引导您输入：
1. 公司基本信息
2. 职位信息
3. 完整的职位描述（JD）

### Q: JD 支持哪些格式？

**A**: 您可以：
1. **直接粘贴** JD 文本
2. **提供文件路径**（.txt, .md, .pdf）
3. **提供在线链接**（LinkedIn、公司官网等）

### Q: 为什么需要完整保存 JD？

**A**: 完整的 JD 用于：
- 精确的简历优化和关键词匹配
- 准确的面试准备
- 全面的技能匹配评估
- 面试前快速回顾
- 不同职位的对比

### Q: 如何查看保存的 JD？

**A**: 使用 `/company/jd` 命令：

```bash
/company/jd google
```

---

## 🎓 面试准备相关

### Q: 支持哪些类型的面试模拟？

**A**: 支持 4 种类型：
- `technical` - 技术面试（编码、算法）
- `system-design` - 系统设计
- `behavioral` - 行为面试（STAR 法则）
- `hr` - HR 面试

### Q: 如何生成面试准备指南？

**A**: 使用 `/interview/prep` 命令：

```bash
/interview/prep google
```

系统会生成包括：
- 技术主题清单
- 推荐练习题
- 公司特定准备建议
- 时间规划

### Q: 模拟面试会提供反馈吗？

**A**: 是的！每次模拟面试后，系统会提供：
- 总体评分（1-5 分）
- 优势和不足
- 具体改进建议
- 下一步准备方向

---

## 💾 数据存储相关

### Q: 数据存储在哪里？

**A**: 所有数据以 JSON 格式存储在 `data/` 目录：
- `data/resume/` - 简历数据
- `data/companies/` - 公司信息
- `data/interviews/` - 面试记录
- `data/questions/` - 面试题库
- `data/analytics/` - 进度追踪

### Q: 如何备份我的数据？

**A**: 备份整个项目目录即可：

```bash
# 使用 git
git add .
git commit -m "Backup data"
git push

# 或手动备份
cp -r . claude-code-interview-backup/
```

### Q: 可以在多台电脑上使用吗？

**A**: 可以！通过 Git 同步项目：

1. 将项目推送到 GitHub
2. 在其他电脑上克隆
3. 继续使用

**注意**: `data/` 目录建议添加到 `.gitignore`，不要上传敏感信息。

---

## 🔧 技术问题

### Q: Word 文档导入需要 pandoc 吗？

**A**: 是的。安装 pandoc：

```bash
# macOS
brew install pandoc

# Linux
sudo apt-get install pandoc

# Windows
# 从 https://pandoc.org/installing.html 下载
```

### Q: PDF 解析不准确怎么办？

**A**: PDF 解析可能不完美，建议：
1. 使用标准简历模板
2. 确保格式清晰
3. 导入后手动检查和补充
4. 或转换为 Markdown 后导入

### Q: 命令无法识别怎么办？

**A**: 确保：
1. 已安装 Claude Code
2. 在项目根目录运行
3. 命令文件存在于 `.claude/commands/` 目录

---

## 🚀 高级功能

### Q: 可以自定义简历模板吗？

**A**: 可以！编辑 `templates/resume_template.md`：

```markdown
# {name}

{contact_line}

## 专业总结
{summary}

...
```

### Q: 如何添加新的面试类型？

**A**: 在 `.claude/commands/interview/` 目录下创建新的命令文件，参考现有命令格式。

### Q: 如何扩展 Skills？

**A**: 在 `.claude/skills/` 目录下添加新的 Skill，遵循 SKILL.md 格式。

---

## 🐛 故障排除

### Q: 导入简历时解析失败

**A**: 检查：
1. 文件格式是否正确
2. 文件路径是否有效
3. 文件是否损坏
4. 尝试转换为 Markdown 格式

### Q: JD 分析结果不准确

**A**: 确保：
1. 提供完整的 JD 文本
2. JD 格式清晰
3. 包含职责和要求描述
4. 可以手动补充结构化信息

### Q: 生成简历格式不理想

**A**: 可以：
1. 自定义简历模板
2. 手动编辑生成的 Markdown
3. 使用 pandoc 转换为 PDF

---

## 📞 获取帮助

### 其他问题？

- 📧 发送邮件: your.email@example.com
- 💬 GitHub Discussions: [链接]
- 📖 查看文档: [README.md](README.md)
- 🔍 搜索已有 Issues: [Issues](https://github.com/yourusername/claude-code-interview/issues)

---

## 🔗 相关资源

- [Claude Code 官方文档](https://code.claude.com/docs)
- [功能增强说明](FEATURE_ENHANCEMENTS.md)
- [贡献指南](CONTRIBUTING.md)
