---
name: web-to-design-md
description: Extract complete design systems from live websites using agent-browser to capture rendered styles, CSS variables, responsive behavior, and animations. Converts websites into structured DESIGN.md documents with companion HTML preview. Use when given website URLs and asked to analyze design, extract style guides, reverse-engineer UI with high fidelity, create design documentation, or capture visual language including colors, typography, spacing, structure, quality, and motion.
---

# Website to DESIGN.md — High Fidelity Design Extraction

Extract complete design systems from live websites, capturing **形色字构质动** (Color, Form, Typography, Structure, Quality, Motion) with maximum fidelity.

## Core Extraction Goals

| 维度 | 中文 | 提取内容 |
|------|------|----------|
| **Color** | 色 | 完整色彩系统（主色、辅助色、中性色、语义色、CSS变量） |
| **Form** | 形 | 形状语言（圆角、阴影、边框、层级） |
| **Typography** | 字 | 字体系统（字体族、字号层级、字重、行高、间距） |
| **Structure** | 构 | 布局结构（网格、间距系统、响应式断点） |
| **Quality** | 质 | 质感（纹理、渐变、透明度、材质感） |
| **Motion** | 动 | 动效系统（过渡、动画、交互反馈、时间函数） |

## When to Use

- "提取这个网站的设计" / "分析这个网页的样式"
- "创建 design.md" / "生成设计文档"
- "逆向这个 UI" / "复制这个网站的风格"
- 需要高保真还原，不只是大致风格

## Tool Priority

### 1. Primary: `agent-browser` (推荐)

**Capabilities:**
- ✅ 执行 JavaScript 获取实际渲染样式
- ✅ 提取 CSS 变量和计算样式
- ✅ 测试响应式断点（模拟不同设备）
- ✅ 捕捉交互状态（hover、active、focus）
- ✅ 记录动画 timing 和 easing
- ✅ 滚动触发动画分析

**Usage:**
```
agent-browser open [URL]
agent-browser eval "document.documentElement.outerHTML"
agent-browser eval "getComputedStyle(element)"
```

### 2. Fallback: `WebFetch`

当 `agent-browser` 不可用时，使用 `WebFetch` 获取静态 HTML 和 CSS，但会丢失：
- JavaScript 渲染的动态内容
- CSS 变量实际值
- 交互状态样式
- 响应式行为

## Extraction Workflow

### Phase 1: Browser Setup & Page Load

```
1. 检查 agent-browser 可用性
2. 打开目标 URL
3. 等待页面完全加载（包括 JS 渲染）
4. 滚动到页面底部触发所有懒加载内容
5. 截图保存页面全貌（可选）
```

### Phase 2: Core Design Token Extraction

执行 JavaScript 提取：**色**
```javascript
// 颜色提取
const colors = new Set();
document.querySelectorAll('*').forEach(el => {
  const styles = getComputedStyle(el);
  colors.add(styles.color);
  colors.add(styles.backgroundColor);
  colors.add(styles.borderColor);
});
// 提取 CSS 变量中的颜色
const cssVars = getComputedStyle(document.documentElement);
for (let prop of cssVars) {
  if (prop.startsWith('--color') || prop.startsWith('--bg')) {
    colors.add(cssVars.getPropertyValue(prop));
  }
}
```

执行 JavaScript 提取：**字**
```javascript
// 字体系统提取
const fonts = new Map();
document.querySelectorAll('h1, h2, h3, h4, h5, h6, p, span, button, a').forEach(el => {
  const styles = getComputedStyle(el);
  const key = `${styles.fontFamily}|${styles.fontSize}|${styles.fontWeight}`;
  fonts.set(key, {
    family: styles.fontFamily,
    size: styles.fontSize,
    weight: styles.fontWeight,
    lineHeight: styles.lineHeight,
    letterSpacing: styles.letterSpacing
  });
});
```

执行 JavaScript 提取：**构**（间距）
```javascript
// 间距系统分析
const spacings = new Set();
document.querySelectorAll('*').forEach(el => {
  const styles = getComputedStyle(el);
  spacings.add(styles.padding);
  spacings.add(styles.margin);
  spacings.add(styles.gap);
});
// 提取 CSS 变量中的间距
for (let prop of cssVars) {
  if (prop.startsWith('--space') || prop.startsWith('--gap')) {
    spacings.add(cssVars.getPropertyValue(prop));
  }
}
```

