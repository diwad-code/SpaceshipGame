# 10 — Balancing Notes
## Notatki Balansowe | Wersja 1.0

> Wartości startowe, budżety zasobów, krzywa trudności i rzeczy do przetestowania.
> Wszystkie liczby z uzasadnieniem — brak magicznych wartości.
> Ostatnia aktualizacja: 2026-05

---

## FILOZOFIA BALANSU

Gra ma być trudna, ale nie arbitralnie surowa.

**Cel:** gracz który rozumie systemy powinien być w stanie dotrzeć do Limes
z żywą (lub prawie żywą) załogą i wystarczającymi zasobami na odkrycie.
Gracz który ignoruje systemy nie powinien dotrzeć do Limes w dobrym stanie.

**Entropia jest wbudowana:** większość parametrów naturalnie spada.
Balans nie polega na tym żeby gracz mógł wszystko naprawić —
polega na tym żeby musiał wybrać *co* naprawia.

**Trudność nie przez losowość, przez priorytety:**
Każde zdarzenie jest zaprojektowane tak żeby miało sens.
Gracz który przegrał powinien wiedzieć dlaczego — nie „miałem pecha",
ale „nie naprawiłem CO₂ na czas" lub „zignorowałem Morale Grzecha".

---

## 1. WARTOŚCI STARTOWE — PEŁNA TABELA

### Zasoby

| Zasób | Start | Produkcja/tura | Konsumpcja/tura (2 aktywnych) | Net/tura |
|---|---|---|---|---|
| TLEN | 80 | +1,8 (ECLSS 100%) | −2,2 (aktywna załoga) | **−0,4** |
| WODA | 70 | +5,88 (WRS 100%) | −6,0 | **−0,12** |
| ŻYWNOŚĆ | 60 | +4,8 (Hydro+Bio 100%) | −4,0 | **+0,8** |
| PALIWO | 100 | 0 (brak produkcji) | −0 (pasywny rejs) | **0** |
| CZĘŚCI | 75 | 0 (brak produkcji) | −per naprawa | **per decyzja** |

**Uzasadnienie TLEN:** net −0,4/turę przy pełnym ECLSS i 2 aktywnych.
Zapas 80 jednostek → wyczerpanie po ~200 turach bez eventów.
Misja: 174 tury. TLEN powinno być komfortowe przy dobrym zarządzaniu ECLSS.
Niebezpieczne gdy ECLSS degraduje do <70%.

**Uzasadnienie WODA:** net −0,12/turę. Praktycznie stały przy sprawnym WRS.
Staje się problemem tylko gdy WRS spada znacznie (<50%).

**Uzasadnienie ŻYWNOŚĆ:** +0,8 netto. Jedzenie NIE jest podstawowym wektorem presji.
Staje się problemem gdy oba systemy produkcji fail (eventy, długotrwały brak konserwacji).
Designed to create stress through system degradation, not baseline consumption.

### Systemy statku (wartości startowe)

| System | Start % | Uwaga |
|---|---|---|
| Kadłub | 100% | — |
| Sensory | 100% | — |
| Lab | 100% | — |
| Comm | 100% | — |
| Medbay | 100% | — |
| Kapsułki torporu (każda) | 100% | Kapsuła Miry: 95% po event `mira_capsule_fault` |
| Warsztat | 100% | — |
| CO₂ Skruber | 100% | — |
| Reaktor Sabatiera | 100% | — |
| WRS | 100% | — |
| Hydroponika | 95% | Nowa, ale wymaga dogrania protokołów |
| Bioreaktory | 97% | — |
| Reaktor Fuzyjny | 100% | — |

### Parametry startowe załogi

| Postać | Health | Morale | Fatigue | Radiation |
|---|---|---|---|---|
| Jakub Nowak | 100 | 80 | 0 | 0 |
| Mira Osei | 100 | 75 | 0 | 0 |
| Grzech | 97 | 80 | 0 | 0 |
| Yuki Tanaka | 95 | 85 | 0 | 0 |
| Amara Nwosu | 100 | 82 | 0 | 0 |
| Lena Kowalska | 100 | 70 | 0 | 0 |
| Felix Ramos | 100 | 78 | 0 | 0 |

---

## 2. BUDŻET PALIWA — KLUCZOWY ZASÓB DECYZJI

PALIWO to jedyny zasób który nie produkuje się i zużywa się przez wybory.

