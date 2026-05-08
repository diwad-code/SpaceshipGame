# Prompt File — Generate New Phaser Scene

> **Instrukcja użycia**: Skopiuj cały tekst PONIŻEJ linii do pliku `.github/prompts/new-scene.prompt.md` w repozytorium. Wywołasz w Copilot Chat poleceniem `/new-scene`.

---

```
---
description: Scaffold a new Phaser 3 scene with proper structure
mode: agent
---

Goal: Create a new Phaser 3 scene class in `src/scenes/` and register it in the main game config.

## Scene name
Ask user for scene name in PascalCase (e.g., `BattleScene`, `ShopScene`, `StarMapScene`).

## File template

📂 `src/scenes/<SceneName>.ts`

```typescript
import Phaser from 'phaser';
import { GameState } from '../systems/GameState';

/**
 * <SceneName> — <one-sentence description of scene purpose>.
 * 
 * Lifecycle:
 * - preload(): load scene-specific assets
 * - create(): set up game objects, UI, input handlers
 * - update(time, delta): per-frame logic (only if needed)
 */
export class <SceneName> extends Phaser.Scene {
  private gameState!: GameState;

  constructor() {
    super({ key: '<SceneName>' });
  }

  init(data?: unknown): void {
    // Receive data from previous scene if any
    this.gameState = GameState.getInstance();
  }

  preload(): void {
    // Load assets specific to this scene
    // Example: this.load.atlas('ships', 'assets/ships.png', 'assets/ships.json');
  }

  create(): void {
    // Build scene
    // Example: this.add.image(400, 300, 'background');

    // Subscribe to game state events
    this.gameState.events.on('resource-changed', this.handleResourceChange, this);

    // Clean up on scene shutdown
    this.events.once('shutdown', this.cleanup, this);
  }

  update(_time: number, _delta: number): void {
    // Per-frame updates (omit method body if not needed)
  }

  private handleResourceChange(type: string, value: number): void {
    // React to game state changes
  }

  private cleanup(): void {
    // Unsubscribe listeners to prevent memory leaks
    this.gameState.events.off('resource-changed', this.handleResourceChange, this);
  }
}
```

## Registration

After creating the scene file, also:

1. Open `src/main.ts` (or wherever the Phaser game config is defined).
2. Import the new scene: `import { <SceneName> } from './scenes/<SceneName>';`
3. Add it to the `scene` array in the Phaser game config:
   ```typescript
   scene: [BootScene, MenuScene, MapScene, <SceneName>]
   ```
4. **DO NOT** auto-start the scene unless explicitly requested. Scenes are usually started via `this.scene.start('<SceneName>', dataObject)` from another scene.

## Reminder for the user
After creating the scene, suggest:
- "To navigate to this scene from elsewhere, call: `this.scene.start('<SceneName>')`"
- "If you need to pass data: `this.scene.start('<SceneName>', { someKey: someValue })` — receive it in `init(data)`"
- "Run `npm run dev` and check the console for any TypeScript errors."
```
