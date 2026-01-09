---
description: 同步面试安排到日历。支持iCal导出、Google Calendar导入、提醒设置。
argument-hint: [action] [calendar-type]
allowed-tools: Read, Write, Glob
---

# 日历同步

将面试安排自动同步到你的日历系统，确保不错过任何重要的面试。

## 使用方法

### 导出面试到iCal格式
```bash
# 导出所有即将到来的面试
/calendar/sync export

# 导出特定公司的面试
/calendar/sync export google

# 导出到指定文件
/calendar/sync export --output interviews.ics
```

### 生成Google Calendar导入链接
```bash
# 生成Google Calendar导入
/calendar/sync google-calendar

# 为特定公司生成
/calendar/sync google-calendar amazon

# 批量导入链接
/calendar/sync google-calendar --all
```

### 设置提醒
```bash
# 设置默认提醒（提前1天、1小时）
/calendar/sync remind --default

# 自定义提醒时间
/calendar/sync remind --before "1 day, 2 hours, 30 minutes"

# 为特定面试设置提醒
/calendar/sync remind --interview google-round2 --before "2 days, 1 day"
```

### 查看面试日历
```bash
# 显示所有即将到来的面试
/calendar/sync list

# 显示本周面试
/calendar/sync list --week

# 显示本月面试
/calendar/sync list --month

# 显示详细日历视图
/calendar/sync list --detailed
```

### 删除日历事件
```bash
# 删除已导出的日历事件
/calendar/sync remove

# 清除所有日历同步
/calendar/sync remove --all
```

## iCal文件格式

### 标准iCal输出
```ical
BEGIN:VCALENDAR
VERSION:2.0
PRODID:-//Claude Code Interview//Interview Calendar//EN
CALSCALE:GREGORIAN
METHOD:PUBLISH
X-WR-CALNAME:面试安排
X-WR-TIMEZONE:Asia/Shanghai
X-WR-CALDESC:来自Claude Code Interview系统的面试安排

BEGIN:VEVENT
DTSTART:20240120T140000Z
DTEND:20240120T150000Z
DTSTAMP:20240115T080000Z
UID:google-round1-20240120@claude-code-interview
CREATED:20240115T080000Z
DESCRIPTION:Google L4面试 - 第1轮\n\n公司: Google\n职位: Software Engineer L4\n类型: Phone Screen\n面试官: John Smith\n\n准备要点:\n- 复习分布式系统\n- 练习2道算法题\n- 准备STAR故事\n\n备注:\n- 通过Zoom进行\n- 提前10分钟加入\n带上纸笔
LAST-MODIFIED:20240115T080000Z
LOCATION:Zoom (Meeting ID: 123-456-789)
SEQUENCE:0
STATUS:CONFIRMED
SUMMARY:🎯 Google面试 - Round 1 (Phone Screen)
TRANSP:OPAQUE
BEGIN:VALARM
TRIGGER:-PT2H
ACTION:DISPLAY
DESCRIPTION:面试提醒：2小时后开始
END:VALARM
BEGIN:VALARM
TRIGGER:-PT1D
ACTION:DISPLAY
DESCRIPTION:面试提醒：明天有面试
END:VALARM
END:VEVENT

BEGIN:VEVENT
DTSTART:20240125T190000Z
DTEND:20240125T203000Z
DTSTAMP:20240115T080000Z
UID:amazon-onsite-20240125@claude-code-interview
CREATED:20240115T080000Z
DESCRIPTION:Amazon L5 Onsite面试\n\n公司: Amazon\n职位: Senior SDE L5\n类型: Onsite (Virtual)\n轮次: 3轮技术 + 1轮行为\n\nRound 1 (10:00-10:45): System Design\nRound 2 (11:00-11:45): Coding\nRound 3 (13:00-13:45): Behavioral\nLunch (14:00-14:30)\nRound 4 (14:30-15:15): Leadership Principles\n\n准备要点:\n- 设计一个分布式系统\n- 练习时间管理\n- 准备6个Amazon LP故事\n\n备注:\n- 所有面试通过Amazon Chime进行\n- Onsite链接: amazon.chime.com/meeting/xxx\n带上纸笔、计算器（如需）
LAST-MODIFIED:20240115T080000Z
LOCATION:Amazon Chime (Virtual Onsite)
SEQUENCE:0
STATUS:CONFIRMED
SUMMARY:🎯 Amazon Onsite - 4轮
TRANSP:OPAQUE
BEGIN:VALARM
TRIGGER:-PT1D
ACTION:DISPLAY
DESCRIPTION:Amazon Onsite明天！确保今天早休息
END:VALARM
BEGIN:VALARM
TRIGGER:-PT2H
ACTION:DISPLAY
DESCRIPTION:Amazon Onsite 2小时后开始
END:VALARM
END:VEVENT

END:VCALENDAR
```

