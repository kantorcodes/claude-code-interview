---
description: 从URL或文件批量导入职位描述（JD），支持多个平台（LinkedIn、Indeed、公司官网等）。自动解析、提取关键信息、批量处理。
argument-hint: <source> [options]
allowed-tools: Read, Write, Skill(jd-analyzer), mcp__web_reader__webReader
---

# 智能JD导入

智能导入职位描述（JD），支持多种来源和格式。

## 使用方法

### 从URL导入单个JD
```bash
# 从LinkedIn导入
/jd/import https://www.linkedin.com/jobs/view/123456789/

# 从Indeed导入
/jd/import https://www.indeed.com/viewjob?jk=123456789

# 从公司官网导入
/jd/import https://careers.google.com/jobs/results/123456/
```

### 从文件导入JD
```bash
# 从文本文件导入
/jd-import ~/Downloads/google-jd.txt

# 从Markdown文件导入
/jd-import ~/Downloads/amazon-jd.md

# 从Word文档导入
/jd-import ~/Downloads/meta-jd.docx
```

### 批量导入
```bash
# 批量导入多个URL
/jd-import --batch ~/jd-urls.txt

# 批量导入目录中的所有JD文件
/jd-import --batch-dir ~/Downloads/jds/

# 从CSV导入
/jd-import --csv ~/job-applications.csv
```

### 交互式导入
```bash
# 交互式粘贴JD
/jd-import --interactive

# 然后粘贴JD文本
```

## 支持的平台

### 1. LinkedIn
**URL格式**:
```
https://www.linkedin.com/jobs/view/[job-id]/
https://www.linkedin.com/jobs/search/?keywords=...
```

**提取内容**:
- ✅ 职位名称和级别
- ✅ 公司和团队信息
- ✅ 职位描述全文
- ✅ 技能要求
- ✅ 职位详情（地点、类型、级别）
- ⚠️ 薪资信息（如果提供）

**处理方式**:
1. 读取LinkedIn页面
2. 提取职位详情区域
3. 清理HTML标签
4. 结构化存储

### 2. Indeed
**URL格式**:
```
https://www.indeed.com/viewjob?jk=[job-id]
https://www.indeed.com/company/[company-name]/jobs
```

**提取内容**:
- ✅ 完整职位描述
- ✅ 公司信息
- ✅ 职位类型和地点
- ✅ 薪资范围（常见）

### 3. Glassdoor
**URL格式**:
```
https://www.glassdoor.com/job-listing/[job-title]-[company]-JI.htm
```

**提取内容**:
- ✅ 职位描述
- ✅ 薪资估算
- ✅ 公司评价和评分

### 4. 公司官网
**URL格式**:
```
https://careers.company.com/jobs/123456
https://jobs.company.com/position/123456
https://www.company.com/careers/openings/...
```

**处理方式**:
- 自动检测常见ATS系统（Workday, Greenhouse, Lever）
- 针对性提取内容
- 保存原始链接

### 5. 招聘网站
**支持**:
- Boss直聘 (bosszhipin.com)
- 拉勾网 (lagou.com)
- 猎聘 (liepin.com)
- 其他本地招聘平台

## 导入流程

### 步骤 1: 检测来源类型
```bash
# 分析输入类型
URL? → 自动检测平台
File? → 读取文件内容
Text? → 直接处理
```

### 步骤 2: 获取JD内容
```bash
# URL方式
使用 webReader MCP 工具:
- 读取网页内容
- 转换为Markdown
- 提取职位信息

# 文件方式
- 读取文件内容
- 检测格式（.txt, .md, .html, .docx）
- 解析文本
```

### 步骤 3: 提取关键信息
```json
{
  "extraction": {
    "company_name": "自动检测或手动确认",
    "position_title": "从JD提取",
    "position_level": "从JD推断 (Junior/Mid/Senior/Staff)",
    "location": "提取工作地点",
    "description": "清理后的完整JD文本",
    "salary": "提取薪资信息（如果存在）",
    "skills": "技能列表"
  }
}
```

### 步骤 4: 智能公司识别
```json
{
  "company_detection": {
    "from_url": {
      "linkedin.com/company/google": "Google",
      "careers.google.com": "Google",
      "jobs.amazon.com": "Amazon"
    },
    "from_jd": {
      "keywords": ["at Google", "Google Cloud"],
      "confidence": "high"
    },
    "manual_confirm": "需要用户确认"
  }
}
```

