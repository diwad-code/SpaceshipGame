# Game Design Document

## Status model

- **Approved** — already defined in `mechanika/` and safe to implement.
- **Deferred** — intentionally out of MVP or still limited to stubs.
- **Open question** — tracked blocker that needs a decision before or during implementation.

## Source stack

- Product brief: `docs/GAME_BRIEF.md`
- Narrative canon: `docs/FABULA.md`
- Mechanics source of truth: `mechanika/`
- MVP boundary: `docs/SCOPE.md`
- Technical structure: `docs/ARCHITECTURE.md`

## Current design snapshot

### Core loop — Approved

One turn is one rotation cycle: awakening, assignment, event, resolution, torpor.  
The mission spans ~174 turns across 5 acts and keeps pressure on crew state, ship systems, resources, and discovery progress.

### MVP content volume — Approved

- 14 gameplay scenes plus `BattleScene` as stub (`mechanika/02-screens-and-scenes.md`)
- 5 core resources + ECLSS/system-health layer (`mechanika/03-resources.md`, `mechanika/05-ship-systems.md`)
- 7 crew members + ARIA, torpor rotation, relations, inner voices (`mechanika/04-crew.md`, `mechanika/08-progression.md`)
- 14 mission types and LifeData discovery track (`mechanika/06-missions.md`)
- 15 MVP events: 6 forced, 9 weighted (`mechanika/07-events.md`)
- 5 hard game-over conditions and 6 narrative endings (`mechanika/09-failure-and-game-over.md`)

### Still deferred after mechanika v1.0

- Battle implementation beyond stub
- Full trait-effect system beyond approved trait hooks
- Quest/faction systems
- Post-MVP life-discovery levels 4–6
- Broader XP trees, difficulty modes, and other ideas parked in `docs/IDEAS_LATER.md`

## Implementation-readiness notes

### Approved implementation anchors

- Systems should be data-driven and read gameplay values from `mechanika/`-derived data files.
- Mobile-first layouts, overlay structure, and scene order are already specified.
- Saves must preserve autosave, permadeath cleanup, and logbook retention.

### Critical blockers before scaffolding logic

- **B1 — Radiation baseline**: sync the final numeric decision across resources, crew, and balancing docs.
- **B7 — Captain torpor rule**: decide whether Jakub torpor is optional or mandatory.

### Important near-term decisions

- Language/i18n direction (`A3`, `D2`)
- Mission/event collision behavior (`B4`)
- Felix solo-path for M14 (`B6`)
- Third Quarter morale pressure tuning (`C2`)

## Action plan

1. Keep repo docs aligned with `mechanika/` as the gameplay source of truth.
2. Resolve the critical blockers in `mechanika/99-open-questions.md` (`B1`, `B7`).
3. Scaffold the Vite + TypeScript + Phaser 4 project from the approved architecture.
4. Convert approved mechanics into data schemas first: resources, crew, ship systems, missions, events.
5. Implement the first playable loop in scene/system order from `mechanika/02-screens-and-scenes.md`.
6. Use early playtests to verify balance items listed in `mechanika/10-balancing-notes.md`.

## Documentation workflow

1. Update `docs/GAME_BRIEF.md` only when product framing changes.
2. Update `docs/FABULA.md` only when canon changes.
3. Update `docs/GDD.md` when implementation order, scope, or blockers change.
4. Update `mechanika/` when gameplay rules themselves change.
