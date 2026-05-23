# 03 — Resources
## Mechanika Zasobów i ECLSS | Wersja 1.0

> Wszystkie wartości przepływu zasobów mają uzasadnienie w danych NASA/ESA.
> Zasoby to co *masz*. ECLSS to co determinuje *jak szybko to tracisz lub zyskujesz*.
> Części zamienne to meta-zasób który pozwala naprawiać ECLSS.
> Ostatnia aktualizacja: 2026-05

---

## ZASADA NACZELNA

Każdy zasób musi mieć:
- **źródło** (jak go zdobyć lub produkować)
- **odpływ** (jak go tracisz)
- **konsekwencję niedoboru** (co się dzieje przy niskim poziomie i przy 0)

Zasób bez odpływu to dekoracja. Zasób bez konsekwencji to liczba bez znaczenia.

---

## 1. ARCHITEKTURA SYSTEMU ZASOBÓW

```
EKLSS (Systemy Podtrzymywania Życia)
         │
         ▼
   ZDROWIE SYSTEMÓW (0–100%)
         │
         ▼
   PRZEPŁYW ZASOBÓW
   ┌─────┴─────┐
   ▼           ▼
ZASOBY      ZASOBY
ŻYCIOWE     OPERACYJNE
(TLEN,       (PALIWO,
 WODA,        CZĘŚCI)
 ŻYWNOŚĆ)
```

**Zasoby życiowe** — produkowane przez ECLSS, konsumowane przez aktywną załogę.
Degradacja systemów ECLSS bezpośrednio wpływa na przepływ.

**Zasoby operacyjne** — skończone. Nie produkujesz ich na statku.
Każda wydana jednostka to decyzja której nie cofniesz.

---

## 2. ZASOBY ŻYCIOWE

### 2.1 TLEN (Oxygen)

**Skala:** 0–100 jednostek *(1 jednostka ≈ jeden dzień tlenu dla pełnej aktywnej załogi)*
**Jednostka realna:** procent normy ECLSS; 100 = zapas bezpieczny na 100 dni

**Dane źródłowe:** ECLSS NASA 2023 — odzysk O₂ z reakcji Sabatiera: **93%**
Elektroliza wody → H₂O → O₂ + H₂. Wodór trafia z powrotem do Sabatiera.
Netto utrata tlenu: **7% na cykl aktywności** — uzupełniany z rezerw lub produkcji.

**Przepływ per tura** *(1 tura = 1 rotacja = ~4 miesiące: 30 dni aktywnych + 90 dni torporu)*:

| Warunek | Zmiana TLEN |
|---|---|
| 2 osoby aktywne, ECLSS 100% | −0,4 jednostki |
| 2 osoby aktywne, ECLSS 50% | −2,0 jednostki |
| 2 osoby aktywne, ECLSS 0% | −6,0 jednostki (śmiertelne w 2 tury) |
| Solar flare (zdarzenie) | −5 do −15 jednorazowo |
| Naprawa ECLSS-Sabatier | +1,5 do +3,0 (po naprawie) |

**Wartość startowa:** 80 jednostek
*(Misja startuje z niepełnymi rezerwami — system ECLSS ma produkować na bieżąco)*

| Próg | Stan | Efekt |
|---|---|---|
| 50–100 | Normalny | Brak efektów |
| 25–49 | Niski | Zdarzenie narracyjne; ARIA informuje o niedoborze |
| 15–24 | Ostrzeżenie | Health aktywnej załogi: −3 pkt/turę |
| 5–14 | Krytyczny | Health aktywnej załogi: −8 pkt/turę; Morale: −10 |
| 1–4 | Śmiertelny | Health: −20 pkt/dzień; bez interwencji — śmierć w 3 doby |
| 0 | **KONIEC GRY** | Cała aktywna załoga umiera w ciągu doby |

> *„ECLSS-CO₂: przy 0% sprawności, poziom CO₂ osiąga granicę śmiertelną
> w 6–12 godzin. To nie metafora."*
> — Dr Amara Nwosu, prywatny log, cykl 14.

---

### 2.2 WODA (Water)

**Skala:** 0–100 jednostek *(100 = pełne rezerwy na ~8 miesięcy bez recyklingu)*