### 步骤 5: 调用jd-analyzer
```bash
# 使用 jd-analyzer Skill
Skill: jd-analyzer

自动分析：
- 提取必需技能
- 提取优先技能
- 分析公司文化
- 提取薪资信息
- 评估匹配度
```

### 步骤 6: 保存到数据库
```bash
# 创建或更新公司文件
Write: data/companies/{company_id}.json

保存结构：
{
  "company_id": "detected-or-provided",
  "basic_info": {...},
  "target_positions": [...],
  "job_descriptions": {
    "position_id": {
      "title": "...",
      "description_source": "original_url",
      "scraped_at": "timestamp",
      "raw_text": "...",
      "structured_analysis": {...},
      "skill_match_analysis": {...}
    }
  }
}
```

### 步骤 7: 生成导入报告
```markdown
✅ JD导入成功！

公司: Google
职位: Software Engineer III (L4)
来源: LinkedIn
JD长度: 2,456 字符

📊 分析结果:
- 必需技能: 7项
- 优先技能: 4项
- 匹配度: 75/100

💡 下一步:
- /company/view google - 查看完整信息
- /resume/optimize google - 优化简历
- /interview/prep google - 准备面试
```

## 批量导入

### 从URL列表批量导入
```bash
# 创建文本文件 jd-urls.txt
cat > jd-urls.txt <<EOF
https://www.linkedin.com/jobs/view/123456789/
https://www.linkedin.com/jobs/view/987654321/
https://careers.google.com/jobs/results/456789/
https://jobs.amazon.com/positions/123456
EOF

# 批量导入
/jd-import --batch ~/jd-urls.txt

# 系统将：
# 1. 读取每个URL
# 2. 自动检测公司
# 3. 提取JD信息
# 4. 保存到对应的company文件
# 5. 生成批量导入报告
```

### 从目录批量导入
```bash
# 导入目录中的所有JD文件
/jd-import --batch-dir ~/Downloads/jds/

# 支持的文件格式：
# - *.txt
# - *.md
# - *.html
# - *.docx (需要pandoc转换)

# 输出：
处理 10 个文件...
✅ google-jd.txt → data/companies/google.json
✅ amazon-jd.md → data/companies/amazon.json
✅ meta-jd.txt → data/companies/meta.json
⚠️ apple-jd.txt (公司识别失败，需要手动指定)
✅ netflix-jd.md → data/companies/netflix.json

成功: 4, 失败: 1, 总计: 5
```

### 从CSV导入
```bash
# CSV格式示例
cat > job-applications.csv <<EOF
company,position,url,status
Google,Software Engineer,https://linkedin.com/jobs/123,applied
Amazon,SDE2,https://amazon.jobs/123,applying
Meta,Production Engineer,https://careers.meta.com/123,researching
EOF

# 导入
/jd-import --csv ~/job-applications.csv

# 将导入所有JD并更新状态
```

## 交互式导入

### 粘贴JD文本
```bash
$ /jd-import --interactive

请粘贴职位描述（JD）文本，按Ctrl+D结束：

# 职位描述
## Software Engineer III, Cloud Platform

Google aims to build an AI that has the best understanding of the world's
information and is helpful to everyone. We're looking for software engineers
to join the Cloud Platform team...

[粘贴完成后按Ctrl+D]

正在分析JD...

请确认以下信息：
- 公司名称: Google
- 职位: Software Engineer III (L4)
- 地点: Beijing, China

确认无误？(y/n): y

✅ JD已保存到: data/companies/google.json
```

## 高级选项

### 自动检测选项
```bash
# 禁用自动公司检测
/jd-import https://... --no-auto-detect

# 手动指定公司
/jd-import https://... --company google

# 指定职位ID
/jd-import https://... --position-id sse-l4
```

### 分析选项
```bash
# 只导入，不分析
/jd-import https://... --no-analyze

# 深度分析（包括文化、薪资）
/jd-import https://... --deep-analyze

# 导入后立即优化简历
/jd-import https://... --optimize-resume
```

### 输出选项
```bash
# 详细输出
/jd-import https://... --verbose

# 静默模式
/jd-import https://... --quiet

# 输出到指定目录
/jd-import https://... --output ~/my-jds/
```

## 智能功能

### 1. 自动去重
```bash
# 检测重复JD
- 相同URL → 跳过
- 相同公司+职位 → 提示更新
- 相似度>90% → 警告可能重复
```

