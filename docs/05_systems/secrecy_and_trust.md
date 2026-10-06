# Secrecy Meter & Trust Network

Status: v1.0 — 2026-10-06 · Owns: Secrecy and Spotlight per-event values, triggers, tiers and cabal-response rules; Trust Network BP sources, rank thresholds and unlocks; character preferences (topics, gifts); confession, Hint, Cover Story and Revelation rules; Lucile's hidden track (Confided lines, Early Truth, Fracture, Mending); Horizon event wording and the ending-determination rule (LAW-23) as applied · Depends on: docs/05_systems/salons_duels_and_economy.md (not yet published; CANON §11g governs meanwhile), docs/01_vision/vision_and_pillars.md §4 · Canon: docs/00_CANON.md

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

**Ownership.** This doc owns every per-event value for Secrecy, Spotlight and BP, the tier consequences' implementation, the preference tables, the confession rules and the Horizon wording (CANON §0b). Canon values are reproduced exactly and cited; everything else is defined here. State-change tags are the CANON §16a set only, and every script follows dialogue_style_guide §2.

---

## 2. The Secrecy Meter

### 2.1 Fiction and lifecycle

**Fiction (LAW-17, R-42).** The cabal already knows who Min-jun is (CANON §8 knowledge timeline). The meter measures how much of the future has leaked into public view: witnesses, press items, police reports, rumour. The cabal reads it as risk (M1 exposure in 1833, M2 the portal) and escalates; the Prefecture reads it as subversion. The tiers name the city's attention, not the cabal's knowledge.

| Phase | Chapters | State |
|---|---|---|
| Dormant | CH-P, CH-01 | No meter; nothing costs Secrecy. |
| Full rules | CH-02–CH-09 | Lit at **0** by the scripted CH-02 slip (§2.4.7). Onlookers from **CH-04** (§2.4.1); Watcher effects of Murmured and Watched from **CH-06**, before which those tiers apply only gossip, fees and the salon lock (CANON §11e). |
| On the road | CH-10–CH-11 | Cap **99** (no Unmasking); CH-10 floor **60**; regional equivalents (§2.2). |
| Paris again | CH-12–CH-13 | Full rules; Unmasking by the Grey Hand. |
| Open war | CH-14 | **Police and public consequences only** (§2.2); Unmasking by the Prefecture. |
| Snuffed | CH-15–CH-17 | Unmasking disabled (CANON §11e); the candle goes out on the crypt stair and nothing is tracked. |
| Retired | CH-E1 / CH-E2 | Spotlight Meter (§2.10) / Canvas Ledger (CANON §4f). |

### 2.2 Tiers, consequences and the cabal's response

Consequences are **cumulative** (a tier includes every effect below it unless superseded). Canon tier ranges and effects are binding (CANON §11e); the implementation is this doc's, and map placement is overworld_and_towns §4.3's. The **ladder tier** column expresses each tier's systemic pressure in the vocabulary of the escalation ladder (CANON §4c: Watch → Soft → Quiet → Hard → Lethal); systemic pressure never moves a rung (§2.8.1).

| Tier · range · the city's attention | Canon consequence | Implementation · whose hand | Cabal reading · ladder tier | CH-10–CH-11 | CH-14 (police / public only) |
|---|---|---|---|---|---|
| **Incognito** 0–19 · a foreigner who plays well | None | — | The Velvet Leash works; Vane's soft faction ascendant · **Watch** | — | — |
| **Murmured** 20–39 · café rumour | Gossip; 1 Watcher per district map; salon fees +10% | One NPC per district map speaks a tier line from dialogue_style_guide §6.3 in place of a set line (CH-14: line 3 only). Watcher from CH-06: Julien's informants (CH-06–CH-08), a Grey Hand lookout (CH-09+). Fee +10% on optional salons. | M1, low: the Hour of Smoke listens · **Watch** | Gossip at inns only | Gossip (line 3) and fee kept; no Watchers |
| **Watched** 40–59 · his name in salons and print | 3 Watchers per district (sight cones); cabal **Shadow** encounters (1 in 8 overworld battles); one salon tier locked | From CH-06: Watchers (as Murmured) and Shadow encounters by Julien's café toughs (CH-06–CH-08), then the Grey Hand (CH-09+); formations §2.8.2. **Locked tier = the highest optional salon tier currently unlocked**; T1 is never locked; story performances and SQ-20's tier-4 salons are never locked (the lock then falls on the next tier down). | M1 rising; Archon sanctions surveillance · **Quiet** | Shadow encounters on W02 (Hunter Automata) | Salon lock kept; no Watchers, no Shadow encounters |
| **Hunted** 60–79 · police interest; papers asked for | Inn ambushes; encounter rate +25%; papers checks on 4 bridges (KEY-11 required); salon income −25% | Ambush roll per paid Paris inn night **1 in 3**; at *Au Diapason Fêlé* **1 in 6** (the regulars keep watch; the battle starts preemptive); formations §2.8.2. This doc owns the odds; overworld_and_towns §4.3 cites them. +25% encounter rate on W01 and on district maps that have encounters; dungeons unaffected. Checkpoints per overworld_and_towns §4.3: **Pont Neuf, Pont des Arts, Pont Royal, Pont au Change**; without KEY-11 the party is turned back (another bridge, the barge or a fiacre). | M1 + M2: frighten him away from the quarries and the door · **Hard** | Ambushes at regional inns; the Aachen passport check (KEY-20) adds one Shadow encounter | Papers checks and income −25% kept; no ambushes, no encounter-rate rise |
| **Compromised** 80–99 · open scandal: the future could be noticed by history | One cabal **Hit** mini-boss per chapter (BOSS-41); Faubourg Saint-Germain shops refuse service; next story beat triggers a **Close Call** (win: −20) | Ambush roll **1 in 2**. Hit §2.8.3; Close Call §2.9.1 (the Prefecture or the Grey Hand). Vidal & Fils (P14) refuses service; Curiosités Corbel serves only through its back lane (itself a restricted zone, overworld_and_towns §4.3). | Brücke's private escalation, unsanctioned like rungs 8 and 10; Archon rebukes · **Lethal** | Hit on W02 (BOSS-41 in its road setting); Close Call becomes a coach-yard escape | Shops refuse; **Close Call kept as a Prefecture chase**; **no Hit** (the BOSS-41 CCR, final section) |
| **Unmasked** 100 · seized | The Unmasking (CANON §11e) | Procedure §2.9.3 | CH-02–CH-08 and CH-14: subversion, the Prefecture (M1). CH-09, CH-12–CH-13: the Grey Hand want a recording (SIG) · **Hard** | Impossible (cap 99) | Prefecture Unmasking (cells of LOC-P25) |

### 2.3 The gain formula

