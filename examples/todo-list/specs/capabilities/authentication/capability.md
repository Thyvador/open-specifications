---
type: urn:open-specs:capability
title: Authentication Capability
description: Capability enabling users to establish and maintain a protected product identity.
tags:
  - example
  - capability
  - authentication
generated:
  by: agent:opencode
  at: 2026-08-25T00:00:00Z
status: draft
---

## Intent Traceability

Parent document: [Task Management PRD](/examples/todo-list/specs/PRD.md).

## Purpose and Outcome

Users can establish a consistent identity, access protected task information, end their session, and recover access when needed.

## Supported Personas

- [Task user](/examples/todo-list/specs/personas/task-user/persona.md)
- [Workspace administrator](/examples/todo-list/specs/personas/workspace-admin/persona.md)

## Scope

- Register an account.
- Authenticate and sign out.
- Maintain an authenticated session.
- Recover access according to account policy.
- Prevent unauthenticated access to protected task information.

## Non-Goals

- Enterprise identity administration.
- Single sign-on integrations in the initial release.
- Delegated administration of all account security settings.

## Related Features

The design stage should create several feature documents, including:

- [Register an account](/examples/todo-list/specs/features/authentication/register/feature.md)
- [Sign in and sign out](/examples/todo-list/specs/features/authentication/session/feature.md)
- [Recover account access](/examples/todo-list/specs/features/authentication/recovery/feature.md)

## Expected Behavior

Only authenticated and authorized users can access protected task information. Authentication and recovery outcomes are clear without revealing whether protected account information exists.

## Constraints and Dependencies

Security, privacy, accessibility, account-recovery, and operational constraints in the [PRD](/examples/todo-list/specs/PRD.md) apply. Technical identity and session decisions are deferred to design.

## Success Metrics

See the authentication failure-rate metric and security guardrails in the [PRD](/examples/todo-list/specs/PRD.md#success-metrics).

## Lifecycle and Priority

Priority: must. Authentication policy must be reviewed with security and operations before the release scope is frozen.
