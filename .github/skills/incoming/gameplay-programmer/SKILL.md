---
name: gameplay-programmer
description: 'Stages implementation-oriented gameplay guidance for when approved mechanics start turning into systems.'
---

# Gameplay Programmer

Use this staged skill when approved mechanic specs need to be translated into clean systems and scene integration.

## Intended SpaceshipGame use

- map approved `mechanika/` rules into `src/systems/`,
- keep gameplay logic data-driven and testable,
- support integration between systems, schemas, and scenes once the app exists.

## Files it may touch

- `src/systems/`,
- `src/data/`,
- `src/models/` and `src/types/`,
- tests for gameplay logic.

## Source

- recommendation source: `SKILLS_RECOMMENDATIONS.txt` (MCP Market skills shortlist),
- adapted locally as a staged skill definition.

## Current gate

- `app scaffold`,
- approved mechanic specs in `mechanika/` for any non-stub behavior.

## Current blockers / open questions

- no `src/` tree yet,
- no gameplay systems yet,
- pending mechanic approval for combat, traits, progression, morale, factions, and quest logic.

## Adaptation notes

- scenes orchestrate; systems own business logic,
- keep saves serializable and data-driven,
- if a mechanic is still blocked, generate only a stub and stop.
