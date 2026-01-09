---
description: 根据弱点分析结果，推荐针对性的练习题和学习资源。智能推荐，追踪进度。
argument-hint: <category> [difficulty]
allowed-tools: Read, Write, Grep
---

# 针对性练习

基于弱点分析，推荐个性化练习题和学习资源。

## 使用方法

### 获取针对弱点练习
```bash
# 基于最近面试的弱点
/weakness/practice

# 练习特定类别
/weakness/practice algorithms
/weakness/practice system-design
/weakness/practice behavioral

# 指定难度
/weakness/practice algorithms medium
/weakness/practice algorithms hard

# 获取每日练习计划
/weakness/practice --daily
```

## 练习类别

### 1. 算法练习
#### 基于弱点推荐
```json
{
  "algorithm_practice": {
    "weakness": "Dynamic Programming",
    "current_level": "Beginner",
    "target_level": "Intermediate",

    "practice_plan": {
      "phase_1": {
        "duration": "Week 1-2",
        "focus": "Basic DP Patterns",
        "problems": [
          {
            "id": 70,
            "name": "Climbing Stairs",
            "difficulty": "Easy",
            "pattern": "Fibonacci-style DP",
            "why": "入门DP，建立基本概念"
          },
          {
            "id": 198,
            "name": "House Robber",
            "difficulty": "Medium",
            "pattern": "Decision DP",
            "why": "练习状态转移思考"
          },
          {
            "id": 213,
            "name": "House Robber II",
            "difficulty": "Medium",
            "pattern": "Circular DP",
            "why": "考虑边界条件"
          }
        ],
        "daily_target": "3-5 problems",
        "time_limit": "30-45 min/problem"
      },

      "phase_2": {
        "duration": "Week 3-4",
        "focus": "Classic DP Problems",
        "problems": [
          {
            "id": 0,
            "name": "Knapsack problem variants",
            "difficulty": "Medium",
            "pattern": "0/1 Knapsack",
            "problems": ["416", "474", "494"]
          },
          {
            "id": 300,
            "name": "Longest Increasing Subsequence",
            "difficulty": "Medium",
            "pattern": "LIS DP",
            "why": "经典子序列DP"
          },
          {
            "id": 1143,
            "name": "Longest Common Subsequence",
            "difficulty": "Medium",
            "pattern": "LCS DP",
            "why": "双序列DP"
          }
        ]
      },

      "phase_3": {
        "duration": "Week 5+",
        "focus": "Advanced Applications",
        "problems": [
          "72 (Edit Distance)",
          "97 (Interleaving String)",
          "127 (Word Ladder II)",
          "140 (Word Break II)"
        ]
      }
    },

    "learning_resources": {
      "articles": [
        "LeetCode DP Explore Cards",
        "GeeksforGeeks DP Tutorial"
      ],
      "videos": [
        "TechLead: Dynamic Programming",
        "CS Dojo: 5 Simple Steps",
        "BackToBackSWE: DP Intuition"
      ],
      "books": [
        "CLRS Chapter 15: Dynamic Programming",
        "Elements of Programming Interviews - DP Chapter"
      ]
    }
  }
}
```

#### 其他算法弱点
```json
{
  "categories": {
    "Arrays & Hashing": {
      "weakness": "Two Pointers应用不熟练",
      "problems": ["15", "167", "125", "42"],
      "focus": "双指针模式识别和应用"
    },
    "Trees & Graphs": {
      "weakness": "BFS/DFS选择不当",
      "problems": ["102", "107", "200", "207"],
      "focus": "图遍历策略和场景"
    },
    "Greedy": {
      "weakness": "贪心证明不充分",
      "problems": ["55", "134", "406", "763"],
      "focus": "贪心选择性质和证明"
    }
  }
}
```

### 2. 系统设计练习

#### 基于弱点推荐
```json
{
  "system_design_practice": {
    "weakness": "Scalability考虑不足",
    "current_level": "Basic",
    "target_level": "Advanced",

    "recommended_problems": [
      {
        "name": "Design TinyURL",
        "focus": [
          "Hash function design",
          "Database sharding",
          "Cache strategy"
        ],
        "key_concepts": [
          "URL encoding schemes",
          "Read-heavy vs Write-heavy",
          "CAP trade-offs"
        ],
        "estimated_time": "45 min",
        "resources": [
          "System Design Primer - URL Shortener",
          "ByteByteGo YouTube"
        ]
      },
      {
        "name": "Design Twitter",
        "focus": [
          "Timeline generation",
          "Fanout patterns",
          "Eventual consistency"
        ],
        "key_concepts": [
          "Push vs Pull model",
          "Hot/Cold storage separation",
          "Redis caching strategies"
        ],
        "estimated_time": "60 min",
        "complexity": "High"
      },
      {
        "name": "Design Chat System",
        "focus": [
          "Real-time messaging",
          "Presence management",
          "Message ordering"
        ],
        "key_concepts": [
          "WebSocket vs Long-polling",
          "Message queue design",
          "Conversation sharding"
        ]
      },
      {
        "name": "Design Google Drive",
        "focus": [
          "File synchronization",
          "Conflict resolution",
          "Version control"
        ],
        "complexity": "Very High",
        "estimated_time": "75 min"
      }
    ],

    "learning_path": {
      "foundations": [
        "1. CAP Theorem and Consistency Models",
        "2. Sharding strategies (Horizontal vs Vertical)",
        "3. Caching patterns (Cache Aside, Write Through)",
        "4. Load Balancing algorithms",
        "5. Database partitioning"
      ],

      "practice_framework": {
        "step1_clarify": "5 min",
        "step2_estimate": "5 min",
        "step3_design": "25 min",
        "step4_scalability": "10 min",
        "step5_bottlenecks": "5 min",
        "step6_tradeoffs": "5 min"
      },

      "practice_schedule": {
        "Week 1": "TinyURL, Pastebin, Instagram",
        "Week 2": "Twitter, Facebook, WhatsApp",
        "Week 3": "Google Drive, YouTube, Netflix",
        "Week 4": "Uber, Airbnb, Yelp (full stack)"
      }
    }
  }
}
```

