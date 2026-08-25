---
type: urn:open-specs:doc
title: Define Intent
description: Guide for defining product WHY and WHAT through root causes, behavior-driven personas, capabilities, constraints, and measurable PRD outcomes.
tags:
  - process
  - intent
  - requirements
  - capabilities
generated:
  by: agent:opencode
  at: 2026-08-20T00:00:00Z
status: draft
---

## Purpose

Define why a product should exist and what it should do before deciding how to build it. Intent turns observed problems into a shared, testable statement of user value, business value, product behavior, scope, constraints, and expected outcomes.

## Stage Focus

The team focuses on WHY and WHAT:

- WHY: the problem, root cause, affected people, value, goals, and measurable outcomes.
- WHAT: product capabilities, expected behavior, scope, non-goals, and non-functional constraints.

Do not decide HOW during this stage. Architecture, technology, APIs, data models, UI components, implementation workflows, and deployment design belong to design stages.

## Inputs

- Reported problem, opportunity, or product hypothesis
- Research, analytics, support data, interviews, and domain evidence
- Existing product goals, constraints, personas, and domain language
- Known legal, security, accessibility, performance, reliability, and operational constraints

## Process

1. Investigate the observable problem and root cause.
2. Identify people whose behavior and outcomes are affected.
3. Describe behavior-driven personas from evidence.
4. Define product capabilities, scope, non-goals, and constraints.
5. Capture intent in the PRD.
6. Define measurable outcomes, baselines, targets, and guardrails.
7. Review intent with product, design, engineering, testing, security, and operations.

## Core Concepts

### Define the Product "WHY"

The WHY explains the meaningful change the product exists to create. It connects an observed problem to affected people, the outcome they need, and the value that outcome provides. It is not a feature or implementation choice.

Start here because later decisions depend on this context. A clear WHY helps the team distinguish problems from symptoms, evaluate competing solutions, set boundaries, and measure impact. Without it, teams can build the wrong thing efficiently or let technical preferences define the product accidentally.

#### Start with the observable problem

Describe what happens, who experiences it, when it happens, and what consequence follows. Avoid solution language such as "users need a dashboard". Include:

- Affected actor or segment
- Situation or trigger
- Observable behavior or failure
- User or business consequence
- Evidence, source, sample, and date

Example:

> New administrators abandon workspace setup during permission configuration. In five moderated sessions and 18% of recent onboarding sessions, administrators could not determine which permissions were required, causing setup to remain incomplete.

#### Separate symptoms from causes

Use repeated why-questions to move from a visible symptom to a condition supported by evidence. Label statements as observed, reported, inferred, or assumed, and record competing explanations when evidence is weak.

#### Define the problem boundary

State what is included and excluded. Identify adjacent problems, users, and outcomes that are deferred. Record constraints such as regulatory obligations, migration needs, accessibility requirements, latency targets, and operational ownership.

### Define the Product "WHAT"

Describe product behavior through capabilities without describing screens, components, services, algorithms, or implementation sequences. A capability is a substantial product outcome or behavioral area that groups several related features. It is broader than a feature and may span multiple releases.

For each capability, document it in `/specs/capabilities/<capability>/capability.md` and map it to several related features. Document:

- Capability: what the product enables.
- Primary actor: who uses or benefits.
- Trigger or context: when it matters.
- Expected behavior: what the product allows, prevents, or communicates.
- User or business outcome: why it exists.
- Priority: must, should, could, or deferred.

Use this hierarchy for traceability:

```text
Product intent
└── Capability
    └── Feature
        └── User story
            └── Acceptance criteria
```

Capability documents remain product-facing and implementation-neutral. Detailed behavior belongs in linked feature documents created during design.

Define non-goals explicitly. State which related capabilities, users, workflows, and outcomes are out of scope.

Capture non-functional constraints as measurable product expectations:

- Security and privacy
- Accessibility
- Performance
- Reliability and recovery
- Compliance and retention
- Platform and integration compatibility
- Operability and service-level objectives

"95% of standard requests complete within two seconds" is a WHAT constraint. "Use a particular cache" is HOW and does not belong here.

### Build Behavior-Driven Personas

