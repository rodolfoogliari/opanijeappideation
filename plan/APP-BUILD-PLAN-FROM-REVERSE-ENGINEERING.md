# Opanijé — App Build Plan from the Reverse-Engineering Sweep

**Status.** Authored 2026-08-17 by the Fable program-plan seat, from the four-competitor
reverse-engineering sweep (Drumgenius, PercussionTutor, eBatuque, Brazilian Drum Machine/Lumbeat),
its nine area verdicts, the Capture Day recordable-content determination produced in the same
sweep, and the current state of `apps/opanije-room` verified against the tree this session.
A **new dated document** under the estate's supersession pattern (D88 — `plan/` is history and no
existing file is edited by this one). **It decides nothing, closes no input, and adds no numbered
row.** Where it disagrees with `plans/PLAN-01-BUILD.md`, `BUILD-LOG.md`, `CHARTER.md` or a
register, they win. Boarding any milestone below is one line in `BUILD-LOG.md`, per D88.

**Authority basis, read this session:** `apps/opanije-room/README.md` and `docs/ARCHITECTURE.md`
(current app state, r8), `docs/FORK-K-DAY-7.md`, `docs/GATES.md`, `docs/ROUTE-TO-DONE.md`,
`docs/ACCEPTANCE.md`; `plan/THE-GAME.md`, `plan/THE-STANDARD.md`,
`plan/RELEASE-1-EXPERIENCE-SPEC-V1.md`, `plan/PRICING-AND-ACCESS.md`, `plan/M0-SHOOT.md`,
`plan/M0-PRODUCTION-PACK.md`; `CHARTER.md`; `registers/DELTAS.md` (D73–D104 incl. D84/D86/D87/D89,
D92–D103), `registers/INPUTS.md` (as updated through 2026-08-17); `BUILD-LOG.md` (through the
2026-08-15 ratification sweep and the 2026-08-17 cycle confirmation); `plans/PLAN-01-BUILD.md`
(the stage sequence of record); `research/ENGAGEMENT-NEUROPSYCHOLOGY-EVIDENCE-BASE.md` and
`research/OPANIJE-GAME-MECHANICS-RESEARCH-REVIEW-2026-07-31.md`.

**What the sweep returned.** Five KEEP-OURS verdicts, four ADOPT verdicts, zero BUILD-NEW. Every
adoption below passed the hard filters: red line #5 (commons free forever), R53 (no recording
names a price or product), the cycle is Release 2+ and never named in recordings (D84, confirmed
2026-08-17), D80's celebration bound, credit-the-human (INPUT-88 answered: the presence lamp shows
live human presence only), one provider / one screen lease, pt-BR teaching with Junior's speaking
voice never navigating, and subtitles on spoken framing assets (INPUT-14 as narrowed 2026-08-15).
Adoptions that failed a law were auto-rejected and are listed in §6 so nobody re-imports them.

---

## 1 · How this plan composes with the sequence of record

`plans/PLAN-01-BUILD.md` owns the spine: **Stage 0 (hygiene) → Stage 1 (Capture Day + pipeline) →
Stage R (the tester-facing surface, no estimate, INPUT-92 answered "whatever it needs") →
Stage 2 (ten humans, SUSPENDED until Stage R exits) → Stage 3 (public free instrument, Play
listing only) → Stage 4 (first money, after Stage 3 shows pull) → Stage 5 (compound).**

This plan does not move a stage boundary. It does three things:

1. **Slots the four ADOPT verdicts into that spine as bounded milestones** (RE-2, RE-3, RE-4
   below), each with budget, lane, and Junior-material dependency.
2. **Converts the KEEP-OURS residues into their cheapest lawful form** — one pipeline acceptance
   gate (RE-5), one question added to an ask that is already owed (§5), and nothing else.
3. **Names the store-shippable tail and its owners**, so "boardable now" is never confused with
   "shippable now": the Phase-5 order is design freeze → GUI industrial-design filing → live
   privacy policy → store submission (`README.md`), and the upload is mechanically blocked by
   INPUT-91 (keystore + escrow, D98 deferred) and INPUT-40 (CNPJ store account).