### 3. 行为面试练习

#### STAR方法训练
```json
{
  "behavioral_practice": {
    "weakness": "STAR结构不清晰",
    "recommended_questions": [
      {
        "question": "Tell me about a time you had to deal with a difficult team member",
        "category": "Conflict Resolution",
        "focus": "如何在Action部分展现成熟度",
        "star_framework": {
          "Situation": "1-2 sentences context",
          "Task": "明确你的责任和目标",
          "Action": "主要部分，你具体做了什么",
          "Result": "量化的结果和学到的东西"
        }
      },
      {
        "question": "Describe a project that failed. What did you learn?",
        "category": "Failure & Learning",
        "focus": "诚实但不失专业，强调学习"
      },
      {
        "question": "Tell me about a time you had to lead a team through a challenging situation",
        "category": "Leadership",
        "focus": "展现领导力和影响力"
      }
    ],

    "practice_methods": [
      {
        "method": "Written Practice",
        "description": "写出完整STAR答案",
        "benefit": "理清思路",
        "time": "15 min/story"
      },
      {
        "method": "Oral Practice",
        "description": "口头练习并录音",
        "benefit": "提升表达自然度",
        "time": "5 min/story"
      },
      {
        "method": "Mock Interview",
        "description": "与伙伴练习",
        "benefit": "真实反馈",
        "frequency": "2-3 times/week"
      }
    ],

    "story_bank": {
      "technical_projects": [
        "最挑战的技术项目",
        "最大的技术失败",
        "最有影响力的贡献",
        "解决的最难bug"
      ],
      "leadership": [
        "带领团队的经历",
        "导师经历",
        "跨部门协作",
        "冲突解决"
      ],
      "growth": [
        "快速学习新技能",
        "适应变化",
        "走出舒适区"
      ]
    }
  }
}
```

### 4. 沟通练习

#### 清晰度训练
```json
{
  "communication_practice": {
    "daily_exercises": [
      {
        "exercise": "Technical Concept Explanation",
        "instruction": "选择一个技术概念，用简单语言解释",
        "time_limit": "2 minutes",
        "example": "解释 '什么是微服务架构' 给非技术人员",
        "framework": [
          "What is it? (一句话定义)",
          "Why use it? (解决的问题)",
          "How does it work? (简单机制)",
          "When to use? (使用场景)"
        ]
      },
      {
        "exercise": "Problem Walkthrough",
        "instruction": "边解题边说出思路",
        "focus": [
          "Thinking out loud",
          "Explaining decisions",
          "Asking clarifying questions"
        ]
      },
      {
        "exercise": "System Design Overview",
        "instruction": "2分钟概述一个系统设计",
        "framework": [
          "Requirements (需求)",
          "High-level design (总体设计)",
          "Key components (核心组件)",
          "Trade-offs (权衡)"
        ]
      }
    ],

    "improvement_checklist": [
      "开始前clarify问题",
      "给出overview再深入",
      "使用结构化表达",
      "主动沟通进展",
      "讨论trade-offs",
      "总结要点"
    ]
  }
}
```

## 每日练习计划

### 自动生成每日计划
```bash
$ /weakness/practice --daily

📅 今日练习计划 - 2024-01-15 (Monday)

🎯 今日重点: Dynamic Programming基础

## 上午 (1 hour)
**Algorithm Practice (DP)**
1. ✅ 70. Climbing Stairs (Easy) - 15min
   - 目标: 理解DP基础
   - 重点: 状态定义和转移

2. ✅ 198. House Robber (Medium) - 20min
   - 目标: 练习DP思维
   - 重点: 状态方程

3. ✅ 746. Min Cost Climbing Stairs (Medium) - 25min
   - 目标: 巩固DP模式
   - 重点: 最优子结构

## 下午 (30 min)
**Communication Practice**
- 口头解释"什么是动态规划" - 2min
- 练习STAR故事: "最大的技术挑战" - 15min
- Mock interview recording review - 13min

## 晚上 (45 min)
**System Design**
- Design Pastebin - 45min
  - Focus: Read optimization and caching
  - Requirements: Write-heavy, low latency

📝 今日反思
- 完成后记录进步和困难
- 更新进度到 data/analytics/weaknesses.json
- 为明天调整计划

💪 明天预告: DP进阶 - 背包问题系列
```

