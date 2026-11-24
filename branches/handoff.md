# handoff

Goal: let a fresh agent or a returning human continue without rereading the whole conversation.

## When to run

End of a session, switching agents or tools, a long conversation near its limit, or the user asks "where are we", "summarize", or "retro".

## Handoff document

Short, in a file or in chat depending on length. Sections:

1. **Goal**: what we are building and why, in two lines.
2. **State**: done, in progress, not started. Name files and branches.
3. **Decisions**: what was chosen and the reason. Include rejected options worth not revisiting.
4. **Next**: the very next action, then the ones after it, each with its check.
5. **Gotchas**: traps, flaky tests, commands that need special flags, things that looked wrong but are fine.
6. **Open questions**: for the user.
7. **How to verify**: exact commands.

Link to files instead of pasting their contents. Use the project's own vocabulary.

## Retro (when asked, or after a rough session)

List what slowed the session down, most severe first, each with a concrete fix to the agent's environment:

- missing or slow checks (tests, types, lint)
- unclear conventions that should be in the repo's agent instructions
- navigation problems (hard-to-find code, misleading names)
- tooling gaps

One line per item: problem, then fix. Do not edit the environment unasked.

## Rules

- Facts only. No speculation presented as state.
- If something was not verified, say so.
- Keep it under one screen where possible.
