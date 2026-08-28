---
type: urn:open-specs:feature-rules
title: Task Management Rules
description: Business rules governing task ownership, state, access, and changes.
tags:
  - example
  - rules
  - tasks
generated:
  by: agent:opencode
  at: 2026-08-25T00:00:00Z
status: draft
---

## Scope

Applies to the [task management capability](/examples/todo-list/specs/capabilities/task-management/capability.md) and its features. Terms use the [task ontology](/examples/todo-list/specs/language/todo-ontology.ttl).

## Invariants

- Every task has exactly one owner.
- Every task has exactly one valid status.
- A task is accessible only to an authorized user.
- A rejected change does not partially update a task.

## Rules

### RULE-001: Initial status

Given a newly created task, the product must assign `Todo` status.

### RULE-002: Ownership

Given a task creation request, the product must assign ownership to the authenticated actor unless an authorized ownership policy permits another owner.

### RULE-003: Protected access

Given an unauthenticated or unauthorized request, the product must not reveal or change protected task data.

### RULE-004: Valid status

Given a status change, the product must accept only ontology-defined statuses.
