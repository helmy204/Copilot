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
| [breakdown-test-jira](../skills/breakdown-test-jira/SKILL.md) | Test Planning and Quality Assurance prompt that generates comprehensive test strategies, task breakdowns, and quality validation plans for Jira projects. | None |
| [breakdown-test-azure](../skills/breakdown-test-azure/SKILL.md) | Test Planning and Quality Assurance prompt that generates comprehensive test strategies, task breakdowns, and quality validation plans for Azure DevOps projects. | None |
| [csharp-xunit](../skills/csharp-xunit/SKILL.md) | Get best practices for XUnit unit testing, including data-driven tests | None |