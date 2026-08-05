# Opanijé — The Build Plans

**Written 2026-08-05.** Produced by compacting a 32-document, 145,680-word ideation estate, reconning
the live opanije.com and the existing codebase, commissioning a design plan from Fable 5, and then
verifying every load-bearing claim in that plan against the actual code.

> ### ⚠️ Amended 2026-08-05 by the founder's ratification
>
> Put to the founder as `PLAN-00-DECISIONS.md` §8 and returned the same day. **Seventeen decisions
> RATIFIED, D96 REJECTED, D98 DEFERRED, D94 PENDING.** A physical-device test the same day returned
> **0/10** and is recorded as **ledger row 59 — FALSIFIED, MEASURED**, the first measured row in the
> company's history. The full record is `../BUILD-LOG.md`; the registers are updated.
>
> Passages superseded by that ruling are marked **AMENDED** inline. Where this document and
> `../BUILD-LOG.md` disagree, **`BUILD-LOG.md` governs.**

> ### ⚠️ Amended 2026-08-05 (later) — the tester programme is suspended
>
> Following ledger row 59's **0/10**, the founder ruled that **the interface, the UI/UX and every
> tester-facing part of the app are redone and deeply reviewed before any human sees it again.**
> Stage 2 is suspended, a new **Stage R** sits between Stage 1 and Stage 2, and Capture Day proceeds
> unchanged. `../BUILD-LOG.md` governs.



---

## Read in this order

| # | File | What it is | Read when |
|---|---|---|---|
| **1** | [`PLAN-00-DECISIONS.md`](PLAN-00-DECISIONS.md) | 20 numbered decisions (D84–D103), 5 new inputs, 7 ledger rows, 5 risks, and a ratification sheet | **First.** Fifteen minutes with a pen. |
| **2** | [`PLAN-01-BUILD.md`](PLAN-01-BUILD.md) | The five-stage build plan, what must never be attempted, and the governance dividend | Once, properly. Then keep the never-attempt table visible. |
| **3** | [`PLAN-02-RUNBOOK.md`](PLAN-02-RUNBOOK.md) | The first ten working days, command by command, prompt by prompt | Tomorrow at 09:00, one day at a time. |
| **4** | [`PLAN-03-LEDGER.md`](PLAN-03-LEDGER.md) | What gets measured, and the three numbers that stop the project | Before Stage 2, and at every stage exit. |

**Supporting material** (one directory up):

- [`../AS-BUILT.md`](../AS-BUILT.md) — **what actually exists**: the code, the live site, the assets,
  and the nine claims an earlier plan got wrong. Read this if you ever doubt a number in these plans.
- [`../BUILD-LOG.md`](../BUILD-LOG.md) — what has been ruled since. **It governs where it and these
  plans disagree.**
- [`../CHARTER.md`](../CHARTER.md) — two pages, and the only thing here that cannot be traded away.

> **The four documents these plans were built from no longer exist on disk.** `FABLE-PLAN.md`
> (the design plan), `VERIFICATION.md` (its claims checked against the code), `MASTER-BRIEF.md` and
> `compacted/` were removed on 2026-08-05 when the estate was compacted — their unique content is in
> `../AS-BUILT.md`, and they remain recoverable from git history at commit **`e38917a`**. Do not go
> looking for them, and do not regenerate them.

---

## The three sentences that matter

**The app is ~80% built and nobody has ever heard it.** `apps/opanije-room` is 12,443 lines of
implementation with 621 tests across 55 suites (re-run 2026-08-05: 613 passed, 8 todo, 0 failures),
13 bilingual routes, and a working APK — and `ACCEPTANCE.md:29` still reads *"BLOCKED — owner:
operator … NOT VERIFIED ON A DEVICE."*

**The best parts of the product are switched off.** The echo loop, the fade-and-rejoin, and the
three-facts closing screen sit behind `playLayerEnabled`, false by default. A student installing
today's build would not see the game the estate spent 145,680 words inventing.

**There is no real audio, and distribution — not code — is the binding constraint.** 72 synthetic
placeholder WAVs stand in for Junior. Meanwhile: 798 Instagram followers, 33 YouTube subscribers, 5
orders ever, none completed.

---

## What these plans decide

**Build the free instrument, give it away, and find out whether anyone plays it twice.**

Ship the Room as a permanently free Android app *and* a link-playable web room at
`opanije.com/toca` — one commons rhythm played by Junior, the echo loop switched on, no account, no
checkout, no store required to try it. The web room is also the iOS version, because iOS is
permanently infeasible from this machine.

Then, only if it measures: activate the payment rail that has been sitting deployed and dormant, and
sell the R$297 course.

**Nine weeks to a public product. Seventeen to first money. Two to three days of Junior's recorded
time.** Every week of it on machinery already proven on this workstation.

---

## The five things most likely to go wrong

1. **Reading the estate instead of building.** 145,680 words is a comfortable place to hide from a
   terminal. The Charter is two pages and it is the only document you need open.
2. **Waiting on Junior.** His latency is uncontrolled; yours is not. Every ask is front-loaded to
   Day 1 so that no build day is blocked on a reply.
3. **Touching the audio engine.** The moment you are reading about buffer sizes, AAudio, or latency
   calibration — stop. The answer to every audio problem in this architecture is another
   pre-rendered file.
4. **Building Stage 4 before Stage 3 measures anything.** Wiring Room's server seams is 5–7 weeks of
   greenfield work behind a designed interface. It is not worth doing for an audience that does not
   exist yet.
5. **Rationalizing away Gate 1.** If fewer than 7 of 10 beginners reach the screen drum unaided,
   the door is broken. Write the criterion down before the testers arrive.

---

## What was corrected in Fable's plan

Fable read the compacted estate and the recon reports; verification then read the code. Three
corrections were material:

- **"Single product only until the entitlement defect is fixed" — the defect was already fixed**
  (`94a2a0dd`/`694da476`). Entitlement is keyed per course and the tests already run two course
  keys. Remediation scheduled against that claim would have been wasted weeks.
- **"3–4 weeks to connect Room to the server" — nothing behind those seams exists.**
  `createRoomApi` is never called, `catalogForPublishing()` throws unconditionally, and
  `SERVER-CONTRACT.md` calls its endpoints "proposed shapes for the missing implementation."
  Re-budgeted to 5–7 weeks and moved behind the free instrument.
- **`createFakeRoomAudio()` is a source-edit-away hazard, not a live vulnerability** —
  `_layout.tsx:70` always injects the real engine. Still fixed, but on Day 2, not in a panic.

Four things nobody had noticed at all: the repo is **GPL v3** repo-wide, the existing APK is signed
with the **debug key** and cannot be submitted, replacing the audio trips a **sha256 provenance
chain that fails closed**, and the Room build script's own header forbids the tester access that
Stage 2 requires (now decided explicitly as **D103**).

---

*The estate got the design right, quite possibly. Nobody knows, because nothing has been measured.
These plans are arranged to change that within two weeks, starting with one person putting one phone
to their ear.*
