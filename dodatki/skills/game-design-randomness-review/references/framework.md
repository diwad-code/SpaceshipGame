# Randomness Framework — Reference

This is the core framework for evaluating randomness in game design. These ideas come from Mark Brown (Game Maker's Toolkit), the Ludology podcast, and designers behind Civilization, XCOM, Slay the Spire, and others.

## The Core Insight

Randomness in games serves four purposes: **variety**, **balance**, **exciting rewards**, and **limiting the information horizon**. The critical design question is not whether to use randomness, but *when* in the decision loop it fires — before or after the player commits to a choice.

## Two Types of Randomness

### Input Randomness (Pre-Luck)

Random events that happen *before* the player decides. The player sees the situation, then plans around it.

**Examples**: procedural level generation (Minecraft), drawing cards (Slay the Spire), rolling dice before placement (Castles of Burgundy), random starting conditions (Spelunky).

**Design effect**: Supports strategic play. The player can read the board and make informed choices. Frustration is lower because failure feels like a planning mistake, not bad luck.

### Output Randomness (Post-Luck)

Random events that happen *after* the player decides. The player commits to a plan, then luck determines the outcome.

**Examples**: hit chances in XCOM, loot drops in Borderlands, random enemy encounters, loot box contents.

**Design effect**: Can feel unfair — your plan fails due to luck, not bad strategy. But it has valid uses: simulating imprecision in abstract combat, forcing risk management and contingency planning, and creating exciting moments of tension.

## Five Evaluation Dimensions

### 1. Timing in the Decision Loop

Where does the randomness fire relative to the player's choice? Input randomness creates puzzles to solve; output randomness creates gambles to take. Neither is inherently better, but the designer should be deliberate about which experience they're creating.

**Key question**: Does the player see the random state before or after they commit to a decision?

### 2. Controlled Variance

Well-designed randomness isn't purely random — it's shaped to prevent extreme outcomes. Pandemic splits epidemic cards evenly across the deck so they can't all cluster. Tetris delivers all 7 block types before repeating any. Diablo 3's smart loot biases drops toward the player's class.

**Key question**: Are there guardrails preventing frustrating streaks or degenerate outcomes?

### 3. Information Flow

Games benefit from alternating between calm stretches (where the player plans) and disruptive spikes of new information. XCOM's enemy pod activation is a high-impact information spike that forces rapid replanning. The rhythm between predictability and disruption keeps players engaged.

**Key question**: Does randomness create a healthy rhythm of planning and adaptation, or is it constant noise?

### 4. Transparency and Legibility

Players make better decisions and feel less cheated when they understand the odds. Showing hit percentages, using familiar mechanisms like dice and cards, and making probability intuitive all help. Cards are naturally legible — a smaller deck means higher draw chances, and cards leave the pool once drawn (dependent probability), creating synergy opportunities.

**Key question**: Can the player understand the probability space well enough to make meaningful risk decisions?

### 5. Directional Fairness

Randomness that only favors the player feels generous rather than unfair. Into the Breach gives buildings a small random chance to block incoming damage, but never a chance to take extra damage. When output randomness exists, biasing it toward the player preserves agency while adding positive surprise.

**Key question**: When randomness swings, does it swing toward the player or against them?

## Techniques for Better Randomness

- **Fudge the numbers** — Fire Emblem secretly boosts displayed hit chances. Civilization guarantees a win after two consecutive losses at 33%. Hearthstone uses pity timers for rare card packs. The player doesn't need to know the true odds if the felt experience is fair.
- **Discourage degenerate play** — Slay the Spire gives bonus starting items only if you reached the first boss last run, discouraging restart-scumming for favorable RNG.
- **Shift output to input** — Into the Breach (from the makers of FTL) moved from output randomness (will my attack hit?) to input randomness (enemies telegraph attacks, you plan around them). This was a direct design response to FTL's frustrations.
- **Use dependent probability** — Cards drawn from a deck create dependent probability (drawing one card changes the odds of drawing others), enabling synergies and deck-building strategies. Dice are independent — each roll is isolated. Choose the mechanism that fits your design goals.
