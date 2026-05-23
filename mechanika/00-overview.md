# 00 — Overview
## Podsumowanie Gry | Wersja 1.0

> Punkt wejścia dla osoby która otwiera to repo po raz pierwszy.
> Każda sekcja odsyła do pliku z pełnym detalem.
> Ten plik nie zastępuje innych plików mechaniki — jest ich mapą.
> Ostatnia aktualizacja: 2026-05

---

## 1. OPIS GRY

**Star Search / SpaceshipGame** to retro pixel-art space management RPG.

Rok 2099. Siedmioosobowa załoga statku *Kairos* leci w kierunku planety
Kepler-442c — jedynego miejsca poza Ziemią gdzie wykryto potencjalne
biosygnatury chemiczne. Podróż trwa 58 lat. Torpor rotacyjny trzyma
załogę przy życiu. Kosmos starzeje ich powoli.

Gracz wciela się w **Commander Jakuba Nowaka** — naukowca który wywalczył
tę misję przez dekadę i zgłosił się jako dowódca bo nie potrafił
jej nikomu oddać. Zarządza statkiem, zasobami i sześciorgiem ludzi
którym jest winien powrót do domu.

Są dwa cele misji:
- *Oficjalny:* wykryć, skatalogować i opisać życie pozaziemskie.
- *Nieoficjalny każdego na pokładzie:* wrócić do domu.

Napięcie między tymi dwoma celami jest sercem tej gry.

---

## 2. TON I KLIMAT

Nie horror. Nie action sci-fi. Nie space opera.

**Bliżej:** Stanisław Lem (*Solaris*), Ursula Le Guin (*The Dispossessed*),
Kim Stanley Robinson (*Aurora*).

Kosmiczna izolacja jest tu warunkiem egzystencjalnym który uwypukla
to co ludzkie — nie zagrożeniem z zewnątrz. Daleko od Ziemi ludzie
stają się dokładnie tacy jacy są. Bez maski. Bez ucieczki.

**Gra wywołuje:**
- Ciekawość poznawczą — co tam jest?
- Ciężar odpowiedzialności — oni są pod twoją opieką
- Intymność — siedmioro ludzi, jedno pudełko, pół wieku
- Euforię odkrycia i długi cień wątpliwości

**Estetyka:** retro-pixel terminal. Interfejs *Kairos* wygląda jak
terminal lat 80. z 2099 roku. Minimalizm formy, maksymalizm znaczenia.

---

## 3. INSPIRACJE

| Inspiracja | Co bierzemy | Czego NIE bierzemy |
|---|---|---|
| **FTL: Faster Than Light** | Event system, blue options, resource management, permadeath | Real-time z pauzą, walka jako core loop |
| **Disco Elysium** | Inner voice skills, narracyjne wybory, arc postaci | Amnesja, detektywistyczna struktura |
| **This War of Mine** | Moralny ciężar decyzji przywódczych | Grafika 2D dark art, post-apo setting |
| **Oxygen Not Included** | ECLSS management, entropia systemów | Sandbox, brak narracji |
| **Kim Stanley Robinson — Aurora** | Twarda SF, izolacja, ludzki koszt odkrycia | Pokoleniowy statek (nasze jest torpor) |

---

## 4. GŁÓWNA PĘTLA GRY

*(Szczegóły: `mechanika/01-game-flow.md`)*

```
1 TURA = 1 cykl rotacyjny = 30 dni aktywnych + 90 dni torporu

FAZA 1: PRZEBUDZENIE  — ARIA raport, stan statku
FAZA 2: PRZYDZIAŁ     — gracz przydziela zadania aktywnej załodze
FAZA 3: ZDARZENIE     — 35-45% szans na event losowy lub FORCED
FAZA 4: ROZLICZENIE   — efekty, degradacja, progi alarmowe
FAZA 5: TORPOR        — zmiana aktywnej załogi, +90 dni

RAZEM: ~174 tury, 5 aktów, ~58 lat misji
```

**5 aktów:**
- Akt I (0–10%): odlot, tutorial ARII, budowanie świata
- Akt II (10–50%): długa ciemność, entropia narasta
- Akt III (50–75%): Trzeci Kwartał — najtrudniejszy punkt psychologicznie
- Akt IV (75–90%): przybycie do Limes, odkrycie, najwyższe stawki
- Akt V (90–100%): rozwiązanie, logbook, zakończenie