## Google Calendar集成

### 生成导入链接
```markdown
## 🔗 Google Calendar Import

### 方法 1: Web界面导入

1. 点击以下链接（会打开Google Calendar）:
   [一键导入所有面试到Google Calendar]

2. 或者手动步骤:
   - 打开 [Google Calendar](https://calendar.google.com)
   - 点击设置齿轮 → "导入与导出"
   - 选择文件: `exports/calendar/interviews.ics`
   - 选择目标日历
   - 点击"导入"

### 方法 2: API链接生成

Google Calendar导入链接:
```
https://calendar.google.com/calendar/render?action=TEMPLATE&text=Google+Interview+Round+1&dates=20240120T140000Z/20240120T150000Z&details=Phone+Screen+with+Google&location=Zoom&trp=false
```

URL编码的参数:
- `text`: 事件标题
- `dates`: 开始时间/结束时间 (格式: YYYYMMDDTHHmmssZ/YYYYMMDDTHHmmssZ)
- `details`: 事件描述
- `location`: 地点
- `trp`: 是否显示忙碌时间

### 方法 3: 批量导入

对于多个面试，使用iCal文件:
1. 运行 `/calendar/sync export`
2. 下载生成的 `interviews.ics` 文件
3. 在Google Calendar中选择"导入"
4. 选择 `interviews.ics` 文件
5. 所有事件将被导入

### 方法 4: 订阅（自动同步）

订阅iCal feed（自动更新）:
```
https://your-domain.com/interviews-feed.ics
```

在Google Calendar中:
1. 添加日历 → "从URL添加"
2. 粘贴上述URL
3. 点击"添加日历"

好处:
  ✅ 自动同步（当有新面试时）
  ✅ 双向同步（在Google Calendar中修改会同步回来）
  ✅ 实时更新
```

## 其他日历系统

### Apple Calendar (macOS/iOS)
```bash
# 双击iCal文件自动打开
# 或
open interviews.ics
```

### Outlook
```bash
# 文件 → 打开 → 导入日历
# 选择 interviews.ics
```

### Thunderbird
```bash
# 事件与任务 → 导入 → 选择iCal文件
```

## 提醒设置

### 多级提醒系统
```markdown
## ⏰ Reminder Levels

### Level 1: 1周前提醒
触发: 面试前7天
内容: "下周有[公司名]面试，本周开始准备"
行动: 开始制定准备计划

示例:
```
BEGIN:VALARM
TRIGGER:-P1W
ACTION:DISPLAY
DESCRIPTION:下周有Google面试！本周开始准备
END:VALARM
```

### Level 2: 1天前提醒
触发: 面试前1天
内容: "明天有[公司名]面试，今天早休息"
行动: 轻松复习，早睡

示例:
```
BEGIN:VALARM
TRIGGER:-P1D
ACTION:DISPLAY
DESCRIPTION:明天Google面试！今天早休息，相信自己
END:VALARM
```

### Level 3: 2小时前提醒
触发: 面试前2小时
内容: "[公司名]面试2小时后开始"
行动: 准备环境，放松

示例:
```
BEGIN:VALARM
TRIGGER:-PT2H
ACTION:DISPLAY
DESCRIPTION:Google面试2小时后开始。放松，你可以的！
END:VALARM
```

### Level 4: 15分钟前提醒
触发: 面试前15分钟
内容: "[公司名]面试15分钟后开始，立即加入"
行动: 加入会议链接

示例:
```
BEGIN:VALARM
TRIGGER:-PT15M
ACTION:DISPLAY
DESCRIPTION:Google面试15分钟后！立即加入Zoom
END:VALARM
```
```

## 面试日程视图

