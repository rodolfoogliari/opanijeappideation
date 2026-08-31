# Opanijé — Build Log

**Status.** Register of record for build decisions, opened 2026-08-05 under **D88**.
**Rule.** Append-only. One line per decision: date, decision, door label. Never rewritten.

**Why this file exists.** D88 puts the estate's register apparatus into maintenance mode.
`CHARTER.md`, the vocabulary sheet (METHOD §5), the Charter §9 prohibition list and
`registers/LEDGER.md` stay alive. `DELTAS.md`, `RECOMMENDATIONS.md`, `CONTRADICTIONS.md`,
`FORKS.md` and `sessions/` freeze as history. From this date a build decision that would once have
become a numbered delta becomes **one line here** instead.

D84–D103 are the last block to enter `DELTAS.md`, because they were numbered for it before D88 took
effect. Everything after them lands on this page.

---

## 2026-08-05 — Ratification of D84–D103

Put to the founder as `plans/PLAN-00-DECISIONS.md` §8. Returned the same day.
**Seventeen ratified, one rejected, one deferred, and one split into a ratified half and a
scheduled half.**

```
D84  monthly cycle out of R1                 [x] RATIFIED  2026-08-05
D85  standard frozen                         [x] RATIFIED  2026-08-05
D86  lean Capture Day replaces M0 shoot      [x] RATIFIED  2026-08-05   ← one-way parts intact
D87  app sells nothing                       [x] RATIFIED  2026-08-05
D88  registers to maintenance mode           [x] RATIFIED  2026-08-05
D89  opanije-room is the product             [x] RATIFIED  2026-08-05   ← ONE-WAY
D90  opanije-mobile is a parts donor         [x] RATIFIED  2026-08-05
D91  mu-plugin rail is the backend           [x] RATIFIED  2026-08-05   ← ONE-WAY
D92  bundle id com.opanije.room              [x] RATIFIED  2026-08-05   ← ONE-WAY at publish
D93  seams unwired until Stage 4             [x] RATIFIED  2026-08-05
D94  play layer ships ON                     [~] SPLIT     — D94a RATIFIED, D94b PENDING
D95  fade stays binary for R1                [x] RATIFIED  2026-08-05
D96  web room is the iOS strategy            [x] REJECTED  2026-08-05   ← founder ruling
D97  per-course purchases from day one       [x] RATIFIED  2026-08-05
D98  release keystore + escrow before upload [x] DEFERRED  2026-08-05   ← founder ruling
D99  two physical handsets before ship       [x] RATIFIED  2026-08-05   ← partly executed, see below
D100 audio provenance stays enforced         [x] RATIFIED  2026-08-05
D101 createFakeRoomAudio behind dev guard    [x] RATIFIED  2026-08-05
D102 verify-apk.sh extends to bundle*        [x] RATIFIED  2026-08-05
D103 ten testers before the design filing    [x] RATIFIED  2026-08-05   ← founder accepted the risk
```

### The three that did not simply ratify

**D94 — SPLIT, and the ratified half is live.** The founder asked for a fuller account before
ruling, then ratified a split of the decision into its reversible and irreversible halves. D94 as
written bundled two commitments that do not have to be taken together, and only one of them is
one-way.

| | Ruling | Door |
|---|---|---|
| **D94a** — the play layer is ON in **tester builds**: Junior's Day 10 sitting and Stage 2's ten testers | **RATIFIED 2026-08-05** | **TWO-WAY.** Red line #5 makes permanent what is *given to the free tier*; a build handed to named individuals is not the free tier, is not published, and can be withdrawn by not issuing the next one. **The door label rests on that and on nothing else** |
| **D94b** — the play layer default flips ON in the **public free room** | **PENDING — scheduled for Stage 3** | **ONE-WAY.** Red line #5 attaches: the free room would keep the echo loop, the fade and the closing facts permanently |

**Why the split holds.** Every piece of evidence D94b needs is produced by D94a. Row 52 (Junior's
verdict on whether the play layer reads as musical information or as a verdict on the player), row 53
(the fade), row 55 (≥7/10 to the screen drum) and Junior's form assent under INPUT-79 all come from
ten sideloaded testers and one sitting — none of which touches the free tier. D94b is then taken at
Stage 3 with that evidence in hand rather than in advance of it.

