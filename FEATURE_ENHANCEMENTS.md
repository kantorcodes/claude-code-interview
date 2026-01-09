# 功能增强说明

本文档说明面试求职管理系统的最新功能增强。

## 增强功能 1: 简历导入 ⭐

### 功能描述
支持导入现有的PDF、Word或Markdown格式简历，自动解析并转换为系统JSON格式。

### 使用方法
```bash
/resume/import /path/to/your/resume.md
```

### 支持的格式

#### 1. Markdown (.md) - 强烈推荐 ✅
**优点**:
- 解析最准确
- 格式保留最好
- 易于手动编辑
- 版本控制友好

**示例**:
```bash
/resume/import ~/Documents/my_resume.md
```

#### 2. PDF (.pdf)
**要求**:
- PDF格式清晰
- 使用标准简历模板
- 避免复杂布局

**处理流程**:
1. 读取PDF文本内容
2. 识别章节标题
3. 提取关键信息
4. 重建结构化数据

**示例**:
```bash
/resume/import ~/Downloads/my_resume.pdf
```

#### 3. Word (.docx)
**要求**:
- 系统需安装pandoc
- 使用标题样式
- 清晰的章节划分

**安装pandoc**:
```bash
# macOS
brew install pandoc

# Linux
sudo apt-get install pandoc

# Windows
# 从 https://pandoc.org/installing.html 下载
```

**处理流程**:
1. 使用pandoc转换为Markdown
2. 读取转换后的内容
3. 解析结构化数据
4. 生成JSON

**示例**:
```bash
/resume/import ~/Documents/my_resume.docx
```

### 智能解析特性

#### 自动识别信息
- ✅ 个人信息（姓名、邮箱、电话、LinkedIn、GitHub）
- ✅ 专业总结
- ✅ 技能清单（编程语言、框架、数据库、工具）
- ✅ 工作经历（公司、职位、时间、成就）
- ✅ 项目经验（项目名、角色、描述、技术）
- ✅ 教育背景（学校、学位、时间、GPA、荣誉）
- ✅ 认证证书

#### 正则表达式匹配
```
邮箱: /[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}/
电话: /[\d\s\-\(\)\+]+/
LinkedIn: /linkedin\.com\/in\/[\w\-]+/
GitHub: /github\.com\/[\w\-]+/
```

#### 章节识别
自动识别常见标题：
- "技能" / "Skills" / "Technical Skills"
- "工作经历" / "Work Experience" / "Experience"
- "项目经验" / "Projects" / "Project Experience"
- "教育背景" / "Education" / "Educational Background"
- "专业总结" / "Summary" / "Profile" / "About"

### 导入报告示例

#### 成功导入
```
✅ 简历导入成功！

📊 导入统计
- 个人信息: ✅ 完整
- 专业总结: ✅ 已导入
- 技能清单: ✅ 12项技能
- 工作经历: ✅ 2份工作
- 项目经验: ✅ 3个项目
- 教育背景: ✅ 2个学位
- 认证证书: ⚠️ 未找到

📁 已保存到: data/resume/base.json

⚠️ 需要手动检查:
1. 电话号码格式可能需要调整
2. 项目"任务调度系统"的链接请手动添加
3. 建议补充认证证书信息

📝 下一步:
- 使用 /resume/edit 编辑任何部分
- 使用 /resume/generate base 生成简历预览
```

#### 部分成功
```
⚠️ 简历部分导入成功

✅ 成功导入:
- 个人信息
- 专业总结
- 技能清单（部分）

❌ 未能识别:
- 工作经历（格式不标准）
- 项目经验（缺少章节标题）

💡 建议:
1. 手动补充工作经历
2. 手动添加项目经验
3. 检查技能清单是否完整
```

### 最佳实践

#### 准备Markdown简历
使用清晰的Markdown结构：
```markdown
# 张三

邮箱: zhangsan@example.com
电话: +86 138-0000-0000

## 专业总结
资深软件工程师...

## 技能
### 编程语言
- Python (专家)
- Java (熟练)

## 工作经历
### 高级软件工程师 | ABC公司 | 2020.06 - 至今
负责...
```

#### 准备PDF简历
- 使用标准模板
- 清晰的章节标题
- 一致的格式
- 避免复杂布局

