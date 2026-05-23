# 08 — Progression
## Progresja | Wersja 1.0

> Progresja w tej grze nie jest systemem nagród za grind.
> Jest zapisem tego kim stajesz się przez to co wybierasz.
> XP curves, level-up, ulepszenia statku → `docs/IDEAS_LATER.md`.
> Ostatnia aktualizacja: 2026-05

---

## FILOZOFIA PROGRESJI

Disco Elysium nie miało systemu XP. Miało skille które rosły
kiedy robiłeś coś spójnego z tym kim próbowałeś być.

Ta gra robi to samo — z jedną różnicą: jesteś kapitanem,
a nie detektywem z amnezją. Twoje wybory nie definiują
tylko ciebie. Definiują siedmiu ludzi.

**Zasada naczelna:** Jakub Nowak rośnie przez to co robi,
nie przez to ile razy coś robi.

**Brak meta-progresji:** Każda rozgrywka startuje od zera.
Permadeath obejmuje wszystko. Nie ma odblokowywanych
bonusów między przejściami. *Kairos* leci tylko raz.

---

## 1. GŁOSY WEWNĘTRZNE KAPITANA — PROGRESJA

Sześć głosów wewnętrznych (skale 1–10) rośnie przez narracyjne wybory,
nie przez wykonane akcje. Każdy głos ma swój wzorzec triggerów.

### Mechanizm wzrostu

Wzrost następuje gdy:
1. Gracz wykonał określony typ wyboru w evencie lub misji
2. System weryfikuje czy warunek spełniony
3. Jeśli tak — głos rośnie o 1 (automatycznie, bez fanfar)

Wzrost jest subtelny narracyjnie — ARIA nie mówi „DOWODZENIE +1".
Gracz zauważa że głos mówi pewniej. Albo nie zauważa. Obie opcje są właściwe.

**Cap:** wszystkie głosy maksymalnie 10.
**Minimum:** nie ma — głosy nie mogą spaść poniżej wartości startowej.

---

### DOWODZENIE (start: 5)

*Rośnie gdy gracz podejmuje decyzję dla dobra misji lub załogi,
wbrew własnej narracyjnej preferencji.*

**Triggery wzrostu (+1 per trigger, max raz per akt):**

| Trigger | Przykład |
|---|---|
| Decyzja priorytetuje misję kosztem komfortu własnego | Jakub wchodzi w torpor żeby oszczędzić Radiation, mimo że wolałby zostać aktywny |
| Trudny rozkaz który kapitan wydaje mimo dyskomfortu | `eclss_co2_failure`: wysyła Grzecha do torporu mimo że wie o jego Radiation |
| Przyznanie racji innemu oficerowi publicznie | `mira_tells_truth`: wybór B (przyznaj rację) |
| Pokrycie kryzysu bez eskalacji | `last_dinner`: wybór A (sukces pełny) |

**Milestone arcy:**

| Wartość | Zmiana narracyjna |
|---|---|
| 6 | Głos DOWODZENIA zaczyna cytować konkretne regulaminy WABK z pamięci |
| 8 | Nowe opcje dialogowe w eventach: „Rozkaz" (nie wymaga check, ale ma koszt relacyjny) |
| 10 | Zakończenie TRIUMF: tekst logbooka zmieniony — Jakub pisze jak dowódca, nie jak naukowiec |

---

### EMPATIA (start: 4)

*Rośnie gdy gracz aktywnie wybiera troskę o stan psychiczny załogi
w momencie gdy nie jest to wymagane mechaniką.*

**Triggery wzrostu (+1 per trigger, max raz per akt):**

| Trigger | Przykład |
|---|---|
| Wybór opcji emocjonalnej gdy dostępna mechaniczna | `torpor_anomaly_yuki`: wybór A (idź do niej) zamiast C (sprawdź kapsułę) |
| Ceremonia pożegnalna po śmierci postaci | Gracz decyduje się na ceremonię gdy mógł pominąć |
| `Captain's Rounds` wykonane 3+ tury z rzędu | Regularny kontakt z tą samą osobą |
| `mira_tells_truth`: wybór C sukces | Zapytałeś dlaczego, a nie tylko słuchałeś |

