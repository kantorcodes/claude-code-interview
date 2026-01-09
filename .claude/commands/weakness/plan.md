---
description: 基于面试反馈和自我分析，生成详细的弱点改进计划。提供学习资源、练习建议、时间规划。
argument-hint: [interview-id] [focus-area]
allowed-tools: Read, Write
---

# 生成弱点改进计划

分析面试表现和技能差距，生成系统化的改进计划。

## 使用方法

### 基于最近面试生成计划
```bash
/weakness/plan

# 将使用最近一次面试的数据
```

### 基于特定面试生成计划
```bash
/weakness/plan google-round1

# 使用特定面试的反馈数据
```

### 聚焦特定领域
```bash
/weakness/plan --technical

# 只关注技术弱点

/weakness/plan --behavioral

# 只关注行为面试弱点

/weakness/plan --communication

# 只关注沟通弱点
```

## 分析维度

### 1. 技术弱点分析
基于面试反馈分析：

#### 算法和数据结构
```json
{
  "weakness": {
    "category": "Algorithms",
    "issues": [
      {
        "problem": "DP问题优化思路不清晰",
        "frequency": "出现3次",
        "severity": "major",
        "impact": "未能通过 coding round"
      }
    ],
    "root_cause": "缺乏系统练习，DP模式掌握不足",
    "improvement_plan": {
      "resources": [
        "LeetCode DP专题 - 50题",
        "《算法导论》动态规划章节",
        "TechLead DP模式视频"
      ],
      "practice_plan": [
        "Week 1-2: 基础DP模式 (Fibonacci, Climbing Stairs)",
        "Week 3-4: 背包问题系列",
        "Week 5-6: LCS, LIS系列",
        "Week 7-8: 综合问题"
      ],
      "success_criteria": "连续10道DP题 >80%正确率"
    }
  }
}
```

#### 系统设计
```json
{
  "weakness": {
    "category": "System Design",
    "issues": [
      {
        "problem": "Scalability考虑不足",
        "examples": ["未考虑数据分片", "缺少缓存策略"],
        "severity": "critical",
        "improvement_needed": "深入学习大规模系统设计"
      }
    ],
    "resources": [
      "DDIA - Designing Data-Intensive Applications",
      "System Design Primer",
      "Google SRE书籍"
    ]
  }
}
```

### 2. 沟通弱点分析

#### 清晰度
```json
{
  "communication": {
    "clarity": {
      "current_level": "中等",
      "issues": [
        "解释问题时思路跳跃",
        "缺少结构化表达",
        "术语使用不一致"
      ],
      "improvement_plan": {
        "techniques": [
          "使用STAR方法组织答案",
          "先给出概述再深入细节",
          "使用First, Next, Finally结构"
        ],
        "practice": [
          "每天口头解释一个算法问题",
          "录制自己的回答并回听",
          "与练习伙伴mock interview"
        ],
        "timeline": "2-3周可见改善"
      }
    }
  }
}
```

#### 主动沟通
```json
{
  "communication": {
    "proactive": {
      "issues": [
        "等待interviewer提示",
        "不主动clarify需求",
        "缺少中间checkpoints"
      ],
      "best_practices": [
        "开始前确认问题理解",
        "每5分钟口头说明思路",
        "遇到歧义立即提问",
        "主动讨论trade-offs"
      ]
    }
  }
}
```

### 3. 时间管理分析

#### 问题识别
```json
{
  "time_management": {
    "problems": {
      "problem_decomposition": {
        "issue": "花了太多时间在理解问题上",
        "avg_time": "12分钟 (目标: 5分钟)",
        "impact": "coding时间不足"
      },
      "coding": {
        "issue": "编码时间超时",
        "avg_time": "35分钟 (目标: 25分钟)",
        "root_cause": "代码优化过度"
      },
      "testing": {
        "issue": "几乎没有时间测试",
        "avg_time": "2分钟 (目标: 5分钟)",
        "risk": "edge cases未检查"
      }
    },
    "recommended_allocation": {
      "understanding": "5 minutes (15%)",
      "planning": "3 minutes (10%)",
      "coding": "20 minutes (60%)",
      "testing": "5 minutes (15%)",
      "total": "45 minutes"
    }
  }
}
```

