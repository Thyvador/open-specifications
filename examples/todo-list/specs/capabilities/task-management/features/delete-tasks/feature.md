---
type: urn:open-specs:feature
title: Delete Tasks
description: Allows authorized users to remove tasks that are no longer relevant.
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

Capability: [Task management](/examples/todo-list/specs/capabilities/task-management/capability.md). Supports `REQ-005`.

## Purpose

Allow users to remove obsolete accessible tasks.

## Scope

An authorized user can delete an accessible task. The product confirms deletion and does not expose inaccessible task existence.

## Actors and Preconditions

The actor is authenticated and authorized for the task.

## Behavior and Flows

Deletion is atomic. Denied or missing targets produce a safe failure response.

## Requirements

See [delete-task story](/examples/todo-list/specs/capabilities/task-management/features/delete-tasks/user-stories/delete-task/user-story.md) and [deletion confirmation story](/examples/todo-list/specs/capabilities/task-management/features/delete-tasks/user-stories/deletion-confirmation/user-story.md).
