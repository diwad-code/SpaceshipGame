# Star Search — Project Plan

## Cel projektu

**Star Search** to retro pixel-art space management game w stylu FTL: Faster Than Light / Crying Suns / Out There.

Gracz jest menedżerem statku kosmicznego na misji w poszukiwaniu życia. Zarządza załogą, rozdziela zadania, wybiera misje, gospodaruje zasobami. Decyzje wpływają na parametry załogi i statku. Występują losowe zdarzenia (uszkodzenia, anomalie, spotkania), które wymagają wykorzystania zgromadzonych zasobów.

**Platformy docelowe**:
- Web (PWA, działa offline, instaluje się jak aplikacja)
- Android (APK przez Trusted Web Activity, publikacja w Google Play)
- iOS — ewentualnie później przez Capacitor

## Stack techniczny

| Warstwa | Technologia | Powód wyboru |
|---|---|---|
| Silnik gry | **Phaser 3** (3.8x/3.9x) | Najlepiej obsługiwany przez Copilot, największy korpus tutoriali, stabilny |
| Język | **TypeScript** | Typy = mniej błędów, lepszy autocomplete, lepsze sugestie Copilota |
| Bundler / dev server | **Vite 6+** | De facto standard 2026, hot reload <100ms |
| Template | `phaserjs/template-vite-ts` | Oficjalny, utrzymywany, gotowy hot-reload |
| PWA | **vite-plugin-pwa** + Workbox | Zero ręcznego SW, auto-update, precache |
| Storage | **idb-keyval** (IndexedDB) | Async, bez blokowania UI, duża pojemność |
| Hosting | **Cloudflare Pages** | Free, unlimited bandwidth, najlepsza wydajność globalna |
| Android APK | **Bubblewrap** (TWA) lub **PWA Builder** | TWA = aktualizacje bez Google Play review |
| RNG | własny `weightedPick` + `seedrandom` | Małe utility, bez zależności |
| State | singleton `GameState` + `Phaser.EventEmitter` | Prosto, bez Reduxa |
| Editor pixel art | **Pixelorama** (free) → **Aseprite** ($19.99) | Pixelorama na start zero-koszt; Aseprite gdy zaboli |

## Architektura katalogów

```
star-search/
├── .github/
│   ├── copilot-instructions.md          ← always-on dla Copilota
│   ├── instructions/
│   │   ├── phaser.instructions.md       ← applyTo: "src/scenes/**"
│   │   └── ui.instructions.md           ← applyTo: "src/ui/**"
│   ├── prompts/
│   │   ├── new-event.prompt.md
│   │   ├── new-scene.prompt.md
│   │   └── code-review.prompt.md
│   └── workflows/deploy.yml             ← GitHub Actions auto-deploy (opcjonalnie)
├── public/
│   ├── assets/                          ← spritesheets, audio, JSON atlasy
│   ├── manifest.webmanifest
│   ├── pwa-192x192.png
│   ├── pwa-512x512.png
│   └── .well-known/assetlinks.json     ← dla TWA Digital Asset Links
├── src/
│   ├── main.ts                          ← entry point, Phaser config
│   ├── scenes/                          ← BootScene, MenuScene, MapScene, EventScene, BattleScene
│   ├── systems/                         ← CrewSystem, ResourceSystem, EventSystem, SaveSystem, RNGSystem
│   ├── data/                            ← events.json, crew.json, ships.json (JSON jak Excel)
│   ├── ui/                              ← komponenty UI (HTML/CSS overlay nad canvasem)
│   ├── types/                           ← interfejsy TS (CrewMember, Resource, GameEvent)
│   └── utils/                           ← weightedRandom.ts, idbStorage.ts
├── docs/
│   ├── SCOPE.md                         ← co JEST w MVP
│   └── IDEAS_LATER.md                   ← pomysły na po MVP
├── index.html
├── vite.config.ts
├── tsconfig.json
├── package.json
└── README.md
```

## Kluczowe systemy gry — wzorce projektowe

### 1. System zdarzeń (Event System)

Zdarzenia trzymane w `src/data/events.json`. Każde zdarzenie:

