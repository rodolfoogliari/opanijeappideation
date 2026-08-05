# Opanijé — The Build Decisions

**Status.** **RETURNED 2026-08-05 — 17 RATIFIED, D96 REJECTED, D98 DEFERRED, D94 SPLIT (D94a
RATIFIED, D94b scheduled for Stage 3).**
Written 2026-08-05, ratified the same day. The record of record is `../BUILD-LOG.md`.

> ### ⚠️ Amended 2026-08-05 by the founder's ratification
>
> Put to the founder as `PLAN-00-DECISIONS.md` §8 and returned the same day. **Seventeen decisions
> RATIFIED, D96 REJECTED, D98 DEFERRED, and D94 SPLIT — D94a RATIFIED, D94b scheduled for Stage 3.** A physical-device test the same day returned
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


**Supersedes nothing in `CHARTER.md`.** Every red line below is intact and every decision here was
checked against Charter §9's prohibition list before it was written.

**What this file is.** The decisions that turn an ideation estate into a shipping Android app, made
at the altitude a solo non-engineer actually operates at. Numbered in the estate's own series so they
drop straight into `registers/DELTAS.md` — next delta was **D84**, next ledger row **52**, next risk
**#30**, next input **INPUT-85**.

**How to ratify.** One line each in `BUILD-LOG.md`: `D84 RATIFIED 2026-08-0X` or `D84 REJECTED —
because …`. Ratifying the block takes fifteen minutes. Every item marked **ONE-WAY** deserves an
hour of thought; everything else is reversible and should be decided in seconds.

---

## 0 · The three facts this block is built on

Before the decisions, the three findings that produced them. Each was verified against the code, not
inferred from the estate.

> **AMENDED 2026-08-05 — Fact 1 is now out of date, and that is the most important thing on this
> page.** A physical-device test has been run. A first-time user did not understand what to do,
> reported that there was no gamified mechanic, and did not understand how to interact at all —
> **0/10**. Recorded as ledger row 59 (FALSIFIED, MEASURED, n=1) and risk #35. The build tested had
> the play layer **off**, which makes it evidence bearing directly on D94 rather than a verdict on
> the product D94 would ship. Read Facts 2 and 3 below with that in hand.

**Fact 1 — the app is ~80% built and nobody has ever heard it.** `apps/opanije-room` is 12,443 lines
of implementation and 621 tests across 55 suites — re-run 2026-08-05 with `~/box/mobile-env.sh`
sourced: **613 passed, 8 todo, 0 failures, in 10 seconds** — plus 13 bilingual routes and a working
98.2 MiB APK dated 2026-08-04. And `ACCEPTANCE.md:29` carries criterion 1 as **"BLOCKED —
owner: operator … NOT VERIFIED ON A DEVICE."** No handset has ever run it. No human has ever heard
the audio through a speaker.

**Fact 2 — the best parts of the product are switched off.** The echo loop, the fade-and-rejoin
model, and the three-facts-plus-personal-best closing screen are all gated behind `playLayerEnabled`
(`AppRuntime.tsx:239-242`), which is `false` unless `__DEV__` or `EXPO_PUBLIC_ROOM_DEMO` is set.
`closing.test.tsx:234` actively asserts the three facts are **absent** by default. A student
installing today's APK would not see the game the estate spent 145,680 words inventing.

**Fact 3 — there is zero real audio, and swapping it is not a file copy.** 72 synthetic placeholder
WAVs (~34 MB, hash-verified, committed to git) stand in for Junior. Replacing them trips a sha256
provenance chain enforced by `assets.test.ts:490-523` that **fails closed** until the manifest is
regenerated — and the generator itself (`make-placeholder-audio.py:287-289`) hard-fails while an
arrangement gate is unresolved. Audio replacement is a pipeline project, not a drag-and-drop.

Everything below follows from those three.

---

## 1 · The scope cuts

These are Fable's five cuts, four adopted as written and one amended.

### D84 — The monthly master cycle is out of Release 1. **TWO-WAY.**
D81 put Junior's monthly listening cycle into Release 1 as operations. It strains the one-obligation
rule, the estate flagged that strain itself as risk #29, and it has no price, no format, and no
audience. Junior's monthly hours go instead to Track B private classes, which produce revenue
evidence. **INPUT-82's go/no-go is answered NO-GO for now.** The cycle returns when 100 weekly-active
students exist to attend it — and when it returns it should return as **D89's Perguntas library**
(§3), which is the cycle's soul at a tenth of its obligation.

