# Opanijé — the document estate

**Opanijé** is a mobile app for learning and practicing Afro-Brazilian percussion — primarily
Candomblé rhythms of the Ketu tradition, rooted in Salvador, Bahia — for Brazilian practitioners and
international learners alike.

This repository is not code. It is the company's **document estate**: the charter, the plan of record,
the registers of every decision and open question, and the session history that produced them.

**Restructured 2026-08-03 under D83.** Session prose used to be the register of record; it no longer
is. The registers are.

**The working set is four documents, not thirty-two.** `CHARTER.md` (two pages, what cannot change),
[`AS-BUILT.md`](AS-BUILT.md) (what exists), [`BUILD-LOG.md`](BUILD-LOG.md) (what was decided) and
[`plans/`](plans/) (what to do). That is roughly 30,000 words and it is everything a planner needs.
Everything else on this page is history, kept because it is auditable — not because it must be read.

**The estate stopped being the work on 2026-08-05.** D84–D103 were put to the founder and returned
the same day — seventeen ratified, one rejected, one deferred, one held. D88 puts the register
apparatus into maintenance mode: most of `registers/` is now frozen history, and build decisions go
to [`BUILD-LOG.md`](BUILD-LOG.md). On the same day the company's **first MEASURED ledger row**
arrived from a physical-device test, and it is **FALSIFIED** — a first-time user could not work out
what to do (row 59). The founder then **suspended the tester programme and ordered the tester-facing
surface redone** (`BUILD-LOG.md`). Start at [`plans/`](plans/), not here.

**Compacted the same day.** Twelve documents of 2026-08-05 recon and compaction (96,089 words) were
folded into `AS-BUILT.md` and removed; they are recoverable from git history at `e38917a`. The estate
went from **267,697 words across 50 documents to 176,379 across 39** and lost nothing that was not
duplicated elsewhere in it.

---

## Start here

| If you want… | Read |
|---|---|
| **What to actually do next** | [`plans/`](plans/) — five documents: the ratified decisions, the five-stage build plan, a day-by-day runbook, and the scoreboard. **Written 2026-08-05, and the only part of this estate that is a plan of execution.** |
| **What has been decided since the freeze** | [`BUILD-LOG.md`](BUILD-LOG.md) — the ratification record, the founder's rulings, and the first device evidence |
| **What actually exists — the code, the site, the assets** | [`AS-BUILT.md`](AS-BUILT.md) — verified 2026-08-05. **Read this before planning anything.** It also lists the nine claims a plan got wrong, so nobody re-derives them |
| **What can never change** | [`CHARTER.md`](CHARTER.md) — the one law, six red lines, the partition, the two ledgers, the grading constitution, the vocabulary rule |
| **What is open right now** | [`BACKLOG.md`](BACKLOG.md) — every open item, door-labelled, by owner |
| **How the estate works** | [`METHOD.md`](METHOD.md) — epistemic labels, one-way/two-way doors, the monthly decision hour, numbering, session format |
| **What the game is** | [`plan/THE-GAME.md`](plan/THE-GAME.md) — the assembled specification |
| **What happens in what order** | [`plan/ROADMAP.md`](plan/ROADMAP.md) |
| **The current state of any numbered item** | [`registers/`](registers/) |
| **Why something was decided** | [`sessions/`](sessions/) — history, not the register |

**Read the Charter before proposing anything.** It is two pages and it is the whole of what cannot be
traded away.

---

## The product, in one paragraph

The core thesis is that **intrinsic motivation — anchored to real named masters, musical groove, and
lineage transmission — can outperform extrinsic engagement mechanics.** The student vocalizes a part,
taps it, then plays it on a screen drum, inside a battery every drum of which is played by one master.
The app never says the student is ready, correct, or good; it opens rooms on facts, renders musical
consequences in sound, and reserves every judgment about a person to a human who says their name.

**The one law: access is bought; standing is only earned.**

---

## The people

**Rodolfo** — founder. Decides price, product name, brand and voice, which traditions and masters are
invited, every business term, and form on secular material. He is here to conceptualize; technical
decisions go to the build side and surface only when they force a product-level fork.

**Junior** — co-founder and sole percussion master for Release 1. Governs all sacred material under
red line #1 — and that is a **governance gate, not a consultation**. He records every drum part
himself, layered; there is no ensemble at this point (S6). Standing resource rule: always choose the
option cheaper in people and more expensive in Junior's own hours (S7).

**Vanderson ("Macumbinho")** — second master, content and delivery contributor. Confirmed out of
Release 1; his inclusion in later releases is an open question.

---

## Where things stand — 2026-08-03

**The game exists now, and it is legible.** Addendum 04 answered the founder's question — how to grade
students without negative or frustrating classification — by separating four things the estate had
collapsed into one: *measurement*, *feedback*, *grading*, and *classification*. Only classification
was ever the danger, and only classification is barred. A game grades the run, never the player.

What follows from that:

- **The drum always sounds** (D77). In-window strikes keep the master's correct part alive;
  out-of-window and wrong-zone strikes fire a real one-shot of the student's actual hit — because a
  real drum struck off-time still sounds.
- **There is no fail state anywhere** (D78). The part thins when unfed and returns when fed. You
  cannot lose; you can only be more or less present in the music.
- **After the round, three facts and one personal best** (D79 — **RATIFIED**). Self-referenced,
  monotonic, per-setting. A number that only ever rises cannot humiliate.
- **The echo loop is the micro-game** (D74) — the teaching voice withdraws and returns, which is the
  tradition's own method rather than a mechanic invented for it (G20, MASTER-CONFIRMED).
- **The repertoire arc is the macro-game** (D75). The map is a city of rhythms, not a difficulty grid.

