---
applyTo: "**/*"
---
# Security Guidelines

These guidelines establish mandatory, production-grade security practices. They are required for all modules and repositories that import this instruction set. All code must be secure by default and follow best practicies for production environments.

Always refer to the latest project instructions ([project.instructions.md](../instructions/project.instructions.md)) for architecture and integration context

Always refer to the latest OWASP Top Ten list for web application security risks: https://owasp.org/www-project-top-ten/

## Authentication
- Use strong authentication mechanisms (e.g., OAuth2, OpenID Connect).
- Set short token expiration times (e.g.,1 hour or less) and implement refresh tokens on user activity.
- Enforce secure password policies and multi-factor authentication (MFA) where applicable.
- Ensure all authentication tokens are transmitted over secure channels (TLS/HTTPS).

## Data Protection
- Encrypt all sensitive data (including PII) at rest using strong encryption algorithms (e.g., AES-256).
- Encrypt all data in transit using TLS 1.2 or higher.
- Limit PII and sensitive data exposure in logs, API responses, and error messages.
- Apply data minimization and retention policies to reduce risk.

## Thread Modeling & Mitigation
- Mitigate all common threats: SQL injection, XSS, CSRF, privilege escalation, SSRF, IDOR and all identified in the OWASP Top Ten list.
- Use strict input validation, output encoding, CSRF tokens, and least priviledge principles.
- Perform regular threat modeling exercises and security reviews during design and development phases.

## Secure Coding Practices
- Follow secure coding standards (e.g., OWASP Secure Coding Practices).
- Never hardcode secrets, API keys, or credentials in source code.
- Use secure secret management solutions (e.g., vaults, Azure Key Vault, environment variables with restricted access).
- Sanitize and validate all user inputs and data types to prevent injection attacks.
- Log security-relevant events for auditability, and protect logs from unauthorized access and do not log sensitive information.
- Apply secure default configurations and disable unnecessary and insecure features or services.
- Regularly update dependencies and libraries to patch known vulnerabilities.
---

## Reference Instructions
- Follow [copilot instructions](copilot.instructions.md)
- Follow [project instructions](../instructions/project.instructions.md)