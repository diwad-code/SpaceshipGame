---
name: scaffold-system
description: 'Creates a pure TypeScript game system scaffold with serializable state and no Phaser scene coupling.'
---

# Scaffold System

Use this skill when creating systems under `src/systems/`.

Rules:

- System file path: `src/systems/{Name}System.ts`.
- Do not depend on Phaser scenes.
- Keep inputs and outputs typed.
- Keep state serializable.
- If the system depends on combat, traits, progression, morale formulas, quests, or factions, create only a stub until `mechanika/` defines the rules.
- Add tests for deterministic logic when practical.

Template:

```ts
export interface ExampleSystemState {
  version: number;
}

export class ExampleSystem {
  private state: ExampleSystemState;

  constructor(initialState: ExampleSystemState = { version: 1 }) {
    this.state = initialState;
  }

  getState(): ExampleSystemState {
    return this.state;
  }

  reset(): void {
    this.state = { version: 1 };
  }
}
```
