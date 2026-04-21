---
name: project-context-keeper
description: 当项目进入多轮对话、跨文件开发、暂停后恢复、多人或多 agent 协作，或需要让 AI 在干活时持续记住项目全貌、关键规则、近期状态与历史教训时使用。适用于“先同步项目上下文再继续”“恢复昨天的开发状态”“做完后更新交接与记忆文件”“避免重复犯同样的问题”等场景。
user-invocable: true
---

# Project Context Keeper

## Skill Goal

把“AI 容易遗忘项目上下文”转化成一套可维护、可恢复、可交接、可压缩的项目记忆系统。

不要把目标定义成“保存所有聊天原文”。

要做的是：

- 沉淀长期有效的项目事实
- 维护当前阶段的真实状态
- 记录关键决策与原因
- 保存可接力的交接摘要
- 沉淀稳定规则与复发问题教训
- 用短快照降低每次恢复成本

## Use This Skill When

在以下场景优先启用本 skill：

- 进入多轮开发，需要持续保留项目全貌
- 暂停一天或几天后，需要快速恢复开发状态
- 多个 agent / 多个人会接力推进同一项目
- 项目开始变复杂，需要先同步结构、状态、规则再动手
- 一轮开发结束后，需要沉淀交接、变更、经验教训
- 已经出现“昨天聊过今天又忘了”或“同样错误重复发生”的迹象

## Do Not Use This Skill When

以下场景不要强行启用：

- 只是一次性的单文件小修
- 只是通用知识问答，与当前项目无关
- 当前任务没有长期记忆价值

## Core Principle

优先维护 **结构化项目状态**，不要维护 **原始聊天仓库**。

始终区分：

- **稳定事实**：项目目标、边界、架构、约束
- **当前状态**：这轮做到哪、当前卡在哪、下一步是什么
- **历史决策**：为什么这么做、放弃了什么
- **稳定规则**：以后继续做都要遵守什么
- **经验教训**：哪些坑已经踩过，不应再次重复

## Context Pack v2-lite Contract

建议在项目根目录维护 `.ai-context/`，至少包含：

- `00-current-context.md`：超轻量恢复快照，优先第一读
- `00-project-overview.md`：项目目标、范围、非目标、硬约束
- `01-architecture-map.md`：主模块、主链路、关键依赖
- `02-current-state.md`：当前阶段、当前进展、当前风险、下一步
- `03-decision-log.md`：关键决策、原因、替代方案、影响范围
- `04-session-handoff.md`：本轮交接摘要，面向下一位继续者
- `05-open-questions.md`：未决问题、阻塞、待确认边界
- `06-change-log.md`：重要变更、验证方式、验证结果、遗留风险
- `07-conventions.md`：项目稳定规则、协作约束、质量要求
- `08-lessons-learned.md`：失败经验、复发问题、纠正规则
- `archive/`：超出长度预算后的归档区

## Default Read Order

开始工作时，按以下顺序读取并决定是否继续深读：

### Step 1. 先读快速快照

优先读取：

1. `.ai-context/00-current-context.md`

先用这份文件回答：

- 项目现在一句话是什么状态
- 当前主任务是什么
- 当前阻塞是什么
- 下一步最该做什么
- 这轮还需要继续读哪些文件

### Step 2. 再读稳定事实

如果需要理解项目全貌，再读取：

1. `.ai-context/00-project-overview.md`
2. `.ai-context/01-architecture-map.md`
3. `.ai-context/07-conventions.md`

### Step 3. 再读当前工作状态

如果需要恢复当前推进面，再读取：

1. `.ai-context/02-current-state.md`
2. `.ai-context/04-session-handoff.md`
3. `.ai-context/05-open-questions.md`
4. `.ai-context/06-change-log.md`

### Step 4. 按需读历史决策与经验

只有在任务涉及方案判断、旧坑复现、规则冲突时，再读取：

1. `.ai-context/03-decision-log.md`
2. `.ai-context/08-lessons-learned.md`

### Step 5. 与仓库事实交叉核对

必须用当前真实代码、文档、配置、用户请求交叉核对记忆文件。

不要把 `.ai-context/` 当成永远正确的单一现实；它是高价值摘要，不是代码事实本身。

## Default Working Workflow

### 1. 先恢复项目快照

在正式分析或改代码前，先输出：

- 当前项目目标
- 当前系统主链路 / 架构概览
- 当前主任务
- 最近关键变更
- 当前阻塞 / 未决问题
- 当前应遵守的关键规则
- 这轮最合理下一步

### 2. 再开始具体工作

在项目快照已清晰后，再进入分析、编码、调试或方案判断。

### 3. 在关键节点持续更新记忆包

以下场景必须更新至少一部分 `.ai-context/`：

