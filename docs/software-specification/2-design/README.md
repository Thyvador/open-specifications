---
type: urn:open-specs:doc
title: Design
description: Guide for turning validated product intent into functional behavior, technical boundaries, contracts, and implementation-ready design artifacts.
tags:
  - process
  - design
  - architecture
  - ontology
generated:
  by: agent:opencode
  at: 2026-08-20T00:00:00Z
status: draft
---

## Purpose

Turn validated product intent into a coherent solution. Intent establishes WHY the product matters and WHAT it must achieve. Design defines HOW that behavior is organized, realized, and exposed while preserving approved outcomes and constraints.

## Stage Focus

The team works across two connected tracks:

- Functional design: features, user stories, flows, rules, language, and visual system decisions.
- Technical design: components, architecture decisions, APIs, events, data responsibilities, and operational constraints.

Work as a cross-functional group of product, design, engineering, testing, security, and operations representatives.

## Inputs

- Reviewed and appropriately frozen `/specs/PRD.md`
- Product capabilities: `/specs/capabilities/<capability>/capability.md`
- Personas: `/specs/personas/<persona>/persona.md`
- Existing domain ontology: `/specs/language/`
- Relevant constraints, metrics, and non-goals
- Optional existing features, components, contracts, and ADRs affected by change

## Process

1. Map PRD outcomes and capabilities to features and user journeys.
2. Establish or extend the domain ontology from the PRD, personas, and existing terms.
3. Describe feature behavior and user stories with acceptance criteria.
4. Capture business rules, states, permissions, errors, and edge cases.
5. Define visual system or design tokens when frontend exists.
6. Identify technical components and responsibilities.
7. Record significant alternatives and decisions in ADRs.
8. Define use cases and cross-component interaction sequences where applicable; every use case includes a Mermaid sequence diagram with alternate and error paths.
9. Define OpenAPI and AsyncAPI contracts where interfaces require them.
10. Review traceability, consistency, testability, and operational readiness.

## Core Concepts

### Functional Design

Functional design describes behavior users and the business can recognize. Features define purpose, scope, and flows. User stories express small, testable scenarios. Rules capture invariants and decision logic. Use cases describe end-to-end interaction when multiple actors or components are involved.

### Technical Design

Technical design defines implementation boundaries and integration contracts. Components describe responsibilities, ownership, dependencies, state, failure behavior, and operational concerns. ADRs record consequential choices and alternatives. OpenAPI and AsyncAPI contracts define machine-readable interfaces.

### Ubiquitous Language and Ontology

Define ubiquitous language through a machine-readable domain ontology. Start with concepts from the PRD, personas, and existing domain knowledge, then refine the ontology as features, rules, flows, components, APIs, events, and use cases are explored.

Store the canonical ontology under `/specs/language/`. RDF/Turtle (`.ttl`) is the recommended format. Define concepts, properties, relationships, constraints, aliases, and distinctions between related terms. A human-readable glossary may be derived from the ontology, but must not become a competing source of truth.

Resolve conflicting terminology before publishing acceptance criteria or machine-readable contracts. Use ontology identifiers consistently across design artifacts where practical. Freeze the ontology version relevant to a development or release cycle with the other design artifacts, and identify affected artifacts when it changes.

### Components and Contracts

Every technical component must have `/specs/components/<component>/component.md`. It describes purpose, responsibilities, non-responsibilities, boundaries, consumers, dependencies, ownership, inputs, outputs, state, data ownership, security, failure behavior, deployment constraints, observability, and related artifacts.

Include an OpenAPI contract when the component exposes or consumes synchronous HTTP APIs. Include an AsyncAPI contract when it publishes or consumes asynchronous events. Link contracts from `component.md`; do not create empty contracts when no interface exists.

### Use-Case Sequence Diagrams

Every use case must include a Mermaid `sequenceDiagram`. Actors may appear directly, but every participant representing an API, service, database, or other component-like boundary must map to a documented component at `/specs/components/<component>/component.md`.

Internal API, service, database, or worker participants are allowed only when grouped inside a Mermaid `box` named after their owning documented component. Participant aliases and internal responsibilities must be clear in the component document. A box must not introduce an undocumented component.

Represent alternate and error behavior inside the diagram using Mermaid control-flow constructs such as `alt` / `else`, `break`, `opt`, and `loop`. Do not add a separate prose section for alternate or error scenarios.

## Expected Outcome

Design is ready for development when implementers understand intended behavior, rules, vocabulary, component boundaries, decisions, and interface contracts without undocumented assumptions. Testers can derive acceptance and contract tests, and operators understand ownership and operational constraints.

The design package produces, where applicable:

- Features
- Capabilities mapped to features
- User stories
- Business rules
- Domain ontology defining ubiquitous language
- Architecture decisions
- Components
- Design tokens and visual rationale
- Use cases
- API guidance and OpenAPI contracts
- Event guidance and AsyncAPI contracts

## Artifacts

