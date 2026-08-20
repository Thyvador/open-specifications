---
type: urn:open-specs:doc
title: Define Intent
description: Guide for defining product WHY and WHAT through root causes, behavior-driven personas, high-level capabilities, constraints, and measurable PRD outcomes.
tags:
  - process
  - intent
  - requirements
generated:
  by: agent:opencode
  at: 2026-08-20T00:00:00Z
status: draft
---

## Purpose

Define why a product should exist and what it should do before deciding how to build it. Intent work turns observed problems into a shared, testable statement of user value, business value, product behavior, scope, constraints, and expected outcomes.

The output is not a feature wish list. It is a decision record that helps product, design, engineering, testing, and operations answer three questions:

- Which problem matters, and for whom?
- What behavior or outcome should change?
- What should the product do and not do?
- How will we know whether the change worked?

> ℹ️ This step covers the WHY and WHAT only. It must not decide the HOW. Architecture, technology, APIs, data models, UI components, implementation workflows, and deployment design belong in later functional and technical design artifacts.

## Process

Complete intent definition in this order:

1. Investigate the root cause behind the reported problem.
2. Identify people whose behavior and outcomes are affected.
3. Describe the desired behavior using evidence-based personas.
4. Define high-level product capabilities, scope, non-goals, and non-functional constraints.
5. Capture the product intent and boundaries.
6. Set measurable outcome metrics and define how they will be observed.
7. Review the PRD with product, design, engineering, testing, and operations representatives.

> ℹ️ Do not begin with a proposed solution. Record solutions as hypotheses until the problem, users, desired outcomes, and product boundaries are clear.

## Define the Product "WHY"

<!-- TODO -->

### Start with the observable problem

Describe what currently happens, who experiences it, and what consequence follows. Avoid solution language such as "users need a dashboard" or "we should add an approval button." Prefer statements such as "support agents cannot identify failed payments before responding to customers, so resolution takes multiple contacts."

A useful problem statement contains:

- Affected actor or segment
- Situation or trigger
- Observable behavior or failure
- User or business consequence
- Evidence and evidence date

Example:

> New administrators abandon workspace setup during permission configuration. In five moderated sessions and 18% of recent onboarding sessions, administrators could not determine which permissions were required, causing setup to remain incomplete.

### Separate symptoms from causes

Use repeated why-questions to move from a visible symptom to a cause that the product can influence. Stop when the answer is supported by evidence and identifies a condition, not another restatement of the symptom.

Example chain:

1. Users do not finish workspace setup.
2. They stop at permission configuration.
3. They cannot tell which permissions are required for their chosen workflow.
4. Permission requirements are presented as an undifferentiated list with no workflow context.

The fourth statement is a plausible root cause because it identifies a specific information gap. Validate it before committing to a design. A cause is not established merely because it is reasonable.

### Record evidence and assumptions

Classify each important statement as one of:

- Observed: directly measured or witnessed.
- Reported: supplied by a user, customer, support agent, or stakeholder.
- Inferred: reasoned from available evidence.
- Assumed: not yet validated.

Record source, sample size, date, and limitations where practical. State competing explanations when evidence is weak. This prevents a loud anecdote from becoming an unchallenged requirement.

### Define the problem boundary

State what is included and excluded. Identify adjacent problems that may be valid but are not part of this intent. Include constraints such as regulatory obligations, platform limitations, migration needs, accessibility requirements, latency targets, and operational ownership.

## Define the Product "WHAT"

After establishing WHY, describe the product behavior at outcome and capability level. Explain what users and other stakeholders should be able to accomplish, without describing screens, components, services, algorithms, or implementation sequences.

### Describe high-level expected features

Each high-level feature should express a meaningful capability or user outcome. A feature statement should identify the actor, behavior, and value.

Good:

> Administrators can understand which permissions a selected workflow requires and configure access with confidence.

Weak:

> Add a permissions panel with checkboxes and a workflow dropdown.

The good statement defines WHAT the product enables. The weak statement prematurely defines UI components and belongs in design only after the underlying problem is validated.

For every expected feature, document:

- Capability: what the product enables.
- Primary actor: who uses or benefits from it.
- Trigger or context: when the capability matters.
- Expected behavior: what the product must allow, prevent, or communicate.
- User or business outcome: why the capability exists.
- Priority: must, should, could, or explicitly deferred.

### Define what the product should not do

Record non-goals and rejected scope explicitly. Include capabilities that may appear related but are intentionally excluded, user groups not served in this release, and outcomes that require a separate initiative. Non-goals prevent teams from turning assumptions into accidental requirements.

### Define non-functional constraints

Capture quality expectations and boundaries as product requirements, without prescribing their technical implementation. Include applicable constraints for:

- Security and privacy: protection expectations, access boundaries, and sensitive-data handling.
- Accessibility: required levels of access and inclusive use.
- Performance: response-time, throughput, or task-duration expectations.
- Reliability: availability, durability, recovery, and acceptable failure behavior.
- Compliance: legal, regulatory, audit, and retention obligations.
- Compatibility: supported platforms, devices, regions, or integrations.
- Operability: supportability, observability, ownership, and service-level objectives.

> ℹ️ State measurable thresholds where known. For example, "95% of standard requests complete within two seconds" is a WHAT constraint. "Use a particular cache" is HOW and does not belong here.

## Do Not Include "HOW" Decisions

Do not specify UI components, architecture, technology choices, APIs, data models, algorithms, implementation details, deployment topology, or technical workflows before validating the underlying problem. Do not convert an unvalidated solution hypothesis into a requirement.

Intent may describe user-visible behavior and quality constraints, but must remain implementation-neutral. Keep validated design decisions to functional design, technical design, API, component, event, or ADR artifacts. Link those artifacts back to the PRD once created.

## Build Behavior-Driven Personas

Personas should explain behavior relevant to product decisions, not create fictional biographies. Build them from research, support data, analytics, interviews, workflow observation, and domain knowledge. Avoid demographic details unless they affect the behavior or constraint being designed for.

### Describe behavior, not identity alone

Each persona should answer:

- What job or outcome is this person responsible for?
- What triggers their interaction with the product?
- What steps do they take today?
- What decisions do they make, and what information do they need?
- What frustrates or blocks them?
- What constraints shape their behavior?
- What does success look like from their perspective?

Use concrete behavioral language. "Checks account status before approving a refund" is useful. "Tech-savvy professional" is not.

### Keep personas distinct and actionable

Create a separate persona only when a group has materially different goals, workflows, constraints, or success criteria. If two groups behave the same way for this product decision, combine them. Identify the primary persona, secondary personas, and negatively affected or indirect users.

Do not treat personas as permanent truth. Add a confidence level, evidence sources, and a review date. Update or retire a persona when evidence changes.

### Persona template

Create each profile at `/specs/personas/<persona>/persona.md`. Use kebab-case for `<persona>`, such as `workspace-admin` or `support-agent`.

Use the [persona template](/docs/software-specification/1-intent/templates/) when creating a profile. Replace its placeholders with evidence from the product context.

## Capture Intent in the PRD

Write the product-level document at `/specs/PRD.md`. Keep it concise enough to review, but complete enough that downstream feature and technical documents can link back to a stable intent. The PRD should describe outcomes and boundaries; it should not prescribe implementation details that belong in design artifacts.

### PRD structure

Use the [PRD template](/docs/software-specification/1-intent/templates/prd-template.md) for `/specs/PRD.md`. Add `generated` when an agent or export process creates the file. Add `verified` only after an independent review or validation event.

### PRD lifecycle

The PRD is a living document during discovery. The team may iterate on its problem statement, personas, goals, capabilities, constraints, and metrics as research and validation produce new evidence.

When development or a release cycle begins, freeze the relevant PRD content and version. The frozen PRD is the reference for the current product state, implementation scope, acceptance tests, and release decisions. Do not silently change frozen intent during development or release; record new findings as follow-up discovery work or explicit change decisions.

After the cycle, reopen the PRD for the next discovery cycle when product state, user needs, evidence, or goals evolve. Maintain history so readers can distinguish current frozen intent from proposed future changes.

### PRD semantic version

