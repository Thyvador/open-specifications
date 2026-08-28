---
type: urn:open-specs:user-story
title: Create a Task
description: Authenticated task user creates a task with a title.
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

As a [Task user](/examples/todo-list/specs/personas/task-user/persona.md), I want to create a task, so that I can record work before forgetting it.

## Context

Feature: [Create tasks](/examples/todo-list/specs/features/task-management/create-tasks/feature.md).

## Acceptance Criteria

### Scenario: Valid task

Given an authenticated user and a non-blank title
When the user creates the task
Then the product creates an owned task with `Todo` status and confirms it

### Scenario: Blank title

Given an authenticated user
When the user submits a blank title
Then the product rejects the request and creates no task

## Errors and Boundaries

### Error: Unauthenticated access

Given an unauthenticated user
When the user submits a task
Then a 401 Unauthorized error is returned

### Error: Unexpected task creation failure

Given an authenticated user
When the user submits a task and an unexpected error occurs
Then a 500 Internal Server Error is returned and task creation is not reported as successful