```
START:                          100 jednostek

Rezerwa obowiązkowa:
  Deceleration burn (Limes):   −15
  Return acceleration:          −15
  Bufor bezpieczeństwa:          −5
  RAZEM REZERWA:                −35

Dostępne na manewry:             65 jednostek
przez ~174 tury

Szacowane zużycie na manewry:
  Korekty kursu (~20 tur):    −20 (po ~1/tura gdy potrzeba)
  Eventy emergency (~2-3):    −12 (po ~5/event)
  Protokół orbitalny M08:      −1 (zaoszczędzone, nie stracone)
  RAZEM ZUŻYTE:               −32

Oczekiwany PALIWO przy Limes:
  100 − 32 = 68
  68 − 15 (decel) = 53

Oczekiwany PALIWO po eksploracji:
  53 − ~8 (manewry orbitalne) = ~45

Powrót wymaga:               −15 (akceleracja) + −5 (bufor)
PALIWO po powrocie:           ~25

Zakończenie CICHY POWRÓT lub TRIUMF jest możliwe przy ostrożnej grze.
Zakończenie ZOSTAJĄ (konieczność) gdy PALIWO <35 przy Limes.
```

**Wniosek:** Gracz który nie zarządza PALIWO aktywnie ma ~60% szans
na powrót. Gracz który optymalizuje manewry — ~90%.
To jest właściwy zakres. Nie gwarantowany powrót, ale nie losowy.

---

## 3. BUDŻET CZĘŚCI — META-ZASÓB

```
START:                           75 jednostek
BRAK PRODUKCJI

Szacowane zużycie przez 174 tury:
  Rutynowe naprawy system degradacji:
    ~3 naprawy/akt × 4 akty × ~7 CZĘŚCI = ~84 CZĘŚCI
  Naprawy wywołane przez eventy:
    ~5 eventów × ~8 CZĘŚCI = ~40 CZĘŚCI
  Misje powierzchniowe (M12, M13):
    −5 CZĘŚCI
  RAZEM POTRZEBNE:              ~129 CZĘŚCI

DEFICIT:                        ~54 CZĘŚCI (bez strategii)
```

**Wniosek:** Gracz NIE może naprawić wszystkiego. To jest celowe.
Musi priorytetyzować. Macierz z `mechanika/05-ship-systems.md`
jest wskazówką — nie każda naprawa jest równie ważna.

**Efekt kaskady CZĘŚCI:**
Gdy Warsztat spada do <65% → każda naprawa kosztuje +1 CZĘŚCI.
Przy Warsztacie <40% → +2 CZĘŚCI/naprawa.
Naprawa Warsztatu kosztuje CZĘŚCI.
*Ten paradoks jest celowy — odkładanie naprawy Warsztatu kosztuje więcej niż jej zrobienie.*

---

## 4. TEMPO DEGRADACJI SYSTEMÓW

Przy standardowej rotacji (2 aktywne osoby: kapitan + 1):
*Możliwe utrzymanie (bez CZĘŚCI): 2–3 systemy per tura.*

```
Liczba systemów: 13 (7 operacyjnych + 6 ECLSS)
Możliwe utrzymania/tura: 2
Cykl pełnego utrzymania: ~6-7 tur

Bez żadnej konserwacji: -0,3% do -0,5%/turę per system
Ze standardową konserwacją (co 6-7 tur): netto ~-0,07%/turę

Szacowany stan systemów przy końcu misji (ze standardową opieką):
  Akt I koniec (tura 17):    ~95%   (świeże, dobrze utrzymane)
  Akt II koniec (tura 87):   ~85%   (widoczna degradacja)
  Akt III koniec (tura 130): ~75%   (napięcie, kilka systemów wymaga napraw)
  Akt IV koniec (tura 157):  ~65%   (statek stary, ale sprawny)
```

**Wyjątek:** CO₂ Skruber degraduje szybciej (~1%/tura) i jest krytyczny.
Powinien być priorytyzowany w konserwacji Grzecha przez całą grę.

---

## 5. KRZYWA TRUDNOŚCI PER AKT

### Akt I — Odlot (tury 1–17, 10%)

```
Trudność:       ████░░░░░░  4/10
Szansa eventu:  35%
Eventy per akt: ~6
Morale degradacja: −2/turę (standard)
Systemy:        ~95-100%
Zasoby:         komfortowe
Cel gracza:     uczyć się priorytetyzacji
Forced eventy:  brak (poza intro)
```

**Projektowany stan na końcu Aktu I:**
- Systemy: ~95% (lekka degradacja)
- PALIWO: ~95 (kilka drobnych korekt)
- CZĘŚCI: ~70 (jedna-dwie naprawy)
- Morale załogi: 65-80 (lekki spadek)
- LifeData: ~5

---

### Akt II — Długa Ciemność (tury 18–87, 50%)

