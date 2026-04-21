# [Site Name] Design System

## 概述 / Overview

**网站类型**: [SaaS / Portfolio / E-commerce / Blog / Dashboard]
**整体风格**: [极简主义 / 编辑风格 / 科技感 / 有机现代 / 粗野主义]
**核心特征**: [3-5 个关键词描述]

**提取来源**: [URL]
**提取日期**: [Date]
**提取工具**: [agent-browser / WebFetch]
**置信度**: [High / Medium / Low]

---

## 一、色 / Color — 色彩系统

### 1.1 品牌色 / Brand Colors

| 角色 | 名称 | Hex | RGB | CSS变量 | 使用场景 |
|------|------|-----|-----|---------|----------|
| 主色 | Primary | `#3B82F6` | rgb(59,130,246) | --color-primary | CTA按钮、链接、强调 |
| 主色悬停 | Primary Hover | `#2563EB` | rgb(37,99,235) | --color-primary-hover | 悬停状态 |
| 辅助色 | Secondary | `#10B981` | rgb(16,185,129) | --color-secondary | 成功状态、替代强调 |
| 强调色 | Accent | `#F59E0B` | rgb(245,158,11) | --color-accent | 特殊高亮 |

### 1.2 中性色阶 / Neutral Scale

| 角色 | 名称 | Hex | RGB | 使用场景 |
|------|------|-----|-----|----------|
| 背景 | Background | `#FFFFFF` | rgb(255,255,255) | 页面背景 |
| 表面 | Surface | `#F9FAFB` | rgb(249,250,251) | 卡片、面板 |
| 表面上层 | Surface Elevated | `#FFFFFF` | rgb(255,255,255) | 弹出层、下拉 |
| 边框 | Border | `#E5E7EB` | rgb(229,231,235) | 分隔线、边框 |
| 边框悬停 | Border Hover | `#D1D5DB` | rgb(209,213,219) | 交互边框 |
| 文字主色 | Text Primary | `#111827` | rgb(17,24,39) | 标题、正文 |
| 文字次级 | Text Secondary | `#6B7280` | rgb(107,114,128) | 描述、元数据 |
| 文字第三 | Text Tertiary | `#9CA3AF` | rgb(156,163,175) | 占位符、禁用 |
| 反色 | Text Inverse | `#FFFFFF` | rgb(255,255,255) | 深色背景上的文字 |

### 1.3 语义色 / Semantic Colors

| 角色 | 名称 | Hex | 使用场景 |
|------|------|-----|----------|
| 成功 | Success | `#10B981` | 成功消息、完成状态 |
| 警告 | Warning | `#F59E0B` | 警告、需注意 |
| 错误 | Error | `#EF4444` | 错误、失败状态 |
| 信息 | Info | `#3B82F6` | 提示信息 |

### 1.4 渐变 / Gradients

```css
--gradient-primary: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
--gradient-bg: linear-gradient(180deg, #f8f9fa 0%, #ffffff 100%);
--gradient-accent: linear-gradient(90deg, #f093fb 0%, #f5576c 100%);
```

### 1.5 暗色模式 / Dark Mode

| 角色 | Hex | 说明 |
|------|-----|------|
| 背景 | `#0F172A` | 深蓝灰背景 |
| 表面 | `#1E293B` | 卡片背景 |
| 文字主色 | `#F8FAFC` | 主要文字 |
| 文字次级 | `#94A3B8` | 次要文字 |

---

## 二、形 / Form — 形状语言

### 2.1 圆角系统 / Border Radius

| Token | 值 | 像素 | 使用场景 |
|-------|-----|------|----------|
| none | 0 | 0px | 锐利角 |
| xs | 2px | 2px | 极小元素 |
| sm | 0.25rem | 4px | 输入框、标签 |
| md | 0.5rem | 8px | 按钮、小卡片 |
| lg | 0.75rem | 12px | 卡片、容器 |
| xl | 1rem | 16px | 大容器、模态框 |
| 2xl | 1.5rem | 24px | 特殊区块 |
| full | 9999px | — | 胶囊、头像 |

### 2.2 阴影系统 / Shadow Scale

| Level | CSS | 使用场景 |
|-------|-----|----------|
| none | none | 扁平元素 |
| xs | `0 1px 2px rgba(0,0,0,0.05)` | 微小提升 |
| sm | `0 1px 3px rgba(0,0,0,0.1)` | 输入框、标签 |
| md | `0 4px 6px -1px rgba(0,0,0,0.1)` | 卡片、按钮 |
| lg | `0 10px 15px -3px rgba(0,0,0,0.1)` | 下拉、弹出 |
| xl | `0 20px 25px -5px rgba(0,0,0,0.1)` | 模态框 |

### 2.3 Z-Index 层级

| 层级 | 值 | 使用场景 |
|------|-----|----------|
| Base | 0 | 默认内容 |
| Dropdown | 10 | 下拉菜单 |
| Sticky | 20 | 粘性头部 |
| Fixed | 30 | 固定元素 |
| Overlay | 40 | 遮罩层 |
| Modal | 50 | 模态框 |
| Toast | 60 | 通知提示 |
| Tooltip | 70 | 工具提示 |

---

## 三、字 / Typography — 字体系统

### 3.1 字体族 / Font Families

| 类型 | 字体族 | Fallback |
|------|--------|----------|
| 主字体 | Inter | system-ui, sans-serif |
| 展示字体 | Playfair Display | Georgia, serif |
| 等宽字体 | JetBrains Mono | Fira Code, monospace |

### 3.2 字号层级 / Type Scale

