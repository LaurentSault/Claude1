# Art Direction & UI

Status: v1.0 — 2026-10-06 · Owns: resolution and hardware constraints, sprite and portrait specs, animation lists, tilesets and palettes, special effects, every UI screen, fonts and the hangul glyph subset, the field walk speed · Depends on: none (canon only) · Canon: docs/00_CANON.md

> Where this doc restates the canon (CANON §1 platform, R-39 sprite cell, §5g visual key, §16a box, §16h UI), the canon is the source. Battle geometry matches `combat_ensemble.md` §2.1, the candle matches `secrecy_and_trust.md` §2.7, and box behaviour matches `dialogue_style_guide.md` §1; this doc adds the art and the hardware behind them. **Hex rule:** every colour is BGR555-snapped (each channel a multiple of 8, so every byte ends in 0 or 8). What the artist picks is what the hardware shows.

## Contents

1. [Art Direction: Two Lights](#1-art-direction-two-lights)
2. [Hardware Constraints](#2-hardware-constraints)
3. [Colour Language](#3-colour-language)
4. [Sprites and Portraits](#4-sprites-and-portraits)
5. [Animation Lists](#5-animation-lists)
6. [Tilesets and Palettes by Location](#6-tilesets-and-palettes-by-location)
7. [Special Effects](#7-special-effects)
8. [UI Screens](#8-ui-screens)
9. [Fonts and Text Rendering](#9-fonts-and-text-rendering)
10. [Accessibility](#10-accessibility)
11. [Canon Additions & Cross-Doc Notes](#canon-additions--cross-doc-notes)

---

## 1. Art Direction: Two Lights

The game is a quarrel between two ways of seeing. Delacroix paints *subjects*: dark grounds, drama, a vermilion shout. Lucile paints *light*: the hour, the air, colour inside shadow (CANON §5e). The art starts on Delacroix's side, with candle pools in black rooms and grey fog on grey stone, and Lucile's eye slowly enters it (§3.4). Paris has **warm sources in a cold world** (réverbères, tallow, Argand lamps, the passages' gas jets); Seoul inverts it with **cold sources on warm interiors** (LED, tubes, phone screens over heated floors). One hand draws both cities, at one outline weight, grid and palette budget, so the Chrono-Labyrinth reads as one world tearing, not two styles colliding.

| # | Rule | In practice |
|---|---|---|
| A1 | Every frame has a named light source | Each tileset (§6.2) names its source; no ambient-only rooms |
| A2 | Colour is narrative | The Violet Shadow Rule, the Wrong Colour, the Hour colours (§3.4) |
| A3 | Hardware honesty | SNES limits are disciplines (CANON §1); the Constraint Lint (§2.7) enforces them |
| A4 | Images, never bodies | Echoes are stone, smoke, paint and sound, never the dead (LAW-07); cholera shown by absence (CANON §16e) |
| A5 | Read by shape and motion | Every state reads without colour (CANON §11j); silhouettes pass a one-colour test first |
| A6 | Period first, romance second | Objects are 1833 (or 2026) to the button; drama comes from light |

---

## 2. Hardware Constraints

### 2.1 Screen, modes and layer roles

**Screen:** 256 × 224 at 60 Hz, 32 × 28 tiles of 8 × 8. PC and Switch output uses integer scaling (4× at 1080p, 9× at 2160p) with an option for 8:7 pixel aspect (§10).

| Context | Mode | BG1 | BG2 | BG3 (2bpp, priority) | OBJ |
|---|---|---|---|---|---|
| Field and overworld on foot | 1 | Map: floors, walls (4bpp) | Overlay: roofs, arches, canopies; **portraits** on dialogue lines (§8.2) | Weather (fog, rain, snow), HUD text, dialogue box | Cast, townsfolk, UI |
| Battle | 1 | Enemies and wards (4bpp) | Backdrop (4bpp) | Windows, text, Onlooker silhouettes | Party, FX, cursor |
| Flight, BOSS-27, Labyrinth folds | 7 (+ Mode 1 split) | Mode 7 plane (8bpp) | — | Mode 1 band only | Craft, party, HUD |
| Menus | 1 | Portraits | Window frames | Text | Cursor, icons |
| Showcase plates (§6.5) | 3 | 8bpp full-screen image | — | — | none |

### 2.2 VRAM, CGRAM and DMA budgets

| VRAM (64 KB) | Field | Battle |
|---|---|---|
| BG1/BG2 4bpp tiles | 32 KB: 952 map tiles (≈ 260–320 metatiles) + 72 portrait tiles (two portraits resident) | 16 KB enemies and wards; 12 KB backdrop |
| BG1/BG2 maps | 8 KB (two 64 × 32, streamed at the camera edge) | 4 KB |
| BG3 tiles and maps | 8 KB: VWF canvas, frames, HUD digits, weather | 8 KB |
| OBJ tiles | 16 KB: frames double-buffered, townsfolk, UI | 16 KB: party 128, FX 256, UI 128 tiles |
| Spare | — | 8 KB for boss-phase swaps |

| CGRAM | Field | Battle |
|---|---|---|
| 0 | Backdrop: the box-gradient target (§8.2) | Backdrop |
| 1–31 | BG3 sub-palettes: text, gold, grey, HUD, weather | Text, gauges, Onlookers |
| 32–111 (BG palettes 2–6) | The map tileset: **75 colours** | Enemies and wards: palettes 2–4 (**≤ 3 per formation**) |
| 112–127 (palette 7) | Portrait, reserved on every map | Backdrop: palettes 5–7 (80–127) |
| 128–255 | OBJ palettes 0–7 (§2.3) | OBJ palettes 0–7 |

**DMA per vblank:** ≤ 4 KB of VRAM plus OAM (544 B) and ≤ 512 B of CGRAM, so the field streams up to six 512-byte character frames a frame. Showcase plates (56 KB) load under forced blank behind a 16-frame fade.

### 2.3 OBJ rules and the 32 × 32 cell

The brief's "expressive 32x32 character sprites" become a **32 × 32 cell holding a figure of about 20 × 30 px on a 16 × 16 grid** (R-39), which fits the OBJ rules:

- **OBSEL size set 3** (16 × 16 small, 32 × 32 large): every PC and Tier A/B frame is one large OBJ; effects, emotes and the cursor are small OBJs; Tier C townsfolk are two stacked small OBJs (16 × 32).
- **Anchor:** the cell's bottom-centre sits on the feet tile's bottom-centre (cell x = tile x − 8, y = tile y − 16); collision uses the feet tile; BG2 overlay hides the head under arches.
- **Scanlines:** 32 OBJs and 34 slivers per line; a large OBJ costs 4. Field: ≤ 6 large OBJs per line, leaving 10 slivers for UI and FX. Battle: the 24-px party stagger puts ≤ 2 party sprites on a line (≤ 4 in the Octave).
- **Colour math reaches only OBJ palettes 4–7:** field OBJs never blend (BG3 does field translucency); battle FX live on 4–7; in the Octave all eight palettes hold members, so FX move to BG3.
- **Fixed indexes:** in every PC palette index 1 = #101018 and index 2 = #F8F8F8, so the cursor, damage digits and overhead markers draw on any party palette.
- **Flips:** right-facing frames mirror, except Lucile (brush roll on the right hip) and Chopin (violet in the left buttonhole).

| OBJ palette | Field | Battle | Octave (BOSS-27) |
|---|---|---|---|
| 0–3 | Leader and cast | Party slots 1–4 (+ cursor, digits, markers) | Members 1–4 |
| 4–5 | Townsfolk ramps; Watchers, patrols | FX (translucent) | Members 5–6 |
| 6 | UI: cursor, emotes, candle, sparkles | FX | Member 7 |
| 7 | Extra cast | FX (Tutti, Remembrances) | Member 8 |

Wards and escorts (Théo, Vane, the BOSS-33 canvas) are static BG1 graphics, so FX translucency never ghosts them.

### 2.4 Field movement and camera (owned values)

| Value | Spec |
|---|---|
| **Walk speed** | **1 px per frame** (60 px/s): 16 frames per tile; 4-frame walk cycle at 8 frames each = 2 tiles per cycle. `formulas_and_curves.md`'s encounter calibration assumes this value |
| Dash | Hold B: 2 px per frame on town and interior maps only. Dungeons and overworlds stay at walk speed, so encounter pacing per minute holds |
| Grid | 4-direction, tile-locked: an input commits a full 16-px step. Diagonal stairs slide 1 px per frame on both axes |
| Camera | Centred on the leader, clamped at map edges, 1:1 scroll with no smoothing; cutscene pans (`{CAM:}`) move at integer px per frame |
| Depth | OAM re-sorted by feet y every frame; BG2 priority tiles draw over sprites |
| Party on maps | Leader only (FF6); members appear in cutscenes and at Lecterns |

### 2.5 HDMA channels and recipes

| Ch | Role | Uses |
|---|---|---|
| 0 | General DMA | Vblank streaming (VRAM, OAM, CGRAM) |
| 1 | CGRAM entry 0 | Box and menu gradient: #3058B8 → #303840, 16 steps of 4 lines |
| 2 | COLDATA ramp | Skies, fog density, Light tints, candle warmth |
| 3 | Window 1 edges | Candle and lantern pools, iris wipes, the Window, Mode 7 clipping |
| 4 | BG1 per-line H-scroll | Water, heat haze, Echo wobble, Labyrinth sine, Engine warps |
| 5 | BG2 per-line scroll | Parallax, rain skew, curtain wipes |
| 6 | Mode 7 matrix, else BG3 scroll | Perspective; fog drift |
| 7 | Register switcher (BGMODE, TM, BG2SC/BG3SC, BG12NBA) | Mode 7 / Mode 1 splits, the dialogue layer swap, Labyrinth seams, the Grand Concert split |

| Effect | Recipe |
|---|---|
| **Fog** | Two BG3 layers drift at 0.25 and 0.5 px per frame, half-added; ch2 ramps density from 25% at the horizon to 60% at the bottom |
| **Rain** | BG3 streaks scroll 3 px down, 1 px left per frame; ≤ 6 four-frame splash OBJs; puddles ripple ±1 px (ch4); lightning adds #F8F8F8 for 2 frames, decaying over 6 |
| **Candle flicker** | ch3 draws a 24–48 px ellipse per flame: colour math adds #302008 inside and subtracts #181820 outside; every 4–7 frames (random) the radius jitters ±1 px and the add steps between three levels; flame tiles cycle over 3 frames; two pools per line (Window 2 is lent to the dialogue box on its lines) |
| **Gradients** | Box fills (ch1); skies in 8–28 steps (ch2); Mode 7 horizon haze |
| **Water** | ch4 sine on reflections: 1–2 px, 16-line period, phase +1 per frame |
| **Chrono-Labyrinth** | ch4 sine of 0–6 px (32-line period) growing near each Clef; ch7 swaps BG12NBA at a drifting seam, so one map shows 1833 tiles above it and 2026 tiles below (a subway platform in the ossuary); mosaic 1 → 4 → 1 over 12 frames when a Clef is detuned; Seoul neon bleeds into one Paris ramp for 8 frames every 3 s; Mode 7 folds at zone exits |
| **Engine warp** (BOSS-28) | ch4 lens bulge at the Pedalboard's wells; the Right Manual's row flip mirrors BG2 for 12 frames |
| **The Window** (CH-17) | ch3 rectangle with a cold add (#6888B8 → #A8C0E0); BG3 snow rises at 0.5 px per frame (LAW-13) |

### 2.6 Mode 7

Mode 7 art is 8bpp, ≤ 256 tiles on a 1024 × 1024 plane, using **CGRAM 1–127 only** so OBJ palettes survive; with no BG3, HUDs are OBJs or a Mode 1 band switched in by ch7. Regular battles never use Mode 7.

| Use | Spec |
|---|---|
| Dirigible flight (W01, W02, CH-14+) | Mode 7 paintings of both overworlds; a Mode 1 sky band on lines 0–47; *La Lumière* is one large and two small OBJs |
| *La Lumière* finale flight (CH-E2) | The 2:30 river run (CANON §4f); Delorme's kite automata as OBJs |
| BOSS-27 The Stilled Hour | The dial as the plane, hands frozen at 00:43, turning 1° per second; clipped to the left 120 px; Mode 1 below line 152 |
| Labyrinth folds (P29) | 24-frame rotate-and-zoom between zones |
| The Door; the Window | The Door scales toward the camera (title, CH-P); Seoul's light rectangle scales out of the shards (CH-17) |

### 2.7 Constraint Lint

The asset pipeline rejects: (1) unsnapped colours; (2) palettes over 15 colours plus transparency, maps over 5 BG palettes, formations over 3 enemy palettes; (3) scanlines over 34 slivers or field cast over 24; (4) maps or formations that overflow the §2.2 VRAM map; (5) PC palettes without the fixed indexes; (6) field OBJ colour math; (7) Mode 7 art using colours ≥ 128; (8) full-screen flashes faster than 3 per second.

---

## 3. Colour Language

### 3.1 UI colours

| Token | Hex | Use |
|---|---|---|
| Window top / bottom | #3058B8 / #303840 | Box and menu gradient (CANON §16a: blue → dark grey) |
| Border / inner shadow | #F8F8F8 / #101828 | 2-px border, 1-px inner shadow |
| Text / text shadow | #F8F8F8 / #182030 | 1-px drop shadow, down-right |
| Key term `[C:gold]` | #F8D058 | Almanach terms |
| Aside `[C:grey]` | #A0A8B0 | Muttered asides |
| Disabled | #687080 | Greyed menu entries ("Not yet.", "Not mine to play.") |
| ATB fill / full | #F8F8F8 / #F8C838 | Gauge (combat_ensemble §2.2) |
| Crescendo | #F8B830 | Full bars glow |
| HP bar ok / low | #50C850 / #E84820 | Low = ≤ 25% (also blinks) |

### 3.2 Elements

| Element | Hex | Icon shape (8 × 8) | FX motif (§7.1) |
|---|---|---|---|
| FIRE (Vermilion) | #E83820 | Flame | Brushstroke flames on a *forte* |
| ICE (Cerulean) | #3890E0 | Hexagonal crystal | Glassy harmonics that ring, then shatter |
| WIND (Zephyr) | #88D0A8 | Spiral | Woodwind breath ribbons |
| EARTH (Ochre) | #C88830 | Square stone | Timpani stones |
| BOLT (Sforzando) | #F8E048 | Zigzag | A struck string snapping |
| WATER (Ondine) | #2858B8 | Droplet | Arpeggio ripples |
| LIGHT (Lumen) | #F8F0C8 | Four-point star | Gold leaf and lead-white rays |
| SHADE (Umbra) | #302040 | Half-filled circle | Lamp-black chiaroscuro wash |
| CHRONO (Tempus) | #E000F8 | Hourglass | Clock-hand sweep in the Wrong Colour |

### 3.3 Light States (CANON §10c)

Tints use colour math on BG1 and BG2, never on BG3 windows. Colour math cannot reach OBJ palettes 0–3, so party and field sprites get the same tint baked into CGRAM whenever the Light changes. Icons differ by **shape** (CANON §11j).

| Light | Tint (fixed colour) | Icon (16 × 16) |
|---|---|---|
| Dawn | Add #281808 at the top, fading to 0 at the bottom (ch2) | Half sun on a line |
| Noon | None: palettes as authored | Full disc, eight rays |
| Dusk | Add #381808 above the horizon, subtract #081018 below | Half sun under a line, down-chevron |
| Night | Subtract #283010 | Crescent |
| Candle | Pools: add #302008 inside, subtract #181820 outside | Teardrop flame |
| Fog | BG3 fog half-add (#A8B0B8) | Three wavy lines |
| Gloom | Subtract #202018; lantern pool if a light source is present | Arch with a downward triangle |

Under LUMIÈRE two Lights coexist: the icon splits into two half-icons and ch2 tints the left and right halves of the screen differently.

### 3.4 Narrative colour rules

- **The Violet Shadow Rule.** Lucile's first lesson is "colour in shadows" (CH-05). Exterior shadow ramps in Paris shift one step per act: Act I #403830 → Act II #403848 → Acts III–IV #383858 → CH-E2 #383060. In CH-E1, once Lucile paints Seoul at night, Seoul's cold shadows warm to #483858: she brings her eye to his city.
- **The Wrong Colour.** #E000F8 (partner cyan #00F8F8) appears in 1833 only in CHRONO effects, the Engine's chord, Unwritten, Archon's final forms, amalgam seams and CH-E1's static automata. In 2026 it is ordinary Hongdae neon.
- **The Hours** (CANON §5g): Velvet #A01828, Gold #C8A040, Iron #505860, Smoke #607088, the Almoner #F0F0F0, Archon #101018 with the sigil key in #D8B048, on masks, seals, ring glints and cabal rooms.
- **Lucile's paint flecks** follow her style: IMPRESSION rose and violet, POINTILLÉ the primaries alternating, IMPASTO cobalt and chrome yellow #F8D040, LUMIÈRE gold and violet.
- **Grief by absence:** black crepe, lime-wash #D8D8C8, chalked dates, empty chairs, ex-votos. No sick figure, ever.

---

## 4. Sprites and Portraits

### 4.1 Sprite cell and palette map

One OBJ palette per character, laid out identically for every PC so swaps, status tints and the fixed indexes (§2.3) work engine-wide.

| Index | Role | Index | Role |
|---|---|---|---|
| 0 | Transparent | 6–8 | Hair: light, mid, shadow |
| 1 | Outline #101018 (fixed) | 9–12 | Primary costume (4 steps) |
| 2 | Highlight #F8F8F8 (fixed) | 13–14 | Secondary costume |
| 3–5 | Skin: light, mid, shadow | 15 | Accent: the CANON §5g signature |

**Rules.** Key light from the upper left. Cloth: three values plus highlight. Selective outline (index 1 on the shadow side and against the background, the darkest costume step on the lit side); no anti-aliasing against transparency. Field eyes are 2 px tall, hands 3 × 3. Likenesses follow period images (Devéria's 1832 Liszt, Signol's 1832 Berlioz, Vigneron's 1833 Chopin); the appendix verifies attributions.

### 4.2 Character keys and costume sets

Sets follow CANON §5g and are chosen by chapter, never by tag. A **set** is the shared field list (§5.1) plus, if the costume fights, the shared battle list (§5.2).

| ID | Hook | Key ramps | Sets (chapters) |
|---|---|---|---|
| PC-01 | Coat tails; white sneakers until CH-05 | #F0C8A0 skin · #181820 hair · #283870 midnight blue | **Modern** (CH-P–CH-01: navy padded jacket, grey hoodie, black jeans, sneakers, tote) · **Frock** (CH-02–CH-04: bottle-green #305038 over the sneakers) · **Tailcoat** (CH-05–CH-17) · **Seoul** (CH-E1: black long padded coat, grey hoodie, midnight-blue scarf; the tailcoat for the premiere) · **Winter** (CH-E2 field: charcoal greatcoat) |
| PC-02 | Headscarf knot; brush roll at the right hip | #B85028 hair · #4058A8 scarf · #C89038 shawl · #808088 dress | **1833** · **Interlude** (CH-11–CH-12 solo: dark redingote, felt hat) · **2026** (cream coat #E8E0C8, red scarf #C82830) · **Winter** (CH-E2: grey wool pelisse) |
| PC-03 | Two tiles of red hair | #C84020 · #386840 · #F0F0E8 cravat | Green coat · **Wedding** (CH-09 field: borrowed black coat, cravat still askew) |
| PC-04 | Moustache; the vermilion V | #202028 · #D83820 | Dandy's coat |
| PC-05 | Rounded shoulders, curls | #282830 · #586878 | Black coat |
| PC-06 | Slim vertical; glove dots; violet | #887058 · #A8A8B0 · #8858B0 | Dove-grey coat |
| PC-07 | Long hair in motion | #E8D090 · #181820 · #C0C8D0 | Frock coat; MEPHISTO frames recolour the coat #382050 and silver #E000F8 |
| PC-08 | *Bandeaux*; folio | #302018 · #703050 · #182038 cuffs | Plum dress |
| PC-09 | Violin-case strap | #383840 · #803040 | Charcoal padded coat, burgundy knit |
| PC-10 | Beanie; sticks in a pocket | #D0A030 · #202020 | Mustard bomber with a samulnori patch |
| PC-11 | Loose cravat; slouch | #607088 · #C8C0B0 | Blue-grey café coat (ANA-03's art) |

**Cabal:** Archon in black with the sigil key on his watch-fob; Vane in crimson; Delorme in an ochre-gold gown; Brücke in a gunmetal apron (CH-E1: under a black 2026 parka); Marthe in the Daughters of Charity's grey-blue habit and white cornette. **CH-E2:** PCs get a winter layer on field sets only; outerwear comes off to fight.

### 4.3 NPC guidelines

- **Tier A/B** (CANON §16h): 32 × 32 cells, 3 drawn directions, 4-frame walk, 1–2 bespoke frames (Rossini eating, Sand's cigar, Corot at his easel, Pleyel inspecting an action).
- **Tier C townsfolk:** 16 × 32, 2-frame walk, from district ramps on OBJ palettes 4–5: Faubourg (workers' blue blouse #405880, ochre, brown), Bourgeois (black, bottle green, linen, rose), Seoul winter (black padding, beige, navy, red).
- **Trades by props:** the ragpicker's basket and hook, the water-carrier's yoke, the costermonger's barrow, the lamplighter winching a réverbère down at dusk, bouquinistes, a Savoyard sweep. National Guard and octroi agents are scenery or CH-01 hazards, never enemies (CANON §12).
- **Children** stand 22–26 px: Petit-Louis, Théo, Victorine, Solange, César Franck; Clara (14) a little under adult height.
- **Dignity:** the poor work, haggle and carry; no sight gags; orphans at work, never a misery tableau. **Seoul:** no brands, logos or K-pop iconography (CANON §16c); no civilian is ever an enemy.

### 4.4 Enemy guidelines

Enemies are BG1 graphics, as in FF6: silhouettes animated by 2-frame tile swaps, palette cycles and HDMA, leaving the OBJ palettes to the party.

| Class | Box | Palettes | Examples |
|---|---|---|---|
| S | 32 × 32 | 1 | Rats, Gaslight Wisps |
| M | 48 × 48 – 64 × 64 | 1 | Black Coats, Grey Hand, Ossuary Echoes, Mk. I automata |
| L | 96 × 96 – 128 × 96 | 1–2 | Hunter Automata, Tableau Echoes |
| Boss | ≤ 160 × 128; BG1 + BG2 over an HDMA backdrop; or Mode 7 | 2–3 | BOSS-28 Engine (seven oscillator columns palette-cycling); BOSS-27 (the Mode 7 dial) |

| Family | Art rule | Defeat |
|---|---|---|
| Echoes (every §12 Echo family) | Half-added, 1-px row wobble. **Images, never bodies:** bones only as ossuary masonry; Tocsin Echoes are gunsmoke and bells; BOSS-04 a choir stall and cope; BOSS-36 a violin throwing a broadside silhouette; BOSS-40 Voltaire's sarcophagus and the torch-bearing hand on Rousseau's tomb | Dust rising over 24 frames |
| Living Tableaux | Canvas-weave dither, gilt frame edges | Paint runs off |
| Automata | Brass, gunmetal, visible escapements; nitinol sheen #A898C0 | Springs burst |
| Static automata (CH-E1) | Shutter slats and Line 2 parts held by static in the Wrong Colour | Collapse to a dot |
| Humans and animals | Black Coats in ill-fitting second-hand coats; the Grey Hand's one grey kid glove (right hand) as a 2 × 3 px #B0B0B0 patch | Humans flee left or slump senseless under spinning stars, never bloodied; animals bolt |

### 4.5 Portrait spec

| Property | Spec |
|---|---|
| Size and depth | 48 × 48, 4bpp, 15 colours plus transparency (CANON §16a) |
| Hardware | 36 BG2 tiles on BG palette 7 during dialogue (§8.2); BG1 in menus (up to four at once) |
| Pose | Head and shoulders, three-quarter view facing right, toward the text |
| Light | Key light from the upper left at 45°; warm in 1833, cool in 2026; one fixed light per portrait, never per scene |
| Palette map | 1 outline · 2 white · 3–6 skin · 7–9 hair · 10–13 costume · 14–15 eyes and accent |
| Expressions | Face swaps: only the top 32 rows (24 tiles) change, so an expression costs one 768-byte upload |
| Costume busts | Chapter-picked busts swap the bottom 16 rows (12 tiles) |
| Framing | Transparent background over the box gradient; the outline never touches the cell edge |

### 4.6 Expression lists

Base set (CANON §16a): **neutral, smile, laugh, sad, angry, surprised, worried, determined, tender**; usage per dialogue_style_guide §3.

- **Tier A** (17 characters: PC-01–11, ANA-01–06 with ANA-03 sharing PC-11's art, FIC-01): all nine plus the canon extras Min-jun *homesick*, Lucile *guilty*, Berlioz *grandiose*, Alkan *deadpan*, Chopin *ironic*, Liszt *rapture*, Archon *cold* = **160 faces**. Busts: Min-jun 5, Lucile 4, Berlioz 2, Brücke 2 (1833, 2026), the rest 1 = **26**. Name tabs per CANON §16h.
- **Tier B** (43 characters): neutral, smile, grave and one bespoke expression (names from dialogue_style_guide §3.4) = **172 faces, 43 busts**: NPC-01 *shy* · 02 *intent* · 03 *cheeky* · 04 *wistful* · 05 *proud* · 06 *glare* · 07 *amused* · 08 *chuckle* · 09 *disdain* · 10 *pensive* · 11 *awed* · 12 *alarmed* · 13 *dreamy* · 14 *cigar* · 15 *inspecting* · 16 *pompous* · 17 *scowl* · 18 *aloof* · 19 *radiant* · 20 *proud* · 21 *giggle* · 22 *piercing* · 23 *genial* · 24 *wary* · 25 *harried* · 26 *fierce* · 27 *uneasy* · 28 *delighted* · 29 *cheerful* · 30 *wry* · 33 *savouring*; FIC-02 *scolding* · 03 *grin* · 04 *frightened* · 05 *flustered* · 07 *sneer* · 08 *steady* · 09 *squint* · 12 *astonished* · 13 *doubtful* · 14 *resolved* · 18 *gloat* · 19 *sweating*. Smithson's "Mme Berlioz" tab swaps text, not art.
- **Reserved:** 10 faces for the style guide's proposed Tier A extras and 8 for its proposed FIC-10/FIC-11 promotion, drawn only if those CCRs are adopted.

---

## 5. Animation Lists

Frame counts are unique drawn frames; timings are in frames at 60 Hz.

### 5.1 Shared field set (every PC, every costume set)

**40 frames per set:** stand 3 (down, up, left; right mirrored), walk 12 (4 per direction at 8 frames each), examine 3, nod and headshake 6, bow 4, kneel and sit 5, surprised 2, hand-hold 2, lean 2, lying 1. Dash reuses the walk at 4 frames each.

### 5.2 Shared battle set (every combat costume; facing left)

**26 frames per fighting set, facing left:** idle 2 (Liszt 3, for the hair), ready 1, step 2, fight 3, cast 3, item 2, defend/Tacet 2, hit 1, weak 1, Swoon 1 (never bloodied), victory 3, flee 2, Stagefright 2, Reverie 1. Marble, Frenzy and other tints are palette effects, not frames.

### 5.3 Per-character bespoke animations

| ID | Field bespoke (frames) | Battle bespoke (frames) | Cadenza | Sets F/B | Frames |
|---|---|---|---|---|---|
| PC-01 | `fallboard_tap` 3, `play_piano` 4, `phone` 2, `phone_throw` 4, `hum` 2, `conduct` 4 | *Resonance* 4; Recital sit 3, loop 4, II 2, III 3; break 2; CONDUCT 4 | *Gaspard Unbound* 6 | 5/4 | 351 |
| PC-02 | §5.4 (11) | §5.4 (24) | *Lever du jour* 6 | 4/4 | 305 |
| PC-03 | `conduct` 4, `grandiose` 2, `read_review` 2 | Cue 2, Tutti 3, lunge 2 | *Dies irae* 6 | 3/1 | 167 |
| PC-04 | `paint` 3, `sketch` 2, `cravat` 2 | CANVAS arc 4, Sketch 3, counter 2 | *La Liberté guidant* 6 | 2/1 | 128 |
| PC-05 | `play_piano` (pedal piano) 4, `read` 2, `tinker` 2 | Étude strikes 6, fail 1, brace 1 | *La Machine* 6 | 2/1 | 128 |
| PC-06 | `play_piano` 4, `mimic` 3, `cough` 2 (foreshadowing, ≤ 4 uses) | Borrow 3, Repay 3, *Tempo Rubato* 2 | *Warszawa* 6 | 2/1 | 129 |
| PC-07 | `play_piano` 4, `rapture` 2, `bow_audience` 2 | TRANSCEND 4, MEPHISTO 3, Transcribe 2 | *La Clochette* 6 | 2/1 | 130 |
| PC-08 | `play_piano` 4, `write` 2, `engrave` 2 | Annotate 3, Canon 2, Fugue 3, Cadence 3 | *Grand Tirage* 6 | 2/1 | 131 |
| PC-09 | `bow_violin` 4, `scowl_stomp` 2 | Sostenuto 4, Spiccato 4 | *Arirang Variations* 6 | 1/1 | 86 |
| PC-10 | `drum` 4, `pumped` 2 | BEAT 6, steal flourish 2 | *Encore Stage* 6 | 1/1 | 86 |
| PC-11 | `play_piano` 4, `sheepish` 2 | IMPROVISE 3, Blue Note 2 | *Changes* 6 | 2/1 | 123 |

Frames = bespoke + Cadenza + 40 per field set + 26 per battle set. **Party total: 1,764.**

### 5.4 Lucile's painting animations

| Animation | Context | Frames | Timing | Notes |
|---|---|---|---|---|
| `easel_setup` | Field | 3 | 8 | A pochade box unfolds from the brush roll |
| `paint` | Field | 2 (loop) | 12 | Wrist dab, palette on the left thumb |
| `step_back` | Field | 2 | 10 | Steps back, tilts her head |
| `sketch` | Field | 2 | 10 | KEY-09 and chalk |
| `fan` | Field (CH-03) | 2 | 16 | Seated, painting a fan |
| IMPRESSION | Battle | 3 | 6 / 4 / 8 | Load, two dabs, flick; each consecutive turn brightens the stroke a palette step (+20%, up to 5) |
| POINTILLÉ | Battle | 3 | 8 hits × 4 | Stipple loop; each hit spawns a Dot marker |
| IMPASTO | Battle | 4 | 10 / 6 / 12 / 8 | Knife charge, heavy smear, hold as the screen dims to Night, recover |
| *Nuit étoilée* | Battle | 6 | 4, two spins | Swirling brush; 8 LIGHT/SHADE hits |
| LUMIÈRE | Battle | 4 | 8 | A warm and a cool brush cross, then open |
| *Shift the Hour* | Battle | 4 | 8 | The raised brush sweeps an arc across the sky; palettes lerp over 32 frames |

### 5.5 Field animation registry, emotes and the lean

`{ANIM:ID:name}` registry (dialogue_style_guide §2.4): `fallboard_tap` (MJ: the hand lifts and taps twice, the game's first frame and the portrait's gesture, LAW-26) · `play_piano` (six PCs; Tier B pianists in 2 frames) · `paint` (LU, DE; Corot in 2) · `conduct` (MJ, BE) · `whittle` (Théo: knife, shaving, inspecting the fused-hands key) · `mimic` (CH) · `cigar` (Sand, with a smoke OBJ) · every bespoke name in §5.3–5.4.

**Emotes:** 16 × 16 balloons on palette 6, 40 frames: `!` `?` `...` `note` `sweat` `vein` `idea` (a candle flaring, never a bulb) `zzz` `tear` `sparkle` (only for the two kisses, the Window, the CH-E2 proposal and the Bosingak promise). No heart.

**The lean** (CANON §16f): the paired Lean frames close 8 px over 20 frames, the screen fades to black over 60, and eight sparkles twinkle over LM-22. Nothing more is drawn.

### 5.6 Guests and escorts

Guests (CANON §6) get a 13-frame battle set (idle 2, command 3, step 2, hit, weak, Swoon, victory 2) on a Tier B field set. Touches: Mathurin's lantern glow, Sand's cane, Corot's misty brush, Florestan and Eusebius as bright and dusk palettes on one sprite, Offenbach's six GALOP frames, Marthe's triage kneel, Thalberg's three-hand reach. Théo (CH-12 escort): walk 4, cower 1, a 2,000-HP bar.

---

## 6. Tilesets and Palettes by Location

### 6.1 Rules

A tileset fits the field budget (§2.2): ≤ 952 tiles, 5 BG palettes of 15, two animation banks of 32 tiles (flames, water, signage). Night map variants exist only for P02, P04, P10, P16, P22, P24 and P28 (CANON §11i); the three overworlds also get Dusk and Night palette shifts for night travel. Hex values below are the anchor colours of each set.

### 6.2 Tilesets (CANON §12)

| TS | LOCs | Anchor colours | Light · mood reference |
|---|---|---|---|
| TS-01 Annex and library | S01, S05, S10 hall (the tower climb borrows TS-21 gears) | #B8C0C0 wall · #687078 lino · #E8F0F0 tube | Fluorescent tubes · a 1962 annex after midnight |
| TS-02 Hidden Study | S02 | #B89048 brass · #483020 walnut · #F8E8A8 hum | The Door's seam · Hammershøi's still rooms |
| TS-03 Seoul streets | S03, S07, S11, S12, S13 exterior, W03 | #A09888 palace wall · #F8B058 sodium · #E030B8 / #30D8E8 neon | Lamps, LED, neon · SNES *Shin Megami Tensei*'s Tokyo |
| TS-04 Seoul interiors | S04, S06, S13, S15 | #C89868 ondol · #E0E8F0 LED · #A83830 hammer felt | LED over warm floors |
| TS-05 Euljiro and Line 2 | S08 | #00A848 Line 2 · #C8C8B8 tile · #606870 shutter | Platform LEDs · shuttered arcades |
| TS-06 Heights and river | S09, S14 | #F8C860 city lights · #182040 night · #403830 bare tree | The city below · Namsan, Yanghwajin |
| TS-10 Paris overworld | W01 (+ Mode 7) | #586070 slate · #506858 Seine · #B0A890 stone | Day sky, smoke · Turgot's plan (1739) |
| TS-11 Vieux Paris | P02, P07, P32; exteriors of P20, P21, P25, P36 | #505860 wet cobble · #F8C058 réverbère · #D8D8C8 lime-wash | Réverbères on ropes · Shotter Boys (1839), Hugo's ink washes |
| TS-12 Boulevards, passages | P03, P10, P16, P09 exterior | #F8D878 gas jet · #98B0B8 glass roof · #305840 shopfront | Passage gaslight · Canella's boulevards |
| TS-13 Hôtels particuliers | P14, P15, P23, P34, P39, R02 interior | #D8B860 mirror gilt · #E0D8C0 boiserie · #902030 damask | Chandeliers · Eugène Lami's interiors |
| TS-14 Salons, musical homes | P05, P11, P19, P36 interior | #C0A050 flaking gilt · #602818 rosewood · #8858B0 violets | Candelabra · Biedermeier room portraits |
| TS-15 Garrets, tavern, dispensary | P04, P20, P21, P37; E04 variant | #403028 smoke-brown · #F0C070 tallow · #E8E8E0 linen | Tallow, one skylight · Drölling's *Kitchen* (1815) |
| TS-16 Studios | P06, E02, E05 | #C8D0D8 north light · #A87838 turpentine · #B83828 silk | North light · Vernet's *Studio* (c. 1820) |
| TS-17 Louvre and Salon | P13, E01 | #783028 wall · #C8A048 gilt frame · #D0D8E0 skylight | Skylights · Morse's *Gallery of the Louvre* (1831–33) |
| TS-18 Halls, theatres | P09 interior, P12, P27, P35 | #A02030 velvet · #F8D070 footlight · #302820 rafters | Gas footlights · Lami's Opéra scenes |
| TS-19 Quarries, crypts | P01, P26 below, P38, P30, E03 | #B8B098 limestone · #F8B048 lantern · #D8E8F0 Clef glow | Lanterns, Gloom · Héricart de Thury (1815); Piranesi for the Heart |
| TS-20 Sewers, cellars, depots | P03 undercroft, P04 cellars, P17, P31 | #405838 slime · #784838 brick · #284040 water | Lanterns through grates |
| TS-21 Clockwork, forge | P18, R02 forges, the Engine dais | #C89838 brass · #505860 gunmetal · #F87828 forge | Forge mouths · Jaquet-Droz, Wright of Derby |
| TS-22 Quays, Montmartre | P22, P24 | #C8C8D0 dawn mist · #607870 river · #D8C8A8 mill sail | Open sky · Turner's *Wanderings by the Seine* (1834–35) |
| TS-23 Monuments | P25 interior, P26 above, P28, P32 interior, P33 | #C8C0A8 Panthéon stone · #182048 night · #4860A0 Mignard blue | Day, candles, stars · Mignard's dome (1663) |
| TS-24 Barricade | P08 | #686860 paving · #A0A0A0 gunsmoke · #C83028 flag | Noon through smoke · Daumier |
| TS-25 Chrono-Labyrinth | P29 | #B8B098 Paris · #E0E8F0 Seoul · #E000F8 seam | TS-19 fused with TS-01, TS-03, TS-05 (§2.5) |
| TS-30 France and Rhine | W02 (+ Mode 7) | #507038 poplar · #C0A878 post road · #486880 river | Day sky · Turner's Rhine |
| TS-31 Forest and Berry | R01, R03, R04, R05 | #E0E0D0 birch · #C08830 October · #F89838 hearth | October sun, Nohant's fire · Corot at Fontainebleau |
| TS-32 Rhine towns | R06, R07, R10, R13, R14 | #707070 coal smoke · #B06850 sandstone · #283860 Prussian blue | Customs lamps · Cologne's unfinished cathedral |
| TS-33 River and coast | R08, R09, R11, R12 | #E8E8E8 steam · #585048 slate cliff · #E8E8D8 chalk | Steam, sea light · Bonington's Normandy |

### 6.3 Seoul 2026 in 16-bit

- **Inverted light:** cold sources (LED #E0E8F0, tubes, phone glow) on warm interiors (ondol #C89868, food steam). Paris animates only fire, water and smoke; Seoul animates everything: signage, traffic lights, platform displays.
- **Same hand:** the 1833 outline weight, grid and palette budget; gradients only by HDMA; cars and scooters as moving tiles; trains as a scrolling BG2 band (BOSS-29's train every 4 turns).
- **Hangul signage is art,** legible to Korean readers and translated on examine; in Lucile's point-of-view scenes Korean addressed to her stays untranslated (CANON §16c).
- **Snow** falls on BG3 at 0.5 px per frame with foreground flakes on OBJs; Dongji *patjuk* steams in the Kang kitchen.
- **No brands, logos or idols;** shops have invented names (Haneul Mart). Hongdae's neon is the Wrong Colour at peace (§3.4).

### 6.4 The Paris-epilogue palette shift (CH-E2, Dec 1833 – Mar 1834)

CH-E2 reuses the Paris maps in winter palettes, applied as palette tables and one snow overlay bank:

| Change | Spec |
|---|---|
| Shadows | Full violet (#383060 / #504878): the end of the Violet Shadow Rule |
| Snow | Roof, sill and parapet overlay tiles on BG2; packed snow #D8E0E8 on streets in Jan–Feb, slush #888890 in late Feb |
| Seine | Pewter #788890 with ice edges #C8D8E0 |
| Light | Short days: window glow #F8C878 smaller and warmer; Dusk comes earlier on every map |
| Lecterns | Amber #D89838, one brightness step dimmer after each major beat; one goes dark per beat (CANON §11h) |
| E02 Atelier | Bare (one easel, no piano) or restored (skylight, Pleyel, Delacroix's spare easel), with morning light #F8E8C8 on both easels |
| E03 Dead Heart | Desaturated TS-19; Archon a living statue mid-gesture; nothing moves but one eye pixel, which glints every 600 frames |
| E04 *Le Diapason Bleu* | TS-15 with blue-grey walls #607088 (the Hour of Smoke, retired) and candle pools on every table |

### 6.5 Showcase plates (Mode 3, 256 colours, no sprites)

| Plate | When | Notes |
|---|---|---|
| *Le Pont Royal, effet de brume* | CH-06; CH-E1 exhibition | Label per branch (LAW-21) |
| *La Nuit étoilée sur le Panthéon* | CH-14 | The swirl animates on a Mode 1 copy before the plate settles |
| *Le Frère de demain*, Seoul | CH-E1, 31 Dec, 23:00 | Candlelit room, piano, figure in shadow with the right hand lifted to tap the fallboard, 민준 on the painted score, a window of stars in broken touch, at its edge a woman with a brush dissolving into light (LAW-26) |
| *Le Frère de demain*, Paris | CH-E2 coda | The same room, Lucile clear at the window, looking at the viewer |
| Reverses; the plaque | After each front; CH-P | LAW-26's inscriptions and "Pour M., qui doit venir. — Les Amis, 1886", lettered as art |

A Mode 7 zoom on a 128 × 128 crop brings the music stand close until 민준 is legible.

---

## 7. Special Effects

### 7.1 Elements and tiers

Element motifs and colours are §3.2. Effects scale with the PWR tier (CANON §10b): **T1** one OBJ burst, 16–24 frames · **T2** adds a BG3 layer · **T3** adds an HDMA distortion (ripple, haze, shear) · **T4** adds full-screen colour math · **T5** adds mosaic and a palette inversion beat. BOLT and lightning flashes last 2 frames (1 frame at half strength under Reduce Flashes, §10).

### 7.2 Command and set-piece effects

| Effect | Spec |
|---|---|
| RECITAL | A translucent spectral piano (palette 5) fades in; Movement I lights the aura ring, II sends notes rising, III bursts; a break shatters it into eight falling notes |
| Tutti | Section silhouettes rise on BG3 in cue order; *Cacophony* jumbles them |
| CANVAS | A two-pigment arc; named pairings flash a still of the canvas they quote |
| *Shift the Hour* | Palettes lerp over 32 frames; the Light icon turns like a dial |
| RUBATO | Borrow pulls a pale thread from an enemy's ATB bar; Repay threads it into an ally's |
| MEPHISTO | Liszt's palette darkens and his backdrop shadow grows horns of smoke for 12 frames: an image, not a demon |
| Synergy, Cadenza | Full-width banner (≤ 30 characters); a Cadenza dims the screen to 50% with the user lit, a gold rim for confidants. SYN-13 never shows the portrait (LAW-26) |
| Octave (BOSS-27) | Each Voice lights one note of the D-to-D staff in its accent colour; Lucile's D resolves the chord and the dial cracks into eight shards |
| Remembrances (CH-E1) | The keepsake glows and the friend appears as a brushstroke sketch in their colour key: a memory, painted, never a ghost |
| Rifts, Lecterns | A 2-px door-shaped seam cycling white-gold inside a ±1-px ripple; Lecterns glow on a 4-frame cycle |

### 7.3 Status visuals

Palette effects: Marble (greyscale), Frenzy (red pulse), Varnish and Glaze (sheen cycle), Unwritten (a vertical scanline wipe leaves a dotted outline in the Wrong Colour). Motion effects: Allegro (afterimage trail), Lento (slow bob), Swing (1-px jitter), Fermata (frozen with a fermata glyph), Stagefright (cower frames). Markers: Hush (barred note), Reverie (`zzz`), Coda (countdown digits), Miasma (a drifting grey-green haze icon; never a sick face), Encore (a gold note overhead), Composed (enemy flashes white every 30 frames).

### 7.4 Transitions

| Transition | Spec |
|---|---|
| Regular battle | "Staff wipe": five horizontal bands shear apart (ch4), then mosaic 1 → 15 over 16 frames; 24 frames total |
| Boss battle | Piano-cluster hit, white flash (2 frames), mosaic over 32 frames |
| Echo battle | Ripple wipe from the Echo's position |
| Duel | Two curtain halves close and reopen (Window 1 and 2) |
| Map change | 16-frame brightness fade |
| Flashback | `{TINT:sepia}`: CGRAM converted to a sepia ramp over a 24-frame crossfade |
| Caption | Centred, no box, upper third, 120 frames (dialogue_style_guide §1.3); place on line 1, date on line 2 |

---

## 8. UI Screens

### 8.1 Window style and screen index

Windows use §3.1: gradient fill, 2-px border with a 1-px corner cut, 1-px inner shadow, unrolling in 6 frames. The cursor is the white gloved hand (16 × 16), bobbing 2 px every 16 frames; Heat shows as candle pips (`|` in mockups). **Mockups use the 32 × 28 tile grid (one character = 8 × 8 px); real text is variable-width, so mockup text is schematic.** IDs: UI-01 Title · UI-02 Dialogue · UI-03 Main menu · UI-04 Status · UI-05 Equip · UI-06 Opus · UI-07 Harmony and Repertoire · UI-08 Secrecy HUD · UI-09 Bonds · UI-10 Salon · UI-11 Duel · UI-12 Battle · UI-13 Grand Concert · UI-14 Save · UI-15 World map · UI-16 Other screens.

### 8.2 Dialogue box (UI-02; CANON §16a, binding)

| Element | Pixels |
|---|---|
| Box | 240 × 64 at x 8–247; y 152–215 (bottom) or 8–71 (top, when the speaker stands low) |
| Frame | 2-px border #F8F8F8, 1-px inner shadow #101828, gradient fill #3058B8 → #303840 |
| Portrait | 48 × 48 at box x 8–55, box y 8–55 |
| Text, with portrait | Box x 59–232 (174 px): **3 lines × 24 characters**, 16-px pitch, line tops at box y 8, 24, 40 |
| Text, no portrait | Box x 7–232 (226 px): **4 lines × 30 characters**, 12-px pitch, tops at 8, 20, 32, 44 |
| Name tab | x 16, y 136–151 (above the box's top-left edge); width = name + 12 px (≤ 117 px for 15 characters) |
| Advance ▼ | Box x 226–232, y 57–61; blinks 30 / 30 frames; absent on auto-advance boxes |
| Choice window | Right edge x 247, bottom y 135 (clear of the tab); 16 px per option; for `[SLIP]` the hand starts on the period option |
| Slip timer | 4-px bar on box y 57–60 draining 226 px over 180 frames (3 s) |

**Build.** BG3 draws frame, tab and VWF text (F1, §9). Inside the box Window 2 masks BG1 and OBJ so the backdrop shows, and ch1 rewrites it into the gradient; on the box's lines ch7 switches BG2 to the portrait map (palette 7) and BG3 from weather to text, so rain stops at the frame. A top box hides the candle. **In battle** BG2 is the backdrop, so `[P:]` shows the name tab only, in a top box without a portrait.

```
   01234567890123456789012345678901
17   ┌───┐
18   │???│
19  ┌┴───┴───────────────────────┐
20  │┌────┐ Rain has no outline. │
21  ││    │                      │
22  ││ 48 │ Six times today I've │
23  ││ px │                      │
24  ││    │ painted this street. │
25  │└────┘                     ▼│
26  └────────────────────────────┘
```

Raw: `[P:PC-02:worried] Rain has no outline. Six times today I've painted this street.` (CH-04 tavern; her tab reads "???" until she gives her name, CANON §16h.)

### 8.3 Title screen (UI-01)

```
┌────────────────────────────────┐
│                                │
│   HARMONIES OF THE LOST ERA    │
│   Harmonies de l'ère perdue    │
│                                │
│           ┌───┬───┐            │
│           │ 1 │ 5 │            │
│           ├───┼───┤            │
│           │ 2 │ 6 │            │
│           ├─(7:51)┤            │
│           │ 3 │ 7 │            │
│           ├───┼───┤            │
│           │ 4 │ 8 │            │
│           └───┴───┘            │
│                                │
│            New Game            │
│          ► Continue            │
│            Config              │
└────────────────────────────────┘
```

The Door in candle-dark, its dial at 7:51. As MUS-001 plays LM-01, panels 1–7 light in note order (baton, sword-cane, rapier, hammer, quill, sabre, folio) and stop on C♯ with **panel 8, the brush, dark**. After either ending it lights (Lucile's D resolves LM-01) and the menu adds **Reverie of the Window** and **Da Capo** (LAW-23). Start sweeps the dial to XII and the Door opens in Mode 7.

### 8.4 Main menu (UI-03)

```
┌──────────────────┬───────────┐
│┌────┐ Min-jun    │►Items     │
││    │ Lv 19      │ Harmony   │
││ 48 │ HP  732/732│ Repertoire│
││    │ INS 100/100│ Equip     │
│└────┘            │ Opus      │
│┌────┐ Lucile     │ Ensemble  │
││    │ Lv 19      │ Bonds     │
││ 48 │ HP  675/675│ Status    │
││    │ INS 100/100│ Sketchbook│
│└────┘            │ Almanach  │
│┌────┐ Chopin     │ Config    │
││    │ Lv 19      │ Save      │
││ 48 │ HP  556/556│           │
││    │ INS 114/114│           │
│└────┘            │           │
│┌────┐ Liszt      │  ,  31    │
││    │ Lv 19      │  #        │
││ 48 │ HP  675/675│  =        │
││    │ INS 100/100│ Murmured  │
│└────┘            │           │
├──────────────────┴───────────┤
│Palais-Royal · Sat 21 Sep 1833│
│CH-08     14:02:31     6,240 F│
└──────────────────────────────┘
```

Order per CANON §16h; CH-08 anchor values (Chopin shows Sotto Voce's −10%). Save greys out away from Lecterns and overworlds; CH-E1 adds **Phone**. Money fields hold 10 digits. Chapter titles appear only on the save screen, never as captions (Tone Rule 6).

### 8.5 Status (UI-04)

```
┌──────────────────────────────┐
│┌────┐ Lucile           Lv 11 │
││    │ Chromomancer           │
││ 48 │ HP   355/ 355          │
││    │ INS   58/  58          │
│└────┘ EXP 3,981  Next 1,119  │
├──────────────┬───────────────┤
│ STR   15     │ Fight         │
│ ART   22     │ Plein Air     │
│ DEF   11     │ Harmony       │
│ RES   17     │ Item          │
│ TMP   23     │ Passive       │
│ LCK   18     │  Plein Air    │
│ ATK   36     │ Opus          │
│ EVA    0%    │  (none)       │
│ M.EVA  0%    │               │
├──────────────┴───────────────┤
│ Secrecy 31 · Murmured        │
└──────────────────────────────┘
```

Lucile joining at Lv 11 (CANON §5b base stats; a Nocturne-tier brush). The footer gives the exact Secrecy value (secrecy_and_trust §2.7); a second page shows gear affinities as §3.2 icons.

### 8.6 Equip (UI-05)

```
┌──────────────────────────────┐
│ Delacroix              Lv 16 │
├──────────────────────────────┤
│►Weapon  Prélude Rapier       │
│ Head    Prélude Hat          │
│ Body    Nocturne Coat        │
│ Relic   Cartouche Glove      │
│ Relic   (empty)              │
├────────────────┬─────────────┤
│►Nocturne Rapier│ ATK  30 ► 41│
│ Prélude Rapier │ DEF  29   29│
│ Étude Rapier   │ RES  29   29│
│                │ EVA  5%   5%│
├────────────────┴─────────────┤
│ Fire and wind ride the blade.│
└──────────────────────────────┘
```

Gains ▲ #50C850, losses ▼ #E84820. Names (≤ 16 + an 8-px icon) follow the CANON §14 pattern; head, body and description are illustrative (items_and_equipment owns names).

### 8.7 Opus (UI-06)

```
┌──────────────────────────────┐
│ Opus Scores           14/32  │
├──────────────────────────────┤
│►✦La Mer          |||   [MJ]  │
│ ✦La Valse        |||   [LI]  │
│ ✦Daphnis et Chloé|||   [LU]  │
│ ✦Classical       |||   [CH]  │
├──────────────────────────────┤
│ Invocation  La Mer   Heat 3  │
│ Level-up    ART +1           │
│ Swell of Tide  ×5  ████ 100% │
│ Undertow       ×3  ██░░  62% │
│ Spindrift      ×1  ░░░░   8% │
└──────────────────────────────┘
```

✦ = Future Score (OPS-13–24); Invocation Heat pips redden with Onlookers; head icons mark the equipper. Skill names are illustrative (skills_and_progression owns HRM names).

### 8.8 Harmony and Repertoire (UI-07)

```
┌──────────────────────────────┐
│ Repertoire  Min-jun   INS 41 │
├──────────────────────────────┤
│ Resonance                 6  │
│ Arirang                   6  │
│ Arabesque No. 1      ||  10  │
│►Clair de lune       |||  12  │
│ Jeux d'eau          |||  12  │
│ Reflets dans l'eau  |||  12  │
│ Prelude in C♯ minor |||  12  │
│ Étude in D♯ minor   |||  12  │
│ Ondine             ||||  14  │
├──────────────────────────────┤
│ Debussy · Suite bergamasque  │
│ I Cantabile  II LIGHT +25%   │
│ III Party heal               │
└──────────────────────────────┘
```

A CH-07 list; Movement I costs 6 + 2 × Heat (CANON §10b); with Onlookers the pips redden and the projected gain prints. REP titles run to **22 characters** (short forms in the final section). In CH-E2 future pieces grey out at salons: "Not mine to play." **Harmony** uses two columns (≤ 16 + element icon + INS). In battle both lists open full-width (256 × 72).

### 8.9 Secrecy HUD and its successors (UI-08)

```
 Paris field (top right)   Seoul, CH-E1            CH-E2
      +5                   ┌───────────────────┐   ┌──┐
      ,                    │▓▓▓▓│▓▓░░│░░░░│░░░░│   │▓▓│ 17/19
      #                    └───────────────────┘   └──┘
      #                     Trending                Ledger
     [=] 31 Murmured (while Select is held)
```

| Tier | Flame (height and motion first, colour last) |
|---|---|
| Incognito 0–19 | 4 px, steady, white-gold #F8F0B0 |
| Murmured 20–39 | 6 px, flickering |
| Watched 40–59 | 9 px, amber #F8A830, smoke wisp |
| Hunted 60–79 | 11 px, red-orange, wax running |
| Compromised 80–99 | 8 px guttering, red halo #E84820 pulsing at 1 Hz |
| Unmasked 100 | Flares to 14 px white, then blows out (cutscene) |

At (232, 4) on Paris maps from CH-02 (CANON §16h); variants and silent gains per secrecy_and_trust §2.7. **Spotlight** (CH-E1): a 64 × 8 bar at (184, 8), ticks at 25/50/75. **Canvas Ledger** (CH-E2): a gilt frame and "17/19"; its menu page shows 19 thumbnails, lost canvases as an empty frame on a nail.

### 8.10 Bonds: the Trust Network (UI-09)

```
┌──────────────────────────────┐
│ Bonds         Evenings left 2│
├──────────────────────────────┤
│►Lucile   ♥ ●●●×××····   480  │
│ Berlioz    ●●●●●●●···   600 a│
│ Delacroix◆ ●●●●●●●●●●  1000 a│
│ Alkan      ●●●●●●····   440  │
│ Chopin   ◆ ●●●●●●●●●●  1000 a│
│ Liszt      ●●●●······   230  │
│ Farrenc    ●●●·······   150  │
├──────────────────────────────┤
│ Lucile · Fractured           │
│ Her trust is capped at R3.   │
│ It will not grow until it    │
│ mends.                       │
│ The Hours of Light ▸ Noon    │
│ Sketchbook ▸ last page       │
└──────────────────────────────┘
```

CH-10. Pips: ● earned, × earned but capped, · unearned; ◆ confidant; "a" away. Lucile's heart shows a crack while Fractured (CANON §11f). The pane lists the next unlock, known gifts, the bond quest's next part and Synergies, and never previews story. "Tell the truth" sits in the Talk menu, greyed "Not yet." below R10.

### 8.11 Salon performance (UI-10)

```
┌──────────────────────────────┐
│┌────┐ Mme Lavergne   Tier 2  │
││ 48 │ Taste  Romantic        │
│└────┘ Fee    60 F × Rapture  │
├──────────────────────────────┤
│ 1 Jeux d'eau       ||| Ravel │
│   ► Name the composer   ×2   │
│ 2 Jeong-dong Nocturne        │
│ 3 Pathétique, II             │
├──────────────────────────────┤
│ Secrecy  +6 to +20  (masks ?)│
│        ► Perform    Change   │
└──────────────────────────────┘
```

The range spans Cabal Presence 0–3 (Heat 3 × (1 + presence) × 2, capped at +20, CANON §11g). Attributions: *Name the composer*, *An old teacher's piece*, *My own* (until the Vow). Own Voice is never shown.

```
┌──────────────────────────────┐
│ Jeux d'eau            Rapture│
│ ▓▓▓▓▓▓▓▓▓▓▓▓░░░░░░░░    62   │
├──────────────────────────────┤
│   ║     <   L        >  R    │
│ ──╫──(A)───────(X)──────(B)──│
│ ──╫─────────(Y)──────────────│
│ ──╫───────────────(A)────────│
│ ──╫──────────────────────────│
│   ║ Bravo!                   │
├──────────────────────────────┤
│  o  o  M  o  o  o  M  o  o   │
└──────────────────────────────┘
```

*Phrase*: prompts scroll onto the hit line, face buttons on the beats, L/R hairpins for dynamics; masked guests (M) appear once the playing starts; the hostess reacts every 8 beats; Rehearsal Mode adds an R badge.

### 8.12 Piano Duel (UI-11)

```
┌──────────────────────────────┐
│ Passage 3/8   ┌────┐ Rossini │
│               │ 48 │         │
│ -100 ░░░░░▓│░░░░░░░░░░ +100  │
├──────────────────────────────┤
│ Thalberg            Min-jun  │
│ ████████░░ 1,140   ███████░░ │
│            BRAVURA           │
│   CANTABILE   ?   PIANISSIMO │
│            ORNAMENT          │
│ Three-Hand Effect: THIS TURN │
├──────────────────────────────┤
│ ► Bravura    Pianissimo      │
│   Ornament   Cantabile   ?   │
└──────────────────────────────┘
```

BOSS-08: Favor opened at −20 (rigged) and stands at −12; Thalberg's Composure 1,140 / 1,500. Each type beats the next clockwise (Bravura > Pianissimo > Ornament > Cantabile > Bravura); "?" is Improvise; the three-hand icon lights every 3rd Passage; a shrinking ring times the input. **Variants:** Rhetoric (BOSS-20: Wit, Charm, Evidence, Silence) and Brushwork (BOSS-32: Light, Colour, Composition, Feeling, with the jurors' portraits).

### 8.13 Battle (UI-12)

```
   01234567890123456789012345678901
00 () ┌────────────────────────┐ , 
01 () │ Prelude in C♯ minor    │ # 
02    └────────────────────────┘ # 
03               o  o  o         = 
04               |  |  |   II      
05             ┌──┐       ┌──┐     
06             │BC│       │MJ│     
07             └──┘       └──┘     
08       .~~.              ┌──┐    
09       ~TE~              │BE│    
10       '~~'              └──┘    
11             ┌──┐         ┌──┐   
12             │BC│         │DE│   
13             └──┘         └──┘   
14 
15  . . . . . . . . . . . . . . . 
16 
17 
18             ▓▓▓▓▓▓│▓▓▓░░░│░░░░░░
19 ┌─────────────┬────────────────┐
20 │►Fight       │Min-jun     312 │
21 │ Orchestrate │ INS 41 ▓▓▓░░░░ │
22 │ Harmony     │Berlioz     380 │
23 │ Synergy     │ INS 45 ▓▓▓▓▓▓▓ │
24 │ Item        │Delacroix   350 │
25 │             │ INS 45 ▓▓▓▓▓░░ │
26 │             │                │
27 └─────────────┴────────────────┘
```

BOSS-05 waves (CH-04, Lv 10): Noon icon, Recital banner, Onlookers and the candle (shown only while an Onlooker remains), Black Coats (BC) and a Tocsin Echo (TE), Min-jun's Movement II marker, Crescendo at 150/300, Berlioz's commands over the enemy list. Sprites are drawn 3 rows high to avoid overlap (real cells: 32 × 32 on 24-px steps). Rectangles (combat_ensemble §2.1): battlefield 0, 0, 256 × 152; enemy list or commands 0, 152, 96 × 72; party window 96, 152, 160 × 72; Crescendo 96, 144, 160 × 8; banner 20, 4, 212 × 14. **Octave:** columns of four at x = 168 and 200, enemies in the left 120 px, the party window in two four-row panes, an eight-note staff for the Crescendo strip (CANON §16h).

### 8.14 Grand Concert split screen (UI-13)

```
┌STAGE─────┬RAFTERS───┬CORRIDOR┐
│MJ LI R46 │DE LU AL ►│CH FA Of│
│Mvt 2/3   │●●○ rec60%│Timer 8 │
└──────────┴──────────┴────────┘
  =====catwalk=====  |rope
 ┌──┐ ( ) ( ) ( )    |  ┌──┐
 │Br│ horn horn horn |  │DE│
 └──┘                |   ┌──┐
   [counterweight]   |   │LU│
                     |    ┌──┐
                     |    │AL│
```

The 24-px strip stays up through CH-13: Stage (Rapture), Rafters (the recording at 20% per surviving horn, max 80%), Corridors (BOSS-19's 12-turn timer); ► and three pips mark the active front, which plays below as a normal battle (the Stage as the duet duel). Switches are a 1.5-s rope-and-curtain wipe. **The eight-bar rescue** splits the screen at line 112 (ch7): Rafters above with Lucile cornered, the Stage below with Liszt covering alone; Min-jun's sprite drops from the lower half into the upper for his one action (combat_ensemble §11.2).

### 8.15 Save (UI-14)

```
┌──────────────────────────────┐
│ Save                 Lectern │
├──────────────────────────────┤
│►1 [MJ][LU][CH][LI]     Lv 19 │
│   The Sewers of Palais-Royal │
│   Palais-Royal · 21 Sep 1833 │
│   14:02:31           6,240 F │
│ 2 [MJ][LU][DE][FA]     Lv 35 │
│   The Night of Stars         │
│   Panthéon · 18 Dec 1833     │
│   30:12:44          48,900 F │
│ 3 [MJ][LU][SY][JW]     Lv 43 │
│   Seoul, 2026                │
│   Hongdae · 28 Dec 2026      │
│   36:05:10      ₩2,480,000   │
│ ◇ Eve of the Window    Lv 40 │
│   The Stilled Hour           │
│   Heart Chamber · 21 Dec 1833│
└──────────────────────────────┘
```

Three slots plus the permanent Eve of the Window (◇). A finished-epilogue slot shows the lit eighth panel and "Seoul" or "Paris". CH-E1 opens this screen in the phone's Notes frame, or at the S08 and S10 metronomes (CANON §11h).

### 8.16 World map (UI-15)

```
┌────────────────────────────────┐
│┌Pleyel: Salle and Workshop┐  , │
│└──────────────────────────┘  # │
│  Montmartre  ^^ mills ^^     = │
│ ·····toll wall·················│
│  ┌┐ ┌┐   [F]   ┌┐ ┌┐  ┌┐       │
│  └┘ └┘    @    └┘ └┘  └┘       │
│ ≈≈≈≈≈≈≈≈≈≈≈ Seine ≈≈≈≈≈≈≈≈≈≈≈≈ │
│   ┌┐  Cité ┌┐   ┌┐   ┌──────┐  │
│   └┘       └┘   └┘   │ mini │  │
│ Panthéon ┌┐  ┌┐      │ map  │  │
│          └┘  └┘      └──────┘  │
└────────────────────────────────┘
```

W01 on foot: the label appears when the leader (@) stands on an entrance; [F] is a fiacre stand (2 F); the 64 × 56 mini-map shows unlocked districts. **Flight** (CH-14+): the Mode 7 plane under a Mode 1 sky band, compass and mini-map as OBJs, and a sun or moon icon warning of the daytime take-off cost in Paris (+2, CANON §11e). W03 swaps fiacre stands for subway entrances.

### 8.17 Other screens (UI-16)

| Screen | Spec |
|---|---|
| Items | 256 slots sorted by class; key items in their own tab; prices under 1 F in sous ("Bread 8s", CANON §14) |
| Ensemble | Party of 4 + reserve, rows, 16 × 16 head icons |
| Sketchbook | KEY-09's last page as one of six chalk drawings on a 128 × 96 sepia page (Paris rooftops with Théo; the Pont des Arts at dawn; an unfinished page; a ship on a horizon; towers of glass in snow; Théo asleep under a blanket, LAW-23.5); Delacroix's 36 Studies in a grid |
| Almanach | Tabs: People, Places, Terms, Gazette, in period voice |
| Fine | "Retry battle" / "Return to last save" (CANON §11a) |
| Crypt-door prompt | Unfinished quests by title only, and "Turn back" (CANON §0c) |
| Window Clock | 12:00 at top centre in F3; pauses in dialogue and menus; amber at 3:00, red at 1:30 (CANON §11i) |
| Phone (CH-E1) | A 112 × 176 handset frame: Map, Messages, Camera, Translate, Music, Wallet, Notes (CANON §4f) |
| Piano-input puzzle (CH-P) | A one-octave strip: D-pad left, down, right, up play D, E, F♯, G; A, B, X, Y play A, B, C♯ and the high D; wrong notes cost nothing |

---

## 9. Fonts and Text Rendering

| Font | Cell and metrics | Use |
|---|---|---|
| F1 Dialogue | 8 × 12 VWF, advance ≤ 7 px incl. 1-px spacing (CANON §16a); roman and italic banks | Dialogue, captions, menu lists |
| F2 Small | 8 × 8 VWF, advance ≤ 6 px | Battle windows (14-character enemy names in 96 px), HUD labels, language badges |
| F3 Digits | 8 × 8 fixed; 8 × 16 bouncing damage digits on OBJ | HP, INS, prices, clocks, damage |
| F4 Display | Serif small caps, 16-px capitals | Title lettering, save-screen chapter titles, Synergy and Cadenza banners |
| F5 Hangul subset | 12 × 12, 14-px advance = 2 characters (CANON §16a) | `[K]…[/K]` runs in the English master |
| F6 Korean | 12 × 12, the 2,350 KS X 1001 syllables | Korean localisation |

**F1 metrics:** rows 0–1 hold accents on capitals, rows 2–9 cap height and ascenders, rows 5–9 x-height, rows 10–11 descenders; lower-case accents sit in rows 2–4, so É, Ç and Ż never clip. **Glyphs** (about 170 per bank): ASCII; French à â ç é è ê ë î ï ô ù û ü ÿ œ æ and their capitals, « » ’ “ ” … — –; German ä ö ü ß (Brücke, Düsseldorf, Kapitän); Polish ą ć ę ł ń ó ś ź ż Ł Ś Ż (*Żal*, *Żelazowa*); ♯ ♭ ♮; ✦, × and the 8-px candle glyph. Command names keep their accents in capitals (ÉTUDE, LUMIÈRE). **Rendering:** text is drawn into BG3 tiles in RAM and uploaded in vblank; lines break only at spaces; italics come from the italic bank, never bold. **Language badges** (`[in German]` and kin) are three-letter F2 small caps in a 20 × 8 pill at line start: GER, FRE, ENG, KOR, POL, LAT, HEB.

**Hangul.** F5 shares the VWF canvas; a run breaks only at spaces and is followed by italic Revised Romanization (CANON §16c). The subset holds **≤ 400 syllables**, of which 84 are seeded: 강민준 강서연 최재원 윤미래 오상우 박혜진 강도현 · 뤼실 오브레 · 괜찮아 오빠 교수님 엄마 동지 팥죽 별의 음악 한성음악원 한마디 · 서연에게 2026년 12월 22일 오후 5시 이후에 열 것 · 사물놀이 아리랑 정동 · 세마치 굿거리 자진모리 휘모리 · 꽹과리 징 장구 북 · 보신각 남산 홍대 인사동 을지로 양화진. The other 316 serve the 40 Hanmadi words and CH-E1 lines; each new syllable needs art sign-off. **Signage, handwriting and plates are art, not font:** Seoul signs, the KEY-39 letter, the drawn packet label and 민준 on the portrait never count against the subset (the label's syllables are seeded only because dialogue quotes it).

**Localisation.** French uses F1's accents and overflows into the 4-line box (CANON §1), with a 2-px thin space before ; : ! ?. Korean (F6) fits 3 lines × 12 syllables with a portrait and 4 × 16 without.

---

## 10. Accessibility

| Feature | Spec | Status |
|---|---|---|
| ATB speed 1–6, Active/Wait, text speed 1–5, Rehearsal Mode | CANON §11j | Canon |
| Shape coding | Light and element icons, candle height and motion, ATB glyphs, Heat as candle pips | Canon + this doc |
| Reduce Flashes | Full-screen flashes ≤ 1 per 2 s, 1 frame at half strength; Labyrinth neon bleed off | Proposed |
| Screen Shake | On / off | Proposed |
| Calm Distortion | Labyrinth wobble ≤ 1 px, no mosaic pulses, Engine warps at half amplitude | Proposed |
| Clear Text | Solid #182040 box fill; the scene behind the box dimmed 50% | Proposed |
| Sound Cues | Visual captions for gameplay sounds: an edge ripple pointing to a humming rift, BOSS-09's chime, a crosshair on Roussel's "Steady…", BOSS-29's train | Proposed |
| Timer Assist | Bite Your Tongue timer 3 → 6 s; timeout still plays the period phrasing | Proposed |
| Controls and output | Full remapping; positional button glyphs with platform letters; Flee as hold L + R or a toggle; integer scaling, 1:1 or 8:7 pixels, optional scanline filter (off) | Proposed |

---

## Canon Additions & Cross-Doc Notes

No canon value is changed. New shared facts:

- **Field walk speed 1 px per frame** (16 frames per tile); dash 2 px per frame on town and interior maps only, so `formulas_and_curves.md`'s encounter calibration holds. *Affects:* formulas_and_curves, dungeons, overworld_and_towns.
- **Doc-local IDs:** TS-01–06, TS-10–25 and TS-30–33 tilesets, UI-01–16 screens, F1–F6 fonts. *Affects:* overworld_and_towns, dungeons, writing docs.
- **Layer rules with design consequences:** enemies and wards are BG1 art; ≤ 3 enemy palettes per formation; field maps get 5 BG palettes (palette 7 holds the portrait); BOSS-27 is a Mode 7 dial and large bosses are BG art (as vision_and_pillars recommends). *Affects:* bestiary, bosses, dungeons, overworld_and_towns, combat_ensemble.
- **Battle text:** `[P:]` in battle shows the name tab only, in a top box without a portrait. *Affects:* dialogue_style_guide, bosses, scenario docs.
- **CCR (CANON §5g):** add colour keys for Seo-yeon (charcoal padded coat, burgundy knit), Jae-won (mustard bomber) and Julien (blue-grey café coat). New costume sets: Min-jun Seoul and Winter; Lucile Interlude (CH-11–CH-12, matching historical_cast's proposed disguise) and Winter; Berlioz's wedding coat; Brücke's 2026 parka. *Affects:* party, act3, epilogues, scenario prose.
- **Animation registry:** §5.3–5.5 add 22 `{ANIM:}` names to the style guide's seven, including Chopin's `cough` (foreshadowing only, ≤ 4 uses). *Affects:* dialogue_style_guide, scenario docs.
- **Colour rules:** the Violet Shadow Rule; the Wrong Colour #E000F8 reserved for CHRONO, the Engine and the static automata, the visual twin of the reserved synth patch (CANON §15a). *Affects:* audio_and_music, bosses, dungeons.
- **Title screen:** panels light in LM-01 order with MUS-001; the brush panel stays dark until an ending. *Affects:* audio_and_music, vision_and_pillars.
- **Chapter titles** appear only on the save screen, never as captions (Tone Rule 6). *Affects:* scenario docs.
- **Repertoire titles ≤ 22 characters;** short forms REP-04 "Doctor Gradus", REP-06 "Cathédrale engloutie", REP-12 "Pavane", REP-16 "Suite No. 2", REP-20 "Left-Hand Prelude", REP-26 "Prometheus", REP-27 'Concerto "Lost Era"', REP-28 "Harmonies". *Affects:* skills_and_progression, combat_ensemble, salons_duels_and_economy.
- **Hangul subset** seeded with 84 syllables (with the style guide's 뤼실 오브레); signage and handwriting do not count. *Affects:* dialogue_style_guide, epilogues, overworld_and_towns (Hanmadi).
- **Depictions:** BOSS-04, BOSS-36 and BOSS-40 as images (consistent with world_rules_and_lore's Echo-shape note); Remembrances as painted sketches. *Affects:* bestiary, bosses, epilogues.
- **CH-P piano-input mapping** (§8.17). *Affects:* prologue_and_act1.
- **Portrait reserve** for the style guide's CCRs (10 Tier A extras; FIC-10/FIC-11 at Tier B), drawn only on adoption. *Affects:* dialogue_style_guide, epilogues.
- **Money fields hold 10 digits,** enough for formulas_and_curves' proposed won cap (₩1,999,999,800). *Affects:* salons_duels_and_economy.
- **CCR (CANON §11j):** add §10's proposed options. *Affects:* combat_ensemble (its own options list), secrecy_and_trust (Timer Assist).
