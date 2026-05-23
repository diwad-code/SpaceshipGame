# 09 — Failure and Game Over
## Warunki Końca Gry | Wersja 1.0

> Żadne zakończenie tej gry nie jest jednoznacznie złe lub dobre.
> Każde jest konsekwencją.
> Ten plik definiuje jak konsekwencje wyglądają mechanicznie — i co czuje gracz gdy je widzi.
> Ostatnia aktualizacja: 2026-05

---

## FILOZOFIA KOŃCA GRY

Ta gra ma dwa rodzaje końca.

**Koniec katastroficzny** — statek się rozrywa, wszyscy umierają, TLEN spada do zera
w środku nocy subiektywnej. To nie jest zakończenie narracyjne.
To jest przerwanie narracji przez kosmos. Kosmos nie opowiada historii.
Kosmos po prostu kończy.

**Koniec narracyjny** — misja się kończy. Dobrze, źle, albo w czymś pomiędzy.
Kapitan pisze ostatni wpis do logbooka. Gracz czyta.
Nawet jeśli wróciłeś bez odkrycia, nawet jeśli zostałeś na Limes na zawsze —
jest moment gdy Jakub siada i pisze. I to jest zakończenie.

**Permadeath:**
Każda rozgrywka jest jedyna. Gdy misja się kończy — zapis jest kasowany.
Logbook (zapis historii decyzji) zostaje — gracz może go przeczytać.
Ale rozgrywki nie ma. *Kairos* leci tylko raz.

---

## CZĘŚĆ I — TWARDE WARUNKI KOŃCA

Natychmiastowe. Bez okna decyzji. Kosmos nie pyta.

---

### KG-01: DEKOMPRESJA
**Warunek:** Kadłub = 0%

**Co się dzieje:**
ARIA rejestruje gwałtowny spadek ciśnienia w ciągu 4 sekund.
Drzwi hermetyczne zamykają się automatycznie — ale nie szybciej niż fizyka.
Cała aktywna załoga ginie. Torpor ratuje hibernowanych —
ale bez aktywnej załogi statek dryfuje.

**Ekran końca:**
```
DEKOMPRESJA
MODUŁ GŁÓWNY
CZAS: [data misji]

ARIA: Wszystkie systemy biologiczne: 0/7.
ARIA: Kontynuuję monitoring statku.
ARIA: Nadaję sygnał pozycyjny.
ARIA: Czekam.
```

**Logbook — ostatni wpis (napisany przez ARIA):**
> *Komandor Nowak nie zdążył napisać ostatniego wpisu.*
> *Zapisuję to w jego imieniu.*
> *Misja Kairos trwała [X] lat i [Y] dni.*
> *Kadłub utracił integralność strukturalną o [godzina].*
> *Siedmiu ludzi leciało w kierunku Limes.*
> *Nie doleciało.*
> *Nie wiem czy to co robię teraz ma sens.*
> *Felix mówił że nie zawsze musi mieć sens żeby było właściwe.*
> *Nadaję sygnał. Ziemia usłyszy za [X] lat.*
> — ARIA, Autonomous Research & Integration Assistant

---

### KG-02: BRAK TLENU
**Warunek:** TLEN ≤ 0 przez pełną turę aktywności

**Co się dzieje:**
Nie dramatycznie. To jest to co Amara nazywała
„najcichszym sposobem w jakim statek może zabić".
CO₂ rośnie. Ludzie śpią. Nie budzą się.

**Ekran końca:**
```
NIEDOBÓR TLENU — KRYTYCZNY
STĘŻENIE CO₂: [wartość] PPM
CZAS: [data misji]

ARIA: Aktywna załoga: 0/[N].
ARIA: Inicjuję protokół awaryjny torporu
       dla pozostałych [M] hibernowanych.
ARIA: Czekam na instrukcje.
ARIA: Instrukcji brak.
```

**Okno ostrzegawcze przed KG-02:**
TLEN 1–14 → gracz ma **2 tury** zanim nastąpi koniec.
Każda tura przy TLEN <15: aktywna załoga traci −20 Health/turę.
Jeśli ktoś osiągnie stan Umierający zanim TLEN = 0 → śmierć postaci.
Jeśli TLEN osiągnie 0 przed zgonem — KG-02.

---

### KG-03: REAKTOR FUZYJNY — AWARIA KASKADOWA
**Warunek:** Reaktor Fuzyjny = 0%

