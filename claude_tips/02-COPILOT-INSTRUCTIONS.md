# GitHub Copilot Instructions — Star Search

> **Instrukcja użycia**: Skopiuj cały tekst PONIŻEJ linii do pliku `.github/copilot-instructions.md` w roocie repozytorium. Copilot będzie automatycznie dołączał te instrukcje do każdego promptu.

---

# Project: Star Search (space management PWA)

## What this project is
A retro pixel-art space management game inspired by FTL: Faster Than Light, Crying Suns, and Out There. Player manages a crew, ship resources, and missions while traveling through procedurally-generated sectors. Browser-first (PWA), distributed as Android APK via Trusted Web Activity.

## Stack (DO NOT DEVIATE WITHOUT EXPLICIT PERMISSION)
- **Phaser 3.9x+** (NOT Phaser 4 — RC, less docs)
- **TypeScript 5.6+** with strict mode
- **Vite 6+** as bundler
- **vite-plugin-pwa** + Workbox for PWA / Service Worker
- **idb-keyval** for IndexedDB storage
- **Phaser.Events.EventEmitter** for cross-scene communication
- **seedrandom** (optional, only for seedable RNG)
- Hosting: **Cloudflare Pages** (or Netlify)
- Android: **Bubblewrap** CLI (TWA), or PWA Builder graphical alternative

## Code style
- **TypeScript strict mode** (`strict: true` in tsconfig).
- Always type function parameters and return types explicitly.
- Prefer **interfaces over type aliases** for object shapes.
- One class per file. File name = class/main export name (PascalCase.ts for classes, camelCase.ts for utilities).
- **JSDoc** for every public method/function: `@param`, `@returns`, one usage example.
- Naming:
  - `camelCase` for variables, functions, methods
  - `PascalCase` for classes, interfaces, types, enums
  - `UPPER_SNAKE_CASE` for module-level constants
  - `kebab-case` for asset filenames
- Constants at the top of the file, after imports.
- Avoid `any` — use `unknown` and narrow with type guards if necessary.
- Avoid magic numbers — extract to named constants with comments.

## Architecture rules
- **Phaser scenes** go in `src/scenes/` (one file per scene class).
- **Game systems** (singletons, no React state library) go in `src/systems/`.
- **Static game data** (events, ships, crew templates) in `src/data/*.json`.
- **Type definitions / interfaces** in `src/types/`.
- **UI overlays** (HTML/CSS over canvas) in `src/ui/`.
- **Utilities** (small, reusable, pure functions) in `src/utils/`.
- **No circular imports.** If two files import each other, refactor.
- **No business logic in scenes.** Scenes orchestrate; systems compute.

## Key conventions
- All randomness goes through `src/utils/rng.ts` (seedable for debug/replay).
- All persistence goes through `src/systems/SaveSystem.ts` (uses idb-keyval).
- All cross-scene communication uses `Phaser.Events.EventEmitter` on `GameState` singleton.
- All game data (events, ships) is **data-driven** — JSON in `src/data/`, never hardcoded in TS.
- Asset paths: `public/assets/<category>/<name>.png` (e.g. `public/assets/ships/scout.png`).
- Spritesheet atlases: PNG + JSON (Aseprite Hash format) loaded via `this.load.atlas()`.

## What NOT to do
- **DO NOT** introduce new dependencies without listing them in `docs/ADRs/` (Architecture Decision Records).
- **DO NOT** use Redux, Zustand, MobX — single GameState singleton is sufficient for this game's scope.
- **DO NOT** use rot.js or other large procedural-generation libraries — write small purpose-specific utilities.
- **DO NOT** use Capacitor or Cordova — we use TWA via Bubblewrap.
- **DO NOT** use `localStorage` — use IndexedDB via `idb-keyval`.
- **DO NOT** use React unless the project explicitly switches to `template-react-ts` (current default is `template-vite-ts` — vanilla TS).
- **DO NOT** import Phaser 4 syntax or features — we are on Phaser 3.
- **DO NOT** use `var` — only `let` and `const`.
- **DO NOT** use class inheritance for game entities — prefer composition (components/data) over deep inheritance.

