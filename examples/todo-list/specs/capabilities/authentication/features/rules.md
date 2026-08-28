---
type: urn:open-specs:feature-rules
title: Authentication Rules
description: Business rules governing identity, protected access, and safe authentication failures.
tags:
  - example
  - rules
  - authentication
generated:
  by: agent:opencode
  at: 2026-08-25T00:00:00Z
status: draft
---

## Scope

Applies to the [authentication capability](/examples/todo-list/specs/capabilities/authentication/capability.md).

## Invariants

- Protected task data requires authenticated and authorized access.
- Credentials are never returned in user-visible responses.
- Failed authentication does not disclose protected account existence.

## Rules

### RULE-001: Protected access

Given no valid authenticated session, the product must deny protected task access.

### RULE-002: Safe failure

Given invalid credentials or recovery data, the product must provide a safe failure without identifying which protected account detail exists.
