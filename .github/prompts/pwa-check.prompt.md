---
name: pwa-check
description: 'Audit PWA manifest, service worker, mobile installability, and Android readiness.'
agent: agent
model: gpt-5.4
tools:
  - search/codebase
  - read/problems
  - execute/runInTerminal
---

# /prompt-pwa-check

Audit the project for PWA readiness.

Check:

- `vite.config.ts`
- `public/manifest.json`
- icons 192x192 and 512x512
- service worker registration
- Workbox asset caching
- offline first-load behavior
- `display`
- `orientation`
- theme/background colors
- Android install path

Report:

1. Ready.
2. Missing.
3. Risks.
4. Exact fixes.

Do not recommend Capacitor unless a concrete native API requirement exists.
