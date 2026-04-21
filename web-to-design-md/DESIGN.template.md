# [Site Name] Design System

## 1. Visual Theme & Atmosphere

**Overall Feel**: [e.g., "Minimalist tech SaaS with bold typography and subtle gradients"]

**Key Characteristics**:
- Clean, spacious layout with generous whitespace
- Bold, confident typography as primary visual element
- Subtle use of color for emphasis rather than decoration
- Consistent rounded corners and soft shadows
- Professional yet approachable personality

**Design Philosophy**: [Describe the core approach, e.g., "Content-first with UI that disappears"]

---

## 2. Color Palette

### Primary Colors

| Role | Hex | RGB | Usage |
|------|-----|-----|-------|
| Primary | `#[VALUE]` | rgb() | CTAs, links, active states |
| Primary Hover | `#[VALUE]` | rgb() | Hover states |
| Primary Light | `#[VALUE]` | rgb() | Backgrounds, badges |

### Secondary/Accent Colors

| Role | Hex | RGB | Usage |
|------|-----|-----|-------|
| Secondary | `#[VALUE]` | rgb() | Alternative CTAs |
| Success | `#[VALUE]` | rgb() | Positive states |
| Warning | `#[VALUE]` | rgb() | Caution states |
| Error | `#[VALUE]` | rgb() | Error states |

### Neutral Scale

| Role | Hex | RGB | Usage |
|------|-----|-----|-------|
| Background | `#[VALUE]` | rgb() | Page background |
| Surface | `#[VALUE]` | rgb() | Cards, modals |
| Surface Elevated | `#[VALUE]` | rgb() | Popovers, dropdowns |
| Border | `#[VALUE]` | rgb() | Dividers, outlines |
| Border Hover | `#[VALUE]` | rgb() | Interactive borders |
| Text Primary | `#[VALUE]` | rgb() | Headlines, body text |
| Text Secondary | `#[VALUE]` | rgb() | Descriptions, meta |
| Text Tertiary | `#[VALUE]` | rgb() | Placeholders, hints |
| Text Inverse | `#[VALUE]` | rgb() | Text on dark backgrounds |

### Dark Mode (if applicable)

| Role | Hex | RGB | Usage |
|------|-----|-----|-------|
| Background | `#[VALUE]` | rgb() | Dark page background |
| Surface | `#[VALUE]` | rgb() | Dark cards |
| Text Primary | `#[VALUE]` | rgb() | Dark mode text |

---

## 3. Typography

### Font Families

- **Primary**: [Font name, e.g., "Inter, -apple-system, BlinkMacSystemFont, sans-serif"]
- **Secondary**: [If applicable]
- **Monospace**: [e.g., "JetBrains Mono, Fira Code, monospace"]

### Type Scale

| Level | Size | Weight | Line Height | Letter Spacing | Usage |
|-------|------|--------|-------------|----------------|-------|
| Display | [px/rem] | [400-900] | [ratio] | [em] | Hero headlines |
| H1 | [px/rem] | [400-900] | [ratio] | [em] | Page titles |
| H2 | [px/rem] | [400-900] | [ratio] | [em] | Section headers |
| H3 | [px/rem] | [400-900] | [ratio] | [em] | Subsection headers |
| H4 | [px/rem] | [400-900] | [ratio] | [em] | Card titles |
| Body Large | [px/rem] | [400-900] | [ratio] | [em] | Lead paragraphs |
| Body | [px/rem] | [400-900] | [ratio] | [em] | Standard text |
| Body Small | [px/rem] | [400-900] | [ratio] | [em] | Captions |
| Tiny | [px/rem] | [400-900] | [ratio] | [em] | Metadata |

### Typography Patterns

- **Headings**: [e.g., "Tight letter-spacing, bold weight"]
- **Body**: [e.g., "Relaxed line-height for readability"]
- **Links**: [e.g., "Underline on hover, color transition"]

---

## 4. Spacing System

### Base Unit

Base unit: [4px/8px]

### Spacing Scale

| Token | Value | Pixels | Usage |
|-------|-------|--------|-------|
| 0 | 0 | 0 | No spacing |
| px | 1px | 1 | Hairline borders |
| xs | [rem] | [px] | Tight gaps |
| sm | [rem] | [px] | Component internal |
| md | [rem] | [px] | Default padding |
| lg | [rem] | [px] | Component gaps |
| xl | [rem] | [px] | Section gaps |
| 2xl | [rem] | [px] | Major separations |
| 3xl | [rem] | [px] | Section padding |
| 4xl | [rem] | [px] | Hero sections |

### Layout Spacing

- **Container max-width**: [px/rem]
- **Container padding**: [px/rem] (mobile), [px/rem] (desktop)
- **Section padding**: [px/rem] vertical
- **Grid gap**: [px/rem]

---

## 5. Components

### Buttons

**Primary Button**
- Background: `#[HEX]`
- Text color: `#[HEX]`
- Padding: [px/rem] [px/rem]
- Border-radius: [px/rem]
- Font: [weight] [size]
- Hover: [description]
- Active: [description]
- Disabled: [description]

