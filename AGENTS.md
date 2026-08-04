# AGENTS.md — opanijeappideation

This is a Markdown-only product and governance estate. It contains no application code, build,
test, deploy, or production lane; do not invent one. Read `CHARTER.md` before proposing any change.

## Authority and records

- `CHARTER.md` is constitutional and wins every conflict. It changes only with explicit founder
  ratification and, where sacred form is touched, Junior's sign-off.
- `plan/PRODUCT-GOALS-VNEXT-CONSOLIDATED-V2.md` is the plan of record. `METHOD.md` owns procedure,
  including epistemic labels; `BACKLOG.md` owns open work; and `registers/` owns current numbered
  state. `sessions/` preserves reasoning history and is not a current-state register.
- Never resolve an input reserved to the founder, Junior, or counsel. Do not upgrade an epistemic
  label without dated evidence.
- Everything else in the estate is proposed until ratified, and proposals are recorded as numbered
  deltas. Founder-issued operator mandates are operative on issue.
- Register claims are append-only: status may change, but superseded and falsified rows remain.
  Continue `registers/NUMBERING.md`; never reuse a number.
- A session that changes the estate follows the consistency steps in `METHOD.md` §7. ONE-WAY
  questions, Junior's decision-hour items, and founder-facing questions use three options with pros
  and cons. Surface technical findings only when they force a product fork, and state the cost rather
  than assuming the conclusion.

## Work discipline

Every plan item and change must trace to the user request, this contract, or verified repository
evidence; otherwise do not implement it. Make the smallest verified change. Add no speculative
framework, dependency, flexibility, unrelated cleanup, or "while we are here" work.

For long work, reuse the existing owning plan as the single durable plan, carrying the objective,
current state, evidence, next action, and material lessons; never create a competing tracker. Reflect
open work in `BACKLOG.md`, numbered state in `registers/`, and session reasoning in `sessions/`. After
a handoff, restart, or context compaction, reread these instructions and the active plan, verify Git
state, and confirm the next action remains in scope.

After each batch, inspect the diff, run the relevant consistency checks, and remove anything that
does not map to the active requirement. At major milestones, use one fresh blind reviewer for scope
drift and overengineering; if unavailable, perform the same review yourself from fresh context and
label it honestly. Never claim a review ran when it did not. A material mistake record contains only
what failed, why, the correction, and how to prevent recurrence.

## Validation and completion

There is no project test runner. Inspect the changed documents against `CHARTER.md`, `METHOD.md`, the
relevant registers, and `BACKLOG.md`, then run `git diff --check`. Completion requires that evidence
and review, not an agent report or elapsed time. Keep authored, pushed, PR-open, merged, and accepted
states distinct; documentation here has no deploy or production effect.
