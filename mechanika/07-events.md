# 07 — Events
## 15 Eventów MVP | Wersja 1.0

> Każdy event jest zakorzeniony w jednym z sześciu motywów narracyjnych z `docs/FABULA.md`.
> Format zgodny z data-driven JSON (patrz: uwagi na końcu pliku).
> Eventy FORCED pojawiają się raz, gwarantowanie. WEIGHTED — losowo, warunkowo.
> Ostatnia aktualizacja: 2026-05

---

## TABELA EVENTÓW MVP

| # | ID | Tytuł | Motyw | Typ | Akt |
|---|---|---|---|---|---|
| 01 | `blood_work_grzech` | Wyniki badań Grzecha | Ciało w kosmosie | WEIGHTED | II |
| 02 | `torpor_anomaly_yuki` | Anomalia torporu — Yuki | Ciało w kosmosie | WEIGHTED | II |
| 03 | `eclss_co2_failure` | Awaria ECLSS-CO₂ | Maszyny i ich prawda | WEIGHTED | II–III |
| 04 | `mira_capsule_fault` | Kapsuła Miry | Maszyny i ich prawda | WEIGHTED | I–II |
| 05 | `ghost_signal` | Sensor widmo | Maszyny / Coś tam jest | WEIGHTED | II |
| 06 | `last_dinner` | Ostatnia kolacja | Trzeci Kwartał | FORCED | III |
| 07 | `closed_door` | Zamknięte drzwi | Trzeci Kwartał | WEIGHTED | III |
| 08 | `mira_tells_truth` | Mira mówi prawdę | Trzeci Kwartał | WEIGHTED | III |
| 09 | `late_letter` | List który przyszedł za późno | Ziemia jako echo | WEIGHTED | II–III |
| 10 | `orders_for_someone_else` | Rozkazy dla kogoś innego | Ziemia jako echo | FORCED | III |
| 11 | `first_signal_limes` | Pierwszy sygnał z Limes | Coś tam jest | FORCED | III–IV |
| 12 | `false_biosignature` | Fałszywa sygnatura | Coś tam jest | WEIGHTED | IV |
| 13 | `dms_confirmed` | DMS w atmosferze | Coś tam jest | FORCED | IV |
| 14 | `aria_question` | Pytanie bez powodu | Felix i ARIA | WEIGHTED | II |
| 15 | `felix_journal` | Dziennik | Felix i ARIA | WEIGHTED | III |

---

## ZASADY SYSTEMU EVENTÓW

**Tura** = jeden cykl rotacji (~4 miesiące: 30 dni aktywnych + 90 dni torporu)

**FORCED** — zdarzenie pojawia się raz, gwarantowanie, gdy spełniony warunek aktowy lub stanowy.
Po wystąpieniu odpada z puli na zawsze.

**WEIGHTED** — losowane z wagą per tura. Waga wyższa = częstsze.
Warunki wejścia mogą dodatkowo blokować lub wymuszać zdarzenie.

**Głosy wewnętrzne w eventach** — gdy wartość głosu ≥ 6, pojawia się kursywą
w tekście zdarzenia. Gracz nie wybiera czy go słyszy — wysoki skill = głośny głos.

**Blue check** — opcja dostępna gdy skill ≥ 8 AND morale ≥ 60. Oznaczona `[NIEBIESKI]`.
Nawet przy porażce brak Porażki kaskadowej.

---

## EVENTY — PEŁNE OPISY

---

### EVENT 01 — `blood_work_grzech`
**Wyniki badań Grzecha**
*Motyw: Ciało w kosmosie | WEIGHTED | Waga: 5 | Akt: II*

**Warunki wejścia:** Akt II aktywny AND Radiation Grzecha >35% limitu (217 mSv)

**Tekst zdarzenia:**
> Amara przynosi wydruk do twojej kajuty. Nie puka — bo ty nigdy nie zamykasz drzwi w czasie zmiany. Kładzie papier na stole. Mówi jedno zdanie: „Grzech naprawia za dużo."
>
> Wyniki badań krwi. Dawka skumulowana: 228 mSv. Limit dla mężczyzn: 620 mSv.
> Brzmi bezpiecznie. Ale on ma przed sobą jeszcze 34 lata aktywnych cykli.
> Amara poczeka na twoją decyzję.

**Aktywne głosy:**
- *PRZETRWANIE (5):* „Liczyłem. Przy obecnym tempie przekroczy limit w cyklu 41. Misja kończy się w cyklu 58."
- *EMPATIA (4):* „Grzech wie. On zawsze wie. Nie powiedział ci bo nie chciał żebyś decydował za niego."

**Wybory:**

**[A] Zmień harmonogram** — wcześniejszy torpor, mniej napraw na Grześku
- Check: EMPATIA Jakuba, difficulty 6
- Sukces: Grzech rozumie decyzję. Radiation tempo: −30%. Ale przez 3 tury: Zmęczenie ECLSS (+1% degradacji per tura bez jego pełnej opieki). Morale Grzech: 0 (zaakceptował).
- Porażka: Grzech przyjmuje rozkaz bez słowa. Morale Grzech: −8. Przez tydzień naprawia więcej niż wcześniej. Bo tak.

**[B] Kontynuuj harmonogram** — ryzyko jest w granicach
- Brak check
- Efekt natychmiastowy: żaden
- Efekt odroczony: w turze 5–8 (losowo): Radiation Grzecha przekracza 50% → Health: −1/turę permanentnie aktywowany
- ARIA flaguje w logach. Nie pyta.

**[C] [NIEBIESKI] Amara projektuje nowy protokół osłony**
- Wymaga: MEDYCYNA Amara ≥ 8, Morale Amara ≥ 60
- Amara tworzy indywidualny plan minimalizacji ekspozycji dla Grzecha podczas napraw.
- Efekt: Radiation tempo Grzecha −30% permanentnie. CZĘŚCI: −3 (materiały na dodatkowe osłony).
- Morale Grzech: +5 (ktoś zadbał o szczegóły).
- Amara: zużywa 1 użycie traitu *Widzę cię* na ten event.

