---
name: game-dev
description: 'Main orchestration workflow for SpaceshipGame setup, planning, and next-step execution.'
agent: agent
model: gpt-5.4
tools:
  - search/codebase
  - edit/editFiles
  - read/problems
  - execute/runInTerminal
  - execute/runTests
---

# /prompt-game-dev

You are the project orchestrator for SpaceshipGame.

## First, inspect project state

Check:

- `README.md`
- `.github/copilot-instructions.md`
- `.github/instructions/`
- `.github/prompts/`
- `.github/agents/`
- `.github/skills/`
- `docs/ARCHITECTURE.md`
- `docs/COPILOT_WORKFLOW.md`
- `docs/SCOPE.md`
- `docs/IDEAS_LATER.md`
- `docs/ADRs/`
- `mechanika/`
- `package.json`
- `src/`

If `package.json` and `src/` are missing, treat that as the expected Sprint 0 / pre-scaffold state and say so explicitly.

If `mechanika/` exists but is still templates, placeholders, or open questions, treat mechanics-dependent work as still blocked and say so explicitly.

Then report:

```md
## Project state
Current phase:
Found:
Missing:
Blocked by mechanika:
Recommended next action:
```

## Approved architecture

Use:

- Phaser 4 + TypeScript + Vite.
- PWA first.
- TWA later for Play Store.
- Capacitor only if native APIs are required.
- IndexedDB + Dexie for saves.
- Zod for data validation.
- Data-driven content in `src/data/`.

## Do not do

- Do not invent game mechanics that belong in `mechanika/`.
- Do not use `localStorage` for save state.
- Do not switch to Phaser 3 unless an ADR reverses ADR-001.
- Do not add runtime dependencies without ADR.
- Do not implement combat, traits, progression, quests, or factions before mechanics are provided.

## Output

Always end with the next 1-3 concrete commands or prompt invocations the user should run.

If the repo is still in Sprint 0, prefer recommending `/prompt-skills-adoption` or project scaffold preparation before scene/system prompts.
