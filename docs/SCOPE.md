# MVP Scope

## In the MVP

The MVP must prove the core management loop without waiting for final mechanics:

- Browser-first Phaser 4 app with TypeScript and Vite.
- PWA installable on Android.
- Pixel-art presentation with placeholder assets.
- Bridge/main management screen.
- Basic sector/map screen with beacons.
- Event screen with weighted choices.
- Crew roster with role, skills, health, morale, and reserved traits.
- Resource management for:
  - `fuel`
  - `scrap`
  - `parts`
- Save/load/autosave through IndexedDB + Dexie.
- At least 15 simple events.
- Basic "search for life" progress flag or track, without final discovery mechanics.

## Not in the MVP

- Battle implementation.
- Turn-based combat.
- Trait effects.
- Crew XP/progression curves.
- Complex morale simulation.
- Quest chains.
- Factions.
- Multiple starting ships.
- iOS support.
- Capacitor app shell.
- Full Playwright E2E suite.
- Final art polish.

## Reserved until `mechanika/`

Do not invent detailed rules for:

- combat,
- injuries/death beyond simple health changes,
- morale formulas,
- skill progression,
- quest logic,
- faction logic,
- life discovery scoring.

These must be integrated only after the user provides the `mechanika/` folder contents.

## MVP scenes

| Scene | Status |
|---|---|
| `BootScene` | Required |
| `PreloadScene` | Required |
| `MainMenuScene` | Required |
| `BridgeScene` | Required |
| `MapScene` | Required |
| `EventScene` | Required |
| `CrewScene` | Required |
| `BattleScene` | Stub only, pending `mechanika/` |

## MVP beacon types

| Type | Status |
|---|---|
| `empty` | Required |
| `event` | Required |
| `shop` | Optional |
| `distress` | Optional/simple event alias |
| `combat` | Reserved |
| `quest` | Reserved |

## Scope-control rules

1. New ideas go to `docs/IDEAS_LATER.md`, not directly to code.
2. New dependencies require an ADR in `docs/ADRs/`.
3. The first playable version can be visually rough.
4. If a feature depends on missing mechanics, add a stub and TODO, then stop.
