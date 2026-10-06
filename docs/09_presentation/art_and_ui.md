# Art Direction & UI

Status: v1.0 — 2026-10-06 · Owns: resolution and hardware constraints, sprite and portrait specs, animation lists, tilesets and palettes, special effects, every UI screen, fonts and the hangul glyph subset, field walk speed · Depends on: none (canon only) · Canon: docs/00_CANON.md

> Where this doc restates the canon (CANON §1 platform, R-39 sprite cell, §5g visual key, §16a box, §16h UI), the canon is the source. Battle-screen geometry follows `combat_ensemble.md` §2 so the two docs never disagree; this doc adds the art behind it. Every hex value is **BGR555-snapped** (each channel a multiple of 8), so what the artist picks is what the hardware shows.

## Contents

1. [Art Direction: The Two Lights](#1-art-direction-the-two-lights)
2. [Hardware Constraints](#2-hardware-constraints)
3. [Colour Language](#3-colour-language)
4. [Sprites and Portraits](#4-sprites-and-portraits)
5. [Animation Lists](#5-animation-lists)
6. [Tilesets and Palettes by Location](#6-tilesets-and-palettes-by-location)
7. [Special Effects](#7-special-effects)
8. [UI Screens](#8-ui-screens)
9. [Production Budget](#9-production-budget)
10. [Canon Additions & Cross-Doc Notes](#canon-additions--cross-doc-notes)

---

## 1. Art Direction: The Two Lights

**Thesis.** The game is a quarrel between two ways of seeing, staged in pixels. Delacroix paints *subjects*: drama, dark grounds, a vermilion shout. Lucile paints *light*: the hour, the air, colour inside shadow (CANON §5e). The world art begins on Delacroix's side, with candle pools in dark rooms and grey fog on grey stone, and Lucile's eye slowly enters it. Seoul 2026 inverts the lighting: cold light sources on warm interiors where 1833 has warm light sources on cold streets. Both cities are drawn by one hand, at one outline weight, so the Chrono-Labyrinth's fusion reads as one world tearing, not two art styles colliding.

| # | Rule | In practice |
|---|---|---|
| A1 | **Every frame has a named light source.** | Each map lists its source (réverbère, gaslight, candle, skylight, LED, lantern) and its Light State (CANON §10c). No ambient-only rooms |
| A2 | **Colour is narrative.** | The Violet Shadow Rule, the Wrong Colour and the pitch colours (§3.5) carry story without a word of text |
| A3 | **Hardware honesty.** | 256 × 224, 15-colour sprite palettes, scanline limits, HDMA and Mode 7 are design disciplines (CANON §1); the engine's Constraint Lint (§2.9) rejects assets that break them |
| A4 | **Images, never bodies.** | Echoes take the shape of images, never of the dead (LAW-07); no corpses in sprites; cholera shown by absence: black crepe, empty chairs, lime-washed walls, ex-votos (CANON §16e) |
| A5 | **Read at a glance.** | Every gameplay state is legible by **shape and motion** as well as colour (CANON §11j); silhouettes are tested in a one-colour pass before any palette is assigned |
| A6 | **Period first, then romance.** | Architecture, clothes and objects are 1833 (or 2026) to the object (§6.3); the drama comes from light, never from anachronistic décor |

---

## 2. Hardware Constraints

### 2.1 Screen and background modes

| Item | Spec |
|---|---|
| Resolution | **256 × 224** (CANON §1), 16 × 14 tiles of 16 px |
| Field and battle | **Mode 1**: BG1 and BG2 at 4bpp (16-colour palettes), BG3 at 2bpp (4-colour palettes) for text, HUD, fog and rain; the "BG3 on top" bit set so dialogue covers the scene |
| Set pieces | **Mode 7** (one 8bpp rotatable layer, 128 × 128 tile map, ≤ 256 unique tiles) for the uses in §2.7 |
| Showcase plates | **Mode 3** (BG1 8bpp, up to 255 colours when no sprites share CGRAM) for the portrait *Le Frère de demain*, Lucile's key canvases, the Sketchbook's last page and the ending-roll vignettes (§6.6) |
| Pixel aspect | Native 8:7 pixels. Display option: **Square pixels** (default, integer ×3/×4/×5) or **4:3 CRT aspect** |

### 2.2 VRAM map (64 KB, field and battle)

| Range | Size | Contents |
|---|---|---|
| $0000–$7FFF | 32 KB | BG1/BG2 shared 4bpp tiles: **1,024 8 × 8 tiles = 256 16 × 16 metatiles per map** |
| $8000–$9FFF | 8 KB | BG1 and BG2 tile maps (64 × 32 each) |
| $A000–$B7FF | 6 KB | BG3 2bpp tiles (384): variable-width text canvas 240, box frame and name tab 24, fog and rain 64, HUD glyphs and the candle 40, spare 16 |
| $B800–$BFFF | 2 KB | BG3 tile map (32 × 32) |
| $C000–$FFFF | 16 KB | OBJ tiles (512 8 × 8 tiles); actor frames are streamed on change, never all resident |

All bases sit on legal boundaries (BG tile data on 8-KB steps, maps on 2-KB steps, OBJ on 16 KB). Menu screens replace the field and may repurpose the whole map.

**DMA budget per vblank:** 4 KB of tiles (eight 32 × 32 actor frames at 512 bytes), the full OAM (544 bytes) and up to 512 bytes of CGRAM, inside the ≈ 5.5 KB an NTSC vblank allows.

### 2.3 CGRAM (256 colours)

| Entries | Use |
|---|---|
| 0–31 | Shared by BG3's eight 4-colour palettes and the first two 4bpp palettes: **text box, HUD, weather** |
| 32–127 | **Six scenery palettes** (BG palettes 2–7: 90 colours per map) |
| 128–255 | **Eight OBJ palettes of 15 colours plus transparency** (CANON §1) |

**Ensemble palette pairing.** Compatible casts share one 15-colour palette, so the whole Octave fits in five: **P0 Min-jun + Julien · P1 Lucile · P2 Delacroix + Alkan** (black coats, dark hair; vermilion and slate accents) **· P3 Chopin + Liszt** (dove grey and black; ash-brown and fair hair; violet and silver) **· P4 Berlioz + Farrenc** (red hair and green coat; dark *bandeaux* and plum). In Seoul: P0 Min-jun, P1 Lucile, P2 Seo-yeon, P3 Jae-won.

**Field OBJ palettes:** 0–4 the pairs above · 5 one guest or named NPC (Théo, Sand, Marthe, the speaking Tier B figure; swapped between shots when a scene holds more) · 6 the speaking portrait (rewritten per speaker in vblank) · 7 shared: the map's crowd ramp (11 colours, §4.3) plus emotes and splashes (4). So the CH-17 farewells hold all eight friends, Julien and one more figure on screen at once. The Secrecy candle and other HUD glyphs live on BG3 (§8.11). **Battle OBJ palettes:** 0–3 one per active member (pair-mates simply load the same colours twice, so a status swap such as Marble greys one sprite only) · 4–5 enemies on OBJ · 6 spell effects · 7 shared (cursor, digits, overhead markers). **Octave formation (BOSS-27):** the eight members fill P0–P4, the Stilled Hour sits on BG, 5 carries effects, 6 the light pillars and staff (8 pitch colours plus a 5-step stone-grey ramp for a Marbled member), 7 digits and markers.

### 2.4 OBJ rules and the 32 × 32 sprite (R-39)

The brief's 32 × 32 sprites are authored in a **32 × 32 cell with a figure about 20 × 30 px on a 16 × 16 tile grid** (CANON R-39). On hardware this is exactly one **large OBJ**:

| Context | OBSEL size pair | Large OBJ | Small OBJ |
|---|---|---|---|
| Field | 16 × 16 / 32 × 32 | Actors (one OAM entry each, 16 tiles, 512 bytes per frame) | Emotes, props, portrait pieces, splashes |
| Battle | 8 × 8 / 32 × 32 | Party, OBJ enemies (M enemies = 4 large OBJs) | Damage digits, overhead markers, sparks |

- **Anchor:** the feet sit at cell pixel (16, 30) on the bottom-centre of the occupied tile; the cell overhangs the tile by 8 px left and right and 16 px up. Collision is the single 16 × 16 tile under the feet.
- **Depth:** actors are y-sorted in OAM every frame. Overhangs (eaves, arches, canopies, door lintels and posts) are **high-priority BG tiles**, so a 20-px figure passes "through" a 16-px door without a gap. Interiors draw doorways one tile wide with two-tile lintels.
- **Scanline ceiling:** 32 OBJ or 34 8-px slivers per line; a 32 × 32 actor costs 4 slivers. **Rule: ≤ 7 actors overlapping any 32-px horizontal band.** Crowds (salon guests seated, the Opéra house, the Salon of 1834, the New Year's Eve hall) are drawn on BG with 2-frame tile animation (fans, hats, phones).
- **OAM budget (128):** field actors ≤ 24 · emotes ≤ 4 · portrait 6 · effects ≤ 16 · weather splashes ≤ 8 · reserve 70. Battle: party 4 (Octave 8) + props ≤ 8 · OBJ enemies ≤ 24 · digits and markers ≤ 40 · effects ≤ 40.
- **Portrait cost:** in the field, one 32 × 32 + five 16 × 16 = 6 entries. In battle (8/32 pair), one 32 × 32 + twenty 8 × 8 = 21 entries, so scripted battle dialogue pauses the battle and hides digits while a box is open.

### 2.5 HDMA channel allocation

| Ch | Default use | Register(s) |
|---|---|---|
| 0 | General DMA (vblank VRAM, OAM, CGRAM uploads); never HDMA | — |
| 1 | Text-box fill gradient: one CGRAM rewrite per scanline | $2121/$2122 |
| 2 | Sky and Light gradient (fixed colour per scanline); in interiors, candle-flicker intensity | $2132 |
| 3 | Window 1 shape: candle pool, lantern radius, Watcher cone, iris wipe; in Mode 7 scenes, matrix A/D | $2126/$2127 / $211B, $211E |
| 4 | Window 2 shape: second pool or cone; the Window rectangle (CH-17); in Mode 7 scenes, matrix B/C | $2128/$2129 / $211C–$211D |
| 5 | BG1 horizontal scroll: heat shimmer, water ripple, Labyrinth wobble, battle transition | $210D |
| 6 | BG3 scroll bands (fog, rain) | $2111 |
| 7 | Layer and mode control: main-screen layers per scanline (Amalgam tear bands); mid-frame mode split (Mode 1 bands above or below a Mode 7 layer, so BG3 text and HUD survive) | $212C, $2105 |

### 2.6 HDMA and colour-math recipes

| Effect | Recipe | Limits |
|---|---|---|
| **Fog** | 2bpp dithered cloud tiles on BG3 (three greys), colour math *add-half*; three bands drift at 0.25, 0.5 and 0.75 px per frame (ch6), densest at the bottom third | Fog yields to the text box: ch6 zeroes scroll and math on box scanlines |
| **Rain** | BG3 streak tiles scrolling (−2, +6) px per frame; up to 8 splash OBJs (3 frames each); thunder adds white fixed colour for 2 frames, decaying over 6 (synchronised with `thunder`, audio_and_music) | Flash Reduction: half brightness, ≤ 3 flashes per second |
| **Candle flicker** | Interiors: ch3/ch4 draw circular windows (radii r−2, r, r+1 tables swapped every 4–9 frames at random); inside, colour math adds warm fixed colour (+3 R, +2 G in 5-bit steps), scaled by scanline distance from the flame (ch2); outside, a −1 B subtract cools the room | **≤ 2 light pools per screen**; further candles glow by palette cycling, without a pool |
| **Gradients** | ch2 feeds one fixed colour per scanline, added to the sky BG; a gradient is 8–14 bands per Light State (§3.3) | Painted Lights crossfade over 30 frames |
| **Lantern (Gloom)** | Dungeons: −3 R, −3 G, −2 B subtract outside a 48-px window around the leader (KEY-05), 64 px with Mathurin's LANTERN | Phone flashlight (KEY-02): a 96-px cone for 600 frames |
| **Watcher and patrol cones** | ch3/ch4 triangle tables rebuilt each frame from position and facing; translucent amber by night, pale by day | ≤ 2 cones on screen (1 in lantern-lit Gloom, where the lantern holds Window 1; further cones draw as dotted OBJ edges); dungeon and town layouts must respect it |
| **Chrono-Labyrinth distortion** | (a) **tear bands**: ch7 alternates BG1 (1833 stone) and BG2 (2026 overlay) in bands 2–8 px tall drifting down 1 px per frame; (b) **wobble**: ch5 sine table, amplitude 0–4 px, period 32 lines; (c) **mosaic pulse** 0 → 15 → 0 over 30 frames at zone seams (the brief's "pixelated amalgams"); (d) **Amalgam Flicker** (combat_ensemble §10.2): a 16-frame palette crossfade between Gloom and fluorescent Noon | Config: Distortion 0 / 50 / 100% |
| **Water** | ch5 sine ripple on reflection rows (amplitude 1 px), palette-cycled glints | — |

### 2.7 Mode 7 uses

| Use | Scene | Notes |
|---|---|---|
| Free flight | *La Lumière* over LOC-W01 and LOC-W02 (CH-14) | Lines 0–63 are a Mode 1 sky band (ch2 gradient, the candle on BG3), Mode 7 below (ch7 split); perspective by ch3/ch4 matrix tables; 4 × walking speed |
| Finale flight | CH-E2, Sat 1 Mar 1834: the 2:30 run over the Seine (CANON §4f) | Seine strip as a 1,024 × 1,024 map; kite automata as OBJ; hits drain the canvas bar shown under the HUD |
| **BOSS-28** the Engine | LOC-P30 | The Engine is the Mode 7 layer: the Right Manual's row flip rotates the arena 180° over 40 frames; Pedalboard gravity wells scale it to 1.3×. ch7 switches to Mode 1 at line 152 so the battle windows stay on BG3 |
| BOSS-25 *Ad Astra* | Heart gate, LOC-P29 | The Varga equation turns behind the boss on a rotating plane, one revolution per 3 turns (its stat rewrite) |
| Title screen | §8.5 | The Door zooms from 1.0× to 1.6× as the dial turns; logo and menu sit in Mode 1 bands above and below it |
| The crossing | End of CH-P | The dial face spins and shrinks to a point over 90 frames, then white |

### 2.8 Field movement and camera (owned value)

| Map type | Walk | Dash (hold B) | Note |
|---|---|---|---|
| Dungeons and mini-dungeons | **1 px per frame** (16 frames per tile) | None | The encounter calibration of formulas_and_curves §5.7 assumes exactly this |
| Towns and interiors | 1 tile per 10 frames | 2 tiles per 10 frames (Config: Hold or Always) | No random encounters there, so dash costs no balance |
| Overworld maps | 1 tile per 8 frames | None | As overworld_and_towns §1; Mode 7 flight 4× |

Walk cycle: one frame change per 8 px moved. Camera: leader centred, clamped at map edges; 16-frame lerp on scripted pans (`{CAM:}`); no zoom outside Mode 7 set pieces (dialogue_style_guide §2.4).

### 2.9 Output and Constraint Lint

PC and Switch builds run the accuracy-first renderer at 60 Hz (NTSC timing). **Constraint Lint** checks every imported asset and every map at build time and in a debug overlay: palette over 15 colours, a tileset over 256 metatiles, more than six actor palettes (five pairs and one guest) or seven actors in a band, more than two pools or cones, an OBJ over the vblank DMA budget, a hex value not BGR555-snapped, a hangul syllable outside the subset (§8.3). An asset that fails does not ship.

---

## 3. Colour Language

### 3.1 Master UI colours

| Token | Hex | Use |
|---|---|---|
| Box top | #2858B8 | Window gradient start (CANON §16a: blue → dark grey) |
| Box bottom | #303038 | Window gradient end |
| Border / text | #F8F8F8 | 2-px border, body text |
| Inner shadow | #101018 | 1-px inner line; text shadow in captions |
| Gold | #F8D048 | `[C:gold]` terms, full ATB, full Crescendo bar, selected tab |
| Grey | #A0A0A8 | `[C:grey]` asides, disabled entries ("Not yet.") |
| Warning | #F86040 | HP ≤ 25%, timers in their last 20% |
| Heal digits | #58E058 | HP restored |
| INS digits | #58A8F8 | INS restored or paid |
| Portrait well | #182040 | The opaque backing of every portrait |

### 3.2 Elements (spell FX and icons)

| Element | Flavour name | Key hex | FX motif |
|---|---|---|---|
| FIRE | Vermilion | #E04020 / #F8A048 | Brushstroke flames licking upward; brass-bell flare |
| ICE | Cerulean | #58A8E0 / #D8F0F8 | Glass harmonics: crystals that ring and split |
| WIND | Zephyr | #A0D888 / #F0F8E8 | Streaks and loose manuscript pages |
| EARTH | Ochre | #C89038 / #685028 | Timpani shock rings, paving stones heaving |
| BOLT | Sforzando | #F8E040 / #F8F8F8 | Struck-string forks, accent marks (>) |
| WATER | Ondine | #3070C8 / #88C8F0 | Arpeggio ripples, the Seine's reflections |
| LIGHT | Lumen | #F8F0C8 / #F8D048 | Gold-leaf flakes, lead-white bloom |
| SHADE | Umbra | #503068 / #181020 | Lamp-black ink blooms (subtractive math) |
| CHRONO | Tempus | **#F048D8 / #40F0E8** | The Wrong Colour (§3.5), clock hands, scanline tear |

### 3.3 Light States (CANON §10c)

Icons follow combat_ensemble §8.3 and differ by silhouette (CANON §11j).

| Light | Icon (16 × 16) | Sky top → horizon | Colour math |
|---|---|---|---|
| Dawn | Half-disc on a line | #485898 → #F8B898 | Add +2 R, +1 G; long violet shadows |
| Noon | Rayed disc | #5890D8 → #C8E0F0 | None; shadows short and neutral |
| Dusk | Half-disc over a chevron | #383060 → #E87848 | Add +3 R, +1 G |
| Night | Crescent and star | #081028 → #283058 | Subtract −2 R, −2 G; réverbère and gas pools carry the warmth |
| Candle | Flame | (interior) | Pools per §2.6 |
| Fog | Three waves | #A8B0B8 → #D0D0D0 | BG3 fog add-half |
| Gloom | Arch over a dot | (underground) | −3 R, −3 G, −2 B outside the lantern window |

**LUMIÈRE (two Lights):** ch2 splits the sky at line 76: the upper band in one Light's gradient, the lower in the other's, with a 4-line dithered seam.

### 3.4 The hex-snapping rule

Each 8-bit channel must end in 0 or 8 (e.g. #E04020). Artists pick from the snapped 32-step ramp per channel; Constraint Lint rejects anything else. Representative colours in this doc are the authoring targets for each tileset's key ramps.

### 3.5 Narrative palette rules

| Rule | What it does | Where |
|---|---|---|
| **The Violet Shadow Rule** | Before Lucile's dawn lesson (CH-05: "colour in shadows"), exterior shadow ramps are neutral grey-brown (#585048). From the first frame after that scene, every exterior palette swaps its two darkest shadow entries for blue-violet (#484070, #302850). Nobody mentions it; replayers notice | All outdoor Paris and regional maps, CH-05 onward |
| **The Wrong Colour** | Magenta #F048D8 and cyan #40F0E8 appear nowhere in 1833 or 2026 except CHRONO actions, the Engine, Archon's final forms, the Amalgam seams and Brücke's static automata: the art twin of the score's single synth patch (CANON §15a). Seoul neon uses other hues (#F87898, #40C8B8) | P29, P30, BOSS-26–28, S08 static pockets, CHRONO FX |
| **Pitch colours** | Each LM-01 note has its friend's colour (CANON §5g, §15c): D #A8B8F0 (MJ) · E #A8D8A0 (BE) · F♯ #F8A088 (DE) · G #B8C0D0 (AL) · A #C8B0F0 (CH) · B #E8F0F8 (LI) · C♯ #D8A0C0 (FA) · octave D #F8D888 on #3850A0 (LU) | Clef plinth glows, the Engine's seven oscillator columns, the Octave pillars and staff, the Door's eight panels, the Window Clock staff. The eighth colour exists nowhere in the stone network: no stone sings the upper D |
| **Act palette arc** | Act I grey-brown and lime-white; Act II gilt and candle-gold; Act III greens, river-silver and autumn ochre; Act IV indigo nocturne; epilogues: Seoul snow-white and LED, Paris winter turning to March gold (§6.6) | Tileset palette sets per act |

### 3.6 Character colour keys (CANON §5g; proposals marked)

| Who | Key ramps (hex) | Accent |
|---|---|---|
| MJ Min-jun | Tailcoat #182858 #283878 #4058A0 · green coat (CH-02) #284830 #386840 · hoodie #888890 · hair #181820 · skin #F0D0B0 #D8A880 #A87050 | Midnight blue #283878 |
| LU Lucile | Auburn #A04020 #C86030 #E08850 · headscarf #3850A0 #6080C0 · shawl #C89038 #E0B060 · dress #788088 #A0A8A8 · skin #F8D8C0 #E0B098 #B07860 · Seoul: coat #F0E8D0, scarf #C82830 | Ultramarine and ochre |
| BE Berlioz | Hair #C04018 #E06830 · coat #305830 #487848 · cravat #E8E8E0 | Red hair |
| DE Delacroix | Hair #201818 · coat #181820 #303038 · waistcoat #D03820 #F05830 | Vermilion |
| AL Alkan | Coat #181820 · slate #586070 #8890A0 · curls #201810 | Slate grey |
| CH Chopin | Hair #786050 #988070 · coat #A0A0A8 #C8C8D0 · gloves #F8F8F8 · violet #7048A0 | Violet |
| LI Liszt | Hair #E0C878 #F8E8A8 · coat #181820 · cravat #F8F8F0 · silver #B8C0C8 | Silver |
| FA Farrenc | *Bandeaux* #281810 · plum #602848 #884068 · ink cuffs #283050 on #E8E0D0 | Plum |
| SY Seo-yeon *(proposed)* | Long black padded coat #202028 #383840 · grey knit scarf #9898A0 · violin case #503828 · hair #101018 | Rosin amber #C88820 |
| JW Jae-won *(proposed)* | Red club windbreaker #C02828 #E04840 · white hoodie #E8E8E8 · knit cap #283048 · janggu on a strap #A06838 | *Obangsaek* ribbons on his sticks: #2848B8 #D02020 #F0C820 #F8F8F8 #181818 |
| JU Julien | Blue-grey frock coat worn open #586878 #788898 · waistcoat unbuttoned at the bottom, no cravat (a 1950 habit) | Hour of Smoke blue-grey |
| Cabal | Vane crimson #A01828 #C83040 · Delorme ochre-gold #C89830 #E8C050 · Brücke gunmetal #485058 #687078 · Marthe white cornette #F0F0E8 · Archon black #101010 with the sigil key #D8B048 | — |

---

## 4. Sprites and Portraits

### 4.1 Cell, proportions and palette map

- **Proportions:** figure ≈ 20 × 30 in the 32 × 32 cell (R-39); head 10 px (three heads tall, a touch taller than FF6), eyes 2 px with a 1-px catchlight. Children (Théo 12, Petit-Louis 11, Victorine 7, César Franck 10) are 22–24 px tall; Clara Wieck 26 px.
- **Key light:** upper left for the whole game (field, battle, portraits). **Outline:** selective, a dark tone of the local colour; true black only where the costume is black.
- **Facings:** field down, up, side (right mirrored for left). Asymmetric props get their own left frames: Min-jun's tote (CH-P–01), Lucile's brush roll at the right hip, Jae-won's janggu strap. Battle sprites face left only (party on the right).
- **One palette** (shared with the pair-mate, §2.3) serves field and battle; a costume variant recolours the same indices.

| Index | Role | Index | Role |
|---|---|---|---|
| 0 | Transparent | 8–10 | Main costume (light, mid, dark) |
| 1 | Outline (darkest local tone) | 11–12 | Secondary costume (light, dark) |
| 2–4 | Skin (light, mid, shadow) | 13 | Accent (the CANON §5g key colour) |
| 5–7 | Hair (light, mid, dark) | 14 | Highlight (#F8F8F8 or #F0F0E8) |
| — | — | 15 | Eyes and deepest shadow |

**Pair palettes** keep indices 1–7, 14 and 15 shared (outline, skin, hair, highlight, eyes) and split 8–13 between the two costumes; two hair colours take indices 5–6 and 7. **Skin ramps** are drawn from life, never a hue shortcut: Min-jun's warm beige (#F0D0B0 → #A87050) carries no yellow cast; Lucile's is fair with a 2-px freckle cluster at 1:1 scale only in portraits.

### 4.2 Costume variants (full field and battle sets)

| Who | Variant | Chapters | Source |
|---|---|---|---|
| MJ | Navy padded jacket, grey hoodie, black jeans, white sneakers, canvas tote | CH-P–CH-01 | CANON §5g |
| MJ | Bottle-green frock coat (oversized) over the sneakers | CH-02–CH-04 | CANON §5g |
| MJ | Midnight-blue tailcoat and boots | CH-05–CH-17, CH-E2 | CANON §5g |
| MJ | Charcoal parka from his own wardrobe over the tailcoat's waistcoat, the midnight-blue cravat worn as a scarf | CH-E1 from LOC-S04 on (before it, the tailcoat) | **Proposed** (Canon Additions) |
| LU | Auburn hair, faded ultramarine headscarf, ochre shawl, paint-flecked grey dress with modest working-woman *gigot* sleeves, brush roll | CH-03–CH-17, CH-E2 | CANON §5g |
| LU | Seo-yeon's cream coat and red scarf (the headscarf in her pocket) | CH-E1 | CANON §5g |

Field-only variants: Berlioz in borrowed wedding finery (P23, CH-09: walk set + `bow`); Min-jun's right hand bandaged (CH-09 cell to CH-10: a 3-px overlay tile). **Winter** is shown by breath vapour (8 × 8 puffs every 90 frames) on outdoor maps from CH-12 and in CH-E1/CH-E2, never by extra costume sets.

### 4.3 NPC guidelines

**Tier B and named NPCs** get bespoke sprites: a reduced field set (stand 3, walk 6, talk 1, bow 2: 12 frames) plus one pose that matches their bespoke portrait expression (Sand `cigar`, Pleyel `inspecting`, Cherubini `scowl`, Rossini `savouring`). **Tier C** townsfolk are built from palette-swappable bases (12 frames each: 9 walk, 2 idle, 1 talk gesture):

| Set | Bases (swaps) |
|---|---|
| Paris 1833 | Worker in blue blouse (3) · grisette (3) · *chiffonnière* with basket and hook (2) · bourgeois in top hat (3) · bourgeoise in bonnet, *gigot* sleeves (3) · Romantic student, long hair (2) · *gamin* (3) · old woman with cane (2) · priest in soutane (1) · Daughter of Charity in white cornette (1) · National Guardsman, shako (1; never fought, CANON §12) · *octroi* agent (1) · coachman in caped greatcoat (2) · water-carrier with yoke and buckets (1) · lamplighter with pole and ladder (1) · washerwoman (2) · *bouquiniste* (2) · salon gentleman in evening dress (3) · salon lady in ball gown (3) |
| Regions | Berry peasant in smock and wide hat (2) · bargeman (2) · Prussian customs officer (1) · steamboat crew (2) |
| Seoul 2026 | Office worker in long padded coat (4) · student with backpack (3) · grandmother in quilted vest (2) · delivery rider in helmet (2) · convenience-store clerk (1) · police officer (1; never fought) · busker (3) · child in snowsuit (2) · couple, hand-hold pair (2) |

**Lamplighters** lower the Left Bank's rope-hung *réverbères* at dusk on night variants (P02, P22); water-carriers recall the clean-water campaigns after 1832 without a word. The Sergent (FIC-24) walks with a crutch drawn with dignity (no comedy frames).

### 4.4 Enemy guidelines

| Class | Size | Layer | Frames |
|---|---|---|---|
| S | 32 × 32 | 1 OBJ | Idle 2, attack 2, special 2; hit = 2-frame white palette flash |
| M | 64 × 64 | 4 OBJ | Idle 2–4, two attacks × 3, special 4 |
| L (bosses, set enemies) | 96 × 96 to 192 × 128 | BG1 (two palettes, 30 colours) | Tile-swap animation (4–8 key poses), HDMA motion, OBJ adds |
| XL | The Engine, the Stilled Hour | Mode 7 or BG1 + BG2 | §2.7 |

**Defeat animations never leave a body (A4):**

| Family (CANON §12) | Palette key | Defeat |
|---|---|---|
| Echoes (Ossuary, Lime, Choir, Tocsin, Cloaca, Abbey, Lorelei, Stilled, residual) | Bone #E0D8C0, slate #586070, resonance aqua #A8D8D0; Tocsin gunsmoke #888888 and bell bronze #A87838; Cloaca #405830; Lorelei long gold light #E8C060 falling like hair, never a face | Dissolves into three rising sound rings (16 × 16, 6 frames) and a fading hum. **Stilled Echoes have no idle animation**: they stand frozen until they act |
| Humans (smugglers, Black Coats, Grey Hand, café toughs, Cleaners, pickpockets, frontier smugglers) | Grey Hand greatcoat #707880 with one grey kid glove #A0A0A8 on the right hand; Black Coats cheap black #282830 with shiny elbows #484858 | **Routed** (turns and runs off the left edge, 6 frames) or **subdued** (kneels, drops the weapon, hands up, 3 frames). Never lies still |
| Animals (rats, boar) | Brown #685040 | Bolts off screen |
| Automata (Mk. I, barrel, Hunter, river, stage, forge) | Gunmetal #485058, brass #C8A050, music-box comb #C0C8D0 | A spring pops; six gear OBJs scatter and bounce once |
| Tableaux and Living Tableaux; Vane's collection | Varnish brown #806030, gilt #D8A840; Vane's crimson #A01828 | The canvas peels from a corner and rolls up; the frame clatters |
| Gaslight Wisps | #A0C8F8 → #F8E070 | Gutters out like a turned-down tap |
| Phantom Quartet | Smoke blue-grey #607088; instruments only | Each instrument fades on its last note |
| Amalgam Echoes | Lutèce stone #C8B890; turnstile steel #B8C0C8 with Line 2 green #38A838; neon wraiths #F87898 / #40C8B8 | Tears along a scanline seam and is gone |
| Static automata (CH-E1) | The Wrong Colour over #101018 | Collapses into noise: mosaic 15, then off |
| Ossia phantoms (BOSS-31 bar 1) | The friends' battle sprites with palettes inverted | Invert back to true colour, then fade (a kindness) |

### 4.5 Portrait spec

| Item | Spec (CANON §16a, §16h) |
|---|---|
| Size | **48 × 48**, head and shoulders, three-quarter view facing right (towards the text), key light upper left |
| Palette | One OBJ palette: **14 drawing colours + the well colour #182040** (index 15), because the portrait shows through a transparent well in the BG3 box and must carry its own backing |
| Implementation | Field: 6 OBJs at OBJ priority 3 in palette 6; battle: 21 OBJs (§2.4) |
| Motion | **Static**: no blinks, no mouth flaps (the brief's "static cut-ins"); an expression change is a hard cut at the box's first character |
| Costume | Swapped as a **48 × 16 collar strip** (bottom two tile rows) per costume variant, picked by chapter, never by tag (dialogue_style_guide §3.1) |
| Never | Mirrored (parting, scars and asymmetries stay true); a cough or illness in the face (Théo, Chopin) |

### 4.6 Tier A expression sets

Base set for all: neutral, smile, laugh, sad, angry, surprised, worried, determined, tender (CANON §16a). Proposed extras (dialogue_style_guide CCR) are **drawn now and shipped behind their fallback** until adopted.

| ID | Name tab(s) (CANON §16h) | Extra | Collar strips |
|---|---|---|---|
| PC-01 | Min-jun | homesick | Hoodie · green coat · tailcoat · parka (proposed) |
| PC-02 | ??? → Lucile (CH-04) | guilty | 1833 · Seoul coat |
| PC-03 | Berlioz | grandiose | — |
| PC-04 | Delacroix | appraising *(proposed; neutral)* | — |
| PC-05 | Alkan | deadpan | — |
| PC-06 | Chopin | ironic | — |
| PC-07 | Liszt | rapture | — |
| PC-08 | Farrenc | sceptical *(proposed; neutral)* | — |
| PC-09 | Seo-yeon | scowl *(proposed; angry)* | — |
| PC-10 | Jae-won | pumped *(proposed; laugh)* | — |
| ANA-03 / PC-11 | Julien | sheepish *(proposed; worried)* | — |
| ANA-01 | Baron d'Orsenne → Archon (CH-12) | cold | Peer's coat · wired to the Engine (CH-16) |
| ANA-02 | Lord Vane | smirk *(proposed; smile)* | — |
| ANA-04 | Mme Delorme → Delorme (CH-12) | contempt *(proposed; angry)* | — |
| ANA-05 | Maître Brücke → Brücke → Elias Brandt | calculating *(proposed; neutral)* | — |
| ANA-06 | Sœur Marthe | serene *(proposed; neutral)* | — |
| FIC-01 | Théo | brave *(proposed; determined)* | — |

### 4.7 Tier B expression sets

Each: **neutral, smile, grave + one bespoke** (dialogue_style_guide §3.4), one palette, no collar strips. NPC-01 Franck *shy* · NPC-02 Thalberg *intent* · NPC-03 Offenbach *cheeky* · NPC-04 Florestan *wistful* · NPC-05 Clara Wieck *proud* · NPC-06 Herr Wieck *glare* · NPC-07 Mendelssohn *amused* · NPC-08 Czerny *laugh* · NPC-09 Ingres *disdain* · NPC-10 Delaroche *pensive* · NPC-11 Chassériau *awed* · NPC-12 Vernet *alarmed* · NPC-13 Corot *dreamy* · NPC-14 Sand *cigar* · NPC-15 Pleyel *inspecting* · NPC-16 Kalkbrenner *pompous* · NPC-17 Cherubini *scowl* · NPC-18 d'Agoult *aloof* · NPC-19 Smithson *radiant* · NPC-20 A. Farrenc *proud* · NPC-21 Victorine *giggle* · NPC-22 Paganini *piercing* · NPC-23 Louis-Philippe *genial* · NPC-24 Gisquet *wary* · NPC-25 Rambuteau *harried* · NPC-26 Belgiojoso *fierce* · NPC-27 Count Apponyi *uneasy* · NPC-28 Thérèse Apponyi *delighted* · NPC-29 Hiller *cheerful* · NPC-30 Heine *wry* · NPC-33 Rossini *savouring* · FIC-02 Mère Gaudin *scolding* · FIC-03 Petit-Louis *grin* · FIC-04 Corbel *frightened* · FIC-05 Lavergne *flustered* · FIC-07 Marlot *sneer* · FIC-08 Roussel *steady* · FIC-09 Mathurin *squint* · FIC-12 Prof. Yoon *astonished* · FIC-13 Det. Oh *doubtful* · FIC-14 Céline *resolved* · FIC-18 Gros-Louis *gloat* · FIC-19 Tissot *sweating*.

**Likeness rule (real people):** portraits follow documented likenesses of 1830–34 (Delacroix's self-portraits, Dantan's statuettes, Achille Devéria's lithographs, the period's engraved portraits), never later photographs; Chopin and Liszt are 23 and 21, not the famous later images.

### 4.8 Emotes and overhead markers

**Emotes** (16 × 16, 40 frames, OBJ palette 7; dialogue_style_guide §2.4): `!` · `?` · `...` · `note` (a quaver bobbing) · `sweat` · `vein` · `idea` (a candle flaring, never a bulb) · `zzz` · `tear` · `sparkle` (gold star burst: the two kisses and the Window only). **No heart emote.**

**Battle overhead markers** (8 × 8, combat_ensemble §2.2): Recital movement (I/II/III in a staff box) · Coda count (two digits) · Tutti tokens (violin, flute, horn, timpani, open mouth) · Rubato charges (clock hands, up to 3) · Bravura and Idée Fixe stacks (pips) · Swell (rising hairpin) · Dots (n/10) · crit mark (red accent >) · Tacet (rest glyph) · Unseen (an eye with a slash).

---

## 5. Animation Lists

Timings are in frames at 60 fps. "Frames" are unique drawings; loops reuse them.

### 5.1 Shared field set (every PC)

| Animation | Unique frames | Timing | Notes |
|---|---|---|---|
| Stand (down, up, side) | 3 | — | Side mirrored |
| Walk (down, up, side) | 6 | 1 frame per 8 px | Step-stand-step-stand |
| Talk gesture | 1 | 12 on, 12 off | Hand lift |
| `{NOD}` / `{HEADSHAKE}` | 2 / 2 | 8 per frame | — |
| `{BOW}` | 2 | 16 per frame | Period bow (men) or curtsey (women) |
| `{KNEEL}` / `{SIT}` | 2 / 3 | Held | Sit has down, up, side |
| Startle (with `{JUMP}`) | 2 | 6 + held | — |
| Laugh | 2 | 6 per frame, 4 loops | Never in grief scenes |
| Look away / down | 2 | Held | Sadness, guilt |
| Cheer, arms up | 1 | Held | — |
| Swoon and lie still (story collapse) | 2 | 8 + held | Passage Swoon, the CH-09 cell |
| Carry / hold out | 1 | Held | Gifts, letters, the ledger |

### 5.2 Shared battle set (every PC; facing left)

| Animation | Frames | Timing |
|---|---|---|
| Ready (breathing) | 2 | 32 per frame loop |
| Step forward (Ready, command input) | 1 | 8-px slide over 6 |
| Fight (wind-up, strike, follow-through) | 3 | 4 / 6 / 10 |
| Cast (Harmony) | 2 | 8 per frame, 3 loops |
| Item | 1 | 20 |
| Hit | 1 | 12, 2-px knockback |
| Defend | 1 | Held |
| Low HP (≤ 25%, kneel) | 1 | Held |
| Swoon | 1 | Held (lying, eyes closed, no blood) |
| Victory | 2 | 12 per frame loop |
| Flee (back turned) | 2 | 6 per frame |
| Cadenza stance | 2 | 10 per frame; banner holds 90 |
| Synergy pose | 1 | Held during the animation |
| Voice (Octave: holding the note) | 1 | Held while the pillar rises |

### 5.3 Per-character bespoke animations

| PC | Field (frames) | Battle unique (frames) |
|---|---|---|
| **MJ** | `fallboard_tap` 4 (lift, tap, lift, tap; 6 each: his first frame of the game, CH-P) · `play_piano` 6 (seated loop 4 + head sway 2) · `conduct` 4 (from CH-04) · phone check 3 (screen glow pixel; `homesick` beats) · humming 1 (with `note`) | **Recital:** the Phantom Grand fades in beside him (64 × 32 prop, 2 OBJs, effects palette); fallboard tap 4 (every Recital begins with it) · seated loop 4 · movement change flourish 3 · Movement III burst 4 · Recital break (startle, off the bench) 3 · **CONDUCT** baton cue 4 · *Resonance* hum 2 (CH-01) · tuning-fork strike 3 (CH-01–02 weapon) |
| **LU** | `paint` 7 · sketch 3 · fan-tray walk 6 (CH-03) · haggle 2 · guilty glance 2 | §5.4 (29 frames + easel prop) |
| **BE** | `conduct` 4 · grandiose arm sweep 3 · drinking 2 (CH-02 tavern) · wedding bow 2 | **Cue** ×5 sections (Strings: bowing · Winds: hand to lips · Brass: fist up · Percussion: downstroke · Chorus: arms open) 2 each · **Tutti** double downbeat 6 · *Cacophony* wince 2 · Idée Fixe stack lunge 2 |
| **DE** | Sketch 3 · appraising (hand to chin) 2 · cravat adjust idle 2 · easel painting 4 (studio) | **CANVAS** rapier stroke trailing both pigments 6 · **Sketch** (notebook, glance, draw, close) 4 · Chiaroscuro counter 3 |
| **AL** | Deadpan blink 2 (once per 240 frames) · reading psalter 2 · crouch to inspect a machine 2 · pedal-piano playing 4 (LOC-P36) | **ÉTUDE** input stance 2 · overhead smash 3 · sweep 3 · double strike 3 · pedal stomp 2 · *Recluse* guard 2. The 12 Études combine these with their own effects |
| **CH** | `mimic` 4 (2 for Kalkbrenner's puffed chest, 2 for Liszt's hair-toss) · `play_piano` 6 · glove to lips 2 (the foreshadowed cough; at most once per chapter, CANON R-11) | **Borrow** (quill sweeps a ghost clock hand off the enemy) 4 · **Repay** (hands it to an ally) 4 · *Tempo Rubato* (sweeps all) 5 · elegant heal cast 2 |
| **LI** | `play_piano` 6 (flamboyant) · rapture (eyes closed, head back) 2 · bow to an audience 2 | **TRANSCEND** sabre twirl, hair flick, two casts 6 · **MEPHISTO** *Transcribe* (mirrors the last action's pose, eyes flash) 4 · Bravura: ready loop speeds by 2 frames per stack |
| **FA** | Writing 3 · straightening cuffs 2 · arms folded (`sceptical`) 2 | **Annotate** (opens folio, writes) 4 · **Canon** (points the pen) 3 · **Fugue** three rising strikes 6 · **Cadence** (closes the folio) 3 |
| **SY** | Violin-case walk set 6 · scowl 2 · playing 4 | **Sostenuto** long-bow loop 4 · **Spiccato** 6 · mode switch 1 |
| **JW** | Drumming on the janggu 4 · fist pump (`pumped`) 2 · phone game 2 | **BEAT** alternating sticks 4 (loop at the *jangdan* tempo) · perfect-hit flash 1 · Encore Stage pose 2 |
| **JU** | Slouched `play_piano` 6 · `sheepish` 2 · Walkman listening 2 (CH-E2 burial scene) | **IMPROVISE** seated at a spectral upright 4 · *Tritone Storm* 4 |

**Romance pair (MJ + LU only):** hand-hold walk (side, 4) and `{LEAN}` (2 frames each, side): sprites face each other and lean 2 px; the text box closes; fade to black with `sparkle` (CANON §16f).

**Other bespoke `{ANIM}`s** (dialogue_style_guide §2.4): `whittle` 3 (Théo, the fused-hands key, CH-07) · `cigar` 3 (Sand) · `paint` 4 (Corot, Delorme, Chassériau) · `play_piano` 6 (Thalberg, Herz, Clara, Hiller, Mendelssohn, Victorine) · `conduct` 4 (Habeneck, Girard).

### 5.4 Lucile's painting animations

Lucile paints the battlefield's light, so her animations change the screen, not only the target.

| Animation | Sprite frames | Prop / FX | Screen effect |
|---|---|---|---|
| Easel unfold (first Plein Air of a battle) | 3 | 16 × 32 easel OBJ in her palette | Stays beside her for the battle |
| Field `paint` | 7 (set easel 3; loop: look, dab, step back, squint) | Easel; canvas fills in 4 tile swaps over a scene | — |
| **IMPRESSION** | 5 (load brush, three alternating dabs, flick) | A trail of short horizontal dabs in the Light's first boosted element colour | Each consecutive repeat adds a dab to the trail (2 at +20% … 6 at +100%): her chain shown as brushwork |
| **POINTILLÉ** | 6 (rapid stipple, brush vibrating) | 8 dot OBJs arc to targets (allies: Cantabile green, Allegro gold, Varnish amber) | Each landing dot ticks the Dots marker (n/10); at 10, the enemy's palette flashes white: **Composed** |
| **IMPASTO** | 6 (palette-knife scoop, two-handed smear, stagger) | A thick swirling stroke across BG3 | Sky crossfades to Night over 30 frames |
| ***Nuit étoilée*** | 8 (brush spun overhead, loop) | Eight 16 × 16 star swirls (4-frame rotation) | ch5 wobble on the sky band; INS digits rise blue |
| **LUMIÈRE** | 6 (a brush in each hand, crossing strokes) | Two colour trails | The sky splits into two gradients (§3.3) |
| **Shift the Hour** | 4 (brush raised, horizon swept right to left) | — | The chosen gradient wipes across the sky over 30 frames |
| *Lever du jour* (Cadenza) | 2 + held | Dawn line drawn across the whole screen | Full-screen Dawn wipe; second phase (confidant): gold leaf falls |
| Sketchbook (field, Talk menu CH-05–CH-08) | 3 | — | Opens UI-12 (§8.1) |

### 5.5 Guests (CANON §6)

Guests get a reduced battle set: ready 2, act 3, hit 1, swoon 1, victory 1, command 3–4. Commands: Mathurin LANTERN (lantern raised, wall Echoes revealed) · Sand NOVEL (opens a book; *Tragedy*, *Romance*, *Satire* each a page colour) · Corot SOUVENIR (misty brush wash) · Clara PRODIGY (miniature keyboard, playing) · Mendelssohn HEBRIDES (a wave of sheet music) · Czerny VELOCITY (metronome swing) · "Florestan" FLORESTAN / EUSEBIUS (stands for one, sits for the other: two personae, never illness) · Offenbach GALOP (cello under one arm; six outcomes, each 2 frames) · Marthe TRIAGE (kneels, bandage roll) · Thalberg THREE HANDS (a third ghost hand between his two). Théo (GST-11) is an escort: walk 6, cower 1, `brave` stand 1, 2,000-HP bar over his head.

### 5.6 Status visuals

| Status | Visual (never disease on a body) |
|---|---|
| Miasma | Grey-green motes (8 × 8) rising; no discoloured skin |
| Smoke | Grey puffs around the head |
| Hush | Rest glyph overhead, mouth line closed |
| Reverie | Eyes closed, `zzz` |
| Delirium | Three quavers circling the head |
| Stagefright | Hit frame, 1-px tremble, `sweat` |
| Stun | Four-point sparks |
| Lento / Allegro | Dimmed / bright chevron on the ATB bar; the ready loop slows / speeds by half |
| Fermata | Fermata glyph overhead; sprite frozen |
| Marble | Palette swapped to a 15-step grey ramp |
| Coda | Two-digit count overhead |
| Frenzy | Red outline pulse |
| Out of Tune / Discord | Wavy staff glyph / broken staff glyph |
| Swing | 1-px jitter on the ATB bar; sprite sways |
| Unwritten | The sprite erases row by row from the top over 8 frames and returns the same way |
| Varnish / Glaze / Mirror | Amber / blue sheen pulse every 60 frames / a pane of glass glints |
| Cantabile, Encore, Inspired, Bulwark, Swell, Fortissimo | Green notes / gold halo / blue sparkle / shield outline / hairpin / red accent |

---

## 6. Tilesets and Palettes by Location

### 6.1 Budgets

Per map: **≤ 256 metatiles** (16 × 16), **six scenery palettes** (90 colours), up to 8 animated tile groups (palette cycling or 2–4-frame tile swaps). BG1 carries ground and walls, BG2 overlays, roofs and foreground, BG3 weather. Tilesets are named **TS-##** (see Canon Additions); maps of one family share tiles and swap palettes.

### 6.2 Tilesets per location (CANON §12)

| LOC | Tileset | Key palette | Light | Mood reference |
|---|---|---|---|---|
| S01 Annex, S05 Library, S10 Hall and clock tower | TS-01 Hanseong | Fluorescent #E0F0F0, linoleum #98A8A0, door wood #A07850, night glass #182030; S05 oak #A87848; S10 gears #C8A050 | Noon (fluorescent); S10 Night | Korean conservatory practice blocks: numbered doors, wired-glass windows, a vending machine's hum |
| S02 Hidden Study | TS-02 Study | Brick #904830 #683020, brass #D8B048, dust light #C8B898, Heart-stone hub #E8E0D0 | Gloom; Candle in CH-E1 (Lucile lights the stubs) | Every object of world_rules_and_lore §6.2 placed to scale; the portrait's dust outline is a 26 × 32-px pale rectangle facing the Door |
| S03 Jeong-dong, S07 Hongdae, S12 Insadong; W03 | TS-03 Seoul Winter | Snow #E8F0F8, snow shadow #8898C0, asphalt #484850, palace wall #A89880, roof tile #384048, warm windows #F8C878, neon #F87898 #40C8B8; S12 timber #805838 | Dusk (S03), Night (S07), Noon (S12) | Bare ginkgo along the Stonewall Road; Hongdae's buskers; Insadong's hanji shops |
| S04 Kang apartment, S15 Kang Piano Service | TS-04 Seoul Domestic | Ondol floor #C89058, wallpaper #F0E8D8, LED #E8F0F8, hammer felt #A02828, radio amber #F8B040 | Candle (warm interior) | His room kept as he left it; felt hammers and a work lamp in his father's shop |
| S06 Hangaram, S13 French Embassy | TS-05 Seoul Civic | Gallery white #F0F0F0, wall #C8C8C8, spotlight #F8E0B0; flag #2048A0 #F8F8F8 #D82828 | Candle (spotlit) | The five real works (three *Grainstacks*, the Pissarro, the van Gogh) and her canvas as Mode 3 plates (§6.6) |
| S08 Euljiro / Line 2 | TS-06 Underground | Shutters #707880, wall tile #A8B8B0, Line 2 green #38A838, fluorescent #D0F0E8; static pockets in the Wrong Colour | Gloom with fluorescent pools | Shuttered print shops and tool stalls; the platform display BOSS-29 uses |
| S09 Namsan, S11 Bosingak, S14 Yanghwajin | TS-07 Heights | City lights #F8D878 on #101830; *dancheong* #389068 #B83020 #3858A8 #D8A040; river #687880; granite #A0A098 | Night (S09, S11); Dusk (S14) | The bell swings in 4 BG frames for 33 strokes; Théo's grave in pale granite under bare trees |
| W01 Paris Overworld | TS-10 | Slate #586878, plaster #D0C0A0, Seine #506870, gardens #507838, smoke #A0A0A0 | By scene; Dusk and Night palette shifts | The Turgot plan's density; landmarks per §6.3 |
| P01 Galleries, P38 Philosophers' crypt, P26 quarry levels | TS-11 Quarry | Limestone #C8B890 #988868, shadow #484038, lime pits #F0F0E0, lantern #F8C860; ossuary bone walls as patterned architecture | Gloom | Piranesi's *Carceri*; the Catacombs' 1810 bone walls; the Frères' inscription at Clef I |
| P02 rue Saint-Jacques, P28 Montagne Sainte-Geneviève, Left Bank fronts (P06, P20, P21) | TS-12 Left Bank | Wet cobbles #605860 #888090, plaster #C8B898, shutters #506048, réverbère flame #F8D070 | Fog (CH-01 rain), Noon; Night variants P02, P28 | Boilly's street crowds; a central gutter and no pavements; cholera ex-votos at Saint-Séverin |
| P03 Faubourg-Poissonnière, P10 Boulevards, P16 Palais-Royal | TS-13 Right Bank | Trees #487030, gaslight #F8E090, awnings #B83828 / #F0E0C0, passage glass #A8C8D0, arcades #D8C8A8 | Noon; Night variants P10, P16 | Tortoni's terrace; scales from every Conservatoire window as animated shutters |
| P04 tavern, P20 attic, P21 Corbel, P36 Alkan house, P37 dispensary, E04 *Le Diapason Bleu* | TS-14 Working Interiors | Timber #604030 #886040, whitewash #E0D8C0, copper #C07040, candle #F8D070; P37 linen #F0F0E8; E04 blue glass #3050A0 | Candle | Chardin's kitchens; the pianino's three dead keys as chipped ivory; fans drying under the attic skylight |
| P05 Lavergne, P14 Faubourg Saint-Germain (courtyards, façades, interiors), P15 Apponyi, P23 British Embassy, P34 Hôtel de Vane, P39 Belgiojoso | TS-15 Salons | Gilt #D8B048 #A88030, damask #902030, mirror #B8C8D0, parquet #A06838, candlelight #F8E0A0; P05's gilt one step duller ("on credit") | Candle | Eugène Lami's salon watercolours; P15's mirrors by BG2 reflection; every painting in P34 in Vane's crimson |
| P06 studio, P11 Chopin, P12 Pleyel, P19 Maison Farrenc, E02 Atelier, E05 Delorme's atelier | TS-16 Studios | North light #A8B8C8, stained floor #806848, canvas #E0D0B0, silks #C83838 #2878A8, copper plates #C88050; P11 violets #7048A0; E05 lens glass #D0E0E8 | Candle; river light by day in P06 | Pleyel's iron frames and felt; E05 mirrors with golden-section overlays |
| P09 Théâtre-Italien, P27 Opéra, P35 Conservatoire hall | TS-17 Theatres | Velvet #A01820, gold #D8A840, boards #A07040, footlights #F8E8A0, hemp #B09868, fly gallery #484850 | Candle | Daumier's theatre prints; P27 also drawn in cross-section (§8.16) |
| P13 Louvre, E01 Salon of 1834 | TS-18 Louvre | Wall #883028, skylight #E0E8F0, frames #D8B048, parquet #A87040, marble #E0D8D0 | Noon (skylight) | Samuel Morse's *Gallery of the Louvre* (1831–33); E01 hung floor to ceiling, her canvas *au ciel* |
| P22 Quays, P32 Île de la Cité, P31 Bercy | TS-19 Seine | River #587880 (dawn #8898B8), quays #B0A890, bouquinistes' boxes #305838, washing boats #706048, mist #C8D0D8; P31 barrels #805830 | Dawn / Fog; Night variant P22 | Turner's Seine watercolours (1834–35); Corot's Paris views |
| P17 Sewers | TS-20 Sewers | Wet stone #485048, slime #506838, water #304840, shrine candle #F8C860, hiss motes #A0A8A8 | Gloom | Palette-cycled drips; Julien's cassette shrine the only warm light |
| P18 Undercroft, R02 forge halls | TS-21 Clockwork | Brass #C8A050, gunmetal #485058, oil #181818, escapement glow #F8E8A0, comb #C0C8D0; R02 forge #C04020 | Candle | Jaquet-Droz automata; ten thousand ticks as 4-frame wheel tiles |
| P07 Marais, P08 Barricade, P25 Prefecture | TS-22 Marais | Paving #807870, smoke #A0A0A0, Place Royale brick #A85838 and stone #D0C8B0, iron #383840, ink #283048 | Noon, smoke-hazed | Daumier, who sketches the riot in-game; Hugo's window over the arcades |
| P26 Val-de-Grâce | TS-23 Abbey | Limestone #E0D8C8, dome #4060A0 with gold #D8B048, linen #F0F0E8, cloister #484050 | Night; Candle in the wards | Granet's cloisters; Mignard's dome as a BG2 ceiling |
| P24 Montmartre, P28 roof, P33 Père-Lachaise | TS-24 Heights | Mill sails #E0D8C0, vines #507830, gypsum #E8E8E0; Panthéon stone #E0D8C8, scaffold #A08060, night #182040, stars #F8F8D0; tombs #A8A898, yew #304830 | Dawn (P24), Night (P28 roof) | The Chappe telegraph on Saint-Pierre changes its arms every 240 frames; David d'Angers' pediment in scaffolding |
| P29 Chrono-Labyrinth | TS-25 Amalgam | BG1 TS-11 stone, BG2 TS-06 tile and steel, seams in the Wrong Colour | Gloom ↔ Noon | A subway platform in the ossuary, a convenience store in the Palais-Royal arcade, practice rooms off rue Bergère (CANON §4b) |
| P30 Heart Chamber, E03 Dead Heart | TS-26 Heart | Resonant stone #D0D8E0 #9098A8; the seven pitch colours (§3.5) | Gloom, lit by the oscillators | A cathedral of singing stone; the Engine per LAW-09 |
| W02 France and Rhine | TS-30 | Fields #88A050, poplars #406030, roads #C8B088, rivers #5878A0, hills #708850 | By scene; Dusk and Night shifts | Cassini-map density, poplar-lined post roads |
| R01 Fontainebleau, R05 Vallée Noire | TS-31 Forest | Sandstone #C0B098, birch #E8E8E0, heath #806080; R05 night #182028 with brass eye-glints #C8A050 | Noon (R01), Night (R05) | Corot's and Théodore Rousseau's 1830s forest studies |
| R03 Nohant, R04 La Châtre | TS-32 Berry | Façade #C8B898, hedges #487038, hearth #F0A040, hemp #A8A060, slate #586068 | Noon; Candle at the fireside | A modest Berry manor, not a château; the Indre valley |
| R06 Liège, R07 Düsseldorf, R10 Strasbourg, R13 Aachen, R14 Cologne | TS-33 Rhine Towns | Coal smoke #686060 · Academy brick #A06048 · pink sandstone #C08070 · Prussian barrier #181818 / #F0F0F0 · cathedral stone #706860 | Noon; Fog at R13 | Cologne's unfinished cathedral with its medieval crane; Strasbourg's bridge of boats to Kehl |
| R08 *Concordia* | TS-34 Steamboat | Deck #A07848, funnel #282828 with brass band #C8A050, steam #E0E0E8, river #587060, cliffs #788060 | Noon → Fog | The 42.7-m PRDG paddle steamer; paddle boxes as animated BG2 wheels |
| R09 Lorelei, R11 Étretat, R12 Le Havre | TS-35 Coast | Slate cliffs #605858; chalk #E8E8E0, sea #4878A0; masts #284058, harbour gold #F8C870 | Dusk, Noon, Dawn | Turner's Rhine; R12 is the sunrise she chose not to paint (BQ-PC02b), so the camera never frames the famous view head-on |
| R02 Château d'Orsenne | TS-36 Orsenne (+ TS-21) | Iron #383840, vault steel #8890A0, park #487038 | Noon; Candle | Forges, model barricades and a patent vault: industrial, never financial (CANON §16e) |

### 6.3 Period accuracy checklist

- **Notre-Dame has no spire** (removed 1786; the next is 1859) and only weathered medieval gargoyles: no Viollet-le-Duc chimeras. The archbishop's palace site beside it lies wrecked since the February 1831 riot.
- **Not yet built:** Sacré-Cœur, the Eiffel Tower, the Palais Garnier, Haussmann's boulevards. The Opéra is the Salle Le Peletier.
- **Under scaffolding:** the Arc de Triomphe (finished 1836), the Madeleine (1842), the Panthéon pediment (1831–37). The Place de la Concorde has no obelisk (raised 1836). The Vendôme column carries Napoleon from Sun 28 Jul 1833 (CH-06).
- The Louvre and Tuileries are not yet joined on the north side; old houses still crowd the Carrousel.
- **Light:** oil *réverbères* on ropes; gas only on the boulevards, in the covered passages and the rue de la Paix.
- **Dress:** women's *gigot* sleeves and wide bonnets; men's tailcoats, high collars, strapped trousers, top hats.
- **Seoul:** no real brands, logos or shopfronts; signage only from the hangul subset (§8.3); real landmarks at street level.

### 6.4 Seoul 2026 in 16-bit

1. **Inverted light.** Cold sources (LED #E8F0F8, fluorescent #D0F0E8) over warm interiors (ondol #C89058); in Paris, warm sources on cold stone. The two cities are lit like opposites.
2. **Neon by palette cycling:** signage ramps of 4 colours rotate every 8 frames; at most two cycling signs per screen, so the street hums without strobing.
3. **Snow:** falling flakes on BG3 (two speeds) plus ≤ 12 foreground OBJ flakes; settled snow on every ledge tile; footprints as 16 × 16 OBJs that fade after 120 frames.
4. **Height without perspective:** towers are BG2 façades whose upper storeys scroll at 50% at map edges, a top-down hint of altitude.
5. **Phones** are a single glowing pixel in every crowd sprite's hand; at Spotlight Trending the glow brightens and faces turn towards Lucile.
6. **Lucile's eyes:** in her point-of-view scenes, electric lights gain soft OBJ halos (colour math add): "this city keeps lightning in glass" (LAW-24).
7. **Same hand:** outline weight, dithering and the three-heads proportion are identical to 1833. Seoul is never drawn "cleaner".

### 6.5 The Paris-epilogue palette shift (CH-E2)

CH-E2 reuses the Paris maps (TS-10, TS-12, TS-13, TS-19, TS-24) in the **winter palette set** (overworld_and_towns WS-19), which then moves through three stages:

| Stage | Dates | Palette |
|---|---|---|
| Hard winter | Sun 22 Dec 1833 – Jan 1834 | Snow #E0E8F0 with violet shadows #8898C0; river grey-green #607870; chimney smoke OBJs; low sun |
| Pale gold | Feb 1834 (the proposal dawn on Montmartre, Sun 9 Feb) | Shadows warm to #9888B0; the sky gradient gains a band of #F8D8A8 |
| First spring | Sat 1 Mar 1834 (the Salon opening) | Wet stone, first green #78A048, clear light; the Violet Shadow Rule becomes **LUMIÈRE shadows**: every shadow ramp pairs a warm and a cool tone, the city painted in her own manner |

Lecterns burn **amber and dimmer** (#C88830); one goes dark after each major beat (CANON §11h) by swapping to unlit brass. The Atelier (E02) shifts from bare (one easel, no piano, grey light) to restored (skylight, Pleyel, Delacroix's easel) by tileset swap. **The Dead Heart (E03)** is the only map in the game with **zero animation**: no palette cycling, no tile swaps, no idle frames; Archon stands mid-gesture in a desaturated stone ramp, and the oscillators are dark. The **Seoul coda** (played as Seo-yeon) reuses TS-01, TS-02 and TS-03 with CH-E1's palettes.

### 6.6 Showcase plates (Mode 3)

Full-screen or framed 8bpp images, no sprites: **_Le Frère de demain_** in both compositions (LAW-26; 160 × 192, the Seoul version with the woman dissolving into light at the window's edge, the Paris version with Lucile painted clearly, looking at the viewer) · Lucile's *Le Pont Royal, effet de brume* (192 × 144) · a Berry field in points (CH-10) · *La Nuit étoilée sur le Panthéon* (CH-14) · her Salon entry No. 61 in both versions (KEY-40) · the S06 exhibition: three *Grainstacks*, Pissarro's *Boulevard Montmartre at Night*, van Gogh's *Starry Night over the Rhône* (public-domain works, repainted in pixels) · the Sketchbook's six last pages (LAW-23.5) · one ending-roll vignette per party member per branch. Plates hold for at least 180 frames and never carry text.

---

## 7. Special Effects

### 7.1 Battle effects

| Tier (CANON §10b) | Budget | Layers |
|---|---|---|
| T1 | ≤ 32 frames | OBJ only (effects palette) |
| T2 | ≤ 48 | OBJ + one palette flash |
| T3 | ≤ 64 | OBJ + BG3 layer |
| T4 | ≤ 90 | OBJ + BG3 + full-screen colour math |
| T5 and Synergies | ≤ 120 (Synergies ≤ 8 s; the Octave 15 s, combat_ensemble §6.5–§6.7) | Two effect layers + HDMA |

- **Recital:** a five-line staff unrolls above Min-jun; each movement adds a ribbon in the piece's element colour; Movement III bursts the ribbons outward. A rising chime marks each movement (CANON §15a).
- **Tutti:** Berlioz's spectral orchestra is drawn on BG3 as blue-white silhouettes (#A8C8F8, add-half), so it costs no OBJ palette; one section per token, up to three.
- **Invocations:** Period Scores open as sepia engravings; ✦ Future Scores glow blue-white and their staff lines shimmer (they are Anachronic, Heat 3).
- **CANVAS:** Delacroix's stroke leaves both pigments as a two-colour band that fades over 20 frames.
- **CHRONO:** the Wrong Colour, clock hands, a 6-frame scanline tear and one mosaic pulse.
- **The Octave:** each Voice raises a pillar in its pitch colour and lights its note on the eight-note staff; the pillars bend into one beam; four strikes each crack a quarter of the Stilled Hour's clock face; a white flash (Flash Reduction caps it); silence.

### 7.2 World effects

| Effect | Spec |
|---|---|
| **Rift** | A door-shaped vertical seam of light, 16 × 32, humming (2-px horizontal wobble on its rows); heard before seen: it appears 30 frames after `rift_hum` starts (LAW-01) |
| **Echo presence** | Field shimmer on walls (palette-cycled aqua flecks) where Mathurin's LANTERN or Perfect Pitch reveals |
| **Lectern** | A brass music stand glowing gold by 4-step palette cycle (8 frames per step); NPCs walk past it unseeing. CH-E2: amber, slower; CH-E1 has none, and the metronome save points tick in 4 frames (S08, S10) |
| **Passage Swoon** | Mosaic 1 → 15 and fade to black over 120 frames; on waking, mosaic 15 → 1 and a slow blur-in |
| **The Window (CH-17)** | A rectangle of Seoul's winter light (ch4 window, add colour math with a #C8D8F0 → #F0F0F8 gradient) with 40 snowflake OBJs falling **upward**; the far side has no outlines (LAW-13) until someone steps through |
| **The Stilled Hour** | Every palette cycle and idle animation on screen stops except the party's; the countdown runs on the clock face |
| **Unwritten** | Row-by-row erasure (§5.6) |
| **Breath vapour** | §4.2 |

### 7.3 Transitions

| Transition | Spec |
|---|---|
| **Into battle: the page turn** | ch5 skews the field more with each scanline as if a page lifts; a white staff-ruled sheet sweeps right to left on BG3; battle fades in. 40 frames. Preemptive: gold page edge. Back attack: the page turns backwards with a red edge. Boss: page turn + `piano_hit` + shake 1 |
| Map change | 16-frame fade to black, 16 in |
| Scene start | Caption (place and date) over a 60-frame fade-in (dialogue_style_guide §1.3) |
| Flashback | Sepia palette (`{TINT:sepia}`) |
| Front switch (CH-13) | Rope-and-curtain wipe, 90 frames (combat_ensemble §11.2) |

---

## 8. UI Screens

Mockups are schematic at roughly 4 px per character and 8 px per row; the coordinate tables are binding. Menu order and HUD placement follow CANON §16h.

### 8.1 Screen index

| ID | Screen | ID | Screen | ID | Screen |
|---|---|---|---|---|---|
| UI-01 | Title (§8.5) | UI-12 | Sketchbook (§8.20) | UI-23 | Octave formation (§8.15) |
| UI-02 | Dialogue box (§8.4) | UI-13 | Almanach (§8.20) | UI-24 | World map (§8.18) |
| UI-03 | Main menu (§8.6) | UI-14 | Config (§8.21) | UI-25 | Flight, Mode 7 (§8.18) |
| UI-04 | Items (§8.20) | UI-15 | Save / Load (§8.17) | UI-26 | Shop and inn (§8.20) |
| UI-05 | Harmony (§8.10) | UI-16 | Field HUD (§8.11) | UI-27 | Window Clock (§8.19) |
| UI-06 | Repertoire (§8.10) | UI-17 | Battle (§8.15) | UI-28 | Phone, CH-E1 (§8.19) |
| UI-07 | Equip (§8.8) | UI-18 | Victory and Fine (§8.20) | UI-29 | Crypt-door prompt (§8.20) |
| UI-08 | Opus (§8.9) | UI-19 | Salon programme (§8.13) | UI-30 | Ending roll (§8.20) |
| UI-09 | Ensemble (§8.20) | UI-20 | *Phrase* (§8.13) | UI-31 | Command overlays (§8.20) |
| UI-10 | Bonds (§8.12) | UI-21 | Piano Duel (§8.14) | | |
| UI-11 | Status (§8.7) | UI-22 | Grand Concert (§8.16) | | |

### 8.2 Window style, cursor and icons

- **Every window** uses the box gradient (#2858B8 → #303038, restarting at each window's top edge), a 2-px #F8F8F8 border with 1-px rounded corners and a 1-px #101018 inner shadow.
- **Cursor:** a white-gloved pointing hand (☞, 16 × 16) that bobs 1 px every 16 frames; per-menu memory follows Config. Sounds: soft square-wave move, confirm, cancel and buzzer clicks (CANON §15a).
- **Selected tab** in gold; a disabled entry is grey and the help line says why ("Not yet.").
- **8-px icons:** the eleven weapon classes (baton, brush, sword-cane, rapier, hammer, quill, sabre, folio, bow, drumsticks, cane), head, body, relic, consumable, key item; Scores ♪ (period), ✦ (future), ✶ (secret); the candle (Secrecy); BP notes (one to three, cracked, grey); a **door** for a confidant; a chain link for a Synergy; ★ for "R9 ★".

### 8.3 Fonts and the hangul subset

| Font | Cell / advance | Use | Notes |
|---|---|---|---|
| F1 VWF | 8 × 12; 3–7 px including 1-px spacing | Dialogue, menus, captions | Roman and italic banks (italic: 1-px shear every 4 rows); cap height 8, x-height 6, descender 2; tabular digits 6 px |
| F2 Battle digits | 8 × 8 | Damage #F8F8F8, heal #58E058, INS #58A8F8, "Miss" | 3 hops over 40 frames |
| F3 Small caps | 5 × 5 | Language badges (GER, FRE, ENG, KOR, POL, LAT, HEB), the candle's tier name | — |
| Hangul | 12 × 12; advance 13 | `[K]` runs in the English master | Counts as 2 characters (CANON §16a) |

**F1 character set:** A–Z, a–z, 0–9 and `. , ; : ! ? ' " “ ” ‘ ’ ( ) - – — … « » / & %`; French é è ê ë à â ç î ï ô û ù ü ÿ œ æ and capitals É È Ê À Â Ç Î Ô Û Œ Æ (capital accents compress to one row above the cap height, so *Le Clavier des Âges* fits the cell); German ä ö ü ß Ä Ö Ü; Polish ż ł ó ś ą ę ć ń Ż Ł Ś (*Żal*, *Żelazowa*); ₩ ♯ ♭ ✦ ★ ☞ ▼ ♪. **No accent is ever dropped** (dialogue_style_guide §7.1). **French build:** same font; overflow moves to the 4-line box (CANON §1). **Korean build:** a full 11,172-syllable 12 × 12 font; boxes hold 3 lines × 13 syllables with a portrait and 4 × 17 without.

**The ≤ 400-syllable subset (CANON §16c), owned here:**

| Block | Syllables | Requested by |
|---|---|---|
| Core (below, binding) | 152 | This doc |
| Hanmadi (40 words, CH-E1) | 100 reserved | epilogues.md |
| Seoul signage and shops | 80 reserved | overworld_and_towns.md |
| Letters and documents | 48 reserved | Scenario docs |
| QA spare | 20 | — |
| **Total** | **400** | |

```
강 민 준 서 연 최 재 원 윤 미 래 오 상 우 박 혜 진 도 현 뤼 실 브 레 별 의
음 악 에 게 년 월 일 후 시 이 열 것 괜 찮 아 하 나 둘 셋 얼 쑤 좋 다 빠 엄
마 교 수 님 동 지 팥 죽 안 돼 한 디 끝 씨 어 세 요 뭐 찾 으 사 물 놀 성 정
리 랑 보 신 각 양 화 울 호 선 을 로 홍 대 인 남 산 늘 트 피 노 비 스 습 관
장 구 꽹 과 징 북 명 휘 모 치 굿 거 자 덕 궁 돌 담 길 철 역 출 입 닫 힘 림
문 술 빛 색 프 묘 종 포 중 용 초 방 카 페 편 점 약 국 버 택 눈 밤 새 해 복
많 받
```

It covers every Korean name in the cast (Kang Min-jun, Seo-yeon, Choi Jae-won, Yoon Mi-rae, Oh Sang-woo, Park Hye-jin, Kang Do-hyun, 뤼실 오브레), 별의 음악, 민준 on the portrait's score, the KEY-39 label "서연에게 — 2026년 12월 22일 오후 5시 이후에 열 것", every word the style guide glosses (괜찮아, 하나 둘 셋, 얼쑤, 좋다, 오빠, 엄마, 아빠, 교수님, 동지, 팥죽, 안 돼, 끝, 민준아, 씨, 어서 오세요, 뭐 찾으세요), 한성음악원, 한마디, 사물놀이, 아리랑, the samulnori instruments and *jangdan*, Seoul place names, and core signage (지하철, 출구, 비상구, 화장실, 편의점, 약국, 노래방, 새해 복 많이 받으세요).

### 8.4 Dialogue box (UI-02; CANON §16a, binding)

| Element | Spec (box-relative px unless noted) |
|---|---|
| Box | 240 × 64 at screen (8, 152); at (8, 8) when the speaker stands in the lower third |
| Fill | Vertical gradient #2858B8 (row 0) → #303038 (row 63): HDMA ch1 rewrites the fill colour every scanline |
| Border / shadow | 2-px #F8F8F8 border; 1-px #101018 inner shadow on all four sides; interior 234 × 58 from (3, 3) |
| Portrait | 48 × 48 at (7, 8), showing through a transparent BG3 well (§4.5) |
| Text, with portrait | x 59–232 (**174 px**), **3 lines × 24 characters**, line tops at y 12, 24, 36 |
| Text, without portrait | x 7–232 (**226 px**), **4 lines × 30 characters**, line tops at y 6, 18, 30, 42 |
| Font | F1, 8 × 12 cell, advance ≤ 7 px; a hangul syllable 12 × 12 counts as 2 characters |
| Advance cursor | ▼ 8 × 6 at (224, 54), blinking 30 on / 30 off; absent on auto-advance |
| Name tab | At (8, −14): 14 px tall, text width + 8 px wide (≤ 15 characters, ≤ 113 px), same gradient and border |
| Language badge | F3 small caps on a #F8F8F8 plate, 24 × 9, straddling the top border at (208, −4) |
| Highlights | Box tiles use BG3 palette P0 (white + gold) or P1 (white + grey): **one highlight colour per box** |
| Choice window | Above the box, right-aligned: 172 px wide, 12-px rows, ☞ cursor; options ≤ 22 characters |
| Bite Your Tongue | A 2-px timer bar along the interior's bottom edge (y 59–60), draining over 180 frames, gold turning #F86040 in the last 60; the modern option carries the candle glyph and "+n" |
| Caption | Unboxed, centred, upper third (y 48–72), F1 white with a 1-px #101018 shadow, 2 lines × ≤ 30 characters, 120 frames |

```
   ┌──────────┐
   │ Lucile   │
┌──┴──────────┴──────────────────────────────────┤FRE├─────┐
│ ┌──────────┐ You came. I bet Théo two                    │
│ │          │ sous you'd sleep through                    │
│ │  PC-02   │ it.                                         │
│ │  smile   │                                             │
│ │  48×48   │                                             │
│ └──────────┘                                          ▼  │
└──────────────────────────────────────────────────────────┘
```

```
                              ┌────────────────────────────┐
                              │   Impressionism.  [c] +5   │
                              │ ☞ It has no name yet.      │
                              └────────────────────────────┘
   ┌──────────┐
   │ Lucile   │
┌──┴──────────┴────────────────────────────────────────────┐
│ ┌──────────┐ Father would have called                    │
│ │          │ this laziness. What                         │
│ │  PC-02   │ would you call it?                          │
│ │  laugh   │                                             │
│ └──────────┘                                             │
│▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀  ← 3-s timer          │
└──────────────────────────────────────────────────────────┘
```

```
   ┌───────────┐
   │ Ragpicker │
┌──┴───────────┴───────────────────────────────────────────┐
│ Rags, bones, bottles! Half                               │
│ this street went in the spring                           │
│ of '32. Their rags still find                            │
│ their way to me.                                      ▼  │
└──────────────────────────────────────────────────────────┘
```

The first mockup is a portrait box; the second a Bite Your Tongue prompt (`[SLIP:3]`, dialogue_style_guide §2.7): the modern option first with the candle glyph `[c]` and its cost, the cursor starting on the period phrasing, the timer draining along the bottom edge; the third the 4 × 30 box without a portrait.

### 8.5 Title screen (UI-01)

```
┌────────────────────────────────────────────────────────────┐
│                                                            │
│                 HARMONIES OF THE LOST ERA                  │
│                  ·  D E F♯ G A B C♯  ·                     │
│                                                            │
│                     ┌───────┬───────┐                      │
│                     │ baton │ quill │                      │
│                     ├───────┼───────┤                      │
│                     │ sword │ sabre │     the key hangs    │
│                     ├──── (7:51) ───┤     on the stand  ⚷  │
│                     │rapier │ folio │                      │
│                     ├───────┼───────┤                      │
│                     │hammer │ brush │                      │
│                     └───────┴───────┘                      │
│                                                            │
│                        ☞ New Game                          │
│                          Continue                          │
│                          Config                            │
│                                                            │
│             Play the future. Keep the secret.              │
└────────────────────────────────────────────────────────────┘
```

The Door's eight panels follow LM-01 note order (world_rules_and_lore §6.2). The Door zooms 1.0× → 1.6× in Mode 7 over the 8-bar intro of MUS-001; the hand-lettered logo and the menu sit in Mode 1 bands (§2.7). **States:** (A) first boot: hands at 7:51. (B) After either ending: hands at XII, fused into the key sigil; the menu adds **Reverie of the Window** and **Da Capo**; Seoul cleared adds snow drifting upward past the Door, Paris cleared adds a phone on the study floor. (C) Both endings cleared: the dust outline on the wall holds the portrait, its figure's hand lifted to tap the fallboard. Only state A appears in pre-launch material (vision_and_pillars spoiler policy).

### 8.6 Main menu (UI-03)

```
┌──────────────────────────────────────────────┬─────────────┐
│ ┌──────┐ Min-jun                      Lv 21  │☞ Items      │
│ │PC-01 │ HP   830 /  830                     │  Harmony    │
│ │      │ INS  112 /  112                     │  Repertoire │
│ └──────┘                                     │  Equip      │
│ ┌──────┐ Lucile                       Lv 21  │  Opus       │
│ │PC-02 │ HP   767 /  767                     │  Ensemble   │
│ │      │ INS  112 /  112                     │  Bonds      │
│ └──────┘                                     │  Status     │
│ ┌──────┐ Chopin                       Lv 21  │  Sketchbook │
│ │PC-06 │ HP   634 /  634                     │  Almanach   │
│ │      │ INS  127 /  127                     │  Config     │
│ └──────┘                                     │  Save       │
│ ┌──────┐ Delacroix                    Lv 21  ├─────────────┤
│ │PC-04 │ HP   830 /  830                     │ Time  17:02 │
│ │      │ INS   95 /   95                     │ 4,310 F     │
│ └──────┘                                     │ Admired     │
├──────────────────────────────────────────────┴─────────────┤
│ Delacroix's Studio                                         │
│ September 1833                                             │
└────────────────────────────────────────────────────────────┘
```

Portraits are the 48 × 48 Tier A art (current collar strip); a back-row member is drawn 8 px right. The footer repeats the scene's caption (place and date). In CH-E1 the money reads ₩, the Renown line becomes the Spotlight tier, and a 13th entry, **Phone**, follows Save (X opens it directly on Seoul maps).

### 8.7 Status (UI-11)

```
┌────────────────────────────────────────────────────────────┐
│ ┌──────┐ Min-jun            Lv 21      Bard / Conductor    │
│ │PC-01 │ HP   830 /  830    EXP          25,880            │
│ │      │ INS  112 /  112    Next level    1,521            │
│ └──────┘ Status  —          Row  Front                     │
├────────────────────────────────────────────────────────────┤
│ STR  19     ATK  56     AR    131     Fight                │
│ ART  28     DEF  37     EVA    0%     RECITAL · CONDUCT    │
│ TMP  24     RES  37     M.EVA  0%     Harmony · Synergy    │
│ LCK  28                               Item                 │
├────────────────────────────────────────────────────────────┤
│ Opus      ✦ La Mer               Passive  Perfect Pitch    │
│ Secrecy   37 · Murmured          Renown   318 · Admired    │
└────────────────────────────────────────────────────────────┘
```

Values are Min-jun's exact Lv-21 stats (CANON §5b growth; no Opus bonuses), with CH-09 anchor gear (ATK 56; DEF and RES 37, §10e). EXP 24,136 reaches Lv 21 and 27,401 Lv 22 (CANON §10a). Pressing ◄► pages through members; R pages to **Affinities** (elements resisted or weak from gear) and the **Cadenza** name once unlocked.

### 8.8 Equip (UI-07)

```
┌ Equip ─ Lucile ────────────────────────────────────────────┐
│  Weapon  ☞ Nocturne Brush       ATK  45                    │
│  Head      Prélude Bonnet                                  │
│  Body      Nocturne Shawl                                  │
│  Relic     Cartouche Glove                                 │
│  Relic     —                                               │
├──────────────────────────────┬─────────────────────────────┤
│  Rhapsodie Brush     ×1      │  ATK   45 → 54  ▲           │
│  Nocturne Brush      (equip) │  AR   109 → 127 ▲           │
│                              │  ART   29                   │
│                              │  DEF   33       RES  33     │
├──────────────────────────────┴─────────────────────────────┤
│ A brush of fine Kolinsky sable, bound in brass. ATK 54.    │
└────────────────────────────────────────────────────────────┘
```

Item names show the canon pattern "[Tier] [Class]" (CANON §14); items_and_equipment.md names the real stock. Party faces in the shop and Equip lists show a small smile (better), neutral (same) or frown (worse) per member.

### 8.9 Opus (UI-08)

```
┌ Opus ──────────────────────┬───────────────────────────────┐
│ ✦ OPS-13 ─ (not yet)       │ ✦ La Mer          Heat ●●●○○  │
│ ✦ OPS-14 Faune             │ Transcribed CH-08 (REP-36)    │
│☞✦ OPS-15 La Mer       [MJ] │ ──────────────────────────────│
│ ✦ OPS-16 Daphnis et Chloé  │ Clarity   ×5  ████████░░  80% │
│ ✦ OPS-17 La Valse     [LI] │ Encore    ×2  ███░░░░░░░  30% │
│ ✦ OPS-18 ─ (not yet)       │ Allegro   ×3  ██████████ ✔    │
│ ♪ OPS-01 … OPS-12 (period) │ Level-up  +1 ART              │
│ ✶ OPS-25 … OPS-32 (secret) │ Invocation  La Mer (×1)       │
└────────────────────────────┴───────────────────────────────┘
```

The list scrolls by family; a face tag shows who has a Score equipped. The right pane shows the Score's skills with learn rates and progress bars, its level-up bonus and Invocation; ✦ Scores show Heat as candle pips. *Illustrative contents:* skills_and_progression.md sets each Score's skills, rates and bonuses (the three skill names shown are CANON §10d cure and buff names; short Score titles such as "Faune" are that doc's to assign). **Transcription** happens at a Lectern: the Score appears letter by letter in Min-jun's hand over 60 frames, with the candle glyph and "+3" when a non-confidant is present (CANON §11c).

### 8.10 Harmony and Repertoire (UI-05, UI-06)

```
┌ Repertoire ─ Min-jun ──────────────────────────────────────┐
│ ☞ REP-01 Clair de lune         INS 12   ●●●○○   Debussy    │
│   REP-08 Ondine                INS 14   ●●●●○   Ravel      │
│   REP-12 Pavane                INS 10   ●●○○○   Ravel      │
│   REP-30 Jeong-dong Nocturne   INS  6   ○○○○○   Kang       │
│   REP-32 Prelude in C          INS  6   ○○○○○   Bach       │
├────────────────────────────────────────────────────────────┤
│ I Cantabile  →  II LIGHT +25%  →  III party heal           │
│ Onlookers 2 — Heat +3 when Movement I begins               │
└────────────────────────────────────────────────────────────┘
```

Movement I costs 6 + 2 × Heat (CANON §10b). Heat pips are grey out of battle and turn red with the projected gain when Onlookers are present (secrecy_and_trust §2.7). In CH-E2, future pieces are greyed at salons with "Not mine to play." (LAW-25). **Harmony** uses the same layout: the equipped Score's Invocation first, the R5 Signature second (marked S, as in the Bonds menu), then skills in the order skills_and_progression assigns, each with INS cost, a spread mark (L/R toggles single/all) and Heat pips where Anachronic. **Recital titles may run to 20 characters** in these lists and in the battle Recital window, which opens full width (CCR in Canon Additions).

### 8.11 Secrecy HUD and its successors (UI-16)

```
 Incognito   Murmured    Watched     Hunted      Compromised
     .           ;          (~)         )(          \*/
     |           |          | |        |~~|         |~|
   [===]       [===]       [===]       [===]       [===]
   0–19        20–39       40–59       60–79       80–99
   steady      flickers    tall amber  red-orange  guttering,
   white-gold              smoke wisp  wax runs    red halo 1 Hz
```

| Element | Spec |
|---|---|
| Candle | 16 × 32 at screen (232, 8) on Paris maps, drawn on BG3 (so it sits above everything) with one 4-colour palette rewritten per tier; tier coded by height and motion (secrecy_and_trust §2.7). Flame #F8F0B0 (Incognito) → #F8B040 (Watched) → #F06020 (Hunted) → halo #C82020 (Compromised) |
| Exact value | Hold Select on a field map, or open Status: "37 · Murmured" on the brass base in F3 |
| Gains / losses | Gold "+n" rises 8 px over 30 frames; blue "−n" sinks; Lucile's report gains are silent (the candle simply grows during the next chapter caption) |
| Variants | Carriage-lantern frame (CH-10–CH-11); the Prefecture seal on the base (CH-14); snuffed on the crypt stair (CH-15) |
| Battle | The candle at (232, 4) only while an Onlooker remains; Onlookers stand at y 16–40 on BG3 with 3-pip timers |
| Spotlight (CH-E1) | A 56 × 8 bar at (192, 8) with a phone glyph and the tier name: Quiet · Trending · Headline · Viral |
| Canvas Ledger (CH-E2) | A 24 × 20 framed-canvas icon at (224, 8) with "16/19" in F2: canvases in hand of the 19 survivors; a red corner pip flashes when one is taken |

### 8.12 Bonds: the Trust Network (UI-10)

```
┌ Bonds ──────────────────────────────────────────────────────┐
│   Lucile     R3 cap  ♥/  [··········] frozen        Nohant  │
│   Berlioz    R6          [████████░░] 470/550 ∞ S   Paris   │
│   Delacroix  R10 ⌂       [██████████] 1000  ∞ S C T Paris   │
│ ☞ Alkan      R5          [█████░░░░░] 330/420 ∞ S   On tour │
│   Chopin     R10 ⌂       [██████████] 1000  ∞ S C T Paris   │
│   Liszt      R6          [█████████░] 480/550 ∞ S   On tour │
│   Farrenc    R4          [████████░░] 230/300 ∞     On tour │
├─────────────────────────────────────────────────────────────┤
│ Alkan · Rank 5 · next: R6 Covering Laugh at 420 BP          │
│ Bond quest: The Railway Étude  ▸ in progress                │
│ Notes ▸     Duo: Pédalier Duo ∞     Tell the truth: Not yet.│
└─────────────────────────────────────────────────────────────┘
```

Bars fill from the current rank's threshold to the next (CANON §11f). Icons: ∞ Duo with Min-jun (R3), S Signature (R5), C Cadenza (R7), T Trio eligibility (R8), ⌂ the confidant's **door**. **Lucile while Fractured:** a cracked heart, the capped rank, a grey frozen bar and no Duo link; each Mending re-draws the crack one stage smaller. **R9 ★** marks 1000 BP awaiting the finale; her Noon gate reads "Rank 7 awaits: The Hours of Light — Noon." (secrecy_and_trust §3.1). Absent members show where they are (CH-10: Berlioz newly married, Delacroix on the Salon du Roi, Chopin on his Op. 10 proofs). **The Horizon is never shown**; the Sketchbook (UI-12) is its only gauge.

### 8.13 Salon programme and *Phrase* (UI-19, UI-20)

```
┌ Salon Lavergne · rue de Provence · Tier 2 · Romantic ──────┐
│ Programme                          Brilliance  Heat  Mood  │
│ 1 ☞ Clair de lune — Debussy           ★★★      ●●●   Rom.  │
│ 2   Jeong-dong Nocturne — Kang        ★★       —     Rom.  │
│ 3   Prelude in C — Bach               ★★       —     Sac.  │
├────────────────────────────────────────────────────────────┤
│ Attribution  ☞ Name the composer · An old teacher's piece  │
│                My own                                      │
│ Projected Secrecy  +6 to +20  (Cabal Presence 0–3)         │
│ Fee 60 F × Rapture        Evenings left  2                 │
└────────────────────────────────────────────────────────────┘
```

```
┌ Rapture [██████████████░░░░░░░░░░]  58     Masks  ◐ ◐ ○ ───┐
│      guests on BG: fans flutter, a lorgnette rises         │
│                                                            │
│  ║                                                         │
│══╬═════════════════════════════════════════════════════════│
│  ║   [A]       [B]   [A]         [Y]     [X]       [A]     │
│══╬═════════════════════════════════════════════════════════│
│  ║         L <<<<<<<<       >>>>>>>> R                     │
│══╬═════════════════════════════════════════════════════════│
│  ║ ← hit line          notes scroll right to left          │
│                                                            │
│   Min-jun at the piano · movement 2 of 3                   │
└────────────────────────────────────────────────────────────┘
```

Projected Secrecy is Heat × (1 + Cabal Presence) × attribution factor, capped at +20 per salon before the Renown multiplier (CANON §11g): naming Debussy gives 3 × (1–4) × 2 = 6–24, shown as "+6 to +20". "My own" is greyed after the Vow (CH-14). *Phrase:* button prompts ride the staff's beat lines; L/R hairpins are held for dynamics; hits flash gold (Perfect) or white (Good). Rapture shows as a bar and as the audience: past 40 fans stop, past 70 a guest rises, past 90 the candles brighten. Cabal masks (0–3) reveal themselves among the guests as the performance begins. Busking (CH-E1) reuses *Phrase* with ₩ and the 8-spot ladder rank (Rookie → Legend).

### 8.14 Piano Duel (UI-21)

```
┌────────────────────────────────────────────────────────────┐
│ Favor  −100 ◄━━━━━━━━━━━━━━━━━┿━━━━━━━━━━━━━━━━━━━► +100   │
│                         ▲ −20  (rigged action)             │
│ Thalberg  ████████████████████░░░░   Passage 3 / 8         │
│ Min-jun   ███████████████░░░░░░░░░   (Composure)           │
│                                                            │
│   ┌──────┐   ═══ two pianos, keyboards facing ═══  ┌─────┐ │
│   │Thalb.│  * third hand on every 3rd Passage      │ MJ  │ │
│   └──────┘                                         └─────┘ │
│                                                            │
│                       Bravura ▲                            │
│  ┌──────┐    Cantabile ◄   ●   ► Pianissimo                │
│  │NPC-33│              Ornament ▼        Improvise: Select │
│  └──────┘   (Rossini judges)    metronome: A on the beat   │
└────────────────────────────────────────────────────────────┘
```

**Wheel on the D-pad:** each type beats the one clockwise from it: Bravura (▲) > Pianissimo (►) > Ornament (▼) > Cantabile (◄) > Bravura (CANON §11g). After choosing, a metronome needle sweeps; A on the downbeat rates the Passage Perfect, Good or Late. Thalberg's Three-Hand Effect is telegraphed one Passage ahead by a ghost hand over his sprite. The judge's Tier B portrait reacts each Passage. **Variants:** the Rhetoric duel (BOSS-20) relabels the wheel Wit ▲ > Charm ► > Evidence ▼ > Silence ◄, with a quill, a rose, a ledger and closed lips; the Brushwork duel (BOSS-32) reads Light > Colour > Composition > Feeling, with Lucile leading and Min-jun's Conduct as a side command.

### 8.15 Battle (UI-17) and the Octave (UI-23)

```
┌────────────────────────────────────────────────────────────────┐
│[Fog]            Ondine (banner)                       [candle] │
│[Rain]            ○ ○ ○   Onlookers, 3-pip timers               │
│                                                                │
│    ┌────┐   ┌────┐                          ┌──┐               │
│    │ E1 │   │ E2 │                          │MJ│ ♪II           │
│    └────┘   └────┘                          └──┘               │
│                                               ┌──┐             │
│        ┌────────┐                             │LU│             │
│        │   E3   │                             └──┘             │
│        │ 64×64  │                               ┌──┐           │
│        └────────┘                               │CH│           │
│                                                 └──┘           │
│                                                       ┌──┐     │
│                                                       │DE│ back│
│                         [███████████████░░░░░░░░░░░░░░░]       │
├────────────────────────┬───────────────────────────────────────┤
│ Pickpockets ×2         │ Min-jun    830/ 830  100  [████████]  │
│ Gaslight Wisp          │ Lucile     604/ 767   86  [█████░░░]  │
│                        │ Chopin     634/ 634  127  [██░░░░░░]  │
│                        │ Delacroix  512/ 830   71  [████████]  │
└────────────────────────┴───────────────────────────────────────┘
```

Geometry is combat_ensemble §2.1 (binding there): enemy zone (8, 16, 128 × 128); party slot *n* at x = 184 + 8(*n* − 1), y = 40 + 24(*n* − 1), back row +16 px; enemy list (0, 152, 96 × 72); party window (96, 152, 160 × 72); Crescendo strip (96, 144, 160 × 8); banner (20, 4, 212 × 14); Light icon (4, 4); field icon (4, 22); candle (232, 4). When a member is Ready the command window (Fight / *Unique* / Harmony / Synergy / Item) covers the enemy list; ► opens Row · Defend · Tacet · Swap · Pilfer. The Recital, Plein Air and Canvas sub-windows open full width over both windows. **Octave formation:** two columns of four at x = 168 and x = 200, enemies inside the left 120 px, the party window split into two 128-px panes of four rows (name, HP, ATB), the enemy list in the banner, and an eight-note staff in place of the Crescendo strip, each note lighting in its pitch colour (§3.5). The eight members share five pair palettes (§2.3), leaving palettes for the pillars, effects and digits.

### 8.16 Grand Concert split screen (UI-22)

```
┌─────────────────────┬────────────────────┬─────────────────────┐
│ STAGE        ● ● ○  │ RAFTERS            │ CORRIDORS           │
│ Rapture ██████░ 64  │ Horns 3/4  Rec 60% │ Timer 9   Roussel ▓▓│
│ Mvt II / III        │ DE LU AL  ▪ ▪ ▪    │ CH FA Off  ▪ ▪ ▪    │
├─────────────────────┴────────────────────┴─────────────────────┤
│  house in shadow: Rapture shown as fans, lorgnettes, a hush    │
│                                                                │
│      ┌──────┐   ══ two pianos, lid to lid ══   ┌──────┐        │
│      │Liszt │                                  │MinJun│        │
│      └──────┘          Berlioz on the podium   └──────┘        │
│                                                                │
│ ┌────────────────────────────────────────────────────────────┐ │
│ │ Passage: Ornament ☞     metronome ─────●─────  (A)         │ │
│ └────────────────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────────┘
```

A 256 × 32 strip shows all three fronts at once in 16 × 16 tokens (sprites cannot scale): the active front's panel is lit gold, its three rotation pips count the front turns left before the switch (combat_ensemble §11.2), and each panel carries its key state (Rapture, the recording percentage and horns left, BOSS-19's timer). Below it the active front plays in full: the Stage as a duet duel, the Rafters and Corridors as normal battle layouts. A switch is the 90-frame rope-and-curtain wipe. **The eight-bar rescue** interrupts with a banner, "Lucile is cornered! Leave the piano?" and the cost "Rapture −15". Before the battle, an establishing shot shows the Salle Le Peletier in cross-section (stage below, fly gallery above, corridors behind), panned in one take (vision_and_pillars screenshot #7).

### 8.17 Save / Load (UI-15)

```
┌ Save ──────────────────────────────────────────────────────┐
│ ┌────────────────────────────────────────────────────────┐ │
│ │ 1  [MJ][LU][CH][DE]   Delacroix's Studio               │ │
│ │    CH-09 Confessions  September 1833   Lv 21   17:02   │ │
│ │    4,310 F   candle 37                                 │ │
│ └────────────────────────────────────────────────────────┘ │
│ ┌────────────────────────────────────────────────────────┐ │
│ │ 2  [MJ][LU][LI][FA]   Nohant                           │ │
│ │    CH-10 Nohant       October 1833     Lv 23   18:40   │ │
│ └────────────────────────────────────────────────────────┘ │
│ ┌────────────────────────────────────────────────────────┐ │
│ │ 3  — empty —                                           │ │
│ └────────────────────────────────────────────────────────┘ │
│ ╔════════════════════════════════════════════════════════╗ │
│ ║ ✦ Eve of the Window   The Heart Chamber                ║ │
│ ║   Saturday 21 December 1833 · cannot be overwritten    ║ │
│ ╚════════════════════════════════════════════════════════╝ │
└────────────────────────────────────────────────────────────┘
```

Each slot shows the active party's field sprites, the scene's caption, chapter number and title, leader level, play time, money and the candle tier. The **Eve of the Window** slot (CANON §11h) appears once created, in a gold double frame. CH-E1 slots read "Jeong-dong · December 2026", ₩ and the Spotlight tier, and the save is made from the phone's Notes app (UI-28). The confirm sound is a single Lectern chime; on Load, the slot's caption plays over the fade-in.

### 8.18 World map and flight (UI-24, UI-25)

```
┌────────────────────────────────────────────────────────────┐
│ Faubourg Saint-Germain                            [candle] │
│                                                            │
│   slate roofs · the Seine · the Panthéon in scaffolding    │
│                                                            │
│                          [MJ]                              │
│                                                            │
│                                               ┌──────────┐ │
│                                               │ ·  Paris │ │
│                                               │    ▲     │ │
│                                               └──────────┘ │
└────────────────────────────────────────────────────────────┘
```

On LOC-W01/W02/W03 the district name appears top-left for 90 frames on entering its icon. On W01 and W02, X toggles a 64 × 48 minimap (bottom right; default on in flight), because Select is reserved for the Secrecy value; on W03, X opens the phone, whose Map app serves instead. Landmarks are 2 × 2 to 4 × 4 icons drawn to the §6.3 checklist; Dusk and Night are palette shifts (overworld_and_towns §4.2). **Flight** (Mode 7, §2.7): the horizon sits at line 64 under an HDMA sky gradient; the gondola of *La Lumière* is a 64 × 32 OBJ at the bottom centre that banks 2 frames into turns; the minimap shows moorings; a daytime take-off inside Paris flashes "+2" on the candle (CANON §11h). In the CH-E2 finale flight a 64 × 6 canvas HP bar sits under the minimap.

### 8.19 Window Clock and Phone (UI-27, UI-28)

```
                 ┌────────────────────────┐
                 │  ◷  07:56      6:41    │
                 └────────────────────────┘
   staff:  D  E  F♯  G  A  B  C♯  ·  D
           ●  ●  ●   ○  ●  ○  ○      ○
```

The Window Clock (CANON §11i) sits top-centre: a pocket-watch face whose hands run from 7:51 to 8:03 and the 12:00 countdown beside it, paused in dialogue and menus, turning #F86040 under 2:24. Along the bottom, the eight-note staff: Min-jun's D is lit from the start; each farewell lights its friend's note in pitch colour (a blue grace note for Julien); the octave D stays dark until Lucile answers the Question, in either branch.

```
          ┌──────────────┐
          │ 16:58   ▮▮▮▯ │
          │ ┌──┐┌──┐┌──┐ │
          │ │Mp││Ms││Cm│ │   Map · Messages · Camera
          │ └──┘└──┘└──┘ │
          │ ┌──┐┌──┐┌──┐ │
          │ │Tr││Mu││Wl│ │   Translate · Music · Wallet
          │ └──┘└──┘└──┘ │
          │ ┌──┐         │
          │ │Nt│         │   Notes (save, CANON §11h)
          │ └──┘         │
          └──────────────┘
```

The phone (CANON §4f) is a 96 × 176 frame centred on screen, in a flat modern palette (#F8F8F8, slate #384050, teal #40C8B8), the only UI not drawn in the box gradient. Its lock screen shows one of the CH-14 photos (KEY-02) if any were taken. Camera opens the album as Mode 3 stills; Translate logs Hanmadi words.

### 8.20 Minor screens

| ID | Screen | Spec |
|---|---|---|
| UI-04 | Items | Tabs Consumables · Equipment · Key Items (256 slots, 99 per stack; key items unlimited, CANON §14); descriptions in period voice; "Sort" groups by class icon |
| UI-09 | Ensemble | Active four and reserve (four, five with Julien) as field sprites; row toggle; swap; guests shown with a padlock; Farrenc's Equal Measure shown as "Reserve EXP 100%" |
| UI-12 | Sketchbook | The last page as a Mode 3 plate (the six states of LAW-23.5); then Delacroix's 36 Studies (STU-01–36) as a 6 × 6 grid of 24 × 24 thumbnails, unrecorded pages blank |
| UI-13 | Almanach | Tabs People · Places · Glossary · Gazette (press items and Intercepted Notes) · Papers (in-world documents, if world_rules_and_lore's CCR is adopted); Tier A/B entries show the neutral portrait |
| UI-18 | Victory and Fine | Reward window in combat_ensemble §12.2 order; level-ups chime per member. **Fine:** the word set like a score's final double bar ‖, MUS-103 under it, options Retry battle / Return to last save |
| UI-26 | Shop and inn | Shopkeeper sprite and name; Buy / Sell; per-member compare faces; prices in F (sous below 1 F, "Bread 8s") or ₩; inn rest is a 60-frame candle-snuff fade |
| UI-29 | Crypt-door prompt | Unfinished quests by title only (CANON §0c), then "Go back" / "Go down" |
| UI-30 | Ending roll | One Mode 3 vignette per party member in the branch, then up to 8 end cards of ≤ 2 plain F1 lines on black, 240 frames each (CANON §1 Tone Rule 6) |
| UI-31 | Command overlays | ÉTUDE: arrow sequence on a strip with a 2.0-s bar · BEAT: rings closing on each beat of the *jangdan* · IMPROVISE: three reels of ii, V, I, IV, ♭VII, ♭II stopping one by one · Rehearsal Mode shows a "♪ Rehearsal" tag on each |

### 8.21 Accessibility and Config (UI-14)

**One difficulty** (CANON §11j). Battle options follow combat_ensemble §14; the presentation options are this doc's.

| Option | Values (default) | Effect |
|---|---|---|
| Battle Mode / ATB Speed | Active, **Wait** / 1–6 (**4**) | CANON §10b |
| Text Speed / Battle Message Speed | 1–5 (**3**) | 4 / 3 / 2 / 1 frames per character, or instant |
| Auto-advance Text | **Off** / On | Holds each box 90 frames + 2 per character |
| Rehearsal Mode | **Off** / On | Every timing input perfect at ×0.8 (CANON §11j) |
| Flash Reduction | **Off** / On | Full-screen flashes ≤ 3 per second at half brightness |
| Screen Shake | **On** / Off | — |
| Distortion | 0 / 50 / **100%** | Labyrinth wobble, tear bands and mosaic pulses scaled |
| Mode 7 Motion | **Full** / Reduced | Reduced: rotation capped at 45°, no banking |
| Candle Flicker | **On** / Steady | Light pools hold one radius |
| Box Style | **Gradient** / High Contrast | High Contrast: solid #182048 fill, 3-px border |
| Colour Assist | **Off** / Deuteranopia / Protanopia / Tritanopia | Alternate CGRAM tables for element, Favor, Rapture and HP colours; every shape code unchanged |
| Audio Cue Visuals | **Off** / On | The ATB ding, telegraphs and Recital chimes also flash an icon |
| Read Aloud | **Off** / On | Platform text-to-speech reads each box in the build's language |
| Dash | **Hold** / Always | Towns and interiors only (§2.8) |
| Display | **Square pixels** (×3 / ×4 / ×5) / 4:3 CRT aspect; Scanlines **Off** / On | §2.1 |
| Button remapping | Full | Every input, including Étude and BEAT |

---

## 9. Production Budget

| Asset | Count | Basis |
|---|---|---|
| PC sprite frames | ≈ 1,200 | 52 shared frames per costume set (§5.1–§5.2) plus bespoke; Min-jun's four sets ≈ 330, Lucile's two ≈ 200, nine others ≈ 75 each |
| Tier B and guest sprites | ≈ 650 | 43 × 13 field frames + 10 guest battle sets × 9 |
| Tier C bases | 32 bases, 384 frames, 66 palette swaps | §4.3 |
| Portraits | 342 expressions + 8 collar strips | Tier A 17 × 10 (one art set serves ANA-03 and PC-11); Tier B 43 × 4; +8 if FIC-10/11 are promoted |
| Tilesets | 31 (TS-01–07, TS-10–26, TS-30–36) | §6.2 |
| Showcase plates | 31 | Portrait ×2, Lucile's canvases ×5, exhibition ×5, Sketchbook ×6, ending vignettes ×13 (Seoul branch 4, Paris branch 9) |
| UI screens | 31 | §8.1 |

Order of work: the vertical slice (vision_and_pillars: screenshots #1 and #2) first, so LOC-S02, LOC-P05, Min-jun's three costumes, Lucile's 1833 set, UI-02, UI-03 and UI-17 pass Constraint Lint before anything else is drawn.

---

## Canon Additions & Cross-Doc Notes

**Canon Change Requests** (until adopted, the stated fallback applies):

- **CCR: Visual keys for PC-09, PC-10 and PC-11** in CANON §5g (§3.6): Seo-yeon's long black padded coat, grey scarf and violin case (accent rosin amber); Jae-won's red club windbreaker, white hoodie, knit cap and janggu with *obangsaek* ribbons; Julien's blue-grey frock coat worn open with no cravat. Why: §5g gives none, and sprites and portraits need them. Fallback: none needed for SY and JW (CH-E1 only); Julien already wears the canon's Hour of Smoke blue-grey. Touches: epilogues.md, party.md, anachronists.md.
- **CCR: Min-jun's CH-E1 costume** (§4.2): his own charcoal parka over the tailcoat's waistcoat, the midnight-blue cravat worn as a scarf, from LOC-S04 onward. Why: §5g ends at the CH-05 tailcoat. Fallback: the tailcoat throughout CH-E1. Touches: epilogues.md.
- **CCR: Two art-owned ID families**, **TS-##** (tilesets, §6.2) and **UI-##** (screens, §8.1). Why: dungeons, world and scenario docs need stable names for tilesets and screens. Fallback: cite this doc's section numbers. Touches: overworld_and_towns.md, dungeons.md, all docs that name a menu.
- **CCR: Recital titles may run to 20 characters** in the Repertoire menu and the full-width battle Recital window (§8.10), e.g. "Jeong-dong Nocturne" (19). Why: CANON §16h caps skill names at 16 and REP titles are not listed. Fallback: the 16-character form "Jeong-dong Noct.". Touches: skills_and_progression.md, combat_ensemble.md.

**Shared facts defined here** (art_and_ui owns them, CANON §0b):

- **Field walk speed** (§2.8): dungeons 1 px per frame (confirming formulas_and_curves §5.7's calibration), towns and interiors 1 tile per 10 frames, overworlds 1 tile per 8 frames; **dash only in towns and interiors**. Touches: formulas_and_curves.md, overworld_and_towns.md, dungeons.md.
- **Hardware rules other docs must design to:** on a field screen, the five ensemble pair palettes plus **one** guest or named-NPC palette, and ≤ 7 actors per 32-px band (scenes needing more named NPCs swap palette 5 between shots or pose extras on BG); **≤ 2 light pools and ≤ 2 Watcher or patrol sight cones per screen** (1 cone in lantern-lit Gloom such as CH-01's patrols); ≤ 256 metatiles and 6 scenery palettes per map; one highlight colour (`[C:gold]` or `[C:grey]`) per text box. Touches: dungeons.md, overworld_and_towns.md (cone placement), dialogue_style_guide.md (the highlight rule), all scenario docs.
- **The hangul subset** (§8.3): the 152 core syllables and the 400-syllable allocation; Hanmadi words must fit the 100-syllable reserve. Touches: epilogues.md, overworld_and_towns.md, dialogue_style_guide.md.
- **Narrative palette rules** (§3.5): the Violet Shadow Rule from Lucile's CH-05 dawn lesson; the Wrong Colour reserved for CHRONO, the Engine, Archon's final forms, the Amalgam seams and the static automata; pitch colours per LM-01 note. Touches: bestiary.md, bosses.md, dungeons.md, audio_and_music.md (the synth-patch twin).
- **Presentation beats:** every battle Recital opens with the fallboard tap; the Window Clock's eight-note staff, whose octave D lights only at Lucile's answer; title-screen states B and C after the endings (pre-launch material uses state A only); the "page turn" battle transition; the Dead Heart as the one map with zero animation. Touches: combat_ensemble.md, act4_and_epilogue.md, epilogues.md, vision_and_pillars.md, audio_and_music.md.
- **Octave palettes:** the eight members fit five ensemble pair palettes (§2.3), not eight as vision_and_pillars §10 suggested; large bosses stay on BG as that doc recommends, and the three freed palettes carry effects, the light pillars and digits. Touches: vision_and_pillars.md, bosses.md.
- **Mode 7 and mode-split uses** (§2.7), including BOSS-28's Engine as the Mode 7 layer with a mid-frame switch to Mode 1 for the battle windows, and BOSS-25's rotating Varga plane. Touches: bosses.md.
- **Defeat presentation** (§4.4): humans routed or subdued, Echoes dissolving into sound rings, automata scattering gears, tableaux rolling up, Ossia phantoms inverting back to true colour; Stilled Echoes have no idle animation. Touches: bestiary.md, bosses.md.
- **UI placements** not fixed elsewhere: the Spotlight bar and the Canvas Ledger icon (§8.11), the phone as a 13th main-menu entry in CH-E1 (X opens it on Seoul maps), the minimap on X on W01 and W02, the Window Clock top-centre, and Read Aloud, Distortion, Mode 7 Motion, Candle Flicker, Box Style and Colour Assist in Config. Touches: secrecy_and_trust.md, combat_ensemble.md (Config), epilogues.md.
- **Portraits:** 14 drawing colours plus the well colour #182040; collar strips for costume changes; the dialogue_style_guide's proposed Tier A extras are drawn now and ship behind their fallbacks; likenesses follow 1830–34 sources. Touches: dialogue_style_guide.md, historical_cast.md.
- **Supports:** the dialogue_style_guide's `{ANIM}` set (§5.3), emote set (§4.8), language badges and text speeds (§8.3, §8.21) are all supplied as specified there.