### Phase 3: Component & Interactive State Extraction

提取 **形** 和 **质**：
```javascript
// 提取圆角、阴影、边框
const components = document.querySelectorAll('button, .card, input, .btn');
components.forEach(el => {
  const styles = getComputedStyle(el);
  console.log({
    borderRadius: styles.borderRadius,
    boxShadow: styles.boxShadow,
    border: styles.border,
    background: styles.background
  });
});
```

捕捉 **动**：
```javascript
// 动画和过渡提取
const animatedElements = document.querySelectorAll('*');
animatedElements.forEach(el => {
  const styles = getComputedStyle(el);
  if (styles.animation !== 'none 0s ease 0s 1 normal none running' ||
      styles.transition !== 'all 0s ease 0s') {
    console.log({
      element: el.tagName,
      animation: styles.animation,
      transition: styles.transition
    });
  }
});
```

### Phase 4: Responsive Breakpoint Testing

```
1. 模拟桌面端 (1920x1080)
2. 模拟平板端 (768x1024)
3. 模拟移动端 (375x812)
4. 记录各断点下的布局变化
5. 提取响应式 CSS 规则
```

### Phase 5: Interaction State Testing

```
1. 模拟 hover 状态并提取样式变化
2. 模拟 active/pressed 状态
3. 模拟 focus 状态（可见时）
4. 记录 state 之间的 transition
```

### Phase 6: Documentation & Preview Generation

1. 整合所有提取数据
2. 按 **形色字构质动** 分类整理
3. 生成 DESIGN.md
4. 创建可视化 HTML 预览

## Quality Checklist

提取完成后验证：

### 色 (Color) ✅
- [ ] 主品牌色提取准确
- [ ] 中性色阶完整（至少 8 级）
- [ ] 语义色（成功、错误、警告）识别
- [ ] CSS 变量中的颜色值提取
- [ ] 渐变定义记录

### 形 (Form) ✅
- [ ] 圆角系统（sm、md、lg、xl）
- [ ] 阴影层级（z-index 对应 shadow）
- [ ] 边框样式（宽度、颜色、虚实）
- [ ] 形状语言（sharp vs rounded）

### 字 (Typography) ✅
- [ ] 字体族完整（包括 fallback）
- [ ] 字号层级（至少 6 级）
- [ ] 字重使用（400、500、600、700）
- [ ] 行高比例
- [ ] 字间距（letter-spacing）

### 构 (Structure) ✅
- [ ] 间距系统（base unit + scale）
- [ ] 网格定义（grid/flex）
- [ ] 容器宽度（max-width）
- [ ] 响应式断点（sm、md、lg、xl）
- [ ] 边距规范

### 质 (Quality) ✅
- [ ] 纹理/噪点（如有）
- [ ] 渐变模式
- [ ] 透明度使用
- [ ] 毛玻璃效果（backdrop-filter）
- [ ] 材质感（Material、Neumorphism 等）

### 动 (Motion) ✅
- [ ] 过渡时长（hover、focus 等）
- [ ] 缓动函数（easing）
- [ ] 动画关键帧
- [ ] 滚动触发动画
- [ ] 微交互（micro-interactions）

## Handling Extraction Gaps

如果某些值无法自动提取：

1. **标注为 [推断]**：基于可见模式合理推测
2. **请求用户补充**："这个 hover 色无法确定，你观察到的是什么？"
3. **使用行业标准**：参考 Tailwind、Material 等系统的默认值
4. **标注不确定性**：在文档中注明哪些是推断的

## Tool Installation (如果 agent-browser 不可用)

```bash
# 安装 agent-browser
curl -fsSL https://install.agent-browser.dev | sh

# 验证安装
agent-browser --version
```

## Output Contract

必须生成：
1. **DESIGN.md** — 完整设计系统文档
2. **DESIGN-preview.html** — 可视化设计板

DESIGN.md 必须包含 **形色字构质动** 六大章节。


## Extraction Process

### Step 1: Website Discovery

Identify what to extract:
- **Single page**: Extract one design.md
- **Multiple pages**: Extract shared system + page-specific notes
- **Multiple sites**: Extract each separately unless visual language is identical

### Step 2: Deep Analysis

Use WebFetch or browser tools to analyze:

**A. Visual Foundation**
- Color palette (primary, secondary, neutrals, accents)
- Typography (font families, sizes, weights, line heights)
- Spacing system (margins, padding, gaps)
- Layout (grid, container widths, breakpoints)

