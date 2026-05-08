---
description: 'Mobile-first UX rules for Android phones, tablets, and PWA layout.'
applyTo: 'src/ui/**, src/scenes/**, public/**'
---

# Mobile UX instructions

- Use Android-style adaptive width classes:
  - Compact: `< 600dp`
  - Medium: `600-840dp`
  - Expanded: `840dp+`
- UI controls must have at least 48x48dp touch targets.
- Phone portrait: one main view plus bottom sheet/overlay panels.
- Phone landscape: slide-in side panel instead of large bottom sheet.
- Tablet: persistent side panel or two-column management layout.
- Avoid hover-only interactions.
- Keep critical UI inside safe areas.
- Canvas/game world may bleed visually, but controls must remain accessible.
- Use `touch-action` deliberately: game canvas can disable browser gestures only if in-game alternatives exist.
