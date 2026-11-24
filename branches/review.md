# review

Goal: review like the senior dev who gets paged when this breaks.

## Scope

Default: the current diff. Narrow or widen on request: uncommitted, staged, branch, a PR, a file, or the whole repo (audit). For an audit, map first: entry points, how data moves, expected load. Then review.

Read the code the change touches, not only the diff. A rename in one file can crash an untouched caller.

## Two axes

Run both. Keep them separate so one does not bias the other. Use parallel subagents when the diff is large and subagents are available.

1. **Spec**: does the change do what the issue, spec, or request asked? Nothing missing, nothing extra.
2. **Standards**: does it follow this repo's conventions, and is it free of common smells (duplication, long functions, shallow abstractions, speculative generality, dead code)?

## What to check

- Bugs and edge cases: empty, null, large, concurrent, malformed.
- Security: injection, path traversal, auth, secrets, unsafe input at trust boundaries.
- Real load: N+1 queries, unbounded loops or memory, missing limits.
- Risky logic without a test.
- Error handling that can lose data or fail silently.
- Code that can be deleted, reused from the repo, or replaced by the platform.
- Changes unrelated to the request (scope creep).

## Output

Most important first. One finding per line, with severity:

```
L42 [must] null deref when user has no email. Guard it.
src/routes/feed.js [must] untouched file now crashes: field renamed. Update caller.
L88 [should] no test for the parser branch.
L130 [cut] helper duplicates lib.parse. Delete.
```

Severity: `must` (blocks merge), `should` (fix soon), `nit` (optional), `cut` (delete).

For a `must`, add on the next line: what goes wrong, and what happens if skipped.

End with a verdict: fix X first, or "ok to merge". Say what you did not check.

## For a PR description

Smallest visual or plain summary that makes the change clear, evidence it works (before and after), and a merge-danger call: one-way or two-way door, plus blast radius.
