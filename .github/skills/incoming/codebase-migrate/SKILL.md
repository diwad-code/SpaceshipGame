---
name: codebase-migrate
description: 'Stages larger repository refactors and structural migrations once SpaceshipGame has a real app tree.'
---

# Codebase Migrate

Use this staged skill for future bulk refactors, folder moves, API migrations, or architecture-aligned restructuring.

## Intended SpaceshipGame use

- help move files safely as `src/`, tests, and data assets grow,
- support future refactors after mechanic specs harden,
- keep documentation and architecture notes synchronized during structural changes.

## Files it may touch

- `src/`,
- `.github/` workflow or prompt files,
- tests,
- architecture and migration docs.

## Source

- recommendation source: `SKILLS_RECOMMENDATIONS.txt` (`ComposioHQ/awesome-codex-skills` shortlist),
- adapted locally instead of imported wholesale.

## Current gate

- `app scaffold`.

## Current blockers / open questions

- no production code tree yet,
- no migration pressure yet,
- real value starts after the first playable loop exists.

## Adaptation notes

- preserve serializable save-state assumptions,
- avoid mixing migration work with speculative mechanics changes,
- keep docs and README updated during every future migration.