Personas explain behavior relevant to product decisions. Build them from research, support data, analytics, interviews, workflow observation, and domain knowledge. Record role, desired outcomes, triggers, current behavior, decisions, information needs, blockers, constraints, success criteria, evidence, confidence, and review date.

Create separate personas only when goals, workflows, constraints, or success criteria materially differ. Identify primary, secondary, indirect, and negatively affected users. Use the [persona template](/docs/software-specification/1-intent/templates/persona-template.md).

### Capture Intent in the PRD

Write the product-level document at [PRD](/specs/PRD.md) using the [PRD template](/docs/software-specification/1-intent/templates/prd-template.md). The PRD should describe outcomes and boundaries, not implementation details.

The PRD should include Summary, Problem and Root Cause, Goals, Capabilities, Non-Goals, Users and Personas, User Outcomes and Behaviors, Requirements, Constraints and Non-Functional Requirements, Success Metrics, Risks and Open Questions, and Rollout and Review.

Requirements must be observable and traceable. For example:

> `REQ-001`: When an administrator selects a workflow, the product shows permissions required for that workflow and explains each permission in plain language.

### Define Measurable Outcomes

For every primary metric, document its name, formula, unit, baseline, target, population, measurement window, source, owner, cadence, decision rule, and guardrails. Use leading indicators for behavior change and lagging indicators for broader outcomes. Avoid vanity metrics unless their causal relationship to the outcome is explicit.

## Expected Outcome

Intent is ready for design when the team can explain WHY the product matters and WHAT it should and should not do without deciding HOW it will be built. The intent package contains validated or explicitly marked assumptions for:

- Root cause and evidence
- Personas and affected behaviors
- PRD goals and measurable outcomes
- Capabilities and related features
- Scope and non-goals
- Non-functional constraints
- Risks, open questions, and rollout boundaries

## Artifacts

| Artifact | Path | Required when | Purpose |
| --- | --- | --- | --- |
| Product requirements | [PRD](/specs/PRD.md) | Every product or initiative | Captures WHY, WHAT, scope, constraints, and metrics |
| Persona profile | [persona profile](/specs/personas/<persona>/persona.md) | User behavior affects intent | Documents evidence-based user behavior and outcomes |

## Do

- Start from evidence and observable problems.
- Separate root causes from symptoms.
- Define user and business outcomes before capabilities.
- State scope, non-goals, and constraints explicitly.
- Make requirements and metrics measurable.
- Link personas and requirements to canonical documents.
- Keep assumptions and confidence visible.

## Do Not

- Do not begin with a proposed solution.
- Do not specify UI components, architecture, technology, APIs, data models, algorithms, implementation details, deployment topology, or technical workflows.
- Do not convert an unvalidated solution hypothesis into a requirement.
- Do not hide scope decisions in feature descriptions.
- Do not use activity or vanity metrics as proof of product impact.
- Do not silently change frozen intent during development or release.

## Templates

- [Persona template](/docs/software-specification/1-intent/templates/persona-template.md)
- [PRD template](/docs/software-specification/1-intent/templates/prd-template.md)
- [Capability template](/docs/software-specification/1-intent/templates/capability-template.md)

## Review Checklist

- Root cause is separated from symptom and supported by evidence.
- Assumptions and confidence levels are explicit.
- Personas describe behaviors, triggers, constraints, and outcomes.
- PRD defines WHY and WHAT without HOW decisions.
- Capabilities group several related features and map to PRD outcomes.
- Capabilities, non-goals, requirements, and constraints are clear.
- Metrics have baseline, target, population, time window, source, and owner.
- Guardrails cover material user, business, security, accessibility, and operational risks.
- Product, design, engineering, testing, security, and operations reviewed the intent.

## Lifecycle and Change Control

The PRD is living during discovery. Teams may iterate as evidence improves. When development or release begins, freeze the relevant PRD content and semantic version. The frozen PRD is the reference for implementation, testing, and release decisions.

Do not silently change frozen intent. Record new findings as follow-up discovery or explicit change decisions. Reopen the PRD in a later discovery cycle when product state, user needs, evidence, or goals evolve.

Use `MAJOR.MINOR.PATCH`: MAJOR for breaking changes, MINOR for additive feature or capability changes, and PATCH for corrections that do not change intended behavior or scope.

## Source

See [Define intent](/docs/specifying-software.md#1-define-intent).
