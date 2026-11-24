# czx

One agent skill, always on. It reads the request, picks the right branch by intent, and replies tersely. You never name it or a branch.

## Layout

```
czx/
  SKILL.md              router + always-on rules
  README.md
  branches/
    clarify.md          align before building
    plan.md             slices, checks, ordering
    build.md            least code, test-first, surgical
    debug.md            feedback loop, root cause, regression test
    review.md           bugs, security, spec + standards
    architect.md        deep modules, shared language
    verify.md           evidence before claims
    handoff.md          session summary and retro
    terse.md            reply style
```

## Where each idea comes from

| Source | What czx takes |
|---|---|
| mattpocock/skills | clarify (grilling), plan (tracer-bullet slices), debug loop, TDD, deep modules, two-axis review, handoff |
| obra/superpowers | skills trigger automatically before work, design before code, plan then execute, red/green TDD, evidence before completion |
| karpathy skills | think before coding, simplicity first, surgical changes, goal-driven execution |
| ponytail | the reuse ladder, never cut validation or security, `shortcut:` comments, review that reads beyond the diff |
| caveman | answer-first terse voice, payload verbatim, never drop negations, drop style for warnings |

## Install

Claude Code (user level):

```
mkdir -p ~/.claude/skills
cp -r czx ~/.claude/skills/czx
```

Project level: copy to `.claude/skills/czx` in the repo. Other agents that read `SKILL.md` skills: copy the folder to that agent's skills directory.

## How auto-triggering works

The `description` in `SKILL.md` front matter is what the agent matches against. It lists the situations (build, fix, review, plan, design, explain, technical questions), so the skill loads without the user naming it. Inside, the routing table picks the branch.

If it fires too rarely, make the description more eager. If it fires on non-technical chat, narrow it.

## Switching off the voice

Say "normal mode" or "stop terse". Rules 1 to 3 stay on.
