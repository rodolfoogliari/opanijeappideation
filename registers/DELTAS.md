# Opanijé — Delta Register (D1–D83)

**Status.** Register of record for this series as of 2026-08-03, under D83 (Addendum 04 §7).
**Supersedes.** The per-session tables in `sessions/` for this series, which remain readable as
derivation history but are no longer the register.
**Range.** D1 through D83.
**Rule.** Rows are appended, never rewritten. A row's status may change; its claim may not.

---

A delta is a change to material the estate already carries as ruled or as plan-of-record: it names
what was, what is now, and it requires the founder's ratification to become fully operative. Deltas
issued inside a session document are operative on issue where that document says so, and reversible
at review; none of D1–D83 touches a red line. No ratification block has yet been returned for
D1–D70; Addendum 04 §9 puts one in front of the founder for D71–D83, of which D79 alone was put
separately and ratified. This file is now the register; the per-session delta tables in `sessions/`
are derivation history.

**Status vocabulary.** RATIFIED — explicitly ratified by the founder. ADOPTED — operative as
plan-of-record on issue, reversible at ratification review. PROPOSED — inoperative until ratified.
SUPERSEDED BY Dxx. WITHDRAWN. Where an issuing document used its own status word, that word is
preserved in quotes.

**Door labels** (D83 item 2). ONE-WAY — expensive or impossible to reverse: consent scope, anything
given to the free tier (red line #5 makes it permanent), the fixed reference dialect, publication of
the standard, and anything shot at M0. TWO-WAY — revisable on evidence. Labels taken from the
estate's own reasoning where it states one; otherwise marked "(derived)". Closed rows carry "—".

**Source keys.** v2.0 = `plan/PRODUCT-GOALS-VNEXT-CONSOLIDATED-V2.md` · v2.1 Amendments =
`sessions/PLAN-AMENDMENTS-FOR-V2.1.md` · R1 Addendum S2 =
`sessions/RELEASE-1-ADDENDUM-SESSION-2-2026-07-31.md` · Mandate 01 =
`plan/OPERATOR-MANDATE-01-ENGAGEMENT-2026-07-31.md` · Addendum 01–04 = `sessions/GAME-ADDENDUM-01..04`.

---

| # | Delta | Was | Now | Status | Door | Source |
|---|---|---|---|---|---|---|
| D1 | Track B starts immediately | R9, a recommendation | A live parallel track, pre-M0 | ADOPTED — v2.0 §16 "Unratified" | TWO-WAY (derived) | v2.0 §16; §7.1 |
| D2 | M0 scope re-ranked by irrecoverability | M0-a/M0-b as the time-critical pair | §7.2's six-item ranking | ADOPTED — v2.0 §16 "Unratified" | ONE-WAY (derived — governs what is shot at M0) | v2.0 §16; §7.2 |
| D3 | Immersion runway opens at M1 | M4 waits for M3 | Room + 1:1 funnel; consultation surface in Release 1 | ADOPTED — v2.0 §16 "Unratified" | TWO-WAY (derived) | v2.0 §16; §6 |
| D4 | M3 is the monthly cycle + quarterly live gift | Weekly live circle | §4.3, subject to INPUT-16 | ADOPTED — v2.0 §16 "Unratified" | TWO-WAY (derived) | v2.0 §16; §7.6 |
| D5 | Gate: G0 expanded; G7 added | G0–G6 as ratified | §8 | ADOPTED — v2.0 §16 "Unratified"; §8 records the G0 expansion and G7 as "unratified" | TWO-WAY (derived) | v2.0 §16; §8 |
| D6 | Free course and Room free set are one door | Separate free course + funnel | §4.1 | ADOPTED — v2.0 §16 "Unratified" | ONE-WAY (derived — free tier, red line #5) | v2.0 §16; §4.1 |
| D7 | Tier 3 base, tiers 1–2 as on-ramp | Base tier undecided (A17) | §3.2, ratify at INPUT-24 | ADOPTED — v2.0 §16 "Unratified" | TWO-WAY (derived) | v2.0 §16; §3.2 |
| D8 | Ledger v0.2 | v0.1, 18 rows | Superseded by D18 / ledger v0.4 | SUPERSEDED BY D18 | — | v2.0 §16; §14 |
| D9 | M5 exit adds the IP portfolio filings | M5 as ratified | §7.8; R38 now conditional | ADOPTED — v2.0 §16 "Unratified" | TWO-WAY (derived) | v2.0 §16; §7.8 |
| D10 | Floor case annotated: cycle upside recorded-not-counted; 1:1 unmodeled | §6 of DEFINITIVE | §9 | ADOPTED — v2.0 §16 "Unratified" | TWO-WAY (derived) | v2.0 §16; §9 |
| D11 | New label VERIFIED-INTERNAL | Eight labels | Ten labels + FALSIFIED status | ADOPTED — v2.0 §16 "Unratified" | TWO-WAY (derived) | v2.0 §16; §0.1 |
| D12 | §11.6 reframed: assignment risk resolved, authorship risk opened; row 21 split | R42 as a commissioned-software audit | §11.6; rows 21a/21b; G7 amended | ADOPTED — v2.0 §16 "Unratified" | TWO-WAY (derived) | v2.0 §16; §11.6 |
| D13 | Release 1 re-scoped: ladder, no commerce, capture deferred, takedown and privacy in scope | §4.1 as written in v1.0 | §4.1 | ADOPTED — v2.0 §16 "Unratified"; the no-commerce clause is SUPERSEDED BY D37 | TWO-WAY (derived) | v2.0 §16; §4.1; R1 Addendum S2 §4 |
| D14 | M0 pre-shoot list gains escrow/backup and INPUT-27 | §18's action list | §7.2 | ADOPTED — v2.0 §16 "Unratified" | ONE-WAY (derived — M0 pre-shoot list) | v2.0 §16; §7.2 |
| D15 | M3 launches on the web rail only | A4's dual rails implied at M3 | §5.1, §7.6 | ADOPTED — v2.0 §16 "Unratified" | TWO-WAY (derived) | v2.0 §16; §5.1 |
| D16 | Escrow and backup passphrase elevated to a ladder precondition | Infrastructure hygiene | §7.0, risk #16 | ADOPTED — v2.0 §16 "Unratified"; §0.3 carries it as "Assumed not done" | ONE-WAY (derived — key loss is unrecoverable) | v2.0 §16; §7.0 |
| D17 | "Enforced at the data layer" restated as "enforced at the API contract layer, validated on read, no client override" | §3.5 as written in v1.0 | §3.5 | ADOPTED — v2.0 §16 "Unratified"; resolves C19 | TWO-WAY (derived) | v2.0 §16; §3.5 |
| D18 | Ledger v0.3 → v0.4 | v0.2, 26 rows | §14, 33 rows | ADOPTED — v2.0 §16 "Unratified" | TWO-WAY (derived) | v2.0 §16; §14 |
| D19 | Risks #16–#20 added; risk #3 amended | 15 risks | §13 | ADOPTED — v2.0 §16 "Unratified" | TWO-WAY (derived) | v2.0 §16; §13 |
| D20 | FALSIFIED declared as a ledger status | Used in the audit, never defined | §0.1 | ADOPTED — v2.0 §16 "New" | TWO-WAY (derived) | v2.0 §16; §0.1 |
| D21 | M1's cash-in restated: not ≈R$0 | "≈ R$0 beyond existing rails" | §7.4's named lines, three unquoted; §9 annotated for recurring infrastructure | ADOPTED — v2.0 §16 "New"; resolves C18 | TWO-WAY (derived) | v2.0 §16; §7.4 |
| D22 | Release 1 sequenced with a named critical path; M1 gains a second hold condition | A scope list | §7.4 — door-only launch permitted if the Room would breach the R$5k floor | ADOPTED — v2.0 §16 "New" | TWO-WAY (derived) | v2.0 §16; §7.4 |
| D23 | Pre-public checkpoint merged with the audit's Release 1 blockers into one gate | Two separate lists | §7.3, nine items with owners | ADOPTED — v2.0 §16 "New" | TWO-WAY (derived) | v2.0 §16; §7.3 |
| D24 | Free-set shape recommended (R48) | INPUT-27 open with no proposal | §4.1 — one rhythm fully laddered, two paths, three tempos | SUPERSEDED BY D73 — Addendum 04 §5 "supersedes R48's shape" | — | v2.0 §16; Addendum 04 §5 |
| D25 | 2026-07-30 session carry-ins recorded as recommendations, not rulings | Unrecorded | R45, R46, R49; INPUT-49, -50, -51; §0.3 | ADOPTED — v2.0 §16 "New" | TWO-WAY (derived) | v2.0 §16; §0.3 |
| D26 | No microphone anywhere in Release 1 | R33: minimal capture ships in Release 1 | §4.1 — capture and local self-recording move to Release 2 | ADOPTED — v2.0 §16 "New"; kept "fully intact" at Addendum 04 §5 | TWO-WAY — v2.0 §0.2 states D26 and D27 are "both reversible" | v2.0 §16; §4.1; Addendum 04 §5 |
| D27 | Offline download deferred to Release 2 | Offline in Release 1 | §4.1 — Release 1 streams; INPUT-47 leaves the critical path | ADOPTED — v2.0 §16 "New" | TWO-WAY — v2.0 §0.2 states D26 and D27 are "both reversible" | v2.0 §16; §4.1 |
| D28 | The student pulls the ladder lever, never the app | "add parts back as they hold" — agent unstated | §3.2 (R51) — closes an implicit machine-verdict fork | WITHDRAWN by D51 — "D28 and R51 are withdrawn" (RULED, 2026-07-31) | — | v2.0 §16; Mandate 01 §2, §9 |
| D29 | The first Caderno entry is earned by first practice, not by answering the call | §4.1's Primeira Chamada "closing into" the entry | A1 | PROPOSED — "inoperative until ratified" | TWO-WAY (derived) | v2.1 Amendments §3; A1 |
| D30 | Salvador appears behind the master's invitation, branched by language | §4.1's permanent trust surface | A2 | PROPOSED — "inoperative until ratified" | TWO-WAY (derived) | v2.1 Amendments §3; A2 |
| D31 | English subtitling promoted to a Release 1 blocker | §7.2 rank 6, a schedule constraint | A3 | PROPOSED — "inoperative until ratified" | TWO-WAY (derived) | v2.1 Amendments §3; A3 |
| D32 | M0 gains four recording categories, all rank 3 | §7.2's six-item ranking | A4 | PROPOSED — "inoperative until ratified" | ONE-WAY (derived — M0 capture) | v2.1 Amendments §3; A4 |
| D33 | Partition capture extends to narration items | §3.5, playable items in view | A5 | PROPOSED — "inoperative until ratified" | ONE-WAY (derived — consent scope captured at M0) | v2.1 Amendments §3; A5 |
| D34 | A bought course is lessons, rooms and narration | §4.1's "owned rooms" | A6 | PROPOSED — "inoperative until ratified" | ONE-WAY (derived — enlarges what a purchase permanently includes; red line #5's never-take-back logic) | v2.1 Amendments §3; A6 |
| D35 | The cache/library boundary defined; permanent free users enter the operations line | Undrawn; unmodeled | A7, A8 | PROPOSED — "inoperative until ratified" | ONE-WAY (derived — free tier permanence) | v2.1 Amendments §3; A7, A8 |
| D36 | Sequencing inverted — mockup and core functionality before the shoot and before most of the counsel brief | §7.4's build order, external clocks first | §2 | PROPOSED | TWO-WAY (derived) | R1 Addendum S2 §8; §2 |
| D37 | Release 1 ships commerce — Pix live before Release 1, plus in-app purchase | §4.1 "ships with no commerce surface at all"; D13; INPUT-42 as an M2 precondition | §4 | PROPOSED; relied on at Addendum 04 §5 for the cycle's rails | TWO-WAY (derived) | R1 Addendum S2 §8; §4 |
| D38 | The battery is Junior alone, layered; E2's named presence is void and needs a replacement | E2, multiple named musicians lighting up | §5 | PROPOSED | ONE-WAY (derived — determines who is shot at M0) | R1 Addendum S2 §8; §5 |
| D39 | Junior recorded as co-founder; standing rule of cheaper in people, more expensive in Junior | Master under A12, terms at INPUT-3 | §6 | PROPOSED; terms open at INPUT-61 | ONE-WAY (derived — founder standing is expensive to reverse) | R1 Addendum S2 §8; §6 |
| D40 | Tempo steps become a pre-shoot decision, because E1's count-ins are tempo-locked | Tempo as a rendering parameter | §7.4, INPUT-59 | PROPOSED; INPUT-59 provisional, must be confirmed pre-shoot (R82) | ONE-WAY (derived — count-ins are locked to the recorded speed) | R1 Addendum S2 §8; §7.4 |
| D41 | Design runs in parallel in a separate tool from the start | R54, a recommendation | S2 | PROPOSED | TWO-WAY (derived) | R1 Addendum S2 §8; §2 |
| D42 | INPUT-9 and §4.5's store re-verification return from M2 to Release 1 | Deferred to M2 on the grounds that Release 1 sells nothing | §4 | PROPOSED | TWO-WAY (derived) | R1 Addendum S2 §8; §4 |
| D43 | The engagement toolkit is open: streaks, targets, goals, XP, celebration, loss aversion, notifications, unlockables | Prohibited "structurally, not by restraint" | §1 | ADOPTED — Mandate 01 §6 "operative on issue... not proposed"; narrowed at the free tier by D66 | TWO-WAY (derived) | Mandate 01 §6; §1 |
| D44 | Two-ledger separation adopted: play layer and Caderno, structurally apart | Undrawn; the prohibition did the work instead | §4.1 | ADOPTED — operative on issue; "finally load-bearing" at Addendum 04 §3.3 | TWO-WAY (derived) | Mandate 01 §6; §4.1 |
| D45 | E12 revised — notification permission asked at the best-converting moment, not after the first entry | E12 | §2 | ADOPTED — operative on issue | TWO-WAY (derived) | Mandate 01 §6; §2 |
| D46 | E9 revised — a session may close with celebration; quiet is an option, not a rule | E9 | §2 | ADOPTED — operative on issue; E9's quiet count "upgraded" at Addendum 04 §3.3 | TWO-WAY (derived) | Mandate 01 §6; §2 |
| D47 | Risk #22 added — celebration mechanics over sacred-adjacent material at maximum public visibility | Risk #2 as written | §4.3 | ADOPTED — operative on issue | TWO-WAY (derived) | Mandate 01 §6; §4.3 |
| D48 | R54's design brief enlarged to carry two moods: practice stillness and celebration | R54 | §5 | ADOPTED — operative on issue; enlarged a third time at Addendum 01 §10 | TWO-WAY (derived) | Mandate 01 §6; §5 |
| D49 | INPUT-39 enlarged: notifications, engagement telemetry, minors and retention mechanics | INPUT-39 as scoped | §5 | ADOPTED — operative on issue | TWO-WAY (derived) | Mandate 01 §6; §5 |
| D50 | M1 exit evidence instrumented per mechanic, not only in aggregate | v2.0 §7.4 | §5 | ADOPTED — operative on issue; extended at Addendum 04 §9 | TWO-WAY (derived) | Mandate 01 §6; §5 |
| D51 | D28/R51 withdrawn — the app may advance the student; unlocking is available as a reward mechanic | "The student pulls the ladder lever; the app never decides that a part is 'held'" | §9 | ADOPTED — operative on issue; §9 is headed RULED, 2026-07-31 and closes INPUT-63; narrowed by D52 from moving to opening | TWO-WAY (derived) | Mandate 01 §6; §9 |
| D52 | Fork A closed. The app opens rooms; it never moves the student into one. D51 narrows from moving to opening | D51 / Mandate 01 §9 | §3 | PROPOSED — Addendum 01 §12 "Proposed. Operative on founder ratification"; records a ruling made in session; "D52 untouched" at Addendum 04 §3.3 | TWO-WAY (derived) | Addendum 01 §12; §3 |
| D53 | Vocalization replaces Western notation product-wide. No tab, staff, or rhythm grid on any surface | Notation unspecified | §4 | PROPOSED — records a ruling made in session; reinforced by G20 (MASTER-CONFIRMED) and G22 | ONE-WAY (derived — the notation the standard and the reference dialect are built on) | Addendum 01 §12; §4 |
| D54 | Voice before drum. Every room's entry runs voice → voice-over-battery → battery. Revises E4's door sequence | E4 | §5.1 | PROPOSED — records a ruling made in session; E4 revised again by D63 | TWO-WAY (derived) | Addendum 01 §12; §5.1 |
| D55 | Tap-along ships in Release 1 as the door mechanic. The app measures the tap, never the voice | Not in scope | §5.2 | PROPOSED — records a ruling made in session; the tap door is free on-ramp under D73 | ONE-WAY (derived — given to the free tier, red line #5) | Addendum 01 §12; §5.2 |
| D56 | Advanced mode: the screen drum — landscape, two hands, vocalize and strike, zones named by the syllables | Not in scope | §6 | PROPOSED — records a ruling made in session; "advanced" removed by D64; free under D73 | ONE-WAY (derived — free tier, and the zone labels are the reference dialect) | Addendum 01 §12; §6 |
| D57 | Solfejo joins the M0 pre-shoot list, recorded locked to the battery | Not in scope | §9.1 | RATIFIED — "D57 and D58 are decided, not proposed" (G19, FOUNDER-DECIDED, 2026-08-01; C21 closed by D61); "Unchanged, decided" at Addendum 04 §8 | ONE-WAY (derived — M0 capture; eight shoot passes) | Addendum 01 §12; Addendum 03 §6.3; Addendum 04 §8 |
| D58 | The stroke sample library joins the M0 pre-shoot list as a new irrecoverable item | Not in scope | §9.2 | RATIFIED — "decided, not proposed" (G19/D61); justification restated by D77, C22 resolved | ONE-WAY (derived — M0 capture; named irrecoverable in the delta itself) | Addendum 01 §12; Addendum 03 §6.3, §8; Addendum 04 §3.3, §8 |
| D59 | Timing feedback is binary. A generous window; no tiers, labels, or accuracy readout on any surface. Per-device calibration leaves Release 1 | Grading tightness open; Addendum 01 §10 flagged it as the cost-deciding decision | §1, §3, §4 | PROPOSED — Addendum 02 §10 "Proposed. Operative on founder ratification"; records G9 (FOUNDER-DECIDED); G9's scope amended by D79 — per-strike stays binary, post-round sustain becomes visible | TWO-WAY (derived) | Addendum 02 §10; §3; Addendum 04 §3.3 |
| D60 | The screen drum is scheduled, not triggered. The app plays the correct part in time; the strike keeps it alive. The native low-latency engine leaves Release 1's critical path | Triggered sample playback assumed by Addendum 01 §6.4 | §1, §4 | PROPOSED — records G10 (FOUNDER-DECIDED); "G10 unchanged" at Addendum 04 §3.3 | TWO-WAY (derived) | Addendum 02 §10; §4 |
| D61 | C21 closed. D57 and D58 are decided, not proposed | Two documents in disagreement | §6.3 | PROPOSED — Addendum 03 §13 "Proposed. Operative on founder ratification"; records G19 (FOUNDER-DECIDED) | — | Addendum 03 §13; §6.3 |
| D62 | No app-fired dropout in Release 1. Support is removed only where the music calls for it. R76's takes 3 and 4 leave the list | Fork J open, three positions offered | §3 | PROPOSED — records G12 (FOUNDER-DECIDED); Fork J DEFERRED, criterion recorded | TWO-WAY (derived) | Addendum 03 §13; §3 |
| D63 | The first session runs the whole sequence at its simplest setting. Fork B closed. Revises E4's door sequence again and adds E20 | Fork B open, three options | §4 | PROPOSED — records G13 (FOUNDER-DECIDED) | ONE-WAY (derived — the first session is the free door; red line #5) | Addendum 03 §13; §4 |
| D64 | R70 revised. The screen drum ships inside the first session, not behind the door. The order survives; the distance does not | R70 | §4 | PROPOSED | ONE-WAY (derived — puts the screen drum inside the free first session) | Addendum 03 §13; §4 |
| D65 | The stroke set is fixed: three zones on hand instruments (slap, tone, bass), two on stick instruments (rim, skin). Labels remain the syllables under D56 | Zone count unspecified | §9 | PROPOSED — records G14 (FOUNDER-DECIDED) | ONE-WAY (derived — sets the sampled stroke set at M0 and the syllable labels) | Addendum 03 §13; §9 |
| D66 | No engagement mechanics on the free tier in Release 1. Mandate 01's INPUT-66 recommendation is withdrawn | INPUT-66 recommended yes | §10 | PROPOSED — records G15 (FOUNDER-DECIDED); read at Addendum 04 §2 item 2 as barring the extrinsic toolkit only, flagged for confirmation at INPUT-84 | TWO-WAY — G15 is "Decision deferred; nothing given for now"; withholding preserves the one-way door | Addendum 03 §13; §10; Addendum 04 §2 |
| D67 | The count-in fires at every session start. R72's variant bank is promoted from mitigation to requirement | R60(b): count-in as the celebration object on advance | §7 | PROPOSED — records G16 (FOUNDER-DECIDED); "G16 untouched" at Addendum 04 §3.3; the vacated celebration slot is filled by D80 | ONE-WAY (derived — the variant bank is shot at M0; count INPUT-74) | Addendum 03 §13; §7 |
| D68 | No comparison between students in Release 1. INPUT-64 answered for Release 1 | INPUT-64 open | §6.1 | PROPOSED — records G17 (FOUNDER-DECIDED), "not yet, maybe never"; G17 stands at Addendum 04 §3.4 | TWO-WAY (derived — withholding; open beyond Release 1) | Addendum 03 §13; §6.1 |
| D69 | No share or export in Release 1. R69's default adopted | INPUT-71 blocking the feature | §6.2 | PROPOSED — records G18 (FOUNDER-DECIDED); INPUT-71 stays in the counsel brief per R78 | TWO-WAY (derived — withholding) | Addendum 03 §13; §6.2 |
| D70 | R76's rough recording reduces from six takes to four — reference alone, one part over reference, break/turnaround, solfejo | Six takes | §3, §5 | PROPOSED; the break/turnaround take's question (INPUT-58) was subsequently answered by G24 rather than by the recording | TWO-WAY (derived — prototype recording, not M0) | Addendum 03 §13; §3, §5 |
| D71 | MASTER-CONFIRMED label added; first reclassification pass | Ten labels | §1.1 | ADOPTED — Addendum 04 §10, plan-of-record under the founder's make-the-plan instruction; §1.1 words it "D71 (proposed)" | TWO-WAY (derived) | Addendum 04 §10; §1.1 |
| D72 | Fork C closed for Release 1; break passes leave M0 | "The game's existence condition" | §1, §8 | ADOPTED — records G24 (MASTER-CONFIRMED); INPUT-58 answered | ONE-WAY (derived — removes ~12 passes from the M0 day; §2 item 4 notes it is "reversible until the shoot") | Addendum 04 §10; §1, §8 |
| D73 | The commons is free; scarcity is priced. Free set = commons rhythms performed by Junior | R48 depth-only shape | §5 | ADOPTED — plan-of-record; supersedes R48's shape and gives INPUT-27 its rule; list at INPUT-80 | ONE-WAY — §5 states the free commons is "permanent under red line #5" | Addendum 04 §10; §5 |
| D74 | The echo loop is the in-room event, rendered from locked solfejo | No in-room event | §4.1 | ADOPTED — plan-of-record; form assent INPUT-79, specification INPUT-78 | TWO-WAY (derived) | Addendum 04 §10; §4.1 |
| D75 | The repertoire arc: the map is the city of rhythms | Map = one rhythm's grid | §4.2 | ADOPTED — plan-of-record | TWO-WAY (derived) | Addendum 04 §10; §4.2 |
| D76 | The grading constitution: facts drive sound, never sentences; sustain visible, precision audible, judgment human | Patchwork of per-surface rules | §3.2 | ADOPTED — plan-of-record; carried into the two-page Charter under D83 item 1 | ONE-WAY (derived — enters the Charter as constitutional material) | Addendum 04 §10; §3.2, §7 |
| D77 | The drum always sounds: scheduled render in-window, real one-shots out-of-window and wrong-zone. C22 resolved; D58 re-justified | Out-of-window unspecified | §3.3 | ADOPTED — plan-of-record | ONE-WAY (derived — depends on the stroke sample library shot at M0) | Addendum 04 §10; §3.3 |
| D78 | The part fades when unfed and returns when fed; no fail state exists anywhere | "Keeps it alive" unspecified | §3.3 | ADOPTED — plan-of-record; the specified reading of G10 | TWO-WAY (derived) | Addendum 04 §10; §3.3 |
| D79 | Post-round sustain facts and per-setting personal bests are visible. Amends G9's scope: per-strike stays binary, silent and audible-only; accuracy readouts stay barred | G9: no readout on any surface | §3.3 | RATIFIED 2026-08-03 (RULED) — put to the founder separately | TWO-WAY — Fork L states "visibility is a two-way door; the underlying facts are collected either way" | Addendum 04 §10; §3.3, §3.6, §15 |
| D80 | The celebration object is the new personal best, non-vocal sound design and light; voice variants reserved for firsts and returns. INPUT-73 answered | Slot empty since G16 | §3.3 | ADOPTED — plan-of-record; closes Fork D | ONE-WAY (derived — the reserved voice variants are shot at M0) | Addendum 04 §10; §3.3, §15 |
| D81 | The cycle enters Release 1 as a monthly live event, ops not build; membership sellable day one. Fork K answered, contingent on INPUT-82 | Cycle at Release 2 | §5 | ADOPTED — plan-of-record; contingent on INPUT-82's go/no-go; strains the one-obligation rule (risk #29) | ONE-WAY (derived — a membership sold day one is a standing promise) | Addendum 04 §10; §5 |
| D82 | The standard-publication workstream opens; the frame is published, the corpus is not; Junior's set is the reference dialect | Non-publication discipline | §6 | ADOPTED — plan-of-record; scope, licence and timing at INPUT-83; risk #28 recorded | ONE-WAY — D83 item 2 names publication and the fixed reference dialect as one-way doors | Addendum 04 §10; §6, §7 |
| D83 | Estate restructure: charter/backlog split, door labels, monthly decision hour | Session-document register | §7 | ADOPTED — plan-of-record; this register is issued under it | TWO-WAY (derived) | Addendum 04 §10; §7 |

---

## Status conflicts on the record

- **C21 — D57 and D58, decided or proposed.** `GAME-CONVERSATION-CONTINUATION-PROMPT-FORK-B-ONWARD`
  §3 listed them under "decided and not up for renegotiation"; Addendum 01 §12 listed them as
  proposed and operative only on ratification. Raised as C21 at Addendum 02 §11 and **closed** by
  G19/D61 (Addendum 03 §6.3): decided. `...FORK-J-ONWARD` §3, §8 still carries C21 as open, and is
  the earlier state.
- **D52–D56, the same disagreement, never formally closed.** The FORK-B continuation §3 lists them
  in the same "decided and not up for renegotiation" block, while Addendum 01 §12 and `README.md`
  call them proposed. G19/D61 reached only D57 and D58. Recorded here as PROPOSED, per the issuing
  document.
- **Addendum 04's own status wording.** The front matter says deltas "are proposed and become fully
  operative on founder ratification... the remaining deltas stay proposed", and §1.1 says
  "D71 (proposed)"; §10's preamble and the inline labels at §3–§7 say ADOPTED. Both hold at once —
  operative as plan-of-record, awaiting the ratification block at §9 — and ADOPTED is used here.
- **C22 — D58's justification.** D58 was justified by Addendum 01 §6.4's triggered playback, which
  D60 replaced. The item was kept (R80) and **re-justified by D77**; C22 is resolved.
- **G15 / D66 read against Addendum 04's grading layer.** Addendum 04 §2 item 2 takes G15 to bar the
  extrinsic toolkit only, not the game's own legibility — flagged by the file itself as "Medium —
  interprets a founder ruling" and put to the founder at INPUT-84. Unconfirmed as of 2026-08-03.

---

*Issued 2026-08-03 under D83 (Addendum 04 §7). Numbering state: last used D83, next D84
(Addendum 04 §16). Nothing in this register is measured evidence; no delta here touches a red line.*