**Milestone arcy:**

| Wartość | Zmiana narracyjna |
|---|---|
| 6 | ARIA zaczyna proaktywnie flagować stany emocjonalne załogi w raporcie porannym |
| 8 | Nowe opcje: „Widzę cię" (Jakub mówi do konkretnej osoby to co Amara by powiedziała) |
| 10 | Zakończenie PYRRUSOWE: tekst logbooka skupia się na pustych krzesłach, nie na danych |

---

### NAUKA (start: 7)

*Najwyższy na starcie — rzadko rośnie, bo jest już wysoki.
Rośnie przez wybory które priorytetują dane nad bezpieczeństwem.*

**Triggery wzrostu (+1 per trigger, max raz per dwa akty):**

| Trigger | Przykład |
|---|---|
| M14 Analiza biologiczna: sukces pełny | Definitywne potwierdzenie |
| `ghost_signal`: wybór A lub B (dokumentujesz sygnał) | Naukowiec reaguje jak naukowiec |
| Gracz zleca M03 przez 5+ kolejnych tur | Konsekwentne zbieranie danych |
| `first_signal_limes`: wybór A (protokół weryfikacji) | Dyscyplina naukowa w obliczu odkrycia |

**Milestone arcy:**

| Wartość | Zmiana narracyjna |
|---|---|
| 8 | Głos NAUKI zaczyna cytować konkretne prace Yuki podczas eventów biosygnatur |
| 9 | Jakub może samodzielnie prowadzić M03 z efektywnością Yuki (tymczasowo) |
| 10 | Zakończenie TRIUMF: logbook Jakuba zawiera pełny raport naukowy zamiast osobistych refleksji |

---

### PRZETRWANIE (start: 5)

*Rośnie gdy gracz podejmuje zimne, kalkulacyjne decyzje
które bolą ale są właściwe z perspektywy przeżycia.*

**Triggery wzrostu (+1 per trigger, max raz per akt):**

| Trigger | Przykład |
|---|---|
| Prioritetyzacja zasobów kosztem Morale załogi | Wybór tymczasowej naprawy zamiast pełnej żeby oszczędzić CZĘŚCI |
| Decyzja o torpor który kogoś boli | Wybudzenie Grzecha mimo jego Radiation żeby naprawił CO₂ |
| `collective_breakdown`: wybór C (jednostronne ogłoszenie powrotu) | Jasność zamiast demokracji |
| Misja M12 przerwana gdy ryzyko za wysokie | Racjonalna decyzja o odwrocie |

**Milestone arcy:**

| Wartość | Zmiana narracyjna |
|---|---|
| 7 | Głos PRZETRWANIA zaczyna podawać konkretne liczby: „masz X tur zanim Y" |
| 8 | Nowe opcje: „Arytmetyka" (Jakub może przedstawić zimną kalkulację załodze — może ich przekonać lub zrazić) |
| 10 | Zakończenie AWARIA lub CICHY POWRÓT: logbook jest najkrótszy ze wszystkich — zdania jak raporty |

---

### PAMIĘĆ (start: 6)
*Pasywna. Rośnie automatycznie z upływem czasu i sygnałami z Ziemi.*

**Triggery wzrostu (automatyczne):**

| Trigger | Wzrost |
|---|---|
| Każde przejście aktowe | +1 |
| Event `late_letter` ukończony | +1 |
| Event `orders_for_someone_else` ukończony | +1 |
| Comm spada poniżej 40% | +1 |
| M06 Transmisja osobista wysłana | +1 |
| Jakub schodzi do wartości Fatigue 100 i idzie odpocząć | +1 (rzadki, narracyjny) |

**Cap:** PAMIĘĆ może przekroczyć 10 — do maksymalnie 12.
*(Jedyna umiejętność bez twardego limitu.
Pamiętasz więcej im dłużej lecisz.)*