### 日历视图
```markdown
## 📅 Interview Calendar - January 2024

### Week 3 (Jan 15-21)

Mon 15:  无
Tue 16:  无
Wed 17:  无
Thu 18:  无
Fri 19:  无
Sat 20:  无
Sun 21:  无

### Week 4 (Jan 22-28)

Mon 22:  🟡 10:00-10:45 AM - Stripe Phone Screen #1
Tue 23:  无
Wed 24:  🟢 2:00-2:45 PM - Google Phone Screen #2
Thu 25:  🔴 10:00 AM - 3:15 PM - Amazon Onsite (4轮)
Fri 26:  无
Sat 27:  无
Sun 28:  🟢 4:00-4:45 PM - Meta Behavioral Screen

图例:
  🔴 Critical (Onsite)
  🟡 Important (Phone Screen)
  🟢 Normal (Initial screen)

### 本周概览

即将到来（7天内）:

1. **Stripe Phone Screen #1**
   时间: Monday, Jan 22, 10:00-10:45 AM
   类型: Phone Screen
   准备:
     - [ ] Review Stripe's engineering blog
     - [ ] Practice 2 coding problems
     - [ ] Prepare STAR stories
     - [ ] Test Zoom/Chime connection

2. **Google Phone Screen #2**
   时间: Wednesday, Jan 24, 2:00-2:45 PM
   类型: Phone Screen (Distributed Systems focus)
   准备:
     - [ ] Review CAP theorem, consistency models
     - [ ] Practice system design problems
     - [ ] Prepare "Why Google" answer
     - [ ] 2 days advance: Start light prep

3. **Amazon Onsite**
   时间: Thursday, Jan 25, 10:00 AM - 3:15 PM
   类型: Virtual Onsite (4轮)
   轮次:
     - 10:00 System Design
     - 11:00 Coding
     - 13:00 Behavioral
     - 14:30 Leadership Principles
   准备:
     - [ ] Complete system design practice
     - [ ] 6 Amazon LP stories ready
     - [ ] Rest well Wednesday night
     - [ ] Have water, snacks ready
     - [ ] Test Amazon Chime connection
     - [ ] Quiet room prepared

4. **Meta Behavioral Screen**
   时间: Sunday, Jan 28, 4:00-4:45 PM
   类型: Behavioral Interview
   准备:
     - [ ] 5-7 STAR stories ready
     - [ ] Meta culture research
     - [ ] "Why Meta" answer
     - [ ] Practice behavioral questions
```

## 冲突检测

### 自动冲突检测
```markdown
## ⚠️ Calendar Conflict Detection

检测到冲突:

**冲突 1: 时间重叠**
  - Meta Phone Screen: Jan 28, 3:00-4:00 PM
  - Google Phone Screen: Jan 28, 3:30-4:15 PM
  - 重叠: 30分钟

  建议: 联系Google重新安排到 4:30 PM

**冲突 2: 准备时间不足**
  - Amazon Onsite: Jan 25, 10:00 AM
  - Stripe Onsite: Jan 26, 10:00 AM
  - 问题: 两个Onsite连续进行，准备时间不足

  建议:
    - 优先Amazon（更匹配）
    - 重新安排Stripe到下周
    - 或专注于Amazon，推迟Stripe

**冲突 3: 过于密集**
  - Week of Jan 22-28: 4 interviews
  - 问题: 可能导致疲劳，影响表现

  建议:
    - 考虑重新安排1个面试
    - 确保有休息时间
    - 优先重要面试
```

## 时区处理

### 多时区支持
```markdown
## 🌍 Time Zone Handling

### 自动时区转换

源时区: America/Los_Angeles (PST)
目标时区: Asia/Shanghai (CST)

转换示例:
  - Google面试: Jan 20, 2:00 PM PST → Jan 21, 6:00 AM CST
  - Amazon onsite: Jan 25, 10:00 AM PST → Jan 26, 2:00 AM CST

### 支持的时区
- America/Los_Angeles (PST/PDT)
- America/New_York (EST/EDT)
- Europe/London (GMT/BST)
- Asia/Shanghai (CST)
- Asia/Tokyo (JST)
- Asia/Singapore (SGT)
- Australia/Sydney (AEDT)
- UTC

### 时区自动检测
系统会自动:
1. 读取面试时区信息
2. 转换到你的本地时区
3. 在日历事件中标注原时区
4. 显示时差提醒

示例:
```
SUMMARY:Google Phone Screen #2 (2:00 PM PST = 6:00 AM CST+1)
```
```

## 面试前提醒内容

### 自动生成提醒内容
```markdown
## 🔔 Reminder Content Templates

### 1天前提醒
```
标题: ⏰ 面试提醒明天

明天你有[公司名]面试！

📅 面试详情:
- 时间: [时间]
- 类型: [类型]
- 时长: [时长]

🎯 今晚准备:
1. 轻松复习核心要点（不超过1小时）
2. 准备好面试环境（测试Zoom/Chime）
3. 选择安静明亮的房间
4. 准备水、纸笔
5. 早睡（保证7-8小时睡眠）

💡 心态:
- 你已经准备充分
- 这是展示自己的机会
- 面试官也是人，正常交流
- 深呼吸，相信自己

