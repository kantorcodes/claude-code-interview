---
description: 查看特定公司的详细信息和准备情况
argument-hint: <company-name>
allowed-tools: Read
---

# 查看公司详情

显示 **$ARGUMENTS** 的详细信息和求职进展。

## 显示内容

### 1. 公司基本信息
- 公司名称、行业、规模
- 公司官网、总部
- 公司类型

### 2. 目标职位
- 职位名称和级别
- 工作地点和团队
- 职位描述摘要

### 3. JD分析结果
#### 技能要求
- 必需技能列表
- 优先技能列表
- 加分项

#### 匹配度分析
- ✅ 完全匹配的技能
- ⚠️ 部分匹配的技能
- ❌ 缺失的技能

#### 总体匹配度
- 评分 (0-100)
- 匹配度等级
- 改进建议

### 4. 申请进度
- 当前状态
- 当前阶段
- 已完成的阶段
- 下一步行动

### 5. 面试安排
- 已安排的面试
- 面试类型和格式
- 面试官信息（如有）
- 时间和平台

### 6. 研究笔记
- 公司文化
- 面试流程
- 已知面试题
- 准备提示

### 7. 薪资范围
- 基本工资范围
- 奖金比例
- 股票/RSU

## 示例输出

```
# Google 详细信息

## 公司信息
**行业**: Technology
**规模**: 100,000+
**类型**: Public
**总部**: Mountain View, CA
**官网**: google.com

## 目标职位
**职位**: Software Engineer III
**级别**: L4
**地点**: Beijing, China
**团队**: Cloud Platform
**状态**: interviewing

## JD分析

### 必需技能
- Python ✓ (expert)
- Java ✓ (intermediate)
- Distributed Systems ✓ (advanced)
- Cloud Computing ✓ (advanced)

### 优先技能
- Kubernetes ⚠️ (基础)
- Machine Learning ✓ (intermediate)

### 缺失技能
- C++ ❌ (需要学习)

### 匹配度: 75/100 (良好)

## 申请进度
**当前状态**: interviewing
**当前阶段**: Technical Round (2/5)

### 已完成
✅ Resume Screen - 2025-01-06
✅ Online Assessment - 2025-01-08

### 进行中
🔄 Technical Round - 已安排 2025-01-15

### 待安排
⏳ System Design
⏳ Behavioral Interview
⏳ HR Round

## 面试安排
**2025-01-15 14:00**
- 类型: Technical Interview
- 格式: Online (Google Meet)
- 时长: 45分钟
- 准备: 算法、数据结构、编码

## 研究笔记
**公司文化**:
- 重视创新和技术卓越
- "Googley"文化（好奇、学习、同理心）
- 用户至上

**面试流程**:
1. 简历筛选
2. 在线测试
3. 技术面试（2轮）
4. 系统设计（1轮）
5. 行为面试（1轮）

**已知问题**:
- 设计URL短链服务
- 实现LRU缓存
- 二叉树遍历

**准备提示**:
- Google强调可扩展性和可靠性
- 重视代码质量和可测试性
- 系统设计要考虑数据一致性

## 薪资范围
- Base: 300k-500k RMB/year
- Bonus: 15-20%
- Stock: RSU 4年

## 快速操作
- /resume/variant google - 创建定制简历
- /interview/prep google - 生成准备指南
- /interview/simulate google technical - 模拟面试
```

## 下一步建议
根据当前状态提供具体建议：
- 需要准备什么
- 优先级排序
- 时间安排建议
