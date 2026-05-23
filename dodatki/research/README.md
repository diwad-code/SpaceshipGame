# README — Jak używać promptów z GPT-5.5 dla Star Search

## Struktura zestawu

```
gpt-prompts/
├── README.md                    ← ten plik
├── 00-RESEARCH-KONTEKST.md      ← baza wiedzy naukowej (zawsze dołączaj)
├── 01-PROPOZYCJE-MECHANIK.md    ← KROK 1: propozycje mechanik
└── 02-IMPLEMENTACJA-W-REPO.md   ← KROK 2: wypełnianie plików mechanika/
```

---

## Kontekst projektu (co GPT musi wiedzieć)

**Stack**: Phaser 4 + TypeScript strict + Vite + Dexie.js + Zod + PWA  
**NIE**: Phaser 3, idb-keyval, localStorage, React, Redux  
**Repo**: folder `mechanika/` ma 12 pustych plików `.md` do uzupełnienia  
**Autorytety**: `.github/copilot-instructions.md` > `docs/ARCHITECTURE.md` > `docs/ADRs/`  
**`claude_tips/`**: TYLKO materiał referencyjny, NIE autorytet

---

## Workflow

### KROK 1 — Propozycje mechanik (nowy czat GPT)

1. Stwórz **Project** w ChatGPT: "Star Search Game Design"
2. Dodaj plik `00-RESEARCH-KONTEKST.md` jako plik wiedzy projektu
3. Wyślij zawartość `01-PROPOZYCJE-MECHANIK.md` jako pierwszą wiadomość
4. GPT zaproponuje warianty A–G (7 kategorii mechanik)
5. Wybierz warianty, poproś o modyfikacje, iteruj
6. Zatwierdź mechaniki → przejdź do Kroku 2

**Czas**: 30–60 minut, 1–2 iteracje

---

### KROK 2 — Implementacja w repo (ten sam czat!)

1. **W tym samym czacie** wyślij zawartość `02-IMPLEMENTACJA-W-REPO.md`
2. Odpowiedz na 6 pytań wstępnych (załoga, tryb, torpor, permadeath, sesja, kampania)
3. GPT będzie uzupełniał pliki jeden po jednym:
   ```
   mechanika/00-overview.md → zatwierdź → 01-game-flow.md → ...
   ```
4. Kopiuj każdą odpowiedź do odpowiedniego pliku w repo

**Kolejność plików** (ważna — późniejsze zależą od wcześniejszych):
```
00-overview.md
01-game-flow.md
02-screens-and-scenes.md
03-resources.md
04-crew.md
05-ship-systems.md
06-missions.md
07-events.md
08-progression.md
09-failure-and-game-over.md
10-balancing-notes.md
99-open-questions.md
```

**Czas**: 2–4h (12 plików, jeden po jednym)

---

## Po uzupełnieniu `mechanika/`

Odblokuje się implementacja systemów w Copilot:
```
/prompt-new-system CrewSystem     ← teraz może używać mechanika/04-crew.md
/prompt-new-system ResourceSystem ← teraz może używać mechanika/03-resources.md
/prompt-new-system EventSystem    ← teraz może używać mechanika/07-events.md
/prompt-new-event [tema]          ← teraz ma wzorzec z mechanika/07-events.md
```

Copilot miał zablokowane te implementacje hasłem `pending mechanika/` — po wypełnieniu odblokowane.

---

## Czerwone flagi (gdy GPT zbacza)

- ❌ Proponuje mechaniki walki, combat damage → `// TODO: pending mechanika/`
- ❌ Pisze XP/progression curves → scope creep, do `docs/IDEAS_LATER.md`
- ❌ Pisze Phaser 3 API (np. `this.physics.add`) → przypomij: **Phaser 4**
- ❌ Proponuje `idb-keyval` lub `localStorage` → **Dexie.js** jest wymagane
- ❌ Splątanie kwantowe jako mechanika komunikacji → to mit, brak FTL (no-comm theorem)
- ❌ Pola snake_case w JSON → camelCase (per Copilot instructions)
- ❌ Brak wartości liczbowych → wymagaj konkretnych danych z researchu
- ❌ Trait effects, faction logic → poza MVP

---

## Przykłady dobrych follow-up po KROKU 1

**Zatwierdzenie z modyfikacją:**
> "Kategoria C Wariant 2 OK, ale dla promieniowania użyj dokładnych limitów NASA: 470 mSv kobiety, 620 mSv mężczyźni (REID 3%). Reszta kategorii zatwierdzona."

**Pytanie o integrację:**
> "Jak third-quarter phenomenon (Kategoria C) wpływa na dice-check (Kategoria D)? Pokaż konkretny wzór modyfikatora."

**Uproszczenie:**
> "Kategoria E komunikacja — wariant 2 jest za skomplikowany. Chcę najprostszą wersję: opóźnienie sygnału jako liczba lat świetlnych wyświetlona graczowi, bez systemu bandwidth. Resztę do IDEAS_LATER.md."

---

## Tabela plików mechanika/ i ich zawartość (referencja)

| Plik | Co zawiera | Kluczowe dane z researchu |
|---|---|---|
| `00-overview.md` | Opis gry, klimat, inspiracje | SF 2099, izolacja, twarda nauka |
| `01-game-flow.md` | Pętla rozgrywki, autosave | Dexie.js save points |
| `02-screens-and-scenes.md` | Ekrany, tekst intro, ton | Phaser 4 scenes per SCOPE.md |
| `03-resources.md` | Zasoby, co przy 0 | ECLSS: O₂ 93%, H₂O 98% |
| `04-crew.md` | Role, parametry, morale | Mars-500, NASA Twin Study, GCR limits |
| `05-ship-systems.md` | ECLSS, reaktor, hull | 4 podsystemy, awarie kaskadowe |
| `06-missions.md` | Typy misji na planecie | COSPAR protokoły, biosygnatury |
| `07-events.md` | 15 eventów MVP | GCR, pył, konflikty, biosygnatury |
| `08-progression.md` | Postęp misji, skala życia | Skala 0–6 (mikroby→inteligencja) |
| `09-failure-and-game-over.md` | Warunki przegranej | ECLSS failure modes |
| `10-balancing-notes.md` | Wartości startowe | Konkretne dane NASA |
| `99-open-questions.md` | Otwarte pytania | Do rozstrzygnięcia iteracyjnie |