**Dane źródłowe:** NASA Brine Processor Assembly 2023 — odzysk wody: **98%**
Pot, wydychane powietrze, mocz — wszystko trafia z powrotem do systemu.
Netto utrata wody: **2% na cykl aktywności** — marginalna, ale akumuluje się.

**Kaskada:** WODA napędza produkcję TLEN (elektroliza). Niski poziom WODA
automatycznie ogranicza produkcję TLEN.

**Przepływ per tura:**

| Warunek | Zmiana WODA |
|---|---|
| 2 osoby aktywne, WRS 100% | −0,12 jednostki |
| 2 osoby aktywne, WRS 50% | −1,2 jednostki |
| 2 osoby aktywne, WRS 0% | −6,0 jednostki (kryzys w 10–15 tur) |
| Awaria rurociągu (zdarzenie) | −5 do −20 jednorazowo |

**Wartość startowa:** 70 jednostek

| Próg | Stan | Efekt |
|---|---|---|
| 50–100 | Normalny | Brak efektów |
| 30–49 | Niski | Produkcja TLEN: −20%; zdarzenie narracyjne |
| 20–29 | Ostrzeżenie | Produkcja TLEN: −40%; Health: −2 pkt/turę |
| 10–19 | Krytyczny | Produkcja TLEN: −70%; Health: −5 pkt/turę; Morale: −8 |
| 1–9 | Śmiertelny | Produkcja TLEN: 0%; Health: −15 pkt/turę |
| 0 | **KONIEC GRY** | Bez wody produkcja O₂ zatrzymuje się; łańcuch prowadzi do śmierci |

> **Uwaga projektowa:** WODA rzadko osiąga 0 bezpośrednio — jej rola to
> ograniczanie produkcji TLEN, co czyni ją cichym multiplikatorem ryzyka.
> Gracz może nie zauważyć WODA=35 aż TLEN zacznie dramatycznie spadać.

---

### 2.3 ŻYWNOŚĆ (Food)

**Skala:** 0–100 jednostek *(1 jednostka = jeden dzień jedzenia dla jednej aktywnej osoby)*

**Dane źródłowe:** NASA Veggie + bioreaktory (Spirulina, drożdże):
- Hydroponika: 50% diety → ~3 jednostki/turę przy pełnej sprawności
- Bioreaktory: 30% diety → ~1,8 jednostki/turę przy pełnej sprawności
- Rezerwy liofilizowane: 20% diety → statyczny bufor, nie regeneruje się

**Przepływ per tura** *(przy 2 aktywnych osobach)*:

| Warunek | Zmiana ŻYWNOŚĆ |
|---|---|
| Hydroponika 100% + Bioreaktory 100% | +4,8 zdobyte − 4,0 zużyte = **+0,8** |
| Hydroponika 50% + Bioreaktory 100% | +3,3 − 4,0 = **−0,7** |
| Hydroponika 0% + Bioreaktory 100% | +1,8 − 4,0 = **−2,2** |
| Oba systemy 0% | 0 produkowane − 4,0 zużyte = **−4,0** (rezerwy tylko) |

**Wartość startowa:** 60 jednostek *(rezerwy liofilizowane; systemy produkcyjne startują)*

| Próg | Stan | Efekt |
|---|---|---|
| 40–100 | Normalny | Brak efektów |
| 20–39 | Niski | Morale: −3/turę dla aktywnej załogi; zdarzenie narracyjne |
| 10–19 | Ostrzeżenie | Morale: −8/turę; Health: −3/turę |
| 3–9 | Krytyczny | Morale: −15/turę; Health: −8/turę |
| 0 | **Głód** | Health: −20/turę; po 3 turach bez jedzenia: stan Krytyczny |

> **Uwaga narracyjna:** Yuki hoduje *Arabidopsis thaliana* w swojej kajucie.
> To nie jest żywność — ale gdy hydroponika spada poniżej 30%,
> pojawia się zdarzenie: Yuki może oddać swoje rośliny do systemu.
> Zysk ŻYWNOŚĆ: +2. Koszt: Morale Yuki −15 i scena której się nie zapomina.

---

## 3. ZASOBY OPERACYJNE

