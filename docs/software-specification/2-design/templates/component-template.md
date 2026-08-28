---
type: urn:open-specs:component
title: Component Template
description: Template for documenting a technical component, its boundaries, responsibilities, dependencies, and contracts.
tags:
  - design
  - component
  - template
generated:
  by: agent:opencode
  at: 2026-08-20T00:00:00Z
status: draft
---

## Purpose

Describe the component's purpose and the product outcomes it supports.

## Responsibilities

- State what this component owns.
- State what it explicitly does not own.

## Ownership

Identify the owning team, accountable role, operational owner, and escalation path.

## Boundaries

Describe the component's functional and technical boundary, including explicit non-responsibilities.

## Consumers

Identify direct consumers, supported use cases, and compatibility expectations.

## Dependencies

List upstream and downstream dependencies, dependency purpose, availability expectations, and failure impact.

## Data Ownership

Describe data owned, accessed, created, modified, retained, or exported by the component.

## Security and Trust Boundaries

Describe authentication, authorization, sensitive-data handling, and trust-boundary crossings.

## Interfaces

Link [API guidance](/docs/software-specification/2-design/templates/api-template.md) and an OpenAPI contract when synchronous HTTP interfaces exist. Link [event guidance](/docs/software-specification/2-design/templates/event-template.md) and an AsyncAPI contract when asynchronous events exist. Omit contracts when no such interface exists.

## State and Data

Describe relevant state, lifecycle, consistency expectations, and data transitions.