### D85 — The notation standard is frozen, not cancelled. **TWO-WAY.**
D82/G22 proposed publishing the notation system openly as a standard. Risk #28 — the standard
outruns the corpus — is not a risk at current corpus size, it is a certainty: the corpus is zero.
The frame stays drafted and in the drawer. It is revisited when there is a corpus for it not to
outrun. **Nothing about this cut touches G22's positioning claim** — Opanijé can position as a
music-education company without having published anything yet.

### D86 — A lean Capture Day replaces the full M0 production shoot for Release 1. **Partly ONE-WAY.**
The estate's own logic makes M0 the governing deadline because of *irrecoverability* — what is shot,
not when the big shoot happens. A one-day kitchen-table capture that honours every one-way door loses
nothing a later professional shoot cannot add on top. **The one-way parts are not cut and not
softened:** consent scope covering interactive and game use signed before anything rolls (INPUT-22),
isolated per-part stems (INPUT-23), the five-value partition captured item-by-item as Junior speaks
it (INPUT-21), and solfejo passes locked to the battery. A lean day that skips any of those four is
not a lean day, it is a wasted one.

### D87 — The app sells nothing and links to no checkout. **TWO-WAY, but do not reverse casually.**
All commerce happens on the web, through the Mercado Pago rail that is already deployed. The app
asks the server what an account owns and plays it. This deletes Google Play billing integration, the
15–30% store tax, and the anti-steering compliance brief from the critical path in a single move. It
also makes the Play listing trivially compliant: an app that sells nothing has almost nothing to
declare.

### D88 — The register apparatus goes to maintenance mode. **TWO-WAY.** *(Amended from Fable.)*
`CHARTER.md`, the vocabulary sheet, the Charter §9 prohibition list, and `LEDGER.md` stay alive.
Everything else — `DELTAS.md`, `RECOMMENDATIONS.md`, `CONTRADICTIONS.md`, `FORKS.md`, `sessions/` —
freezes: read-only, cited when useful, never extended. Build decisions become one line in
`BUILD-LOG.md` (date, decision, door label).

**The amendment:** Fable proposed freezing Room's `GATES.md` too. Verification found **56 `GATE:`
markers in non-test `src/`** — these are founder-, counsel- and Junior-owned decisions embedded
directly in shipping code, not process ceremony. Freezing the register while the markers stay in the
code creates orphans. So: `GATES.md` freezes as a *document*, but the 56 in-code markers are
inventoried once (`npm run gate` already has `check-gates.mjs` for this) and each is either closed,
converted to a `BUILD-LOG` line, or explicitly deferred with a date. **One sweep, one afternoon, then
the register can freeze honestly.**

---

## 2 · The salvage decisions

### D89 — `apps/opanije-room` is the product. **ONE-WAY in practice.**
All future work lands here. It is the only artifact on earth implementing the estate's actual
inventions. It is not a mockup any more and stops being described as one.

### D90 — `apps/opanije-mobile` is a parts donor, then archived. **TWO-WAY.**
Four modules are lifted into Room: the hand-rolled PKCE auth flow, `expo-secure-store` session
handling, the repository factory, and the `expo-video` signed-playback pattern. Then the app is
archived with a README pointer — **not deleted**, because its iOS project is the estate's only iOS
asset and costs nothing to keep.

