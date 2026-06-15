# Asset Extraction Tool Integration

This skill can work with external image extraction tools, but it does not assume perfect automatic cutout.

The skill decides what should be extracted.
External tools extract the assets.

## Recommended tools

- Figma
- Photoshop
- Photopea
- remove.bg
- Segment Anything
- Illustrator Image Trace
- SVG tracing tools
- Manual pen tool extraction

## Extraction decision rules

Use automatic cutout tools for:

- Clear foreground objects
- Product images
- People
- Isolated collage pieces
- Stickers
- Paper scraps
- Large hand-drawn shapes

Use manual extraction for:

- Overlapping collage elements
- Torn paper edges
- Transparent tape
- Thin handwritten annotations
- Low-contrast doodles
- Elements touching important text

Use CSS instead of cutout for:

- Grid lines
- Section dividers
- Simple geometric blocks
- Background colors
- Simple gradients
- Scanlines
- Hover overlays

Use real HTML instead of cutout for:

- All important readable text
- Navigation
- CTA
- Metadata
- Tags
- Case names
- Contact details

## Asset priority

Use this priority scale:

- A — Required. Without this asset, the page loses its core identity or content.
- B — Recommended. Improves visual fidelity and style.
- C — Optional. Can be replaced by CSS or omitted.
- D — Decorative. Can be hidden on mobile or removed if needed.

## Cutout task list template

| Priority | Asset | Extraction Method | Suggested Tool | Required on Mobile | Notes |
|---|---|---|---|---|---|
| A | hero-main.webp | Manual crop / subject cutout | Photoshop / Figma | Yes | Preserve main silhouette |
| A | case-01.webp | Rectangular crop | Figma | Yes | Core project image |
| B | tape-blue.png | Manual cutout | Photoshop | Optional | Transparent edge important |
| B | hand-arrow-01.svg | Vector trace | Illustrator / Figma | Optional | Keep line roughness |
| C | paper-noise.webp | Texture crop | Figma | Yes | Can tile |
| D | small-star-doodle.svg | Redraw or omit | Figma | No | Decorative only |
