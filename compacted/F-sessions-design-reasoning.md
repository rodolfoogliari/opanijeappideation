# Opanijé — Design Reasoning, Compacted

App for learning Afro-Brazilian percussion (Ketu Candomblé). Master = **Junior**, named tradition
authority and co-founder; sacred material's *form* is his (red line #1). Also live: **#2** standing is
only earned, never machine-granted; **#5** anything given free is permanent; **#6** takedown reach over
master recordings. **D26: no microphone, anywhere.** Acceptance test **FF3**: single-player adults *and*
beginners who cannot play to a metronome, both playing on day one. M1's headline numbers:
first-session completion, day-7 return.

---

## 1 · The screen drum — architecture (the core)

### 1.1 Form and zone geometry

- **G6/D56:** phone **flat on a table, landscape, two hands**. Screen = a drum head divided into
  **zones**. The student **vocalizes the part and strikes the zone the syllable names**.
- **G26 (MASTER-CONFIRMED):** it may **resemble a real drum viewed from above**.
- **G14/D65 — the stroke set is fixed by the material:** **three zones on hand instruments — slap,
  tone, bass; two on stick instruments — rim and skin.** *Rejected:* designer-chosen
  "easy/medium/hard" difficulty steps.
- **Zone labels are Junior's syllables, never the English words.** "Slap/tone/bass" is the founder's
  specification of *which strokes exist*; putting those words on screen would reintroduce exactly the
  Western notation D53 removed. Easy to collapse; must not be.
