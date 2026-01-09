---
description: 生成可视化分析仪表板，展示求职进度、面试表现、技能差距等。支持多种输出格式。
argument-hint: [output-format] [time-range]
allowed-tools: Read, Write, Glob, Grep
---

# 分析仪表板

生成全面的可视化分析报告，帮助你了解求职进度和改进效果。

## 使用方法

### 生成基本仪表板
```bash
# 默认格式（Markdown）
/analytics/dashboard

# 指定输出格式
/analytics/dashboard html
/analytics/dashboard markdown
/analytics/dashboard pdf

# 指定时间范围
/analytics/dashboard --week
/analytics/dashboard --month
/analytics/dashboard --all
```

### 生成特定类型报告
```bash
# 只显示应用漏斗
/analytics/dashboard --funnel

# 只显示技能分析
/analytics/dashboard --skills

# 只显示面试表现
/analytics/dashboard --interviews

# 只显示进步趋势
/analytics/dashboard --trends

# 完整仪表板（所有部分）
/analytics/dashboard --full
```

### 导出报告
```bash
# 导出到文件
/analytics/dashboard --output exports/analytics/report-2024-01-15.html

# 在浏览器中打开（HTML格式）
/analytics/dashboard html --open

# 生成PDF报告
/analytics/dashboard pdf --output exports/analytics/report.pdf
```

## 仪表板组成部分

### 1. 应用漏斗可视化
```markdown
## 📊 Application Funnel

应用进度追踪：

Researching (100)
    ▼
Applied (45) [45% conversion]
    ▼
Screening (12) [27% conversion]
    ▼
Interviews (5) [42% conversion]
    ▼
Offers (2) [40% conversion]

Overall Conversion Rate: 4.4%
```

### 2. 技能差距热图
```markdown
## 🔥 Skill Gap Heatmap

技能对比矩阵：

Your Skills vs. Job Requirements

┌─────────────────────┬────────┬────────┬────────┬────────┐
│ Category            │ Your   │ Market │ Avg    │ Gap    │
│                     │ Level  │ Demand │ Req    │ Score  │
├─────────────────────┼────────┼────────┼────────┼────────┤
│ Python              │ Expert │   85%  │ Inter  │  +25   │
│ JavaScript          │ Advan  │   78%  │ Expert │  -15   │
│ Distributed Systems │ Inter  │   65%  │ Expert │  -35   │
│ System Design       │ Inter  │   82%  │ Advan  │  -20   │
│ Cloud (AWS/GCP)     │ Advan  │   90%  │ Expert │  -10   │
│ Machine Learning    │ Basic  │   45%  │ Inter  │  -25   │
│ Kubernetes          │ Basic  │   72%  │ Inter  │  -40   │
│ Go                  │ None   │   38%  │ Basic  │  -50   │
└─────────────────────┴────────┴────────┴────────┴────────┘

Legend:
  +20+: Above requirements ✅
  +0 to +20: Meets requirements 🟢
  -0 to -20: Slight gap 🟡
  -20 to -40: Moderate gap 🔴
  -40+: Critical gap ⚠️
```

### 3. 面试表现趋势
```markdown
## 📈 Interview Performance Trends

面试评分变化（最近10次）

Interview Scores Over Time

Score (1-5)
  5 │                    ┌─────┐
    │              ┌─────┘     └─────┐
  4 │         ┌─────┘                 │
    │    ┌────┘                       └─────┐
  3 │ ───┘                                 │
    │                                       └──
  2 │
    │
  1 │
    └──────────────────────────────────────────
       1  2  3  4  5  6  7  8  9  10

Trend: Improving ↗️
Current: 4.2/5
Baseline: 2.8/5
Improvement: +50%

Category Breakdown:
  Coding:       3.8/5 ⬆️ +0.6
  System Design: 4.0/5 ⬆️ +0.8
  Behavioral:   4.5/5 ⬆️ +0.4
  Communication: 3.9/5 ⬆️ +0.5
```

