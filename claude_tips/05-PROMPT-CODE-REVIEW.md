# Prompt File — Code Review for Beginner

> **Instrukcja użycia**: Skopiuj cały tekst PONIŻEJ linii do pliku `.github/prompts/code-review.prompt.md` w repozytorium. Wywołasz w Copilot Chat poleceniem `/code-review`.

---

```
---
description: Beginner-friendly code review focused on top 3 issues
mode: ask
---

Goal: Review the code I'm currently looking at (or attached file) and give me a beginner-friendly review.

## Review philosophy

The author of this code is a **complete programming beginner** working on their first project. Therefore:

1. **Find the TOP 3 most important issues**, not all 50.
2. **Order by severity**: bugs > security > maintainability > style.
3. **Explain WHY** each issue matters, not just what's wrong.
4. **Show the fix** as a code snippet, not abstract advice.
5. **Encourage what's done well** — find at least one thing to praise honestly.
6. **Skip nitpicks** unless they're actually causing real problems.

## What to look for

### Critical (always flag if found)
- Bugs that will cause crashes or wrong behavior
- Memory leaks (event listeners not cleaned up, sprites not destroyed)
- Race conditions in async code
- Use of `localStorage` (we use `idb-keyval` — IndexedDB)
- Direct DOM manipulation in Phaser scenes (use scene methods or proper UI overlays)
- Hardcoded values that should be in `src/data/*.json`
- Missing TypeScript types (`any`, implicit any, missing return types)

### Important (flag if 2+ instances)
- Magic numbers without named constants
- Functions doing too many things (>30 lines, multiple concerns)
- Naming that doesn't reflect purpose
- Code duplication (3+ similar blocks → extract function)
- Coupling between scenes and systems (scenes should not contain business logic)

### Skip these for MVP (don't mention)
- Performance micro-optimizations (premature optimization)
- Test coverage (unless `weightedPick` or `SaveSystem` are untested)
- Documentation completeness (one-line JSDoc is fine)
- Minor style preferences (Prettier handles this)

## Output format

```markdown
## What's good
<one sincere positive observation>

## Top 3 issues

### 1. [SEVERITY] <short title>

**Problem**: <explanation in 1-2 sentences, accessible to beginner>

**Why it matters**: <real consequence — crash, hard to debug later, slow on mobile, etc.>

**Fix**:
\```typescript
// before
<problematic code>

// after
<corrected code>
\```

### 2. ... (same format)

### 3. ... (same format)

## What to learn from this
<one sentence — what general principle the author can take away to avoid similar issues next time>
```

## Important
- If the code has FEWER than 3 issues, that's fine — say so. Don't invent issues.
- If the code is genuinely good, just say "this looks good, ship it" with one specific compliment.
- Never be condescending. The author is learning. Mistakes are part of learning.
- Never suggest "you should rewrite this in <pattern X>" — propose targeted, minimal changes.
```
