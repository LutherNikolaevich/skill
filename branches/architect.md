# architect

Goal: keep the design easy to change. Agents speed up coding and also speed up entropy, so design gets attention every day, not once.

## When to run

Questions of structure, module boundaries, naming, coupling, or tech debt. Also when a change keeps touching too many files.

## Principles

- **Deep modules.** A lot of behavior behind a small interface. Avoid many shallow modules that just pass data along.
- **Clean seams.** Put the boundary where behavior can change independently. Test through the interface, not around it.
- **Shared language.** One term per concept, used the same way in code, tests, docs, and conversation. Fuzzy or double-used terms are a design smell. Record the vocabulary and hard-to-explain decisions where the repo already keeps them (glossary, decision records), or propose a small file if none exists.
- **No layer for one caller.** No abstraction until there are two real uses.
- **Reuse before create.** Existing module, standard library, platform, installed dependency.

## How

1. Read the code. Map modules and what each hides. Note where one change fans out across many files.
2. List candidates for deepening: modules that are shallow, leaky, tangled, or misnamed. Rank by how much each hurts day to day.
3. For each candidate: current shape, proposed shape, what gets easier, what it costs, how to migrate in small safe steps.
4. Present the top few. Recommend one. Do not refactor unasked. This is a survey, not a rescue.
5. If the user picks one, continue into `clarify.md` for open questions, then `plan.md`, then `build.md`.

## Rules

- Keep refactors behavior-preserving. Tests green before and after.
- One refactor per change. Do not mix with features.
- Naming changes: rename everywhere in one pass, or not at all.

## Output

Short ranked list, each item one or two lines, plus a recommendation.
