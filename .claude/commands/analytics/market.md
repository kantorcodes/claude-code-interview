---
description: 分析市场趋势、技能需求、薪资水平等市场情报。提供竞争定位和技能投资建议。
argument-hint: [analysis-type] [location]
allowed-tools: Read, Write, Glob, Grep
---

# 市场情报分析

提供全面的市场情报，帮助你做出数据驱动的求职决策。

## 使用方法

### 生成市场分析报告
```bash
# 综合市场分析
/analytics/market

# 技能需求分析
/analytics/market --skills

# 薪资分析
/analytics/market --salary

# 竞争定位
/analytics/market --positioning

# 趋势分析
/analytics/market --trends

# 地区市场分析
/analytics/market --location "San Francisco"
/analytics/market --location "New York"
/analytics/market --location "Beijing"
```

### 对比分析
```bash
# 对比多个地区
/analytics/market --compare "San Francisco" "New York" "Remote"

# 对比不同公司级别
/analytics/market --compare-levels Junior Senior Staff

# 对比不同时间段
/analytics/market --compare-months 2024-01 2024-02
```

### 导出报告
```bash
# 导出为报告
/analytics/market --output exports/market/report-2024-01-15.md

# 生成可分享版本
/analytics/market --share
```

## 分析维度

### 1. 技能需求趋势分析
```markdown
## 📈 Skill Demand Trends

基于所有导入JD的技能需求分析

### 🔥 Top 20 Most In-Demand Skills

┌──────────────────────┬────────┬────────┬────────┬────────┐
│ Skill                │ Demand │ Growth │ Supply│ Gap    │
├──────────────────────┼────────┼────────┼────────┼────────┤
│ 1. Python            │   92%  │  +12%  │  High │  30%   │
│ 2. JavaScript        │   88%  │   +8%  │  High │  25%   │
│ 3. React             │   82%  │  +15%  │  Med  │  40%   │
│ 4. AWS               │   79%  │  +18%  │  Med  │  45%   │
│ 5. Kubernetes        │   75%  │  +25%  │  Low  │  65%   │
│ 6. TypeScript        │   74%  │  +20%  │  Med  │  35%   │
│ 7. Go                │   68%  │  +22%  │  Low  │  58%   │
│ 8. Distributed Systs │   65%  │  +10%  │  Low  │  70%   │
│ 9. Machine Learning  │   62%  │  +28%  │  Low  │  75%   │
│ 10. GraphQL          │   58%  │  +16%  │  Med  │  30%   │
│ 11. Docker           │   85%  │   +5%  │  High │  20%   │
│ 12. SQL              │   80%  │   +3%  │  High │  15%   │
│ 13. System Design    │   90%  │   +8%  │  Low  │  80%   │
│ 14. CI/CD            │   72%  │  +12%  │  Med  │  35%   │
│ 15. Microservices    │   68%  │  +15%  │  Med  │  40%   │
│ 16. REST APIs        │   86%  │   +2%  │  High │  10%   │
│ 17. Testing          │   70%  │   +6%  │  Med  │  25%   │
│ 18. Security         │   58%  │  +14%  │  Low  │  45%   │
│ 19. Cloud Native     │   64%  │  +20%  │  Low  │  55%   │
│ 20. Data Engineering │   55%  │  +18%  │  Low  │  50%   │
└──────────────────────┴────────┴────────┴────────┴────────┘

Demand: % of job postings requiring this skill
Growth: 6-month trend in demand
Supply: Relative availability of candidates
Gap: Demand vs. Supply gap (investment opportunity)

### 📊 Category Analysis

**Frontend**:
  - React: 82% demand, +15% growth 🔥
  - Vue.js: 35% demand, +8% growth
  - Angular: 28% demand, -3% decline 📉

**Backend**:
  - Python: 92% demand, +12% growth 🔥
  - Node.js: 75% demand, +6% growth
  - Go: 68% demand, +22% growth 🚀
  - Java: 55% demand, -5% decline 📉

**Cloud**:
  - AWS: 79% demand, +18% growth 🔥
  - GCP: 52% demand, +25% growth 🚀
  - Azure: 48% demand, +15% growth

**Data**:
  - ML/AI: 62% demand, +28% growth 🚀
  - Data Engineering: 55% demand, +18% growth
  - Analytics: 48% demand, +12% growth

**DevOps**:
  - Kubernetes: 75% demand, +25% growth 🚀
  - Docker: 85% demand, +5% growth
  - CI/CD: 72% demand, +12% growth

### 💡 Skill Investment Recommendations

**High ROI Skills** (High demand + High growth + Low supply):
  1. 🚀 Kubernetes (+25% growth, 65% gap)
  2. 🚀 Machine Learning (+28% growth, 75% gap)
  3. 🚀 Go (+22% growth, 58% gap)
  4. 🚀 GCP (+25% growth, 55% gap)
  5. 🔥 React (+15% growth, 40% gap)

**Saturated Skills** (High demand + High supply):
  ⚠️ JavaScript, Python, SQL, Docker
  → Good to have, but competitive

**Declining Skills**:
  📉 Angular (-3%), Java (-5%), jQuery (-15%)
  → Consider deprioritizing

### 🎯 Your Skill Positioning

Your Top Skills vs Market:

┌───────────────────┬────────┬────────┬────────┐
│ Your Skill        │ Your   │ Market │ Compet-│
│                   │ Level  │ Demand │ itive │
├───────────────────┼────────┼────────┼────────┤
│ Python            │ Expert │   92%  │   ✅   │
│ Distributed Sys   │ Advan  │   65%  │   ✅   │
│ AWS               │ Advan  │   79%  │   ✅   │
│ System Design     │ Inter  │   90%  │  Gap ⚠️│
│ Kubernetes        │ Basic  │   75%  │  Gap ⚠️│
│ Go                │ None   │   68%  │  Gap 🔴│
│ Machine Learning  │ Basic  │   62%  │  Gap 🟡│
└───────────────────┴────────┴────────┴────────┘

Competitive Advantage:
  ✅ Strong in high-demand areas (Python, AWS)
  ✅ Differentiated in distributed systems
  ⚠️ Gap in Kubernetes (critical)
  🔴 Missing Go (significant opportunity)

Quick Wins (1-2 months):
  1. Kubernetes: Intermediate → Advanced
  2. Machine Learning: Basic → Intermediate

Medium-term (3-6 months):
  1. Go: None → Intermediate
  2. System Design: Intermediate → Advanced
```