### 3.1 PALIWO FUZYJNE (Fusion Fuel)

**Skala:** 0–100 jednostek *(100 = pełny załadunek startowy mieszaniny D/³He)*

**Dane źródłowe:** Koncepcja Daedalus/Icarus — napęd fuzji termojądrowej,
masa paliwa: 50 000 ton D/³He (zmodyfikowane dla skali tej gry do jednostek abstrakcyjnych).

**Ważna zasada:** Paliwo NIE jest zużywane podczas rejsu pasywnego.
Statek cruisuje na istniejącej prędkości. Paliwo jest wydawane na:
- Korekty kursu (małe manewry)
- Uniki przed zagrożeniami (zdarzenia)
- Deceleration burn (faza docelowa)
- Powrotny kurs (po misji)

**Konsumpcja per zdarzenie/decyzja:**

| Manewr | Koszt PALIWO |
|---|---|
| Korekta kursu (rutynowa) | −1 |
| Unik przed obiektem (zdarzenie) | −2 do −4 |
| Emergency burn (kryzys) | −5 do −8 |
| Deceleration burn (start fazy IV) | −15 *(automatyczny, nie opcjonalny)* |
| Acceleration burn (powrót) | −15 *(automatyczny, nie opcjonalny)* |

**Wartość startowa:** 100 jednostek

**Rezerwy krytyczne:**

| Próg | Stan | Efekt |
|---|---|---|
| 65–100 | Normalny | Wszystkie manewry dostępne |
| 40–64 | Ostrożność | Zdarzenie narracyjne; ARIA informuje o bilansie |
| 35 | **Punkt powrotu** | Minimum żeby wrócić na Ziemię. Poniżej — bez gwarancji powrotu. |
| 20–34 | Krytyczny | Tylko life-critical manewry; powrót niemożliwy lub ryzykowny |
| 10–19 | Ostatnia rezerwa | Deceleration przy Limes niemożliwy lub tylko częściowy |
| <10 | Dryf | Statek traci zdolność manewrową. Trajektoria niekontrolowana. |
| 0 | **KONIEC GRY** | Dryf bez kontroli — specjalne zakończenie narracyjne |

> **Uwaga projektowa:** PALIWO to zasób decyzji, nie czasu.
> Gracz może skończyć misję ze 40 jednostkami lub z 15.
> Różnica: zakończenie „Triumf" vs zakończenie „Zostają" lub „Cisza".

---

### 3.2 CZĘŚCI ZAMIENNE (Spare Parts)

**Skala:** 0–100 jednostek *(abstrakacja — obejmuje: elektronika, moduły mechaniczne, uszczelnienia, materiały)*

**Dane źródłowe:** Szacunki inżynieryjne misji długodystansowych —
do 50% masy statku to zapas części zamiennych i materiałów naprawczych.
*Kairos* startuje z 75 jednostkami (25% zostało zużyte przy pre-launch).

**Brak produkcji:** Części zamienne nie regenerują się.
Drukarki 3D na statku pozwalają na naprawy elementarne,
ale nie zastąpią skomplikowanych modułów.
*(Realistyczne ograniczenie — pełne self-manufacturing to nie 2099.)*

**Koszt napraw per system:**

| System | Naprawa pełna | Naprawa tymczasowa (do 50%) |
|---|---|---|
| CO₂ Scrubber | 8 CZĘŚCI | 4 CZĘŚCI |
| Reaktor Sabatiera | 12 CZĘŚCI | 6 CZĘŚCI |
| Water Recovery System (WRS) | 10 CZĘŚCI | 5 CZĘŚCI |
| Hydroponika | 6 CZĘŚCI | 3 CZĘŚCI |
| Bioreaktory | 5 CZĘŚCI | 2 CZĘŚCI |
| Kapsuła torporu (1 szt.) | 8 CZĘŚCI | 4 CZĘŚCI |
| Sensory zewnętrzne | 7 CZĘŚCI | 4 CZĘŚCI |
| Reaktor fuzyjny | 20 CZĘŚCI | 10 CZĘŚCI |
| Laboratorium naukowe | 9 CZĘŚCI | 5 CZĘŚCI |
| Komunikacja | 6 CZĘŚCI | 3 CZĘŚCI |