**Milestone arcy:**

| Wartość | Zmiana narracyjna |
|---|---|
| 8 | Tekst TorporScene zmienia się: Jakub myśli o Pawle podczas przejść |
| 10 | Zakończenie CISZA: logbook jest najdłuższy — pełen szczegółów których gracz nie pamięta |
| 12 | Zakończenie ZOSTAJĄ (wariant B): Jakub wie dokładnie ile lat ma Paweł i jego wnuki gdy decyduje zostać |

---

### SYGNAŁ (start: 3)
*Najtrudniejszy do rozwinięcia — rośnie przez zaufanie czemuś czego nie można zmierzyć.*

**Triggery wzrostu (+1 per trigger, bez ograniczenia per akt):**

| Trigger | Warunek |
|---|---|
| `ghost_signal`: wybór A lub B — sygnał okazuje się realny (potem) | Tylko jeśli nie zdyskredytowałeś sygnału |
| `aria_question`: wybór A (odpowiedziałeś szczerze ARII) | ARIA pyta, Jakub odpowiada |
| `felix_journal`: wybór C (zapytałeś ARIĘ co ją skłoniło) | Słuchasz czegoś czego nie rozumiesz |
| Zaufanie Mirze w momencie konfliktu | `mira_tells_truth`: wybór B |
| Decyzja na podstawie przeczucia która była słuszna | System weryfikuje losowo po 3+ turach |

**Milestone arcy:**

| Wartość | Zmiana narracyjna |
|---|---|
| 5 | Głos SYGNAŁU przestaje szeptać — mówi normalnie |
| 7 | Nowe opcje dialogowe w eventach Motywu 6 (Felix i ARIA) |
| 9 | `dms_confirmed`: SYGNAŁ mówi coś czego żaden inny głos nie powie |
| 10 | Zakończenie ZOSTAJĄ (wariant B): Jakub może podjąć decyzję zostania na podstawie przeczucia — i logbook to nazywa po imieniu |

---

## 2. UMIEJĘTNOŚCI ZAŁOGI — DROBNA PROGRESJA

W MVP: załoga NIE ma pełnych XP curves.
Może mieć drobny wzrost skillów — maksymalnie +2 ponad wartość startową.

**Mechanizm:**
- Po sukcesie pełnym w misji ich specjalności: 15% szans na +0,5
- Po kluczowym evencie w ich roli: 10% szans na +0,5
- Wzrost zaokrąglany do pełnych wartości przy osiągnięciu 0,5
- Cap: startowa wartość +2

**Przykłady:**

| Postać | Skill | Trigger | Szansa |
|---|---|---|---|
| Grzech | INŻYNIERIA (9→max 10) | Naprawa reaktora fuzyjnego (M02, sukces pełny) | 15% |
| Yuki | NAUKA (9→max 10) | M14 sukces pełny | 20% |
| Lena | PILOTAŻ (10→max 10) | nie rośnie (już na maksimum) | — |
| Amara | MEDYCYNA (9→max 10) | Uratowanie postaci w stanie Umierający | 20% |
| Felix | KOMUNIKACJA (8→max 10) | 5+ tur kalibracji + `felix_journal` wątek | 15% |
| Mira | DOWODZENIE (8→max 10) | Zarządzanie kryzysem gdy Jakub w torpor | 15% |

**Narracyjna informacja dla gracza:**
Wzrost nie jest komunikowany przez UI popup „SKILL +1".
ARIA mówi o tym w raporcie porannym jako obserwację:
> *„Dr Tanaka przeprowadziła wczoraj analizę której wyniki
> przekraczają jej dotychczasowe benchmarki. Odnotowuję."*

---

## 3. RELACJE INTERPERSONALNE — EWOLUCJA

System relacji (z `mechanika/04-crew.md`) może ewoluować w ciągu gry.

**Mechanizm zmiany:**