- 完成一轮重要分析后
- 做出关键技术 / 产品决策后
- 完成一批重要代码改动后
- 跑完关键验证后
- 用户纠正了明显错误后
- 准备暂停当前会话时
- 准备切换给另一个 agent / 另一个人时

### 4. 结束前写交接与快照

会话结束前，至少更新：

- `.ai-context/00-current-context.md`
- `.ai-context/02-current-state.md`
- `.ai-context/04-session-handoff.md`

如果这轮改动影响后续判断，再同步更新：

- `.ai-context/03-decision-log.md`
- `.ai-context/05-open-questions.md`
- `.ai-context/06-change-log.md`
- `.ai-context/07-conventions.md`
- `.ai-context/08-lessons-learned.md`

## Required File Semantics

### `00-current-context.md`

保持极短，作为冷启动入口。

只保留：

- 当前一句话状态
- 当前主任务
- 当前阻塞
- 下一步
- 必读文件

### `07-conventions.md`

只记录 **稳定、重复有效、需要长期遵守** 的项目规则。

不要把一次性的会话决定写进这里。

### `08-lessons-learned.md`

只记录：

- 用户明确纠正过的错误
- 已经重复出现两次以上的问题
- 后续极可能再次踩中的坑
- 已经形成清晰纠正规则的失败经验

不要把所有错误都记成 lesson。

## Verification-First Rule

没有验证过，不要写成“已完成”。

更新 `02-current-state.md` 或 `06-change-log.md` 时，明确区分：

- 已思考 / 已准备
- 已执行
- 已验证
- 仍待验证

如果只是推断、尚未运行、尚未核对，不要伪装成结果。

## Compression Rule

把会话压缩成“未来继续工作真正需要的信息”。

优先保留：

- 仍成立的事实
- 会影响后续的决策
- 当前真实状态
- 当前主阻塞
- 下一步动作
- 已验证结论
- 稳定规则与教训

优先丢弃：

- 寒暄
- 已失效的临时讨论
- 对后续没有价值的细碎过程
- 冗长原始聊天转录

## Archive Rule

避免上下文文件不断膨胀。

默认遵守：

- `00-current-context.md` 只保留当前快照
- `04-session-handoff.md` 只保留最近一轮摘要
- `05-open-questions.md` 只保留仍未解决的问题
- `06-change-log.md` 保留最近重要条目，旧内容移入 `archive/`
- `08-lessons-learned.md` 只保留仍活跃的高价值教训，过时内容移入 `archive/`

详细规则见 `references/09-归档与体积控制规则.md`。

## Required Output Contract

触发本 skill 时，默认先输出：

1. **当前项目快照**
2. **已读取的上下文来源**
3. **当前最可信的项目状态**
4. **当前需要遵守的关键规则**
5. **可能复发的关键风险 / 教训**
6. **仍不确定的地方**
7. **建议下一步**
8. **本轮需要更新哪些记忆文件**

## Initialization Rule

如果项目里还没有 `.ai-context/`，优先使用 `scripts/init_context_pack.py` 初始化 v2-lite 记忆包。

初始化后，先补最小必要信息：

- `00-current-context.md`
- `00-project-overview.md`
- `01-architecture-map.md`
- `02-current-state.md`
- `07-conventions.md`

再逐步补齐其它文件。

## Anti-Goals

不要把这个 skill 变成：

- 原始聊天存档系统
- 超长流水账生成器
- 每个文件都重复同样内容的系统
- 只会写文档、不会帮助继续推进工作的秘书型噪音工具

## Success Criteria

如果本 skill 运作正确，应出现这些变化：

- 恢复开发更快
- AI 更少忘记项目主线
- AI 更容易先读对文件，而不是全量乱读
- 稳定规则更少被反复违反
- 同类错误更少重复出现
- 多 agent / 多人接力时断层更少

## References

按需读取以下文件：

- `00-先读我.md`：这个 skill 包的使用方式与升级说明
- `references/01-上下文文件规范.md`：v2-lite 记忆包结构与文件职责
- `references/02-更新与压缩规则.md`：什么时候更新、如何压缩、如何保持文件短
- `references/03-交接与滚动摘要规范.md`：如何写交接摘要
- `references/04-反模式与遗忘风险.md`：哪些做法会导致上下文失效
- `references/05-效果评估与验收.md`：如何评估这套机制是否真的有效
- `references/06-GitHub最佳实践对齐评估.md`：当前版本与公开最佳实践的对照结果
- `references/07-项目规则层规范.md`：如何维护 `07-conventions.md`
- `references/08-经验沉淀与复发问题.md`：如何维护 `08-lessons-learned.md`
- `references/09-归档与体积控制规则.md`：如何避免记忆文件膨胀