#### 准备Word简历
- 使用标题样式（Heading 1, 2, 3）
- 清晰的章节划分
- 简洁的格式
- 导出前检查

## 增强功能 2: JD完整保存 ⭐

### 功能描述
添加公司时，系统现在会**完整保存职位描述（JD）的原始文本**，不仅仅是提取的结构化信息。

### JD信息保存

#### 保存的数据字段
```json
{
  "job_descriptions": {
    "pos_001": {
      "title": "Software Engineer III, Cloud Platform",
      "description_source": "https://linkedin.com/jobs/...",
      "scraped_at": "2025-01-09T14:30:00Z",
      "raw_text": "完整的JD原文...",
      "structured_analysis": {
        "required_skills": [...],
        "preferred_skills": [...]
      }
    }
  }
}
```

#### 字段说明
- **raw_text**: 完整的JD原文（最重要！）
- **description_source**: JD来源（LinkedIn、公司官网等）
- **scraped_at**: 保存时间
- **structured_analysis**: 结构化分析结果
- **skill_match_analysis**: 技能匹配分析

### JD提供方式

#### 方式 1: 直接粘贴（推荐）
```bash
/company/add google
```
然后直接粘贴完整JD文本。

#### 方式 2: 文件路径
```bash
/company/add google
```
提供JD文件路径：
- `~/Downloads/google-jd.txt`
- `~/Documents/LinkedIn_JD.pdf`

#### 方式 3: 在线链接
```bash
/company/add google
```
提供在线JD链接：
- `https://www.linkedin.com/jobs/view/123456789/`
- `https://careers.google.com/jobs/results/123456/`

### 查看保存的JD

#### 使用新命令查看
```bash
/company/jd google
```

显示：
- JD基本信息（来源、时间、长度）
- 完整JD原文（格式化显示）
- 结构化分析摘要
- 快速操作提示

#### 导出JD
```bash
# 导出为Markdown
/company/jd google > export_jd.md

# 导出为纯文本
/company/jd google > export_jd.txt
```

### JD完整保存的重要性

#### 1. 精确的简历优化
完整的JD文本可以：
- 提取精确的关键词
- 识别所有技能要求
- 理解职位的具体期望
- 匹配公司文化关键词

#### 2. 准确的面试准备
完整JD帮助：
- 了解所有职责要求
- 准备相关技术问题
- 理解团队和项目
- 准备行为面试问题

#### 3. 技能匹配评估
基于完整JD：
- 全面评估技能匹配
- 识别技能差距
- 优先学习重点
- 制定学习计划

#### 4. 面试前快速回顾
- 不用再翻找原JD
- 快速复习关键要求
- 准备针对性问题
- 检查准备情况

#### 5. 职位对比
对比不同公司：
- 比较技能要求
- 对比职责范围
- 对比福利待遇
- 做出最佳选择

### 多职位管理

#### 添加多个职位
```bash
# 第一个职位
/company/add google
# 系统创建 pos_001

# 第二个职位
/company/add google
# 系统询问：添加新职位？选择是
# 系统创建 pos_002
```

#### 查看特定职位的JD
```bash
# 公司只有一个职位
/company/jd google

# 公司有多个职位
/company/jd google pos_002
```

### JD更新管理

#### JD版本控制
如果JD有更新：
1. 重新运行 `/company/add google`
2. 选择更新现有职位
3. 系统保留历史版本
4. 记录更新时间

#### JD变更通知
系统会标记：
- 最后更新时间
- 变更历史
- 需要重新准备的内容

## 数据模型更新

### 公司数据模型更新
更新了 `data/companies/template.json`：

#### 新增字段
```json
{
  "job_descriptions": {
    "position_id": {
      "raw_text": "",           // 新增：完整JD原文
      "description_source": "",  // 新增：JD来源
      "scraped_at": null,        // 新增：抓取时间
      ...
    }
  },
  "created_at": null,            // 新增：创建时间
  "updated_at": null             // 新增：更新时间
}
```

#### 结构改进
- **target_positions**: 现在是数组，支持多个职位
- **job_descriptions**: 按position_id组织
- **完整JD**: 保存到raw_text字段
- **结构化分析**: 保存到structured_analysis字段

