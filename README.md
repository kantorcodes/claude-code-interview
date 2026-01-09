<div align="center">

  <!-- 主标题和徽章 -->
  # 🎯 Claude Code Interview System

  ### 全功能的求职和面试准备管理系统 v2.0

  [![Claude Code](https://img.shields.io/badge/Claude-Code-Compatible-blue?logo=anthropic)](https://code.claude.com)
  [![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
  [![Version](https://img.shields.io/badge/Version-2.0.0-orange.svg)](https://github.com/yourusername/claude-code-interview)
  [![Status](https://img.shields.io/badge/Status-Production--Ready-success.svg)]()

  <!-- 功能徽章 -->
  [![Resume](https://img.shields.io/badge/Resume-Management-red.svg)]()
  [![Interview](https://img.shields.io/badge/Interview-Preparation-purple.svg)]()
  [![JD Analysis](https://img.shields.io/badge/JD-Analysis-yellow.svg)]()
  [![Analytics](https://img.shields.io/badge-Analytics-Dashboard-blue.svg)]()
  [![No Database](https://img.shields.io/badge/Database-Free-brightgreen.svg)]()

  <!-- 平台徽章 -->
  [![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey.svg)]()
  [![Storage](https://img.shields.io/badge/Storage-JSON%20%2B%20Markdown-9cf.svg)]()
  [![Skills](https://img.shields.io/badge/AI%20Skills-8-purple.svg)]()
  [![Commands](https://img.shields.io/badge/Commands-20%2B-brightgreen.svg)]()

  [快速开始](#快速开始) • [核心功能](#核心功能) • [使用指南](#使用指南) • [最佳实践](#最佳实践)

</div>

---

## 📖 项目简介

**Claude Code Interview System** 是一个生产就绪的求职和面试准备管理系统，基于 Claude Code 构建。从 JD 分析到薪资谈判，提供端到端的智能求职助手。

### ✨ v2.0 重大更新

- 🎯 **8个AI技能** - JD分析、简历优化、面试指导、问题生成、智能协调、薪资谈判、职业规划、LinkedIn导入
- 📊 **可视化分析** - 交互式仪表板、市场情报、竞争定位、成功预测
- 🤝 **工作流自动化** - 智能协调器自动规划和执行复杂任务
- 📅 **日历集成** - 自动同步面试安排，多级提醒系统
- 💰 **Offer谈判** - 专业级薪资分析和还盘策略
- 🚀 **职业规划** - 5年发展路线图，技能差距分析，角色转换指导

### 核心亮点

- 🚀 **生产就绪** - 完整实现，开箱即用
- 🤖 **AI驱动** - 8个专业AI技能，20+命令
- 📊 **数据驱动** - 可视化仪表板，市场趋势分析
- 🎯 **端到端** - 从JD到Offer的全流程覆盖
- 💾 **隐私优先** - 所有数据本地存储
- 🔄 **可扩展** - 模块化设计，易于定制

---

## 🎬 快速开始

### 前置要求

确保您已安装 [Claude Code](https://code.claude.com)：

```bash
# 安装 Claude Code
npm install -g @anthropic-ai/claude-code

# 或使用 Homebrew (macOS)
brew install claude-code
```

### 5分钟上手

#### 1️⃣ 初始化系统

```bash
/setup
```

交互式向导会引导你：
- ✅ 创建数据结构
- ✅ 配置系统设置
- ✅ 上传基础简历
- ✅ 设置目标和偏好
- ✅ 生成初始计划

#### 2️⃣ 导入第一个JD

```bash
# 从LinkedIn导入
/jd/import https://www.linkedin.com/jobs/view/123456789/

# 或粘贴JD文本
/jd/import --interactive
```

系统会自动：
- 📊 分析技能要求
- 🎯 评估匹配度
- 💡 提供改进建议
- 💾 保存到数据库

#### 3️⃣ 优化简历

```bash
/resume/optimize google sse-l4
```

系统会：
- 🎯 突出相关技能
- 📝 优化关键词密度
- ✅ ATS格式化
- 📄 生成定制版本

#### 4️⃣ 准备面试

```bash
/interview/prep google
```

获得：
- 📅 10天准备计划
- 📚 推荐学习资源
- 🎯 每日任务清单
- 💡 成功预测

#### 5️⃣ 模拟面试

```bash
/interview/simulate google coding --mode time-pressure
```

真实面试体验：
- 🎭 专业面试官
- ⏱️ 计时压力
- 📊 详细反馈
- 💪 改进建议

---

## 🚀 核心功能

### 📄 简历管理

| 功能 | 说明 |
|------|------|
| **智能JD分析** | 自动提取技能要求、匹配度评估、文化分析 |
| **ATS优化** | 针对Workday、Greenhouse、Lever优化 |
| **关键词分析** | 目标密度优化，提升通过率 |
| **简历变体** | 为每个职位生成定制版本 |
| **A/B测试** | 追踪不同版本效果 |
| **PDF导出** | 多模板支持，专业格式 |

### 🎤 面试准备

| 功能 | 说明 |
|------|------|
| **智能模拟** | 公司特定的真实面试模拟 |
| **多种模式** | 标准、时间压力、挑战、新手友好 |
| **问题生成** | 基于JD生成针对性问题库 |
| **弱点分析** | 智能识别需要改进的领域 |
| **个性化指导** | 10天准备计划，每日任务 |
| **成功预测** | ML风格的概率评估模型 |

### 📊 分析洞察

| 功能 | 说明 |
|------|------|
| **可视化仪表板** | 应用漏斗、技能热图、趋势分析 |
| **市场情报** | 技能趋势、薪资分析、竞争定位 |
| **进步追踪** | 活动日历、技能曲线、目标达成 |
| **成功模式** | 识别有效策略，推荐最优路径 |
| **预测分析** | 基于历史预测面试成功率 |

### 🤝 求职协调

| 功能 | 说明 |
|------|------|
| **智能协调器** | 端到端工作流自动化 |
| **批量导入** | LinkedIn、Indeed、公司网站 |
| **日历同步** | iCal导出、Google Calendar集成 |
| **提醒系统** | 多级智能提醒（1周、1天、2小时） |
| **状态追踪** | 实时更新申请状态 |

### 💰 Offer谈判

| 功能 | 说明 |
|------|------|
| **Offer分析** | 全面分析薪资package |
| **市场调研** | Levels.fyi数据，薪资benchmark |
| **谈判策略** | 专业级策略和脚本 |
| **多Offer对比** | 维度对比，推荐决策 |
| **还盘起草** | 邮件模板和话术指导 |

### 🚀 职业规划

| 功能 | 说明 |
|------|------|
| **5年规划** | 详细职业发展路线图 |
| **技能差距** | 角色转换指导（SDE→SRE等） |
| **学习路径** | 12周学习计划，资源推荐 |
| **认证建议** | 行业认证路线图 |
| **角色对比** | IC vs Management路径 |

---

## 📖 使用指南

### 核心工作流

#### 工作流 1: 完整申请流程 🎯

```bash
# 步骤 1: 导入和分析JD
/jd/import https://linkedin.com/jobs/123
# 或
/jd/analyze google

# 步骤 2: 生成定制简历
/resume/optimize google sse-l4

# 步骤 3: 查看匹配度
/company/view google

# 步骤 4: 面试准备
/interview/prep google

# 步骤 5: 模拟面试
/interview/simulate google coding

# 步骤 6: 查看弱点
/weakness/plan

# 步骤 7: 针对性练习
/weakness/practice

# 步骤 8: 追踪进度
/analytics/dashboard
```

#### 工作流 2: 面试准备循环 🔄

```bash
# 准备 → 模拟 → 反馈 → 改进
/interview/prep amazon
/interview/simulate amazon system-design
/weakness/analyze
/weakness/practice system-design
```

#### 工作流 3: 智能协调 🤖

```bash
# 让AI协调器为你规划完整策略
/coordinator "我想在3个月内拿到Google offer"

# 自动完成：
# ✅ 分析差距
# ✅ 生成计划
# ✅ 优化简历
# ✅ 准备面试
# ✅ 追踪进度
```

### 常用命令速查表

#### 🔧 系统管理
```bash
/setup                          # 初始化系统
/status                         # 查看系统状态
/progress                       # 快速进度概览
```

#### 🏢 公司和JD管理
```bash
/company/add [name]             # 添加新公司
/company/view [company]         # 查看公司详情
/company/list                   # 列出所有公司
/jd/import [url]                # 导入JD
/jd/analyze [company]           # 重新分析JD
```

#### 📄 简历操作
```bash
/resume/optimize [company] [position]  # 优化简历
/resume/compare [v1] [v2]            # 对比简历
/resume/export-pdf                  # 导出PDF
```

#### 🎤 面试准备
```bash
/interview/prep [company]              # 生成准备计划
/interview/simulate [company] [type]   # 模拟面试
/interview/history                    # 查看面试历史
```

#### 📉 弱点改进
```bash
/weakness/analyze                      # 分析弱点
/weakness/plan                         # 生成改进计划
/weakness/practice                     # 推荐练习
```

#### 📊 分析和洞察
```bash
/analytics/dashboard                   # 可视化仪表板
/analytics/market                      # 市场情报
/analytics/progress                    # 进度追踪
```

#### 🤝 协调和自动化
```bash
/coordinator [goal]                    # 智能协调
/calendar/sync                         # 日历同步
/offer/negotiate [company]             # Offer谈判
/career/advise                         # 职业建议
```

---

## 💡 使用场景

### 场景 1: 准备Google面试 🎯

```bash
# 1. 导入Google JD
/jd/import [Google JD URL]

# 2. 生成Google定制简历
/resume/optimize google sse-l4

# 3. 生成10天准备计划
/interview/prep google

# 4. 模拟Google面试
/interview/simulate google coding --mode time-pressure

# 5. 查看反馈和弱点
/weakness/plan

# 6. 针对性练习
/weakness/practice algorithms medium

# 7. 追踪进度
/analytics/dashboard
```

### 场景 2: 比较多个Offer 💰

```bash
# 1. 分析第一个Offer
/offer/negotiate google --analyze
# Total: $340k

# 2. 分析第二个Offer
/offer/negotiate amazon --analyze
# Total: $345k (first year)

# 3. 对比分析
/offer/compare google amazon

# 4. 生成谈判策略
/offer/negotiate google --strategy

# 5. 起草还盘邮件
/offer/negotiate google --draft-email
```

### 场景 3: 系统性提升技能 📈

```bash
# 1. 全面分析弱点
/weakness/plan

# 2. 生成8周改进计划
# (自动生成详细计划)

# 3. 获取每日练习
/weakness/practice --daily

# 4. 练习后记录
/weakness/practice --record

# 5. 查看进步
/analytics/weakness

# 6. 调整计划
/weakness/plan --update
```

### 场景 4: 职业转换（SDE → SRE）🔄

```bash
# 1. 获取转换指导
/career/advise "SDE to SRE transition"

# 2. 分析技能差距
# (自动识别K8s、监控等差距)

# 3. 生成12周学习路径
# (详细学习计划)

# 4. 推荐认证
/career/certifications --role sre

# 5. 规划项目
/career/projects --sre-transition

# 6. 转换时间线
/career/timeline --sde-to-sre
```

---

## 📂 项目结构

```
claude-code-interview/
├── .claude/
│   ├── skills/              # AI技能（8个）
│   │   ├── jd-analyzer/          # JD分析
│   │   ├── resume-optimizer/    # 简历优化
│   │   ├── interview-coach/     # 面试指导
│   │   ├── question-generator/  # 问题生成
│   │   ├── coordinator/         # 智能协调
│   │   ├── offer-negotiator/    # 薪资谈判
│   │   ├── career-advisor/      # 职业规划
│   │   └── linkedin-importer/   # LinkedIn导入
│   │
│   ├── agents/              # 子代理（1个）
│   │   └── interview-simulator.md  # 面试模拟器
│   │
│   └── commands/            # 命令（20+个）
│       ├── setup.md            # 初始化
│       ├── company/            # 公司管理
│       ├── resume/             # 简历操作
│       ├── interview/          # 面试准备
│       ├── weakness/           # 弱点分析
│       ├── analytics/          # 数据分析
│       ├── calendar/           # 日历同步
│       └── jd-import.md        # JD导入
│
├── data/                     # 数据文件
│   ├── schemas/             # JSON Schema验证（4个）
│   ├── resume/              # 简历数据
│   ├── companies/           # 公司数据
│   ├── interviews/          # 面试记录
│   ├── analytics/           # 分析数据
│   └── state.json           # 系统状态
│
├── docs/                    # 文档
│   ├── getting-started.md
│   ├── commands-reference.md
│   └── best-practices.md
│
└── README.md               # 本文件
```

---

## 🎓 最佳实践

### 1. 定期更新数据

```bash
# 每周
/weakness/practice --record  # 记录练习
/analytics/dashboard         # 查看进度

# 每月
/weakness/plan --update      # 调整计划
/career/review               # 职业回顾
```

### 2. 保持一致性

```bash
# 每日练习（2-3小时）
/weakness/practice --daily

# 每周模拟面试（1-2次）
/interview/simulate

# 每周进度回顾（周日晚上）
/progress
```

### 3. 利用智能协调

```bash
# 让AI帮你规划复杂任务
/coordinator "规划下周的面试准备"
/coordinator "分析我所有申请的优先级"
/coordinator "生成本月学习计划"
```

### 4. 数据驱动决策

```bash
# 查看市场趋势
/analytics/market

# 分析竞争定位
/analytics/market --positioning

# 预测成功率
/analytics/dashboard --probability
```

---

## 📊 数据隐私

所有数据存储在本地，不会上传到云端：

- ✅ 简历数据：本地 `data/resume/`
- ✅ 公司数据：本地 `data/companies/`
- ✅ 面试记录：本地 `data/interviews/`
- ✅ 分析数据：本地 `data/analytics/`

---

## 🐛 故障排除

### 常见问题

**Q: 命令找不到？**
```bash
# 确保在项目根目录
pwd

# 检查命令文件
ls .claude/commands/

# 如果缺失，运行安装
/setup
```

**Q: 数据文件缺失？**
```bash
# 重新初始化
/setup --force
```

**Q: 技能调用失败？**
```bash
# 检查技能文件
ls .claude/skills/
```

---

## 🤝 贡献

欢迎贡献！请查看 `CONTRIBUTING.md` 了解详情。

### 贡献方式

1. 报告Bug
2. 提出新功能建议
3. 提交代码改进
4. 完善文档
5. 分享使用经验

---

## 📄 许可证

MIT License - 详见 `LICENSE` 文件

---

## 🙏 致谢

感谢所有贡献者和用户的支持！

特别感谢：
- Anthropic团队创建Claude Code
- 所有测试用户提供的反馈
- 开源社区的工具和资源

---

## ⭐ 如果这个项目对你有帮助，请给个Star！

---

<div align="center">

  **Made with ❤️ by the Claude Code Interview community**

  *Happy interviewing! 🚀*

  [⬆ 返回顶部](#-claude-code-interview-system)

</div>
