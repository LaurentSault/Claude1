# Overworld, Districts & Towns

Status: v1.0 — 2026-10-06 · Owns: overworld structure, every district/town/interior layout, named townsfolk, shop placement, secrets, chapter-state changes · Depends on: secrecy_and_trust (tier implementations, restricted zones, Close Call doors, Spotlight, Evening haunts), formulas_and_curves (§5.7, §12.1 encounter numbers), art_and_ui (walk speed, tilesets), dialogue_style_guide (notation, flags, length targets), historical_cast (NPC scenes), combat_ensemble (Snowfall, CH-15 switching); items_and_equipment (item names and prices), bestiary, dungeons, side_and_bond_quests (not yet published) · Canon: docs/00_CANON.md

## Table of Contents

1. [Scope, Conventions and Local IDs](#1-scope-conventions-and-local-ids)
2. [World Structure](#2-world-structure)
   - 2.1 Map roster · 2.2 Paris Overworld (LOC-W01) · 2.3 Transport progression · 2.4 France and Rhine Overworld (LOC-W02) · 2.5 Seoul Overworld (LOC-W03)
3. [World-Map Encounter Zones](#3-world-map-encounter-zones)
4. [World Rules](#4-world-rules)
   - 4.1 Lecterns · 4.2 Light, night and weather · 4.3 Secrecy on the map · 4.4 World states
5. [Paris 1833: Districts and Interiors](#5-paris-1833-districts-and-interiors)
6. [Paris 1833: Dungeon Hooks](#6-paris-1833-dungeon-hooks)
7. [Regional 1833](#7-regional-1833)
8. [Seoul 2026](#8-seoul-2026)
9. [Paris 1834 (CH-E2)](#9-paris-1834-ch-e2)
10. [Canon Additions & Cross-Doc Notes](#canon-additions--cross-doc-notes)

---

## 1. Scope, Conventions and Local IDs

**What this doc owns.** The overworlds (LOC-W01–W03); every town (T), interior (I) and event stage (E) of CANON §12, including the town or event halves of mixed LOCs (P03, P04, P10, P12, P25, S10, E01); named townsfolk; shop, inn and Lectern placement; hidden items in towns; map secrets; chapter-state changes. Dungeon (D) and mini-dungeon (mD) interiors are `dungeons.md`'s; this doc gives only their **hooks** (§6–§9): host map, door, and what the town around them does.

**What it cites.** Every LOC, CH, KEY, LM, BOSS, NPC, FIC, ANA, GST and PC ID is canon (CANON §0c). Shop *names* and inn names are binding from CANON §12; shop *inventories* and every item price, gifts included, belong to `items_and_equipment.md`; fares and fees sit inside the CANON §11h and §14 bands. Values owned by published docs are used as they stand there: encounter numbers (formulas_and_curves §12.1), walk speed (art_and_ui), Secrecy and Spotlight implementations, restricted zones and Close Call doors (secrecy_and_trust §2), text notation (dialogue_style_guide).

**Grid.** All field maps use 16 × 16 tiles; one screen is 16 × 14 tiles (256 × 224). Map sizes below are in tiles (W × H). Walking speed is art_and_ui's: 1 px per frame (16 frames per tile, 225 tiles a minute) on all maps; dash (hold B) 2 px per frame on town and interior maps only; *La Lumière* flies at 4 px per frame.

**Doc-local IDs (not canon families; usable as flag names).**

| Prefix | Meaning | Range used |
|---|---|---|
| TF-### | Named townsfolk (fictional, non-party, non-canon). Portrait tier C (`[N:]` name tab) | TF-001–TF-088 |
| WS-## | World state (a chapter-state change applied to one or more maps); engine flag `g_ws01`–`g_ws21` (dialogue_style_guide §2.3 scope prefix `g_`) | WS-01–WS-21 |
| WP-xx | Watcher post on a district map (A = Murmured+, B/C = Watched+) | per map |
| OM-A/B/C | Omnibus line | 3 lines |
| BG-# | Barge landing of *La Mouette* | BG-1–BG-7 |
| MR-# | Dirigible mooring (W01) | MR-1, MR-2 |

**Dialogue samples.** Every sample is one text box written in dialogue_style_guide §1.2 and §2.2 notation: `SPEAKER [P:ID:expr] text` for a portrait (the capitalised label is for writers and QA only) or `[N:Name] text` for Tier C; the box-final `[W]` is implicit and never written; the ellipsis is one glyph (…). Length targets are the guide's §8.3: portrait boxes ≤ 60 characters (cap 72, 3 × 24), no-portrait boxes ≤ 96 (cap 120, 4 × 30). Tier B portraits (CANON §16h) use neutral, smile, grave plus the one bespoke expression dialogue_style_guide §3.4 assigns. German lines carry `[in German]` and Lucile's Seoul exchanges with Min-jun carry `[in French]` (CANON §16c), first after the portrait. Lines are listed under the **chapter state** in which the NPC says them; "CH-05+" means "from CH-05 until a later state replaces it". Flags follow dialogue_style_guide §2.3 (`g_` for this doc's world states and debts).

**Hidden items.** Named only from canon lists: the §14 anchor consumables, the §11f favourite gifts, the §10c relics, the §14 tier pattern ("[Tier] [Class]"), or francs. `items_and_equipment.md` assigns ITM numbers and stats. Every hidden item is a sparkle-less examine point (FF6 rule: walk up and press A), never a chest in a town.

---

## 2. World Structure

### 2.1 Map roster

| LOC | Map | Size (tiles) | Scale | Chapters | Movement | Music |
|---|---|---|---|---|---|---|
| LOC-W01 | Paris Overworld | 192 × 144 | 1 tile ≈ 40 m (street-block scale) | CH-02–CH-14; CH-E2 (winter state, WS-19) | Foot; omnibus, fiacre (CH-05); barge (CH-08); dirigible (CH-14) | LM-04 |
| LOC-W02 | France and Rhine Overworld | 256 × 192 | 1 tile ≈ 4 km (route-map scale) | CH-10–CH-11; CH-14; CH-E2 (Fontainebleau leg only) | Foot; diligence (CH-10); steamboat (CH-11, scripted); dirigible (CH-14) | LM-29 |
| LOC-W03 | Seoul Overworld (Dec 2026) | 160 × 128 | 1 tile ≈ 120 m | CH-E1 | Foot; subway; taxi | LM-24 |

All three are saveable anywhere (CANON §11h); CH-E1 saves go through the phone's Notes app.

### 2.2 Paris Overworld (LOC-W01)

**Layout (north up).** The Seine runs west to east through the middle; the Farmers-General toll wall is the map's frame; Montmartre sits outside it at the top, Bercy and Père-Lachaise outside it at the right.

```
                       [P24] MONTMARTRE  MR-1 (CH-14)        . [P33] PERE-LACHAISE
  ====== toll wall ======== Barriere des Martyrs ===========.    (beyond the wall)
   [P23][P39]              [P03 FBG-POISSONNIERE]            :
   Fbg Saint-Honore         P04 P12 P35  Cite Bergere        :
          [P10 GRAND BOULEVARDS]  P05 P09 P11 P18 P19 P27 . . :
   Madeleine o====o Italiens ====o Poissonniere ====o St-Martin ===o Bastille
               DIL (Messageries)   POST (Hotel des Postes)       [P07 MARAIS]
   Champs-       [P16 PALAIS-ROYAL]                               P08 P36 E04
   Elysees       [P13 LOUVRE]        Chatelet
 ~~~~~~~~~ SEINE ~~~~~[P22 QUAYS/PONT DES ARTS]~~[P32 CITE]~~[E05 St-Louis]~~~~~> [P31 BERCY]
   MR-2          P06  P21  P20                                   (beyond the wall)
   Champ-de-Mars [P14 FBG SAINT-GERMAIN]      [P02 LATIN QUARTER]  [P28 PANTHEON]
                  P15  P34  rue du Bac         P37   [P26 VAL-DE-GRACE]
  ====== toll wall ============================ Barriere d'Enfer (P01 south mouth) =====
```

**Nodes.** District hubs are entered by walking onto their footprint; single-interior "event doors" are entered from the overworld when the story opens them.

| Node | LOC / service | Opens | Reached by |
|---|---|---|---|
| Latin Quarter | P02 (T) | CH-01 (night arrival), W01 from CH-02 | foot; OM-B (CH-05) |
| Faubourg-Poissonnière | P03 (T) with P04, P12, P35 | CH-02 | foot; OM-A |
| Salon Lavergne | P05 (event door, rue de Provence) — becomes a P10 interior from CH-05 | CH-03 | foot |
| Théâtre-Italien | P09 (event door, place des Italiens) — exterior only from CH-12 (P10 night variant) | CH-03 (2 Apr only) | foot |
| Seine Quays | P22 (T) with P06, P20, P21 | CH-03 | foot; OM-B; BG-1/BG-2 |
| Marais | P07 (T) with P08, P36; E04 in CH-E2 — paving-stone dray blocks it before CH-04 (WS-03) | CH-04 | foot; OM-A, OM-C |
| Île de la Cité | P32 (T) with P25 — crossed (not entered) in CH-02 | CH-04 | foot; OM-C; BG-3 |
| Grand Boulevards | P10 (T) with P05, P09, P11, P18, P19, P27, two salons — the Act II hub | CH-05 | foot; OM-A; fiacre |
| Faubourg Saint-Germain | P14 (T) with P15, P34 — dress gate (below) | CH-05 | foot; fiacre |
| Louvre | P13 (D) — copyist's card gate (Lucile) | CH-06 | foot; BG-1 |
| Montmartre | P24 (T) | CH-06 | foot via Barrière des Martyrs; fiacre; MR-1 |
| Dispensary | P37 (I) via P02's south end | CH-07 | foot |
| Palais-Royal | P16 (T) with P17 | CH-08 | foot; OM-B; fiacre |
| Faubourg Saint-Honoré | P23 (I) CH-09; P39 (I) CH-14 — event doors | CH-09 | fiacre |
| Bercy | P31 (D) — outside the wall | CH-09 (scripted) | BG-7 only |
| Diligence yard (DIL) | Messageries royales, rue Notre-Dame-des-Victoires — gateway to W02 | CH-10 | foot; fiacre |
| Hôtel des Postes (POST) | event door, rue Jean-Jacques-Rousseau — Sand's Lyon mail-coach farewell, Lucile alone | CH-14 (Thu 12 Dec) | foot |
| Val-de-Grâce | P26 (D) | CH-12 | foot (night) |
| Panthéon | P28 (T) with P38, P29 | CH-12 | foot; OM-B; scripted rope drop from *La Lumière* (Night of Stars) |
| Père-Lachaise | P33 (T opt) — outside the wall | CH-14 | foot by the Barrière d'Aunay (Z7); fiacre |
| Champ-de-Mars | MR-2 (mooring only) | CH-14 | dirigible |

Night variants (CANON §11i) are marked in each entry's header (§5).

**Act I: the masked city (CH-02–CH-04).** Unopened districts render as unlabelled, desaturated silhouettes. Walking into one triggers a period obstacle, never an invisible wall:

| District | Blocker until it opens | Line (`[N:]` box) |
|---|---|---|
| P10 Grand Boulevards (CH-05) | Tortoni's doorman turns away the bottle-green frock coat and sneakers, and the stroll along the terrace is the only way onto the boulevard from Act I's side streets | `[N:Doorman] Tortoni's terrace is for gentlemen in boots, monsieur. Yours are from no century I know.` |
| P14 Faubourg Saint-Germain (CH-05) | The Suisse porters of the hôtels | `[N:Porter] Visitors on foot use the tradesmen's gate. You have no trade I can see.` |
| P07 Marais (CH-04) | A dray unloading paving stones across rue Saint-Antoine (WS-03) | `[N:Carter] Six hundred paving stones for the rue Saint-Antoine. Go round, or carry some.` |
| P24 Montmartre (CH-06) | The National Guard picket posted at the Barrière des Martyrs since the CH-01 shooting (CANON R-03); no battle (CANON §12) | `[N:Guardsman] Since that business in the quarries, nobody leaves by this barrier unsearched. Come back in summer.` |
| P16 Palais-Royal (CH-08) | Berlioz steers Min-jun away (party bark; on foot CH-03–CH-07 a gallery guard does it) | `[N:Gallery guard] The arcades are closed to men without a hat. And a purse.` |

**Act II: Paris opens (CH-05).** The chapter's first free-roam beat is the delivery of the midnight-blue tailcoat from Vane's tailor (CANON §5g). From that frame the doorman steps aside, P10 and P14 resolve into colour, the first fiacre stand (Boulevard des Italiens) runs its tutorial ride, and OM-A begins service. New nodes then light up by chapter: P13 and P24 (CH-06); P15, P18's shop and P37 (CH-07); P16 and the river (CH-08); P23, P31 and P34 (CH-09). Act II is the hub loop: between story beats the player returns to W01 and spends the chapter's Evenings (CANON §11i) at its nodes.

**Acts III–IV.** CH-10 locks W01 (WS-12): the party leaves from the Messageries yard and Paris is not loaded. **CH-11 interlude (Lucile):** P20, P22's Left Bank screen, P02 and P37 only; the W01 path between them is a short scripted walk. **CH-12, after the Sun 24 Nov return (WS-13):** P10 (the walkout by night, then day), P11 (one visit), P22 with P06, P20 and P21 (SQ-13 opens on the quays, CANON §4d), P03 with P04 and P12 (Offenbach at the Conservatoire gate, Sat 30 Nov), P07 with P36 (Alkan turns 20, Sat 30 Nov), P32, and P05, P14 with P15, and P19 for the chapter's one Evening, then P02 (night variant before the storming, with P37) and P28. P16, P24 and P33 stay closed until CH-14; P13 never reopens. CH-13 is a single gala day on P10 and P27 (0 Evenings). CH-14 opens everything (unlimited Evenings, *La Lumière* at MR-1, P33, P38, P39, P27 by night for BOSS-36) until the Panthéon crypt-door prompt (CANON §0c) closes W01 for CH-15–CH-17.

### 2.3 Transport progression

| Mode | Chapters | Where | Cost | Rules |
|---|---|---|---|---|
| On foot | CH-P onward | All maps | — | W01 random encounters (§3) |
| Omnibus | CH-05–CH-14, CH-E2 | 3 fixed lines; board at stop signs | 6 sous a ride (CANON §11h) | No encounters; stops skip districts not yet open. Liveries of the period's rival companies; routes are game routes |
| Fiacre | CH-05–CH-14, CH-E2 | One stand per open district hub | 2 F a ride (CANON §11h) | Fast travel menu of open districts and event doors; no encounters |
| Seine barge *La Mouette* | CH-08–CH-14 | 7 landings (BG) | 1 F a hop | Master Yvon Le Goff (TF-036); battles on deck use Fog (CANON §10c); laid up for winter in CH-E2 |
| Diligence | CH-10–CH-11, CH-14; CH-E2 (Paris–Fontainebleau only, SQ-23) | W02 stations | 40–120 F a leg (CANON §11h; table §2.4) | A paid leg skips walking and encounters; first ride of each road is scripted; passports KEY-20 at borders |
| Rhine steamboat *Concordia* | CH-11 | Cologne → Mainz | Scripted | Is LOC-R08 (dungeon) |
| Dirigible *La Lumière* | CH-14 (free flight); CH-E2 (one finale flight) | W01 and W02 | Free; daytime take-off inside Paris Secrecy +2 (CANON §11h) | Mode 7 flight at 4 × walking speed; no encounters aloft; lands only at MR-1, MR-2 on W01 and on any open plain tile on W02; "Wait for nightfall" at a mooring spends one Evening (unlimited in CH-14) and makes the take-off free |
| Subway | CH-E1 | 11 stations (§2.5) | ₩1,550 a ride (flavour; phone Wallet) | Phone Map menu; no encounters |
| Taxi | CH-E1 | Any W03 node | ₩4,800 flat (flavour) | Phone menu; no encounters. Drops at the nearest open street when a Headline closure blocks the node (§2.5) |

**Omnibus lines (CH-05+).** OM-A *Dames Blanches* (white): Madeleine – Italiens (P10) – Poissonnière (P03) – Porte Saint-Martin – Bastille (P07). OM-B *Favorites* (green): Palais-Royal (P16, from CH-08) – Pont Neuf (P22) – rue Saint-Jacques (P02) – Panthéon (P28, from CH-12). OM-C *Écossaises* (tartan trim): Châtelet (P32) – Hôtel de Ville – Place Royale (P07).

**Barge landings (CH-08+).** BG-1 Port Saint-Nicolas (Louvre, P13/P22 Right Bank) · BG-2 Quai des Grands-Augustins steps (P22 Left Bank, below P20) · BG-3 Quai Desaix (P32) · BG-4 Port de la Grève (Hôtel de Ville, for P07) · BG-5 Quai de l'École sewer outfall (serves P17; `dungeons.md` decides whether it is an entrance or a shortcut exit) · BG-6 Port Saint-Bernard (Halle aux vins, Left Bank east, for P28) · BG-7 Bercy (CH-09 scripted run, beyond the Barrière de la Rapée).

### 2.4 France and Rhine Overworld (LOC-W02)

```
                                                   [R07 DUSSELDORF]
   NORMANDY (CH-14)                               /        |
  [R11 Etretat]--[R12 Le Havre]        [R13 Aachen]        | road (Tue 19 Nov)
                        \                   |              |
                       (Rouen)              |        [R14 COLOGNE]==Rhine (Concordia)==.
                           \                |                                          ||
                            \          [R06 LIEGE]                              [R09 LORELEI]
                             \              |                                          ||
                              \        (Brussels)                                   (Mainz)
                               \            |                                           |
                                \    (Valenciennes)                                     |
                                 \        /                                             |
                                 [W01 PARIS]------(Chalons)------(Nancy)------[R10 STRASBOURG]=Kehl=> Baden
                                      |
                [R02 Orsenne]--[R01 FONTAINEBLEAU]
                                      |
                       (Orleans) -- (Vierzon) -- (Chateauroux)
                                                      |
                                            [R04 LA CHATRE]--[R03 NOHANT]
                                                      |
                                            [R05 VALLEE NOIRE]
```

Bracketed names are LOCs; parenthesised names are **relay posts**: non-enterable post-house sprites where the diligence changes horses (overworld saves allowed; no new LOC).

**Diligence legs (fares inside the CANON §11h band).**

| Leg | Fare | Opens | Scripted first ride |
|---|---|---|---|
| Paris – Fontainebleau | 40 F | CH-10 | Liszt's tour sets out (Corot, GST-03) |
| Fontainebleau – La Châtre (via Orléans, Vierzon, Châteauroux) | 90 F | CH-10 | Arrival at the Auberge du Lion d'Argent |
| La Châtre – Nohant | walk only (1.5 lieues) | CH-10 | — |
| Paris – Liège (via Valenciennes, Brussels) | 120 F | CH-11 | Chopin joins at Liège |
| Liège – Aachen | 40 F | CH-11 | Border, KEY-20 checked (R13) |
| Aachen – Düsseldorf | 60 F | CH-11 | — |
| Düsseldorf – Cologne | 40 F | CH-11 | Tue 19 Nov ride to the *Concordia* |
| Mainz – Strasbourg (fast diligence) | 100 F | CH-11 | Thu 21 Nov; Sand's letter waiting |
| Strasbourg – Paris (via Nancy, Châlons) | 120 F | CH-11 | Return, Sun 24 Nov |
| Paris – Le Havre (via Rouen) | 90 F | CH-14 | BQ-PC02b |
| Le Havre – Étretat | 40 F | CH-14 | BQ-PC02b |
| Fontainebleau – Château d'Orsenne | walk only | CH-14 | — |

**Opening by chapter.** CH-10: the south road only (Paris, R01, relays, R04, R03, R05). CH-11: the north and east roads and the Rhine (R06, R13, R07, R14, R08, R09, R10); the south road greys out. CH-14: everything, plus Normandy (R11, R12) and R02. Towns whose canon revisit is "—" (R04, R05, R06, R08, R13, R14) remain visible but cannot be entered after their chapter: no mooring field, a closed barrier or, for the *Concordia*, a hull steaming away. **Liszt and Nohant:** entering R03 while Sand is in residence (CH-10) moves Liszt to the Lion d'Argent in R04 (party bark: "A touring virtuoso calling on a notorious novelist would be in every paper"), enforcing the CANON §16e staging rule. In CH-14 Sand is gone. Liszt and Delacroix may enter, but Chopin never enters R03 in any chapter (CANON §16e: Chopin and Sand never share a scene or a location). If he is in the active party when *La Lumière* lands at R03, he moves to reserve with the bark `CHOPIN [P:PC-06:ironic] Country air and I quarrel. I'll mind the balloon.` and waits aboard; arriving on foot over W02, the same swap fires at the R03 node (`CHOPIN [P:PC-06:ironic] Country air and I quarrel. I'll wait at the post-house.`).

### 2.5 Seoul Overworld (LOC-W03)

```
  [S13 French Embassy]      [S12 INSADONG]      [S11 BOSINGAK]
     (Chungjeongno)            (Anguk)            (Jonggak)
            \                    |                  |
   [S03 JEONG-DONG: S01 S02 S05 S10] ---- [S08 Euljiro / Line 2] ---- [S15 Kang Piano Service]
        (City Hall)                        (Euljiro 3-ga)               (Euljiro 4-ga)
                                                   \
  [S07 HONGDAE]   [S14 YANGHWAJIN]               [S09 NAMSAN] (Myeongdong)
  (Hongik Univ.)    (Hapjeong)
  [S04 Kang apartment] (Mangwon)
  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ HAN RIVER ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
                                    [S06 HANGARAM / Seoul Arts Center] (Nambu Bus Terminal)
```

Eleven subway stations (parentheses) are the fast-travel nodes in the phone Map menu: Chungjeongno, Anguk, Jonggak, City Hall, Euljiro 3-ga, Euljiro 4-ga, Myeongdong, Hongik Univ., Hapjeong, Mangwon and Nambu Bus Terminal. S02, S05 and S10 are entered through S03 (the campus). **Spotlight Meter on the map** (CANON §11e; implementation secrecy_and_trust §2.10, verbatim): **Trending (25–49):** phone-camera crowds slow movement: walk speed −25% on Seoul town maps while Lucile is in the party. **Headline (50–74):** reporters block some streets: the east end of the Deoksugung Stonewall Road (S03), Insadong's main lane (S12) and Hongdae's busking street (S07) close; side alleys detour. **Viral (75–99):** Lucile cannot paint in public (field painting prompts greyed: "Not with a hundred phones watching."); Céline's lawyers' offer becomes available. **100:** forced press scrum (fail-forward): a scripted run through the nearest subway station, Jae-won running interference; Spotlight set to 50. This doc adds one placement: at Headline and above, busking spots 1–3 (S07) are unavailable until Spotlight falls below 50; the S03 detour runs down the Jeong-dong church lane and the S12 detour through the teahouse alley.

---

## 3. World-Map Encounter Zones

Families come only from CANON §12 and LAW-07; W01–W03 are "areas not listed", so the bestiary sets the final ENM rosters. Enemy level = the chapter's §10e anchor −2 to +0. **Never a battle against the National Guard, Prefecture or octroi agents, soldiers or Seoul civilians** (CANON §12); humans are routed, never killed.

**Rates.** The tiers below use formulas_and_curves §12.1's mean steps between battles (grace included): **Low 570 · Medium 443 · High 352**; Hunted ×1.25 (**488 / 380 / 301**, CANON §11e); the War overlay raises a zone one tier; the Winter overlay sets Low everywhere. Formations: 2 foes (40%), 3 (45%), 4 (15%). At Watched tier and above (CH-06+), 1 W01 battle in 8 is a cabal **Shadow** formation per secrecy_and_trust §2.8.2: Black Coats ×2 + a Watcher in CH-06–CH-08, Grey Hand ×3 from CH-09; on W02 in CH-10–CH-11, Hunter Automata ×2 (river automata on the Rhine legs). CH-14: no Shadow formations and no Hunted rise. **No encounters** on bridges, on the lit boulevard spine (P10's Madeleine–Saint-Martin axis by day), while riding any vehicle, in the dirigible, on W03, or on town and interior maps.

**W01 Paris.**

| Zone | Area | Opens | Day families | Night (palette) families | Rate |
|---|---|---|---|---|---|
| Z1 Left Bank streets | Latin Quarter, Montagne, Faubourg Saint-Jacques | CH-02 | quarry rats, Miasma Wraiths (near the old lime pits by the Carmel) | + Ossuary Echoes (CH-02–CH-04 only, strays from P01) | Medium |
| Z2 Right Bank faubourgs | Poissonnière, Saint-Denis, road to the Martyrs barrier | CH-02 | pickpocket gangs, rats | Gaslight Wisps (CH-05+) | Low |
| Z3 Islands and quays | Cité, Saint-Louis, river banks | CH-04 | Gargoyle Echoes (Cité only) | Gargoyle Echoes, Miasma Wraiths | Low |
| Z4 Marais | East of the Hôtel de Ville to the Bastille | CH-04 | pickpocket gangs; Black Coats (CH-04 only) | Tocsin Echoes (CH-05+, WS-05) | Medium |
| Z5 Boulevards | Madeleine–Bastille band, Chaussée-d'Antin | CH-05 | pickpocket gangs | Gaslight Wisps | Low |
| Z6 West faubourgs | Saint-Germain, Saint-Honoré, Champs-Élysées | CH-05 | pickpocket gangs | Grey Hand pickets (CH-09+) | Low |
| Z7 Beyond the wall | Montmartre slopes (gypsum quarries), Père-Lachaise road (from the Barrière d'Aunay) | CH-06 | quarry rats, Miasma Wraiths | Miasma Wraiths | Medium |
| War overlay | All zones | CH-14 | Grey Hand, Roussel's Cleaners | + stage-machinery automata strays | +1 tier (Low → Medium, Medium → High; High stays High) |
| Winter overlay | All zones | CH-E2 | Living Tableau squads, leftover automata | residual Echoes | Low everywhere |

**W02 France and Rhine.**

| Zone | Region | Opens | Families | Rate |
|---|---|---|---|---|
| Y1 Île-de-France plain | Paris – Fontainebleau; Paris – Valenciennes | CH-10 | Grey Hand road pickets (LAW-11), boar | Low |
| Y2 Forest | Fontainebleau, Orsenne woods | CH-10 | Hunter Automata, boar | Medium |
| Y3 Berry | Orléans – La Châtre – Nohant | CH-10 | Hunter Automata, boar | Medium |
| Y4 North road | Valenciennes – Brussels – Liège | CH-11 | frontier smugglers, Grey Hand road pickets | Medium |
| Y5 Rhineland | Aachen – Düsseldorf – Cologne | CH-11 | frontier smugglers, river automata | Medium |
| Y6 Middle Rhine gorge | Cologne – Mainz banks (on foot only from CH-14) | CH-14 | river automata, Lorelei Echoes | High |
| Y7 East road | Mainz – Strasbourg – Nancy – Paris | CH-11 | frontier smugglers | Low |
| Y8 Normandy | Rouen – Le Havre – Étretat | CH-14 | frontier smugglers (coastal), Hunter Automata strays | Medium |

**W03 Seoul.** No random encounters. From the night Brücke's hunt begins (CH-E1), **static pockets** appear: visible flickers of the reserved synth palette in alleys and on side screens (Euljiro back lanes, the Jongno side streets behind S11, the Namsan footpath approaches, and the edges of the S03, S07 and S12 town screens). Touching one starts a battle with static automata (CANON §12, S08 family; formulas_and_curves §12.1 sets one formation of three at the CH-E1 anchor). Pockets **may spawn on Seoul town screens**: any battle there shows **2 phone-camera Onlookers**, and Lucile's styles feed the Spotlight Meter with their Heat (secrecy_and_trust §2.10). Battles under falling snow use Snowfall (combat_ensemble). Pockets vanish permanently after BOSS-30 (the oscillator shatters, LAW-24). Ossia phantoms appear only inside S09.

---

## 4. World Rules

### 4.1 Lecterns (save points)

Lecterns are glowing music stands visible only to rift-touched eyes (CANON §11h). NPCs walk through them; Lucile, when in the party, never sees one (field bark on first save after she joins: `LUCILE [P:PC-02:surprised] You stare at that corner like a cat at a ghost.`).

**Placement rules (binding for this doc's maps).**

1. Each district hub (T) has at least one Lectern, within 12 tiles of its fiacre stand or arrival point.
2. Each home interior has one: Min-jun's room at P04, Lucile's attic P20 (CH-05+), the Atelier E02 (CH-E2).
3. A Lectern stands within 8 tiles outside every mini-dungeon or dungeon door on a town map (interior Lecterns are `dungeons.md`'s).
4. An interior that hosts a scripted boss, duel or concert has one in its antechamber: P05, P12, P15, P35, P39.
5. Never on a map during a chase, a stealth sequence, a three-front battle, or CH-17 free movement (the Window Clock). CH-15–CH-16 Lecterns are `dungeons.md`'s and must exist: party switching in CH-15 happens only at Lecterns and plinths (combat_ensemble), Window Talk 4 is staged at the Heart-gate Lectern (secrecy_and_trust §5.5.1), and the Eve of the Window save is made at the last Lectern before BOSS-26 (CANON §11h, LAW-23.6).
6. Regional towns and fields have one each (R11 at the fishermen's capstans; R01 at the Apremont rocks).
7. **CH-E2:** every Lectern persists, amber and dimmer; after each major story beat one goes dark (keeping its save function) in this order: P28 (after the 22 Dec concert) → P02 (after Delorme's first theft is discovered and the Canvas Ledger opens) → P32 (after the proposal, Sun 9 Feb) → P22 (after the portrait sitting) → P10 (after the jury, Sat 15 Feb) → E02 (as the *Harmonies* finale ends, Sat 1 Mar).
8. **CH-E1:** no Lecterns. Phone Notes saves anywhere outside dungeons; metronomes serve in S08 (a busker's, abandoned) and S10 (the practice rooms'). **CH-P:** the first Lectern flickers into being at the foot of the S02 stair while the Door is ringing.

**Town Lectern list** (rule 1 hub Lecterns first, then rule 3 door Lecterns).

| Map | Lecterns |
|---|---|
| P02 | Saint-Séverin porch (also within 8 tiles of the Lys d'Or yard well, CH-04) · Val-de-Grâce gate lodge (P26 gate, the CH-06 laundry-wall stair, P37's door) |
| P03 | Conservatoire railings (also serves the undercroft trapdoor) |
| P04 | Room 3 (home) |
| P05 | cloakroom |
| P07 | Place Royale arcade · rue Saint-Antoine fountain (P08's door; CH-04 only; from WS-05 the spot holds the candle shrine) |
| P10 | Centre: the elm bench before the Café Hardy (also serves the Passage de l'Opéra mouth) · Centre: rue Le Peletier stage door (P27; dark on gala day, WS-14, when the party arrives by scripted carriage and the first save is inside P27) · West: rue de la Paix corner (P18) |
| P12 | showroom vestibule |
| P14 | rue du Bac fountain · rue de Varenne gate (P34) |
| P15 | embassy anteroom |
| P16 | Galerie d'Orléans · Trois Dièses cloakroom (P17 cellar door) |
| P20 | attic (CH-05+) |
| P22 | Left Bank: Pont des Arts steps · Right Bank: quai du Louvre door (P13, CH-06) |
| P24 | Auberge des Trois Moulins yard |
| P28 | Panthéon steps (also serves the crypt door: P38, E03, P29) |
| P32 | Notre-Dame parvis · rue de Jérusalem (P25 cell stair) |
| P33 | gate |
| P35 | green room |
| P39 | anteroom |
| Regional | R01 (Apremont rocks), R03 (garden gate), R04 (inn hall; Indre bridge for R05), R06, R07, R10, R11, R12, R14 (quay office, by the *Concordia*'s gangway) |
| CH-E2 | E02, plus every Paris Lectern above (rule 7) |

### 4.2 Light, night and weather

**Time.** There is no clock; time moves by story beat and by spending Evenings (CANON §11i). **Day** scenes use Noon outdoors; scripted mornings use Dawn; an Evening shifts the map to Dusk, then Night.

**Night.** Only seven maps have an authored second (night) state: **P02, P04, P10, P16, P22, P24, P28** (CANON §11i). Every other town and interior is visited only in its one authored state. A map's *one* state may itself be night or dusk: R05, S07 and S11 are night-only; S03 is winter dusk, with a Night palette shift (no new map) for the 31 Dec beats. The three overworlds use a **palette shift** for Dusk and Night (no authored night maps), which is how the dirigible flies by night. Interiors are Candle-lit in every state.

**Weather overlays** (sprite and palette layers on the map's existing state; never a new map). Rain, fog, river mist and falling snow flag a map as *precipitation*, so outdoor battles there use **Fog** (CANON §10c); settled snow without falling flakes keeps the time-of-day Light.

**By chapter:** CH-01 downpour (P02, night) · CH-02 drizzle on 3 visits in 5 (W01, P02, P03) · CH-03 one shower on P22 · CH-04 smoke haze over P07 on 5 Jun · CH-05 dawn mist on P22 (the lesson) · CH-06 heat shimmer, river mist at the Pont Royal · CH-08 storm on the night of Sat 21 Sep (P10, P12) · CH-09 dawn mist on the Pont des Arts (the confession) · CH-10 ground fog in R05 · CH-11 rain at R13, spray on R08 and R09 · CH-12 fog (W01, P02) · CH-14 frost by day, clear star nights (P24, P28) · CH-E2 snow on the roofs, falling snow on 1 visit in 3 · CH-E1 falling snow on W03, S03, S09, S11 and S14 (W03 pocket battles and S09 use combat_ensemble's Snowfall).

### 4.3 Secrecy on the map

Tier effects come from CANON §11e and their implementations from secrecy_and_trust §2.2 and §2.4.4; this doc places them. Watchers start in CH-06 and are absent in CH-14. **Watcher posts** (WP-A appears at Murmured, WP-B and WP-C at Watched) and each map's **restricted zone** (secrecy_and_trust §2.4.4's list; a Watcher sighting there costs Secrecy +3 once per map entry; the tiles are red-tinted at Murmured+):

| Map | WP-A | WP-B | WP-C | Restricted zone |
|---|---|---|---|---|
| P02 | Saint-Séverin porch | Sorbonne steps | Val-de-Grâce gate | Carmel quarry hatch, south end |
| P03 | Conservatoire railings | rue Cadet corner | Cité Bergère arch | — |
| P07 | Place Royale arcade | rue Saint-Antoine fountain | Pavillon du Roi passage | — |
| P10 | Tortoni terrace | Passage de l'Opéra mouth | rue de la Paix corner | Horlogerie Brücke rear court (P18), West screen |
| P14 | rue de Varenne gate | rue Saint-Dominique | rue du Bac fountain | Hôtel de Vane gate, rue de Varenne |
| P16 | Galerie d'Orléans | Café des Trois Dièses door | garden fountain | Café des Trois Dièses cellar door |
| P22 | Pont des Arts toll booth | Institut steps | Henri IV statue (Pont Neuf) | — |
| P24 | Saint-Pierre tower | Windmill lane | Barrière des Martyrs | gypsum-quarry mouths, north slope |
| P28 | Panthéon steps | Saint-Étienne porch | Polytechnique gate | scaffold yard |
| P32 | Notre-Dame parvis | Quai Desaix | rue de Jérusalem | Prefecture courtyard (P25) |

**Hunted (60–79).** Prefecture papers checks on the **Pont Neuf, Pont au Change, Pont Saint-Michel and Pont Royal** (drawn on P22, P32 and P02); without KEY-11 the guard turns the party back (cross elsewhere, take the barge or a fiacre). The Pont des Arts asks its sou toll and no papers. **Inn ambushes:** an inn night in Paris (paid, or Room 3 at P04) rolls an ambush at **33%** (50% at Compromised); at *Au Diapason Fêlé* **25%** at Hunted, made a preemptive battle by Petit-Louis's warning (secrecy_and_trust §2.2 governs its Compromised value). Ambush rosters by chapter are secrecy_and_trust §2.8.2's (Julien's café toughs, Black Coats, Grey Hand; Hunter Automata at regional inns in CH-10–CH-11). Encounter rate ×1.25 on W01 (§3). **Compromised (80–99):** Vidal & Fils (P14) refuses service; Curiosités Corbel's high-tier relic counter refuses ("*Monsieur is not received.*"); lower-tier shops elsewhere always sell. Close Calls end at the safe doors marked in §5 (P04, P06, P19 from CH-05, P36 from CH-04, P11 from CH-06, P39 in CH-14). **CH-14:** no Watchers, no ambushes, no encounter-rate rise (papers checks and shop refusals remain). **Unmasked:** P25 cells (CH-02–CH-08, CH-14) or the Bercy safe house (CH-09–CH-13).

**Services that lower Secrecy.** Press rebuttal (−10, 500 F, once per chapter): Heine at his Tortoni table (P10) or the Maison Farrenc counter (P19), available from CH-05 (Lucien carries the copy to the printer until Aristide is at the counter in CH-08). Inn night (−1): any inn. SQ-04's counter-ink press (`side_and_bond_quests.md`) may use the Galerie d'Orléans bookseller (P16).

### 4.4 World states

| WS | Trigger (engine flag `g_wsNN`) | Maps | What changes |
|---|---|---|---|
| WS-01 | CH-01 arrival | P02 | Night + downpour; shuttered shops; Mathurin's farewell |
| WS-02 | CH-02 start | W01, P02–P04 | The masked city; 2 Evenings |
| WS-03 | CH-02–CH-03 | W01, P07 | Paving-stone dray blocks rue Saint-Antoine; gone in CH-04 (the stones become the barricade) |
| WS-04 | CH-03 caricature (rung 3) | P04, P03, P16 (CH-08) | *Le Corsaire*'s "Mandarin Mimic" pinned behind the tavern bar; Nanette keeps a copy |
| WS-05 | Riot done (CH-04 end) | P07, W01 Z4 | Re-laid stones, chipped Pavillon du Roi, a candle shrine at the rue Saint-Antoine fountain, Tocsin Echoes at night; a ballad-seller in CH-07 |
| WS-06 | Tailcoat delivered (CH-05) | W01, P10, P14 | Paris opens (§2.2) |
| WS-07 | Sun 28 Jul (CH-06) | P10 west screen | Crowds at Place Vendôme for the statue; rue de la Paix impassable for one beat |
| WS-08 | Mon 5 Aug (CH-06), after the Fri 2 Aug studio showing and Sand's visit to the attic (Sat 3 Aug); on Sand's word Corbel puts it in his window (historical_cast) | P21 | *Le Pont Royal, effet de brume* in Corbel's window; a crowd outside (an Anachronic showing, LAW-21); Ingres passes on Tue 6 Aug |
| WS-09 | CH-07 | P12, P37 | Théo at Pleyel's and the dispensary; SQ-07 worry icon on the W01 map until SQ-07 completes |
| WS-10 | Sat 21 Sep (CH-08) | P12, P10 | Charity-concert posters; storm |
| WS-11 | Dawn, 4 Oct (CH-09): the chapter's last free beat, a walk from the Pont des Arts to the attic | P20, P21, P22 | Attic dark, easel gone; Corbel's shutters half down; Couleurs Ravenel asks after her |
| WS-12 | CH-10–CH-11 | W01 | Paris locked; in CH-11 only the interlude maps load (P20, P22 Left Bank, P02, P37; §2.2) |
| WS-13 | Sun 24 Nov (CH-12) | P10 night, P02 night | Théâtre-Italien walkout outside; fog |
| WS-14 | CH-13 | P10 | Gala posters, carriages, Tortoni empty |
| WS-15 | CH-14 | all W01 | Open war overlay; *La Lumière* moored at MR-1; Belgiojoso's door opens |
| WS-16 | SQ-12 bought (CH-14) | P24 | The Montmartre studio's door gains a brass plate; becomes E02 in CH-E2 |
| WS-17 | Vane defects (CH-14) | P14 | Hôtel de Vane shuttered, servants dismissed; Tissot gone with his master |
| WS-18 | Crypt-door prompt accepted | W01 | Closed for CH-15–CH-17 |
| WS-19 | CH-E2 | W01, all Paris maps | Winter Paris (§9.1) |
| WS-20 | CH-E1 | W03, Seoul maps | Snow; static pockets; Spotlight effects |
| WS-21 | CH-06, after Lucile's report (rung 6) | P02 | The Val-de-Grâce laundry-wall stair found flooded: standing water to the third step, a chalk J on the lintel; grilled from the next map load (§6) |

---

## 5. Paris 1833: Districts and Interiors

Entry format: header line (type · LM · size · night variant), **Open** (canon story visits, then this doc's optional windows), mood and layout, **Services**, **Townsfolk** (lines by chapter state), **Secrets**, **States**.

**Hub rule (binding for every Open line).** Once a district hub (T), a shop or a home interior has opened, it stays enterable for the rest of Act II (until the CH-09 abduction night), in CH-14 and in CH-E2, unless its entry limits it. Event interiors (P05, P09, P11, P15, P23, P35, P39) open only in the windows their entries list. In CH-10–CH-13 only the maps named in §2.2 load.

### LOC-P02 Latin Quarter: rue Saint-Jacques — T · LM-04 (CH-01 rain: LM-18 cue) · 72 × 40 · night variant

**Open:** CH-01 (night), CH-02–CH-09, CH-11 interlude (Lucile), CH-12 (night), CH-14, CH-E2. **Mood:** students, ragpickers and wax ex-votos for the cholera dead; the street climbs south from the river like a spine.

```
 N  Pont Saint-Michel (checkpoint) . place Saint-Michel -- rue de la Harpe [Maison Grimaud] [juge de paix, CH-14]
    Petit-Pont (river) -- rue Saint-Jacques
    | Saint-Severin [LECTERN] [Pharmacie Laborde] [Hotel du Lys d'Or: yard well, CH-04]
    | Sorbonne . College de France . Louis-le-Grand        -> east: P28
    | rue Saint-Jacques (one long screen, 3 crossings)
    | [P37 Dispensary] [Val-de-Grace gate lodge: LECTERN] [gate -> P26] [laundry-wall stair, CH-06] [fountain*]
 S  Carmel wall: quarry hatch (P01 exit, grilled; restricted)   fiacre stand at Saint-Severin
```
*\*Rambuteau's fountain, from CH-05, only under `byt_boil_water` (historical_cast).*

**Services:** Hôtel du Lys d'Or (inn; tier price, CANON §14) · Pharmacie Laborde, first branch (consumables) · Maison Grimaud, rue de la Harpe (colour merchant; locked while Lucile is in the party until flag `g_aubray_debt_cleared`, Canon Additions) · Lectern ×2 (§4.1) · fiacre (CH-05+) · OM-B. **The justice of the peace's chambers, rue de la Harpe** (sub-interior, CH-14 only): the family-council room of SQ-07 step 5 (LAW-23.1); the council sits behind the door while Min-jun, Lucile and Louise Farrenc wait on the corridor bench, the one place on the map where the law is drawn as a closed door.

| ID | Who | Lines |
|---|---|---|
| FIC-09 | Mathurin Lebœuf | CH-01: `MATHURIN [P:FIC-09:grave] Up you go. Rue Saint-Jacques. Forget my face and the cellar.` |
| TF-001 | Mme Clotilde Varin, keeper of the Lys d'Or | CH-02: `[N:Mme Varin] Ten francs a night, monsieur, and I don't take buttons, however foreign.` · CH-05+: `[N:Mme Varin] The Inspection capped my well. Now I pay the water-carrier like a lodger.` · CH-12+: `[N:Mme Varin] The Corean from the papers! I turned you away in March. Now it's sixty francs.` |
| TF-002 | Basile Laborde, pharmacist | CH-02: `[N:M. Laborde] Four Thieves vinegar? Since last spring I sell more of it than bread.` · CH-07+ `[IF:byt_boil_water]`: `[N:M. Laborde] The prefect's fountain! I sell less vinegar. I find I don't mind.` |
| TF-003 | Mère Ursule, candle-seller at Saint-Séverin | CH-02: `[N:Mère Ursule] A candle for someone, monsieur? Everyone on this street has someone.` · CH-05+ with Lucile: `LUCILE [P:PC-02:sad] Papa's candle. April. I'll light it myself.` |
| TF-004 | Jules Morin, medical student | CH-02: `[N:Jules] Anatomy at eight, chemistry at ten, and I still can't afford a candle.` · CH-12 night: `[N:Jules] The surgeons at Val-de-Grâce say the old abbey wing hums at night.` |
| TF-005 | Isidore Grimaud, colour merchant | CH-05+ until `g_aubray_debt_cleared`: `[N:M. Grimaud] Her father's account was sold, monsieur. I sell colours. I don't judge.` |
| TF-088 | Clerk of the justice of the peace | CH-14 (SQ-07 step 5): `[N:Clerk] The council is of men, monsieur. The ladies and the foreigner will wait here.` |

**Secrets:** a Sal Volatile wedged behind the Saint-Séverin poor box (CH-02); 120 F in a student's lost purse under the Sorbonne steps (CH-05+, returned to Jules for a Café Noir ×3 instead if the player chooses); the Carmel wall shows the old Frères' clef mark (Almanach "Les Sept Pierres", CH-12+, Perfect Pitch reveals it).
**States:** WS-01 rain-night (only the inn and the pharmacy's night bell answer); CH-02 drizzle; CH-04 the Lys d'Or yard well open (the Rust gallery, §6), capped from CH-05; CH-06 the laundry-wall stair flooded (WS-21), grilled thereafter; CH-12 fog-night (Watchers replaced by two Grey Hand pickets at the Val-de-Grâce gate); CH-E2 snow, ex-votos replaced by New Year greenery.

### LOC-P03 Faubourg-Poissonnière and the Conservatoire — T / mD · LM-04 · 64 × 48

**Open:** CH-02–CH-09, CH-12–CH-14, CH-E2. Undercroft mD: CH-03 (§6). **Mood:** scales pouring from every window, Cherubini's frown at the railings.

```
 rue Bergere: [CONSERVATOIRE + P35 hall] [LECTERN railings]  [Armurerie Vidal]
 Cite Bergere (arch, no. 4)                 rue Cadet: [P12 PLEYEL, no. 9]
 rue du Faubourg-Poissonniere: [P04 AU DIAPASON FELE] ... fiacre stand (CH-05+)
```

**Services:** Armurerie Vidal (weapons, armour) · Lectern · fiacre · OM-A.

| ID | Who | Lines |
|---|---|---|
| NPC-17 | Luigi Cherubini | CH-05+: `CHERUBINI [P:NPC-17:grave] You again. They say you play. Play quietly.` |
| TF-006 | Joseph Vidal, armourer | CH-02: `[N:Joseph Vidal] Batons for pupils, canes for students, and credit for nobody.` · CH-05+: `[N:Joseph Vidal] My father's shop in the Faubourg sells this steel at thrice the price.` |
| TF-007 | Père Lhomme, Conservatoire porter | CH-02: `[N:Père Lhomme] No entry without the director's leave. And he never gives leave.` · CH-04: `[N:Père Lhomme] The Mandarin Mimic? Don't scowl at me, monsieur, I didn't draw it.` |
| FIC-26 | Hippolyte Vasseur | CH-02: `[N:Hippolyte] Failed the violin concours again. My bow arm, they say, is a pump handle.` |
| TF-008 | Mlle Rosalie Bertin, singer at a window | CH-03: `[N:Rosalie] Do, ré, mi… You there! Was I flat? Don't lie. Foreigners can't.` |

**Secrets:** **Cité Bergère, no. 4 (CH-02–CH-04):** a pale young man practises behind a first-floor window (Op. 10, published that summer); examining the window gives the Almanach entry "Cité Bergère" and Min-jun hums along (`MIN-JUN [P:PC-01:homesick] …No. Not yet. He doesn't know me.`). From CH-05 the window shows "À louer". A Pitch Pipe in the Conservatoire gutter (CH-02); a cake of Prussian blue dropped by a copyist at the rue Cadet corner (CH-05+, Lucile's favourite gift).
**States:** CH-03 caricature on the Conservatoire notice board (WS-04); CH-12 Offenbach seen queuing at the gate (cameo, Sat 30 Nov); CH-E2 the P35 hall's posters for Sun 22 Dec.

### LOC-P04 *Au Diapason Fêlé* — I / mD · LM-02 · 24 × 18 (ground floor), 12 × 10 (Room 3) · night variant

**Open:** CH-02 (home), CH-04 (Lucile's first sketch, Thu 9 May), CH-14, CH-E2, and as an inn whenever P03 is open. **Close Call safe door** in every chapter that can have one (secrecy_and_trust §2.9.1). Cellars mD: CH-02 (§6; the Cartouche Glove is found there, CANON §11a). **Mood:** smoke, soup, a pianino with three dead keys.

```
 [door]  tables . tables . hearth      [PIANINO, 3 dead keys]  <- T1 salon spot
 [bar: Mere Gaudin; cracked fork above]  [stair up -> Room 3: bed, LECTERN, window on the street]
 [trapdoor -> cellars (mD)]            [back door -> yard, Petit-Louis's crate]
```

**Services:** Inn: Room 3 rest is free to Min-jun's party (his lodging, KEY-06; in CH-02 Mère Gaudin takes a tune for the soup); any party without Min-jun pays the tier price · T1 salon (Mère Gaudin, CANON §11g) · Lectern in Room 3 · KEY-06 room key. **Sign:** Étienne Gaudin's cracked tuning fork, hung over the bar (historical_cast: her late husband, a piano tuner, d. Apr 1832).

| ID | Who | Lines |
|---|---|---|
| FIC-02 | Mère Gaudin | CH-02: `GAUDIN [P:FIC-02:smile] Soup for a tune. Three keys are dead, mind. Play round them.` · CH-09: `GAUDIN [P:FIC-02:grave] Whatever you're in, my door's barred to grey coats.` · CH-14: `GAUDIN [P:FIC-02:neutral] Gros-Louis is in the back. Says he owes you a kindness.` · CH-E2 (after 9 Feb): `GAUDIN [P:FIC-02:smile] Engaged men pay half for soup. Married men, full.` |
| FIC-03 | Petit-Louis | CH-02: `PETIT-LOUIS [P:FIC-03:smile] Message run? Two sous. Love letters, five.` · CH-14: `PETIT-LOUIS [P:FIC-03:neutral] I know every grey glove on this street by his walk.` |
| FIC-24 | Auguste Pichon, "le Sergent" | CH-02: `[N:Le Sergent] Left this leg at the Moskva, lad. The rest of me still sings.` · CH-05+: `[N:Le Sergent] A barricade! In my day we carried muskets, not pamphlets.` |
| FIC-25 | Nanette | CH-02: `[N:Nanette] Found a button, a spoon, a sou and a love letter. Only the sou's useful.` · CH-03+: `[N:Nanette] Found a newspaper with your face on it. Drawn wrong. I kept it.` |
| FIC-26 | Hippolyte Vasseur | CH-03+ (evenings): `[N:Hippolyte] Play the moonlight one again. I'll pretend I'm passing exams.` |
| FIC-18 | Gros-Louis Bréhat | CH-14: `GROS-LOUIS [P:FIC-18:neutral] Grey gloves are carting Bercy barrels up to the Panthéon.` |

**Secrets:** a Tisane ×2 in the hearth niche (CH-02); a Café Noir ×2 under the bar's loose board (CH-04); the dead keys are fixed in CH-E2 (Théo's work: one examine line).
**States:** night variant = the T1 salon evening (regulars at tables, Candle); WS-04 caricature behind the bar (CH-03–CH-05, then taken down: `[N:Nanette] Mère Gaudin used it to light the stove.`); CH-E2 holly over the door.

### LOC-P05 Salon Lavergne — I · LM-19 · 28 × 20

**Open:** CH-03 (Herz contest BOSS-03, "Ondine", Sat 27 Apr), CH-05; optional T2 salons CH-03–CH-09, CH-12–CH-14 (one Evening each) and CH-E2. Event door on W01 until CH-05, then a P10 interior (rue de Provence). **Mood:** gilt on credit, ambitious bourgeois. **Layout:** vestibule (cloakroom Lectern) → long salon with a Pleyel grand under a too-large chandelier → card room (where Lucile sells fans in CH-03) → dining room.

| ID | Who | Lines |
|---|---|---|
| FIC-05 | Mme Hortense Lavergne | CH-03: `LAVERGNE [P:FIC-05:smile] Herz plays at nine. You play after him, if they're awake.` · CH-05+: `LAVERGNE [P:FIC-05:smile] Your name is cleared, and my gilt gets compliments.` |
| TF-009 | Baptiste, footman | `[N:Baptiste] Cards here, monsieur. Madame counts the guests, and then the spoons.` |
| TF-010 | M. Achille Lavergne, wholesale draper | `[N:M. Lavergne] Draper by day, patron by night. Both trades sell appearances.` |

**Secrets:** a Courage Draught under the card-room table (CH-03). **States:** CH-03 Lucile's fan tray in the card room (Vane's shadowed purse is seen from the salon doorway, scripted); CH-05+ a second chandelier "on approval".

### LOC-P06 Delacroix's Studio, 15 quai Voltaire — I · LM-12 · 22 × 16

**Open:** CH-03 (KEY-07 letter), CH-06 (Fri 2 Aug, the first canvas), CH-09 (the emblems), CH-E2 (portrait sitting); optional visits whenever Delacroix is in the party roster in Paris; **Close Call safe door** in every chapter that can have one. **Mood:** turpentine, Moroccan silks, river light. **Layout:** stair from the quai → studio (north window over the Seine, the *Women of Algiers* canvas under a sheet until CH-09, a dais, a Moroccan chest) → small sitting room (Delacroix's notebooks).

| ID | Who | Lines |
|---|---|---|
| TF-011 | Fanfan, the studio's colour-grinder boy | CH-03: `[N:Fanfan] Monsieur grinds his own vermilion. I grind the rest and sneeze.` · CH-09: `[N:Fanfan] He's drawn eight little emblems. A baton, a brush, a sword… for what?` · CH-E2: `[N:Fanfan] He's sent three models away this week. He was waiting for you two.` |

**Secrets:** a Courage Draught ×2 in the Moroccan chest (CH-03); the CH-09 emblem sheet is examinable on the easel (CANON LAW-22 clue); his notebooks in the sitting room stay shut (`MIN-JUN [P:PC-01:neutral] [C:grey](His notes. Not mine to read.)[/C]`). His favourite gifts are found elsewhere (the watercolour cakes at Couleurs Ravenel, P22). **States:** Fri 2 Aug only: *Le Pont Royal, effet de brume* on the dais (the first showing; Sand is not there, CANON §4b); CH-09 the *Women of Algiers* uncovered; CH-E2 the dais set with a piano stool and a candle (the sitting).

### LOC-P07 The Marais and Place Royale — T · LM-28 · 64 × 44

**Open:** CH-04 (riot, Wed 5 Jun), CH-07, CH-12 (Alkan's birthday Evening at P36), CH-14, CH-E2 (E04 at its north edge). **Mood:** old mansions turned workshops; tension before the riot, scar tissue after.

```
 Bd du Temple (north edge): [E04, CH-E2]
 Place Royale: arcades [LECTERN] . no. 6 (Hugo's windows) . [P36 Alkan house lane]
 Pavillon du Roi passage (south side) ---> rue Saint-Antoine [P08 barricade] [fountain]
 fiacre stand at the Bastille end; OM-A, OM-C
```

| ID | Who | Lines |
|---|---|---|
| NPC-32 | Victor Hugo (at his window) | CH-07: `[N:Victor Hugo] I watched your barricade from up here. I am writing nothing about it. Yet.` |
| NPC-43 | Honoré Daumier | CH-07: `[N:Daumier] I drew you on the barricade. No one believes it's the man in that coat.` |
| TF-012 | Berthe Rioux, seamstress | CH-04: `[N:Berthe] A march on the fifth, they say. My husband says stay in. I say sew faster.` · CH-05+: `[N:Berthe] Stones back in the street, holes in the shutters. Paris heals by paving.` |
| TF-013 | Old Fabre, cabinetmaker | CH-04: `[N:Old Fabre] Twelve hours a day for two francs. Then ask me why men march.` · CH-07: `[N:Old Fabre] I mended the shutters the riot broke. The riot paid better than work.` |
| TF-014 | Jeanne Lhuillier, widow | CH-04: `[N:Jeanne] My Paul fell at Saint-Merry last June. I march for him, not a party.` · CH-05+: `[N:Jeanne] Someone left flowers on the stones. It wasn't the Prefecture.` |

**Secrets:** a Throat Lozenge ×3 in the arcade's pillar niche (CH-04); a Hebrew psalter left for Alkan by a bookbinder under the Pavillon du Roi (CH-07+, Alkan's favourite gift); in CH-07 a ballad-seller sings "the Corean of the barricade" (Renown +5 the first time, Secrecy +0).
**States:** WS-03 dray (pre-CH-04); 5 Jun smoke haze and Onlookers at every window; WS-05 aftermath (candle shrine at the fountain, Tocsin Echoes on Z4 at night, children playing barricade with loose stones in CH-07); CH-E2 snow on the arcades.

### LOC-P09 Théâtre-Italien (Salle Favart) — I · LM-19 · 30 × 26

**Open:** CH-03 (Tue 2 Apr, the Smithson benefit; seen from the gallery); CH-12 exterior only (Sun 24 Nov walkout, on the P10 night variant at the place des Italiens). **Layout:** gallery stair → the *paradis* (top gallery) with a view down onto the stage and two pianos; corridors are closed off. **Townsfolk:** `[N:Usher] Gallery seats, the gods. You'll see the tops of two very famous heads.` (CH-03) · CH-12 exterior: `[N:Cab driver] Midnight, and the musicians walked out. Monsieur Berlioz is still shouting.`. **Secrets:** an Eyewash under a gallery bench (CH-03).

### LOC-P10 Grand Boulevards and the Passage de l'Opéra — T / mD · LM-04 · 2 screens: West 64 × 40, Centre 80 × 40 · night variant

**Open:** CH-05–CH-09 (the Act II hub); CH-12 (the walkout by night, then day); CH-13 (gala day); CH-14 (and the Opéra stage door by night for BOSS-36, §6); CH-E2. Passage de l'Opéra Echo nest mD: CH-05 (§6). **Mood:** gaslight, dandies, ices; money and gossip moving at a stroll.

```
 WEST: Madeleine . rue de la Paix [P18 Horlogerie Brucke] -> Place Vendome (WS-07)
       Bd des Capucines . [Hotel de la Lyre]
 CENTRE: Bd des Italiens: [Tortoni: Heine's table] [Cafe Hardy: elm bench, LECTERN] [fiacre stand]
   north side: rue Taitbout [Salon Bastide] . rue de Provence [P05] [no. 61 Liszt flat]
               rue de la Chaussee-d'Antin [P11] . rue Le Peletier [P27 Opera] <- [Passage de l'Opera mD]
   south side: place des Italiens [P09] . rue de Richelieu [Schlesinger's] [Pharmacie Laborde]
               rue Saint-Marc [P19 Maison Farrenc] . Passage des Panoramas
   east edge:  Comtesse Merlin's hotel (towards Porte Saint-Martin)
```

**Services:** Hôtel de la Lyre (inn) · Pharmacie Laborde, boulevard branch · Schlesinger's (Opus Scores; door opens CH-06 when Schlesinger is met, CANON NPC-41) · Heine's press rebuttal (§4.3) · T2 Salon Bastide (rue Taitbout, Taste Novel, FIC-17) and T3 Salon Merlin (Taste Romantic, NPC-52; CH-07+) as interiors · **Anna Liszt's flat** (rue de Provence 61, sub-interior): a free rest once per chapter from CH-07 (historical_cast) · Lectern ×3 (§4.1) · fiacre · OM-A. **Evening haunts** (secrecy_and_trust §3.6): Liszt at Tortoni's; Berlioz on the Café Hardy terrace from CH-12.

| ID | Who | Lines |
|---|---|---|
| TF-015 | Gustave, Tortoni waiter | CH-05: `[N:Gustave] Vanilla, pistachio or Neapolitan. The poets take theirs on credit.` · CH-13: `[N:Gustave] All Paris goes to the gala. I'll serve sorbets to empty chairs.` |
| TF-016 | M. Duval, Hôtel de la Lyre | `[N:M. Duval] Every room has a balcony. The poets rent them by the hour, to be seen writing.` |
| TF-017 | Émile Laborde, pharmacist | `[N:Émile Laborde] Father sells remedies to students. I sell them to dandies, in nicer bottles.` |
| NPC-30 | Heinrich Heine | CH-05+: `HEINE [P:NPC-30:wry] The Nightingale of Nowhere! For a fee, Paris forgets you.` |
| NPC-41 | Maurice Schlesinger | CH-06: `[N:Schlesinger] Chopin's Opus 10, fresh from the press. And I hear you transcribe marvels.` · CH-08+: `[N:Schlesinger] A musical gazette, monsieur. Next year. Paris needs someone arguing in print.` |
| NPC-48 | Anna Liszt (rue de Provence 61) | CH-07+: `[N:Anna Liszt] Franz is out. Franz is always out. Sit, have soup, you're too thin.` |
| FIC-17 | Mme Bastide | `[N:Mme Bastide] Novelty, Monsieur Kang! My guests are bored of anything written before Tuesday.` |
| NPC-52 | Comtesse Merlin | `[N:Comtesse Merlin] Sing or play, as you like. In Havana we never made a guest choose.` |
| TF-018 | "La Fouine", pickpocket chief | CH-05: `[N:La Fouine] Nice coat. Shame if someone admired it too closely.` · CH-14: `[N:La Fouine] Grey gloves pay better than purses this month. I took neither.` |

**Secrets:** a Paganini broadsheet pasted on the Passage de l'Opéra wall (CH-05+, Liszt's favourite gift); a box of cigars forgotten on Tortoni's terrace (CH-07+, Liszt's gift); a Bouillon ×2 under the elm bench before the Café Hardy (CH-05); fine kid gloves from a glover's tray in the Passage de l'Opéra, bought (CH-06+, Chopin's gift; price: items_and_equipment); 300 F in the Passage des Panoramas lost-and-found if the player has spoken to all nine townsfolk above (CH-08+).
**States:** night variant = gaslight, Gaslight Wisps on Z5, Tortoni full; WS-07 Vendôme crowds; WS-10 concert posters; WS-13 walkout outside P09; WS-14 gala carriages; CH-E2 snow and New Year sellers.

### LOC-P11 Chopin's Apartment, 5 rue de la Chaussée-d'Antin — I · LM-13 · 16 × 12

**Open:** CH-05 (after the Pleyel meeting), CH-09 (his confession); optional while Chopin is in Paris and in the roster (not 11 Aug–7 Sep); CH-12 one visit (bronchitis: he receives from a chaise longue, one cough, no more); CH-14; CH-E2. **Close Call safe door** from CH-06. **Layout:** concierge's lodge → stair → salon (Pleyel grand, Parma violets in a glass, a Polish map over the mantel) → study.

| ID | Who | Lines |
|---|---|---|
| TF-019 | Mme Pernelle, concierge | CH-05+: `[N:Mme Pernelle] Monsieur Chopin teaches until four. After four, only the violets.` · CH-12: `[N:Mme Pernelle] The doctor says no visitors. Monsieur says one. Don't make him laugh.` |
| PC-06 | Chopin (CH-12, not in the party) | `CHOPIN [P:PC-06:ironic] Sit. I am forbidden to talk, so you will have to.` |

**Secrets:** none to take (his gifts are found elsewhere: the Polish émigré newspaper at Père Gobert's stall, P22). **States:** CH-05 packing cases still in the study (he moved in June, CANON §3a); CH-09 the G-minor Ballade's pages on the stand, the last one blank (R-46); CH-12 the chaise longue by the stove and a doctor's bottle on the mantel; CH-E2 a winter fire, and the Ballade's pages put away in a drawer (history keeps its 1835 date).

### LOC-P12 Pleyel: Salle and Workshop, 9 rue Cadet — I / mD · LM-19 · Salle 28 × 22, Workshop 32 × 20

**Open:** CH-05 (meets Chopin), CH-07 (SQ-07 opens; Théo), CH-08 (KEY-17; Sat 21 Sep concert; first kiss on the roof), CH-14, CH-E2 (keepsake forge). **Layout:** showroom (grands in rows; **brass serial plates** examinable, the CH-05 clue that matches the Hidden Study upright, LAW-22) → Salle (300 chairs, stage) → yard → workshop (felt, spruce, iron frames, glue pots, Théo's bench from CH-07) → roof hatch (CH-08 only).
**Services:** Pleyel Voicing upgrades (KEY-12) · keepsake forge (CH-E2, §9) · Lectern in the showroom vestibule.

| ID | Who | Lines |
|---|---|---|
| NPC-15 | Camille Pleyel | CH-05: `PLEYEL [P:NPC-15:neutral] Every instrument here wears a brass plate. Read it.` · CH-E2: `PLEYEL [P:NPC-15:grave] A keepsake? Then it is not only metal we forge.` |
| NPC-16 | Friedrich Kalkbrenner | CH-05: `KALKBRENNER [P:NPC-16:neutral] Three years of lessons with me, and you may play in public.` |
| TF-020 | Maître Ducros, workshop foreman | CH-05: `[N:Ducros] Felt, spruce and iron, monsieur. Mind the glue pots, they bite.` · CH-07+: `[N:Ducros] The Aubray boy whittles keys on his break. Clever fingers, that one.` |
| FIC-01 | Théo Aubray | CH-07+: `THÉO [P:FIC-01:smile] Look, a key! Its hands are stuck, like a stopped clock.` |

**Secrets:** oversized orchestral manuscript paper in the Salle's music cupboard (CH-05+, Berlioz's gift); a Pitch Pipe ×2 on the tuner's shelf; a Maelzel metronome on the showroom counter, bought (CH-14, Julien's gift). **States:** CH-05 Marie Moke-Pleyel's comic-awkward scene with Berlioz in the showroom (NPC-45); WS-10 posters and storm; CH-E2 the forge lit in the yard.

### LOC-P14 Faubourg Saint-Germain — T · LM-07 · 72 × 44

**Open:** CH-05 (dress gate lifted), CH-07, CH-12 (one Evening: Salon d'Agoult, Vidal & Fils), CH-14, CH-E2. Not loaded in CH-09: Lucile's night break-in reaches P34 by scene cut (§6). **Mood:** shuttered mansions, old money, porters in livery. **Layout:** rue de Varenne (P34 Hôtel de Vane) ‖ rue Saint-Dominique (P15) ‖ rue de Beaune (Marie d'Agoult's T3 salon, Taste Sacred, NPC-18; Liszt met here in CH-05) ‖ rue du Bac (Missions Étrangères chapel; fountain Lectern; fiacre stand) ‖ Vidal & Fils on the rue du Bac corner.
**Services:** Vidal & Fils (high-tier weapons and armour; refuses service at Compromised) · T3 Salon d'Agoult · Lectern ×2 (rue du Bac fountain; rue de Varenne gate for P34, §4.1) · fiacre.

| ID | Who | Lines |
|---|---|---|
| TF-021 | Augustin Vidal | CH-05: `[N:Augustin Vidal] Our blades dress the Faubourg. My son sells to students; we sell to fathers.` · Compromised: `[N:Augustin Vidal] Forgive me. My clients would not like to see you served here.` |
| TF-022 | Grégoire, Suisse porter | `[N:Grégoire] Madame la Marquise is not at home. She is never at home to walkers.` |
| TF-023 | Marquise de Pontcarré, dowager | `[N:Marquise] Before the Revolution this street had forty carriages. Now, nineteen and a draper.` |
| TF-024 | A seminarian of the Missions Étrangères | `[N:Seminarian] Corée? Rome named a vicar for it two years ago. None of our priests has reached it yet.` |

**Secrets:** **the Missions Étrangères map (CH-05+):** a missionary wall map in the chapel corridor marks "Corée" with a single cross; examining it plays a wordless homesick beat (`MIN-JUN [P:PC-01:homesick] …`, LM-32 cue) and gives the Almanach entry "Corée". A Moroccan silk scarf in Vidal & Fils' window, sold to the party for a token sum by Augustin after CH-07 (Delacroix's gift; price: items_and_equipment). **States:** CH-07 embassy carriages on rue Saint-Dominique; WS-17 Hôtel de Vane shuttered (CH-14 after Vane defects); CH-E2 Vane's packing crates in his courtyard (Canvas Ledger spot #19).

### LOC-P15 Hôtel d'Apponyi (Hôtel de Monaco, 57 rue Saint-Dominique) — I · LM-21 · 40 × 28

**Open:** CH-07 (Sat 7 Sep duel, BOSS-08; Rossini judges); optional T3 salons with Countess Apponyi (Taste Virtuosic) CH-07–CH-09, CH-12–CH-14; CH-E2 (salon only, §9.1). **Layout:** courtyard → vestibule (anteroom Lectern) → **ballroom of mirrors** (two Pleyel grands facing each other; the claque's chairs) → Rudolf Apponyi's writing room (his journal on the desk: Almanach "An evening not recorded").

| ID | Who | Lines |
|---|---|---|
| TF-025 | Herr Pölzl, major-domo | CH-07, before BOSS-08: `[N:Herr Pölzl] His Excellency's guests are announced, monsieur. Even those who win.` · after BOSS-08: `[N:Herr Pölzl] The Count's diarist has a cold this week. He recorded nothing.` |
| NPC-27 | Count Antal Apponyi | CH-07: `COUNT APPONYI [P:NPC-27:uneasy] A duel of pianos in my house. Let it be a short one.` |
| NPC-28 | Countess Thérèse Apponyi | CH-07+: `THÉRÈSE [P:NPC-28:delighted] A Virtuosic programme, please. Vienna judges by the fingers.` |
| NPC-33 | Gioachino Rossini | CH-07: `ROSSINI [P:NPC-33:savouring] I judge with my ears and my supper. Both are waiting.` |

**Secrets:** a Smelling Salts ×2 in the cloakroom (CH-07). **States:** CH-07 the claque's chairs set in two rows facing Min-jun's piano; after the duel the chairs are stacked and one mirror is cracked if Min-jun won (`g_duel_thalberg_won`); CH-12–CH-14 salon nights, the ballroom lit by half its candles in winter; CH-E2 the Countess's salon only, the ballroom shut.

### LOC-P16 Palais-Royal — T · LM-04 · 56 × 48 · night variant

**Open:** CH-08 (sewer descent, P17), CH-14 (SQ-21 may use the café), CH-E2. **Mood:** gambling upstairs, booksellers below, pickpockets everywhere. **Layout:** the new glass-roofed Galerie d'Orléans (Lectern) ‖ garden with fountain ‖ arcades: Coutellerie du Palais, Hôtel des Arcades, the **Café des Trois Dièses** (Julien's café-concert cellar), the gaming-room stair ‖ cellar door to P17 behind the café (restricted zone, §4.3; a chalk J on its lintel from CH-08, the same mark found at the flooded Val-de-Grâce stair, §6).
**Services:** Hôtel des Arcades (inn) · Coutellerie du Palais (weapons, armour) · Lectern ×2 (§4.1) · fiacre · OM-B. **Evening haunt:** Julien at the Trois Dièses (CH-14, secrecy_and_trust §3.6).

| ID | Who | Lines |
|---|---|---|
| TF-026 | M. Constant, Hôtel des Arcades | `[N:M. Constant] Pay before midnight. After midnight my guests pay in dice.` |
| TF-027 | Mme Héloïse Bastien, cutler | `[N:Mme Bastien] Sabres, sword-canes, and a hammer for the young man with smith's arms.` |
| TF-028 | Mme Rigaud, owner of the Trois Dièses | CH-08: `[N:Mme Rigaud] Monsieur Julien plays at ten. Chords like a stair in the dark.` · CH-14: `[N:Mme Rigaud] He hasn't played since October. He sits there and listens to the rain.` |
| TF-029 | Old Pradel, bookseller | CH-08: `[N:Pradel] Le Corsaire, back numbers. The Mandarin Mimic sells best. No offence.` · CH-14: `[N:Pradel] Your caricature's out of fashion. Now they draw you as Orpheus.` |

**Secrets:** a café-concert song sheet pinned in the Trois Dièses cloakroom (CH-08+, Julien's gift); Neapolitan coffee from the café's counter, bought (CH-14, Julien's gift); a Courage Draught ×2 under the fountain rim (CH-08); an English Shakespeare at Pradel's stall, bought (CH-08+, Berlioz's gift). Gift prices are items_and_equipment's. **States:** night variant = gaming-room lamps, double pickpocket density; CH-14 the café dark except Julien's table; CH-E2 Mme Rigaud has hired a harpist (Julien plays at E04 now).

### LOC-P19 Maison Farrenc, 21 rue Saint-Marc — I · LM-15 · 20 × 16

**Open:** CH-05–CH-09, CH-12–CH-14, CH-E2 (shop from CH-05; the family met in CH-08). **Close Call safe door** from CH-05 (secrecy_and_trust §2.9.1). **Layout:** shop counter (Lucien, the engraver's apprentice, keeps it CH-05–CH-07; Aristide from CH-08; engraved plates in racks) → engraving room (the press) → stair to the house (Victorine's practising heard through the floor; Louise's voice behind a door until CH-08).
**Services:** Opus Scores (Period Scores, CANON §11c) · press rebuttal (§4.3; Lucien takes the copy and the 500 F to the printer until CH-08).

| ID | Who | Lines |
|---|---|---|
| TF-030 | Lucien, engraver's apprentice | CH-05–CH-07 (counter): `[N:Lucien] Monsieur Farrenc is at the printer's. I can sell, but I can't haggle.` · CH-08+ (press): `[N:Lucien] Every note backwards on copper. You learn to read in a mirror.` |
| — | Louise Farrenc (voice only, CH-05–CH-07) | `[N:Voice] Again from bar twelve, Victorine. Slower is not weaker.` |
| NPC-20 | Aristide Farrenc | CH-08: `A. FARRENC [P:NPC-20:smile] Haydn to Hummel, engraved here. Some music must not be lost.` · CH-12: `A. FARRENC [P:NPC-20:neutral] I worked out your road home. Madame Sand needed an address.` · CH-14 (after SQ-07): `A. FARRENC [P:NPC-20:grave] Tuteur. A large word. He'll have a guardian who notices him.` |
| NPC-21 | Victorine Farrenc | CH-08+: `VICTORINE [P:NPC-21:smile] Maman says I may play for you if I don't rush the trill.` · CH-14: `VICTORINE [P:NPC-21:giggle] A ship that sails on air? Papa says no. Maman says maybe!` |

**Secrets:** an old Couperin harpsichord edition on the bottom shelf, bought (CH-08+, Farrenc's gift); an edition of Bach's *Well-Tempered Clavier*, bought (CH-08+, Alkan's gift); an engraver's burin on Lucien's bench, given if the player watches him pull one proof (CH-08+). Gift prices are items_and_equipment's. **States:** CH-05–CH-07 Lucien alone at the counter, the house door shut; CH-08 Louise at the counter; CH-14 SQ-07 papers on the desk; CH-E2 the Overture No. 1 proofs drying (CANON §15e).

### LOC-P20 Lucile's Attic, 7 rue des Grands-Augustins — I · LM-03 · 14 × 10

**Open:** CH-04; CH-05–CH-09 (party base; Lectern; dark from the CH-09 dawn, WS-11); CH-11 (her interlude); CH-12; CH-14; CH-E2 (her lodging until the wedding: KEY-40 still gives this address). **Layout:** five flights of stairs (Bourdin's door on the first, Mme Gervais's laundry on the fourth) → one room under a skylight: easel, fans drying on strings, Théo's cot by the stove.

| ID | Who | Lines |
|---|---|---|
| FIC-23 | M. Bourdin, landlord | CH-04: `[N:M. Bourdin] Rent's the first, Mademoiselle. The gentleman who bought your notes is prompt.` · CH-09: `[N:M. Bourdin] Gone, she and the boy. Rent's paid to Christmas. I didn't ask who paid.` |
| TF-031 | Mme Gervais, laundress | CH-05: `[N:Mme Gervais] The boy coughs less since the Sister's medicine. God keep her.` · CH-11: `[N:Mme Gervais] Men took the boy at the dispensary. She ran out without her shawl.` |
| FIC-01 | Théo | CH-04–CH-06, examine only (he is asleep; coughs are SFX, historical_cast): `MIN-JUN [P:PC-01:worried] [C:grey](A boy asleep by the stove. Breathing carefully.)[/C]` · CH-07–CH-09: `THÉO [P:FIC-01:smile] Lucile says not to touch the wet fans. I touch the dry ones.` |

**Secrets:** Valencia oranges in a crate on the landing, bought from Mme Gervais's brother (CH-05+, Lucile's gift); Sand's *Indiana* on the sill (cannot be taken: `MIN-JUN [P:PC-01:neutral] Her copy. Inscribed. I'll find her another.`; a second copy is sold at Père Gobert's stall, P22). **States:** WS-11 empty and dark (CH-09 dawn to CH-11); CH-11 interlude: Théo's cot stripped; CH-14 the IMPASTO canvases stacked; CH-E2 her Salon canvas on the easel.

### LOC-P21 Maison Corbel, rue Dauphine — I · LM-07 · 18 × 14

**Open:** CH-04, CH-07 (her point-of-view scene: the letter at the counter), CH-09; shop CH-04–CH-09, CH-12–CH-14, CH-E2. **Layout:** front shop (sign: **Curiosités Corbel**) → workroom (fan and snuffbox painters' benches) → back room (the dead drop; where Vane recruited Lucile on 28 Apr).
**Services:** Curiosités Corbel (relics; the high-tier relic counter refuses service at Compromised, §4.3).

| ID | Who | Lines |
|---|---|---|
| FIC-04 | Anselme Corbel | CH-04: `CORBEL [P:FIC-04:neutral] Fans, snuffboxes, a cameo of the late Emperor. Honest work.` · CH-06 (WS-08, from Mon 5 Aug): `CORBEL [P:FIC-04:smile] A crowd at my window, for fog! I should sell tickets.` · CH-09: `CORBEL [P:FIC-04:frightened] I know nothing. I keep a shop. Buy something and go.` |
| TF-032 | Zoé, fan painter | `[N:Zoé] Lucile paints the best fans in Paris and the worst lies. Her face tells all.` |

**Secrets:** a Sculptor's Oil in the workroom drawer (CH-07); on the curiosities shelf, an automaton songbird (CH-07+, Alkan's gift) and a child's fan painted by Zoé (CH-08+, Farrenc's "gift for Victorine"), both bought (prices: items_and_equipment). **States:** WS-08 window crowd (Anachronic showing, from Mon 5 Aug); WS-11 shutters half down; CH-14 Corbel sits on the family council (LAW-23) and closes early that day; CH-E2 her fans in the window, signed "L. Aubray" (historical_cast).

### LOC-P22 Seine Quays and Pont des Arts — T · LM-22 · 2 screens: Left Bank 96 × 32 (Pont Royal to the quai des Grands-Augustins), Right Bank 64 × 32 (Tuileries terrace to the Louvre and the Pont Neuf) · night variant

**Open:** CH-03–CH-09, CH-11 (Left Bank screen, Lucile), CH-12–CH-14, CH-E2. **Mood:** dawn mist, bouquinistes, the bridge where the romance begins and breaks.

```
 RIGHT BANK:  [Terrasse du Bord de l'Eau, Tuileries: L2]  [BG-1 Port Saint-Nicolas]  quai du Louvre [P13 door, LECTERN]
                 ||                               ||  PONT DES ARTS (toll booth, WP-A)          ||  Pont Neuf (Henri IV, WP-C)
            PONT ROYAL (L1)                                                                     ||
 LEFT BANK:  foot of rue du Bac . quai Voltaire [P06] . quai Malaquais [no. 19, Sand] . Institut [LECTERN steps]
             rue de Seine [Couleurs Ravenel] . quai Conti . rue Dauphine [P21] . quai des Grands-Augustins [P20] [BG-2]
```

**Services:** Couleurs Ravenel, at the head of rue de Seine (brushes, CH-05+) · bouquinistes (flavour sales) · Lectern ×2 (§4.1) · fiacre · OM-B · BG-1, BG-2. **Bridges:** the Pont Royal and the Pont Neuf are Hunted-tier papers checkpoints (§4.3); the Pont des Arts asks its sou and no papers. **Lesson spots** (LAW-23 table): L1 "Reflections" at the Pont Royal stair (CH-06, river mist); L2 "Broken Colour" on the Terrasse du Bord de l'Eau (CH-07, Noon).
**19 quai Malaquais (George Sand's door):** opens CH-06–CH-09 and in CH-14 before Thu 12 Dec, and never while Liszt, Delacroix or Chopin is in the active party (CANON §16e); it hosts the optional CH-07 quai Malaquais supper (historical_cast: Min-jun and Lucile only). Otherwise `[N:Mariette] Madame writes until dawn and receives at noon. Bring Mademoiselle Aubray.` (TF-087, Sand's maid).

| ID | Who | Lines |
|---|---|---|
| TF-033 | Père Gobert, bouquiniste | CH-03: `[N:Père Gobert] Old maps, old sermons, old love letters. Nothing new is worth reading.` · CH-05+: `[N:Père Gobert] A quarry map, 1780s, two francs. Do try not to fall in.` · CH-12+: `[N:Père Gobert] The Corean! You sell better than Byron this winter. Sign one?` |
| TF-034 | Mme Toussaint, Pont des Arts toll-keeper | CH-03–CH-04: `[N:Mme Toussaint] One sou to cross, monsieur. Painters pay the same as peers.` · CH-05+: `[N:Mme Toussaint] One sou, Monsieur Kang. My grandson heard you play. He says you're worth two.` |
| TF-035 | Mlle Adèle Ravenel, colour merchant | CH-05: `[N:Mlle Ravenel] Kolinsky, hog, badger. And credit, for you, Mademoiselle Aubray.` · CH-09 (dawn, WS-11): `[N:Mlle Ravenel] She passed at first light with the boy and a trunk. Not a word to me.` · CH-11 (to Lucile): `[N:Mlle Ravenel] Back, mademoiselle? Your credit is good here. It always was.` |
| TF-036 | Yvon Le Goff, master of *La Mouette* | CH-08: `[N:Le Goff] La Mouette carries coal, wine and fools. Today, fools. Aboard!` · CH-14: `[N:Le Goff] Ice on the oars this morning. Where to, my sorcerer?` |

**Secrets:** the toll-keeper's box of lost things holds a Sal Volatile ×2 and, from CH-06, Byron's poems (Delacroix's gift), given once the party has crossed ten times; Parma violets from a flower barrow on the Pont Neuf, bought (CH-06+, Chopin's gift); at Père Gobert's stall, Nerval's *Faust* (1828) (CH-03+, Berlioz's gift), Sand's *Indiana* (CH-05+, Lucile's gift) and a Polish émigré newspaper (CH-06+, Chopin's gift), all bought; English watercolour cakes on the Couleurs Ravenel counter, bought (CH-06+, Delacroix's gift). Gift prices are items_and_equipment's. Crossing tolls: 1 sou, auto-deducted, every chapter.
**States:** CH-05 dawn mist (the joining lesson on the Pont des Arts); CH-06 river mist at the Pont Royal (L1); CH-09 dawn mist (the confession), then the WS-11 walk to the empty attic; night variant = lamps on the water, Lucile's Evening haunt (secrecy_and_trust §3.6) and the proposed stage of BQ-PC02 part 5, Dusk (part 6, Night, is the Night of Stars at P28, CANON §0c); CH-12 SQ-13's easel spot by the Pont Neuf steps; CH-E2 ice at the bank, bouquinistes in mittens.

### LOC-P23 British Embassy (Hôtel de Charost) — I · LM-11 · 30 × 22

**Open:** CH-09 only (Thu 3 Oct wedding; Liszt a witness). **Layout:** courtyard → chapel (borrowed flowers) → salon (the supper table, the window Petit-Louis taps on). Lectern: none (the thread split starts here).

| ID | Who | Lines |
|---|---|---|
| TF-037 | Mr. Hobbs, embassy footman | morning: `[N:Footman] The chapel is through here, sir. The bride is late; the groom is louder.` · supper, after Petit-Louis's tap: `[N:Footman] The groom has left his own supper, sir. With a sword-cane. Is that French custom?` |

**Secrets:** a Bouillon ×2 on the buffet. **States:** morning: the chapel with borrowed white roses and too few chairs; evening: the supper table, one candle per guest, and the garden window that Petit-Louis taps on (CANON §4b).

### LOC-P24 Montmartre — T · LM-23 · 64 × 56 · night variant

**Open:** CH-06 (first painting outing), CH-14 (MR-1 mooring; SQ-12 studio; Lesson L4 "Night"), CH-E2 (E02 hub; the proposal at dawn, Sun 9 Feb 1834). **Mood:** windmills, vines, open sky, the city laid out below the wall.

```
   north slope: gypsum-quarry mouths (restricted)          [MR-1 mooring field, CH-14]
          [Saint-Pierre: Chappe telegraph on the tower]
   windmills . windmill lane . vines . low wall (painting spot; L4 at night)
   [Auberge des Trois Moulins: LECTERN in the yard]   [studio: SQ-12 -> E02]
          rue des Martyrs down to the Barriere des Martyrs (octroi post; Guard picket to CH-05) -> W01
```

**Services:** Auberge des Trois Moulins (inn) · Lectern · fiacre (stand at the barrier) · MR-1 (CH-14).

| ID | Who | Lines |
|---|---|---|
| TF-038 | Mère Lacaze, Trois Moulins | CH-06: `[N:Mère Lacaze] Wine from our own vines, outside the toll. Cheap and honest, both.` |
| TF-039 | Nicolas Blot, miller | `[N:Blot] When the wind's right I grind. When it's wrong, I watch the painters.` |
| TF-040 | M. Chaix, telegraph *stationnaire* | CH-06: `[N:M. Chaix] Lille to Paris in minutes, by arms and eyes. Don't ask what it says.` · CH-14: `[N:M. Chaix] Your balloon startled my signals. Lille thinks Paris is under attack.` |
| TF-041 | Suzon, vintner's girl | CH-14 night: `[N:Suzon] Painting the sky? Sit on the low wall. The stars are bigger there.` |
| NPC-25 | Comte de Rambuteau | CH-14 at MR-1: `RAMBUTEAU [P:NPC-25:harried] A flying ship needs a permit. None exists. I'll invent one.` (the `byt_sky_omnibus` payoff, historical_cast) |

**Secrets:** a Chocolat in the windmill's grain loft (CH-14); a rosary on the church step, returned or kept (CH-06+, Liszt's gift; returning it to the curé gives a Panacea instead). **States:** CH-06 plein-air day; CH-14 dirigible mast and the studio "À vendre" sign (WS-16 after SQ-12); night variant = the Night lesson; CH-E2 snow, the Atelier lit (§9).

### LOC-P25 Prefecture of Police and Cells, rue de Jérusalem — I / mD · LM-28 · 26 × 20

**Open:** CH-04 (Gisquet clears Min-jun with KEY-10 and Daumier's testimony; KEY-11 issued), Unmasking (cells escape mD, BOSS-42; §6). **Layout:** courtyard (restricted) → clerks' hall → Gisquet's office → cell stair. `[N:M. Pinson] Name, birthplace, trade. "Corée" isn't on my form. I'll use the margin.` (TF-042, clerk, CH-04) · `GISQUET [P:NPC-24:grave] Again, Monsieur Kang. Paris gossips; I listen. Sit.` (Unmasking).

### LOC-P28 Panthéon and Montagne Sainte-Geneviève — T · LM-01 · 56 × 48 · night variant

**Open:** CH-12 (night, after the escape from Val-de-Grâce), CH-14 (Night of Stars on the roof, Wed 18 Dec; P38 optional; crypt-door prompt), CH-15 (scaffold ascent with David d'Angers, NPC-44), CH-E2 (the E03 door; the first Lectern to go dark). **Layout:** Panthéon steps (Lectern) and David d'Angers' pediment scaffold ‖ Saint-Étienne-du-Mont (Clef III beneath) ‖ École Polytechnique gate (Clef VI beneath) ‖ crypt door (P38 optional in CH-14; P29 in CH-15) ‖ roof reached by the scaffold, or by rope from *La Lumière* (Night of Stars only).

| ID | Who | Lines |
|---|---|---|
| TF-043 | Maître Roch, scaffold foreman | CH-12: `[N:Maître Roch] Monsieur David carves at dawn. Nobody climbs without his leave.` · CH-14: `[N:Maître Roch] Up the scaffold, at night? Fine. Fall quietly.` |
| TF-044 | Félix Tanguy, Polytechnique student | CH-12: `[N:Félix] The cellars under the École hum. We tell the first-years it's ghosts.` · CH-14: `[N:Félix] I've worked out your balloon's lift. You're overloaded by one Liszt.` |

**Secrets:** a Sel de Vie behind the scaffold's tool chest (CH-14); Perfect Pitch hears all three Clef hums here at once (Almanach "The Mountain Sings", CH-14). **States:** CH-12 fog-night; CH-14 clear frost-night, stars (LM-30 cue on the roof); CH-E2 its Lectern is the first to go dark (§4.1).

### LOC-P32 Île de la Cité and Notre-Dame — T · LM-04 · 64 × 36

**Open:** CH-04 (to the Prefecture), CH-05–CH-09, CH-12–CH-14, CH-E2. **Mood:** Hugo's cathedral, dilapidated, its spire gone since the 1790s; weathered gargoyles, half broken; the old Hôtel-Dieu straddling the river arm. **Layout:** parvis (Lectern) ‖ Notre-Dame (tower stair to the bourdon *Emmanuel*) ‖ Hôtel-Dieu front ‖ quai Desaix flower market (BG-3) ‖ rue de Jérusalem (P25) ‖ north edge: Pont au Change → place du Châtelet (Fontaine du Palmier; OM-C).

| ID | Who | Lines |
|---|---|---|
| TF-045 | Mélie, flower-seller | CH-04: `[N:Mélie] Lilac, lily of the valley. May flowers, monsieur, while they last.` · CH-14: `[N:Mélie] Hothouse roses. Dear, but she'll remember.` |
| TF-046 | Jacquot, bell-ringer's boy | CH-04: `[N:Jacquot] Since Monsieur Hugo's book, all ask for the hunchback. I say he's at lunch.` · CH-14: `[N:Jacquot] We ring the bourdon at Christmas. Come and feel it in your teeth.` |
| NPC-25 | Rambuteau (CH-05 after Sat 22 Jun, Châtelet fountain: the clean-water scene) | `RAMBUTEAU [P:NPC-25:smile] Fountains first. A city that drinks clean water argues less.` |

**Secrets:** a Four Thieves ×3 under the flower stall (CH-04); from the bell chamber (CH-14) Perfect Pitch hears Rachmaninoff's *The Bells* in the city's peals, the canon trigger for REP-42's transcription (CANON §15d). **States:** Gargoyle Echoes on Z3; CH-E2 snow on the towers.

### LOC-P33 Père-Lachaise Cemetery — T (opt) · LM-18 · 48 × 48

**Open:** CH-14 (optional), CH-E2. Outside the wall; on foot by the Barrière d'Aunay (Z7) or by fiacre. **Layout:** gate (Lectern) → avenue → Héloïse and Abélard's tomb → hill (Molière, La Fontaine) → **an unmarked patch of grass in the eleventh division**. Min-jun visits alone (the party waits at the gate). `[N:Père Mathieu] Héloïse and Abélard by the gate, Molière up the hill. Room for all the rest.` (TF-047, keeper, CH-14) · CH-E2: `[N:Père Mathieu] You again, monsieur, at that empty patch. Waiting for someone?` · at the patch: `MIN-JUN [P:PC-01:homesick] …Not yet. Not for a long time.` (the Lantern Rule: he names no one). **Secrets:** none; the scene is the secret.

### LOC-P35 Conservatoire Concert Hall, rue Bergère — E · LM-11 · 32 × 28

**Open:** CH-14 (Sun 15 Dec: Hiller, Chopin and Liszt play Bach's three-keyboard concerto, Habeneck conducting); CH-E2 (Sun 22 Dec afternoon: Berlioz's concert, Girard conducting, Paganini in a side box). Entered through P03. **Layout:** foyer → green room (Lectern) → hall (stage, three keyboards in CH-14; orchestra in CH-E2; side boxes). `[N:Usher] Three keyboards on one stage. They've had the floor shored up.` (TF-048, CH-14) · CH-E2: `[N:Usher] The Italian in the side box? Paganini. Don't stare. He notices.`.

### LOC-P36 Alkan Family House — I · LM-16 · 18 × 14

**Open:** CH-04 (shelters the wounded; Alkan joins), CH-05–CH-09 (Alkan's Evening haunt), CH-12 (his 20th birthday, Sat 30 Nov: one Evening scene), CH-14, CH-E2 (Canvas Ledger spot #13). **Close Call safe door** from CH-04. **Layout:** a cramped house off Place Royale: schoolroom (his father's pupils' benches), music room with a pedal piano, kitchen, a stair crowded with siblings' instrument cases. Townsfolk are unnamed family (party.md and historical_cast own the household).

| ID | Who | Lines |
|---|---|---|
| — | Alkan's sister | CH-04: `[N:Alkan's sister] Put the wounded on the pupils' benches. Father will teach standing.` · CH-05+: `[N:Alkan's sister] He practises nine hours. We eat our soup in time with the pedals.` |
| — | Alkan's younger brother | CH-12: `[N:Alkan's brother] Twenty today, and he asked for a metronome. We bought him a cake.` |

**Secrets:** a Tisane ×3 on the kitchen shelf (CH-04); an edition of Bach's *Well-Tempered Clavier* open on the pedal piano is examinable only (his gift copy is bought at Maison Farrenc, P19, CH-08+). **States:** CH-04 the schoolroom an infirmary (riot wounded on the benches, basins on the desk); CH-05–CH-09 pupils' slates on the benches; CH-12, Sat 30 Nov: the birthday supper laid after nightfall, when the Sabbath ends, the siblings playing a round on every instrument in the house; CH-14 a row of tuning forks cooling on the schoolroom desk (KEY-32, Alkan's work for the descent; examine only).

### LOC-P37 Sœur Marthe's Dispensary, Val-de-Grâce gate — I · LM-31 · 20 × 14

**Open:** CH-07 (Théo's care; SQ-07 step 2, 300 F), CH-08, CH-11 interlude (Théo taken, Thu 14 Nov), CH-12, CH-14, CH-E2. **Layout:** waiting benches → boiling copper and clean-linen shelves → three cots → Marthe's desk. Entered from P02's south end, beside the Val-de-Grâce gate lodge Lectern.

| ID | Who | Lines |
|---|---|---|
| ANA-06 | Sœur Marthe | CH-07: `MARTHE [P:ANA-06:neutral] Boil it. Then boil it again. Sit, child. Breathe slowly.` · CH-11 (to Lucile): `MARTHE [P:ANA-06:worried] The abbey undercroft. At vespers. Quietly, child.` · CH-12: `MARTHE [P:ANA-06:determined] His key hangs in the sacristy at vespers. Go.` · CH-14+: `MARTHE [P:ANA-06:determined] I chose my side when I chose this work.` |
| TF-049 | Mme Leroux, a patient's mother | `[N:Mme Leroux] The Sister saved my little one last spring. Water, salt, sugar, patience.` |
| TF-050 | Brother Côme, orderly | `[N:Brother Côme] We boil the linen, the water, the instruments. Surgeons laugh. Patients don't.` · CH-11: `[N:Brother Côme] Two men in grey, a closed carriage. The boy didn't cry. I did.` |

**States:** CH-07+ `[IF:byt_boil_water]` Rambuteau's fountain at the door, a queue with jugs (historical_cast); CH-07–CH-08 Théo's cot by the window (SQ-07 step 2); CH-11 an empty cot with a whittled key on the blanket; CH-12 the back door to the hospital laundry left unbarred (how Marthe smuggles Lucile in); CH-E2 Marthe is the Aubray-Kangs' physician (a "Rest" option here restores HP/INS free).

### LOC-P39 Princess Belgiojoso's Salon — I · LM-19 · 30 × 22

**Open:** CH-14 (SQ-20 Salon Circuit, T4; Thalberg's December visit; BOSS-35 option; safe house and **Close Call safe door**), CH-E2 (BOSS-35 rematch, February). **Layout:** anteroom (Lectern) → salon with two pianos back to back → a pale study with Lombard maps → a back stair to the stable yard (how Vane and Tissot come and go after the defection).

| ID | Who | Lines |
|---|---|---|
| NPC-26 | Cristina Belgiojoso | CH-14: `BELGIOJOSO [P:NPC-26:fierce] Vienna took my lands and left me two pianos. Fair.` · CH-E2: `BELGIOJOSO [P:NPC-26:smile] My guest from Vienna is back. Do not win too quickly.` |
| TF-051 | Signor Ferrante, Lombard exile | CH-14+: `[N:Signor Ferrante] At home they jail men for songs. Here they only review them.` |
| TF-089 | Nina, the princess's maid | CH-14 (after Vane defects): `[N:Nina] The English lord takes his soup upstairs. He tips like a man saying goodbye.` |

**Secrets:** a Panacea in the study bureau (CH-14). **States:** CH-14 before SQ-20, the salon half-furnished (her fortune is confiscated; the pianos are lent); after Vane's defection, his and Tissot's coats on the anteroom pegs (historical_cast: she shelters them); CH-E2 Thalberg's travelling case in the anteroom in February.

---

## 6. Paris 1833: Dungeon Hooks

Interiors, puzzles, treasure and encounter tables are `dungeons.md`'s; this list fixes only each door and what the town does around it.

| LOC | Door (host map) · opens · town-side note |
|---|---|
| P01 Saint-Denis Galleries | Carmel quarry mouth, P02 south end (restricted) · CH-01, exit only · an Inspection des Carrières grille seals it from CH-02 (the link reopens from P29 in CH-15) |
| Rust gallery (rung 4) | The old well in the Hôtel du Lys d'Or yard, P02 · CH-04 only · Min-jun goes down alone to map the quarries for his door; one mapped gallery (`dungeons.md`); it collapses behind him, and when he climbs out the map item *Quarry Notes* is gone from his satchel (stolen in the dust: Brücke and Julien, CANON §4c rung 4). From CH-05 the well is capped with fresh masonry (Mme Varin's CH-05+ line, §5 P02) |
| P03 undercroft (mD) | Old Menus-Plaisirs storeroom trapdoor, P03 · CH-03 · Père Lhomme lends the key once Berlioz vouches |
| P04 cellars (mD) | Tavern trapdoor · CH-02 · BOSS-02; the Cartouche Glove (CANON §11a) |
| P08 Barricade | rue Saint-Antoine, P07 · CH-04 · Onlookers at every P07 window |
| P10 Passage de l'Opéra nest (mD) | The Passage's middle gallery · CH-05 · its shops shutter during the nest |
| Val-de-Grâce quarry access (rung 6) | A cellar stair behind the hospital laundry wall at P02's south end · CH-06 · the access Min-jun was searching, found flooded (WS-21: standing water to the third step, a chalk J on the lintel, the mark Julien's toughs use; the same J is chalked on the Trois Dièses cellar door in CH-08). Lucile's portrait flickers `guilty` if she is in the party (CANON §4c rung 6). Sealed by a hospital grille thereafter |
| P13 Louvre | quai du Louvre door, P22 · CH-06 · Lucile's copyist's card admits the party |
| P17 Sewers | Cellar door behind the Café des Trois Dièses, P16; BG-5 outfall · CH-08 |
| P18 Clockwork Undercroft (mD) | Back stair of Horlogerie Brücke, P10 west · CH-07 · the shop front (ten thousand ticks, a music-box chime, LM-10 cue) has no service; its door is forced in CH-14 (KEY-28) |
| P25 cells (mD) | Prefecture cell stair, P32 · Unmasking |
| P26 Val-de-Grâce | Hospital gate, P02 south end; chaplain's door via KEY-22 · CH-12 night · surgeons and patients above ground are non-combat |
| P27 Opéra | Stage door and front of house, rue Le Peletier, P10 · CH-13 · P10 in gala state (WS-14) |
| P27 Opéra by night (BOSS-36) | The rue Le Peletier stage door on P10's night variant · CH-14 only · opens with BQ-PC07's finale step (Liszt hears a violin on one string behind the shutters); missable; closes at the crypt-door prompt. The stage-door Lectern stands lit (§4.1) |
| P29 / P30 | Panthéon crypt door, P28 (KEY-27) · CH-15–CH-17 · point-of-no-return prompt at the door (CANON §0c) |
| P31 Bercy | BG-7 beyond the Barrière de la Rapée · CH-09 · Berlioz's rescue boards *La Mouette* at BG-2 |
| P34 Hôtel de Vane | rue de Varenne gate, P14 · CH-09 (Lucile): entered by scene cut at P34's garden wall at night; P14 is not loaded (it has no night state) · CH-14 by the gate, by day · shuttered after Vane's defection (WS-17) |
| P38 Philosophers' Tombs | Crypt side door, P28 · CH-14 optional · BOSS-40 |

---

## 7. Regional 1833

### LOC-R01 Forest of Fontainebleau — T / field · LM-23 · 72 × 64

**Open:** CH-10 (Corot, GST-03; an Echo stalks the forest), CH-14. **Layout:** a field map, not a town: the Bas-Bréau oaks (entry from W02) → Corot's easel among birches → Gorges d'Apremont rocks (Lectern) → woodcutters' clearing (rest at a hut fire: free, once per visit) → Franchard gorge (the Echo's lair; `dungeons.md` owns the encounter). No inn or shop (CANON §12 lists none).
`COROT [P:NPC-13:smile] Sit still, monsieur. You are standing in my foreground.` (CH-10) · `[N:Gros-Jean] Something walks the Franchard gorge at dusk. Not a boar. It hums, like a bell under water.` (TF-052, woodcutter, CH-10) · talk again (CH-10): `[N:Gros-Jean] And at Apremont something ticks in the heather. That one I leave alone.` (historical_cast: the Franchard Echo and the Apremont automaton scout are separate threats; the scout is a Y2 Hunter Automata formation by the Apremont rocks) · CH-14: `[N:Gros-Jean] Since you came, the humming stopped. My axe thanks you.` **Secrets:** a Cordial ×2 under the Apremont rock (CH-10).

### LOC-R03 Nohant — T · LM-23 · 48 × 40 (house interiors 40 × 24)

**Open:** CH-10 (Sand in residence; Liszt kept at R04, §2.4), CH-14 (Sand gone; the house kept for winter; Chopin stays aboard *La Lumière*, §2.4). **Mood:** Sand's house, cigars, children, fireside; a long Berry autumn.

```
   village green (old elms) . little church of Sainte-Anne
   [garden gate: LECTERN] -> garden (POINTILLE painting spot; L3 lesson) -> farmyard
   HOUSE: hall . salon (piano; dinner with Casimir) . dining room . Sand's study
          blue room (Lucile) . kitchen (Mere Thibault) . back stair
```

The CH-10 night attack is a house-defence wave fought **inside** (hall, salon, back stair; Candle light), because R03 has a single day state (§4.2). The garden is the L3 lesson spot; Window Talk 1 is the salon fireside.

| ID | Who | Lines |
|---|---|---|
| NPC-14 | George Sand | CH-10: `SAND [P:NPC-14:smile] Ma petite Lumière, the blue room. Monsieur, the questions.` |
| NPC-53 | Casimir Dudevant | CH-10: `[N:M. Dudevant] Monsieur. Dinner is at six. We are civil at dinner.` |
| NPC-50 | Solange Dudevant | CH-10: `[N:Solange] Can you play a bourrée? Only bourrées are allowed today.` |
| TF-053 | Mère Thibault, cook | CH-10: `[N:Mère Thibault] Madame eats when she remembers. You'll eat now.` · CH-14: `[N:Mère Thibault] Madame's in Paris and the house is cold. Sit by my fire.` |
| TF-054 | Père Grillon, hurdy-gurdy player | CH-10: `[N:Père Grillon] A bourrée? The Berry has danced it this way since my grandfather.` · CH-14: `[N:Père Grillon] I played your little Corean tune at the fair. They liked it.` |

**Secrets:** **the *Metronome of Nohant*** (UI "Nohant Metronome"; relic, CANON §10c), CH-14 only: on the salon piano with a card in Sand's hand, "Pour celui qui bat mal la mesure. — G." (in-world text; translation shown: "For the one who keeps poor time"); a Valencia orange ×3 in the larder (CH-10).

### LOC-R04 La Châtre — T · LM-23 · 48 × 36

**Open:** CH-10 only. **Mood:** a market town with a squat old keep. **Layout:** market square (stalls) → Auberge du Lion d'Argent (inn; Liszt's benefit concert in its long hall; Lectern in the inn hall) → the keep → the Indre bridge (road to Nohant, 1.5 lieues; Lectern for R05).
**Services:** Auberge du Lion d'Argent (inn; its long hall offers an inn-hall performance counted as a T1 salon, CCR) · Mercerie Aubert (consumables; CCR).
`[N:M. Pacaud] Monsieur Liszt has taken the first floor and half the town's candles.` (TF-055, innkeeper) · `[N:Mère Chaumette] Chestnuts, walnuts, a goose if you've the coin.` (TF-056) · `[N:Mme Aubert] Thread, tisanes, lamp oil. Everything a traveller forgets.` (TF-057). **Secrets:** a Smelling Salts ×2 under the market cross (CH-10).

### LOC-R06 Liège — T · LM-29 · 56 × 40

**Open:** CH-11 only (Chopin joins). **Mood:** coal smoke over the Meuse, gun-makers' signs, a ten-year-old at the keyboard. **Layout:** Meuse quay (diligence yard) → Place Saint-Lambert and the Prince-Bishops' palace front → Hôtel de la Meuse (inn; its salon piano is where César Franck plays for the visitors; Lectern) → arms-makers' street (Coutellerie Lambotte; CCR).
`[N:M. Franck] César will play for you, messieurs. Then you will write to Paris of him.` (NPC-49) · `CÉSAR [P:NPC-01:smile] Papa says I mustn't stop between pieces. May I stop now?` · `[N:Mme Dejardin] The Franck boy plays our piano every evening. His father sells the seats.` (TF-058) · `[N:Hubert] Coal from Seraing, iron from Seraing. Everything black comes from Seraing.` (TF-059, coal porter) · `[N:M. Lambotte] Liège steel, monsieur. Hammers for your large friend, sabres for the fair one.` (TF-060). **Secrets:** a Café Noir ×2 behind the Hôtel de la Meuse piano (CH-11). **States:** CH-11 evening: César at the piano, his father at the door with a cash box; the arms-makers' street shuttered by dusk.

### LOC-R07 Düsseldorf — T · LM-29 · 56 × 44

**Open:** CH-11 (Mendelssohn, Clara and Wieck, "Florestan", Czerny; the Seventh Panel), CH-14. **Layout:** Rhine quay → old Electoral Palace (the Academy: Schadow's office, the long gallery where Mendelssohn's private November academy is held) → Hofgarten → Gasthof zum Goldenen Anker (inn; Lectern; its taproom piano offers an inn-hall performance counted as a T1 salon, CCR) → Farbenhandlung Weiss (brushes and relics; CCR) → Löwen-Apotheke (consumables; CCR), the only consumables counter between Paris and Strasbourg before BOSS-14. German speech carries `[in German]`; Liszt, Mendelssohn or Clara interpret (CANON §16c).
`[N:Frau Haas] [in German] Herr Mendelssohn rehearses at nine. The whole street hums the oboe part.` (TF-061) · `[N:Schadow] [in German] A curious French allegory. I bought it for the colour, not the sums.` (NPC-51, CH-11) · `[N:Karl Reinhold] [in German] The Director wants Nazarene saints. I paint the river when he looks away.` (TF-062, student) · `[N:Herr Weiss] [in German] Brushes from Munich, varnish from Antwerp. Paris prices, alas.` (TF-063) · `[N:Herr Adler] [in German] Valerian, camphor, a cordial for the boat. The Rhine is cold in November.` (TF-091, apothecary). **Secrets:** a Grand Cordial in the Academy's cast room (CH-14). **States:** CH-14 the Academy quiet; Schadow absent; Frau Haas remembers the party.

### LOC-R10 Strasbourg and the Kehl Bridge — T · LM-29 · 64 × 40

**Open:** CH-11 (Thu 21 Nov: Sand's letter waits), CH-14. **Layout:** cathedral square (the spire; inside, the great **astronomical clock, stopped for decades**: Almanach "A Stilled Clock", one line from Alkan if present) → Hôtel de la Cathédrale (inn; Lectern; the letter at the desk; its dining room offers an inn-hall performance counted as a T1 salon, CCR) → Pharmacie du Dôme (consumables; CCR) → the bridge of boats to Kehl with French and Baden customs posts (KEY-20; no battles at the posts).
`[N:M. Kientz] A letter waits for you, monsieur, from Paris. A lady's hand.` (TF-064, CH-11) · `[N:Customs officer] Papers. Baden lies across the boats. France lies behind you.` (TF-065) · `[N:M. Wendling] Tincture of valerian for the nerves, monsieur? You look as if you need two.` (TF-066). **Secrets:** a Cordial in the stopped clock's case, a verger's forgotten flask (CH-11). **States:** CH-11 Thu 21 Nov: rain on the square, Sand's letter in the inn's pigeonholes; CH-14 the bridge of boats half-dismantled for the ice (the Baden post closed; Kehl unreachable).

### LOC-R11 Étretat Cliffs — field (BQ-PC02b) · LM-03 · 48 × 40

**Open:** CH-14 (BQ-PC02b; BOSS-39 optional). **Layout:** shingle beach with fishermen's capstans and boats turned into huts (Lectern at the capstans) → the Porte d'Aval arch → cliff path → the Needle viewpoint (plein-air spot; the Light cycles in BOSS-39). `[N:Père Lemonnier] Paint the Needle if you like. It's stood longer than any king.` (TF-067).

### LOC-R12 Le Havre Harbour — T (BQ-PC02b) · LM-03 · 56 × 40

**Open:** CH-14 (BQ-PC02b). **Layout:** outer harbour jetty (dawn view of masts and sun: the painting she chooses not to take) → fish auction hall (*la criée*; the subject of her alternative Salon entry, KEY-40) → basin quays (Lectern at the harbour office). `[N:Grande Margot] Mackerel! Herring! Sole for the gentry! Bid, or out of my light!` (TF-068) · `[N:Pilot Dufresne] Sunrise on the outer harbour. Every painter wants it. None get up.` (TF-069).

### LOC-R14 Cologne: the Rhine Landing — T · LM-29 · 48 × 32

**Open:** CH-11 only (Tue 19 Nov). **Layout:** the unfinished cathedral with its medieval crane on the stump of the south tower → PRDG quay office (Lectern) → the *Concordia* taking on coal (gangway = door to R08). `[N:Herr Brungs] [in German] The Concordia sails for Mainz at seven. Coal first, passengers after.` (TF-070). **Secrets:** a Chocolat ×2 in the quay office coal scuttle (CH-11). **States:** Tue 19 Nov dawn: coal smoke, the crane's wheel turning; after boarding the map closes (CANON §12 revisit "—").

**Regional dungeon hooks.** R02 Château d'Orsenne: gatehouse off the Fontainebleau–Orsenne path (CH-14; CH-E2 via SQ-23 by diligence). R05 Vallée Noire: the Indre path from R04's bridge (CH-10, night-only map). R08 *Concordia*: R14's gangway. R09 Lorelei: landing below the rock, from R08 in CH-11 and by dirigible in CH-14. R13 Aachen border post: on the Liège–Aachen leg, entered automatically (KEY-20 check; rain).

---

## 8. Seoul 2026

### 8.1 Prologue (CH-P, Thu 5 Mar 2026, 22:10–23:40 KST)

#### LOC-S01 Hanseong Conservatory: Annex (Room B-07) — I · LM-02 · corridor 40 × 12; B-07 12 × 10

```
 ANNEX B1  +----------------------------------------------------------+
           | B-01  B-03  B-05  [B-07]           vending   stair up -> |
           | ======== corridor (strip lights, one flickering) ======== |
           | B-02  B-04  B-06   B-08    notice board   guard's chair    |
           +----------------------------------------------------------+
 B-07: battered conservatory upright (KEY-04 on the stand) . high window-well
       to the courtyard . storage closet (hairline crack: the hum) . radiator
```

**Interactables (CH-P).** The upright: the first frame is the double fallboard tap; playing *Clair de lune* is the movement tutorial's goal. The closet: examine ×3 (hum louder each time; Perfect Pitch hears it as a sustained D) → pull off the back panel → the counterweighted bookcase swings → stair to S02. The notice board: a faded 2012 flyer, "Visiting Professor Lazare Morvan — have you seen him?", now a campus joke ("the professor in the basement", CANON §3d). Vending machine: canned coffee, ₩1,500 (flavour; he has no use for it). No battles, no shops.
`[N:Mr. Hwang] Rooms lock at midnight, Min-jun-ssi. The basement's cold. So's the ghost.` (TF-071, night guard) · `[N:So-ra] Still here? The annex hums at night. Heating, probably.` (TF-072, student, leaving at 22:30).
**CH-E1 state:** missing posters for Min-jun still on the board beside the 2012 flyer; B-07 holds Seo-yeon's violin case and a card on the stand, "keeping it warm"; maintenance has tacked the closet's back panel in place (Seoul branch: at 16:52 the arrival party pushes it out from behind and climbs into the snow). Mr. Hwang: `[N:Mr. Hwang] I put up your poster myself in March. Welcome home, Min-jun-ssi.`. **CH-E2 coda:** Seo-yeon practising alone at dusk; the hum returns at 16:52.

#### LOC-S02 The Hidden Study — I / E · LM-01 · 16 × 14

```
        stair (from the bookcase) v
   [LECTERN, CH-P only]     [plaque: "Pour M., qui doit venir. -- Les Amis, 1886"]
   [1880s Pleyel upright; score open: LM-01's eight notes]   [music stand + brass hook: KEY-01]
   [dust outline where a small painting hung]  facing ->  [THE DOOR: 8 panels, clock-dial lock at 7:51]
```

**Puzzle (binding, CANON §4b CH-P):** the dial stands at 7:51; play **D E F♯ G A B C♯ D** on the upright; the hands turn to XII and line up into the key-shaped sigil; take KEY-01 from its hook; unlock; play; step through. Wrong notes cost nothing. The eight panels' emblems (baton, brush, sword-cane, rapier, hammer, quill, sabre, folio) are examinable but described only as "carvings" until CH-09 lets the player recognise them.
**CH-E1:** Window arrival point (16:52; KEY-01 still in the dial); the BOSS-30 arena on New Year's Eve (the dial is the 12-turn countdown, CANON §13); afterwards the oscillator shards glitter on the floor and the study stays sealed by agreement with Prof. Yoon. **CH-E2 coda:** Min-jun's phone on the floor below the Door, face up, at 16:52.

### 8.2 Seoul epilogue (CH-E1, Tue 22 Dec 2026 – Fri 1 Jan 2027)

#### LOC-S03 Jeong-dong and the Deoksugung Stonewall Road — T · LM-24 · 64 × 40 · one state: winter dusk, snow (a Night palette shift, no new map, for the 31 Dec beats)

**Layout:** the stone-wall road under bare ginkgos (busking spot 7, at the west end, clear of the Headline closure) → the red-brick Jeong-dong church (1897) and its side lane (the Headline detour, §2.5) → the white tower of the old Russian legation on its rise → Hanseong Conservatory gate (S01, S05, S10 inside; Lucile needs the KEY-33 lanyard) → City Hall station stair → Haneul Mart → Ms. Bae's hotteok cart.

| ID | Who | Lines |
|---|---|---|
| TF-073 | Ms. Bae, hotteok seller | `[N:Ms. Bae] Hotteok, two thousand won. Cinnamon sugar. It burns your tongue in winter.` · 31 Dec: `[N:Ms. Bae] Concert tonight? I'll keep two hot for after. Pay me next year.` |
| TF-074 | Jun-ho, Haneul Mart clerk | `[N:Jun-ho] Snow boots by the door. Your friend reads the ramyeon labels like scripture.` |
| TF-071 | Mr. Hwang, night guard (at the gate from 24 Dec) | `[N:Mr. Hwang] Reporters again, Min-jun-ssi. I told them you're shy. Use the church lane.` |
| PC-02 | Lucile, first evening (22 Dec) | `LUCILE [P:PC-02:surprised] [in French] This city keeps lightning in glass.` (CANON LAW-24 line) |

**States:** 22 Dec dusk: Min-jun's missing-person posters still taped to the conservatory gate; from the "missing student returns" news (Spotlight +10), the posters are gone and two reporters wait at the gate (they close the road's east end at Headline); 31 Dec Night palette: a queue for the S10 concert under paper lanterns, the hotteok cart lit.

#### LOC-S04 Kang Family Apartment — I · LM-32 · 20 × 16

**Layout:** entry (shoes off; a pair of white sneakers missing since March) → living room (floor heating; Seo-yeon's music stand) → kitchen (*patjuk* on Dongji, 22 Dec) → Min-jun's room, kept as he left it (his keyboard, an Alliance Française textbook, a 2026 calendar still on March) → Seo-yeon's room (Lucile sleeps here) → balcony over Mapo. Free rest (beds; Spotlight −2 a night, secrecy_and_trust §2.10). Haneul Mart on the block's ground floor.

| ID | Who | Lines |
|---|---|---|
| FIC-11 | Park Hye-jin (Tier C) | `[N:Park Hye-jin] Eat first. Then tell me where you've been. Then eat again.` |
| FIC-10 | Kang Do-hyun (Tier C) | `[N:Kang Do-hyun] Your room's as you left it. Your mother dusted round your mess.` |
| PC-09 | Seo-yeon | 22 Dec: `SEO-YEON [P:PC-09:angry] I kept your practice room warm. You owe me nine months.` |

**States:** 22 Dec, first night: his mother asleep at the kitchen table beside the cooling *patjuk*, a bowl kept for him; from 23 Dec: Lucile's paint box on the balcony sill, Seo-yeon's music stand moved to make room; 31 Dec: a second place laid beside his at the table (Lucile is family now), and the calendar in his room turned to December.

#### LOC-S05 Conservatory Library and Archives — I · LM-01 · 32 × 24

**Layout:** reading room (long tables, green lamps) → archive cage (box JD-1888-07, KEY-36) → Prof. Yoon's carrel. The Thu 31 Dec 23:00 packet opening (the brief's image) is staged at the reading room's centre table (Seoul branch); in the CH-E2 coda Seo-yeon is given the packet here after ~17:10.

| ID | Who | Lines |
|---|---|---|
| FIC-12 | Prof. Yoon Mi-rae | `YOON [P:FIC-12:smile] Gloves on. Some of these letters waited a long time for you.` · 31 Dec, 23:00: `YOON [P:FIC-12:astonished] The wax is unbroken. It's eleven. Open it.` |
| TF-075 | Mr. Lim, archivist | `[N:Mr. Lim] Box JD-1888-07. Sealed in 1906. Mind the wax; it's older than us all.` |

**States:** 23–30 Dec: Théo's open letter laid out under glass on Yoon's carrel (LAW-24); 31 Dec: the room dark but for the centre table's lamp; CH-E2 coda: one lamp, the hangul-labelled packet waiting (LAW-25).

#### LOC-S06 Hangaram Art Museum: "Light & Colour" — I · LM-03 · 4 rooms (24 × 16 each)

**Layout (binding hang, CANON §12):** Room 1 three Monet *Grainstacks* (she laughs) → Room 2 Pissarro, *Boulevard Montmartre at Night* → Room 3 van Gogh, *Starry Night over the Rhône* (she weeps: "They found it without a door") → Room 4 her own canvas, labelled "Circle of Corot, *Le Pont Royal, effet de brume*, c. 1833" and lent from a private collection in La Châtre (she chooses to leave it anonymous, LAW-24). Entry needs KEY-34. Gift shop sells postcards only (flavour).

| ID | Who | Lines |
|---|---|---|
| TF-076 | Ms. Seo, docent | `[N:Ms. Seo] Please, not so close to the van Gogh, ma'am. Ma'am? Are you all right?` · Room 4: `[N:Ms. Seo] Nobody knows the painter. A woman, some say. The light is too new.` |

**States:** Room 4's label reads aloud as a scripted beat (Spotlight +5, secrecy_and_trust §2.10); after it, Room 4's bench is the one place in Seoul where Lucile sits alone.

#### LOC-S07 Hongdae Busking Street — T · LM-24 · 64 × 36 · one state: night

**Layout:** station exit plaza (busking spot 1) → walking-street stage (spot 2) → playground corner (spot 3) → noraebang (the CH-E1 *Phrase* scene) → Gyeoul Outfitters (head and body gear; CCR, Canon Additions) → Haneul Mart → street-food row. At Headline+ the walking street closes and spots 1–3 are unavailable (§2.5).

| ID | Who | Lines |
|---|---|---|
| TF-077 | DJ Moon, busking-ladder rival | `[N:DJ Moon] This corner's mine on Saturdays. Pull a bigger crowd and it's yours.` · after spot 3 is cleared: `[N:DJ Moon] Fine. The corner's yours. Who taught your friend to paint that fast?` |
| TF-078 | Mrs. Choi, noraebang owner | `[N:Mrs. Choi] Room four, one hour. The tambourine's free. Damages aren't.` |

**States:** 24–25 Dec: Christmas couples and a carol from every shop door; from 26 Dec: DJ Moon's amp at spot 1 until he is beaten; 31 Dec: the street empties toward Jongno by 23:00.

#### LOC-S10 Conservatory Concert Hall and Clock Tower — E / D approach · LM-10 → LM-26 · hall 40 × 30

**Layout:** foyer → hall (stage with a concert grand for the Thu 31 Dec *Harmonies* premiere) → backstage practice rooms (their **metronomes** are the save points, CANON §11h) → clock-tower door (the climb is `dungeons.md`'s; it leads down to S02 for BOSS-30).

| ID | Who | Lines |
|---|---|---|
| TF-079 | Stage manager | before 31 Dec: `[N:Stage manager] House opens at half nine. Whoever keeps winding the tower clock, it isn't us.` · 31 Dec, after the attack: `[N:Stage manager] The tower clock's stopped at twelve. Nobody touch it.` |

**States:** 26–30 Dec rehearsals (the hall is open to the party; the tower door is chained); 31 Dec: full house, then the attack (Brücke's horns in the flies), the chain cut.

#### LOC-S11 Bosingak Pavilion — E · LM-26 · 40 × 32 · one state: night, snow

**Layout:** the pavilion and bell above a fenced plaza (busking spot 8), Jonggak station stair. Midnight: 33 strokes. `[N:Steward] Thirty-three strokes at midnight. Behind the line, please, and mind the snow.` (TF-080). The promise at the bell (no proposal in CH-E1, CANON §16f) is a scenario scene staged at the plaza's east rail. **States:** before 31 Dec: an empty plaza, one steward, busking allowed; 31 Dec from 23:30: the crowd fills the plaza and busking closes.

#### LOC-S12 Insadong — T · LM-24 · 56 × 32

**Layout:** main lane of antique and paper shops → Mr. Baek's coin shop (francs at ₩200 each, CANON §14) → a teahouse up a side alley (the Headline detour) → Hanji-bang (relics: charms, *norigae*, brush sets; CCR) → spiral shopping courtyard (busking spot 4) → Haneul Mart → Anguk station.

| ID | Who | Lines |
|---|---|---|
| TF-081 | Mr. Baek, numismatist | `[N:Mr. Baek] Louis-Philippe sous? I buy by weight, young man. Keep the silver ones.` |
| TF-082 | Ms. Kim, teahouse | `[N:Ms. Kim] Jujube tea for the cold. Your friend holds the cup like a chalice.` |

**States:** selling francs inside Mr. Baek's shop costs nothing, but paying with 1833 coins anywhere in public costs Spotlight +3 (secrecy_and_trust §2.10); at Headline the main lane closes and the teahouse alley carries all traffic.

#### LOC-S13 French Embassy in Seoul — I · LM-03 · 24 × 18

**Layout:** consular waiting room → interview desk → courtyard. The d'Orsenne Foundation's letter vouches for her; KEY-41 issued. No forgery is shown, and nothing on screen reveals her birth year (CANON LAW-24).

| ID | Who | Lines |
|---|---|---|
| TF-083 | M. Ferrier, consular officer | `[N:M. Ferrier] Your French, madame, is my great-grandmother's letters come to life. Sign here, please.` |
| TF-090 | Ms. Han Ji-soo, consular assistant (Hanmadi teacher) | `[N:Ms. Han] Seoryu is documents, ireum is name. You'll write both a hundred times.` |

#### LOC-S14 Yanghwajin Foreign Missionary Cemetery — T · LM-30 · 40 × 36

**Layout:** hillside rows above the Han → chapel → Théo's stone near the chapel ("THÉOPHILE AUBRAY · FACTEUR DE PIANOS · 1821–1898") → steps down to the riverside park (busking spot 5, outside the cemetery). Real graves are rendered as generic stones; no real name is legible. `[N:Mr. Jo] Aubray? The row by the chapel. Few visit that row in winter.` (TF-084, caretaker). **States:** first visit: snow on Théo's stone, no flowers; afterwards: Lucile's sprig of dried lavender from her paint box on the stone, which stays for the rest of CH-E1.

#### LOC-S15 Kang Piano Service, Euljiro — I · LM-32 · 16 × 12

**Layout:** workbench (felt hammers, a radio on low) → parts shelves → back room. **Service:** weapon upgrades (CANON §12). `[N:Kang Do-hyun] Hand me that baton. I'll re-felt the grip. Felt's felt, any century.` **States:** from 23 Dec: Min-jun's 1833 baton on the bench under a lamp; after S08: a shuttered arcade shutter two doors down rattles in the wind (the dungeon's entrance, closed after BOSS-29).

**Dungeon hooks.** S08 Euljiro Underground Arcade and Line 2 tunnels: stairs from Euljiro 3-ga station and a shuttered arcade shutter near S15 (the abandoned busker's metronome is its save point). S09 Namsan: footpath from Myeongdong; the cable-car plaza outside it holds the Namsan busking spot.

**Busking ladder spots (CANON §4f).** 1–3 Hongdae (S07 exit plaza, walking-street stage, playground corner) · 4 Insadong (S12 courtyard) · 5 Yanghwajin (S14 riverside park) · 6 Namsan (cable-car plaza) · 7 Jeong-dong (S03 ginkgo road) · 8 Bosingak plaza (S11). Rookie → Legend in that order of recommended difficulty.

**Hanmadi word sources (40 words, CANON §4f).** Each listed teacher gives the words in their row, one per conversation, once Lucile has heard that word in an ambient line; 별 *byeol* is not on the list (it is the reward skill). Jae-won's optional busking clip (secrecy_and_trust §2.10) gives one S07 word early.

| Where (teacher) | Words |
|---|---|
| S04 (mother, father, Seo-yeon) — 8 | 엄마 *eomma* mum · 아빠 *appa* dad · 밥 *bap* meal · 팥죽 *patjuk* red-bean porridge · 따뜻해 *ttatteutae* it's warm · 동지 *Dongji* winter solstice · 오빠 *oppa* big brother · 가족 *gajok* family |
| S03 (Ms. Bae, Jun-ho, Mr. Hwang) — 5 | 눈 *nun* snow · 은행나무 *eunhaengnamu* ginkgo · 호떡 *hotteok* sweet pancake · 돌담길 *doldamgil* stone-wall road · 겨울 *gyeoul* winter |
| S01/S05/S10 (Prof. Yoon, Mr. Lim, stage manager) — 5 | 교수님 *gyosunim* professor · 피아노 *piano* · 연습 *yeonseup* practice · 음악 *eumak* music · 악보 *akbo* score |
| S06 (Ms. Seo) — 4 | 그림 *geurim* painting · 빛 *bit* light · 색 *saek* colour · 화가 *hwaga* painter |
| S07 (DJ Moon, Mrs. Choi, Jae-won) — 5 | 노래 *norae* song · 노래방 *noraebang* singing room · 대박 *daebak* amazing · 떡볶이 *tteokbokki* rice cakes · 친구 *chingu* friend |
| S12 (Mr. Baek, Ms. Kim) — 4 | 차 *cha* tea · 붓 *but* brush · 한지 *hanji* mulberry paper · 동전 *dongjeon* coin |
| S14 (Mr. Jo) — 3 | 강 *gang* river · 바람 *baram* wind · 기억 *gieok* memory |
| S15 (father) — 2 | 조율 *joyul* tuning · 망치 *mangchi* hammer |
| S11 (steward) — 2 | 종 *jong* bell · 새해 복 많이 받으세요 *saehae bok mani badeuseyo* Happy New Year |
| S13 (Ms. Han, TF-090) — 2 | 서류 *seoryu* documents · 이름 *ireum* name |

### 8.3 Paris-branch coda in Seoul (CH-E2, Tue 22 Dec 2026, played as Seo-yeon)

Route (6–8 minutes, no battles, CANON LAW-25): S01 B-07 (practice; the hum at 16:52) → closet and stair → S02 (the phone; the video plays as a cutscene) → S03 campus walk in falling snow (her Spotlight-free sprite; townsfolk give one line each: Mr. Hwang, Ms. Bae) → ~17:10 phone call from Prof. Yoon → S05 reading room (the packet with the hangul label; KEY-39; the portrait) → fade on her bow lifting. Only these maps are loaded; W03 is not.

---

## 9. Paris 1834 (CH-E2)

### 9.1 Winter Paris (WS-19, Sun 22 Dec 1833 – Sat 1 Mar 1834)

W01 takes its winter state: snow on every roof, ice at the river's edge, braziers at the fiacre stands, the Winter overlay encounters (§3). **Transport:** foot, omnibus and fiacres (CANON §11h); *La Mouette* is laid up for the winter at BG-2; *La Lumière* stays moored at MR-1 until the Sat 1 Mar finale flight, then is dismantled there (SQ-23); a diligence runs Paris–Fontainebleau only, for SQ-23's Château d'Orsenne (R02). **Open:** P02, P03 with P35, P04, P05, P06, P07 with E04, P10 (salons Bastide and Merlin), P11, P12, P14 (d'Agoult; P34's courtyard), P15 (salon only), P16, P19, P20, P21, P22, P24 with E02, P28 (E03 door), P32, P33, P36, P37, P39, E01, E05 (fiacre). **Closed:** P01, P08, P09, P13 (the Louvre is shut for the Salon hang and reopens as E01), P17, P18's undercroft (the shop front is open; Brücke works at the bench for SQ-23's scenes), P23, P25 (no Unmasking), P26, P27, P29, P30, P31, P38. Secrecy is retired; the HUD slot shows the Canvas Ledger (CANON §4f).

**New winter lines** (other winter lines sit in their §5 entries): `[N:Mme Toussaint] Ice on the river, and still one sou. Love isn't charged extra.` (P22) · `[N:Gustave] A hot chocolate for the painter? On the house. She's in all the papers.` (P10, after the jury).

### 9.2 LOC-E02 Atelier Aubray-Kang — I (home hub) · LM-22 · 24 × 18

```
   [skylight: cracked (bare) / glazed (restored)]
   [Lucile's easel]   [Delacroix's spare easel: restored only]   [Pleyel piano: restored only]
   [gallery wall: 19 hooks, one per recovered canvas]   [LECTERN]   [stove]
   [door -> P24 lane]          [loft ladder: Min-jun's cot]       [window: Paris below]
```

**Exists in every CH-E2 run** (CANON §12). States are keyed to the engine flag `g_atelier_restored` (dialogue_style_guide §2.3). **Bare** (`not_g_atelier_restored`; SQ-12 not done): one easel, no piano, a cracked skylight, the friends' pooled "wedding money" paid the rent (cutscene); the 5,000 F restoration is a side task with the next free SQ number (`side_and_bond_quests.md`). **Restored** (`g_atelier_restored`; SQ-12 or the side task): glazed skylight, the Pleyel piano and Delacroix's spare easel: the two upgrade stations. **Station functions (proposal; CCR in Canon Additions):** the piano offers Pleyel Voicing upgrades without the trip to P12; the easel offers Lucile's brush upgrades from Couleurs Ravenel stock. **Gallery wall:** every canvas recovered for the Canvas Ledger hangs on its own hook as it comes home, so the room fills through the winter. **Services:** free rest (the loft cot is Min-jun's; Lucile still lodges at P20 until the June wedding, as her Salon *livret* address shows), Lectern (the last to go dark, §4.1). `[N:Ginette] Water for the painters! Two sous a bucket, and I carry it up the hill.` (TF-085, water-carrier). The proposal at dawn, Sun 9 Feb, is staged at P24's low wall; the Sat 1 Mar birthday supper and the *Harmonies* finale (REP-28, MUS-170) are staged in this room.

### 9.3 LOC-E04 *Le Diapason Bleu* — I · LM-08 · 20 × 14

**Where:** Boulevard du Temple, P07's north edge. **Until 1 Jan 1834:** a boarded shopfront; Julien sanding the bar (recruited or not). **From January:** blue lamps, a bad upright, a knee-high stage, eight tables, and a loose stage board that SQ-23's Walkman scene may use. `JULIEN [P:ANA-03:smile] Blue lamps, a bad upright and real chords. Mine, this time.` · `[N:Lisette] He says the new tune is his own. He says it like a confession.` (TF-086, barmaid).

### 9.4 LOC-E01 Salon of 1834 (event-stage parts) — D / E · LM-27

**Sat 15 Feb (BOSS-32):** the jury room off the Grande Galerie: a long baize table of Academicians; Ingres's chair at the head (Favor −30 opener), Delaroche's at the window (the swing vote, SQ-11); Delacroix, no juror, pleads from an advocate's bench by the door. **Sat 1 Mar (opening):** the Salon Carré hung floor to cornice; *Women of Algiers*, *Lady Jane Grey* and *Saint Symphorian* at eye level (CANON §3a); KEY-40's No. 61 hung *au ciel* on the north wall. The crowd, the canvas's HP bar and BOSS-33 belong to `bosses.md` and `dungeons.md`.

**Dungeon hooks.** E03 The Dead Heart: the Panthéon crypt door at P28, optional (Archon mid-gesture, the Unwritten). E05 Delorme's Atelier: a mirrored house on the Île Saint-Louis's north quai, by fiacre; stormed on the morning of Sat 1 Mar (CANON §4f).

### 9.5 Canvas Ledger recovery spots (19)

Each spot is a map event (a canvas glimpsed, then 1–2 Living Tableau battles, CANON §4f). `epilogues.md` owns the scenes and titles; this doc fixes the places.

| # | Map | Spot | # | Map | Spot |
|---|---|---|---|---|---|
| 1 | P21 | Corbel's back room | 11 | P02 | A student's room at the Lys d'Or |
| 2 | P06 | Delacroix's sitting room | 12 | P07 | Berthe Rioux's workroom |
| 3 | P19 | Victorine's practice room | 13 | P36 | Alkan's music room |
| 4 | P12 | Salle Pleyel corridor | 14 | P24 | Trois Moulins dining room |
| 5 | P39 | Belgiojoso's study | 15 | P37 | Marthe's desk |
| 6 | P10 | Tortoni's back room | 16 | P14 | The Marquise de Pontcarré's hall |
| 7 | P10 | Hôtel de la Lyre, a dealer's room | 17 | E04 | Above Julien's bar |
| 8 | P16 | Pradel's stall, Galerie d'Orléans | 18 | P03 | Hippolyte's garret |
| 9 | P22 | Père Gobert's bouquiniste stall | 19 | P14 | Vane's packing crates (P34 courtyard; before he sails in March) |
| 10 | P32 | Mélie's flower stall | | | |

---

## Canon Additions & Cross-Doc Notes

**Canon Change Requests** (not used as canon until the Lead Designer amends CANON):

- **CCR: night states (§11i).** This doc reads "night map variants" as *second authored states* and adds none, but gives the three overworlds a Dusk/Night palette shift (needed for night dirigible flights) and authors some maps with a single night or dusk state (R05, S07, S11 night; S03 dusk). Request: one clarifying sentence in §11i. Touches: art_and_ui, epilogues, act3.
- **CCR: new fictional shops.** Mercerie Aubert (R04, consumables), Coutellerie Lambotte (R06, weapons/armour), Farbenhandlung Weiss (R07, brushes/relics), Pharmacie du Dôme (R10, consumables), Gyeoul Outfitters (S07, Seoul head/body gear), Hanji-bang (S12, Seoul relics). CANON §12 names no regional vendor and no Seoul armour or relic vendor, although §14 prices Seoul armour and relics. Touches: items_and_equipment, salons_duels_and_economy.
- **CCR: Hotel Ginkgo** (fictional, S03, ₩60,000), open only while S04's lobby is blocked at Spotlight Headline+. Touches: secrecy_and_trust, epilogues.
- **CCR: Maison Grimaud** opens as a P02 colour shop on flag `aubray_debt_cleared` (CANON §12 never clears the debt). Proposal: Vane hands back the 1,200 F notes when he defects (CH-14). Touches: act4_and_epilogue, anachronists, items_and_equipment.
- **CCR: W01 scope.** P31 Bercy and P33 Père-Lachaise lie outside the toll wall; request LOC-W01 read "inside the toll wall, plus Montmartre, Bercy and Père-Lachaise". Touches: dungeons, historical_notes_and_liberties.
- **CCR: E02 upgrade stations:** piano = Pleyel Voicing upgrades; easel = Lucile's brush upgrades (Couleurs Ravenel stock). Touches: items_and_equipment, skills_and_progression.
- **CCR: townsfolk.** TF-001–TF-086 are doc-local, fictional and tier C; any that another doc needs should take the next free FIC number.

**Shared facts defined inside this doc's slice:**

- **W01 service nodes:** the Messageries royales diligence yard; the Hôtel des Postes event door (Lucile alone sees Sand onto the Lyon mail-coach, Thu 12 Dec); moorings MR-1 (Montmartre, *La Lumière*'s home and the CH-E2 "Montmartre mooring") and MR-2 (Champ-de-Mars). Touches: act4_and_epilogue, epilogues.
- **Transport:** barge *La Mouette* (master Yvon Le Goff, TF-036; landings BG-1–BG-7; 1 F a hop; laid up in CH-E2); omnibus lines OM-A *Dames Blanches*, OM-B *Favorites*, OM-C *Écossaises*; per-leg diligence fares (§2.4); dirigible landing and "wait for nightfall" rules; a CH-E2 Paris–Fontainebleau diligence for SQ-23; Seoul fares and the taxi refusal at Headline+. Touches: salons_duels_and_economy, epilogues, side_and_bond_quests.
- **Act I district blockers** and the CH-05 opening on the tailcoat delivery (CANON §5g). Touches: prologue_and_act1, act2.
- **Encounter zones** Z1–Z7, Y1–Y8, Seoul static pockets and step rates; the bestiary fixes rosters. Touches: bestiary, dungeons, epilogues.
- **Weather overlays;** falling snow counts as precipitation, so outdoor battles use Fog. Touches: combat_ensemble.
- **Lectern rules,** the town Lectern list and the CH-E2 dimming order. Touches: epilogues, dungeons.
- **Secrecy placements:** Watcher posts and restricted zones, the four checkpoint bridges, inn-ambush odds (1 in 3; 1 in 6 at P04), Compromised refusals, press-rebuttal points (Heine at Tortoni; Maison Farrenc). Touches: secrecy_and_trust.
- **Staging enforcement:** Liszt is moved to R04 whenever the party enters R03 in CH-10 (CANON §16e); R04, R05, R06, R08, R13 and R14 close after their chapter; optional salon windows at P05 and P15. Touches: act3, salons_duels_and_economy.
- **Sub-interiors (not new LOCs):** Salons Bastide and Merlin and Anna Liszt's flat in P10; Salon d'Agoult and the Missions Étrangères corridor in P14; the fictional **Café des Trois Dièses** (Julien's 1833 café, with the P17 door) in P16. Touches: anachronists, act2, side_and_bond_quests (SQ-21).
- **Item placements in towns:** all 24 favourite gifts of the eight characters (CANON §11f), and the **Nohant Metronome** in the CH-14 R03 revisit (if items_and_equipment places the relic elsewhere, that doc wins and this spot becomes a Cordial). Touches: items_and_equipment.
- **CH-E1:** the 8 busking spots, the 40 Hanmadi words and their teachers (syllables must be in the ≤ 400-syllable hangul subset), Haneul Mart branches. Touches: epilogues, art_and_ui.
- **CH-E2:** the 19 Canvas Ledger spots, the Atelier gallery wall, Lucile lodging at P20 until the June wedding (matching KEY-40's address), E04 opening on 1 Jan 1834. Touches: epilogues.
- **For historical_notes_and_liberties to verify:** Marie d'Agoult's 1833 salon on rue de Beaune; Comtesse Merlin's hôtel toward the Porte Saint-Martin; the Messageries royales address; Sand and Musset leaving from the Hôtel des Postes; the omnibus company names; the one-sou Pont des Arts toll; Notre-Dame without its spire; the stopped Strasbourg astronomical clock; the Düsseldorf Academy in the old Electoral Palace; the Kehl bridge of boats; Chopin at 4 Cité Bergère until June 1833.