#### 改进策略
```markdown
# 时间管理改进计划

## 短期策略（1-2周）
1. **设置时间提醒**
   - 使用timer或alarm
   - 每10分钟检查进度
   - 强制进入下一步

2. **快速问题分解**
   - 练习5分钟内完成clarification
   - 使用框架化思考（输入→处理→输出）
   - 列出关键测试用例

3. **MVP优先**
   - 先写最简solution
   - 确保正确性再优化
   - 避免premature optimization

## 长期策略（3-4周）
1. **建立节奏感**
   - 每天计时练习3-5题
   - 形成时间直觉
   - 自动调整节奏

2. **提升编码速度**
   - 练习常用代码模式
   - 减少语法错误
   - 使用IDE快捷键

3. **快速测试技能**
   - 学习快速构造测试用例
   - 识别常见edge cases
   - 使用assertion模板
```

### 4. 思维模式分析

#### 问题分解
```json
{
  "thinking_patterns": {
    "decomposition": {
      "current": "直接进入细节",
      "target": "自顶向下分解",
      "gap": "缺少中间层思考",
      "practice": [
        "练习画系统架构图",
        "使用分层设计思维",
        "先high-level再细节"
      ]
    },
    "edge_cases": {
      "current": "最后才想到",
      "target": "设计时考虑",
      "techniques": [
        "使用测试驱动设计",
        "列出所有边界条件",
        "考虑异常和错误处理"
      ]
    },
    "trade_offs": {
      "current": "缺少权衡分析",
      "target": "主动讨论trade-offs",
      "framework": [
        "识别关键约束",
        "列出多个方案",
        "比较pros/cons",
        "选择并justify"
      ]
    }
  }
}
```

## 改进计划生成