---

## 5. KAPITAN I GŁOSY WEWNĘTRZNE

*(Szczegóły: `docs/FABULA.md`, `mechanika/04-crew.md`, `mechanika/08-progression.md`)*

**Commander Jakub Nowak** (lat 44 przy starcie):
Naukowiec-astrobiolog który wywalczył misję przez 10 lat lobbowania.
Zgłosił się jako dowódca bo nie umiał jej nikomu oddać.
Poświęcił małżeństwo i relację z synem (Paweł, teraz 20 lat).

**Sześć głosów wewnętrznych** — mechanika w stylu Disco Elysium.
Każdy skill to perspektywa która przemawia w kluczowych momentach:

| Głos | Skill start | Charakter |
|---|---|---|
| DOWODZENIE | 5 | Autorytet. Obowiązek. Regulaminy WABK. |
| EMPATIA | 4 | Relacje. Ból. To co czują inni — nawet gdy nie mówią. |
| NAUKA | 7 | Ciekawość. Analiza. Sens misji. |
| PRZETRWANIE | 5 | Zimna arytmetyka. Zasoby. Ryzyko. |
| PAMIĘĆ | 6 | Ziemia. Paweł. To co zostawione. Rośnie z czasem. |
| SYGNAŁ | 3 | Intuicja. To czego dane nie tłumaczą. Rośnie przez wybory. |

Głosy rosną przez narracyjne wybory, nie przez grind.

---

## 6. ZAŁOGA

*(Szczegóły: `docs/FABULA.md`, `mechanika/04-crew.md`)*

| Postać | Rola | Trait | Prawda ukryta |
|---|---|---|---|
| **Mira Osei** | XO | *Zimna głowa* — w kryzysie DOWODZENIE +2 | Powinna dowodzić. Wie o tym. |
| **Grzech** | Inżynier | *Śląski sposób* — porażka INŻYNIERIA → częściowy sukces | Wypadek na Meridian. Nie opowiada. |
| **Dr Yuki Tanaka** | Astrobiolog | *Obsesja biosygnatur* — NAUKA +2 / Morale −20 po fałszywej | K2-18b żyje w jej głowie. |
| **Dr Amara Nwosu** | Medyk/Psycholog | *Widzę cię* — ujawnia prawdziwy stan psychologiczny | Prywatne logi których nie wysyła na Ziemię. |
| **Lena Kowalska** | Pilot | *Czyste lądowanie* — bez kaskady nawet przy porażce | Zostawiła kogoś na Ziemi. |
| **Felix Ramos** | AI Operator | *Język ARII* — ARIA efektywna +20% gdy aktywny | Granica między nim a ARIĄ się zaciera. |
| **ARIA** | AI statku | Tutorial, asystent, coś więcej | Zaczyna zadawać pytania których protokoły nie przewidują. |

**Śmierć postaci** jest możliwa i nieodwracalna.
Śmierć Yuki blokuje odkrycie życia.
Śmierć Amary blokuje regenerację Morale przez cały Akt IV.

---

## 7. SYSTEMY MECHANICZNE

*(Szczegóły: kolejne pliki `mechanika/`)*

### Skill Check
`skill (1–10) + modyfikatory stanu + d6 (1–6) ≥ difficulty (3/6/9/12/15)`

Wyniki: Pełny sukces / Sukces z komplikacją / Częściowy / Porażka / **Porażka kaskadowa**

Blue check (niebieska opcja): skill ≥ 8 AND morale ≥ 60 → bez kaskady.

### Parametry postaci (każda)
- **Health** 0–100: degradacja biologiczna, urazy
- **Morale** 0–100: izolacja, konflikty, straty
- **Fatigue** 0–100: reset w torpor
- **Radiation** 0–620 mSv: akumulacyjne, nieodwracalne

### Zasoby
- **TLEN** 80/100 start: ECLSS produkuje, aktywna załoga zużywa
- **WODA** 70/100 start: 98% recyrkulacja, kaskaduje na TLEN
- **ŻYWNOŚĆ** 60/100 start: hydroponika + bioreaktory
- **PALIWO** 100/100 start: manewry i powrót (min. 35 na powrót)
- **CZĘŚCI** 75/100 start: naprawy, brak produkcji, niedobór celowy

