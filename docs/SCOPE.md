# MVP Scope

## In the MVP

The MVP now targets the first playable implementation of the approved `mechanika/` v1.0:

- Browser-first Phaser 4 app with TypeScript and Vite.
- PWA installable on Android.
- Pixel-art presentation with placeholder art where needed.
- Scene flow covering:
  - `BootScene`
  - `PreloadScene`
  - `MainMenuScene`
  - `BridgeScene`
  - `EventScene`
  - `CrewScene`
  - `SystemsScene`
  - `TorporScene`
  - `MapScene`
  - `LogbookScene`
  - `ApproachScene`
  - `EndingScene`
  - `GameOverScene`
- Crew roster for 7 characters plus ARIA context.
- Crew state: health, morale, fatigue, radiation, torpor rotation, and relations.
- Ship/system state for 13 systems including ECLSS dependencies.
- Resource model for `oxygen`, `water`, `food`, `fuel`, and `parts`.
- Mission model for 14 MVP missions and the LifeData track.
- Event model for 15 MVP events with forced/weighted structure and blue options.
- Save/load/autosave through IndexedDB + Dexie with logbook retention after permadeath.
- Narrative endings and hard game-over conditions defined in `mechanika/09-failure-and-game-over.md`.

## Not in the MVP

- Battle implementation beyond stub.
- Faction systems.
- Quest chains / quest beacons.
- Full trait-effect simulation beyond approved hooks.
- Broad XP trees and post-MVP progression systems.
- Life-discovery levels 4–6.
- Multiple starting ships.
- iOS support.
- Capacitor app shell.
- Full Playwright E2E suite.
- Final art polish.

## Open implementation blockers

These are already identified and must be resolved or explicitly deferred before coding the affected systems:

- Radiation baseline decision (`B1`)
- Captain torpor rule (`B7`)
- Language/i18n direction (`A3`, `D2`)
- Mission/event collision handling (`B4`)

## MVP scenes

| Scene | Status |
|---|---|
| `BootScene` | Required |
| `PreloadScene` | Required |
| `MainMenuScene` | Required |
| `BridgeScene` | Required |
| `EventScene` | Required |
| `CrewScene` | Required |
| `SystemsScene` | Required |
| `TorporScene` | Required |
| `MapScene` | Required |
| `LogbookScene` | Required |
| `ApproachScene` | Required in Act IV |
| `EndingScene` | Required |
| `GameOverScene` | Required |
| `BattleScene` | Stub only |

## MVP beacon / content statuses

| Type | Status |
|---|---|
| `event` | Required |
| mission travel / approach content | Required |
| `combat` | Stub/reserved |
| `quest` | Deferred |

## Scope-control rules

1. `mechanika/` is the gameplay source of truth; do not invent conflicting rules in code.
2. New ideas outside MVP go to `docs/IDEAS_LATER.md`, not directly to code.
3. New dependencies require an ADR in `docs/ADRs/`.
4. The first playable version can be visually rough.
5. If a feature depends on unresolved or deferred mechanics, keep it as a stub and stop there.
