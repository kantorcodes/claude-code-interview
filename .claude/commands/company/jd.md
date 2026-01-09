---
description: 查看保存的职位描述（JD）原文
argument-hint: <company-name> [position-id]
allowed-tools: Read
---

# 查看职位描述（JD）

显示 **$1** 的职位描述原文。

## 参数说明
- **company-name**: 必需，公司名称
- **position-id**: 可选，职位ID
  - 如果公司只有一个职位，可以省略
  - 如果有多个职位，需要指定position_id

## 显示内容

### 1. JD基本信息
- 职位名称
- JD来源
- 保存时间
- JD长度

### 2. 完整JD原文
显示保存的完整JD文本，包括：
- 职位概述
- 职责描述
- 技能要求
- 资格要求
- 加分项
- 福利待遇

### 3. 结构化分析摘要
- 必需技能数量
- 优先技能数量
- 匹配度评分

## 使用示例

### 查看公司唯一职位的JD
```bash
/company/jd google
```

输出：
```
# Google - Software Engineer III (L4)

## JD信息
- **职位**: Software Engineer III, Cloud Platform
- **级别**: L4
- **地点**: Beijing, China
- **来源**: https://linkedin.com/jobs/view/123456789/
- **保存时间**: 2025-01-09 14:30:00
- **JD长度**: 2,456 字符

## 完整JD原文

职位描述

Google aims to build an AI that has the best understanding of the world's
information and is helpful to everyone. We're looking for software engineers
to join the Cloud Platform team and help us build the future of cloud computing.

Minimum qualifications:
- Bachelor's degree in Computer Science or equivalent practical experience
- 3 years of experience in software development
with knowledge of one or more of the following: Python, Java, C++
- Experience working with two or more from the following: web application
development, distributed or parallel systems, machine learning, information
retrieval, networking, developing large software systems, or security software
development

Preferred qualifications:
- Master's degree or PhD in Computer Science or related technical field
- 5 years of experience in distributed systems, machine learning,
information retrieval, networking or security software development
- Experience working with cloud computing platforms (AWS, Azure, Google Cloud)

Responsibilities:
- Design, develop, test, deploy, maintain and improve software.
- Manage individual project priorities, deadlines and deliverables.
- Contribute to the team's technical culture.

[完整JD内容...]

---

## 结构化分析摘要
- 必需技能: 7项
- 优先技能: 4项
- 匹配度: 75/100

## 快速操作
- /company/view google - 查看公司详情
- /resume/variant google - 创建定制简历
- /interview/prep google - 生成面试准备指南
```

### 查看公司特定职位的JD
```bash
/company/jd google pos_002
```

当公司有多个职位时，指定position_id。

## JD格式化显示

系统会格式化显示JD：
- 保留原始段落结构
- 高亮关键部分（技能、要求）
- 清晰的层级结构
- 易于阅读

## 导出JD

如果需要导出JD到文件：
```bash
# 导出为Markdown
/company/jd google > export_jd.md

# 导出为纯文本
/company/jd google > export_jd.txt
```

## JD对比

可以对比不同公司的JD：
```bash
# 先保存一个公司的JD
/company/jd google > google_jd.md

# 再保存另一个公司的JD
/company/jd meta > meta_jd.md

# 手动对比或使用diff工具
diff google_jd.md meta_jd.md
```

## 注意事项
- JD原文对面试准备很重要
- 建议面试前再次查看
- 注意JD的更新时间
- 多个职位时使用position_id区分

## 相关命令
- `/company/add` - 添加公司和JD
- `/company/view` - 查看公司详情
- `/company/list` - 列出所有公司和职位