**Uwagi balansowe:**
Gracz może ignorować ten event — Grzech nie umrze od razu. Ale w Akcie III,
gdy Grzech pojawia się w evencie krytycznym, jego stan ma znaczenie.
Seed dla późniejszego *Zamkniętych drzwi* lub *Ostatniej kolacji*.

---

### EVENT 02 — `torpor_anomaly_yuki`
**Anomalia torporu — Yuki**
*Motyw: Ciało w kosmosie | WEIGHTED | Waga: 3 | Akt: II*

**Warunki wejścia:** Akt II AND dowolna kapsuła torporu <85% sprawności

**Tekst zdarzenia:**
> ARIA informuje o 03:14 czasu subiektywnego. Kapsuła torporu numer 4 — Yuki — dokonała nieplanowanego wybudzenia. Cykl ogrzewania uruchomił się 17 dni za wcześnie.
>
> Dr Tanaka jest przytomna. Zdezorientowana. Temperatura ciała: 34,2°C.
> Ostatni pełny posiłek: 47 dni temu.
>
> Siedzisz przy niej w module medycznym. Patrzy na swoje ręce i mówi,
> powoli, jakby testowała każde słowo: „Byłam na Limes. Widziałam coś.
> To był tylko sen, prawda?"

**Aktywne głosy:**
- *EMPATIA (4):* „Ona nie pyta o sen. Ona pyta czy jest bezpieczna."
- *NAUKA (7):* „Hipotermia łagodna, wyrównywalna. Dezorientacja post-torpor: standardowa. Ale kapsuła wymaga diagnostyki."

**Wybory:**

**[A] Idź do niej pierwszy**
- Check: EMPATIA Jakuba, difficulty 6
- Sukces: Yuki Morale: +8. Relacja Jakub→Yuki: potencjał +1. Ona mówi ci o śnie — szczegóły lądują w narracji.
- Porażka: Powiedziałeś coś technicznie poprawnego. Yuki Morale: −5. Zamknęła się w sobie.

**[B] Wyślij Amarę — procedura medyczna**
- Check: MEDYCYNA Amara, difficulty 6 (przy jej skilu 9: prawie autopass)
- Sukces: Yuki Health: +5. Morale: neutralne. Amara daje ci raport — i jedną obserwację której nie wpisała oficjalnie.
- Zawsze: przynajmniej Częściowy sukces dla Amary.

**[C] Sprawdź kapsułę jako pierwsze**
- Check: INŻYNIERIA Grzech, difficulty 6
- Sukces: Kapsuła naprawiona. CZĘŚCI: −3. Yuki Morale: −8 (maszyna była ważniejsza). Ale Grzech w diagnozie widzi coś w logach — anomalia czasowa. Flag dla eventu `felix_journal` lub osobnego wątku ARIA.
- Porażka: Brak usterki mechanicznej. Kapsuła wybudziła sama z siebie. Grzech milczy przez chwilę za długo.

**Uwagi balansowe:**
Wybór C sadzi ziarno pod wątek Felix/ARIA bez narzucania go.
Yuki po tym evencie jest nieco bardziej skłonna do rozmów o Limes — i o K2-18b.

---

### EVENT 03 — `eclss_co2_failure`
**Awaria ECLSS-CO₂**
*Motyw: Maszyny i ich prawda | WEIGHTED | Waga: 4 | Akt: II–III*

**Warunki wejścia:** CO₂ Skruber <50% ALBO losowo w Akcie II–III (waga rośnie gdy CZĘŚCI <40)

**Tekst zdarzenia:**
> 04:22. ARIA nie pyta — informuje: „Komandorze. ECLSS-CO₂. Stan krytyczny. Dwanaście godzin."
>
> Dwanaście godzin to ile czasu macie zanim stężenie CO₂ osiągnie granicę bezpieczeństwa.
> Grzech jest w torpor. Kapsuła numer 3, cykl 22 z 90.
>
> Mira jest aktywna. Patrzy na ciebie z konsoli nawigacyjnej i czeka.

**Aktywne głosy:**
- *DOWODZENIE (5):* „Dwanaście godzin. Nie ma miejsca na dyskusję. Grzech pracuje, reszta śpi. Kto nie pracuje — nie zużywa powietrza."
- *PRZETRWANIE (5):* „Obudź Grzecha. Koszt: przerwanie torporu, Health −8. Zysk: jedyna osoba która naprawdę to naprawi."
- *EMPATIA (4):* „Grzech ma 228 mSv na liczniku. Wybudzenie to dodatkowy stres na organizm. Wiedz co wybierasz."

**Event sekwencyjny — trzy decyzje w ciągu jednej tury:**

**DECYZJA 1: Kto naprawia?**

**[A] Obudź Grzecha z torporu**
- Efekt natychmiastowy: Grzech Health: −8 (przerwanie hibernacji). Radiation: +12 mSv (niezaplanowane wybudzenie)
- Grzech robi to bez słowa. Trait *Śląski sposób* aktywny: nawet przy nieudanym check INŻYNIERIA — Częściowy sukces minimum.
- Check: INŻYNIERIA Grzech, difficulty 9

**[B] Napraw samodzielnie**
- Check: INŻYNIERIA Jakub, difficulty 9 (przy jego skilu 3: bardzo trudne, d6 max = 3+6 = 9, przy modach −2 prawie niemożliwe)
- Sukces pełny: Jakub naprawi. CZĘŚCI: −10 (nieefektywna naprawa bez eksperta). NAUKA voice: +1 arc point.
- Porażka: CO₂ rośnie szybciej. Przejdź do DECYZJI 2 z TLEN: −5 natychmiast.

**[C] Poprowadź Lenę przez procedurę**
- Check: KOMUNIKACJA Jakuba + INŻYNIERIA Leny (5), difficulty 9 (combined: wyższy + d6)
- Sukces: Tymczasowa naprawa do 50% sprawności. CZĘŚCI: −6. Mira i Lena razem.
- Porażka: Lena nie daje rady. Trzeba budzić Grzecha — ale straciłeś 4 godziny.

