# Opanijé — The Build Plan

**Status.** PROPOSED, then amended 2026-08-05 by the founder's ratification. Written 2026-08-05,
corrected against a line-level verification of the code.

> ### ⚠️ Amended 2026-08-05 by the founder's ratification
>
> Put to the founder as `PLAN-00-DECISIONS.md` §8 and returned the same day. **Seventeen decisions
> RATIFIED, D96 REJECTED, D98 DEFERRED, D94 PENDING.** A physical-device test the same day returned
> **0/10** and is recorded as **ledger row 59 — FALSIFIED, MEASURED**, the first measured row in the
> company's history. The full record is `../BUILD-LOG.md`; the registers are updated.
>
> Passages superseded by that ruling are marked **AMENDED** inline. Where this document and
> `../BUILD-LOG.md` disagree, **`BUILD-LOG.md` governs.**

**Reads with:** `PLAN-00-DECISIONS.md` (what was decided), `PLAN-02-RUNBOOK.md` (the first ten days,
command by command), `PLAN-03-LEDGER.md` (what gets measured and what stops the project).

**Who executes this.** Rodolfo, alone, vibecoding with Claude Code (Max x20). Junior records and
governs. There is no third person. Every estimate below is in **vibecoding weeks** — meaning weeks
of a non-engineer describing intent to Claude and shepherding the result — not engineer-weeks, and
they assume roughly 20 focused hours a week, not 40.

---

## The shape of it, on one page

```
STAGE 0  Hygiene + the ask            week 0–1     ships nothing public
STAGE 1  Capture Day + the pipeline   week 1–3     ships owned audio, internally
STAGE R  The tester-facing surface    week 1–?     ships a door a beginner can walk through   ← NEW
STAGE 2  Ten humans                   SUSPENDED    resumes when Stage R exits
STAGE 3  Public: the free instrument  after R      Play listing only — D96 rejected the web room
STAGE 4  First money                  +5–7 wks     accounts + entitlements + the rail live
STAGE 5  Compound                     later        shaped by whatever Stage 3–4 measured
```

**Stage R is lettered, not numbered, on purpose.** Inserting a "Stage 2" would renumber every stage
after it, and `NUMBERING.md`'s rule — a gap is cheaper than a collision — applies to plan structure
as much as to registers. Stages 0 and 1 run in parallel with it; Stage 2 waits for it.

> **AMENDED 2026-08-05 (later) — the timeline below is no longer claimable, and saying so is the
> point.** The founder suspended the tester programme and ordered the tester-facing surface redone
> after row 59 measured it at 0/10. **Stage R has no estimate**, because nobody yet knows how much of
> the surface is wrong — one unaided tester established that it does not work, not what it would take
> to make it work. Any week-count published before Stage R has scoped itself would be invented. The
> stage *sequence* below stands; the *arithmetic* does not, until Stage R exits.

> **AMENDED 2026-08-05.** Three changes to the shape above, none of which move the stage boundaries
> but all of which change what happens inside them:
>
> - **A door redesign now sits across Stages 1–2**, unscheduled here because its size is INPUT-92.
>   Ledger row 59 measured the current door at **0/10** — one tester, on a real device, who could not
>   tell what to do or how to interact. Stage 2's ten testers are no longer the first contact with a
>   beginner; they are the second, and the first one failed.
> - **Stage 3 loses the web room as its primary surface** (D96 REJECTED). The Play listing carries
>   Stage 3 alone, Release 1 has no iOS path, and INPUT-90 asks the founder what replaces it.
> - **Stage 0's escrow is deferred** (D98). Stage 3 cannot begin its store upload until it closes.

**To a public product: ~9 weeks. To first money: ~17 weeks.** Two to three days of Junior's recorded
time in total. Every week of it runs on machinery already proven on this workstation.

Stage 4 is longer than Fable estimated, deliberately — see D93. Room's server seams are designed but
entirely unwired; `createRoomApi` has never been called and `SERVER-CONTRACT.md` calls its endpoints
"proposed shapes for the missing implementation." That is greenfield behind an interface.

---

## The single most important sentence in this plan

**Ship Stage 3 before you build Stage 4.**

