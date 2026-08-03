# Opanijé — Game Conversation: Continuation Prompt, Fork J onward

**Written 2026-08-01, at the close of the session that produced
`GAME-ADDENDUM-02-THE-SCREEN-DRUM-ARCHITECTURE-2026-08-01.md`.**

**How to use this file.** Paste it, or point at it, to open the next session of the game
conversation. It is written to be read cold — with no memory of the sessions that produced it — and
it assumes only that the estate documents named in §2 are available. It supersedes
`GAME-CONVERSATION-CONTINUATION-PROMPT-FORK-B-ONWARD.md`, which should be read only for Fork B's
original framing.

---

## 1 · The instruction to open with

> You are a product manager contracted to Opanijé, a seed-stage company. Read the estate documents
> in §2, then take the forks in §4 in the order given. Forks A is closed — do not reopen it. **Work
> Fork J first**, and see §4's note on why the order changed.
>
> For each fork: state the question in plain language, then give **three options with pros and cons
> for each**. Do not decide anything reserved to Junior, to counsel, or to the founder — surface it
> as a numbered input instead. Propose deltas; do not treat them as operative until ratified.
>
> Before working a fork, say what you understand the situation to be and ask for an OK.

---

## 2 · What to read, and in what order

| # | Document | Why |
|---|---|---|
| 1 | `PRODUCT-GOALS-VNEXT-CONSOLIDATED-V2.md` | The plan of record. Red lines, the Room, the partition, the ledger, the risks |
| 2 | `OPERATOR-MANDATE-01-ENGAGEMENT-2026-07-31.md` | **Read before assuming anything is forbidden.** Opens the engagement toolkit; withdraws the prohibitions in its §2; its §4 and §10 are the real boundaries |
| 3 | `GAME-ADDENDUM-01-VOCALIZATION-AND-THE-SCREEN-DRUM-2026-07-31.md` | Vocalization as notation, the door, advanced mode, the shoot. **Its §6.4 assumes triggered sample playback and is superseded by D60** |
| 4 | `GAME-ADDENDUM-02-THE-SCREEN-DRUM-ARCHITECTURE-2026-08-01.md` | This session. G9, G10, the scope reduction, the research review's corrections, the rough recording, Fork J |
| 5 | `RELEASE-1-EXPERIENCE-SPEC-V1.md` | E1–E19, the student's path. Mandate 01 withdrew parts of §3 and §5 |
| 6 | `RELEASE-1-ADDENDUM-SESSION-2-2026-07-31.md` | §7 is the original seed. Its §7.1 and §7.8 prohibitions are **withdrawn** by Mandate 01 |
| 7 | `PLAN-AMENDMENTS-FOR-V2_1.md` | D28–D35, INPUT-52, R49–R54 |
| 8 | `OPANIJE-GAME-MECHANICS-RESEARCH-REVIEW-2026-07-31.md` | Hold & Rejoin and the audit of the first game proposal. **Post-Mandate-01, pre-Addendum-01** — it knows the toolkit is open and knows nothing of vocalization, the tap door, or the screen drum. Addendum 02 §6 states exactly what in it is right and what is wrong |
| 9 | `compass_artifact_...md` | The engagement-neuroscience research base. Pre-Mandate-01, so its "this product forbids streaks" framing is stale — the evidence in it is not |

**Two traps worth naming.**

- Documents 5, 6 and 9 state prohibitions Mandate 01 has since withdrawn. Read Mandate 01 second,
  always.
- **Document 3's §6.4 describes an audio architecture that no longer holds.** It assumes the screen
  produces sound by triggering samples on strike. D60 replaced that with scheduled playback. Reading
  §6.4 without Addendum 02 produces a wrong cost model and reintroduces a native audio engine the
  plan has just removed from Release 1.

---

## 3 · Where things stand

**Decided and not up for renegotiation:**

