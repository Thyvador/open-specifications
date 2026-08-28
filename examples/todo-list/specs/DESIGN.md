---
name: Todo List Design System
version: "0.1.0"
description: Minimal visual identity for the todo-list example.
colors:
  primary: "#1D4ED8"
  background: "#FFFFFF"
  on-background: "#111827"
  surface: "#F3F4F6"
  on-surface: "#111827"
  error: "#B91C1C"
typography:
  body-md:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: "400"
    lineHeight: 24px
  label-sm:
    fontFamily: Inter
    fontSize: 12px
    fontWeight: "600"
    lineHeight: 16px
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
    typography: "{typography.label-sm}"
    rounded: "{rounded.md}"
    padding: 12px 16px
---

## Overview

Calm, clear task management interface that emphasizes focus, state visibility, and trustworthy actions.

## Colors

Blue primary actions distinguish task changes. Neutral surfaces separate task groups. Error red is reserved for actionable failures and never replaces explanatory text.

## Typography

Inter provides readable task content and compact labels. Status labels must remain legible at normal and enlarged text sizes.

## Layout

Use an 8px spacing rhythm, 24px container padding, and responsive layouts that preserve task title visibility on small screens.

## Elevation & Depth

Use subtle surface contrast rather than decorative shadows. Destructive confirmation states must remain visually distinct without relying on color alone.

## Shapes

Use 8px control and card radius. Keep hit areas large enough for keyboard and touch interaction.

## Components

Apply component tokens consistently to task actions, status indicators, forms, and error messages. Every state must have a non-color indicator.

## Do's and Don'ts

- Do preserve accessible contrast and visible focus.
- Do make task state and action outcomes clear.
- Do not use color as the only state or error signal.
- Do not introduce one-off spacing or control styles without updating tokens.

## Validation and Export

```bash
npx @google/design.md lint DESIGN.md
npx @google/design.md export --format json-tailwind DESIGN.md > tailwind.theme.json
```