The free instrument needs no account, no server, no seam, and no payment. It is local-first by
design and 80% built. Everything that touches a network — OAuth, entitlements, the repository
factory, signed video — is Stage 4, and Stage 4 is only worth building if Stage 3 measures a
number worth monetising. The estate's entire history is of building the sophisticated thing before
the simple thing was tested. Do not do it again.

---

# Stage 0 — Hygiene and the ask

**Weeks:** ~0.5, and it overlaps week 1.
**Ships:** nothing public.
**Junior:** zero recorded hours; one WhatsApp reply.

### What happens

**The escrow, first, before anything else.** One machine currently holds the code, every credential,
the backup key, and the signing key, with no standby. D16 has been the estate's highest-ranked
overdue item for weeks.

> **AMENDED 2026-08-05 — D98 DEFERRED by founder ruling.** The production release keystore is *not*
> generated in Stage 0. Two consequences, both mechanical: **Stage 3 cannot upload to any store until
> it closes**, and the total-loss exposure stays open. Recorded as risk #37 and INPUT-91.
>
> **The two halves are separable, and the cheaper half is still available.** D16's credential and
> backup-key escrow — two off-box locations, a restored passphrase, a verified test restore, nothing
> printed to a log — needs no keystore and closes most of the exposure on its own. This plan does not
> schedule it against the founder's ruling; it records that the ruling deferred D98, not D16.

**Then the code becomes the product's.** Four small changes, none more than half a day:

| Task | Where | Why |
|---|---|---|
| `createFakeRoomAudio()` behind a dev guard | `engine.ts:107`, `AppRuntime.tsx:25,245` | D101 — a forged Caderno entry is permanent |
| `verify-apk.sh` extends to `bundle*` | `plugins/with-verified-apk.js` | D102 — the RECORD_AUDIO tripwire doesn't fire on the artifact Play actually wants |
| Bundle ID → `com.opanije.room` | app config | D92 — must happen before first publish, never after |
| The 56 in-code `GATE:` markers, swept once | non-test `src/` | D88's amendment — close, convert, or date each |

**And the slow clocks start.** Two things have lead times measured in weeks and nothing else can
compress them: the Google Play developer account under the CNPJ (INPUT-40) and the combined counsel
brief — privacy policy, consent instrument, **and the GPL question (INPUT-85)** in one commission,
which is what R78 wanted in the first place.