### 2. 薪资分析
```markdown
## 💰 Salary Market Analysis

基于50+个JD的薪资数据分析

### 📍 By Location

**San Francisco Bay Area**:
┌───────────────────┬────────┬────────┬────────┐
│ Level             │ Base   │ Stock  │ Total  │
├───────────────────┼────────┼────────┼────────┤
│ Junior            │ 120-150│  20-40 │ 140-190│
│ Mid-level         │ 160-200│  40-80 │ 200-280│
│ Senior            │ 200-260│  80-150│ 280-410│
│ Staff             │ 260-320│ 150-250│ 410-570│
│ Principal         │ 320-400│ 250-400│ 570-800│
└───────────────────┴────────┴────────┴────────┘

**New York**:
  Junior: 100-130k total
  Mid-level: 150-200k total
  Senior: 200-280k total
  Staff: 280-380k total

**Seattle**:
  Junior: 110-140k total
  Mid-level: 150-210k total
  Senior: 210-300k total
  Staff: 300-420k total

**Remote (US)**:
  Junior: 90-120k total
  Mid-level: 130-180k total
  Senior: 180-250k total
  Staff: 250-350k total

**Beijing/Shanghai**:
  Junior: 200-400k CNY
  Mid-level: 400-700k CNY
  Senior: 700-1200k CNY
  Staff: 1200-2000k CNY

### 🏢 By Company Tier

**Tier 1 (FAANG+)**:
  - Total Comp: $280-800k
  - Base: $160-400k
  - Stock: $80-400k
  - Bonus: 15-25%

**Tier 2 (Stripe, Airbnb, etc.)**:
  - Total Comp: $220-450k
  - Base: $150-250k
  - Stock: $50-150k
  - Bonus: 10-20%

**Tier 3 (Late-stage startups)**:
  - Total Comp: $160-300k
  - Base: $130-200k
  - Stock: $30-100k
  - Bonus: 10-15%

**Tier 4 (Early-stage startups)**:
  - Total Comp: $120-220k
  - Base: $100-160k
  - Stock: $20-60k (high upside)
  - Bonus: 5-10%

### 💎 Premium Skills Impact

Skills that command salary premium:

**Machine Learning**:
  - Premium: +20-35%
  - Senior ML Engineer: $350-550k

**System Design/Architecture**:
  - Premium: +15-25%
  - Staff Architect: $400-600k

**Cloud/AWS/GCP**:
  - Premium: +10-20%
  - Cloud Architect: $320-450k

**Security**:
  - Premium: +15-30%
  - Security Engineer: $300-500k

**DevOps/SRE**:
  - Premium: +10-18%
  - SRE Lead: $280-400k

### 📊 Salary vs Skills Correlation

Analyzing your market value:

Your Estimated Market Value:
  Base on skills: $180-220k
  With experience (5y): $200-260k
  With current offers: $220-280k

Competitive Positioning:
  - You're in the 60th percentile
  - Room for upside: +20-30%
  - Key gap: Kubernetes, Go

To reach 80th percentile:
  1. Add Kubernetes (+10-15%)
  2. Add Go (+8-12%)
  3. System Design to Expert (+15-20%)

Projected upside: +25-35%
Potential total: $275-350k

### 💡 Negotiation Insights

Market Leverage Points:
  1. ✅ Distributed Systems expertise (scarce skill)
  2. ✅ Cloud experience (high demand)
  3. ⚠️ System design (improving, room to grow)
  4. ❌ Kubernetes (missing skill, hurts leverage)

Negotiation Tips:
  - Highlight distributed systems projects
  - Emphasize cloud migration experience
  - Frame system design as "actively developing"
  - Be prepared to address gaps honestly

Salary Anchors:
  - Amazon SDE2: $240-280k
  - Google L4: $260-320k
  - Meta E4: $280-350k
  - Stripe L3: $250-300k
```