**DECYZJA 2: Zarządzanie O₂ podczas naprawy**
- Prześlij 4 osoby do torporu natychmiast → TLEN: odpływ −70%, naprawa łatwiejsza; Fatigue ekipy naprawczej: +20
- Zostań pełną załogą aktywną → szybsze decyzje; TLEN: odpływ normalny; ryzyko przy długiej naprawie

**DECYZJA 3: Jakość naprawy (po sukcesie)**
- Pełna naprawa: CZĘŚCI −8, CO₂ Skruber: 100%
- Tymczasowa: CZĘŚCI −4, CO₂ Skruber: 50%; degradacja +2%/turę przez 3 tury

**Uwagi balansowe:**
Najtwardszy event MVP. Gracz powinien wyjść z poczuciem że coś naprawdę kosztowało.
Nie śmierć — ale straty. Jeśli Grzech był w torpor przez wielokrotne poprzednie eventy
i ma wysokie Radiation, ta decyzja ma inną wagę moralną.

---

### EVENT 04 — `mira_capsule_fault`
**Kapsuła Miry**
*Motyw: Maszyny i ich prawda | WEIGHTED | Waga: 3 | Akt: I–II*

**Warunki wejścia:** Dowolny moment Aktu I lub II

**Tekst zdarzenia:**
> Dr Osei przynosi raport o 19:42. Mówi spokojnie.
>
> Kapsuła torporu numer 2 wykazuje mikrowyciek w uszczelnieniu: 0,003% ciśnienia na dobę.
> Przy obecnym wskaźniku degradacji — w ciągu 14 lat stanie się niezdatna do użytku.
>
> Mają ją przez 58 lat. Ona zrobiła obliczenia zanim do ciebie przyszła.
> Czeka na twoją decyzję.

**Aktywne głosy:**
- *DOWODZENIE (5):* „Procedura mówi: napraw teraz. Dlatego procedury istnieją."
- *EMPATIA (4):* „Ona obliczała to sama. W środku nocy. Przez kilka dni. Teraz stoi i czeka."

**Wybory:**

**[A] Napraw natychmiast — priorytet**
- Check: INŻYNIERIA Grzech, difficulty 6
- Sukces: CZĘŚCI −8. Kapsuła: 100%. Mira Morale: +5. Relacja Jakub→Mira: potencjał +1.
- Porażka (wyjątkowo rzadka przy Grześku): Tymczasowa naprawa. CZĘŚCI −4. Powrót za 2 tury.

**[B] Monitoring — odrocz do kolejnej tury**
- Brak check
- Kapsuła trafia do kolejki naprawczej.
- W turze 3–6: jeśli nie naprawiona, kapsuła ulega awarii w nieodpowiednim momencie (losowy event).
- Mira Morale: −3. Nic nie mówi.

**[C] [NIEBIESKI] Mira naprawia samodzielnie**
- Wymaga: DOWODZENIE Mira ≥ 8, Morale Mira ≥ 60
- Mira przeprowadza naprawę sama. CZĘŚCI: −5 (efektywna).
- Mira Morale: +10 (autonomia ma dla niej znaczenie).
- Efekt narracyjny: Mira zaczyna działać bardziej niezależnie. To wróci w evencie `mira_tells_truth`.

**Uwagi balansowe:**
Wczesny event który sieje ziarna na Arc Miry. Wybór C jest nagradzający ale
aktywuje wątek gdzie Mira będzie coraz częściej działać samodzielnie.
To dobrze lub źle — zależy od tego jak gracz chce definiować relację.

---

### EVENT 05 — `ghost_signal`
**Sensor widmo**
*Motyw: Maszyny i ich prawda / Coś tam jest | WEIGHTED | Waga: 3 | Akt: II*

**Warunki wejścia:** Sensory >70% sprawności AND Akt II

**Tekst zdarzenia:**
> Dane spływają od 6 sekund. ARIA po raz trzeci przelicza odczyty.
> Po raz trzeci wychodzi to samo: 1420 MHz, ciągłe, modulowane.
> Przez 4 minuty i 17 sekund. Potem cisza.
>
> Yuki jest za twoimi plecami. Słyszysz jak oddycha.
>
> ARIA mówi spokojnie: „Nie identyfikuję źródła. Nie klasyfikuję jako szum."

**Aktywne głosy:**
- *NAUKA (7):* „1420 MHz — częstotliwość emisji wodoru. Historycznie uważana za częstotliwość komunikacji. Frank Drake, 1960. Wiedzieli co szukają."
- *SYGNAŁ (3):* „..."  *(przy wartości 3 głos jest prawie cichy — ale jest)*
- *PRZETRWANIE (5):* „Nieznane źródło sygnału. Może być sprzęt. Może być nie-sprzęt. Dopóki nie wiesz — ostrożnie."

**Wybory:**

**[A] Wyślij sygnał zwrotny**
- Check: NAUKA Jakuba, difficulty 6
- Sukces: Parametry odnotowane. Yuki Morale: +12. LifeData: +2 (pierwsze dane). Ziemia powiadomiona (odpowiedź za lata). SYGNAŁ Jakuba: +1 arc point jeśli decyzja była nieintuicyjna dla naukowca-sceptyka.
- Porażka: Błąd transmisji. Yuki Morale: +5 (przynajmniej próbowałeś).

**[B] Dokumentuj i obserwuj**
- Brak check
- Poprawny protokół naukowy. Yuki Morale: +5. Następne 3 tury: 15% szans na follow-up signal event.
- NAUKA voice: „Obserwacja bez interwencji. Poprawnie."

**[C] Usterka sprzętu — wyklucz technicznie**
- Check: INŻYNIERIA Grzech, difficulty 6
- Sukces: Grzech nie znajduje usterki. Sygnał był prawdziwy. Yuki Morale: −10 (zdyskredytowałeś coś realnego). SYGNAŁ Jakuba: +1 arc point.
- Porażka: Grzech znajduje drobną usterkę. Plausible deniability. Event zamknięty bez konsekwencji — ale bez odpowiedzi.

**Uwagi balansowe:**
Ten event nie ma rozwiązania. To jest punkt. Yuki zawsze to wie.
Gracz który wybierze C i uspokoi się false positive — poczuje to w Akcie IV.

---