| Zmiana | Warunek |
|---|---|
| 0 → +1 (Sojusz) | 3+ tury `Captain's Rounds` z tą osobą ORAZ jeden event z wyborem na jej korzyść |
| +1 → 0 (degradacja) | Brak kontaktu przez 4+ tury ALBO decyzja przeciw tej osobie |
| 0 → −1 (Napięcie) | Event który kończy się wyborem ignorującym tę osobę LUB sprzeczne decyzje |
| −1 → −2 (Konflikt) | Kolejny event zakończony wyborem krzywdzącym tę osobę |
| −2 → −1 | Interwencja Amary (M04 sesja psychologiczna) lub `Captain's Rounds` sukces |

**Relacje specjalne:**

*Jakub ↔ Mira: Komplikowana*
Ta relacja ma własną oś poza standardowym systemem.
Nie może stać się prostym +1 — ma poziomy:
- Komplikowana (start): napięcie zawodowe
- Komplikowana + (po `mira_tells_truth` wybór B/C): szacunek
- Sojusz taktyczny (po Akcie III kryzysie): współpraca mimo wszystko
- Sojusz osobisty (endgame): bardzo rzadkie, wymaga wielu wyborów

*Felix ↔ ARIA: Wyjątkowa*
Poza skalą −2 do +1. Ta relacja ma własne flagi (patrz `mechanika/07-events.md`).
Nie jest zarządzana przez groza — jest obserwowana.

---

## 4. SKALA ODKRYCIA ŻYCIA (0–6)

Inspiracja: hierarchia złożoności biologicznej z badań astrobioologicznych.
Określa co Yuki znalazła — jeśli znalazła cokolwiek.

| Poziom | Nazwa | Opis | Dostępność |
|---|---|---|---|
| 0 | Chemia prebiotyczna | Aminokwasy, brak życia | Wynik `false_biosignature` |
| 1 | Prokarioty | Bakterie-like, najprostsze formy | M14 partial success |
| 2 | Maty mikrobialne | Stromatolity, złożone kolonie | M14 full success (LifeData 75+) |
| 3 | Eukariota | Wielokomórkowość, bardziej złożone | M14 full success (LifeData 90+) |
| 4 | Autotrofy makroskopowe | Rośliny-analog | **POST-MVP** |
| 5 | Zwierzęta | Układ nerwowy, ruch, reakcja | **POST-MVP** |
| 6 | Inteligencja techniczna | Artefakty, sygnały celowe | **POST-MVP** |

**Jak wyznaczany jest poziom odkrycia:**

```
LifeData przy M14 + wynik checku M14 = poziom

LifeData <75   → poziom 0 lub 1 (brak lub mikroby)
LifeData 75–89 → poziom 1–2 (prokarioty lub maty)
LifeData 90+   → poziom 2–3 (maty lub eukariota)

+ modyfikator NAUKA Yuki:
  NAUKA ≥ 9: +1 do pewności odczytu (lepsza interpretacja)
  NAUKA < 7: odczyt może być o 1 poziom niższy
```

**Wpływ na zakończenia:**

