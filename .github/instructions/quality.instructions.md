---
applyTo: '**/*.{cs,sql,tf,js,ts}'
---

# Code Quality Guidelines
This document outlines the code quality guidelines for the project. Adhering to these guidelines will ensure that our code is of high quality, maintainable, and efficient across all repositories. These guidelines are mandatory and must be followed by all developers, contractors, contributors, and AI agents working on the project and applied to all programming languages and technologies used in the project for all codebases.

## General Guidelines
- Code smells to avoid:
  - Duplicate code: Eliminate code duplication by creating reusable functions or modules.
  - Long methods/functions: Break down large methods into smaller, more focused ones.
  - Large classes/modules: Refactor large classes into smaller, more cohesive ones.
  - Magic numbers and strings: Avoid using hardcoded values in your code. Use constants or configuration files instead.
  - Tight coupling: Ensure that your code is modular and loosely coupled to improve maintainability and testability.
  - Hardcoded secrets: NEVER hardcode sensitive information (e.g., API keys, database credentials) in source code. Use secure secret management solutions (e.g., vaults, Azure Key Vault, environment variables with restricted access).
  - Unused variables and code: Remove any unused variables, functions, classes, or code blocks to improve readability and maintainability.
  - Excessive comments: If you find yourself writing a lot of comments to explain what the code does, consider refactoring the code to make it more self-explanatory.
  - Deep nesting: Avoid deep nesting of loops and conditionals. Refactor to reduce complexity.
  - Inconsistent naming conventions: Follow consistent naming conventions for variables, functions, classes, and other code elements to improve readability.
- Refactor code as needed (e.g., extract methods, rename variables, reorganize code, use dependency injection) while adhering to the above guidelines.

## Reference Instructions
- Follow [copilot instructions](../instructions/copilot.instructions.md)