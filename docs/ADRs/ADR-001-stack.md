# ADR-001: Browser-first stack

## Status

Accepted.

## Context

The project is a solo-developed retro pixel-art spaceship management game. It must run in a browser and on Android phones/tablets. Development will happen in VS Code with GitHub Copilot Pro+.

Claude's research suggested Phaser 3, `idb-keyval`, Cloudflare Pages, and a strict no-Capacitor rule. Our previous research recommended Phaser 4, Dexie, PWA-first delivery, TWA later, and Capacitor only if native APIs become necessary.

## Decision

Use:

- **Phaser 4** for rendering/input/scenes.
- **TypeScript** with strict mode.
- **Vite** as the build tool.
- **PWA** for the MVP Android path.
- **TWA** for later Google Play distribution if native APIs are not needed.
- **Dexie.js over IndexedDB** for save data and migrations.
- **Zod** for validating data-driven content.
- **Vitest** for mission-critical logic tests.

## Consequences

- The project stays browser-first and easy to deploy.
- Save schema migration is available from day one.
- Copilot must be guided to use Phaser 4, because many examples online still target Phaser 3.
- The architecture remains independent of React/Redux/Zustand.
- Capacitor remains possible, but only after a specific native requirement appears.

## Alternatives rejected

| Alternative | Reason |
|---|---|
| Phaser 3 as a hard rule | More mature docs, but the approved architecture is Phaser 4 and the Copilot instructions will enforce that. |
| Godot 4 primary | Strong fallback, but less aligned with browser-first PWA workflow. |
| `idb-keyval` as primary save layer | Too small for future migrations; Dexie gives better structure. |
| `localStorage` | Synchronous, small, not suitable for save state. |
| Capacitor from day one | Adds Android build complexity before native APIs are required. |
| React UI from day one | Adds framework complexity; HTML/CSS overlays are enough for MVP. |