```
Trudność:       ██████░░░░  6/10
Szansa eventu:  35%
Eventy per akt: ~24
Morale degradacja: −2/turę (standard)
Systemy:        ~80-95% (degradacja widoczna)
Zasoby:         napięcie zaczyna się
Cel gracza:     zarządzać entropią
Forced eventy:  ghost_signal (prawdopodobny), late_letter
```

**Projektowany stan na końcu Aktu II:**
- Systemy: ~80-85% (wymagają uwagi)
- PALIWO: ~78 (kilkanaście korekt)
- CZĘŚCI: ~50 (naprawy eventów + degradacja)
- Morale załogi: 55-70 (odczuwalne zmęczenie)
- LifeData: ~15-20
- Radiation Grzecha: ~160-200 mSv (zbliża się do 50% limitu)

---

### Akt III — Trzeci Kwartał (tury 88–130, 75%)

```
Trudność:       █████████░  9/10
Szansa eventu:  45%
Eventy per akt: ~19 (więcej per tura)
Morale degradacja: −3/turę (Third Quarter +50%)
Systemy:        ~70-80% (kilka pilnych napraw)
Zasoby:         presja
Cel gracza:     przetrwać spójność zespołu
Forced eventy:  last_dinner (obowiązkowy), orders_for_someone_else
```

**Projektowany stan na końcu Aktu III:**
- Systemy: ~65-75% (wymagają napraw)
- PALIWO: ~65
- CZĘŚCI: ~30-35 (kluczowy zasób)
- Morale załogi: 40-60 (Third Quarter zostawia ślad)
- LifeData: ~25-35
- Radiation Grzecha: ~280-320 mSv (powyżej 50% → debuff Health aktywny)

---

### Akt IV — Przybycie (tury 131–157, 90%)

```
Trudność:       ████████░░  8/10 (mniej zdarzeń, wyższe stawki)
Szansa eventu:  40%
Eventy per akt: ~10
Morale degradacja: −2/turę (normalizacja po kryzysie)
Systemy:        ~60-70% (statek wyraźnie stary)
Zasoby:         PALIWO i CZĘŚCI krytyczne
Cel gracza:     osiągnąć odkrycie nie tracąc możliwości powrotu
Forced eventy:  first_signal_limes, dms_confirmed
```

**Projektowany stan na końcu Aktu IV:**
- Systemy: ~55-70%
- PALIWO: ~40-55 (po deceleration: ~25-40)
- CZĘŚCI: ~15-25 (ostatnie naprawy)
- Morale załogi: 50-70 (euforia odkrycia lub depresja fałszywej sygnatury)
- LifeData: ~60-90 (zależy od misji)

---

### Akt V — Rozwiązanie (tury 158–174, 100%)

```
Trudność:       ██████░░░░  6/10 (mechanicznie uproszczony)
Szansa eventu:  20% (zakończenia dominują)
Eventy per akt: ~3-4 (fabularnie ważne, nie losowe)
Cel gracza:     zamknąć historię
Focused na:     logbook, decyzja o powrocie/zostaniu
```

---

## 6. KLUCZOWE LICZBY Z BADAŃ NAUKOWYCH

*(Źródło: NASA, ESA, RAD/MSL, Kanas 2021, Bradford SpaceWorks NIAC 2013/2018)*

| Parametr | Wartość w grze | Źródło realne |
|---|---|---|
| Promieniowanie GCR baseline | 1,81 mSv/dzień = ~54 mSv/turę aktywną | NASA RAD/MSL 2013 |
| Limit radiacji (kobiety) | 470 mSv | NASA REID 3% |
| Limit radiacji (mężczyźni) | 620 mSv | NASA REID 3% |
| Redukcja radiacji w torpor | −95% (→ ~16 mSv/90 dni torporu) | SpaceWorks NIAC 2013 |
| Utrata kości (bez grawit.) | 1,5%/miesiąc → ~1,5 pkt Health/turę | NASA Twin Study |
| Recyrkulacja wody | 98% | NASA BPA 2023 |
| Odzysk O₂ (Sabatier) | 93% | ECLSS NASA |
| Third Quarter onset | 50–75% czasu misji | Kanas 2021 |
| Third Quarter Morale debuff | −3/turę (vs standard −2) | Estymacja z Mars-500 |
| Solar flare Radiation bonus | +50 do +120 mSv (jednorazowy) | NASA SPE data |
| Deceleration burn | −15 PALIWO | Szacunek per Daedalus model |
| Opóźnienie sygnału (14,2 ly) | 14,2 roku = ~43 tury | Prędkość światła |

---

## 7. PRAWDOPODOBIEŃSTWA EVENTÓW

