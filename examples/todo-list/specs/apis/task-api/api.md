---
type: urn:open-specs:api
title: Task API Guidance
description: Human guidance for the synchronous task management API.
tags:
  - example
  - api
  - tasks
generated:
  by: agent:opencode
  at: 2026-08-25T00:00:00Z
status: draft
---

## Purpose

Expose authenticated task lifecycle behavior. Canonical contract: [openapi.yaml](/examples/todo-list/specs/apis/task-api/openapi.yaml).

## Consumers and Authentication

Consumers are authenticated product clients. Requests carry authenticated actor context.

## Operations

Support creating, listing, retrieving, updating, and deleting tasks. Task status uses ontology-defined values.

## Errors and Compatibility

Invalid input, missing identity, denied access, and unavailable service produce documented safe errors. The API must not reveal inaccessible task existence.

## Traceability

Component: [Task service](/examples/todo-list/specs/components/task-service/component.md). Rules: [Task management rules](/examples/todo-list/specs/features/task-management/rules.md).
