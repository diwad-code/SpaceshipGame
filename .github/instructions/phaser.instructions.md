---
description: 'Rules for Phaser scenes and pixel-art rendering.'
applyTo: 'src/scenes/**/*.ts, src/ui/**/*.ts, src/main.ts'
---

# Phaser 4 instructions

- Use Phaser 4 APIs and verify examples that look like Phaser 3 code.
- Scenes must extend `Phaser.Scene`.
- Scenes may call systems, but must not contain business logic.
- Implement scene lifecycle methods only as needed: `init`, `preload`, `create`, `update`.
- Clean up event listeners on scene shutdown.
- Use `pixelArt: true` in Phaser config.
- Prefer `Phaser.Scale.FIT` and `Phaser.Scale.CENTER_BOTH`.
- Use texture atlases instead of many separate sprite images.
- Use pointer input APIs for mouse/touch compatibility.
- `BattleScene` is a stub only until `mechanika/` defines combat.