**The business shape moved too.** The commons is free and scarcity is priced (D73). The notation
system will be published openly as a **standard** for teaching Afro-Brazilian percussion, and Opanijé
positions as a music-education company (G22) — which reversed the estate's own "free screen drum is
value leakage" critique: giving the instrument away *is* the distribution strategy. Breaks are
deferred (G24), freeing shoot capacity that now buys commons rhythms instead (R88). The master's
monthly listening cycle enters Release 1 as **operations, not build** (D81) — an appointment the app
carries, with submission over ordinary channels so the no-microphone cut (D26) stays intact.

**What is not true yet.** Nothing in this estate carries the label **MEASURED**. Not one row. The
ledger exists to keep that fact visible, and Track B — ten hand-booked private classes — is the
cheapest path to changing it.

---

## The three deadlines that govern sequencing

1. **Escrow, today.** Signing keystore and repository key off-box, backup passphrase restored. One
   machine currently holds the code, every credential, the backup key and the signing key, with no
   standby. Hours of work; it outranks everything (D16, risk #16, INPUT-44).
2. **The M0 shoot.** The cameras stop. Decisions are ranked by what cannot be recovered afterward, not
   by perceived value. Consent scope and item-by-item partition capture are the least recoverable and
   the cheapest. See [`plan/M0-SHOOT.md`](plan/M0-SHOOT.md).
3. **The GUI industrial design filing**, time-critical **before any screens go public** — and a mockup
   is being built.

---

## What is open, in one glance

- **Junior owes:** the classroom transcription (INPUT-78) and form assent on the rendered echo
  (INPUT-79) — together these specify and sanction the micro-game; plus the stroke library, the stroke
  vocabulary, partition capture, the reference-dialect confirmation, and the mockup conversation.
- **The founder owes:** the commons list (INPUT-80 — **one-way**, red line #5 makes it permanent), the
  count-in variant count (INPUT-74), the vocabulary sheet (INPUT-81), the cycle's go/no-go (INPUT-82),
  and confirmation of one derived reading of his own ruling (INPUT-84).
- **Founder and counsel owe:** publication scope, licence, timing, and the positioning's effect on the
  trademark strategy (INPUT-83).
- **Two forks are open:** Fork L — does visible sustain survive contact with students? Ratified now,
  tested at the pilot and M1, reversed without cost if ledger row 49 fails. And Fork E's free half —
  where on the dial the free door sits, blocked on INPUT-69.
- **One contradiction is open: C23.** E2's named presence was voided by D38 (Junior alone, layered),
  its replacement left open at INPUT-61 — and Addendum 04's presence lamp then builds on E2 as though
  it were live. Found during this restructure; recorded, not resolved.

Full detail, with door labels and blocking gates, in [`BACKLOG.md`](BACKLOG.md).

---

## Repository map

```
CHARTER.md          what cannot change
BACKLOG.md          what is open, door-labelled, by owner
METHOD.md           how the estate works

registers/          the register of record — current state of every numbered series
  DECISIONS.md        rulings A, session decisions S, game decisions G, experience decisions E
  DELTAS.md           D1–D83 — proposed changes and their ratification state
  INPUTS.md           INPUT-1–84 — questions reserved to a named human
  RECOMMENDATIONS.md  R1–R88 — the PM's advice, and whether it was taken
  LEDGER.md           rows 1–51 — load-bearing claims and what would convert them
  RISKS.md            #1–#29
  FORKS.md            the fork board, A–L
  CONTRADICTIONS.md   C1–C23 and their dispositions
  NUMBERING.md        next number in every series; known gaps
  CHARTER-PROVENANCE.md  exact sources behind the Charter, and what the estate cites but no longer holds

plan/               what is being built
  PRODUCT-GOALS-VNEXT-CONSOLIDATED-V2.md   the plan of record
  THE-GAME.md                              the assembled game specification
  M0-SHOOT.md                              the capture manifest — every item one-way
  PRICING-AND-ACCESS.md                    commons free, scarcity priced, and the cycle
  THE-STANDARD.md                          the publication workstream
  ROADMAP.md                               the sequence, and why that sequence
  RELEASE-1-EXPERIENCE-SPEC-V1.md          the student's path, end to end
  OPERATOR-MANDATE-01-ENGAGEMENT-*.md      the engagement toolkit, and its four charter boundaries

research/           the evidence base — narrows the design space, does not choose the product
sessions/           the reasoning that produced all of the above; history, not the register
```

---

## Working with this estate

**Every claim carries an epistemic label.** RULED, MASTER-CONFIRMED, FOUNDER-FACT, ADOPTED,
ASSUMPTION, HYPOTHESIS, MEASURED, FALSIFIED and the rest are defined in [`METHOD.md`](METHOD.md) §1.
**No row upgrades without dated evidence.** Never upgrade a label to make a plan read better.

**Deltas are proposed; the founder ratifies.** Operator mandates are the one exception — founder-issued
and operative on issue.

**Open inputs are reserved.** Never resolve one unilaterally. Where a terse answer must be interpreted,
write the interpretation down as a confirm-or-correct row with the cost of being wrong stated.

**Questions to the founder come as three options with pros and cons.** Plain language, and plainer when
asked.

**Nothing should be built because it worked in a paper.** The research base narrows the design space
and does not choose the product; gamification effects are positive on average, heterogeneous, and often
small. There is almost no high-quality evidence for a single-player, microphone-free, culturally
governed percussion practice product. The product still has to be measured.

---

*Estate restructured 2026-08-03 under D83 (Game Addendum 04 §7). Nothing in this repository is measured
evidence unless a ledger row says MEASURED — and as of this date, none does.*
