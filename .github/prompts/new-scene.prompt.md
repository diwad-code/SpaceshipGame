---
name: new-scene
description: 'Create a new Phaser 4 scene following SpaceshipGame architecture.'
agent: agent
model: gpt-5.4
tools:
  - search/codebase
  - edit/editFiles
  - read/problems
---

# /new-scene

Create or update a Phaser 4 scene for: `${input:sceneName}`.

Before editing:

1. Search existing scenes.
2. Check `.github/instructions/phaser.instructions.md`.
3. Check whether the requested scene depends on `mechanika/`.

Rules:

- Scene class name: `{Name}Scene`.
- File path: `src/scenes/{Name}Scene.ts`.
- Scenes orchestrate rendering and input only.
- Business logic belongs in systems.
- Register event listeners with cleanup on shutdown.
- If the scene is `BattleScene`, create only a stub with `TODO: pending mechanika/`.

After editing, summarize what was created and what still needs registration.
