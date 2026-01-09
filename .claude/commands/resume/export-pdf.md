---
description: 将简历导出为PDF格式，支持多种模板和样式。自动处理格式、字体、页边距，确保ATS兼容性。
argument-hint: <variant-name> [template]
allowed-tools: Read, Write, Bash
---

# 导出PDF简历

将简历变体 **$1** 导出为PDF格式。可选使用模板 **$2**。

## 使用方法

### 基础用法
```bash
# 导出默认模板
/resume/export-pdf google_v2

# 使用指定模板
/resume/export-pdf google_v2 modern

# 导出到指定位置
/resume/export-pdf google_v2 professional ~/Downloads/
```

## 可用模板

### 1. **classic** (推荐 - 最ATS友好)
**特点**:
- 简洁单列布局
- 标准字体（Times New Roman）
- 最适合ATS系统
- 黑白打印友好

**适用**:
- 大公司（Workday ATS）
- 保守行业（金融、政府）
- 需要打印的场合

### 2. **modern** (推荐 - 平衡美观和可读性)
**特点**:
- 轻微格式化（加粗标题）
- 使用Calibri字体
- ATS兼容性良好
- 适合大多数公司

**适用**:
- 科技公司（Greenhouse/Lever ATS）
- 中型公司
- 一般求职场景

### 3. **creative** (初创公司友好)
**特点**:
- 现代化设计
- 支持颜色和图标
- 强调个人品牌
- ATS兼容性中等

**适用**:
- 初创公司
- 设计/创意岗位
- 强调个人风格

### 4. **technical** (技术岗位专用)
**特点**:
- 突出技术技能
- GitHub/项目链接突出显示
- 包含技术栈可视化
- ATS兼容性良好

**适用**:
- 软件工程师岗位
- 技术主导的公司
- 需要展示技术深度

## PDF导出流程

### 步骤 1: 读取简历变体
```bash
# 读取JSON格式的简历变体
Read: data/resume/variants/google_v2.json
```

### 步骤 2: 转换为Markdown
将JSON转换为结构化Markdown：

```markdown
# Li Ming
**Senior Software Engineer**

📍 Beijing, China | 📧 liming.dev@example.com
🔗 linkedin.com/in/liming-dev | 💻 github.com/liming-dev

## Professional Summary
Senior Software Engineer with 5+ years of experience in distributed systems
and cloud computing. Expert in Python and Go, with deep expertise in
microservices architecture and system optimization.

## Technical Skills

### Programming Languages
Python (Expert), Go (Intermediate), Java (Advanced), TypeScript (Advanced)

### Frameworks & Tools
Django, FastAPI, Spring Boot, React, Kubernetes, Docker, AWS, PostgreSQL, Redis

### Core Competencies
- Microservices Architecture
- Distributed Systems
- Cloud Computing (AWS/GCP)
- System Design & Scalability
- CI/CD & DevOps

## Work Experience

### ByteDance | Senior Software Engineer
**March 2022 - Present | Beijing**

Designed and implemented high-concurrency order processing system:
- Scaled peak QPS from 5k to 50k (900% improvement)
- Achieved 99.99% system availability
- Reduced service latency by 60% through optimization
- Led team of 5 engineers in microservices migration

### Meituan | Software Engineer
**July 2019 - February 2022 | Beijing**

Developed food delivery dispatch system:
- Optimized delivery routing algorithms, reducing average time by 12%
- Implemented distributed caching, reducing database load by 70%
- Refactored monolithic application into 10+ microservices

## Projects

### Distributed Task Scheduler
**Creator | June 2021 - Present**
- GitHub: github.com/liming-dev/task-scheduler
- 1.5k+ GitHub stars, used by 3 companies in production
- Supports 100k+ tasks/second per cluster
- Implemented graceful failover and data consistency

### Real-time Analytics Dashboard
**Core Contributor | September 2020 - December 2021**
- GitHub: github.com/liming-dev/analytics-dashboard
- 800+ GitHub stars
- Efficient aggregation algorithms, 50% faster than commercial tools
- Real-time data visualization supporting millions of data points

## Education

### Tsinghua University | Master of Computer Science
**September 2017 - June 2019 | Beijing**
- GPA: 3.8/4.0
- Honors: Outstanding Graduate, National Scholarship

### Zhejiang University | Bachelor of Software Engineering
**September 2013 - June 2017 | Hangzhou**
- GPA: 3.7/4.0
- Honors: Provincial Outstanding Graduate

## Certifications

- **AWS Certified Solutions Architect** (Amazon Web Services, 2021)
- **Google Cloud Professional Cloud Architect** (Google Cloud, 2022)

## Languages

- **Chinese**: Native
- **English**: Advanced
```

### 步骤 3: 应用模板样式
根据选择的模板应用样式：

#### Classic模板样式
```css
字体: Times New Roman, 11pt
标题: 14pt, 全大写, 加粗
页边距: 1 inch
行间距: 1.0
颜色: 黑白
```

#### Modern模板样式
```css
字体: Calibri, 11pt
标题: 14pt, 加粗
页边距: 0.75 inch
行间距: 1.15
颜色: 黑色（标题可深蓝）
```

### 步骤 4: 生成PDF
使用以下工具之一：

#### 选项1: Pandoc (推荐)
```bash
pandoc data/resume/variants/google_v2.md \
  -o exports/Li_Ming_Google_Resume.pdf \
  --pdf-engine=xelatex \
  -V geometry:margin=1in \
  -V fontsize=11pt \
  --template templates/classic.tex \
  --toc=false
```