```json
{
  "id": "abandoned_station_01",
  "title": "Opuszczona stacja",
  "description": "Z mgły wynurza się stacja badawcza. Ślady walki.",
  "weight": 5,
  "requirements": { "min_fuel": 1 },
  "choices": [
    {
      "text": "Zbadaj wnętrze (wymaga inżyniera)",
      "requires": { "crew_skill": "engineering", "min_value": 3 },
      "outcomes": [
        { "weight": 70, "text": "Znalazłeś części.", "effects": [{ "type": "parts", "value": 3 }] },
        { "weight": 30, "text": "Pułapka. Ranny członek załogi.", "effects": [{ "type": "crew_hp", "value": -2 }] }
      ]
    },
    {
      "text": "Lećmy dalej",
      "outcomes": [
        { "weight": 100, "text": "Bezpiecznie kontynuujesz misję.", "effects": [] }
      ]
    }
  ]
}
```

**Kluczowy insight z FTL**: outcome'y wewnątrz wyboru są ważone (np. 70% sukces, 30% strata). To czyni wybory ciekawymi, ale nie czysto losowymi — gracz widzi opcje i decyduje świadomie. „Blue option" = wybór dostępny tylko gdy spełnione `requires` (gwarantuje lepszy wynik).

**MVP**: 15-20 zdarzeń wystarczy do pierwszego playtestu. Cel docelowy: 50-100.

### 2. Weighted random (serce gry)

```typescript
// src/utils/weightedRandom.ts
export function weightedPick<T>(items: { value: T, weight: number }[]): T {
  const total = items.reduce((s, i) => s + i.weight, 0);
  let r = Math.random() * total;
  for (const item of items) {
    if ((r -= item.weight) <= 0) return item.value;
  }
  return items[items.length - 1].value;
}
```

5 linijek, ale obsługuje: wybór zdarzenia, outcome wyboru, drop zasobów, generację statku przeciwnika.

### 3. System załogi (Crew System)

```typescript
// src/types/CrewMember.ts
export interface CrewMember {
  id: string;
  name: string;
  role: 'pilot' | 'engineer' | 'medic' | 'soldier' | 'scientist';
  skills: {
    piloting: number;     // 0-10
    engineering: number;
    combat: number;
    science: number;
    medicine: number;
  };
  health: number;       // 0-10
  morale: number;       // 0-10
  traits: string[];     // np. ['lucky', 'cynical', 'veteran']
}
```

Skille rosną przez wykonywanie zadań (jak w FTL). Morale spada przy stratach, rośnie przy sukcesach. Traity to flagi modyfikujące outcome'y zdarzeń.

### 4. Resource Management

**MVP — minimum 3 zasoby**:
- `fuel` (paliwo) — koszt jumpu między beaconami
- `scrap` (złom) — uniwersalna waluta
- `parts` (części zamienne) — naprawy statku

Każdy zasób MUSI mieć **input** (zdarzenia, sklepy, walka) i **output** (jump, naprawa, kupno). Brak inputu = ślepa uliczka. Brak outputu = bezużyteczny zasób.

### 5. Mapa sektora (Map Scene)

Graf — każdy node = beacon, krawędzie = możliwe jumpy. Procedural generation:
1. Rozrzuć N punktów (15-25) w obszarze 800×600 px (Poisson disc sampling — równomierny rozkład).
2. Połącz każdy beacon z 2-4 najbliższymi (relative neighborhood graph).
3. Każdy beacon ma typ: `empty | event | shop | combat | distress | quest`.
4. Start na lewej krawędzi, exit na prawej.

### 6. Save / Load

```typescript
// src/systems/SaveSystem.ts
import { get, set, del } from 'idb-keyval';

const SAVE_KEY = 'savegame_slot1';

export async function saveGame(state: GameState): Promise<void> {
  await set(SAVE_KEY, JSON.stringify(state));
}

export async function loadGame(): Promise<GameState | null> {
  const raw = await get<string>(SAVE_KEY);
  return raw ? JSON.parse(raw) : null;
}

export async function deleteSave(): Promise<void> {
  await del(SAVE_KEY);
}
```

Auto-save po każdym jumpie. Permadeath = po game over kasuj save.

### 7. State Management — bez Reduxa