### 2. 自动归档
```bash
# 归档旧版本
当更新已有JD时：
1. 备份旧版本到 company.json.bak
2. 更新为新版本
3. 记录更新历史
```

### 3. 智能分类
```bash
# 自动分类职位
- 前端/后端/全栈
- 技术/产品/设计
- 初级/中级/高级/专家
```

### 4. 提醒功能
```bash
# 智能提醒
- 发现高匹配度职位 → ⭐ 标记
- 发现紧急职位 → ⏰ 提醒
- 发现申请截止日期 → 📅 通知
```

## 输出示例

### 成功导入
```markdown
✅ JD导入成功！

📋 基本信息
公司: Google (Alphabet Inc.)
职位: Software Engineer III, Cloud Platform
级别: L4 (Mid-level)
地点: Beijing, China / Remote

📄 JD信息
来源: LinkedIn
URL: https://linkedin.com/jobs/view/123456789/
保存时间: 2024-01-15 14:30:00
JD长度: 2,456 字符

💰 薪资信息
基础: $150k - $200k
股票: $50k - $100k/year
总计: ~$230k - $340k

🎯 技能分析
必需技能 (7):
  ✅ Python (expert) - 完全匹配
  ✅ Distributed Systems (advanced) - 完全匹配
  ⚠️ Kubernetes (intermediate) - 需要加强
  ❌ Go (missing) - 需要学习

优先技能 (4):
  ✅ Cloud Computing (advanced)
  ⚠️ Machine Learning (basic)

📊 匹配度评估
总体匹配度: 75/100
- 技术匹配: 72/100
- 经验匹配: 80/100
- 文化匹配: 85/100

💡 下一步建议
1. /resume/optimize google sse-l4 - 创建定制简历
2. /interview/prep google - 准备面试
3. /weakness/plan - 查看改进计划
```

### 批量导入报告
```markdown
📦 批量导入报告

总计: 10 个JD
成功: 8
失败: 2
跳过: 0 (重复)

✅ 成功导入:
1. Google - Software Engineer III
2. Amazon - SDE II
3. Meta - Production Engineer
4. Microsoft - Senior Software Engineer
5. Netflix - Senior Backend Engineer
6. Stripe - Software Engineer
7. Airbnb - Full Stack Engineer
8. Spotify - Backend Developer

❌ 失败:
1. Unknown Company - Senior Engineer (无法识别公司)
   建议: 手动指定公司名称重新导入

2. Apple - (页面访问受限)
   建议: 尝试从其他来源获取JD

📊 统计:
- 高匹配度 (>80): 3 ⭐⭐⭐
- 中等匹配度 (60-80): 4 ⭐⭐
- 低匹配度 (<60): 1 ⭐

💡 建议:
优先申请:
1. Google (匹配度: 85)
2. Amazon (匹配度: 82)
3. Meta (匹配度: 78)

需要加强技能:
- Kubernetes (3个职位需要)
- Go (2个职位需要)
```

## 故障排除

### 常见问题

**问题1: URL无法访问**
```
原因: 网站限制访问或URL失效
解决:
- 检查URL是否正确
- 尝试登录后访问
- 复制JD文本使用交互式导入
```

**问题2: 公司识别错误**
```
原因: URL或JD中公司名称不明确
解决:
- 使用 --company 手动指定公司
- 使用 --no-auto-detect 跳过自动识别
```

**问题3: JD解析不完整**
```
原因: 动态加载或特殊格式
解决:
- 使用交互式粘贴完整JD
- 从其他平台获取相同职位
- 手动复制粘贴完整内容
```

**问题4: 批量导入失败**
```
原因: 网络问题或格式错误
解决:
- 检查网络连接
- 验证文件格式
- 逐个导入查看详细错误
```

## 数据存储

**公司文件位置**:
```
data/companies/
├── google.json
├── amazon.json
├── meta.json
└── ...
```

**导入历史**:
```json
{
  "import_history": [
    {
      "timestamp": "2024-01-15T14:30:00Z",
      "source": "https://linkedin.com/jobs/123",
      "company": "google",
      "position": "sse-l4",
      "status": "success"
    }
  ]
}
```

## 相关命令

- `/company/view <company>` - 查看公司详情
- `/company/jd <company>` - 查看JD原文
- `/jd/analyze <company>` - 重新分析JD
- `/resume/optimize <company>` - 优化简历
- `/jd-import --help` - 查看完整帮助
