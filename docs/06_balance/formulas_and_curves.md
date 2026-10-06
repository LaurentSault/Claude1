# Balance — Formulas & Curves

Status: v1.0 — 2026-10-06 · Owns: every formula, the EXP table, stat growth curves, enemy scaling rules, drop/gold/escape/encounter formulas, time-to-kill simulations · Depends on: CANON; reads combat_ensemble.md (battle rules, formations, Light passives, split-party and status details) and overworld_and_towns.md (encounter zones) · Canon: docs/00_CANON.md

## Contents

1. [Reading this document](#1-reading-this-document)
2. [CANON §10 reproduced (verbatim)](#2-canon-10-reproduced-verbatim)
3. [Conventions: notation, rounding, order of operations, stacking](#3-conventions-notation-rounding-order-of-operations-stacking)
4. [Combat formulas, with worked examples](#4-combat-formulas-with-worked-examples)
5. [Reward and field formulas, with worked examples](#5-reward-and-field-formulas-with-worked-examples)
6. [EXP table and level pacing](#6-exp-table-and-level-pacing)
7. [Stat growth per playable character](#7-stat-growth-per-playable-character)
8. [Opus Scores: level-up bonuses and skill learning](#8-opus-scores-level-up-bonuses-and-skill-learning)
9. [Gear curves (derived targets)](#9-gear-curves-derived-targets)
10. [Enemy design rules](#10-enemy-design-rules)
11. [Time-to-kill simulations](#11-time-to-kill-simulations)
12. [Encounter rates, difficulty knobs, RNG and caps](#12-encounter-rates-difficulty-knobs-rng-and-caps)
13. [Canon Additions & Cross-Doc Notes](#canon-additions--cross-doc-notes)

---

## 1. Reading this document

- **Section 2 is canon.** It is a verbatim copy of CANON §10 (v1.0). Nothing in it may be edited here; changes go through the Lead Designer as a CCR (logged in the last section).
- **Everything else is derived.** Every table below was computed by script from the CANON §10 formulas and the CANON §5b join stats, then checked against the CANON §10e anchor table. Where the canon leaves a mechanic open (multi-hit splitting, drop odds, per-step encounter rolls, the Opus bonus ledger), this doc defines it, and every such rule is logged as a shared fact in the last section. Where canon text needs a reading (a "−10%" on a hit chance, "+25% preemptive chance"), this doc uses the reading `combat_ensemble` already applies and lists it for the Lead Designer; where this doc would prefer to change a canon effect, it files a CCR and does not use it.
- **Battle rules come from `combat_ensemble`** (CANON §0b: formations, Light passives, statuses, split parties). Power budgets for commands live here (§8.4) and `combat_ensemble` quotes them.
- **Precedence** (CANON §0b): canon, then this doc for formulas and curves, then docs that cite it. `skills_and_progression`, `bestiary`, `bosses` and `items_and_equipment` reference these numbers and never redefine them.
- **Verification result.** All 18 rows of the CANON §10e anchor table reproduce from the formulas, every column, with one rounding exception: the CH-07 boss anchor is exactly 9,250 before rounding, which "round half up" makes 9,300 while the table prints 9,200 (a half-to-even artefact). It has no gameplay effect (BOSS-09's 8,000 HP sits within tolerance of either value) and is logged as a CCR.
- **Abbreviations** follow CANON §4: MJ, LU, BE, DE, AL, CH, LI, FA, SY, JW, JU; (g) = guest. "Std" = standard enemy. "Anchor" = a CANON §10e value. f(L) = (L + 9)/10.

---

## 2. CANON §10 reproduced (verbatim)

> Copied unchanged from `docs/00_CANON.md` §10 (v1.0, 2026-10-06), character for character, from its first paragraph to the end of the sanity calculations.

`formulas_and_curves.md` must reproduce this section exactly and may only add derived tables. Rounding rule everywhere: **round half up** at the end of each formula unless a formula says ⌊floor⌋, with the binding intermediate-rounding exceptions listed in the §10e assumptions.

### §10a Stats, caps, curves

| Stat | Abbr | Function | Cap |
|---|---|---|---|
| Hit Points | HP | KO ("Swoon") at 0 | 9,999 (party); **65,535 per HP bar** (enemies; a 16-bit word; superbosses chain bars as phases) |
| Inspiration | INS | Pays for Harmony skills, Recitals, some commands (the MP equivalent) | 999 |
| Strength | STR | Physical Attack Rating | 99 |
| Artistry | ART | Skill and spell power, healing | 99 |
| Defense | DEF | Physical mitigation (base + gear) | 255 |
| Resolve | RES | Magical mitigation and status resistance (base + gear) | 255 |
| Tempo | TMP | ATB fill speed | 99 |
| Luck | LCK | Crits, hit/evade adjustment, steal, rare drops | 99 |
| Weapon Attack | ATK | From the weapon | 255 |
| Evasion / Magic Evasion | EVA / M.EVA | % dodge (gear and relics only) | 75% |

**Level cap 99. Damage and heal cap 9,999 per hit.**
- **Growth:** Stat(L) = Base₁ + g × (L − 1); g = S 0.90 / A 0.75 / B 0.60 / C 0.45 / D 0.30. Opus Score level-up bonuses add on top (§11c).
- **HP(L)** = 40 + h × L + 0.6 × L²; h = S 32 / A 28 / B 25 / C 22 / D 19.
- **INS(L)** = 10 + i × L + 0.05 × L²; i = S 4.5 / A 3.8 / B 3.0 / C 2.2 / D 1.5.
- **EXP to reach level L** = ⌊10 × (L − 1)^2.6⌋: L10 = 3,027; L20 = 21,123; L30 = 63,421; L40 = 137,014; L99 = 1,503,792.
- **Enemy EXP** (each living active member receives it in full): X(E) = ⌊0.7 × E^1.6 + 2E⌋ at enemy level E; bosses ×12. Reserve members receive 50% (100% while Farrenc is in the active party).
- **Enemy francs:** G(E) = ⌊1.5E + E²/12⌋; bosses ×10. Seoul enemies drop won: G(E) × 200.
- **Opus Points (OP):** standard enemy 1–3, boss 10–30 (§11c).

### §10b Core formulas

- **Attack Rating:** AR = 2 × ATK + STR (party). Enemies list AR directly: standard enemy AR = 1.5 × L + 5; boss AR = 2.5 × L + 10.
- **Physical damage** = AR × (L + 9)/10 × 100/(100 + DEF_target) × VAR(0.90–1.10) × MOD.
- **Magical damage** = (4 × PWR + 2 × ART) × (L + 9)/10 × 100/(100 + RES_target) × VAR × MOD. A spell spread to all targets ×0.5.
- **Healing** = (4 × PWR + 2 × ART) × (L + 9)/10 × VAR(0.95–1.05); ignores RES; spread ×0.5. Items heal fixed amounts.
- **PWR tiers:** attack T1 12 / T2 28 / T3 50 / T4 80 / T5 120; heal T1 10 / T2 24 / T3 45 / T4 70. Availability: T1 from CH-01, T2 from CH-05, T3 from CH-10, T4 from CH-14, T5 post-game and epilogue optional content. Synergies: Duo 160, Trio 220, Quartet 260, Octave 4 hits × 300. (Party only: enemies never use the PWR formula; see the enemy model below.)
- **INS cost by tier:** attack T1 4 / T2 9 / T3 16 / T4 28 / T5 50; heal T1 5 / T2 10 / T3 18 / T4 30. Recital Movement I = 6 + 2 × Heat. Synergies cost no INS. *Check:* 4 T1 casts at CH-01 (16 INS), about 10 T2 casts at CH-09 (95), 7.5 T4 casts at CH-16 (210).
- **MOD (multiplicative):** crit ×2; weakness ×2, resist ×0.5, null ×0, absorb ×−1; Varnish ×0.5 (physical taken); Glaze ×0.5 (magical taken); Defend ×0.5; Fortissimo ×1.5 (next action); Light State ±25% (§10c); back row ×0.5 for melee dealt and taken (row-free weapons, spells and commands ignore row).
- **Physical hit %** = clamp(WeaponAcc + (LCK_a − LCK_t)/4 − EVA_t, 5, 99); WeaponAcc 90–100.
- **Status-inflict %** = clamp(Base + (ART_a − RES_t)/2 − M.EVA_t, 5, 95). Damage spells always hit unless reflected or nulled. Bosses carry immunity lists (bosses doc).
- **Critical %** = 3 + LCK/8 (≈ 15% at LCK 99). Annotate marks force crits. Synergies never crit.
- **ATB:** gauge 0–256. Fill per second = (TMP + 25) × 1.6 × SpeedSet × StatusMod. SpeedSet (options 1–6) = 1.5 / 1.3 / 1.15 / **1.0 (default)** / 0.85 / 0.7. Allegro ×1.5, Lento ×0.5, Fermata ×0. *Check:* TMP 15 → 64/s → 4.0 s per turn; TMP 30 → 88/s → 2.9 s; TMP 60 → 136/s → 1.9 s. Active and Wait modes (Wait default). Battle start: random 0–(2 × TMP). Preemptive: party gauges full. Back attack: party gauges 0, rows reversed.
- **Rows:** front/back per member (FF6). Back row halves melee dealt and taken.
- **Boss DEF/RES** = 1.2 × the standard enemy DEF of the boss's level (below).
- **Party RES** (with gear) = 5 + 1.5L (same curve as party DEF).
- **Enemy model (binding for bestiary and bosses).** *Standard enemy:* TMP = 10 + 0.45L; LCK = 5 + 0.5L; EVA and M.EVA 0–10% by family; ART (used for status-inflict only) = 5 + L; Magic Attack Rating **MAR = 1.8L + 6**; **enemy spell damage = MAR × (L + 9)/10 × 100/(100 + RES_target) × VAR**, ×0.5 when spread to all. *Boss:* TMP = 15 + 0.5L; LCK = 10 + 0.6L; ART = 10 + 1.5L; MAR = 3.0L + 12. *Check:* a CH-09 standard enemy spell = 44 × 3.0 × 100/137 = **96** (11.6% of 830 HP); a CH-16 one = 78 × 4.9 × 100/165 = **232** (11.6% of 2,000).

### §10c Elements and Light States

Opposite pairs: **FIRE ↔ ICE, WIND ↔ EARTH, BOLT ↔ WATER, LIGHT ↔ SHADE**. **CHRONO** has no opposite.

| UI name | Flavour name | Musical / painterly flavour |
|---|---|---|
| FIRE | Vermilion | *Forte*: red pigment, passion, brass |
| ICE | Cerulean | *Pianissimo*: cold blue, glassy harmonics |
| WIND | Zephyr | Woodwinds, breath, the plein-air breeze |
| EARTH | Ochre | *Basso*: earth pigments, timpani, stone |
| BOLT | Sforzando | Sudden accents, struck strings, lightning |
| WATER | Ondine | Arpeggios, the Seine, reflections |
| LIGHT | Lumen | Major keys, gold leaf, lead white |
| SHADE | Umbra | Minor keys, lamp-black, chiaroscuro |
| CHRONO | Tempus | Time itself: the cabal's arts, the Engine, Min-jun's late skills, Unwritten. Party members resist it only through the relics *Metronome of Nohant* and *Pleyel Tuning Hammer* (UI: "Nohant Metronome", "Tuning Hammer"); enemies may resist or absorb it as listed in §13. Every CHRONO action is Anachronic (Heat 5). |

Rules: weakness ×2, resist ×0.5, null ×0, absorb heals. **Dual-element attacks** (Canvas, some Synergies) use whichever element gives the attacker the better multiplier; they are resisted only if both elements are resisted and absorbed only if both are absorbed.

**Light States.** Every battle has one, set by location and time, shown as a HUD icon. Painted Lights (Dawn/Noon/Dusk/Night) come from Lucile's *Shift the Hour*, some Études, Canvases and enemy skills; LUMIÈRE lets two coexist (contradictory modifiers cancel).

| Light | Default where | Boost +25% / weaken −25% | Passive |
|---|---|---|---|
| Dawn | Outdoors 05–08 h | +LIGHT +ICE / −SHADE −FIRE | Party regen +1/32 max HP per turn (weaker than Cantabile) |
| Noon | Outdoors by day | +FIRE +EARTH / −ICE −WIND | Party ATK +10% |
| Dusk | Outdoors 17–20 h | +WATER +WIND / −BOLT −EARTH | Party EVA +10% |
| Night | Outdoors at night | +SHADE +BOLT / −LIGHT −WATER | Enemy hit −10%; party crit +5%; Echoes +10% damage |
| Candle | Interiors, salons | +FIRE | — |
| Fog | Rain, river, fog | +WATER +WIND | All physical hit −10% |
| Gloom | Underground | +SHADE / −LIGHT | All hit −10% |

### §10d Statuses (durations count the bearer's own turns)

| Status | Type | Effect | Duration | Cure |
|---|---|---|---|---|
| Swoon (KO) | − | HP 0 | — | Sal Volatile, Sel de Vie, *Encore* |
| Miasma | − | −1/16 max HP per turn (never called "cholera") | until cured | Four Thieves (*Vinaigre des Quatre Voleurs*), *Clarity*, Panacea |
| Smoke | − | Physical hit −50% | 4 | Eyewash, *Clarity* |
| Hush | − | No Harmony, Recitals, Synergies or painting commands | 4 | Throat Lozenge, *Clarity* |
| Reverie | − | Cannot act; wakes when damaged | 3–5 | Damage, Smelling Salts |
| Delirium | − | Attacks random targets | 4 or until hit | Damage, Panacea |
| Stagefright | − | Skips next 2 turns (1 turn after a broken Recital, §5c) | 2 | Courage Draught, Panacea |
| Stun | − | Loses its next turn | 1 | Wears off (bosses immune unless stated) |
| Lento | − | ATB ×0.5 | 5 | *Allegro* cancels |
| Fermata | − | ATB frozen | 3 | Wears off; Chopin's Rubato Repay |
| Marble | − | Petrified (counts as KO for a wipe) | until cured | Sculptor's Oil, Panacea |
| Coda | − | Countdown → KO | 20 (5 when a boss says so) | Recital *Da Capo* resets; Encore triggers on KO |
| Frenzy | − | Auto-Fight, ATK +50% | battle | Panacea |
| Out of Tune | − | ART −25%, INS costs +50% | 5 | Pitch Pipe, Panacea |
| Discord | − | Cannot join Synergies; gives no Crescendo Gauge | 5 | Pitch Pipe, Panacea |
| Swing | − | ATB fill randomly ×0.5–×1.5 each second | 4 | Wears off |
| Unwritten | − (CHRONO) | Removed from battle; returns after 3 turns with current HP; whole party Unwritten = wipe. Min-jun immune until CH-17 (LAW-04 resonance; the Heart's shattering ends it, LAW-13) | 3 | Wears off |
| Composed | − (enemy) | DEF and RES −50% (from 10 Pointillé Dots) | 3 | — |
| Allegro | + | ATB ×1.5 | 6 | — |
| Varnish | + | Physical damage taken ×0.5 | battle | Dispel |
| Glaze | + | Magical damage taken ×0.5 | battle | Dispel |
| Cantabile | + | +1/16 max HP per turn | 6 | — |
| Mirror | + | Reflects single-target spells | 3 reflections | Dispel |
| Encore | + | Auto-revive at 25% HP once | until triggered | — |
| Fortissimo | + | Next action ×1.5 | 1 action | — |
| Swell (stack) | + | +10% ATK and ART per stack (max 5); −1 stack per 2 turns ("Crescendo" always means the shared gauge, §11b) | — | — |
| Inspired | + | INS costs −50% | 4 | — |
| Bulwark | + | Damage taken −50%; intercepts hits aimed at allies below 25% HP | 4 | — |
| Tacet | + | Holding a full ATB: DEF/RES +25% until acting | until act | — |

### §10e Balance Anchor Table

Assumptions (all computed from §10a–b): average STR = 12 + 0.6(L − 1); best shop weapon ATK = 10 + 2.2L; party DEF and RES (with gear) = 5 + 1.5L; standard enemy DEF = RES = 3 + 1.05L; caster ART (A-grade) = 13 + 0.75(L − 1); "typical spell" = best available tier, single target; standard enemy HP = 3.5 × typical physical damage; standard enemy hit ≈ 8.5–10% of average HP; boss HP anchor = 4 actions × typical physical × target rounds (8 Act I, 10 Act II, 12 Act III, 13 Act IV, 15 epilogue, 25 per superboss bar set), scaled by party size with the §13 rules.
- **Intermediate rounding (binding):** Weapon ATK, AR, party DEF/RES, enemy DEF/RES, enemy AR and enemy MAR are rounded half up **before use**; average STR and caster ART stay fractional (ART 42.25 at Lv 40). Standard enemy HP rounds to the nearest 10 and the boss anchor to the nearest 100. Avg max HP and INS use the grade-B curves (h 25, i 3.0). The boss anchor uses typical damage against standard DEF; against a boss's 1.2× DEF, real fights run ≈ 5–8% more rounds.

| Chapter | Avg Lv | Avg max HP | Avg max INS | Weapon ATK | AR | Party DEF | Enemy DEF/RES | Typical phys dmg | Typical spell dmg (tier) | Std enemy HP | Enemy AR | Std enemy dmg/hit | EXP / F per std enemy | Boss HP anchor (4 PCs) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CH-01 | 2 | 92 | 16 | 14 | 41 | 8 | 5 | 43 | 79 (T1) | 150 | 8 | 8 | 6 / 3 | 1,400 |
| CH-02 | 4 | 150 | 23 | 19 | 52 | 11 | 7 | 63 | 95 (T1) | 220 | 11 | 13 | 14 / 7 | 2,000 |
| CH-03 | 7 | 244 | 33 | 25 | 66 | 16 | 10 | 96 | 121 (T1) | 340 | 16 | 22 | 29 / 14 | 3,100 |
| CH-04 | 10 | 350 | 45 | 32 | 81 | 20 | 14 | 135 | 146 (T1) | 470 | 20 | 32 | 47 / 23 | 4,300 |
| CH-05 | 12 | 426 | 53 | 36 | 91 | 23 | 16 | 165 | 280 (T2) | 580 | 23 | 39 | 61 / 30 | 6,600 |
| CH-06 | 14 | 508 | 62 | 41 | 102 | 26 | 18 | 199 | 307 (T2) | 700 | 26 | 47 | 75 / 37 | 8,000 |
| CH-07 | 16 | 594 | 71 | 45 | 111 | 29 | 20 | 231 | 334 (T2) | 810 | 29 | 56 | 91 / 45 | 9,200 |
| CH-08 | 19 | 732 | 85 | 52 | 127 | 34 | 23 | 289 | 376 (T2) | 1,010 | 34 | 71 | 115 / 58 | 11,600 |
| CH-09 | 21 | 830 | 95 | 56 | 136 | 37 | 25 | 326 | 403 (T2) | 1,140 | 37 | 81 | 133 / 68 | 13,100 |
| CH-10 | 23 | 932 | 105 | 61 | 147 | 40 | 27 | 370 | 653 (T3) | 1,300 | 40 | 91 | 151 / 78 | 17,800 |
| CH-11 | 26 | 1,096 | 122 | 67 | 161 | 44 | 30 | 433 | 709 (T3) | 1,520 | 44 | 107 | 180 / 95 | 20,800 |
| CH-12 | 29 | 1,270 | 139 | 74 | 177 | 49 | 33 | 506 | 766 (T3) | 1,770 | 49 | 125 | 211 / 113 | 24,300 |
| CH-13 | 32 | 1,454 | 157 | 80 | 191 | 53 | 37 | 572 | 816 (T3) | 2,000 | 53 | 142 | 243 / 133 | 27,400 |
| CH-14 | 34 | 1,584 | 170 | 85 | 202 | 56 | 39 | 625 | 1,223 (T4) | 2,190 | 56 | 154 | 265 / 147 | 32,500 |
| CH-15 | 37 | 1,786 | 189 | 91 | 216 | 61 | 42 | 700 | 1,296 (T4) | 2,450 | 61 | 174 | 300 / 169 | 36,400 |
| CH-16 | 40 | 2,000 | 210 | 98 | 231 | 65 | 45 | 781 | 1,367 (T4) | 2,730 | 65 | 193 | 336 / 193 | 40,600 |
| CH-E1/E2 | 43 | 2,224 | 231 | 105 | 247 | 70 | 48 | 868 | 1,437 (T4) | 3,040 | 70 | 214 | 373 / 218 | 52,100 |
| Superbosses | 50 | 2,790 | 285 | 120 | 281 | 80 | 56 | 1,063 | 2,192 (T5) | 3,720 | 80 | 262 | 465 / 283 | 106,300 (3 bars) |

**Sanity calculations.**
- *CH-09 physical:* L21, ATK 56, STR 24 → AR 136 × 3.0 × 100/125 = **326** ✓. A standard enemy (1,140 HP) falls in 3.5 hits ✓.
- *CH-09 enemy:* AR 37 × 3.0 × 100/137 = **81** = 9.8% of 830 HP ✓ (about 10 unhealed hits to KO). Across the table the standard hit runs 8.6–9.8% ✓.
- *CH-16 physical:* L40, AR 231 × 4.9 × 100/145 = **781** ✓. Enemy: 65 × 4.9 × 100/165 = **193** = 9.7% of 2,000 ✓.
- *Spell:* T4 at L40, ART 42.25: (320 + 84.5) × 4.9 × 100/145 = **1,367** ✓.
- *Boss:* BOSS-12 Roussel I, 13,000 HP ÷ (4 × 326) ≈ **10 rounds** ✓. BOSS-26 Archon, 30,000 ÷ (4 × 781) ≈ 9.6 rounds before Synergies ✓.
- *Octave vs BOSS-27 (36,000 HP, RES 58):* (4 × 300 + 2 × 42.25) × 4.9 × 100/158 = **3,984 per hit × 4 = 15,935**. With the minimum 3 confidants (+30%) = 20,715 (58% of the bar); with all 7 confidants and Julien's Blue Note (×1.79) = 28,524 (79%). The Octave breaks the ward and never one-shots; 2–5 rounds of normal damage finish it ✓.
- *Healing:* T2 heal (24) at L21, ART 28: (96 + 56) × 3.0 = **456** = 55% of 830 ✓.
- *Damage cap:* L99, ATK 180, STR 99 → AR 459 × 10.8 × 100/207 (Lv-99 standard enemy DEF 107) = 2,395 × Fortissimo 1.5 × crit 2 = 7,185 × weakness 2 → **9,999 cap**, reachable only by stacking ✓.
- *ATB:* a CH-09 average member (TMP ≈ 22) fills in 256/(47 × 1.6) = **3.4 s** ✓.
- *Levelling:* from CH-03 the anchors need 11–34 standard-enemy kills per CP hour (Act I ≈ 9, Act II ≈ 16, Act III ≈ 26, Act IV ≈ 26, epilogues ≈ 29; mean ≈ 19) plus story-boss EXP (×12). CH-01–02 levels come mainly from BOSS-01/02. **Encounter-rate target for dungeons.md** (dungeons ≈ 45% of CP time, 2–4 enemies per battle): one battle per ~5 minutes of exploration in Acts I–II and per ~3 minutes in Acts III–IV and the epilogues. Optional CH-14 content can push the party to 42 before the finale.
- *Superbosses:* going from Lv 45 to Lv 50 needs 60,544 EXP ≈ 140 late-game kills, which fits the 5.5 h of optional epilogue and post-game play (§4). BOSS-31/34 sit at Lv 55 (3 bars × 36,000); BOSS-43 keeps Lv 99 (NG+ carries levels).

---

## 3. Conventions: notation, rounding, order of operations, stacking

### 3.1 Notation

| Symbol | Meaning | Range or source |
|---|---|---|
| L, E | Level of the acting unit (party member, or enemy E) | 1–99 |
| f(L) | Level factor (L + 9)/10 | 1.0 at Lv 1, 4.9 at Lv 40, 10.8 at Lv 99 |
| ATK | Weapon attack | 0–255; shop bands CANON §14; targets in 9 |
| STR, ART, DEF, RES, TMP, LCK | Stats | Curves in 7; caps in 2 |
| AR | Attack Rating | Party 2 × ATK + STR; enemies listed |
| MAR | Enemy Magic Attack Rating | Enemy model (2) |
| PWR | Skill power | T1–T5, heal T1–T4, Synergy PWR (2) |
| VAR | Variance multiplier | 0.90–1.10 damage, 0.95–1.05 healing (4.6) |
| MOD | Product of all modifiers | 3.4 |
| EVA, M.EVA | Evasion, magic evasion (%) | Gear and relics only, 0–75 |
| WeaponAcc | Weapon accuracy | 90–100 by class (9) |
| _a, _t | Attacker, target | — |
| A | Boss action budget: damaging actions per boss turn | 10.4 |

### 3.2 Rounding and integer implementation

Canon (CANON §10, §10e): round half up at the end of each formula; ⌊ ⌋ where written; Weapon ATK, AR, party DEF/RES, enemy DEF/RES, enemy AR and MAR are rounded half up **before use**. This doc adds:

1. **Every stored stat is an integer.** A party member's stat at level L is the curve value rounded half up (the CANON §5b method). Fractional values (average STR, caster ART 42.25) exist only inside the §10e anchor derivation.
2. **Enemy TMP, LCK and ART** are rounded half up when an enemy is built and stored as bytes.
3. **Engine arithmetic: one exact rational per hit.** Each damage or heal is computed as a single fraction in 64-bit integers: numerator = power term × (L + 9) × 100 × (90 + r) × every MOD numerator (and every stat-modifier numerator, 3.4 rule 3); denominator = 10 × (100 + DEF or RES) × 100 × every MOD denominator. Result = (2 × numerator + denominator) div (2 × denominator), which is round half up. Healing drops the mitigation factor and uses (95 + r). No floating point and no fixed-point intermediate rounding, except the canon's listed pre-rounded quantities (Weapon ATK, AR, party DEF/RES, enemy DEF/RES, enemy AR and MAR, CANON §10e). PC and Switch builds therefore produce identical numbers. *Check (4.6 Ex A, r = 0):* 85 × 19 × 100 × 90 ÷ (10 × 114 × 100) = 14,535,000 ÷ 114,000 = 127.5 → **128**. The largest numerator in play (AR 459 × 108 × 100 × 110, then crit 2/1, Fortissimo 3/2, weakness 2/1 and Light 5/4) stays below 2⁴⁰.
4. **Percent chances are rolled in basis points:** success if rand(10,000) < chance × 100.
5. **Negative results** (absorb) round the magnitude half up, then negate.

### 3.3 Order of operations (every damage or healing event)

1. **Power term:** AR (physical); 4 × PWR + 2 × ART (party magic and healing); MAR (enemy magic). Percentage stat modifiers have already been applied to the stat they name (3.4, rule 3): weapon ATK inside AR, STR inside AR, ART inside the magical term.
2. **× f(L)** of the acting unit.
3. **× mitigation** 100/(100 + DEF_t) or 100/(100 + RES_t). Healing skips this step.
4. **× VAR** (one roll per hit per target).
5. **× MOD**, the product of every modifier in 3.4 (crit, element, Light State, row, spread, guards, buffs, passives).
6. **Round half up** once.
7. **Clamp:** null anywhere in the MOD chain gives 0 (pop-up "Null"); otherwise minimum 1, maximum 9,999.
8. **Apply:** absorb heals the target instead; HP clamps to 0…max; damage beyond the remaining HP of an enemy bar is discarded (12.5).

### 3.4 Modifier stacking

1. **Different sources multiply** (CANON §10b "MOD (multiplicative)").
2. **Stacks of one source add before multiplying:** Swell 10% per stack (max 5); Liszt's Bravura 10% per action (max 50%); Berlioz's Idée Fixe 15% per Fight (max 3 stacks); IMPRESSION's streak 20% per turn (max 100%); Octave confidants 10% each plus Julien's Blue Note 9% (the CANON §10e check uses 1 + 0.70 + 0.09 = ×1.79); *Recorded Echo* 5% per 20% of the KEY-23 recording.
3. **Percentage stat modifiers change the stat they name, and nothing else** (the literal CANON §10a–d reading). "ATK ±x%" scales **weapon ATK** inside AR = 2 × ATK + STR (CANON §10a defines ATK as the weapon's): Noon "Party ATK +10%" (CANON §10c), Frenzy +50%, Swell +10% per stack. "ART ±x%" scales the **ART stat** inside 4 × PWR + 2 × ART and in status rolls: Out of Tune −25%, Swell +10% per stack (CANON §10d). "STR ±x%" scales STR inside AR (Recluse +25%). "DEF/RES ±x%" scale the defensive stat (Composed −50%, Tacet +25%). A modified weapon ATK, the AR built from it and a modified DEF or RES are rounded half up before use, as CANON §10e lists them; a modified ART stays an exact fraction inside the one-rational computation (3.2 rule 3). *Example:* Noon on Alkan at Lv 40 makes his ATK 98 × 1.1 = 107.8 → 108 and his AR 2 × 108 + 50 = **266** (from 246). *Consequence:* ART is about 21% of the magical term at T4 and Lv 40, so Out of Tune costs a T4 caster about 6% of a spell's damage (Liszt, Lv 40: 1,336 → 1,257 against RES 54) and its real bite is the ×1.5 INS cost; at T1 it costs about 9%. This doc prefers a stronger reading and files it as a CCR in the last section; it is not used until adopted. On enemies, `combat_ensemble` §9 applies Out of Tune to MAR and status ART.
4. **Elements:** weakness ×2, resist ×0.5, null ×0, absorb ×−1; a dual-element attack takes the better multiplier for the attacker (CANON §10c). The Light State ×1.25 or ×0.75 is applied for the element actually chosen.
5. **Named multipliers:** Fortissimo ×1.5; CONDUCT ×1.25; Plein Air ×1.25 (Lucile's styles in Dawn, Noon, Fog); Chiaroscuro ×1.25 (Canvas in Dusk, Night, Candle); Sideman ×1.2; Echoes at Night ×1.1; Sotto Voce heals ×1.2; Defend, Varnish, Glaze, Bulwark ×0.5 on damage taken; back row ×0.5 melee dealt and taken; spread ×0.5, row ×0.75 (4.5).

*Stack example:* Liszt at Lv 40 (ART 50) casting T4 with Swell 2, Bravura 3, a weakness and a boosted Light. Swell 2 raises his ART to 60, so the power term goes from 320 + 100 = 420 to 320 + 120 = 440 (×1.048); then Bravura ×1.30 × weakness ×2 × Light ×1.25 = **×3.40** overall: 1,400 × 3.25 = 4,550 against RES 54, instead of 1,336.

---

## 4. Combat formulas, with worked examples

Every example uses stats from section 7 (curve values rounded half up) and anchor gear from section 9.

### 4.0 Curves and costs

| Formula (CANON §10a–b) | Example A | Example B |
|---|---|---|
| **Stat(L)** = Base₁ + g × (L − 1), rounded half up | Liszt's ART (S, base 15) at Lv 26: 15 + 0.90 × 25 = 37.5 → **38** | Alkan's STR (S, base 15) at Lv 40: 15 + 0.90 × 39 = 50.1 → **50** |
| **HP(L)** = 40 + h × L + 0.6 × L² | Alkan (S, h 32) at Lv 26: 40 + 832 + 405.6 = **1,278** | Min-jun (B, h 25) at Lv 40: 40 + 1,000 + 960 = **2,000** (the CANON §10e anchor) |
| **INS(L)** = 10 + i × L + 0.05 × L² | Chopin (S, i 4.5) at Lv 21: 10 + 94.5 + 22.05 = 126.55 → **127** | Min-jun (A, i 3.8) at Lv 1: 10 + 3.8 + 0.05 = 13.85 → **14** (CANON §5b) |
| **EXP to reach L** = ⌊10 × (L − 1)^2.6⌋ | Lv 21: ⌊10 × 20^2.6⌋ = **24,136** | Lv 45: ⌊10 × 44^2.6⌋ = **187,489**; the step 44 → 45 costs 10,878 |
| **Recital Movement I** = 6 + 2 × Heat INS | A Heat-3 piece: 6 + 6 = **12 INS** | A Heat-5 piece: 6 + 10 = **16 INS**; Out of Tune never applies (Perfect Pitch) |
| **Boss DEF/RES** = 1.2 × standard DEF of the boss's level | BOSS-12 (Lv 22): standard DEF 3 + 23.1 = 26.1 → 26; × 1.2 = 31.2 → **31** | BOSS-26 (Lv 40): standard DEF 45 × 1.2 = **54** |

### 4.1 Attack Rating

**AR = 2 × ATK + STR** (party). Standard enemy AR = 1.5L + 5; boss AR = 2.5L + 10. All rounded half up before use.

- *Example A.* Delacroix, CH-04, Lv 10: STR = 14 + 0.75 × 9 = 20.75 → **21**; anchor Prélude rapier ATK 32 → AR = 64 + 21 = **85**.
- *Example B.* Alkan, CH-16, Lv 40: STR = 15 + 0.90 × 39 = 50.1 → **50**; Opus Magnum hammer ATK 98 → AR = 196 + 50 = **246**. For comparison, a Lv-40 standard enemy has AR 65 and BOSS-26 (Lv 40) has AR 110.

### 4.2 Physical damage

**Physical = AR × f(L) × 100/(100 + DEF_t) × VAR × MOD.** Used by Fight and by every skill tagged PHYS (weapon-based: it can miss, it can crit, and row applies unless the weapon or command is row-free).

- *Example A.* Delacroix (AR 85, Lv 10) Fights a CH-04 Black Coat (standard Lv 10, DEF 14): 85 × 1.9 × 100/114 = 141.67 → **128 to 156** across the VAR range, mean 142. (The anchor's typical 135 uses the average STR of 17.4.)
- *Example B.* Alkan (AR 246, Lv 40) against BOSS-26 Archon (DEF 1.2 × 45 = 54): 246 × 4.9 × 100/154 = 782.7. With a crit (×2) and Fortissimo (×1.5): **2,348** (2,113 to 2,583 across VAR). From the back row, hammers not being row-free, ×0.5: 1,174.

### 4.3 Magical damage, PWR tiers and INS

**Magical = (4 × PWR + 2 × ART) × f(L) × 100/(100 + RES_t) × VAR × MOD;** spread ×0.5. INS costs per CANON §10b; Out of Tune ×1.5, Inspired ×0.5, TRANSCEND (two spells) total ×1.5; costs round half up, minimum 1 for any non-zero cost.

- *Example A.* Liszt, CH-11, Lv 26: ART = 15 + 0.90 × 25 = 37.5 → **38**. A T3 BOLT against a standard Lv-26 enemy (RES 30): (200 + 76) × 3.5 × 100/130 = **743**. Against BOSS-14 the Rheinwolf (Lv 27, RES 1.2 × 31 = 37) with an ICE spell into its weakness: 705 × 2 = **1,410**. TRANSCEND with two T3 spells costs (16 + 16) × 1.5 = 48 of his 143 INS.
- *Example B.* Lucile, CH-06, Lv 14, ART 24: a T2 spell at all enemies (Lv 14, RES 18): (112 + 48) × 2.3 × 100/118 = 311.9 → ×0.5 = **156 each**. Enemy side: a CH-09 standard enemy spell is 44 × 3.0 × 100/137 = **96** (the CANON check); BOSS-26's party-wide spell (MAR 132) against party RES 65 is 132 × 4.9 × 100/165 × 0.5 = **196** per member (392 single-target).

### 4.4 Healing and HP ticks

**Healing = (4 × PWR + 2 × ART) × f(L) × VAR(0.95–1.05);** ignores RES; spread ×0.5; items heal fixed amounts (CANON §14). **Ticks:** Miasma −1/16, Cantabile +1/16 and Dawn +1/32 of max HP resolve when the bearer's gauge fills, before the command (`combat_ensemble` §3.6); round half up, minimum 1. **No cap** (CANON §10d): on enemies too a Miasma tick is 1/16 of the bar's max HP, so a 36,000-HP bar loses 2,250 per tick and BOSS-26 (30,000) 1,875. Bosses answer it only through the immunity lists `bosses` writes (CANON §10b); a 999 cap is filed as a CCR (last section) and is not used.

- *Example A.* Chopin, CH-09, Lv 21, ART = 15 + 0.75 × 20 = **30**: T2 heal (96 + 60) × 3.0 = 468; Sotto Voce ×1.2 = **562** (534 to 590), which is 68% of an 830-HP member.
- *Example B.* Farrenc, CH-16, Lv 40, ART = 13 + 0.75 × 39 = 42.25 → **42**: T4 heal to all, (280 + 84) × 4.9 = 1,784 → ×0.5 = **892 each** (45% of a 2,000-HP member). Miasma on the same member costs 125 HP per turn.

### 4.5 Multi-target split

| Targeting | Multiplier | Applies to |
|---|---|---|
| Single target | ×1 | Default |
| Row (one party row, or one enemy column) | ×0.75 | Canvas Subject "row", SYN-21, row-hitting enemy skills |
| All (spread) | ×0.5 | Spells, heals, Tutti, Invocations, Synergies "to all", enemy spells (CANON §10b) |
| Multi-hit, fixed target | Power term ÷ hits, per hit | SYN-02 (8 hits), SYN-09 (6), *Nuit étoilée* (8); each hit rolls VAR and crit separately |
| Multi-hit, random targets | Power term ÷ hits, per hit, no spread penalty | POINTILLÉ (8 hits), Spiccato (4) |

Rules: (1) the spread or row penalty applies only if two or more valid targets exist when the action resolves; on a lone survivor it is ×1. (2) A multi-hit skill's listed PWR is its total; each hit uses (4 × PWR + 2 × ART)/n, so splitting never changes total damage before crits, weakness and the 9,999 cap. The Octave (SYN-16) is the one exception: 4 hits × PWR 300 **each** (canon). (3) **Synergy stat rule:** a Duo, Trio or Quartet uses the magical formula with its canon PWR, the **mean ART** of its participants and the **mean level** of its participants (`combat_ensemble` §6.4 quotes this rule); it never crits. **The Octave (SYN-16) is the exception: it uses Min-jun's ART and level** (`combat_ensemble` §6.7), because the eight members' mean ART at Lv 40 is 39.4 (315 ÷ 8), which would give 15,863 instead of the CANON §10e check's 15,935. The canon check uses the anchor caster ART 42.25, which is Min-jun's unrounded Lv-40 curve value; with his stored ART 42 each hit is (1,200 + 84) × 4.9 × 100/158 = 3,982, so 15,928 for four hits (−0.05%).

- *Example A.* SYN-08 at CH-04 (BE and DE, both ART 16, Lv 10) against a barricade wave of two Black Coats (RES 14, 470 HP each): (640 + 32) × 1.9 × 100/114 = 1,120 → spread ×0.5 = **560 each**: the wave falls in one Synergy.
- *Example B.* SYN-02 at CH-07 (MJ ART 24, LI ART 29, mean 26.5, Lv 16) against BOSS-09 (RES 25, BOLT-weak): (640 + 53) × 2.5 × 100/125 = 1,386 total → 173.25 per hit × 2 (weakness) = **347 per hit, 2,776 for all eight**.

### 4.6 Damage variance

**VAR = (90 + r)/100,** r a uniform integer 0–20 (21 outcomes, mean exactly 1.00). Healing uses (95 + r)/100 with r 0–10. One roll per hit per target, enemies included. P(VAR ≥ 1.05) = 6/21 = 28.6%.

- *Example A.* Delacroix's 141.67 base hit: r = 0 → **128**, r = 10 → 142, r = 20 → **156**.
- *Example B.* Chopin's 561.6 heal base: r = 0 → **534**, r = 10 → **590**.

### 4.7 Critical hits

**Critical % = 3 + LCK/8.** Implemented as crit_bp = 300 + ⌊12.5 × LCK⌋ basis points; Night adds 500 bp (party only). Annotate marks force crits on any damage type. Synergies never crit; healing never crits; enemies crit only with physical attacks. A crit is ×2 in MOD.

- *Example A.* Min-jun at Lv 1 (LCK 13): 300 + 162 = **462 bp = 4.62%**.
- *Example B.* Jae-won at Lv 45 (LCK 54): 300 + 675 = **9.75%**, 14.75% at Night; LCK 99 gives 15.37% (the canon's "≈ 15%"). A Lv-21 standard enemy (LCK 16) crits 5% of the time for 162, which is 19.5% of an 830-HP member.

### 4.8 Physical hit and evasion

**Hit % = clamp(WeaponAcc + (LCK_a − LCK_t)/4 − EVA_t, 5, 99),** then the situational multipliers that `combat_ensemble` §8.3 and §9 fix for the canon's percentage wording, with a final floor of 5%: Smoke ×0.5 ("Physical hit −50%"); Fog ×0.9 on physical hits, both sides ("All physical hit −10%"); Gloom ×0.9 on every hit and status roll, both sides ("All hit −10%"); Night ×0.9 on enemy hit and status rolls ("Enemy hit −10%"). **Dusk:** party members' EVA_t +10 (cap 75%), inside the clamp ("Party EVA +10%"). These are readings of canon text, listed for the Lead Designer in the last section. Enemy WeaponAcc: standard 95, boss 100 (the bestiary may set 90–100 by family). Damage spells always hit (canon).

- *Example A.* Alkan (hammer, Acc 90, LCK 11 at Lv 11) against a CH-05 Gaslight Wisp (Lv 12, LCK 11, EVA 10): 90 + 0 − 10 = **80%**; in Gloom 72%.
- *Example B.* A Lv-21 standard enemy (Acc 95, LCK 16) against Chopin (LCK 23 at Lv 21, EVA 8 from gear): 95 − 1.75 − 8 = **85.25%**; at Night 76.7%; Smoked at Night 38.4%; at Dusk (EVA 18) 75.25%.

### 4.9 Status infliction

**Status % = clamp(Base + (ART_a − RES_t)/2 − M.EVA_t, 5, 95),** then Gloom ×0.9 (and Night ×0.9 for enemy casters), floor 5 (`combat_ensemble` §8.3). Party RES = base + gear (9). Out of Tune lowers the ART used here by 25%.

| Status | Base band (this doc) | `combat_ensemble` §9 default |
|---|---|---|
| Smoke, Lento, Out of Tune | 60–70 | 65 |
| Hush, Delirium, Discord, Swing | 50–60 | 55 |
| Frenzy | 45–55 | 50 |
| Reverie, Stagefright, Miasma | 35–50 | 45 |
| Stun, Fermata | 30–40 | 35 |
| Marble, Coda | 25–35 | 30 |
| Enemy-cast Unwritten | 40 | 40 |

Each skill states its own Base inside its band (`skills_and_progression`, `bestiary`). Boss immunity lists stay with `bosses`.

- *Example A.* Chopin (Lv 16, ART 26) casts a Base-60 Lento on a standard Lv-16 enemy (RES 20, M.EVA 5): 60 + 3 − 5 = **58%**.
- *Example B.* BOSS-04 Le Chantre (Lv 9, ART 10 + 13.5 → 24) uses its Hush (Base 55, the default) on Delacroix (Lv 7, RES 14 + 1 from Prélude armour = 15): 55 + 4.5 = 59.5%, and in the undercroft's Gloom 59.5 × 0.9 = **53.6%**. An Ossuary Echo (Lv 2, ART 7) exhaling Miasma (Base 45) on Min-jun (RES 13): 45 − 3 = 42%, in the galleries' Gloom **37.8%**.

### 4.10 ATB, battle start and formations

**Fill per second = (TMP + 25) × 1.6 × SpeedSet × StatusMod;** turn time = 256 ÷ fill. The engine adds fill ÷ 60 per frame at 60 Hz. Swing multiplies fill by (0.5 + 0.1r), r uniform 0–10, re-rolled each second. Battle start: random 0 to 2 × TMP for every unit (canon). **Formations** are rolled in order on every random encounter (`combat_ensemble` §5.2 fixes their layouts and opening gauges; the odds below are this doc's, which it quotes). ΔLCK = party mean LCK − enemy mean LCK, over living active members and enemies.

| Formation | Chance | Rolled | Opening gauges (`combat_ensemble` §5.2) | Flee (5.6) |
|---|---|---|---|---|
| Preemptive | clamp(6 + ΔLCK/4, 2, 16)%; +25 percentage points outdoors while Lucile is active (her Plein Air "+25% preemptive chance", CANON §5c, read as points), maximum 40% | First | Party 256, enemies 0 | Normal |
| Back Attack | clamp(4 − ΔLCK/8, 1, 8)% | Only if no Preemptive | Party 0, enemies random; rows reversed (CANON §10b) | ×0.5 |
| Pincer | 2% | Only if both fail, and only on maps `dungeons` or `overworld_and_towns` flag *open* | Random; no rows (all front) | ×0.5 |
| Side Attack | 2% | Only if Pincer fails, *open* maps only | Party 256, enemies 0 | First check succeeds |
| Normal | Remainder | — | Random 0–(2 × TMP) | Normal |

None of these occurs in boss or scripted battles; relics may move them (`items_and_equipment`).

- *Example A.* Min-jun, Lv 2, TMP 13: 38 × 1.6 = 60.8 per second → **4.21 s per turn**; his first turn, from a starting gauge of 0–26, comes after 3.8–4.2 s.
- *Example B.* Liszt, Lv 40, TMP 50, Allegro: 75 × 1.6 × 1.5 = 180 per second → **1.42 s**; at SpeedSet 6 (×0.7) 2.03 s. A CH-10 field battle with MJ, LU, LI, AL (mean LCK 23.5) against Lv-23 enemies (LCK 17), ΔLCK 6.5: preemptive 6 + 1.625 = 7.6%, outdoors with Lucile **32.6%**; back attack clamp(4 − 0.81, 1, 8) = 3.2% of the rest. On an *open* map the outdoor battle therefore opens Preemptive 32.6%, Back Attack 2.1%, Pincer 1.3%, Side Attack 1.3%, Normal 62.6%.

### 4.11 Enemy model in practice

The canon model (section 2) gives every enemy number from its level. This doc adds standard WeaponAcc 95 and boss 100, and applies the MOD chain to enemy spells (element, Glaze, Defend, Bulwark, Light State, spread; no crits on spells).

- *Example A.* A CH-09 standard enemy's physical hit on party DEF 37: 37 × 3.0 × 100/137 = **81** (9.8% of 830 HP).
- *Example B.* BOSS-26's physical hit on a Lv-40 party (DEF 65): 110 × 4.9 × 100/165 = **327** (16.3% of 2,000 HP); its single-target spell is 392 (19.6%).

### 4.12 Crescendo Gauge in practice

Canon gains and costs are in CANON §11b. Implementation: the HP-loss gain is computed per hit as 100 × damage ÷ max HP for the member hit, accumulated with fractions kept per member and paid out in whole points. The simulations in section 11 give boss-fight gains of **28–61 points per round** on the critical path and about 80 against superbosses. With the boss-battle start of 50, the first Duo is affordable in round 1 or 2, then one Duo every ≈ 2 rounds, a Trio every ≈ 4 or a Quartet every ≈ 6.

- *Example A.* CH-09, BOSS-12 hits the party for 326 HP per round on average (9.8% of party HP, i.e. 39% of one member's 830): +39, plus a Recital movement every other round (+1.5); BOSS-12 has no weakness to feed the +2 bonus, so ≈ **+41 per round** and a Duo every 2.4 rounds.
- *Example B.* CH-16, BOSS-26 against MJ, DE, AL, CH at Lv 40 (mean max HP 2,010): the boss side takes 1,063 HP per round, 13.2% of party HP, which is +53 (1,063 ÷ 2,010 × 100, summed over the members hit); Min-jun's Recital adds a movement every other round (+1.5) and the casters' LIGHT weakness hits about +1.6, so ≈ **+56 per round**. From the floor of 50 (`combat_ensemble` §11.8) the first Duo is ready in round 1 and the next every 1.8 rounds, which is the 5 Duos of the 11.3 row.

---

## 5. Reward and field formulas, with worked examples

### 5.1 EXP award

**X(E) = ⌊0.7 × E^1.6 + 2E⌋;** bosses ×12, applied after the floor. Each **living** active member receives the formation total in full; reserve members receive ⌊50%⌋ (100% while Farrenc is active); members Swooned, Marbled or Unwritten when the battle ends receive 0; guests gain none (CANON §6). Defeated enemies count; fled ones do not. This doc adds:

- **Duels, the Rapture battle and survival battles award no EXP** (BOSS-03, 08, 17, 20, 32, 35; BOSS-16). They pay OP (5.3), Renown and purses instead. This is what makes the pacing in 6.2 land on the canon's act averages.
- **Boss parts and adds** (heads, gears, horns, easels, wolves, the Phantom Quartet, wave members) **award no EXP, francs or OP**; the core's ×12 pays for the whole fight. This keeps 6.2, 8.3 and the income check valid: at the elite rate they would add about 8,900 critical-path EXP (BOSS-05's waves alone 912, 38% of CH-04's budget).
- **A boss that leaves by its own script** at an HP threshold or a timer (BOSS-02 flees at 25%, BOSS-18's Brücke escapes at 50%, BOSS-19's Roussel withdraws) counts as defeated and pays in full.
- **Split and solo segments** (CH-09 threads, CH-11 and CH-12 Lucile, CH-13 fronts, CH-15 parties) follow 6.3.

*Example A.* A CH-06 formation of three standard Lv-14 enemies: 3 × 75 = **225 EXP** to each active member; 112 to each reserve member, or 225 with Farrenc active.
*Example B.* BOSS-12 (Lv 22): ⌊98.4 + 44⌋ = 142 × 12 = **1,704 EXP** to each of the four on the field at the end (Min-jun's phase-2 join counts as active, `combat_ensemble` §11.8); members in the other CH-09 thread receive 852, or 1,704 if Farrenc fought.

### 5.2 Francs and won

**G(E) = ⌊1.5E + E²/12⌋;** bosses ×10; Seoul enemies pay G(E) × 200 won. Paid once per battle into the shared purse, for defeated enemies only.

*Example A.* The CH-06 formation above pays 3 × 37 = **111 F**.
*Example B.* A standard-class S08 static sentinel automaton (Lv 43) pays 218 × 200 = **₩43,600** (a minion-class automaton in a static pack pays ⌊218 × 0.4⌋ = 87 F, ₩17,400); BOSS-30 (Lv 44) pays 227 × 10 × 200 = **₩454,000**.

### 5.3 Opus Points (OP)

| Enemy class | OP per enemy defeated |
|---|---|
| Standard | 1 at Lv 1–19, 2 at Lv 20–39, 3 at Lv 40+ (CANON "1–3") |
| Minion | 1 |
| Elite | Standard + 1 |
| Mini-boss (gatekeepers outside CANON §13) | 6 + ⌊Lv/4⌋ |
| Boss (every CANON §13 boss, BOSS-41 and BOSS-42 included) | clamp(8 + ⌊Lv/2⌋, 10, 30) (CANON "10–30") |
| Duel, Rapture or survival battle | The boss value at the chapter's §10e anchor level |

Every active member with a Score equipped earns the battle total; reserve members ⌊50%⌋. Farrenc's Equal Measure covers EXP only (CANON §5c), not OP. Boss parts and adds pay nothing (5.1). Split segments follow 6.3: in CH-13's single three-front battle every member earns all three bosses' OP.

*Example A.* The CH-06 formation: **3 OP** to each active equipper.
*Example B.* BOSS-12 (Lv 22): 8 + 11 = **19 OP**; the BOSS-08 Thalberg duel (CH-07 anchor Lv 16): 8 + 8 = **16 OP**.

### 5.4 Drops

On each defeat, roll the rare slot first: **rare % = clamp(4 + (LCK_best − LCK_t)/4, 2, 16),** where LCK_best is the highest LCK among living active members. If it fails, roll the common slot at **35%**. Bosses give their guaranteed reward (`bosses` doc) with no roll. Fled or escaped enemies drop nothing; a steal never removes a drop.

*Example A.* CH-06: Min-jun (LCK 23) against a Lv-14 enemy (LCK 12): rare 4 + 2.75 = **6.75%**; common 35% of the remainder = 32.6%; nothing 60.6%.
*Example B.* Jae-won (Lv 45, LCK 54) against a Lv-55 Ossia phantom (LCK 33): rare 4 + 5.25 = **9.25%**.

### 5.5 Steal

**Success = clamp(40 + LCK_a − LCK_t, 5, 95)%** (CANON §11a). "1 success in 8 takes the rare slot" is implemented as a 1/8 roll on each success, plus a **pity rule**: the 8th successful steal against the same ENM ID without a rare is forced rare (a counter per ENM ID, kept in the save). After any success the enemy is picked clean. GALOP and a perfect BEAT use the same formula with the user's LCK.

*Example A.* Min-jun (Lv 7, LCK 18) wearing the Cartouche Glove against a Lv-7 enemy (LCK 9): **49%**; the rare slot comes 6.1% per attempt.
*Example B.* Jae-won (Lv 43, LCK 52) lands a perfect BEAT on a standard-class S08 static sentinel automaton (Lv 43, LCK 27): **65%**.

### 5.6 Escape

**Per second held: 10% + (party mean TMP − enemy mean TMP)%, clamp 5–90** (CANON §11a). Means are over living active members and living enemies, using the TMP stat (ATB statuses do not count). One check per 60 frames of running battle time while L + R are held; releasing resets the timer; in Wait mode the timer runs only while battle time runs. **Formation rules** (`combat_ensemble` §12.1): after a Back Attack or in a Pincer the chance is halved (after the clamp, so 2.5–45%); in a Side Attack the first check succeeds. Success leaves with no rewards and no penalty beyond the battle's end: the Crescendo Gauge empties, as after every battle (CANON §11b), and Heat already added stays. Impossible in boss and scripted battles.

*Example A.* CH-03: MJ 16, BE 13, DE 15 and Alkan as a guest on his own curves (TMP 13, 7.1 rule 6), mean 14.25, against Lv-7 enemies (TMP 13): **11.25% per second**; 30.1% within 3 seconds; mean 8.9 s; after a Back Attack 5.6% per second.
*Example B.* CH-15: LI 47, LU 42, MJ 34, CH 40, mean 40.75, against Lv-37 enemies (TMP 27): **23.75% per second**; 55.7% within 3 seconds; mean 4.2 s.

### 5.7 Encounter rate per step

After each battle, map load or scripted battle, a **grace** of G steps passes with no encounter; after that, each step rolls **rand(65,536) < 16 × R × M** (R is stated per 4,096, so every modifier below stays an exact integer). Mean steps between battles = **G + 4,096 ÷ (R × M)**. A step is one 16-px tile moved. M is the product of modifiers: Hunted tier ×1.25 (CANON §11e, `overworld_and_towns` §3); a relic effect `ENC_HALF` ×0.5 or `ENC_NONE` ×0 (the items doc names the relics); Lucile's solo segments (CH-11 interlude, CH-12) ×0.5 in Echo zones. The War overlay (W01 from CH-14) raises a zone one rate tier instead of multiplying (12.1). No roll is made on bridges, on the lit boulevard spine, aboard any vehicle or aloft, on W03, in towns or in the Heart Chamber (12.1). Calibration: **90 steps per exploration minute in dungeons** (walk speed 1 px per frame = 3.75 tiles/s, about 40% of dungeon time spent moving) and **200 on overworld maps** (`overworld_and_towns` §1 sets 1 tile per 8 frames there, 450 tiles a minute, so about 44% of overworld time is spent moving). Per-area values are in 12.1.

*Example A.* An Act II dungeon (G 144, R 11): mean 516 steps ≈ **5.7 minutes**; chance of a battle within the first 300 steps = 1 − (1 − 11/4,096)^156 = **34%**.
*Example B.* An Act III dungeon while Hunted (R 17 × 1.25 = 21.25, threshold 340 of 65,536; G 64): mean **257 steps ≈ 2.9 minutes**, against 305 steps (3.4 minutes) at Watched or below.

---

## 6. EXP table and level pacing

### 6.1 The EXP table (levels 1–99)

**EXP to reach level L = ⌊10 × (L − 1)^2.6⌋** (CANON §10a). "Cumulative" is the total needed to reach that level; "To next" is the gap to the following level. Canon checkpoints reproduce exactly: Lv 10 = 3,027; Lv 20 = 21,123; Lv 30 = 63,421; Lv 40 = 137,014; Lv 99 = 1,503,792. EXP gained at Lv 99 is discarded.

| Lv | Cumulative | To next | Lv | Cumulative | To next | Lv | Cumulative | To next |
|---|---|---|---|---|---|---|---|---|
| 1 | 0 | 10 | 34 | 88,743 | 7,162 | 67 | 538,039 | 21,453 |
| 2 | 10 | 50 | 35 | 95,905 | 7,508 | 68 | 559,492 | 21,972 |
| 3 | 60 | 113 | 36 | 103,413 | 7,859 | 69 | 581,464 | 22,495 |
| 4 | 173 | 194 | 37 | 111,272 | 8,216 | 70 | 603,959 | 23,022 |
| 5 | 367 | 289 | 38 | 119,488 | 8,579 | 71 | 626,981 | 23,555 |
| 6 | 656 | 398 | 39 | 128,067 | 8,947 | 72 | 650,536 | 24,092 |
| 7 | 1,054 | 520 | 40 | 137,014 | 9,323 | 73 | 674,628 | 24,633 |
| 8 | 1,574 | 654 | 41 | 146,337 | 9,703 | 74 | 699,261 | 25,179 |
| 9 | 2,228 | 799 | 42 | 156,040 | 10,090 | 75 | 724,440 | 25,729 |
| 10 | 3,027 | 954 | 43 | 166,130 | 10,481 | 76 | 750,169 | 26,284 |
| 11 | 3,981 | 1,119 | 44 | 176,611 | 10,878 | 77 | 776,453 | 26,843 |
| 12 | 5,100 | 1,295 | 45 | 187,489 | 11,281 | 78 | 803,296 | 27,407 |
| 13 | 6,395 | 1,480 | 46 | 198,770 | 11,690 | 79 | 830,703 | 27,975 |
| 14 | 7,875 | 1,673 | 47 | 210,460 | 12,103 | 80 | 858,678 | 28,547 |
| 15 | 9,548 | 1,876 | 48 | 222,563 | 12,523 | 81 | 887,225 | 29,124 |
| 16 | 11,424 | 2,087 | 49 | 235,086 | 12,947 | 82 | 916,349 | 29,705 |
| 17 | 13,511 | 2,307 | 50 | 248,033 | 13,376 | 83 | 946,054 | 30,290 |
| 18 | 15,818 | 2,535 | 51 | 261,409 | 13,812 | 84 | 976,344 | 30,880 |
| 19 | 18,353 | 2,770 | 52 | 275,221 | 14,252 | 85 | 1,007,224 | 31,473 |
| 20 | 21,123 | 3,013 | 53 | 289,473 | 14,697 | 86 | 1,038,697 | 32,072 |
| 21 | 24,136 | 3,265 | 54 | 304,170 | 15,148 | 87 | 1,070,769 | 32,674 |
| 22 | 27,401 | 3,523 | 55 | 319,318 | 15,603 | 88 | 1,103,443 | 33,280 |
| 23 | 30,924 | 3,789 | 56 | 334,921 | 16,064 | 89 | 1,136,723 | 33,891 |
| 24 | 34,713 | 4,061 | 57 | 350,985 | 16,529 | 90 | 1,170,614 | 34,506 |
| 25 | 38,774 | 4,342 | 58 | 367,514 | 17,000 | 91 | 1,205,120 | 35,125 |
| 26 | 43,116 | 4,629 | 59 | 384,514 | 17,475 | 92 | 1,240,245 | 35,748 |
| 27 | 47,745 | 4,922 | 60 | 401,989 | 17,956 | 93 | 1,275,993 | 36,375 |
| 28 | 52,667 | 5,223 | 61 | 419,945 | 18,441 | 94 | 1,312,368 | 37,006 |
| 29 | 57,890 | 5,531 | 62 | 438,386 | 18,932 | 95 | 1,349,374 | 37,641 |
| 30 | 63,421 | 5,844 | 63 | 457,318 | 19,426 | 96 | 1,387,015 | 38,281 |
| 31 | 69,265 | 6,164 | 64 | 476,744 | 19,926 | 97 | 1,425,296 | 38,924 |
| 32 | 75,429 | 6,491 | 65 | 496,670 | 20,430 | 98 | 1,464,220 | 39,572 |
| 33 | 81,920 | 6,823 | 66 | 517,100 | 20,939 | 99 | 1,503,792 | — (cap) |

### 6.2 Level pacing per chapter

Method: the party enters each chapter at the previous chapter's exit level and leaves at the top of the CANON §4a range (the levels a chapter is *played* at; CH-01 and CH-02 exit about one level higher because their closing bosses alone are worth most of a level). Story-boss EXP is the core ×12 at the boss's own level (duels, Rapture and survival pay 0; parts and adds pay 0, per 5.1); the remainder is filled by standard kills at the chapter's anchor level. CH-01 and CH-02 are boss-driven (CANON §10e): their kill counts are the handful of fights the dungeons force. Kills come from dungeons (≈ 45% of CP time from CH-05, 30% in town-heavy Act I; CANON §10e) and from **overworld walking** on W01 and W02 with encounters on: **4% of CP time in CH-02–CH-04, 3% in CH-05–CH-08, 1% in CH-09, 6% in CH-10, 4% in CH-11, 2% in CH-12, 6% in CH-14 and CH-E2, and none in CH-01, CH-13, CH-15–CH-17 or CH-E1** (fiacres, the omnibus, the barge, diligence legs, the steamboat and the dirigible all skip encounters; W03 has no rolls). Overworld foes stand at anchor −2 to +0 (`overworld_and_towns` §3), so each counts as 0.83–0.97 of an anchor kill; 12.1 trims the dungeon rates so that the totals below still hold. Formations average **2.35 foes in Act I** and **3 afterwards** in dungeons (12.1 weights) and 2.75 on the overworld; "Battles / CP h" divides the kills by the dungeon mean.

| Chapter | CP h | Lv in → out | EXP needed | Story-boss EXP | Std kills | of which overworld | Kills / CP h | Battles / CP h |
|---|---|---|---|---|---|---|---|---|
| CH-P | 0.5 | 1 → 1 | 0 | 0 (no battles) | 0 | 0 | 0 | 0 |
| CH-01 | 1 | 1.0 → 4.2 | 173 | 168 (BOSS-01) | 8 | 0 | 8.0 | 3.4 |
| CH-02 | 1.25 | 4.2 → 5.7 | 151 | 288 (BOSS-02) | 4 | 2 | 3.2 | 1.4 |
| CH-03 | 2.25 | 5.7 → 8.0 | 1,014 | 492 (BOSS-04) | 18 | 5 | 8.0 | 3.4 |
| CH-04 | 2.5 | 8.0 → 11.0 | 2,407 | 732 (BOSS-05) | 36 | 6 | 14.3 | 6.1 |
| CH-05 | 2 | 11.0 → 13.0 | 2,414 | 900 (BOSS-06) | 25 | 3 | 12.4 | 4.1 |
| CH-06 | 2 | 13.0 → 15.0 | 3,153 | 1,092 (BOSS-07) | 27 | 3 | 13.7 | 4.6 |
| CH-07 | 2.25 | 15.0 → 17.0 | 3,963 | 1,188 (BOSS-09) | 30 | 4 | 13.6 | 4.5 |
| CH-08 | 2 | 17.0 → 20.0 | 7,612 | 2,868 (BOSS-10, BOSS-11) | 41 | 4 | 20.6 | 6.9 |
| CH-09 | 2 | 20.0 → 22.0 | 6,278 | 1,704 (BOSS-12) | 34 | 1 | 17.2 | 5.7 |
| CH-10 | 2 | 22.0 → 24.0 | 7,312 | 1,932 (BOSS-13) | 36 | 8 | 17.8 | 5.9 |
| CH-11 | 1.75 | 24.0 → 27.0 | 13,032 | 2,280 (BOSS-14) | 60 | 5 | 34.1 | 11.4 |
| CH-12 | 2.25 | 27.0 → 30.0 | 15,676 | 2,652 (BOSS-15) | 62 | 3 | 27.4 | 9.1 |
| CH-13 | 2 | 30.0 → 33.0 | 18,499 | 6,096 (BOSS-18 and BOSS-19: one battle, 6.3) | 51 | 0 | 25.5 | 8.5 |
| CH-14 | 1.5 | 33.0 → 35.0 | 13,985 | 3,312 (BOSS-21) | 40 | 7 | 26.9 | 9.0 |
| CH-15 | 2.5 | 35.0 → 39.0 | 32,162 | 12,201 received on average (own Warden 3,600, the other two at the reserve share, BOSS-25 3,876; 6.3) | 81 fought (≈ 67 received) | 0 | 32.6 | 10.9 |
| CH-16 | 1 | 39.0 → 41.0 | 18,270 | 12,984 (BOSS-26, 27, 28) | 16 | 0 | 15.7 | 5.2 |
| CH-17 | 0.25 | 41 → 41 | 0 | 0 (no battles) | 0 | 0 | 0 | 0 |
| CH-E1 | 3 | 41.0 → 45.0 | 41,152 | 8,952 (BOSS-29, BOSS-30) | 86 | 0 | 28.8 | 9.6 |
| CH-E2 | 3 | 41.0 → 45.0 | 41,152 | 4,632 (BOSS-33; BOSS-32 duel 0) | 98 | 10 | 32.6 | 10.9 |

**Act averages:** Act I 9.4 kills per CP hour (1.9 of them overworld), Act II 15.5 (1.5), Act III 26.0 (1.9), Act IV 26.2 (1.4), epilogues 28.8 (CH-E1) to 32.6 (CH-E2, 3.4 overworld). CANON §10e states ≈ 9 / 16 / 26 / 26 / 29: **match**. CH-E2's extra twelve kills come from the Living Tableau battles of the Canvas Ledger (CANON §4f), which is where its missing second story boss would otherwise sit. CH-E1's static pockets on W03 sit outside this budget (12.1).

**Split chapters.** *CH-09:* the row tracks the BOSS-12 four. Min-jun, caged for most of the chapter, receives the reserve share of the Bercy battles he does not fight (6.3) and ends about 0.6 level behind them, or level with them if Farrenc fought in the Bercy thread. *CH-13:* the three fronts are one battle, so every member receives both BOSS-18 and BOSS-19 (the canon's own Act III target of ≈ 26 assumes exactly this; counting one boss per member would give 27.6). *CH-15:* each member receives its own party's battles in full and the other two parties' at the reserve share; with Farrenc in Party 1 and in the merged four, and 20% of the chapter's battles fought after the merge, a member receives 0.82 of every kill fought, so the parties together fight 81 kills to deliver the 67 each member needs. With Farrenc in Party 3 every figure moves by under 2%; with Julien recruited (3 / 3 / 3), by under 3%.

**Income check.** Running G(E) over the same kills, with boss francs ×10, chests at 25% of battle francs and the CANON §14 salon shares, gives Act I **348 F/h**, Act II **1,595**, Act III **4,526**, Act IV **9,591**, epilogues **10,618**, against the CANON §14 table's 350 / 1,600 / 4,500 / 9,000 / 10,700. Every act is within 1% except Act IV (+6.6%): CH-15's three parties fill one purse, so all three Wardens pay their 1,690 F. The surplus only eases the affordability rule; `salons_duels_and_economy` may take about 4,500 F out of CH-15's chests to land on 9,000.

**Optional levelling.** CH-14's optional content (4.5 h) at the Act III–IV encounter rate yields about 26 kills per hour at Lv 34–38: about 117 kills or 34,000 EXP. The five optional bosses add 19,188 more (BOSS-36 4,032, BOSS-37 2,916, BOSS-38 4,032, BOSS-39 4,032, BOSS-40 4,176). A completionist therefore leaves CH-14 at **about 41** (149,093 EXP: 41.3; CANON §4a "opt to 42") and, after CH-15's critical-path EXP, enters CH-16 at **about 44** (44.4), four levels over the CH-16 anchor: the reward for optional play is a BOSS-26 that falls in about 8.4 canon-pace rounds (typical Fight 896 at Lv 44) instead of 9.6. Post-game Lv 45 → 50 needs 60,544 EXP, about 140 kills at Lv 45–50 (CANON §10e).

### 6.3 Late joiners and reserve lag

**Join rule** (CANON §5): a member who joins or rejoins arrives at max(listed level, active-party average − 1), the average rounded half up, with EXP set to that level's cumulative value. *Examples:* Farrenc joins early in CH-08 with the party at 17 → max(18, 16) = **18**; Lucile rejoins at the start of CH-12 with the party at 27 → max(11, 26) = **26**, or her own level if higher; Berlioz and Delacroix, last active at about 22 in CH-09, return in CH-12 at **26** by the same rule.

**The join rule also fires at the start of every solo or split segment** and at every regrouping: the CH-09 threads, the CH-11 Lucile interlude, the CH-12 Lucile solo and the CH-12 regrouping, the CH-13 fronts, and the CH-15 parties and their merge. Each controlled member rises to max(own level, average − 1), where the average is that of the last full active party (rounded half up). Levels gained this way apply the equipped Score's shape (8.1).

**EXP and OP in split and solo segments** (CANON §10a reserve rule, applied as `combat_ensemble` §11.8 sets it):

| Segment | Who is active | Everyone else |
|---|---|---|
| CH-09 threads (Min-jun's cell; BOSS-12's Bercy thread, BE + 2; the other thread) and CH-15 parties (3 / 3 / 2, then the merged four) | The thread's or party's own members, in full; a mid-battle `JOIN` (BOSS-12 phase 2) counts as active | Every other permanent member present in the chapter receives the reserve share of that battle: EXP 50%, or 100% while Farrenc fights in it; OP 50% (Equal Measure covers EXP only) |
| CH-13 three-front battle (`combat_ensemble` §11.2: one battle, one reward screen) | Every permanent member on a front: the whole battle's EXP (BOSS-18 + BOSS-19 = 6,096; BOSS-17 pays none) and OP (24 + 24 + 24 = 72) | Offenbach is a guest and gains nothing |
| CH-11 Lucile interlude, CH-12 Lucile solo | Lucile alone, in full | The Rhine and Paris parties gain nothing from her battles, and she nothing from theirs (she is not in their roster, CANON §4a); the join rule closes the gap |

*Lucile's path:* she leaves at the CH-09 dawn at about 20, rejoins in CH-10 at 21 (party 22 − 1) and ends CH-10 at about 23.1; she earns nothing on the Rhine; the CH-11 interlude raises her to **25** (party average 25.5 → 26, − 1) if act3 places it mid-chapter, or 26 if it follows BOSS-14; the CH-12 solo opens at **26** (party 27 − 1).

**Reserve lag.** A member benched at Lv 20 while the actives climb to Lv 30 gains half of 42,298 EXP and ends at 42,272 cumulative: **Lv 25.8, four levels behind**. With Farrenc active the lag is zero. This is the mechanical case for her passive, and the reason the join rule exists for members who are away from the party entirely.

---

## 7. Stat growth per playable character

### 7.1 Growth rules

1. **Curve stats:** Stat(L) = round half up of Base₁ + g × (L − 1), g by grade S 0.90 / A 0.75 / B 0.60 / C 0.45 / D 0.30. HP(L) and INS(L) per CANON §10a by grade. Recomputed from scratch at every level-up, so rounding never accumulates.
2. **Opus ledger** (8.1) is added on top: flat points to STR, ART, DEF, RES, TMP, LCK; percentages multiply the HP and INS curves.
3. **DEF and RES below are base values.** Gear adds the section 9 targets, so that the party mean with gear sits on the CANON anchor 5 + 1.5L.
4. **Passives applied after the curve:** Chopin's Sotto Voce ×0.9 max HP; Seo-yeon's Sibling ×1.2 TMP while Min-jun is active; Alkan's Recluse ×1.25 STR in its condition. Percent modifiers to max HP add together before multiplying (Chopin with +20% Opus HP has ×1.10, not ×1.08).
5. **Caps:** STR, ART, TMP, LCK 99; DEF, RES 255 with gear; HP 9,999; INS 999 (12.5). Curves alone first touch 99 at Lv 94 (Alkan STR; Liszt ART and TMP) and Lv 95 (Jae-won and Julien LCK). No curve reaches 9,999 HP (Alkan's Lv-99 maximum is 9,089) or 999 INS (Chopin's is 946); those caps need Opus percentages.
6. **Guest template:** guests (CANON §6) are fixed at the chapter anchor level with Lv-1 bases STR 12 / ART 13 / DEF 10 / RES 11 / TMP 12 / LCK 11, grade B in every stat, and anchor gear. Their STR curve is exactly the §10e average STR, so a guest *is* the anchor party member. **The template applies to GST-01–GST-11 only.** A permanent member who appears as a guest before joining (Alkan in CH-03, CANON §5a) uses his own PC curves at the anchor level with anchor gear: at Lv 7 HP 293, STR 20, DEF 18, TMP 13 (AR 70; DEF 21 with Prélude armour), keeping his S-grade STR and A-grade DEF; as a guest he still counts 0.5 in the party-size factor and has only Fight, Defend and Item (`combat_ensemble` §4.0). Remembrances (CH-E1) cast with the giver's Lv-50 row below (Lv 55 once the busking ladder is cleared), weapon ATK 120 (131 at Lv 55) and no Opus ledger.

### 7.2 Join stats (CANON §5b, reproduced and verified)

Every value below was recomputed from the Lv-1 bases, grades and curves; all 88 match CANON §5b.

| ID | Join Lv | HP | INS | STR | ART | DEF | RES | TMP | LCK | Grades HP/INS/STR/ART/DEF/RES/TMP/LCK | Lv-1 bases STR/ART/DEF/RES/TMP/LCK |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PC-01 MJ | 1 | 66 | 14 | 10 | 13 | 9 | 12 | 12 | 13 | B/A/C/A/C/A/B/A | 10/13/9/12/12/13 |
| PC-02 LU | 11 | 355 | 58 | 15 | 22 | 11 | 17 | 23 | 18 | C/A/C/A/D/B/A/B | 10/14/8/11/15/12 |
| PC-03 BE | 5 | 195 | 26 | 15 | 13 | 14 | 11 | 12 | 11 | A/B/B/B/B/C/C/C | 13/11/12/9/10/9 |
| PC-04 DE | 6 | 212 | 30 | 18 | 14 | 14 | 13 | 14 | 11 | B/B/A/B/B/B/B/C | 14/11/11/10/11/9 |
| PC-05 AL | 11 | 465 | 33 | 24 | 13 | 21 | 14 | 15 | 11 | S/D/S/C/A/C/C/D | 15/8/13/9/10/8 |
| PC-06 CH | 13 | 388 | 77 | 11 | 24 | 11 | 25 | 22 | 18 | D/S/D/A/D/S/A/B | 7/15/7/14/13/11 |
| PC-07 LI | 15 | 505 | 78 | 19 | 28 | 15 | 19 | 28 | 19 | C/A/B/S/C/B/S/B | 11/15/9/11/15/11 |
| PC-08 FA | 18 | 684 | 95 | 17 | 26 | 20 | 26 | 18 | 26 | B/A/C/A/B/A/C/A | 9/13/10/13/10/13 |
| PC-09 SY | 40 | 1,880 | 242 | 27 | 42 | 27 | 34 | 43 | 35 | C/A/C/A/C/B/A/B | 9/13/9/11/14/12 |
| PC-10 JW | 40 | 2,120 | 178 | 42 | 20 | 34 | 27 | 43 | 49 | A/C/A/D/B/C/A/S | 13/8/11/9/14/14 |
| PC-11 JU | 33 | 1,419 | 190 | 23 | 37 | 22 | 29 | 37 | 43 | C/A/C/A/C/B/A/S | 9/13/8/10/13/14 |

### 7.3 Projected stats by level

Curve values, no Opus ledger, no gear (DEF and RES are base). Columns below a character's join level are formula values only (no one is ever below their join level in play) and exist so scaled content and Da Capo can read any level.

**PC-01 Kang Min-jun** · joins Lv 1 · grades HP/INS/STR/ART/DEF/RES/TMP/LCK B/A/C/A/C/A/B/A

| Lv | 1 | 5 | 10 | 15 | 20 | 25 | 30 | 35 | 40 | 45 | 50 | 60 | 70 | 80 | 99 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HP | 66 | 180 | 350 | 550 | 780 | 1,040 | 1,330 | 1,650 | 2,000 | 2,380 | 2,790 | 3,700 | 4,730 | 5,880 | 8,396 |
| INS | 14 | 30 | 53 | 78 | 106 | 136 | 169 | 204 | 242 | 282 | 325 | 418 | 521 | 634 | 876 |
| STR | 10 | 12 | 14 | 16 | 19 | 21 | 23 | 25 | 28 | 30 | 32 | 37 | 41 | 46 | 54 |
| ART | 13 | 16 | 20 | 24 | 27 | 31 | 35 | 39 | 42 | 46 | 50 | 57 | 65 | 72 | 87 |
| DEF | 9 | 11 | 13 | 15 | 18 | 20 | 22 | 24 | 27 | 29 | 31 | 36 | 40 | 45 | 53 |
| RES | 12 | 15 | 19 | 23 | 26 | 30 | 34 | 38 | 41 | 45 | 49 | 56 | 64 | 71 | 86 |
| TMP | 12 | 14 | 17 | 20 | 23 | 26 | 29 | 32 | 35 | 38 | 41 | 47 | 53 | 59 | 71 |
| LCK | 13 | 16 | 20 | 24 | 27 | 31 | 35 | 39 | 42 | 46 | 50 | 57 | 65 | 72 | 87 |

**PC-02 Lucile Aubray** · joins Lv 11 · grades HP/INS/STR/ART/DEF/RES/TMP/LCK C/A/C/A/D/B/A/B

| Lv | 1 | 5 | 10 | 15 | 20 | 25 | 30 | 35 | 40 | 45 | 50 | 60 | 70 | 80 | 99 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HP | 63 | 165 | 320 | 505 | 720 | 965 | 1,240 | 1,545 | 1,880 | 2,245 | 2,640 | 3,520 | 4,520 | 5,640 | 8,099 |
| INS | 14 | 30 | 53 | 78 | 106 | 136 | 169 | 204 | 242 | 282 | 325 | 418 | 521 | 634 | 876 |
| STR | 10 | 12 | 14 | 16 | 19 | 21 | 23 | 25 | 28 | 30 | 32 | 37 | 41 | 46 | 54 |
| ART | 14 | 17 | 21 | 25 | 28 | 32 | 36 | 40 | 43 | 47 | 51 | 58 | 66 | 73 | 88 |
| DEF | 8 | 9 | 11 | 12 | 14 | 15 | 17 | 18 | 20 | 21 | 23 | 26 | 29 | 32 | 37 |
| RES | 11 | 13 | 16 | 19 | 22 | 25 | 28 | 31 | 34 | 37 | 40 | 46 | 52 | 58 | 70 |
| TMP | 15 | 18 | 22 | 26 | 29 | 33 | 37 | 41 | 44 | 48 | 52 | 59 | 67 | 74 | 89 |
| LCK | 12 | 14 | 17 | 20 | 23 | 26 | 29 | 32 | 35 | 38 | 41 | 47 | 53 | 59 | 71 |

**PC-03 Hector Berlioz** · joins Lv 5 · grades HP/INS/STR/ART/DEF/RES/TMP/LCK A/B/B/B/B/C/C/C

| Lv | 1 | 5 | 10 | 15 | 20 | 25 | 30 | 35 | 40 | 45 | 50 | 60 | 70 | 80 | 99 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HP | 69 | 195 | 380 | 595 | 840 | 1,115 | 1,420 | 1,755 | 2,120 | 2,515 | 2,940 | 3,880 | 4,940 | 6,120 | 8,693 |
| INS | 13 | 26 | 45 | 66 | 90 | 116 | 145 | 176 | 210 | 246 | 285 | 370 | 465 | 570 | 797 |
| STR | 13 | 15 | 18 | 21 | 24 | 27 | 30 | 33 | 36 | 39 | 42 | 48 | 54 | 60 | 72 |
| ART | 11 | 13 | 16 | 19 | 22 | 25 | 28 | 31 | 34 | 37 | 40 | 46 | 52 | 58 | 70 |
| DEF | 12 | 14 | 17 | 20 | 23 | 26 | 29 | 32 | 35 | 38 | 41 | 47 | 53 | 59 | 71 |
| RES | 9 | 11 | 13 | 15 | 18 | 20 | 22 | 24 | 27 | 29 | 31 | 36 | 40 | 45 | 53 |
| TMP | 10 | 12 | 14 | 16 | 19 | 21 | 23 | 25 | 28 | 30 | 32 | 37 | 41 | 46 | 54 |
| LCK | 9 | 11 | 13 | 15 | 18 | 20 | 22 | 24 | 27 | 29 | 31 | 36 | 40 | 45 | 53 |

**PC-04 Eugène Delacroix** · joins Lv 6 · grades HP/INS/STR/ART/DEF/RES/TMP/LCK B/B/A/B/B/B/B/C

| Lv | 1 | 5 | 10 | 15 | 20 | 25 | 30 | 35 | 40 | 45 | 50 | 60 | 70 | 80 | 99 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HP | 66 | 180 | 350 | 550 | 780 | 1,040 | 1,330 | 1,650 | 2,000 | 2,380 | 2,790 | 3,700 | 4,730 | 5,880 | 8,396 |
| INS | 13 | 26 | 45 | 66 | 90 | 116 | 145 | 176 | 210 | 246 | 285 | 370 | 465 | 570 | 797 |
| STR | 14 | 17 | 21 | 25 | 28 | 32 | 36 | 40 | 43 | 47 | 51 | 58 | 66 | 73 | 88 |
| ART | 11 | 13 | 16 | 19 | 22 | 25 | 28 | 31 | 34 | 37 | 40 | 46 | 52 | 58 | 70 |
| DEF | 11 | 13 | 16 | 19 | 22 | 25 | 28 | 31 | 34 | 37 | 40 | 46 | 52 | 58 | 70 |
| RES | 10 | 12 | 15 | 18 | 21 | 24 | 27 | 30 | 33 | 36 | 39 | 45 | 51 | 57 | 69 |
| TMP | 11 | 13 | 16 | 19 | 22 | 25 | 28 | 31 | 34 | 37 | 40 | 46 | 52 | 58 | 70 |
| LCK | 9 | 11 | 13 | 15 | 18 | 20 | 22 | 24 | 27 | 29 | 31 | 36 | 40 | 45 | 53 |

**PC-05 Charles-Valentin Alkan** · joins Lv 11 · grades HP/INS/STR/ART/DEF/RES/TMP/LCK S/D/S/C/A/C/C/D

| Lv | 1 | 5 | 10 | 15 | 20 | 25 | 30 | 35 | 40 | 45 | 50 | 60 | 70 | 80 | 99 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HP | 73 | 215 | 420 | 655 | 920 | 1,215 | 1,540 | 1,895 | 2,280 | 2,695 | 3,140 | 4,120 | 5,220 | 6,440 | 9,089 |
| INS | 12 | 19 | 30 | 44 | 60 | 79 | 100 | 124 | 150 | 179 | 210 | 280 | 360 | 450 | 649 |
| STR | 15 | 19 | 23 | 28 | 32 | 37 | 41 | 46 | 50 | 55 | 59 | 68 | 77 | 86 | 99 |
| ART | 8 | 10 | 12 | 14 | 17 | 19 | 21 | 23 | 26 | 28 | 30 | 35 | 39 | 44 | 52 |
| DEF | 13 | 16 | 20 | 24 | 27 | 31 | 35 | 39 | 42 | 46 | 50 | 57 | 65 | 72 | 87 |
| RES | 9 | 11 | 13 | 15 | 18 | 20 | 22 | 24 | 27 | 29 | 31 | 36 | 40 | 45 | 53 |
| TMP | 10 | 12 | 14 | 16 | 19 | 21 | 23 | 25 | 28 | 30 | 32 | 37 | 41 | 46 | 54 |
| LCK | 8 | 9 | 11 | 12 | 14 | 15 | 17 | 18 | 20 | 21 | 23 | 26 | 29 | 32 | 37 |

**PC-06 Frédéric Chopin** · joins Lv 13 · grades HP/INS/STR/ART/DEF/RES/TMP/LCK D/S/D/A/D/S/A/B

| Lv | 1 | 5 | 10 | 15 | 20 | 25 | 30 | 35 | 40 | 45 | 50 | 60 | 70 | 80 | 99 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HP | 60 | 150 | 290 | 460 | 660 | 890 | 1,150 | 1,440 | 1,760 | 2,110 | 2,490 | 3,340 | 4,310 | 5,400 | 7,802 |
| HP ×0.9 (Sotto Voce) | 54 | 135 | 261 | 414 | 594 | 801 | 1,035 | 1,296 | 1,584 | 1,899 | 2,241 | 3,006 | 3,879 | 4,860 | 7,022 |
| INS | 15 | 34 | 60 | 89 | 120 | 154 | 190 | 229 | 270 | 314 | 360 | 460 | 570 | 690 | 946 |
| STR | 7 | 8 | 10 | 11 | 13 | 14 | 16 | 17 | 19 | 20 | 22 | 25 | 28 | 31 | 36 |
| ART | 15 | 18 | 22 | 26 | 29 | 33 | 37 | 41 | 44 | 48 | 52 | 59 | 67 | 74 | 89 |
| DEF | 7 | 8 | 10 | 11 | 13 | 14 | 16 | 17 | 19 | 20 | 22 | 25 | 28 | 31 | 36 |
| RES | 14 | 18 | 22 | 27 | 31 | 36 | 40 | 45 | 49 | 54 | 58 | 67 | 76 | 85 | 102 |
| TMP | 13 | 16 | 20 | 24 | 27 | 31 | 35 | 39 | 42 | 46 | 50 | 57 | 65 | 72 | 87 |
| LCK | 11 | 13 | 16 | 19 | 22 | 25 | 28 | 31 | 34 | 37 | 40 | 46 | 52 | 58 | 70 |

**PC-07 Franz Liszt** · joins Lv 15 · grades HP/INS/STR/ART/DEF/RES/TMP/LCK C/A/B/S/C/B/S/B

| Lv | 1 | 5 | 10 | 15 | 20 | 25 | 30 | 35 | 40 | 45 | 50 | 60 | 70 | 80 | 99 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HP | 63 | 165 | 320 | 505 | 720 | 965 | 1,240 | 1,545 | 1,880 | 2,245 | 2,640 | 3,520 | 4,520 | 5,640 | 8,099 |
| INS | 14 | 30 | 53 | 78 | 106 | 136 | 169 | 204 | 242 | 282 | 325 | 418 | 521 | 634 | 876 |
| STR | 11 | 13 | 16 | 19 | 22 | 25 | 28 | 31 | 34 | 37 | 40 | 46 | 52 | 58 | 70 |
| ART | 15 | 19 | 23 | 28 | 32 | 37 | 41 | 46 | 50 | 55 | 59 | 68 | 77 | 86 | 99 |
| DEF | 9 | 11 | 13 | 15 | 18 | 20 | 22 | 24 | 27 | 29 | 31 | 36 | 40 | 45 | 53 |
| RES | 11 | 13 | 16 | 19 | 22 | 25 | 28 | 31 | 34 | 37 | 40 | 46 | 52 | 58 | 70 |
| TMP | 15 | 19 | 23 | 28 | 32 | 37 | 41 | 46 | 50 | 55 | 59 | 68 | 77 | 86 | 99 |
| LCK | 11 | 13 | 16 | 19 | 22 | 25 | 28 | 31 | 34 | 37 | 40 | 46 | 52 | 58 | 70 |

**PC-08 Louise Farrenc** · joins Lv 18 · grades HP/INS/STR/ART/DEF/RES/TMP/LCK B/A/C/A/B/A/C/A

| Lv | 1 | 5 | 10 | 15 | 20 | 25 | 30 | 35 | 40 | 45 | 50 | 60 | 70 | 80 | 99 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HP | 66 | 180 | 350 | 550 | 780 | 1,040 | 1,330 | 1,650 | 2,000 | 2,380 | 2,790 | 3,700 | 4,730 | 5,880 | 8,396 |
| INS | 14 | 30 | 53 | 78 | 106 | 136 | 169 | 204 | 242 | 282 | 325 | 418 | 521 | 634 | 876 |
| STR | 9 | 11 | 13 | 15 | 18 | 20 | 22 | 24 | 27 | 29 | 31 | 36 | 40 | 45 | 53 |
| ART | 13 | 16 | 20 | 24 | 27 | 31 | 35 | 39 | 42 | 46 | 50 | 57 | 65 | 72 | 87 |
| DEF | 10 | 12 | 15 | 18 | 21 | 24 | 27 | 30 | 33 | 36 | 39 | 45 | 51 | 57 | 69 |
| RES | 13 | 16 | 20 | 24 | 27 | 31 | 35 | 39 | 42 | 46 | 50 | 57 | 65 | 72 | 87 |
| TMP | 10 | 12 | 14 | 16 | 19 | 21 | 23 | 25 | 28 | 30 | 32 | 37 | 41 | 46 | 54 |
| LCK | 13 | 16 | 20 | 24 | 27 | 31 | 35 | 39 | 42 | 46 | 50 | 57 | 65 | 72 | 87 |

**PC-09 Kang Seo-yeon** · joins Lv 40 · grades HP/INS/STR/ART/DEF/RES/TMP/LCK C/A/C/A/C/B/A/B

| Lv | 1 | 5 | 10 | 15 | 20 | 25 | 30 | 35 | 40 | 45 | 50 | 60 | 70 | 80 | 99 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HP | 63 | 165 | 320 | 505 | 720 | 965 | 1,240 | 1,545 | 1,880 | 2,245 | 2,640 | 3,520 | 4,520 | 5,640 | 8,099 |
| INS | 14 | 30 | 53 | 78 | 106 | 136 | 169 | 204 | 242 | 282 | 325 | 418 | 521 | 634 | 876 |
| STR | 9 | 11 | 13 | 15 | 18 | 20 | 22 | 24 | 27 | 29 | 31 | 36 | 40 | 45 | 53 |
| ART | 13 | 16 | 20 | 24 | 27 | 31 | 35 | 39 | 42 | 46 | 50 | 57 | 65 | 72 | 87 |
| DEF | 9 | 11 | 13 | 15 | 18 | 20 | 22 | 24 | 27 | 29 | 31 | 36 | 40 | 45 | 53 |
| RES | 11 | 13 | 16 | 19 | 22 | 25 | 28 | 31 | 34 | 37 | 40 | 46 | 52 | 58 | 70 |
| TMP | 14 | 17 | 21 | 25 | 28 | 32 | 36 | 40 | 43 | 47 | 51 | 58 | 66 | 73 | 88 |
| TMP ×1.2 (Sibling) | 17 | 20 | 25 | 30 | 34 | 38 | 43 | 48 | 52 | 56 | 61 | 70 | 79 | 88 | 99 |
| LCK | 12 | 14 | 17 | 20 | 23 | 26 | 29 | 32 | 35 | 38 | 41 | 47 | 53 | 59 | 71 |

**PC-10 Choi Jae-won** · joins Lv 40 · grades HP/INS/STR/ART/DEF/RES/TMP/LCK A/C/A/D/B/C/A/S

| Lv | 1 | 5 | 10 | 15 | 20 | 25 | 30 | 35 | 40 | 45 | 50 | 60 | 70 | 80 | 99 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HP | 69 | 195 | 380 | 595 | 840 | 1,115 | 1,420 | 1,755 | 2,120 | 2,515 | 2,940 | 3,880 | 4,940 | 6,120 | 8,693 |
| INS | 12 | 22 | 37 | 54 | 74 | 96 | 121 | 148 | 178 | 210 | 245 | 322 | 409 | 506 | 718 |
| STR | 13 | 16 | 20 | 24 | 27 | 31 | 35 | 39 | 42 | 46 | 50 | 57 | 65 | 72 | 87 |
| ART | 8 | 9 | 11 | 12 | 14 | 15 | 17 | 18 | 20 | 21 | 23 | 26 | 29 | 32 | 37 |
| DEF | 11 | 13 | 16 | 19 | 22 | 25 | 28 | 31 | 34 | 37 | 40 | 46 | 52 | 58 | 70 |
| RES | 9 | 11 | 13 | 15 | 18 | 20 | 22 | 24 | 27 | 29 | 31 | 36 | 40 | 45 | 53 |
| TMP | 14 | 17 | 21 | 25 | 28 | 32 | 36 | 40 | 43 | 47 | 51 | 58 | 66 | 73 | 88 |
| LCK | 14 | 18 | 22 | 27 | 31 | 36 | 40 | 45 | 49 | 54 | 58 | 67 | 76 | 85 | 99 |

**PC-11 Julien Marchetti** · joins Lv 33 · grades HP/INS/STR/ART/DEF/RES/TMP/LCK C/A/C/A/C/B/A/S

| Lv | 1 | 5 | 10 | 15 | 20 | 25 | 30 | 35 | 40 | 45 | 50 | 60 | 70 | 80 | 99 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HP | 63 | 165 | 320 | 505 | 720 | 965 | 1,240 | 1,545 | 1,880 | 2,245 | 2,640 | 3,520 | 4,520 | 5,640 | 8,099 |
| INS | 14 | 30 | 53 | 78 | 106 | 136 | 169 | 204 | 242 | 282 | 325 | 418 | 521 | 634 | 876 |
| STR | 9 | 11 | 13 | 15 | 18 | 20 | 22 | 24 | 27 | 29 | 31 | 36 | 40 | 45 | 53 |
| ART | 13 | 16 | 20 | 24 | 27 | 31 | 35 | 39 | 42 | 46 | 50 | 57 | 65 | 72 | 87 |
| DEF | 8 | 10 | 12 | 14 | 17 | 19 | 21 | 23 | 26 | 28 | 30 | 35 | 39 | 44 | 52 |
| RES | 10 | 12 | 15 | 18 | 21 | 24 | 27 | 30 | 33 | 36 | 39 | 45 | 51 | 57 | 69 |
| TMP | 13 | 16 | 20 | 24 | 27 | 31 | 35 | 39 | 42 | 46 | 50 | 57 | 65 | 72 | 87 |
| LCK | 14 | 18 | 22 | 27 | 31 | 36 | 40 | 45 | 49 | 54 | 58 | 67 | 76 | 85 | 99 |

### 7.4 What the curves say

- **Role fingerprints hold at every level.** Alkan's HP and STR lead the party from join to cap (Lv 40: 2,280 HP, 50 STR); Liszt's ART and TMP lead the casters (Lv 40: ART 50, TMP 50, a 2.1-second turn); Chopin carries the deepest INS (270 at Lv 40) and RES (49) but the thinnest body (1,584 HP after Sotto Voce); Farrenc and Min-jun share A-grade RES and LCK (41–42 each at Lv 40), the party's best status resistance and steal odds.
- **The anchor sits where it should.** The eight permanent members' mean STR curve is 11.1 + 0.56(L − 1), a little under the anchor's 12 + 0.6(L − 1): the anchor describes the members who actually Fight (BE, DE, AL average 14.0 + 0.75(L − 1)). The mean ART curve, 12.5 + 0.69(L − 1), brackets the A-grade caster anchor 13 + 0.75(L − 1).
- **Late joiners are not handicapped.** Seo-yeon and Jae-won join at Lv 40 with six-stat totals within 4% of Min-jun's at the same level (SY 208, JW 215, MJ 215); Julien joins at 33 with the S-grade LCK that his IMPROVISE reels and Blue Note crits want.

---

## 8. Opus Scores: level-up bonuses and skill learning

### 8.1 The level-up bonus ledger

Each Score carries a **bonus shape** (CANON §11c's examples: +1 ART, +2 TMP, +5% max HP). When its equipper levels up, the shape is added to that character's **Opus ledger**, which is permanent (unequipping removes nothing; Da Capo keeps it with the levels). Caps stop any one stat from running away, FF6-style, while the number of level-ups available (about 29 from CH-05 to the end of CH-16) is what really limits the total.

| Bonus shape | Added per level-up | Ledger cap per character | Effect at the cap, for a Lv-40 anchor member |
|---|---|---|---|
| +1 STR | +1 | +20 | AR 231 → 251: physical damage +8.7% |
| +1 ART | +1 | +20 | T4 spell +9.9%; status rolls +10 points |
| +1 DEF | +1 | +20 | Physical damage taken −10.8% |
| +1 RES | +1 | +20 | Magical damage taken −10.8%; enemy status rolls −10 points |
| +1 LCK | +1 | +20 | Crit +2.5 points; hit +5; steal +20; rare drop +5 |
| +2 TMP | +2 | +10 | Turns +16.4% |
| +5% max HP | +5% | +20% | 2,000 → 2,400 |
| +5% max INS | +5% | +20% | 210 → 252 |

Each Score's shape is assigned by `skills_and_progression` (it owns every OPS); where a Score carries two shapes, each counts against its own cap (a recommendation for the secret Scores is in the last section). **Every level gained applies the equipped Score's shape once**, including join-rule jumps (Berlioz and Delacroix 22 → 26 in CH-12 take four shapes; 6.3) and levels earned in reserve; a member with no Score equipped gains no shape for that level. **Order at level-up:** (1) set the new level; (2) recompute the curves; (3) add the equipped Score's shape, clipped at the cap; (4) displayed stat = curve + ledger (flat) or curve × (1 + ledger %) (HP, INS), then the hard caps; (5) current HP and INS rise by the increase in their maximums.

**Level-ups available with a Score equipped** (Scores arrive in CH-05): MJ, LU, BE, DE, AL about 29–30 by the end of CH-16; CH 28; LI 26; FA 23; JU 8; then +4 in either epilogue and +5 more for optional play to Lv 50.

### 8.2 What the ledger is worth

A **typical** Lv-41 profile spends its 29 level-ups as HP +20% (4), main attack stat +10 (10), a second stat +6 (6), TMP +6 (3) and DEF or RES +6 (6). Seo-yeon and Jae-won, who join at Lv 40 (CANON §5b), reach BOSS-31 with about 10 level-ups: HP +10%, main stat +3, a second stat +3, TMP +2, DEF +2. Re-running the section 11 simulations with those profiles:

| Fight | Mixed-play rounds: no ledger → typical ledger | Boss pressure (% party HP per round) | With the Lost Era weapons that exist at that point (ATK 165) |
|---|---|---|---|
| BOSS-26 (CH-16) | 8.8 → 8.5 | 13.2% → 9.7% | n/a: no Lost Era weapon exists before CH-E2 (the friends' are forged there from their KEY-30 keepsakes, CANON §6, §14) |
| BOSS-28 core (CH-16) | 7.4 → 6.6 | 13.6% → 10.1% | n/a: no Lost Era weapon exists before CH-E2 |
| BOSS-33 (CH-E2) | 10.3 → 9.5 | 14.4% → 10.6% | 8.9 rounds (Alkan's, Liszt's and Chopin's, forged at Pleyel's) |
| BOSS-34 (CH-E2 post-game; MJ, AL, LI, CH, Lv 50) | 30.9 → 27.3 | 19.6% → 14.6% | 24.6 rounds (Alkan's, Liszt's, Chopin's; Min-jun's comes only after BOSS-31 or BOSS-34) |
| BOSS-31 (CH-E1 optional; MJ, LU, SY, JW, Lv 50, four Lv-50 Remembrances) | 30.4 → 27.6 | 18.8% → 15.1% | 25.5 rounds (only Seo-yeon's *Hanseong*, from the busking ladder's Legend rank, and Lucile's *Pinceau Lumière* if `items_and_equipment` places it in CH-E1; Jae-won's *Sinmyeong* drops from BOSS-31 itself) |

**Reading:** the ledger buys safety (about a quarter less pressure) far more than speed (3–12% fewer rounds); Lost Era weapons buy speed, and only in the epilogues. The simulations in section 11 are run with no ledger, i.e. they are the hardest case a player meets on the critical path.

### 8.3 Opus Points and learning rates

Per-skill progress += battle OP × rate %, learned at 100% (CANON §11c). OP per battle follows 5.3. Income for a member who keeps a Score equipped from CH-05 and is in every battle open to them (in CH-09 a member of the BOSS-12 team; in CH-15 Min-jun: Party 2 in full, the other parties at the reserve share, then the merged four; 6.3):

| Chapter | CH-05 | CH-06 | CH-07 | CH-08 | CH-09 | CH-10 | CH-11 | CH-12 | CH-13 | CH-14 | CH-15 | CH-16 | CH-E1 | CH-E2 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| OP earned | 40 | 43 | 62 | 76 | 87 | 92 | 141 | 169 | 174 | 130 | 198 | 134 | 317 | 353 |
| OP per CP h | 20 | 22 | 28 | 38 | 44 | 46 | 81 | 75 | 87 | 87 | 79 | 134 | 106 | 118 |
| Cumulative | 40 | 83 | 145 | 221 | 308 | 400 | 541 | 710 | 884 | 1,014 | 1,212 | 1,346 | 1,663 | 1,699 |

CH-13 counts 51 kills and all three bosses' OP (one battle: 24 + 24 + 24); CH-E1 is 86 × 3 + BOSS-29 29 + BOSS-30 30; CH-E2 is 98 × 3 + BOSS-33 30 + the BOSS-32 duel 29. Act averages: **Act II ≈ 30 OP per CP hour, Act III ≈ 72, Act IV ≈ 92, epilogues ≈ 106 (CH-E1) to 118 (CH-E2).**

| Rate | OP to learn | Battles at 3 OP (CH-05–08) | at 6 OP (CH-09–16) | at 9 OP (epilogues) | CP hours in Act II | Act III | Act IV |
|---|---|---|---|---|---|---|---|
| ×10 | 10 | 4 | 2 | 2 | 0.33 | 0.14 | 0.11 |
| ×8 | 13 | 5 | 3 | 2 | 0.43 | 0.18 | 0.14 |
| ×6 | 17 | 6 | 3 | 2 | 0.57 | 0.24 | 0.18 |
| ×5 | 20 | 7 | 4 | 3 | 0.67 | 0.28 | 0.22 |
| ×4 | 25 | 9 | 5 | 3 | 0.83 | 0.35 | 0.27 |
| ×3 | 34 | 12 | 6 | 4 | 1.13 | 0.47 | 0.37 |
| ×2 | 50 | 17 | 9 | 6 | 1.67 | 0.69 | 0.54 |
| ×1 | 100 | 34 | 17 | 12 | 3.33 | 1.39 | 1.09 |

**Recommended rates** for `skills_and_progression` (it assigns the exact rate per skill within these): T1 attack ×10, T1 heal ×8; T2 attack ×6, heal ×5; T3 attack ×4, heal ×3; T4 attack and heal ×2; T5 ×1; low-tier buffs, debuffs and statuses (Allegro, Smoke, Lento) ×5; high-tier ones (Encore, Mirror, Fermata) ×3; field utility ×8. **Mastery cost = ⌈100 ÷ the Score's slowest rate⌉ OP**, because every skill on the equipped Score learns at once (CANON §11c: each battle's OP advances every skill by OP × its rate %). Targets: **Period Scores 25–50 OP** (slowest skill ×4–×2); **Future Scores ✦ 34–50 OP** (slowest ×3–×2); **secret Scores 100 OP** (one ×1 skill). An always-active equipper earns 1,346 OP by the end of CH-16, about 27 masteries' worth at the 50-OP upper Period target (13 at the secret 100), while each member can hold only one Score and the game has 32 in all; so the **supply of Scores**, not OP, gates the party's spell lists. Full 32-Score mastery for all eight is post-game.

### 8.4 Tier gates and power budgets

**Tier gates** pair a level with a chapter flag, so neither grinding nor a fast party can bring a tier before its CANON §10b availability chapter (the party reaches Lv 11.0 at the end of CH-04, 22.0 at the end of CH-09 and 33.0 at the end of CH-13 on the 6.2 pacing, and sooner with grinding):

| Tier | Canon availability | Earliest learn (level **and** flag) | Score rule |
|---|---|---|---|
| T1 | CH-01 | Lv 1 | — |
| T2 | CH-05 | Lv 11 **and** CH-05 started | Scores arrive in CH-05 |
| T3 | CH-10 | Lv 22 **and** CH-10 started | A Score teaching T3 is first obtainable in CH-10 |
| T4 | CH-14 | Lv 33 **and** CH-14 started | A Score teaching T4 is first obtainable in CH-14 |
| T5 | Post-game and epilogue optional content | Lv 41 (the epilogue entry level), **and only from epilogue-optional or post-game sources** | Only from epilogue-optional or post-game sources |

**Learn rule.** A level-learned skill of tier Tn is learned at the first level-up at which both the level and the chapter flag are met. A member who reached the level earlier learns it at the first battle end after the flag is set. The same gates set the **command tier** of every scaling command (`combat_ensemble` §1 table: levels 1–10 T1, 11–21 T2, 22–32 T3, 33+ T4, each capped at its canon chapter; T5 only with a learned T5 skill).

**Power budgets** (balance targets; `skills_and_progression` sets each skill's exact value inside them):

| Family | Formula | Budget |
|---|---|---|
| Fight | Physical | AR (4.1) |
| Harmony attack and heal | Magical or healing | Canon PWR tiers |
| ÉTUDE (AL) | Physical × E | E = 1.5 for a 3-input Étude, rising to 3.0 for 8 inputs; the Lv-50 Étude 3.5 |
| CANVAS (DE) | Magical, his best attack tier and his ART, dual element | Subject one ×1, row ×0.75, all ×0.5; a named rider (Stagefright, Fortissimo) costs 20% of PWR |
| PLEIN AIR (LU) | Magical, her best attack tier | IMPRESSION streak +20% per turn (canon); POINTILLÉ 8 random hits sharing one power term; IMPASTO ×1.5 single, and *Nuit étoilée* shares IMPASTO's term over 8 hits |
| RECITAL burst (MJ, Movement III) | Magical | 1.5 × his best attack tier |
| Tutti (BE) | Magical | 3-token recipe 3.0 × best tier (it costs three Cue turns); 2-token 2.0×; *Cacophony* = T1, non-elemental |
| Invocation (Opus Score) | Magical | 2 × the tier available when the Score is first obtainable; spread unless single-target |
| Cadenza | Magical PWR 180, physical ×4.0, or healing PWR 150 | A confidant's second phase adds 50% of the first (`combat_ensemble` §7) |
| Synergy | Canon PWR: Duo 160, Trio 220, Quartet 260, Octave 4 hits × 300 | Stat rule 4.5 (mean ART and level; the Octave Min-jun's); heal parts PWR 0.4 × the Synergy's, no spread penalty (`combat_ensemble` §6.4) |
| IMPROVISE (JU) | Magical | ii–V–I = best heal tier, spread; *Tritone Storm* = 2 × best tier CHRONO, spread; *Blue Note* = 1 × best tier, one random enemy |
| BEAT (JW) | Physical, 0.3 per hit, up to 8 hits | × (1 + 0.1 per perfect press), so a perfect 8-hit BEAT is ×4.3 a Fight. This outdoes Alkan's capstone Étude (11.4 parity table); a cut to 0.2 per hit (×2.9) is proposed to `combat_ensemble` in the last section and is not yet used |
| BOW (SY) | Spiccato: physical, 4 random hits × 0.4 | ×1.6 a Fight; Sostenuto = best heal tier, spread, +25% per consecutive Sostenuto turn (max +100%, `combat_ensemble` §4.6) |

At Lv 40 a magical Cadenza (PWR 180, ART 42) deals (720 + 84) × 4.9 × 100/145 = 2,717, 3.5 typical Fights and more than a Duo (2,447 at the same level) in a single turn: the payoff for fighting at ≤ 25% HP. Against a Lv-40 boss (RES 54) the same Cadenza deals 2,558, and `combat_ensemble` §7's check (ART 42.25) 2,560.

---

## 9. Gear curves (derived targets)

The canon fixes weapon ATK by tier (CANON §14, ≈ 10 + 2.2L) and the party's DEF and RES **with gear** (5 + 1.5L). Subtracting the eight permanent members' mean base curves (DEF 9.9 + 0.51(L − 1), RES 11.1 + 0.64(L − 1)) gives the armour each tier must supply. `items_and_equipment` owns every item and price; these are the targets its head and body pieces must hit on average.

| Tier | Chapters | Weapon ATK (canon) | Head + body DEF | Head + body RES | Typical relic EVA / M.EVA |
|---|---|---|---|---|---|
| Étude | CH-01–02 | 12–19 | 1–2 | 0–1 | 0 |
| Prélude | CH-03–04 | 24–32 | 3–6 | 1–3 | 0–5 |
| Nocturne | CH-05–07 | 36–45 | 8–12 | 5–8 | 5 |
| Rhapsodie | CH-08–09 | 52–56 | 15–17 | 11–13 | 5–8 |
| Concerto | CH-10–13 | 60–80 | 19–28 | 15–22 | 8 |
| Symphonie | CH-14–15 | 85–91 | 30–33 | 24–27 | 8–10 |
| Opus Magnum | CH-16, CH-E2 | 98–105 | 36–39 | 29–32 | 10 |
| Seoul modern | CH-E1 | 98–105 | 38–39 | 31–32 | 10 |
| Lost Era | — | 150–180 | — | — | — |

- **Split:** body 60%, head 40% of each target. Relics may add up to +10 DEF or RES each (CH-10 onward) without moving the mean more than 5%.
- **Spread by grade is intended.** At Lv 40 with Opus Magnum armour (36 DEF), Chopin stands at 19 + 36 = 55 and Alkan at 42 + 36 = 78 against the anchor 65; Chopin's Sotto Voce (targeted 50% less often) pays for the difference.
- **In Act I the curve runs ahead of the anchor:** Min-jun's base DEF 9 already exceeds the CH-01 anchor of 8, so the tutorial is a little gentler than the table, by design.

**Weapon class accuracy (WeaponAcc).** Items may vary ±2 per weapon.

| Class | Holder | WeaponAcc | Row-free (CANON §10b, §5a) |
|---|---|---|---|
| Batons | MJ | 95 | Yes |
| Brushes | LU | 95 | No |
| Sword-canes | BE | 95 | No |
| Rapiers | DE | 100 | No |
| Hammers | AL | 90 | No |
| Quills | CH | 98 | Yes |
| Sabres | LI | 95 | No |
| Folios | FA | 98 | Yes |
| Bows | SY | 98 | No |
| Drumsticks | JW | 95 | No |
| Canes | JU | 92 | No |

---

## 10. Enemy design rules

### 10.1 Enemy classes

The canon defines two templates, standard and boss (section 2). This doc adds three classes between and below them, so the bestiary, dungeons and bosses docs can build any foe from a level and two lookups.

| Class | HP | AR and MAR | DEF and RES | TMP | EXP and F | OP | Per formation | Used for |
|---|---|---|---|---|---|---|---|---|
| Minion | ×0.4 | ×0.8 | ×0.9 | +0 | ×0.4 | 1 | 4–6 | Rat swarms, Gaslight Wisps, static automata packs |
| Standard | ×1.0 | ×1.0 | ×1.0 | canon | ×1.0 | 1–3 (5.3) | 2–4 | The bulk of every bestiary family |
| Elite | ×2.5 | ×1.25 | ×1.1 | +3 | ×2.5 (floored) | Standard + 1 | At most 1 | Cabal "Shadow" encounters (CANON §11e), inn ambushes, dungeon veterans |
| Mini-boss | ×4.0 | ×1.5 | ×1.2 | Boss TMP | ×4.0 | 6 + ⌊Lv/4⌋ | 1 + up to 1 standard or 2 minions | Gatekeepers not listed in CANON §13. BOSS-41 "Hit" is a §13 boss and uses the boss model (10.6) |
| Boss | §13 value | Boss AR and MAR | 1.2 × standard DEF | Boss TMP | EXP ×12, F ×10 | 10–30 | — | CANON §13 only |

### 10.2 Roles (standard and elite only)

A role reshapes a foe without changing its threat. **Invariant:** HP multiplier × the larger output multiplier stays within 0.90–1.25. The two roles above 1.1 pay for it: the Brute with RES 0.8 and no real spells, the Guardian with the weakest offence in the table.

| Role | HP | AR | MAR | DEF | RES | TMP | Notes | HP × output |
|---|---|---|---|---|---|---|---|---|
| Balanced | 1.0 | 1.0 | 1.0 | 1.0 | 1.0 | +0 | Default | 1.00 |
| Brute | 1.15 | 1.05 | 0.6 | 1.1 | 0.8 | −2 | Physical only; folds to magic | 1.21 |
| Guardian | 1.5 | 0.75 | 0.75 | 1.4 | 1.2 | −2 | Covers allies below 25% HP | 1.13 |
| Striker | 0.75 | 1.35 | 0.8 | 0.9 | 0.9 | +2 | Hits 11.5–13.5% of a member's HP (±5%, 10.5 step 8); dies in 2–3 hits | 1.01 |
| Caster | 0.8 | 0.7 | 1.35 | 0.85 | 1.25 | +0 | 60% of its actions are spells | 1.08 |
| Skirmisher | 0.85 | 1.1 | 0.8 | 0.9 | 0.9 | +5 | EVA +10 (standard EVA cap 20) | 0.94 |
| Hexer | 1.0 | 0.8 | 0.9 | 1.0 | 1.1 | +0 | ART +5, status Base +10 | 0.90 |

### 10.3 Level bands

Standard and boss stats for every level the critical path uses, plus post-game levels. Std HP = 3.5 × typical physical, rounded to 10 (CANON §10e). TMP, LCK and ART follow the canon lines exactly (standard TMP 10 + 0.45L, LCK 5 + 0.5L, ART 5 + L; boss TMP 15 + 0.5L, LCK 10 + 0.6L, ART 10 + 1.5L, all rounded half up when built). The last column is 4 × typical physical: multiply it by the act's target rounds (8 / 10 / 12 / 13 / 15, 25 for a superboss's bar set) and by the party-size factor of CANON §13 to anchor any new boss. Above Lv 50 the anchor assumes weapon ATK min(10 + 2.2L, 180) and STR min(12 + 0.6(L − 1), 99), because gear plateaus at Lost Era; a boss anchor above 65,535 must be split into chained bars.

| Lv | Std HP | Std AR | Std MAR | Std DEF = RES | Std EXP | Std F | Std OP | Boss AR | Boss MAR | Boss DEF = RES | Boss EXP | Boss F | Boss OP | Boss HP per target round (4 PCs) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 120 | 7 | 8 | 4 | 2 | 1 | 1 | 13 | 15 | 5 | 24 | 10 | 10 | 138 |
| 2 | 150 | 8 | 10 | 5 | 6 | 3 | 1 | 15 | 18 | 6 | 72 | 30 | 10 | 172 |
| 3 | 190 | 10 | 11 | 6 | 10 | 5 | 1 | 18 | 21 | 7 | 120 | 50 | 10 | 213 |
| 4 | 220 | 11 | 13 | 7 | 14 | 7 | 1 | 20 | 24 | 8 | 168 | 70 | 10 | 253 |
| 5 | 260 | 13 | 15 | 8 | 19 | 9 | 1 | 23 | 27 | 10 | 228 | 90 | 10 | 290 |
| 6 | 290 | 14 | 17 | 9 | 24 | 12 | 1 | 25 | 30 | 11 | 288 | 120 | 11 | 336 |
| 7 | 340 | 16 | 19 | 10 | 29 | 14 | 1 | 28 | 33 | 12 | 348 | 140 | 11 | 384 |
| 8 | 390 | 17 | 20 | 11 | 35 | 17 | 1 | 30 | 36 | 13 | 420 | 170 | 12 | 441 |
| 9 | 430 | 19 | 22 | 12 | 41 | 20 | 1 | 33 | 39 | 14 | 492 | 200 | 12 | 495 |
| 10 | 470 | 20 | 24 | 14 | 47 | 23 | 1 | 35 | 42 | 17 | 564 | 230 | 13 | 540 |
| 11 | 530 | 22 | 26 | 15 | 54 | 26 | 1 | 38 | 45 | 18 | 648 | 260 | 13 | 598 |
| 12 | 580 | 23 | 28 | 16 | 61 | 30 | 1 | 40 | 48 | 19 | 732 | 300 | 14 | 659 |
| 13 | 640 | 25 | 29 | 17 | 68 | 33 | 1 | 43 | 51 | 20 | 816 | 330 | 14 | 730 |
| 14 | 700 | 26 | 31 | 18 | 75 | 37 | 1 | 45 | 54 | 22 | 900 | 370 | 15 | 795 |
| 15 | 750 | 28 | 33 | 19 | 83 | 41 | 1 | 48 | 57 | 23 | 996 | 410 | 15 | 855 |
| 16 | 810 | 29 | 35 | 20 | 91 | 45 | 1 | 50 | 60 | 24 | 1,092 | 450 | 16 | 925 |
| 17 | 870 | 31 | 37 | 21 | 99 | 49 | 1 | 53 | 63 | 25 | 1,188 | 490 | 16 | 997 |
| 18 | 950 | 32 | 38 | 22 | 107 | 54 | 1 | 55 | 66 | 26 | 1,284 | 540 | 17 | 1,080 |
| 19 | 1,010 | 34 | 40 | 23 | 115 | 58 | 1 | 58 | 69 | 28 | 1,380 | 580 | 17 | 1,156 |
| 20 | 1,070 | 35 | 42 | 24 | 124 | 63 | 2 | 60 | 72 | 29 | 1,488 | 630 | 18 | 1,225 |
| 21 | 1,140 | 37 | 44 | 25 | 133 | 68 | 2 | 63 | 75 | 30 | 1,596 | 680 | 18 | 1,306 |
| 22 | 1,210 | 38 | 46 | 26 | 142 | 73 | 2 | 65 | 78 | 31 | 1,704 | 730 | 19 | 1,388 |
| 23 | 1,300 | 40 | 47 | 27 | 151 | 78 | 2 | 68 | 81 | 32 | 1,812 | 780 | 19 | 1,482 |
| 24 | 1,370 | 41 | 49 | 28 | 161 | 84 | 2 | 70 | 84 | 34 | 1,932 | 840 | 20 | 1,568 |
| 25 | 1,440 | 43 | 51 | 29 | 170 | 89 | 2 | 73 | 87 | 35 | 2,040 | 890 | 20 | 1,645 |
| 26 | 1,520 | 44 | 53 | 30 | 180 | 95 | 2 | 75 | 90 | 36 | 2,160 | 950 | 21 | 1,734 |
| 27 | 1,600 | 46 | 55 | 31 | 190 | 101 | 2 | 78 | 93 | 37 | 2,280 | 1,010 | 21 | 1,825 |
| 28 | 1,690 | 47 | 56 | 32 | 200 | 107 | 2 | 80 | 96 | 38 | 2,400 | 1,070 | 22 | 1,928 |
| 29 | 1,770 | 49 | 58 | 33 | 211 | 113 | 2 | 83 | 99 | 40 | 2,532 | 1,130 | 22 | 2,023 |
| 30 | 1,830 | 50 | 60 | 35 | 221 | 120 | 2 | 85 | 102 | 42 | 2,652 | 1,200 | 23 | 2,092 |
| 31 | 1,910 | 52 | 62 | 36 | 232 | 126 | 2 | 88 | 105 | 43 | 2,784 | 1,260 | 23 | 2,188 |
| 32 | 2,000 | 53 | 64 | 37 | 243 | 133 | 2 | 90 | 108 | 44 | 2,916 | 1,330 | 24 | 2,286 |
| 33 | 2,100 | 55 | 65 | 38 | 254 | 140 | 2 | 93 | 111 | 46 | 3,048 | 1,400 | 24 | 2,398 |
| 34 | 2,190 | 56 | 67 | 39 | 265 | 147 | 2 | 95 | 114 | 47 | 3,180 | 1,470 | 25 | 2,500 |
| 35 | 2,260 | 58 | 69 | 40 | 276 | 154 | 2 | 98 | 117 | 48 | 3,312 | 1,540 | 25 | 2,590 |
| 36 | 2,360 | 59 | 71 | 41 | 288 | 162 | 2 | 100 | 120 | 49 | 3,456 | 1,620 | 26 | 2,694 |
| 37 | 2,450 | 61 | 73 | 42 | 300 | 169 | 2 | 103 | 123 | 50 | 3,600 | 1,690 | 26 | 2,799 |
| 38 | 2,560 | 62 | 74 | 43 | 311 | 177 | 2 | 105 | 126 | 52 | 3,732 | 1,770 | 27 | 2,919 |
| 39 | 2,650 | 64 | 76 | 44 | 323 | 185 | 2 | 108 | 129 | 53 | 3,876 | 1,850 | 27 | 3,027 |
| 40 | 2,730 | 65 | 78 | 45 | 336 | 193 | 3 | 110 | 132 | 54 | 4,032 | 1,930 | 28 | 3,122 |
| 41 | 2,830 | 67 | 80 | 46 | 348 | 201 | 3 | 113 | 135 | 55 | 4,176 | 2,010 | 28 | 3,233 |
| 42 | 2,930 | 68 | 82 | 47 | 360 | 210 | 3 | 115 | 138 | 56 | 4,320 | 2,100 | 29 | 3,344 |
| 43 | 3,040 | 70 | 83 | 48 | 373 | 218 | 3 | 118 | 141 | 58 | 4,476 | 2,180 | 29 | 3,471 |
| 44 | 3,140 | 71 | 85 | 49 | 386 | 227 | 3 | 120 | 144 | 59 | 4,632 | 2,270 | 30 | 3,586 |
| 45 | 3,230 | 73 | 87 | 50 | 399 | 236 | 3 | 123 | 147 | 60 | 4,788 | 2,360 | 30 | 3,686 |
| 46 | 3,330 | 74 | 89 | 51 | 412 | 245 | 3 | 125 | 150 | 61 | 4,944 | 2,450 | 30 | 3,803 |
| 47 | 3,430 | 76 | 91 | 52 | 425 | 254 | 3 | 128 | 153 | 62 | 5,100 | 2,540 | 30 | 3,920 |
| 48 | 3,550 | 77 | 92 | 53 | 438 | 264 | 3 | 130 | 156 | 64 | 5,256 | 2,640 | 30 | 4,053 |
| 49 | 3,650 | 79 | 94 | 54 | 452 | 273 | 3 | 133 | 159 | 65 | 5,424 | 2,730 | 30 | 4,173 |
| 50 | 3,720 | 80 | 96 | 56 | 465 | 283 | 3 | 135 | 162 | 67 | 5,580 | 2,830 | 30 | 4,251 |
| 55 | 4,260 | 88 | 105 | 61 | 536 | 334 | 3 | 148 | 177 | 73 | 6,432 | 3,340 | 30 | 4,866 |
| 60 | 4,820 | 95 | 114 | 66 | 609 | 390 | 3 | 160 | 192 | 79 | 7,308 | 3,900 | 30 | 5,503 |
| 70 | 5,950 | 110 | 132 | 77 | 766 | 513 | 3 | 185 | 222 | 92 | 9,192 | 5,130 | 30 | 6,802 |
| 80 | 6,980 | 125 | 150 | 87 | 936 | 653 | 3 | 210 | 252 | 104 | 11,232 | 6,530 | 30 | 7,977 |
| 90 | 7,440 | 140 | 168 | 98 | 1,117 | 810 | 3 | 235 | 282 | 118 | 13,404 | 8,100 | 30 | 8,500 |
| 99 | 7,870 | 154 | 184 | 107 | 1,289 | 965 | 3 | 258 | 309 | 128 | 15,468 | 9,650 | 30 | 8,995 |

*Lv 16 note:* 925 × 10 = 9,250 is the exact half case behind the CH-07 rounding CCR (section 1).

### 10.4 Boss rules: HP, action budget, pressure

**HP** comes only from CANON §13 (party-size rule, gauntlet ×0.75, timed ≈ ×0.8, multi-part cores carry the anchor, ±15% tolerance). This doc adds the **boss action budget A**: the average number of damaging actions the boss side takes per boss turn, counting parts and adds, with gimmick actions (bone walls, sluices, boiler ticks, row flips) free on top. Assumed action mix: 40% single-target physical, 30% single-target spell, 30% party-wide spell (×0.5 each).

| Act | A | Turn pattern | Pressure target (% of party max HP lost per round) | Simulated (section 11) |
|---|---|---|---|---|
| I | 1.0 | One action per turn | 8–16% (tiny HP pools) | 7.9–15.6% |
| II | 1.5 | Two actions every other turn | 9–12% | 9.0–11.5% (BOSS-12's three-member phase 1: 11.4%) |
| III | 2.0 | Two actions per turn | 12–16% | 12.4–15.7% |
| IV | 2.25 | Two per turn, three every fourth turn | 13–16% | 13.2–15.2% |
| Epilogues | 2.5 | Alternating two and three | 13–15% | 13.3–14.4% |
| Superbosses | 3.0 | Three per turn | 18–22% | 18.8% (BOSS-31), 19.6% (BOSS-34) |

**Per-hit ceilings:** a boss's ordinary single-target hit stays at or under 35% of an average member's max HP and a party-wide hit at or under 15% each. Bigger blows must be telegraphed and answerable: Roussel's "Steady…" (60%, interruptible by any hit of 5% of his HP), the Rheinwolf's boiler blast at pressure 100. **Survival battles (BOSS-16) are exempt from the per-hit ceilings:** Archon at Lv 45 against a Lv-29 party hits for 401 and casts for 533 (41% of 1,299), because the fight cannot be lost (11.4). *Check:* BOSS-26's physical hit is 327 (16% of 2,000) and its single spell 392 (20%).

### 10.5 How to build an enemy for any chapter

1. **Level:** the chapter's §10e anchor; a dungeon's deeper floors may go to anchor + 2, never beyond anchor + 3 for standard foes.
2. **Base row:** read 10.3.
3. **Class** (10.1), then **one role** (10.2).
4. **Affinities:** at most one weakness and one resistance for a standard foe; elites may add a null. Families set the elements (CANON §12 families; LAW-07 for Echoes).
5. **EVA and M.EVA:** 0–10 by family (canon); Skirmisher +10.
6. **Statuses:** Base from the bands in 4.9; inflict with the row's ART.
7. **Rewards:** EXP and francs from the row × class; OP from 5.3; one common and one rare steal and drop (CANON §11a).
8. **Validate:** its hit must be **(8.5–10%) × class AR multiplier × role AR multiplier** of the anchor's average max HP, ±5% (Standard Balanced 8.5–10%; Striker 11.5–13.5%; Guardian 6.4–7.5%; Caster 6.0–7.0%; Brute 8.9–10.5%; Elite Balanced 10.6–12.5%); its HP must equal 3.5 typical hits × class × role within ±10%. **A standard formation's total HP must not exceed 14 typical hits** (four standard foes), or 10.5 in Act I (three standard foes). Formations containing an elite or a mini-boss may reach 20 typical hits and count as two battles in the 6.2 kill budget.

*Example A — a CH-06 Louvre Tableau Echo built as a Striker* (Lv 15, anchor + 1). Base row: HP 750, AR 28, MAR 33, DEF/RES 19, TMP 17, LCK 13, ART 20, EXP 83, F 41, OP 1. Striker: HP 750 × 0.75 = **560**; AR 28 × 1.35 = **38**; MAR 26; DEF/RES 17; TMP 19. Against the Lv-14 party (DEF 26): 38 × 2.4 × 100/126 = **72**, 14.2% of 508 HP: inside the Striker window 11.5–13.5% ±5% (to 14.2%). The anchor party's typical 199 kills it in 2.8 hits.

*Example B — a CH-12 Grey Hand veteran built as an Elite Guardian* (Val-de-Grâce, Lv 30). Base row: HP 1,830, AR 50, MAR 60, DEF/RES 35, TMP 24, EXP 221, F 120, OP 2. Elite then Guardian: HP 1,830 × 2.5 × 1.5 = **6,860**; AR 50 × 1.25 × 0.75 = **47**; DEF 35 × 1.1 × 1.4 = **54**; RES 35 × 1.1 × 1.2 = **46**; TMP 24 + 3 − 2 = **25**; EXP 552, F 300, OP 3. Against the Lv-29 party (DEF 49): 47 × 3.9 × 100/149 = **123**, 9.7% of 1,270 HP: inside the Elite Guardian window (8.5–10%) × 1.25 × 0.75 = 8.0–9.4% ±5% (to 9.8%). The party's typical Fight against DEF 54 is 177 × 3.8 × 100/154 = 437, so it soaks 15.7 hits, about four rounds on its own: a gatekeeper worth one Duo.

### 10.6 Scaling bosses: BOSS-41 and BOSS-42

Both are CANON §13 bosses and scale to the party's average level. The §13 header puts every listed boss on the CANON §10b boss model, so both use boss AR 2.5L + 10, boss MAR 3.0L + 12, boss TMP, LCK and ART, and boss DEF/RES (1.2 × standard), and both pay boss rewards (CANON §10a): EXP ×12, F ×10, OP clamp(8 + ⌊Lv/2⌋, 10, 30). **BOSS-41 "Hit":** 4 × the chapter's standard HP (canon), BOLT-weak, FIRE-resistant. **BOSS-42 The Turnkey:** 0.6 × the chapter's boss anchor (canon), FIRE-weak.

| Chapter | Party avg Lv | BOSS-41 HP (4 × std) | BOSS-41 AR / MAR | Boss DEF = RES | Rewards (each): EXP / F / OP | BOSS-42 HP (0.6 × anchor) | BOSS-42 AR / MAR |
|---|---|---|---|---|---|---|---|
| CH-02 | 4 | 880 | 20 / 24 | 8 | 168 / 70 / 10 | 1,200 | 20 / 24 |
| CH-03 | 7 | 1,360 | 28 / 33 | 12 | 348 / 140 / 11 | 1,900 | 28 / 33 |
| CH-04 | 10 | 1,880 | 35 / 42 | 17 | 564 / 230 / 13 | 2,600 | 35 / 42 |
| CH-05 | 12 | 2,320 | 40 / 48 | 19 | 732 / 300 / 14 | 4,000 | 40 / 48 |
| CH-06 | 14 | 2,800 | 45 / 54 | 22 | 900 / 370 / 15 | 4,800 | 45 / 54 |
| CH-07 | 16 | 3,240 | 50 / 60 | 24 | 1,092 / 450 / 16 | 5,500 | 50 / 60 |
| CH-08 | 19 | 4,040 | 58 / 69 | 28 | 1,380 / 580 / 17 | 7,000 | 58 / 69 |
| CH-09 | 21 | 4,560 | 63 / 75 | 30 | 1,596 / 680 / 18 | 7,900 | 63 / 75 |
| CH-10 | 23 | 5,200 | 68 / 81 | 32 | 1,812 / 780 / 19 | 10,700 | 68 / 81 |
| CH-11 | 26 | 6,080 | 75 / 90 | 36 | 2,160 / 950 / 21 | 12,500 | 75 / 90 |
| CH-12 | 29 | 7,080 | 83 / 99 | 40 | 2,532 / 1,130 / 22 | 14,600 | 83 / 99 |
| CH-13 | 32 | 8,000 | 90 / 108 | 44 | 2,916 / 1,330 / 24 | 16,400 | 90 / 108 |
| CH-14 | 34 | 8,760 | 95 / 114 | 47 | 3,180 / 1,470 / 25 | 19,500 | 95 / 114 |

BOSS-41 is a short, sharp fight: 4 × standard HP is about a third of the chapter's boss anchor (CH-09: 4,560 of 13,100), while its boss AR hits for 16.6% of the anchor's HP (CH-09: 63 × 3.0 × 100/137 = 138 of 830). Its ×12 reward makes one Compromised-tier Hit worth about 12 standard kills; a smaller reward is filed as a CCR (last section) and is not used. Rewards are shared once per battle like any boss's; BOSS-42 pays the same table at the same level.

---

## 11. Time-to-kill simulations

### 11.1 Method

- **Party.** The members CANON §4a makes available in each chapter, at the chapter's §10e anchor level, with the curve stats of section 7, anchor weapons (10 + 2.2L) and anchor armour (section 9); 11.1b lists every simulated member's numbers. No Opus ledger (the hardest case; 8.2 gives the ledger's effect). Guests use the 7.1 template and count 0.5 in the party-size factor (CANON §13); Alkan in CH-03 is a guest on his own curves (7.1 rule 6). Seo-yeon's Sibling (+20% TMP) is left out, a small conservative error. At Lv 50 the anchor weapon is ATK 120, as the CANON §10e superboss row assumes, although shop gear tops out at 105 (CANON §14); at 105, post-game clock C runs about 3% longer.
- **A round** is `combat_ensemble` §1's round (one ATB cycle in which every living member acts once), measured at the party's mean TMP, so a faster member acts (TMP + 25)/(mean TMP + 25) times per round and a slower one less than once.
- **Three clocks for bosses.** **A (canon pace):** HP ÷ (party size × typical physical against standard DEF), the exact method behind the CANON §10e and §13 anchors; this is the row that must match the target. **B:** the same against the boss's 1.2× DEF. **C (mixed play):** each member uses their role (Fighters Fight; Delacroix's Canvas and the casters find weaknesses 40% of the time; Liszt's TRANSCEND counts ×1.5; Min-jun's Recital, Chopin's Rubato and Farrenc's Annotate count as 0.6, 0.5 and 0.8 of a spell), a healer spends enough turns to cover the boss's output at 85% efficiency, Duos fire whenever the Crescendo Gauge reaches 100, and casters whose INS runs dry (pool × 0.85 plus two Café Noir, plus two Chocolat from CH-10) fall back to Fight.
- **Boss output** follows the 10.4 action budget and mix; physical hits land 90% of the time.
- **Standard formations:** 2 foes in CH-01 and CH-03, 1 foe (or 2 minions) for Min-jun alone in CH-02, 3 afterwards; enemy actions 70% physical, 30% spells. Simulated formations are the **modal** size; pacing (6.2) uses the 12.1 weighted mean (2.35 foes in Act I, 3 afterwards).
- **Affinities.** "Weak" rows give casters and Delacroix the weakness 40% of the time. BOSS-31 and BOSS-34 "resist all but CHRONO (bar 3)" (CANON §13): bars 1–2 are modelled at normal affinity and bar 3 halves every elemental spell, Duo and Remembrance except Min-jun's CHRONO skills; Fights are non-elemental and unaffected.
- **Split fights.** BOSS-12 is run as phase 1 with Berlioz + 2 (here Delacroix and Liszt; n = 3) until 70% HP, then phase 2 with Min-jun (n = 4); 11.3 explains the trigger.

### 11.1b Simulated members

Every member the simulations field, at the level and gear used, after anchor armour (section 9: head + body DEF / RES by tier). Cells read **HP · INS · AR · ART · DEF · RES · TMP**; Chopin's HP includes Sotto Voce (×0.9); TMP is before Seo-yeon's Sibling (×1.2 while Min-jun is active: 55 at Lv 43, 61 at Lv 50). The Guest is the 7.1 template. Armour is the exact section 9 subtraction at the anchor level (party DEF or RES anchor minus the eight members' mean base, rounded half up), so it can sit up to 1 point under the section 9 tier bands, and at 0 in the Étude tier, where the curves already meet the anchor.

| Ch. | Lv | Gear (weapon ATK; armour DEF / RES) | Members |
|---|---|---|---|
| CH-01 | 2 | Étude (ATK 14; armour 0 / 0) | MJ 92 · 18 · 38 · 14 · 9 · 13 · 13; Guest (Mathurin) 92 · 16 · 41 · 14 · 11 · 12 · 13 |
| CH-02 | 4 | Étude (ATK 19; armour 0 / 0) | MJ 150 · 26 · 49 · 15 · 10 · 14 · 14; BE 162 · 23 · 53 · 13 · 14 · 10 · 11 |
| CH-03 | 7 | Prélude (ATK 25; armour 3 / 1) | MJ 244 · 39 · 63 · 18 · 15 · 18 · 16; BE 265 · 33 · 67 · 15 · 19 · 13 · 13; DE 244 · 33 · 69 · 15 · 18 · 15 · 15; AL (g) 293 · 23 · 70 · 11 · 21 · 13 · 13 |
| CH-04 | 10 | Prélude (ATK 32; armour 6 / 3) | MJ 350 · 53 · 78 · 20 · 19 · 22 · 17; BE 380 · 45 · 82 · 16 · 23 · 16 · 14; DE 350 · 45 · 85 · 16 · 22 · 18 · 16 |
| CH-05 | 12 | Nocturne (ATK 36; armour 7 / 5) | MJ 426 · 63 · 87 · 21 · 21 · 25 · 19; BE 462 · 53 · 92 · 18 · 26 · 19 · 15; DE 426 · 53 · 94 · 18 · 25 · 22 · 18; LU 390 · 63 · 87 · 22 · 18 · 23 · 23 |
| CH-06 | 14 | Nocturne (ATK 41; armour 9 / 7) | MJ 508 · 73 · 98 · 23 · 24 · 29 · 20; DE 508 · 62 · 106 · 19 · 28 · 25 · 19; LU 466 · 73 · 98 · 24 · 21 · 26 · 25; CH 382 · 83 · 93 · 25 · 20 · 33 · 23 |
| CH-07 | 16 | Nocturne (ATK 45; armour 11 / 8) | MJ 594 · 84 · 107 · 24 · 27 · 31 · 21; BE 642 · 71 · 112 · 20 · 32 · 24 · 17; DE 594 · 71 · 115 · 20 · 31 · 27 · 20; LI 546 · 84 · 110 · 29 · 27 · 28 · 29 |
| CH-08 | 19 | Rhapsodie (ATK 52; armour 15 / 11) | MJ 732 · 100 · 122 · 27 · 32 · 37 · 23; AL 865 · 57 · 135 · 16 · 42 · 28 · 18; LI 675 · 100 · 126 · 31 · 32 · 33 · 31; FA 732 · 100 · 121 · 27 · 36 · 38 · 18 |
| CH-08 (BOSS-11) | 20 | Rhapsodie (ATK 54; armour 15 / 12) | DE 780 · 90 · 136 · 22 · 37 · 33 · 22; CH 594 · 120 · 121 · 29 · 28 · 43 · 27 (MJ and LI one level above their CH-08 row) |
| CH-09 | 21 | Rhapsodie (ATK 56; armour 17 / 13) | MJ 830 · 112 · 131 · 28 · 35 · 40 · 24; BE 893 · 95 · 137 · 23 · 41 · 31 · 19; DE 830 · 95 · 141 · 23 · 40 · 35 · 23; LI 767 · 112 · 135 · 33 · 35 · 36 · 33 |
| CH-10 | 23 | Concerto (ATK 61; armour 19 / 15) | MJ 932 · 124 · 142 · 30 · 38 · 44 · 25; LU 863 · 124 · 142 · 31 · 34 · 39 · 32; LI 863 · 124 · 146 · 35 · 38 · 39 · 35; AL 1,093 · 71 · 157 · 18 · 49 · 34 · 20 |
| CH-11 | 26 | Concerto (ATK 67; armour 21 / 17) | AL 1,278 · 83 · 172 · 19 · 53 · 37 · 21; LI 1,018 · 143 · 160 · 38 · 41 · 43 · 38; FA 1,096 · 143 · 154 · 32 · 46 · 49 · 21; Guest (Mendelssohn, "Florestan") 1,096 · 122 · 161 · 28 · 46 · 43 · 27; LU solo at Lv 25 965 · 136 · 155 · 32 · 36 · 42 · 33 |
| CH-12 | 29 | Concerto (ATK 74; armour 25 / 20) | LU 1,183 · 162 · 171 · 35 · 41 · 48 · 36; MJ 1,270 · 162 · 171 · 34 · 47 · 53 · 29; DE 1,270 · 139 · 183 · 28 · 53 · 47 · 28; AL 1,473 · 96 · 188 · 21 · 59 · 42 · 23; LU solo at Lv 26 1,018 · 143 · 169 · 33 · 41 · 46 · 34 |
| CH-13 | 32 | Concerto (ATK 80; armour 27 / 22) | DE 1,454 · 157 · 197 · 30 · 57 · 51 · 30; LU 1,358 · 183 · 184 · 37 · 44 · 52 · 38; AL 1,678 · 109 · 203 · 22 · 63 · 45 · 24; CH 1,136 · 205 · 176 · 38 · 43 · 64 · 36; FA 1,454 · 183 · 183 · 36 · 56 · 58 · 24; Guest (Offenbach) 1,454 · 157 · 191 · 32 · 56 · 52 · 31 |
| CH-14 | 34 | Symphonie (ATK 85; armour 29 / 24) | MJ 1,584 · 197 · 195 · 38 · 53 · 61 · 32; BE 1,686 · 170 · 203 · 31 · 61 · 48 · 25; AL 1,822 · 119 · 215 · 23 · 67 · 48 · 25; CH 1,242 · 221 · 187 · 40 · 46 · 68 · 38 |
| CH-15 | 37 | Symphonie (ATK 91; armour 33 / 27) | MJ 1,786 · 219 · 208 · 40 · 58 · 66 · 34; LU 1,675 · 219 · 208 · 41 · 52 · 60 · 42; CH 1,408 · 245 · 200 · 42 · 51 · 73 · 40; AL 2,045 · 134 · 229 · 24 · 73 · 52 · 26; LI 1,675 · 219 · 215 · 47 · 58 · 60 · 47 |
| CH-16 | 40 | Opus Magnum (ATK 98; armour 35 / 29) | MJ 2,000 · 242 · 224 · 42 · 62 · 70 · 35; DE 2,000 · 210 · 239 · 34 · 69 · 62 · 34; AL 2,280 · 150 · 246 · 26 · 77 · 56 · 28; CH 1,584 · 270 · 215 · 44 · 54 · 78 · 42 |
| CH-16 (BOSS-28) | 41 | Opus Magnum (ATK 100; armour 37 / 30) | LU 1,951 · 250 · 228 · 44 · 57 · 65 · 45; LI 1,951 · 250 · 235 · 51 · 64 · 65 · 51 (MJ and CH one level above their CH-16 row) |
| CH-E1 | 43 | Seoul modern (ATK 105; armour 39 / 32) | MJ 2,224 · 266 · 239 · 45 · 67 · 76 · 37; LU 2,095 · 266 · 239 · 46 · 60 · 68 · 47; SY 2,095 · 266 · 238 · 45 · 67 · 68 · 46; JW 2,353 · 197 · 255 · 21 · 75 · 60 · 46 |
| CH-E2 | 43 | Opus Magnum (ATK 105; armour 39 / 32) | MJ 2,224 · 266 · 239 · 45 · 67 · 76 · 37; AL 2,525 · 167 · 263 · 27 · 84 · 60 · 29; LI 2,095 · 266 · 246 · 53 · 67 · 68 · 53; CH 1,769 · 296 · 230 · 47 · 59 · 84 · 45 |
| Post-game | 50 | Anchor ATK 120 (shop gear tops out at 105); armour 45 / 38 | MJ 2,790 · 325 · 272 · 50 · 76 · 87 · 41; AL 3,140 · 210 · 299 · 30 · 95 · 69 · 32; LI 2,640 · 325 · 280 · 59 · 76 · 78 · 59; CH 2,241 · 360 · 262 · 52 · 67 · 96 · 50; LU 2,640 · 325 · 272 · 51 · 68 · 78 · 52; SY 2,640 · 325 · 271 · 50 · 76 · 78 · 51; JW 2,940 · 245 · 290 · 23 · 85 · 69 · 51 |

### 11.2 Standard enemies, every chapter

CH-P (prologue) and CH-17 (the Window) contain no battles.

| Ch. | Party (Lv · gear) | Std enemy HP / AR / DEF | Foes | Rounds to clear: all-Fight / mixed | Enemy hit / spell | Damage taken per round (% of party HP) | HP lost per battle | Heal per battle (casts of best heal) | §10e check |
|---|---|---|---|---|---|---|---|---|---|
| CH-01 | MJ + Mathurin (g) (Lv 2 · Étude) | 150 / 8 / 5 | 2 | 3.5 / 3.4 | 8 / 10 | 15 (8.3%) | 52 (28%) | 0.7 × T1 | hit 8.7% ✓ |
| CH-02 | MJ alone; BE joins at the chapter's end (Lv 4 · Étude) | 220 / 11 / 7 | 1 (or 2 minions) | 3.7 / 3.7 | 13 / 15 | 12 (8.0%) | 44 (29%) | 0.5 × T1 | hit 8.7% ✓ |
| CH-03 | MJ, BE, DE + Alkan (g, own curves) (Lv 7 · Prélude) | 340 / 16 / 10 | 2 | 1.8 / 1.9 | 22 / 26 | 42 (4.0%) | 80 (8%) | 0.7 × T1 | hit 9.0% ✓ |
| CH-04 | MJ, BE, DE (Lv 10 · Prélude) | 470 / 20 / 14 | 3 | 3.5 / 4.0 | 32 / 38 | 92 (8.5%) | 365 (34%) | 2.4 × T1 | hit 9.1% ✓ |
| CH-05 | MJ, BE, DE, LU (Lv 12 · Nocturne) | 580 / 23 / 16 | 3 | 2.6 / 2.2 | 39 / 48 | 108 (6.3%) | 239 (14%) | 0.8 × T2 | hit 9.2% ✓ |
| CH-06 | MJ, DE, LU, CH (Lv 14 · Nocturne) | 700 / 26 / 18 | 3 | 2.6 / 2.5 | 47 / 57 | 124 (6.5%) | 305 (16%) | 0.8 × T2 | hit 9.3% ✓ |
| CH-07 | MJ, BE, DE, LI (Lv 16 · Nocturne) | 810 / 29 / 20 | 3 | 2.6 / 2.4 | 56 / 68 | 151 (6.3%) | 356 (15%) | 1.0 × T2 | hit 9.4% ✓ |
| CH-08 | MJ, AL, LI, FA (Lv 19 · Rhapsodie) | 1,010 / 34 / 23 | 3 | 2.6 / 2.3 | 71 / 84 | 192 (6.4%) | 452 (15%) | 1.1 × T2 | hit 9.7% ✓ |
| CH-09 | MJ, BE, DE, LI (Lv 21 · Rhapsodie) | 1,140 / 37 / 25 | 3 | 2.6 / 2.6 | 81 / 96 | 214 (6.4%) | 550 (17%) | 1.2 × T2 | hit 9.8% ✓ |
| CH-10 | MJ, LU, LI, AL (Lv 23 · Concerto) | 1,300 / 40 / 27 | 3 | 2.6 / 1.7 | 91 / 107 | 230 (6.1%) | 400 (11%) | 0.5 × T3 | hit 9.8% ✓ |
| CH-11 | AL, LI, FA + Mendelssohn (g) (Lv 26 · Concerto) | 1,520 / 44 / 30 | 3 | 2.6 / 2.0 | 107 / 129 | 287 (6.4%) | 573 (13%) | 0.7 × T3 | hit 9.8% ✓ |
| CH-12 | LU, MJ, DE, AL (Lv 29 · Concerto) | 1,770 / 49 / 33 | 3 | 2.6 / 2.3 | 125 / 148 | 329 (6.3%) | 742 (14%) | 0.8 × T3 | hit 9.8% ✓ |
| CH-13 | DE, LU, AL (rafters) (Lv 32 · Concerto) | 2,000 / 53 / 37 | 3 | 3.5 / 2.9 | 142 / 172 | 376 (8.4%) | 1084 (24%) | 1.0 × T3 | hit 9.8% ✓ |
| CH-14 | MJ, BE, AL, CH (Lv 34 · Symphonie) | 2,190 / 56 / 39 | 3 | 2.6 / 2.4 | 154 / 185 | 418 (6.5%) | 1002 (15%) | 0.5 × T4 | hit 9.7% ✓ |
| CH-15 | MJ, LU, CH (Party 2) (Lv 37 · Symphonie) | 2,450 / 61 / 42 | 3 | 3.5 / 2.7 | 174 / 209 | 419 (8.3%) | 1117 (22%) | 0.6 × T4 | hit 9.7% ✓ |
| CH-16 | MJ, DE, AL, CH (Lv 40 · Opus Magnum) | 2,730 / 65 / 45 | 3 | 2.6 / 2.6 | 193 / 232 | 509 (6.3%) | 1311 (16%) | 0.6 × T4 | hit 9.7% ✓ |
| CH-E1 | MJ, LU, SY, JW (Lv 43 · Seoul modern) | 3,040 / 70 / 48 | 3 | 2.6 / 2.2 | 214 / 254 | 499 (5.7%) | 1088 (12%) | 0.6 × T4 | hit 9.6% ✓ |
| CH-E2 | MJ, AL, LI, CH (Lv 43 · Opus Magnum) | 3,040 / 70 / 48 | 3 | 2.6 / 2.2 | 214 / 254 | 521 (5.9%) | 1126 (13%) | 0.5 × T4 | hit 9.6% ✓ |
| Post-game, CH-E2 branch | MJ, AL, LI, CH (Lv 50 · Opus Magnum) | 3,720 / 80 / 56 | 3 | 2.6 / 1.8 | 262 / 315 | 635 (5.7%) | 1152 (10%) | 0.4 × T4 | hit 9.4% ✓ |
| Post-game, CH-E1 branch | MJ, LU, SY, JW (Lv 50 · Seoul modern) | 3,720 / 80 / 56 | 3 | 2.6 / 1.9 | 262 / 315 | 607 (5.5%) | 1168 (11%) | 0.5 × T4 | hit 9.4% ✓ |

**Reading.** A standard formation falls in 1.7–4.0 rounds (2.6 rounds of pure Fight from CH-05 on, exactly the canon's 3.5 hits per foe). It costs the party 4–9% of its HP per round and 8–35% per battle (median 15%): about **six battles of unhealed attrition** at the median and three at worst, so a party heals about one best-tier cast per battle. The two heavier rows are deliberate: CH-04's barricade waves (a party of three facing three) and the split-party fronts of CH-13 and CH-15 (three members).

**Solo segments** (CANON §4a; `combat_ensemble` §11.8 hides Synergy and Swap). The soloist's level comes from the join rule (6.3); gear is the chapter's anchor tier.

| Segment | Soloist (Lv · gear) | Foes (anchor Lv) | Soloist's attack | Turns to clear | Enemy hit / spell on the soloist | HP lost per battle (% of max) | Notes |
|---|---|---|---|---|---|---|---|
| CH-09 cell escape | MJ (Lv 21 · Rhapsodie: HP 830, AR 131, DEF 35, RES 40) | 1 standard (1,140 HP, Lv 21) | Fight only: his injured hand is an uncurable Hush except REP-20 (`combat_ensemble` §11.8); 308 per turn after crits and misses | 4 (3.7) | 82 / 94 | 288 (35%) | Two fights leave him near 30%; the third reaches the Cadenza window. *Gaspard Unbound* on a lone target: (720 + 56) × 3.0 × 100/125 = **1,862**, enough to finish any fresh standard foe |
| CH-09 cell escape | MJ (as above) | 2 minions (460 HP each) | Fight, 313 per turn | 3 | 67 / 75 | 290 (35%) | The Cadenza tutorial needs the gauge at 100 when he is at ≤ 25% HP; a wounded soloist gains only +1 per 1% lost, so the tutorial battle must open at 100 (scripted; `bosses`) |
| CH-11 Lucile interlude | LU (Lv 25 · Concerto: HP 965, INS 136, ART 32, DEF 36, RES 42) | 1 standard (1,520 HP, Lv 26) | IMPRESSION T3, 734 then +20% a turn | 2 | 113 / 131 | 179 (19%) | 32 INS a fight; Echo rate ×0.5 (5.7) |
| CH-11 Lucile interlude | LU (as above) | 2 standard | IMPRESSION | 4 (3 under Dawn, Noon or Fog: Plein Air ×1.25) | 113 / 131 | 537 (56%); 448 (46%) with Plein Air | A two-foe formation costs half her HP: keep them rare |
| CH-12 Lucile solo | LU (Lv 26 · Concerto, Lv-29 tier: HP 1,018, INS 143, ART 33, DEF 41, RES 46) | 1 standard (1,770 HP, Lv 29) | IMPRESSION, 745 (931 with Plein Air) | 3 (2 with Plein Air) | 132 / 151 | 314 (31%); 209 (21%) with Plein Air | Plein Air needs an ambient Dawn, Noon or Fog; *Shift the Hour* costs the turn it would save, so it does not pay in a one-foe fight |
| CH-12 Lucile solo | LU (as above) | 2 minions (710 HP each) | IMPRESSION | 2 | 105 / 120 | 249 (24%) | — |
| CH-12 Lucile solo | LU (as above) | 2 standard | IMPRESSION | 4 | 132 / 151 | 732 (72%); 627 (62%) with Plein Air | Too costly: `dungeons` should field 1 standard or 2 minions in the CH-12 solo, and a 2-standard formation only beside a Lectern |

### 11.3 Story bosses, every chapter

| Ch. | Boss (Lv) | HP: core + must-kill parts | Party (Lv) | n eff | A: canon pace (target) | B: vs boss DEF | C: mixed (% of A) | Duos | Boss side per round (% of party HP) | Heal casts / round | INS spent | Verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CH-01 | BOSS-01 (Lv 4) | 520 | MJ + Mathurin (g) (Lv 2) | 1.5 | 8.1 (8) | 8.3 | 8.3 (103%) | 0 | 29 (15.6%) | 0.45 | 14 | ✓ +1% |
| CH-02 | BOSS-02 (Lv 6) | 1,100 | MJ; BE from turn 5 (Lv 4) | 2 | 8.7 (8) | 9.0 | 11.8 (135%) | 0 | 42 (13.4%) | 0.54 | 32 | ✓ +9% |
| CH-03 | BOSS-04 (Lv 9) | 2,600 | MJ, BE, DE + Alkan (g, own curves) (Lv 7) | 3.5 | 7.7 (8) | 8.0 | 7.4 (96%) | 0 | 83 (7.9%) | 0.80 | 41 | ✓ -3% |
| CH-04 | BOSS-05 (Lv 12) | 3,200 + 2,820 | MJ, BE, DE (Lv 10) | 3 | 7.9 (8) | 8.2 | 11.0 (139%) | 4 | 100 (9.2%) | 0.77 | 61 | ✓ -1% |
| CH-05 | BOSS-06 (Lv 14) | 5,600 | MJ, BE, DE, LU (Lv 12) | 4 | 8.5 (10) | 8.9 | 5.0 (59%) | 3 | 195 (11.5%) | 0.79 | 113 | ✓ -15% |
| CH-06 | BOSS-07 (Lv 16) | 7,000 | MJ, DE, LU, CH (Lv 14) | 4 | 8.8 (10) | 9.2 | 5.1 (58%) | 3 | 220 (11.5%) | 0.64 | 134 | ✓ -12% |
| CH-07 | BOSS-09 (Lv 17) | 8,000 + 2,700 | MJ, BE, DE, LI (Lv 16) | 4 | 8.7 (10) | 9.0 | 6.4 (74%) | 3 | 238 (10.0%) | 0.78 | 170 | ✓ -13% |
| CH-08 | BOSS-10 (Lv 19) | 8,500 | MJ, AL, LI, FA (Lv 19) | 4 | 7.4 (7.5) | 7.6 | 4.6 (63%) | 2 | 271 (9.0%) | 0.76 | 148 | ✓ -2% |
| CH-08 | BOSS-11 (Lv 20) | 11,000 + 6,000 | MJ, DE, CH, LI (Lv 20) | 4 | 9.0 (10) | 9.3 | 8.7 (97%) | 4 | 273 (9.3%) | 0.60 | 246 | ✓ -10% |
| CH-09 | BOSS-12 (Lv 22) | 13,000 | BE, DE, LI to 70% HP, then + MJ (Lv 21) | 3 → 4 | 11.0 (10) | 11.5 | 8.5 (77%) | 3 | 284 → 326 (11.4% → 9.8%) | 0.82 | 243 | ✓ +10% |
| CH-10 | BOSS-13 (Lv 24) | 17,800 + 4,000 | MJ, LU, LI, AL (Lv 23) | 4 | 12.0 (12) | 12.7 | 7.3 (61%) | 4 | 466 (12.4%) | 0.71 | 466 | ✓ +0% |
| CH-11 | BOSS-14 (Lv 27) | 19,000 | AL, LI, FA + Florestan (g) (Lv 26) | 3.5 | 12.5 (12) | 13.2 | 6.6 (53%) | 4 | 578 (12.9%) | 0.80 | 315 | ✓ +4% |
| CH-12 | BOSS-15 (Lv 30) | 24,000 + 6,000 | LU, MJ, DE, AL (Lv 29) | 4 | 11.9 (12) | 12.7 | 11.2 (94%) | 6 | 653 (12.6%) | 0.81 | 403 | ✓ -1% |
| CH-13 | BOSS-18 (Lv 33) | 20,000 | DE, LU, AL (rafters) (Lv 32) | 3 | 11.7 (12) | 12.4 | 10.0 (86%) | 5 | 650 (14.5%) | 0.73 | 215 | ✓ -3% |
| CH-13 | BOSS-19 (Lv 33) | 13,500 | CH, FA + Offenbach (g) (corridors) (Lv 32) | 2.5 | 9.4 (9.6) | 10.1 | 7.5 (79%) | 4 | 654 (15.7%) | 0.61 | 233 | ✓ -2% |
| CH-14 | BOSS-21 (Lv 35) | 30,000 | MJ, BE, AL, CH (Lv 34) | 4 | 12.0 (13) | 12.8 | 10.6 (88%) | 7 | 933 (14.4%) | 0.59 | 334 | ✓ -8% |
| CH-15 | BOSS-23 (Lv 37) | 27,000 | MJ, LU, CH (Party 2) (Lv 37) | 3 | 12.9 (13) | 13.6 | 9.1 (71%) | 5 | 764 (15.2%) | 0.45 | 552 | ✓ -1% |
| CH-15 | BOSS-25 (Lv 39) | 36,000 | MJ, AL, LI, CH (merged) (Lv 37) | 4 | 12.9 (13) | 13.9 | 8.0 (62%) | 5 | 1002 (14.2%) | 0.59 | 620 | ✓ -1% |
| CH-16 | BOSS-26 (Lv 40) | 30,000 | MJ, DE, AL, CH (Lv 40) | 4 | 9.6 (9.75) | 10.2 | 8.8 (92%) | 5 | 1063 (13.2%) | 0.58 | 267 | ✓ -2% |
| CH-16 | BOSS-28 (Lv 43) | 40,000 | MJ, LU, LI, CH (Lv 41) | 4 | 12.4 (13) | 13.4 | 7.4 (60%) | 5 | 1062 (13.6%) | 0.56 | 815 | ✓ -5% |
| CH-E1 | BOSS-29 (Lv 42) | 40,000 | MJ, LU, SY, JW (Lv 42) | 4 | 12.0 (15) | 12.7 | 9.8 (82%) | 6 | 1123 (13.3%) | 0.70 | 512 | ⚠ -20% |
| CH-E1 | BOSS-30 (Lv 44) | 52,000 | MJ, LU, SY, JW (Lv 43) | 4 | 15.0 (15) | 16.1 | 12.7 (85%) | 8 | 1210 (13.8%) | 0.74 | 678 | ✓ -0% |
| CH-E2 | BOSS-33 (Lv 44) | 52,000 | MJ, AL, LI, CH (Lv 43) | 4 | 15.0 (15) | 16.1 | 10.3 (69%) | 7 | 1265 (14.4%) | 0.64 | 810 | ✓ -0% |
| Post-game (CH-E2) | BOSS-34 (Lv 55) | 108,000 (3 × 36,000) | MJ, AL, LI, CH (Lv 50 · Opus Magnum) | 4 | 25.4 (25) | 28.2 | 30.9 (122%) | 25 | 2171 (19.6%) | 0.94 | 1235 | ✓ +2% |
| Optional (CH-E1) | BOSS-31 (Lv 55) | 108,000 (3 × 36,000) | MJ, LU, SY, JW + four Lv-50 Remembrances (Lv 50 · Seoul modern) | 4 | 25.4 (25) | 28.2 | 30.4 (120%) | 24 | 2075 (18.8%) | 1.09 | 1059 | ✓ +2% |

**Column notes.** *Target* is the act's round target (8 Act I, 10 Act II, 12 Act III, 13 Act IV, 15 epilogue, 25 superboss), ×0.75 for the gauntlet bosses BOSS-10 and BOSS-26 and ×0.8 for the timed BOSS-19 (CANON §13). *Verdict* compares clock A with the target; ±15% is the CANON §13 tolerance. Parts: BOSS-05's three waves, BOSS-09's gears, BOSS-11's Phantom Quartet, BOSS-13's wolves and BOSS-15's easels must die for the fight to end cleanly and are included in clock C (clock A uses the core, as the canon does). BOSS-17, BOSS-20 and BOSS-32 are duels and BOSS-16 a survival battle (11.4); BOSS-22 and BOSS-24 behave like BOSS-23 (same HP-per-member). *BOSS-12:* its 13,000 HP assumes four members (CANON §13 party-size rule), but phase 1 has only Berlioz + 2. Clock A is 11.0 (+10%) if Min-jun joins at 70% HP (the first 3,900 fall to three) and 11.6 (+16%, outside tolerance) if he joins at 50%, so `bosses` should trigger phase 2 at 70% HP or earlier. *BOSS-31 and BOSS-34* exist only in their own branches (CANON §13, §4f): BOSS-31 is fought by the Seoul party, each member calling one Remembrance per battle (`combat_ensemble` §4.3; the four strongest at Lv 50 power deal 13,826 on bars 1–2, net 10,532 after the turns they use). With Lv-55 Remembrances (busking ladder cleared) BOSS-31's clock C is 29.6, without any 32.8; if bar 3 did not resist, the two clocks would be 26.3 and 27.1.

### 11.4 Optional, special and post-game fights

**Optional CH-14 bosses** (the party is 33–35 on the critical path and up to 42 with optional play; target 13 rounds):

| Boss | Lv | HP | Clock A at party Lv 34 | at Lv 38 | at Lv 42 | Fits the target at |
|---|---|---|---|---|---|---|
| BOSS-36 Paganini's Shadow | 40 | 38,000 | 15.2 | 13.0 | 11.4 | Lv 38 |
| BOSS-37 The Lorelei Echo | 32 | 22,000 | 8.8 | 7.5 | 6.6 | CH-11 (party Lv 26: 12.7 against target 12) |
| BOSS-38 The Forge Colossus | 40 | 40,000 | 16.0 | 13.7 | 12.0 | Lv 38–40 |
| BOSS-39 The Needle Echo | 40 | 32,000 | 12.8 | 11.0 | 9.6 | Lv 34 (its HP matches the CH-14 anchor, 32,500) |
| BOSS-40 The Philosophers' Echo | 41 | 2 × 18,000 | 14.4 | 12.3 | 10.8 | Lv 36–38 |

Every optional boss lands inside 13 ± 2 rounds somewhere in the optional level range, so the order the player takes them in matters and none is out of band. BOSS-39 runs −21% against an anchor computed at its own Lv 40, but it is a missable bond-quest showcase sized to the chapter anchor; logged as a note, no change requested.

**Special fights:**

| Fight | Simulation | Verdict |
|---|---|---|
| BOSS-16 Archon: The Audience (Lv 45 against a Lv-29 party) | Stasis nulls party damage. Archon's physical hit averages 401 after misses (31% of the 1,299 average HP) and his spell 533 (41%); at A = 2 he takes 1,481 HP per round (28.5% of party HP). Without healing the "party HP < 25%" exit comes after ≈ 2.6 rounds; Defend (×0.5) and steady healing stretch it to the 6-turn exit. | Intended: an unloseable lesson in power (survival), awarding OP only |
| BOSS-27 The Stilled Hour (36,000) | Octave on Min-jun's ART and level (4.5): 3,982 per hit with his stored ART 42, so 15,928 with no confidant bonus (the canon check's 15,935 uses 42.25), 20,708 with the minimum 3 confidants (canon 20,715), 28,512 with 7 confidants and Julien's Blue Note (canon 28,524). The remaining 15,292 or 7,488 HP fall in **4.7 or 2.3 rounds** at Lv 41 (4 × 808 per round) | ✓ CANON "2–5 rounds" |
| BOSS-28 full clear (core 40,000 + manuals and pedalboard 19,000) | Clock A 18.3 rounds; mixed play ≈ 11 | Parts are optional: each one destroyed removes a gimmick |
| BOSS-30 with Remembrances (CH-E1) | One Lv-50 Liszt Remembrance (*La Clochette*, Cadenza PWR 180, ART 59) deals (720 + 118) × 5.9 × 100/159 = 3,110, about three-quarters of a round of party damage | Upside not counted in 11.3 |
| BOSS-31 Ossia (CH-E1 only, S09; 3 × 36,000, Lv 55; MJ, LU, SY, JW at Lv 50 in Seoul modern gear) | A 25.4, B 28.2, C 30.4 with four Lv-50 Remembrances (29.6 at Lv 55 power, 32.8 with none). Min-jun heals about one turn in every round (1.09 casts) because the Seoul party has no Chopin or Farrenc; bar 3 halves Lucile's styles and the Duos, so Seo-yeon's Spiccato and Jae-won's BEAT carry it. Typical ledger 27.6; with Seo-yeon's *Hanseong* (and Lucile's *Pinceau Lumière* if placed in CH-E1) 25.5 | ✓ |
| BOSS-34 The Unwritten (CH-E2 only, E03; 3 × 36,000, Lv 55; MJ, AL, LI, CH at Lv 50 in Opus Magnum) | A 25.4, B 28.2, C 30.9: the casters run dry around round 13 and bar 3's resistance turns it into an INS-management test (Chocolat, Élixirs, Inspired). Min-jun is no longer immune to Unwritten (CANON §13). Typical ledger 27.3; with Alkan's, Liszt's and Chopin's Lost Era weapons 24.6 | ✓ |
| BOSS-43 Da Capo (Lv 99, 3 × 60,000, NG+) | A Lv-99 Lost Era party (AR 459, Alkan's STR 99) deals 2,174 per Fight against its DEF 128; 180,000 HP ÷ (4 × 2,174) ≈ 21 rounds before Synergies | ✓ Within the superboss band |

**Command parity at Lv 40.** One member's best output per turn against a Lv-40 boss (DEF and RES 54), mean VAR, no crit, weakness or Light, using the 8.4 budgets; weapon ATK 98 for every member (the Seoul members at the bottom of their CH-E1 band).

| Command (member, stat) | Per use | Turns it occupies | Per turn | Notes |
|---|---|---|---|---|
| Fight (Alkan, AR 246) | 783 | 1 | 783 | The anchor's typical Fight against a boss |
| ÉTUDE, best at Lv 40 (×3.0, 8 inputs) | 2,348 | 1 | 2,348 | 2,935 Conducted (×1.25); no INS; the Lv-50 capstone (×3.5) would be 2,740 here |
| BEAT, perfect 8 hits (Jae-won, AR 238; ×4.32) | 3,271 | 1 | 3,271 | No INS; also steals; 6 Perfects 2,908; Rehearsal Mode 2,617 |
| BEAT at the proposed 0.2 per hit (×2.88) | 2,181 | 1 | 2,181 | 6 Perfects 1,939: below the Étude at Lv 40 and the capstone at Lv 50 (2,951 against 3,697) |
| Spiccato (Seo-yeon, AR 223; ×1.6) | 1,135 | 1 | 1,135 | No INS; switching from Sostenuto costs no turn |
| Tutti, 3 tokens (Berlioz, ART 34; 3.0 × T4) | 3,271 | 4 (3 Cues + Tutti) | 818, or 1,285 if the Cues are Winds or Percussion (624 each) | Cₜ INS once; riders cost 20% each |
| CANVAS, one target (Delacroix, ART 34; T4) | 1,235 | 1 | 1,235 | 1,543 under Chiaroscuro (Dusk, Night, Candle); dual element finds weaknesses |
| IMPRESSION (Lucile, ART 43; T4) | 1,292 → 2,584 | 1 | 1,809 over a 5-turn ramp | 3,230 at full streak under Plein Air |
| Harmony T4 (Liszt, ART 50) | 1,336 | 1 | 1,336; TRANSCEND 2,673 for 1.5 × INS | Bravura adds up to +50% |

**Reading.** The INS-free commands run from 1.4 Fights (Spiccato) to 3.0 (the Étude), except BEAT, which reaches 4.2 and steals besides: a three-hour Seoul member outdoes Alkan, whose whole identity is the input burst (P1). The cut to 0.2 per hit puts BEAT at 2.8 Fights, under the Étude, and is proposed to `combat_ensemble` (last section); this doc keeps 0.3 in 8.4 until that doc adopts the cut.

### 11.5 Findings

1. **Every chapter row matches the CANON §10e balance anchor table.** All 18 anchor rows reproduce exactly (one rounding CCR, CH-07), and every story boss sits within the ±15% tolerance under the canon's own clock **except BOSS-29** (12.0 rounds against a 15-round epilogue target, −20%; its 40,000 HP is 23% under the 52,100 epilogue anchor). BOSS-06 sits on the edge (−15%), as a multi-part tutorial boss should.
2. **Minimal correction for BOSS-29** (logged as a CCR): no HP change. Add one derivation rule to CANON §13: *"An epilogue's opening boss is anchored to the Act IV round target (13), because the branch party is newly formed."* Under it the Lv-42 anchor is 4 × 836 × 13 = 43,500 and BOSS-29 sits at −8%, inside tolerance.
3. **Mixed play runs at 53–122% of the canon clock** (median 80%; the two superbosses, whose bar 3 resists everything but CHRONO, are the slowest). From CH-05 on, spells run 1.7–2.0 times typical physical damage and Duos arrive every two rounds; healing and INS are the brakes. CH-02 and CH-04 run longer (135–139%) because Min-jun fights alone for four turns and the barricade adds three waves. No critical-path boss falls in under 4.6 rounds, so no boss can be skipped by burst, and parties of Fighters still meet the canon pace exactly.
4. **Healing need per boss round** is 0.45–1.09 best-tier casts: the party spends 11–27% of its turns healing (most of them the healer's), and against superbosses the healer heals almost every turn (BOSS-31's Seoul party, with Min-jun as its only real healer, more than every turn).
5. **INS is the real limiter only in long fights.** Critical-path bosses spend 14–815 INS (within the casters' pools plus two consumables); superbosses spend more than the pool and force the fallback to Fight.
6. **Split and solo segments hold.** BOSS-12 stays in tolerance only if Min-jun joins by 70% HP (11.3). The solo segments cost 19–35% of the soloist's HP per one-foe battle; two-standard formations in Lucile's solos (46–72%) are the one place where a single critical-path battle can take most of a member's HP, so 11.2 limits them.
7. **Command parity:** BEAT is the one command above its family's ceiling (parity table above).

---

## 12. Encounter rates, difficulty knobs, RNG and caps

### 12.1 Encounter rates per area type

The per-step model is in 5.7. Values are calibrated so that dungeons (about 45% of critical-path time from CH-05, 30% in Act I; CANON §10e) and overworld walking (6.2 shares) together deliver the kill rates of 6.2.

**Overworld rate tiers.** `overworld_and_towns` §3 assigns every W01 zone (Z1–Z7) and W02 zone (Y1–Y8) a tier; this doc owns the numbers behind the tiers.

| Tier | Grace G | R (per 4,096) | Mean steps | ≈ Minutes per battle (200 steps a minute) | Hunted (×1.25) | Formation sizes (weights) |
|---|---|---|---|---|---|---|
| Low | 160 | 10 | 570 | 2.9 | 488 steps, 2.4 min | 2 (40%), 3 (45%), 4 (15%) |
| Medium | 128 | 13 | 443 | 2.2 | 380 steps, 1.9 min | 2 (40%), 3 (45%), 4 (15%) |
| High | 96 | 16 | 352 | 1.8 | 301 steps, 1.5 min | 2 (40%), 3 (45%), 4 (15%) |

- **Overlays:** the War overlay (W01 from CH-14) raises every zone one tier (Low → Medium, Medium → High); the Winter overlay (CH-E2) sets Low everywhere.
- **Shadow formations:** at Watched tier and above, 1 W01 formation in 8 is replaced by a cabal "Shadow" formation: one elite Grey Hand (10.1) with two standard Grey Hand (CANON §11e). It counts as two battles in the kill budget (10.5).
- **No rolls** on bridges, on the lit boulevard spine (P10's Madeleine–Saint-Martin axis by day), aboard any vehicle (omnibus, fiacre, barge, diligence, steamboat) or aloft in *La Lumière*.
- **W03 Seoul has no rolls.** Its **static pockets** (`overworld_and_towns` §3) are visible touch encounters: each is one standard S08 formation of three static automata at the CH-E1 anchor, with standard rewards (373 EXP and ₩43,600 per automaton). They sit outside the 6.2 budget, so the map may place them freely: every five pockets cleared add about half a level at Lv 43. They vanish after BOSS-30.

**Area types.**

| Area type | Examples | Grace G | R (per 4,096) | Mean steps | Steps per minute | ≈ Minutes per battle | Formation sizes (weights) |
|---|---|---|---|---|---|---|---|
| Town, interior, salon, inn, shop | Hub maps of P03, P04, P10 (their undercroft, cellars and Passage count as mini-dungeons); P05, P19, P36; Seoul hubs | — | 0 | — | — | None | — |
| Paris and France–Rhine overworld | W01, W02 | By tier | By tier | 352–570 | 200 | 1.8–2.9 | 2 (40%), 3 (45%), 4 (15%) |
| Seoul overworld | W03 | — | 0 | — | — | Static pockets only (touch) | 3 |
| Story dungeon, Act I | P01, P08; mini-dungeons in P03, P04 | 128 | 11 | 500 | 90 | 5.6 | 1 (10%), 2 (50%), 3 (35%), 4 minions (5%) |
| Story dungeon, Act II | P13, P17, P18, P31; the P10 mini-dungeon | 144 | 11 | 516 | 90 | 5.7 | 2 (25%), 3 (50%), 4 (25%) |
| Story dungeon, Act III | R05, R08, R13, P26, P27 | 64 | 17 | 305 | 90 | 3.4 | 2 (25%), 3 (50%), 4 (25%) |
| Story dungeon, Act IV | P34, P29 | 64 | 18 | 292 | 90 | 3.2 | 2 (25%), 3 (50%), 4 (25%) |
| Story dungeon, epilogues | S08, S10, E01, E05 | 64 | 22 | 250 | 90 | 2.8 | 2 (25%), 3 (50%), 4 (25%) |
| Optional dungeon | R09, R02, R11, P38, S09, E03 | 64 | 24 | 235 | 90 | 2.6 | 3 (50%), 4 (50%) |
| Heart Chamber | P30 | — | 0 | — | — | Scripted formations only | — |
| Post-game labyrinth (Da Capo) | P29 | 48 | 28 | 194 | 90 | 2.2 | 3 (40%), 4 (60%) |

Patrols in CH-01 and the stealth sections of CH-09 (P34) and CH-12 (P26) are hazards, never battles (CANON §12); Echo zones inside them keep the dungeon rate, ×0.5 in Lucile's solo segments (5.7). `dungeons` may vary R by ±15% per dungeon and must keep the act's mean. Act I's mean is 0.1 + 1.0 + 1.05 + 0.2 = **2.35 foes** (four minions counted as four foes); Acts II–IV average 3.0; the overworld 2.75.

**Calibration against the canon targets:**

| Act | Kills per CP h (6.2) | Overworld share of CP time | Overworld battles per CP h | Overworld kill-equivalents per CP h | Dungeon kills per CP h | Dungeon foes per battle | Dungeon battles per CP h | Dungeon share | Dungeon minutes per battle | CANON §10e target |
|---|---|---|---|---|---|---|---|---|---|---|
| I | 9.4 | 3.4% | 0.82 | 1.9 | 7.5 | 2.35 | 3.2 | 30% (Act I is town-heavy) | 5.6 | ≈ 5 |
| II | 15.5 | 2.6% | 0.60 | 1.5 | 13.9 | 3.0 | 4.6 | 45% | 5.8 (the R 11 / G 144 row gives 5.7) | ≈ 5 |
| III | 26.0 | 2.9% | 0.74 | 1.9 | 24.1 | 3.0 | 8.0 | 45% | 3.4 | ≈ 3 |
| IV | 26.2 | 1.7% | 0.51 | 1.4 | 24.8 | 3.0 | 8.3 | 45% | 3.3 (the R 18 row gives 3.2) | ≈ 3 |
| CH-E1 | 28.8 | 0% | 0 | 0 | 28.8 | 3.0 | 9.6 | 45% | 2.8 | ≈ 3 |
| CH-E2 | 32.6 | 6.0% | 1.26 | 3.4 | 29.3 | 3.0 | 9.8 | 45% | 2.8 | ≈ 3 |

**Reading.** Because the overworld now supplies 5–20% of each act's kills (20% in town-heavy Act I, 5–10% afterwards), dungeons run 12–16% slower than the canon's "≈ 5 minutes" in Acts I–II and 8–13% slower than "≈ 3" in Acts III–IV; the epilogues run 7% faster. All stay inside the canon's "≈". Raising any overworld share by one point costs Act II about 0.5 dungeon kills an hour, so the shares in 6.2 are ceilings for `overworld_and_towns`, not targets.

### 12.2 Designer knobs

CANON §11j sets **one difficulty**. These are the team's tuning levers; anything inside CANON §10 is not a knob and changes only by CCR. After any change, re-run section 11: every clock-A row must stay within ±15% of its target.

| Knob | Default | Safe range | Moves | Owner |
|---|---|---|---|---|
| Encounter R and G per area and per overworld tier | 12.1 | R ±25%, G ±32 | Kills per hour, so level pacing | This doc; `dungeons` ±15% per dungeon; `overworld_and_towns` picks each zone's tier |
| Overworld time shares | 6.2 (0–6% of CP time by chapter) | Ceilings: +1 point costs Act II 0.5 dungeon kills an hour | The split between overworld and dungeon kills | This doc, `overworld_and_towns` |
| Formation size weights | 12.1 | Mean ±0.3 foes | Kills per hour, battle length | This doc, `dungeons` |
| Boss action budget A | 1.0 / 1.5 / 2.0 / 2.25 / 2.5 / 3.0 | ±0.25 | Pressure, healing share, fight length | This doc, `bosses` |
| Class multipliers | 10.1 | ±10% | Minion and elite threat | This doc, `bestiary` |
| Role multipliers | 10.2 | Keep the 0.90–1.25 invariant | Variety without threat drift | `bestiary` |
| Rare drop base / common drop | 4% / 35% | 3–6% / 25–45% | Rare economy, consumable income | This doc, `items_and_equipment` |
| Steal pity | 8th success | 6th–10th | Rare steal reliability | This doc |
| Preemptive base | 6% (Plein Air's +25 points is canon text, not a knob) | 4–8% | Opening tempo | This doc |
| Pincer / Side Attack | 2% / 2% on *open* maps | 0–4% each | Variety of openings | This doc, `combat_ensemble` (layouts) |
| Opus ledger caps | +20 stat, +10 TMP, +20% HP and INS | ±5 points, ±5% | Late-game survivability | This doc, `skills_and_progression` |

### 12.3 Player-facing options

- **ATB speed (SpeedSet 1–6)** scales every gauge equally, so action ratios and every section 11 number are unchanged; only real time changes (a Lv-21 member's turn: 3.4 s at the default, 4.9 s at SpeedSet 6).
- **Active vs Wait.** Wait (default) stops the battle clock while a command submenu or target cursor is open; Active keeps it running. In Active, a player who spends 2 seconds per command in menus hands a Lv-21 standard enemy (fill 70.4 per second) 0.55 extra turns per command: the only true "hard mode", chosen by the player.
- **Rehearsal Mode** makes every timing input perfect at ×0.8 of its result. For a player who averages 85% of perfect without it, the cost is about −6% on Études and BEAT; boss clocks move by at most +3%.
- **Retry battle** after a wipe (CANON §11a) restores HP and INS and re-seeds the battle stream (12.4), so a retry is never an identical replay.

### 12.4 RNG rules

1. **Generator:** xorshift32 in three streams. FIELD: encounter steps, formation choice, and the Preemptive, Back Attack, Pincer and Side Attack rolls. BATTLE: everything inside a battle (VAR, hit, crit, status, steal, drops, enemy AI choices, Swing, GALOP, IMPROVISE reel offsets). MINIGAME: *Phrase*, Duel Passages, busking.
2. **Seeding:** FIELD is seeded from the system clock at New Game and Da Capo and stored in every save; BATTLE is seeded from two FIELD draws at each battle start; Retry draws a fresh seed.
3. **rand(n)** is uniform over 0…n − 1 by rejection sampling (no modulo bias). Percent chances are rolled in basis points.
4. **Roll order per action:** hit, crit, VAR, status; on a defeat, rare drop, then common drop.
5. **No hidden adaptive difficulty.** Nothing rubber-bands encounter rates, damage or drops. The only memories in the system are the encounter grace (5.7) and the steal pity (5.5).
6. **Bosses:** scripted patterns are deterministic; only choices `bosses` marks as random draw from BATTLE.

### 12.5 Caps behaviour

| Quantity | Cap | Behaviour |
|---|---|---|
| Damage or healing per hit | 9,999 | Clamped after rounding; each hit of a multi-hit clamps alone. Reaching it needs a crit × Fortissimo × weakness stack at Lv 99 (CANON §10e check) |
| Minimum damage | 1 | 0 only when nulled |
| Party max HP | 9,999 | First reachable at Lv 94 through the full +20% Opus ledger (Alkan 8,350 × 1.20 = 10,020); at Lv 99 a +15% ledger suffices (9,089 × 1.15 = 10,452). The ledger moves in 5% steps |
| Party max INS | 999 | First reachable at Lv 91 (Chopin 834 × 1.20 = 1,001); at Lv 99 +10% suffices (946 × 1.10) |
| Enemy HP per bar | 65,535 | Superbosses chain bars as phases; damage beyond a bar's remaining HP is discarded and the next bar opens at the phase change. BOSS-31 and BOSS-34 (36,000 a bar) and BOSS-43 (60,000) each fit one 16-bit bar |
| STR, ART, TMP, LCK | 99 | Curves reach it at Lv 94–95; ledger points beyond the cap are kept but do nothing |
| DEF, RES | 255 | Never reached (best case ≈ 102 RES (Chopin, Lv 99) + 32 armour + 20 relics + 20 ledger = 174; DEF ≈ 87 (Alkan) + 39 + 20 + 20 = 166) |
| ATK | 255 | Never reached (Lost Era 180) |
| EVA, M.EVA | 75% | Sum of gear and relics, clamped |
| Level, EXP | 99, 1,503,792 | Excess EXP discarded, reserve members included |
| Crescendo Gauge | 300 | Excess gain discarded |
| ATB gauge | 256 | Holds at full (Tacet) |
| Stacks | Swell 5; Bravura +50%; Idée Fixe 3 | Further stacks refresh duration only |
| Money | 9,999,999 F (CANON §14) | Excess discarded. Won: see the last section |

---

## Canon Additions & Cross-Doc Notes

**Canon Change Requests** (for the Lead Designer; none is used by this doc until adopted):

- **CCR: CH-07 boss anchor rounding (CANON §10e).** 4 × 231.25 × 10 = 9,250 exactly; round half up gives **9,300**, the table prints 9,200 (half-to-even). Either amend the cell to 9,300 or annotate it. No gameplay effect: BOSS-09's 8,000 is −13% of 9,200 and −14% of 9,300, inside tolerance either way. Touches: the canon only.
- **CCR: epilogue opening-boss rule (CANON §13 derivation notes).** Add: *"An epilogue's opening boss is anchored to the Act IV round target (13), because the branch party is newly formed."* BOSS-29 (40,000) then sits at −8% of the 43,500 Lv-42 anchor instead of −23% of 52,100. Optional second sentence: *"An optional boss available in a single chapter may be anchored to that chapter's anchor"*, which documents BOSS-37 (CH-11 anchor) and BOSS-39 (CH-14 anchor, −21% against its own Lv 40). No HP changes. Touches: bosses.
- **CCR: percentage stat modifiers scale the full power term (CANON §10c Noon, §10d Out of Tune, Swell, Frenzy).** Proposal: "ART ±x%" scales the whole 4 × PWR + 2 × ART term (and status ART), "ATK ±x%" scales the whole AR. *Why:* under the literal reading now used (3.4 rule 3), ART is about 21% of a T4 spell, so the canon's percentages barely show on spells. *Worked numbers* (Liszt, Lv 40, T4 against RES 54, base 1,336): Out of Tune literal 1,257 (−6%), proposed 1,002 (−25%); Swell ×5 literal 1,496 (+12%), proposed 2,005 (+50%). Noon on Alkan (Lv 40, ATK 98, STR 50): literal AR 246 → 266 (+8%), proposed 271 (+10%). Touches: canon §10c–d, combat_ensemble §9, skills_and_progression, bestiary, bosses.
- **CCR: enemy Miasma tick capped at 999 (CANON §10d).** Proposal: on enemies a Miasma tick is min(1/16 max HP, 999). *Why:* uncapped, one status takes 6.25% of a boss bar every boss turn. *Worked numbers:* BOSS-26 (30,000 HP, about 8.8 boss turns over its mixed-play clock) loses 1,875 a tick, 16,500 in all (55% of its HP), against 8,800 (29%) capped; a BOSS-34 bar loses 2,250 a tick instead of 999. Standard foes are unaffected (the largest, Lv 50, ticks 233). Until adopted, `bosses` must carry Miasma on the immunity list of any boss it should not dominate. Touches: canon §10d, combat_ensemble §9, bosses.
- **CCR: BOSS-41 "Hit" pays EXP ×4, F ×4, OP 6 + ⌊Lv/4⌋ (CANON §13 header, §10a).** *Why:* the Hit is a Secrecy penalty that recurs once per chapter while Compromised (CANON §11e); at boss rewards it is worth about 12 standard kills and so rewards being Compromised. *Worked numbers* (CH-09, Lv 21): canon 1,596 EXP / 680 F / 18 OP each; proposed 532 / 272 / 11. Touches: canon §13, bosses, secrecy_and_trust.

**Readings of canon text** (used now because `combat_ensemble` already applies them; for the Lead Designer to confirm):

- Light States: "All physical hit −10%" (Fog), "All hit −10%" (Gloom) and "Enemy hit −10%" (Night) are ×0.9 after the clamp, floor 5%; Gloom covers status rolls on both sides and Night covers enemy status rolls (`combat_ensemble` §8.3). Smoke's "Physical hit −50%" is ×0.5 (`combat_ensemble` §9). Dusk's "Party EVA +10%" is +10 points inside the hit clamp; Night's "party crit +5%" is +500 basis points.
- Noon's "Party ATK +10%" is weapon ATK (CANON §10a defines ATK as the weapon's).
- Lucile's Plein Air "+25% preemptive chance outdoors" is +25 percentage points, maximum 40% (4.10).
- BOSS-31 and BOSS-34 "Resists all but CHRONO (bar 3)": bar 3 resists every element except CHRONO; bars 1–2 keep the affinities `bosses` gives them (11.1).

**New shared rules this doc defines** (CANON §0b: formulas are this doc's slice; listed so other docs can cite them):

- **Arithmetic** (3.2): integer stats; enemy TMP/LCK/ART rounded when built; one exact rational per hit in 64-bit integers, round half up, no intermediate rounding beyond the canon's pre-rounded quantities; basis-point rolls. Affects every balance doc.
- **Order of operations and stacking** (3.3, 3.4): one VAR roll per hit; same-source stacks add, different sources multiply; a percentage stat modifier changes only the stat it names. Affects `combat_ensemble`, `skills_and_progression`, `bestiary`, `bosses`.
- **Targeting and Synergy stats** (4.5): row ×0.75; no spread penalty on a lone target; multi-hit splits the power term (Octave excepted); Duos, Trios and Quartets use the participants' mean ART and mean level, the Octave Min-jun's ART and level; Synergies never crit. Affects `combat_ensemble`, `skills_and_progression`.
- **VAR** as 21 equal steps (4.6); **crits** in basis points, Night +500 bp, none on healing or Synergies, enemies on physical only (4.7). Affects `combat_ensemble`, `bosses`.
- **Hit**: enemy WeaponAcc 95 standard, 100 boss; Dusk adds EVA inside the clamp (4.8). Affects `bestiary`, `bosses`.
- **Status Base bands** (4.9), containing `combat_ensemble` §9's defaults; ticks resolve when the bearer's gauge fills and are uncapped (4.4). Affects `skills_and_progression`, `bestiary`, `bosses`.
- **Formation odds** (4.10): Preemptive clamp(6 + ΔLCK/4, 2, 16)% (+25 points outdoors with Lucile, max 40%), Back Attack clamp(4 − ΔLCK/8, 1, 8)%, Pincer and Side Attack 2% each on *open* maps, rolled in that order; flee ×0.5 after a Back Attack or in a Pincer, first check guaranteed in a Side Attack (5.6). Affects `combat_ensemble`, `dungeons`, `overworld_and_towns`.
- **Escape** timing details (5.6); **steal** 1/8 roll plus pity on the 8th success per ENM ID (5.5); **drops** rare clamp(4 + ΔLCK/4, 2, 16)% then common 35% (5.4). Affects `bestiary`, `items_and_equipment`, `combat_ensemble`.
- **EXP** (5.1): duels, the Rapture battle and survival battles award no EXP; **boss parts and adds pay nothing** (no EXP, francs or OP); a boss that leaves by script at an HP threshold or timer counts as defeated. Affects `bosses`, `combat_ensemble`, `salons_duels_and_economy`.
- **OP table** (5.3): standard 1 / 2 / 3 by level band, elite +1, mini-boss 6 + ⌊Lv/4⌋ (non-§13 gatekeepers only), every §13 boss clamp(8 + ⌊Lv/2⌋, 10, 30), duels at the chapter anchor; reserve 50%; Equal Measure covers EXP only. Affects `skills_and_progression`, `bestiary`, `bosses`.
- **Join rule detail** (6.3): the party average is rounded half up before the −1; the rule also fires at the start of every solo or split segment and at every regrouping (CH-09, CH-11, CH-12, CH-13, CH-15). **Split-segment rewards** (6.3): CH-09 threads and CH-15 parties pay their own members in full and every other permanent member the reserve share (`combat_ensemble` §11.8); CH-13's three fronts are one battle in which every member is active (BOSS-18 + BOSS-19 EXP, all three bosses' OP); Lucile's CH-11 and CH-12 solos pay only her. Affects `party`, `skills_and_progression`, `act2`, `act3`, `act4_and_epilogue`, `combat_ensemble`.
- **Encounter model** (5.7, 12.1): grace + per-step roll at 1/65,536 resolution; overworld tiers **Low G 160 R 10 (570 steps), Medium G 128 R 13 (443), High G 96 R 16 (352)**; War overlay +1 tier, Hunted ×1.25, 1 Shadow formation in 8 on W01 at Watched and above (one elite Grey Hand + two standard); no rolls on bridges, the lit boulevard spine, vehicles or W03; W03 static pockets are touch encounters outside the kill budget; dungeon rows by act (Act I G 128 R 11, Act II G 144 R 11, Act III G 64 R 17, Act IV G 64 R 18, epilogues G 64 R 22); overworld time shares by chapter as ceilings (6.2); relic keys `ENC_HALF` (×0.5) and `ENC_NONE` (×0) for `items_and_equipment`; calibration assumes 90 dungeon steps and 200 overworld steps per exploration minute (`art_and_ui` owns the dungeon walk speed of 1 px per frame; `overworld_and_towns` §1 the overworld speed). Affects `dungeons`, `overworld_and_towns`, `items_and_equipment`, `art_and_ui`.
- **Guest stat template** (all grade B, bases 12/13/10/11/12/11, anchor gear) for GST-01–11 only; a permanent member appearing as a guest (Alkan, CH-03) uses his own curves; the **Remembrance stat rule** (giver's Lv-50 or Lv-55 row, ATK 120 or 131, no ledger) (7.1). Affects `party`, `combat_ensemble`, `epilogues`, `prologue_and_act1`.
- **Opus ledger** (8.1): bonus shapes, per-character caps, application order; every level gained, join-rule jumps and reserve levels included, applies the equipped Score's shape once. Affects `skills_and_progression`.
- **Learning** (8.3, 8.4): learn-rate recommendations; **mastery cost = ⌈100 ÷ the slowest rate⌉ OP** (Period 25–50, Future ✦ 34–50, secret 100); **tier gates by level and chapter flag: T2 Lv 11 and CH-05 started, T3 Lv 22 and CH-10 started, T4 Lv 33 and CH-14 started, T5 Lv 41 and only from epilogue-optional or post-game sources**, with the learn rule (first qualifying level-up, or the first battle end after the flag); power budgets per command family, including the Cadenza heal (PWR 150) and Synergy heal parts (0.4 × PWR). Affects `skills_and_progression`, `combat_ensemble`, `items_and_equipment` (when Scores teaching each tier may be sold).
- **Armour DEF/RES targets per tier, relic budget, weapon-class accuracy** (9). Affects `items_and_equipment`.
- **Enemy classes** (minion, elite, mini-boss), **roles** with the threat invariant, and the **build procedure** (10.1–10.5): the hit window is (8.5–10%) × class AR × role AR multiplier ±5%; a standard formation holds at most 14 typical hits (10.5 in Act I), a formation with an elite or mini-boss at most 20 and counts as two battles. Affects `bestiary`, `dungeons`, `bosses`.
- **Boss action budget A, pressure targets and per-hit ceilings**, survival battles exempt (10.4). Affects `bosses`.
- **BOSS-41 and BOSS-42 on the CANON §10b boss model with boss rewards** (10.6). Affects `bosses`, `secrecy_and_trust`.
- **RNG streams and Retry re-seeding** (12.4). Affects `combat_ensemble`, `salons_duels_and_economy` (MINIGAME stream).

**Cross-doc notes (no CCR needed):**

- **combat_ensemble:** (1) its §9 Miasma row cites "ticks on enemies cap at 999 (formulas_and_curves §4.4)"; the cap is now a CCR only, so the row should read "no cap (CANON §10d)", and Miasma could join its default boss immunity list. (2) Its §12.2 item 1 still pays boss parts and adds X(boss Lv) × 2.5; this doc now pays them nothing (5.1). (3) **Proposal: BEAT at 0.2 per hit** (×2.9 with 8 Perfects) so that Alkan's Lv-50 Étude stays the top input burst (11.4 parity table); this doc keeps 0.3 in 8.4 until §4.6 changes. (4) Its §1 command-tier table already matches the 8.4 levels; the chapter-flag learn rule for level-learned skills is added here. (5) Its §11.8 reserve-share rule is applied as written; this doc adds that CH-13's three fronts are one battle with every member active, and that Lucile's solos pay only her (6.3). (6) The CH-09 cell escape, the Cadenza tutorial, must open with the gauge at 100: a wounded soloist reaching ≤ 25% HP has gained almost nothing (11.2).
- **overworld_and_towns:** replace "Low 320 · Medium 224 · High 160" in §3 with the tier means **570 / 443 / 352** steps (G 160 R 10, G 128 R 13, G 96 R 16); treat the 6.2 overworld time shares as ceilings when routing walking; static pockets may be placed freely (outside the kill budget; about half a level per five). Its walking speed (1 tile per 8 frames) underlies the 200-steps-a-minute calibration.
- **bosses:** trigger BOSS-12's phase 2 (Min-jun joins) at 70% HP or earlier, or clock A runs +16% (11.3); BOSS-41 and BOSS-42 use the boss model and boss rewards (10.6); list Miasma immunity wherever an uncapped tick should not dominate; the cell-escape battle opens the Crescendo at 100; confirm the bar-3 reading for BOSS-31 and BOSS-34.
- **dungeons:** use the act-by-act R and G of 12.1 (dungeon pace now 5.6–5.7 minutes a battle in Acts I–II and 3.2–3.4 in Acts III–IV); in Lucile's CH-12 solo field 1 standard foe or 2 minions, and 2 standard foes only beside a Lectern (they cost 62–72% of her HP); keep two-foe formations rare in the CH-11 interlude; respect the 10.5 formation HP caps.
- **skills_and_progression:** (1) mastery costs follow ⌈100 ÷ slowest rate⌉ (8.3); (2) level-learned skills obey the level-and-flag gates (8.4); (3) **recommendation** (moved from 8.1): give the eight secret Scores (OPS-25–32) two bonus shapes each, counted against separate caps, as the reward for finding them; (4) under the literal reading Out of Tune costs a T4 caster only about 6% of a spell (its INS ×1.5 is the real bite), unless the CCR above is adopted.
- **salons_duels_and_economy:** Act IV runs 9,591 F/h (+6.6%) because all three CH-15 Wardens pay into one purse; about 4,500 F less in CH-15's chests lands it on 9,000. **Won cap:** CANON §14 caps francs at 9,999,999 but sets no won cap; a full purse converts to ₩1,999,999,800 at ₩200 per franc. Recommend that exact figure (10 digits) as the won cap so conversion can never overflow (also for `art_and_ui`).
- **act3 / act4_and_epilogue:** where the CH-11 Lucile interlude falls sets her level (25 mid-chapter, 26 after BOSS-14); CH-15's EXP split assumes about 20% of the chapter's battles after the merge (6.2).
- **items_and_equipment:** whether Lucile's *Pinceau Lumière* can be earned in CH-E1 moves BOSS-31 by about half a round (27.6 → 27.1 with the typical ledger; Seo-yeon's *Hanseong* alone is worth one round, both together 2.1; 8.2); attach `ENC_HALF` / `ENC_NONE` to named relics.
- **epilogues and dungeons:** CH-E2's single HP story boss means about 12 more standard kills (Living Tableau battles of the Canvas Ledger) than CH-E1 to reach Lv 45 (6.2).
- **Superboss anchor and gear:** the §10e superboss row assumes weapon ATK 120, but shop gear tops out at 105 (CANON §14), which adds about 3% to post-game clock C; Lost Era weapons (150–180) take BOSS-34 from 27.3 to 24.6 rounds with the typical ledger, inside tolerance (8.2). For `bosses`, `items_and_equipment`.
- **Income check:** every act within 1% of CANON §14 except Act IV (+6.6%, above). For `salons_duels_and_economy`.
- No new IDs (ENM, ITM, HRM, OPS, MUS or SQ) are created by this doc.
