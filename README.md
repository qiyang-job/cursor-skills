# Cursor Skills Collection

个人 Cursor AI 技能库，用于提升 AI 编码助手的输出质量和效率。

## 📚 Skills 目录

| Skill | 描述 | 用途 |
|-------|------|------|
| **premium-ui-experience** | 高端 UI/UX 设计质量控制 | 确保 AI 输出精致、专业的用户界面 |
| **project-context-keeper** | 项目上下文管理 | 管理长对话中的项目记忆和上下文 |
| **token-context-economics** | Token 经济学 | 优化上下文使用效率，减少 Token 消耗 |
| **vibe-coding-kickoff** | Vibe Coding 启动 | 新项目启动时的最佳实践和检查清单 |
| **web-to-design-md** | 网站设计提取 | 将网站转换为结构化设计文档 |

## 🚀 安装方法

### 方式1：个人使用（推荐）

```bash
# 克隆到 Cursor skills 目录
git clone https://github.com/liudengwang/cursor-skills.git ~/.cursor/skills/cursor-skills-collection

# 或者复制所有 skills
cp -r cursor-skills/* ~/.cursor/skills/
```

### 方式2：项目特定使用

```bash
# 在项目根目录创建 .cursor/skills
cd your-project
mkdir -p .cursor/skills

# 复制需要的 skill
cp -r /path/to/cursor-skills/web-to-design-md .cursor/skills/
```

## 📝 Skill 详情

### 1. premium-ui-experience
确保 AI 生成的 UI 具有专业品质：
- 设计一致性检查
- 视觉层次优化
- 交互细节打磨
- 反 AI 味模板化

### 2. project-context-keeper
管理复杂项目的长期记忆：
- 上下文文件维护
- 项目规则沉淀
- 会话摘要管理
- 经验复用机制

### 3. token-context-economics
优化 Token 使用效率：
- 智能上下文分层
- 最小阅读范围
- 搜索优先策略
- 验证检查点

### 4. vibe-coding-kickoff
新项目启动的标准化流程：
- 开工总则
- 启动检查清单
- 开发前置模板
- 收口决策框架

### 5. web-to-design-md
网站设计分析和提取：
- 色彩系统提取
- 字体层级分析
- 组件文档生成
- 设计预览创建

## 🔧 使用方式

安装后，在 Cursor 中 AI 会自动识别并使用这些 skills。你也可以主动触发：

```
"使用 vibe-coding-kickoff 帮我启动新项目"
"用 web-to-design-md 分析这个网站"
"启用 premium-ui-experience 提升界面质量"
```

## 📄 文件结构

```
cursor-skills/
├── README.md
├── premium-ui-experience/
│   ├── SKILL.md              # 主要技能定义
│   ├── 00-先读我.md
│   └── references/           # 参考资料
├── project-context-keeper/
│   └── ...
├── token-context-economics/
│   └── ...
├── vibe-coding-kickoff/
│   └── ...
└── web-to-design-md/
│   ├── SKILL.md
│   ├── DESIGN.template.md
│   ├── preview.template.html
│   └── EXTRACTION.md
```

## 🎯 最佳实践

1. **选择合适的 Skill**: 根据任务类型选择最相关的 skill
2. **阅读先读我**: 每个 skill 都有 `00-先读我.md`，先了解设计意图
3. **参考资料**: `references/` 目录包含详细的指导文档
4. **反馈迭代**: 根据使用效果调整 skill 参数

## 📖 参考资源

- [Cursor Skills 官方文档](https://cursor.com/skills)
- [创建 Custom Skills 指南](https://github.com/cursor-ai/skills-guide)

## 🤝 贡献

这些 skills 是基于实际项目经验沉淀而成。如果你有改进建议：
1. Fork 本仓库
2. 创建 feature 分支
3. 提交 Pull Request

## 📝 License

MIT License - 自由使用和修改

---

**创建者**: [你的名字]
**更新时间**: 2026-04-22
