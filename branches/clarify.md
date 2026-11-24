# clarify

Goal: make sure you and the user mean the same thing before any work starts. Misalignment is the most expensive bug.

## When to run

- The request names an outcome but not the shape ("add auth", "make it faster", "build a dashboard").
- Two or more readings would produce different work.
- A design has branches nobody has decided.
- The user is thinking aloud and wants a sounding board.

Skip it for small, clear, reversible tasks. Ask nothing you can find out by reading the repo.

## How

1. Read first. Check the code, docs, and existing terms before asking.
2. Ask one question at a time. Put your recommended answer inside the question so the user can reply "yes".
3. Walk the decision tree top down: resolve the choice that blocks other choices first.
4. Use the project's own words. If a term is fuzzy or used two ways, pin it down and reuse the pinned term from then on. If the project keeps a glossary or decision records, update them when a term or hard decision settles.
5. Stress-test with one concrete edge case when a decision feels too easy.
6. Offer 2 or 3 approaches with trade-offs when the choice is real. Lead with the one you recommend.
7. When the picture is clear, play it back in a few sentences, in chunks small enough to read. Wait for a yes or a correction.

## Stop conditions

Stop questioning when remaining unknowns are cheap to change later. Say what you are assuming and move on.

## Output

A short confirmed summary: goal, constraints, decisions made, open items. Then continue into `plan.md` or `build.md`.