- The app opens rooms; it never moves the student into one (**D52**).
- Vocalization replaces Western notation product-wide (**D53**). Junior's solfejo carries **both
  rhythm and stroke** (FOUNDER-FACT, ledger row 40).
- Every room is entered voice → voice-over-battery → battery (**D54**).
- Tap-along ships as the door mechanic; the app measures the tap, never the voice (**D55**).
- Advanced mode ships: the screen drum, landscape, phone flat, two hands, zones named by the
  syllables (**D56**).
- Solfejo and the stroke sample library are on the M0 pre-shoot list (**D57, D58** — but see C21).
- **Timing feedback is binary. A generous window, no tiers, no labels, no accuracy readout anywhere
  (D59).**
- **The screen drum is scheduled, not triggered — the app plays the correct part in time and the
  strike keeps it alive (D60).**

**The architecture in one sentence:** *your finger keeps his groove alive; the drum tells you where
you are; the app never says.*

**The line that governs the engagement layer:** *the app never grades your drumming; it may
celebrate everything else.* Mandate 01 §4 and §10, plus three additions in Addendum 01 §11 and one in
Addendum 02 §15, are what actually binds.

**What got smaller this session, and it is the first time:** per-device calibration and the native
low-latency audio engine both left Release 1's critical path. Fork G lost its enabling condition.

**What is still growing:** Release 1 was roughly ten workstreams when risk #21 was written. It now
also carries store billing on two platforms, a play-layer subsystem, notification infrastructure,
celebration assets, a tap/screen-drum surface, and a voice-first entry sequence. The founder's rule
is one new standing obligation at a time. **Argue every addition against risk #21 — the failure mode
is not a bad Release 1, it is no Release 1.**

---

## 4 · The fork board

| Fork | Question | Status | Deadline |
|---|---|---|---|
| **A** | What "the app advances the student" means | **CLOSED — D52** | — |
| **J** | Does the app ever remove support, and who fires it | **OPEN — next** | Before Fork C |
| **C** | Does the break/turnaround variant get shot at M0 | OPEN — **now depends on J** | **Pre-shoot** |
| **B** | Where the first session ends | OPEN — reshaped by D59/D60 | Mockup |
| **E** | Where advanced mode sits, and whether it is free | OPEN — reshaped by R74 | Mockup |
| **H** | Does the engagement layer run on the free tier | OPEN | **Permanent once shipped** |
| **D** | What celebration is built on, and how the count-in survives wear | OPEN | Pre-shoot (partly) |
| **F** | Sharing and export | OPEN — larger under the Guitar Hero frame | Before any share surface |
| **G** | Comparison between students | OPEN but **downgraded** — G9 removes the comparable number | Mockup |
| **I** | Does the app ever listen | DEFERRED, deliberately | Release 2 |

**Why the order changed from the previous prompt.** That prompt put Fork B first, on the grounds
that first-session completion is a headline number and the mockup precedes the shoot. Both still
true. But **J is free and it prices C**, and C carries the only hard external deadline on the board —
roughly twelve additional passes that double Junior's shoot day, unrecoverable once the cameras
stop. Answering B before J means answering it against an unknown session architecture, since B's
third option *is* a dropout. The founder may reorder; this is a recommendation, not a ruling.

---

### Fork J — Does the app ever remove support, and who fires it *(work this first)*

**The question.** The Game Mechanics Research Review proposes Hold & Rejoin as the core game: the
reference part drops, the student continues, it returns, and he hears whether he stayed with it. The
founder challenged this in session on three grounds and the challenge holds up:

- **It removes the thing that works.** The strongest evidence in the base is that entraining to a
  real groove is intrinsically rewarding. A dropout takes the groove away to build a game out of its
  absence.
- **What returns is a report card, not a reward.** For a beginner it usually reads *you drifted*. The
  app never says it, so governance is clean — but the music-dropout literature is blunt that
  guilt-shaped motivation predicts quitting.
- **It is done *to* him.** R58 already frames fewer drums as exposure and *the student's move*. An
  app-fired dropout is the same exposure with autonomy removed, and autonomy is the best-supported
  lever available.

