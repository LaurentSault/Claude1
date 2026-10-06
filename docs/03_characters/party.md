# The Ensemble — Playable Party

Status: v1.0 — 2026-10-06 · Owns: party members' biographies, appearance and sprite/portrait notes, personality, arcs, relationships, battle-identity overview, bond-arc overview (bond-quest beat outlines and rank-event titles), ending fates and credits afterwords for PC-01–PC-11, plus short dossiers for guests GST-01–GST-11 · Depends on: docs/02_lore/world_rules_and_lore.md (final); reads and stays consistent with dialogue_style_guide (format, voices), secrecy_and_trust (BP values, confession rules, Horizon wording), combat_ensemble (command rules), historical_cast (NPC ties), art_and_ui (sprite keys) · Canon: docs/00_CANON.md

> **Related docs.** Every skill, Étude, Study and Tutti named below is taken from `skills_and_progression.md` (v1.0), which owns every HRM, ETU, STU, TUT and OPS number; this doc only selects each member's signature handful. `side_and_bond_quests.md` did not exist when this file was completed: bond-quest part titles, rank events and beats are this doc's (CANON §0b: "bond-quest beat outlines"), and side_and_bond_quests owns their full content, maps and rewards. Where anything here seems to disagree with the canon, the canon wins.

## Contents