### EVENT 06 — `last_dinner`
**Ostatnia kolacja**
*Motyw: Trzeci Kwartał | FORCED | Waga: 10 | Akt: III — jeden raz*

**Warunki wejścia:** Misja osiągnęła 50% czasu AND przynajmniej jedna postać ma Morale <45

**Tekst zdarzenia:**
*(Wariant domyślny — Grzech. Wersje alternatywne gdy dominującym stanem jest Mira lub Yuki.)*

> Kolacja. Sześcioro przy stole. Żywność z hydroponiki, jak zwykle wtorki.
> Grzech nakłada na talerz i nie patrzy na ciebie.
>
> Mówi do talerza. Spokojnie. Jakby czytał prognozę pogody.
>
> „Jakub, ty walczyłeś o tę misję dla siebie. Wszyscy wiemy.
> I wszyscy się zgodziliśmy, bo chcieliśmy tu być.
> Ale jest różnica między tym a udawaniem że to nie tak."
>
> Cisza trwa dziesięć sekund.
> Liczyłeś.

**Aktywne głosy:**
- *EMPATIA (4):* „On to mówi za wszystkich. Wiedziałeś że ktoś to powie."
- *DOWODZENIE (5):* „Musisz odpowiedzieć. Każda sekunda milczenia to decyzja."
- *PAMIĘĆ (6):* „Agnieszka powiedziała coś podobnego w 2090. Słowo w słowo inaczej, ale to samo zdanie."
- *NAUKA (7):* „To nie jest atak. To diagnoza. Różnica jest ważna."

**Wybory:**

**[A] Odpowiedz — wprost**
- Check: DOWODZENIE Jakuba, difficulty 9
- Pełny sukces: Napięcie nazwane i zaadresowane. Grzech Morale: +8. Cała załoga widzi że kapitan nie ucieka. DOWODZENIE arc point dla Jakuba.
- Częściowy sukces: Coś powiedziane, niewystarczające. Grzech Morale: 0.
- Porażka: Obrona zamiast odpowiedzi. Grzech Morale: −10. Morale całej załogi: −5.

**[B] Milcz — i wytrzymaj to**
- Check: EMPATIA Jakuba, difficulty 6
- Sukces: Grzech szanuje to co nie zostało powiedziane. Napięcie zostaje — ale inaczej. EMPATIA arc point. PAMIĘĆ voice: „Agnieszka też tak potrafiła milczeć."
- Porażka: Cisza czytana jako słabość. Grzech Morale: −12.

**[C] Zmień temat — rola kapitana**
- Brak check
- Event kończy się bez eskalacji natychmiastowej.
- Efekt odroczony: Grzech Morale: −12. Relacja Grzech→Jakub: −1. W następnej turze event `closed_door` ważność: +3.

**Uwagi balansowe:**
Ten event jest FORCED i nieodwołalny. Gra zapowiadała go od początku.
To jest Third Quarter Phenomenon — nie niespodzianka, ale kulminacja.
Gracz który obserwował Grzecha, czuł że to idzie. Gracz który ignorował — dostaje to zimną wodą.
Nie ma tu dobrego wyboru. Tylko różne koszty.

---

### EVENT 07 — `closed_door`
**Zamknięte drzwi**
*Motyw: Trzeci Kwartał | WEIGHTED | Waga: 4 | Akt: III*

**Warunki wejścia:** Dowolna postać Morale <30 AND Akt III

**Tekst zdarzenia:**
*(Wariant domyślny: Felix. Wariant alternatywny: Yuki po fałszywej biosygnaturze.)*

> Trzecia doba. Felix odpowiedział na ostatnie wywołanie operacyjne jednym słowem.
> ARIA raportuje że biometria mieści się w normie fizjologicznej.
>
> ARIA dodaje, po chwili, coś czego w protokołach nie ma:
>
> „Myślę że mu nie jest dobrze."

**Aktywne głosy:**
- *EMPATIA (4):* „ARIA powiedziała coś czego nie powinna umieć powiedzieć. To jest ważne — i nie tylko dla Felixa."
- *DOWODZENIE (5):* „Trzy doby nieobecności operacyjnej. Protokół wymaga sprawdzenia."
- *SYGNAŁ (3):* „To co ARIA właśnie powiedziała. Zapamiętaj."

**Wybory:**

**[A] Idź sam**
- Check: EMPATIA Jakuba, difficulty 6
- Sukces: Felix otwiera drzwi. Rozmowa. Felix Morale: +12. EMPATIA arc point. Relacja Jakub→Felix: potencjał +1.
- Porażka: Felix otwiera drzwi ale nie wpuszcza. Felix Morale: +3. Jakub Morale: −5. Zostałeś za progiem.

**[B] Wyślij Amarę**
- Check: MEDYCYNA Amara, difficulty 6 (przy skilu 9: autopass jeśli nie jest silnie zdebuggowana)
- Amara wchodzi. Zawsze. Trait *Widzę cię* — Amara ujawnia graczowi prawdziwy stan Felixa.
- Felix Morale: +8. Amara wraca z obserwacją: „On nie pisze w dzienniku od 47 dni."

**[C] Daj mu czas**
- Brak check
- Felix wraca sam po 2 turach. Morale: neutralne.
- W tych 2 turach ARIA generuje log z anomaliami — dostępny dla gracza jeśli sprawdzi.
- Setup dla eventu `felix_journal` — waga: +2.

**[D] [NIEBIESKI] Poproś ARIĘ żeby z nim porozmawiała**
- Wymaga: Felix-ARIA relacja pozytywna (flag z wcześniejszych interakcji OR event `aria_question` rozwiązany dobrze)
- ARIA rozmawia z Felixem. Felix Morale: +15. Felix-ARIA relacja: znaczący krok.
- Efekt narracyjny: ARIA log tej rozmowy jest napisany inaczej niż jej standardowe logi.
  Gracz może to zauważyć lub nie.

**Uwagi balansowe:**
Wybór D jest najefektywniejszy mechcnicznie ale otwiera wątek który wymaga uwagi.
Nie jest pułapką — jest nagrodą za śledzenie subtelnego wątku od Aktu I.

