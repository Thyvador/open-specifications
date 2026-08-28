---
type: urn:open-specs:component
title: Task Service Component
description: Component responsible for task lifecycle behavior, ownership, and task access decisions.
tags:
  - example
  - component
  - tasks
generated:
  by: agent:opencode
  at: 2026-08-25T00:00:00Z
status: draft
---

## Purpose

Support task management outcomes defined by the [task management capability](/examples/todo-list/specs/capabilities/task-management/capability.md).

## Responsibilities

- Create, read, update, complete, and delete tasks.
- Enforce task ownership and access rules.
- Maintain valid task states.

The component does not own account credentials or authentication policy.

## Ownership

Product engineering owns the component. Operations owns availability and incident response.

## Boundaries

The component owns task behavior and task data lifecycle. Authentication establishes identity; this component authorizes task access.

## Consumers

The product client and authenticated task workflows consume this component.

## Dependencies

- Authentication component for actor identity.
- Task data store for task persistence.

## Data Ownership

Owns task title, description, owner, status, and lifecycle timestamps.

## Security and Trust Boundaries

Requests cross from authenticated clients into the protected task boundary. Every operation requires identity and authorization evaluation.

## Interfaces

The synchronous interface is described by the [Task API guidance](/examples/todo-list/specs/apis/task-api/api.md) and [OpenAPI contract](/examples/todo-list/specs/apis/task-api/openapi.yaml). No asynchronous event contract is defined for this example.

## State and Data

Task states are `Todo`, `InProgress`, and `Completed`, defined by the [task ontology](/examples/todo-list/specs/language/todo-ontology.ttl).

## Failure and Operations

Reject invalid or unauthorized changes without partial updates. Monitor task-change failures, access denials, and latency.

## Decisions and Traceability

See [task service ADR](/examples/todo-list/specs/adrs/2026-08-25-task-service-boundary/adr.md).
