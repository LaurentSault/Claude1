# Items, Equipment & Shops

Status: v1.0 — 2026-10-06 · Owns: every item name (ITM), stat, price and location; shop inventories by chapter; key-item detail (KEY-01–KEY-41 as expanded here); Voicing and keepsake-forge rules; ultimate (Lost Era) equipment and the quests that grant it · Depends on: docs/05_systems/combat_ensemble.md, docs/06_balance/formulas_and_curves.md · Related: docs/07_world/overworld_and_towns.md (shop placement, hidden-item spots), docs/05_systems/secrecy_and_trust.md (gift reactions) · Canon: docs/00_CANON.md

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

**What this doc fixes.** Every ITM entry: name, UI name, stats, effect, price, sell value, and every place it can be obtained (shop, chest, steal, drop, quest, story). It also fixes what each canon shop sells in each chapter (CANON §12 names, CANON §14 bands), the Voicing upgrade service, the keepsake forge, and the detail behind every canon KEY item. **It does not fix** formulas (formulas_and_curves), battle rules (combat_ensemble), enemy steal/drop assignments by ENM ID (bestiary; this doc names the items and the families that carry them), chest tiles (dungeons), quest steps (side_and_bond_quests), HRM content of Opus Scores (skills_and_progression), or income tables (salons_duels_and_economy).

**Binding inputs.** Price bands, tiers, slots, anchor consumables, Lost Era names and requirements, and the KEY list: CANON §14. Weapon ATK target ≈ 10 + 2.2L: CANON §10e. Armour DEF/RES targets per tier (head + body, split 40/60), relic DEF/RES budget (+10 each, CH-10 on), weapon-class accuracy: formulas_and_curves §9. Drop and steal odds (rare clamp(4 + ΔLCK/4, 2, 16)%, common 35%, steal 1-in-8 rare with an 8th-success pity): formulas_and_curves §5.4–5.5. Relic keys `ENC_HALF` (×0.5) and `ENC_NONE` (×0): formulas_and_curves §5.7. Formation odds that relics may move: combat_ensemble §5.2.

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
| ITM-500–569 | Relics | 500–545 |
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

Rules: stages are bought in order; a fully voiced weapon has cost 175% of its price, which keeps Voicing a money sink rather than a tier skip (+6 ATK is about +5% AR at CH-09). Story weapons without a list price are voiced as if priced at their tier's named price. **Lost Era weapons, ITM-100 Tuning Fork and the Seoul Lost Era pieces cannot be voiced.** The stage shows as a suffix in its own column of the Equip window ("+2"), never inside the 16-character name. *Salons note:* this doc defines Voicing for weapons only; if salons_duels_and_economy voices the duel pianos too, it shares the name and this service window.

### 2.5 Keepsake forge (CH-E2, CANON §6, §14)

In the Paris branch, Pleyel and Théo forge each friend's Lost Era weapon in the workshop yard at LOC-P12 when three conditions are met: (1) the friend is at bond **R10** and (2) has finished his or her **bond-quest finale**, and (3) the friend's **KEY-30 keepsake** was received in CH-17. No fee: Pleyel charges nothing for "metal that is not only metal" (historical_cast, NPC-15 line). Forging takes one visit and no Evening (the epilogues have no Evening budget, CANON §11i). A farewell skipped in CH-17 locks that forge until Da Capo (CANON §6). Requirements and effects per weapon: §12.

---

## 3. Weapons

Source codes: **Shop** (shop, chapter of first stock), **Chest** (dungeons places the tile in the named LOC), **Steal/Drop** (bestiary assigns the ENM within the named family), **Quest** (side_and_bond_quests places the step), **Story** (automatic). "Sell" is half price; ◆ = unsellable.

### 3.1 Batons — Min-jun (row-free, Acc 95)