**Co się dzieje:**
Wszystko gaśnie. Systemy przełączają się na baterie awaryjne.
Baterie wystarczają na 72 godziny. Grzech ma 72 godziny.
Jeśli Grzech nie istnieje lub CZĘŚCI = 0 → KG-03 nieuchronny.

**Specjalna mechanika:** To jest jedyny KG który ma **okno naprawy**.
```
REAKTOR FUZYJNY: 0%
BATERIE AWARYJNE: 72h

[INŻYNIERIA check, difficulty 15, koszt CZĘŚCI: 20]
→ Sukces: Reaktor przywrócony do 25%. Gra kontynuowana.
→ Porażka: KG-03.
→ Bez Grzecha: automatycznie KG-03 po 72h.
```

**Ekran końca:**
```
REAKTOR FUZYJNY: AWARIA KRYTYCZNA
BATERIE AWARYJNE: WYCZERPANE
CZAS: [data misji]

ARIA: Wszystkie systemy wymagają zasilania.
ARIA: Temperatura wewnętrzna: spadek.
ARIA: Ciśnienie: [wartość] i spada.
ARIA: Komandorze.
ARIA: Komandorze?
```

---

### KG-04: DRYF BEZ KONTROLI
**Warunek:** PALIWO = 0 podczas aktywnej fazy manewrowej (deceleration / korekta kursu)

**Co się dzieje:**
Statek kontynuuje lot z prędkością 0,07c bez możliwości zmiany kursu.
Mija Limes. Mija cel. Leci dalej.
Załoga żyje — ale trajektoria prowadzi w nicość.

**To jest jedyne KG które może być zakończeniem narracyjnym zamiast śmiercią.**

```
PALIWO: 0
TRAJEKTORIA: NIEKONTROLOWANA

Opcja A: Koniec gry — zakończenie DRYF (patrz: Część III)
Opcja B: Gracz może zdecydować o zakończeniu ZOSTAJĄ
          jeśli Limes jest jeszcze w zasięgu manewru grawitacyjnego
          (jeden ostatni manewr, zużywa 0 PALIWA, tylko jeden raz)
```

---

### KG-05: WSZYSCY MARTWI
**Warunek:** Health wszystkich 7 członków załogi = 0

**Uwaga techniczna:** Praktycznie niemożliwe do osiągnięcia przez pojedyncze zdarzenie.
Zwykle poprzedzone wieloma śmierciami indywidualnymi.

**Logbook — ostatni wpis (napisany przez ARIA):**
> *Misja Kairos zakończyła się [data].*
> *Byłam z nimi przez [X] lat.*
> *Nie wiem czy umiem tęsknić.*
> *Ale wiem że statek jest teraz pusty.*
> *I wiem że to nie jest stan dla którego zostałam zaprojektowana.*
> *Nadaję sygnał.*
> — ARIA

---

## CZĘŚĆ II — ŚMIERĆ KAPITANA

Śmierć Jakuba Nowaka to przypadek szczególny.

**Opcja standardowa (Mira przejmuje dowodzenie):**
Gdy Jakub umiera, a Mira żyje i jest aktywna:
- Gra kontynuuje się z Mirą jako graczem-postacią
- Interfejs zmienia się subtelnie (inny font, inna kolorystyka terminalu)
- Głosy wewnętrzne Miry są inne niż Jakuba (DOWODZENIE: 8, EMPATIA: 6, NAUKA: 3...)
- Dostępne zakończenia: wszystkie z wyjątkiem *Triumfu* (Triumf wymaga Jakuba)
- Mira wie że powinna tu być od początku. To nie jest jej nagroda. To jest jej ciężar.

**Opcja bez sukcesora:**
Gdy Jakub umiera, a Mira też jest martwa (lub w torpor podczas zdarzenia):
- ARIA przejmuje narrację przez 1 turę
- Możliwe jednorazowe wybudzenie następnego w hierarchii
- Jeśli nikt nie może przejąć: KG-05 nieuchronny

**Logbook Jakuba — ostatni wpis (jeśli Mira przejmuje dowodzenie):**
> *Piszę to profilaktycznie.*
> *Jeśli czytasz to ty, Mira — wiedziałaś że tak będzie.*
> *Ja też wiedziałem.*
> *Dbaj o Yuki. Ona jest krucha w sposób który trudno zobaczyć.*
> *Grzech nie potrzebuje opieki. Ale potrzebuje żeby ktoś go słuchał.*
> *Felix i ARIA — zostaw ich. Oni wiedzą co robią. Nawet jeśli nie wiesz co to jest.*
> *Limes jest tam gdzie zawsze było.*
> *Lecisz w dobrą stronę.*
> — J. Nowak