### ECLSS i systemy statku
13 systemów z własnym zdrowiem (0–100%).
Degradują pasywnie. Naprawia je Grzech (CZĘŚCI + INŻYNIERIA check).
Gracz nie może naprawić wszystkiego — priorytetyzacja jest mechaniką.

### Eventy
15 eventów MVP: 6 FORCED (gwarantowane), 9 WEIGHTED (warunkowe).
Szansa eventu: 35% (Akty I–II), 45% (Akt III), 40% (Akt IV).
Eventy mają głosy wewnętrzne, blue checki, system flag narracyjnych.

### Misje
14 typów: podróżne (zawsze), podejście Limes, orbitalne, powierzchniowe.
Misje wieloturowe (M12, M13) blokują postaci na 2 tury.
M14 (Analiza biologiczna) wyznacza poziom odkrycia (0–3 w MVP).

---

## 8. SZEŚĆ ZAKOŃCZEŃ

*(Szczegóły: `mechanika/09-failure-and-game-over.md`)*

| Zakończenie | Warunki | Charakter |
|---|---|---|
| **Triumf** | Odkrycie potwierdzone + załoga ≥5/7 + powrót | Pełny sukces. Wracasz z odpowiedzią. |
| **Pyrrusowe** | Odkrycie potwierdzone + straty 3–5 osób | Znalazłeś. Ale puste miejsca przy stole. |
| **Cichy powrót** | Brak odkrycia + wszyscy żyją | Misja nieudana technicznie — ale to też jest coś. |
| **Awaria** | Statek za uszkodzony na kontynuację | Wybrałeś ludzi ponad misję. |
| **Zostają** | PALIWO <15 przy Limes LUB aktywny wybór | Z konieczności albo z wyboru. Obie są prawdziwe. |
| **Cisza** | Comm = 0 przez 8+ tur, sygnał z Ziemi zamilkł | Lecisz do pytania. Nie do domu. |

Każde zakończenie: tekst logbooka kapitana lub ARII.
Żadne nie jest jednoznacznie dobre lub złe — każde jest konsekwencją.

**Twardy koniec gry (KG):** dekompresja, brak O₂, reaktor = 0, dryf, wszyscy martwi.
Permadeath: zapis usunięty, logbook zachowany.

---

## 9. MAPA PLIKÓW MECHANIKI

| Plik | Zawartość |
|---|---|
| `00-overview.md` | **Ten plik** — punkt wejścia |
| `01-game-flow.md` | Pętla gry, 5 faz tury, rotacja torporu, akty |
| `02-screens-and-scenes.md` | 14 scen Phaser 4, layouty, przepływ, overlaye |
| `03-resources.md` | TLEN/WODA/ŻYWNOŚĆ/PALIWO/CZĘŚCI + ECLSS systemy |
| `04-crew.md` | Profile 7 postaci, parametry, skill checki, relacje |
| `05-ship-systems.md` | Hull/Sensory/Lab/Comm/Medbay/Torpor/Warsztat |
| `06-missions.md` | 14 misji: podróżne, podejście, orbitalne, powierzchniowe |
| `07-events.md` | 15 eventów MVP z pełnymi opisami, głosami, efektami |
| `08-progression.md` | Głosy kapitana, skille załogi, relacje, skala odkrycia |
| `09-failure-and-game-over.md` | 5 KG, 6 zakończeń narracyjnych, logbooki, permadeath |
| `10-balancing-notes.md` | Wartości startowe, budżety, krzywa trudności, testy |
| `99-open-questions.md` | Wszystkie otwarte pytania z priorytetem |

---

## 10. MAPA POZOSTAŁYCH DOKUMENTÓW

| Plik | Zawartość |
|---|---|
| `docs/FABULA.md` | Biblia narracyjna: postacie, dialogi, motywy, intro, zakończenia |
| `docs/GAME_BRIEF.md` | Krótki opis produktu i misji |
| `docs/GDD.md` | Strukturalny dokument projektowy |
| `docs/ARCHITECTURE.md` | Stack, struktura katalogów, reguły |
| `docs/SCOPE.md` | Co jest i czego nie ma w MVP |
| `docs/IDEAS_LATER.md` | Odroczone pomysły |
| `docs/ADRs/ADR-001-stack.md` | Decyzja stacku: Phaser 4, Dexie, Zod |
| `dodatki/research/00-RESEARCH-KONTEKST.md` | Baza naukowa NASA/ESA |

