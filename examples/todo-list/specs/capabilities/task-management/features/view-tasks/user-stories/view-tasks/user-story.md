---
type: urn:open-specs:user-story
title: View Accessible Tasks
description: Authenticated task user views tasks they are permitted to access.
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

As a [Task user](/examples/todo-list/specs/personas/task-user/persona.md), I want to view my tasks, so that I know what work remains.

## Context

Feature: [View and filter tasks](/examples/todo-list/specs/features/task-management/view-tasks/feature.md).

## Acceptance Criteria

### Scenario: Tasks exist

Given an authenticated user with accessible tasks
When the user views tasks
Then the product returns those tasks with their state

### Scenario: No accessible tasks

Given an authenticated user without accessible tasks
When the user views tasks
Then the product returns an empty result without exposing other tasks

## Errors and Boundaries

### Error: Unauthenticated access

Given an unauthenticated user
When the user requests accessible tasks
Then the product returns a 401 Unauthorized error without revealing task data