**And Junior gets one message.** Not three messages over three weeks — one, containing: the Capture
Day invitation with two candidate dates, the classroom-transcription ask (INPUT-78: *"tell me, voice
note is fine, how a first lesson with a total beginner actually runs, minute by minute"*), and
rough-audio permission (INPUT-72). His latency is uncontrolled; yours is not. Front-load every ask.

### Continue when

**AMENDED:** originally *"keys verified restorable from the second location."* With D98 deferred,
Stage 0 continues on the four code changes and the two slow clocks alone. The escrow condition moves
to a precondition of **Stage 3's store upload**, where it is now the binding constraint rather than a
hygiene item.

---

# Stage 1 — Capture Day and the pipeline

**Weeks:** 1–3.
**Ships:** internally — the first instructional audio Opanijé has ever owned.
**Junior:** one day, 6–8 hours.
**Spend:** the one operator consent this plan needs — a capture kit (USB interface, two mics, stands,
headphones), roughly **R$2–3k**, inside the existing M0 earmark. Everything else is labour.

### The order matters, and it is not obvious

**The pipeline is built BEFORE the recording day, against fake stems.** This is the single most
important sequencing decision in the stage, and it exists because of a verified trap: replacing the
72 synthetic WAVs trips a sha256 provenance chain (`assets.test.ts:490-523`) that **fails closed**,
and the audio generator itself hard-fails while an arrangement gate is unresolved
(`make-placeholder-audio.py:287-289`). If you discover that on the evening of Capture Day, you have
burned Junior's scarcest resource and cannot use what you captured.

So: build the stem→render pipeline in week 1, prove it end-to-end on fake stems (record yourself
clapping), settle **INPUT-87** (which arrangement is authoritative) before the day, and rehearse the
whole chain alone on Day 7. Every problem found in rehearsal is a problem Junior never sits through.

### The capture manifest

Consent first, on paper and in his own voice, **before anything rolls**. That is INPUT-89/INPUT-22,
rank 1 of the estate's six irrecoverable items, and it is non-negotiable: interactive and game use
licensed, isolated stems and one-shot sampling in scope, broad the first time (R19), bilingual.

Then, in this order:

1. **Reference pulse** — the agogô or a click Junior plays to.
2. **Isolated per-part stems** — Junior layered over the reference in headphones. S6's method at
   kitchen-table scale. Every part recorded separately; *never* a mixed performance you plan to
   separate later. Source separation will not produce clean stems and it wastes the day's authority.
3. **Four solfejo passes locked to the battery** — two parts × two speeds. Locked to the battery is
   what makes the echo loop buildable by muting at render time.
4. **The stroke one-shot library** — every stroke, several velocity layers, for the free battery's
   instruments. This is what fires when a student hits out-of-window (D77 — the drum always sounds).
5. **10–12 count-in variants**, including the return-after-absence variant (R79).
6. **The welcome, and the two next-step invitations** — price-free, per R53. No master's voice ever
   names a price or a product.
7. **Three seeded Perguntas answers** — so that surface can ship non-empty later.
8. **The partition, item by item, as he speaks it** — INPUT-21. Written down in his words while he
   is in the room. This is irrecoverable context: the rulings can come later, being in the room with
   him cannot.
9. **A dozen 30-second reel clips**, last, while the room is warm. These are Stage 3's entire content
   calendar and they cost twenty minutes at the end of a day that is already set up.

**Back up every file to two locations before dinner.** Not tomorrow.

### Then the pipeline runs

Stems → ladder renders + `AUTHORED-TIMING` grids → `npm run publish:manifest` → 621 tests green →
build → install → play. The 72 synthetic placeholders retire.

### Continue when

A full session plays end-to-end with real audio on the founder's own phone.

**First evidence: row 54** — *does scheduled audio feel like playing, or like miming?* A written,
dated, honest answer from the first two humans on earth to hear it: Rodolfo and Junior. This is the
plan's riskiest load-bearing hypothesis and it is deliberately tested in week 3, where failing is
cheapest.

---

# Stage R — The tester-facing surface

**Weeks:** unknown, and deliberately not invented. **Ships:** a door an unaided beginner can walk
through. **Junior:** one sitting, timed as below. **Runs in parallel with Stage 1** — audio capture
and surface work do not contend for the same hours.

### Why this stage exists

Ledger row 59. One unaided first-time user, on a real device, could not tell what to do, saw no game
mechanic, and could not work out how to interact. **0/10.** That is the only measured fact the
company has about its own product, and it is about the surface.

### What it is not

It is **not** a visual refresh, and it is not a re-skin of the current screens. The finding was not
*"it looks wrong"* — it was *"I could not tell what to touch"*. The thing being redesigned is the
**first ninety seconds**: what a person sees, what they are asked to do, and how they discover that
the screen is a drum. A prettier version of an illegible door is still an illegible door.

### What must be true when it exits

1. An unaided first-time user reaches the screen drum and plays, without being told how. **Measured,
   not assumed** — row 60.
2. **The play layer is on while the surface is being designed** (D94a), not added afterwards. Row 59's
   tester described the play-layer-off build as having no mechanic; designing the door around that
   build would design the door around the wrong product.
3. `EXPO_PUBLIC_ROOM_DEMO`'s two gates are separated first, so a play-layer build does not also carry
   `/review` and `/past-the-door`. That is D94a's scope and it is a precondition of everything else
   here.

### The trap this stage carries — risk #38

**A redesign with no measurement loop repeats the failure it exists to fix.** Row 59 came from
handing a build to one unaided human. The tester *programme* is suspended, but the *act* that
produced the estate's only measured fact costs one person and an hour. **Run the cheapest honest
version of it continuously** — one or two people, informally, repeatedly, throughout Stage R — rather
than waiting for the ten-tester cohort to resume. A redesign that reaches Stage 2 without ever having
been watched by a beginner is the same bet that produced the 0/10.

### Junior sits inside this stage, not after it

Charter §9 item 10 is a *ship* gate, not a design gate, so nothing compels a sitting during a
redesign. But the estate's own repeated finding is that he answers around working objects rather than
documents. **Show him the redesign at the point where it is playable but still cheap to change** —
not the current build, and not a finished one. INPUT-69, 79, 41, 62 and 88 travel with that sitting,
and `PLAN-02-RUNBOOK.md` Day 10 moves with it.

### Continue when

**Row 60 measured** — the redesigned door is self-explanatory to an unaided first-time user. Then,
and only then, Stage 2 resumes and spends the ten hand-picked testers on a surface that has already
been shown to work on somebody.

---

# Stage 2 — Ten humans  ·  **SUSPENDED 2026-08-05**

> **SUSPENDED, not cancelled.** No hand-picked tester receives a build until Stage R exits. Rows 48,
> 50, 53, 55 and 58 are all Stage 2 instruments and none of them can be measured meanwhile — they
> stay HYPOTHESIS/ASSUMPTION rather than being marked blocked, because they are not blocked, they are
> simply not yet testable. **D103's accepted risk stands and is currently unspent.** Everything below
> is the stage as it will run when it resumes.

**Weeks:** 3–5.
**Ships:** a sideloaded APK to ten hand-picked testers. Debug-signed is fine here; the production
keystore is for Stage 3.
**Junior:** 2 hours.

> **AMENDED 2026-08-05 — this stage no longer starts from zero.** A beginner has already been handed
> the app on a real device and scored it **0/10**: could not tell what to do, saw no game mechanic,
> could not work out how to interact (ledger row 59, risk #35). Two things follow.
>
> **First, the door is redesigned before the ten testers, not after.** Spending ten hand-picked people
> on a door already measured as failing wastes the scarcest evidence in the plan. How much Release 1
> scope that redesign gets is INPUT-92 — a founder call, because it may delay Capture Day.
>
> **Second, row 55's ≥7/10 criterion is now harder to judge honestly, not easier.** The temptation
> after a 0/10 is to read any improvement as success. Write the criterion down before the testers
> arrive, exactly as this plan already says, and judge it rather than negotiate it.

### Junior goes first

He sees the drum, the echo loop, the fade, the closing screen — on a working phone, with his own
sound coming out of it. In one sitting, around one real object, this discharges what the estate has
had open for weeks: **INPUT-69** (the mockup conversation), **INPUT-79** (form assent on the rendered
echo), **INPUT-41**, **INPUT-62**, and **INPUT-88** (C23's presence question). The estate concluded
this itself — he answers around working objects, not around documents. Charter §9 item 10 makes this
a gate, not a courtesy: no screen-drum surface ships without him having seen it.

**D94a makes this sitting heavier than it looks.** The play layer is on *in this build* — that is
what D94a ratified on 2026-08-05, and it is two-way because a sideload is not the free tier. What
Junior is approving is the game, not a drum. **His verdict here is also what D94b waits on**: the
one-way commitment to put the play layer in the public free room is taken at Stage 3, with row 52 in
hand rather than in advance of it. Row 52 is his verdict, in his words, written down: *does this read as
musical information, or as a verdict on the player?*

### Then nine more

The nine-question pilot (R87). Ask them the things only humans can answer:

- Did you go from voicing to playing on the screen in one sitting, unaided? *(row 55, target ≥7/10)*
- Did the echo loop read as teaching, or as a test? *(row 48)*
- When your part thinned, did you understand why? *(rows 50, 53)*
- Did it feel like playing, or like miming? *(row 54, second cohort)*

And log R75's two Android latency flags from every device, for free, to learn the real distribution
(row 58).

### Continue when — and this stage has teeth

**Row 55 MEASURED at ≥7/10.** If a beginner cannot get from voice to screen drum in one sitting,
**stop and redesign the door.** Do not proceed to distribution with a broken first session. This is
the one gate in the plan authorized to halt the launch, and it should be used if it fires.

---

# Stage 3 — Public: the free instrument

**Weeks:** 5–9.
**Ships:** `opanije.com/toca` and the Play listing.
**Junior:** one voice note to his network. That single act is the entire seed strategy.

### What goes live

| Surface | What it is | Why it is first |
|---|---|---|
| ~~**The web room**~~ | ~~Room exported to web, behind `opanije.com/toca`~~ | **WITHDRAWN — D96 REJECTED 2026-08-05.** Not the iOS version and not the primary surface. Release 1 has no iOS path and no no-install surface; INPUT-90 asks what replaces them. The web export still exists as an artifact — what is withdrawn is its promotion to strategy. |
| **The Play listing** | Under the CNPJ developer account, **production-keystore signed** | ~~The second date, offered only after someone has already played on the web.~~ **AMENDED — with D96 rejected this is the *only* public surface, and D98's deferral blocks its upload until INPUT-91 closes.** |
| **D94b — the play layer in the public free room** | The production default flips on | **Taken here, not earlier.** One-way under red line #5. Decided with row 52 (Junior's verdict), row 55 (≥7/10) and the ten testers' answers in hand — all of them produced by D94a at Stage 2. |
| **Instrumentation** | First-party only, per R50 — session started, first session completed, D7 return | The estate's two headline numbers finally get real values |

**The store-listing checklist**, all of which is cheap but none of which can be skipped: production
keystore (D98), AAB verified by the extended `verify-apk.sh` (D102), bundle ID `com.opanije.room`
(D92), replacement bilingual privacy policy live (the current one is four years stale), Data Safety
declared honestly — **no microphone, first-party analytics only** — and in-app account deletion if
accounts exist, which under D93 they do not yet, which is one more reason Stage 3 precedes Stage 4.

### The GUI design filing

R37 orders it before screens go public. If counsel's quote breaches the R$5k floor, this plan
**recommends accepting the risk and shipping**: a design registration protecting a product with no
users protects nothing worth its floor-breach. That is a founder call, and it is one of the few
genuine spend decisions in the whole sequence.

### Distribution begins the same week — not after

The build is not the launch. The four acts, in order of leverage:

1. **Junior's voice note to his 1,000+ former students.** Real people, his people, already in
   WhatsApp groups, in Salvador. His voice, his framing, R53-clean. If 5% touch it, the first 50
   users cost nothing and arrive pre-trusting. **This is the highest-leverage distribution act
   available to this company and it costs one voice note.** Row 57 measures it.

   > **AMENDED 2026-08-05 — D96 REJECTED.** The link in that voice note was the web room: tap,
   > play, no install. It is now a Play Store listing, which asks each of those 1,000 people to
   > install an Android app instead — a materially higher ask, and nothing at all for the iPhone
   > share of them. Row 57 is amended to say it measures a different act than the one it was
   > written for, and risk #36 carries the exposure. **INPUT-90 is the question this act is
   > waiting on**, and it should be answered before the voice note is sent rather than after.
2. **Reels with a playable punchline.** Twelve are already shot from Capture Day. 20–30 seconds of
   Junior playing, captioned EN/PT, ending on *"toca esse toque agora — link na bio."* One a week is
   sustainable. 800 followers is small but it is not zero, and the format is built for forwarding,
   which is where Brazilian reach actually happens.
3. **The idle outreach CRM gets a job.** `/var/www/outreach` is a working cold-outreach engine with
   two market lanes (EN-GLOBAL / PT-BR) and it is switched off. Point it at a hand-built list of 200
   batucada schools, blocos, capoeira academies and university percussion ensembles worldwide, with
   a **non-commercial** offer: a free instrument their members can practice with between rehearsals,
   played by a Timbalada-lineage mestre. Ask for nothing but a forward. This is the one channel where
   200 emails can produce 1,000 users, because each recipient is a multiplier rather than a user.
4. **Search, not subscribers, on YouTube.** 33 subscribers is irrelevant; *"como tocar ijexá"* search
   volume is not. Capture Day's teaching passes, lightly cut, titled for search, description linking
   the web room. Evergreen, compounding, zero marginal cost.

**Not proposed:** paid acquisition (no budget, CAC unmeasured), press (there is no story yet — "app
launches" is not news), influencer outreach (nothing to trade), and any in-app growth mechanic
(share/export is closed by G18/D69 and red line #6 until INPUT-71 is answered — **distribution
happens *to* the app, not *through* it**).

### Continue when

**Rows 41 and 24 MEASURED** — first-session completion and D7 return, with real values and dates,
the first genuinely MEASURED rows in the estate's history.

**Gate to Stage 4: 100 completed first sessions.** Any D7 value — the number is a baseline, not a
bar. You cannot fail a number you have never had.

---

# Stage 4 — First money

**Weeks:** 9–17. *(Fable said 3–4 weeks; verification says 5–7 for the seam work alone. Budget the
larger number.)*
**Ships:** accounts, entitlements, the course, and a live payment rail.
**Junior:** zero required — the course content already exists in Google Classroom. Optionally one
re-record day for the weakest lessons, deferrable.

### What this stage actually is

It is two projects that look like one.

**Project A — wire Room's seams (5–7 weeks).** This is the real work. `createRoomApi` is never
called, `AccountIdentityPort` has no implementation, `RemoteRenderSource` is never instantiated,
`factSender` throws by default, `catalogForPublishing()` throws unconditionally. The interfaces are
well-designed and the contract is versioned, which is a large head start — but nothing behind them
exists. Sequence: PKCE auth → SecureStore sessions → `http-repository` against
`opanije-mobile-api/v1` → entitlement reads → `expo-video` with signed playback.

**Project B — flip the rail (2 weeks, mostly founder-time and calendar).** ~9,600 lines of PHP that
have never run in production go live when one literal changes:
`OPANIJE_COURSE_ACCESS_MODE = 'dormant'` at `opanije-course-access.php:20`, master gate at
`:267-269`. **That deserves its own staged activation** — a real-payment drill first, counsel's razão
social confirmations, then the flip, then a live test purchase of a *second* course to confirm the
per-course grant works as verified (D97).

### And the takedown drill

Red line #6's operating form — signed-URL expiry, entitlement revocation, cache behaviour — is
**proven by a drill before any paid consented material ships.** Ledger row 30 is currently FALSIFIED:
there is no cross-system takedown anywhere in the estate. This is the stage that converts it, and it
is a hard requirement, not a nice-to-have. A takedown that stops at the CDN is not a takedown.

### Continue when

**Row 7 MEASURED** — course sales at R$297 against the funnel's real size. **Hold condition inherited
from M2 unchanged: fewer than 20 sales in 30 days → hold the ladder** and diagnose list, offer, or
price before any further spend. **Row 25 MEASURED in parallel** via Track B's ten hand-booked private
classes, which have been running throughout.

---

# Stage 5 — Compound

**Month 5+.** Shaped entirely by what Stages 3 and 4 measured, which is the point of measuring.

- **The atlas** (Concept B — narrated cultural rooms assembled by an agentic pipeline from the 3,400
  existing images, the Salvador POI dataset, and Junior's sofa voice memos) — **if D7 return holds.**
  A media surface without a practice loop has no retention; this bolts onto the instrument, never
  replaces it.
- **Perguntas ao Mestre** (Concept C — students ask by WhatsApp, Junior answers a handful monthly by
  name in recorded voice, Claude transcribes/translates/indexes into a permanent library) — 1–2
  vibecoding weeks, ~1 hour of Junior a month, and it is the cheapest durable differentiation
  available. It ships with the three seeded answers from Capture Day and **promises no cadence** — a
  library, not a subscription.
- **The full professional M0 shoot** — only now, sized by what retention proved worth deepening.
- **The monthly cycle** (D81) — revisited when 100 weekly actives exist to attend it.
- **The standard** (D82) — revisited when there is a corpus for it not to outrun.

---

# What must never be attempted

Print this. Each item has eaten weeks from someone.

| Never | Substitute | Why |
|---|---|---|
| **Real-time audio DSP, a native low-latency engine, Oboe/AAudio, "just a small C++ mixer"** | Another pre-rendered file. Scheduled audio with the grid read from the authored render (G10/D60/R73). | The single most dangerous attraction in the estate. Nobody here can debug a buffer underrun. |
| **Custom native modules / ejecting from Expo** | Expo config plugins — `with-verified-apk` already proves the pattern. If a capability isn't reachable in managed Expo, redesign the feature. | The moment `android/` stops being disposable prebuild output, every upgrade becomes archaeology. |
| **iOS, in any form, including "just checking if it builds"** | The web room *is* the iPhone version (D96). | No Mac, no Xcode, no signing identity. Permanently infeasible from this machine. |
| **A new backend, a Node server, any second stack on the VPS** | The existing mu-plugin PHP + `opanije-mobile/v1`. Every server feature is a new endpoint in that contract. | D91. 9,600 lines already written, deployed, and versioned. |
| **Subscriptions, renewals, dunning** | One-time purchases. A manually-renewed season pass if the cycle ever sells. | Recurring billing is a company-sized project. |
| **Google Play billing / IAP** | Web checkout (Pix), server-side entitlements, an app that sells nothing (D87). | Weeks of integration, 15–30% margin, an anti-steering brief — for a store with no audience. |
| **Per-device latency calibration or any accuracy readout** | The generous binary window; log R75's two latency flags from day one. | Barred by Charter §9 item 11 *and* technically unsound — the offset is unknowable. |
| **AI stem separation or audio cleanup on Junior's recordings** | Capture stems and one-shots *as* stems and one-shots on Capture Day. | It won't produce clean stems, it wastes the day's authority, and generated audio drifts toward red line #4. |
| **A custom sync engine or an offline-download library** | Local-first AsyncStorage for everything free; idempotent progress writes for everything owned; streaming with HTTP caching per D27. | Conflict resolution is a graveyard. Facts survive the network (E16); nothing else syncs. |
| **Device-farm QA, or calling emulator evidence device evidence** | The emulator harness for regressions, two physical phones (D99), and the ten Stage-2 humans. | Audio feel and touch latency are founder-time, scheduled — not hoped for. |
| **Disabling the audio provenance test to make a build pass** | Regenerate the manifest (D100). | It failing closed is the feature: it proves the audio in the build is the audio Junior consented to. |

---

# The governance dividend

244 decisions are an asset when they are *spent* — cited to end a discussion in five seconds — and a
liability when they only accumulate. The estate was built by a PM-and-founder dialogue that no longer
runs daily. A solo builder needs the Charter as **a pre-answered question bank consulted at design
time**, not a review gate passed at ship time.

**Kept alive — four documents, and that is all:**

- **`CHARTER.md`** — read before any design session. Sovereign, unchanged.
- **The vocabulary sheet** (METHOD §5) — pinned next to `strings.ts`. Every user-facing string passes
  the sentence test *when it is written*. This is where classification leaks back in, so this is the
  one live review.
- **The Charter §9 prohibition list** — handed verbatim to an independent review model once per
  stage: *"find violations of these fifteen lines."* That turns the Charter into automated review
  fuel instead of ceremony. One review round per stage replaces the eight-round protocol.
- **`LEDGER.md`** — the only register this plan *adds* to. Every stage's exit number is written in as
  a dated MEASURED row. The ledger is the estate's conscience and it finally gets fed.

**Frozen — history, not process:** `DELTAS.md`, `RECOMMENDATIONS.md`, `CONTRADICTIONS.md`,
`FORKS.md`, `sessions/`, and Room's `GATES.md` (after the one-afternoon sweep of its 56 in-code
markers, per D88's amendment). Frozen means read-only and cited when useful, never extended. A build
decision that would once have become a numbered delta becomes one line in `BUILD-LOG.md`.

**The one new ritual:** a weekly thirty-minute WhatsApp exchange with Junior — this week's screens or
clips, next week's asks. Red line #1 as a habit rather than a gate queue. His formal assents get
gathered in working sittings around real objects, which is how he actually answers.

---

## The number that governs everything

**100 people who played twice.** Not installs. Not follows. Returns.

If six months of this cannot produce 100 second sessions, the app is not a standalone business, and
it should settle honestly into being the immersion funnel's trust surface — which is still worth
having built, at roughly the cost this plan spends. Say that now, while it is cheap to say, so that
it is not a crisis later.

---

*The app is the instrument and the funnel. The business is the human layer. Build the instrument,
give it away, and find out whether anyone plays it twice.*