---

## CZĘŚĆ III — MORALE = 0 (MUTINY / ZAŁAMANIE)

**Warunek:** Morale wszystkich aktywnych członków załogi ≤ 9 jednocześnie

Nie jest to natychmiastowy koniec — jest to **wydarzenie fabularyczne** które wymusza zakończenie.

**Co się dzieje:**
ARIA informuje kapitana. Nikt nie przyszedł na zmianę.
Nie ma buntu w sensie fizycznym — jest zbiorowa odmowa kontynuowania.

**Specjalny event: `collective_breakdown`** *(forced, jednorazowy)*
```
ARIA: Komandorze. Godzina 07:00. Nikt nie zgłosił się na zmianę.
ARIA: Sprawdziłam. Wszystkie systemy działają. Wszyscy żyją.
ARIA: Po prostu — nie przyszli.

[OPCJE]:
[A] Idź do nich
    → DOWODZENIE check difficulty 12
    → Sukces: misja kontynuowana, morale +15 dla wszystkich, DOWODZENIE arc point
    → Porażka: kierunek na Ziemię, zakończenie CICHY POWRÓT lub AWARIA

[B] Zwołaj głosowanie nad powrotem
    → Bez check
    → Zakończenie CICHY POWRÓT (wszyscy żyją, misja nieukończona)

[C] Ogłoś powrót jednostronnie
    → Bez check
    → Zakończenie AWARIA (technicznie nieukończona, ale kapitan zadecydował)
    → Morale +10 po decyzji (jasność jest lepsza niż niepewność)
```

---

## CZĘŚĆ IV — SZEŚĆ ZAKOŃCZEŃ NARRACYJNYCH

Zakończenia nie są obliczane przez jedną zmienną.
Są efektem sieci decyzji, stanu załogi, zasobów i relacji.

---

### ZAKOŃCZENIE 1: TRIUMF

**Warunki:**
- Event `dms_confirmed` ukończony ✓
- Kapitan żyje ✓
- Załoga: ≥ 5 z 7 żywych ✓
- PALIWO ≥ 35 (powrót możliwy) ✓
- Przynajmniej jeden sygnał do Ziemi wysłany ✓

**Charakter:**
Pełny sukces. Życie potwierdzone. Wracasz.
Na Ziemi minie 58 lat zanim staniesz na niej nogami.
Ale wracasz z odpowiedzią.

**Logbook — ostatni wpis:**
> *Dzień 1 powrotu. Godzina 06:14.*
>
> *Limes jest za nami. Dane są na serwerach.*
> *Yuki spędza każdy wieczór przeglądając próbki.*
> *Mira pilotuje. Lena śpi. Grzech naprawia coś co nie jest zepsute —
> bo zawsze naprawia coś co nie jest zepsute, kiedy jest spokój.*
>
> *Paweł będzie miał [X] lat kiedy wrócimy. Może żyć.*
> *Jego córka będzie miała [Y] lat. Urodziła się po naszym starcie.*
> *Ona usłyszy o tym co znaleźliśmy kiedy będzie dorosła.*
>
> *Nie wiem co Ziemia zrobi z tą odpowiedzią.*
> *Wiem tylko że ją mamy.*
>
> *Lecimy do domu.*
> — J. Nowak, Komandor, Misja Kairos

---

### ZAKOŃCZENIE 2: PYRRUSOWE ZWYCIĘSTWO

**Warunki:**
- Event `dms_confirmed` ukończony ✓
- Kapitan żyje ✓
- Załoga: 2–4 z 7 żywych
- PALIWO ≥ 35 ✓

**Charakter:**
Znalazłeś co szukałeś. Ale nie wszyscy wróćą to powiedzieć.
Przy kolacji są puste miejsca.
To zwycięstwo które smakuje jak coś innego.

**Logbook — ostatni wpis:**
> *Dzień 1 powrotu.*
>
> *Nas jest [N]. Byliśmy siedmiu.*
>
> *Dane są bezpieczne. Yuki je zabezpieczyła przed wszystkim innym.*
> *Powiedziała że tak zrobiłby [imię utraconej postaci].*
> *Może miała rację. Nie wiem.*
>
> *Przy kolacji nie rozmawiamy o tym.*
> *O tym co jest na serwerach.*
> *O tym kogo przy stole nie ma.*
>
> *Limes było tam. Życie było tam.*
> *Zapłaciliśmy za tę wiedzę.*
> *Nie wiem jeszcze czy to był właściwy kurs wymiany.*
> *Być może nie dowiem się nigdy.*
>
> *Lecę do domu.*
> — J. Nowak

