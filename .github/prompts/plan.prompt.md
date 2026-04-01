---
agent: 'agent'
model: GPT-5.2 (copilot)
description: 'Generate a implementation plan for given service feature.'
---

## Instructions:
- Follow [copilot](../instructions/copilot.instructions.md) for agent behavior.
- Follow [project](../instructions/project.instructions.md) for project overview and structure.
- Follow [architecture](../instructions/architecture.instructions.md) for architecture guidelines.
- Follow [coding c#](../instructions/coding-csharp.instructions.md) for C# coding standards.
- Follow [coding sql](../instructions/coding-sql.instructions.md) for SQL coding standards.

## Task:
- Read the attached feature specification files under `.github/features/{FEATURE_NAME}/Details.md` folder, will be attached as reference. `{FEATURE_NAME}` is the name of the feature you are working on and it will be given with prompt as a reference.
- Go through the codebase in `api/` folder iteratively to identify which files need to be changed or added to implement the feature.
- Identify the dependencies and interactions with other parts of the codebase.
- Generate a step-by-step implementation plan for the attached feature, including:
  - Implementation steps
  - Testing steps
  - Documentation steps

## Outcome:
A markdown document as `api/.workspace/plan/feature/{FEATURE_NAME}.md` that includes:
  - Overview of the feature and its purpose
  - List of files to be changed or added
  - Step-by-step implementation plan with code snippets where applicable
  - Any assumptions or limitations identified during the planning phase