### Szansa eventu per tura

| Akt | Szansa | Uzasadnienie |
|---|---|---|
| I | 35% | Spokojny start, nauka mechanik |
| II | 35% | Standard — entropia narasta ale równomiernie |
| III | 45% | Third Quarter — chaos psychologiczny i techniczny |
| IV | 40% | Lekko podwyższone — zbliżenie do nieznanego |
| V | 20% | Skupienie na zakończeniu, nie na eventach |

### Weighted events — wagi per motyw per akt

| Motyw | Akt I | Akt II | Akt III | Akt IV | Akt V |
|---|---|---|---|---|---|
| Ciało w kosmosie | 3 | 3 | 4 | 2 | 1 |
| Maszyny i prawda | 4 | 4 | 3 | 2 | 1 |
| Trzeci Kwartał | 0 | 1 | 5 | 1 | 0 |
| Ziemia jako echo | 2 | 3 | 3 | 1 | 0 |
| Coś tam jest | 0 | 1 | 1 | 5 | 2 |
| Felix i ARIA | 1 | 2 | 2 | 1 | 0 |

*(Wyższe liczby = częstsze losowanie eventów tego motywu)*

---

## 8. BALANS SKILL CHECKÓW

### Rozkład trudności eventów per difficulty

| Difficulty | Opis | % eventów |
|---|---|---|
| 3 (rutynowe) | — | 10% |
| 6 (wymagające) | — | 45% |
| 9 (trudne) | — | 35% |
| 12 (krytyczne) | — | 8% |
| 15 (prawie niemożliwe) | — | 2% |

### Szanse sukcesu przy standardowych skillach

*(skill + d6, bez modyfikatorów stanu)*

| Difficulty | Skill 5 | Skill 7 | Skill 9 |
|---|---|---|---|
| 3 | 100% | 100% | 100% |
| 6 | 83% | 100% | 100% |
| 9 | 33% | 67% | 100% |
| 12 | 0% | 17% | 50% |
| 15 | 0% | 0% | 0% (blue check needed) |

**Wniosek:** Difficulty 9 to właściwy "trudny" check — ekspert (skill 9) zawsze przejdzie,
specjalista (skill 7) ma 67%, kapitan z podstawami (skill 5) ma 33%.
Difficulty 12 to "tylko ekspert" — i nawet ekspert przy złym stanie może polegać.

### Modyfikatory stanu — wpływ na szanse

Przy Health <60 (−1 modifier): szansa na difficulty 9 spada:
- Skill 7: 67% → 50%
- Skill 9: 100% → 83%

Przy Health <35 (−2 modifier) + Morale <30 (−2 modifier):
- Skill 9 na difficulty 9: 100% → 50%

*Gracz który zaniedbał stan załogi będzie przegrywał checki
które powinny być trywialne dla ekspertów.*

---

## 9. LIFEDATA — BALANS ODKRYCIA

Cel: dotarcie do Limes z wystarczającym LifeData żeby M14 Analiza była możliwa.

```
Wymagane LifeData dla zakończeń:

Zakończenie TRIUMF:     LifeData ≥ 75 + M14 full success
Zakończenie PYRRUSOWE:  LifeData ≥ 50 + M14 partial
Zakończenie CICHY POWRÓT: LifeData dowolne (brak odkrycia)

Jak zgromadzić LifeData ≥ 75 przy optymalnej grze:

M03 Obserwacja (co tura, 50 tur): +50 (50 × 1 średnio)
M07 Spektroskopia (1-2 tury):     +4-8
M10 Skanowanie atmosferyczne:     +3
M11 Mapowanie powierzchni:        +2
M12 Ekspedycja (sukces pełny):    +8
RAZEM MAKSYMALNE:                 ~77-83

Realistyczne (z przerwami, porażkami, event_false_biosignature):
                                  ~55-70

Stąd: LifeData ≥ 75 jest MOŻLIWE ale wymaga konsekwentnej pracy.
Gracz który pomijał obserwacje naukowe przez 30+ tur
nie dotrze do progu Triumfu — i to jest właściwe.
```

---

## 10. RZECZY DO PRZETESTOWANIA

Lista zagadnień wymagających weryfikacji w pierwszych sesjach playtestowych.

### Krytyczne (blokery przed MVP release)

- [ ] **Spirala ECLSS:** czy degradacja CO₂ przy braku konserwacji
  jest wystarczająco widoczna przed KG-02? Czy 2 tury ostrzeżenia to za mało?

- [ ] **PALIWO vs powrót:** czy typowy gracz ma wystarczające PALIWO na powrót
  po dotarciu do Limes? Cel: 40-60% gier powinno mieć powrót możliwy.

