---
name: Product Design System
version: "0.1.0"
description: Visual identity, design tokens, and usage guidance for product interfaces.
colors:
  primary: "#000000"
  secondary: "#666666"
  background: "#FFFFFF"
  on-background: "#000000"
typography:
  body-md:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: "400"
    lineHeight: 24px
rounded:
  sm: 4px
  md: 8px
spacing:
  unit: 8px
  container-padding: 24px
components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.background}"
    typography: "{typography.body-md}"
    rounded: "{rounded.md}"
    padding: 12px 16px
---

## Overview

Describe the visual identity, brand personality, and product experience this system should create.

## Colors

Explain palette roles, semantic meaning, contrast expectations, and interaction usage. Reference color tokens rather than repeating values.

## Typography

Explain type families, hierarchy, scale, weight, line height, and readability decisions.

## Layout

Explain grid, spacing rhythm, containers, responsive behavior, alignment, and density.

## Elevation & Depth

Explain surfaces, borders, shadows, overlays, and depth relationships.

## Shapes

Explain corner radius, icon geometry, control dimensions, and shape usage.

## Components

Describe component roles, states, variants, accessibility expectations, and token application. Component token entries belong in YAML frontmatter.

## Do's and Don'ts

- Do use token references such as `{colors.primary}` for shared values.
- Do preserve contrast and accessible interaction states.
- Do keep visual decisions consistent with product intent and user needs.
- Do not introduce one-off values when an existing token applies.
- Do not use a token outside its documented semantic role.

## Validation and Export

Validate this exact `DESIGN.md` file with:

```bash
npx @google/design.md lint DESIGN.md
npx @google/design.md diff DESIGN.md DESIGN-v2.md
npx @google/design.md export --format json-tailwind DESIGN.md > tailwind.theme.json
```

The YAML frontmatter contains normative tokens. Markdown sections explain why tokens exist and how coding agents should apply them.
