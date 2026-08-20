---
type: urn:open-specs:doc
title: Agent Guidelines
description: Rules and conventions for automated agents and bots that read, write, or modify files in this repository. Defines permitted actions, formatting rules, verification, and safety constraints.
tags:
  - agents
  - automation
  - governance
generated: 
  by: agent:chatgpt-5-mini
  at: 2026-08-13
verified:
  - by: human:thyvador
    at: 2026-08-13
---

## Edit rules for agents

When an agent writes or updates files in this repository, it must obey these rules:

1. Frontmatter: Every file the agent creates or modifies must include YAML frontmatter matching the frontmatter schema described in `docs/file-format.md`. Include at least `type`, `title`, `description` and `tags`.

2. Atomicity: Keep edits small and focused. One logical change per pull request. Avoid mixing unrelated updates (e.g., content change + refactor + formatting) in same change.

3. Provenance: Agent-generated files must include a `generated` frontmatter entry, for example:

```yaml
generated:
  by: agent:your-agent-name
  at: 2026-08-13T12:34:56Z
```

4. Verification: If the change affects machine-readable artifacts (OpenAPI, schemas), include validation output or a linting result in the PR description or as an attached artifact.

5. No secrets: Never write credentials, tokens, private keys, or other secrets into the repository. If a task requires secrets, the agent should fail the operation and report required steps.

6. Testability: Changes that introduce new artifacts should include minimal examples or tests demonstrating the artifact's correctness (examples/ folder or small schema tests).

7. Human review: For all changes, require at least one human reviewer before merge.

## Formatting and style enforcement

Agents must format Markdown and frontmatter according to `docs/file-format.md`. Key rules to enforce programmatically:

- A file with title in frontmatter MUST NOT contain a top-level (`#`) heading.
- Headings must be followed by a blank line.
- Lists must be surrounded by blank lines.
 - Headings must use ATX style (##, ###) rather than setext underlines. This repository enforces ATX headings.
- Use fenced code blocks with language tags for machine-readable snippets (`json`, `yaml`, `openapi`).
- Link documents with Markdown links using repository-root-relative paths, for example `[reference name](/path/to/ref)`, not inline code spans such as `/path/to/ref`.
- Keep frontmatter keys stable; do not invent ad-hoc keys without repository-level agreement.


## Example frontmatter for agent-created feature scaffold

```yaml
type: urn:open-specs:feature
title: Quick Add Task
description: Feature scaffold for quick-add functionality used in mobile and desktop clients.
tags:
  - feature
  - todo
generated:
  by: agent:scaffold-bot
  at: 2026-08-13T12:34:56Z
```
