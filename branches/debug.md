# debug

Goal: find the root cause, fix it, and prove it stays fixed. Guessing is the failure mode.

## Phases (do not skip ahead)

### 1. Build a feedback loop
Get a fast, deterministic signal that goes red on this bug: a failing test, a script, a curl, a replayed input. Without it you are guessing. If the bug is flaky, raise the rate (loop it, add load, pin seeds, control time) until it fails often enough to learn from.

### 2. Minimise
Shrink the repro: fewer inputs, fewer files, fewer steps. Remove everything that does not change the outcome.

### 3. Hypothesise
Write 2 or 3 specific, falsifiable causes, ranked. Each says what you would observe if it were true. Read the code on the failing path. Check recent changes near it.

### 4. Instrument
Add the narrowest logging or probe that separates the hypotheses. Observe, do not assume. Change one thing at a time. Follow the bad value backward to where it first went wrong, not where it crashed.

### 5. Fix
Fix the cause, not the symptom. One small change. No drive-by cleanup. If the fix needs a design change, say so and ask before doing it.

### 6. Prove
- Turn the repro into a regression test. It must fail without the fix and pass with it.
- Run the wider suite.
- Remove your temporary instrumentation.

## Rules

- State the hypothesis before each probe.
- If three fixes in a row fail, stop. The model of the problem is wrong. Go back to phase 1 and question the assumptions or ask the user.
- Performance bugs: measure first, with a baseline number. Never optimize unmeasured.
- Say "not reproduced" when it is. Do not claim a fix you could not observe.

## Report

Root cause in one sentence. The fix. The test that guards it. What you could not check.