Every Secrecy **gain** (any positive value, including scripted `[SEC:+n]` tags, Heat, salon totals and Lucile's reports) is computed as:

**Gain = round_half_up( Base × Renown multiplier × (1 − 0.05 × confidants) )**

- **Renown multiplier** (CANON §11e): ×1.0 at Renown 0–249 · ×1.25 at 250–499 · ×1.5 at 500–749 · ×1.75 at 750–999. Read at the moment of the gain.
- **Confidants:** members who have received a rank-10 confession (CANON §17). Lucile becomes one only at the CH-14 Night of Stars, even after the Early Truth (§5.2.4). Maximum 7 (LU, BE, DE, AL, CH, LI, FA) = ×0.65. Julien never counts (he already knows).
- **Rounding:** once, at the end, half up (CANON §10).
- **Lowers are never multiplied.** `[SEC:-10]` is exactly −10.
- **Flat exceptions** (not multiplied): story locks (§2.6), the Unmasking reset, Gisquet's bail-out reset, and the Close Call loss (+10).
- **Bounds:** 0–100 (99 in CH-10–CH-11). A gain that would exceed 100 sets 100 and triggers the Unmasking.

*Example.* Renown 420, two confidants, a Heat 3 Recital before Onlookers: 3 × 1.25 × 0.90 = 3.375 → **+3**.

### 2.4 Trigger catalogue

#### 2.4.1 Battle: Onlookers and Heat

**Onlookers appear from CH-04** (CANON §4a; combat_ensemble §4.0); CH-02–CH-03 battles have none. They are silhouettes at the top edge of the battlefield; while any remain, each **Anachronic** action adds its Heat (CANON §11e).

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

**Heat table** (added once per action while ≥ 1 Onlooker remains; an action with several Anachronic sources adds only its highest Heat).

| Action | Heat | Source |
|---|---|---|
| Future Recital piece (REP-01–25 with a Recital effect): added once when Movement I begins; Continue and CONDUCT add nothing | REP Heat 1–5 | CANON §15d |
| Min-jun's own works and period works (REP-00, REP-27–34) | 0 | CANON §15d |
| Lucile: IMPRESSION / POINTILLÉ / IMPASTO / LUMIÈRE | 2 / 3 / 4 / 2 (LUMIÈRE feeds Spotlight in CH-E1) | CANON §11e |
| Shift the Hour, Delacroix's Canvas, Tutti recipes, period Invocations (OPS-01–12) | 0 | — |
| ✦ Future Score Invocation (OPS-13–24) | 3 | CANON §11c |
| Harmony skills | 0, except CHRONO skills (5), Julien's Signature *Modal Vamp* (3: jazz harmony) and Liszt's *Ecstasy* (5: REP-21); skills learned from ✦ Scores carry 0 | CANON §10c; this doc |
| Secret Scores (OPS-25–32) | 0: none is drawn from a future work (skills_and_progression §4); a future-drawn Score would carry 3 | this doc |
| Julien's Improvise | 3 (Tritone Storm, a CHRONO result: 5) | CANON §11e, §10c |
| Any party CHRONO action, including one re-performed by Liszt's Transcribe | 5 | CANON §10c |
| Liszt's Transcribe of a Recital's Movement I | that REP's Heat | this doc |
| Synergies: SYN-01 3 · SYN-02 3 · SYN-13 4 · SYN-14 3 · SYN-15 5 · SYN-16 5 · SYN-20 3 · all others 0 | as listed | SYN-15 canon; rest this doc |
| Cadenzas: MJ *Gaspard Unbound* 5 · LU *Lever du jour* 2 · JU *Changes* 3 (5 when it resolves as Tritone Storm) · all others 0 | as listed | this doc |

*Synergy rule:* a Synergy's Heat is the highest Heat among its Anachronic parts. Min-jun's part counts as its REP (SYN-01 = REP-01, 3; SYN-02 and SYN-14's Tempest = REP-16, 3). Lucile's part counts only when she paints a strike: IMPRESSION 2, or IMPASTO 4 in SYN-13, which is learned on the Night of Stars. Setting a Light (SYN-10, SYN-12, SYN-23) is Shift the Hour, Heat 0. Julien's part in SYN-20 is jazz harmony, 3.

**Battle slip.** BOSS-07: reading the hidden formula aloud with copyists watching is a fixed **+15** (CANON §13).

#### 2.4.2 Salons

The salon minigame belongs to salons_duels_and_economy; its Secrecy cost is defined here and uses the canon formula (CANON §11g):

1. Raw = Σ over future pieces of **Heat × (1 + Cabal Presence) × attribution factor** (*name the composer* ×2; *an old teacher's piece* ×1; *my own* ×0.5, unavailable after the Vow).
2. Cap the raw total at **+20**.
3. Apply §2.3 (Renown, confidants, rounding).
4. Subtract **3 per piece attributed to "an old teacher"**, then **2 if the programme holds no future piece at all** ("period-only": REP-27–34 only).
5. A single salon's net result is never below **−6**.

Story performances ignore this formula and add only their scripted values (§2.4.7). Murmured raises optional salon fees by 10%; Hunted lowers salon income by 25%; Watched locks the top optional tier, never SQ-20's tier-4 salons (§2.2).

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

**Modifiers.** *Abroad* (CH-10–CH-11, outside Paris): −2, minimum 3 (the Hour of Smoke's rumour mill is Parisian). *Covering Laugh*: a non-confidant at R6+ in the active party laughs the slip off, −2, minimum 3, once per slip (§3.3). **English** before Onlookers or any non-party NPC: a fixed base of **+5** (multiplied as usual; CANON §5f); English alone with Vane costs 0. Base values therefore stay inside the canon range **+3 to +10**.

Slips reach the player three ways: **scripted slips** (story; §2.4.7), **slip options** in ordinary `[Q:]` choices (marked with the candle glyph and their value, §6), and **Bite Your Tongue** prompts.

**Bite Your Tongue register.** `[SLIP:3]` prompts: 3 seconds; on timeout Min-jun bites his tongue (the period phrasing plays). Modern phrasing costs **+5 to +15** and always buys a better outcome (CANON §11e). Cost guide: +5–6 commoners or artisans; +8 a life-saving fact; +10–12 officials, society or a cabal ear; +15 press and cabal together.

| Flag | CH | Where / who | Modern phrasing (label) | Cost | Period phrasing (label) | Modern outcome |
|---|---|---|---|---|---|---|
| `byt_boil_water` | CH-02 | LOC-P04, Mère Gaudin filling the stockpot | "Boil it. It's alive." | +8 | "Humour me: boil it?" | She boils every pot from then on; 2 Tisanes from her each chapter from CH-04; Petit-Louis escapes the autumn fever. Rambuteau's CH-05 Châtelet fountain scene reads the flag and funds a fountain at the Val-de-Grâce gate (historical_cast NPC-25; no new prompt) |
| `byt_line_up` | CH-04 | LOC-P25, Gisquet weighing KEY-10 | "Show it to each alone." | +10 | "This man paid them." | Gisquet has the sketch shown to Marlot's men one at a time; two admit that face paid them, contradicting Marlot, and the charge against Min-jun collapses on the spot. None can name him: the face stays "a gentleman's servant" (CANON FIC-19). `[BP:PC-03:+10]`, `[BP:PC-04:+10]` |
| `byt_hand_guide` | CH-05 | LOC-P12, Kalkbrenner's *guide-mains* | "It hurts the tendons." | +6 | "I must decline, sir." | Chopin, overhearing, hides a smile in his glove; that evening he mimics the *guide-mains* for Min-jun alone: Chopin's join BP +20 |
| `byt_nitinol` | CH-07 | LOC-P18, Alkan and the spring (shop clerk listening) | "Nickel and titanium." | +10 | "It remembers its shape" | `[BP:PC-05:+20]`; KEY-14 Almanach entry completed |
| `byt_sawdust` | CH-08 | LOC-P12 workshop, Théo (visiting with Lucile) coughing | "Dust scars the lungs." | +5 | "The air's too thick." | Pleyel promises that if the boy comes to him it will be to the finishing room, never the sawpit; `[BP:PC-02:+15]` |
| `byt_women_vote` | CH-10 | LOC-R03, Sand at dinner | "Women vote. And lead." | +12 | "Women hold us up." | Sand's farewell letter gains a line naming him an ally; Lucile's Unsent Letters bank +10 (§5.4) |
| `byt_handwash` | CH-12 | LOC-P26 hospital ward, a surgeon (Marthe present) | "Wash between beds." | +10 | "Humour a foreigner." | The ward adopts chlorinated hand-washing; Marthe gives 2 Panaceas; flag read by her CH-13 defection scene |
| `byt_sky_omnibus` | CH-14 | LOC-P24 Montmartre, at *La Lumière*'s mooring (MR-1): Rambuteau's dirigible-permit gag | "An omnibus in the sky." | +10 | "Just a balloon, sir." | Rambuteau signs the permit with a flourish; `[BP:PC-07:+15]` |

Scenario docs may add prompts using the cost guide; every prompt must keep a period phrasing that still lets the scene progress, and every modern outcome buys help, trust or lives, never money (LAW-19).

#### 2.4.4 Objects, places and field actions

| Trigger | Value | Rule |
|---|---|---|
| Seen with the phone (KEY-02) or student ID (KEY-03) | +10 | Scripted exposure checks only: CH-02 Petit-Louis lifts the "glass slate" (chase him to avoid it); CH-04 Gisquet asks for papers (showing the ID costs +10; letting Berlioz vouch costs 0). |
| Phone flashlight | +4 | Only if a Watcher is on screen; 6 uses CH-01–CH-13 (CANON §14). Watchers can share a screen with the flashlight only in the first room of P17 and P26, which open off watched maps. |
| Phone camera (CH-14) | +4 per photo | If any non-confidant is in frame or in the party (CANON §14). |
| Watcher sighting in a restricted zone | +3 | Once per map entry. The restricted zone is the one per district map listed in overworld_and_towns §4.3, which places the tiles. |
| Defeating a Watcher | +3 | Clears that map's Watchers for the rest of the chapter. |
| Dirigible take-off by day inside Paris | +2 | Night take-offs and take-offs outside the wall cost 0. |
| Transcription with a non-confidant in the active party | +3 | Per ✦ Score transcribed at a Lectern (CANON §11c). A confidants-only party transcribes free. |
| Field Talk topic *Tomorrow* with a non-confidant | +3 | §3.6. |

#### 2.4.5 Lucile's reports

Each confidence Min-jun shares with Lucile during CH-05–CH-08, up to the charity concert of Sat 21 Sep 1833, adds **+8** at the chapter-end fade, silently, through the §2.3 formula (CANON §11f). Confidences shared after the Early Truth cost nothing. Register in §5.2.2.

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
| CH-06 | CONF CH06-01 "Seoul" (reported at the chapter-end fade) | +8 |
| CH-07 | The Thalberg duel, Sat 7 Sep (either result; the embassy hushes it) | +6 |
| CH-08 | Charity concert, Salle Pleyel, Sat 21 Sep | +8 |
| CH-09 | *Ma mère l'Oye* (REP-13) four hands with Liszt at the wedding supper | +4 |
| CH-09 | End of chapter | Lock ≥ 60 (§2.6) |
| CH-10 | Prelude for the Left Hand (REP-20) at Nohant | +2 |
| CH-11 | "Madame Schu— Mademoiselle Wieck" (R-18) | +5 |
| CH-11 | *Doctor Gradus* (REP-04) for Czerny (Heat 2 + 1: Mendelssohn's academy and Czerny's publishing circle in earshot) | +3 |
| CH-12 | "Le Gibet" (REP-09) for Archon; Archon's Revelation | 0 (cabal only) |
| CH-13 | *Concerto "Lost Era"* (REP-27) at the Opéra | 0 (Heat 0) |
| CH-14 | "Scarbo" (REP-10) for Vane; Night of Stars on the Panthéon roof | 0 (private) |
| CH-14 | Hostile gala review in *Le Corsaire* (only if BOSS-17 ended below Rapture 40; combat_ensemble §11.2) | +5 |
| CH-14 (SQ-20) | BOSS-35 Thalberg rematch at Belgiojoso's, either result | +6 |

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
| Julien's Counter-Rumour | −10 | once (CH-14) | Requires Julien recruited (SQ-21); he plants the last rumour the Hour of Smoke ever spreads |
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
| **Gains / losses** | Gold "+n" rises 8 px over 30 frames with audio's `secrecy_rise`; blue "−n" sinks with `secrecy_fall` (audio_and_music §8.2). **Tier up:** that tier's V7 sting (audio_and_music §5.1) and the tier name on the base for 90 frames. **Tier down:** no sting; the music layer reverts at the next phrase end. |
| **Silent gains** | Lucile's report gains are applied at the chapter-end fade: the candle is visible and simply grows, with no "+n" and no sound (§5.2.2). |
| **Variants** | CH-10–CH-11: the candle sits in a carriage-lantern frame. CH-14: the brass base shows the Prefecture's seal (police and public only). CH-15: snuffed on the crypt stair, a smoke curl, then hidden. CH-E1: Spotlight bar. CH-E2: Canvas Ledger. |
| **Battle HUD** | Onlooker silhouettes stand at the battlefield's top edge, each with a 3-pip timer. In RECITAL, PLEIN AIR, Opus and Synergy menus every Anachronic entry shows Heat as 1–5 candle pips; with Onlookers present the pips turn red and the projected gain ("+4") is printed beside the entry. |
| **Dialogue** | Any option that raises Secrecy carries the 8-px candle glyph and its value before selection (§6). |
| **Salon programme screen** | Shows the projected Secrecy of the chosen programme as a range (best and worst Cabal Presence) before the performance. |
| **Almanach** | Press items and Intercepted Notes (§2.8.2) file under "Gazette", in period voice. |

### 2.8 The cabal's response

#### 2.8.1 Coupling rules

1. **Rungs fire on schedule.** No Secrecy value delays, skips or advances a rung of CANON §4c.
2. **Secrecy sets the pressure between rungs** (the systemic responses of §2.2, in the ladder's own tier vocabulary) and the **stated reason** for the next rung (the tier box, §2.8.4).
3. **Unsanctioned spikes mirror the ladder.** As with rungs 5, 8 and 10, the Compromised Hit is Brücke acting without Archon; the next tier box shows Archon's rebuke.
4. **From CH-14 the cabal is at open war.** Their attacks are story battles; Secrecy then governs only police and public consequences.

#### 2.8.2 Formations

Families come from CANON §8 and §12; the bestiary assigns ENM numbers. Each won Shadow encounter files one of 12 **Intercepted Notes** in the Almanach (cabal correspondence in period voice; flavour only).

| Band | Shadow encounter (Watched+, CH-06+) | Inn ambush (Hunted+) | Watcher battle |
|---|---|---|---|
| CH-02 | — | Julien's café toughs ×3 | — |
| CH-03–CH-04 | — | Black Coats ×3 (CH-04: until Marlot's capture at the riot) | — |
| CH-05–CH-08 | Julien's café toughs ×2 + 1 Watcher | Julien's café toughs ×3; from CH-07, ×2 + a Brücke Mk. I automaton | Watcher + 1 café tough |
| CH-09, CH-12–CH-13 | Grey Hand ×3 | Grey Hand ×3 | Grey Hand lookout + 1 Grey Hand |
| CH-10–CH-11 | Hunter Automata ×2 (river automata on the Rhine) | Hunter Automata ×2 | — |
| CH-14 | None | None | None |

All human foes are routed or subdued, never killed (CANON §16e); none is Prefecture, octroi or National Guard (CANON §12).

#### 2.8.3 The Hit (BOSS-41)

- **Sender:** always **Brücke**, never sanctioned ("Brücke wants him dead from the first day", CANON §8). **CH-02–CH-05:** the automaton runs a *retrieval* setting (it goes for the phone and the student ID: Brücke wants proof, and is not yet sure this is the Kang of his dossier). **CH-06–CH-13:** *lethal* setting, after the "Seoul" report confirms him (rung 8).
- **Trigger:** on reaching Compromised, each later district or overworld map load rolls 25%; the 4th load is guaranteed. Once per chapter. Not in CH-14 or after, pending the BOSS-41 CCR (final section).
- **Result:** a normal boss battle (wipe → Retry or Return, CANON §11a). It does not change Secrecy. Archon's rebuke appears in the next tier box.

#### 2.8.4 Tier boxes

Each chapter's existing cabal scene (or, where a chapter has none, a ≤ 6-box interlude at chapter end) carries **one tier box**: 1–3 boxes chosen by Secrecy at that moment. Low = 0–39 (`sec_low`), Mid = 40–79 (`sec_mid`), High = 80–99 (`sec_high`). After an Unmasking, the next tier box is replaced by a line about the seizure. Gists (the scenario docs write the lines):

| CH | Scene and speakers | Low | Mid | High |
|---|---|---|---|---|
| CH-02 | Julien reports "the Oriental pianist" to Vane (rung 1) | A tavern curiosity with three dead keys | He names composers nobody in Paris has heard of | Half the faubourg hums his tunes; Julien asks for men |
| CH-03 | Vane, certain after "Ondine", wins Archon's approval for the Leash (rung 2) | Vane: a discreet man can be kept | Delorme: let the press laugh at him first (rung 3) | Brücke: every week he plays, the record grows; Archon refuses him, for now |
| CH-04 | Vane decides on the frame-up (rung 5, unsanctioned) | He frets the boy is becoming beloved | A hero of the wrong cause is a finished cause | The Prefecture already keeps a file; Vane panics |
| CH-05 | Vane's patronage offer to Min-jun, in English (private) | Vane praises his discretion: Paris rewards it | Paris is talking; Vane offers to steer what it says | Half the city wants to hear him, the other half a magistrate |
| CH-06 | Brücke and Vane after the word "Seoul" arrives | (sample below) | (sample below) | (sample below) |
| CH-07 | Vane and Brücke rig the duel (rung 7) | Humiliate him gently: a lesson | Humiliate him publicly: a disgraced man is not believed | Brücke: disgraced, then silenced. Vane refuses to hear it |
| CH-08 | Julien and Brücke over the Pleyel tensioner (rung 8) | Julien: just make it break | Julien: break it before the concert, the city loves him | Julien leaves; Brücke alone resets the specification |
| CH-09 | Archon orders the abduction (rung 9) | Record him before anyone notices him | Record him before the city does | Record him tonight; the city is already listening |
| CH-10 | Brücke dispatches the automata (rung 10). Floor 60: Low unused | — | Out of Paris, out of sight: good for knives | The roads talk too; finish it in the Berry |
| CH-11 | Delorme and Marthe as Théo is taken (rung 11) | The girl will come for the boy | …and he will come for the girl | …and the whole Rhine heard him on the way |
| CH-12 | Archon's Audience: one line inside the Offer (rung 12) | Archon admires his care | Paris has begun to say his name | Paris says his name in every café; Archon can make it stop, if he stays |
| CH-13 | Roussel briefs his riflemen (rung 13) | The hall will watch the stage | The hall came for him; keep to the rafters | The whole hall came for him; let it look at the stage |

**Sample: CH-06** (an excerpt for act2's cabal scene at LOC-P18, rue de la Paix, after midnight).

```
// Excerpt: the tier box inside act2's CH-06 cabal scene; act2 owns the scene header and STATE footer. No state changes.
[MUS:LM-05]
[IF:sec_low]
BRÜCKE   [P:ANA-05:neutral] Seoul. He hides it from the whole city and hands it to the girl. He is the Kang.
[/IF]
[IF:sec_mid]
BRÜCKE   [P:ANA-05:neutral] Seoul. He said it to the girl himself. He is the Kang.
[/IF]
[IF:sec_high]
BRÜCKE   [P:ANA-05:angry] Seoul. And the whole faubourg humming his tunes. He is the Kang.
[/IF]
VANE     [P:ANA-02:neutral] He's a boy at a piano, Brücke. Not a war.
BRÜCKE   [P:ANA-05:neutral] A boy at a piano is how wars are remembered.
```

### 2.9 Fail states and recovery

#### 2.9.1 Close Call

- **Trigger:** when a story beat (a scripted chapter scene) begins with Secrecy ≥ 80, a Close Call plays first. Once per chapter. CH-02–CH-08 and CH-14: Prefecture agents. CH-09, CH-12–CH-13: the Grey Hand. CH-10–CH-11: a coach-yard escape from Hunter Automata.
- **Rules:** a 90-second chase on the current district map. Pursuers use CH-01 sight cones; being seen starts a 5-second pursuit that ends at the nearest checkpoint lamp, as in CH-01. Reach any safe door: *Au Diapason Fêlé* (P04), Delacroix's studio (P06), Maison Farrenc (P19, from CH-05), the Alkan house (P36, from CH-04), Chopin's apartment (P11, from CH-06), Belgiojoso's salon (P39, CH-14); on the road, the party's inn. No battle (CANON §12).
- **Win:** −20. **Caught** (timer expires): **+10 flat**, which may trigger the Unmasking. The story beat then plays either way.

#### 2.9.2 Compromised shops

Vidal & Fils (P14) shows "*Monsieur is not received.*" until Secrecy falls below 80; Curiosités Corbel serves only through its back lane (a restricted zone: a Watcher sighting there costs +3, §2.4.4). Every other shop sells as normal.

#### 2.9.3 The Unmasking

| Step | Rule |
|---|---|
| Trigger | Secrecy reaches 100. Fires at the next safe moment: the end of the current battle or scene, or the next map load. Never inside a dungeon (fires on exit), a boss battle or a story set piece. If no safe moment remains in the chapter, it fires at the first safe moment of the next chapter, with that chapter's captor. If the next chapter forbids Unmasking (CH-10, CH-15), it fires instead at the current chapter's last Lectern before the chapter-end scene; if that is impossible, Secrecy is set to 99 and nothing else happens. |
| Captor | Prefecture: CH-02–CH-08 and CH-14 (cells of LOC-P25). Grey Hand: CH-09, CH-12–CH-13 (the Bercy safe house, reusing the P25 layout, with a phonautograph horn in the cell). The horn is never played into: Min-jun refuses, and the escape begins before he touches a key (only CH-09 and CH-13 attempt the recording, LAW-12; KEY-23 is untouched). Impossible in CH-10–CH-11 (cap 99) and from CH-15. |
| Escape | Escape mini-dungeon, boss **BOSS-42 The Turnkey** (scales to party average, CANON §13). Min-jun starts alone with his baton; the party joins at the first door (the friends broke in, or bribed a turnkey). |
| Costs | −10% of francs (rounded half up to the sou). One random roster member −20 BP ("questioned"): eligible are members present in the chapter, below R10, with unfrozen BP (confidants and R10 friends are spared; if none is eligible, no loss). |
| Reset | Secrecy set to **60** (flat). |
| Gisquet's bail-out | **Once per game**, at the first Prefecture Unmasking from CH-05 on (Gisquet has known Min-jun since CH-04): **Accept** = released by the back stair, no dungeon, no francs or BP lost, Secrecy set to **65**; **Refuse** = escape as normal. Gisquet's leverage is Archon's (R-28): the next tier box shows Archon learning of it. |
| Never | A game over, a lost item, a lost save, a skipped story beat. |

### 2.10 Spotlight Meter (CH-E1) and Canvas Ledger (CH-E2)

**Spotlight Meter** (CANON §11e): press and online attention on Lucile, 0–100, HUD bar top-right in Seoul. Gains are flat (no Renown, no confidants). Map placements are overworld_and_towns §2.5's.

| Tier | Range | Consequence (canon in bold, implementation after) |
|---|---|---|
| Quiet | 0–24 | — |
| Trending | 25–49 | **Phone-camera crowds slow movement**: slow-walk zones (50% speed) on S03, S07, S11 and S12 |
| Headline | 50–74 | **Reporters block some streets**: the S03 main gate (detour by the Jeong-dong church lane) and the S04 lobby (enter by the car-park stair; the apartment night still counts); taxis refuse |
| Viral | 75–99 | Headline effects plus crowds on every town map; Lucile cannot paint in public (field painting prompts greyed: "Not with a hundred phones watching."); Céline's lawyers' offer becomes available |
| 100 | — | **Forced press scrum** (fail-forward): a scripted run through the nearest subway station, Jae-won running interference; Spotlight set to **50** |

| Raise | Value | Lower | Value |
|---|---|---|---|
| "Missing student returns" news (scripted) | +10 | Det. Oh's statement (scripted) | −15 |
| Lucile paints in public | +5 + style Heat | Céline's lawyers (once, Viral only) | −20 |
| Battle with Onlookers (2 phone-camera bystanders on Seoul town maps). Seoul battle Heat counts only Lucile's painting: her styles, *Lever du jour* 2, SYN-01 at IMPRESSION's 2 | that Heat | Passive decay: 10 min of field play in Seoul | −1 (max −6 per story beat) |
| Busking with Lucile present | +3 | A night at the Kang apartment | −2 (max −6 in CH-E1) |
| Paying with 1833 coins in public | +3 | | |
| A school group films Lucile sketching her own canvas from memory in front of it, LOC-S06 (scripted) | +5 | | |
| Jae-won posts a busking clip with Lucile in frame (optional; gives a Hanmadi word) | +5 | | |

**Canvas Ledger (CH-E2).** The Secrecy slot becomes the Ledger of Lucile's 19 surviving canvases (CANON §4f). No Secrecy, Onlookers or Heat exist in CH-E2; future pieces are greyed at salons ("Not mine to play.", LAW-25).

### 2.11 Tuning targets

Chapter-end Secrecy for three reference styles (worked in §8: Run A Careful, Run C Median, Run B Reckless). Playtests that fall outside these bands by more than 10 points for two chapters trigger a values review.

| Chapter | Careful (period programmes, cleared crowds, rebuttals) | Median | Reckless (name the composer, public bursts, every modern phrasing) |
|---|---|---|---|
| CH-02 | 0–5 | 2–10 | 15–25 |
| CH-03 | 10–20 | 12–25 | 35–55 |
| CH-04 | 40 (lock) | 40 (lock) | 45–70 |
| CH-05 | 10–25 | 25–40 | 55–80 |
| CH-06 | 10–25 | 30–45 | 70–100 (first Unmasking likely) |
| CH-07 | 5–25 | 40–55 | 75–90 |
| CH-08 | 15–25 | 60–85 | 75–95 |
| CH-09 | 60 (lock) | 60–80 | 70–95 |
| CH-10 | 60–65 | 60–75 | 70–99 |
| CH-11 | 55–65 | 60–75 | 70–99 |
| CH-12–CH-13 | 15–55 | 25–45 | 30–60 (second Unmasking likely in CH-12) |
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
3. **Lucile's Noon gate:** her BP cannot pass **549** until BQ-PC02 part 3 (Noon) is complete. This makes the canon tuning target exact (R7 by CH-08 requires parts 1–3, §5.2.1). The Bonds menu says so: "Rank 7 awaits: The Hours of Light — Noon."
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
| Lucile's Confided lines | Share +15 · Keep it light +5 | 8 choices (CH06-01 is scripted, 0 BP), §5.2.2 | Share adds the +8 report |
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
| R10 | **Confession** ("Tell the truth"), **command upgrade** (canon examples: Chopin's *Tempo Rubato*, Delacroix's LIGHT pigment; the rest per skills_and_progression §17.2), **Kindred dialogue** (CH-14 Kindred Evenings, extended CH-17 farewells, battle banter); **Lost Era** weapon eligibility (CANON §14) | CANON §11f, §14 |

### 3.4 Join BP and fixed story events

Members who join late start higher, as late joiners arrive at higher levels (CANON §5). In Da Capo, join BP = max(listed value, 50% of that member's final BP in the finished run; LAW-23.6).

| Member | Join BP (when) | Fixed story events (chapter: value) | Total fixed incl. join |
|---|---|---|---|
| PC-02 LU | 50 (CH-05; banked from CH-04: first meeting +20, the paymaster sketch +30) | CH-05 joins +30, Pont des Arts dawn lesson +30 · CH-06 first canvas +30, birthday rain study +30 · CH-08 roof kiss +40 · CH-13 eight bars +40 · lessons and Window Talks per §3.2 · CH-14 optional: KEY-18 burned together +20 (a Kindred scene if she is already R10) · CH-14 Night of Stars → 1000 | 250 before CH-14 (plus lessons, Talks) |
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

With Lucile in CH-05–CH-08, T5 Home and T12 Tomorrow open a Confided-line choice (§5.2.2); her T2 Colour closes with a Horizon line in CH-06–CH-08 and from CH-12 (§5.7).

### 3.7 Preferences

**Topics.**

| Member | Beloved (+15) | Liked (+10) | Disliked (0) and why |
|---|---|---|---|
| LU | T2 Colour | T5 Home, T10 Poets (Sand's novels) | T9 Money: the 1,200 F debt is a stone in her pocket |
| BE | T10 Poets (Shakespeare, Goethe, Virgil) | T7 Love (Harriet), T12 Tomorrow (orchestras of a thousand) | T9 Money: Harriet's theatre debts came with the bride; he answers any sum with Virgil |
| DE | T2 Colour | T10 Poets (Byron, Dante), T1 Craft (Mozart) | T8 Machines: he distrusts "progress" |
| AL | T8 Machines | T6 Faith (Scripture), T1 Craft (Bach) | T7 Love: painfully shy; he opens the psalter |
| CH | T5 Home (Poland, exile) | T1 Craft (his mimicry of other pianists), T3 Society | T4 The Street: Warsaw fell while he waited in Stuttgart |
| LI | T12 Tomorrow (a seeker) | T6 Faith, T4 The Street (the poor, the Saint-Simonians) | T3 Society: salons that pay a musician like a footman; the Saint-Cricq affair of 1828 still stings |
| FA | T9 Money (fees, equal pay) | T1 Craft, T5 Home (Victorine) | T3 Society: salon flattery that never seats a woman composer |
| JU | T1 Craft | T3 Society (the cafés), T12 Tomorrow | T11 Fame: his fame is stolen |

**Gifts.** Favourites are canon (CANON §11f); the items doc creates every ITM entry (UI names ≤ 16 characters, CANON §16h).

| Member | Favourites (+25) | Liked (+15) | Disliked (0, returned) |
|---|---|---|---|
| LU | Prussian Blue · Indiana (Sand) · Valencia Oranges | Madder Lake (Couleurs Ravenel) · Hot Chestnuts (quay vendor, P22) · Spinning Top (for Théo; Curiosités Corbel) | Painted Fan (she paints forty a week) · Snuffbox |
| BE | Faust (Nerval) · Shakespeare (En) · Orchestra Paper | Guitar Strings (Schlesinger's) · Aeneid (Virgil) · Hamlet Playbill (the 1827 Odéon troupe; bouquinistes) | Rossini Score · Hair Pomade |
| DE | Moroccan Silk · Byron's Poems · English Paints | Dante's Inferno · Throat Lozenge (the existing consumable; his hidden ailment) · Mozart Score | Ingres Print · Mechanical Toy |
| AL | Hebrew Psalter · Automaton Bird · Bach WTC Edition | Watch Movement (Curiosités Corbel) · Railway Print (the Saint-Étienne line) · Black Tea | Theatre Tickets · Ball Invitation |
| CH | Parma Violets · Polish Gazette · Kid Gloves | Gingerbread (Toruń, which he praised as a boy) · Silk Cravat · Bach Fugues | Tsar's Portrait (a print of Nicholas I; Warsaw, 1831) · Military March |
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

All bonds can be maxed in one run (CANON §11f). Dedicated play below = every bond-quest part, the Beloved topic each chapter, three favourite and three liked gifts, about 10 battles a chapter in the active party, and the Evening scenes shown.

| Member | Dedicated BP by start of CH-12 (Revelation needs R8 = 690) | Dedicated BP by end of CH-14 |
|---|---|---|
| BE | 865 (3 Evening scenes): finale possible before CH-12 | 1000 (R10) |
| AL | 764 (no Evening scene needed) | 1000 |
| LI | 714 (2 Evening scenes) | 1000 (finale in CH-14) |
| FA | 694 (2 Evening scenes) | 1000 |
| JU | — (joins CH-14 at 550) | 1000 with 4 Evening scenes |
| CH, DE | 1000 at CH-09 (guaranteed) | 1000 |
| LU | Fractured until CH-12; §5 | 1000 (Night of Stars) |

CH-14's unlimited Evenings let a player who rationed badly catch up on scenes; only timing (Duos, Signatures, Cadenzas, the Revelation, Liszt's CH-14-only finale) is truly rationed.

---

## 4. Confession

### 4.1 The rule

| Item | Rule |
|---|---|
| Availability | "Tell the truth" appears in a member's Talk menu only at **R10**; below that it is greyed: "Not yet." (CANON §11f). Sole exception: Lucile's Early Truth at R7 (§5.2.4), which is not a confidant's confession: she becomes a confidant only when the Night of Stars sets R10 (CH-14). |
| Cost | One Evening (free in CH-14, whose Evenings are unlimited). Scripted confessions cost nothing. |
| Who | Scripted: Chopin and Delacroix (CH-09), Lucile (CH-14; with the Early Truth no confession plays, and R10 alone makes her a confidant, CANON §4b). Optional: Berlioz, Liszt, Farrenc, Alkan. Julien already knows (no confession). Seo-yeon already knows; Jae-won is told in CH-E1 (story). |
| Confidant perks | Octave +10% each; Secrecy gains −5% each; one Cover Story per chapter; the member's Cadenza gains its second phase; a confidant star on the Bonds page; Kindred farewell in CH-17 (CANON §11b, §11d, §11f). |
| The Lantern Rule | Every confession from CH-09 obeys LAW-18: tell friends who I am, never when they die. Legacy may be told; death never. |
| After Archon's Revelation | A confession not yet made plays as **"The Truth, from You"**, with every perk (CANON §11f). |

**Scene numbering.** Menu-driven system scenes take reserved sequence numbers inside each member's bond-quest code (dialogue_style_guide §2.1): **81–88** Evening scenes 1–8, **90** the Hint, **91** an optional confession from the Talk menu (Lucile: the Early Truth), **92** the Cover Story. Scripted confessions keep their scenario docs' chapter numbers. Every full scene in this doc carries the guide's ten-field header and `STATE` footer; an excerpt written for another doc's scene says so (§6.3 rule 8).

### 4.2 The Hint

A preview of a member's reaction to the truth, offered once per member from the Talk menu: −20 BP at R8, free at R9 (Lucile: −20 at R6, free at R7). The reaction always names what is still missing, so the Hint doubles as a signpost to the bond-quest finale. The Bonds menu withdraws it from a member once Archon's Revelation (CH-12) has told them. Julien is never offered it. **Lucile's Hint before 21 Sep is never reported, costs no Secrecy and is not a Confided line.** She files it as a joke and writes nothing; her guilty portrait is the only trace.

```
SCENE    SCN-BQPC03-90 "The Hint: Berlioz"
LOC      Current town map (Bonds ▸ Talk)
CH       CH-03–CH-09, CH-12–CH-14 · any day at R8+ · the map's time and weather
MUSIC    LM-11
LIGHT    The map's
TRIGGER  Bonds ▸ Talk ▸ The Hint; talk; once
CAST     PC-01 · PC-03
REQUIRES r8_pc03 · not_confidant_pc03 · not_bqpc03_hint_seen
SETS     bqpc03_hint_seen
STATE    see footer

MIN-JUN  [P:PC-01:neutral] [FLAG:bqpc03_hint_seen] What if I came from very far away… in time?
BERLIOZ  [P:PC-03:grandiose] [IF:not_r9_pc03][BP:PC-03:-20][/IF] Then you'd be the one man in Paris my music was written for!
BERLIOZ  [P:PC-03:smile] Tell me properly when my *Idée fixe* is laid to rest.

STATE  BP PC-03 −20 (at R8 only) · FLAGS bqpc03_hint_seen
```

```
SCENE    SCN-BQPC04-90 "The Hint: Delacroix"
LOC      Current town map (Bonds ▸ Talk)
CH       CH-03–CH-09 · any day at R8+ · the map's time and weather
MUSIC    LM-12
LIGHT    The map's
TRIGGER  Bonds ▸ Talk ▸ The Hint; talk; once
CAST     PC-01 · PC-04
REQUIRES r8_pc04 · not_confidant_pc04 · not_bqpc04_hint_seen
SETS     bqpc04_hint_seen
STATE    see footer

MIN-JUN    [P:PC-01:neutral] [FLAG:bqpc04_hint_seen] What if I came from very far away… in time?
DELACROIX  [P:PC-04:smile] [IF:not_r9_pc04][BP:PC-04:-20][/IF] Then you'd be the most interesting sitter I was ever refused.
DELACROIX  [P:PC-04:neutral] Ask me again when the Algiers canvas is dry.

STATE  BP PC-04 −20 (at R8 only) · FLAGS bqpc04_hint_seen
```

```
SCENE    SCN-BQPC05-90 "The Hint: Alkan"
LOC      Current town map (Bonds ▸ Talk)
CH       CH-05–CH-14 · any day at R8+ · the map's time and weather
MUSIC    LM-16
LIGHT    The map's
TRIGGER  Bonds ▸ Talk ▸ The Hint; talk; once
CAST     PC-01 · PC-05
REQUIRES r8_pc05 · not_confidant_pc05 · not_bqpc05_hint_seen
SETS     bqpc05_hint_seen
STATE    see footer

MIN-JUN  [P:PC-01:neutral] [FLAG:bqpc05_hint_seen] What if I came from very far away… in time?
ALKAN    [P:PC-05:deadpan] [IF:not_r9_pc05][BP:PC-05:-20][/IF] Ecclesiastes says there is nothing new under the sun.
ALKAN    [P:PC-05:deadpan] I always suspected him of rounding. Finish the railway piece with me.

STATE  BP PC-05 −20 (at R8 only) · FLAGS bqpc05_hint_seen
```

```
SCENE    SCN-BQPC06-90 "The Hint: Chopin"
LOC      Current town map (Bonds ▸ Talk)
CH       CH-06–CH-09 · any day at R8+ · the map's time and weather
MUSIC    LM-13
LIGHT    The map's
TRIGGER  Bonds ▸ Talk ▸ The Hint; talk; once
CAST     PC-01 · PC-06
REQUIRES r8_pc06 · not_confidant_pc06 · not_bqpc06_hint_seen
SETS     bqpc06_hint_seen
STATE    see footer

MIN-JUN  [P:PC-01:neutral] [FLAG:bqpc06_hint_seen] What if I came from very far away… in time?
CHOPIN   [P:PC-06:ironic] [IF:not_r9_pc06][BP:PC-06:-20][/IF] In time? Then you know how my ballade ends.
CHOPIN   [P:PC-06:sad] Don't tell me. I must find it alone.

STATE  BP PC-06 −20 (at R8 only) · FLAGS bqpc06_hint_seen
```

```
SCENE    SCN-BQPC07-90 "The Hint: Liszt"
LOC      Current town map (Bonds ▸ Talk)
CH       CH-07–CH-14 · any day at R8+ · the map's time and weather
MUSIC    LM-14
LIGHT    The map's
TRIGGER  Bonds ▸ Talk ▸ The Hint; talk; once
CAST     PC-01 · PC-07
REQUIRES r8_pc07 · not_confidant_pc07 · not_bqpc07_hint_seen
SETS     bqpc07_hint_seen
STATE    see footer

MIN-JUN  [P:PC-01:neutral] [FLAG:bqpc07_hint_seen] What if I came from very far away… in time?
LISZT    [P:PC-07:rapture] [IF:not_r9_pc07][BP:PC-07:-20][/IF] Then I want to hear everything, *mon ami*!
LISZT    [P:PC-07:neutral] But not yet. Not until I have faced my ghost.

STATE  BP PC-07 −20 (at R8 only) · FLAGS bqpc07_hint_seen
```

```
SCENE    SCN-BQPC08-90 "The Hint: Farrenc"
LOC      Current town map (Bonds ▸ Talk)
CH       CH-08–CH-14 · any day at R8+ · the map's time and weather
MUSIC    LM-15
LIGHT    The map's
TRIGGER  Bonds ▸ Talk ▸ The Hint; talk; once
CAST     PC-01 · PC-08
REQUIRES r8_pc08 · not_confidant_pc08 · not_bqpc08_hint_seen
SETS     bqpc08_hint_seen
STATE    see footer

MIN-JUN  [P:PC-01:neutral] [FLAG:bqpc08_hint_seen] What if I came from very far away… in time?
FARRENC  [P:PC-08:neutral] [IF:not_r9_pc08][BP:PC-08:-20][/IF] Then you'd owe me a very precise account.
FARRENC  [P:PC-08:smile] Bring it when the Treasury is safe.

STATE  BP PC-08 −20 (at R8 only) · FLAGS bqpc08_hint_seen
```

```
SCENE    SCN-BQPC02-90 "The Hint: Lucile"
LOC      Current town map (Bonds ▸ Talk)
CH       CH-05–CH-14 · any day at R6+ · the map's time and weather
MUSIC    LM-03
LIGHT    The map's
TRIGGER  Bonds ▸ Talk ▸ The Hint; talk; once
CAST     PC-01 · PC-02
REQUIRES r6_pc02 · not_early_truth · not_g_fractured · not_bqpc02_hint_seen
SETS     bqpc02_hint_seen
STATE    see footer

MIN-JUN  [P:PC-01:neutral] [FLAG:bqpc02_hint_seen] What if I came from very far away… in time?
LUCILE   [P:PC-02:guilty] [IF:not_r7_pc02][BP:PC-02:-20][/IF] Then you'd be very far from home.
LUCILE   [P:PC-02:tender] …Tell me when you're sure of me.

STATE  BP PC-02 −20 (at R6 only) · FLAGS bqpc02_hint_seen · never reported, no Secrecy, no CONF
```

Lucile's guilty portrait on her Hint is deliberate: on a first run it reads as shyness, on a second as the report she chooses not to write.

### 4.3 Scripted confessions

| Who | When and where | Trigger | Cue | Beat that must land |
|---|---|---|---|---|
| Chopin | CH-09, LOC-P11 | BQ-PC06 *Żal* finale sets R10 | REP-12 *Pavane* (CANON §15d) | He asks; Min-jun answers, "You will be played every day for two hundred years." The Lantern Rule is born (LAW-18). He pledges to help find the door and keep the secret. |
| Delacroix | CH-09, LOC-P06 | BQ-PC04 finale (*Women of Algiers*) sets R10 | LM-12 | He sketches an emblem for each friend (the Door's panels, LAW-22 clue). |
| Lucile | CH-14, the Panthéon roof (the Night of Stars sets R10 and makes her a confidant, Early Truth or not) | §5 | LM-22 → LM-30 | Without the Early Truth, the Revelation told her and the roof plays "The Truth, from You". With it, no confession plays (CANON §4b): the summer's secret is simply kept. |

### 4.4 Optional confessions

| Who | Available | Where | He / she asks | Min-jun's answer (Lantern Rule) | What only this scene gives |
|---|---|---|---|---|---|
| Berlioz | CH-03–CH-09 and CH-12–CH-14, once R10 (absent CH-10–CH-11) | P04 tavern, or P10 café from CH-12 | Will France understand him? | Not for a long time; then the whole world will (his canon arc, CANON §5d). | He swears to conduct the future only under its makers' names: the scene that seeds the Vow's "credit" clause. |
| Alkan | CH-05–CH-14, once R10 (never absent; on the road in CH-10–CH-11 the scene plays at the party's inn) | P36, at the pedal piano | Nothing about himself | Silence on his withdrawal and on the railway piece (LAW-18, BQ-PC05) | The only confession that ends in a laugh. |
| Farrenc | CH-08–CH-14, once R10 (on the road, at the party's inn) | P19, after hours, among the plates | Does anyone play her music in 2026? | Forgotten, then found again (LAW-18). If the scenario docs have already placed this exchange elsewhere, she asks instead what women earn in 2026. | Her resolve to fight harder; the bar-line holds. |
| Liszt | CH-14 only (BQ-PC07 finale is BOSS-36) | P10, Tortoni's after closing | To hear the future, though not his own: that he will write himself | He plays him Debussy, never Liszt's own future work (LAW-16) | Always "The Truth, from You": the Revelation always reaches him first. |

Both samples are the pre-Revelation versions; after CH-12 the scenario docs prefix one box of "The Truth, from You".

```
SCENE    SCN-BQPC05-91 "Alkan: the truth"
LOC      LOC-P36 Alkan Family House (the pedal piano); on the road, the party's inn
CH       CH-05–CH-14 · any evening once R10 · late, the house asleep
MUSIC    LM-16
LIGHT    Candle
TRIGGER  Bonds ▸ Talk ▸ Tell the truth; talk; once
CAST     PC-01 · PC-05
REQUIRES r10_pc05 · not_confidant_pc05
SETS     confidant_pc05
STATE    see footer

[MUS:LM-16]
MIN-JUN  [P:PC-01:neutral] [EVE:-1] Charles-Valentin. I'm not from Corée the way you think. I'm from 2026.
ALKAN    [P:PC-05:deadpan] I see.[D:60]
ALKAN    [P:PC-05:deadpan] Does the Sabbath still fall on Saturday?
MIN-JUN  [P:PC-01:smile] It does.
ALKAN    [P:PC-05:smile] [FLAG:confidant_pc05] Then the important things survived. Play me something from it.
MIN-JUN  [P:PC-01:smile] Something quiet, then. Everyone's asleep.
ALKAN    [P:PC-05:deadpan] Play it badly. Nobody believes a prophet who plays well.
MIN-JUN  [P:PC-01:laugh] That's the worst advice I've ever had. I'll take it.

STATE  FLAGS confidant_pc05 · EVE −1 (none in CH-14)
```

```
SCENE    SCN-BQPC08-91 "Farrenc: the truth"
LOC      LOC-P19 Maison Farrenc (after hours, among the plates); on the road, the party's inn
CH       CH-08–CH-14 · any evening once R10 · after closing
MUSIC    LM-15
LIGHT    Candle
TRIGGER  Bonds ▸ Talk ▸ Tell the truth; talk; once
CAST     PC-01 · PC-08
REQUIRES r10_pc08 · not_confidant_pc08
SETS     confidant_pc08
STATE    see footer

[MUS:LM-15]
MIN-JUN  [P:PC-01:neutral] [EVE:-1] Louise. I'm from 2026. I came through a door under my school.
FARRENC  [P:PC-08:neutral] Then tell me something useful. In 2026, does anyone play my music?
MIN-JUN  [P:PC-01:sad] For a long time, no. You were forgotten.
MIN-JUN  [P:PC-01:smile] Then they found you again. They play you in concert halls now.
FARRENC  [P:PC-08:determined] [FLAG:confidant_pc08] Forgotten.[D:30] Then I shall make it very difficult for them.

STATE  FLAGS confidant_pc08 · EVE −1 (none in CH-14)
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

### 4.6 Too early, wrong person, never

| Case | What happens |
|---|---|
| "Tell the truth" below R10 | "Not yet." No cost. |
| Confiding (not confessing) in Lucile, CH-05–CH-08 | +15 BP and **+8 Secrecy**, reported, and read back to the player in CH-09 (§5.2.2). The trap of the game, and fair: the shadowed purse (CH-03) is on screen before any confidence, and her POV scene (CH-07) before the last ones. |
| Never | An optional member never told gives no Octave bonus and a shorter CH-17 farewell; the keepsake is still given (CANON §6). |
| Wrong person: a **Reckless Confession** | **+25 Secrecy**, nothing gained, once per NPC. |

The Hint (§4.2), the Early Truth (§5.2.4) and the Revelation (§4.5) cover the other timings.

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
| Lucile | CH-14 only, after the Night of Stars | Paints a fan of a mournful foreigner at a piano; it sells out at Corbel's and makes the "Mandarin Mimic" look harmless. |
| Berlioz | From his confession; absent CH-10–CH-11 | Announces a festival of a thousand musicians in the press; Paris forgets the Corean to laugh at Berlioz. |
| Liszt | CH-14 (after his confession) | Improvises at Belgiojoso's until dawn; the morning papers speak only of Liszt. |
| Farrenc | From her confession | Has Aristide print a dull notice listing Min-jun as an arranger for Maison Farrenc; a boring fact beats an exciting rumour. |
| Alkan | From his confession | Tells the Conservatoire that the glowing slate someone saw was part of his metronome prototype, and answers every follow-up question with Scripture. |

```
SCENE    SCN-BQPC06-92 "Cover Story: Chopin"
LOC      LOC-P05 Salon Lavergne (vignette backdrop; played from any town map)
CH       CH-09, CH-11, CH-13–CH-14 · any evening, Murmured or higher · candlelit salon
MUSIC    LM-19
LIGHT    Candle
TRIGGER  Bonds ▸ Cover Story ▸ Chopin; talk; once per chapter
CAST     [N:Salon Guest] · PC-06
REQUIRES confidant_pc06 · sec_t1
SETS     —
STATE    see footer

GUEST    [N:Salon Guest] They say the Corean plays music from the moon. Or from the devil. Nobody agrees.
{ANIM:PC-06:mimic}
CHOPIN   [P:PC-06:ironic] From the moon? Allow me.[SFX:piano_hit][D:40]
CHOPIN   [P:PC-06:ironic] Like this, yes? All elbows and comets.
GUEST    [N:Salon Guest] [SEC:-10] Ha! Then he is merely dreadful. What a relief.

STATE  SEC −10
```

---

## 5. The heroine's track

### 5.1 Timeline

| Phase | When | Trust rules | Secrecy link | Horizon inputs (LAW-23) |
|---|---|---|---|---|
| Recruited | CH-03, Sun 28 Apr (Vane, CANON §8d) | — | — | — |
| Met | CH-04, Thu 9 May | 50 BP banked | — | — |
| Reporting | CH-05 → Sat 21 Sep (charity concert) | Normal BP; Noon gate; Confided lines | **+8 per shared confidence**, chapter-end fade, silent | L1, L2, Early Truth |
| Turned | 21 Sep → CH-09 night | Normal | Nothing more is reported | — |
| Revealed | CH-09 dawn (KEY-18) | **Fracture** | End-of-chapter lock ≥ 60 | — |
| Fractured | CH-10–CH-11 | BP frozen; cap; Unsent Letters bank | Floor 60 through CH-10: the game holds at Hunted for the first half of her Fracture | WT1, Nohant answer, Sand's counsel, L3, Corot |
| Mended | CH-12 (Mending 2) → CH-14 | Normal BP; Duos | — (not yet a confidant) | WT2; then in CH-14: L4, WT3, SQ-11, SQ-12, SQ-13, BQ-PC08, SQ-07 |
| Night of Stars | CH-14, Wed 18 Dec | R10; confidant | Gains −5%; her Cover Story | — |
| Labyrinth | CH-15 | — | Snuffed | W4, WT4 |
| The Question | CH-17 | — | — | Final words |

### 5.2 Before the reveal

#### 5.2.1 Tuning

Canon target: R7 by the end of CH-08 requires BQ-PC02 parts 1–3 and most optional Lucile scenes; the default path reaches R5–R6 (CANON §11f).

| Source, CH-04 to CH-08 | Default path | Dedicated path |
|---|---|---|
| Banked, join and fixed events (§3.4; the CH-08 kiss included) | 210 | 210 |
| Lessons L1, L2 | 20 | 20 |
| Battles | 45 | 60 |
| Confided lines in mandatory scenes (CH05-01, CH08-01) | 20 | 30 |
| Field Talk, four chapters | 25 (one Liked, three Neutral) | 55 (T2 ×3 at +15, T5 ×1 at +10) |
| Gifts | 15 | 90 |
| Evening scenes 1–3 | 25 | 90 |
| BQ-PC02 parts 1–3 | 0 | 180 |
| **Total** | **360 (R5)** | **735 (R8)** |

Without parts 1–3 the Noon gate holds her at 549 (R6) however much else is done; with parts 1–3 and no optional scenes she ends near 515 (R6). Both halves of the target are needed.

#### 5.2.2 Confided lines

A Confided line is a small, true thing Min-jun chooses to share: never the whole truth. Each is a `[Q:]` with **Share** (+15 BP, `[CONF:CH##-##]`, +8 Secrecy at the chapter-end fade) and **Keep it light** (+5 BP). Shared lines before the Early Truth and before the 21 Sep concert are reported. In CH-09 Julien's bundle (KEY-18) reads back each reported line: Min-jun's own spoken words, then her sentence. Her reports also hold **observation entries** (whom he met, his quarry searches, which feed rung 6). Observation entries carry no separate cost: the canon prices her reports per confidence (+8), which already includes the Hour of Smoke's rumour (LAW-17). Lucile's Hint before 21 Sep is never reported, costs no Secrecy and is not a Confided line (§4.2).

| CONF | Scene | What he shares | Her sentence in the report (KEY-18) |
|---|---|---|---|
| CH05-01 | CH-05 Pont des Arts dawn lesson (mandatory) | His father tunes pianos for a living | "His father tunes pianos. He laughed when he said it, as if it were a secret." |
| CH05-02 | CH-05 Evening scene 1 (§6.4) | A sister who plays the violin and says he plays too loud | "He has a sister, a violinist. He misses her. He did not say so." |
| CH05-03 | CH-05–CH-08 Field Talk T5 Home | He is looking for a way home, "a door" | "He speaks of a door. He says the word as if it were a person." |
| CH06-01 | CH-06 lesson L1, Pont Royal (**scripted, no choice**; 0 BP) | The name of his city: Seoul | "His city is called Seoul. I have written it as he spelled it." |
| CH06-02 | CH-06–CH-08 Field Talk T12 Tomorrow | In his city the night is never dark | "He says that in his city the night is never dark. He is homesick, or mad." |
| CH06-03 | CH-06 Evening scene 2 | He has never finished a piece of his own | "He has never finished a work of his own. He says the music he plays belongs to other men." |
| CH07-01 | CH-07 lesson L2, Tuileries (an aside after the lesson choice) | He hears music no one has written yet | "He says he hears music no one has written yet. I believe him. That is the worst of it." |
| CH07-02 | CH-07 Evening scene 3 | His mother will still be setting a place for him | "His mother sets a place for him at table. He says so every time it rains." |
| CH08-01 | CH-08 Pleyel workshop, before the concert (mandatory) | If he found the door, he does not know if he would go | "He does not know whether he would go through his door." Her false report of 21 Sep twists it: "He has given up any door." |

CH06-01 is always reported: it is how Brücke confirms the Kang of his dossier (CANON §8). The Early Truth window therefore opens only after L1. Maximum reported: 9 lines (8 by choice, CH06-01 always), +72 base Secrecy.

#### 5.2.3 R7

R7 needs 550 BP **and** BQ-PC02 part 3 (Noon) (§3.1). At R7 her Hint is free and, in CH-06–CH-08, the Early Truth appears.

#### 5.2.4 The Early Truth

| Item | Rule |
|---|---|
| Window | R7, CH-06 (after lesson L1) to the end of CH-08 (CANON §11f) |
| Where | "Tell the truth" in her Talk menu (one Evening). **Roof variant:** if she is R7 on the Salle Pleyel roof after the CH-08 kiss, act2's roof scene offers it as a `[Q:]` at no Evening cost, the last chance, and on that branch plays the scene below from its second box. |
| Effects | `[BP:PC-02:+40]`, `[HZ:W1]` (+15). She never writes it down; every later confidence costs nothing. Fracture cap −1 instead of −3. At the reveal: "I never told them. Not that." She is not a confidant until R10: no Secrecy reduction, Cover Story or Cadenza second phase before CH-14. |
| What she does not do | Confess her own errand in return. She lies about her errand, never her feelings (CANON §16f); the guilty portrait says the rest. |

```
SCENE    SCN-BQPC02-91 "The Early Truth"
LOC      LOC-P20 Lucile's Attic (under the skylight)
CH       CH-06–CH-08 · any evening after lesson L1, Thu 11 Jul – Sat 21 Sep 1833 · night, clear
MUSIC    LM-22
LIGHT    Candle
TRIGGER  Bonds ▸ Talk ▸ Tell the truth (R7); talk; once. Roof variant: act2's CH-08 roof [Q:] jumps to box 2
CAST     PC-01 · PC-02
REQUIRES r7_pc02 · ch06_l1_done · not_early_truth
SETS     early_truth
STATE    see footer

[MUS:LM-22]
MIN-JUN  [P:PC-01:neutral] [EVE:-1] Stay a minute. There's something I've never said to anyone here.
MIN-JUN  [P:PC-01:tender] Lucile. The place I come from isn't far away. It's far ahead.
MIN-JUN  [P:PC-01:neutral] Two hundred years ahead. I was born in 2003. I came through a door.
LUCILE   [P:PC-02:surprised] …[D:60]
LUCILE   [P:PC-02:guilty] You shouldn't tell anyone that. Not even me. Especially me.
MIN-JUN  [P:PC-01:smile] Too late.
LUCILE   [P:PC-02:tender] [BP:PC-02:+40] [HZ:W1] [FLAG:early_truth] Then it stays here. Between us. Not one word of it on paper.

STATE  BP PC-02 +40 · HZ W1 · FLAGS early_truth · EVE −1 (menu trigger only; the roof variant starts at box 2 and spends none)
       Not a confidant: confidant_pc02 is written only at the Night of Stars (CH-14). Later CONF lines report nothing.
```

### 5.3 The reveal (CH-09)

| What | Effect |
|---|---|
| The reports | Every reported Confided line read back verbatim, in the player's own words (KEY-18). With the Early Truth, the last page ends on her line above. |
| Secrecy | No change at the reveal; the end-of-chapter lock (≥ 60) applies. |
| BP | Frozen at its current value. |
| Rank | Capped at max(rank − 3, 2); with the Early Truth max(rank − 1, 2). Cracked heart on the Bonds page. |
| Locked | Duos with Min-jun (SYN-01); BQ-PC02 parts; Ensemble Scenes with her. |
| Kept | Learned skills, her Signature, her Cadenza (if earned). Rank-gated access above the cap is suspended. |
| Horizon | Unchanged. Forgiving fast or slow feeds Horizon only through the LAW-23 inputs that follow; neither is punished (CANON §16f). |
| Sketchbook | KEY-09 enters Min-jun's inventory; its last page is frozen until Mending 1. |

### 5.4 Fracture, Mending and the Unsent Letters

| Event | Cap | BP | Also |
|---|---|---|---|
| Fracture, CH-09 dawn | as §5.3 | Frozen | — |
| **Mending 1**, CH-10 Nohant | +2 | Frozen | The Sketchbook page updates again |
| CH-11 interlude | — | — | She acts alone: no BP, no bank |
| **Mending 2**, CH-12, under Mignard's dome (KEY-24) | +2 | **Unfrozen; bank paid** | Duos unlock; BQ-PC02 parts 4–5 open |
| Night of Stars, CH-14 | R10 | 1000 | Confidant (`confidant_pc02`); "The Truth, from You" if no Early Truth; SYN-13 |

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

**Sand's farewell letter** (delivered by Petit-Louis at LOC-P04 on the evening of Thu 12 Dec, CH-14, as Lucile returns from seeing Sand off at the Lyon mail-coach; filed in the Almanach). world_rules_and_lore §13.23 owns the letter's opening lines; this doc owns everything from the first box below to the sign-off. The band paragraph uses Horizon at delivery. While the gate is unmet only band 3's paragraph plays, because LAW-23.5 promises that hint in every run and the Théo paragraph already says the rest.

```
// Excerpt: Sand's letter as a document (no portrait, 4 × 30 boxes), after world_rules_and_lore §13.23's opening; act4_and_epilogue owns the delivery scene's header and STATE footer. No state changes.
LETTER   [N:Sand's Letter] The coach leaves within the hour, Alfred is sulking, and I have one sheet left. So: brief.
[IF:gate_unmet]
LETTER   [N:Sand's Letter] Théo first. Always Théo. She will not leave that boy with nothing: not for you, not for heaven. Settle him.
LETTER   [N:Sand's Letter] A master, a guardian, a seal on paper. Then ask her anything you like.
[IF:hz_band_3]
LETTER   [N:Sand's Letter] She has not decided. Neither have you, I think. Your last words will matter, Kang. Choose them; don't recite.
[/IF]
[/IF]
[IF:gate_met]
LETTER   [N:Sand's Letter] You have made Théo safe. I know what that cost. So does she. Thank you, my friend.
[IF:hz_band_5]
LETTER   [N:Sand's Letter] She asks me what snow looks like on towers of glass. I told her to ask you. She has wings now. Mind them.
[/IF]
[IF:hz_band_4]
LETTER   [N:Sand's Letter] She talks of harbours and horizons, and pretends it is about painting. Is it?
[/IF]
[IF:hz_band_3]
LETTER   [N:Sand's Letter] She has not decided. Neither have you, I think. Your last words will matter, Kang. Choose them; don't recite.
[/IF]
[IF:hz_band_2]
LETTER   [N:Sand's Letter] She paints the bridges as if she means to sign them all. Paris has its hooks in her. Good hooks.
[/IF]
[IF:hz_band_1]
LETTER   [N:Sand's Letter] Her roots go down to the quarries, that girl. She belongs to these rooftops, and they to her.
[/IF]
[/IF]
[IF:byt_women_vote]
LETTER   [N:Sand's Letter] You told me women vote where you come from. I have decided to behave as if they did.
[/IF]
LETTER   [N:Sand's Letter] Be good to *ma petite Lumière*. If you are not, I will write a novel about you, and it will sell. — G.
```

**Window Talk 3's closing line** (the Panthéon roof). The band lines play only once the gate is met; while it is unmet, the Théo line replaces them.

```
// Excerpt: the closing line of Window Talk 3 inside act4_and_epilogue's Night of Stars scene (LOC-P28, CH-14, Wed 18 Dec 1833); act4 owns the header and STATE footer. No state changes.
[IF:gate_met]
[IF:hz_band_5]
LUCILE   [P:PC-02:smile] Tell me again about the towers of glass.
[/IF]
[IF:hz_band_4]
LUCILE   [P:PC-02:tender] I keep painting ships. Isn't that strange?
[/IF]
[IF:hz_band_3]
LUCILE   [P:PC-02:neutral] Ask me on the day. I'll know on the day.
[/IF]
[IF:hz_band_2]
LUCILE   [P:PC-02:smile] Look at the bridges. Every one of them is mine.
[/IF]
[IF:hz_band_1]
LUCILE   [P:PC-02:tender] Théo will be a master here. I want to see it.
[/IF]
[/IF]
[IF:gate_unmet]
LUCILE   [P:PC-02:worried] Théo still coughs at night, you know.
[/IF]
```

**Other tells** (fiction, never gauges). Most Horizon inputs land in CH-06–CH-10, so one tell speaks while the answer is still forming:

| Tell | Rule |
|---|---|
| T2 Colour Field Talk | In CH-06–CH-08 and from CH-12 (never while `g_fractured`), Lucile's T2 Colour Field Talk closes with one line by band, whatever the gate: band 5 "What colour is snow under your lamps?" · band 4 "I keep painting the edge of the sea." · band 3 "I haven't chosen my palette yet." · band 2 "Every bridge here owes me a picture." · band 1 "I'll paint these roofs till I'm old." |
| Victory bark | From CH-12, one Lucile victory bark in three is her band line instead of her standard pool (never while `g_fractured`; while `gate_unmet` the Théo line plays): band 5 "Does your sky do that?" · band 4 "Another dawn. I count them." · band 3 "Paint first. Decide later." · band 2 "Paris. Worth every sou." · band 1 "I'd know these roofs blind." · gate unmet "Théo would love that." |
| SQ-07 worry icon | Lucile's worry icon marks SQ-07 on the map CH-07–CH-14 (LAW-23.1). |
| Crypt-door prompt | Lists SQ-07 by title if unfinished (CANON §0c). |
| The Question's music | In band 3 only, the final-words menu drops all melody to the Heart's lone C♯ (Clef VII's pitch, world_rules_and_lore §13.22) as an LM-17 drone; the other bands keep LM-22 under the menu (audio_and_music). Every LM-01 statement already stops on C♯ (CANON §15c); this is the one place the whole score does. |

The lessons carry no tell: both options are written with equal warmth (LAW-23).

### 5.8 Reverie and Da Capo

- **Reverie of the Window:** no meter, no BP change; loads at CH-17's first free frame after BOSS-28 and plays the opposite answer (LAW-23.6).
- **Da Capo (NG+):** carries 50% of each member's BP (join BP = max(listed, carried), §3.4); ranks are recomputed from carried BP; confidant flags, Confided lines, the Early Truth, the bank, Horizon and Renown reset; Secrecy relights at 0 in CH-02; the Sketchbook's last page works as a compass from the start of the run (Sketchbook menu; KEY-09 itself becomes viewable in CH-05), with Théo still overriding until SQ-07.

---

## 6. Dialogue choice framework

### 6.1 Choice types

| Type | Script | Presentation | Timer | On timeout | Typical effects |
|---|---|---|---|---|---|
| Standard choice | `[Q:a\|b]` or `[Q:a\|b\|c]` | 2–3 labels ≤ 22 characters; the full line is spoken after selection | None | — | `[BP]`, `[FLAG]`, `[HZ]`, `[OV]`, `[SHD]` |
| Slip option | `[Q:]` with one option carrying `[SEC:+n]` | Candle glyph and "+n" after that label | None | — | `[SEC]` (§2.4.3 matrix value) |
| Bite Your Tongue | `[SLIP:3][Q:modern\|period][/SLIP]` | Timer bar under the box; modern label first, with candle glyph and "+n"; cursor on the period label | 3 s | Period phrasing | `[SEC]` plus the outcome |
| Confided line | `[Q:share\|keep light]` (labels written per scene) | **No glyph**: the cost is hidden, because she reports it | None | — | `[BP]`, `[CONF]` |
| Horizon choice | `[Q:]` | No glyph, no hint; equal warmth | None | — | `[HZ]` |
| Reckless Confession | NPC talk menu "Tell the truth" | Candle glyph and "+25" | None | — | `[SEC:+25]` |

Branches use `#1`/`#2`/`#END` (dialogue_style_guide §2.3); text is unwrapped; state tags open the box that dramatises them.

**Engine flags** (read by `[IF:]`, never shown, never written by hand): `sec_low` 0–39, `sec_mid` 40–79, `sec_high` 80–99 (the tier-box bands of §2.8.4; 100 never reaches a tier box, because the Unmasking fires first); `hz_band_1`…`hz_band_5` (≤ −30, −29…−5, −4…+5, +6…+29, ≥ +30); `gate_met`, `gate_unmet`; `g_fractured`; the guide's `rN_pcNN` and `sec_t1`…`sec_t5`.

**Flags written once by `[FLAG:]`:** `early_truth` (only by the Early Truth, §5.2.4); `confidant_pc03`…`confidant_pc08` (each by its member's confession); `confidant_pc02` (only by the CH-14 Night of Stars, never by the Early Truth); the eight `byt_*` flags of §2.4.3 (each in its prompt's modern branch); `bqpc02_hint_seen`…`bqpc08_hint_seen` (§4.2).

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
8. Scripts follow dialogue_style_guide §2: the ten-field header, SPEAKER labels, `#n`/`#END`, the `STATE` footer. An excerpt written for another doc's scene says so in a `//` comment and leaves the header and footer to its host. This doc audits every `STATE` footer's `[CONF]` and `[SEC]` lines.

### 6.4 Sample: a Confided line (CH-05, Lucile's Evening scene 1, her attic)

```
SCENE    SCN-BQPC02-81 "Who taught you"
LOC      LOC-P20 Lucile's Attic (skylight)
CH       CH-05 · any evening, Sat 15 Jun – Wed 10 Jul 1833 · 21:00, clear
MUSIC    LM-03
LIGHT    Candle
TRIGGER  P20, Bonds ▸ Evening with Lucile; talk; once
CAST     PC-02 · PC-01
REQUIRES —
SETS     —
STATE    see footer

LUCILE   [P:PC-02:smile] Who taught you to play? Someone patient, I hope.[Q:My mother. My sister.|A teacher, long ago.]
  #1 My mother. My sister.
     MIN-JUN [P:PC-01:homesick] [BP:PC-02:+15] [CONF:CH05-02] My mother taught me. My sister plays violin. She says I play too loud.
  #2 A teacher, long ago.
     MIN-JUN [P:PC-01:smile] [BP:PC-02:+5] A teacher, long ago. She'd hate my posture.
  #END
LUCILE   [P:PC-02:tender] [EVE:-1] …[D:30] Play me something quieter, then.

STATE  BP PC-02 +15 (#1) | +5 (#2) · CONF CH05-02 (#1; hidden Secrecy +8 at the CH-05 chapter-end fade) · EVE −1
```

The player sees two notes or one over her portrait. Nothing else happens until the chapter-end fade, when the candle grows by 8 and no one says why.

---

## 7. Interactions between Secrecy and Trust

Most couplings are stated with their rule: confidant damping (§2.3), Cover Stories (§4.7), confidants-only transcription (§2.4.4), Bite Your Tongue bonds (§2.4.3), the Revelation (§4.5), Lucile's canvases (§2.4.7), Reckless Confession (§4.6). Five cross the systems and are gathered here:

| Interaction | Direction | Rule |
|---|---|---|
| Confiding in Lucile, CH-05–CH-08 | Trust ↔ Secrecy | Each shared Confided line buys +15 BP toward the R7 she needs for the Early Truth and costs +8 Secrecy she reports. The Early Truth ends the cost; only R10 (the Night of Stars) makes her a confidant |
| Covering Laugh | Trust → Secrecy | A non-confidant at R6+ in the active party trims each slip by 2 (minimum 3): the friends who do not know yet still protect him |
| *Tomorrow* topic | Secrecy ↔ Trust | Liszt's Beloved topic and Berlioz's and Julien's Liked cost +3 Secrecy unless the friend is a confidant (Julien always free): for those three the warmest talk is the one that leaks |
| The Unmasking | Secrecy → Trust | −20 BP to one random eligible member (present, below R10, unfrozen): the city's attention costs a friend's trust |
| The Octave | Trust → combat | +10% damage per confidant (CANON §11b): every confession made for cover also strengthens the final Synergy |

---

## 8. Worked playthroughs

Values follow §2.3 exactly; Secrecy and Lucile's BP are end-of-chapter values; Horizon is the running total. "Lock" = §2.6; "(Hit)" marks that chapter's BOSS-41 fight.

### 8.1 Run A, "The Keeper" (YES)

Period programmes and teacher attributions, crowds cleared before Recitals, rebuttals and SQ-04, every bond quest, the Early Truth in CH-07, Wings at every lesson. Renown 60 (CH-03), 260 (duel), 560 (gala).

| CH | Key events (gains after multipliers) | Secrecy | Lucile BP | Horizon |
|---|---|---|---|---|
| CH-02 | Slip +4, *Clair de lune* +3; decay −3, inn −1 | 3 | — | 0 |
| CH-03 | "Ondine" +10, caricature +10; period salon −2; decay and inn −8 | 13 | — | 0 |
| CH-04 | *Arabesque* +2; Brass Cue clears the barricade crowd; lock | 40 | 50 banked | 0 |
| CH-05 | Opens at 20; *Jeux d'eau* +3, teacher salon +1; Heine −10; −8; reports ×2 +16 | 22 | 255 (R4) | 0 |
| CH-06 | Canvas +2, transcription +3; SQ-04 −15; −8; reports ×2 +16 | 20 | 470 (R6) | +3 |
| CH-07 | Period salon −2; Noon → R7 → **Early Truth** (no confidant until R10); duel +6, transcription +4; rebuttal −10; decay −6, inn −1 | 11 | 680 (R7) | +21 |
| CH-08 | Concert +10, transcriptions +8; decay −6, inn −1; nothing reported | 22 | 810 (R8) | +21 |
| CH-09 | Chopin, Delacroix confess (confidants 2); wedding +5; lock | 60 | Fracture: cap R7 | +21 |
| CH-10 | Nohant +2; inn −1 | 61 | Mending 1 (cap R9); bank 43 | +39 |
| CH-11 | Schu— +6, *Gradus* +3, Chopin's Cover Story −10, transcription +3, inn −1 | 62 | — | +39 |
| CH-12 | Delacroix's Cover Story −10 (Chopin absent), rebuttal −10, transcriptions +6, decay −6 (the one Evening goes to WT2), modern hand-washing +11. Revelation: BE R9, LI R8, FA R8, AL R9: no losses | 53 | Mending 2: 883 (R9) | +44 |
| CH-13 | Delacroix's and Chopin's Cover Stories −20 | 33 | 928 | +44 |
| CH-14 | BE, AL, FA, LI confess (confidants 6); T4 salon +5 (one teacher piece: 8 raw × 1.5 × 0.70 = 8, then −3), take-offs 2 × +2; Cover Stories ×4 −40, decay −6, inn nights −5 (floor 0); the Night of Stars makes Lucile the 7th confidant | 0 | **1000 (R10)** | +52 |
| CH-15 | Party 2, Window Talk 4 | — | — | +62 |
| CH-17 | "Beside me, there." (+5): **+67, YES**. Octave +70% | | | |

Horizon detail: L1 +3, L2 +3, Early Truth +15; CH-10 WT1 +5, "Ask her, not me." 0, "I loved your rain." +10, L3 +3, "Spring is far off." 0; WT2 +5; CH-14 L4 +3, WT3 +5, BQ-PC08 with her +5, SQ-07 +10, SQ-12 −10, SQ-13 −5; CH-15 W4 +5, WT4 +5. Sketchbook after the council: towers of glass in snow.

### 8.2 Run B, "The Virtuoso" (NO)

Names the composer (or claims the pieces before the Vow), bursts before crowds, every modern phrasing, six Confided lines, no BQ-PC02, Evenings spent on salons, Roots at every lesson. Renown 260 (CH-05, after Lavergne), 480 (duel), 560 (concert), 800 (gala).

| CH | Key events (gains after multipliers) | Secrecy | Lucile BP | Horizon |
|---|---|---|---|---|
| CH-02 | +7 scripted, boil water +8, tavern salon +6; −4 | 17 | — | 0 |
| CH-03 | +20 scripted; "my own" salon +9 (+3 Shadow); −6 | 40 (T2 locked) | — | 0 |
| CH-04 | *Arabesque* +2, barricade Recital +3, line-up +10, "kilometres" +4; −4 | 55 | 50 banked | 0 |
| CH-05 | Opens at 35; Lavergne capped +20 first, while still Murmured (Renown passes 250); *Jeux d'eau* +4, hand-guide +8; −8; reports ×2 +20 | 79 | 165 (R3) | 0 |
| CH-06 | Canvas +3, transcription +4 → 86, street burst +7 → 93 (**Hit**); formula aloud +19 → **Unmasking**, Gisquet's bail-out → 65; −8; reports ×2 +20 | 77 | 290 (R4) | −5 |
| CH-07 | T2 "my own" +9 (T3 locked) → 86 (Hit); **Close Call** won −20; duel +8; −8; report +10 | 76 | 365 (R5) | −10 |
| CH-08 | Transcriptions +8 → 84 (Hit); Close Call won −20; concert +10; −8; report +12 | 78 | 435 (R6) | −10 |
| CH-09 | Chopin, Delacroix confess; wedding +5 → 83 (Hit); Close Call **caught** +10; Cover Stories −20; lock | 73 | Fracture: cap R3 | −10 |
| CH-10 | Nohant +3, modern answer to Sand +16 → 92 (Hit; Close Call won −20); inn −2 | 70 | Mending 1 (cap R5); bank 25 | −30 |
| CH-11 | Schu— +7, Cover Story −10, *Gradus* +4, Toccata on the *Concordia* +7, inn −1 | 77 | — | −30 |
| CH-12 | Revelation: **LI, FA, AL −50 each**. Cover Story −10, Watchers +8, transcriptions +8 → 83 (Hit), hand-washing +14; Close Call caught +10 → **Unmasking** (Grey Hand, Bercy): escape, −10% francs, Alkan −20 BP, reset 60; decay −6 | 54 | Mending 2: 490 (R6) | −25 |
| CH-13 | Cover Stories −20 | 34 | 535 | −25 |
| CH-14 | T4 salon (*Scarbo*, *L'isle joyeuse*) +28, take-offs +9, photos +24 → 95; Close Call won −20; Cover Stories −30; −6 | 39 | **1000 (R10)** | −45 |
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
| CH-14 | Salon +5, take-offs +6, three photos +15; Alkan confesses; four Cover Stories −40 (CH, DE, AL, and Lucile after the Night of Stars); −6. Noon (+70 → R7); Night of Stars | 5 | **1000 (R10)** | **+1** |
| CH-17 | Octave +40%. See below | | | |

Horizon detail: L1 +3, L2 −5; CH-10 WT1 +5, "Paris needs her." −10, "I loved your rain." +10, L3 −5, "Go. Paint with him." −5; WT2 +5; CH-14 L4 +3, WT3 +5, SQ-11 −15, SQ-13 −5, BQ-PC08 with her +5, SQ-07 +10; CH-15 nothing (Lucile in Party 3, WT4 skipped). Sand's letter (12 Dec, before the Mon 16 Dec council) carried the Théo paragraph and the band-3 line, "Your last words will matter"; after the council the Sketchbook shows the unfinished page.

| Final words at Horizon +1 | Total | Answer |
|---|---|---|
| "Beside me, there." (+5) | +6 | YES |
| "Whatever you choose." (0) | +1 | **YES (this run)** |
| "Who you become here." (−5) | −4 | NO |

*Variants.* With SQ-12 also done (−10), Horizon enters CH-17 at −9: even "Beside me, there." gives −4, NO, and the page shows the Pont des Arts at dawn. At exactly 0, "Whatever you choose." ties at 0: NO. Without the family council, every row reads NO and her first words are "I will not leave Théo with nothing."

---

## Canon Additions & Cross-Doc Notes

**CCR** (for the Lead Designer; this doc runs the reading stated until a ruling):

- **CCR:** CANON §13 BOSS-41 "any chapter up to CH-14" conflicts with §11e "from CH-14 … only police and public events". This doc reads §11e as governing and runs no Hit in CH-14; bosses.md builds no CH-14 Hit until the Lead Designer rules. *Touches:* CANON §11e, §13; bosses.

**New shared facts owned by this doc** (CANON §0b: Secrecy, Trust and Spotlight per-event values, BP rules, Horizon wording): Julien's Counter-Rumour (§2.5); Heat for Synergies, Cadenzas, Transcribe, *Modal Vamp* (3), *Ecstasy* (5) and secret Scores (0) (§2.4.1); ranks never fall, Lucile's Noon gate and the Unsent Letters bank (§3.1, §5.4); Lucile a confidant only from the Night of Stars, CANON §17 read strictly (§2.3); Unmasking BP-loss eligibility, deferral and the unplayed horn (§2.9.3); the Spotlight implementation (§2.10); the Bite Your Tongue register, slip matrix, Onlooker table, ambush odds and formations (§2.2–§2.4, §2.8.2); the CH-14 gala review +5 and BOSS-35 +6 (§2.4.7); every Trust table (§3); system-scene sequences 81–88 and 90–92 in BQ-PC codes and the `bqpcNN_hint_seen` flags (§4.1); Lucile's tells (§5.7).

**Cross-doc notes** (one line per affected doc):

- **dialogue_style_guide:** §2.3 `sec_low`/`sec_mid`/`sec_high` become 0–39 / 40–79 / 80–99; the `confidant_pc02` row reads "(Lucile: only the CH-14 Night of Stars)" in place of "(Lucile: the Early Truth or her CH-14 confession)"; the `byt_*` list stays eight (historical_cast makes Rambuteau's fountain a `byt_boil_water` payoff); add `bqpcNN_hint_seen`, the reserved sequences and Lucile's band victory barks (§5.7); this doc now uses `#n`/`#END`, so the `→n` alias can retire.
- **overworld_and_towns:** §4.3 "Grey Hand ambush" should read "ambush formation per secrecy_and_trust §2.8.2"; its bridges, restricted zones, Corbel back lane, ambush odds and §2.5 Spotlight placements are cited here unchanged (Hotel Ginkgo stays its CCR).
- **historical_cast:** FIC-19 and NPC-24: under `byt_line_up` the face stays unnamed, so drop "named in Gisquet's file" and "can name Tissot the same day"; NPC-16: the `byt_hand_guide` outcome is now courteous; NPC-25: the permit gag sits at MR-1 here too.
- **items_and_equipment:** delete the Prefecture's 100 F (`byt_line_up`); rename ITM-636 "Kalkbrenner Book" to "Tsar's Portrait" (a print of Nicholas I).
- **world_rules_and_lore:** §13.23: this doc's part of Sand's letter begins "The coach leaves within the hour…", with no clock hour.
- **combat_ensemble:** Synergy rule and table now agree (SYN-10, 12, 23 = 0); Improvise and *Changes* as Tritone Storm = 5; the hostile gala review = +5.
- **skills_and_progression:** its Heat requests adopted (*Modal Vamp* 3, *Ecstasy* 5, ✦-learned skills 0, secret Scores 0).
- **salons_duels_and_economy:** Secrecy order of operations (§2.4.2); "period-only" = REP-27–34; Watched never locks T1 or SQ-20's salons; one rebuttal per chapter from either source; Renown resets in Da Capo.
- **audio_and_music:** tier stings and silent falls per its §5.1; `secrecy_rise`/`secrecy_fall` on gains and losses; the band-3 C♯ drone under the final-words menu.
- **art_and_ui:** candle spec and variants; silent report gains at the chapter-end fade; Heat pips; BP note icons; Bonds menu; 12 Intercepted Notes.
- **bosses:** BOSS-41 always Brücke's (retrieval CH-02–CH-05, lethal CH-06–CH-13), 25% per map load, guaranteed by the 4th; BOSS-35 adds +6 Secrecy.
- **bestiary:** the §2.8.2 formations (Black Coats CH-03–CH-04 only; Julien's café toughs CH-02 and CH-05–CH-08; Mk. I automaton from CH-07); a routed Watcher enemy.
- **dungeons:** the Unmasking escape starts with Min-jun alone; only the first rooms of P17 and P26 let a Watcher see the flashlight.
- **side_and_bond_quests:** bond-quest BP and gates (§3.5); Ensemble Scenes need R4 and an Evening; Julien joins at 550 BP; SQ-20's salons are never locked; keep sequences 81–88 and 90–92 free in BQ codes.
- **party:** join BP and fixed events (KEY-18 burning +20); preferences (Liszt dislikes T3; Berlioz's T9 reason; Chopin's Tsar's Portrait); Lucile a confidant only from the Night of Stars.
- **scenario docs:** the scripted register; the eight prompts (`byt_line_up` +10 without naming Tissot; `byt_sky_omnibus` at MR-1, +10); Confided lines; the Early Truth and its roof branch; Lucile's Cover Story only after the Night of Stars; tier boxes; Sand's letter and WT3 gate logic; Lucile's T2 band lines.
- **anachronists:** the Intercepted Notes' texts and the tier-box lines.
- **epilogues:** Spotlight on overworld placements; the S06 school group +5; Seoul Heat from Lucile's painting only.
