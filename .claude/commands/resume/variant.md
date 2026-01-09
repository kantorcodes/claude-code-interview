---
description: 为特定公司创建定制化简历变体
argument-hint: <company-name>
allowed-tools: Read, Write, Edit, Skill(jd-analyzer)
---

# 创建简历变体

为 **$ARGUMENTS** 创建定制化简历变体。

## 工作流程

### 步骤 1: 检查公司信息
首先检查是否已添加该公司的JD信息。

如果 `data/companies/$ARGUMENTS.json` 不存在，提示用户：
```
未找到 $ARGUMENTS 的公司信息。
请先运行 /company/add $ARGUMENTS 添加公司信息和JD。
```

### 步骤 2: 使用 jd-analyzer Skill
调用 jd-analyzer Skill 分析该公司的JD：
- 提取必需技能和优先技能
- 识别关键关键词
- 分析公司文化
- 评估与基础简历的匹配度

### 步骤 3: 创建简历变体
基于JD分析结果，创建 `data/resume/variants/$ARGUMENTS.json`：

```json
{
  "variant_id": "$ARGUMENTS",
  "parent_resume": "base.json",
  "created_at": "当前时间",
  "updated_at": "当前时间",
  "target_company": "$ARGUMENTS",
  "optimizations": {
    "highlighted_skills": [...],
    "emphasized_projects": [...],
    "tailored_summary": "...",
    "keywords_to_emphasize": [...],
    "reordered_sections": [...]
  }
}
```

### 步骤 4: 优化建议
提供详细的优化建议，包括：
- 哪些技能应该突出显示
- 哪些项目经验应该强调
- Summary如何调整
- 成就描述如何重写
- 建议的关键词插入位置

### 步骤 5: 生成报告
输出匹配度分析报告：
```
# $ARGUMENTS 简历匹配度分析

## 匹配度评分: XX/100

### ✅ 完全匹配的技能
- ...

### ⚠️ 部分匹配的技能
- ...

### ❌ 缺失的关键技能
- ...

## 优化建议
1. ...
2. ...
3. ...

## 下一步
使用 /resume/generate $ARGUMENTS 生成Markdown简历
```

## 注意事项
- 确保公司信息文件已存在
- JD分析需要 jd-analyzer Skill
- 简历变体不会修改基础简历
- 可以为同一公司创建多个变体（不同职位）