- [ ] **Trzeci Kwartał:** czy morale −3/turę + eventy w Akcie III
  nie jest zbyt punishing dla nowych graczy? Testować z Morale startowym −5 per postać.

- [ ] **Grzech bottleneck:** czy gracz który straci Grzecha w Akcie II
  może realnie dotrzeć do Limes? (Ma być trudne, nie niemożliwe.)

### Ważne (przed wyjściem z early access)

- [ ] **LifeData accumulation:** czy obserwacje naukowe nie są
  zbyt powolne? Cel: gracz który konsekwentnie robi M03 powinien mieć ~50 LifeData przy Akcie IV.

- [ ] **Relacje interpersonalne:** czy relacja +1 daje wystarczającą
  mechaniczną nagrodę żeby warta była inwestycji `Captain's Rounds`?

- [ ] **Głosy wewnętrzne:** czy wzrost jest zauważalny dla gracza?
  Czy różnica między SYGNAŁ 3 a SYGNAŁ 7 jest wyraźna narracyjnie?

- [ ] **AMARA jako single point of failure:** czy utrata Amary
  jest właściwie widoczna w konsekwencjach? (Cel: poważna, ale gra kontynuowana.)

### Do obserwacji (post-launch)

- [ ] Średni poziom LifeData graczy przy Akcie IV.
- [ ] % graczy którzy zdobywają zakończenie TRIUMF vs reszta.
- [ ] Które eventy są najczęściej "wymuszającymi reload" (pomimo permadeath).
- [ ] Czy event `last_dinner` jest zauważany jako kulminacja czy niespodzianka.

---

## 11. ZNANE RYZYKA BALANSU

| Ryzyko | Opis | Mitygacja |
|---|---|---|
| **Grzech bottleneck** | Jeden specjalista dla wszystkich napraw | Trait *Śląski sposób* + inni mogą robić naprawy difficulty ≤6 |
| **PALIWO zbyt ciasne** | Gracz zostaje zbyt często z konieczności | Zwiększyć start do 110 jeśli testy potwierdzą problem |
| **Morale spiral** | Akt III zbyt punishing jeśli zbiegnie się z technicznym kryzysem | Amara ma recovery; `Captain's Rounds` zawsze dostępne |
| **LifeData easy mode** | Yuki robi M03 każdą turą i ma 90 LifeData przed Limes | Sensory degradują — M03 wymaga Sensory >50%. Przy degradacji senory blokują |
| **False biosignature trap** | Gracz celebruje, dostaje `false_biosignature`, −25 Morale Yuki | To jest celowe napięcie, nie bug. Ale: sprawdzić czy nie demotywuje do dalszej gry |
| **Torpor paradoks** | Każda osoba w torpor jest niedostępna dla eventów | Standardowe 2 aktywne osoby powinny wystarczyć. Alert jeśli event wymaga >3 osób |

---

## 12. DOCELOWE ODCZUCIE PER TURA

| Moment | Jak powinno się czuć |
|---|---|
| Tura 1 (Day 1) | Czyste, pełne możliwości. Troché nieswojnie. |
| Tura 20 (Akt II) | Rutyna. Systemy lekko degradują. „OK, wiem co robię." |
| Tura 50 (środek Aktu II) | Ziemia jest opóźniona o miesiące. „Lecę." |
| Tura 88 (Akt III start) | Coś się zmienia. Grzech milczał przez kolację. |
| Tura 100 (Third Quarter) | Napięcie. Każda decyzja kosztuje więcej niż powinna. |
| Tura 130 (Akt III koniec) | Przetrwaliśmy. Ale nie wszyscy są tacy jak byli. |
| Tura 140 (Akt IV) | Limes rośnie w sensorach. Yuki nie śpi. |
| Tura 157 (M14) | Odpowiedź. Po pięćdziesięciu latach latania — jest odpowiedź. |
| Tura 174 (zakończenie) | Cokolwiek to jest. To jest konsekwencja. |

---

## Balancing update — v1.0

**Ukończono:**
- Pełne wartości startowe zasobów, systemów i załogi
- Budżety PALIWO i CZĘŚCI z obliczeniami
- Krzywa trudności per akt z projektowanymi stanami na końcu każdego aktu
- Kluczowe liczby NASA jako referencyjna tabela
- Prawdopodobieństwa eventów per akt i motyw
- Statystyki sukcesu skill checków
- Balans LifeData i ścieżki odkrycia
- Lista rzeczy do przetestowania (priorytetyzowana)
- Znane ryzyka z mitigacją