**B. Components**
- Buttons (variants, states, sizes)
- Cards and containers
- Forms and inputs
- Navigation patterns
- Hero sections
- Feature blocks

**C. Interactions & Motion**
- Hover states
- Scroll behaviors
- Animations (transitions, durations, easing)
- Micro-interactions

**D. Content Tone**
- Headline style and personality
- CTA phrasing patterns
- Voice and messaging approach

### Step 3: Documentation

Write DESIGN.md following the template structure.

## DESIGN.md Template

```markdown
# [Site Name] Design System

## 1. Visual Theme & Atmosphere

**Overall Feel**: [e.g., "Minimalist tech SaaS with bold typography"]
**Key Characteristics**:
- [Characteristic 1]
- [Characteristic 2]
- [Characteristic 3]

## 2. Color Palette

### Primary Colors
| Role | Hex | Usage |
|------|-----|-------|
| Primary | `#3B82F6` | CTAs, links, highlights |
| Secondary | `#10B981` | Success states, accents |

### Neutral Scale
| Role | Hex | Usage |
|------|-----|-------|
| Background | `#FFFFFF` | Page background |
| Surface | `#F9FAFB` | Cards, sections |
| Border | `#E5E7EB` | Dividers, outlines |
| Text Primary | `#111827` | Headlines, body |
| Text Secondary | `#6B7280` | Captions, meta |

### Dark Mode (if supported)
[Document inverted palette if applicable]

## 3. Typography

### Font Families
- **Primary**: Inter, system-ui, sans-serif
- **Monospace**: JetBrains Mono, monospace

### Type Scale
| Level | Size | Weight | Line Height | Letter Spacing | Usage |
|-------|------|--------|-------------|----------------|-------|
| H1 | 48px | 700 | 1.1 | -0.02em | Hero headlines |
| H2 | 36px | 600 | 1.2 | -0.01em | Section headers |
| H3 | 24px | 600 | 1.3 | 0 | Subsection headers |
| Body | 16px | 400 | 1.6 | 0 | Paragraph text |
| Small | 14px | 500 | 1.5 | 0.01em | Labels, captions |
| Tiny | 12px | 500 | 1.4 | 0.02em | Meta, timestamps |

## 4. Spacing System

### Base Unit: 4px

| Token | Value | Usage |
|-------|-------|-------|
| xs | 4px | Tight gaps |
| sm | 8px | Internal padding |
| md | 16px | Component padding |
| lg | 24px | Section gaps |
| xl | 32px | Major separations |
| 2xl | 48px | Section padding |
| 3xl | 64px | Hero spacing |

### Container
- Max width: 1200px
- Side padding: 24px (mobile), 48px (desktop)

## 5. Components

### Buttons

**Primary Button**
- Background: `#3B82F6`
- Text: `#FFFFFF`
- Padding: 12px 24px
- Border-radius: 8px
- Font-weight: 600
- Hover: darken 10%, scale(1.02)

**Secondary Button**
- Background: transparent
- Border: 1px solid `#E5E7EB`
- Text: `#111827`
- Hover: background `#F9FAFB`

### Cards

**Standard Card**
- Background: `#FFFFFF`
- Border: 1px solid `#E5E7EB`
- Border-radius: 12px
- Padding: 24px
- Shadow: `0 1px 3px rgba(0,0,0,0.1)`
- Hover: translateY(-4px), shadow increase

### Inputs

**Text Field**
- Height: 44px
- Padding: 12px 16px
- Border: 1px solid `#D1D5DB`
- Border-radius: 8px
- Focus: border `#3B82F6`, ring 2px

## 6. Layout Principles

### Grid System
- 12-column grid
- Gap: 24px
- Responsive: 4 col (mobile), 8 col (tablet), 12 col (desktop)

### Section Spacing
- Between sections: 80px (desktop), 48px (mobile)
- Section padding: 80px 0

## 7. Depth & Elevation

### Shadow Scale
| Level | Shadow | Usage |
|-------|--------|-------|
| sm | `0 1px 2px rgba(0,0,0,0.05)` | Inputs, small cards |
| md | `0 4px 6px rgba(0,0,0,0.1)` | Cards, dropdowns |
| lg | `0 10px 15px rgba(0,0,0,0.1)` | Modals, popovers |
| xl | `0 20px 25px rgba(0,0,0,0.15)` | Overlays |

