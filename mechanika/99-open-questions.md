# 99 — Open Questions
## Pytania Otwarte — Konsolidacja | Wersja 1.0

> Wszystkie nierozstrzygnięte pytania projektowe zebrane z wszystkich plików mechaniki.
> Każde pytanie ma status, priorytet i wskazanie którego pliku dotyczy.
> Odpowiedzi na pytania krytyczne blokują implementację.
> Ostatnia aktualizacja: 2026-05

---

## JAK CZYTAĆ TEN PLIK

**Status:**
- `OTWARTE` — brak decyzji, wymaga odpowiedzi
- `SUGESTIA` — proponowane rozwiązanie, wymaga zatwierdzenia
- `ZABLOKOWANE` — zależy od innej decyzji (podano której)
- `ODROCZONE` — świadomie poza MVP, do `docs/IDEAS_LATER.md`

**Priorytet:**
- `KRYTYCZNE` — blokuje implementację kluczowych systemów
- `WAŻNE` — wpływa na decyzje projektowe w Akcie IV–V
- `NISKIE` — może być rozstrzygnięte w trakcie produkcji

---

## KATEGORIA A — FABUŁA I NARRACJA

*(Źródło: `docs/FABULA.md`, sekcja 11)*

---

### A1 — Paweł Nowak jako postać aktywna

**Pytanie:** Czy Paweł (syn Jakuba) pojawia się jako aktywna postać
w wiadomościach z Ziemi — z własnym głosem, rozwojem, historią?
Czy jest tylko nazwanym podmiotem w monologach PAMIĘCI?

**Status:** `OTWARTE`
**Priorytet:** `WAŻNE`
**Dotyczy:** `docs/FABULA.md`, `mechanika/07-events.md` (event `late_letter`)

**Kontekst decyzji:**
- Pełna postać: bogatsze emocje, więcej contentu do napisania, silniejszy arc PAMIĘCI
- Nazwany podmiot: lżejszy produkcyjnie, zachowuje prywatność narracyjną
- Sugestia: Paweł jako głos bez portretu — słyszalny, niewidoczny

---

### A2 — Zakończenie Felix/ARIA — otwarte czy kanoniczne