| 层级 | 尺寸 | 字重 | 行高 | 字间距 | 用途 |
|------|------|------|------|--------|------|
| Display XL | 6rem (96px) | 700 | 1 | -0.02em | 超大标题 |
| Display | 4.5rem (72px) | 700 | 1.1 | -0.02em | 主标题 |
| H1 | 3rem (48px) | 700 | 1.2 | -0.01em | 页面标题 |
| H2 | 2.25rem (36px) | 600 | 1.2 | -0.01em | 区块标题 |
| H3 | 1.5rem (24px) | 600 | 1.3 | 0 | 子标题 |
| H4 | 1.25rem (20px) | 600 | 1.4 | 0 | 卡片标题 |
| Large | 1.125rem (18px) | 400 | 1.6 | 0 | 引导文字 |
| Body | 1rem (16px) | 400 | 1.6 | 0 | 正文 |
| Small | 0.875rem (14px) | 500 | 1.5 | 0.01em | 小字、标签 |
| Tiny | 0.75rem (12px) | 500 | 1.4 | 0.02em | 元数据 |

---

## 四、构 / Structure — 布局结构

### 4.1 间距系统 / Spacing (4px base)

| Token | 值 | 像素 | 使用场景 |
|-------|-----|------|----------|
| 0 | 0 | 0 | 无间距 |
| 1 | 0.25rem | 4px | 基础单位 |
| 2 | 0.5rem | 8px | 小间隙 |
| 3 | 0.75rem | 12px | 标准间隙 |
| 4 | 1rem | 16px | 组件内边距 |
| 6 | 1.5rem | 24px | 大间隙 |
| 8 | 2rem | 32px | 区块间隙 |
| 12 | 3rem | 48px | 区块内边距 |
| 16 | 4rem | 64px | 大区块内边距 |
| 20 | 5rem | 80px | Hero间距 |
| 24 | 6rem | 96px | 超大间距 |

### 4.2 容器系统 / Container

| 尺寸 | 最大宽度 | 内边距 |
|------|----------|--------|
| sm | 640px | 1rem |
| md | 768px | 1.5rem |
| lg | 1024px | 2rem |
| xl | 1280px | 3rem |
| 2xl | 1536px | 4rem |

### 4.3 响应式断点 / Breakpoints

| 断点 | 宽度 | 调整 |
|------|------|------|
| sm | < 640px | 单列，堆叠布局 |
| md | 640-768px | 2列，紧凑间距 |
| lg | 768-1024px | 3-4列，标准间距 |
| xl | 1024-1280px | 4列，宽松间距 |
| 2xl | > 1280px | 完整布局 |

---

## 五、质 / Quality — 质感与品质

### 5.1 背景质感

| 类型 | 说明 | 使用场景 |
|------|------|----------|
| 纯色 | 单一颜色 | 标准背景 |
| 渐变 | 线性渐变 | Hero区域、强调区块 |
| 纹理 | 细微噪点/图案 | 特殊质感 |
| 毛玻璃 | backdrop-filter: blur | 悬浮面板 |

### 5.2 透明度使用

| 透明度 | 使用场景 |
|--------|----------|
| 100% | 主要文字、重要元素 |
| 80% | 次级文字 |
| 60% | 禁用状态、占位符 |
| 40% | 背景装饰、水印 |
| 20% | 分割线、边框 |

---

## 六、动 / Motion — 动效系统

### 6.1 过渡时长

| 类型 | 时长 | 使用场景 |
|------|------|----------|
| instant | 0ms | 立即响应 |
| fast | 100ms | 微交互 |
| normal | 200ms | 标准过渡 |
| slow | 300ms | 明显动画 |
| slower | 400ms | 大型元素 |

### 6.2 缓动函数

| 名称 | CSS | 使用场景 |
|------|-----|----------|
| ease | ease | 标准过渡 |
| ease-in | ease-in | 进入动画 |
| ease-out | ease-out | 退出动画 |
| spring | cubic-bezier(0.34, 1.56, 0.64, 1) | 弹性效果 |
| smooth | cubic-bezier(0.4, 0, 0.2, 1) | Material Design |
| expo | cubic-bezier(0.16, 1, 0.3, 1) | 流畅减速 |

### 6.3 交互动画

**按钮悬停**
- 时长: 200ms
- 缓动: ease-out
- 效果: 背景色变化 + translateY(-2px)

**卡片悬停**
- 时长: 300ms
- 缓动: ease-out
- 效果: 阴影增强 + scale(1.02)

**滚动显示**
- 触发: 元素进入视口20%
- 动画: 淡入 + 上移30px
- 时长: 600ms
- 缓动: cubic-bezier(0.16, 1, 0.3, 1)
- 交错: 100ms

---

## 七、组件规范

### 按钮 / Button

**Primary**
```css
background: var(--color-primary);
color: white;
padding: 0.75rem 1.5rem;
border-radius: var(--radius-md);
font-weight: 600;
transition: all 200ms ease-out;
/* Hover */
background: var(--color-primary-hover);
transform: translateY(-2px);
```

### 卡片 / Card

```css
background: var(--color-surface);
border: 1px solid var(--color-border);
border-radius: var(--radius-lg);
padding: var(--space-6);
box-shadow: var(--shadow-sm);
transition: all 300ms ease-out;
/* Hover */
box-shadow: var(--shadow-md);
transform: translateY(-4px);
```

---

## 八、AI 实现指南

### 快速构建模板

**Hero Section**
```
创建Hero区块:
- 背景: [颜色/渐变]
- 最小高度: 100vh
- 标题: Display XL尺寸，居中/左对齐
- 副标题: Large尺寸，60%宽度，次级色
- CTA按钮: Primary样式
- 内边距: space-20
```

---

**提取来源**: [URL]
**提取日期**: [YYYY-MM-DD]
**置信度**: [High/Medium/Low]