**Warning attached to this decision.** Mobile is formally PARKED under DN-3 ("do not build against
it"), its CI was reduced to `workflow_dispatch` after **30 consecutive typecheck failures**, and its
`node_modules` is absent so its current state is *unverified*. Treat the lift as **porting from a
reference implementation**, not as moving working code. Budget a week, not a day, and expect to
rewrite rather than copy. If a module resists for more than two days, write it fresh against Room's
own conventions — Mobile's version is a spec, not a dependency.

### D91 — The dormant mu-plugin rail is the backend. Forever, absent a founder ruling. **ONE-WAY.**
13 opanije mu-plugins, ~360 KB, ~9,600 lines, deployed, versioned, with a REST contract
(`opanije-mobile/v1`), fixtures, and a JSON schema. Nobody proposes a new backend. Every server-side
feature is a new endpoint in that contract. The VPS runs it today at 0.04 load and will run it at
1,000 users without noticing.

### D92 — Production bundle ID is `com.opanije.room`. **ONE-WAY once published.**
Verified free. Room currently ships `com.opanije.room.mockup`; the parked
`com.opanije.course.debug.preview` retires. **Rename before the first store upload, never after** —
changing it post-publication means a new listing and orphaned installs. Note the rename also touches
the keychain service string (orphaning any stored sessions) and deep-link configuration.

### D93 — Room's outward seams stay unwired until Stage 4. **TWO-WAY.**
Verification is blunt about their true state: `createRoomApi` is never called,
`createCommercePlanner` is imported by no screen, `RemoteRenderSource` is never instantiated,
`AccountIdentityPort` has no implementation, `factSender` throws by default, `catalogForPublishing()`
throws unconditionally, and `SERVER-CONTRACT.md:5` describes its endpoints as *"proposed shapes for
the missing implementation."*

**This means "connect Room to the server" is greenfield behind a designed interface, not a wiring
job.** Fable's 3–4 week estimate is optimistic; **budget 5–7 vibecoding weeks** and schedule it after
the free instrument has shipped and shown pull. The free instrument needs no account, no server, and
no seam — and that is what makes it shippable first.

---

## 3 · The product decisions

### D94 — The play layer ships ON for students. **ONE-WAY (red line #5 attaches).** ⚠️ *The most important decision in this block.*

> **SPLIT 2026-08-05, and the ratified half is live.** Row 59's 0/10 was measured on a build with
> this layer switched **off**, and the tester's own words were *"there was no gamified mechanic"* —
> a literal description of `playLayerEnabled = false`, not an opinion about the design. The founder
> ratified a split of this decision into its two halves:
>
> - **D94a — RATIFIED. TWO-WAY.** The play layer is on in **tester builds**: Junior's Day 10 sitting
>   and Stage 2's ten testers. Red line #5 does not attach to a hand-picked sideload, and D103
>   already ruled that cohort is not "public".
> - **D94b — PENDING, scheduled for Stage 3. ONE-WAY.** The production default flips only with
>   row 52, row 55 and the testers' answers in hand.
>
> Every piece of evidence D94b needs is produced by D94a, so the irreversible commitment is taken
> *after* the evidence instead of before it. Charter §9 item 10 is discharged early — Junior sees it
> at Day 10, under D94a.
>
> **D94a costs a bounded code change, not zero.** `EXPO_PUBLIC_ROOM_DEMO` gates the play layer
> **and** the demonstration route tree (`REVIEW_ROUTE_TREE = ['review', 'past-the-door']`,
> `_layout.tsx:48`), and `build-room-apk.sh:63-64` requires those surfaces stay off in anything a
> student receives. The two gates are separated first; then tester builds carry the play layer with
> `/review` off. See `../BUILD-LOG.md`.
`playLayerEnabled` becomes true in production builds. The echo loop, the fade-and-rejoin, and the
three-facts-plus-personal-best closing screen are the product; shipping them switched off ships a
demo of a drum.

Three things follow and none is optional:

1. **`closing.test.tsx:234` inverts.** It currently asserts the three facts are absent by default; it
   must assert they are present. Every test written against the play layer's absence flips with it.
2. **Junior sees it before it is public.** Charter §9 item 10 — no screen-drum surface ships without
   Junior having seen it. The play layer *is* screen-drum surface.
3. **It is a one-way door**, because everything the free tier shows is given permanently under red
   line #5. Turning the play layer on for the free room means the free room has an echo loop forever.
   That is the right trade — it is the product — but it is ratified, not slid into.

### D95 — The fade model stays binary for Release 1. **TWO-WAY.**
Verification found the fade is thinner than the estate believes: binary `full` (0.6) / `thin` (0.2),
recomputed per cycle, companion audio only, recovering the next cycle. No decay curve, no
cross-session unfed decay; the real feeding measure at `tap.ts:82-83` is computed and discarded.

**Ship it as built.** It satisfies D78 (no fail state) and D77 (the drum always sounds), it is
already tested, and whether a decay curve is even desirable is exactly what Stage 2's ten humans are
for. Wire the discarded measure into the ledger as telemetry — measure it, don't act on it yet.
Recorded as **row 53**.

### D96 — The web room is the iOS strategy, and the primary distribution surface. **TWO-WAY.**

> **REJECTED 2026-08-05 by founder ruling.** No reason recorded and none is owed. The argument below
> stands as issued and is *not* softened after the fact — but it did not carry. Consequences are
> recorded as **risk #36** and **INPUT-90**: Release 1 has no iOS path and no no-install tap-to-play
> surface, ledger row 56 is withdrawn on issue, and row 57 is amended because Junior's voice note now
> asks 1,000+ people to install an app rather than tap a link. The web export itself is not
> prohibited — only its promotion to strategy.
No Mac, no Xcode, no signing identity — iOS is permanently infeasible from this machine. Room is
`react-native-web` 0.21.0 capable and a web export has been run and recorded
(`ACCEPTANCE.md:29`). `opanije.com/toca` reaches every iPhone user with zero store risk, and it is
the only artifact anyone will actually tap from a WhatsApp forward. **The web room is not a
consolation prize for the app; the app is the second date.**

### D97 — Purchases are per-course from day one. **TWO-WAY.** *(Reverses Fable's constraint.)*
Fable proposed one product only until a `W1-CL-ENTITLE` per-course-grant defect was fixed.
**Verification found that defect already closed.** `opanije_course_access_subject_holds_course()`
(`opanije-course-access.php:1511-1546`) keys on `course_key` in a two-level ledger and re-verifies
the stored key; `opanije_course_app_user_may_read()` routes through it and its docblock names this
exact failure mode as the thing it exists to prevent. `OPANIJE_COURSE_ACCESS_MAX_COURSES = 2` and the
tests already exercise two course keys.

**Remediation scheduled against that claim is wasted work — do not do it.** Confirm with one live
test purchase at activation and move on.

---

## 4 · The safety decisions

### D98 — A real release keystore is created and escrowed before any store upload. **ONE-WAY.**

> **DEFERRED 2026-08-05 by founder ruling.** Not cancelled. Two consequences follow mechanically and
> are recorded as **risk #37** and **INPUT-91**: no store upload is possible until it closes, and the
> single-machine total-loss exposure D16 has carried as the estate's oldest overdue item stays open.
> **The two halves are separable** — the credential and backup-key escrow can be done without
> generating a production keystore, and closes most of the exposure on its own.
The existing 98.2 MiB APK is a *release variant signed with the debug key*
(`build-room-apk.sh:46`) — perfectly good for sideloading to testers, **not store-submittable**. A
production keystore is generated once, escrowed to two off-box locations with a restored passphrase,
and never printed to a log. This merges with the D16 escrow deadline, which is already the estate's
highest-ranked overdue item: **do them in the same session on Day 1.** Losing this key after
publication means the app can never be updated again.

### D99 — Two physical Android handsets before public ship. **TWO-WAY, but do not skip.**

> **RATIFIED 2026-08-05, and partly executed.** A device test has already been run; its result is
> ledger row 59 and risk #35. `ACCEPTANCE.md:29` criterion 1 is no longer wholly BLOCKED.
`ACCEPTANCE.md` criterion 1 is BLOCKED and owner-assigned to the operator. The two things only a
human can verify — how the audio *feels* through a speaker and how the touch latency *feels* under a
finger — are the two things this entire product rests on. Emulator evidence is not device evidence.
One current phone (the founder's) plus **one used low-tier Android, ~R$400** — the single hardware
purchase these plans endorse.

### D100 — Audio provenance stays enforced. **TWO-WAY.**
When real stems replace the 72 synthetic WAVs, the manifest is regenerated
(`npm run publish:manifest`) and the sha256 chain in `assets.test.ts` stays on. It failing closed is
the feature: it is the thing that proves the audio in the build is the audio Junior consented to.
Never disable it to make a build pass — regenerate.

### D101 — `createFakeRoomAudio()` moves behind a dev guard. **TWO-WAY. Half a day.**
Defined at `engine.ts:107`, imported by production `AppRuntime.tsx:25`, live as
`?? createFakeRoomAudio()` at `:245`. Verification's correction matters: `_layout.tsx:70` always
injects the real engine, so **no runtime path selects the fake** — it is a source-edit-away hazard,
not a live vulnerability. Fix it because a forged Caderno entry is permanent and the Caderno's
defences guard against exported callers rather than a substituted engine. Fix it on Day 2, not in a
panic.

### D103 — Ten NDA-free testers under a private-sideload exception. **TWO-WAY. Founder call.**
`build-room-apk.sh`'s own header carries Build Handoff 01 §5 phase 5 verbatim: *"NOTHING THIS SCRIPT
PRODUCES MAY GO PUBLIC. No tester access, no store listing, no screenshot leaving the estate before
the industrial-design filing."* Stage 2 hands the APK to ten people. **That is a direct collision and
it must be decided, not slid past.**

The ruling: **the ten-tester sideload is not "public."** They are hand-picked, individually known,
receive the APK directly, and are asked not to screenshot. The design filing protects against a
competitor copying a published GUI; ten people in Junior's network are not that. The alternative —
waiting for the filing before any human tests the product — inverts the plan's whole logic and
delays the only evidence that matters by however long counsel takes.

**But it is the founder's risk to accept**, and it is recorded here rather than buried in a build
script comment. If the founder declines, Stage 2 shrinks to Junior plus two people in the room with
the phone in *your* hand, which preserves most of the evidence at some cost in honesty.

### D102 — `verify-apk.sh` extends to `bundle*` before any Play upload. **TWO-WAY. Two hours.**
`plugins/with-verified-apk.js` guards only `assemble*` tasks and scans only `outputs/apk`. Play
requires an AAB. As written, **the RECORD_AUDIO tripwire — which is red line enforcement in CI form —
does not fire on the artifact that actually ships.** Also make it CI-portable: it currently sources
the workstation-absolute `$HOME/box/mobile-env.sh`.

---

## 5 · What goes to a human

Five new inputs. Fable proposed collapsing 40+ open INPUTs to eight; these five are added to that
eight, and every other open input is answered by default under D88 ("the plan's position stands
unless contradicted"), logged, and reversible.

| ID | Question | Owner | When | Cost of being wrong |
|---|---|---|---|---|
| **INPUT-85** | The repo is **GPL v3** (`LICENSE.txt`), repo-wide, covering both apps. Is the app intended to be GPL, or is the app subtree relicensed before store submission? Opanijé appears to hold all copyright, so relicensing is available — but it is a founder-and-counsel call, not a build call. | Founder + counsel | **Week 1** — bundled into the single combined brief with the privacy policy | High. Discovering this at submission stalls the launch; discovering it after stalls it worse. |
| **INPUT-86** | D94 turns the play layer on for the **free** room, making the echo loop permanent under red line #5. Confirm the free set's contents (this ratifies INPUT-80 in its concrete form): **Ijexá, two parts, two speeds, with the play layer on.** | Founder | **Week 1, one hour** | One-way. Everything given free is given forever. |
| **INPUT-87** | `make-placeholder-audio.py:287-289` hard-fails while an arrangement gate is closed. Which arrangement is authoritative for the free rhythm — settle it so the pipeline can run on Capture Day's output the same afternoon. | Junior (form) + founder | **Before Capture Day** | Medium. An unsettled arrangement means Day 9 does not happen. |
| **INPUT-88** | C23 is still open: E2's named on-screen presence was voided by D38, and E21's presence lamp builds on it. With the battery being Junior layered four times, what does the presence surface show? | Junior + founder | **Stage 2 sitting, with a phone in hand** | Low if deferred, because the lamp can ship dark. |
| **INPUT-89** | Capture Day consent scope: does the instrument license **interactive and game use** and **isolated stems + one-shot sampling**? This is INPUT-22/-23 in operating form. | Counsel drafts, Junior signs | **Capture Day morning, before anything rolls** | **Highest in the estate.** Not recoverable without re-consenting a master and reopening commercial terms from a weak position. |

---

## 6 · The new ledger rows

The estate has **not one MEASURED row** in 51. These are the rows this build produces, in the order
they become cheap to measure. Written unmeasured, with the evidence that would convert each.

| Row | Claim | Label now | Converts when |
|---|---|---|---|
| **52** | The play layer, shipped on, reads as musical information and not as a verdict on the player | ASSUMPTION | Junior's verdict in the Stage 2 sitting, in his words, written down |
| **53** | The binary fade is sufficient — students perceive thinning as consequence without a decay curve | ASSUMPTION | Stage 2: asked directly of 10 testers; the discarded `tap.ts` measure logged alongside |
| **54** | Scheduled pre-rendered audio feels like *playing*, not like miming | HYPOTHESIS (est. row 45) | Day 9, two humans, dated written answers; then 10 humans at Stage 2 |
| **55** | A beginner goes voice → screen drum in one sitting unaided | HYPOTHESIS (est. row 46) | Stage 2, target ≥7/10 testers |
| **56** | The web room converts a WhatsApp forward into a completed first session | ASSUMPTION | Stage 3, first-party instrumentation, 100 completed first sessions |
| **57** | Junior's former-student network forwards the link when he asks | ASSUMPTION | Stage 3, one voice note, measured in sessions within 7 days |
| **58** | The Android device distribution supports the generous binary window | ASSUMPTION | R75's two latency flags logged from the first public build |

---

## 7 · The new risks

| # | Risk | Why it is new | Mitigation |
|---|---|---|---|
| **#30** | The play layer has never been seen by a student — all of its evidence is from tests written by the people who designed it | D94 ships it on; the estate has confidence without contact | Stage 2's ten humans, before public ship, with authority to stop the launch |
| **#31** | GPL v3 unresolved at store submission | Found in verification, absent from the entire estate | INPUT-85, week 1, in the combined counsel brief |
| **#32** | Regenerating audio is coupled to an unresolved human decision (`make-placeholder-audio.py:287-289`) | Capture Day's output cannot reach the app while the arrangement gate is closed | INPUT-87 settled *before* Capture Day, and the Day 7 rehearsal proves the whole chain on fake stems |
| **#33** | Reviving `opanije-mobile`'s modules costs more than writing them fresh (parked, CI off, 30 consecutive typecheck failures, unverified) | D90's lift is porting, not copying | Two-day timebox per module, then write fresh |
| **#34** | The estate has more governance capacity than build capacity, and will refill the register the moment pressure appears | This is the failure mode that produced 145,680 words and zero audio | D88; `BUILD-LOG.md` is the only writable register on the build side |

---

## 8 · Ratification sheet

Copy into `BUILD-LOG.md`, mark each, done.

**Returned 2026-08-05.** Reproduced below as marked.

```
D84  monthly cycle out of R1                 [x] RATIFIED  [ ] REJECTED
D85  standard frozen                         [x] RATIFIED  [ ] REJECTED
D86  lean Capture Day replaces M0 shoot      [x] RATIFIED  [ ] REJECTED   ← one-way parts intact
D87  app sells nothing                       [x] RATIFIED  [ ] REJECTED
D88  registers to maintenance mode           [x] RATIFIED  [ ] REJECTED
D89  opanije-room is the product             [x] RATIFIED  [ ] REJECTED
D90  opanije-mobile is a parts donor         [x] RATIFIED  [ ] REJECTED
D91  mu-plugin rail is the backend           [x] RATIFIED  [ ] REJECTED   ← ONE-WAY
D92  bundle id com.opanije.room              [x] RATIFIED  [ ] REJECTED   ← ONE-WAY at publish
D93  seams unwired until Stage 4             [x] RATIFIED  [ ] REJECTED
D94  play layer ships ON                     [~] SPLIT: D94a RATIFIED / D94b PENDING (Stage 3)
D95  fade stays binary for R1                [x] RATIFIED  [ ] REJECTED
D96  web room is the iOS strategy            [ ] RATIFIED  [x] REJECTED
D97  per-course purchases from day one       [x] RATIFIED  [ ] REJECTED
D98  release keystore + escrow before upload [ ] RATIFIED  [ ] REJECTED  ** DEFERRED**   ← ONE-WAY
D99  two physical handsets before ship       [x] RATIFIED  [ ] REJECTED
D100 audio provenance stays enforced         [x] RATIFIED  [ ] REJECTED
D101 createFakeRoomAudio behind dev guard    [x] RATIFIED  [ ] REJECTED
D102 verify-apk.sh extends to bundle*        [x] RATIFIED  [ ] REJECTED
D103 ten testers before the design filing    [x] RATIFIED  [ ] REJECTED   ← founder's risk to accept
```

---

*Filed as PROPOSED, returned the same day. Nothing here upgraded a ledger label. The first MEASURED
row did not wait for Day 9 and it did not arrive the way this document expected: it is **row 59,
FALSIFIED**, from a device test on 2026-08-05, and it says the door does not work. That is the
ledger doing its job on the first day it was asked to.*
