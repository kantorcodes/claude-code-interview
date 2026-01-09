---
description: 初始化系统配置，引导用户完成初始设置。配置个人信息、目标职位、薪资期望，并创建基础数据文件。
argument-hint: [no arguments]
allowed-tools: Read, Write, Edit
---

# 系统初始化向导

欢迎使用 **Claude Code Interview System**！

本向导将引导您完成初始配置，让您快速开始使用系统管理求职和面试准备。

## 配置步骤

### 步骤 1: 创建基础数据目录结构

确保以下目录存在：
- `data/resume/` - 简历数据
- `data/companies/` - 公司和职位数据
- `data/interviews/` - 面试记录
- `data/questions/` - 问题库
- `data/analytics/` - 进度追踪
- `data/schemas/` - JSON Schema 验证文件
- `exports/` - 导出文件
- `templates/` - 简历模板

### 步骤 2: 配置个人信息

询问以下信息并保存到配置文件：

#### 必填信息：
1. **姓名** - 用于生成个性化文档
2. **邮箱** - 主要联系方式
3. **电话** - 备用联系方式

#### 可选信息：
4. **所在地** - 城市, 国家/地区
5. **LinkedIn** - LinkedIn个人资料链接
6. **GitHub** - GitHub个人资料链接
7. **个人网站** - 个人作品集或博客

### 步骤 3: 配置求职偏好

#### 目标职位
1. **目标职位类型** (可多选)：
   - 软件工程师 (Software Engineer)
   - 前端工程师 (Frontend Engineer)
   - 后端工程师 (Backend Engineer)
   - 全栈工程师 (Full Stack Engineer)
   - 系统架构师 (System Architect)
   - 机器学习工程师 (ML Engineer)
   - 数据工程师 (Data Engineer)
   - DevOps工程师 (DevOps Engineer)
   - 产品经理 (Product Manager)
   - 其他 (请说明)

2. **目标级别** (可多选)：
   - Junior (L1-L2)
   - Mid-level (L3-L4)
   - Senior (L5)
   - Staff (L6)
   - Principal (L7+)

3. **目标地点** (可多选)：
   - 具体城市列表
   - 是否接受远程工作
   - 是否愿意 relocate

4. **目标公司类型** (可多选)：
   - Big Tech (Google, Meta, Amazon, Microsoft, Apple)
   - 独角兽创业公司
   - 成长型创业公司
   - 中大型公司
   - 不限

#### 薪资期望
5. **期望薪资范围**：
   - 基础年薪范围 (例如: $150k - $200k)
   - 期望的一级股票/期权
   - 期望的签约奖金
   - 期望的总薪酬

#### 时间安排
6. **求职时间安排**：
   - 开始求职日期
   - 期望入职日期
   - 每周可投入小时数
   - 是否在职求职 (On-site job search)

### 步骤 4: 导入或创建简历

#### 选项 A: 导入现有简历
如果已有简历，运行：
```bash
/resume/import <resume-file-path>
```

#### 选项 B: 创建新简历
1. 引导用户输入个人信息
2. 逐项填写：
   - 专业总结
   - 技能列表
   - 工作经历
   - 项目经验
   - 教育背景
   - 认证证书
3. 保存到 `data/resume/base.json`

### 步骤 5: 初始化分析数据

创建 `data/analytics/progress.json`:
```json
{
  "user_id": "generated-uuid",
  "period": {
    "start": null,
    "end": null
  },
  "overview": {
    "days_spent": 0,
    "total_hours": 0,
    "average_hours_per_day": 0
  },
  "practice_statistics": {
    "technical_questions_completed": 0,
    "system_design_questions_completed": 0,
    "behavioral_questions_practiced": 0,
    "mock_interviews_completed": 0
  },
  "skill_proficiency": {},
  "company_progress": {},
  "weak_areas": [],
  "weekly_goals": []
}
```

### 步骤 6: 创建首个公司/JD (可选)

如果用户已有目标公司和JD：

1. 运行 `/company/add <company-name>`
2. 输入职位描述 (JD)
3. 自动进行JD分析
4. 生成初步准备计划

或者跳过此步骤，稍后添加。

### 步骤 7: 生成初始准备计划

基于配置信息，生成个性化的准备计划：

#### 如果提供了JD：
1. 分析JD要求
2. 对比当前技能
3. 识别技能差距
4. 生成学习计划
5. 推荐练习题目

#### 如果未提供JD：
1. 基于目标职位类型生成通用准备计划
2. 推荐核心技能学习资源
3. 建议基础练习题目

### 步骤 8: 验证配置

验证所有配置文件：
- ✅ `data/resume/base.json` 存在且有效
- ✅ `data/analytics/progress.json` 已初始化
- ✅ `data/state.json` 已创建
- ✅ 用户偏好已保存

显示配置摘要：
```
📋 配置摘要

👤 用户: [姓名]
📧 邮箱: [邮箱]

🎯 目标职位: [职位列表]
📍 目标地点: [地点列表]
💰 期望薪资: [薪资范围]

📊 初始状态:
   - 简历: ✅ 已配置
   - 目标公司: [数量] 个
   - 练习记录: 0

🚀 下一步:
   1. 添加目标公司: /company/add <company-name>
   2. 导入职位描述: /company/add-jd <company> <position>
   3. 开始面试准备: /interview/prep <company>
```

## 创建的文件

向导完成后，以下文件将被创建：

