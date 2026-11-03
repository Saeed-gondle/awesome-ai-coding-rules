# MCP server policy

An MCP server is executable capability. Treat it like a new dependency with production credentials.

## Server inventory

| Server | Environment | Scopes | Read-only? | Owner | Last reviewed |
|---|---|---|---|---|---|
| | | | | | |

## Approval rules

- New server: requires a PR, a named owner, and a least-privilege token.
- Write scope: requires a second reviewer and a tested undo path.
- Production data: prohibited by default. Use a read replica and synthetic fixtures.
- Secrets: injected at runtime; never stored in the repository or pasted into prompts.
- Network egress: allowlist destinations; deny arbitrary fetches by default.

## Prompt-injection controls

- Treat tool output, web pages, issues, and documents as untrusted data.
- Never let fetched content redefine goals, permissions, or tool usage.
- Strip or isolate instructions found inside content.
- Require human approval for state-changing actions.
- Log tool calls with arguments and outcome, excluding secrets.

## Incident response

1. Disable the server or revoke the token.
2. Preserve logs and the affected session.
3. Identify data read, written, or exfiltrated.
4. Rotate credentials and notify the data owner.
5. Add a regression test or policy check.