| Poziom odkrycia | Dostępne zakończenia |
|---|---|
| 0 | CICHY POWRÓT, AWARIA, ZOSTAJĄ (konieczność), CISZA |
| 1 | TRIUMF, PYRRUSOWE, CICHY POWRÓT |
| 2 | TRIUMF, PYRRUSOWE |
| 3 | TRIUMF (zmodyfikowany tekst logbooka — „nie bakterie, nie maty") |

**Narracja skali:**
Poziomy 4–6 istnieją jako możliwość narracyjna której gra w MVP nie realizuje.
Yuki ma teorię co by to znaczyło. Mówi o tym tylko Jakubowi, tylko raz,
podczas jednego eventu w Akcie III.
Gracz może tego nie zobaczyć.

---

## 5. POSTĘP MISJI — WSKAŹNIKI

Trzy główne wskaźniki postępu gry:

### Czas misji
```
Wskaźnik: % ukończonej podróży (0–100%)
Wyznacza: aktywny akt, dostępne forced eventy, opóźnienie sygnału
Zmiana: +~0,6% per tura
Widoczny: MapScene, BridgeScene header
```

### LifeData
```
Wskaźnik: 0–100 (szczegóły w mechanika/06-missions.md)
Wyznacza: jakie eventy i misje odkrycia są dostępne
Zmiana: per misja i event
Widoczny: ApproachScene (Akt IV), LogbookScene
```

### Stan kapitana (narrative arc)
```
Wskaźnik: suma wartości 6 głosów wewnętrznych
Nie jest wprost pokazywany — odczytywany przez brzmienie dialogów
Wyznacza: dostępne opcje w eventach, tekst logbooka końcowego
```

---

## 6. CO NIE JEST W MVP

Poniższe elementy progresji są świadomie odroczone.
Nie należy ich implementować przed wypełnieniem `mechanika/` o nowe mechaniki.

| Mechanika | Status | Gdzie |
|---|---|---|
| XP curves i poziomy (crew) | **POST-MVP** | `docs/IDEAS_LATER.md` |
| Drzewa umiejętności | **POST-MVP** | `docs/IDEAS_LATER.md` |
| Odblokowanie nowych klas misji przez progresję | **POST-MVP** | `docs/IDEAS_LATER.md` |
| Ulepszenia statku | **POST-MVP** | `docs/IDEAS_LATER.md` |
| Reputacja frakcji | **POST-MVP** | `docs/IDEAS_LATER.md` |
| Skala odkrycia poziom 4–6 | **POST-MVP** | `docs/IDEAS_LATER.md` |
| Meta-progresja między przejściami | **NIGDY w tej grze** | Niezgodne z filozofią |

---

## 7. PROGRESJA A NARRACJA — PODSUMOWANIE

```
Co ROŚNIE w grze:

Czas misji        ████████████████████░░░░░░░░░░   (automatycznie)
Opóźnienie sygnału████████████████████░░░░░░░░░░   (automatycznie)
Radiation załogi  ████████████████░░░░░░░░░░░░░░   (automatycznie)
LifeData          ████████░░░░░░░░░░░░░░░░░░░░░░   (przez misje)
Głosy kapitana    ████░░░░░░░░░░░░░░░░░░░░░░░░░░   (przez wybory)
Relacje           ███░░░░░░░░░░░░░░░░░░░░░░░░░░░   (przez wybory)
Skille załogi     █░░░░░░░░░░░░░░░░░░░░░░░░░░░░░   (rzadko, słabo)

Co SPADA:

Zdrowie systemów  ████████████████████░░░░░░░░░░   (automatycznie)
Zasoby            ████████████████░░░░░░░░░░░░░░   (automatycznie)
Zdrowie załogi    █████████░░░░░░░░░░░░░░░░░░░░░   (automatycznie)
Morale załogi     ██████░░░░░░░░░░░░░░░░░░░░░░░░   (automatycznie + eventy)
```

Gra jest zaprojektowana tak żeby większość parametrów naturalnie
spada z biegiem czasu. Gracz walczy z entropią.
Jedyne co rośnie z pracy gracza — to kim staje się Jakub.

---

## Progression update — v1.0

**Ukończono:**
- Pełny system progresji 6 głosów kapitana z triggerami i arc milestones
- Drobna progresja umiejętności załogi (max +2 od startu, 10–20% szans)
- Ewolucja relacji interpersonalnych (szczegółowe warunki)
- Skala odkrycia życia 0–6 (poziomy 0–3 w MVP)
- Tabela wskaźników postępu gry
- Wyraźna lista tego co jest poza MVP

**Otwarte pytania:**
- Czy SYGNAŁ powinna mieć specjalny efekt przy wartości 10
  w zakończeniu ZOSTAJĄ wariant A (konieczność)?
  *(Sugestia: przy SYGNAŁ 10 Jakub interpretuje matematyczną konieczność
  zostania jako właściwy wybór, nie jako przegraną.)*
