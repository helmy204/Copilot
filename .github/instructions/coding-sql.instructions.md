---
applyTo: '**/*.{sql}'
---

# SQL Coding Standards
This document outlines the SQL coding standards for the project. Adhering to these standards will ensure that our SQL code is consistent, readable, maintainable, and safe across all repositories.

## General Guidelines
- Use clear, descriptive names for tables, columns, indexes, and other database objects.
- Write readable SQL queries by:
  - Use consistent formatting for SQL statements (e.g., line breaks, indentation).
  - Use meaningful aliases for tables and columns to improve readability.
  - Use uppercase for SQL keywords (e.g., `SELECT`, `FROM`, `WHERE`).
  - Use pascalCase for table and column names (e.g., Users, Orders).
  - Use camelCase for table and column names (e.g., userId, orderDate).
  - Avoid using reserved keywords as identifiers (e.g., table names, column names).
- Avoid using `SELECT *`; specify the columns you need.
- Use parameterized queries to prevent SQL injection attacks.
- Comment complex SQL queries to explain the logic and purpose of the code.
- Test queries for correctness and performance before using them.
- NEVER hardcode sensitive information (e.g., database credentials) in SQL scripts.
- Use `JOIN`s instead of subqueries where possible for better performance.
- Always include a `WHERE` clause in `UPDATE` and `DELETE` statements to prevent accidental data loss.
- Use transactions for operations that involve multiple steps to ensure data integrity.

## Reference Instructions
- Follow [general coding standards](../instructions/coding.standards.instructions.md)
- Follow [quality guidelines](../instructions/quality.instructions.md)
- Follow [security guidelines](../instructions/security.instructions.md)