| ITM | Name (UI) | ATK | ART+ | Element / effect | Source | Price |
|---|---|---|---|---|---|---|
| 100 | Tuning Fork | 12 | +1 | REP-00 *Resonance* Stun base +10 · "It hums before it strikes." | Story CH-P (on his person, CANON §5f) | ◆ |
| 101 | Étude Baton | 14 | +1 | — | Shop: Armurerie Vidal CH-02 | 60 |
| 102 | Prélude Baton | 24 | +2 | — | Shop: Armurerie Vidal CH-03 | 220 |
| 103 | Berlioz's Baton | 30 | +2 | Each Conduct adds +5 Crescendo · "From the barricade, with love." | Story, end of CH-04 (CANON §4b) | ◆ |
| 104 | Nocturne Baton | 36 | +3 | — | Shop: Vidal CH-05 | 560 |
| 105 | Ebony Baton | 42 | +3 | Recital Movement I costs −2 INS | Shop: Vidal & Fils CH-07 | 980 |
| 106 | Rhapsodie Baton | 52 | +4 | — | Shop: Vidal CH-08 | 1,150 |
| 107 | Silver Baton | 54 | +4 | Recital III bursts +10% | Shop: Vidal & Fils CH-09 · Chest: P31 Bercy | 1,380 |
| 108 | Concerto Baton | 62 | +5 | — | Shop: Lambotte CH-11 (CCR) · Vidal CH-12 | 2,100 |
| 109 | Rehearsal Baton | 70 | +5 | A Recital breaks only on a hit ≥ 30% of max HP (not 20%) | Shop: Vidal & Fils CH-12 | 2,800 |
| 110 | Gala Baton | 77 | +5 | Fight is LIGHT | Chest: P27 corridors (CH-13) | — (sell 1,725) |
| 111 | Symphonie Baton | 85 | +6 | — | Shop: Vidal CH-14 | 3,900 |
| 112 | Mended Baton | 89 | +6 | A Conducted ally also gains Swell +1 · "Théo re-trued the crack." | Story CH-14 (§12.2: ITM-103 reforged by Théo) | ◆ |
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
| 136 | Nohant Sable | 66 | +5 | POINTILLÉ +10% · "Ma petite Lumière. — G." | Story CH-10: Sand's gift at Nohant after Mending scene 1 | ◆ |
| 137 | Concerto Brush | 62 | +5 | — | Weiss CH-11 (CCR) · Ravenel CH-12 | 2,100 |
| 138 | Munich Sable | 70 | +5 | Plein Air +25% also under Dusk | Weiss CH-11 (CCR) · Ravenel CH-12 | 2,800 |
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
| 168 | Concerto Sword-cane (Conc. Swordcane) | 66 | — | Coutellerie, Vidal CH-12 | 2,100 |
| 169 | Francs-juges Cane | 74 | Tutti +10% | Coutellerie CH-12 | 2,800 |
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
| 198 | Concerto Rapier | 66 | — | Lambotte CH-11 (CCR; Delacroix is in Paris, buy ahead) · Vidal CH-12 | 2,100 |
| 199 | Sardanapalus Rapier (Sardanapale) | 74 | Fight is FIRE; Canvas *Sardanapale* +10% | Vidal & Fils CH-12 | 2,800 |
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
| 226 | Concerto Hammer | 66 | — | Lambotte CH-11 (CCR) · Coutellerie CH-12 | 2,100 |
| 227 | Liège Hammer | 74 | Recluse also triggers when he is the only member in the front row | Lambotte CH-11 (CCR) · Coutellerie CH-12 | 2,800 |
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
| 254 | Concerto Quill | 62 | +5 | — | Lambotte CH-11 (CCR) · Vidal CH-12 | 2,100 |
| 255 | Mazurka Quill | 70 | +5 | *Repay* with 3 charges also gives Allegro | Lambotte CH-11 (CCR) · Vidal & Fils CH-12 | 2,800 |
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
| 284 | Concerto Sabre | 66 | +3 | — | Lambotte CH-11 (CCR) · Coutellerie CH-12 | 2,100 |
| 285 | Liège Sabre | 74 | +3 | Fight is BOLT | Lambotte CH-11 (CCR) · Coutellerie CH-12 | 2,800 |
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
| 408 | Turban of Tangier | 5/4 | M.EVA +5 | DE, LI, AL | Quest: BQ-PC04, second step | ◆ |
| 410 | Fencing Mask | 7/4 | Physical counter damage taken −50% (Riposte, Chiaroscuro and Libretto `ON HIT`) | BE, DE, LI, AL | Coutellerie CH-08 | 1,050 |
| 411 | Lace Cap | 6/6 | Immune to Hush | All | Vidal & Fils CH-09 | 1,100 |
| 413 | Rhine Cap | 10/7 | Immune to Lento | All | Lambotte CH-11 (CCR) · Vidal CH-12 | 2,200 |
| 414 | Pelisse Hood | 9/9 | Immune to Out of Tune and Discord | All except MJ (already immune) | Weiss CH-11 (CCR) · Vidal & Fils CH-12 | 2,400 |
| 415 | Grey Kid Cap | 11/8 | Immune to Stagefright | All | Steal: Grey Hand elites, P26 (rare) | — (sell 1,250) |
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
| 464 | Travelling Cloak | 14/11 | Immune to Lento | All | Lambotte CH-11 (CCR) · Vidal CH-12 | 2,300 |
| 465 | Berry Smock | 13/12 | Dawn regeneration doubled for the wearer | All | Mercerie Aubert CH-10 (CCR) · Vidal & Fils CH-12 | 2,200 |
| 466 | Buff Coat | 17/11 | Physical damage taken −10% | BE, DE, LI, AL, JW | Coutellerie CH-12 | 2,600 |
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
| 511 | Three-Hand Glove | — | Fight becomes EARTH / LIGHT / WIND, best multiplier applies (dual rule, CANON §10c) | Prize: BOSS-08 lost (Thalberg's courtesy) · or BOSS-35 won | ◆ |
| 512 | Pleyel Tuning Hammer (Tuning Hammer) | — | **CHRONO resist ×0.5** (CANON §10c); immune to Lento | Story CH-08: Pleyel's thanks after the Sat 21 Sep concert (KEY-17) | ◆ |
| 513 | Copal Varnish | auto-Protect | Wearer starts each battle with **Varnish** | Corbel CH-08 | 2,200 |
| 514 | Tortoise Fan | — | EVA +8, M.EVA +8 | Corbel CH-08 | 2,000 |
| 515 | Postilion Boots | Hermes Sandals | Wearer starts each battle with **Allegro** | Corbel CH-09 | 2,400 |
| 516 | Shepherd's Bell | Tintinnabar | Wearer regains 1 HP per field step | Story CH-10: Père Grillon at Nohant, after Lucile's Pissarro-style Berry canvas | ◆ |
| 517 | Steel Busk | — | DEF +10 | Lambotte CH-11 (CCR) · Corbel CH-12 | 2,800 |
| 518 | Lodestone Charm | — | RES +10 | Weiss CH-11 (CCR) · Corbel CH-12 | 2,800 |
| 519 | Huntsman's Horn | — | Preemptive +10 points (cap 40%, formulas_and_curves §4.10) | Chest: R01 Franchard gorge (CH-10) · Corbel CH-12 | 3,000 |
| 520 | Smith's Wristband | Hyper Wrist | STR +15% | Weiss CH-11 (CCR) · Corbel CH-12 | 3,400 |
| 521 | Ivory Hairpin | Gold Hairpin | INS costs ×0.75 | Weiss CH-11 (CCR) · Corbel CH-12 | 4,200 |
| 522 | Academy Medal | Earring | Magical damage dealt +15% | Corbel CH-12 | 4,000 |
| 523 | Gilder's Leaf | Barrier Ring (auto-Shell) | Wearer starts each battle with **Glaze** | Corbel CH-12 | 3,800 |
| 524 | Grey Kid Glove | — | Crescendo gains from this wearer ×1.25 (not with Groove) | Steal: Grey Hand elites, P31 and P26 (rare) | — (sell 1,500) |
| 525 | Brass Escapement | — | Wearer's battle-start gauge is at least 128 | Drop: Brücke Mk. I automata, P18 (rare) · Steal: river automata, R08 | — (sell 1,200) |
| 526 | Garde Gorget | True Knight | Wearer intercepts single-target hits on allies below 25% HP (as Bulwark, without the −50%) | Steal: Roussel's Cleaners, P34 (rare) | — (sell 2,500) |
| 527 | Sylphide Ribbon | Ribbon | Immune to Smoke, Hush, Reverie, Delirium, Stagefright, Lento, Marble, Frenzy, Out of Tune, Discord, Swing, Miasma | Story CH-13: Taglioni (NPC-37) ties it on Lucile's wrist after the gala | ◆ |
| 528 | Nohant Metronome | — | **CHRONO resist ×0.5** (canon); immune to Swing · "Pour celui qui bat mal la mesure. — G." | Find: Sand's piano at Nohant, CH-14 revisit (overworld_and_towns §7) | ◆ |
| 529 | Venetian Mirror | Wall Ring | Wearer starts each battle with **Mirror** | Corbel CH-14 | 6,500 |
| 530 | Encore Locket | Reraise | Wearer starts each battle with **Encore** | Corbel CH-14 | 7,800 |
| 531 | Paganini String | Offering | Fight strikes 4 times, each ×0.5, never crits | Drop: BOSS-36 guaranteed (bosses binds) | ◆ |
| 532 | Felted Clapper | Moogle Charm | `ENC_NONE`: no random encounters (scripted, touch and boss battles still occur) | Story CH-14: Jacquot at Notre-Dame's bell chamber (LOC-P32) | ◆ |
| 533 | Premier Prix | Exp. Egg | EXP received ×1.5 | Story CH-14: Cherubini, after Hiller's concert (Sun 15 Dec), "an old prize nobody claimed" | ◆ |
| 534 | Fouine's Ring | Sneak Ring | Pilfer success +20 points | Quest CH-14: return La Fouine's stolen dice (P10) | ◆ |
| 535 | Belgiojoso Cameo | — | M.EVA +15; immune to Hush | Prize: BOSS-35 won (CH-14 or CH-E2) · or SQ-20 completion | ◆ |
| 536 | Clef Chip | — | Wearer's CHRONO damage dealt +20% | Drop: Amalgam Echoes, P29 (rare) | — (sell 3,500) |
| 537 | Golden Lyre | Economizer (half) | INS costs ×0.5 (does not stack with Ivory Hairpin; Inspired then gives ×0.25) | Chest: E03 Dead Heart (CH-E2) · Chest: S09 Namsan summit (CH-E1) | ◆ |
| 538 | Medal of 1834 | — | DEF +10, RES +10 | Vidal & Fils CH-E2 | 9,800 |
| 539 | Laurel Ring | — | All stats +3 (STR, ART, DEF, RES, TMP, LCK) | Corbel CH-E2 | 11,000 |
| 540 | Norigae Tassel | — | Wearer starts each battle with **Cantabile** | Hanji-bang CH-E1 (CCR) | ₩1,600,000 |
| 541 | Lucky Pouch | Coin Toss | Won after battle ×1.5 · *bokjumeoni* | Hanji-bang CH-E1 (CCR) | ₩1,700,000 |
| 542 | Hand Warmer | — | Immune to Lento, Fermata | Haneul Mart CH-E1 | ₩1,600,000 |
| 543 | Headphones | — | Immune to Reverie, Delirium, Hush | Gyeoul Outfitters CH-E1 (CCR) | ₩2,000,000 |
| 544 | Transit Card | Sprint Shoes | Field speed ×1.5 on Seoul maps; subway rides free | Story CH-E1: Seo-yeon's spare card | ◆ |
| 545 | Concert Pass | — | Party Crescendo +20 at battle start | Busking ladder, rank 4 (Headliner) | ◆ |

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
| 017 | Panacea **A** | Cure all negative statuses except KO | — | Laborde CH-07 | 300 |
| 018 | Picnic Hamper **A** | Full party rest at a Lectern | — | Laborde CH-05 | 400 |
| 019 | Barley Sugar | +15 INS | *Sucre d'orge* | Laborde CH-03 | 12 |
| 020 | Vichy Water | 300 HP to the party | Bottled spa water | Laborde CH-05 | 120 |
| 021 | Eau de Mélisse | Party Cantabile | The Carmelite water | Laborde CH-07 | 90 |
| 022 | Hoffmann's Drops | Cure Lento, Swing | Ether drops | Laborde CH-08 | 30 |
| 023 | Grand Vichy | 1,000 HP to the party | — | Laborde CH-12 | 600 |
| 024 | Valerian Tincture | Cure Delirium, Frenzy | — | Pharmacie du Dôme CH-11 (CCR) · Laborde CH-12 | 80 |
| 025 | Smelling Bottle | Revive at 25% and cure all statuses | — | Laborde CH-14 | 450 |
| 026 | Café Royal | +60 INS to the party | Coffee with cognac | Laborde CH-14 | 900 |
| 027 | Hot Chestnuts | 200 HP; also Lucile's Liked gift | Quay vendor | P22 vendor, CH-03 | 2 |

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
| 050 | Ruggieri Rocket | FIRE 900, all enemies | Corbel CH-12 | 300 |
| 051 | Bellows Charge | WIND 900, all enemies | Weiss CH-11 (CCR) · Corbel CH-12 | 300 |
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

CANON §11c fixes the families: 12 Period Scores (OPS-01–12) sold at Maison Farrenc and Schlesinger's; 12 Future Scores ✦ (OPS-13–24) transcribed by Min-jun at a Lectern, mapped to REP-17, REP-35…REP-45; 8 secret Scores (OPS-25–32) from bosses and quests. Each Score is unique (bought once). `skills_and_progression` owns every OPS's skills, rates, bonus shape and Invocation; **skills_and_progression.md does not exist yet**, so the Period and secret titles below are this doc's proposals (all works public domain and published before 1834). Prices and sources are binding here. "Tier" is the highest Harmony tier a Score may teach under the formulas_and_curves §8.4 gates (T2 from CH-05, T3 first obtainable CH-10, T4 CH-14).

| OPS | Score (proposed title) | Tier | Source | Price |
|---|---|---|---|---|
| OPS-01 | Gluck, *Orphée et Eurydice* (1774) | T2 | Maison Farrenc CH-05 | 900 |
| OPS-02 | Mozart, *Don Giovanni* (1787) | T2 | Maison Farrenc CH-05 | 900 |
| OPS-03 | Haydn, *The Creation* (1798) | T2 | Maison Farrenc CH-06 | 1,200 |
| OPS-04 | Beethoven, Symphony No. 5 (1808) | T2 | Schlesinger's CH-06 | 1,200 |
| OPS-05 | Weber, *Der Freischütz* (1821) | T2 | Schlesinger's CH-07 | 1,500 |
| OPS-06 | Rameau, *Les Indes galantes* (1735) | T2 | Maison Farrenc CH-08 | 2,000 |
| OPS-07 | Beethoven, Symphony No. 9 (1824) | T3 | Story CH-10: Aristide Farrenc posts it to the Auberge du Lion d'Argent, La Châtre (the first T3 Score) | — |
| OPS-08 | Rossini, *Guillaume Tell* (1829) | T3 | Schlesinger's CH-12 | 3,600 |
| OPS-09 | Bellini, *Norma* (1831) | T3 | Schlesinger's CH-12 | 3,600 |
| OPS-10 | Meyerbeer, *Robert le diable* (1831) | T3 | Story CH-13: Meyerbeer's (NPC-34) compliment after the gala, a bound copy | — |
| OPS-11 | Handel, *Messiah* (1742) | T4 | Maison Farrenc CH-14 | 7,200 |
| OPS-12 | Beethoven, *Missa solemnis* (1823) | T4 | Schlesinger's CH-14 | 7,200 |
| OPS-13–24 ✦ | Future Scores (REP-17, REP-35–45, CANON §15d) | per gate | Transcription at a Lectern after each CANON §15d trigger: OPS-14 CH-05, OPS-16 CH-06, OPS-17 CH-07, OPS-15 and OPS-23 CH-08, OPS-18 CH-10, OPS-19 CH-11, OPS-13 and OPS-20 CH-12, OPS-22 CH-13, OPS-21 CH-14, OPS-24 CH-15 | — |
| OPS-25 | Kang Min-jun, *Concerto "Lost Era"*: the cadenza (secret) | T3 | CH-13, Own Voice ≥ 6 (CANON §11g) | — |
| OPS-26 | Paganini, *24 Caprices* (pub. 1820) | T4 | BOSS-36 Paganini's Shadow (CH-14) | — |
| OPS-27 | Schubert, *Winterreise* (1828) | T3 | BOSS-37 The Lorelei Echo (CH-11 or CH-14) | — |
| OPS-28 | Rousseau, *Le Devin du village* (1752) | T4 | BOSS-40 The Philosophers' Echo (CH-14) | — |
| OPS-29 | Beethoven, *Wellington's Victory* (1813) | T4 | BOSS-38 The Forge Colossus (CH-14 or CH-E2) | — |
| OPS-30 | Haydn, *The Seasons* (1801) | T4 | BOSS-39 The Needle Echo (CH-14, BQ-PC02b) | — |
| OPS-31 | Bach, *The Art of Fugue* (1751) | T5 | BOSS-31 Ossia (CH-E1) or BOSS-34 The Unwritten (CH-E2), beside Delorme's notebook page (LAW-27) | — |
| OPS-32 | *Harmonies de l'ère perdue*, complete (REP-28) | T5 | BOSS-43 Da Capo: The Unstruck Bell (NG+) | — |

*Why these secret titles:* each answers its boss: a virtuoso's caprices for Paganini's Echo, a winter journey for the Rhine's grief, Rousseau's own opera for the philosopher who wrote it, Maelzel-era mechanical bombast for Archon's war engine, the year turning for the Needle's cycling Light, an unfinished fugue for the history that didn't happen. The ✦ trigger chapters copy CANON §15d.

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
