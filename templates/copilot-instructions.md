# Copilot repository instructions

Follow `AGENTS.md` for architecture, commands, and boundaries.

## Review priorities

1. Correctness and data loss
2. Security and tenant isolation
3. Missing tests or unverified claims
4. Performance regressions on hot paths
5. Maintainability

Do not comment on formatting that the formatter already enforces. Do not suggest a new dependency when the standard library or an existing package is sufficient.

## Pull request expectations

- Explain the user-visible change in one paragraph.
- List the exact verification commands and results.
- Call out migrations, feature flags, and rollback steps.
- Disclose any AI-generated code that was not reviewed line by line.