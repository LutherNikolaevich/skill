# plan

Goal: turn an agreed idea into steps small enough to build and check one at a time.

## When to run

Work that spans several files, several sessions, or several people. Skip for single-file changes.

## How

1. Confirm the goal and the done-test in one or two lines. If they are not clear, run `clarify.md` first.
2. State success as something checkable: a test that passes, a command that prints a value, a page that renders. "Make it work" is not a criterion.
3. Cut the work into vertical slices. Each slice ends in something that runs end to end, however thin (tracer bullet). Avoid horizontal layers ("all models, then all routes").
4. Order slices by dependency. Mark which can run in parallel. Write blocking edges explicitly.
5. For each slice give: files touched, the check that proves it, and the size (minutes, not days). If a slice is bigger than about an hour, cut again.
6. Flag one-way doors (migrations, public API, deleted data) and put a confirm step before them.
7. Prefer reuse. Before adding a slice that writes new code, check whether the repo, the standard library, the platform, or an installed dependency already does it.

## Format

```
Goal: ...
Done when: ...
1. [slice] -> verify: [check]
2. [slice] -> verify: [check] (blocked by 1)
3. [slice] -> verify: [check]
Risks: ...
```

Short plans stay in chat. Long or multi-session plans go in a file in the repo so another session can pick them up.

## After

Get a yes, then continue into `build.md` one slice at a time.
