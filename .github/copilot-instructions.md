# Copilot Instructions — SpaceshipGame / Star Search

## Project

Retro pixel-art spaceship management game. The player manages a ship, crew, missions, resources, and random incidents during a search-for-life mission.

The project is browser-first and targets Android through PWA first, then TWA if Play Store distribution is needed.

Game mechanics details will be delivered separately in the `mechanika/` folder. Until then, mechanics-dependent systems are integration points only. Do not invent combat, trait effects, morale formulas, XP curves, factions, or quest-chain logic.

## Approved stack

- Engine: Phaser 4
- Language: TypeScript, strict mode
- Build tool: Vite
- PWA: vite-plugin-pwa + Workbox
- Saves: Dexie.js over IndexedDB
- Data validation: Zod
- Unit tests: Vitest
- E2E tests: Playwright after MVP
- Android MVP: PWA install
- Android Play Store later: TWA / Bubblewrap
- Capacitor: deferred; only if native APIs are required

## Architecture rules

- Phaser scenes go in `src/scenes/`.
- Pure game logic systems go in `src/systems/`.
- Runtime state models go in `src/models/` or `src/types/`.
- Data files go in `src/data/`.
- Zod schemas go in `src/data/schemas/`.
- Save/load code goes in `src/storage/`.
- UI overlays go in `src/ui/`.
- Shared utilities go in `src/utils/`.
- Scenes orchestrate rendering and input; systems compute business logic.
- Do not put business logic in Phaser scenes.
- Do not add circular imports.
- Keep save state serializable.

## Data-driven rules

- Crew, missions, events, ship systems, resources, and balancing values must come from data files.
- Do not hardcode gameplay values in systems.
- Validate all game data with Zod during boot/preload.
- Adding a simple event/mission/crew template should not require changing system logic.

## Save rules

- Do not use `localStorage` for primary game saves.
- Use Dexie.js and IndexedDB for save slots, autosave, and schema migrations.
- Include save schema versioning from the start.
- Cache static assets through the service worker, not through the save system.

## Mobile-first rules

- Touch targets for UI controls should be at least 48x48dp.
- Compact width `< 600dp`: one primary panel, use bottom sheets/overlays.
- Medium width `600-840dp`: allow a side panel.
- Expanded width `840dp+`: use a persistent two-column management layout.
- Respect safe areas on mobile.
- Use `image-rendering: pixelated` for canvas/assets that should stay pixel-sharp.

## Pixel-art rules

- Prefer a logical 16:9 resolution such as 480x270 or 320x180.
- Phaser config should use `pixelArt: true` and disable antialiasing where applicable.
- Use texture atlases for sprites.
- Avoid final art polish before the core loop is playable.

## Mechanics pending `mechanika/`

Allowed now:

- Stub `BattleScene` / `BattleSystem`.
- `traits: string[]` field on crew models.
- Skill fields and morale fields.
- Reserved beacon types such as `combat` and `quest`.

Not allowed before `mechanika/`:

- Combat damage formulas.
- Enemy AI.
- Trait effects.
- XP/progression curves.
- Complex morale logic.
- Quest-chain logic.
- Faction systems.

## Dependencies

Do not introduce new runtime dependencies without adding an ADR under `docs/ADRs/`.

## Testing philosophy

For MVP, prioritize tests for:

- weighted random selection,
- save/load/migration,
- resource deltas,
- event choice resolution.

Do not block MVP on broad coverage targets.

## Copilot workflow

- Use `/game-dev` for project orchestration.
- Use `/new-scene` for Phaser scenes.
- Use `/new-system` for systems.
- Use `/new-event` for event data.
- Use `/data-schema` for JSON + Zod models.
- Use `/pwa-check` before mobile testing.
- Use `/mobile-ux` for phone/tablet UI review.
- Use `/code-review` after implementation chunks.

These custom slash commands come from the `name:` field in each file under `.github/prompts/`.
