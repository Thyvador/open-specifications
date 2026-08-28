---
type: urn:open-specs:user-story
title: Delete an Accessible Task
description: Authorized task user deletes a task that is no longer relevant.
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

As a [Task user](/examples/todo-list/specs/personas/task-user/persona.md), I want to delete an obsolete task, so that my list remains trustworthy.

## Context

Feature: [Delete tasks](/examples/todo-list/specs/features/task-management/delete-tasks/feature.md).

## Acceptance Criteria

### Scenario: Authorized deletion

Given an authenticated user authorized for a task
When the user deletes it
Then the product removes it and confirms deletion

### Scenario: Unauthorized deletion

Given an authenticated user not authorized for a task
When the user attempts deletion
Then the product rejects it without revealing task existence

## Errors and Boundaries

### Error: Unauthorized deletion

Given an authenticated user who is not authorized for a task
When the user attempts to delete it
Then the product rejects the request without revealing task existence

### Error: Deletion failure

Given an authenticated user authorized for a task
When deletion cannot be completed
Then the product returns an error and does not report success while the task remains
