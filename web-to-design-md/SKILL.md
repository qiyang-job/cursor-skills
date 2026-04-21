---
name: web-to-design-md
description: Extract design systems from websites and convert them into structured DESIGN.md documents with companion HTML preview. Use when given website URLs and asked to analyze design, extract style guides, reverse-engineer UI, create design documentation, or capture visual language for implementation.
---

# Website to DESIGN.md

Convert any website into a structured design system document (DESIGN.md) with a visual HTML preview.

## When to Use

- User provides website URL(s) and asks to "extract design", "analyze website", "create design.md", or "reverse engineer UI"
- User wants to understand a site's visual language, color system, typography, or components
- User needs design documentation for rebuilding or referencing a site's style
- User mentions "design system", "style guide", "UI kit", or "design tokens" in context of a website

## Quick Start Workflow

```
1. Identify target URL(s) from user input
2. Fetch and analyze the website content
3. Extract design tokens (colors, typography, spacing)
4. Document components and patterns
5. Write DESIGN.md
6. Generate HTML preview companion
7. Deliver both files to user
```

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
