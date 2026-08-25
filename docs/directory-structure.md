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
│   ├── DESIGN.md                           # Optional: Google DESIGN.md tokens (YAML frontmatter) + rationale for frontends
│   ├── PRD.md                              # Product Requirement Definition: high-level goals and success metrics
│   ├── capabilities/
│   │   ├── <capability-name>/
│   │   │   └── capability.md                # Product capability grouping related features
│   │   └── features/
│   │       └── <feature-name>/
│   │           ├── feature.md                  # Feature description: overview, scope, UX flows
│   │           ├── rules.md                    # Business rules and invariants for the feature
│   │           └── user-stories/
│   │               └── us-<id>/
│   │                   └── user-story.md       # Focused user story with acceptance criteria
│   ├── personas/
│   │   └── <persona-name>/
│   │       └── persona.md                  # Persona profile and motivations
│   ├── inputs/                             # Raw inputs: interviews, research notes, spreadsheets
│   │   └── *
│   ├── use-cases/
│   │   └── <use-case-name>/
│   │       └── use-case.md                 # Interaction sequences, diagrams, edge cases
│   ├── adrs/
│   │   └── <YYYY-MM-DD>-<adr-name>/
│   │       └── adr.md                      # Architecture Decision Record
│   ├── components/
│   │   └── <component-name>/
│   │       ├── component.md                # Component/service responsibilities and interfaces 
│   │       ├── apis/                       # Optional: API contracts and API guidance
│   │       │   └── <api-name>/
│   │       │       ├── openapi.yaml        # OpenAPI contract
│   │       │       └── api.md
│   │       └── events/                     # Optional: async event contracts (AsyncAPI)
│   │           └── <event-name>/
│   │               └── asyncapi.yaml
│   └── language/                           # Domain ontologies defining ubiquitous language and change log
│       ├── <domain>.ttl                    # RDF/Turtle ontology
├── ops/
│   ├── runbooks/
│   │   └── <date>-<title>.md               # Operational runbooks and incident playbooks
│   ├── releases/
│   │   └── <version>.md                    # Release notes and runbooks for versioned releases
│   └── monitoring.md                       # Key metrics, dashboards, and logs guidance
├── src/                                    # Implementation or reference implementations
│   └── *                                   # Source code
├── openspec.yaml                           # Repository/project context (used by automation)
├── AGENTS.md                               # Agent guidelines: how agents should read and modify repo
└── README.md                               # Repository and product overview, navigation links
```

## Folder explanations

- `specs/` — Primary location for product documentation. Keep narrative content, decision records, and structured artifacts here. Files under `specs/` are the canonical source of truth for product behaviour.
- `PRD.md` — High-level product requirements. Describe goals, target users, non-functional requirements, and success metrics.
- `capabilities/` — Product-level capabilities. Each capability groups one or more related features around a meaningful outcome or behavioral area and may span multiple releases.
- `DESIGN.md` describing design tokens (YAML frontmatter) and human rationale. Use the DESIGN.md schema to expose colors, typography, spacing, component tokens, and exportable derivatives (Tailwind/CSS).
- `features/` — Each feature gets its own folder containing a `feature.md` for narrative, `rules.md` for business logic, and a `user-stories/` subfolder for testable stories.
- `personas/` — Short profiles of representative users. Use these to drive acceptance criteria and prioritization.
- `inputs/` — Unprocessed inputs such as interview transcripts, raw research notes, and imported documents. Keep originals here to preserve provenance.
- `use-cases/` — End-to-end interaction descriptions. Include sequence diagrams or step-by-step flows and enumerate edge cases and error handling.
- `adrs/` — Architecture Decision Records. Each ADR should be dated and contain context, alternatives, decision, and consequences.
- `components/` — Documentation for technical components that the product relies on (datastore, cache, external services). Include interfaces and deployment notes.
- `apis/` and `events/` — Machine-readable contract artifacts. Prefer `openapi.yaml` and `asyncapi.yaml` filenames and keep human guidance in adjacent `*.md` files.
- `language/` — Optional domain languages and ontologies. Use standard formats where appropriate and record changes in `log.md`.
- `ops/` — Operational documentation needed to run and monitor the product: runbooks, release guides, and monitoring definitions.
- `src/` — Implementation.

## Repository-level files

- `openspec.yaml` — Machine-readable changelog and context used by agents to identify important entry points and what to index.
- `AGENTS.md` — Guidelines for bots and automated tools: where to write, which files they may edit, and verification rules.
- `README.md` — Human-facing landing page that explains repository purpose and links into important spec pages.

## Changelog

A `log.md` file MAY appear at any level of the hierarchy to record the history of changes to that scope. This follows the Open Knowledge Format (OKF) convention for log files. The format is a flat list of date-grouped entries, newest first:

```markdown
# Directory Update Log

## 2026-08-14
* **Create**: Added file-format definitions and examples for all spec types.
* **Update**: Enhanced directory-structure documentation with changelog guidance.

## 2026-08-13
* **Create**: Created foundational spec structure and AGENTS.md guidelines.
```

Date headings MUST use ISO 8601 `YYYY-MM-DD` format. Log entries are prose; the leading bold word (`**Create**`, `**Update**`, `**Deprecate**`, `**Fix**`) is a convention to indicate the type of change.

Use `log.md` to track:
- Creation of new major artifacts or subdirectories
- Significant updates to existing specifications
- Deprecation or removal of features or files
- Breaking changes to contracts (APIs, data models)

Benefits of maintaining a log:
- Agents can quickly understand what has changed and when
- Humans can review history without relying on git log
- Supports temporal queries like "what changed this month"

## Conventions and tips

- Use kebab-case for directory names and `YYYY-MM-DD` for ADR timestamps.
- Keep frontmatter consistent across `specs/` files so tooling can index reliably.
- Place machine-readable artifacts in dedicated subfolders (`apis/`, `events/`, `model/`, `examples/`) rather than inline in narrative files.
- Prefer small files with a single responsibility; avoid very large monolithic documents.
- Maintain a root-level `log.md` to track major milestones and breaking changes.