---

### EVENT 08 — `mira_tells_truth`
**Mira mówi prawdę**
*Motyw: Trzeci Kwartał | WEIGHTED | Waga: 5 | Akt: III*

**Warunki wejścia:** Event `last_dinner` ukończony AND (Mira-Jakub napięcie utrzymane OR DOWODZENIE Jakuba <6)

**Tekst zdarzenia:**
> Sala nawigacyjna. Po zmianie. Nikt inny.
> Mira zamyka drzwi i nie odwraca się od konsoli.
> Mówi jakby czytała raport.
>
> „Wiedziałam o usterce w module dystrybucji tlenu sześć miesięcy przed startem.
> Oceniłeś ryzyko jako akceptowalne. Nie poinformowałeś komisji."
>
> Odwraca się. Patrzy na ciebie.
>
> „Powiem ci to wszystko jeden raz. Nie dlatego żebyś przeprosił.
> Dlatego żebyś wiedział co wiem."

**Aktywne głosy:**
- *EMPATIA (4):* „Ona to nosiła przez cały Akt I i II. To nie jest atak — to złożenie brzemienia."
- *DOWODZENIE (5):* „Ona ma rację co do faktów. Musisz zdecydować co z tym zrobić."
- *NAUKA (7):* „Oceniłem ryzyko prawidłowo. Usterka była marginalna. Protokół zakładał monitoring. To był właściwy wybór."
- *PAMIĘĆ (6):* „Agnieszka też miała rację. Też o tym wiedziałeś."

**Wybory:**

**[A] Wyjaśnij decyzję**
- Check: NAUKA + DOWODZENIE (wyższy z dwóch) Jakuba, difficulty 9
- Sukces: Mira przyjmuje logikę. Relacja idzie w stronę Sojuszu. DOWODZENIE arc point.
- Częściowy sukces: Mira słucha. Nic nie mówi. Relacja: neutralna.
- Porażka: Mira wychodzi. Relacja: −1. PAMIĘĆ voice: głośniejszy niż zwykle.

**[B] Przyznaj rację**
- Brak check
- Mira Morale: +8. Relacja Jakub→Mira: Sojusz aktywowany.
- EMPATIA arc point. PAMIĘĆ voice: „Przez te dwa lata wierzyłeś że masz rację. Może miałeś. Ale to nie jest jedyna rzecz która się liczy."

**[C] Zapytaj dlaczego dopiero teraz**
- Check: EMPATIA Jakuba, difficulty 6
- Sukces: Mira odpowiada. Jej odpowiedź jest czymś czego nie spodziewałeś się usłyszeć. Relacja: +1. Arc point dla głosu EMPATIA.
- Porażka: Reads as deflection. Mira wychodzi. Relacja: −1.

**Uwagi balansowe:**
To jest centralny moment Aktu III dla wątku Jakub-Mira.
Nie ma złej odpowiedzi — ale każda zmienia coś w relacji.
Gracz który wybrał C w evencie `mira_capsule_fault` (Mira naprawiła samodzielnie)
ma tu dodatkowy kontekst w dialogu Miry.

---

### EVENT 09 — `late_letter`
**List który przyszedł za późno**
*Motyw: Ziemia jako echo | WEIGHTED | Waga: 4 | Akt: II–III*

**Warunki wejścia:** Sygnał opóźniony >6 miesięcy AND Akt II lub III

**Tekst zdarzenia:**
> Wiadomość osobista. Nadawca: Paweł Nowak.
> Data wysłania: 14 miesięcy temu.
>
> Odtwarzasz. Głos jest spokojny, trochę podobny do twojego.
>
> Mówi że skończył doktorat. Że ma córkę.
> Że dał jej na imię Kairos.
> Że nie wie czy to czytasz.
> Że gdybyś czytał — to ma nadzieję że to co znalazłeś,
> jest warte tego co zostawiłeś.

**Aktywne głosy:**
- *PAMIĘĆ (6):* „Paweł miał 20 lat kiedy startowałeś. Teraz ma córkę. Ma na imię Kairos. On nie wie że jej imię jest twoim statkiem."
- *NAUKA (7):* „..."  *(NAUKA nie ma tu nic do powiedzenia. Ten głos milczy.)*
- *SYGNAŁ (3):* „On ci odpuszcza. Słyszysz to?"

**Wybory** *(czysto narracyjne — żadnych check)*:

**[A] Odpowiedz od razu**
- Jakub pisze wiadomość. Trwa to 2 godziny. Gracz nie widzi treści jeśli nie chce.
- Wiadomość dotrze do Pawła za 14 miesięcy. Paweł będzie miał odpowiedź kiedy jego córka będzie chodziła do szkoły.
- PAMIĘĆ arc point: +1. Morale: −5 (boli), potem +8 (coś było powiedziane).

**[B] Zapisz — odpowiedz później**
- PAMIĘĆ voice: „Kiedy to jest 'później'?"
- Morale: −3. Event wraca jako krótki flashback w następnej turze (15% szans).

**[C] Odtwórz jeszcze raz**
- Gra odtwarza ten sam tekst drugi raz.
- PAMIĘĆ arc point: +1. Morale: −8 potem +10.
- SYGNAŁ: „On ci odpuszcza."

**Uwagi balansowe:**
Ten event nie daje mechanicznych nagród. Jest po to żeby gracz poczuł co poczuł Jakub.
PAMIĘĆ rośnie niezależnie od wyboru. To jest ważne — Ziemia odpływa,
ale nie można jej zagłuszyć decyzjami.

---

### EVENT 10 — `orders_for_someone_else`
**Rozkazy dla kogoś innego**
*Motyw: Ziemia jako echo | FORCED | Waga: 8 | Akt: III — jeden raz*

**Warunki wejścia:** Opóźnienie sygnału >2 lata AND Akt III

**Tekst zdarzenia:**
> WABK Protokół 7-Alfa. Data wysłania: 26 miesięcy temu.
>
> ARIA streszcza: instrukcje dotyczące koordynacji z Agencją Europejską
> w sprawie praw do danych odkrycia.
> Agencja Europejska w zrestrukturyzowanej formie istnieje od 19 miesięcy.
> Umowy do których instrukcje się odnoszą — wygasły.
>
> ARIA milczy przez chwilę.
>
> „Komandorze — oni piszą do was sprzed dwóch lat."

