# Items, Equipment & Shops

Status: v1.0 — 2026-10-06 · Owns: every item name (ITM), stat, price and location; shop inventories by chapter; key-item detail (KEY-01–KEY-41 as expanded here); Voicing and keepsake-forge rules; ultimate (Lost Era) equipment and the quests that grant it · Depends on: docs/05_systems/combat_ensemble.md, docs/06_balance/formulas_and_curves.md · Related: docs/05_systems/skills_and_progression.md (owner of every Opus Score), docs/07_world/overworld_and_towns.md (shop placement, map openness by chapter, hidden-item spots), docs/05_systems/secrecy_and_trust.md (gift reactions, Compromised refusals), docs/05_systems/salons_duels_and_economy.md (not yet published; CANON §11g and §14 govern) · Canon: docs/00_CANON.md

## Table of Contents

1. [Scope, Conventions and ID Ranges](#1-scope-conventions-and-id-ranges)
2. [Equipment Slots and Rules](#2-equipment-slots-and-rules)
3. [Weapons](#3-weapons)
4. [Armour: Head and Body](#4-armour-head-and-body)
5. [Relics](#5-relics)
6. [Consumables and Battle Items](#6-consumables-and-battle-items)
7. [Key Items](#7-key-items)
8. [Opus Score Sources](#8-opus-score-sources)
9. [Gifts and Curios](#9-gifts-and-curios)
10. [Shop Inventories by Chapter](#10-shop-inventories-by-chapter)
11. [Rare Items: Steals, Drops, Duel Prizes, Finds](#11-rare-items-steals-drops-duel-prizes-finds)
12. [Lost Era Ultimates and Epilogue-Branch Items](#12-lost-era-ultimates-and-epilogue-branch-items)
13. [Economy Checks](#13-economy-checks)
14. [Canon Additions & Cross-Doc Notes](#canon-additions--cross-doc-notes)

---

## 1. Scope, Conventions and ID Ranges

**What this doc fixes.** Every ITM entry: name, UI name, stats, effect, price, sell value, and every place it can be obtained (shop, chest, steal, drop, quest, story). It also fixes what each canon shop sells in each chapter (CANON §12 names, CANON §14 bands), the Voicing upgrade service, the keepsake forge, and the detail behind every canon KEY item. **It does not fix** formulas (formulas_and_curves), battle rules (combat_ensemble), enemy steal/drop assignments by ENM ID (bestiary; this doc names the items and the families that carry them), chest tiles (dungeons), quest steps (side_and_bond_quests), Opus Scores: titles, teach lists, bonus shapes and the twelve Period Score prices (skills_and_progression owns every OPS; §8 restates its sources), or income tables (salons_duels_and_economy).

**Binding inputs.** Price bands, tiers, slots, anchor consumables, Lost Era names and requirements, and the KEY list: CANON §14. Weapon ATK target ≈ 10 + 2.2L: CANON §10e. Armour DEF/RES targets per tier (head + body, split 40/60), relic DEF/RES budget (+10 each, CH-10 on), weapon-class accuracy: formulas_and_curves §9. Drop and steal odds (rare clamp(4 + ΔLCK/4, 2, 16)%, common 35%, steal 1-in-8 rare with an 8th-success pity): formulas_and_curves §5.4–5.5. Relic keys `ENC_HALF` (×0.5) and `ENC_NONE` (×0): formulas_and_curves §5.7. Formation odds that relics may move: combat_ensemble §5.2. Which Paris districts are open in which chapter: overworld_and_towns §2.2 (Paris is closed to the party in CH-10–CH-11 except Lucile's interlude maps, and in CH-12–CH-13 only P02, P10 and P28 are open, so no Paris weapon, armour, brush or relic counter trades in CH-10–CH-13).

**Display rules (CANON §16h).** Item names ≤ 16 characters plus an 8-px icon. Where a canonical "[Tier] [Class]" name runs longer, the UI uses a short form: tiers abbreviate to *Prél.*, *Noct.*, *Rhap.*, *Conc.*, *Symph.*, and Opus Magnum to *Magnum*; Berlioz's class shows as *Swordcane* (e.g. "Symph. Swordcane", "Magnum Rapier"). The full name appears in the one-line description (≤ 30 characters in the Equip window, CANON §16a no-portrait width) and in the Almanach. Prices under 1 F show in sous ("8s"); everything else in whole francs (CANON §14).

**Selling.** Every item sells for ⌊50%⌋ of its buy price. Items marked **◆ unsellable** (keepsakes, story-given weapons, KEY items) cannot be sold or discarded. Seoul shops buy at the same 50%, in won at ₩200 per franc of list price (CANON §14).

**ID ranges (this doc's ITM family, CANON §0c).**

| Range | Family | Used |
|---|---|---|
| ITM-001–039 | Restoratives and cures (1833–34) | 001–027 |
| ITM-040–059 | Battle items | 040–053 |
| ITM-060–079 | Seoul consumables (CH-E1) | 060–074 |
| ITM-100–399 | Weapons, by class blocks of 30 | see §3 |
| ITM-400–449 | Head armour | 400–429 |
| ITM-450–499 | Body armour | 450–481 |
| ITM-500–569 | Relics | 500–556 |
| ITM-600–679 | Gifts and curios | 600–660 |

Weapon blocks: Batons 100–129 · Brushes 130–159 · Sword-canes 160–189 · Rapiers 190–219 · Hammers 220–249 · Quills 250–279 · Sabres 280–309 · Folios 310–339 · Canes 340–359 · Bows 360–369 · Drumsticks 370–379.

---

## 2. Equipment Slots and Rules

### 2.1 Slots (CANON §14)

Each character has **Weapon, Head, Body, Relic × 2**. Guests cannot be re-equipped (CANON §6). Inventory: 256 slots, 99 per stack; KEY items sit in their own unlimited tab (CANON §14).

| Slot | Gives | Rule |
|---|---|---|
| Weapon | ATK (AR = 2 × ATK + STR, CANON §10b); some add ART+, LCK+, an element, or a rider | One class per character (§2.2); WeaponAcc by class (formulas_and_curves §9), items vary it by at most ±2 |
| Head | DEF, RES; some EVA, M.EVA or a resistance | Universal unless marked |
| Body | DEF, RES; some EVA, M.EVA or a resistance | Universal unless marked |
| Relic ×2 | One effect each (§5); DEF/RES +10 at most, CH-10 on | The same relic cannot be worn twice by one character; CHRONO resistance never stacks (combat_ensemble §8.2) |

**ART+ on weapons.** The canon has no MAG stat; spell power comes from ART (CANON §10a). Caster-class weapons therefore carry a flat **ART+** that is added to the wearer's ART like an Opus ledger point (formulas_and_curves §3.4 rule 3) and counts toward the cap of 99. At T4 and Lv 40, ART is about 21% of the magical term (formulas_and_curves §3.4), so the largest shop ART+ (+7) is worth about 3.5% of spell damage: flavour with a measurable edge, never a second weapon curve.

**Element on a weapon** makes Fight elemental (affinity and Light apply, CANON §10c); a weapon never changes the element of a command or skill.

### 2.2 Weapon class per character (CANON §5a, §14; accuracy formulas_and_curves §9)

| PC | Class | Row-free | WeaponAcc | Secondary stat on the class | Joins with |
|---|---|---|---|---|---|
| PC-01 Min-jun | Batons | Yes | 95 | ART+ | ITM-100 Tuning Fork (CH-P) |
| PC-02 Lucile | Brushes | No | 95 | ART+ | ITM-132 Nocturne Brush (CH-05) |
| PC-03 Berlioz | Sword-canes | No | 95 | — | ITM-160 Étude Sword-cane (CH-02) |
| PC-04 Delacroix | Rapiers | No | 100 | — | ITM-190 Étude Rapier (CH-03) |
| PC-05 Alkan | Hammers | No | 90 | — | ITM-221 Joiner's Mallet (CH-04) |
| PC-06 Chopin | Quills | Yes | 98 | ART+ | ITM-250 Nocturne Quill (CH-06) |
| PC-07 Liszt | Sabres | No | 95 | ART+ (half) | ITM-280 Nocturne Sabre (CH-07) |
| PC-08 Farrenc | Folios | Yes | 98 | ART+ | ITM-310 Rhapsodie Folio (CH-08) |
| PC-09 Seo-yeon | Bows (violin bows) | No | 98 | ART+ | ITM-360 Brazilwood Bow (CH-E1) |
| PC-10 Jae-won | Drumsticks (*janggu* sticks) | No | 95 | — | ITM-370 Yeolchae (CH-E1) |
| PC-11 Julien | Canes | No | 92 | LCK+ | ITM-340 Symphonie Cane (CH-14) |

**Row-free weapons pay for it.** Batons, Quills and Folios ignore the back-row halving (CANON §10b), so their standard line sits 2 ATK under the melee line at the low tiers (never below the canon band) and carries ART+ instead.

### 2.3 Tier ladder and the standard line

Every tier sells one standard "[Tier] [Class]" per class present in that chapter, at the tier's entry; named weapons fill the top of each band. Melee and row-free ATK by tier:

| Tier (CANON §14) | Chapters | Std ATK melee / row-free | Named top of band | Std price | Named price (shop) | ART+ std / top |
|---|---|---|---|---|---|---|
| Étude | CH-01–02 | 16 / 14 | 19 | 80 (row-free 60) | 150 | +1 / +1 |
| Prélude | CH-03–04 | 26 / 24 | 32 | 220 | 380 | +2 / +2 |
| Nocturne | CH-05–07 | 38 / 36 | 45 (row-free 42) | 560 | 980 | +3 / +3 |
| Rhapsodie | CH-08–09 | 52 / 52 | 56 (row-free 54) | 1,150 | 1,380 | +4 / +4 |
| Concerto | CH-10–13 | 66 / 62 | 74 shop, 80 found (row-free 70 / 77) | 2,100 | 2,800 (found items unpriced, sell 1,725) | +5 / +5 |
| Symphonie | CH-14–15 | 86 / 85 | 91 (row-free 89) | 3,900 | 5,100 | +6 / +6 |
| Opus Magnum | CH-16, CH-E2 | 98 / 98 | 105 (row-free 102) | 5,600 | 6,900 | +7 / +7 |
| Seoul modern | CH-E1 | 98 / 98 | 105 (row-free 102) | ₩1,120,000 | ₩1,380,000 | +7 / +7 |
| Lost Era | Epilogues | 150–180 | — | not sold | — | +10 / +12 |

*Anchor check:* the standard line meets CANON §10e's "best shop weapon" at each tier's entry chapter within 3 ATK (CH-05 anchor 36, std 38; CH-08 anchor 52, std 52; CH-14 anchor 85, std 86; CH-16 anchor 98, std 98), and the named top meets the tier's last chapter (CH-07 45; CH-09 56; CH-13 80; CH-15 91; CH-E1/E2 105).

### 2.4 Voicing (weapon refinement)

Pleyel's workshop (LOC-P12) **voices** a weapon: new felt and leather at the grip, the balance re-weighted, the shaft re-trued. The service needs the Pleyel Workshop Pass (KEY-12, CH-05) and opens in **CH-07**, the chapter CANON §4a lists for Pleyel Voicing. Kang Do-hyun gives the same service at Kang Piano Service (LOC-S15) in CH-E1 ("Felt's felt, any century"), and the restored Atelier's Pleyel (LOC-E02) gives it in CH-E2.

| Stage | Effect | Price (Paris) | Price (Seoul) |
|---|---|---|---|
| +1 | ATK +2 | 25% of the weapon's list price | ×200 in won |
| +2 | ATK +4 | +50% | ×200 |
| +3 | ATK +6 | +100% | ×200 |

Rules: stages are bought in order; a fully voiced weapon has cost 175% of its price, which keeps Voicing a money sink rather than a tier skip (+6 ATK is +12 AR: about +9% at CH-09, AR 136 → 148, and +5% at CH-16, AR 231 → 243, where the next tier's standard weapon gives +12 to +20 ATK). Story weapons without a list price are voiced as if priced at their tier's named price. **Lost Era weapons, ITM-100 Tuning Fork and the Seoul Lost Era pieces cannot be voiced.** *Windows:* P12 in CH-07–CH-09 and CH-14 (Paris is closed to the party in CH-10–CH-13), Kang Piano Service in CH-E1, P12 and the restored E02 piano in CH-E2. The stage shows as a suffix in its own column of the Equip window ("+2"), never inside the 16-character name. *Salons note:* this doc defines Voicing for weapons only; if salons_duels_and_economy voices the duel pianos too, it shares the name and this service window.

### 2.5 Keepsake forge (CH-E2, CANON §6, §14)

In the Paris branch, Pleyel and Théo forge each friend's Lost Era weapon in the workshop yard at LOC-P12 when three conditions are met: (1) the friend is at bond **R10** and (2) has finished his or her **bond-quest finale**, and (3) the friend's **KEY-30 keepsake** was received in CH-17. No fee: Pleyel charges nothing for "metal that is not only metal" (historical_cast, NPC-15 line). Forging takes one visit and no Evening (the epilogues have no Evening budget, CANON §11i). A farewell skipped in CH-17 locks that forge until Da Capo (CANON §6). Requirements and effects per weapon: §12. Pleyel's smith works the metal and Théo fits, binds and voices it; Théo casts no brass before the Door's key, his first brass casting, in spring 1834 (CANON LAW-22).

---

## 3. Weapons

Source codes: **Shop** (shop, chapter of first stock), **Chest** (dungeons places the tile in the named LOC), **Steal/Drop** (bestiary assigns the ENM within the named family), **Quest** (side_and_bond_quests places the step), **Story** (automatic). "Sell" is half price; ◆ = unsellable.

### 3.1 Batons — Min-jun (row-free, Acc 95)

| ITM | Name (UI) | ATK | ART+ | Element / effect | Source | Price |
|---|---|---|---|---|---|---|
| 100 | Tuning Fork | 12 | +1 | REP-00 *Resonance* Stun base +10 · "It hums before it strikes." | Story CH-P (on his person, CANON §5f) | ◆ |
| 101 | Étude Baton | 14 | +1 | — | Shop: Armurerie Vidal CH-02 | 60 |
| 102 | Prélude Baton | 24 | +2 | — | Shop: Armurerie Vidal CH-03 | 220 |
| 103 | Berlioz's Baton | 30 | +2 | Each Conduct adds +5 Crescendo · "From the barricade, with love." | Story, end of CH-04 (CANON §4b); becomes ITM-112 in CH-14 | ◆ |
| 104 | Nocturne Baton | 36 | +3 | — | Shop: Vidal CH-05 | 560 |
| 105 | Ebony Baton | 42 | +3 | Recital Movement I costs −2 INS | Shop: Vidal & Fils CH-07 | 980 |
| 106 | Rhapsodie Baton | 52 | +4 | — | Shop: Vidal CH-08 | 1,150 |
| 107 | Silver Baton | 54 | +4 | Recital III bursts +10% | Shop: Vidal & Fils CH-09 · Chest: P31 Bercy | 1,380 |
| 108 | Concerto Baton | 62 | +5 | — | Shop: Lambotte CH-11 (CCR) · Chest: R05 Vallée Noire (CH-10) | 2,100 |
| 109 | Rehearsal Baton | 70 | +5 | A Recital breaks only on a hit ≥ 30% of max HP (not 20%) | Shop: Lambotte CH-11 (CCR) | 2,800 |
| 110 | Gala Baton | 77 | +5 | Fight is LIGHT | Chest: P27 corridors (CH-13) | — (sell 1,725) |
| 111 | Symphonie Baton | 85 | +6 | — | Shop: Vidal CH-14 | 3,900 |
| 112 | Mended Baton | 89 | +6 | A Conducted ally also gains Swell +1 · "Théo re-trued the crack." | Story CH-14: Théo re-trues ITM-103, cracked parrying a blade in the CH-13 rafters (§12.2) | ◆ |
| 113 | Opus Magnum Baton (Magnum Baton) | 98 | +7 | — | Chest: P29 Hanseong zone (CH-15) · Shop: Vidal CH-E2 | 5,600 |
| 114 | Ivory Baton | 102 | +7 | Recital Movement I costs −4 INS | Shop: Vidal & Fils CH-E2 | 6,900 |
| 115 | Graphite Baton | 98 | +7 | — | Shop: Kang Piano Service CH-E1 | ₩1,120,000 |
| 116 | Ash Baton | 102 | +7 | Recital III bursts +10% · Do-hyun's own turning | Shop: Kang Piano Service CH-E1 | ₩1,380,000 |
| 129 | **Baton of Tomorrow** (Tomorrow Baton) | 150 | +12 | Lost Era (§12) | BOSS-31 or BOSS-34 | ◆ |

### 3.2 Brushes — Lucile (melee, Acc 95)

Couleurs Ravenel (rue de Seine, LOC-P22) stocks every Paris brush; Lucile will not enter Maison Grimaud (CANON §12).

| ITM | Name (UI) | ATK | ART+ | Element / effect | Source | Price |
|---|---|---|---|---|---|---|
| 132 | Nocturne Brush | 36 | +3 | — | Joins with it (CH-05) · Ravenel CH-05 | 560 |
| 133 | Kolinsky Filbert | 42 | +3 | IMPRESSION +10% | Ravenel CH-07 | 980 |
| 134 | Rhapsodie Brush | 52 | +4 | — | Ravenel CH-08 | 1,150 |
| 135 | Badger Blender | 54 | +4 | *Shift the Hour* also gives her Cantabile | Ravenel CH-08 (she leaves at the CH-09 dawn) | 1,380 |
| 136 | Nohant Sable | 66 | +5 | POINTILLÉ +10% · "Ma petite Lumière. — G." | Story CH-10: Sand's gift at Nohant after Mending scene 1; becomes ITM-159 at LUMIÈRE (§12.3) | ◆ |
| 137 | Concerto Brush | 62 | +5 | — | Weiss CH-11 (CCR; bought ahead, Lucile is in Paris) | 2,100 |
| 138 | Munich Sable | 70 | +5 | Plein Air +25% also under Dusk | Weiss CH-11 (CCR) | 2,800 |
| 139 | Palette Knife | 77 | +5 | Fight ignores 25% of DEF | Chest: P26 abbey wing, Lucile's CH-12 solo | — (sell 1,725) |
| 140 | Symphonie Brush | 85 | +6 | — | Ravenel CH-14 | 3,900 |
| 141 | Harbour Brush | 91 | +6 | IMPASTO and *Nuit étoilée* +10% | Quest: BQ-PC02b finale, Le Havre (LOC-R12) | ◆ |
| 142 | Opus Magnum Brush (Magnum Brush) | 98 | +7 | — | Chest: P29 Lutèce zone (CH-15) · Ravenel CH-E2 | 5,600 |
| 143 | Lumière Sable | 102 | +7 | LUMIÈRE costs −25% INS | Ravenel CH-E2 · Atelier easel (E02, restored) | 6,900 |
| 144 | Synthetic Flat | 98 | +7 | — | Hanji-bang CH-E1 (CCR; fallback §10.8) | ₩1,120,000 |
| 145 | Weasel-Hair But | 102 | +7 | Each Hanmadi word learned: her styles +0.25% (max +10%) · 붓 *but*, "brush" | Hanji-bang CH-E1 (CCR; fallback §10.8) | ₩1,380,000 |
| 159 | **Pinceau Lumière** | 158 | +12 | Lost Era (§12) | Story, both epilogues (§12.3) | ◆ |

### 3.3 Sword-canes — Berlioz (melee, Acc 95)

| ITM | Name (UI) | ATK | Element / effect | Source | Price |
|---|---|---|---|---|---|
| 160 | Étude Sword-cane | 16 | — | Joins with it (end CH-02) · Vidal CH-02 | 80 |
| 161 | Rome Sword-cane | 19 | Idée Fixe stack 1 starts at battle start · "Carried home from the Villa Medici." | Chest: P04 cellars (CH-02) | — (sell 75) |
| 162 | Prélude Sword-cane (Prél. Swordcane) | 26 | — | Vidal CH-03 | 220 |
| 163 | Malacca Sword-cane | 32 | — | Vidal CH-04 | 380 |
| 164 | Nocturne Sword-cane (Noct. Swordcane) | 38 | — | Vidal CH-05 | 560 |
| 165 | Dandy's Sword-cane | 45 | Idée Fixe max 4 stacks | Vidal & Fils CH-07 | 980 |
| 166 | Rhapsodie Sword-cane (Rhap. Swordcane) | 52 | — | Vidal CH-08 · Coutellerie CH-08 | 1,150 |
| 167 | Ophelia Cane | 56 | Fight is WATER · "Harriet's wedding gift." | Story CH-09: Harriet's gift at the British Embassy, Thu 3 Oct | ◆ |
| 168 | Concerto Sword-cane (Conc. Swordcane) | 66 | — | Lambotte CH-11 (CCR; Berlioz is in Paris, buy ahead) | 2,100 |
| 169 | Francs-juges Cane | 74 | Tutti +10% | Lambotte CH-11 (CCR) | 2,800 |
| 170 | Rob Roy Cane | 80 | Cue: Brass also gives Berlioz Fortissimo | Chest: P27 rafters (CH-13) | — (sell 1,725) |
| 171 | Symphonie Sword-cane (Symph. Swordcane) | 86 | — | Coutellerie CH-14 | 3,900 |
| 172 | Waverley Cane | 91 | Idée Fixe max 4 stacks; Fight crit +5 points | Coutellerie CH-14 · Chest: R02 Château d'Orsenne | 5,100 |
| 173 | Opus Magnum Sword-cane (Magnum Swordcane) | 98 | — | Chest: P29 Orpheus zone · Coutellerie CH-E2 | 5,600 |
| 174 | Sabbath Cane | 105 | Fight is SHADE; Tutti +10% | Coutellerie CH-E2 | 6,900 |
| 189 | ***Idée Fixe*** | 175 | Lost Era (§12) | Forge CH-E2 | ◆ |

### 3.4 Rapiers — Delacroix (melee, Acc 100)

| ITM | Name (UI) | ATK | Element / effect | Source | Price |
|---|---|---|---|---|---|
| 190 | Étude Rapier | 19 | — | Joins with it (CH-03) | — (sell 75) |
| 191 | Prélude Rapier | 26 | — | Vidal CH-03 | 220 |
| 192 | Meknès Blade | 32 | Fight is FIRE · "Morocco, 1832." | Quest: BQ-PC04, first step (CH-03–04) | ◆ |
| 193 | Nocturne Rapier | 38 | — | Vidal CH-05 | 560 |
| 194 | Salon Épée | 45 | Canvas +10% | Vidal & Fils CH-07 | 980 |
| 195 | Rhapsodie Rapier | 52 | — | Vidal CH-08 | 1,150 |
| 196 | Chios Rapier | 54 | Fight is ICE | Chest: P17 sewers (CH-08) | — (sell 690) |
| 197 | Algiers Rapier | 56 | Fight is LIGHT; Sketch also reveals steals | Quest: BQ-PC04 finale (by CH-09, mandatory) | ◆ |
| 198 | Concerto Rapier | 66 | — | Lambotte CH-11 (CCR; Delacroix is in Paris, buy ahead) | 2,100 |
| 199 | Sardanapalus Rapier (Sardanapale) | 74 | Fight is FIRE; Canvas *Sardanapale* +10% | Lambotte CH-11 (CCR) | 2,800 |
| 200 | Tableau Rapier | 80 | Chiaroscuro counter chance 40% (from 25%) | Drop: Living Tableaux, P26 (rare) | — (sell 1,725) |
| 201 | Symphonie Rapier | 86 | — | Vidal CH-14 | 3,900 |
| 202 | Palais Rapier | 91 | Canvas +10% | Vidal & Fils CH-14 | 5,100 |
| 203 | Opus Magnum Rapier (Magnum Rapier) | 98 | — | Chest: P29 Lutèce zone · Vidal CH-E2 | 5,600 |
| 204 | Missolonghi Rapier | 105 | Fight is WIND; Canvas +10% | Vidal & Fils CH-E2 | 6,900 |
| 219 | ***Liberté*** | 172 | Lost Era (§12) | Forge CH-E2 | ◆ |

### 3.5 Hammers — Alkan (melee, Acc 90)

| ITM | Name (UI) | ATK | Element / effect | Source | Price |
|---|---|---|---|---|---|
| 220 | Prélude Hammer | 26 | — | Vidal CH-04 | 220 |
| 221 | Joiner's Mallet | 30 | — | Joins with it (end CH-04) | — (sell 190) |
| 222 | Nocturne Hammer | 38 | — | Vidal CH-05 | 560 |
| 223 | Forge Hammer | 45 | Fight is EARTH | Vidal & Fils CH-07 | 980 |
| 224 | Rhapsodie Hammer | 52 | — | Coutellerie CH-08 | 1,150 |
| 225 | Spike Maul | 56 | Études +5% | Quest: BQ-PC05, second step | ◆ |
| 226 | Concerto Hammer | 66 | — | Lambotte CH-11 (CCR) | 2,100 |
| 227 | Liège Hammer | 74 | Recluse also triggers when he is the only member in the front row | Lambotte CH-11 (CCR) | 2,800 |
| 228 | Seraing Maul | 80 | Fight is BOLT | Chest: R08 *Concordia* boiler deck (CH-11) | — (sell 1,725) |
| 229 | Symphonie Hammer | 86 | — | Coutellerie CH-14 | 3,900 |
| 230 | Machine Hammer | 91 | Études +5%; Acc 92 | Coutellerie CH-14 | 5,100 |
| 231 | Opus Magnum Hammer (Magnum Hammer) | 98 | — | Chest: P29 Orpheus zone · Coutellerie CH-E2 | 5,600 |
| 232 | Ostinato Hammer | 105 | Études +5%; Stun on Fight (base 20) | Coutellerie CH-E2 | 6,900 |
| 249 | ***Pédalier*** | 180 | Lost Era (§12) | Forge CH-E2 | ◆ |

### 3.6 Quills — Chopin (row-free, Acc 98)

| ITM | Name (UI) | ATK | ART+ | Element / effect | Source | Price |
|---|---|---|---|---|---|---|
| 250 | Nocturne Quill | 36 | +3 | — | Joins with it (CH-06) · Vidal CH-06 | 560 |
| 251 | Steel Nib | 42 | +3 | His heals +10% | Vidal & Fils CH-07 | 980 |
| 252 | Rhapsodie Quill | 52 | +4 | — | Vidal CH-08 | 1,150 |
| 253 | Ballade Quill | 54 | +4 | *Borrow* also inflicts Lento (base 40) | Quest: BQ-PC06 finale (by CH-09, mandatory) | ◆ |
| 254 | Concerto Quill | 62 | +5 | — | Lambotte CH-11 (CCR) | 2,100 |
| 255 | Mazurka Quill | 70 | +5 | *Repay* with 3 charges also gives Allegro | Lambotte CH-11 (CCR) | 2,800 |
| 256 | Liège Goose Quill | 77 | +5 | Sotto Voce targeting weight 0.4 (from 0.5) | Story CH-11: César Franck's father gives it at Liège when Chopin joins | ◆ |
| 257 | Symphonie Quill | 85 | +6 | — | Vidal CH-14 | 3,900 |
| 258 | Polonaise Quill | 89 | +6 | His heals +10%; M.EVA +5 | Vidal & Fils CH-14 | 5,100 |
| 259 | Opus Magnum Quill (Magnum Quill) | 98 | +7 | — | Chest: P29 Hanseong zone · Vidal CH-E2 | 5,600 |
| 260 | Fantaisie Quill | 102 | +7 | *Repay* +1 charge once per battle | Vidal & Fils CH-E2 | 6,900 |
| 279 | ***Żelazowa*** | 150 | +12 | Lost Era (§12) | Forge CH-E2 | ◆ |

### 3.7 Sabres — Liszt (melee, Acc 95; ART+ at half the caster value)

| ITM | Name (UI) | ATK | ART+ | Element / effect | Source | Price |
|---|---|---|---|---|---|---|
| 280 | Nocturne Sabre | 38 | +2 | — | Joins with it (CH-07) · Vidal CH-07 | 560 |
| 281 | Hussar Sabre | 45 | +2 | Bravura max +60% | Vidal & Fils CH-07 | 980 |
| 282 | Rhapsodie Sabre | 52 | +2 | — | Coutellerie CH-08 | 1,150 |
| 283 | Fantastique Sabre | 56 | +2 | TRANSCEND costs ×1.4 INS (not ×1.5) | Coutellerie CH-09 | 1,380 |
| 284 | Concerto Sabre | 66 | +3 | — | Lambotte CH-11 (CCR) · Chest: R05 Vallée Noire (CH-10) | 2,100 |
| 285 | Liège Sabre | 74 | +3 | Fight is BOLT | Lambotte CH-11 (CCR) | 2,800 |
| 286 | Opéra Sabre | 80 | +3 | Bravura does not reset on the first hit taken each battle | Chest: P27 stage machinery (CH-13) | — (sell 1,725) |
| 287 | Symphonie Sabre | 86 | +3 | — | Coutellerie CH-14 | 3,900 |
| 288 | Cambridge Sabre | 91 | +3 | Riposte: counters physical hits 20% · "Vane's, as a Blue." | Prize: BOSS-20 won, CH-14 (Vane surrenders it when he defects) | ◆ |
| 289 | Opus Magnum Sabre (Magnum Sabre) | 98 | +4 | — | Chest: P29 Orpheus zone · Coutellerie CH-E2 | 5,600 |
| 290 | Magyar Sabre | 105 | +4 | Bravura max +60%; Fight is FIRE | Coutellerie CH-E2 | 6,900 |
| 309 | ***Mephisto*** | 170 | +10 | Lost Era (§12) | Forge CH-E2 | ◆ |

*Cambridge Sabre if BOSS-20 is lost:* Vane still defects (the story continues, CANON §11g) and leaves the sabre on the shuttered hall table at LOC-P14 (WS-17), so it is never missable.

### 3.8 Folios — Farrenc (row-free, Acc 98)

Maison Farrenc (LOC-P19) sells Folios beside its Opus Scores: bound engraved plates, brass-cornered, the publisher's own stock.

| ITM | Name (UI) | ATK | ART+ | Element / effect | Source | Price |
|---|---|---|---|---|---|---|
| 310 | Rhapsodie Folio | 52 | +4 | — | Joins with it (CH-08) · Maison Farrenc CH-08 | 1,150 |
| 311 | Engraver's Folio | 54 | +4 | *Annotate* costs 0 INS | Maison Farrenc CH-09 | 1,380 |
| 312 | Concerto Folio | 62 | +5 | — | Lambotte CH-11 (CCR) · Maison Farrenc CH-12 | 2,100 |
| 313 | Copperplate Folio | 70 | +5 | *Canon* echoes at ×1.2 | Maison Farrenc CH-12 | 2,800 |
| 314 | Haydn Folio | 77 | +5 | *Fugue* +10% | Chest: R07 Düsseldorf Academy library (CH-11) | — (sell 1,725) |
| 315 | Symphonie Folio | 85 | +6 | — | Maison Farrenc CH-14 | 3,900 |
| 316 | Hummel Folio | 89 | +6 | *Cadence* heal +20% | Maison Farrenc CH-14 | 5,100 |
| 317 | Opus Magnum Folio (Magnum Folio) | 98 | +7 | — | Chest: P29 Lutèce zone · Maison Farrenc CH-E2 | 5,600 |
| 318 | Overture Folio | 102 | +7 | *Annotate* places 4 crit marks | Maison Farrenc CH-E2 (with the Overture No. 1 proofs, CANON §15e) | 6,900 |
| 339 | ***Trésor*** | 152 | +12 | Lost Era (§12) | Forge CH-E2 | ◆ |

### 3.9 Canes — Julien (melee, Acc 92)

| ITM | Name (UI) | ATK | LCK+ | Element / effect | Source | Price |
|---|---|---|---|---|---|---|
| 340 | Symphonie Cane | 85 | +3 | — | Joins with it (CH-14, SQ-21) · Coutellerie CH-14 | 3,900 |
| 341 | Ivory-Knob Cane | 91 | +3 | Sideman +25% (from +20%) | Coutellerie CH-14 | 5,100 |
| 342 | Opus Magnum Cane (Magnum Cane) | 98 | +4 | — | Chest: P29 Orpheus zone · Coutellerie CH-E2 | 5,600 |
| 343 | Boulevard Cane | 105 | +4 | IMPROVISE *Blue Note* +20% | Story CH-E2: E04 *Le Diapason Bleu* opening night (1 Jan 1834) | ◆ |
| 359 | ***Blue Note*** | 165 | +8 | Lost Era (§12) | Forge CH-E2 | ◆ |

### 3.10 Bows and Drumsticks — Seoul members (CH-E1 only)

Kang Piano Service (LOC-S15) re-hairs bows and turns sticks: the canon "weapon upgrades" vendor (CANON §12) sells the Seoul weapon line and voices any weapon.

| ITM | Name (UI) | Class | ATK | Stat+ | Effect | Source | Price |
|---|---|---|---|---|---|---|---|
| 360 | Brazilwood Bow | Bow | 98 | ART+7 | — | Joins with it | — (sell ₩560,000) |
| 361 | Pernambuco Bow | Bow | 105 | ART+7 | Sostenuto chain starts at +25% | Kang Piano Service | ₩1,380,000 |
| 369 | ***Hanseong*** | Bow | 162 | ART+10 | Lost Era (§12) | Busking ladder, Legend rank | ◆ |
| 370 | Yeolchae | Sticks | 98 | — | — (the club's practice pair) | Joins with it | — (sell ₩560,000) |
| 371 | Birch Gungchae | Sticks | 105 | — | BEAT Good window ±10 frames (from ±8) | Kang Piano Service | ₩1,380,000 |
| 379 | ***Sinmyeong*** | Sticks | 170 | — | Lost Era (§12) | Drop: BOSS-31 | ◆ |

---

## 4. Armour: Head and Body

Targets (formulas_and_curves §9): each tier's standard head + body pair lands inside the head + body DEF/RES band, split about 40/60. Standard pieces are universal; named pieces may carry an equip list (FF6-style) and one rider. Period cut first, game logic second: a "Coat" is a frock coat, redingote or spencer cut for whoever wears it, so the universal line needs no gendered duplicate.

### 4.1 Standard line (universal)

| Tier | Head (ITM, name, DEF/RES, price) | Body (ITM, name, DEF/RES, price) | Pair DEF/RES | §9 band DEF / RES |
|---|---|---|---|---|
| Étude | 400 Étude Cap 1/0, 45 | 450 Étude Coat 1/1, 80 | 2/1 | 1–2 / 0–1 |
| Prélude | 402 Prélude Hat 2/1, 160 | 452 Prélude Coat 3/2, 240 | 5/3 | 3–6 / 1–3 |
| Nocturne | 405 Nocturne Hat 4/3, 380 | 455 Nocturne Coat 6/4, 520 | 10/7 | 8–12 / 5–8 |
| Rhapsodie | 409 Rhapsodie Hat 6/5, 820 | 459 Rhapsodie Coat 10/7, 980 | 16/12 | 15–17 / 11–13 |
| Concerto | 412 Concerto Hat 9/6, 1,500 | 463 Concerto Coat 13/10, 1,700 | 22/16 | 19–28 / 15–22 |
| Symphonie | 417 Symphonie Hat 12/10, 2,800 | 469 Symphonie Coat (Symph. Coat) 19/15, 3,000 | 31/25 | 30–33 / 24–27 |
| Opus Magnum | 421 Magnum Hat 15/12, 4,000 | 473 Magnum Coat 22/18, 4,200 | 37/30 | 36–39 / 29–32 |
| Seoul modern | 425 Beanie 15/12, ₩800,000 | 477 Winter Parka 23/19, ₩880,000 | 38/31 | 38–39 / 31–32 |

### 4.2 Named head armour

| ITM | Name (UI) | DEF/RES | Rider | Who | Source | Price |
|---|---|---|---|---|---|---|
| 401 | Workman's Cap | 1/1 | — | All | Chest: P01 Saint-Denis Galleries (CH-01) | — (sell 20) |
| 403 | Felt Beret | 2/2 | ART +1 | All | Vidal CH-04 | 280 |
| 404 | Ultramarine Scarf | 3/4 | Plein Air preemptive bonus also indoors · "Faded, and hers." | LU | Story: joins wearing it (CH-05); ◆ | ◆ |
| 406 | Beaver Top Hat | 5/3 | Immune to Smoke | Men | Vidal & Fils CH-05 (the Faubourg dress code) | 780 |
| 407 | Poke Bonnet | 4/4 | Immune to Reverie | LU, FA | Vidal & Fils CH-05 | 760 |
| 408 | Moroccan Cap | 5/4 | M.EVA +5 | DE, LI, AL | Quest: BQ-PC04, second step | ◆ |
| 410 | Fencing Mask | 7/4 | Physical counter damage taken −50% (Riposte, Chiaroscuro and Libretto `ON HIT`) | BE, DE, LI, AL | Coutellerie CH-08 | 1,050 |
| 411 | Lace Cap | 6/6 | Immune to Hush | All | Vidal & Fils CH-09 | 1,100 |
| 413 | Rhine Cap | 10/7 | Immune to Lento | All | Lambotte CH-11 (CCR) | 2,200 |
| 414 | Pelisse Hood | 9/9 | Immune to Out of Tune and Discord | All except MJ (already immune) | Weiss CH-11 (CCR) | 2,400 |
| 415 | Grey Kid Cap | 11/8 | Immune to Stagefright | All | Steal: Grey Hand elites, W01 Shadow formations (CH-09+) and P30 (rare); steal-only (§11.4) | — (sell 1,250) |
| 416 | Opera Hat | 11/8 | M.EVA +5 | Men | Chest: P27 cloakroom (CH-13) | — (sell 1,300) |
| 418 | Astrakhan Hat | 13/11 | Immune to Lento | All | Vidal & Fils CH-14 | 3,600 |
| 419 | Silk Bonnet | 12/12 | Immune to Hush, Reverie | All | Vidal & Fils CH-14 | 3,800 |
| 420 | Lutèce Helm | 14/10 | DEF +5 under Gloom | All | Drop: BOSS-22 guaranteed (bosses binds) | ◆ |
| 422 | Laurel Circlet | 16/13 | Crit +5 points | All | Vidal & Fils CH-E2 | 4,900 |
| 423 | Winter Bonnet | 15/14 | Immune to Miasma, Smoke | All | Vidal & Fils CH-E2 | 5,000 |
| 426 | Earmuffs | 15/13 | Immune to Reverie, Hush | All | Gyeoul Outfitters CH-E1 (CCR) | ₩960,000 |

### 4.3 Named body armour

| ITM | Name (UI) | DEF/RES | Rider | Who | Source | Price |
|---|---|---|---|---|---|---|
| 451 | Bottle-Green Frock | 2/1 | — · "Too big. Kindly meant." | MJ | Story CH-02: Mère Gaudin's late husband's coat (CANON §5g) | ◆ |
| 453 | Smock of Daubrée's | 3/3 | ART +1 | LU, DE, FA | Vidal CH-04 | 300 |
| 454 | Midnight Tailcoat | 7/5 | M.EVA +5 · "Vane's tailor. Kept anyway." | MJ | Story CH-05 (CANON §5g) | ◆ |
| 456 | Spencer Jacket | 6/6 | EVA +5 | All | Vidal & Fils CH-05 | 680 |
| 457 | Redingote | 8/5 | Immune to Smoke | All | Vidal & Fils CH-06 | 800 |
| 458 | Copyist's Apron | 6/7 | Canvas and Plein Air +5% | LU, DE | Chest: P13 Louvre (CH-06) | — (sell 380) |
| 460 | Fencing Jacket | 12/6 | Physical damage taken −10% | BE, DE, LI, AL | Coutellerie CH-08 | 1,100 |
| 461 | Moiré Gown | 9/9 | M.EVA +5 | LU, FA | Vidal & Fils CH-08 | 1,050 |
| 462 | Wedding Waistcoat | 10/8 | Party Crescendo +10 at battle start | BE | Story CH-09 (Berlioz wears it out of his own wedding) | ◆ |
| 464 | Travelling Cloak | 14/11 | Immune to Lento | All | Lambotte CH-11 (CCR) | 2,300 |
| 465 | Berry Smock | 13/12 | Dawn regeneration doubled for the wearer | All | Mercerie Aubert CH-10 (CCR) | 2,200 |
| 466 | Buff Coat | 17/11 | Physical damage taken −10% | BE, DE, LI, AL, JW | Lambotte CH-11 (CCR) | 2,600 |
| 467 | Sylphide Gauze | 14/14 | EVA +5, M.EVA +5 | LU, FA, CH | Chest: P27 rafters, Taglioni's dressing room (CH-13) | — (sell 1,300) |
| 468 | Riverman's Oilskin | 15/12 | Immune to the Rain field's Soaked (combat_ensemble §10.2) | All | Chest: R08 *Concordia* (CH-11) | — (sell 1,200) |
| 470 | Greatcoat | 20/14 | Physical damage taken −10% | BE, DE, LI, AL, JU | Coutellerie CH-14 | 3,800 |
| 471 | Velvet Gown | 18/18 | M.EVA +8 | LU, FA | Vidal & Fils CH-14 | 4,000 |
| 472 | Frock of Hanseong | 19/16 | Immune to CHRONO's Unwritten | All except MJ | Drop: BOSS-23 guaranteed (bosses binds) | ◆ |
| 474 | Atelier Smock | 22/19 | Plein Air and Canvas +10% | LU, DE | Atelier easel (E02, restored) CH-E2 | 5,000 |
| 475 | Dress Coat of 1834 | 23/19 | Immune to Stagefright, Hush | All | Vidal & Fils CH-E2 | 5,200 |
| 476 | Cuirassier's Vest | 24/16 | Physical damage taken −15% | BE, DE, LI, AL, JU | Coutellerie CH-E2 | 5,200 |
| 478 | Long Padding | 24/19 | Immune to Lento, Fermata | All | Gyeoul Outfitters CH-E1 (CCR) | ₩1,040,000 |
| 479 | Navy Padded Jacket | 23/19 | Wearer gains Swell +1 at battle start · "Where it all began." | MJ | Story CH-E1: his own jacket, back from 1833 (§7, KEY-tab note) | ◆ |
| 480 | Cream Coat | 23/20 | Her styles +5% · Seo-yeon's coat (CANON §5g) | LU | Story CH-E1: Seo-yeon lends it on the first evening | ◆ |
| 481 | Club Hanbok Vest | 24/17 | Groove: Crescendo gains ×1.30 (from ×1.25) | JW | Story CH-E1: the samulnori club's performance vest | ◆ |

*Navy Padded Jacket (CH-P–CH-01).* In CH-P and CH-01 Min-jun's body slot holds the same jacket at DEF 1/RES 1. In CH-02 the story swaps it for the Bottle-Green Frock and moves it to the KEY tab as a memento ("Too warm, too strange, too much 2026"); in CH-E1 it returns to the Equip list at the stats above. It never appears in a Paris shop's sell list.

---

## 5. Relics

FF6 relic analogues in period dress. Relic prices follow the CANON §14 band of the tier in which they are first sold; Étude has no relic for sale (the Cartouche Glove is found). Effects use combat_ensemble and formulas_and_curves terms exactly; percentage stat modifiers change only the stat they name (formulas_and_curves §3.4).

| ITM | Name (UI) | FF6 analogue | Effect | First source | Price |
|---|---|---|---|---|---|
| 500 | Cartouche Glove | Thief Glove | Adds **Pilfer** to the side menu (CANON §11a) | Chest: P04 cellars (CH-02), canon | — (sell 150) |
| 501 | Busker's Bowl | Coin Toss | Francs after battle ×1.5 (not cumulative) | Story CH-02: Mère Gaudin, after the first T1 salon · "Soup for a tune. Coins for two." | ◆ |
| 502 | Courier's Boots | Sprint Shoes | Field walking speed ×1.5 (not on overworlds while riding) | Corbel CH-04 | 450 |
| 503 | Opera Glass | Sniper Sight | Physical hit +20 points, inside the clamp | Corbel CH-04 | 600 |
| 504 | Herz Medal | — | EVA +5, M.EVA +5 | Prize: BOSS-03 (any result) | ◆ |
| 505 | Fencing Glove | Black Belt | 25% chance to counter a physical hit with Fight | Corbel CH-04 | 750 |
| 506 | Practice Mute | Charm Bangle | `ENC_HALF`: random encounters ×0.5 | Corbel CH-05 | 1,600 |
| 507 | Rosin Cake | — | Crit +10 points | Corbel CH-05 | 1,200 |
| 508 | Watch Lantern | Back Guard | No Back Attack and no Pincer (combat_ensemble §5.2) | Corbel CH-06 | 1,500 |
| 509 | Dancing Pumps | — | EVA +10 | Vidal & Fils CH-07 | 1,800 |
| 510 | Rossini's Napkin | — | After each victory the wearer regains 10% max HP · "Stains from a famous supper." | Prize: BOSS-08 won (Rossini) | ◆ |
| 511 | Three-Hand Glove | — | Fight becomes EARTH / LIGHT / WIND, best multiplier applies (dual rule, CANON §10c) | Prize: BOSS-08 lost (Thalberg's courtesy) · or BOSS-35 won, if not yet owned (§11.3) | ◆ |
| 512 | Pleyel Tuning Hammer (Tuning Hammer) | — | **CHRONO resist ×0.5** (CANON §10c); immune to Lento | Story CH-08: Pleyel's thanks after the Sat 21 Sep concert (KEY-17) | ◆ |
| 513 | Copal Varnish | auto-Protect | Wearer starts each battle with **Varnish** | Corbel CH-08 | 2,200 |
| 514 | Tortoise Fan | — | EVA +8, M.EVA +8 | Corbel CH-08 | 2,000 |
| 515 | Postilion Boots | Hermes Sandals | Wearer starts each battle with **Allegro** | Corbel CH-09 | 2,400 |
| 516 | Shepherd's Bell | Tintinnabar | Wearer regains 1 HP per field step | Story CH-10: Père Grillon at Nohant, after Lucile's Pissarro-style Berry canvas | ◆ |
| 517 | Steel Busk | — | DEF +10 | Lambotte CH-11 (CCR) · Corbel CH-14 | 2,800 |
| 518 | Lodestone Charm | — | RES +10 | Weiss CH-11 (CCR) · Corbel CH-14 | 2,800 |
| 519 | Huntsman's Horn | — | Preemptive +10 points (cap 40%, formulas_and_curves §4.10) | Chest: R01 Franchard gorge (CH-10) · Weiss CH-11 (CCR) · Corbel CH-14 | 3,000 |
| 520 | Smith's Wristband | Hyper Wrist | STR +15% | Weiss CH-11 (CCR) · Corbel CH-14 | 3,400 |
| 521 | Ivory Hairpin | Gold Hairpin | INS costs ×0.75 | Weiss CH-11 (CCR) · Corbel CH-14 | 4,200 |
| 522 | Academy Medal | Earring | Magical damage dealt +15% | Weiss CH-11 (CCR) · Corbel CH-14 | 4,000 |
| 523 | Gilder's Leaf | Barrier Ring (auto-Shell) | Wearer starts each battle with **Glaze** | Weiss CH-11 (CCR) · Corbel CH-14 | 3,800 |
| 524 | Grey Kid Glove | — | Crescendo gains from this wearer ×1.25 (not with Groove) | Steal: Grey Hand, P31, P26, P27 (rare) · Drop: Grey Hand elites (rare) · BOSS-19 (guaranteed) | — (sell 1,500) |
| 525 | Brass Escapement | — | Wearer's battle-start gauge is at least 128 | Drop: Brücke Mk. I automata, P18 (rare) · Steal: river automata, R08 | — (sell 1,200) |
| 526 | Garde Gorget | True Knight | Wearer intercepts single-target hits on allies below 25% HP (as Bulwark, without the −50%) | Steal: Roussel's Cleaners, P34, and BOSS-21 (rare); steal-only (§11.4) | — (sell 2,500) |
| 527 | Sylphide Ribbon | Ribbon | Immune to Smoke, Hush, Reverie, Delirium, Stagefright, Lento, Marble, Frenzy, Out of Tune, Discord, Swing, Miasma | Story CH-13: Taglioni (NPC-37) ties it on Lucile's wrist after the gala | ◆ |
| 528 | Nohant Metronome | — | **CHRONO resist ×0.5** (canon); immune to Swing · "Pour celui qui bat mal la mesure. — G." | Find: Sand's piano at Nohant, CH-14 revisit (overworld_and_towns §7) | ◆ |
| 529 | Venetian Mirror | Wall Ring | Wearer starts each battle with **Mirror** | Corbel CH-14 | 6,500 |
| 530 | Encore Locket | Reraise | Wearer starts each battle with **Encore** | Corbel CH-14 | 7,800 |
| 531 | Paganini String | Offering | Fight strikes 4 times, each ×0.5, never crits | Drop: BOSS-36 guaranteed (bosses binds) | ◆ |
| 532 | Felted Clapper | Moogle Charm | `ENC_NONE`: no random encounters (scripted, touch and boss battles still occur) | Story CH-14: Jacquot at Notre-Dame's bell chamber (LOC-P32) | ◆ |
| 533 | Premier Prix | Exp. Egg | EXP received ×1.5 | Story CH-14: Cherubini, after Hiller's concert (Sun 15 Dec), "an old prize nobody claimed" | ◆ |
| 534 | Fouine's Ring | Sneak Ring | Pilfer success +20 points | Trade CH-14: La Fouine (TF-018, P10) sells it once the party has landed 20 successful Pilfers | 3,000 |
| 535 | Belgiojoso Cameo | — | M.EVA +15; immune to Hush | Prize: SQ-20 completion (CH-14) · or BOSS-35 won in CH-E2 if SQ-20 was skipped (§11.3) | ◆ |
| 536 | Clef Chip | — | Wearer's CHRONO damage dealt +20% | Drop: Amalgam Echoes, P29 (rare) | — (sell 3,500) |
| 537 | Golden Lyre | Economizer (half) | INS costs ×0.5 (does not stack with Ivory Hairpin; Inspired then gives ×0.25) | Chest: E03 Dead Heart (CH-E2) · Chest: S09 Namsan summit (CH-E1) | ◆ |
| 538 | Medal of 1834 | — | DEF +10, RES +10 | Vidal & Fils CH-E2 | 9,800 |
| 539 | Laurel Ring | — | All stats +3 (STR, ART, DEF, RES, TMP, LCK) | Corbel CH-E2 | 11,000 |
| 540 | Norigae Tassel | — | Wearer starts each battle with **Cantabile** | Hanji-bang CH-E1 (CCR) | ₩1,600,000 |
| 541 | Lucky Pouch | Coin Toss | Won after battle ×1.5 · *bokjumeoni* | Hanji-bang CH-E1 (CCR) | ₩1,700,000 |
| 542 | Hand Warmer | — | Immune to Lento, Fermata | Haneul Mart CH-E1 | ₩1,600,000 |
| 543 | Headphones | — | Immune to Reverie, Delirium, Hush | Gyeoul Outfitters CH-E1 (CCR) | ₩2,000,000 |
| 544 | Transit Card | Sprint Shoes | Field speed ×1.5 on Seoul maps; subway rides free | Story CH-E1: Seo-yeon's spare card | ◆ |
| 545 | Concert Pass | — | Party Crescendo +20 at battle start | Busking ladder, 4th spot cleared (§11.3) | ◆ |
| 546 | Gilt Lorgnette | Scan-on-hit | The wearer's Fight also works as a Rough Sketch (target's HP and affinities shown for the battle) · "Mme Lavergne sees everything twice." | Prize: first Rapture ≥ 90 at Salon Lavergne (§11.3) | ◆ |
| 547 | Feuilleton | — | Immune to Reverie and Delirium · "To be continued in Tuesday's number." | Prize: first Rapture ≥ 90 at Salon Bastide | ◆ |
| 548 | Havana Mantilla | — | Wearer regains 2% of max INS at each turn start | Prize: first Rapture ≥ 90 at Salon Merlin | ◆ |
| 549 | Ivory Missal | — | Wearer's healing +15% | Prize: first Rapture ≥ 90 at Salon d'Agoult | ◆ |
| 550 | Opal of Vienna | — | Allegro on the wearer lasts 9 turns (from 6) | Prize: first Rapture ≥ 90 at Countess Apponyi's | ◆ |
| 551 | Golden Compass | — | The wearer's rank actions take ×0.85 (from ×0.75) and all-target actions ×0.6 (from ×0.5) | Drop: BOSS-15 Delorme, guaranteed (§11.2) | ◆ |
| 552 | Stopped Horn | — | Immune to Fermata and Lento; the wearer's gauge cannot be pushed back (Escapement, Libretto `ATB` −) | Drop: BOSS-18, guaranteed: one of the four horns, its throat plugged | ◆ |
| 553 | Orpheus Mask | — | Immune to Unwritten and Reverie | Drop: BOSS-24, guaranteed | ◆ |
| 554 | Varga Lens | — | The wearer's stats cannot be lowered (Libretto `STAT` −, Composed-type debuffs, Out of Tune's ART cut) | Drop: BOSS-25, guaranteed | ◆ |
| 555 | Ground Lens | — | The wearer's magical damage treats the target's RES as 25% lower | Drop: BOSS-33, guaranteed (Delorme's own optics) | ◆ |
| 556 | Unstruck Bell | — | Party Crescendo +50 at battle start; Synergies the wearer joins deal +10% | Drop: BOSS-43, guaranteed (NG+) | ◆ |

**Tuning note.** Copal Varnish and Gilder's Leaf are named for Lucile's father's trade (a frame-gilder, CANON §5e) and her own varnish tricks (she taught Sand); Varnish and Glaze are the canon statuses. One of each on two members is the intended mid-game defensive build; neither stacks with the status from other sources (a battle-long status is either on or off).

---

## 6. Consumables and Battle Items

Items heal and hurt **fixed amounts** (CANON §10b), ignore rows, Mirror and Hush, and cannot target Unwritten units (combat_ensemble §4.4). Canon anchors (CANON §14) are marked **A**; their values and prices are binding. Period remedies are real ones of the 1830s, used for their game function only; nothing is claimed as a cure for cholera (CANON §16e).

### 6.1 Restoratives and cures (1833–34)

| ITM | Name (UI) | Effect | Period note | First sold | Price |
|---|---|---|---|---|---|
| 001 | Tisane **A** | 150 HP | Lime-blossom tea | Laborde P02, CH-02 | 8 |
| 002 | Bouillon **A** | 500 HP | Beef broth from the *bouillon* houses | Laborde P10, CH-05 | 40 |
| 003 | Cordial **A** | 1,500 HP | Spiced wine cordial | Mercerie Aubert CH-10 (CCR) · Laborde CH-12 | 180 |
| 004 | Grand Cordial **A** | Full HP | — | Laborde CH-14 | 600 |
| 005 | Café Noir **A** | +30 INS | Black coffee | Mère Gaudin's counter (P04) and Laborde, CH-02 | 30 |
| 006 | Chocolat **A** (*Chocolat de Santé*) | +100 INS | Pharmacists' "health chocolate" | Mercerie Aubert CH-10 (CCR) · Laborde CH-12 | 150 |
| 007 | Élixir **A** | Full HP and INS | — | Not sold (§11.4) | — |
| 008 | Sal Volatile **A** | Revive at 25% | Smelling-salt spirit | Laborde CH-02 | 40 |
| 009 | Sel de Vie **A** | Revive at 100% | — | Laborde CH-14 | 1,500 |
| 010 | Smelling Salts **A** | Cure Reverie | — | Laborde CH-02 | 10 |
| 011 | Four Thieves **A** (*Vinaigre des Quatre Voleurs*) | Cure Miasma | The plague vinegar | Laborde CH-02 | 15 |
| 012 | Eyewash **A** | Cure Smoke | Rose water | Laborde CH-02 | 10 |
| 013 | Throat Lozenge **A** | Cure Hush | *Pâte de guimauve* | Laborde CH-02 | 12 |
| 014 | Courage Draught **A** | Cure Stagefright | — | Laborde CH-03 | 25 |
| 015 | Sculptor's Oil **A** | Cure Marble | — | Laborde CH-06 | 60 |
| 016 | Pitch Pipe **A** | Cure Out of Tune, Discord | — | Laborde CH-04 | 40 |
| 017 | Panacea **A** | Cure all negative statuses except KO | — | Laborde CH-08 | 300 |
| 018 | Picnic Hamper **A** | Full party rest at a Lectern | — | Mercerie Aubert CH-10 (CCR) · Laborde CH-12 | 400 |
| 019 | Barley Sugar | +15 INS | *Sucre d'orge* | Laborde CH-03 | 12 |
| 020 | Vichy Water | 300 HP to the party | Bottled spa water | Laborde CH-05 | 120 |
| 021 | Eau de Mélisse | Party Cantabile | The Carmelite water | Laborde CH-07 | 90 |
| 022 | Hoffmann's Drops | Cure Lento, Swing | Ether drops | Laborde CH-08 | 30 |
| 023 | Grand Vichy | 1,000 HP to the party | — | Laborde CH-12 | 400 |
| 024 | Valerian Tincture | Cure Delirium, Frenzy | — | Pharmacie du Dôme CH-11 (CCR) · Laborde CH-12 | 80 |
| 025 | Smelling Bottle | Revive at 25% and cure all statuses | — | Laborde CH-14 | 450 |
| 026 | Café Royal | +60 INS to the party | Coffee with cognac | Laborde CH-14 | 900 |
| 027 | Hot Chestnuts | 60 HP; also Lucile's Liked gift | Quay vendor | P22 vendor, CH-03 | 2 |

**Free supply (secrecy_and_trust §2.2):** Mère Gaudin gives **2 Tisanes each chapter from CH-04** if `byt_boil_water` was taken; Sœur Marthe gives **2 Panaceas** once (`byt_handwash`, CH-12); the Prefecture pays **100 F** (`byt_line_up`, CH-04).

### 6.2 Battle items

Fixed damage, elemental (affinity and Light apply, CANON §10c), no crit, never miss. All-target items split their listed total ×0.5 per target.

| ITM | Name (UI) | Effect | First sold | Price |
|---|---|---|---|---|
| 040 | Squib | FIRE 60, one enemy | Laborde CH-02 | 15 |
| 041 | Paving Stone | EARTH 150, one enemy · "From rue Saint-Antoine." | Find: ×5 at P08 (CH-04); never sold | — |
| 042 | Lampblack Pouch | SHADE 120 and Smoke (base 65), one enemy | Corbel CH-04 | 45 |
| 043 | Beeswax Candle | LIGHT 300, one enemy | Laborde CH-05 | 70 |
| 044 | Hourglass Sand | Lento (base 65), one enemy | Corbel CH-05 | 40 |
| 045 | Leyden Jar | BOLT 400, one enemy | Corbel CH-07 | 120 |
| 046 | Glacière Ice | ICE 400, one enemy | Laborde CH-07 | 120 |
| 047 | Seltzer Siphon | WATER 400, one enemy | Laborde CH-08 | 120 |
| 048 | Mesmer's Magnet | Reverie (base 50), one enemy | Corbel CH-08 | 60 |
| 049 | Tocsin Bell | Stun (base 35), one enemy; bosses immune | Corbel CH-09 | 80 |
| 050 | Ruggieri Rocket | FIRE 900, all enemies | Chest: P26 abbey wing ×2 (CH-12) · Corbel CH-14 | 300 |
| 051 | Bellows Charge | WIND 900, all enemies | Weiss CH-11 (CCR) · Corbel CH-14 | 300 |
| 052 | Ruggieri Bouquet | FIRE 2,000, all enemies | Corbel CH-14 | 1,200 |
| 053 | Galvanic Pile | BOLT 2,000, all enemies | Corbel CH-14 | 1,200 |

Ruggieri items honour the real Paris pyrotechnic house of that name, as a product name only; no Ruggieri character appears.

### 6.3 Seoul consumables (CH-E1, Haneul Mart)

Every 1833 consumable the party carries still works in Seoul. Haneul Mart sells modern equivalents, priced near the franc price × 200 and inside the CANON §14 won band (₩1,000–300,000).

| ITM | Name (UI) | Effect (= 1833 item) | Price |
|---|---|---|---|
| 060 | Barley Tea | 150 HP (Tisane) | ₩1,500 |
| 061 | Gimbap | 500 HP (Bouillon) | ₩8,000 |
| 062 | Ssanghwa Tonic | 1,500 HP (Cordial) | ₩36,000 |
| 063 | Abalone Porridge | Full HP (Grand Cordial) | ₩120,000 |
| 064 | Canned Coffee | +30 INS (Café Noir) | ₩6,000 |
| 065 | Red Ginseng Shot | +100 INS (Chocolat) | ₩30,000 |
| 066 | Ammonia Inhalant | Revive at 25% (Sal Volatile) | ₩8,000 |
| 067 | Wild Ginseng Root | Revive at 100% (Sel de Vie) | ₩300,000 |
| 068 | Eye Drops | Cure Smoke | ₩2,000 |
| 069 | Throat Spray | Cure Hush | ₩2,400 |
| 070 | Pocket Tuner | Cure Out of Tune, Discord (Pitch Pipe) | ₩8,000 |
| 071 | Cold Medicine | Cure all negative statuses except KO (Panacea) | ₩60,000 |
| 072 | Hot Pack | Party Cantabile (Eau de Mélisse) | ₩18,000 |
| 073 | Lunchbox Set | Full party rest at a save point (Picnic Hamper) | ₩80,000 |
| 074 | Hotteok | 300 HP to the party (Ms. Bae's cart, LOC-S03) | ₩2,000 |

---

## 7. Key Items

Canon fixes each KEY's name, source and purpose (CANON §14). This table adds the UI name (≤ 16), the in-game description (one line, ≤ 30 characters), and the mechanical detail this doc owns. All KEY items are ◆, weightless, and sit in the KEY tab.

| KEY | UI name | Description line | Detail |
|---|---|---|---|
| KEY-01 | Ornate Brass Key | Two clock hands, one key. | Leaves the tab when it turns in the dial (CH-P); re-listed as "seen in the dial" in CH-E1 |
| KEY-02 | Smartphone | 3%. Six lights left. | Field command *Flashlight* (6 uses, CH-01–CH-13; Secrecy per CANON §11e); CH-14 recharge to 20% on KEY-28: *Camera* (12 photos), last 5% greyed for CH-17; Seoul: becomes the phone menu |
| KEY-03 | Student ID | Hanseong. Kang Min-jun. | Examine shows his 2025 photo; showing it is a Slip (+10, CANON §14) |
| KEY-04 | Clair de lune | Photocopy, A4, creased. | Source of REP-01; paper type is examinable ("too white for 1833") |
| KEY-05 | Quarry Lantern | Mathurin's. Mind the oil. | Field light radius 3 tiles in Gloom maps; Mathurin's LANTERN command while he is a guest |
| KEY-06 | Room Key | Room 3, Au Diapason Fêlé. | Free inn rest at P04 in CH-02 |
| KEY-07 | Berlioz's Letter | "Admit the bearer. — H.B." | Opens P06 and P05 (CH-03) |
| KEY-08 | Salon Invitation | Stamped T1. | Stamps T2 (CH-03), T3 (CH-07), T4 (SQ-20, CH-14); unlocks salon tiers (CANON §11g) |
| KEY-09 | Lucile's Sketchbook | The last page is hers. | Viewable from CH-05; in the tab from the CH-09 dawn; last page per LAW-23.5 |
| KEY-10 | Paymaster Sketch | Charcoal. A face. Tissot. | Evidence before Gisquet (CH-04) |
| KEY-11 | Laissez-passer | Prefecture stamp, 1833. | Passes Hunted-tier bridge checks |
| KEY-12 | Workshop Pass | Pleyel & Cie, rue Cadet. | Voicing (§2.4) from CH-07; SQ-07 |
| KEY-13 | Formula Sketch | E = mc², in drapery. | First proof (CH-06) |
| KEY-14 | Nitinol Spring | It remembers its shape. | Proof of alloys (CH-07); Almanach entry completed by Alkan's Bite Your Tongue |
| KEY-15 | JAZZ MIX '87 | A cassette. Side B. | Proof of the Walkman; buried in CH-E2 (SQ-23) |
| KEY-16 | Vane's Ledger | Calf leather, a code. | Clef map, Panel VII, the 30 Sep order; handed to Gisquet in the Seoul branch only |
| KEY-17 | Action Assembly | A Pleyel action, mended. | Restores Chopin's Pleyel (CH-08); triggers the Tuning Hammer (ITM-512) |
| KEY-18 | "Lumière" File | Her reports. Your words. | Reads back Confided lines; may be burned in CH-14 |
| KEY-19 | Clef Map | Seven stones, decoded. | Marks Clef I–VII on the W01 map from CH-10 |
| KEY-20 | Passports | Visas, a ticket book. | Diligence legs and the Aachen border (CH-10–CH-11, CH-14) |
| KEY-21 | Ad Astra | H.V. 1934. Panel VII. | Opens the Heart gate (CH-15) |
| KEY-22 | Chaplain's Key | Abbé Rives's ring. | Val-de-Grâce abbey wing (CH-12) |
| KEY-23 | Cylinder | Your signature, 0–80%. | Shows the BOSS-18 percentage; scales *Recorded Echo*; destroyed in CH-16 |
| KEY-24 | Unsent Letters | Letters she never sent. | Readable (KEY-tab Read) |
| KEY-25 | Gala Programme | Salle Le Peletier, 6 Dec. | Readable programme (lore doc text) |
| KEY-26 | Helm Key | La Lumière, ex-Sourdine. | Dirigible flight from CH-14 |
| KEY-27 | Crypt Key | And a timetable: 00:43. | Opens P29; triggers the crypt-door prompt (CANON §0c) |
| KEY-28 | Crank Dynamo | Brücke's. One charge left. | One recharge of KEY-02 (CH-14) |
| KEY-29 | Heart Shard | Warm. It hums in D. | Given to Delacroix in CH-17 |
| KEY-30 | Keepsakes of 1833 | Six gifts. Seven, maybe. | Sub-list of 6–7 keepsakes (§12.4): Remembrances (Seoul) or forge components (Paris) |
| KEY-31 | Indenture | Théo, apprenticed. Signed. | Gate for YES (LAW-23); Sketchbook last page switches to the Horizon state |
| KEY-32 | Clef Forks | Three forks. Alkan's. | Detunes plinths (CH-15); one returns as his keepsake |
| KEY-33 | Visitor Lanyard | Hanseong. Guest. | Campus doors for Lucile (CH-E1) |
| KEY-34 | Exhibition Tickets | "Light & Colour." Two. | Entry to LOC-S06 |
| KEY-35 | Testament | Of the Stilled Hour. | Charge and Codicil readable; the Codicil burns in CH-E1 |
| KEY-36 | Box JD-1888-07 | "Caisse Aubray." | Contents by branch (CANON §14); readable letter text per LAW-24/25 |
| KEY-37 | Paganini's Note | To Berlioz. A viola? | Side scene (*Harold*) in CH-E2 |
| KEY-38 | Survey Dossier | 2049. Burn it. | Burned with Brücke (CH-E2, optional) |
| KEY-39 | Hangul Letter | 서연에게 | Final reveal of the Paris coda; the hangul label counts 2 characters per syllable (CANON §16a) |
| KEY-40 | Salon *Livret* | No. 61. Hers. | Salon access; the entry text per CANON §14 (BQ-PC02b variant) |
| KEY-41 | Embassy Receipt | Lucile Aubray. Papers. | Proof of her papers (CH-E1) |
| (memento) | Padded Jacket | Too warm, too strange. | Min-jun's navy jacket in the KEY tab CH-02–CH-17; returns as ITM-479 in CH-E1 (§4.3). Not a canon KEY; no number |

**KEY-30 keepsake sub-list (CANON §6).** Chopin's score page · Liszt's glove · Berlioz's baton · Delacroix's sketch · Farrenc's engraved plate · Alkan's Clef tuning fork (one of KEY-32) · Julien's cassette (if recruited). Berlioz's keepsake baton is the baton he conducted the gala with, not ITM-103 (which Min-jun has carried since CH-04).

---

## 8. Opus Score Sources

CANON §11c fixes the families: 12 Period Scores (OPS-01–12) sold at Maison Farrenc and Schlesinger's, 12 Future Scores ✦ (OPS-13–24) transcribed by Min-jun at a Lectern, 8 secret Scores (OPS-25–32) from bosses and quests. **skills_and_progression owns every OPS** (its §4: title, work, teach list, bonus shape, Invocation and the twelve Period prices); this section restates its sources and prices so that shop stock (§10) and boss rewards (§11.2) are built from one table, and it defers to skills_and_progression on any difference. Scores are not ITM entries: each sits in the Opus menu, is bought once (the shop row greys out "Owned"), cannot be sold, and never appears in a chest. MF = Maison Farrenc (LOC-P19), Schl. = Schlesinger's (LOC-P10, door opens CH-06).

| OPS | Score (UI) | Work | Source | Price |
|---|---|---|---|---|
| OPS-01 | Well-Tempered | J. S. Bach, *Das wohltemperierte Klavier* I (1722) | MF CH-05 | 400 |
| OPS-02 | Messiah | Handel, *Messiah* (1741) | MF CH-05 | 500 |
| OPS-03 | Requiem | Mozart, Requiem, K. 626 (1791) | Schl. CH-06 | 600 |
| OPS-04 | Eroica | Beethoven, Symphony No. 3 (1804) | Schl. CH-06 | 700 |
| OPS-05 | Pastoral | Beethoven, Symphony No. 6 (1808) | MF CH-07, after the duel | 800 |
| OPS-06 | Orphée | Gluck, *Orphée et Eurydice*, Paris version (1774) | Schl. CH-08 | 1,000 |
| OPS-07 | Guillaume Tell | Rossini, *Guillaume Tell* (1829) | MF CH-08 | 1,100 |
| OPS-08 | Robert le diable | Meyerbeer, *Robert le diable* (1831) | Schl. CH-12 (the return to Paris; P10 is open) | 2,000 |
| OPS-09 | Norma | Bellini, *Norma* (1831) | MF CH-12 | 2,200 |
| OPS-10 | The Creation | Haydn, *Die Schöpfung* (1798) | MF CH-14 | 3,500 |
| OPS-11 | Don Giovanni | Mozart, *Don Giovanni* (1787) | Schl. CH-14 | 3,800 |
| OPS-12 | Ninth Symphony | Beethoven, Symphony No. 9 (1824) | MF CH-14 | 4,200 |
| OPS-13–24 ✦ | Future Scores (REP-17, REP-35–45, CANON §15d) | — | Transcribed free at the Lectern skills_and_progression §4.2 names: OPS-14 CH-05 (Hôtel de la Lyre), OPS-16 CH-06 (Trois Moulins), OPS-17 CH-07 (P15 anteroom), OPS-15 CH-08 (quay, *La Mouette*), OPS-23 CH-08 (P19), OPS-18 CH-10 (first W02 Lectern), OPS-19 CH-11 (Goldenen Anker), OPS-13 and OPS-20 CH-12 (P26 abbey and dome), OPS-22 CH-13 (*La Lumière*'s gondola), OPS-21 CH-14 (P32), OPS-24 CH-15 (Party 2's first P29 Lectern). Secrecy +3 per transcription with a non-confidant in the party (CANON §11c) | — |
| OPS-25 | Lost Era | Kang Min-jun, *Concerto "Lost Era"* (REP-27) | BOSS-17 cleared with Own Voice ≥ 6 (CANON §11g) | — |
| OPS-26 | Devin du Village | Rousseau, *Le Devin du village* (1752) | BOSS-40, CH-14 (missable) | — |
| OPS-27 | Wellington | Beethoven, *Wellingtons Sieg* (1813) | BOSS-38, CH-14 or CH-E2 (SQ-23) | — |
| OPS-28 | Caprice No. 24 | Paganini, Caprice No. 24 (1820) | BOSS-36, CH-14 (missable) | — |
| OPS-29 | Oberon | Weber, *Oberon* (1826) | BOSS-37, CH-11 or CH-14 | — |
| OPS-30 | Barricades | F. Couperin, *Les Barricades mystérieuses* (1717) | BQ-PC08 finale, CH-14 | — |
| OPS-31 | Art of Fugue | J. S. Bach, *Die Kunst der Fuge* (1751) | BOSS-31, CH-E1 (other branch via Reverie) | — |
| OPS-32 | Unfinished | Schubert, Symphony in B minor, D. 759 (1822) | BOSS-34, CH-E2 (other branch via Reverie) | — |

**Stock windows** (skills_and_progression §3.6): restocks after the CH-07 duel, in CH-08, on the CH-12 return and in CH-14; no Score is sold in CH-10–CH-11 (the party is out of Paris) or on the single gala day of CH-13. The two Score counters also sell gifts and Folios (§10.6). Period prices sit below the CANON §14 relic band of their tier because a Score is a fifth purchase on top of the kit; §13 counts them in the affordability check as an optional sink, not as kit.

---

## 9. Gifts and Curios

Favourites are canon (CANON §11f); Liked and Disliked lists and reactions are secrecy_and_trust §3.7, whose UI names this doc keeps. Gifts are consumed when given; one gift per member per chapter (secrecy_and_trust §3.3). Town finds follow overworld_and_towns §5; other sources are this doc's. **Shared items:** the *Metronome* (ITM-654) is Julien's favourite and Liszt's dislike; *Throat Lozenge* (ITM-013) and *Hot Chestnuts* (ITM-027) are consumables that double as Liked gifts.

| Member | Favourites (+25) | Liked (+15) | Disliked (0, returned) |
|---|---|---|---|
| LU | 600 Prussian Blue (find P03 rue Cadet corner, CH-05; Ravenel 6) · 601 Indiana (Sand) (Père Gobert P22, 6) · 602 Valencia Oranges (Mme Gervais's brother P20, 1 each; ×3 Nohant larder) | 603 Madder Lake (Ravenel, 5) · 027 Hot Chestnuts (P22 vendor, 2) · 604 Spinning Top (Corbel, 3) | 605 Painted Fan (Corbel, 4) · 606 Snuffbox (Corbel, 15) |
| BE | 607 Faust (Nerval) (Gobert, 4, CH-03+) · 608 Shakespeare (En) (Pradel P16, 8, CH-08+) · 609 Orchestra Paper (find P12 music cupboard, CH-05; Schlesinger's 6) | 610 Guitar Strings (Schlesinger's, 3) · 611 Aeneid (Gobert, 5) · 612 Hamlet Playbill (Gobert, 1) | 613 Rossini Score (Schlesinger's, 8) · 614 Hair Pomade (Laborde P10, 4) |
| DE | 615 Moroccan Silk (Vidal & Fils window, 1 after CH-07) · 616 Byron's Poems (P22 toll-keeper's box, CH-06+) · 617 English Paints (find P06 chest, CH-06+) | 618 Dante's Inferno (Gobert, 5) · 013 Throat Lozenge (Laborde, 12) · 619 Mozart Score (Schlesinger's, 8) | 620 Ingres Print (Gobert, 3) · 621 Mechanical Toy (Corbel, 12) |
| AL | 622 Hebrew Psalter (find P07 Pavillon du Roi, CH-07+) · 623 Automaton Bird (find P36 cupboard, CH-14) · 624 Bach WTC Edition (Maison Farrenc, 30, CH-08+) | 625 Watch Movement (Corbel, 20) · 626 Railway Print (Gobert, 2) · 627 Black Tea (Laborde P10, 3) | 628 Theatre Tickets (P10 kiosk, 5) · 629 Ball Invitation (find P14, from the Marquise, free) |
| CH | 630 Parma Violets (Pont Neuf barrow, 1, CH-06+) · 631 Polish Gazette (find P11 lodge, CH-06+) · 632 Kid Gloves (Passage de l'Opéra glover, 12, CH-06+) | 633 Gingerbread (Polish émigré stall P22, 2) · 634 Silk Cravat (Vidal & Fils, 10) · 635 Bach Fugues (Maison Farrenc, 15) | 636 Kalkbrenner Book (Schlesinger's, 6) · 637 Military March (Schlesinger's, 2) |
| LI | 638 Rosary (find P24 church step, CH-06+) · 639 Cigar Box (find Tortoni terrace, CH-07+) · 640 Paganini Sheet (find Passage de l'Opéra wall, CH-05+) | 641 Lamartine Poems (Gobert, 5) · 642 Tokaji Wine (Hôtel de la Lyre cellar, 20) · 643 Le Globe Issue (Pradel, back number, 1) | 654 Metronome · 644 Pocket Mirror (Corbel, 6) |
| FA | 645 Engraver's Burin (find P19, Lucien's proof, CH-08+) · 646 Couperin Edition (Maison Farrenc, 40, CH-08+) · 647 Victorine's Gift (Zoé's child's fan, Corbel, 5, CH-08+) | 648 Haydn Quartets (Schlesinger's, 12) · 649 Account Ledger (Pradel, 3) · 650 Quill Knife (Armurerie Vidal, 4) | 651 Conduct Manual (Gobert, 2) · 652 Perfume Flask (Laborde P10, 15) |
| JU | 653 Naples Coffee (Café des Trois Dièses, 2, CH-14) · 654 Metronome (Pleyel showroom, 30, CH-14) · 655 Song Sheet (find Trois Dièses cloakroom, CH-08+) | 656 Bass String (Schlesinger's, 4) · 657 Staff Paper (Schlesinger's, 2) · 658 Absinthe (Trois Dièses, 3) | 659 Laurel Wreath (Mélie, P32, 2) · 660 Fan Letter (find P16, free) |

*Absinthe* and *Tokaji Wine* are tavern-and-salon alcohol within the T rating (CANON §16e); neither has a battle use. *Le Globe* stopped in April 1832, so Pradel sells a back number.
## 10. Shop Inventories by Chapter

### 10.1 Rules

- **Names and places** are CANON §12's; **opening windows** follow overworld_and_towns §2.2 (which districts the party can walk into each chapter); **prices** are those of §3–§6 and sit in the CANON §14 band of the tier in which the item is first sold. Source columns in §3–§6 name an item's *first* shop; this section lists every chapter it is on sale.
- **Stock carries forward.** Each row adds to the row above. A tier's standard "[Tier] [Class]" line stays on sale through the next tier and then drops; named weapons and armour drop when the next tier's chapters end; **consumables, relics and gifts never drop**. Stock is unlimited (FF6 rule) unless a row says "one".
- **Paris is shut to the party in CH-10–CH-13** (the tour, then a city held by the Grey Hand). Concerto-tier gear is therefore sold on the road in CH-10–CH-11 (§10.7) and found in CH-12–CH-13 dungeons (§11.5); Paris counters jump to Symphonie stock in CH-14 and keep the Concerto standard line as the "previous tier", so a party that skipped the road shops can still catch up.
- **Rejoin kit (CH-12).** Berlioz and Delacroix, who stayed in Paris through CH-10–CH-11, rejoin wearing the Concerto standard weapon of their class (ITM-168, ITM-198) and a Concerto Coat (ITM-463) **if** the slot they left holds something weaker; they shopped while the party toured. Nothing is added to the inventory, so the rule creates no resale.
- **Lucile haggles** (CANON §5d): with her in the active party, Couleurs Ravenel and Curiosités Corbel (her employer) sell at **−10%**, rounded half up to the franc. Not while her BP is frozen (CH-09 dawn to Mending 2), not in Seoul.
- **Secrecy refusals** (CANON §11e): at Compromised (80–99) Vidal & Fils refuses service ("Monsieur is not received."); Curiosités Corbel trades through its back-lane counter at full stock and price (overworld_and_towns §4.3; see the cross-doc note on secrecy_and_trust §2.9.2). Every other shop always sells.
- **Selling:** any shop buys any sellable item at ⌊50%⌋ of list (§1); Seoul shops pay in won at ₩200 per franc of list.

### 10.2 Shop roster and windows

| Shop | LOC | Keeper | Open | Sells |
|---|---|---|---|---|
| Armurerie Vidal | P03, rue Bergère | Joseph Vidal (TF-006) | CH-02–CH-09, CH-14, CH-E2 | Standard Batons, Sword-canes, Rapiers, Hammers, Quills, Sabres; standard armour |
| Vidal & Fils | P14, rue du Bac corner | Augustin Vidal (TF-021) | CH-05–CH-09, CH-14, CH-E2 | Named weapons and armour, two relics |
| Coutellerie du Palais | P16, the arcades | Mme Héloïse Bastien (TF-027) | CH-08–CH-09, CH-14, CH-E2 | Sword-canes, Hammers, Sabres, Canes, fencing gear |
| Couleurs Ravenel | P22, head of rue de Seine | Mlle Adèle Ravenel (TF-035) | CH-05–CH-09, CH-14, CH-E2 (and the E02 easel) | Brushes, pigments |
| Curiosités Corbel | P21, rue Dauphine | Anselme Corbel (FIC-04) | CH-04–CH-09, CH-14, CH-E2 | Relics, battle items, curios |
| Pharmacie Laborde | P02 (Basile, TF-002) from CH-02; P10 (Émile, TF-017) from CH-05 | as named | CH-02–CH-09; CH-11 (P02, Lucile's interlude); CH-12 (P02 night bell, P10); CH-13 (P10); CH-14; CH-E2 | Consumables, battle items |
| Mère Gaudin's counter | P04 | FIC-02 | CH-02–CH-09, CH-14, CH-E2 | Tisane, Café Noir; the inn |
| Maison Farrenc | P19 (from P10) | Aristide Farrenc (NPC-20) | CH-05–CH-09, CH-12, CH-14, CH-E2 | Period Scores (§8), Folios, gifts; press rebuttal |
| Schlesinger's | P10, rue de Richelieu | Maurice Schlesinger (NPC-41) | CH-06–CH-09, CH-12, CH-14, CH-E2 | Period Scores (§8), gifts |
| Pleyel workshop | P12 | Camille Pleyel (NPC-15) | CH-07–CH-09, CH-14 (Voicing); CH-E2 (Voicing, keepsake forge) | Services (§2.4, §2.5) |
| Mercerie Aubert (CCR) | R04 La Châtre | Mme Aubert (TF-057) | CH-10 | Consumables, travel clothes |
| Coutellerie Lambotte (CCR) | R06 Liège | M. Lambotte (TF-060) | CH-11 | Concerto weapons (every Paris class but Brushes), armour |
| Farbenhandlung Weiss (CCR) | R07 Düsseldorf | Herr Weiss (TF-063) | CH-11, CH-14 | Brushes, relics |
| Pharmacie du Dôme (CCR) | R10 Strasbourg | M. Wendling (TF-066) | CH-11, CH-14 | Consumables |
| Haneul Mart | S03, S04 (ground floor), S07, S12 | Jun-ho (TF-074) at S03 | CH-E1 | Consumables, one relic |
| Kang Piano Service | S15 | Kang Do-hyun (FIC-10) | CH-E1 | Seoul weapons, Voicing |
| Gyeoul Outfitters (CCR) | S07 | shop clerk (Tier C) | CH-E1 | Head and body gear, one relic |
| Hanji-bang (CCR) | S12 | shop owner (Tier C) | CH-E1 | Brushes, relics |
| Mr. Baek's coin shop | S12 | TF-081 | CH-E1 | Buys francs at ₩200 each (CANON §14); sells nothing |
| Atelier stations | E02 (restored only) | — | CH-E2 | Piano: Voicing; easel: Ravenel's CH-E2 list plus ITM-474 |

### 10.3 Weapons and armour

**Armurerie Vidal (P03).**

| Chapter | Weapons | Armour and other |
|---|---|---|
| CH-02 | Étude Baton 60 · Étude Sword-cane 80 | Étude Cap 45 · Étude Coat 80 |
| CH-03 | + Prélude Baton, Prélude Sword-cane, Prélude Rapier 220 each | + Prélude Hat 160 · Prélude Coat 240 |
| CH-04 | + Malacca Sword-cane 380 · Prélude Hammer 220 | + Felt Beret 280 · Smock of Daubrée's 300 |
| CH-05 | + Nocturne Baton, Nocturne Sword-cane, Nocturne Rapier, Nocturne Hammer 560 each; Étude line drops | + Nocturne Hat 380 · Nocturne Coat 520; Étude armour drops |
| CH-06 | + Nocturne Quill 560 | — |
| CH-07 | + Nocturne Sabre 560 | — |
| CH-08–CH-09 | + Rhapsodie Baton, Rhapsodie Sword-cane, Rhapsodie Rapier, Rhapsodie Quill 1,150 each; Prélude line and Malacca drop | + Rhapsodie Hat 820 · Rhapsodie Coat 980 · Quill Knife 4 (gift); Felt Beret and Smock drop |
| CH-14 | Concerto Baton, Concerto Sword-cane, Concerto Rapier, Concerto Quill 2,100 each (previous tier) · Symphonie Baton, Symphonie Rapier, Symphonie Quill 3,900 each | Concerto Hat 1,500 · Concerto Coat 1,700 · Symphonie Hat 2,800 · Symphonie Coat 3,000 · Quill Knife 4 |
| CH-E2 | Symphonie Baton, Rapier, Quill 3,900 each · Magnum Baton, Magnum Rapier, Magnum Quill 5,600 each | Symphonie Hat 2,800 · Symphonie Coat 3,000 · Magnum Hat 4,000 · Magnum Coat 4,200 · Quill Knife 4 |

**Vidal & Fils (P14).** Refuses service at Compromised.

| Chapter | Weapons | Armour, relics, gifts |
|---|---|---|
| CH-05 | Nocturne Baton, Sword-cane, Rapier, Hammer 560 each (the Faubourg pays the same as the students, whatever Augustin says) | Nocturne Hat 380 · Nocturne Coat 520 · Beaver Top Hat 780 · Poke Bonnet 760 · Spencer Jacket 680 |
| CH-06 | + Nocturne Quill 560 | + Redingote 800 · Silk Cravat 10 |
| CH-07 | + Ebony Baton, Dandy's Sword-cane, Salon Épée, Forge Hammer, Steel Nib, Hussar Sabre 980 each | + Dancing Pumps 1,800 · Moroccan Silk 1 (window scarf, sold after CH-07) |
| CH-08 | Nocturne line moves to Armurerie Vidal only | + Moiré Gown 1,050 |
| CH-09 | + Silver Baton 1,380 | + Lace Cap 1,100 |
| CH-14 | Palais Rapier, Polonaise Quill 5,100 each; CH-05–CH-09 weapons and armour drop | Astrakhan Hat 3,600 · Silk Bonnet 3,800 · Velvet Gown 4,000 · Dancing Pumps 1,800 · Silk Cravat 10 · Moroccan Silk 1 |
| CH-E2 | + Ivory Baton, Missolonghi Rapier, Fantaisie Quill 6,900 each | + Laurel Circlet 4,900 · Winter Bonnet 5,000 · Dress Coat of 1834 5,200 · Medal of 1834 9,800 |

**Coutellerie du Palais (P16).**

| Chapter | Weapons | Armour |
|---|---|---|
| CH-08 | Rhapsodie Sword-cane, Rhapsodie Hammer, Rhapsodie Sabre 1,150 each | Rhapsodie Hat 820 · Rhapsodie Coat 980 · Fencing Mask 1,050 · Fencing Jacket 1,100 |
| CH-09 | + Fantastique Sabre 1,380 | — |
| CH-14 | Concerto Sword-cane, Concerto Hammer, Concerto Sabre 2,100 each (previous tier) · Symphonie Sword-cane, Symphonie Hammer, Symphonie Sabre, Symphonie Cane 3,900 each · Waverley Cane, Machine Hammer, Ivory-Knob Cane 5,100 each | Symphonie Hat 2,800 · Symphonie Coat 3,000 · Greatcoat 3,800 |
| CH-E2 | Symphonie line as CH-14 · Magnum Sword-cane, Magnum Hammer, Magnum Sabre, Magnum Cane 5,600 each · Sabbath Cane, Ostinato Hammer, Magyar Sabre 6,900 each | Magnum Hat 4,000 · Magnum Coat 4,200 · Cuirassier's Vest 5,200 |

### 10.4 Brushes and relics

**Couleurs Ravenel (P22).** −10% with Lucile in the active party. From the CH-09 dawn the counter line changes (WS-11, overworld_and_towns): Mlle Ravenel asks after her.

| Chapter | Stock |
|---|---|
| CH-05 | Nocturne Brush 560 · Prussian Blue 6 · Madder Lake 5 |
| CH-07 | + Kolinsky Filbert 980 |
| CH-08–CH-09 | + Rhapsodie Brush 1,150 · Badger Blender 1,380 |
| CH-14 | Concerto Brush 2,100 (previous tier) · Symphonie Brush 3,900 · Prussian Blue 6 · Madder Lake 5 |
| CH-E2 | Symphonie Brush 3,900 · Magnum Brush 5,600 · Lumière Sable 6,900 · pigments. The restored E02 easel sells the same list plus Atelier Smock 5,000 |

**Curiosités Corbel (P21).** −10% with Lucile; back-lane counter at Compromised. Relics never leave the shelf once stocked.

| Chapter | Added stock |
|---|---|
| CH-04 | Courier's Boots 450 · Opera Glass 600 · Fencing Glove 750 · Lampblack Pouch 45 · Spinning Top 3 · Painted Fan 4 · Snuffbox 15 |
| CH-05 | Practice Mute 1,600 · Rosin Cake 1,200 · Hourglass Sand 40 |
| CH-06 | Watch Lantern 1,500 · Mechanical Toy 12 · Pocket Mirror 6 |
| CH-07 | Leyden Jar 120 · Watch Movement 20 |
| CH-08 | Copal Varnish 2,200 · Tortoise Fan 2,000 · Mesmer's Magnet 60 · Victorine's Gift (Zoé's child's fan) 5 |
| CH-09 | Postilion Boots 2,400 · Tocsin Bell 80 |
| CH-14 | Steel Busk 2,800 · Lodestone Charm 2,800 · Huntsman's Horn 3,000 · Smith's Wristband 3,400 · Gilder's Leaf 3,800 · Academy Medal 4,000 · Ivory Hairpin 4,200 · Venetian Mirror 6,500 · Encore Locket 7,800 · Ruggieri Rocket 300 · Bellows Charge 300 · Ruggieri Bouquet 1,200 · Galvanic Pile 1,200 |
| CH-E2 | Laurel Ring 11,000 |

### 10.5 Consumables

**Pharmacie Laborde (P02 and P10; one stock list).** The boulevard branch adds its dandy's shelf from CH-05: Hair Pomade 4 · Black Tea 3 · Perfume Flask 15.

| Chapter | Added stock |
|---|---|
| CH-02 | Tisane 8 · Café Noir 30 · Sal Volatile 40 · Smelling Salts 10 · Four Thieves 15 · Eyewash 10 · Throat Lozenge 12 · Squib 15 |
| CH-03 | Courage Draught 25 · Barley Sugar 12 |
| CH-04 | Pitch Pipe 40 |
| CH-05 | Bouillon 40 · Vichy Water 120 · Beeswax Candle 70 |
| CH-06 | Sculptor's Oil 60 |
| CH-07 | Eau de Mélisse 90 · Glacière Ice 120 |
| CH-08 | Panacea 300 · Hoffmann's Drops 30 · Seltzer Siphon 120 |
| CH-11 | P02 only, during Lucile's interlude: Cordial 180 (her one chance to stock up alone) |
| CH-12 | Cordial 180 · Chocolat 150 · Grand Vichy 400 · Valerian Tincture 80 · Picnic Hamper 400 |
| CH-14 | Grand Cordial 600 · Sel de Vie 1,500 · Smelling Bottle 450 · Café Royal 900 |

**Mère Gaudin's counter (P04):** Tisane 8 · Café Noir 30, from CH-02; plus the free Tisanes of `byt_boil_water` (§6.1). **Street sellers** (each a single examine-and-buy point, overworld_and_towns §5): Hot Chestnuts 2 (P22 quay, CH-03+) · Valencia Oranges 1 (P20 landing, CH-05+) · Parma Violets 1 (Pont Neuf barrow, CH-06+) · Gingerbread 2 (Polish émigré stall, P22, CH-06+) · Kid Gloves 12 (Passage de l'Opéra glover, CH-06+). Every other gift vendor and price is in §9.

### 10.6 Music counters (non-Score stock)

**Maison Farrenc (P19).** Press rebuttal 500 F, once per chapter (CANON §11e).

| Chapter | Added stock |
|---|---|
| CH-06 | Bach Fugues 15 |
| CH-08 | Rhapsodie Folio 1,150 · Couperin Edition 40 · Bach WTC Edition 30 |
| CH-09 | Engraver's Folio 1,380 |
| CH-12 | Concerto Folio 2,100 · Copperplate Folio 2,800 |
| CH-14 | Symphonie Folio 3,900 · Hummel Folio 5,100; Rhapsodie Folio and Engraver's Folio drop |
| CH-E2 | Magnum Folio 5,600 · Overture Folio 6,900 (sold off the drying rack beside the Overture No. 1 proofs); Concerto Folios drop |

**Schlesinger's (P10).** CH-06: Orchestra Paper 6 · Guitar Strings 3 · Rossini Score 8 · Mozart Score 8 · Kalkbrenner Book 6 · Military March 2. CH-08: + Haydn Quartets 12 · Bass String 4 · Staff Paper 2.

### 10.7 Regional shops (CH-10, CH-11, CH-14; CCR, fallback §10.8)

| Shop | Chapter | Stock |
|---|---|---|
| Mercerie Aubert (R04) | CH-10 | Tisane 8 · Bouillon 40 · Cordial 180 · Café Noir 30 · Chocolat 150 · Sal Volatile 40 · Smelling Salts 10 · Four Thieves 15 · Eyewash 10 · Throat Lozenge 12 · Pitch Pipe 40 · Panacea 300 · Picnic Hamper 400 · Concerto Hat 1,500 · Concerto Coat 1,700 · Berry Smock 2,200 |
| Coutellerie Lambotte (R06) | CH-11 | Concerto Baton, Concerto Sword-cane, Concerto Rapier, Concerto Hammer, Concerto Quill, Concerto Sabre, Concerto Folio 2,100 each · Rehearsal Baton, Francs-juges Cane, Sardanapalus Rapier, Liège Hammer, Mazurka Quill, Liège Sabre 2,800 each · Concerto Hat 1,500 · Concerto Coat 1,700 · Rhine Cap 2,200 · Travelling Cloak 2,300 · Buff Coat 2,600 · Steel Busk 2,800 |
| Farbenhandlung Weiss (R07) | CH-11 | Concerto Brush 2,100 · Munich Sable 2,800 · Pelisse Hood 2,400 · Lodestone Charm 2,800 · Huntsman's Horn 3,000 · Smith's Wristband 3,400 · Gilder's Leaf 3,800 · Academy Medal 4,000 · Ivory Hairpin 4,200 · Bellows Charge 300 |
| Farbenhandlung Weiss (R07) | CH-14 | + Symphonie Brush 3,900 · Venetian Mirror 6,500 |
| Pharmacie du Dôme (R10) | CH-11 | Tisane 8 · Bouillon 40 · Cordial 180 · Café Noir 30 · Chocolat 150 · Sal Volatile 40 · Smelling Salts 10 · Four Thieves 15 · Eyewash 10 · Throat Lozenge 12 · Pitch Pipe 40 · Panacea 300 · Hoffmann's Drops 30 · Valerian Tincture 80 · Picnic Hamper 400 |
| Pharmacie du Dôme (R10) | CH-14 | + Grand Cordial 600 · Sel de Vie 1,500 · Café Royal 900 |

Lambotte's and Weiss's CH-11 counters are where the tour buys ahead for the three friends who are not on it (Berlioz, Delacroix, Lucile): the cursor shows a ghost portrait for any absent member who can equip the item, and the price line reads "for Paris". R04 and R06 close after their chapter (overworld_and_towns §2.4); R07 and R10 reopen in CH-14.

### 10.8 Seoul shops (CH-E1) and the CCR fallback

| Shop | Stock (won) |
|---|---|
| Haneul Mart (S03, S04, S07, S12) | Barley Tea 1,500 · Gimbap 8,000 · Ssanghwa Tonic 36,000 · Abalone Porridge 120,000 · Canned Coffee 6,000 · Red Ginseng Shot 30,000 · Ammonia Inhalant 8,000 · Wild Ginseng Root 300,000 · Eye Drops 2,000 · Throat Spray 2,400 · Pocket Tuner 8,000 · Cold Medicine 60,000 · Hot Pack 18,000 · Lunchbox Set 80,000 · Hand Warmer 1,600,000 |
| Ms. Bae's cart (S03) | Hotteok 2,000 |
| Kang Piano Service (S15) | Graphite Baton 1,120,000 · Ash Baton 1,380,000 · Pernambuco Bow 1,380,000 · Birch Gungchae 1,380,000 · Voicing (§2.4, list price × 200) |
| Gyeoul Outfitters (S07, CCR) | Beanie 800,000 · Winter Parka 880,000 · Earmuffs 960,000 · Long Padding 1,040,000 · Headphones 2,000,000 |
| Hanji-bang (S12, CCR) | Synthetic Flat 1,120,000 · Weasel-Hair But 1,380,000 · Norigae Tassel 1,600,000 · Lucky Pouch 1,700,000 |

Seoul shops take only won; francs become won at Mr. Baek's (₩200 per franc, CANON §14). Paying with 1833 coins in public is a Spotlight raise (+3, CANON §11e), so no counter accepts them.

**Fallback if the new-shop CCR (overworld_and_towns) is refused.** No item, price or window changes; only the counter's name does, to a canon name. Mercerie Aubert's stock is sold at the Auberge du Lion d'Argent's counter (R04); Lambotte's in the yard of the Hôtel de la Meuse (R06); Weiss's at the Gasthof zum Goldenen Anker (R07); the Pharmacie du Dôme's at the Hôtel de la Cathédrale (R10); Gyeoul Outfitters' and Hanji-bang's head, body and relic stock at Haneul Mart's S07 and S12 branches; Hanji-bang's two brushes at Kang Piano Service.

### 10.9 Inns and paid services

| Chapter (tier) | Inn night (CANON §14) | Inns open |
|---|---|---|
| CH-02 (Étude) | 10 F (*Au Diapason Fêlé* free with KEY-06) | P02 Lys d'Or, P04 |
| CH-03–CH-04 (Prélude) | 15 F | + — |
| CH-05–CH-07 (Nocturne) | 25 F | + P10 Lyre, P24 Trois Moulins (CH-06) |
| CH-08–CH-09 (Rhapsodie) | 40 F | + P16 Arcades |
| CH-10–CH-13 (Concerto) | 60 F | R04 Lion d'Argent (CH-10), R06 Meuse, R07 Goldenen Anker, R10 Cathédrale (CH-11), P02 and P10 (CH-12–CH-13) |
| CH-14–CH-15 (Symphonie) | 100 F | every Paris inn, R07, R10 |
| CH-E2 (Opus Magnum) | 150 F (the Atelier and Marthe's dispensary rest free) | every Paris inn |
| CH-E1 (Seoul) | ₩60,000 at Hotel Ginkgo (CCR, only while the S04 lobby is blocked) | S03 |

**Paid services cited here for the economy check (§13), owned elsewhere:** Voicing (§2.4); press rebuttal 500 F (CANON §11e); SQ-07 step 2, Théo's convalescence, 300 F (LAW-23); SQ-12 the Atelier 5,000 F (CANON §0c) or the CH-E2 restoration 5,000 F (CANON §12); fiacre 2 F, omnibus 6 sous, barge 1 F, diligence 40–120 F a leg (CANON §11h, overworld_and_towns §2.3–§2.4); the keepsake forge is free (§2.5).

---

## 11. Rare Items: Steals, Drops, Duel Prizes, Finds

### 11.1 Family loot (binding item lists; the bestiary assigns them per ENM)

Every ENM carries a common and a rare steal (CANON §11a) and a common and a rare drop. The bestiary gives each ENM its family's four items below; where a family spans two tiers it may use the second line from the chapter shown. Odds: steal clamp(40 + LCK_a − LCK_t, 5, 95)% with 1 success in 8 rare and the 8th-success pity; drops rare clamp(4 + ΔLCK/4, 2, 16)%, then common 35% (formulas_and_curves §5.4–5.5). Names are UI names; ITM numbers are in §3–§6.

| Family (CANON §12) | Where, when | Common steal | Rare steal | Common drop | Rare drop |
|---|---|---|---|---|---|
| Ossuary Echoes | P01 CH-01; Z1 strays CH-02–CH-04 | Tisane | Sal Volatile | Smelling Salts | Beeswax Candle |
| Lime Wraiths | P01 | Four Thieves | Eyewash | Four Thieves | Sal Volatile |
| Quarry rats, rats, sewer rats | P01, P04, P17, Z1, Z7 | Tisane | Squib | Tisane | Café Noir |
| Miasma Wraiths | Z1, Z3, Z7 (CH-02+) | Four Thieves | Eau de Mélisse | Four Thieves | Courage Draught |
| Gros-Louis's smugglers | P04 cellars, CH-02 | Café Noir | Squib | Tisane | Sal Volatile |
| Choir Echoes | P03 undercroft, CH-03 | Throat Lozenge | Pitch Pipe | Throat Lozenge | Courage Draught |
| Black Coats | P08, Z4, CH-04 | Courage Draught | Fencing Glove | Tisane | Lampblack Pouch |
| Tocsin Echoes | P08; Z4 night CH-05+ | Eyewash | Tocsin Bell | Eyewash | Pitch Pipe |
| Gaslight Wisps | P10; Z2, Z5 night (CH-05+) | Eyewash | Leyden Jar | Beeswax Candle | Rosin Cake |
| Pickpocket gangs | P10, Z2, Z4–Z6 | Café Noir | Courier's Boots | Bouillon | Opera Glass |
| Gargoyle Echoes | Z3 (Cité) | Sculptor's Oil | Lampblack Pouch | Sculptor's Oil | Opera Glass |
| Watchers (secrecy_and_trust §2.8) | Town maps CH-06+; informants to CH-08, Grey Hand lookouts after | Café Noir | Opera Glass | Eyewash | Courier's Boots |
| Tableau Echoes | P13, CH-06 | Sculptor's Oil | Madder Lake | Bouillon | Hourglass Sand |
| Brücke Mk. I automata | P18, CH-07 | Hourglass Sand | Brass Escapement | Leyden Jar | Brass Escapement |
| Cloaca Echoes | P17, CH-08 | Four Thieves | Seltzer Siphon | Four Thieves | Panacea |
| Phantom Quartet spectres | P17 | Hoffmann's Drops | Bass String | Hoffmann's Drops | Rosin Cake |
| Julien's café toughs | P17; P16 night | Café Noir | Absinthe | Bouillon | Fencing Mask |
| Grey Hand | P31 CH-09, P26, P27; Z6 night and W01 Shadow formations CH-09+ | Bouillon (Cordial from CH-12) | Grey Kid Glove | Sal Volatile | Panacea |
| Barrel automata | P31 | Hoffmann's Drops | Brass Escapement | Seltzer Siphon | Tocsin Bell |
| Hunter Automata | R01, R05, Y2, Y3, Y8 | Cordial | Huntsman's Horn | Leyden Jar | Steel Busk |
| Boar | Y1–Y3 | Bouillon | Cordial | Hot Chestnuts | Cordial |
| Frontier smugglers | Y4, Y5, Y7, Y8, R13 | Café Noir | Tokaji Wine | Cordial | Lodestone Charm |
| River automata | R08, Y5, Y6 | Seltzer Siphon | Brass Escapement | Glacière Ice | Bellows Charge |
| Lorelei Echoes | R09, Y6 | Smelling Salts | Eau de Mélisse | Smelling Salts | Valerian Tincture |
| Abbey Echoes | P26, CH-12 | Throat Lozenge | Chocolat | Cordial | Sel de Vie |
| Living Tableaux (and CH-E2 squads) | P26 CH-12; CH-E2 streets, E01, E05 | Sculptor's Oil (Grand Cordial in CH-E2) | Gilder's Leaf | Cordial (Smelling Bottle in CH-E2) | Tableau Rapier |
| Grey Hand assassins | P27, CH-13 | Cordial | Grey Kid Glove | Panacea | Tocsin Bell |
| Stage-machinery automata | P27; W01 war strays CH-14 | Leyden Jar | Brass Escapement | Leyden Jar | Ruggieri Rocket |
| Roussel's Cleaners | P34; W01 war overlay, CH-14 | Cordial | Garde Gorget | Panacea | Smelling Bottle |
| Vane's animated collection | P34 | Sculptor's Oil | Venetian Mirror | Chocolat | Gilder's Leaf |
| Forge automata | R02, CH-14 and CH-E2 | Grand Cordial | Smith's Wristband | Galvanic Pile | Cuirassier's Vest |
| Amalgam Echoes (Lutèce constructs, turnstile golems, neon wraiths) | P29, CH-15 | Grand Cordial | Élixir | Smelling Bottle | Clef Chip |
| Grey Hand elite | W01 Shadow formations CH-09+; P30, CH-16 | Sel de Vie | Grey Kid Cap | Grand Cordial | Grey Kid Glove |
| Stilled Echoes | P30, CH-16 | Smelling Bottle | Élixir | Café Royal | Élixir |
| Residual Echoes | CH-E2 streets, E03 | Smelling Bottle | Élixir | Café Royal | Élixir |
| Leftover automata | CH-E2 streets, E05 | Galvanic Pile | Brass Escapement | Grand Vichy | Smith's Wristband |
| Static automata | S08; W03 static pockets, CH-E1 | Pocket Tuner | Headphones | Canned Coffee | Hand Warmer |
| Ossia phantoms | S09, CH-E1 | Red Ginseng Shot | Élixir | Wild Ginseng Root | Élixir |

*Absinthe* and *Tokaji Wine* are gift items (§9) with no battle use; a café tough's flask and a smuggler's cask are where a T-rated game keeps its alcohol (CANON §16e).

### 11.2 Boss rewards (guaranteed) and boss steals (for bosses.md)

The guaranteed reward is binding here for its item; `bosses` fixes everything else about the fight. The steal column is this doc's proposal for each boss's Libretto `STEAL` line (bosses.md may adopt or replace it, never with an item outside this doc). Duel-format and invulnerable bosses have no steal.

| BOSS | Guaranteed item reward | Steal: common / rare |
|---|---|---|
| BOSS-01 Ossuary Warden | Sal Volatile ×2 | Tisane / Beeswax Candle |
| BOSS-02 Gros-Louis | The stolen francs back (CANON §13); Squib ×3 | Café Noir / Courier's Boots |
| BOSS-03 Herz (duel) | Herz Medal (any result) | — |
| BOSS-04 Le Chantre | Pitch Pipe ×2 · Throat Lozenge ×3 | Throat Lozenge / Felt Beret |
| BOSS-05 Marlot | Fencing Glove · Courage Draught ×3 | Courage Draught / Opera Glass |
| BOSS-06 Passage Chimera | Beeswax Candle ×3 | Eyewash / Rosin Cake |
| BOSS-07 *The Raft* | Vichy Water ×3 | Sculptor's Oil / Eau de Mélisse |
| BOSS-08 Thalberg (duel) | Won: Rossini's Napkin · lost: Three-Hand Glove | — |
| BOSS-09 Escapement Hound | Brass Escapement | Leyden Jar / Practice Mute |
| BOSS-10 Cloaca Leviathan | Seltzer Siphon ×3 | Four Thieves / Panacea |
| BOSS-11 Julien | Hoffmann's Drops ×3 (KEY-15 by story) | Café Noir / Naples Coffee |
| BOSS-12 Roussel I | Panacea ×2 | Bouillon / Grey Kid Glove |
| BOSS-13 Le Meneur de Loups | Cordial ×3 · Leyden Jar ×2 | Cordial / Huntsman's Horn |
| BOSS-14 The Rheinwolf | Glacière Ice ×3 | Seltzer Siphon / Brass Escapement |
| BOSS-15 Delorme | Golden Compass | Sculptor's Oil / Gilder's Leaf |
| BOSS-16 Archon: The Audience | — (survival) | — ("Nothing to take.") |
| BOSS-17 Grand Concert: Stage | OPS-25 if Own Voice ≥ 6 (§8) | — |
| BOSS-18 Brücke and the Phonautograph | Stopped Horn | Leyden Jar / Brass Escapement |
| BOSS-19 Roussel II | Grey Kid Glove | Cordial / Grey Kid Cap |
| BOSS-20 Lord Vane (duel) | Cambridge Sabre (§3.7: never missable) | — |
| BOSS-21 Roussel and the Cleaners | Grand Cordial ×3 · Smelling Bottle ×2 | Grand Cordial / Garde Gorget |
| BOSS-22 Warden of Lutèce | Lutèce Helm | Grand Cordial / Élixir |
| BOSS-23 Warden of Hanseong | Frock of Hanseong | Smelling Bottle / Élixir |
| BOSS-24 Orpheus Descending | Orpheus Mask | Smelling Bottle / Élixir |
| BOSS-25 Ad Astra | Varga Lens | Café Royal / Élixir |
| BOSS-26 Archon, Baron d'Orsenne | Élixir | Grand Cordial / Sel de Vie |
| BOSS-27 The Stilled Hour | — | — (invulnerable until the Octave) |
| BOSS-28 Archon and the Engine | Élixir ×2 (KEY-29 by story) | Café Royal / Élixir |
| BOSS-29 Automaton "Line 2" | Pocket Tuner ×3 · Élixir | Canned Coffee / Hand Warmer |
| BOSS-30 Elias Brandt | Élixir ×2 | Red Ginseng Shot / Headphones |
| BOSS-31 Ossia | Sinmyeong · OPS-31 · the Baton of Tomorrow (§12.2) · Delorme's notebook page (LAW-27, lore) | Wild Ginseng Root / Élixir |
| BOSS-32 The Salon Jury (duel) | KEY-40 (canon) | — |
| BOSS-33 Delorme's Masterwork | Ground Lens | Grand Cordial / Laurel Circlet |
| BOSS-34 The Unwritten | OPS-32 · the Baton of Tomorrow (§12.2) · Delorme's notebook page | Café Royal / Élixir |
| BOSS-35 Thalberg rematch (duel) | §11.3 | — |
| BOSS-36 Paganini's Shadow | Paganini String · OPS-28 | Café Royal / Rosin Cake |
| BOSS-37 The Lorelei Echo | OPS-29 · Valerian Tincture ×3 | Smelling Salts / Eau de Mélisse |
| BOSS-38 The Forge Colossus | OPS-27 · Cuirassier's Vest | Galvanic Pile / Smith's Wristband |
| BOSS-39 The Needle Echo | Encore Locket | Grand Cordial / Élixir |
| BOSS-40 The Philosophers' Echo | OPS-26 (from the second to fall) | Café Royal / Élixir (each) |
| BOSS-41 "Hit" | First Hit: Brass Escapement; later Hits: Panacea | Leyden Jar / Brass Escapement |
| BOSS-42 The Turnkey | Courage Draught ×2 | Bouillon / Grey Kid Cap |
| BOSS-43 Da Capo: The Unstruck Bell | Unstruck Bell | Élixir / Laurel Ring |

### 11.3 Duel, salon and busking prizes

Salons and piano duels are this game's colosseum: no wager, but every named room pays once for a great evening.

| Contest | Condition | Prize |
|---|---|---|
| BOSS-03 Herz cutting contest (CH-03) | Any result | Herz Medal (ITM-504) |
| BOSS-08 Thalberg (CH-07) | Won / lost | Rossini's Napkin (ITM-510) / Three-Hand Glove (ITM-511) |
| BOSS-20 Lord Vane (CH-14) | Won; if lost, found at P14 after WS-17 | Cambridge Sabre (ITM-288) |
| BOSS-35 Thalberg rematch (CH-14 or CH-E2) | Won | Belgiojoso Cameo (ITM-535) if not owned; else Three-Hand Glove if not owned; else Grand Cordial ×3 |
| SQ-20 The Salon Circuit (CH-14) | Completed | Belgiojoso Cameo (ITM-535) |
| Salon Lavergne (T2, Romantic) | First optional salon with Rapture ≥ 90 | Gilt Lorgnette (ITM-546) |
| Salon Bastide (T2, Novel) | Same | Feuilleton (ITM-547) |
| Salon Merlin (T3, Romantic) | Same | Havana Mantilla (ITM-548) |
| Salon d'Agoult (T3, Sacred) | Same | Ivory Missal (ITM-549) |
| Countess Apponyi (T3, Virtuosic) | Same | Opal of Vienna (ITM-550) |
| T1 *Au Diapason Fêlé* | First salon (CH-02) | Busker's Bowl (ITM-501) |
| BOSS-17, BOSS-32 | Story results | OPS-25 (Own Voice ≥ 6); KEY-40 |

**Busking ladder (CH-E1, 8 spots in CANON §4f order; one prize each, on first clear).**

| Spot | Place | Prize |
|---|---|---|
| 1 | Hongdae station exit plaza (S07) | Hot Pack ×3 |
| 2 | Hongdae walking-street stage | Red Ginseng Shot ×3 |
| 3 | Hongdae playground corner | Pocket Tuner ×3 |
| 4 | Insadong courtyard (S12) | Concert Pass (ITM-545) |
| 5 | Yanghwajin riverside park (S14) | Wild Ginseng Root ×2 |
| 6 | Namsan cable-car plaza | Headphones (ITM-543) |
| 7 | Jeong-dong ginkgo road (S03) | Lucky Pouch (ITM-541) |
| 8 | Bosingak plaza (S11): Legend | *Hanseong* (ITM-369, §12.5); the Remembrances rise to Lv 55 power (CANON §4f) |

### 11.4 Unsold rarities

| Item | Shop | Steal | Drop | Chest or find | Boss or prize |
|---|---|---|---|---|---|
| Élixir (ITM-007) | Never | Amalgam, Stilled, Residual Echoes; Ossia phantoms (rare); BOSS-22–25, 28, 31, 34, 39, 40 (rare) | Stilled, Residual Echoes; Ossia phantoms (rare) | R02 ×1, P29 ×2, P30 ×1, S08 ×1, E05 ×1 | BOSS-26 ×1, BOSS-28 ×2, BOSS-29 ×1, BOSS-30 ×2 |
| Grey Kid Cap (ITM-415): **steal-only** | Never | Grey Hand elite (rare); BOSS-19, BOSS-42 (rare) | Never | Never | Never |
| Garde Gorget (ITM-526): **steal-only** | Never | Roussel's Cleaners; BOSS-21 (rare) | Never | Never | Never |
| Tableau Rapier (ITM-200): **drop-only** | Never | Never | Living Tableaux (rare) | Never | Never |
| Clef Chip (ITM-536): **drop-only** | Never | Never | Amalgam Echoes (rare) | Never | Never |
| Brass Escapement (ITM-525) | Never | Mk. I, barrel, river, stage and leftover automata (rare) | Mk. I automata (rare) | — | BOSS-09; first BOSS-41 |
| Grey Kid Glove (ITM-524) | Never | Grey Hand, assassins (rare); BOSS-12 (rare) | Grey Hand elite (rare) | — | BOSS-19 |
| Golden Lyre (ITM-537) | Never | — | — | S09 summit (CH-E1); E03 (CH-E2) | — |
| Paganini String (ITM-531) | Never | — | — | — | BOSS-36 (BQ-PC07 climax; missable) |
| Paving Stone (ITM-041) | Never | — | — | ×5 at P08 (CH-04) | — |

Sel de Vie appears before its CH-14 shop debut only as an Abbey Echo rare drop (CH-12), and once as a find at P28 (CH-14, overworld_and_towns §5).

### 11.5 Chests and finds by location (item lists for dungeons.md)

`dungeons` places the tiles; this table fixes what is in them. Town examine points are overworld_and_towns §5's (its items are named from canon lists and numbered here); TUT pages and Study chests are skills_and_progression's.

| LOC | Chapter | Contents |
|---|---|---|
| P01 Saint-Denis Galleries | CH-01 | Workman's Cap · Tisane ×3 · Sal Volatile |
| P04 cellars | CH-02 | Cartouche Glove (canon) · Rome Sword-cane · Squib ×3 |
| P03 undercroft | CH-03 | Prélude Hat · Courage Draught ×2 |
| P08 Barricade | CH-04 | Paving Stone ×5 · Pitch Pipe ×2 |
| P10 Passage de l'Opéra nest | CH-05 | Nocturne Coat · Beeswax Candle ×2 |
| P13 Louvre | CH-06 | Copyist's Apron · Sculptor's Oil ×2 |
| P18 Clockwork Undercroft | CH-07 | Leyden Jar ×2 · Hourglass Sand ×2 |
| P17 Sewers | CH-08 | Chios Rapier · Seltzer Siphon ×2 · Panacea |
| P31 Bercy | CH-09 | Silver Baton · Bouillon ×3 |
| R01 Franchard gorge | CH-10 | Huntsman's Horn |
| R05 Vallée Noire | CH-10 | Concerto Baton · Concerto Sabre · Cordial ×2 |
| R08 *Concordia* | CH-11 | Seraing Maul (boiler deck) · Riverman's Oilskin |
| R07 Academy library | CH-11 | Haydn Folio |
| R09 Lorelei | CH-11 or CH-14 | Valerian Tincture ×2 |
| P26 Val-de-Grâce | CH-12 | Palette Knife (abbey wing, Lucile's solo) · Ruggieri Rocket ×2 · Chocolat ×2 |
| P27 Opéra | CH-13 | Gala Baton (corridors) · Rob Roy Cane (rafters) · Sylphide Gauze (rafters, Taglioni's dressing room) · Opéra Sabre (stage machinery) · Opera Hat (cloakroom) |
| P34 Hôtel de Vane | CH-14 | Grand Cordial ×2 |
| R02 Château d'Orsenne | CH-14 | Waverley Cane · Élixir |
| P38 Philosophers' Tombs | CH-14 | Sel de Vie |
| P29 Chrono-Labyrinth | CH-15 | Lutèce zones: Magnum Brush, Magnum Rapier, Magnum Folio · Hanseong zones: Magnum Baton, Magnum Quill · Orpheus zones: Magnum Sword-cane, Magnum Hammer, Magnum Sabre, Magnum Cane · each of the three zones and the Heart gate: Magnum Hat, Magnum Coat (4 of each) · Élixir ×2 |
| P30 Heart Chamber | CH-16 | Élixir (before BOSS-26's Lectern) |
| S08 Euljiro / Line 2 | CH-E1 | Élixir · Abalone Porridge ×2 |
| S09 Namsan | CH-E1 | Golden Lyre (summit) |
| E05 Delorme's Atelier | CH-E2 | Élixir · Grand Cordial ×2 |
| E03 The Dead Heart | CH-E2 | Golden Lyre |

The P29 and P30 Opus Magnum pieces exist because no shop opens between CH-14 and the finale (CANON §0c point of no return): the CH-16 four reach BOSS-26 with Opus Magnum weapons and armour, which the CANON §10e CH-16 row assumes.

---

