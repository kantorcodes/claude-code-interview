---
description: 交互式添加公司和职位信息，完整保存JD原始文本
argument-hint: <company-name>
allowed-tools: Read, Write, Edit, Skill(jd-analyzer)
---

# 添加公司信息

添加 **$ARGUMENTS** 到您的求职列表，完整保存职位描述（JD）信息。

## 收集步骤

### 1. 公司基本信息
请提供以下信息：

**必填**:
- 公司名称: $ARGUMENTS
- 行业（如：Technology, Finance, Healthcare）
- 公司官网

**可选**:
- 总部地点
- 公司规模（如：100-500, 1000-5000, 10000+）
- 公司类型（如：Public, Private, Startup）

### 2. 目标职位信息
请提供您申请的职位信息：

- 职位ID（自动生成或手动指定，如：pos_001）
- 职位名称（如：Software Engineer III）
- 职位级别（如：L4, Senior, Principal）
- 工作地点
- 团队/部门
- 职位状态（如：preparing, applied, interviewing）

### 3. 职位描述（JD）- 重要！⭐
**这是最重要的部分！我们将完整保存JD文本。**

#### JD信息收集
请提供以下JD信息：

**完整JD文本** (必填):
您可以通过以下方式提供：
1. **直接粘贴** - 复制完整JD文本粘贴到这里
2. **上传文件** - 提供包含JD的文件路径
3. **JD链接** - 提供在线JD链接，我将帮您读取

**JD来源** (可选):
- LinkedIn
- 公司官网
- 招聘网站（如：拉勾、Boss直聘）
- 内推
- 其他

**JD文本应包含**:
- ✅ 职位概述
- ✅ 职责描述
- ✅ 技能要求（必需和优先）
- ✅ 资格要求（教育和经验）
- ✅ 加分项
- ✅ 福利待遇（可选）

#### JD保存方式
系统将：
1. **保存完整JD原文** 到 `raw_text` 字段
2. **记录JD来源** 到 `description_source` 字段
3. **记录抓取时间** 到 `scraped_at` 字段
4. **使用 jd-analyzer Skill** 分析JD
5. **提取结构化信息** 到 `structured_analysis`
6. **评估匹配度** 到 `skill_match_analysis`

### 4. 自动分析
收集完信息后，我将：
1. 创建 `data/companies/$ARGUMENTS.json` 文件
2. 保存完整JD原文
3. 使用 jd-analyzer Skill 分析JD
4. 提取关键技能和要求
5. 评估与您简历的匹配度
6. 生成结构化分析报告

### 5. 输出报告
```
✅ 公司信息已保存: data/companies/$ARGUMENTS.json

📄 JD信息已保存:
- JD来源: LinkedIn
- 保存时间: 2025-01-09 14:30:00
- JD长度: 2,456 字符

📊 JD分析结果

## 关键技能
**必需** (7项):
- Python (expert)
- Distributed Systems (advanced)
- Cloud Computing (advanced)
- ...

**优先** (4项):
- Kubernetes (基础)
- Machine Learning (中级)
- ...

**加分** (3项):
- 开源贡献
- 技术博客
- ...

## 匹配度分析
✅ 完全匹配: 7项
⚠️ 部分匹配: 3项
❌ 缺失: 2项

**总体匹配度**: 75/100

**评估**:
- 技术栈匹配度高
- 需要加强Kubernetes
- 建议学习C++基础

## 下一步建议
1. /resume/variant $ARGUMENTS - 创建定制简历
2. /interview/prep $ARGUMENTS - 生成面试准备指南
3. /question/generate $ARGUMENTS - 生成面试题库
```

## JD信息存储结构

保存的公司JSON将包含完整的JD信息：

