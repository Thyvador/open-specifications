---
type: urn:open-specs:feature
title: Update Task State
description: Allows authorized users to update task details and state as work progresses.
tags:
  - example
  - feature
  - tasks
generated:
  by: agent:opencode
  at: 2026-08-25T00:00:00Z
status: draft
---

## Intent Traceability

Capability: [Task management](/examples/todo-list/specs/capabilities/task-management/capability.md). Supports `REQ-003` and `REQ-004`.

## Purpose

Keep task information and progress accurate.

## Scope

An authorized user can update title, description, ownership where permitted, and status. Status values are defined by the domain ontology.

## Actors and Preconditions

The actor is authenticated and authorized for the task. Updates must target an existing task.

## Behavior and Flows

Valid changes are persisted and confirmed. Invalid state changes and denied access are rejected without partial updates.

## Requirements

See [update-task stories](/examples/todo-list/specs/features/task-management/update-tasks/user-stories/).
