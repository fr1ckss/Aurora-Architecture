[English](README.md) | [Русский](README_RU.md)
# Aurora Architecture

An open development ecosystem by Aurora Code. This repository serves as the **source of truth** for shared standards and AI agent instructions. Individual projects (such as Havn) remain independent.

## Structure

- `docs/ARCHITECTURE.md` — ecosystem concept and principles.
- `docs/STANDARDS.md` — standards framework and planned areas.
- `ai/cursor/aurora-core.mdc` — core Cursor instructions.
- `ai/cursor/level-learning.mdc` — learning mode.
- `ai/cursor/level-development.mdc` — development mode.
- `.cursor/rules/custom.mdc` within an individual project (not this repository) — optional project-specific rules.

## Installing Cursor Rules in a Project

In your project (for example, Havn), create a `.cursor/rules/` directory and **copy** the following files:

1. `aurora-core.mdc`
2. **One** of the following: `level-learning.mdc` or `level-development.mdc`

Target structure:

```
havn/
└── .cursor/
    └── rules/
        ├── aurora-core.mdc
        ├── level-learning.mdc      # OR level-development.mdc
        └── custom.mdc              # OPTIONAL: project-specific rules
```

**Important:** The single source of truth for maintained rules is `aurora_architecture/ai/cursor/`. Files inside Havn are installed copies used by Cursor, not independent versions of the standards.

To modify a shared rule, update it in Aurora Architecture first, then apply the changes to individual projects.

When switching levels, replace the existing level file. Do not keep both installed simultaneously, as both use `alwaysApply: true`.

### Custom Project Rules

If you need additional project-specific instructions, create a `.cursor/rules/custom.mdc` file **inside your project** with `alwaysApply: true` in its metadata.

This file is optional and is not included in the Aurora installation files.

Example:

```
---
description: Project-specific agent rules
alwaysApply: true
---

# Project Rules

- Follow the naming conventions defined in PROJECT.md.
- Keep user-facing interface text in Russian.
```

Aurora rules establish the shared foundation, while `custom.mdc` defines local project preferences.

Custom rules must not override core safety requirements, verification integrity, or action approval requirements.

If rules conflict, the agent must report the conflict rather than arbitrarily choosing which rule to follow.

**Updates:** `aurora-core.mdc` and the selected level file are updated from Aurora Architecture. The `custom.mdc` file remains under the project's control and must not be overwritten during Aurora updates.

A separate `PROJECT.md` file describes the individual project, including its name, purpose, technology stack, and setup instructions.

This file belongs to the individual project, not Aurora Architecture.

## Updates

For now, installation and updates are performed manually.

An automated installer or CLI is planned for a future tooling stage and is not required to get started.

## Status

The Cursor rules are an initial version intended for testing in real projects.

Planned standards listed in `STANDARDS.md` should not automatically be considered approved or mandatory.