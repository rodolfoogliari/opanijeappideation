# Opanijé — The Game — assembled specification

**Status.** Register of record for this series as of 2026-08-03, under D83 (Addendum 04 §7).
**Supersedes.** The per-session tables in `sessions/` for this series, which remain readable as
derivation history but are no longer the register.
**Range.** game specification.
**Rule.** Rows are appended, never rewritten. A row's status may change; its claim may not.

---

**What this file is.** The single statement of what the game *is* after Game Addendum 04. Until
2026-08-03 the game existed only as four addenda written on four days, each amending the last; a
builder had to read all four and reconcile them. This file reconciles them once. Its spine is
Addendum 04 §§3–4; its limbs are Addendum 01 §§4–6 (vocalization as notation, the door, the screen
drum), Addendum 02 §§2–5 (the screen drum's architecture, why binary, the error channel), Addendum
03 §§4, 7, 9 (Fork B closed, the count-in, the stroke set) and the Experience Spec §2 (the
student's path end to end).

**What this file is not.** It invents nothing. Every mechanic below traces to a numbered decision,
delta or recommendation, and every row carries its source. Where the estate has not decided
something, this file says so and names the open item rather than filling the gap. Where two
documents disagree, §12 records the disagreement instead of resolving it silently.

**Authority.** Where this file and `CHARTER.md` disagree, the Charter governs (Charter §11). Where
this file and any session document disagree, the later document governs, and Game Addendum 04
(2026-08-03) is the plan of record for anything it touches.

**Epistemic labels** are carried verbatim from the issuing document. Nothing is upgraded.

**Door labels** (D83 item 2). ONE-WAY — expensive or impossible to reverse: consent scope, anything
given to the free tier (red line #5 makes it permanent), the fixed reference dialect, publication of
the standard, and anything shot at M0 (the shoot is the irrecoverability deadline that governs all
sequencing). TWO-WAY — revisable on evidence. Labels are taken from the estate's own reasoning where
it states one; otherwise marked "(derived)". Closed and ratified items carry "—".

---

## 1 · The grading constitution (D76)

**D76, ADOPTED 2026-08-03.** One principle replaces the patchwork of per-surface rules, G9
carve-outs and Mandate 01 §10 items that governed evaluation before it.

> **Facts may drive sound; nothing may drive a sentence.**
> **Sustain is visible, precision is audible, judgment is human.**
> **The game grades the round; the ear grades the playing; the master grades the player.**

**What the app may do.** Operate mechanically on facts, and render musical consequences from them.
A strike at time *t* in zone *z* is a fact; the app may schedule audio on it, sustain a part on it,
fade a part for want of it, light a lamp with it, count it after the round, and compare it to the
same student's own earlier count.

**What the app may not do.** Express an evaluation in words, numbers, meters, tiers, stars, letters
or percentages about the quality of playing — and say anything at all about the player. (Addendum
04 §3.2; Charter §6.)

**The four things the estate had collapsed into one banned category.** Keeping them apart is what
made a game possible without touching the charter.

| # | Thing | What it is | Permitted | Source |
|---|---|---|---|---|
| 1.1 | Measurement | A strike occurred at time *t* in zone *z* — a fact | Yes | Addendum 04 §3.1; Charter §6 |
| 1.2 | Feedback | What that meant, musically — information | Yes, in the audible channel | Addendum 04 §3.1; Charter §6 |
| 1.3 | Grading | How this round went — a summary of play | Yes, post-round, self-referenced (D79) | Addendum 04 §3.1, §3.3; Charter §6 |
| 1.4 | Classification | What this student *is* — a claim about a person | **Never** — machine claims of readiness, correctness, mastery or standing | Addendum 04 §3.1; Charter §6 |

**The three assumptions the refactor found overextended**, recorded because the reasoning has to
survive the decision.

| # | Assumption | Finding | Source |
|---|---|---|---|
| 1.5 | "Any visible measure of play is a verdict on musicianship" | False by conflation — only classification is dangerous, and a game grades the run, never the player. Deleting grading deleted legibility, and with legibility went the game | Addendum 04 §3.1 |
| 1.6 | "Precision is the quantity to grade" | False for this instrument. G9's three arguments are correct against *precision readouts*, and were overextended to all post-round visibility. The musical quantity a battery cares about is **presence** — are you with us, and for how long | Addendum 04 §3.1 |
| 1.7 | "Silence protects the student" | False; silence produced risk #25, the competence illusion. The protective move is information in the **audible channel**, where a real drum delivers it | Addendum 04 §3.1 |

**The architecture in one sentence**, from the session that built the instrument and still exact:

> **Your finger keeps his groove alive; the drum tells you where you are; the app never says.**

(Addendum 02 §2. Clause 1 is G10; clause 2 is the tradition's own method and R15's reference pulse;
clause 3 is Mandate 01 §3, whose own one-line form — *the app never grades your drumming; it may
celebrate everything else* — survives D76 unchanged.)

---

## 2 · The four feedback levels

Four levels, in order of the timescale they run on. Nothing crosses between them: what is audible
mid-play is never written on a screen mid-play, and what is written after the round is never a
sentence about the player.

### 2.1 · Level 1 — during play: entirely audible, plus one honest light

| # | Event | What happens | Status | Source |
|---|---|---|---|---|
| 2.1.1 | Strike inside the generous window | Junior's correct part stays alive — scheduled render, not a per-strike trigger. G10 unchanged | ADOPTED (D77) | Addendum 04 §3.3; Addendum 02 §1 (G10) |
| 2.1.2 | Strike outside the window | A one-shot of the **real stroke** fires — the student's actual hit, audible, off the groove — because a real drum struck off-time still sounds | ADOPTED (D77) | Addendum 04 §3.3 |
| 2.1.3 | Strike in the wrong zone | Likewise: an audibly wrong stroke at the right time. Already designed before D77 | ADOPTED (D77); channel from Addendum 02 §5 | Addendum 04 §3.3; Addendum 02 §5 |
| 2.1.4 | The part goes unfed | It **fades** — thins, does not stop. The battery never stops for you | ADOPTED (D78) | Addendum 04 §3.3 |
| 2.1.5 | The part is fed again | It **returns**. You cannot lose; you can only be more or less present in the music | ADOPTED (D78) | Addendum 04 §3.3; Charter §6 |
| 2.1.6 | Fail state | **None exists anywhere in the product** | ADOPTED (D78) | Addendum 04 §3.3, §3.4; Charter §6 |
| 2.1.7 | The presence lamp | The student's own slot glows while their part is fed and dims as it fades — a one-to-one visual mirror of the audio, no numbers. E2 already lights the named musicians as each joins; the student joins them on screen | **PM-RECOMMENDED (E21)** — the one open item at this level | Addendum 04 §3.3 |
| 2.1.8 | Everything else on screen | Nothing else appears mid-play. E3 stands: propped phone, arm's length, no menus | FOUNDER-DECIDED (E3); restated ADOPTED (R85) | Addendum 04 §3.3, §12 (R85); Experience Spec §1 (E3) |
| 2.1.9 | The voice | **Never measured, in any mode.** Unchanged, absolute — structurally true today under D26 (no microphone) and it stays true if a microphone ever ships | RULED, charter-level | Addendum 04 §3.3; Charter §9 item 8 |

**Why the error channel is the right one.** Under G3 the syllable names the sound and under G6 the
syllable names the zone, so striking the slap zone where the part wants bass produces an audibly
wrong stroke at the right time. The student hears **stroke** errors and never hears **timing**
errors — that is the clean split, and it is why D58's stroke sample library is not merely what makes
the screen audible but the entire feedback system (Addendum 02 §5). D77 restates that justification
on solid ground and resolves C22: the sample library exists so the drum is honest (Addendum 04 §3.3,
§8).

**Why latency is tolerable here.** An off-grid hit has no exact reference to smear against, so a
one-shot fired late is not a false readout (Addendum 04 §3.3). Scheduled audio is buffered ahead and
is immune to output latency; the native low-latency audio engine is off Release 1's critical path
(Addendum 02 §4, DERIVED).

**One build question the estate has not decided.** Whether a wrong-zone strike sounds *instead of*
the correct part or *on top of* it — a design question with a real pedagogical difference, recorded
as PM-ASSERTION and explicitly not decided (Addendum 02 §5). Open; see §9.

### 2.2 · Level 2 — after the round: the game grades the round (D79, RATIFIED 2026-08-03, RULED)

Shown only after the musical ending — E9's quiet count, upgraded (Addendum 04 §3.3).

| # | Element | Specification | Status | Source |
|---|---|---|---|---|
| 2.2.1 | Fact 1 | **Cycles the battery played with you** | RATIFIED (D79) | Addendum 04 §3.3, §10 |
| 2.2.2 | Fact 2 | **Longest unbroken hold** | RATIFIED (D79) | Addendum 04 §3.3, §10 |
| 2.2.3 | Fact 3 | **The setting** — part, drums present, tempo, mode | RATIFIED (D79) | Addendum 04 §3.3 |
| 2.2.4 | What a fed cycle is | A cycle where a generous proportion of the part's strikes landed in the generous window — **cycle granularity, never milliseconds**; the proportion is tuned in the pilot and never displayed per strike | ADOPTED with D79 (R83) | Addendum 04 §3.3, §12 (R83) |
| 2.2.5 | The one personal best | **Longest hold at this setting** — self-referenced (the student against their own yesterday), monotonic (it only ever goes up), per-setting (a best at more exposure is a different best) | RATIFIED (D79) | Addendum 04 §3.3 |
| 2.2.6 | The celebration object | The **new personal best**, carried by non-vocal sound design and the room's light. INPUT-73 answered; Fork D closed | ADOPTED (D80) | Addendum 04 §3.3, §10, §15 |
| 2.2.7 | Junior's voice variants | Reserved for **firsts and returns** — first entry, first rhythm finished, return after absence (R66's repair asset). Not spent on the personal best | ADOPTED (D80) | Addendum 04 §3.3; Addendum 01 §14 (R66) |
| 2.2.8 | The count-in | Remains the **opening** ritual, fired at every session start; G16 untouched by D80 | FOUNDER-DECIDED (G16) | Addendum 04 §3.3; Addendum 03 §7 |
| 2.2.9 | The monotonic display rule | The screen **never says "below your best."** Short of the best, only the neutral facts show. Equal or beyond, the best updates and the room celebrates. A number that only ever rises cannot humiliate | ADOPTED with D79 (R84) | Addendum 04 §3.3, §12 (R84) |
| 2.2.10 | The size of the screen | At most **three facts plus the best**; nothing evaluative mid-play beyond the presence lamp | ADOPTED (R85) | Addendum 04 §12 |

**What the amendment to G9 is, exactly.** Per-strike feedback remains binary, generous and
audible-only. What changes is that a **post-round aggregate of those binaries** — sustain — becomes
visible. Accuracy-style readouts remain barred on every surface. G9's device-fairness argument does
not reach cycle-granular sustain through a generous window; its FF3 argument is answered by
self-reference and monotonic display; its surface argument is answered by the sentence ban. This is
the one place the plan amends a founder ruling's scope; it was put to the founder separately and
**ratified 2026-08-03 (RULED)** (Addendum 04 §3.3, §10; Charter §9 item 11).

### 2.3 · Level 3 — across rounds: the map lights, never dims (D75 + R65 carried)

| # | Element | Specification | Status | Source |
|---|---|---|---|---|
| 2.3.1 | What the map records | Rooms visited, rhythms met, parts carried, personal bests. **All monotonic** | ADOPTED (D75) | Addendum 04 §3.3, §4.2, §10 |
| 2.3.2 | The map's form | The map **is** the state space, lit — one object, not a progress display beside a difficulty grid | R65 carried | Addendum 04 §3.3, §4.2; Addendum 01 §14 |
| 2.3.3 | The play ledger | Stays **resettable by design**. The two-ledger architecture was built for exactly this and is finally load-bearing; the play layer never writes into the Caderno's tables | Architecture, charter-level | Addendum 04 §3.3; Charter §4 |
| 2.3.4 | How doors open | **On facts.** D52 untouched: the app opens, never promotes, never asserts readiness | D52 | Addendum 04 §3.3; Addendum 01 §3 |
| 2.3.5 | The vocabulary rule | Play-layer words are **spatial and musical** — rooms, visits, holds, bests — and never borrow the Caderno's. No "received," "confirmed," "mastered," "level," "rank," "graduate." The wording is where classification would leak back in, so the wording is specified | R86, Strong; sheet at `METHOD.md` §5; approval at INPUT-81 | Addendum 04 §3.3, §12; Charter §7 |

**The sentence test**, from the vocabulary sheet: if a string can be read as a statement *about the
student* rather than *about the round*, it is wrong, however friendly it sounds (`METHOD.md` §5).

### 2.4 · Level 4 — the master, monthly, by name

The **only** place a person is ever assessed. Layer 2, unchanged, human, capped by Junior's hours,
and pulled into Release 1 operationally as a monthly live event where he responds by name (D81,
contingent on INPUT-82). The game deliberately points at it: the ending's invitation (E7/E10) now
includes the cycle. The app carries only the appointment, the calendar, the replay and the Caderno
entry; submission runs over ordinary channels outside the app, keeping D26 (no microphone) fully
intact. (Addendum 04 §3.3, §5.)

---

## 3 · The micro-game: the echo loop (D74, ADOPTED; form assent INPUT-79)

The in-room event Release 1 lost — dropouts out under G12, breaks deferred under G24 — returns
through the **voice channel**, which G12 never touched. Oral pedagogy runs on an echo shape: the
teacher voices the part; the student joins; the teacher's voice withdraws as the student holds it;
teacher and student land together.

Rendered, exactly as Addendum 04 §4.1 states it:

> **voice together → voice withdraws → you alone (battery continues) → voice returns → you hear
> whether you held.**

| # | Property | Specification | Source |
|---|---|---|---|
| 3.1 | The battery is never perturbed | It continues throughout. The teaching voice receding is **not a game mechanic but the method itself** — which G20 has confirmed is the tradition's | Addendum 04 §4.1; §1 (G20) |
| 3.2 | How every state is produced | **Render-time muting on solfejo recorded locked to the battery (R63)** — no new capture, no audio engine, no per-state performance. This is why the loop is nearly free to build | Addendum 04 §4.1, §8; Addendum 01 §9.1 |
| 3.3 | The material it runs on | Eight solfejo passes, locked, decided (D57, G19) — every part, slow and normal. Locked can be soloed later; standalone can never be locked afterwards | Addendum 01 §9.1 (R63); Addendum 03 §6.3 (G19); Addendum 04 §8 |
| 3.4 | Blocking condition 1 | **INPUT-78** — the classroom transcription: how a real lesson with Junior actually runs, minute by minute. The proven classroom (G21) is the loop's specification and the estate has never asked for it. **Ask first** | Addendum 04 §4.1, §9, §11 |
| 3.5 | Blocking condition 2 | **INPUT-79** — Junior's form assent that the rendered withdrawal is his teaching and not a trick played on it. Answered by seeing the mockup, not by description | Addendum 04 §4.1, §9 |
| 3.6 | Where it is tested | Ledger row 48 — *the echo loop is experienced as teaching, not testing* — HYPOTHESIS, converts at the pilot (R87) then M1 | Addendum 04 §13 |

**It answers the illegibility frustration.** The reveal is the moment the student learns whether they
held — the information the old silent design withheld (Addendum 04 §3.4).

---

## 4 · The macro-game: the repertoire arc (D75, ADOPTED)

The map stops being a difficulty grid for one rhythm and becomes **the city**.

| # | Property | Specification | Source |
|---|---|---|---|
| 4.1 | What a room is | A rhythm: Ijexá, afoxé, samba de roda, samba-reggae, the toques Junior is authorised to teach — each a room, each entered voice-first, each carrying its own personal bests | Addendum 04 §4.2 |
| 4.2 | Why the catalog is wide | **G23** — Junior records any Bahian rhythm he is authorised to teach, Candomblé and popular (MASTER-CONFIRMED) | Addendum 04 §1, §4.2 |
| 4.3 | Which rooms are free | **G25** — rhythms already readily available online are free; the commons is free, scarcity is priced (D73). The free commons rooms are simultaneously the standard's teaching corpus (D82) | Addendum 04 §1, §4.2, §5, §6 |
| 4.4 | What progress is | **Rhythms met and carried further** — never a completion fraction, never a person-level | Addendum 04 §4.2; `METHOD.md` §5 |
| 4.5 | What it answers | Day-7 return gets a next room that is genuinely new; boredom is answered by the arc as illegibility is answered by the echo | Addendum 04 §3.4, §4.2 |
| 4.6 | The ladder's framing inside a room | Fewer drums is exposure, more drums is shelter; speed is separate; **moving down is a move**, not a retreat (R58). Parts switch freely in both directions at any time (E8) | Addendum 04 §3.4; Experience Spec §1 (E8); R1 Addendum S2 §10 (R58) |
| 4.7 | The room's name | The Room is unnamed — it is simply where you play (E18) | Experience Spec §1 |

---

## 5 · The session, end to end

Addendum 04 §4.3's sequence is the spine. The Experience Spec §2 supplies the surrounding path — the
first-ever session and every session after it. Both are given, because a builder needs both.

**5.1 · The spine (Addendum 04 §4.3).**

| # | Step | Detail | Source |
|---|---|---|---|
| 5.1.1 | Count-in | Junior's count-in fires at **every** session start. The master calls you in; the app opens the way the room opens | Addendum 04 §4.3; Addendum 03 §7 (G16) |
| 5.1.2 | Voice together | The syllables and the student, over the battery | Addendum 04 §4.3; Addendum 01 §5.1 (G4) |
| 5.1.3 | The echo reveal | §3 above — voice withdraws, the student holds, the voice returns | Addendum 04 §4.1, §4.3 |
| 5.1.4 | The student's chosen branch | More exposure, more drums, another tempo, another part — E8, in both directions, at any time | Addendum 04 §4.3; Experience Spec §1 |
| 5.1.5 | A second reveal, or a clean full-battery close | Either ending is musical | Addendum 04 §4.3 |
| 5.1.6 | The quiet count | Three facts, and the best if beaten (§2.2) | Addendum 04 §3.3, §4.3 |
| 5.1.7 | The invitation | E7/E10, **now including the cycle** — the master offers the next step, and the appointment with a human who might say your name | Addendum 04 §3.3, §4.3, §5 |
| 5.1.8 | Battery Detective | Survives as an **optional thirty-second prelude, not the spine** | Addendum 04 §4.3 |

**5.2 · The whole path, first session onward (Experience Spec §2, with the later rulings applied).**

| # | Moment | What happens | Source |
|---|---|---|---|
| 5.2.1 | Arrival | A presentation — what this is, whose it is, what happens here. Then Google sign-in. Nothing is audible before this point, so the presentation carries the whole conversion | Experience Spec §2; §1 (E4) |
| 5.2.2 | Welcome | Junior, recorded once, seconds not minutes. The single most-viewed asset in the estate | Experience Spec §2, §4 |
| 5.2.3 | Choosing | The student picks their part, preceded under E19 by one plain question about whether they have an instrument to hand. Whatever they pick is reversible at any moment, in either direction (E8) | Experience Spec §2; §6 (E19 open) |
| 5.2.4 | The call | The Primeira Chamada. The battery is there, the student's part is theirs | Experience Spec §2 |
| 5.2.5 | The whole instrument, day one | **G13/E20:** the first session runs voice → voice over the battery → battery → the tap door → the screen drum, all of it, at its simplest setting. "Advanced mode" is no longer advanced; it is the product | Addendum 03 §4 |
| 5.2.6 | Playing | The screen shows who is in the room — names and faces, present, not moving — plus the presence lamp (E21). The phone is propped; the hands are busy; nothing on screen asks for attention | Experience Spec §2; Addendum 04 §3.3 |
| 5.2.7 | Rising | A level change is a **clean break**: the cycle finishes, the master calls the next player in with a count-in, the battery resumes with the new part (E1). *The Experience Spec's "never when the app decides (D28/R51)" was withdrawn by D51 and narrowed by D52 — the app opens rooms, it never moves the student into one. See §12* | Experience Spec §1, §2; Mandate 01 §2, §9 (D51); Addendum 01 §3 (D52) |
| 5.2.8 | Closing | The quiet count, now specified as three facts plus the best (§2.2) | Experience Spec §2; Addendum 04 §3.3 |
| 5.2.9 | The first entry | After the first real practice the Caderno's card stops being empty. It says what happened, when, and who was in the room. **Earned by practice, never by answering the call** (E5) | Experience Spec §1, §2 |
| 5.2.10 | Being asked back | Only after that first entry does the app ask whether the student wants to be called back — in the master's framing, not the system's (E12, as revised by D45) | Experience Spec §1, §2; Mandate 01 §2 |
| 5.2.11 | Returning | Today's session at the top of the home screen; the rhythm and how far through it beneath; the Caderno card, now with something in it (E6) | Experience Spec §1, §2 |
| 5.2.12 | The ending | When the free rhythm is finished the master speaks again — not to sell, but to say what comes next. Domestic path or Salvador. **Neither recording names a price** (E7, E10, R53) | Experience Spec §2, §3 |
| 5.2.13 | Staying free | The student who never buys keeps the room exactly as it was, permanently, with nothing withdrawn, degraded or nagged (E13, red line #5) | Experience Spec §2, §3 |

**5.3 · The instrument the session is played on**, gathered so it is not read out of three files.

| # | Property | Specification | Source |
|---|---|---|---|
| 5.3.1 | Notation | **None.** No tablature, no staff, no rhythm grid, no piano-roll on any surface. Vocalization is how a part is written, shown, taught and referenced (G2) | Addendum 01 §4 |
| 5.3.2 | Why the syllable is the instruction | Junior's vocalization carries both rhythm **and** stroke (G3, FOUNDER-FACT). Say the bass syllable, strike the bass zone. No legend, no translation step | Addendum 01 §4, §6.1 |
| 5.3.3 | The door | Voice alone → voice over the battery → battery (G4). All three states are render-time muting on material already in the can | Addendum 01 §5.1 |
| 5.3.4 | Tap-along | The student vocalizes and taps together; the app measures the **tap** and never the voice. The door, not the session — what you do before you have an instrument, on the bus, in the first ninety seconds (G5, E3) | Addendum 01 §5.2 |
| 5.3.5 | What the hand does | Unison, pulse, or reference (the agogô) — three different skills. PM-RECOMMENDED unison first, independence as a later room; **pedagogy, so it is Junior's — INPUT-68** | Addendum 01 §5.3 |
| 5.3.6 | The screen drum | Phone flat, **landscape**, two hands; the screen is a drum head divided into zones; the student vocalizes and strikes the zone the syllable names (G6). It **may resemble a real drum viewed from above** (G26) | Addendum 01 §6.1; Addendum 04 §1 |
| 5.3.7 | The zone set | Three zones on hand instruments — slap, tone, bass; two on stick instruments — rim and skin (G14). That is the zone *count* and the zone *stroke*, **not the zone label**: what the student sees is Junior's syllable, never the English word (D56) | Addendum 03 §9 |
| 5.3.8 | One surface, not two | Zone count is the dial — one zone at the door, two, then three. Tap-along and the screen drum are the same instrument at different settings (R74). G14 fixes where the top of the dial is | Addendum 02 §12; Addendum 03 §9 |
| 5.3.9 | What it cannot encode | **How hard.** Touch velocity is unreliable across devices and must not be relied on — which keeps the screen drum a *transcription* device rather than a simulation of playing | Addendum 01 §6.2 |
| 5.3.10 | Audio architecture | **Scheduled, not triggered** (G10): the app plays Junior's correct part in time with the battery; the strike keeps it alive rather than firing each sample. Out-of-window and wrong-zone strikes are the exception, and they fire one-shots (D77) | Addendum 02 §1; Addendum 04 §3.3 |
| 5.3.11 | The timing window | **Binary and generous** (G9): inside it the stroke lands in the groove, outside it it does not. No tiers, no labels, no per-strike marks. Per-device calibration is out of Release 1 | Addendum 02 §1, §3, §4 |
| 5.3.12 | The gate on shipping it | **No screen-drum surface ships without Junior having seen it** (Mandate 01 §10 item 10, red line #1). Building it unshown is permitted and expected; shipping it unshown is not. Under G13 this now gates the free first session | Charter §9; Addendum 03 §4 |

---

## 6 · The frustration audit

Every known frustration source in rhythm-game design, checked against this architecture. All eight
items from Addendum 04 §3.4, each with the architectural answer rather than a promise of restraint.

| # | Frustration source | The architectural answer | Source |
|---|---|---|---|
| 6.1 | **Fail states** | None exist; **fade-and-rejoin replaces them** (D78). The battery never stops for you | Addendum 04 §3.4; §3.3 (D78) |
| 6.2 | **Forced repetition** | None; E8's free part-switching in both directions stands, with R58's framing — fewer drums is exposure, more drums is shelter, and moving down is a move | Addendum 04 §3.4; Experience Spec §1 (E8) |
| 6.3 | **Difficulty walls** | None; the student sets every axis, and the door's alternative (behavioural facts) opens rooms on presence alone | Addendum 04 §3.4 |
| 6.4 | **Negative feedback** | None in sentences; **error lives in sound**, where it informs without addressing the person (D77) | Addendum 04 §3.4; §3.3 |
| 6.5 | **Comparison** | None — G17 stands: no comparison between students, "not yet, maybe never" | Addendum 04 §3.4; Addendum 03 §6.1 |
| 6.6 | **Loss** | Nothing is ever taken — red lines #2 and #5; no hearts, no decay, monotonic records | Addendum 04 §3.4; Charter §2 |
| 6.7 | **Illegibility** | The one frustration the old design *created* — answered by the echo reveal (§3), the honest drum (§2.1), and the visible hold (§2.2) | Addendum 04 §3.4 |
| 6.8 | **Boredom** | Answered by the echo loop and the repertoire arc (§3, §4) | Addendum 04 §3.4 |

**The residual risk, named rather than assumed away.** Risk #27 — sustain becomes a proxy score, and
players chase the hold the way they would an accuracy number. Mitigation: nothing mid-play, monotonic
display, no comparison, resettable ledger, and ledger row 49's pressure-and-guilt items **measured
rather than assumed** (Addendum 04 §14, §13).

---

## 7 · What remains barred (§3.5, restated in full)

Unchanged, all of it. Nothing in this file relaxes any line below.

| # | Barred | Source |
|---|---|---|
| 7.1 | Accuracy percentages | Addendum 04 §3.5; Charter §9 item 11 |
| 7.2 | Stars | Addendum 04 §3.5 |
| 7.3 | Letters | Addendum 04 §3.5 |
| 7.4 | Tiers | Addendum 04 §3.5; Addendum 02 §1 (G9) |
| 7.5 | "Perfect/good/miss" labels | Addendum 04 §3.5; `METHOD.md` §5 |
| 7.6 | Fail screens | Addendum 04 §3.5; §3.3 (D78) |
| 7.7 | Streaks with loss | Addendum 04 §3.5 |
| 7.8 | Person-levels | Addendum 04 §3.5; §3.3 (R86) |
| 7.9 | Readiness or mastery claims | Addendum 04 §3.5; Charter §6 |
| 7.10 | Public rank | Addendum 04 §3.5; Addendum 03 §6.1 (G17) |
| 7.11 | Comparison between students | Addendum 04 §3.5; Addendum 03 §6.1 (G17) |
| 7.12 | Purchasable repair | Addendum 04 §3.5; Addendum 01 §14 (R66) |
| 7.13 | Synthetic voice | Addendum 04 §3.5; Charter §2 red line #4 |
| 7.14 | Any game result touching the Caderno | Addendum 04 §3.5; Charter §4 |
| 7.15 | Any measurement of the voice | Addendum 04 §3.5, §3.3; Charter §9 item 8 |

Also standing, from the consolidated prohibition list: anything purchasable that confers,
accelerates or implies standing; anything that gates access to what was given (hearts, lives,
energy, timers on the free room); badges, titles or ranks that read as a master's acknowledgment;
any recording of a master that names a price or a product; any gamified surface that survives a
withdrawal of the material it points at; no share or export until INPUT-71 is answered; no
screen-drum surface shipped without Junior having seen it (`CHARTER.md` §9).

**Everything not on the list is permitted.** Where a mechanic is arguable: build it, put it in the
mockup, and take it to Junior — not to the product manager (`CHARTER.md` §9).

---

## 8 · Why the amendment stays below the charter (§3.6)

| # | Point | Statement | Source |
|---|---|---|---|
| 8.1 | What D79 amends | **G9 — a founder design ruling, not a red line.** The scope amended is post-round visibility; per-strike feedback is untouched | Addendum 04 §3.6, §3.3 |
| 8.2 | Red line #2 is untouched | Standing is only earned. **Sustain confers nothing and writes nowhere** — it is not currency, it opens no Caderno entry, and the play layer never writes into the Caderno's tables | Addendum 04 §3.6; Charter §2, §4 |
| 8.3 | Mandate 01 §3 is honoured | "No machine verdict on musicianship" holds under §1's distinction: a round summary is a fact about play, framed against the player's own history, expressed without sentences about the person | Addendum 04 §3.6; Mandate 01 §3 |
| 8.4 | The procedure that was followed | D79 was flagged plainly as the one place the plan amends a founder ruling's scope, put to the founder **separately**, and ratified 2026-08-03 (RULED). It was not carried through inside a block of proposals | Addendum 04 §3.3, §10 |
| 8.5 | What is left genuinely open | Whether the distinction holds **in the student's experience** is an empirical question and is instrumented as such — ledger row 49, and the pilot questions at R87 | Addendum 04 §3.6, §13, §12 |
| 8.6 | The reversal path | Fork L: D79's visible sustain is ratified now and reversed **without cost** if row 49 fails, because the underlying facts are collected either way. That is what makes it a two-way door | Addendum 04 §15; `METHOD.md` §2 |

---

## 9 · What is open in this specification, with door labels

Every open item the game depends on. ONE-WAY items get the formal treatment — the three-option fork,
the written input, the founder's or Junior's signature.

| # | Open item | Owner | Door | Source |
|---|---|---|---|---|
| 9.1 | **INPUT-78** · the classroom transcription — the echo loop's specification. Ask first | Junior | ONE-WAY (derived — on the pre-shoot owed list; it shapes M0's echo-loop material). *`BACKLOG.md` §1 labels this two-way; see §12* | Addendum 04 §4.1, §8, §9, §11 |
| 9.2 | **INPUT-79** · form assent on the rendered echo | Junior | ONE-WAY (derived — red line #1 form assent on free-tier material). *`BACKLOG.md` §3.1 labels this two-way; see §12* | Addendum 04 §4.1, §8, §9 |
| 9.3 | **INPUT-69** · the mockup form assent on the screen drum, now small under G26 | Junior | ONE-WAY (derived — G13/E20 put the screen drum inside the free first session, which red line #5 makes permanent) | Addendum 04 §1, §8; Addendum 03 §4 |
| 9.4 | **INPUT-70** · which strokes and drums may be sampled in isolation under the partition | Junior | ONE-WAY — shot at M0 | Addendum 01 §9.2; Addendum 04 §8 |
| 9.5 | **INPUT-77** · which instruments take the three-zone hand vocabulary and which the two-zone stick vocabulary; whether the reference instrument needs one of its own | Founder names, Junior confirms against the solfejo | ONE-WAY — shot at M0 | Addendum 03 §9; Addendum 04 §8 |
| 9.6 | **INPUT-67 (reframed)** · Junior's syllable set fixed as the **reference dialect** | Junior | ONE-WAY — the fixed reference dialect; changing it after publication breaks everyone who adopted it | Addendum 04 §6; `METHOD.md` §2 |
| 9.7 | **INPUT-68** · unison, pulse or reference — what the hand does while the mouth does the part | Junior (pedagogy) | TWO-WAY (derived) | Addendum 01 §5.3 |
| 9.8 | **INPUT-74** · how many count-in variants are shot, and of what kinds. R79 recommends 10–12, including a return-after-absence variant | Founder | ONE-WAY — shot at M0; the wear is unrecoverable because a synthetic substitute is barred | Addendum 03 §7; Addendum 04 §8 |
| 9.9 | **INPUT-80** · the commons list — which rhythms are free. Junior confirms availability and teaching order | Founder | ONE-WAY — the free tier, red line #5 | Addendum 04 §5, §11 |
| 9.10 | **INPUT-81** · the vocabulary sheet approved (R86) | Founder | TWO-WAY (derived) | Addendum 04 §11, §12; `METHOD.md` §5 |
| 9.11 | **INPUT-82** · the cycle's go/no-go, format, submission channel and price — against the one-obligation rule, eyes open | Founder **and** Junior together | ONE-WAY in obligation — a standing monthly commitment; risk #29 | Addendum 04 §5, §11, §14 |
| 9.12 | **INPUT-84** · confirm that G15 bars the **extrinsic toolkit**, not the game's own legibility | Founder | ONE-WAY (derived — it governs what runs at the free door, which red line #5 makes permanent). *`BACKLOG.md` §1 labels this two-way; see §12* | Addendum 04 §2, §11 |
| 9.13 | **E21** · the presence lamp, still PM-RECOMMENDED and the only unratified element of Level 1 | Founder, at the mockup | TWO-WAY (derived) | Addendum 04 §3.3 |
| 9.14 | **E19's sub-fork** · whether the door asks about instrument ownership before routing | Founder | TWO-WAY (derived) | Experience Spec §1, §6 |
| 9.15 | **Wrong-zone rendering** · does a wrong-zone strike sound *instead of* the correct part or *on top of* it? Recorded as PM-ASSERTION, explicitly not decided | Build side, with Junior's ear | TWO-WAY (derived) | Addendum 02 §5 |
| 9.16 | **R82** · confirm the tempo ladder first-hand; the pedagogical half is MASTER-CONFIRMED, the specific ladder is still relayed | Founder → Junior | ONE-WAY — twelve drum passes, eight solfejo passes and every count-in lock to the chosen speeds | Addendum 03 §12; Addendum 04 §8 |
| 9.17 | **R88** · spend the freed break capacity on 2–3 commons rhythms at on-ramp depth (1–2 parts, slow + normal) | Founder | ONE-WAY — shot at M0 and given to the free tier | Addendum 04 §8, §12 |
| 9.18 | **R87** · extend the usability pilot to nine questions — is the hold count experienced as invitation or pressure; does the fade read as information or punishment | Build side; blocked only by INPUT-72 | TWO-WAY (derived) | Addendum 04 §12 |
| 9.19 | **Fork L** · does D79's visible sustain survive contact with students | Instrumented; pilot then M1 | TWO-WAY — estate-stated: visibility is a two-way door, the underlying facts are collected either way | Addendum 04 §15 |
| 9.20 | **Fork C** · breaks at M0 | Closed for Release 1 under G24; returns as material allows | — (closed) | Addendum 04 §1, §15 |
| 9.21 | **Fork D** · celebration | Closed under D80 | — (closed) | Addendum 04 §15 |
| 9.22 | **Fork K** · day-7 return | Answered contingent on INPUT-82 — the arc across the week, the appointment across the month, the count-in across the day | TWO-WAY (derived); its contingency is 9.11 | Addendum 04 §5, §15 |

**The claims this specification is betting on**, carried so the pilot and M1 are read as tests rather
than verdicts.

| # | Ledger row | Claim | Status | Converts at | Source |
|---|---|---|---|---|---|
| 9.23 | 48 | The echo loop is experienced as teaching, not testing | HYPOTHESIS | Pilot (R87), then M1 | Addendum 04 §13 |
| 9.24 | 49 | Visible sustain and personal bests increase voluntary replay without pressure or guilt | HYPOTHESIS | Pilot + M1 — replays after the best is secure; pressure/guilt items | Addendum 04 §13 |
| 9.25 | 50 | The fade reads as honest information, not punishment | HYPOTHESIS | Pilot | Addendum 04 §13 |
| 9.26 | 51 | The commons-free / scarcity-priced boundary converts free players to the paid line | HYPOTHESIS | M2, first paid cohort | Addendum 04 §13 |
| 9.27 | 46 | A beginner can be carried from voice to the screen drum in one sitting | HYPOTHESIS | M1 on first-session completion, or earlier through the usability pilot | Addendum 03 §4 |

---

## 10 · What the game requires at M0

The shoot is the irrecoverability deadline that governs all sequencing. Everything here is
ONE-WAY by definition — the cameras stop.

| # | Asset | Scope | Status after Addendum 04 | Source |
|---|---|---|---|---|
| 10.1 | Twelve drum passes | Four parts × three speeds — the deep rhythm | Unchanged; the tempo ladder still owes R82 | Addendum 04 §8 |
| 10.2 | Eight solfejo passes, **locked to the battery** | Every part, slow + normal; never standalone (R63) | Unchanged, decided (D57, G19). The echo loop and the whole voice door are rendered from these | Addendum 04 §8; Addendum 01 §9.1 |
| 10.3 | Stroke sample library | Every instrument in the free rhythm's battery; every stroke the solfejo names; several velocity layers, several takes; isolated clean one-shots. ~20–40 minutes | Kept; justification restated by D77 — the drum always sounds. C22 resolved | Addendum 04 §8; Addendum 01 §9.2; Addendum 03 §8 |
| 10.4 | Count-in variant bank | 10–12, including a longer one and a return-after-absence variant (R79) | Unchanged; count at INPUT-74. Fires at every session start under G16, so a bank of three is a jingle inside a fortnight | Addendum 04 §8; Addendum 03 §7 |
| 10.5 | Break / turnaround passes (~12) | — | **Removed — G24.** Fork C closed for Release 1 | Addendum 04 §1, §8 |
| 10.6 | Commons rhythms at on-ramp depth | 2–3 rhythms, 1–2 parts each, slow + normal | **New — R88.** Funded by the freed break capacity; serves D73 and D75 | Addendum 04 §8, §12 |
| 10.7 | Echo-loop states | — | **No new capture** — render-time muting of locked solfejo. INPUT-78/79 shape it | Addendum 04 §8 |
| 10.8 | Consent scope, partition capture (vocalization tier live), entrance calls, welcome, invitation | — | Unchanged | Addendum 04 §8; Experience Spec §4 |

---

## 11 · The build order this specification implies

Carried from Addendum 04 §9 without addition, so the spec and the plan cannot drift apart.

| # | Stage | Work | Source |
|---|---|---|---|
| 11.1 | Now, zero cost | Ratify or strike the deltas — D79 read twice. Confirm §2's four readings. Send INPUT-78 and INPUT-72 to Junior in one message. Label the open register one-way/two-way. Draft the commons list | Addendum 04 §9 |
| 11.2 | Pre-mockup | Build the mockup to carry: the echo loop, the drum-viewed-from-above with the presence lamp, the fade-and-rejoin behaviour, the post-round screen (three facts + best), the repertoire map. This is the object INPUT-79 and INPUT-69 are answered by seeing | Addendum 04 §9 |
| 11.3 | Pre-shoot | Close the owed list. Confirm the tempo ladder (R82). Lock the commons rhythms into the shoot day (R88) | Addendum 04 §9 |
| 11.4 | First build quarter | The instrument (tap door → screen drum, one surface per R74, scheduled audio per G10, D77's one-shots, D78's fade). The echo renderer (muting states over locked solfejo). The post-round and personal-best layer with the vocabulary sheet applied (R86). The repertoire map. The cycle's thin surfaces if INPUT-82 goes. Instrumentation per D50, extended to replays after the best is secure, pressure/guilt items, and fade-comprehension | Addendum 04 §9 |
| 11.5 | M1 | Read the numbers against R81-as-amended: **a core game and an appointment, no extrinsic layer.** Ledger rows 48–51 convert or fail here and at the pilot. The extrinsic toolkit remains available past the door and stays untested until a deliberate M2 experiment | Addendum 04 §9, §5 |

---

## 12 · Conflicts and gaps recorded rather than resolved

A register may not resolve a disagreement between two documents by choosing quietly. Each is stated,
with the later document's reading marked.

| # | Conflict | The two positions | Reading carried here | Source |
|---|---|---|---|---|
| 12.1 | **Who advances the student** | Experience Spec §2 and §3 invariant 4: the student pulls every lever, "never when the app decides (D28/R51)." Mandate 01 §2 and §9 **withdraw D28/R51 (D51)** — the app may advance the student — and Addendum 01 §3 **narrows D51 to D52**: the app *opens* rooms, it never *moves* the student into one | The later state: **D52.** Doors open on facts; the app opens, never promotes, never asserts readiness (restated untouched at Addendum 04 §3.3) | Experience Spec §2, §3; Mandate 01 §2, §9; Addendum 01 §3; Addendum 04 §3.3 |
| 12.2 | **E2, named presence** | E2 was **voided** by D38 under S6 — one man recorded four times cannot light up as four musicians, replacement question at INPUT-60. Addendum 04 §3.3 nonetheless states "E2 already lights the named musicians as each joins" and builds E21's presence lamp on it | **Registered as C23; not resolved.** E21 inherits the unresolved S6/D38 question, and until INPUT-60 is answered it is open whether the lamp *is* that answer (one slot, the student's own) or E2 is genuinely revived | Session 2 §5, §8 (D38); Addendum 04 §3.3; `registers/CONTRADICTIONS.md` C23 |
| 12.3 | **E9, the quiet count** | Experience Spec E9: a session closes with a quiet count. Mandate 01 §2 **revises it (D46)** — a session may close with celebration, a goal met, a streak advanced; quiet remains an option, not a rule. Addendum 04 §3.3 and §4.3 restore the quiet count as the ending and **upgrade** it to three facts plus the best | The later state: **the quiet count, upgraded** — three facts, one personal best, monotonic display. D46's celebration survives only as D80's non-vocal best moment, and streaks stay off the free tier under G15 | Experience Spec §1; Mandate 01 §2; Addendum 04 §3.3, §4.3 |
| 12.4 | **Door labels on three inputs** | `registers/INPUTS.md` labels INPUT-78, INPUT-79 and INPUT-84 **ONE-WAY (derived)**; `BACKLOG.md` §1 and §3.1 label the same three **two-way** | Carried as ONE-WAY at §9.1, §9.2 and §9.12 — the conservative reading, since each shapes either M0 material or what runs at the free door. The divergence is flagged, not resolved | `registers/INPUTS.md`; `BACKLOG.md` §1, §3.1 |
| 12.5 | **G15 against the grading layer** | G15 bars engagement mechanics on the free tier. Addendum 04 §2 reading 2 holds that round facts, personal bests and the lit map are the **game's own legibility**, not engagement mechanics, and run wherever the game runs | Carried as Addendum 04 states it — **and flagged by that file itself as "Medium — interprets a founder ruling," awaiting INPUT-84.** If the founder reads G15 the other way, §2.2 and §2.3 do not run at the free door | Addendum 03 §10 (G15); Addendum 04 §2, §11 |
| 12.6 | **INPUT-81's status** | `CHARTER.md` §7 names INPUT-81 as where approval happens; Addendum 04 §11 and `registers/INPUTS.md` carry INPUT-81 as **OPEN**, owed by the founder | Carried as **open** at §9.10. The Charter line reads as naming where approval happens, not as recording that it has | `CHARTER.md` §7; Addendum 04 §11; `registers/INPUTS.md` |

**No gaps.** Every game decision G1 through G26 is located in the estate and carried in §13; no
number in the series is missing, and nothing in §§1–11 rests on a decision this file could not
find.

---

## 13 · The decision base, complete — G1 through G26

The game decisions in full, so the spec above can be checked against its foundation without opening
four session files. Labels verbatim. This table restates; `registers/DECISIONS.md` is the register
of record for the series.

| # | Decision | Label | Where it lands in this spec | Door | Source |
|---|---|---|---|---|---|
| G1 | The app opens rooms; it never moves the student into one. Fork A closed | FOUNDER-DECIDED | §2.3.4, §12.1 | — | Addendum 01 §1, §3 |
| G2 | Vocalization replaces Western notation product-wide. No tab, no staff, no rhythm grid on any surface | FOUNDER-DECIDED | §5.3.1 | — | Addendum 01 §1, §4 |
| G3 | Junior's vocalization carries both rhythm and stroke, as do most masters' | FOUNDER-FACT | §5.3.2, §2.1 error channel | — | Addendum 01 §1 |
| G4 | Voice before drum. Every room's entry runs voice → voice-over-battery → battery | FOUNDER-DECIDED | §5.1.2, §5.3.3 | — | Addendum 01 §1, §5.1 |
| G5 | Tap-along ships in Release 1 as the door mechanic — vocalize and tap together | FOUNDER-DECIDED | §5.3.4 | ONE-WAY (derived — it is the free door; red line #5) | Addendum 01 §1, §5.2 |
| G6 | Advanced mode: the screen drum. Phone flat on a table, landscape, two hands, vocalize and strike | FOUNDER-DECIDED | §5.3.6 | — (superseded in placement by G13/E20) | Addendum 01 §1, §6 |
| G7 | Solfejo and the stroke sample library join the M0 pre-shoot list | DERIVED from G2–G6 | §10.2, §10.3 | ONE-WAY — shot at M0 | Addendum 01 §1, §9 |
| G8 | The engagement layer is designed against the research base, not against taste | PM-RECOMMENDED | §6, §9.18 | TWO-WAY (derived) | Addendum 01 §1, §8 |
| G9 | Timing feedback is binary and musical. A generous window; no tiers, no labels, no accuracy readout, on any surface | FOUNDER-DECIDED | §5.3.11 — **scope amended by D79** at §2.2 | — (amended, ratified) | Addendum 02 §1, §3 |
| G10 | The screen drum is scheduled, not triggered. The student's strike keeps Junior's correct part alive | FOUNDER-DECIDED | §2.1.1, §5.3.10 | — | Addendum 02 §1, §2 |
| G11 | Vocalization is the app's founding idea, not a substitution arrived at in session | FOUNDER-FACT | §5.3.1 provenance | — | Addendum 03 §1 |
| G12 | No app-fired dropout in Release 1. Support is removed only where the music itself calls for it | FOUNDER-DECIDED | §3 — the echo loop returns the in-room event through the voice channel, which G12 never touched | — | Addendum 03 §1; Addendum 04 §4.1 |
| G13 | The first session runs the whole sequence at its simplest setting — voice, tap door, screen drum, "all the way, dumbed down" | FOUNDER-DECIDED | §5.2.5 | ONE-WAY (estate-stated "high and permanent") — commits the screen drum to the free tier under red line #5 and E13 | Addendum 03 §1, §4 |
| G14 | The stroke set is three for hand instruments — slap, tone, bass — and two for stick instruments — rim and skin | FOUNDER-DECIDED | §5.3.7 | ONE-WAY (derived — fixes the shoot's sampling scope at M0) | Addendum 03 §1, §9 |
| G15 | No engagement mechanics on the free tier in Release 1. Decision deferred; nothing given for now | FOUNDER-DECIDED | §12.5 — its scope against the grading layer is at INPUT-84 | ONE-WAY — red line #5 makes anything given to the free tier permanent, mechanics included | Addendum 03 §1, §10 |
| G16 | The master's count-in fires at every session start, not only on advance. The variant bank is shot | FOUNDER-DECIDED | §2.2.8, §5.1.1, §10.4 | ONE-WAY — the bank is shot at M0 and a synthetic substitute is barred | Addendum 03 §1, §7 |
| G17 | No comparison between students in Release 1 — "not yet, maybe never" | FOUNDER-DECIDED | §6.5, §7.11 | — (Fork G closed for Release 1; INPUT-64 open beyond it) | Addendum 03 §1, §6.1 |
| G18 | No share or export in Release 1 | FOUNDER-DECIDED | §7, standing list | — (INPUT-71 stays in the counsel brief per R78) | Addendum 03 §1, §6.2 |
| G19 | C21 closed: D57 and D58 are decided, not proposed | FOUNDER-DECIDED | §10.2, §10.3 | — | Addendum 03 §1, §6.3 |
| G20 | Vocalization is genuinely this tradition's transmission method. INPUT-36 closed | MASTER-CONFIRMED | §3.1 — the echo is the method, not a mechanic | — | Addendum 04 §1 |
| G21 | The app remains the product direction. The core teaching assumptions are held proven by Junior's long experience with real students | FOUNDER-DECIDED + MASTER-CONFIRMED | §3.4 — the proven classroom is the loop's specification | — | Addendum 04 §1 |
| G22 | The notation system will be introduced openly as a standard; Opanijé positions as a music-education company | FOUNDER-DECIDED | §4.3 — the free commons rooms are the standard's teaching corpus | ONE-WAY — publication of the standard; published is published | Addendum 04 §1, §6 |
| G23 | Junior records any Bahian rhythm he is authorised to teach — Candomblé and popular | MASTER-CONFIRMED | §4.2 | — | Addendum 04 §1 |
| G24 | Breaks are deferred. Not every rhythm has one; introducing them now is difficult. Fork C closes for Release 1 as "later" | MASTER-CONFIRMED; INPUT-58 answered | §10.5, §9.20 — and it is why §3's echo loop had to carry the in-room event | — | Addendum 04 §1 |
| G25 | Rhythms already readily available online (e.g. Ijexá) are free. The commons is free; scarcity is priced | FOUNDER-DECIDED | §4.3 | ONE-WAY — the free tier, red line #5; the list is INPUT-80 | Addendum 04 §1, §5 |
| G26 | The screen drum may resemble a real drum viewed from above | MASTER-CONFIRMED (direction); mockup assent INPUT-69 remains, now small | §5.3.6 | ONE-WAY (derived — the surface ships inside the free first session and needs Junior's sight under Charter §9 item 10) | Addendum 04 §1 |

---

*Assembled 2026-08-03 under D83 (Addendum 04 §7) from Game Addenda 01–04, the Operator Mandate, the
Experience Spec and the Charter. Nothing here is measured evidence; ledger rows 46 and 48–51 exist
so the pilot and M1 are read as tests rather than verdicts. D79 is ratified; the remaining deltas of
Addendum 04 are ADOPTED and operative as plan-of-record, reversible at ratification review. Every
form question on the tradition's material remains Junior's.*
