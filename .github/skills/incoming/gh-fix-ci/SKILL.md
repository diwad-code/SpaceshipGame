---
name: gh-fix-ci
description: 'Stages future GitHub Actions failure diagnosis and repair workflow for SpaceshipGame.'
---

# GH Fix CI

Use this staged skill when GitHub Actions exist and the repository needs targeted diagnosis of failed workflows.

## Intended SpaceshipGame use

- inspect failing build, lint, or test jobs,
- triage workflow regressions,
- keep CI fixes small and aligned with the repo architecture.

## Files it may touch

- `.github/workflows/`,
- test or config files directly causing CI failure,
- docs that describe required validation commands.

## Source

- recommendation source: `SKILLS_RECOMMENDATIONS.txt` (`ComposioHQ/awesome-codex-skills` shortlist),
- adapted locally for GitHub-first diagnostics rather than copied as-is.

## Current gate

- `CI`.

## Current blockers / open questions

- no GitHub Actions workflows yet,
- no build/test pipeline yet,
- current repo state is Sprint 0 docs-only.

## Adaptation notes

- always inspect actual workflow logs before editing,
- never guess the failure root cause from memory alone,
- avoid adding CI complexity before the app exists.
