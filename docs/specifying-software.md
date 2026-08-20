---
type: urn:open-specs:doc
title: Specifying Software with OpenSpec
description: |
  How to author a software specification using OpenSpec: intent, design (functional and technical), development handoff, testing, and operations.
tags:
  - process
  - guide
  - lifecycle
generated: 
  by: agent:chatgpt-5-mini
  at: 2026-08-14
validated: 
  by: human:thyvador
  at: 2026-08-14
---

## Overview

OpenSpec defines a lightweight, predictable approach for specifying software. The goal is to produce artifacts that are useful to product managers, designers, developers, testers, and automation. A typical specification lifecycle contains five phases: define intent, design, develop (handoff), test (validation), and deploy/operate. This page explains each phase and where artifacts belong in the repository structure.

## 1. Define intent

Start by describing why the product or feature exists. Create a concise Product Requirements Document (PRD) that describes goals, success metrics, target users, constraints, and non-functional requirements. Capture representative users as personas—short profiles that explain motivations and typical behaviours.

Where to put files:

- `specs/PRD.md` for the product-level intent and success metrics.
- `specs/personas/<persona>/persona.md` for persona profiles.

Why it matters:

Clear intent reduces ambiguity during design and development. Personas guide prioritisation and acceptance criteria for user stories.

## 2. Design

Design splits into two complementary tracks: functional design (what the product does) and technical design (how the product is realised). Keep each artifact focused and link them using absolute repository paths or stable identifiers in frontmatter.

### 2.1 Functional design

Functional design captures features, user stories, business rules, and the domain vocabulary (semantic language or ontology) used across the spec.

- Semantic language / ontology: If you need canonical terms or an ontology, place machine-readable artifacts under `specs/language/`.
- Design tokens / visual system: If product includes frontend (web, mobile, desktop), include an optional `specs/DESIGN.md` at repository root under `specs/`. Use YAML frontmatter for tokens (colors, typography, spacing, rounded, components) and prose for rationale. This file enables automated exports (Tailwind, CSS, token JSON) and linting via `npx @google/design.md lint docs/DESIGN.md`.
- Features: For each feature, create `specs/features/<feature>/feature.md` describing purpose, scope, and UX flows.
- User stories: Draft small, testable stories under `specs/features/<feature>/user-stories/us-<id>/user-story.md` with clear acceptance criteria.
- Business rules: Record precise invariants and rule logic in `specs/features/<feature>/rules.md` so tests and agents can validate behavior.

Functional deliverables are the primary source for acceptance tests and product validation.

### 2.2 Technical design

Technical design captures architectural decisions, API and event contracts, and concrete interaction flows.

- Components: Define technical components (services, databases) in `specs/components/<component>/component.md`. Describe responsibilities, interfaces, deployment constraints, and dependencies so implementers and operators understand boundaries and integration points.
- ADRs: Record architecture decisions in `specs/adrs/<YYYY-MM-DD>-<name>/adr.md` with context, options, decision, and consequences.
- APIs: Place OpenAPI contracts in `specs/apis/<api>/openapi.yaml` and human guidance in `specs/apis/<api>/api.md`.
- Events: Place AsyncAPI contracts under `specs/events/<event>/asyncapi.yaml` for event-driven designs.
- Use cases: Document end-to-end sequences in `specs/use-cases/<name>/use-case.md`, including actors, components, and error handling.

Design artifacts are useful for implementers and frontend engineers who need exact tokens and rationale.

Technical artifacts are the canonical interface and integration contracts used by implementers and automated validation.

## 3. Develop (handoff)

OpenSpec does not prescribe development methods. The spec is a handoff: developers should rely on `specs/` artifacts (APIs, user stories, rules) to implement behaviour.

Handoff checklist:

- Ensure each user story has acceptance criteria.
- Ensure APIs and events have machine-readable contracts (OpenAPI/AsyncAPI).
- Provide small example payloads in `specs/examples/` when helpful.
 - Provide `docs/DESIGN.md` when frontend present. Include token references used by components and a short export guide (example: `npx @google/design.md export --format json-tailwind docs/DESIGN.md > tailwind.theme.json`). Validate DESIGN.md with the linter as part of handoff.

## 4. Test

Testing validates that implementation meets the spec. Focus on two classes of tests:

- Acceptance tests: Validate user stories' acceptance criteria end-to-end. Map tests to `specs/features/.../user-stories` entries.
- Rule/contract tests: Validate business rules and API contracts. Use JSON Schema, contract tests, or unit tests that reference `specs/features/.../rules.md` and `specs/apis/*/openapi.yaml`.

## 5. Deploy / Operate

Operational readiness is part of the software lifecycle. Maintain operational artifacts that tell operators how to run and recover the system.

- Runbooks: `ops/runbooks/<date>-<title>.md` for incident playbooks and troubleshooting steps.
- Releases: `ops/releases/<version>.md` for release procedures and rollbacks.
- Monitoring: `ops/monitoring.md` with key metrics, SLOs, and alerting guidance.

Operators and SREs should be included early in design so runbooks and monitoring are useful from day one.

## Example minimal workflow

1. Create `specs/PRD.md` and one or two personas.
2. Add a feature folder `specs/features/tasks/` with `feature.md`, `rules.md`, and one `user-story.md`.
3. Add `specs/apis/todo-api/openapi.yaml` if sync API required.
4. Add CI checks to validate frontmatter and OpenAPI.
5. Implement code in `src/` and add contract tests.

Following these steps produces a spec that is readable, actionable, and automatable.