## 智能推荐算法

### 基于历史表现推荐
```json
{
  "recommendation_engine": {
    "factors": {
      "weakness_severity": "权重 40%",
      "learning_progress": "权重 30%",
      "interview_upcoming": "权重 20%",
      "time_available": "权重 10%"
    },

    "algorithm": {
      "step1": "识别最严重的弱点类别",
      "step2": "评估当前水平",
      "step3": "推荐适当难度的问题",
      "step4": "考虑即将到来的面试",
      "step5": "匹配可用时间"
    },

    "example": {
      "weakness": "Time Management in coding interviews",
      "upcoming_interview": "Google in 10 days",
      "recommendation": {
        "focus": "Speed + Time allocation",
        "problems": "Easy-Medium (not Hard)",
        "daily_count": "4-5 problems",
        "time_per_problem": "30 min (strict)",
        "tracking": "记录每题时间分配"
      }
    }
  }
}
```

### 自适应难度调整
```json
{
  "adaptive_difficulty": {
    "rules": {
      "连续3题正确": "提升难度",
      "连续2题错误": "降低难度",
      "超时但正确": "保持难度，优化速度",
      "快速完成但错误": "加强基础，降低难度"
    },

    "progression": {
      "Easy → Medium": "正确率 >80% 且 平均时间 <20min",
      "Medium → Hard": "正确率 >70% 且 平均时间 <30min",
      "降级条件": "正确率 <50% 或 超时 >45min"
    }
  }
}
```

## 进度追踪

### 记录练习结果
```json
{
  "practice_session": {
    "date": "2024-01-15",
    "category": "Dynamic Programming",
    "problems_completed": 3,
    "problems": [
      {
        "id": 70,
        "name": "Climbing Stairs",
        "result": "✅ Passed",
        "time_taken": "12 min",
        "difficulty_felt": "Easy",
        "notes": "理解较快，代码简洁"
      },
      {
        "id": 198,
        "name": "House Robber",
        "result": "✅ Passed",
        "time_taken": "22 min",
        "difficulty_felt": "Medium",
        "notes": "需要优化状态转移思路"
      }
    ],
    "overall_performance": "Good",
    "next_focus": "More DP pattern recognition"
  }
}
```

### 更新弱点状态
```bash
# 练习后自动更新
Write: data/analytics/weaknesses.json

{
  "categories": {
    "Dynamic Programming": {
      "status": "improving",
      "level": "basic → intermediate",
      "problems_completed": 15,
      "accuracy": 80.0,
      "avg_time": "25 min",
      "trend": "upward"
    }
  }
}
```

## 输出格式

### 完整练习推荐
```markdown
🎯 针对性练习推荐

基于最近面试分析：
- 技术弱点: Dynamic Programming
- 系统设计: Scalability考虑不足
- 沟通: 表达清晰度需提升

---

## 📌 优先级 1: Dynamic Programming (Critical)

### 本周目标 (Week 1)
- 完成15道DP题
- 掌握基础DP模式
- 正确率达到75%

### 今日练习 (3 problems)
1. 70. Climbing Stairs (Easy)
2. 198. House Robber (Medium)
3. 213. House Robber II (Medium)

### 学习资源
- 📖 LeetCode DP Explore
- 🎥 TechLead DP Tutorial
- 💡 CLRS Chapter 15

---

## 📌 优先级 2: 系统设计Scalability

### 本周目标
- 完成3个系统设计
- 重点: 缓存和分片策略

### 推荐设计
1. Design TinyURL (Focus: Read optimization)
2. Design Pastebin (Focus: Write optimization)
3. Design Instagram (Focus: Social graph scalability)

---

## 📌 优先级 3: 沟通清晰度

### 每日练习
- 1个技术概念解释 (2min)
- 1个STAR故事准备
- 1次mock interview recording

---

## 📊 进度追踪

| Category | Progress | Target | Status |
|----------|----------|--------|--------|
| DP | 12/50 problems | 15 | 🟡 On Track |
| System Design | 1/10 designs | 3 | 🔴 Behind |
| Communication | 5/15 practices | 7 | 🟡 On Track |

## 💪 鼓励

进步是一个螺旋上升的过程。坚持练习，你会看到明显的改善！

Remember: 每个Expert都曾经是Beginner 💪
```

## 互动功能

### 练习记录
```bash
# 记录练习结果
/weakness/practice --record

# 交互式记录
Problem ID: 70
Result: ✅ Passed
Time: 12 min
Notes: Good

✅ 已记录到 progress.json
```

### 查看推荐历史
```bash
/weakness/practice --history

显示过去7天的练习推荐
```

## 相关命令

- `/weakness/plan` - 生成改进计划
- `/interview/simulate` - 测试练习效果
- `/analytics/progress` - 查看整体进度
- `/leetcode/random` - 随机练习题