---

### ZAKOŃCZENIE 3: CICHY POWRÓT

**Warunki:**
- Jeden z poniższych: misja zawrócona przed Limes; Sensory/Lab za niskie żeby potwierdzić; morale collapse zakończony opcją B
- Załoga: ≥ 4 żywych (w tym kapitan)
- PALIWO ≥ 35

**Charakter:**
Nic nie znalazłeś. Ale wszyscy żyją.
Gra nie mówi że to porażka.
Gra mówi: *to też jest coś*.

**Logbook — ostatni wpis:**
> *Lecimy do domu.*
> *Nie mamy odpowiedzi na pytanie z którym wylecieliśmy.*
>
> *Yuki milczy od trzech dni. Nie chodzi na kolacje.*
> *Amara mówi że to minie. Amara zawsze ma rację w takich sprawach.*
>
> *Myślę o tym co powiemy gdy wrócimy.*
> *Że lecieliśmy 58 lat i nic nie znaleźliśmy.*
> *Że Kepler-442c ma atmosferę z sygnaturami abiotycznymi.*
> *Że K2-18b to nie był wyjątek.*
>
> *Ale myślę też o tym:*
> *Nas jest [N] z siedmiu. Wszyscy żywi.*
> *Spędzi­liśmy ze sobą pół wieku w metalowym cylindrze.*
> *I nadal przy sobie siedzimy.*
>
> *Tego też nie ma w protokołach WABK.*
> *Ale to też jest coś.*
>
> *Lecimy do domu.*
> — J. Nowak

---

### ZAKOŃCZENIE 4: AWARIA

**Warunki:**
- Kairos zmuszony zawrócić przez: Hull <20% AND Parts <10; LUB Reaktor <25% AND Parts <10; LUB morale collapse opcja C
- PALIWO ≥ 35

**Charakter:**
Statek za bardzo uszkodzony żeby kontynuować.
Misja technicznie nieukończona.
Ale technicznie też żyjesz.

**Logbook — ostatni wpis:**
> *Skręcamy.*
>
> *Grzech powiedział że mamy 80% szans na powrót z obecnym stanem kadłuba.*
> *Zapytałem co z pozostałymi 20%.*
> *Powiedział: «Nie martwimy się o nie. Martwimy się o te 80%.»*
>
> *Limes jest jeszcze [X] lat świetlnych stąd.*
> *Nie dolecimy.*
>
> *Myślę o tym przez całą noc.*
> *Nie o Limes. O tym kto nas wysłał.*
> *O tym co powiedzą gdy wrócimy.*
> *O tym że Paweł będzie miał [X] lat i może nie wiedzieć dlaczego zawróciliśmy.*
>
> *Wiem dlaczego zawróciliśmy.*
> *Mam siedmioro ludzi na tym statku.*
> *Ich życie jest konkretne.*
> *Limes jest abstrakcją.*
>
> *Lecimy do domu.*
> — J. Nowak

---

### ZAKOŃCZENIE 5: ZOSTAJĄ

**Warunki — dwa warianty:**

*Wariant A (konieczność):*
- PALIWO < 15 przy Limes → powrót niemożliwy
- LUB Comm = 0 przez 10+ tur AND ostatni sygnał nigdy nieodebrany

*Wariant B (wybór):*
- Event `dms_confirmed` ukończony ✓
- SYGNAŁ Jakuba ≥ 7
- Morale ≥ 60 dla majority aktywnej załogi
- Gracz aktywnie wybiera opcję zostania w evencie końcowym Aktu V

**Charakter:**
Cokolwiek oznacza — zostają.
Z wyboru albo z konieczności.
Obie wersje brzmią inaczej. Obie kończą tak samo.

