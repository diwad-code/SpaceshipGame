# Game Design Document

## Status model

- **Approved now** — safe to use before the final mechanika pass.
- **Reserved** — known placeholder that must not be fully implemented yet.
- **Open question** — needs user decision or later spec work.

## Product frame

- Brief source: `docs/GAME_BRIEF.md`
- Narrative source: `docs/FABULA.md`
- Mechanics source: `mechanika/`

## Core player loop

- **Approved now:** manage ship state, review crew, travel, resolve events, track mission progress.
- **Reserved:** advanced combat, progression, and quest-chain loops.

## Content tracks

### Narrative and worldbuilding

- **Approved now:** create and maintain the story baseline in `docs/FABULA.md`.
- **Open question:** which story beats should be mandatory in MVP events.

### Mechanics and balance

- **Reserved:** final formulas and balance values until `mechanika/` is filled.

### UI and scene planning

- **Approved now:** document scene order, overlays, and mobile-first priorities.

## Crew and content placeholders

- **Approved now:** crew roles, skills fields, morale fields, and event hooks may be described at a high level.
- **Reserved:** trait effects, XP curves, faction behaviors, and quest logic.

## Documentation workflow

1. Stabilize `docs/GAME_BRIEF.md`.
2. Build or revise `docs/FABULA.md`.
3. Keep `docs/GDD.md` aligned with the brief, fabula, and scope.
4. Move final gameplay rules into `mechanika/` as they are approved.

## Open questions

- What is the first narrative revelation the player should encounter?
- Which event themes must exist before the first playable prototype?
- Which crew relationships are canon versus left systemic/open?
