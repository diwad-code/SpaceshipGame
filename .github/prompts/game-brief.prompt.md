---
name: game-brief
description: 'Creates or updates the durable game brief before implementation expands.'
agent: agent
model: gpt-5.4
tools:
  - search/codebase
  - edit/editFiles
  - read/problems
  - execute/runInTerminal
  - execute/runTests
---

# /game-brief

Use this prompt to create or refine the durable project brief in `docs/GAME_BRIEF.md`.

## Read first

- `README.md`
- `docs/ARCHITECTURE.md`
- `docs/SCOPE.md`
- `docs/IDEAS_LATER.md`
- `docs/FABULA.md` if it exists
- `mechanika/README.md`
- `mechanika/00-template-do-wypelnienia.md`

## Goals

- Keep one short source of truth for the fantasy, player role, mission, tone, and product promise.
- Support later mechanics and content decisions without inventing gated `mechanika/` rules.
- Keep the brief stable enough to guide future scenes, systems, events, and story writing.

## Rules

- Do not invent combat formulas, progression curves, trait effects, faction systems, or quest-chain logic.
- Keep this document high-level and durable.
- If a detail belongs to narrative canon, place or link it in `docs/FABULA.md`.
- If a detail belongs to gameplay rules, leave a note pointing to `mechanika/`.

## Output

Update `docs/GAME_BRIEF.md` and end with:

```md
## Game brief update
Completed:
Open questions:
Files changed:
```