**Dependency vocabulary used throughout:**

- **NONE** — ships complete against placeholder renders; no Junior material, no capture, no new
  line on his day.
- **CAPTURE-DAY** — the milestone's real material is recorded on the Capture Day; the build side
  ships empty-safe before it, and the day's manifest (per `plan/M0-PRODUCTION-PACK.md` and the
  recordable-content determination) already carries the items.
- **POST-CAPTURE** — executes only on the day's processed output (stems → renders → regenerated
  manifest under D100).

**Budgets** are vibecoding-sized per PLAN-01: **S** ≤ 1 focused day, **M** 2–5 days, **L** a week
or more. **Lanes:** Opus = core play / audio / money-adjacent; Sonnet = content plumbing /
localization. Every card, both lanes, carries the §4 verification bar — the Room repo runs at
highest scrutiny regardless of who implements.

---

## 2 · The ordered milestone list

### Phase A — boardable NOW (no content dependency; Stages 0, R, and 1-in-parallel)

| # | Milestone | Source | Budget | Lane | Junior material |
|---|---|---|---|---|---|
| RE-0 | Stage-0 code residue closed: D101 fake-audio guard, D102 `verify-apk.sh` → `bundle*`, one sweep of the 56 in-code `GATE:` markers (D88 amendment). Pre-check `BUILD-LOG.md` before boarding — any part may already be done | Ratified D101/D102/D88; not a sweep verdict, but everything below builds on a tree where these hold | S | Sonnet (D101 diff gets the blind-Opus pass) | NONE |
| RE-1 | **D94a gate separation** — the play layer gets its own build-time opt-in, independent of the demonstration route tree (`EXPO_PUBLIC_ROOM_DEMO` currently sets both `playLayerEnabled`, `AppRuntime.tsx`, and `REVIEW_ROUTE_TREE`, `_layout.tsx`); tester builds then carry the game with `/review` off | D94a RATIFIED; BUILD-LOG 2026-08-05 names it a precondition of the Stage-R redesign | S | Opus | NONE |
| RE-2 | **Sitting survives display sleep and lock** (ADOPT, Area 2b — *Drumgenius* background playback is explicitly praised in its reviews; *eBatuque* ships offline+background as core practice-room utility; the market proves a practice loop that dies with the display is a broken loop). Scope: the **held RoomSession lease only** — E3 props the phone at arm's length and the listen/echo phases leave the screen untouched for minutes, so the display will time out mid-sitting. Partial treatment already exists and is the card's starting point: `src/app/room.tsx:29` `useKeepAwake('room-session')`, `src/audio/engine.ts:305` `shouldPlayInBackground: true`. The card completes it (drum surface, deliberate lock, cycle-credit accumulation while the display is dark), decides in-card between lease-scoped keep-awake and the players' stays-active treatment — preferring whichever adds **no lock-screen media-notification surface** — and proves it in the emulator harness | Area 2b ADOPT; Experience Spec §6 already owes "audio continuity when the screen dims" | S–M | Opus | NONE |
| RE-3 | **Stage-R door: competitor-informed acceptance criteria and the returning-student fast path** (ADOPT, Area 6 — *Drumgenius*'s first-minute funnel and *Brazilian Drum Machine*'s open-straight-into-a-working-groove set the time-to-first-sound bar; *eBatuque*'s negative proofs set the floor: login demanded on every open, unlabeled instrument icons — "sou analfabeta em percussão" — and an entry interstitial are its most-hated traits; *PercussionTutor*'s lone Brazilian review is a failed first session). Lands **inside** the Stage-R redesign INPUT-92 already mandates, as its measurable criteria: (a) sign-in once — a returning student cold-starts to Home/today's session (E6) with no re-auth and no interstitial ever; (b) every part choice labeled in plain pt-BR/EN words with zero percussion-literacy assumption; (c) time-to-first-sound from sign-in instrumented through the existing funnel and budgeted in-card; (d) E4's law preserved — **nothing audible before sign-in**, so the "free preview before the door" half of the funnel is auto-rejected and the presentation screen keeps carrying the whole conversion. Screen forms are authored in Claude Design (`mobile/screens/`, project e5cc196e) and imported — never drawn in the CLI | Area 6 ADOPT; ledger row 59 (0/10) and row 60 own the stage's exit | M (criteria + instrumentation; the redesign itself is Stage R's own unestimated work) | Opus | NONE |
| RE-4 | **Rhythm dossier data spine, empty-safe** (ADOPT, Areas 3b + 4 merged — one schema, one surface pass). Five fields on the catalog row and the room's identity surfaces: (1) stable traditional name with an **append-only alias list** so a display rename can never break search or memory (*eBatuque*'s renaming update severed its users' research into the tradition — encode the lesson); (2) credit line naming Junior as performer — structural under red line #6, and *PercussionTutor*'s credited-lineage players are its #1 praise theme while *eBatuque* claims "percussionistas reconhecidos" and never names one; (3) a 1–2 sentence "where this toque sits" cultural note as app text, pt-BR + EN — *Drumgenius*'s master-name-source-history provenance line is the stated reason users trust it, and app TEXT doing the heavy lifting is Junior's own script-economy constraint; (4) canonical tempo anchor as data (INPUT-59 stays data-owned — *Brazilian Drum Machine*'s per-rhythm canonical tempo range is the model); (5) the narration seam wired to `src/data/api.ts`'s existing validated narration read path, BUILT-NOT-WIRED until Capture Day media exists, partition validation fail-closed. Surfaces: today's-session card (E6), choose-part header, room entry moment — **never the map cells**, which stay quiet booleans (FORK-K §5.6). Absent content renders **nothing**: no placeholder prose, ever — only Junior's words describe the tradition. Placeholder demo data plainly synthetic, gated exactly like today's placeholder rhythm (`src/data/catalog.ts` GATE: INPUT-53/80, INPUT-52) | Areas 3b + 4 ADOPT | M | Sonnet | NONE to build; content is CAPTURE-DAY (see RE-9) |
| RE-5 | **Stem→render pipeline proven on fake stems, with a loudness-normalization acceptance gate** — PLAN-01 Stage 1's own pre-day sequencing rule (settle INPUT-87, prove the chain end-to-end before Junior sits down; `make-placeholder-audio.py` hard-fails while the arrangement gate is open, and the sha256 provenance chain fails closed by design, D100), plus the sweep's one Area-2 residue: production renders are loudness-normalized at acceptance so *eBatuque*'s standing complaint — "quieter than other phone media", no master fader — never becomes our review theme | PLAN-01 Stage 1; Area 2 KEEP-OURS residue | M | Opus | NONE (fake stems); the gate then applies POST-CAPTURE |

