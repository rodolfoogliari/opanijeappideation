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
| **D94a** — the play layer is ON in **tester builds**: Junior's Day 10 sitting and Stage 2's ten testers | **RATIFIED 2026-08-05** | **TWO-WAY.** Red line #5 does not attach — a hand-picked sideload is not the free tier, and D103 already ruled this same cohort is not "public" |
| **D94b** — the play layer default flips ON in the **public free room** | **PENDING — scheduled for Stage 3** | **ONE-WAY.** Red line #5 attaches: the free room would keep the echo loop, the fade and the closing facts permanently |

**Why the split holds.** Every piece of evidence D94b needs is produced by D94a. Row 52 (Junior's
verdict on whether the play layer reads as musical information or as a verdict on the player), row 53
(the fade), row 55 (≥7/10 to the screen drum) and Junior's form assent under INPUT-79 all come from
ten sideloaded testers and one sitting — none of which touches the free tier. D94b is then taken at
Stage 3 with that evidence in hand rather than in advance of it.

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

Recorded as **ledger row 59 — FALSIFIED, MEASURED, n=1, 2026-08-05**, and as **risk #35**.

**Three things this does and does not mean, kept separate on purpose.**

1. **It is real and it is dated.** Under METHOD's honesty rules an honest FALSIFIED outranks a
   hopeful ASSUMPTION. This is the estate's first MEASURED row after 51 unmeasured ones, and it
   arrived as a negative. That is the register working, not failing.

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

*Opened 2026-08-05. Under D88 this is the only register the build side writes to; `LEDGER.md` is the
only one it adds rows to.*
