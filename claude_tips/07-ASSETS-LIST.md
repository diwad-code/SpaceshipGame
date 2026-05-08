# Pixel Art Assets — Lista do pobrania

> Wszystkie linki sprawdzone w maju 2026. Licencje sprawdzaj w paczce — może się zmienić.

## Priorytet 1 — pobierz przed Sprintem 1 (CC0, free, full-commercial)

### Kenney (najbardziej polecane — zero atrybucji)

Wszystkie paczki Kenneya są **CC0** — możesz użyć w komercyjnej grze, bez podania źródła. Najlepszy zestaw startowy:

| Paczka | Link | Co zawiera |
|---|---|---|
| **Space Shooter Redux** | https://kenney.nl/assets/space-shooter-redux | 295 sprite'ów: statki, asteroidy, UFO, lasery, efekty |
| **Space Shooter Extension** | https://kenney.nl/assets/space-shooter-extension | Dopełnienie Redux: dodatkowe statki, tła |
| **Pixel Shmup** | https://kenney.nl/assets/pixel-shmup | Pixel-art alternatywa do Redux (mniejsza rozdzielczość, bardziej retro) |
| **Planets** | https://kenney.nl/assets/planets | Gotowe planety (vector + pixel) |
| **Space Kit** | https://kenney.nl/assets/space-kit | 150+ izometrycznych modeli — przydatne na ikony statku, wnętrze |
| **UI Pack** | https://kenney.nl/assets/ui-pack | 800+ przycisków, paneli, kontrolek |
| **Input Prompts Pixel 16x** | https://kenney.nl/assets/input-prompts-pixel-16 | Pixelowe ikony klawiszy, gamepada — kluczowe dla mobile UI |

### Bundle dla solo-deva

- **Kenney Game Assets All-in-1**: https://kenney.itch.io/kenney-game-assets
  - **$19.95 jednorazowo**
  - 60 000+ assetów wszystkich Kenneya w jednej paczce
  - Polecam dla solo-deva — zwraca się od pierwszej iteracji

## Priorytet 2 — uzupełnienia (sprawdź licencję per pack)

### CraftPix

- **Free Pixel Art SCI-FI Icon Pack**: https://craftpix.net/freebies/free-pixel-art-sci-fi-icons-pack/
  - 20 ikon space 128×128 (planety, meteory, galaktyki)
  - **Licencja CraftPix Free**: ✅ komercja, ❌ resale plików źródłowych
- **Space Game UI** (premium): https://craftpix.net/categorys/space-game-ui/
  - Futurystyczne UI: radary, holo-menu, kontrolki statku

### itch.io — szukaj filtra `free` + tag `pixel art` + `sci-fi`

- **OVERSTELLAR Pixel Art Pack**: https://free-game-assets.itch.io
  - Animowane gwiazdy, planety, mgławice, efekty FX, tła
  - Idealne dla space management (atmosfera!)
- **20 Free SCI-FI Icons Pixel Art**: https://free-game-assets.itch.io/20-free-sci-fi-icons-pixel-art

### OpenGameArt.org

https://opengameart.org/art-search?keys=space+pixel
- Niewyczerpane źródło
- **ZAWSZE czytaj pole „License"** przy każdym asset (preferuj CC0 lub CC-BY)
- Nie zakładaj — różne assety mają różne wymogi atrybucji

## Priorytet 3 — audio (na później, Sprint 6)

### Muzyka tła

- **OpenGameArt — Sci-Fi Music**: https://opengameart.org/art-search?keys=space&field_art_type_tid%5B%5D=12
  - Filtruj po CC0 / CC-BY
- **Free Music Archive**: https://freemusicarchive.org
  - Sprawdzaj licencję — niektóre wymagają atrybucji
- **Kevin MacLeod (incompetech.com)**: https://incompetech.com/music/royalty-free
  - CC-BY, wymaga atrybucji w credits

### Efekty dźwiękowe

- **Kenney – Sci-Fi Sounds**: https://kenney.nl/assets/sci-fi-sounds (CC0!)
- **Kenney – UI Audio**: https://kenney.nl/assets/ui-audio (CC0)
- **freesound.org**: https://freesound.org — sprawdzaj licencję

## AI pixel art (jeśli musisz coś niestandardowego)

