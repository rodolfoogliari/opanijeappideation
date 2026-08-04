# Opanijé — Game Addendum 02: The Screen Drum's Architecture, and the Line on Grading

**Date.** 2026-08-01 (second session of the game conversation).

**Status.** FOUNDER-DECIDED where marked; PM-RECOMMENDED where marked; DERIVED where a consequence
follows necessarily and is stated so it is visible rather than discovered. Deltas are **proposed**
and require founder ratification, except where they record a founder ruling made in session.

**Authority.** Product form on secular material, brand, voice and product shape are the founder's
under v2.0 §12 (RULED). Everything here that touches sacred material's *form* is reserved to Junior
under red line #1 and is registered as an open input, not decided.

**What this file is.** The second session of the game conversation, opened against
`GAME-CONVERSATION-CONTINUATION-PROMPT-FORK-B-ONWARD.md`. It did **not** reach Fork B. It ruled two
things about the screen drum that Fork B now depends on, read the one estate document that was
missing from the last session, and opened one new fork.

**Numbering continues the estate.** Game decisions from G9 (Addendum 01 ends at G8). Deltas from D59
(ends at D58). Inputs from INPUT-72 (ends at INPUT-71). Recommendations from R73 (ends at R72).
Ledger rows from 44 (ends at 43). Risks from #25 (ends at #24). Contradictions from C21 (v2.0 §17
ends at C20).

**Nothing here touches a red line.** §15 states the addition to Mandate 01 §10. §4 states the one
place where existing red-line exposure is *reduced*, which is a first for this conversation.

---

## 1 · What was decided

| # | Decision | Status |
|---|---|---|
| G9 | **Timing feedback is binary and musical.** A generous window: inside it the stroke lands in the groove, outside it it does not. **No tiers, no labels, no accuracy readout, on any surface** | FOUNDER-DECIDED |
| G10 | **The screen drum is scheduled, not triggered.** The app plays Junior's correct part in time with the battery; the student's strike keeps it alive rather than firing each sample | FOUNDER-DECIDED |