**Pytanie:** Czy wątek Felix/ARIA ma jedno kanoniczne zakończenie
(ARIA „budzi się" do pełnej świadomości) czy pozostaje celowo otwartym pytaniem
bez odpowiedzi?

**Status:** `SUGESTIA`
**Priorytet:** `WAŻNE`
**Dotyczy:** `docs/FABULA.md`, `mechanika/07-events.md` (events 14, 15), `mechanika/08-progression.md`

**Sugerowane rozwiązanie:**
Celowo otwarte. ARIA nigdy dramatycznie „nie budzi się".
Zmienia się powoli, subtelnie. Gracz może interpretować jej zachowanie
jako świadomość lub jako doskonały model statystyczny ludzkiego zachowania.
Gra nie rozstrzyga. Felix rozstrzyga dla siebie — i nie mówi nam co myśli.

---

### A3 — Język dialogów załogi

**Pytanie:** Czy każda postać mówi w swoim natywnym języku
(Mira po angielsku, Grzech po polsku, Yuki po japońsku) z tłumaczeniem
jako mechaniką immersyjną — czy wszyscy mówią jednym językiem gry?

**Status:** `OTWARTE`
**Priorytet:** `WAŻNE`
**Dotyczy:** `docs/FABULA.md`, `mechanika/02-screens-and-scenes.md`

**Kontekst decyzji:**
- Jeden język (polski): prostsza implementacja, spójna narracja
- Wielojęzyczność: immersja, ale wymaga tłumaczeń i UI dla każdego języka
- Kompromis: wszyscy mówią po polsku jako lingua franca misji,
  ale Grzech ma śląski akcent w sformułowaniach, Yuki cytuje po japońsku fragmenty

---

### A4 — Utrata ARII jako postaci

**Pytanie:** Czy gracz może stracić ARIĘ jako funkcjonującą postać?
(awaria systemu AI, decyzja Felixa, błąd krytyczny)

**Status:** `SUGESTIA`
**Priorytet:** `WAŻNE`
**Dotyczy:** `docs/FABULA.md`, `mechanika/09-failure-and-game-over.md`

**Sugerowane rozwiązanie:**
ARIA może ulec częściowej degradacji (Comm system failure, hardware damage)
ale nie „umiera" dramatycznie. Przy Comm = 0: ARIA ograniczona do lokalnych systemów.
Przy Reaktor Fuzyjny = 0: ARIA w trybie minimum (jeden zdanie per tura).
Pełna utrata ARII: tylko przy KG-03 (całkowita awaria reaktora) — wtedy gra i tak kończy się.

---

### A5 — Nazwa planety i nadanie przez Yuki

**Pytanie:** *Limes* (granica, łacina) jako robocza nazwa przez całą grę?
Czy Yuki nadaje jej własną nazwę po potwierdzeniu życia?
Jeśli tak — jaką?

**Status:** `SUGESTIA`
**Priorytet:** `NISKIE`
**Dotyczy:** `docs/FABULA.md`, `mechanika/07-events.md` (event `dms_confirmed`)

**Sugerowane rozwiązanie:**
*Limes* przez całą grę. W evencie `dms_confirmed` —
Yuki mówi po cichu jedno słowo którego nie tłumaczy.
Gracz może to zinterpretować lub nie. Oficjalna nazwa zostaje *Limes*.

---

### A6 — Epilog ARII w zakończeniu ZOSTAJĄ (wariant B)

**Pytanie:** Czy zakończenie ZOSTAJĄ (wariant B — wybór) powinno mieć
dodatkowy epilog z perspektywy ARII po upływie [X] lat?

**Status:** `SUGESTIA`
**Priorytet:** `NISKIE`
**Dotyczy:** `mechanika/09-failure-and-game-over.md`

**Sugerowane rozwiązanie:**
Tak, ale krótki — 3–5 zdań. ARIA po 10 latach od decyzji.
Felix pisze w dzienniku. Limes nadal tam jest.
Dostępny jako opcja z ekranu LogbookScene po zakończeniu.

---

## KATEGORIA B — MECHANIKA KLUCZOWA

---

### B1 — PROMIENIOWANIE: fundamentalny błąd liczbowy

**Pytanie:** ⚠️ Przy aktualnym baseline (1,81 mSv/dzień) i kapitanie
aktywnym przez każdą turę — limit 620 mSv zostaje przekroczony
po ~11 turach aktywności. Jak to rozwiązać?

**Status:** `KRYTYCZNE` — wymaga decyzji przed implementacją
**Priorytet:** `KRYTYCZNE`
**Dotyczy:** `mechanika/03-resources.md`, `mechanika/04-crew.md`, `mechanika/10-balancing-notes.md`

**Analiza:**
```
Baseline 1,81 mSv/dzień = ~54 mSv/turę aktywną
Limit mężczyźni: 620 mSv
Tury do przekroczenia przy ciągłej aktywności: 620/54 = ~11 tur

Misja trwa: ~174 tury
Nawet przy rotacji torporu (1 akt. / 3 torporu):
  ~43,5 cykli × 54 mSv = 2,349 mSv — 3,8× powyżej limitu
```

**Opcje rozwiązania:**

| Opcja | Zmiana | Konsekwencja |
|---|---|---|
| A | Obniż baseline do ~0,05 mSv/dzień (lepsza osłona statku) | Zmiana w 03-resources.md i 10-balancing-notes.md; 1,5 mSv/turę |
| B | Zwiększ limity do wartości „misyjnych" (3× wyższe) | Mniej naukowe, ale działa |
| C | Radiation jako skala symboliczna (0–100) nie mSv | Traci naukowe zakorzenienie |
| D | Kapitan NIE jest aktywny przez każdą turę (musi rotować torpor) | Zmiana filozofii gry |

**Sugerowane rozwiązanie — Opcja A:**
*Kairos* ma osłonę 50 g/cm² + magazyn centralny jako shelter.
Baseline: 0,36 mSv/dzień (20% wartości RAD/MSL).
Tura aktywna: 0,36 × 30 = 10,8 mSv.
Kapitan przy rotacji 1:3: ~43,5 × 10,8 = 470 mSv → poniżej limitu 620 mSv. ✓
Solar flare: +25–60 mSv (nadal odczuwalny). ✓

---

### B2 — Minimum kapsuł torporu dla rotacji

**Pytanie:** Ile kapsuł musi być sprawnych żeby rotacja torporu
była w ogóle możliwa?

**Status:** `SUGESTIA`
**Priorytet:** `WAŻNE`
**Dotyczy:** `mechanika/05-ship-systems.md`, `mechanika/01-game-flow.md`

**Sugerowane rozwiązanie:**
Minimum 4 z 7 kapsuł sprawnych (>40% każda).
Uzasadnienie: zawsze musi być możliwość żeby kapitan + 1 byli aktywni,
reszta w torpor. 5 osób w torpor = 5 sprawnych kapsuł minimum?
Lub: minimum 1 kapsuła sprawna per nieaktywna osoba.

---

### B3 — Zachowanie CISZA gdy Comm naprawione w ostatniej chwili

**Pytanie:** Jeśli Comm = 0 przez 8+ tur (trigger zakończenia CISZA)
ale gracz naprawia Comm w ostatniej chwili — czy zakończenie CISZA
ma alternatywną wersję?

**Status:** `SUGESTIA`
**Priorytet:** `NISKIE`
**Dotyczy:** `mechanika/09-failure-and-game-over.md`

**Sugerowane rozwiązanie:**
Tak. Naprawione Comm przed Aktem V = dostępna „Cisza z odpowiedzią":
Ziemia milczała przez lata. Potem sygnał. Co to jest za Ziemia?
Ten element warto rozwinąć jako osobne micro-event.

---

### B4 — Kolizja misji z eventem: priorytet decyzji

**Pytanie:** Kiedy event wymaga postaci zaangażowanej w misję wieloturową,
kto podejmuje decyzję automatyczną jeśli gracz wybierze ignorowanie eventu?
ARIA? Najlepsza dostępna postać? Najgorsza?

**Status:** `SUGESTIA`
**Priorytet:** `WAŻNE`
**Dotyczy:** `mechanika/06-missions.md`, `mechanika/07-events.md`

**Sugerowane rozwiązanie:**
Gdy gracz wybiera ignorowanie eventu (misja kontynuowana):
ARIA wybiera najlepszą dostępną aktywną postać dla eventu.
Jeśli kapitan jest jedyną dostępną osobą: kapitan musi przerwać misję.
*(Kapitan jest zawsze aktywny — zawsze jest ktoś do decyzji.)*

---

### B5 — Wariant dropsond dla M12

**Pytanie:** Czy misja M12 (Ekspedycja atmosferyczna) powinna mieć
wariant bez lądowania — dropsondy orbitalne?
Bezpieczniejsze, mniej LifeData, nie wymaga Leny.

**Status:** `SUGESTIA`
**Priorytet:** `NISKIE`
**Dotyczy:** `mechanika/06-missions.md`

**Sugerowane rozwiązanie:**
Tak, jako M12b. Stats:
- Tylko Yuki (NAUKA difficulty 6)
- Tura: 1 (szybsze)
- LifeData: +3 (mniej niż pełna ekspedycja)
- Brak ryzyka śmierci
- Nie triggeruje COSPAR protocol (brak fizycznych próbek)
- Nie umożliwia M14 Analiza biologiczna

---

### B6 — M14 solo przez Felixa

**Pytanie:** Czy Felix może przeprowadzić M14 Analizę biologiczną
samodzielnie jeśli Yuki jest niedostępna (w torpor, ranna, martwa)?

**Status:** `SUGESTIA`
**Priorytet:** `WAŻNE`
**Dotyczy:** `mechanika/06-missions.md`

**Sugerowane rozwiązanie:**
Tak, ale:
- Difficulty: 15 zamiast 12 (bez Yuki to prawie niemożliwe)
- Efekt sukcesu: LifeData +5 (zamiast +10)
- Efekt: odkrycie MOŻLIWE (poziom 1 maksymalnie)
- Narracja: Felix w laboratorium, sam, bez Yuki.
  ARIA mu asystuje. To jest osobny wariant logbooka.

---

### B7 — Torpor Jakuba obowiązkowy czy opcjonalny

**Pytanie:** Czy gracz może w ogóle zdecydować żeby Jakub nigdy
nie wchodził w torpor? Czy gra powinna to blokować?

**Status:** `OTWARTE`
**Priorytet:** `KRYTYCZNE`
**Dotyczy:** `mechanika/01-game-flow.md`, `mechanika/04-crew.md`

**Kontekst:**
Powiązane z B1 (promieniowanie). Jeśli rozwiążemy B1 przez Opcję A
(niższy baseline), kapitan może być aktywny przez każdą turę
bez przekroczenia limitu. Ale to usuwa mechaniczny powód do torporu.

**Wariant A:** Torpor opcjonalny — kapitan może zawsze być aktywny,
ale accumuluje Radiation i Fatigue szybciej. Balans premiuje torpor.

**Wariant B:** Torpor obowiązkowy co 3–4 tury — gra blokuje kapytana.
Zmniejsza kontrolę gracza, ale odpowiada realizmowi biologicznemu.

---

## KATEGORIA C — BALANS I LICZBY

---

### C1 — LifeData: cap i tempo akumulacji

**Pytanie:** Czy cap LifeData = 100 jest właściwy?
Czy tempo akumulacji przez M03 (obserwacja co tura) nie sprawia
że gracz ma za dużo LifeData zanim dotrze do Limes?

**Status:** `SUGESTIA`
**Priorytet:** `WAŻNE`
**Dotyczy:** `mechanika/06-missions.md`, `mechanika/10-balancing-notes.md`

**Sugerowane rozwiązanie:**
Limit M03 per akt: maksymalnie +20 LifeData z M03 per akt (nie per tura).
Uzasadnienie: dane z rejsu mają diminishing returns — po pewnym czasie
wiesz tyle samo, musisz dotrzeć blisko żeby dowiedzieć się więcej.
Powyżej 20/akt: M03 daje tylko +0,5 zamiast +1–2.

---

### C2 — Morale Third Quarter: −3/turę zbyt surowe?

**Pytanie:** Degradacja Morale +50% w Akcie III (−3/tura zamiast −2)
w połączeniu z potencjalnymi eventami i `last_dinner` — czy to nie jest
zbyt punishing dla niedoświadczonego gracza?

**Status:** `OTWARTE`
**Priorytet:** `WAŻNE`
**Dotyczy:** `mechanika/04-crew.md`, `mechanika/10-balancing-notes.md`

**Propozycja testu:**
Zacząć od −2,5/turę w Akcie III (zamiast −3).
Third Quarter ma być trudny, ale nie wall.

---

### C3 — Wartość startowa Morale Miry: 75

**Pytanie:** Mira startuje z Morale 75 (niżej niż reszta).
Czy to nie jest zbyt odczuwalne dla gracza który nie wie o jej tle?

**Status:** `SUGESTIA`
**Priorytet:** `NISKIE`
**Dotyczy:** `mechanika/04-crew.md`

**Sugerowane rozwiązanie:**
Zachować. Gracz zauważy że Mira jest „trochę ciszej" niż reszta
bez wiedzy dlaczego — i to jest właściwy efekt narracyjny.

---

## KATEGORIA D — TECHNICZNE I UI

---

### D1 — Głosy wewnętrzne na mobile

**Pytanie:** EventScene na telefonie (<600dp): głosy wewnętrzne
są widoczne od razu czy schowane za ikoną?

**Status:** `SUGESTIA`
**Priorytet:** `WAŻNE`
**Dotyczy:** `mechanika/02-screens-and-scenes.md`

**Sugerowane rozwiązanie:**
Schowane za ikoną (toggle button u góry eventu).
Tap na ikonę → panel głosów wysuwa się z dołu (bottom sheet).
Domyślnie zamknięte na mobile, otwarte na desktop.

---

### D2 — Język gry i UI

**Pytanie:** Gra jest w języku polskim?
Czy docelowo będzie angielska wersja?

**Status:** `OTWARTE`
**Priorytet:** `WAŻNE`
**Dotyczy:** wszystkie pliki narracyjne

**Kontekst:**
Wszystkie narracyjne pliki są po polsku.
Jeśli planowana jest wersja angielska — architektura i18n musi być w kodzie od początku.
Decyzja ma wpływ na strukturę plików JSON.

---

### D3 — Dźwięk i muzyka

**Pytanie:** Wymagania audio nie są zdefiniowane w żadnym pliku mechaniki.
Jaki jest zakres: efekty dźwiękowe, muzyka ambientowa, tematy per postać?

**Status:** `OTWARTE`
**Priorytet:** `WAŻNE`
**Dotyczy:** `mechanika/02-screens-and-scenes.md`, `docs/SCOPE.md`

**Minimalne wymagania MVP:**
- 1 ambient loop (przestrzeń kosmiczna)
- Efekty UI (klik, alert, check sukces/porażka)
- 1 motyw dla TorporScene
- Brak głosu lektora (zbyt kosztowne dla MVP)

---

### D4 — Opcje trudności

**Pytanie:** Czy gra powinna mieć wybór poziomu trudności?
(np. łatwiejszy: +20% CZĘŚCI na start; trudniejszy: −10% PALIWO)

**Status:** `SUGESTIA`
**Priorytet:** `NISKIE`
**Dotyczy:** `mechanika/10-balancing-notes.md`

**Sugerowane rozwiązanie:**
MVP: jeden poziom trudności.
Post-MVP: tryb narracyjny (mniejszy koszt porażek, więcej kontekstu emocjonalnego).

---

### D5 — Identyfikacja zapisu gry

**Pytanie:** Jak nazywa się zapis gry? Czy Dexie schema ma named slots,
czy jeden permanentny slot "active run"?

**Status:** `SUGESTIA`
**Priorytet:** `WAŻNE`
**Dotyczy:** implementacja `src/storage/SaveSystem.ts`

**Sugerowane rozwiązanie:**
Jeden aktywny slot + kopia zapasowa poprzedniego stanu.
Nazwa: `kairos_run_[timestamp]_active` i `kairos_run_[timestamp]_backup`.
Logbooki: osobna tabela Dexie, nie usuwana przy permadeath.

---

## KATEGORIA E — POST-MVP (ODROCZONE)

Pytania które nie blokują MVP ale wymagają decyzji przed rozszerzeniem.

---

### E1 — Skala odkrycia 4–6

**Pytanie:** Kiedy i jak zaimplementować poziomy życia 4–6 (rośliny, zwierzęta, inteligencja)?

**Status:** `ODROCZONE`
**Dotyczy:** `mechanika/08-progression.md`, `docs/IDEAS_LATER.md`

---

### E2 — System walki (BattleScene)

**Pytanie:** Kiedy i jak zdefiniować mechaniki walki?

**Status:** `ODROCZONE`
**Dotyczy:** `mechanika/BattleScene stub`, `docs/IDEAS_LATER.md`

---

### E3 — Wpływ SYGNAŁ=10 na ZOSTAJĄ wariant A

**Pytanie:** Gdy Jakub zostaje z konieczności (PALIWO=0) ale SYGNAŁ=10 —
czy logbook powinien być inny? Czy to jest triumf przebrany za tragedię?

**Status:** `SUGESTIA`
**Priorytet:** `NISKIE` (MVP-level detail)
**Dotyczy:** `mechanika/08-progression.md`, `mechanika/09-failure-and-game-over.md`

**Sugerowane rozwiązanie:**
Tak. Przy SYGNAŁ ≥ 9 i zakończeniu ZOSTAJĄ wariant A:
logbook Jakuba ma dodatkowy akapit — „Może miałem to wszystko od początku zaplanowane."

---

## PRIORYTET ZAMKNIĘCIA — LISTA DECYZYJNA

Pytania które MUSZĄ być rozstrzygnięte przed kodowaniem systemów MVP:

```
KRYTYCZNE (resolve first):
☐ B1 — Promieniowanie: baseline do korekty (sugestia: Opcja A)
☐ B7 — Torpor Jakuba: obowiązkowy czy opcjonalny?

WAŻNE (resolve before Act IV implementation):
☐ A2 — Felix/ARIA: otwarte zakończenie (sugestia: tak, celowo otwarte)
☐ A3 — Język dialogów (sugestia: jeden język + akcenty)
☐ B4 — Kolizja misji/event: kto decyduje automatycznie
☐ B6 — M14 solo przez Felixa (sugestia: tak, difficulty 15)
☐ C2 — Third Quarter: −3/turę czy −2,5/turę?
☐ D2 — Język gry i i18n architektura

NISKIE (można odkryć w trakcie produkcji):
☐ A1 — Paweł jako postać aktywna
☐ A4 — ARIA loss condition
☐ A5 — Nazwa planety po odkryciu
☐ B5 — M12b dropsondy
☐ C1 — LifeData cap per akt
☐ D4 — Opcje trudności
```

---

## Open Questions update — v1.0

**Ukończono:**
- Konsolidacja wszystkich pytań otwartych z 9 plików mechaniki
- Kategorie A–E (fabuła, mechanika, balans, techniczne, post-MVP)
- Status i priorytet każdego pytania
- Lista decyzyjna z kolejnością zamknięcia

**Krytyczne blokery przed implementacją:**
- B1 (promieniowanie) — wymaga korekty wartości w 03-resources.md
- B7 (torpor Jakuba) — wymaga decyzji filozoficznej o design intent
