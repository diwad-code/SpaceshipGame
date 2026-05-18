# Expanded skills and MCP adoption research

Analysis date: 2026-05-18
Mode: comprehensive good-plus set, not a minimum shortlist.

This folder extends the root `SKILLS_RECOMMENDATIONS.txt` with broader internet, marketplace, GitHub, and MCP-directory research. It is intentionally selective: the goal is a stronger adoption stack for `SpaceshipGame`, not a dump of every attractive tool.

## Repository fit filters

Keep candidates only when they support at least one of these needs:

- Phaser 4 / browser-first / PWA development.
- Mechanics, narrative, event, mission, or game-design documentation without inventing unapproved `mechanika/` rules.
- Data-driven TypeScript architecture, Zod schemas, save migration, or Vitest/Playwright validation.
- Mobile-first UI overlays, HUD, accessibility, responsive layout, and design handoff.
- Agent workflow quality: skill creation, documentation generation, context grounding, review, CI diagnosis, and safe autonomous execution.

Reject or defer candidates when they are primarily Unity, Unreal, Godot, Bevy, Minecraft server, native mobile, game-store automation, or unrelated SaaS automation unless the project later adopts that tool explicitly.

## Additional sources checked

### MCP directories and marketplaces

- MCP Market: `https://mcpmarket.com/`
- MCP Market game-development skills: `https://mcpmarket.com/tools/skills/categories/game-development`
- MCP Market game-development MCPs: `https://mcpmarket.com/categories/game-development`
- Smithery: `https://smithery.ai/`
- PulseMCP: `https://pulsemcp.com/`
- Glama MCP directory: `https://glama.ai/mcp/servers`
- LobeHub MCP directory: `https://lobehub.com/mcp`
- Playbooks MCP directory: `https://playbooks.com/mcp`
- Awesome MCP servers: `https://github.com/punkpeye/awesome-mcp-servers`
- GitHub MCP/server topic searches.

### Agent skill and prompt marketplaces

- ComposioHQ `awesome-codex-skills`: `https://github.com/ComposioHQ/awesome-codex-skills`
- ComposioHQ `awesome-claude-skills`: `https://github.com/ComposioHQ/awesome-claude-skills`
- sickn33 `antigravity-awesome-skills`: `https://github.com/sickn33/antigravity-awesome-skills`
- VoltAgent `awesome-agent-skills`: `https://github.com/VoltAgent/awesome-agent-skills`
- bergside `awesome-design-skills`: `https://github.com/bergside/awesome-design-skills`
- alirezarezvani `claude-skills`: `https://github.com/alirezarezvani/claude-skills`
- Skills marketplace / SkillsMP: `https://skillsmp.com/`
- Agent Skill Market: `https://skillmarketplace.ai/`
- Claude marketplace directories: `https://claudemarketplaces.com/`
- Prompt libraries for reference only: PromptDen, Snack Prompt, AIPRM, PromptBase.

## New high-value additions

These are additions to the previous target set, grouped by adoption value.

### A. Core MCPs for an autonomous coding workflow

1. **GitHub MCP Server**
   - Use for issue/PR context, CI logs, commit/status inspection, and release workflow support.
   - Adopt when GitHub workflow automation becomes a recurring project need.

2. **Filesystem MCP Server**
   - Use for structured local file operations where the chosen agent environment requires explicit filesystem access.
   - Adopt only with a scoped repository root and no access to secrets.

3. **Context7 MCP / documentation-context MCP**
   - Use to ground Phaser, Vite, Workbox, Dexie, Zod, Vitest, and Playwright work in current docs.
   - Very useful before dependency or API-heavy implementation tasks.

4. **Sequential Thinking MCP**
   - Use for complex multi-phase architecture, migration, and adoption decisions.
   - Helpful for avoiding shallow one-step plans when the task has many gates.

5. **Memory MCP**
   - Use for durable, project-local adoption context only if memory scope and retention are explicit.
   - Do not store secrets, private data, or unstable task details.

6. **Brave Search MCP / web-search MCP**
   - Use for live marketplace, package, and vulnerability research.
   - Adopt only if the agent environment has clear API-key handling.

### B. Browser, PWA, and QA MCPs

1. **Microsoft Playwright MCP**
   - Highest-value browser automation MCP for the future Phaser/PWA app.
   - Use for E2E smoke checks, PWA installability review, screenshots, accessibility snapshots, and mobile viewport testing.

2. **Browserbase MCP / hosted browser automation**
   - Good later option if local Playwright is not enough or shared cloud browser sessions are needed.
   - Defer until there is a real app shell and a reason to use hosted automation.

3. **web-eval-agent / autonomous web evaluation MCPs**
   - Useful later for autonomous UI review and regression notes.
   - Defer until there are stable scenes and overlays to evaluate.

4. **PWA Kit MCP Server**
   - Not game-specific, but useful later as a delivery/PWA-quality support tool.
   - Defer until Vite + PWA scaffolding exists.

### C. Phaser and game-production MCPs

1. **Phaser Editor MCP Server**
   - Strongest direct engine/editor MCP found.
   - Use if Phaser Editor v5 becomes part of the workflow for scenes, assets, training levels, or visual layout.