**Ordering inside Phase A:** RE-0 → RE-1 first (everything Stage-R touches builds on them), then
RE-2/RE-3/RE-4 in parallel with RE-5 — surface work and pipeline work do not contend for the same
hours (BUILD-LOG 2026-08-05: Stages 0 and 1 run unchanged through the redesign).

### Phase B — blocked on Capture Day (the day itself is operator-scheduled; irrecoverability governs, D86)

| # | Milestone | Source | Budget | Lane | Junior material |
|---|---|---|---|---|---|
| RE-6 | **Real-audio ingestion**: Capture Day stems → ladder renders + `AUTHORED-TIMING` grids → `npm run publish:manifest` → full suite green → build → install. The 72 synthetic placeholders retire; the provenance chain is **regenerated, never disabled** (D100); RE-5's loudness gate is applied to every accepted render | PLAN-01 Stage 1 | M | Opus | POST-CAPTURE |
| RE-7 | **Count-in bank landing** — the recorded bank (the determination closes INPUT-74's count at **twelve + COUNTIN-RETURN**, pending the founder's confirmation of that closure) replaces the three placeholder assets; rotation and persistence are already BUILT (`src/data/countIn.ts`, FORK-K §2.1), so this is asset wiring plus tests. Bank stays invisible and unenumerable (FORK-K §3.4 — a visible collection is an unlockable) | G16/R79; INPUT-74 | S | Sonnet | POST-CAPTURE |
| RE-8 | **Commons rooms: congo and cabila at on-ramp depth** — the 2026-08-14 founder expansion of INPUT-80 (ijexá + congo + cabila; Junior's availability-and-order half still open for the new two). Each room enterable **voice-first** (G4, D75): requires the commons solfejo recorded **locked to each commons battery** — the recordable-content determination's Block-E addition; a commons room shot without locked solfejo is a room whose door cannot open. Catalog rows arrive through RE-4's schema; entrance calls as captured | D75; D73/R88; INPUT-80 | M–L | Opus (room/audio) with Sonnet plumbing subtasks | POST-CAPTURE |
| RE-9 | **Dossier content landing** — per-item traditional name in Junior's naming, credit line, one **verbatim** "what this is" line from the captured narration transcript (pt-BR primary, EN subtitle string per E11/INPUT-14), and per-item partition values (INPUT-21/52) enforced fail-closed through the existing read path. Which free rooms carry it is the founder's call — anything shown in a free room is ONE-WAY under red line #5 | Areas 3b + 4 ADOPT, content half | S–M | Sonnet | CAPTURE-DAY (narration + partition are on the day's manifest); lands POST-CAPTURE |
| RE-10 | **Spoken framing assets + subtitles**: the welcome into `src/app/welcome.tsx`'s wired-and-empty slot, the two next-step invitations into the ending's existing consumers (`src/i18n/strings.ts`), EN subtitles on all spoken framing assets — INPUT-14's narrowed scope. R53 checked per asset; the cycle is never named (D84) | E4, E7/E10, E11; INPUT-14 | S–M | Sonnet | POST-CAPTURE |

### Phase C — human evidence gates (not agent cards; owners named; the plan schedules nothing here)

| Gate | Owner | What it settles |
|---|---|---|
| Junior's sitting, at the point where the redesigned surface is playable but still cheap to change (BUILD-LOG 2026-08-05) — a D94a build via RE-1 | Founder + Junior | INPUT-69 (screen drum), INPUT-79 (rendered echo — after INPUT-78's classroom transcription has shaped it), INPUT-41 (fixed ladder vs live muting — the one door that could reopen Area 2's mixer question), INPUT-62, row 52. Charter §9 item 10 discharged before any public ship |
| Stage 2 resumes: ten hand-picked testers (D103 stands, unspent) | Operator/founder | Rows 48/50/53/54/55/58; row 55 ≥7/10 is the one gate authorized to halt the launch |
| D94b — play layer default ON in the public free room | Founder | ONE-WAY under red line #5; taken at Stage 3 with rows 52 and 55 in hand |
| Handset-and-ear pass on the founder's phone (D99; the current head is not VERIFIED ON A DEVICE anywhere) | Operator/founder | Downbeat alignment, `full|thin` audibility, additive-strike masking, touch latency — feel evidence no emulator supplies |

### Phase D — the store-shippable tail (Stage 3; sequencing is the Phase-5 order, `README.md`)

| # | Milestone | Source | Budget | Lane | Junior material |
|---|---|---|---|---|---|
| RE-11 | **Store artifact readiness**: production keystore signing path once INPUT-91 closes; AAB verified by the D102-extended `verify-apk.sh` (the RECORD_AUDIO tripwire must fire on the artifact Play actually requires); bundle ID → `com.opanije.room` at the last responsible moment before first upload, never after (D92 — the rename also touches the keychain service string and deep links); honest Data Safety declaration — no microphone (`allowsRecording:false` is structural), first-party analytics only; store listing copy passes the sentence test and names no price (D87 — the app sells nothing and links to no checkout, which makes the listing trivially compliant) | D92/D98→INPUT-91/D102/D87 | M | Opus | NONE |
| — | External blockers, owner-side, already registered: INPUT-40 (CNPJ Play account — longest external lead time), INPUT-91 (keystore + escrow — **no store upload is possible until it closes**), INPUT-39 (bilingual privacy policy live), R37 GUI design filing (founder already ruled: accept the risk and ship if the quote breaches the R$5k floor), INPUT-90 (the iOS / no-install answer — **before** the distribution acts, especially Junior's voice note), INPUT-85 (GPL relicensing, in counsel's combined brief) | — | — | — | — |

### Beyond store-shippable (named, not planned here)

**Stage 4 — first money** (D93: seam wiring is greenfield behind a designed interface, 5–7 weeks —
PKCE auth → SecureStore sessions → http-repository against `opanije-mobile/v1` (D91) →
entitlement reads → `expo-video` signed playback; the rail flip with a staged activation and one
live second-course test purchase, D97; and the takedown drill that converts ledger row 30 —
red line #6's operating form, scope ruled 2026-08-14: everything Opanijé controls, excluding
copies already on a device). It starts only after Stage 3's gate — 100 completed first sessions.
**Ship Stage 3 before you build Stage 4** is PLAN-01's single most important sentence and this
plan repeats it rather than re-deriving it.

---

## 3 · Boardable NOW versus blocked, in one place

**Boardable today, in order:** RE-0, RE-1, RE-2, RE-3, RE-4, RE-5. None consumes Junior material,
none adds a line to his day, all six run on placeholder renders, and together they mean Capture
Day's output lands in an app whose door, dossier spine, pipeline and gate separation are already
waiting for it. RE-3 and RE-4 ship the app-side seams **empty-safe** — the competitor-proven
surfaces exist before the content that fills them, which is the correct order because the content
is one-way and the seams are not.

**Blocked on Capture Day (and only on it):** RE-6 through RE-10. The day itself is
operator-scheduled (D86; `plan/M0-PRODUCTION-PACK.md` §5 owns the blanks); its four one-way parts
are untouched by this plan. The recordable-content determination from this sweep is the day's
content companion; the one manifest delta this plan depends on is its Block-E addition — commons
solfejo locked to the commons batteries — without which RE-8's rooms cannot open voice-first.

**Blocked on people, not on capture:** everything in Phase C, plus the Phase-D external blockers.
No agent card below may silently absorb one of these; each is a named gate with a named owner.

---

## 4 · Verification spec

### 4.1 · The common bar — every milestone, both lanes

The Room repo runs at highest scrutiny: adversarial verification on core screens, pixel-verified
claims, device-run preconditions. Concretely, a milestone is `DONE` only with:

1. **`npm run gate` green** — clean ESLint, strict TypeScript, full Jest including the
   prohibitions 1–20 registry (`src/__tests__/prohibitions.test.ts`) and the gates test. Recorded
   totals rot; the current run is the evidence.
2. **No new Android permission**: `scripts/verify-apk.sh` green on the built artifact. The
   standing trap is expo config plugins adding `RECORD_AUDIO` by default; after RE-0, the check
   must also cover `bundle*` outputs (D102).
3. **Strings discipline**: every new user-facing string ships pt-BR + EN, passes the sentence test
   (METHOD §5 — if it can be read as a statement about the student rather than the round, it is
   wrong), uses no Caderno vocabulary (R86), names no price or product (D87/R53), and never
   presents absent content as placeholder prose.
4. **Adversarial pass on the actual diff**: a blind Opus reviewer receives the diff, the Charter
   §9 prohibition list verbatim, and the milestone's own must-not-introduce list (below), and
   hunts violations plus correctness defects. Findings are fixed and the fix re-verified by
   reading the code, not the fixer's claim — each review round re-verifies the last (the
   eight-round protocol collapsed to one honest round per milestone, per PLAN-01's governance
   dividend).
