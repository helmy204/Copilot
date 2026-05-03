# 🎯 Agent Skills

Agent Skills are self-contained folders with instructions and bundled resources that enhance AI capabilities for specialized tasks. Based on the [Agent Skills specification](https://agentskills.io/specification), each skill contains a `SKILL.md` file with detailed instructions that agents load on-demand.

Skills differ from other primitives by supporting bundled assets (scripts, code samples, reference data) that agents can utilize when performing specialized tasks.

### How to Use Agent Skills

**What's Included:**
- Each skill is a folder containing a `SKILL.md` instruction file
- Skills may include helper scripts, code templates, or reference data
- Skills follow the Agent Skills specification for maximum compatibility

**When to Use:**
- Skills are ideal for complex, repeatable workflows that benefit from bundled resources
- Use skills when you need code templates, helper utilities, or reference data alongside instructions
- Skills provide progressive disclosure - loaded only when needed for specific tasks

**Usage:**
- Browse the skills table below to find relevant capabilities
- Copy the skill folder to your local skills directory
- Reference skills in your prompts or let the agent discover them automatically

| Name | Description | Bundled Assets |
| ---- | ----------- | -------------- |
| [breakdown-plan-azure](../skills/breakdown-plan-azure/SKILL.md) | Azure DevOps work item planning and automation prompt that generates comprehensive project plans with Epic > Feature > Story > Test hierarchy, dependencies, priorities, and board tracking. | None |
| [breakdown-plan-jira](../skills/breakdown-plan-jira/SKILL.md) | Jira ticket planning and automation prompt that generates comprehensive project plans with Epic > Story/Task > Sub-task hierarchy, dependencies, priorities, and board tracking. | None |
| [breakdown-test-jira](../skills/breakdown-test-jira/SKILL.md) | Test Planning and Quality Assurance prompt that generates comprehensive test strategies, task breakdowns, and quality validation plans for Jira projects. | None |
| [breakdown-test-azure](../skills/breakdown-test-azure/SKILL.md) | Test Planning and Quality Assurance prompt that generates comprehensive test strategies, task breakdowns, and quality validation plans for Azure DevOps projects. | None |
| [breakdown-epic-pm](../skills/breakdown-epic-pm/SKILL.md) | Prompt for creating an Epic Product Requirements Document (PRD) for a new epic. This PRD will be used as input for generating a technical architecture specification. | None |
| [breakdown-epic-arch](../skills/breakdown-epic-arch/SKILL.md) | Prompt for creating the high-level technical architecture for an Epic, based on a Product Requirements Document. | None |
| [csharp-xunit](../skills/csharp-xunit/SKILL.md) | Get best practices for XUnit unit testing, including data-driven tests | None |
| [javascript-typescript-jest](../skills/javascript-typescript-jest/SKILL.md) | Best practices for writing JavaScript/TypeScript tests using Jest, including mocking strategies, test structure, and common patterns. | None |
| [dotnet-best-practices](../skills/dotnet-best-practices/SKILL.md) | Ensure .NET/C# code meets best practices for the solution/project. | None |
| [csharp-async](../skills/csharp-async/SKILL.md) | Get best practices for C# async programming | None |
| [create-implementation-plan](../skills/create-implementation-plan/SKILL.md) | Create a new implementation plan file for new features, refactoring existing code or upgrading packages, design, architecture or infrastructure. | None |
| [create-architectural-decision-record](../skills/create-architectural-decision-record/SKILL.md) | Create an Architectural Decision Record (ADR) document for AI-optimized decision documentation. | None |
| [breakdown-feature-prd](../skills/breakdown-feature-prd/SKILL.md) | Prompt for creating Product Requirements Documents (PRDs) for new features, based on an Epic. | None |
| [breakdown-feature-implementation](../skills/breakdown-feature-implementation/SKILL.md) | Prompt for creating detailed feature implementation plans, following Epoch monorepo structure. | None |
| [make-skill-template](../skills/make-skill-template/SKILL.md) | Create new Agent Skills for GitHub Copilot from prompts or by duplicating this template. Use when asked to "create a skill", "make a new skill", "scaffold a skill", or when building specialized AI capabilities with bundled resources. Generates SKILL.md files with proper frontmatter, directory structure, and optional scripts/references/assets folders. | None |
| [context-engineering](../skills/context-engineering/SKILL.md) | This skill enables the agent to perform "High-Precision Filtering" of conversation history. It distinguishes between transient "noise" (user small talk, irrelevant updates) and "Permanent Constraints" (brand rules, technical limitations, negative constraints). Use when you want to ensure that the agent focuses on relevant information and adheres to established guidelines throughout a session.
 | None |
| [mcp-orchestration](../skills/mcp-orchestration/SKILL.md) | This skill enables Agent to operate as an Active Agent rather than a passive text generator. It allows the model to interact with the Model Context Protocol (MCP), enabling it to browse files, call APIs, and execute local/remote tools to ground its prompt generation in real-world data. Use when you want to ensure that the agent can access up-to-date information and perform actions beyond text generation, such as fetching data from APIs or managing project tasks.
 | None |
| [plan-act-observe](../skills/plan-act-observe/SKILL.md) | This skill implements the Agentic Reasoning Core. It prevents the model from "shooting from the hip" by enforcing a mandatory internal reflection cycle. The agent must simulate potential outcomes, execute the most logical path, and then critique its own output against user requirements before final delivery.
 | None |