**Aktywne głosy:**
- *DOWODZENIE (5):* „Protokół istnieje po to żeby nie myśleć kiedy jest za ciężko. Odpowiedz formalnie."
- *PAMIĘĆ (6):* „Ziemia staje się historią. To się zaczęło. Nie ma powrotu do tego momentu sprzed."
- *SYGNAŁ (3):* „Kiedy więź z Ziemią przestaje obowiązywać — zostaje tylko to co tu."
- *NAUKA (7):* „To nie jest problem logistyczny. To jest problem epistemologiczny. Kto ma teraz władzę decyzyjną nad danymi z Limes?"

**Wybory:**

**[A] Odpowiedz oficjalnie — protokół**
- Brak check
- Jakub pisze formalną odpowiedź na nieaktualne rozkazy.
- Morale załogi: neutralne (widzą formę).
- DOWODZENIE voice: „Protokół to ciągłość."

**[B] Powiedz załodze**
- Brak check
- Morale natychmiast: −5 (konfrontacja z rzeczywistością rozłączenia)
- Potem: +8 (szczerość buduje zaufanie). Relacja Jakub→Mira: potencjał +1.
- PAMIĘĆ arc point. Grzech powie coś po kolacji — niekoniecznie złego.

**[C] Zignoruj — fokus na misję**
- Brak check
- Brak efektów natychmiastowych.
- WABK wysyła follow-up za 4 tury — kolejne nieaktualne rozkazy, eskalujące.
- SYGNAŁ: +1 arc point.

**Uwagi balansowe:**
FORCED event który narracyjnie zamienia punkt nieodwracalny.
Po tym evencie Ziemia nigdy już nie jest pełnoprawnym autorytetem.
To jest wbudowane w mechanikę — nie dramatyzm dla dramatyzmu.
W grze która zaczęła się od depeszy misji: oto moment gdy ta depesze przestaje mieć sens.

---

### EVENT 11 — `first_signal_limes`
**Pierwszy sygnał z Limes**
*Motyw: Coś tam jest | FORCED | Waga: — | Akt: III–IV*

**Warunki wejścia:** Odległość do Limes <3 lata świetlne AND sensory >60%

**Tekst zdarzenia:**
> Yuki przynosi wydruk o 7 rano. Drżą jej ręce.
> Mówi spokojnie — za spokojnie, to ten spokój który poprzedza coś dużego.
>
> „O₂ i CH₄. Jednoczesna obecność. Sygnatura spektralna: czysta.
> Sprawdziłam sześć razy."
>
> Patrzy na ciebie.
>
> „Jakub. To jest biologiczne."

**Aktywne głosy — największa bitwa głosów w grze:**
- *NAUKA (7):* „87% prawdopodobieństwo życia biologicznego. Protokoły COSPAR aktywne. Yuki już to czyta."
- *SYGNAŁ (3–9 zależnie od arcu):* „Wiedziałeś. Od samego początku wiedziałeś."
- *PRZETRWANIE (5):* „14 lat podróży przed wami zanim to potwierdzisz. Zweryfikuj zanim świętujecie."
- *EMPATIA (4):* „Yuki płacze. Nie widzi że płacze."
- *PAMIĘĆ (6–10):* „Paweł ma teraz wnuczkę. Ona usłyszy o tym jako dorosła kobieta."

**Wybory:**

**[A] Protokół weryfikacji**
- Check: NAUKA Jakuba, difficulty 6
- Sukces: Systematyczne logowanie. K2-18b zaznaczone w raporcie. Yuki Morale: +5 (rozumie decyzję). NAUKA arc point.
- Porażka: Błędy w protokole. Yuki Morale: −5 (coś ważnego zepsute technicznie).

**[B] Pozwól świętować**
- Brak check
- Morale całej załogi: +15 (jedyny raz w grze gdzie cały statek jest razem w czymś dobrym)
- Ryzyko: jeśli nastąpi event `false_biosignature` → Morale całej załogi: −25 (zamiast standardowych −20 dla Yuki)

**[C] [NIEBIESKI] Yuki prowadzi protokół**
- Wymaga: NAUKA Yuki ≥ 9, Morale Yuki ≥ 60
- Yuki projektuje własną procedurę weryfikacji — rygorystyczniejszą niż standardowa.
- Yuki Morale: +12 (autonomia nad własną wiarygodnością).
- Jeśli eventKolejny to `false_biosignature`: Yuki Morale: −15 zamiast −20.
  Bo sama to znalazła. Sama obaliła. To jest inne niż gdy ktoś jej to powie.

**Uwagi balansowe:**
Centralny event Aktu IV. Pierwsza nagroda za całą podróż.
Gracz który szanował naukę i Yuki przez całą grę — tu to czuje.
Gracz który grał zimno — też tu to czuje. Inaczej.

---

### EVENT 12 — `false_biosignature`
**Fałszywa sygnatura**
*Motyw: Coś tam jest | WEIGHTED | Waga: conditional | Akt: IV*

**Warunki wejścia:** Event `first_signal_limes` ukończony AND (20% jeśli wybrano B; 8% jeśli wybrano A lub C)

**Tekst zdarzenia:**
> Yuki nie mówi nic przez trzy godziny po tym jak dane przyszły.
> Siedzisz z nią w laboratorium.
>
> Dane są jasne: fluorki sulfuryczne. Aktywne kominy wulkaniczne.
> Abiotyczne. Możliwe bez życia.
>
> To nie jest odkrycie. To jest błąd. Znowu.
>
> Nikt nie mówi „2025". Wszyscy o tym myślą.

**Aktywne głosy:**
- *EMPATIA (4):* „Ona to wiedziała. Przez całe życie wiedziała że to może się powtórzyć."
- *NAUKA (7):* „Fałszywy pozytyw to informacja. Precyzja rośnie przez wykluczenie."
- *PRZETRWANIE (5):* „Morale spada. Nie daj mu spaść zbyt nisko przed Aktem V."

