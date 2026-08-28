---
type: urn:open-specs:feature
title: View and Filter Tasks
description: Allows authenticated users to find tasks they are permitted to access and understand their state.
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

Capability: [Task management](/examples/todo-list/specs/capabilities/task-management/capability.md). Supports `REQ-002` and task recovery.

## Purpose

Help users find current and completed work without reconstructing it from other tools.

## Scope

An authenticated user can view accessible tasks and distinguish `Todo`, `In progress`, and `Completed` states. Empty results are clearly represented.

## Actors and Preconditions

The actor is an authenticated task user. Access is limited to tasks permitted by authorization rules.

## Behavior and Flows

The product returns accessible tasks. It does not reveal whether inaccessible tasks exist.

## Requirements

See [view-task stories](/examples/todo-list/specs/features/task-management/view-tasks/user-stories/).

## Success Signals

Contributes to task recovery rate in the [PRD](/examples/todo-list/specs/PRD.md#success-metrics).
