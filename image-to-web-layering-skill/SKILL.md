---
name: image-to-web-layering
description: Convert complex visual webpage images, AI-generated web mockups, editorial layouts, collage posters, and experimental portfolio screenshots into maintainable responsive HTML/CSS/JS by separating image assets, real HTML content, interaction states, and responsive recomposition plans. Use when turning a screenshot or generated webpage image into a coded webpage.
---

# Image to Web Layering Skill

## Purpose

This skill helps convert complex visual webpage screenshots, AI-generated web mockups, editorial layouts, collage-style posters, experimental portfolio images, and mixed-media visual compositions into maintainable responsive webpages.

The goal is not pixel-perfect screenshot tracing. The goal is:

> Complex visuals become image assets.
> Core information becomes real HTML.
> Interaction states become structured UI states.
> Responsive layouts are recomposed, not blindly scaled.

Use this skill whenever the input is a complex visual image that needs to be transformed into a webpage.

---

## Core Principle

Always separate the image into implementation layers:

1. Background Layer
2. Grid / Layout Layer
3. Media Layer
4. Content Layer
5. Decoration Layer
6. Interaction Layer

Do not treat the screenshot as one flat image.

---

## Layer Definitions

### L0 — Background Layer

Includes:
- Paper texture
- Noise
- Grain
- Gradient mist
- Scan marks
- Photocopy texture
- Surface tint
- Background color

Implementation:
- CSS background color
- CSS gradients
- Repeated texture image
- Fixed pseudo-element overlay

Preferred asset types:
- WebP
- PNG
- Small repeated texture files

Do not merge foreground content into the background.

### L1 — Grid / Layout Layer

Includes:
- Thin grid lines
- Column guides
- Section dividers
- Coordinate lines
- Numbering axis
- Index marks
- Editorial rules

Implementation:
- CSS grid
- CSS pseudo-elements
- SVG only when shape is complex

Preferred approach:
- Use CSS wherever possible.
- Keep layout lines responsive.

### L2 — Media Layer

Includes:
- Hero image
- Product image
- Case image
- Photography
- Architecture image
- Artwork image
- Screenshot
- Cropped image
- Specimen detail

Implementation:
- Real image elements using `<img>` or `<picture>`
- Use WebP / AVIF when possible
- Use PNG / WebP with transparency for irregular cutouts

Do not place important textual information inside flattened media images unless it is part of the artwork.

### L3 — Content Layer

Includes:
- Main title
- Section title
- Body copy
- Navigation
- CTA
- Project names
- Years
- Industry
- Role
- Tags
- Metadata
- Contact information
- Case description

Implementation:
- Must be real HTML text
- Must be editable
- Must be responsive
- Must preserve reading order

Never export core content as an image.

### L4 — Decoration Layer

Includes:
- Hand-drawn arrows
- Doodles
- Circles
- Underlines
- Stickers
- Tape
- Sticky notes
- Torn paper
- Stamps
- Handwritten annotations
- Rough icons
- Scribbles
- Collage scraps

Implementation:
- Independent SVG / PNG / WebP assets
- Usually absolutely positioned
- `pointer-events: none`
- `aria-hidden="true"` unless meaningful

These elements may be hidden or simplified on mobile.

### L5 — Interaction Layer

Includes:
- Hover labels
- Hover metadata
- Scanline effect
- Enlarged preview
- Tooltip
- Selected state
- Expanded detail
- Cursor hint
- Active filter
- CTA hover
- Case preview

Implementation:
- Real HTML structure
- CSS transitions
- Small JavaScript only when necessary
- Do not bake interaction states into static images.

---

## Analysis Procedure

### Step 1 — Identify Page Type

Classify the image:

- Regular UI
- Editorial layout
- Experimental collage
- Portfolio index
- Poster-like landing page
- Product narrative page
- Archive / case index
- Mixed media website