**Wartość startowa:** 75 jednostek

| Próg | Stan | Efekt |
|---|---|---|
| 50–100 | Normalny | Wszystkie naprawy dostępne |
| 25–49 | Ostrożność | Grzech komentuje niedobór; strategiczne decyzje |
| 10–24 | Krytyczny | Tylko life-critical naprawy (ECLSS, kapsułki torporu) |
| 1–9 | Ostatnia rezerwa | Jedna, maksymalnie dwie naprawy zostały |
| 0 | **Brak napraw** | Uszkodzone systemy pozostają uszkodzone. Na zawsze. |

> *„Mam siedemnaście kamieni z miejsc gdzie pracowałem.
> Z każdego wyciągnąłem coś co nie miało działać — i działało.
> Tutaj nie ma sklepu. Pamiętaj o tym zanim zdecydujesz
> co jest priorytetem."*
> — Grzech, dzień 3 misji.

---

## 4. ECLSS — SYSTEMY PODTRZYMYWANIA ŻYCIA

ECLSS to nie zasób — to warstwa która determinuje przepływ zasobów.
Każdy system ma własne Zdrowie (0–100%) i wpływa na konkretne zasoby.

### 4.1 Mapa ECLSS

```
REAKTOR FUZYJNY (zasilanie)
        │
        ├──── CO₂ SKRUBER ──────────► usuwa CO₂ z powietrza
        │           │
        │           ▼
        ├──── REAKTOR SABATIERA ────► CO₂ + H₂ → CH₄ + H₂O (TLEN ↑, WODA ↑)
        │
        ├──── OGS (elektroliza) ────► H₂O → O₂ + H₂ (TLEN ↑)
        │
        ├──── WRS (odzysk wody) ────► pot/mocz/odd. → WODA ↑
        │
        ├──── HYDROPONIKA ──────────► ŻYWNOŚĆ ↑
        │
        └──── BIOREAKTORY ──────────► ŻYWNOŚĆ ↑
```

### 4.2 Profile systemów ECLSS

---

#### CO₂ SKRUBER
*Absorbery litowe + system regeneracji*

**Dane:** awaria = śmiertelne stężenie CO₂ w 6–12 godzin (>10 000 ppm)

| Sprawność | Efekt |
|---|---|
| 75–100% | CO₂ <2 000 ppm — bezpieczny poziom |
| 50–74% | CO₂ 2 000–4 000 ppm — Health: −1/turę aktywnej załogi |
| 25–49% | CO₂ 4 000–8 000 ppm — Health: −3/turę; Morale: −5/turę |
| 10–24% | CO₂ >8 000 ppm — Health: −8/turę; stan Ranny w 2 tury |
| 0% | CO₂ śmiertelny — **KONIEC GRY** jeśli brak naprawy w 1 turę |

**Koszt naprawy:** 8 CZĘŚCI (pełna) / 4 CZĘŚCI (tymczasowa do 50%)
**Kto naprawia:** Grzech (INŻYNIERIA check, difficulty 9)

---

#### REAKTOR SABATIERA
*Konwersja CO₂ + H₂ → CH₄ + H₂O*

**Dane:** odpowiada za 93% odzysku O₂; przy awarii utrata tlenu 7× szybsza

| Sprawność | Efekt na TLEN |
|---|---|
| 75–100% | Pełny odzysk O₂ (93%) |
| 50–74% | Odzysk 70% — TLEN spada szybciej (×2 baseline) |
| 25–49% | Odzysk 40% — TLEN spada 4× szybciej |
| 0% | Brak odzysku — TLEN spada 14× szybciej |

**Koszt naprawy:** 12 CZĘŚCI (pełna) / 6 CZĘŚCI (tymczasowa)
**Kto naprawia:** Grzech (INŻYNIERIA check, difficulty 9)

---

#### WATER RECOVERY SYSTEM (WRS)
*Recyrkulacja 98% wody z potu, oddechu, moczu*

**Dane:** NASA BPA 2023 — 98% recovery rate

