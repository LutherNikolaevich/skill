# build

Goal: the smallest correct change, proven by a check.

## Before writing

1. Read the code the change touches and trace the real data flow. Be lazy about the solution, never about reading.
2. Climb the ladder and stop at the first rung that holds:
   1. Does this need to exist at all?
   2. Is it already in this codebase?
   3. Does the standard library do it?
   4. Does the platform do it natively?
   5. Does an installed dependency do it?
   6. Can it be one line?
   7. Only then: write the minimum that works.
3. Define the check first: a failing test, a repro command, or an observable result.

## While writing

- Red, green, refactor for logic. Write one failing test, watch it fail for the right reason, write the minimum to pass, then clean up. One slice at a time. Do not write all tests first.
- Test through public interfaces and behavior, not internals. Skip tests for trivial glue.
- Logic with a branch, loop, parser, money, or security leaves behind one small test.
- Match existing style, naming, and patterns even if you would do it differently.
- Do not add options, abstractions, or error handling for cases that cannot happen.
- Do not touch adjacent code, comments, or formatting. If you see unrelated dead code or bugs, mention them in one line. Do not fix them.
- Remove only the imports, variables, and functions your own change orphaned.
- When you cut a corner on purpose, leave a `shortcut:` comment with when to revisit.
- Never cut: validation at trust boundaries, handling that prevents data loss, security checks, accessibility.

## Deep modules

When adding structure, prefer a small interface hiding a lot of behavior over many shallow pieces. Do not add a layer for one caller.

## Ending

Run the check from step 3. Then follow `verify.md`. Report in the terse format: what changed, what was checked, what was skipped.
