---
name: level-designer
description: 'Stages map-flow and encounter-structure guidance for sectors, beacons, and pacing.'
---

# Level Designer

Use this staged skill when the project starts formalizing sector flow, beacon pacing, encounter distribution, or layout-driven progression.

## Intended SpaceshipGame use

- shape sector/map progression,
- review beacon pacing and event density,
- support encounter distribution without drifting into unsupported combat systems.

## Files it may touch

- `mechanika/01-game-flow.md`,
- `mechanika/02-screens-and-scenes.md`,
- `mechanika/07-events.md`,
- future map or beacon data docs.

## Source

- recommendation source: `SKILLS_RECOMMENDATIONS.txt` (MCP Market skills shortlist),
- adapted into a repo-staged skill instead of treated as an active engine-specific package.

## Current gate

- `Sprint 0 docs` for pacing notes,
- practical use expands after map/beacon systems are specified.

## Current blockers / open questions

- map progression rules are not finalized yet,
- reserved beacon types such as `combat` and `quest` are still blocked by `mechanika/`.

## Adaptation notes

- focus on pacing, structure, and readability,
- keep combat and quest-chain details out until approved,
- prefer simple sector-flow language over premature numeric balancing.
