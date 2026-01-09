---
description: 生成全面的面试准备指南
argument-hint: <company-name> [interview-type]
allowed-tools: Read, Write, Skill(interview-coach), Skill(question-generator)
---

# 面试准备指南

为 **$1** 生成定制化面试准备指南。

## 参数说明
- **company-name**: 必需，目标公司名称
- **interview-type**: 可选，面试类型
  - `technical` - 技术面试
  - `system-design` - 系统设计
  - `behavioral` - 行为面试
  - `hr` - HR面试
  - 省略则生成全面准备指南

## 工作流程

### 步骤 1: 分析公司和JD
读取 `data/companies/$1.json`：
- 提取关键技能
- 识别技术栈
- 了解面试流程
- 分析公司文化

### 步骤 2: 识别准备重点
基于JD和公司特点：
- 技术主题清单
- 优先级排序
- 时间估算

### 步骤 3: 推荐练习题
使用 question-generator Skill：
- 生成相关技术题
- 推荐系统设计题
- 准备行为面试题

### 步骤 4: 生成准备指南
创建 `exports/interview-guides/$1_prep_guide.md`

## 准备指南结构

```markdown
# $1 面试准备指南

生成时间: {当前时间}
目标职位: {职位名称}

## 面试流程概览
{面试各阶段}

## 技术准备清单

### 高优先级 (必须掌握)
- [ ] {主题1} - 预计{X}小时
- [ ] {主题2} - 预计{X}小时

### 中优先级 (建议掌握)
- [ ] {主题3} - 预计{X}小时

### 低优先级 (加分项)
- [ ] {主题4} - 预计{X}小时

## 推荐练习题

### 算法和数据结构
1. {题目1} - {难度} - {频率}
2. {题目2} - {难度} - {频率}

### 系统设计
1. {题目1} - {公司常见}
2. {题目2} - {相关度}

### 行为面试 (STAR)
1. {问题1} - {能力}
2. {问题2} - {能力}

## 公司特定准备

### 技术重点
- {该公司重视的技术}
- {面试风格}

### 文化匹配
- {公司价值观}
- {行为特质}

### 已知问题
- {历年高频题}
- {该公司特色题}

## 时间规划

### 距离面试还有{X}天
**每日任务**:
- Day 1-3: {任务}
- Day 4-7: {任务}

### 每日时间分配
- 上午 (2h): {主题}
- 下午 (2h): {主题}
- 晚上 (1h): {主题}

## 学习资源
- {推荐资源}
- {练习平台}
- {参考文档}

## 模拟面试
- /interview/simulate $1 technical
- /interview/simulate $1 system-design
- /interview/simulate $1 behavioral

## 最后提醒
- {重要提示}
- {注意事项}
```

## 示例输出片段

### Google 技术准备
```
## 高优先级技术主题

### 1. 分布式系统 (8h)
**重点**:
- CAP定理
- 一致性算法
- 分布式事务
- 数据分片

**推荐练习**:
- 设计URL短链服务
- 设计分布式缓存
- 设计分布式锁

**资源**:
- DDIA - Designing Data-Intensive Applications
- Google系统设计论文

### 2. 算法和数据结构 (6h)
**重点**:
- 图算法
- 动态规划
- 树遍历
- 哈希表

**推荐题目**:
- LRU Cache (Medium)
- Merge K Sorted Lists (Hard)
- Word Ladder (Medium)

### 3. Python深入 (4h)
**重点**:
- GIL
- 内存管理
- 装饰器
- 生成器

## Google已知问题
1. 设计一个URL缩短服务 ⭐⭐⭐
2. 实现LRU缓存 ⭐⭐⭐
3. 设计一个键值存储 ⭐⭐
4. 解释MapReduce ⭐⭐
```

## 输出文件
保存到: `exports/interview-guides/{company}_prep_guide.md`

## 下一步
1. 查看准备指南
2. 制定学习计划
3. 开始每日练习
4. 定期模拟面试
