# Opanijé — Game & Student Experience (compacted spec)

Mobile app teaching Afro-Brazilian percussion (Ketu Candomblé + Bahian popular toques) from one
living master, "Junior". No Western notation. Student plays along to a recorded battery (ensemble)
via voice, taps, or a screen drum.

## 1 · Grading constitution (D76)

> Facts may drive sound; nothing may drive a sentence.
> Sustain is visible, precision is audible, judgment is human.
> The game grades the round; the ear grades the playing; the master grades the player.

| Category | Definition | Permitted? |
|---|---|---|
| Measurement | strike occurred at time *t* in zone *z* — a fact | Yes |
| Feedback | what it meant musically | Yes, **audible channel only** |
| Grading | how this round went | Yes, **post-round only, self-referenced** |
| Classification | what this student *is* (readiness, correctness, mastery, standing) | **Never** |

May: schedule audio on a strike, sustain a part, fade one for want of a strike, light a lamp, count
after the round, compare to the same student's own earlier count. May not: express evaluation in
words, numbers, meters, tiers, stars, letters or percentages about playing quality; say anything at
all about the player.

One line: **Your finger keeps his groove alive; the drum tells you where you are; the app never
says.**

## 2 · The instrument (the screen drum)

| Property | Spec |
|---|---|
| Posture | Phone flat on a table, **landscape**, two hands. Screen = drum head seen from above, divided into zones. May visually resemble a real drum from above (G26). |
| Zones | 3 on hand instruments: slap / tone / bass. 2 on stick instruments: rim / skin. (G14) |
| Zone labels | The student sees **Junior's syllable**, never the English stroke word (D56). |
| Notation | **None** — no tablature, staff, rhythm grid, piano-roll on any surface. Vocalization IS the notation (G2). |
| Instruction | The syllable carries both rhythm *and* stroke (G3). Say the bass syllable → strike the bass zone. No legend, no translation step. |
| One surface | Zone count is the dial: 1 zone at the door → 2 → 3. Tap-along and screen drum are the **same instrument at different settings** (R74). |
| Velocity | **Not encoded.** Touch velocity unreliable across devices; the drum is a *transcription* device, not a simulation. |
| Timing window | **Binary and generous** (G9). Inside = in the groove; outside = not. No tiers, no labels, no per-strike marks. No per-device calibration in Release 1. |
| Audio model | **Scheduled, not triggered** (G10). App renders Junior's correct part in time with the battery; the strike *keeps it alive*, it does not fire the sample. |
| Latency | Tolerable: scheduled audio is buffered ahead; off-grid one-shots have no reference to smear against. Native low-latency engine is off Release 1's critical path. |
| Ship gate | **No screen-drum surface ships without Junior having seen it** (red line #1). Building it unshown is fine; shipping is not. |

### Strike handling — the only three cases

| Case | Behaviour |
|---|---|
| **In-window, right zone** | Junior's correct part **stays alive** (scheduled render continues). No per-strike sound, no mark. |
| **Out-of-window** | A one-shot of the **real stroke** fires — the student's actual hit, audible, off the groove. A real drum struck off-time still sounds. |
| **Wrong zone** | A one-shot of the wrong stroke fires — audibly wrong stroke at the right time. |
| **Unfed part** | The part **fades** — thins, never stops. The battery never stops for you. |
| **Fed again** | The part **returns**. You cannot lose; you can only be more or less present. |
| **Fail state** | **None exists anywhere in the product.** |

By design the student hears **stroke** errors and never **timing** errors. The stroke sample library
is therefore the entire feedback system, not decoration.

**Open build question:** does a wrong-zone strike sound *instead of* the correct part, or *on top of*
it? Explicitly undecided.

**Presence lamp (E21, unratified):** the student's own slot glows while their part is fed, dims as it
fades — 1:1 visual mirror of the audio, no numbers. It is the **only** thing on screen mid-play
beyond the room's named/faced musicians. Propped phone, arm's length, no menus (E3).

**The voice is never measured, in any mode** — charter-level; true today because there is no
microphone (D26), and stays true if one ever ships.

## 3 · The micro-loop — the echo loop (D74)

The teaching shape of oral pedagogy, rendered:

> **voice together → voice withdraws → you alone (battery continues) → voice returns → you hear
> whether you held.**

| Property | Spec |
|---|---|
| Battery | Never perturbed. Continues throughout all four states. |
| Implementation | **Render-time muting** on solfejo (sung syllables) recorded *locked to the battery*. No new capture, no audio engine, no per-state performance. This is why the loop is nearly free to build. |
| Material | 8 solfejo passes, locked: every part, slow + normal. Locked material can be soloed later; standalone can never be locked afterwards. |
| Why it matters | The **reveal** is the moment the student learns whether they held — the information the older silent design withheld. It is the answer to illegibility. |
| Gate 1 | INPUT-78 — the classroom transcription (how a real Junior lesson runs minute by minute). The proven classroom is the loop's specification. |
| Gate 2 | INPUT-79 — Junior's assent that the rendered withdrawal is his teaching, answered by *seeing the mockup*. |

The teaching voice receding is the method itself, not a game mechanic.

## 4 · The macro-loop — the repertoire arc (D75)

The map is not a difficulty grid for one rhythm; it is **the city**.

- **A room = a rhythm** (Ijexá, afoxé, samba de roda, samba-reggae, and any toque Junior is
  authorised to teach). Each entered voice-first; each carries its own personal bests.
- **The Room is unnamed** (E18) — it is simply where you play.
- **Free rooms**: rhythms already readily available online. The commons is free; scarcity is priced.
  Free commons rooms double as the published notation standard's teaching corpus.
- **Progress = rhythms met and carried further.** Never a completion fraction, never a person-level.
- **Ladder inside a room**: fewer drums = exposure, more drums = shelter; speed is a separate axis;
  **moving down is a move, not a retreat**. Parts switch freely in both directions at any time (E8).
- **The map records** rooms visited, rhythms met, parts carried, personal bests — **all monotonic.
  The map lights and never dims.** It *is* the state space, lit — one object, not a progress display
  beside a grid.
- **Doors open on facts.** The app opens rooms; it never promotes, never moves the student, never
  asserts readiness.
- **Vocabulary rule**: play-layer words are spatial/musical — rooms, visits, holds, bests. Never
  "received", "confirmed", "mastered", "level", "rank", "graduate". **Sentence test:** if a string
  can be read as a statement *about the student* rather than *about the round*, it is wrong, however
  friendly.
- **Play ledger is resettable by design** and never writes into the Caderno (the master's notebook /
  standing record). Two separate ledgers.

## 5 · Session spine, step by step

1. **Count-in.** Junior's recorded count-in fires at **every** session start (not only on advance).
   Bank of 10–12 variants incl. a longer one and a return-after-absence one.
2. **Voice together.** Syllables + student, over the battery.
3. **The echo reveal.** §3.
4. **Student's chosen branch.** More exposure, more drums, another tempo, another part — any
   direction, any time.
5. **A second reveal, or a clean full-battery close.** Either ending is musical.
6. **The quiet count.** Post-round screen (§6).
7. **The invitation.** The master offers the next step, now including the monthly cycle appointment.
8. **Battery Detective** survives only as an optional 30-second prelude, not the spine.

**The door (voice→drum), used every room:** voice alone → voice over the battery → battery (G4). All
three states are render-time muting of already-captured material.

**Tap-along stage:** student vocalizes and taps *together*; the app measures the **tap**, never the
voice. This is the door, not the session — what you do before you have an instrument, on the bus, in
the first 90 seconds. Whether the hand does unison, pulse, or reference (the agogô) is Junior's
pedagogical call, still open.

**First session runs the whole instrument, day one** (G13/E20): voice → voice over battery →
battery → tap door → screen drum, all of it, at its simplest setting. "Advanced mode" is the
product.

## 6 · Post-round summary — exact contents

Shown **only after the musical ending**. Size ceiling: **at most three facts plus the best.**

| Slot | Content |
|---|---|
| Fact 1 | **Cycles the battery played with you** |
| Fact 2 | **Longest unbroken hold** |
| Fact 3 | **The setting** — part, drums present, tempo, mode |
| Personal best | **Longest hold at this setting** |

**Fed cycle definition:** a cycle where a generous proportion of the part's strikes landed in the
generous window. **Cycle granularity, never milliseconds.** The proportion is tuned in the pilot and
is never displayed per strike.

**Personal-best rules:** self-referenced (student vs their own yesterday, never another student);
**monotonic** (only ever rises); **per-setting** (a best at more exposure is a different best).

**Monotonic display rule:** the screen **never says "below your best."** Short of the best, only the
three neutral facts show. Equal or beyond, the best updates and the room celebrates.

**Celebration object** = the new personal best, carried by **non-vocal sound design and the room's
light**. Junior's recorded voice variants are reserved for **firsts and returns** — first entry,
first rhythm finished, return after absence — and are never spent on a personal best.

Nothing evaluative appears mid-play beyond the presence lamp. Per-strike feedback stays binary,
generous, audible-only; only the **post-round aggregate of those binaries (sustain)** is visible.
Accuracy-style readouts stay barred on every surface.

**Named residual risk:** sustain becomes a proxy score and players chase the hold like an accuracy
number. Mitigations: nothing mid-play, monotonic display, no comparison, resettable ledger,
pressure/guilt measured rather than assumed.

## 7 · Screens and surfaces (student app only)

| Surface | Contents |
|---|---|
| **Arrival / presentation** | What this is, whose it is, what happens here. Nothing is audible before this point, so it carries the entire conversion — highest-stakes screen in Release 1. |
| **Google sign-in (OAuth)** | Then straight on. |
| **Welcome** | Junior, recorded once, seconds not minutes. Most-viewed asset in the estate. |
| **Choosing** | Student picks their part; preceded (open sub-fork) by one plain question — "do you have an instrument with you?" — routing between palmas-and-voice and agogô. Every pick reversible any moment, either direction. |
| **The call** | The *Primeira Chamada*. The battery is there; the student's part is theirs. |
| **Play screen** | Who is in the room — names and faces, present, not moving — plus the presence lamp. Phone propped, hands busy, nothing asks for attention. Landscape screen drum in drum mode. |
| **Level change** | **Clean break**: cycle finishes, master calls the next player in with a count-in, battery resumes with the new part. |
| **Post-round / quiet count** | §6. |
| **Home screen** | Today's session at the top; the rhythm and how far through it beneath; the Caderno card. |
| **Caderno card** | Empty until the first *real practice* (never earned by answering the call). Then: what happened, when, who was in the room. |
| **Opt-in nudge prompt** | Asked only *after* the first entry is written, in the master's framing, not the system's. |
| **The repertoire map** | The city of rooms, lit, never dimming. |
| **The ending** | Free rhythm finished → the master speaks again, not to sell but to say what comes next: domestic path (caixa / Vanderson's toque) or Salvador. **Neither recording names a price.** Salvador exists only here. |
| **Cycle surfaces (thin, conditional)** | Appointment, calendar, replay, Caderno entry. Submission runs outside the app over ordinary channels. |

**Staying free:** the student who never buys keeps the room exactly as it was, permanently — nothing
withdrawn, degraded or nagged. **Language** follows the phone, manual override. **Connection loss:**
the loop continues, the lever fails gracefully, facts buffer locally and sync on return. **Cache is
not a library** — ephemeral, invisible, OS-evicted, no user-facing list; Release 1 streams.

## 8 · Prohibitions — what the game may never show or say

Accuracy percentages · stars · letters · tiers · "perfect/good/miss" labels · fail screens · streaks
with loss · person-levels · readiness or mastery claims · public rank · comparison between students
· purchasable repair · synthetic voice · any game result touching the Caderno · any measurement of
the voice.

Also barred: anything purchasable that confers, accelerates or implies standing; anything gating
access to what was already given (hearts, lives, energy, timers on the free room); badges, titles or
ranks that read as a master's acknowledgment; any master recording that names a price or product;
any gamified surface that survives withdrawal of the material it points at; share or export;
shipping a screen-drum surface Junior has not seen. Also absent from Release 1: microphone, commerce
/ price display of any kind, 1:1 booking, permanent Salvador surface, download library, a name for
the Room.

**Everything not on this list is permitted.** Where a mechanic is arguable: build it, put it in the
mockup, take it to Junior.

**Invariants:** facts never verdicts (a progress bar filling toward a goal is a verdict in costume);
counts never targets ("12 cycles", never "12 of 20"); no streaks and no reproach; the student pulls
every lever; the master offers the path, the app handles the price; a rule may be stated, a person
may not be measured (an empty Caderno card may say what earns an entry, not how close you are);
facts survive the network; nothing is ever taken back.

**Frustration audit — architectural answers:** fail states → none, fade-and-rejoin replaces them;
forced repetition → free part-switching both ways; difficulty walls → student sets every axis;
negative feedback → error lives in sound, never in sentences; comparison → none between students;
loss → nothing is ever taken, monotonic records, no hearts, no decay; illegibility → echo reveal +
honest drum + visible hold; boredom → echo loop + repertoire arc.

## 9 · Roadmap sequence

**0 · Escrow (outranks everything).** Escrow the Android signing keystore and backup repo key
off-box; restore a passphrase to backup archives. One machine holds code, credentials, backup key
and signing key, no standby.

**1 · Now (zero cost).** Ratify or strike deltas D71–D83 (D79 read twice — the one place the plan
amends a founder ruling). Confirm the four derived readings, esp. whether the free-tier
engagement-mechanics ban reaches the grading layer. Send Junior one message carrying INPUT-78 +
INPUT-72. Label the open register one-way/two-way. Draft the commons list. *Why first:* Junior's
latency is uncontrolled, ratification's is not — ask first, ratify while waiting.

**2 · Pre-mockup.** A mockup carrying exactly five things: (1) the echo loop; (2) the drum from
above with the presence lamp; (3) fade-and-rejoin; (4) the post-round screen — three facts + best,
monotonic rule; (5) the repertoire map. Alongside: extend the usability pilot to nine questions
(adding *is the hold count invitation or pressure?* and *does the fade read as information or
punishment?*); decide the monthly-cycle go/no-go so the mockup's ending is truthful; include the
engagement layer so Junior rules on visible form. *Gate:* INPUT-79 and INPUT-69 are answered by
seeing this. Industrial-design filing is time-critical **before any screen goes public** — shown to
Junior is not public; shown in a pitch or store listing is.

**3 · Pre-shoot (all one-way — the cameras stop).** Close the owed founder/Junior input list;
confirm the tempo ladder first-hand; lock 2–3 commons rhythms at on-ramp depth into the shoot day;
update the counsel brief once; capture the rights partition item-by-item with the vocalization tier
live; settle consent scope covering interactive use and isolated stems.

**M0 shoot assets:** 12 drum passes (4 parts × 3 speeds); **8 solfejo passes locked to the battery**
(every part, slow + normal, never standalone); stroke sample library (~20–40 min: every instrument
in the free rhythm's battery, every stroke the solfejo names, several velocity layers and takes,
isolated clean one-shots); count-in variant bank of 10–12; commons rhythms at on-ramp depth (2–3
rhythms, 1–2 parts, slow + normal); entrance calls, welcome, next-step invitation ×2, narrated video
per catalog item; consent scope. **Removed:** ~12 break/turnaround passes (breaks deferred — not
every rhythm has one). **Echo-loop states require no new capture.**

**4 · First build quarter.** (4.1) The instrument: tap door → screen drum as one surface, scheduled
audio, real one-shots for out-of-window and wrong-zone, fade-and-rejoin. (4.2) The echo renderer:
muting states over locked solfejo — shaped by INPUT-78, gated on INPUT-79. (4.3) Post-round and
personal-best layer with the vocabulary sheet applied — strings specified before written, because
this is where classification leaks back in. (4.4) The repertoire map. (4.5) The cycle's thin
surfaces if the cycle goes. (4.6) Instrumentation: replays *after* the best is secure,
pressure/guilt items, fade-comprehension. Also: play layer as a separate resettable subsystem that
never writes to the Caderno; entitlement rewrite; accounts; Pix rail live before Release 1.

**5 · M1.** Measures a product **with** a core game and an appointment and **without** the extrinsic
toolkit — recorded as the baseline, dated, before the numbers exist. **Two numbers judge every game
element: first-session completion and day-7 return.** Extrinsic toolkit (streaks, XP, goals, loss
aversion, unlockables) stays past the door and untested until a deliberate M2 experiment — shipping
it inside M1 would make M1 unreadable.

**Track B (parallel, always).** Ten hand-booked, hand-paid private classes across Junior and
Vanderson, founder hosting each as measurement — the only line producing MEASURED evidence (master
payout, willingness to pay at two price points, list conversion, founder-hour cost per sale, whether
teaching rhythm through a screen works at all).

**The Gate (month 12 from M1).** Seven criteria; the losable one is zero red-line violations plus a
consent/rights archive auditing clean — game-use consent scope, the five-value partition enforced at
the API contract layer, the no-payment-link invariant run as a query. Outcomes: venture option,
continue bootstrapped, or hold at one house.

**Hypotheses under test (pilot / M1 / M2):** echo loop experienced as teaching not testing · visible
sustain and bests increase voluntary replay without pressure or guilt (governs whether visible
sustain is reversed) · the fade reads as information not punishment · the commons-free /
scarcity-priced boundary converts · a beginner can be carried from voice to screen drum in one
sitting.

## 10 · ID index (one line each)

**Game decisions (G).** G1 app opens rooms, never moves the student · G2 vocalization replaces
Western notation product-wide · G3 the vocalization carries both rhythm and stroke · G4 voice before
drum: voice → voice-over-battery → battery · G5 tap-along ships as the Release 1 door mechanic · G6
screen drum: phone flat, landscape, two hands, vocalize and strike · G7 solfejo + stroke library go
on the M0 pre-shoot list · G8 engagement layer designed against research, not taste · G9 timing
feedback binary and musical, generous window, no readouts (post-round scope amended by D79) · G10
scheduled not triggered — the strike keeps the part alive · G11 vocalization is the founding idea ·
G12 no app-fired dropout in Release 1 · G13 first session runs the whole sequence at its simplest
setting · G14 3 strokes for hand instruments, 2 for stick · G15 no engagement mechanics on the free
tier in Release 1 · G16 count-in fires at every session start · G17 no comparison between students ·
G18 no share or export · G19 solfejo and sample-library decisions are decided, not proposed · G20
vocalization is genuinely this tradition's transmission method · G21 the app stays the product
direction; teaching assumptions held proven · G22 the notation system is published openly as a
standard · G23 Junior records any Bahian rhythm he is authorised to teach · G24 breaks deferred out
of Release 1 · G25 rhythms readily available online are free · G26 the screen drum may resemble a
real drum viewed from above.

**Experience decisions (E).** E1 level change is a clean break with a count-in · E2 screen shows
named presence, musicians lighting as each joins (voided once, unresolved) · E3 phone propped and
glanced at, one lever, no menus · E4 door = presentation → OAuth → welcome → choose part → call →
play → first entry · E5 first Caderno entry earned by first real practice · E6 home screen leads
with today's session + Caderno card · E7 master offers the next step at the end of the free rhythm ·
E8 parts switchable freely both directions any time · E9 session closes with a quiet count · E10
Salvador appears at the ending only · E11 language follows the phone with override · E12 nudges
opt-in, asked after the first entry · E13 free student keeps the room forever unchanged · E14 a
bought course = lessons + rooms + narrated video · E15 no 1:1 in Release 1 · E16 connection loss:
loop continues, facts buffer and sync · E17 the free rhythm is Junior's · E18 the Room is unnamed ·
E19 door asks one plain instrument-ownership question (open) · E20 the whole instrument on day one ·
E21 the presence lamp (recommended, unratified).

**Plan decisions (D).** D1 private-class pilot · D14 pre-shoot stems list · D16 escrow keys ·
D26 no microphone · D27 no download library · D28 student pulls every lever (withdrawn by D51) ·
D36 mockup before shoot · D38 voided E2's four-musicians lighting · D45 revised the ask-back framing
· D46 allowed celebration endings (superseded) · D50 instrumentation plan · D51 withdrew D28 · D52
narrowed it: the app opens rooms, never moves the student · D56 the student sees the syllable, not
the English stroke word · D57 eight locked solfejo passes · D58 the stroke sample library · D73
commons free, scarcity priced · D74 the echo loop · D75 the repertoire arc / lit map · D76 the
grading constitution · D77 real one-shots for out-of-window and wrong-zone strikes · D78
fade-and-rejoin, no fail state · D79 post-round visible sustain, ratified · D80 celebration = the
personal best, non-vocal · D81 monthly live master cycle · D82 free commons rooms are the standard's
teaching corpus · D83 assemble one register of record.

**Recommendations (R).** R10 Track B pilot · R49 lock-and-file the design · R51 (with D28,
withdrawn) · R53 recordings name no price · R58 moving down is a move · R59 play layer separate and
resettable · R63 solfejo recorded locked to the battery · R65 the map is the state space, lit · R66
return-after-absence repair asset · R74 one surface, zone count as dial · R78 keep share/export in
the counsel brief · R79 10–12 count-in variants · R81 M1 baseline (amended) · R82 confirm the tempo
ladder first-hand · R83 fed cycle = generous proportion in the generous window, cycle granularity ·
R84 monotonic display rule · R85 at most three facts plus the best; nothing evaluative mid-play ·
R86 the play-layer vocabulary sheet · R87 nine-question usability pilot · R88 spend freed break
capacity on 2–3 commons rhythms.

**Sessions (S).** S2 the ladder framing source · S3 accounts, entitlements and the Pix rail before
Release 1 · S6 the named-presence problem (one man recorded four times cannot light as four
musicians).

**Open inputs (INPUT).** 14 subtitle/localization scope · 21 partition capture item-by-item incl.
narration · 27 which toque is free · 36 vocalization as transmission (closed) · 41 ladder pedagogy ·
44 second machine / escrow ruling · 47 whether a session cache is a copy · 58 breaks (answered:
later) · 60 replacement for named presence · 62 Junior rules on engagement-layer form · 64
comparison beyond Release 1 · 67 Junior's syllable set fixed as the reference dialect (one-way) · 68
what the hand does: unison, pulse or reference · 69 mockup assent on the screen drum · 70 which
strokes/drums may be sampled in isolation · 71 share/export · 72 the rough-audio question (blocks
the pilot) · 73 the celebration object (answered) · 74 how many count-in variants · 77 which
instruments take 3-zone vs 2-zone vocabulary · 78 the classroom transcription · 79 form assent on
the rendered echo · 80 the commons list · 81 vocabulary sheet approval · 82 the monthly cycle's
go/no-go, format, channel, price · 83 publication scope · 84 whether the free-tier mechanics ban
reaches the game's own legibility.

**One-way doors (expensive/impossible to reverse):** consent scope; anything given to the free tier
(permanent by red line); the fixed reference dialect; publication of the standard; and **anything
shot at M0 — the shoot is the irrecoverability deadline that governs all sequencing.**
