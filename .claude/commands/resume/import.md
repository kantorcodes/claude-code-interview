---
description: 导入现有简历（支持PDF、Word、Markdown格式）
argument-hint: <file-path>
allowed-tools: Read, Write, Edit, Bash
---

# 导入现有简历

从 **$ARGUMENTS** 导入您的现有简历。

## 支持的格式

### 1. Markdown (.md) - 推荐 ✅
**最简单的方式**
- 直接读取内容
- 保持格式
- 易于编辑

### 2. PDF (.pdf)
**需要转换工具**
- 使用PDF读取工具提取文本
- 保留基本结构
- 可能需要手动调整

### 3. Word (.docx)
**需要转换工具**
- 使用pandoc转换为Markdown
- 或使用其他文档处理工具
- 保留基本格式

## 工作流程

### 步骤 1: 读取文件
根据文件类型：
- **Markdown**: 直接使用Read工具读取
- **PDF**: 使用PDF读取工具提取文本
- **Word**: 使用pandoc转换为Markdown后读取

### 步骤 2: 解析内容
提取以下信息：
- 个人信息（姓名、联系方式）
- 专业总结
- 技能列表
- 工作经历
- 项目经验
- 教育背景
- 认证证书

### 步骤 3: 转换为JSON
将提取的信息转换为 `data/resume/base.json` 格式

### 步骤 4: 验证和编辑
- 显示提取的信息供用户确认
- 标记可能需要手动编辑的部分
- 允许用户补充缺失信息

### 步骤 5: 保存
- 保存到 `data/resume/base.json`
- 显示导入报告

## 使用方法

### 方式 1: Markdown简历（最简单）
```bash
/resume/import /path/to/resume.md
```

### 方式 2: PDF简历
```bash
/resume/import ~/Documents/my_resume.pdf
```
系统将：
1. 读取PDF内容
2. 提取文本信息
3. 解析结构
4. 生成JSON

### 方式 3: Word简历
```bash
/resume/import ~/Documents/my_resume.docx
```
系统将：
1. 使用pandoc转换为Markdown
2. 读取转换后的内容
3. 解析结构
4. 生成JSON

## 检测的简历结构

### Markdown格式示例
```markdown
# 张三

邮箱: zhangsan@example.com
电话: +86 138-0000-0000
LinkedIn: linkedin.com/in/zhangsan
GitHub: github.com/zhangsan

## 专业总结
资深软件工程师，专注于分布式系统和机器学习...

## 技能
### 编程语言
- Python (专家)
- Java (熟练)
- JavaScript (熟练)

### 框架
- React
- Spring Boot
- Django

## 工作经历

### 高级软件工程师 | ABC科技公司 | 2020.06 - 至今
负责核心微服务架构设计和开发...

**成就**:
- 设计并实现高并发订单处理系统，处理能力提升300%
- 领导5人团队完成微服务迁移项目
- 优化数据库查询性能，响应时间降低50%

**技术栈**: Java, Spring Cloud, Redis, MySQL, Docker

### 软件工程师 | XYZ互联网 | 2018.07 - 2020.05
参与电商平台开发...

## 项目经验

### 分布式任务调度系统 | 创始人 | 2022.01 - 至今
GitHub: github.com/zhangsan/task-scheduler

一个可扩展的任务调度框架...

**成就**:
- GitHub stars 1k+
- 被3家公司用于生产环境

**技术**: Go, gRPC, Etcd, Docker

## 教育背景

### 计算机科学硕士 | 清华大学 | 2016.09 - 2018.06
GPA: 3.8/4.0
**荣誉**: 优秀毕业生、国家奖学金
**课程**: 分布式系统、机器学习、高级算法

### 计算机科学学士 | 北京大学 | 2012.09 - 2016.06
GPA: 3.7/4.0
**荣誉**: 一等奖学金
```

## PDF/Word处理

### PDF读取
对于PDF文件，尝试：
1. 读取PDF文本内容
2. 识别章节标题
3. 提取关键信息
4. 重建结构

**注意**: PDF格式解析可能不完美，建议：
- 使用清晰的PDF模板
- 检查导入结果
- 手动调整缺失部分

### Word转换
对于Word文件，使用pandoc：
```bash
pandoc input.docx -o temp.md
```
然后读取转换后的Markdown文件。

**要求**: 系统需要安装pandoc
```bash
# macOS
brew install pandoc

# Linux
sudo apt-get install pandoc

# Windows
# 从 https://pandoc.org/installing.html 下载
```

## 导入报告

### 成功示例
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

### 部分成功示例
```
⚠️ 简历部分导入成功

✅ 成功导入:
- 个人信息
- 专业总结
- 技能清单（部分）

❌ 未能识别:
- 工作经历（格式不标准）
- 项目经验（缺少章节标题）

📁 已保存到: data/resume/base.json

💡 建议:
1. 手动补充工作经历
2. 手动添加项目经验
3. 检查技能清单是否完整

📝 下一步:
- 使用 /resume/edit work_experience 添加工作经历
- 使用 /resume/edit projects 添加项目经验
```

## 智能解析规则

### 个人信息识别
识别以下模式：
- 邮箱: `/[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}/`
- 电话: `/[\d\s\-\(\)\+]+/`
- LinkedIn: `/linkedin\.com\/in\/[\w\-]+/`
- GitHub: `/github\.com\/[\w\-]+/`

### 章节识别
识别常见标题：
- "技能" / "Skills" / "Technical Skills"
- "工作经历" / "Work Experience" / "Experience"
- "项目经验" / "Projects" / "Project Experience"
- "教育背景" / "Education" / "Educational Background"
- "专业总结" / "Summary" / "Profile" / "About"

### 技能提取
从技能部分提取：
- 编程语言
- 框架和库
- 数据库
- 工具
- 概念

### 经历解析
解析工作/项目条目：
- 识别公司/项目名称
- 提取职位/角色
- 解析时间范围
- 提取成就要点
- 识别技术栈

## 错误处理

### 文件不存在
```
❌ 错误: 文件不存在
请检查文件路径是否正确。
```

### 格式不支持
```
❌ 错误: 不支持的文件格式
支持的格式: .md, .pdf, .docx
请将文件转换为支持的格式。
```

### 解析失败
```
❌ 错误: 无法解析文件内容
可能原因:
1. 文件格式不标准
2. 内容结构混乱
3. 文件损坏

💡 建议:
1. 检查文件是否能正常打开
2. 尝试转换为Markdown格式
3. 或使用 /resume/init 手动创建
```

## 最佳实践

### 推荐格式
**Markdown是最佳选择**，因为：
- 解析最准确
- 格式保留最好
- 易于手动编辑
- 版本控制友好

### PDF准备
如果使用PDF：
- 使用标准模板
- 清晰的章节标题
- 一致的格式
- 避免复杂布局

### Word准备
如果使用Word：
- 使用标题样式
- 清晰的章节划分
- 简洁的格式
- 导出前检查

## 下一步操作

导入完成后：
1. ✏️ 检查并补充信息
2. 📄 生成简历预览
3. 🎯 添加目标公司
4. 📝 创建简历变体