### 3. 竞争定位分析
```markdown
## 🎯 Competitive Positioning

你在市场中的竞争地位分析

### 📊 Overall Competitive Score

Your Score: 72/100
Market Position: **Top 30%** ✅

┌────────────────────────────────────────┐
│              Score Distribution         │
│                                        │
│  90-100 │███│ (5%) - Top tier          │
│  80-89  │███████│ (15%) - Senior+     │
│  70-79  │███████████│ (30%) ← You ✅  │
│  60-69  │███████████████│ (35%)       │
│  <60    │███████████████████████│ (15%)│
└────────────────────────────────────────┘

### 🔍 Detailed Positioning

**Technical Skills**: 68/100
  Position: Top 40%
  Strengths: Python, Distributed Systems
  Gaps: Kubernetes, Go

**Experience**: 75/100
  Position: Top 35%
  5 years, good progression
  Need more leadership

**Education**: 80/100
  Position: Top 25%
  Master's degree is plus
  Strong school reputation

**Communication**: 70/100
  Position: Top 40%
  Good, not excellent
  STAR method needs practice

**System Design**: 65/100
  Position: Top 45%
  Average, improving
  Critical gap to close

**Cultural Fit**: 85/100
  Position: Top 20%
  Strong alignment
  Leadership potential

### 🏆 Competitive Advantages

1. **Distributed Systems Expertise** 🚀
   - Rare skill (only 20% have)
   - High market value
   - Differentiates you from peers

2. **Cloud Experience** ☁️
   - AWS/GCP production experience
   - High demand skill
   - Scarcity = leverage

3. **Full-stack Capability** 💻
   - Frontend + Backend + DevOps
   - Versatility valued
   - Startup-friendly

4. **Strong Education** 🎓
   - Master's from top school
   - Signals potential
   - Opens doors

5. **Chinese + English** 🌏
   - Bilingual advantage
   - US + China opportunities
   - Market differentiator

### ⚠️ Competitive Disadvantages

1. **Missing Kubernetes** 🔴
   - 75% of jobs require it
   - Critical gap
   - Immediate priority

2. **No Go Experience** 🔴
   - 68% demand, growing
   - Shows lack of adaptability
   - Quick win potential

3. **System Design** 🟡
   - Average level
   - Required for senior roles
   - 3-month learning path

4. **ML/AI Knowledge** 🟡
   - Basic only
   - 62% demand, growing fast
   - Nice-to-have, not critical

5. **Leadership Experience** 🟡
   - Limited formal leadership
   - Required for Staff+ roles
   - Long-term development

### 🎯 Positioning Strategy

**Current Strategy**: "Distributed Systems Generalist"

Target Companies:
  ✅ Tier 2-3 (Stripe, Airbnb, Dropbox)
  ✅ Startups (need versatilists)
  ⚠️ Tier 1 (Google, Meta) - mixed
  ❌ Pure ML companies

**6-Month Strategy**: Transition to "Cloud Architect"

Action Plan:
  1. Month 1-2: Kubernetes to Advanced
  2. Month 2-4: System Design to Expert
  3. Month 3-6: Go to Intermediate

Expected Outcome:
  - Move to Top 20% (80+ score)
  - Target Tier 1 companies
  - Salary potential: +25-35%

**12-Month Strategy**: "Senior Architect"

Long-term vision:
  - Add: Leadership, Security, ML
  - Target: Staff/Principal roles
  - Salary: $350-500k

### 📈 Market Trajectory

Your Career Path:

Current (72/100): Senior SDE
  ↓
6 months (80/100): Senior/Staff SDE
  ↓
12 months (85/100): Staff SDE
  ↓
24 months (90/100): Senior Staff/Principal

Salary Projection:
  Current: $180-220k
  6 months: $220-280k
  12 months: $260-350k
  24 months: $320-450k

Key Milestones:
  ✅ Senior SDE (achieved)
  ⏳ Staff SDE (6-12 months)
  ⏳ Senior Staff (18-24 months)
  ⏳ Principal (3-5 years)
```

