# Skill intake / upload area

Use this directory as the staging area for additional skills before they become active repository skills.

## What goes here

- draft skills copied in for review,
- selected skills copied or adapted from `dodatki/skills/`,
- external skill references,
- partially adapted skill packages,
- notes about source, purpose, and gate.

## Currently staged recommended skills

- `changelog-generator` — release and milestone summaries (`CI/release` gate)
- `webapp-testing` — browser/PWA validation support (`app scaffold` gate)
- `gh-fix-ci` — GitHub Actions diagnostics (`CI` gate)
- `codebase-migrate` — larger refactors after the app exists (`app scaffold` gate)
- `game-designer` — design framing without blocked mechanics (`Sprint 0 docs` gate)
- `gameplay-programmer` — implementation support after `mechanika/` and app scaffold (`app scaffold` gate)
- `level-designer` — sector/beacon pacing support (`Sprint 0 docs` gate)
- `game-artist` — later visual direction support (`design pipeline` gate)

## Required note for each incoming skill

Include at least:

- original source,
- intended use in SpaceshipGame,
- current gate (`Sprint 0 docs`, `app scaffold`, `CI`, `design pipeline`, or `external tool`),
- blockers or open questions.

## Promotion rule

A skill moves from `incoming/` to an active folder in `.github/skills/` only after it is adapted to repository conventions and documented in the workflow docs.
