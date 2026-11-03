# CLAUDE.md

@AGENTS.md

## Claude Code workflow

- Use plan mode for changes that touch more than three files or any migration.
- Before editing, list the files you will change and the command that proves the change works.
- Prefer `rg` for search and read the surrounding implementation before proposing an edit.
- Use subagents for independent research or review, not for editing the same files in parallel.
- Keep a task note in `TODO.md` only while the task is active; remove it before finishing.

## Communication

- Lead with the result, then the evidence, then the remaining risk.
- Do not claim a command passed unless you ran it in this session and saw the output.
- If the repository contradicts these instructions, stop and ask which one is authoritative.