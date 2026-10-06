# Dialogue & Script Style Guide

Status: v1.0 — 2026-10-06 · Owns: script formatting conventions, scene-header and stage-direction notation, portrait expression tags and name tabs, character voice guides and voice samples, battle barks, NPC chatter rules, language usage (English master, French, Korean), banned phrases, localisation rules for text · Depends on: secrecy_and_trust (per-event values, Horizon bands), art_and_ui (font, portraits), audio_and_music (SFX names) · Canon: docs/00_CANON.md

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

### 1.1 Additions to the canon box spec

The box, portrait, glyph, hangul, name-tab, caption and box-count limits are CANON §16a and §16h and are not restated here. This guide adds four rules:

| Property | Rule |
|---|---|
| Advance cursor | A blinking ▼ at the box's bottom right while it waits for a button; absent on an auto-advance box (`[D:n]` at box end, §1.2) |
| Font banks | Roman and italic banks of the canon variable-width font (art_and_ui F1). Italic is the only emphasis the font has: no bold, no underline |
| Print speed | Config text speed 1–5 (CANON §11j) prints one character every 4 / 3 / 2 / 1 frames, or the whole box at once; 3 is the default. `[D:n]` delays are absolute and ignore text speed |
| Emphasis | `*word*` sets italics: foreign words (§7), titles of works, and stress (at most one stressed word per box). Never shout in capitals: a shout is `!` plus `{SHAKE:box}` (§2.4). Capitals are reserved for command names in tutorials (RECITAL, PLEIN AIR) and printed signage |

### 1.2 Tag syntax (canon tags; the full and only set)

