---
name: new-system
description: 'Create a new pure TypeScript game system following data-driven rules.'
agent: agent
model: gpt-5.4
tools:
  - search/codebase
  - edit/editFiles
  - read/problems
  - execute/runTests
---

# /new-system

Create or update a game system for: `${input:systemName}`.

Before editing:

1. Search existing systems.
2. Check `docs/ARCHITECTURE.md`.
3. Check `docs/SCOPE.md`.
4. Determine whether the requested system depends on `mechanika/`.

Rules:

- File path: `src/systems/{Name}System.ts`.
- Systems are pure TypeScript and should not depend on Phaser scenes.
- Use typed inputs/outputs.
- Keep state serializable.
- Add Vitest tests for deterministic logic when practical.
- If the system is `BattleSystem`, `TraitSystem`, or `ProgressionSystem`, create only a stub unless `mechanika/` defines the rules.
