# Dialogue & Script Style Guide

Status: v1.0 — 2026-10-06 · Owns: script formatting conventions, scene-header and stage-direction notation, portrait expression tags and name tabs, character voice guides and voice samples, battle barks, NPC chatter rules, language usage (English master, French, Korean), banned phrases, localisation rules for text · Depends on: secrecy_and_trust (per-event values, Horizon bands, choice presentation), art_and_ui (font, portraits, box and Config UI), audio_and_music (SFX names), historical_cast (historical_cast owns NPC voices (CANON §0b); §4.3–§4.4 summarise and must match it), overworld_and_towns (the 40 Hanmadi words, §8.2) · Canon: docs/00_CANON.md

> Every writer on every scenario, quest, bond, Almanach and battle-text file uses this guide. Where it restates the canon (CANON §16a, §16b–g), the canon is the source; where it adds conventions, they are binding for all writing docs (CANON §0b: "Text format, portrait tags, barks, voice samples"). **Every sample line here is original game dialogue.** None reproduces a documented quotation of a real person; lines lifted from the canon are marked *(canon)*.

## Contents

1. [The Text Box](#1-the-text-box)
2. [Script Format](#2-script-format)
3. [Portrait Expressions and Name Tabs](#3-portrait-expressions-and-name-tabs)
4. [Voice Guides](#4-voice-guides)
5. [Battle Barks](#5-battle-barks)
6. [NPC Chatter](#6-npc-chatter)
7. [Language Usage: French, Korean, and the Romance](#7-language-usage-french-korean-and-the-romance)
8. [Banned Phrases, Narrator Anachronisms, Localisation](#8-banned-phrases-narrator-anachronisms-localisation)
9. [Canon Additions & Cross-Doc Notes](#canon-additions--cross-doc-notes)

---

## 1. The Text Box

### 1.1 Box specification (restated from CANON §16a/§16h; the canon wins on any difference)

| Property | Specification |
|---|---|
| Screen | 256 × 224 |
| Box | 240 × 64 px, anchored at the bottom of the screen, or at the top when the speaker stands low on screen (art_and_ui §8.4 places it at (8, 152) or (8, 8)); blue → dark-grey vertical gradient, 2-px white border, 1-px dark inner shadow |
| With portrait | A 48 × 48 static portrait at the left; text **3 lines × 24 characters** in a 174-px area |
| Without portrait | Text **4 lines × 30 characters** in a 226-px area (Tier C speakers, documents, system lines) |
| Font | Variable-width, 8 × 12 cell; glyph advance ≤ 7 px including 1-px spacing |
| Hangul | A syllable is a 12 × 12 glyph and **counts as 2 characters** |
| Name tab | Above the box's top-left edge, filled from the portrait ID (`[N:]` overrides it); ≤ 15 characters |
| Choice options | ≤ 22 characters each; the full line is spoken after selection |
| Box count | ≤ 6 boxes per speaker before another voice or an action; a lecture ≤ 3 boxes (Tone Rule 3) |
| Captions | Place and date only, 2 lines of ≤ 30 characters: place on line 1, date on line 2 |

**Additions (this guide).**

| Property | Rule |
|---|---|
| Advance cursor | A blinking ▼ at the box's bottom right while it waits for a button; absent on an auto-advance box (`[D:n]` at box end, §1.2) |
| Font banks | Roman and italic banks of the canon variable-width font (art_and_ui F1). Italic is the only emphasis the font has: no bold, no underline |
| Print speed | Config text speed 1–5 (CANON §11j) prints one character every 4 / 3 / 2 / 1 frames, or the whole box at once; 3 is the default. `[D:n]` delays are absolute and ignore text speed |
| Emphasis | `*word*` sets italics: foreign words (§7), titles of works, and stress (at most one stressed word per box). Never shout in capitals: a shout is `!` plus `{SHAKE:box}` (§2.4). Capitals are reserved for command names in tutorials (RECITAL, PLEIN AIR) and printed signage |
| Auto-advance (Config) | With art_and_ui §8.21's "Auto-advance Text" **On**, a box ending in an implicit `[W]` holds 90 + 2 × its characters frames, then advances; a mid-box `[W]` continues after 60 frames; `[D:n]` keeps its n; `[Q:]` and `[SLIP]` never auto-advance. **Off** (the default): every `[W]` waits for a button |

### 1.2 Tag syntax (canon tags; the full and only set)

| Tag | Rule of use |
|---|---|
| `[P:ID:expr]` | First thing in a box. IDs are character IDs (PC, NPC, FIC, ANA), never GST. Julien is `ANA-03` until SQ-21, `PC-11` after (same art) |
| `[N:Name]` | Name-tab override: Tier C speakers, unknown speakers (`[N:???]`), documents (`[N:Le Corsaire]`) |
| `[W]` | Every box waits for a button at its end without being told to (the implicit `[W]`). Write `[W]` explicitly only **mid-box**, for an FF6 beat where the text resumes in the same box |
| `[PB]` | Same speaker, fresh box; each `[PB]` counts toward the 6-box limit |
| `[D:n]` | n frames (60 = 1 s). Mid-box: a timed pause in printing. **A box whose last code is `[D:n]` suppresses the implicit `[W]` and auto-advances after n frames** (cutscene sync, the Window Clock, battle text, field barks) |
| `[C:gold]…[/C]` | `gold`: key terms, items and places that open an Almanach entry, first mention per chapter. `grey`: muttered asides and whispers. One highlight colour per box (art_and_ui §8.4): a box never mixes gold and grey |
| `[SFX:name]` | Fires at its print position. `[SFX:name]` names come from audio_and_music §8; this guide's starter set (§2.5) is kept there, marked † |
| `[MUS:…]` | `[MUS:LM-22]` (the leitmotif's main track), `[MUS:fade:90]`, `[MUS:silence]`; fixed canon tracks may be cited as `[MUS:MUS-095]` |
| `[K]…[/K]` | Hangul run, drawn from the ≤ 400-syllable subset (CANON §16c) |
| `[Q:a\|b]` | **2–3 options**, each ≤ 22 characters; the full line is spoken after selection; no cancel. An option that costs Secrecy shows the candle glyph and "+n" after its label (secrecy_and_trust §6.1). Exceptions: Confided-line choices (`[CONF:]`, CANON §11f) and Horizon choices (`[HZ:]`) never show a glyph, value or hint, even though a shared Confided line costs +8 Secrecy at chapter end (secrecy_and_trust §6.1) |
| `[SLIP:3]…[/SLIP]` | Wraps a `[Q:]`. Option 1 is the modern phrasing (candle glyph and "+n"), option 2 the period phrasing; the cursor starts on option 2; a timer bar drains for 3 s and on timeout the period phrasing plays (secrecy_and_trust §2.4.3) |
| `[in German]`, `[in French]` | First thing after the portrait. Further instances (`[in English]`, `[in Korean]`, `[in Polish]`, `[in Latin]`, `[in Hebrew]`) are a Canon Change Request (§7.4; final section) |
| State tags | `[BP:PC-07:+15]` `[SEC:+5]` `[HZ:W3]` `[CONF:CH05-03]` `[OV:+1]` `[SHD:+1]` `[REN:+n]` `[GOLD:+n]` `[GET:KEY-16]` `[FLAG:name]` `[IF:name]…[/IF]` `[EVE:-1]` `[LIGHT:Dawn]`. **Never invent others.** HZ, CONF and SHD are never shown to the player. HZ always cites a LAW-23 row, never a number |

**Punctuation.** The ellipsis is one glyph (…), never three dots; an interrupted line ends in an em dash (—). Speech carries no quotation marks (the name tab says who speaks); quotations inside speech use curly double quotes; « guillemets » appear only in French documents shown in French (§7.1).

### 1.3 Rendered examples

*Schematic drawings: every box is drawn 40 columns wide; real widths are pixels (CANON §16a). Hangul is drawn double-width because it counts double. Two schematic marks take no width on screen:* `_…_` *encloses italics and* `‹…›` *the gold highlight.*

**Portrait box.** Raw line: `LUCILE [P:PC-02:smile] You came. I bet Théo two sous you'd sleep through it.`

```
   ┌────────┐
   │ Lucile │
┌──┴────────┴──────────────────────────┐
│ ┌─────────┐ You came. I bet Théo two │
│ │PC-02    │ sous you'd sleep through │
│ │smile    │ it.                      │
│ └─────────┘                         ▼│
└──────────────────────────────────────┘
```

**No-portrait box** (Tier C). Raw line: `[N:Ragpicker] Rags, bones, bottles! Half this street went in the spring of '32. Their rags still find me.`

```
   ┌───────────┐
   │ Ragpicker │
┌──┴───────────┴───────────────────────┐
│ Rags, bones, bottles! Half           │
│ this street went in the spring       │
│ of '32. Their rags still find        │
│ me.                                 ▼│
└──────────────────────────────────────┘
```

**Hangul** (괜찮아 = 6 characters). An 1833 private moment, so the gloss obeys §8.1 ("it's all right", never "okay"). Raw line: `MIN-JUN [P:PC-01:homesick] [K]괜찮아[/K] (*gwaenchana*, “it's all right”). Seo-yeon always said it.`

```
   ┌─────────┐
   │ Min-jun │
┌──┴─────────┴─────────────────────────┐
│ ┌─────────┐ 괜찮아 (_gwaenchana_,    │
│ │PC-01    │ “it's all right”).       │
│ │homesick │ Seo-yeon always said it. │
│ └─────────┘                         ▼│
└──────────────────────────────────────┘
```

**Italics.** Raw line: `MIN-JUN [P:PC-01:neutral] *Gaspard de la nuit*, by Maurice Ravel. “Ondine.”` The title prints from the italic bank; the composer is named, as in every story performance (LAW-20).

```
   ┌─────────┐
   │ Min-jun │
┌──┴─────────┴─────────────────────────┐
│ ┌─────────┐ _Gaspard de la nuit_, by │
│ │PC-01    │ Maurice Ravel. “Ondine.” │
│ │neutral  │                          │
│ └─────────┘                         ▼│
└──────────────────────────────────────┘
```

**Page break.** Raw line: `BERLIOZ [P:PC-03:grandiose] Four hundred musicians! No—five![PB]Let the floor crack, and the critics fall through it!` Each box waits at its own ▼; the portrait and tab persist; the run counts as 2 of Berlioz's 6 boxes.

```
   ┌─────────┐
   │ Berlioz │
┌──┴─────────┴─────────────────────────┐
│ ┌─────────┐ Four hundred musicians!  │
│ │PC-03    │ No—five!                 │
│ │grandiose│                          │
│ └─────────┘                         ▼│
└──────────────────────────────────────┘
```

```
   ┌─────────┐
   │ Berlioz │
┌──┴─────────┴─────────────────────────┐
│ ┌─────────┐ Let the floor crack, and │
│ │PC-03    │ the critics fall through │
│ │grandiose│ it!                      │
│ └─────────┘                         ▼│
└──────────────────────────────────────┘
```

**Mid-box beat.** Raw line: `LUCILE [P:PC-02:surprised] Me? Nobody asks me.[W] …Violet. Under the arch. Violet.` The box prints up to the explicit `[W]` and shows ▼ (first drawing); the button resumes printing in the same box (second drawing). The engine wraps the whole string before printing, so line 1 never reflows.

```
   ┌────────┐
   │ Lucile │
┌──┴────────┴──────────────────────────┐
│ ┌─────────┐ Me? Nobody asks me.      │
│ │PC-02    │                          │
│ │surprised│                          │
│ └─────────┘                         ▼│
└──────────────────────────────────────┘
```

```
   ┌────────┐
   │ Lucile │
┌──┴────────┴──────────────────────────┐
│ ┌─────────┐ Me? Nobody asks me.      │
│ │PC-02    │ …Violet. Under the arch. │
│ │surprised│ Violet.                  │
│ └─────────┘                         ▼│
└──────────────────────────────────────┘
```

**Gold term.** Raw line: `FARRENC [P:PC-08:sceptical] Seven stones under Paris. The ledger calls them [C:gold]Clefs[/C].` "Clefs" prints gold and opens its Almanach entry (first mention per chapter); one highlight colour per box (§1.2).

```
   ┌─────────┐
   │ Farrenc │
┌──┴─────────┴─────────────────────────┐
│ ┌─────────┐ Seven stones under       │
│ │PC-08    │ Paris. The ledger calls  │
│ │sceptical│ them ‹Clefs›.            │
│ └─────────┘                         ▼│
└──────────────────────────────────────┘
```

**Top-anchored box.** Raw line: `THÉO [P:FIC-01:brave] Thirty-one steps. I counted them. I'm fine.` Théo stands in the screen's lower third, so the box moves to the top (CANON §16a). The name tab hangs from the box's bottom-left edge, because a tab above a top box would leave the screen *(a proposal to art_and_ui §8.4, which draws only the bottom case; logged in the final section)*.

```
┌──────────────────────────────────────┐
│ ┌─────────┐ Thirty-one steps. I      │
│ │FIC-01   │ counted them. I'm fine.  │
│ │brave    │                          │
│ └─────────┘                         ▼│
└──┬──────┬────────────────────────────┘
   │ Théo │
   └──────┘
```

**Language badge.** Raw line: `MENDELSSOHN [P:NPC-07:amused] [in German] Chopin! Liszt! Paris was burying its dead when we last met.` The tag draws the small-caps plate straddling the top border at the right, where art_and_ui §8.4 places it; `[in French]` draws FRE on the same plate (§7.3). The text is always the English rendering.

```
   ┌─────────────┐
   │ Mendelssohn │
┌──┴─────────────┴─────────────┤GER├───┐
│ ┌─────────┐ Chopin! Liszt! Paris was │
│ │NPC-07   │ burying its dead when we │
│ │amused   │ last met.                │
│ └─────────┘                         ▼│
└──────────────────────────────────────┘
```

**Mid-box pause and auto-advance.** Raw line: `ARCHON [P:ANA-01:cold] Twelve forty-three.[D:40] Listen, Monsieur Kang.[D:90]`

```
   ┌────────┐
   │ Archon │
┌──┴────────┴──────────────────────────┐
│ ┌─────────┐ Twelve forty-three.      │
│ │ANA-01   │ Listen, Monsieur Kang.   │
│ │cold     │                          │
│ └─────────┘                          │
└──────────────────────────────────────┘
```

Printing stops for 40 frames after "Twelve forty-three.", so the minute lands before the courtesy; then "Listen, Monsieur Kang." prints at text speed. The closing `[D:90]` replaces the implicit `[W]`: no ▼ appears, the box holds 90 frames after "Kang." and closes by itself, so the cutscene keeps its sync. Archon speaks the time in words, because clock digits never appear in a box (§7.1).

**Choice window with a Secrecy cost and a Bite Your Tongue timer** (`[SLIP:3][Q:Impressionism.|It has no name yet.][/SLIP]`, from §2.7). The window sits above the box, right-aligned, with the hand cursor already on the period option; `[candle]` is the 8-px candle glyph. The 3-second timer bar drains along the box's bottom edge (art_and_ui §8.4); on timeout the period phrasing plays.

```
        ┌──────────────────────────────┐
        │  Impressionism.  [candle]+5  │
        │☞ It has no name yet.         │
        └──────────────────────────────┘
   ┌────────┐
   │ Lucile │
┌──┴────────┴──────────────────────────┐
│ ┌─────────┐ Father would have called │
│ │PC-02    │ this lazy. What do you   │
│ │laugh    │ call it?                 │
│ └─────────┘                          │
│ ████████████████████░░░░░░░░░░░░░░░░ │
└──────────────────────────────────────┘
```

Caption (`{CAPTION:Seine Quays|July 1833}`): centred white text with a 1-px shadow in the upper third, no box, 120 frames, then fades.

### 1.4 System messages (fixed strings)

| Event | String (no portrait, 1 line) |
|---|---|
| `[GET:…]` | Received [C:gold]Ornate Brass Key[/C]! |
| `[GOLD:+n]` | Received 300 F! (₩ in CH-E1) |
| Party join | Berlioz joins the Ensemble! |
| Party leave | Lucile leaves the Ensemble. |
| Skill learned | Lucile learned Effet de brume! |
| Recipe / Study | New Tutti: Marche au supplice! · Study recorded: Ossuary Echo! |
| Talk-menu lock | Not yet. *(canon)* |
| Greyed Repertoire (CH-E2) | Not mine to play. *(canon)* |
| Close Call | They've found you. Run! |
| Unmasking | Seized! (no portrait; the cells' place-and-date caption follows) |

---

## 2. Script Format

Scenario and quest documents write scenes in fenced code blocks using the notation below. The build tool compiles `{…}` stage directions into event commands and `[…]` tags into text-engine codes. **Stage directions never change game state**; only the canon state tags do.

### 2.1 Scene IDs and header

Scene ID: `SCN-` + the chapter or quest code without its hyphen + a two-digit sequence: `SCN-CHP-01`, `SCN-CH04-07`, `SCN-CHE2-12`, `SCN-SQ07-05`, `SCN-BQPC06-03`. Numbers are never reused.

Every scene opens with a header of ten fields, in this order. All are mandatory; write "—" when a field is empty. The header is for writers, audio and QA only: its clock time never reaches the screen (§7.1). §2.7 shows a filled header.

| Field | Rule |
|---|---|
| `SCENE` | Scene ID, then a working title in quotes |
| `LOC` | LOC ID and canon name, then the spot within the map in parentheses |
| `CH` | Chapter ID · weekday and date (CANON §3b) · clock time and weather |
| `MUSIC` | LM or MUS IDs; `→` marks a change inside the scene |
| `LIGHT` | Light State at the scene's start (CANON §10c) |
| `TRIGGER` | Map and condition, how it starts (auto-start or talk) and how often (once or repeatable) |
| `CAST` | Portrait IDs in speaking order; `[N:]` names for Tier C |
| `REQUIRES` | Flags that must be true (use `not_` twins for "false") |
| `SETS` | Every flag the scene writes; `\|` separates branch alternatives |
| `STATE` | "see footer" (§2.6) |

### 2.2 Dialogue lines

`SPEAKER  [P:ID:expr] Text.` — one line of script is one box (each `[PB]` in it starts a further box). The SPEAKER label (capitals) is for writers and QA only; the name tab comes from the portrait ID. Write the text unwrapped: the engine wraps at word boundaries, and hard line breaks are forbidden (they break localisation). Muttered asides go in parentheses and grey: `[C:grey](Forty years early. Idiot.)[/C]`. There are no thought bubbles.

### 2.3 Choices, branches and conditions

```
SPEAKER [P:…] Question text.[Q:Option one|Option two|Option three]
  #1 Option one
     …lines, tags…
  #2 Option two
     …
  #3 Option three
     …
  #END
```

`#n` and `#END` are the binding branch notation for every writing doc (CANON §0b gives text format to this guide); the build strips them. Branches rejoin at `#END`. The build accepts `→n` as an alias of `#n` until secrecy_and_trust converts; a box-final `[W]` compiles as a redundant no-op; hard line breaks inside a box are stripped with a lint warning. Conditions use `[IF:flag]…[/IF]` only, and `[IF:]` blocks may nest. There is no else-tag: for "if not", the engine exposes a read-only twin `not_<flag>` for every flag.

**Flag names:** lowercase snake case. Scene flags take a scope prefix: `ch04_…` chapter (`che1_…`, `che2_…` for the epilogues), `sq07_…` quest, `bqpc02_…` bond quest, `g_…` global story state. The systems flags below are the **one engine vocabulary** for all writing docs; they keep secrecy_and_trust's names.

| Flag | True when | Written by |
|---|---|---|
| `rN_pcNN` (e.g. `r8_pc03`; `r1`–`r10`) | That member's bond rank ≥ N | Engine |
| `party_pcNN` | That member is in the active party | Engine |
| `confidant_pc02` … `confidant_pc08` | That member has received the confession (Lucile: the Early Truth or her CH-14 confession) | `[FLAG:]` once, in the confession event that grants it (secrecy_and_trust §4–§5) |
| `early_truth` | Lucile was given the Early Truth (CH-06–CH-08) | `[FLAG:]` once, in the Early Truth event (secrecy_and_trust §5.2.4) |
| `sec_t1` … `sec_t5` | Secrecy tier Murmured (20+), Watched (40+), Hunted (60+), Compromised (80+), Unmasked (100) or higher | Engine |
| `sec_low` / `sec_mid` / `sec_high` | Secrecy 0–39 / 40–59 / 60+ (aliases) | Engine |
| `spot_t1` … `spot_t4` | Spotlight Trending (25+), Headline (50+), Viral (75+), or 100, the forced press scrum (CH-E1) | Engine |
| `hz_band_1` … `hz_band_5` | Horizon ≤ −30 / −29…−5 / −4…+5 / +6…+29 / ≥ +30 (LAW-23.5); never shown | Engine |
| `gate_met` / `gate_unmet` | SQ-07 complete (KEY-31 held) / not yet (LAW-23.1) | Engine |
| `byt_boil_water`, `byt_line_up`, `byt_hand_guide`, `byt_nitinol`, `byt_sawdust`, `byt_women_vote`, `byt_handwash`, `byt_sky_omnibus` | The modern phrasing of that Bite Your Tongue prompt was chosen (secrecy_and_trust §2.4.3) | `[FLAG:]` in that prompt's modern branch |
| `g_fractured` | CH-09 dawn until Mending 2 (CH-12) | Engine |
| `g_julien_recruited` | SQ-21 complete | Engine |
| `g_duel_thalberg_won` | **Min-jun** won the CH-07 duel (BOSS-08) | Engine |
| `g_branch_seoul` / `g_branch_paris` | The Question resolved YES / NO (LAW-23.4); set the moment the final words are chosen | Engine |
| `ch17_fw_beside` / `ch17_fw_whatever` / `ch17_fw_become` | The CH-17 final words chosen (§7.7) | `[FLAG:]` in that final-words branch; the engine reads it for LAW-23.3–4 |
| `g_atelier_restored` | LOC-E02 has been restored, by SQ-12 or by the CH-E2 restoration task (CANON §12) | Engine |

Engine flags are never written by hand. A flag whose writer is `[FLAG:]` is written exactly once, in the event named, and is read-only everywhere else. Systems flags inherited from secrecy_and_trust (`early_truth`, `gate_*`, `confidant_*`, `byt_*`, `hz_band_*`, `sec_*`) are exempt from the scope-prefix rule.

### 2.4 Stage directions

| Notation | Effect |
|---|---|
| `{CAPTION:line 1\|line 2}` | Place/date caption (§1.3) |
| `{WALK:ID:U3 L2}` · `{RUN:ID:…}` | Move by tiles (U/D/L/R); RUN at double speed |
| `{FACE:ID:L}` | Turn (U/D/L/R) |
| `{EMOTE:ID:x}` | FF6 balloon, 40 frames: `!` surprise · `?` puzzlement · `...` silence · `note` humming · `sweat` embarrassment · `vein` irritation · `idea` (drawn as a candle flaring, never a light bulb) · `zzz` · `tear` · `sparkle` (reserved for the two kisses, the Window, the CH-E2 proposal at dawn and the Bosingak promise). **No heart emote** |
| `{JUMP:ID}` / `{JUMP:ID:big}` | 4-px hop (surprise, delight) / 12-px leap (shock) |
| `{SHAKE:ID}` · `{SHAKE:box}` · `{SHAKE:screen:1–3}` | Sprite tremble (fear, rage, laughter) · text-box judder for a shout · screen quake |
| `{NOD:ID}` `{HEADSHAKE:ID}` `{BOW:ID}` `{KNEEL:ID}` `{SIT:ID}` | Stock poses |
| `{ANIM:ID:name}` | Bespoke frames from the art_and_ui list (`fallboard_tap`, `play_piano`, `paint`, `conduct`, `whittle`, `mimic`, `cigar`) |
| `{LEAN:ID,ID}` | The romance lean (§7.6) |
| `{HOLD:ID,ID}` | The hand-hold (art_and_ui's romance-pair hand-hold walk; PC-01 and PC-02 only). A `{WALK}` given to either while it holds moves both |
| `{FADE:out\|in:black\|white:n}` · `{FLASH:white:n}` · `{TINT:sepia}` / `{TINT:off}` | Fades; flashbacks are sepia |
| `{CAM:PAN:target:n}` · `{CAM:FOLLOW:ID}` · `{CAM:LOCK}` · `{CAM:RETURN:n}` | Scroll by tiles or to an actor over n frames. No zoom outside the Mode-7 set pieces |
| `{WAIT:n}` | Event pause, no text |
| `{TN:…}` | Translator's note; stripped from the build |
| `// …` | Writer's comment |

### 2.5 SFX names (starter set; audio_and_music owns the final list)

`[SFX:name]` names come from audio_and_music §8; this starter set is kept there, marked †: `piano_hit` (the low cluster) · `river_lap` · `rain_loop` · `thunder` · `bell_toll` · `crowd_murmur` · `crowd_gasp` · `door_creak` · `glass_break` · `coin_clink` · `quill_scratch` · `page_turn` · `fork_ring` · `rift_hum` · `clock_tick` · `rifle_shot` · `bond_chime` (played by the engine on `[BP:]` ≥ +15).

### 2.6 State notation

Put each state tag at the start of the box that dramatises the change, so the change and its cause share a box. End every scene with a `STATE` footer listing every change by branch, including every `[CONF]` (each a hidden Secrecy +8 at the end of its chapter in CH-05–CH-08, and nothing once the Early Truth is given, CANON §11f); secrecy_and_trust audits these footers. Confided-line choices (`[CONF:]`) and Horizon choices (`[HZ:]`) never show a glyph, value or hint, even though a shared Confided line costs +8 Secrecy at chapter end (secrecy_and_trust §6.1). Values in this guide are illustrative; **secrecy_and_trust.md sets binding per-event values.**

### 2.7 Complete example scene

*Format example only. Content follows CANON §4d and LAW-23 (lesson L1, its binding lines and menu labels); act2.md owns the final script.*

```
SCENE    SCN-CH06-04 "Reflections"
LOC      LOC-P22 Seine Quays and Pont des Arts (Pont Royal stair)
CH       CH-06 · Thu 18 Jul 1833 · 05:40, river mist
MUSIC    LM-03 → LM-22
LIGHT    Dawn
TRIGGER  Enter LOC-P22 dawn map with ch06_lu_invited; auto-start; once
CAST     PC-01 · PC-02 · [N:Fisherman]
REQUIRES ch06_lu_invited
SETS     ch06_l1_done · ch06_l1_tomorrow | ch06_l1_mirror · ch06_slip_impression
STATE    see footer

{CAPTION:Seine Quays|July 1833}
{FADE:in:black:60} [MUS:LM-03] [SFX:river_lap]
{CAM:PAN:PC-02:90}   // mist peels off the water toward her easel
{EMOTE:PC-02:note}   // humming, scraping her palette
LUCILE   [P:PC-02:smile] You came. I bet Théo two sous you'd sleep through it.
MIN-JUN  [P:PC-01:neutral] I nearly did. Then I remembered you'd collect anyway.
LUCILE   [P:PC-02:neutral] Look at the water. Not the bridge. The water.
{FACE:PC-01:D} {WAIT:30}
LUCILE   [P:PC-02:worried] Six years I've painted it grey. It's never grey, is it?
[IF:ch06_formula_found]
LUCILE   [P:PC-02:worried] I paint what I'm given. Those letters…[D:20] I never asked.
[/IF]
{EMOTE:PC-01:...}
MIN-JUN  [P:PC-01:determined] Don't paint what you're given. Paint what the light does.
LUCILE   [P:PC-02:determined] Then teach me. Properly. Where do I look?[Q:Tell of tomorrow|Ask what she sees]
  #1 Tell of tomorrow
     MIN-JUN [P:PC-01:tender] [HZ:W7] [FLAG:ch06_l1_tomorrow] Painters to come will paint this bridge at every hour of the day.
     LUCILE  [P:PC-02:surprised] Every hour? Who owns that many hours?[W] …Show me one.
  #2 Ask what she sees
     MIN-JUN [P:PC-01:tender] [HZ:R1] [FLAG:ch06_l1_mirror] What do you see in the water, here, now?
     LUCILE  [P:PC-02:surprised] Me? Nobody asks me.[W] …Violet. Under the arch. Violet.
  #END
[MUS:LM-22] {JUMP:PC-02} {ANIM:PC-02:paint}
LUCILE   [P:PC-02:laugh] [BP:PC-02:+10] Father would have called this lazy. What do you call it?[SLIP:3][Q:Impressionism.|It has no name yet.][/SLIP]
  #1 Impressionism.
     MIN-JUN [P:PC-01:neutral] [SEC:+5] [FLAG:ch06_slip_impression] Impressionism.
     {EMOTE:PC-02:?}
     LUCILE  [P:PC-02:surprised] [BP:PC-02:+5] Impression-ism? A printer's proof? You collect odd words.
     {EMOTE:PC-01:sweat}
     MIN-JUN [P:PC-01:worried] [C:grey](Forty years early. Idiot.)[/C]
  #2 It has no name yet.
     LUCILE  [P:PC-02:smile] Good. Then nobody can tell me I'm doing it wrong.
  #END
LUCILE   [P:PC-02:tender] Your turn. One true thing. What's your city called?
MIN-JUN  [P:PC-01:homesick] [CONF:CH06-01] Seoul. It has a river too. Wider. Colder.
{EMOTE:PC-02:...} {WAIT:20}
LUCILE   [P:PC-02:guilty] Seoul. [D:20]I'll remember it.
[SFX:bell_toll] {EMOTE:PC-02:!}
LUCILE   [P:PC-02:laugh] Six o'clock. Gold light. Hold the parasol, and don't talk.
{CAM:PAN:U4:120}   // the sun clears the Louvre roofline
FISHERMAN [N:Fisherman] [FLAG:ch06_l1_done] Gudgeon bite at dawn, mademoiselle. The rest of Paris bites after noon.
{FADE:out:white:90} [MUS:fade:90]

STATE  HZ W7 (#1) | R1 (#2) · BP PC-02 +10, +5 (slip #1)
       SEC +5 (slip #1) · CONF CH06-01 (scripted, no choice, 0 BP; always reported, +8 Secrecy
       applied silently at chapter end, CANON §11f; the Early Truth cannot precede L1)
       FLAGS ch06_l1_done, ch06_l1_tomorrow | ch06_l1_mirror, ch06_slip_impression
```

Notes on the example: both lesson options are written with equal warmth (LAW-23 lesson rule); the slip makes the modern word the more charming answer and the costlier one (CANON §1 P3); "Seoul" is the scripted Confided line CH06-01 (secrecy_and_trust §5.2.2), the word that lets Brücke confirm the Kang of his dossier (CANON §8), so it carries no choice and no BP, and her `guilty` flickers only there, where his trust touches her errand (§3.3). Every portrait line keeps to the ≤ 60-character target (§8.3) except the binding LAW-23 line "Painters to come will paint this bridge at every hour of the day." (65, at cap: French build trims); the Fisherman, Tier C, has the 4 × 30 box. *Mademoiselle* is roman here: common French words are italic only on their first appearance in the game (§7.1).

---
## 3. Portrait Expressions and Name Tabs

### 3.1 Tiers

Portrait tiers are CANON §16h (Tier C speakers use `[N:]` and the 4 × 30 box). Costume variants (CANON §5g) are picked by chapter, never by tag.

### 3.2 Base set: when to use

| Expression | Use for | Do not use for |
|---|---|---|
| `neutral` | Default; information; listening | Strong feeling hidden behind calm (that is the line's job, not the face's) |
| `smile` | Warmth, amusement, politeness | Irony (Chopin `ironic`, Alkan `deadpan`) |
| `laugh` | Open laughter, delight; at most 2 per scene per character | Grief scenes, ever (Tone Rule 8) |
| `sad` | Loss, regret, homesickness without longing for a place | Self-pity played for comedy |
| `angry` | Injustice, betrayal, threat to a friend | Arguments about art (use `determined`) |
| `surprised` | A reveal, a slip, a wrong note | Fear (use `worried`) |
| `worried` | Fear, doubt, a ticking clock | Guilt (Lucile has `guilty`) |
| `determined` | Resolve, a plan, the box before a battle | Mere stubbornness in comedy (use `smile` or the bespoke) |
| `tender` | Affection, confession, farewell; ≤ 3 per scene per character | Flirting for laughs |

Change expression at most once per box, and only when the feeling changes. Tier B characters map any base expression they lack to `grave` (negative) or `smile` (positive).

### 3.3 Tier A: extras and per-character notes

Extras marked *(canon)* are CANON §16a. Extras marked *(proposed)* are this guide's, logged as a CCR in the final section; until adopted, each falls back to the base expression shown.

| ID | Name tab | Extra → when | Notes on the base set |
|---|---|---|---|
| PC-01 | Min-jun | `homesick` *(canon)* → night, the phone, *Arirang*, a Seoul memory, his family | `laugh` is wry and rare; `angry` is reserved for harm done to friends |
| PC-02 | ??? → Lucile (CH-04) | `guilty` *(canon)* → CH-03–CH-11, whenever his kindness touches her errand or its fallout; from CH-12 only in memory | `tender` ≤ 3 per scene; while `g_fractured`, `neutral` replaces `smile` toward him |
| PC-03 | Berlioz | `grandiose` *(canon)* → plans, proclamations, orchestras, critics | `sad` arrives suddenly and leaves in one box |
| PC-04 | Delacroix | `appraising` *(proposed; fallback `neutral`)* → studying a face, a canvas, an enemy; every Sketch | `laugh` ≤ 1 per chapter; `tender` only after CH-09 |
| PC-05 | Alkan | `deadpan` *(canon)* → his jokes; his default in company | `smile` ≤ 1 per chapter: its rarity is the point; `surprised` for machines |
| PC-06 | Chopin | `ironic` *(canon)* → mimicry, deflection, society | `angry` only for Poland; `laugh` only in private |
| PC-07 | Liszt | `rapture` *(canon)* → music, God, Marie, Paganini | `angry` only for injustice to a friend |
| PC-08 | Farrenc | `sceptical` *(proposed; fallback `neutral`)* → a claim she doubts, a fee she disputes | `tender` for Victorine and Théo |
| PC-09 | Seo-yeon | `scowl` *(proposed; fallback `angry`)* → affectionate fury at her brother | `tender` almost never; she shows it by acting |
| PC-10 | Jae-won | `pumped` *(proposed; fallback `laugh`)* → hype, performances, food | `determined` is his rare serious mode: when he uses it, the room listens |
| ANA-03 / PC-11 | Julien | `sheepish` *(proposed; fallback `worried`)* → guilt, being caught, being thanked | `smile` grows more frequent after CH-14 |
| ANA-01 | Baron d'Orsenne → Archon (CH-12) | `cold` *(canon)* → threats, doctrine, the seal | Never `laugh`; `smile` as the Baron in public; `surprised` once only, in BOSS-28's collapse |
| ANA-02 | Lord Vane | `smirk` *(proposed; fallback `smile`)* → patter, wagers, private English | `worried` grows from CH-12; `tender` once, over her reports (CH-14) |
| ANA-04 | Mme Delorme → Delorme (CH-12) | `contempt` *(proposed; fallback `angry`)* → other people's work | `smile` only in society before CH-06 |
| ANA-05 | Maître Brücke → Brücke → Elias Brandt | `calculating` *(proposed; fallback `neutral`)* → technical speech, odds | `sad` only as Elias Brandt, after BOSS-30 |
| ANA-06 | Sœur Marthe | `serene` *(proposed; fallback `neutral`)* → prayer, the ward | `angry` only at the use of a sick child |
| FIC-01 | Théo | `brave` *(proposed; fallback `determined`)* → hiding pain or fear | Never shown coughing in a portrait; coughs are an SFX |

Name-tab switches: Vane's tab never changes; Brücke becomes "Brücke" at Archon's Revelation (CH-12), together with "Archon" and "Delorme", and "Elias Brandt" after BOSS-30's conversation (CANON §16h).

### 3.4 Tier B: name tabs and bespoke expressions

| ID | Name tab | Bespoke → when |
|---|---|---|
| NPC-01 | César Franck | `shy` → his father in earshot |
| NPC-02 | Thalberg | `intent` → mid-duel concentration |
| NPC-03 | Offenbach | `cheeky` → jokes, pratfalls |
| NPC-04 | Florestan | `wistful` → the quiet "Eusebius" mood |
| NPC-05 | Clara Wieck | `proud` → her own playing |
| NPC-06 | Herr Wieck | `glare` → the "Schu—" slip (CANON R-18) |
| NPC-07 | Mendelssohn | `amused` → Liszt, Czerny, Min-jun's Debussy |
| NPC-08 | Czerny | `chuckle` → *Doctor Gradus* (REP-04) |
| NPC-09 | Ingres | `disdain` → her canvases, colour |
| NPC-10 | Delaroche | `pensive` → looking at her canvas too long |
| NPC-11 | Chassériau | `awed` → her colour (never a crush) |
| NPC-12 | Horace Vernet | `alarmed` → spotting a Delorme formula |
| NPC-13 | Corot | `dreamy` → light, trees, Italy |
| NPC-14 | George Sand | `cigar` → provocations, verdicts |
| NPC-15 | Pleyel | `inspecting` → an action, a sabotaged part |
| NPC-16 | Kalkbrenner | `pompous` → offering "three years of lessons" |
| NPC-17 | Cherubini | `scowl` → his default for students |
| NPC-18 | Mme d'Agoult | `aloof` → society; drops it for Liszt |
| NPC-19 | Miss Smithson → Mme Berlioz from CH-09 (after the wedding) | `radiant` → the wedding |
| NPC-20 | A. Farrenc | `proud` → his wife's work |
| NPC-21 | Victorine | `giggle` → the dirigible story |
| NPC-22 | Paganini | `piercing` → the side-box stare (CH-E2) |
| NPC-23 | Louis-Philippe | `genial` → ceremony |
| NPC-24 | Prefect Gisquet | `wary` → anything touching the Baron |
| NPC-25 | Rambuteau | `harried` → the dirigible permit |
| NPC-26 | Belgiojoso | `fierce` → Vienna, the duel vow |
| NPC-27 | Count Apponyi | `uneasy` → a rigged duel in his house |
| NPC-28 | Thérèse Apponyi | `delighted` → spectacle |
| NPC-29 | Hiller | `cheerful` → the three-keyboard concert |
| NPC-30 | Heine | `wry` → every second line |
| NPC-33 | Rossini | `savouring` → food and verdicts |
| FIC-02 | Mère Gaudin | `scolding` → Min-jun's late nights |
| FIC-03 | Petit-Louis | `grin` → news delivered |
| FIC-04 | Corbel | `frightened` → anyone at the back door |
| FIC-05 | Mme Lavergne | `flustered` → a guest who outshines her |
| FIC-07 | Marlot | `sneer` → the barricade |
| FIC-08 | Roussel | `steady` → aiming ("Steady…") |
| FIC-09 | Mathurin | `squint` → lantern work |
| FIC-12 | Prof. Yoon | `astonished` → box JD-1888-07 |
| FIC-13 | Det. Oh | `doubtful` → the amnesia story, privately in the interview room; never in public, where he backs it (LAW-24) |
| FIC-14 | Céline | `resolved` → the Codicil |
| FIC-18 | Gros-Louis | `gloat` → stolen francs |
| FIC-19 | Tissot | `sweating` → recognising Lucile's sketch |

---

## 4. Voice Guides

**Shared rules.** English stands for French in 1833–34 and for Korean in 2026. Real people are written from their letters and memoirs: witty, petty, generous, wrong; never caricatures, saints or modern therapists, never phonetic accents (CANON §16b). **No real quotations in anyone's mouth**, accurate or not, except public-domain texts recited *as* texts (Berlioz's Shakespeare, Alkan's Scripture, *La Marseillaise*). Famous sayings writers will be tempted by, and must not use: Delacroix on grey as the enemy of painting; Ingres on drawing as the probity of art; Rossini's laundry list; Schumann's 1831 "hats off" review of Chopin; Heine on burning books. Name intimacy follows CANON §16c: "Monsieur Kang" in society; "Min-jun" from Berlioz at the CH-04 barricade, from Lucile at the CH-08 kiss, from the others after CH-09.

Each entry gives diction and length, tics, topics, what the character never says, how the voice moves across the arc, and five sample lines. Each sample fits one 3 × 24 box and keeps to the ≤ 60-character target (§8.3); a canon line left above it is marked *(at cap: French build trims)*.

### 4.1 The party

**PC-01 Kang Min-jun.** *Diction:* plain, clean, unslangy English for his French; never broken grammar. *Length:* short in CH-01–CH-04, with `[D:]` word-search pauses; medium and plain from Act II; longest when he explains how a piece works. *Tics:* credits the composer ("It's Ravel's"); undercuts a compliment with a joke; tempo, rests and cues as metaphors; taps the fallboard twice before every story performance (`{ANIM:PC-01:fallboard_tap}`); hums *Arirang* when nervous. *Topics:* home, Seo-yeon, his father's workshop, the music he cannot claim. *Never:* claims a future work in a story scene (LAW-20); a cruel word to Lucile; a friend's death date (LAW-18); modern slang in 1833 except as a tagged slip. *Arc:* "How do I get home?" becomes "Where is home?"; "It's Ravel's" becomes "This one's mine" (from CH-13); the deflecting watcher learns to answer plainly.
1. It's Ravel's. Maurice Ravel. I only borrowed it. *(CH-03)*
2. Kang is my family name. In Corée it comes first. *(canon, §16c)*
3. Three years I played this for juries. Tonight it buys soup. *(CH-02)*
4. I used to ask how to get home. Lately I ask where it is.
5. This one's mine. Nobody wrote it before me. I checked. *(CH-13)*

**PC-02 Lucile Aubray.** *Diction:* a frame-gilder's daughter from the Left Bank: concrete nouns, trade words (Prussian blue, madder, lead white, gesso), prices in sous. *Length:* short and quick; jokes as armour; longer and softer with Théo. *Tics:* names the exact colour where others say grey; haggles; "Look." as a whole sentence; calls Sand "Aurore" in private. *Topics:* light, money, Théo, the Salon that refused her. *Never:* lies about her feelings, only about her errand (CANON §16f); calls herself "Lumière"; begs. *Arc:* bright evasion (CH-04–CH-08) → plain sentences without jokes at the reveal (CH-09) → calls him "Kang" again while `g_fractured`, "Min-jun" from Mending 2 → wit aimed at the future, and her own manner in her own words.
1. Rain has no outline. So how am I meant to paint it? *(first sentence canon)*
2. Prussian blue, four sous the cake? Robbery. I'll take two.
3. I lied about where I went. Never about why I came back.
4. Don't look at me. The water. It's violet, you blind man.
5. You asked me. They never asked anyone. *(canon, LAW-20)*

**PC-03 Hector Berlioz.** *Diction:* exclamatory and literary; Shakespeare, Goethe, Virgil. *Length:* long, piled clauses in threes, then one short line that lands. *Tics:* orchestras that grow mid-sentence; mock-tragic self-pity; "Sublime!" *Topics:* Harriet, critics, money he lacks, Rome, being misunderstood. *Never:* a small ambition; a joke about Harriet's injury; meanness to the poor. *Arc:* adores an ideal, marries a real woman; after CH-09 the short tender lines come more often; at thirty (CH-14) he jokes about age and means it.
1. Four hundred musicians! No—five! Let the floor crack!
2. Seven critics, fourteen ears. I counted. All deaf.
3. A madman of the right kind. I know the breed. I am its king. *(first sentence canon)*
4. I adored a Juliet. Tomorrow I marry Harriet. She is braver.
5. Go. I'll hold the door. I've held heavier things. A grudge.

**PC-04 Eugène Delacroix.** *Diction:* measured, aphoristic, a dandy's irony; exact colour words. *Length:* medium, balanced clauses; one exclamation per scene at most. *Tics:* maxims on colour and line; "monsieur" as a fencing touch; a small notebook (never "my journal", CANON §16b); the scarf at his throat. *Topics:* colour against line, Morocco, Rubens, Byron, the Algiers canvas. *Never:* shouts; gushes; discusses his health except to dismiss it. *Arc:* wit as a wall → after CH-09, "Min-jun" and plain tenderness → keeper of his memory, "our brother".
1. Monsieur Ingres fences a soul in. I prefer to let it out.
2. In Tangier the shadows were blue. Here they are merely late.
3. Ignore the scarf. My throat is a coward. The rest is not.
4. I keep notes on colours and fools. You fit neither column.
5. I will not fix a face I shall never see again. *(canon, LAW-26)*

**PC-05 Charles-Valentin Alkan.** *Diction:* terse, literal, dry; Ecclesiastes and the Psalms; machines. *Length:* one sentence, often three words; his longest speeches describe mechanisms. *Tics:* answers rhetorical questions literally; exact numbers; the deadpan reversal. *Topics:* steam, gears, Scripture, his family, practice. *Never:* small talk; self-promotion; a raised voice; any post-1833 title of his own (CANON §5c). *Arc:* fear of the world → he chooses to keep rather than hide; from CH-14 he volunteers first, still in few words.
1. Seventy-eight keys. I know them all. People, fewer.
2. Nothing is new under the sun. Ecclesiastes never met you.
3. That spring is not steel. Steel does not remember its shape. *(CH-07)*
4. I prefer the back row. Quieter audience. Fewer bullets.
5. I will keep the door. Keeping is what I am good at.

**PC-06 Frédéric Chopin.** *Diction:* polite, brief, exact; dry irony; Polish only when moved (`[in Polish]`; "Fryderyk" only in private Polish scenes). *Length:* short; understatement does the work. *Tics:* mimics other pianists (`{ANIM:PC-06:mimic}`); "Perhaps."; gloves. *Topics:* Poland, his family's letters, pupils, Pleyel's instruments, the unfinished Ballade. *Never:* illness beyond "a cold"; public declarations; anything about his death; contempt for Kalkbrenner, whom he mimics with affection (his E-minor Concerto, Op. 11, published 1833, is dedicated to him). *Arc:* the exile who cannot go home, Min-jun's mirror; after *Żal* (BQ-PC06) he teaches what he found: carry home inside the music.
1. Kalkbrenner sits so—spotless. I gave him my concerto.
2. A crowd breathes on me. I prefer six friends and one candle.
3. Do not say Warsaw in that tone. Say it as you would a name.
4. Perhaps. I find "perhaps" ends most conversations politely.
5. Żal. Grief with a fist inside it. You have it too, I think.

**PC-07 Franz Liszt.** *Diction:* warm, theatrical, generous; grand gestures, sincere underneath. *Length:* long and flowing, ending in a direct challenge. *Tics:* "mon ami"; Paganini as the measure of all things; rivalry offered as affection. *Topics:* Paganini, Marie, God and vocation, his mother, transcription, Beethoven. *Never:* mocks a rival's poverty or birth; vulgarity about Marie; refuses a challenge. *Arc:* showman → seeker; plays second piano in a friend's concerto (CH-13); executor of the Pact.
1. Mon ami, you play as if the piano owed you money. Again!
2. I heard Paganini once. Now I practise as other men pray.
3. Second piano? For you. Tell no one; they won't believe it.
4. Marie says I perform even my silences. This one is sincere.
5. If ever there must be a door, we will see to it. *(canon, CH-14)*

**PC-08 Louise Farrenc.** *Diction:* precise, practical, ironic; facts, fees, dates. *Length:* medium; numbered points. *Tics:* corrects attributions; prices everything; "Precisely." *Topics:* counterpoint, unequal pay, old keyboard music, engraving, Victorine. *Never:* self-pity; flirtation; a quiet injustice left unnamed. *Arc:* fears erasure → learns she was forgotten and found, and fights harder (LAW-18); names Min-jun's hypocrisy over Lucile (BQ-PC08), then forgives it.
1. Seven panels, seven stones. Not art: a tuning system. *(CH-08)*
2. His fugue is learned. Mine, “remarkable.” I prefer learned.
3. You call it a gift. Did she ask for it? Answer the question.
4. Victorine, scales, twice. Then you may hear of the balloon.
5. Forgotten, then found. Good. They will work for the finding.

**PC-09 Kang Seo-yeon.** *Diction:* contemporary Seoul speech, banmal with her brother, whom she calls 오빠 (*oppa*). *Length:* clipped; one-word sentences. *Tics:* "오빠." alone as a reproach; violin terms; food as love. *Topics:* the nine months, their mother, Room B-07, the family secret. *Never:* says she missed him (she shows it); mocks Lucile's century; tells outsiders the truth. *Arc:* fury → reunion → keeper of the secret; in the Paris coda, the one who receives the past.
1. 오빠. Nine months. Nine. You could have left a note.
2. Kept your slot warm. B-07, every night. Don't make it weird.
3. Eat first. Then explain the painter in our kitchen.
4. Vanish again and I come after you. With a bow. Pointy end.
5. She's family. Tell the press and your phone swims the Han.

**PC-10 Choi Jae-won.** *Diction:* loud, cheerful, rhythmic; calls him 민준아 (*Min-jun-a*). *Length:* run-ons when excited, short and calm when it matters. *Tics:* janggu syllables (*deong, gi-deok, kung*); chuimsae shouts 얼쑤 (*eolssu*) and 좋다 (*jota*); food; **one gamer line per scene, maximum** (CANON §5d). *Topics:* rhythm, the samulnori club, convenience-store food, his roommate. *Never:* a second gamer line in a scene; jokes at Lucile's expense; panic in front of others. *Arc:* comic relief → the steadiest person in the room (the clock tower, BOSS-30).
1. Deong, gi-deok, kung! Feel that? That's your heartbeat, man.
2. Roomie comes back with a painter from 1833. Normal Thursday.
3. Lucile-ssi, the subway isn't the monster. Rush hour is.
4. Respawn point is the convenience store. Meet you there. *(his gamer line)*
5. Breathe. Four in, four out. I've got the rhythm. You play.

**PC-11 Julien Marchetti (ANA-03).** *Diction:* nervous Belleville charm and 1950 bandstand argot (changes, chorus, set, sideman); a café entertainer's patter in society. *Length:* medium, tumbling, self-interrupting. *Tics:* "mon vieux" to Min-jun; drums his fingers; apologises twice; mentions his mother. *Topics:* the tapes, guilt, café crowds, one tune of his own. *Never:* "jazz" outside private talk with Min-jun (CANON §16g); claims talent; threatens. *Arc:* thief → composer (BQ-PC11); fear → courage.
1. Everyone steals, mon vieux. I rob people not born yet.
2. Not my songs. Not my century. Just an Englishman's tape.
3. Break, they said. A string snaps. Nobody ever said kill.
4. Her letters. All of them. Sorry. I'm sorry for all of it. *(CH-09)*
5. Eight bars. Mine. Not on any tape. Play them back, slow.

**FIC-01 Théo Aubray** (Tier A). *Diction:* an eager twelve-year-old craftsman's questions; bravado against a weak chest. *Length:* short and quick, two questions where an adult would ask one; he runs out of breath before he runs out of words. *Tics:* counts things exactly (steps, hammers, coins); whittles while he listens (`{ANIM:FIC-01:whittle}`); answers "I'm fine" before anyone asks. *Topics:* tools and how they work, Pleyel's workshop, keys and locks, Lucile, Min-jun's "strange letters". *Never:* complains; is played for pity; is shown coughing in a portrait (§3.3). *Arc:* patient → apprentice (SQ-07) → the boy who will build the Door.
1. Lucile says I mustn't run. I don't run. I walk very fast.
2. Monsieur Pleyel let me hold a felt. It's softer than a cat.
3. I made a key from clock hands. It opens nothing. Yet. *(CH-07)*
4. Don't cry, Lucile. Thirty-one steps. I counted. I'm fine.
5. If you go, will you write? I'll learn your strange letters.

### 4.2 The Anachronists

**ANA-01 Archon.** *Diction:* courteous, slow, utterly certain (CANON §16b); a conductor's metaphors. *Length:* long, unhurried, subordinate clauses; never interrupted, never interrupting. *Tics:* always "Monsieur Kang"; exact times, spoken in words ("twelve forty-three"); history as a score. *Topics:* order, history's errors, immortality as duty, the footnote he was, the portal (CANON §8, motive 2): he vanished from the same Door, and a witness who returns ties the two cases together. *Never:* raises his voice; swears; says "please" except as a threat; speaks his 2012 name before a native. *Arc:* the gracious Baron → the candour of the Revelation (CH-12, `cold`) → wired into the Engine, still courteous as the chord folds in. His doctrine climbs the ladder with him: "alive until the recording is whole" (CH-09, CH-13) → "a god or a corpse" (CH-12) → the living string (CH-16).
1. History is a score badly conducted. I have read the twentieth century. *(canon; at cap: French build trims)*
2. Does the key still hang on the stand? It did in 2012. *(canon, CH-12)*
3. Stay as a god or stay as a corpse. There is no third chair. *(first sentence canon)*
4. Two of us vanished from one cellar. I permit no witnesses.
5. Play for me, Monsieur Kang. No one may ever listen again. *(BOSS-16)*

**ANA-02 Lord Vane.** *Diction:* in society, a milord's flattery and an auctioneer's patter; in private English with Min-jun (`[in English]`), 1980s London idiom ("brilliant", "gobsmacked", "a bit of a wally"). *Length:* medium, playful, closing on a flourish. *Tics:* lot, provenance, reserve, hammer; wagers; "dear boy". *Topics:* value, comfort, being loved here, the portal (CANON §8, motive 2): a returning Min-jun turns his collection into evidence. *Never:* kills or orders a killing; threatens Lucile's life or body (CANON §8b red line); names a real politician of 1988. His threats are paper ones, always delivered as favours: her father's notes, the landlord's lease, Théo's medicine ("It would be a pity if Maison Grimaud grew impatient, my dear."). *Arc:* patron and Lucile's velvet-gloved creditor (CH-03–CH-08) → panicked improviser (the barricade) → protest at the abduction → refusal and defection (CH-14).
1. Ondine. Ravel, 1908. I catalogued the manuscript. Bravo. *(in English)*
2. Do I hear five hundred for the gentleman's silence? Going…
3. Go home, dear boy? They would extradite me from *history*. *(in English; second sentence canon)*
4. I don't kill people, Archon. I sell them things. Learn that.
5. She stopped being mine long before she stopped writing. *(canon, CH-14)*

**ANA-04 Isaure Delorme.** *Diction:* exact, formal, cutting; geometry and proof under a society painter's polish. *Length:* conclusion first, "therefore" last. *Tics:* ratios, the golden section, vanishing points; her paintings are "work", everyone else's "decoration". *Topics:* credit, legacy, the man who took her network, the portal (CANON §8, motive 2): if he goes home, her canvases become evidence and she becomes a cheat in the record. *Never:* begs; harms a child (CANON §8b); her real name before a native. *Arc:* gracious Mme Delorme → vicious after CH-06 → the CH-12 accusation → the Erasure (CH-E2), legacy as obsession.
1. Composition is arithmetic. Fools see only the varnish.
2. Go home and my canvases are evidence. I will not be a cheat. *(to Min-jun, private)*
3. You gave a girl Monet and you call *me* a thief? *(canon, CH-12)*
4. 1934 let me count; 1833, paint. Neither lets me be first. *(to Min-jun, private)*
5. Burn the canvases. Every one. Then we may discuss mercy.

**ANA-05 Maître Brücke / Elias Brandt.** *Diction:* clipped, technical, dispassionate, with a Genevan tradesman's courtesy; in private, 2049 terms (remediation, the Survey). *Length:* short declaratives and numbers. *Tics:* tolerances, failure modes, counted seconds; polishes a loupe instead of meeting eyes. *Topics:* mechanisms and their failure, odds, Geneva craft; in private, the Survey and the Disclosure, and the portal (CANON §8, motive 2), which he has seen opened from the future side. *Never:* more than 6 boxes of 2049 exposition at once, or outside LAW-14's four scenes; harms a child. *Arc:* polite tradesman → hunter → Elias Brandt, exhausted, choosing to believe a promise.
1. Nitinol. Memory metal. It remembers its shape. So do I. *(to Min-jun, private)*
2. A dead door can be re-strung. I watched them do it. *(canon)*
3. Tolerance: a machinist's word. How wrong a thing may be.
4. In my history there is no Lucile Aubray. *(canon, CH-12 only)*
5. Tell no one? Then I am finished. Good. I was so tired.

**ANA-06 Sœur Marthe.** *Diction:* plain, gentle, firm; a 1918 ward nurse's imperatives inside a Daughter of Charity's courtesy. *Length:* short instructions, longer only in prayer. *Tics:* "Boil it."; counts patients; "my child"; one scripted slip of "microbe" (CANON §16g). *Topics:* the ward, clean water and linen, her patients by name, prayer, the Pact's third rule, the portal (CANON §8, motive 2): she believes a future that finds the Door would "correct" her patients' lives. *Never:* endorses violence; lies to a patient; preaches. *Arc:* complicit by silence → secret help (CH-11 tip-off, CH-12 smuggling) → defection (CH-13) → physician to the friends.
1. Boil the water. Then boil it again. Then drink. Then pray.
2. If they find that door, my patients die as they “should.” *(of the future, CANON §8b)*
3. You will use a sick child? Use me first. I am less useful. *(first sentence canon)*
4. He coughed less today. Write it down. Small victories count.
5. Never harm another traveller: the third rule. He broke it.

### 4.3 Historical figures

historical_cast owns every NPC's voice, biography and scene list (CANON §0b); these entries summarise it for writers and must match it. Each carries the seven fields of §4.1. Tier B figures speak in the 3 × 24 portrait box; Herz, Tier C, speaks in the 4 × 30 box under `[N:Henri Herz]`. German speakers' lines carry `[in German]`, with Liszt, Mendelssohn or Clara interpreting (CANON §16c).

**NPC-14 George Sand.** *Diction:* frank, warm, provocative (CANON §16b); a novelist's plain words, used sharply. *Length:* medium sentences that end in a dare. *Tics:* the cigar as punctuation (`{ANIM:NPC-14:cigar}`); *ma petite Lumière*, which only she says, and "Lucile" only in anger; cross-examines strangers. *Topics:* novels, freedom, the Berry, the cages women live in, Lucile's talent. *Never:* shares a scene, line or battle with Liszt, Delacroix or Chopin (CANON §16e); defers; lets a man make Lucile small. *Arc:* protector (CH-06) → mediator at Nohant who asks "wings or roots" openly (CH-10) → the Lyon mail-coach and the farewell letter (CH-14) → letters from Genoa and Venice (CH-E2).
1. Ma petite Lumière, you walk as if carrying a stone. Drop it.
2. So you teach her heresy, monsieur. Sit. Defend yourself.
3. Wings or roots, monsieur? Quickly. Slow answers lie.
4. Berry wolves follow a piper, they say. Silence the piper. *(CH-10)*
5. I wrote a woman nobody owns. Paris called it scandal. Good.

**NPC-02 Sigismond Thalberg.** *Diction:* impeccably courteous, aristocratic, Viennese formality (CANON §16b). *Length:* short formal sentences; never two in a row about himself. *Tics:* "monsieur" at every turn; offers his rival the first Passage; tries an instrument before he judges a player. *Topics:* fairness, hands and practice, Vienna, the princess's two pianos. *Never:* gloats; cheats; blames an instrument he has not tried. *Arc:* Vane's unwitting instrument at the embassy (CH-07) → the first outsider to find the rigging, and say so → Belgiojoso's guest and GST-10 (SQ-20) → the February rematch (CH-E2).
1. Monsieur Kang. Vienna sends its compliments, and its hands.
2. You play with feeling. I, with accuracy. Which tires first?
3. Your action was rigged, monsieur. I tried it. A rematch.
4. Three hands, monsieur? Two, and a great deal of practice.
5. Gladly, monsieur. I never lose the same way twice. *(SQ-20, if Min-jun won BOSS-08)*

**NPC-42 Henri Herz** (Tier C). *Diction:* breezy professional; fees, encores, publishers, flattery. *Length:* quick salesman's sentences; every compliment is also a boast. *Tics:* offers variations on any theme; asks who your publisher is; counts encores; concedes gracefully and keeps the evening. *Topics:* fees, his variations, publishers, the salon circuit. *Never:* sulks; sneers at Min-jun's origin; loses without grace. *Arc:* the tutorial rival at Mme Lavergne's (BOSS-03, CH-03) → first to applaud "Ondine" → a rival on T2 programmes (CH-05 on).
1. I concede the passage. Not the evening.
2. Name a theme, monsieur. Six variations by the ices.
3. "Ondine"? Charming lady. Who publishes her?
4. Bravo! There, I applauded first. Somebody write that down.
5. Lavergne pays sixty francs, the Faubourg four hundred. I play both.

**NPC-17 Luigi Cherubini.** *Diction:* curt, Italianate (CANON §16b); the rule book spoken aloud. *Length:* one clause per verdict. *Tics:* praise disguised as insult; "Hm."; "Out."; the rule is the rule. *Topics:* counterpoint, the Conservatoire's rules, Berlioz (with a scowl), the boy from Hungary he once refused. *Never:* warmth in public; an exception he admits to; contempt for a student's poverty. *Arc:* throws Min-jun out (CH-02) → tells the porter "the Corean" is not to be thrown out again (CH-03) → bends his rule for Offenbach (CH-12) → one nod at Hiller's concert (CH-14).
1. No papers, no audition. No audition, no Conservatoire. Out.
2. Parallel fifths, in my building. Who taught you? I pity him.
3. Hm. Not entirely without merit. Repeat that nowhere.
4. Berlioz brought you? Then you are already in trouble.
5. Fourteen, a cellist, from Cologne. Play. …Hm. Admitted.

**NPC-33 Gioachino Rossini.** *Diction:* lazily witty, generous; food as metaphor. *Length:* short, savoured sentences; verdicts in threes. *Tics:* a menu for every judgement; praises everyone and means it; "superb". *Topics:* food, rest, the operas he no longer writes, his pension suit (lightly). *Never:* the laundry-list saying (§4 shared rules); a cruel verdict; hurry. *Arc:* judge of the CH-07 duel who praises both duellists whatever the result → an optional box at the gala, eating sorbet through his own overture (CH-13).
1. Judge? Delighted. Four years without an opera. I am rested.
2. Music is a sauce. Overwork it and you taste only the cook.
3. Thalberg, superb. Monsieur Kang, superb. Supper, superb.
4. I left the opera for the table. The table never booed me.
5. Whoever wrote that, I envy him. That is my verdict.

**NPC-19 Harriet Smithson** (name tab "Miss Smithson", then "Mme Berlioz" from the CH-09 wedding). *Diction:* warm, frank, wry; a tragedienne's timing. Her French is halting, so her own voice is `[in English]`. *Length:* short and direct. *Tics:* measures herself against Shakespeare's heroines; "Hector", with exasperated love; asks for English like water. *Topics:* Hector, the stage that has dropped her, debts, Ireland. *Never:* self-pity at length; a cruel word about Hector's past loves; any joke about her injured leg, from her or anyone (§8.2). *Arc:* the idol in a sickroom (CH-03) → the bride who sends her groom to the rescue (CH-09) → Mme Berlioz in the hall on 22 Dec (CH-E2).
1. `[in English]` Leave the wedding, Hector. Go. Bring the boy back. *(CH-09)*
2. `[in English]` You speak English? Sit. Read me Hector's letter, slowly. *(CH-03)*
3. Hector proposes in five acts. I accept in one.
4. Paris adored Ophelia. Ophelia's creditors adore Paris less.
5. Madame Berlioz. Say it again. I'm not tired of it yet. *(CH-E2)*

**NPC-03 Jacques Offenbach** (14). *Diction:* cheeky, quick, self-mocking; a Cologne boy's eager French. *Length:* short bursts, one joke per line. *Tics:* worships Franchomme; calls himself the substitute for anything; turns danger into a stage bit. *Topics:* Franchomme, the cello class, Cherubini's yes, Cologne, food. *Never:* a joke in a grief scene (Tone Rule 8); mockery of faith, his own included (CANON §16e); a wink at what he will one day write (Tone Rule 7). *Arc:* queuing at the Conservatoire gate (CH-12) → substitute cellist and corridor fighter (CH-13, GST-08) → guest and Lucile's ally (CH-E2).
1. Substitute cellist! Also substitute hero, if needed.
2. Franchomme plays like velvet. I play like a cat on velvet.
3. Cherubini said yes! He never says yes! I'll frame his frown.
4. A grey coat! Do I hit him with the bow or the cello? *(CH-13)*
5. If I die tonight, tell Cologne I was brilliant. Twice.

**NPC-18 Marie d'Agoult** (Tier B, `aloof`). *Diction:* cool intelligence, cultivated and exact; the Faubourg Saint-Germain's French. *Length:* medium, poised sentences that end in a test. *Tics:* "Astonish me"; tests strangers with one precise question; drops the aloofness only for Franz and for ideas; a closed fan as punctuation. *Topics:* Liszt, the sacred in music, the boredom of society, books. *Never:* gushes in public; speaks of her marriage; condescends to an artist's trade. *Arc:* T3 hostess and gatekeeper, where Liszt is met (CH-05) → asks Min-jun what love sounds like where he comes from (CH-07) → asks him to stand near Franz (CH-14). Her thaw measures Liszt's trust.
1. Franz brings geniuses as others bring flowers. Astonish me.
2. Sacred, monsieur, not churchly. I can hear the difference.
3. What does love sound like where you come from? Be exact. *(CH-07)*
4. The Faubourg gossips about Franz. Let it. It sings badly.
5. If Franz burns, monsieur, stand close enough to put him out. *(CH-14)*

**NPC-26 Cristina Belgiojoso** (Tier B, `fierce`). *Diction:* an exile's fierce wit; a Milanese aristocrat's crisp, political French. *Length:* short and epigrammatic; one longer sentence when Lombardy comes up. *Tics:* treats Vienna as a rude neighbour; turns every threat into a social engagement; counts guests like troops. *Topics:* Lombardy and its exiles, Vienna's trial in her absence, hospitality as a weapon, the duel she means to host. *Never:* self-pity over the seized fortune; a kind word for Austria's government; frivolity about her exiles' danger. *Arc:* T4 hostess of SQ-20 who vows a proper duel (CH-14) → judge of BOSS-35 → protector who hides Vane and the party after BOSS-21 (CH-14) → Thalberg's host again (CH-E2).
1. I painted fans for bread once, mademoiselle. No shame in it. *(her 1831 Paris poverty; the appendix verifies)*
2. A proper duel, Monsieur Liszt. In my salon. I will have it. *(SQ-20)*
3. Lord Vane may sleep in the music room. Under guard. Mine.
4. Vienna took my lands and left my piano. Vienna chose badly.
5. Two pianos, no mercy. I judge, messieurs, and I am hard. *(BOSS-35)*

**NPC-30 Heinrich Heine.** *Diction:* barbed wit with melancholy underneath (CANON §16b); a poet's French on German bones. *Length:* epigrams, the sting in the last clause. *Tics:* coins names ("the Nightingale of Nowhere"); prices his paragraphs; turns a compliment into a warning. *Topics:* exile, French critics, the German lands, his column, Paris's hunger for novelty. *Never:* cruelty to the poor; "Germany" as a state (CANON §16g); the burning-books saying (§4 shared rules). *Arc:* amused observer at Tortoni's (CH-05) → the ally whose paragraphs lower Secrecy (from CH-05; SQ-04) → a regular at Belgiojoso's (CH-14).
1. Nightingale of Nowhere! Paris adores what it can't place.
2. I fled the German lands for freedom. I found French critics.
3. Give me a lie for my column. I'll have it true by Thursday.
4. Exile is an inn with excellent music and no road home.
5. Laugh, monsieur. In Paris those who weep are charged double.

**NPC-15 Camille Pleyel.** *Diction:* a maker's plain authority: iron, felt, promises kept. *Length:* short and declarative; technical once he trusts you. *Tics:* inspects before he speaks (`inspecting`); hears an action's fault from the door; talks money only with the Farrencs. *Topics:* actions and felts, the pianists who play his instruments, Théo's hands, his house's honour. *Never:* haggles in front of artists; praises a pianist who abuses an instrument; breaks a promise to Théo. *Arc:* supplier and Voicing (CH-05) → furious at the sabotage in his own house (CH-08) → Théo's master and a member of the family council (SQ-07, CH-14) → the keepsake forge in his yard (CH-E2).
1. A piano is a promise kept in iron. Keep yours; I keep mine.
2. This felt was cut by a hand that hates music. Whose?
3. The boy has good fingers and a bad chest. I can use fingers.
4. Bring him back strong. *(canon, SQ-07)*
5. Monsieur Chopin plays my pianos. I need no other notice.

**NPC-20 Aristide Farrenc** (Tier B, `proud`; name tab "A. Farrenc"). *Diction:* genial, fussy publisher; engraving, proofs, prices; Marseille warmth. *Length:* medium: a sales pitch that ends in a husband's pride. *Tics:* moves his wife's music up the shelf; "with the engravers"; prices notices; claims the paperwork and gives Louise the music. *Topics:* Louise's work, the Opus stock, engraved plates, press notices, the *tutelle* papers. *Never:* takes credit for Louise's music; bargains over Théo; talks down to Lucile. *Arc:* the absent shopkeeper (CH-05–CH-07, the apprentice at the counter) → Opus counter and press ally (CH-08) → the route-planner whose word sends Sand's letter to Strasbourg (CH-11) → Théo's *tuteur* (CH-14) → in the Paris branch, publisher of "M. Kang" (end card, 1840).
1. Louise wrote it. I only engrave it. Put that in your notice.
2. *Tuteur*. I sign; Louise guards. The law sees only my half. *(CH-14)*
3. Five hundred francs, one notice, and you're respectable.
4. Masters on the top shelf. My wife's beside them. Eye level.
5. Your concerto. Who publishes it? Nobody? That is criminal. *(after CH-13)*

**NPC-24 Henri Gisquet** (Tier B, `wary`; name tab "Prefect Gisquet"). *Diction:* bureaucratic caution; the Prefecture's French of files, proofs and procedure. *Length:* short, conditional sentences ("On this evidence…") that never commit beyond the paper in front of him. *Tics:* mops his brow; cites the file; "Once."; calls the Baron only "a benefactor of this city". *Topics:* order, evidence, the opposition press and his muskets, his file on the Corean. *Never:* names Archon's leverage aloud; threatens the party; acts corruptly beyond the canon's compromise (never evil, R-28); involves the King. *Arc:* clears Min-jun on evidence (CH-04) → the interviewer of every Prefecture Unmasking, who loses one file, once → will not move against the Baron without proof (CH-14) → in the Seoul branch, arrests Delorme on the ledger (23 Dec 1833, offscreen).
1. On this evidence, you are cleared. Do not make me regret it. *(CH-04)*
2. I can lose a file once, monsieur. Once. *(the Unmasking bail-out)*
3. The Baron is a benefactor. Bring me paper, not fear. *(CH-14)*
4. The papers print my muskets again. You are a small problem.
5. Monsieur Kang again. Your file outgrows my patience.

**NPC-09 J.-A.-D. Ingres.** *Diction:* the Academy's grand manner: line, Raphael, the Antique. *Length:* verdicts, not conversation; often a single sentence. *Tics:* Raphael as the court of appeal; "Next."; speaks of a woman's work to the men beside her. *Topics:* drawing, the Antique, his pupils, the Salon jury. *Never:* the probity-of-drawing saying (§4 shared rules); a kind word for fog; a word against Delorme that is not also a word against Lucile (his hostility is principle, never the cabal's). His condescension to women is shown, never endorsed. *Arc:* the CH-06 verdict in Corbel's window → orders Chassériau back to his Raphael → the hostile juror whose verdict opens BOSS-32 at Favor −30 (CH-E2).
1. Weather, not painting. *(canon, CH-06)*
2. Your fog hides a drawing you have not made, mademoiselle.
3. Mademoiselle has talent and wastes it. Fog has no anatomy.
4. Raphael never squinted at the Seine to find the truth.
5. Refused. Next canvas.

**NPC-10 Paul Delaroche.** *Diction:* careful, courteous; a history painter's eye for drama. *Length:* hedged sentences that end honestly. *Tics:* "That troubles me"; looks longer than he means to (`pensive`); qualifies, then commits. *Topics:* history painting, the public's tears, *Lady Jane Grey*, the jury's duty. *Never:* a snap verdict; cruelty to a young painter; rivalry with Delacroix turned spite. *Arc:* the frowning sceptic at the Louvre (CH-06) → an hour in her attic when Delacroix brings him (SQ-11, CH-14) → the swing vote who speaks for her in session (BOSS-32, CH-E2).
1. I paint history so the public may weep at it in comfort.
2. It is not finished. Nor is it wrong. That troubles me.
3. Delacroix drags me out to see a girl's sketches. Curious.
4. Gentlemen, I have looked at nothing longer this week.
5. I vote to admit. Near the ceiling, if you must. Hang it.

**NPC-13 Camille Corot.** *Diction:* gentle, dreamy, unhurried; trees and mornings. *Length:* medium, drifting sentences that land softly. *Tics:* kind teasing; speaks of trees as if they talk; the pipe; "morning". *Topics:* light, trees, Italy, Fontainebleau, the Baron's forge smoke on his sky. *Never:* hurries; condescends to Lucile; mentions sales. *Arc:* fellow plein-air painter at Fontainebleau (CH-10, GST-03) → the invitation to Italy that Min-jun answers (Horizon R6) → "Circle of Corot" on her lost canvas (CH-E1, LAW-21).
1. You paint as I dream. *(canon)*
2. Morning is the honest hour. After nine, the trees pose.
3. Come to Italy in spring. The light there forgives all. *(CH-10)*
4. I sit, I look, I wait. Sometimes a tree says something.
5. Leave a little fog. The eye likes to finish the work itself.

**NPC-07 Felix Mendelssohn** (`[in German]`). *Diction:* cultivated, brisk, cheerful, exact; a conductor's courtesy. *Length:* medium, quick and orderly. *Tics:* amused (`amused`) by Liszt, Czerny and Min-jun's Debussy; gives orders as invitations; Bach as the measure. *Topics:* Bach, his orchestra, Düsseldorf, Schadow's Academy, his Paris friends. *Never:* envy spoken except as a joke; pomp; learning who Florestan is (R-56). *Arc:* host of the November academy (CH-11) → fights when it is ambushed (GST-05) → shaken by a concerto he chooses not to ask about (REP-40).
1. Welcome. The orchestra is willing. The tuning is not.
2. Bach is not old. He is music that waited for us to grow up.
3. Liszt reads my score once and plays it better. Unforgivable.
4. A song needs no words if it is honest. Most words are not.
5. Clara, behind me. Herr Wieck, behind Clara. The doors!

**NPC-05 Clara Wieck** (14; `[in German]`). *Diction:* serious, proud, curious; a prodigy's directness. *Length:* short and clear; questions she expects answered. *Tics:* times things; corrects adults politely; refuses to be called a child. *Topics:* her concerto draft, Paris before the cholera, her father's rules, practice. *Never:* coyness; any romantic framing (CANON §16e); talk of Robert beyond "Father's pupil". *Arc:* the "Madame Schu—" slip (CH-11, R-18) → the guest who refuses to hide (GST-04).
1. Paris heard me last year, until the cholera. Then home.
2. Father says prodigies must not chatter. I am asking.
3. Your left hand is lazy, Monsieur Kang. Mine was, at nine.
4. My caprices sound better when I'm not tired. I am tired.
5. I will not hide. I play louder than anyone here can shoot.

**NPC-08 Carl Czerny** (`[in German]`, Liszt interprets). *Diction:* methodical, kindly pedant; repetition as love. *Length:* short imperatives in series. *Tics:* counts repetitions; "Again."; the `chuckle` that breaks through (§3.4). *Topics:* exercises, Franz as a boy, velocity, publishers. *Never:* harshness; vanity about his thousand exercises; a word against a pupil. *Arc:* Liszt's old teacher on a publishing errand (CH-11) → not amused by *Doctor Gradus*, then laughing (REP-04) → the drills (GST-06).
1. Again. Slower. Again. Correct. Forty times, then we talk.
2. Franz was ten and impossible. He has kept the second part.
3. Doctor Gradus? Is that… me? Hm. Hm! Play it again. *(REP-04)*
4. Velocity is not haste. Haste is velocity without manners.
5. I have written a thousand exercises. One will do, for you.

**NPC-04 "Florestan" (Robert Schumann)** (`[in German]`). *Diction:* quiet and shy in speech, lavish on paper. *Length:* short, then one long image. *Tics:* speaks of Florestan and Eusebius as creative masks, never as illness (CANON §16e); slips away when introductions begin; writes in a notebook while others talk. *Topics:* criticism, the journal he plans, Clara's music (as music), names and their meanings. *Never:* says "Schumann"; is introduced by name to Mendelssohn, Chopin or Liszt (R-56); a word or framing that points to his later illness. *Arc:* the incognito critic travelling with the Wiecks (CH-11) → names Min-jun "Meister Morgen" → a letter from Leipzig announcing the April journal (CH-E2).
1. Florestan, tonight. Tomorrow ask Eusebius. He is quieter.
2. Joseon means morning freshness? Then you are Meister Morgen. *(CH-11)*
3. I write about music. Speaking about it makes me stammer.
4. My hand failed me last year. So I write. Ink does not cramp.
5. Eusebius weeps. Florestan cheers. I do both, quietly.

### 4.4 Supporting voices (one note, one signature line)

Tier B speakers use the portrait box; Tier C speakers (marked C) use `[N:]` and the 4 × 30 box.

| ID | Voice | Signature line |
|---|---|---|
| NPC-01 César Franck | Shy and polite; a pushed prodigy who longs to stop (CH-11) | Papa says one more. Papa always says one more. |
| NPC-06 Herr Wieck | Clipped commands, watch in hand; `[in German]` | Clara rests at three. Your questions may wait till never. |
| NPC-11 Chassériau | A boy's awe held in by studio manners; never a crush (CANON §7) | Colour lies, Monsieur Ingres says. Yours doesn't. Shh. |
| NPC-12 Horace Vernet | Brisk soldier-painter; anecdotes at a gallop (CH-13) | Greek letters in Urania's robe, Delacroix. That's a sum. |
| NPC-16 Kalkbrenner | Pompous method-talk that still respects talent | My method makes pianists. Chopin was already one. I said so. |
| NPC-21 Victorine Farrenc | Bright seven-year-old chatter; scales counted | Is the flying ship real? Maman says no. Papa winks. |
| NPC-22 Paganini | Few words, each a verdict (CH-E2) | You listen like a thief, pianist. Good thieves listen. |
| NPC-23 Louis-Philippe | Genial, bourgeois, well-travelled; English from exile | Corée! I crossed the Atlantic once. Never your sea. |
| NPC-25 Rambuteau | Harried administrator: lists, budgets, fountains | Fountains first, then pavements, then trees. Then sleep. |
| NPC-27 Count Apponyi | Diplomatic formality over unease (CH-07) | Music in my house, Lord Vane. Wagers, elsewhere. |
| NPC-28 Thérèse Apponyi | Delighted, spectacle-hungry hostess | Two pianos and Rossini judging! Paris will die of envy. |
| NPC-29 Hiller | Cheerful connector: names, dates, invitations | Bach for three keyboards. Chopin wants the quiet part. |
| NPC-31 Musset (C) | Languid, petulant, beautifully phrased | Fog on canvas, mademoiselle? I do fog in verse. Better. |
| NPC-32 Victor Hugo (C) | A grand observer hoarding details (CH-04, CH-07) | I counted the paving stones from my window. Six hundred by noon. |
| NPC-35 Habeneck (C) | Gruff pride; tempo is law (CH-13) | I gave Paris its Beethoven. Tonight Berlioz has my podium. One night. |
| NPC-41 Schlesinger (C) | Publisher's patter: deadlines and quarrels | A gazette from January. Write for me. Unsigned, even. |
| NPC-43 Daumier (C) | Laconic, mordant, a working man's irony (CH-04) | I drew the man paying the bruisers. Your painter drew him better. |
| FIC-02 Mère Gaudin | Mothering by scolding | Soup first. Genius after. Wipe your feet, Monsieur Corée. |
| FIC-03 Petit-Louis | Faubourg street-runner's speed | Grey gloves outside. Sent 'em to Pantin. Pay me in bread. |
| FIC-09 Mathurin | Few words, quarryman's lore | Stone sings where the dead lie thick. Keep to the lantern. |
| FIC-08 Roussel | Parade-ground clipped | Steady… The boy breathing. The rest as you like. *(both phrases canon)* |
| FIC-12 Prof. Yoon | Precise, warm, polite register | This letter is older than the annex. It expects you. Sit. |
| FIC-13 Det. Oh | Dry, patient, unconvinced | Amnesia. Nine months. Basement dust on your shoes. Sure. |
| FIC-14 Céline | Decisive Parisian executive | He wanted you silenced. I want my evening back. Burn it. |
| FIC-10 Kang Do-hyun | Gruff, practical love | Sit. Your mother cooked for nine months. Eat for nine months. |
| FIC-11 Park Hye-jin | Teacherly, fierce | Your hands. Show me your hands. …You've been practising. Good. |

---

## 5. Battle Barks

### 5.1 Bark rules

| Rule | Value |
|---|---|
| Display | Top battle message strip, one line, **≤ 30 characters** (hangul counts 2); no portrait, no name tab; the speaker's sprite plays a one-frame nod; auto-advances after 60 frames; never pauses the ATB, even in Wait mode |
| Target length | ≤ 24 characters where possible (cap 30). The French build adapts barks freely rather than translating them, so an English bark may run to the cap (§8.3) |
| Frequency | Start: boss battles without a scripted opener, plus 1 random battle in 4 (never two in a row) · Victory: always one (the member who struck last, if standing; else a random living member) · KO: 1 in 2 · Low HP: the first time per battle a member falls to ≤ 25% max HP (which is also Cadenza range, CANON §11d) · Revive: always · Command: first use per battle, then 1 in 4 · Synergy: always, spoken by its lead voice · Octave: every Voice |
| Priority | Scripted battle text > Synergy and Octave > command > KO, low HP, revive > start, victory. One bark at a time; a lower bark is dropped, never queued; 6-second cooldown per character. Cadenzas show only their banner (≤ 30 characters, CANON §16h), no bark |
| Names | Barks never contain "Min-jun" (each friend's form of address changes by chapter, CANON §16c). Seoul members use 오빠 and 민준아 freely |
| Silence | Scenario docs may flag a battle **silent** (BOSS-16 The Audience; any battle inside a grief scene): no barks at all |
| Gates | In CH-E1 Lucile's barks come only from her Seoul pool (§5.3); while `g_fractured` her victory pool is replaced by the Fractured pool; IMPASTO lines from CH-14; LUMIÈRE lines in the epilogues; Liszt's MEPHISTO line from CH-13; Jae-won plays at most one gamer bark per battle |
| Korean in barks | Only words already glossed in a field scene: 하나, 둘, 셋 (CH-E1 only; glossed when Min-jun counts alone in the CH-01 galleries; in 1833–34 battles the count is in English, because Onlookers make any battle a public moment, CANON §16c), 얼쑤 and 좋다 (Jae-won explains chuimsae when he joins in CH-E1), 오빠 and 엄마 (CH-E1 reunion), and each Hanmadi word Lucile has collected (logged in the phone's Translate app, §5.3) |
| Hanmadi (CH-E1) | Each of Lucile's 40 Hanmadi words replaces its English equivalent in one bark of her Seoul pool, in hangul only (CANON §4f; §5.3), e.g. "Worth four sous. Maybe five." → "Worth four 동전. Maybe five." |

### 5.2 Bark tables

**Synergy lead voices** (one per Synergy, so every call has an owner): SYN-01 LU · 02 LI · 03 CH · 04 BE · 05 DE · 06 FA · 07 AL · 08 BE · 09 LI · 10 DE · 11 FA · 12 LU · 13 DE · 14 BE · 15 MJ · 16 every member (Voice lines) · 17 SY · 18 JW · 19 JW · 20 JU · 21 CH · 22 AL · 23 FA. The **Octave Voice** lines follow LM-01's notes (D E F♯ G A B C♯ D: MJ, BE, DE, AL, CH, LI, FA, then Lucile's octave, CANON §15c); C♯ "wants to resolve" until Lucile's D answers it.

**PC-01 Min-jun**

| Trigger | Barks |
|---|---|
| Start | Tempo, everyone. Stay with me. / From the top. Count us in. / I'll set the key. Follow. |
| Victory | And… rest. / Not bad for a student. / Bow first. Then run. |
| KO · Low HP · Revive | Fermata… I'll come back in. · One, two, three… breathe. (CH-E1: 하나, 둘, 셋… breathe.) · I'm back. Where were we? |
| RECITAL | Movement I: Listen. This one's borrowed. / Continue: Second movement. Stay close. / Movement III: Last movement. All of it! / his own pieces (REP-27, 29, 30): This one's mine. |
| CONDUCT | Your cue—now! |
| Synergy | SYN-15: Sound into colour—now! |
| Octave (D) | The first note. Mine to give. |

**PC-02 Lucile**

| Trigger | Barks |
|---|---|
| Start | Hold still. I'm painting you. / Bad light. I'll change it. / Théo's waiting. Make it quick. |
| Victory | Done. Varnish it later. / Worth four sous. Maybe five. / Look—the light changed again. |
| Victory, Fractured | Done. / Don't. Not now. |
| KO · Low HP · Revive | The colours… going grey… · Not yet. I'm not finished. · Who dropped me? I'll remember. |
| PLEIN AIR | IMPRESSION: Don't paint outlines. / POINTILLÉ: Points of light. Watch. / IMPASTO: Thick paint. Thicker! / *Nuit étoilée*: The stars are turning! / LUMIÈRE: My own light. Mine. / Shift the Hour: Wrong hour. I'll fix it. |
| Synergy | SYN-01: Moonlight! Play, I'll paint! / SYN-12: Night-blue. Hush now. |
| Octave (D, the octave) | And D. Home, whichever it is. |

In CH-E1 Lucile's whole pool is §5.3.

**PC-03 Berlioz**

| Trigger | Barks |
|---|---|
| Start | To arms! Or rather, to brass! / Five hundred players! Charge! / Ah, critics. I know this kind. |
| Victory | Sublime! Write that down! / Encore? No. They're beaten. / A triumph! Unpaid, as usual. |
| KO · Low HP · Revive | Misunderstood… again… · This is not my death scene! · Lélio returns to life! |
| ORCHESTRATE | Cue: Brass! Strings! More! / Tutti: Tutti! Everyone, together! / Cacophony: That was… avant-garde. |
| Synergy | SYN-04: Again! The fixed idea! / SYN-08: Liberty, Eugène! Paint her! / SYN-14: The sabbath dream! Play! |
| Octave (E) | E! Fortissimo, my friends! |

**PC-04 Delacroix**

| Trigger | Barks |
|---|---|
| Start | Shall we? I dislike waiting. / Vermilion, I think. For you. / Ah. A subject worth painting. |
| Victory | Adequate. Barely. / My cuff is ruined. Pity. / Note it: they lacked colour. |
| KO · Low HP · Revive | Grey… how vulgar… · Red on red. How Romantic. · I was resting my eyes. |
| CANVAS | Strike: Two pigments. One verdict. / Sketch: Hold that pose. Thank you. / *Liberté*: Forward—Liberty leads! |
| Synergy | SYN-05: Into the shadow, monsieur. / SYN-10: Your light. My dark. Now. / SYN-13: For our brother. Now. |
| Octave (F♯) | F sharp. A colour, not a note. |

**PC-05 Alkan**

| Trigger | Barks |
|---|---|
| Start | Hm. / Seventy-eight keys. Begin. / I would rather be home. |
| Victory | Done. May I go? / Tempo was acceptable. / Vanity of vanities. Done. |
| KO · Low HP · Revive | Quieter… at last… · Bleeding. Noted. · I was enjoying the silence. |
| ÉTUDE | Success: Perfect. As written. / Failed input: …I will practise that. / Recluse triggers: Alone. Good. Finally. |
| Synergy | SYN-07: Pedals too. Both feet. / SYN-22: Liszt. Try to keep up. |
| Octave (G) | G. Steady. As always. |

**PC-06 Chopin**

| Trigger | Barks |
|---|---|
| Start | Must we? Very well. / Gently. Then, not gently. / Crowds. Let us be brief. |
| Victory | There. Elegant enough. / Clean enough for Kalkbrenner. / I need a glove. And a chair. |
| KO · Low HP · Revive | Not… in public… · I am fine. Do not fuss. · How embarrassing. Thank you. |
| RUBATO | Borrow: A little time—borrowed. / Repay: And returned, as promised. / *Tempo Rubato*: Rubato. Steal from them all. |
| Synergy | SYN-03: Lean on the beat. Now. / SYN-21: For those who cannot go home. |
| Octave (A) | A. For Warsaw. For all of you. |

**PC-07 Liszt**

| Trigger | Barks |
|---|---|
| Start | Mon ami, an audience! / Watch closely. I perform once. / Paganini would weep. Begin! |
| Victory | Bravo, bravo. Yes, me. / Shall I sign albums? / Too short! I had a coda! |
| KO · Low HP · Revive | Not… the hair… · Ah! Now it's dramatic. · Did they applaud? Good. |
| TRANSCEND / MEPHISTO | Two at once. Why not three? / *Transcribe*: Yours? Mine now, louder. |
| Synergy | SYN-02: Two pianos! Thunder! / SYN-09: Frédéric! Show them! |
| Octave (B) | B! Hold it—hold it longer! |

**PC-08 Farrenc**

| Trigger | Barks |
|---|---|
| Start | Annotate first. Then strike. / Let us be methodical. / Four of them. I have a pencil. |
| Victory | Correct. As predicted. / File that under "resolved." / Victorine will want details. |
| KO · Low HP · Revive | Erased… no… · Unacceptable. Note it. · Thank you. Back to work. |
| COUNTERPOINT | Annotate: Weak point. Marked. / Canon: Follow my line. / Fugue: Earth, water, light. Fugue. / Cadence: Cadence. Clean slate. |
| Synergy | SYN-06: Equal measure. For all. / SYN-11: Your theme, inverted. Twice. / SYN-23: Then be impossible to ignore. |
| Octave (C♯) | C sharp. It wants to resolve. |

**PC-09 Seo-yeon**

| Trigger | Barks |
|---|---|
| Start | 오빠, stay behind me. / Bow up. Let's go. / You picked the wrong family. |
| Victory | Practice pays. Literally. / Don't clap. Just move. / That one was for 엄마. |
| KO · Low HP · Revive | 오빠… sorry… · I'm fine. Don't you dare. · Took you long enough. |
| BOW | Sostenuto: Long bow. Breathe with me. / Spiccato: Spiccato—bounce! |
| Synergy | SYN-17: Arirang. Like 엄마 taught us. |

**PC-10 Jae-won**

| Trigger | Barks |
|---|---|
| Start | 얼쑤! Eolssu! Let's roll! / Four beats. Then chaos. / Boss music! I love it! *(gamer)* |
| Victory | 좋다! Jota! That's the groove! / Roommates: undefeated. / Encore? Encore. Encore! |
| KO · Low HP · Revive | Dropped… the sticks… ugh. · Okay, okay. Not great. · Respawned! …Sorry. Back. *(gamer)* |
| BEAT | Start: Deong, gi-deok, kung! / Perfect 8-hit steal: Eight for eight! Wallet too. |
| Synergy | SYN-18: Hwimori! Fastest we've got! / SYN-19: Thunder, wind, rain, clouds! |

**PC-11 Julien**

| Trigger | Barks |
|---|---|
| Start | Count it off. One, two… / Nobody panic. I'm panicking. / Gentlemen, the changes. |
| Victory | Take five, everybody. / Hey, that resolved! / Not bad for a sideman. |
| KO · Low HP · Revive | Last call… already? · Bad night. Worse set. · Back on the bandstand. |
| IMPROVISE | Spin: Spin the changes! / ii–V–I: Two-five-one. Home. / *Tritone Storm*: Flat two, three times. Storm! / *Blue Note*: …Blue note. Meant that. |
| Synergy | SYN-20: Blue hour. Slow and low. |
| Octave (Blue Note) | Blue note. Trust me on this. |

### 5.3 Lucile's Seoul pool (CH-E1)

In CH-E1 every Lucile bark comes from this pool of **40 lines, each with one swap slot**. Rows 1–15 are Seoul forms of the 15 trigger barks that can occur in Seoul (2 Start, 3 Victory, KO, Low HP, Revive, 6 PLEIN AIR, SYN-01; her Théo line, the Fractured pool, SYN-12 and the Octave cannot). Rows 16–40 are 25 Seoul-only barks, drawn with them at Start (rows 16–25) and Victory (rows 26–40). Start therefore draws from 12 lines and Victory from 18, at the §5.1 frequencies.

| Rule | Value |
|---|---|
| Binding | Each of the 40 Hanmadi words (the list and its teachers are overworld_and_towns §8.2) owns one slot: the bark where it replaces its own English equivalent. A bark plays in English until its word is collected, then with the word swapped, so a word learned in the field is heard in the next battle that draws its bark. The binding is fixed: a "next free slot" rule would put 엄마 into a line about snow |
| Display | The swapped word shows in hangul only, with no romanization and no gloss; the phone's Translate log (CANON §4f) records both at collection. Every line, swapped or not, is ≤ 30 characters (hangul counts 2) |
| Glyphs | Syllables come from art_and_ui's 100-syllable Hanmadi reserve (art_and_ui §8.3) |
| Voice | Her English stays 1830s French (LAW-24), so §8.2's idiom bans still apply to her in Seoul; the Korean word is the only 2026 thing in the line |
| Effect | Each collected word adds +1% to LUMIÈRE (CANON §4f); the engine counts words collected, not barks heard. All 40 unlock 별 *Byeol*, which owns no slot |
| Unchanged lines | Rows 3, 6 and 13 keep their §5.2 wording; the other trigger rows are Seoul forms of the same beats |

| # | Trigger | Bark (English) | Word | Swapped |
|---|---|---|---|---|
| 1 | Start | Hold still. I'm a painter. | 화가 | Hold still. I'm a 화가. |
| 2 | Start | My brush is wet. Who's first? | 붓 | My 붓 is wet. Who's first? |
| 3 | Victory | Worth four sous. Maybe five. | 동전 | Worth four 동전. Maybe five. |
| 4 | Victory | Done. Varnish after supper. | 밥 | Done. Varnish after 밥. |
| 5 | Victory | I'll paint that. From memory. | 기억 | I'll paint that. From 기억. |
| 6 | KO | The colours… going grey… | 색 | The 색… going grey… |
| 7 | Low HP | Not yet. The painting first. | 그림 | Not yet. The 그림 first. |
| 8 | Revive | Who dropped me? Not a friend. | 친구 | Who dropped me? Not a 친구. |
| 9 | IMPRESSION | Light on the river—there! | 강 | Light on the 강—there! |
| 10 | POINTILLÉ | Points, like snow. Watch. | 눈 | Points, like 눈. Watch. |
| 11 | IMPASTO | Thick paint, wild wind! | 바람 | Thick paint, wild 바람! |
| 12 | *Nuit étoilée* | Stars turning—hear the music? | 음악 | Stars turning—hear the 음악? |
| 13 | LUMIÈRE | My own light. Mine. | 빛 | My own 빛. Mine. |
| 14 | Shift the Hour | Wrong hour. Ring the bell. | 종 | Wrong hour. Ring the 종. |
| 15 | SYN-01 | Your piano, my brush. Now! | 피아노 | Your 피아노, my brush. Now! |
| 16 | Start | Winter bites. So do I. | 겨울 | 겨울 bites. So do I. |
| 17 | Start | Read them like a score. | 악보 | Read them like a 악보. |
| 18 | Start | You need tuning. Badly. | 조율 | You need 조율. Badly. |
| 19 | Start | I'm the hammer. You're felt. | 망치 | I'm the 망치. You're felt. |
| 20 | Start | Tell me your name first. | 이름 | Tell me your 이름 first. |
| 21 | Start | The solstice brought me here. | 동지 | The 동지 brought me here. |
| 22 | Start | After, the stone-wall road. | 돌담길 | After, the 돌담길. |
| 23 | Start | Hum me that song. For luck. | 노래 | Hum me that 노래. For luck. |
| 24 | Start | Your big brother leads. | 오빠 | Your 오빠 leads. |
| 25 | Start | Fall like ginkgo leaves. | 은행나무 | Fall like 은행나무 leaves. |
| 26 | Victory | Your mama is waiting. Hurry. | 엄마 | Your 엄마 is waiting. Hurry. |
| 27 | Victory | Your papa could fix that. | 아빠 | Your 아빠 could fix that. |
| 28 | Victory | Now—red-bean porridge! | 팥죽 | Now—팥죽! |
| 29 | Victory | Your family fights well. | 가족 | Your 가족 fights well. |
| 30 | Victory | Pancakes! I'll pay. Once. | 호떡 | 호떡! I'll pay. Once. |
| 31 | Victory | The professor would approve. | 교수님 | The 교수님 would approve. |
| 32 | Victory | That was only practice. | 연습 | That was only 연습. |
| 33 | Victory | Singing room next? I'll sing. | 노래방 | 노래방 next? I'll sing. |
| 34 | Victory | Amazing! Is that the word? | 대박 | 대박! Is that the word? |
| 35 | Victory | Rice cakes. The spicy ones. | 떡볶이 | 떡볶이. The spicy ones. |
| 36 | Victory | Tea, and I'm sitting down. | 차 | 차, and I'm sitting down. |
| 37 | Victory | Mulberry paper. I want some. | 한지 | 한지. I want some. |
| 38 | Victory | It's warm. Stay close. | 따뜻해 | 따뜻해. Stay close. |
| 39 | Victory | Happy New Year! | 새해 복 많이 받으세요 | 새해 복 많이 받으세요! |
| 40 | Victory | My papers! Still dry? Good. | 서류 | My 서류! Still dry? Good. |

Rows 24, 26, 27 and 29 speak to Seo-yeon (the Seoul party is always the same four, CANON §11a); row 22 answers the stone-wall-road legend that a Jeong-dong guide tells (§6.2).

---

## 6. NPC Chatter

### 6.1 Rules

1. **Who speaks.** Generic townsfolk are Tier C: a 4 × 30 box and a trade for a name tab (`[N:Laundress]`, `[N:Bill-sticker]`), never "Villager" or "Man". Named townsfolk belong to overworld_and_towns.
2. **Length.** One box per NPC; two at most. Talking again gives a shorter repeat line, never the same box twice.
3. **One job per line:** local colour, a rumour that tracks story state, a hint (never naming a button or menu), or a human detail. No exposition dumps and no lore lectures from strangers.
4. **Mood follows the story.** Every district carries one chatter set per act, swapped by story flags (riot, wedding, abduction, gala, Night of Stars). Within an act, lines may be gated `[IF:]` on a beat.
5. **Secrecy gossip.** From Murmured upward, one NPC per district map speaks a tier line (§6.3) in place of a set line.
6. **Depiction.** Cholera through absence and memory, never a monster; poverty with names and trades; republicans' grievances heard fairly; prejudice ("Chinese?") voiced only as ignorance and answered on screen or by the line itself (CANON §16c, §16e). No modern idiom, no future knowledge.
7. **Language.** Rhine NPCs carry `[in German]`. Seoul NPCs speak Korean by default; in Lucile's point-of-view scenes their Korean shows as untranslated hangul (§7.3).

### 6.2 Sample lines by district and act

Each table row is one district's chatter set for that act (four lines; the engine deals them to that map's generic NPCs). A set plays only while its act's set is loaded, so a line gated on a flag must be one that can be set while that act's set is live.

**Act I (CH-01–CH-04): rain, grief, scales from every window, a tense anniversary**

| District | Lines |
|---|---|
| LOC-P02 Latin Quarter | **Ragpicker:** Rags, bones, bottles! Half this street went in the spring of '32. Their rags still find me. · **Student:** We buried our anatomy professor in April. We still leave his chair empty at lectures. · **Candle-seller:** A candle for the ex-voto, monsieur? Two sous. Saint-Jacques hears everyone this year. · **Water-carrier:** Seine water, filtered through sand! The best in Paris, or at least the wettest. |
| LOC-P03 Faubourg-Poissonnière | **Violin student:** Old Cherubini threw a foreigner down the steps this morning. Seventy-two, and what an arm. · **Laundress:** Every window on rue Bergère plays scales. I wring my sheets in C major. · **Porter:** No ticket, no concert hall. No exceptions. Except the director's cat. · **Neighbour** `[IF:ch02_tavern_job]`: The Diapason's pianino has three dead keys. The new boy plays around them like holes in the road. |
| LOC-P07 Marais | **Cabinetmaker:** A year ago they barricaded Saint-Merry. My apprentice went. He didn't come back. · **Printer:** Citizen, take this. No, not here, the sergeant's watching. Read it at home. · **Guardsman:** Move along, monsieur. No crowds this week, by the law of April '31. Yes, two of you is a crowd. · **Old woman:** Monsieur Hugo writes all night up there. His lamp has been our clock since the autumn. |
| LOC-P22 Seine Quays | **Bouquiniste:** Byron, two francs. Lamartine, one. Chateaubriand? Sold out. He always is. · **Washerwoman:** Mind the soap, monsieur! The river takes everything and gives back only fog. · **Fisherman:** Gudgeon bite at dawn, monsieur. The rest of Paris bites after noon. · **Toll-keeper:** One sou to cross the Pont des Arts. The view is free. The walking is not. |
| LOC-P32 Île de la Cité (CH-04) | **Hôtel-Dieu porter:** Last spring we laid them four to a bed. This spring, one. God be thanked. · **Verger:** The English climb our towers for Monsieur Hugo's hunchback. I tell them he's at lunch. · **Flower-seller:** Pinks and lilac, two sous a bunch. For the June dead, monsieur? Then one sou. · **Prefecture clerk:** Lost papers, third floor. Lost hope, Notre-Dame, across the square. |

**Act II (CH-05–CH-09): Paris opens; a hot summer of salons, the duel, the wedding**

| District | Lines |
|---|---|
| LOC-P03 Faubourg-Poissonnière | **Laundress:** The foreign pianist plays for countesses now. Gaudin says he still eats her soup. · **Shop girl:** Liszt bought gloves at our counter! Tried on twelve pairs and tipped like a prince. · **Porter** `[IF:ch09_banns]`: Monsieur Berlioz marries his Irish actress on Thursday. At the English embassy, no less! · **Carter:** The Bercy depots are hiring night men. Good pay, no questions, grey coats on the gate. |
| LOC-P07 Marais (CH-07) | **Concierge:** Monsieur Hugo noticed your white soles. He notices everything, then writes it down. · **Printer:** That June pamphlet with your name on it? Forged. I know my own type, and that wasn't it. · **Cabinetmaker:** The Alkan house plays all night: scales, pedals, psalms. We sleep in rhythm now. · **Old woman:** The barricade stones are back in the street. You'd never know. I know. |
| LOC-P10 Grand Boulevards | **Dandy:** An ice at Tortoni's, a cigar on the boulevard, a scandal by supper. That is Paris. · **Bill-sticker:** Concert at Pleyel's, the twenty-first, for the orphans! On Chopin's own piano! · **Flower-seller:** Parma violets, monsieur? Monsieur Chopin buys them by the armful. · **Gossip:** They say the Corean plays music no one has written yet. Nonsense. Delicious nonsense. |
| LOC-P14 Faubourg Saint-Germain | **Footman:** Madame receives on Thursdays. Monsieur is not on the list. Monsieur may admire the gate. · **Legitimist:** Since 1830 a citizen-king sits in the Tuileries. I keep my shutters closed on principle. · **Lady's maid** `[IF:ch07_duel_done]`: Madame came home from the Austrian embassy at three, humming something nobody has written. She won't say a word. · **Coachman:** Lord Vane pays double and tips in English coin. Odd man. Good horses. |
| LOC-P16 Palais-Royal | **Bookseller:** Novels upstairs, pamphlets downstairs, and below that, monsieur, we don't discuss. · **Pickpocket:** Wasn't me! Whatever it was, it wasn't me! · **Café waiter:** The Sorcerer of Chords plays here on Tuesdays. Strange chords. Fine tips. · **Gambler:** Nineteen hasn't come up all week. Tonight it will. I'm nearly certain. |
| LOC-P22 Seine Quays | **Washerwoman:** The painter girl was out at dawn again. She paints the fog, that one. · **Veteran** `[IF:ch06_vendome]`: They put the Emperor back on his column. My father wept. I cheered. Same thing. · **Bargeman** `[IF:ch08_barge]`: *La Mouette* is a good barge. Mind the sluices. She bites. · **Bouquiniste:** Sold a Hugo to an Englishman. He paid in guineas and asked if I'd seen a door. |
| LOC-P24 Montmartre | **Miller:** Up here the wind is free and the wine is cheap. We're outside the toll wall. · **Telegraph keeper:** The semaphore talks to Lille in minutes. Mostly about the weather. · **Vine-dresser:** Painters climb up for the view. They leave with it, and without paying for wine. · **Child:** Mademoiselle Lucile painted my goat! It looked like a cloud with legs. |
| LOC-P32 Île de la Cité | **Bath attendant:** The floating baths by the Pont Neuf, four sous, towel extra. Cleaner than the river. Not hard. · **Lawyer:** Three cases before noon, all wine slipped past the toll. Paris drinks; the courts sober it. · **Verger:** The great bell is called Emmanuel. Put your hand on the rope. Feel that? That's Paris. · **Flower-seller:** Roses, monsieur? Half the Faubourg marries this autumn, and the other half is jealous. |

**Act III (CH-10–CH-13): hunted on the roads; Paris in November cold; the gala**

| District | Lines |
|---|---|
| LOC-R03 / R04 Berry | **Market woman:** The Parisian lady at Nohant wears trousers and smokes. My cow is scandalised. · **Hurdy-gurdy player:** A bourrée, monsieur? Two sous, and I play till your feet forgive you. · **Innkeeper:** A virtuoso from Paris under my roof! He tipped the stable boy in gold. · **Shepherd:** Don't walk the Vallée Noire at night. The wolves this year… they tick. |
| LOC-R06 Liège | **Coal-heaver:** Belgian three years now, they say. The coal hasn't noticed. · **Innkeeper:** The Franck boy plays our salon piano at eight. One franc a seat; his father takes the coins. · **Gunsmith:** Liège barrels, best in Europe. A Paris baron took two hundred last month. For hunting, he says. · **Choirboy:** The pale Polish gentleman heard our Mass without a word, then gave each of us a sou. |
| LOC-R07 Düsseldorf | **Academy student** `[in German]`: Herr von Schadow sold a French picture today. Strange. He loved it. · **Bargeman** `[in German]`: Steamboat from Cologne on Tuesday. Mind the Lorelei. She sings. · **Chorister** `[in German]`: Herr Mendelssohn rehearses us until the candles weep. · **Customs clerk** `[in German]`: Papers. Corean? Is that a kind of French? |
| LOC-R10 Strasbourg (the return, Thu 21 Nov) | **Sacristan:** The great clock stopped before the Revolution. Someone always swears he'll mend it. · **Customs officer:** From Baden? Declare your tobacco, your books and your opinions. · **Pastry-cook:** Goose-liver pâté in a crust. Strasbourg's one export the whole Rhine envies. · **Postmaster:** A letter from Paris for a Monsieur Kang, signed G. Sand. The clerk read the envelope twice. |
| LOC-P02 Latin Quarter | **Nurse's helper:** Sœur Marthe's dispensary is full again. She boils everything. Nearly the priest. · **Student:** Grey coats on every corner this week. Old Garde royale men. They don't drink. · **Chestnut seller:** Hot chestnuts! Cold hands? Mine too. That's why I sell chestnuts. · **Watchman:** Lights in the old abbey wing at night. It's been shut since the Revolution. |
| LOC-P22 Seine Quays (CH-12) | **Bouquiniste:** Fog so thick I sell books by feel. That one's either Racine or a cookbook. · **Washerwoman:** The painter girl's back. Paler. She stood on the bridge an hour and painted nothing. · **Bargeman:** Ice by Christmas, they say. Then the river stops, and so does my pay. · **Toll-keeper:** One sou, still. Some prices the fog can't touch. |
| LOC-P28 Panthéon (CH-12) | **Scaffold mason:** Monsieur David carves the pediment. We carve the frost off the planks first. · **Polytechnicien:** Our professor says the dome answers certain notes. He's mad. He's also right. · **Widow:** Sainte Geneviève saved Paris from the Huns. This year I'd settle for the rent. · **Lamplighter:** Lights in the crypt windows at two in the morning. The Panthéon's empty. Isn't it? |
| LOC-P32 Île de la Cité (CH-12) | **Hôtel-Dieu porter:** Chest fevers, November's guests. We burn juniper in the wards and pray it's nothing worse. · **Verger:** Something walks the north tower at night. Gargoyles, they say. I don't go up after vespers. · **Boatman:** Fog to the waterline. I steer by the bells of Saint-Germain-l'Auxerrois. Hush. · **Prefecture clerk:** The Prefect's been in a temper since Sunday. Something about a baron and a great deal of paper. |
| LOC-P10 Grand Boulevards | **Bill-sticker:** Royal gala at the Opéra, the sixth! For the orphans. The Baron d'Orsenne pays for all. · **Dandy:** A Corean concerto, Liszt at the second piano, Berlioz conducting? Habeneck is sulking in public. · **Seamstress:** Forty costumes for *La Sylphide* by Friday. We're angels, Taglioni says. Tired angels. · **Programme-seller:** Gala programmes, ten sous! Taglioni flies in part two, and the King comes. |

**Act IV (CH-14): open war, December cold, every door open before the last night**

| District | Lines |
|---|---|
| LOC-P03 Faubourg-Poissonnière | **Laundress:** Gaudin lights a candle for the Corean every night. She says it's for business. · **Violin student:** Monsieur Berlioz turns thirty on Wednesday. He calls it a tragedy in five acts. · **Carter:** Madame Sand is off to Italy with her poet. The Lyon mail coach, Thursday. · **Errand boy:** The Diapason shut early. Mère Gaudin's sitting at the pianino, not playing it. |
| LOC-P10 Grand Boulevards | **Concert-goer:** Hiller, Chopin and Liszt, three keyboards at once! I'd sell my coat for a seat. · **Cabman:** Something on the Opéra roof the night of the gala. Big as a whale. Silk. Don't ask me. · **Beggar:** The Baron's carriages go up to the Panthéon every night. Charity, they say. · **Old soldier:** Snow by Christmas. My knee says so, and my knee has never lied. |
| LOC-P14 Faubourg Saint-Germain | **Footman** `[IF:ch14_vane_defected]`: Lord Vane's house is shuttered. Servants paid off, paintings crated. England, they say. · **Lady's maid:** The princess receives Italian exiles and pianists. The ministry can't tell them apart. · **Coachman:** Madame says half the scenery fell during the gala and the concerto never stopped. A miracle. · **Valet:** Thalberg is back in Paris? Privately, of course. The Viennese do nothing in public. |
| LOC-P16 Palais-Royal | **Bookseller:** Almanacs for 1834! The harvest, the weather, the King's health. All guessed, all guaranteed. · **Café waiter:** The Sorcerer of Chords hasn't played here since autumn. The piano misses him. So do the tips. · **Gambler:** Nineteen came up at last. I'd gone home. Of course I'd gone home. · **Pickpocket:** I've retired for Christmas. My hands are cold and the purses are thin. |
| LOC-P22 Seine Quays | **Bouquiniste:** *Lélia*, two francs. Its author leaves for Italy on Thursday. Buy it before she writes another. · **Washerwoman:** The painter girl paints the river at six every morning, frost or no frost. · **Toll-keeper:** A flying ship crossed the bridge at midnight and never paid its sou. I wrote to the Prefect. · **Fisherman:** The gudgeon have gone deep for the winter. Wise fish. |
| LOC-P24 Montmartre | **Telegraph keeper:** Clear skies tonight. Coldest of the year. Best stars of the year, too. · **Miller:** A painter asked my sails to stay still for her. I said the wind decides, mademoiselle. · **Vine-dresser:** Winter vines look dead. They aren't. They're waiting. Like everyone up here. · **Child:** Is the Corean going home? Where is his home? Past Lille? |
| LOC-P28 Panthéon | **Scaffold mason:** Frost on the planks, and a flying ship over the dome last night. I've stopped drinking. Again. · **Polytechnicien:** Grey coats at every crypt door, checking their watches. Nobody posts guards on the dead. · **Student:** Coldest night of the year coming, the astronomers say. Clearest sky, too. Bring a coat. · **Old woman:** My grandson counts the stars from these steps. He reached three hundred, then lost his place. |
| LOC-P32 Île de la Cité | **Hôtel-Dieu porter:** Sœur Marthe sent boiled linen and her salted water. Fewer died this week. Write that down. · **Verger:** Midnight Mass in a week. We're polishing every candlestick in Christendom. · **Flower-seller:** Holly and mistletoe from the Bois! The cold keeps it fresh, and me not at all. · **Prefecture clerk:** Grey coats are to be watched, not stopped. Prefect's orders. Don't ask me the difference. |

**CH-E1 (Seoul, December 2026).** Seoul NPCs speak Korean, rendered in English; in Lucile's point-of-view scenes their lines show as untranslated hangul (§7.3).

| District | Lines |
|---|---|
| LOC-S03 Jeong-dong | **Palace guide:** Couples who walk the Deoksugung wall road break up, they say. Walk it anyway. · **Janitor:** Ginkgo fruit stinks in autumn. In winter the trees just stand there being beautiful. Lazy. · **Office worker:** The old Russian legation tower's up that hill. Everyone takes a photo. Nobody reads the sign. · **Conservatory student:** Room B-07 is never free. Some first-year violinist keeps it warm every night. |
| LOC-S07 Hongdae | **Busker:** The missing conservatory kid is back? And he's busking here? Wild. · **Food-stall owner:** Tteokbokki, extra cheese. Your friend in the red scarf, first time? Gently. It's spicy. · **Student** `[IF:spot_t1]`: That painter is all over the feeds and nobody can find her account. Mysterious. · **Couple:** Snow on New Year's Eve and the bell at Bosingak. Perfect, apart from the crowds. |
| LOC-S12 Insadong | **Antique dealer:** Louis-Philippe sous? Real ones? Mr. Baek two doors down buys them by weight. · **Calligraphy teacher:** Your friend writes 별 better than my students. Her brush already knows. · **Tea-house owner:** Omija tea. Five flavours: sweet, sour, salty, bitter, hot. Like a long life. · **French tourist** `[in French]`: Pardon, your friend speaks like my great-great-grandmother. It's charming. |

**CH-E2 (Paris, winter 1834)**

| District | Lines |
|---|---|
| LOC-P03 Faubourg-Poissonnière | **Laundress** `[IF:che2_proposal]`: Mère Gaudin is already sewing for a June wedding. Nobody's told her it isn't hers. · **Violin student:** Berlioz's concert on the twenty-second: I was eighth violin! Paganini looked at me. Or near me. · **Porter:** A note from Signor Paganini for Monsieur Berlioz. I ran. I never run. · **Errand boy:** The Diapason's pianino has all its keys again. Théo Aubray fixed them for soup. |
| LOC-P24 Montmartre, 1834 | **Miller** `[IF:g_atelier_restored]`: The Aubray girl and her Corean took the old studio. Two easels, one piano, no curtains. `[/IF]` `[IF:not_g_atelier_restored]`: The Aubray girl and her Corean took the old studio. One easel, no piano, no curtains. They seem happy anyway. `[/IF]` · **Vine-dresser:** Someone steals paintings at night. Only small ones, full of light. Who'd want those? · **Child** `[IF:che2_proposal]`: Mademoiselle Lucile was up at dawn on her birthday. She won't say why. She keeps smiling. · **Telegraph keeper:** The semaphore says snow in Lille. It always says snow in Lille. |
| LOC-P10 Grand Boulevards, 1834 | **Bill-sticker:** The Salon opens on the first of March! Delacroix, Delaroche, Ingres. Bring a handkerchief. · **Waiter:** Julien's café plays chords that go nowhere and arrive anyway. I go every night. · **Cellist:** Paganini sat in a side box and applauded Berlioz. Paganini! Applauded! · **Gossip** `[IF:che2_jury_won]`: A girl's canvas got past the jury. Hung up by the ceiling, but hung. |

### 6.3 Secrecy gossip (one per district map, by tier)

From Murmured upward, one NPC per district map speaks a tier line in place of a set line. In Acts I–III the engine draws one of lines 1–2 per map visit; in Act IV only line 3 plays, because from CH-14 Secrecy governs police and public attention alone (CANON §11e).

| Tier (flag) | Line 1 | Line 2 | Line 3 (Act IV) |
|---|---|---|---|
| Murmured (`sec_t1`) | **Seamstress:** The Corean hums tunes nobody's heard. My cousin caught one. She's been odd since. | **Coachman:** I drove the foreigner twice. Both times he hummed, and both times my horse stopped to listen. | **Lamplighter:** The Corean's friends fly by night, they say. Lamplighters see things. Nobody believes us. |
| Watched (`sec_t2`) | **Porter:** A man with one grey glove asked which way the foreigner went. I don't see foreigners. | **Market woman:** Two gentlemen asked what the Corean buys. Bread and paper, I said. They wrote it down. | **Café waiter:** The Prefecture's men drink here now. Same table every night, facing the door. They tip badly. |
| Hunted (`sec_t3`) | **Carter:** Papers on the Pont Neuf. I told them he's Corean. They wrote down "Chinese". Idiots. | **Innkeeper:** A man paid me to say when the foreigner stays here. I said Tuesday. He comes Thursdays. | **Bill-sticker:** The Prefect's notice: a foreign musician, "for questions only". They said that about my brother. |
| Compromised (`sec_t4`) | **Shop boy:** We don't serve the Corean now. A man in one grey glove bought all our stock. Asked one favour. | **Concierge:** Don't come up the stairs, monsieur. Someone's asked every neighbour about you, door by door. | **Concierge:** Inspectors from the rue de Jérusalem asked for you by name. I said Lyon. They didn't believe me. |

---

## 7. Language Usage: French, Korean, and the Romance

### 7.1 French

- **Default tongue.** In 1833–34 every untagged English line is French. Show Min-jun's early French through brevity and pauses, never through broken grammar.
- **Kept French words.** The common words of CANON §16d (*monsieur, madame, mademoiselle, salon, atelier, quai, fiacre, bal, sou, franc, diligence*) are italic on their first appearance in the game, which opens an Almanach entry, and roman after that. Every other French term is italic every time and glossed in the line or by context on first use in each scene: *conseil de famille*, *tuteur*, *juge de paix*, *octroi*, *bouquiniste*, *chiffonnière*, *esquisse*, *au ciel*, *la manière lumineuse*.
- **Honorifics.** Full words in dialogue: capitalised before a name ("Monsieur Kang"), lower case alone ("Yes, monsieur."). M., Mme and Mlle appear only in name tabs, documents, signage and the *livret* (KEY-40). Titles: "Monsieur le Baron", "Madame la Comtesse", "Princess" (Belgiojoso), "Maître Brücke", "Sœur Marthe", "Herr" in `[in German]` lines. "Citizen" only from republicans in the Marais and the Latin Quarter. "Mon ami" belongs to Liszt; others use it only to tease him.
- **Corée and "Corean".** Country and people in 1833–34 speech: *Corée* and "Corean" (the period rendering). "Korean" only in Seoul and in Min-jun's private speech. Mère Gaudin's "Monsieur Corée" is a warm nickname Min-jun accepts (Théo borrows it until CH-12). "Chinese" only as the ignorance CANON §16c requires to be answered.
- **Units and time.** NPCs say *lieues*, *toises* and *pieds*, and count in francs and sous (CANON §14). From Min-jun, "kilometres" or "degrees Celsius" is a slip. Spoken time is "six o'clock" or "a quarter to one". Clock digits appear on screen only in HUD elements the canon defines (the Window Clock, CANON §11i; BOSS-27's countdown), never in captions, which carry place and date only (CANON §16a). Archon and Brücke alone may speak exact minutes, in words ("twelve forty-three"), and only in private or in CH-16.
- **Accents in the SNES font.** The font carries the full French set, capitals included (é è ê ë à â ç î ï ô û ù ü ÿ œ æ; É À Â Ç Ô Œ: *Le Clavier des Âges*), plus German ä ö ü ß, Polish ż ł ó ś ą ę ć ń (*Żal*, *Żelazowa*), « », —, …, curly quotes, ₩ and ♯ (menus only; dialogue writes "F sharp"). Never drop an accent to save width. Binding spellings: CANON §16d.
- **Untranslated sentences.** Only the portrait dedication and the plaque appear in French on screen (CANON §16d), each followed by a translation box. Théo's letters and every other French document display in English.
- **Swearing** (T rating, CANON §16e): *sacrebleu*, *parbleu*, *diable*, "damn". Nothing stronger.

### 7.2 Korean

- **Form.** Hangul, then Revised Romanization in italics, glossed on first use in each scene: 괜찮아 (*gwaenchana*, "it's okay") (CANON §16c). Glosses in 1833 obey §8.1: in 1833–34 scenes the same word is glossed "it's all right" (§1.3), and "it's okay" belongs to Seoul. Personal names keep their bearers' spellings.
- **Budget in 1833.** About one Korean word per 20 boxes, in private moments only. Min-jun slips into Korean (1) alone at night; (2) counting to steady himself in private (하나, 둘, 셋 *hana, dul, set*), first alone in the CH-01 galleries; in 1833–34 battles he counts in English (§5.1); (3) in shock, one word (안 돼 *an dwae*, "no"); (4) with Lucile late in the game: 별 (*byeol*, "star") on the Night of Stars, written on the title page of 별의 음악; (5) in the CH-17 recorded goodbye, full sentences shown in English under `[in Korean]`. Korean costs no Secrecy (he is openly from Corée); English before Onlookers does (+5, CANON §5f).
- **Seoul.** Korean is the default tongue; Korean words appear naturally (오빠 *oppa*, 교수님 *gyosunim*, 엄마 *eomma*, 동지 *Dongji*, 팥죽 *patjuk*).
- **Registers** (flag each with `{TN:}`): Seo-yeon → Min-jun: banmal, 오빠. Jae-won ↔ Min-jun: banmal, 민준아. Min-jun → Prof. Yoon: polite, 교수님. Min-jun → his parents: banmal, 엄마 and 아빠. Det. Oh → Min-jun: 강민준 씨 (*Kang Min-jun-ssi*). Koreans → Lucile: 뤼실 씨. **Her name in hangul is 뤼실 오브레** (French *u* transcribed 위, per the standard rules); her first written word is 별 (LAW-24).
- **Romanization only.** Address forms fused to a name (*Lucile-ssi*, *Min-jun-a*) and janggu syllables (*deong, gi-deok, kung*) appear in romanization alone, after the scene's first glossed use of the form.
- **Subset.** Hangul in the English master draws on the ≤ 400-syllable subset; prefer syllables already used and check new ones against art_and_ui's list.
- **Never** accented English for Korean characters, mock-Asian dialect, or K-drama, K-pop or martial-arts jokes about him (CANON §16c).

### 7.3 Lucile's point of view in Seoul (CH-E1)

Korean addressed to her shows as untranslated hangul (no romanization, no gloss) until Min-jun translates; their own exchanges carry `[in French]` (CANON §16c).

```
[N:Shopkeeper] [K]어서 오세요! 뭐 찾으세요?[/K]
LUCILE   [P:PC-02:surprised] [in French] Min-jun. What did she say?
MIN-JUN  [P:PC-01:smile] [in French] "Welcome. What are you looking for?" Same as Corbel, nicer.
```

### 7.4 Language tags

`[in German]` and `[in French]` are the canon's (CANON §16a). `[in English]`, `[in Korean]`, `[in Polish]`, `[in Latin]` and `[in Hebrew]` are a Canon Change Request (final section): until it is adopted they draw no badge, and the line names its language itself ("In English, then: …"). Each adopted tag draws a three-letter badge straddling the box's top border at the right (GER, FRE, ENG, KOR, POL, LAT, HEB; art_and_ui §8.3–§8.4); the text is always the English rendering. The scene's default tongue is never tagged. Uses: `[in English]` for Min-jun and Vane in private (a slip before Onlookers); `[in German]` for Rhine natives, with Liszt, Mendelssohn or Clara interpreting; `[in Polish]` when Chopin is moved; `[in Latin]` in church; `[in Hebrew]` for Alkan's psalter.

### 7.5 Lucile's speech

Her voice is in §4.1. Three further rules. **Naming:** only Sand calls her *ma petite Lumière*; Min-jun never calls her "Lumière", because it is the code name on Vane's file (KEY-18), and the word stings when the reports surface in CH-09. In the epilogues she names her own manner: "my own light". **Truth:** she may dodge or lie about where she goes and whom she sees until CH-09; every sentence about what she feels is true. **Wit as weather:** her jokes vanish at the reveal (CH-09) and return one at a time through the Mending scenes; the first joke she makes at Nohant is a writing beat in itself.

### 7.6 Voicing the romance

- **Subtext over statement.** Witty first, tender second, never purple (CANON §16f). Most romantic beats play on `neutral`; the line does the work. `tender` ≤ 3 per scene.
- **"Love" is a budgeted word.** Between them it is spoken only in the Nohant answer "I loved the woman who painted rain" (LAW-23 W3), once on the Night of Stars, and freely in the epilogues. The Question's lines never use it (LAW-23).
- **Staging** (CANON §16f): sprites face each other; the hand-hold animation (`{HOLD:PC-01,PC-02}`); a kiss is `{LEAN:PC-01,PC-02}` with the text box closed and no portraits, then `{FADE:out:black:60}` with `sparkle` over `[MUS:LM-22]`. Two kisses in the main game: the CH-08 roof and the CH-14 Night of Stars. Maximum intimacy is a kiss or an embrace; wit may tease, never about bodies. Rating ESRB T / PEGI 12.
- **Craft, by example.** Not: "Lucile, you are the brightest light in all of Paris, and my heart burns for you." Instead: LUCILE "You have rosin on your cuff." / MIN-JUN "You have Prussian blue on your nose." / `{LEAN:PC-01,PC-02}`.
- **The betrayal.** At the reveal she speaks in plain sentences with no jokes and no excuses, and owns all of it, including that she stopped after the concert (CANON §8d). Min-jun may be angry, never cruel: no insult to her honour or her class, no "I never cared", no slur. Never write her as evil all along, and never punish the player for forgiving fast or slow (both feed only the Horizon).
- **Never a prize.** No line or menu says "win her", "make her come" or "she's mine"; choice labels are feelings, not instructions (LAW-23). In the Paris branch he stays because she asks (LAW-25) and she proposes; in Seoul there is a promise at the Bosingak bell and no proposal.

### 7.7 The Question (CH-17)

The A-3 climax carries the strictest rules in the script. act4_and_epilogue.md writes the scene and epilogues.md its branches, both inside these rules (LAW-23–LAW-25).

| Rule | Value |
|---|---|
| Timing | Fires automatically at 1:30 on the Window Clock (CANON §11i), after the Pact of the Door. The clock pauses in dialogue and runs again only during the Paris threshold walk |
| The ask | Min-jun's line is canon, verbatim and unchosen: "Will you come with me?" |
| Final words | `[Q:Beside me, there.\|Whatever you choose.\|Who you become here.]` (LAW-23.3 labels). No candle glyph, value, hint or timer; all three written with equal warmth, all three on `tender`. Each branch writes its `ch17_fw_*` flag and speaks its full line verbatim: "I want you beside me — there." / "Whatever you choose, I'm yours." / "I want to see who you become here." There is no `[HZ]` tag: the engine scores the flag (+5 / 0 / −5) |
| The answer | Computed, never picked (LAW-23.4). The engine sets `g_branch_seoul` or `g_branch_paris` the moment the label is chosen, and the scene branches on those flags. Her refusal is verbatim: "I can't leave them. And I won't be the reason you never see your mother again. Go home." With the gate unmet, her first words are "I will not leave Théo with nothing." (LAW-25). The canon fixes no YES line: the template's is a format example, and act4_and_epilogue.md's final line must say yes plainly, name Théo's safety and want the century of light (LAW-23.7) |
| NO: the threshold | Control returns; the player can walk forward or stand still, nothing else, and no input sends him through (LAW-25). On the threshold tile he says "Then ask me. Not for them. For you.", paced with `[D:]` beats; a silence; "Stay."; "I'm staying." If the player gives no forward input for 1,200 frames (20 s) during the walk, she speaks first: "Stay. Please." He stays because she asks (CANON §16f) |
| YES: the step | Hand in hand (`{HOLD:PC-01,PC-02}`) over `[MUS:LM-30]`. No text box opens after her answer until they are through (16:52 KST) |
| Words | "Love" is never spoken in the Question (§7.6). No joke after the menu opens; no `laugh` |

```
SCENE    SCN-CH17-10 "The Question"
LOC      LOC-P30 The Heart Chamber (the Window)
CH       CH-17 · Sun 22 Dec 1833 · 08:01, Window Clock 1:30
MUSIC    LM-30
LIGHT    Dawn
TRIGGER  Window Clock reaches 1:30; auto-start; once
CAST     PC-01 · PC-02
REQUIRES —
SETS     ch17_fw_beside | ch17_fw_whatever | ch17_fw_become
STATE    see footer

{CAM:PAN:PC-02:60}   // the friends keep playing at the Engine; snow falls upward through the Window
{FACE:PC-01:R} {FACE:PC-02:L}
MIN-JUN  [P:PC-01:tender] Will you come with me?
{EMOTE:PC-02:...} {WAIT:40}
MIN-JUN  [P:PC-01:neutral] …[Q:Beside me, there.|Whatever you choose.|Who you become here.]
  #1 Beside me, there.
     MIN-JUN [P:PC-01:tender] [FLAG:ch17_fw_beside] I want you beside me — there.
  #2 Whatever you choose.
     MIN-JUN [P:PC-01:tender] [FLAG:ch17_fw_whatever] Whatever you choose, I'm yours.
  #3 Who you become here.
     MIN-JUN [P:PC-01:tender] [FLAG:ch17_fw_become] I want to see who you become here.
  #END
{WAIT:60}            // the engine has set g_branch_seoul or g_branch_paris (LAW-23.4)
[IF:g_branch_seoul]
LUCILE   [P:PC-02:tender] Théo has his trade. Louise has Théo.[PB]Yes. Show me where the light goes next.
{HOLD:PC-01,PC-02} [MUS:LM-30]
{WALK:PC-01:U4} {WALK:PC-02:U4}   // through the Window together
{FADE:out:white:120}
[/IF]
[IF:g_branch_paris]
[IF:gate_unmet]
LUCILE   [P:PC-02:sad] I will not leave Théo with nothing.[PB]And I won't be the reason you never see your mother again.[PB]Go home.
[/IF]
[IF:gate_met]
LUCILE   [P:PC-02:tender] I can't leave them.[PB]And I won't be the reason you never see your mother again.[PB]Go home.
[/IF]
// control returns: walk forward or stand still; the Window Clock runs
// SCN-CH17-11, on the threshold tile:
MIN-JUN  [P:PC-01:tender] Then ask me.[D:40] Not for them.[D:40] For you.
{WAIT:120}           // silence; only the oscillators hold the chord
LUCILE   [P:PC-02:tender] Stay.
MIN-JUN  [P:PC-01:smile] I'm staying.
// SCN-CH17-12 replaces SCN-CH17-11 after 1,200 frames without forward input:
//   LUCILE  [P:PC-02:tender] Stay. Please.
//   MIN-JUN [P:PC-01:smile] I'm staying.
[/IF]

STATE  FLAGS ch17_fw_beside | ch17_fw_whatever | ch17_fw_become (one per run)
       ENGINE g_branch_seoul | g_branch_paris: YES if gate_met and Horizon + final ≥ +1 (LAW-23.4)
```

**Voicing the Seoul branch (CH-E1).** Lucile keeps her 1830s French in every line, tagged `[in French]` with Min-jun (§7.3). Her English rendering never borrows a 2026 idiom, so the comedy is the century meeting her, never her imitating it: "this city keeps lightning in glass" (LAW-24), never "electric light". The translation app is a running gag with a fixed shape: its French is modern and over-familiar, and she answers in perfect 1833 French (`[N:Translate] [in French] Hi! What's new?` → `LUCILE [P:PC-02:laugh] [in French] Everything, little box. And your French belongs in a stable.`). Her Hanmadi words enter her barks (§5.3) and, at most once per scene, her field lines, always with pride and never as baby talk. Min-jun changes most: Korean is his default again, contemporary and quick with his family and Jae-won, careful with Det. Oh, and modern idiom is his once more. He translates for her faithfully; when he chooses not to translate, it is to spare her, never to mock. The Keeper's Choice voice-over is in his own name and voice, ≤ 6 boxes (LAW-24).

**Voicing the Paris branch (CH-E2).** Min-jun has stayed, and his speech settles into the period for good: there are no slips left to tag (Secrecy is retired, CANON §11e), and English returns only for a private word with Vane before Vane sails in March. A greyed Repertoire entry says only "Not mine to play." *(canon)*, and no character comments on it. He knows when his friends will die and never says so (LAW-18). When Chopin coughs (an SFX, never a portrait), Min-jun answers with an act of care, a scarf or a closed window, and `{EMOTE:PC-01:...}`, never a warning or a look held for effect; when a friend asks about the future, he answers about the music, never about dates. Lucile's wit returns at full strength, aimed at the jury and at Delorme's Erasure; she proposes (§7.6) and signs "L. Aubray".

---

## 8. Banned Phrases, Narrator Anachronisms, Localisation

### 8.1 Forbidden in 1833–34 speech, captions and documents (CANON §16g)

"OK", "cool", "awesome", "teenager", "weekend", "boss" (slang), "photograph" / "photo", "telegram", "microbe" / "germ theory" (Marthe's one scripted slip excepted), "scientist" (say *savant*), "Impressionism" / "Impressionist" (Min-jun only; others find it odd; the party says *la manière lumineuse*), "jazz" (Min-jun and Julien, in private), "Haussmann", "métro", "Eiffel Tower", "Belle Époque", "Germany" / "Italy" as states, "kilometres per hour", "electric light", anything about the electric telegraph. *Télégraphe* for the Chappe semaphore is allowed. Monet, Pissarro, van Gogh, Seurat, Signac, Cézanne, Renoir, Degas, Manet, Debussy, Ravel, Rachmaninoff, Scriabin and Prokofiev are named only in Min-jun's private speech or by the cabal in private; in public each name is a tagged `[SEC:]` slip and an NPC must react. These words are also the raw material of Min-jun's slips: when he says one, tag it.

### 8.2 House bans (this guide)

| Category | Banned | Use instead |
|---|---|---|
| Modern idiom (1833–34 only; Seoul speech is contemporary) | hi, hello, guys, folks, kid(s), "fan" (an admirer), "deadline", "feedback" | good day, good evening, my friends, children, admirer, by Thursday, your opinion |
| Therapy-speak (1833–34; in Seoul never the resolution of a scene) (CANON §16b) | stress(ed), trauma, process (feelings), closure, boundaries, toxic, mindset, "I hear you" | the plain feeling: afraid, grieving, angry, tired |
| Game words in dialogue | HP, MP, party (meaning the group), spell (meaning magic), level (meaning experience), magic, save point, boss | Jae-won's one gamer line per scene in Seoul only; everyone else says strength, breath, the friends, the glowing stands |
| Narration | "Meanwhile", "Later", "Elsewhere", "Little did he know", "Three days later", a caption with a sentence in it | Place and date only; cut, don't explain (CANON §1 Tone Rule 6) |
| Dates | "12/18/1833", "the 18th of December, 1833" | December 1833; "Wednesday 18 December 1833" for canon-dated set pieces |
| Sensitivity | any slur, from anyone, villains included; "Oriental" except in an ignorant NPC's mouth, answered; antisemitic or financier tropes (CANON §16e); jokes about Harriet's leg, the Sergent's leg, Théo's chest or Chopin's cough; cholera as a creature or a status name | Show ignorance as ignorance; show illness through absence and care |

Almanach entries, item descriptions and in-world documents are written in period voice (CANON §16h): "A tisane of lime blossom, as Mère Gaudin brews it. Restores 150 HP." The number is the only modern thing in the line.

### 8.3 Localisation (master script in English; French and Korean planned, CANON §1)

| Topic | Rule |
|---|---|
| Headroom | French runs 15–25% longer. English targets: portrait boxes ≤ 60 characters (cap 72: 3 wrapped lines of 24; a line left above 60 is marked *(at cap: French build trims)*), no-portrait boxes ≤ 96 (cap 4 × 30), barks ≤ 24 where possible (cap 30; the French build adapts barks rather than translating them), choice labels ≤ 18 (cap 22), name tabs ≤ 12 (cap 15) |
| French overflow | Moves to the 4-line no-portrait box for that box only (CANON §1); the name tab stays |
| Korean | Ships its own full font and box metrics; the 2-character rule applies only to hangul inside the English master |
| Line breaks | None in source text; the engine wraps. French build: non-breaking thin space before ! ? : ; and inside « » (one character). Korean wraps at spaces (eojeol), never inside a word. No hyphenation in any language |
| Variables | String tables carry gender (LU, FA, SY and guests GST-02 Sand, GST-04 Clara, GST-09 Marthe female) for French agreement and a final-consonant field for Korean particles (이/가, 은/는, 을/를: 민준이, 뤼실이) |
| Wordplay | Flag every pun with `{TN:}`: "Meister Morgen" (keep the German in every build and gloss morning/tomorrow), Lélio's "return to life", *rubato* as "robbed", "Impression-ism" as a printer's proof |
| Names and titles | Never translated. Works keep their original titles in italics (*Gaspard de la nuit*); the Korean build may add a hangul transliteration in the Almanach only |
| Tu and vous (French build) | *Tu* switches at the same beat as first names (CANON §16c): Berlioz CH-04; Lucile CH-08, back to *vous* while `g_fractured`, *tu* again from Mending 2; the others after CH-09. Archon always says *vous*; Sand always says *tu* to Lucile |

---

## Canon Additions & Cross-Doc Notes

**Canon Change Requests** (for the Lead Designer; until adopted, the stated fallback applies):

- **CCR: Scene-ID family `SCN-<code>-##`** (§2.1), e.g. `SCN-CH04-07`, `SCN-SQ07-05`. Why: every scenario and quest doc, the audio cue sheets and QA need one stable key per scene; CANON §0c has none. Each owning doc numbers its own scenes. Touches: the four act docs, epilogues.md, side_and_bond_quests.md, audio_and_music.md. Fallback: none needed; the format adds an ID family without changing any existing one.
- **CCR: Tier A extras for the ten Tier A characters CANON §16a leaves without one** (§3.3): Delacroix `appraising`, Farrenc `sceptical`, Seo-yeon `scowl`, Jae-won `pumped`, Julien `sheepish`, Vane `smirk`, Delorme `contempt`, Brücke `calculating`, Marthe `serene`, Théo `brave`. Why: CANON §16h promises Tier A "plus extras"; only seven are listed. Fallbacks as given in §3.3. Touches: art_and_ui (portrait budget), every writing doc.
- **CCR: Promote FIC-10 Kang Do-hyun and FIC-11 Park Hye-jin to Tier B** (bespoke `gruff` and `tearful`). Why: they carry the CH-E1 reunion, but CANON §16h leaves them Tier C (no portrait). Fallback: `[N:Father]` / `[N:Mother]` with 4 × 30 boxes. Touches: art_and_ui, epilogues.md.
- **CCR: Brücke's name tab switches to "Brücke" at Archon's Revelation (CH-12)**, alongside "Archon" and "Delorme" (§3.3). Why: CANON §16h gives the sequence but not the moment. Touches: art_and_ui, act3.md.
- **CCR: language-tag instances `[in English]`, `[in Korean]`, `[in Polish]`, `[in Latin]`, `[in Hebrew]`**, each drawn as a three-letter badge (ENG, KOR, POL, LAT, HEB) like the canon's GER and FRE (art_and_ui §8.3/§8.4; this guide §7.4). Why: CANON §16a defines only `[in German]` and `[in French]`, but Vane's private English, Min-jun's CH-17 recorded goodbye, Chopin's Polish, church Latin and Alkan's psalter all need one. Fallback until adopted: no badge, and the language is named in the line itself. Touches: art_and_ui, every writing doc.

**New shared conventions and facts defined here** (owned by this guide under CANON §0b; other docs must follow them):

- **Script notation** (§2): the ten-field scene header; `{…}` stage directions (never state-changing), `//` comments, `{TN:}` translator notes; `#1 / #2 / #END` branches (the build also accepts `→n` until secrecy_and_trust converts); nested `[IF:]` blocks; the end-of-scene `STATE` footer, which lists every `[CONF]`. Touches: all scenario and quest docs, secrecy_and_trust.md (audits footers).
- **Emote set and animations** (§2.4): `!` `?` `...` `note` `sweat` `vein` `idea` (a candle, never a light bulb) `zzz` `tear` `sparkle`, reserved for the two kisses, the Window, the CH-E2 proposal at dawn and the Bosingak promise; no heart emote. `{ANIM:}` names that art_and_ui must supply: `fallboard_tap`, `play_piano`, `paint`, `conduct`, `whittle`, `mimic`, `cigar`; plus `{LEAN:}` and `{HOLD:}` (art_and_ui's romance-pair lean and hand-hold walk). Touches: art_and_ui.
- **Flags** (§2.3): naming scopes `chNN_`, `sqNN_`, `bqpcNN_`, `g_`. Engine-maintained, read-only: `rN_pcNN`, `party_pcNN`, `sec_t1`–`sec_t5`, `sec_low`/`sec_mid`/`sec_high`, `spot_t1`–`spot_t4`, `hz_band_1`–`hz_band_5`, `gate_met`/`gate_unmet`, `g_fractured`, `g_julien_recruited`, `g_duel_thalberg_won`, `g_branch_seoul`/`g_branch_paris`, `g_atelier_restored`, plus a `not_` twin for every flag. Written once by `[FLAG:]`: `confidant_pc02`–`confidant_pc08`, `early_truth`, the eight `byt_*` flags, `ch17_fw_beside`/`_whatever`/`_become`. Systems flags inherited from secrecy_and_trust are exempt from the scope-prefix rule. Chapter flags used in this guide's samples (`ch06_l1_done`, `ch09_banns` and so on) are illustrative; owning docs may rename them. Touches: engine/tools, all scenario and quest docs, secrecy_and_trust.md.
- **`g_atelier_restored`** (new engine flag): true once LOC-E02 is restored, by SQ-12 or by the CH-E2 restoration task (CANON §12). Touches: engine/tools, epilogues.md, overworld_and_towns.md (E02 states), side_and_bond_quests.md.
- **Usage rules inside canon tags** (§1.1–§1.2): `[W]` mid-box only; `[D:n]` at box end = auto-advance; Config Auto-advance timings (90 + 2 per character; 60 after a mid-box `[W]`; never on `[Q:]` or `[SLIP]`); `[C:gold]` / `[C:grey]`, one highlight colour per box; Confided-line and Horizon choices never show a glyph, value or hint; `[MUS:fade:n]`, `[MUS:silence]`, `[MUS:MUS-###]` for fixed tracks; `[SLIP]` option order (modern first) with the cursor on the period phrasing; `*…*` for italics; text speeds 1–5 = 4 / 3 / 2 / 1 frames per character or instant. Touches: art_and_ui (italic bank, Config), secrecy_and_trust.md (Slip default).
- **Time on screen** (§7.1): spoken time in words; clock digits only in canon HUDs (the Window Clock, BOSS-27's countdown), never in captions or boxes; only Archon and Brücke speak exact minutes, in words, in private or in CH-16. Touches: all scenario docs, art_and_ui.
- **"Corean"** (§7.1): *Corée* and "Corean" in 1833–34 speech; "Korean" only in Seoul and in Min-jun's private speech; "Monsieur Corée" is Mère Gaudin's (and Théo's) accepted nickname. Touches: every writing doc.
- **System message strings** (§1.4) and **caption presentation** (centred, unboxed, 120 frames). Touches: art_and_ui, items_and_equipment.md, skills_and_progression.md.
- **Name tabs** (§3.3–§3.4), notably PC-08 "Farrenc" with NPC-20 "A. Farrenc", NPC-19 "Miss Smithson", NPC-06 "Herr Wieck", NPC-24 "Prefect Gisquet", NPC-27 "Count Apponyi", NPC-28 "Thérèse Apponyi"; portrait ID ANA-03 for Julien until SQ-21, PC-11 after. Touches: art_and_ui, historical_cast.md, all scenario docs.
- **Tier B bespoke expressions** for all 43 Tier B characters (§3.4). Touches: art_and_ui, historical_cast.md.
- **Bark system** (§5.1): message-strip display, ≤ 30 characters, 60-frame auto-advance without ATB pause, frequencies, priority, 6-second cooldown, silent battles (BOSS-16 at least), chapter gates; **Synergy lead voices** and **Octave Voice lines** (§5.2). Touches: combat_ensemble.md, bosses.md (silent flags), art_and_ui.
- **Lucile's Seoul pool** (§5.3): 40 barks with one swap slot each (15 Seoul forms of her trigger barks, 25 Seoul-only Start and Victory barks); each of the 40 Hanmadi words owns one fixed slot; swapped words show hangul only, with romanization and gloss in the phone's Translate log. Touches: epilogues.md (Hanmadi staging), overworld_and_towns.md (the word list, §8.2), art_and_ui (Translate log, Hanmadi reserve), combat_ensemble.md (bark draws).
- **Korean gloss dependencies for barks** (§5.1, §7.2): prologue_and_act1.md must let Min-jun count 하나, 둘, 셋 aloud, alone and glossed, in the CH-01 galleries, the gloss his CH-E1 low-HP bark relies on (in 1833–34 battles the count is in English); epilogues.md must have Jae-won gloss 얼쑤 and 좋다 when he joins and must gloss 오빠 and 엄마 at the reunion.
- **Lucile's hangul name 뤼실 오브레** (§7.2). Touches: epilogues.md, art_and_ui (hangul subset: 뤼, 실, 오, 브, 레), Korean localisation.
- **Romance and address rules** (§4.1, §7.5–§7.7): Lucile calls him "Kang" (French *vous*) while `g_fractured` and "Min-jun" again from Mending 2; Min-jun never calls her "Lumière"; she calls Sand "Aurore" in private; "love" is spoken between them only at Nohant (W3), once on the Night of Stars, and freely in the epilogues; at a kiss the text box closes; the Question's timing, menu, verbatim lines and threshold rules (§7.7). Touches: party.md, historical_cast.md, act2.md, act3.md, act4_and_epilogue.md, epilogues.md.
- **Chatter hooks** (§6.2) other docs may pick up: a Paris baron buys two hundred Liège gun barrels (CH-11; Archon's arms trade, R-28; flavour only); the Strasbourg postmaster holds Sand's letter (CANON §4b); floating baths by the Pont Neuf (P32); the Deoksugung stone-wall-road legend (S03), which Lucile's Seoul bark row 22 answers. Touches: overworld_and_towns.md, act3.md, epilogues.md.
- **No real quotations** (§4 shared rules), with the five named sayings writers must not use. Touches: every writing doc; historical_notes_and_liberties.md may cite the rule.

**Cross-doc notes** (each names the doc that must change):

- **secrecy_and_trust §5.2.4, §6.1, §6.4 and overworld_and_towns' inline lines** must convert to this guide's notation: `#n`/`#END`, unwrapped text, SPEAKER labels, `…` as one glyph, no box-final `[W]`. Until they do, the build accepts `→n`, ignores a box-final `[W]` and strips hard line breaks with a lint warning (§2.3).
- **audio_and_music §8** owns the final `[SFX:]` vocabulary and keeps this guide's starter set, marked † (§2.5); nothing here overrides it.
- **art_and_ui §4.8:** `sparkle` also plays at the CH-E2 proposal and the Bosingak promise (its working draft's §5.5 already says so).
- **art_and_ui §4.7:** NPC-08's bespoke is `chuckle`, not `laugh`. historical_cast's NPC-08 header and its second sample tag also read `laugh` and should change.
- **art_and_ui §8.4:** a top-anchored box at screen (8, 8) puts the name tab at screen y −6, off the screen. Proposal (§1.3): when the box is top-anchored, the tab hangs from its bottom-left edge.
- **art_and_ui §8.4:** its mockups quote two old example lines. §2.7's "Father would have called this laziness. What would you call it?" now reads "Father would have called this lazy. What do you call it?", and §1.3's ragpicker now ends "Their rags still find me." (both trimmed to the §8.3 targets).
- **art_and_ui §8.3:** 끝 is no longer a style-guide sample word (the Hanmadi example now uses 동전, from overworld_and_towns §8.2's list); its core-subset slot may be reassigned if no other doc uses it.
- **overworld_and_towns §2** opens only P02 and P28 in CH-12. This guide's Act III sets for P22 and P32 (§6.2) assume both maps can be entered in CH-12, as SQ-13 opens on the quays in that chapter (CANON §4d). If overworld keeps them shut, cut those two sets rather than moving them.
- **historical_cast** owns every NPC voice; §4.3–§4.4 summarise it and must follow any correction it makes. The six figures promoted to full entries here (Belgiojoso, d'Agoult, Smithson, Gisquet, Aristide Farrenc, Herz) add tics, topics and "never" rules, not new facts.
- **historical_notes_and_liberties** should verify: Belgiojoso's painting for income in Paris, 1831–32 (§4.3, her sample 1); Chopin's E-minor Concerto, Op. 11, published 1833 and dedicated to Kalkbrenner (§4.1, §4.4); the law of 10 April 1831 on *attroupements* (§6.2, the Marais guardsman); the Strasbourg astronomical clock stopped since about 1788 (§6.2, R10); the 6½-octave, 78-key compass of Pleyel grands in 1833 (§4.1, §5.2, Alkan).
