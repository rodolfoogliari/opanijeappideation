# Opanijé — Numbering State

**Status.** Register of record, as of **2026-08-05** (the D84–D103 ratification; previously
2026-08-03, Game Addendum 04 §16).

**Rule.** Continue the estate's numbering. **Never reuse a number** — not for a withdrawn item, not
for a superseded one, not for a number that turned out to be a duplicate. A gap is cheaper than a
collision.

---

## Next number, by series

| Series | Last used | **Next** | Register |
|---|---|---|---|
| Deltas | **D103** | — *frozen under D88; use `../BUILD-LOG.md`* | `DELTAS.md` |
| Inputs | **INPUT-92** | — *frozen under D88; use `../BUILD-LOG.md`* | `INPUTS.md` |
| Recommendations | R88 | — *frozen under D88* | `RECOMMENDATIONS.md` |
| Ledger rows | **60** | **61** | `LEDGER.md` — **the only register still taking new rows** |
| Risks | **#38** | **#39** | `RISKS.md` |
| Experience decisions | E21 | **E22** | `DECISIONS.md` |
| Game decisions | G26 | **G27** | `DECISIONS.md` |
| Forks | L | **M** | `FORKS.md` |
| Contradictions | C23 | **C24** | `CONTRADICTIONS.md` |
| Founder rulings | A17 | **A18** | `DECISIONS.md` |
| Session decisions | S9 | **S10** | `DECISIONS.md` |

---

## Known gaps and irregularities

Recorded rather than silently repaired, because a quiet renumbering is how a register loses its
authority.

**INPUT-29 is missing.** The v1.0 register runs INPUT-28 → INPUT-30 with no 29 and no note. It was
either resolved in the third 2026-07-29 session or lost in consolidation. **Flagged, not invented** —
the number stays retired and is not reassigned.

**The G-series has two meanings and they must not be confused.**
- **G1–G26** are *game decisions*, in `DECISIONS.md`.
- **G0–G7** are *Gate criteria*, in `PRODUCT-GOALS-VNEXT-CONSOLIDATED-V2.md` §8.
Always cite Gate criteria as "Gate G0", never bare.

**The letter series collide with the numbered series.** Forks are bare letters (Fork A … Fork L);
contradictions are always C + number (C1 … C22). "Fork C" and "C3" are unrelated items. Founder
rulings are A + number (A1 … A17) and are unrelated to Fork A.

**FF1–FF4 are founder facts**, not forks and not a numbered register — they live in
`PRODUCT-GOALS-VNEXT-CONSOLIDATED-V2.md` §3.1. FF1's valence was reversed by G22; see
`../plan/THE-STANDARD.md`.

---

## Where the numbering came from

Each session document continued the previous one's series. That chain is now history rather than
mechanism — the registers in this directory are the register of record under **D83**, and new numbers
are drawn from the table above rather than from the last session file.

| Block | Source document |
|---|---|
| D1–D28, INPUT-1–51, R1–R51, rows 1–33, #1–#22, A1–A17, C1–C20 | `plan/PRODUCT-GOALS-VNEXT-CONSOLIDATED-V2.md` |
| D29–D35, INPUT-52–53, R52–R54, rows 34–35 | `sessions/PLAN-AMENDMENTS-FOR-V2.1.md` |
| D36–D42, INPUT-54–56, R55–R58, rows 36–37, S1–S9 | `sessions/RELEASE-1-ADDENDUM-SESSION-2-2026-07-31.md` |
| E1–E19 | `plan/RELEASE-1-EXPERIENCE-SPEC-V1.md` |
| D43–D51, INPUT-57–66, R59–R62, rows 38–39 | `plan/OPERATOR-MANDATE-01-ENGAGEMENT-2026-07-31.md` |
| D52–D58, INPUT-67–71, R63–R72, rows 40–43, #23–#24, G1–G8 | `sessions/GAME-ADDENDUM-01-…-2026-07-31.md` |
| D59–D60, INPUT-72, R73–R76, rows 44–45, #25, G9–G10, C21 | `sessions/GAME-ADDENDUM-02-…-2026-08-01.md` |
| D61–D70, INPUT-73–77, R77–R82, rows 46–47, #26, G11–G19, E20, C22, Fork K | `sessions/GAME-ADDENDUM-03-…-2026-08-01.md` |
| D71–D83, INPUT-78–84, R83–R88, rows 48–51, #27–#29, G20–G26, E21, Fork L | `sessions/GAME-ADDENDUM-04-…-2026-08-03.md` |
| D84–D103, INPUT-85–92, rows 52–60, #30–#38 | `plans/PLAN-00-DECISIONS.md`, ratified 2026-08-05 — see `BUILD-LOG.md`. Rows 59, #35–#37 and INPUT-90–92 were **not** in the issuing document: they came from a device test and from the founder's rulings on D96 and D98 |

Block boundaries are as each document states them. Where a document's own accounting disagreed with
the next document's "continuing from", the discrepancy is noted in the relevant register rather than
resolved by preference.

---

## What D88 changes about this file

**Most of the series above are now closed.** D88 (ratified 2026-08-05) puts the register apparatus
into maintenance mode: `DELTAS.md`, `RECOMMENDATIONS.md`, `CONTRADICTIONS.md`, `FORKS.md` and
`sessions/` freeze. A build decision that would once have drawn the next D-number becomes **one line
in `../BUILD-LOG.md`** instead.

Two series stay open, because they are how the estate learns rather than how it deliberates:
**`LEDGER.md`** (next row **61**) and **`RISKS.md`** (next **#39**).

The no-reuse rule survives the freeze and applies to the frozen series too. **Ledger row 56 is
withdrawn on issue** under D96 and its number is retired, not reassigned — the first entry in this
file's gap list that was created by a founder ruling rather than by a lost document.

**D94 is split, not renumbered.** On 2026-08-05 the founder ratified a split of D94 into **D94a**
(the play layer in tester builds — RATIFIED, two-way) and **D94b** (the play layer in the public free
room — PENDING, one-way under red line #5). No new number was drawn. This follows the estate's own
precedent for ledger row 21, split into 21a and 21b by D12 and counted once. As with row 21, **there
is no undivided D94 after this date** — cite D94a or D94b, never bare D94.

---

*Numbering state, 2026-08-05. Under D88, update this file when a ledger row or risk is added; the
frozen series no longer advance.*