---

## 11. STATUS DOKUMENTACJI

### Ukończone

| Dokument | Status |
|---|---|
| `docs/FABULA.md` | ✅ Wersja 1.0 — pełna biblia narracyjna |
| `mechanika/01-game-flow.md` | ✅ Wersja 1.0 |
| `mechanika/02-screens-and-scenes.md` | ✅ Wersja 1.0 |
| `mechanika/03-resources.md` | ✅ Wersja 1.0 — patrz: korekta Radiation w 99 |
| `mechanika/04-crew.md` | ✅ Wersja 1.0 |
| `mechanika/05-ship-systems.md` | ✅ Wersja 1.0 |
| `mechanika/06-missions.md` | ✅ Wersja 1.0 |
| `mechanika/07-events.md` | ✅ Wersja 1.0 — 15 eventów MVP |
| `mechanika/08-progression.md` | ✅ Wersja 1.0 |
| `mechanika/09-failure-and-game-over.md` | ✅ Wersja 1.0 |
| `mechanika/10-balancing-notes.md` | ✅ Wersja 1.0 |
| `mechanika/99-open-questions.md` | ✅ Wersja 1.0 |
| `mechanika/00-overview.md` | ✅ Wersja 1.0 — ten plik |

### Wymagające korekty przed implementacją

| Dokument | Korekta | Priorytet |
|---|---|---|
| `mechanika/03-resources.md` | Radiation baseline: 1,81 → ~0,36 mSv/dzień (patrz: pytanie B1 w 99) | **KRYTYCZNE** |
| `mechanika/04-crew.md` | Zaktualizować wartości Radiation per tura po korekcie baseline | **KRYTYCZNE** |
| `mechanika/10-balancing-notes.md` | Zaktualizować tabelę kluczowych liczb po korekcie Radiation | WAŻNE |

### Jeszcze do wypełnienia (poza mechaniką)

| Dokument | Status |
|---|---|
| `docs/GDD.md` | Szkielet — wymaga synchronizacji z mechaniką |
| `mechanika/06-missions.md` | Rozważyć M12b (dropsondy) — pytanie B5 w 99 |

---

## 12. DWIE DECYZJE PRZED KODOWANIEM

*(Z `mechanika/99-open-questions.md`, sekcja B)*

**B1 — Radiation baseline:**
Zmień `1,81 mSv/dzień` na `0,36 mSv/dzień` w `mechanika/03-resources.md`.
Uzasadnienie: RAD/MSL mierzy poza statkiem przy minimalnej osłonie.
*Kairos* z osłoną 50 g/cm² redukuje to ~5×.
Bez tej korekty kapitan przekracza limit radiacji po ~11 turach.

**B7 — Torpor kapitana:**
Zdecydować: czy kapitan MOŻE być aktywny przez każdą turę
(opcjonalny torpor, balans premiuje odpoczynek)
czy MUSI wchodzić w torpor co 3–4 tury (obowiązkowy).
Decyzja wpływa na design Fazy 5 tury i interfejs BridgeScene.

---

## Overview update — v1.0

**Data ukończenia dokumentacji mechaniki:** 2026-05

**Zawartość mechaniki w liczbach:**
- 14 misji MVP (6 podróżnych, 3 podejście, 2 orbitalne, 3 powierzchniowe)
- 15 eventów MVP (6 FORCED, 9 WEIGHTED)
- 7 postaci z pełnymi profilami mechanicznymi
- 6 zakończeń narracyjnych + 5 twardych KG
- 13 systemów statku (7 operacyjnych + 6 ECLSS)
- 5 zasobów + 1 akumulator (LifeData)
- 6 głosów wewnętrznych kapitana z triggerami wzrostu
- ~174 tury, 5 aktów, 58 lat misji w czasie fikcji

**Następny krok:**
Rozstrzygnąć pytania B1 i B7 z `mechanika/99-open-questions.md`.
Potem: scaffoldowanie projektu Vite + Phaser 4
per `docs/ARCHITECTURE.md` i `.github/copilot-instructions.md`.