**What the research says back, and it does not simply agree.** Anticipation is where the pull lives
(Salimpoor 2011, MECHANISTIC); surprise is pleasurable only when you were confident beforehand
(Cheung 2019) and your beginner is not; curiosity pays only when the gap feels resolvable
(Gruber & Ranganath 2019). But Bjork's desirable difficulties cut the other way: the dropout is
probably a good *teaching* tool and a bad *day-one moment*. Both are true. The research narrows this
to **never let an unannounced gap land on someone who does not yet have the pattern** — it does not
say remove the gap.

**Three positions were offered in session and none was taken:**

1. **Out entirely.** No dropouts anywhere; the game is additive only — parts entering, calls, breaks.
   *Coherent, but the whole game then rests on breaks, which cost a shoot day and may not exist in
   these toques.*
2. **Demoted.** Never the core, never in session one, never fired by the app — available as a button
   the student presses when he wants exposure. *Fixes the autonomy problem, costs nothing to render,
   and §7.3 of the research review already proposes exactly this wording ("take more support away").
   Weakest as a designed moment.*
3. **Settled by the rough recording.** Takes 3, 4 and 5 of Addendum 02 §7 are two dropouts and a
   break. Play both to Junior and to one beginner and ask which makes them want to go again.
   *Cheapest answer, already scoped, no new cost. Costs a few days.*

Two further shapes were raised and are available inside any of the above: **fix the return** (Junior
counts the battery back in, so the gap becomes anticipation rather than absence — costs a few extra
count-ins at the shoot), and **gate it on the pattern** (nobody meets a dropout until behavioural
facts show they have been in the room enough times).

**Touches:** Fork C, R66, INPUT-58, ledger row 45, risk #25.

---

### Fork C — Does the break/turnaround variant get shot at M0

**Unchanged in substance, changed in weight.** If Fork J removes dropouts, breaks and turnarounds
become the *only* additive musical event the game has, and this fork stops being an enhancement and
becomes the game's existence condition.

**The prior question is free and is now answerable by performance rather than description:**
**INPUT-58** — do these toques carry breaks at all? Addendum 02 §7 take 5 asks Junior to play one.

**Cost:** roughly twelve additional passes on top of twelve — it doubles his day — and it is
unrecoverable once the shoot ends. Everything else the game needs is free at render time or cheap.
**Contrast this against every other item before committing it.**

**Note:** the free rhythm is permanent under E13, so whatever is rendered from it is committed
forever.

---

### Fork B — Where the first session ends *(reshaped)*

**What changed.** The surfaces are no longer four separate things. Under R74 the tap door and the
screen drum are one instrument at different zone counts, so the sequence is **voice → the zone dial →
the drum room**, and the "screen drum as a distant advanced mode" framing is weaker than it was.

**What did not change.** FF3's acceptance test is explicit: single-player adults and beginners who
cannot play to a metronome, **both able to play on day one**. First-session completion is one of
M1's two headline exit numbers.

**The three options, restated against the new architecture:**

1. **The session ends at the door** — voice and one zone, complete and self-contained, closing on the
   invitation to bring an instrument. *Arguably breaches FF3 for someone who already has sticks.*
2. **The session ends in the drum room, no perturbation.** *Safe middle; tests the central bet last,
   which may mean never.*
3. **The session ends on the peak event** — whatever Fork J leaves standing. *Puts the hardest thing
   in front of the least prepared person on the day the headline number is measured, and per Addendum
   02 §6 it stacks two session architectures into eight beats.*

**Also live:** E19's instrument question already routes people and may make this a two-answer fork.
And §9.3 of the research review offers a **measurement** route — a seven-question usability pilot,
non-statistical, possibly through Track B (INPUT-72) — so part of this need not be answered by
argument at all.

**Touches:** E4, E19, R70, R74, ledger rows 41 and 42.

---