🌟 明天会成功的！加油！
```

### 2小时前提醒
```
标题: ⏰ 面试2小时提醒

[公司名]面试2小时后开始！

✅ 最后检查清单:
- [ ] 网络/Zoom/Chime连接正常
- [ ] 环境：安静、明亮、整洁
- [ ] 设备：充电、笔记本、笔
- [ ] 水和零食（如需）
- [ ] 简历准备（打印版或打开）
- [ ] 笔记：公司信息、问题列表

🎯 面试前30分钟:
- 最后浏览一下公司信息
- 复习3-5个关键要点
- 深呼吸，放松心态
- 提前10分钟加入会议

🌟 你准备好了！Go get it!
```

### 15分钟前提醒
```
标题: ⚡️ 立即加入面试

[公司名]面试15分钟后开始！

🚀 立即行动:
1. 停止其他事情
2. 打开面试链接
3. 检查音频视频
4. 加入会议（提前5-10分钟）
5. 自我介绍准备

💪 最后的话:
- 自信！你值得这个机会
- 微笑，友好
- 清晰表达
- 享受过程

🎉 Good luck! You got this!
```
```

## 导出选项

### 批量导出
```bash
# 导出所有面试
/calendar/sync export --all

# 导出本月面试
/calendar/sync export --month 2024-01

# 导出指定状态的面试
/calendar/sync export --status "confirmed,scheduled"

# 导出到特定目录
/calendar/sync export --output ~/Documents/interviews/

# 包含提醒（iCal ALARMS）
/calendar/sync export --with-alarms

# 只导出特定公司
/calendar/sync export --company google,amazon
```

### 导出格式选择
```bash
# iCal格式（默认）
/calendar/sync export --format ical

# CSV格式（Excel可打开）
/calendar/sync export --format csv

# JSON格式（程序化处理）
/calendar/sync export --format json

# Markdown格式（人类可读）
/calendar/sync export --format markdown

# HTML格式（网页）
/calendar/sync export --format html
```

## 与其他工具集成

### Notion日历
```markdown
## 📌 Notion Integration

1. 导出为CSV格式:
   ```bash
   /calendar/sync export --format csv --output interviews.csv
   ```

2. 在Notion中:
   - 创建新的数据库视图
   - 选择"Calendar view"
   - 导入CSV文件
   - 设置日期列为时间轴

3. 结果: 面试自动显示在Notion日历中
```

### Todoist集成
```markdown
## ✅ Todoist Integration

导出为任务列表:
```bash
/calendar/sync export --todoist
```

每个面试变成Todoist任务:
- 标题: 面试名称
- 截止日期: 面试时间
- 优先级: 根据公司重要性
- 标签: #interview #[公司名]
- 描述: 准备要点
```

### Slack提醒
```markdown
## 💬 Slack Reminders

发送提醒到Slack:
```bash
/calendar/sync slack --interview google-round1 --before "1 day, 2 hours"
```

Slack消息:
```
🔔 面试提醒

明天你有Google Phone Screen #2！

⏰ 时间: 2:00 PM PST
📋 类型: Distributed Systems focus

🎯 准备要点:
- [ ] Review CAP theorem
- [ ] Practice 1 system design problem
- [ ] Prepare "Why Google" answer

💪 加油！
```
```

## 自动同步工作流

### 定期同步
```bash
# 每天自动同步
/calendar/sync auto --daily

# 每周自动导出
/calendar/sync auto --weekly

# 有新面试时自动同步
/calendar/sync auto --on-add
```

### Webhook集成
```bash
# 设置webhook
/calendar/sync webhook --url https://your-server.com/interview-webhook

# 当有新面试时发送POST请求
# Body包含面试详细信息
```

## 文件存储

### 导出文件位置
```bash
# 默认位置
exports/calendar/
├── interviews.ics          # 所有面试（iCal格式）
├── interviews.csv          # 所有面试（CSV格式）
├── interviews.html         # 所有面试（HTML日历）
├── google-interviews.ics   # Google面试
├── amazon-interviews.ics   # Amazon面试
└── calendar-feeds/         # 订阅源
    ├── all-interviews.ics  # 完整feed
    ├── upcoming.ics        # 即将到来（30天）
    └── confirmed.ics       # 已确认的面试
```

## 相关命令

- `/interview/list` - 查看所有面试
- `/interview/add` - 添加新面试
- `/interview/update` - 更新面试信息
- `/company/schedule` - 查看公司面试安排
- `/analytics/dashboard` - 查看整体进度

---

**Pro Tip**: 定期同步日历，确保不会错过任何面试。建议每天检查一次日历，确认第二天的安排！ 📅✅
