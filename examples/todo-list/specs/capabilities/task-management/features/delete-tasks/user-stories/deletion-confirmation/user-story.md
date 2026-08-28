---
type: urn:open-specs:user-story
title: Confirm Task Deletion
description: Task user confirms deletion before an accessible task is permanently removed.
tags:
  - example
  - user-story
  - tasks
  - deletion
generated:
  by: agent:opencode
  at: 2026-08-26T00:00:00Z
status: draft
---

## Story

As a [Task user](/examples/todo-list/specs/personas/task-user/persona.md), I want to confirm before deleting a task, so that I do not remove it accidentally.

## Context

Feature: [Delete tasks](/examples/todo-list/specs/capabilities/task-management/features/delete-tasks/feature.md).

## Acceptance Criteria

### Scenario: Confirmation is required

Given an authenticated user authorized for a task
When the user starts the deletion action
Then the product asks the user to confirm deletion and does not remove the task yet

### Scenario: User confirms deletion

Given the deletion confirmation is shown for an accessible task
When the user confirms deletion
Then the product removes the task and confirms successful deletion

### Scenario: User cancels deletion

Given the deletion confirmation is shown for an accessible task
When the user cancels deletion
Then the product keeps the task unchanged and returns the user to task management

### Scenario: Confirmation identifies task

Given the deletion confirmation is shown
When the user reviews the confirmation
Then the product identifies the task clearly and communicates that deletion cannot be undone

## Errors and Boundaries

### Error: Unauthorized deletion confirmation

Given an authenticated user who is not authorized for a task
When the user attempts to start deletion
Then the product rejects the request without revealing task existence

### Error: Deletion failure after confirmation

Given an authenticated user authorized for a task
When the user confirms deletion and the deletion cannot be completed
Then the product reports the failure and does not claim that the task was deleted

### Error: Stale task confirmation

Given a deletion confirmation was opened for a task that is no longer available
When the user confirms deletion
Then the product rejects the request and communicates that the task could not be deleted

## Notes

Deletion must occur only after explicit confirmation. Starting or cancelling the confirmation must never modify the task.