#### 选项2: wkhtmltopdf
```bash
wkhtmltopdf \
  --margin-top 0.5in \
  --margin-bottom 0.5in \
  --margin-left 0.75in \
  --margin-right 0.75in \
  data/resume/variants/google_v2.html \
  exports/Li_Ming_Google_Resume.pdf
```

#### 选项3: Markdown to PDF (在线)
- 使用在线工具: markdown2pdf.com
- 或VS Code插件: Markdown PDF

### 步骤 5: 添加PDF元数据
```bash
# 使用exiftool添加元数据
exiftool \
  -Title="Li Ming - Software Engineer Resume" \
  -Author="Li Ming" \
  -Keywords="Software Engineer, Python, Distributed Systems, Kubernetes" \
  -Creator="Claude Code Interview System" \
  exports/Li_Ming_Google_Resume.pdf
```

### 步骤 6: 验证PDF
```bash
# 检查文件大小
ls -lh exports/Li_Ming_Google_Resume.pdf

# 验证可以提取文本（ATS兼容性）
pdftotext exports/Li_Ming_Google_Resume.pdf - | head -20

# 检查字体和嵌入信息
pdfinfo exports/Li_Ming_Google_Resume.pdf
```

## 输出规范

### 文件命名
```
格式: {FirstName}_{LastName}_{Position}_{Company}.pdf

示例:
Li_Ming_Senior_Engineer_Google.pdf
Li_Ming_Software_Engineer_Amazon.pdf
Li_Ming_Tech_Lead_Microsoft.pdf
```

### 文件要求
- **文件大小**: < 1MB (目标: 200-500KB)
- **页数**: 1-2页 (首选: 1页)
- **字体**: 嵌入标准字体
- **文本可选**: 所有文本必须可选择（非图片）

## 质量检查清单

导出前检查：
- [ ] 内容完整（无截断）
- [ ] 日期格式一致
- [ ] 联系信息准确
- [ ] 链接可点击
- [ ] 无拼写错误
- [ ] 符合1-2页限制

导出后检查：
- [ ] PDF可正常打开
- [ ] 文字清晰可读
- [ ] 格式保持一致
- [ ] 页码正确（如有）
- [ ] 文件大小合理
- [ ] 文本可选择（ATS兼容）

## 输出位置

**默认位置**: `exports/{FirstName}_{LastName}_{Company}_Resume.pdf`

**自定义位置**: 如果提供路径参数，导出到指定位置

## 示例输出

```bash
$ /resume/export-pdf google_v2 modern

✅ 正在读取简历变体: google_v2
✅ 转换为Markdown格式
✅ 应用modern模板样式
✅ 生成PDF文件...
✅ 添加PDF元数据
✅ 验证PDF质量

📄 导出成功！

文件位置: exports/Li_Ming_Google_Resume.pdf
文件大小: 342 KB
页数: 1页
模板: modern

下一步：
- 打开PDF检查格式: open exports/Li_Ming_Google_Resume.pdf
- 提交前进行最终预览
- 为不同公司创建定制版本
```

## 高级功能

### 批量导出
```bash
# 导出所有变体
/resume/export-pdf --all

# 导出特定公司的所有变体
/resume/export-pdf google --all-variants
```

### 自定义样式
```bash
# 使用自定义LaTeX模板
/resume/export-pdf google_v2 --template ~/templates/myresume.tex

# 自定义页边距
/resume/export-pdf google_v2 --margin 0.8

# 自定义字体大小
/resume/export-pdf google_v2 --fontsize 10pt
```

### 导出为多种格式
```bash
# 同时导出PDF和Word
/resume/export-pdf google_v2 --formats pdf,docx

# 导出为HTML预览
/resume/export-pdf google_v2 --format html
```

## 故障排除

### 常见问题

**问题1: PDF中文乱码**
```
原因: 缺少中文字体
解决:
- 使用xelatex引擎（支持中文）
- 或使用支持UTF-8的模板
```

**问题2: 格式错乱**
```
原因: Markdown格式不正确
解决:
- 检查Markdown语法
- 使用pandoc的--wrap=none选项
- 检查表格和列表格式
```

**问题3: 文件过大**
```
原因: 图片或高分辨率元素
解决:
- 压缩图片
- 使用PDF优化工具
- 移除不必要的元素
```

**问题4: PDF生成失败**
```
原因: 缺少依赖工具
解决:
- 安装pandoc: brew install pandoc
- 安装LaTeX: brew install mactex
- 或使用在线工具
```

## 最佳实践

1. **提前测试**: 在申请前1-2天导出并检查
2. **多个版本**: 为不同公司准备不同版本
3. **备份保存**: 保留所有导出的PDF版本
4. **版本控制**: 在文件名中包含版本号
5. **格式验证**: 使用ATS扫描工具验证
6. **打印测试**: 打印出来检查实际效果

## ATS优化提示

导出时自动应用以下ATS优化：
- ✅ 使用标准字体
- ✅ 避免图像和图表
- ✅ 简洁的格式
- ✅ 清晰的章节标题
- ✅ 嵌入字体信息
- ✅ 可选择的文本
- ✅ 标准的文件命名

## 相关命令

- `/resume/compare <v1> <v2>` - 对比简历变体
- `/resume/optimize <company>` - 优化简历
- `/resume/list` - 列出所有变体
