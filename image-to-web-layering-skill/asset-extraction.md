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

Use rectangular crops for:

- Photos already inside rectangular cards
- Hero photos with clean edges
- Image banners
- Device screenshots that remain rectangular
- Background plates that do not need transparency

Use masked crops for:

- Irregular edges over a simple background
- Torn paper and taped pieces
- Organic collage fragments
- Shapes where a hard rectangle would visibly break the composition

Use subject cutout tools for:

- Clear foreground objects
- Product images
- People
- Devices floating over another background
- Isolated collage pieces
- Stickers
- Paper scraps
- Large hand-drawn shapes

Use manual extraction or edge refinement for:

- Overlapping collage elements
- Torn paper edges
- Transparent tape
- Thin handwritten annotations
- Low-contrast doodles
- Elements touching important text

Use inpaint or cleanup for:

- Baked-in UI text that should become HTML
- Grid lines or dividers that should become CSS
- Neighboring sections accidentally included in a crop
- Captions, dates, filters, or metadata over media that should be editable
- Small artifacts left after background removal

Use upscale/enhance for:

- Crops smaller than their intended rendered size
- Blurry or compressed source regions
- Dark crops that lose product or architectural detail
- Cutouts with soft edges after segmentation

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

Keep text inside a media asset only when it belongs to the photographed object or scene, such as package labels, phone screens, signage, or artwork. Remove or rebuild UI overlay text as HTML/CSS.

## Asset priority

Use this priority scale:

- A — Required. Without this asset, the page loses its core identity or content.
- B — Recommended. Improves visual fidelity and style.
- C — Optional. Can be replaced by CSS or omitted.
- D — Decorative. Can be hidden on mobile or removed if needed.

## Cutout task list template

| Priority | Asset | Extraction Type | Suggested Tool | Format | Required on Mobile | QA Notes |
|---|---|---|---|---|---|---|
| A | hero-main.webp | Rect crop / cleanup | Figma / Photoshop | WebP | Yes | Remove baked-in UI text if present |
| A | product-01.png | Subject cutout | Photoshop / remove.bg / SAM | PNG/WebP alpha | Yes | Refine alpha edges and shadow |
| A | case-01.webp | Rect crop | Figma | WebP | Yes | Core project image |
| B | tape-blue.png | Manual cutout | Photoshop | PNG/WebP alpha | Optional | Transparent edge important |
| B | hand-arrow-01.svg | Vector trace | Illustrator / Figma | SVG | Optional | Keep line roughness |
| C | paper-noise.webp | Generated/clean texture | Figma / script | WebP | Yes | Must not contain text or foreground shapes |
| D | small-star-doodle.svg | Redraw or omit | Figma | SVG | No | Decorative only |

## Asset quality gate

Before using extracted assets in the webpage:

- Natural asset width should be at least 1.5x the rendered width; prefer 2x for hero and product assets.
- Background textures must not contain semantic text, logos, titles, or obvious foreground remnants.
- Rectangular media crops must not contain UI text that will be rebuilt in HTML.
- Cutouts must have clean alpha edges and no visible matte halo.
- Low-resolution or dark assets should be upscaled, sharpened, and contrast-adjusted before export.
- Photos should usually be WebP/AVIF; transparent cutouts should be PNG or WebP with alpha; simple marks should be SVG or CSS.
- Generate a contact sheet or equivalent visual check before implementation when more than three assets are extracted.