2. **Phaser MCP / Phaser by phaserjs**
   - Keep as a primary Phaser-specific candidate for scene, asset, and game-loop assistance.
   - Verify exact package, publisher, and compatibility before installing.

3. **Figma Dev Mode MCP Server**
   - Strong for HUD, overlay, mobile layout, safe-area, and design-token handoff.
   - Useful before UI implementation becomes heavy.

4. **Blender MCP Server**
   - Secondary art-pipeline support for mockups, pre-rendered assets, or promo visuals.
   - Defer until the project has an art workflow.

### D. Documentation, design, and skill-source additions

1. **antigravity-awesome-skills**
   - Large cross-agent skill library worth mining for documentation, testing, planning, and review skills.
   - Use as a source catalog, not as a bulk import.

2. **awesome-agent-skills / awesome-claude-skills**
   - Useful for finding cross-agent SKILL.md conventions and mature reusable patterns.
   - Compare against existing local prompts before adopting.

3. **awesome-design-skills**
   - Strong additional source for UI/design-system skills.
   - Relevant to mobile-first overlays and future Figma/design-token workflow.

4. **agent-skill-creator**
   - More implementation-oriented complement to `skill-creator`.
   - Consider when converting this research into actual `.github/skills/*` packages.

5. **spec-driven-development skills**
   - Useful if later work needs disciplined requirements-to-implementation flow.
   - Keep as a second-wave option because current BMad-derived docs already cover part of this need.

6. **session-handover / context-engineering skills**
   - Useful for long-running game development with many agent sessions.
   - Adopt only if the team wants formal handoff docs beyond current README/docs updates.

7. **design-token extraction tools such as design-extract or dembrandt**
   - Useful later if the project has a web visual identity or Figma/site references to convert into tokens.
   - Defer until UI art direction exists.

## Updated final good-plus target set

### Adopt or build early

- Existing `scaffold-scene` skill.
- Existing `scaffold-system` skill.
- BMad-adapted `game-brief` package.
- BMad-adapted `gdd` package.
- BMad-adapted `mechanika-spec` skill.
- BMad-adapted `architecture` package.
- `skill-creator` / `agent-skill-creator` pattern.
- `content-research-writer` or equivalent documentation authoring skill.
- `Context7 MCP` or another docs-grounding MCP.
- `Sequential Thinking MCP` for multi-phase adoption decisions.

### Adopt when app scaffolding starts

- `Phaser Editor MCP Server` if Phaser Editor v5 is used.
- `Phaser MCP / Phaser by phaserjs` after package/publisher verification.
- `Figma Dev Mode MCP Server` for UI overlays and mobile layouts.
- `Microsoft Playwright MCP` once the PWA app can run.
- `webapp-testing` skill.

### Adopt when workflows mature

- `GitHub MCP Server` for PR/issue/CI automation.
- `gh-fix-ci` skill after GitHub Actions exist.
- `changelog-generator` for milestone/release summaries.
- `codebase-migrate` for larger refactors.
- `Memory MCP` only with explicit retention and privacy rules.
- `Brave Search MCP` or equivalent live-search MCP if API-key handling is approved.

### Keep in second-wave/watchlist

- `Blender MCP Server` for art/promo/mockup pipeline.
- `Browserbase MCP` for hosted browser sessions.
- `web-eval-agent` for autonomous UI quality review.
- `PWA Kit MCP Server` for delivery checks.
- `awesome-design-skills` candidates for future UI/design-system work.
- PromptDen / Snack Prompt / AIPRM / PromptBase as inspiration sources only.

### Continue rejecting for now

- Unity-first, Unreal-first, Godot-first, Bevy-first, Minecraft plugin, native console, or engine-migration skills.
- Dungeon Fighter Online automation, Epic Games automation, or unrelated platform automation.
- SaaS-heavy workflow skills unless the project actually adopts that external process.
- Any MCP that requires broad filesystem, browser, GitHub, or web-search permissions without a clear security boundary.

## Autonomous adoption order

1. **Read state**: inspect README, docs, `mechanika/`, `.github/prompts/`, `.github/skills/`, package/app presence, and existing workflows.
2. **Classify gates**:
   - Sprint 0 docs-only gate.
   - App scaffold gate.
   - Test/PWA gate.
   - CI/release gate.
   - Art/design pipeline gate.
3. **Execute unblocked docs/design work first**:
   - create or update game brief prompt/docs,
   - create or update GDD prompt/docs,
   - create or update mechanika-spec skill,
   - create or update architecture/investigate prompts,
   - keep README/docs indexes current.
4. **Prepare skills before MCP installs**:
   - create local skills from selected patterns,
   - document source, purpose, acceptance criteria, and activation gate,
   - avoid bulk imports.
5. **Only then configure MCPs**:
   - add MCP configuration only when the relevant workflow exists,
   - prefer repo-scoped and least-privilege settings,
   - never commit secrets or personal tokens.
6. **Validate after every phase**:
   - run available repo tests/build/lint,
   - for docs-only changes run formatting/diff checks,
   - run review/security validation before completion.
7. **Stop and report blockers**:
   - missing app scaffold,
   - missing CI workflows,
   - missing approved mechanics,
   - unknown package publisher/security posture,
   - required credentials or external service setup.
