---
title: Open Specifications
---

Open Specifications is an open-source software specification standard. It defines a small, opinionated set of conventions for authoring software specifications so they remain consistent, readable, and machine-parsable across projects.

## Purpose

- Provide a consistent spec structure that teams and tools can rely on
- Provide consistent file formats for narrative content, metadata, and machine-readable schema
- Serve both humans (clear prose, examples) and agents (stable metadata, parsable frontmatter)

## Design Principles

- Human-first: readable Markdown narrative, examples, and usage notes
- Machine-friendly: structured metadata in YAML/JSON, optional formal schema (JSON Schema)
- Minimal: small surface area, easy to adopt
- Extensible: allow profiles, versioning, and optional sections

## Recommended Files & Layout

See. [Directory structure](/docs/directory-structure.md) and [File format](/docs/file-format.md)

 
## Contributing

PRs welcome. Keep changes small, add examples, and update schema/metadata when adding new fields.

### Commits

This repository uses the [Gitmoji](https://github.com/carloscuesta/gitmoji). Commit usage:

```
<intention> [scope?][:?] <message>
```

- `intention`: An emoji from the list.
- `scope`: An optional string that adds contextual information for the scope of the change.
- `message`: A brief explanation of the change.