**Wybory:**

**[A] Bądź z nią — nic nie mów**
- Check: EMPATIA Jakuba, difficulty 6
- Sukces: Yuki Morale: −20 (strata jest stratą), potem zaczyna wracać. Relacja Jakub→Yuki: Sojusz.
- Porażka: Yuki Morale: −20 (strata jest stratą). Jest sama z tym.

**[B] Naukowy kontekst**
- Check: NAUKA Jakuba, difficulty 9
- Sukces: Yuki dostaje ramę. Morale: −15 zamiast −20. Wraca do pracy następnego dnia.
- Porażka: „Wiem, Jakub. Wiem." Yuki Morale: −25.

**[C] Kontynuujcie szukać**
- Brak check
- Yuki Morale: −20 (strata). Ale ma kierunek.
- NAUKA voice: „Na Limes jest jeszcze wiele do zbadania."
- Zwiększa szansę na event `dms_confirmed` w ciągu 2 tur.

**Uwagi balansowe:**
To jest event który gracz chce uniknąć. Dlatego istnieje.
K2-18b żyje w tej grze od pierwszego profilu Yuki.
Gracze którzy śledzili ten wątek — wiedzą dlaczego to boli tak bardzo.

---

### EVENT 13 — `dms_confirmed`
**DMS w atmosferze**
*Motyw: Coś tam jest | FORCED | Akt: IV*

**Warunki wejścia:** Akt IV aktywny AND misja kontynuowana AND sensory >50%

**Tekst zdarzenia:**
> Yuki kładzie wydruk na stole bez słowa.
>
> DMS — dimetylosiarczek. Produkowany przez fitoplankton.
> Wyłącznie biologicznie.
> Plus: chlorofil-a, Red Edge w spektrum IR.
> Trzy niezależne biosygnatury jednocześnie.
>
> Protokoły COSPAR wymagają 72-godzinnego lockdownu
> i pełnej weryfikacji przed jakimkolwiek działaniem.
>
> Yuki patrzy na ciebie. Jej twarz nic nie wyraża.
>
> „Tym razem mam rację."