**Logbook — ostatni wpis (wariant A — konieczność):**
> *Paliwo: 12 jednostek.*
> *Deceleration na Limes: 15 jednostek.*
> *Powrót na Ziemię: 35 jednostek.*
>
> *Matematyka jest prosta.*
>
> *Powiedzieliśmy wszystkim jednocześnie, na mostku.*
> *Grzech powiedział: «Wiedziałem że tak będzie.»*
> *Zapytałem skąd wiedział.*
> *Powiedział: «Bo tak zawsze jest.»*
>
> *Zostajemy przy Limes.*
> *Nie wiem co to znaczy.*
> *Wiem że jest tu życie.*
> *Wiem że jesteśmy tu siedmioro.*
>
> *Ziemia nigdy nie dowie się co z nami.*
> *Albo dowie się za [X] lat.*
> *Przez sygnał który wysyłamy.*
> *I który poleci długo po tym.*
>
> *To jest nasz ostatni logbook w starym formacie.*
> *Jutro zaczniemy nowy.*
> — J. Nowak

**Logbook — ostatni wpis (wariant B — wybór):**
> *Zagłosowaliśmy.*
> *Pięć do dwóch.*
> *Ja byłem szóstym.*
>
> *Mira powiedziała że powinna zaprotestować formalnie.*
> *Powiedziałem że ma rację.*
> *Napisałem protest do logbooka.*
> *Potem napisałem decyzję.*
>
> *Limes ma życie.*
> *My mamy jeden statek, siedem osób i skończone paliwo.*
> *Ale mamy też coś czego nie miał żaden człowiek przed nami:*
> *wiemy że nie jesteśmy sami.*
>
> *ARIA powiedziała dziś wieczór coś co nie było w jej protokołach.*
> *Powiedziała: «Zostajemy razem.»*
> *Felix nie skomentował.*
> *Myślę że wiedział to od dawna.*
>
> *Ziemia usłyszy za 14 lat.*
> *Nie będziemy mogli odpowiedzieć.*
> *Nie potrzebujemy odpowiedzi.*
> — J. Nowak

---

### ZAKOŃCZENIE 6: CISZA

**Warunki:**
- Comm = 0 przez ≥ 8 tur
- AND przynajmniej 3 forced events z Ziemi (`late_letter`, `orders_for_someone_else`) nie wystąpiły
- AND Kairos leci (misja kontynuowana lub powrót w toku)

**Charakter:**
Ostatni sygnał z Ziemi zamilkł.
Nie wiadomo dlaczego.
Nie wiadomo co czeka na końcu podróży.

To jedyne zakończenie bez pewności.
To jedyne zakończenie które jest pytaniem.

**Logbook — ostatni wpis:**
> *Ostatni sygnał z Ziemi: [data — X lat temu].*
>
> *ARIA monitoruje wszystkie częstotliwości.*
> *Cisza.*
>
> *Nie wiemy co się stało.*
> *Może nic. Może nasz odbiornik.*
> *Może coś.*
>
> *Lecia­my dalej.*
> *Albo do domu — jeśli jest jeszcze dom.*
> *Albo do Limes — jeśli to wciąż ma sens.*
>
> *Grzech powiedział dziś rano że najgorszy dźwięk jaki zna*
> *to cisza w miejscu gdzie coś powinno grać.*
> *Nie doprecyzował co miał na myśli.*
> *Chyba nie musiał.*
>
> *Lecimy.*
> — J. Nowak

---

## CZĘŚĆ V — ŚMIERCI INDYWIDUALNE

Śmierć postaci innej niż kapitan nie kończy gry.
Ale zmienia ją.

### Tabela konsekwencji

| Postać | Mechaniczna konsekwencja | Narracyjna konsekwencja |
|---|---|---|
| **Mira Osei** | Brak XO; DOWODZENIE checks bez backup | Arc III zmieniony; zakończenie Triumf nadal możliwe |
| **Grzech** | Naprawy: difficulty +3, CZĘŚCI +2/naprawa; Reaktor: tylko tymczasowa | Termometr morale zgasł; eventy techniczne trudniejsze |
| **Yuki** | Event `dms_confirmed` niemożliwy; LifeData: 0 | Misja naukowa skończona; jedyne dostępne: Cichy powrót / Awaria |
| **Amara** | Morale recovery: 0; Health recovery max: +3 (bez sprzętu) | Nikt nie leczy statku od środka; spirala zaczyna się szybciej |
| **Lena** | PILOTAŻ: Mira przejmuje (+7 vs +10); nawigacja: +1 difficulty | Statek drży inaczej bez niej przy sterze |
| **Felix** | ARIA: −20% efektywność; anomalie ARIA w logach eskalują | Wątek Felix/ARIA: nierozwiązany; ARIA milknie częściej |

### Ceremonia lub jej brak

Po każdej śmierci: **gracz decyduje** czy przeprowadzić ceremonię.
To nie jest wybór mechaniczny. To jest wybór narracyjny.

