---
name: webapp-testing
description: 'Stages browser and PWA validation guidance for the future Phaser/Vite app shell.'
---

# Webapp Testing

Use this staged skill when SpaceshipGame has a runnable browser app and needs repeatable smoke, UI, or PWA checks.

## Intended SpaceshipGame use

- validate Phaser scene boot flow in the browser,
- review mobile viewport behavior and installability,
- support future Playwright-based smoke tests and regression checks.

## Files it may touch

- `package.json`,
- Playwright or Vitest test files,
- `.github/workflows/` when browser validation enters CI,
- `docs/` notes for QA or PWA checks.

## Source

- recommendation source: `SKILLS_RECOMMENDATIONS.txt` (`ComposioHQ/awesome-codex-skills` shortlist),
- adapted locally for a Phaser 4 + Vite + PWA workflow.

## Current gate

- `app scaffold` now,
- `test/PWA` once the project can actually boot in a browser.

## Current blockers / open questions

- no `package.json`,
- no `src/` tree,
- no runnable Phaser shell,
- no Playwright setup yet.

## Adaptation notes

- prefer validating existing repo commands instead of inventing a test stack,
- keep testing focused on browser-first and Android-PWA behavior,
- avoid assuming desktop-only UI patterns.