> **A correction to an earlier draft of this entry, kept visible.** It justified D94a's TWO-WAY door
> partly by citing D103 — *"D103 already ruled this cohort is not 'public'"*. That was importing a
> ruling outside its scope: D103 ruled on **disclosure novelty for the industrial-design filing**, not
> on red line #5's permanence test. The two questions share a cohort and nothing else. D94a's door
> label stands on red line #5's own terms, above.

**Charter §9 item 10 is discharged early rather than deferred.** Junior sees the play layer at the
Day 10 sitting under D94a, which is *before* any public ship — so the gate that governs D94b is
already satisfied when D94b comes up.

**D94a is not free of code, and the reason is load-bearing.** `EXPO_PUBLIC_ROOM_DEMO=1` — the
existing opt-in, and the one `plans/PLAN-02-RUNBOOK.md` Day 2 already uses — sets **two** gates, not
one: `playLayerEnabled` (`AppRuntime.tsx:241`) **and** the demonstration route tree
`REVIEW_ROUTE_TREE = ['review', 'past-the-door']` (`_layout.tsx:48`, `routeTree.ts:8`).
`scripts/build-room-apk.sh:63-64` states the constraint in its own words: those surfaces *"are gated
off by default and must stay that way in anything a student could receive."*

A `ROOM_DEMO=1` build therefore hands ten testers the play layer **and** `/review` and INPUT-62's
past-the-door proposal. **D94a's scope is to separate the two gates** — the play layer gets its own
build-time opt-in, independent of the demonstration route tree — after which tester APKs carry the
play layer with the review surfaces off. That is the whole of D94a's code, and it is bounded.

**D96 — REJECTED.** The web room is *not* adopted as the iOS strategy and *not* adopted as the
primary distribution surface. Founder ruling, no reason recorded, and none is owed. Consequences are
recorded as risk #36 and INPUT-90 rather than argued here: Release 1 has **no iOS path** and **no
no-install tap-to-play surface**, which changes what Junior's voice note can point at. The web export
itself is not prohibited by this ruling — only its promotion to strategy.

**D98 — DEFERRED.** The production release keystore and the escrow event are postponed, not
cancelled. Two consequences follow mechanically and are recorded as risk #37: **no store upload is
possible until it closes**, and the single-machine total-loss exposure that D16 has carried as the
estate's highest-ranked overdue item **stays open**. `PLAN-02-RUNBOOK.md` Day 1 is amended
accordingly.

---

## 2026-08-05 — Founder rulings taken alongside the block

| Item | Ruling | Register |
|---|---|---|
| The free set — what is given away permanently under red line #5 | **Ijexá, two parts (agogô + one drum part), two speeds.** Confirmed now | Answers INPUT-86 / INPUT-80. **ONE-WAY.** The *"with the play layer on"* clause is carried by **D94b** and settled at Stage 3 with rows 52 and 55 in hand — D94a does not touch the free set. |
| Capture kit — USB interface, two mics, stands, headphones | **Approved, ~R$2–3k**, inside the existing M0 earmark. Reserve floor R$5,000 untouched. | The one operator spend consent in the plan set |
| GUI design filing vs the R$5k floor (R37) | **Accept the risk and ship** if counsel's quote breaches the floor | Founder call, taken |
| GPL v3 vs relicensing the app subtree | **Goes to counsel** in the single combined brief, week 1 | INPUT-85 routed |
| Ten NDA-free testers before the design filing | **Risk accepted** | = D103 RATIFIED |

---

## 2026-08-05 — First device evidence, and it is negative

**Reported by the founder.** A physical-device test has been run — the D99 work is therefore partly
executed, and `ACCEPTANCE.md:29` criterion 1 is no longer wholly BLOCKED. **The result is the first
primary evidence in the company's history, and it fails.**

> The tester did not understand what to do. There was no gamified mechanic. They did not understand
> how to interact at all. **0/10.**

Recorded as **ledger row 59 — FALSIFIED, n=1, 2026-08-05** — and as **risk #35**.