```typescript
// src/systems/GameState.ts
export class GameState {
  private static instance: GameState;
  
  fuel = 10;
  scrap = 0;
  parts = 5;
  crew: CrewMember[] = [];
  currentBeaconId = '';
  events = new Phaser.Events.EventEmitter();
  
  static getInstance(): GameState {
    if (!GameState.instance) GameState.instance = new GameState();
    return GameState.instance;
  }
  
  modifyResource(type: 'fuel' | 'scrap' | 'parts', delta: number): void {
    this[type] = Math.max(0, this[type] + delta);
    this.events.emit('resource-changed', type, this[type]);
  }
}
```

Sceny i UI subskrybują się przez `GameState.getInstance().events.on('resource-changed', handler)`. Prosto, działa, zero zewnętrznych libów.

## Roadmapa sprintów (do MVP)

| Sprint | Tydzień | Cel | Definition of Done |
|---|---|---|---|
| **0** | Przed | Setup środowiska | Działający `npm run dev` z template'em Phasera |
| **1** | 1 | MapScene + statek | Klikalna mapa z 10 beaconami, statek się przemieszcza |
| **2** | 2 | Stan gry + zasoby | Klik na beacon = -1 fuel, game over przy fuel=0 |
| **3** | 3 | System zdarzeń | 10 zdarzeń, 30% szans po jumpie, modal z wyborami |
| **4** | 4 | Załoga + UI | 3 startowych crew, panel po prawej, requires na zdarzeniach |
| **5** | 5 | Save/load + PWA | IndexedDB save, instalacja jako PWA na telefonie |
| **6** | 6 | Polish + Bubblewrap | Audio, animacje, deploy Cloudflare, APK przez Bubblewrap |

**Po MVP** (3-6 miesięcy iteracji):
- 50+ zdarzeń
- 2-3 typy statków startowych
- System walki turn-based
- Drzewa misji, frakcje, fabuła główna

## Zasady walki ze scope creep

1. **`docs/SCOPE.md`** — co JEST w MVP. Świętość. Zmiany tylko w ekstremalnych przypadkach.
2. **`docs/IDEAS_LATER.md`** — wszystkie nowe pomysły idą TUTAJ, nie do kodu.
3. **W piątek każdego sprintu MUSI być coś klikalnego.** Bez wyjątku.
4. **Pokaż grę 3 osobom po sprincie 3.** Nie czekaj do końca.
5. **Polishing assetów = po MVP.** Dopóki nie ma core loopu, używasz Kenney placeholderów.

## Realistyczny budżet czasu

Bazując na postmortemach solo-deweloperów (np. Bass Monkey: 18 miesięcy od zera w niepełnym wymiarze):

- **2-3 tygodnie** — fundamenty (HTML/CSS/JS basics, jeśli zero doświadczenia)
- **4-6 tygodni** — MVP (przy 2-3h dziennie systematycznie)
- **3-6 miesięcy** — iteracja do publikowalnej v1.0
- **+1-2 miesiące** — Google Play review pipeline (Internal → Closed → Open → Production)

**Razem realistycznie: 6-12 miesięcy do publikacji w Google Play.** Każdy kto obiecuje krócej, kłamie.

## Inspiracje — co dokładnie kraść

Gry, których architektura przekłada się na ten projekt:

- **FTL: Faster Than Light** — event system, blue options, weighted outcomes, sektory z beaconami, permadeath
- **Crying Suns** — narracyjne zdarzenia, pixel art na rich background, mood/atmosfera
- **Out There** — minimalizm zasobów (paliwo, tlen, żelazo), ciemny ton
- **Star Traders: Frontiers** — głęboki crew management, traity, trading

**NIE kradnij**: real-time-with-pause z FTL (rok pracy dla solo-deva). Zostań przy turn-based.

## Źródła i referencje

- Phaser docs: https://phaser.io/learn
- Vite PWA plugin: https://vite-pwa-org.netlify.app
- Bubblewrap: https://github.com/GoogleChromeLabs/bubblewrap
- Kenney assets: https://kenney.nl/assets
- FTL event analysis: https://ftl.fandom.com/wiki/Event
- idb-keyval: https://github.com/jakearchibald/idb-keyval
- GitHub Copilot custom instructions: https://docs.github.com/en/copilot/customizing-copilot
