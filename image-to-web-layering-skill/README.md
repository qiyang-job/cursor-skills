# Image to Web Layering Skill

A practical skill for converting complex visual webpage images, AI-generated website mockups, editorial layouts, collage-style posters, and experimental portfolio screenshots into maintainable responsive HTML/CSS/JS.

Core principle:

> Complex visuals become image assets. Core information becomes real HTML. Interaction states become structured UI states. Responsive layouts are recomposed, not blindly scaled.

## When to use

Use this skill when converting:

- AI-generated webpage images
- Experimental editorial web mockups
- Collage-style portfolio pages
- Magazine-like layouts
- Cultural institution websites
- Visual archive pages
- Poster-style landing pages
- Product narrative pages with dense visual layering

## What it produces

Before writing code, this skill asks the agent to output:

1. Page structure
2. Layer map
3. Asset extraction list
4. Core HTML content list
5. DOM plan
6. CSS layering strategy
7. Interaction state plan
8. Responsive recomposition plan
9. Development instructions
10. QA checklist

## Basic usage prompt

Copy this into Cursor, Codex, or another coding agent with the target image attached or referenced:

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

## Implementation prompt

After the analysis is complete and assets are prepared, use:

```text
Based on the layering report, generate the complete HTML, CSS, and JavaScript.

Requirements:
- Use real HTML text for all core information.
- Use extracted assets for media, decorations, texture, collage, and handmade visuals.
- Use CSS for grid, layout, spacing, section lines, and responsive behavior.
- Use minimal JavaScript only for filtering, expandable details, scroll states, or light parallax.
- Preserve the visual language, but do not flatten the webpage into one image.
- Desktop can preserve visual complexity; mobile must preserve information order and usability.
```

## Recommended project flow

```text
1. Generate or collect the webpage image.
2. Run this skill to produce a layering report.
3. Prepare assets according to the asset extraction list.
4. Put assets into the suggested folder structure.
5. Ask the coding agent to implement the page from the report.
6. Validate using validation.md.
```

## Quality target

- Desktop: 85% visual language fidelity + 100% usable structure
- Tablet: 70% visual language fidelity + 100% readable structure
- Mobile: 60% visual language fidelity + 100% content order and usability
- Core text: always real HTML
- Interaction states: structured, not baked into static images
