---
description: 对比不同简历变体的差异，分析关键词密度、匹配度、ATS兼容性等指标。帮助选择最佳版本。
argument-hint: <variant1> <variant2>
allowed-tools: Read, Write, Grep
---

# 对比简历变体

对比 **$1** 和 **$2** 两个简历变体，分析它们在关键词、匹配度、格式等方面的差异。

## 使用方法

### 对比两个变体
```bash
/resume/compare google_v1 google_v2
```

系统将：
1. 读取两个变体文件
2. 提取关键信息进行对比
3. 生成差异报告
4. 提供选择建议

## 对比维度

### 1. 基本信息
- 文件名和创建时间
- 目标公司和职位
- 变体版本号
- 最后修改时间

### 2. 关键词密度分析
对比关键词在各个部分的密度：

```json
{
  "keyword_density_comparison": {
    "summary": {
      "variant1": 18.5,
      "variant2": 22.3,
      "difference": "+3.8",
      "winner": "variant2"
    },
    "experience": {
      "variant1": 12.3,
      "variant2": 14.7,
      "difference": "+2.4",
      "winner": "variant2"
    },
    "skills": {
      "variant1": 95.0,
      "variant2": 100.0,
      "difference": "+5.0",
      "winner": "variant2"
    }
  }
}
```

### 3. 技能匹配度
对比与JD的技能匹配度：

```json
{
  "match_score_comparison": {
    "variant1": {
      "overall": 82.5,
      "required_skills": 85.0,
      "preferred_skills": 78.0
    },
    "variant2": {
      "overall": 89.2,
      "required_skills": 92.0,
      "preferred_skills": 85.0
    },
    "improvement": "+6.7",
    "winner": "variant2"
  }
}
```

### 4. ATS兼容性
评估ATS系统解析能力：

```json
{
  "ats_compatibility": {
    "workday": {
      "variant1": "medium",
      "variant2": "high"
    },
    "greenhouse": {
      "variant1": "high",
      "variant2": "high"
    },
    "lever": {
      "variant1": "high",
      "variant2": "high"
    },
    "overall_winner": "variant2"
  }
}
```

### 5. 内容差异
详细对比各部分内容：

#### Summary对比
```markdown
### Variant 1
资深软件工程师，专注于分布式系统和机器学习...

### Variant 2
资深软件工程师，专注于大规模分布式系统、云计算和机器学习，
拥有5年高并发系统开发经验...

**分析**: v2更详细，突出"大规模"和"高并发"关键词
```

#### 技能排序对比
```markdown
### Variant 1
1. Python, Java, Go
2. Django, Spring Boot, React
3. Docker, Kubernetes

### Variant 2
1. Python, Go, Java
2. Kubernetes, Docker, AWS
3. Django, Spring Boot, FastAPI

**分析**: v2将Kubernetes提前，更匹配JD要求
```

#### 经验描述对比
```markdown
### 字节跳动 - Variant 1
负责抖音电商后台核心系统的开发和优化...

### 字节跳动 - Variant 2
设计并实现高并发订单处理系统，QPS从5k提升至50k，
系统稳定性达到99.99%...

**分析**: v2使用量化数据，更具体
```

### 6. 性能指标
```json
{
  "performance_metrics": {
    "keyword_optimization": {
      "variant1": 75,
      "variant2": 90,
      "winner": "variant2"
    },
    "readability": {
      "variant1": 85,
      "variant2": 82,
      "winner": "variant1"
    },
    "conciseness": {
      "variant1": 80,
      "variant2": 78,
      "winner": "variant1"
    },
    "impact_orientation": {
      "variant1": 72,
      "variant2": 92,
      "winner": "variant2"
    }
  }
}
```

## 输出格式

### 完整对比报告
```markdown
# 简历变体对比报告：google_v1 vs google_v2

## 总体评分

| 指标 | Variant 1 | Variant 2 | 差异 | 推荐 |
|------|-----------|-----------|------|------|
| **匹配度** | 82.5 | 89.2 | +6.7 | ✅ v2 |
| **关键词密度** | 15.8% | 19.2% | +3.4% | ✅ v2 |
| **ATS兼容性** | Medium | High | ↑ | ✅ v2 |
| **可读性** | 85 | 82 | -3 | v1 |
| **影响力** | 72 | 92 | +20 | ✅ v2 |

**综合推荐**: ✅ **Variant 2**

---

## 详细分析

### 1. 关键词对比

#### 高优先级关键词覆盖
| 关键词 | Variant 1 | Variant 2 | JD要求 |
|--------|-----------|-----------|--------|
| Distributed Systems | ✅ (3次) | ✅ (5次) | 必须 |
| Python | ✅ (4次) | ✅ (4次) | 必须 |
| Kubernetes | ⚠️ (1次) | ✅ (3次) | 必须 |
| Scalability | ❌ (0次) | ✅ (2次) | 优先 |

**结论**: v2覆盖更多JD关键词

### 2. 技能部分对比

**Variant 1**:
- 编程语言: Python, Java, Go, JavaScript
- 框架: Django, Spring Boot, React
- 工具: Docker, Kubernetes, AWS

**Variant 2**:
- 编程语言: Python, Go, Java, TypeScript
- 工具: Kubernetes, Docker, AWS, GCP
- 框架: Django, Spring Boot, FastAPI

**差异**:
- v2将Kubernetes提前（更匹配JD）
- v2添加GCP和FastAPI（更全面）
- v2使用TypeScript替代JavaScript（更现代）

### 3. Summary对比

**Variant 1**:
> 资深软件工程师，专注于分布式系统和机器学习。精通Python、Java技术栈，有丰富的微服务架构经验。

**Variant 2**:
> 资深软件工程师，专注于大规模分布式系统和云计算。拥有5年高并发系统开发经验，精通Python和Go，擅长微服务架构设计和系统优化。

**分析**:
- v1: 38词，简洁但信息量较少
- v2: 62词，更详细，突出"大规模"、"高并发"关键词
- **推荐**: v2（更匹配JD要求）

### 4. 工作经验对比

#### 字节跳动 - Variant 1
```
- 主导设计并实现高并发订单处理系统，处理能力提升300%
- 优化微服务架构，将服务间调用延迟降低60%
```

#### 字节跳动 - Variant 2
```
- 设计并实现高并发订单处理系统，峰值QPS从5k提升至50k，
  系统稳定性达到99.99%，处理能力提升900%