| Artifact | Path | Required when | Purpose |
| --- | --- | --- | --- |
| Feature | `/specs/features/<feature>/feature.md` | Feature exists | Defines feature purpose, scope, and behavior |
| Capability link | `/specs/capabilities/<capability>/capability.md` | Feature contributes to a capability | Maintains product-outcome traceability |
| User story | `/specs/features/<feature>/user-stories/<us-name>/user-story.md` | Behavior needs focused acceptance criteria | Defines a small, testable scenario |
| Business rules | `/specs/features/<feature>/rules.md` | Feature has decision logic or invariants | Defines precise rules and edge behavior |
| Domain ontology | `/specs/language/` | Domain concepts or relationships need canonical definitions | Establishes machine-readable ubiquitous language |
| ADR | `/specs/adrs/<YYYY-MM-DD>-<name>/adr.md` | Choice has meaningful alternatives or consequences | Preserves architecture rationale |
| Component | `/specs/components/<component>/component.md` | Technical boundary exists | Defines ownership and interfaces |
| Design system | `/specs/DESIGN.md` | Frontend exists | Defines visual system and rationale using exact `DESIGN.md` filename |
| Use case | `/specs/use-cases/<name>/use-case.md` | Use case is documented | Defines sequence, mandatory Mermaid diagram, and error handling |
| API contract | `/specs/apis/<api>/openapi.yaml` | Synchronous interface exists | Defines machine-readable API contract |
| Event contract | `/specs/events/<event>/asyncapi.yaml` | Asynchronous interface exists | Defines machine-readable event contract |

## Do

- Trace every feature and decision to a PRD goal, persona, requirement, or constraint.
- Define behavior before implementation tasks.
- Specify normal, alternate, error, permission, and boundary paths.
- Use ontology concepts and identifiers consistently across prose, contracts, examples, and tests.
- Keep components focused with explicit ownership and boundaries.
- Validate machine-readable contracts.
- Record alternatives and consequences for consequential technical choices.
- Update related artifacts together when behavior or terminology changes.

## Do Not

- Do not silently change PRD goals, scope, or success measures.
- Do not hide business rules in UI descriptions or code-only notes.
- Do not mix implementation tasks into user stories.
- Do not document a required API or event only in prose.
- Do not reference an undocumented component-like participant in a sequence diagram.
- Do not place API, service, database, or worker participants outside a box for their owning component.
- Do not describe alternate or error scenarios in a separate use-case section; represent them in the Mermaid diagram.
- Do not assign overlapping component ownership without recording the boundary.
- Do not introduce unexplained synonyms or ontology concepts outside the canonical ontology.
- Do not create ADRs for trivial choices.
- Do not bypass security, accessibility, testing, or operational review.

## Templates

- [Feature template](/docs/software-specification/2-design/templates/feature-template.md)
- [User story template](/docs/software-specification/2-design/templates/user-story-template.md)
- [Business rules template](/docs/software-specification/2-design/templates/rules-template.md)
- [Component template](/docs/software-specification/2-design/templates/component-template.md)
- [ADR template](/docs/software-specification/2-design/templates/adr-template.md)
- [API guidance template](/docs/software-specification/2-design/templates/api-template.md)
- [Event guidance template](/docs/software-specification/2-design/templates/event-template.md)
- [Use case template](/docs/software-specification/2-design/templates/use-case-template.md)
- [DESIGN.md template](/docs/software-specification/2-design/templates/DESIGN.md)

## Review Checklist

- Every PRD goal and in-scope outcome maps to design artifacts.
- Every feature maps to a product capability and each capability maps to its intended outcomes.
- Features, stories, and rules are behaviorally precise and testable.
- Acceptance criteria cover normal, alternate, error, permission, and boundary cases.
- Canonical language is consistent across prose, contracts, and examples.
- Components have clear boundaries, ownership, dependencies, and failure behavior.
- Required APIs and events have linked machine-readable contracts.
- ADRs explain context, alternatives, decision, and consequences.
- Design tokens and visual rationale exist when frontend work is in scope.
- Domain ontology defines concepts and relationships used by design artifacts.
- Every use case includes a Mermaid `sequenceDiagram` consistent with its written flow.
- Every component-like diagram participant maps to a documented component and is grouped under its owning `box`.
- Alternate and error paths use Mermaid control-flow constructs such as `alt`, `else`, `break`, `opt`, or `loop`.
- Security, accessibility, performance, reliability, and operability constraints are addressed.
- Open questions, assumptions, and deferred decisions are explicit.
- Design does not silently change frozen intent.

## Lifecycle and Change Control

Design artifacts may evolve while design is active. When development or release begins, freeze the relevant behavior, language, contracts, and decisions. Contract changes require impact review and updates to consumers, tests, and release scope.

Ontology changes must identify affected stories, rules, components, APIs, events, use cases, and tests. ADRs preserve historical decisions; superseded decisions should link to their replacement rather than being rewritten without history.

The visual design artifact must use exact filename `DESIGN.md` because Google `@google/design.md` tooling depends on that filename. Validate it with `npx @google/design.md lint DESIGN.md` and review token changes with the tool's `diff` command.
