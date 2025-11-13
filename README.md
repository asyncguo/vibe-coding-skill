# 🚀 Vibe Coding Skill

本仓库用于存储和分享 Claude Code、Codex 等 AI Agent 的通用 Skill，实现多种自动化及 AI 编程能力，支持社区持续贡献与应用。

## ✨ 特性

- **📦 即用即插**：所有 Skill 均可直接导入使用，无需额外配置
- **🎯 场景丰富**：覆盖代码审查、需求分析、架构设计等多种场景
- **🌍 社区驱动**：欢迎社区贡献，共同构建强大的 AI 编程能力库
- **🔧 易于扩展**：清晰的结构设计，方便贡献者添加新的 Skill
- **📚 完善文档**：每个 Skill 都配有详细的使用说明和示例

## 🚦 快速开始

### 安装使用

1. **克隆仓库**
```bash
git clone https://github.com/asyncguo/vibe-coding-skill.git
cd vibe-coding-skill
```

2. **复制命令到 Claude Code 配置目录**

```bash
# macOS/Linux
cp claude-code/commands/*.md ~/.claude/commands/

# Windows PowerShell
Copy-Item claude-code\commands\*.md "$env:USERPROFILE\.claude\commands\"
```

如果 `.claude/commands` 目录不存在，先创建它：
```bash
# macOS/Linux
mkdir -p ~/.claude/commands

# Windows PowerShell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\commands"
```

3. **验证安装**

在任意项目中打开 Claude Code，输入 `/` 查看可用命令，应该能看到：
- `/reflect` - 代码反思与批判性分析
- `/spec` - 需求规范模式

4. **使用示例**
```bash
# 使用反思命令分析代码
/reflect src/main.ts

# 使用需求规范命令
/spec 用户登录功能
```

## 📂 项目结构

```
vibe-coding-skill/
├── claude-code/              # Claude Code 专用 Skills
│   └── commands/             # 命令/Slash Commands
│       ├── reflect.md        # 代码反思与批判性分析
│       └── spec.md           # 需求规范模式
├── skills/                   # 通用 Skill 库（规划中）
├── examples/                 # 使用示例和测试脚本（规划中）
├── docs/                     # 文档和开发指南（规划中）
├── LICENSE                   # MIT 许可证
└── README.md                 # 项目说明文档
```

## 🎨 现有 Skills

### 1. Code Reflection (`/reflect`)

**功能**：对代码进行深度、客观、严格的批判性分析

**适用场景**：
- 代码审查（Code Review）
- 重构前的代码质量评估
- 架构设计分析
- 性能和安全问题排查

**特点**：
- 🎯 自适应分析深度（根据代码类型和规模）
- 🔍 多维度评估（架构、性能、安全、可维护性等）
- 📊 结构化输出（Critical/Significant/Improvement 分级）
- ✅ 客观诚实（既指出问题，也认可优点）

**使用示例**：
```bash
# 分析特定文件
/reflect src/auth/login.ts

# 分析多个文件
/reflect src/components/Button.tsx src/hooks/useAuth.ts

# 分析最近修改的文件
/reflect
```

### 2. Requirements Specification (`/spec`)

**功能**：定义需求规范，从产品和用户视角明确「要构建什么」

**适用场景**：
- 新功能开发前的需求明确
- 产品需求文档（PRD）编写
- 技术方案设计前的需求澄清
- 跨团队协作的需求对齐

**特点**：
- 📋 完整的需求框架（用户故事、功能需求、非功能需求等）
- 🎚️ 分级详细度（简单/标准/复杂功能适配不同模板）
- ✅ 可测试性（每个需求都有明确的验收标准）
- 🔗 可追溯性（唯一 ID 标识每个需求）

**使用示例**：
```bash
# 为新功能编写需求规范
/spec 用户密码重置功能

# 为复杂特性编写完整规范
/spec 多租户权限管理系统
```

## 🛠️ 如何贡献

我们欢迎社区贡献新的 Skill 或改进现有内容！

### 贡献流程

1. **Fork 本仓库**

2. **创建特性分支**
```bash
git checkout -b feature/new-skill
```

3. **添加你的 Skill**
   - 将 Skill 文件放置在对应目录
   - 遵循现有的文件命名和结构规范
   - 编写清晰的使用说明和示例

4. **提交更改**
```bash
git add .
git commit -m "feat: add new skill for XXX"
git push origin feature/new-skill
```

5. **创建 Pull Request**
   - 详细描述你的 Skill 功能和使用场景
   - 如有必要，附上使用示例和效果截图

### Skill 开发规范

#### 对于 Claude Code Commands

命令文件应包含以下部分：

1. **Front Matter（元数据）**：
```yaml
---
description: 简短描述命令功能
argument-hint: <参数提示>
---
```

2. **功能说明**：清晰描述命令的用途和目标

3. **使用指南**：说明何时使用、如何使用

4. **核心原则**：列出命令执行时遵循的原则

5. **框架/模板**：提供结构化的执行框架

6. **示例**：提供具体的使用示例

#### 文件命名规范

- 使用小写字母和连字符：`my-skill.md`
- 名称应简洁且具有描述性
- 避免使用特殊字符和空格

### 贡献示例

#### 好的贡献示例 ✅

```markdown
---
description: API 接口设计审查
argument-hint: <API endpoint path>
---

# API Design Review

清晰的功能描述...

## 核心原则
1. RESTful 设计规范
2. 安全性检查
...

## 使用示例
/api-review /api/users
```

#### 不推荐的示例 ❌

- 缺少文档说明
- 没有使用示例
- 功能描述不清晰
- 未遵循项目结构

## 📝 待办事项与规划

- [ ] 添加更多编程场景的 Skill
  - [ ] 测试用例生成
  - [ ] 文档生成
  - [ ] Bug 根因分析
  - [ ] 性能优化建议
- [ ] 支持更多 AI Agent（Cursor、Copilot 等）
- [ ] 建立 Skill 评级和推荐系统
- [ ] 添加交互式 Skill 配置工具
- [ ] 构建在线 Skill 市场

## 🤝 社区

- **讨论**：使用 [GitHub Discussions](https://github.com/asyncguo/vibe-coding-skill/discussions) 进行交流
- **问题反馈**：通过 [GitHub Issues](https://github.com/asyncguo/vibe-coding-skill/issues) 报告问题
- **功能建议**：欢迎在 Issues 中提出新的 Skill 想法

## 📄 许可证

本项目采用 [MIT License](LICENSE) 开源协议。

## 🙏 致谢

感谢所有为本项目做出贡献的开发者！

---

**Built with ❤️ by the community**