### 综合改进计划
```markdown
# 弱点改进计划

## 📊 总体评估

基于最近3次面试分析：
- 技术能力: 72/100
- 沟通能力: 68/100
- 时间管理: 55/100
- 系统思维: 65/100

**优先级排序**:
1. 🔴 时间管理 (Critical)
2. 🟡 系统设计 (High)
3. 🟡 动态规划 (High)
4. 🟢 沟通清晰度 (Medium)

---

## 🎯 Phase 1: 时间管理强化 (Week 1-2)

### 目标
将45分钟coding round的时间分配优化到合理范围

### 每日练习
- **Morning (30min)**: 2题快速练习，严格计时
  - Understanding: ≤5min
  - Coding: ≤20min
  - Testing: ≥5min

- **Evening (45min)**: 1题完整练习，录制过程
  - 复盘时间分配
  - 识别浪费时间的环节

### 关键改进
1. ✅ 使用timer强制时间限制
2. ✅ 练习快速问题理解（5min framework）
3. ✅ 优先完成MVP，再优化
4. ✅ 每题后进行时间回顾

### 成功指标
- [ ] 90%题目在45min内完成
- [ ] Understanding阶段 ≤5min
- [ ] Testing阶段 ≥5min
- [ ] 连续3天达标

---

## 🎯 Phase 2: 系统设计深化 (Week 3-4)

### 学习资源
- 📖 DDIA - 第5, 6, 7章
- 📖 System Design Primer
- 🎥 System Design Interview Course

### 练习计划
**每周3个系统设计题**:
1. Monday: URL Shortener
2. Wednesday: Design Twitter
3. Friday: Design Uber

### 每题框架
```
1. Clarify Requirements (5min)
2. Capacity Estimation (5min)
3. API Design (10min)
4. Data Model (10min)
5. High-level Design (15min)
6. Scalability (10min)
```

### 重点强化
- [ ] 数据分片策略
- [ ] 缓存设计模式
- [ ] 负载均衡方法
- [ ] 数据一致性保证
- [ ] 容错和恢复

### 成功指标
- [ ] 能独立设计中等复杂度系统
- [ ] 主动讨论trade-offs
- [ ] 考虑scalability和reliability
- [ ] 解释清晰有逻辑

---

## 🎯 Phase 3: 动态规划专题 (Week 5-6)

### 学习路径
**Week 5: 基础DP模式**
- Day 1-2: Fibonacci, Climbing Stairs (入门)
- Day 3-4: House Robber系列
- Day 5-6: 背包问题 (0/1, 完全, 多重)
- Day 7: 综合练习

**Week 6: 进阶DP**
- Day 1-2: LCS, LIS, 编辑距离
- Day 3-4: 状态压缩DP
- Day 5-6: 区间DP, 树形DP
- Day 7: 模拟测试

### 练习策略
- 每天至少3道DP题
- 按模式分类练习
- 总结每种模式的识别特征
- 建立DP pattern checklist

### 成功指标
- [ ] 完成50道DP题
- [ ] 能识别DP问题类型
- [ ] 30分钟内解决中等DP
- [ ] 正确率 >80%

---

## 🎯 Phase 4: 沟通提升 (Week 7-8)

### 结构化表达训练

#### STAR方法强化
**练习**: 每天1个行为问题
- Situation: 10-15秒
- Task: 5-10秒
- Action: 45-60秒 (核心)
- Result: 15-20秒

#### 技术解释框架
```
1. High-level overview (是什么)
2. Key components (包含什么)
3. How it works (怎么工作)
4. Trade-offs (优缺点)
5. When to use (使用场景)
```

### 练习方法
1. **每日练习** (30min)
   - 口头解释一个技术概念
   - 录制并回听
   - 标记改进点

2. **Mock Interview** (每周2次)
   - 与伙伴练习
   - 请求反馈
   - 专注改进

3. **自我记录**
   - 记录常见表达问题
   - 准备标准答案模板
   - 反复练习至自然

### 成功指标
- [ ] 表达清晰有逻辑
- [ ] 使用结构化框架
- [ ] 主动clarify需求
- [ ] 讨论trade-offs

---

## 📅 每周时间安排

### Weekday (2-3 hours/day)
- **Morning (1h)**: LeetCode练习 (2题)
- **Evening (1-2h)**: 专题学习或Mock interview

### Weekend (4-6 hours/day)
- **Saturday**: 系统设计深度学习
- **Sunday**: 综合复习 + Mock interviews

### 每周检查
- [ ] 完成既定练习量
- [ ] 弱点有改善
- [ ] 时间达标
- [ ] 调整下周计划

---

## 📈 进度追踪

### Week 1-2: 时间管理
- Baseline: 55/100
- Week 1 Goal: 65/100
- Week 2 Goal: 75/100

### Week 3-4: 系统设计
- Baseline: 65/100
- Week 3 Goal: 72/100
- Week 4 Goal: 80/100

### Week 5-6: 动态规划
- Baseline: 60/100
- Week 5 Goal: 70/100
- Week 6 Goal: 80/100

### Week 7-8: 沟通
- Baseline: 68/100
- Week 7 Goal: 75/100
- Week 8 Goal: 82/100

### 综合目标
- **Start**: 65/100 (average)
- **8-Week Goal**: 80/100 (average)
- **Stretch**: 85/100 (average)

---

## 🎓 学习资源汇总

### 在线课程
- [ ] Grokking the System Design Interview
- [ ] LeetCode Explore (Cards系列)
- [ ] TechLead YouTube Channel

### 书籍
- [ ] DDIA - Designing Data-Intensive Applications
- [ ] Elements of Programming Interviews
- [ ] Cracking the Coding Interview

### 平台
- [ ] LeetCode (算法练习)
- [ ] Pramp (Mock interviews)
- [ ] Interviewing.io (真实面试记录)
- [ ] System Design One (系统设计案例)

### YouTube频道
- [ ] TechLead
- [ ] CS Dojo
- [ ] System Design Interview
- [ ] Back To Back SWE

---

## 💡 执行建议

1. ** consistency > intensity**
   每天坚持2小时 > 周末突击10小时

2. **质量 > 数量**
   深度理解10题 > 浅尝辄止50题

3. **反馈循环**
   Practice → Feedback → Adjust → Practice

4. **记录进步**
   建立进步日志，可视化成长

5. **保持健康**
   充足睡眠 + 适度运动 = 高效学习

---

## 📊 成功标准

### 8周后的预期成果：

**Technical Skills**:
- [ ] 能解决Hard难度算法题
- [ ] 能独立设计中等复杂系统
- [ ] 理解常见设计模式

**Communication**:
- [ ] 表达清晰有逻辑
- [ ] 能有效讨论技术方案
- [ ] 能主动沟通进展

**Time Management**:
- [ ] 45分钟内完成coding round
- [ ] 合理分配各阶段时间
- [ ] 有时间测试和优化

**Confidence**:
- [ ] 减少面试焦虑
- [ ] 提升问题解决信心
- [ ] 建立面试节奏感

---

## 🔄 迭代优化

每2周review:
1. 评估进度
2. 调整计划
3. 重新聚焦
4. 继续前进

**记住**: 改进是一个渐进过程，持续努力，终会成功！💪
```

## 持续追踪

### 保存改进计划
```bash
# 保存到analytics
Write: data/analytics/weaknesses.json

{
  "current_plan": {
    "start_date": "2024-01-15",
    "end_date": "2024-03-15",
    "phases": [...],
    "progress": {...}
  }
}
```

### 定期更新
```bash
# 每周更新进度
/weakness/plan --update

# 查看当前进度
/weakness/plan --status
```

## 相关命令

- `/weakness/practice` - 获取针对性练习
- `/interview/simulate` - 模拟面试测试
- `/analytics/weakness` - 查看弱点分析
- `/progress` - 查看整体进度
