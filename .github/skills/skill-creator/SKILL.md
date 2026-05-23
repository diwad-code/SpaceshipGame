---
name: skill-creator
description: 'Creates or adapts local repository skills using the SpaceshipGame conventions and activation gates.'
---

# Skill Creator

Use this skill when adding a new package under `.github/skills/`.

Checklist:

- Confirm the skill supports the approved stack, docs workflow, narrative work, or future gated workflows.
- Write a short `name` and `description` in frontmatter.
- Explain when to use the skill and what files it may touch.
- Record any gate such as Sprint 0 docs-only, app scaffold required, CI required, or external tool required.
- If the skill comes from an external pattern, adapt it instead of bulk-copying it.
- If the skill is not ready for active use, stage it under `.github/skills/incoming/` first.

Do not:

- commit secrets or personal tokens,
- assume external MCP configuration already exists,
- invent blocked game mechanics.
