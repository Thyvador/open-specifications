---
type: urn:open-specs:prd
title: Product Requirements Document Template
description: Template for capturing product intent, users, outcomes, constraints, requirements, and measurable success metrics.
version: 1.2.0
tags:
  - product
  - requirements
  - template
generated:
  by: agent:opencode
  at: 2026-08-20T00:00:00Z
status: draft
---

## Summary

State the problem, target users, and intended outcome in one paragraph.

## Problem and Root Cause

Describe the observable problem, evidence, validated root cause, and remaining assumptions.

## Goals

State outcomes this product or initiative will achieve.

## Non-Goals

State related outcomes and capabilities explicitly excluded from scope.

## Users and Personas

Link primary and secondary personas, for example [Workspace Administrator](/specs/personas/workspace-admin/persona.md).

## Capabilities

Describe substantial product outcomes or behavioral areas. Each capability must group several related features and remain implementation-neutral. Create a linked [capability document](/specs/capabilities/<capability>/capability.md) for each capability.

- [Capability name](/specs/capabilities/<capability>/capability.md)
- [Another capability name](/specs/capabilities/<capability>/another-capability.md)

Capabilities may span multiple releases. Detailed feature behavior belongs in design-stage feature documents.

## Constraints and Non-Functional Requirements

Capture legal, security, accessibility, performance, reliability, platform, data, and operational constraints.

## Success Metrics

For each metric, define its formula, baseline, target, population, measurement window, data source, owner, cadence, decision rule, and guardrails.

| Metric | Definition | Baseline | Target | Window | Source | Owner |
| --- | --- | ---: | ---: | --- | --- | --- |
| Example metric | Define the measured outcome and denominator | Value | Target | Period | Data source | Owner |

## Risks and Open Questions

Record uncertainty, competing explanations, dependencies, and decisions still required.

## Rollout and Review

Describe rollout boundaries, experiment or release approach, review date, and criteria for continuing, changing, or stopping the initiative.