### Bezpieczne prawnie (rekomendowane)

- **Retro Diffusion**: https://retrodiffusion.ai
  - Model dedykowany pixel art
  - Trenowany na licencjonowanych danych Astropulse
  - **50 darmowych kredytów na start**
  - Plugin do Aseprite (lokalny)
  - **Najlepsze rozwiązanie AI dla solo-deva w 2026**

- **PixelLab**: https://pixellab.ai
  - Pixel art z animacjami
  - Plugin do Aseprite
  - API do generowania w runtime
  - Bardziej zaawansowane, większa krzywa nauki

### Tinker only (prawnie szare)

- **Stable Diffusion + LoRA `nerijs/pixel-art-xl`**
  - HuggingFace, darmowe, ale wymaga GPU lokalnie albo Colab
  - Wynik nie jest pixel-perfect — musisz pixelate w Aseprite
- **Midjourney / DALL-E / Sora**: **NIE używaj do pixel art**
  - Generują „pseudo-pixel" (rozmyte), bez palety, bez snapowania do siatki

## Asset pipeline — jak organizować

### Struktura folderów

```
star-search/
├── public/
│   └── assets/
│       ├── kenney/
│       │   ├── space-shooter-redux/   ← surowe Kenneya
│       │   ├── ui-pack/
│       │   └── input-prompts/
│       ├── ships/                     ← finalne spritesheets do gry
│       │   ├── scout.png
│       │   └── scout.json             ← Aseprite atlas
│       ├── ui/
│       └── audio/
└── assets-source/                     ← surowe pliki .ase, .pxo (poza buildem)
    └── ships/
        └── scout.ase
```

### Workflow

1. **Surowe assety** trzymaj w `assets-source/` (folder poza Vite build, edytowalne w Aseprite/Pixelorama).
2. **Eksportuj do `public/assets/`** jako spritesheet PNG + JSON atlas.
   - Aseprite: `File → Export Sprite Sheet → JSON Hash → format Phaser`
   - Pixelorama: `File → Export → Spritesheet`
3. **Wczytaj w Phaserze**:
   ```typescript
   this.load.atlas('ship', 'assets/ships/scout.png', 'assets/ships/scout.json');
   ```
4. **Użyj w scenie**:
   ```typescript
   this.add.sprite(x, y, 'ship', 'idle_001');
   // Animacja:
   this.anims.create({
     key: 'idle',
     frames: this.anims.generateFrameNames('ship', {
       prefix: 'idle_', start: 1, end: 4, zeroPad: 3
     }),
     frameRate: 8,
     repeat: -1
   });
   ```

## Licencje — szybka ściąga

| Licencja | Komercja | Atrybucja | Uwagi |
|---|---|---|---|
| **CC0 / Public Domain** | ✅ | ❌ nie wymagana | Najwygodniejsza. Kenney = CC0. |
| **CC-BY** | ✅ | ✅ wymagana | Dodaj credits w grze (np. ekran „Credits") |
| **CC-BY-SA** | ✅ | ✅ wymagana | Twój projekt MUSI być na tej samej licencji — często niepożądane |
| **CC-BY-NC** | ❌ | ✅ wymagana | NIE wolno używać w grze, którą sprzedajesz |
| **CC-BY-ND** | ✅ | ✅ wymagana | Bez modyfikacji — często blokuje |
| **CraftPix Free** | ✅ | ❌ | Ale NIE wolno odsprzedawać plików źródłowych |
| **OpenGameArt-Custom** | różnie | różnie | Sprawdzaj per asset |

**Złota zasada**: zawsze trzymaj plik `LICENSE.txt` z każdej paczki w odpowiednim folderze. Gdy wydajesz grę — zrób ekran „Credits" z listą atrybucji dla CC-BY.

## Czego NIE używać

- **Assety Disney/Marvel/Pixar/Nintendo/Lucasfilm** — copyright
- **Sprite ripy z istniejących gier** (Star Wars, Star Trek, Mass Effect itp.) — naruszenie IP
- **AI generowane obrazy z DALL-E/Midjourney/Sora** w komercyjnej grze pixel art — szare prawnie + estetycznie nie pasują
- **Assety bez wyraźnej licencji** — domyślnie all rights reserved, NIE wolno używać