## 新增命令

### 1. /resume/import
导入现有简历。

**语法**:
```bash
/resume/import <file-path>
```

**参数**:
- `file-path`: 简历文件路径（支持.md, .pdf, .docx）

**示例**:
```bash
/resume/import ~/Documents/resume.md
/resume/import ~/Downloads/resume.pdf
/resume/import ~/Documents/resume.docx
```

### 2. /company/jd
查看保存的JD原文。

**语法**:
```bash
/company/jd <company-name> [position-id]
```

**参数**:
- `company-name`: 公司名称（必需）
- `position-id`: 职位ID（可选，多职位时需要）

**示例**:
```bash
/company/jd google
/company/jd google pos_002
```

## 使用示例

### 完整流程（导入简历）

```bash
# 1. 导入现有简历
/resume/import ~/Documents/my_resume.md

# 系统输出：
# ✅ 简历导入成功！
# 📁 已保存到: data/resume/base.json
# ⚠️ 需要手动检查:
# 1. 项目链接请手动添加

# 2. 添加公司（包含完整JD）
/company/add meta

# 系统提示：
# 请提供JD信息：
# 1. 直接粘贴
# 2. 文件路径
# 3. 在线链接

# 选择：直接粘贴完整JD

# 系统输出：
# ✅ 公司信息已保存
# 📄 JD已保存（2,456字符）
# 📊 匹配度: 75/100

# 3. 查看保存的JD
/company/jd meta

# 系统显示完整JD原文和分析

# 4. 创建定制简历
/resume/variant meta

# 5. 生成简历
/resume/generate meta

# 6. 准备面试
/interview/prep meta
```

## 技术实现

### 简历解析流程

#### Markdown解析
1. Read工具读取文件
2. 按行解析内容
3. 识别章节标题（#, ##）
4. 提取各部分内容
5. 应用正则表达式
6. 构建JSON结构

#### PDF解析
1. PDF读取工具提取文本
2. 识别标题格式
3. 重建段落结构
4. 提取关键信息
5. 构建JSON结构

#### Word解析
1. 使用pandoc转换为Markdown
2. 读取转换后的内容
3. 按Markdown方式解析
4. 构建JSON结构

### JD保存流程

#### JD收集
1. 用户粘贴/提供文件/提供链接
2. 系统接收完整文本
3. 保存到raw_text字段

#### JD分析
1. jd-analyzer Skill分析
2. 提取结构化信息
3. 评估技能匹配
4. 保存分析结果

#### JD检索
1. /company/jd命令
2. 读取raw_text字段
3. 格式化显示
4. 包含分析摘要

## 注意事项

### 简历导入
- ⚠️ PDF解析可能不完美，需要手动检查
- ⚠️ Word需要pandoc，请提前安装
- ✅ Markdown是最可靠的方式
- ✅ 导入后务必检查并补充信息

### JD保存
- ⭐ 完整JD非常重要，请提供完整内容
- ⭐ 记录JD来源，便于后续参考
- ⭐ 定期检查JD是否有更新
- ⭐ 多职位时使用position_id区分
- ⚠️ JD包含敏感信息，注意隐私

## 后续改进

### 计划中的增强
1. **简历格式检测** - 自动检测简历格式并建议最佳转换方式
2. **JD智能填充** - 从常见招聘网站自动抓取JD
3. **简历模板库** - 提供更多简历模板选择
4. **JD相似度分析** - 对比不同公司的JD相似度
5. **批量导入** - 支持批量导入多个简历
6. **版本历史** - 保留简历和JD的历史版本

### 反馈
如果遇到问题或有建议，请：
1. 检查文件格式是否正确
2. 确认文件路径是否有效
3. 查看系统提示的错误信息
4. 手动补充解析失败的部分

## 总结

这两个功能增强显著提升了系统的实用性：

1. **简历导入** - 用户可以快速导入现有简历，无需从零开始
2. **JD完整保存** - 完整保存JD信息，支持更准确的准备和分析

结合使用，用户可以：
- 快速导入现有简历
- 添加公司时完整保存JD
- 基于完整JD创建定制简历
- 准备更有针对性的面试
- 获得更准确的匹配度评估
