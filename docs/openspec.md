---
type: urn:open-specs:spec
title: openspec.yaml
description: Specification for repository-level `openspec.yaml` which provides project metadata and agent context used by automation and readers.
tags:
  - openspec
  - metadata
  - repo
generated: 
  by: agent:chatgpt-5-mini
  at: 2026-08-13
verified:
  - by: human:thyvador
    at: 2026-08-13
---

## Overview

The `openspec.yaml` file at the repository root contains high-level project metadata and agent configuration used by automation processes. It is intended to be small, stable, and easy for both humans and agents to read. Agents use `openspec.yaml` to locate important entry points (for example `specs/`, `apis/`, or CI hooks) and to discover maintainers and teams.

## Fields

The repository `openspec.yaml` SHOULD contain the following top-level fields. Fields not listed here are allowed but should be used sparingly.

- application: Metadata about the project. Typical keys:
  - name: human-friendly project name
  - description: short description of the project
  - version: semantic version of the spec or repository snapshot
  - type: `single-domain` or `multi-domain` to indicate repo scope

- teams: Sequence of team entries. Each team contains:
  - name: team name
  - description: optional human description
  - members: sequence of member objects. Each member has `type` (human|agent), `name`, and optional `email` or `description`.

## Example

The following example is taken from this repository's `openspec.yaml` and shows a minimal, practical layout:

```yaml
application:
  name: OpenSpec
  description: OpenSpec is a specification for open-source projects.
  version: 0.0.1
  type: single-domain
teams:
  - name: OpenSpec
    description: OpenSpec maintainers
    members:
      - type: human
        name: thyvador
        email: ahiltcher.pro@gmail.com
      - type: agent
        name: chatgpt-5-mini
        description: An AI assistant for OpenSpec
```

## Validation and usage

Keep `openspec.yaml` minimal. Automation tools should validate its presence and basic structure in CI. Recommended checks:

- `application.name` exists and is non-empty
- `application.version` follows semver-like format
- Each team has at least one humanmember
- At least one team is defined

Agents should read `openspec.yaml` but not overwrite it without human consent. When tools need to update metadata (for example bumping a version), prefer creating a PR with the change and include validation output in the PR body.

## Placement and discoverability

Place `openspec.yaml` at the repository root. Use stable keys so agents can reliably discover teams, owners, and important paths. If your repository contains multiple specs or products, consider adding a `paths` section listing primary entry points (for example `specs/`, `apis/`, `ops/`).
