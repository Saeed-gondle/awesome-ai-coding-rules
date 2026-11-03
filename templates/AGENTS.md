# AGENTS.md

## Project

Describe the product in one sentence. Name the primary users and the riskiest domain rule.

## Stack

- Language/runtime: `<e.g. TypeScript 5.x + Node 22>`
- Package manager: `<pnpm>`
- Framework: `<e.g. Next.js App Router>`
- Database: `<e.g. Postgres + Drizzle>`
- Tests: `<e.g. Vitest + Playwright>`
- Deploy target: `<e.g. Cloudflare Workers>`

## Commands

```bash
<install>          # install dependencies
<dev>              # start local development
<lint>             # lint
<typecheck>        # type-check
<test>             # run the fast test suite
<test:integration> # run integration tests
<build>            # production build
```

Run the smallest relevant check first. Before claiming a task is complete, run `<lint>`, `<typecheck>`, and `<test>` and paste the actual output.

## Architecture boundaries

- `<path/>` owns `<responsibility>`. Do not move domain logic into route handlers.
- `<path/>` is generated. Never edit it by hand.
- Database changes live in `<migrations/>` and require a human-approved migration.
- Shared contracts live in `<packages/contracts>`. Update both producer and consumer.

## Working agreement

1. Restate the task and acceptance criteria before editing.
2. Read the relevant files. Do not invent APIs, fields, or commands.
3. Make the smallest coherent change.
4. Add or update a test that would fail without the change.
5. Run the verification commands and report exact results.
6. Stop after two failed attempts with the same error and explain the hypothesis.

## Definition of done

- The acceptance criteria are satisfied.
- Tests cover the new behaviour and the important failure path.
- Lint, type-check, and tests pass locally.
- No unrelated refactors or formatting churn.
- Documentation or changelog updated when behaviour changes.
- No secrets, customer data, or debug artefacts in the diff.

## Hard boundaries

- Never run `git push`, `git reset --hard`, `git clean -fd`, deploy commands, or destructive database commands.
- Never read or print `.env`, credentials, tokens, private keys, or production data.
- Never disable a test, lint rule, type check, or security check to make CI pass.
- Never add a dependency without explaining why the standard library or an existing dependency is insufficient.
- Ask before changing public APIs, billing logic, authentication, authorization, or data retention.

## Code style

- Follow the existing patterns in the nearest file.
- Prefer explicit types at module boundaries.
- Keep side effects at the edges; keep domain logic pure where practical.
- Error messages must state what failed and what the caller can do next.
- Comments explain *why*, not *what*.

## Review checklist

- [ ] Tenant isolation is preserved.
- [ ] Input validation happens at the trust boundary.
- [ ] Errors do not leak secrets or internal paths.
- [ ] Expensive operations have limits and timeouts.
- [ ] New user-visible behaviour has a test.