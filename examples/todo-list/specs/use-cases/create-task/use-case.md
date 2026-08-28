---
type: urn:open-specs:use-case
title: Create Task Use Case
description: End-to-end interaction for creating an authenticated user's task.
tags:
  - example
  - use-case
  - tasks
generated:
  by: agent:opencode
  at: 2026-08-25T00:00:00Z
status: draft
---

## Goal and Actors

The task user records new work. The participating components are the [authentication service](/examples/todo-list/specs/components/auth-service/component.md) and [task service](/examples/todo-list/specs/components/task-service/component.md). Internal API, service, and database participants are grouped inside their owning component boxes.

## Preconditions and Trigger

The user is authenticated and submits a non-blank task title.

## Main Success Scenario

1. User submits task data.
2. Task service validates identity and input through the authentication service.
3. Task service creates an owned task with `Todo` status.
4. Product confirms the created task.

## Sequence Diagram

```mermaid
sequenceDiagram
    actor User
    box rgb(112, 164, 216) Task Service
      participant TaskApi as API
      participant Service as Service
      participant Store@{ "type" : "database", "alias": "Database"}
    end
    box rgb(57, 175, 86) Authentication Service
      participant AuthService as Service
    end

    User->>+TaskApi: Submit title and description
    TaskApi->>+AuthService: Validate authentication
    break when token is not valid
      AuthService-->>TaskApi: Unauthorized
      TaskApi-->>User: Return Unauthorized error
    end
    AuthService-->>-TaskApi: Authenticated identity
    alt when task data is incomplete
      TaskApi-->>User: Return Bad Request error
    else when task data is valid
      TaskApi->>+Service: Create task for authenticated user
      Service->>+Store: Persist owned task with Todo status
      break when database returns an error
        Store-->>Service: Persistence error
        Service-->>TaskApi: Creation failure
        TaskApi-->>User: Return Internal Server Error
      end
      Store-->>-Service: Created task
      Service-->>-TaskApi: Created task
      TaskApi-->>-User: Confirm task creation
    end

```

## Postconditions

One accessible task exists with the authenticated user as owner and `Todo` status.

## Traceability

Feature: [Create tasks](/examples/todo-list/specs/features/task-management/create-tasks/feature.md). Rules: [Task management rules](/examples/todo-list/specs/features/task-management/rules.md).
