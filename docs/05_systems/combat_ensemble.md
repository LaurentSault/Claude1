# Combat — The Ensemble (ATB)

Status: v1.0 — 2026-10-06 · Owns: battle rules, ATB details, command menus, statuses and elements in detail, the complete Synergy skill list (effects, power, animation), Cadenza rules, battle-stage modifiers, special battle types, the enemy AI script language (Libretto) · Depends on: none · Canon: docs/00_CANON.md

## Table of Contents

1. [Scope, Conventions and Design Intent](#1-scope-conventions-and-design-intent)
2. [Battle Screen and HUD](#2-battle-screen-and-hud)
3. [ATB Specification](#3-atb-specification)
4. [Command Menus](#4-command-menus)
5. [Rows, Formations, Targeting, Reflection and Counters](#5-rows-formations-targeting-reflection-and-counters)
6. [Harmony, Synergy and the Crescendo Gauge](#6-harmony-synergy-and-the-crescendo-gauge)
7. [Cadenza (Desperation)](#7-cadenza-desperation)
8. [Elements and Light States](#8-elements-and-light-states)
9. [Statuses](#9-statuses)
10. [Battle-Stage Modifiers: Onlookers and Field Effects](#10-battle-stage-modifiers-onlookers-and-field-effects)
11. [Special Battle Types](#11-special-battle-types)
12. [Escape, Victory, Defeat](#12-escape-victory-defeat)
13. [Enemy AI Script Language: the Libretto](#13-enemy-ai-script-language-the-libretto)
14. [Accessibility and Difficulty](#14-accessibility-and-difficulty)
15. [Canon Additions & Cross-Doc Notes](#canon-additions--cross-doc-notes)

---

## 1. Scope, Conventions and Design Intent

**Fixes:** how a battle looks, ticks, takes input, resolves and ends; every command's mechanics; every status and element interaction; all 23 Synergies; the Cadenza; field effects; special battle formats; the Libretto that `bestiary.md` and `bosses.md` script enemies in. **Does not fix:** CANON §10 formulas (reproduced, never altered) or their derivations and power budgets (`formulas_and_curves.md`, whose numbers this doc uses); skill lists (HRM, ETU, STU, TUT, OPS: `skills_and_progression.md`); enemy stats (`bestiary.md`); boss phases and full scripts (`bosses.md`); duel minigames (`salons_duels_and_economy.md`); Secrecy values, Heat per event and Onlooker counts (`secrecy_and_trust.md`).

| Combat law | Consequence |
|---|---|
| **Every command is a person** (P1) | Every command has a signature currency on top of INS: Recital spends turns, Plein Air the Light, Orchestrate tokens, Canvas pigments, Étude fingers, Rubato time, Transcend a doubled cast, Counterpoint attention |
| **The loudest move costs the most cover** (P3) | Anachronic actions add Heat before Onlookers; a quieter option of nearly equal value always exists |
| **The Ensemble wins on tempo** (P1) | A Synergy lands several members' turns at once, at P1, with no INS, no miss and a rider; the Crescendo fills fastest when the party suffers |
| **Weight, never gore** (Tone Rule 8) | Humans are *routed* or *subdued*; Echoes *dissolve into sound*; automata *collapse into springs* |
| **Short and readable** | At default speed: standard battle 45–90 s, story boss 6–12 min. Animations ≤ 4 s; Synergies ≤ 8 s; the Octave ≤ 15 s, skippable on repeats |

**Conventions.** A **turn** is one filling of the bearer's own gauge (CANON §10d). A **round** is one ATB cycle in which every living party member acts once (CANON §10e); a status or mark lasting *n* rounds lasts *n* of its bearer's own turns. All damage and healing use CANON §10b, rounded half up; "×0.5 spread" is the canon all-target penalty. Scaling commands (Canvas, Plein Air, Orchestrate, Recital bursts, Counterpoint, BOW, IMPROVISE) read a **command tier** from the user's level, using the tier gates of formulas_and_curves §8.4 (each gate is the first level of the chapter where CANON §10b makes the tier available), and never above the canon chapter: T2 from CH-05, T3 from CH-10, T4 from CH-14.

| User level | Tier | Attack PWR (Pₜ) | Attack INS (Cₜ) | Heal PWR (Hₜ) | Heal INS |
|---|---|---|---|---|---|
| 1–10 | T1 | 12 | 4 | 10 | 5 |
| 11–21 | T2 | 28 | 9 | 24 | 10 |
| 22–32 | T3 | 50 | 16 | 45 | 18 |
| 33+ | T4 | 80 | 28 | 70 | 30 |
| Lv 41+ and a learned T5 HRM (taught only by epilogue-optional or post-game sources) | T5 | 120 | 50 | 70 (no T5 heal exists) | 30 |

---

## 2. Battle Screen and HUD

### 2.1 Layout (256 × 224, FF6 side view; CANON §16h)

| Region | Rectangle (x, y, w × h) | Contents |
|---|---|---|
| Battlefield | 0, 0, 256 × 152 | Backdrop on BG1/BG2 (large bosses on a background layer); Light tint by colour math |
| Enemy zone | 8, 16, 128 × 128 | Up to 6 enemies (8 with scripted adds); front rank at the zone's right edge, back rank 24 px left |
| Party column | 184–255, 40–151 | Four 32 × 32 cells; slot *n* front-row origin x = 184 + 8(*n* − 1), y = 40 + 24(*n* − 1); **back row +16 px x** (slot 4 back ends at x = 255) |
| Ward / escort | 232, 24, 24 × 32 | Théo, Vane, a canvas or an instrument (§11.4) |
| Enemy list | 0, 152, 96 × 72 | Names ≤ 14 characters, duplicates collapsed ("Grey Hand ×3"); the command window covers it when a member is Ready |
| Party window | 96, 152, 160 × 72 | Four 16-px rows: name or cycling status icon (≤ 9 characters), HP, INS, 40-px ATB bar |
| Crescendo strip | 96, 144, 160 × 8 | From CH-04: three bars of 100; a full bar glows gold |
| Banner | 20, 4, 212 × 14 | One line ≤ 30 characters: skill and item names, barks, `SAY` lines. Synergy and Cadenza banners (≤ 30 characters) stay at 8, 4, 240 × 20 |

**Octave formation (BOSS-27, binding):** two columns of four at x = 168 and x = 200 on 32 × 32 cells; enemies confined to the left 120 px; the party window widens to 256 px and splits into two 128-px panes of four rows (name, HP, ATB; INS is hidden because Voice costs nothing); the enemy list moves into the banner; an eight-note staff replaces the Crescendo strip and lights one note per Voice (§6.7).

### 2.2 HUD elements

| Element | Where | Behaviour |
|---|---|---|
| **Light State icon** | 4, 4 | From CH-05 (§4.0): current Light (two half-icons under LUMIÈRE); shape-coded (§8.3) |
| **Field icon** | 4, 22 | Active field effect (§10.2) |
| **Timer** | 112, 26 | Timed battles (§11.6): "12" for turns, "1:30" for clocks |
| **Candle** | 232, 4 | Only while an Onlooker remains; highlighting an Anachronic command flickers it and shows the Heat pips before they are paid |
| **Onlookers** | y 16–40, between the sides | Silhouettes on BG3, from CH-04 (§10.1) |
| **ATB bar** | Party window | White while filling; gold with the two-note ding when full (CANON §15a); pale blue with a rest glyph in Tacet; a chevron for Allegro, dimmed for Lento, a fermata glyph, a 1-px jitter for Swing |
| **Synergy links** | Left of each ATB bar | A chain-link beside each member of a learned, affordable Synergy; gold once that member is Ready |
| **Overhead markers** | 8 × 8, above sprites | Recital movement, Coda count, Tutti tokens, Rubato charges, Bravura and Idée Fixe stacks, Swell, Dots (n/10), crit marks, Tacet, Unseen |
| **Annotated data** | Enemy list | After *Annotate*, HP and ATB bars replace the enemy's name (Select toggles) |

---

## 3. ATB Specification

### 3.1 The gauge

Every party member and enemy has a gauge of **0–256** and is **Ready** at 256. Fill per second of battle clock (CANON §10b): **Fill = (TMP + 25) × 1.6 × SpeedSet × StatusMod**; SpeedSet 1.5 / 1.3 / 1.15 / **1.0 (setting 4, default)** / 0.85 / 0.7; StatusMod = Allegro ×1.5 × Lento ×0.5 × Swing (×0.5–×1.5), or 0 under Fermata. Enemy TMP follows CANON §10b (standard 10 + 0.45L, boss 15 + 0.5L), rounded half up.

**Seconds per turn** (StatusMod 1):

| TMP | Speed 1 | Speed 4 (default) | Speed 6 | Typical holder |
|---|---|---|---|---|
| 10 | 3.05 | 4.57 | 6.53 | A Lv 1 standard enemy |
| 15 | 2.67 | 4.00 | 5.71 | Canon check (CANON §10b) |
| 22 | 2.27 | 3.40 | 4.86 | CH-09 average member |
| 30 | 1.94 | 2.91 | 4.16 | Liszt at join (28); a CH-16 boss (35) |
| 40 | 1.64 | 2.46 | 3.52 | Late-game Lucile, Liszt |
| 60 | 1.25 | 1.88 | 2.69 | Liszt at Lv 50 (59) |
| 99 | 0.86 | 1.29 | 1.84 | Cap |

### 3.2 The battle clock and the two modes

The **battle clock** is the time base for every gauge, timed status and clock timer.

| Situation | Active mode | Wait mode (default) |
|---|---|---|
| Action animation or skill banner playing | Clock stopped | Clock stopped |
| Bark in the banner (dialogue_style_guide §5.1) | Clock runs | Clock runs |
| Top-level command list open | Clock runs | Clock runs (stops if *Pause on Command* is on, §14) |
| Sub-list open (Harmony, Item, Recital, Canvas, Synergy, Cue…) or target cursor active | Clock runs | **Clock stopped** |
| Étude, BEAT, Hwimori or IMPROVISE input window | Clock stopped (the input has its own timer) | Clock stopped |
| Start (pause) | Stopped, screen dims, "PAUSE" | Same |

### 3.3 The Ready queue and input

1. A member whose gauge reaches 256 joins the **Ready queue** (first in, first out); the two-note ding plays and the window opens for the head of the queue.
2. **Y** passes the window to the next Ready member, who keeps a full gauge. **Tacet** also passes it and grants DEF/RES +25% until the member acts; the automatic cycle skips Tacet members, but **Y** reaches them.
3. Enemies never wait: a full enemy gauge runs `ON TURN` at once and enqueues the action.

### 3.4 The action queue

Confirmed actions enter one shared queue and resolve one at a time. **On confirmation the actor's gauge drops to 0 and stays frozen until the action resolves**, then refills; the actor is *Committed* in between.

| Lane | Contents | Order |
|---|---|---|
| **P0** | Libretto `ON START`, `ON PHASE` and scripted events; the Octave's automatic firing; wave arrivals | Before everything |
| **P1** | Counters; Bulwark interceptions; Encore revivals; Chiaroscuro counters; Canon echoes; Synergies; Conducted actions; the eight-bar rescue (§11.2) | Before any queued P2 |
| **P2** | Every other action | First in, first out |

INS and items are spent **at resolution**, never at confirmation.

Opening gauges by formation are in §5.2.

### 3.5 Speed statuses and gauge manipulation

- **Allegro and Lento cancel:** applying either to a bearer of the other removes the old status and does not apply the new one.
- **Swing** re-rolls every second, in 0.1 steps from ×0.5 to ×1.5. **Fermata** forces 0; an Allegro gained under Fermata waits for it to end.
- **Gauge moves** are fractions of 256, rounded half up: *Borrow* −77 (30%), *Repay* +87 per charge (34%), Winds Cue −26 (10%), Libretto `ATB` as written. Gauges clamp to 0–256. **Three Repay charges** set the recipient's gauge to 256 and move it to the head of the Ready queue (§3.3).

### 3.6 Turns, durations and ticks

**Turn sequence**, whenever a gauge reaches 256: (1) **ticks**: Miasma, Cantabile, Dawn (party only), Wading regeneration (§10.2); (2) **Coda** −1, Swoon at 0 (Encore triggers if held); (3) **skips**: Stun, Stagefright, Reverie (gauge to 0); (4) **action**: the command window or `ON TURN`; (5) **end of turn**: timed statuses count down and expire at 0; Swell loses a stack every second turn.

**Phantom turns.** Fermata (gauge frozen) and Unwritten (off the field) count down on *phantom turns*, one every 256 ÷ ((TMP + 25) × 1.6 × SpeedSet) seconds. Fermata bearers still tick Miasma and Cantabile; Unwritten bearers tick nothing. Reserve members' timers are frozen.

### 3.7 Edge cases (binding)

| # | Case | Ruling |
|---|---|---|
| 1 | Gauges fill on the same frame | Party before enemies; party by slot 1→4; enemies by formation index (front rank first, then top to bottom) |
| 2 | Target gone at resolution | Offensive single-target actions retarget at random on the same side; heals and buffs go to the lowest-HP% living ally; a revive whose target is up goes to another Swooned ally; with no valid target the action fizzles, nothing spent |
| 3 | Actor disabled before resolution (Swoon, Marble, Reverie, Stun, Stagefright, Fermata, Unwritten; Hush for blocked commands) | Cancelled, nothing spent, gauge refills from 0 |
| 4 | INS short at resolution | "Not enough INS": the turn is spent |
| 5 | Swoon while Ready or in Tacet | Gauge empties; the member leaves the queue |
| 6 | Revival and Swap entry | Gauge 0 after a revive; 128 after Encore or Swap (CANON §11a) |
| 7 | Fermata on a full gauge | Stays full but cannot act or join Synergies; keeps its queue place |
| 8 | Stun on a Ready member | The pending turn is lost at once |
| 9 | Conduct | A P1 bonus action; the ally's own gauge is untouched |
| 10 | Counters | No ATB; P1 straight after the trigger; **never trigger counters**; at most one per unit per triggering action (a multi-hit is one action) |
| 11 | Phase change with a queued boss action | The boss's action is discarded; party actions proceed against the new phase |
| 12 | Battle ends mid-queue | Unresolved actions are discarded, nothing spent |
| 13 | Recital break | Tested per hit after mitigation: one hit ≥ 20% of Min-jun's max HP |
| 14 | Last two members fall to one action | The wipe check runs once, after the action resolves |

---

## 4. Command Menus

### 4.0 Unlock schedule (CANON §4a)

Battle systems arrive chapter by chapter; a system not yet listed is absent from menus, HUD and enemy scripts. Everything later in this document assumes its row has been reached.

| From | Battle systems added | Notes |
|---|---|---|
| CH-01 | Fight / RECITAL / Item; Defend; REP-00 *Resonance*; **Harmony** appears when Min-jun learns his first HRM | Single row (no Row entry); no Crescendo strip, Synergy, Cadenza, Tacet or Onlookers. Light modifiers already apply (Chiaroscuro reads them from CH-03) but the icon is hidden |
| CH-02 | ORCHESTRATE (Berlioz joins mid-BOSS-02 by Libretto `JOIN`, §13.6); Pilfer (Cartouche Glove, tavern cellars) | Out of battle: the Secrecy Meter |
| CH-03 | **Row**; party of 3; CANVAS with *Sketch* locked | Alkan (guest) has Fight, Defend and Item; his ÉTUDE arrives when he joins |
| CH-04 | **Crescendo strip** (boss battles start at 50 from BOSS-05); first Synergy SYN-08 (taught in BOSS-05); **Tacet**; **Onlookers and Heat**; CONDUCT (end of chapter); ÉTUDE (Alkan joins) | Duos learned earlier at rank 3 become usable here |
| CH-05 | **Light State icon** (BOSS-06 is the tutorial); PLEIN AIR with *Shift the Hour*; Opus Score Harmony and **Invocations**; party of 4 + reserve | T2 commands (§1) |
| CH-06 | RUBATO | — |
| CH-07 | TRANSCEND; *Sketch* and Studies | — |
| CH-08 | In-battle **Swap**; COUNTERPOINT; the **Unwritten** status | — |
| CH-09 | **Cadenza** (Min-jun's cell escape is the tutorial) | Split control (§11.8) |
| CH-10 | POINTILLÉ | T3 commands |
| CH-13 | MEPHISTO (*Transcribe*); Min-jun's own works in RECITAL (§4.6) | Three-front battle (§11.2) |
| CH-14 | IMPASTO; IMPROVISE (Julien, SQ-21) | T4 commands |
| CH-16 | Octave formation and *Voice* (§6.7) | — |
| CH-E1 | BOW, BEAT, SYN-17–19, Remembrances, LUMIÈRE | Seoul roster only (CANON §11a) |
| CH-E2 | LUMIÈRE; SYN-16 as a normal Synergy | No Onlookers or Heat |

### 4.1 The standard menu and controls

**Command window** (over the enemy list): **Fight / *Unique* / Harmony / Synergy / Item** (CANON §11a), as unlocked (§4.0). *Synergy* shows only while one is executable (§6.2); **Fight becomes Cadenza** when the member qualifies (§7), and ◄► on it toggles back. **►** opens the side menu: **Row · Defend · Tacet · Swap · Pilfer** (Cartouche Glove).

| Button | Function |
|---|---|
| A / B | Confirm / back |
| Y | Pass the window to the next Ready member |
| X | Toggle the help line (description and INS cost) |
| L or R (tap) | In target mode: switch side, or toggle single/all on a spreadable action |
| L + R (hold) | Flee (§12.1) |
| Select | Toggle enemy names / Annotated bars |
| Start | Pause |

### 4.2 Fight

A physical attack on one target (CANON §10b damage, hit and crit). Batons, Quills and Folios are row-free; every other weapon is melee. Passives reading Fight: *Idée Fixe*, *Bravura*, *Sideman*, *Recluse*. Frenzy and Delirium force it.

### 4.3 Harmony

Learned Harmony skills (HRM): the equipped Opus Score's **Invocation** first, the rank-5 **Signature** second, the rest in the order `skills_and_progression.md` assigns.

- **Costs** multiply and round half up: Out of Tune ×1.5, Inspired ×0.5, both ×0.75. **Spreadable** skills toggle single/all with L or R (×0.5 per target). **Hush** blocks the menu, Invocations included.
- **Invocations:** no INS, once per battle (Berlioz twice), Heat 3 when ✦ (CANON §11c).
- **Remembrances (CH-E1)** appear on their own line directly below the equipped Score's Invocation; both remain usable. Each keepsake received (KEY-30) is usable once per battle (CANON §6), and each Seoul member may call **one** per battle. A Remembrance casts the giver's Cadenza (§7) on the giver's Lv-50 stats (Lv 55 after the busking ladder; formulas_and_curves §7.1), with its second phase if the giver was a confidant. A missed farewell means no keepsake and no line.

### 4.4 Item

One consumable per action, at the fixed amounts of CANON §14. Items ignore rows, Mirror and Hush, cannot target an Unwritten unit and never revive enemies.

### 4.5 The side menu

| Entry | Effect | Gauge after |
|---|---|---|
| **Row** | Switch the actor's row at once | **128** (half a turn) |
| **Defend** | Damage taken ×0.5 until the actor's next turn (CANON §10b); with Varnish or Glaze, ×0.25 | 0 |
| **Tacet** | Hold the full gauge; DEF/RES +25% until the member acts (CANON §10d); pass the window | 256 (held) |
| **Swap** | Choose the outgoing slot (the actor, **or a Swooned or Marbled ally**) and a reserve, who enters at 128. Not in forced-party battles (CANON §11a), duels or the Octave; guests stay. The leaver keeps HP, INS and statuses (timers frozen) but loses tokens, charges, stacks and chains; swapping Min-jun out ends his Recital without Stagefright | Actor's turn spent |
| **Pilfer** | Cartouche Glove only. clamp(40 + LCK_a − LCK_t, 5, 95)%; 1 success in 8 takes the rare slot (CANON §11a). Once per enemy; then "Nothing left to take." | 0 |

### 4.6 Unique commands

#### PC-01 Min-jun — RECITAL and CONDUCT

The **Recital** sub-list shows **Conduct** (from the end of CH-04), then **Continue** and **Da Capo** while a Recital is active, or else the Repertoire with each piece's Heat pips and INS cost (**6 + 2 × Heat**, CANON §10b).

| Step | What happens | Crescendo |
|---|---|---|
| **Movement I** | INS paid once; if an Onlooker remains, the piece's **Heat is added once, now** (CANON §11e); effect A begins | — |
| **Continue → II** | Effect B joins A | +3 |
| **Continue → III** | Burst C; the Recital ends | +3 |

- **Effects.** *Modifiers* ("LIGHT +25%", "party TMP +10%") last while the Recital is active and multiply with the Light. *Statuses* are applied at their movement, re-applied (re-rolled on enemies) at the next, and keep their remaining duration afterwards. *Bursts* at III: damage **PWR 1.5 × Pₜ**, healing **1.5 × Hₜ** (formulas_and_curves §8.4; ×0.5 spread when all-target), revival at 50% HP.
- **REP-00 *Resonance*** (INS 6, Heat 0) has two movements: I Stuns every Echo-family enemy (base 60; BOSS-01's core excepted); II shatters props tagged `bonewall` (BOSS-01's bone wall) and ends the piece. No III.
- **Own works.** From CH-13 his own works (REP-27, REP-29, REP-30) join the battle Repertoire at Heat 0 (CANON §5c). CANON §15d gives them no movement effects, so a CCR in the final section proposes them; until it is adopted each movement gives only its +3 Crescendo (§6.3).
- **Ending vs breaking.** Any other command (Swap and every Synergy except SYN-03 included) **ends** it with no penalty. A hit ≥ 20% of max HP, Hush, Stagefright, Reverie or Fermata **breaks** it: auras stop and he suffers **1 turn of Stagefright** (CANON §5c). REP-20 survives Hush. Swoon or Marble ends the Recital (auras stop, no Stagefright); Stun costs his turn but the Recital holds. A Recital survives waves and front switches.
- **Branches.** CH-E2 battles keep every learned REP at no Heat (CANON §11e); in CH-E1 Recitals never feed the Spotlight Meter.
- ***Da Capo*** (any movement; his turn; no INS, Heat or Crescendo): returns the piece to Movement I (B drops, A stays) and **resets every party member's Coda count**: the "Recital *Da Capo*" of CANON §10d.
- ***Conduct*** (0 INS): one ally takes an **immediate bonus action at ×1.25** to damage, healing and Étude power; the ally's gauge is untouched; the Recital neither ends nor advances (CANON §5c). Never the same ally twice running; never a Synergy, Cadenza, Swap or Flee; a Conducted Étude cannot fail; a Conducted IMPRESSION keeps its chain; allies who cannot choose (Reverie, Stagefright, Stun, Fermata, Frenzy, Delirium, Marble) cannot be Conducted.
- ***Perfect Pitch***: immune to Out of Tune and Discord, and to Unwritten until CH-17 (CANON §5c).

#### PC-02 Lucile — PLEIN AIR (and *Shift the Hour*)

| Style | From | INS | Target | Power | Element | Rider | Heat |
|---|---|---|---|---|---|---|---|
| **IMPRESSION** | CH-05 | Cₜ | One enemy | Pₜ; **+20% per consecutive IMPRESSION turn**, max +100% | The Light's first boosted element (table below) | — | 2 |
| **POINTILLÉ** | CH-10 | 1.5 Cₜ | 8 hits on random enemies, **or** 8 dots on random allies | 8 hits sharing one Pₜ term (Pₜ/8 each), no spread penalty | Light's first boosted element | Each hit adds a **Dot**; at 10 Dots the enemy is **Composed** (3 turns) and its Dots reset. Ally mode: each dot gives a random living ally Cantabile, Allegro or Varnish (repeats refresh) | 3 |
| **IMPASTO** | CH-14 | 2 Cₜ | One enemy | 1.5 Pₜ | Light's first boosted element | **Sets Night**; Discord (base 40); Lucile gains Allegro | 4 |
| *Nuit étoilée* | (IMPASTO under Night) | 2 Cₜ | 8 hits on one enemy (fixed multi-hit, formulas §4.5) | 8 hits sharing IMPASTO's 1.5 Pₜ term | **LIGHT + SHADE** (dual) | Each landing hit restores 2% of max INS to every party member | 4 |
| **LUMIÈRE** | Epilogues | 1.5 Cₜ | All enemies | 2 Pₜ, ×0.5 spread; **+1% per Hanmadi word** in CH-E1 (max +40%) | Best boosted element of either Light (dual rule) | Sets **two** Painted Lights of her choice (§8.3) | 2 |

| Light | Dawn | Noon | Dusk | Night | Candle | Fog | Gloom |
|---|---|---|---|---|---|---|---|
| First boosted element | LIGHT | FIRE | WATER | SHADE | FIRE | WATER | SHADE |

- **Chain:** any other action by Lucile, Shift the Hour included, resets IMPRESSION's bonus; being hit does not. **Dots** persist all battle (n/10 overhead); only POINTILLÉ adds them.
- ***Shift the Hour*** (0 INS, her turn, Heat 0): set Dawn, Noon, Dusk or Night until something else replaces it (§8.3).
- ***Plein Air*** (passive): styles +25% under Dawn, Noon or Fog; affinities shown on her cursor; preemptive +25 percentage points outdoors (§5.2). **Fracture** (CH-09 to Mending 2) only locks her Synergies with Min-jun (CANON §11f).

#### PC-03 Berlioz — ORCHESTRATE

***Cue*** (0 INS, his turn) adds one section token (max 3; a fourth pushes out the oldest) and fires a small effect at once:

| Section | Immediate effect |
|---|---|
| Strings | Heals the lowest-HP% ally, heal PWR 0.5 Hₜ |
| Winds | WIND hit on one enemy, PWR 0.4 Pₜ; its gauge −10% |
| Brass | **Clears every Onlooker** (CANON §11e); Berlioz gains Swell +1 |
| Percussion | EARTH hit on one enemy, PWR 0.4 Pₜ; Stun (base 30; bosses immune unless stated) |
| Chorus | One ally: cures Hush and grants Cantabile |

***Tutti*** (Cₜ INS) consumes the tokens and fires the summon whose recipe (TUT-01–20) matches, order irrelevant (CANON §5c). **Budget by token count** (formulas_and_curves §8.4): 1 token **Pₜ**, 2 tokens **2.0 Pₜ**, 3 tokens **3.0 Pₜ**, single target; all-target recipes take ×0.5 spread; each rider (a status, a Light, a party buff) costs 20% of the power. Unknown combinations play ***Cacophony*** (one random enemy, non-elemental, T1 PWR 12). Known recipes light up in the token tray as soon as the tokens match; e.g. Brass + Brass + Percussion = ***Marche au supplice*** (EARTH + FIRE, massive single target).

- Not blocked by Hush (he conducts; he does not sing). Tokens survive waves and front switches and are lost on Swoon, Marble, Unwritten or Swap. **Invocation** twice per battle. ***Idée Fixe***: consecutive Fights on one target +15% each, max 3 stacks (CANON §5c); anything else resets it.

#### PC-04 Delacroix — CANVAS (and *Sketch*)

**Free Canvas** (Cₜ INS): two different unlocked Pigments and a Subject: one enemy ×1.0, one rank ×0.75, all ×0.5; PWR Pₜ; dual-element rule (CANON §10c). A painted strike: it ignores row and is never reflected. **Named recipes** (Studies and story; listed in `skills_and_progression.md`) fix pigments and subject and add one rider, e.g. ***Sardanapale*** (FIRE + SHADE, Stagefright), ***Chios*** (ICE + WATER, all enemies), ***Liberté*** (FIRE + WIND, party Fortissimo); some set a Light.

| Pigments | FIRE, WIND | EARTH, WATER | ICE, BOLT | SHADE | LIGHT |
|---|---|---|---|---|---|
| Unlocked | At join (CH-03) | CH-05 | CH-08 | CH-10 | Bond rank 10 |

***Sketch*** (0 INS, never misses) records an enemy's Study (STU-01–36, from its Libretto `STUDY` line) **once the enemy has used the linked action this battle**: "I paint movement, not statues." Otherwise a **Rough Sketch** reveals HP and affinities for the battle. Aimed at an Onlooker, it clears that Onlooker (CANON §11e).

- ***Chiaroscuro***: Canvas +25% under Dusk, Night or Candle; 25% chance to counter, with a P1 Fight, the enemy that Swoons an ally (CANON §5c).

#### PC-05 Alkan — ÉTUDE

Select an Étude: the input staff opens and the battle clock stops. Enter its sequence (3–8 inputs drawn from ↑ ↓ ← → A B X Y L R) within **2.0 s** (CANON §5c). Correct: the Étude fires. Wrong input or timeout: ***Fausse note***, a plain Fight. No INS.

- **Power budget** (formulas_and_curves §8.4): physical formula, AR × the Étude's multiplier, **×1.5 for a 3-input Étude rising to ×3.0 for 8 inputs; the Lv-50 Étude ×3.5**, divided evenly across hits. Études always hit, ignore row and may carry an element or set a Light. Learned at Lv 11 (3), 14, 18, 22, 26, 30, 34, 38, 43 and 50.
- **Conducted:** cannot fail, ×1.25. **Rehearsal Mode:** perfect at ×0.8 (CANON §11j).
- ***Recluse*** (passive): when he is the last member standing or the only member in the back row, he holds **Bulwark** (refreshed each turn while the condition lasts) and +25% STR.

#### PC-06 Chopin — RUBATO

| Sub-command | Effect |
|---|---|
| ***Borrow*** (0 INS) | One enemy's gauge −77 (30%); store 1 charge (max 3). At bond rank 10, ***Tempo Rubato***: Borrow hits all enemies (still +1 charge) |
| ***Repay*** (0 INS, needs ≥ 1 charge) | Give all charges to **one other** ally, +87 gauge (34%) each; 3 charges = an immediate turn: the recipient's gauge is set to 256 and it moves to the head of the Ready queue. Repay on a Fermata bearer **cures Fermata** first (CANON §10d) |

- Charges survive waves and front switches; they are lost on Swoon, Unwritten or Swap. A boss whose Libretto lists `IMMUNE atb` ignores Borrow.
- ***Sotto Voce*** (passive): enemy random targeting weight 0.5 (§13.4); his heals +20%; max HP −10% (CANON §5c).

#### PC-07 Liszt — TRANSCEND → MEPHISTO

- ***Transcend***: two Harmony skills, each with its own target, in one action for **total INS × 1.5** (CANON §5c); Bravura applies to both; blocked by Hush.
- ***Transcribe*** (from CH-13, when the command becomes **MEPHISTO**): re-perform the **last skill used in the battle by anyone** at ×1.25 (CANON §5c). Copyable: Harmony skills, enemy skills, a Recital's Movement I, a Tutti. Everything else (Fight, items, other unique commands, Cadenzas, Synergies, `UNIQUE` skills) is skipped when the log is read. Cost: the original INS, or 10% of his max INS for an enemy skill. A copied Movement I applies once and carries its Heat; a copied Tutti needs no tokens.
- ***Bravura***: +10% damage per consecutive action without being hit (max +50%); any enemy action that connects with him resets it.

#### PC-08 Farrenc — COUNTERPOINT

| Sub-command | INS | Effect |
|---|---|---|
| ***Annotate*** | 0.5 Cₜ (min 2) | Scan (stats, affinities, steals, Study; logged to the Almanach); shows its ATB bar; highlights one weakness on every cursor; places **3 crit marks**: the next 3 party hits on it crit (one mark per hit of a multi-hit; Synergies and Cadenzas never crit and use none) |
| ***Canon*** | Cₜ | Marks one ally for 2 rounds (2 of the ally's turns); after each of their actions she echoes at P1: an attack → heal PWR 0.5 Hₜ on the lowest-HP% ally; a heal → hit PWR 0.5 Pₜ on that ally's last target or a random enemy |
| ***Fugue*** (Lv 22) | 1.5 Cₜ | 3 rising hits on one enemy, each 0.6 Pₜ: EARTH → WATER → LIGHT |
| ***Cadence*** (Lv 30) | 1.5 × heal INS | Party **cleanse** (§9) and heal PWR 0.5 Hₜ, no spread penalty |

- ***Equal Measure*** (passive): reserve members receive 100% EXP while she is active (CANON §5c, §10a).

#### PC-09 Seo-yeon — BOW

No INS. The command shows its mode; ◄► switches **Sostenuto / Spiccato** without spending a turn (CANON §5c).

- ***Sostenuto***: party heal PWR Hₜ, ×0.5 spread (formulas_and_curves §8.4), **+25% for each consecutive Sostenuto turn** (max +100%), and the party holds Cantabile while she keeps choosing it. Any other action ends the chain.
- ***Spiccato***: 4 hits on random enemies, each ×0.4 her Fight damage, no spread penalty (formulas_and_curves §8.4); ignores row (command).
- ***Sibling*** (passive): +20% TMP while Min-jun is active.

#### PC-10 Jae-won — BEAT

A ring closes on each beat of the current *jangdan*; press A on the beat. **Perfect** = ±3 frames (60 fps), **Good** = ±8, anything else ends the combo. Up to 8 hits on one enemy, each 0.3 × his Fight damage × **(1 + 0.1 per Perfect)** (max ×1.8; a perfect 8-hit BEAT is ×4.3 a Fight, formulas_and_curves §8.4). A **perfect 8-hit BEAT also steals** (Pilfer's roll, success guaranteed; CANON §11a). No INS. Rehearsal Mode: all Perfect at ×0.8, steal included.

| *Jangdan* | Levels | Beat interval |
|---|---|---|
| *Semachi* | 40–42 | 0.67 s |
| *Gutgeori* | 43–45 | 0.50 s |
| *Jajinmori* | 46–48 | 0.38 s |
| *Hwimori* | 49+ | 0.25 s |

- ***Groove*** (passive): all Crescendo gains ×1.25 while he is active.

#### PC-11 Julien — IMPROVISE

Three reels of chord symbols (ii, V, I, IV, ♭VII, ♭II), each in a different order, spin at 10 symbols/s; A stops them left to right (CANON §5c). No INS. Rehearsal Mode slows them to 4 symbols/s. **Every Improvise is Anachronic, Heat 3**; Tritone Storm, being CHRONO, is Heat 5 (the highest Heat in an action applies).

Results marked CANON §5c are canon; numbers follow formulas_and_curves §8.4; the other results are this doc's.

| Reels | Result | Effect |
|---|---|---|
| ii – V – I (in order) | ***Turnaround*** (CANON §5c) | Party heal PWR Hₜ, ×0.5 spread |
| ♭II ♭II ♭II | ***Tritone Storm*** (CANON §5c) | CHRONO to all enemies, PWR 2 Pₜ, ×0.5 spread |
| V V V | *Dominant* | Party Allegro |
| I I I | *Tonic* | Party Varnish |
| IV IV IV | *Amen* | Encore on the living ally with the lowest HP% |
| ♭VII – IV – I (in order) | *Backdoor* | Party cleanse |
| ii ii ii | *Dorian Vamp* | Swing on all enemies (base 60) |
| ♭VII ♭VII ♭VII | *Flat Seven* | Lento on all enemies (base 60) |
| Anything else | ***Blue Note*** (CANON §5c) | One random enemy, non-elemental, PWR Pₜ |

- ***Sideman*** (passive): +20% damage when the previous resolved action was an ally's.

### 4.7 Guests (CANON §6)

Guests use their CANON §6 commands, take an active slot at the chapter anchor level, gain no EXP and cannot be re-equipped, swapped, or join Synergies or Cadenzas; their HP loss and kills still feed the Crescendo. AI guests run a mirrored Libretto (§13.7). Only system values are added here.

| GST | Command | Control | Added values |
|---|---|---|---|
| GST-01 Mathurin | LANTERN | P | Reveals Unseen enemies (§10.2); Smoke base 70 |
| GST-02 Sand | NOVEL | P | *Satire*'s DEF −25% lasts 5 turns; Nohant wave only |
| GST-03 Corot | SOUVENIR | P | Heal PWR Hₜ, ×0.5 spread |
| GST-04 Clara | PRODIGY | AI | Libretto in §13.7 |
| GST-05 Mendelssohn | HEBRIDES | P | Wave PWR Pₜ, ×0.5 spread |
| GST-06 Czerny | VELOCITY | P | — |
| GST-07 "Florestan" | FLORESTAN / EUSEBIUS | AI | Switches persona after every 2 actions |
| GST-08 Offenbach | GALOP | P | Weights out of 16: trip, screech, pocket-pick, cheer, can-can kick 3 each; pratfall 1 |
| GST-09 Marthe | TRIAGE | P | Once per battle, then Fight only |
| GST-10 Thalberg | THREE HANDS | P | Each hit 0.5 Pₜ |
| GST-11 Théo | — | — | Escort, 2,000 HP (§11.4) |

---

## 5. Rows, Formations, Targeting, Reflection and Counters

### 5.1 Rows

- **Party:** front or back (CANON §10b). The back row halves melee dealt and taken: melee-weapon Fights and enemy skills tagged `melee` (every Libretto `FIGHT`). Everything else is row-free: Batons, Quills, Folios, Harmony, unique commands, items, Synergies, Cadenzas.
- **Enemies:** each stands in the **front** or **back rank**. While a front-rank enemy stands, the back rank takes and deals ×0.5 melee; once the front rank is empty, the back rank counts as front.
- **Forced row changes** come only from Libretto `ROWSWAP` and `PULL` (BOSS-10's sluices, BOSS-28's Right Manual and Pedalboard, BOSS-29's trains; CANON §13). The answer is always **Row** (half a turn, §4.5).

### 5.2 Formations

Rolled in order on a random encounter: Preemptive, then Back Attack (only if no Preemptive), then on *open* maps Pincer and Side Attack. Chances for the first two are formulas_and_curves §4.10; ΔLCK = party mean LCK − enemy mean LCK.

| Formation | Chance | Layout | Opening gauges | Rows | Flee |
|---|---|---|---|---|---|
| Normal | Remainder | Enemies left, party right | Each unit random 0–(2 × TMP) (CANON §10b) | As set | Normal |
| Preemptive | clamp(6 + ΔLCK/4, 2, 16)%; +25 percentage points outdoors with Lucile active (Plein Air), max 40% | Normal | Party 256, enemies 0 | As set | Normal |
| Back Attack | clamp(4 − ΔLCK/8, 1, 8)%, only if no Preemptive | Mirrored: party left, enemies right | Party 0, enemies random | **Reversed** for the battle (CANON §10b) | ×0.5 |
| Pincer | 2%, rolled after both fail, only on maps `dungeons.md` flags *open* | Enemies on both sides; party in one column at x 112–175 | Random | **None**: every member counts as front, both ways | ×0.5 |
| Side Attack | 2%, rolled after Pincer fails, *open* maps only | Party split 2 + 2 at both edges; enemies centred | Party 256, enemies 0 | Enemy ranks ignored (all front) | First check succeeds |

Boss and scripted battles are Normal unless their script says otherwise; relics may alter the chances (`items_and_equipment.md`).

### 5.3 Targeting

| Scope | Rule |
|---|---|
| Single | Default cursor: offensive → this member's last target (*Cursor Memory*, §14) or the front-most enemy; heal → the lowest HP% ally; buff → self |
| Spread | L or R toggle on spreadable skills; ×0.5 per target |
| Rank | One enemy rank, ×0.75 per target (Canvas, SYN-21, rank skills) |
| All | All-target skills; ×0.5 per target unless the skill states its own budget |
| Random multi-hit | Each hit picks a random valid target |
| Fixed multi-hit | All hits on one target; once it falls, the rest go random |

**Untargetable:** Unwritten units, sealed members (§13.6), Unseen enemies (single-target actions only, §10.2), Onlookers (except by Sketch), BOSS-17's conductor (CANON §13); enemies skip Marble members. Single-target actions may hit an ally on purpose (to wake Reverie or Delirium); spread actions hit only the chosen side.

### 5.4 Reflection (Mirror)

1. Mirror (3 reflections, CANON §10d) bounces **single-target Harmony skills and single-target `magical` enemy skills** aimed at its bearer, harmful or helpful, to a random living unit on the side opposite the bearer, with the caster's stats.
2. Never reflected: spread, all-target and random multi-hit actions, Canvas, Études, Recitals, Tuttis, Invocations, Synergies, Cadenzas, items, Fight, `physical` skills.
3. A bounced spell never bounces again. The FF6 trick is legal: cast a single-target spell at your own Mirrored ally to rebound it onto the enemies.

### 5.5 Counters and interceptions

- **Counters** (Libretto `ON HIT`, Chiaroscuro, relics) follow edge case 10 (§3.7): P1, no ATB, never chained, at most one per unit per triggering action, aimed at the attacker by default.
- **Bulwark interception.** When a single-target enemy action targets an ally below 25% max HP, a living Bulwark bearer other than the target takes it with its own defences and Bulwark's ×0.5; with several bearers, the highest current HP% steps in. Spread and random hits are never intercepted. Wards count as allies (§11.4).

---

## 6. Harmony, Synergy and the Crescendo Gauge

### 6.1 The two families compared

| | **Harmony** (HRM) | **Synergy** (SYN) |
|---|---|---|
| What | One member's solo art or spell: the brief's "Sheet-Music Magic" | A combination technique of 2, 3, 4 or 8 members |
| Learned | Opus Scores (OP progress) and levels; the rank-5 Signature (CANON §11c, §11f) | Bond ranks, Ensemble Scenes, story (CANON §11b; per entry in §6.5) |
| Cost | INS by tier (CANON §10b) | **Crescendo only**: Duo 100, Trio 200, Quartet and Octave 300. No INS |
| Who must be present | The caster | **Every listed member** in the active party, able to act, with a **full gauge** |
| ATB | The caster's turn | Empties **every** participant's gauge |
| Blocked by | Hush | On any participant: Hush, **Discord**, Reverie, Stagefright, Stun, Fermata, Frenzy, Delirium, Marble, Swoon, Unwritten; for MJ + LU Synergies, Lucile's Fracture (CANON §11f) |
| Crit / miss | Can crit; damage spells always hit | **Never crit, never miss** |
| Row, Mirror | Ignore row; single-target ones can be reflected | Ignore row; never reflected |
| Heat | CHRONO skills 5; ✦ Invocations 3 (secrecy_and_trust §2.4.1) | Per secrecy_and_trust §2.4.1 (listed under §6.5) |

### 6.2 Synergy procedure

1. **Eligible** when Crescendo ≥ cost and every member is active, Ready (full gauge, waiting or in Tacet) and unblocked.
2. *Synergy* appears in the window of the eligible member heading the Ready queue (CANON §11b), listing every executable Synergy.
3. On confirmation the cost is paid, every participant's gauge drops to 0, Tacet ends, and the Synergy resolves at **P1** (§3.4), so no partner can fall in between.
4. Joining any Synergy except SYN-03 ends Min-jun's Recital (no penalty). "Last" Synergies (SYN-04, 07, 11, 22) stay greyed until their source occurs; SYN-04, 07 and 22 consume their record when fired. Synergies cannot be Conducted, Transcribed or copied by SYN-11.

### 6.3 The Crescendo Gauge (0–300; CANON §11b)

| Source | Gain | Clarification |
|---|---|---|
| HP lost | +1 per 1% of max HP, per member | Actual HP lost (overkill excluded), fractions carried per member; guests count, wards do not; a Swoon by Coda counts the HP it removes |
| Recital movement advanced | +3 | Movements II and III, including SYN-03's advance; not Movement I or Da Capo |
| Weakness hit | +2 per hit | Every hit of a multi-hit; Synergy hits count |
| Enemy defeated | +5 | Routed, subdued, dissolved or collapsed; summoned adds count; enemies that leave by their own script give 0 |
| Recital effects | REP-07 Movement III +30; REP-22 +20 per turn (CANON §15d) | — |
| Groove | All gains ×1.25 while Jae-won is active | — |

A **Discorded** member's HP loss, weakness hits and kills give nothing (CANON §10d). The gauge starts at **0 (50 in boss battles from BOSS-05; the gauge does not exist before CH-04)**, carries across waves and fronts, resets after the battle (the CH-16 sequence excepted, §11.8), and also pays for **Cadenzas** (100, §7). Vane's *Wager* stakes it in BOSS-20 (CANON §13).

### 6.4 Synergy power

- **Damage:** CANON §10b magical formula with the Synergy's PWR (Duo 160, Trio 220, Quartet 260, Octave 300 per hit). Duo, Trio and Quartet use the participants' **mean ART and mean level** (formulas_and_curves §4.5 rule 3); statuses roll with the mean ART. **The Octave uses Min-jun's ART and level**, which reproduces CANON §10e exactly.
- **Heal parts:** healing formula with PWR 0.4 × the Synergy's (Duo 64, Trio 88, Quartet 104), no spread penalty.
- All-target ×0.5 spread, rank ×0.75. **Multi-hit:** compute the full single-hit damage D; each of *n* hits deals D ÷ *n* before per-target modifiers, each capped at 9,999.
- *Sanity* (numbers only; in play SYN-01 is locked from the CH-09 Fracture): CH-09 Duo MJ + LU (mean ART 28.5, Lv 21) vs BOSS-12 (RES 31): (640 + 57) × 3.0 × 100/131 = **1,596**, 12.3% of 13,000; SYN-01 vs standard enemies (RES 25): 836 each, 73% of 1,140 HP.

### 6.5 The complete Synergy list

Names, members and unlocks are CANON §11b; effects, power, elements and animations are fixed here. Multi-hit targeting follows formulas_and_curves §4.5.

| SYN | Banner name | Members | Unlock | Cost | Effect and power | Element |
|---|---|---|---|---|---|---|
| SYN-01 | Clair de Lune Impression | MJ + LU | LU rank 3; locked from the CH-09 Fracture to Mending 2 | 100 | All enemies, PWR 160 ×0.5 spread; then party heal PWR 64 | LIGHT |
| SYN-02 | Two-Piano Tempest | MJ + LI | LI rank 3 | 100 | 8 hits on one enemy (fixed multi-hit), D ÷ 8 each | BOLT |
| SYN-03 | Rubato Recital | MJ + CH | CH rank 3 | 100 | Party Allegro; the active Recital advances one movement (+3 Crescendo). If none is active, the last piece he played this battle restarts at Movement I for 0 INS (its Heat applies); greyed if he has played none | — |
| SYN-04 | Idée Fixe Fortissimo | MJ + BE | BE rank 3 | 100 | Berlioz's last Tutti this battle fires twice, each at ×0.6 of its power, no tokens needed; firing consumes the record, so SYN-04 greys until Berlioz fires another Tutti; greyed if the last was *Cacophony* or none | Recipe's |
| SYN-05 | Portrait in Shadow | MJ + DE | DE rank 3 | 100 | All enemies, PWR 160 ×0.5 spread; Smoke (base 70) on all | SHADE |
| SYN-06 | Equal Temperament | MJ + FA | FA rank 3 | 100 | Party cleanse (§9); removes every positive status from all enemies | — |
| SYN-07 | Pédalier Duo | MJ + AL | AL rank 3 | 100 | Alkan's last successful Étude repeats at ×1.5, input-free; firing consumes the record, so SYN-07 greys until Alkan lands a new Étude | Étude's |
| SYN-08 | Liberty Leading the Orchestra | BE + DE | Story CH-04 (taught in BOSS-05) | 100 | All enemies, PWR 160 ×0.5 spread | FIRE + WIND |
| SYN-09 | Les Deux Virtuoses | LI + CH | Ensemble Scene, CH-07+ | 100 | 6 hits on one enemy (fixed multi-hit), D ÷ 6 each, rotating FIRE → ICE → WIND → EARTH → BOLT → WATER | Rotating |
| SYN-10 | Chiaroscuro et Lumière | LU + DE | Ensemble Scene, CH-06+ | 100 | Lucile sets the Painted Light the player picks; Delacroix strikes all enemies in its two boosted elements, PWR 160 ×0.5 spread | Light's pair (dual) |
| SYN-11 | Double Fugue | FA + AL | Ensemble Scene, CH-08+ | 100 | The last *offensive* enemy skill used this battle fires twice at enemies, at its user's level and AR/MAR, keeping its targeting; status parts roll with Farrenc's ART. Never copies `UNIQUE` skills | Skill's |
| SYN-12 | Nocturne in Blue | LU + CH | Ensemble Scene, CH-08+ | 100 | Sets Night; Reverie (base 50) on all enemies | — |
| SYN-13 | Brother from Tomorrow | MJ + LU + DE | Story, CH-14 Night of Stars (LU and DE rank 10) | 200 | 4 hits on all enemies, PWR 220 ×0.5 spread, D ÷ 4 per hit | LIGHT + SHADE |
| SYN-14 | Symphony of Tomorrow | MJ + BE + LI | BE and LI rank 8 | 200 | 60% of the budget: Tutti *Songe d'une nuit du sabbat* on all enemies (×0.5 spread, SHADE + FIRE); 40%: the Tempest's 8 BOLT hits on one enemy | SHADE + FIRE, then BOLT |
| SYN-15 | Prometheus | MJ + LU + BE | LU and BE rank 8, CH-14+ | 200 | All enemies, PWR 220 ×0.5 spread; party Inspired (REP-26) | FIRE + LIGHT |
| SYN-16 | Octave of the Lost Era | All 8 permanent members | Story CH-16; usable post-game and in CH-E2 | 300 | 4 hits × PWR 300 on one target; confidant and Blue Note multipliers; rules in §6.7 | CHRONO |
| SYN-17 | Arirang for Two | MJ + SY | Story CH-E1 | 100 | Party Cantabile and Allegro; cures Discord and Swing (as REP-31) | — |
| SYN-18 | Hwimori | MJ + JW | Story CH-E1 | 100 | 8-press BEAT input at *hwimori* tempo whatever Jae-won's level; PWR 160 split into 8 hits; +10% per Perfect; a perfect 8 also steals | — |
| SYN-19 | Samulnori | MJ + LU + SY + JW | Story CH-E1 | 300 | 4 hits on all enemies, PWR 260 ×0.5 spread, D ÷ 4: kkwaenggwari BOLT, jing WIND, janggu WATER, buk SHADE | Four single elements |
| SYN-20 | Blue Hour | JU + MJ + LU | JU and LU rank 8 (optional) | 200 | All enemies, PWR 220 ×0.5 spread; Swing (base 60) on all | SHADE + WATER |
| SYN-21 | Polonaise of Exiles | CH + DE | Ensemble Scene, CH-09+ | 100 | One enemy rank, PWR 160 ×0.75; Stagefright (base 50) | EARTH + ICE |
| SYN-22 | Rival Virtuosi | LI + AL | Ensemble Scene, CH-08+ | 100 | Liszt's last single Harmony attack and Alkan's last successful Étude replay together, each ×1.2, input-free; firing consumes both records, so SYN-22 greys until both sources recur | Each source's |
| SYN-23 | Les Inadmissibles | LU + FA | Ensemble Scene, CH-14+, after the SQ-07 family council | 100 | Lucile sets the Painted Light the player picks; Farrenc Annotates every enemy (scan + 3 crit marks each) and each becomes **weak** to that Light's first boosted element for 3 of its turns, overriding other affinities unless its Libretto says `AFFINITY locked` | — |

**Heat.** A Synergy's Heat is added once, at resolution, if an Onlooker remains (CANON §11e). Values per secrecy_and_trust §2.4.1: SYN-01 3, SYN-02 3, SYN-13 4, SYN-14 3, SYN-15 5, SYN-16 5, SYN-20 3, others 0; Cadenzas MJ 5, LU 2, JU 3.

**Animations** (≤ 8 s each except SYN-16; two effect layers).

| SYN | Animation |
|---|---|
| SYN-01 | Moonlit blue; a piano fades in under Min-jun; Lucile's white dabs fall as healing sparkles |
| SYN-02 | Two pianos slam lid to lid; eight forks of lightning leap from the lids |
| SYN-03 | Chopin borrows a sweep of the clock face and lends it to Min-jun |
| SYN-04 | The last summon plays, freezes on a fermata, then replays with its players doubled |
| SYN-05 | Delacroix sketches Min-jun in black chalk; the drawing swells into a curtain of shadow |
| SYN-06 | Farrenc rules eight staff lines; Min-jun's scale snaps them true; status icons untie |
| SYN-07 | A pedal drone; Alkan's Étude replays at double size on a rising pedal keyboard |
| SYN-08 | The tricolour sweeps across; flame and wind become spectral brass and woodwinds charging |
| SYN-09 | Four hands at one keyboard; six coloured notes burst on the target in turn |
| SYN-10 | Lucile washes the sky with the hour; Delacroix slashes a two-colour stroke through it |
| SYN-11 | Farrenc writes the enemy's move on a staff; Alkan's inversion strikes its owner twice |
| SYN-12 | Prussian-blue night pours down; a nocturne; the enemies' outlines soften and slump asleep |
| SYN-13 | Candlelight on Min-jun at the keyboard; Delacroix's black chalk races to catch the scene while Lucile flicks broken-touch stars across a window behind him; before the drawing can resolve, four bands of gold and shadow pour out of the window onto the enemies |
| SYN-14 | The sabbath's *Dies irae* bells flood in; two pianos rise from it for eight bolts |
| SYN-15 | A ring of spectral players; Lucile paints each chord its colour; a white-gold eruption |
| SYN-16 | §6.7 |
| SYN-17 | Violin and hummed *Arirang* fall as soft snow that settles on the party as light |
| SYN-18 | Janggu against piano, faster and faster, rings closing at *hwimori* speed; the screen shakes |
| SYN-19 | The four advance like a *pungmul* troupe: kkwaenggwari bolt, jing wind, janggu rain, buk clouds |
| SYN-20 | Twilight blue; a spectral bass walks; Lucile drags blue-black across the screen in swing time |
| SYN-21 | A polonaise rhythm; Delacroix paints a frozen Polish field that heaves under one rank |
| SYN-22 | Split screen: Liszt's spell and Alkan's Étude land on the same downbeat |
| SYN-23 | Lucile paints the hour; Farrenc's red-ink margin notes glow over every enemy in its colour |

SYN-13 never shows the composed portrait, the hangul score or the fallboard tap: those are reserved for LAW-26 and MUS-150.

### 6.6 Coverage notes

Min-jun pairs with all seven friends, and eight friend-to-friend Duos exist (BE–DE, LI–CH, LU–DE, FA–AL, LU–CH, CH–DE, LI–AL, LU–FA); every permanent member (PC-01–08) has at least four Synergies. The other thirteen friend pairs, and the three members without a Trio (Chopin, Alkan, Farrenc), are deliberate gaps: such parties play on solo commands and Cadenzas. Two gap-fillers are proposed as CCRs in the final section; neither is used here.

### 6.7 The Octave of the Lost Era (SYN-16)

**In BOSS-27 (CANON §11b):**
1. All 8 permanent members stand in the Octave formation (§2.1). Julien, if recruited, stands behind the Engine and adds his **Blue Note** automatically.
2. Each unique command becomes **Voice**; Fight, Harmony and Item remain. Voice is free, uses the turn, lights the member's LM-01 note (MJ D, BE E, DE F♯, AL G, CH A, LI B, FA C♯, LU the octave D; CANON §15c) and **restores one second** of the countdown. Once per member. Voice ignores Hush but is **blocked by Discord**, which makes the Pitch Pipe the party's key item here.
3. The eighth note fires SYN-16 at P0: no Crescendo cost, any order.
4. 4 CHRONO hits × PWR 300, Min-jun's ART and level, × **(1 + 0.10 × confidants + 0.09 with Julien)**: ×1.30 to ×1.79, exactly as CANON §10e checks.
5. The countdown is a Stasis clock (§11.6); `bosses.md` sets its values.

**Animation** (15 s, skippable on repeats): the music drops to a held chord; each note rises as a pillar of light in its friend's colour key (CANON §5g); the pillars bend into one beam over the Stilled Hour; four strikes each crack a quarter of its clock face; white flash, then silence.

**Outside BOSS-27 (CH-E2 and post-game):** a normal Synergy for 300, once per battle, when the active four are Ready and all eight permanent members are in the roster with none in reserve Swooned (the reserve four join the animation). Same four hits on one enemy (retargeting if it falls), same multipliers; Min-jun's ART and level if he is active, else those of the highest-ART active member. It does not exist in CH-E1, where the Remembrances stand in for the friends.

---

## 7. Cadenza (Desperation)

Qualification, cost and unlocks are CANON §11d (from CH-09, §4.0). **Fixed here:** damage is **magical PWR 180** on the member's ART, or **physical ×4.0** (Fight's formula; *La Machine* and *Encore Stage*); healing is **PWR 150** (formulas_and_curves §8.4). Cadenzas never crit or miss, ignore row and Mirror, split multi-hits D ÷ *n* and take ×0.5 spread when all-target. ◄► reverts the entry to Fight. Hush does not block a Cadenza; Discord does. A confidant's **second phase** follows in the same banner and adds 50% of phase 1 plus its listed rider; it also plays for **Min-jun once he has 3 confidants** (certain from CH-14), always for Seo-yeon (she already knows), for Jae-won once told (CH-E1) and for Julien after BQ-PC11. *Sanity:* Min-jun at Lv 40 (ART 42.25) against a Lv-40 boss (RES 54): (720 + 84.5) × 4.9 × 100/154 = **2,560**, more than a Duo at mean ART 42.25 (2,305) or a T4 spell (1,287) in one member's turn: the payoff for fighting at ≤ 25% HP.

| Member | Cadenza (CANON §5c) | Formula | Phase 1 | Element | Phase 2 rider (after 50% of phase 1) |
|---|---|---|---|---|---|
| PC-01 | *Gaspard Unbound* | Magical | 3 hits on all enemies (Ondine, Le Gibet, Scarbo), ×0.5 spread | WATER, SHADE, SHADE | Delirium (base 50) on all enemies; party Allegro |
| PC-02 | *Lever du jour* | Magical | Sets Dawn; all enemies, ×0.5 spread | LIGHT | Party Cantabile and Varnish |
| PC-03 | *Dies irae* | Magical | One enemy | SHADE + EARTH | Stagefright (base 50) on all enemies |
| PC-04 | *La Liberté guidant* | Magical | One enemy rank, ×0.75 | FIRE + WIND | Party Fortissimo |
| PC-05 | *La Machine* | Physical ×4.0 | 12 hits on one enemy | EARTH | Stun (base 40) |
| PC-06 | *Warszawa* | Heal | Party heal, ×0.5 spread, and Cantabile | — | Every enemy's gauge −50%; Rubato charges set to 3 |
| PC-07 | *La Clochette* | Magical | 8 hits on random enemies, no spread penalty | BOLT | — |
| PC-08 | *Grand Tirage* | Magical | Annotates every enemy, then EARTH → WATER → LIGHT on all, ×0.5 spread | EARTH, WATER, LIGHT | Party cleanse and Inspired |
| PC-09 | *Arirang Variations* | Heal | Party heal, ×0.5 spread, and Allegro | — | Encore on Min-jun (on herself if he is absent) |
| PC-10 | *Encore Stage* | Physical ×4.0 | 8 hits on one enemy, input-free; steals as a perfect BEAT | — | Crescendo +40 (+50 with Groove) |
| PC-11 | *Changes* | Heal or magical | Auto-stops the reels: *Turnaround* (heal, ×0.5 spread) if any ally is below 50% HP, else *Tritone Storm* (CHRONO to all, ×0.5 spread) | As result | The other result at 50% |

---

## 8. Elements and Light States

### 8.1 The nine elements (CANON §10c)

| Element | Flavour | Opposite | Main party sources |
|---|---|---|---|
| FIRE | Vermilion | ICE | Canvas (join), IMPRESSION under Noon or Candle, SYN-08, SYN-15, Tuttis |
| ICE | Cerulean | FIRE | Canvas (CH-08), *Chios*, SYN-21 |
| WIND | Zephyr | EARTH | Canvas (join), Winds Cue, SYN-08, Mendelssohn, Thalberg |
| EARTH | Ochre | WIND | Canvas (CH-05), Percussion Cue, Fugue, *La Machine* |
| BOLT | Sforzando | WATER | Canvas (CH-08), SYN-02, *La Clochette*, "Florestan" |
| WATER | Ondine | BOLT | Canvas (CH-05), REP-08 "Ondine", Fugue, IMPRESSION under Dusk or Fog |
| LIGHT | Lumen | SHADE | Canvas (rank 10), REP-01, SYN-01, *Lever du jour* |
| SHADE | Umbra | LIGHT | Canvas (CH-10), SYN-05, IMPRESSION under Night or Gloom |
| CHRONO | Tempus | — | *Tritone Storm*, SYN-16, REP-23 and REP-25 bursts, Min-jun's late skills |

### 8.2 Affinity resolution

- Each unit holds one affinity per element: **weak ×2, normal ×1, resist ×0.5, null ×0, absorb ×−1** (heals by the computed amount).
- Multiplication order: affinity × Light × the other CANON §10b MODs (crit, Fortissimo, Varnish or Glaze, Defend, back row). Light boosts also enlarge absorb-healing.
- **Dual-element actions** compute (affinity × Light) for each element and keep the better for the attacker, which reproduces CANON §10c: resisted only if both are resisted, absorbed only if both are absorbed; normal + absorb counts as normal, null + absorb as null.
- Non-elemental: Fight with an unelemented weapon, *Cacophony*, *Blue Note*, SYN-18, items.
- **CHRONO** has no opposite. Party members resist it (×0.5) only through the *Nohant Metronome* or the *Tuning Hammer*; two such relics do not stack. Every **party** CHRONO action is Anachronic at Heat 5; enemy actions never add Heat.

### 8.3 Light States

Every battle has one Light (CANON §10c: Dawn, Noon, Dusk, Night, Candle, Fog, Gloom), ambient from the map and time of day (CANON §11i) until something paints over it. It is computed from CH-01; its icon appears in CH-05 (§4.0).

| Rule | Detail |
|---|---|
| Painted Light | Shift the Hour, IMPASTO, some Études and Canvas recipes, SYN-10, 12 and 23, *Lever du jour*, LUMIÈRE, Libretto `LIGHT`. Lasts **until replaced**; no timer |
| Scope | The ±25% applies to elemental damage by **both sides**, never to healing |
| Two Lights (LUMIÈRE) | Each element's two modifiers add, so a boost and a weaken cancel; both passives apply; any single Light replaces both. Dawn + Noon: LIGHT and EARTH +25%, FIRE and ICE 0, SHADE and WIND −25%, plus regeneration and ATK +10% |
| Passives | **Dawn:** party regenerates 1/32 max HP per turn. **Noon:** party weapon ATK +10%. **Dusk:** party EVA +10 points (cap 75%). **Fog:** physical hit ×0.9, both sides. **Gloom:** every hit and status roll ×0.9, both sides. **Night:** enemy hit and status rolls ×0.9; party crit +5 points; Echo-family damage ×1.1. Hit and status multipliers apply after the clamp, floor 5% (formulas_and_curves §4.8–4.9) |
| Rivals | Lucile's styles +25% under Dawn, Noon, Fog; Delacroix's Canvas +25% under Dusk, Night, Candle: the Impressionist and the Romantic fight over the hour |
| Icons (§14) | Dawn half-disc on a line · Noon rayed disc · Dusk half-disc over a chevron · Night crescent and star · Candle flame · Fog three waves · Gloom arch over a dot |

---

## 9. Statuses

Durations count the bearer's own turns (CANON §10d), ending at the end of the bearer's turn (§3.6). "Cleanse" = everything a Panacea removes: every negative status except Swoon (CANON §14), Coda (reset only by *Da Capo*, CANON §10d) and Unwritten (the bearer is off the field). "Dispel" = SYN-06 and skills tagged *Dispel* in `skills_and_progression.md`.

| Status | Exact effect | Duration | Re-application | Cure | Immunities and interactions |
|---|---|---|---|---|---|
| Swoon (KO) | HP 0, cannot act; all other statuses cleared | — | — | Sal Volatile (25%), Sel de Vie (100%), *Encore* | Encore triggers instead if held; persists after battle; bosses immune to instant-Swoon effects |
| Miasma | −1/16 max HP at turn start; can Swoon | Until cured | — | Four Thieves, *Clarity*, Panacea, cleanse | Persists after battle; ticks on enemies cap at 999 (formulas_and_curves §4.4); never called cholera (CANON §16e) |
| Smoke | Physical hit chance ×0.5 (min 5%) | 4 | Refresh | Eyewash, *Clarity*, Panacea | Stacks with Fog and Gloom |
| Hush | Blocked: Harmony (incl. Invocations, Remembrances, Transcend, Transcribe), Recitals except REP-20, Synergies, Plein Air incl. Shift the Hour, Canvas incl. Sketch | 4 | Refresh | Throat Lozenge, *Clarity*, Panacea, Chorus Cue, *Song without Words* | Breaks a Recital. Unaffected: Fight, Conduct, Orchestrate, Étude, Rubato, Counterpoint, BOW, BEAT, IMPROVISE, Voice, Cadenza, Items |
| Reverie | Cannot act; any HP damage wakes | 3–5 (rolled) | Re-roll | Damage, Smelling Salts, Panacea | Breaks a Recital |
| Delirium | Fights a random unit of either side each turn | 4 or until damaged | Refresh | Damage, Panacea | Cannot be Conducted; bosses immune by default |
| Stagefright | Skips the next 2 turns (1 after a broken Recital) | 2 | Does not extend | Courage Draught, Panacea, REP-12 | Breaks a Recital |
| Stun | Loses the next turn | 1 | — | Wears off | Bosses immune unless stated (CANON) |
| Lento | Gauge ×0.5 | 5 | Refresh | *Allegro* cancels; Panacea | Cancels or is cancelled by Allegro (§3.5) |
| Fermata | Gauge frozen; cannot act even when full | 3 (phantom turns) | Refresh | Wears off, *Repay*, Panacea | Breaks a Recital; bosses immune by default |
| Marble | Petrified; skipped by enemy targeting; counts as KO for a wipe; timers frozen | Until cured | — | Sculptor's Oil, Panacea | Persists after battle; bosses immune by default |
| Coda | Count over the head falls by 1 at each turn start; Swoon at 0 | 20 (5 when a boss says so) | Does **not** reset the count | *Da Capo* resets it to its start; ends with the battle | Panacea does not cure it; Encore revives after; bosses immune by default |
| Frenzy | Auto-Fight on a random enemy, ATK +50% | Battle | — | Panacea | Bosses immune by default |
| Out of Tune | ART −25%; INS costs ×1.5 | 5 | Refresh | Pitch Pipe, Panacea | Min-jun immune (Perfect Pitch) |
| Discord | Cannot join Synergies, perform Voice or Cadenza; gives no Crescendo. On enemies: blocks skills tagged `ENSEMBLE` (volleys, shield walls, Quartet riffs) | 5 | Refresh | Pitch Pipe, Panacea, REP-31, SYN-17 | Min-jun immune |
| Swing | Gauge ×0.5–×1.5, re-rolled every second | 4 | Refresh | Wears off, Panacea, REP-31, SYN-17 | Multiplies with Allegro or Lento |
| Unwritten (CHRONO) | Removed from the field; returns after 3 phantom turns with current HP, statuses frozen; a whole party Unwritten = wipe | 3 | — | Wears off | Min-jun immune until CH-17 (CANON); items cannot target; bosses immune by default |
| Composed (enemy) | DEF and RES −50% | 3 | — | — | Only from 10 Pointillé Dots |
| Allegro | Gauge ×1.5 | 6 | Refresh | — | Cancels or is cancelled by Lento |
| Varnish | Physical damage taken ×0.5 | Battle | — | Dispel | Coexists with Glaze and Defend |
| Glaze | Magical damage taken ×0.5 | Battle | — | Dispel | Coexists with Varnish and Defend |
| Cantabile | +1/16 max HP at turn start | 6 | Refresh | — | Stacks with Dawn regeneration |
| Mirror | Reflects single-target spells (§5.4) | 3 reflections | Refills to 3 | Dispel | Never reflects Synergies, items or physical skills |
| Encore | Auto-revive once at 25% HP, gauge 128 | Until triggered | — | — | Not triggered by Marble or Unwritten |
| Fortissimo | Next resolved action ×1.5 | 1 action | Does not stack | — | Liberté gives it to the party |
| Swell | +10% ATK and ART per stack, max 5; −1 stack every second turn | — | Stacks | — | "Crescendo" always means the gauge (CANON §10d) |
| Inspired | INS costs ×0.5 | 4 | Refresh | — | With Out of Tune: ×0.75 |
| Bulwark | Damage taken ×0.5; intercepts (§5.5) | 4 | Refresh | — | Alkan's *Recluse* keeps it refreshed |
| Tacet | DEF/RES +25% while holding a full gauge | Until the bearer acts | — | — | Ends on any action, including a Synergy |

**On enemies:** Hush blocks every `magical` skill and skills tagged `voice`; Out of Tune: MAR −25% and the ART used for its status rolls −25%; Marble: the enemy counts as defeated with full rewards and plays its EXIT (humans freeze and surrender → subdue; Echoes dissolve; automata collapse); Stun, Stagefright, Reverie and Fermata skip turns as for the party; Discord as in its row.

**Status-inflict defaults** (CANON §10b formula, inside the formulas_and_curves §4.9 bands; each skill states its own Base): Smoke, Lento, Out of Tune **65**; Hush, Delirium, Discord, Swing **55**; Reverie, Stagefright, Miasma **45**; Frenzy **50**; Stun, Fermata **35**; Marble, Coda **30**; enemy-cast Unwritten **40**.

**Default boss immunities** (the Libretto `IMMUNE` line may remove any of them explicitly): instant Swoon, Marble, Coda, Unwritten, Stun (CANON), Fermata, Frenzy, Delirium.

**After battle** only Swoon, Miasma and Marble persist; everything else clears.

---

## 10. Battle-Stage Modifiers: Onlookers and Field Effects

### 10.1 Onlookers (CANON §11e)

- Onlooker counts per secrecy_and_trust §2.4.1; each carries a 3-pip timer that loses a pip at the start of each turn of the slot-1 party member and leaves at 0. Onlookers have no gauge and never act.
- **Heat** is added once per Anachronic action resolved while one remains, at the action's highest Heat; a Recital's once, at Movement I. A Brass Cue clears all Onlookers, a Sketch one, and any enemy Swooned by a critical hit all (a scare).
- **CH-E1:** phone-camera silhouettes; only Lucile's painting adds Heat, and only to the Spotlight Meter: her Plein Air styles, *Lever du jour* and SYN-01 (counted at IMPRESSION's Heat 2), per secrecy_and_trust §2.10. **CH-E2:** no Onlookers.

### 10.2 Field effects

A field effect is set by the map; it stacks with, but never replaces, the Light State.

| Field effect | Where | Default Light | Rules | Counterplay |
|---|---|---|---|---|
| **Salon Audience** | P04 (tavern salon), P05, P15, P39 and any salon battle | Candle | Always 3 Onlookers. **Applause:** an enemy Swooned by a weakness hit while an Onlooker remains gives +5 extra Crescendo | Keep the crowd for Crescendo, or clear it for cover |
| **Rain** | Outdoor maps in rain (P02 in CH-01, the quays) | Fog | **Soaked:** units in the front row or front rank take BOLT damage ×1.25 | Move to the back row; paint over the Fog |
| **Sewer Water** | P17, flooded passages of P26 | Gloom | **Wading:** front-row party members EVA −10 points; WATER-absorbing enemies regenerate 1/32 max HP at turn start | Back row; Dusk; BOSS-10's sluices swap rows (CANON §13) |
| **Catacomb Darkness** | P01, P29 crypt zones, P38 | Gloom | **Unseen:** back-rank enemies cannot be chosen by single-target actions (spread and random hits still land) until revealed by a LIGHT hit, a Dawn or Noon Light, or Mathurin's LANTERN | Light them up; spread attacks |
| **Opera Stage** | P27 stage and rafters | Candle | **Footlights:** crit chance +5 points for and against front-row units. **Fly system:** counterweights are targetable props (HP set by `bosses.md`); a destroyed counterweight falls on the linked front (§11.2) | Back row for safety, front row for crits |
| **Snowfall** | CH-E1 battles under falling snow (W03 static pockets; S09) | Fog | ICE damage ×1.25 (Fog already supplies the physical-hit penalty) | ICE-weak foes melt; spells over physical hits |
| **Amalgam Flicker** | P29 amalgam zones | Gloom ↔ Noon | After every 3 party actions the ambient Light flips between the zone's 1833 Gloom and its 2026 fluorescent Noon; a Painted Light holds until the next flip | Time elemental bursts to the flip; REP-25 rides it |

---

## 11. Special Battle Types

### 11.1 Registry

| Type | Canon uses | Rules | Fail state |
|---|---|---|---|
| Multi-wave | BOSS-05; CH-10 Nohant house defence | §11.7 | Fine |
| Three-front | CH-13: BOSS-17, 18, 19 | §11.2 | Fine on any front's wipe; never from Rapture |
| Duel | BOSS-03, 08, 20, 32, 35; BOSS-17's stage | §11.3 | Never ends the game (CANON §11g) |
| Escort / Ward | GST-11 Théo (CH-12); Vane in BOSS-21; Lucile's canvas in BOSS-33 | §11.4 | Théo or Vane at 0: Fine. Canvas at 0: no Fine, poorer ending text (CANON §13) |
| Defend-the-Instrument | Template | §11.5 | Per use |
| Timed | BOSS-05 powder keg, BOSS-19, BOSS-27, BOSS-30 | §11.6 | Per battle |
| Split party and chains | CH-09 threads, CH-15 parties, the CH-16 sequence | §11.8 | Fine |
| Survival | BOSS-16 | §11.9 | Cannot be lost |
| Octave | BOSS-27 | §6.7 | Per `bosses.md` |
| Chained bars | BOSS-31, 34, 43 | Each bar (≤ 65,535 HP, CANON §10a) is a Libretto phase; overflow damage is lost at a bar break; Crescendo carries | Fine |

### 11.2 The Grand Concert (CH-13, LOC-P27)

**Fronts.** **Stage** (BOSS-17): Min-jun and Liszt, Berlioz conducting and untargetable, scored by **Rapture** 0–100. **Rafters** (BOSS-18): Delacroix, Lucile, Alkan. **Corridors** (BOSS-19): Chopin, Farrenc, Offenbach (guest). CANON §4a, §13.

1. **Rotation.** Stage → Rafters → Corridors, switching after **3 front turns** (CANON §13): a duet Passage on the Stage (`salons_duels_and_economy.md`), a party action elsewhere. A resolved front drops out.
2. **Frozen fronts.** Only the active front's clock runs; gauges, statuses and timers (BOSS-19's 12 turns) wait. A switch is a 1.5 s rope-and-curtain wipe.
3. **Shared state.** One Crescendo Gauge for the building, starting at 50. Corridors carry 1 stagehand Onlooker (secrecy_and_trust §2.4.1); Rafters none (Taglioni's *Sylphide* covers them); the Stage's values are scripted (REP-27 Heat 0).
4. **Cross-front hooks.** (a) A counterweight destroyed in the Rafters damages the corridor enemies at once, frozen or not (CANON §13). (b) **The eight-bar rescue** (CANON §4b) always plays: when `cornered` (item 8) fires, a one-option prompt ("Eight bars!") gives Min-jun one P1 action on the Rafters (any command but RECITAL); Rapture −15 while Liszt covers. (c) BOSS-19's timer expiring brings Roussel to the stage door: **Rapture −20**, and he withdraws wounded. (d) Own Voice ≥ 6 adds a cadenza phase to the Stage.
5. **Resolution.** Stage: three movements played. Rafters: Brücke escapes at 50%. Corridors: Roussel subdued or withdrawn. The battle ends when all three are resolved.
6. **Presentation.** A three-panel strip across the top (party HP, enemy state, the active front lit, three rotation pips). The Stage borrows voices V5–V6 (CANON §15a).
7. **Rapture below 40.** At the end of a Stage rotation with Rapture < 40, Liszt covers the next Stage rotation alone (AI Passages ×0.75) and Brücke gains one free *Escapement* at the next switch to the Rafters. Finishing the concert below 40 halves the Renown gain and adds a hostile gala review in CH-14 (value per secrecy_and_trust). The Own Voice phase and secret Score are unaffected (CANON §11g). Rapture never causes Fine.
8. **`cornered`** = Lucile at ≤ 30% max HP, or the target of a Rafters `CHARGE`, during a Rafters rotation; fires once per battle. `bosses.md` scripts at least one Rafters `CHARGE` at `party.member(PC-02)`, so the canon beat always plays.

### 11.3 Duels

Duels use the duel screen: no gauges, Harmony or items; Composure and Favor replace HP (CANON §11g) and Passage rules belong to the salons doc. Hooks fixed here: the party's Crescendo enters at 50 so Vane's *Wager* can stake it (BOSS-20); Min-jun's **Conduct** in BOSS-32 makes Lucile's next Passage ×1.25; Rehearsal Mode covers every Passage; a lost duel never shows the Fine screen.

### 11.4 Escorts and wards

An escort or ward takes no slot, has no gauge and never acts; it stands at the ward position (§2.1) with its own HP bar above the party window. The party may heal it and give it Varnish or Glaze; Bulwark intercepts for it below 25% (§5.5). Only the Libretto targets `escort` and `ward` reach it; party spread actions never do. The BOSS-33 canvas starts at 9,999 minus the damage taken in the *La Lumière* flight (CANON §4f).

### 11.5 Defend-the-Instrument (template)

A ward variant: a piano with a **Tuning** bar. Below 50% Tuning, every Recital modifier and burst is ×0.75 (Perfect Pitch cannot help: the piano is out of tune, not Min-jun); at 0, RECITAL is unavailable ("the strings are gone"). In these battles only, Min-jun's side menu gains ***Set the Pins*** (his turn; +25% Tuning): he resets the drifting unisons with a tuning hammer borrowed from the piano's own case, his father's trade (CANON §5f). Saboteurs target `ward`. Placements are proposals only (final section).

### 11.6 Timed battles

| Timer kind | Counts | Canon examples |
|---|---|---|
| Turn timer | One unit's turns, or a front's turns | BOSS-19 (12 corridor turns); BOSS-05 powder keg (5 turns); BOSS-30 clock-dial (12 turns, resets) |
| Clock timer | Battle-clock seconds × SpeedSet, so slow settings never shorten real time | Libretto `TIMER … seconds` |
| Stasis clock | Counts down; Voice adds seconds back | BOSS-27 (§6.7) |

Timers show top-centre (§2.2). Each battle declares its expiry outcome: fail-forward (BOSS-19) or Fine.

### 11.7 Multi-wave battles

Between waves there is no reward screen. HP, INS, statuses, Swoons, Crescendo, the Recital, Tutti tokens and Rubato charges all carry; party gauges keep their values; the new wave enters at random 0–(2 × TMP) after a "Wave 2/4" banner, and Onlookers stay. Rewards are totalled at the end.

### 11.8 Split parties

CH-09's threads and CH-15's parties fight separately. Swap draws only on the thread's own reserve; members in other threads take **reserve EXP** (50%, or 100% while Farrenc fights).

- **CH-15:** parties switch only at Lecterns and plinths, never mid-battle; the Crescendo resets after each battle as usual, so no party inherits another's gauge.
- **CH-16:** BOSS-26 → 27 → 28 is one sequence; HP, INS, statuses and Crescendo carry, with the Crescendo floored at 50 at each boss start.
- **Mid-battle joins** (BOSS-02 Berlioz on turn 5; BOSS-12 phase 2 Min-jun): Libretto `JOIN` enters at gauge 128 in the first free slot and counts as active for EXP.
- **Solo battles** (Min-jun CH-09; Lucile CH-11 and CH-12): Synergy and Swap hidden; POINTILLÉ's ally mode hits only her.
- **CH-09 cell:** Min-jun's right hand is injured, an uncurable Hush for the battle, except REP-20 (CANON §15d); the cell escape is the Cadenza tutorial (CANON §11d).

### 11.9 Survival battles

BOSS-16 shows "?????" HP and nulls all damage (CANON §13). It ends on its scripted condition (6 turns, or party HP below 25%); anyone Swooned returns at 1 HP; the Fine screen cannot appear.

---

## 12. Escape, Victory, Defeat

### 12.1 Flee (CANON §11a)

Hold **L + R** (or toggle, §14). Per formulas_and_curves §5.6: one check per 60 frames of running battle clock while held (releasing resets the timer), at **10% + (party mean TMP − enemy mean TMP)%, clamped 5–90%**, over living active members (guests included) and living enemies, using the TMP stat only (ATB statuses do not count). While fleeing, command windows stay closed and enemies keep acting. **This doc adds:** Back Attack and Pincer halve the chance; a Side Attack's first check succeeds. Boss and scripted battles show "Can't escape!" (CANON §11a). A flee gives no rewards; Heat already added stays.

### 12.2 Victory

Victory comes when every enemy is defeated (routed, subdued, dissolved, collapsed) or gone, or by script. After the last exit and the party's pose, the reward window lists:

1. **EXP** (CANON §10a; formulas_and_curves §5.1): X(E) summed, in full to each living active member; reserve 50% (100% while Farrenc is active); guests and members Swooned, Marbled or Unwritten at battle end 0. Duels, the Rapture battle and survival battles give 0; boss parts and adds give X(boss Lv) × 2.5 each.
2. **Money:** G(E) summed, bosses ×10; won at ×200 in CH-E1.
3. **OP** per equipped Opus Score (formulas_and_curves §5.3): 1–3 per standard enemy, 10–30 per boss.
4. **Items** (formulas_and_curves §5.4): per defeated enemy, the rare slot first at clamp(4 + (LCK_best − LCK_t)/4, 2, 16)%, LCK_best being the highest living active LCK; if it fails, the common slot at 35%. Bosses give their guaranteed reward.
5. **Studies** and Almanach entries.
6. **Bond +1** per active member (CANON §11f; max +30 a chapter; none while Lucile's BP is frozen).
7. **Level-ups**, stat gains and Harmony skills learned.

A advances; holding B fast-forwards.

### 12.3 Defeat and continue

**A wipe** = every active member Swooned, Marbled or Unwritten (reserves never step in on their own), or a battle's own fail condition. The **"Fine"** screen (CANON §11a) offers:

| Option | Effect |
|---|---|
| **Retry battle** | Same formation; full HP and INS; statuses cleared; inventory and Crescendo restored to the battle's starting snapshot |
| **Return to last save** | Loads the most recent save slot, or the Eve of the Window slot if that is the latest |

No money is lost (CANON §11a). There is **no other game over**: the Unmasking, duels, Rapture, BOSS-19's timer and the BOSS-33 canvas are all fail-forward. From the title screen, *Continue* loads the most recent save.

---

## 13. Enemy AI Script Language: the Libretto

Every regular enemy, boss part and AI guest has one **Libretto**: a short, line-based script that `bestiary.md` and `bosses.md` write in. It is FF6-style (conditions checked top-down, one action per turn) and compiles to a byte-code table per formation.

### 13.1 Header

| Keyword | Meaning |
|---|---|
| `LIBRETTO <id> "<name>"` | Opens a block; `<id>` is an ENM, BOSS (parts suffixed L, R, P…) or GST id (`SAMPLE-` ids exist only in this document's examples); the name ≤ 14 characters |
| `LEVEL n` · `RANK front\|back` | Level; formation rank (§5.1) |
| `TAGS …` | Family and flags: `echo`, `human`, `automaton`, `animal`, `construct`, `grey_hand`, `tableau`; props (counterweights, easels, walls) carry `prop`, and BOSS-01's wall also `bonewall` (§4.6) |
| `EXIT rout\|subdue\|dissolve\|collapse` | Defeat animation; **humans must use rout or subdue** (Tone Rule 8) |
| `IMMUNE default_boss, -Stun, Hush` | Immunities; `default_boss` expands to the §9 list; `-X` removes X |
| `AFFINITY FIRE:weak SHADE:absorb …` | Per element; `AFFINITY locked` refuses SYN-23's override |
| `STUDY <STU-id> ON "<skill>"` | Sketch records the Study after this skill is seen (§4.6) |
| `STEAL common <ITM-id> / rare <ITM-id>` | Pilfer table |
| `UNIQUE "<skill>", …` | Cannot be Transcribed or copied by SYN-11 |
| `MULTI n` | Actions per turn (default 1) |
| `SPARE PC-01` | Damage that would Swoon Min-jun leaves him at 1 HP; his random weight ×0.5. Archon's doctrine (CANON §4c): the Grey Hand and Roussel in CH-09, CH-13 and CH-14; Archon in BOSS-26 |
| `HUNT PC-01` | Min-jun's random weight ×2.0. Brücke's private orders (CANON §4c rungs 8, 10, 16): his automata in CH-10 and CH-E1 |
| `VAR $name = n` | Integer variables, reset each battle |

### 13.2 Event blocks

| Block | Runs |
|---|---|
| `ON START` | Once, at P0, before any gauge fills |
| `ON TURN` | Each time this unit's gauge fills |
| `ON HIT <filter>` | After an action damages or affects this unit; one counter per triggering action, never chained |
| `ON TARGETED <filter>` | After an action aimed at this unit resolves, hit or miss |
| `PHASE n WHEN <cond>` · `ON PHASE n` | Declares a threshold (checked after every resolved action; phases only advance) and its entry actions at P0; the unit's queued action is discarded |
| `ON ALLY DOWN ["<name>"]` | When another enemy is defeated |
| `ON TIMER <name>` | When a named timer expires |
| `ON LIGHT <state>` | When the Light becomes `<state>` |
| `ON CHARGE BREAK "<skill>"` | When a telegraphed skill is interrupted |
| `ON DOWN` | When this unit reaches 0 HP, before its exit (a last action, a line) |

Filters: `physical`, `magical`, `item`, `synergy`, `any`, `element(FIRE)`, `command(RECITAL)`, `by(PC-07)`, `damage >= 10%`.

### 13.3 Statements

- `IF <cond> : <action> [THEN <free action>]`. In `ON TURN` the first true line acts and ends the turn; `THEN` chains a free action (`SET`, `ADD`, `SAY`) onto it.
- `ALSO <free action>` runs whenever it is reached, without ending the turn.
- `ROTATE … END` cycles its lines on successive turns; `CHOOSE … END` picks one by weight (`3: USE "X" -> …`).
- With `MULTI n`, `ON TURN` is evaluated *n* times per turn; `ROTATE` advances per evaluation.
- `DEFAULT : <action>` closes every `ON TURN`; a unit with no `ON TURN` passes. In every other block, lines run in order.

### 13.4 Targets

`self` · `party.random` · `party.all` · `party.front` · `party.back` · `party.lowest(hp%)` · `party.highest(hp)` · `party.has(<status>)` · `party.not(<status>)` · `party.slot(n)` · `party.member(PC-##)` · `party.performer` (the member in a Recital) · `attacker` · `last.target` · `charge.target` · `ally.random` · `ally.all` · `ally.lowest(hp%)` · `ally.name("<name>")` · `escort` · `ward`.
**Random weights:** 1.0 per eligible party member, Chopin ×0.5 (*Sotto Voce*), Min-jun ×0.5 under `SPARE` or ×2.0 under `HUNT`; Swooned, Marbled, Unwritten and sealed members are excluded; Bulwark interception applies after selection.

### 13.5 Conditions

`self.hp% <= n` · `turn == n` · `turn % n == 0` · `chance n%` · `once` · `phase == n` · `light == Night` · `onlookers > 0` · `crescendo >= n` · `party.count(alive) <= n` · `party.count(not <status>) >= n` · `party.has(PC-##)` (that member is active and on the field) · `party.any(recital)` · `cornered` (§11.2) · `recital.movement >= n` · `ally.alive("<name>")` · `timer(<name>) <= n` · `$var >= n` · `flag.<name> >= n` (story values such as `flag.recording`, KEY-23's 0–80) · `hit.damage >= 5% self.maxhp` · `hit.element == FIRE`. Combine with `AND`, `OR`, `NOT` and parentheses.

### 13.6 Actions

| Action | Effect |
|---|---|
| `USE "<skill>" -> <target>` · `FIGHT -> <target>` | Use a skill; basic attack (tagged `melee`) |
| `CHARGE "<skill>" -> <target> FOR n TURN BREAK <cond>` | Telegraph: banner and a target marker now, resolution at the unit's n-th next turn unless `<cond>` occurs first |
| `SUMMON <id> AT front\|back MAX n` · `FLEE` · `TRANSFORM <id>` | Formation changes |
| `LIGHT <state>` · `ROWSWAP party` · `PULL party.back -> front` · `ATB <target> ±n%` | Field and tempo |
| `STATUS <target> +<status> [n]` · `CLEAR <target> -<status>\|positive` · `SWAPSTATUS <target> Allegro Lento` | Scripted statuses (no roll) |
| `TIMER START <name> n turns(self)\|turns(front)\|seconds` · `PHASE n` · `END BATTLE victory\|fail\|scripted` | Flow |
| `TARGETABLE yes\|no` · `HIDE` · `REVEAL` | Visibility |
| `DAMAGE <target> <n>% maxhp` | Fixed damage (BOSS-12, 19, 21 *Steady…*): ignores DEF/RES, guards and VAR; no crit; `SPARE` still applies |
| `HEAL <target> <n>%` · `REVIVE <ally target> <n>%` | Restore n% of max HP (BOSS-09's chime); revive a defeated enemy at n% (BOSS-40) |
| `STEAL gold <n>%` | Takes n% of the party's francs (BOSS-02); recovered in full if the unit is defeated, lost if it flees |
| `JOIN PC-## [gauge n]` | A party member enters mid-battle (BOSS-02 Berlioz, BOSS-12 Min-jun), default gauge 128 (§11.8) |
| `SEAL <target> n turns [BREAK <filter>]` | Off the field and untargetable, timers frozen (BOSS-22 burial, BOSS-23 doors); the slot shows a marker allies may target, and a hit matching `<filter>` on it frees the member early |
| `NOHEAL <target> n` | The target cannot regain HP for n turns, items and ticks included (BOSS-15 *Vanishing Point*); revival still works |
| `GUARD self null\|reverse [from back]` | Null all damage (BOSS-16), or turn damage into healing; `from back` limits it to hits by back-row attackers (BOSS-24) |
| `STAT <target> <stat> ±n%` · `AFFINITY SET <ELEM>:<aff>` · `AFFINITY FROM light` | Rewrite a stat (BOSS-25); change one affinity; weak to the current Light's weakened elements and resisting its boosted ones (BOSS-25) |
| `VULNERABLE self ×n FOR n TURN` | Damage taken ×n (BOSS-38's overheat window) |
| `GRANT PC-##\|party "<command>" UNTIL <cond>` | Adds a context command to the side menu (BOSS-11 *Recognition*, BOSS-07's formula, BOSS-10's levers) |
| `SAY "<text>"` · `PASS` | One banner line ≤ 30 characters, no portrait; longer lines chain as consecutive `SAY`s; do nothing. Dialogue scenes inside a battle use the CANON §16a box and tags, not `SAY` |

**Skill lines** (in the bestiary and boss skill tables): `SKILL "<name>" physical|magical <ELEMENT|none> ×<power>` or `SKILL "<name>" fixed <n>% maxhp`, then `one|all|rank [status <name> <base>] [tags melee, voice, ENSEMBLE, UNIQUE]`. Power multiplies the unit's AR (physical) or MAR (magical) inside the CANON §10b enemy formula; `fixed` resolves as `DAMAGE`; all-target skills take ×0.5 automatically; `ENSEMBLE` skills are blocked by Discord, `magical` and `voice` skills by Hush (§9).

### 13.7 Examples

**A. A regular Echo** (syntax sample; the bestiary owns the real entry, id and numbers).
```
LIBRETTO SAMPLE-A "Lime Wraith"
LEVEL 3  RANK back  TAGS echo  EXIT dissolve
AFFINITY LIGHT:weak SHADE:absorb FIRE:weak
SKILL "Lime Breath" magical none ×0.8 all status Miasma 45
ON TURN
  IF light == Dawn : USE "Lime Breath" -> party.all
  IF chance 30% AND party.count(not Miasma) >= 1 : USE "Lime Breath" -> party.all
  DEFAULT : FIGHT -> party.random
ON HIT element(LIGHT)
  SAY "The lime remembers light."
```

**B. A telegraph** (the BOSS-12 *Steady…* mechanic of CANON §13; here every attempt spends a cartridge; `bosses.md` writes the full script).
```
LIBRETTO BOSS-12 "Roussel"
LEVEL 22  RANK front  TAGS human, grey_hand  EXIT subdue
IMMUNE default_boss
SPARE PC-01   ; "the boy breathing" (CANON §4c rung 14)
VAR $shots = 0
SKILL "Steady…" fixed 60% maxhp one tags UNIQUE
ON TURN
  IF $shots < 3 AND turn % 3 == 0 : CHARGE "Steady…" -> party.highest(hp) FOR 1 TURN BREAK hit.damage >= 5% self.maxhp THEN ADD $shots 1
  DEFAULT : FIGHT -> party.random
ON CHARGE BREAK "Steady…"
  SAY "The Garde never misses twice."
```

**C. Functions living in parts** (BOSS-28's CANON §13 functions: destroying a part silences its block).
```
LIBRETTO BOSS-28R "Right Manual"
ON TURN
  IF turn % 3 == 0 : ROWSWAP party
  DEFAULT : PASS
LIBRETTO BOSS-28L "Left Manual"
ON HIT magical
  SWAPSTATUS party.all Allegro Lento
LIBRETTO BOSS-28P "Pedalboard"
ON TURN
  IF party.count(alive) >= 2 : PULL party.back -> front
  DEFAULT : PASS
```
The core's *Recorded Echo* reads `flag.recording` and adds +5% damage per 20 points (CANON §13).

**D. An AI guest** (GST-04, sides mirrored: `party` means her allies).
```
LIBRETTO GST-04 "Clara"
ON TURN
  IF party.any(recital) : USE "PRODIGY" -> party.performer
  DEFAULT : USE "Caprice" -> party.not(Allegro)
```

### 13.8 Lint rules (checked by the build)

1. Every `ON TURN` ends with `DEFAULT`; no turn produces more actions than `MULTI`.
2. `EXIT` by family: `human` → rout or subdue; `echo` → dissolve; `automaton` → collapse; `animal` → rout; `tableau` → dissolve; `construct` → collapse; `grey_hand` → subdue or rout. `SPARE` and `HUNT` never appear in one Libretto.
3. Every `CHARGE` has a `BREAK` clause.
4. `SAY` lines fit the banner and never put invented words in a historical figure's mouth as a real quotation (CANON §16b).
5. Nothing targets Onlookers, and no Libretto exists for the National Guard, the Prefecture, octroi agents, soldiers or Seoul civilians (CANON §12).

---

## 14. Accessibility and Difficulty

**There is one difficulty** (CANON §11j). The numbers never change; the game instead offers mercies (Retry battle with a full restore, no money lost, the Eve of the Window save) and the options below. At Wait mode and speed 6, a CH-09 party member gets a turn every 4.9 s and the clock stops in every sub-menu.

| Option | Values (default) | Effect |
|---|---|---|
| Battle Mode | Active / **Wait** | §3.2 (CANON) |
| Pause on Command | **Off** / On | Wait only: the clock also stops on the top-level command list |
| ATB Speed | 1–6 (**4**) | CANON §10b |
| Battle Message Speed | 1–5 (**3**) | Banner and `SAY` duration |
| Text Speed | 1–5 (**3**) | Dialogue (CANON §11j) |
| Rehearsal Mode | **Off** / On | Every timing input perfect at ×0.8: Études, *Phrase*, Duel Passages, BEAT, SYN-18, busking (CANON §11j); IMPROVISE reels slow to 4 symbols/s |
| Flee Input | **Hold** / Toggle | Toggle: tap L + R to start fleeing, again to stop |
| Cursor Memory | Off / **On** | §5.3 |
| Flash Reduction | **Off** / On | Full-screen flashes capped at 3 per second at half brightness (SYN-02, SYN-16, *Tritone Storm*, BOSS-28) |
| Screen Shake | **On** / Off | — |
| Audio Cue Visuals | **Off** / On | The ATB ding, telegraph sounds and Recital chimes also flash an icon |
| Shape coding | Always on | Light State icons (§8.3) and status icons differ by silhouette, not only colour (CANON §11j) |
| Button remapping | Full | Every battle input, including Étude and BEAT inputs |

---

## Canon Additions & Cross-Doc Notes

**New shared facts (others reference, never redefine):**
- **Unlock schedule** (§4.0, from CANON §4a): Light computed from CH-01, icon from CH-05; no Crescendo before CH-04, boss start 50 from BOSS-05; Alkan as a CH-03 guest has Fight, Defend, Item. *Affects:* bosses, bestiary, skills_and_progression, prologue_and_act1, art_and_ui.
- **Round** = one ATB cycle in which every living member acts once; *n* rounds = *n* of the bearer's own turns. *Affects:* skills_and_progression, formulas_and_curves, bosses.
- **Command tier** (§1): formulas §8.4 gates, capped by canon chapter; T5 only with a learned T5 HRM. **Command numbers** on the formulas §8.4 budgets (§4.6, §7); *Nuit étoilée* shares IMPASTO's term; Synergies use mean ART and level (the Octave Min-jun's); SYN-02 and SYN-09 are fixed-target multi-hits. *Affects:* skills_and_progression, formulas_and_curves, bosses.
- **Command and ATB rules:** *Da Capo* resets Coda; Conduct's limits; Row costs half a turn; Swap may replace a Swooned or Marbled ally; Encore and Swap enter at gauge 128; three Repay charges = gauge 256 at the head of the queue; INS and items paid at resolution; Recital Crescendo for II and III only; Recital ending and breaking (incl. Swoon, Marble, Stun); REP-00's two movements and the `bonewall` prop; the Hush lists. *Affects:* skills_and_progression, formulas_and_curves, bosses, art_and_ui.
- **Synergy effects and animations** (§6.5): SYN-04, 07, 22 consume their record; SYN-12 Reverie base 50; SYN-13 never shows the portrait (LAW-26, MUS-150); the Octave outside BOSS-27; Voice blocked by Discord. **Cadenza effects** (§7), reused by Remembrances on their own line below the Invocation. *Affects:* skills_and_progression, bosses, epilogues, audio_and_music, art_and_ui.
- **Formations, field and statuses:** Pincer and Side Attack (2% each, *open* maps) and the map flag ***open***; enemy ranks; **Unseen**; seven field effects (Snowfall on Fog); inflict defaults inside the formulas §4.9 bands; the default boss immunity list; enemy-side Hush (`magical`, `voice`), Out of Tune, Marble and Discord. *Affects:* dungeons, overworld_and_towns, bestiary, bosses, items_and_equipment.
- **Battle formats:** Rapture below 40 and `cornered` (§11.2; `bosses.md` must script a Rafters `CHARGE` at Lucile); split-party, CH-16 carry, `JOIN` and solo-battle rules (§11.8). *Affects:* bosses, act2, act3, act4_and_epilogue, salons_duels_and_economy.
- **The Libretto** (§13), mandatory for `bestiary.md` and `bosses.md`, including `fixed` skills, the A-1 flags `SPARE PC-01` and `HUNT PC-01`, and the §13.6 actions. *Affects:* bestiary, bosses.
- **Options** added to CANON §11j's list (§14). **Defend-the-Instrument** with ***Set the Pins*** (§11.5); proposed placements, not canon: a CH-08 backstage skirmish at Salle Pleyel (LOC-P12) and the CH-E1 concert-hall approach (LOC-S10). *Affects:* art_and_ui, act2, epilogues, dungeons.

**Cross-doc notes (no CCR needed):**
- **formulas_and_curves:** (1) state in §4.5 that the Octave uses Min-jun's ART and level, an exception to rule 3 that the CANON §10e check needs; (2) add to §5.6 this doc's Back Attack and Pincer flee ×0.5 and the Side Attack's guaranteed first check; (3) note in §4.10 that Pincer and Side Attack are rolled after its two formations fail.
- **secrecy_and_trust:** (1) its rule "Lucile's part counts as IMPRESSION" makes SYN-10, 12 and 23 Heat 2, but its §2.4.1 table says 0; this doc follows whichever it keeps; (2) *Changes* or an IMPROVISE that resolves as *Tritone Storm* is CHRONO, so Heat 5 under CANON §10c, not 3; (3) it owns the value of the hostile gala review (§11.2 item 7).
- **overworld_and_towns:** Snowfall follows its precipitation rule and W03 static pockets. **dialogue_style_guide:** barks use the 212 × 14 banner and never stop the clock (§3.2).

**Readings of ambiguous canon text (for the Lead Designer to confirm):** Lucile's "+25% preemptive chance" = +25 percentage points (formulas_and_curves §4.10); Night's "Echoes +10% damage" = damage dealt by Echo-family enemies; "+3 per Recital movement advanced" = Movements II and III only; Fermata and Unwritten durations run on phantom turns; Panacea also leaves Coda and Unwritten (§9); IMPROVISE is a slot, not a timing input, so Rehearsal Mode slows its reels to 4 symbols/s instead of forcing a result (CANON §11j).

**CCR (proposed; not used in this document):**
- **CCR: battle Recital effects for REP-27, REP-29, REP-30** (CANON §15d; no CHRONO, so Heat stays 0; bursts at the Recital III budget). REP-30 *Jeong-dong Nocturne*: Cantabile → party RES +15% → party heal 1.5 Hₜ ×0.5 spread. REP-29 *La Musique des étoiles*: LIGHT +25% → party regains 2% of max INS per turn → LIGHT burst 1.5 Pₜ to all ×0.5 spread. REP-27 *Concerto "Lost Era"*: party Swell +1 per movement → Crescendo +20 → LIGHT + WATER burst 1.5 Pₜ on one enemy. *Why:* CANON §5c lists them for battle from CH-13 with no effects anywhere; vision_and_pillars makes this where his arc and the risk economy meet. *Affects:* canon §15d, skills_and_progression, audio_and_music.
- **CCR: SYN-24 *Fantastique for Piano*** (BE + LI, Duo, Ensemble Scene CH-07+): Liszt replays Berlioz's last Tutti as a piano transcription, one target at ×1.4, adding BOLT and consuming the record as SYN-04 does; grounded in Liszt's real 1833 transcription (CANON §3a); fills the BE–LI gap. *Affects:* canon §11b, skills_and_progression, side_and_bond_quests.
- **CCR: SYN-25 *Concerto for Three Keyboards*** (CH + AL + FA, Trio, all at rank 8, after Hiller's concert of Sun 15 Dec 1833): WATER, EARTH and LIGHT waves on all enemies, PWR 220 ×0.5 spread, and party Allegro; echoes CH-14's Bach concerto (CANON §15e) and gives Chopin, Alkan and Farrenc a Trio. *Affects:* canon §11b, skills_and_progression, act4_and_epilogue.
