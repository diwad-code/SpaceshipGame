# Architecture

## Position after Claude review

Claude's research pack is useful as a reference, but it is not the architecture authority. The accepted project architecture is:

- **Phaser 4 + TypeScript + Vite** for browser-first development.
- **PWA-first delivery**, then **TWA** if Google Play distribution is needed.
- **Capacitor is deferred** and only considered if native APIs become necessary.
- **IndexedDB via Dexie.js** for save data.
- **Data-driven gameplay**: crew, missions, events, ship systems, and resources are defined in data files and validated with Zod.

Claude proposals accepted:

- `scenes/`, `systems/`, `data/`, `types/`, `ui/`, `storage/`, `utils/` separation.
- Scenes orchestrate rendering and input; systems own business logic.
- Event definitions as JSON with weighted choices and requirements.
- `weightedPick` as a small tested utility.
- UI overlays for management screens where HTML/CSS is more accessible than canvas-only UI.
- Scope-control docs: `SCOPE.md`, `IDEAS_LATER.md`, and ADRs.
- Code review prompt focused on high-signal issues only.

Claude proposals rejected or modified:

- **Rejected:** "Phaser 3 only / no Phaser 4". The approved architecture stays on Phaser 4.
- **Rejected:** `idb-keyval` as the main save abstraction. Dexie.js remains approved because schema versioning and migrations matter for long-running save files.
- **Modified:** "No Capacitor ever" becomes "no Capacitor for MVP; consider only for native APIs post-MVP."
- **Deferred:** Battle, traits, progression, combat beacon logic, quest logic, and morale formulas until `mechanika/` arrives.

## Target project structure

```text
SpaceshipGame/
├── .github/
│   ├── copilot-instructions.md
│   ├── instructions/
│   │   ├── phaser.instructions.md
│   │   ├── data-driven.instructions.md
│   │   └── mobile-ux.instructions.md
│   ├── prompts/
│   │   ├── game-dev.prompt.md
│   │   ├── new-scene.prompt.md
│   │   ├── new-system.prompt.md
│   │   ├── new-event.prompt.md
│   │   ├── data-schema.prompt.md
│   │   ├── pwa-check.prompt.md
│   │   ├── mobile-ux.prompt.md
│   │   └── code-review.prompt.md
│   ├── agents/
│   │   ├── game-planner.agent.md
│   │   ├── game-architect.agent.md
│   │   └── game-reviewer.agent.md
│   └── skills/
│       ├── scaffold-scene/
│       │   └── SKILL.md
│       └── scaffold-system/
│           └── SKILL.md
├── public/
│   ├── manifest.json
│   └── assets/
├── src/
│   ├── main.ts
│   ├── data/
│   │   ├── schemas/
│   │   ├── crew.json
│   │   ├── missions.json
│   │   ├── events.json
│   │   ├── ship-systems.json
│   │   └── resources.json
│   ├── models/
│   ├── scenes/
│   ├── systems/
│   ├── state/
│   ├── storage/
│   ├── ui/
│   ├── types/
│   └── utils/
├── docs/
├── mechanika/
└── claude_tips/
```

## Source of truth order

When documents overlap, resolve conflicts in this order:

1. `mechanika/` for final gameplay mechanics.
2. `docs/SCOPE.md` for MVP boundaries and post-MVP exclusions.
3. `docs/ADRs/` for accepted technical decisions.
4. `docs/ARCHITECTURE.md` for project structure and system boundaries.
5. `.github/copilot-instructions.md` for day-to-day Copilot behavior.
6. `claude_tips/` as reference material only; it is not authoritative.

## Core systems

| System | MVP responsibility | Notes |
|---|---|---|
| `ShipSystem` | Ship hull/status/system health | No combat damage formula until `mechanika/`. |
| `CrewSystem` | Crew roster, assignments, health/morale clamps | Traits/progression are reserved fields only. |
| `MissionSystem` | Active mission state, mission steps, completion | Final mission mechanics wait for `mechanika/`. |
| `ResourceSystem` | Fuel, scrap, parts and resource deltas | Every resource needs an input and output. |
| `EventSystem` | Weighted random event selection and choice resolution | Effects must stay simple until mechanics spec arrives. |
| `LifeSearchSystem` | Search-for-life progress and discovery flags | Detailed discovery mechanics wait for `mechanika/`. |
| `SaveSystem` | Dexie save/load/autosave/schema versioning | `localStorage` is not allowed for primary saves. |

## Event model

Events should be data-driven and compatible with FTL-like "blue options":

```json
{
  "id": "abandoned_station_01",
  "title": "Opuszczona stacja",
  "weight": 5,
  "requirements": { "minFuel": 1 },
  "choices": [
    {
      "id": "investigate",
      "text": "Zbadaj wnętrze",
      "requires": { "crewSkill": "engineering", "minValue": 3 },
      "outcomes": [
        { "weight": 70, "text": "Znaleziono części.", "effects": [{ "resource": "parts", "delta": 3 }] },
        { "weight": 30, "text": "Wypadek przy eksploracji.", "effects": [{ "crewHealth", "delta": -1 }] }
      ]
    }
  ]
}
```

Combat-related requirements and death/permadeath effects are reserved until `mechanika/` defines the exact rules.

## Mechanics integration points

The following are allowed as **stubs or type placeholders only** until the user provides the `mechanika/` folder:

| Integration point | Allowed now | Not allowed yet |
|---|---|---|
| `BattleScene` | Stub with TODO | Combat implementation |
| `BattleSystem` | Stub with interface only | Damage formulas, enemy AI |
| `TraitSystem` | `traits: string[]` field | Trait effects |
| `ProgressionSystem` | `skills` fields | XP curves and level-up rules |
| `BeaconType.combat` | Enum value as reserved | Combat encounters |
| `BeaconType.quest` | Enum value as reserved | Quest chains |
| Morale | Numeric field and clamp | Detailed morale events/formulas |

## Mermaid overview

```mermaid
graph TB
    subgraph App["Browser / Android PWA"]
        Phaser["Phaser 4 scenes"]
        Systems["Pure TypeScript game systems"]
        Data["JSON data + Zod schemas"]
        Storage["IndexedDB + Dexie"]
        PWA["Service Worker + manifest"]
        UI["HTML/CSS management UI overlays"]
    end

    Phaser --> Systems
    Phaser --> UI
    Systems --> Data
    Systems --> Storage
    PWA --> App

    subgraph Future["Pending mechanika/"]
        Battle["BattleSystem / BattleScene"]
        Traits["TraitSystem"]
        Progression["ProgressionSystem"]
        Quest["Quest/combat beacon logic"]
    end

    Systems -. integration points .-> Future
```