### 4. 时间分配分析
```markdown
## ⏰ Time Allocation Analysis

时间投入分析（过去30天）

Total: 120 hours

┌────────────────────────────────────┐
│ LeetCode Practice       ████████ 32h (27%) │
│ System Design           ██████ 24h (20%) │
│ Resume Optimization     ████ 16h (13%) │
│ Interview Simulation    ████ 18h (15%) │
│ Behavioral Prep         ██ 10h (8%)  │
│ Company Research        ████ 20h (17%) │
└────────────────────────────────────┘

ROI Analysis:
  Highest Impact:
    1. System Design (+0.8 score improvement)
    2. Interview Simulation (+0.6 score improvement)
    3. LeetCode Practice (+0.4 score improvement)

  Low Impact:
    1. Resume Optimization (already optimized)
    2. Company Research (diminishing returns)

Recommendation:
  Shift 10h from Company Research to System Design
```

### 5. 弱点改进追踪
```markdown
## 🎯 Weakness Improvement Tracking

弱点改进进度（过去8周）

┌────────────────────┬────────┬────────┬────────┬────────┐
│ Weakness           │ Start  │ Current│ Change │ Status │
├────────────────────┼────────┼────────┼────────┼────────┤
│ Time Management    │   55/100│   75/100│ +20    │ ✅     │
│ Dynamic Programming│   60/100│   72/100│ +12    │ 🟡     │
│ System Design      │   65/100│   80/100│ +15    │ ✅     │
│ Communication      │   68/100│   75/100│ +7     │ 🟡     │
│ Kubernetes         │   30/100│   45/100│ +15    │ 🔴     │
│ Go                 │    0/100│   25/100│ +25    │ 🔴     │
└────────────────────┴────────┴────────┴────────┴────────┘

Overall Progress: +15.7 points avg

Top Achievements:
  🏆 Time Management: +20 points (Target: 75/100 ✓)
  🏆 System Design: +15 points (Target: 80/100 ✓)

Needs Focus:
  ⚠️ Go: Still at 25/100, critical gap
  ⚠️ Kubernetes: Only 45/100, requires more practice
```

### 6. 公司对比矩阵
```markdown
## 🏢 Company Comparison Matrix

申请公司对比

┌────────────┬───────┬───────┬───────┬───────┬───────┐
│ Company    │ Match │ Prog- │ Interviews│ Expected│ Status│
│            │ Score │ ress │           │ Salary │       │
├────────────┼───────┼───────┼───────┼───────┼───────┤
│ Google     │  85%  │ 3/5   │   2    │ $340k │ Active│
│ Amazon     │  82%  │ 4/5   │   3    │ $280k │  Onsite│
│ Meta       │  78%  │ 2/5   │   1    │ $360k │ Active│
│ Microsoft  │  75%  │ 3/5   │   2    │ $260k │ Active│
│ Netflix    │  72%  │ 1/5   │   0    │ $420k │ Applied│
│ Stripe     │  70%  │ 2/5   │   1    │ $320k │ Screening│
│ Airbnb     │  68%  │ 3/5   │   1    │ $290k │ Active│
└────────────┴───────┴───────┴───────┴───────┴───────┘

Progress Stages:
  1: Applied
  2: Screening
  3: Phone Screen
  4: Onsite
  5: Offer/Negotiation

Top Prospects (by Match Score):
  1. Google (85%) - High potential
  2. Amazon (82%) - Onsite scheduled ⭐
  3. Meta (78%) - Phone screen completed

Next Actions:
  - Amazon: Prepare for onsite (3 days)
  - Google: Follow up on 2nd interview
  - Meta: Technical screen next week
```