Include a `version` field in PRD frontmatter using `MAJOR.MINOR.PATCH`, for example `version: 1.2.0`. Increment the version when discovery changes the PRD:

- MAJOR: breaking changes to product goals, scope, user outcomes, requirements, or compatibility expectations.
- MINOR: additive feature, capability, requirement, persona, or metric changes that preserve existing intent.
- PATCH: corrections, clarifications, or bug fixes that do not change intended behavior or scope.

Freeze the version together with PRD content for development and release. A release must identify which frozen PRD version it implements. Version changes during a frozen cycle require an explicit review of impact and release scope.

### Write testable requirements

Each requirement should describe one observable capability or constraint. Use identifiers when requirements need traceability, such as `REQ-001`. Avoid combining several behaviors in one sentence.

Good:

> `REQ-001`: When an administrator selects a workflow, the product shows permissions required for that workflow and explains each permission in plain language.

Weak:

> Make permissions easier and improve onboarding.

The good requirement can become acceptance criteria and can be traced to a persona, root cause, feature, and test. The weak requirement expresses an aspiration without observable behavior.

## Set Clear, Measurable Metrics

Metrics should measure outcomes, not activity. A count of shipped screens or completed tickets may describe output, but it does not prove that the underlying problem improved.

### Metric definition

For every primary metric, document:

- Name and precise definition
- Formula and unit
- Baseline value and baseline period
- Target value and target date or measurement window
- Population and segmentation
- Data source and instrumentation owner
- Reporting cadence
- Decision triggered by success or failure
- Guardrail metrics that prevent local optimization

Example:

| Metric | Definition | Baseline | Target | Window | Source | Owner |
| --- | --- | ---: | ---: | --- | --- | --- |
| Setup completion rate | Percentage of new administrators completing required setup within 24 hours of starting | 62% | 80% | 8 weeks after rollout | Onboarding events | Product analytics |
| Setup-related support contacts | Median setup-related contacts per new workspace in first 14 days | 0.8 | <= 0.4 | 8 weeks after rollout | Support system | Support operations |
| Permission overgrant rate | Percentage of configured workspaces granting permissions not required by selected workflow | 12% | <= 5% | Weekly | Audit events | Security |

Use one consistent denominator and define event names before implementation. A target without a baseline, population, or time window is not measurable.

### Choose leading and lagging indicators

Leading indicators show whether users encounter the intended behavior change, such as viewing workflow-specific permission explanations. Lagging indicators show whether the broader outcome improved, such as setup completion or support contact reduction. Use both when the lagging result takes time to observe.

### Define guardrails

Guardrails detect harm or trade-offs hidden by a primary metric. Examples include error rate, task duration, accessibility completion rate, security incidents, cancellation rate, infrastructure cost, and operator workload. A feature should not be considered successful if it improves one metric while violating a critical guardrail.

### Avoid vanity metrics

Page views, registrations, notification sends, and feature clicks are useful only when connected to a desired behavior or outcome. Explain the causal relationship or treat them as diagnostic signals rather than success criteria.

## Review Checklist

Before moving to design, confirm:

- Root cause is separated from symptom and supported by evidence.
- Assumptions and confidence levels are explicit.
- Primary and secondary personas describe behaviors, triggers, constraints, and outcomes.
- PRD defines WHY: problem, root cause, users, goals, and measurable outcomes.
- PRD defines WHAT: high-level capabilities, expected behaviors, non-goals, requirements, and non-functional constraints.
- PRD does not prematurely specify UI components, architecture, or other HOW decisions.
- PRD lifecycle state identifies whether content is in discovery or frozen for development and release.
- PRD uses semantic versioning and the version is frozen with the release scope.
- Requirements are observable and can become acceptance criteria.
- Each success metric has baseline, target, population, time window, source, and owner.
- Guardrails cover material user, business, security, accessibility, and operational risks.
- Links point to canonical repository documents using Markdown links.
- Product, design, engineering, testing, and operations have reviewed the intent.

## Outcome

Intent is ready for functional and technical design when the team can explain WHY the product matters and WHAT it should and should not do, including high-level capabilities, non-functional constraints, and measurement plan, without prematurely deciding HOW it will be built.