1. **配置文件**:
   - `data/config/user_preferences.json` - 用户偏好设置
   - `data/state.json` - 系统状态跟踪

2. **数据文件**:
   - `data/resume/base.json` - 基础简历（如果创建）
   - `data/analytics/progress.json` - 进度追踪
   - `data/analytics/weaknesses.json` - 弱点分析

3. **问题库**:
   - `data/questions/technical.json` - 技术问题库（空）
   - `data/questions/behavioral.json` - 行为问题库（空）
   - `data/questions/system_design.json` - 系统设计问题库（空）
   - `data/questions/hr.json` - HR问题库（空）

## 数据验证

使用JSON Schema验证创建的文件：

```bash
# 验证简历数据
data/schemas/resume.schema.json

# 验证公司数据（如果添加）
data/schemas/company.schema.json

# 验证分析数据
data/schemas/analytics.schema.json
```

## 使用示例

### 完整初始化流程
```bash
# 开始初始化
/setup

# 系统将引导您：
# 1. 输入个人信息
# 2. 配置求职偏好
# 3. 导入或创建简历
# 4. (可选) 添加目标公司
# 5. 生成准备计划
```

### 快速初始化（使用默认值）
```bash
/setup --quick

# 跳过可选步骤，仅配置必需信息
# 可以稍后通过其他命令补充
```

### 重新配置
```bash
/setup --reconfigure

# 保留现有数据，仅重新配置偏好
```

## 配置文件示例

### data/config/user_preferences.json
```json
{
  "version": "1.0",
  "created_at": "2024-01-01T10:00:00Z",
  "updated_at": "2024-01-01T10:00:00Z",
  "personal_info": {
    "name": "张三",
    "email": "zhangsan@example.com",
    "phone": "+86 138-0000-0000",
    "location": "北京, 中国",
    "linkedin": "linkedin.com/in/zhangsan",
    "github": "github.com/zhangsan"
  },
  "job_preferences": {
    "target_positions": [
      "软件工程师",
      "全栈工程师"
    ],
    "target_levels": [
      "Mid-level (L3-L4)",
      "Senior (L5)"
    ],
    "target_locations": [
      "北京",
      "上海",
      "远程"
    ],
    "company_types": [
      "Big Tech",
      "成长型创业公司"
    ],
    "remote_accepted": true,
    "relocation_willing": true
  },
  "salary_expectations": {
    "base_range": "$150k - $200k",
    "stock_expectation": "$50k+/year",
    "signing_bonus": "$20k - $30k",
    "total_target": "$220k - $280k"
  },
  "time_schedule": {
    "start_date": "2024-01-01",
    "target_start_date": "2024-03-01",
    "hours_per_week": 20,
    "currently_employed": true
  }
}
```

### data/state.json
```json
{
  "version": "1.0",
  "initialized": true,
  "initialized_at": "2024-01-01T10:00:00Z",
  "last_updated": "2024-01-01T10:00:00Z",
  "active_companies": [],
  "pending_interviews": [],
  "in_progress_resumes": [],
  "recent_activities": [],
  "statistics": {
    "total_companies": 0,
    "total_interviews": 0,
    "total_practice_hours": 0
  }
}
```

## 错误处理

### 常见问题

**问题 1: 数据目录创建失败**
```
❌ 错误: 无法创建数据目录
✅ 解决: 检查文件系统权限，确保父目录可写
```

**问题 2: 简历导入失败**
```
❌ 错误: 简历文件格式不支持
✅ 解决: 请使用 Markdown, PDF 或 Word (.docx) 格式
```

**问题 3: 配置文件验证失败**
```
❌ 错误: 配置文件格式不正确
✅ 解决: 系统将尝试修复或使用默认值
```

## 下一步

配置完成后，建议按以下顺序使用系统：

1. **添加目标公司**:
   ```bash
   /company/add google
   ```

2. **导入职位描述**:
   ```bash
   /company/add-jd google software-engineer
   ```

3. **分析JD并优化简历**:
   ```bash
   /jd/analyze google
   /resume/optimize google software-engineer
   ```

4. **准备面试**:
   ```bash
   /interview/prep google
   ```

5. **模拟面试**:
   ```bash
   /interview/simulate google technical
   ```

6. **查看进度**:
   ```bash
   /analytics/dashboard
   ```

## 技术说明

### 实现方式

本命令是一个交互式向导，通过以下方式实现：

1. **顺序执行**: 按步骤顺序引导用户
2. **用户交互**: 在关键步骤询问用户输入
3. **数据验证**: 使用JSON Schema验证生成的文件
4. **错误恢复**: 遇到错误时提供恢复选项
5. **进度保存**: 每步完成后保存，支持中断后继续

### 允许的工具

- **Read**: 读取现有配置和模板文件
- **Write**: 创建新的配置和数据文件
- **Edit**: 编辑现有文件（reconfigure模式）

## 最佳实践

1. **首次使用**: 建议完整执行所有步骤
2. **快速开始**: 可以使用 `--quick` 跳过可选步骤
3. **定期更新**: 使用 `--reconfigure` 更新偏好
4. **备份数据**: 定期备份 `data/` 目录
5. **版本控制**: 建议将 `data/` 目录加入 Git（注意敏感信息）

## 帮助和支持

如需帮助，请参考：
- `/help` - 查看所有可用命令
- `docs/getting-started.md` - 详细入门指南
- `docs/troubleshooting.md` - 故障排除指南