```json
{
  "company_id": "google",
  "basic_info": {...},
  "target_positions": [
    {
      "position_id": "pos_001",
      "title": "Software Engineer III",
      "level": "L4",
      "location": "Beijing, China",
      "team": "Cloud Platform",
      "status": "applied"
    }
  ],
  "job_descriptions": {
    "pos_001": {
      "title": "Software Engineer III, Cloud Platform",
      "description_source": "https://linkedin.com/jobs/...",
      "scraped_at": "2025-01-09T14:30:00Z",

      "raw_text": "Google is looking for software engineers...

Minimum qualifications:
- Bachelor's degree in Computer Science or equivalent
- 3 years of experience in software development
with knowledge of one or more of the following: Python, Java, C++
...

Preferred qualifications:
- Master's degree or PhD
- 5 years of experience in distributed systems
...",

      "structured_analysis": {
        "required_skills": [
          "Python",
          "Java",
          "C++",
          "Distributed Systems"
        ],
        "preferred_skills": [
          "Kubernetes",
          "Machine Learning",
          "Data Engineering"
        ],
        "responsibilities": [
          "Design, develop, test, deploy, maintain and improve software",
          "Manage individual project priorities, deadlines and deliverables"
        ],
        "minimum_qualifications": [
          "Bachelor's degree in Computer Science or equivalent",
          "3 years of experience in software development"
        ],
        "preferred_qualifications": [
          "Master's degree or PhD",
          "5 years of experience in distributed systems"
        ]
      },

      "skill_match_analysis": {
        "matched_skills": [
          {"skill": "Python", "proficiency": "expert"},
          {"skill": "Distributed Systems", "proficiency": "advanced"}
        ],
        "partial_match_skills": [
          {"skill": "Java", "proficiency": "intermediate", "required": "advanced"}
        ],
        "missing_skills": [
          {"skill": "C++", "action": "需要学习基础"}
        ]
      }
    }
  }
}
```

## 示例输入

### 基本信息
```
名称: Google
行业: Technology
官网: google.com
规模: 100,000+
类型: Public
总部: Mountain View, CA
```

### 职位信息
```
职位ID: pos_001 (自动生成)
职位: Software Engineer III
级别: L4
地点: Beijing, China
团队: Cloud Platform
状态: applied
```

### JD文本 - 方式1: 直接粘贴
```
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
...

请粘贴完整JD（包括所有职责、要求、福利等）
```

### JD文本 - 方式2: 文件路径
```
请提供JD文件路径:
~/Downloads/google-jd.txt

或从招聘网站导出的JD文件:
~/Downloads/LinkedIn_JD_Software_Engineer.pdf
```

### JD文本 - 方式3: 在线链接
```
请提供JD链接:
https://www.linkedin.com/jobs/view/123456789/

或公司官网职位页面:
https://careers.google.com/jobs/results/123456/
```

## JD收集建议

### ✅ 好的JD
- 完整的职位描述
- 明确的技能要求
- 详细的职责说明
- 清晰的资格要求
- 包含公司福利

### ⚠️ 需要补充
- 如果JD太简略，建议：
  1. 查看公司官网的详细描述
  2. 结合多个招聘网站的信息
  3. 咨询HR或内推人
  4. 参考类似职位的JD

### 📝 JD保存的重要性
完整的JD文本用于：
1. **简历优化** - 提取精确的关键词
2. **面试准备** - 了解具体要求
3. **技能匹配** - 准确评估匹配度
4. **后续参考** - 面试前快速回顾
5. **职位对比** - 比较不同职位的要求

## 多个职位管理

如果同一公司有多个职位：
1. 第一次添加时创建公司文件
2. 后续添加时可以追加新职位
3. 每个职位有独立的position_id
4. 每个职位保存完整的JD

示例：
```bash
/company/add google
# 添加第一个职位 pos_001

/company/add google
# 系统询问：添加新职位还是更新现有职位？
# 选择"添加新职位" -> pos_002
```

## JD更新

如果JD有更新：
1. 重新运行 `/company/add google`
2. 选择更新现有职位
3. 系统会保留历史版本
4. 记录更新时间

## 注意事项
- ⭐ **完整保存JD** - 原始文本对后续分析很重要
- ⭐ **JD来源** - 记录JD来源便于后续参考
- ⭐ **多语言支持** - 系统支持中英文JD
- ⭐ **定期更新** - JD可能有变化，及时更新
- ⭐ **隐私注意** - JD包含敏感信息，妥善保管