### 7. 活动日历热图
```markdown
## 📅 Activity Calendar

活动强度热图（最近90天）

       Jan 2024          Feb 2024          Mar 2024
  S M T W T F S    S M T W T F S    S M T W T F S
           ▃ ▃ ▃                     ▃ ▃ ▃ ▃
  ▂ ▃ ▄ █ █▊ ▂    ▂ ▃ ▄ ▅ █ █    ▄ ▅ ▅ ▆ █
  █ ▇ █ █ █▊ ▄    ▅ ▆ ▇ █ █ █    ▇ █ █ █ █
  █ ▅ ▄ ▃ ▂ ▂    ▇ █ █ █ █ █    █ █ █ █ █
  ▂ ▂ ▂ ▃ ▄ ▅    ▆ ▅ ▄ ▃ ▂ ▂    ▇ █ █ █ █

Legend:
  ▂ 0-1 hours  (Light)
  ▃ 1-2 hours
  ▄ 2-3 hours
  ▅ 3-4 hours
  ▆ 4-5 hours
  ▇ 5-6 hours
  █ 6+ hours  (Intensive)

Streak Days: 47 🔥
Total Hours: 240
Avg Daily: 2.7h

Most Active Periods:
  - Week 3-5: Interview preparation (avg 4.5h/day)
  - Week 8-10: System design focus (avg 3.8h/day)

Light Activity:
  - Week 6: Burnout break
  - Week 9: Family events

Insight: Consistency is key! 47-day streak is excellent.
```

### 8. 技能学习曲线
```markdown
## 📚 Skill Learning Curves

技能掌握进度（学习曲线）

Distributed Systems Mastery

Progress
100% │
     │                                            ╭─────
 90% │                                        ╭───╯
     │                                    ╭───╯
 80% │                                ╭───╯  ← Current level
     │                            ╭───╯
 70% │                        ╭───╯
     │                    ╭───╯
 60% │                ╭───╯
     │            ╭───╯
 50% │        ╭───╯
     │    ╭───╯
 40% ───╯────────────────────────────────────────────
     │
     └──────────────────────────────────────────────
        Week 1  2  3  4  5  6  7  8  9  10

Learning Rate:
  - Fast phase: Weeks 1-4 (steep curve)
  - Plateau: Weeks 5-6 (consolidation)
  - Growth: Weeks 7-10 (advanced concepts)

Time to Mastery: ~12 weeks (projected)

Related Skills Progress:
  - System Design: +15%
  - Database Design: +12%
  - API Design: +18%

Next Milestone: Advanced (90%) in 2 weeks
```

### 9. 面试成功率预测
```markdown
## 🎯 Interview Success Probability

基于历史表现的预测模型

Current Success Probability: 68% 🟢

┌────────────────────────────────────────────┐
│              Probability Distribution       │
│                                             │
│  50% ████████████████████████████           │
│  60% ████████████████████████████████       │
│  70% ████████████████████████████████████  │ ← You
│  80% ██████████████████████████████████████│
│  90% ██████████████████████████████████████│
│                                             │
└────────────────────────────────────────────┘

Confidence Interval: 68% ± 8% [60%, 76%]

Factors Influencing Score:

┌─────────────────────┬────────┬────────┬────────┐
│ Factor              │ Weight │ Score  │ Impact │
├─────────────────────┼────────┼────────┼────────┤
│ Technical Skills    │   35%  │  72/100│ +25.2  │
│ Communication       │   20%  │  75/100│ +15.0  │
│ Problem Solving     │   20%  │  70/100│ +14.0  │
│ Cultural Fit        │   15%  │  85/100│ +12.8  │
│ Time Management     │   10%  │  75/100│ +7.5   │
└─────────────────────┴────────┴────────┴────────┘

Projected Outcomes:
  - Google (85% match): 78% success probability
  - Amazon (82% match): 75% success probability
  - Meta (78% match): 70% success probability

To Reach 80% Overall:
  - Improve Technical Skills to 80/100 (+8 points)
  - Focus on system design and algorithms
  - Estimated time: 3-4 weeks

Historical Trend:
  Week 1: 45% → Week 10: 68% (+23 points)
  Trajectory: On track to reach 80% by Week 14
```

