---
description: 根据JSON简历生成格式化的Markdown文档
argument-hint: [variant-name]
allowed-tools: Read, Write, Edit
---

# 生成Markdown简历

将简历数据转换为格式化的Markdown文档。

## 参数说明
- **variant-name**: 可选，指定要生成的简历变体
  - 省略或使用 "base": 生成基础简历
  - 使用公司名（如 "google"）: 生成该公司定制简历

## 工作流程

### 步骤 1: 读取简历数据
- 如果指定了变体，读取 `data/resume/variants/{variant}.json`
- 否则读取 `data/resume/base.json`

### 步骤 2: 应用模板
使用 `templates/resume_template.md` 模板生成简历

### 步骤 3: 生成Markdown
创建 `exports/resumes/{name}_resume.md` 文件

### 步骤 4: 输出结果
显示生成的文件路径和预览

## 简历模板结构

```markdown
# {姓名}

{联系方式}

## 专业总结
{summary}

## 技能
### 编程语言
{skills.programming_languages}

### 框架和库
{skills.frameworks}

### 数据库
{skills.databases}

### 工具
{skills.tools}

### 技术概念
{skills.concepts}

## 工作经历

### {职位} | {公司} | {时间}
{工作总结}

**成就**:
- {成就1}
- {成就2}
**技术栈**: {technologies}

## 项目经验

### {项目名称} | {角色}
{项目描述}

**成就**:
- {成就1}
- {成就2}
**技术**: {technologies}
**链接**: {url}

## 教育背景

### {学位} | {学校} | {时间}
**GPA**: {gpa}
**荣誉**: {honors}
**相关课程**: {courses}

## 认证证书
{certifications}

## 语言能力
{languages}
```

## 输出示例

```
✅ 简历已生成: exports/resumes/google_resume.md

📄 文件内容预览:
# 张三

📧 zhangsan@example.com | 📱 +86 138-0000-0000
📍 北京, 中国
🔗 linkedin.com/in/zhangsan | 💻 github.com/zhangsan

## 专业总结
资深软件工程师，专注于分布式系统和机器学习...
...
```

## 下一步操作
- 查看生成的Markdown文件
- 可以手动编辑微调
- 转换为PDF（使用pandoc或其他工具）
- 用于投递简历
