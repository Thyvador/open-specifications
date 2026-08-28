---
type: urn:open-specs:feature
title: Create Tasks
description: Allows authenticated users to record new tasks with a title and optional description.
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

Capability: [Task management](/examples/todo-list/specs/capabilities/task-management/capability.md). 

Parent: [PRD](/examples/todo-list/specs/PRD.md).

## Purpose

Enable a task user to capture work before it is forgotten.

## Scope

The authenticated user submits a title and optional description. The product creates a task owned by that user with an initial `Todo` status and confirms the result.

## Actors and Preconditions

The actor is an authenticated task user. A valid title is required.

## Behavior and Flows

Valid creation succeeds. Blank titles are rejected. Unauthenticated requests are rejected without creating data. Failure is communicated without losing an already confirmed task.

## Requirements

See [create-task story](/examples/todo-list/specs/capabilities/task-management/features/create-tasks/user-stories/create-task/user-story.md).

## Success Signals

Contributes to task activation rate in the [PRD](/examples/todo-list/specs/PRD.md#success-metrics).