**Secondary Button**
- Background: [value]
- Border: [width] solid `#[HEX]`
- Text color: `#[HEX]`
- Hover: [description]

**Tertiary/Ghost Button**
- Background: [value]
- Text color: `#[HEX]`
- Hover: [description]

### Cards

**Standard Card**
- Background: `#[HEX]`
- Border: [width] solid `#[HEX]`
- Border-radius: [px/rem]
- Padding: [px/rem]
- Shadow: [value]
- Hover: [description]

**Feature Card**
- [Differences from standard]

### Inputs

**Text Input**
- Height: [px/rem]
- Padding: [px/rem]
- Border: [width] solid `#[HEX]`
- Border-radius: [px/rem]
- Font: [size]
- Placeholder color: `#[HEX]`
- Focus: [description]
- Error: [description]

**Textarea**
- [Specifications]

**Select/Dropdown**
- [Specifications]

### Navigation

**Header/Nav**
- Height: [px/rem]
- Background: [value]
- Position: [fixed/static/sticky]
- Shadow: [value when scrolled]

**Mobile Menu**
- [Description]

### Other Components

[Document: Badges, Tags, Avatars, Modals, Alerts, Tooltips, etc.]

---

## 6. Layout Principles

### Grid System

- **Columns**: [number]
- **Column width**: [calculation]
- **Gutter**: [px/rem]
- **Margin**: [px/rem]

### Container

- **Max-width**: [px/rem]
- **Padding**: [px/rem]

### Responsive Behavior

| Breakpoint | Width | Adjustments |
|------------|-------|-------------|
| sm | < [px] | [Changes] |
| md | [px] - [px] | [Changes] |
| lg | [px] - [px] | [Changes] |
| xl | > [px] | [Changes] |

---

## 7. Depth & Elevation

### Shadow Scale

| Level | Shadow | Usage |
|-------|--------|-------|
| none | none | Flat elements |
| sm | `[value]` | Inputs, tags |
| md | `[value]` | Cards, buttons |
| lg | `[value]` | Dropdowns, popovers |
| xl | `[value]` | Modals |
| 2xl | `[value]` | Overlays |

### Border Radius Scale

| Token | Value | Usage |
|-------|-------|-------|
| none | 0 | Sharp corners |
| sm | [px/rem] | Inputs, small elements |
| md | [px/rem] | Buttons, cards |
| lg | [px/rem] | Containers |
| xl | [px/rem] | Large sections |
| full | 9999px | Pills, avatars |

### Z-Index Scale

| Layer | Z-Index | Usage |
|-------|---------|-------|
| Base | 0 | Default content |
| Dropdown | 10 | Select menus |
| Sticky | 20 | Sticky headers |
| Fixed | 30 | Fixed elements |
| Overlay | 40 | Backdrops |
| Modal | 50 | Dialogs |
| Toast | 60 | Notifications |
| Tooltip | 70 | Tooltips |

---

## 8. Motion & Animation

### Transition Defaults

| Property | Duration | Easing |
|----------|----------|--------|
| Default | [ms] | [easing] |
| Fast | [ms] | [easing] |
| Slow | [ms] | [easing] |

### Easing Functions

- **Default**: [easing, e.g., "ease-out"]
- **Enter**: [easing]
- **Exit**: [easing]
- **Bounce**: [easing]

### Common Animations

**Hover States**
- Buttons: [description]
- Cards: [description]
- Links: [description]

**Scroll Behaviors**
- Smooth scroll: [enabled/disabled]
- Reveal animations: [description]
- Parallax: [description]

**Page Transitions**
- [Description]

---

## 9. Content Patterns

### Voice & Tone

- **Personality**: [e.g., "Professional but approachable"]
- **Language**: [e.g., "Clear, concise, action-oriented"]
- **Sentence style**: [e.g., "Sentence case for headlines"]

### Headline Patterns

- [Example patterns observed]

### CTA Patterns

- [Example button labels observed]

---

## 10. Do's and Don'ts

### Do

- [Best practice 1]
- [Best practice 2]
- [Best practice 3]

### Don't

- [Anti-pattern 1]
- [Anti-pattern 2]
- [Anti-pattern 3]

---

## 11. Agent Prompt Guide

### Quick Start Templates

**Building a Button**
```
Create a [primary/secondary] button with:
- Background: #[HEX]
- Text: [weight] [size] #[HEX]
- Padding: [value]
- Border-radius: [value]
- Hover: [effect]
```

**Building a Card**
```
Create a card with:
- Background: #[HEX]
- Border: [specs]
- Border-radius: [value]
- Padding: [value]
- Shadow: [value]
- Hover: [effect]
```

**Building a Section**
```
Create a [type] section with:
- Background: [value]
- Padding: [value]
- Max-width: [value]
- Content: [layout description]
```

### Implementation Notes

- [Specific guidance for AI implementation]
- [Common pitfalls to avoid]
- [Recommended libraries if applicable]

---

**Document Version**: 1.0
**Extracted From**: [URL(s)]
**Extraction Date**: [Date]
**Confidence Level**: [High/Medium/Low - note if significant inference was needed]