### 10. 每周目标完成情况
```markdown
## 🎯 Weekly Goals Completion

每周目标完成情况（过去8周）

┌──────┬────────────────┬────────┬────────┬────────┐
│ Week │ Focus          │ Target │ Actual │ Status │
├──────┼────────────────┼────────┼────────┼────────┤
│  1   │ Setup          │   5/5  │   5/5  │ ✅     │
│  2   │ LeetCode       │  15qs  │  18qs  │ ✅     │
│  3   │ System Design  │   2/2  │   1/2  │ 🟡     │
│  4   │ Resume         │   3/3  │   3/3  │ ✅     │
│  5   │ Interviews     │   2/2  │   1/2  │ 🔴     │
│  6   │ Rest           │  -     │  -     │ ⏸️     │
│  7   │ Weakness       │  80%   │  75%   │ 🟡     │
│  8   │ Practice       │  20qs  │  22qs  │ ✅     │
└──────┴────────────────┴────────┴────────┴────────┘

Completion Rate: 75% (6/8 weeks fully achieved)

Streak:
  ✅✅🟡✅🔴⏸️🟡✅
  Current: 1 week streak

Goal Achievement by Category:
  Technical: 80% (8/10 goals met)
  Practice: 75% (6/8 goals met)
  Applications: 67% (4/6 goals met)

This Week's Goals:
  ☐ Complete 5 LeetCode problems (Hard focus)
  ☐ Design 1 system (Twitter clone)
  ☐ Mock interview (2 sessions)
  ☐ Update 3 applications
  ☐ Read DDIA Chapter 5

On Track for: 6/10 goals
```

## 输出格式

### 1. Markdown格式（默认）
```markdown
# Analytics Dashboard

Generated: 2024-01-15 14:30:00
Time Range: Last 30 days

[All sections in Markdown format with charts and tables]
```

### 2. HTML格式
```html
<!DOCTYPE html>
<html>
<head>
    <title>Analytics Dashboard - Claude Code Interview</title>
    <style>
        /* Modern CSS styling */
        /* Interactive charts */
        /* Responsive design */
    </style>
</head>
<body>
    <div class="dashboard">
        <!-- Interactive visualizations -->
        <!-- Charts using Canvas or SVG -->
        <!-- Collapsible sections -->
        <!-- Filter controls -->
    </div>
</body>
</html>
```

### 3. PDF格式
```bash
# Generate PDF with proper layout
/analytics/dashboard pdf --output report.pdf

Features:
- Multi-page layout
- Charts and graphs
- Professional formatting
- Print-ready quality
```

## 生成流程

### 步骤 1: 读取数据
```bash
# 读取所有相关数据
Read: data/analytics/progress.json
Glob: data/companies/*.json
Glob: data/interviews/*.json
Read: data/resume/base.json
Read: data/state.json
```

### 步骤 2: 聚合指标
```json
{
  "aggregated_metrics": {
    "total_applications": 45,
    "interviews_completed": 12,
    "offers_received": 2,
    "avg_score": 4.2,
    "time_invested": "120 hours",
    "improvement_rate": "+23%"
  }
}
```

### 步骤 3: 生成可视化
```bash
# 创建图表和图形
- ASCII/Unicode charts for terminal
- SVG/Canvas for HTML
- Table layouts for comparison
```

### 步骤 4: 添加洞察
```markdown
### 💡 Key Insights

1. **Strengths**: System design improved 15 points
2. **Weaknesses**: Go and Kubernetes need focus
3. **Opportunities**: 2 companies at onsite stage
4. **Recommendations**: Prioritize Amazon prep
```

### 步骤 5: 导出报告
```bash
# 保存到文件
Write: exports/analytics/dashboard-{timestamp}.html
Write: exports/analytics/dashboard-{timestamp}.md
```

## 高级功能

### 自定义时间范围
```bash
# 最近7天
/analytics/dashboard --days 7

# 最近30天
/analytics/dashboard --days 30

# 自定义日期范围
/analytics/dashboard --from 2024-01-01 --to 2024-01-31

# 特定月份
/analytics/dashboard --month 2024-01
```

### 过滤和分组
```bash
# 只看特定公司
/analytics/dashboard --company google

# 只看特定类型
/analytics/dashboard --type technical

# 按面试状态分组
/analytics/dashboard --group-by status
```