### Border Radius Scale
| Token | Value | Usage |
|-------|-------|-------|
| sm | 4px | Inputs, tags |
| md | 8px | Buttons, small cards |
| lg | 12px | Cards, containers |
| xl | 16px | Modals, sections |
| full | 9999px | Pills, avatars |

## 8. Motion & Animation

### Transitions
| Property | Duration | Easing | Usage |
|----------|----------|--------|-------|
| Hover | 200ms | ease-out | Buttons, links |
| Expand | 300ms | cubic-bezier(0.4,0,0.2,1) | Accordions, menus |
| Slide | 400ms | cubic-bezier(0.16,1,0.3,1) | Page transitions |
| Fade | 250ms | ease-in-out | Modals, toasts |

### Scroll Behaviors
- Smooth scroll: enabled
- Sticky header: scrolls past 100px
- Reveal animations: fade-up on scroll into view

## 9. Responsive Breakpoints

| Breakpoint | Width | Behavior |
|------------|-------|----------|
| Mobile | < 640px | Single column, stacked nav |
| Tablet | 640-1024px | 2-column, condensed spacing |
| Desktop | > 1024px | Full layout, max-width container |

## 10. Do's and Don'ts

### Do
- Use generous whitespace
- Maintain consistent spacing
- Use color intentionally (not decoration)
- Ensure sufficient contrast ratios

### Don't
- Mix multiple primary colors
- Use more than 2 font families
- Create cramped layouts
- Overuse animations

## 11. Agent Prompt Guide

### Building a Hero Section
```
Create a hero section with:
- Full viewport height minus header
- Centered content, max-width 800px
- Large headline (H1) with tight letter-spacing
- Supporting subheadline (body-large)
- Two CTAs: primary + secondary
- Subtle gradient or illustration background
- Padding: 120px top, 80px bottom
```

### Building a Feature Card
```
Create a feature card with:
- White background, subtle border
- 24px padding
- Icon (40x40) in brand color
- H3 heading, 16px margin-top
- Body text description
- Hover: lift effect with shadow increase
```

---

**Document Version**: 1.0
**Extracted From**: [Site URL]
**Date**: [Current Date]
```

## HTML Preview Companion

Always generate a companion HTML file named `DESIGN-preview.html` alongside the DESIGN.md.

### Preview Structure

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Design System Preview - [Site Name]</title>
    <style>
        /* Preview styles using extracted design tokens */
    </style>
</head>
<body>
    <nav><!-- Navigation --></nav>
    
    <main>
        <section id="overview"><!-- Visual overview --></section>
        <section id="colors"><!-- Color palette display --></section>
        <section id="typography"><!-- Type scale --></section>
        <section id="components"><!-- Component examples --></section>
        <section id="markdown"><!-- Raw markdown source --></section>
    </main>
</body>
</html>
```

### Preview Must Include

1. **Color Swatches**: Visual display of all colors with hex values
2. **Type Scale**: Sample text for each typography level
3. **Component Gallery**: Live examples of buttons, cards, inputs
4. **Spacing Visual**: Visual representation of spacing scale
5. **Raw Markdown**: Collapsible section with full DESIGN.md source

## Quality Checklist

Before delivering, verify:

- [ ] Color values are exact (hex or rgb)
- [ ] Typography has specific sizes and weights
- [ ] Spacing uses a clear system (4px/8px base)
- [ ] Components have hover/active states documented
- [ ] Responsive behavior is described
- [ ] HTML preview renders correctly
- [ ] Another agent could rebuild the site from this document

## Example Usage

**User Input**:
> "Extract the design from https://linear.app"

**Process**:
1. Fetch Linear.app homepage
2. Analyze color system (dark theme, purple accents)
3. Document typography (SF Mono, Inter)
4. Extract components (minimal buttons, glass cards)
5. Note interactions (hover states, smooth scroll)
6. Write DESIGN.md
7. Generate DESIGN-preview.html

**Output Files**:
- `DESIGN.md` - Full design system documentation
- `DESIGN-preview.html` - Visual design board

## Troubleshooting

**Can't access website?**
- Try alternative paths (homepage vs specific page)
- Document public-facing pages only
- Note authentication barriers

**Design inconsistent across pages?**
- Document shared system first
- Note page-specific variations separately
- Identify if intentional or legacy

**Missing details?**
- Make reasonable assumptions based on visible patterns
- Mark inferred values clearly
- Keep documentation opinionated and usable
