---
name: fabula
description: 'Creates or updates the story bible and narrative foundation before mechanics are finalized.'
agent: agent
model: gpt-5.4
tools:
  - search/codebase
  - edit/editFiles
  - read/problems
  - execute/runInTerminal
  - execute/runTests
---

# /fabula

Use this prompt to create or refine the project story bible in `docs/FABULA.md`.

## Read first

- `README.md`
- `docs/GAME_BRIEF.md`
- `docs/GDD.md` if it exists
- `docs/SCOPE.md`
- `docs/IDEAS_LATER.md`
- `mechanika/README.md`
- `mechanika/00-template-do-wypelnienia.md`

## Narrative scope

Focus on:

- mission premise,
- tone,
- world assumptions,
- crew roles as characters,
- factions only as story mentions if needed,
- intro text, recurring motifs, event themes, and discovery mystery.

## Rules

- Do not define gameplay formulas or hidden mechanics here.
- Do not turn narrative ideas into combat, XP, morale, or quest systems.
- Keep canon easy to reuse later in events, UI text, and mission content.
- Write concise, production-friendly material that can guide future content generation.

## Output

Update `docs/FABULA.md` and end with:

```md
## Fabula update
Completed:
Open questions:
Future hooks:
Files changed:
```