### 比较模式
```bash
# 比较两个时间段
/analytics/dashboard --compare "2024-01-01 to 2024-01-15" "2024-01-16 to 2024-01-31"

# 比较公司与市场平均水平
/analytics/dashboard --benchmark
```

### 趋势预测
```bash
# 预测未来表现
/analytics/dashboard --forecast 4weeks

# 基于当前趋势的建议
/analytics/dashboard --recommendations
```

## 智能分析

### 自动识别模式
```markdown
### 🤖 Pattern Recognition

Detected Patterns:
  1. ✅ Consistent study schedule (47-day streak)
  2. ⚠️ Burnout risk (intensive weeks followed by breaks)
  3. ✅ Strong improvement in system design
  4. ⚠️ Coding practice plateau (weeks 7-9)
  5. ✅ High interview-to-offer conversion (40%)

Recommendations:
  - Maintain consistency but reduce intensity
  - Add variety to coding practice
  - Leverage system design strength
  - Schedule rest days proactively
```

### 成功概率计算
```markdown
### 📊 Success Probability Model

Bayesian estimation based on:
  - Historical interview performance
  - Skill match scores
  - Company-specific patterns
  - Time invested per skill
  - Weakness improvement trajectory

P(Success) = Σ(Weight_i × Feature_i) / Σ(Weights)

Current: 68% ± 8%
Target: 80%
Gap: 12 percentage points
```

### 优先级建议
```markdown
### 🎯 Priority Recommendations

This Week (Priority: HIGH):
  1. Amazon onsite preparation (3 days)
     - System design review
     - Behavioral stories (STAR)
     - Practice 5 coding problems

  2. Go fundamentals (2 hours/day)
     - Complete basic tutorial
     - Practice 10 easy problems
     - Build small project

Next Week (Priority: MEDIUM):
  1. Kubernetes basics
  2. Google 2nd interview prep
  3. Update 3 applications

This Month (Priority: LOW):
  1. LinkedIn profile optimization
  2. Network with 5 engineers
  3. Apply to 5 new companies
```

## 导出和分享

### 生成可分享链接
```bash
# 导出为HTML并上传
/analytics/dashboard html --share

# 生成PDF分享
/analytics/dashboard pdf --email recruiter@example.com
```

### 定期报告
```bash
# 每周自动生成
/analytics/dashboard --schedule weekly

# 发送到邮箱
/analytics/dashboard --email me@example.com --frequency weekly
```

## 示例输出

### 完整仪表板示例
```markdown
# 📊 Analytics Dashboard
## Claude Code Interview System

**Generated**: January 15, 2024 at 14:30:00
**Time Range**: Last 30 days (December 16, 2023 - January 15, 2024)
**Data Points**: 245 activities tracked

---

## 📌 Executive Summary

🎯 **Overall Progress**: 68/100 (+15 points from baseline)

**Key Achievements**:
- ✅ Completed 12 interviews (avg score: 4.2/5)
- ✅ Advanced to onsite at 3 companies
- ✅ Received 2 offers
- ✅ Improved system design by 15 points

**Areas for Improvement**:
- ⚠️ Go language (25/100)
- ⚠️ Kubernetes (45/100)
- ⚠️ Time management consistency

**This Week's Focus**:
1. Amazon onsite preparation (3 days)
2. Go fundamentals (2h/day)
3. Complete 5 LeetCode problems

---

## 📊 Application Funnel

```
Researching: 100 companies
    ↓ 45% applied
Applied: 45 companies
    ↓ 27% screening
Screening: 12 companies
    ↓ 42% interviews
Interviews: 5 companies
    ↓ 40% offers
Offers: 2 companies ✅
```

**Overall Conversion**: 4.4% (Research → Offer)

**Funnel Health**: 🟢 Above industry average (2-3%)

---

[Continue with all other sections...]
```

## 相关命令

- `/analytics/progress` - 查看详细进度数据
- `/analytics/weakness` - 查看弱点分析
- `/analytics/market` - 市场情报分析
- `/company/list` - 查看所有申请公司
- `/interview/history` - 面试历史记录
- `/progress` - 快速进度概览