### 4. 趋势预测
```markdown
## 📊 Market Trends & Predictions

未来6-12个月的技术市场趋势

### 🚀 Rising Stars (Fast Growth)

**Machine Learning Engineering**:
  Current Demand: 62%
  Growth Rate: +28% (6-month)
  12-Month Prediction: 80% demand
  Investment Priority: 🔴 HIGH
  Learning Time: 6-12 months
  ROI: Very High (+30-40% salary)

**Cloud Native (Kubernetes + Envoy + gRPC)**:
  Current Demand: 64%
  Growth Rate: +20% (6-month)
  12-Month Prediction: 78% demand
  Investment Priority: 🔴 HIGH
  Learning Time: 3-6 months
  ROI: High (+20-30% salary)

**Go Language**:
  Current Demand: 68%
  Growth Rate: +22% (6-month)
  12-Month Prediction: 82% demand
  Investment Priority: 🟡 MEDIUM-HIGH
  Learning Time: 2-4 months
  ROI: High (+15-25% salary)

**GraphQL**:
  Current Demand: 58%
  Growth Rate: +16% (6-month)
  12-Month Prediction: 70% demand
  Investment Priority: 🟢 MEDIUM
  Learning Time: 2-3 months
  ROI: Medium (+10-15% salary)

### 📉 Declining Skills

**jQuery**:
  Current: 15% demand
  Trend: -15% (declining fast)
  Prediction: <5% by 2025
  Action: ❌ Deprioritize

**Angular (v1-8)**:
  Current: 28% demand
  Trend: -3% (slow decline)
  Prediction: Stable at ~20%
  Action: ⚠️ Maintenance only

**Monolithic Architecture**:
  Current: Declining
  Trend: -8% (6-month)
  Prediction: Niche only
  Action: ❌ Focus on microservices

**Traditional DevOps (no K8s)**:
  Current: Being replaced
  Trend: -10% (6-month)
  Prediction: Legacy maintenance
  Action: 🔴 Must learn Kubernetes

### 💡 Emerging Trends

**Edge Computing**:
  - Current: Niche (10%)
  - Prediction: 35% in 12 months
  - Watch: Cloudflare Workers, Vercel

**WebAssembly**:
  - Current: Early (15%)
  - Prediction: 40% in 12 months
  - Watch: Performance-critical apps

**AI/LLM Integration**:
  - Current: Emerging (25%)
  - Prediction: 65% in 12 months
  - Watch: LangChain, OpenAI API

**Platform Engineering**:
  - Current: Niche (12%)
  - Prediction: 45% in 12 months
  - Watch: Internal developer platforms

**Zero Trust Security**:
  - Current: Growing (35%)
  - Prediction: 70% in 12 months
  - Watch: Security by default

### 🎯 12-Month Skill Portfolio

Recommended Skill Mix for 2025:

**Core Skills** (Must have):
  ✅ Python, JavaScript/TypeScript
  ✅ Kubernetes, Docker
  ✅ AWS/GCP
  ✅ System Design
  ✅ SQL, NoSQL

**Growth Skills** (Competitive edge):
  🚀 Go, Rust
  🚀 Machine Learning basics
  🚀 GraphQL
  🚀 Observability (Prometheus, Grafana)

**Emerging Skills** (Future-proof):
  💡 WebAssembly
  💡 Edge Computing
  💡 AI/LLM Integration
  💡 Platform Engineering

**Deprioritize**:
  ❌ jQuery, Angular v1
  ❌ Monolithic only
  ❌ Traditional DevOps (no K8s)
```