- 优化微服务架构，通过服务拆分和缓存优化，
  将服务间调用延迟从100ms降至40ms，降低60%
```

**分析**:
- v1: 提到"提升300%"但缺乏基线数据
- v2: 使用具体数字（QPS: 5k→50k, 延迟: 100ms→40ms）
- v2添加"系统稳定性99.99%"（关键指标）
- **推荐**: v2（数据更具体可信）

### 5. ATS兼容性分析

#### Workday ATS
- **Variant 1**: ⚠️ Medium
  - 问题: 技能使用复杂格式
  - 建议: 简化为逗号分隔列表

- **Variant 2**: ✅ High
  - 优势: 标准格式，清晰章节
  - 可通过率: 95%

#### Greenhouse ATS
- **Variant 1**: ✅ High
- **Variant 2**: ✅ High
- 两者都适合Greenhouse

#### Lever ATS
- **Variant 1**: ✅ High
- **Variant 2**: ✅ High
- 两者都适合Lever

### 6. 可读性评估

| 方面 | Variant 1 | Variant 2 | 说明 |
|------|-----------|-----------|------|
| 字数 | 485 | 542 | v1更简洁 |
| 段落长度 | 适中 | 稍长 | v1更易读 |
| 专业术语密度 | 中等 | 较高 | v2技术性更强 |
| 整体流畅度 | 85/100 | 82/100 | v1更流畅 |

**结论**: 如果看重简洁性，选择v1；如果看重技术深度，选择v2

### 7. 应用效果追踪

如果有历史数据：

```json
{
  "variant_performance": {
    "v1": {
      "applications": 5,
      "interviews": 2,
      "conversion_rate": "40%"
    },
    "v2": {
      "applications": 3,
      "interviews": 2,
      "conversion_rate": "67%"
    },
    "winner": "v2"
  }
}
```

---

## 最终建议

### 推荐使用：Variant 2 ✅

**理由**:
1. ✅ 匹配度更高（89.2 vs 82.5）
2. ✅ 关键词覆盖更全面
3. ✅ ATS兼容性更好
4. ✅ 量化数据更具体
5. ✅ 更突出高并发和大规模系统经验

**使用场景**:
- 申请Google的Distributed Systems相关岗位
- ATS系统为Workday的公司
- 需要突出量化成果的职位

### 备选：Variant 1

**适用场景**:
- 需要更简洁版本的职位
- 面试时作为参考（更容易口头表达）
- ATS为Greenhouse/Lever的公司

---

## 优化建议

### 对Variant 2的进一步优化
1. **降低字数**: 可将542词压缩至500词左右
2. **简化技术术语**: 考虑HR阅读体验
3. **增加软技能**: 补充团队协作相关内容

### 合并两个版本的优点
可以考虑创建Variant 3：
- 采用v2的关键词和量化数据
- 采用v1的简洁表达
- 平衡技术深度和可读性
```

## 使用场景

### 场景1: 选择最佳版本
```bash
# 对比两个版本
/resume/compare google_v1 google_v2

# 根据建议选择更优版本
```

### 场景2: A/B测试分析
```bash
# 对比两个A/B测试版本
/resume/compare google_A google_B

# 查看哪个版本表现更好
```

### 场景3: 前后对比
```bash
# 对比优化前后的差异
/resume/compare google_original google_optimized

# 了解优化效果
```

## 数据文件位置

**变体文件**: `data/resume/variants/{variant_name}.json`
**对比报告**: 自动生成并显示在终端

## 注意事项

1. **客观性**: 对比基于数据分析，客观展示差异
2. **上下文**: 考虑目标公司和JD的具体要求
3. **灵活性**: 推荐仅供参考，根据实际情况调整
4. **迭代优化**: 简历优化是持续过程，不断改进
