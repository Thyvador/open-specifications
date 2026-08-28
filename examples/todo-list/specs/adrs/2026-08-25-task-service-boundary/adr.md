---
type: urn:open-specs:adr
title: Task Service Boundary
description: Decision record for separating task lifecycle behavior from authentication responsibilities.
tags:
  - example
  - adr
  - architecture
generated:
  by: agent:opencode
  at: 2026-08-25T00:00:00Z
status: draft
---

## Context

The product needs protected task CRUD behavior while authentication must remain reusable and independently governed.

## Options Considered

- Combine identity and task behavior in one component.
- Separate authentication identity from task lifecycle and authorization behavior.

## Decision

Separate authentication from the task service. Authentication establishes identity; the task service authorizes task operations and owns task data.

## Consequences

Task ownership is explicit and task behavior remains focused. Requests require a dependable identity boundary and cross-component authorization tests.

## Traceability

Related components: [Task service](/examples/todo-list/specs/components/task-service/component.md). Related capabilities: [Task management](/examples/todo-list/specs/capabilities/task-management/capability.md), [Authentication](/examples/todo-list/specs/capabilities/authentication/capability.md).
