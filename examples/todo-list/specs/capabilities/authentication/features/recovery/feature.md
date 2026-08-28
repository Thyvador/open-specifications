---
type: urn:open-specs:feature
title: Recover Account Access
description: Allows an account holder to recover access according to product security policy.
tags:
  - example
  - feature
  - authentication
generated:
  by: agent:opencode
  at: 2026-08-25T00:00:00Z
status: draft
---

## Intent Traceability

Capability: [Authentication](/examples/todo-list/specs/capabilities/authentication/capability.md). Supports `REQ-007` and authentication guardrails.

## Purpose

Restore legitimate access without exposing account information or weakening security.

## Scope

An account holder can request and complete recovery according to the approved account policy.

## Actors and Preconditions

The actor has an account or believes they have one. Recovery responses must not disclose protected account existence.

## Behavior and Flows

Requests, invalid recovery attempts, expiry, and successful recovery are handled according to security policy.