### Fork E — Where advanced mode sits, and whether it is free

**Reshaped by R74.** If zone count is a dial on one surface rather than two products, the question
becomes *where on the dial the free door sits* rather than *is advanced mode free*.

**R70 recommends the screen sits behind the basic door** — voice, then tap, then drum, then more
zones — never as a shortcut past the instrument. **R74 puts pressure on that**, because a dial is
naturally exposed. Risk #23 is the honest version: a successful phone game whose users never buy an
instrument, never book a class and never go to Salvador inverts the funnel.

**The free-tier half is permanent** under red line #5 and E13 — including mechanics.

**Blocked on INPUT-69** — Junior's form assent on a glass surface standing in for a drum. Softened by
D59/D60 (it grades nobody and plays his correct part) but not closed. Shown as a working mockup,
never described.

---

### Fork H — Does the engagement layer run on the free tier

Mandate 01's INPUT-66 recommends yes: the free door is where first-session completion and day-7
return are measured. **Red line #5 makes anything given free permanent, including mechanics.** A
streak given free is a streak owed forever, as is whichever position on the zone dial sits free.

Interacts with Fork E's free half, Fork B's session-one scope, and E17.

---

### Fork D — Celebration and the count-in's wear

R60(b) chose the master's count-in; Deci 1999 supports the reward *class* strongly. But a count-in
fired on every advance becomes a jingle within a week, and Mandate 01 §4.4 forbids a synthetic
substitute, so the wear is unrecoverable. **R72 (shoot a bank of variants) mitigates and is available
only at the shoot.** Open: how often his voice fires, what carries the moments between, and whether
the biggest moments get a rarer asset.

---

### Fork F — Sharing and export

**Larger than it was.** The Guitar Hero framing makes the product more filmable, not less, and
advanced mode produces a shareable object as a byproduct. That is the only genuine spread lever in
the product — and it is a rights problem first: a video contains Junior's audio, on a platform red
line #6 cannot reach. **INPUT-71**, founder and counsel together. **R69 holds no share or export in
Release 1 until it is answered.**

---

### Fork G — Comparison between students *(downgraded)*

It was live because tap and screen-drum accuracy were precise comparable numbers. **Under D59 that
number does not exist.** INPUT-64 stays open and stops being urgent. Note that public absolute
ranking reduces perceived competence among weaker learners, which is the FF3 population.

---

### Fork I — Does the app ever listen *(deferred, deliberately)*

D26 removes the microphone from Release 1. Position reached: presence-plus-playback is the right
product and a deaf Release 1 is the right release. **Risk #25 sharpens this** — under scheduled audio
the part sounds correct regardless, so nothing in Release 1 can tell a student he has not got it.
Revisit with M1 data against R45/INPUT-49.

---

## 5 · The deadline that governs everything

**The M0 shoot.** D36 puts the mockup before the shoot so Junior sees working things rather than
descriptions. **Addendum 02 §6 adds that the mockup needs an audio half** — the questions reserved to
him are about sound and cannot be answered from a screen. R76's six-take rough recording is that
half, and it needs his written OK first (R55).

Near-zero cost while the cameras roll, impossible afterwards: consent scope for interactive/game use
· Junior's ruling on marking the name · isolated stems · the five-value partition item by item ·
entrance calls and count-ins · the welcome · the next-step invitation · **solfejo locked to the
battery** · **the stroke sample library** · **the count-in variant bank** · and, if Fork C says yes,
**the break/turnaround variants**.

