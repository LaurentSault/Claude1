# HARMONIES OF THE LOST ERA — THE CANON

> **Canon status:** version **1.0**, dated **2026-10-06**. This file is the single source of truth for every shared fact.
> **Rule:** **If any document disagrees with this canon, the canon wins; log proposed canon changes in §2** (Canon change log, §2b).
> **Cite as** "CANON §n" plus the stable ID (e.g. "CANON §13 BOSS-27"). IDs are never renumbered. A downstream doc that creates a new item takes the next free number in its family and logs it in §2b.
> **Calendar convention:** 1833–34 dates are Gregorian, Paris local mean time (UTC+0:09:21). 2026–27 dates are Seoul time (KST, UTC+9). The two are linked at the same calendar date and UTC clock time (LAW-06). Weekdays are given where a scene is dated.
> **Geography convention:** Paris in 1833 had twelve arrondissements, numbered differently from today. In-world text names *quartiers* and streets, never modern arrondissement numbers.
> **Identity spine (memorise):** protagonist **Kang Min-jun** (강민준); heroine **Lucile Aubray**; school **Hanseong Conservatory of Music** (한성음악원); cabal **La Confrérie de l'Heure Immobile** (the Brotherhood of the Stilled Hour, "the Anachronists"); leader **Archon** (Dr. Lazare Morvan, alias Baron Lazare d'Orsenne); game opens **Thu 5 Mar 2026 / Tue 5 Mar 1833**.

---

## §0 Document Map & Ownership

### §0a File map (fixed)

```
docs/00_BRIEF.md                              original creative brief (exists, read it first)
docs/00_CANON.md                              THE CANON (single source of truth)
docs/01_vision/vision_and_pillars.md          pitch, pillars, tone, player fantasy, comparables
docs/02_lore/world_rules_and_lore.md          rifts, Hidden Study, spatial anchors, laws of time, Anachronist history
docs/03_characters/party.md                   playable party: bios, arcs, kits overview, bond arcs
docs/03_characters/historical_cast.md         every historical NPC: bio, in-game role, voice, scenes
docs/03_characters/anachronists.md            the cabal: each member's dossier, arc, boss tie-in
docs/04_scenario/prologue_and_act1.md         chapter-by-chapter scenario + key scripted dialogue
docs/04_scenario/act2.md
docs/04_scenario/act3.md
docs/04_scenario/act4_and_epilogue.md         Act IV (CH-14–CH-17): labyrinth, final battle, the Window, farewells, the Question
docs/04_scenario/epilogues.md                 the two playable epilogues CH-E1 (Seoul 2026) and CH-E2 (Paris 1834), ending rolls, codas
docs/04_scenario/dialogue_style_guide.md      text box format, voices, sample barks
docs/05_systems/combat_ensemble.md            ATB, commands, Harmony & Synergy skills, statuses, elements
docs/05_systems/skills_and_progression.md     full skill lists per character, Opus/sheet-music system, leveling
docs/05_systems/secrecy_and_trust.md          Secrecy Meter + Trust Network/bond + confession rules
docs/05_systems/salons_duels_and_economy.md   salon performances, piano duels (Thalberg), money, shops
docs/06_balance/formulas_and_curves.md        damage/heal/hit formulas, EXP & stat curves, tuning tables
docs/06_balance/bestiary.md                   every regular enemy with stats, by area
docs/06_balance/bosses.md                     every boss: stats, phases, AI scripts, layouts
docs/06_balance/items_and_equipment.md        weapons, armor, relics, consumables, key items, shops
docs/07_world/overworld_and_towns.md          overworld maps, districts, towns, interiors, NPCs
docs/07_world/dungeons.md                     all dungeons floor-by-floor, puzzles, encounters
docs/08_quests/side_and_bond_quests.md        side quests, bond questlines, optional content
docs/09_presentation/audio_and_music.md       soundtrack list, leitmotifs, SFX, SPC/5-channel spec, repertoire clearance
docs/09_presentation/art_and_ui.md            sprites, tiles, palettes, portraits, UI/menu spec
docs/10_appendix/historical_notes_and_liberties.md   research notes, every liberty taken and why
README.md                                     project index
```

### §0b Ownership

**Rule.** The canon owns every *shared fact*: any name, ID, date, age, location, join/leave point, chapter order, boss level/HP/weakness, formula, cap, threshold, price band, key item, leitmotif, repertoire entry, lore law or ending rule that two or more documents need. Leaf docs own *elaboration inside those facts*. Precedence: **canon > owner leaf doc > a leaf doc that only cites**. A leaf doc that needs a new or changed shared fact puts a **Canon Change Request** (CCR: what, why, which docs it touches) at the top of its own file, logs it in §2b, and does not use the change until the canon is amended.

| Kind of detail | Owner (elaborates, bounded by) | May reference, never redefine |
|---|---|---|
| Pitch, pillars, tone wording, comparables | vision_and_pillars (§1) | all |
| Lore exposition, in-world documents, reveal-schedule wording | world_rules_and_lore (§9 LAWs) | scenario, characters, quests |
| Party bios, voices, arcs, bond-quest beat outlines | party (§5) | systems, quests, scenario |
| Historical NPC bios, voices, scene lists | historical_cast (§7) | scenario, quests, world |
| Cabal dossiers and internal politics | anachronists (§8) | scenario, bosses, lore |
| Scene-by-scene beats, scripted dialogue, cutscenes | the four scenario act docs and epilogues.md (§3, §4) | quests, audio cue sheets |
| Text format, portrait tags, barks, voice samples | dialogue_style_guide (§16) | all writing docs |
| Battle rules detail, full status/element tables, Synergy effects | combat_ensemble (§10, §11) | skills, balance, bosses |
| Every skill (HRM), Opus Score (OPS), Étude (ETU), Study (STU), Tutti recipe (TUT) | skills_and_progression (§5, §11) | party, items, balance |
| Secrecy/Trust/Spotlight per-event values, Horizon event wording | secrecy_and_trust (§11e–f, LAW-23) | scenario, quests |
| Salon/duel minigame rules, shop pricing policy, income tables | salons_duels_and_economy (§11g, §14) | items, world |
| Formula derivations, per-level curve tables, the EXP table | formulas_and_curves (**must reproduce §10 exactly**) | skills_and_progression, bestiary, bosses, items |
| Regular enemies (ENM): names, stats, drops, steals | bestiary (§10e anchors) | dungeons, world |
| Boss stats beyond ID/Lv/HP/weakness, phases, AI, arenas | bosses (§13 binding) | scenario (battle beats only) |
| Every item (ITM), price, stat, shop stock | items_and_equipment (§14 bands and KEY list binding) | world, quests, economy |
| Overworld maps, towns, interiors, named townsfolk | overworld_and_towns (§12 LOC IDs) | quests |
| Dungeon layouts, puzzles, treasure, encounter tables | dungeons (§12 LOC IDs) | bestiary (names only) |
| Side and bond quest content, rewards (items named from items doc) | side_and_bond_quests (§0c reserved IDs) | scenario |
| Track list (MUS), SFX, SPC spec, clearance | audio_and_music (§15 LM/REP binding) | scenario cue notes |
| Sprites, tiles, palettes, portraits, UI | art_and_ui (§16a box spec binding) | all |
| Research notes, bibliography, liberties register | historical_notes_and_liberties (must list every Y in §2 and §7) | all |

### §0c ID conventions and reserved IDs

| Family | Format | Owner of new numbers |
|---|---|---|
| Chapters | CH-P, CH-01…CH-17, CH-E1, CH-E2 | canon only |
| Locations | LOC-S## Seoul 2026 · LOC-P## Paris 1833 · LOC-R## regional · LOC-E## Paris 1834 epilogue · LOC-W## overworld maps | canon |
| Characters | PC-## party · GST-## guest · NPC-## historical · FIC-## fictional non-cabal · ANA-## Anachronist | canon |
| Bosses / enemies | BOSS-## (canon) · ENM-### regular enemies (bestiary) | canon / bestiary |
| Items | KEY-## key items (canon) · ITM-### all other items (items doc) | canon / items |
| Systems | SYN-## Synergy · HRM-PC##-## Harmony skill · OPS-## Opus Score · REP-## Recital repertoire · ETU-## Alkan Étude · STU-## Delacroix Study · TUT-## Berlioz Tutti recipe | canon (SYN, REP) / skills doc (others) |
| Lore and text | LAW-## · R-## reconciliation · LM-## leitmotif · MUS-### track | canon (LAW, R, LM) / audio (MUS) |
| Quests | SQ-## side quest · BQ-PC##[a/b] bond quest | quests doc, except the reserved IDs below |

**Reserved quest IDs (cited by the canon; the quest doc must use these numbers and titles):**

| ID | Title | Window | Canon use |
|---|---|---|---|
| SQ-04 | Ink and Counter-Ink | CH-05–CH-09 | Secrecy −15 (§11e) |
| SQ-07 | Apprentice of Pleyel | CH-07–CH-14 | **Gate for YES** (LAW-23); Théo indentured to Pleyel; Aristide Farrenc named his *tuteur* by a *conseil de famille*, Louise his guardian in fact. Binding steps in LAW-23.1 |
| SQ-11 | The Jury | CH-14 | Horizon R2: Delacroix (no Academician, so no vote) brings Delaroche, the jury's swing vote, to see her canvases; in CH-E2 Delaroche speaks for her in session (BOSS-32 Favor +20) |
| SQ-12 | The Atelier | CH-14 | Horizon R4 (buy and restore a Montmartre studio, 5,000 F); restores LOC-E02 (which exists either way: fallback in §12) |
| SQ-13 | The Seine at Six Hours | CH-12–CH-14 | Horizon R5 |
| SQ-20 | The Salon Circuit | CH-14 | Tier-4 salons; Belgiojoso's vow (R-10); unlocks BOSS-35 |
| SQ-21 | Changes | CH-14 | Recruits Julien as PC-11 |
| SQ-22 | Before April | CH-E2 | The rue Transnonain reflection (LAW-19) |
| SQ-23 | The Last Anachronisms | CH-E2 | Destroys the cabal's remaining evidence, including the Engine's last oscillator (LAW-25) |
| BQ-PC02 | The Hours of Light (Lucile; 6 parts: Dawn, Morning, Noon, Afternoon, Dusk, Night) | CH-05–CH-14 | Romance spine. Parts 1–5 are optional; **part 6 (Night) is the scripted CH-14 Night of Stars and counts as the finale** |
| BQ-PC02b | A Harbour of Her Own (Étretat → Le Havre) | CH-14 | Unlocks BOSS-39; changes her Salon entry (KEY-40) |
| BQ-PC03 | Idée Fixe (Berlioz) | CH-03–CH-14 | — |
| BQ-PC04 | The Colours of Algiers (Delacroix) | CH-03–CH-09 | **Mandatory** by CH-09 |
| BQ-PC05 | The Railway Étude (Alkan) | CH-05–CH-14 | — |
| BQ-PC06 | Żal (Chopin) | CH-06–CH-09 | **Mandatory** by CH-09 |
| BQ-PC07 | Transcendence (Liszt) | CH-07–CH-14 | Climax BOSS-36 |
| BQ-PC08 | The Treasury (Farrenc) | CH-08–CH-14 | Horizon W5 if Lucile is present at the finale. Farrenc conceives her anthology of early keyboard music herself when Delorme threatens Pleyel's old-music archive; Min-jun recognises *Le Trésor des pianistes* (1861–72) and stays silent (LAW-16, LAW-18) |
| BQ-PC11 | A Tune of My Own (Julien) | CH-14 | Optional |

**Point of no return.** CH-15–CH-16 are one continuous night with no free roam, and CH-10–CH-11 take the party out of Paris. Every quest window above except the CH-E2 quests therefore closes at the end of CH-14 at the latest. At the Panthéon crypt door (end of CH-14) a prompt lists unfinished quests **by title only** and offers to turn back. The CH-E2 Atelier restoration task (LOC-E02 fallback) takes the next free SQ number from the quests doc.

---

## §1 Logline, Design Pillars, Tone Rules, Player Fantasy

**Logline.** In 1833 Paris, a Korean composition student who fell through a door beneath his Seoul conservatory must outplay a cabal of time-travellers who have stolen the future to rule the past and who will kill him before they let him go home, while the painter they sent to keep him there becomes the reason he must choose between two centuries.

### Design pillars