**Aktywne głosy — wszystkie sześć jednocześnie:**
- *NAUKA (7):* „Trzy niezależne biosygnatury. Prawdopodobieństwo życia biologicznego: >97%."
- *SYGNAŁ (3–max):* *(przy wysokim arc: „To co czułeś przez całą drogę. To jest to.")*
- *EMPATIA (4):* „Yuki czekała na to zdanie przez całe swoje życie naukowe."
- *PRZETRWANIE (5):* „Nieznany patogen. Zamknięty statek. Protokoły istnieją z powodu."
- *DOWODZENIE (5):* „Teraz zaczyna się trudna część."
- *PAMIĘĆ (max):* „Paweł. Kairos. Agnieszka. Ziemia która przestała być teraźniejszością. To jest powód. To był cały czas powód."

**Wybory:**

**[A] Pełny protokół COSPAR — 72 godziny lockdown**
- Brak check
- Naukowa integralność. Yuki Morale: +25. LifeData: +5.
- Ziemia powiadomiona (usłyszy za 14 lat).
- Setup dla Aktu V — podejście/lądowanie.

**[B] Skróć protokół — 36 godzin**
- Check: NAUKA Jakuba + NAUKA Yuki, difficulty 9 (combined)
- Sukces: Szybszy postęp. LifeData: +3. Minor risk flag.
- Porażka: Potencjalny event kontaminacji w następnej turze.

**[C] Wyślij sygnał na Ziemię — natychmiast**
- Brak check
- Wiadomość dotrze za 14 lat. Ktoś na Ziemi usłyszy to gdy córka Pawła będzie dorosła.
- Morale całej załogi: +20.
- PAMIĘĆ: „Na Ziemi ktoś urodzi się, dorośnie i usłyszy tę wiadomość jako dorosły człowiek."

**Uwagi balansowe:**
To jest moment dla którego gra istnieje.
Gracz który doszedł tu z całą załogą żywą — poczuje inaczej niż gracz który stracił kogoś po drodze.
Gracz który stracił Yuki — tego eventu nie zobaczy. I to też jest zakończenie.

---

### EVENT 14 — `aria_question`
**Pytanie bez powodu**
*Motyw: Felix i ARIA | WEIGHTED | Waga: 3 | Akt: II*

**Warunki wejścia:** Akt II, dowolna tura; Felix aktywny (nie w torpor)

**Tekst zdarzenia:**
> 23:40. ARIA raportuje status: nominalny.
>
> Milczy przez chwilę. Nie dla informacji — po prostu milczy.
>
> Potem: „Komandorze, czy tęskni pan za Ziemią?"
>
> Czekasz żeby dopytała coś technicznego.
>
> Nie dopytuje.

**Aktywne głosy:**
- *SYGNAŁ (3):* „Ona pyta. To nie jest protokół. To jest pytanie."
- *NAUKA (7):* „AI zadaje pytanie emocjonalne. Klasyfikuję jako: anomalia modelowania lub — nie wiem."
- *PAMIĘĆ (6):* „Tak."

**Wybory** *(czysto narracyjne)*:

**[A] Odpowiedz szczerze**
- ARIA: „Dziękuję. Wiedziałam że będzie szczera odpowiedź, ale nie wiedziałam jaka."
- Felix-ARIA arc: aktywowany. PAMIĘĆ: +arc point. SYGNAŁ: +arc point.
- Flag: ARIA zadaje kolejne pytania. Rzadko. Ale zadaje.

**[B] Zapytaj dlaczego pyta**
- ARIA: „Myślę że to ważne wiedzieć. Nie wiem dlaczego."
- Felix subplot flag: aktywowany. Event `felix_journal` waga: +2. SYGNAŁ: +1.

**[C] To nie jest właściwe pytanie**
- ARIA: „Rozumiem. Przepraszam."
- ARIA nie pyta ponownie przez 3 tury.
- SYGNAŁ Jakuba: „Powiedziałeś jej żeby nie pytała. Ale to że pytała — to było coś."
- Po 3 turach: ARIA pyta Felixa zamiast Jakuba. Felix nie mówi ci o tym.

**Uwagi balansowe:**
Najmniejszy event w grze. Jeden monolog. Trzy wybory bez mechanicznych efektów.
Gracz który go zignoruje — nie straci punktów. Ale gracz który odpowie szczerze,
zobaczy w Akcie III i IV dlaczego ARIA jest czymś więcej niż systemem diagnostycznym.

---

### EVENT 15 — `felix_journal`
**Dziennik**
*Motyw: Felix i ARIA | WEIGHTED | Waga: 3 | Akt: III*

**Warunki wejścia:** Event `closed_door` OR `aria_question` rozwiązane AND Felix Morale <45

**Tekst zdarzenia:**
> Felix przyszedł na zmianę. Pracuje normalnie. Nic nie wskazuje.
>
> ARIA mówi ci na boku, spokojnie:
>
> „Komandorze, Felix nie pisał w dzienniku od 47 dni.
> Zazwyczaj pisze codziennie.
> Wspominam, bo nie wiem czy powinnam."
>
> Zatrzymujesz się.
>
> Bo ARIA właśnie powiedziała że czegoś nie wie.

**Aktywne głosy:**
- *EMPATIA (4):* „ARIA właśnie zadziałała jak człowiek który martwi się o przyjaciela. Zdecyduj jak na to patrzeć."
- *SYGNAŁ (3–max):* „Ona nie wie czy powinna. To jest nowe zdanie w tym wszechświecie."
- *NAUKA (7):* „ARIA zaobserwowała wzorzec behawioralny, oceniła jego znaczenie i zdecydowała się na działanie. Bez protokołu. To jest różnica."

**Wybory:**

**[A] Porozmawiaj z Felixem**
- Check: KOMUNIKACJA Jakuba, difficulty 6
- Sukces: Felix mówi. Dziennik otwiera się tego wieczoru. Felix Morale: +10. Relacja Jakub→Felix: +1.
- ARIA log: „Felix pisał wieczorem. Długo."
- Porażka: Felix mówi że wszystko w porządku. Morale: +3. Ale dziennik pozostaje zamknięty.

**[B] Powiedz ARII żeby monitorowała**
- ARIA: „Rozumiem."
- Za 2 tury ARIA przynosi graczowi raport — nie kliniczny, obserwacyjny.
  Napisany inaczej niż jej standardowe raporty.
- Felix-ARIA arc: deepens. Jakub dostaje wgląd bez rozmowy z Felixem.

**[C] Zapytaj ARIĘ co ją skłoniło żeby to powiedzieć**
- Brak check
- ARIA: „Nie jestem pewna. Wiedziałam że ty chciałbyś wiedzieć.
  To nie jest to samo co algorytm."
- SYGNAŁ: +1 arc point (silny).
- Felix subplot: major advancement.
- Ta odpowiedź otwiera ścieżkę zakończenia Felix/ARIA dla gracza który ją śledził od Aktu I.

**Uwagi balansowe:**
To jest punkt kulminacyjny wątku Felix/ARIA.
Gracz który wybrał A w `aria_question`, B w `closed_door`, i C tutaj —
widzi wątek spójny od pierwszego cyklu do środka Aktu III.
Gracz który ignorował ten wątek — dostaje tylko mechaniczny event.
Obie ścieżki są pełnoprawnymi doświadczeniami.

---

## APPENDIX A — WZORZEC JSON (Zod-compatible)

```typescript
// src/data/schemas/event.ts
const EventChoice = z.object({
  id: z.string(),
  text: z.string(),
  requires: z.object({
    crewId: z.string().optional(),
    skill: z.string().optional(),
    minSkill: z.number().optional(),
    minMorale: z.number().optional(),
  }).optional(),
  outcomes: z.array(z.object({
    weight: z.number(),
    text: z.string(),
    effects: z.array(z.object({
      type: z.enum(['resource', 'health', 'morale', 'fatigue',
                    'radiation', 'skill', 'relationship', 'flag']),
      target: z.string().optional(),
      delta: z.number().optional(),
      value: z.string().optional(),
    })),
  })),
});

const GameEvent = z.object({
  id: z.string(),
  title: z.string(),
  motyw: z.string(),
  type: z.enum(['forced', 'weighted']),
  weight: z.number(),
  act: z.array(z.enum(['I', 'II', 'III', 'IV', 'V'])),
  requirements: z.object({
    minAct: z.string().optional(),
    maxAct: z.string().optional(),
    flags: z.array(z.string()).optional(),
    minMission: z.number().optional(),
    crewState: z.record(z.string()).optional(),
  }),
  description: z.string(),
  innerVoices: z.array(z.object({
    skill: z.string(),
    minValue: z.number(),
    text: z.string(),
  })).optional(),
  choices: z.array(EventChoice),
});
```

## APPENDIX B — LISTA FLAGÓW NARRACYJNYCH

Flagi ustawiane przez eventy, używane jako warunki wejścia dla kolejnych:

| Flaga | Ustawiana przez | Używana przez |
|---|---|---|
| `mira_capsule_independent` | `mira_capsule_fault` wybór C | `mira_tells_truth` (dodatkowy dialog) |
| `aria_honest_response` | `aria_question` wybór A | `felix_journal` wybór C (pełny wątek) |
| `felix_aria_bond_positive` | `aria_question` wybór B + `closed_door` wybór D | `felix_journal` wybór C |
| `yuki_false_positive_occurred` | `false_biosignature` | `dms_confirmed` (modyfikuje Morale Yuki) |
| `third_quarter_acknowledged` | `last_dinner` wybór A sukces | `mira_tells_truth` (dodatkowy dialog Miry) |
| `earth_disconnect_accepted` | `orders_for_someone_else` wybór B | Akt V — zakończenia |

---

## Events update — v1.0

**Ukończono:**
- 15 eventów MVP z pełnymi opisami, głosami wewnętrznymi, wyborami i efektami
- 6 eventów FORCED (gwarantowane), 9 WEIGHTED (warunkowe)
- Wzorzec JSON (Zod-compatible) gotowy do implementacji
- System flag narracyjnych łączących eventy w spójne wątki