**Corrected 2026-08-05 after review: this row is not MEASURED and must not be cited as such.**
`METHOD.md` §1 reserves MEASURED for completed transactions or observed cohorts; this is one
founder-reported session with no device, build SHA or protocol recorded. **FALSIFIED is earned and is
the stronger claim anyway** — the row asserts something universal ("self-explanatory to an unaided
first-time user") and one counterexample refutes a universal. What a single tester cannot establish
is the positive.

**Three things this does and does not mean, kept separate on purpose.**

1. **It is real and it is dated.** Under METHOD's honesty rules an honest FALSIFIED outranks a
   hopeful assumption. It is the first row in 52 to carry a status won by contact with a human
   outside the estate, and it arrived as a negative. That is the register working, not failing.

2. **It does not close row 55.** Row 55 is defined as ten beginners on a play-layer-**on** build,
   observed, target ≥7/10. This was one tester on a play-layer-**off** build. It is a precursor
   signal on Gate 1, not Gate 1 firing. Do not record it as though row 55 has been measured, and do
   not let it be argued away either.

3. **"There was no gamified mechanic" is a literal description of the shipped build, not an opinion
   about the design.** *(This finding is what D94a now answers: the next tester holds a build with
   the play layer on.)* `playLayerEnabled` (`AppRuntime.tsx:239-242`) is false unless `__DEV__` or
   `EXPO_PUBLIC_ROOM_DEMO` is set. The tester was handed the drum toy. The echo loop, the
   fade-and-rejoin and the three-facts closing screen — the entire game the estate spent 145,680
   words inventing — were switched off in the artifact they held. **This is the single strongest
   piece of evidence bearing on D94, and it arrived from outside the estate.**

**What it does not excuse.** "Did not understand how to interact at all" is a finding about the
*door*, and the door is only partly the play layer's job. A first-time user who cannot tell what to
touch is a first-session failure whether or not the game is on. Both fixes are needed and they are
not the same fix.

---


---

## 2026-08-05 (later) — The tester programme is suspended and the tester-facing surface is redone

**Founder ruling, following ledger row 59.**

> The feedback was so negative that we are not going to test now. The interface, the UI/UX and all
> tester-facing parts of the app are going to be redone and deeply reviewed.

**This answers INPUT-92** — the question of how much Release 1 scope the door redesign gets. The
answer is: whatever it needs, and it precedes testing rather than fitting around it. INPUT-92 is
closed by this ruling.

### What is suspended

| | Status |
|---|---|
| **Stage 2's ten-tester cohort** | **SUSPENDED**, not cancelled. No hand-picked tester receives a build until the redesigned surface exists |
| **Ledger row 55** (≥7/10 to the screen drum) | Cannot be measured. It was always defined on ten testers; there are now none scheduled. **It stays HYPOTHESIS — do not mark it blocked, it is simply not yet testable** |
| **Rows 48 and 50** (HYPOTHESIS) and **rows 53 and 58** (HYPOTHESIS as corrected 2026-08-05) | Same — all Stage 2 instruments, none measurable meanwhile |
| **D103** (ten testers before the design filing) | Ratified and unspent. The accepted risk stands; nothing is currently drawing on it |
| **D99's second handset** | Not urgent while nobody is testing. The founder's own device remains the build-check surface |

### What is not suspended, and this is the important half

**Capture Day and the audio pipeline proceed.** They are governed by Junior's availability and by
irrecoverability, not by the interface. Audio is independent of the surface being redone, and
deferring the shoot to wait for a redesign would spend the one resource that cannot be recovered
(INPUT-89's consent scope, the partition in his words) to protect one that can. **Stages 0 and 1 run
unchanged.**

**D94a keeps its purpose and gains urgency.** The redesigned surface must be designed *with* the play
layer on, not with it off and the layer added afterwards — the whole finding of row 59 is that the
product without it reads as nothing. The gate-separation work (`EXPO_PUBLIC_ROOM_DEMO` setting both
`playLayerEnabled` and the review route tree) is now a precondition of the redesign rather than of a
tester handout.

**D94b is unaffected.** It was already scheduled for Stage 3, and it now waits on a redesigned
surface as well as on rows 52 and 55.

### Junior is inside the redesign, not a reviewer after it

Charter §9 item 10 — no screen-drum surface ships without Junior having seen it — is a **ship** gate,
not a design gate, so it does not compel a sitting during the redesign. But `ACCEPTANCE.md:39` and
the estate's own repeated finding is that **he answers around working objects, not around
documents**. Showing him a surface that is about to be discarded spends his scarcest resource on a
throwaway; showing him nothing until it is finished risks discovering at the end that the form is
wrong.

**The build-side call, recorded here rather than put to the founder:** Junior sees the redesign at
the point where it is playable but still cheap to change — not the current build, and not a finished
one. His Day 10 sitting in `PLAN-02-RUNBOOK.md` moves with the redesign rather than staying on its
original date. INPUT-69, 79, 41, 62 and 88 travel with it.

### The plan gains a stage

**Stage R — the tester-facing surface**, between Stage 1 and Stage 2. It is lettered rather than
numbered deliberately: inserting a "Stage 2" would renumber every stage after it, and `NUMBERING.md`'s
rule that a gap is cheaper than a collision applies to plan structure as much as to registers.

Recorded as **ledger row 60** (the redesigned door is self-explanatory — the row that replaces 59's
falsification when it is re-measured) and **risk #38** (a redesign with no measurement loop repeats
the failure it exists to fix).

---

## 2026-08-05 (later) — The estate is compacted

**Founder instruction.** The 2026-08-05 recon and verification set was folded into the base documents
so a planner or refactor consumes fewer tokens.

**Removed — twelve files, 96,089 words:** `MASTER-BRIEF.md`, `FABLE-PLAN.md`, `VERIFICATION.md`, and
`compacted/A`–`I`. **They are recoverable from git history at commit `e38917a`.**

**Why it is safe.** `MASTER-BRIEF.md` and `compacted/A`–`G` were compactions of documents that sit in
this same repository — they duplicated `README`, `CHARTER`, `plan/`, `registers/`, `sessions/` and
`research/` rather than adding to them. `FABLE-PLAN.md`'s surviving conclusions are already carried by
`plans/`, which was written from it and then corrected against the code. Only three of the twelve held
original material: `VERIFICATION.md` and `compacted/H`–`I`.

**Added — one file:** **`AS-BUILT.md`**, carrying the unique findings from those three plus the nine
wrong claims, so that no future plan re-derives them.

**The first pass of it was lossy, and an audit caught that.** Comparing every distinctive identifier
and figure in the deleted set against the surviving tree found material genuinely gone rather than
merely restated. Restored: Room's 21-document inventory — including **`docs/MOCKUP-QUESTIONS.md`, an
existing 12-step script for the session with Junior that Stage R should start from rather than
rewrite**, and `docs/review/`'s 8 adversarial rounds; the VPS capacity envelope and what it can and
cannot host; the *"do not restart"* salvage verdict; and the live site's deployment debris. Left
dropped deliberately: per-file byte sizes, theme filenames, the full immersion price matrix, and
workstation build-trap detail that lives in the machine's own `CLAUDE.md`.

**The claim to make about this compaction is therefore the narrower one:** no load-bearing fact was
lost, and everything is recoverable at `e38917a`. Not "nothing was dropped" — things were, and they
were chosen.

**Net: the estate goes from 267,697 words across 50 documents to 182,407 across 39 — a 34% cut — and
loses no load-bearing fact that is not either duplicated elsewhere in it or preserved in git.**
Measured, not estimated: 96,089 words removed, 5577 added. `AS-BUILT.md` is not a register and takes no numbered rows.

*A caution for whoever reads this next:* the deleted set is where the estate's own compaction lived.
If a future session wants the 32-document estate summarised again, **it should not regenerate it** —
it should read the working set: `CHARTER.md`, `METHOD.md` (§1's status labels and §5's vocabulary
sheet — the ledger is unreadable without the first, and Stage R has no wording rule without the
second), `AS-BUILT.md`, `BUILD-LOG.md`, `plans/`, and `registers/INPUTS.md` (the plans cite INPUT
numbers constantly and this is the only place their text lives). **38,887 words.**

*An audit of the first version of this compaction found the four-document set could not answer its
own assignments — it excluded every status-label definition, the vocabulary sheet binding every
user-facing string Stage R will rewrite, and the text of the five INPUTs that travel with Junior's
sitting. The set above is the corrected one.*

---

## 2026-08-05 (later) — Known stale, deliberately not edited

Recorded rather than silently repaired.

**`CHARTER.md` was stale in three places, and the founder ratified the amendment.** Recorded here
first as an operator decision, then taken: the founder authorised the edit explicitly on 2026-08-05.
It is issued as **D104**.

| Where | Was | Now |
|---|---|---|
| §2 | Item-by-item capture happens "at the **M0 shoot**" | "on the **capture day**" — D86 replaced the full production shoot with a lean one-day capture. What must be captured is unchanged; item-by-item partition capture remains one of the four one-way parts a lean day may not skip |
| §9 | "build it, put it in the **mockup**, and take it to Junior" | "put it in the **app**" — D89 ruled `apps/opanije-room` is the product. The instruction is unchanged, only the word |
| §10 | The one-obligation rule "**is** genuinely strained by the monthly cycle (D81)" | "**was** … for Release 1 the strain is removed" — D84 took the cycle out of R1 and answered INPUT-82 NO-GO. **Risk #29 is retained rather than retired**, because the strain returns with the cycle at 100 weekly actives |

**Three procedural points, because amending a constitutional document is where process earns its
keep.**

1. **Explicit founder ratification was obtained** — §11 requires it and nothing less would do.
2. **Junior's sign-off was not required and was not sought.** Red line #1 attaches where *sacred
   material's form* is touched. None of the three edits touches form, the partition, or any mechanic
   on sacred material; they are citation corrections following decisions already ratified.
3. **It had to be a delta, and that reopened a register D88 had just closed.** §11: *"a delta that
   would change this file must say so in its own text"*, and the Charter governs any disagreement —
   so a Charter amendment cannot be a BUILD-LOG line. **D104 is therefore the single exception to
   D88's freeze**, and `DELTAS.md` now stands closed to everything except Charter amendments. The
   next such delta is D105.

**What was deliberately not touched:** no red line, the one law, the partition, the two ledgers, the
grading constitution, the vocabulary rule, the authority table, or §9's prohibition list. The Charter
now carries its own amendment history at §11.

**`plan/` (singular) was not reconciled.** Its eight documents are the 2026-07/08 estate and none of
them knows about the ratification — `ROADMAP.md` still carries the old sequence, and
`PRODUCT-GOALS-VNEXT-CONSOLIDATED-V2.md` carries a VPS disk figure (73% full) that `AS-BUILT.md`
supersedes (77%). They are **history under D88** and rewriting history is what this estate's own
rules forbid. `README.md` now disambiguates `plan/` from `plans/` and says which wins.

**`BACKLOG.md` was not reconciled item-by-item.** It carries a staleness banner naming exactly what
it does not know. Reconciling it is itself an open task, and it is a real one: `README.md` routes
"what is open right now" there.

---

## 2026-08-15 — Capture Day production pack authored

2026-08-15 — `plan/M0-PRODUCTION-PACK.md` created: run-of-show, deliverable spec, ingest/backup rule, in-room decision card (INPUT-23, INPUT-70) and consent-execution checklist for the lean Capture Day (D86). A new dated document; no existing register or `plan/` file edited. Logistics only — it decides nothing and closes no input. TWO-WAY.

---

## 2026-08-15 — Ratification sweep: the founder's 2026-08-14 rulings

Made in real operator turns during the 2026-08-14 workstation session (the mission-control board
session) and carried here by that session's handoff record; this entry is the estate's durable copy.
Nothing below issues a decision — this entry **records** rulings already made. The INPUT rows it
names are updated in `registers/INPUTS.md` in the same commit; the frozen registers are cited,
never edited.

- **Consent scope — ALL AGREED, ratified by all parties.** Every use tier granted — playable-inside,
  gamifiable, teachable, archive — with vocalizations covered **distinctly from speech**. INPUT-22 is
  ANSWERED YES; no amend-and-re-consent cycle is needed before recording. What survives: INPUT-89's
  instrument wording must name **vocalizations** explicitly rather than leaning on "voice"; INPUT-23
  (stems) stays open and is decided in the room, on the day. Door: ONE-WAY (consent scope). D86's
  lean Capture Day keeps all four one-way parts; this ruling clears the first of them.
- **The commons is three rhythms: ijexá, congo, cabila.** Expands INPUT-80/INPUT-86's Ijexá-only
  answer at rhythm level — the direction red line #5 permits (the house may give more, never less).
  Junior's availability-and-teaching-order confirmation stays open for congo and cabila. Door:
  ONE-WAY (red line #5 — permanent).
- **The cycle is quarterly at R$97/quarter**, billed quarterly, Pix/Mercado Pago; founding members
  keep the rate. Delegated to the lead, decided, and Junior ratified. Supersedes D84's monthly-shape
  premise in part; the submission channel is the one open item. **Not addressed by the ruling and
  flagged back to the founder in one line:** whether D84's Release-1 exclusion and its
  100-weekly-actives return threshold still stand for the quarterly form. Door: TWO-WAY until sold;
  toward founding members the rate is ONE-WAY once sold.
- **Teaching language is pt-BR — and Junior's speaking voice is not used in the teaching layer, only
  his vocalizations.** The spoken framing assets — the welcome, the narration, the invitation —
  remain, and remain subtitle-bearing; INPUT-14's real scope is those assets alone. Door: TWO-WAY.
- **Play-surface credit: credit the human, never the layer; the presence lamp shows live human
  presence only.** Answers INPUT-88, and resolves the fork C23 records in favour of the
  lamp-as-live-presence reading. Door: TWO-WAY while unpublished (red line #5 attaches when the
  free room ships it).
- **Takedown reach: everything Opanijé controls, explicitly excluding copies already on a device;
  stated to the teller before consent; human counsel deferred to pre-publication.** Red line #6's
  operating form gains its ruled scope; the cross-system build itself remains owed. Door: ONE-WAY
  (it shapes what the teller is told before consent).
- **Estate-level rulings recorded for completeness** (their operational homes are the hub, not this
  repo): the D-U-N-S filing is done and the seller-of-record entity question is closed — holder and
  seller are the same party; the on-hold WooCommerce orders are test data; the Zelle payee is a test
  method to be removed; course products 1049/1050 are unpublished under a full backup gate;
  ElevenLabs spend is deferred until footage is ready to cut; the BorgBase key is escrowed off-box
  by the operator.

**PROPOSED — the teaching travels without translation.** The lead's derivation from the rulings
above, put up for ratification rather than asserted: because notation, teaching and input are one
artifact in Junior's vocalization (G2, G3), and the play layer has no legend and no translation
step, the instructional loop is **language-independent** — Portuguese-or-English is a property of
the framing assets, not of the instruction. The estate has never written this down, and has never
made the reach argument it implies (the standard's distribution case — THE-STANDARD §1.3 territory,
recorded here because `plan/` is history under D88). It also narrows INPUT-14 as noted above.
Status: PROPOSED until the founder and Junior ratify.

---

## 2026-08-21 — Junior live via founder relay: five settled facts

- **INPUT-72 GRANTED**: rough-audio audience is "sim, apresente roteiro pra gravar" — test-grade only, never public; roteiro delivered same day. Door: ONE-WAY.
- **INPUT-78 ANSWERED**: classroom sequence is (1) solfejo apresenta, (2) solfejo+tambor, (3) solfejo do ritmo, (4) toque do ritmo; INPUT-79 stays open. Door: ONE-WAY (derived).
- **INPUT-67 confirmation half ANSWERED**: register syllables agudo='tá', médio='tu', grave='dum' ("diferença tonal"); stroke/part mapping (INPUT-77) stays with the founder. Door: ONE-WAY.
- **INPUT-80 Junior's half CLOSED**: comfortable teaching all rhythms, order ijexá→congo→cabila correct; his standing ruling — availability/comfort is never re-asked. Door: ONE-WAY (red line #5).
- **INPUT-62 DELEGATED** by Junior ("decide for us"); PROPOSED in response, owner Founder for ratification: return invitation freezes at one quiet card/room-stays-open/one return action, with its never-list as the permanent boundary. Door: TWO-WAY (derived).

---

## 2026-08-30 — Five rulings threaded from the opanije repo (2026-08-28/29)

- **2026-08-28**: founder ruled the stroke vocabulary — hand slap='Tá', tone='Tu', bass='Dum'; sticks skin='Tá', rim='Ti' (opanije `GATES.md:42`, wired `zones.ts:4-6,10-11`). Door: ONE-WAY (fixed reference dialect).
- **2026-08-28**: operator ruled sacred-status control — catalog rows may read `cleared-by-operator` to render; the gate still fails closed on everything else (opanije `GATES.md:46`, `toque-echo-reference.py:89`). Door: TWO-WAY (derived).
- **2026-08-28**: operator picked Home bento option C (opanije `GATES.md:57`, wired opanije #1323). Door: TWO-WAY.
- **2026-08-29**: operator ruled the Cidade→RODA rename — label-deep only, keys/routes/testIDs stay `cidade` (opanije `GATES.md:58`). Door: TWO-WAY.
- **2026-08-29**: operator re-deferred the three Room evidence acts to 2026-09-16 (opanije #1325). Door: TWO-WAY.

---

*Opened 2026-08-05. Under D88 this is the only register the build side writes to; `LEDGER.md` is the
only one it adds rows to.*

## 2026-08-31 — INPUT-62 ratified

- **INPUT-62 RATIFIED** (founder delegation in a live turn — "decide for me" — lead ratified the
  PROPOSED response as written): the return invitation freezes at its demonstrated form — one
  quiet card, room-remains-open, one return action; the never-list (pontos, sequência, meta,
  prêmio, reconhecimento do mestre, posição, comparação entre estudantes, leitura de tempo) is
  the permanent boundary; any widening requires a new founder+Junior decision. Door: TWO-WAY
  (derived — no free-tier engagement layer survives G15/D66).

## 2026-08-31 — the ratification set closed (founder, live turn)

- **INPUT-19 RATIFIED**: the narrow no-digital-skill reading (R11) stands — usable without
  digital skill never means feature removal, only never-mandatory-to-play. Door: TWO-WAY.
- **INPUT-24 RATIFIED**: tier 3 is the product's base; tiers 1–2 are the on-ramp. Door: TWO-WAY.
- **INPUT-28 RATIFIED**: A14 reads as a proprietary interactive product, never a points layer —
  coherent with INPUT-62's boundary ratified the same day. Door: TWO-WAY.
- **INPUT-26 ANSWERED**: Vanderson's role is PONTUAL (per project, when called); terms agreed
  per project; Release 1 does not depend on him. Feeds INPUT-3; narrows INPUT-55. Door: TWO-WAY.

## 2026-08-31 — the business-facts interview (founder, live turn)

- **INPUT-1 ANSWERED**: no email list exists. **INPUT-7 ANSWERED**: no grants tracked now.
- **INPUT-4 ANSWERED**: fixed costs ~R$1,500/month; rises to R$5-6k with course-launch
  social-media work. **INPUT-8 ANSWERED**: no company account, no treasury — costs leave the
  founder's personal account; course revenue will land at the seller CNPJ (Junior's company),
  an asymmetry the terms memo must reconcile.
- **INPUT-5 PARTIAL**: immersion window = maybe January next year; capacity/supplier cost open.
- **INPUT-3 + INPUT-61 FACT**: terms are oral, 50/50, founder and Junior, nothing written.
  Junior delegated terms to the founder; founder delegated the WRITTEN FORM to the lead, with
  brainstorm + double-blind review, ruling to be recorded when made.
- **INPUT-10/11 DELEGATED** (same turn): private-class prices in both price worlds + the
  never-cross rule's operating form — lead decides via the same brainstorm + double-blind.

## 2026-08-31 — two delegated rulings (double-blind adjudicated) + the MEI answer

- **INPUT-10/11 RULED** (founder delegated live; two blind Opus lenses, lead adjudicated):
  private classes — presencial R$500 single / R$1.800 month (4x), online R$400 / R$1.500 month,
  60 min both, prepaid packs, BRL only, never printed. Never-cross operating form: one premium
  sheet for the master's time (floor R$1.800/month), no arithmetic bridge, quote totals never
  rates, no discounts (move to a group format instead), no free trial class, the founder quotes
  — the master never says a number, institutional inquiries route to B2B, one repricing date.
  Buyer-indexed dual pricing REJECTED (community-reputation risk lands on the master).
  30-day market falsifier recorded. Doors: TWO-WAY (prices), the quoting protection ONE-WAY
  socially. Full adjudication: workstation ~/scratch/doc-revamp-2026-08-31/ADJUDICATION-2026-08-31.md.
- **INPUT-3/61 WRITTEN FORM RULED** (same process): "Acordo entre os fundadores" drafted —
  memory-not-contract, pt-BR authoritative, 9 sections; costs-reimbursed-first with worked
  example; ONE monthly statement both see (the load-bearing clause); monthly settlement;
  reserve 10% of net to 3 months of costs; personal money in = recorded loan; possession-is-
  not-ownership sentence; Junior's red lines verbatim-faithful; mutual veto on the name at
  exit; subordinate-to-the-word clause. DRAFT-ACORDO-FUNDADORES-2026-08-31.md (this repo,
  DRAFT — the two humans read it ALOUD together first; the money clause is SAID before it is
  sent; counsel before signatures carry weight).
- **MEI ceiling ANSWERED (founder, live):** not a problem for now — plan: shift part of the
  receipts to a second MEI (his brother's, with headroom) or simply start paying taxes past
  the ceiling. R$65k-annualised watch stays armed machine-side; contador/counsel question only
  when the shift becomes live.