**Provenance note on G10.** The founder stated this as a description ("a Guitar Hero like, but Afro
Bahia percussion, the sound set will play the correct Junior version of the groove") rather than as
a ruling, and confirmed it by instructing this file be written. It is recorded as a decision. If
that reading is wrong it should be corrected before ratification, not after.

**A three-option fork on graded timing was put and answered.** The founder was offered binary /
tiers-on-tap-only / tiers-everywhere-by-amendment, and chose binary.

---

## 2 · The architecture, in one sentence

> **Your finger keeps his groove alive; the drum tells you where you are; the app never says.**

Each clause is load-bearing. The first is G10. The second is the tradition's own method and R15's
reference pulse. The third is Mandate 01 §3, now holding on the hardest surface in the product
rather than only on the easy ones.

---

## 3 · Why binary, stated so the reasoning survives the decision

Three arguments, in the order of their strength. The first is not a governance argument and should
be read first by anyone tempted to reopen this.

**3.1 · The offset is unknowable, so the readout would be false.** Android exposes two hardware
feature flags — `android.hardware.audio.low_latency` (continuous output latency ≤45 ms) and
`android.hardware.audio.pro` (round-trip ≤20 ms), defined in CDD §5.6 and §5.10 — and **no API that
reports actual latency at runtime** (VERIFIED-EXTERNAL, 2026-08-01, developer.android.com). Touch
input latency is separate, undocumented, and varies by device and screen refresh. An assumed offset
is therefore wrong by a different amount on every phone.

The consequence is not academic. "Precise" on a flagship and "precise" on an entry device are
different physical events, and the error lands hardest on the low-tier Android population — which in
Brazil is the domestic practitioner, the audience the free door exists for. A student would be told
he is sloppy because his phone is cheap.

**3.2 · The governance line stops holding as the surface becomes a drum.** Game Addendum 01 §5.2
settles that a screen tap is a screen fact rather than a musical verdict, and that holds on
tap-along, where nobody mistakes tapping a phone on a bus for drumming. **It stops holding on the
screen drum, whose entire purpose is to stand in for a drum.** A precision grade on that surface is
a musical verdict — Mandate 01 §10 item 3, tracing to §3.

**3.3 · FF3 is the acceptance test and a precision readout points at it.** The two groups a base
product must serve are single-player adults and beginners who cannot play to a metronome, *which is
most beginners*. Public absolute performance feedback reduces perceived competence among weaker
learners (Game Mechanics Research Review §4; Sailer et al. 2017), and that is precisely the FF3
population.

**What was explicitly not done.** §10 item 3 traces to Mandate 01 §3, which is founder-issued and
withdrawable by the same instrument that issued it. The founder was offered that route as option 3
and declined it. This is recorded so that the item is understood to have survived a live challenge
rather than never having been tested.

---

## 4 · What G9 and G10 remove — the session's only scope reduction

Every prior session in this conversation added to Release 1. This one subtracts.

- **Per-device calibration leaves Release 1.** Game Addendum 01 §10 named tight grading as "the
  decision that makes advanced mode cheap or expensive." A generous window absorbs device variation.
  It is now cheap. **DERIVED.**
- **The native low-latency audio engine leaves Release 1's critical path.** Scheduled audio is
  buffered ahead and is immune to output latency; it does not require Oboe/AAudio or `AVAudioEngine`
  to be acceptable. Risk #18 (nobody in the estate has built mobile audio) is not resolved, but it is
  no longer load-bearing for M1. **DERIVED.**
- **Mandate 01 §10 item 3 stands untouched.** No amendment, no delta against the founder's own
  mandate, no new red-line exposure.
- **INPUT-69 softens.** A glass drum that plays Junior's correct part and grades nobody is a milder
  form question than one that reports a student's imprecision on a toque of Obaluaiê. The input
  remains open and remains Junior's; it is simply a smaller ask.
- **Fork G shrinks to near-nothing.** Its stated reason for being live was that tap and screen-drum
  accuracy are "precise, comparable numbers, which makes leaderboards genuinely feasible." Under G9
  that number does not exist. Comparison between students returns to theoretical. INPUT-64 stays
  open but is no longer urgent.

---

## 5 · The error channel that survives, and why it is the right one

G9 removes the timing readout. It does **not** remove feedback, because the zones do the work.

Under G3 the syllable names the sound, and under G6 the syllable names the zone. So striking the
slap zone where the part wants bass produces **an audibly wrong stroke at the right time**. The
student hears stroke errors and never hears timing errors.

That is the clean split and it was already implicit in G3. It also gives **D58 (the stroke sample
library) a second and better job**: the samples are no longer only what makes the screen audible,
they are the entire feedback system. This raises D58's value and does not change its cost.

**PM-ASSERTION, flagged rather than assumed:** whether a wrong-zone strike should sound *instead of*
the correct part or *on top of* it is a design question with a real pedagogical difference. Not
decided here.

---

## 6 · The Game Mechanics Research Review, now read

`OPANIJE-GAME-MECHANICS-RESEARCH-REVIEW-2026-07-31.md` was absent from the project during Addendum
01's session and was supplied during this one. Its position in the estate is now precise: **written
after Operator Mandate 01 and before Game Addendum 01.** It quotes the mandate correctly and knows
the toolkit is open; it contains no mention of vocalization-as-notation, the tap door, or the screen
drum.

**Confirmed correct.** Its audit table is sound. It correctly demotes four over-claims from the first
game proposal: the `Rules/Goals + Challenge + Mystery` combination (measured on learning outcomes,
not retention), peak–end as a return device, the rolling weekly pulse, and prerecorded-master
relatedness. Its §5.3 arrives independently at R58 and R65 — the ladder is a state space, not a
line — which raises confidence in R65 rather than duplicating it.

**Wrong against the estate.**

| Its claim | The estate |
|---|---|
| §3: "Adult practitioners only in the current product plan" | **False.** FF3 names beginners; risk #13 states a beginner-first game invites minors as a population; Mandate 01 D49 enlarges INPUT-39 explicitly for "a population that includes minors." Its own §10 guardrails and §8.3 note on personal investment therefore bind *harder*, not softer, and it applies them as if softer |
| §9.4's randomised product test | **Foreclosed.** Ledger row 38 — Release 1 ships once, no counterfactual — and R71's arithmetic: ≈291 users per arm for a ten-point D7 difference, ≈2,500 for five points, while splitting the cohort halves precision on both of M1's headline numbers |
| §8.2: do not ship the streak alongside the game | **Live, not closed.** Mandate 01 R60(a) ships the streak. Game Addendum 01 §8.6 answers with the discriminator — a streak is satisfied by the minimum session, the game is not. That yields a *defensible* read, not a clean one. The objection survives the answer and is recorded rather than dismissed |

**Five findings that were not available before it was read.**

1. **Fork B's option 3 is heavier than its wording suggests.** §7.2's one-sitting shape is five beats
   and assumes the session *is* the drum room. D54 puts three beats in front of it. "End on one short
   dropout at the peak" is therefore two session architectures stacked — eight beats — on the day the
   headline number is measured.
2. **The mockup needs an audio half that is not scoped.** §11's six questions for Junior — is this
   dropout musically real, how long may support disappear, which instrument may be the reference
   without becoming a metronome — cannot be answered from a screen. D36, Mandate 01 §4.3 and Game
   Addendum 01 §6.3 all require "a working mockup, never described," and all are visual. See §7 and
   R76.
3. **§11's worst case is dead.** Its decision rule ends: if neither dropouts nor calls are valid, do
   not force the recording into a game. Written before D55. **The tap door is now the fallback**, it
   measures a screen fact, and it touches the body recording not at all. Fork C is materially
   de-risked by this.
4. **§9.3 survives where §9.4 does not.** The seven-question usability pilot is non-statistical,
   needs no cohort, and answers most of what Fork B argues about. **Track B is a candidate vehicle**
   — ten paid sessions, founder in the room, students already submitting recordings, ≈R$0. Not free:
   it adds a research task to a paid class and competes with Track B's own exit evidence (rows 18,
   25, 6, 17, risk #14). Offered, not recommended.
5. **Release 1 carries no relatedness mechanism either research base endorses.** The review and the
   compass document converge independently — the review at §4 ("prerecorded presence cannot be
   assumed to equal reciprocal human relatedness"), the compass via Hove & Risen 2009, where
   affiliation effects were unique to interpersonal synchrony. v2.0 §3.3 states that "retention runs
   on an appointment with a named human who might say your name." **That appointment is the monthly
   cycle, which is Release 2 / M3.** Release 1's retention therefore rests entirely on the play
   layer: streak, celebration, map, implementation intention. This is a Release-2 thesis that
   Release 1 is being asked to carry, and it is stated here rather than discovered at M1.

---

## 7 · The rough prototype recording, scoped

Scoped in session. **PM-RECOMMENDED and awaiting the founder's go plus Junior's written OK (R55).**

**The reframe that makes it worth doing:** Junior performs the edit and judges it in the same act. We
are not building something to show him. He makes it, and if he cannot play it — or plays it and says
it is not how the music works — that *is* the answer. Under red line #1 this is the correct shape:
the authority designing the form rather than reviewing ours.

| # | Take | Answers |
|---|---|---|
| 1 | The reference alone, looping | Which instrument may carry the pulse without becoming a metronome (R15) |
| 2 | One part over the reference, straight through, no hole | The control. Without it the test proves nothing |
| 3 | Same, reference drops one cycle, returns | Fork J, short form |
| 4 | Same, reference drops several cycles, returns | How long support may disappear before it stops being the music |
| 5 | A break or turnaround, if these toques carry them | **INPUT-58, performed rather than asked** |
| 6 | The same part in solfejo | Proves the format before D57 spends eight shoot passes on it |

**ASSUMPTION on time:** 30–60 minutes. His estimate replaces this one.

**Open technical question, his to answer:** whether he can produce two parts at once alone on a
phone. If not, takes 2–4 need two devices or the list changes.

**Rules attached.** Written OK before anything is recorded (R55). Prototype only, never a stem
source, never shippable in any form. Deleted when M0's real stems land — the trigger stated now,
because rough takes survive. This is **not** the partition capture (INPUT-21 stays at the shoot,
item by item) and **not** a tempo decision (INPUT-59 stays pre-shoot, though this informs it).

**One thing this recording cannot do.** A dropout Junior improvises in ten minutes is still a red
line #1 form decision. The recording is evidence; **his ruling is a separate act and must be said in
words.** A casual take must not be allowed to stand in for it.

---

## 8 · The device-latency finding, and why no device study is needed

Investigated at the founder's instruction. Recorded because it changes a Release 1 scope item.

- **Android answers the question itself.** The two feature flags in §3.1 are runtime queries. There
  is no device list to acquire, maintain, or let go stale (VERIFIED-EXTERNAL, 2026-08-01).
- **They err in the safe direction.** A device that does not report a flag is not necessarily slower;
  it means the OEM did not declare the feature. So some fast phones receive the conservative path and
  no slow phone receives a broken instrument.
- **The flags are necessary, not sufficient.** They describe output latency, not touch-to-sound.
  Touch handling sits on top. Under G10 this stops mattering for Release 1.
- **Published crowdsourced data exists and is loose.** n-Track's chart carries 13,731 devices with
  the operator's own disclaimer that measurements are not scientifically accurate — different rooms,
  acoustics and volume settings — and its Android chart contains an entry labelled iPhone X. Grade
  **REPORTED**, never VERIFIED.
- **Market context (VERIFIED-EXTERNAL, 2026-08-01).** Statcounter: Samsung ≈33.8% (Feb 2026), Xiaomi
  ≈15.7% (early 2026). Omdia 2024: Samsung 39%, Motorola 25%, Apple 7%; sub-US$200 devices doubled
  in shipments to 41% of the total. An OLX national listing sample was pulled and is **not** a proxy
  for the installed base — relevance ranking rewards promotion spend and resale value, and iPhones
  dominated the sample against every market source. It is useful for acquisition pricing only.

**What follows (R75):** log both flags from day one. Within weeks of launch the real distribution is
known — not Brazil's, not OLX's, *ours* — which converts an ASSUMPTION into a MEASURED row at zero
cost and using data the app collects incidentally. No pre-launch device purchase is required, and
the one recommended in session is withdrawn.

---

## 9 · What is still open, stated honestly

**This session did not reach Fork B.** Several three-option forks were put and left unanswered while
the conversation moved. They are listed so they are not lost:

- The dropout question, opened by the founder's challenge and now **Fork J** (§11).
- Where advanced mode sits and whether it is free — **Fork E**, reshaped by R74 and not ruled.
- Who may hear the rough prototype audio — **INPUT-72**.
- **C21**, below: two estate documents disagree about whether D57 and D58 are decided.

---

## 10 · Deltas (continuing Game Addendum 01, which ends at D58)

**Proposed. Operative on founder ratification.** Both record rulings made in session.

| # | Delta | Was | Now |
|---|---|---|---|
| D59 | **Timing feedback is binary.** A generous window; no tiers, labels, or accuracy readout on any surface. Per-device calibration leaves Release 1 | Grading tightness open; Game Addendum 01 §10 flagged it as the cost-deciding decision | §1, §3, §4 |
| D60 | **The screen drum is scheduled, not triggered.** The app plays the correct part in time; the strike keeps it alive. The native low-latency engine leaves Release 1's critical path | Triggered sample playback assumed by Game Addendum 01 §6.4 | §1, §4 |

---

## 11 · Register additions (continuing Game Addendum 01, which ends at INPUT-71)

**Founder**

- **INPUT-72 · Who may hear the rough prototype audio?** Internal only (founder and Junior); internal
  plus Track B students, with one extra line in the written OK; or internal plus beginners recruited
  separately, leaving Track B clean. Touches both consent scope and Track B's purpose. Blocks §7's
  §9.3 pilot, not the recording itself.

**Contradiction**

- **C21 · D57 and D58: decided or proposed?** `GAME-CONVERSATION-CONTINUATION-PROMPT-FORK-B-ONWARD`
  §3 lists them under "decided and not up for renegotiation." `GAME-ADDENDUM-01` §12 lists them as
  proposed and operative only on ratification. They are the two items that add to Junior's shoot day
  — roughly eight solfejo passes and 20–40 minutes of samples. **One word from the founder closes
  it, and it should be closed before INPUT-57 is put to Junior**, since he is being asked to accept
  a day whose contents are not yet settled.

**New fork**

- **Fork J · Does the app ever remove support, and who fires it?** Opened by the founder's challenge
  that a dropout is built on removing the thing that works, delivers a report card rather than a
  reward, and is done *to* the student rather than chosen by him. Three positions were offered — out
  entirely, demoted to a student-pressed button, or settled by the rough recording — and none was
  taken. **Fork C's value depends on this**: if dropouts are out, breaks and turnarounds carry the
  game alone, and breaks cost roughly twelve additional passes and double Junior's shoot day.

**Existing items that change**

- **INPUT-64 — downgraded.** Comparison between students loses its enabling condition under G9; no
  precise comparable accuracy number will exist. Still open, no longer urgent.
- **INPUT-69 — softened, not closed.** See §4.
- **INPUT-58 — now answerable by performance** rather than by description. See §7, take 5.

---

## 12 · Recommendations (continuing Game Addendum 01, which ends at R72)

| # | Recommendation | Status |
|---|---|---|
| R73 | Read the timing grid from the authored render, never from audio peak detection. The backing is pre-rendered, so the grid is known; do not infer what was authored | Build-side, strong |
| R74 | **One surface, zone count as the dial** — one zone at the door, two, then three. Tap-along and the screen drum are the same instrument at different settings, not two builds. *Note: this inverts R70's sequencing if the dial is exposed at the free door. Fork E, not ruled here* | Recommendation |
| R75 | Log `android.hardware.audio.low_latency` and `android.hardware.audio.pro` from day one, so any Release 2 decision on triggered audio rests on our users' real device distribution | Build-side, near-zero cost |
| R76 | Run §7's six-take rough recording as soon as Junior's written OK exists. It answers INPUT-58 by performance, de-risks D57 before it is spent, and creates the audio half of the mockup that D36 requires | **Pre-mockup, strong** |

---

## 13 · Ledger implications (continuing Game Addendum 01, which ends at row 43)

No existing row's status changes.

| # | Claim | Status | Converts at | Required evidence |
|---|---|---|---|---|
| 44 | A generous binary window is device-tolerant enough that per-device calibration is unnecessary | HYPOTHESIS | Prototype | One low-tier Android device, one drummer, a working prototype. Cheap and available before M1 |
| 45 | Scheduled audio is experienced as playing rather than as miming | HYPOTHESIS | Prototype → M1 | §9.3's pilot questions; then voluntary second-round rate. **The honest risk in the architecture** |

Both rows have the same caveat as rows 38 and 41–43: Release 1 ships once, so they are recorded as a
designed first measurement rather than as anything a first cohort can prove.

---

## 14 · Risks added (continuing Game Addendum 01, which ends at #24)

**25 · The competence illusion.** Under G10 the part sounds correct whether or not the student's
hand is. He may feel he has the toque without having it, and — with no microphone (D26) and no
grading (G9) — **the app cannot tell and is not permitted to.** This is the price of the architecture
and it is paid deliberately. *Mitigation: the zone channel (§5) preserves stroke errors as audible;
the master's monthly listening cycle is the human check, and it is Release 2 / M3, which is the same
gap §6 finding 5 names.*

---

## 15 · What still must not be built — addition to Mandate 01 §10 and Addendum 01 §11

Items 1–7 (Mandate 01) and 8–10 (Addendum 01) stand unchanged. One addition:

11. **No timing accuracy readout, in any form, on any surface** — no tiers, no labels, no
    percentage, no "perfect/good/close," no per-strike marks, no session accuracy summary. The window
    is binary and its result is audible only (G9, §3).

---

*Game Addendum 02, 2026-08-01. Sits under `PRODUCT-GOALS-VNEXT-CONSOLIDATED-V2.md` and beside
`OPERATOR-MANDATE-01-ENGAGEMENT-2026-07-31.md`, `GAME-ADDENDUM-01-VOCALIZATION-AND-THE-SCREEN-DRUM-2026-07-31.md`,
`RELEASE-1-EXPERIENCE-SPEC-V1.md`, `PLAN-AMENDMENTS-FOR-V2_1.md` and
`RELEASE-1-ADDENDUM-SESSION-2-2026-07-31.md`. Nothing here is measured evidence. Deltas are proposed
and not operative until ratified. Every form question on sacred material is registered and reserved
to Junior, not resolved. Forks B through J are open and carried in the continuation prompt filed
beside this document.*
