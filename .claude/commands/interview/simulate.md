---
description: 启动真实的模拟面试会话
argument-hint: <company-name> <interview-type> [duration]
allowed-tools: Read, Write, Skill(interview-coach)
---

# 模拟面试

启动 **$1** 的 **$2** 模拟面试。

## 参数说明
- **company-name**: 必需，目标公司名称
- **interview-type**: 必需，面试类型
  - `technical` - 技术面试（编码）
  - `system-design` - 系统设计
  - `behavioral` - 行为面试
  - `hr` - HR面试
  - `onsite` - 完整onsite模拟
- **duration**: 可选，面试时长（分钟），默认45

## 工作流程

### 步骤 1: 面试准备
读取公司和用户信息：
- 公司和职位信息
- JD分析结果
- 用户简历和技能
- 历史面试记录

### 步骤 2: 面试设置
- 确认面试类型和时长
- 说明面试规则
- 设置计时器

### 步骤 3: 开始面试
使用 interview-coach Skill 进行模拟面试：
- 扮演面试官
- 提问并追问
- 记录回答
- 计时提醒

### 步骤 4: 面试评估
- 分析回答质量
- 识别优势和不足
- 提供改进建议
- 评分（1-5分制）

### 步骤 5: 保存记录
创建 `data/interviews/{date}_{company}_{type}.json`

## 面试类型详解

### Technical Interview (技术面试)
**形式**: 编程题
**时长**: 45分钟
**流程**:
1. 介绍问题 (2分钟)
2. 讨论方案 (5分钟)
3. 编写代码 (20分钟)
4. 测试优化 (10分钟)
5. 追问讨论 (8分钟)

**评估维度**:
- 问题理解 (5分)
- 方案设计 (5分)
- 代码质量 (5分)
- 优化能力 (5分)
- 沟通表达 (5分)

### System Design Interview (系统设计)
**形式**: 架构设计
**时长**: 45-60分钟
**流程**:
1. 理解需求 (5分钟)
2. 高层设计 (10分钟)
3. 详细设计 (20分钟)
4. 讨论trade-offs (10分钟)
5. 总结 (5分钟)

**评估维度**:
- 需求理解 (5分)
- 架构设计 (5分)
- 可扩展性 (5分)
- 可靠性 (5分)
- 讨论深度 (5分)

### Behavioral Interview (行为面试)
**形式**: STAR问题
**时长**: 30-45分钟
**流程**:
1. 提问 (每个问题3-5分钟)
2. 倾听回答
3. 追问细节
4. 评估反馈

**评估维度**:
- STAR结构 (5分)
- 故事相关性 (5分)
- 成果量化 (5分)
- 沟通清晰 (5分)
- 文化匹配 (5分)

### HR Interview (HR面试)
**形式**: 问答
**时长**: 30分钟
**流程**:
1. 自我介绍 (2分钟)
2. 职业规划 (5分钟)
3. 为什么选我们 (5分钟)
4. 薪资期望 (5分钟)
5. 其他问题 (10分钟)
6. 反向提问 (5分钟)

## 面试记录格式

```json
{
  "interview_id": "int_001",
  "company_id": "$1",
  "position_id": "...",
  "interview_date": "2025-01-09T14:00:00Z",
  "interview_type": "$2",
  "round": 1,
  "duration_minutes": $ARGUMENTS,

  "questions_asked": [
    {
      "question_id": "q_001",
      "type": "coding|system_design|behavioral",
      "question": "问题描述",
      "difficulty": "medium",
      "time_allocated": 20,
      "user_response": {
        "approach": "解题思路",
        "code_written": true,
        "time_taken": 18
      },
      "interviewer_feedback": "代码结构清晰，但可以进一步优化",
      "rating": 4
    }
  ],

  "overall_feedback": {
    "strengths": ["编码能力强", "沟通好"],
    "areas_for_improvement": ["需要加强DP"],
    "next_steps": ["练习更多DP题"]
  },

  "overall_rating": 3.8
}
```

## 面试反馈

### 技术面试反馈示例
```
## 面试反馈

### 总体评分: 4.0/5.0 ⭐⭐⭐⭐

### 详细评分
- 问题理解: 5/5 ⭐⭐⭐⭐⭐
- 方案设计: 4/5 ⭐⭐⭐⭐
- 代码质量: 4/5 ⭐⭐⭐⭐
- 优化能力: 3/5 ⭐⭐⭐
- 沟通表达: 5/5 ⭐⭐⭐⭐⭐

### 优势 ✅
- 思路清晰，考虑了多种方案
- 代码结构良好，可读性强
- 与面试官沟通积极
- 考虑了边界情况

### 需要改进 ⚠️
- 可以更深入考虑优化
- 时间复杂度分析可以更详细
- 可以主动讨论更多trade-offs

### 具体建议
1. 在写代码前先列出所有边界情况
2. 练习更多动态规划题目
3. 思考时多问"为什么这个方案"

### 下一步准备
- [ ] 复习动态规划基础
- [ ] 练习5道DP题目
- [ ] 准备系统设计面试
```

## 注意事项
- 面试过程会记录时间
- 建议录音回听（可选）
- 保持真实面试环境
- 可以暂停（但计入时间）
- 面试结束后查看详细反馈

## 输出文件
- 面试记录: `data/interviews/{date}_{company}_{type}.json`
- 详细反馈: 显示在终端
- 统计更新: `data/analytics/progress.json`

## 下一步
- 查看面试记录
- 根据反馈改进
- 准备下一轮面试
- `/interview/feedback <id>` - 深度分析
