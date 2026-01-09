---
description: 显示所有正在申请的公司及其状态
allowed-tools: Read, Glob
---

# 公司列表

显示您正在申请的所有公司及其当前状态。

## 显示内容

对每个公司显示：
- 📌 公司名称
- 💼 目标职位
- 📊 申请状态
- 📍 当前阶段
- 📈 准备度评分
- 🎯 下一步行动
- 📅 面试安排（如有）

## 状态说明

**申请状态**:
- `preparing` - 准备中
- `applied` - 已投递
- `screening` - 简历筛选
- `interviewing` - 面试中
- `offer` - 收到offer
- `rejected` - 已拒绝
- `withdrawn` - 已撤回

**面试阶段**:
- `resume_screen` - 简历筛选
- `online_assessment` - 在线测试
- `technical_round` - 技术面试
- `system_design` - 系统设计
- `behavioral` - 行为面试
- `onsite` - 现场面试
- `hr_round` - HR面试

**准备度评分**:
- 90-100: 非常准备充分
- 75-89: 准备较好
- 60-74: 需要加强
- <60: 需要大量准备

## 示例输出

```
# 申请中的公司 (3)

## 1. Google
**职位**: Software Engineer III (L4)
**状态**: 🔄 interviewing
**阶段**: Technical Round (2/5)
**准备度**: 75/100 ⚠️
**面试安排**:
- 2025-01-15: Technical Interview (Online)
- 2025-01-20: System Design (Online)

**下一步**:
- [ ] 复习分布式系统
- [ ] 练习算法题
- [ ] 准备Google行为问题

---

## 2. Meta
**职位**: Software Engineer (E4)
**状态**: 📝 applied
**阶段**: Resume Screen
**准备度**: 65/100 ⚠️
**下一步**:
- [ ] /resume/variant meta - 创建定制简历
- [ ] /interview/prep meta - 生成准备指南

---

## 3. Amazon
**职位**: SDE II
**状态**: ✅ offer
**准备度**: 85/100 ✓
**下一步**:
- [ ] /offer/compare - 比较offer
```

## 快速操作
每个公司后面提供快速命令提示：
- `/company/view <name>` - 查看详情
- `/resume/variant <name>` - 创建简历变体
- `/interview/prep <name>` - 面试准备
- `/interview/simulate <name>` - 模拟面试

## 统计信息
显示总数：
- 总申请公司数
- 各状态数量
- 本周面试安排
- 整体准备度