### 5. 技能组合建议
```markdown
## 🎨 Skill Combinations & Synergies

高价值的技能组合分析

### 💎 Golden Skill Sets

**Set 1: Cloud Native Architect**
  Skills: Kubernetes + Go + AWS/GCP + Microservices
  Demand: 68% of senior roles
  Salary Premium: +30-40%
  Your Fit: 40% (need Go + K8s advanced)
  Investment: 4-6 months
  ROI: ⭐⭐⭐⭐⭐

**Set 2: ML Platform Engineer**
  Skills: Python + TensorFlow/PyTorch + Kubernetes + MLOps
  Demand: 45% of high-paying roles
  Salary Premium: +35-50%
  Your Fit: 30% (need ML + MLOps)
  Investment: 8-12 months
  ROI: ⭐⭐⭐⭐ (high effort, high reward)

**Set 3: Full-Stack SRE**
  Skills: Frontend + Backend + Kubernetes + Monitoring
  Demand: 52% of startups
  Salary Premium: +20-30%
  Your Fit: 75% (need advanced K8s)
  Investment: 2-3 months
  ROI: ⭐⭐⭐⭐⭐ (quick win)

**Set 4: Distributed Systems Expert**
  Skills: Distributed Systems + Go + System Design + Cloud
  Demand: 35% of Tier 1 companies
  Salary Premium: +25-35%
  Your Fit: 80% (need Go + design polish)
  Investment: 3-4 months
  ROI: ⭐⭐⭐⭐⭐

### 🎯 Recommended Path

**Quick Win (2-3 months)**: Full-Stack SRE
  - Kubernetes: Basic → Advanced
  - Add: Prometheus, Grafana
  - Leverage: Existing full-stack skills
  - Outcome: +20-30% market value

**Mid-term (4-6 months)**: Cloud Native Architect
  - Add: Go (Intermediate)
  - Add: Advanced microservices patterns
  - Leverage: Distributed systems background
  - Outcome: +30-40% market value

**Long-term (8-12 months)**: ML Platform Engineer
  - Add: ML/MLOps fundamentals
  - Add: TensorFlow/PyTorch
  - Leverage: Python + K8s skills
  - Outcome: +35-50% market value

### 📊 Skill Synergy Matrix

Your Current Skills × Potential Skills:

┌─────────────────┬────────┬────────┬────────┬────────┐
│                 │ Go     │ K8s    │ ML     │ GraphQ │
├─────────────────┼────────┼────────┼────────┼────────┤
│ Python          │   60%  │   75%  │   90%  │   50%  │
│ Distributed Sys │   95%  │   90%  │   70%  │   60%  │
│ AWS/GCP         │   80%  │   95%  │   65%  │   55%  │
│ System Design   │   85%  │   90%  │   60%  │   50%  │
│ Full-stack      │   55%  │   85%  │   50%  │   80%  │
└─────────────────┴────────┴────────┴────────┴────────┘

Synergy Score = Combined market value

Highest Synergy Pairs:
  1. Distributed Systems + Go = 95% 🔥
  2. AWS/GCP + Kubernetes = 95% 🔥
  3. Python + ML = 90% 🚀
  4. System Design + Go = 85% ✅
  5. System Design + K8s = 90% ✅

Your Best Next Move:
  **Kubernetes** (highest average synergy: 84%)

Why:
  - Synergizes with ALL your skills
  - High demand (75%)
  - Quick learning (2-3 months)
  - Immediate ROI
```

