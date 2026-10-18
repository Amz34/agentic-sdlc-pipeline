# SDLC Rule 05: Code Review & Security Standards

## 1. Zero Credential Leakage
- Never commit secrets, API keys, private tokens, or connection strings.
- Always use environment variables or secret vaults.

## 2. Automated Quality Gates
- **Type Safety:** Zero compiler errors (`tsc --noEmit` or mypy).
- **Linting:** Zero unhandled linter errors.
- **Security Audit:** All external parameters must be sanitized and validated before database or shell execution.

## 3. Human in the Loop
- Automated review tools (e.g. CodeRabbit, AI reviewer) provide feedback, but final PR approval requires human sign-off.
