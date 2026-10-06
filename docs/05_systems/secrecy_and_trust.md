# Secrecy Meter & Trust Network

Status: v1.0 — 2026-10-06 · Owns: Secrecy and Spotlight per-event values, triggers, tiers and cabal-response rules; Trust Network BP sources, rank thresholds and unlocks; character preferences (topics, gifts); confession, Hint, Cover Story and Revelation rules; Lucile's hidden track (Confided lines, Early Truth, Fracture, Mending); Horizon event wording and the ending-determination rule (LAW-23) as applied · Depends on: none (canon only) · Related: docs/05_systems/salons_duels_and_economy.md (salon minigame; not yet published, CANON §11g governs) · Canon: docs/00_CANON.md

---

## Table of contents

1. [Design principles and ownership](#1-design-principles-and-ownership)
2. [The Secrecy Meter](#2-the-secrecy-meter)
3. [The Trust Network](#3-the-trust-network)
4. [Confession](#4-confession)
5. [The heroine's track](#5-the-heroines-track)
6. [Dialogue choice framework](#6-dialogue-choice-framework)
7. [Interactions between Secrecy and Trust](#7-interactions-between-secrecy-and-trust)
8. [Worked playthroughs](#8-worked-playthroughs)
9. [Canon Additions & Cross-Doc Notes](#canon-additions--cross-doc-notes)

---

## 1. Design principles and ownership

The two systems are the **Conceal** and **Befriend** verbs of the core loop (vision_and_pillars §4), and Horizon is **Choose**. They pull against each other on purpose: brilliance raises Secrecy (P3), friendship lowers it (confidants, Cover Stories), and the one person Min-jun most wants to trust is the one who reports him (A-2).

| Principle | Rule in play |
|---|---|
| **The city sees, friends feel.** | Every Secrecy cost is shown *before* the choice (candle glyph, Heat pips), with one deliberate exception: Lucile's reports, which are never flagged (CANON §11f). Bond and Horizon effects are never shown before a choice; BP is shown after it as note icons, Horizon never. |
| **Fail forward.** | No Secrecy or Trust outcome ends the game. The Unmasking is a mini-dungeon and a fine; losing a Close Call or a Hit costs only position. |
| **The ladder is the cabal's will; Secrecy is the city's attention.** | Rungs (CANON §4c) fire on schedule. Secrecy decides the systemic pressure *between* rungs and how the cabal justifies the next one (LAW-17). |
| **Gift, not theft.** | The future is the most persuasive thing Min-jun owns. Bite Your Tongue trades Secrecy for help, Trust or lives; it never trades it for profit (LAW-19). |
| **Her answer is grown.** | Horizon inputs are exactly the LAW-23 table. No system in this doc adds a Horizon input; this doc only words them and signposts them. |

**Ownership.** This doc owns every per-event value for Secrecy, Spotlight and BP, the tier consequences' implementation, the preference tables, the confession rules and the Horizon wording (CANON §0b). Canon values are reproduced exactly and cited; everything else is defined here. State-change tags are the CANON §16a set only.

---

## 2. The Secrecy Meter

### 2.1 Fiction and lifecycle

**Fiction (LAW-17, R-42).** The cabal already knows who Min-jun is (CANON §8 knowledge timeline). The meter measures how much of the future has leaked into public view: witnesses, press items, police reports, rumour. The cabal reads it as risk (M1 exposure in 1833, M2 the portal) and escalates; the Prefecture reads it as subversion. The tiers name the city's attention, not the cabal's knowledge.

| Phase | Chapters | State |
|---|---|---|
| Dormant | CH-P, CH-01 | No meter. Phone flashlight, slips and Mathurin's questions cost nothing. |
| Lit | CH-02 (first slip) | Meter starts at **0**; the scripted slip lights the candle (§2.4.7). |
| Full rules | CH-02–CH-09 | All tiers. Watcher effects of Murmured and Watched from **CH-06** only; before CH-06 those tiers apply only gossip, fees and the salon lock (CANON §11e). |
| On the road | CH-10–CH-11 | Capped at **99** (no Unmasking). CH-10 also floored at **60** (CH-09 lock). Regional equivalents of tier effects (§2.2). |
| Paris again | CH-12–CH-13 | Full rules; Unmasking by the Grey Hand. |
| Open war | CH-14 | **Police and public consequences only** (§2.2 last column); Unmasking by the Prefecture. |
| Snuffed | CH-15–CH-17 | Unmasking disabled (CANON §11e). The candle goes out on the crypt stair; no gains or losses are tracked. |
| Retired | CH-E1 / CH-E2 | Spotlight Meter (§2.10) / Canvas Ledger (CANON §4f). |

### 2.2 Tiers and consequences

Consequences are **cumulative** (a tier includes every effect below it unless superseded). Canon tier ranges and effects are binding (CANON §11e); the implementation columns are this doc's.

| Tier | Range | Canon consequence | Implementation | CH-10–CH-11 equivalent | CH-14 (police / public only) |
|---|---|---|---|---|---|
| **Incognito** | 0–19 | None | — | — | — |
| **Murmured** | 20–39 | Gossip; 1 Watcher per district map; salon fees +10% | Gossip: 1 in 3 town NPCs swaps a line for a rumour line (pool by chapter, scenario docs). Watcher from CH-06. Fee +10% applies to optional salons. | Gossip at inns only | Gossip and fee kept; no Watchers |
| **Watched** | 40–59 | 3 Watchers per district (sight cones); cabal **Shadow** encounters (1 in 8 overworld battles); one salon tier locked | Watchers and Shadow encounters from CH-06 (§2.8.2). **Locked tier = the highest optional salon tier currently unlocked**; T1 is never locked; story performances are never locked. | Shadow encounters on W02 (Hunter Automata) | Salon lock kept; no Watchers, no Shadow encounters |
| **Hunted** | 60–79 | Inn ambushes; encounter rate +25%; papers checks on 4 bridges (KEY-11 required); salon income −25% | Ambush roll per paid inn night: **33%** (25% at *Au Diapason Fêlé*, where Petit-Louis's warning makes it a preemptive battle). +25% to random-encounter rate on W01 and on district maps that have encounters; dungeons unaffected. Checkpoints: **Pont Neuf, Pont au Change, Pont Saint-Michel, Pont Royal**. Without KEY-11 (before CH-04) the guard turns the party back and they must cross elsewhere (the Pont des Arts charges its sou toll and asks no papers). | Ambushes at regional inns; **passport check** at the Aachen post (KEY-20) adds one Shadow encounter | Papers checks and income −25% kept; no ambushes, no encounter-rate rise |
| **Compromised** | 80–99 | One cabal **Hit** mini-boss per chapter (BOSS-41); Faubourg Saint-Germain shops refuse service; next story beat triggers a **Close Call** (win: −20) | Ambush roll rises to **50%**. Hit and Close Call per §2.9. Refusing shops: every shop in LOC-P14 (Vidal & Fils) and the high-tier relic counter at Curiosités Corbel. | Hit on W02 (BOSS-41 in its road setting); Close Call becomes a coach-yard escape | Shops refuse; **Close Call kept as a Prefecture chase**; **no Hit** (BOSS-41's window "up to CH-14" is read as through CH-13, see Canon Additions) |
| **Unmasked** | 100 | The Unmasking (CANON §11e) | Procedure in §2.9.3 | Impossible (cap 99) | Prefecture Unmasking (cells of LOC-P25) |

### 2.3 The gain formula

Every Secrecy **gain** (any positive value, including scripted `[SEC:+n]` tags, Heat, salon totals and Lucile's reports) is computed as:

**Gain = round_half_up( Base × Renown multiplier × (1 − 0.05 × confidants) )**

- **Renown multiplier** (CANON §11e): ×1.0 at Renown 0–249 · ×1.25 at 250–499 · ×1.5 at 500–749 · ×1.75 at 750–999. Read at the moment of the gain.
- **Confidants:** members who have received a confession (R10, or Lucile's Early Truth, §5.2.4). Maximum 7 (LU, BE, DE, AL, CH, LI, FA) = ×0.65. Julien never counts (he already knows).
- **Rounding:** once, at the end, half up (CANON §10).
- **Lowers are never multiplied.** `[SEC:-10]` is exactly −10.
- **Flat exceptions** (not multiplied): story locks (§2.6), the Unmasking reset, Gisquet's bail-out reset, and the Close Call loss (+10).
- **Bounds:** 0–100 (99 in CH-10–CH-11). A gain that would exceed 100 sets 100 and triggers the Unmasking.

*Example.* Renown 420, two confidants, a Heat 3 Recital before Onlookers: 3 × 1.25 × 0.90 = 3.375 → **+3**.

### 2.4 Trigger catalogue

#### 2.4.1 Battle: Onlookers and Heat

**Onlooker spawn table.** Onlookers are silhouettes at the top edge of the battlefield. While any remain, each **Anachronic** action adds its Heat (CANON §11e).

| Battle location | Onlookers |
|---|---|
| Paris district maps (T), day | 2 |
| Paris district night variants (P02, P04, P10, P16, P22, P24, P28) | 1 |
| Paris overworld (W01), day / night | 1 / 0 |
| Salons, embassies, LOC-P35, story battles staged before an audience | 3 |
| LOC-P08 barricade (BOSS-05 and its waves) | 3 |
| LOC-P13 Louvre galleries (copyists) | 2 |
| LOC-P27 Opéra: corridors / rafters / roof | 1 (stagehands) / 0 / 0 |
| Regional towns (R04, R06, R07, R10, R14) | 1 · Nohant (R03), Fontainebleau and the Vallée Noire: 0 |
| LOC-R08 *Concordia* | 2 (passengers) |
| All other dungeons and mini-dungeons | 0 |

**Departure.** Each Onlooker carries a 3-pip timer that loses one pip at the start of each turn of the party's slot-1 member (Min-jun when present); at 0 pips it leaves (= "flee after 3 turns"). **Clearing:** Berlioz's Brass Cue clears all; Delacroix's Sketch aimed at an Onlooker clears that one (no Study recorded); any enemy KO'd by a critical hit clears all (a scare).

**Heat table** (added once per action while ≥ 1 Onlooker remains).

| Action | Heat | Source |
|---|---|---|
| Future Recital piece (REP-01–25 with a Recital effect): added once when Movement I begins; Continue and CONDUCT add nothing | REP Heat 1–5 | CANON §15d |
| Min-jun's own works and period works (REP-00, REP-27–34) | 0 | CANON §15d |
| Lucile: IMPRESSION / POINTILLÉ / IMPASTO / LUMIÈRE | 2 / 3 / 4 / 2 (LUMIÈRE feeds Spotlight in CH-E1) | CANON §11e |
| Shift the Hour, Delacroix's Canvas, Tutti recipes, period Invocations (OPS-01–12) | 0 | — |
| ✦ Future Score Invocation (OPS-13–24) | 3 | CANON §11c |
| Secret Scores (OPS-25–32): 3 if the skills doc flags the Score as drawn from a future work, else 0 | 3 / 0 | this doc |
| Julien's Improvise (any reel result) | 3 | CANON §11e |
| Any party CHRONO action, including a CHRONO skill re-performed by Liszt's Transcribe | 5 | CANON §10c |
| Liszt's Transcribe of a Recital's Movement I | that REP's Heat | this doc |
| Synergy containing an Anachronic component: SYN-01 3 · SYN-02 3 · SYN-13 4 · SYN-14 3 · SYN-15 5 · SYN-16 5 · SYN-20 3 · all others 0 | as listed | SYN-15 canon; rest this doc |
| Cadenzas: MJ *Gaspard Unbound* 5 · LU *Lever du jour* 2 · JU *Changes* 3 · all others 0 | as listed | this doc |

*Synergy rule:* a Synergy's Heat is the highest Heat among its Anachronic components; Min-jun's part counts as the REP it is flavoured on (SYN-02 = REP-16), Lucile's part as IMPRESSION unless the Synergy names another style.

**Battle slip.** BOSS-07: reading the hidden formula aloud with copyists watching is a fixed **+15** (CANON §13).

#### 2.4.2 Salons

The salon minigame belongs to salons_duels_and_economy; its Secrecy cost is defined here and uses the canon formula (CANON §11g):

1. Raw = Σ over future pieces of **Heat × (1 + Cabal Presence) × attribution factor** (*name the composer* ×2; *an old teacher's piece* ×1; *my own* ×0.5, unavailable after the Vow).
2. Cap the raw total at **+20**.
3. Apply §2.3 (Renown, confidants, rounding).
4. Subtract **3 per piece attributed to "an old teacher"**, then **2 if the programme holds no future piece at all** ("period-only": REP-27–34 only).
5. A single salon's net result is never below **−6**.

Story performances ignore this formula and add only their scripted values (§2.4.7). Murmured raises optional salon fees by 10%; Hunted lowers salon income by 25%; Watched locks the top optional tier (§2.2).

#### 2.4.3 Speech: slips by audience

**Slip classes.** *Word*: a modern word or unit (any CANON §16g forbidden term, "kilometres", "photo"). *Name*: a future person, work or movement named in public (Debussy, Monet, "Impressionism", "jazz"). *Knowledge*: a fact from after 1833 stated as fact (germ theory, a technology, a coming event).

| Audience in earshot | Word | Name | Knowledge |
|---|---|---|---|
| Alone, or confidants only | 0 | 0 | 0 |
| Non-confidant party members only | 3 | 3 | 3 |
| Commoners (tavern, street, market, barge) | 3 | 4 | 5 |
| Artists and bourgeois (studios, workshops, shops, T1–T2 salons) | 4 | 6 | 7 |
| Society and officials (T3–T4 salons, embassies, Prefecture, Opéra, hospital staff) | 5 | 7 | 9 |
| Press or cabal in earshot (Heine, a journalist, Vane, a masked guest, a Watcher) | 6 | 8 | 10 |

**Modifiers.** *Abroad* (CH-10–CH-11, outside Paris): −2, minimum 3 (the Hour of Smoke's rumour mill is Parisian). *Covering Laugh*: a non-confidant at R6+ in the active party laughs the slip off, −2, minimum 3, once per slip (§3.3). **English** before Onlookers or any non-party NPC: flat **+5** (CANON §5f); English alone with Vane costs 0. Slip values therefore stay inside the canon range **+3 to +10**.

Slips reach the player three ways: **scripted slips** (story; §2.4.7), **slip options** in ordinary `[Q:]` choices (marked with the candle glyph and their value, §6), and **Bite Your Tongue** prompts.

**Bite Your Tongue register.** `[SLIP:3]` prompts: 3 seconds; on timeout Min-jun bites his tongue (the period phrasing plays). Modern phrasing costs **+5 to +15** and always buys a better outcome (CANON §11e). Cost guide: +5–6 commoners or artisans; +8 a life-saving fact; +10–12 officials, society or a cabal ear; +15 press and cabal together.

| Flag | CH | Where / who | Modern phrasing (label) | Cost | Period phrasing (label) | Modern outcome |
|---|---|---|---|---|---|---|
| `byt_boil_water` | CH-02 | LOC-P04, Mère Gaudin filling the stockpot | "Boil it. It's alive." | +8 | "Humour me: boil it?" | She boils every pot from then on; 2 Tisanes from her each chapter from CH-04; Petit-Louis escapes the autumn fever (scenario hook) |
| `byt_line_up` | CH-04 | LOC-P25, Gisquet and the paymaster sketch | "Show it to each alone." | +6 | "This man paid them." | Tissot is named the same day: `[GOLD:+100]` Prefecture reward; Berlioz `[BP:PC-03:+10]` |
| `byt_hand_guide` | CH-05 | LOC-P12, Kalkbrenner's guide-mains | "It hurts the tendons." | +6 | "I must decline, sir." | Chopin, overhearing, laughs aloud: Chopin's join BP +20 |
| `byt_nitinol` | CH-07 | LOC-P18, Alkan and the spring (shop clerk listening) | "Nickel and titanium." | +10 | "It remembers its shape" | `[BP:PC-05:+20]`; KEY-14 Almanach entry completed |
| `byt_sawdust` | CH-08 | LOC-P12 workshop, Théo (visiting with Lucile) coughing | "Dust scars the lungs." | +5 | "The air's too thick." | Pleyel promises that if the boy comes to him it will be to the finishing room, never the sawpit; `[BP:PC-02:+15]` |
| `byt_women_vote` | CH-10 | LOC-R03, Sand at dinner | "Women vote. And lead." | +12 | "Women hold us up." | Sand's farewell letter gains a line naming him an ally; Lucile's Unsent Letters bank +10 (§5.4) |
| `byt_handwash` | CH-12 | LOC-P26 hospital ward, a surgeon (Marthe present) | "Wash between beds." | +10 | "Humour a foreigner." | The ward adopts chlorinated hand-washing; Marthe gives 2 Panaceas; flag read by her CH-13 defection scene |
| `byt_sky_omnibus` | CH-14 | Hôtel de Ville, Rambuteau's dirigible-permit gag | "An omnibus in the sky." | +8 | "Just a balloon, sir." | Rambuteau signs the permit with a flourish; Liszt `[BP:PC-07:+15]` |

Scenario docs may add prompts using the cost guide; every prompt must keep a period phrasing that still lets the scene progress.

#### 2.4.4 Objects, places and field actions

| Trigger | Value | Rule |
|---|---|---|
| Seen with the phone (KEY-02) or student ID (KEY-03) | +10 | Scripted exposure checks only: CH-02 Petit-Louis lifts the "glass slate" (chase him to avoid it); CH-04 Gisquet asks for papers (showing the ID costs +10; letting Berlioz vouch costs 0). Confiscation during an Unmasking costs nothing. |
| Phone flashlight | +4 | Only if a Watcher is on screen; 6 uses CH-01–CH-13 (CANON §14). |
| Phone camera (CH-14) | +4 per photo | If any non-confidant is in frame or in the party (CANON §14). |
| Watcher sighting in a restricted zone | +3 | Once per map entry. Restricted zones: quarry access points (P02 rue Saint-Jacques hatch, P24 gypsum-quarry mouths, P28 scaffold yard), cabal properties (P18 shop rear court, P34 gate on rue de Varenne, Julien's café cellar door at P16), the Prefecture courtyard (P25). Overworld doc places the tiles (red-tinted at Murmured+). |
| Defeating a Watcher | +3 | Clears that map's Watchers for the rest of the chapter. |
| Dirigible take-off by day inside Paris | +2 | Night take-offs and take-offs outside the wall cost 0. |
| Transcription with a non-confidant in the active party | +3 | Per ✦ Score transcribed at a Lectern (CANON §11c). A confidants-only party transcribes free. |
| Field Talk topic *Tomorrow* with a non-confidant | +3 | §3.6. |

#### 2.4.5 Lucile's reports

Each confidence Min-jun shares with Lucile during CH-05–CH-08, up to the charity concert of Sat 21 Sep 1833, adds **+8** at chapter end, silently, through the §2.3 formula (CANON §11f). Confidences shared after the Early Truth cost nothing. Register in §5.2.2.

#### 2.4.6 Reckless Confession

Telling the truth to a non-party NPC: **+25**, nothing gained, once per NPC (CANON §11f). List in §4.6.

#### 2.4.7 Scripted Secrecy register

Story values are fixed; they pass through §2.3. Story performances always name the composer.

| CH | Event | Value |
|---|---|---|
| CH-02 | First slip at the tavern: "that's Debussy's *Suite bergamasque*" (Name, commoners) | +4 |
| CH-02 | *Clair de lune* (REP-01) on the pianino; Berlioz hears it | +3 |
| CH-03 | "Ondine" (REP-08) at Salon Lavergne, Sat 27 Apr | +10 |
| CH-03 | Rung 3: "The Mandarin Mimic" in *Le Corsaire* (CANON §4c) | +10 |
| CH-04 | *Arabesque No. 1* (REP-02) at the tavern, first meeting with Lucile | +2 |
| CH-04 | Riot frame-up, Wed 5 Jun | Lock ≥ 40 (§2.6) |
| CH-05 | Opening: name cleared in the press | Lock max(current − 20, 20) |
| CH-05 | *Jeux d'eau* (REP-11) in the Pleyel showroom | +3 |
| CH-06 | Lucile's *Le Pont Royal, effet de brume* in Corbel's window (Ingres sees it) | +2 |
| CH-06 | CONF CH06-01 "Seoul" (reported at chapter end) | +8 |
| CH-07 | The Thalberg duel, Sat 7 Sep (either result; the embassy hushes it) | +6 |
| CH-08 | Charity concert, Salle Pleyel, Sat 21 Sep | +8 |
| CH-09 | *Ma mère l'Oye* (REP-13) four hands with Liszt at the wedding supper | +4 |
| CH-09 | End of chapter | Lock ≥ 60 (§2.6) |
| CH-10 | Prelude for the Left Hand (REP-20) at Nohant | +2 |
| CH-11 | "Madame Schu— Mademoiselle Wieck" (R-18) | +5 |
| CH-11 | *Doctor Gradus* (REP-04) for Czerny | +3 |
| CH-12 | "Le Gibet" (REP-09) for Archon; Archon's Revelation | 0 (cabal only) |
| CH-13 | *Concerto "Lost Era"* (REP-27) at the Opéra | 0 (Heat 0) |
| CH-14 | "Scarbo" (REP-10) for Vane; Night of Stars on the Panthéon roof | 0 (private) |

Lucile's later public showings (BQ-PC02 parts, SQ-20) add the Heat of their style (IMPRESSION 2, POINTILLÉ 3, IMPASTO 4) as scripted values (LAW-21).

### 2.5 Decay and recovery

| Lower | Value | Limit | Rule |
|---|---|---|---|
| Passive decay | −1 per 10 min of field play | −6 per chapter | Timer runs on Paris district maps and W01 only; pauses in menus, dialogue, battles and dungeons. Never outside Paris. |
| Inn night | −1 | −5 per chapter | Any paid rest, including *Au Diapason Fêlé*; each also spends an Evening (CANON §11i); applied after an ambush is won. |
| *An old teacher's piece* | −3 per piece | — | §2.4.2 step 4 |
| Period-only programme | −2 | per salon | §2.4.2 step 4 |
| Cover Story | −10 | once per chapter per confidant | §4.7 |
| Press rebuttal (Heine, or Maison Farrenc) | −10 | once per chapter (either source, not both) | 500 F; from CH-05 |
| SQ-04 "Ink and Counter-Ink" | −15 | once | On completion, CH-05–CH-09 |
| Close Call won | −20 | once per chapter | §2.9.1 |
| Julien's Counter-Rumour | −10 | once (CH-14) | Requires PC-11 at R7+; he plants the last rumour the Hour of Smoke ever spreads |
| Unmasking | set to 60 | — | Gisquet's bail-out sets 65 (§2.9.3) |

Lowers cannot push Secrecy below an active story floor (§2.6).

### 2.6 Story locks

| When | Lock | Duration |
|---|---|---|
| CH-04, the pamphlet planted at the riot | Secrecy = max(current, 40) | Floor of 40 until CH-05 opens |
| CH-05 opening (acquittal printed) | Secrecy = max(current − 20, 20) | One-time |
| End of CH-09 | Secrecy = max(current, 60) | Floor of 60 through CH-10 |
| CH-10–CH-11 | Cap 99 | Whole chapters |
| CH-14 | Police and public consequences only | Whole chapter |
| CH-15 onward | Snuffed | Rest of the main game |

### 2.7 UI

| Element | Spec |
|---|---|
| **Candle** (HUD top-right on Paris maps, CANON §16h) | 16 × 32 px sprite on a brass base. Flame by tier, coded by **height and motion** as well as colour (§11j): Incognito small white-gold, steady · Murmured flickering · Watched tall amber with a smoke wisp · Hunted red-orange, wax running · Compromised guttering, red halo pulsing at 1 Hz · Unmasked flares white, then blows out (cutscene). |
| **Exact value** | Hold Select on any field map, or open Status: the number 0–100 and the tier name appear on the brass base. |
| **Gains / losses** | Gold "+n" rises 8 px over 30 frames; blue "−n" sinks. Tier up: one low bell stroke (V7 sting) and the tier name on the base for 90 frames. Tier down: a soft two-note chime. |
| **Silent gains** | Lucile's report gains are applied during the next chapter's opening caption: the candle is visible and simply grows, with no "+n" and no sound (§5.2.2). |
| **Variants** | CH-10–CH-11: the candle sits in a carriage-lantern frame. CH-14: the brass base shows the Prefecture's seal (police and public only). CH-15: snuffed on the crypt stair, a smoke curl, then hidden. CH-E1: Spotlight bar. CH-E2: Canvas Ledger. |
| **Battle HUD** | Onlooker silhouettes stand at the battlefield's top edge, each with a 3-pip timer. In RECITAL, PLEIN AIR, Opus and Synergy menus every Anachronic entry shows Heat as 1–5 candle pips; with Onlookers present the pips turn red and the projected gain ("+4") is printed beside the entry. |
| **Dialogue** | Any option that raises Secrecy carries the 8-px candle glyph and its value before selection (§6). |
| **Salon programme screen** | Shows the projected Secrecy of the chosen programme as a range (best and worst Cabal Presence) before the performance. |
| **Almanach** | Press items and Intercepted Notes (§2.8.2) file under "Gazette", in period voice. |

### 2.8 The cabal's response

#### 2.8.1 Coupling rules

1. **Rungs fire on schedule.** No Secrecy value delays, skips or advances a rung of CANON §4c.
2. **Secrecy sets the pressure between rungs** (systemic events, below) and the **stated reason** for the next rung (the tier box, §2.8.4).
3. **Unsanctioned spikes mirror the ladder.** As with rungs 5, 8 and 10, the Compromised Hit is Brücke acting without Archon; the next tier box shows Archon's rebuke.
4. **From CH-14 the cabal is at open war.** Their attacks are story battles; Secrecy then governs only police and public consequences.

#### 2.8.2 Response by tier

| Tier | The city's attention | The cabal's reading (A-1) | Systemic response | Whose hand |
|---|---|---|---|---|
| Incognito | A foreigner who plays well | The Velvet Leash works; Vane's soft faction ascendant | None | — |
| Murmured | Café rumour | M1, low: the Hour of Smoke watches | 1 Watcher per district (CH-06+) | Julien's informants (to CH-08); Grey Hand (CH-09+) |
| Watched | His name in salons and print | M1 rising; Archon sanctions surveillance | 3 Watchers per district (CH-06+); Shadow encounters 1 in 8 overworld battles (CH-06+); top salon tier locked | Black Coats (CH-06–08); Grey Hand (CH-09+); Hunter Automata (W02) |
| Hunted | Police interest; papers asked for | M1 + M2: frighten him away from the quarries and the door | Inn ambushes; encounter rate +25%; bridge checks; salon income −25% | Ambush roster below |
| Compromised | Open scandal: the future could be noticed by history | Brücke's private escalation; Archon rebukes | Hit (BOSS-41); Faubourg Saint-Germain shops refuse; Close Call | Brücke (Hit); Prefecture or Grey Hand (Close Call) |
| Unmasked | Seized | CH-02–08 and CH-14: subversion (Prefecture). CH-09–13: SIG (the Grey Hand try to make him play for a hidden horn) | The Unmasking (§2.9.3) | Prefecture / Grey Hand |

**Encounter rosters** (families from CANON §8 and §12; the bestiary assigns ENM numbers). Each won Shadow encounter files one of 12 **Intercepted Notes** in the Almanach (cabal correspondence in period voice; flavour only).

| Band | Shadow encounter (Watched+, CH-06+) | Inn ambush (Hunted+) | Watcher battle |
|---|---|---|---|
| CH-02 | — | Julien's café toughs ×3 | — |
| CH-03–CH-05 | — | Black Coats ×3 | — |
| CH-06–CH-08 | Black Coats ×2 + 1 Watcher | Black Coats ×2 + Brücke Mk. I automaton (from CH-07) | Watcher + 1 café tough |
| CH-09, CH-12–CH-13 | Grey Hand ×3 | Grey Hand ×3 | Grey Hand lookout + 1 Grey Hand |
| CH-10–CH-11 | Hunter Automata ×2 (river automata on the Rhine) | Hunter Automata ×2 | — |
| CH-14 | None | None | None |

All human foes are routed or subdued, never killed (CANON §16e); none is Prefecture, octroi or National Guard (CANON §12).

#### 2.8.3 The Hit (BOSS-41)

- **Sender:** always **Brücke**, never sanctioned ("Brücke wants him dead from the first day", CANON §8). **CH-02–CH-05:** the automaton runs a *retrieval* setting (it goes for the phone and the student ID: Brücke wants proof, and is not yet sure this is the Kang of his dossier). **CH-06–CH-13:** *lethal* setting, after the "Seoul" report confirms him (rung 8).
- **Trigger:** on reaching Compromised, each later district or overworld map load rolls 25%; the 4th load is guaranteed. Once per chapter. Not in CH-14 or after.
- **Result:** a normal boss battle (wipe → Retry or Return, CANON §11a). It does not change Secrecy. Archon's rebuke appears in the next tier box.

#### 2.8.4 Tier boxes

Each chapter's existing cabal scene (or, where a chapter has none, a ≤ 6-box interlude at chapter end) carries **one tier box**: 1–3 boxes chosen by Secrecy at that moment. Low = 0–39, Mid = 40–79, High = 80–99. After an Unmasking, the next tier box is replaced by a line about the seizure. Gists (the scenario docs write the lines):

| CH | Scene and speakers | Low | Mid | High |
|---|---|---|---|---|
| CH-02 | Julien reports "the Oriental pianist" to Vane (rung 1) | A tavern curiosity with three dead keys | He names composers nobody in Paris has heard of | Half the faubourg hums his tunes; Julien asks for men |
| CH-03 | Vane, certain after "Ondine", wins Archon's approval for the Leash (rung 2) | Vane: a discreet man can be kept | Delorme: let the press laugh at him first (rung 3) | Brücke: every week he plays, the record grows; Archon refuses him, for now |
| CH-04 | Vane decides on the frame-up (rung 5, unsanctioned) | He frets the boy is becoming beloved | A hero of the wrong cause is a finished cause | The Prefecture already keeps a file; Vane panics |
| CH-05 | Vane's patronage offer to Min-jun, in English (private) | Vane praises his discretion: Paris rewards it | Paris is talking; Vane offers to steer what it says | Half the city wants to hear him, the other half a magistrate |
| CH-06 | Brücke and Vane after the word "Seoul" arrives | Hiding changes nothing: he is the Kang | (sample below) | (sample below) |
| CH-07 | Vane and Brücke rig the duel (rung 7) | Humiliate him gently: a lesson | Humiliate him publicly: a disgraced man is not believed | Brücke: disgraced, then silenced. Vane refuses to hear it |
| CH-08 | Julien and Brücke over the Pleyel tensioner (rung 8) | Julien: just make it break | Julien: break it before the concert, the city loves him | Julien leaves; Brücke alone resets the specification |
| CH-09 | Archon orders the abduction (rung 9) | Record him before anyone notices him | Record him before the city does | Record him tonight; the city is already listening |
| CH-10 | Brücke dispatches the automata (rung 10). Floor 60: Low unused | — | Out of Paris, out of sight: good for knives | The roads talk too; finish it in the Berry |
| CH-11 | Delorme and Marthe as Théo is taken (rung 11) | The girl will come for the boy | ...and he will come for the girl | ...and the whole Rhine heard him on the way |
| CH-12 | Archon's Audience: one line inside the Offer (rung 12) | Archon admires his care | Paris has begun to say his name | Paris says his name in every café; Archon can make it stop, if he stays |
| CH-13 | Roussel briefs his riflemen (rung 13) | The hall will watch the stage | The hall came for him; keep to the rafters | The whole hall came for him; let it look at the stage |

**Sample: CH-06, Mid and High** (Brücke and Vane, rue de la Paix, after midnight).

```
[MUS:LM-05]
[IF:sec_high]
[P:ANA-05:angry] Seoul. And the whole
faubourg humming his
tunes. He is the Kang.[W]
[/IF]
[IF:sec_mid]
[P:ANA-05:neutral] Seoul. He said it to
the girl himself.
He is the Kang.[W]
[/IF]
[P:ANA-02:neutral] He's a boy at a piano,
Brücke. Not a war.[W]
[P:ANA-05:neutral] A boy at a piano
is how wars are
remembered.[W]
```

*`sec_low`, `sec_mid` and `sec_high` are engine flags set from the meter when the scene loads (§6.1).*

### 2.9 Fail states and recovery

#### 2.9.1 Close Call

- **Trigger:** when a story beat (a scripted chapter scene) begins with Secrecy ≥ 80, a Close Call plays first. Once per chapter. CH-02–CH-08 and CH-14: Prefecture agents. CH-09, CH-12–CH-13: the Grey Hand. CH-10–CH-11: a coach-yard escape from Hunter Automata.
- **Rules:** a 90-second chase on the current district map. Pursuers use CH-01 sight cones; being seen starts a 5-second pursuit that ends at the nearest checkpoint lamp, as in CH-01. Reach any safe door: *Au Diapason Fêlé* (P04), Delacroix's studio (P06), Maison Farrenc (P19, from CH-05), the Alkan house (P36, from CH-04), Chopin's apartment (P11, from CH-06), Belgiojoso's salon (P39, CH-14); on the road, the party's inn. No battle (CANON §12).
- **Win:** −20. **Caught** (timer expires): **+10 flat**, which may trigger the Unmasking. The story beat then plays either way.

#### 2.9.2 Compromised shops

Every shop in LOC-P14 and Curiosités Corbel's relic counter show "*Monsieur is not received.*" until Secrecy falls below 80. Lower-tier shops elsewhere always sell.

#### 2.9.3 The Unmasking

| Step | Rule |
|---|---|
| Trigger | Secrecy reaches 100. Fires at the next safe moment: the end of the current battle or scene, or the next map load. Never inside a dungeon (fires on exit), a boss battle or a story set piece. If no safe moment remains in the chapter, it fires at the first safe moment of the next chapter, with that chapter's captor. |
| Captor | Prefecture: CH-02–CH-08 and CH-14 (cells of LOC-P25). Grey Hand: CH-09–CH-13 (the Bercy safe house, reusing the P25 layout, with a phonautograph horn in the cell). Impossible in CH-10–CH-11 (cap 99) and from CH-15. |
| Escape | Escape mini-dungeon, boss **BOSS-42 The Turnkey** (scales to party average, CANON §13). Min-jun starts alone with his baton; the party joins at the first door (the friends broke in, or bribed a turnkey). |
| Costs | −10% of francs (rounded half up to the sou). One random roster member −20 BP ("questioned"): eligible are members present in the chapter, below R10, with unfrozen BP (confidants and R10 friends are spared; if none is eligible, no loss). |
| Reset | Secrecy set to **60** (flat). |
| Gisquet's bail-out | **Once per game**, at the first Prefecture Unmasking from CH-05 on (Gisquet has known Min-jun since CH-04): **Accept** = released by the back stair, no dungeon, no francs or BP lost, Secrecy set to **65**; **Refuse** = escape as normal. Gisquet's leverage is Archon's (R-28): the next tier box shows Archon learning of it. |
| Never | A game over, a lost item, a lost save, a skipped story beat. |

### 2.10 Spotlight Meter (CH-E1) and Canvas Ledger (CH-E2)

**Spotlight Meter** (CANON §11e): press and online attention on Lucile, 0–100, HUD bar top-right in Seoul. Gains are flat (no Renown, no confidants).

| Tier | Range | Consequence (canon in bold, implementation after) |
|---|---|---|
| Quiet | 0–24 | — |
| Trending | 25–49 | **Phone-camera crowds slow movement**: walk speed −25% on Seoul town maps while Lucile is in the party |
| Headline | 50–74 | **Reporters block some streets**: the east end of the Deoksugung Stonewall Road (S03), Insadong's main lane (S12) and Hongdae's busking street (S07) close; side alleys detour |
| Viral | 75–99 | Lucile cannot paint in public (field painting prompts greyed: "Not with a hundred phones watching."); Céline's lawyers' offer becomes available |
| 100 | — | **Forced press scrum** (fail-forward): a scripted run through the nearest subway station, Jae-won running interference; Spotlight set to **50** |

| Raise | Value | Lower | Value |
|---|---|---|---|
| "Missing student returns" news (scripted) | +10 | Det. Oh's statement (scripted) | −15 |
| Lucile paints in public | +5 + style Heat | Céline's lawyers (once, Viral only) | −20 |
| Battle with Onlookers (Seoul town maps: 2 phone-camera bystanders): Lucile's style | its Heat (LUMIÈRE 2) | Passive decay: 10 min of field play in Seoul | −1 (max −6 per story beat) |
| Busking with Lucile present | +3 | A night at the Kang apartment | −2 (max −6 in CH-E1) |
| Paying with 1833 coins in public | +3 | | |
| Lucile reads her own canvas's label aloud at LOC-S06 (scripted) | +5 | | |
| Jae-won posts a busking clip with Lucile in frame (optional; gives a Hanmadi word) | +5 | | |

**Canvas Ledger (CH-E2).** The Secrecy slot becomes the Ledger of Lucile's 19 surviving canvases (CANON §4f). No Secrecy, Onlookers or Heat exist in CH-E2; future pieces are greyed at salons ("Not mine to play.", LAW-25).

### 2.11 Tuning targets

Chapter-end Secrecy for three reference styles (worked in §8). Playtests that fall outside these bands by more than 10 points for two chapters trigger a values review.

| Chapter | Careful (period programmes, cleared crowds, rebuttals) | Median | Reckless (name the composer, public bursts, every modern phrasing) |
|---|---|---|---|
| CH-02 | 0–5 | 2–10 | 15–25 |
| CH-03 | 10–20 | 12–25 | 35–55 |
| CH-04 | 40 (lock) | 40 (lock) | 45–70 |
| CH-05 | 10–25 | 25–40 | 55–80 |
| CH-06 | 10–25 | 30–45 | 70–100 (first Unmasking likely) |
| CH-07–CH-08 | 5–25 | 40–85 | 75–95 |
| CH-09 | 60 (lock) | 60–80 | 70–95 |
| CH-10–CH-11 | 58–65 | 60–75 | 70–99 |
| CH-12–CH-13 | 10–45 | 25–45 | 30–60 (second Unmasking likely in CH-12) |
| CH-14 | 0–10 | 0–20 | 30–50 |

---

## 3. The Trust Network

### 3.1 Bond Points and ranks

Each bonded member (PC-02–PC-08, PC-11) holds **0–1000 BP** with Min-jun (CANON §11f). Seo-yeon and Jae-won have no ranks.

| Rank | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 | R9 | R10 |
|---|---|---|---|---|---|---|---|---|---|---|
| BP | 0 | 50 | 120 | 200 | 300 | 420 | 550 | 690 | 840 | 1000 + bond-quest finale |

**Rules.**
1. **Ranks never fall.** A member's rank is the highest threshold ever reached. BP can drop (minimum 0) and must climb back past the *next* threshold to rank up. The only displayed drop is Lucile's Fracture cap (§5.4).
2. **R10 needs both** 1000 BP and the bond-quest finale (for Lucile, BQ-PC02 part 6, the Night of Stars). BP stops at 1000; a member at 1000 without the finale shows **R9 ★** ("the finale awaits").
3. **Lucile's Noon gate:** her BP cannot pass **549** until BQ-PC02 part 3 (Noon) is complete. This makes the canon tuning target exact (R7 by CH-08 requires parts 1–3, §5.2.3). The Bonds menu says so: "Rank 7 awaits: The Hours of Light — Noon."
4. **Guaranteed bonds:** BQ-PC04's and BQ-PC06's mandatory finales (CH-09) set Delacroix's and Chopin's BP to 1000 and grant R10. The Night of Stars (CH-14) sets Lucile's BP to 1000 and grants R10 (CANON §11f).

### 3.2 BP sources

| Source | Value | Limit | Notes |
|---|---|---|---|
| Battle in the active party | +1 | +30 per member per chapter | Guests and reserve earn none |
| Fixed story events | per member, §3.4 | — | `[BP:]` in story scenes |
| Story-scene dialogue choices | +5 to +20 | as scripted | Never shown before choosing |
| Bond-quest steps | +40 to +100 | §3.5 | |
| Evening scene | +15, plus one choice worth +5 / +10 / +20 | §3.6 counts | Costs one Evening |
| Field Talk (one topic) | Beloved +15 · Liked +10 · Neutral +5 · Disliked 0 | once per member per chapter | No Evening |
| Gift | Favourite +25 (first time each; repeats +5) · Liked +15 (first time; repeats +5) · Neutral +5 · Disliked 0, gift returned | one gift per member per chapter | No Evening |
| Ensemble Scene | +15 to each participant | once per scene | Both participants R4+; costs one Evening |
| Lucile's lessons L1–L4 | +10 for either option | 4 | Horizon per LAW-23 |
| Lucile's Window Talks | +20 | 4 | Horizon W2 |
| Lucile's Confided lines | Share +15 · Keep it light +5 | 9 opportunities, §5.2.2 | Share adds the +8 report |
| Bite Your Tongue outcomes | as listed in §2.4.3 | — | Modern phrasing only |
| Early Truth | +40 | once | §5.2.4 |

### 3.3 What each rank unlocks

| Rank | Unlock | Source |
|---|---|---|
| R1 | Field Talk (topics T1–T4, T6, T8–T11); gifts; Evening scene 1 | this doc |
| R2 | **Personal topics** T5 Home, T7 Love, T12 Tomorrow | CANON §11f |
| R3 | **Duo Synergy with Min-jun** (SYN-01–07) | CANON §11b, §11f |
| R4 | The Bonds menu shows the member's **Notes** page (Beloved topic, one Liked gift, one Disliked gift); **Ensemble Scenes** eligible | this doc |
| R5 | **Signature** Harmony skill (LU *Effet de brume*, BE *Chœur d'ombres*, DE *La Barque de Dante*, AL *Les Omnibus*, CH *Étude en ut mineur*, LI *Harmonies poétiques*, FA *Air russe*, JU *Modal Vamp*) | CANON §11f |
| R6 | **Covering Laugh**: while this member is a non-confidant in the active party, a slip costs −2 (minimum 3; one cover per slip; the highest-ranked eligible member covers) | this doc |
| R7 | **Cadenza** (from CH-09; members already at R7 gain it in CH-09) | CANON §11d |
| R8 | **Trio eligibility**; the **Hint** at −20 BP (Lucile: R6 at −20) | CANON §11f |
| R9 | Hint free (Lucile: R7); bond-quest **finale** may start | CANON §11f; this doc |
| R10 | **Confession** ("Tell the truth"), **command upgrade** (canon examples: Chopin's *Tempo Rubato*, Delacroix's LIGHT pigment; the rest per skills_and_progression), **Kindred dialogue** (CH-14 Kindred Evenings, extended CH-17 farewells, battle banter); **Lost Era** weapon eligibility (CANON §14) | CANON §11f, §14 |

### 3.4 Join BP and fixed story events

Members who join late start higher, as late joiners arrive at higher levels (CANON §5). In Da Capo, join BP = max(listed value, 50% of that member's final BP in the finished run; CANON LAW-23.6).

| Member | Join BP (when) | Fixed story events (chapter: value) | Total fixed incl. join |
|---|---|---|---|
| PC-02 LU | 50 (CH-05; banked from CH-04: first meeting +20, the paymaster sketch +30) | CH-05 joins +30, Pont des Arts dawn lesson +30 · CH-06 first canvas +30, birthday rain study +30 · CH-08 roof kiss +40 · CH-13 eight bars +40 · lessons and Window Talks per §3.2 · CH-14 Night of Stars → 1000 | 250 before CH-14 (plus lessons, Talks) |
| PC-03 BE | 50 (end CH-02) | CH-03 letter of introduction +20 · CH-04 barricade, first name, baton +50 · CH-05 Marie Moke-Pleyel scene +10 · CH-09 leaves his wedding to lead the rescue +80 · CH-12 rejoins +20 · CH-13 conducts the concerto +30 · CH-14 30th birthday, Wed 11 Dec +30 | 290 |
| PC-04 DE | 50 (CH-03) | CH-03 35th birthday, Fri 26 Apr +20 · CH-04 barricade +40 · CH-06 Lucile's canvas in his studio +20 · CH-09 BQ-PC04 finale → 1000 | 130 before CH-09 |
| PC-05 AL | 120 (end CH-04) | CH-07 the nitinol springs +40 · CH-09 the rescue +20 · CH-12 20th birthday, Sat 30 Nov +30 · CH-13 the rafters +30 | 240 |
| PC-06 CH | 120 (CH-06) | CH-07 back from Touraine for the duel +30 · CH-08 the restored Pleyel concert +50 · CH-09 BQ-PC06 finale → 1000 | 200 before CH-09 |
| PC-07 LI | 120 (CH-07) | CH-09 *Le jardin féerique* with Min-jun +30 · CH-10 the tour +50 · CH-10 rides in for BOSS-13 +20 · CH-11 interprets on the Rhine +30 · CH-13 second piano +80 · CH-14 Hiller's concert +10 | 340 |
| PC-08 FA | 200 (CH-08) | CH-10 decodes the ledger +40 · CH-11 the Seventh Panel recovered +20 · CH-13 the corridors +20 · CH-14 the Vow +40 · SQ-07 family council +40 (when done) | 360 |
| PC-11 JU | 550 (CH-14, SQ-21) | CH-15 Party 3, Orpheus +30 (if placed there) | 580 |

### 3.5 Bond quests

**Standard bond quest** (BQ-PC03 *Idée Fixe*, BQ-PC05 *The Railway Étude*, BQ-PC07 *Transcendence*, BQ-PC08 *The Treasury*, BQ-PC11 *A Tune of My Own*): four parts and a finale.

| Step | Opens at | BP |
|---|---|---|
| Part 1 | R2 | +40 |
| Part 2 | R4 | +60 |
| Part 3 | R5 | +60 |
| Part 4 | R7 | +80 |
| Finale | R9 | +100 |
| **Total** | | **340** |

Windows are canon (CANON §0c); BQ-PC07's finale is BOSS-36 in CH-14 only, so Liszt's R10 (and confession) can only happen in CH-14. If the quests doc stages a quest in a different number of parts, the opening part pays +40, the finale +100 and the middle parts share the remaining 200.

**Mandatory bond quests** (BQ-PC04 *The Colours of Algiers*, BQ-PC06 *Żal*): story-placed, no rank gates. Part 1 +40, part 2 +60, part 3 +80, finale (CH-09) sets 1000 and R10.

**BQ-PC02 *The Hours of Light*** (sequential; none can be played while Lucile is Fractured):

| Part | Opens at | BP | Note |
|---|---|---|---|
| 1 Dawn | R3 | +50 | From CH-05 |
| 2 Morning | R4 | +60 | From CH-05 |
| 3 Noon | R5 | +70 | From CH-05; lifts the Noon gate (BP earned above 549 before Noon is lost) |
| 4 Afternoon | R6 | +80 | From Mending 2 (CH-12) |
| 5 Dusk | R7 | +90 | From Mending 2 |
| 6 Night | scripted, CH-14 | sets 1000, R10 | The Night of Stars |

**BQ-PC02b *A Harbour of Her Own*** (CH-14): +60 BP.

### 3.6 Evenings, Evening scenes and Field Talk

**Evening scenes** cost one Evening (CANON §11i: CH-02 2 · CH-03 3 · CH-04 2 · CH-05 4 · CH-06 4 · CH-07 4 · CH-08 2 · CH-09 1 · CH-10 2 · CH-11 1 · CH-12 1 · CH-13 0 · CH-14 unlimited). Scene *n* needs rank R*n*; one scene per member per Evening. On the road (CH-10–CH-11) scenes play at inns with whoever travels. Scenes beyond R10 play as **Kindred** scenes (no BP).

| Member | Evening scenes | Haunt |
|---|---|---|
| LU | 6 (plus 6 BQ-PC02 parts, 4 lessons, 4 Window Talks) | P20 attic; P22 quays |
| BE | 8 | P04 tavern (to CH-09); P10 boulevard café (CH-12+) |
| DE | 6 | P06 studio |
| AL | 8 | P36 house |
| CH | 6 | P11 apartment |
| LI | 8 | P10 Boulevards, Tortoni's |
| FA | 8 | P19 Maison Farrenc |
| JU | 4 | P16 Palais-Royal (CH-14) |

**Field Talk.** Once per member per chapter, from the Bonds menu (Talk) on any town map: pick one topic.

| ID | Topic | Opens | Covers |
|---|---|---|---|
| T1 | The Craft | R1 | Music of the day, technique, rivals |
| T2 | Colour | R1 | Painting, light, the Salon |
| T3 | Society | R1 | Salons, gossip, who sat with whom |
| T4 | The Street | R1 | Politics, the poor, the barricades |
| T5 | Home | R2 | Birthplaces, families, exile |
| T6 | Faith | R1 | God, Scripture, the soul |
| T7 | Love | R2 | Love, marriage, longing |
| T8 | Machines | R1 | Inventions, engines, clockwork |
| T9 | Money | R1 | Fees, debts, prices |
| T10 | Poets | R1 | Books, theatre, poetry |
| T11 | Fame | R1 | The press, reviews, reputation |
| T12 | Tomorrow | R2 | Dreams of the music and art to come. **Secrecy +3 with a non-confidant** (slip, party-only audience); free with confidants and Julien |

With Lucile in CH-05–CH-08, T5 Home and T12 Tomorrow open a Confided-line choice (§5.2.2).

### 3.7 Preferences

**Topics.**

| Member | Beloved (+15) | Liked (+10) | Disliked (0) and why |
|---|---|---|---|
| LU | T2 Colour | T5 Home, T10 Poets (Sand's novels) | T9 Money: the 1,200 F debt is a stone in her pocket |
| BE | T10 Poets (Shakespeare, Goethe, Virgil) | T7 Love (Harriet), T12 Tomorrow (orchestras of a thousand) | T9 Money: generous with money he does not have |
| DE | T2 Colour | T10 Poets (Byron, Dante), T1 Craft (Mozart) | T8 Machines: he distrusts "progress" |
| AL | T8 Machines | T6 Faith (Scripture), T1 Craft (Bach) | T7 Love: painfully shy; he opens the psalter |
| CH | T5 Home (Poland, exile) | T1 Craft (his mimicry of other pianists), T3 Society | T4 The Street: Warsaw fell while he waited in Stuttgart |
| LI | T12 Tomorrow (a seeker) | T6 Faith, T4 The Street (the poor, the Saint-Simonians) | T11 Fame: everyone speaks to him of Liszt; he would rather hear of you |
| FA | T9 Money (fees, equal pay) | T1 Craft, T5 Home (Victorine) | T3 Society: salon flattery that never seats a woman composer |
| JU | T1 Craft | T3 Society (the cafés), T12 Tomorrow | T11 Fame: his fame is stolen |

**Gifts.** Favourites are canon (CANON §11f); the items doc creates every ITM entry (UI names ≤ 16 characters, CANON §16h).

| Member | Favourites (+25) | Liked (+15) | Disliked (0, returned) |
|---|---|---|---|
| LU | Prussian Blue · Indiana (Sand) · Valencia Oranges | Madder Lake (Couleurs Ravenel) · Hot Chestnuts (quay vendor, P22) · Spinning Top (for Théo; Curiosités Corbel) | Painted Fan (she paints forty a week) · Snuffbox |
| BE | Faust (Nerval) · Shakespeare (En) · Orchestra Paper | Guitar Strings (Schlesinger's) · Aeneid (Virgil) · Hamlet Playbill (the 1827 Odéon troupe; bouquinistes) | Rossini Score · Hair Pomade |
| DE | Moroccan Silk · Byron's Poems · English Paints | Dante's Inferno · Throat Lozenge (the existing consumable; his hidden ailment) · Mozart Score | Ingres Print · Mechanical Toy |
| AL | Hebrew Psalter · Automaton Bird · Bach WTC Edition | Watch Movement (Curiosités Corbel) · Railway Print (the Saint-Étienne line) · Black Tea | Theatre Tickets · Ball Invitation |
| CH | Parma Violets · Polish Gazette · Kid Gloves | Gingerbread (Toruń, which he praised as a boy) · Silk Cravat · Bach Fugues | Kalkbrenner Book · Military March |
| LI | Rosary · Cigar Box · Paganini Sheet | Lamartine Poems · Tokaji Wine · Le Globe Issue (the Saint-Simonian paper) | Metronome (to him, time is a suggestion) · Pocket Mirror |
| FA | Engraver's Burin · Couperin Edition · Victorine's Gift | Haydn Quartets · Account Ledger · Quill Knife | Conduct Manual (a manual of feminine deportment) · Perfume Flask |
| JU | Naples Coffee · Metronome (Maelzel's) · Song Sheet | Bass String · Staff Paper · Absinthe | Laurel Wreath · Fan Letter |

Every other gift is Neutral (+5).

### 3.8 Losses

| Loss | Value | Rule |
|---|---|---|
| Hint at R8 (Lucile at R6) | −20 | §4.2 |
| Archon's Revelation, member present at R7 or below | −50 | §4.5; Lucile exempt |
| Unmasking ("questioned") | −20, one random eligible member | §2.9.3 |
| Disliked gift | 0 (returned; uses that chapter's gift) | §3.7 |
| Fracture | BP frozen, rank capped | §5.4 |

### 3.9 Budget proof

All bonds can be maxed in one run (CANON §11f). Dedicated play below = every bond-quest part, the Beloved topic each chapter, three favourite and three liked gifts, about 10 battles a chapter in the active party, and the Evening scenes shown. Casual = no bond quest, random topics, two gifts, one Evening scene.

| Member | Dedicated BP by start of CH-12 (Revelation needs R8 = 690) | Dedicated BP by end of CH-14 | Casual BP by end of CH-14 |
|---|---|---|---|
| BE | 865 (3 Evening scenes) → finale possible before CH-12 | 1000 (R10) | 520 (R5) |
| AL | 764 (no Evening scene needed) | 1000 | 494 (R5) |
| LI | 714 (2 Evening scenes) | 1000 (finale in CH-14) | 580 (R6) |
| FA | 694 (2 Evening scenes) | 1000 | 560 (R6) |
| JU | — (joins CH-14) | 1000 with 4 Evening scenes | 640 (R7) |
| CH, DE | 1000 at CH-09 (guaranteed) | 1000 | 1000 |
| LU | Fractured until CH-12; §5 | 1000 (Night of Stars) | 1000 |

CH-14's unlimited Evenings let a player who rationed badly catch up on scenes; only timing (Duos, Signatures, Cadenzas, the Revelation, Liszt's CH-14-only finale) is truly rationed.

---

## 4. Confession

### 4.1 The rule

| Item | Rule |
|---|---|
| Availability | "Tell the truth" appears in a member's Talk menu only at **R10**; below that it is greyed: "Not yet." (CANON §11f). Sole exception: Lucile's Early Truth (§5.2.4). |
| Cost | One Evening (free in CH-14, whose Evenings are unlimited). Scripted confessions cost nothing. |
| Who | Scripted: Chopin and Delacroix (CH-09), Lucile (CH-14 unless the Early Truth came first). Optional: Berlioz, Liszt, Farrenc, Alkan. Julien already knows (no confession). Seo-yeon already knows; Jae-won is told in CH-E1 (story). |
| Confidant perks | Octave +10% each; Secrecy gains −5% each; one Cover Story per chapter; the member's Cadenza gains its second phase; a confidant star on the Bonds page; Kindred farewell in CH-17 (CANON §11b, §11d, §11f). |
| The Lantern Rule | Every confession from CH-09 obeys LAW-18: tell friends who I am, never when they die. Legacy may be told; death never. |
| After Archon's Revelation | A confession not yet made plays as **"The Truth, from You"**, with every perk (CANON §11f). |

### 4.2 The Hint

A preview of a member's reaction to the truth, offered once per member from the Talk menu: −20 BP at R8, free at R9 (Lucile: −20 at R6, free at R7). The reaction always names what is still missing, so the Hint doubles as a signpost to the bond-quest finale. Julien is never offered it.

```
[P:PC-01:neutral] What if I came from very
far away… in time?[W]

[P:PC-03:grandiose] Then you'd be the one
man in Paris my music
was written for![W]
[P:PC-03:smile] Tell me properly when
my Idée Fixe is laid to
rest.[W]

[P:PC-04:smile] Then you'd be the most
interesting sitter I was
ever refused.[W]
[P:PC-04:neutral] Ask me again when the
Algiers canvas is dry.[W]

[P:PC-05:deadpan] Ecclesiastes says there
is nothing new under the
sun.[W]
[P:PC-05:deadpan] I always suspected him
of rounding. Finish the
railway piece with me.[W]

[P:PC-06:ironic] In time? Then you know
how my ballade ends.[W]
[P:PC-06:sad] Don't tell me. I must
find it alone.[W]

[P:PC-07:rapture] Then I want to hear
everything, mon ami![W]
[P:PC-07:neutral] But not yet. Not until
I have faced my ghost.[W]

[P:PC-08:neutral] Then you'd owe me a very
precise account.[W]
[P:PC-08:smile] Bring it when the
Treasury is safe.[W]

[P:PC-02:guilty] Then you'd be very far
from home.[W]
[P:PC-02:tender] ...Tell me when you're
sure of me.[W]
```

Lucile's guilty portrait on her Hint is deliberate: on a first run it reads as shyness, on a second as the report she will have to write.

### 4.3 Scripted confessions

| Who | When and where | Trigger | Cue | Beat that must land |
|---|---|---|---|---|
| Chopin | CH-09, LOC-P11 | BQ-PC06 *Żal* finale sets R10 | REP-12 *Pavane* (CANON §15d) | He asks; Min-jun answers, "You will be played every day for two hundred years." The Lantern Rule is born (LAW-18). He pledges to help find the door and keep the secret. |
| Delacroix | CH-09, LOC-P06 | BQ-PC04 finale (*Women of Algiers*) sets R10 | LM-12 | He sketches an emblem for each friend (the Door's panels, LAW-22 clue). |
| Lucile | Early Truth (CH-06–CH-08) or CH-14, the Panthéon roof | §5 | LM-22 → LM-30 | Without the Early Truth, the Revelation told her; the roof plays "The Truth, from You". |

### 4.4 Optional confessions

| Who | Available | Where | He / she asks | Min-jun's answer (Lantern Rule) | What only this scene gives |
|---|---|---|---|---|---|
| Berlioz | CH-03–CH-09, CH-12–CH-14 (absent CH-10–CH-11) | P04 tavern, or P10 café from CH-12 | Will France understand him? | Not for a long time; then the whole world will (his canon arc, CANON §5d). | He swears to conduct the future only under its makers' names: the scene that seeds the Vow's "credit" clause. |
| Alkan | CH-05 | P36, at the pedal piano | Nothing about himself | Silence on his withdrawal and on the railway piece (LAW-18, BQ-PC05) | The only confession that ends in a laugh. |
| Farrenc | CH-08 | P19, after hours, among the plates | Does anyone play her music in 2026? | Forgotten, then found again (LAW-18). If the scenario docs have already placed this exchange elsewhere, she asks instead what women earn in 2026. | Her resolve to fight harder; the bar-line holds. |
| Liszt | CH-14 only (BQ-PC07 finale is BOSS-36) | P10, Tortoni's after closing | To hear the future, though not his own: that he will write himself | He plays him Debussy, never Liszt's own future work (LAW-16) | Always "The Truth, from You": the Revelation always reaches him first. |

**Sample: Alkan** (P36, late; the house asleep).

```
[MUS:LM-16]
[P:PC-01:neutral] Charles-Valentin. I'm
not from Corée the way
you think. From 2026.[W]
[P:PC-05:deadpan] I see.[D:60][W]
[P:PC-05:deadpan] Does the Sabbath still
fall on Saturday?[W]
[P:PC-01:smile] It does.[W]
[P:PC-05:smile] Then the important
things survived. Play
me something from it.[W]
[FLAG:confidant_pc05]
```

**Sample: Farrenc** (P19).

```
[MUS:LM-15]
[P:PC-08:neutral] Then tell me something
useful. In 2026, does
anyone play my music?[W]
[P:PC-01:sad] For a long time, no.
You were forgotten.[W]
[P:PC-01:smile] Then they found you
again. They play you
in concert halls now.[W]
[P:PC-08:determined] Forgotten.[D:30] Then I
shall make it very
difficult for them.[W]
[FLAG:confidant_pc08]
```

### 4.5 Archon's Revelation (CH-12)

Archon tells everyone present what Min-jun is (CANON §11f). Present: LU, BE, DE, LI, FA, AL (Chopin is in bed with bronchitis and is already a confidant).

| Member state at the Revelation | Reaction | Effect |
|---|---|---|
| Confidant (DE always; BE, AL or FA if told) | Steps beside him before Archon finishes | None |
| R8 or higher | "Tell us yourself, when you are ready." | None |
| R7 or lower | Hurt. Gists: Berlioz would have kept it for him and was not allowed to; Liszt would have believed him, and that is what wounds; Farrenc keeps accounts and this one is short; Alkan keeps silences well and was not trusted with this one | **−50 BP** |
| Lucile | Exempt | If no Early Truth, this is how she learns |

The confession stays open afterwards as "The Truth, from You". The Revelation is the system's teaching moment: confessing early pays.

### 4.6 Too early, too late, wrong person

| Case | What happens |
|---|---|
| "Tell the truth" below R10 | "Not yet." No cost. |
| The Hint at R8 | −20 BP; the friend feels tested. Free one rank later. |
| Confiding (not confessing) in Lucile, CH-05–CH-08 | +15 BP and **+8 Secrecy**, reported, and read back to the player in CH-09 (§5.2.2). The trap of the game, and fair: the shadowed purse (CH-03) and her own POV scene (CH-07) are on screen first. |
| The Early Truth to Lucile (R7, CH-06–CH-08) | Rewarded: never reported, later confidences free, Horizon W1 +15, a milder Fracture. |
| Too late: Archon's Revelation | −50 BP for members at R7 or below. |
| Never | An optional member never told gives no Octave bonus and a shorter CH-17 farewell; the keepsake is still given (CANON §6). |
| Wrong person: a **Reckless Confession** | **+25 Secrecy**, nothing gained, once per NPC. |

**Reckless Confession NPCs** (each has "Tell the truth" in its talk menu during the window; the option is marked with the candle glyph and "+25"):

| NPC | Window | What happens |
|---|---|---|
| FIC-02 Mère Gaudin | CH-02–CH-14 | Feels his forehead, sends him to bed, and tells the whole tavern as a joke by supper. |
| FIC-03 Petit-Louis | CH-02–CH-14 | Delighted; sells the story to a café for two sous. The Hour of Smoke buys it. |
| FIC-04 Corbel | CH-04–CH-09 | Goes grey and shuts the shop early; the cabal's frightened dead drop passes it on. |
| ANA-06 Sœur Marthe | CH-07–CH-12 | Tells him very quietly never to say that aloud again, least of all here. Her waiting room heard it. |
| NPC-30 Heine | CH-05–CH-14 | Finds a man from the future who chooses to be poor in Paris too absurd to believe, and runs a column on the "Nightingale of Nowhere" that week. |
| NPC-14 George Sand | CH-10 (Nohant) | She does not believe him, and if she did she would have to write it; she tells Lucile he is more of a poet than she feared. |

### 4.7 Cover Stories

A confidant's once-per-chapter event: **−10**, from the Bonds menu on any town map, a 3–6 box vignette, no Evening. Greyed at Incognito ("Nothing to hide yet.") and while the confidant is absent.

| Confidant | Available | Vignette |
|---|---|---|
| Chopin | From CH-09; absent CH-10 and CH-12 | At a salon he mimics "the Corean pianist" so absurdly that the rumour becomes a joke. |
| Delacroix | From CH-09; absent CH-10–CH-11 | Takes Min-jun to the Opéra and introduces him all evening as a provincial bore; the gossip dies of tedium. |
| Lucile | CH-12–CH-14 only: she will not lie to the city for him until she has stopped lying to him, and not while Fractured | Paints a fan of a mournful foreigner at a piano; it sells out at Corbel's and makes the "Mandarin Mimic" look harmless. |
| Berlioz | From his confession; absent CH-10–CH-11 | Announces a festival of a thousand musicians in the press; Paris forgets the Corean to laugh at Berlioz. |
| Liszt | CH-14 (after his confession) | Improvises at Belgiojoso's until dawn; the morning papers speak only of Liszt. |
| Farrenc | From her confession | Has Aristide print a dull notice listing Min-jun as an arranger for Maison Farrenc; a boring fact beats an exciting rumour. |
| Alkan | From his confession | Tells the Conservatoire that the glowing slate someone saw was part of his metronome prototype, and answers every follow-up question with Scripture. |

**Sample: Chopin.**

```
[N:Salon Guest] They say the Corean plays
music from the moon. Or from
the devil. Nobody agrees.[W]
[P:PC-06:ironic] From the moon? Allow
me.[SFX:piano_hit][D:40][W]
[P:PC-06:ironic] Like this, yes? All
elbows and comets.[W]
[N:Salon Guest] Ha! Then he is merely
dreadful. What a relief.[W]
[SEC:-10]
```

---

## 5. The heroine's track

### 5.1 Timeline

| Phase | When | Her secret | Trust rules | Secrecy link | Horizon inputs (LAW-23) |
|---|---|---|---|---|---|
| Recruited | CH-03, Sun 28 Apr | Vane's agent; not yet met | — | — | — |
| Met | CH-04, Thu 9 May | Her sketch, meant as a report, saves him | 50 BP banked | — | — |
| Reporting | CH-05 → Sat 21 Sep (charity concert) | Weekly letters filed as "Lumière" (CANON §8d) | Normal BP; Noon gate; Confided lines | **+8 per shared confidence**, chapter end, silent | L1, L2, Early Truth |
| Turned | 21 Sep → CH-09 night | False report; steals the ledger to save him | Normal | Nothing more is reported | — |
| Revealed | CH-09 dawn | Julien's bundle (KEY-18); she confesses everything | **Fracture** | End-of-chapter lock ≥ 60 | — |
| Fractured | CH-10–CH-11 | Nohant; Théo seized; she goes alone | BP frozen; cap; Unsent Letters bank | — | WT1, Nohant answer, Sand's counsel, L3, Corot |
| Mended | CH-12 (Mending 2) → CH-14 | Rejoins for good | Normal BP; Duos | Her Cover Story | WT2; then in CH-14: L4, WT3, SQ-11, SQ-12, SQ-13, BQ-PC08, SQ-07 |
| Night of Stars | CH-14, Wed 18 Dec | — | R10 | — | — |
| Labyrinth | CH-15 | — | — | Snuffed | W4, WT4 |
| The Question | CH-17 | — | — | — | Final words |

### 5.2 Before the reveal

#### 5.2.1 Tuning

Canon target: R7 by the end of CH-08 requires BQ-PC02 parts 1–3 and most optional Lucile scenes; the default path reaches R5–R6 (CANON §11f).

| Source, CH-04 to CH-08 | Default path | Dedicated path |
|---|---|---|
| Banked, join and fixed events (§3.4; the CH-08 kiss included) | 210 | 210 |
| Lessons L1, L2 | 20 | 20 |
| Battles | 45 | 60 |
| Confided lines in mandatory scenes (CH05-01, CH08-01) | 20 | 30 |
| Field Talk, four chapters | 25 | 52 |
| Gifts | 15 | 90 |
| Evening scenes 1–3 | 25 | 90 |
| BQ-PC02 parts 1–3 | 0 | 180 |
| **Total** | **360 (R5)** | **732 (R8)** |

Without parts 1–3 the Noon gate holds her at 549 (R6) however much else is done; with parts 1–3 and no optional scenes she ends near 515 (R6). Both halves of the target are needed.

#### 5.2.2 Confided lines

A Confided line is a small, true thing Min-jun chooses to share: never the whole truth. Each is a `[Q:]` with **Share** (+15 BP, `[CONF:CH##-##]`, +8 Secrecy at chapter end) and **Keep it light** (+5 BP). Shared lines before the Early Truth and before the 21 Sep concert are reported. In CH-09 Julien's bundle (KEY-18) reads back each reported line: Min-jun's own spoken words, then her sentence. Her reports also hold **observation entries** (whom he met, his quarry searches, which feed rung 6); those cost nothing, because they are the cabal's knowledge, not the city's (LAW-17).

| CONF | Scene | What he shares | Her sentence in the report (KEY-18) |
|---|---|---|---|
| CH05-01 | CH-05 Pont des Arts dawn lesson (mandatory) | His father tunes pianos for a living | "His father tunes pianos. He laughed when he said it, as if it were a secret." |
| CH05-02 | CH-05 Evening scene 1 | A sister who plays the violin and says he plays too loud | "He has a sister, a violinist. He misses her. He did not say so." |
| CH05-03 | CH-05–CH-08 Field Talk T5 Home | He is looking for a way home, "a door" | "He speaks of a door. He says the word as if it were a person." |
| CH06-01 | CH-06 lesson L1, Pont Royal (**scripted, no choice**; 0 BP) | The name of his city: Seoul | "His city is called Seoul. I have written it as he spelled it." |
| CH06-02 | CH-06–CH-08 Field Talk T12 Tomorrow | In his city the night is never dark | "He says that in his city the night is never dark. He is homesick, or mad." |
| CH06-03 | CH-06 Evening scene 2 | He has never finished a piece of his own | "He has never finished a work of his own. He says the music he plays belongs to other men." |
| CH07-01 | CH-07 lesson L2, Tuileries (an aside after the lesson choice) | He hears music no one has written yet | "He says he hears music no one has written yet. I believe him. That is the worst of it." |
| CH07-02 | CH-07 Evening scene 3 | His mother will still be setting a place for him | "His mother sets a place for him at table. He says so every time it rains." |
| CH08-01 | CH-08 Pleyel workshop, before the concert (mandatory) | If he found the door, he does not know if he would go | "He does not know whether he would go through his door." Her false report of 21 Sep twists it: "He has given up any door." |

CH06-01 is always reported: it is how Brücke confirms the Kang of his dossier (CANON §8). The Early Truth window therefore opens only after L1. Maximum reported: 9 lines, +72 base Secrecy.

#### 5.2.3 R7

R7 needs 550 BP **and** BQ-PC02 part 3 (Noon) (§3.1). At R7 her Hint is free and, in CH-06–CH-08, the Early Truth appears.

#### 5.2.4 The Early Truth

| Item | Rule |
|---|---|
| Window | R7, CH-06 (after lesson L1) to the end of CH-08 (CANON §11f) |
| Where | "Tell the truth" in her Talk menu (one Evening). **Roof variant:** if she is R7 on the Salle Pleyel roof after the CH-08 kiss, the scene offers it as a `[Q:]` at no Evening cost, the last chance. |
| Effects | `[BP:PC-02:+40]`, `[HZ:W1]` (+15). She becomes a confidant (Secrecy gains −5%). She never writes it down; every later confidence costs nothing. Fracture cap −1 instead of −3. At the reveal: "I never told them. Not that." Her Cover Story still waits for CH-12 (§4.7). |
| What she does not do | Confess her own errand in return. She lies about her errand, never her feelings (CANON §16f); the guilty portrait says the rest. |

```
[MUS:LM-22]
[P:PC-01:tender] Lucile. The place I come
from isn't far away.
It's far ahead.[W]
[P:PC-01:neutral] Two hundred years ahead.
I was born in 2003. I
came through a door.[W]
[P:PC-02:surprised] ...[D:60][W]
[P:PC-02:guilty] You shouldn't tell
anyone that. Not even
me. Especially me.[W]
[P:PC-01:smile] Too late.[W]
[P:PC-02:tender] Then it stays here.
Between us. Not one
word of it on paper.[W]
[BP:PC-02:+40][HZ:W1][FLAG:early_truth]
```

### 5.3 The reveal (CH-09)

| What | Effect |
|---|---|
| The reports | Every reported Confided line read back verbatim, in the player's own words (KEY-18). With the Early Truth, the last page ends on her line above. |
| Secrecy | No change at the reveal; the end-of-chapter lock (≥ 60) applies. |
| BP | Frozen at its current value. |
| Rank | Capped at max(rank − 3, 2); with the Early Truth max(rank − 1, 2). Cracked heart on the Bonds page. |
| Locked | Duos with Min-jun (SYN-01); BQ-PC02 parts; Ensemble Scenes with her; her Cover Story. |
| Kept | Learned skills, her Signature, her Cadenza (if earned). Rank-gated access above the cap is suspended. |
| Horizon | Unchanged. Forgiving fast or slow feeds Horizon only through the LAW-23 inputs that follow; neither is punished (CANON §16f). |
| Sketchbook | KEY-09 enters Min-jun's inventory; its last page is frozen until Mending 1. |

### 5.4 Fracture, Mending and the Unsent Letters

| Event | Cap | BP | Also |
|---|---|---|---|
| Fracture, CH-09 dawn | as §5.3 | Frozen | — |
| **Mending 1**, CH-10 Nohant | +2 | Frozen | The Sketchbook page updates again |
| CH-11 interlude | — | — | She acts alone: no BP, no bank |
| **Mending 2**, CH-12, under Mignard's dome (KEY-24) | +2 | **Unfrozen; bank paid** | Duos unlock; BQ-PC02 parts 4–5 open; her Cover Story |
| Night of Stars, CH-14 | R10 | 1000 | Confession or "The Truth, from You"; SYN-13 |

**The Unsent Letters bank.** Everything she would have earned while frozen (battles, Window Talk 1's +20, L3's +10, gifts, Field Talk, the `byt_women_vote` +10) is banked at **50%**, rounded half up at payout, and paid at Mending 2 with one Bonds-menu line: "She kept writing." Nothing done for her during the Fracture is wasted; it is held, like her letters.

*Example.* R6 at 480 BP, no Early Truth: cap 3 → Mending 1 cap 5 → Mending 2 cap 7. Banked 70 → +35 → 515 BP, shown R6 (cap 7).

### 5.5 Horizon inputs and their wording

Values are LAW-23's, unchanged. Labels are ≤ 22 characters; the full line is spoken after selection (CANON §16a).

| Input | When and who asks | Labels | Full line spoken | Value |
|---|---|---|---|---|
| Lessons L1–L4 | CH-06, 07, 10, 14; Lucile at her easel | "Tell of tomorrow" / "Ask what she sees" | Canon lines (LAW-23.2) | W7 +3 / R1 −5 |
| Early Truth | CH-06–CH-08 | "Tell the truth" | §5.2.4 | W1 +15 |
| Sand's counsel | CH-10, Nohant, the fallout talk. Sand: some women need wings and some need roots; she says Paris needs her, and dares him to say she is wrong | "Paris needs her." / "Ask her, not me." / "She isn't Paris's." | "You're right. Paris needs her." / "Ask her. Not me, not you." / "She isn't Paris's. Or mine." | R3 −10 / 0 / 0 |
| Nohant answer | CH-10, Sand, later that night: did he love Lucile, or the girl Vane wrote for him? | "I loved your rain." / "I don't know any more" | "I loved the woman who painted rain." / "I don't know any more. I'm trying to." | W3 +10 / 0 |
| Corot's invitation | CH-10, Fontainebleau: Corot asks her to Italy next spring | "Go. Paint with him." / "Spring is far off." | "Go. Paint with him in spring." / "Spring is a long way off." | R6 −5 / 0 |
| Window Talks 1–4 | §5.5.1 | — | — | W2 +5 each |
| Party 2 | CH-15, Lucile in Party 2 through the Seoul amalgam zones | Party select | — | W4 +5 |
| BQ-PC08 finale | CH-14, Lucile in the active party | — | — | W5 +5 |
| SQ-07 complete | Step 5, CH-14 family council (KEY-31) | — | — | W6 +10 (and the gate) |
| SQ-11, SQ-12, SQ-13 | CH-14 (SQ-13 from CH-12) | — | — | R2 −15, R4 −10, R5 −5 |
| Final words | CH-17, the Question | "Beside me, there." / "Whatever you choose." / "Who you become here." | "I want you beside me — there." / "Whatever you choose, I'm yours." / "I want to see who you become here." | +5 / 0 / −5 |

#### 5.5.1 Window Talks

| WT | Place and cost | Her question | What the scene does |
|---|---|---|---|
| 1 | Nohant, by Sand's fireside, frost on the window over the Berry fields (CH-10, one Evening; BP banked) | What would he write if no one ever heard it? | The first honest talk since the bridge; she answers her own question with the Berry fields she is painting in points |
| 2 | Val-de-Grâce, under Mignard's dome, after Mending 2 (CH-12, one Evening) | What does the sky look like over his city? | He tells her Seoul's sky is orange and starless; she promises him stars, which seeds the Night of Stars |
| 3 | The Panthéon roof, before she paints (CH-14, mandatory) | Where would he hang this painting, if he could hang it anywhere? | Closing line by band (§5.7) |
| 4 | The last amalgam zone, at the Heart-gate Lectern after the merge (CH-15, optional: speak to her) | With W4: what she saw in his city. Without: what the Door sounds like | The last quiet before the Heart |

### 5.6 The ending rule

Binding (LAW-23.4), evaluated when the Question fires (1:30 left on the Window Clock, CANON §11i):

1. **Gate.** If SQ-07 is incomplete, the answer is **NO**, and her first words are "I will not leave Théo with nothing."
2. **Total** = Horizon (frozen as the Question begins; clamped −100…+100, practically −65…+77) + final words (+5 / 0 / −5).
3. **Total ≥ +1 → YES** (CH-E1). **Total ≤ 0 → NO** (CH-E2). A tie at 0 is NO.

Because W6 (+10) is the gate's own reward, every YES includes it. The final-words menu always appears, even when the result is already fixed; the words are always spoken. Reverie of the Window plays the opposite answer (LAW-23.6).

### 5.7 Reading the signs

**The Sketchbook (KEY-09), the only gauge** (LAW-23.5). Viewable at her invitation from her Talk menu in CH-05–CH-08, and from the Sketchbook menu after the CH-09 handover; recomputed each time it opens.

| State | Last page |
|---|---|
| SQ-07 incomplete (any Horizon) | **Théo asleep under a blanket.** Since step 5 happens only in CH-14, this is the page for most of the game: her anchor, in pencil. |
| Horizon ≤ −30 | Paris rooftops with Théo |
| −29…−5 | The Pont des Arts at dawn |
| −4…+5 | An unfinished page (the only band where the final words can still decide) |
| +6…+29 | A ship on a horizon |
| ≥ +30 | "Towers of glass in snow", imagined from his stories |
| CH-09 handover → Mending 1 | Frozen on its last state |

**Sand's farewell letter** (delivered Thu 12 Dec, CH-14, as Lucile returns from the Lyon mail-coach; filed in the Almanach). The band paragraph uses Horizon at delivery.

```
[N:Sand's Letter] Kang —
It is five in the morning,
the coach is stamping, and
Alfred is sulking. So: brief.[W]
[IF:gate_unmet]
[N:Sand's Letter] Théo first. Always Théo.
She will not leave that boy
with nothing: not for you,
not for heaven. Settle him.[W]
[N:Sand's Letter] A master, a guardian, a seal
on paper. Then ask her
anything you like.[W]
[/IF]
[IF:gate_met]
[N:Sand's Letter] You have made Théo safe. I
know what that cost. So does
she. Thank you, my friend.[W]
[/IF]
[IF:hz_band_5]
[N:Sand's Letter] She asks me what snow looks
like on towers of glass. I
told her to ask you. She has
wings now. Mind them.[W]
[/IF]
[IF:hz_band_4]
[N:Sand's Letter] She talks of harbours and
horizons, and pretends it is
about painting. Is it?[W]
[/IF]
[IF:hz_band_3]
[N:Sand's Letter] She has not decided. Neither
have you, I think. Your last
words will matter, Kang.
Choose them; don't recite.[W]
[/IF]
[IF:hz_band_2]
[N:Sand's Letter] She paints the bridges as if
she means to sign them all.
Paris has its hooks in her.
Good hooks.[W]
[/IF]
[IF:hz_band_1]
[N:Sand's Letter] Her roots go down to the
quarries, that girl. She
belongs to these rooftops,
and they to her.[W]
[/IF]
[IF:byt_women_vote]
[N:Sand's Letter] You told me women vote where
you come from. I have decided
to behave as if they did.[W]
[/IF]
[N:Sand's Letter] Be good to ma petite Lumière.
If you are not, I will write
a novel about you, and it
will sell. — G.[W]
```

**Window Talk 3's closing line** (the Panthéon roof; `gate_unmet` overrides the bands).

```
[IF:hz_band_5][P:PC-02:smile] Tell me again about
the towers of glass.[W][/IF]
[IF:hz_band_4][P:PC-02:tender] I keep painting ships.
Isn't that strange?[W][/IF]
[IF:hz_band_3][P:PC-02:neutral] Ask me on the day.
I'll know on the day.[W][/IF]
[IF:hz_band_2][P:PC-02:smile] Look at the bridges.
Every one of them is
mine.[W][/IF]
[IF:hz_band_1][P:PC-02:tender] Théo will be a master
here. I want to see it.[W][/IF]
[IF:gate_unmet][P:PC-02:worried] Théo still coughs at
night, you know.[W][/IF]
```

**Other tells** (fiction, never gauges):

| Tell | Rule |
|---|---|
| SQ-07 worry icon | Lucile's worry icon marks SQ-07 on the map CH-07–CH-14 (LAW-23.1). |
| Crypt-door prompt | Lists SQ-07 by title if unfinished (CANON §0c). |
| Victory quote (CH-12 on) | One of six by band, owned by the style guide: band 5 wonders whether the light is like this in his city; band 4 counts dawns; band 3 paints first and thinks later; band 2 tells Paris it is worth it; band 1 would know these rooftops blindfolded; gate unmet says Théo would have liked that. |
| The Question's music | In band 3 the final-words menu holds LM-01's C♯ unresolved under the choice (audio doc). |

The lessons carry no tell: both options are written with equal warmth (LAW-23).

### 5.8 Reverie and Da Capo

- **Reverie of the Window:** no meter, no BP change; loads at CH-17's first free frame after BOSS-28 and plays the opposite answer (LAW-23.6).
- **Da Capo (NG+):** carries 50% of each member's BP (join BP = max(listed, carried), §3.4); ranks are recomputed from carried BP; confidant flags, Confided lines, the Early Truth, the bank, Horizon and Renown reset; Secrecy relights at 0 in CH-02; the Sketchbook last page works as a compass from CH-05 (Théo still overrides until SQ-07).

---

## 6. Dialogue choice framework

### 6.1 Choice types

| Type | Script | Presentation | Timer | On timeout | Typical effects |
|---|---|---|---|---|---|
| Standard choice | `[Q:a\|b]` or `[Q:a\|b\|c]` | 2–3 labels ≤ 22 characters; the full line is spoken after selection | None | — | `[BP]`, `[FLAG]`, `[HZ]`, `[OV]`, `[SHD]` |
| Slip option | `[Q:]` with one option carrying `[SEC:+n]` | Candle glyph and "+n" after that label | None | — | `[SEC]` (§2.4.3 matrix value) |
| Bite Your Tongue | `[SLIP:3][Q:modern\|period][/SLIP]` | Timer bar under the box; modern label first, with candle glyph and "+n" | 3 s | Period phrasing | `[SEC]` plus the outcome |
| Confided line | `[Q:share\|keep light]` (labels written per scene) | **No glyph**: the cost is hidden, because she reports it | None | — | `[BP]`, `[CONF]` |
| Horizon choice | `[Q:]` | No glyph, no hint; equal warmth | None | — | `[HZ]` |
| Reckless Confession | NPC talk menu "Tell the truth" | Candle glyph and "+25" | None | — | `[SEC:+25]` |

Branches are written in docs as →1, →2, →3 under the `[Q:]` line (authoring notation, stripped at build). Engine flags read by `[IF:]` and never shown: `sec_low`, `sec_mid`, `sec_high`; `hz_band_1`…`hz_band_5` (≤ −30, −29…−5, −4…+5, +6…+29, ≥ +30); `gate_met`, `gate_unmet`; `early_truth`; `confidant_pc02`…`confidant_pc08`; every `byt_*` flag of §2.4.3.

### 6.2 What the player sees

| Value | Before a choice | After a choice | Readable where |
|---|---|---|---|
| Secrecy | Candle glyph and value (except Confided lines) | "+n" / "−n" on the candle | HUD candle; exact value on Select or Status |
| Heat | Candle pips; projected gain when Onlookers are present | "+n" on the candle | Battle menus |
| Bond Points | Never | 1–3 note icons over the member's portrait (+5–9, +10–19, +20 or more); a cracked note for a loss; a grey note while frozen; nothing for 0 | Bonds menu: exact BP, rank, next threshold, Notes page from R4 |
| Horizon | Never | Never | The Sketchbook's last page only |
| Confided lines | Never | Never | Read back in CH-09 (KEY-18) |
| Shadow, Own Voice | Never | Never | Felt in BOSS-31/34 and the CH-13 cadenza |
| Renown | Salon screen forecast | Popup | Status |

### 6.3 Authoring rules

1. Labels ≤ 22 characters; spoken lines obey CANON §16a (3 × 24 with a portrait, 4 × 30 without; ≤ 6 boxes per speaker).
2. At most 3 options. A bond choice that pleases no one carries no `[BP]` tag (dialogue choices pay +5 to +20 or nothing; the only BP losses are §3.8's).
3. A choice may tag several members; only members present in the scene receive BP.
4. Slip options use the §2.4.3 matrix; Bite Your Tongue uses its cost guide (+5 to +15); every prompt keeps a period phrasing that lets the scene progress.
5. Horizon choices are written with equal warmth, never framed as right or wrong, and never placed beside a bond-heavy option that would telegraph a "correct" answer (LAW-23 lesson rule).
6. `[HZ]` takes only a LAW-23 ID; `[SEC]` values are always pre-multiplier; lowers are written negative (`[SEC:-10]`).
7. Lucile's scenes in CH-05–CH-08 must offer the Confided lines of §5.2.2 where listed, and no others.

### 6.4 Sample: a Confided line (CH-05, Lucile's Evening scene 1, her attic)

```
[MUS:LM-03]
[P:PC-02:smile] Who taught you to play?
Someone patient, I hope.[W]
[Q:My mother. My sister.|A teacher, long ago.]
→1 [P:PC-01:homesick] My mother taught me. My
sister plays violin. She
says I play too loud.[W]
   [BP:PC-02:+15][CONF:CH05-02]
→2 [P:PC-01:smile] A teacher, long ago.
She'd hate my posture.[W]
   [BP:PC-02:+5]
[P:PC-02:tender] ...[D:30] Play me
something quieter, then.[W]
[EVE:-1]
```

The player sees two notes or one over her portrait. Nothing else happens until the next chapter's caption, when the candle grows by 8 and no one says why.

---

## 7. Interactions between Secrecy and Trust

| Interaction | Direction | Rule |
|---|---|---|
| Confidants dampen gains | Trust → Secrecy | −5% per confidant on every gain, up to −35% (§2.3) |
| Cover Stories | Trust → Secrecy | −10 per confidant per chapter (§4.7) |
| Confidants-only party | Trust → Secrecy | Transcriptions and *Tomorrow* talk cost nothing |
| Covering Laugh | Trust → Secrecy | A non-confidant at R6+ in the active party: slips −2 (minimum 3) |
| Confiding in Lucile, CH-05–CH-08 | Trust ↔ Secrecy | +15 BP buys the R7 she needs, and costs +8 Secrecy she reports |
| The Early Truth | Trust → Secrecy | Ends the report cost; makes her a confidant |
| Bite Your Tongue | Secrecy → Trust | The modern phrasing buys bonds: Alkan +20, Chopin +20, Lucile +15, Liszt +15, Berlioz +10 |
| *Tomorrow* topic | Secrecy ↔ Trust | Liszt's Beloved, Berlioz's and Julien's Liked, at +3 Secrecy unless they are confidants |
| The Unmasking | Secrecy → Trust | −20 BP to one random member below R10 |
| Archon's Revelation | Trust | Members at R7 or below lose 50 BP |
| Lucile's canvases | Romance → Secrecy | Every public showing adds its style's Heat (LAW-21) |
| CH-09 lock and the Fracture | Both | The game is at Hunted (≥ 60) through CH-10, exactly while she is Fractured |
| Reckless Confession | Misplaced trust → Secrecy | +25, nothing gained |
| The Octave | Trust → combat | +10% damage per confidant (CANON §11b) |

---

## 8. Worked playthroughs

Values follow §2.3 exactly; Secrecy and Lucile's BP are end-of-chapter values; Horizon is the running total. "Lock" = §2.6.

### 8.1 Run A, "The Keeper" (YES)

Period programmes and teacher attributions, crowds cleared before Recitals, rebuttals and SQ-04, every bond quest, the Early Truth in CH-07, Wings at every lesson. Renown 60 (CH-03), 260 (duel), 560 (gala).

| CH | Key events (gains after multipliers) | Secrecy | Lucile BP | Horizon |
|---|---|---|---|---|
| CH-02 | Slip +4, *Clair de lune* +3; decay −3, inn −1 | 3 | — | 0 |
| CH-03 | "Ondine" +10, caricature +10; period salon −2; decay and inn −8 | 13 | — | 0 |
| CH-04 | *Arabesque* +2; Brass Cue clears the barricade crowd; lock | 40 | 50 banked | 0 |
| CH-05 | Opens at 20; *Jeux d'eau* +3, teacher salon +1; Heine −10; −8; reports ×2 +16 | 22 | 255 (R4) | 0 |
| CH-06 | Canvas +2, transcription +3; SQ-04 −15; −8 (floor 0); reports ×2 +16 | 20 | 470 (R6) | +3 |
| CH-07 | Period salon −2; Noon → R7 → **Early Truth** (confidants 1); duel +6, transcription +4; rebuttal −10; decay −6, inn −1 | 11 | 680 (R7) | +21 |
| CH-08 | Concert +10, transcriptions +8; decay −6, inn −1; nothing reported | 22 | 810 (R8) | +21 |
| CH-09 | Chopin, Delacroix confess (3); wedding +4; lock | 60 | Fracture: cap R7 | +21 |
| CH-10 | Nohant +2; inn −1 | 61 | Mending 1 (cap R9); bank 43 | +39 |
| CH-11 | Schu— +5, *Gradus* +3, Chopin's Cover Story −10, transcription +3, inn −1 | 61 | — | +39 |
| CH-12 | DE and LU Cover Stories −20, rebuttal −10, transcriptions +6, decay −6 (the one Evening goes to WT2), modern hand-washing +11. Revelation: BE R9, LI R8, FA R8, AL R9: no losses | 42 | Mending 2: 883 (R9) | +44 |
| CH-13 | Three Cover Stories −30 | 12 | 928 | +44 |
| CH-14 | T4 salon +5, take-offs +4; BE, AL, FA, LI confess (7); Cover Stories | 0 | **1000 (R10)** | +52 |
| CH-15 | Party 2, Window Talk 4 | — | — | +62 |
| CH-17 | "Beside me, there." (+5): **+67, YES**. Octave +70% | | | |

Horizon detail: L1 +3, L2 +3, Early Truth +15; CH-10 WT1 +5, "Ask her, not me." 0, "I loved your rain." +10, L3 +3, "Spring is far off." 0; WT2 +5; CH-14 L4 +3, WT3 +5, BQ-PC08 with her +5, SQ-07 +10, SQ-12 −10, SQ-13 −5; CH-15 W4 +5, WT4 +5. Sketchbook after the council: towers of glass in snow.

### 8.2 Run B, "The Virtuoso" (NO)

Names the composer (or claims the pieces before the Vow), bursts before crowds, every modern phrasing, six Confided lines, no BQ-PC02, Evenings spent on salons, Roots at every lesson. Renown 260 (CH-05), 480 (duel), 560 (concert), 800 (gala).

| CH | Key events (gains after multipliers) | Secrecy | Lucile BP | Horizon |
|---|---|---|---|---|
| CH-02 | +7 scripted, boil water +8, tavern salon +6; −4 | 17 | — | 0 |
| CH-03 | +20 scripted; "my own" salon +9 (+3 Shadow); −6 | 40 (T2 locked) | — | 0 |
| CH-04 | Barricade Recital +3, line-up +6, "kilometres" +4; −4 | 49 | 50 banked | 0 |
| CH-05 | Opens at 29; +3, hand-guide +6, Lavergne capped +20; −8; reports ×2 +20 | 70 | 165 (R3) | 0 |
| CH-06 | Canvas +3, transcription +4, street burst +7 → 84 (**Hit**); formula aloud +19 → **Unmasking**, Gisquet's bail-out → 65; −8; reports ×2 +20 | 77 | 290 (R4) | −5 |
| CH-07 | T2 "my own" +9 (T3 locked) → 86 (Hit); **Close Call** won −20; duel +8; −8; report +10 | 76 | 365 (R5) | −10 |
| CH-08 | Transcriptions +8 → 84 (Hit); Close Call won −20; concert +10; −8; report +12 | 78 | 435 (R6) | −10 |
| CH-09 | Chopin, Delacroix confess; wedding +5 → 83 (Hit); Close Call **caught** +10; Cover Stories −20; lock | 73 | Fracture: cap R3 | −10 |
| CH-10 | Nohant +3, modern answer to Sand +16 → 92 (Hit; Close Call won −20); inn −2 | 70 | Mending 1 (cap R5); bank 25 | −30 |
| CH-11 | Schu— +7, Cover Story −10, *Gradus* +4, Toccata on the *Concordia* +7, inn −1 | 77 | — | −30 |
| CH-12 | Revelation: **LI, FA, AL −50 each**. Cover Story −10, Watchers +8, transcriptions +8 → 82 (Hit), hand-washing +14; Close Call caught +10 → **Unmasking** (Grey Hand, Bercy): escape, −10% francs, Alkan −20 BP, reset 60; decay −6 | 54 | Mending 2: 490 (R6) | −25 |
| CH-13 | Cover Stories −20 | 34 | 535 | −25 |
| CH-14 | T4 salon (Scarbo, *L'isle joyeuse*) +28, take-offs +9, photos +24 → 95; Close Call won −20; Cover Stories −30; −6 | 39 | **1000 (R10)** | −45 |
| CH-17 | "Who you become here." (−5): **−50, NO** ("Beside me, there." would give −40). Octave +30% | | | |

Horizon detail: L1 −5, L2 −5; CH-10 WT1 skipped, "Paris needs her." −10, "I don't know any more" 0, L3 −5, "Go. Paint with him." −5; WT2 +5; CH-14 L4 −5, WT3 +5, SQ-11 −15, SQ-12 −10, SQ-13 −5, BQ-PC08 without her 0, SQ-07 +10; CH-15 nothing. Sketchbook: rooftops with Théo. Two Unmaskings, six Hits, six Close Calls (two caught), no game over: a loud, valid run that ends in Paris.

### 8.3 Run C, "The Tightrope" (decided by the final words)

Some salons named, some teacher attributions, SQ-04 and rebuttals, BQ-PC02 Dawn and Morning but Noon only in CH-14, no Early Truth, Alkan confessed in CH-14. Renown 240 (CH-06), 300 (lost duel), 600 (gala).

| CH | Key events (gains after multipliers) | Secrecy | Lucile BP | Horizon |
|---|---|---|---|---|
| CH-02 | +7 scripted; −5 | 2 | — | 0 |
| CH-03 | +20 scripted; teacher salon −1; −8 | 13 | — | 0 |
| CH-04 | *Arabesque* +2, barricade Recital +3; lock | 40 | 50 banked | 0 |
| CH-05 | Opens at 20; +3, Lavergne named +16; −8; report +8 | 39 | 160 (R3) | 0 |
| CH-06 | Canvas +2, transcription +3, sighting +3; SQ-04 −15; −8; reports ×2 +16 | 40 | 350 (R5) | +3 |
| CH-07 | T2 teacher salon +3 (T3 locked); lost duel +6; transcription +4; rebuttal −10; −8; report +10 | 45 | 465 (R6) | −2 |
| CH-08 | Transcriptions +8, "photo" slip +5, Watcher +4, *Tomorrow* with Farrenc +4, ambush won, inn −1, sighting +4, concert +10, decay −6; report +10 | 83 | 535 (R6) | −2 |
| CH-09 | Hit; Close Call **caught** +10 → 93; confessions; Cover Stories −20; wedding +5; lock | 78 | Fracture: cap R3 | −2 |
| CH-10 | Nohant +2 → 80 (Hit; Close Call won −20); inn (floor) | 60 | Mending 1 (cap R5); bank 30 | −7 |
| CH-11 | Schu— +6, Cover Story −10, *Gradus* +3, transcription +3, inn −1 | 61 | — | −7 |
| CH-12 | Revelation: LI −50 (R7); BE, FA, AL R8. Cover Story −10, rebuttal −10, decay −6, transcriptions +6 | 41 | Mending 2: held at **549** (Noon gate) | −2 |
| CH-13 | Cover Stories −20; transcription with Alkan present +4 | 25 | 549 | −2 |
| CH-14 | Salon +5, take-offs +6, three photos +15; Alkan confesses; four Cover Stories −40; −6. Noon (+70 → R7); Night of Stars | 5 | **1000 (R10)** | **+1** |
| CH-17 | Octave +40%. See below | | | |

Horizon detail: L1 +3, L2 −5; CH-10 WT1 +5, "Paris needs her." −10, "I loved your rain." +10, L3 −5, "Go. Paint with him." −5; WT2 +5; CH-14 L4 +3, WT3 +5, SQ-11 −15, SQ-13 −5, BQ-PC08 with her +5, SQ-07 +10; CH-15 nothing (Lucile in Party 3, WT4 skipped). Sand's letter (12 Dec, before the Mon 16 Dec council) carried the Théo paragraph and the band-3 line, "Your last words will matter"; after the council the page shows the unfinished page.

| Final words at Horizon +1 | Total | Answer |
|---|---|---|
| "Beside me, there." (+5) | +6 | YES |
| "Whatever you choose." (0) | +1 | **YES (this run)** |
| "Who you become here." (−5) | −4 | NO |

*Variants.* With SQ-12 also done (−10), Horizon enters CH-17 at −9: even "Beside me, there." gives −4, NO, and the page shows the Pont des Arts at dawn. At exactly 0, "Whatever you choose." ties at 0: NO. Without the family council, every row reads NO and her first words are "I will not leave Théo with nothing."

---

## Canon Additions & Cross-Doc Notes

**CCR** (for the Lead Designer; not used by other docs until adopted):

- **CCR: BOSS-41 window** read as CH-02–CH-13 ("up to CH-14" exclusive), since §11e makes CH-14 police-and-public only. *Touches:* CANON §13, bosses.
- **CCR: Julien's Counter-Rumour**, a new §11e lower (−10, once, CH-14, PC-11 at R7+). *Touches:* §11e, party, side_and_bond_quests (SQ-21).
- **CCR: ranks never fall** (rank = highest reached; BP may drop; the Fracture cap is the only displayed drop), so the R8 Hint and the Revelation cannot strip Trios or Cadenzas. *Touches:* §11f, skills_and_progression, art_and_ui.
- **CCR: Lucile's Noon gate** (BP ≤ 549 until BQ-PC02 part 3), making §11f's tuning target exact. *Touches:* §11f, side_and_bond_quests (parts 1–3 playable from CH-05, sequential, none while Fractured).
- **CCR: the Unsent Letters bank** (BP earned while frozen banked at 50%, paid at Mending 2). *Touches:* §11f, party, act3.
- **CCR: Heat for Synergies, Cadenzas, Liszt's Transcribe and secret Scores** (§2.4.1). *Touches:* §11e, combat_ensemble, skills_and_progression.
- **CCR: Unmasking BP-loss eligibility.** "One random party member −20 BP" is drawn only from members present, below R10 and with unfrozen BP (none eligible = no loss). *Touches:* §11e, scenario docs.
- **CCR: Spotlight additions** (tier implementations; LOC-S06 label +5; Jae-won's clip +5; Kang apartment night −2; decay cap per story beat). *Touches:* §11e, epilogues.

**New shared facts, by affected doc:**

- **combat_ensemble:** Onlooker spawn table; slot-1 three-pip departure rule.
- **skills_and_progression:** secret-Score Heat flag; R10 command upgrades beyond the two canon examples stay theirs; R4 Notes page and R6 Covering Laugh are rank perks.
- **salons_duels_and_economy:** Secrecy order of operations (cap +20 → multipliers → −3 per teacher piece, −2 period-only → floor −6); "period-only" = REP-27–34; Watched locks the highest unlocked optional tier (never T1); rebuttal once per chapter from either source; Renown resets in Da Capo.
- **items_and_equipment:** ITM entries for every liked and disliked gift of §3.7 (UI names given); Mère Gaudin's 2 Tisanes per chapter (`byt_boil_water`), Marthe's 2 Panaceas (`byt_handwash`), the Prefecture's 100 F (`byt_line_up`).
- **overworld_and_towns, dungeons:** checkpoint bridges (Pont Neuf, Pont au Change, Pont Saint-Michel, Pont Royal; the Pont des Arts asks a toll, not papers); restricted-zone tiles; Close Call safe doors; the Unmasking escape starts with Min-jun alone; Evening-scene haunts.
- **bestiary:** a Watcher enemy (informant to CH-08, Grey Hand lookout from CH-09; routed) and the formations of §2.8.2.
- **bosses:** BOSS-41 is always Brücke's (retrieval CH-02–CH-05, lethal CH-06–CH-13), 25% per map load, guaranteed by the 4th.
- **side_and_bond_quests:** bond-quest BP and rank gates (+40/+60/+60/+80/+100 at R2/R4/R5/R7/R9); BQ-PC02 parts +50/+60/+70/+80/+90; BQ-PC02b +60; Ensemble Scenes need both members at R4 and cost an Evening; Julien joins at 550 BP.
- **party, historical_cast:** join BP and fixed-event values; topics T1–T12 and all preferences; Cover Story vignettes; Hint reactions; optional confession beats; Revelation gists; Gisquet's once-per-game bail-out (from CH-05; accept = Secrecy 65).
- **scenario docs (prologue_and_act1, act2, act3, act4_and_epilogue):** the scripted Secrecy register; eight Bite Your Tongue prompts and flags; Confided lines CH05-01…CH08-01 and their KEY-18 sentences; the CH-08 roof variant of the Early Truth; Sand's counsel and Nohant lines and labels; Window Talk topics; Sand's farewell letter (CH-14); tier boxes; Reckless Confession reactions.
- **dialogue_style_guide:** engine flags (§6.1), branch notation, the slip matrix, Lucile's six victory-quote tells.
- **audio_and_music:** LM-01's C♯ held under the final-words menu in Horizon band 3; tier-up bell and tier-down chime.
- **art_and_ui:** candle spec and variants; Onlooker and Heat pips; BP note icons; Bonds menu contents; Sketchbook viewable from Lucile's Talk menu in CH-05–CH-08; 12 Intercepted Notes in the Almanach.
- **anachronists:** the 12 Intercepted Notes' texts and the tier-box lines.
- **epilogues:** Spotlight tier implementations (streets closed in S03, S07, S12; Viral disables public painting; the subway scrum).
