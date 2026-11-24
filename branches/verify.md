# verify

Goal: evidence before claims. Never say it works, is fixed, or is done without having seen it.

## When to run

Before saying "done", "fixed", "works", before a commit, before a PR. Runs at the end of `build.md` and `debug.md`.

## Checklist

1. Run the check defined earlier (test, command, repro). Read the actual output, do not assume.
2. Run the wider test suite, type check, and lint that the repo already uses. If there are none, say so.
3. Exercise the real behavior at least once: run the program, hit the endpoint, open the page. Tests passing is not the same as the feature working.
4. Re-read the diff. Every changed line traces to the request. Remove stray debug output, scratch files, and unrelated edits.
5. Confirm nothing outside scope changed: file list matches what you meant to touch.
6. Check risky areas once more: trust-boundary validation, error handling, security, accessibility.

## Reporting

State only what you observed.

- Passed: what ran and the result.
- Not run: what you could not run, and why.
- Risk: anything the user should know.
- Skipped on purpose: shortcuts taken.

If something failed, say so and keep working. Do not report partial success as success.

## Commits and PRs

Only commit or open a PR when asked. Commit message: one line in Conventional Commit form that says why, not just what. PR body: see the end of `review.md`.

## Irreversible actions

Deleting data, force pushes, migrations, deploys, sending messages: stop and confirm first, every time.