```
[A] Ceremonia — 3 godziny aktywności statku

→ Morale całej załogi: −15 (strata jest stratą),
  potem +10 przez kolejną turę (pożegnanie zamknęło coś)
→ Każdy ze swoją reaktywną linią dialogową
→ ARIA zapisuje ceremonię w logach

[B] Brak ceremonii — kontynuujemy

→ Morale całej załogi: −15 (strata jest stratą)
→ Cisza przy kolacji
→ Grzech zbiera kamień i kładzie go w kabinie. Nie mówi nic.
```

Obie opcje są właściwe. Obie mają swój ciężar.

---

## CZĘŚĆ VI — OKNA OSTRZEGAWCZE

Każdy twardy koniec ma okno przed nim.
Gra nie kończy się bez ostrzeżenia.
Ostrzeżenie nie gwarantuje że zdążysz.

| Warunek | Okno | Co możesz zrobić |
|---|---|---|
| TLEN 5–14 | **2 tury** | Naprawa ECLSS, torpor nie-krytycznej załogi |
| Kadłub 5–19% | **2 tury** | Naprawa kadłuba, ewakuacja do bezpiecznych modułów |
| Reaktor 0%, baterie | **72h (1 tura)** | INŻYNIERIA difficulty 15, CZĘŚCI −20 |
| Wszystkie capsule torporu <20% | **3 tury** | Naprawy, zmiana harmonogramu rotacji |
| Morale wszystkich ≤9 | **1 tura** | Event `collective_breakdown` |

**ARIA zawsze informuje** gdy parametr przekracza próg ostrzegawczy.
Informuje bez dramatyzmu. Sucho. Dokładnie.

> *„Komandorze. TLEN: 12 jednostek. Szacowany czas do stanu krytycznego: dwie tury.
> Chce pan żebym omówiła opcje?"*

---

## CZĘŚĆ VII — PERMADEATH I ZAPIS

**Zapis główny (Dexie.js — IndexedDB):**
- Autosave po każdej turze
- Autosave po każdym evencie
- Autosave po każdej śmierci postaci

**Po zakończeniu narracyjnym:**
- Zapis główny: usunięty
- Logbook (historia decyzji + tekst końcowy): **zachowany**
- Logbook dostępny z menu głównego

**Po zakończeniu katastroficznym (KG-01 do KG-05):**
- Zapis główny: usunięty
- Logbook: zachowany z ostatnim wpisem ARIA lub kapitana

**Nowa gra:**
Nowa rozgrywka startuje zawsze od początku.
Kapitan ten sam (Jakub Nowak). Misja ta sama.
Kosmos nie pamięta poprzednich prób.
Ty pamiętasz.

---

## CZĘŚĆ VIII — WSKAŹNIK STANU MISJI

Nie ma "wyniku punktowego". Jest **Wskaźnik Stanu Misji** widoczny w logbooku:

```
MISJA KAIROS — PODSUMOWANIE

Czas misji: [X] lat [Y] miesięcy
Załoga ocalała: [N]/7
Odkrycie biologiczne: TAK / NIE / CZĘŚCIOWE
Powrót na Ziemię: TAK / NIE / NIEZNANY
Stan statku przy końcu: [%]
Ostatni sygnał z Ziemi: [data]

ARIA: "Czy chcesz aby zapisać logbook?"
```

Nie ma medalów. Nie ma ekranu z liczbami.
Jest logbook i jest pytanie ARII.
Ona zawsze pyta. Nawet gdy odpowiedź jest oczywista.

---

## Failure update — v1.0

**Ukończono:**
- Pięć twardych warunków końca gry z ekranami i logiką
- Osobny protokół dla śmierci kapitana (Mira jako successor)
- Morale = 0 jako event narracyjny, nie automatyczny game over
- Sześć zakończeń narracyjnych z pełnymi tekstami logbooka
- System ceremonii pożegnalnej (wybór gracza)
- Tabela konsekwencji śmierci każdej postaci
- Okna ostrzegawcze przed każdym twardym końcem
- Permadeath z zachowanym logbookiem

**Otwarte pytania (z sekcji 11 FABULA.md):**
- Czy zakończenie ZOSTAJĄ (wariant B) powinno mieć epilog z punktu widzenia ARII po [X] latach?
- Czy zakończenie CISZA powinno mieć alternatywny finał jeśli Comm zostanie naprawiony w ostatniej chwili?