- **R74 — one surface, zone count as the dial.** Tap-along and the screen drum are **the same
  instrument at different settings**, not two builds: one zone at the door → two → three. G14 fixes
  the top of the dial. (An earlier PM-rec of bass/open/slap — "do not build five before Junior has
  seen three" — is superseded in specifics by G14.)
- **INPUT-77 (open):** which instruments take the three-zone hand vocabulary vs the two-zone stick
  vocabulary, and whether the reference instrument (R15's pulse-carrier) needs its own. Founder names
  the mapping; **Junior confirms it against the solfejo** — under G3 the syllable set defines the
  stroke set, so a mismatch shows up as a zone with no syllable or a syllable with no zone.

### 1.2 What the surface can and cannot encode

**Can:** which stroke, and when. **Cannot: how hard** — touch velocity is unreliable across devices and
must not be relied on. Treated as *useful*: it keeps the screen drum a **transcription device**, not a
simulation of playing — protecting both the governance line and the real instrument.

### 1.3 Audio engine — scheduled, not triggered (G10/D60)

> **Your finger keeps his groove alive; the drum tells you where you are; the app never says.**

- The app **plays Junior's correct part, pre-rendered, in time with the battery**; the student's
  strike **keeps that part alive** rather than firing its sample per hit.
- **Rejected: triggered sample playback** (the original Addendum-01 assumption) — it makes perceived
  quality hostage to device latency.
- **Scheduled audio is buffered ahead and immune to output latency.** DERIVED: the **native
  low-latency engine leaves Release 1's critical path** — no Oboe/AAudio, no `AVAudioEngine` needed
  for acceptability (risk #18, nobody here has built mobile audio, is unresolved but no longer
  load-bearing). **Per-device calibration also leaves Release 1.**
- **R73:** read the timing grid **from the authored render, never from audio peak detection**. The
  backing is pre-rendered, so the grid is known — never infer what was authored.
- **Ledger 45, the honest risk:** *scheduled audio is experienced as playing rather than as miming.*

### 1.4 Hit detection — the binary window (G9/D59)

- **One generous window.** Inside it the stroke lands in the groove; outside it, it does not. **No
  tiers, labels, percentages, per-strike marks or session accuracy summary on any surface** (Mandate 01
  §10 item 11).
- Three reasons, strongest first:
  1. **The offset is unknowable, so the readout would be false.** Android exposes only two hardware
     flags — `android.hardware.audio.low_latency` (continuous output ≤45 ms) and
     `android.hardware.audio.pro` (round-trip ≤20 ms), CDD §5.6/§5.10 — and **no runtime API for
     actual latency**. Touch latency is separate, undocumented, varies by device and refresh rate. An
     assumed offset is wrong by a different amount on every phone, and the error lands hardest on
     low-tier Android — the domestic practitioner the free door exists for. *A student would be told
     he is sloppy because his phone is cheap.*
  2. **The governance line breaks as the surface becomes a drum.** A tap is a screen fact on
     tap-along; on a surface whose purpose is to stand in for a drum, a precision grade is a musical
     verdict (Mandate 01 §10 item 3 → §3).
  3. **FF3.** Public absolute performance feedback reduces perceived competence among weaker learners
     (Sailer et al. 2017) — precisely the FF3 population.
- ***Rejected, offered and declined:*** tiers on tap-along only; tiers everywhere by amending Mandate
  01 §3 (the founder *could* have withdrawn his own rule — offered as option 3, declined). Recorded so
  the rule is known to have survived a live challenge.
- ***Device study rejected.*** The flags are runtime queries — no list to acquire or let go stale —
  and they err safe: an undeclared flag only means the OEM didn't declare it, so some fast phones get
  the conservative path and **no slow phone gets a broken instrument**. Crowdsourced charts (n-Track,
  13 731 devices) graded **REPORTED, never VERIFIED** — the operator disclaims accuracy and the
  Android chart contains an "iPhone X". An OLX listing sample was **rejected as a proxy for the
  installed base** (relevance ranking rewards promotion spend and resale value). Kept: Samsung ≈33.8 %,
  Xiaomi ≈15.7 %, sub-US$200 devices 41 % of shipments. **R75: log both flags from day one** — real
  distribution known within weeks at zero cost; the pre-launch device purchase was withdrawn.

### 1.5 Sample playback, layering, coexistence

**D77 — the drum always sounds.** Three layers coexist:

1. **The scheduled render** — Junior's correct part, in time with the battery, alive while fed.
2. **Out-of-window strikes fire a one-shot of the real stroke** — the student's actual hit, audible,
   off the groove, because a real drum struck off-time still sounds. **Latency is tolerable here
   precisely because an off-grid hit has no exact reference to smear against.**
3. **Wrong-zone strikes sound as themselves** — striking slap where the part wants bass gives **an
   audibly wrong stroke at the right time**. The student therefore **hears stroke errors and never
   hears timing errors**: the clean split, already implicit in G3.

**D78 — the sustain model: the part fades when unfed and returns when fed. No fail state exists
anywhere.** The battery never stops for you; your part thins when you stop feeding it and returns when
you strike again — what happens in a real battery when a player drops out and rejoins. *Rejected:*
silence (it produced risk #25) and any fail screen.

**Open PM-ASSERTION, never decided:** whether a wrong-zone strike sounds *instead of* or *on top of*
the correct part — a real pedagogical difference.

**Stroke sample library (D58, decided by G19).** Not derivable from the battery stems — individual
strokes cannot be cleanly extracted from a performance. Separate capture, same room, same instruments,
same day, **irrecoverable afterwards**. Spec: every instrument of the free battery; every stroke the
solfejo names; **several velocity layers per stroke, several takes each; isolated one-shots, clean, no
room bleed**. ~20–40 min, mechanical, no take direction. **INPUT-70 (Junior):** which strokes, and
whether any stroke or drum is off-limits to isolated sampling — a one-shot of a consecrated drum is a
different object from a passage of music. **C22:** D58's original justification ("the screen makes no
sound, so the app must") was destroyed by D60; kept anyway (R80 — 20–40 min buys an option that cannot
be bought later), and **D77 re-justifies it: the library exists so the drum is honest.**

### 1.6 Where it sits in the product

- **G13/D63/E20 — the first session runs the whole sequence at its simplest setting:** voice → voice
  over battery → battery → tap door → **screen drum**, "all the way, dumbed down."
- **D64 — R70 revised.** R70 put the screen drum *behind* the door, "never a shortcut past the
  instrument." **The order survives; the distance does not.** "Advanced mode" is no longer advanced —
  it is the product. Risk #23 (a phone game whose users never buy an instrument) rises accordingly and
  **was re-rated without a new number, so it is easy to miss**.
- DERIVED and **permanent**: reaching the screen drum in the free first session **commits it to the
  free tier forever** (red line #5) — the one high-cost derived reading in the estate.
- **Mandate 01 §10 item 10 now gates the free door:** no screen-drum surface ships without Junior
  having seen it. Building unshown is expected; shipping unshown is not.
- Mid-play nothing appears except the presence lamp. E3 stands: arm's length, no menus.

---

## 2 · Vocalization (Addendum 01)

- **G11:** vocalization is the app's **founding idea**. **G20 (MASTER-CONFIRMED):** it is genuinely
  this tradition's transmission method (INPUT-36 closed).
- **G2/D53:** vocalization **replaces Western notation product-wide** — no tab, staff, rhythm grid or
  piano-roll on any surface.
- **G3 (load-bearing):** **Junior's solfejo encodes stroke as well as rhythm.** The syllable *names the
  sound*. Without it the substitution would be "a downgrade dressed as a cultural choice." With it one
  artifact does three jobs: **notation** (what a part looks like), **teaching** (how it is transmitted,
  in the tradition's own method), **input** (which zone to strike). No legend, no translation step —
  which is why the screen drum is a small design.
- **G4/D54 — voice before drum.** Every room entered the same way: **(1) voice alone** — the part as a
  sentence before it is a sound; **(2) voice over the battery** — the landing moment, sentence and
  sound become one thing; **(3) battery**. **Free to build:** with solfejo recorded locked to the
  battery (R63), all three states are **render-time muting of material already in the can**.
- **The echo loop (D74) — call-and-response as the in-room event.** Oral pedagogy runs on an echo
  shape. Rendered: **voice together → voice withdraws → you alone (battery continues) → voice returns
  → you hear whether you held.** The **battery is never artificially perturbed**; the *teaching voice*
  receding is the method itself, not a mechanic. Nearly free. Conditions: **INPUT-78** — a
  minute-by-minute transcription of a real Junior lesson, because the proven classroom is the loop's
  specification and was never asked for; **INPUT-79** — his form assent that rendered withdrawal is his
  teaching, not a trick played on it.
- **Tap-along (G5/D55)** — the door mechanic: vocalize and tap together. **The app measures the tap and
  never the voice.** It is **the door, not the session** — the bus, the first ninety seconds, before
  you own sticks; nobody taps and drums at once.
- **Why no microphone (D26, absolute).** **No measurement of the voice, ever, in any mode** — it stays
  unmeasured even if a mic ever ships. "The one part of the practice that is between the student and
  the tradition." It also keeps the governance line clean: a tap is a screen fact, not a musical
  verdict.
- **INPUT-68 (Junior, pedagogy):** what the hand does while the mouth does the part — **unison** (tap
  what you voice; day-one), **pulse** (polyrhythmic independence; arguably the real drummer's skill),
  **reference** (tap the agogô). PM-rec: unison first.
- **Costs accepted, not overlooked:** nothing to print, nothing to study off-app, nothing to check
  against a second source, and competitors will have tabs; no visual notation means nothing for a deaf
  user; subtitling gains are bounded — syllables cross languages, Junior *explaining* in Portuguese
  does not. **Moat:** anyone can tab a toque in an afternoon; this notation is inseparable from
  recordings of one specific man.
- **Partition tier activated.** The sacred partition's second value — *gamifiable
  (recognition/vocalization only)* — had been dead weight. Vocalization, tap-along and the screen drum
  are all recognition-and-vocalization forms and do **not** seat a student in an ensemble role inside a
  recorded liturgical battery. Material Junior would never mark *playable-inside* can now be marked
  gamifiable **using a form the partition itself sanctions**.
- **INPUT-67 reframed, not closed:** the app fixes **Junior's syllable set as the reference dialect**
  for his material, inside a frame letting other masters carry their own — how living standards for
  oral material work, and how red line #1 scales without imposing one master's syllables on another's
  tradition.

---

## 3 · The fork board, resolved

| Fork | Resolution |
|---|---|
| **A** advancing the student | **CLOSED (G1/D52).** The app **opens** rooms, never **moves** anyone. Doors open on behavioural facts (time, cycles, sessions, days) or on holding the solfejo at the door. **Neither is required** — any room walkable any time, both directions. The app never asserts readiness, only that a door is open, so there is no claim for the student's ear to contradict |
| **B** where the first session ends | **CLOSED (G13/D63/E20):** the whole sequence, simplest setting. *Rejected option 1* (session ends at the door) arguably breached FF3 for someone who already owns sticks |
| **C** breaks/turnarounds at M0 | Briefly **the game's existence condition** — with dropouts out, breaks were the only additive in-room event. **CLOSED for R1 (G24, MASTER-CONFIRMED):** not every rhythm has one; introducing them now is difficult. Deferred, not absent from the tradition. ~12 passes that would have doubled Junior's day leave M0; **R88** spends the freed capacity on 2–3 commons rhythms |
| **D** celebration / count-in wear | **CLOSED (D80)** — see §4.3 |
| **E** where the screen drum sits, free or not | Zone half closed (G14/D65); **free half derived, not ruled** — and permanent once shipped |
| **F** sharing and export | **CLOSED for R1 (G18/D69).** A video of someone playing along carries Junior's audio where **red line #6 cannot reach it** — "a takedown that stops at the CDN is not honoured by a platform that never heard of us." INPUT-71 open, non-urgent; **R78 keeps it in the counsel brief anyway** — one brief is cheaper than two |
| **G** comparison between students | **CLOSED for R1 (G17):** "not yet, maybe never." G9 had already removed the mechanism — under a binary window no comparable number exists. Ruling and evidence agree |
| **H** free-tier engagement mechanics | **CLOSED for R1 (G15/D66):** none, deferred. **Red line #5 makes anything given free permanent, including mechanics** — give nothing now and add later is available; the reverse is not. Mandate 01's INPUT-66 recommended the opposite and **was withdrawn as the worse answer** |
| **I** does the app ever listen | DEFERRED to Release 2 |
| **J** does the app remove support | **DEFERRED (G12/D62)** — **the criterion outvalues the answer:** support is removed **only where the music itself calls for it**, a property of the material, never a game mechanic. *All three options offered were rejected as a class* because each treated the dropout as *ours* to add, demote or test; the answer moved it out of the design space — the same logic that put the reference pulse on a tradition instrument rather than a metronome. A musically-native dropout is still a red-line-#1 form call, said in words |
| **K** day-7 return | Opened *because* comparison, sharing and free-tier engagement were switched off in one session. **ANSWERED contingent on INPUT-82 (D81):** count-in opens the day, the repertoire arc pulls across the week, the monthly appointment pulls across the month |
| **L** (new) | **Does D79's visible sustain survive contact with students?** OPEN, instrumented; a two-way door — the underlying facts are collected either way |

---

## 4 · Grading the game (Addendum 04)

### 4.1 The distinction that unlocked it

Four things had been collapsed into one banned category: **measurement** (a strike occurred at time *t*
in zone *z* — a fact); **feedback** (what it meant musically — information); **grading** (how this
*round* went); **classification** (what this *student is*). Only the fourth is dangerous and only the
fourth is charter-forbidden. **A game grades the run, never the player.** The estate feared
classification, deleted grading, and with grading went legibility, and with legibility went the game.

Two more assumptions overturned. **"Precision is the quantity to grade"** — false here; G9's arguments
are right *against precision readouts* and were overextended to all post-round visibility. What a
battery cares about is **presence** — are you with us, and for how long. **"Silence protects the
student"** — false; silence produced **risk #25, the competence illusion** (under scheduled audio the
part sounds right whether or not the hand is). The protective move is information **in the audible
channel**. *A real battery never issues a sentence about you, and it never lets you not know.*

### 4.2 The grading constitution (D76)

> **Facts may drive sound; nothing may drive a sentence.**
> **Sustain is visible, precision is audible, judgment is human.**
> **The game grades the round; the ear grades the playing; the master grades the player.**

The app may operate mechanically on facts and render musical consequences. It may never express an
evaluation in words, numbers, meters, tiers, stars, letters or percentages about the quality of
playing, and never anything at all about the player.

### 4.3 Four feedback levels

**L1 — during play: entirely audible, plus one honest light.** D77 + D78 (§1.5). **E21 — the presence
lamp:** E2 already lights the named musicians as each joins; **the student's own slot glows the same
way while their part is fed and dims as it fades** — a one-to-one visual mirror of the audio, **no
numbers**. The student joins the named musicians on screen: the product's promise made visible.

**L2 — after the round (D79; separately RATIFIED 2026-08-03)**, only after the musical ending (E9's
quiet count):
- **Three facts of the run:** (1) **cycles the battery played with you**; (2) **longest unbroken
  hold**; (3) **the setting** (part, drums present, tempo, mode). A **fed cycle** = a generous
  proportion of the part's strikes landed in the generous window — **cycle granularity, never
  milliseconds** (R83).
- **One personal best: longest hold at this setting.** **Self-referenced** (you vs your own yesterday),
  **monotonic** (only ever rises), **per-setting** (a best at more exposure is a different best).
- **R84 — monotonic display rule:** no screen ever says "below your best." Short of it, only the
  neutral facts; equal or beyond, the best updates and the room celebrates. *A number that only rises
  cannot humiliate.* **R85:** at most three facts plus the best.
- **Exact scope of the G9 amendment:** per-strike stays binary, generous, audible-only; what becomes
  visible is a **post-round aggregate of those binaries**. Accuracy readouts stay barred everywhere.
  G9's device-fairness argument does not reach cycle-granular sustain through a generous window; its
  FF3 argument is answered by self-reference plus monotonic display; its surface argument by the
  sentence ban.

**L3 — across rounds: the map lights, never dims** (D75 + R65). Rooms visited, rhythms met, parts
carried, bests — all monotonic; play ledger resettable, Caderno separate. **R86 — the vocabulary
rule:** play-layer words are spatial and musical (*rooms, visits, holds, bests*), never the Caderno's —
no "received," "confirmed," "mastered," "level," "rank," "graduate." **The wording is where
classification leaks back in, so the wording is specified.**

**L4 — the only place a person is assessed:** the master, monthly, by name.

**D80 — the celebration object is the new personal best**, carried by non-vocal sound design and the
room's light; Junior's voice variants stay reserved for **firsts and returns**. The slot was empty
because **G16 moved the count-in to every session start — "a thing that happens every time is not a
reward, it is furniture"** — and Mandate 01 §4.4 bars a synthetic substitute (hence **R79: 10–12
count-in variants including a return-after-absence one; at every start, three is a jingle in a
fortnight**).

### 4.4 Frustration audit

Fail states — none. Forced repetition — none (E8 free switching both ways; R58: fewer drums is
exposure, more drums is shelter, moving down is a move). Difficulty walls — none. Negative feedback —
none in sentences. Comparison — none. Loss — nothing ever taken (no hearts, no decay, monotonic
records). **Illegibility — the one frustration the old design created** — answered by the echo reveal,
the honest drum, the visible hold. Boredom — echo loop plus repertoire arc.
**Still barred:** accuracy percentages, stars, letters, tiers, perfect/good/miss, fail screens, streaks
with loss, person-levels, readiness/mastery claims, public rank, comparison, purchasable repair,
synthetic voice, any game result touching the Caderno, any measurement of the voice.

### 4.5 Refactor plan

- **D75 — the repertoire arc:** under G23/G25 the map stops being one rhythm's difficulty grid and
  becomes **the city** — Ijexá, afoxé, samba de roda, samba-reggae — each a room, entered voice-first,
  carrying its own bests; day-7 return gets a genuinely new room.
- **D73 — the commons is free; scarcity is priced.** Free: **commons rhythms performed by Junior** plus
  the full on-ramp (voice, tap, screen drum, echo loop), permanent under #5 — safe, because they were
  never scarce. Paid: depth, rarer authorised rhythms, this battery's rooms, the human layer. **This
  reverses the earlier "a free screen drum is value leakage" critique** — under G22 the free instrument
  is the standard's distribution vehicle; giving it away is the strategy, not the leak.
- **D81 — the cycle enters R1 as operations, not build:** a **monthly live event** (streamed; Salvador
  when possible) where Junior responds **by name**; the app carries only appointment, calendar, replay,
  Caderno entry. Submission runs outside the app, keeping **D26 intact**. Strains the one-obligation
  rule; go/no-go is INPUT-82.
- **D82 — publish the frame, never the corpus:** the syllable system's structure as a public standard;
  recordings, stems and renders remain the priced scarcity.
- **D83 — estate restructure:** two-page Charter (red lines, partition, consent-and-credit, grading
  constitution, vocabulary rule) split from a working backlog; **one-way/two-way door labels** (only
  one-way doors get formal treatment: consent scope, anything given free, the reference dialect,
  publication, anything shot at M0); a **monthly decision hour** — no input ages past 30 days.
- **D71 — new label MASTER-CONFIRMED**, above FOUNDER-FACT for tradition claims.
- **Session shape:** count-in → voice together → echo reveal → student's chosen branch → second reveal
  or clean full-battery close → quiet count, three facts, best if beaten → invitation including the
  cycle. Battery Detective survives as an optional 30-second prelude, not the spine.

---

## 5 · ID index

**Game decisions.** G1 app opens rooms, never moves. G2 vocalization replaces notation. G3 solfejo
encodes stroke as well as rhythm. G4 voice before drum. G5 tap-along is the door. G6 the screen drum.
G7 solfejo + sample library join M0. G8 engagement designed against research, not taste. G9 binary
generous window, no readout. G10 scheduled, not triggered. G11 vocalization is the founding idea. G12
no app-fired dropout. G13 first session runs everything, simplest setting. G14 three strokes hand / two
stick. G15 no free-tier engagement mechanics. G16 count-in at every start. G17 no comparison. G18 no
share/export. G19 D57/D58 decided, not proposed. G20 vocalization is this tradition's method. G21 the
app remains the direction; teaching assumptions proven by real students. G22 the notation is published
openly as a standard; Opanijé is a music-education company. G23 Junior records any Bahian rhythm he is
authorised to teach. G24 breaks deferred. G25 commons rhythms are free. G26 drum-viewed-from-above is
acceptable.

**Deltas.** D52–D58 are the written form of G1–G7 (D52 Fork A closed; D53 no Western notation; D54
voice→battery entry; D55 tap-along ships; D56 screen drum, zones named by syllables; D57 solfejo to M0
locked to the battery; D58 stroke sample library to M0). D59 binary timing, calibration out. D60
scheduled audio, native engine off the critical path. D61/D63/D65/D66/D67/D68/D69 are the written form
of G19/G13/G14/G15/G16/G17/G18. D62 no app-fired dropout (G12). D64 R70 revised — screen drum inside
the first session. D70 rough recording cut 6 takes → 4. D71 MASTER-CONFIRMED label. D72 Fork C closed.
D73 commons free / scarcity priced. D74 echo loop. D75 repertoire arc. D76 grading constitution. D77
the drum always sounds. D78 fade when unfed, no fail state. D79 post-round facts + personal bests
visible (RATIFIED). D80 celebration = new personal best. D81 monthly cycle in R1 as ops. D82
standard-publication workstream. D83 estate restructure. *Earlier, referenced:* D26 no microphone; D36
mockup before shoot; D37 R1 ships commerce; D38 Junior plays every drum layered, voiding E2; D50
per-mechanic instrumentation; D51 advance on behavioural facts.

**Recommendations.** R63 record solfejo locked to the battery, never standalone — locked→standalone is
free, the reverse impossible. R64 partition capture with the vocalization tier live. R65 the map **is**
the state space, lit — one object. R66 streak repair is musical, never purchasable. R67 implementation
intention at onboarding (d = 0.65, largest well-supported effect in the base, one screen). R68 reward
vocabulary = Junior's real voice plus non-vocal sound design only (Deci 1999: tangible
performance-contingent rewards undermine intrinsic motivation d ≈ −0.28…−0.40; positive verbal feedback
enhances it d ≈ +0.33). R69 no share/export until INPUT-71. R70 screen drum behind the door —
**revised by D64**. R71 instrument the streak/game discriminator (rounds after the streak ticks,
replays, notification-decliners as a free quasi-control): **a streak is satisfied by the minimum
session; the game is not**. R72 count-in variant bank. R73 grid from the render. R74 one surface, zone
count as the dial. R75 log both latency flags. R76 the rough prototype recording — 4 takes (reference
alone; one part over reference; break/turnaround; solfejo), **Junior performs and judges it in the same
act**. R77 take 5 first. R78 keep INPUT-71 in the brief. R79 shoot 10–12 count-ins. R80 keep D58
despite C22. R81 label M1 in advance as a no-engagement-layer baseline (amended: R1 *does* have a core
game and an appointment). R82 confirm the tempo relay first-hand pre-shoot — the whole three-step ladder
rests on a second-hand statement and every pass is locked to it. R83 sustain at cycle granularity. R84
monotonic display. R85 three facts + best. R86 the vocabulary sheet. R87 extend the usability pilot to
nine questions — *is the hold count invitation or pressure? does the fade read as information or
punishment?* R88 spend freed break capacity on 2–3 commons rhythms at on-ramp depth.

**Inputs.** 21 partition capture (widened). 36 vocalization as the tradition's method (**closed**, G20).
57 will Junior play every part himself. 58 do these toques carry breaks (**answered**, G24). 59 tempo
steps (provisional, pre-shoot). 62 form assent on the engagement layer (urgency fell). 64 comparison
(**answered for R1**). 66 free-tier mechanics (**answered**, G15). 67 the reference dialect. 68
hand-vs-mouth pedagogy. 69 form assent on the screen drum — small under G26 but it gates the **free
first session**. 70 sampling permissions. 71 sharing/export. 72 who may hear the rough prototype audio
(blocks the pilot). 73 celebration object (**answered**, D80). 74 count-in variant count. 75 "one track"
= one part at a time. 76 does the sample library stay in the shoot. 77 stroke vocabulary per instrument.
78 classroom transcription. 79 form assent on the rendered echo. 80 the commons list. 81 vocabulary
sheet. 82 the cycle's go/no-go, format, channel, price. 83 publication scope and trademark effect.
**84 — confirm that G15 bars the *extrinsic toolkit*, not the game's own legibility (round facts, bests,
the lit map); this one interprets a founder ruling and is unconfirmed.**

**Ledger (HYPOTHESIS unless noted).** 40 vocalization carries rhythm+stroke (FOUNDER-FACT). 41 the tap
door lifts first-session completion. 42 the screen drum retains without displacing the real drum. 43 the
engagement layer survives ~4-week novelty decay (measure D30, not only D7). 44 a generous binary window
is device-tolerant enough that calibration is unnecessary. 45 scheduled audio reads as playing, not
miming. 46 a beginner can go voice → screen drum in one sitting. 47 these toques carry breaks (resolved
by G24). 48 the echo loop reads as teaching, not testing. 49 visible sustain and bests increase
voluntary replay without pressure or guilt. 50 the fade reads as information, not punishment. 51
commons-free/scarcity-priced converts.

**Risks.** #23 the screen displaces the drum (re-rated up by D64, no new number). #24 a master's
material beyond takedown reach. #25 the competence illusion. #26 M1 measures a product the engagement
layer was never switched on in. #27 sustain becomes a proxy score. #28 the standard outruns the corpus.
#29 the monthly cycle strains the one-obligation rule. **Contradictions:** C21 (D57/D58 decided or
proposed — closed by G19); C22 (D58's justification — resolved by D77).

**Rejected outright.** Randomised A/B at Release 1 — R1 ships once, and ≈291 users/arm are needed for a
ten-point D7 difference (≈2 500 for five points) while splitting the cohort halves precision on both
headline numbers. Peak–end as a return device, the rolling weekly pulse, and prerecorded-master
relatedness — over-claims demoted. The "no-app-first" and "sketch-shoot-first" refactor proposals —
withdrawn under G21/G24. Portrait stills of a full battery (Junior plays every drum himself, layered —
which voids E2's named-musicians screen and is why the presence lamp had to be invented). **Release 1
carries no relatedness mechanism either research base endorses** (Hove & Risen 2009: affiliation effects
were unique to *interpersonal* synchrony) — which is why D81 pulls the human cycle forward.