## 生成市场报告

### 综合报告
```markdown
# 🌍 Market Intelligence Report
## Claude Code Interview System

**Generated**: January 15, 2024
**Data Source**: 50+ JDs from Tier 1-3 companies
**Time Period**: Last 6 months
**Analysis Type**: Comprehensive market analysis

---

## 📊 Executive Summary

**Market Health**: 🟢 Strong & Growing
  - Job openings: +18% (6-month trend)
  - Average salary: +12% (year-over-year)
  - Competition: Moderate (supply/demand balanced)

**Your Position**: 72/100 (Top 30%)
  - Strengths: Distributed Systems, Cloud, Full-stack
  - Gaps: Kubernetes, Go, System Design
  - Opportunity: +25-35% upside in 6 months

**Top 3 Recommendations**:
  1. 🚀 Learn Kubernetes (2-3 months, +20% value)
  2. 🚀 Add Go language (3-4 months, +15% value)
  3. 🚀 Improve System Design (3-6 months, +20% value)

**Market Trends**:
  - Rising: ML (+28%), Kubernetes (+25%), Go (+22%)
  - Stable: Python, JavaScript, AWS
  - Declining: jQuery (-15%), Monolithic (-8%)

---

[Continue with all sections...]
```

## 数据源

### 读取和分析
```bash
# 从所有公司的JD中提取数据
Glob: data/companies/*.json
Grep: "skills", "salary", "requirements"

# 从进度数据中分析趋势
Read: data/analytics/progress.json

# 从面试数据中获取反馈
Glob: data/interviews/*.json

# 从简历数据中对比技能
Read: data/resume/base.json
```

### 分析算法
```python
# 技能需求计算
demand = (companies_requiring_skill / total_companies) * 100

# 增长率计算
growth = ((current_demand - past_demand) / past_demand) * 100

# 供需差距
gap = demand - (1 / supply_rank) * 100

# 竞争分数
competitive_score = (
    technical_skills * 0.35 +
    experience * 0.25 +
    education * 0.15 +
    communication * 0.15 +
    system_design * 0.10
)
```

## 相关命令

- `/analytics/dashboard` - 查看可视化仪表板
- `/company/compare` - 对比多个公司
- `/jd/analyze` - 分析单个JD
- `/resume/optimize` - 基于市场优化简历
- `/weakness/plan` - 生成改进计划
