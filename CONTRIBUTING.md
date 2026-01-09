# 贡献指南

感谢您考虑为面试和求职管理系统做出贡献！

## 🤝 如何贡献

我们欢迎各种形式的贡献，包括但不限于：

- 🐛 报告 Bug
- 💡 提出新功能
- 📝 改进文档
- 🔧 提交代码修复
- ✨ 开发新功能
- 🌍 帮助国际化

## 📋 报告 Bug

在创建 Bug 报告前，请先检查：

1. 是否已有相同的 Issue
2. 问题是否在最新版本中存在
3. 提供尽可能详细的信息

### Bug 报告模板

```markdown
**问题描述**
简要描述问题是什么

**复现步骤**
1. 执行命令 '...'
2. 点击 '....'
3. 滚动到 '....'
4. 看到错误

**期望行为**
描述您期望发生什么

**截图**
如果适用，添加截图来帮助解释问题

**环境信息**
- 操作系统: [例如 Windows 11, macOS 14, Ubuntu 22.04]
- Claude Code 版本: [例如 1.0.0]
- 项目版本: [例如 1.0.0]

**附加信息**
添加其他有助于理解问题的信息
```

## 💡 功能请求

### 功能请求模板

```markdown
**您的功能请求是否与问题相关？**
描述您遇到的问题，例如：每次需要手动...让我感到困扰

**描述您想要的解决方案**
清晰简洁地描述您想要发生什么

**描述您考虑过的替代方案**
描述您考虑过的替代功能或解决方案

**附加信息**
添加其他关于功能请求的信息或截图
```

## 🔧 开发流程

### 准备工作

1. **Fork** 本仓库
2. **克隆** 您的 fork：
   ```bash
   git clone https://github.com/yourusername/claude-code-interview.git
   ```
3. **安装依赖**：
   ```bash
   # 确保已安装 Claude Code
   npm install -g @anthropic-ai/claude-code
   ```

### 创建分支

为您的功能或修复创建一个分支：

```bash
git checkout -b feature/AmazingFeature
# 或
git checkout -b fix/AnnoyingBug
```

### 进行更改

1. 遵循现有代码风格
2. 添加必要的注释
3. 更新相关文档
4. 测试您的更改

### 提交更改

使用清晰的提交消息：

```bash
git commit -m "Add some AmazingFeature"
```

### 推送到分支

```bash
git push origin feature/AmazingFeature
```

### 开启 Pull Request

1. 前往 GitHub 上的原始仓库
2. 点击 "New Pull Request"
3. 选择您的功能分支
4. 填写 PR 描述模板
5. 等待代码审查

## 📝 Pull Request 模板

```markdown
## 描述
简要描述您的更改

## 类型
- [ ] Bug 修复
- [ ] 新功能
- [ ] 代码重构
- [ ] 文档更新
- [ ] 性能优化
- [ ] 其他

## 相关 Issue
关闭 #(issue number)

## 更改内容
列出您所做的具体更改

## 测试
描述您如何测试这些更改

## 截图
如果适用，添加截图

## 检查清单
- [ ] 我的代码遵循项目风格
- [ ] 我已更新相关文档
- [ ] 我已测试更改
- [ ] 新功能不破坏现有功能
```

## 🎨 代码风格

### 命名规范

- 文件名：使用小写字母和连字符
- JSON 字段：使用下划线或驼峰命名
- 命令：使用斜杠命令格式 `/category:action`

### 文档规范

- 使用清晰的中文描述
- 添加使用示例
- 更新 README 和相关文档

## 🧪 测试

在提交 PR 前，请确保：

1. ✅ 所有斜杠命令正常工作
2. ✅ JSON 数据模型格式正确
3. ✅ Skills 和 Subagents 正常加载
4. ✅ 文档已更新

## 📧 联系方式

如有任何问题，请通过以下方式联系：

- 📧 Email: your.email@example.com
- 💬 GitHub Discussions: [ discussions link ]

## 🌟 贡献者

感谢所有贡献者！

<a href="https://github.com/yourusername/claude-code-interview/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=yourusername/claude-code-interview" />
</a>

---

**再次感谢您的贡献！** 🎉