1. [How to Read This Document](#1-how-to-read-this-document)
2. [The Ensemble at a Glance](#2-the-ensemble-at-a-glance)
3. [PC-01 Kang Min-jun](#3-pc-01-kang-min-jun)
4. [PC-02 Lucile Aubray](#4-pc-02-lucile-aubray)
5. [PC-03 Hector Berlioz](#5-pc-03-hector-berlioz)
6. [PC-04 Eugène Delacroix](#6-pc-04-eugène-delacroix)
7. [PC-05 Charles-Valentin Alkan](#7-pc-05-charles-valentin-alkan)
8. [PC-06 Frédéric Chopin](#8-pc-06-frédéric-chopin)
9. [PC-07 Franz Liszt](#9-pc-07-franz-liszt)
10. [PC-08 Louise Farrenc](#10-pc-08-louise-farrenc)
11. [PC-09 Kang Seo-yeon](#11-pc-09-kang-seo-yeon)
12. [PC-10 Choi Jae-won](#12-pc-10-choi-jae-won)
13. [PC-11 Julien Marchetti](#13-pc-11-julien-marchetti)
14. [Guest Members (GST-01–GST-11)](#14-guest-members-gst-01gst-11)
15. [Relationship Matrix](#15-relationship-matrix)
16. [Ties Beyond the Party](#16-ties-beyond-the-party)
17. [Canon Additions & Cross-Doc Notes](#canon-additions--cross-doc-notes)

---

## 1. How to Read This Document

- **Every section has the same spine:** header table → appearance → personality and backstory → want vs need → arc by chapter → defining scene → battle identity → bond questline → ending fates (both branches, LAW-24/25) → credits afterword (historical members only).
- **Acts** (CANON §4a): Act I = CH-01–CH-04, Act II = CH-05–CH-09, Act III = CH-10–CH-13, Act IV = CH-14–CH-17, then the epilogue of the branch (CH-E1 or CH-E2). Each arc table runs chapter by chapter and is followed by a one-line **By act** summary.
- **Facts come from CANON §3–§11.** Stats, join levels and grades are CANON §5b and are not repeated. Commands are CANON §5c; their battle rules are combat_ensemble §4.6. BP values, Evening counts and confession rules are secrecy_and_trust §3–§5.
- **Defining scenes.** FF6 gives each member one scene the player remembers them by (Celes at the opera, Cyan's dream). Each member here has exactly one, and no two share a scene.
- **Bond tables** list one headline event per rank. Standard bond quests (BQ-PC03, 05, 07, 08, 11) open Part 1 at R2, Part 2 at R4, Part 3 at R5, Part 4 at R7 and the finale at R9 (secrecy_and_trust §3.5); other ranks are headed by that member's Evening scene of the same number (Evening scene *n* needs R*n*). Mandatory bond quests (BQ-PC04, BQ-PC06) are story-placed and listed in order; their R7–R9 thresholds have no scene of their own, because the CH-09 finale sets 1000 BP whatever rank the member holds (secrecy_and_trust §3.1). A rank row marked "—" in the Event column is reached by BP alone, and the row says what it unlocks.
- **Lantern Rule for the credits.** Tone Rule 6 forbids any friend's death on the ending roll. The afterwords in this file therefore narrate works and legacy only and are written for a proposed post-credits **Afterword** screen (CCR in the final section). Each is headed here with life dates for the writers; the screen itself shows the birth year alone and never states a death.
- **Scripted lines** follow CANON §16a and dialogue_style_guide §2.2 (one line = one box; target ≤ 60 characters with a portrait). Every line here is original game dialogue; none is a quotation of a real person.

---

## 2. The Ensemble at a Glance

### 2.1 Roster

| ID | Name | Role | Unique command | Weapon | Theme | Door emblem (LAW-22) | LM-01 note | Cadenza |
|---|---|---|---|---|---|---|---|---|
| PC-01 | Kang Min-jun | Buffer/debuffer, flex caster | RECITAL, CONDUCT | Batons | LM-02 | Baton | 1 · D | *Gaspard Unbound* |
| PC-02 | Lucile Aubray | Field controller, light caster | PLEIN AIR | Brushes | LM-03 | Brush | 8 · D (the octave) | *Lever du jour* |
| PC-03 | Hector Berlioz | Summoner, heavy hitter | ORCHESTRATE | Sword-canes | LM-11 | Sword-cane | 2 · E | *Dies irae* |
| PC-04 | Eugène Delacroix | Elemental spellblade, collector | CANVAS | Rapiers | LM-12 | Rapier | 3 · F♯ | *La Liberté guidant* |
| PC-05 | Charles-Valentin Alkan | Tank, burst damage | ÉTUDE | Hammers | LM-16 | Hammer | 4 · G | *La Machine* |
| PC-06 | Frédéric Chopin | Healer, time control | RUBATO | Quills | LM-13 | Quill | 5 · A | *Warszawa* |
| PC-07 | Franz Liszt | Offensive magic duelist | TRANSCEND → MEPHISTO | Sabres | LM-14 | Sabre | 6 · B | *La Clochette* |
| PC-08 | Louise Farrenc | Analyst, support | COUNTERPOINT | Folios | LM-15 | Folio | 7 · C♯ (the leading tone) | *Grand Tirage* |
| PC-09 | Kang Seo-yeon | Fast support, sustain | BOW | Bows | LM-32 (family) | — | — | *Arirang Variations* |
| PC-10 | Choi Jae-won | Combo striker | BEAT | Drumsticks | LM-24 (Seoul) | — | — | *Encore Stage* |
| PC-11 | Julien Marchetti | Gambler-caster | IMPROVISE | Canes | LM-08 | — | Blue Note (+9%) | *Changes* |

The eight permanent members are the eight notes of LM-01. Farrenc holds C♯, the leading tone on which every statement stops; Lucile holds the octave D that resolves it. That is the musical shape of the whole game: seven friends who are almost a home, and the one who completes it (CANON §15c).

### 2.2 Availability by chapter

● in the active roster · g guest · ◐ partial (see note) · — absent · blank = not yet joined or not in this branch.

| Ch. | MJ | LU | BE | DE | AL | CH | LI | FA | SY | JW | JU | Note |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CH-01 | ● | | | | | | | | | | | + Mathurin (GST-01) |
| CH-02 | ● | | ◐ | | | | | | | | | BE bursts into BOSS-02 on turn 5, joins at chapter end |
| CH-03 | ● | | ● | ● | g | | | | | | | AL guest for BOSS-04 |
| CH-04 | ● | | ● | ● | ◐ | | | | | | | Barricade forced (MJ, BE, DE); AL joins at end |
| CH-05 | ● | ● | ● | ● | ● | | | | | | | LU joins |
| CH-06 | ● | ● | ● | ● | ● | ● | | | | | | CH joins; leaves for Touraine Sun 11 Aug |
| CH-07 | ● | ● | ● | ● | ● | ◐ | ● | | | | | CH back for the duel, Sat 7 Sep (R-57) |
| CH-08 | ● | ● | ● | ● | ● | ● | ● | ● | | | | All 8 |
| CH-09 | ◐ | ◐ | ◐ | ● | ● | ● | ● | ● | | | | Three threads; LU leaves at dawn |
| CH-10 | ● | ◐ | — | — | ● | — | ● | ● | | | | LU Fractured; Sand and Corot guests |
| CH-11 | ● | ◐ | — | — | ● | ◐ | ● | ● | | | | CH joins at Liège; LU solo interlude |
| CH-12 | ● | ● | ● | ● | ● | — | ● | ● | | | | LU solo first; CH has bronchitis |
| CH-13 | ◐ | ● | ◐ | ● | ● | ● | ◐ | ● | | | | Stage MJ, LI (BE conducts); Rafters DE, LU, AL; Corridors CH, FA |
| CH-14 | ● | ● | ● | ● | ● | ● | ● | ● | | | ◐ | JU via SQ-21 |
| CH-15 | ● | ● | ● | ● | ● | ● | ● | ● | | | ◐ | Three parties; MJ always Party 2 |
| CH-16 | ● | ● | ● | ● | ● | ● | ● | ● | | | ◐ | Octave formation |
| CH-17 | ● | ● | ● | ● | ● | ● | ● | ● | | | ◐ | Window Clock; farewells |
| CH-E1 | ● | ● | | | | | | | ● | ● | | Seoul roster + Remembrances |
| CH-E2 | ● | ● | ● | ● | ● | ● | ● | ● | | | ◐ | + Offenbach, Marthe (g) |

---

## 3. PC-01 Kang Min-jun

| Field | Value |
|---|---|
| ID / name | PC-01 · **Kang Min-jun** (강민준); name tab "Min-jun" |
| Dates | b. 9 Aug 2003, Incheon. Paris branch only: d. March 1889, Paris (LAW-25) |
| Age in game | 22 → 23 on Fri 9 Aug 1833 (CH-06); 23 in CH-E1 |
| Role / archetype | Buffer/debuffer, flex caster · Bard / Conductor |
| Weapon | Batons (row-free); first weapon his tuning fork (Étude tier) |
| Unique command | RECITAL; CONDUCT from the end of CH-04 |
| Join / leave / rejoin | CH-P; never leaves (solo thread CH-09; on stage CH-13; always Party 2 in CH-15) |

### 3.1 Appearance

Five costume sets, chosen by chapter (CANON §5g; art_and_ui §4.2): **Modern** (navy padded jacket, grey hoodie, black jeans, white sneakers, canvas tote; CH-P–CH-01) · **Frock** (Étienne Gaudin's oversized bottle-green frock coat over the sneakers, cuffs turned back twice; CH-02–CH-04) · **Tailcoat** (midnight blue from Vane's tailor, CH-05–CH-17, kept after the betrayal as a reminder of what a leash feels like) · **Seoul** (black long padded coat, midnight-blue scarf; the tailcoat again for the premiere) · **Winter** (CH-E2 charcoal greatcoat). Black hair worn a little long, so the fringe falls into his eyes when he plays and he shakes it back between phrases. Slim, slightly stooped from practice rooms; the white sneakers are the silhouette's hook until CH-05 (the Hour of Smoke notices them, world_rules_and_lore §13.12).

- **Battle idle (2 frames):** baton loose in his right hand; he taps it twice against his left palm, the fallboard tap made portable.
- **Field idle:** after 8 seconds without input he hums (`hum`, a `note` balloon), and in 1833 maps the hummed phrase is LM-32's *Arirang* opening.
- **Portrait:** 5 busts; extra `homesick` (night, the phone, family). His `laugh` is wry and rare; `angry` is kept for harm done to friends.

### 3.2 2026: the life he falls out of

- **Family.** His father **Kang Do-hyun** (FIC-10, 55) runs **Kang Piano Service** in Euljiro: a narrow shop of felt hammers, a radio tuned to baseball, uprights waiting on their backs. Min-jun spent his childhood under pianos handing his father tools, which is why he can read a sabotaged action at a glance (CH-07, CH-08). His mother **Park Hye-jin** (FIC-11, 52) teaches piano and was his first teacher. Before his first recital, aged six, she told him to knock twice on the fallboard "so the piano knows you're coming"; he has done it ever since, and Delacroix will paint it (LAW-26). His sister **Seo-yeon** (PC-09) plays the violin and tells him he plays too loud. The family moved from Incheon to an apartment in Mapo-gu in 2012, when his father took over the Euljiro shop.
- **Conservatory.** A composition major at Hanseong (entered March 2022), a strong pianist, in his 3rd year (5th semester) in spring 2026 after 18 months as an arranger-pianist in an ROK Army band (Apr 2023 – Oct 2024), where he learned to arrange anything for whoever turned up to rehearsal. That skill is why he can talk to Berlioz about orchestration in CH-03. Mentor: **Prof. Yoon Mi-rae** (FIC-12). In term he shares a dormitory room in Jeong-dong with **Choi Jae-won** (PC-10).
- **Ambition.** Three years of Alliance Française evening classes in Mapo, taken in high school because he meant to study composition in Paris one day: hence his intermediate French in March 1833 (CANON §5f). He wants to write one large piece that someone else would want to play.
- **Flaws.** A perfectionist who has never finished a major work: his laptop holds a folder of first pages. His autumn 2025 jury piece, the *Jeong-dong Nocturne* (REP-30), was three minutes of a nocturne that stops; Prof. Yoon's note on it read "Beautiful. Where does it go?" He hides behind other men's genius (he is a superb interpreter), deflects with jokes, watches instead of acting, and at his worst mistakes homesickness for a moral position.

### 3.3 Personality and musical voice

Wry, self-deprecating, a watcher; kind by reflex, homesick by night; he hums *Arirang* when nervous and always names the composer ("It's Ravel's. Maurice Ravel. I only borrowed it."). He speaks of music in tempo, rests and cues, and of feelings almost never.

**His own voice** (LM-02): pentatonic melody with Korean colour over gently modern harmony. He hears in parallel ninths like Debussy and thinks in long-short 12/8 lilts he caught from Jae-won's samulnori rehearsals, and he builds pieces from the left hand up. His three finished works chart his growth (CANON §5f): the *Concerto for Two Pianos "Lost Era"* (REP-27, CH-13), *La Musique des étoiles* (REP-29, written on the Panthéon roof, Wed 18 Dec 1833) and the finale of *Harmonies de l'ère perdue* (REP-28, epilogues). The hidden **Own Voice** tally (CANON §11g) is his bond with himself.

### 3.4 Want vs need

**Wants:** to go home. **Needs:** to discover where home is, and to stop borrowing: to finish something of his own, and to hold himself to the standard he holds the cabal to.

### 3.5 The guilt arc

For two acts Min-jun is the honest traveller among thieves: he names Ravel when the Anachronists pass the future off as their own, and he coins the word "Anachronists" in CH-06 as an accusation. But every recital leaks the future into the record, and the person he has changed most is Lucile. He gave her an idea ("Then don't paint outlines"), she transformed it, and her canvases put a death order on her (LAW-21). In CH-12 Delorme turns his word back on him: "You gave a girl Monet and you call *me* a thief?" In BQ-PC08 Part 4 Farrenc asks the question he cannot dodge: did Lucile ask for it? He accepts the charge rather than defending himself. Lucile's answer ("You asked me. They never asked anyone.") forgives without absolving, and in CH-14 he swears **the Vow** (consent, credit, no harm and no profit), voiced by Farrenc and Delacroix. The "my own" salon option disappears. In Paris he goes beyond the Vow's letter and never performs a future piece for an audience again; in Seoul he tells the truth as music (Keeper's Choice (a)).

### 3.6 Arc by chapter

| Ch. | Beat |
|---|---|
| CH-P | *Clair de lune* in Room B-07; the hum; the Hidden Study; the eight-note dial; he steps through |
| CH-01 | Wakes among bones with a phone at 3%; Mathurin; fights Echoes with a hummed tone (REP-00) |
| CH-02 | Thrown out of the Conservatoire by Cherubini; plays for soup; first slip ("Debussy's *Suite bergamasque*"); Berlioz hears him |
| CH-03 | Delacroix's studio; Alkan; watches Chopin and Liszt; "Ondine" at Lavergne's; Vane leaves early |
| CH-04 | Quarry notes stolen; framed by a pamphlet; holds the barricade; "Min-jun" from Berlioz; receives the baton |
| CH-05 | Paris opens; meets Chopin and Liszt; Vane's patronage and tailcoat; Lucile's dawn lesson |
| CH-06 | *E = mc²*; names the Anachronists; turns 23 with a rain study in his hands |
| CH-07 | Nitinol; the Thalberg duel, won or lost; Théo carves his key |
| CH-08 | Restores Chopin's Pleyel with his father's hands; spares Julien; first kiss on the Salle Pleyel roof |
| CH-09 | Confesses to Chopin and Delacroix (the Lantern Rule); abducted, right hand injured; plays left-handed to survive; Lucile's reports in his hands at dawn |
| CH-10 | Hunted out of Paris; goes to Nohant anyway; Sand's questions; Mending 1 |
| CH-11 | Rhine; "Madame Schu—"; plays LM-22 alone on the Lorelei |
| CH-12 | Val-de-Grâce; Archon's Revelation; refuses a throne; Delorme's charge |
| CH-13 | His concerto premieres; eight bars for Lucile (defining scene) |
| CH-14 | The Vow; Night of Stars; writes *La Musique des étoiles* overnight |
| CH-15–16 | Walks his own remembered Seoul; first voice of the Octave |
| CH-17 | Farewells under the Window Clock; "Will you come with me?" |
| CH-E1 / CH-E2 | Seoul: home, the premiere, Brücke freed by a promise, the portrait at 23:00. Paris: he stays because she asks, plays the finale from memory and never writes it down |

**By act.** *I:* a refused foreigner survives on other men's music and finds a first friend. *II:* he becomes a salon sensation, names the Anachronists, and confides in the woman paid to report him. *III:* betrayed, hunted and injured, he learns that his own music is the only thing the cabal cannot steal. *IV:* he swears the Vow, writes the coda that holds the Window open, and asks the question. *Epilogue:* he answers "Where is home?" in one of two centuries.

### 3.7 Defining scene: "Eight Bars" (CH-13, Fri 6 Dec 1833)

The first performance of the first thing he has ever finished, before the King, with Liszt at the second piano and Berlioz on the podium, and Brücke's horns waiting to steal his signature. In the rafters Lucile is cornered. Min-jun takes his hands off his own concerto for eight bars, the most expensive silence of his life (Rapture −15), while Liszt covers both parts. Then the two of them modulate mid-movement, and the key change spoils the recording (LAW-12). The future he carried in his head was never what protected him; his own music and his own choice were. Afterwards she says only: "That was yours. Not the future's."

### 3.8 Battle identity

**Role:** sets auras that make the rest of the Ensemble better, then turns them into bursts. **RECITAL** runs a learned piece through three movements (aura → stronger aura → burst) and **breaks** on a hit of 20% max HP or more, Hush, Stagefright, Reverie or Fermata, with 1 turn of Stagefright. **CONDUCT** gives one ally an immediate ×1.25 action without breaking the piece. **Perfect Pitch** makes him immune to Out of Tune, Discord and, until CH-17, Unwritten.

| Signature skill | Source | Concept |
|---|---|---|
| *Resonance* | REP-00 | A hummed tone: I stuns every Echo, II shatters bone walls. The first thing he fights with |
| *Clair de lune* | REP-01 | Cantabile → LIGHT +25% → party heal; the piece that started everything (Heat 3) |
| The *Gaspard* triptych | REP-08, 09, 10 | "Ondine" (WATER aura, Lento → WATER burst), "Le Gibet" (RES −20% → Coda), "Scarbo" (SHADE aura → Delirium → SHADE storm): Vane's piece, at both ends of the game |
| *Vers la flamme* | REP-22 | Crescendo +20 at each of Archon's turns → FIRE + LIGHT nova (CH-16) |
| *A440* · *Overtone* · *Just Intonation* | HRM-PC01-01, -05, -08 | His own non-elemental tones: no resistance ever halves them; *A440* bites harder on Echoes |
| *Ritardando* · *Tempus* · *Accelerando* | HRM-PC01-09–11 | CHRONO, learned by story in the labyrinth and at the instant the Stilled Hour breaks: the residue of having been its string (Heat 5) |
| His own works | REP-27, 29, 30 | *Concerto "Lost Era"*, *La Musique des étoiles*, *Jeong-dong Nocturne*: Heat 0 from CH-13 (+3 Crescendo per movement until combat_ensemble's effect CCR is adopted) |
| *Gaspard Unbound* | Cadenza | Ondine, Le Gibet, Scarbo in one breath (WATER, SHADE, SHADE); with 3 confidants a second phase: Delirium on all, party Allegro |

**Best Synergy partners:** Lucile (SYN-01 *Clair de Lune Impression*), Chopin (SYN-03 advances his Recital), Berlioz (SYN-04, SYN-14), Liszt (SYN-02); Lucile and Delacroix together for SYN-13 *Brother from Tomorrow*. **Play pattern:** open Movement I, Conduct Alkan (a Conducted Étude cannot fail) or Lucile (a Conducted IMPRESSION keeps its chain), keep Varnish on him so no single hit breaks the piece. Against superbosses his tones and CHRONO are the bard's quiet answer: the one key bar 3 of BOSS-31 and BOSS-34 does not resist.

### 3.9 Bond arc

Min-jun is the hub and has no bond rank (CANON §5d). His growth is tracked by **Own Voice** (0–10): +1 each time he plays REP-30 at a salon instead of a future piece, +1 at key arc choices. At 6 or more the CH-13 concerto gains its extended cadenza phase, and Liszt hands him the annotated second-piano part afterwards: the secret Score OPS-25 *Lost Era*, whose exclusive *Second Piano* gives the whole party Swell +2 (skills_and_progression §4.3). His Lost Era baton (*Baton of Tomorrow*, Berlioz's CH-04 baton reforged by Théo) is earned by defeating BOSS-31 or BOSS-34.

### 3.10 Ending fates

| Seoul (YES, CH-E1) | Paris (NO, CH-E2) |
|---|---|
| Crosses awake, hand in hand with Lucile, at 16:52 KST. His mother sets the place at table she never cleared. To Det. Oh and the press he tells an amnesia story; the truth goes to his family, Jae-won and Prof. Yoon. He writes the finale of *Harmonies* on the blank last page and premieres it on New Year's Eve; he defeats Brücke in the Hidden Study and frees him with a promise ("I will tell no one anything that could hurt anyone."); at 23:00 he opens the packet with Lucile and finds Delacroix's portrait (the brief's image); a promise at the Bosingak bell. Default Keeper's Choice (a): he tells it as music. End card: *Harmonies de l'ère perdue* published (2027). | He stays because she asks, records a goodbye to his family with the friends crowding into frame, and throws the phone home. He supports Lucile before the Salon jury, sits for the portrait with his face in shadow at his own request ("History must not be able to find me."), and plays the *Harmonies* finale from memory at Chopin's 24th-birthday supper, never writing it down. He marries Lucile in June 1834, publishes obscurely as "M. Kang" with Maison Farrenc (*Nocturnes de Séoul*, 1840), helps crate the Door for his younger self in March 1886 and writes the hangul letter to Seo-yeon at 75. Every 5 March he taps Clef I twice; it never answers. Buried at Montmartre (1889); Lucile joins him in 1891. |

*Proposed ending-roll vignettes (epilogues.md owns the roll):* Seoul: Room B-07's sign-up sheet with two names on Thursday nights, his and Seo-yeon's. Paris: the Atelier at dawn, his hand lifting to tap a fallboard twice while Lucile, at the window, does not look round.

---
## 4. PC-02 Lucile Aubray

| Field | Value |
|---|---|
| ID / name | PC-02 · **Lucile Aubray**; name tab "???" until she gives her name (CH-04), then "Lucile" |
| Dates | b. Fri 9 Feb 1810, Paris. Seoul branch: lives on in 2026 (LAW-24). Paris branch: d. 1891, Paris (LAW-25) |
| Age in game | 23 through the main game and CH-E1; 24 on Sun 9 Feb 1834 (CH-E2), the morning she proposes |
| Role / archetype | Field controller, light caster · Chromomancer (FF5 Geomancer × FF6 Relm) |
| Weapon | Brushes |
| Unique command | PLEIN AIR (IMPRESSION → POINTILLÉ → IMPASTO → LUMIÈRE), sub-command *Shift the Hour* |
| Join / leave / rejoin | Joins CH-05; leaves at dawn CH-09; PC (Fractured) CH-10; solo interlude CH-11; solo, then rejoins for good CH-12 |

### 4.1 Appearance

Auburn hair under a faded **ultramarine headscarf** whose knot is her silhouette's hook; an ochre shawl; a paint-flecked grey dress; a brush roll at the right hip from which a pochade box unfolds (`easel_setup`). She stands with a slight forward lean, the posture of someone always looking at something. Sets: **1833** · **Interlude** (CH-11–CH-12 solo: a dark man's redingote and grey felt hat lent by Sand for the night streets) · **2026** (Seo-yeon's cream coat and red scarf) · **Winter** (CH-E2 grey wool pelisse).

- **Battle idle (2 frames):** she squints past the enemy at the sky and turns the brush in her fingers, reading the battlefield like a motif.
- **Field idle:** after 8 seconds she unfolds the pochade box and dabs (`paint`), then steps back with her head tilted (`step_back`).
- **Portrait:** 4 busts; extra `guilty` (CH-03–CH-11, whenever his kindness touches her errand; from CH-12 only in memory). *Proposed for art_and_ui:* a fleck of paint on her cheek whose colour tracks her current manner: Prussian blue (CH-05–CH-09), Berry ochre (CH-10–CH-12), chrome yellow (CH-14), a warm and a cool fleck together (epilogues).

### 4.2 Personality and backstory

Quick-tongued, proud, funny; a fierce haggler who names the exact colour where others say grey (madder, Prussian blue, lead white, gesso) and says "Look." as a whole sentence. She lies about her errand, **never about her feelings** (CANON §16f). She carries guilt like a stone in her pocket and would die for Théo.

She grew up in **Gilles Aubray**'s frame-gilding shop on the rue de la Harpe, among gesso, red bole, gold leaf and burnishing agates; she could lay leaf before she could spell. Her mother **Madeleine** died in 1822, when Lucile was twelve and Théo one, and Lucile became the boy's second mother. Gilding paid for two years in **Mme Daubrée**'s small women's atelier on the rue de Seine (FIC-16; 1826–1828, this doc's dating), and in 1828 she won a Louvre copyist's card, later earning state copy commissions for provincial churches (the CH-06 copy of Delorme's *Vow*). The École des Beaux-Arts was closed to her as to every woman (R-48). On 14 Apr 1832 the cholera took her father and left Théo with a weak chest, and 1,200 F of debt. Her entry for the **Salon of 1833**, a careful portrait of Théo whittling by the skylight, was refused. She lives in the attic at **7 rue des Grands-Augustins** (LOC-P20) and paints fans and snuffboxes for **Anselme Corbel** (LOC-P21).

### 4.3 George Sand

They met in **January 1831** in Corbel's workroom, where the newly arrived Aurore Dudevant, six years older, was painting snuffboxes for money. Lucile, twenty, showed her how to float copal varnish thin enough that a lid never yellows; Aurore paid her back by talking for three hours about novels. Sand calls her ***ma petite Lumière***, because she always moved her stool to follow the window light, and pushed her to try the Salon. Lucile calls her "Aurore" in private. **Sand is the only person Lucile never lies to**, so from April 1833 she simply stops telling her anything, and Sand notices the silence.

| Ch. | What Sand is to her |
|---|---|
| CH-06 | Sees *Le Pont Royal* in the attic and tells Corbel to hang it in his window: the showing Archon's renewed death order will cite, a guilt Sand carries to Nohant |
| CH-07 | Optional supper at the quai Malaquais, Musset sulking |
| CH-09 | Sends her and Théo to Nohant with a note to the household |
| CH-10 | Shelters her; asks Min-jun the Wings-or-Roots question in front of her; fights for her house (GST-02) |
| CH-11 | Lends the redingote; writes to Min-jun at Strasbourg against Lucile's wishes ("I have never obeyed her in anything that mattered") |
| CH-14 | Lucile alone sees her off at the Lyon mail-coach (Thu 12 Dec); the farewell letter (secrecy_and_trust §5.7) |
| Both branches | "G.S., déc. 1834" on the portrait's reverse (LAW-26) |

What each gives the other: Sand gives Lucile the example of a woman who chose her own name; Lucile gives Sand a friend from before *Indiana* who wants nothing from George Sand. That is why Vane's code name cuts so deep: he filed her reports under **"Lumière"**, the pet name she once let slip, so the one honest thing in her life became the label on her dishonesty. Sand: "He stole my word for her."

### 4.4 Poverty and leverage

*Flavour figures inside CANON §14's anchors (R-55); salons_duels_and_economy owns prices.*

| Item | Figure | Note |
|---|---|---|
| Her father's debts | **1,200 F** | To Maison Grimaud (gilding and colour supplies) and her landlord M. Bourdin (FIC-23). She will not set foot in Grimaud's until the debt is paid and buys at Couleurs Ravenel instead |
| Attic rent | 150 F a year | Skylight, two beds, a stove that smokes |
| Income | ≈ 20 F a week | Corbel pays 10 sous a fan leaf and 1 F a snuffbox lid; she paints about forty fans a week, which is why a painted fan is the one gift she hands back |
| Théo | medicine, food, warmth | Every sou above bread goes to his chest |
| Vane's offer (Sun 28 Apr) | debts bought and held unenforced; Théo's care at Sœur Marthe's dispensary; a **50 F** monthly "stipend for materials"; an introduction to the **Salon of 1834** and a purchase | Two weeks of fans every month, a doctor, and the door to the Salon |
| Vane's threat | seizure and eviction | Always delivered as a favour: "It would be a pity if Maison Grimaud grew impatient, my dear." |

### 4.5 Her art

| Manner | Grounded in | From | Canvases (LAW-21) | In battle | What it means to her |
|---|---|---|---|---|---|
| Gilt, fans, copies | Her father's trade; the copyists' gallery | Before CH-05 | — | — | Paints what sells; "Rain has no outline" is her frustration, already seeing colour in grey |
| **IMPRESSION** | Monet | CH-05; first canvas *Le Pont Royal, effet de brume*, Fri 2 Aug 1833 | 11, from August | A strike in the Light's first boosted element; +20% per consecutive turn | "Look at the water. Not the bridge." Joy, and the first theft she does not know she is part of |
| **POINTILLÉ** | Pissarro's divisionist years and rural subjects ("Pissarro's manner") | CH-10, the Berry fields | 9, from October | 8 small hits that build Dots toward Composed; or 8 dots of Cantabile, Allegro, Varnish on allies | Patience: painting a field one point at a time while she cannot touch him |
| **IMPASTO** | van Gogh | CH-14 | 4, in December | A heavy hit that sets Night; under Night, *Nuit étoilée* (8 LIGHT/SHADE hits that restore INS) | Feeling made visible: the stars over the Panthéon |
| **LUMIÈRE** | Her own | Epilogues | — | Two Light States at once | "Then I'll paint something he won't." Her own light |

Only Min-jun ever says "Impressionism"; Paris calls her style ***la manière lumineuse*** (CANON §16g). Every public showing is Anachronic (Heat 2–4) and draws a press item (LAW-21): Ingres calls *Le Pont Royal* "weather, not painting"; *Le Charivari* tells its readers to bring an umbrella; Delorme turns pale. Delorme burns five canvases in CH-11, so nineteen survive into the Canvas Ledger.

### 4.6 The recruitment (Sun 28 Apr 1833)

At Mme Lavergne's salon on Sat 27 Apr she sells painted fans from a tray and, like everyone in the room, stops breathing when a foreigner in a borrowed frock coat plays "Ondine". She sees Lord Vane leave early; she does not see that he watched her watching. The next morning he is waiting in Corbel's back room with her father's notes in his hand. He tells her the story the cabal tells (CANON §8d): a fragile foreign prodigy who speaks of a voyage home that would kill him; friends in society who want him safe in Paris; would she befriend him, make Paris dear to him, and report whom he meets, what he says of his origins, and above all whether he speaks of leaving, or of a "door". Nobody tells her the word "time". She agrees for Théo, for the roof, and because the story sounds like protection: at first she truly believes she is keeping a homesick boy from a fatal journey. The Salon introduction she agrees to for herself, and that is the part she is ashamed of. Vane champions her ("a leash of silk, not iron"); Archon approves ("cheaper than a bullet"); Brücke and Marthe object; Delorme sneers until August.

### 4.7 What she feels, stage by stage

| Ch. · date | What she does | What she believes | What she feels |
|---|---|---|---|
| CH-03 · 28 Apr | Takes Vane's purse (the shadowed hand) | She is protecting a sick man | Relief, fear, and a small cold shame about the Salon |
| CH-04 · Thu 9 May | Sketches him at the tavern as her first report; "Rain has no outline." / "Then don't paint outlines." | He is a job | Professional envy, then wonder. When he is framed, she gives the sketch of the paymaster to the Prefect instead of to Vane: the first crack |
| CH-05 | Joins; dawn lesson on the Pont des Arts; first weekly letter to Corbel's | Her letters are harmless observation | Delight in painting; a knot every Thursday |
| CH-06 | First canvas; "Seoul" in report no. 11; a rain study for his birthday (Fri 9 Aug) | His friends mean well | Falling for him. She leaves his mother's cooking out of the report ("not your business"); each confidence now feels like theft. If he gives her the Early Truth, she never writes it down |
| CH-07 | Her playable scene at Corbel's: a letter, a long hesitation, Vane's velvet threat (Théo, Grimaud) | Something is wrong with the story | Trapped. She delivers the letter |
| CH-08 · Sat 21 Sep | Sees at the charity concert that Vane's people meant the piano to hurt him; sends a false report ("He has given up any door"); first kiss on the Salle Pleyel roof | They are not protecting him | Fury, and a love she has no right to yet: she kisses him having stopped, not having confessed |
| CH-09 · 3–4 Oct | Told of the abduction by a panicked Corbel, breaks into the Hôtel de Vane, steals the ledger, sends Petit-Louis to the wedding supper; exposed at dawn by Julien's bundle | Nothing will excuse her | Plain shame without self-pity; the relief of the truth. She expects to lose him and gives him what she can |
| CH-10 | Nohant; fights beside him while Fractured; paints the Berry in points | She has no claim on him | Anger at herself worn as pride toward him; then, under Sand's roof, the first joke since the bridge |
| CH-11 · Thu 14 Nov | Théo taken; Marthe's note; she goes after him alone and asks Sand not to tell | She will not be rescued by the man she lied to | Terror for Théo, and resolve |
| CH-12 | Frees Théo herself; rejoins; reads him her unsent letters under Mignard's dome | She has earned the right to stand next to him | Standing |
| CH-13 | Saves Delacroix in the rafters; watches Min-jun leave his concerto for her | He chose a person over the future | Seen |
| CH-14 | Sees Sand off alone; the Night of Stars | — | Love, said aloud once |
| CH-15–16 | Sees his Seoul in the amalgam zones (with W4); sings the Octave's second voice | — | Wonder at towers of glass, or homesickness for rooftops, by Horizon |
| CH-17 | Answers the Question | — | §4.14 |

**By act.** *I:* a gilder's daughter sells fans, takes a lord's purse for her brother's sake, and sketches the man she is paid to watch. *II:* she learns to paint light, falls in love, stops reporting, steals the ledger, and confesses at dawn. *III:* Fractured and marked for death, she fights beside him, goes alone for Théo, and earns her place back by acting. *IV:* she paints the stars, hears the truth, and gives her own answer. *Epilogue:* in Seoul she walks into the century of light; in Paris she becomes Lucile Aubray in her own.

### 4.8 The betrayal, written so she stays herself

The six rules of CANON §16f are her spine: her coercion is shown early (CH-03 shadow, CH-07 her own scene); she lies about her errand and never her feelings; she stops reporting **before** she is exposed (CH-08); she acts to save him before she is caught (the ledger); she pays (a death order, five canvases burned, Théo taken); and she earns her way back by acting (Nohant, the abbey undercroft, the rafters). At the reveal she speaks in plain sentences, with no jokes and no excuses.

```
// CH-09 dawn, LOC-P22 Pont des Arts. Beat excerpt; act2.md owns the scene and its ID.
LUCILE   [P:PC-02:neutral] Vane paid my father's debts. He pays for Théo's medicine.
LUCILE   [P:PC-02:neutral] I wrote to him every Thursday. Everything you told me.
[IF:early_truth]
LUCILE   [P:PC-02:sad] I never told them. Not that.
[/IF]
LUCILE   [P:PC-02:neutral] I stopped after the concert. That changes nothing you heard.
MIN-JUN  [P:PC-01:sad] Everything I told you on the bridge. You wrote it down.
LUCILE   [P:PC-02:neutral] [GET:KEY-16] Yes. This is his ledger. Your door is in it.
{EMOTE:PC-02:...} {WAIT:40}
LUCILE   [P:PC-02:sad] [GET:KEY-09] Keep it. It's the only honest thing I own.
```

### 4.9 Reconciliation

Forgiveness is never a menu: the player is not punished for forgiving fast or slow, and both only feed Horizon (CANON §16f). The road back has three stations. **Nohant (CH-10):** Sand mediates, asks the Wings-or-Roots question aloud, and asks Min-jun whether he loved Lucile or the girl Vane wrote for him. Lucile fights at his side in the house-defence wave and the Vallée Noire, and at Mending 1 makes her first joke since the bridge: he still owes her two sous from the dawn lesson (*proposed for act3.md*). **The interlude (CH-11):** she chooses to act rather than wait. **The dome (CH-12):** after freeing Théo herself she reads him her unsent letters (KEY-24); Mending 2 unfreezes her bond, and the banked points arrive with one line on the Bonds page: "She kept writing." In CH-14 Vane, reading her early reports before he defects, gives the verdict history will not: "She stopped being mine long before she stopped writing." The two of them may burn the reports together (KEY-18, optional).

### 4.10 Want vs need

**Wants:** Théo safe, the debt gone, a canvas on the Salon's walls. **Needs:** to choose her own life after years of having it chosen for her by a death, a debt and a lord, and to find a light that is hers and not borrowed from masters she could one day meet in a museum.

### 4.11 Defining scene: "The Night of Stars" (CH-14, Wed 18 Dec 1833)

On the Panthéon roof, among David d'Angers' scaffolding, she paints ***La Nuit étoilée sur le Panthéon*** in IMPASTO: the dome as a black bell and the sky turning over it in coils of chrome yellow and Prussian blue. Window Talk 3 (mandatory) asks where he would hang it if he could hang it anywhere, and her closing line falls by Horizon band. He tells her the stars were once thought to make music, and she answers with the line the whole game rests on: "Then teach us the music of the stars." He writes *La Musique des étoiles* that night; Delacroix will paint her phrase into the portrait's dedication (LAW-26). The second kiss; "love" spoken once (dialogue_style_guide §7.6); rank 10; SYN-13 with Delacroix.

### 4.12 Battle identity

**Role:** she controls the battlefield's light. *Shift the Hour* (0 INS) sets Dawn, Noon, Dusk or Night; her styles hit in the Light's first boosted element; **Plein Air** adds +25% under Dawn, Noon or Fog, shows enemy affinities on her cursor and adds +25% preemptive chance outdoors. She competes with Delacroix over the Light (his Chiaroscuro wants Dusk, Night or Candle; she wants Dawn, Noon or Fog): Romantic colour against Impressionist light, made into a party-building choice.

| Signature skill | Source | Concept |
|---|---|---|
| IMPRESSION | Command (CH-05) | Chain strike, +20% per consecutive turn (max +100%) |
| POINTILLÉ | Command (CH-10) | 8 hits building Dots; Composed at 10 |
| IMPASTO / *Nuit étoilée* | Command (CH-14) | Sets Night; under Night, 8 swirling hits that restore INS |
| LUMIÈRE | Command (epilogues) | Two Lights at once |
| *Shift the Hour* | Sub-command | Painted Light, 0 INS |
| *Effet de brume* | R5 Signature (HRM-PC02-04) | WATER to all enemies, then sets Fog and Smokes them (base 60): the river mist of her first canvas |
| *Lever du jour* | Cadenza | Sets Dawn, LIGHT on all; phase 2 party Cantabile and Varnish |
| 별 *Byeol* | Seoul only (HRM-PC02-07; all 40 Hanmadi words) | LIGHT to all, party Inspired: her first written hangul word, "star" |

Her innate line is the party's LIGHT: *Lead White* (T2, at join), *Gold Leaf* (T3, CH-10) and *Zenith* (T4, CH-14), plus *Glaze* and *Varnish* for the front row. **Rank 10, *Golden Hour*** (the Night of Stars): *Shift the Hour* no longer resets IMPRESSION's streak, so she can repaint the sky mid-chain.

**Best Synergy partners:** Min-jun (SYN-01), Delacroix (SYN-10, SYN-13), Chopin (SYN-12 *Nocturne in Blue*), Farrenc (SYN-23 *Les Inadmissibles*), Berlioz (SYN-15 *Prometheus*), Julien (SYN-20 *Blue Hour*); in Seoul, SYN-19 *Samulnori*.

### 4.13 Bond questline: BQ-PC02 *The Hours of Light* and BQ-PC02b

Six sequential parts, each an hour of Paris light; none can be played while she is Fractured (secrecy_and_trust §3.5).

| Rank | Event | Title — beat |
|---|---|---|
| R1 | Evening 1 | **Fans Drying** — the attic at night, forty fan leaves pegged on strings, Théo asleep; she paints at speed and asks about his family (CONF CH05-02) |
| R2 | Evening 2 | **Other Men's Music** — the quays; he admits he has never finished a piece (CONF CH06-03); she admits she has never painted anything she owns |
| R3 | Part 1 · Dawn | **The Flower Quay** — dawn on the Quai aux Fleurs buying a sou of anemones for Théo's room; she teaches him to price a colour by eye. Unlocks SYN-01 |
| R4 | Part 2 · Morning | **Forty Fans** — he helps her finish a rush order for Corbel by noon and learns the arithmetic of her week |
| R5 | Part 3 · Noon | **The Refused Portrait** — behind the attic door, the Salon-refused portrait of Théo; she speaks of her father for the first time. Lifts the Noon gate; Signature *Effet de brume* |
| R6 | Part 4 · Afternoon (from Mending 2) | **The Gilder's Daughter** — she redeems her father's burnishing agate from the Mont-de-Piété and gilds the frame Delacroix ordered for the Algiers canvas, as Gilles did for ten years |
| R7 | Part 5 · Dusk (from Mending 2) | **The Lamplighter's Round** — at dusk she paints each *réverbère* along the quai as it is lit and asks what the lights of his city look like; she decides to sign nothing yet, "until I know whose century I'm in". (R7 in CH-06–CH-08 also opens the Early Truth) |
| R8 | — | Reached by BP after Mending 2 (CH-12–CH-14). Opens her Trios: SYN-15 *Prometheus* once Berlioz is also R8 (CH-14+), SYN-20 *Blue Hour* once Julien is also R8 |
| R9 | — | Reached by BP; no unlock of its own. Her finale is scripted, so the Night of Stars sets R10 from whatever rank she holds |
| R10 | Part 6 · Night (scripted) | **The Night of Stars** (§4.11) |

Evening scenes 3–6: **A Place at Table** (CONF CH07-02, his mother's empty chair) · **Indiana Aloud** (she reads Sand's novel to him, then makes him read a page back and corrects every vowel) · **Théo Counts** (from CH-07, once Théo is introduced: cards by candlelight; Théo counts every trick out loud) · **The Quays After Rain** (LOC-P22; the river violet under the arches).

**BQ-PC02b *A Harbour of Her Own*** (CH-14; Étretat → Le Havre): at the Étretat cliffs the Needle Echo (BOSS-39) cycles the Light from Dawn to Dusk; at Le Havre at sunrise she sets up before the harbour, the masts and the low red sun, and Min-jun goes quiet, because he has seen this painting in a book. She sees his face, turns her easel to the fish market waking on the quay, and paints *Le Havre, la criée au lever du jour*, which becomes her Salon entry No. 61 (KEY-40). In the Paris branch she will stand before Monet's harbour in 1874 and smile at the canvas she chose not to take (LAW-21).

**Confession.** The **Early Truth** (R7, CH-06 after lesson L1 to the end of CH-08; last chance on the Salle Pleyel roof after the kiss): she says it must stay "between us. Not one word of it on paper", and keeps her word. Otherwise Archon's Revelation tells her in CH-12, and the Panthéon roof plays as "The Truth, from You".

### 4.14 The Question: what decides her answer

She is asked "Will you come with me?" in CH-17 with ninety seconds on the Window Clock, and her answer is computed from the whole game (LAW-23), never chosen from a menu. Three things decide it, and each is a real part of her:

1. **The law (the gate).** Until Théo has a master and a guardian the Code civil will accept (SQ-07: Pleyel's indenture, Aristide Farrenc named *tuteur* by a *conseil de famille*, Louise his guardian in fact), she cannot go: the law bars her from her own brother's council. With the gate unmet she always refuses: "I will not leave Théo with nothing."
2. **Her imagination (Horizon).** How far her picture of her own life has already crossed the Window. Wings: the Early Truth, the Window Talks, the Nohant answer, seeing his Seoul in Party 2, the Treasury finale, Théo made safe, the lessons spent on tomorrow. Roots: the lessons spent on her own eyes, Delaroche come to see her canvases (SQ-11), the Montmartre atelier (SQ-12), the Seine at six hours (SQ-13), Sand's "Paris needs her", Corot's spring. The Sketchbook's last page (KEY-09) is her mind's picture: rooftops with Théo; the Pont des Arts at dawn; an unfinished page; a ship on a horizon; towers of glass in snow.
3. **His last words** (+5 / 0 / −5), phrased as feeling and never as instruction.

**If YES:** she trusts him completely, Théo is safe, and she wants to see the century where light-painting was born. **If NO:** her art and her people belong here; she wants to become Lucile Aubray in her own time, not a follower of masters she could meet in a museum; and she will not be the reason he never sees his mother again. She sends him home. When he stops at the light and asks her to ask for herself, she asks him to stay (LAW-25). Neither answer is a failure, and neither is a prize: she is never won (CANON §16f).

### 4.15 Ending fates

| Seoul (YES, CH-E1) | Paris (NO, CH-E2) |
|---|---|
| She steps into a snowy Dongji afternoon in her ochre shawl; by nightfall she is wearing Seo-yeon's cream coat and red scarf. She speaks 1830s French, corrects the translation app's grammar, learns hangul within a week (first written word 별, "star") and gathers 40 Hanmadi words. Electric light is "lightning in glass". At the "Light & Colour" exhibition she laughs at the room of haystacks, weeps before *Starry Night over the Rhône* ("They found it without a door"), and finds her own canvas labelled "Circle of Corot": "Let it be anonymous. It was a gift." At Yanghwajin she learns her sickly brother lived to 77 and crossed the world for her. She paints Seoul at night and reaches LUMIÈRE; a promise at the Bosingak bell (no proposal). End card: "In March 2027, papers arrived in the name of Lucile Aubray." | She refuses, then asks him to stay. Through the winter she prepares her Salon entry while Delorme's Erasure hunts her canvases (the Canvas Ledger). She **proposes** at dawn on Montmartre on her 24th birthday, Sun 9 Feb 1834; sits beside him for Delacroix, painted clearly at the window and looking at the viewer, and writes "Il est resté." on the reverse; leads the Brushwork duel before the jury (BOSS-32, Sat 15 Feb); is hung *au ciel* at the opening (Sat 1 Mar) and guards her canvas through BOSS-33. She signs "L. Aubray", grows LUMIÈRE ("Then I'll paint something he won't."), marries him in June 1834, stands before Monet's harbour at the first Impressionist exhibition (15 Apr 1874) and is buried beside him at Montmartre (1891). Art historians call her early sketches "the Aubray Problem". |

*Proposed ending-roll vignettes:* Seoul: a canvas of Jeong-dong at night drying among the felt hammers of Kang Piano Service, Min-jun's father's radio tuned to baseball. Paris: two easels in the Montmartre skylight, one canvas signed, one left blank for the morning.

---
## 5. PC-03 Hector Berlioz

| Field | Value |
|---|---|
| ID / name | PC-03 · **Hector Berlioz**; name tab "Berlioz" |
| Dates | 11 Dec 1803, La Côte-Saint-André (Isère) – 8 Mar 1869, Paris |
| Age in game | 29 → 30 on Wed 11 Dec 1833 (CH-14) |
| Role / archetype | Summoner, heavy hitter · Summoner / Knight |
| Weapon / command | Sword-canes · ORCHESTRATE (*Cue*, *Tutti*) |
| Join / leave / rejoin | Bursts into BOSS-02 on turn 5, joins at the end of CH-02; absent CH-10–CH-11 (newly married); rejoins CH-12; conducts (untargetable) in CH-13 |

**Appearance.** A shock of red hair like a struck match (two tiles of the sprite), hawk nose, green coat, cravat permanently askew; a borrowed black coat for the wedding (CH-09), cravat still askew. *Battle idle:* he conducts an invisible orchestra with his free hand, beat and rebound. *Field:* `read_review`, a newspaper crumpled into a ball. Portrait extra `grandiose`, whose `sad` arrives in one box and leaves in the next.

**Personality and backstory.** Volcanic, grandiose and very funny about it; generous with money he does not have; deeply afraid of being misunderstood. A doctor's son from the Dauphiné, sent to Paris in 1821 to study medicine, he fled the dissecting room for the Opéra's library and studied at the Conservatoire under Le Sueur. In September 1827 he saw the Irish actress Harriet Smithson play Ophelia and Juliet and never recovered; the *Symphonie fantastique* (5 Dec 1830) put his obsession into an *idée fixe*. He won the Prix de Rome in 1830 at the fourth attempt, lost his fiancée, the pianist Marie Moke, to Camille Pleyel while he was in Rome, and came back in November 1832 to a concert (9 Dec) that Harriet attended. In 1833 he is courting her against his family's wishes and her creditors, writing criticism he hates for money, and playing the guitar and flute: he is the one composer in the party who cannot really play the piano.

**Want vs need.** Wants Ophelia, a thousand musicians, and Paris to understand. Needs to marry a real, injured, indebted woman, and to write anyway, knowing France will misunderstand him for a century.

| Ch. | Arc beat |
|---|---|
| CH-02 | Drinking off a bad review at the tavern, hears *Clair de lune*: "a madman of the right kind" |
| CH-03 | Letter of introduction (KEY-07); takes Min-jun to Delacroix and Alkan |
| CH-04 | The barricade; calls him "Min-jun"; first Synergy with Delacroix (SYN-08); gives him a conductor's baton |
| CH-05–08 | BQ-PC03; the comic-awkward meeting with Marie Moke-Pleyel |
| CH-09 | Marries Harriet (Thu 3 Oct); leaves his own wedding supper to lead the rescue (defining scene) |
| CH-12–13 | Rejoins for Val-de-Grâce; conducts the *Concerto "Lost Era"* while Habeneck sulks (R-29) |
| CH-14–17 | Turns 30 (Wed 11 Dec); second voice of LM-01 (E); conducts *La Musique des étoiles* to hold the Window open |

**By act.** *I:* the drunk at the tavern who hears the future and decides it needs a friend; the barricade. *II:* courts an injured actress against his family, and leaves his own wedding supper to rescue the foreigner. *III:* a newlywed in Paris while the others tour; back for Val-de-Grâce, then on the Opéra's podium for a friend's concerto. *IV:* thirty, conducting the music that holds the Window open, and staying in a century that will misunderstand him.

**Defining scene: "The Wedding Menu" (CH-09, Thu 3 Oct 1833).** Four hours married, in borrowed finery at the British Embassy, Berlioz is handed an address at Bercy by a breathless eleven-year-old. Harriet tells him to go before he has finished asking. He writes on the back of the menu ("You married a man who writes symphonies about the scaffold; you cannot be surprised when he runs to one", world_rules_and_lore §13.14) and leads the rescue thread himself (BOSS-12 phase 1, without Min-jun). The man who loved an ideal proves he can love real people more than his own legend.

**Battle identity.** The party's summoner who also carries a blade. *Cue* adds a section token with a small effect at once (Strings heal the lowest ally, Winds a WIND jab, **Brass clears every Onlooker** and gives him Swell, Percussion an EARTH jab that may Stun, Chorus cures Hush and grants Cantabile); *Tutti* fires the Spectral Orchestral Summon matching up to three tokens (20 recipes, TUT-01–20, learned from his notebook pages). He uses his Opus Score's Invocation twice per battle; **Idée Fixe** adds +15% per consecutive Fight on one target. Signature skills: *Marche au supplice* (TUT-16, Brass + Brass + Percussion, EARTH + FIRE, massive single target) · *Songe d'une nuit du sabbat* (TUT-17, Brass + Percussion + Chorus, SHADE + FIRE on all; the SYN-14 Tutti) · *Fantaisie sur la Tempête* (TUT-19, Winds + Winds + Strings, WATER + WIND on all) · *Scène aux champs* (TUT-02, a lone Winds cue: WIND on one) · *Chœur d'ombres* (R5 Signature, from *Lélio*: SHADE on all, then Reverie) · *Coup d'archet* and *Estocade* (sword-cane cuts on the downbeat; *Estocade* feeds Idée Fixe) · *Cacophony* (any unknown recipe) · *Dies irae* (Cadenza: SHADE + EARTH, phase 2 Stagefright on all). **Rank 10, *Maestro*:** his gauge refills from 128 after a Cue, so a three-token Tutti arrives a turn and a half sooner. **Best partners:** Delacroix (SYN-08), Min-jun (SYN-04, SYN-14), Lucile (SYN-15), Liszt (SYN-14).

**Bond questline: BQ-PC03 *Idée Fixe*** (CH-03–CH-14; 8 Evening scenes at the tavern, then a boulevard café from CH-12).

| Rank | Event | Title — beat |
|---|---|---|
| R1 | Evening 1 | **Fourteen Ears** — he reads aloud the review that called him noise, and counts the critics |
| R2 | Part 1 (by CH-06) | **Pages from Rome** — redeem his pawned notebooks from the Mont-de-Piété: the Rome sketches, and folded inside them the *Marche au supplice* pages he carried to Italy and back (TUT-16) |
| R3 | Evening 3 | **The Guitar** — he plays it, badly and beautifully, and admits the piano defeats him. Unlocks SYN-04 |
| R4 | Part 2 | **Ophelia's Letter** — Min-jun translates Hector's overwrought English for Harriet, softening it; she laughs for the first time in a month |
| R5 | Part 3 | **Marie, Again** — at Pleyel's, Marie Moke-Pleyel; he confesses the pistols and the lady's-maid disguise of 1831 and laughs at the man who bought them. Signature |
| R6 | Evening 6 | **Money He Does Not Have** — he lends Mère Gaudin 50 F he must borrow from Liszt |
| R7 | Part 4 | **La Côte-Saint-André** — his father's letter refusing consent to marry an actress; he decides anyway. Cadenza |
| — | Story step (CH-09, Thu 3 Oct; every run) | **The Bride's Gift** — at the British Embassy supper, before Petit-Louis arrives, Harriet hands back the *Sabbat* pages he gave her in 1832: "Finish it for a living woman." *Songe d'une nuit du sabbat* (TUT-17) |
| R8 | Evening 8 | **A Thousand Musicians** — he asks, seriously, whether the future will ever give him a thousand players. Hint |
| R9 | Finale (CH-12–CH-14) | **The Real Woman** (after the wedding) — Harriet tells Min-jun the truth behind the *idée fixe*: he fears she is only a role. He writes eight bars for Harriet, not Ophelia, and the *idée fixe* is laid to rest; the storm pages of the *Tempête* fantasy go back into his notebook (TUT-19) |
| R10 | Confession (optional) | At the tavern or the café he asks whether France will understand him. "Not for a long time. Then the whole world will." He swears to conduct the future only under its makers' names, seeding the Vow's credit clause. Command upgrade *Maestro* |

**Ending fates.** *Both branches:* he stays in his own century; Var. I of *Harmonies*, *Allegro con fuoco*, is signed with a sword-cane, 1834. **Seoul:** his keepsake baton becomes a Remembrance (*Dies irae*); end card: *Harold en Italie*, Sun 23 Nov 1834. **Paris:** in the hall for the 22 Dec concert as Paganini watches from a side box; reads Paganini's note asking for a viola work (KEY-37) aloud to the Atelier; his baton forges the sword-cane *Idée Fixe*. *Proposed vignette:* rehearsing *Harold*, a viola part written for a man who will never play it.

**Afterword (1803–1869).** *Harold en Italie* was first heard on 23 November 1834. For three decades Berlioz paid his way as a critic, chiefly for the *Journal des Débats*. *Benvenuto Cellini* failed at the Opéra (1838); Paganini's gift of 20,000 francs made *Roméo et Juliette* (1839) possible. His *Treatise on Instrumentation* (1844) taught the century to write for orchestra, while *La Damnation de Faust* (1846) nearly ruined him. He wrote the *Te Deum*, *L'Enfance du Christ* and *Les Troyens*, which he never saw staged complete; that waited for the twentieth century. In 1865 he finished his *Mémoires*, among the liveliest books ever written by a composer.

---

## 6. PC-04 Eugène Delacroix

| Field | Value |
|---|---|
| ID / name | PC-04 · **Eugène Delacroix**; name tab "Delacroix" |
| Dates | 26 Apr 1798, Charenton-Saint-Maurice – 13 Aug 1863, Paris |
| Age in game | 34 → 35 on Fri 26 Apr 1833 (CH-03) |
| Role / archetype | Elemental spellblade, collector · Red Mage / Mystic Knight (+ Blue-Magic Studies) |
| Weapon / command | Rapiers · CANVAS (+ *Sketch* from CH-07) |
| Join / leave / rejoin | Joins CH-03; absent CH-10–CH-11 (the Salon du Roi commission; CANON §16e keeps him from Sand); rejoins CH-12; Rafters team in CH-13 |

**Appearance.** Dark hair and moustache, a black dandy's coat over a vermilion waistcoat (the sprite's "vermilion V"), a silk scarf at the throat that is never removed. *Battle idle:* rapier point low, he flicks an invisible speck from his cuff. *Field:* `cravat` (the scarf adjusted), `sketch`, `paint`. Proposed portrait extra `appraising` (fallback `neutral`); `tender` only after CH-09.

**Personality and backstory.** Aristocratic reserve, dry wit, a dandy in public; measured, aphoristic, exact about colour. Orphaned young (father 1805, mother 1814), trained under Guérin and befriended by Géricault, for whose *Raft of the Medusa* he posed as a young man, he made his name at the Salon with *The Barque of Dante* (1822), scandalised it with *The Massacre at Chios* (1824) and *The Death of Sardanapalus* (1827–28), and answered July 1830 with *Liberty Leading the People*. From January to July 1832 he travelled in Morocco with the comte de Mornay's mission, and a few days in Algiers gave him the interior he is now trying to paint. In 1833 Thiers has given him the Salon du Roi at the Palais Bourbon. His *Journal* lapsed in 1824 (it resumes in 1847), so he keeps notes; he hides a chronic throat ailment and a great deal of private tenderness. He is no Academician (1857).

**Want vs need.** Wants to win colour's war against line and keep his privacy intact. Needs to let one person in, and to let a younger painter's "heresy" sharpen his own colour.

| Ch. | Arc beat |
|---|---|
| CH-03 | Joins on Berlioz's letter; 35th birthday; BOSS-04 |
| CH-04 | *Liberty* made flesh on the rue Saint-Antoine; SYN-08 |
| CH-06 | Lucile's first canvas shown in his studio (Fri 2 Aug): fascinated, and furious that it works |
| CH-07–08 | *Sketch* and Studies (FF5 Blue Magic); ICE and BOLT pigments |
| CH-09 | BQ-PC04 finale; confession; the eight emblems (defining scene) |
| CH-12–14 | Steps beside Min-jun before Archon finishes the Revelation; saved by Lucile in the rafters (CH-13); voices the Vow with Farrenc (CH-14); SYN-13 |
| CH-16–17 | Third voice of LM-01 (F♯); holds an oscillator line at the Window; receives the Heart shard for the Door's dial (KEY-29) |

**By act.** *I:* a dandy who lends his studio to Berlioz's madman and his sword to a barricade. *II:* fights colour's war on the Algiers canvas, steals a violet from a younger painter, hears the truth and draws eight emblems. *III:* the Salon du Roi keeps him in Paris while the others travel; he rejoins for the abbey and is saved in the rafters by the woman he once called a heretic. *IV:* voices the Vow, holds the Window's chord, and carries home the shard that will lock the Door.

**Defining scene: "Eight Emblems" (CH-09, LOC-P06).** The Algiers canvas has its last colour; Min-jun has told him the truth. Delacroix does not answer. He takes his notebook and draws, one per friend: a baton, a brush, a sword-cane, a rapier, a hammer, a quill, a sabre, a folio. The player has seen these eight panels on a door in a cellar in Seoul (LAW-22). The guarded man has just designed a home for his brother, and does not know it yet.

**Battle identity.** CANVAS: two unlocked Pigments and a Subject (one / rank / all), a dual-element painted strike that ignores row; Pigments FIRE and WIND at join, EARTH and WATER (CH-05), ICE and BOLT (CH-08), SHADE (CH-10), LIGHT (R10). *Sketch* records 36 Studies (STU-01–36), each unlocking a named recipe; aimed at an Onlooker it clears them. **Chiaroscuro:** Canvas +25% under Dusk, Night or Candle; 25% counter when an ally Swoons. SHADE is ground in CH-10 for the Salon du Roi ceiling and first usable when he rejoins in CH-12. Signature skills: *Liberté* (story recipe, CH-04: FIRE + WIND on all, party Fortissimo) · *Chios* (CH-08: ICE + WATER on all at a kinder spread) · *Femmes d'Alger* (BQ-PC04 finale: LIGHT + FIRE on all, sets Candle so his next Canvases gain Chiaroscuro) · *Sardanapale* (CH-12: FIRE + SHADE on one, Stagefright) · *Barque de Dante* (R5 Signature: WATER + SHADE on all, Lento, the damned clinging to the boat) · *Missolonghi* (STU-23, sketched from Vane's animated collection: EARTH + LIGHT on all, party Varnish) · *Touche* (his Fights carry a pigment: the Mystic Knight's edge) · *La Liberté guidant* (Cadenza: FIRE + WIND on a rank, phase 2 party Fortissimo). **Rank 10:** the LIGHT pigment itself (canon). **Best partners:** Berlioz (SYN-08), Lucile (SYN-10, SYN-13), Chopin (SYN-21), Min-jun (SYN-05).

**Bond questline: BQ-PC04 *The Colours of Algiers*** (mandatory, CH-03–CH-09; 6 Evening scenes at the studio).

| Rank / step | Event | Title — beat |
|---|---|---|
| R1 | Evening 1 | **Notes on Fools** — he shows Min-jun the notebook where he keeps colours and fools |
| R2 | Evening 2 | **Byron by Lamplight** — the *Giaour*; he reads, Min-jun corrects one English word, and is forgiven |
| R3 | Evening 3 | **Rubens and Rain** — why shadows have colour. Unlocks SYN-05 |
| Part 1 (CH-03–04) | Story | **The Trunk from Tangier** — Moroccan silks, a brass tray, a sketchbook of a harem interior; the shadows will not come right |
| R4 | Evening 4 | **The Throat** — his voice fails at a dinner for Thiers' secretary; Min-jun covers; privacy is armour |
| Part 2 (CH-06) | Story | **Heresy** — after Lucile's canvas he copies her violet shadow onto a scrap, then pins the scrap above his easel |
| R5 | Evening 5 | **Constable's Green** — England, 1825. Signature *La Barque de Dante* |
| Part 3 (CH-07–08) | Story | **The Critic's Knife** — Delorme's press campaign calls the canvas "the Moroccan sickness"; he refuses to answer in print and answers on canvas instead, reworking his old *Scio* studies (*Chios* recipe) |
| R6 | Evening 6 | **The Dandy's Mirror** — the waistcoat is armour too |
| R7–R9 | — | Crossed by BP from Parts 2–3 and story events, or skipped outright when the finale sets 1000. R7 brings his Cadenza in CH-09; R8 his Trio eligibility (SYN-13 itself waits for the CH-14 story unlock) and the Hint, moot once he hears the truth |
| Finale (CH-09) | Story → R10 | **Women of Algiers** — the last colour laid; LIGHT pigment and the *Femmes d'Alger* recipe; the scripted confession (LM-12) and the emblems |

**Ending fates.** **Seoul:** paints *Le Frère de demain* from memory in February 1834 ("I will not fix a face I shall never see again"), Lucile dissolving into light at the window in her own touch; designs the Door that spring; gives Théo the portrait "for when your sister is found"; his variation (Var. II, *Sarabande*, 1841) has its bass corrected in pencil, and this doc names the corrector: Chopin. Remembrance: *La Liberté guidant*. **Paris:** paints the portrait from life in a playable sitting, Lucile clear at the window and Min-jun's face in shadow at his request; pleads for her as an outside advocate before the jury sits (no Academician, he has no vote), and if he brought Delaroche to her canvases in CH-14 (SQ-11), Delaroche speaks for her in session; *Women of Algiers* hangs at the same Salon. His keepsake sketch forges the rapier *Liberté*.

**Afterword (1798–1863).** *Women of Algiers in Their Apartment* was bought by the state at the Salon of 1834. Delacroix spent the next thirty years on walls: the Palais Bourbon's Salon du Roi and its library, the library of the Luxembourg, the ceiling of the Louvre's Galerie d'Apollon, the Chapel of the Holy Angels at Saint-Sulpice. In 1838 he painted Chopin and George Sand on one canvas, later cut in two. He resumed his *Journal* in 1847 and entered the Académie at last in 1857. The young painters who followed called him their father: Fantin-Latour painted an *Homage to Delacroix* (1864), and Signac traced *From Eugène Delacroix to Neo-Impressionism* (1899).

---

## 7. PC-05 Charles-Valentin Alkan

| Field | Value |
|---|---|
| ID / name | PC-05 · **Charles-Valentin Alkan**; name tab "Alkan" |
| Dates | 30 Nov 1813, Paris – 29 Mar 1888, Paris |
| Age in game | 19 → 20 on Sat 30 Nov 1833 (CH-12) |
| Role / archetype | Tank, burst damage · Monk (input techniques) |
| Weapon / command | Hammers · ÉTUDE |
| Join / leave / rejoin | Guest CH-03 (BOSS-04); joins at the end of CH-04; never leaves (Act III tour; Rafters team in CH-13) |

**Appearance.** Black coat, dark curls, slate-grey accents; rounded shoulders, as if expecting rain. *Battle idle:* his hands open and close, warming for octaves. *Field:* `read` (a Hebrew psalter), `tinker` (a watch movement), `play_piano` at the family pedal piano. Portrait extra `deadpan`; one `smile` per chapter at most, and its rarity is the point.

**Personality and backstory.** Deadpan, bookish, painfully shy in company; devout, reading Hebrew; fascinated by machines; dazzling at the keyboard, invisible in a salon. Born Charles-Valentin Morhange in the Marais, son of Alkan Morhange, who kept a small music school there (the children took their father's first name as a surname), he entered the Conservatoire at six, took the premier prix for piano at ten (1824) under Zimmerman and for harmony in 1827, and was playing salons as a prodigy before his voice broke. He has published variations (*Les Omnibus*) and his first *Concerto da camera* (1832). At nineteen he teaches, practises and hopes, quietly, for a Conservatoire chair.

**Want vs need.** Wants the world to behave like a mechanism: predictable, private, seventy-eight keys. Needs to choose to keep rather than hide, and to give pieces of himself away.

| Ch. | Arc beat |
|---|---|
| CH-03 | Guest in the Conservatoire undercroft he has known since he was six (BOSS-04) |
| CH-04 | His family shelters the barricade's wounded; he joins |
| CH-07 | "That spring is not steel." He spots nitinol at the Horlogerie Brücke |
| CH-08–11 | SYN-11 with Farrenc; the tour; on the Nohant house-defence roster with Farrenc |
| CH-12–14 | Turns 20 the week of Val-de-Grâce; the rafters; grinds three tuning forks to the tablature's wolf fifth |
| CH-15–17 | Gives out the forks (defining scene); translates the Frères' inscription; fourth voice of LM-01 (G); holds an oscillator line at the Window |

**By act.** *I:* a nineteen-year-old prodigy who would rather be anywhere than a salon; his family shelters the wounded and he follows them out of the house. *II:* reads a future alloy at a glance and imagines a machine in music. *III:* the tour's quiet anchor and the rafters' shield; turns twenty in the week of the abbey. *IV:* grinds the forks, keeps the door, and chooses to be a keeper rather than a recluse.

**Defining scene: "The Wolf Fifth" (CH-15, the crypt door).** Three parties must part in the dark. Alkan unwraps three tuning forks (KEY-32) he ground at his family's bench the week before, one for each party, each sounding the tablature's wolf fifth. He hands them out without a speech. "I will keep the door. Keeping is what I am good at." The recluse has made himself useful in three places at once.

**Battle identity.** ÉTUDE: enter a 3–8 input sequence within 2.0 s; correct fires, wrong plays *Fausse note* (a Fight); 12 Études (3 at Lv 11, then at Lv 14, 18, 22, 26, 30, 34, 38, 43, 50), named only from pre-1834 works or plain French terms. A Conducted Étude cannot fail. **Recluse:** last standing or alone in the back row, he holds Bulwark and +25% STR. Signature skills: *Martèlement* (ETU-01, his opener: an EARTH hammer-blow) · *Carillon* (ETU-06, Lv 22: BOLT on all) · *Moto perpetuo* (ETU-09, Lv 34: seven random hits) · *Fugato* (ETU-10, Lv 38: the eight-input single-target peak) · *Ostinato* (ETU-12, Lv 50: EARTH ×3.5, the figure that never stops) · *Les Omnibus* (R5 Signature: one sure blow on every enemy) · *Psaume* (a psalm under his breath: Bulwark and Cantabile) · *La Machine* (Cadenza: 12 EARTH hits, physical ×4.0, phase 2 Stun). **Rank 10, *Sang-froid*:** his input window widens from 2.0 to 2.5 s. **Best partners:** Min-jun (SYN-07, and Conduct), Farrenc (SYN-11), Liszt (SYN-22).

**Bond questline: BQ-PC05 *The Railway Étude*** (CH-05–CH-14; 8 Evening scenes at the family house, LOC-P36). Min-jun stays silent about *Le chemin de fer* (1844) and about Alkan's decades of withdrawal (LAW-18).

| Rank | Event | Title — beat |
|---|---|---|
| R1 | Evening 1 | **Seventy-Eight Keys** — he tests Min-jun's ear at the pedal piano, and approves with one word |
| R2 | Part 1 | **The Saint-Étienne Print** — a print of France's first railway; he has never seen a locomotive and means to |
| R3 | Evening 3 | **Ecclesiastes** — nothing new under the sun; he suspects the Preacher of rounding. Unlocks SYN-07 |
| R4 | Part 2 | **The Fire Pump at Chaillot** — they listen to the old steam pumps; he times the pistons on his watch |
| R5 | Part 3 | **Pistons in E** — he sketches an étude in the pumps' rhythm and tears it up twice. Signature |
| R6 | Evening 6 | **The Brothers Alkan** — a crowded household of musicians; he is the quiet one |
| R7 | Part 4 | **The Sabbath Light** — Friday supper at the house; he asks whether the world gets louder. Cadenza |
| R8 | Evening 8 | **A Chair at the Conservatoire** — the post he hopes for; Min-jun keeps his face still. Hint |
| R9 | Finale | **The Railway Étude** — he plays the machine he imagined, a perpetual motion of wheels; Min-jun recognises its shape and says nothing |
| R10 | Confession (optional) | At the pedal piano, the house asleep: "Does the Sabbath still fall on Saturday?" "It does." "Then the important things survived." The only confession that ends in a laugh. Command upgrade *Sang-froid* |

**Ending fates.** **Seoul:** co-executor of the Pact with Liszt and Théo, crating the Door in March 1886 at seventy-two; Var. III, *Ostinato*, hammer, 1886. His fork becomes a Remembrance (*La Machine*). **Paris:** helps destroy the cabal's last evidence (SQ-23); alone of the friends he asks to keep a single nitinol spring as a curiosity, turns it over for a long minute, and drops it into Pleyel's furnace himself ("It remembers its shape. I would rather it forgot."); his fork forges the hammer *Pédalier*. *Proposed vignette:* explaining an escapement to Théo at the Atelier bench.

**Afterword (1813–1888).** *Le chemin de fer* (1844) was among the first pieces of music about a railway. The *Grande sonate "Les quatre âges"* followed in 1847. Passed over for the Conservatoire's piano professorship in 1848, Alkan withdrew from public life for most of the next quarter-century and wrote some of the century's most formidable piano music in private: the twelve études in the minor keys, Op. 39 (1857), hold a symphony and a concerto for piano alone. He returned with his *Petits Concerts* at the Salle Érard (1873–1880). Pianists of the twentieth century rediscovered him.

---
## 8. PC-06 Frédéric Chopin

| Field | Value |
|---|---|
| ID / name | PC-06 · **Frédéric Chopin**; name tab "Chopin" ("Fryderyk" only in private Polish scenes) |
| Dates | 1 Mar 1810 (baptismal record 22 Feb), Żelazowa Wola – 17 Oct 1849, Paris |
| Age in game | 23; turns 24 on Sat 1 Mar 1834, the Salon's opening day (CH-E2) |
| Role / archetype | Healer, time control · White Mage / Time Mage |
| Weapon / command | Quills (row-free) · RUBATO (*Borrow*, *Repay*; *Tempo Rubato* at R10) |
| Join / leave / rejoin | Joins CH-06; in Touraine Sun 11 Aug – Sat 7 Sep (R-57), back for the duel; stays in Paris CH-10 (pupils, Op. 10 proofs); joins the tour at Liège (CH-11); in bed with bronchitis CH-12; Corridors team CH-13 |

**Appearance.** Ash-brown hair, a dove-grey coat, white gloves, a violet in the buttonhole; the slimmest vertical silhouette in the party. *Battle idle:* he tugs one glove finger straight, quill held like a conductor's pencil. *Field:* `mimic`, `play_piano`, and `cough` (an SFX-led foreshadowing, at most four uses, never a portrait). Portrait extra `ironic`; `angry` only for Poland; `laugh` only in private.

**Personality and backstory.** Elegant, private, fastidious, a wicked mimic of other pianists; a melancholy that turns to steel when Poland is mentioned. The son of a French-born teacher at the Warsaw Lyceum, a prodigy under Żywny and Elsner, he left Warsaw on 2 Nov 1830, was in Vienna when the November Rising broke out, and learned of Warsaw's fall in Stuttgart in September 1831. In Paris since that autumn, he made his debut at the Salle Pleyel on 26 Feb 1832 and lives by teaching aristocratic pupils at 20 F a lesson. In 1833 his Études Op. 10 appear, dedicated to Liszt, and his E-minor Concerto, dedicated to Kalkbrenner, whom he mimics with affection; in June he moves to the rue de la Chaussée-d'Antin. He dreads public concerts. The G-minor Ballade, begun in 1831, has no ending.

**Want vs need.** Wants a Poland that no longer exists, and never to play for a crowd. Needs to carry home inside the music, and to teach Min-jun, his mirror, how.

| Ch. | Arc beat |
|---|---|
| CH-03 | Seen from the gallery, playing Onslow four hands with Liszt (Tue 2 Apr) |
| CH-05–06 | Plays Op. 10 No. 3 for Min-jun at Pleyel's; comes to the Louvre to see Lucile's copy, fights, joins; blesses Min-jun's Nocturne Op. 9 No. 2 (REP-34) |
| CH-07–08 | Back from Touraine for the duel; his own Pleyel sabotaged and restored (KEY-17) |
| CH-09 | *Żal*; confession; the Lantern Rule (defining scene) |
| CH-11–14 | Joins at Liège (young Franck at the keyboard); counters the Lorelei's song; the corridors with Farrenc and Offenbach; Bach for three keyboards with Hiller and Liszt (Sun 15 Dec) |
| CH-16–E2 | Fifth voice of LM-01 (A); keepsake: a score page; in Paris, improvises a mazurka on *Arirang* and spends his 24th birthday at the Atelier |

**By act.** *I:* glimpsed from a theatre gallery, playing four hands with Liszt. *II:* the exile who will not play for crowds lends his own Pleyel to a concert for cholera orphans, watches Min-jun's hands restore it after the sabotage, finds his own way into the Ballade, and asks the question Min-jun feared. *III:* stays in Paris with his pupils and proofs, then meets the tour at Liège and counters the Lorelei's song; bronchitis keeps him from the abbey. *IV:* the corridors at the Opéra, Bach for three keyboards, and a fifth voice for the Octave; in Paris, a birthday kept at the Atelier by a friend who knows too much and says nothing.

**Defining scene: "Żal" (CH-09, LOC-P11).** He finds the door into the Ballade's ending himself, not by being told (history keeps its 1835 date, R-46). Then, while Min-jun plays Ravel's *Pavane* (REP-12), he asks the question Min-jun has feared since March. Min-jun answers with the only truth he will ever tell about a friend's future: "You will be played every day for two hundred years." The Lantern Rule is born (LAW-18), and Chopin pledges to help find the door and keep the secret.

**Battle identity.** *Borrow* takes 30% from one enemy's ATB and stores a charge (max 3); *Repay* gives every charge to one ally (+34% ATB each; three charges = an immediate turn, and it cures Fermata). **Sotto Voce:** enemies target him half as often; heals +20%; max HP −10%. Signature skills: *Borrow* · *Repay* · *Tempo Rubato* (R10 upgrade: Borrow hits all) · *Étude ut mineur* (R5 Signature, Op. 10 No. 12: the left-hand storm, 8 random SHADE + BOLT hits; the fury of 1831 turned outward) · *Cantilena* → *Mazurka* → *Valse brillante* (his heal line: H2 at join, H3 at his first CH-11 battle, H4 in CH-14) · *Encore* (revives at 25% or grants Encore) · *Fermata* (freezes one enemy's gauge) · *Warszawa* (Cadenza: party heal and Cantabile; phase 2 drains every enemy gauge by half and sets 3 charges). **Best partners:** Min-jun (SYN-03 advances his Recital), Liszt (SYN-09), Lucile (SYN-12), Delacroix (SYN-21).

**Bond questline: BQ-PC06 *Żal*** (mandatory, CH-06–CH-09; 6 Evening scenes at his apartment).

| Rank / step | Event | Title — beat |
|---|---|---|
| R1 | Evening 1 | **Six Friends and One Candle** — why he hates crowds; he mimics Kalkbrenner's spotless wrists |
| R2 | Evening 2 | **Violets** — Parma violets, the émigré post, a sister's handwriting |
| Part 1 (CH-06) | Story | **Letters from Warsaw** — a family letter delayed by the censors; "Say it as you would a name" |
| R3 | Evening 3 | **Pupils** — a countess who plays with her elbows. Unlocks SYN-03 |
| R4 | Evening 4 | **Pleyel's Voice** — the instrument he prefers when he is well, and why |
| Part 2 (CH-07) | Story | **Le Côteau** — back from Touraine with the *Grand Duo* and no ending for the Ballade. "Żal. Grief with a fist inside it." Min-jun gives the Korean word for the same thing: 한 (*han*) |
| R5 | Evening 5 | **Mimicry** — he plays "the Corean pianist" and Min-jun laughs. Signature |
| Part 3 (CH-08) | Story | **The Silenced Treble** — restoring his sabotaged Pleyel with Min-jun's workshop hands; the charity concert |
| R6 | Evening 6 | **Stuttgart** — the night he learned Warsaw had fallen |
| R7–R9 | — | Crossed by BP from Parts 2–3 and the concert, or skipped when the finale sets 1000. R7 brings his Cadenza in CH-09; R8 the Hint (moot once he hears the truth); he has no Trio (combat_ensemble §6.6) |
| Finale (CH-09) | Story → R10 | ***Żal*** — the Ballade's door; the scripted confession (REP-12); *Tempo Rubato* |

**Ending fates.** **Seoul:** Var. IV, *Mazurka*, quill, 1834; his score page becomes the Remembrance Seo-yeon calls most (*Warszawa*). **Paris:** Min-jun carries the knowledge of 1849 and never speaks it; when Chopin coughs, Min-jun closes a window or lends a scarf (dialogue_style_guide §7.7). The mazurka on *Arirang*; the *Harmonies* finale played at his 24th-birthday supper; his score page forges the quill *Żelazowa*. *Proposed vignette:* the Atelier's Pleyel in March light, a window closed against the wind by another hand.

**Afterword (1810–1849).** The G-minor Ballade was finished in 1835 and published in 1836, the year he met George Sand. Summers at Nohant (1839–1846) gave the world much of his greatest music; the twenty-four Preludes were finished in Majorca in 1838–39, followed by the B-flat-minor Sonata, the Polonaise-Fantaisie and the Barcarolle. His last Paris concert was at the Salle Pleyel on 16 February 1848. He never saw Poland again. Since 1927 Warsaw has held a competition in his name.

---

## 9. PC-07 Franz Liszt

| Field | Value |
|---|---|
| ID / name | PC-07 · **Franz Liszt**; name tab "Liszt" |
| Dates | 22 Oct 1811, Raiding (Doborján), Kingdom of Hungary – 31 Jul 1886, Bayreuth |
| Age in game | 21 → 22 on Tue 22 Oct 1833 (CH-10) |
| Role / archetype | Offensive magic duelist · Black Mage / Magic Knight |
| Weapon / command | Sabres · TRANSCEND, which becomes MEPHISTO (+ *Transcribe*) in CH-13 |
| Join / leave / rejoin | Joins CH-07; never leaves (leads the Act III tour; second piano in CH-13) |

**Appearance.** Long fair hair always in motion (his battle idle alone has 3 frames, for the hair), black frock coat, white cravat, silver accents; MEPHISTO frames recolour the coat deep violet. *Battle idle:* chin up, sabre on his shoulder, hair swaying. *Field:* `rapture`, `bow_audience`. Portrait extra `rapture`.

**Personality and backstory.** Magnetic, theatrical, competitive, generous to a fault, with a spiritual undertow beneath the showmanship. Son of an Esterházy estate official, taught in Vienna by Czerny and Salieri, he came to Paris in 1823 and was refused by Cherubini because the Conservatoire did not admit foreigners: he knows exactly how Min-jun's CH-02 felt. His father died at Boulogne in 1827; he wanted to become a priest, taught instead, and had his heart broken by a count's daughter. In April 1832 he heard Paganini and began to practise as other men pray. In 1833 he lives with his mother Anna on the rue de Provence, is newly in love with Marie d'Agoult, is transcribing Berlioz's *Fantastique* for piano and has written one piece called *Harmonies poétiques et religieuses*.

**Want vs need.** Wants to be the Paganini of the piano and to be adored. Needs to serve: to play second piano in a friend's concerto and turn rivalry into brotherhood.

| Ch. | Arc beat |
|---|---|
| CH-03 | Seen at the Smithson benefit |
| CH-05 | Met at Marie d'Agoult's, transcribing the *Fantastique* |
| CH-07 | Watches the rigged Thalberg duel, provoked and delighted; joins |
| CH-09 | Witness at Berlioz's wedding; plays *Le jardin féerique* four hands with Min-jun (REP-13) |
| CH-10 | The virtuoso's tour; the benefit at La Châtre; rides into the Vallée Noire (defining scene) |
| CH-11–13 | Interprets German on the Rhine; reunion with Czerny; MEPHISTO; second piano at the Opéra |
| CH-14–17 | Tells Belgiojoso about the embassy duel; BQ-PC07 finale; "If ever there must be a door, we will see to it"; sixth voice of LM-01 (B); keepsake: a glove his mother has mended |

**By act.** *I:* a star seen across a theatre. *II:* a rival at d'Agoult's and a delighted witness to a rigged duel, who joins because the foreigner made him want to practise. *III:* hides the hunted man inside his own tour, walks out on applause for him, interprets him across the Rhine, and plays second piano in his concerto. *IV:* faces the legend he wanted to become, promises a door, and becomes the friend who will crate it fifty-two years later.

**Defining scene: "The Unplayed Encore" (CH-10, La Châtre).** Liszt has kept the hunted Min-jun hidden in the most public place in France, his own tour, and stayed clear of Nohant ("a touring virtuoso calling on a notorious novelist would be in every paper"). Mid-applause at the La Châtre benefit, a Nohant stable-boy on a lathered horse brings word that the wolves are hunting in the Vallée Noire. Liszt bows once, leaves his encore unplayed, and rides into the Vallée Noire in concert dress (BOSS-13). The showman walks out on applause for a friend.

**Battle identity.** TRANSCEND casts two Harmony spells in one action for INS × 1.5. MEPHISTO (CH-13) adds *Transcribe*: re-perform the last skill used in battle by anyone, ally or enemy, at ×1.25. **Bravura:** +10% damage per consecutive action without being hit (max +50%). He owns the party's FIRE, ICE and BOLT. Signature skills: *Transcend* · *Transcribe* · *Harm. poétiques* (R5 Signature, *Harmonies poétiques*, his real piece of 1833: LIGHT on all, party Inspired) · *Con Fuoco* / *Glaciale* / *Sforzando* (his T2 trio at join, the pairs TRANSCEND was made for) · *Feroce* / *Cristallo* / *Fulmine* (T3, Act III) · *Tutta Forza* / *Hiver* / *Tempesta* (T4, CH-14) · *Ecstasy* (BQ-PC07's quest-locked reward, REP-21: FIRE + LIGHT on all, Heat 5) · *La Clochette* (Cadenza: 8 BOLT hits). **Rank 10, *Transcendence*:** TRANSCEND costs INS × 1.25 instead of × 1.5. **Best partners:** Min-jun (SYN-02 *Two-Piano Tempest*), Chopin (SYN-09), Alkan (SYN-22), Berlioz (SYN-14).

**Bond questline: BQ-PC07 *Transcendence*** (CH-07–CH-14; finale BOSS-36 in CH-14 only; 8 Evening scenes at Tortoni's).

| Rank | Event | Title — beat |
|---|---|---|
| R1 | Evening 1 | **Ices at Tortoni's** — he demands the future's gossip and gets Debussy's harmonies instead |
| R2 | Part 1 | **Mon ami, Again!** — a friendly cutting session; "as if the piano owed you money" |
| R3 | Evening 3 | **Cherubini Threw Me Out Too** — two refused foreigners. Unlocks SYN-02 |
| R4 | Part 2 | **The Rosary** — Anna Liszt's kitchen; the priesthood he was talked out of |
| R5 | Part 3 | **Marie** — d'Agoult asks Min-jun to stand near Franz; he performs even his silences. Signature |
| R6 | Evening 6 | **The Saint-Simonians** — art as priesthood; he half believes it |
| R7 | Part 4 | **The Broadsheet Devil** — a violin heard at night in the empty Opéra. Cadenza |
| R8 | Evening 8 | **Second Piano** — "For you. Tell no one." Hint |
| R9 | Finale | **Transcendence** — BOSS-36, Paganini's Shadow: he faces the legend he wanted to become; afterwards Min-jun plays him Scriabin's Fifth Sonata and he learns *Ecstasy* |
| R10 | Confession (CH-14 only) | Always "The Truth, from You" (the Revelation reaches him first). At Tortoni's after closing he asks to hear the future, though not his own: that he will write himself. Min-jun plays him Debussy. Command upgrade *Transcendence* |

**Ending fates.** **Seoul:** executor of the Pact in March 1886 with Alkan and Théo, on his last visit to Paris; Var. V, *Choral*, sabre, 1886; the portrait's provenance reads "gift of the Abbé Liszt and friends". Remembrance: *La Clochette*. **Paris:** executor with Théo and the elderly Min-jun and Lucile; at Belgiojoso's he turns pages for the Thalberg rematch (BOSS-35) while the princess renews her vow of a "proper" duel (R-10), the one he will play in 1837; his glove forges the sabre *Mephisto*. *Proposed vignette:* two pianos at Belgiojoso's, Liszt at the second, bowing to the first.

**Afterword (1811–1886).** With Marie d'Agoult he lived in Switzerland and Italy (1835–1839); they had three children. From 1839 to 1847 he toured Europe as no pianist had before, effectively inventing the solo recital, and paid for Beethoven's monument at Bonn. As Kapellmeister at Weimar (1848–1861) he wrote the symphonic poems, the B-minor Sonata and the *Faust* Symphony, and championed Wagner and Berlioz. He took minor orders in Rome in 1865, taught hundreds of pupils without fee, and divided his last years between Rome, Weimar and Budapest. His last visit to Paris was in March 1886.

---

## 10. PC-08 Louise Farrenc

| Field | Value |
|---|---|
| ID / name | PC-08 · **Louise Farrenc** (née Jeanne-Louise Dumont); name tab "Farrenc" |
| Dates | 31 May 1804, Paris – 15 Sep 1875, Paris |
| Age in game | 29 (turned 29 on 31 May 1833, before she joins) |
| Role / archetype | Analyst, support · Scholar / Red Mage |
| Weapon / command | Folios (row-free) · COUNTERPOINT (*Annotate*, *Canon*; *Fugue* Lv 22, *Cadence* Lv 30) |
| Join / leave / rejoin | Joins CH-08; never leaves (Act III tour; Corridors team in CH-13) |

**Appearance.** Dark hair in smooth *bandeaux*, a plum dress, ink-stained cuffs, a folio under one arm. *Battle idle:* she runs a pencil down a margin and turns a page. *Field:* `write`, `engrave`, `play_piano`. Proposed portrait extra `sceptical` (fallback `neutral`); `tender` for Victorine and Théo.

**Personality and backstory.** Brisk, rigorous, ironic; tender with her daughter; furious at injustice, especially the quiet kind. Born into a family of sculptors and raised among artists, she studied piano with Moscheles and Hummel and composition privately with Anton Reicha, since the Conservatoire's composition classes did not admit women. At seventeen (1821) she married the flautist Aristide Farrenc, who now runs a music publishing house at 21 rue Saint-Marc (LOC-P19); their daughter Victorine, seven, is already a pianist. She composes, publishes, keeps the firm's accounts in her head, and is not yet a professor (1842).

**Want vs need.** Wants her work counted: fees, credit, a seat at the table. Fears erasure. Needs to learn she will be forgotten and found again, and to fight harder for knowing it; and to forgive Min-jun the hypocrisy she names.

| Ch. | Arc beat |
|---|---|
| CH-05–07 | Absent but felt: the Period Scores Min-jun buys at Maison Farrenc carry pencilled fingering corrections in a firm hand, and Lucien, the engraver's apprentice at the counter (overworld_and_towns TF-030), only says that Monsieur Farrenc is at the printer's |
| CH-08 | Recognises Delorme's formulas as a tuning system of seven; joins; argues Haydn with Min-jun (REP-44) |
| CH-10 | Decodes the ledger at La Châtre (defining scene); with Sand, names the Code that bars them both from Théo's council |
| CH-11–13 | Reads "H.V. 1934" on the Seventh Panel; the timed corridors fight with Chopin and Offenbach |
| CH-14 | Voices the Vow with Delacroix; waits in the corridor during Théo's family council: "The law cannot see us. Then we shall be impossible to ignore." Lampshades the dirigible |
| CH-16–17 | Seventh voice of LM-01: C♯, the leading tone that waits to be resolved; keepsake: an engraved plate |

**By act.** *I:* not yet met. *II:* the hand in the margins of his Scores, then the mind that reads seven paintings as one tuning system. *III:* breaks the ledger by one candle, names the Code with Sand, reads "H.V. 1934", and holds the corridors. *IV:* names Min-jun's hypocrisy, forgives it, voices the Vow, and becomes Théo's guardian in fact while the law looks the other way.

**Defining scene: "By One Candle" (CH-10, the Lion d'Argent, Sat 19 Oct 1833).** While Liszt plays downstairs, Farrenc breaks Vane's auction-catalogue cipher: seven lots, seven churches and schools above the quarries, seven pitches, *ré* to *do♯*. "A scale that stops on its leading tone is not finished. It is waiting." Then, on the last page, "L. — to be removed." She does not wait for morning: Min-jun must know before he rides to Nohant. The party's conscience is the first to know Lucile's life is forfeit, and the first to act on it.

**Battle identity.** *Annotate* scans an enemy and places 3 crit marks; *Canon* makes an ally's every action echo its complement (attack → heal, heal → strike); *Fugue* (EARTH → WATER → LIGHT) and *Cadence* (party cleanse and heal) arrive with levels. **Equal Measure:** while she is active, reserve members receive 100% EXP, a nod to her real fight for equal pay. She owns the party's EARTH. Signature skills: *Annotate* · *Canon* · *Fugue* · *Cadence* · *Air russe* (R5 Signature, R-58: theme and three variations, four hits in EARTH, WATER, WIND, ICE) · *Marginalia* (HP and affinities of every enemy at once) · *Engraving* → *Burin* → *Copperplate* (her EARTH line, T2 to T4) · *Grand Tirage* (Cadenza: Annotates every enemy, then EARTH → WATER → LIGHT on all; phase 2 party cleanse and Inspired). **Rank 10, *Stretto*:** *Canon* marks two allies, the target and the most wounded. **Best partners:** Min-jun (SYN-06), Alkan (SYN-11), Lucile (SYN-23 *Les Inadmissibles*).

**Bond questline: BQ-PC08 *The Treasury*** (CH-08–CH-14; 8 Evening scenes at Maison Farrenc). She conceives her anthology of early keyboard music herself when Delorme threatens Pleyel's old-music archive; Min-jun recognises *Le Trésor des pianistes* (1861–72) and stays silent.

| Rank | Event | Title — beat |
|---|---|---|
| R1 | Evening 1 | **Precisely** — she prices his salon fees and finds he has been underpaid by a third |
| R2 | Part 1 | **Fees and Fugues** — she recovers the missing francs from Mme Lavergne, politely and completely |
| R3 | Evening 3 | **Engraver's Proof** — reading a plate backwards, like a mirror. Unlocks SYN-06 |
| R4 | Part 2 | **Victorine's Scales** — four hands with a seven-year-old who wants to hear about the balloon |
| R5 | Part 3 | **The Couperin Box** — Pleyel's archive of forgotten harpsichord books, which Delorme's agents bid for (she collects old temperament treatises). Signature |
| R6 | Evening 6 | **Reicha's Pupil** — the classes she was never allowed into |
| R7 | Part 4 (CH-12–14) | **You Call It a Gift** — "Did she ask for it? Answer the question." She names his hypocrisy over Lucile; he accepts it. Cadenza |
| R8 | Evening 8 | **Equal Measure** — what a woman's fugue is worth. Hint |
| R9 | Finale (CH-14) | **The Treasury** — Delorme's men raid Pleyel's archive; the archive saved, she carries out a first edition of Couperin's *Les Barricades mystérieuses* (OPS-30 *Barricades*) and resolves to publish three centuries of keyboard music; Horizon W5 if Lucile is present |
| R10 | Confession (optional) | Among the plates, after hours: does anyone play her music in 2026? "For a long time, no. Then they found you again." "Then I shall make it very difficult for them." Command upgrade *Stretto* |

**Ending fates.** *Both branches:* Théo's guardian in fact (SQ-07); Théo will cut the plaque with Maison Farrenc's old letter-punches. **Seoul:** Var. VI, *Invention à deux voix*, folio, 1842; end card: her professorship (1842); Remembrance *Grand Tirage*. **Paris:** Maison Farrenc publishes "M. Kang" (*Nocturnes de Séoul*, 1840); her Overture No. 1 is heard in CH-E2; her plate forges the folio *Trésor*. *Proposed vignette:* Victorine at the Atelier's Pleyel, her mother marking the fingering.

**Afterword (1804–1875).** In 1842 Louise Farrenc became professor of piano at the Paris Conservatoire, a post she held for thirty years: one of the most prestigious chairs in European music, and one almost no woman of her century was allowed to hold. She wrote three symphonies (1841–1847) and a Nonet (1849) whose success led her to demand, and win, pay equal to her male colleagues'. The Académie des Beaux-Arts twice gave her its Prix Chartier (1861, 1869). With Aristide she published *Le Trésor des pianistes* (1861–1872), three centuries of keyboard music in twenty-three volumes. Forgotten for a century, her music is played again.

---
## 11. PC-09 Kang Seo-yeon

| Field | Value |
|---|---|
| ID / name | PC-09 · **Kang Seo-yeon** (강서연); name tab "Seo-yeon" |
| Dates / age | b. 3 Apr 2007, Incheon · 19 |
| Role / archetype | Fast support, sustain · Dancer / Bard |
| Weapon / command | Bows · BOW (*Sostenuto* / *Spiccato*, switched without spending a turn) |
| Join / leave | CH-E1 only (joins on the night of the return, Tue 22 Dec 2026, *proposed*); in CH-E2 the playable, battle-free coda |

**Appearance.** Chin-length black hair, a charcoal padded coat, a burgundy knit, a violin case strapped across her back; she lends Lucile her cream coat and red scarf. *Battle idle:* bow point-down, she rolls her shoulders and flexes the fingers of her left hand. *Field:* `bow_violin`, `scowl_stomp`. Proposed portrait extra `scowl`.

**Personality and backstory.** Blunt, stubborn, loyal; clipped banmal with her brother, whom she calls 오빠 (*oppa*), often as a one-word reproach. Food is how she says love. A violinist since five, she entered Hanseong as a first-year in March 2026, two days before he vanished; she reported him missing on Fri 6 Mar, turned 19 a month later with an empty chair at the table, and took his Thursday slot in Room B-07 "so it stays warm". With Jae-won she ran the posters and the vigil (*proposed*).

**Want vs need.** Wants her brother back and an explanation. Needs to forgive him for leaving, and (Paris) to finish what he could not.

**Arc and defining scenes.** *Seoul:* **"Nine Months"**, the reunion ("오빠. Nine months. Nine. You could have left a note."); then the busking ladder, Lucile's clothes and hangul, and the clock tower. She keeps the family secret. *Paris:* **"The Bow Lifts"**, the coda (LAW-25): Room B-07, the hum swelling at 16:52, the study, the phone's recorded goodbye with the friends crowding into frame, the snowy campus, Prof. Yoon's call at about 17:10, the packet labelled 서연에게, the hangul letter asking her to write the score's blank last page, the portrait and the fallboard tap she recognises. The coda ends on her bow lifting.

**Battle identity.** *Sostenuto* heals the party each turn she keeps choosing it (+25% per consecutive turn, max +100%) and holds Cantabile; *Spiccato* lands four quick hits. **Sibling:** +20% TMP while Min-jun is active. Signature skills: *Sostenuto* · *Spiccato* · *Harmonics* (HRM-PC09-01: glassy flageolet tones, ICE T4) · *Col legno* (Stun, the bow's wood on the string) · *Con sordino* (Glaze on every ally) · *Arirang for Two* (SYN-17) · *Samulnori* (SYN-19) · *Arirang Variations* (Cadenza: party heal and Allegro; phase 2 Encore on Min-jun). No bond ranks; she already knows. Lost Era bow *Hanseong* from the busking ladder's Legend rank.

**Ending fates.** **Seoul:** the secret kept; she plays the opening of *Harmonies*' finale at the premiere's rehearsal while Min-jun writes the rest (*proposed*). **Paris:** the one who receives the past; she learns her brother lived to old age, married, and wrote to her at seventy-five.

---

## 12. PC-10 Choi Jae-won

| Field | Value |
|---|---|
| ID / name | PC-10 · **Choi Jae-won** (최재원); name tab "Jae-won" |
| Dates / age | b. 17 Jan 2003, Busan · 23 |
| Role / archetype | Combo striker · Thief / Monk |
| Weapon / command | Drumsticks · BEAT (timed combo up to 8 hits, *jangdan* cycles *semachi* → *gutgeori* → *jajinmori* → *hwimori*) |
| Join / leave | CH-E1 only |

**Appearance.** A mustard bomber with a samulnori patch, a black beanie, drumsticks in the back pocket. *Battle idle:* he spins one stick and bounces on his toes in 12/8. *Field:* `drum`, `pumped`. Proposed portrait extra `pumped`; his rare `determined` makes the room listen.

**Personality and backstory.** Loud, cheerful, rhythmic; a 4th-year percussion major who re-auditioned for a year to get in (2023) and leads the conservatory's samulnori club; calls his roommate 민준아 (*Min-jun-a*), punctuates with janggu syllables and chuimsae shouts, and is allowed one gamer line per scene. For nine months he kept Min-jun's half of their dormitory room exactly as it was.

**Want vs need.** Wants his friend back and the club's New Year's Eve set to go well. Needs to be taken seriously, and turns out to be the steadiest person in the room.

**Arc and defining scene.** Told the truth in CH-E1, he takes it with one question ("Was the food good?") and then never doubts it. **"Four In, Four Out"** (CH-E1, the clock tower, LOC-S10): as Brücke's gears grind and Min-jun's hands shake, Jae-won keeps time for the whole climb. "Breathe. Four in, four out. I've got the rhythm. You play."

**Battle identity.** Each perfect press adds +10%; a perfect 8-hit BEAT also steals. **Groove:** Crescendo gains ×1.25. Signature skills: *Semachi* → *Gutgeori* → *Jajinmori* → *Hwimori* (the BEAT cycles by level, Lv 40 to 49+, each faster) · *Sangmo* (the ribboned hat spins through the line) · *Chuimsae* (Fortissimo and Crescendo +10: the shout of 얼쑤 *eolssu*) · *Hwimori* (SYN-18 with Min-jun) · *Samulnori* (SYN-19) · *Encore Stage* (Cadenza: 8 input-free hits that steal; phase 2 Crescendo +40). No bond ranks. Lost Era sticks *Sinmyeong* from BOSS-31.

**Ending fates.** **Seoul:** keeps the secret; the samulnori club opens the New Year's Eve premiere. **Paris:** never learns the truth; in the coda a text from him lights Seo-yeon's phone as she crosses the snowy campus, his only line in that branch (*proposed*).

---

## 13. PC-11 Julien Marchetti

| Field | Value |
|---|---|
| ID / name | PC-11 · **Julien Marchetti** (ANA-03, "le Sorcier des accords"); `ANA-03` portrait until SQ-21, `PC-11` after (same art) |
| Dates / age | b. 14 Apr 1922, Paris-Belleville · 31 (body and lived; never bound) |
| Role / archetype | Gambler-caster · Gambler |
| Weapon / command | Canes · IMPROVISE (three reels of chord symbols) |
| Join / leave | Optional: recruited in CH-14 through SQ-21 "Changes" at the party average −1 (Lv 33), at 550 BP (R7); stays through CH-16 and CH-E2; not in CH-E1 |

**Appearance.** A blue-grey café coat, a loose cravat, a slouch. *Battle idle:* fingers drumming on the cane's head, shoulders loose in a swing beat. *Field:* `play_piano`, `sheepish`. Proposed portrait extra `sheepish`; `smile` grows more frequent after CH-14.

**Personality and backstory.** Charming, guilty, nervous; a natural sideman who was never a leader; apologises twice and mentions his mother. A Belleville boy, a session pianist in the Saint-Germain-des-Prés cellar clubs, he followed "a bass note nobody was playing" into the catacombs on 28 Jul 1950 and woke in the July Revolution. Delorme found him playing ninth chords for coins in a Palais-Royal café and made him the Hour of Smoke; he took a binding ring and has never put it on. His fame is Vane's Walkman and five mixtapes, transcribed by ear: music he never heard in his own life. He carried out rungs 1, 4, 6 and 8, believing the Pleyel would only "break". His first report on Min-jun ended: "I don't think he's dangerous. I think he's lost."

**Want vs need.** Wants absolution, and applause he does not have to steal. Needs to write one tune of his own, and to lead for eight bars.

**Arc and defining scene.** CH-08: BOSS-11; Min-jun spares him. **"The Bundle"** (CH-09, Bercy): sickened to learn Brücke made the Pleyel lethal, he guides the rescuers out and puts Lucile's reports in Min-jun's hands. "Her letters. All of them. Sorry. I'm sorry for all of it." CH-14: recruited; CH-15: Party 3 (BOSS-24 rises to 27,000 HP with him); CH-16: his Blue Note adds +9% to the Octave; CH-17: he chooses to stay.

**Battle identity.** IMPROVISE stops three reels: ii–V–I is *Turnaround* (party heal), ♭II ×3 is *Tritone Storm* (CHRONO to all), mismatches give *Blue Note*; every Improvise is Anachronic (Heat 3). **Sideman:** +20% damage acting right after an ally. Signature skills: *Turnaround* · *Tritone Storm* · *Blue Note* · *Dominant* and *Backdoor* (combat_ensemble §4.6) · *Walking Bass* (EARTH T4, at join) · *Rimshot* (Stun) · *Modal Vamp* (R5 Signature, his at once since he joins at 550 BP: four free Blue Notes) · *Changes* (Cadenza: auto-stops on *Turnaround* if anyone is below half HP, else *Tritone Storm*). **Rank 10, *Second Chorus*:** once per battle he may re-spin the third reel. **Best partners:** Lucile and Min-jun (SYN-20 *Blue Hour*); anyone fast enough to act just before him.

**Bond questline: BQ-PC11 *A Tune of My Own*** (CH-14; 4 Evening scenes at the Palais-Royal). He joins at R7, so Parts 1–4 and Evening scenes 1–4 are open at once; the finale opens at R9. No confession: he already knows.

| Rank | Event | Title — beat |
|---|---|---|
| R7 (join) | Part 1 | **Not My Songs** — he plays a tape tune at his old café; the crowd loves it; he cannot bear it |
| R7 | Part 2 | **Mon Vieux** — Belleville in the 1930s against Mapo in the 2010s; two boys and their mothers |
| R7 | Part 3 | **Eight Empty Bars** — Min-jun sets him eight bars with nothing borrowed; he fails twice |
| R7 | Part 4 | **The Walkman's Grave** — the Walkman has been silent since his borrowed dynamo was wrecked in BOSS-11; the party's own dynamo (KEY-28) could wake it, and he decides he will never transcribe from it again |
| R8 | — | Reached by BP; opens SYN-20 *Blue Hour* once Lucile is also R8 |
| R9 | Finale | **A Tune of My Own** — eight bars of his own: "Mine. Not on any tape. Play them back, slow." |
| R10 | — | 1000 BP with the finale done: command upgrade *Second Chorus* and the Lost Era cane *Blue Note* (CANON §14). No confession scene: he already knows |

**Ending fates.** **Seoul:** stays in 1833; his waltz "pour M." (1851) waits in box JD-1888-07; his cassette becomes a Remembrance (*Changes*). **Paris:** opens *Le Diapason Bleu* on the Boulevard du Temple (Jan 1834), a jazz club a century early by candlelight; listens to the tapes once more before the Walkman is buried (SQ-23); his cassette forges the cane *Blue Note*. History lets his borrowed chords fade; what lasts is the tune he wrote himself.

---

## 14. Guest Members (GST-01–GST-11)

Guests take an active slot at the chapter's anchor level, gain no EXP, cannot be re-equipped or swapped, and never join Synergies or Cadenzas (CANON §6; combat_ensemble §4.7). Historical guests' biographies and voices belong to historical_cast; each entry here gives only what the guest is *in the party*: why they fight, what their command says about them, one moment for the scenario writers, and one note for art.

### 14.1 GST-01 Mathurin Lebœuf
*FIC-09 · b. 1772 (61) · CH-01, Saint-Denis Galleries · LANTERN (P): reveals hidden paths, Unseen enemies and Echoes in walls, or Smoke (base 70) on one enemy · Tier B `squint`*

A wine-runner who has carried casks under the toll wall for forty years and hides from the same patrols as the stranger. He pities a lost foreigner and asks nothing; he touches Clef I for luck as quarrymen always have, and lends Min-jun his lantern (KEY-05). His command is his trade: he knows where the stone is hollow. **Moment:** at the foot of the rue Saint-Jacques shaft, rain running down the ladder, he refuses the foreigner's only coin ("Keep it. You'll need bread more than I need thanks."). He is Min-jun's first friend in 1833. **Art:** lantern glow drawn into the sprite.

### 14.2 GST-02 George Sand
*NPC-14 · 29 · CH-10, the Nohant house-defence wave only · NOVEL (P): Tragedy (Coda 20 on one), Romance (Reverie on all), Satire (Out of Tune and DEF −25% on all, 5 turns); a cane · Tier B `cigar`*

Her house and her friend are under attack, and she fights the way she writes: by choosing the genre. The wave's roster is Min-jun, Lucile and one of Farrenc or Alkan; she never shares a battle, scene or line with Liszt, Delacroix or Chopin (CANON §16e), so she is absent from BOSS-13. **Moment:** standing over a broken automaton, she recognises the Berry legend of the wolf-leader in the pack and gives the hint that silencing the piper scatters the wolves. **Art:** a 2-frame cigarillo smoke loop; Berry shawl over the grey redingote.

### 14.3 GST-03 Camille Corot
*NPC-13 · 37 · CH-10, Forest of Fontainebleau · SOUVENIR (P): misty party heal, then Varnish on all · Tier B `dreamy`*

A lone-rock Echo (LAW-07) stalks the sandstone where he paints, and he will not leave his easel to it. His command heals the way his canvases soothe, through a silver haze. **Moment:** he looks at Lucile's Berry studies and says, "You paint as I dream," then invites her to Italy next spring, which opens the Horizon choice R6 (Min-jun's "Go. Paint with him." or "Spring is far off."). **Art:** a soft brush trailing mist on SOUVENIR.

### 14.4 GST-04 Clara Wieck
*NPC-05 · 14 · CH-11, Düsseldorf · PRODIGY (AI, at her father's insistence): replays Min-jun's current Recital movement one tier higher, otherwise Caprice (Allegro on one ally) · Tier B `proud`*

When Mendelssohn's academy is ambushed she refuses to hide, and the command that copies Min-jun's playing a tier higher is the prodigy's pride made mechanical. She is never romanticised (CANON §16e). **Moment:** the "Madame Schu— Mademoiselle Wieck" slip (R-18): her father glares; no joke follows. **Art:** a little under adult height; music case clutched like a shield.

### 14.5 GST-05 Felix Mendelssohn
*NPC-07 · 24 · CH-11 · HEBRIDES (P): WATER + WIND wave on all; Song without Words cures Hush on the party · Tier B `amused`*

The host whose city the Seventh Panel threatens, newly the municipal music director. Amused by Liszt, by Czerny and by Min-jun's Debussy, he hears REP-40 named as Rachmaninoff's and asks no further question, as a gentleman. **Moment:** he conducts the academy's evening as if the ambush were a late arrival. **Art:** neat dark curls, conductor's poise.

### 14.6 GST-06 Carl Czerny
*NPC-08 · 42 · CH-11 · VELOCITY (P): party Allegro; out of battle, three School of Velocity drills (+1 TMP per member, max +3) · Tier B `chuckle`*

He came west to hear his old pupil and will not let him be shot. **Moment:** Min-jun plays him *Doctor Gradus ad Parnassum* (REP-04); he is not amused, then laughs, and opens the drills. **Art:** a teacher's frock coat and a metronome-steady stance.

### 14.7 GST-07 Robert Schumann, as "Florestan"
*NPC-04 · 23 · BOSS-14 only, aboard the Concordia · FLORESTAN / EUSEBIUS (AI): BOLT strikes or Cantabile, switching persona every 2 actions · Tier B `wistful`, name tab "Florestan"*

A Leipzig critic travelling incognito with Wieck, never introduced by name to Mendelssohn, Chopin or Liszt (R-56). His two personae are creative masks, never illness (CANON §16e). **Moment:** told that Joseon's name means "morning freshness", he christens Min-jun "Meister Morgen". **Art:** one sprite, two palettes: bright for Florestan, dusk for Eusebius.

### 14.8 GST-08 Jacques Offenbach
*NPC-03 · 14 · CH-13 corridors; CH-E2 · GALOP (P): one of six comic effects, weighted to good results · Tier B `cheeky`*

A substitute cellist in the Opéra pit who follows Chopin "for the adventure" and worships Franchomme. His random command is comedy kept in character (Tone Rule 8), never at the period's expense. **Moment:** in CH-E2 he carries Lucile's canvas on the approach to BOSS-33, cello case and all. **Art:** six GALOP frames; a cello case taller than his shoulders.

### 14.9 GST-09 Sœur Marthe
*ANA-06 · body 31 · CH-14; CH-E2 · TRIAGE (P): once per battle, full heal and every negative status cured on one ally · Tier A (`serene` proposed)*

The cabal's physician who defects after the Opéra: the future given away for no credit, the positive mirror of Gift, Not Theft. One perfect act of care per battle, then she fights with what she has. **Moment:** in the Seoul branch she receives Min-jun's letter asking her to watch over Théo; in the Paris branch she becomes the Aubray-Kangs' physician. **Art:** the Daughters of Charity's grey-blue habit and white cornette; a triage kneel.

### 14.10 GST-10 Sigismond Thalberg
*NPC-02 · 21 · optional: SQ-20 (CH-14); CH-E2, both visits as Belgiojoso's guest · THREE HANDS (P): bass EARTH, melody LIGHT, arpeggio WIND · Tier B `intent`*

Respect earned in a duel he knows was rigged in his favour, and an apology made in person. His three hits are the "three-hand" device he will unveil in Paris in 1836 (R-10). **Moment:** after the BOSS-35 rematch, won or lost, he bows to Min-jun exactly as deeply as Min-jun bows to him. **Art:** black and pearl-grey, kept clear of the party's key colours.

### 14.11 GST-11 Théo Aubray
*FIC-01 · 12 · CH-12, the Val-de-Grâce escape · no command: an escort with a 2,000-HP bar · Tier A (`brave` proposed)*

The boy the whole romance turns on. He calls Min-jun "Monsieur Corée" until the abbey, and "Min-jun" ever after; he whittles a fused-hands key in CH-07, casts the real one in Pleyel's foundry the next spring, and half a century later carries it to Seoul. **Moment:** running out of breath before he runs out of words, he counts the abbey steps aloud so his sister will not worry: "Thirty-one. I counted. I'm fine." **Art:** a cap too big, Lucile's ultramarine muffler, a cower frame; never shown coughing in a portrait.

---

## 15. Relationship Matrix

One line per pair (55 pairs). Historical friendships earlier or closer than the record are R-00 liberties.

| Pair | Relationship |
|---|---|
| MJ–LU | Teacher and pupil who swap roles: she teaches him to look, he tells her not to paint outlines; trust broken at dawn, rebuilt by acts; the Question |
| MJ–BE | His first friend in Paris and first to use his name; the baton; Berlioz conducts his concerto |
| MJ–DE | The guarded dandy who becomes his brother, designs his door and paints his face in shadow |
| MJ–AL | Two quiet men; Conduct makes Alkan's Études flawless; Min-jun keeps Alkan's future silent |
| MJ–CH | Mirror exiles, *żal* and *han*; the Lantern Rule is born between them |
| MJ–LI | Rivals across two pianos who become brothers; the showman plays his second piano |
| MJ–FA | His conscience and his ledger: she names his hypocrisy, forgives it, and publishes him (Paris) |
| MJ–SY | Siblings: fury as love; she kept his slot warm and, in Paris, receives his past |
| MJ–JW | Roommates; the friend who keeps time when his hands shake |
| MJ–JU | The thief he could have become; spared, he becomes a sideman, then a composer |
| LU–BE | He calls her colour "symphonic"; she paints Harriet a white-rose fan when the newlyweds' rooms are bare (CH-12+); *Prometheus* (SYN-15) |
| LU–DE | Light against colour, rivals over the Light State; her father gilded his frames; she saves him in the rafters; he paints her into the portrait (SYN-10, SYN-13) |
| LU–AL | He asks the weight of a cake of Prussian blue; she asks him to sit; he lasts four minutes |
| LU–CH | Born three weeks apart; he came to the Louvre for her copy; *Nocturne in Blue*; in Paris his 24th birthday is kept at her Atelier |
| LU–LI | He calls her canvases "transcriptions of weather", his highest praise; she makes him carry the easel |
| LU–FA | Two women the law will not seat: *Les Inadmissibles*; Farrenc becomes Théo's guardian in fact |
| LU–SY | Seoul: the cream coat, the red scarf, and hangul lessons at the kitchen table. Paris: Seo-yeon meets her only in a portrait and a video |
| LU–JW | Seoul: he explains that the subway is not the monster, rush hour is; noraebang. Paris: never meet |
| LU–JU | He exposed her; he was also the only cabal member who flinched; *Blue Hour* (both R8) is mutual forgiveness |
| BE–DE | "All brass and no drawing," says Delacroix, and stands beside him on every barricade (SYN-08) |
| BE–AL | The loudest and the quietest; Alkan answers Berlioz's rhetorical questions literally |
| BE–CH | Berlioz adores his playing and cannot forgive his indifference to orchestras; Chopin mimics his hair |
| BE–LI | Liszt transcribes his symphony and witnesses his wedding; *Symphony of Tomorrow* (SYN-14) |
| BE–FA | He sits on Théo's family council that bars her, and votes the way she tells him |
| BE–SY | Never meet; his baton is a Remembrance she can call; in Paris she sees him conducting the friends in the phone video |
| BE–JW | Never meet; Jae-won once played the four-timpani thunder of the *Scène aux champs* in an exam, and bows to its author's Remembrance |
| BE–JU | He calls Julien a pickpocket of tunes, then asks for the eight bars twice |
| DE–AL | Delacroix sketches Alkan's hands; Alkan permits it, once |
| DE–CH | Both confess in CH-09; *Polonaise of Exiles*; their real friendship begins around 1838; Chopin corrects the bass of his 1841 variation |
| DE–LI | Two dandies, one theatrical and one reserved; wariness turns to respect at the Window |
| DE–FA | She reads the equations in Delorme's panels; he refuses to destroy any painting; together they voice the Vow |
| DE–SY | Never meet; in the Paris coda she studies his portrait and his initials |
| DE–JW | Never meet; to Jae-won his Remembrance is "the painter who sets fire to the platform" |
| DE–JU | He sketches Julien at a borrowed piano and gives him the sketch; Julien keeps it |
| AL–CH | Future neighbours (Square d'Orléans, from the 1840s); in the game, devout men who understand silence |
| AL–LI | *Rival Virtuosi*; co-executors of the Pact (Seoul) |
| AL–FA | Two contrapuntal minds; *Double Fugue*; she annotates, he hammers |
| AL–SY | Never meet; his fork is a Remembrance; his initials on the portrait |
| AL–JW | Never meet; Jae-won calls *La Machine* "a drummer who ended up on piano" |
| AL–JU | The Walkman is the one future object Alkan begs to open; Julien lets him, once |
| CH–LI | Real friends and playful rivals: Onslow four hands, Bach for three keyboards; *Les Deux Virtuoses* |
| CH–FA | Fastidious and precise: she corrects his publishers' errors; the corridors front together |
| CH–SY | Never meet; *Warszawa* is the Remembrance she calls most |
| CH–JW | Never meet; Jae-won learns his name from the Remembrance banner and a mazurka on his phone |
| CH–JU | Chopin mimics Julien's swing so precisely that Julien laughs for the first time in 1833 |
| LI–FA | He leads the tour; she keeps its accounts and tells him what his generosity costs |
| LI–SY | Never meet; *La Clochette* Remembrance; the provenance "gift of the Abbé Liszt" |
| LI–JW | Never meet; Jae-won calls the Liszt Remembrance "the headliner" |
| LI–JU | The showman tells the thief that applause is the cheap part |
| FA–SY | Never meet; Seo-yeon reads the 1842 professorship end card (Seoul) |
| FA–JW | Never meet; *Grand Tirage* Remembrance |
| FA–JU | She calculates exactly what he stole and from whom, and sets the terms of his restitution: play only his own tune at her house |
| SY–JW | The vigil's two organisers; *Samulnori*; sibling-like bickering; in Paris, his text in the coda |
| SY–JU | Never meet; in Seoul she sight-reads his 1851 waltz "pour M." from the archive box |
| JW–JU | Never meet; hearing *Changes*, Jae-won asks who the drummer is, and is told there isn't one |

---

## 16. Ties Beyond the Party

| PC | Anachronists | Historical and fictional NPCs |
|---|---|---|
| PC-01 | Archon's living string; Vane's private English; Brücke's quarry (freed by a promise in Seoul); Julien spared; Delorme's accuser and accused | Mère Gaudin, Petit-Louis, Mathurin; Cherubini; Prof. Yoon; Pleyel; Gisquet; Heine ("the Nightingale of Nowhere") |
| PC-02 | Vane's agent and his refusal; Delorme's target (Erasure); Marthe's patient's sister and her rescuer | Sand; Théo; Corbel; Mme Daubrée; M. Bourdin; Ingres (hostile); Delaroche (swing vote); Chassériau; Corot |
| PC-03 | Archon insists on him for the gala podium (R-29), and gets a conductor who carries the orchestra through the pianists' mid-concerto modulation that spoils the recording | Harriet Smithson; Marie Moke-Pleyel; Habeneck; Paganini; Girard |
| PC-04 | Delorme's rival in paint | Thiers; Ingres; Delaroche; Horace Vernet |
| PC-05 | Brücke's metal, read at a glance | His family; Cherubini's Conservatoire |
| PC-06 | His Pleyel, Julien's "break" and Brücke's "lethal" (rung 8) | Franchomme; Hiller; Kalkbrenner; Pleyel; Offenbach |
| PC-07 | Thalberg's sponsor, Vane | Marie d'Agoult; Anna Liszt; Czerny; Belgiojoso; Thalberg; Clara Wieck |
| PC-08 | Delorme's formulas | Aristide and Victorine Farrenc; Pleyel; Sand (the Code) |
| PC-09 / PC-10 | Brücke in 2026 | The Kang parents; Prof. Yoon; Det. Oh |
| PC-11 | Former brothers: Delorme found him, Vane lent the tapes, Brücke betrayed him | Mère Gaudin's tavern crowd |

---

## Canon Additions & Cross-Doc Notes

**CCR** (logged here instead of CANON §2b; nothing in this doc depends on it being adopted):

- **CCR: a post-credits Historical Afterword screen.** *What:* after the ending roll and end cards of either branch, an optional plain-text **Afterword** screen (also reopenable from the title menu once seen) with one paragraph per historical party member, PC-03–PC-08, using the afterword texts of §5–§10. Each paragraph runs to at most 6 boxes in the 4 × 30 no-portrait format, is headed by the name and birth year only, and tells works and legacy within the Lantern Rule (LAW-18): no death is ever stated or depicted. *Why:* the brief asks for a historically careful game, and players who have lived beside these six people will want to know what became of their work; Tone Rule 6 allows narration only on the ending roll and end cards, so a new screen needs a canon exception. *Touches:* CANON §1 (Tone Rule 6), epilogues.md (placement after the cards), art_and_ui (screen layout), audio_and_music (a quiet arrangement of LM-01 under it), historical_notes_and_liberties (each paragraph verified). *Fallback until adopted:* the six paragraphs are writer reference only, and their substance may feed the existing end cards within the 2-line limit.

**New shared facts** (elaboration inside this doc's slice, CANON §0b; other docs cite, never redefine):

- **Defining scenes** (binding titles and beats for the scenario docs): Min-jun "Eight Bars" (CH-13); Lucile "The Night of Stars" (CH-14); Berlioz "The Wedding Menu" (CH-09); Delacroix "Eight Emblems" (CH-09); Alkan "The Wolf Fifth" (CH-15, the crypt door: he hands out the KEY-32 forks without a speech); Chopin "Żal" (CH-09); Liszt "The Unplayed Encore" (CH-10: at his La Châtre benefit a Nohant stable-boy brings word of the wolves, and he leaves his encore unplayed and rides into the Vallée Noire in concert dress); Farrenc "By One Candle" (CH-10, Sat 19 Oct); Seo-yeon "Nine Months" (CH-E1) and "The Bow Lifts" (CH-E2 coda); Jae-won "Four In, Four Out" (CH-E1, the clock tower); Julien "The Bundle" (CH-09). *Affects:* prologue_and_act1, act2, act3, act4_and_epilogue, epilogues.
- **Bond-quest part titles, rank events and Evening-scene titles** for BQ-PC02, BQ-PC02b, BQ-PC03, BQ-PC04, BQ-PC05, BQ-PC06, BQ-PC07, BQ-PC08 and BQ-PC11 (§4.13, §5–§10, §13), each with its beat. Specific placements: BQ-PC03 Part 1 "Pages from Rome" carries TUT-16 *Marche au supplice*; a **story step, "The Bride's Gift"**, fires at the CH-09 wedding supper in every run and gives TUT-17 *Songe d'une nuit du sabbat* (Harriet returns the *Sabbat* pages); the BQ-PC03 finale carries TUT-19 (all three as skills_and_progression §5.2 places them). BQ-PC04 Part 3 reworks the *Scio* studies (the *Chios* recipe). BQ-PC08's finale is Delorme's raid on Pleyel's archive and yields OPS-30 *Barricades*. BQ-PC02 Part 4 redeems Gilles Aubray's burnishing agate from the Mont-de-Piété and gilds the frame for *Women of Algiers*. Lucile's Evening scene 5, "Théo Counts", needs CH-07 or later (Théo is introduced in CH-07). *Affects:* side_and_bond_quests (owns full content, maps and rewards), secrecy_and_trust (Evening-scene names), items_and_equipment (quest props as ITM entries: the Rome notebooks, the burnishing agate, the Saint-Étienne railway print, the Couperin box).
- **Rank rows without scenes:** Delacroix's and Chopin's R7–R9 and Lucile's and Julien's R8–R9 have no events of their own; the rows state what each threshold unlocks (Cadenza, Hint, Trio eligibility, SYN-15 and SYN-20 openings, Julien's R10 *Second Chorus* and Lost Era cane). *Affects:* secrecy_and_trust, side_and_bond_quests.
- **Min-jun's 2026 life:** the Kangs moved from Incheon to Mapo-gu in 2012, when Kang Do-hyun took over the Euljiro shop; the fallboard tap began at his first recital, aged six, on his mother's advice ("so the piano knows you're coming"); REP-30 was his autumn 2025 jury piece, and Prof. Yoon's note on it read "Beautiful. Where does it go?"; a laptop folder of first pages; army-band arranging as the root of his orchestral talk with Berlioz; his musical voice (parallel ninths, 12/8 lilts caught from Jae-won's samulnori rehearsals, pieces built from the left hand up). *Affects:* prologue_and_act1, epilogues, audio_and_music (LM-02 notes), dialogue_style_guide.
- **Lucile's background figures:** Mme Daubrée's atelier, 1826–1828; her refused Salon of 1833 entry is a portrait of Théo whittling by the skylight; she taught Sand to float copal varnish; Sand's pet name comes from her moving her stool to follow the window light; attic rent 150 F a year; Corbel pays 10 sous a fan leaf and 1 F a snuffbox lid, about forty fans a week (≈ 20 F); Vane's velvet threat, "It would be a pity if Maison Grimaud grew impatient, my dear." All within CANON §14's anchors and R-55. *Affects:* act2 (the CH-03 and CH-07 POV scenes), salons_duels_and_economy (flavour only), overworld_and_towns (LOC-P20 dressing).
- **Farrenc before CH-08:** she is never on screen, but the Period Scores sold at Maison Farrenc in CH-05–CH-07 carry her pencilled fingerings, and Lucien (TF-030) says only that Monsieur Farrenc is at the printer's. This follows historical_cast's fix keeping both Farrencs off the counter before CH-08. *Affects:* overworld_and_towns, items_and_equipment (Score description text), act2.
- **Ending-fate details:** Chopin is the hand that corrected the bass of Delacroix's 1841 *Sarabande* (world_rules_and_lore §13.02 leaves it unnamed); in the Paris branch Alkan drops the last nitinol spring into Pleyel's furnace during SQ-23; Liszt turns pages at BOSS-35 while Belgiojoso renews her vow; Berlioz reads KEY-37 aloud at the Atelier. *Proposed* (epilogues owns them): the ending-roll vignettes in each section; Seo-yeon joins the Seoul party on the night of the return, Tue 22 Dec 2026, plays the opening of the *Harmonies* finale at the premiere's rehearsal, and organised the posters and vigil with Jae-won; Jae-won's single line in the Paris coda is a text message. *Affects:* epilogues, side_and_bond_quests (SQ-23), act4_and_epilogue.
- **Julien's Walkman** (reading of R-15): what BOSS-11 wrecked is Brücke's borrowed dynamo; the Walkman itself survives, silent. In BQ-PC11 Part 4 he swears never to transcribe from it again, and he plays it once more only to say goodbye before it is buried (SQ-23, CH-E2). *Affects:* side_and_bond_quests, epilogues, items_and_equipment (KEY-15 text).
- **Guest moments** (§14): Mathurin refuses the foreigner's only coin; Sand's wolf-leader hint over a broken automaton; Corot's "You paint as I dream" over the Berry studies; Mendelssohn's unasked question; Thalberg's matched bow after BOSS-35; Théo's "Thirty-one. I counted. I'm fine." *Affects:* prologue_and_act1, act3, act4_and_epilogue, epilogues.
- **Relationship-matrix beats** (§15) are seed material for Ensemble Scenes, Field Talk and CH-14 Kindred dialogue: Lucile's white-rose fan for Harriet (CH-12+), Alkan weighing a cake of Prussian blue and lasting four minutes as a sitter, Liszt carrying Lucile's easel, Chopin mimicking Julien's swing, Farrenc's restitution terms for Julien, Delacroix's sketch of Julien at a borrowed piano, Alkan opening the Walkman once, and Jae-won's four-timpani exam. *Affects:* side_and_bond_quests, act4_and_epilogue, epilogues.
- **Art proposals:** Lucile's cheek fleck tracking her manner (Prussian blue, Berry ochre, chrome yellow, a warm and a cool fleck together); Min-jun's battle idle (two baton taps on his palm) and *Arirang* field hum; Delacroix's speck-flick idle; Chopin's glove-tug idle. *Affects:* art_and_ui.

**Cross-doc notes** (each names the doc that must act):

- **skills_and_progression:** every skill, Étude, Study, Tutti, Score and rank-10 upgrade named here is its v1.0 name and effect; this doc no longer proposes any skill. It relies on its §4.3 (OPS-25 from BOSS-17 with Own Voice ≥ 6; OPS-30 from the BQ-PC08 finale), §5.2 (TUT-16, TUT-17, TUT-19 placements, now matched by the BQ-PC03 table) and §17.2.
- **combat_ensemble:** REP-27, REP-29 and REP-30 give only +3 Crescendo per movement until its effect CCR is adopted; §3.8 says so.
- **secrecy_and_trust:** Evening-scene counts (LU 6, BE 8, DE 6, AL 8, CH 6, LI 8, FA 8, JU 4), BQ-PC02's part gates and the mandatory quests' BP are used unchanged; please add the CH-07 gate to Lucile's Evening scene 5.
- **world_rules_and_lore:** this doc follows its CCR on Julien's ring (CANON §8 wording: he took a ring and never wore it) and its §13.12 white-soles report. It names Chopin as the corrector of Var. II, which fills a gap and changes no wording there.
- **historical_cast:** consistent with its Sand, Théo and Farrenc entries and its fixes (no Farrenc at the counter before CH-08; Lucile's redingote disguise; Anna Liszt's mended glove; Théo's "Monsieur Corée"). New here and for it to mirror: the Nohant stable-boy as Liszt's CH-10 messenger (Petit-Louis stays in Paris).
- **dialogue_style_guide:** the excerpt in §4.8 uses its §2.2 line format and §2.4 stage directions; the portrait extras marked "proposed" here (Delacroix `appraising`, Farrenc `sceptical`, Seo-yeon `scowl`, Jae-won `pumped`, Julien `sheepish`, Marthe `serene`, Théo `brave`) depend on its pending CCR and fall back as it specifies.
- **art_and_ui:** costume sets follow its §4.2 and its pending CCR (Min-jun Seoul and Winter; Lucile Interlude and Winter; Berlioz's wedding coat). Liszt's 3-frame idle and Chopin's ≤ 4 `cough` uses match its §5.2–§5.3.
- **epilogues / act4_and_epilogue:** the Keeper's Choice default (a) and every branch fate here follow LAW-24–LAW-26; the vignettes are proposals for the ending roll.
- **historical_notes_and_liberties**, please verify: Berlioz's Prix de Rome at the fourth attempt (1827–1830); Alkan's premiers prix (piano 1824, harmony 1827); Chopin's E-minor Concerto, Op. 11, published 1833 and dedicated to Kalkbrenner; Liszt's single 1833 piece *Harmonies poétiques et religieuses*; Delacroix's few days in Algiers (June 1832); Berlioz finishing his *Mémoires* in 1865 (published 1870); Farrenc's Prix Chartier (1861, 1869) and *Le Trésor des pianistes* in 23 volumes (1861–1872); Alkan's *Petits Concerts* at the Salle Érard (1873–1880); the Chaillot steam pumps still working in 1833; the flower market on the Quai aux Fleurs in 1833. The variation correction, the friendships and all bond-quest events are R-00 inventions.