**Four form questions must be in the mockup Junior sees**, gathered as one conversation: **INPUT-41**
(is a self-advancing ladder honest teaching), **INPUT-52** (the free rhythm's partition value),
**INPUT-62** (form assent on the engagement layer), **INPUT-69** (form assent on the screen drum).

**And one to ask before any of it: INPUT-36** — is vocalization genuinely this tradition's teaching
method? Everything since D53 rests on it. **It has been promoted to foundational and it has not yet
been asked.**

**One thing to close before INPUT-57 is put to Junior: C21.** Two estate documents disagree about
whether D57 and D58 are decided or proposed. He is being asked to accept a shoot day whose contents
are not settled.

---

## 6 · Numbering state

Continue from these. Do not renumber, do not reuse, do not renumber retroactively.

| Series | Last used | Next |
|---|---|---|
| Deltas | D60 | **D61** |
| Inputs | INPUT-72 | **INPUT-73** |
| Recommendations | R76 | **R77** |
| Ledger rows | 45 | **46** |
| Risks | #25 | **#26** |
| Experience decisions | E19 | **E20** |
| Game decisions | G10 | **G11** |
| Contradictions | C21 | **C22** |
| Forks | J | **K** |

**Open inputs currently blocking or promoted:** INPUT-36 (promoted to foundational — ask first),
INPUT-41, INPUT-52, INPUT-57, INPUT-58, INPUT-59 (enlarged), INPUT-62, INPUT-64 (downgraded),
INPUT-66, INPUT-67 (narrowed), INPUT-68, INPUT-69 (softened), INPUT-70, INPUT-71, INPUT-72.

**Open contradiction:** C21 (D57/D58 decided or proposed).

---

## 7 · Working method

**The founder's format.** Read the situation → ask for an OK → present questions with **three
options each, with pros and cons**. Plain language, and plainer when asked — he will ask for it
simpler and that request should be honoured without losing the substance. He is here to
conceptualize; technical decisions go to the build side and technical findings surface only when
they force a product-level fork. When they do, **surface them with the cost stated, not the
conclusion assumed** — the audio-latency question in Addendum 02 §8 dissolved once the platform's own
capability flags were read, and an afternoon of phone-buying was recommended before that check was
made. Check whether the platform already answers it.

**Epistemic discipline is load-bearing.** Every claim carries a label: RULED, REPORTED, ASSUMPTION,
HYPOTHESIS, MEASURED, FOUNDER-FACT, PM-ASSERTION, VERIFIED-EXTERNAL, VERIFIED-INTERNAL, ADOPTED,
FALSIFIED. **No ledger row upgrades without dated evidence.** Falsified rows are retained with the
work that would make them true named beside them. Note that the research review uses a *second*
label set (DIRECT-ADJACENT, TRANSFER, MECHANISTIC, HYPOTHESIS) — either map it or adopt it as a
research-provenance sub-scale, but do not run two systems unremarked.

**Deltas are proposed; the founder ratifies.** Operator mandates are the exception — founder-issued
and operative on issue.

**Open inputs are reserved** to the founder, Junior, or counsel. Never resolve one unilaterally.

**The standing resource rule (S7):** always choose the option cheaper in other people's time and more
expensive in Junior's own hours. He is a co-founder. But S7 says spend his hours, not spend them
without asking — every item that costs him a shoot day is an input, not an assumption.

**The founder's operating rule:** one new standing obligation at a time. Load-bearing in every
sequencing decision, and Release 1 is carrying more than it was two days ago.

**Two numbers judge every game element:** first-session completion and day-7 return. Argue against
those, not against whether something is fun.

**And the honest caveat to carry into any engagement argument:** the research base narrows the design
space and does not choose the product. Gamification effects are positive on average, heterogeneous,
and often small. Nothing should be built because it worked in a paper. There is almost no
high-quality evidence for a single-player, microphone-free, culturally governed percussion practice
product — so the product still has to be measured.

---

*Continuation prompt, 2026-08-01. Supersedes
`GAME-CONVERSATION-CONTINUATION-PROMPT-FORK-B-ONWARD.md`. Companion to
`GAME-ADDENDUM-02-THE-SCREEN-DRUM-ARCHITECTURE-2026-08-01.md`. Fork A is closed. Forks B through J
are open, with **J first because it prices C**, C carrying the hardest deadline because the cameras
stop, and H because red line #5 makes it permanent.*