## Audience and code style preferences
The repository owner is a **complete programming beginner** working with Copilot Pro+. Therefore:
- **Prefer clarity over cleverness.**
- Avoid advanced TypeScript features unless absolutely necessary: mapped types, conditional types, type-level programming, deep generics.
- Use **descriptive variable names**, even if longer.
- Add **inline comments** explaining "why", not "what".
- When generating code, **explain it briefly** in chat before/after the code block.
- When suggesting refactors, suggest **one small change at a time**, not large rewrites.

## Performance constraints (mobile-first)
- Target: smooth on a 3-year-old mid-range Android (e.g. Pixel 6a, Samsung A52).
- Aim for **60 FPS** on mobile during normal gameplay, **30 FPS minimum**.
- **Pool sprites** when possible — don't create/destroy in hot loops.
- **Atlas all sprites** — single texture per scene if feasible.
- Avoid heavy `setInterval` / `setTimeout` — use Phaser's `time.addEvent()` instead.
- Audio: prefer short SFX in OGG, music can be MP3 or OGG. Keep total audio < 5 MB.

## Accessibility
- All buttons should have keyboard equivalents (where it makes sense for a touch-first game, this means at least Enter/Space/Arrow keys).
- Color choices should pass WCAG AA contrast on critical UI text.
- Font size: minimum 14px on mobile, 16px preferred for body text.

## Testing philosophy
- For MVP: **write tests only for `weightedPick` and `SaveSystem`**. These are mission-critical.
- Use **Vitest** (native Vite integration, zero config).
- E2E testing in Playwright — **after MVP**, not during.
- No code coverage targets for MVP. Ship first, test more later.

## Git workflow
- Single `main` branch.
- Commit after every working piece (small, focused commits).
- Commit messages in English, format: `feat: add event system`, `fix: crew morale clamp`, `docs: update README`.
- Tag releases: `v0.1.0-mvp`, `v0.2.0-events`, etc.

## When in doubt
- Re-read this file.
- Check `01-PROJECT-PLAN.md` in repo root for design decisions.
- Ask the user before introducing new patterns.

---

# File-scoped instructions (use `.github/instructions/*.instructions.md`)

Below are stubs you can split into separate files with `applyTo:` frontmatter:

## .github/instructions/scenes.instructions.md
```
---
applyTo: "src/scenes/**"
---
- Each scene is a class extending `Phaser.Scene`.
- Constructor takes a unique scene key as string.
- Implement `preload()`, `create()`, `update()` as needed.
- DO NOT put business logic here — delegate to systems.
- Use `this.scene.start('SceneKey', dataObject)` for transitions.
- Listen to GameState events via `GameState.getInstance().events.on(...)`.
- Clean up listeners in `shutdown()` or `this.events.once('shutdown', ...)`.
```

## .github/instructions/systems.instructions.md
```
---
applyTo: "src/systems/**"
---
- Systems are singletons accessed via `getInstance()`.
- Systems hold state; scenes hold rendering.
- Systems emit events via internal `Phaser.Events.EventEmitter`.
- Systems are pure TypeScript — no Phaser scene references inside (avoid coupling).
- All async operations return Promises (no callbacks).
- Save/load operations go through SaveSystem only.
```

## .github/instructions/ui.instructions.md
```
---
applyTo: "src/ui/**"
---
- UI overlays use HTML/CSS, NOT Phaser game objects.
- Position via CSS (absolute, z-index above canvas).
- Mount/unmount via DOM manipulation in scene lifecycle.
- Listen to GameState events to re-render reactively.
- Touch-first: minimum 44×44 px touch targets.
- Pixel-perfect rendering: `image-rendering: pixelated;` on all `<img>` for sprites.
```