| Sprawność | Efekt na WODA |
|---|---|
| 75–100% | Recyrkulacja 98% — WODA prawie stała |
| 50–74% | Recyrkulacja 75% — WODA −0,8/turę |
| 25–49% | Recyrkulacja 40% — WODA −2,5/turę |
| 0% | Brak recyrkulacji — WODA −6/turę; kryzys w ~12 tur |

**Koszt naprawy:** 10 CZĘŚCI (pełna) / 5 CZĘŚCI (tymczasowa)
**Kto naprawia:** Grzech (INŻYNIERIA check, difficulty 6)

---

#### HYDROPONIKA
*Sałata, kapusta, soja — NASA Veggie program*

**Dane:** 50% diety przy pełnej sprawności

| Sprawność | Produkcja ŻYWNOŚĆ/turę |
|---|---|
| 75–100% | +3,0 jednostki |
| 50–74% | +1,8 jednostki |
| 25–49% | +0,8 jednostki |
| 0% | +0 (wszystko martwe) |

**Specjalna interakcja:** Yuki może przeznaczać czas na opiekę nad hydroponią.
NAUKA check (difficulty 6) → +0,5 ŻYWNOŚĆ/turę; failure: brak efektu.
*(To jest dla niej coś więcej niż agronomia.)*

**Koszt naprawy:** 6 CZĘŚCI (pełna) / 3 CZĘŚCI (tymczasowa)
**Kto naprawia:** Grzech lub Yuki (INŻYNIERIA check, difficulty 6)

---

#### BIOREAKTORY
*Spirulina, drożdże, fermentacja — 30% diety*

| Sprawność | Produkcja ŻYWNOŚĆ/turę |
|---|---|
| 75–100% | +1,8 jednostki |
| 50–74% | +1,0 jednostki |
| 25–49% | +0,4 jednostki |
| 0% | +0 |

**Koszt naprawy:** 5 CZĘŚCI (pełna) / 2 CZĘŚCI (tymczasowa)
**Kto naprawia:** Grzech (INŻYNIERIA check, difficulty 6)

---

#### REAKTOR FUZYJNY
*Zasilanie całego statku*

**Uwaga:** Reaktor fuzyjny zasila WSZYSTKO. Przy niskiej sprawności
efektywność całego ECLSS spada proporcjonalnie.

| Sprawność | Efekt globalny |
|---|---|
| 75–100% | ECLSS pełna wydajność |
| 50–74% | ECLSS −15% wydajności; minor events narracyjne |
| 25–49% | ECLSS −40%; tylko life-critical systemy na pełnej mocy |
| 10–24% | ECLSS −75%; kryzys energetyczny; Paliwo: −2/turę (awaryjne zasilanie) |
| 0% | **KONIEC GRY** — wszystko gaśnie |

**Koszt naprawy:** 20 CZĘŚCI (pełna) / 10 CZĘŚCI (tymczasowa)
**Kto naprawia:** Grzech *(tylko Grzech — difficulty 12)*

> *„Reaktor fuzyjny to jedyna rzecz na tym statku której nie naprawię
> z zamkniętymi oczami. Reszta to hydraulika. Reaktor to inna klasa.
> Jeśli kiedyś zapytasz mnie jak długo mam — popatrz najpierw
> na reaktor."*
> — Grzech.

---

## 5. DEGRADACJA SYSTEMÓW — PASYWNA

Systemy ECLSS degradują pasywnie nawet bez zdarzeń.
*Kairos* będzie stary zanim dotrze do celu.

**Pasywna degradacja per tura (rotacja ~4 miesiące):**

| System | Degradacja / turę | Uzasadnienie |
|---|---|---|
| CO₂ Skruber | −1% | Zużycie absorbentów litowych |
| Reaktor Sabatiera | −0,5% | Katalityczna degradacja |
| WRS | −0,8% | Biofouling (osady biologiczne w filtrach) |
| Hydroponika | −1,5% | Zużycie nawozów, oświetlenia UV |
| Bioreaktory | −1,0% | Mutacja szczepów, zużycie mediów |
| Reaktor fuzyjny | −0,2% | Zmęczenie materiałowe |

> **Konsekwencja:** bez regularnych przeglądów (INŻYNIERIA check, difficulty 6,
> koszt 0 CZĘŚCI) systemy degradują się do ~50% sprawności po ~30 turach.
> Grzech musi pracować żeby statek żył. To nie jest mechanika w tle —
> to jest jego rola na pokładzie.

