# Design Extraction Guide

Reference for extracting design tokens from websites.

## Color Extraction

### Primary/Brand Colors
Look for:
- CTA buttons (primary action color)
- Links and interactive elements
- Logo/accent colors
- Active states

### Neutral Scale
Look for:
- Background colors (page, sections, cards)
- Text colors (headings, body, secondary)
- Border colors
- Divider/separator colors

### Semantic Colors
- Success: Check success messages, checkmarks
- Error: Error messages, validation states
- Warning: Warning banners, alerts
- Info: Info banners, badges

**Tools**:
- Browser dev tools color picker
- CSS variable inspection (`:root` or body styles)
- Screenshot + digital color meter

## Typography Extraction

### Font Families
Check:
- `<body>` or `:root` font-family declarations
- Heading-specific fonts
- Monospace/code fonts

### Type Scale
Measure:
- Hero/Display text size
- H1, H2, H3, H4 sizes
- Body text size
- Caption/small text size

Also capture:
- Line heights for each level
- Letter spacing
- Font weights used

**Tools**:
- Browser dev tools → Computed → font-size
- WhatFont browser extension
- Screenshot + measurement

## Spacing Extraction

### Base Unit
Determine if spacing follows:
- 4px grid (0, 4, 8, 12, 16, 24, 32, 48, 64...)
- 8px grid (0, 8, 16, 24, 32, 48, 64, 96...)

### Common Values
Measure:
- Button padding (horizontal/vertical)
- Card padding
- Section padding (vertical)
- Grid gaps
- Input padding

**Tools**:
- Browser dev tools → Box model panel
- Measure spacing between elements

## Component Extraction

### Buttons
Document:
- Default state (bg, text, border, padding, radius)
- Hover state (bg change, shadow, transform)
- Active/pressed state
- Disabled state
- Size variants (sm, md, lg)

### Cards
Document:
- Background color
- Border (width, color, style)
- Border radius
- Padding (internal spacing)
- Shadow
- Hover effect

### Inputs
Document:
- Height
- Padding
- Border (default, focus, error)
- Border radius
- Placeholder style

### Navigation
Document:
- Height
- Background (solid, transparent, blur)
- Position (static, sticky, fixed)
- Shadow on scroll
- Mobile behavior

## Motion Extraction

### Transitions
Check CSS for:
```css
transition: property duration easing;
```

Common patterns:
- Hover transitions: 150-300ms
- Color transitions: 200ms
- Transform transitions: 300ms
- Complex animations: 400-600ms

### Easing Functions
Common values:
- `ease` / `ease-out` - Standard transitions
- `ease-in-out` - Smooth both ways
- `cubic-bezier(0.4, 0, 0.2, 1)` - Material design standard
- `cubic-bezier(0.16, 1, 0.3, 1)` - Expo out (snappy)

### Scroll Behaviors
- Smooth scroll: `scroll-behavior: smooth`
- Sticky headers: `position: sticky`
- Reveal animations: IntersectionObserver triggers

## Responsive Extraction

### Breakpoints
Check CSS media queries for:
- Mobile max-width
- Tablet range
- Desktop min-width

Common breakpoints:
- 640px (sm)
- 768px (md)
- 1024px (lg)
- 1280px (xl)

### Responsive Patterns
Document changes at each breakpoint:
- Grid columns (4 → 8 → 12)
- Navigation (hamburger → horizontal)
- Typography scale (smaller on mobile)
- Spacing (reduced on mobile)

## Content Tone Extraction

### Voice Characteristics
- Formal vs casual
- Technical vs simple
- Playful vs serious
- Short vs descriptive

### Writing Patterns
- Headline style (sentence case vs title case)
- CTA patterns ("Get Started" vs "Sign Up Now")
- Feature descriptions
- Error messages tone

## Common Challenges

### Inconsistent Values
If a site uses inconsistent values:
- Document the most common pattern
- Note variations as "exceptions"
- Recommend a standardized system

### Dynamic Themes
If site has light/dark mode:
- Extract both palettes
- Note CSS variables used
- Document toggle mechanism

### Complex Gradients
If extracting gradients:
- Note gradient direction
- Capture all color stops
- Document opacity changes

### Missing Hover States
If hover states are hidden:
- Check CSS `:hover` rules
- Use dev tools to force state
- Make reasonable assumptions

## Quality Checklist

After extraction, verify:

- [ ] Colors are exact hex/rgb values
- [ ] Typography has specific px/rem values
- [ ] Spacing uses consistent base unit
- [ ] Component states are documented
- [ ] Animations have duration + easing
- [ ] Responsive breakpoints noted
- [ ] Content tone captured
- [ ] Another agent could rebuild from docs

## Quick Reference: CSS Properties to Check

```css
/* Colors */
color, background-color, border-color

/* Typography */
font-family, font-size, font-weight, line-height, letter-spacing

/* Spacing */
margin, padding, gap

/* Layout */
max-width, width, height, display, grid, flex

/* Visual */
border-radius, border, box-shadow, opacity

/* Motion */
transition, animation, transform
```
