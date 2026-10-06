# Skills, Opus Sheets & Progression

Status: v1.0 — 2026-10-06 · Owns: every skill of every PC (HRM), the unique-command content (Repertoire effects, Plein Air styles, Tutti recipes TUT, Canvas recipes and Studies STU, Études ETU, reel strips, *jangdan* patterns), the Opus Score system and its full catalogue (OPS), Invocations, rank-5 Signatures and rank-10 command upgrades, menu short forms for Synergies and Cadenzas, skill pacing · Depends on: docs/05_systems/combat_ensemble.md, docs/06_balance/formulas_and_curves.md · Canon: docs/00_CANON.md

## Table of Contents

1. [Scope, Conventions and Design Intent](#1-scope-conventions-and-design-intent)
2. [How Skills Are Learned](#2-how-skills-are-learned)
3. [The Opus Score System](#3-the-opus-score-system)
4. [The Opus Score Catalogue (OPS-01–32)](#4-the-opus-score-catalogue-ops-0132)
5. [Orchestral Summons: Invocations, Tuttis, Remembrances](#5-orchestral-summons-invocations-tuttis-remembrances)
6. [The Shared Harmony Pool (HRM-PC00)](#6-the-shared-harmony-pool-hrm-pc00)
7. [PC-01 Kang Min-jun: RECITAL and CONDUCT](#7-pc-01-kang-min-jun-recital-and-conduct)
8. [PC-02 Lucile Aubray: PLEIN AIR](#8-pc-02-lucile-aubray-plein-air)
9. [PC-03 Hector Berlioz: ORCHESTRATE](#9-pc-03-hector-berlioz-orchestrate)
10. [PC-04 Eugène Delacroix: CANVAS, Sketch and the Studies](#10-pc-04-eugène-delacroix-canvas-sketch-and-the-studies)
11. [PC-05 Charles-Valentin Alkan: ÉTUDE](#11-pc-05-charles-valentin-alkan-étude)
12. [PC-06 Frédéric Chopin: RUBATO](#12-pc-06-frédéric-chopin-rubato)
13. [PC-07 Franz Liszt: TRANSCEND and MEPHISTO](#13-pc-07-franz-liszt-transcend-and-mephisto)
14. [PC-08 Louise Farrenc: COUNTERPOINT](#14-pc-08-louise-farrenc-counterpoint)
15. [PC-09 Seo-yeon, PC-10 Jae-won, PC-11 Julien](#15-pc-09-seo-yeon-pc-10-jae-won-pc-11-julien)
16. [Guests (GST-01–GST-10)](#16-guests-gst-01gst-10)
17. [Rank Rewards, Cadenzas and Synergy References](#17-rank-rewards-cadenzas-and-synergy-references)
18. [Progression Pacing and the Power Curve](#18-progression-pacing-and-the-power-curve)
19. [Canon Additions & Cross-Doc Notes](#canon-additions--cross-doc-notes)

---

## 1. Scope, Conventions and Design Intent

**Fixes:** what every party member can do and when: each Harmony skill (HRM), each command's content, each Opus Score (OPS) with what it teaches, its level-up bonus and its Invocation, and the chapter-by-chapter growth of the whole kit. **Does not fix:** command mechanics, ATB, statuses and Synergy effects (`combat_ensemble`), formulas, power budgets, OP income and the Opus ledger caps (`formulas_and_curves`), Heat per event (`secrecy_and_trust`), item prices other than the twelve Period Scores (`items_and_equipment`, `salons_duels_and_economy`).

| Design law | Consequence in this doc |
|---|---|
| **The command is the character** (CANON §1 P1) | Each member's identity lives in an innate list that no Score teaches: Min-jun's pure tones and late CHRONO, Delacroix's *Touche*, Berlioz's blade, Alkan's stances. Scores give breadth; levels and commands give a face |
| **Gift, not theft** (P2) | Only the twelve ✦ Scores carry the future. Their Invocations cost cover; the techniques a friend learns from them are the friend's own and cost nothing (§3.5) |
| **Brilliance has a price** (P3) | The Opus system always offers a quiet equal: every ✦ Invocation (Heat 3) has a Period Invocation of the same tier and PWR (Heat 0); the ✦ Score's edge is its skill list and timing, never raw power |
| **FF5 depth, FF6 warmth** | Scores are magicite (shared learning, level-up bonuses, summons); Studies are Blue Magic; Études are Blitzes; the reels are Setzer's; each is tied to a scene the player remembers |

**Notation.** Tier PWR and INS are CANON §10b: attack T1 12 / 4 INS, T2 28 / 9, T3 50 / 16, T4 80 / 28, T5 120 / 50; heal H1 10 / 5, H2 24 / 10, H3 45 / 18, H4 70 / 30. **Pₜ, Cₜ, Hₜ** are the user's command tier power, attack INS and heal power (`combat_ensemble` §1: Lv 1–10 T1, 11–21 T2, 22–32 T3, 33+ T4, each capped by its canon chapter). **Base n** is a status-inflict Base inside the `formulas_and_curves` §4.9 bands. **1/All** = spreadable (L or R toggles; ×0.5 per target). **Spreadable status skills** roll on every enemy at Base −15. **PHYS** skills use the physical formula with the user's AR and can miss unless stated. **Rider** = a status, Light or party buff added to a damaging action; each costs 20% of its power (`formulas_and_curves` §8.4). **Heat** applies only while an Onlooker remains (CANON §11e). Names fit the CANON §16h limit of 16 characters; longer canonical names keep a listed short form.

**ID formats** (CANON §0c). **HRM-PC##-##**: PC01–PC11 are a member's innate skills, numbered in learn order; **HRM-PC00-##** is the shared pool that only Scores teach (a family number this doc reserves for skills with no owner). **OPS-##**, **TUT-##**, **STU-##**, **ETU-##** as canon. A named Canvas recipe is keyed to the Study that unlocks it (its STU ID); the four story recipes carry names only.

---

## 2. How Skills Are Learned

| Source | What it gives | Who | Rule |
|---|---|---|---|
| **Level** | Innate HRMs | The owner only | At the first level-up where level **and** tier flag are met (T2 Lv 11 and CH-05; T3 Lv 22 and CH-10; T4 Lv 33 and CH-14); a member already over the level learns it at the first battle end after the flag (`formulas_and_curves` §8.4). Status, support and PHYS skills have no tier flag |
| **Opus Score** | Shared and cross-taught HRMs | Anyone equipped, except Signatures | OP × rate % per battle; learned at 100% (§3.2). A Score's own chapter gate replaces the level gate; only a T5 skill also needs Lv 41 |
| **Bond rank 5** | Signature HRM | Character-locked | CANON §11f; Signatures scale with the command tier (§17.1) |
| **Story and quest** | Named exceptions | The member named | Min-jun's CHRONO skills, Liszt's *Ecstasy*, Lucile's 별 *Byeol*, every Repertoire piece, Plein Air styles, pigments, Canvas story recipes |
| **Command content** | Études, Studies, Tutti pages | The commander | Études by Alkan's level; Studies by *Sketch*; Tutti recipes from notebook pages |
| **Bond rank 10** | Command upgrade | The member | §17.2 |

**Harmony menu order** (`combat_ensemble` §4.3 leaves the tail to this doc): the equipped Score's Invocation, the Signature, then attack skills by element in CANON §10c order (FIRE, ICE, WIND, EARTH, BOLT, WATER, LIGHT, SHADE, CHRONO, non-elemental) and by tier, then heals, revives, cures, buffs, debuffs, field skills. **System strings** (one line, no portrait, `dialogue_style_guide` §1.4 format): *Lucile learned Effet de brume!* · *Mastered: Messiah!* · *Transcribed: ✦La Mer!* · *New Tutti: Marche au supplice!* · *Study recorded: Gaslight Wisp!* · *New Étude: Carillon!*

---

## 3. The Opus Score System

CANON §11c: **32 Scores**: 12 Period (OPS-01–12), 12 Future ✦ (OPS-13–24, one-to-one with REP-17 and REP-35–45), 8 secret (OPS-25–32). Each is unique; each character equips one.

### 3.1 Equipping

| Rule | Detail |
|---|---|
| Where | The **Opus** menu (CANON §16h; layout `art_and_ui` UI-06), any time outside battle and cutscenes, including forced-party segments at Lecterns. Never in battle |
| Who | Any PC, reserve members included; guests never (CANON §6). Seo-yeon and Jae-won equip in CH-E1 from the party's stock |
| One each | A Score held by someone shows the holder's head icon; choosing it swaps it over with one confirm |
| Display | For the highlighted member: the Invocation and its Heat pips, the level-up shape, every taught skill with rate and a progress bar (✓ when known), and a ★ when that member has mastered the Score |
| Unequipped | No OP is earned and no level-up shape is applied (`formulas_and_curves` §8.1) |
| Da Capo | Scores, learned skills, Studies, Tutti recipes, Repertoire and the Opus ledger carry (LAW-23.6). Plein Air styles, pigments and rank-10 upgrades replay with the story they belong to |

### 3.2 Opus Points and learn rates

- **Income** (`formulas_and_curves` §5.3): standard 1 / 2 / 3 OP by level band, elite +1, mini-boss 6 + ⌊Lv/4⌋, any CANON §13 boss clamp(8 + ⌊Lv/2⌋, 10, 30), duels, Rapture and survival battles at the chapter anchor's boss value. Every active equipper earns the battle total; reserve equippers ⌊50%⌋ (Equal Measure covers EXP only). **Added here:** a member Swooned, Marbled or Unwritten when the battle ends earns 0 OP, as for EXP.
- **Progress** is stored **per member per skill**, not per Score: OP × rate % is added to every not-yet-known skill on the equipped Score; a skill taught by two Scores advances on whichever is equipped, at that Score's rate. Overflow past 100% is discarded.
- **Rates** follow `formulas_and_curves` §8.3, with one interpolation of mine: T1 attack ×10, H1 ×8; T2 attack ×6, H2 ×5; T3 attack ×4, H3 ×3; T4 and H4 ×2; T5 ×1; low statuses and cures (Allegro, Lento, Smoke, Cantabile, Swell, Clarity, Fortissimo) ×5; **mid statuses (Hush, Reverie, Stagefright, Delirium, Discord, Glaze, Varnish, Inspired) ×4**; high statuses (Encore, Mirror, Fermata, Marble, Coda) ×3; field utility ×8; a secret Score's exclusive skill ×1.
- **Mastery** = ⌈100 ÷ the Score's slowest rate⌉ OP: Period 25–50, ✦ 34–50, secret 100. A Score is mastered per member.

*Example.* Lucile equips OPS-03 *Requiem* in CH-06 and wins a three-foe battle (3 OP): Sepia 18%, Lullaby 12%, Glas 9%. Twelve such battles master it (34 OP); the chapter yields 43 OP (`formulas_and_curves` §8.3), so one Score per chapter in Act II is the honest pace.

### 3.3 Level-up bonus

Every Score has a **shape** from the `formulas_and_curves` §8.1 ledger: +1 STR, +1 ART, +1 DEF, +1 RES, +1 LCK, +2 TMP, +5% max HP or +5% max INS, applied once per level gained with it equipped (join-rule jumps and reserve levels included), clipped at the per-character caps (+20 to a stat, +10 TMP, +20% HP and INS). Secret Scores carry **two shapes**, each against its own cap (the `formulas_and_curves` recommendation, adopted). The 24 regular Scores split ART 4, STR 4, DEF 3, RES 3, TMP 3, HP 3, LCK 2, INS 2, so every role finds its stat by CH-08.

### 3.4 Invocations

Each Score holds one **Invocation** (an Orchestral Summon, CANON §11d): no INS, **charge 0** (it resolves on the equipper's turn), once per battle, **twice for Berlioz**, blocked by Hush, never reflected, never Transcribed (§13). Power is 2 × the tier available when the Score is first obtainable (`formulas_and_curves` §8.4): **PWR 56** for CH-05–09 Scores, **100** for CH-10–13, **160** for CH-14–15, **240** for post-game; heal Invocations **48 / 90 / 140**; spread ×0.5 unless single-target; −20% per rider. It casts with the equipper's ART and level and can crit. Full list in §5.1.

### 3.5 Future Scores ✦ and Secrecy

| Act | Secrecy | Source |
|---|---|---|
| **Transcribing** a ✦ Score at a Lectern after its story trigger | **+3** if any non-confidant is in the active party (before the Renown multiplier); 0 with confidants only | CANON §11c; `secrecy_and_trust` §2.4.1 |
| **Invoking** a ✦ Score with an Onlooker present | **Heat 3** | CANON §11c, §11e |
| Equipping, learning, levelling with a ✦ Score | 0 | — |
| **Casting a skill learned from a ✦ Score** | 0 (CHRONO skills 5, as always) | This doc: the friend learns a technique from Min-jun's page; only the summoned orchestra sounds like the future |
| Period and secret Scores | 0: **no secret Score is drawn from a future work**, so `secrecy_and_trust`'s flag is 0 for all eight (OPS-25 is Min-jun's own concerto) | This doc |
| CH-E1 | ✦ Invocations never feed the Spotlight Meter (only Lucile's painting does, CANON §11e) | — |
| CH-E2 | No Heat; every Score works; the Repertoire limit of LAW-25 binds salons only | CANON §11e |

The prompt at the Lectern reads *Transcribe ✦La Mer? (Secrecy +3)* with the candle glyph when a non-confidant is present; **Ensemble** is one button away, so a player may bench the uninitiated first. Transcriptions per chapter: CH-05 1, CH-06 1, CH-07 1, CH-08 2, CH-10 1, CH-11 1, CH-12 2, CH-13 1, CH-14 1, CH-15 1 (the cadence `secrecy_and_trust`'s sample runs assume).

### 3.6 Where Scores come from

Period Scores are sold at **Maison Farrenc** (LOC-P19, from CH-05) and **Schlesinger's** (LOC-P10, door opens CH-06), with restocks after CH-07's duel, in CH-08, on the return to Paris in CH-12 and in CH-14; nothing is sold in CH-10–11 (the party is out of Paris) or on the one night of CH-13. ✦ Scores are transcribed. Secret Scores are guaranteed boss or quest rewards. Expected holdings: **12 by CH-09, 18 by CH-12, 23 by CH-14 on the critical path (up to 29 with optional content), 24 at the finale (30 with every optional one), 31 after one superboss and 32 through Reverie of the Window**.

## 4. The Opus Score Catalogue (OPS-01–32)

Skill IDs are in §6–§15; Invocation details in §5.1. "MF" = Maison Farrenc, "Schl." = Schlesinger's. Prices are for `salons_duels_and_economy` to audit against its affordability rule (they sit below the CANON §14 relic band of their tier, because a Score is a fifth purchase on top of the kit).

### 4.1 Period Scores (OPS-01–12)

| OPS | Score | Work | Obtained | Teaches (rate) | Mastery | Level-up | Invocation | Secrecy |
|---|---|---|---|---|---|---|---|---|
| OPS-01 | Well-Tempered | J. S. Bach, *Das wohltemperierte Klavier* I (1722) | CH-05 · MF · 400 F | Lied ×8 · Ripple ×10 · Clarity ×5 · Pianissimo ×4 | 25 | +5% INS | Fugue No. 1 | 0 |
| OPS-02 | Messiah | Handel, *Messiah* (1741) | CH-05 · MF · 500 F | Lead White ×6 · Cantilena ×5 · Encore ×3 | 34 | +1 RES | Hallelujah | 0 |
| OPS-03 | Requiem | Mozart, Requiem, K. 626 (1791) | CH-06 · Schl. · 600 F | Sepia ×6 · Lullaby ×4 · Glas ×3 | 34 | +1 ART | Lacrimosa | 0 |
| OPS-04 | Eroica | Beethoven, Symphony No. 3 (1804) | CH-06 · Schl. · 700 F | Brio ×10 · Con Fuoco ×6 · Fanfare ×5 · Le Trac ×4 | 25 | +1 STR | Marcia funebre | 0 |
| OPS-05 | Pastoral | Beethoven, Symphony No. 6 (1808) | CH-07 · MF (after the duel) · 800 F | Zephyr ×6 · Engraving ×6 · Cantabile ×5 · Varnish ×4 | 25 | +5% HP | The Storm | 0 |
| OPS-06 | Orphée | Gluck, *Orphée et Eurydice*, Paris version (1774) | CH-08 · Schl. · 1,000 F | Frisson ×10 · Glaciale ×6 · Sourdine ×8 · Miroir ×3 | 34 | +1 LCK | Blessed Spirits | 0 |
| OPS-07 | Guillaume Tell | Rossini, *Guillaume Tell* (1829) | CH-08 · MF · 1,100 F | Scintilla ×10 · Sforzando ×6 · Allegro ×5 · Glaze ×4 | 25 | +2 TMP | Cavalry Charge | 0 |
| OPS-08 | Robert le diable | Meyerbeer, *Robert le diable* (1831; Schlesinger's own best-seller) | CH-12 · Schl. · 2,000 F | Lamp-Black ×4 · Sepia ×6 · Vertigo ×4 · Diabolus ×4 | 25 | +1 DEF | Nuns' Ballet | 0 |
| OPS-09 | Norma | Bellini, *Norma* (1831) | CH-12 · MF · 2,200 F | Cristallo ×4 · Mazurka ×3 · Lento ×5 · Lullaby ×4 | 34 | +1 RES | Casta diva | 0 |
| OPS-10 | The Creation | Haydn, *Die Schöpfung* (1798) | CH-14 · MF · 3,500 F | Zenith ×2 · La Crue ×2 · Resurrexit ×2 | 50 | +1 ART | Fiat Lux | 0 |
| OPS-11 | Don Giovanni | Mozart, *Don Giovanni* (1787) | CH-14 · Schl. · 3,800 F | Tutta Forza ×2 · Feroce ×4 · Statuaire ×3 | 50 | +1 STR | Commendatore | 0 |
| OPS-12 | Ninth Symphony | Beethoven, Symphony No. 9 (1824; Paris premiere by Habeneck, 1831) | CH-14 · MF · 4,200 F | Valse brillante ×2 · Encore ×3 · Clarity ×5 · Inspire ×4 | 50 | +5% HP | Ode to Joy | 0 |

### 4.2 Future Scores ✦ (OPS-13–24)

Mapping and chapters are CANON §15d. **Trigger** is the story beat after which the next Lectern offers the transcription.

| OPS | Score | Work (REP) | Trigger and Lectern | Teaches (rate) | Mastery | Level-up | Invocation | Secrecy |
|---|---|---|---|---|---|---|---|---|
| OPS-13 | Isle of the Dead | Rachmaninoff, Op. 29 (REP-17) | CH-12 · poling across the drowned quarry under the abbey (rung 6's flood) · P26 abbey Lectern | Lamp-Black ×4 · Burin ×4 · Glas ×3 | 34 | +1 DEF | Charon's Oar | +3 · Heat 3 |
| OPS-14 | L'Après-midi | Debussy, *Prélude à l'après-midi d'un faune* (REP-35) | CH-05 · the first idle afternoon on the Grand Boulevards · Hôtel de la Lyre Lectern (**the Opus tutorial**) | Zephyr ×6 · Lied ×8 · Lento ×5 · Miroir ×3 | 34 | +2 TMP | Faune | +3 · Heat 3 |
| OPS-15 | La Mer | Debussy, *La Mer* (REP-36) | CH-08 · first night aboard *La Mouette* · quay Lectern | Torrent ×6 · Ripple ×10 · Glaze ×4 · Encore ×3 | 34 | +1 ART | Wind and Sea | +3 · Heat 3 |
| OPS-16 | Daphnis et Chloé | Ravel, Suite No. 2 (REP-37) | CH-06 · dawn over the rooftops from Montmartre · Auberge des Trois Moulins Lectern | Lead White ×6 · Cantilena ×5 · Cantabile ×5 · Fermata ×3 | 34 | +5% HP | Danse générale | +3 · Heat 3 |
| OPS-17 | La Valse | Ravel, *La Valse* (REP-38) | CH-07 · the embassy ballroom after the duel · P15 anteroom Lectern | Con Fuoco ×6 · Sepia ×6 · Vertigo ×4 · Glas ×3 | 34 | +1 LCK | La Valse | +3 · Heat 3 |
| OPS-18 | Le Tombeau | Ravel, *Le Tombeau de Couperin* (REP-39) | CH-10 · the road out of Paris (each movement mourns a friend) · first W02 Lectern | Mistral ×4 · Gold Leaf ×4 · Mazurka ×3 · Clarity ×5 | 34 | +1 RES | Rigaudon | +3 · Heat 3 |
| OPS-19 | Concerto No. 2 | Rachmaninoff, Op. 18 (REP-40) | CH-11 · Mendelssohn's academy · Gasthof zum Goldenen Anker Lectern | Burin ×4 · Fulmine ×4 · Encore ×3 · Swell ×5 | 34 | +1 STR | Moderato | +3 · Heat 3 |
| OPS-20 | Symphony No. 2 | Rachmaninoff, Op. 27 (REP-41) | CH-12 · Mending 2 under Mignard's dome · P26 dome Lectern | Déluge ×4 · Mazurka ×3 · Inspire ×4 · Varnish ×4 | 34 | +5% INS | Adagio | +3 · Heat 3 |
| OPS-21 | The Bells | Rachmaninoff, Op. 35 (REP-42) | CH-14 · Notre-Dame's bells · LOC-P32 Lectern | Tempesta ×2 · Hiver ×2 · Glas ×3 · Pianissimo ×4 | 50 | +1 DEF | Sleigh-Bells | +3 · Heat 3 |
| OPS-22 | Poem of Ecstasy | Scriabin, *Le Poème de l'extase* (REP-43) | CH-13 · on the Opéra roof after the gala · *La Lumière*'s gondola Lectern | Feroce ×4 · Gold Leaf ×4 · Inspire ×4 · Miroir ×3 | 34 | +1 ART | Apothéose | +3 · Heat 3 |
| OPS-23 | Classical | Prokofiev, Symphony No. 1 (REP-44) | CH-08 · Farrenc's Haydn argument · LOC-P19 Lectern | Scintilla ×10 · Sforzando ×6 · Allegro ×5 · Retraite ×8 · Fermata ×3 | 34 | +2 TMP | Molto vivace | +3 · Heat 3 |
| OPS-24 | Scythian Suite | Prokofiev, Op. 20 (REP-45) | CH-15 · the Hanseong amalgam zones · Party 2's first P29 Lectern | Copperplate ×2 · Tramontane ×2 · Tenebrae ×2 · Le Trac ×4 | 50 | +1 STR | Sun Cortège | +3 · Heat 3 (no Onlookers in P29) |

### 4.3 Secret Scores (OPS-25–32)

Each teaches one **exclusive** skill at ×1 (mastery 100 OP) and carries two shapes. Boss rewards are guaranteed drops for `bosses.md`.

| OPS | Score | Work | Obtained | Teaches (rate) | Level-up | Invocation | Secrecy |
|---|---|---|---|---|---|---|---|
| OPS-25 | Lost Era | Kang Min-jun, *Concerto for Two Pianos "Lost Era"* (REP-27) | CH-13 · BOSS-17 cleared with **Own Voice ≥ 6** (CANON §11g); Liszt hands Min-jun the second-piano part, annotated | **Second Piano ×1** · Inspire ×4 · Encore ×3 | +1 ART & +5% INS | The Modulation | 0 (his own) |
| OPS-26 | Devin du Village | Rousseau, *Le Devin du village* (1752) | CH-14 · BOSS-40 The Philosophers' Echo (P38, missable) | **Social Contract ×1** · Clarity ×5 · Lullaby ×4 | +1 RES & +1 LCK | Le Devin | 0 |
| OPS-27 | Wellington | Beethoven, *Wellingtons Sieg*, Op. 91 (1813) | CH-14 · BOSS-38 The Forge Colossus (R02), or CH-E2 via SQ-23 | **Cannonade ×1** · Tutta Forza ×2 · Fanfare ×5 | +1 STR & +1 DEF | Vitoria | 0 |
| OPS-28 | Caprice No. 24 | Paganini, Caprice No. 24 (published 1820) | CH-14 · BOSS-36 Paganini's Shadow (BQ-PC07 climax, missable) | **Four Strings ×1** · Tempesta ×2 · Sforzando ×6 · Allegro ×5 | +2 TMP & +1 ART | Caprice | 0 |
| OPS-29 | Oberon | Weber, *Oberon* (1826; the mermaids' song) | CH-11 or CH-14 · BOSS-37 The Lorelei Echo (R09) | **Fairy Horn ×1** · Déluge ×4 · Torrent ×6 · Lullaby ×4 | +1 RES & +5% HP | Mermaids' Song | 0 |
| OPS-30 | Barricades | F. Couperin, *Les Barricades mystérieuses* (1717) | CH-14 · BQ-PC08 finale: the first edition Farrenc saves from Delorme's raid on Pleyel's archive | **Rempart ×1** · Marginalia ×5 · Tempo Giusto ×5 | +1 DEF & +1 RES | Les Barricades | 0 |
| OPS-31 | Art of Fugue | J. S. Bach, *Die Kunst der Fuge* (1751; its last fugue breaks off) | CH-E1 · BOSS-31 Ossia (S09); other branch via Reverie | **Contrapunctus ×1** · Resurrexit ×2 · Tenebrae ×2 | +1 ART & +1 LCK | Last Fugue | 0 |
| OPS-32 | Unfinished | Schubert, Symphony in B minor, D. 759 (1822; unheard until 1865) | CH-E2 · BOSS-34 The Unwritten (E03); other branch via Reverie | **Unfinished ×1** · Tempus ×2 · Valse brillante ×2 | +5% HP & +5% INS | B Minor | 0 (CHRONO, but CH-E2 has no Heat) |

The two post-game Scores are works their composers left unfinished, given by the two faces of the history that did not happen (LAW-27), to a man whose wound is that he never finished anything (CANON §5f). Both branches end with Min-jun finishing *Harmonies*.

## 5. Orchestral Summons: Invocations, Tuttis, Remembrances

CANON §11d names three families. All three ignore row and Mirror and cost no Crescendo.

### 5.1 Invocations (one per Score)

Charge 0, once per battle (Berlioz twice), no INS (§3.4). PWR already includes the −20% per rider.

| OPS | Invocation | PWR | Element | Target | Rider | Heat |
|---|---|---|---|---|---|---|
| 01 | Fugue No. 1 | 56 | — | 4 hits on random enemies, no spread penalty | — | 0 |
| 02 | Hallelujah | 45 | LIGHT | All | Party Cantabile | 0 |
| 03 | Lacrimosa | 56 | SHADE | All | — | 0 |
| 04 | Marcia funebre | 56 | EARTH | One | — | 0 |
| 05 | The Storm | 56 | BOLT + WIND | All | — | 0 |
| 06 | Blessed Spirits | heal 48 | — | Party | — | 0 |
| 07 | Cavalry Charge | 45 | — | All | Party Allegro | 0 |
| 08 | Nuns' Ballet | 80 | SHADE | All | Reverie (base 45) | 0 |
| 09 | Casta diva | 80 | ICE | All | Sets Night | 0 |
| 10 | Fiat Lux | 160 | LIGHT | All | — | 0 |
| 11 | Commendatore | 128 | FIRE + SHADE | One | Marble (base 30) | 0 |
| 12 | Ode to Joy | heal 112 | — | Party | Party Cantabile | 0 |
| 13 | Charon's Oar | 100 | SHADE | All | — | 3 |
| 14 | Faune | 45 | WIND | All | Reverie (base 40) | 3 |
| 15 | Wind and Sea | 56 | WATER + WIND | All | — | 3 |
| 16 | Danse générale | 56 | LIGHT + WIND | All | — | 3 |
| 17 | La Valse | 45 | SHADE + FIRE | All | Delirium (base 45) | 3 |
| 18 | Rigaudon | 80 | WIND | All | Party Allegro | 3 |
| 19 | Moderato | 100 | EARTH | One | — | 3 |
| 20 | Adagio | heal 90 | — | Party | — | 3 |
| 21 | Sleigh-Bells | 160 | ICE + BOLT | All | — | 3 |
| 22 | Apothéose | 100 | FIRE + LIGHT | All | — | 3 |
| 23 | Molto vivace | 45 | BOLT | One | Party Allegro | 3 |
| 24 | Sun Cortège | 160 | LIGHT + EARTH | All | — | 3 |
| 25 | The Modulation | — | — | Both sides | Party cleanse and Allegro; Lento (base 60) on all enemies | 0 |
| 26 | Le Devin | — | — | Both sides | Scans every enemy (as Marginalia); party Cantabile | 0 |
| 27 | Vitoria | 160 | FIRE + EARTH | All | — | 0 |
| 28 | Caprice | 160 | BOLT | One | — | 0 |
| 29 | Mermaids' Song | 80 | WATER | All | Reverie (base 40) | 0 |
| 30 | Les Barricades | — | — | Party | Bulwark (4 turns) | 0 |
| 31 | Last Fugue | 240 | — | All | — | 0 |
| 32 | B Minor | 240 | CHRONO | All | — | 5 (moot in CH-E2) |

*Check.* *Faune* in CH-05 (Min-jun, Lv 12, ART 21) against standard RES 16: (180 + 42) × 2.1 × 100/116 = 402, ×0.5 = **201 per enemy** plus a Reverie roll, free, once: a third of a standard foe each, which is why it is worth its Heat. *Fiat Lux* in CH-14 (Lucile, Lv 34, ART 39) against RES 39: (640 + 78) × 4.3 × 100/139 = 2,221, ×0.5 = **1,111 per enemy**, half a standard foe in a free action.

### 5.2 Tutti recipes (TUT-01–20)

Berlioz's **Cue** tokens (Strings S, Winds W, Brass B, Percussion P, Chorus C; max 3; immediate effects in `combat_ensemble` §4.6) are spent by **Tutti** (Cₜ INS). **Charge** = the Cue turns the recipe needs. Budget (`formulas_and_curves` §8.4): 1 token Pₜ (or Hₜ), 2 tokens ×2.0, 3 tokens ×3.0; all-target ×0.5; −20% per rider. Unknown combinations play *Cacophony* (one random enemy, non-elemental, PWR 12). Names are Berlioz's works to 1833 (CANON §15e).

| TUT | Tokens | Recipe (short form) | Power | Element | Target | Rider | Page found |
|---|---|---|---|---|---|---|---|
| TUT-01 | S | *Rêveries* | 1.0 Hₜ | — | Party heal | — | Known at join (end CH-02) |
| TUT-02 | W | *Scène aux champs* | 1.0 Pₜ | WIND | One | — | Known at join |
| TUT-03 | B | *Rob Roy* | 1.0 Pₜ | FIRE | One | — | Known at join |
| TUT-04 | P | *Les Francs-juges* | 0.8 Pₜ | EARTH | One | Stun (base 30) | CH-03 · Conservatoire undercroft, after BOSS-04 |
| TUT-05 | C | *Chant de bonheur* | — | — | Party | Cantabile | CH-04 · Alkan family house, after the barricade |
| TUT-06 | S S | *Un bal* | 1.6 Hₜ | — | Party heal | Party Allegro | CH-05 · Pleyel's salle: Marie Moke-Pleyel returns his old pages |
| TUT-07 | W W | *La harpe éolienne* (Harpe éolienne) | 2.0 Pₜ | WIND | All | — | CH-05 · Passage de l'Opéra Echo nest |
| TUT-08 | B B | *Waverley* | 2.0 Pₜ | FIRE | One | — | CH-06 · Louvre copyists' gallery |
| TUT-09 | P P | *Le roi Lear* | 2.0 Pₜ | BOLT | All | — | CH-07 · Clockwork Undercroft |
| TUT-10 | C C | *Le Ballet des ombres* (Ballet d'ombres) | 1.6 Pₜ | SHADE | All | Smoke (base 60) | CH-08 · Sewers of Palais-Royal |
| TUT-11 | S W | *Concert de sylphes* (Sylphes) | 1.6 Pₜ | WIND | All | Reverie (base 50) | CH-08 · backstage, Salle Pleyel, Sat 21 Sep |
| TUT-12 | B P | *Chanson de brigands* (Brigands) | 1.6 Pₜ | EARTH + FIRE | One | Stagefright (base 45) | CH-09 · Bercy, after BOSS-12 (he led the rescue) |
| TUT-13 | S C | *Méditation religieuse* (Méditation) | — | — | Party | Revives every Swooned ally at 25%; if none, heal 2.0 Hₜ | CH-12 · Val-de-Grâce chapel |
| TUT-14 | W C | *Irlande* | — | — | Party | Glaze | CH-12 · on rejoining: Harriet's letter carries the Irish melodies |
| TUT-15 | W B | *Herminie* | 1.6 Pₜ | LIGHT | One | Berlioz gains 3 Idée Fixe stacks | CH-14 · his 30th birthday, Wed 11 Dec |
| TUT-16 | B B P | *Marche au supplice* (Marche supplice) | 3.0 Pₜ | EARTH + FIRE | One | — | BQ-PC03 step 1 (by CH-06) |
| TUT-17 | B P C | *Songe d'une nuit du sabbat* (Sabbat) | 3.0 Pₜ | SHADE + FIRE | All | — | BQ-PC03 step at the wedding, Thu 3 Oct (CH-09): Harriet's gift |
| TUT-18 | S S W | *La mort d'Orphée* | 2.4 Pₜ | LIGHT | All | Party Cantabile | CH-12 · abbey quarries |
| TUT-19 | W W S | *Fantaisie sur la Tempête* (La Tempête) | 3.0 Pₜ | WATER + WIND | All | — | BQ-PC03 finale (CH-14) |
| TUT-20 | C C B | *La mort de Cléopâtre* (Cléopâtre) | 2.4 Pₜ | SHADE | One | Coda (base 35) | CH-14 · Philosophers' Tombs (P38, optional) |

*Herminie* (1828) carries the melody that became the *idée fixe*; its rider loads his passive. SYN-14 fires *Songe d'une nuit du sabbat* whether or not TUT-17 is known; SYN-04 replays whatever recipe fired last. Recipes known: 3 at join, 5 by CH-04, 9 by CH-06, 14 by CH-09, 17 by CH-12, 20 by CH-14 (none in CH-10–11: he is newly married, CANON §5a).

### 5.3 Remembrances (CH-E1 only)

Each CH-17 keepsake (KEY-30) received becomes one line under the Invocation: charge 0, once per battle per keepsake, one per Seoul member per battle; it casts the giver's Cadenza (`combat_ensemble` §7) on the giver's Lv-50 row, ATK 120, no ledger (Lv 55, ATK 131 once the busking ladder is cleared; CANON §6, `formulas_and_curves` §7.1), with the second phase if the giver was a confidant.

| Keepsake | Giver | Casts | Element |
|---|---|---|---|
| Score page | Chopin | *Warszawa* | Heal |
| Glove | Liszt | *La Clochette* | BOLT |
| Baton | Berlioz | *Dies irae* | SHADE + EARTH |
| Sketch | Delacroix | *La Liberté guidant* | FIRE + WIND |
| Engraved plate | Farrenc | *Grand Tirage* | EARTH, WATER, LIGHT |
| Clef tuning fork | Alkan | *La Machine* | EARTH |
| Cassette (if recruited) | Julien | *Changes* | As result |

## 6. The Shared Harmony Pool (HRM-PC00)

Skills no one learns by level: only Scores teach them, and anyone may learn them. HRM-PC00-24–31 are the secret Scores' exclusives.

| ID | Skill | INS | Power | Element | Target | Effect | Taught by (rate) |
|---|---|---|---|---|---|---|---|
| HRM-PC00-01 | Brio | 4 | T1 · 12 | FIRE | 1/All | — | OPS-04 ×10 |
| HRM-PC00-02 | Frisson | 4 | T1 · 12 | ICE | 1/All | — | OPS-06 ×10 |
| HRM-PC00-03 | Scintilla | 4 | T1 · 12 | BOLT | 1/All | — | OPS-07 ×10, OPS-23 ×10 |
| HRM-PC00-04 | Ripple | 4 | T1 · 12 | WATER | 1/All | — | OPS-01 ×10, OPS-15 ×10 |
| HRM-PC00-05 | Lied | 5 | H1 · 10 | — | 1/All ally | Heal | OPS-01 ×8, OPS-14 ×8 |
| HRM-PC00-06 | Torrent | 9 | T2 · 28 | WATER | 1/All | — | OPS-15 ×6, OPS-29 ×6 |
| HRM-PC00-07 | Zephyr | 9 | T2 · 28 | WIND | 1/All | — | OPS-05 ×6, OPS-14 ×6 |
| HRM-PC00-08 | Sepia | 9 | T2 · 28 | SHADE | 1/All | — | OPS-03 ×6, OPS-08 ×6, OPS-17 ×6 |
| HRM-PC00-09 | Déluge | 16 | T3 · 50 | WATER | 1/All | — | OPS-20 ×4, OPS-29 ×4 |
| HRM-PC00-10 | Mistral | 16 | T3 · 50 | WIND | 1/All | — | OPS-18 ×4 |
| HRM-PC00-11 | Lamp-Black | 16 | T3 · 50 | SHADE | 1/All | — | OPS-08 ×4, OPS-13 ×4 |
| HRM-PC00-12 | La Crue | 28 | T4 · 80 | WATER | 1/All | The Seine in flood | OPS-10 ×2 |
| HRM-PC00-13 | Tramontane | 28 | T4 · 80 | WIND | 1/All | — | OPS-24 ×2 |
| HRM-PC00-14 | Tenebrae | 28 | T4 · 80 | SHADE | 1/All | — | OPS-24 ×2, OPS-31 ×2 |
| HRM-PC00-15 | Lullaby | 8 | — | — | 1/All enemy | Reverie, base 45 | OPS-03 ×4, OPS-09 ×4, OPS-26 ×4, OPS-29 ×4 |
| HRM-PC00-16 | Le Trac | 8 | — | — | One enemy | Stagefright, base 45 ("stage fright") | OPS-04 ×4, OPS-24 ×4 |
| HRM-PC00-17 | Vertigo | 8 | — | — | One enemy | Delirium, base 55 | OPS-08 ×4, OPS-17 ×4 |
| HRM-PC00-18 | Diabolus | 8 | — | — | One enemy | Discord, base 55 (on enemies blocks `ENSEMBLE` skills: volleys, shield walls) | OPS-08 ×4 |
| HRM-PC00-19 | Statuaire | 18 | — | — | One enemy | Marble, base 30 | OPS-11 ×3 |
| HRM-PC00-20 | Glas | 16 | — | — | One enemy | Coda (20), base 30 | OPS-03, 13, 17, 21 ×3 |
| HRM-PC00-21 | Resurrexit | 30 | — | — | One ally | Revives a Swooned ally at 100% HP | OPS-10 ×2, OPS-31 ×2 |
| HRM-PC00-22 | Retraite | 12 | — | — | Field / party | Field: return to the dungeon's entrance or last Lectern passed. Battle: the next flee check succeeds (not bosses) | OPS-23 ×8 |
| HRM-PC00-23 | Sourdine | 10 | — | — | Field | Encounters ×0.5 for 300 steps (the `ENC_HALF` modifier; never stacks with a relic) | OPS-06 ×8 |
| HRM-PC00-24 | Second Piano | 24 | — | — | Party | Swell +2 on every ally: the whole party plays second piano to his concerto. Never Anachronic | OPS-25 ×1 |
| HRM-PC00-25 | Social Contract | 30 | — | — | Party | For the caster's next 3 turns, damage to any ally is split equally among living allies (rounded half up) | OPS-26 ×1 |
| HRM-PC00-26 | Cannonade | 28 | T4 · 80 | FIRE + EARTH | 6 random hits | No spread penalty | OPS-27 ×1 |
| HRM-PC00-27 | Four Strings | 28 | T4 · 80 | EARTH, WATER, WIND, BOLT | 4 hits, one enemy | One hit per string, G D A E, each its own element | OPS-28 ×1 |
| HRM-PC00-28 | Fairy Horn | 18 | — | — | All enemies | Stun, base 40 (bosses immune) | OPS-29 ×1 |
| HRM-PC00-29 | Rempart | 30 | — | — | Party | Varnish and Glaze on every ally | OPS-30 ×1 |
| HRM-PC00-30 | Contrapunctus | 50 | T5 · 120 | — | 4 hits, one enemy | Non-elemental, so no resistance halves it. Needs Lv 41 | OPS-31 ×1 |
| HRM-PC00-31 | Unfinished | 50 | T5 · 120 | CHRONO | All enemies | ×0.5 spread; Heat 5. Needs Lv 41 | OPS-32 ×1 |

**Taught by Scores but innate to someone** (cross-learnable): Min-jun's Pianissimo, Cantabile, Swell, Inspire, Tempus; Lucile's Lead White, Glaze, Varnish, Gold Leaf, Zenith; Berlioz's Fanfare; Chopin's Cantilena, Clarity, Allegro, Lento, Encore, Miroir, Mazurka, Fermata, Valse brillante; Liszt's nine elemental spells; Farrenc's Marginalia, Tempo Giusto, Engraving, Burin, Copperplate. **Never on a Score** (the faces of the cast): every Signature, *Ecstasy*, *Byeol*, and the skills marked "own" in §7–§15. The elemental map is deliberate: Liszt owns FIRE, ICE and BOLT; Farrenc EARTH; Lucile LIGHT; Min-jun the non-elemental tone and CHRONO; WATER, WIND and SHADE belong to the Scores, so everyone has something to borrow.

## 7. PC-01 Kang Min-jun: RECITAL and CONDUCT

Bard and conductor (CANON §5c). Mechanics are `combat_ensemble` §4.6: Movement I pays **6 + 2 × Heat** INS and adds its Heat once; Continue advances (+3 Crescendo each); III is a burst at **1.5 Pₜ** (heals 1.5 Hₜ, revivals at 50%) and ends the piece; *Da Capo* resets Coda; **CONDUCT** (end of CH-04) gives an ally a ×1.25 bonus action. Modifiers ("WATER +25%") apply to party damage of that element while the piece lasts; "again" means the Movement I status is re-rolled. Effects follow CANON §15d; where the canon names two parts, Movement II re-applies the first.

### 7.1 The battle Repertoire

| REP | Piece | Joins (CANON §15d scene) | INS (Heat) | I | II | III |
|---|---|---|---|---|---|---|
| REP-00 | Resonance | CH-01 | 6 (0) | Stun every Echo (base 60; BOSS-01's core excepted) | Shatters `bonewall` props; ends (no III) | — |
| REP-01 | Clair de lune | CH-01 (KEY-04 in his tote) | 12 (3) | Party Cantabile | LIGHT +25% | Party heal, ×0.5 spread |
| REP-31 | Arirang | CH-02, hummed | 6 (0) | Party: cure Discord and Swing | Cure again; party Cantabile | Party heal, ×0.5 spread |
| REP-08 | Ondine | CH-03, Lavergne salon | 14 (4) | WATER +25% | Lento on all enemies (base 60) | WATER burst, all, ×0.5 |
| REP-02 | Arabesque No. 1 | CH-04, meeting Lucile | 10 (2) | Party TMP +10% | Party regains 2% max INS per turn | Party Allegro |
| REP-14 | Prelude in C♯ minor | CH-04, barricade bells | 12 (3) | Stagefright on all enemies (base 45) | Again | EARTH bell strike, one |
| REP-11 | Jeux d'eau | CH-05, Pleyel showroom | 12 (3) | WATER +25% | Party EVA +10 points | Party cleanse |
| REP-03 | Reflets dans l'eau | CH-06, lesson on reflections | 12 (3) | Mirror on one ally | Party Mirror | WATER wave, all, ×0.5 |
| REP-19 | Étude in D♯ minor | CH-07, duel finale | 12 (3) | Fortissimo on one ally | Fortissimo on every ally | FIRE burst, one |
| REP-15 | Prelude in G minor | CH-08, facing Julien | 12 (3) | Party Swell +1 | Party Swell +1 | March strike, one, non-elemental |
| REP-12 | Pavane | CH-09, Chopin's confession | 10 (2) | Party Cantabile | Party: cure Stagefright | Encore on the lowest-HP% ally |
| REP-20 | Left-Hand Prelude | CH-09, the cell | 10 (2) | Party Cantabile (**playable while Hushed**) | Again | Heal the lowest-HP% ally |
| REP-24 | Toccata | CH-11, the *Concordia* | 16 (5) | Party Allegro | BOLT +25% | 6 BOLT hits on one enemy |
| REP-09 | Le Gibet | CH-12, "Play for me" | 14 (4) | Enemy RES −20% | Holds | Coda (20) on one enemy (base 30) |
| REP-23 | Suggestion diabolique | CH-12, vs Delorme | 16 (5) | Hush on all enemies (base 55) | Again | SHADE + CHRONO strike, one |
| REP-27 | Concerto "Lost Era" | CH-13, after BOSS-17 | 6 (0) | +3 Crescendo per movement only (no effects in CANON §15d) | — | — |
| REP-30 | Jeong-dong Nocturne | CH-13 (salon piece from CH-03) | 6 (0) | As REP-27 | — | — |
| REP-29 | La Musique des étoiles | CH-14, written Wed 18 Dec | 6 (0) | As REP-27 | — | — |
| REP-07 | L'isle joyeuse | CH-14, first dirigible flight | 14 (4) | Party Allegro | Party Fortissimo | Crescendo +30 |
| REP-10 | Scarbo | CH-14, Hôtel de Vane | 16 (5) | SHADE +25% | Delirium on all enemies (base 55) | SHADE storm, all, ×0.5 |
| REP-18 | Vocalise | CH-14, Night of Stars | 10 (2) | Party regains 2% max INS per turn | Party Cantabile | Revive one ally at 50% (if none, heal the lowest) |
| REP-06 | Cathédrale engloutie | CH-15 | 14 (4) | Party Varnish | Party Glaze | EARTH + WATER quake, all, ×0.5 |
| REP-25 | Visions fugitives | CH-15 (Nos. 1, 7, 14) | 14 (4) | Sets Dawn | Sets Dusk | Sets Night; CHRONO burst at 1.0 Pₜ, all, ×0.5 (its Heat is the piece's 4, paid at I) |
| REP-22 | Vers la flamme | CH-16, Archon's phases | 16 (5) | Crescendo +20 at each of his turns | Adds FIRE and LIGHT +25% | FIRE + LIGHT nova, all, ×0.5 |
| REP-05 | The Snow Is Dancing | CH-E1, first snow (also field music) | 10 (2) | Lento on all enemies (base 60) | Again | ICE burst, all, ×0.5 |

**Not battle pieces:** REP-04 (opens Czerny's drills, §16), REP-13 and REP-16 (SYN-02 flavour, salon duets), REP-21 (Liszt's *Ecstasy*), REP-26 (SYN-15 only), REP-17 and REP-35–45 (✦ Invocations), REP-28 and REP-32–34 (salons). In CH-E2 every battle piece stays (CANON §11e).

### 7.2 Harmony skills

| ID | Skill | INS | Power | Element | Target | Effect | Learned |
|---|---|---|---|---|---|---|---|
| HRM-PC01-01 | A440 | 4 | T1 · 12 | — | One | ×1.25 against `echo` enemies: a pure A cancels a recording (own) | Lv 2 (CH-01) |
| HRM-PC01-02 | Pianissimo | 6 | — | — | One enemy | Hush, base 55 | Lv 4 (CH-02) |
| HRM-PC01-03 | Dissonance | 5 | — | — | One enemy | Out of Tune, base 65 (own) | Lv 7 (CH-03) |
| HRM-PC01-04 | Cantabile | 6 | — | — | One ally | Cantabile | Lv 10 (CH-04) |
| HRM-PC01-05 | Overtone | 9 | T2 · 28 | — | 1/All | Non-elemental (own) | Lv 12, CH-05 |
| HRM-PC01-06 | Swell | 8 | — | — | One ally | Swell +1 | Lv 14 (CH-06) |
| HRM-PC01-07 | Inspire | 14 | — | — | One ally | Inspired | Lv 20 (CH-08) |
| HRM-PC01-08 | Just Intonation | 16 | T3 · 50 | — | 1/All | Non-elemental (own) | Lv 24, CH-10 |
| HRM-PC01-09 | Ritardando | 16 | — | CHRONO | All enemies | Lento (base 60) and gauge −15% (−39); Heat 5 (own) | Story: CH-15, first amalgam zone, when Seoul and Paris overlap in his ears |
| HRM-PC01-10 | Tempus | 28 | T4 · 80 | CHRONO | 1/All | Heat 5 | Lv 37 and the CH-15 story flag |
| HRM-PC01-11 | Accelerando | 24 | — | CHRONO | Party | Allegro and gauge +25% (+64); Heat 5 (own) | Story: CH-16, the instant the Stilled Hour breaks (before BOSS-28) |

His CHRONO is the residue of living inside the Stilled Hour and survives the Heart's shattering (it is CANON §10c's "Min-jun's late skills"); it is the one key that bar 3 of BOSS-31 and BOSS-34 does not resist, and BOSS-43 is weak to it. The non-elemental tones (A440, Overtone, Just Intonation) never meet a resistance: the bard's quiet answer to the superbosses.

## 8. PC-02 Lucile Aubray: PLEIN AIR

Chromomancer: Delacroix paints subjects, she paints the hour (CANON §5e). Numbers are `combat_ensemble` §4.6; each style is a lesson she turned into her own hand (LAW-20: "You asked me. They never asked anyone.").

| Style | Unlocked | Master and lesson (CANON §4d) | INS | Shape | Heat |
|---|---|---|---|---|---|
| **IMPRESSION** | CH-05 dawn lesson, Pont des Arts | Monet: colour in shadows | Cₜ | One enemy, Pₜ in the Light's first boosted element, +20% per consecutive turn (max +100%) | 2 |
| **POINTILLÉ** | CH-10, Lesson 3 "The Field in Points" (Berry) | "Pissarro's manner" (his divisionist years) | 1.5 Cₜ | 8 random hits sharing Pₜ, each a Dot (10 = Composed); or 8 dots of Cantabile, Allegro or Varnish on allies | 3 |
| **IMPASTO** | CH-14, Lesson 4 "Night", Montmartre | Van Gogh | 2 Cₜ | 1.5 Pₜ on one enemy; sets Night; Discord (base 40); she gains Allegro | 4 |
| *Nuit étoilée* | IMPASTO cast under Night | — | 2 Cₜ | 8 LIGHT + SHADE hits on one enemy; each restores 2% max INS to the party | 4 |
| **LUMIÈRE** | CH-E1: painting Seoul at night · CH-E2: "Then I'll paint something he won't" | Her own | 1.5 Cₜ | 2 Pₜ to all, ×0.5; sets two Painted Lights; +1% per Hanmadi word (CH-E1, max +40%) | 2 (Spotlight only, CH-E1) |
| *Shift the Hour* | CH-05 | — | 0 | Sets Dawn, Noon, Dusk or Night | 0 |

**First boosted element by Light:** Dawn LIGHT · Noon FIRE · Dusk WATER · Night SHADE · Candle FIRE · Fog WATER · Gloom SHADE. *Plein Air* (+25% under Dawn, Noon, Fog) makes Dawn-IMPRESSION her signature opener; Delacroix's *Chiaroscuro* wants Dusk, Night or Candle, so the two quarrel over the hour on every turn (CANON §11d). **Rank 10 (*Golden Hour*, Night of Stars):** *Shift the Hour* no longer resets IMPRESSION's streak. Her canvases follow the same ladder (LAW-21): 11 IMPRESSION from August, 9 POINTILLÉ from October, 4 IMPASTO in December.

| ID | Skill | INS | Power | Element | Target | Effect | Learned |
|---|---|---|---|---|---|---|---|
| HRM-PC02-01 | Lead White | 9 | T2 · 28 | LIGHT | 1/All | — | Join, Lv 11 (CH-05) |
| HRM-PC02-02 | Glaze | 10 | — | — | One ally | Glaze | Lv 13 |
| HRM-PC02-03 | Varnish | 10 | — | — | One ally | Varnish | Lv 16 |
| HRM-PC02-04 | Effet de brume | Cₜ | 0.6 Pₜ | WATER | All enemies, ×0.5 | **Signature** (R5): sets Fog, then Smoke (base 60) on all; named for her first canvas | R5 |
| HRM-PC02-05 | Gold Leaf | 16 | T3 · 50 | LIGHT | 1/All | — | Lv 22, CH-10 |
| HRM-PC02-06 | Zenith | 28 | T4 · 80 | LIGHT | 1/All | — | Lv 33, CH-14 |
| HRM-PC02-07 | 별 Byeol | 30 | T4 · 80 | LIGHT | All enemies, ×0.5 | Party Inspired. Her first written hangul word, "star" (own) | CH-E1: all 40 Hanmadi words (CANON §4f) |

*Check.* *Effet de brume* at Lv 12 (ART 22) against RES 16: (67.2 + 44) × 2.1 × 100/116 = 201, ×0.5 = 101, and the Fog it sets lifts its WATER to 126 per enemy while blinding them, for 9 INS: a defensive opener that also arms her Plein Air bonus.

## 9. PC-03 Hector Berlioz: ORCHESTRATE

Summoner and knight. *Cue* and *Tutti* are `combat_ensemble` §4.6; recipes are §5.2; Invocation twice per battle; *Idée Fixe* rewards three Fights on one target. **Rank 10 (*Maestro*, BQ-PC03 finale):** after a Cue his gauge refills from 128 instead of 0, so a three-token Tutti takes 2.5 turns instead of 4 (Lv 40: 1,308 per turn against 818).

| ID | Skill | INS | Power | Element | Target | Effect | Learned |
|---|---|---|---|---|---|---|---|
| HRM-PC03-01 | Fanfare | 6 | — | — | One ally | Fortissimo | Join, Lv 5 (end CH-02) |
| HRM-PC03-02 | Coup d'archet | 8 | PHYS AR ×1.5 | Weapon | One | A sword-cane cut on the downbeat (own) | Lv 8 (CH-03) |
| HRM-PC03-03 | Chœur d'ombres | Cₜ | 0.8 Pₜ | SHADE | All enemies, ×0.5 | **Signature** (R5, from *Lélio*): Reverie (base 45) after the damage | R5 |
| HRM-PC03-04 | Estocade | 16 | PHYS AR ×1.6 | Weapon | One | Stagefright (base 45); counts as a Fight for *Idée Fixe* (own) | Lv 26 (CH-12 rejoin) |

## 10. PC-04 Eugène Delacroix: CANVAS, Sketch and the Studies

Spellblade and collector. **Free Canvas** (Cₜ): two unlocked Pigments and a Subject (one ×1, rank ×0.75, all ×0.5), PWR Pₜ, dual-element rule, never reflected; *Chiaroscuro* +25% under Dusk, Night or Candle (`combat_ensemble` §4.6). **Named recipes** fix the pair, the Subject and one rider (−20%); a recipe whose pigment is not yet unlocked is listed greyed. **Pigments** (CANON §5c): FIRE and WIND at join (CH-03); EARTH and WATER CH-05; ICE and BOLT CH-08; **LIGHT at rank 10, the BQ-PC04 finale in CH-09**; SHADE in CH-10 while he grinds lamp-black for the Salon du Roi ceiling, first usable when he rejoins in CH-12. **Rank 10** is the LIGHT pigment itself (canon).

**Story recipes**

| Recipe | Pigments · subject | Rider | Learned |
|---|---|---|---|
| Liberté | FIRE + WIND · all | Party Fortissimo | CH-04, the rue Saint-Antoine barricade (BOSS-05) |
| Chios | ICE + WATER · all | Spread ×0.75 instead of ×0.5 | CH-08, BQ-PC04 step: the *Scio* studies |
| Femmes d'Alger | LIGHT + FIRE · all | Sets Candle (so his next Canvases gain *Chiaroscuro*) | CH-09, BQ-PC04 finale, with the LIGHT pigment |
| Sardanapale | FIRE + SHADE · one | Stagefright (base 45) | CH-12, on rejoining |

**Sketch** (0 INS, unlocked CH-07) records an enemy's Study once that enemy has used the linked action this battle; otherwise a Rough Sketch shows HP and affinities, and aimed at an Onlooker it clears it. The bestiary attaches each family Study to one member of that family (`STUDY STU-## ON "<skill>"`); `bosses.md` does the same for boss Studies. Boss Studies are missable (FF5's Blue Magic rule); Da Capo carries every Study.

| STU | Study | Source (chapter) | Sketch after | Recipe | Pigments · subject · rider |
|---|---|---|---|---|---|
| STU-01 | Gaslight Wisp | Gaslight Wisps, P10 (CH-07+) | its flare | Contre-jour | FIRE + WIND · one · Smoke (60) |
| STU-02 | Pickpocket | pickpocket gangs, P10 (CH-07+) | its snatch | Pochade | EARTH + WIND · one · he gains Allegro |
| STU-03 | Brücke Mk. I | Mk. I automata, P18 (CH-07, CH-14) | its spring-lash | Hachures | BOLT + EARTH · rank · Stun (35) |
| STU-04 | Mk. I Escapement | same family | its gauge rewind | Ébauche | WATER + WIND · one · Lento (60) |
| STU-05 | Escapement Hound | BOSS-09 (CH-07) | its chime heal | Justinien | LIGHT + EARTH · one · Dispel |
| STU-06 | Cloaca Echo | Cloaca Echoes, P17 (CH-08) | its surge | Frottis | WATER + EARTH · all · Lento (55) |
| STU-07 | Sewer Rat | sewer rats, P17 | its gnaw | Grotesque | EARTH + SHADE · one · Out of Tune (60) |
| STU-08 | Phantom Quartet | Quartet spectres, P17; BOSS-11's Quartet | its riff | Paganini | BOLT + SHADE · one · Swing (55) |
| STU-09 | Café Tough | Julien's toughs, P17 | its bottle throw | Giaour | FIRE + EARTH · one · Stagefright (45) |
| STU-10 | Cloaca Leviathan | BOSS-10 (CH-08) | its sluice wave | Les Natchez | WATER + LIGHT · all · party Cantabile |
| STU-11 | The Cassette | BOSS-11 (CH-08) | the Walkman plays | Trompe-l'œil | ICE + WIND · all · Reverie (45) |
| STU-12 | Grey Hand Volley | Grey Hand, P31/P26/P27/P30 (CH-09+) | its volley | Boissy d'Anglas | FIRE + WIND · rank · Stagefright (45) |
| STU-13 | Barrel Automaton | barrel automata, P31 (CH-09) | its roll | Camaïeu | EARTH + ICE · one · Stun (35) |
| STU-14 | Roussel's Aim | BOSS-12 (CH-09; he must fight in the Bercy thread) | "Steady…" | Mirabeau | BOLT + WIND · one · Hush (55) |
| STU-15 | Grey Hand Shield | Grey Hand, P26 (CH-12+) | its shield wall | Cromwell | EARTH + SHADE · one · Lento (60) |
| STU-16 | Abbey Echo | Abbey Echoes, P26 (CH-12) | its plainchant | Richelieu | LIGHT + FIRE · one · Hush (55) |
| STU-17 | Living Tableau | Living Tableaux, P26 (CH-12; CH-E2) | its frame-step | Le Tasse | SHADE + WIND · one · Delirium (50) |
| STU-18 | Vanishing Point | BOSS-15 (CH-12) | *Vanishing Point* | Repoussoir | LIGHT + SHADE · one · Fermata (35) |
| STU-19 | Stage Automaton | stage machinery, P27 (CH-13) | its counterweight drop | Faust | SHADE + FIRE · all · Out of Tune (60) |
| STU-20 | Grey Assassin | Grey Hand assassins, P27 (CH-13) | its knife-throw | Liège | FIRE + EARTH · rank · Delirium (50) |
| STU-21 | Phonautograph | BOSS-18's horns (CH-13) | a horn records | Esquisse | WATER + BOLT · one · Hush (55) |
| STU-22 | Roussel Cleaner | Roussel's Cleaners, P34 (CH-14) | its sweep | Nancy | ICE + EARTH · rank · Stun (35) |
| STU-23 | Vane Collection | Vane's animated collection, P34 (CH-14) | its tableau pose | Missolonghi | EARTH + LIGHT · all · party Varnish |
| STU-24 | Hunter Automaton | Hunter Automata, R01 (CH-14) | its pounce | Tigre | EARTH + WIND · one · he gains Swell +1 |
| STU-25 | Boar | boar, R01 (CH-14) | its charge | Fantasia | FIRE + WIND · all · party Allegro |
| STU-26 | River Automaton | river automata, W02 and R09–R10 (CH-14) | its steam jet | Louis d'Orléans | FIRE + WATER · one · Smoke (60) |
| STU-27 | Lorelei Echo | Lorelei Echoes, R09 (CH-14) | its song | Macbeth | SHADE + WIND · all · Reverie (45) |
| STU-28 | Smuggler | frontier smugglers (W02) and Gros-Louis's men (P04), CH-14 | its smoke pot | Cadix | WATER + ICE · rank · Lento (60) |
| STU-29 | Forge Automaton | forge automata, R02 (CH-14; CH-E2) | its slag hurl | Meknès | EARTH + FIRE · all · sets Noon |
| STU-30 | Lutèce Construct | Amalgam Echoes, P29 Lutèce zones (CH-15) | its barricade rebuild | Ombre portée | EARTH + SHADE · rank · Stagefright (45) |
| STU-31 | Turnstile Golem | P29 Hanseong zones (CH-15) | its door-close | Tanger | WIND + BOLT · one · Stun (35) |
| STU-32 | Neon Wraith | P29 (CH-15) | its flicker | Clair-obscur | LIGHT + SHADE · all · Smoke (60) |
| STU-33 | Orpheus | BOSS-24 (CH-15, Party 3) | "Do not look back" | Jeune orpheline | WATER + LIGHT · one · Cantabile on the lowest-HP ally |
| STU-34 | Stilled Echo | Stilled Echoes, P30 (CH-16) | its time-stop | Gethsemane | LIGHT + SHADE · one · Encore on the lowest-HP ally |
| STU-35 | Archon's Tactics | BOSS-26 (CH-16) | a *Tactics* row shuffle | Marino Faliero | ICE + SHADE · one · Coda (30) |
| STU-36 | Golden Section | BOSS-33 (CH-E2) | a skied canvas falls | Au ciel | LIGHT + WIND · all · sets Dawn |

Early families (Ossuary Echoes, Choir Echoes, Black Coats, Tocsin and Tableau Echoes) meet him before CH-07 and give no Study: the cost of the order the story is told in. CH-15's Studies need him in the right party (or the merged party, where `dungeons.md` repeats the three families).

| ID | Skill | INS | Power | Element | Target | Effect | Learned |
|---|---|---|---|---|---|---|---|
| HRM-PC04-01 | Touche | 6 | — | Pigment | Self | His Fights this battle carry one unlocked pigment of his choice (own: the Mystic Knight's edge) | Join, Lv 6 (CH-03) |
| HRM-PC04-02 | Grisaille | 5 | — | — | One enemy | Smoke, base 65 (own) | Lv 9 (CH-03) |
| HRM-PC04-03 | Barque de Dante | Cₜ | 0.8 Pₜ | WATER + SHADE | All enemies, ×0.5 | **Signature** (R5, *La Barque de Dante*, 1822): Lento (base 60), the damned clinging to the boat | R5 |
| HRM-PC04-04 | Pentimento | 10 | — | — | One enemy | **Dispel**: removes every positive status (own) | Lv 16 (CH-07) |

## 11. PC-05 Charles-Valentin Alkan: ÉTUDE

Monk. Enter the sequence within **2.0 s** (clock stopped); success fires the Étude, a miss is *Fausse note* (a plain Fight). No INS; always hits; ignores row. Power = AR × E split across hits: E = 1.5 + 0.3 per input above 3 (3 → 1.5 … 8 → 3.0), the Lv-50 Étude 3.5, −20% per rider (`formulas_and_curves` §8.4). Conducted: cannot fail, ×1.25. **Rank 10 (*Sang-froid*, BQ-PC05 finale):** the window is 2.5 s. Names are plain French terms (CANON §5c).

| ETU | Étude | Lv | Input | E | Element | Target | Rider |
|---|---|---|---|---|---|---|---|
| ETU-01 | Martèlement | 11 | → ← A | 1.5 | EARTH | One | — |
| ETU-02 | Octaves | 11 | ↑ ↓ B | 1.2 | — | One | Stun (base 30) |
| ETU-03 | Pédale | 11 | ↓ ↓ A | 1.5 | — | All, ×0.5 | — |
| ETU-04 | Tierces | 14 | → ↓ ← B | 1.8 | WIND | One | — |
| ETU-05 | Main gauche | 18 | ← ← → X | 1.44 | — | One | Out of Tune (base 65) |
| ETU-06 | Carillon | 22 | ↑ → ↓ ← A | 2.1 | BOLT | All, ×0.5 | — |
| ETU-07 | Aubade | 26 | ↓ ← ↑ → B A | 1.92 | LIGHT | One | Sets Dawn |
| ETU-08 | Sérénade | 30 | ← → ← → X Y | 1.92 | SHADE | One | Sets Night |
| ETU-09 | Moto perpetuo | 34 | ↑ ↑ ↓ ↓ ← → A | 2.7 | — | 7 random hits | — |
| ETU-10 | Fugato | 38 | ← ↓ → ↑ A B X Y | 3.0 | — | One | — |
| ETU-11 | Prestissimo | 43 | L R ↑ ↓ ← → A B | 2.4 | — | All, ×0.5 | Lento (base 60) |
| ETU-12 | Ostinato | 50 | A B A B ↓ ↓ L R | 3.5 | EARTH | One | — |

*Check:* *Fugato* at Lv 40 (AR 246) against DEF 54 is 782.7 × 3.0 = **2,348**, the `formulas_and_curves` §11.4 parity line.

| ID | Skill | INS | Power | Element | Target | Effect | Learned |
|---|---|---|---|---|---|---|---|
| HRM-PC05-01 | Psaume | 8 | — | — | Self | Bulwark (4 turns) and Cantabile: a psalm under his breath (own) | Lv 12 (CH-05) |
| HRM-PC05-02 | Les Omnibus | 0.5 Cₜ (min 2) | PHYS AR ×1.0 | Weapon | Every enemy | **Signature** (R5, his variations, Op. 2): one blow each, no spread penalty, always hits | R5 |
| HRM-PC05-03 | Contre-coup | 8 | — | — | Self | Until his next turn, each physical hit on him draws a P1 Fight in return (own) | Lv 20 (CH-08) |

## 12. PC-06 Frédéric Chopin: RUBATO

Healer and time mage. *Borrow* (enemy gauge −30%, +1 charge, max 3) and *Repay* (+34% per charge to one ally; 3 = an immediate turn; cures Fermata) are `combat_ensemble` §4.6. **Rank 10:** *Tempo Rubato*, Borrow hits all enemies (canon).

| ID | Skill | INS | Power | Element | Target | Effect | Learned |
|---|---|---|---|---|---|---|---|
| HRM-PC06-01 | Cantilena | 10 | H2 · 24 | — | 1/All ally | Heal | Join, Lv 13 (CH-06) |
| HRM-PC06-02 | Clarity | 6 | — | — | One ally | Cures Miasma, Smoke, Hush (CANON §10d) | Join |
| HRM-PC06-03 | Allegro | 8 | — | — | One ally | Allegro (cancels Lento) | Lv 14 |
| HRM-PC06-04 | Lento | 6 | — | — | One enemy | Lento, base 65 | Lv 16 (CH-07) |
| HRM-PC06-05 | Encore | 18 | — | — | One ally | Revives a Swooned ally at 25%, or grants Encore to a living one (CANON §10d) | Lv 18 (CH-08) |
| HRM-PC06-06 | Miroir | 12 | — | — | One ally | Mirror (3 reflections) | Lv 21 (CH-09) |
| HRM-PC06-07 | Étude ut mineur | Cₜ | Pₜ | SHADE + BOLT | 8 random hits | **Signature** (R5, Op. 10 No. 12, published 1833): the left-hand storm, no spread penalty | R5 |
| HRM-PC06-08 | Mazurka | 18 | H3 · 45 | — | 1/All ally | Heal | Lv 22, CH-10 (learned at his first CH-11 battle: he stays in Paris in CH-10) |
| HRM-PC06-09 | Fermata | 16 | — | — | One enemy | Fermata, base 35 | Lv 26 (CH-11) |
| HRM-PC06-10 | Valse brillante | 30 | H4 · 70 | — | 1/All ally | Heal (Op. 18, composed 1833) | Lv 33, CH-14 |

*Sotto Voce* adds +20% to every heal above: *Cantilena* at Lv 21 heals 562 (`formulas_and_curves` §4.4).

## 13. PC-07 Franz Liszt: TRANSCEND and MEPHISTO

Black mage and duellist. **TRANSCEND:** two Harmony skills, each with its own target, in one action for total INS × 1.5; *Bravura* applies to both; Hush blocks it; Invocations cannot be paired (they are summons). **MEPHISTO** (CH-13) adds *Transcribe*: the last skill used by anyone at ×1.25, original INS (10% of his max INS for an enemy skill); copies Harmony, enemy skills, a Recital's Movement I and a Tutti; never Invocations, other commands or Synergies. **Rank 10 (*Transcendence*, BQ-PC07 finale):** TRANSCEND costs INS × 1.25. Pairs worth teaching: two opposites (Con Fuoco + Glaciale) to find a weakness blind; Fulmine + Lamp-Black under Night (both elements boosted); *Harm. poétiques* on one turn so that the next TRANSCEND is paid at half under Inspired.

| ID | Skill | INS | Power | Element | Target | Effect | Learned |
|---|---|---|---|---|---|---|---|
| HRM-PC07-01 | Con Fuoco | 9 | T2 · 28 | FIRE | 1/All | — | Join, Lv 15 (CH-07) |
| HRM-PC07-02 | Glaciale | 9 | T2 · 28 | ICE | 1/All | — | Join |
| HRM-PC07-03 | Sforzando | 9 | T2 · 28 | BOLT | 1/All | — | Lv 17 |
| HRM-PC07-04 | Harm. poétiques | 1.5 Cₜ | 0.8 Pₜ | LIGHT | All enemies, ×0.5 | **Signature** (R5, *Harmonies poétiques*, 1833): party Inspired | R5 |
| HRM-PC07-05 | Feroce | 16 | T3 · 50 | FIRE | 1/All | — | Lv 22, CH-10 |
| HRM-PC07-06 | Cristallo | 16 | T3 · 50 | ICE | 1/All | — | Lv 24 |
| HRM-PC07-07 | Fulmine | 16 | T3 · 50 | BOLT | 1/All | — | Lv 26 |
| HRM-PC07-08 | Tutta Forza | 28 | T4 · 80 | FIRE | 1/All | — | Lv 33, CH-14 |
| HRM-PC07-09 | Hiver | 28 | T4 · 80 | ICE | 1/All | — | Lv 35 |
| HRM-PC07-10 | Tempesta | 28 | T4 · 80 | BOLT | 1/All | — | Lv 37 |
| HRM-PC07-11 | Ecstasy | 40 | T4 · 80 | FIRE + LIGHT | All enemies, **×0.75** each | Scriabin's Sonata No. 5 (REP-21) as Min-jun taught it to him; Anachronic, Heat 5 (own) | BQ-PC07 finale, after BOSS-36 (CH-14) |

## 14. PC-08 Louise Farrenc: COUNTERPOINT

Scholar. *Annotate*, *Canon*, *Fugue* (Lv 22) and *Cadence* (Lv 30) are `combat_ensemble` §4.6. **Rank 10 (*Stretto*, BQ-PC08 finale):** *Canon* marks two allies, the target and the lowest-HP% other ally.

| ID | Skill | INS | Power | Element | Target | Effect | Learned |
|---|---|---|---|---|---|---|---|
| HRM-PC08-01 | Marginalia | 4 | — | — | All enemies | HP and affinities of every enemy for the battle (a Rough Sketch on all) | Join, Lv 18 (CH-08) |
| HRM-PC08-02 | Tempo Giusto | 6 | — | — | One ally | Cures Lento, Swing and Out of Tune | Join |
| HRM-PC08-03 | Engraving | 9 | T2 · 28 | EARTH | 1/All | — | Lv 19 |
| HRM-PC08-04 | Air russe | Cₜ | Pₜ | EARTH, WATER, WIND, ICE | 4 random hits | **Signature** (R5, R-58): theme and three variations, one element each, no spread penalty | R5 |
| HRM-PC08-05 | Burin | 16 | T3 · 50 | EARTH | 1/All | — | Lv 23, CH-10 |
| HRM-PC08-06 | Copperplate | 28 | T4 · 80 | EARTH | 1/All | — | Lv 34, CH-14 |

## 15. PC-09 Seo-yeon, PC-10 Jae-won, PC-11 Julien

**Seo-yeon — BOW** (CH-E1): *Sostenuto* (party heal Hₜ ×0.5, +25% per consecutive turn, party Cantabile while chained) or *Spiccato* (4 random hits, each ×0.4 her Fight); switching costs no turn; *Sibling* +20% TMP beside Min-jun (`combat_ensemble` §4.6).

| ID | Skill | INS | Power | Element | Target | Effect | Learned |
|---|---|---|---|---|---|---|---|
| HRM-PC09-01 | Harmonics | 28 | T4 · 80 | ICE | 1/All | Glassy flageolet tones (own) | Join, Lv 40 |
| HRM-PC09-02 | Col legno | 10 | — | — | One enemy | Stun, base 35 (own) | Lv 42 |
| HRM-PC09-03 | Con sordino | 30 | — | — | Party | Glaze on every ally (own) | Lv 44 |

**Jae-won — BEAT** (CH-E1): press A as each of 8 rings closes (Perfect ±3 frames, Good ±8); each hit 0.3 × Fight × (1 + 0.1 per Perfect); a perfect 8 steals. Rings carry the *janggu* stroke of the cycle (덩 *deong* both heads, 쿵 *kung* bass, 덕 *deok* stick, 기덕 *gideok* grace); the accent is visual only.

| *Jangdan* | Levels | Interval | The 8 rings |
|---|---|---|---|
| *Semachi* | 40–42 | 0.67 s | deong · deok · deok · kung · deok · deok · deong · deok |
| *Gutgeori* | 43–45 | 0.50 s | deong · gideok · kung · deok · kung · deok · deong · deok |
| *Jajinmori* | 46–48 | 0.38 s | deong · deong · deok · kung · deok · deong · kung · deok |
| *Hwimori* | 49+ | 0.25 s | deong · deok · kung · deok · deong · deok · kung · deok |

| ID | Skill | INS | Power | Element | Target | Effect | Learned |
|---|---|---|---|---|---|---|---|
| HRM-PC10-01 | Sangmo | 12 | PHYS AR ×1.5 | Weapon | All enemies, ×0.5 | The ribboned hat spins through the line (own) | Join, Lv 40 |
| HRM-PC10-02 | Chuimsae | 10 | — | — | One ally | Fortissimo and Crescendo +10: the shout of 얼쑤 *eolssu* (own) | Lv 43 |

**Julien — IMPROVISE** (CH-14–CH-16, CH-E2): three reels stopped left to right at 10 symbols/s (4 in Rehearsal Mode); results and numbers are `combat_ensemble` §4.6. **Reel strips** (8 positions, looping):

| Reel | Strip |
|---|---|
| 1 | ii · V · I · ii · ♭VII · V · IV · ♭II |
| 2 | V · I · ii · V · ♭II · I · ♭VII · IV |
| 3 | I · ii · V · I · IV · ii · ♭II · ♭VII |

Blind stops give *Turnaround* 1.6%, *Dominant*, *Tonic* and *Dorian Vamp* 0.8% each, *Backdoor* 0.4%, *Amen*, *Flat Seven* and *Tritone Storm* 0.2% each, *Blue Note* 95.1%; an aimed stop has a 100-ms window (250 ms in Rehearsal). **Rank 10 (*Second Chorus*, BQ-PC11 finale):** once per battle he may re-spin reel 3 after seeing the first two.

| ID | Skill | INS | Power | Element | Target | Effect | Learned |
|---|---|---|---|---|---|---|---|
| HRM-PC11-01 | Walking Bass | 28 | T4 · 80 | EARTH | 1/All | (own) | Join, Lv 33 (CH-14) |
| HRM-PC11-02 | Rimshot | 10 | — | — | One enemy | Stun, base 35 (own) | Join |
| HRM-PC11-03 | Modal Vamp | Cₜ | 0.5 Pₜ per turn | — | Random enemy | **Signature** (R5; he joins at 550 BP, so at once): for his next 4 turns a free *Blue Note* fires at each turn start; Anachronic, Heat 3 | Join |

## 16. Guests (GST-01–GST-10)

Guests cannot learn or equip; they bring one command at the chapter anchor (CANON §6; values `combat_ensemble` §4.7).

| GST | Command | Full content |
|---|---|---|
| GST-01 Mathurin | LANTERN | Reveal hidden paths, Unseen enemies and Echoes in walls; or Smoke (base 70) on one enemy |
| GST-02 Sand | NOVEL | *Tragedy*: Coda (20) on one enemy · *Romance*: Reverie on all · *Satire*: Out of Tune and DEF −25% (5 turns) on all |
| GST-03 Corot | SOUVENIR | Misty party heal Hₜ ×0.5, then Varnish on all |
| GST-04 Clara | PRODIGY (AI) | Replays Min-jun's current movement one tier higher; otherwise *Caprice*, Allegro on one ally |
| GST-05 Mendelssohn | HEBRIDES | WATER + WIND wave Pₜ ×0.5 · *Song without Words*: cures Hush on the party |
| GST-06 Czerny | VELOCITY | Party Allegro. Out of battle (after REP-04): three *School of Velocity* drills (Op. 299 Nos. 1–3) on the *Phrase* staff; each one a member passes gives that member **+1 TMP**, outside the Opus ledger (max +3 each) |
| GST-07 "Florestan" | FLORESTAN / EUSEBIUS (AI) | BOLT strike Pₜ or Cantabile on one ally; switches persona every 2 actions |
| GST-08 Offenbach | GALOP | One of six at random (weights out of 16): trip (Fermata 1) 3, screech (Hush) 3, pocket-pick (Steal) 3, cheer (Allegro) 3, can-can kick (double hit) 3, pratfall (1 damage) 1 |
| GST-09 Marthe | TRIAGE | Once per battle: full heal and cure every negative status on one ally |
| GST-10 Thalberg | THREE HANDS | Three hits at 0.5 Pₜ each: bass EARTH, melody LIGHT, arpeggio WIND |

## 17. Rank Rewards, Cadenzas and Synergy References

**17.1 Signatures (R5, CANON §11f)** are listed in each member's table. They are character-locked, never on a Score, and **scale with the command tier** (Pₜ, Cₜ), so a Signature earned at R5 in CH-06 is still a turn worth taking in CH-16.

**17.2 Rank-10 command upgrades** (CANON §11f names two; `secrecy_and_trust` §3.3 leaves the rest here):

| Member | Upgrade | Effect |
|---|---|---|
| LU | *Golden Hour* | *Shift the Hour* keeps IMPRESSION's streak |
| BE | *Maestro* | Gauge refills from 128 after a Cue |
| DE | LIGHT pigment (canon) | Eighth pigment; *Femmes d'Alger* |
| AL | *Sang-froid* | Étude window 2.5 s |
| CH | *Tempo Rubato* (canon) | Borrow hits all enemies |
| LI | *Transcendence* | TRANSCEND at INS × 1.25 |
| FA | *Stretto* | *Canon* marks two allies |
| JU | *Second Chorus* | Re-spin reel 3 once per battle |

**17.3 Cadenza menu short forms** (≤ 16; banners keep the full name, `combat_ensemble` §7): Gaspard Unbound · Lever du jour · Dies irae · Liberté guidant · La Machine · Warszawa · La Clochette · Grand Tirage · Arirang Var. · Encore Stage · Changes.

**17.4 Synergies** (names, members, effects and unlocks are CANON §11b and `combat_ensemble` §6.5, unchanged; the menu short form is this doc's, CANON §16h):

| SYN | Banner | Menu | Unlock | SYN | Banner | Menu | Unlock |
|---|---|---|---|---|---|---|---|
| 01 | Clair de Lune Impression | Clair de Lune | LU R3 | 13 | Brother from Tomorrow | Frère de demain | Story CH-14 |
| 02 | Two-Piano Tempest | 2-Piano Tempest | LI R3 | 14 | Symphony of Tomorrow | Sym. of Tomorrow | BE, LI R8 |
| 03 | Rubato Recital | Rubato Recital | CH R3 | 15 | Prometheus | Prometheus | LU, BE R8, CH-14+ |
| 04 | Idée Fixe Fortissimo | Idée Fixe ff | BE R3 | 16 | Octave of the Lost Era | Octave | Story CH-16 |
| 05 | Portrait in Shadow | Shadow Portrait | DE R3 | 17 | Arirang for Two | Arirang for Two | Story CH-E1 |
| 06 | Equal Temperament | Temperament | FA R3 | 18 | Hwimori | Hwimori | Story CH-E1 |
| 07 | Pédalier Duo | Pédalier Duo | AL R3 | 19 | Samulnori | Samulnori | Story CH-E1 |
| 08 | Liberty Leading the Orchestra | Liberty Leading | Story CH-04 | 20 | Blue Hour | Blue Hour | JU, LU R8 |
| 09 | Les Deux Virtuoses | Deux Virtuoses | Scene CH-07+ | 21 | Polonaise of Exiles | Polonaise | Scene CH-09+ |
| 10 | Chiaroscuro et Lumière | Chiaroscuro | Scene CH-06+ | 22 | Rival Virtuosi | Rival Virtuosi | Scene CH-08+ |
| 11 | Double Fugue | Double Fugue | Scene CH-08+ | 23 | Les Inadmissibles | Inadmissibles | Scene CH-14+, after SQ-07 council |
| 12 | Nocturne in Blue | Nocturne in Blue | Scene CH-08+ | | | | |

## 18. Progression Pacing and the Power Curve

Levels are the `formulas_and_curves` §6.2 exits; OP is an always-equipped member (§8.3); "Harmony" is a typical active member's known HRMs (own + Score-learned); Scores are critical path (with optional content).

| Ch. | Lv | Tier | Scores | OP | Harmony | Études | Tuttis | Studies | Pigments | Styles | Recital |
|---|---|---|---|---|---|---|---|---|---|---|---|
| CH-01 | 4 | T1 | 0 | — | 1 (MJ) | — | — | — | — | — | 2 |
| CH-02 | 6 | T1 | 0 | — | 2 | — | 3 | — | — | — | 3 |
| CH-03 | 8 | T1 | 0 | — | 2–3 | — | 4 | — | 2 | — | 4 |
| CH-04 | 11 | T1 | 0 | — | 3–4 | 3 | 5 | — | 2 | — | 6 |
| CH-05 | 13 | T2 | 3 | 40 | 4–6 | 3 | 7 | — | 4 | IMPRESSION | 7 |
| CH-06 | 15 | T2 | 6 | 83 | 6–8 | 4 | 9 | — | 4 | 1 | 8 |
| CH-07 | 17 | T2 | 8 | 145 | 8–10 | 4 | 10 | 5 | 4 | 1 | 9 |
| CH-08 | 20 | T2 | 12 | 221 | 10–13 | 5 | 12 | 11 | 6 | 1 | 10 |
| CH-09 | 22 | T2 | 12 | 308 | 12–15 | 6 | 14 | 14 | 7 | 1 | 12 |
| CH-10 | 24 | T3 | 13 | 400 | 14–17 | 6 | 14 | 14 | 8 | POINTILLÉ | 12 |
| CH-11 | 27 | T3 | 14 (15) | 541 | 16–19 | 7 | 14 | 14 | 8 | 2 | 13 |
| CH-12 | 30 | T3 | 18 (19) | 710 | 19–23 | 8 | 17 | 18 | 8 | 2 | 15 |
| CH-13 | 33 | T3 | 19 (21) | 884 | 21–25 | 8 | 17 | 21 | 8 | 2 | 17 |
| CH-14 | 35 (opt 42) | T4 | 23 (29) | 1,014 | 24–30 | 9 (10) | 20 | 29 | 8 | IMPASTO | 21 |
| CH-15 | 39 | T4 | 24 (30) | 1,212 | 27–33 | 10 | 20 | 33 | 8 | 3 | 23 |
| CH-16 | 41 | T4 | 24 (30) | 1,346 | 29–35 | 10 | 20 | 35 | 8 | 3 | 24 |
| CH-E1 / E2 | 45 | T4 | 24–31 | ≈1,690 | 32–38 | 11 | 20 | 36 (E2) | 8 | LUMIÈRE | 25 (E1) / 24 (E2) |
| Post-game | 50 | T5 | 31–32 | — | 40+ | 12 | 20 | 36 | 8 | 4 | 25 |

**Act I — one man and a tuning fork (CH-P–CH-04).** Min-jun survives on Fight, *Resonance* and *A440*; Berlioz arrives with three Tuttis and a blade; Delacroix with two pigments. The party has no Scores and few spells, so the first Synergy (SYN-08 at the barricade) lands like a revelation: one turn of the Ensemble outweighs four of anyone alone (Typical Fight 135 against a Duo's 560 per foe).

**Act II — the city opens its music (CH-05–CH-09).** Scores arrive with Paris: three in CH-05, twelve by the confessions. T2 doubles every caster's output (T1 146 → T2 280); Lucile paints the hour; *Sketch* turns every new enemy into a lesson. Players choose breadth: each member masters about one Score per chapter, so who wears *Messiah* or *Guillaume Tell* is the act's real decision. The ✦ Scores put cover on the table: the strongest early Invocations cost Heat 3 in streets and salons.

**Act III — specialisation on the road (CH-10–CH-13).** T3 arrives through a ✦ Score (*Le Tombeau*) because the shops are behind them; POINTILLÉ, MEPHISTO and the Rhine's 141 OP chapter let each member grow a second role. OP per hour triples (Act III ≈ 72), so masteries come two or three a chapter. Spells reach 1.7–2.0 Fights and Duos come every two rounds.

**Act IV — everything at once (CH-14–CH-17).** T4, IMPASTO, the secret Scores and the rank-10 upgrades arrive in the chapter with unlimited Evenings; a completionist leaves at Lv 41 with up to 29 Scores. The finale tests width, not one combo: Min-jun's CHRONO, the Octave (15,935 at the canon check) and a full Étude book (*Fugato* 2,348) all matter, and no boss falls in under 4.6 rounds.

**Epilogues and post-game.** Seoul trades Scores for people (Seo-yeon, Jae-won, the Remembrances); Paris keeps the eight and forges Lost Era weapons. The two unfinished works, *Art of Fugue* and *Unfinished*, open T5 for the superbosses and Da Capo, and their last Invocations (PWR 240) are the only summons that outgrow the Synergies.

## Canon Additions & Cross-Doc Notes

**New shared facts (owned here; other docs cite, never redefine):**
- **HRM catalogue:** 31 pool skills HRM-PC00-01–31 (§6) and the innate lists HRM-PC01–PC11 (§7–§15), including skills the canon names only as cures or statuses: *Clarity*, *Encore* (revive at 25% or grant Encore), *Allegro*. *Affects:* party, combat_ensemble, items_and_equipment (no skill shares an item name), art_and_ui (UI-06/07 mocks: OPS-15's real list is Torrent, Ripple, Glaze, Encore).
- **Learning rules:** per-member, per-skill progress shared across Scores; Swooned, Marbled or Unwritten members earn 0 OP; mid-tier status rate ×4; spreadable status skills at Base −15; a Score's chapter replaces the level gate (T5 still needs Lv 41); Signatures scale with the command tier. *Affects:* formulas_and_curves (§5.3, §8.3), combat_ensemble.
- **OPS-01–32** (§4): names, works, sources, Period prices (400–4,200 F), teach lists, shapes, Invocations (§5.1). Secret sources: OPS-25 BOSS-17 with Own Voice ≥ 6; OPS-26 BOSS-40; OPS-27 BOSS-38; OPS-28 BOSS-36; OPS-29 BOSS-37; OPS-30 BQ-PC08 finale; OPS-31 BOSS-31; OPS-32 BOSS-34. **No secret Score is future-drawn (Heat flag 0).** *Affects:* bosses (guaranteed drops), side_and_bond_quests (BQ-PC08 reward), items_and_equipment and salons_duels_and_economy (Period stock, prices, restocks), audio_and_music (Invocation stingers for the period works and OPS-31/32: new MUS-2xx arrangements), dungeons (Lecterns named in §4.2), secrecy_and_trust (transcription cadence §3.5).
- **TUT-01–20** with page locations (§5.2): chests in LOC-P03, P17, P18, P13, P26 quarries and chapel, P38, the Passage de l'Opéra nest; scenes at Pleyel's (Marie Moke-Pleyel), the Salle Pleyel concert, Bercy, the wedding and Berlioz's 30th birthday. *Affects:* dungeons, act2, act3, act4_and_epilogue, side_and_bond_quests (BQ-PC03 steps carry TUT-16, 17, 19).
- **STU-01–36** and 40 Canvas recipes (§10), story recipes *Liberté* (CH-04), *Chios* (CH-08), *Femmes d'Alger* (CH-09), *Sardanapale* (CH-12). The bestiary must give one member of each named family a `STUDY` line on the named action; `bosses.md` does the same for BOSS-09, 10, 11, 12, 15, 18, 24, 26, 33; `dungeons.md` repeats the three P29 families in the merged section. *Affects:* bestiary, bosses, dungeons, side_and_bond_quests (BQ-PC04 steps).
- **ETU-01–12** names and inputs (§11); Alkan's *Psaume*, *Contre-coup*. *Affects:* art_and_ui (input staff), party.
- **Min-jun's CHRONO** by story: *Ritardando* (CH-15, first amalgam zone), *Tempus* (Lv 37 + CH-15), *Accelerando* (CH-16, as the Stilled Hour breaks); they persist into both epilogues. *Affects:* act4_and_epilogue, bosses (BOSS-31/34 bar 3, BOSS-43).
- **Rank-10 upgrades** *Golden Hour*, *Maestro*, *Sang-froid*, *Transcendence*, *Stretto*, *Second Chorus* (§17.2); **Signature effects** (§17.1); Liszt's *Ecstasy* (×0.75 to all, Heat 5); Lucile's 별 *Byeol*. *Affects:* secrecy_and_trust §3.3, party, side_and_bond_quests (each finale names its upgrade).
- **Menu short forms** for all 23 Synergies and 11 Cadenzas (§17.3–17.4), and for long Signatures (*Barque de Dante*, *Étude ut mineur*, *Harm. poétiques*) and Tuttis (§5.2). *Affects:* art_and_ui, combat_ensemble.
- **Julien's reel strips, Jae-won's ring strokes, Czerny's three drills (+1 TMP each, max +3, outside the ledger), GST content** (§15–§16). *Affects:* combat_ensemble, salons_duels_and_economy (*Phrase* drills), act3.
- **System strings** "Mastered: …!", "Transcribed: ✦…!", "New Étude: …!" (§2). *Affects:* dialogue_style_guide §1.4.

**Cross-doc notes (no CCR needed):**
- **combat_ensemble:** please confirm two rulings this doc applies to command content: Invocations cannot be Transcribed by MEPHISTO or paired by TRANSCEND (they are summons); *Estocade* counts as a Fight for *Idée Fixe*. TUT-13 and TUT-14 use the heal/support reading of the Tutti budget (×1/×2/×3 of Hₜ).
- **secrecy_and_trust:** add *Modal Vamp* (Heat 3: jazz harmony) and *Ecstasy* (Heat 5: REP-21) to the §2.4.1 table; skills learned from ✦ Scores carry Heat 0 (only Invocations carry 3).
- **formulas_and_curves:** the ledger split of the 24 regular Scores is ART 4, STR 4, DEF 3, RES 3, TMP 3, HP 3, LCK 2, INS 2; the secret Scores carry two shapes each, as recommended.
- **audio_and_music:** REP-29 joins battle when written (CH-14), matching its cue sheet; REP-25's movements stay Nos. 1, 7, 14.

**CCR (not used here):**
- **CCR: battle effects for REP-27, REP-29, REP-30.** I endorse `combat_ensemble`'s proposal unchanged; until adopted they give only +3 Crescendo per movement (§7.1). *Touches:* CANON §15d, combat_ensemble, audio_and_music.
- **CCR: the HRM-PC00 family number.** CANON §0c gives HRM-PC##-## per member; this doc uses PC00 for skills only Scores teach. Request that §0c note "PC00 = shared pool (skills doc)". *Touches:* CANON §0c only.
