---
name: changelog-generator
description: 'Stages release and milestone changelog work for SpaceshipGame without inventing unsupported delivery steps.'
---

# Changelog Generator

Use this staged skill when the repository needs structured milestone summaries, release notes, or visible progress updates.

## Intended SpaceshipGame use

- summarize shipped documentation, feature, or workflow milestones,
- draft `CHANGELOG.md` or release-note sections,
- help keep README progress notes readable once the project starts moving beyond Sprint 0.

## Files it may touch

- `CHANGELOG.md`,
- `README.md`,
- release summary docs under `docs/`,
- PR or milestone notes when that workflow exists.

## Source

- recommendation source: `SKILLS_RECOMMENDATIONS.txt` (`ComposioHQ/awesome-codex-skills` shortlist),
- adapted locally for SpaceshipGame instead of copied verbatim.

## Current gate

- `CI/release` for routine use,
- can be promoted earlier only if the repo adopts a durable changelog workflow.

## Current blockers / open questions

- no release workflow yet,
- no `CHANGELOG.md` yet,
- no app milestone cadence yet.

## Adaptation notes

- keep output concise and beginner-friendly,
- summarize only repo reality; do not invent shipped features,
- if milestones are still vague, write open questions instead of fake release notes.