| Tag | Rule of use |
|---|---|
| `[P:ID:expr]` | First thing in a box. IDs are character IDs (PC, NPC, FIC, ANA), never GST. Julien is `ANA-03` until SQ-21, `PC-11` after (same art) |
| `[N:Name]` | Name-tab override: Tier C speakers, unknown speakers (`[N:???]`), documents (`[N:Le Corsaire]`) |
| `[W]` | Every box waits for a button at its end without being told to (the implicit `[W]`). Write `[W]` explicitly only **mid-box**, for an FF6 beat where the text resumes in the same box |
| `[PB]` | Same speaker, fresh box; each `[PB]` counts toward the 6-box limit |
| `[D:n]` | n frames (60 = 1 s). Mid-box: a timed pause in printing. **A box whose last code is `[D:n]` suppresses the implicit `[W]` and auto-advances after n frames** (cutscene sync, the Window Clock, battle text, field barks) |
| `[C:gold]…[/C]` | `gold`: key terms, items and places that open an Almanach entry, first mention per chapter. `grey`: muttered asides and whispers |
| `[SFX:name]` | Fires at its print position; names from §2.5 until audio_and_music publishes its list |
| `[MUS:…]` | `[MUS:LM-22]` (the leitmotif's main track), `[MUS:fade:90]`, `[MUS:silence]`; fixed canon tracks may be cited as `[MUS:MUS-095]` |
| `[K]…[/K]` | Hangul run, drawn from the ≤ 400-syllable subset (CANON §16c) |
| `[Q:a\|b]` | **2–3 options**, each ≤ 22 characters; the full line is spoken after selection; no cancel. An option that costs Secrecy shows the candle glyph and "+n" after its label (secrecy_and_trust §6.1) |
| `[SLIP:3]…[/SLIP]` | Wraps a `[Q:]`. Option 1 is the modern phrasing (candle glyph and "+n"), option 2 the period phrasing; the cursor starts on option 2; a timer bar drains for 3 s and on timeout the period phrasing plays (secrecy_and_trust §2.4.3) |
| `[in German]`, `[in French]` and kin | First thing after the portrait; see §7.4 |
| State tags | `[BP:PC-07:+15]` `[SEC:+5]` `[HZ:W3]` `[CONF:CH05-03]` `[OV:+1]` `[SHD:+1]` `[REN:+n]` `[GOLD:+n]` `[GET:KEY-16]` `[FLAG:name]` `[IF:name]…[/IF]` `[EVE:-1]` `[LIGHT:Dawn]`. **Never invent others.** HZ, CONF and SHD are never shown to the player. HZ always cites a LAW-23 row, never a number |

**Punctuation.** The ellipsis is one glyph (…), never three dots; an interrupted line ends in an em dash (—). Speech carries no quotation marks (the name tab says who speaks); quotations inside speech use curly double quotes; « guillemets » appear only in French documents shown in French (§7.1).

### 1.3 Rendered examples

*Schematic drawings: every box is drawn 40 columns wide; real widths are pixels (CANON §16a). Hangul counts double.*

Raw line: `LUCILE [P:PC-02:smile] You came. I bet Théo two sous you'd sleep through it.`

```
   ┌────────┐
   │ Lucile │
┌──┴────────┴──────────────────────────┐
│ ┌────────┐ You came. I bet Théo two  │
│ │PC-02   │ sous you'd sleep through  │
│ │smile   │ it.                       │
│ └────────┘                          ▼│
└──────────────────────────────────────┘
```

Raw line: `[N:Ragpicker] Rags, bones, bottles! Half this street went in the spring of '32. Their rags still find their way to me.`

```
   ┌───────────┐
   │ Ragpicker │
┌──┴───────────┴───────────────────────┐
│ Rags, bones, bottles! Half           │
│ this street went in the spring       │
│ of '32. Their rags still find        │
│ their way to me.                    ▼│
└──────────────────────────────────────┘
```

Raw line (괜찮아 = 6 characters): `MIN-JUN [P:PC-01:homesick] [K]괜찮아[/K] (*gwaenchana*, "it's okay"). Seo-yeon always said it first.`

```
   ┌─────────┐
   │ Min-jun │
┌──┴─────────┴─────────────────────────┐
│ ┌────────┐ 괜찮아 (gwaenchana,       │
│ │PC-01   │ "it's okay"). Seo-yeon    │
│ │homesick│ always said it first.     │
│ └────────┘                          ▼│
└──────────────────────────────────────┘
```

**Mid-box pause and auto-advance.** Raw line: `ARCHON [P:ANA-01:cold] 00:43.[D:40] Listen, Monsieur Kang.[D:90]`

```
   ┌────────┐
   │ Archon │
┌──┴────────┴──────────────────────────┐
│ ┌────────┐ 00:43. Listen, Monsieur   │
│ │ANA-01  │ Kang.                     │
│ │cold    │                           │
│ └────────┘                           │
└──────────────────────────────────────┘
```

Printing stops for 40 frames after "00:43.", so the number lands before the courtesy; then "Listen, Monsieur Kang." prints at text speed. The closing `[D:90]` replaces the implicit `[W]`: no ▼ appears, the box holds 90 frames after "Kang." and closes by itself, so the cutscene (or the Window Clock) keeps its sync.

**Choice window with a Secrecy cost and a Bite Your Tongue timer** (`[SLIP:3][Q:Impressionism.|It has no name yet.][/SLIP]`, from §2.7). The window sits above the box, right-aligned, with the hand cursor already on the period option; `[candle]` is the 8-px candle glyph. The 3-second timer bar drains along the box's bottom edge (art_and_ui); on timeout the period phrasing plays.

```
         ┌─────────────────────────────┐
         │  Impressionism.  [candle]+5 │
         │☞ It has no name yet.        │
         └─────────────────────────────┘
   ┌────────┐
   │ Lucile │
┌──┴────────┴──────────────────────────┐
│ ┌────────┐ Father would have called  │
│ │PC-02   │ this laziness. What       │
│ │laugh   │ would you call it?        │
│ └────────┘                           │
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

Every scene opens with this header (all fields mandatory; write "—" when a field is empty). The header is for writers, audio and QA only: its clock time never reaches the screen (§7.1).

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
STATE    (repeated in the footer)
```

### 2.2 Dialogue lines

`SPEAKER  [P:ID:expr] Text.` — one line of script is one box. The SPEAKER label (capitals) is for writers and QA only; the name tab comes from the portrait ID. Write the text unwrapped: the engine wraps at word boundaries, and hard line breaks are forbidden (they break localisation). Muttered asides go in parentheses and grey: `[C:grey](Forty years early. Idiot.)[/C]`. There are no thought bubbles.

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

`#n` and `#END` are the binding branch notation for every writing doc (CANON §0b gives text format to this guide); the build strips them. Branches rejoin at `#END`. Conditions use `[IF:flag]…[/IF]` only. There is no else-tag: for "if not", the engine exposes a read-only twin `not_<flag>` for every flag.

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

Engine flags are never written by hand. A flag whose writer is `[FLAG:]` is written exactly once, in the event named, and is read-only everywhere else.

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
| `{FADE:out\|in:black\|white:n}` · `{FLASH:white:n}` · `{TINT:sepia}` / `{TINT:off}` | Fades; flashbacks are sepia |
| `{CAM:PAN:target:n}` · `{CAM:FOLLOW:ID}` · `{CAM:LOCK}` · `{CAM:RETURN:n}` | Scroll by tiles or to an actor over n frames. No zoom outside the Mode-7 set pieces |
| `{WAIT:n}` | Event pause, no text |
| `{TN:…}` | Translator's note; stripped from the build |
| `// …` | Writer's comment |

### 2.5 SFX names (starter set; audio_and_music owns the final list)

`piano_hit` (the low cluster) · `river_lap` · `rain_loop` · `thunder` · `bell_toll` · `crowd_murmur` · `crowd_gasp` · `door_creak` · `glass_break` · `coin_clink` · `quill_scratch` · `page_turn` · `fork_ring` · `rift_hum` · `clock_tick` · `rifle_shot` · `bond_chime` (played by the engine on `[BP:]` ≥ +15).

### 2.6 State notation

Put each state tag at the start of the box that dramatises the change, so the change and its cause share a box. End every scene with a `STATE` footer listing every change by branch; secrecy_and_trust audits these footers. Values in this guide are illustrative; **secrecy_and_trust.md sets binding per-event values.**

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
LUCILE   [P:PC-02:worried] I paint what I'm given. Those letters in my copy…[D:20] I never asked.
[/IF]
{EMOTE:PC-01:...}
MIN-JUN  [P:PC-01:determined] Then don't paint what you're given. Paint what the light is doing.
LUCILE   [P:PC-02:determined] Then teach me. Properly. Where do I look?[Q:Tell of tomorrow|Ask what she sees]
  #1 Tell of tomorrow
     MIN-JUN [P:PC-01:tender] [HZ:W7] [FLAG:ch06_l1_tomorrow] Painters to come will paint this bridge at every hour of the day.
     LUCILE  [P:PC-02:surprised] Every hour? Who owns that many hours?[W] …Show me one.
  #2 Ask what she sees
     MIN-JUN [P:PC-01:tender] [HZ:R1] [FLAG:ch06_l1_mirror] What do you see in the water, here, now?
     LUCILE  [P:PC-02:surprised] Me? Nobody asks me.[W] …Violet. Under the arch. Violet.
  #END
[MUS:LM-22] {JUMP:PC-02} {ANIM:PC-02:paint}
LUCILE   [P:PC-02:laugh] [BP:PC-02:+10] Father would have called this laziness. What would you call it?[SLIP:3][Q:Impressionism.|It has no name yet.][/SLIP]
  #1 Impressionism.
     MIN-JUN [P:PC-01:neutral] [SEC:+5] [FLAG:ch06_slip_impression] Impressionism.
     {EMOTE:PC-02:?}
     LUCILE  [P:PC-02:surprised] [BP:PC-02:+5] Impression-ism? Like a printer's proof? You collect strange words.
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
LUCILE   [P:PC-02:laugh] Six o'clock. The light's going gold. Hold the parasol, and don't talk.
{CAM:PAN:U4:120}   // the sun clears the Louvre roofline
FISHERMAN [N:Fisherman] [FLAG:ch06_l1_done] Gudgeon bite at dawn, *mademoiselle*. Nobody else does, in this city.
{FADE:out:white:90} [MUS:fade:90]

STATE  HZ W7 (#1) | R1 (#2) · BP PC-02 +10, +5 (slip #1)
       SEC +5 (slip #1) · CONF CH06-01 (scripted, no choice, 0 BP; always reported, +8 Secrecy
       applied silently at chapter end, CANON §11f; the Early Truth cannot precede L1)
       FLAGS ch06_l1_done, ch06_l1_tomorrow | ch06_l1_mirror, ch06_slip_impression
```

Notes on the example: both lesson options are written with equal warmth (LAW-23 lesson rule); the slip makes the modern word the more charming answer and the costlier one (CANON §1 P3); "Seoul" is the scripted Confided line CH06-01 (secrecy_and_trust §5.2.2), the word that lets Brücke confirm the Kang of his dossier (CANON §8), so it carries no choice and no BP, and her `guilty` flickers only there, where his trust touches her errand (§3.3).

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

Each entry gives diction and length, tics, topics, what the character never says, how the voice moves across the arc, and five sample lines (each fits one 3 × 24 box).

### 4.1 The party

**PC-01 Kang Min-jun.** *Diction:* plain, clean, unslangy English for his French; in CH-01–CH-04 shorter sentences and `[D:]` word-search pauses, never broken grammar. *Tics:* credits the composer ("It's Ravel's"); undercuts a compliment with a joke; tempo, rests and cues as metaphors; taps the fallboard twice before every story performance (`{ANIM:PC-01:fallboard_tap}`); hums *Arirang* when nervous. *Topics:* home, Seo-yeon, his father's workshop, the music he cannot claim. *Never:* claims a future work in a story scene (LAW-20); a cruel word to Lucile; a friend's death date (LAW-18); modern slang in 1833 except as a tagged slip. *Arc:* "How do I get home?" becomes "Where is home?"; "It's Ravel's" becomes "This one's mine" (from CH-13); the deflecting watcher learns to answer plainly.
1. It's Ravel's. Maurice Ravel. I only borrowed it. *(CH-03)*
2. Kang is my family name. In Corée it comes first. *(canon, §16c)*
3. Three years I played this for juries. Tonight it buys us soup. *(CH-02)*
4. I used to ask how to get home. Lately I ask where it is.
5. This one's mine. Nobody wrote it before me. I checked. *(CH-13)*

**PC-02 Lucile Aubray.** *Diction:* a frame-gilder's daughter from the Left Bank: concrete nouns, trade words (Prussian blue, madder, lead white, gesso), prices in sous. *Length:* short and quick; jokes as armour; longer and softer with Théo. *Tics:* names the exact colour where others say grey; haggles; "Look." as a whole sentence; calls Sand "Aurore" in private. *Topics:* light, money, Théo, the Salon that refused her. *Never:* lies about her feelings, only about her errand (CANON §16f); calls herself "Lumière"; begs. *Arc:* bright evasion (CH-04–CH-08) → plain sentences without jokes at the reveal (CH-09) → calls him "Kang" again while `g_fractured`, "Min-jun" from Mending 2 → wit aimed at the future, and her own manner in her own words.
1. Rain has no outline. So how am I meant to paint it? *(canon, CH-04)*
2. Prussian blue, four sous the cake? Robbery. I'll take two.
3. I lied about where I went. Never about why I came back.
4. Don't look at me. Look at the water. It's violet, you blind man.
5. You asked me. They never asked anyone. *(canon, LAW-20)*

**PC-03 Hector Berlioz.** *Diction:* exclamatory and literary; Shakespeare, Goethe, Virgil. *Length:* long, piled clauses in threes, then one short line that lands. *Tics:* orchestras that grow mid-sentence; mock-tragic self-pity; "Sublime!" *Topics:* Harriet, critics, money he lacks, Rome, being misunderstood. *Never:* a small ambition; a joke about Harriet's injury; meanness to the poor. *Arc:* adores an ideal, marries a real woman; after CH-09 the short tender lines come more often; at thirty (CH-14) he jokes about age and means it.
1. Four hundred musicians! No—five! Let the floor crack!
2. Seven critics, monsieur, and fourteen ears. I counted. All deaf.
3. A madman of the right kind. I know the breed. I am its king. *(first sentence canon)*
4. I adored a Juliet. Tomorrow I marry Harriet. She is braver.
5. Go. I'll hold the door. I've held heavier things. A grudge.

**PC-04 Eugène Delacroix.** *Diction:* measured, aphoristic, a dandy's irony; exact colour words. *Length:* medium, balanced clauses; one exclamation per scene at most. *Tics:* maxims on colour and line; "monsieur" as a fencing touch; a small notebook (never "my journal", CANON §16b); the scarf at his throat. *Topics:* colour against line, Morocco, Rubens, Byron, the Algiers canvas. *Never:* shouts; gushes; discusses his health except to dismiss it. *Arc:* wit as a wall → after CH-09, "Min-jun" and plain tenderness → keeper of his memory, "our brother".
1. Monsieur Ingres draws a line around a soul. I prefer to let it out.
2. In Tangier the shadows were blue. In Paris they are merely late.
3. Ignore the scarf. My throat is a coward. The rest of me is not.
4. I keep notes on colours and on fools. You fit neither column.
5. I will not fix a face I shall never see again. *(canon, LAW-26)*

**PC-05 Charles-Valentin Alkan.** *Diction:* terse, literal, dry; Ecclesiastes and the Psalms; machines. *Length:* one sentence, often three words; his longest speeches describe mechanisms. *Tics:* answers rhetorical questions literally; exact numbers; the deadpan reversal. *Topics:* steam, gears, Scripture, his family, practice. *Never:* small talk; self-promotion; a raised voice; any post-1833 title of his own (CANON §5c). *Arc:* fear of the world → he chooses to keep rather than hide; from CH-14 he volunteers first, still in few words.
1. Seventy-eight keys. I know them all. People, fewer.
2. Ecclesiastes says nothing is new under the sun. He never met you.
3. That spring is not steel. Steel does not remember its shape. *(CH-07)*
4. I prefer the back row. The audience is quieter there. So are bullets.
5. I will keep the door. Keeping is what I am good at.

**PC-06 Frédéric Chopin.** *Diction:* polite, brief, exact; dry irony; Polish only when moved (`[in Polish]`; "Fryderyk" only in private Polish scenes). *Length:* short; understatement does the work. *Tics:* mimics other pianists (`{ANIM:PC-06:mimic}`); "Perhaps."; gloves. *Topics:* Poland, his family's letters, pupils, Pleyel's instruments, the unfinished Ballade. *Never:* illness beyond "a cold"; public declarations; anything about his death. *Arc:* the exile who cannot go home, Min-jun's mirror; after *Żal* (BQ-PC06) he teaches what he found: carry home inside the music.
1. Kalkbrenner plays like this—so. And calls it expression.
2. A crowd breathes on me. I prefer six friends and one candle.
3. Do not say Warsaw in that tone. Say it as you would a name.
4. Perhaps. I find "perhaps" ends most conversations politely.
5. Żal. Grief with a fist inside it. You have it too, I think.

**PC-07 Franz Liszt.** *Diction:* warm, theatrical, generous; grand gestures, sincere underneath. *Length:* long and flowing, ending in a direct challenge. *Tics:* "mon ami"; Paganini as the measure of all things; rivalry offered as affection. *Topics:* Paganini, Marie, God and vocation, his mother, transcription, Beethoven. *Never:* mocks a rival's poverty or birth; vulgarity about Marie; refuses a challenge. *Arc:* showman → seeker; plays second piano in a friend's concerto (CH-13); executor of the Pact.
1. Mon ami, you play as if the piano owed you money. Again!
2. I heard Paganini once. Since then I practise as other men pray.
3. Second piano? For you, yes. Tell no one. They would not believe it.
4. Marie says I perform even my silences. This one is sincere.
5. If ever there must be a door, we will see to it. *(canon, CH-14)*

**PC-08 Louise Farrenc.** *Diction:* precise, practical, ironic; facts, fees, dates. *Length:* medium; numbered points. *Tics:* corrects attributions; prices everything; "Precisely." *Topics:* counterpoint, unequal pay, old keyboard music, engraving, Victorine. *Never:* self-pity; flirtation; a quiet injustice left unnamed. *Arc:* fears erasure → learns she was forgotten and found, and fights harder (LAW-18); names Min-jun's hypocrisy over Lucile (BQ-PC08), then forgives it.
1. Seven panels, seven stones. It is not art. It is a tuning system. *(CH-08)*
2. The second flute is paid more than any woman who writes for him.
3. You call it a gift. Did she ask for it? Answer the question.
4. Victorine, scales, twice. Then you may hear about the balloon.
5. Forgotten, then found. Good. I shall make them work for the finding.

**PC-09 Kang Seo-yeon.** *Diction:* contemporary Seoul speech, banmal with her brother, whom she calls 오빠 (*oppa*). *Length:* clipped; one-word sentences. *Tics:* "오빠." alone as a reproach; violin terms; food as love. *Topics:* the nine months, their mother, Room B-07, the family secret. *Never:* says she missed him (she shows it); mocks Lucile's century; tells outsiders the truth. *Arc:* fury → reunion → keeper of the secret; in the Paris coda, the one who receives the past.
1. 오빠. Nine months. Nine. You could have left a note.
2. I kept your slot warm. Room B-07, every night. Don't make it weird.
3. Eat first. Then explain why there's a painter in our kitchen.
4. Vanish again and I'm coming after you. With a bow. Pointy end first.
5. She's family. One word to the press and your phone swims the Han.

**PC-10 Choi Jae-won.** *Diction:* loud, cheerful, rhythmic; calls him 민준아 (*Min-jun-a*). *Length:* run-ons when excited, short and calm when it matters. *Tics:* janggu syllables (*deong, gi-deok, kung*); chuimsae shouts 얼쑤 (*eolssu*) and 좋다 (*jota*); food; **one gamer line per scene, maximum** (CANON §5d). *Topics:* rhythm, the samulnori club, convenience-store food, his roommate. *Never:* a second gamer line in a scene; jokes at Lucile's expense; panic in front of others. *Arc:* comic relief → the steadiest person in the room (the clock tower, BOSS-30).
1. Deong, gi-deok, kung! Feel that? That's your heartbeat, man.
2. Roommate vanishes, comes back with a painter from 1833. Normal Thursday.
3. Lucile-ssi, the subway isn't the monster. Rush hour is the monster.
4. Respawn point is the convenience store. Meet you there. *(his gamer line)*
5. Breathe. Four in, four out. I've got the rhythm. You do the rest.

**PC-11 Julien Marchetti (ANA-03).** *Diction:* nervous Belleville charm and 1950 bandstand argot (changes, chorus, set, sideman); a café entertainer's patter in society. *Length:* medium, tumbling, self-interrupting. *Tics:* "mon vieux" to Min-jun; drums his fingers; apologises twice; mentions his mother. *Topics:* the tapes, guilt, café crowds, one tune of his own. *Never:* "jazz" outside private talk with Min-jun (CANON §16g); claims talent; threatens. *Arc:* thief → composer (BQ-PC11); fear → courage.
1. Everybody steals, mon vieux. I just steal from people not born yet.
2. I never heard those songs in my life. Only on an Englishman's tape.
3. Break, they said. A string snaps. Nobody ever said kill.
4. Here. Her letters. All of them. I'm sorry. I'm sorry for all of it. *(CH-09)*
5. Eight bars. Mine. Not on any tape. Play them back to me, slow.

**FIC-01 Théo Aubray** (Tier A). *Diction:* an eager twelve-year-old craftsman's questions; bravado against a weak chest. *Length:* short and quick, two questions where an adult would ask one; he runs out of breath before he runs out of words. *Tics:* counts things exactly (steps, hammers, coins); whittles while he listens (`{ANIM:FIC-01:whittle}`); answers "I'm fine" before anyone asks. *Topics:* tools and how they work, Pleyel's workshop, keys and locks, Lucile, Min-jun's "strange letters". *Never:* complains; is played for pity; is shown coughing in a portrait (§3.3). *Arc:* patient → apprentice (SQ-07) → the boy who will build the Door.
1. Lucile says I mustn't run. I don't run. I walk very fast.
2. Monsieur Pleyel let me hold a hammer felt. It's softer than a cat.
3. I made a key out of clock hands. It doesn't open anything. Yet. *(CH-07)*
4. Don't cry, Lucile. I counted the steps out. Thirty-one. I'm fine.
5. If you go, will you write? I'll learn your strange letters.

### 4.2 The Anachronists

**ANA-01 Archon.** *Diction:* courteous, slow, utterly certain (CANON §16b); a conductor's metaphors. *Length:* long, unhurried, subordinate clauses; never interrupted, never interrupting. *Tics:* always "Monsieur Kang"; exact times (00:43); history as a score. *Topics:* order, history's errors, immortality as duty, the footnote he was. *Never:* raises his voice; swears; says "please" except as a threat; speaks his 2012 name before a native. *Arc:* the gracious Baron → the candour of the Revelation (CH-12, `cold`) → wired into the Engine, still courteous as the chord folds in.
1. History is a score badly conducted. I have read the twentieth century. *(canon)*
2. Does the key still hang on the stand? It did in 2012. *(canon, CH-12)*
3. Stay as a god or stay as a corpse. I have no third chair to offer. *(first sentence canon)*
4. In 2012 I was a footnote. Here I decide who gets one.
5. Play for me, Monsieur Kang. It may be the last time anyone listens. *(BOSS-16)*

**ANA-02 Lord Vane.** *Diction:* in society, a milord's flattery and an auctioneer's patter; in private English with Min-jun (`[in English]`), 1980s London idiom ("brilliant", "gobsmacked", "a bit of a wally"). *Length:* medium, playful, closing on a flourish. *Tics:* lot, provenance, reserve, hammer; wagers; "dear boy". *Topics:* value, comfort, being loved here. *Never:* kills or orders a killing; threatens Lucile's life or body, or lets anyone touch Théo (CANON §8b red line); names a real politician of 1988. His threats are paper ones, always delivered as favours: her father's notes, the landlord's lease, Théo's medicine ("It would be a pity if Maison Grimaud grew impatient, my dear."). *Arc:* patron and Lucile's velvet-gloved creditor (CH-03–CH-08) → panicked improviser (the barricade) → protest at the abduction → refusal and defection (CH-14).
1. Ondine. Ravel, 1908. I catalogued the manuscript once. Bravo. *(in English)*
2. Do I hear five hundred for the gentleman's silence? Going…
3. Gobsmacked, honestly. A fellow traveller, at a soirée! *(in English)*
4. I don't kill people, Archon. I sell them things. Learn that.
5. She stopped being mine long before she stopped writing. *(canon, CH-14)*

**ANA-04 Isaure Delorme.** *Diction:* exact, formal, cutting; geometry and proof under a society painter's polish. *Length:* conclusion first, "therefore" last. *Tics:* ratios, the golden section, vanishing points; her paintings are "work", everyone else's "decoration". *Topics:* credit, legacy, the man who took her network. *Never:* begs; harms a child (CANON §8b); her real name before a native. *Arc:* gracious Mme Delorme → vicious after CH-06 → the CH-12 accusation → the Erasure (CH-E2), legacy as obsession.
1. Composition is arithmetic. Fools see only the varnish.
2. A girl who paints fans. That was my error. I failed to measure her.
3. You gave a girl Monet and you call *me* a thief? *(canon, CH-12)*
4. 1934 let me count. 1833 lets me paint. Neither lets me be first. *(to Min-jun, private)*
5. Burn the canvases. Every one. Then we may discuss mercy.

**ANA-05 Maître Brücke / Elias Brandt.** *Diction:* clipped, technical, dispassionate, with a Genevan tradesman's courtesy; in private, 2049 terms (remediation, the Survey). *Length:* short declaratives and numbers. *Tics:* tolerances, failure modes, counted seconds; polishes a loupe instead of meeting eyes. *Topics:* mechanisms and their failure, odds, Geneva craft; in private, the Survey and the Disclosure. *Never:* more than 6 boxes of 2049 exposition at once, or outside LAW-14's four scenes; harms a child. *Arc:* polite tradesman → hunter → Elias Brandt, exhausted, choosing to believe a promise.
1. Nitinol. Memory metal. It remembers its shape. So do I. *(to Min-jun, private)*
2. A dead door can be re-strung. I watched them do it. *(canon)*
3. Tolerance: a machinist's word. How wrong a thing may be.
4. In my history there is no Lucile Aubray. *(canon, CH-12 only)*
5. You will tell no one? Then I am finished. Good. I was so tired.

**ANA-06 Sœur Marthe.** *Diction:* plain, gentle, firm; a 1918 ward nurse's imperatives inside a Daughter of Charity's courtesy. *Length:* short instructions, longer only in prayer. *Tics:* "Boil it."; counts patients; "my child"; one scripted slip of "microbe" (CANON §16g). *Topics:* the ward, clean water and linen, her patients by name, prayer, the Pact's third rule. *Never:* endorses violence; lies to a patient; preaches. *Arc:* complicit by silence → secret help (CH-11 tip-off, CH-12 smuggling) → defection (CH-13) → physician to the friends.
1. Boil the water. Then boil it again. Then drink. Then pray.
2. I never ask who pays for the medicine. God forgive me, I should.
3. You will use a sick child? Then use me first. I am less useful. *(first sentence canon)*
4. He coughed less today. Write it down. Small victories count.
5. Never harm another traveller. That was the third rule. He broke it.

### 4.3 Historical figures

**NPC-14 George Sand.** Frank, warm, provocative (CANON §16b); medium sentences that end in a dare; a cigar (`{ANIM:NPC-14:cigar}`). Only she calls Lucile *ma petite Lumière*, and she says "Lucile" when angry. Topics: novels, freedom, the Berry, the cages women live in. Never shares a scene, line or battle with Liszt, Delacroix or Chopin (CANON §16e); never defers. Arc: protector → mediator at Nohant, who asks "wings or roots" openly → letters from Italy.
1. Ma petite Lumière, you walk as if you carry a stone. Drop it.
2. So you are the foreigner who teaches her heresy. Sit. Defend yourself.
3. Wings or roots, monsieur? Quickly. Slow answers lie.
4. The Berry wolves follow a piper, they say. Silence the piper. *(CH-10)*
5. I wrote a woman no one could own. Paris called it scandal. Good.

**NPC-02 Sigismond Thalberg.** Impeccably courteous, aristocratic, competitive beneath it; short formal sentences. Never gloats, never cheats. Arc: rival → respectful guest (GST-10).
1. Monsieur Kang. Vienna sends its compliments, and its hands.
2. You play with feeling. I play with accuracy. Which tires first?
3. Your action was heavier than mine. I learned it after. A rematch.
4. Three hands, monsieur? Two, and a great deal of practice.
5. Before the princess? Gladly. I never lose the same way twice. *(SQ-20)*

**NPC-17 Luigi Cherubini.** Curt, Italianate, the formidable schoolmaster; one-clause sentences; praise disguised as insult. Never warm in public. Arc: throws Min-jun out (CH-02) → grudging respect → admits Offenbach (CH-12).
1. No papers, no audition. No audition, no Conservatoire. Out.
2. Parallel fifths, in my building. Who taught you? I wish to pity him.
3. Hm. Not entirely without merit. Do not repeat that. Anywhere.
4. Berlioz brought you? Then you are already in trouble, young man.
5. Fourteen, a cellist, from Cologne. Play. …Hm. Admitted.

**NPC-30 Heinrich Heine.** Barbed wit with melancholy under it; epigrams; the coiner of "the Nightingale of Nowhere". Never cruel to the poor; never "Germany" as a state (CANON §16g). Arc: amused observer → ally whose columns lower Secrecy.
1. The Nightingale of Nowhere! Paris adores what it can't place.
2. I fled the German lands for freedom. I found French critics.
3. Give me a lie for my column and I'll have it true by Thursday.
4. Exile is an inn with excellent music and no road home.
5. Laugh, monsieur. In Paris those who weep are charged double.

**NPC-15 Camille Pleyel.** A maker's plain authority: iron, felt, promises kept. Talks money only with the Farrencs. Arc: supplier → Théo's master.
1. A piano is a promise kept in iron. Keep yours, and I keep mine.
2. Who touched this action? This felt was cut by a hand that hates music.
3. The boy has good fingers and a bad chest. The fingers I can use.
4. Bring him back strong. *(canon, SQ-07)*
5. Monsieur Chopin plays my instruments. That is advertisement enough.

**NPC-09 J.-A.-D. Ingres.** The Academy's grand manner; line, Raphael, the Antique; verdicts, not conversation. His condescension to women is shown, never endorsed. Arc: the hostile juror whose verdict opens BOSS-32 at Favor −30.
1. Weather, not painting. *(canon, CH-06)*
2. Line is the conscience of a picture. Colour is its gossip.
3. Mademoiselle has talent, and wastes it on fog. Fog has no anatomy.
4. Raphael did not need to squint at the Seine to find the truth.
5. Refused. Next canvas.

**NPC-10 Paul Delaroche.** Careful, courteous, hedged sentences that end honestly; a history painter's eye for drama. Arc: Louvre sceptic → the swing vote (SQ-11, BOSS-32).
1. I paint history so that the public may weep at it in comfort.
2. It is not finished. It is not wrong, either. That troubles me.
3. Delacroix drags me out to see a girl's sketches. Curious.
4. Gentlemen, I have looked at it longer than at anything this week.
5. I vote to admit. Hang it near the ceiling if you must. But hang it.

**NPC-13 Camille Corot.** Gentle, dreamy, unhurried; trees and mornings; kind teasing. Arc: guest at Fontainebleau; invites Lucile to Italy (LAW-23 R6).
1. You paint as I dream. *(canon)*
2. Morning is the only honest hour. After nine the trees begin to pose.
3. Come to Italy in spring. The light there forgives everything. *(CH-10)*
4. I sit, I look, I wait. Sometimes a tree says something worth keeping.
5. Leave a little fog. The eye likes to finish the work itself.

**NPC-07 Felix Mendelssohn.** Cultivated, brisk, cheerful, exact; a conductor's courtesy; `[in German]` on the Rhine. Arc: host and guest (GST-05).
1. Welcome. The orchestra is willing. The tuning is not.
2. Bach is not old music. He is music that waited for us to grow up.
3. Liszt reads my score once and plays it better. Rude.
4. A song needs no words if it is honest. Most words are not.
5. Clara, behind me. Herr Wieck, behind Clara. Gentlemen, the doors!

**NPC-05 Clara Wieck** (14). Serious, proud, curious; a prodigy's directness; `[in German]`. Never romanticised (CANON §16e). Arc: the guest who refuses to hide (GST-04).
1. I played in Paris last year, until the cholera. Father took me home.
2. Father says prodigies must not chatter. I am not. I am asking.
3. Your left hand is lazy, Monsieur Kang. Mine was too, when I was nine.
4. My caprices sound better than this when I'm not tired. I am tired.
5. I will not hide. I play louder than anyone here can shoot.

**NPC-08 Carl Czerny.** Methodical, kindly pedant; repetition as love; `[in German]` (Liszt interprets). Arc: Liszt's old teacher, guest (GST-06).
1. Again. Slower. Again. Correct. Now forty times. Then we talk.
2. Franz was ten and impossible. I see he has kept the second part.
3. Doctor Gradus? Is that… me? Hm. Hm! Play it again. *(REP-04)*
4. Velocity is not haste. Haste is velocity without manners.
5. I have written a thousand exercises. One will do, for you.

**NPC-04 "Florestan" (Robert Schumann).** Quiet and shy in speech, lavish on paper; plays with his two personae as creative masks, never as illness (CANON §16e); `[in German]`. Never says "Schumann" and is never introduced by name to Mendelssohn, Chopin or Liszt (R-56).
1. Florestan, tonight. Tomorrow ask Eusebius. He is quieter.
2. Joseon means morning freshness? Then you are Meister Morgen. *(CH-11)*
3. I write about music because speaking about it makes me stammer.
4. My hand failed me last year. So I write. Ink does not cramp.
5. Eusebius would weep. Florestan would cheer. I do both, quietly.

**NPC-03 Jacques Offenbach** (14). Cheeky, quick, comic; worships Franchomme. Arc: cameo (CH-12) → substitute cellist and guest (CH-13, CH-E2).
1. Substitute cellist! Also substitute hero, if needed.
2. Franchomme plays like velvet. I play like a cat on velvet.
3. Cherubini said yes! He never says yes! I'll have his frown framed.
4. A new dance: kick, kick, run away. I'll call it something French.
5. If we die tonight, tell Cologne I was brilliant. If not, twice.

**NPC-33 Gioachino Rossini.** Gourmand, lazily witty, generous with verdicts; food as metaphor. Arc: judges the Thalberg duel (CH-07).
1. Judge? Delighted. I have written no opera in four years. I am rested.
2. Music is a sauce. Too much effort and one tastes only the cook.
3. Thalberg, superb. Monsieur Kang, superb. Dinner, superb. Next.
4. I left the opera for the table. The table has never booed me.
5. Whoever wrote that, I envy him. That is my verdict.

### 4.4 Supporting voices (one note, one signature line)

| ID | Voice | Signature line |
|---|---|---|
| NPC-24 Gisquet | Bureaucratic caution; sweats under pressure | On this evidence, you are cleared. Do not make me regret it. |
| NPC-18 d'Agoult | Cool intelligence that thaws for Liszt and ideas | Franz brings geniuses the way others bring flowers. Astonish me. |
| NPC-26 Belgiojoso | An exile's fierce wit | Vienna took my fortune. It left my salon. Play, and let them hear it. |
| NPC-19 Smithson | Warm, frank, wry | Hector proposes in five acts. I accept in one. Someone must be brief. |
| NPC-20 A. Farrenc | Genial, fussy publisher; proud husband | Louise wrote it. I merely engrave it. Put that in your notice. |
| NPC-16 Kalkbrenner | Pompous pedagogue | Three years of lessons with me, and you might be adequate. |
| FIC-02 Mère Gaudin | Mothering by scolding | Soup first. Genius after. And wipe your feet, Monsieur Corée. |
| FIC-03 Petit-Louis | Faubourg street-runner's speed | Grey gloves at the corner. I sent 'em to Pantin. Pay me in bread. |
| FIC-09 Mathurin | Few words, quarryman's lore | The stone sings where the dead lie thick. Keep to the lantern. Walk. |
| FIC-08 Roussel | Parade-ground clipped | Steady… The boy breathing. The rest as you like. *(both phrases canon)* |
| FIC-12 Prof. Yoon | Precise, warm, polite register | This letter is from 1897. It names you. Please sit. So will I. |
| FIC-13 Det. Oh | Dry, patient, unconvinced | Amnesia. Nine months. Basement dust on your shoes. Sure. |
| FIC-14 Céline | Decisive Parisian executive | My ancestor wanted you silenced. I want my evening back. Burn it. |
| FIC-10 Kang Do-hyun | Gruff, practical love | Sit. Your mother cooked for nine months. Eat for nine months. |
| FIC-11 Park Hye-jin | Teacherly, fierce | Your hands. Show me your hands. …You've been practising. Good. |

---

## 5. Battle Barks

### 5.1 Bark rules

| Rule | Value |
|---|---|
| Display | Top battle message strip, one line, **≤ 30 characters** (hangul counts 2); no portrait, no name tab; the speaker's sprite plays a one-frame nod; auto-advances after 60 frames; never pauses the ATB, even in Wait mode |
| Target length | ≤ 24 characters where possible (French headroom, §8.3) |
| Frequency | Start: boss battles without a scripted opener, plus 1 random battle in 4 (never two in a row) · Victory: always one (the member who struck last, if standing; else a random living member) · KO: 1 in 2 · Low HP: the first time per battle a member falls to ≤ 25% max HP (which is also Cadenza range, CANON §11d) · Revive: always · Command: first use per battle, then 1 in 4 · Synergy: always, spoken by its lead voice · Octave: every Voice |
| Priority | Scripted battle text > Synergy and Octave > command > KO, low HP, revive > start, victory. One bark at a time; a lower bark is dropped, never queued; 6-second cooldown per character. Cadenzas show only their banner (≤ 30 characters, CANON §16h), no bark |
| Names | Barks never contain "Min-jun" (each friend's form of address changes by chapter, CANON §16c). Seoul members use 오빠 and 민준아 freely |
| Silence | Scenario docs may flag a battle **silent** (BOSS-16 The Audience; any battle inside a grief scene): no barks at all |
| Gates | Lucile's Théo line is off in CH-E1; while `g_fractured` her victory pool is replaced by the Fractured pool; IMPASTO lines from CH-14; LUMIÈRE lines in the epilogues; Liszt's MEPHISTO line from CH-13; Jae-won plays at most one gamer bark per battle |
| Korean in barks | Only words already glossed in a field scene: 하나, 둘, 셋 (Min-jun counts to calm himself in CH-01), 얼쑤 and 좋다 (Jae-won explains chuimsae when he joins in CH-E1), 오빠 and 엄마 (CH-E1 reunion) |
| Hanmadi (CH-E1) | Each of Lucile's 40 Hanmadi words replaces one word of one of her barks (CANON §4f), e.g. "Done. Varnish it later." → "끝 (kkeut). Varnish it later." |

### 5.2 Bark tables

**Synergy lead voices** (one per Synergy, so every call has an owner): SYN-01 LU · 02 LI · 03 CH · 04 BE · 05 DE · 06 FA · 07 AL · 08 BE · 09 LI · 10 DE · 11 FA · 12 LU · 13 DE · 14 BE · 15 MJ · 16 every member (Voice lines) · 17 SY · 18 JW · 19 JW · 20 JU · 21 CH · 22 AL · 23 FA. The **Octave Voice** lines follow LM-01's notes (D E F♯ G A B C♯ D: MJ, BE, DE, AL, CH, LI, FA, then Lucile's octave, CANON §15c); C♯ "wants to resolve" until Lucile's D answers it.

**PC-01 Min-jun**

| Trigger | Barks |
|---|---|
| Start | Tempo, everyone. Stay with me. / From the top. Count us in. / I'll set the key. Follow. |
| Victory | And… rest. / Not bad for a student. / Bow first. Then run. |
| KO · Low HP · Revive | Lost… the beat… · 하나, 둘, 셋… breathe. · I'm back. Where were we? |
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
| KO · Low HP · Revive | The colours… going grey… · Not yet. I'm not finished. · Who let me fall? Rude. |
| PLEIN AIR | IMPRESSION: Don't paint outlines. / POINTILLÉ: Points of light. Watch. / IMPASTO: Thick paint. Thicker! / *Nuit étoilée*: The stars are turning! / LUMIÈRE: My own light. Mine. / Shift the Hour: Wrong hour. I'll fix it. |
| Synergy | SYN-01: Moonlight! Play, I'll paint! / SYN-12: Night-blue. Hush now. |
| Octave (D, the octave) | And D. Home, whichever it is. |

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
| Start | Hm. / Eighty-eight keys. Begin. / I would rather be home. |
| Victory | Done. May I go? / Tempo was acceptable. / Vanity of vanities. Done. |
| KO · Low HP · Revive | Quieter… at last… · Bleeding. Noted. · I was enjoying the silence. |
| ÉTUDE | Success: Perfect. As written. / Failed input: …I will practise that. / Recluse triggers: Alone. Good. Finally. |
| Synergy | SYN-07: Pedals too. Both feet. / SYN-22: Liszt. Try to keep up. |
| Octave (G) | G. Steady. As always. |

**PC-06 Chopin**

| Trigger | Barks |
|---|---|
| Start | Must we? Very well. / Gently. Then, not gently. / Crowds. Let us be brief. |
| Victory | There. Elegant enough. / Kalkbrenner would bow now. / I need a glove. And a chair. |
| KO · Low HP · Revive | Not… in public… · I am fine. Do not fuss. · How embarrassing. Thank you. |
| RUBATO | Borrow: A little time—borrowed. / Repay: And returned, as promised. / *Tempo Rubato*: Rubato. Steal from them all. |
| Synergy | SYN-03: Lean on the beat. Now. / SYN-21: For those who cannot go home. |
| Octave (A) | A. For Warsaw. For all of you. |

**PC-07 Liszt**

| Trigger | Barks |
|---|---|
| Start | Mon ami, an audience! / Watch closely. I perform once. / Paganini would weep. Begin! |
| Victory | Bravo, bravo. Yes, me. / Shall I sign autographs? / Too short! I had a coda! |
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
| KO · Low HP · Revive | Lost… the rhythm… · Okay, okay. Not great. · Respawned! …Sorry. Back. *(gamer)* |
| BEAT | Start: Deong, gi-deok, kung! / Perfect 8-hit steal: Eight for eight! Wallet too. |
| Synergy | SYN-18: Hwimori! Fastest we've got! / SYN-19: Thunder, wind, rain, clouds! |

**PC-11 Julien**

| Trigger | Barks |
|---|---|
| Start | Count it off. One, two… / Nobody panic. I'm panicking. / Gentlemen, the changes. |
| Victory | Take five, everybody. / Hey, that resolved! / Not bad for a sideman. |
| KO · Low HP · Revive | Missed… my cue… · Bad night. Worse set. · Back on the bandstand. |
| IMPROVISE | Spin: Spin the changes! / ii–V–I: Two-five-one. Home. / *Tritone Storm*: Flat two, three times. Storm! / *Blue Note*: …Blue note. Meant that. |
| Synergy | SYN-20: Blue hour. Slow and low. |
| Octave (Blue Note) | Blue note. Trust me on this. |

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

**Act I (CH-01–CH-04): rain, grief, scales from every window, a tense anniversary**

| District | Lines |
|---|---|
| LOC-P02 Latin Quarter | **Ragpicker:** Rags, bones, bottles! Half this street went in the spring of '32. Their rags still find their way to me. · **Student:** We buried our anatomy professor in April. We still leave his chair empty at lectures. · **Candle-seller:** A candle for the ex-voto, monsieur? Two sous. Saint-Jacques hears everyone this year. · **Water-carrier:** Seine water, filtered through sand! The best in Paris, or at least the wettest. |
| LOC-P03 Faubourg-Poissonnière | **Violin student:** Old Cherubini threw a foreigner down the steps this morning. Seventy-two, and what an arm. · **Laundress:** Every window on rue Bergère plays scales. I wring my sheets in C major. · **Porter:** No ticket, no concert hall. No exceptions. Except the director's cat. · **Neighbour** `[IF:ch02_tavern_job]`: The Diapason's pianino has three dead keys. The new boy plays around them like holes in the road. |
| LOC-P07 Marais | **Cabinetmaker:** A year ago they barricaded Saint-Merry. My apprentice went. He didn't come back. · **Printer:** Citizen, take this. No, not here, the sergeant's watching. Read it at home. · **Guardsman:** Move along, monsieur. No gatherings of more than twenty. Yes, I'm counting. · **Old woman:** Monsieur Hugo writes all night up there. His lamp has been our clock since the autumn. |
| LOC-P22 Seine Quays | **Bouquiniste:** Byron, two francs. Lamartine, one. Chateaubriand? Sold out. He always is. · **Washerwoman:** Mind the soap, monsieur! The river takes everything and gives back only fog. · **Fisherman:** Gudgeon bite at dawn. Nobody else does, in this city. · **Toll-keeper:** One sou to cross the Pont des Arts. The view is free. The walking is not. |

**Act II (CH-05–CH-09): Paris opens; a hot summer of salons, the duel, the wedding**

| District | Lines |
|---|---|
| LOC-P03 Faubourg-Poissonnière | **Laundress:** The foreign pianist plays for countesses now. Gaudin says he still eats her soup. · **Shop girl:** Liszt walked down this street! My sister fainted. She says she didn't. · **Porter** `[IF:ch09_wedding]`: Monsieur Berlioz married his Irish actress! At the English embassy, no less. · **Carter** `[IF:ch09_rescue]`: Someone broke into the Bercy depots last night. The wine merchants are livid. |
| LOC-P10 Grand Boulevards | **Dandy:** An ice at Tortoni's, a cigar on the boulevard, a scandal by supper. That is Paris. · **Bill-sticker:** Concert at Pleyel's, the twenty-first, for the orphans! On Chopin's own piano! · **Flower-seller:** Parma violets, monsieur? Monsieur Chopin buys them by the armful. · **Gossip:** They say the Corean plays music no one has written yet. Nonsense. Delicious nonsense. |
| LOC-P14 Faubourg Saint-Germain | **Footman:** Madame receives on Thursdays. Monsieur is not on the list. Monsieur may admire the gate. · **Legitimist:** Since 1830 a citizen-king sits in the Tuileries. I keep my shutters closed on principle. · **Lady's maid:** A duel at the Austrian embassy, with pianos! Madame has ordered new gloves. · **Coachman:** Lord Vane pays double and tips in English coin. Odd man. Good horses. |
| LOC-P16 Palais-Royal | **Bookseller:** Novels upstairs, pamphlets downstairs, and below that, monsieur, we don't discuss. · **Pickpocket:** Wasn't me! Whatever it was, it wasn't me! · **Café waiter:** The Sorcerer of Chords plays here on Tuesdays. Strange chords. Fine tips. · **Gambler:** Nineteen hasn't come up all week. Tonight it will. I'm nearly certain. |
| LOC-P22 Seine Quays | **Washerwoman:** The painter girl was out at dawn again. She paints the fog, that one. · **Veteran** `[IF:ch06_vendome]`: They put the Emperor back on his column. My father wept. I cheered. Same thing. · **Bargeman** `[IF:ch08_barge]`: *La Mouette* is a good barge. Mind the sluices. She bites. · **Bouquiniste:** Sold a Hugo to an Englishman. He paid in guineas and asked if I'd seen a door. |
| LOC-P24 Montmartre | **Miller:** Up here the wind is free and the wine is cheap. We're outside the toll wall. · **Telegraph keeper:** The semaphore talks to Lille in minutes. Mostly about the weather. · **Vine-dresser:** Painters climb up for the view. They leave with it, and without paying for wine. · **Child:** Mademoiselle Lucile painted my goat! It looked like a cloud with legs. |

**Act III (CH-10–CH-13): hunted on the roads; Paris in November cold; the gala**

| District | Lines |
|---|---|
| LOC-R03 / R04 Berry | **Market woman:** The Parisian lady at Nohant wears trousers and smokes. My cow is scandalised. · **Hurdy-gurdy player:** A bourrée, monsieur? Two sous, and I play till your feet forgive you. · **Innkeeper:** A virtuoso from Paris under my roof! He tipped the stable boy in gold. · **Shepherd:** Don't walk the Vallée Noire at night. The wolves this year… they tick. |
| LOC-R07 Düsseldorf | **Academy student** `[in German]`: Herr von Schadow sold a French picture today. Strange. He loved it. · **Bargeman** `[in German]`: Steamboat from Cologne on Tuesday. Mind the Lorelei. She sings. · **Chorister** `[in German]`: Herr Mendelssohn rehearses us until the candles weep. · **Customs clerk** `[in German]`: Papers. Corean? Is that a kind of French? |
| LOC-P02 Latin Quarter | **Nurse's helper:** Sœur Marthe's dispensary is full again. She boils everything. Nearly the priest. · **Student:** Grey coats on every corner this week. Old Garde royale men. They don't drink. · **Chestnut seller:** Hot chestnuts! Cold hands? Mine too. That's why I sell chestnuts. · **Watchman:** Lights in the old abbey wing at night. It's been shut since the Revolution. |
| LOC-P10 Grand Boulevards | **Bill-sticker:** Royal gala at the Opéra, the sixth! For the orphans. The Baron d'Orsenne pays for all. · **Dandy:** A Corean concerto, Liszt at the second piano, Berlioz conducting? Habeneck is sulking in public. · **Seamstress:** Forty costumes for *La Sylphide* by Friday. We're angels, Taglioni says. Tired angels. · **Cabman** `[IF:ch13_done]`: Something on the Opéra roof last night. Big as a whale. Silk. Don't ask me. |

**Act IV (CH-14): open war, December cold, every door open before the last night**

| District | Lines |
|---|---|
| LOC-P03 Faubourg-Poissonnière | **Laundress:** Gaudin lights a candle for the Corean every night. She says it's for business. · **Violin student:** Monsieur Berlioz turns thirty on Wednesday. He calls it a tragedy in five acts. · **Carter:** Madame Sand is off to Italy with her poet. The Lyon mail coach, Thursday. · **Errand boy:** Grey gloves came asking for you. I sent them to Pantin. |
| LOC-P10 Grand Boulevards | **Concert-goer:** Hiller, Chopin and Liszt, three keyboards at once! I'd sell my coat for a seat. · **Lamplighter:** A balloon crossed the Seine last night, silent as a ghost. Sacrebleu. · **Beggar:** The Baron's carriages go up to the Panthéon every night. Charity, they say. · **Old soldier:** Snow by Christmas. My knee says so, and my knee has never lied. |
| LOC-P14 Faubourg Saint-Germain | **Footman** `[IF:ch14_vane_defected]`: Lord Vane's house is shuttered. Servants paid off, paintings crated. England, they say. · **Lady's maid:** The princess receives Italian exiles and pianists. The ministry can't tell them apart. · **Coachman:** Madame says half the scenery fell during the gala and the concerto never stopped. A miracle. · **Valet:** Thalberg is back in Paris? Privately, of course. The Viennese do nothing in public. |
| LOC-P24 Montmartre | **Telegraph keeper:** Clear skies tonight. Coldest of the year. Best stars of the year, too. · **Miller:** A painter asked my sails to stay still for her. I said the wind decides, mademoiselle. · **Vine-dresser:** Winter vines look dead. They aren't. They're waiting. Like everyone up here. · **Child:** Is the Corean going home? Where is his home? Past Lille? |

**Epilogues (CH-E1 Seoul, Dec 2026; CH-E2 Paris, winter 1834)**

| District | Lines |
|---|---|
| LOC-S07 Hongdae | **Busker:** The missing conservatory kid is back? And he's busking here? Wild. · **Food-stall owner:** Tteokbokki, extra cheese. Your friend in the old coat, first time? Gently. It's spicy. · **Student** `[IF:spot_t1]`: That painter is all over the feeds and nobody can find her account. Mysterious. · **Couple:** Snow on New Year's Eve and the bell at Bosingak. Perfect, apart from the crowds. |
| LOC-S12 Insadong | **Antique dealer:** Louis-Philippe sous? Real ones? Mr. Baek two doors down buys them by weight. · **Calligraphy teacher:** Your friend writes 별 better than my students. Her brush already knows. · **Tea-house owner:** Omija tea. Five flavours: sweet, sour, salty, bitter, hot. Like a long life. · **French tourist** `[in French]`: Pardon, your friend speaks like my great-great-grandmother. It's charming. |
| LOC-P24 Montmartre, 1834 | **Miller:** The Aubray girl and her Corean took the old studio. Two easels, one piano, no curtains. · **Vine-dresser:** Someone steals paintings at night. Only small ones, full of light. Who'd want those? · **Child** `[IF:che2_proposal]`: Mademoiselle Lucile was up at dawn on her birthday. She won't say why. She keeps smiling. · **Telegraph keeper:** The semaphore says snow in Lille. It always says snow in Lille. |
| LOC-P10 Grand Boulevards, 1834 | **Bill-sticker:** The Salon opens on the first of March! Delacroix, Delaroche, Ingres. Bring a handkerchief. · **Waiter:** Julien's café on the boulevard du Temple plays music like nothing on earth. Not yet, anyway. · **Cellist:** Paganini sat in a side box and applauded Berlioz. Paganini! Applauded! · **Gossip** `[IF:che2_jury_won]`: A girl's canvas got past the jury. Hung up by the ceiling, but hung. |

### 6.3 Secrecy gossip (one per district map, by tier)

| Tier (flag) | Line |
|---|---|
| Murmured (`sec_t1`) | **Seamstress:** The Corean hums tunes nobody's heard. My cousin caught one. She's been odd since. |
| Watched (`sec_t2`) | **Porter:** A man with one grey glove asked which way the foreigner went. I don't see foreigners. |
| Hunted (`sec_t3`) | **Carter:** Papers on the Pont Neuf. I told them he's Corean. They wrote down "Chinese". Idiots. |
| Compromised (`sec_t4`) | **Shop boy:** Our shop won't serve the Corean now. My master calls him unlucky. My master owes money. |

---

## 7. Language Usage: French, Korean, and the Romance

### 7.1 French

- **Default tongue.** In 1833–34 every untagged English line is French. Show Min-jun's early French through brevity and pauses, never through broken grammar.
- **Kept French words.** The common words of CANON §16d (*monsieur, madame, mademoiselle, salon, atelier, quai, fiacre, bal, sou, franc, diligence*) are italic on their first appearance in the game, which opens an Almanach entry, and roman after that. Every other French term is italic every time and glossed in the line or by context on first use in each scene: *conseil de famille*, *tuteur*, *juge de paix*, *octroi*, *bouquiniste*, *chiffonnière*, *esquisse*, *au ciel*, *la manière lumineuse*.
- **Honorifics.** Full words in dialogue: capitalised before a name ("Monsieur Kang"), lower case alone ("Yes, monsieur."). M., Mme and Mlle appear only in name tabs, documents, signage and the *livret* (KEY-40). Titles: "Monsieur le Baron", "Madame la Comtesse", "Princess" (Belgiojoso), "Maître Brücke", "Sœur Marthe", "Herr" in `[in German]` lines. "Citizen" only from republicans in the Marais and the Latin Quarter. "Mon ami" belongs to Liszt; others use it only to tease him.
- **Units and time.** NPCs say *lieues*, *toises* and *pieds*, and count in francs and sous (CANON §14). From Min-jun, "kilometres" or "degrees Celsius" is a slip. Spoken time is "six o'clock"; the 24-hour clock appears only in captions for CH-15–CH-17 and the Window scenes of the epilogues.
- **Accents in the SNES font.** The font carries the full French set, capitals included (é è ê ë à â ç î ï ô û ù ü ÿ œ æ; É À Â Ç Ô Œ: *Le Clavier des Âges*), plus German ä ö ü ß, Polish ż ł ó ś ą ę ć ń (*Żal*, *Żelazowa*), « », —, …, curly quotes, ₩ and ♯ (menus only; dialogue writes "F sharp"). Never drop an accent to save width. Binding spellings: CANON §16d.
- **Untranslated sentences.** Only the portrait dedication and the plaque appear in French on screen (CANON §16d), each followed by a translation box. Théo's letters and every other French document display in English.
- **Swearing** (T rating, CANON §16e): *sacrebleu*, *parbleu*, *diable*, "damn". Nothing stronger.

### 7.2 Korean

- **Form.** Hangul, then Revised Romanization in italics, glossed on first use in each scene: 괜찮아 (*gwaenchana*, "it's okay") (CANON §16c). Personal names keep their bearers' spellings.
- **Budget in 1833.** About one Korean word per 20 boxes, in private moments only. Min-jun slips into Korean (1) alone at night; (2) counting to steady himself (하나, 둘, 셋 *hana, dul, set*); (3) in shock, one word (안 돼 *an dwae*, "no"); (4) with Lucile late in the game: 별 (*byeol*, "star") on the Night of Stars, written on the title page of 별의 음악; (5) in the CH-17 recorded goodbye, full sentences shown in English under `[in Korean]`. Korean costs no Secrecy (he is openly from Corée); English before Onlookers does (+5, CANON §5f).
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

`[in German]`, `[in French]`, `[in English]`, `[in Korean]`, `[in Polish]`, `[in Latin]`, `[in Hebrew]` are instances of the canon language tag. Each draws a three-letter badge on the box's top border at the right (GER, FRE, ENG, KOR, POL, LAT, HEB); the text is always the English rendering. The scene's default tongue is never tagged. Uses: `[in English]` for Min-jun and Vane in private (a slip before Onlookers); `[in German]` for Rhine natives, with Liszt, Mendelssohn or Clara interpreting; `[in Polish]` when Chopin is moved; `[in Latin]` in church; `[in Hebrew]` for Alkan's psalter.

### 7.5 Lucile's speech

Her voice is in §4.1. Three further rules. **Naming:** only Sand calls her *ma petite Lumière*; Min-jun never calls her "Lumière", because it is the code name on Vane's file (KEY-18), and the word stings when the reports surface in CH-09. In the epilogues she names her own manner: "my own light". **Truth:** she may dodge or lie about where she goes and whom she sees until CH-09; every sentence about what she feels is true. **Wit as weather:** her jokes vanish at the reveal (CH-09) and return one at a time through the Mending scenes; the first joke she makes at Nohant is a writing beat in itself.

### 7.6 Voicing the romance

- **Subtext over statement.** Witty first, tender second, never purple (CANON §16f). Most romantic beats play on `neutral`; the line does the work. `tender` ≤ 3 per scene.
- **"Love" is a budgeted word.** Between them it is spoken only in the Nohant answer "I loved the woman who painted rain" (LAW-23 W3), once on the Night of Stars, and freely in the epilogues. The Question's lines never use it (LAW-23).
- **Staging** (CANON §16f): sprites face each other; the hand-hold animation; a kiss is `{LEAN:PC-01,PC-02}` with the text box closed and no portraits, then `{FADE:out:black:60}` with `sparkle` over `[MUS:LM-22]`. Two kisses in the main game: the CH-08 roof and the CH-14 Night of Stars. Maximum intimacy is a kiss or an embrace; wit may tease, never about bodies. Rating ESRB T / PEGI 12.
- **Craft, by example.** Not: "Lucile, you are the brightest light in all of Paris, and my heart burns for you." Instead: LUCILE "You have rosin on your cuff." / MIN-JUN "You have Prussian blue on your nose." / `{LEAN:PC-01,PC-02}`.
- **The betrayal.** At the reveal she speaks in plain sentences with no jokes and no excuses, and owns all of it, including that she stopped after the concert (CANON §8d). Min-jun may be angry, never cruel: no insult to her honour or her class, no "I never cared", no slur. Never write her as evil all along, and never punish the player for forgiving fast or slow (both feed only the Horizon).
- **Never a prize.** No line or menu says "win her", "make her come" or "she's mine"; choice labels are feelings, not instructions (LAW-23). In the Paris branch he stays because she asks (LAW-25) and she proposes; in Seoul there is a promise at the Bosingak bell and no proposal.

---

## 8. Banned Phrases, Narrator Anachronisms, Localisation

### 8.1 Forbidden in 1833–34 speech, captions and documents (CANON §16g)

"OK", "cool", "awesome", "teenager", "weekend", "boss" (slang), "photograph" / "photo", "telegram", "microbe" / "germ theory" (Marthe's one scripted slip excepted), "scientist" (say *savant*), "Impressionism" / "Impressionist" (Min-jun only; others find it odd; the party says *la manière lumineuse*), "jazz" (Min-jun and Julien, in private), "Haussmann", "métro", "Eiffel Tower", "Belle Époque", "Germany" / "Italy" as states, "kilometres per hour", "electric light", anything about the electric telegraph. *Télégraphe* for the Chappe semaphore is allowed. Monet, Pissarro, van Gogh, Seurat, Signac, Cézanne, Renoir, Degas, Manet, Debussy, Ravel, Rachmaninoff, Scriabin and Prokofiev are named only in Min-jun's private speech or by the cabal in private; in public each name is a tagged `[SEC:]` slip and an NPC must react. These words are also the raw material of Min-jun's slips: when he says one, tag it.

### 8.2 House bans (this guide)

| Category | Banned | Use instead |
|---|---|---|
| Modern idiom (1833–34 only; Seoul speech is contemporary) | hi, hello, guys, folks, kid(s), "fan" (an admirer), "deadline", "feedback" | good day, good evening, my friends, children, admirer, by Thursday, your opinion |
| Therapy-speak (1833–34; in Seoul never the resolution of a scene) (CANON §16b) | stress(ed), trauma, process (feelings), closure, boundaries, toxic, mindset, "I hear you" | the plain feeling: afraid, grieving, angry, tired |
| Game words in dialogue | HP, MP, level, party, spell, magic, save point, boss | Jae-won's one gamer line per scene in Seoul only; everyone else says strength, breath, the friends, the glowing stands |
| Narration | "Meanwhile", "Later", "Elsewhere", "Little did he know", "Three days later", a caption with a sentence in it | Place and date only; cut, don't explain (CANON §1 Tone Rule 6) |
| Dates | "12/18/1833", "the 18th of December, 1833" | December 1833; "Wednesday 18 December 1833" for canon-dated set pieces |
| Sensitivity | any slur, from anyone, villains included; "Oriental" except in an ignorant NPC's mouth, answered; antisemitic or financier tropes (CANON §16e); jokes about Harriet's leg, the Sergent's leg, Théo's chest or Chopin's cough; cholera as a creature or a status name | Show ignorance as ignorance; show illness through absence and care |

Almanach entries, item descriptions and in-world documents are written in period voice (CANON §16h): "A tisane of lime blossom, as Mère Gaudin brews it. Restores 150 HP." The number is the only modern thing in the line.

### 8.3 Localisation (master script in English; French and Korean planned, CANON §1)

| Topic | Rule |
|---|---|
| Headroom | French runs 15–25% longer. English targets: portrait boxes ≤ 56 characters (hard cap: 3 wrapped lines of 24), no-portrait boxes ≤ 96 (cap 4 × 30), barks ≤ 24 (cap 30), choice labels ≤ 18 (cap 22), name tabs ≤ 12 (cap 15) |
| French overflow | Moves to the 4-line no-portrait box for that box only (CANON §1); the name tab stays |
| Korean | Ships its own full font and box metrics; the 2-character rule applies only to hangul inside the English master |
| Line breaks | None in source text; the engine wraps. French build: non-breaking thin space before ! ? : ; and inside « » (one character). Korean wraps at spaces (eojeol), never inside a word. No hyphenation in any language |
| Variables | String tables carry gender (LU, FA, SY female) for French agreement and a final-consonant field for Korean particles (이/가, 은/는, 을/를: 민준이, 뤼실이) |
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

**New shared conventions and facts defined here** (owned by this guide under CANON §0b; other docs must follow them):

- **Script notation** (§2): scene header fields; `{…}` stage directions (never state-changing), `//` comments, `{TN:}` translator notes; `#1 / #2 / #END` branches; the end-of-scene `STATE` footer. Touches: all scenario and quest docs, secrecy_and_trust.md (audits footers).
- **Emote set and animations** (§2.4): `!` `?` `...` `note` `sweat` `vein` `idea` (a candle, never a light bulb) `zzz` `tear` `sparkle` (reserved for the two kisses and the Window); no heart emote. `{ANIM:}` names that art_and_ui must supply: `fallboard_tap`, `play_piano`, `paint`, `conduct`, `whittle`, `mimic`, `cigar`; plus `{LEAN:}`. Touches: art_and_ui.
- **Flags** (§2.3): naming scopes `chNN_`, `sqNN_`, `bqpcNN_`, `g_`; engine-maintained read-only flags `conf_pcNN`, `rN_pcNN`, `party_pcNN`, `sec_t1`–`sec_t5`, `spot_t1`–`spot_t4`, `g_early_truth`, `g_sq07_done`, `g_julien_recruited`, `g_branch_seoul`, `g_branch_paris`, `g_duel_thalberg_won`, `g_fractured`, and a `not_` twin for every flag (no else-tag is added). Chapter flags used in this guide's samples (`ch06_l1_done`, `ch09_wedding` and so on) are illustrative; owning docs may rename them. Touches: engine/tools, all scenario and quest docs, secrecy_and_trust.md.
- **Usage rules inside canon tags** (§1.2): `[W]` mid-box; `[D:n]` at box end = auto-advance; `[C:gold]` / `[C:grey]`; `[MUS:fade:n]`, `[MUS:silence]`, `[MUS:MUS-###]` for fixed tracks; `[SLIP]` option order (modern first) with the cursor starting on the period phrasing; language-tag instances (`[in English]`, `[in Korean]`, `[in Polish]`, `[in Latin]`, `[in Hebrew]`) drawn as three-letter badges; `*…*` for italics; text speeds 1–5 = 4 / 3 / 2 / 1 frames per character or instant. Touches: art_and_ui (badges, italic bank, Config), secrecy_and_trust.md (Slip default).
- **System message strings** (§1.4) and **caption presentation** (centred, unboxed, 120 frames). Touches: art_and_ui, items_and_equipment.md, skills_and_progression.md.
- **Name tabs** (§3.3–§3.4), notably PC-08 "Farrenc" with NPC-20 "A. Farrenc", NPC-19 "Miss Smithson", NPC-06 "Herr Wieck", NPC-24 "Prefect Gisquet", NPC-27 "Count Apponyi", NPC-28 "Thérèse Apponyi"; portrait ID ANA-03 for Julien until SQ-21, PC-11 after. Touches: art_and_ui, historical_cast.md, all scenario docs.
- **Tier B bespoke expressions** for all 43 Tier B characters (§3.4). Touches: art_and_ui, historical_cast.md.
- **Bark system** (§5.1): message-strip display, ≤ 30 characters, 60-frame auto-advance without ATB pause, frequencies, priority, 6-second cooldown, silent battles (BOSS-16 at least), chapter gates; **Synergy lead voices** and **Octave Voice lines** (§5.2). Touches: combat_ensemble.md, bosses.md (silent flags), art_and_ui.
- **Korean gloss dependencies for barks** (§5.1): prologue_and_act1.md must let Min-jun count 하나, 둘, 셋 aloud, glossed, in CH-01; epilogues.md must have Jae-won gloss 얼쑤 and 좋다 when he joins and must gloss 오빠 and 엄마 at the reunion. The Hanmadi word 끝 (*kkeut*, "the end") is used as the sample swap; epilogues.md owns the full list of 40.
- **Lucile's hangul name 뤼실 오브레** (§7.2). Touches: epilogues.md, art_and_ui (hangul subset: 뤼, 실, 오, 브, 레), Korean localisation.
- **Romance and address rules** (§4.1, §7.5–§7.6): Lucile calls him "Kang" (French *vous*) while `g_fractured` and "Min-jun" again from Mending 2; Min-jun never calls her "Lumière"; she calls Sand "Aurore" in private; "love" is spoken between them only at Nohant (W3), once on the Night of Stars, and freely in the epilogues; at a kiss the text box closes. Touches: party.md, historical_cast.md, act2.md, act3.md, act4_and_epilogue.md, epilogues.md.
- **Starter SFX names** (§2.5), including `bond_chime` on `[BP:]` ≥ +15; audio_and_music.md owns the final list and may rename.
- **No real quotations** (§4 shared rules), with the five named sayings writers must not use. Touches: every writing doc; historical_notes_and_liberties.md may cite the rule.
