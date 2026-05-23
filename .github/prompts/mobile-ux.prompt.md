---
name: mobile-ux
description: 'Review mobile/tablet UX against Android adaptive layout and touch requirements.'
agent: ask
model: gpt-5.4
tools:
  - search/codebase
  - read/problems
---

# /mobile-ux

Review the current UI for mobile and tablet usability.

Check:

- Compact, medium, and expanded width handling.
- 48x48dp touch targets.
- Safe-area handling.
- Pixel-art scaling.
- No hover-only controls.
- Phone bottom-sheet/overlay behavior.
- Tablet side-panel behavior.
- Accessibility of critical UI text.

Return only high-impact recommendations.
