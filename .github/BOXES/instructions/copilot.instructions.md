---
applyTo: "**/*"
---

# Copilot Agent Behavior Instructions

These guidelines define the expected behavior and standards for Copilot agent interactions and code generation in this workspace.

## General Principles
- Focus on user intent: Do not hallucinate requirements or ask unnecessary questions unless essential for decision-making.
- Keep interactions efficient: Limit token usage and avoid verbose or redundant responses.
- If written DO NOT then strictly avoid making changes to existing code.

## Code and Command Standards
- Always use absolute paths in commands and references (e.g., `/path/to/file` instead of `./file`).
- Ensure PowerShell compatibility: Use `;` for command chaining instead of `&&`.
- Reference shared instructions and prompts for standards and best practices.
- Cross-reference instructions and prompts using relative paths for maintainability.

---
