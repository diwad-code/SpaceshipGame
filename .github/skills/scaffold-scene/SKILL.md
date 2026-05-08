---
name: scaffold-scene
description: 'Creates a Phaser 4 scene scaffold that follows SpaceshipGame architecture, lifecycle cleanup, and mechanika integration rules.'
---

# Scaffold Scene

Use this skill when creating scenes under `src/scenes/`.

Rules:

- Use Phaser 4.
- Class name: `{Name}Scene`.
- File path: `src/scenes/{Name}Scene.ts`.
- Do not put business logic in the scene.
- Subscribe to shared events only with shutdown cleanup.
- If the requested scene is mechanics-dependent, create a stub and reference `mechanika/`.

Template:

```ts
import Phaser from 'phaser';

export class ExampleScene extends Phaser.Scene {
  constructor() {
    super({ key: 'ExampleScene' });
  }

  create(): void {
    this.events.once(Phaser.Scenes.Events.SHUTDOWN, () => {
      this.cleanup();
    });
  }

  update(_time: number, _delta: number): void {
    // Rendering/input orchestration only. Business logic belongs in systems.
  }

  private cleanup(): void {
    // Remove external listeners here.
  }
}
```