5. **Pixel-verified claims**: any "renders correctly" claim is backed by a capture from the
   emulator harness (`~/scratch/room-avd-smoke` pattern; emulator and `adb` share one
   `netrun.sh` namespace, launched from a fresh login), at default and 200% text where layout is
   touched. A fetched export or green build proves nothing about a screen.
6. **Device preconditions labeled, never simulated away**: evidence is classed per
   `docs/ACCEPTANCE.md` — BUILT / WIRED / MODELLED IN MEMORY / EXECUTED IN A BROWSER / VERIFIED
   ON A DEVICE — and anything whose truth is *feel* (audio through a speaker, touch latency,
   drift) stays `OPEN` until the handset-and-ear pass. Emulator evidence is never called device
   evidence.

### 4.2 · Per-milestone specifics

| # | Verification beyond the common bar | Must NOT introduce |
|---|---|---|
| RE-0 | D101: a test that fails if `createFakeRoomAudio()` becomes reachable from production code again. D102: a deliberately permission-polluted `bundle*` build fails the check. Gate sweep: `node scripts/check-gates.mjs` before/after — every marker closed, converted to a BUILD-LOG line, or dated; none silently deleted | Answering any gate's question in code — a `GATE:` marker records a decision reserved to a person |
| RE-1 | A `playLayer`-on build's production route set omits `/review` and `/past-the-door` (walk the export route table, as `walk-web-routes.sh` does today); a demo build still reaches them; `closing.test.tsx` families updated to the new gate without weakening the demo-off default (D94b is not flipped here) | Any change to the public free-room default — that is D94b, founder-owned, Stage 3, ONE-WAY |
| RE-2 | Automated emulator check in the harness: start a sitting, force display off and a lock mid-phase (`adb shell input keyevent`), assert the battery loop continues and accumulated cycle credit survives to Closing; quiet close and lease release still silence everything (the Ensaio rule: a practice surface HOLDS the lease or its audio outlives the screen); app-switch does **not** grant endless background playback beyond the held sitting; `verify-apk.sh` green — zero new permissions | Audio outliving the lease; a lock-screen media-player chrome that reframes the Room as a background utility (the endless-session default the research base excludes, game-mechanics review §10); any new manifest permission |
| RE-3 | Time-to-first-sound events flow through the existing funnel with the R81 baseline label (BASELINE-RECORD.md is written before numbers exist); cold-start-signed-in mounted-router test lands Home without re-auth, plus an emulator restart proving it on the artifact; PT/EN part labels present and read by accessibility tools; 200% text walk of the door; the silent-before-sign-in invariant asserted (E4) — no audio route reachable pre-guard; Stage R's own row-60 measurement (an unaided beginner, continuously, per risk #38) stays the stage's exit and is not replaced by these checks | Anything audible before sign-in; an entry interstitial of any kind; a second sign-in ask on reopen; percussion-literacy assumptions in labels; scoring the door redesign by these criteria alone while skipping the human measurement loop |
| RE-4 | Schema round-trip tests incl. append-only alias behavior (a rename adds, never replaces; old name still resolves); PT/EN render test per field; absent-content-renders-nothing snapshot per surface; map cells unchanged (boolean, no text — assert against FORK-K §5.6); narration seam exercised against the fail-closed partition validator with `withheld` and unknown values; prohibitions suite green (no completion fraction, no level word, no lock/timer reading on unvisited rooms — Charter §9 item 2) | App-authored liturgical prose or paraphrase; price/product wording near a master's material (R53/D87); presentation of `archive-only`/`withheld` items; standing or lineage vocabulary in the credit line (R86 — it credits the human, never grades one); lighting or texting the map cells |
| RE-5 | The full chain runs on self-recorded fake stems end-to-end (clap test) before the day; INPUT-87 confirmed settled before the day or the card reports `BLOCKED` naming it; loudness gate: accepted renders measure within the declared LUFS window and the gate rejects a deliberately quiet fixture; provenance chain intact (`assets.test.ts` sha256 family green after regeneration) | Disabling the provenance test to make a build pass (D100 — failing closed is the feature); DSP "fixes" on stems (no AI separation, no cleanup — never-attempt table) |
| RE-6 | Everything RE-5 asserts, on real output; a full session plays end-to-end with real audio on the founder's phone (PLAN-01 Stage 1 exit); row 54's question (playing or miming?) answered in writing by the first two humans to hear it | Shipping any recording whose consent instrument is not executed (red line #6 — does not ship, no exceptions) |
| RE-7 | Rotation test across simulated sessions incl. the persisted index (already covered — extend to the real bank size); RETURN variant selection rule tested; no surface enumerates or names variants | Any UI acknowledging the bank exists ("a new call today" is a collection, a collection is an unlockable) |
| RE-8 | Per-room asset suite: every rung battery omits the selected part, voice-over equals rung battery + syllable line, loop seams clean (extend the existing asset reconciliation to each commons rhythm); voice-first entry walked in the mounted router per room; catalog rows carry RE-4 fields or render empty-safe | Inventing teaching order (Junior confirms order for congo/cabila — INPUT-80's open half); shipping a room whose locked solfejo was not captured (no standalone-solfejo fallback — R63: locked is never derivable from standalone) |
| RE-9 | Verbatim-only test: rendered narration text matches the transcript source exactly; partition fail-closed proven per item; free-room carriage matches the founder's ruling and nothing else | Editing Junior's words; defaulting an item's partition; carrying dossier content into a free room without the ruling (ONE-WAY under red line #5) |
| RE-10 | Welcome ≤ the determination's length target and R53-clean (checked against transcript); both invitations price-free, product-free, cycle-unnamed (D84); subtitle track present for every spoken framing asset, EN following E11's rules; welcome slot's silent-fallback behavior retained when the asset is absent | The master's voice navigating the app (voice owns warmth and identity; app text owns navigation); any recording naming what expires |
| RE-11 | `verify-apk.sh` (extended) green on the exact AAB uploaded; bundle-ID rename executed once, immediately before first upload, with keychain/deep-link touchpoints re-tested; Data Safety answers cross-checked against the manifest and the first-party-only fact pipeline; store listing strings through the sentence test | Uploading anything before INPUT-91 closes; a listing that names the price of anything (there is nothing to name — D87) |

---

## 5 · Register-side residues from the KEEP-OURS verdicts (no code, one ask)

- **Area 3 (teaching method):** fold exactly one question into the INPUT-78 classroom-transcription
  ask that Stage 0 already sends Junior — *when he teaches, does he expose the timeline/marcação,
  and with which instrument?* The answer, not Drumgenius's clave-toggle, decides whether a
  reference-emphasized render state ever joins the ladder (the proven classroom is the loop's
  specification, THE-GAME §3.4). One sentence in a message already owed; no card.
- **Area 1 (practice loop):** no card. The loop's open items are the estate's own gates
  (INPUT-78/79, INPUT-69) and travel with Junior's sitting (Phase C). The competitor field proved
  the thesis: the market's best loop — PercussionTutor's isolate-then-mute "become the missing
  player" — is structurally ours in stronger form, with the audible feedback channel and empty
  chair no competitor has, and with zero microphone.
- **Area 5 (progression):** no card. The category shipped nothing to adopt — all four competitors
  rate ABSENT on progression — and its complaint boards independently ratify our two hardest rules
  (eBatuque wiping saved state ↔ our monotonic map and permanent Caderno; its lifetime→subscription
  betrayal ↔ red line #5's ratchet). The one market-proven retention mechanism, PercussionTutor's
  free content-drop cadence 13 years running, is already ours structurally (D75's arc; every
  commons addition permanent under red line #5) — future drops are INPUT-80/capture-owned, not
  buildable.
- **Presence lamp:** INPUT-88 is answered — the lamp shows **live human presence only**. Release 1
  has no live-presence surface (the cycle is Release 2+, D84 confirmed 2026-08-17), so the lamp
  ships dark and no play surface makes a presence claim. INPUT-60 (what is photographed for the
  play screen) remains open and is a Capture Day Block-J concern, not a build card.

---

## 6 · What this plan deliberately does NOT do

Scope discipline, stated so nobody re-imports a rejected mechanism or re-opens a settled door:

1. **No engraved notation, score view, tab, staff, or grid on any surface** — G2/D53 is
   FOUNDER-DECIDED product-wide. eBatuque's per-loop notation and the sweep's score-follows-playhead
   "unclaimed win" are auto-rejected as surfaces: the eight locked solfejo passes ARE the score
   synced to the playhead, in the master's voice.
2. **No live per-part mixer, no stem faders, no support-part mute at runtime** — §3 prohibition 16;
   the ladder is authored. eBatuque's mixer enters only if Junior himself answers INPUT-41 the
   other way at his sitting, around the working object — never by competitor imitation.
3. **No stem/WAV/MIDI export, no DAW citizenship, no share/export of any kind** — G18/D69,
   INPUT-71 in the counsel brief, THE-STANDARD §2: the recordings, stems and renders are never
   published; the corpus is the priced scarcity.
4. **No generative recombination, humanization sliders, or algorithmic rearrangement of Junior's
   material** — red line #1 and the game-mechanics review §5.4: "variable" means complete,
   master-designed, authority-approved scripts. Session-to-session variety is carried by the
   twelve-variant count-in bank and the authored rung set, nothing else.
5. **No full background-playback posture, no lock-screen media chrome, no gig-metronome mode** —
   RE-2 adopts exactly the narrow half the laws permit: the held sitting survives the display; the
   Room remains a session with a musical close, not an endless loop (review §10).
6. **No recording, listening, or video-record-your-practice** — D26; structurally
   `allowsRecording:false`; eBatuque's record feature is auto-rejected.
7. **No engagement mechanics at the free door** — G15/D66 stands; INPUT-84's reading stays the
   founder's; nothing here touches streaks, XP, goals, badges, ranks, comparison, or purchasable
   anything (Charter §9, all twenty prohibitions).
8. **No commerce in the app, no IAP, no Play billing, no subscriptions, no checkout link** — D87.
   The quarterly R$97 cycle is Release 2+ (D84, confirmed 2026-08-17) and is never named in any
   recording or surface this plan ships.
9. **No iOS work of any kind** — D96 REJECTED; INPUT-90 owns the answer and blocks the
   distribution acts, not the build.
10. **No notification scheduling** — that is Fork-K P1's own track, blocked on counsel's INPUT-39;
    no RE card adds `expo-notifications` or any permission.
11. **No new backend, no second stack** — D91: every server feature is a new endpoint in the
    mu-plugin `opanije-mobile/v1` contract, and none of it starts before Stage 4's gate.
12. **No native audio engine, no DSP tempo-stretch, no per-device latency calibration** — the
    never-attempt table stands; the competitors' loudest complaint class (Drumgenius's stretch
    artifacts, PercussionTutor's varispeed pitch-shift) is avoided categorically because every
    tempo step is Junior actually playing at that speed.
13. **No hand-drawn UI in the CLI** — new or changed screen forms are authored in Claude Design
    (`mobile/screens/`, project e5cc196e) and imported; the CLI wires.
14. **No decisions** — this plan closes no input, flips no default, adds nothing to the free tier,
    amends no capture manifest (the Block-E solfejo addition is the recordable-content
    determination's to propose and the operator's to accept), and re-litigates nothing REJECTED or
    DEFERRED. Where a milestone meets a named gate, it ships empty-safe and waits.

---

## 7 · The one-line summary the board needs

Six cards are boardable tonight on placeholder audio — RE-0, RE-1, RE-2, RE-3, RE-4, RE-5 — and
together they make the app **ready to receive** Capture Day rather than blocked behind it; five
more (RE-6–RE-10) unblock the moment the day's files are backed up to two locations before dinner;
the store tail (RE-11) is mechanical once the operator-owned gates (INPUT-91, INPUT-40, INPUT-39,
INPUT-90, R37) close in the Phase-5 order; and the sweep's verdict on the market is that our laws
are not a handicap to engineer around but the product's edge — every ADOPT above is a competitor
proving demand for something our architecture does in a stronger, lawful form.

*Authored 2026-08-17 by the Fable program-plan seat under D88's supersession pattern. Nothing here
is measured evidence; boarding any milestone is one `BUILD-LOG.md` line; every form question on
the tradition's material remains Junior's.*