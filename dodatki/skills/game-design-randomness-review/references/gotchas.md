# Gotchas — Common Mistakes When Evaluating Randomness

These are failure modes to watch for in your analysis. Avoid them.

## Treating all randomness as bad
Randomness serves real design purposes — variety, balance, rewards, and information management. The question is never "should this game have randomness?" but "is the randomness well-placed and well-controlled?"

## Ignoring the input/output distinction
Saying "this game has too much RNG" without specifying whether it's input or output randomness is vague and unhelpful. The two types create fundamentally different player experiences and require different fixes.

## Assuming output randomness is always wrong
Output randomness is a valid design tool. It simulates imprecision in abstract systems (a soldier missing a shot), forces contingency planning, and creates tension. The problem isn't output randomness itself — it's output randomness without transparency, guardrails, or player recourse.

## Overlooking restart-scumming incentives
If input randomness heavily determines success (like finding a jetpack in Spelunky's first crate), players will restart repeatedly until they get favorable RNG. This turns a roguelike into a slot machine. Check whether the design inadvertently rewards this behavior.

## Forgetting controlled variance
Pure randomness creates streaks that feel broken. If a design uses randomness without any shaping (bag systems, pity timers, weighted distributions, deck splitting), that's usually the highest-leverage fix. Point to specific techniques rather than just saying "make it less random."

## Confusing legibility with simplicity
Making randomness legible doesn't mean dumbing it down. Cards, dice, and displayed percentages help players understand probability without reducing strategic depth. Suggest mechanisms that make odds intuitive, not mechanisms that remove decision-making.

## Evaluating from the designer's math, not the player's feel
A 95% hit chance that misses feels terrible even though it's statistically expected. Fire Emblem and Civilization both secretly adjust odds because the mathematically correct outcome and the emotionally correct outcome aren't the same. Evaluate how randomness *feels* to play, not just whether the numbers are fair on paper.

## Suggesting "remove the randomness" as a fix
Removing randomness entirely often makes games worse — perfectly deterministic games can become solvable puzzles or pure execution tests. The fix is usually better-placed, better-controlled randomness, not less of it.
