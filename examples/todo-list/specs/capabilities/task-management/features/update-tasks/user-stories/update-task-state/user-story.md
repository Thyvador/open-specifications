---
type: urn:open-specs:user-story
title: Update Task State
description: Authenticated task user updates an accessible task and its progress state.
tags:
  - example
  - user-story
  - tasks
generated:
  by: agent:opencode
  at: 2026-08-25T00:00:00Z
status: draft
---

## Story

As a [Task user](/examples/todo-list/specs/personas/task-user/persona.md), I want to update task state, so that my task list reflects progress.

## Context

Feature: [Update task state](/examples/todo-list/specs/features/task-management/update-tasks/feature.md).

## Acceptance Criteria

### Scenario: Valid state change

Given an authenticated user authorized for a task
When the user changes its state to `Completed`
Then the product persists and confirms the new state

### Scenario: Unauthorized task

Given an authenticated user not authorized for a task
When the user attempts an update
Then the product rejects it without changing the task

## Errors and Boundaries

### Error: Unknown task status

Given an authenticated user authorized for a task
When the user submits an unknown task status
Then the product rejects the request with a validation error and does not change the task

### Error: Invalid task identifier

Given an authenticated user
When the user attempts to update a task with an invalid identifier
Then the product rejects the request with a not-found error and does not reveal protected task data