| # | Pillar | What it means in play | Test (a feature that fails it is cut) |
|---|---|---|---|
| P1 | **The Ensemble Is the Hero** | FF6-style: every party member has a defining chapter scene, a bond questline, a unique command and a voice in the final **Octave**. No stat sticks. | Could another character's command or scene do this job? If yes, redesign it. |
| P2 | **Gift, Not Theft** | Every villain, system and ending asks when carrying the future into the past is a gift and when it is a theft. The Anachronists pass the future off as their own; Min-jun names its makers and pays a price (Secrecy, history, Lucile's canvases). | Does it make the player weigh credit, consent or harm? |
| P3 | **Brilliance Has a Price** | Every future act (a Ravel recital, a van Gogh brushstroke, a modern word) is the strongest option and raises suspicion. The player always chooses between power and cover. | Does it make the player weigh showing off against hiding? |
| P4 | **Every Rung Is Personal** | The cabal's campaign climbs a visible ladder (§4c). Each rung is carried out by a named member with a motive and strikes at someone Min-jun loves. | Can you name who did it, why, and whom it hurt? |
| P5 | **Two Cities, One Heart** | Plague-scarred streets against candlelit salons; 1833 Paris against 2026 Seoul. Lucile's answer grows from the whole game, never a menu pick, and both epilogues are full playable chapters where the brief's final image lands. | Does it feed the contrast, the bonds or the Horizon? |

### Tone rules
1. **Melancholy with a pulse.** Every sad scene keeps something living in frame (a child laughing, a melody, a Berlioz joke). Every triumph keeps a cost in frame.
2. **One quiet scene before every set piece.** Each chapter places a candle, a piano or rain before its big battle.
3. **Intellectual, not academic.** People argue about art the way people argue about love. No lecture runs longer than 3 text boxes.
4. **Real people are people.** Historical figures are written from their letters and memoirs: witty, petty, generous, wrong. Never punchlines, never saints (§16).
5. **The supernatural is acoustic.** Rifts, Echoes and the Engine are expressed through sound, resonance and light. No wizards, demons or gods.
6. **No narrator.** Exposition is spoken by a character, written in an in-world document, or shown. On-screen captions give only place and date. **The only exception:** after each epilogue, an FF6-style **ending roll** gives one vignette per party member present in that branch, then up to **8 end cards** of at most 2 plain-text lines each (legacies and works, within the Lantern Rule; never a friend's death, except Min-jun's and Lucile's own on the Paris cards). The Keeper's Choice variants (LAW-24) are spoken by Min-jun in voice-over, in his own name. Seoul cards: Lucile's papers (Mar 2027); *Harold en Italie* (Sun 23 Nov 1834); Farrenc's professorship (1842); Théo Aubray, *facteur de pianos*, sails for Korea (1888); *Harmonies de l'ère perdue* published (2027). Paris cards: married, June 1834; *Nocturnes de Séoul* (1840); her Salon entry, hung *au ciel*; Théo sails for Korea (1888); Montmartre cemetery (1889 and 1891).
7. **History's people never learn what they could not know**, except through a documented in-fiction event (a confession, LAW-18's Lantern Rule).
8. **Violence has weight but no gore** (T rating). Human enemies are routed, subdued or arrested. Comedy lives in character (Berlioz's grandiosity, Liszt's vanity, Alkan's deadpan, Offenbach's cheek, Jae-won's samulnori showmanship, with gamer talk capped at one line per scene), never in grief scenes and never at the period's expense.

### Platform and localisation
**Target:** authentic SNES constraints as design discipline (256 × 224; 8 sprite palettes of 15 colours plus transparency; the SPC700 rules of §15a), shipping on **PC and Switch** on an accuracy-first engine. There is **no cartridge ROM budget**. **Master script in English**; the §16a limits are English limits. **Planned localisations: French and Korean.** French overflow uses the 4-line no-portrait box; Korean ships its own full font. The ≤ 400-syllable hangul subset (§16c) applies only to hangul inside the English script.

### Player fantasy
*"I am the only person in 1833 who has heard the future, and the most dangerous thing I own is my own memory."* The player astonishes Paris with music no one has heard, protects a secret that could get everyone they love killed, and earns the friendship of geniuses by helping them become themselves, not by handing them answers. In the end they choose which century is home, and so does the woman they love.

**Comparables:** FF6 (ensemble cast, magicite growth, the opera set piece, split parties, a world that opens late), FF5 (command depth, Blue-Magic collecting via Delacroix's Studies), Chrono Trigger (dual and triple techs, multiple endings), Persona (bonds that change the ending), Suikoden II (historical-political intrigue).

---

## §2 Reconciliations with the Brief

### §2a Reconciliation register

Every beat of the brief and of Addenda A-1, A-2 and A-3 is preserved. Problems are solved in fiction wherever possible. **Liberty = Y** means the item must appear in `historical_notes_and_liberties.md`. Blanket liberty **R-00:** all historical party members' adventuring, combat and close friendship with a fictional man, and every friendship among historical characters that is earlier or closer than the record (notably Delacroix–Chopin, documented from c. 1838), are invented (Y); private conversations with real people are invented (not separately flagged). Documented **first meetings** that fall after the game are kept: the canon stages around them (§16e) rather than bringing them forward.

| ID | Brief text | Canon decision | In-fiction justification | Liberty |
|---|---|---|---|---|
| R-01 | "Catacombs of Saint-Denis" | Name kept for **LOC-P01 Saint-Denis Galleries**: quarry galleries under the Faubourg Saint-Jacques running from the crypt traditionally linked to Saint Denis (under the old Carmel of Notre-Dame-des-Champs) south to the Barrière d'Enfer ossuary. Nothing lies under the town of Saint-Denis. | Quarrymen named the galleries after the crypt at their head. | Y (naming) |
| R-02 | "damp, cholera-ravaged Catacombs" | The *city* is reeling from the 1832 epidemic (~18,400 dead). The galleries hold lime pits from 1832 burials seeping down at the quarry mouths and are haunted by **Echoes** of the epidemic's grief (LAW-07). | Archon's 5 Mar 1833 strike of the Clefs woke resonance-shades of recent mass grief. | Y (supernatural) |
| R-03 | "militia patrols" | Armed **octroi agents** (*préposés de l'octroi*) and quarry inspectors (*Inspection des Carrières*) hunting wine-runners who use the quarries to dodge the toll wall, backed that night by a **National Guard picket** called out after a smuggler shot an agent, plus Archon's **Grey Hand** searching for "the arrival". All patrols are stealth hazards, never battles (§12 enemy rule). | Real smuggling practice. | N |
| R-04 | "roaming ghouls" | Ghouls = **Ossuary Echoes**, a bestiary family. Recordings, not souls. | LAW-07 | Y (fantasy) |
| R-05 | "Emerging into the Latin Quarter… shelter near the Conservatoire de Paris" | Two beats. He emerges at rue Saint-Jacques (Left Bank) in a rainstorm (CH-01), then crosses the river to the **Faubourg-Poissonnière quarter, rue Bergère** (Right Bank), where the real Conservatoire stands, and finds the tavern **Au Diapason Fêlé** (CH-02). | "Conservatoire" is the one name in Paris he knows how to find. | N |
| R-06 | Gaspard de la nuit at a low-tier salon | "Ondine" at **Salon Lavergne**, Sat 27 Apr 1833 (CH-03). | — | N |
| R-07 | Vane, "from 1988", takes note | Kept. Vane is a 1988 auctioneer who has catalogued Ravel autographs and recognises the piece. | §8 | N |
| R-08 | Act I climax: Vane frames Min-jun during a Marais street riot | **Wed 5 Jun 1833**: a banned anniversary march for the dead of the June 1832 rebellion becomes a riot on rue Saint-Antoine, provoked by Vane's mercenaries; a pamphlet in Min-jun's name is planted. Framing comes before the slower sabotage rungs because **Vane jumped the ladder without Archon's sanction**; Archon rebukes him for making Min-jun a hero (§4c rung 5). | Real republican agitation in 1833; the riot itself is invented. | Y |
| R-09 | "Louvre atelier" | The copyists' gallery and Salon Carré (LOC-P13), where licensed copyists, Lucile among them, work at easels. Artists' lodgings left the Louvre in 1806. | Copying was the Louvre's living atelier; women were admitted. | Y (minor) |
| R-10 | "A legendary dueling mechanic is introduced: Min-jun vs. Thalberg" (Act II) | The full **Piano Duel** debuts at the Thalberg duel, **Sat 7 Sep 1833** (CH-07). Thalberg (21) makes a **private, unannounced visit** as the Austrian Embassy's guest; Vane sponsors it to humiliate Min-jun. The embassy diarist Count Rudolf Apponyi agrees to leave the evening out of his journal, which is why history keeps no record. **Rossini (NPC-33), the embassy's guest of honour, judges the duel.** Princess Belgiojoso, an exile whom Vienna has just charged with treason and stripped of her fortune, is **not present**; when Liszt tells her about it (CH-14, SQ-20) she vows to host "a proper one" (the real duel, 31 Mar 1837). Thalberg already uses, privately, the "three-hand" device he will unveil in Paris in 1836 (record: c. 1835–36) (Y). Thalberg returns on two more unrecorded private visits, in **December 1833** (SQ-20) and **February 1834** (CH-E2), both as Belgiojoso's guest; his public Paris debut stays 1835–36. A three-Passage salon "cutting contest" with Henri Herz (CH-03) only previews the controls. | Thalberg's Viennese aristocratic ties make an embassy visit plausible. | Y |
| R-11 | Chopin "frail, melancholic, burdened" | Kept and balanced: also witty, elegant, a merciless mimic. His burden is Poland's fall (1831), exile and dread of public concerts. No disease mechanic; his illness is only foreshadowed. | His letters. | N |
| R-12 | Formulas hidden in artwork by a popular painter | **Mme Isaure Delorme** (ANA-04). Her seven commissioned panels hide equations that tune the Clefs (**tablature**, LAW-08). | The formulas are functional, not vanity. | N |
| R-13 | Synthetic alloys in a watchmaker's shop | **Maître Anselm Brücke** (ANA-05), rue de la Paix: nitinol springs, carbon filament. Alkan, a machine enthusiast, notices the metal (CH-07). | — | N |
| R-14 | "Sewers of Palais-Royal" | A real Right Bank sewer branch joined to the cellars, gambling-den tunnels and drains under the Palais-Royal; scale exaggerated. | The Palais-Royal really was riddled with cellars. | Y (minor) |
| R-15 | Julien (1950) passes off **late-20th-century** jazz | Julien transcribes, by ear, **Vane's 1988 Walkman and its five mixtapes** (KEY-15), powered by a crank dynamo Brücke lent him, wrecked in BOSS-11 (the party gets its own dynamo, KEY-28, only in CH-14). He passes off music he never heard in his own life. Scripts evoke the style (extended chords, modal vamps, quartal voicings); they never quote a real melody or name a real artist. | Internal fix. | N |
| R-16 | Confession arc: max bond with Chopin and Delacroix (Act II) | Their bond questlines BQ-PC06 and BQ-PC04 are mandatory and reach rank 10 by CH-09, where both confessions are scripted. | — | N |
| R-17 | Nohant in Act III | Sand withdraws to Nohant for the second half of Oct 1833 (CH-10), then returns to Paris and leaves for Italy with Musset on the real date, Thu 12 Dec 1833. She travels through Italy (Lyon and the Rhône; Marseille 18–20 Dec; Genoa, where she falls ill; Florence; Venice from January 1834, exact arrival date fixed by the appendix) for all of CH-E2 and appears only by letter. Her first CH-E2 letter is dated from Genoa. Under the §16e staging rule she never shares a scene, line or battle with Liszt, Delacroix or Chopin. | — | Y (minor) |
| R-18 | "Robert & Clara Schumann" | Always **Robert Schumann (23) and Clara Wieck (14)**: unmarried, not courting (that begins 1835), never framed romantically. In CH-11 Min-jun slips and calls her "Madame Schu— Mademoiselle Wieck": a scripted Secrecy slip (+5); Friedrich Wieck glares; no follow-up joke. | The brief's error becomes the hero's error. | Y (their Düsseldorf presence, Nov 1833; Robert travels while convalescing after his Oct crisis, incognito as "Florestan", R-56) |
| R-19 | Mendelssohn on the Rhine | Accurate: municipal music director at Düsseldorf from autumn 1833. He hosts a private November academy (fictional). | — | Y (minor: the academy) |
| R-20 | Czerny as a visitor | In Düsseldorf in Nov 1833 on a publishing errand and to hear his old pupil Liszt. His real western trip was 1837. | — | Y |
| R-21 | Chopin on the Rhine (Act III tour) | Chopin's real Rhineland trip was May 1834 (Aachen festival, then Düsseldorf). Moved to Nov 1833: he stays in Paris through CH-10 and joins the tour at Liège. Liszt, Farrenc and Alkan travelling with him is also invented, as is **Liszt's October 1833 stay at La Châtre** (benefit concert, CH-10). The *Concordia* is the real PRDG paddle steamer (1827, Cologne–Mainz); her battle is fictional. | — | Y |
| R-22 | César Franck in the cast | **Age 10, in Liège** with his driving father Nicolas-Joseph (CH-11). The family moves to Paris only in 1835. He never appears in Paris. | Liège lies on the Paris–Brussels–Aachen road. | N |
| R-23 | Horace Vernet in the cast | Director of the Villa Medici, in Rome. He appears **only in CH-13** on a short Paris leave (ministry business) as the gala's guest of honour. | — | Y |
| R-24 | Ingres, Delaroche, Chassériau, Corot | Ingres and his pupil Chassériau (13; 14 from 20 Sep) in Paris; Delaroche finishing *The Execution of Lady Jane Grey*; Corot painting at Fontainebleau (Salon 1833 second-class medal). | Accurate. | N |
| R-25 | Offenbach in the cast | Arrived Nov 1833; admitted to the Conservatoire cello class Sat 30 Nov 1833. Cameo in CH-12, then a 14-year-old substitute cellist in the Opéra pit (CH-13). | — | Y (minor: the pit) |
| R-26 | "Abandoned Monastery of Val-de-Grâce" | Val-de-Grâce is a **working military hospital**. Dungeon 3 is the **disused old abbey wing and the quarries beneath**; patients and surgeons are present above ground. Archon is a benefactor of the hospital (his cover). | Locals call the sealed cloister annex "the abandoned monastery". | Y (minor) |
| R-27 | Archon "an immortal genius" | Not literally immortal: he slows his ageing through **Stasis** (LAW-11). The seal would make it permanent at the price of never leaving Paris. His fate is the ironic eternity he wanted: one endless second inside the collapsed Stilled Hour (LAW-13). | — | N |
| R-28 | Archon's political empire of "modern military tactics and industrial patents… corrupt officials" | Arms and machine patents filed through front men (rifled-barrel tooling, puddling refinements, semaphore codes), counter-insurgency doctrine sold to the War Ministry and National Guard. Prefect of Police **Gisquet** is compromised, not evil: his real 1831 musket-purchase controversy is Archon's leverage. Archon is an **industrialist**, never a banker (§16e). Louis-Philippe is never complicit. | — | Y (Gisquet's dealings) |
| R-29 | Grand Concert Battle at the Opéra; "dual-piano concerto" | **Salle Le Peletier**, a royal benefit gala for cholera orphans sponsored by Archon, **Fri 6 Dec 1833**. The piece is **Min-jun's first original work, the *Concerto for Two Pianos "Lost Era"*** (REP-27), Berlioz conducting: his interpreter-to-composer turn. | Benefit galas were common Opéra practice. Berlioz conducting is itself a liberty (he takes up the baton for his own concerts in 1835): Archon insists on him for spectacle, Habeneck sulks, and on 22 Dec Girard conducts, as the record says. | Y (event fictional; Berlioz on the podium) |
| R-30 | "Subterranean Panthéon" | The Panthéon crypt plus the real quarries under the Montagne Sainte-Geneviève, distorted by time. The party enters by David d'Angers' pediment scaffolding (1831–37). | — | Y (fantasy) |
| R-31 | "forgotten spatial anchors beneath Paris" | The seven **Clefs** (LAW-02). | — | N |
| R-32 | Synergy climax of Min-jun, Chopin, Liszt, Berlioz, Farrenc, Delacroix | The **Octave of the Lost Era**: the brief's six plus Lucile (A-2) and Alkan. All six named voices are preserved. | §11b | N |
| R-33 | "corrupted, synthesized piano engine that warps physical space" | **Le Clavier des Âges** (the Engine), built by Brücke with Clef-shard oscillators (LAW-09); BOSS-28. | — | N |
| R-34 | Ending: Min-jun returns to 2026 | A-3 branch: CH-17 question → CH-E1 (Seoul) or CH-E2 (Paris). | §9 LAW-23–26 | N |
| R-35 | "bid an emotional farewell to his mentors" | Both branches contain the farewell, played before the Question during the Window (CH-17). In Paris it becomes an inverted goodbye: she asks him to stay, he agrees, and he throws a recorded message to his family through the closing Window (LAW-25). | — | N |
| R-36 | Portrait "in the conservatory library… old manuscript collection" | The **Jeong-dong Collection**, box **JD-1888-07** ("Caisse Aubray"), recovered in the 2019 annex works and catalogued Nov 2026 (LAW-26). | — | N |
| R-37 | "Seoul conservatory" | Fictional **Hanseong Conservatory of Music**, Jeong-dong, Jung-gu, built over the foundations of the old French legation. No real school is depicted. | Ties the Door to real Franco-Korean history (treaty 4 Jun 1886). | Y (fictional institution on a fictionalised site) |
| R-38 | "5-channel sound synthesis" | SPC700 has 8 voices: **5 music + 3 SFX** as the house rule, with documented exceptions (§15a). | — | N |
| R-39 | "expressive 32x32 character sprites" | Characters are authored in a **32×32 cell** (figure about 20×30 px) on a **16×16 tile grid**, for field and battle. | Larger than FF6, as the brief asks. | N |
| R-40 | "buffs/debriefs" typo | Read as **buffs/debuffs** (already corrected in 00_BRIEF.md). | — | N |
| R-41 | Anachronists "entered through similar anomalies throughout history" | Every rift reaches the same Paris Clef network through future-side fragments of Clef stone (LAW-02–04). | — | N |
| R-42 | Secrecy "raises suspicion among the Anachronist adversaries" | The cabal already knows who he is; the Secrecy Meter measures how much of the future he leaks into the public record, which the cabal reads as risk and answers by escalating (LAW-17). | — | N |
| R-43 | Confession only after maxing a bond | One documented exception, the **Early Truth**: Lucile alone can be told at rank 7 during CH-06–CH-08 (§11f). | Systems exception required by A-2. | N |
| R-44 | Chopin and Liszt "met" in Act II | They already knew each other. Min-jun *sees* them play Onslow's F-minor four-hand sonata at Harriet Smithson's benefit, Tue 2 Apr 1833 (CH-03), and *meets* them in CH-05. | — | N |
| R-45 | "Chopin's Pleyel grand… high-stakes concert" | A charity concert at Salle Pleyel for cholera orphans, **Sat 21 Sep 1833**, where Min-jun is to perform on Chopin's own Pleyel. | — | Y (invented date) |
| R-46 | Chopin's "emotional block" (bond example) | He cannot find the ending of the Ballade in G minor (begun 1831). BQ-PC06 unlocks the door but does not finish the piece; history keeps its 1835 date. | — | N |
| R-47 | Delacroix's "revolutionary canvas" (bond example) | *Women of Algiers in Their Apartment*, finished for the Salon of 1834 (BQ-PC04). | — | N |
| R-48 | Women and art institutions | Women could exhibit at the Salon and copy at the Louvre, never enter the École des Beaux-Arts. Farrenc is not yet a professor (1842). | Accurate. | N |
| R-49 | A-1: the portal fear needs concrete stakes | **Brücke (ANA-05) is from 2049.** He remembers a history in which Min-jun came home alone and told the world (the **Kang Disclosure**), which created the Chronometric Survey that hunted travellers (LAW-14). Screen time for 2049 material is capped (LAW-14). | — | N |
| R-50 | A-2: heroine b. 1810, 23 in 1833, younger friend of George Sand | **Lucile Aubray**, b. Fri 9 Feb 1810, Paris: 23 through the main game and CH-E1; turns 24 on Sun 9 Feb 1834 during CH-E2 (the morning she proposes). Met Sand in Jan 1831 painting snuffboxes at Maison Corbel (§5e). | Sand really painted snuffboxes and fans for money in 1831. | N (original character) |
| R-51 | A-2: her Impressionism is "a dangerous change to history" | Made thematic: her canvases stir 1833 and are absorbed by the ossia (LAW-15, LAW-21). Min-jun must reckon with having done what he condemns (LAW-20). | — | N |
| R-52 | A-3: her answer, and the portrait in both branches | Hidden state plus final words decide (LAW-23); the portrait lands in both branches (LAW-26). | — | N |
| R-53 | Paganini and the 22 Dec 1833 concert | Paganini attends Berlioz's 22 Dec 1833 concert and praises him; in Jan 1834 he asks for a viola work (→ *Harold en Italie*). His famous kneeling to Berlioz (16 Dec 1838) is **not** depicted. | — | N |
| R-54 | Act hour bands (I 1–8, II 9–18, III 19–26, IV 27–30+) | Kept within ±1.25 h (§4a). | — | N |
| R-55 | In-game prices | 1833 wages (~2–3 F a day) make JRPG prices absurd. Prices are stylised (§14), with real anchors for flavour. The **₩200/F** carry-over rate is a balance abstraction (a real Louis-Philippe 5 F or 20 F piece is worth far more in 2026): in fiction the numismatist buys his bag of copper sous by weight, and Min-jun keeps his few silver and gold pieces as keepsakes. | — | Y |
| R-56 | Visitors on the Rhine (CH-11) | **Robert Schumann appears in CH-11 only as "Florestan"**, a Leipzig critic travelling with Wieck (his name tab reads "Florestan"). He is never introduced by name to Mendelssohn, Chopin or Liszt, so the documented first meetings (Mendelssohn and Chopin 1835, Liszt 1840) stand. The Rhine encounters of Clara with Liszt and with Czerny (record: Vienna, 1837–38) are invented. Sand's documented first meetings with Liszt (autumn 1834), Delacroix (1834) and Chopin (1836) are kept by the §16e staging rule. | The "Madame Schu—" slip lands better because no one present knows the name. | Y |
| R-57 | Chopin in the party, summer 1833 | Chopin really spent August 1833 at Le Côteau (Azay-sur-Cher, Touraine) with Franchomme and the Forest family; their *Grand Duo* (published July 1833) was played in Tours in September. In the game he leaves on Sun 11 Aug and is back for the Sat 7 Sep duel, then stays through CH-08: a compression of his Touraine stay and the Tours concert. The appendix fixes the exact dates from the correspondence (his letter of 18 Sep 1833). | — | Y |
| R-58 | Farrenc's repertoire | Farrenc's *Air russe varié*, Op. 17 (composed 1835, published 1836), is heard as sketches in 1833–34. | — | Y (minor) |
| R-59 | The E = mc² copy (CH-06) | Living artists' works hung in the Musée du Luxembourg, not the Louvre. The formula is spotted in Lucile's state-commissioned copy, for a provincial church, of Delorme's *Vow of Anne of Austria*, made from Delorme's modello deposited at the Louvre for copyists. | Copying for provincial churches was common state work. | Y (minor: the modello at the Louvre) |

### §2b Canon change log

Proposed canon changes are logged here (date, requesting doc, what, why, docs touched, decision). The canon is amended only by the Lead Designer; until then the CCR is not used.

| Date | Version | Requested by | Change | Decision |
|---|---|---|---|---|
| 2026-10-06 | 1.0 | Lead Designer | §0a: added docs/04_scenario/epilogues.md (CH-E1/CH-E2) split out of act4_and_epilogue.md (now CH-14–CH-17) | Adopted |
| 2026-10-06 | 1.0 | Design panel (Historical Fact-Checker; Consistency & Math Auditor; Brief Compliance Reviewer) | Adoption review: solstice, calendar link, Sand staging rule, liberties R-56–R-59, balance anchors, branch logic, UI and presentation specs | Adopted as v1.0 |

---

## §3 Master Timeline

### §3a Real historical anchors (1830–1834)

| Date | Event | Game use |
|---|---|---|
| 27–29 Jul 1830 | July Revolution; Louis-Philippe King of the French (9 Aug) | Julien arrives 28 Jul 1830 (a Resonance Date) |
| 5 Dec 1830 | *Symphonie fantastique* premiere | Berlioz's Tutti recipes |
| 9 Sep 1831 | Vicariate Apostolic of Korea created in Rome | The one thread linking "Corée" to Paris (Missions Étrangères, rue du Bac) |
| Autumn 1831 | Chopin arrives in Paris | Backstory |
| Jan 1831 | Aurore Dudevant (Sand) arrives in Paris, paints snuffboxes and fans for money | How Sand met Lucile |
| 26 Feb 1832 | Chopin's Paris debut, Salle Pleyel | Backstory |
| Feb–Apr 1832 | Clara Wieck visits Paris with her father; leaves because of the cholera | Clara remembers Paris (CH-11) |
| Late Mar–autumn 1832 | Cholera; ~18,400 dead in Paris | Lucile's father dies 14 Apr 1832; Théo left weak |
| Apr 1832 | Liszt hears Paganini | Liszt's arc; BOSS-36 |
| Jan–Jul 1832 | Delacroix in Morocco | Source of *Women of Algiers* (BQ-PC04) |
| 5–6 Jun 1832 | June Rebellion (Saint-Merry barricades) | The 5 Jun 1833 anniversary march (CH-04) |
| 1831–1833 | Gisquet's musket-purchase affair | Archon's leverage over the Prefect |
| Aug 1832–Feb 1833 | Daumier imprisoned at Sainte-Pélagie | Daumier, just released, sketches the riot (CH-04) |
| Nov 1832 / 9 Dec 1832 | Berlioz back from Rome; *Fantastique* + *Lélio* concert, Harriet Smithson present | Backstory |
| Late 1832–early 1833 | Liszt meets Marie d'Agoult | CH-05 |
| 1 Mar 1833 | Salon of 1833 opens (Corot's medal) | Ambient |
| 16 Mar 1833 | Harriet Smithson breaks her leg | CH-02 gossip |
| Tue 2 Apr 1833 | Smithson benefit, Théâtre-Italien: Chopin and Liszt play Onslow's F-minor four-hand sonata | CH-03 set piece |
| Jun 1833 | Chopin moves from 4 Cité Bergère to 5 rue de la Chaussée-d'Antin; Op. 10 published that summer | LOC-P11 |
| Sat 22 Jun 1833 | Rambuteau becomes Prefect of the Seine | CH-05 ambient |
| Summer 1833 | Sand's *Lélia*; affair with Musset begins | CH-06+ |
| Sun 28 Jul 1833 | Napoleon's statue restored to the Vendôme column | CH-06 crowd event |
| Aug–Sep 1833 | Chopin at Le Côteau (Azay-sur-Cher, Touraine) with Franchomme and the Forests; their *Grand Duo* played in Tours in September | Chopin away 11 Aug–7 Sep (R-57) |
| 1833 | Liszt's piano transcription of the *Fantastique*; Delacroix's Salon du Roi commission (Palais Bourbon) | CH-05, CH-11 |
| Thu 3 Oct 1833 | Berlioz marries Harriet at the British Embassy; Liszt a witness | CH-09 |
| Oct 1833 | Mendelssohn begins as Düsseldorf music director; Schumann's crisis (17–18 Oct) | CH-11 |
| Nov 1833 | Offenbach arrives; admitted to the cello class Sat 30 Nov | CH-12, CH-13 |
| Sun 24 Nov 1833 | Berlioz's benefit at the Théâtre-Italien; the musicians walk out at midnight | CH-12 opening quiet scene |
| Thu 12 Dec 1833 | Sand and Musset leave for Italy | CH-14 farewell letter |
| Sun 15 Dec 1833 | Hiller's concert: Hiller, Chopin and Liszt play Bach's concerto for three keyboards | CH-14 quiet scene |
| 00:43, Sun 22 Dec 1833 | Winter solstice (00:33 UT = 00:43 Paris mean time; verified against Meeus and an ephemeris; ±2 min tolerated). Paris sunrise that morning: 07:51 | The seal (LAW-10); the Window (LAW-13) |
| Sun 22 Dec 1833 | Berlioz concert at the Conservatoire hall, Narcisse Girard conducting; Paganini attends (Conservatoire-hall concerts were normally Sunday afternoons; the appendix confirms the start time) | CH-E2 opening scene (a Sunday-afternoon concert) |
| Jan 1834 | Paganini asks Berlioz for a viola work | CH-E2 (KEY-37) |
| Sat 1 Mar 1834 | Salon of 1834 opens (*Women of Algiers*, *Lady Jane Grey*, Ingres's *Saint Symphorian*) | CH-E2 climax |
| Apr 1834 | Schumann's *Neue Zeitschrift für Musik* begins | CH-E2 letter |
| 13–14 Apr 1834 | Insurrection; rue Transnonain massacre | After the game; only SQ-22 (text and a still, LAW-19) |
| Autumn 1834; late 1836 | Sand meets Liszt (through Musset) and Delacroix (the Buloz portrait) in 1834; meets Chopin in late 1836 | After the game; kept as bar-lines (§16e staging rule); "G.S., déc. 1834" on the portrait's reverse (LAW-26) |
| Sun 23 Nov 1834 | *Harold en Italie* premiere | Seoul end card (§1 Tone Rule 6) |
| 1835–1839 | Thalberg's Paris debut; the real duel (31 Mar 1837); first Paris railway (1837); daguerreotype (1839) | Foreshadowing only |

### §3b In-game calendar

| Chapter | In-game dates | Notes |
|---|---|---|
| CH-P | Thu 5 Mar 2026, 22:10–23:40 KST | Min-jun crosses at 23:40 KST |
| CH-01 | Tue 5 Mar 1833, 14:49 arrival → dawn Wed 6 Mar | Passage Swoon until ~18:45; emerges at rue Saint-Jacques ~23:00 in rain |
| CH-02 | 6–20 Mar 1833 | Tavern weeks |
| CH-03 | 26 Mar – 30 Apr 1833 | Smithson benefit Tue 2 Apr; Delacroix turns 35 Fri 26 Apr; Lavergne salon Sat 27 Apr; Vane recruits Lucile Sun 28 Apr |
| CH-04 | 1 May – 6 Jun 1833 | Meets Lucile Thu 9 May; riot Wed 5 Jun |
| CH-05 | 15 Jun – 10 Jul 1833 | Paris opens; Rambuteau 22 Jun |
| CH-06 | 11 Jul – 10 Aug 1833 | Vendôme Sun 28 Jul; Lucile's first canvas Fri 2 Aug; Min-jun turns 23 Fri 9 Aug |
| CH-07 | 15 Aug – 14 Sep 1833 | Chopin in Touraine Sun 11 Aug – Sat 7 Sep (R-57); duel night Sat 7 Sep |
| CH-08 | 15–21 Sep 1833 | Charity concert Sat 21 Sep |
| CH-09 | 22 Sep – 4 Oct 1833 | Archon orders Lucile removed Mon 30 Sep (offscreen; Vane refuses and records it in his ledger, §8d); wedding Thu 3 Oct; abduction night 3–4 Oct |
| CH-10 | 12–28 Oct 1833 | Liszt turns 22 Tue 22 Oct |
| CH-11 | 1–24 Nov 1833 | Chopin joins at Liège; Théo seized Thu 14 Nov; the panel sold and shipped Mon 18 Nov; *Concordia* from Cologne Tue 19 Nov; the Lorelei and Mainz Wed 20 Nov; Strasbourg (Sand's letter) Thu 21 Nov |
| CH-12 | Sun 24 Nov – Sun 1 Dec 1833 | Return on the Théâtre-Italien night; infiltration night Tue 26 Nov; Alkan turns 20 Sat 30 Nov |
| CH-13 | Fri 6 Dec 1833 | Opéra gala |
| CH-14 | 7–20 Dec 1833 | Vane Mon 9 Dec; Berlioz turns 30 Wed 11 Dec; Sand leaves Thu 12 Dec; Hiller's concert Sun 15 Dec; Night of Stars Wed 18 Dec |
| CH-15 | Sat 21 Dec 1833, 19:00 → 23:50 | Solstice night |
| CH-16 | Sat 21 Dec 23:50 → Sun 22 Dec 07:30 | BOSS-26 from 23:50; the seal begins at the solstice instant (**00:43**); the chord must hold 7 h 08 min, until sunrise at 07:51 |
| CH-17 | Sun 22 Dec 1833, 07:51–08:03 (Paris sunrise) | = Tue 22 Dec 2026, 16:41–16:53 KST |
| CH-E1 | Tue 22 Dec 2026 16:52 KST → Fri 1 Jan 2027 00:00 | Seoul epilogue; ends on the Bosingak bell. (Dongji 2026 falls on 22 Dec, 05:50 KST: flavour.) |
| CH-E2 | Sun 22 Dec 1833 (afternoon) → Sat 1 Mar 1834; coda Tue 22 Dec 2026 | Paris epilogue; Lucile turns 24 Sun 9 Feb 1834 (proposal); jury session Sat 15 Feb; Salon opening and Chopin's 24th birthday Sat 1 Mar; coda in Seoul |

**Game start:** Thu 5 Mar 2026 (Seoul) / Tue 5 Mar 1833 (Paris). **Main-game end:** Sun 22 Dec 1833, 08:03. **Final dates:** 1 Jan 2027 00:00 (Seoul branch) or 1 Mar 1834 + 22 Dec 2026 coda (Paris branch). No canon crossing or stay spans a 29 February (LAW-06).

### §3c Anachronist arrivals in the past

| ID | Left the future | Arrived in Paris | Far end (LAW-03) | What rang the network (LAW-04) |
|---|---|---|---|---|
| ANA-04 Delorme | 31 Mar 1934, Paris Catacombs | 31 Mar 1814 | Clef V in situ (120 y) | Allied armies enter Paris: **the first traveller** |
| ANA-01 Archon | 21 Jun 2012, Seoul (the Door) | 21 Jun 1819 | Seoul Door (193 y) | Delorme's first deliberate striking of the Clefs |
| ANA-06 Sœur Marthe | 11 Nov 1918, Val-de-Grâce vaults (Armistice night) | 11 Nov 1822 | Clef II in situ (96 y) | One of Delorme's experimental strikes |
| ANA-02 Vane | 19 Nov 1988, London (Mayfair saleroom) | 19 Nov 1827 | London Stone (161 y) | Rue Saint-Denis election riots |
| ANA-03 Julien | 28 Jul 1950, Paris Catacombs | 28 Jul 1830 | Clef V in situ (120 y) | July Revolution |
| ANA-05 Brücke | 2 Nov 2049, Seoul (Survey-tuned Door) | 2 Nov 1831 | Seoul Door, re-tuned (218 y) | None needed; the Survey forced it |
| PC-01 Min-jun | 5 Mar 2026 23:40 KST, Seoul (the Door) | 5 Mar 1833 14:49 | Seoul Door (193 y) | **Archon's failed seal test** (LAW-04) |

**Cabal chronology:** binding rings first forged by Delorme for Archon, 21 Jun 1820; the **Pact of the Hour** sworn by Archon, Delorme and Marthe, 21 Jun 1826; Vane joins Jan 1828; Julien 1830 (never takes a ring); Brücke Jan 1832; the Engine's first oscillator tuned to Archon, 1 Jan 1833.

### §3d The 2026 Seoul timeline

| Date (KST) | Event |
|---|---|
| 1886–1906 | Treaty of 4 Jun 1886; Commissioner Collin de Plancy arrives 1888 with Théo Aubray and the crate; legation building completed 1896, Door installed in its music-room cellar; legation becomes a consulate general in 1906 and the cellar is bricked up behind a counterweighted bookcase (LAW-22) |
| 1962 | Hanseong Conservatory builds its annex over the legation foundations |
| 21 Jun 2012 | Visiting Prof. Lazare Morvan (Archon) vanishes from the annex: campus legend of "the professor in the basement" |
| 2019 | Annex foundation works, funded by the d'Orsenne Foundation under the open Charge of Archon's Testament (KEY-35), recover the **Jeong-dong Collection** (legation storeroom crates). The Hidden Study's entrance stays shut and is missed, but the works leave a hairline crack behind Room B-07's storage closet. |
| Tue 3 Mar 2026 | Spring semester begins (Mon 2 Mar is the Samiljeol substitute holiday). Min-jun starts his **3rd year** (entered Mar 2022; on leave for military service Apr 2023 – Oct 2024; resumed Mar 2025) |
| Thu 5 Mar 2026 | 22:10 Min-jun practises *Clair de lune* in Annex Room B-07, hears a hum through the closet crack, finds the study; 23:40 crosses |
| Fri 6 Mar 2026 | Reported missing by his sister Seo-yeon; campus search |
| Mar–Dec 2026 | Posters, vigil. Seo-yeon, now a first-year violinist at Hanseong, takes his practice-room slot "so it stays warm". |
| Sep–Nov 2026 | Prof. Yoon Mi-rae catalogues the collection. Box **JD-1888-07** ("Caisse Aubray") holds Théo's papers, an open letter (text per branch) and a sealed packet under a donor embargo (contents per branch: KEY-36, LAW-26). Yoon reads the open letter in November. |
| Tue 22 Dec 2026, 16:41 | The Window opens (Dongji afternoon, snow). **Seoul branch:** 16:52 Min-jun and Lucile cross, awake (a held Window costs no Swoon, LAW-05), and climb out through Room B-07's closet into the snow; 16:53 Brücke dives through as the Window collapses, swoons on the study floor until ~19:50, and is gone before anyone comes back. **Paris branch:** Min-jun's phone lands on the study floor at 16:52 (08:02 Paris), a minute before the Window closes. |
| Thu 31 Dec 2026 | Seoul branch: New Year's Eve concert (the *Harmonies* premiere); Brücke's attack, the clock-tower climb and the duel in the Hidden Study (BOSS-30); 23:00, the embargo hour, Min-jun opens the packet (the brief's image); midnight bell at Bosingak |
| Tue 22 Dec 2026 (Paris branch coda) | Seo-yeon, practising in Room B-07, hears the hum, finds the phone and plays the video; ~17:10 Prof. Yoon calls her; the packet labelled in hangul to Seo-yeon is opened |

---
## §4 Chapter Table

Critical path (CP) = **34.0 h** to the end of either epilogue. Completionist ≈ **56 h** (CP + 22.0 h optional: the Opt column sums to 19.5 h, plus 2.5 h of post-game superbosses and collection). Seeing the other epilogue through Reverie (LAW-23) adds ≈ 4 h (≈ 60 h total). Party abbreviations: MJ Min-jun, LU Lucile, BE Berlioz, DE Delacroix, AL Alkan, CH Chopin, LI Liszt, FA Farrenc, SY Seo-yeon, JW Jae-won, JU Julien; (g) = guest. Levels are the expected range; §10e gives the anchor average.

### §4a Structure

| ID | Title | Act | CP hours | Opt +h | Primary LOCs | Party available | Dungeon | Bosses | Lv | Systems introduced |
|---|---|---|---|---|---|---|---|---|---|---|
| CH-P | The Door Beneath Jeong-dong | Prologue | 0.00–0.50 | 0 | S01, S02 | MJ | — | — | 1 | Movement, examine, Lectern save, piano-input puzzle |
| CH-01 | The Saint-Denis Galleries | I | 0.50–1.50 | 0.25 | P01, P02 | MJ + Mathurin (GST-01) | P01 | BOSS-01 | 1–3 | ATB battle; Fight / Recital / Item; patrol stealth (sight cones); Echo enemies; Passage Swoon |
| CH-02 | The Out-of-Tune Upright | I | 1.50–2.75 | 0.50 | P02, P03, P04 | MJ; BE joins at end | Tavern cellars (mini) | BOSS-02 | 3–5 | Francs, shops, inns; tavern salon (T1); **Secrecy Meter**; Bite Your Tongue |
| CH-03 | Gaspard at the Salon | I | 2.75–5.00 | 1.00 | P03, P05, P06, P09, P22 | MJ, BE, DE (joins); AL (g) | Conservatoire undercroft (mini) | BOSS-03, BOSS-04 | 5–8 | Party of 3, rows, **Trust Network**, bond quests (BQ-PC03, BQ-PC04), Canvas, duel controls preview |
| CH-04 | The Barricades of the Marais | I | 5.00–7.50 | 1.00 | P07, P20, P21, P08, P36, P25, P32 | MJ, BE, DE (forced); AL joins at end | P08 | BOSS-05 | 8–11 | Multi-wave battle, **Crescendo Gauge**, first Synergy (SYN-08), Onlookers & Heat, Tacet, Conduct, Étude |
| CH-05 | The Grand Boulevards | II | 7.50–9.50 | 1.25 | P10, P11, P12, P14, P19, P22 | MJ, BE, DE, AL; LU joins | Passage de l'Opéra Echo nest (mini) | BOSS-06 | 11–13 | **Fiacre**, party of 4 + reserve, **Light States & Plein Air**, Lucile's BQ-PC02, **Opus Scores**, Renown |
| CH-06 | Impressions | II | 9.50–11.50 | 1.25 | P13, P06, P24, P20 | + CH joins | P13 Louvre | BOSS-07 | 13–15 | Rubato; lesson choices (hidden Horizon); **Early Truth** window; Watchers; Score transcription |
| CH-07 | The Duel at the Hôtel d'Apponyi | II | 11.50–13.75 | 1.25 | P15, P18, P12, P14, P21, P37 | CH away in Touraine until the duel (R-57); + LI joins | P18 Clockwork Undercroft | BOSS-08 (duel), BOSS-09 | 15–17 | **Piano Duel**, Transcend, Pleyel Voicing, Sketch/Studies; SQ-07 opens |
| CH-08 | The Sewers of Palais-Royal | II | 13.75–15.75 | 1.00 | P16, P17, P12, P19 | + FA joins (all 8) | P17 | BOSS-10, BOSS-11 | 17–20 | **Seine barge**, sluice puzzles, Counterpoint, in-battle Swap, Unwritten status |
| CH-09 | Confessions | II | 15.75–17.75 | 0.50 | P11, P06, P23, P34, P31, P22 | all 8 → three-thread split; LU leaves at dawn | P31 Bercy | BOSS-12 | 20–22 | **Confession** events, **split control** (3 threads), Cadenza, Lucile **Fracture** |
| CH-10 | Nohant | III | 17.75–19.75 | 1.25 | W02, R01, R03, R04, R05 | MJ, LI, FA, AL; LU (Fractured); Sand (g, Nohant only), Corot (g, Fontainebleau only). DE stays in Paris (Salon du Roi commission); CH stays in Paris (lessons, Op. 10) | R05 Vallée Noire | BOSS-13 | 22–24 | **Diligence**, France overworld, guests, Pointillé, Mending, **Window Talks** |
| CH-11 | The Rhine | III | 19.75–21.50 | 1.00 | R06, R13, R07, R14, R08, R09, R10; P20, P37 | MJ, LI, FA, AL; CH joins at Liège; Clara, Mendelssohn, Czerny, "Florestan" (Schumann) (g); LU solo interlude | R08 *Concordia* | BOSS-14 | 24–27 | Steamboat, guest rotation, Czerny drills, passports |
| CH-12 | Val-de-Grâce | III | 21.50–23.75 | 0.75 | P26, P37, P28 | LU solo → LU, MJ, BE, DE, LI, FA, AL; Théo (escort) | P26 | BOSS-15, BOSS-16 | 27–30 | Lucile stealth (Shift the Hour as light puzzle), survival battle, Archon's Revelation |
| CH-13 | The Grand Concert | III | 23.75–25.75 | 0.50 | P27 | Stage MJ, LI (BE conducting); Rafters DE, LU, AL; Corridors CH, FA, Offenbach (g) | P27 | BOSS-17, BOSS-18, BOSS-19 | 30–33 | **Simultaneous three-front battle**, Rapture meter, MEPHISTO, Min-jun's own pieces (Heat 0) |
| CH-14 | The Night of Stars | IV | 25.75–27.25 | 4.50 | P34, P14, P28, P38, all | all 8; Marthe (g); JU (PC-11, optional) | P34 Hôtel de Vane; optional dungeons | BOSS-20 (duel), BOSS-21 | 33–35 (opt to 42) | **Dirigible**, Impasto, Window Talk 3 (mandatory), phone recharge and camera, all optional content; point-of-no-return prompt (§0c) |
| CH-15 | The Chrono-Labyrinth | IV | 27.25–29.75 | 0.50 | P28, P29 | three parties (3 / 3 / 2, or 3 with JU; MJ always in Party 2), then merged 4 | P29 | BOSS-22, 23, 24, 25 | 35–39 | **Three-party switching**, Clef detuning, Amalgam zones |
| CH-16 | The Stilled Hour | IV | 29.75–30.75 | 0 | P30 | 4 → all 8 (Octave formation) | P30 | BOSS-26, 27, 28 | 39–41 | **Octave**; Eve-of-the-Window save |
| CH-17 | The Fleeting Window | IV | 30.75–31.00 | 0 | P30 | all | — | — | — | Window Clock (12:00, §11i), farewells and keepsakes, the Pact, the Question |
| CH-E1 | Seoul, 2026 | Epilogue A (YES) | 31.00–34.00 | 3.00 | W03, S01–S15 | MJ, LU, SY (PC-09), JW (PC-10) + Remembrances | S08, S10 (approach), S02 (duel); opt S09 | BOSS-29, 30; opt BOSS-31 | 41–45 (opt to 50) | Phone menu, subway fast travel, won (₩), Spotlight Meter, busking ladder, Hanmadi, noraebang, Remembrance summons, LUMIÈRE (definitions §4f) |
| CH-E2 | Paris, 1834 | Epilogue B (NO) | 31.00–34.00 | 3.00 | E01–E05, P35, P24, R02, P06, P39, P04 | all 8; JU (if recruited); Offenbach (g), Marthe (g) | E05, E01; opt E03 | BOSS-32 (duel), 33; opt BOSS-34, 35, 38 (SQ-23) | 41–45 (opt to 50) | Canvas Ledger (Erasure hunt), Salon of 1834 event, *La Lumière* finale flight, portrait sitting, LUMIÈRE, the Last Anachronisms chain, Thalberg rematch (definitions §4f) |

*Optional hours:* 0.25+0.5+1+1+1.25+1.25+1.25+1+0.5+1.25+1+0.75+0.5+4.5+0.5+3 = **19.5 h** (one epilogue counted), plus **2.5 h** post-game superbosses and collection = **22.0 h**.

### §4b Story beats, escalation rung and romance beat per chapter

| ID | Story beat | Escalation (rung #, §4c) | Romance (§4d) |
|---|---|---|---|
| CH-P | Late at night Min-jun practises *Clair de lune*, taps the fallboard twice (his habit, first frame) and hears a hum from a hairline crack (left by the 2019 works) behind Room B-07's storage closet. He pulls off the closet's back panel: behind it the 1906 brickwork, split by the 2019 works, has fallen away from the back of the counterweighted bookcase, which swings open onto a stair down to the Hidden Study: an eight-panelled Door with a clock-dial lock, the Ornate Brass Key hanging by its bow from a brass hook on the music stand, a French score *Harmonies de l'ère perdue* with a blank last page, an 1880s Pleyel upright, a dust outline where a small painting hung, and a plaque, "Pour M., qui doit venir. — Les Amis, 1886". **Puzzle (binding):** the dial's hands stand at 7:51 (the Window's sunrise, explained only in CH-17); the score's first page, open on the upright, shows LM-01's eight notes; playing **D E F♯ G A B C♯ D** turns the hands to XII, where they line up into the key-shaped sigil, and the key then fits. Wrong notes carry no penalty. He unlocks the Door, plays, and steps into darkness; the self-closing bookcase swings shut behind him, and from the closet side its back reads as one more blind panel among the old bricks, so the March search finds nothing. | 0 (unknowing): Archon's seal test in 1833 is what opens the Door. | — |
| CH-01 | He wakes after the Passage Swoon among bones and lime pits, phone at 3%. Old quarryman Mathurin, a wine-runner hiding from the same patrols, guides him past the octroi agents, a National Guard picket and the "men in grey" (stealth hazards: being seen means a 5-second chase and a reset to the last lantern checkpoint). He fights Echoes with resonance (humming, clapping, a tuning fork) and climbs out at rue Saint-Jacques into a rainstorm. | 1 The Search | — |
| CH-02 | Penniless, he crosses Paris to the one name he knows and is thrown out of the Conservatoire by Cherubini. He earns soup at *Au Diapason Fêlé* on a pianino with three dead keys. His first slip ("that's Debussy's *Suite bergamasque*") starts the Secrecy Meter. Berlioz, drinking off a bad review, hears *Clair de lune* and declares him "a madman of the right kind". | 1 The Search (Julien hears of "the Oriental pianist") | — |
| CH-03 | Berlioz takes him to Delacroix's studio and to the 19-year-old Alkan. From the gallery of the Théâtre-Italien he watches Chopin and Liszt play Onslow at Harriet Smithson's benefit. At Mme Lavergne's salon he survives Henri Herz's cutting contest, then plays Ravel's "Ondine"; the room goes silent and Lord Vane leaves early. | 2 Velvet Leash (Lucile recruited 28 Apr); 3 Ink ("The Mandarin Mimic" caricature) | Lucile sells painted fans at the salon. Vane watches her watching Min-jun; a gloved hand passes a purse (shadowed). |
| CH-04 | Min-jun maps the quarries for his door; the gallery collapses behind him and his notes are stolen. Vane's mercenaries turn the 5 June march into a riot and plant a pamphlet in his name. Min-jun, Berlioz and Delacroix hold the rue Saint-Antoine barricade; the fighting spills through the Pavillon du Roi into Place Royale, where Hugo watches from his window above the arcades. They capture Captain Marlot, and clear his name before Prefect Gisquet with Lucile's sketch of the paymaster and Daumier's testimony. Alkan's family shelters the wounded; Alkan joins. Berlioz gives Min-jun a conductor's baton. | 4 Rust; 5 The Barricade (**unsanctioned**) | **First meeting (Thu 9 May)**, staged: she sketches him at the tavern and complains "rain has no outline". He: "Then don't paint outlines." Her sketch, meant as a report, saves him: the first crack in her role. |
| CH-05 | Paris opens: boulevards, Pleyel's, the Faubourg Saint-Germain. He meets Chopin at Pleyel's and Liszt (transcribing the *Fantastique*) at Marie d'Agoult's. Vane offers patronage and a Pleyel on loan. Archon, offscreen, rebukes Vane for the barricade. | 2 Velvet Leash tightens ("make him love Paris") | **She joins.** First plein-air lesson at dawn on the Pont des Arts: colour in shadows. IMPRESSION unlocked. |
| CH-06 | At the Louvre, Min-jun spots *E = mc²* in the drapery of Lucile's state-commissioned copy, for a provincial church, of Delorme's *Vow of Anne of Austria*, made from the modello Delorme deposited for copyists (R-59); a copyist's painting comes alive. Chopin, there to see Lucile's copy, fights beside them and joins. Lucile's first Monet-style canvas causes a stir. On Sun 11 Aug, just after the chapter, Franchomme carries Chopin off to Touraine (R-57). | 3 Ink (art-press campaign); 6 The Drowned Gallery | **First canvas**, *Le Pont Royal, effet de brume*, shown Fri 2 Aug in Delacroix's studio (Sand is not there; she sees it later in Lucile's attic): Delacroix fascinated; Ingres, seeing it in Corbel's window, calls it "weather, not painting"; Delorme turns pale. On Fri 9 Aug she gives him a small rain study for his 23rd birthday. Early Truth window opens. |
| CH-07 | Alkan notices nitinol springs at the Horlogerie Brücke; the party fights through its undercroft. Vane brings Thalberg to the Austrian Embassy; Brücke rigs the action; Rossini judges; Chopin, back from Touraine that evening, watches. The duel is won or lost and the story continues either way. Liszt, provoked and delighted, joins. Théo is introduced (SQ-07). | 7 Humiliation | Player-controlled scene as Lucile: a letter left at Maison Corbel; she hesitates. Her coercion (Théo, the debt) is shown. |
| CH-08 | Farrenc recognises Delorme's formulas as a tuning system of seven and joins. Someone is sabotaging Chopin's Pleyel before the charity concert; the trail runs through the Palais-Royal sewers to Julien and his cassette shrine. Min-jun spares him. | 8 The Accident (Brücke secretly made it lethal) | At the concert she realises Vane's people meant to hurt him and sends Vane a false report. **First kiss** on the Salle Pleyel roof (fade). |
| CH-09 | Chopin's *Żal* and Delacroix's *Algiers* finales lead to the first confessions; both pledge to help. Berlioz weds Harriet. That night the Grey Hand abduct Min-jun to the Bercy depots to force a performance and record his signature, injuring his right hand. **Three threads:** Lucile breaks into the Hôtel de Vane, steals the ledger, finds the address and sends Petit-Louis running to the wedding supper; Berlioz leaves his own wedding to lead the rescue; Min-jun escapes his cell alone. They converge on Roussel. Julien, sickened, guides them out and hands Min-jun the bundle of Lucile's reports. | 9 Abduction | **The reveal (by Julien).** The reports quote the player's own confided lines. Dawn on the Pont des Arts: she admits everything, including that she stopped reporting after the concert, and puts the ledger in his hands, then presses her sketchbook (KEY-09) on him too: "Keep it. It's the only honest thing I own." **Fracture.** She leaves for Nohant with Théo. |
| CH-10 | Hunted, Min-jun is taken out of Paris by Liszt on a "virtuoso's tour" with Farrenc and Alkan; Delacroix stays for the Salon du Roi commission (Thiers) and Chopin for his pupils and the Op. 10 proofs. On the road Farrenc decodes the ledger: the Clef map, the Seventh Panel's location in Düsseldorf, and "L. — to be removed". Corot paints at Fontainebleau (GST-03). Liszt lodges at the Auberge du Lion d'Argent in La Châtre and gives a benefit concert there, keeping clear of Nohant ("a touring virtuoso calling on a notorious novelist would be in every paper"). Angry, Min-jun goes to Nohant anyway: Sand shelters Lucile, challenges him, and hosts one cool, polite dinner with Casimir Dudevant. By night automata attack the house (a house-defence wave: MJ, LU and one of FA/AL, plus Sand as guest); Sand recognises the Berry legend of the wolf-leader in the pack and gives the hint for the hunt. In the Vallée Noire, Liszt rides in from La Châtre for BOSS-13. | 10 The Knife (Lucile ordered killed; Brücke aims at Min-jun too) | Fallout talks with Sand mediating (Horizon choices). **Pissarro-style canvases** of the Berry fields. She fights beside him at the house and in the Vallée Noire. Mending scene 1. She returns to Paris with Théo for his treatment. |
| CH-11 | By diligence to Liège, where Chopin joins the tour (10-year-old Franck at the keyboard), over the Aachen border to Düsseldorf (Mendelssohn, Clara Wieck and her father, the critic "Florestan" travelling with them (R-56), Czerny; the "Madame Schu—" slip). **The Seventh Panel:** Academy director Wilhelm von Schadow (NPC-51) bought *Ad Astra* in 1832 as "a curious French allegory"; on Mon 18 Nov Brücke's agents buy it from him with forged Prussian export papers and ship it upriver on the *Concordia* from Cologne toward Mainz. On Tue 19 Nov the party rides to Cologne and boards (BOSS-14, the boiler sabotage, is fought aboard); on Wed 20 Nov they take the panel off at the Lorelei and leave the boat at Mainz; on Thu 21 Nov a fast diligence brings them to Strasbourg, where Sand's letter is waiting. A short playable interlude in Paris: Théo is taken from Sœur Marthe's dispensary (Thu 14 Nov); Marthe secretly tells Lucile where; Lucile goes after him alone. | 11 Leverage | Apart. Min-jun plays LM-22 alone on the Lorelei cliffs. Lucile's interlude shows her choosing to act, not wait. |
| CH-12 | Lucile, smuggled in by Marthe, steals the chaplain's key, frees Théo from the abbey undercroft and unbars the gate. The party reaches Paris on Sun 24 Nov (the Théâtre-Italien walkout as the opening quiet scene) and storms Val-de-Grâce on the night of Tue 26 Nov, defeating Delorme. Archon receives them, reveals Min-jun's origin to all, explains the seal and the immortality it promises, and offers a throne. Min-jun refuses; they escape with Théo. | 12 The Offer ("Stay as a god or stay as a corpse") | **She rejoins** for good. Under Mignard's dome she reads him her unsent letters. Mending scene 2. |
| CH-13 | Archon's royal gala at the Opéra. Min-jun and Liszt premiere Min-jun's *Concerto "Lost Era"* with Berlioz conducting while two teams fight in the rafters and corridors and smash Brücke's recording horns. Archon gets only a partial signature. The party captures Brücke's dirigible on the roof. Sœur Marthe defects. | 13 Record, Then Kill | In the rafters Lucile saves Delacroix; when she is cornered, Min-jun leaves the piano for eight bars to save her while Liszt covers. Afterwards: "That was yours. Not the future's." |
| CH-14 | Ordered to kill Lucile, Vane refuses. The party confronts him at the Hôtel de Vane (rhetoric duel); Roussel's cleaners come to kill Vane and Lucile and take Min-jun alive ("the boy breathing"); Vane gives up the Panthéon crypt key and the solstice timetable and defects. Sand leaves for Italy (Thu 12 Dec; Lucile alone sees her off at the Lyon mail-coach); Hiller, Chopin and Liszt play Bach (Sun 15 Dec); optional content opens across France; at Belgiojoso's (SQ-20) Liszt tells the princess about the embassy duel. On the Panthéon roof Lucile paints the stars. | 14 Cleaning House; Archon readies 15 | **Night of Stars:** *La Nuit étoilée sur le Panthéon* (IMPASTO). "Then teach us the music of the stars." Min-jun writes the coda *La Musique des étoiles* that night. Scripted confession (if no Early Truth). **Rank 10.** |
| CH-15 | Three parties descend through the crypt into labyrinth zones where 1833 Paris and 2026 Seoul are fused (a subway platform in the ossuary, a convenience store in the Palais-Royal arcade, Hanseong practice rooms off rue Bergère). **Routing (binding):** Party 1 (Lutèce zones) detunes Clefs I–II and faces BOSS-22; Party 2 (Hanseong zones, made from Min-jun's memories, so **Min-jun is always in Party 2**) detunes Clefs III–IV and faces BOSS-23; Party 3 (Orpheus zones) detunes Clefs V–VI and faces BOSS-24. Each party strikes its plinths with one of Alkan's tuning forks (KEY-32). The merged party then opens the Heart gate with Panel VII (BOSS-25). | 15 The Seal (being tuned) | Window Talk 4. If she is in Party 2 (W4), she walks through his city with him and sees it for the first time. |
| CH-16 | Archon and his Grey Hand formations (from 23:50); at the solstice instant (00:43) the Stilled Hour begins and only the eight-voice Octave can break it; Archon fuses with the Engine. When the Engine collapses, the half-struck chord folds in on him and the Heart shatters. Brücke flees with the last oscillator. | 15 The Seal broken | She is the second voice of the Octave. |
| CH-17 | At Paris sunrise the dying network opens the Door one last time; the friends hold it open by playing *La Musique des étoiles* on the Engine's ruined keyboard. Under the Window Clock (§11i): farewells and keepsakes (KEY-30), the Pact of the Door, the Heart shard given to Delacroix. Min-jun asks: "Will you come with me?" | — | **The Question.** Her answer comes from the whole game (LAW-23). |
| CH-E1 | They step out into the Hidden Study, awake, on a snowy Dongji afternoon (16:52 KST). Family reunion, a police interview, the problem of her papers (Théo's open letter), Céline d'Orsenne burning Archon's Codicil, an exhibition where Lucile finds her own lost canvas, Théo's grave. Brücke has followed and hunts Min-jun before he can "disclose". New Year's Eve premiere of the completed *Harmonies*; Brücke's attack, the clock-tower climb (S10) and the duel in the Hidden Study (BOSS-30); the sealed packet opened at 23:00 (the brief's image); the Bosingak bell. | 16 The Last Hour (Brücke, in 2026) | Culmination as a modern romance: snow, noraebang, the bell. She paints Seoul at night and reaches LUMIÈRE. |
| CH-E2 | Lucile asks him to stay; he agrees and throws his phone, carrying a recorded goodbye, through the closing Window (LAW-25). That day Paganini sits in the audience at Berlioz's Sunday-afternoon concert. Through the winter Lucile prepares her Salon entry while Delorme's Erasure hunts her canvases (Canvas Ledger, §4f); the friends destroy the cabal's last evidence (SQ-23). Lucile proposes at dawn on Montmartre on her 24th birthday, Sun 9 Feb 1834; Delacroix paints the portrait from life (playable sitting). The jury sits at the Louvre on Sat 15 Feb (BOSS-32). On Sat 1 Mar: the *La Lumière* flight, BOSS-33 at the Salon's opening, and that night Chopin's 24th-birthday supper at the Atelier, where the *Harmonies* finale is played from memory and never written down (REP-28). Coda: Seoul, 22 Dec 2026, played as Seo-yeon. | No rung against him; Delorme's **Erasure** targets Lucile's legacy | Culmination: a shared atelier, her Salon debut hung "au ciel", won from the jury (with Delaroche's voice if SQ-11 is done), LUMIÈRE. |

### §4c Escalation ladder (A-1)

Rungs are numbered in chapter order. **Tier** shows the climb (Watch → Soft → Quiet → Hard → Lethal). **Archon's doctrine:** keep Min-jun alive until his signature is **fully** recorded (LAW-12), then kill him. The CH-13 recording is partial, so from CH-14 he again needs Min-jun alive as the living string. **Three unsanctioned spikes:** rung 5 (Vane), rung 8 (Brücke) and rung 10's lethal tuning against Min-jun (Brücke). **Motive** (A-1, §8): **M1** = exposure in 1833; **M2** = the portal (he must never go home); **SIG** = the signature or the seal.

| # | Rung | Ch. | Tier | Carried out by | Action against Min-jun | Motive | Sanctioned by Archon? | Player-facing signal |
|---|---|---|---|---|---|---|---|---|
| 1 | The Search | CH-01–02 | Watch | Grey Hand; Julien | Comb the quarries for "the arrival" (date known, place not); tavern rumours | M1 | Yes | Men in grey with lanterns; a pianist asking questions |
| 2 | The Velvet Leash | CH-03–08 | Soft | Vane (Lucile, unwitting of the truth) | Keep him content in Paris and watched: patronage, a loaned Pleyel, Lucile | M1 + M2 (A-2: a reason not to go home) | Yes ("cheaper than a bullet") | Invisible on a first run; the shadowed purse in CH-03 |
| 3 | Ink | CH-03–06 | Quiet | Delorme (press), Vane | "The Mandarin Mimic" caricature in *Le Corsaire*; art-press attacks | M1 | Yes | Secrecy +10 scripted; newspaper items |
| 4 | Rust | CH-04 | Quiet | Brücke, Julien | Quarry gallery collapsed behind him; his notes stolen | M2 (sabotage the search for the way back) | Yes | Map item lost; cave-in event |
| 5 | The Barricade | CH-04 | Hard | Vane via Captain Marlot | Frame-up as an agitator at a riot | M1 | **No** (Vane's panic; Archon rebukes him in CH-05) | Barricade battle; Secrecy forced ≥ 40 |
| 6 | The Drowned Gallery | CH-06 | Quiet | Julien (from Lucile's report) | Floods the Val-de-Grâce quarry access he was searching | M2 | Yes | Flooded passage; Lucile's guilty portrait expression |
| 7 | Humiliation | CH-07 | Quiet | Vane; Brücke rigs the action | The Thalberg duel, a paid claque | M1 | Yes | Duel starts at Favor −20 |
| 8 | The Accident | CH-08 | Quiet → Lethal | Julien (believes "break"); Brücke (secretly "lethal") | Rigged Pleyel string assembly | M1 + M2 | **No** (Brücke's private escalation) | Dungeon; Julien's horror when he learns |
| 9 | Abduction | CH-09 | Hard | Archon via Commandant Roussel | Kidnap to force a performance and record the signature | SIG | Yes (ordered) | Split-control rescue |
| 10 | The Knife | CH-10 | Hard (Min-jun, sanctioned) / Lethal (Lucile; Brücke's private tuning against Min-jun) | Brücke's automata | Night attack at Nohant; Lucile marked for death | M2 + leverage | Lucile: yes. Min-jun: **no** ("alive if possible"; Brücke tunes them to kill) | House-defence wave and boss battle; "L. — to be removed" in the ledger |
| 11 | Leverage | CH-11 | Hard | Delorme (Théo seized); Brücke (boiler sabotage) | Hostage to lure Lucile and Min-jun; boiler set to blow | M2 + leverage | Yes | Sand's letter; steamboat boss |
| 12 | The Offer | CH-12 | Soft / Hard | Archon | "Stay as a god or stay as a corpse"; survival battle | M2 + leverage | Archon's own act | Archon: The Audience |
| 13 | Record, Then Kill | CH-13 | Lethal | Brücke, Roussel | Record the signature on stage, then shoot him | SIG | Yes | Three-front battle |
| 14 | Cleaning House | CH-14 | Lethal | Roussel's cleaners | Kill Vane and Lucile; take Min-jun alive for the solstice (Roussel's order: "the boy breathing") | M2 + leverage | Yes | Boss battle protecting Vane |
| 15 | The Seal | CH-15–16 | Lethal | Archon | Bind Min-jun into the Heart as the living string | M2 + Archon's reign | Archon's plan | Final dungeon and battle |
| 16 | The Last Hour | CH-E1 | Lethal | Brücke, alone in 2026 | Silence Min-jun before he can "disclose" | M2 only | — (Archon gone) | Euljiro automata; clock-tower climb; duel in the Hidden Study |

### §4d Romance arc (A-2) with Horizon inputs (LAW-23)

| Ch. | Beat | Lucile's status | Style | Horizon input (W = Wings +, R = Roots −) |
|---|---|---|---|---|
| CH-03 | Seen at the salon; recruited by Vane on 28 Apr (shadowed) | NPC | — | — |
| CH-04 | First meeting (staged); her paymaster sketch clears him | NPC | — | — |
| CH-05 | Dawn lesson on the Pont des Arts; joins | PC | IMPRESSION | — |
| CH-06 | First Monet-style canvas and its stir; birthday gift; Early Truth possible (R7) | PC | — | Lesson 1 "Reflections" (W7 +3 / R1 −5); Early Truth W1 +15 |
| CH-07 | Her POV scene at Maison Corbel; Théo introduced | PC | — | Lesson 2 "Broken Colour"; SQ-07 opens (completion later gives W6 +10 and meets the gate) |
| CH-08 | Turns quietly (false report); first kiss | PC | — | Early Truth window closes at chapter end |
| CH-09 | Steals the ledger to save him; revealed by Julien; Fracture; gives him her sketchbook (KEY-09); leaves | PC → leaves | — | — |
| CH-10 | Nohant: fallout, Sand's mediation, fighting together, Mending 1 | PC (Fractured) | POINTILLÉ | Lesson 3 "The Field in Points"; Window Talk 1 (W2 +5); Nohant answer (W3 +10 / 0); Sand's counsel (R3 −10 / 0); Corot's invitation to Italy next spring: Min-jun's line (R6 −5 / 0) |
| CH-11 | Paris interlude: Théo taken; she goes alone | Solo interlude | — | — |
| CH-12 | Frees Théo herself; rejoins; unsent letters; Mending 2 | PC | — | Window Talk 2 (W2 +5); SQ-13 opens (CH-12–CH-14) |
| CH-13 | Saves Delacroix; Min-jun's eight bars | PC | — | — |
| CH-14 | Night of Stars; confession; rank 10 | PC | IMPASTO | Lesson 4 "Night"; Window Talk 3, mandatory (W2 +5); SQ-11 (R2 −15), SQ-12 (R4 −10), SQ-13 (any time CH-12–CH-14, R5 −5); BQ-PC08 finale with her present (W5 +5); SQ-07 last chance (crypt-door prompt) |
| CH-15 | Sees Seoul in the amalgam zones | PC | — | Window Talk 4 (W2 +5); in Party 2 through the Seoul zones (W4 +5) |
| CH-16 | Second voice of the Octave | PC | — | — |
| CH-17 | "Will you come with me?" | PC | — | Final words (+5 / 0 / −5) |
| CH-E1 | Seoul: museums, her lost canvas, Théo's grave, the bell | PC | LUMIÈRE | — |
| CH-E2 | Paris: atelier, her proposal on her 24th birthday (Sun 9 Feb 1834), the portrait sitting, the jury, the Salon | PC | LUMIÈRE | — |

### §4e Brief beat → chapter map

| Brief beat | Chapter |
|---|---|
| Secret basement room at the Seoul conservatory; step through | CH-P |
| Catacombs of Saint-Denis; ghouls, militia, basic acoustic attacks | CH-01 |
| Latin Quarter in the rain, homeless; shelter near the Conservatoire; tavern upright | CH-01 end, CH-02 |
| Berlioz hears him; introduces Delacroix and Alkan | CH-02 end, CH-03 |
| *Gaspard de la nuit* at a low-tier salon; Vane takes note | CH-03 |
| Vane's frame-up, Marais riot, barricade fight with Berlioz and Delacroix | CH-04 |
| Overworld expands: Grand Boulevards, Louvre atelier, Pleyel workshop, Faubourg Saint-Germain | CH-05 (opened), CH-06, CH-07 |
| Meets Chopin and Liszt | CH-05 (joins CH-06, CH-07) |
| Thalberg duel at the Hôtel d'Apponyi | CH-07 |
| Formulas in a popular painter's work; alloys in a watchmaker's shop | CH-06, CH-07 |
| Sewers of Palais-Royal; Chopin's Pleyel sabotage; Julien | CH-08 |
| Confessions to Chopin and Delacroix | CH-09 |
| Regional estates, Nohant, Rhine; Schumann, Clara, Mendelssohn, Czerny | CH-10, CH-11 |
| Val-de-Grâce; Archon's master plan | CH-12 |
| Grand Concert Battle at the Opéra; dual-piano concerto; rafters and corridors | CH-13 |
| Chrono-Labyrinth; spatial anchors; Paris/Seoul amalgams | CH-15 |
| Synergy climax breaking the temporal warding | CH-16 (BOSS-27) |
| Archon with the corrupted synthesized piano engine | CH-16 (BOSS-28) |
| Fleeting window; farewell | CH-17 |
| Return to 2026; the 1834 portrait | CH-E1 (as written); CH-E2 coda (adapted) |
| A-1 escalation | §4c, LAW-14 |
| A-2 romance | §4d, §5e, §8d |
| A-3 branch | CH-17, CH-E1, CH-E2, LAW-23–26 |

### §4f Epilogue content summary

| | CH-E1 Seoul, 2026 (YES) | CH-E2 Paris, 1834 (NO) |
|---|---|---|
| New areas | Seoul overworld (W03), Jeong-dong, Kang apartment, Hongdae, Insadong, French Embassy, Hangaram exhibition, Yanghwajin, Euljiro/Line 2 tunnels, Namsan, Conservatory clock tower, Bosingak | Winter Paris, Atelier Aubray-Kang (Montmartre), Le Diapason Bleu, Delorme's atelier, the Dead Heart, Salon of 1834, Château d'Orsenne patent vault (Belgiojoso's salon and Delacroix's studio revisited) |
| Party | MJ, LU, SY, JW + Remembrances (§6) | All 8 (+ JU), Offenbach (g), Marthe (g) |
| Story boss | BOSS-29 Automaton "Line 2"; BOSS-30 Elias Brandt, The Last Hour (in the Hidden Study) | BOSS-32 The Salon Jury (Lucile leads; Louvre, Sat 15 Feb 1834); BOSS-33 Delorme's Masterwork (Salon opening, Sat 1 Mar 1834) |
| Optional challenge | BOSS-31 Ossia (Namsan); busking ladder; Hanmadi word collection | BOSS-34 The Unwritten (Dead Heart); BOSS-35 Thalberg rematch; BOSS-38 via SQ-23; SQ-22, SQ-23; the Atelier restoration (if SQ-12 was skipped) |
| Unique systems | Phone menu, subway, ₩, Spotlight Meter, busking ladder, Hanmadi, noraebang | Canvas Ledger (Erasure hunt), *La Lumière* finale flight, the portrait sitting, the keepsake forge |
| Musical climax | *Harmonies* finale written on the blank last page and premiered, 31 Dec 2026 | *Harmonies* finale played from memory at Chopin's birthday supper, 1 Mar 1834, never written down; KEY-39 asks Seo-yeon to write the last page |
| Final image | Min-jun and Lucile open the packet in the library, 31 Dec 2026, 23:00 | Seo-yeon opens the packet and sees the fallboard tap, 22 Dec 2026; the coda ends on her bow lifting |

**Epilogue systems (binding definitions).**
- **Canvas Ledger / Erasure hunt (CH-E2).** The Secrecy HUD slot becomes the Canvas Ledger, tracking Lucile's **19 surviving canvases** (24 minus the 5 burned, LAW-21) as Delorme's agents remove them. Each recovered canvas (a map event plus 1–2 Living Tableau battles) adds +1 to BOSS-32's starting Favor (cap +15). Canvases not recovered appear in the end text as "lost to history".
- **Busking ladder (CH-E1).** 8 spots (Hongdae ×3, Insadong, Yanghwajin, Namsan, Jeong-dong, Bosingak plaza) using the salon *Phrase* minigame, paid in ₩, ranked Rookie → Legend. Clearing all 8 raises the Remembrances from Lv 50 to Lv 55 power (§6) and earns Seo-yeon's Lost Era bow (§14).
- **Hanmadi (한마디, CH-E1).** 40 Korean words Lucile picks up from NPCs and signs. Each changes one of her battle quotes and adds +1% to LUMIÈRE's power; all 40 unlock her Seoul-only skill 별 *Byeol*.
- **Noraebang (CH-E1).** One scene using *Phrase*; no new system.
- **Phone menu (CH-E1).** Map (subway fast travel), Messages (quest log), Camera (album: the CH-14 photos, KEY-02), Translate (running gag and Hanmadi log), Music (sound test), Wallet, Notes (save anywhere outside dungeons, §11h).
- ***La Lumière* finale flight (CH-E2, Sat 1 Mar 1834).** On the morning of the opening, Delorme's agents spirit Lucile's accepted canvas off to her atelier (E05). The party storms it and recovers the canvas, but Living Tableaux hold the quays, so *La Lumière* (flown down from its Montmartre mooring) carries it to the Louvre: a 2:30 Mode-7 run over the river past Delorme's kite automata. Damage taken carries into the canvas's HP bar in BOSS-33. *La Lumière* is then dismantled (SQ-23).
- **Portrait sitting (CH-E2).** Three conversation topics with Delacroix that change his lines and unlock his Lost Era forge (his keepsake is still the component); the player never chooses the painting's composition (LAW-26).
- **Keepsake forge (CH-E2).** Each KEY-30 keepsake is the component that lets Pleyel and Théo forge its giver's Lost Era weapon at the Pleyel workshop (§6, §14).

---
## §5 Playable Party Roster

Eight permanent members (PC-01–PC-08), two Seoul-branch members (PC-09, PC-10) and one optional recruit (PC-11). Active party: 4. Stats use §10a. Join stats below are exact (Lv-1 base + growth × (Lv − 1), rounded half up; HP/INS from the §10a curves; no Opus bonuses included). Members who join or rejoin late arrive at **max(listed level, active-party average − 1)**.

### §5a Roster summary

| ID | Name | Dates | Age in game | Join / leave / rejoin | Role | Archetype | Weapon | Unique command |
|---|---|---|---|---|---|---|---|---|
| PC-01 | **Kang Min-jun** (강민준) | b. 9 Aug 2003, Incheon | 22 → 23 on Fri 9 Aug 1833 (CH-06) | CH-P; never leaves (solo thread CH-09; on stage CH-13) | Buffer/debuffer, flex caster | Bard / Conductor | Batons (row-free) | RECITAL, CONDUCT |
| PC-02 | **Lucile Aubray** | b. 9 Feb 1810, Paris (fate: LAW-24/25) | 23 in the main game and CH-E1; turns 24 on Sun 9 Feb 1834 (CH-E2) | Joins CH-05; leaves dawn CH-09; PC (Fractured) CH-10; solo interlude CH-11; solo then rejoins CH-12 | Field controller, light caster | Chromomancer (FF5 Geomancer × FF6 Relm) | Brushes | PLEIN AIR |
| PC-03 | **Hector Berlioz** | 11 Dec 1803 – 8 Mar 1869 | 29 → 30 on Wed 11 Dec (CH-14) | Joins end CH-02; absent CH-10–11 (newly married); rejoins CH-12 | Summoner, heavy hitter | Summoner / Knight | Sword-canes | ORCHESTRATE |
| PC-04 | **Eugène Delacroix** | 26 Apr 1798 – 13 Aug 1863 | 34 → 35 on Fri 26 Apr (CH-03) | Joins CH-03; absent CH-10–CH-11 (the Salon du Roi commission begins; §16e keeps him from Sand); rejoins CH-12 | Elemental spellblade, collector | Red Mage / Mystic Knight (+ Blue-Magic Studies) | Rapiers | CANVAS |
| PC-05 | **Charles-Valentin Alkan** | 30 Nov 1813 – 29 Mar 1888 | 19 → 20 on Sat 30 Nov (CH-12) | Guest CH-03; joins end CH-04; never leaves | Tank, burst damage | Monk (input techniques) | Hammers | ÉTUDE |
| PC-06 | **Frédéric Chopin** | 1 Mar 1810 (baptismal record 22 Feb) – 17 Oct 1849 | 23; turns 24 on Sat 1 Mar 1834, the Salon's opening day (CH-E2) | Joins CH-06; absent Sun 11 Aug – Sat 7 Sep 1833 (Touraine with Franchomme; real, R-57), rejoins at the duel; absent CH-10 (stays in Paris: lessons, Op. 10), rejoins the tour at Liège at the start of CH-11; absent CH-12 (bronchitis); rejoins CH-13 | Healer, time control | White Mage / Time Mage | Quills (row-free) | RUBATO |
| PC-07 | **Franz Liszt** | 22 Oct 1811 – 31 Jul 1886 | 21 → 22 on Tue 22 Oct (CH-10) | Joins CH-07; never leaves | Offensive magic duelist | Black Mage / Magic Knight | Sabres | TRANSCEND → MEPHISTO |
| PC-08 | **Louise Farrenc** | 31 May 1804 – 15 Sep 1875 | 29 (birthday before joining) | Joins CH-08; never leaves | Analyst, support | Scholar / Red Mage | Folios (row-free) | COUNTERPOINT |
| PC-09 | **Kang Seo-yeon** (강서연) | b. 3 Apr 2007, Incheon | 19 | CH-E1 only (coda NPC in CH-E2) | Fast support, sustain | Dancer / Bard | Bows | BOW |
| PC-10 | **Choi Jae-won** (최재원) | b. 17 Jan 2003, Busan | 23 | CH-E1 only | Combo striker | Thief / Monk | Drumsticks | BEAT |
| PC-11 | **Julien Marchetti** (ANA-03), optional | b. 14 Apr 1922, Paris-Belleville | 31 (body and lived) | Recruit CH-14 via SQ-21; stays through CH-16 and CH-E2 (not in CH-E1) | Gambler-caster | Gambler | Canes | IMPROVISE |

### §5b Join stats and growth

Growth per level (§10a): S 0.90 · A 0.75 · B 0.60 · C 0.45 · D 0.30. Lv-1 bases are listed for formulas_and_curves.

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
| PC-09 SY | 40 (CH-E1 entry average ≈ 41, − 1; raised by the §5 join rule if the party arrives higher) | 1,880 | 242 | 27 | 42 | 27 | 34 | 43 | 35 | C/A/C/A/C/B/A/B | 9/13/9/11/14/12 |
| PC-10 JW | 40 (as PC-09) | 2,120 | 178 | 42 | 20 | 34 | 27 | 43 | 49 | A/C/A/D/B/C/A/S | 13/8/11/9/14/14 |
| PC-11 JU | 33 (party avg − 1) | 1,419 | 190 | 23 | 37 | 22 | 29 | 37 | 43 | C/A/C/A/C/B/A/S | 9/13/8/10/13/14 |

### §5c Commands, passives, Synergy hooks

| ID | Unique command (mechanic) | Passive | Synergy hooks (§11b) |
|---|---|---|---|
| PC-01 | **RECITAL**: choose a learned piece (REP). Movement I sets an aura (INS paid once); on later turns "Continue" advances to Movement II (stronger aura), then III (a burst, after which the aura ends). The Recital **breaks** if he takes a hit ≥ 20% of max HP or is Hushed, Stagefrighted, put in Reverie or Fermata; he then suffers a **1-turn Stagefright** (an exception to the 2-turn default, §10d). Any other command ends it except **CONDUCT** (from end of CH-04): give one ally an immediate turn at ×1.25 power without breaking the Recital. **REP-30 *Jeong-dong Nocturne* is a salon piece from CH-03 (Heat 0). From CH-13 his own compositions (REP-27, REP-29, REP-30) also join the battle Recital list at Heat 0.** | **Perfect Pitch**: immune to Out of Tune and Discord; reveals hidden Resonance objects; immune to Unwritten while his far end is resonant (LAW-04), until CH-17. | SYN-01–07, 13–16, 17–20 |
| PC-02 | **PLEIN AIR**: paint in the battle's Light State (§10c). *IMPRESSION* (Monet, CH-05): a strike in the Light's first boosted element; repeated on consecutive turns +20% each (max +100%). *POINTILLÉ* (Pissarro, CH-10; grounded in his 1886–1890 divisionist period and rural subjects, so scripts call it "Pissarro's manner"): 8 small hits spread over enemies, each adding a Dot (10 Dots = **Composed**); on allies, 8 dots of Cantabile/Allegro/Varnish spread at random. *IMPASTO* (van Gogh, CH-14): a heavy hit that sets Night, may inflict Discord, and gives her Allegro; under Night it becomes *Nuit étoilée*, 8 swirling LIGHT/SHADE hits that restore INS. *LUMIÈRE* (her own, epilogues): two Light States at once. Sub-command **Shift the Hour** (0 INS, uses her turn): set Dawn, Noon, Dusk or Night. | **Plein Air**: her styles +25% under Dawn, Noon or Fog; enemy elemental affinities shown on target select; +25% preemptive chance outdoors. | SYN-01, 10, 12, 13, 15, 16, 19, 20, 23 |
| PC-03 | **ORCHESTRATE**: *Cue* adds a section token (Strings, Winds, Brass, Percussion, Chorus; max 3) with a small immediate effect; *Tutti* fires the Spectral Orchestral Summon matching the token combination (order irrelevant; 20 recipes, TUT-01–20, learned from pages of his notebooks; an unknown combination plays *Cacophony*, weak and non-elemental). Example: Brass + Brass + Percussion = *Marche au supplice* (EARTH/FIRE, massive single target). He may also use his equipped Opus Score's Invocation twice per battle (others once). | **Idée Fixe**: each consecutive Fight on the same target +15% (max 3 stacks). | SYN-04, 08, 14, 15, 16 |
| PC-04 | **CANVAS** (the brief's Visual Canvas): pick two unlocked Pigments (elements) and a Subject (one / row / all). The strike carries both elements (§10c dual rule). Named pairings carry riders, e.g. *Sardanapale* (FIRE + SHADE, Stagefright), *Chios* (ICE + WATER, all enemies), *Liberté* (FIRE + WIND, party Fortissimo). Sub-command **Sketch**: study an enemy to record its Study (36 Studies, STU-01–36, FF5 Blue-Magic collecting); each Study unlocks a new named Canvas recipe. Pigments: FIRE and WIND at join, EARTH and WATER CH-05, ICE and BOLT CH-08, SHADE CH-10, LIGHT at bond rank 10. | **Chiaroscuro**: Canvas +25% under Dusk, Night or Candle; 25% chance to counterattack when an ally is KO'd. | SYN-05, 08, 10, 13, 16, 21 |
| PC-05 | **ÉTUDE**: enter a directional/button sequence within 2.0 s (FF6 Blitz analogue). 12 Études (ETU-01–12): 3 known at join (Lv 11), then one each at Lv 14, 18, 22, 26, 30, 34, 38, 43 and 50. Names come from his pre-1834 works or plain French terms (never a post-1833 Alkan title). A Conducted Étude cannot fail its input. | **Recluse**: when last standing, or the only member in the back row, auto-Bulwark and +25% STR. | SYN-07, 11, 16, 22 |
| PC-06 | **RUBATO**: *Borrow* lowers one enemy's ATB by 30% and stores 1 charge (max 3); *Repay* gives all charges to one ally, each +34% ATB (3 charges = an immediate turn). At bond rank 10, *Tempo Rubato*: Borrow hits all enemies. | **Sotto Voce**: enemies target him 50% less often; his heals +20%; max HP −10%. | SYN-03, 09, 12, 16, 21 |
| PC-07 | **TRANSCEND**: cast two Harmony spells in one action (total INS × 1.5). **MEPHISTO** (from CH-13) adds *Transcribe*: re-perform the last skill used in the battle by anyone, ally or enemy, at ×1.25 (original INS cost; enemy skills cost 10% of his max INS; cannot copy unique commands or Synergies, except a Recital's Movement I or a Tutti). | **Bravura**: each consecutive action taken without being hit +10% damage (max +50%); a hit resets it. | SYN-02, 09, 14, 16, 22 |
| PC-08 | **COUNTERPOINT**: *Annotate* scans an enemy (full stats) and marks one weakness; the next 3 hits on it auto-crit. *Canon* marks an ally for 2 rounds; after each of their actions she echoes a complement (an attack is followed by a small heal on the lowest-HP ally, a heal by a strike). *Fugue* (Lv 22): 3 rising hits, EARTH → WATER → LIGHT. *Cadence* (Lv 30): party cleanse and a small heal. | **Equal Measure**: while she is in the active party, reserve members receive 100% EXP instead of 50% (a nod to her real fight for equal pay). | SYN-06, 11, 16, 23 |
| PC-09 | **BOW**: *Sostenuto* (party heal over time while she keeps choosing it) or *Spiccato* (4 rapid hits); switching modes costs no turn. | **Sibling**: +20% TMP while Min-jun is in the active party. | SYN-17, 19 |
| PC-10 | **BEAT**: timed button-press combo, up to 8 hits; each perfect press +10% damage; a perfect 8-hit BEAT also steals (§11a). Combos follow the *jangdan* rhythmic cycles of samulnori, faster as he levels: *semachi* → *gutgeori* → *jajinmori* → *hwimori*. | **Groove**: Crescendo gain +25%. | SYN-18, 19 |
| PC-11 | **IMPROVISE**: three reels of chord symbols (ii, V, I, IV, ♭VII, ♭II) stopped one by one (FF6 Slot analogue). ii–V–I heals the party; ♭II ×3 is *Tritone Storm* (CHRONO to all); mismatches give *Blue Note* (a random single hit). Every Improvise is Anachronic (Heat 3). | **Sideman**: +20% damage when acting immediately after an ally. In the Octave he adds a Blue Note (+9%). | SYN-20 |

**Cadenzas** (§11d): MJ *Gaspard Unbound* (the suite he played at Lavergne's) · LU *Lever du jour* (named for the CH-05 dawn lesson on the Pont des Arts) · BE *Dies irae* · DE *La Liberté guidant* · AL *La Machine* · CH *Warszawa* · LI *La Clochette* · FA *Grand Tirage* · SY *Arirang Variations* · JW *Encore Stage* · JU *Changes*.

### §5d Personality, arc, bond questline, confession

| ID | Personality | Arc | Bond questline | Confession |
|---|---|---|---|---|
| PC-01 | Wry, self-deprecating, a watcher. A perfectionist who has never finished a major work of his own. Kind by reflex, homesick by night; hums *Arirang* when nervous. | Interpreter of other people's genius → composer with his own voice (CH-13 concerto; *La Musique des étoiles*; *Harmonies*). Hiding → trusting. "How do I get home?" → "Where is home?" From condemning the cabal to recognising himself in them and choosing differently (LAW-20). | — (the hub; hidden **Own Voice** tally, §11g) | — |
| PC-02 | Quick-tongued, proud, funny, a fierce haggler. Sees colour where others see grey. Carries guilt like a stone in her pocket; would die for Théo. | Paints what sells → paints light → finds her own style (LUMIÈRE). Vane's instrument → the cabal's enemy → their target. Her life chosen for her → she chooses her own century. | BQ-PC02 The Hours of Light; BQ-PC02b A Harbour of Her Own | Early Truth at R7 (CH-06–CH-08 only), else scripted CH-14 (R10). §11f |
| PC-03 | Volcanic, grandiose and very funny about it. Generous with money he does not have. Deeply afraid of being misunderstood. | Loves an ideal (Harriet as *idée fixe*) → marries a real, injured woman. Learns France will misunderstand him for a century and writes anyway. The friend who leaves his own wedding to rescue you. | BQ-PC03 Idée Fixe | Optional, R10 |
| PC-04 | Aristocratic reserve, dry wit, a dandy in public. Keeps notes and sketchbooks (his *Journal* lapsed from 1824 to 1847). Hides a chronic throat ailment and private tenderness. | Guarded → brother. Fights for colour in *Women of Algiers*, sharpened by Lucile's "heresy". Becomes keeper of Min-jun's memory: designs the Door, paints the portrait. | BQ-PC04 The Colours of Algiers (mandatory) | Scripted CH-09 (R10) |
| PC-05 | Deadpan, bookish, painfully shy in company. Devout; reads Hebrew. Fascinated by machines. Dazzling at the keyboard, invisible in a salon. | Fear of the world → chooses to be a keeper rather than a recluse. In BQ-PC05 he imagines a piece about a machine; Min-jun stays silent about *Le chemin de fer* (1844) and about Alkan's decades of withdrawal (LAW-18). Co-executor of the Pact (Seoul branch). | BQ-PC05 The Railway Étude | Optional, R10 |
| PC-06 | Elegant, private, fastidious. A wicked mimic of other pianists. Melancholy that turns to steel when Poland is mentioned. | An exile who cannot go home (Poland after 1831): Min-jun's mirror. Breaks his block on the G-minor Ballade by finding the feeling himself. Learns to carry home inside music, and teaches it back. | BQ-PC06 Żal (mandatory) | Scripted CH-09 (R10) |
| PC-07 | Magnetic, theatrical, competitive, generous to a fault. Newly in love with Marie d'Agoult. A spiritual undertow beneath the showmanship. | Showman → seeker; plays second piano in someone else's concerto. Rivalry with Min-jun → brotherhood. The last friend: executor of the Pact in March 1886. | BQ-PC07 Transcendence (climax BOSS-36) | Optional, R10 |
| PC-08 | Brisk, rigorous, ironic. Tender with her daughter Victorine. Furious at injustice, especially the quiet kind. | Fears erasure → learns she was forgotten, then rediscovered, and resolves to fight (her 1842 professorship and equal-pay victory come on schedule). The party's conscience about history; names Min-jun's hypocrisy over Lucile, then forgives it. Becomes Théo's guardian in fact (SQ-07: the law bars her from the *tutelle* and the family council, so Aristide is named *tuteur*). | BQ-PC08 The Treasury | Optional, R10 |
| PC-09 | Blunt, stubborn, loyal. Furious at her brother for vanishing; kept his practice slot warm. | Grief → reunion; keeps the family secret. In the Paris branch she is the one who receives the past. | — | Already knows |
| PC-10 | Loud, cheerful, a 4th-year percussion major (entered 2023 after a year of re-auditioning) who leads the conservatory's samulnori club. Gamer talk is capped at one line per scene. | Comic relief who turns out to be the steadiest person in the room. | — | Told in CH-E1 |
| PC-11 | Charming, guilty, nervous; a natural sideman who was never a leader. | Thief → composer: writes his first truly original tune in 1833 (BQ-PC11). | BQ-PC11 A Tune of My Own | Not applicable (he knows) |

### §5e Lucile Aubray: canonical background (A-2)
- **Family:** father **Gilles Aubray**, frame-gilder of rue de la Harpe, died of cholera 14 Apr 1832. Mother **Madeleine** died in 1822. Brother **Théophile "Théo" Aubray** (FIC-01), b. 14 Jan 1821 (12 in 1833), came through the cholera with a weak chest; he needs medicine, food and warmth. Gilles left **1,200 F** of debts to Maison Grimaud (gilding and colour supplies) and the landlord.
- **Training:** a Louvre copyist's card since 1828; two years in a small women's atelier (Mme Daubrée's, rue de Seine). Rejected by the Salon of 1833 with a conventional portrait. Lives in an attic at **rue des Grands-Augustins** (LOC-P20). Earns her living painting fans and snuffboxes for **Maison Corbel**, rue Dauphine (LOC-P21).
- **George Sand:** they met in January 1831 at Maison Corbel, where the newly arrived Aurore Dudevant painted snuffboxes and fans for money. Lucile taught her varnish tricks. Sand, six years older, calls her ***ma petite Lumière***, pushed her toward the Salon, and is the only person Lucile never lies to.
- **Battle identity:** Delacroix paints *subjects* (elemental narratives); Lucile paints *light* (time of day, atmosphere, the battlefield itself). Her styles evolve IMPRESSION → POINTILLÉ → IMPASTO → LUMIÈRE.
- **Trust track and betrayal:** §11f (reports, Early Truth, Fracture, Mending); ending rule LAW-23.

### §5f Kang Min-jun: canonical background
- **School:** **3rd-year** composition major at Hanseong Conservatory (5th semester in spring 2026: entered Mar 2022, lost four semesters to military service, resumed Mar 2025), a strong pianist. Mentor **Prof. Yoon Mi-rae** (FIC-12). Roommate **Choi Jae-won** (PC-10). Served 18 months (Apr 2023 – Oct 2024) as an arranger-pianist in an ROK Army band.
- **Family:** father **Kang Do-hyun** (FIC-10), piano technician, *Kang Piano Service*, Euljiro (why Min-jun understands piano actions, which matters in the Pleyel sabotage plots); mother **Park Hye-jin** (FIC-11), piano teacher and his first teacher; sister **Kang Seo-yeon** (PC-09). Home: an apartment in Mapo-gu.
- **Languages:** Korean (native); English (fluent: a private channel with Vane, who uses 1980s idioms; English in front of Onlookers is a Slip, Secrecy +5); **French** from three years of Alliance Française evening classes, taken because he dreamed of studying in Paris: intermediate in March 1833, fluent by Act II, his accent part of his "foreigner" cover; **no German** (Liszt, Mendelssohn or Clara interpret on the Rhine). He presents himself openly as **from Corée** (no false identity). Display rules in §16c.
- **Tells:** **taps the fallboard twice** before playing (a childhood superstition): animated in the prologue's first frame and painted in the portrait (LAW-26).
- **On arrival:** smartphone at 3% (KEY-02), student ID (KEY-03), photocopied *Clair de lune* (KEY-04), a pencil, and a tuning fork (his first weapon, an Étude-tier baton-class item; not to be confused with the Pitch Pipe consumable or KEY-32).
- **Composer's wound:** has never finished a large work. The *Concerto "Lost Era"* (CH-13) is his first; *La Musique des étoiles* (CH-14) his second; the finale of *Harmonies* (epilogues) his third.

### §5g Visual key (binding for art_and_ui, portraits and prose)
| Who | Costume and palette key |
|---|---|
| MJ | CH-P–CH-01: navy padded jacket, grey hoodie, black jeans, white sneakers, canvas tote. From CH-02: Mère Gaudin's late husband's oversized bottle-green frock coat over his sneakers. From CH-05: a midnight-blue tailcoat and boots from Vane's tailor, kept after the betrayal as a reminder. Accent: midnight blue |
| LU | Auburn hair under a faded ultramarine headscarf, ochre shawl, paint-flecked grey dress, brush roll at the hip. In 2026: Seo-yeon's cream coat and red scarf |
| BE | Shock of red hair, green coat, cravat askew |
| DE | Dark hair and moustache, black dandy's coat, vermilion waistcoat |
| AL | Black coat, dark curls; slate grey |
| CH | Ash-brown hair, dove-grey coat, white gloves, a violet in the buttonhole |
| LI | Long fair hair, black frock coat, white cravat; silver accents |
| FA | Dark *bandeaux*, plum dress, ink-stained cuffs |
| Cabal | Hour of Velvet (Vane) crimson; Hour of Gold (Delorme) ochre-gold; Hour of Iron (Brücke) gunmetal; Hour of Smoke (Julien) blue-grey; the Almoner (Marthe) white; Archon black, with the sigil key |

---

## §6 Guest / Temporary Party Members & Key NPC Allies

Guests take a party slot, gain no EXP, cannot be re-equipped, and are fixed at the chapter's anchor level (§10e) unless noted. (P) = player-controlled, (AI) = AI-controlled.

| GST | Who | When | Why they fight | Battle command (mechanic) | Control |
|---|---|---|---|---|---|
| GST-01 | **Mathurin Lebœuf** (FIC-09), old quarryman and wine-runner, 61 | CH-01 | Hides from the same patrols; pities the lost foreigner | **LANTERN**: reveals hidden paths and Echoes in walls; Smoke on one enemy | P |
| GST-02 | **George Sand** (NPC-14) | CH-10 (the Nohant house-defence wave only; never in a battle with Liszt, Delacroix or Chopin, §16e) | Her house and her friend are under attack | **NOVEL**: choose a genre. *Tragedy*: Coda (20) on one enemy. *Romance*: Reverie on all. *Satire*: Out of Tune and DEF −25% on all. Weapon: cane | P |
| GST-03 | **Camille Corot** (NPC-13) | CH-10 (Fontainebleau) | An Echo stalks the forest where he paints | **SOUVENIR**: misty heal on all plus Varnish | P |
| GST-04 | **Clara Wieck** (NPC-05), 14 | CH-11 | Mendelssohn's academy is ambushed; she refuses to hide | **PRODIGY**: replays Min-jun's current Recital movement at +1 tier, otherwise *Caprice* (Allegro on one ally) | AI (her father insists) |
| GST-05 | **Felix Mendelssohn** (NPC-07) | CH-11 | Host; the Seventh Panel threatens his city | **HEBRIDES**: WATER + WIND wave on all; *Song without Words* cures Hush on the party | P |
| GST-06 | **Carl Czerny** (NPC-08) | CH-11 | Came to hear Liszt; will not let his pupil be shot | **VELOCITY**: Allegro on the party. Out of battle, *School of Velocity* drills give +1 TMP per PC (max +3) | P |
| GST-07 | **Robert Schumann** (NPC-04), name tab "Florestan" (R-56) | CH-11, BOSS-14 only | Aboard the *Concordia* | **FLORESTAN / EUSEBIUS**: toggles between his two literary personae: BOLT strikes or Cantabile. Written as creative masks, never as illness (§16e) | AI |
| GST-08 | **Jacques Offenbach** (NPC-03), 14 | CH-13 corridors team; CH-E2 | Substitute cellist who follows Chopin "for the adventure" | **GALOP**: random comic effect from six (trip = Fermata 1, cello screech = Hush, pocket-pick = Steal, pratfall = 1 damage, cheer = Allegro, "can-can kick" = double hit), weighted to good results | P |
| GST-09 | **Sœur Marthe** (ANA-06) | CH-14; CH-E2 | Defector after the Opéra | **TRIAGE**: full heal and cure all negative statuses on one ally, once per battle | P |
| GST-10 | **Sigismond Thalberg** (NPC-02) | Optional: SQ-20 Salon Circuit (CH-14); CH-E2 (both private visits as Belgiojoso's guest, R-10) | Respect earned in the CH-07 duel | **THREE HANDS**: three hits (bass EARTH, melody LIGHT, arpeggio WIND) | P |
| GST-11 | **Théo Aubray** (FIC-01) | CH-12 escape | Escort | Non-combat; escort HP bar (2,000) | — |

**Keepsakes (KEY-30, both branches).** At the CH-17 farewells, before the Question, each friend gives Min-jun a keepsake: Chopin's score page, Liszt's glove, Berlioz's baton, Delacroix's sketch, Farrenc's engraved plate, Alkan's Clef tuning fork (one of KEY-32), plus Julien's cassette if he was recruited.
- **Seoul branch: Remembrances** (CH-E1 only, the Seoul branch's Orchestral Summons). Each keepsake is a one-use-per-battle summon that casts that friend's Cadenza at **Lv 50 power (Lv 55 once the busking ladder is cleared, §4f)**.
- **Paris branch: the keepsake forge.** Each keepsake is the component that unlocks its giver's Lost Era weapon at Pleyel's workshop in CH-E2 (Chopin's score page → Chopin's quill, and so on; Julien's cassette → his cane).
- **A farewell skipped in CH-17 costs that friend's Remembrance (Seoul) or that friend's Lost Era forge (Paris, until Da Capo).** The Window Clock (§11i) is tuned so that direct play sees every farewell.

**Key non-combat allies:** Camille Pleyel (NPC-15: piano "Voicing" upgrades, Théo's master, the keepsake forge); Aristide Farrenc (NPC-20: Opus Score shop, press notices, Théo's *tuteur*); Maurice Schlesinger (NPC-41: second Score vendor); Mère Gaudin (FIC-02: tavern, first home); Petit-Louis (FIC-03: runner, informant); Princess Belgiojoso (NPC-26: tier-4 salon patron from CH-14, CH-14 safe house); Prefect Gisquet (NPC-24: ambiguous ally, one-time Unmasking bail-out); Heine (NPC-30: Secrecy-lowering columns); Prof. Yoon Mi-rae (FIC-12: Seoul archive); Det. Oh Sang-woo (FIC-13); Céline d'Orsenne (FIC-14).

**Fictional supporting cast (FIC, non-cabal):**

| FIC | Name | Born / age | Role |
|---|---|---|---|
| FIC-01 | Théophile "Théo" Aubray | 14 Jan 1821 – 3 Nov 1898 (Seoul) | Lucile's brother, 12; Pleyel apprentice (SQ-07); later *facteur de pianos* at Pleyel, Wolff & Cie; builds the Door; escorts the crate to Seoul 1888; buried at Yanghwajin (both branches) |
| FIC-02 | Joséphine "Mère" Gaudin | b. 1781 | Keeper of *Au Diapason Fêlé*; widowed by the cholera |
| FIC-03 | Petit-Louis Gaudin | b. 1822 (11) | Her son; street runner and informant |
| FIC-04 | Anselme Corbel | b. 1779 | Dealer, rue Dauphine; the cabal's frightened dead drop |
| FIC-05 | Mme Hortense Lavergne | b. 1790 | Hostess of the tier-2 salon, rue de Provence |
| FIC-06 | Maison Grimaud | — | Colour merchant and creditor whose notes Vane buys |
| FIC-07 | Captain Marlot | b. 1794 | Leader of the Black Coats, Vane's day-hire mercenaries (BOSS-05) |
| FIC-08 | Commandant Roussel | b. 1789 | Former captain of the disbanded Garde royale who styles himself Commandant; chief of Archon's Grey Hand; carries Brücke's rifle (BOSS-12, 19, 21) |
| FIC-09 | Mathurin Lebœuf | b. 1772 (61) | Quarryman-smuggler, CH-01 guide (GST-01) |
| FIC-10 | Kang Do-hyun | b. 1971 (55) | Min-jun's father, piano technician |
| FIC-11 | Park Hye-jin | b. 1974 (52) | Min-jun's mother, piano teacher |
| FIC-12 | Prof. Yoon Mi-rae | b. 1978 (48) | Composition professor; leads the Jeong-dong Collection catalogue |
| FIC-13 | Det. Oh Sang-woo | b. 1985 (41) | Jung-gu missing-persons detective |
| FIC-14 | Céline d'Orsenne | b. 1979 (47) | Head of the d'Orsenne Foundation (Paris); descends from Archon's son; opens the sealed Codicil of his Testament (KEY-35) on Tue 1 Dec 2026 and burns it after meeting Min-jun (CH-E1 only; in the Paris branch it is filed as an ancestor's fantasy). She does **not** carry the name Morvan, which no one in the 19th century ever knew. |
| FIC-15 | Victor-Lazare d'Orsenne | b. 1827 | Archon's son (background) |
| FIC-16 | Mme Daubrée | b. 1785 | Ran the small women's atelier where Lucile trained |
| FIC-17 | Mme Bastide | b. 1796 | Hostess of the second tier-2 salon, rue Taitbout (Taste: Novel) |
| FIC-18 | Gros-Louis Bréhat | b. 1790 | Smuggler king of the tavern cellars (BOSS-02); later a CH-14 informant |
| FIC-19 | Fernand Tissot | b. 1798 | Vane's steward and paymaster: the face in Lucile's sketch (KEY-10); night porter at the Hôtel de Vane in CH-09; defects with Vane |
| FIC-20 | Abbé Gaspard Rives | b. 1771 | Val-de-Grâce chaplain; owner of the Chaplain's Key (KEY-22) |
| FIC-21 | Rose Lambert | b. 1799 | Mère Gaudin's cousin at no. 12 rue Transnonain (SQ-22) |
| FIC-22 | Kapitän Johann Weyer | b. 1790 | Master of the *Concordia* (CH-11) |
| FIC-23 | M. Bourdin | b. 1780 | Lucile's landlord, whose notes Vane bought |
| FIC-24 | Auguste Pichon, "le Sergent" | b. 1772 | Tavern regular: one-legged Napoleonic veteran who sings *La Marseillaise* off-key |
| FIC-25 | Nanette | b. 1815 | Tavern regular: a *chiffonnière* who finds everything |
| FIC-26 | Hippolyte Vasseur | b. 1812 | Tavern regular: a Conservatoire violin student who always fails his exams |

---
## §7 Historical Supporting Cast Table

Party members (PC-03–PC-08) are in §5 (liberty: blanket R-00, plus R-21 for the Rhine trip and R-57 for Chopin's summer). Ages are for the game span (5 Mar – 22 Dec 1833); "→" marks a birthday inside it. Liberty = Y when presence or role contradicts the record.

| ID | Name | Birth – death | Age 1833 | Real 1833 whereabouts | In-game role | First CH | Liberty |
|---|---|---|---|---|---|---|---|
| NPC-01 | César Franck | 10 Dec 1822 – 8 Nov 1890 | 10 → 11 | Liège | Prodigy on the Rhine road; side scene with his father | CH-11 | N |
| NPC-02 | Sigismond Thalberg | 8 Jan 1812 – 27 Apr 1871 | 21 | Vienna; German tours | Duel rival (BOSS-08), later GST-10; private returns Dec 1833 (SQ-20) and Feb 1834 (CH-E2) | CH-07 | **Y**: private Paris visits; the early "three-hand" device (R-10) |
| NPC-03 | Jacques Offenbach | 20 Jun 1819 – 5 Oct 1880 | 13 → 14 | Cologne; Paris from Nov; admitted 30 Nov | Comic guest (GST-08) | CH-12 | **Y** (minor): Opéra pit |
| NPC-04 | Robert Schumann | 8 Jun 1810 – 29 Jul 1856 | 22 → 23 | Leipzig; crisis 17–18 Oct | Guest, known only as "Florestan" (R-56). Min-jun tells him that Joseon's name means "morning freshness"; his letter, and later the *Neue Zeitschrift* (April 1834, the CH-E2 letter), call Min-jun **"Meister Morgen"** (*Morgen* is both "morning" and "tomorrow"; only Min-jun laughs at the second meaning) | CH-11 | **Y**: in Düsseldorf; incognito (R-56) |
| NPC-05 | Clara Wieck | 13 Sep 1819 – 20 May 1896 | 13 → 14 | Leipzig, touring | Guest (GST-04); the slip; meets Liszt and Czerny early (R-56) | CH-11 | **Y**: in Düsseldorf |
| NPC-06 | Friedrich Wieck | 18 Aug 1785 – 6 Oct 1873 | 47 → 48 | Leipzig | Clara's domineering father | CH-11 | **Y** |
| NPC-07 | Felix Mendelssohn | 3 Feb 1809 – 4 Nov 1847 | 24 | Düsseldorf (director from autumn) | Host (GST-05) | CH-11 | **Y** (minor): the academy |
| NPC-08 | Carl Czerny | 21 Feb 1791 – 15 Jul 1857 | 42 | Vienna | Liszt's old teacher (GST-06) | CH-11 | **Y** |
| NPC-09 | J.-A.-D. Ingres | 29 Aug 1780 – 14 Jan 1867 | 52 → 53 | Paris (*Portrait of M. Bertin*, 1832) | Academic foe of Lucile's art; the hostile juror whose verdict opens BOSS-32 at Favor −30 | CH-06 | N |
| NPC-10 | Paul Delaroche | 17 Jul 1797 – 4 Nov 1856 | 35 → 36 | Paris, painting *Lady Jane Grey*; Academician since 1832 | Louvre sceptic in CH-06; in CH-E2 the academician juror who is Lucile's swing vote (BOSS-32, SQ-11) | CH-06 | N |
| NPC-11 | Théodore Chassériau | 20 Sep 1819 – 8 Oct 1856 | 13 → 14 | Ingres's studio | Copies beside Lucile; her colour astonishes him, an artistic awakening that foreshadows his later turn from Ingres toward Delacroix. Never a crush (he is 13–14) | CH-06 | N |
| NPC-12 | Horace Vernet | 30 Jun 1789 – 17 Jan 1863 | 43 → 44 | Rome, Villa Medici; official mission to Algeria (Bône, Algiers), May–Jun 1833 | Gala guest of honour; spots a Delorme formula | CH-13 | **Y**: Paris leave (R-23) |
| NPC-13 | Camille Corot | 16 Jul 1796 – 22 Feb 1875 | 36 → 37 | Paris / Fontainebleau | Plein-air peer to Lucile (GST-03): "You paint as I dream" | CH-10 | N |
| NPC-14 | George Sand | 1 Jul 1804 – 8 Jun 1876 | 28 → 29 | Paris, 19 quai Malaquais; leaves for Italy 12 Dec | Lucile's elder-sister friend (GST-02); never shares a scene with Liszt, Delacroix or Chopin (§16e) | CH-06 | **Y** (minor): Nohant in Oct (R-17) |
| NPC-15 | Camille Pleyel | 18 Dec 1788 – 4 May 1855 | 44 → 45 | Pleyel & Cie, 9 rue Cadet | Piano maker; Voicing; Théo's master | CH-05 | N |
| NPC-16 | Friedrich Kalkbrenner | Nov 1785 (date uncertain) – 10 Jun 1849 | 47–48 | Paris, Pleyel's partner | Pompous pedagogue; offers Min-jun "three years of lessons" | CH-05 | N |
| NPC-17 | Luigi Cherubini | 14 Sep 1760 – 15 Mar 1842 | 72 → 73 | Director, Conservatoire, rue Bergère | Throws Min-jun out (CH-02); grudging respect; admits Offenbach | CH-02 | N |
| NPC-18 | Marie d'Agoult | 31 Dec 1805 – 5 Mar 1876 | 27 | Paris salon | Liszt's love; where Liszt is met | CH-05 | N |
| NPC-19 | Harriet Smithson | 18 Mar 1800 – 3 Mar 1854 | 32 → 33 | Paris; leg broken 16 Mar | Berlioz's bride | CH-03 | N |
| NPC-20 | Aristide Farrenc | 9 Apr 1794 – 31 Jan 1865 | 38 → 39 | Paris, publisher and flautist | Opus Score shop; Théo's *tuteur* (SQ-07) | CH-08 | N |
| NPC-21 | Victorine Farrenc | 23 Feb 1826 – 3 Jan 1859 | 7 | Paris | Farrenc's daughter, young pianist | CH-08 | N |
| NPC-22 | Niccolò Paganini | 27 Oct 1782 – 27 May 1840 | 50 → 51 | Touring; Paris in Dec | Legend in talk; attends the 22 Dec concert; BOSS-36 is an Echo of his legend, not the man | CH-E2 | N |
| NPC-23 | Louis-Philippe I | 6 Oct 1773 – 26 Aug 1850 | 59 → 60 | Tuileries | Vendôme ceremony; royal box at the gala; never complicit | CH-06 | **Y**: invented gala |
| NPC-24 | Henri Gisquet | 14 Jul 1792 – 23 Jan 1866 | 40 → 41 | Prefect of Police (1831–36), rue de Jérusalem | Clears Min-jun (CH-04); compromised by Archon; arrests Delorme (Seoul branch) | CH-04 | **Y**: ties to Archon |
| NPC-25 | Comte de Rambuteau | 9 Nov 1781 – 23 Apr 1869 | 51 → 52 | Prefect of the Seine from 22 Jun | Civic ambience; clean-water scene; the dirigible-permit gag | CH-05 | N |
| NPC-26 | Cristina Belgiojoso | 28 Jun 1808 – 5 Jul 1871 | 24 → 25 | Paris, in exile; charged with treason by Vienna, fortune confiscated | Tier-4 patron; judges the BOSS-35 rematch in her own salon; vows to host the real duel (R-10) | CH-14 | N |
| NPC-27 | Count Antal (Anton) Apponyi | 7 Dec 1782 – 17 Oct 1852 | 50 → 51 | Austrian ambassador, Paris | Duel host | CH-07 | N |
| NPC-28 | Countess Thérèse Apponyi (née Nogarola) | 1790 – 1874 | ~43 | Paris salon | Hostess; Chopin later dedicates Op. 27 to her | CH-07 | N |
| NPC-29 | Ferdinand Hiller | 24 Oct 1811 – 11 May 1885 | 21 → 22 | Paris | Chopin's and Liszt's friend; the 15 Dec Bach concert | CH-05 | N |
| NPC-30 | Heinrich Heine | 13 Dec 1797 – 17 Feb 1856 | 35 → 36 | Paris since 1831 | Salon wit ("the Nightingale of Nowhere"); press rebuttals | CH-05 | N |
| NPC-31 | Alfred de Musset | 11 Dec 1810 – 2 May 1857 | 22 → 23 | Paris; with Sand from June | Sulky cameo | CH-06 | N |
| NPC-32 | Victor Hugo | 26 Feb 1802 – 22 May 1885 | 31 | Paris, Place Royale | Watches the riot from his window | CH-04 | N |
| NPC-33 | Gioachino Rossini | 29 Feb 1792 – 13 Nov 1868 | 41 | Paris | Gourmand guest of honour at the embassy; judges the Thalberg duel (R-10) | CH-07 | N |
| NPC-34 | Giacomo Meyerbeer | 5 Sep 1791 – 2 May 1864 | 41 → 42 | Paris | Gala guest | CH-13 | N |
| NPC-35 | François-Antoine Habeneck | 22 Jan 1781 – 8 Feb 1849 | 52 | Opéra conductor | Yields his podium to Berlioz, sulking | CH-13 | N |
| NPC-36 | Louis Véron | 5 Apr 1798 – 27 Sep 1867 | 34 → 35 | Opéra director | Gala impresario | CH-13 | N |
| NPC-37 | Marie Taglioni | 23 Apr 1804 – 22 Apr 1884 | 28 → 29 | Paris Opéra | Her *Sylphide* interlude covers the rafters fight | CH-13 | N |
| NPC-38 | Adolphe Nourrit | 3 Mar 1802 – 8 Mar 1839 | 31 | Paris Opéra | Gala tenor | CH-13 | N |
| NPC-39 | Narcisse Girard | 27 Jan 1797 – 16 Jan 1860 | 36 | Paris | Conducts the 22 Dec concert | CH-E2 | N |
| NPC-40 | Count Rudolf Apponyi | 1802 – 1853 | ~31 | Embassy attaché and diarist | Why the duel "isn't recorded" | CH-07 | N |
| NPC-41 | Maurice Schlesinger | 3 Oct 1798 – 25 Feb 1871 | 34 → 35 | Publisher of Chopin's Op. 10 and of the Chopin–Franchomme *Grand Duo* (July 1833) | Second Opus vendor; plans the *Gazette musicale* | CH-06 | N |
| NPC-42 | Henri Herz | 6 Jan 1803 – 5 Jan 1888 | 30 | Paris | Salon cutting contest (BOSS-03) | CH-03 | **Y** (minor): the contest |
| NPC-43 | Honoré Daumier | 26 Feb 1808 – 10 Feb 1879 | 25 | Released from Sainte-Pélagie early 1833 | Sketches the riot; witness for Min-jun | CH-04 | N |
| NPC-44 | David d'Angers | 12 Mar 1788 – 5 Jan 1856 (some sources say 4 Jan) | 44 → 45 | Carving the Panthéon pediment | Lets the party up the scaffold | CH-15 | N |
| NPC-45 | Marie Moke-Pleyel | 4 Sep 1811 (some sources 4 Jul) – 30 Mar 1875 | 21 → 22 | Paris, pianist | Berlioz's ex-fiancée: a comic-awkward scene | CH-05 | N |
| NPC-46 | Auguste Franchomme | 10 Apr 1808 – 21 Jan 1884 | 24 → 25 | Paris, cellist; Touraine with Chopin in Aug 1833 | Chopin's friend who takes him to Touraine (R-57); the *Grand Duo* is a flavour item; Offenbach's idol | CH-06 | N |
| NPC-47 | Adolphe Thiers | 15 Apr 1797 – 3 Sep 1877 | 35 → 36 | Minister of Commerce and Public Works | Delacroix's patron (Salon du Roi commission) | CH-10 (mention), CH-13 | N |
| NPC-48 | Anna Liszt | 28 May 1788 – 6 Feb 1866 | 44 → 45 | Paris, rue de Provence (no. 61; earlier 7 bis rue de Montholon, 1827; the appendix confirms the year of the move) | Liszt's mother, warm and practical | CH-07 | N |
| NPC-49 | Nicolas-Joseph Franck | 1794 – 1871 | ~39 | Liège | César's driving father | CH-11 | N |
| NPC-50 | Solange Dudevant | 13 Sep 1828 – 17 Mar 1899 | 4 → 5 | Paris / Nohant | Child cameo at Nohant | CH-10 | N |
| NPC-51 | Wilhelm von Schadow | 6 Sep 1788 – 19 Mar 1862 | 44 → 45 | Düsseldorf, director of the Academy | Bought the Seventh Panel *Ad Astra* in 1832 as "a curious French allegory"; sells it to Brücke's agents on forged export papers (CH-11) | CH-11 | N (the panel is fictional) |
| NPC-52 | Comtesse Merlin (María de las Mercedes Santa Cruz y Montalvo) | 5 Feb 1789 – 31 Mar 1852 | 44 | Paris, hostess of a famous musical salon | Tier-3 salon hostess (Taste: Romantic) | CH-07 | N |
| NPC-53 | Casimir Dudevant | 9 Jul 1795 – 8 Mar 1871 | 37 → 38 | Nohant | Sand's husband: one cool, polite Nohant dinner; away at La Châtre market on the night of the attack | CH-10 | N |

---

## §8 The Anachronists

**Name:** *La Confrérie de l'Heure Immobile*, the **Brotherhood of the Stilled Hour**. "Anachronists" is Min-jun's word (CH-06); the party adopts it, Archon sneers at it, then uses it himself in CH-12.
**Sigil:** a clock face whose two hands are fused into a single upright **key** at XII, ringed by seven dots (the Clefs). Archon copied it in 2012 from the bow of the **Ornate Brass Key** (KEY-01), which hangs by its bow from a brass hook on the Hidden Study's music stand; the friends, in 1834, designed that key's bow after the cabal's sigil (a closed loop, LAW-16). The player sees the key in CH-P, so the first sight of the sigil (CH-03, Vane's signet) is a jolt of recognition. Members wear black-enamel **binding rings** bearing it (Stasis, LAW-11). Julien keeps his in a pocket and has never put it on.

**Hierarchy:** **Archon** (*le Premier*) commands four **Hours**: the Hour of Velvet (Vane: society, patronage, press), the Hour of Gold (Delorme: art, Clef science, the tablature), the Hour of Iron (Brücke: machines, automata, the Engine) and the Hour of Smoke (Julien: cafés, rumour, informants). **Sœur Marthe** is the **Almoner**: the cabal's physician, no vote. Operatives: the **Grey Hand**, about 40 veterans of the Garde royale, which was disbanded after July 1830, under Commandant Roussel (FIC-08, a former Garde royale captain); they wear grey greatcoats and a single grey kid glove on the right hand, hence the name. The **Black Coats**: Captain Marlot's (FIC-07) day-hire bruisers, hired by Vane, in black frock coats bought from the same old-clothes dealer, cheap imitation gentlemen. Also Brücke's automata, paid clerks and footmen.

**The Pact of the Hour (sworn 21 Jun 1826):** (1) never go home; (2) never reveal **that you come from the future** to a native; (3) never harm another traveller. Archon breaks the third rule in 1833: Min-jun "is not one of us until he chooses to stay". It mirrors the friends' **Pact of the Door** (LAW-22): one pact hides a door, the other builds one.

**The two motives (A-1), shared by all members:**
1. **Exposure in 1833.** Min-jun's future performances and slips (words, objects, knowledge) invite scrutiny of every "prodigy" in Paris, them included.
2. **Exposure of the portal in 2026.** If he returns, he is living proof of the doorway. Two disappearances from one Seoul building (Archon 2012, Min-jun 2026), a physical Door and a witness would bring police, scientists and press. The Door could be studied, guarded, shut or **used** from the future side, and the archives searched for "impossible" prodigies, uncovering their names, works and hiding places. Brücke has *seen* this happen (LAW-14). Their secret survives only if Min-jun never goes home.

**Internal tensions:** (1) **Delorme vs Archon.** She found the Clefs and he took the network from her; in revenge she secretly "sold" tablature Panel VII to the Düsseldorf Academy in 1832 to hold the seal hostage (drives CH-11). (2) **Soft vs hard faction.** Vane and Julien want Min-jun managed; Brücke wants him dead from the first day; Archon wants him alive until the signature is fully recorded (LAW-12), and, once the recording proves partial, alive for the solstice. (3) **Archon vs Vane.** Vane's unsanctioned frame-up made Min-jun a hero; Archon despises Vane's vanity, Vane fears being sacrificed first. (4) **Brücke's secret.** In the history he remembers, Archon vanishes from the record in December 1833. He has never told Archon. (5) **Marthe vs Archon.** Medicine against power; she is overruled on using sick Théo as leverage, and the third rule's breach turns her.

**What the cabal knows about Min-jun, and when (binding).** CH-01: a traveller named Kang will arrive on 5 Mar 1833, place unknown (Brücke's dossier). CH-02: Julien connects the rumour of "the Oriental pianist". CH-03: Vane is certain ("Ondine"). CH-06: Lucile reports the word "Seoul", which proves to Brücke that this is the Kang of his dossier; Brücke begins his private lethal escalation (rung 8). The cabal never needs the Secrecy Meter to identify him: the meter tracks the future leaking into public view (LAW-17).

**Who knows the full seal (binding).** That the seal binds Min-jun into the Heart forever as the living string and kills every far end is known to **Archon, Delorme and Brücke** since 1832. **Marthe** learns it in CH-11, and it turns her. **Vane** learns it at Archon's Revelation (CH-12), protests, and defects in CH-14. **Julien** never learns it before he turns (CH-09). Vane's ledger (KEY-16) holds the Clef map, Panel VII's location and "L. — to be removed", **never** the living-string clause: the party hears that clause only from Archon, in CH-12.

### §8a Roster: identity

| ID | Title / 1833 alias | Real name | Origin | Arrived (far end) | Body / lived age, Dec 1833 | Cover |
|---|---|---|---|---|---|---|
| ANA-01 | **Archon** / Baron Lazare d'Orsenne | Dr. Lazare Morvan (b. 2 Feb 1969, Rennes) | Seoul, 21 Jun 2012: visiting professor of acoustics at Hanseong | 21 Jun 1819 (Seoul Door → Clef I) | 47 / 57 | Industrialist, ironmaster and arms patentee (Forges d'Orsenne; Château d'Orsenne near Fontainebleau), Peer of France, benefactor of Val-de-Grâce |
| ANA-02 | **Vane** / Lord Adrian Vane | Adrian Vane Holloway (b. 3 May 1951, London) | London, 19 Nov 1988: auctioneer of 19th-century French art | 19 Nov 1827 (London Stone → Clef V) | 39 / 43 | English milord, collector and patron; Hôtel de Vane, rue de Varenne |
| ANA-03 | **Julien** / Julien Marchetti, "le Sorcier des accords" | Julien Marchetti (b. 14 Apr 1922, Paris-Belleville) | Paris, 28 Jul 1950: cellar-club session pianist | 28 Jul 1830 (Clef V in situ) | 31 / 31 (never bound) | Café-concert and salon improviser, Palais-Royal |
| ANA-04 | **The Painter** / Mme Isaure Delorme | Dr. Hélène Varga (b. 9 Oct 1899, Budapest) | Paris, 31 Mar 1934: mathematician at the Institut Henri Poincaré | 31 Mar 1814 (Clef V in situ): the first traveller | 44 / 54 | Popular history painter, Salon medals 1822 and 1827, church commissions; atelier on the Île Saint-Louis |
| ANA-05 | **The Watchmaker** / Maître Anselm Brücke | Elias Brandt (b. 30 Jan 2012, Geneva) | Seoul, 2 Nov 2049: deserter field engineer of the Chronometric Survey | 2 Nov 1831 (Survey-tuned Seoul Door → Clef I) | 38 / 39 | Swiss watchmaker, Horlogerie Brücke, rue de la Paix |
| ANA-06 | **Sœur Marthe** | Marthe Lenoir (b. 14 Mar 1893, Amiens) | Paris, 11 Nov 1918: army nurse in the Val-de-Grâce vaults on Armistice night | 11 Nov 1822 (Clef II in situ) | 31 / 36 | Daughter of Charity running the free dispensary at the Val-de-Grâce gate |

### §8b Roster: motives, threat, fate

| ID | Introduced / stole | Why he/she won't go home | Personal stake in the portal secret | Red line | Rungs carried out (§4c) | Combat style | Bosses | Fate: Seoul branch / Paris branch |
|---|---|---|---|---|---|---|---|---|
| ANA-01 | Arms and machine patents through front men (rifled-barrel tooling, puddling refinements, semaphore codes); counter-insurgency doctrine sold to the War Ministry; leverage over Gisquet; the seal plan | In 2012 a footnote; here he steers a kingdom, and the seal promises an immortal reign | He vanished from the **same Door**: a returning Min-jun ties the two cases together, the study is opened, and a future that can reach 1833 can "correct" his empire | None | 9, 12, 15 (orders 10, 11, 13, 14) | P1 sabre and *Tactics* (Grey Hand formations, row shuffles); the Engine (space warps); CHRONO | BOSS-16, 26, 28 | Both: held forever in one endless second inside the collapsed Stilled Hour; a living statue in the Dead Heart (visitable in CH-E2 only) |
| ANA-02 | Art-market foreknowledge (bought Corot and Delacroix sketches cheap); a 1988 **Walkman with five mixtapes** | Prison in 1988; here he is loved | "They would extradite me from *history*": his collection becomes evidence | **Will not kill**; refuses outright to harm Lucile | 2, 3, 5, 7 | Former Cambridge sabre blue; *Wager* (bets his Composure against the party's Crescendo); Riposte | BOSS-20 (proxies BOSS-05, BOSS-08) | Both: defects CH-14 and sails for England Mar 1834. Seoul only: testifies against Delorme (the ledger goes to Gisquet, LAW-24) |
| ANA-03 | Extended chords, modal vamps, quartal voicings transcribed from Vane's tapes | In 1950 he was nobody and his mother was dead | Exposed as "the Paris jazz hoax" | **Will not kill**: thought the rigged piano would only break | 1, 4, 6, 8 | The **Phantom Quartet** (spectral bass, drums, sax, piano); Swing status; Blue Note crits | BOSS-11 | Turns in CH-09; recruitable (PC-11). Seoul: stays in 1833; his waltz "pour M." (1851) lies in the Jeong-dong box. Paris: opens *Le Diapason Bleu* (Jan 1834) |
| ANA-04 | Cinematic composition, ground modern lenses, photographic tonal values; the **tablature** (seven formula panels, LAW-08) | In 1934 no one would let her be a genius; here she is a painter, a bitter half-victory | Her canvases become evidence and she becomes a cheat in the record; she wants discovery on her own terms | Will kill to protect her legacy; **never a child** (keeps Théo fed and warm) | 3, 11; author of 15's tablature | **Golden Section** geometry; *Vanishing Point* (traps a member in perspective); Living Tableau summons; formula wards that rewrite stats | BOSS-15, 33 | Seoul: arrested 23 Dec 1833 on the ledger's evidence (Théo's abduction); dies 1841 in Saint-Lazare. Paris: free (the friends keep the ledger out of court, LAW-25) until defeated at the Salon of 1834; flees to Budapest ahead of a warrant |
| ANA-05 | Memory-metal springs and synthetic alloys; automata; **phonautograph horns** (recording sound 24 years before Scott); the dirigible *La Sourdine*; the crank dynamo; **the Engine**; Roussel's rifle | A deserter: his own future would "remediate" him | Total: he knows the date Min-jun vanished (the cabal *knew he was coming*) and has seen the Disclosure. If Min-jun returns, Brücke's world begins and his executioners are born | **None toward Min-jun**; never a child | 4, 7, 8, 10, 11, 13, 16 | **Escapement** (ticks ATB backward), Fermata, automaton summons, *Last Hour* countdown | BOSS-09 (device), 13, 14, 18, 29, 30 | Seoul: dives through the collapsing Window; defeated in the Hidden Study, where his oscillator shatters; freed by Min-jun's promise; vanishes into the New Year crowd. Paris: stays, burns his Survey dossier with Min-jun and surrenders the last oscillator (SQ-23); d. 1871 |
| ANA-06 | Boiled water, quarantine, oral rehydration: she saved several hundred lives in 1832 | Her patients need her | Believes a future that finds the portal would "correct" history and her patients would die as they "should" have (she is wrong: LAW-15) | **Absolute no to violence**; opposed using a sick child | None; unknowingly provides the Théo leverage, then betrays it | Healer (GST-09) | — | Both: defects after the Opéra; keeps her dispensary. Seoul: receives Min-jun's letter asking her to watch over Théo. Paris: becomes the Aubray-Kangs' physician |

### §8c Dossier notes (writers elaborate in anachronists.md)

**ANA-01 Archon.** A brilliant French acoustician told in 2012 that he would never be more than a footnote. While surveying an "acoustic anomaly" under the Hanseong annex he found the Hidden Study, studied the Door for weeks (hanging the key back on its hook on the music stand each night), and on 21 Jun 2012 it rang with Delorme's 1819 strike and he walked through. Creed: "History is a score badly conducted. I have read the twentieth century. I will conduct this one." He needs Min-jun **alive** as the seal's living string until his signature is fully recorded (LAW-12), then dead; the partial recording of CH-13 keeps Min-jun's life useful to him to the end. Married a widow in 1825; son b. 1827. His **Testament of the Stilled Hour** (KEY-35, written 20 Dec 1833) has an open Charge (fund a foundation, dig at Jeong-dong when Korea opens, keep the sealed room shut) and a sealed Codicil for December 2026 ordering his heirs to discredit or silence "a young Korean who will come out of the cellar". Voice: courteous, slow, utterly certain. One scene where the player understands him: CH-12, the footnote speech. He lets the party leave Val-de-Grâce on purpose: the Heart is Min-jun's only door home, so the boy must come to it on the solstice, and the gala will record his signature first.

**ANA-02 Vane.** A charming London auctioneer running a forged-provenance ring. The night before his 1988 arrest he touched a "singing stone from the Paris catacombs" at a Mayfair viewing (the London Stone). He recognised "Ondine" because he once catalogued a Ravel autograph. He devised the Velvet Leash, recruited Lucile, and staged the barricade frame-up without sanction. He protests the abduction, refuses Archon's order to kill Lucile (CH-14) and defects. Understood in CH-14: he reads her early reports and says, "She stopped being mine long before she stopped writing."

**ANA-03 Julien.** A sideman in the Saint-Germain-des-Prés cellar clubs who got lost at a 1950 catacomb party and woke during the July Revolution. His "lack of original talent" is doubly literal: he passes off music he never heard in his own life. Brücke secretly changed the Pleyel tensioner spec from "snap" to "lethal"; that betrayal turns Julien (CH-09). Arc: fear → courage; he reveals Lucile's role, and plays beside Min-jun if recruited.

**ANA-04 The Painter.** A Budapest-born mathematician measuring anomalous acoustics in the catacombs in 1934 as Europe closed around her. She mapped the Clefs, wrote the resonance equations, struck the network in 1819 (drawing Archon) and lost it to him. After CH-06 she demands that Lucile's canvases be burned. Her CH-12 line frames Min-jun's reckoning: "You gave a girl Monet and you call *me* a thief?"

**ANA-05 The Watchmaker.** A field engineer of the Chronometric Survey who refused to take part in the 2048 Remediation Directive's killings and fled through the Survey-tuned Door with a field kit (nitinol, carbon filament, a solid-state slate that died in 1832) and the Survey's dossier on the cabal, compiled from Min-jun's 2027 testimony in Brücke's history. Irony: in his history no record names a painter Lucile Aubray; Théo Aubray appears only as the Pleyel technician who escorted the crate. The leash he opposed is what prevents his future, and the Engine he built is what kills the portal (LAW-14).

**ANA-06 Sœur Marthe.** A nurse from the last weeks of the Great War who stepped into the Val-de-Grâce vaults on Armistice night and has never stopped working. She treats Théo in good faith while Vane pays; when Delorme imprisons Théo in the abbey next door (CH-11) she secretly helps Lucile (CH-12) and defects after the Opéra (CH-13). She is the positive mirror of "Gift, Not Theft": the future given away, for no credit.

### §8d The heroine's recruitment (A-2)

| Item | Canon |
|---|---|
| Recruiter | **Vane**, in Maison Corbel's back room, **Sun 28 Apr 1833** (the day after the Lavergne salon) |
| Champion / opponents | **Championed** by Vane ("a leash of silk, not iron"). **Approved** by Archon ("cheaper than a bullet, and it keeps him alive and near"). **Opposed** by Brücke ("an unknown variable"; his "in my history there is no Lucile Aubray" is recalled only inside the CH-12 2049 scene, LAW-14 cap) and by Marthe ("you will use a sick child?"). **Scorned** by Delorme ("a girl who paints fans") until CH-06, when she sees the canvases and turns vicious. Julien is uneasy and silent until CH-09. |
| Leverage | Vane bought Gilles Aubray's **1,200 F** of debts from Maison Grimaud and the landlord (threat: seizure and eviction); pays for Théo's care at Sœur Marthe's dispensary; promises an introduction to the **Salon of 1834** and a purchase; a 50 F monthly "stipend for materials". |
| What she was told | "A fragile foreign prodigy who speaks of a voyage home that would kill him. His friends in society want him safe in Paris. Befriend him; make Paris dear to him; tell me whom he meets, what he says of his origins, and above all whether he speaks of leaving, or of a 'door'." She is **never told about time travel** (the cabal's secrecy motive forbids it). At first she believes she is protecting him. |
| What she reports | Weekly letters left with M. Corbel, which Vane files under the code name **"Lumière"** (taken from Sand's pet name for her, which she once mentioned): his meetings, moods, quarry searches (→ rung 6), and the word "Seoul" (→ Brücke's confirmation, CH-06). Every confidence shared during CH-05–CH-08, up to the charity concert of Sat 21 Sep, is reported (§11f). **Exception:** if he gave her the Early Truth, she never writes it down. |
| When and why she turns | Begins **Sat 21 Sep 1833** (CH-08): she sees Vane's people meant to hurt him and sends a false report ("He has given up any door"). Decisive on the night of **3–4 Oct** (CH-09): told of the abduction by a panicked Corbel, she breaks into the Hôtel de Vane, steals **Vane's ledger** (KEY-16), and sends Petit-Louis with the address to Berlioz's wedding supper. At dawn she confesses and gives Min-jun the ledger. |
| Cabal reaction | Brücke detects her false report of 21 Sep. On **Mon 30 Sep** Archon orders her removed. Vane quietly refuses but records the order in his ledger ("L. — to be removed", dated 30 Sep 1833). Lucile steals the ledger on 3–4 Oct without seeing that page; Farrenc finds it in CH-10. After the theft Archon renews the order, citing both the stolen ledger and "the future hung in a shop window on rue Dauphine" (LAW-21), and Brücke's automata attack Nohant (CH-10). Delorme seizes Théo from Marthe's dispensary and burns five of her canvases (CH-11). Lucile frees Théo herself (CH-12). She is targeted again in the Opéra rafters (CH-13). Archon orders Vane to kill her (CH-14); Vane defects; Roussel's cleaners come for both. |

---
## §9 Laws of Time & Lore

### §9a The mechanism

**LAW-01 Rifts.** A rift is a *resonant knot* tying a moment in the future to a moment in the past, as two strings tuned alike make each other sing. It appears as a door-shaped seam of light humming at one pitch. Rifts are heard before they are seen, which is why a musician notices them.

**LAW-02 The Clefs (the "forgotten spatial anchors").** Seven nodes of naturally resonant limestone ("singing stones") lie in the quarries under the Left Bank. Around 1250 the quarrymen-monks of the Abbey of Sainte-Geneviève (the *Frères des Sept Pierres*) shaped them into plinths carved with a clef-like mark, then forgot them. Delorme rediscovered them in 1814. Travellers did not make them.

| Clef | Name | Beneath | Delorme tablature panel above it (hidden formula) |
|---|---|---|---|
| I | The Crypt | Saint-Denis Galleries / old Notre-Dame-des-Champs (Seoul Door arrivals) | *The Martyrdom of Saint Denis* (Schrödinger equation) |
| II | Val | Val-de-Grâce | *The Vow of Anne of Austria* (E = mc²) |
| III | Geneviève | Saint-Étienne-du-Mont | *Sainte Geneviève Watching over Paris* (Maxwell's equations, vector form) |
| IV | Urania | The Observatoire | *Urania Measuring the Heavens* (Einstein field equations) |
| V | Enfer | Barrière d'Enfer ossuary | *Orpheus Descending* (Dirac equation) |
| VI | Polytechnique | École Polytechnique, Montagne Sainte-Geneviève | *Archimedes at Syracuse* (Lorentz factor) |
| VII | **The Heart** | Beneath the Panthéon | *Ad Astra* (her own Varga resonance equation, signed "H.V. 1934"); sent to Düsseldorf in 1832 |

**The Mouth and the Heart.** Clef I and the Heart were cut from one bed of stone; the Frères called them the Mouth and the Heart. What the Heart sends, it receives through the Mouth: Seoul Door arrivals (whose far end is a shard of the Heart) surface at Clef I, and returns leave from the Heart.

**LAW-03 Far ends and pitches.** On the future side a rift opens wherever a **fragment of Clef stone** lies (in situ or carried away). Each has a fixed **offset** in years, set when it was cut and never chosen. Known: **Clef V in situ** (120 y: Delorme 1934→1814, Julien 1950→1830); **Clef II in situ** (96 y: Marthe 1918→1822); the **London Stone**, carried off by a quarryman in 1786 (161 y: Vane 1988→1827); the **Seoul Door**, whose dial holds the Heart's largest shard (193 y: Archon 2012→1819, Min-jun 2026→1833). Only in Brücke's remembered history was an offset ever re-tuned (218 y), by the Survey.

**LAW-04 Opening and resonance.** A rift opens only when the Paris network **rings**: through a mass upheaval in the city (a *Resonance Date*: invasion, revolution, riot) or deliberate striking. (Sole exception: Brücke's 2049 crossing, forced from the future side by the Survey's re-tuned Door.) Every far end whose offset maps onto that instant opens (a passable **window**) for a few minutes. **Resonance:** a crossing leaves the traveller's far end **resonant** (latently open, not passable) for a year and a day, or until a binding ring damps it. Only while resonant does it carry a recordable signature (LAW-12) and qualify as a living string (LAW-10). In Dec 1833 only Min-jun's is resonant: Julien's (Jul 1830) has faded and Brücke's was damped by his ring (Jan 1832). "Window" always means the physical opening; "resonant" the latent state. **5 Mar 1833, 14:49:** Brücke's Survey dossier said Kang Min-jun vanished at 23:40 KST on 5 Mar 2026. Archon timed his first seal test to strike the Heart at that instant to smother the Seoul Door; the strike opened it instead. **The cabal's own act brought Min-jun.**

**LAW-05 Arrival, the Passage Swoon, and return.** A crossing through a struck or collapsing rift costs 2–4 hours of unconsciousness (the **Passage Swoon**). A crossing through a **held** Window (kept open by music, LAW-13) costs no Swoon. Arrivals wake within a few hundred metres of the Clef their far end is tuned to (Seoul Door → Clef I; Clef V in situ and the London Stone → Clef V; Clef II in situ → Clef II), never exactly on it, which is why the Grey Hand searched the Crypt galleries and Mathurin found him first. **To return**, a traveller must stand at the Heart when it is struck at their own fragment's pitch; a window then opens at their far end for minutes. Only living people and what they carry or throw can pass. Every cabal member except Brücke (whose re-tuned far end will never exist in this history) *could* have gone home this way through Archon's control of the Heart. They refused.

**LAW-06 Same date, same clock.** The two ends are linked at the same calendar date and the same UTC clock time, a whole number of calendar years apart (the fragment's offset). Time then runs at the same rate on both sides, so local clocks differ only by time zone (Paris mean time UTC+0:09:21; KST UTC+9). Min-jun left at 23:40 KST, 5 Mar 2026 (14:40 UTC) and arrived at 14:49 Paris time, 5 Mar 1833. The Window at Paris sunrise, 07:51 on 22 Dec 1833, opens at 16:41 KST on 22 Dec 2026: Paris dawn on one side, Seoul's low winter afternoon on the other. He is missing in Seoul for exactly as long as he lives in Paris (291.7 days): neither Mar–Dec 1833 nor Mar–Dec 2026 contains a 29 February. **No canon crossing or stay spans a 29 February.**

**LAW-07 Echoes (the monsters).** A strong ring imprints the city's recent grief, fear and noise onto stone and shadow as semi-solid **Echoes** (Ossuary Echoes, Miasma Wraiths, Tocsin Echoes (gunsmoke and alarm-bell shapes, never people), Gargoyle Echoes, Tableau Echoes). They are **recordings, not souls**, and never take the shape of the dead (§16e); defeating them harms no one. Area rosters in §12. They strengthen with Archon's experiments and fade after the network dies; only residual Echoes remain near the Dead Heart (CH-E2), and the Engine's last oscillator breeds "static" automata in 2026 (CH-E1). Other foes are automata, animals and humans; humans are always routed, subdued or arrested.

**LAW-08 Tablature.** Delorme's seven panels tune the seven Clefs like pegs on an instrument the size of Paris (pigment ground from Clef stone plus the hidden equations). Without Panel VII the seal cannot close without a **living string**, which is why Archon needs Min-jun at the Heart. A Clef is **detuned** either by destroying its panel or by striking its plinth with one of Alkan's tuning forks (KEY-32); in CH-15 the parties strike the plinths.

**LAW-09 The Engine (*Le Clavier des Âges*).** A synthesized piano built by Brücke (1832–33), with oscillators cut from Clef shards and a keyboard that strikes all seven Clefs as one chord. Its voice is the only synthesizer timbre in the score (§15a). **Look (binding):** a three-manual console of black iron and Clef limestone, 4 m wide; behind it seven pale stone oscillator columns, one per Clef, each glowing in its struck pitch; an iron-bar pedalboard; four phonautograph horns. In BOSS-28 Archon is wired into the bench by brass cables at spine and wrists, his sabre fused to the Left Manual.

**LAW-10 Sealing from the 1833 side.** At the winter-solstice instant (**00:43, 22 Dec 1833**; 00:33 UT) the Engine begins the **Stilled Hour** chord through the tablature using a living string: a traveller whose far end is currently resonant (LAW-04; in Dec 1833 only Min-jun's, opened by Archon's own test). The chord must hold about 7 h, from 00:43 to sunrise at 07:51. If it holds until sunrise, the network becomes a **closed loop**: every far end dies forever (no one can reach 1814–1833 again or go home), a standing wave holds near-total **Stasis** inside the old Farmers-General wall, and the living string is bound into the Heart, conscious and unageing, forever. "Trapping Min-jun forever" is literal.

**LAW-11 Stasis and ageing ("immortality").** A traveller wearing a binding ring ages at **¼ rate** inside the city wall and normally outside it (why the cabal sends Grey Hand and automata on the Act III roads). Archon, tied to the Engine since 1 Jan 1833, ages at **1/10**. Unbound travellers (Julien, Min-jun) age normally. When the network dies (22 Dec 1833) everyone ages normally from then on. Body ages in §8a follow this rule (rings from 1820 for Archon and Delorme, 1826 Marthe, 1828 Vane, 1832 Brücke).

**LAW-12 The signature.** Each resonant far end (LAW-04) leaves a resonance **signature** on its traveller that sounds when he performs with full commitment. Brücke's phonautograph horns can record it. A complete recording lets the Engine use a *recorded* string instead of the living man, and from that moment Min-jun alive is only a danger. Hence the abduction (CH-09: force a performance) and the Opéra trap (CH-13: record, then kill). At the Opéra, Min-jun and Liszt modulate mid-concerto and scramble the key, so the recording is **always partial** (at most 80%, KEY-23, BOSS-18), and Archon must bind him in person in CH-16.

**LAW-13 The death of the network and the Fleeting Window.** When the Octave breaks the Stilled Hour (BOSS-27) and the Engine collapses (BOSS-28), the half-struck chord folds inward onto Archon (his endless second) and **the Heart shatters**. Its largest shard falls into Min-jun's hand (KEY-29). The dying network rings once more, **at the pitch it was tuned to: Min-jun's signature**, so only the Seoul Door answers; the other fragments' pitches are never struck again, which is why no traveller can go home to his or her own time. Anyone standing at the Heart could step through to 2026 (Lucile does on the YES path; Brücke dives through as it collapses). Julien, if recruited and present, chooses to stay; Delorme, Vane and Marthe are not in the chamber. The Window opens at **Paris sunrise, 07:51, 22 Dec 1833**, as a rectangle of Seoul's winter light with snow falling upward, and stays open **only while music is played into the Heart's shards**: the friends play *La Musique des étoiles* on the Engine's ruined keyboard (its last oscillators still sound), Berlioz conducting, Alkan and Delacroix holding the oscillator lines. The coda lasts **12 minutes (07:51–08:03; 16:41–16:53 KST)**. Afterwards no rift can open to any moment after 22 Dec 1833, and the Seoul Door is a dead door from 16:53 KST, 22 Dec 2026. Brücke flees the collapse carrying the Engine's last oscillator.

**LAW-14 The Chronometric Survey and the Kang Disclosure (the A-1 fear made concrete).** Brücke remembers an *ossia* history (LAW-15) in which Min-jun returned **alone** in December 2026 and told police and press everything. Two disappearances from one building, a physical Door and a living witness led to: the site sealed by the state (2027) → the **Chronometric Survey** (Seoul–Geneva, 2031) → the shard re-tuned to chosen offsets (2040) → the **Remediation Directive** (2048): teams sent into the past to remove travellers and "restore the record". **Was the cabal right?** In Brücke's history, yes. There was no Engine: Archon's solstice seal, struck through the tablature alone, failed and cracked the Heart without shattering it. The spall that fell into Min-jun's hand became the Door's lock, the network survived Archon's fall, and the Door stayed tunable. Lucile never met Min-jun there (the Survey dossier has no entry for her); the friends and Théo still built the Door, because knots hold in every history (LAW-16). In this history, no: Brücke built the Engine, and its destruction killed the network completely; and Min-jun either keeps the secret (Seoul) or never returns (Paris). **The cabal was right to fear him and wrong to kill for it; the danger ended the moment they lost.** Brücke still hunts him in 2026 because he cannot verify that the Door is dead ("A dead door can be re-strung. I watched them do it.") and because testimony alone founded the Survey in his memory. **Screen-time cap:** 2049 material appears in at most four scenes (CH-07 hint, CH-12, the CH-E1 duel in the Hidden Study, the CH-E2 dossier) and never as more than 6 boxes of exposition at once.

### §9b History and ethics

**LAW-15 The Score and the Ossia.** History is written like a score. **Bar-lines** are heavily damped events attested by many independent records: wars, revolutions, epidemics, the births, deaths and major works of the famous, documented concerts and Salons. Attempts to change a bar-line are absorbed and events reroute to the same outcome (the April 1834 insurrection happens with or without the party; Berlioz marries Harriet on 3 Oct 1833; Chopin will die in 1849; Impressionism still arrives in the 1860s–70s). The 5 June 1833 riot is ossia: Vane caused it, and history forgets it. The **ossia** is the optional passage: attributions, unknown works, small and private lives. The ossia changes freely and all the travellers' thefts live there: Julien's songs fade, Delorme's canvases are later judged "eccentric" and many burn in 1871, Archon's patents are "strangely never adopted". Changes in the ossia are never "corrected" from the future. *The ethical sting:* the ossia is where ordinary people live. The "safe" changes rewrite real, small lives (Lucile, Théo, Petit-Louis, Marthe's patients). The game never says changing history is forbidden; it asks who has the right.

**LAW-16 Knots (closed loops).** Self-consistent loops with no origin are allowed and stable. Canon has exactly four: (1) **the Door itself**: built because Min-jun came, and he came because it was built (the Pact of the Door); (2) **the key's bow**: shaped in 1834 after the cabal's sigil, which Archon copied from that key in 2012; (3) **the plaque**, "Pour M., qui doit venir"; (4) **the Arrival**: Archon's 5 Mar 1833 strike was timed by a dossier that records the arrival the strike caused (LAW-04). The score's **blank last page** is part of knot (1): it must reach 2026 blank in both branches (LAW-22). **No branch may break a knot:** both epilogues must deliver the Door, key, score and plaque to Seoul by the route in LAW-22. Composers' works are never knots: no real person's documented work is ever given to them by Min-jun, and he never plays a composer's own future work to that composer (Tone Rule 7).

**LAW-17 Secrecy in fiction.** The cabal knows who Min-jun is (§8 knowledge timeline). What it cannot control is how much of the future he leaks into the public record. The Secrecy Meter (§11e) measures that leak: witnesses, press items, police reports and rumours that could make Paris, and one day the archivists of 2026, notice that the future is loose in 1833. The cabal reads it as risk to itself (motive 1) and to the portal (motive 2) and escalates as it rises; the Prefecture reads it as subversion. What the cabal learns it also uses: the Hour of Smoke turns Lucile's reports (until CH-08) and Watchers' sightings into rumour, so they too raise the meter. **The tiers name the city's attention, not the cabal's knowledge.**

**LAW-18 The Lantern Rule.** From CH-09 Min-jun keeps a rule: *tell friends who I am, never when they die.* Chopin asks; Min-jun answers, "You will be played every day for two hundred years." He does not warn Alkan of his decades of withdrawal. He does tell Farrenc she was forgotten and rediscovered, because that is legacy, not death; she fights harder, and the bar-line holds.

**LAW-19 Foreknowledge and the living.** Min-jun may use foreknowledge to save individuals (the ossia), never for profit. SQ-22 "Before April" (CH-E2): knowing the rue Transnonain massacre will happen on 14 Apr 1834, he cannot stop it (a bar-line), but persuades Mère Gaudin's cousin Rose Lambert (FIC-21) to move out of no. 12 in March. Told in text and a still image only (§16e).

**LAW-20 Gift and theft: Min-jun's reckoning and the Vow.** (1) **Credit.** In story performances Min-jun always names the real composer ("*Gaspard de la nuit*, by Maurice Ravel"); that honesty is what exposes him to Vane. At optional salons the player may choose the attribution (§11g): *name the composer*, *an old teacher's piece*, or the lie *my own*, which adds **Shadow** (0–10; feeds the Shadow Virtuoso phase of BOSS-31/34 and changes Delorme's, Farrenc's and Lucile's lines; never affects Horizon). (2) **Lucile.** Her early Impressionism is a deliberate change to history: he gave her an idea ("don't paint outlines"), not a canvas, and she transformed it, but he still changed a life and an art without anyone's consent. Delorme says so (CH-12), Farrenc says so (BQ-PC08), and he accepts it. Lucile's answer: "You asked me. They never asked anyone." (3) **The Vow** (voiced by Farrenc and Delacroix in CH-14, sworn there; the "my own" salon option disappears afterwards): **consent** (a person chooses to know), **credit** (the future's work is never claimed), **no harm and no profit** (no patents, no fortunes, no politics). His humility is the opposite of the cabal's vanity: in Seoul he tells it as music by default (Keeper's Choice (a), LAW-24); in Paris his face is hidden in the portrait.

**LAW-21 Lucile's canvases in history.** In 1833 she paints **24 canvases** in the new manner (11 IMPRESSION from Aug, 9 POINTILLÉ from Oct, 4 IMPASTO in Dec); Delorme burns 5 (CH-11). **In 1833 they are dangerous:** every public showing of a Lucile canvas is an Anachronic event (Heat 2–4) and draws a press item, and Archon's renewed CH-10 death order cites both the ledger and "the future hung in a shop window on rue Dauphine". Only later does history file the survivors as oil *esquisses*, a familiar category, so no bar-line moves. *Seoul branch:* the unsigned survivors scatter through Sand's and Corot's circles and are lost or misattributed; in 2026 one hangs in the "Light & Colour" exhibition as **"Circle of Corot, *Le Pont Royal, effet de brume*, c. 1833"** (lent by the fictional Musée de la Vallée Noire). She chooses not to claim it: "Let it be anonymous. It was a gift." *Paris branch:* she stops imitating the future by choice ("Then I'll paint something he won't") and grows LUMIÈRE, her own manner. She signs "L. Aubray"; her Salon of 1834 entry (KEY-40) is hung "au ciel" (skied); she lives to stand, smiling, before Monet's harbour at sunrise, the painting she chose not to take (BQ-PC02b), at the first Impressionist exhibition (15 Apr 1874), and dies in 1891. Art historians call her early sketches **"the Aubray Problem"**; the 2026 label reads "Lucile Aubray (1810–1891), *Le Pont Royal, effet de brume*, 1833".

### §9c The Hidden Study

**LAW-22 The Hidden Study and the Pact of the Door.** *What:* the sealed music-room cellar of the old **French legation in Jeong-dong**, preserved under Hanseong Conservatory's 1962 annex. *Who built it, and why (the mystery):* **"Les Amis"**, Min-jun's friends, under the **Pact of the Door**, sworn during the Window (CH-17) in both branches: "We will build you a door in Seoul, or you will never have come to us." *How:* Delacroix designed the Door in spring 1834; **Théo Aubray** cast its key in Pleyel's foundry that spring (his first brass casting) and carved its eight panels over his apprenticeship (finished 1841), showing the eight emblems (baton, brush, sword-cane, rapier, hammer, quill, sabre, folio). The Heart's largest shard (KEY-29, given to Delacroix in CH-17) is set in the clock-dial lock. The Door stood in Théo's workshop for 45 years while the friends each wrote one variation of the joint score *Harmonies de l'ère perdue*, its last page left blank "for M., who must come". In the Paris branch Min-jun plays his finale from memory on 1 Mar 1834 and never writes it down ("I saw it empty. If I fill it, I never came."), so the page stays blank in both branches (knot (1), LAW-16). In **March 1886**, during Liszt's last visit to Paris (he dies that July), the Door was crated with the score, the plaque, keepsakes and a sealed packet. Executors: **Liszt, Alkan and Théo** (Seoul branch); **Liszt, Théo and the elderly Min-jun and Lucile** (Paris branch). After the Franco-Korean treaty (4 Jun 1886), Théo, aged 67, escorted the crate to Seoul with Commissioner Collin de Plancy's party in **1888** as technician for the new mission's pianos. He installed the Door in the music-room cellar of the new legation building in **1896**, behind a counterweighted self-closing bookcase, with an 1880s Pleyel upright beside it and the portrait on the wall facing the Door. He died in Seoul on 3 Nov 1898 and lies at **Yanghwajin**. When the legation became a consulate general in 1906, the staff took the portrait down to protect it, packed it into Théo's crate with his papers "according to M. Aubray's written wishes" (the embargo), stored the crate in the adjoining storeroom and bricked up the cellar. *The 2026 room contains:* the Door; the **Ornate Brass Key** (KEY-01), hanging by its bow from a brass hook on the music stand; the score; the upright; the plaque **"Pour M., qui doit venir. — Les Amis, 1886"**; a dust outline where the portrait hung. *Clue schedule:* CH-P (all of the above); CH-05 (Pleyel's brass serial plates match the upright's); CH-07 (Théo whittles a little key shaped like fused clock hands); CH-09 (Delacroix sketches an emblem for each friend; the player recognises the panels); CH-12 (Archon: "Does the key still hang on the stand? It did in 2012"); CH-14 (Liszt: "If ever there must be a door, we will see to it"); CH-17 (the Pact; the shard; payoff); epilogue codas (crating in 1886; Théo at Chemulpo, 1888).

### §9d The ending (A-3)

**LAW-23 The Question.** In CH-17 Min-jun asks, "Will you come with me?" Her answer is computed, never picked from a menu.
1. **Gate:** **SQ-07 "Apprentice of Pleyel"** must be complete: Théo indentured to Pleyel; **Aristide Farrenc his *tuteur***, named by a ***conseil de famille*** before the *juge de paix*; **Louise Farrenc his guardian in fact**. (Code civil of 1804, art. 442, bars women other than the mother and female ascendants from any *tutelle* or family council, so neither Louise nor Lucile can hold it.) The Aubrays have no male relatives, so under art. 409 the justice seats men known as friends of the late father and of the family: Corbel, Delacroix (who bought frames from Gilles for ten years), Aristide Farrenc, Pleyel, Berlioz and Alkan. Min-jun, a foreigner without papers, cannot sit; he waits in the corridor with Lucile, whom the law bars from her own brother's council, and with Louise: "The law cannot see us. Then we shall be impossible to ignore." If the gate is unmet she **always** refuses: "I will not leave Théo with nothing." Lucile's worry icon marks the quest on the map from CH-07 to CH-14, and Sand's CH-14 farewell letter states the rule outright.
   **SQ-07 steps (binding):** (1) CH-07, automatic: Théo whittles the fused-hands key; Pleyel: "Bring him back strong." (2) Player: pay 300 F for Théo's convalescence at Marthe's dispensary (CH-07–CH-08, or CH-12–CH-14). (3) CH-08, automatic: restoring Chopin's Pleyel (KEY-17) earns Pleyel's offer of an indenture. (4) CH-12, automatic: once Théo is freed, Lucile consents. (5) Player, CH-14: the family-council session → KEY-31. Only steps 2 and 5 are up to the player, and both stay open until the Panthéon crypt door (§0c).
2. **Horizon** (hidden, −100…+100, starts at 0):

| Wings (+) | Value | Roots (−) | Value |
|---|---|---|---|
| W1 Early Truth given (§11f) | +15 | R1 Lesson choice "Ask what she sees" (L1–L4 below) | −5 each |
| W2 Window Talks (CH-10 Nohant fireside, CH-12 dome, CH-14 roof [mandatory], CH-15 amalgam) | +5 each | R2 SQ-11 The Jury completed | −15 |
| W3 Nohant answer "I loved the woman who painted rain" ("I don't know any more" = 0) | +10 | R3 Agree with Sand that "Paris needs her" (other answers 0) | −10 |
| W4 Lucile in Party 2 through the CH-15 Seoul amalgam zones | +5 | R4 SQ-12 The Atelier completed | −10 |
| W5 BQ-PC08 finale with Lucile present | +5 | R5 SQ-13 The Seine at Six Hours completed | −5 |
| W6 SQ-07 complete | +10 | R6 CH-10: Corot invites her to join him in Italy next spring (his real 1834 journey); Min-jun says "Go. Paint with him in spring." (−5) or "Spring is a long way off." (0), and she accepts or declines in reply | −5 |
| W7 Lesson choice "Tell of tomorrow" (L1–L4; binary with R1) | +3 each | | |
| **Max** | **+77** | **Max** | **−65** |

   **The four lessons (binding topics, places and lines):**

| Lesson | Ch. | Topic (place) | W7 "Tell of tomorrow" (+3) | R1 "Ask what she sees" (−5) |
|---|---|---|---|---|
| L1 | CH-06 | Reflections (Pont Royal) | "Painters to come will paint this bridge at every hour of the day." | "What do you see in the water, here, now?" |
| L2 | CH-07 | Broken Colour (Tuileries) | "They'll lay pure colours side by side and let the eye mix them." | "Mix it your way. What does Paris look like to you?" |
| L3 | CH-10 | The Field in Points (the Berry) | "One day a man will paint whole fields in points of light." | "Paint the Berry the way Sand tells it." |
| L4 | CH-14 | Night (Montmartre, before the Night of Stars) | "A Dutchman will paint the stars turning like this." | "Paint the sky you'll remember from this hill." |

   *Lesson rule:* neither option is "more respectful". W7 lines are written as shared wonder that she asks for (a window); R1 lines as shared looking at her own place (a mirror). Script both with equal warmth.
3. **Final words (CH-17):** "I want you beside me — there." (+5) / "Whatever you choose, I'm yours." (0) / "I want to see who you become here." (−5). They are phrased as feeling, never instruction; for most players the Horizon has already decided.
   **Menu labels** (each ≤ 22 characters, §16a; the full line is spoken after selection): final words "Beside me, there." / "Whatever you choose." / "Who you become here."; Nohant "I loved your rain." / "I don't know any more"; lessons "Tell of tomorrow" / "Ask what she sees"; Sand's counsel "Paris needs her." (the other answers' labels are set by secrecy_and_trust within the limit); Corot "Go. Paint with him." / "Spring is far off."
4. **Rule:** **YES** if the gate is met **and** Horizon + final ≥ +1. Otherwise **NO** (a tie gives NO).
5. **Signposting:** the last page of **Lucile's Sketchbook** (KEY-09; in Min-jun's keeping from the CH-09 dawn, viewable from the Sketchbook menu, §16h) shows one of five states: ≤ −30 Paris rooftops with Théo; −29…−5 the Pont des Arts at dawn; **−4…+5 an unfinished page** (the only band where the final words can still decide; Sand's CH-14 letter hints "your last words will matter"); +6…+29 a ship on a horizon; ≥ +30 "towers of glass in snow" imagined from his stories. **While the SQ-07 gate is unmet, the last page shows Théo asleep under a blanket whatever the Horizon**; it switches to the Horizon state when SQ-07 completes. From the CH-09 handover the page does not change until Mending scene 1 (CH-10). Sand asks the Wings-or-Roots question openly at Nohant.
6. **Seeing the other ending:** after either epilogue the title menu unlocks **Reverie of the Window**: it loads at **CH-17's first free-movement frame, after BOSS-28**, using the finished save's levels, items and equipment (the farewells replay; keepsakes already received are kept), plays the Question with the **opposite** answer, and leads into the other epilogue (if SQ-07 was incomplete, the Reverie presents it as done, labelled "as it might have been"). The **Eve of the Window** save, created automatically at the last Lectern before BOSS-26, remains as a manual fallback. **New Game+ (Da Capo)** carries levels, equipment, learned skills, Studies, Tutti recipes, Repertoire, 50% of francs and 50% of bond points; resets quests and Horizon; and shows the Sketchbook page as a compass from the start.
7. **Meaning:** *YES*: she trusts him completely, Théo is safe, and she wants to see the century where light-painting was born. *NO*: her art and her people belong here, and she wants to become Lucile Aubray in her own time, not a follower of masters she could meet in a museum; she sends him home, and when he stops at the light and asks her to ask, she asks him to stay (LAW-25). Neither answer is "good" or "bad"; both endings are full and joyful.

**LAW-24 Seoul branch (YES).** They step through hand in hand at 16:52 KST, awake (a held Window costs no Swoon, LAW-05); Brücke, fleeing with the Engine's last oscillator, dives through behind them as the Window collapses (16:53), swoons on the study floor until ~19:50 and is gone before anyone comes back. *The portal:* the Window closes at 16:53 KST; the Door is a dead door; KEY-01 is found still in its dial. *Remaining 1833 secrets:* with Lucile gone, the friends hand Vane's ledger to Gisquet (its "Lumière" pages can no longer hurt her); Delorme is arrested on 23 Dec 1833 and Vane testifies; Vane sails for England in March 1834; Julien and Marthe stay. *A-1 resolution:* Brücke's war is fought to stop the Kang Disclosure. On New Year's Eve he climbs the clock tower (S10) and descends to the Hidden Study, where he tries to re-string the dead Door with the last oscillator ("A dead door can be re-strung."); the shard in the dial answers no signature but Min-jun's, and Min-jun will not play. After BOSS-30 the oscillator shatters (the static automata die with it), and Min-jun tells him, "I will tell no one anything that could hurt anyone." Brücke chooses to believe him and is free; a second Elias Brandt, aged 14, is growing up in Geneva in a world where the Survey will never exist, and Brücke chooses never to go near him. *What Min-jun tells the world:* a cover story of amnesia after an accident, accepted by Det. Oh and the press. The truth goes only to his family, Jae-won and Prof. Yoon. **Céline d'Orsenne** opens the sealed Codicil of Archon's Testament (KEY-35) on Tue 1 Dec 2026, meets Min-jun, and burns it. The study stays sealed by agreement with Prof. Yoon. The portrait goes on public display with the provenance "gift of the Abbé Liszt and friends, Paris, 1886; carried to Seoul by Th. Aubray, 1888": the painting is public, the secret is not. **The Keeper's Choice** (final scene; changes only the closing stills and Min-jun's own voice-over, at most 6 boxes each, §1 Tone Rule 6): **(a) Tell it as music** (canonical default for all other docs: the *Harmonies* premiere is his only testimony); (b) tell only those who love him; (c) tell the world: a press conference, nothing to verify behind a dead door, the world shrugs and Céline's lawyers shield Lucile's privacy. *Lucile in 2026:* she speaks 1830s French; Min-jun translates, phone translation apps are a running joke (she corrects their grammar), and she learns hangul within a week (her first written word is 별, *byeol*, "star"). Papers: **Théo's open letter** in box JD-1888-07 ("Si ma sœur vient, aidez-la. Elle s'appelle Lucile. Elle viendra avec l'ami coréen, au solstice d'hiver de 2026."), read by Prof. Yoon in November, convinces Yoon; the d'Orsenne Foundation vouches for her at the French Embassy (LOC-S13). The game never shows forgery; the end card reads only, "In March 2027, papers arrived in the name of Lucile Aubray." She meets electric light ("this city keeps lightning in glass"), the subway, women in every profession; at the "Light & Colour" exhibition (LOC-S06; real works on fictional loan: three of Monet's *Grainstacks*, 1890–91; Pissarro's *Boulevard Montmartre at Night*, 1897; van Gogh's *Starry Night over the Rhône*, 1888; and her own anonymous canvas) she laughs at the room of haystacks, weeps before the van Gogh ("They found it without a door"; it rhymes with her Panthéon night), and finds her own canvas. She visits Théo's grave at Yanghwajin and learns her sickly brother lived to 77 and crossed the world for her. She paints Seoul at night and reaches LUMIÈRE.

**LAW-25 Paris branch (NO).** She refuses: "I can't leave them. And I won't be the reason you never see your mother again. Go home." (If the SQ-07 gate is unmet, her first words are "I will not leave Théo with nothing.") He walks to the threshold (playable; the Window Clock keeps running; the player can only walk forward or stand still). At the light he stops: "Then ask me. Not for them. For you." After a silence she asks: "Stay." He answers, "I'm staying," takes out the phone (its locked last charge, §14), records a goodbye to his family with the friends crowding into frame, and **throws the phone through the Window**; it lands on the study floor at **16:52 KST (08:02 Paris)**, a minute before the Window closes. He turns back. If the player stands at the threshold for 20 s, she asks first ("Stay. Please."). No input sends him through. **He stays because she asks, never by overriding her** (§16f). *What he gives up:* his parents and sister; his century (medicine, recordings, every note written after 1833 that he cannot remember); his degree and career; and from CH-E2 on he chooses, beyond the Vow's letter, never to perform a future piece for an audience (once, at his June 1834 wedding, for friends). CH-E2 salons and BOSS-35 use REP-27–34 and *Harmonies*; future pieces (REP-01–26, REP-35–45) are greyed out there ("Not mine to play."). Battle Recitals keep the full Repertoire (they are not performances); Secrecy, Onlookers and Heat are retired in CH-E2 (§11e). He carries the burden of knowing when his friends will die (Chopin above all). *What he gains:* Lucile, a brotherhood, and his own music. He marries Lucile in June 1834 (after the epilogue, on the ending card), publishes as "M. Kang" with Maison Farrenc (*Nocturnes de Séoul*, 1840: obscure, in the ossia), writes the hangul letter to Seo-yeon in March 1886 aged 75, and dies in March 1889; he is buried in the Montmartre cemetery, where Lucile joins him in 1891. *The portal:* dead. *A-1:* resolved by absence: with no return there can be no Disclosure. Brücke watches the Door close with Min-jun still in 1833; his war is over, and in an optional CH-E2 scene he and Min-jun burn the Survey dossier (KEY-38). *Remaining secrets:* the friends keep Vane's ledger out of court, because its "Lumière" pages would expose Lucile as Vane's agent; and Min-jun will not testify in a record that would fix his name and face (the Vow). So Delorme is free until the Salon of 1834 (BOSS-33), then flees to Budapest ahead of a warrant; Vane leaves in March 1834 without testifying; Julien opens *Le Diapason Bleu*. SQ-23 "The Last Anachronisms" destroys the rest: Archon's patent vault at the Château d'Orsenne (BOSS-38), Brücke's surviving automata (Brücke helps), **the Engine's last oscillator** (Brücke surrenders it; it is ground to powder in Pleyel's foundry, and Théo keeps a pinch for the Door's dial setting, flavour only), *La Lumière* dismantled after its finale flight, the Walkman buried (Julien listens one last time). *Why the phone is safe:* the Door is dead, and the video shows only people in old clothes playing a piano in a stone room; Seo-yeon shows it to no one but family. *Coda (Tue 22 Dec 2026), playable as Seo-yeon* (PC-09 sprite, no battles, 6–8 minutes): Room B-07 → the hum → the study → the phone video (its stills include the CH-14 photos, KEY-02) → a walk across the snowy campus → the library (LOC-S05) → the packet → the portrait. Box JD-1888-07's open letter (Théo, Seoul, 1897): « Le Coréen est resté. Ma sœur aussi. Ce paquet n'est pas pour vous : gardez-le jusqu'au 22 décembre 2026 et remettez-le à Mlle Kang Seo-yeon. » ("The Korean stayed. So did my sister. This packet is not for you: keep it until 22 December 2026 and give it to Miss Kang Seo-yeon.") Yoon read it in November and recognised the missing student's sister on the first-year roster. The sealed packet bears a hangul label, "서연에게 — 2026년 12월 22일 오후 5시 이후에 열 것" ("To Seo-yeon — open after 5 p.m., 22 December 2026"); Yoon calls her at about 17:10. Inside: the hangul letter (KEY-39), which asks Seo-yeon to write the score's blank last page, and the portrait. The coda ends on her bow lifting.

**LAW-26 The portrait, *Le Frère de demain* (both branches).** Eugène Delacroix, oil on canvas, 73 × 60 cm, **February 1834**. Inscribed lower left in his hand: ***"À notre frère de demain, qui nous apprit la musique des étoiles."*** (In-game translation: *"To our brother from tomorrow, who taught us the music of the stars."*) The phrase comes from CH-14, where Lucile asks Min-jun to "teach us the music of the stars", and it is also the title of his own coda, *La Musique des étoiles* (별의 음악). Composition: a candlelit room, a piano, a figure in shadow at the keyboard with his **right hand lifted to tap the fallboard twice**; on the painted music stand a tiny score marked **민준** in hangul; a window of swirling stars in broken touch, Delacroix's homage to Lucile's manner.

| | Seoul branch (CH-E1) | Paris branch (CH-E2) |
|---|---|---|
| Painted | From memory, after they have gone | From life, at a playable sitting in Delacroix's studio |
| The woman | At the window's edge a woman with a brush dissolves into light, painted in *her* touch | Lucile, painted clearly at the window in her own manner, looking at the viewer |
| Why the face is in shadow | "I will not fix a face I shall never see again." | Min-jun asks: "History must not be able to find me." |
| Reverse | *"et à notre sœur, qui l'a suivi"* ("and to our sister, who followed him"), then the initials E.D., F.C., F.L., H.B., L.F., C.-V.A.; below, in another ink, "G.S., déc. 1834" (Sand adds hers when Théo shows her the canvas, after her return from Italy and her first meeting with Delacroix) | *"Il est resté."* ("He stayed.") in Lucile's hand, signed L.A.; then E.D., F.C., F.L., H.B., L.F., C.-V.A.; below, "G.S., déc. 1834" |
| Route to 2026 | Delacroix gives it to Théo "for when your sister is found" → the 1886 crate → hung in the study 1896 → packed 1906 (embargo: "à ouvrir le 31 décembre 2026, à onze heures du soir") | Min-jun and Lucile give it to Théo with the key → the same route (embargo: the hangul label to Seo-yeon, "open after 5 p.m., 22 December 2026", LAW-25) |
| Found by, when | **Min-jun, with Lucile beside him**, Thu 31 Dec 2026, 23:00 (the embargo hour), library reading room: the brief's image, played | **Seo-yeon**, Tue 22 Dec 2026, after 17:10; she recognises the fallboard tap. Last shot: her face, then the painting, then her bow lifting |
| Meaning | The past said goodbye | The past says hello |

**LAW-27 Secret and post-game lore.** (1) **Ossia** (BOSS-31, Namsan, Seoul) and **the Unwritten** (BOSS-34, Dead Heart, Paris) are two faces of one thing: the history that didn't happen, pushing through the last echo; their middle phase is **the Shadow Virtuoso**, the Min-jun who stole the future. Defeating either yields Delorme's notebook page. Their windows: BOSS-31 in CH-E1, BOSS-34 in CH-E2 (party anchor Lv 50, §10e). (2) The Sainte-Geneviève chronicle in that notebook records "a man who came out of the stone speaking no known tongue, in the year 1253": travellers are older than the cabal, and the game never answers who first heard the stones sing. (3) The NG+-only **Da Capo: The Unstruck Bell** (BOSS-43) is the network's last unstruck note.

---
## §10 Stats, Elements, Statuses & Core Formulas

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
## §11 Systems Vocabulary & Rules Summary

### §11a The Ensemble
- **Party:** 4 active plus up to 4 in reserve (5 once Julien is recruited; the Seoul roster is MJ, LU, SY, JW). Guests take an active slot (§6). Swap freely at Lecterns, inns and on overworld maps through the **Ensemble** menu. **In-battle Swap** (from CH-08): an active member spends their turn to bring in a reserve, who enters at 50% ATB. The Octave formation (BOSS-27) is scripted.
- **Rows:** front/back per member (§10b).
- **Commands:** Fight / *Unique command* / Harmony / Synergy (shown when available) / Item. Sub-menu: Row, Defend, **Tacet** (hold a full ATB to line up a Synergy; DEF/RES +25% while holding), Swap.
- **Forced parties:** CH-01 (MJ + Mathurin), CH-04 barricade (MJ, BE, DE), CH-09 three threads, CH-10 Nohant house defence (MJ, LU, one of FA/AL, + Sand), CH-11 Rhine roster, CH-12 Lucile solo, CH-13 three fronts, CH-15 three parties (MJ in Party 2).
- **Flee:** hold L + R (as in FF6). Success chance per second held = 10% + (party average TMP − enemy average TMP)%, clamped 5–90%. Impossible in boss and scripted battles.
- **Steal:** the relic *Gant de Cartouche* (UI "Cartouche Glove"; after the famous Parisian thief; found in the CH-02 tavern cellars) adds **Pilfer** to the wearer's sub-menu. Success = clamp(40 + LCK_a − LCK_t, 5, 95)%; 1 success in 8 takes the rare slot. Offenbach's GALOP and a perfect 8-hit BEAT also steal. Every ENM lists a common and a rare steal.
- **Party wipe:** a "Fine" screen offers **Retry battle** (HP and INS restored, same formation) or **Return to last save**. No money is lost.

### §11b Harmony, Synergy and the Crescendo Gauge
- **Harmony skills (HRM-PC##-##)** = each character's *solo* arts and spells, paid with INS and learned from Opus Scores and levels. This is the brief's "Sheet-Music Magic". Min-jun's piano pieces are performed through RECITAL from his Repertoire (REP, §15d).
- **Synergy skills (SYN-##)** = combination techniques for 2, 3, 4 or 8 members, paid from the shared **Crescendo Gauge** (0–300, three bars). **Gains:** +1 per 1% of max HP any party member loses; +3 per Recital movement advanced; +2 per weakness hit; +5 per enemy defeated. Starts at 0 (50 in boss battles); resets after each battle. **Costs:** Duo 100, Trio 200, Quartet/Octave 300. A Synergy is available when every participant has a full ATB (Tacet helps); it appears in the menu of whichever participant acts first and empties all participants' gauges. Discorded members cannot join.
- **Unlocks:** a Duo with Min-jun at that partner's bond rank 3; other Duos through optional **Ensemble Scenes**; a Trio when all members are at rank 8. **Exceptions:** SYN-13 unlocks by story at CH-14's Night of Stars (LU and DE at R10); SYN-15 also needs CH-14; SYN-17–19 unlock by story in CH-E1 (Seoul members have no bond ranks); SYN-20 needs JU and LU at rank 8; SYN-23 needs its Ensemble Scene after the SQ-07 family council.

| SYN | Name | Members | Effect (summary) | Unlock |
|---|---|---|---|---|
| SYN-01 | Clair de Lune Impression | MJ + LU | LIGHT to all; party heal | LU rank 3 |
| SYN-02 | Two-Piano Tempest | MJ + LI | 8 BOLT hits | LI rank 3 |
| SYN-03 | Rubato Recital | MJ + CH | Party Allegro; current Recital advances one movement | CH rank 3 |
| SYN-04 | Idée Fixe Fortissimo | MJ + BE | Last Tutti recipe fires twice | BE rank 3 |
| SYN-05 | Portrait in Shadow | MJ + DE | SHADE to all + Smoke | DE rank 3 |
| SYN-06 | Equal Temperament | MJ + FA | Cleanse the party; dispel enemy buffs | FA rank 3 |
| SYN-07 | Pédalier Duo | MJ + AL | Alkan's last Étude repeats at ×1.5, input-free | AL rank 3 |
| SYN-08 | Liberty Leading the Orchestra | BE + DE | FIRE + WIND to all (**first Synergy, scripted CH-04**) | Story CH-04 |
| SYN-09 | Les Deux Virtuoses | LI + CH | Six hits of rotating elements | Ensemble Scene CH-07+ |
| SYN-10 | Chiaroscuro et Lumière | LU + DE | Sets a Light, then a Canvas strike in its boosted elements | Ensemble Scene CH-06+ |
| SYN-11 | Double Fugue | FA + AL | Repeats the last enemy skill twice against enemies | Ensemble Scene CH-08+ |
| SYN-12 | Nocturne in Blue | LU + CH | Night Light + Reverie on all | Ensemble Scene CH-08+ |
| SYN-13 | Brother from Tomorrow | MJ + LU + DE | LIGHT + SHADE dual, 4 hits on all | LU and DE rank 10 (CH-14) |
| SYN-14 | Symphony of Tomorrow | MJ + BE + LI | Tutti *Songe d'une nuit du sabbat* + Tempest | BE and LI rank 8 |
| SYN-15 | Prometheus | MJ + LU + BE | Berlioz's spectral orchestra plays Scriabin's *Prometheus* (REP-26) while Lucile paints its colour-light: FIRE + LIGHT to all, party Inspired (Heat 5) | LU and BE rank 8, CH-14+ |
| SYN-16 | **Octave of the Lost Era** | all 8 | 4 CHRONO hits × PWR 300; breaks the Stilled Hour | Story CH-16; usable post-game and in CH-E2 |
| SYN-17 | Arirang for Two | MJ + SY | Party Cantabile + Allegro | Story CH-E1 |
| SYN-18 | Hwimori | MJ + JW | 8-hit timed combo in the fastest *jangdan* | Story CH-E1 |
| SYN-19 | Samulnori | MJ + LU + SY + JW | Four-instrument sweep: kkwaenggwari thunder (BOLT), jing wind (WIND), janggu rain (WATER), buk clouds (SHADE) | Story CH-E1 |
| SYN-20 | Blue Hour | JU + MJ + LU | SHADE + WATER to all, Swing on enemies | JU and LU rank 8 (optional) |
| SYN-21 | Polonaise of Exiles | CH + DE | EARTH + ICE to one row, Stagefright | Ensemble Scene CH-09+ |
| SYN-22 | Rival Virtuosi | LI + AL | Liszt's last spell + Alkan's last Étude together | Ensemble Scene CH-08+ |
| SYN-23 | Les Inadmissibles | LU + FA | Lucile sets a Light; Farrenc Annotates every enemy, marking a weakness to that Light's boosted element for 3 turns | Ensemble Scene, CH-14+, after the SQ-07 family council (two women the law will not seat) |

**Octave rule (BOSS-27):** all 8 permanent members stand in two rows of four and each member's unique command becomes **Voice**. When all 8 Voices have been performed (each restores one "second" of the Stilled Hour's countdown) the Octave fires automatically. Each **confidant** (rank-10 confession made) adds +10% Octave damage; Julien, if recruited, adds a **Blue Note** (+9%). Sanity check in §10e.

### §11c Opus Scores (the magicite equivalent)
- **32 Scores (OPS-01–32):** 12 Period Scores (OPS-01–12: masterworks and 1830s works, sold at Maison Farrenc and Schlesinger's), 12 Future Scores ✦ (OPS-13–24: Min-jun's transcriptions, mapped one-to-one to REP-17, REP-35, REP-36 … REP-45 in that order, §15d), 8 secret (OPS-25–32: bosses and quests). Each is unique; each character equips one.
- Each Score **teaches 2–5 Harmony skills** at learn rates ×1–×10. After each battle the equipper earns OP (§10a); per-skill progress += OP × rate %, learned at 100%. Anyone can learn any skill except character-locked **Signature** skills.
- Each Score grants a **level-up bonus** (e.g. +1 ART, +2 TMP, +5% max HP) whenever its equipper levels with it equipped.
- Each Score holds one **Invocation** (an Orchestral Summon), usable once per battle by its equipper (twice by Berlioz).
- **Transcription:** at a Lectern after a story trigger, Min-jun writes a future work out from memory as a ✦ Score. Transcribing with a non-confidant in the active party: Secrecy +3. ✦ Invocations are Anachronic (Heat 3).

### §11d Visual Canvas, Plein Air, Orchestral Summons, Cadenza
- **Visual Canvas** = Delacroix's CANVAS and its Sketch/Studies collection (§5c). **Plein Air** = Lucile's command; the two compete over the Light State (Romantic colour versus Impressionist light).
- **Orchestral Summons**, three families: (1) Berlioz's **Tutti** recipes (TUT-01–20); (2) **Invocations** held in Opus Scores; (3) **Remembrances** (CH-E1 only, §6).
- **Cadenza** (desperation): Cadenzas unlock in **CH-09** (tutorial: Min-jun's cell escape at ≤ 25% HP). Members already at bond rank 7 gain theirs then; others on reaching rank 7 (Min-jun and the Seoul members by story). When a member is at ≤ 25% max HP and the Crescendo Gauge is ≥ 100, their "Fight" becomes "Cadenza" (costs 100 Crescendo). Names in §5c. A confidant's Cadenza gains a second phase.

### §11e The Secrecy Meter (LAW-17) and the Spotlight Meter
Scale 0–100 ("Suspicion": how much of the future has leaked into public view), shown as a candle whose flame grows. **Watcher effects of the Murmured and Watched tiers start in CH-06** (the tutorial); before then those tiers apply only gossip, fees and the salon lock.

| Tier | Range | Consequences |
|---|---|---|
| Incognito | 0–19 | None |
| Murmured | 20–39 | Gossip in NPC dialogue; 1 Watcher per district map; salon fees +10% (fame has its uses) |
| Watched | 40–59 | 3 Watchers per district (sight cones); cabal "Shadow" encounters (1 in 8 overworld battles); one salon tier locked |
| Hunted | 60–79 | Inn ambushes; encounter rate +25%; Prefecture papers checks on 4 bridges (KEY-11 required); salon income −25% |
| Compromised | 80–99 | One scripted cabal **Hit** mini-boss per chapter (BOSS-41); Faubourg Saint-Germain shops refuse service; the next story beat triggers a **Close Call** chase (win: −20) |
| Unmasked | 100 | **The Unmasking**: Min-jun is seized, by the Prefecture in CH-02–CH-08 and in CH-14 (cells of LOC-P25), or by the Grey Hand in CH-09–CH-13 (a Bercy safe house that reuses the P25 escape layout) → escape mini-dungeon (BOSS-42); lose 10% of francs; one random party member −20 BP (questioned); meter resets to 60. In CH-10–CH-11 Secrecy is capped at 99. Unmasking is disabled from CH-15 on and in both epilogues. **No game over.** |

**Moment-to-moment layer.** (1) **Onlookers:** battles in public areas (streets, salons, the Opéra) show 1–3 Onlooker silhouettes. Each **Anachronic** action adds its **Heat** to Secrecy while any Onlooker remains: future Recital pieces (REP Heat 1–5; **a Recital's Heat is added once, when Movement I begins**), Lucile's styles (IMPRESSION 2, POINTILLÉ 3, IMPASTO 4, LUMIÈRE 2, the last feeding the Spotlight Meter in CH-E1), ✦ Invocations 3, Improvise 3, CHRONO skills 5. Onlookers flee after 3 turns, or are cleared by a Brass Cue (Berlioz), a Sketch aimed at them (Delacroix), or a scare (any enemy KO'd by a crit). The choice: burst now, or spend turns clearing the crowd. (2) **Bite Your Tongue:** marked dialogues give a 3-second choice between a modern phrasing (more persuasive, a better outcome, sometimes life-saving advice like "boil the water") and a safe period phrasing; the modern one costs +5 to +15. (3) **Watchers:** cabal spies with sight cones on town maps; seen in a restricted zone +3; defeating one +3 but clears that map's Watchers for the chapter. (4) **Phone flashlight** in dark dungeons (limited charges, §14): reveals hidden paths; +4 if a Watcher is on screen. (5) **Dirigible:** each daytime take-off inside Paris +2.

**Other raises:** future pieces at salons (§11g); dialogue slips +3 to +10; seen with the phone or student ID +10; **confidences shared with Lucile during CH-05–CH-08 +8 each, applied silently at chapter end** (she reports them); transcription with a non-confidant present +3; Reckless Confession to a non-party NPC +25. All gains × **Renown multiplier** (×1.0 at 0–249, ×1.25 at 250–499, ×1.5 at 500–749, ×1.75 at 750–999), then −5% per confidant.

**Lowers:** "an old teacher's piece" attribution −3; period-only salon programme −2; passive decay −1 per 10 minutes of field play in Paris districts (max −6 per chapter); inn night −1 (max −5 per chapter); a confidant's **Cover Story** event −10 (once per chapter per confidant); press rebuttal by Heine or through Maison Farrenc −10 (500 F, once per chapter); SQ-04 "Ink and Counter-Ink" −15.

**Story locks:** CH-04 forces ≥ 40 (the frame-up); CH-05 sets max(current − 20, 20) (name cleared); CH-09's end forces ≥ 60 through CH-10 (Liszt's tour); Secrecy is capped at 99 in CH-10–CH-11; from CH-14 the cabal is at open war and Secrecy governs only police and public events. **Story performances add only their scripted values.**

**CH-E2:** the Secrecy Meter is **retired** (the portal is dead and the threat of exposure with it); its HUD slot shows the **Canvas Ledger** (§4f). Onlookers and Heat no longer apply. In battle, RECITAL keeps every learned REP; at salons and in public story scenes only period works and his own (REP-27–34, *Harmonies*) can be chosen, and future pieces are greyed out ("Not mine to play.", LAW-25). **CH-E1:** the Vow places no limit on repertoire; the Secrecy Meter is replaced by the Spotlight Meter, and Heat feeds it only when Lucile paints in public.

**Spotlight Meter (CH-E1 only):** the meter inverted into press and online attention on Lucile. Tiers Quiet 0–24 / Trending 25–49 / Headline 50–74 / Viral 75–99 / 100 = a forced press scrum (fail-forward; resets to 50). Raises: the "missing student returns" news +10 (scripted), Lucile painting in public +5 (plus her style's Heat), busking with Lucile present +3, paying with 1833 coins in public +3. Lowers: Det. Oh's statement −15 (scripted), Céline's lawyers −20 (once), passive decay. Trending: phone-camera crowds slow movement; Headline: reporters block some streets.

### §11f The Trust Network
- **Bond Points (BP)** 0–1000 per party member with Min-jun. **Ranks:** R1 0 / R2 50 / R3 120 / R4 200 / R5 300 / R6 420 / R7 550 / R8 690 / R9 840 / **R10 1000** (R10 also requires the bond-quest finale; for Lucile, BQ-PC02 part 6 is the scripted Night of Stars, §0c).
- **Sources:** each battle in the active party +1 (max +30 per chapter); dialogue choices +5 to +20; gifts +5 to +25 (3 favourite gifts each, below); bond-quest steps +40 to +100; Ensemble Scenes +15; fixed story events. All bonds can be maxed in one run; Evenings are rationed per chapter until CH-14, which has unlimited Evenings (§11i).
- **Favourite gifts (binding; the items doc creates the ITM entries):** LU: a cake of Prussian blue, Sand's *Indiana* (1832), Valencia oranges · BE: Nerval's *Faust* translation (1828), an English Shakespeare he can barely read, oversized orchestral manuscript paper · DE: a Moroccan silk scarf, Byron's poems, English watercolour cakes · AL: a Hebrew psalter, an automaton songbird, an edition of Bach's *Well-Tempered Clavier* · CH: Parma violets, a Polish émigré newspaper, fine kid gloves · LI: a rosary, a box of cigars, a Paganini broadsheet · FA: an engraver's burin, an old Couperin harpsichord edition, a gift for Victorine · JU: Neapolitan coffee, a Maelzel metronome, a café-concert song sheet.
- **Unlocks:** R2 personal topics; R3 Duo Synergy with Min-jun; R5 Signature Harmony skill (below); R7 Cadenza (from CH-09, §11d); R8 Trio eligibility and the **Hint**; **R10 confession**, command upgrade (e.g. Tempo Rubato, Delacroix's LIGHT pigment) and Kindred dialogue.
- **R5 Signatures (character-locked Harmony skills):** LU *Effet de brume* · BE *Chœur d'ombres* (from *Lélio*, 1831–32) · DE *La Barque de Dante* (1822) · AL *Les Omnibus* (his variations, Op. 2, c. 1828–29; the appendix verifies) · CH *Étude en ut mineur* (Op. 10 No. 12, published 1833) · LI *Harmonies poétiques* (his real piece of 1833, which also echoes the game's title) · FA *Air russe* (R-58) · JU *Modal Vamp*. Liszt's *Ecstasy* (REP-21) stays BQ-PC07's quest-locked reward, separate from his Signature.
- **Guaranteed bonds:** story events and the mandatory steps of BQ-PC06 and BQ-PC04 bring Chopin and Delacroix to 1,000 BP by CH-09. CH-14's Night of Stars sets Lucile to R10.
- **Hint** ("What if I came from very far away… in time?"): previews a member's reaction. At R8 it costs −20 BP; at R9 it is free. (Lucile: R6 costs −20, R7 free.)
- **Confession rule:** "Tell the truth" appears in a member's talk menu only at **R10**; below that it is greyed out ("Not yet."). Scripted: Chopin and Delacroix (CH-09), Lucile (CH-14 if not earlier). Optional: Berlioz, Liszt, Farrenc, Alkan. A Reckless Confession to any non-party NPC: Secrecy +25, nothing gained. **Confidant perks:** Octave +10%, Secrecy gains −5%, one Cover Story per chapter.
- **Archon's Revelation (CH-12):** Archon tells the whole party what Min-jun is. Members present who are not yet confidants react by rank: R8+ "Tell us yourself, when you are ready" (no loss); R7 or below, hurt (−50 BP). The confession stays available afterwards as "The Truth, from You" with every perk. Confessing early pays: no penalty and perks sooner. **Lucile is exempt from the Revelation penalty.** Without the Early Truth, the Revelation is how she learns, and her CH-14 scripted confession plays as "The Truth, from You". Her BP unfreezes and her Duo Synergies with Min-jun unlock when she rejoins in CH-12 (Mending 2).
- **Lucile special rules:**
  1. **Reports:** each confidence shared with her during CH-05–CH-08 adds Secrecy +8 at chapter end. Never flagged on screen; each one is stored as a "Confided" line and **read back verbatim in her reports** when Julien hands them over in CH-09 (KEY-18).
  2. **Early Truth:** at **R7, during CH-06–CH-08 only**, Min-jun may tell her. She never reports it; her later confidences cost nothing; Horizon W1 +15; at the reveal she says, "I never told them. Not that."
  *Tuning target:* R7 by the end of CH-08 requires BQ-PC02 parts 1–3 and most optional Lucile scenes; the default path reaches R5–R6, so the Early Truth is a dedicated player's reward.
  3. **Fracture (CH-09):** her BP freezes and her rank is capped at max(current − 3, 2) (only −1 with Early Truth), shown as a cracked heart; her Duo Synergies with Min-jun are locked. **Mending** scenes (CH-10 Nohant, CH-12 dome) raise the cap by +2 each; Mending 2 also unfreezes her BP and unlocks her Duos. The Night of Stars (CH-14) sets R10.

### §11g Salons, Duels, Renown, Own Voice
- **Salon Performance:** choose a programme of 3 pieces. The hostess has a **Taste** (Romantic / Virtuosic / Sacred / Novel); each piece has a mood, a Brilliance value and Heat (REP). Minigame *Phrase*: timed button prompts on a scrolling staff (A/B/X/Y on the beats, L/R for dynamics) → **Rapture** 0–100. Fee = tier base × Rapture%; Renown += Rapture/10 × tier. Tiers and base fees: **T1** tavern (5 F), **T2** bourgeois (Lavergne, 60 F), **T3** aristocratic (Faubourg Saint-Germain, Apponyi; 400 F), **T4** Belgiojoso circle (SQ-20, 2,000 F). **Cabal Presence** (0–3 masked guests). Secrecy per future piece = Heat × (1 + Cabal Presence) × attribution factor: *name the composer* ×2; *an old teacher's piece* ×1, then −3; *my own* ×0.5, +1 Shadow, Renown gain ×1.5 (unavailable after the Vow, CH-14). **Secrecy from one salon is capped at +20 before the Renown multiplier.** Story performances always name the composer and add only their scripted values. An optional salon spends one Evening (§11i).
- **Salon hosts (binding names):** T1 *Au Diapason Fêlé* (Mère Gaudin). T2 Mme Lavergne, rue de Provence (Taste: Romantic) and Mme Bastide, rue Taitbout (FIC-17; Novel). T3 Countess Thérèse Apponyi (NPC-28; Virtuosic), Comtesse Merlin (NPC-52; Romantic), Marie d'Agoult (NPC-18; Sacred). T4 Princess Belgiojoso (NPC-26; SQ-20, from CH-14).
- **Piano Duel** (non-lethal; BOSS-03 teaser, 08, 17 variant, 20, 32, 35): duellists alternate **8 Passages**. Wheel: **Bravura > Pianissimo > Ornament > Cantabile > Bravura**; **Improvise** is a random type at +50%. Each Passage is a timing input that scales its result. The **Favor** bar runs −100 to +100: win at +100, or by being ahead after 8 Passages. **Composure** (duel HP) drops with misses; at 0 a duellist is forced into Pianissimo. Thalberg's *Three-Hand Effect* (every 3rd Passage; every 2nd in BOSS-35; an early private use of his 1836 device, R-10) beats both Bravura and Cantabile. **Rhetoric variant** (Vane): Wit > Charm > Evidence > Silence > Wit. **Brushwork variant** (Salon Jury, Lucile leads): Light > Colour > Composition > Feeling > Light. **Losing never ends the game**; the story continues with different consequences.
- **Renown** 0–999: Unknown 0–99, Noticed 100–249, Admired 250–499, Celebrated 500–749, Legendary 750–999. It raises fees and invitations and multiplies Secrecy gains (§11e).
- **Own Voice** (hidden, 0–10): +1 each time Min-jun plays his own composition (REP-30, available at salons from CH-03) at a salon instead of a future piece, +1 at key arc choices. At ≥ 6, the CH-13 concerto gains an extended cadenza phase and a secret Opus Score. It never affects the ending.

### §11h Saving and transport
- **Saving:** **Lecterns** (glowing music stands visible only to rift-touched eyes) in towns and dungeons; anywhere on overworld maps. Inns restore HP and INS. 3 slots plus the permanent **Eve of the Window** slot (before BOSS-26). Title menu after an ending: **Reverie of the Window** and **Da Capo** (NG+) (LAW-23).
- **Saving in the epilogues:** Lecterns are the network's afterglow. In **CH-E2** they persist, amber and dimmer; one goes dark after each major story beat as a quiet lore cue, but all keep their save function. **CH-E1 has no Lecterns:** save anywhere outside dungeons through the phone's Notes app; inside S08 and S10, metronomes serve as save points (a busker's abandoned one in S08, the practice rooms' in S10; Min-jun hears them tick).
- **Transport progression:** on foot (CH-P–04) → **fiacre** stands (CH-05; fast travel between unlocked Paris districts, 2 F a ride) and the **omnibus** (fixed lines, 6 sous) → **Seine barge *La Mouette*** (CH-08; quays, islands, sewer outfalls) → **diligence** (CH-10; France overworld stations, 40–120 F a leg; passports, KEY-20) → **Rhine steamboat *Concordia*** (CH-11, scripted) → **dirigible *La Lumière*** (captured CH-13, flown from CH-14: free flight over the Paris and France overworlds).
- **The dirigible in fiction:** Brücke's *La Sourdine* ("the Mute"): a hydrogen envelope of his synthetic silk with clockwork-spring propellers wound by a steam winch, built to carry assassins silently over the city. Captured on the Opéra roof; Lucile renames it. Free at night; daytime take-offs inside Paris +2 Secrecy. The party knowingly uses an anachronism to save history (lampshaded by Farrenc). CH-E2: one finale flight, then dismantled at Montmartre (SQ-23). CH-E1: not available.
- **Epilogue transport:** Seoul uses the subway (fast travel between stations), taxis and the phone menu; Paris uses fiacres.

### §11i Time: Evenings, light by time of day, the Window Clock
- **Time advances by story beat; there is no clock.** **Evenings per chapter:** CH-02 2 · CH-03 3 · CH-04 2 · CH-05 4 · CH-06 4 · CH-07 4 · CH-08 2 · CH-09 1 · CH-10 2 · CH-11 1 · CH-12 1 · CH-13 0 · CH-14 unlimited (CH-15–CH-17 none; the epilogues use no Evening budget). An optional salon, a bond evening scene, the CH-10 and CH-12 Window Talks, or an inn rest each spend one. Unused Evenings expire at chapter end.
- **Night map variants** exist only for P02, P04, P10, P16, P22, P24 and P28. **Outdoor Light State follows the scene:** day = Noon unless scripted Dawn or Dusk; Evening scenes = Dusk, then Night.
- **The Window Clock (CH-17).** A 12:00 real-time count that runs only during free movement and pauses in dialogue and menus. Six farewell spots (BE, DE, AL, CH, LI, FA; seven with JU) each cost a fixed 1:00 when spoken to; the friends playing the Engine are spoken to at their posts. The **Pact of the Door** (mandatory, 1:00) fires automatically at 3:00 remaining and **the Question** at 1:30. Walking directly between spots sees every farewell with at least 2:00 to spare; only dawdling misses one. A missed friend's goodbye plays as a single line during the credits (and costs its keepsake's use, §6).

### §11j Options and accessibility
ATB speed 1–6 and Active/Wait (§10b); a **Rehearsal Mode** toggle that makes every timing input (Études, *Phrase*, Duel Passages, BEAT, busking) perfect at ×0.8 result; text speed 1–5; Light State icons that differ by shape as well as colour for colour-blind players. **One difficulty.**

---
## §12 Location Master List

Types: OW overworld, T town or district hub, I interior, D dungeon, mD mini-dungeon, E event stage. LM IDs from §15. In-world text uses quartiers and streets only. Enemy families, inns and shops are listed at the end of this section.

### Seoul (2026)
| LOC | Name | District | Type | First | Revisit | Mood | LM |
|---|---|---|---|---|---|---|---|
| LOC-W03 | Seoul Overworld (Dec 2026) | Jung-gu, Jongno, Mapo, Seocho, Yongsan | OW | CH-E1 | — | Neon, snow, a city that never stops | LM-24 |
| LOC-S01 | Hanseong Conservatory: Annex (Room B-07) | Jeong-dong, Jung-gu | I | CH-P | CH-E1 | Fluorescent practice rooms after midnight | LM-02 |
| LOC-S02 | The Hidden Study | Beneath the annex (reached through Room B-07's closet and the bookcase stair) | I / E | CH-P | CH-E1 (arrival; BOSS-30 arena), CH-E2 coda | Dust, brass, a door that hums | LM-01 |
| LOC-S03 | Jeong-dong and the Deoksugung Stonewall Road | Jung-gu | T | CH-E1 | — | Old legation quarter, palace walls, winter ginkgo | LM-24 |
| LOC-S04 | Kang Family Apartment | Mapo-gu | I | CH-E1 | — | Floor heating, a mother's cooking, his room kept as he left it | LM-32 |
| LOC-S05 | Conservatory Library and Archives | Jeong-dong | I | CH-E1 | CH-E2 coda | Reading-room hush; box JD-1888-07 | LM-01 |
| LOC-S06 | Hangaram Art Museum, Seoul Arts Center: "Light & Colour" (fictional loan exhibition of real works) | Seocho-gu | I | CH-E1 | — | Three Monet *Grainstacks* (1890–91), Pissarro's *Boulevard Montmartre at Night* (1897), van Gogh's *Starry Night over the Rhône* (1888), and one anonymous canvas (LAW-24) | LM-03 |
| LOC-S07 | Hongdae Busking Street | Mapo-gu | T | CH-E1 | — | Buskers, street food; busking minigame | LM-24 |
| LOC-S08 | Euljiro Underground Arcade and Line 2 tunnels | Jung-gu | D | CH-E1 | — | Shuttered shops, humming trains, Brücke's static automata | LM-10 |
| LOC-S09 | Namsan and N Seoul Tower | Yongsan-gu | D (opt) | CH-E1 | — | Wind, love locks, the city's lights below; superboss Ossia | LM-17 |
| LOC-S10 | Conservatory Concert Hall and Clock Tower | Jeong-dong | D (approach) / E | CH-E1 | — | New Year's Eve; gears above the stage; the climb that leads down to the Hidden Study (BOSS-30 is fought in S02) | LM-10 → LM-26 |
| LOC-S11 | Bosingak Pavilion | Jongno | E | CH-E1 | — | The midnight bell, 33 strokes, snow | LM-26 |
| LOC-S12 | Insadong | Jongno | T | CH-E1 | — | Antique shops; the numismatist Mr. Baek buys Louis-Philippe sous by weight | LM-24 |
| LOC-S13 | French Embassy in Seoul | Seodaemun-gu | I | CH-E1 | — | Paperwork comedy in two centuries of French | LM-03 |
| LOC-S14 | Yanghwajin Foreign Missionary Cemetery | Mapo-gu | T | CH-E1 | — | Théo's grave, river wind, bare trees | LM-30 |
| LOC-S15 | Kang Piano Service | Euljiro, Jung-gu | I | CH-E1 | — | Felt hammers, his father's radio | LM-32 |

### Paris (1833)
| LOC | Name | District | Type | First | Revisit | Mood | LM |
|---|---|---|---|---|---|---|---|
| LOC-W01 | Paris Overworld | The city inside the toll wall, plus Montmartre | OW | CH-02 | all | Fog, chimneys, bells | LM-04 |
| LOC-P01 | Saint-Denis Galleries | Under the Faubourg Saint-Jacques → Barrière d'Enfer | D | CH-01 | CH-15 (link) | Bones, lime pits, lantern light | LM-17 |
| LOC-P02 | Latin Quarter: rue Saint-Jacques | Left Bank | T | CH-01 | CH-12 | Rain, students, ragpickers, cholera ex-votos | LM-04 |
| LOC-P03 | Faubourg-Poissonnière and the Conservatoire (with undercroft) | Rue Bergère | T / mD | CH-02 | all | Scales from every window; Cherubini's frown | LM-04 |
| LOC-P04 | *Au Diapason Fêlé* (with cellars) | Rue du Faubourg-Poissonnière | I / mD | CH-02 | CH-04, CH-14, CH-E2 | Smoke, soup, a pianino with three dead keys | LM-02 |
| LOC-P05 | Salon Lavergne | Rue de Provence | I | CH-03 | CH-05 | Gilt on credit; ambitious bourgeois | LM-19 |
| LOC-P06 | Delacroix's Studio | 15 quai Voltaire | I | CH-03 | CH-06, CH-09, CH-E2 | Turpentine, Moroccan silks, river light | LM-12 |
| LOC-P07 | The Marais and Place Royale | Right Bank | T | CH-04 | CH-07 | Old mansions turned workshops; tension | LM-28 |
| LOC-P08 | Barricade of rue Saint-Antoine | Marais | D | CH-04 | — | Paving stones, smoke, *La Parisienne* | LM-28 |
| LOC-P09 | Théâtre-Italien (Salle Favart) | Boulevards | I | CH-03 | CH-12 (exterior) | The 2 Apr benefit; the 24 Nov walkout | LM-19 |
| LOC-P10 | Grand Boulevards and the Passage de l'Opéra | Bd des Italiens, Tortoni | T / mD | CH-05 | all | Gaslight, dandies, ices | LM-04 |
| LOC-P11 | Chopin's Apartment | 5 rue de la Chaussée-d'Antin | I | CH-05 | CH-09 | Violets, a Pleyel, homesickness | LM-13 |
| LOC-P12 | Pleyel: Salle and Workshop | 9 rue Cadet | I / mD | CH-05 | CH-07, CH-08 | Sawdust, felt, iron frames | LM-19 |
| LOC-P13 | The Louvre: Copyists' Gallery and Salon Carré | Right Bank | D | CH-06 | — | Easels, masterpieces, a painting that moves | LM-09 |
| LOC-P14 | Faubourg Saint-Germain | Left Bank | T | CH-05 | CH-07, CH-14 | Shuttered mansions, old money | LM-07 |
| LOC-P15 | Hôtel d'Apponyi (the Hôtel de Monaco, 57 rue Saint-Dominique, rented from Marshal Davout's widow as the Austrian Embassy, 1820s–1838) | Faubourg Saint-Germain | I | CH-07 | — | Ballroom of mirrors; a duel of pianos | LM-21 |
| LOC-P16 | Palais-Royal | Galleries and arcades | T | CH-08 | CH-14 | Gambling, booksellers, pickpockets | LM-04 |
| LOC-P17 | Sewers of Palais-Royal | Beneath the Palais-Royal | D | CH-08 | — | Dripping vaults, cassette hiss | LM-08 |
| LOC-P18 | Horlogerie Brücke and the Clockwork Undercroft | Rue de la Paix | mD | CH-07 | CH-14 | Ten thousand ticks | LM-10 |
| LOC-P19 | Maison Farrenc (shop and house) | Rue Saint-Marc (quartier Feydeau, by the Bourse); no. 21 (the firm's address Dec 1831 – May 1836) | I | CH-05 (shop) | all | Engraved plates, Victorine practising | LM-15 |
| LOC-P20 | Lucile's Attic | Rue des Grands-Augustins | I | CH-04 | CH-06, CH-11, CH-12 | Skylight, fans drying, Théo coughing | LM-03 |
| LOC-P21 | Maison Corbel | Rue Dauphine | I | CH-04 | CH-07, CH-09 | Trinkets and a back room | LM-07 |
| LOC-P22 | Seine Quays and Pont des Arts | Centre | T | CH-03 | all | Dawn mist, bouquinistes | LM-22 |
| LOC-P23 | British Embassy (Hôtel de Charost) | Faubourg Saint-Honoré | I | CH-09 | — | A wedding in borrowed finery | LM-11 |
| LOC-P24 | Montmartre | Village outside the wall | T | CH-06 | CH-14, CH-E2 | Windmills, vines, open sky; the Chappe telegraph station on the tower of Saint-Pierre | LM-23 |
| LOC-P25 | Prefecture of Police and Cells | Rue de Jérusalem, Île de la Cité | I / mD | CH-04 | Unmasking | Ink, iron, informers | LM-28 |
| LOC-P26 | Val-de-Grâce: hospital, abbey wing, quarries | Faubourg Saint-Jacques | D | CH-12 | — | A working hospital above, a sealed monastery below, Mignard's dome | LM-06 |
| LOC-P27 | Salle Le Peletier (Opéra): stage, rafters, corridors, roof | Rue Le Peletier | D / E | CH-13 | — | Three fronts at once | LM-21 |
| LOC-P28 | Panthéon and Montagne Sainte-Geneviève (David d'Angers' scaffolding) | Left Bank | T | CH-12 | CH-14, CH-15 | The dome against the stars | LM-01 |
| LOC-P29 | The Chrono-Labyrinth | Panthéon crypt and quarries | D | CH-15 | Post-game (BOSS-43) | Paris and Seoul fused in pixels | LM-17 / LM-24 |
| LOC-P30 | The Heart Chamber | Beneath the Panthéon | D | CH-16 | CH-17 | A cathedral of resonant stone | LM-25 → LM-30 |
| LOC-P31 | Bercy Wine Depots | East, by the Seine | D | CH-09 | — | Barrels, barges, a stolen night | LM-06 |
| LOC-P32 | Île de la Cité and Notre-Dame | Centre | T | CH-04 | all | Hugo's cathedral, gargoyle Echoes | LM-04 |
| LOC-P33 | Père-Lachaise Cemetery | East | T (opt) | CH-14 | CH-E2 | A grave Min-jun knows too well | LM-18 |
| LOC-P34 | Hôtel de Vane | Rue de Varenne | D | CH-09 (Lucile interlude) | CH-14 | A collector's mansion; every painting a confession | LM-07 |
| LOC-P35 | Conservatoire Concert Hall | Rue Bergère | E | CH-14 (Hiller's concert, Habeneck conducting; reported in *Le Pianiste* as the Salle des Menus-Plaisirs) | CH-E2 | 22 Dec 1833, a Sunday afternoon: Paganini in a side box | LM-11 |
| LOC-P36 | Alkan Family House | Marais | I | CH-04 | CH-14 | A cramped musical household, a pedal piano | LM-16 |
| LOC-P37 | Sœur Marthe's Dispensary | Val-de-Grâce gate | I | CH-07 | CH-11, CH-12 | Boiled water, clean linen, quiet authority | LM-31 |
| LOC-P38 | Panthéon Crypt: the Philosophers' Tombs | Beneath the nave | D (opt) | CH-14 | — | Voltaire and Rousseau, still arguing | LM-17 |
| LOC-P39 | Princess Belgiojoso's Salon | Faubourg Saint-Honoré | I | CH-14 (SQ-20) | CH-E2 | Italian exiles, a pale princess, two pianos | LM-19 |

### Regional (1833)
| LOC | Name | Region | Type | First | Revisit | Mood | LM |
|---|---|---|---|---|---|---|---|
| LOC-W02 | France and Rhine Overworld | Paris → Berry; Paris → Rhineland | OW | CH-10 | CH-14+ | Poplars, post roads, rivers | LM-29 |
| LOC-R01 | Forest of Fontainebleau | Seine-et-Marne | T / field | CH-10 | CH-14 | Rocks, birches, Corot at his easel | LM-23 |
| LOC-R02 | Château d'Orsenne | Near Fontainebleau | D (opt) | CH-14 | CH-E2 (SQ-23) | Archon's estate: forges, model barricades, a patent vault | LM-06 |
| LOC-R03 | Nohant | Berry | T | CH-10 | CH-14 | Sand's house, cigars, children, fireside | LM-23 |
| LOC-R04 | La Châtre | Berry | T | CH-10 | — | Market town; Liszt lodges at the Auberge du Lion d'Argent and gives a benefit concert (R-21) | LM-23 |
| LOC-R05 | The Vallée Noire | Berry | D | CH-10 | — | Night forest, mechanical wolves | LM-10 |
| LOC-R06 | Liège | Kingdom of Belgium | T | CH-11 | — | Coal smoke, a 10-year-old at the keyboard | LM-29 |
| LOC-R07 | Düsseldorf | Prussian Rhine Province | T | CH-11 | CH-14 | Academy painters, Mendelssohn's rehearsals | LM-29 |
| LOC-R08 | Rhine steamboat *Concordia* | Middle Rhine | D | CH-11 | — | Paddles, steam, cliffs. Real PRDG paddle steamer (1827, Cologne–Mainz, 42.7 m, 70 hp); the party boards at Cologne (LOC-R14). Her battle is fictional (R-21) | LM-29 |
| LOC-R09 | The Lorelei | Middle Rhine | D (opt) | CH-11 | CH-14 | Echoing rock; grief | LM-22 |
| LOC-R10 | Strasbourg and the Kehl bridge | The Rhine border | T | CH-11 (return) | CH-14 | Cathedral spire, customs posts | LM-29 |
| LOC-R11 | Étretat cliffs | Normandy | Field (BQ) | CH-14 | — | The Needle, wind, plein air | LM-03 |
| LOC-R12 | Le Havre harbour | Normandy | T (BQ) | CH-14 | — | Dawn masts, and the canvas she chose not to paint (BQ-PC02b) | LM-03 |
| LOC-R13 | Aachen border post | Prussian frontier | mD | CH-11 | — | Customs barrier, passports, rain | LM-28 |
| LOC-R14 | Cologne: the Rhine landing | Prussian Rhine Province | T | CH-11 | — | Unfinished cathedral, the PRDG quay, the *Concordia* taking on coal | LM-29 |

### Paris epilogue (1834)
| LOC | Name | District | Type | First | Mood | LM |
|---|---|---|---|---|---|---|
| LOC-E01 | Salon of 1834 (Louvre: Salon Carré and Grande Galerie) | Louvre | D / E | CH-E2 | Thousands of canvases, a crowd, one small canvas of light, hung *au ciel* | LM-27 |
| LOC-E02 | Atelier Aubray-Kang | Montmartre | I (home hub) | CH-E2 | Two easels, one piano, morning light (restored). **Exists in every CH-E2 run:** if SQ-12 is incomplete when CH-E2 begins (including via Reverie), the friends pool their savings (the wedding money) to rent the same unrestored studio (cutscene); it opens bare (one easel, no piano) and its restoration becomes a CH-E2 side task (5,000 F; next free SQ number). Restored (by SQ-12 or the side task): skylight, a Pleyel piano and Delacroix's spare easel, i.e. two upgrade stations | LM-22 |
| LOC-E03 | The Dead Heart | Beneath the Panthéon | D (opt) | CH-E2 | Silent stone; Archon mid-gesture, forever; the Unwritten | LM-17 (frozen) |
| LOC-E04 | *Le Diapason Bleu* (Julien's café-concert) | Boulevard du Temple | I | CH-E2 | A jazz club a century early, by candlelight | LM-08 |
| LOC-E05 | Delorme's Atelier | Île Saint-Louis | D | CH-E2 | Mirrors, lenses, the geometry of envy | LM-09 |

### Enemy families by area (binding for bestiary and dungeons)
| Area | Families |
|---|---|
| P01 Saint-Denis Galleries | Ossuary Echoes, Lime Wraiths, quarry rats |
| P04 tavern cellars | Gros-Louis's smugglers, rats |
| P03 Conservatoire undercroft | Choir Echoes |
| P08 Barricade | Black Coats, Tocsin Echoes |
| P10 Boulevards and Passage de l'Opéra | Gaslight Wisps, pickpocket gangs |
| P13 Louvre | Tableau Echoes |
| P18 Clockwork Undercroft | Brücke Mk. I automata |
| P17 Sewers of Palais-Royal | Cloaca Echoes, sewer rats, Phantom Quartet spectres, Julien's café toughs |
| P31 Bercy | Grey Hand, barrel automata |
| R01 / R05 Fontainebleau, Vallée Noire | Hunter Automata, boar |
| R06–R14 Rhine road and river | Frontier smugglers, river automata, Lorelei Echoes |
| P26 Val-de-Grâce | Grey Hand, Abbey Echoes, Living Tableaux |
| P27 Opéra | Grey Hand assassins, stage-machinery automata |
| P34 Hôtel de Vane | Roussel's Cleaners, Vane's animated collection |
| R02 Château d'Orsenne | Forge automata |
| P29 Chrono-Labyrinth | Amalgam Echoes (Lutèce constructs, turnstile golems, neon wraiths) |
| P30 Heart Chamber | Grey Hand elite, Stilled Echoes |
| S08 Euljiro / Line 2 | Static automata |
| S09 Namsan | Ossia phantoms |
| CH-E2 (E01, E03, E05, streets) | Living Tableau squads, residual Echoes, leftover automata |
| Any area not listed (e.g. P38, R09, R11) | Assigned by the bestiary from the families above, within LAW-07 and the rule below |

**Rule:** no battle is ever fought against the National Guard, Prefecture agents, octroi agents, uniformed soldiers or any Seoul civilian. CH-01 patrols are stealth hazards: being seen means a 5-second chase and a reset to the last lantern checkpoint. BOSS-42 The Turnkey is a Grey Hand bruiser bribed into the cells.

### Inns, shops and salons (binding names; all shops fictional)
- **Inns:** P02 Hôtel du Lys d'Or · P04 *Au Diapason Fêlé* · P10 Hôtel de la Lyre · P16 Hôtel des Arcades · P24 Auberge des Trois Moulins · R04 Auberge du Lion d'Argent · R06 Hôtel de la Meuse · R07 Gasthof zum Goldenen Anker · R10 Hôtel de la Cathédrale. Seoul: hotel stays only where the story needs them (₩60,000, §14).
- **Shops:** Armurerie Vidal (P03), Coutellerie du Palais (P16), Vidal & Fils (P14, high tier) for weapons and armour; **Couleurs Ravenel**, rue de Seine, for brushes (Lucile will not enter Maison Grimaud until the debt is cleared); Pharmacie Laborde (P02, P10) for consumables; Curiosités Corbel (P21) for relics; Maison Farrenc (P19) and Schlesinger's (P10) for Opus Scores. Seoul: Haneul Mart for consumables; Kang Piano Service (S15) for weapon upgrades; the Insadong numismatist Mr. Baek (S12).
- **Salons:** hosts and Tastes in §11g.

---

## §13 Boss Master List

HP, level and weakness are binding for `bosses.md`. **All §13 values are final; bosses.md may not rescale them.** Duel-format bosses use Composure and Favor (§11g), not HP. Human bosses are routed, subdued or arrested, never shown dying. Boss DEF/RES = 1.2 × standard enemy DEF at the boss's level (§10b). Boss TMP, LCK, ART and MAR follow the §10b enemy model. "abs" = absorbs.

**How the HP values were derived (for new optional bosses and for fights where the party size varies):**
- **Party-size rule:** boss HP = chapter anchor (§10e) × (PCs + 0.5 × guests) / 4.
- **Gauntlet rule:** a boss followed by another boss in the same dungeon visit with no Lectern between uses ×0.75 (BOSS-10, BOSS-26). **Timed fights** are discounted (BOSS-19, ≈ ×0.8).
- **Multi-part bosses:** the core carries the anchor; optional parts are extra (BOSS-28).
- **Tuning tolerance:** listed values may sit up to about ±15% from the rule; where the party size varies, scale from the listed value (BOSS-24).

| BOSS | Name | CH | LOC | Lv | HP | Weak / Resist | Party present | Gimmick (one line) |
|---|---|---|---|---|---|---|---|---|
| BOSS-01 | Ossuary Warden (Echo) | CH-01 | P01 | 4 | 520 | LIGHT / SHADE | MJ + Mathurin (g) | Raises a bone wall every 3 turns; the hummed Recital *Resonance* shatters it; Mathurin's Lantern reveals its core |
| BOSS-02 | Gros-Louis, King of the Smugglers (FIC-18) | CH-02 | P04 cellars | 6 | 1,100 | — / — | MJ; BE bursts in on turn 5 | Steals francs; flees at 25% unless Stunned |
| BOSS-03 | Henri Herz (salon cutting contest) | CH-03 | P05 | — | Composure 600 (3 Passages) | — | MJ | Previews the duel wheel; cannot be lost badly |
| BOSS-04 | Le Chantre (Echo of a dead choirmaster) | CH-03 | P03 undercroft | 9 | 2,600 | LIGHT / abs SHADE | MJ, BE, DE, AL (g) | Hush every 4 turns; matching his pitch with a Recital Stuns him |
| BOSS-05 | Captain Marlot and the Black Coats | CH-04 | P08 | 12 | 3,200 (+3 waves of 2 × 470) | — / — | MJ, BE, DE | Wave battle with Onlookers on the barricade, then a 5-turn powder-keg countdown; SYN-08 taught here |
| BOSS-06 | The Passage Chimera (Echo) | CH-05 | P10 | 14 | 5,600 (body 2,000 + 3 heads × 1,200) | Heads: FIRE, ICE, BOLT, each weak to its opposite | any 4 of 5 | Light State tutorial: Shift the Hour weakens two heads at once |
| BOSS-07 | Tableau Vivant: *The Raft* | CH-06 | P13 | 16 | 7,000 (+ castaway adds 400) | FIRE, BOLT / abs WATER, res ICE | any 4 | Waves flood the back row every 3 turns; reading its hidden formula aloud exposes the core but is a Slip (+15, copyists watching) |
| BOSS-08 | Sigismond Thalberg (Piano Duel) | CH-07 | P15 | — | Composure 1,500 | — | MJ | Rigged action: Favor starts at −20; Three-Hand Effect every 3rd Passage; losing allowed |
| BOSS-09 | The Escapement Hound | CH-07 | P18 | 17 | 8,000 (+3 gears × 900) | BOLT / ICE | any 4 | Heals 10% at each clock chime unless its gears are smashed |
| BOSS-10 | Cloaca Leviathan (Echo) | CH-08 | P17 | 19 | 8,500 | LIGHT / abs WATER | any 4 | Sluice levers shift the water level, which swaps rows |
| BOSS-11 | Julien and the Phantom Quartet | CH-08 | P17 | 20 | 11,000 (+4 × 1,500) | LIGHT / SHADE | any 4 incl. MJ | Swing status; kill the rhythm section first; at 30% he plays the cassette, and Min-jun's *Recognition* ("name the tune") cancels it |
| BOSS-12 | Commandant Roussel and the Grey Hand (I) | CH-09 | P31 | 22 | 13,000 | — / — | Phase 1: BE + 2 of DE, LI, AL, FA, CH; phase 2: MJ joins as the 4th | Rolling and exploding barrels; telegraphed "Steady…" rifle shot (interrupt with any hit ≥ 5% of his HP, or the target loses 60% max HP); 3 shots maximum |
| BOSS-13 | Le Meneur de Loups and Hunter Automata | CH-10 | R05 | 24 | 17,800 (+2 × 2,000) | BOLT, WATER / FIRE | any 4 of MJ, LU, LI, FA, AL (no Sand: §16e) | Brücke builds the pack around the Berry legend of the wolf-leader (which Sand later wrote up in *Légendes rustiques*, 1858): a cloaked automaton "piper" leads the Hunter wolves. Night battle; wolves hunt the lowest-HP member; Lucile's Dawn reveals them; silencing the piper scatters the pack (Sand's hint, given at Nohant) |
| BOSS-14 | The Rheinwolf (boiler automaton) | CH-11 | R08 | 27 | 19,000 | WATER, ICE / abs FIRE | any 3 + "Florestan" (Schumann, g, AI) | Boiler pressure +10 per turn; ICE/WATER lower it; at 100 a FIRE blast on all, then reset |
| BOSS-15 | The Painter: Isaure Delorme | CH-12 | P26 | 30 | 24,000 (+3 easels × 2,000) | SHADE / LIGHT | LU + 3 of MJ, BE, DE, LI, FA, AL | Golden Section wards split the field; Vanishing Point traps a member (cannot be healed); smash the easels |
| BOSS-16 | Archon: The Audience | CH-12 | P26 | 45 | unkillable (shown ?????) | — | same | Survival: a Stasis field nulls all damage; ends after 6 turns or when party HP < 25%; "Play for me." Archon's Revelation follows |
| BOSS-17 | The Grand Concert: Stage | CH-13 | P27 | — | Rapture 0–100 (the Hall's attention) | — | MJ, LI (BE conducting, untargetable) | Duet duel over 3 movements; keep Rapture ≥ 40 while control switches between the three fronts every 3 turns; the eight-bar rescue costs Rapture −15; Own Voice ≥ 6 adds a cadenza phase |
| BOSS-18 | Brücke and the Phonautograph Engine | CH-13 | P27 rafters | 33 | 20,000 (+4 horns × 2,500) | BOLT, WATER / FIRE | DE, LU, AL | Each surviving horn adds +20% to the recording (max 80%: the mid-concerto modulation always spoils completeness). The percentage only scales Archon's CH-16 move *Recorded Echo* (+5% damage per 20%) and changes lines; it never removes the need for the living string (LAW-12). Escapement rewinds ATB; cutting a counterweight also damages the corridor enemies; Brücke escapes at 50% |
| BOSS-19 | Commandant Roussel (II) | CH-13 | P27 corridors | 33 | 13,500 (timed fight) | — / — | CH, FA, Offenbach (g) | Timer = 12 turns of the corridor front (it pauses while control is on another front). On expiry there is no game over: Roussel reaches the stage door, BOSS-17 Rapture −20, and Roussel withdraws wounded. "Steady…" |
| BOSS-20 | Lord Vane (Rhetoric Duel) | CH-14 | P34 | — | Composure 3,000 | — | MJ (LU may second) | Wit / Charm / Evidence / Silence; *Wager*: he stakes his Composure against the party's Crescendo; at Favor +60 he reads her early reports and the scene turns |
| BOSS-21 | Roussel and the Cleaners (III) | CH-14 | P34 | 35 | 30,000 | — / — | any 4 (protect Vane, 3,000 HP) | His last three cartridges; Grey Hand shield wall |
| BOSS-22 | Warden of Lutèce | CH-15 | P29 | 37 | 27,000 | WIND / abs EARTH | Party 1 (3) | A stone giant of 1833 Paris: rebuilds barricades, buries one member every 4 turns (dig out with WIND) |
| BOSS-23 | Warden of Hanseong | CH-15 | P29 | 37 | 27,000 | EARTH / BOLT | Party 2 (3) | Glass, neon and subway doors: "closes doors" on one party slot for 2 turns; neon flicker inflicts Smoke |
| BOSS-24 | Orpheus Descending | CH-15 | P29 | 37 | 18,000 (27,000 if Julien joins Party 3) | LIGHT / abs SHADE | Party 3 (2, or 3 with JU) | "Do not look back": attacking its back half reverses damage |
| BOSS-25 | Ad Astra (the Seventh Panel's shadow) | CH-15 | P29 (Heart gate) | 39 | 36,000 | Weakness = the current Light's weakened elements / resists the boosted ones | merged party (4) | The Varga equation rewrites one stat every 3 turns; Shift the Hour re-tunes its weakness |
| BOSS-26 | Archon, Baron d'Orsenne | CH-16 | P30 | 40 | 30,000 | LIGHT / SHADE | 4 | *Tactics*: Grey Hand formations (shield wall, volley); rearranges party rows |
| BOSS-27 | The Stilled Hour | CH-16 | P30 | 43 | 36,000 | Invulnerable until the Octave | all 8 (Octave formation) | Temporal ward with a time-freeze countdown from 00:43 (the solstice instant); each Voice restores one second; the Octave breaks the ward |
| BOSS-28 | Archon and the Engine (*Clavier des Âges*) | CH-16 | P30 | 43 | Core 40,000 + Left Manual 6,000 + Right Manual 6,000 + Pedalboard 7,000 | BOLT, WATER / abs CHRONO | 4 | Warps space: Right Manual flips rows every 3 turns; Left Manual pitch-bends spells (swaps Lento/Allegro); Pedalboard gravity wells pull the back row forward; destroying each silences that function. *Recorded Echo* deals +5% damage per 20% of the KEY-23 recording (BOSS-18). Look: LAW-09 |
| BOSS-29 | Automaton "Line 2" | CH-E1 | S08 | 42 | 40,000 | WATER / abs BOLT | MJ, LU, SY, JW | Announces its next attack on the platform display one turn ahead; a train passes every 4 turns (dodge by switching rows) |
| BOSS-30 | Elias Brandt, The Last Hour | CH-E1 | S02 (Hidden Study; approach through S10) | 44 | 52,000 | WATER, LIGHT / CHRONO | Seoul party | Brandt tries to re-string the dead Door with the last oscillator ("A dead door can be re-strung."); the clock-dial lock is the arena's countdown (12 turns; resets); reverses party ATB. He fails because the shard in the dial answers only Min-jun's signature; his oscillator shatters; ends in his conversation with Min-jun (the promise) |
| BOSS-31 | Ossia (optional superboss) | CH-E1 | S09 | 55 | 3 bars × 36,000 | Resists all but CHRONO (bar 3) | Seoul party + Remembrances | Bar 1: phantoms of the 1833 friends; bar 2: the Shadow Virtuoso (+1 move per 2 Shadow); bar 3: Ossia, "the history that didn't happen" |
| BOSS-32 | The Salon Jury (Duel) | CH-E2 | Louvre jury room (E01) | — | Composure 3,600 | — | LU leads; MJ supports with Conduct | The jury's admissions session, **Sat 15 Feb 1834** (in-game date within the real February sessions), before the 1 Mar opening; the jurors are Academicians. Brushwork wheel. Ingres is hostile: his verdict opens at Favor −30, +1 per recovered canvas (Canvas Ledger, cap +15). **Delaroche** (NPC-10) is the swing vote: SQ-11 done = Delaroche speaks for her in session (+20). Delacroix, no Academician until 1857, can plead only as an outside advocate ("champions her *before* the jury", never "on" it). KEY-40 is issued after the session |
| BOSS-33 | Delorme's Masterwork: *The Golden Section* | CH-E2 | E01 | 44 | 52,000 | SHADE, BOLT / LIGHT | any 4 | Opening day, Sat 1 Mar 1834. Skied paintings fall as attacks; protect Lucile's canvas (KEY-40's No. 61; its own 9,999-HP bar, minus the damage taken in the *La Lumière* flight) for the best ending text |
| BOSS-34 | The Unwritten (optional superboss) | CH-E2 | E03 | 55 | 3 bars × 36,000 | Resists all but CHRONO (bar 3) | any 4 | Inflicts Unwritten every turn; **Min-jun is no longer immune**; bar 2 is the Shadow Virtuoso |
| BOSS-35 | Thalberg Rematch (optional duel) | CH-14 (SQ-20) / CH-E2 | P39 | — | Composure 4,000 | — | MJ | Three-Hand Effect every 2nd Passage; Belgiojoso judges; previews 1837. CH-E2: only REP-27–34 and *Harmonies* may be played (LAW-25) |
| BOSS-36 | Paganini's Shadow (Echo, optional) | CH-14 only (missable; Echoes fade after CH-16, LAW-07) | P27 (night) | 40 | 38,000 | LIGHT / SHADE | 4 incl. LI | Plays on one string; each turn's string sets its element; BQ-PC07 climax |
| BOSS-37 | The Lorelei Echo (optional) | CH-11 or CH-14 | R09 | 32 | 22,000 | FIRE / abs WATER | any 4 | Reverie song; Chopin's Rubato counters it |
| BOSS-38 | The Forge Colossus (optional) | CH-14, or CH-E2 via SQ-23 | R02 | 40 | 40,000 | WATER, ICE / abs FIRE | any 4 | Archon's prototype steam war machine; overheats every 5 turns (double-damage window) |
| BOSS-39 | The Needle Echo (optional) | CH-14 only (BQ-PC02b; missable) | R11 | 40 | 32,000 | LIGHT / abs WIND | 4 incl. LU | The Light cycles Dawn → Noon → Dusk every 2 turns |
| BOSS-40 | The Philosophers' Echo (Voltaire and Rousseau, optional) | CH-14 only (missable) | P38 | 41 | 2 × 18,000 | One LIGHT-weak, one SHADE-weak | any 4 | They debate; kill both within 3 turns of each other or the survivor revives the other |
| BOSS-41 | Assassin Automaton Mk. Ω ("Hit") | any chapter up to CH-14 (Compromised tier) | random | party avg | 4 × chapter standard enemy HP | BOLT / FIRE | current party | Secrecy consequence (§11e) |
| BOSS-42 | The Turnkey (Unmasking escape) | CH-02–CH-14 | P25 or the Bercy safe house (§11e) | party avg | 0.6 × chapter boss anchor | FIRE / — | current party | A Grey Hand bruiser bribed into the cells; escape boss; scales |
| BOSS-43 | Da Capo: The Unstruck Bell (NG+ only) | post-game | P29 | 99 | 3 bars × 60,000 | CHRONO / all others | any 4 | Every 10 turns it replays one story boss as a phase |

---
## §14 Economy & Items Anchors

**Currency (1833–34):** the **franc (F) = 20 sous (s)**; 1 sou = 5 centimes. Money is counted internally in sous; the UI shows prices under 1 F in sous ("Bread 8s") and the rest in whole francs. Coins in flavour text: sou, 5 F silver écu, 20 F gold piece (a "louis", with the king's head; old soldiers still say "napoléon"). Money cap 9,999,999 F. Prices are stylised (R-55); real anchors for flavour only: labourer's day wage 2–3 F; garret rent 120–200 F a year; modest dinner 1 F 50; fiacre ride 1 F 50; Chopin's lesson 20 F; a Pleyel grand about 2,000 F; diligence Paris–Brussels about 35 F. **Seoul (CH-E1):** the won (₩). Francs carry over and are sold to the Insadong numismatist Mr. Baek at **₩200 per franc**, a balance abstraction (R-55): he buys the bag of copper sous by weight, and Min-jun keeps his few silver and gold pieces as keepsakes.

### Price bands and tiers
Equipment tier names: **Étude → Prélude → Nocturne → Rhapsodie → Concerto → Symphonie → Opus Magnum → Lost Era** (one unique ultimate per character, never sold; names and requirements below). Pattern: "[Tier] [Class]" (e.g. *Nocturne Baton*, *Concerto Sabre*), plus uniquely named items. Weapon ATK at the chapter where sold ≈ 10 + 2.2 × Lv (§10e).

| Tier | Chapters | Weapon ATK | Weapons | Head / body armour | Relics | Consumables | Inn |
|---|---|---|---|---|---|---|---|
| Étude | CH-01–02 | 12–19 | 60–150 F | 40–120 F | — | 1–40 F | 10 F |
| Prélude | CH-03–04 | 24–32 | 200–400 F | 150–300 F | 300–800 F | 1–60 F | 15 F |
| Nocturne | CH-05–07 | 36–45 | 500–1,000 F | 300–800 F | 1,000–2,000 F | 5–150 F | 25 F |
| Rhapsodie | CH-08–09 | 52–56 | 1,100–1,400 F | 800–1,100 F | 1,500–2,500 F | 5–300 F | 40 F |
| Concerto | CH-10–13 | 60–80 | 2,000–3,500 F | 1,500–2,600 F | 2,500–4,500 F | 20–400 F | 60 F |
| Symphonie | CH-14–15 | 85–91 | 3,800–5,200 F | 2,800–4,000 F | 5,000–8,000 F | 40–1,500 F | 100 F |
| Opus Magnum | CH-16, CH-E2 | 98–105 | 5,500–7,000 F | 4,000–5,200 F | 8,000–11,000 F | 40–1,500 F | 150 F |
| Seoul modern gear | CH-E1 | 98–105 | ₩1,100,000–1,400,000 | ₩800,000–1,040,000 | ₩1,600,000–2,200,000 | ₩1,000–300,000 | ₩60,000 (hotel) |
| Lost Era | — | 150–180 | not sold | — | — | — | — |

**Affordability rule (binding):** each tier's critical-path income (earned during that tier's chapters) covers **≥ 70% of a 4-member weapon + head + body kit at band midpoints**.

### Expected income (critical-path play)
*Assumptions:* ≈ 19 standard kills per CP hour (§10e), boss F ×10, chests = 25% of battle F, 2 optional salons per chapter in CH-02–08, CH-14 and CH-E2, 1 in CH-10–12. Act figures are averages; income rises within each act.

| Act | F per hour | Of which salons |
|---|---|---|
| I | 350 | ~7% |
| II | 1,600 | ~15% |
| III | 4,500 | ~3% |
| IV | 9,000 | ~7% |
| Epilogues | 10,700 F or ₩2,140,000 | ~9% |

### Slots, inventory, consumables
- **Slots per character:** Weapon, Head, Body, Relic × 2. Weapon classes: Batons (MJ), Brushes (LU), Sword-canes (BE), Rapiers (DE), Hammers (AL), Quills (CH), Sabres (LI), Folios (FA), Bows (SY), Drumsticks (JW), Canes (JU).
- **Inventory:** 256 slots, 99 per stack; key items in a separate, unlimited tab.
- **Anchor consumables (first sold; UI names ≤ 16 characters, §16h):** Tisane 150 HP, 8 F (CH-02) · Bouillon 500 HP, 40 F (CH-05) · Cordial 1,500 HP, 180 F (CH-10) · Grand Cordial full HP, 600 F (CH-14) · Café Noir +30 INS, 30 F · Chocolat (*Chocolat de Santé*) +100 INS, 150 F (CH-10) · Élixir full HP/INS (not sold) · **Sal Volatile** revive at 25%, 40 F (CH-02) · **Sel de Vie** revive at 100%, 1,500 F (CH-14) · Smelling Salts (Reverie) 10 F · Four Thieves (*Vinaigre des Quatre Voleurs*; Miasma) 15 F · Eyewash (Smoke) 10 F · Throat Lozenge (Hush) 12 F · Courage Draught (Stagefright) 25 F · Sculptor's Oil (Marble) 60 F · **Pitch Pipe** (Out of Tune, Discord) 40 F · Panacea (all negative statuses except KO) 300 F · Picnic Hamper (full party rest at a Lectern) 400 F.

### Lost Era ultimates (binding names)
MJ *Baton of Tomorrow* (UI "Tomorrow Baton"; Berlioz's CH-04 baton reforged by Théo) · LU *Pinceau Lumière* · BE sword-cane *Idée Fixe* · DE rapier *Liberté* · AL hammer *Pédalier* · CH quill *Żelazowa* · LI sabre *Mephisto* · FA folio *Trésor* · SY bow *Hanseong* · JW sticks *Sinmyeong* · JU cane *Blue Note*. **Requirement:** bond R10 plus the holder's bond-quest finale (JU: BQ-PC11). Min-jun, who has no bond rank, earns his by defeating BOSS-31 or BOSS-34. SY and JW have no bond ranks either: Seo-yeon's comes from the busking ladder's Legend rank, Jae-won's from BOSS-31. **Paris branch:** the friends' weapons also need the giver's keepsake, forged at Pleyel's (§6).

### Key items (binding)
| KEY | Name | Obtained | Purpose |
|---|---|---|---|
| KEY-01 | **Ornate Brass Key** (bow: two clock hands fused into a key) | CH-P | Unlocks the Door; stays in the dial in 2026 (leaves inventory); found there again in CH-E1 |
| KEY-02 | Smartphone | CH-P | 3% charge: **6 flashlight uses** in CH-01–CH-13 (Secrecy risk), then dead. Recharged once in CH-14 on KEY-28 to 20%: **camera** unlocked (up to 12 photos of friends; Secrecy +4 if a non-confidant sees), the last 5% locked (greyed out) for the CH-17 recording. Paris: thrown through the Window; the photos appear as stills in the recorded goodbye Seo-yeon watches. Seoul: becomes the phone menu; the photos fill its album |
| KEY-03 | Hanseong Student ID | CH-P | Secrecy liability (+10 if seen) |
| KEY-04 | Photocopied Score: *Clair de lune* | CH-P | 2026 paper; source of REP-01 |
| KEY-05 | Quarryman's Lantern | CH-01 (Mathurin) | Light in dark dungeons |
| KEY-06 | Room Key, *Au Diapason Fêlé* | CH-02 | First home |
| KEY-07 | Berlioz's Letter of Introduction | CH-03 | Opens Delacroix's studio and the Lavergne salon |
| KEY-08 | Salon Invitation Card (stamped T1–T4) | CH-03+ | Unlocks salon tiers |
| KEY-09 | **Lucile's Sketchbook** | CH-05 (viewable); in Min-jun's inventory from the CH-09 dawn, when she presses it on him | Horizon signpost (LAW-23.5); its last page does not change from the CH-09 handover until Mending scene 1 |
| KEY-10 | Lucile's Sketch of the Paymaster | CH-04 | Evidence before Gisquet; the face is Vane's steward Fernand Tissot (FIC-19) |
| KEY-11 | Laissez-passer (Prefecture) | CH-04 | Required at Hunted-tier papers checks |
| KEY-12 | Pleyel Workshop Pass | CH-05 | Voicing upgrades; SQ-07 |
| KEY-13 | Formula Sketch (E = mc²) | CH-06 | First proof of the cabal |
| KEY-14 | Nitinol Spring | CH-07 | Proof of synthetic alloys |
| KEY-15 | Julien's Mixtape ("JAZZ MIX '87") | CH-08 | Proof of Vane's Walkman (R-15) |
| KEY-16 | **Vane's Ledger** | CH-09 | Lucile's turn; Clef map, Seventh Panel, the death order dated 30 Sep 1833 (never the living-string clause, §8); handed to Gisquet for Delorme's arrest in the Seoul branch only (LAW-24, LAW-25) |
| KEY-17 | Pleyel Action Assembly | CH-08 | Restores Chopin's Pleyel for the concert |
| KEY-18 | Lucile's Reports ("Lumière" file) | CH-09 (Julien) | The reveal; reads back the Confided lines; may be burned together in CH-14 (optional scene) |
| KEY-19 | Clef Map of the Quarries | CH-10 (Farrenc decodes) | Clef locations (LAW-02) |
| KEY-20 | Passports and Diligence Ticket Book | CH-10 | Regional travel; the Aachen border |
| KEY-21 | **The Seventh Panel, *Ad Astra*** | CH-11 | Opens the Heart gate (CH-15) |
| KEY-22 | Chaplain's Key (abbey wing) | CH-12 (Lucile) | Val-de-Grâce access |
| KEY-23 | Phonautograph Cylinder (partial signature, 0–80% by BOSS-18) | CH-13 | Lore; scales *Recorded Echo* in BOSS-28; destroyed in CH-16 |
| KEY-24 | Lucile's Unsent Letters | CH-12 | Reconciliation; readable |
| KEY-25 | Gala Programme | CH-13 | Story |
| KEY-26 | Helm Key of *La Lumière* | CH-13 | Dirigible |
| KEY-27 | **Panthéon Crypt Key** and Archon's Solstice Timetable | CH-14 (Vane) | Labyrinth entrance |
| KEY-28 | Brücke's Hand-Crank Dynamo | CH-14 (Horlogerie Brücke, LOC-P18 revisit) | Recharges the phone once |
| KEY-29 | Heart Shard | CH-16 | Given to Delacroix in CH-17; set in the Door's dial (LAW-22) |
| KEY-30 | Keepsakes of 1833 (6, or 7 with Julien) | CH-17 farewells (both branches) | Seoul: Remembrance summons in CH-E1. Paris: the keepsake forge for each giver's Lost Era weapon in CH-E2 (§6) |
| KEY-31 | Théo's Apprentice Indenture | SQ-07 step 5 (the family council) | Gate for YES (LAW-23) |
| KEY-32 | Alkan's Clef Tuning Forks (a set of three, one per CH-15 party) | CH-15 | Detune Clefs at their plinths (LAW-08); one becomes Alkan's keepsake |
| KEY-33 | Visitor Lanyard (Hanseong) | CH-E1 | Campus access for Lucile |
| KEY-34 | "Light & Colour" Exhibition Tickets | CH-E1 | LOC-S06 |
| KEY-35 | Testament of the Stilled Hour | CH-E1 | Written by Archon on 20 Dec 1833, in two parts. The open **Charge**, known to his heirs since 1834: endow a foundation; when Korea opens, buy and dig the Jeong-dong legation ground; find a sealed room and keep it shut (why the Foundation paid for the 2019 works). The sealed **Codicil**, "to be opened in December 2026", draws on Brücke's dossier: it names "a young Korean who will come out of the cellar" and orders that he be discredited or silenced. Céline opens the Codicil on Tue 1 Dec 2026 and burns it after meeting Min-jun (CH-E1). Paris branch: filed as an ancestor's fantasy (one line in the coda's news ticker) |
| KEY-36 | Archive Box JD-1888-07 ("Caisse Aubray") | CH-E1 / CH-E2 coda | Contents by branch (LAW-26). **Seoul:** Théo's papers; Théo's open letter about Lucile (LAW-24); Julien's waltz "pour M." (1851); the sealed packet (portrait; "à ouvrir le 31 décembre 2026, à onze heures du soir"). **Paris:** Théo's papers; Théo's short open letter of 1897 asking that the packet be kept for Seo-yeon (LAW-25), with nothing about helping Lucile; the sealed packet labelled in hangul to Seo-yeon (KEY-39 letter + portrait) |
| KEY-37 | Paganini's Note to Berlioz | CH-E2 | Side scene (*Harold*) |
| KEY-38 | Survey Dossier | CH-E2 | Brücke's gift, burned |
| KEY-39 | Hangul Letter (서연에게) | CH-E2 coda | The final reveal; written by Min-jun in March 1886, aged 75; asks Seo-yeon to write the score's blank last page |
| KEY-40 | Salon of 1834 *Livret* | CH-E2, after the jury session (BOSS-32) | Salon access. Entry: "AUBRAY (Mlle Lucile), rue des Grands-Augustins, 7. — 61. *Le Pont des Arts, matin d'hiver.*" If BQ-PC02b is complete, No. 61 is *Le Havre, la criée au lever du jour*. BOSS-33 protects whichever canvas is entered |
| KEY-41 | Embassy Receipt (Lucile Aubray) | CH-E1 | Her papers |

---

## §15 Music Canon

### §15a SNES audio constraint
The SPC700 has **8 voices** and 64 KB of audio RAM. **House rule (the brief's "5-channel synthesis"): voices V0–V4 carry music, V5–V7 SFX** (V5 UI and footsteps, V6 battle hits and spells, V7 ambience and stings). **Exceptions:** in-battle set pieces BOSS-17 (Stage) and BOSS-27 (Octave) may borrow V5–V6 (7 music voices, SFX ducked to V7); **Grand Mode** (all 8 voices, cutscenes only): MUS-070 Concerto "Lost Era" opening, MUS-095 *La Musique des étoiles* (only in CH-17's opening and closing cutscenes; during the playable Window it follows the 7-voice rule, with V7 for UI SFX), MUS-150 *Le Frère de demain* (portrait, both branches), MUS-160 Bosingak, MUS-170 Salon Night finale (the *Harmonies* finale at Chopin's birthday supper, 1 Mar 1834). **ARAM budget:** sound driver ≤ 5.5 KB; 0.5 KB reserved for zero page, stack, I/O and the sample directory; sequence data ≤ 6 KB; music BRR samples ≤ 28 KB (≤ 14 instruments per loaded song, the 17-sample palette below being global; the grand piano ≈ 12 KB, 2 zones); SFX samples ≤ 8 KB; echo buffer ≤ 16 KB (EDL ≤ 8; default EDL 4 = 8 KB; salons and churches EDL 8). **Sample palette:** grand piano, detuned pianino (tavern), strings, horn, flute, oboe, harp, timpani, snare, organ, barrel organ/accordion (streets), choir "aah", upright-bass pizzicato (Julien), music box (Brücke), hurdy-gurdy (Nohant), a plucked-silk gayageum-like timbre (Seoul), and **one square/saw synth patch reserved for the Engine and Archon's final forms** (and the static automata of CH-E1): the only modern timbre in the score. **SFX:** soft square-wave menu clicks, footsteps per surface, chimes for spell invocations, a two-note ATB-ready ding, rising chimes for Recital movements, a dramatic low piano-cluster impact for crits and boss hits.

### §15b Track naming
`MUS-### "Title" [LM-xx, LM-yy]`; English title with optional French subtitle. Bands: MUS-001–099 story and area, MUS-100–149 battle and boss, MUS-150–199 epilogues, MUS-200+ arrangements of real repertoire titled by the original work and REP ID (e.g. `MUS-201 "Clair de lune (Debussy) — tavern pianino" [REP-01]`). Fixed: MUS-001 "Harmonies of the Lost Era" (title) [LM-01, LM-02]; MUS-100 "The Ensemble" [LM-20]; MUS-101 "Duel of Tempos" [LM-21]; MUS-130 "Vers la Coda" [LM-25]. audio_and_music owns the rest.

### §15c Leitmotifs
| LM | Name | Represents | Character of the motif | Key uses |
|---|---|---|---|---|
| LM-01 | Harmonies of the Lost Era | The Door, the friends, the title score | A rising **eight-note** figure spanning one octave in D major (**D E F♯ G A B C♯ D**), one note per Octave voice: notes 1–7 belong to MJ, BE, DE, AL, CH, LI, FA; note 8, the octave, belongs to Lucile. Every statement stops on C♯, the leading tone, until LM-26, LM-27 and LM-30, where Lucile's D resolves it (in both branches: the octave is the note that completes him). The same eight notes solve the CH-P dial puzzle | Title, Hidden Study, Panthéon, endings |
| LM-02 | From Tomorrow | Min-jun | Pentatonic melody (Korean colour) over gently modern harmony | Tavern, field, his scenes |
| LM-03 | Impression | Lucile | Whole-tone shimmer on harp and flute, never quite landing | Her scenes, the exhibition |
| LM-04 | Ville Lumière, Ville Malade | Paris streets | Minor waltz on barrel organ, rain percussion | Overworld and towns |
| LM-05 | The Stilled Hour | The cabal | A **12-tone row** over a ticking ostinato: their music is from the wrong century | Cabal scenes, cabal bosses |
| LM-06 | Archon | Archon | Organ pedal and industrial anvils; whole-tone ascent; the reserved synth patch in BOSS-28 | Val-de-Grâce, Archon |
| LM-07 | A Gentleman's Wager | Vane | A courtly minuet that warps like stretched cassette tape (tape wow) | Faubourg Saint-Germain, Vane |
| LM-08 | Blue Notes in the Dark | Julien | Ninth chords, walking bass; evokes, never quotes | Sewers, *Le Diapason Bleu* |
| LM-09 | Golden Section | Delorme | A crab canon (palindrome) with Fibonacci phrase lengths | Louvre, Delorme |
| LM-10 | Escapement | Brücke | Clockwork pizzicato and music box in 7/8 | Horlogerie, automata, Seoul clock tower and the BOSS-30 duel |
| LM-11 | Idée Fixe | Berlioz | Quotation of Berlioz's own *idée fixe* (1830, public domain) | Berlioz, wedding, 22 Dec concert |
| LM-12 | Liberty's Palette | Delacroix | Brass fanfare softening into strings | Studio, portrait |
| LM-13 | Żal | Chopin | Original mazurka lilt with a sighing appoggiatura | Chopin's apartment |
| LM-14 | Transcendence | Liszt | Octave runs resolving into a chorale | Liszt |
| LM-15 | Counterpoint of the Unremembered | Farrenc | Two-voice invention, the second voice entering late | Maison Farrenc |
| LM-16 | Ostinato | Alkan | A grave figure that never stops, with sudden silences | Alkan |
| LM-17 | Resonance | Clefs, rifts, Echoes | Sustained hum with beating overtones | Dungeons under Paris |
| LM-18 | Miasma | Cholera, grief | Lament over a descending bass | Poor quarters, memorials |
| LM-19 | Candlelight Salon | Salons | Gentle galop | Salons |
| LM-20 | The Ensemble | Regular battle | Driving 12/8 with piano lead | MUS-100 |
| LM-21 | Duel of Tempos | Bosses and duels | Two competing tempi that lock together | MUS-101+ |
| LM-22 | Two Hours of Light | The romance | LM-02 and LM-03 in counterpoint | Pont des Arts, kiss, Night of Stars |
| LM-23 | Nohant Afternoons | Sand, the countryside | Pastoral 6/8, hurdy-gurdy bourrée | Nohant, Fontainebleau, Montmartre |
| LM-24 | Jeong-dong Night | 2026 Seoul | Lo-fi chiptune groove, gayageum-like pluck | Prologue, Seoul |
| LM-25 | Vers la Coda | Final battle | LM-06 inverted against LM-01 | BOSS-26–28 |
| LM-26 | Snow on Jeong-dong | Seoul epilogue | LM-01 completed in a major key | CH-E1 |
| LM-27 | Salon Night, 1834 | Paris epilogue | LM-01 completed as a waltz | CH-E2; the *Harmonies* finale at Chopin's birthday supper, Sat 1 Mar 1834 (MUS-170) |
| LM-28 | La Rue | Riots, police, politics | Snare and fragments of Auber's *La Parisienne* (1830, PD) | Marais, Prefecture, borders |
| LM-29 | Rhine Journey | Travel abroad | Broad horn call | France and Rhine overworld |
| LM-30 | La Musique des étoiles | Min-jun's coda; the Window; the portrait | LM-01's eight notes finally resolved over LM-22 | CH-14 roof, CH-17, portrait, Yanghwajin |
| LM-31 | Hymn of the Ward | Sœur Marthe | Modal hymn | Dispensary, Val-de-Grâce |
| LM-32 | Eomma | Min-jun's family, homesickness | The opening of *Arirang* (traditional, PD), hummed | Kang apartment, Seoul amalgam floors |

### §15d Repertoire: future works Min-jun performs
**Clearance rule:** only works **first published in 1930 or earlier** (US public domain as of 1 Jan 2026; the appendix verifies each first edition); all five composers are public domain under EU life + 70 (Prokofiev since 2024; Ravel in France since 2016 after wartime extensions). Arrangements are new chiptune transcriptions made from first editions or PD scans; no recordings, no modern editions. **Heat** = Secrecy value when performed before Onlookers or at salons (§11e, §11g).

| REP | Composer | Work | Composed / published | Chapter and scene | Recital effect (I → II → III) or use | Heat | US / EU 2026 |
|---|---|---|---|---|---|---|---|
| REP-00 | — | *Resonance* (a hummed tone) | — | CH-01 | Stuns Echoes → shatters bone walls | 0 | — |
| REP-01 | Debussy | *Clair de lune* (Suite bergamasque) | c. 1890 / 1905 | CH-P; CH-02 Berlioz hears it | Cantabile → LIGHT +25% → party heal | 3 | PD / PD |
| REP-02 | Debussy | *Arabesque No. 1* | 1888–91 / 1891 | CH-04 first meeting with Lucile | Party TMP +10% → INS regen → Allegro | 2 | PD / PD |
| REP-03 | Debussy | *Reflets dans l'eau* (Images I) | 1905 / 1905 | CH-06 lesson on reflections | Mirror on one ally → party Mirror → WATER wave | 3 | PD / PD |
| REP-04 | Debussy | *Doctor Gradus ad Parnassum* (Children's Corner) | 1908 / 1908 | CH-11 for Czerny (not amused, then laughs) | Unlocks Velocity drills | 2 | PD / PD |
| REP-05 | Debussy | *The Snow Is Dancing* (Children's Corner) | 1908 / 1908 | CH-E1 first snow | Field music; Lento on enemies | 2 | PD / PD |
| REP-06 | Debussy | *La cathédrale engloutie* (Préludes I) | 1910 / 1910 | CH-15 labyrinth | Varnish → Glaze → EARTH + WATER quake | 4 | PD / PD |
| REP-07 | Debussy | *L'isle joyeuse* | 1904 / 1904 | CH-14 first dirigible flight | Allegro → Fortissimo → Crescendo Gauge +30 | 4 | PD / PD |
| REP-08 | Ravel | "Ondine" (*Gaspard de la nuit*) | 1908 / 1909 | **CH-03 Lavergne salon** (the brief's Gaspard) | WATER +25%, enemy Lento → WATER burst | 4 | PD / PD |
| REP-09 | Ravel | "Le Gibet" (*Gaspard*) | 1908 / 1909 | CH-12 "Play for me" (Archon) | Enemy RES −20% → Coda (20) on one enemy | 4 | PD / PD |
| REP-10 | Ravel | "Scarbo" (*Gaspard*) | 1908 / 1909 | CH-14 Hôtel de Vane: Vane asks for it, closing the circle he opened with "Ondine"; Min-jun's Cadenza | SHADE +25% → Delirium on all → SHADE storm | 5 | PD / PD |
| REP-11 | Ravel | *Jeux d'eau* | 1901 / 1902 | CH-05 Pleyel showroom | WATER +25%, EVA +10% → cleanse | 3 | PD / PD |
| REP-12 | Ravel | *Pavane pour une infante défunte* | 1899 / 1900 | CH-09 Chopin's confession | Cantabile, cures Stagefright → Encore on one ally | 2 | PD / PD |
| REP-13 | Ravel | *Ma mère l'Oye* (four hands) | 1908–10 / 1910 | CH-09 wedding: Min-jun and Liszt play *Le jardin féerique* | SYN-02 flavour | 2 | PD / PD |
| REP-14 | Rachmaninoff | Prelude in C♯ minor, Op. 3 No. 2 | 1892 / 1893 | CH-04 barricade bells | Stagefright chance on enemies → EARTH bell strike | 3 | PD / PD |
| REP-15 | Rachmaninoff | Prelude in G minor, Op. 23 No. 5 | 1901 / 1904 | CH-08 confronting Julien | Swell +1 per movement → march strike | 3 | PD / PD |
| REP-16 | Rachmaninoff | Suite No. 2 for Two Pianos, Op. 17 | 1900–01 / 1901 | CH-07 rehearsing with Liszt | SYN-02 flavour; salon duet | 3 | PD / PD |
| REP-17 | Rachmaninoff | *Isle of the Dead*, Op. 29 (orchestral) | 1909 / 1909 | CH-12 Score drop | ✦ Score Invocation only (OPS-13; spectral orchestra; SHADE) | 3 (✦ Invocation, §11c) | PD / PD |
| REP-18 | Rachmaninoff | *Vocalise*, Op. 34 No. 14 | 1912, rev. 1915 / by 1916 | CH-14 Night of Stars | INS regen → party Cantabile → revive one ally | 2 | PD / PD |
| REP-19 | Scriabin | Étude in D♯ minor, Op. 8 No. 12 | 1894 / 1895 | CH-07 duel finale | Duel finisher; Fortissimo → FIRE burst | 3 | PD / PD |
| REP-20 | Scriabin | Prelude for the Left Hand, Op. 9 No. 1 | 1894 / 1895 | CH-09 cell (right hand injured), CH-10 Nohant | Playable while Hushed; Cantabile | 2 | PD / PD |
| REP-21 | Scriabin | Piano Sonata No. 5, Op. 53 | 1907 / 1907 | BQ-PC07 Liszt's finale | Liszt Signature *Ecstasy* | 5 | PD / PD |
| REP-22 | Scriabin | *Vers la flamme*, Op. 72 | 1914 / 1914 | CH-16 Archon phases | Crescendo Gauge +20 per turn → FIRE/LIGHT nova | 5 | PD / PD |
| REP-23 | Prokofiev | *Suggestion diabolique*, Op. 4 No. 4 | 1908, rev. 1912 / 1913 | CH-12 vs Delorme | Enemy Hush → SHADE + CHRONO strike | 5 | PD / PD |
| REP-24 | Prokofiev | Toccata, Op. 11 | 1912 / 1913 | CH-11 steamboat pistons | Allegro + BOLT +25% → 6-hit BOLT | 5 | PD / PD |
| REP-25 | Prokofiev | *Visions fugitives*, Op. 22 (selected) | 1915–17 / 1917 (verify; ≤ 1930 either way) | CH-15 amalgam zones | Light State shifts each movement → CHRONO-lite burst | 4 | PD / PD |
| REP-26 | Scriabin | *Prometheus: The Poem of Fire*, Op. 60 (orchestral) | 1910 / 1911 | CH-14+ | SYN-15 only: Berlioz's spectral orchestra plays it while Lucile paints its colour part | 5 | PD / PD |
| REP-35 | Debussy | *Prélude à l'après-midi d'un faune* (orchestral) | 1891–94 / 1895 | CH-05 transcription | ✦ Invocation only (OPS-14) | 3 | PD / PD |
| REP-36 | Debussy | *La Mer* (orchestral) | 1903–05 / 1905 | CH-08 (the barge *La Mouette*) | ✦ Invocation only (OPS-15) | 3 | PD / PD |
| REP-37 | Ravel | *Daphnis et Chloé*, Suite No. 2 (orchestral) | 1909–12 / 1913 | CH-06 (dawn over the rooftops) | ✦ Invocation only (OPS-16) | 3 | PD / PD |
| REP-38 | Ravel | *La Valse* (orchestral) | 1919–20 / 1921 | CH-07 (the embassy ballroom) | ✦ Invocation only (OPS-17) | 3 | PD / PD |
| REP-39 | Ravel | *Le Tombeau de Couperin* (orchestral suite) | 1914–19 / 1918 (piano), 1919 (orch.) | CH-10 (the road out of Paris) | ✦ Invocation only (OPS-18) | 3 | PD / PD |
| REP-40 | Rachmaninoff | Piano Concerto No. 2, Op. 18 | 1900–01 / 1901 | CH-11 (Mendelssohn's academy) | ✦ Invocation only (OPS-19) | 3 | PD / PD |
| REP-41 | Rachmaninoff | Symphony No. 2, Op. 27 | 1906–07 / 1908 | CH-12 | ✦ Invocation only (OPS-20) | 3 | PD / PD |
| REP-42 | Rachmaninoff | *The Bells*, Op. 35 (choral symphony) | 1913 / 1920 | CH-14 (Notre-Dame's bells) | ✦ Invocation only (OPS-21) | 3 | PD / PD |
| REP-43 | Scriabin | *Le Poème de l'extase*, Op. 54 (orchestral) | 1905–08 / 1908 | CH-13 (after the gala) | ✦ Invocation only (OPS-22) | 3 | PD / PD |
| REP-44 | Prokofiev | Symphony No. 1 "Classical", Op. 25 | 1916–17 / 1925 | CH-08 (Farrenc's Haydn argument) | ✦ Invocation only (OPS-23) | 3 | PD / PD |
| REP-45 | Prokofiev | *Scythian Suite*, Op. 20 (orchestral) | 1914–15 / 1923 | CH-15 (the amalgam zones) | ✦ Invocation only (OPS-24) | 3 | PD / PD |
| — | **Excluded** | Prokofiev Sonata No. 7 (1942); Rachmaninoff *Rhapsody on a Theme of Paganini* (1934); Ravel Concerto in G (1932) and Concerto for the Left Hand | — | Never used | — | — | Not PD in the US |
| — | **Excluded** | Debussy *Golliwogg's Cakewalk* (sensitivity: racial caricature); Ravel *Boléro* (PD, but not worth the legal noise); **any jazz composition or recording** behind Julien's tapes (evoke the style, never quote a melody or name an artist) | — | Never used | — | — | — |

**Originals and other repertoire:**
| REP | Work | In-world date | Use | Heat | Status |
|---|---|---|---|---|---|
| REP-27 | Kang Min-jun, *Concerto for Two Pianos "Lost Era"* | 1833 | **CH-13 Opéra** (BOSS-17); afterwards a Recital | 0 | Project-owned |
| REP-28 | Les Amis and Min-jun, *Harmonies de l'ère perdue* | Variations 1834–1886. Finale: **Seoul** — written on the blank last page on 31 Dec 2026 and premiered that night; **Paris** — played from memory at Chopin's birthday supper in the Atelier, Sat 1 Mar 1834, and never written down (LAW-22) | CH-E1 New Year's Eve premiere; CH-E2 Salon Night supper (MUS-170) | 0 | Project-owned |
| REP-29 | Kang Min-jun, *La Musique des étoiles* (별의 음악), the Window coda | 18 Dec 1833 | CH-14 roof; CH-17 the friends play it; its theme is LM-30 | 0 | Project-owned |
| REP-30 | Kang Min-jun, *Jeong-dong Nocturne* (his unfinished student piece) | 2025 | Salon piece from CH-03 that raises Own Voice; a battle Recital from CH-13 | 0 | Project-owned |
| REP-31 | Traditional (Korean), *Arirang* | folk | Hummed CH-02, CH-11, CH-17; in CH-E2 Chopin improvises a mazurka on it. Recital: cures Discord and Swing | 0 | PD |
| REP-32 | J. S. Bach, Prelude in C, WTC I | 1722 | Safe salon piece | 0 | PD |
| REP-33 | Beethoven, *Pathétique* Sonata, II | 1799 | Safe salon piece | 0 | PD |
| REP-34 | Chopin, Nocturne Op. 9 No. 2 | pub. 1832 | Played with Chopin's blessing from CH-06 | 0 | PD |

### §15e 1830s repertoire performed by historical characters (all PD)
Chopin: Études Op. 10 (published summer 1833; No. 3 played for Min-jun in CH-05), Nocturnes Op. 9 (1832), Mazurkas Op. 7 (1832), the G-minor Ballade (fragments only; finished 1835). Chopin and Liszt: Onslow's Sonata in F minor for four hands (CH-03, 2 Apr). Hiller, Chopin and Liszt: J. S. Bach's concerto for three keyboards (CH-14, 15 Dec). Liszt: *Grande fantaisie de bravoure sur La Clochette* (1832–34), the piano transcription of the *Symphonie fantastique* (1833). Berlioz: *Symphonie fantastique* (1830), *Lélio* (1831–32), *Le roi Lear*, *Rob Roy*, *Les Francs-juges*, *Waverley* (the Tutti recipes); *Harold en Italie* commissioned Jan 1834 (CH-E2 only). Alkan: *Concerto da camera* No. 1 (1832). Farrenc: *Air russe varié*, Op. 17 (composed 1835, published 1836; heard as sketches in 1833–34, R-58); Overture No. 1, Op. 23 (1834, CH-E2). Mendelssohn: *The Hebrides* (1830, rev. 1832), *Songs without Words* Book 1 (CH-11). Clara Wieck: *Caprices en forme de valse*, Op. 2 (1832); the draft of her Piano Concerto, Op. 7 (begun 1833). Robert Schumann: *Papillons*, Op. 2; *Impromptus on a Theme by Clara Wieck*, Op. 5 (1833). Czerny: *School of Velocity*, Op. 299 (the drills). Thalberg: an operatic fantasy in his "three-hand" manner (title unspecified; appendix verifies). Opéra: Meyerbeer *Robert le diable* (1831), Schneitzhoeffer's *La Sylphide* (1832, Taglioni). Salons: Rossini *Guillaume Tell* overture, Bellini "Casta diva" (*Norma*, 1831). Paganini: Caprice No. 24 (published 1820; BOSS-36). Street: Auber *La Parisienne* (1830), *La Marseillaise* (CH-04).

---
## §16 Style & Sensitivity Rules

### §16a Dialogue box specification (binding for art_and_ui and all scenario docs)
- **Screen** 256 × 224. The box is anchored at the bottom (top when the speaker stands low on screen): 240 × 64 px, a blue → dark-grey vertical gradient, 2-px white border, 1-px dark inner shadow.
- **With portrait:** a 48 × 48 static portrait at the left; text **3 lines × 24 characters**. **Without portrait:** **4 lines × 30 characters**. Variable-width 8 × 12 font. A **name tab** sits above the box's top-left edge, filled from the portrait ID (name tabs and portrait tiers in §16h).
- **Glyphs:** glyph advance ≤ 7 px including 1-px spacing, inside an 8 × 12 cell, so 24 characters fit the 174-px text area with a portrait and 30 fit the 226-px area without. A hangul syllable is a 12 × 12 glyph and **counts as 2 characters**.
- **Script tag syntax:** `[P:PC-02:smile]` portrait (ID:expression) · `[N:Stranger]` name override · `[W]` wait for button · `[PB]` page break · `[D:30]` delay in frames · `[C:gold]term[/C]` highlighted key term · `[SFX:piano_hit]` · `[MUS:LM-22]` music cue · `[K]…[/K]` hangul run · `[Q:option a|option b]` choice (each option ≤ 22 characters; the full line is spoken after selection) · `[SLIP:3]…[/SLIP]` a Bite Your Tongue prompt with its timer in seconds · `[in German]` / `[in French]` language tag.
- **State-change tags (binding; never invent others):** `[BP:PC-07:+15]` bond points · `[SEC:+5]` Secrecy, before the Renown multiplier · `[HZ:W3]` / `[HZ:R2]` Horizon (the value always comes from the LAW-23 table, never a literal) · `[CONF:CH05-03]` a Confided line (ID CH##-##) · `[OV:+1]` Own Voice · `[SHD:+1]` Shadow · `[REN:+n]` Renown · `[GOLD:+n]` money (F or ₩ by branch) · `[GET:KEY-16]` / `[GET:ITM-###]` item · `[FLAG:name]` and `[IF:name]…[/IF]` flags · `[EVE:-1]` spend an Evening (§11i) · `[LIGHT:Dawn]` set the Light State. HZ, CONF and SHD are never shown to the player.
- **Expressions:** neutral, smile, laugh, sad, angry, surprised, worried, determined, tender. Extras: Berlioz *grandiose*, Alkan *deadpan*, Lucile *guilty*, Liszt *rapture*, Chopin *ironic*, Min-jun *homesick*, Archon *cold*. Historical NPCs: neutral, smile, grave.
- **Length:** at most 6 boxes per speaker before another voice or an action; lectures at most 3 boxes (Tone Rule 3). **No narrator:** captions give only place and date, on two lines ("Faubourg-Poissonnière" / "March 1833").

### §16b How historical figures speak
Voices are drawn from letters, memoirs and journals: never caricatures, never saints, never modern therapists. No phonetic accents ("zis", "ze"); language is tagged (`[in German]`) and national colour comes from vocabulary.

| Figure | Voice notes |
|---|---|
| Berlioz | Exclamatory and literary (Shakespeare, Goethe, Virgil); mocks himself, then is suddenly tender |
| Delacroix | Measured, aphoristic; a dandy's irony hiding loyalty; "keeps notes" (no *Journal* in 1833) |
| Chopin | Polite and brief, dry irony, a wicked mimic; Polish only when moved; "Frédéric" in society, "Fryderyk" in private Polish scenes |
| Liszt | Warm, theatrical, generous, "mon ami"; grand gestures, sincere underneath |
| Alkan | Terse and dry; Scripture references; unexpected deadpan jokes |
| Farrenc | Precise, practical, ironic; speaks of facts and fees |
| George Sand | Frank, warm, provocative; calls Lucile *ma petite Lumière*; smokes |
| Heine | Barbed wit with melancholy underneath |
| Cherubini | Curt and Italianate; a formidable old schoolmaster |
| Thalberg | Impeccably courteous, aristocratic, competitive under the courtesy |
| Archon | Courteous, slow, utterly certain |

### §16c Min-jun's Korean identity
- In 1833 he presents himself openly as **from Corée (Joseon)**, a land almost no Parisian can place; that ignorance protects him. No false identity. (The Vicariate of Korea dates from 1831; French missionaries first entered Korea in 1836.)
- **Name order:** family name first. The period mistake "Monsieur Min-jun" is corrected with good humour ("Kang is my family name; in Corée it comes first"); society then says "Monsieur Kang"; friends move to "Min-jun" as intimacy grows: Berlioz from the CH-04 barricade, Lucile from the CH-08 kiss, the others after CH-09. Berlioz's letters spell him "Kang Minn-djoun"; Schumann calls him "Meister Morgen" (NPC-04).
- **Languages on screen:** Min-jun speaks Korean, English and French but no German (§5f). On the Rhine, Liszt, Mendelssohn or Clara interpret, and German lines carry `[in German]`. English with Vane is a private channel; English in front of Onlookers is a Slip (Secrecy +5). **CH-E1:** in Lucile's point-of-view scenes, Korean addressed to her shows as untranslated hangul until Min-jun translates; their own exchanges are tagged `[in French]`.
- NPC exoticism or prejudice ("Chinese?", "the Mandarin Mimic") is always shown as the speaker's ignorance and is answered or undercut on screen (Sand, Delacroix). Never mock-Asian dialect, accented spelling, "exotic" music cues, or martial-arts, K-drama or K-pop jokes about him.
- **Korean words:** hangul, then Revised Romanization in italics, glossed on first use in each scene: 괜찮아 (*gwaenchana*, "it's okay"). In 1833 scenes at most about **one Korean word per 20 boxes**, private moments only; natural use in Seoul (오빠 *oppa*, 교수님 *gyosunim*, 엄마 *eomma*, 동지 *Dongji*, 팥죽 *patjuk*). Personal names keep their bearer's spelling (Kang Min-jun, Kang Seo-yeon, Choi Jae-won, Yoon Mi-rae, Oh Sang-woo). Honorific registers are flagged in translation notes. The art doc owns a hangul glyph subset (≤ 400 syllables).
- His French is intermediate at first and fluent by Act II; his accent is part of being a foreigner.

### §16d French usage
Common words italicised on first appearance and left untranslated (*monsieur, madame, mademoiselle, salon, atelier, quai, fiacre, bal, sou, franc, diligence*). Anything else is glossed in line or by context; no untranslated full sentences except the portrait dedication and the plaque. NPCs measure in *lieues*; Min-jun saying "kilometres" is a slip. Names keep their accents. **Binding spellings:** Lucile (one *l* at the end), Théo, Brücke, d'Orsenne, Delorme, *Au Diapason Fêlé*, *La Lumière*, *Le Clavier des Âges*, Hanseong.

### §16e Depiction rules
- **Cholera:** never personified as a monster or boss and never a status name (Miasma is generic). Shown through absence: empty chairs, lime pits, orphans, memorial candles. Echoes are recordings, never sick people or corpses (LAW-07). No corpses in sprites.
- **Poverty:** specific, with dignity and agency; named people with trades; never a joke or scenery.
- **Riots and politics:** republicans' and workers' grievances are presented fairly and the Saint-Merry dead are honoured; the villains are Vane's provocateurs. No gore: human enemies flee, surrender or fall senseless. Rue Transnonain is never shown (LAW-19).
- **Real people:** no invented crimes or vices beyond the record, except the flagged Gisquet compromise. No romance or sexual content involving real people beyond documented relationships (Liszt–d'Agoult, Sand–Musset, Berlioz–Smithson). **Clara Wieck (14) is never romanticised.** **Sand staging rule (binding):** before CH-E2 ends, George Sand never shares a scene, a line or a battle with Liszt, Delacroix or Chopin. Their documented first meetings (Liszt autumn 1834, Delacroix 1834, Chopin late 1836) are bar-lines; Chopin and Sand never share a scene or a location in the game. Likewise "Florestan" is never introduced by name to Mendelssohn, Chopin or Liszt (R-56). Real deaths are never depicted; Chopin's illness is only foreshadowed (a cough); Schumann's later illness is never depicted or mocked, and Florestan and Eusebius are creative personae.
- **Faith:** Alkan's Judaism, Chopin's and Liszt's Catholicism and Marthe's vocation are respected.
- **No financier-cabal imagery whatsoever.** Archon's empire is industrial and military; no banks, money-lending or "hidden financier" tropes for any villain or creditor (Lucile's creditor is a colour merchant and a landlord).
- **Women:** the constraints on Farrenc, Sand and Lucile are shown, never endorsed.
- **Rating target: ESRB T / PEGI 12.** Fantasy violence, alcohol (taverns), tobacco (Sand's cigars), mild language ("sacrebleu", "damn"), disease and death referenced, romance up to a kiss.

### §16f Romance tone (A-2)
- **SNES staging:** sprites face each other; hand-hold animation; a kiss is implied by sprites leaning in, then a fade to black with star sparkles over LM-22. Maximum intimacy: a kiss or an embrace; no bedroom scenes. Witty first, tender second, never purple. Two kisses in the main game (CH-08 roof, CH-14 Night of Stars).
- **The betrayal, written so she stays sympathetic:** (1) her coercion (Théo, the debt) is shown early (CH-03 shadow scene, CH-07 point-of-view scene); (2) she lies about her errand, **never about her feelings**; (3) she stops reporting **before** the reveal (CH-08); (4) she acts to save him before she is exposed (CH-09 ledger) and confesses fully when confronted; (5) she pays a real price (marked for death, Théo taken); (6) she earns her way back through action (Nohant, freeing Théo, saving Delacroix). Min-jun may be angry, never cruel. Never frame her as "evil all along", and never punish the player for forgiving her quickly or slowly (both only feed Horizon).
- **She is never a prize.** She refuses things; her answer in CH-17 is hers. In the NO branch he stays **because she asks him to**, never by overriding her refusal (LAW-25). In CH-E2 **she proposes** (dawn on Montmartre, her 24th birthday, Sun 9 Feb 1834). In CH-E1 there is no proposal: a promise at the Bosingak bell.

### §16g Forbidden anachronisms (captions, documents, all 1833–34 speech)
Forbidden: "OK", "cool", "awesome", "teenager", "weekend", "boss" (as slang), "photograph"/"photo", "telegram", "microbe"/"germ theory" (Marthe's slip), "scientist" (say *savant*), "Impressionism"/"Impressionist" (coined 1874; only Min-jun says it, and others find it odd; the party calls Lucile's style ***la manière lumineuse***), "jazz" (only Min-jun and Julien, in private), "Haussmann", "métro", "Eiffel Tower", "Belle Époque", "Germany"/"Italy" as states (say Prussia, the German lands, Piedmont, the Italian states), "kilometres per hour", "electric light", and anything about the electric telegraph. **Allowed:** "télégraphe" for the Chappe optical semaphore, in everyday use in 1833 (a station stands on the tower of Saint-Pierre de Montmartre, LOC-P24); only the electric telegraph and "telegram" are forbidden. Railways exist in France (Saint-Étienne lines) but none in Paris until 1837. Monet, Pissarro, van Gogh, Seurat, Signac, Cézanne, Renoir, Degas, Manet (born 1832, an infant), Debussy, Ravel, Rachmaninoff, Scriabin and Prokofiev are named only in Min-jun's private speech (or by the cabal in private); in public each costs Secrecy (§11e), and NPCs must react.

### §16h UI and presentation spec (binding for art_and_ui and every doc that names a menu)
- **Main menu, in this order:** Items · Harmony · Repertoire · Equip · Opus · Ensemble (party, rows, swap) · Bonds (the Trust Network; Lucile's cracked-heart state) · Status · Sketchbook (KEY-09's last page plus Delacroix's Studies) · Almanach (entries for met NPC-##, LOC and glossary terms, written in period voice) · Config (§11j) · Save (at Lecterns and on overworld maps; §11h for the epilogues). CH-E1 adds the phone menu (§4f).
- **HUD:** the Secrecy candle top-right on Paris maps (the Canvas Ledger in the same slot in CH-E2); the Spotlight bar top-right in Seoul; the Light State icon top-left in battle; the Crescendo Gauge as a three-bar strip above the ATB window.
- **Battle layout (FF6 side view):** enemies on the left, party on the right in a diagonal column of four, the back row offset 16 px. **Octave formation (BOSS-27):** two columns of four at x = 168 and x = 200 on 32 × 32 cells, enemies confined to the left 120 px, and the ATB window split into two four-row panes.
- **Portraits:** **Tier A** (full expression set plus extras): PC-01–11, ANA-01–06, FIC-01 Théo. **Tier B** (neutral / smile / grave plus one bespoke expression): the people among GST-01–10, FIC-02–05, FIC-07–09, FIC-12–14, FIC-18–19, NPC-01–30 and NPC-33 (Rossini, the duel's judge). **Tier C:** no portrait; use `[N:]`.
- **Name tabs:** ANA-01 "Baron d'Orsenne" until Archon's Revelation (CH-12), then "Archon"; ANA-02 "Lord Vane"; ANA-04 "Mme Delorme", then "Delorme" from CH-12; ANA-05 "Maître Brücke", then "Brücke", then "Elias Brandt" after BOSS-30's conversation; Lucile "???" until she gives her name (CH-04); Schumann "Florestan" (R-56).
- **Name-length limits** (characters of the variable-width font): party names ≤ 9 (Delacroix fits); name tab ≤ 15; item, skill, Opus Score and Study names ≤ 16 plus an 8-px icon; enemy names in the battle list ≤ 14; captions ≤ 30 per line (place on line 1, date on line 2). Synergy and Cadenza names may run to 30 characters because they appear in the full-width battle banner; their menu entries use a ≤ 16 short form assigned by skills_and_progression. Long canonical names go in descriptions only. **Short forms:** *Vinaigre des Quatre Voleurs* → "Four Thieves"; *Chocolat de Santé* → "Chocolat"; *Metronome of Nohant* → "Nohant Metronome"; *Pleyel Tuning Hammer* → "Tuning Hammer"; *Gant de Cartouche* → "Cartouche Glove"; *Baton of Tomorrow* → "Tomorrow Baton"; Commandant Roussel → "Roussel"; Charles-Valentin Alkan → "Alkan"; Kang Min-jun → "Min-jun".

---

## §17 Glossary

| Term | Definition |
|---|---|
| **Almoner, the** | Sœur Marthe's place in the cabal: physician, no vote (§8) |
| **Amalgam zones** | CH-15 labyrinth areas where 1833 Paris and 2026 Seoul are fused |
| **Anachronic** | Flag on any future piece, style or CHRONO action; adds Heat before Onlookers (§11e) |
| **Anachronists** | Min-jun's name for the Brotherhood of the Stilled Hour (§8) |
| **Archon** | Cabal leader: Dr. Lazare Morvan, alias Baron Lazare d'Orsenne (ANA-01) |
| **Archon's Revelation** | CH-12: Archon tells the party Min-jun's origin; reactions by rank (§11f) |
| **Au Diapason Fêlé** | "The Cracked Tuning Fork": the Faubourg-Poissonnière tavern, Min-jun's first home (LOC-P04) |
| **Aubray Problem** | Paris branch: art historians' puzzle over Lucile's 1833 sketches (LAW-21) |
| **Bar-line** | A heavily documented historical event that resists change (LAW-15) |
| **Binding ring** | Black-enamel signet tying its wearer to Clef Stasis (LAW-11) |
| **Bite Your Tongue** | Timed dialogue choice: modern phrasing versus period phrasing (§11e) |
| **Black Coats** | Captain Marlot's day-hire bruisers in second-hand black frock coats, hired by Vane (§8) |
| **Blue Note** | Julien's +9% bonus to the Octave; also his Improvise misfire |
| **Brother from Tomorrow** | The friends' name for Min-jun; SYN-13; the portrait's dedication (LAW-26) |
| **Cabal Presence** | 0–3 masked cabal guests at a salon; multiplies Heat (§11g) |
| **Cadenza** | Desperation move at ≤ 25% HP for 100 Crescendo; unlocked in CH-09, then at bond rank 7 (§11d) |
| **Canvas** | Delacroix's dual-pigment command, the brief's "Visual Canvas" (§5c) |
| **Canvas Ledger** | CH-E2 tracker of Lucile's 19 surviving canvases during Delorme's Erasure; replaces the Secrecy HUD (§4f) |
| **Chronometric Survey** | The Seoul–Geneva agency of Brücke's remembered future (LAW-14) |
| **Clavier des Âges** | "Keyboard of the Ages": Archon's Engine (LAW-09) |
| **Clef** | One of seven resonant stone anchors under the Left Bank (LAW-02) |
| **Close Call** | Chase crisis triggered at Compromised Secrecy (§11e) |
| **Composed** | Enemy debuff from 10 Pointillé Dots: DEF/RES −50% |
| **Composure / Favor** | Duel HP and the duel's win bar (§11g) |
| **Confided lines** | Confidences Min-jun told Lucile in CH-05–CH-08, read back in her reports (§11f) |
| **Confidant** | A member told the truth at rank 10 |
| **Confrérie de l'Heure Immobile** | The Brotherhood of the Stilled Hour, the cabal (§8) |
| **Conseil de famille** | The family council before the *juge de paix* that names Aristide Farrenc Théo's *tuteur* (SQ-07, LAW-23) |
| **Cover Story** | A confidant's once-per-chapter event that lowers Secrecy |
| **Crescendo Gauge** | Shared 0–300 gauge paying for Synergies and Cadenzas (§11b); "Crescendo" always means this gauge |
| **Da Capo** | New Game+ (LAW-23); also the Recital that resets Coda |
| **Dead Heart** | The shattered Heart chamber after CH-16 (LOC-E03) |
| **Early Truth** | Confessing to Lucile at rank 7 during CH-06–CH-08 (§11f) |
| **Echo** | A resonance-imprint monster: a recording, not a soul (LAW-07) |
| **Ensemble** | The party system and its menu (§11a) |
| **Ensemble Scene** | Optional event that unlocks a Synergy without Min-jun |
| **Erasure** | Delorme's CH-E2 campaign against Lucile's legacy (Canvas Ledger) |
| **Evening** | A rationed slot for an optional salon, bond scene, Window Talk or inn rest (§11i) |
| **Eve of the Window** | Permanent save before BOSS-26 (§11h) |
| **Far end** | The future-side end of a rift: a Clef fragment (LAW-03) |
| **Fleeting Window** | The last 12-minute opening of the Seoul Door, 07:51–08:03, 22 Dec 1833 (LAW-13) |
| **Fracture / Mending** | Lucile's capped bond after the reveal and its repair (§11f) |
| **Grey Hand** | Archon's enforcers: about 40 veterans of the disbanded Garde royale under Commandant Roussel, one grey kid glove on the right hand (§8) |
| **Hanmadi** | CH-E1 collection of 40 Korean words Lucile learns (§4f) |
| **Harmony skill** | A character's solo art or spell, paid with INS (§11b) |
| **Heart, the** | Clef VII beneath the Panthéon (LAW-02) |
| **Heat** | Secrecy value of an Anachronic act (§11e) |
| **Hidden Study** | The sealed legation cellar under the Hanseong annex (LAW-22) |
| **Hint** | Safe preview of a member's reaction to the truth (§11f) |
| **Horizon** | Hidden −100…+100 value that, with the gate and final words, decides Lucile's answer (LAW-23) |
| **Hours, the** | The cabal's four ranks: Velvet, Gold, Iron, Smoke (§8) |
| **Invocation** | An Orchestral Summon held in an Opus Score (§11c) |
| **Jeong-dong Collection** | Legation crates recovered 2019, catalogued 2026; box JD-1888-07 (§3d) |
| **Kang Disclosure** | Min-jun's public testimony in Brücke's remembered history (LAW-14) |
| **Keeper's Choice** | Seoul-branch closing choice of how to tell the truth (LAW-24) |
| **Keepsake** | A friend's farewell gift in CH-17 (KEY-30): a Remembrance in Seoul, a forge component in Paris (§6) |
| **La Lumière** | The captured dirigible, formerly *La Sourdine* (§11h) |
| **La manière lumineuse** | The 1833 name for Lucile's style (§16g) |
| **Lantern Rule** | Tell friends who I am, never when they die (LAW-18) |
| **Lectern** | Save point: a glowing music stand (§11h) |
| **Les Amis** | The friends who swear the Pact of the Door and build it (LAW-22) |
| **Light State** | Battlefield lighting (Dawn, Noon, Dusk, Night, Candle, Fog, Gloom) (§10c) |
| **Living string** | The traveller with a resonant far end bound into the seal (LAW-10) |
| **Lost Era (tier)** | Unique ultimate equipment (§14) |
| **Lumière** | (1) Sand's pet name for Lucile; (2) Vane's code name for her reports; (3) LUMIÈRE, her own painting style; (4) the dirigible *La Lumière* |
| **Meister Morgen** | Schumann's name for Min-jun ("morning" and "tomorrow") (NPC-04) |
| **Mouth, the** | Clef I, cut from the same bed as the Heart; where Seoul Door arrivals surface (LAW-02) |
| **Octave of the Lost Era** | The eight-voice final Synergy (SYN-16) |
| **Onlooker** | Witness silhouette in public battles (§11e) |
| **Opus Score / OP** | Equippable sheet music that teaches skills; Opus Points earned per battle (§11c) |
| **Ossia** | The malleable passages of history (LAW-15); also the Seoul superboss (BOSS-31) |
| **Own Voice** | Hidden tally of Min-jun's own music (§11g) |
| **Pact of the Door** | The friends' oath to build the Door in Seoul (LAW-22) |
| **Pact of the Hour** | The cabal's 1826 founding oath, broken by Archon (§8) |
| **Passage Swoon** | 2–4 hours of unconsciousness after a crossing through a struck or collapsing rift; a held Window costs none (LAW-05) |
| **Phonautograph horns** | Brücke's sound recorders, used to capture the signature (LAW-12) |
| **Plein Air** | Lucile's command (§5c) |
| **Point of no return** | The Panthéon crypt-door prompt that ends every quest window (§0c) |
| **Rapture** | Salon and concert performance score (§11g) |
| **Recital** | Min-jun's three-movement performance command (§5c) |
| **Remembrance** | Seoul-branch summon from an 1833 keepsake (§6) |
| **Remediation Directive** | 2048 order to remove travellers, in Brücke's history (LAW-14) |
| **Renown** | Public fame 0–999 (§11g) |
| **Resonance Date** | A mass upheaval that rings the Clefs (LAW-04) |
| **Resonant** | A far end's latent state for a year and a day after a crossing: recordable, bindable, not passable (LAW-04) |
| **Reverie of the Window** | Post-game mode replaying CH-17 with the other answer (LAW-23) |
| **Rung** | A step on the cabal's escalation ladder (§4c) |
| **Secrecy Meter** | 0–100 gauge of how much of the future has leaked into public view; the cabal escalates as it rises (LAW-17, §11e) |
| **Seoul Door** | The Door in the Hidden Study, offset 193 years (LAW-03) |
| **Shadow** | 0–10 tally of future pieces claimed as his own; feeds the Shadow Virtuoso (LAW-20) |
| **Shift the Hour** | Lucile's sub-command that sets the Light State |
| **Signature** | A traveller's recordable resonance (LAW-12) |
| **Sketch / Study** | Delacroix's enemy-study collection that unlocks Canvas recipes (§5c) |
| **Spotlight Meter** | The Seoul-epilogue inversion of Secrecy (§11e) |
| **Stasis** | Slowed ageing near the living Clef network (LAW-11) |
| **Stilled Hour** | The seal chord, begun at the solstice instant (00:43, 22 Dec 1833); the cabal's name; BOSS-27 |
| **Swell** | Stacking buff, +10% ATK and ART per stack (§10d) |
| **Synergy** | A 2-, 3-, 4- or 8-member combination technique (§11b) |
| **Tablature** | Delorme's seven formula panels that tune the Clefs (LAW-08) |
| **Tacet** | Holding a full ATB to line up a Synergy (§11a) |
| **Tocsin Echoes** | Gunsmoke-and-alarm-bell Echoes of the barricades; never the shapes of the dead (LAW-07) |
| **Trust Network** | The bond-rank system with Min-jun (§11f) |
| **Tutti / Cue** | Berlioz's summon trigger and its section tokens (§5c) |
| **Unwritten** | CHRONO status; also the Paris superboss (BOSS-34) |
| **Velvet Leash** | Rung 2: keep him content in Paris (Vane, Lucile) |
| **Voice** | A party member's command in the Octave formation (§11b) |
| **Vow, the** | Min-jun's code: consent, credit, no harm and no profit (LAW-20) |
| **Watcher** | Cabal spy with a sight cone on town maps, from CH-06 (§11e) |
| **Window Clock** | CH-17's 12:00 count, running only in free movement (§11i) |
| **Window Talks** | Four night conversations (one mandatory) that add Horizon (LAW-23) |

*End of the Canon.*
