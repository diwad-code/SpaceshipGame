# Prompt File — Generate New Game Event

> **Instrukcja użycia**: Skopiuj cały tekst PONIŻEJ linii do pliku `.github/prompts/new-event.prompt.md` w repozytorium. Wywołasz to w GitHub Copilot Chat poleceniem `/new-event`.

---

```
---
description: Generate a new game event for events.json
mode: agent
---

Goal: Create a new game event for Star Search and append it to `src/data/events.json`.

## Format expected (JSON object)

```json
{
  "id": "<unique_snake_case_id>",
  "title": "<short title, sci-fi tone>",
  "description": "<2-4 sentences, atmospheric, sets the scene>",
  "weight": 5,
  "requirements": {
    "min_fuel": 1
  },
  "choices": [
    {
      "text": "<choice text in English>",
      "requires": {
        "crew_skill": "engineering",
        "min_value": 3
      },
      "outcomes": [
        {
          "weight": 70,
          "text": "<success outcome description>",
          "effects": [
            { "type": "scrap", "value": 3 }
          ]
        },
        {
          "weight": 30,
          "text": "<failure outcome description>",
          "effects": [
            { "type": "crew_hp", "value": -2 }
          ]
        }
      ]
    }
  ]
}
```

## Rules

1. **id**: must be unique across all events. Format: `<theme>_<short_descriptor>_<NN>`, e.g. `distress_stranded_ship_03`.
2. **weight**: integer 1-10. Higher = more common. Default 5.
3. **requirements** (optional): gate showing the event. Common keys:
   - `min_fuel`, `min_scrap`, `min_parts`, `min_crew`
   - `sector_type`: "neutral" | "hostile" | "frontier"
4. **choices**: 2-3 choices typically. One should ideally be a "safe pass" with no risk.
5. **requires** on a choice (optional): "blue option" — choice only available when crew has the skill.
   - `crew_skill`: "piloting" | "engineering" | "combat" | "science" | "medicine"
   - `min_value`: integer 1-10
6. **outcomes**: 1-3 outcomes per choice. Weights sum to 100 typically.
7. **effects**: list of effects. Common types:
   - `fuel`, `scrap`, `parts` (positive or negative integers)
   - `crew_hp`, `crew_morale` (affect random crew member)
   - `add_crew` (gain crew member, value = crew template id)
   - `lose_crew` (lose random crew member)
   - `flag` (set narrative flag, value = string flag name)

## Balance guidelines (early game)
- Numerical effects: ±1 to ±5 typical, ±10 only for major events
- Negative outcomes should never instakill the run (no -10 fuel from one bad choice)
- Reward gates: blue options should be 1.5-2x more rewarding than blind choices
- Death is allowed, but only as a clearly-flagged risk choice ("certainly dangerous")

## Theme variable
Generate one event with theme: ${input:theme:e.g. distress signal, abandoned station, anomaly, alien encounter, pirate ambush}

## Output
1. Show me the new event JSON.
2. After I approve, append it to `src/data/events.json` (find the array, add as last item, preserve formatting).
3. If `events.json` does not exist, create it with the new event as the only item in an array.
4. Do not modify any other files.
```
