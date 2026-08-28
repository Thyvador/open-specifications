---
type: urn:open-specs:capability
title: Task Management Capability
description: Capability enabling authenticated users to maintain tasks and understand their current state.
tags:
  - example
  - capability
  - tasks
generated:
  by: agent:opencode
  at: 2026-08-25T00:00:00Z
status: draft
---

## Intent Traceability

Parent document: [Task Management PRD](/examples/todo-list/specs/PRD.md).

Supports `REQ-001` through `REQ-005` and the task activation, completion, and recovery metrics.

## Purpose and Outcome

Users can maintain a trustworthy list of work, understand task state, and return to unfinished work without reconstructing it from other tools.

## Supported Personas

- [Task user](/examples/todo-list/specs/personas/task-user/persona.md)
- [Workspace administrator](/examples/todo-list/specs/personas/workspace-admin/persona.md)

## Scope

- Create a task.
- View accessible tasks.
- Update task details and state.
- Mark a task complete.
- Delete a task when permitted.

## Non-Goals

- Scheduling, reminders, dependencies, or automated prioritization.
- Complex project planning.
- Anonymous task creation or access.

## Related Features

This capability is decomposed into several feature documents:

- [Create tasks](/examples/todo-list/specs/features/task-management/create-tasks/feature.md)
- [View and filter tasks](/examples/todo-list/specs/features/task-management/view-tasks/feature.md)
- [Update task state](/examples/todo-list/specs/features/task-management/update-tasks/feature.md)
- [Delete tasks](/examples/todo-list/specs/features/task-management/delete-tasks/feature.md)

## Expected Behavior

An authenticated user can create and manage tasks they are authorized to access. The product makes task state and the result of each requested change clear.

## Constraints and Dependencies

Task access follows the product's authentication and authorization rules. Task changes must preserve user trust by communicating success or failure. Detailed technical dependencies are deferred to design.

## Success Metrics

See the task activation, completion, and recovery metrics in the [PRD](/examples/todo-list/specs/PRD.md#success-metrics).

## Lifecycle and Priority

Priority: must. This capability is part of the initial release scope and may expand in later discovery cycles.
