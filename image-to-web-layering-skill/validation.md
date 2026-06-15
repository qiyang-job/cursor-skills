# Validation Protocol

Use this file to verify whether the skill is effective.

Do not validate only by pixel similarity. Use six dimensions:

1. Layer accuracy
2. Content fidelity
3. Visual language fidelity
4. Responsive usability
5. Maintainability
6. Asset extraction quality

## 1. Layer Accuracy

Check whether the skill correctly classified elements into:

- Background
- Grid / Layout
- Media
- Content
- Decoration
- Interaction

Core text must be HTML.
Complex handmade visuals should be image assets.
Grid and layout rules should usually be CSS.

### Checklist

- [ ] Main title is HTML text
- [ ] Body copy is HTML text
- [ ] Navigation and CTA are HTML
- [ ] Case metadata is HTML
- [ ] Grid lines are CSS or lightweight SVG
- [ ] Photos and artwork are media assets
- [ ] Tape, stickers, paper scraps, and doodles are decoration assets
- [ ] Hover labels and expanded details are structured UI states
- [ ] Source UI text is not accidentally baked into media crops
- [ ] Background textures do not contain semantic text or foreground remnants

## 2. Content Fidelity

All important information must be preserved as real editable text:

- Navigation
- Hero title
- Intro copy
- CTA
- Section titles
- Case names
- Years
- Roles
- Industries
- Tags
- Contact details

Target: 100%.

## 3. Visual Language Fidelity

The final webpage should preserve:

- Canvas model: full-bleed, centered max-width shell, hybrid, or poster-like composition
- Composition logic
- Typography hierarchy and source font category
- Hero title line rhythm
- Color mood
- Image layering
- Collage relationship
- Editorial rhythm
- Experimental visual character

Pixel-perfect matching is not required.

Target:
- Desktop visual fidelity: 85%
- Tablet visual fidelity: 70%
- Mobile visual fidelity: 60%
- Content fidelity: 100%

## 4. Responsive Usability

Test at:

- 1440px
- 1024px
- 768px
- 390px

Checklist:

- [ ] No horizontal overflow
- [ ] No blocked text
- [ ] No broken image layering
- [ ] CTA remains usable
- [ ] Information order remains logical
- [ ] Hover-only information has mobile fallback
- [ ] Decorative assets do not cover content
- [ ] Centered fixed-width designs do not stretch indefinitely on wide screens

## 5. Maintainability

Checklist:

- [ ] Assets are named clearly
- [ ] Decorative assets are separated
- [ ] z-index system is consistent
- [ ] Text is editable
- [ ] Cases can be replaced
- [ ] Layout can be extended
- [ ] CSS is not overly dependent on one fixed screenshot size
- [ ] Decoration layer uses pointer-events: none where appropriate
- [ ] Display fonts are chosen by source typography category, not arbitrary defaults
- [ ] No unnecessary negative letter spacing

## 6. Asset Extraction Quality

Check the extraction strategy and asset condition:

- [ ] A contact sheet or equivalent visual review was used for multiple assets
- [ ] Each asset declares an extraction type: rect crop, masked crop, subject cutout, cleanup/inpaint, upscale, vector/CSS recreate, or regenerate
- [ ] Non-rectangular foreground objects use alpha cutouts when rectangular crops look wrong
- [ ] Unwanted UI text, neighboring section lines, and metadata overlays are removed from media assets
- [ ] Text that remains in images is part of the photographed object or artwork
- [ ] Low-resolution crops are upscaled/enhanced before use
- [ ] Asset natural size is at least 1.5x intended rendered size where possible
- [ ] Photo assets use WebP/AVIF, alpha assets use PNG/WebP alpha, and simple marks use SVG/CSS

## Required Browser Checks

Run these checks after implementation when a browser is available:

- 1440px, 1024px, 768px, and 390px viewport checks
- `document.documentElement.scrollWidth <= document.documentElement.clientWidth`
- All images complete with nonzero natural size
- No console errors
- Hero title line count and CTA visibility are acceptable
- Filter/tab/expanded states work through real click or tap actions

## Scoring Table

| Dimension | Score 1-5 | Target |
|---|---:|---:|
| Layer accuracy |  | >= 4 |
| Content fidelity |  | 5 |
| Desktop visual fidelity |  | >= 4 |
| Responsive usability |  | >= 4 |
| Maintainability |  | >= 4 |
| Interaction clarity |  | >= 4 |
| Asset extraction quality |  | >= 4 |

If three different image types can pass this table, the skill is effective enough for repeated use.
