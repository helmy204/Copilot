# Copilot Workspace

This repository is a structured knowledge and configuration workspace for GitHub Copilot. It is focused on shaping agent behavior through reusable assets rather than shipping application runtime code.

## What This Repo Contains

At a high level, the repository is organized around five capability pillars under `.github`:

- `agents`: specialized chat modes for focused domains (architecture, DevOps, product planning, database work, and implementation).
- `instructions`: reusable rule sets that influence coding behavior, quality, security, and delivery practices.
- `prompts`: task-specific prompt templates for planning, implementation, testing, and specification workflows.
- `skills`: packaged capability bundles with `SKILL.md` entry points and optional reference resources.
- `BOXES`: a startup and product-building framework (Brain, Origin, eXperience, Engine, Signal, Flow, Help) with dedicated prompts and instructions.

## Repository Snapshot

Current observable inventory:

- Agents: 15 files
- Instructions: 12 files
- Prompts: 7 files
- Skills: 28 files
- BOXES assets: 11 files

This composition indicates the repository is intended as a Copilot operating system for strategy, architecture, delivery, and governance workflows.

## Directory Overview

```text
.
├── README.md
└── .github
		├── agents/
		├── instructions/
		├── prompts/
		├── skills/
		└── BOXES/
```

## Key Purpose of Each Area

- `/.github/agents`: defines reusable expert personas for task routing and specialization.
- `/.github/instructions`: enforces cross-cutting standards (security, quality, performance, DevOps mindset).
- `/.github/prompts`: accelerates common workflows through prebuilt prompt recipes.
- `/.github/skills`: encapsulates rich, discoverable capabilities, often with supporting references.
- `/.github/BOXES`: provides a business-to-product lifecycle framework from idea validation to customer success.

## Suggested Usage Pattern

1. Pick an agent mode that matches your objective.
2. Let relevant instructions auto-apply by file type and scope.
3. Use prompts for repeatable workflow acceleration.
4. Invoke skills for deeper domain execution.
5. Use BOXES when you need end-to-end venture and product framing.

## Notes

- This repository is primarily configuration and knowledge architecture.
- If you want to extend it, add new assets inside `.github` following existing naming conventions.