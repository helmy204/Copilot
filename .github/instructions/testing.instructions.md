---
applyTo: "**/*.{cs,sql,tf}"
---

# Testing Guidelines

Follow these best practices to ensure code reliability and maintainability:

## Test Organization
- Organize test cases into separate folders under the top-level `src` directory:
  - `*.UnitTests/` for unit tests
  - `*.IntegrationTests/` for integration tests
  - `*.PactTests/` for contract tests
- Group related tests into classes and namespaces that mirror the structure of the production code.
- Name test files and functions clearly to indicate their purpose and scope.

## Best Practices
- Test early and often; write tests as you develop features.
- Cover all critical logic with automated tests (unit, integration, contract, load, and, if relevant, end-to-end).
- Use clear, descriptive names for test cases and functions.
- Keep tests isolated and independent from each other.
- Use mocks/stubs for external dependencies.
- Check for both expected and edge case behaviors.
- Run all tests before merging or releasing code.
- Track and report test coverage; aim for at least 85% where practical.
- Document how to run tests in the project README.

## References
- [architecture](../instructions/architecture.instructions.md)
