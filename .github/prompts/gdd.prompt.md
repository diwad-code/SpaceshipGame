---
name: gdd
description: 'Builds or updates the Game Design Document while respecting mechanika gates.'
agent: agent
model: gpt-5.4
tools:
  - search/codebase
  - edit/editFiles
  - read/problems
  - execute/runInTerminal
  - execute/runTests
---

# /gdd

Use this prompt to maintain `docs/GDD.md` as the structured design reference.

## Read first

- `README.md`
- `docs/GAME_BRIEF.md`
- `docs/FABULA.md`
- `docs/ARCHITECTURE.md`
- `docs/SCOPE.md`
- `mechanika/README.md`
- `mechanika/00-template-do-wypelnienia.md`
- any refined files inside `mechanika/`

## Goals

- Translate the current project intent into a structured design doc.
- Keep narrative, UX, scope, and content plans aligned.
- Record placeholders and open questions instead of inventing blocked mechanics.

## Rules

- Treat `mechanika/` as the future gameplay source of truth.
- Keep sections explicit about status: approved now, reserved, or open question.
- Prefer tables, bullet lists, and short sections over long prose.
- Link to `docs/FABULA.md` for worldbuilding and story canon.

## Output

Update `docs/GDD.md` and end with:

```md
## GDD update
Completed:
Blocked by mechanika:
Open questions:
Files changed:
```