---

## 6. DANE NAUKOWE — LIFEDATA *(reserved, post-MVP)*

**Koncepcja:** Dane zbierane przez sensory statku i laboratoria
podczas zbliżania do Limes. Ograniczone pasmem transmisji do Ziemi.

| Zasób | Opis |
|---|---|
| Pojemność zbierania | Sensory + Lab zdrowie × czas |
| Limit transmisji do Ziemi | Maleje z odległością (laser optyczny) |
| Efekt na zakończenia | Wysoki LifeData = pełna dokumentacja odkrycia |

> Status: **zarezerwowane do Aktu IV i V**. Nie implementować przed `mechanika/06-missions.md`.

---

## 7. BILANS ZASOBÓW — WARTOŚCI STARTOWE

| Zasób | Start | Minimum bezpieczne | Punkt krytyczny | Koniec gry |
|---|---|---|---|---|
| TLEN | 80 | 25 | 15 | 0 |
| WODA | 70 | 30 | 20 | 0 |
| ŻYWNOŚĆ | 60 | 20 | 10 | 0 (po 3 turach) |
| PALIWO | 100 | 35 *(powrót)* | 20 | 0 / dryf |
| CZĘŚCI | 75 | 25 | 10 | 0 *(brak napraw)* |

---

## 8. INTERAKCJE MIĘDZY ZASOBAMI — MAPA KASKAD

```
Niska WODA
    │
    ▼
Mniejsza produkcja TLEN (OGS)
    │
    ▼
Szybszy spadek TLEN
    │
    ▼
Health aktywnej załogi spada
    │
    ▼
Morale spada (załoga wie co się dzieje)
    │
    ▼
Skill checki gorzej (modyfikatory stanu)
    │
    ▼
Naprawy trudniejsze do wykonania
    │
    ▼
ECLSS degraduje szybciej
    │
    └────────────────────► pętla zamknięta
```

**Zasada projektowa:** gracze mogą wpaść w spiralę degradacji
jeśli ignorują wczesne sygnały ostrzegawcze. ARIA informuje o progach —
ale gracz musi zdecydować co naprawić jako pierwsze.

---

## 9. ROLA GRZECHA — KOMENTARZ NARRACYJNY

Grzech jest sercem systemu zasobów. Bez niego ECLSS degraduje,
części się nie zużywają efektywnie, naprawy trwają dłużej lub nie dochodzą do skutku.

**Mechanicznie:**
- Tylko Grzech naprawia Reaktor Fuzyjny
- Grzech ma Trait *Śląski sposób* — nieudany check INŻYNIERIA nigdy nie jest pełną porażką
- Przy Morale Grzecha <30: automatycznie odmawia niebezpiecznych napraw
  *(to jest sygnał fabularny — gdy Grzech odmawia, coś jest bardzo nie tak)*

**Narracyjnie:**
Grzech zbiera kamienie. Kairos będzie osiemnastym.
Jeśli Grzech umrze — tego kamienia nikt nie zbierze.
I statek bez kogoś kto go kocha jako maszynę, psuje się szybciej.

---

## 10. KOMENTARZ PROJEKTOWY — CO NIE JEST TUTAJ

Zarezerwowane do późniejszych plików `mechanika/`:

- Szczegółowe efekty zdarzeń na zasoby → `mechanika/07-events.md`
- Misje eksploracyjne przy Limes i koszt zasobów → `mechanika/06-missions.md`
- Systemy statku jako pełna lista (kadłub, sensory, lab) → `mechanika/05-ship-systems.md`
- LifeData / dane naukowe → `mechanika/06-missions.md` (Akt IV)

---

## Resources update — v1.0

**Ukończono:**
- Pięć zasobów MVP z przepływami opartymi na danych NASA
- ECLSS jako warstwa systemowa (6 podsystemów ze zdrowotnością)
- Pasywna degradacja systemów (statek się starzeje)
- Mapa kaskad między zasobami
- Progi krytyczne i warunki końca gry per zasób
- Wartości startowe i bilans
- Narracyjna rola Grzecha w mechanice
