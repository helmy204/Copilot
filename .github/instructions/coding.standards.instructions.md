---
applyTo: '**/*.{cs,sql,tf,js,ts}'
---

# General Coding Standards
This document outlines the general coding standards for the project. Adhering to these standards will ensure that our code is consistent, readable, maintainable, and safe across all repositories. These guidelines are mandatory and must be followed by all developers, contractors, contributors, and AI agents working on the project and applied to all programming languages and technologies used in the project for all codebases.

## General Guidelines
- Use clear, descriptive names for variables, functions, classes, and other code elements.
- Keep functions and modules small and focused on a single responsibility.
- Follow the DRY (Don't Repeat Yourself) principle to avoid code duplication. Reuse code through functions, classes, and modules when possible instead of copying and pasting.
- Write readable code by:
  - Use consistent formatting (e.g., line breaks, indentation).
  - Use meaningful names and avoid abbreviations that may not be universally understood.
  - Use comments to explain complex logic and the purpose of code sections. Avoid obvious comments that do not add value.
- Handle errors gracefully and provide meaningful error messages to facilitate debugging and user understanding.
- Validate and sanitize all external inputs to prevent security vulnerabilities and ensure data integrity.
- Write meaningful unit tests and integration tests to ensure code correctness and facilitate future refactoring. Aim for high test coverage, especially for critical code paths.
- NEVER hardcode sensitive information (e.g., API keys, database credentials) in source code. Use secure secret management solutions (e.g., vaults, Azure Key Vault, environment variables with restricted access).
- Use version control best practices, including meaningful commit messages and regular commits.

## Reference Instructions
- Follow [copilot guidelines](../instructions/copilot.instructions.md)
- Follow [quality guidelines](../instructions/quality.instructions.md)
- Follow [security guidelines](../instructions/security.instructions.md)