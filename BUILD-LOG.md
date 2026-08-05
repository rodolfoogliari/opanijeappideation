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
**Seventeen ratified, one rejected, one deferred, one held pending.**

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
D94  play layer ships ON                     [ ] PENDING   — further explanation requested
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

**D94 — PENDING.** Not rejected and not deferred. The founder asked for a fuller account of what
turning the play layer on actually commits the company to before ruling. Held open; nothing in the
build proceeds against it either way. **This is now the highest-priority open decision in the
estate**, for the reason in the device finding below.

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
| The free set — what is given away permanently under red line #5 | **Ijexá, two parts (agogô + one drum part), two speeds, with the play layer on** | Answers INPUT-86 / INPUT-80. **ONE-WAY.** Note its play-layer clause is contingent on D94. |
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
   about the design.** `playLayerEnabled` (`AppRuntime.tsx:239-242`) is false unless `__DEV__` or
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
