---
type: urn:open-specs:feature-rules
title: Business Rules Template
description: Template for precise business rules, invariants, decisions, and edge-case behavior.
tags:
  - design
  - rules
  - template
generated:
  by: agent:opencode
  at: 2026-08-20T00:00:00Z
status: draft
---

## Scope

Link the feature, PRD requirement, and affected language terms.

## Invariants

- State values that must always remain true.

## Priorities and Conflicts

Explain rule precedence when rules conflict.

## Rules

### RULE-001: [Name]

#### Statement

Given [precondition] When [condition], the product must [observable decision or behavior].

#### Example
<!-- Optional section: when rule need example. -->

Provide valid, invalid, boundary, and conflicting examples.

#### Error
<!-- Optional section: when rule outcome is an error, add error description. -->

```yaml
http_status: <HTTP status>
type: <uri>
title: <HUman readable title>
```