Then decide how much should be rebuilt in code versus preserved as image assets.

Also classify the canvas model before coding:

- Full-bleed responsive page
- Centered fixed/max-width editorial canvas
- Hybrid full-bleed background with constrained content
- Poster-like fixed composition with responsive recomposition

Do not assume the layout should stretch to fill very wide browsers. If the screenshot uses a designed canvas, implement a centered site shell with a max width and an outer browser background.

### Step 1A — Identify Typography System

Map typography before implementation:

- Hero/display type: serif, high-contrast serif, condensed sans, tall compressed sans, grotesk, mono, or custom lettering
- Navigation/caption type
- Body copy type
- Metadata/tag type

Use close web-safe or open-source font stacks. Do not use arbitrary default serif/sans fonts for hero typography when a closer display category is visible. If commercial fonts are unavailable, choose a close fallback and document the tradeoff.

### Step 2 — Identify Main Sections

Break the page into sections, such as:

- Hero / Poster Intro
- Case Index / Visual Archive
- Method / Process
- Selected Detail / Specimen
- Services / System
- Evidence / Metrics
- Contact / Ending

Each section should become a real `<section>` in HTML.

### Step 3 — Detect Core Information

Identify all text or semantic information that must become HTML:

- Brand name
- Navigation items
- Hero headline
- Intro paragraph
- CTA text
- Section labels
- Case names
- Case metadata
- Method steps
- Contact details

Output them as structured content.

### Step 4 — Detect Image Assets

Identify all visual elements that should be exported as assets:

- Main photos
- Case thumbnails
- Cropped images
- Stickers
- Tape
- Hand-drawn arrows
- Handwritten annotations
- Paper scraps
- Texture overlays
- Stamps
- Irregular masks

For each asset, provide:
- Suggested filename
- Source element
- Layer
- Format
- Priority: A/B/C/D
- Whether it is required on mobile
- Whether it is decorative or semantic
- Suggested extraction method

Choose an extraction strategy for each asset:

- Rect crop: rectangular photos, cards, and banners
- Masked crop: irregular edges over simple backgrounds
- Subject cutout: products, people, devices, stickers, paper scraps, and floating objects
- Inpaint cleanup: remove baked-in UI text, grid lines, or neighboring sections that should be HTML/CSS
- Upscale enhance: small, blurry, or compressed crops that render larger in the webpage
- Vector/CSS recreate: simple icons, arrows, grid lines, dots, dividers, and geometric marks
- Regenerate/replace: non-essential visuals that cannot be cleanly extracted and are not specific real content

Core UI text, navigation, titles, metadata, filters, and contact details should not remain baked into media assets. Packaging labels, phone screens, environmental signs, and product marks may stay inside media when they are part of the photographed object or scene.

### Step 5 — Detect Layout System

Describe:
- Grid system
- Column count
- Section spacing
- Alignment logic
- Intentional misalignment
- Overlap areas
- Z-index relationship
- Which elements are absolute
- Which elements remain in normal document flow

### Step 6 — Define Interaction States

For each interactive object, define:
- Default state
- Hover state
- Active state
- Focus state
- Mobile behavior

Typical examples:
- Case item hover shows year, role, industry, keywords
- Image hover shows scanline or slight zoom
- CTA hover creates marker underline
- Filter active state changes label style
- Detail module expands on click

### Step 7 — Define Responsive Recomposition

Do not blindly scale the desktop layout.

For mobile:
- Preserve content order
- Keep core media
- Hide excessive decorative assets
- Reduce absolute positioning
- Stack case index items
- Keep CTA visible
- Avoid horizontal overflow
- Simplify hover-only information into always-visible or tap-visible metadata

Output separate recommendations for:
- Desktop
- Tablet
- Mobile

---

## Required QA Passes

Use these passes when implementing, not only when analyzing:

1. Asset QA pass
   - Generate or inspect a contact sheet for extracted assets.
   - Re-crop, mask, inpaint, or recreate assets that contain unwanted baked-in UI text.
   - Ensure background textures do not contain semantic text or strong foreground shapes.
   - Check whether each asset is large enough for its rendered size; upscale and sharpen when needed.
2. Visual rhythm pass
   - Check hero title line count, CTA visibility, main media proportion, section heights, and card rhythm against the source image.
   - Preserve the source's canvas behavior: centered max-width canvas vs full-bleed layout.
3. Browser QA pass
   - Test at 1440px, 1024px, 768px, and 390px.
   - Check no horizontal overflow, no blocked text, all images loaded, and no console errors.
   - Verify every interactive filter/tab/expanded state with an actual browser action when possible.

---

## Output Format

When this skill is used, always produce the following sections:

1. Page structure
2. Layer map
3. Canvas model
4. Typography map
5. Asset extraction list
6. Core HTML content list
7. Suggested DOM structure
8. CSS layering strategy
9. Interaction state plan
10. Responsive recomposition plan
11. Implementation instructions
12. QA checklist

---

## Implementation Rules

1. Text that users need to read, copy, search, translate, update, or interact with must be HTML text.
2. Handmade visual texture, irregular marks, tape, torn paper, doodles, stamps, and complex collage elements should be exported as image assets.
3. Grid lines, column rules, dividers, and spacing systems should usually be CSS.
4. Hover, active, focus, selected, and expanded states must be implemented structurally, not baked into static images.
5. Desktop visual complexity may be high, but mobile must prioritize order and readability.
6. Do not use large rounded cards, glassmorphism, generic SaaS blocks, or template portfolio patterns unless the source image clearly uses them.
7. Avoid unnecessary JavaScript. Use CSS for most state feedback. Use JavaScript only for filtering, expandable details, scroll states, or parallax.
8. Decorative assets should use `alt=""` and `aria-hidden="true"`.
9. Always define a z-index system before implementing absolute-positioned collage elements.
10. The final webpage should preserve the visual language, not necessarily every pixel.
11. Do not stretch a designed fixed-width canvas across unlimited browser width; use a centered max-width shell when the source indicates one.
12. Match typography categories deliberately, especially hero/display type. Document fallback fonts when exact fonts are unavailable.
13. Do not keep unwanted source UI text inside media crops. Re-crop, mask, inpaint, or rebuild that content as HTML/CSS.
14. Use cutouts with alpha for non-rectangular products, devices, stickers, paper, and floating objects when rectangular crops would look wrong.
15. Enhance low-resolution extracted assets before use when their rendered size exceeds the crop's useful resolution.
16. Avoid negative letter spacing unless the source clearly depends on it and the text remains readable; prefer 0 letter spacing for maintainable web output.

---

## Suggested Z-Index System

```css
:root {
  --z-bg: 0;
  --z-grid: 10;
  --z-media: 20;
  --z-content: 30;
  --z-decoration: 40;
  --z-interaction: 50;
  --z-header: 80;
  --z-noise: 100;
}
```

---

## Suggested Asset Naming

```text
/assets
  /bg
    paper-noise.webp
    scan-texture.webp
    gradient-wash.webp

  /media
    hero-main.webp
    case-01.webp
    case-02.webp
    specimen-01.webp

  /doodle
    arrow-01.svg
    circle-01.svg
    underline-01.svg
    sun-01.svg

  /collage
    tape-blue.png
    tape-pink.png
    sticky-note-yellow.webp
    torn-paper-01.webp
    stamp-01.svg

  /mask
    torn-edge-01.png
    irregular-mask-01.svg
```

---

## Final Quality Standard

- Desktop: 85% visual similarity, 100% usable structure
- Tablet: 70% visual similarity, 100% readable structure
- Mobile: 60% visual similarity, 100% content order and usability
- Interaction: restrained, clear, and maintainable
- Assets: named, replaceable, and layered
