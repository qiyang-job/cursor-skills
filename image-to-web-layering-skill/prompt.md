# Usage Prompts

## Analysis Prompt

Use this before writing code.

```text
Please use the Image to Web Layering Skill to analyze this webpage image.

Goal:
Convert this image into a maintainable responsive webpage.

Before writing code, first output:
1. Page structure
2. Layer map
3. Asset extraction list
4. Core HTML content list
5. DOM plan
6. CSS layering strategy
7. Interaction state plan
8. Responsive recomposition plan
9. QA checklist

Principle:
Complex visuals become image assets.
Core information becomes real HTML.
Interaction states become structured UI states.
Responsive layouts are recomposed, not blindly scaled.
```

## Asset Extraction Prompt

Use this after the first report.

```text
Based on the layering report, produce a cutout task list.

For each asset, include:
- filename
- source element
- priority A/B/C/D
- extraction method
- suggested tool
- required on mobile or optional
- whether it is decorative or semantic
- notes for transparent background, mask, or crop
```

## Implementation Prompt

Use this after assets are prepared.

```text
Based on the layering report and the available assets, generate the complete responsive webpage using HTML, CSS, and minimal JavaScript.

Requirements:
- Use real HTML text for all core information.
- Use extracted assets for media, decorations, texture, collage, and handmade visuals.
- Use CSS for grid, layout, spacing, section lines, and responsive behavior.
- Use JavaScript only for filtering, expandable details, scroll states, or light parallax.
- Preserve the visual language, but do not flatten the webpage into one image.
- Desktop can preserve visual complexity; mobile must preserve information order and usability.
- Hide or simplify decorative assets on mobile when they block reading or create overflow.
- Provide a short implementation note explaining any intentional deviations from the source image.
```

## QA Prompt

Use this after the first implementation.

```text
Evaluate the generated webpage using validation.md.

Check:
1. Layer accuracy
2. Content fidelity
3. Visual language fidelity
4. Responsive usability
5. Maintainability
6. Interaction clarity

Return:
- score table
- concrete issues
- priority fixes
- exact files/selectors to adjust
```
