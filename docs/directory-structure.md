---
type: urn:open-specs:doc
title: Directory Structure
description: 
generated: 
  by: agent:chatgpt-5-mini
  at: 2026-08-13
verified:
  - by: human:thyvador
    at: 2026-08-13
---
## Overview

This repository layout is optimized for a single application specification. The top-level `specs/` directory contains product definition, feature documentation, personas, and other artifacts that describe what to build, why, and how it should behave. Operational material, examples, and source code live alongside the spec artifacts so teams and automation can find authoritative information in one place.

## Design goals

- Predictable: stable paths and filenames that tooling and agents can rely on.
- Human-first: narrative content written for readers with clear sections and examples.
- Machine-friendly: small, consistent frontmatter and dedicated places for machine-readable artifacts (OpenAPI, schemas, examples).

## Detailed structure

The tree below shows the recommended layout for a single-app repository. Use it as a template and adapt only when there is a clear reason.

```text
├── specs/
│   ├── PRD.md                    # Product Requirement Definition: high-level goals and success metrics
│   ├── features/
│   │   └── <feature-name>/
│   │       ├── feature.md         # Feature description: overview, scope, UX flows
│   │       ├── rules.md           # Business rules and invariants for the feature
│   │       └── user-stories/
│   │           └── us-<id>/
│   │               └── user-story.md # Focused user story with acceptance criteria
│   ├── personas/
│   │   └── <persona-name>/
│   │       └── persona.md         # Persona profile and motivations
│   ├── inputs/                    # Raw inputs: interviews, research notes, spreadsheets
│   │   └── *
│   ├── use-cases/
│   │   └── <use-case-name>/
│   │       └── use-case.md        # Interaction sequences, diagrams, edge cases
│   ├── adrs/
│   │   └── <YYYY-MM-DD>-<adr-name>/
│   │       └── adr.md             # Architecture Decision Record
│   ├── components/
│   │   └── <component-name>/
│   │       └── component.md       # Component/service responsibilities and interfaces
│   ├── apis/                      # Optional: API contracts and API guidance
│   │   └── <api-name>/
│   │       ├── openapi.yaml       # OpenAPI contract
│   │       └── api.md
│   ├── events/                    # Optional: async event contracts (AsyncAPI)
│   │   └── <event-name>/
│   │       └── asyncapi.yaml
│   └── model/                     # Optional: domain model, ontologies, change log
│       ├── <ontology>.ttl         # RDF/Turtle ontology (optional)
│       └── log.md                 # Model change log and migration notes
├── ops/
│   ├── runbooks/
│   │   └── <date>-<title>.md      # Operational runbooks and incident playbooks
│   ├── releases/
│   │   └── <version>.md           # Release notes and runbooks for versioned releases
│   └── monitoring.md              # Key metrics, dashboards, and logs guidance
├── src/                           # Implementation or reference implementations
│   └── *                          # Source code
├── openspec.yaml                  # Repository/project context (used by automation)
├── AGENTS.md                      # Agent guidelines: how agents should read and modify repo
└── README.md                      # Repository and product overview, navigation links
```

## Folder explanations
- `specs/` — Primary location for product documentation. Keep narrative content, decision records, and structured artifacts here. Files under `specs/` are the canonical source of truth for product behaviour.
- `PRD.md` — High-level product requirements. Describe goals, target users, non-functional requirements, and success metrics.
- `features/` — Each feature gets its own folder containing a `feature.md` for narrative, `rules.md` for business logic, and a `user-stories/` subfolder for testable stories.
- `personas/` — Short profiles of representative users. Use these to drive acceptance criteria and prioritization.
- `inputs/` — Unprocessed inputs such as interview transcripts, raw research notes, and imported documents. Keep originals here to preserve provenance.
- `use-cases/` — End-to-end interaction descriptions. Include sequence diagrams or step-by-step flows and enumerate edge cases and error handling.
- `adrs/` — Architecture Decision Records. Each ADR should be dated and contain context, alternatives, decision, and consequences.
- `components/` — Documentation for technical components that the product relies on (datastore, cache, external services). Include interfaces and deployment notes.
- `apis/` and `events/` — Machine-readable contract artifacts. Prefer `openapi.yaml` and `asyncapi.yaml` filenames and keep human guidance in adjacent `*.md` files.
- `model/` — Optional domain models and ontologies. Use standard formats where appropriate and record changes in `log.md`.
- `ops/` — Operational documentation needed to run and monitor the product: runbooks, release guides, and monitoring definitions.
- `src/` — Implementation.

## Repository-level files

- `openspec.yaml` — Machine-readable changelog and context used by agents to identify important entry points and what to index.
- `AGENTS.md` — Guidelines for bots and automated tools: where to write, which files they may edit, and verification rules.
- `README.md` — Human-facing landing page that explains repository purpose and links into important spec pages.

## Conventions and tips

- Use kebab-case for directory names and `YYYY-MM-DD` for ADR timestamps.
- Keep frontmatter consistent across `specs/` files so tooling can index reliably.
- Place machine-readable artifacts in dedicated subfolders (`apis/`, `events/`, `model/`, `examples/`) rather than inline in narrative files.
- Prefer small files with a single responsibility; avoid very large monolithic documents.
