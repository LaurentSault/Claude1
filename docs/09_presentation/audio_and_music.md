# Audio & Music

Status: v1.0 — 2026-10-06 · Owns: the soundtrack list (MUS-###), leitmotif detail (elaboration of the LM-01–LM-32 table), the SPC700 audio spec (voice plan, ARAM map, BRR palette, echo, driver), the SFX list, adaptive music rules, repertoire arrangements and the 2026 repertoire clearance table · Depends on: none (canon only) · Canon: docs/00_CANON.md

> Binding inputs: CANON §15a (SPC700 constraint), §15b (track naming and the fixed MUS IDs), §15c (leitmotifs), §15d–§15e (repertoire and clearance rule), §16a (the `[SFX:]` and `[MUS:]` tags). Where this file and the canon disagree, the canon wins. Scenario docs cite this file's MUS and SFX IDs in their cue notes (CANON §0b).

## Contents

1. [The Rules of the Score](#1-the-rules-of-the-score)
2. [SPC700 Audio Spec](#2-spc700-audio-spec)
3. [Leitmotifs](#3-leitmotifs)
4. [Original Soundtrack Tracklist](#4-original-soundtrack-tracklist)
5. [Adaptive Music Rules](#5-adaptive-music-rules)
6. [The Repertoire](#6-the-repertoire)
7. [Repertoire Clearance (2026)](#7-repertoire-clearance-2026)
8. [SFX List](#8-sfx-list)
9. [Cue Tags for Writers](#9-cue-tags-for-writers)
10. [Canon Additions & Cross-Doc Notes](#canon-additions--cross-doc-notes)

---

## 1. The Rules of the Score

The game is about a musician, so the score is a second script. Eight rules bind every composer, arranger and sound designer.

| # | Rule | Source |
|---|---|---|
| A1 | **The C♯ never resolves early.** Every statement of LM-01 stops on C♯ until LM-30 (CH-14 roof), LM-26 (CH-E1) and LM-27 (CH-E2) give it Lucile's D. Jingles and the title loop hang on C♯; audio QA runs a "C♯ check" on every cue that quotes LM-01 | CANON §15c |
| A2 | **One modern timbre.** The square/saw patch (SMP-16) sounds only from the Engine, Archon's final forms, the CH-E1 static automata and the Engine's ruined keyboard in the Fleeting Window. CHRONO spells and Brücke's clockwork use period samples | CANON §15a, LAW-09 |
| A3 | **Five music voices, three SFX voices**, with only the canon's named exceptions (§2.2). A cue that needs a sixth voice is rewritten | CANON §15a, R-38 |
| A4 | **Min-jun is never an "exotic" cue.** LM-02 and LM-32 are pentatonic, played and hummed with dignity; no gong, parallel-fourth cliché or "Oriental" stinger ever cues his entrances, name or heritage. His colour is the gayageum-like pluck and a bent note; the samulnori instruments belong to Jae-won's BEAT and the Seoul Synergies, played as the craft they are | CANON §16c |
| A5 | **Evoke, never quote, twentieth-century popular music.** Julien's jazz and the Seoul lo-fi are original melodies in a style (§7.3) | CANON §15d, R-15 |
| A6 | **Melancholy with a pulse.** Every grief cue keeps one living line (MUS-009's harp ostinato, MUS-103's heartbeat) | Tone Rule 1 |
| A7 | **The quiet before the set piece.** Every area track has a quiet rendering on V0–V2 for the scene before a chapter's big battle; MUS-022 and MUS-031 are written quiet | Tone Rule 2 |
| A8 | **Silence is a cue.** `[MUS:silence]` is scored at named beats: Archon's first line of the Revelation, "Play for me.", the Question, the phone leaving his hand, the bow lifting | — |

---

## 2. SPC700 Audio Spec

### 2.1 The hardware discipline

The SPC700 gives **8 voices**, **64 KB of audio RAM (ARAM)**, 32 kHz stereo, BRR samples (**16 samples per 9-byte block**), ADSR/GAIN envelopes, an 8-tap FIR echo, one noise generator on a **single global clock**, and pitch modulation by the previous voice (PMON). There is no cartridge ROM budget (CANON §1): banks load from disk per song, so **ARAM is the only budget**, and everything here would play on a real SNES.

### 2.2 Voice plan (house rule and every exception)

House rule: **V0–V4 music, V5–V7 SFX**; V5 UI and footsteps, V6 battle hits and spells, V7 ambience and stings (CANON §15a).

| Context | V0 | V1 | V2 | V3 | V4 | V5 | V6 | V7 |
|---|---|---|---|---|---|---|---|---|
| Field, town, dungeon | Melody | Counter-melody | Harmony / drone | Bass | Percussion, colour, or the Hour layer (§5.1) | UI, footsteps | Event SFX (doors, chests) | Ambience loop (rain, river), stings |
| Battle | Lead | Counter | Harmony | Bass | Percussion | UI, ATB ding, Recital chimes | Hits, spells | Second spell layer, enemy cries, Onlooker gasps |
| Battle Recital (§5.5) | Piano right hand | Piano left hand | Strings | Harp | Bass / colour | as battle | as battle | as battle |
| Salon *Phrase* | The piece (V0–V4) | | | | | Prompt ticks | Hit grades, dynamics | Room tone, murmur, applause |
| Piano Duel | Duellist A (pan left) | Duellist B (pan right) | Strings | Harp | Percussion | UI | Passage results | Crowd |
| **BOSS-17 Stage, BOSS-27** | Music V0–V6 | | | | | | | **All SFX** (4-deep queue, §2.3) |
| **Grand Mode** (MUS-070, MUS-095 cutscenes, MUS-150, MUS-160, MUS-170) | Music V0–V7 | | | | | | | SFX muted; text advances silently |
| Playable Fleeting Window (MUS-095, 7 voices) | Music V0–V6 | | | | | | | UI SFX only; footsteps muted |
| Ordinary cutscene | Music V0–V4 | | | | | Off | Event SFX | Ambience |

### 2.3 SFX priority and voice stealing

| Class | Priority | Examples | Home voice |
|---|---|---|---|
| Story sting | 7 (never stolen) | `piano_hit` in script, `rifle_shot`, `fallboard_tap` in the prologue and portrait | V7 (V6 if V7 is held by a P7) |
| Boss telegraph | 6 | `rifle_cock` ("Steady…"), `boiler_hiss`, `train_approach`, `dial_tick` | V7 |
| Heavy impact | 5 | `piano_hit` on crits, `piano_hit_boss`, KO | V6 |
| Spell, Synergy | 4 | element sets, `synergy_banner` | V6 (layer on V7) |
| Weapon hit | 3 | weapon-class sets | V6 |
| UI decision | 2 | `cursor_confirm`, `cursor_cancel`, `atb_ready` | V5 |
| UI motion | 1 | `cursor_move`, footsteps | V5 |
| Ambience | 0 | `rain_loop`, `river_lap`, `crowd_murmur` | V7 |

**Stealing.** A request takes its home voice if the current sound there has equal or lower priority; otherwise it tries V7 if V7 holds priority ≤ 1; otherwise a P1 sound is dropped and a P3 sound waits up to 3 frames, then drops. A stolen ambience loop pauses and returns with a 16-frame fade. A story sting ducks the music by 6 dB for 30 frames. **On V7-only contexts** (BOSS-17, BOSS-27) the queue order is P7 > P6 > P5 > **`atb_ready`** > P4 > P3 > P1: the ATB ding is promoted so no player ever misses a turn by ear (it also flashes under Config → Audio Cue Visuals).

### 2.4 ARAM map (64 KB, binding)

| Range | Size | Contents |
|---|---|---|
| $0000–$00EF | 240 B | Driver zero page |
| $00F0–$00FF | 16 B | SPC I/O registers |
| $0100–$0173 | 116 B | Stack |
| $0174–$01FF | 140 B | Sample directory: 35 entries × 4 B (15 music: 14 instruments with the piano's two zones; 20 SFX) |
| $0200–$17FF | 5,632 B (5.5 KB) | Sound driver code, SFX sequences, instrument maps |
| $1800–$2FFF | 6,144 B (6 KB) | Sequence data of the loaded song, including the 1.5 KB **Recital slot** in battle banks (§5.5) |
| $3000–$9FFF | 28,672 B (28 KB) | Music BRR samples of the loaded bank (≤ 14 instruments) |
| $A000–$BFFF | 8,192 B (8 KB) | SFX BRR samples (global, resident) |
| $C000–$FFFF | 16,384 B (16 KB) | Echo buffer; the IPL ROM overlay at $FFC0 is switched off at boot so the buffer owns the top 64 bytes |

The 0.5 KB reserve of CANON §15a is $0000–$01FF. The echo region is fixed at 16 KB so EDL can change between songs without moving samples; when a song runs EDL ≤ 7, the unused tail stays zero-filled.

### 2.5 Echo presets

EDL steps are 16 ms and 2 KB each (EDL 4 = 64 ms, 8 KB; EDL 8 = 128 ms, 16 KB). FIR values are signed 8-bit starting points, tuned by ear on hardware. **EDL changes only on a song load**: battle songs load at EDL 4, and Light States in battle switch FIR and feedback (EFB) only, because changing EDL mid-song requires clearing the buffer.

| Preset | FIR taps C0–C7 | EDL | EFB | Where |
|---|---|---|---|---|
| Clear | 127, 0, 0, 0, 0, 0, 0, 0 | 2 | +24 | Streets, markets, Noon battles |
| Velvet | 12, 33, 43, 43, 19, −2, −13, −7 | 8 | +48 | Salons, churches (CANON §15a), Candle and Dusk battles |
| Stone | 64, 48, 16, 0, 0, 0, 0, 0 | 6 | +56 | Quarries, crypt, sewers, Night and Gloom battles; the Heart Chamber at EDL 8, EFB +72 |
| Wet | 32, 32, 32, 16, 8, 8, 0, 0 | 5 | +40 | Rain, fog, river, Fog battles |
| Bright | 96, −16, 32, 0, 16, 0, 0, 0 | 4 | +32 | Dawn, Virtuosic salons, Seoul lo-fi at EDL 3 |
| Phone | −16, 0, 72, 0, 72, 0, −16, 16 | 1 | +8 | The Walkman (KEY-15), the phone video in the CH-E2 coda |

### 2.6 BRR sample palette (CANON's 17 instruments, 18 samples)

Abbreviations used in §4: **Pno** grand piano, **Pnn** pianino, **Str** strings, **Hn** horn, **Fl** flute, **Ob** oboe, **Hp** harp, **Tmp** timpani, **Sn** snare, **Org** organ, **Acc** barrel organ/accordion, **Ch** choir "aah", **Bs** upright-bass pizzicato, **MBx** music box, **HG** hurdy-gurdy, **Gy** gayageum-like pluck, **Syn** the reserved synth, **Nz** the noise generator (no sample).

| SMP | Instrument | Root / range | Rate | Blocks / bytes | Loop and envelope | Notes |
|---|---|---|---|---|---|---|
| 00a | Grand piano, low zone | A2; plays A0–E4 | 16 kHz | 704 / 6,336 | Last 64 blocks loop as the sustain tail; ADSR decay to 40% over 0.6 s | Sampled from a restored period Pleyel grand: warm, quick decay, the 1833 sound. Min-jun's note in the Octave |
| 00b | Grand piano, high zone | A5; plays F4–C8 | 22 kHz | 640 / 5,760 | As 00a | Zones meet at E4/F4 with a 2-semitone overlap crossfaded in the map. **Together ≈ 11.8 KB** (CANON: ≈ 12 KB) |
| 01 | Pianino | C4 | 16 kHz | 256 / 2,304 | Loop; fast release | Two strings 9 cents apart baked in, so it beats: *Au Diapason Fêlé* |
| 02 | Strings ensemble | A4 | 16 kHz | 200 / 1,800 | Loop; vibrato from the driver | Pizzicato via GAIN fast release; a **solo-violin map** (narrow vibrato, root an octave up) serves Seo-yeon |
| 03 | Horn | F3 | 16 kHz | 120 / 1,080 | Loop | The score's only brass: fanfares, Berlioz's note |
| 04 | Flute | A5 | 16 kHz | 64 / 576 | Loop; breath baked into the attack | Farrenc's note (Aristide was a flautist) and half of Lucile's shimmer |
| 05 | Oboe | A4 | 16 kHz | 72 / 648 | Loop | Chopin's note; low-passed, it becomes Julien's "sax line" without imitating any player |
| 06 | Harp | C5 | 22 kHz | 160 / 1,440 | No loop (pluck) | Lucile's instrument and her octave D |
| 07 | Timpani | D2 | 11 kHz | 180 / 1,620 | No loop | Layered with SMP-08 pitched up = Archon's anvil |
| 08 | Snare | — | 16 kHz | 110 / 990 | No loop | Played high with instant key-off = the cabal's rim tick |
| 09 | Organ | C3 | 16 kHz | 48 / 432 | Single-period loop | Alkan's pedal piano and Archon's pedal; two detuned voices with PMON = LM-17's beating hum |
| 10 | Barrel organ / accordion | C4 | 16 kHz | 96 / 864 | Loop with baked 6 Hz tremolo | The streets of Paris |
| 11 | Choir "aah" | A3 | 16 kHz | 180 / 1,620 | Loop | Liszt's note; with the Velvet FIR and a low root it is the **hum** of LM-32 |
| 12 | Upright-bass pizzicato | E2 | 11 kHz | 128 / 1,152 | No loop | Julien's walking bass; the general bass in most banks |
| 13 | Music box | C6 | 22 kHz | 96 / 864 | No loop | Brücke and his automata only |
| 14 | Hurdy-gurdy | G3 | 16 kHz | 112 / 1,008 | Loop with the buzzing *trompette* | Nohant and the Berry |
| 15 | Gayageum-like pluck | D4 | 22 kHz | 144 / 1,296 | No loop; the driver's bend command adds the *nonghyeon* lift (up to +60 cents) | 2026 Seoul and Min-jun's memory |
| 16 | Synth (reserved) | 32-sample saw-square cycle | — | 2 / 18 | Loops entire | Rule A2. PMON and noise give the Engine its warp and the automata their static |
| | **Palette total** | | | **3,312 / 29,808** | | More than one bank's 28,672 B: no song can load all seventeen |

**Bank rule.** A song loads ≤ 14 instruments within 28,672 B. The heaviest legal-count bank (piano plus the 13 next-largest instruments) would weigh 28,782 B, 110 B over, and the bank builder refuses it; no track needs it. The heaviest shipped bank is the shared Chrono-Labyrinth bank (MUS-037–039: Pno, Acc, Gy, Str, Ob, Hp, Org, Bs, Sn, Ch, Tmp = 23,958 B). **Every battle bank includes the Recital set: Pno, Str, Hp, Fl and Ob** (16,560 B; 20,412 B with MUS-100's Hn, Tmp and Bs), so a Recital or an Invocation starts without a load (§5.5).

### 2.7 The *Diapason* driver

The driver (≤ 5.5 KB, 48 ticks per quarter) offers volume and pan ramps, vibrato, tremolo, portamento, the **bend** (*nonghyeon*), a global **wow LFO** (0.8 Hz, ±15 cents, with a scripted 40-cent sag: Vane, the Walkman, the phone video), per-voice echo, noise, PMON and 4-deep loops. Game-facing features (binding for engineering):

| Feature | What it does | Used by |
|---|---|---|
| **Rendering** | Swaps the song's instrument map (16 slots of sample, envelope, tuning; ≤ 64 B each; ≤ 4 per song). Same notes, new colour, zero sequence bytes; a tempo offset of up to ±10% is allowed. A rendering chosen at song load may bring its own bank (MUS-101's Seoul rendering) | Night, rain, winter and town variants; the tavern pianino; Light States |
| **Layer mask** | Mute bits per sequence track, set by the game and ramped over 1 bar. A song may carry up to 3 alternate tracks for V4 and 2 for V1/V2, only one sounding per voice | Secrecy tiers, Echo and automata layers, Rapture, farewell and Ledger layers, the repaired dead keys, destroyed Engine parts |
| **Twin balance** | An equal-power 16-step table that sets complementary volumes on a voice pair from one game value (0–15) | The Chrono-Labyrinth crossfade (§5.4) |
| **Bar clock** | A bar counter the game can read and write | Party switching in CH-15; resuming field music after battle |
| **Bookmark** | Saves the sequence position; resume restarts at the saved bar's downbeat | Field → battle → field; battle → Recital → battle |
| **Sync marker** | Sends a byte to the game at a scored beat | Cutscenes, the Window Clock, ending-roll vignettes |
| **Slot upload** | Accepts a ≤ 1.5 KB sub-sequence into the Recital slot while music plays (serviced in idle time; under 4 frames) | Recital cues, Cadenza stingers |

**Noise clock house rule.** The noise clock is global, so the whole score shares one value, **NCK $1D (≈ 10.7 kHz)**, for hats, rain, swishes and brushes. Thunder retunes to $14 (≈ 1.3 kHz) for 40 frames and the static automata use $1F (32 kHz); while a retune holds, music noise voices are masked. In the Chrono-Labyrinth the zone's dominant era owns the clock (§5.4).

**Sequence budget.** ≤ 6 KB per loaded song: field songs average 3.5 KB; battle songs ≤ 4.5 KB plus the 1.5 KB Recital slot; Grand Mode cues, which are through-composed, may use the full 6 KB.

---

## 3. Leitmotifs

The canon fixes each motif's name, meaning and character (CANON §15c). This section fixes the notes, rhythm, harmony and variants. Two tables come first because every other section leans on them.

### 3.1 The Octave orchestration of LM-01

Each of LM-01's eight notes belongs to one Octave voice (CANON §15c) and, in this score, to one instrument. When the theme is played in full orchestration, each friend's note sounds on that friend's instrument; BOSS-27's Voices (combat_ensemble §6.7) sound the same notes on the same instruments.

| Note | Pitch | Voice | Instrument (SMP) | Why |
|---|---|---|---|---|
| 1 | D | Min-jun | Grand piano (00a/b) | The pianist from tomorrow |
| 2 | E | Berlioz | Horn (03) | The orchestra's brass, his Tuttis |
| 3 | F♯ | Delacroix | Strings (02) | LM-12's fanfare softens into strings |
| 4 | G | Alkan | Organ (09) | His pedal piano |
| 5 | A | Chopin | Oboe (05) | The sighing appoggiatura of LM-13 |
| 6 | B | Liszt | Choir (11) | The chorale beneath the showman |
| 7 | C♯ | Farrenc | Flute (04) | Aristide's instrument; the voice the record forgot holds the leading tone |
| 8 | D (octave) | Lucile | Harp (06) | LM-03's harp; the note that completes him |

### 3.2 Main track per leitmotif

`[MUS:LM-xx]` in a script plays the motif's main track (dialogue_style_guide §1.2).

| LM | Main track | LM | Main track | LM | Main track | LM | Main track |
|---|---|---|---|---|---|---|---|
| 01 | MUS-003 | 09 | MUS-021 | 17 | MUS-004 | 25 | MUS-130 |
| 02 | MUS-008 | 10 | MUS-024 | 18 | MUS-009 | 26 | MUS-151 |
| 03 | MUS-017 | 11 | MUS-011 | 19 | MUS-012 | 27 | MUS-171 |
| 04 | MUS-006 | 12 | MUS-010 | 20 | MUS-100 | 28 | MUS-016 |
| 05 | MUS-013 | 13 | MUS-019 | 21 | MUS-101 | 29 | MUS-029 |
| 06 | MUS-033 | 14 | MUS-023 | 22 | MUS-020 | 30 | MUS-095 |
| 07 | MUS-014 | 15 | MUS-025 | 23 | MUS-030 | 31 | MUS-027 |
| 08 | MUS-026 | 16 | MUS-015 | 24 | MUS-002 | 32 | MUS-034 |

### 3.3 The thirty-two motifs

Each entry gives *Shape* (intervals and rhythm), *Harmony* and *Variants* by context.

**LM-01 Harmonies of the Lost Era.** *Shape:* D E F♯ G A B C♯ as seven even crotchets in 4/4, the C♯ tied across a bar under a fermata: one breath. *Harmony:* I – ii7 – iii – IV – V – vi, then the C♯ bare over an A pedal. *Variants:* the Hidden Study (the upright alone over an organ drone on A: the puzzle's first page); the title (full Octave orchestration); the Panthéon (organ); jingles (a quick arpeggio, still on C♯); BOSS-27 (stacked as a chord); resolved only in LM-26, LM-27 and LM-30, the D arriving on harp and then doubled by piano.

**LM-02 From Tomorrow.** *Shape:* G-major pentatonic; from D a leap up a major sixth to B (the "homesick sixth"), then a fall A–G–E to a low D; long–short–short, the third beat held. *Harmony:* Gadd9, Cmaj7, Em7, Dsus2; never a dominant seventh. *Variants:* tavern (pianino, 2/4); field (piano, a grace note on the held note); 2026 (gayageum, the held note bent upward); Pno I of the Concerto; half of LM-22.

**LM-03 Impression.** *Shape:* harp ripples on the whole-tone scale on D (D E F♯ G♯ A♯ C) in rising 6/8 waves; the flute climbs toward the upper D and always stops on C. *Harmony:* alternating augmented triads, no dominant pull. *Variants:* IMPRESSION (harp, flute); POINTILLÉ (pizzicato dots); IMPASTO (low strings, quicker waves); LUMIÈRE (whole-tone scales on D and C♯ interlocked into a chromatic shimmer that finally lands on D: her own manner); MUS-022 (a minor frame).

**LM-04 Ville Lumière, Ville Malade.** *Shape:* A-minor waltz; E drops a minor sixth to G♯, then climbs A–A♯–B–C; the answer turns to C major (the City of Light) and sinks back (the sick city). Rain percussion is noise in uneven quavers, like gutter drips. *Variants:* Left Bank (accordion); Boulevards (strings and flute); Night (harp and oboe, ♩=120); Rain (Wet echo); absorbed into LM-27 in 1834.

**LM-05 The Stilled Hour.** *Shape:* the row **D–C♯–A–B♭–F♯–F–B–C–G♯–G–E–E♭**, six semitone pairs ticking like a clock; it opens with Min-jun's first and seventh notes reversed (the cabal starts where he stops), over a rim tick at one per real second. *Harmony:* none; hexachord clusters in string harmonics. *Variants:* Men in Grey (fast tremolo); the Watched layer (first four notes); BOSS-11 (swung); BOSS-27 (frozen; the tick stops at 00:43); BOSS-28 (synth). To 1833 ears: music from the wrong century.

**LM-06 Archon.** *Shape:* an organ pedal on C, outside the friends' D major; a whole-tone ascent C–D–E–F♯–G♯–A♯ in minims; anvils (timpani layered with high snare) on beat 1 and the off-beat of 3. *Harmony:* whole-tone clusters; nothing resolves because nothing needs to. *Variants:* Val-de-Grâce (against LM-31); BOSS-16 (one step per Archon turn); LM-25 (inverted); BOSS-28 (synth with PMON warp); the CH-E1 Testament (dry piano).

**LM-07 A Gentleman's Wager.** *Shape:* a galant G-major minuet, two-bar phrases ending on trills; the wow LFO bends every voice, with a 40-cent sag on beat 2 of every eighth bar: a cassette stretching. *Harmony:* I–IV–V–I with one ♭VI (E♭) in bar 6, a colour from 1988. *Variants:* Faubourg Saint-Germain (strings); Corbel's back room (piano); BOSS-20 (three against four); CH-14, when he reads her reports, the wow stops once.

**LM-08 Blue Notes in the Dark.** *Shape:* walking bass in crotchets; rootless piano voicings over a Dorian vamp, Dm9–G13; a low-passed oboe line bending its thirds; swung noise brushes. *Variants:* the sewers (over LM-17); BOSS-11 (fast, the row swung in); MUS-172 (a melody heard nowhere earlier: his own tune, BQ-PC11); the Walkman burial (Phone echo, wow).

**LM-09 Golden Section.** *Shape:* a thirteen-note palindrome played against its own retrograde (a crab canon), in Fibonacci phrase lengths; MUS-021's 34-bar loop is built 13 + 21 and peaks at bar 21 (34 × 0.618). *Harmony:* F minor, the ear's one foothold. *Variants:* Louvre (strings); E05 (high feedback, mirrors); BOSS-15 (fast); BOSS-25 (all in retrograde, echo by Light State); the CH-E2 Erasure.

**LM-10 Escapement.** *Shape:* 7/8 (2+2+3); the music box turns a seven-note figure that lands on a new beat each bar; pizzicato ticks beneath. *Harmony:* B minor with a Lydian E♯. *Variants:* the Horlogerie; the Vallée Noire (a hurdy-gurdy drone as the wolf-leader's pipe); BOSS-14 (steam timpani); CH-E1's static (synth corrupting the music box); the clock tower; BOSS-30.

**LM-11 Idée Fixe.** *Shape:* a quotation of the arching *idée fixe* of the *Symphonie fantastique* (1830, public domain), on flute and strings as in its first statement. *Variants:* comedy (low staccato oboe); the 3 Oct 1833 wedding (organ, bell voicing); the street (barrel organ); the "sabbath" form (pitch-bent oboe for the finale's shrill clarinet); the 22 Dec lobby (strings).

**LM-12 Liberty's Palette.** *Shape:* a B♭ horn fanfare in dotted rhythm, a fourth F–B♭ then a sixth up to G, its cadence taken softly by strings. *Harmony:* I–vi–IV–V with a swerve to ♭VI. *Variants:* the studio (strings); battle (full brass); the confession (muted horn); MUS-150 (one held horn note under LM-30); the CH-E2 sitting.

**LM-13 Żal.** *Shape:* an original mazurka (never a Chopin quotation) in 3/4, the accent moving between beats 2 and 3; its sigh is a long upper neighbour falling a semitone. *Harmony:* C♯ minor with the raised fourth (F double-sharp). *Variants:* his apartment (piano, oboe); the confession (piano, slower); *Warszawa* (polonaise rhythm, snare); Rubato (tempo flexing against the beat).

**LM-14 Transcendence.** *Shape:* a falling two-octave cascade in octaves, E major, settling into a four-part chorale on choir and organ: showman, then seeker. *Variants:* battle (runs only); Pno II of the Concerto; BOSS-36 (beside MUS-274); MEPHISTO (diminished runs); his farewell (the chorale alone).

**LM-15 Counterpoint of the Unremembered.** *Shape:* a G-minor two-voice invention; the oboe answers the flute's two-bar subject a bar late: the voice the record forgot. *Variants:* Maison Farrenc (flute and piano); from the BQ-PC08 finale and the Vow the answer enters on time; *Fugue* (three voices); *Cadence* (V–I).

**LM-16 Ostinato.** *Shape:* a grave quaver figure G–B♭–A–D in the organ's pedal that never stops, except for one-bar silences at bars 7, 12, 20 and 27. *Variants:* the Alkan house; Étude inputs (accelerating); *Recluse* (alone); *La Machine* (a machine rhythm, no railway reference, LAW-18).

**LM-17 Resonance.** *Shape:* two organ voices about 3 Hz apart, beating two to three times a second, the fifth and octave on choir. *Root:* the nearest Clef (world_rules_and_lore §4): I D, II E, III F♯, IV G, V A, VI B, the Heart C♯. *Variants:* P01 on D; P26 on E; each CH-15 zone on its Clefs; the Lorelei a quarter-tone flat of A, belonging to no Clef; the Dead Heart still and beatless.

**LM-18 Miasma.** *Shape:* a 3/2 lament over a chromatic bass D–C♯–C–B–B♭–A, the oboe rising against it, a harp ostinato keeping the pulse. *Variants:* memorials; Père-Lachaise; SQ-22 (piano); MUS-103; the Orpheus zones.

**LM-19 Candlelight Salon.** *Shape:* a gentle 2/4 galop in F, bouncing piano, flute in dotted figures. *Variants:* by Taste (§5.2); Pleyel's showroom by day; the "Bravo" tail.

**LM-20 The Ensemble.** *Shape:* 12/8, piano octaves over a galloping long–short bass, B minor. *Harmony:* i–♭VI–♭VII–i, a Neapolitan C before each loop. *Variants:* Echo and Gloom (LM-17 hum on V4); automata (music box on V4); Seoul (MUS-154).

**LM-21 Duel of Tempos.** *Shape:* bass in 3/4 against melody in 4/4 at one pulse, locking every 12 beats. E minor. *Variants:* duels (duellists panned left and right); the Wardens; the Jury; the Masterwork.

**LM-22 Two Hours of Light.** *Shape:* LM-02 on piano against LM-03 on harp and flute; for seven bars pentatonic and whole-tone rub; on bar 8 they meet on E, the ninth above D: together, not yet home. *Variants:* the dawn lessons; the CH-08 kiss (strings swell into the fade, CANON §16f); Window Talks (piano and harp); the Lorelei (his line alone); the CH-12 dome; the CH-E2 proposal (hurdy-gurdy drone); the Atelier.

**LM-23 Nohant Afternoons.** *Shape:* a 6/8 bourrée over a hurdy-gurdy drone on G and D, leaping fourths, the *trompette* buzzing on beats 1 and 4. *Variants:* Nohant; Fontainebleau (strings and harp, for Corot); Montmartre (accordion); the house defence (fast).

**LM-24 Jeong-dong Night.** *Shape:* swung semiquavers at ♩=84; a pentatonic gayageum figure over low-passed Fmaj7–Em7–Dm7–Cmaj7; noise crackle and brushes. *Variants:* CH-P (March, no snow); December 2026 (with LM-26); the Hanseong zones; the static; the coda.

**LM-25 Vers la Coda.** *Shape:* LM-06 inverted into a falling whole-tone bass (A♯–G♯–F♯–E–D–C) while LM-01 climbs above it, until the treble's C♯ grinds against the bass's C: the semitone the game argues over. *Variants:* BOSS-26; BOSS-27 (frozen); BOSS-28 (synth); the Heart Chamber field.

**LM-26 Snow on Jeong-dong.** *Shape:* LM-01 completed in D major, 6/8: the C♯ rises to D on harp at bar 3, and the melody continues into a phrase never heard before: the life after. *Variants:* the reunion (piano); the noraebang ballad (4/4); Bosingak (bell voicing); the Seoul credits.

**LM-27 Salon Night, 1834.** *Shape:* LM-01 completed as a waltz at ♩=144: notes 1–6 as crotchets, the C♯ a full bar 3, the D on bar 4's downbeat. *Variants:* winter Paris (accordion); Salon Night; BOSS-33; the Paris credits.

**LM-28 La Rue.** *Shape:* 2/4 snare with rimshots and fragments of the opening march phrase of Auber's *La Parisienne* (1830, public domain). *Variants:* the barricade (tocsin bell voicing); the Prefecture (slow piano); the Aachen border (horn); the Unmasking.

**LM-29 Rhine Journey.** *Shape:* a broad E♭ horn call, a fifth then the octave (E♭–B♭–E♭), dotted, strings answering. *Variants:* overworld; towns; the *Concordia* (paddle-wheel timpani in three); *La Lumière* (LM-03 above).

**LM-30 La Musique des étoiles.** *Shape:* LM-01's eight notes over LM-22 at ♩=69; the C♯ is harmonised by A major and the D lands on harp: the first perfect cadence LM-01 is ever given. *Variants:* the CH-14 roof (first hearing); the Window (with the Engine's last oscillators); MUS-150; Yanghwajin (piano and gayageum); both credits.

**LM-31 Hymn of the Ward.** *Shape:* a four-part hymn in E Phrygian, in minims, organ and choir. *Variants:* the dispensary; Val-de-Grâce (against LM-06); her defection (strings); CH-E2.

**LM-32 Eomma.** *Shape:* the opening of *Arirang* (traditional, public domain) in 3/4, hummed on the choir's hum rendering. *Variants:* the Kang apartment (with piano); Kang Piano Service (felt-hammer clicks); the Seoul amalgam zones (gayageum); Chopin's mazurka (MUS-231); Seo-yeon's *Arirang Variations*.

---

## 4. Original Soundtrack Tracklist

**89 tracks**: 42 story and area, 19 battle and boss, 20 epilogue, and 8 featured repertoire arrangements. Fixed canon IDs: MUS-001, MUS-070, MUS-095, MUS-100, MUS-101, MUS-130, MUS-150, MUS-160, MUS-170 (CANON §15a–b). Gaps in numbering are reserved. Loop lengths are computed from bars and tempo. "Rendering" = the same sequence through another instrument map (§2.7). Grand Mode cues are marked **GM**.

### 4.1 Story and area (MUS-001–099)

| MUS | Title | Usage | LM | Tempo | Key / mode | Mood | Instruments | Loop |
|---|---|---|---|---|---|---|---|---|
| 001 | Harmonies of the Lost Era | Title screen, attract loop | LM-01, LM-02 | ♩=88 | D major, ends on C♯ over A | Wistful, wide | Pno, Str, Hp, Fl, Hn | Intro 8 bars; loop bars 9–40 (1:27); the seam rides the C♯ |
| 002 | Jeong-dong Night | CH-P campus and annex; LOC-S01 in CH-E1 | LM-24, LM-02 | ♩=84, swung | C Ionian | Late, lonely, warm | Gy, Pno, Bs, Str, Nz | 4-bar intro; loop 24 bars (1:09) |
| 003 | The Door Beneath Jeong-dong | S02 Hidden Study (CH-P, CH-E1, coda); S05; P28 (organ rendering); the crypt-door prompt | LM-01, LM-17 | ♩=60 | D major, pedal A | Dust, awe | Pno (upright map), Org, Ch, Hp | Loop 16 bars (1:04); the beating hum never breaks at the seam |
| 004 | Resonance | P01, P38, quarries, Clef plinths; S09 Namsan (wind rendering); E03 still rendering | LM-17 | ♩=50 | Drone on the Clef's pitch | Bones, lime, a humming city | Org ×2 (PMON), Ch, Tmp, Nz | Loop 20 bars (1:36) |
| 005 | Men in Grey | CH-01 chases, Watchers, Close Call, P31 Bercy, Unmasking escape | LM-05, LM-06 | ♩=144 | Row over a C pedal | Hunted | Str (tremolo), Sn, Tmp, Org, Pno | Intro 2; loop 16 bars (0:27) |
| 006 | Ville Lumière, Ville Malade | W01; P02, P03, P10, P16, P32; renderings Left Bank, Boulevards, Night, Rain | LM-04 | ♩=132 (3/4) | A minor / C major | Fog, bells, beauty with grief beneath | Acc, Str, Hp, Bs, Nz | Intro 4; loop 48 bars (1:05) |
| 007 | Au Diapason Fêlé | P04, first home; inn rest tag | LM-02, LM-19 | ♩=104 (2/4) | G major | Smoky, kind | Pnn, Acc, Str, Bs, Sn | Loop 32 bars (0:37). The pianino's dead keys E♭4, A♭4 and C5 are rests in the melody; a dormant CH-E2 layer (Théo's repair) fills them |
| 008 | From Tomorrow | Min-jun's theme; homesick nights | LM-02 | ♩=72 | G major pentatonic | Wry, gentle | Pno, Str, Hp, Gy, Bs | Loop 24 bars (1:20) |
| 009 | Empty Chairs | Memorials, poor quarters, P33, SQ-22's still | LM-18 | ♩=56 (3/2) | D minor | Grief with dignity | Str, Ob, Org, Hp | Loop 16 bars (1:43) |
| 010 | Liberty's Palette | Delacroix; P06; the CH-E2 sitting (a dormant LM-30 harp layer) | LM-12 | ♩=92 | B♭ major | Ardent, dandyish | Hn, Str, Tmp, Pno, Ob | Fanfare intro 2; loop 32 bars (1:23) |
| 011 | Idée Fixe | Berlioz; P23 wedding rendering; P35 lobby | LM-11 | ♩=120 | C major | Volcanic, funny | Fl, Str, Hn, Tmp, Bs | Loop 40 bars (1:20) |
| 012 | Candlelight Salon | P05, P09, P12 (day), P39 | LM-19 | ♩=132 (2/4) | F major | Gilt, gossip | Pno, Str, Fl, Hp, Bs | Loop 48 bars (0:44) + 4-bar "Bravo" tail |
| 013 | The Stilled Hour | Cabal scenes, masked guests, Vane's signet | LM-05 | ♩=60 | Twelve-tone row | Cold, patient, wrong | Sn (rim), Org, Str harmonics, Ch, Pno | Loop 24 bars (1:36) |
| 014 | A Gentleman's Wager | Vane; P14, P21, P34 | LM-07 | ♩=108 (3/4) | G major, wow | Charming, crooked | Str, Ob, Pno (short GAIN), Hp, Bs | Loop 32 bars (0:53) |
| 015 | Ostinato | Alkan; P36 | LM-16 | ♩=76 | G minor | Deadpan, devout | Org, Pno, Str, Ch | Loop 28 bars with four one-bar silences (1:28) |
| 016 | La Rue | P07, P08 (tocsin rendering), P25, R13 | LM-28 | ♩=112 (2/4) | E minor; *La Parisienne* in G | Tension, grievance | Sn, Tmp, Hn, Str, Acc | Loop 32 bars (0:34) |
| 017 | Impression | **Heroine's theme**; P20; R11, R12 (plein-air rendering); S06, S13 (2026 rendering) | LM-03 | ♩.=54 (6/8) | Whole-tone on D | Bright, proud, unsettled | Hp, Fl, Str, Pno, Ob | Loop 32 bars (1:11) |
| 018 | Sacrebleu! | Comedy: Berlioz's plans, Liszt's vanity, Offenbach, the dirigible permit | LM-11, LM-19 | ♩=152 | F major | Pompous, sly | Ob (low), Bs, Pno, Hn, Sn | Loop 16 bars (0:25) |
| 019 | Żal | Chopin; P11 | LM-13 | ♩=126 (3/4) | C♯ minor, E major trio | Elegant, homesick | Pno, Ob, Str, Hp | Loop 48 bars (1:09) |
| 020 | Two Hours of Light | **Love theme**; P22, lessons, CH-08 kiss, Window Talks, CH-12 dome, E02, the CH-E2 proposal (HG rendering) | LM-22 | ♩=66 | D, meeting on E | Tender, witty | Pno, Hp, Fl, Str, Bs | Loop 32 bars (1:56) |
| 021 | Golden Section | Delorme; P13, E05 | LM-09 | ♩=89 | F minor | Geometric, envious | Str, Ob, Hp, Org, Pno | Loop 34 bars, climax bar 21 (1:32) |
| 022 | Lumière | Lucile's errand: CH-03 purse, CH-07 POV, CH-09 reveal and dawn | LM-03, LM-07 | ♩=58 | Whole-tone in a minor frame | Ashamed, loving | Hp, Fl, Str, Pno | Loop 20 bars (1:23); quiet cue |
| 023 | Transcendence | Liszt | LM-14 | ♩=100 | E major | Theatrical, spiritual | Pno, Ch, Org, Str, Tmp | Loop 32 bars (1:17) |
| 024 | Escapement | Brücke; P18, R05 | LM-10 | ♪=210 (7/8) | B minor | Ticking menace | MBx, Bs, Str pizz, Sn, Tmp | Loop 32 bars (1:04) |
| 025 | Counterpoint of the Unremembered | Farrenc; P19 | LM-15 | ♩=96 | G minor | Brisk, principled | Fl, Ob, Pno, Bs | Loop 32 bars (1:20) |
| 026 | Blue Notes in the Dark | Julien; P17 | LM-08, LM-17 | ♩=92, swung | D Dorian | Smoky, sorry | Bs, Pno, Ob (low-pass), Org, Nz | Loop 24 bars (1:03) |
| 027 | Hymn of the Ward | Marthe; P37; Val-de-Grâce wards | LM-31 | ♩=63 | E Phrygian | Quiet authority | Org, Ch, Str, Hp | Loop 16 bars (1:01) |
| 028 | Confessions | CH-09 confessions; optional confessions; "The Truth, from You" | LM-13, LM-12, LM-02 | ♩=60 | D♭ major | Trust, relief | Pno, Str, Ob, Hn (muted) | Loop 24 bars (1:36) |
| 029 | Rhine Journey | W02; R06, R07, R10, R14 (town); R08 *Concordia* (deck rendering) | LM-29 | ♩=104 | E♭ major | Broad, foreign | Hn, Str, Tmp, Fl, Bs | Intro 4; loop 40 bars (1:32) |
| 030 | Nohant Afternoons | R03, R04, R01, P24; Sand | LM-23 | ♩.=66 (6/8) | G major, drone | Pastoral, warm | HG, Fl, Str, Bs, Tmp | Loop 32 bars (0:58) |
| 031 | The Lorelei | R09; LM-22 alone on the cliffs (CH-11) | LM-22, LM-17 | ♩=54 | A minor | Apart, echoing | Pno (Velvet, EDL 8), Org, Str | Loop 16 bars (1:11); quiet cue |
| 032 | Val-de-Grâce | P26; R02 Château d'Orsenne | LM-06, LM-31 | ♩=80 | C whole-tone / E Phrygian | Clinical, monumental | Org, Tmp (anvil), Ch, Str, Pno | Loop 32 bars (1:36) |
| 033 | Archon | The Audience, the Revelation, the footnote speech, the Testament (CH-E1) | LM-06, LM-05 | ♩=66 | C, whole-tone | Courteous, certain | Org, Str, Tmp, Ch | Loop 20 bars (1:13) |
| 034 | Eomma | S04, S15, Seoul amalgam floors; *Arirang* hummed | LM-32 | ♩=60 (3/4) | Pentatonic | Hold me | Ch (hum), Pno, Gy, Str | Loop 16 bars (0:48) |
| 035 | La Lumière | Dirigible flight (CH-14); CH-E2 finale flight (2:30): a ♩=132 rendering that unmasks a dormant LM-27 counter-line on V4 | LM-29, LM-03, LM-01 | ♩=120 | D major | Soaring, guilty-glad | Hn, Str, Hp, Fl, Tmp | Loop 40 bars (1:20) |
| 036 | Night of Stars | CH-14 roof: *La Nuit étoilée sur le Panthéon*; LM-30 heard first | LM-22, LM-03, LM-30 | ♩=63 | D major | Wonder | Hp, Fl, Pno, Str, Ch | Through-composed 64 bars (4:04), sync markers |
| 037 | Labyrinth I: Lutèce | CH-15 Party 1, Clefs I–II | LM-17, LM-04 / LM-24 | ♩=84 | D drone | Fused, uncanny | Twin plan: Acc / Gy, Pno, Bs, Sn ↔ kit | Loop 32 bars (1:31), shared bar clock |
| 038 | Labyrinth II: Hanseong | Party 2 (Min-jun's memories), Clefs III–IV | LM-24, LM-32, LM-02 / LM-04 | ♩=84 | F♯–G drone | Home seen wrong | Twin plan: Gy / Str, Pno, Bs, kit ↔ Sn | Loop 32 bars (1:31) |
| 039 | Labyrinth III: Orpheus | Party 3, Clefs V–VI | LM-17, LM-18 / LM-24 | ♩=84 | A–B drone | Do not look back | Twin plan: Ob / Gy, Hp, Org, Nz | Loop 32 bars (1:31) |
| 040 | Rank Up | Bond rank R2–R10; confidant variant | LM-01 | ♩=96 | D major, on C♯ | Warm | Pno, Hp, Str | Jingle, 2 bars (3 s); the R10 variant adds the friend's own note on their instrument (§3.1) |
| 070 | Concerto "Lost Era" — Opening (**GM**) | CH-13 gala opening cutscene | LM-01, LM-02, LM-14 | ♩=76 → 112 | D minor → D major | Debut, nerve | Pno I, Pno II, Str ×2, Hn, Tmp, Fl, Ch (8 voices) | Through-composed 1:58; hands off to MUS-112 on a downbeat |
| 095 | La Musique des étoiles | CH-17 opening and closing cutscenes (**GM**); the playable Window (7 voices, V7 UI); S14 Yanghwajin (piano-and-gayageum rendering, 5 voices) | LM-30, LM-22, LM-01 | ♩=69 | D major | Farewell, gratitude | GM: Pno, Hp, Fl, Str ×2, Hn, Ch, Syn (the Engine's last oscillators, low-passed) · Window: the same minus Str ×2 | Playable: loop 24 bars (1:23) with farewell layers (§5.6) |

### 4.2 Battle and boss (MUS-100–149)

Every battle bank holds the Recital set: Pno, Str, Hp, Fl, Ob (§2.6).

| MUS | Title | Usage | LM | Tempo | Key / mode | Mood | Instruments | Loop |
|---|---|---|---|---|---|---|---|---|
| 100 | The Ensemble | Regular battles, 1833; Echo/Gloom and automata layers on V4 | LM-20 | ♩.=150 (12/8) | B minor | Driving, gallant | Pno, Str, Hn, Tmp, Bs | Intro 2; loop 32 bars (0:51) |
| 101 | Duel of Tempos | Standard bosses (BOSS-01, 02, 04, 06, 07, 10, 37, 39, 40, 42); BOSS-29 Seoul rendering | LM-21 | ♩=168 | E minor | Two wills | Pno, Str, Hn, Tmp, Sn | Intro 4; loop 48 bars (1:09) |
| 102 | Encore! | Victory | LM-20, LM-01 | ♩=132 | D major | Triumphant, cheeky | Pno, Hn, Str, Tmp | 3-bar fanfare (LM-01 to C♯, then a sly turn to A) + 8-bar results loop |
| 103 | Fine | The party-wipe screen | LM-01, LM-18 | ♩=50 | D minor | Hush | Pno, Bs (heartbeat) | LM-01 notes 7 → 2 descending, stopping on E; 8-bar loop |
| 104 | The Barricade | BOSS-05 waves and powder keg | LM-28, LM-21 | ♩=152 | E minor | Smoke, courage | Sn, Tmp, Hn, Str, Acc | Loop 32 bars (0:50); keg layer (§5.5) |
| 105 | Passages | Piano Duels BOSS-03, BOSS-08, BOSS-35; its 16-bar prelude loops as field music in P15 and the P27 lobby | LM-21, LM-02 | ♩=138 | A minor vs A♭ major | Glittering combat | Pno ×2 (L/R), Str, Hp, Tmp | 8 Passage blocks × 4 bars + finisher (MUS-219 in CH-07) |
| 106 | Wit and Silence | BOSS-20 rhetoric duel | LM-07, LM-21 | ♩=116 | G major, wow | Fencing with words | Str, Ob, Pno, Hp, Sn | 8 Passage blocks; at Favor +60 drops to MUS-022 |
| 107 | Phantom Quartet | BOSS-11 | LM-08, LM-05 | ♩=176, swung | D Dorian → row | Spectral swing | Bs, Pno, Ob, Org, Nz | Loop 32 bars (0:44); each killed spectre mutes its voice |
| 108 | Steady… | Roussel: BOSS-12, BOSS-21; BOSS-42 | LM-05, LM-28 | ♩=126 | C minor | Military, grim | Sn, Tmp, Hn, Str, Org | Loop 32 bars (1:01); "Steady…" drops to a snare roll |
| 109 | Clockwork Predators | BOSS-09, 13 (HG piper rendering), 14, 38, 41 | LM-10, LM-21 | ♪=252 (7/8) | B minor | Machine hunger | MBx, Str pizz, Tmp, Sn, Hn | Loop 32 bars (0:53) |
| 110 | The Painter | BOSS-15; BOSS-25 *Ad Astra* (its retrograde section) | LM-09, LM-05 | ♩=144 | F minor | Brilliant, envious | Str, Ob, Org, Pno, Tmp | Loop 34 bars (0:57) |
| 111 | The Audience | BOSS-16 survival | LM-06 | ♩=66 | C whole-tone | Overwhelming calm | Org, Ch, Tmp (anvil), Str | Six sections, one per Archon turn; "Play for me." cuts to silence, then MUS-209 |
| 112 | Concerto "Lost Era" — Three Fronts | BOSS-17 Stage (7 voices); BOSS-18 Rafters, BOSS-19 Corridors (5-voice mixes) | LM-01, LM-02, LM-14, LM-21 | ♩=112 | D minor → F major → D major | Glory under fire | Stage: Pno I, Pno II, Str, Hn, Tmp, Fl, Hp | Three movements, each a 32-bar loop (1:09); §5.5 |
| 113 | Wardens | BOSS-22, 23, 24 | LM-21, LM-17 / LM-24 | ♩=168 | D, F♯, A by party | Fused colossi | Twin plan + Tmp | Loop 32 bars (0:46) |
| 130 | Vers la Coda | BOSS-26; CH-16 Heart Chamber field (pedal layer alone) | LM-25 | ♩=152 | C against D | The last argument | Org, Str, Hn, Tmp, Pno | Intro 4; loop 64 bars (1:41) |
| 131 | The Stilled Hour | BOSS-27 (7 voices); the 00:43 instant as intro | LM-25, LM-05, LM-01 | ♩=60 | Frozen row → Octave chord | Time held | Pno, Hn, Str, Org, Ob, Ch, Fl (Hp in the bank for Lucile's note on V7) | 16-bar loop under Voice layers; 15-s Octave cue (§5.5) |
| 132 | Le Clavier des Âges | BOSS-28 | LM-25, LM-06, LM-05 | ♩=176 | C (synth) against D | Industrial terror | **Syn**, Org, Tmp, Str, Pno | Loop 48 bars (1:05); each destroyed part mutes its voice |
| 140 | Ossia / The Unwritten | BOSS-31 (Gy rendering), BOSS-34 (Acc rendering) | LM-01, LM-02, LM-05 | ♩=160 | D; LM-02 inverted; row | The history that didn't happen | Pno, Str, Ch, Gy or Acc, Tmp | One 32-bar loop per HP bar; bar 2 is the Shadow Virtuoso |
| 141 | The Unstruck Bell | BOSS-43 (NG+) | LM-01 and medley | ♩=132 | Modulating | The last note | Pno, Str, Hn, Ch, Tmp | Loop 64 bars; every 10 turns quotes 8 bars of the replayed boss's track; LM-01 never resolves |

### 4.3 Epilogues (MUS-150–199)

| MUS | Title | Usage | LM | Tempo | Key / mode | Mood | Instruments | Loop |
|---|---|---|---|---|---|---|---|---|
| 150 | Le Frère de demain (**GM**) | The portrait: CH-E1 library at 23:00; CH-E2 coda | LM-30, LM-12 | ♩=63 | D major | The past says goodbye / hello | Pno, Hp, Fl, Ob, Str ×2, Hn, Ch | Through-composed 2:24; branch tails (§5.7) |
| 151 | Snow on Jeong-dong | CH-E1 main theme; reunion; a 16-bar 4/4 ballad section for the noraebang scene | LM-26 | ♩.=56 (6/8) | D major | Snow, home | Pno, Gy, Str, Hp, Fl | Loop 32 bars (1:09) |
| 152 | Seoul, Neon and Snow | W03; S03, S07, S12 | LM-24, LM-26 | ♩=92, swung | C Ionian | A city that never stops | Gy, Pno, Bs, Str, Nz | Loop 32 bars (1:23) |
| 153 | Static | S08 Euljiro and Line 2 | LM-10, LM-24 | ♪=231 (7/8) | B minor | Shuttered, buzzing | **Syn**, MBx, Bs, Pno, Nz ($1F) | Loop 32 bars (0:58) |
| 154 | Neon Ensemble | CH-E1 regular battles | LM-20, LM-24 | ♩.=150 (12/8) | B minor | Driving, backbeat | Pno, Gy, Bs, Str, Nz | Loop 32 bars (0:51) |
| 155 | The Clock Tower | S10 approach, New Year's Eve | LM-10, LM-26 | ♩=132 | E minor → D | Ascent against time | MBx, Str, Pno, Tmp, Hn | Loop 40 bars (1:13) |
| 156 | The Last Hour | BOSS-30 in the Hidden Study | LM-10, LM-05, LM-01 | ♩=144 | B minor; LM-01 to C♯ | Desperate, pitiable | **Syn**, MBx, Pno (upright map), Str, Tmp | Loop 48 bars (1:20); a dial reset inserts one silent bar |
| 157 | Harmonies — New Year's Eve Premiere | CH-E1 hall: REP-28's finale written on the blank page | LM-01, LM-26, LM-11, LM-12, LM-13, LM-14, LM-15, LM-16 | ♩=96 | D major | Gratitude in public | Pno, Str, Hn, Fl, Ob | Through-composed 3:12; each friend's variation quotes his or her motif; ends on D |
| 158 | Ending Roll — Seoul | Vignettes for the branch's party | Party LMs, LM-26 | ♩=88 | D major | Warm, proud | Pno, Gy, Str, Hp, Fl | Through 4:30, a sync marker per vignette |
| 159 | Credits — Seoul: Snow Falling Upward | Seoul credits | LM-26, LM-24, LM-30 | ♩=76 | D major | Bright, open | Pno, Gy, Str, Hp, Bs | Through 5:20 |
| 160 | Bosingak (**GM**) | Midnight, 33 strokes | LM-26, LM-01 | ♩=60 | D major | Promise | Ch, Str ×2, Pno, Hp, Gy, Tmp, Hn | Through 2:12; strokes in a bell voicing (Tmp, low Pno, Hp harmonic) |
| 170 | Salon Night, 1834 (**GM**) | REP-28's finale at Chopin's 24th-birthday supper, Sat 1 Mar 1834 | LM-27 | ♩=144 (3/4) | D major | Joy remembered | Pno, Str ×2, Fl, Ob, Hn, Hp, Bs | Through 3:30; it never repeats, because it is never written down |
| 171 | Paris, 1834 | CH-E2 winter Paris; E01 Salon of 1834 | LM-27, LM-04 | ♩=132 (3/4) | A minor → D major | Winter, belonging | Acc, Str, Hp, Pno, Bs | Loop 48 bars (1:05); Ledger layer (§5.7) |
| 172 | Le Diapason Bleu | E04; SQ-23 Walkman burial (Phone rendering) | LM-08 | ♩=100, swung | F Dorian | Candlelit, honest | Bs, Pnn, Ob, Str, Nz | Loop 32 bars (1:17) |
| 173 | Erasure | Canvas Ledger hunts, Living Tableau squads, E05 | LM-09, LM-03 | ♩=126 | F minor | Theft of light | Str, Ob, Hp, Org, Tmp | Loop 34 bars (1:05) |
| 174 | The Jury | BOSS-32 brushwork duel | LM-03, LM-21, LM-09 | ♩=120 | Whole-tone vs F minor | Her case | Hp, Fl, Str, Pno, Sn | 8 Passage blocks; Delaroche's +20 modulates to D |
| 175 | Masterwork | BOSS-33 | LM-09, LM-27, LM-21 | ♩=160 | F minor ↔ D major | The Salon fights back | Str, Hn, Tmp, Hp, Pno | Loop 34 bars (0:51) |
| 176 | Ending Roll — Paris | Vignettes (all 8, Julien if recruited) | Party LMs, LM-27 | ♩=92 | D major | Rooted, glad | Pno, Str, Hp, Fl, Acc | Through 4:50 |
| 177 | Credits — Paris: Il est resté | Paris credits | LM-27, LM-30, LM-04 | ♩=72 | D major | Rooted, wistful | Str (solo-violin map), Pno, Hp, Acc, Fl | Through 5:40; opens on one sustained string D (§5.7) |
| 178 | Coda: Room B-07 | CH-E2 coda as Seo-yeon, Tue 22 Dec 2026 | LM-24, LM-32, LM-01 | ♩=76 | D major, to C♯ | The past says hello | Gy, Str (solo-violin map), Pno, Org (decay hum), Nz | Three 16-bar sections keyed to place (6–8 min) |

### 4.4 Featured repertoire arrangements on the album

| MUS | Title | Scene | Instruments | Length |
|---|---|---|---|---|
| 201 | "Clair de lune (Debussy) — tavern pianino" [REP-01] | CH-02, Berlioz hears it | Pnn alone, dead keys honoured | 2:40 |
| 208 | "Ondine (Ravel) — Salon Lavergne" [REP-08] | CH-03, Sat 27 Apr 1833 | Pno (both zones on V0–V3), Hp | 3:05 |
| 213 | "Le jardin féerique (Ravel) — four hands" [REP-13] | CH-09 wedding, Min-jun and Liszt | Pno four hands (V0–V3), Str | 2:10 |
| 218 | "Vocalise (Rachmaninoff) — Night of Stars" [REP-18] | CH-14 | Pno, Str, Fl | 3:30 |
| 219 | "Étude in D♯ minor (Scriabin) — duel finale" [REP-19] | CH-07 | Pno ×2, Tmp | 1:45 |
| 231 | "Arirang (traditional) — Chopin's mazurka" [REP-31] | CH-E2 | Pno, Ob | 2:00 |
| 250 | "Sonata in F minor for four hands (Onslow) — Théâtre-Italien" [§15e] | CH-03, Tue 2 Apr 1833 | Pno four hands (V0–V3), Str | 2:20 |
| 277 | "Concerto for three keyboards (Bach) — Hiller's concert" [§15e] | CH-14, Sun 15 Dec 1833 | Pno ×3 (V0–V2), Str, Bs | 2:30 |

---

## 5. Adaptive Music Rules

All changes land on the next bar line unless stated; layer masks ramp over one bar (§2.7).

### 5.1 Secrecy tiers (Paris field and town songs)

Every Paris field song reserves V4 as the **Hour layer**. The tiers name the city's attention, not the cabal's knowledge (LAW-17), so the layer sounds like the city listening.

| Tier (CANON §11e) | V4 and other changes | Sting on entering the tier (V7) |
|---|---|---|
| Incognito 0–19 | The song as written | — |
| Murmured 20–39 | A second rim tick on beat 4 of every bar, barely audible; `whisper` SFX near gossiping NPCs | `tier_murmured` (two breathy noise puffs) |
| Watched 40–59 | V4 becomes LM-05's tick at one per second; every 8 bars V1 inserts the row's first four notes (D–C♯–A–B♭). A Watcher's cone (Watchers appear from CH-06) entering the screen adds `watcher_near` (a low string tremolo) | `tier_watched` |
| Hunted 60–79 | "Hunted" rendering: strings to pizzicato, accordion to oboe, tempo −8%; the tick doubles | `tier_hunted` (snare roll and LM-05's first four notes) |
| Compromised 80–99 | The field song is replaced by MUS-005; a Close Call plays MUS-005 at full tempo, and a win (−20) returns the field song at the bookmarked bar | `tier_compromised` |
| Unmasked 100 | Hard cut to silence, `piano_hit`, then MUS-005's escape rendering for BOSS-42's mini-dungeon | — |

Falling tiers revert at the next phrase end (8 bars) with no sting, so relief arrives quietly. From CH-14 (open war) the layer follows police and public events only (CANON §11e); in CH-E2 the Hour layer is removed and V4 returns to percussion.

### 5.2 Salon audiences

During *Phrase* the chosen REP arrangement owns V0–V4 (§6). The room is V7.

| Input | Audio response |
|---|---|
| Rapture 0–39 | `crowd_murmur` at 60% under the piece; fan rustles and a creaking chair on misses |
| Rapture 40–79 | Murmur fades to 20%; on crossing 50 and 75, a soft collective `crowd_sigh` |
| Rapture 80–100 | Room tone silent; echo feedback +16 (the room "opens") |
| Result | Applause by grade: 0–39 three polite claps; 40–79 a 2-s applause loop; 80–100 an ovation (4 s) and MUS-012's "Bravo" tail |
| Cabal Presence 1 | A pocket-watch tick at ♩=60 in the room tone, indifferent to the piece's tempo |
| Cabal Presence 2 | A second watch, half a second out of phase |
| Cabal Presence 3 | Both watches, and the hostess's piano map detuned +6 cents for the evening |
| Taste | Every salon runs at EDL 8 (CANON §15a); Taste sets the taps and feedback: Romantic, Velvet · Virtuosic, Bright taps · Sacred, Velvet at EFB +72 (a chapel ring) · Novel, Clear taps at EFB +16 (a dry, modern room) |

### 5.3 Duels

In MUS-105, MUS-106 and MUS-174 each Passage is a 4-bar block whose material matches the Passage type: Bravura (octave runs, horn), Pianissimo (piano alone, Velvet), Ornament (trills, harp), Cantabile (melody over strings), Improvise (a random block, transposed up a tone). **Favor** sets the accompaniment: below −40 the strings drop out of the player's blocks; above +40 the horn joins them; at ±100 the finisher plays. Thalberg's Three-Hand Effect plays its melody on Pno II with arpeggios split across V2 and V3 (the illusion of a third hand). In BOSS-32, Delaroche's speech (+20) modulates the cue from F minor to D, Lucile's key.

### 5.4 Weather, night and the Chrono-Labyrinth

**Rain:** `rain_loop` on V7 (house-clock noise in random 3–9-frame drips); the Rain rendering (Wet echo, −3 dB); `thunder` every 20–45 s, ducking music 6 dB for 1 s with the flash; interiors keep the rain at 40% through a low-pass. **Fog:** EDL two steps longer at map load, music −2 dB, so Paris sounds farther away. **River** maps add `river_lap`. **Night** maps (P02, P04, P10, P16, P22, P24, P28; CANON §11i) use the Night rendering (harp for flute, softer strings).

**The Chrono-Labyrinth (CH-15).** MUS-037–039 share one bank and one 84-BPM bar clock and use the **Twin plan**:

| Voice | Role |
|---|---|
| V0 | 1833 lead (accordion, strings or oboe) |
| V1 | 2026 lead (gayageum or low-passed piano), the same notes as V0 |
| V2 | Shared harmony (era-neutral piano or harp) |
| V3 | Shared bass, carrying the zone's Clef drone |
| V4 | Era percussion: snare and drips (1833) or lo-fi kit and subway hum (2026) |

The map gives each tile an **era value** 0 (pure 1833) to 15 (pure 2026); zone seams are painted as gradients 4–8 tiles wide (dungeons.md). The driver's twin balance sets V0/V1 on an equal-power curve; V4 switches instrument on the bar line once the value crosses 8; the echo switches Stone ↔ Bright at the same threshold; V7 crossfades rain-drip and subway-hum ambience; the dominant era owns the noise clock (§2.7). **Clef detuning:** V3 holds a drone of the party's undetuned Clefs; each struck plinth (KEY-32) removes that pitch with `fork_ring` and a 2-bar decay. When all six are detuned, only C♯, the Heart, is left sounding at the Heart gate. **Party switching** writes the bar clock, so the next party's track enters on the same bar, as if all three were one song in three rooms.

### 5.5 Battle rules

- **Entry and return.** The field song is bookmarked; after victory and MUS-102 it resumes at the bookmarked bar's downbeat. After boss battles it restarts from bar 1.
- **Light States** change the battle echo preset only (Dawn Bright, Noon Clear, Dusk and Candle Velvet, Night and Gloom Stone, Fog Wet). *Shift the Hour* plays a four-chime `shift_*` SFX.
- **Recital (CANON §5c).** On Movement I the slot upload brings the REP cue; battle music bookmarks and the cue takes V0–V4 (§2.2). Each movement is a loop; *Continue* advances at the next bar line with `recital_mov2` or `recital_mov3`; Movement III ends on its final cadence, then battle music resumes. A **broken** Recital plays `recital_break` (a string snap and piano slam), one silent bar, and the bookmark. CONDUCT plays over the Recital without breaking it.
- **Cadenzas** take V0–V4 for 6–8 s, each on its owner's material: "Scarbo" (MJ), LM-03 (LU), the *Dies irae* (BE), LM-12 (DE), LM-16 (AL), LM-13 (CH), Paganini's bell theme (LI), LM-15 (FA), LM-32 (SY), *hwimori* (JW), LM-08 (JU). A confidant's second phase adds 4 bars.
- **Set pieces.** BOSS-05: each of the five keg turns doubles the V4 snare. BOSS-11: killing a spectre mutes its voice (bass V3, drums V4, "sax" V1, piano V2); the cassette at 30% is a 4-bar Phone-echo break, and *Recognition* snaps the band back. BOSS-12/21: "Steady…" leaves only a snare roll until the shot is interrupted or fired. BOSS-28: destroying the Right Manual, Left Manual or Pedalboard mutes V2, V1 or V3 respectively, leaving the synth core alone.
- **The Three Fronts (MUS-112).** One sequence, three mixes: **Stage** (7 voices; Rapture ≥ 60 adds Pno II's octave doubling); **Rafters** (V0–V4 with the Stone echo low-pass; music box counter-line on V4); **Corridors** (V0–V4 with Clear echo at −4 dB; snare on V4). A front switch changes the mix on the next beat. **The eight-bar rescue:** Pno I falls silent for exactly 8 bars while Pno II covers, and the strings take Min-jun's line. BOSS-19's timeout plays a stage-door slam on V7 and Rapture's −20 drops the horn. Own Voice ≥ 6 unlocks a cadenza section (16 bars, solo piano).
- **The Octave (MUS-131).** The 00:43 instant: the tick stops, one bar of silence, then the frozen row as a seven-voice cluster on V0–V6. Each Voice replaces one cluster voice with that friend's LM-01 note on their instrument (§3.1), held, in whatever order the party acts. Lucile's octave D never takes a music voice: it rings on V7 as `octave_voice_d8`, played on the battle bank's harp (SMP-06, present in every battle bank) and held as a P7 sting. When all eight are lit, the 15-s Octave animation re-strikes the seven-note chord four times on V0–V6 under Lucile's held D, then a white flash and silence.

### 5.6 The Fleeting Window (CH-17)

MUS-095 opens in Grand Mode, then drops to 7 voices for the playable Window (V7 carries UI only; footsteps are muted). Under the 12:00 clock (CANON §11i):

| Event | Music |
|---|---|
| Free movement starts | 24-bar loop: Pno (the friends at the Engine), Hp, Fl, Hn, Ch, the low-passed Engine oscillator (Syn) and one free counter-melody voice |
| A farewell spoken (1:00 each) | The counter-melody voice adds that friend's leitmotif to its rotation (LM-11, LM-12, LM-16, LM-13, LM-14, LM-15; LM-08 for Julien) |
| 3:00, the Pact of the Door | Modulation up a tone for 8 bars, all six motifs in turn, then back |
| 1:30, the Question | V1–V6 hold an A pedal under the piano; the harp falls silent; `[MUS:silence]` on her answer |
| YES | Her harp D returns; the full theme resumes; the closing Grand Mode cutscene places her D on the step through |
| NO | Piano alone, slower; at "Stay." her harp D returns, alone; the phone's throw cuts to silence; the closing cutscene ends on the shards' last `shard_ring` |

A missed farewell's line during the credits is underscored by that friend's motif for 4 bars.

### 5.7 Epilogue rules

- **Spotlight (CH-E1).** Trending adds phone `camera_shutter` bursts near crowds; Headline adds a news-ticker blip pattern on V4 of MUS-152; Viral doubles the shutter bursts; the forced scrum at 100 plays a 12-bar press-scrum rendering of MUS-152 (full kit, −10% tempo).
- **Canvas Ledger (CH-E2).** MUS-171's harp counter-line gains one bar for every 4 canvases recovered (19 canvases: 5 bars at 19, the full line); an unrecovered canvas is never mourned in music.
- **Lecterns (CH-E2).** Each `lectern_hum` sounds a semitone lower than in 1833; as one goes dark after a major beat it plays `lectern_fade` (the held note detunes and dies).
- **MUS-150 tails.** Seoul: the D on harp, then piano, under Min-jun and Lucile. Paris: the same cadence; the bow-lift shot is scored in silence.
- **Paris credits (MUS-177)** open on one sustained string D on the solo-violin map: the note Seo-yeon is asked to write (KEY-39). In the coda (MUS-178) the phone video plays MUS-095 through the Phone echo preset, as a phone speaker would.

---

## 6. The Repertoire

**Numbering.** Each REP's arrangement is **MUS-2NN for REP-NN** (MUS-201 = REP-01, as CANON §15b's example). Real works performed by historical characters (CANON §15e), which have no REP ID, take MUS-250–278 and cite `[§15e]`.

**Method (binding).** Arrange only from first editions or public-domain scans (§7.2); reduce to five voices (melody, inner voice, bass, two colour voices); keep the composer's tempo and key; cut only at phrase ends. A **Recital cue** (≤ 1.5 KB, §2.7) has three looping sections, Movement I, II and III, using the battle bank's Recital set (Pno, Str, Hp, Fl, Ob; REP-00 also uses CH-01's Ch and Org); horn and timpani lines double only where the bank holds them. An **Invocation stinger** (✦ Scores) runs 8–15 s. Renderings: *grand* (salons, battle), *pianino* (the tavern), *upright* (the Hidden Study), *practice room* (Room B-07, a modern upright, brighter). Heat values are the canon's.

### 6.1 Future works and Min-jun's own (REP-00–REP-45)

| MUS | REP | Work | Scene (CANON §15d) | Arrangement: Movement I / II / III, or stinger |
|---|---|---|---|---|
| 200 | 00 | *Resonance* (hummed) | CH-01 | Ch hum over Org, beating at the target Echo's pitch; I stuns, II shatters (no III) |
| 201 | 01 | Debussy, *Clair de lune* | CH-P (practice room), CH-02 (pianino) | Opening theme in D♭, 9/8 / the *Un poco mosso* arpeggios / climax and closing chords |
| 202 | 02 | Debussy, *Arabesque No. 1* | CH-04, meeting Lucile | Opening triplet arpeggios / the theme / the close |
| 203 | 03 | Debussy, *Reflets dans l'eau* | CH-06, lesson on reflections | Opening ripples / the rising surge / the climax wave |
| 204 | 04 | Debussy, *Doctor Gradus ad Parnassum* | CH-11, for Czerny | One 40-s section (drill unlock) |
| 205 | 05 | Debussy, *The Snow Is Dancing* | CH-E1, first snow (also field music) | The patter in D minor / the middle melody / the close |
| 206 | 06 | Debussy, *La cathédrale engloutie* | CH-15 | Parallel-chord opening / the cathedral rising / the full-chord climax (V0–V3) |
| 207 | 07 | Debussy, *L'isle joyeuse* | CH-14, first dirigible flight | Trills and dance / the A-major tune / the coda's fanfare |
| 208 | 08 | Ravel, "Ondine" | **CH-03, Salon Lavergne** | The shimmering chord tremolo / the ondine's song / the climax and her vanishing arpeggio |
| 209 | 09 | Ravel, "Le Gibet" | CH-12, "Play for me" | The tolling B♭ alone / chords join / the last tolls (Coda) |
| 210 | 10 | Ravel, "Scarbo" | CH-14, Vane; Min-jun's Cadenza | Repeated-note figure / the leaping dance / the climax |
| 211 | 11 | Ravel, *Jeux d'eau* | CH-05, Pleyel's showroom | E-major arpeggios / the cascade / the glissando |
| 212 | 12 | Ravel, *Pavane pour une infante défunte* | CH-09, Chopin's confession | Theme in G / second theme / return in full chords |
| 213 | 13 | Ravel, *Ma mère l'Oye*, "Le jardin féerique" (four hands) | CH-09 wedding, with Liszt | Pno four hands (V0–V3) and Str; one 2:10 cue (SYN-02 flavour) |
| 214 | 14 | Rachmaninoff, Prelude in C♯ minor | CH-04, the barricade bells | The three-note motto in bell voicing / the agitated middle / the climax chords split over V0–V3 |
| 215 | 15 | Rachmaninoff, Prelude in G minor | CH-08, Julien | The march / the lyrical middle / the march returns |
| 216 | 16 | Rachmaninoff, Suite No. 2 | CH-07, rehearsing with Liszt | The Valse for two pianos |
| 217 | 17 | Rachmaninoff, *Isle of the Dead* | CH-12 ✦ (OPS-13) | Stinger: the 5/8 rowing figure, low strings and harp |
| 218 | 18 | Rachmaninoff, *Vocalise* | CH-14, Night of Stars | Melody on strings / the climb / the last rise (revive) |
| 219 | 19 | Scriabin, Étude in D♯ minor | CH-07 duel finale | The leaping octave theme / the climax / the final chords |
| 220 | 20 | Scriabin, Prelude for the Left Hand | CH-09 cell, CH-10 | V0 silent by design: the left hand alone, three sections |
| 221 | 21 | Scriabin, Sonata No. 5 | BQ-PC07 (Liszt's *Ecstasy*) | The low trill and upward flight / the languid theme / the ecstatic close |
| 222 | 22 | Scriabin, *Vers la flamme* | CH-16, Archon | The slow tremolo / the build / the blaze |
| 223 | 23 | Prokofiev, *Suggestion diabolique* | CH-12, Delorme | The repeated-note ostinato / the march / the final smash |
| 224 | 24 | Prokofiev, Toccata | CH-11, the *Concordia* | Repeated Ds / the chromatic battle / the climax |
| 225 | 25 | Prokofiev, *Visions fugitives* | CH-15 | No. 1 *Lentamente* (Dawn) / No. 7 *Pittoresco* (Dusk, harp) / No. 14 *Feroce* (Night) |
| 226 | 26 | Scriabin, *Prometheus* | SYN-15 only | 15-s cue: the "mystic chord" on Str, Fl and Ob (horn where the bank holds one); Lucile's colour part as harp |
| 227 | 27 | Kang Min-jun, *Concerto "Lost Era"* | CH-13; Recital afterwards | First-movement theme / the slow movement / the finale (from MUS-070 and MUS-112) |
| 228 | 28 | Les Amis and Min-jun, *Harmonies* | CH-E2 salons, BOSS-35 | The friends' variations in turn; **the finale is never in this cue** (it lives only in MUS-157 and MUS-170) |
| 229 | 29 | Kang Min-jun, *La Musique des étoiles* | CH-14, CH-17; Recital from CH-14 | LM-30 for piano: theme / harp joins / the D lands |
| 230 | 30 | Kang Min-jun, *Jeong-dong Nocturne* | Salons from CH-03; Recital from CH-13 | LM-02 as a nocturne; III ends on an open fifth: unfinished |
| 231 | 31 | Traditional, *Arirang* | Hummed CH-02, CH-11, CH-17; CH-E2 mazurka | Ch hum over Pno; the CH-E2 rendering is Chopin's mazurka (Pno, Ob) |
| 232 | 32 | Bach, Prelude in C (WTC I) | Safe salon piece | Broken chords / the pedal build / the final chords |
| 233 | 33 | Beethoven, *Pathétique*, II | Safe salon piece | Theme / the minor episode / the return |
| 234 | 34 | Chopin, Nocturne Op. 9 No. 2 | From CH-06, with his blessing | Theme in E♭ / ornamented return / cadenza and close |
| 235 | 35 | Debussy, *Prélude à l'après-midi d'un faune* | CH-05 ✦ (OPS-14) | The flute's descending opening, a harp sweep |
| 236 | 36 | Debussy, *La Mer* | CH-08 ✦ (OPS-15) | The first movement's dawn swell |
| 237 | 37 | Ravel, *Daphnis et Chloé*, Suite No. 2 | CH-06 ✦ (OPS-16) | The sunrise: murmuring harp and strings, the rising melody |
| 238 | 38 | Ravel, *La Valse* | CH-07 ✦ (OPS-17) | The waltz rising out of murk, then the crash |
| 239 | 39 | Ravel, *Le Tombeau de Couperin* (orchestral) | CH-10 ✦ (OPS-18) | The Rigaudon's opening |
| 240 | 40 | Rachmaninoff, Piano Concerto No. 2 | CH-11 ✦ (OPS-19) | The opening bell chords in crescendo |
| 241 | 41 | Rachmaninoff, Symphony No. 2 | CH-12 ✦ (OPS-20) | The Adagio's long melody (oboe for clarinet) |
| 242 | 42 | Rachmaninoff, *The Bells* | CH-14 ✦ (OPS-21) | The first movement's sleigh-bell glitter in a harp-and-piano bell voicing; no text |
| 243 | 43 | Scriabin, *Le Poème de l'extase* | CH-13 ✦ (OPS-22) | The climactic trumpet theme, on horn where the bank holds one, else strings |
| 244 | 44 | Prokofiev, Symphony No. 1 "Classical" | CH-08 ✦ (OPS-23) | The finale's opening dash |
| 245 | 45 | Prokofiev, *Scythian Suite* | CH-15 ✦ (OPS-24) | The closing sunrise crescendo |

### 6.2 The 1830s repertoire (CANON §15e)

| MUS | Work | Scene | Arrangement |
|---|---|---|---|
| 250 | Onslow, Sonata in F minor for four hands | CH-03, Chopin and Liszt, Tue 2 Apr 1833 | Pno four hands (V0–V3), Str; heard from the gallery (Velvet) |
| 251 | Chopin, Étude Op. 10 No. 3 | CH-05, played for Min-jun | Pno, the E-major melody, 1:40 |
| 252 | Chopin, Mazurkas Op. 7 | Salon ambience, P11 | Pno |
| 253 | Chopin, Ballade in G minor (fragments) | BQ-PC06 | The opening only; the cue stops mid-phrase, as he does (R-46) |
| 254 | Liszt, *Grande fantaisie de bravoure sur La Clochette* | Liszt's salon showpiece; *La Clochette* Cadenza | Pno, the bell theme in high octaves |
| 255 | Liszt, transcription of the *Symphonie fantastique* | CH-05, at Marie d'Agoult's | Pno, the *idée fixe* page |
| 256 | Berlioz, *Symphonie fantastique* | Tutti recipes (*Marche au supplice*, *Songe d'une nuit du sabbat*) | 6–10-s stingers: Hn, Str, Tmp, Ch |
| 257 | Berlioz, *Lélio* | *Chœur d'ombres* Signature | Ch, Str |
| 258 | Berlioz, overtures *Le roi Lear*, *Rob Roy*, *Les Francs-juges*, *Waverley* | Tutti recipes | One stinger per overture |
| 259 | Alkan, *Concerto da camera* No. 1 | P36, BQ-PC05 | Pno, Str |
| 260 | Farrenc, *Air russe varié* (sketches, R-58) | BQ-PC08; *Air russe* Signature | Pno; the theme and one variation, the second left unfinished |
| 261 | Farrenc, Overture No. 1, Op. 23 | CH-E2 | Str, Fl, Ob, Hn, Tmp |
| 262 | Mendelssohn, *The Hebrides* | GST-05 HEBRIDES | The opening: low strings, horn |
| 263 | Mendelssohn, *Songs without Words*, Book 1 | CH-11; *Song without Words* | Pno |
| 264 | Clara Wieck, *Caprices en forme de valse*, Op. 2 | CH-11 | Pno |
| 265 | Clara Wieck, Piano Concerto, Op. 7 (draft) | CH-11 | Pno, Str; a few bars, as a draft |
| 266 | Robert Schumann, *Papillons*, Op. 2 | CH-11, "Florestan" | Pno |
| 267 | Robert Schumann, *Impromptus*, Op. 5 | CH-11 | Pno |
| 268 | Czerny, *School of Velocity*, Op. 299 | CH-11 drills | Pno, exercise loops |
| 269 | Thalberg, operatic fantasy (title unspecified, CANON §15e) | BOSS-08, BOSS-35 Passages | **A project-owned pastiche** in his manner on Bellini's "Casta diva"; no Thalberg opus is quoted |
| 270 | Meyerbeer, *Robert le diable* | CH-13 gala | Str, Hn, Org |
| 271 | Schneitzhoeffer, *La Sylphide* | CH-13, Taglioni's interlude | Hp, Fl, Str |
| 272 | Rossini, *Guillaume Tell* overture | Salons; CH-07 embassy (Rossini present) | The galop: Str, Hn, Tmp |
| 273 | Bellini, "Casta diva" (*Norma*) | Salons | Ob as the voice, Hp, Str |
| 274 | Paganini, Caprice No. 24 | BOSS-36 | Str (solo-violin map), Pno |
| 275 | Auber, *La Parisienne* | Streets; LM-28 | Acc, Sn |
| 276 | Rouget de Lisle, *La Marseillaise* | CH-04 march; the Sergent off-key | Acc, Sn; the Sergent's rendering detuned |
| 277 | Bach, Concerto for three keyboards | CH-14, Hiller, Chopin and Liszt, Sun 15 Dec 1833 | Pno ×3, Str, Bs; arranged from BWV 1063 (D minor) |
| 278 | *Dies irae* (plainchant, as quoted in the *Fantastique*) | Berlioz's Cadenza | Ch, Org |

---

## 7. Repertoire Clearance (2026)

### 7.1 Clearance table

US rule: works first published in 1930 or earlier are public domain as of 1 Jan 2026 (95-year term). EU rule: life + 70 (CANON §15d).

| Composer | Died | Works used | First published | US 2026 | EU 2026 | Risk | Recommendation |
|---|---|---|---|---|---|---|---|
| Claude Debussy | 1918 | REP-01–07, 35, 36 | 1891–1910 | PD | PD since 1989 | Low | Durand and Fromont first editions; *Golliwogg's Cakewalk* excluded (sensitivity) |
| Maurice Ravel | 1937 | REP-08–13, 37–39 | 1900–1921 | PD | PD (EU 2008; France since 2016 after wartime extensions) | Low | Demets and Durand first editions; *Boléro* excluded; both concertos (1932) excluded |
| Sergei Rachmaninoff | 1943 | REP-14–18, 40–42 | 1893–1920 | PD | PD since 2014 | Low | Gutheil first editions; *Rhapsody on a Theme of Paganini* (1934) excluded; *The Bells* used without its text |
| Alexander Scriabin | 1915 | REP-19–22, 26, 43 | 1895–1914 | PD | PD since 1986 | Low | Belaieff, Jurgenson and Russischer Musikverlag first editions |
| Sergei Prokofiev | 1953 | REP-23–25, 44, 45 | 1913–1925 (*Visions fugitives*: the appendix fixes the year; ≤ 1930 either way) | PD | PD since 2024 | Medium | Confirm **publication**, not composition, by 1930 for each; avoid revised Soviet-era editions; Sonata No. 7 (1942) excluded |
| Chopin, Liszt, Berlioz, Alkan, L. Farrenc, Mendelssohn, C. and R. Schumann, Czerny, Onslow, Meyerbeer, Schneitzhoeffer, Rossini, Bellini, Paganini, Auber, Rouget de Lisle, Bach, Beethoven | 1750–1896 | REP-32–34; MUS-250–278; LM-11, LM-28 | 1722–1836 | PD | PD | Low (editions only) | Early editions or PD scans; never a modern Urtext |
| Thalberg | 1871 | None quoted (MUS-269 is a pastiche) | — | — | — | None | Keep the pastiche whatever title the appendix fixes |
| Traditional | — | REP-31, LM-32 *Arirang*; the *Dies irae* | Folk / plainchant | PD | PD | Low | Notate the common folk melody from a pre-1930 printed source; no modern arrangement or later lyric |
| Project originals | 2026 | REP-27–30; every LM except the quotations in LM-11, LM-28, LM-32 | 2026 | Studio copyright | Studio copyright | — | Register the score; credit "Les Amis" in-fiction only |
| Excluded (CANON §15d) | — | Prokofiev Sonata No. 7; Rachmaninoff *Rhapsody*; Ravel concertos; *Golliwogg's Cakewalk*; *Boléro*; any jazz composition or recording | — | — | — | — | Never used, never quoted |

### 7.2 Traps and procedure

1. **Editions.** Some EU states grant separate rights to critical editions (Germany, for example, protects scholarly editions for 25 years). Arrangers work only from first editions or PD scans and log each cue in the **source ledger**: MUS ID, edition, publisher, year, scan archive.
2. **Recordings.** None are used; every sound is synthesized by the driver from project-recorded samples.
3. **Credit.** In-game titles always name the composer (LAW-20); no publisher marks appear.
4. **Territories.** In Japan (2018) and the Republic of Korea (2013) the move to life + 70 did not revive expired works; under the earlier terms, including Japan's wartime additions for Allied nationals, all five future composers had expired before those dates. Counsel confirms per territory before the Switch submission.

### 7.3 Sound-alike audit

Every melody in LM-08, LM-24 and MUS-002, 026, 107, 152, 153, 154 and 172 is compared by a staff musicologist against jazz standards and published lo-fi catalogues; any four-bar melodic match, or a recognisable riff, is rewritten. Julien's tapes are evoked by harmony and texture (extended chords, modal vamps, quartal voicings) and never by tune (R-15).

---

## 8. SFX List

Names are the `[SFX:name]` vocabulary (CANON §16a). The starter set of dialogue_style_guide §2.5 is kept unchanged and marked †. Voice and priority follow §2.2–§2.3.

### 8.1 SFX sample bank (resident, ≤ 8,192 B)

| SMP | Sample | Bytes | Used for |
|---|---|---|---|
| X01 | Piano cluster (low, struck) | 1,440 | `piano_hit` family |
| X02 | Bell | 720 | Chimes, ATB ding, Recital and spell chimes, Octave Voices (transposed) |
| X03 | Wood knock | 216 | `fallboard_tap`, `door_creak` start, wood footsteps |
| X04 | Stone grit | 288 | Stone and cobble steps, rubble |
| X05 | Metal ring | 360 | Blades, `fork_ring`, automata |
| X06 | Spring | 216 | Automata collapsing "into springs" |
| X07 | Glass | 540 | `glass_break`, ICE |
| X08 | Crowd murmur | 576 | `crowd_murmur`†, salons, Onlookers |
| X09 | Gong (*jing*) | 648 | BEAT, Samulnori, the jing in SYN-19 |
| X10 | Small gong (*kkwaenggwari*) | 288 | BEAT, Samulnori |
| X11 | Low thump | 360 | `rifle_shot`†, heavy impacts, *buk* |
| X12 | Water | 324 | `river_lap`†, WATER, wading |
| X13 | Paper | 180 | `page_turn`†, Annotate, Sketch |
| X14 | Clock tick | 72 | `clock_tick`†, CHRONO, Rubato, Coda |
| X15 | Camera shutter | 144 | Phone camera (KEY-02), Spotlight |
| X16 | Square click (one cycle) | 18 | Menu clicks (CANON §15a) |
| X17 | String snap | 252 | `recital_break` |
| X18 | Hand clap | 108 | Applause built from re-triggered claps |
| X19 | Bowed swell | 432 | BOW, Strings Cue |
| X20 | Brass stab | 396 | FIRE, Brass Cue, Synergy banners |
| | **Total** | **7,578** | 614 B spare |

Noise-based sounds (rain, wind, swishes, breath, static, thunder) cost no sample bytes (§2.7, noise clock rule).

### 8.2 The list

| Category | Voice | SFX |
|---|---|---|
| UI | V5 | `cursor_move` (square click, C7) · `cursor_confirm` (rising fifth) · `cursor_cancel` (falling fifth) · `cursor_buzz` · `menu_open` / `menu_close` · `atb_ready` (the two-note ding, bell B5–E6) · `choice_open` (harp pluck) · `slip_tick` (Bite Your Tongue timer, one per second) · `slip_timeout` · `save_lectern` (held bell fifth) · `item_get` (three rising harp notes) · `key_item_get` (four notes ending on C♯) · `coin_clink`† · `bond_chime`† (engine-played on `[BP:]` ≥ +15) · `sketchbook_open` · `almanach_entry` |
| UI, CH-E1 | V5 | `phone_tap` · `phone_ping` (a rising sixth) · `camera_shutter` · `translate_beep` |
| Footsteps (party leader, alternate walk frames) | V5 | `step_cobble` · `step_mud` (rain) · `step_parquet` (salons) · `step_marble` (Louvre, Opéra) · `step_carpet` (near-silent) · `step_stone` (quarries) · `step_bone` (ossuary) · `step_water` (sewers, wading) · `step_wood` (decks, barricades, tavern) · `step_grass` · `step_gravel` (Montmartre) · `step_snow` (winter 1834, Seoul) · `step_tile` (subway, conservatory) · `step_iron` (catwalks, clock tower) |
| Ambience | V7 | `rain_loop`† · `thunder`† (NCK $14) · `river_lap`† · `wind_loop` · `crowd_murmur`† · `crowd_gasp`† · `crowd_sigh` · `bell_toll`† · `harbour_bell` (Le Havre) · `fire_crackle` · `paddle_wheel` (*Concordia*) · `steam_hiss` · `subway_rumble` · `traffic_hush` · `whisper` |
| Story and event | V6 / V7 | `fallboard_tap` (**two soft wood knocks**, Min-jun's tell) · `piano_hit`† (the low cluster) · `rift_hum`† · `lectern_hum` / `lectern_fade` · `fork_ring`† (Clef detuning) · `shard_ring` · `decay_hum` (the shard after 08:03; the coda's hum) · `window_open` (rising bells, noise "snow") · `phone_land` (16:52) · `door_creak`† · `glass_break`† · `quill_scratch`† · `page_turn`† · `clock_tick`† · `whittle` (Théo) · `cough_soft` (Théo and Chopin's foreshadowing only, never Miasma or crowds, CANON §16e) · `kiss_sparkle` (the two kisses) |
| Weapon hits | V6 | `hit_baton` (swish, tap) · `hit_brush` (wet slap) · `hit_swordcane` (draw and slash) · `hit_rapier` (thin ring) · `hit_hammer` (wooden thud) · `hit_quill` (scratch-stab) · `hit_sabre` (broad slash) · `hit_folio` (book slap) · `hit_bow` (twang, rosin) · `hit_drumsticks` (rim and tom) · `hit_cane` (tap) · enemies `hit_claw`, `hit_bite`, `hit_clank` (automata), `hit_echo` (reverse swell), `hit_rifle` (butt-stroke) · `miss_whiff` · `defend_block` |
| Outcomes | V6 | `crit` (= `piano_hit`) · `piano_hit_boss` (two clusters an octave apart) · `ko_party` (falling harp glissando) · `echo_dissolve` (a chime rising into silence) · `automaton_collapse` (spring cascade) · `human_routed` (running steps) · `encore_revive` (a clap burst) |
| Spells (tier n = n bell chimes first) | V6 + V7 | FIRE `spell_vermilion` (brass stab) · ICE `spell_cerulean` (glass harmonics) · WIND `spell_zephyr` (breath sweep) · EARTH `spell_ochre` (timpani rumble) · BOLT `spell_sforzando` (struck-string crack) · WATER `spell_ondine` (harp arpeggio) · LIGHT `spell_lumen` (rising major triad) · SHADE `spell_umbra` (reversed minor cluster) · CHRONO `spell_tempus` (reversed ticks under the wow; **never the synth**) · `heal` · `buff_up` / `debuff_down` · `cure` |
| Statuses | V6 | `st_hush` (muffled thump) · `st_reverie` (three-note lullaby) · `st_stagefright` (two heartbeats) · `st_out_of_tune` (detuned bend) · `st_discord` (tritone) · `st_fermata` (the tick stops) · `st_allegro` / `st_lento` · `st_unwritten` (a page torn backwards) · `st_marble` (stone crack) · `st_miasma` (dull low wind) · `st_coda` (one tick per count) |
| Unique commands | V5 / V6 | RECITAL `recital_start` (`fallboard_tap`, then a chord), `recital_mov2` / `recital_mov3` (two / three rising chimes), `recital_burst`, `recital_break` (string snap, piano slam) · CONDUCT `conduct` · PLEIN AIR `brush_stroke`, `shift_dawn` / `_noon` / `_dusk` / `_night` (four chimes rising, level, falling, low) · ORCHESTRATE `cue_strings`, `cue_winds`, `cue_brass`, `cue_percussion`, `cue_chorus`, `tutti`, `cacophony` (detuned tutti) · CANVAS `pigment`, `canvas_strike`, `sketch` · ÉTUDE `etude_input` (each correct press a rising piano note), `etude_fail` · RUBATO `rubato_borrow` (ticks rewinding), `rubato_repay` (ticks accelerating) · TRANSCEND two chime sets in octaves; `transcribe` · COUNTERPOINT `annotate`, `canon`, `fugue`, `cadence` · BOW `sostenuto`, `spiccato` · BEAT `beat_kkwaenggwari`, `beat_janggu`, `beat_buk`, `beat_jing`, `beat_perfect` · IMPROVISE `reel_spin`, `reel_stop` (a pizzicato note per reel), `blue_note` · common `tacet`, `swap`, `flee` |
| Synergy and Octave | V6 / V7 | `synergy_banner` (piano glissando into a brass chord) · `octave_voice_d`, `_e`, `_fs`, `_g`, `_a`, `_b`, `_cs` (a bell doubling each friend's held note, §3.1) · `octave_voice_d8` (Lucile's D on the bank's harp, §5.5) · `octave_fire` |
| Duels | V6 | `passage_ready` · `passage_perfect` / `_good` / `_miss` · `favor_shift` · `composure_break` · `three_hand` · `duel_bravura`, `duel_pianissimo`, `duel_ornament`, `duel_cantabile` · rhetoric `wit`, `charm`, `evidence`, `silence` (a clock that stops) · brushwork `light`, `colour`, `composition`, `feeling` |
| Secrecy and attention | V7 | `secrecy_rise` (candle flare: a match puff and a bell ping that rises with the tier) · `secrecy_fall` (the candle gutters) · `tier_murmured`, `tier_watched`, `tier_hunted`, `tier_compromised` (§5.1) · `watcher_spot` (spoon on glass, string stab) · `watcher_near` · `onlooker_gasp` (each Heat gain) · `onlooker_flee` · `slip_warning` · CH-E1 `spotlight_flash` |
| Boss telegraphs | V7 | `rifle_cock` ("Steady…") · `rifle_shot`† · `boiler_hiss` (BOSS-14, rising) · `clock_chime` (BOSS-09) · `train_approach` (BOSS-29) · `door_close` (BOSS-23) · `dial_tick` (BOSS-30) · `stilled_tick` (BOSS-27) · `keg_fuse` (BOSS-05) |

---

## 9. Cue Tags for Writers

- `[MUS:LM-xx]` plays the motif's main track (§3.2); fixed canon tracks may be cited directly (`[MUS:MUS-095]`); `[MUS:fade:n]` and `[MUS:silence]` as in the style guide. Any other track or rendering is marked with a writer's comment (`// MUS-006 rain`) and placed from the audio cue sheet, until the cue-tag CCR below is adopted.
- `[SFX:name]` uses §8's names only. A missing sound is requested from this doc, never invented in a script.
- Story performances cue their MUS-2NN arrangement after the spoken attribution (LAW-20). Format example only (prologue_and_act1.md owns the scene):

```
[MUS:silence] {ANIM:PC-01:fallboard_tap} [SFX:fallboard_tap]
MIN-JUN  [P:PC-01:neutral] *Ondine*, from *Gaspard de la nuit*. By Maurice Ravel.
{ANIM:PC-01:play_piano}   // MUS-208 (REP-08), grand rendering
```

---

## Canon Additions & Cross-Doc Notes

**New facts in this doc's own families (no canon change needed).**
- **Track IDs** MUS-002–040, 102–113, 131–141, 151–159, 171–178 and 200–278 are defined here; fixed canon IDs are untouched. *Affects:* scenario docs, epilogues.md, dungeons.md, overworld_and_towns.md (cue notes).
- **Main track per leitmotif** (§3.2), the target of `[MUS:LM-xx]`. *Affects:* dialogue_style_guide and all writers.
- **The final SFX vocabulary** (§8), keeping every starter name of dialogue_style_guide §2.5. *Affects:* all scripts; combat_ensemble's Audio Cue Visuals (`atb_ready`, Recital chimes, the §8.2 telegraphs).
- **Octave orchestration** (§3.1: MJ piano, BE horn, DE strings, AL organ, CH oboe, LI choir, FA flute, LU harp); in BOSS-27 Lucile's D always rings on V7 (§5.5). *Affects:* combat_ensemble §6.7, bosses.md.
- **The tavern pianino's dead keys are E♭4, A♭4 and C5** (MUS-007, MUS-201); Théo's CH-E2 repair restores them. *Affects:* prologue_and_act1, overworld_and_towns (P04), historical_cast.
- **LM-05's row** D–C♯–A–B♭–F♯–F–B–C–G♯–G–E–E♭, for any puzzle or document that quotes it. *Affects:* dungeons.md, anachronists.md.
- **LM-17 roots** follow world_rules_and_lore §4 (Clefs I–VII = D E F♯ G A B C♯); the Lorelei hums a quarter-tone flat of A, outside the network. *Affects:* dungeons.md (R09).
- **Chrono-Labyrinth audio** (§5.4): tile era values 0–15, 4–8-tile gradient seams, one bank and bar clock for MUS-037–039, a Clef pitch removed per struck plinth, C♯ alone at the Heart gate. *Affects:* dungeons.md.
- **Recital timing:** the movement's effect applies at once; its music advances at the next bar line. No mechanical change. *Affects:* combat_ensemble (note).
- **REP-25's movements** are *Visions fugitives* Nos. 1, 7 and 14 (Dawn, Dusk, Night). *Affects:* skills_and_progression, combat_ensemble.
- **The CH-17 score** (§5.6): MUS-095 voices the Engine's last oscillators on the reserved synth (within CANON §15a), with farewell layers, the Pact modulation and the Question's pedal. *Affects:* act4_and_epilogue.
- **Epilogue scoring** (§5.7): the Paris credits open on one sustained string D; the coda's phone video plays MUS-095 through the Phone echo; MUS-171 grows with the Canvas Ledger; CH-E2 Lecterns hum a semitone lower. *Affects:* epilogues.md, overworld_and_towns.
- **Presentation-only layers** for Secrecy tiers and Cabal Presence (§5.1–§5.2) change no values. *Affects:* secrecy_and_trust, salons_duels_and_economy.
- **`cough_soft`** is reserved for Théo and Chopin's foreshadowing (CANON §16e). *Affects:* historical_cast, scenario docs.

**Canon Change Requests.**
- **CCR: cue-tag syntax** (CANON §16a, dialogue_style_guide §1.2): allow `[MUS:MUS-###]` for any track and a rendering suffix (`[MUS:MUS-006:rain]`), because renderings (§2.7) are how the score varies cheaply. Until adopted, scripts use writer's comments (§9). *Touches:* §16a, the style guide, scenario docs.
- **CCR: track naming for non-REP works** (CANON §15b): §15e works have no REP ID, so MUS-250–278 cite `[§15e]`; REP arrangements follow MUS-2NN = REP-NN. *Touches:* §15b.
- **CCR: Thalberg's fantasy** (CANON §15e): MUS-269 is a project-owned pastiche in his three-hand manner on Bellini's "Casta diva", so no Thalberg opus needs clearing whatever title the appendix fixes. *Touches:* §15e, historical_notes_and_liberties, salons_duels_and_economy (Passages read "Thalberg: Fantaisie").
- **CCR: Bach's concerto for three keyboards** (CANON §3a, §15e): arranged from BWV 1063 in D minor; if the appendix fixes BWV 1064, MUS-277 is rearranged on the same voice plan. *Touches:* §15e, historical_notes_and_liberties, act4_and_epilogue (CH-14).
- **Appendix requests** (no canon change): cite the pre-1930 printed source for *Arirang*; confirm each Prokofiev first-edition year (*Visions fugitives* above all); file the §7.2 source ledger.
