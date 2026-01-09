---
description: 列出所有追踪的不足，支持过滤和排序
---

# 列出追踪的不足

正在读取不足追踪数据...

## 使用方法

```
/weakness/list [filter] [sort]
```

### 过滤器 (filter)
- `recurring` - 仅显示重复出现的不足
- `high-priority` - 仅显示高优先级（>= 7.0）
- `not-improved` - 仅显示未改善的
- `category:<name>` - 按类别筛选
  - 类别：technical, communication, time_management, thinking_pattern, other
- `status:<status>` - 按状态筛选
  - 状态：not_improved, partially_improved, improved, resolved

### 排序方式 (sort)
- `priority` - 按优先级排序（默认）
- `frequency` - 按出现次数
- `severity` - 按严重程度
- `recent` - 按最近出现时间

## 示例

```
/weakness/list                           # 列出所有不足，按优先级排序
/weakness/list recurring                # 仅显示重复出现的不足
/weakness/list category:technical       # 仅显示技术类不足
/weakness/list status:not_improved      # 仅显示未改善的不足
/weakness/list recurring sort:frequency # 重复不足按频率排序
```

---

请指定过滤器和排序方式，或直接按回车查看所有不足。
