# Opanijé — Pricing/Access · The Standard · The M0 Shoot (compacted, 2026-08-03)

Opanijé = mobile app teaching Afro-Brazilian (Bahian) percussion. Master = **Junior** (co-founder, S7/D39); second master **Vanderson**. Founder holds price authority. Registers of record dated 2026-08-03 under D83. All money figures are ASSUMPTION at R$5.50/USD unless stated.

---

## 1 · Pricing and access

**Charter law:** access is bought; standing is only earned. Courses/memberships/classes/seasons sell. Book entries, stage passage, master's acknowledgment — never purchasable. Red line #5: whatever the free tier is given is **permanent, never withdrawn** (ratchet ⇒ every free-side choice is ONE-WAY). Red line #2 / R4: a *Confirmed* entry carries **no link to any payment record**, enforced at the API contract layer. R53: no recording of a master may name a price or product, nor appear inside a promo/upsell moment.

**D73 (ADOPTED) — the commons is free; scarcity is priced.** Supersedes R48's depth-only shape.

| Side | Item |
|---|---|
| FREE | Commons rhythms (readily available online — Ijexá the named example) **performed by Junior** (G25 × E17 compose) |
| FREE | Full on-ramp instrument: **voice, tap, screen drum, the echo loop** — this is the standard's distribution vehicle (G22), not leakage |
| FREE | Free course + Room free set = **one door** (D6), Primeira Chamada, first Caderno entry |
| FREE | The room a free student already has, forever, unchanged (E13) |
| PAID | **Depth** on free material (more parts, more speeds, full ladder) |
| PAID | **Rarer authorised rhythms** (any Bahian toque Junior is authorised to teach — Candomblé and popular, G23) |
| PAID | **This specific battery's rooms** — every drum is Junior, layered (S6/D38); uncopyable |
| PAID | **The human layer** — the master's ear, monthly, by name |
| NEITHER | Standing: entry, passage, honour, acknowledgment. Allocated by Junior alone (A5) |

Free-set size: R48 costed ≈2×4×3 = **24 renders ≈60–70 MB**; D73/R88's set has **no restated render/storage/bandwidth figure** — open gap bearing on INPUT-48.

**Seven revenue lines, never cross-wired (red line #6).**

| Line | Reference price | Notes |
|---|---|---|
| Course | **R$297** one-time | Room plays what you own. Converts M2 |
| Cycle membership ("the Roda") | **R$59/mo** | Sells presence/cadence/being-heard; sells no content (R3). Price actually at INPUT-82 |
| Private 1:1 | INPUT-11, both price worlds | A8 RULED; **IAP-exempt**; highest-margin digital line; immersion feeder |
| Cultural immersion | **USD $2,500–4,000**, adult-only | Consultation-closed, no in-app checkout. Margin ≈R$8–9k/student |
| Institutional licensing (Memória Viva) | **US$500–2,000/institution/yr** + per-project | 6–18 month fuse |
| B2B bookings | Quoted | Existing desk (INPUT-6) |
| Goods | Store per line | Funnel-fed |

**Rails.** Live: PayPal in `/shop` (USD), manual bank transfer (payee is an individual, not the CNPJ seller — INPUT-42/O4). Installed-inactive: Stripe, Mercado Pago. **Pix/BRL: does not exist** — ledger row 29 FALSIFIED 2026-07-30; S3 makes it live before Release 1 (O3). **Store billing (Apple/Google): does not exist** — purchase adapter implements only `external-browser` handoff; S4 makes Release 1 sell in-app, additive to the web rail (D37), website stays priority funnel (S5). Store accounts under company CNPJ not opened (S8/O1/INPUT-40; Apple org route needs a **D-U-N-S number**, long lead). Small-business fee programmes not applied for (O2). **No subscription capability at all** (no renewals/dunning/cancellation) — from-zero build. Entitlement rail `GET /wp-json/opanije-mobile/v1/entitlements` is deployed, returns **HTTP 503 `service_disabled`**, capped at 2 purchasable courses / 1 purchase shape; being rewritten at zero rows for free-permanent-set + owned courses + no ceiling. **R13: the app never reads a store receipt** — receipt → server → server validates and writes entitlement → app asks the server, always the same question.

**Commission arithmetic per R$297 course:** Web+Pix ~1% fee → **≈R$205** (≈49 sales to recover R$10k); web PayPal-shaped ~8% → ≈R$184 (≈55); in-app small-business 15% → ≈R$163 (≈61); in-app standard 30% → ≈R$119 (≈84). Gap between in-app rates = **R$44/sale**. R56: state the rail mix in the monthly cash model.

**Store-tax asymmetry (Apple 3.1.3(d), VERIFIED-EXTERNAL 2026-07-29, expiring):** 1:1 person-to-person realtime = **exempt** (tutoring the named example); one-to-few/one-to-many realtime must use IAP. Cycle subscription 15–30%; paid course 15–30%; **live group session 15–30%, explicitly not exempt**; immersion none (real-world service). Illustrative R$400 class @70% master share: ≈R$120 via Pix vs ≈R$60 via IAP. **Unresolved:** whether D81's one-to-many monthly membership classifies as subscription or live group session — 15–30 points of every in-app membership sale.

**Other contribution figures.** Cycle ≈R$42/member/month (8% fees, ~20% confirmation-fee pool). Individually-confirmed track capped ≈**100–200 concurrent students** by the master's listening hours. Cycle modelled 150 members ≈R$77k/yr; upside 300 ≈R$151k, 500 ≈R$252k (recorded, never counted). **Ring-fence R6+R25:** Junior sets a three-way monthly hours budget (INPUT-12) — confirmation hours (never sellable/surfaced as inventory), cycle-listening hours, private-class hours; private-class availability is a hard constraint on the booking calendar. Master economics = revenue share + per-confirmation fee + cycle-listening compensation + 1:1 share + booking fees + structural credit (actual terms INPUT-3; instrument reopened by INPUT-61).

**Cash discipline.** Reserve floor **R$5,000** (automatic hold below). Free treasury ≈**R$10–12k**. M0 earmark **R$8–10k** (study points: R$5–15k per master's Room, R$1.5–3k per archive episode). No pre-counting of grants/pilots/B2B/1:1. Founder labour priced at replacement cost, never zero; CAC unmeasured. Floor case (mature year): immersions +R$264k, courses +R$156k, cycle +R$77k, archive/institutional/B2B +R$85k, operations −R$60k ⇒ **≈+R$520k (~USD 95k)** — a target, not fact; −R$60k excludes founder draw (P3, INPUT-4a) and does not yet carry storage/CDN/recurring infra.

**Milestones.** M2 ≥20 sales/30d, ≥55/90d (**<20 at day 90 ⇒ hold the ladder**); precondition — delete ~2,600 lines of orphaned course code before real buyers touch the purchase path. M3 ≥50 members by month 3, retention ≥70% (**<50% ⇒ recurring model is wrong**), ≈R$2.1k/mo. M4 ≥6 students ≈R$48–54k; <4 ⇒ postpone; never breach the R$5k floor even at full cancellation. M5 cumulative ≥R$120k within 12 months of M1 + one paid institutional pilot. Gates G1 ≥R$120k (stretch R$180k); G2 retention ≥70% + churn curve; G3 one season ≥60% capacity. Track B: ten hand-booked 1:1 sessions (Junior + Vanderson), cash in ≈R$0.

**Funnel (A6 — the Roda does NOT feed the immersion).** Domestic: list → free door → paid course → cycle. International: free tier subtitled (INPUT-14) → the named battery → **paid 1:1 with that named master** (IAP-exempt) → consultation → season. Institutional: outreach from M3 via existing console.

### The monthly master-listening cycle (D81, answers Fork K) — operationally

Release-1 form, **operations not build**:

| Element | Where |
|---|---|
| **Monthly live event**, streamed + in Salvador when possible; Junior responds **by name** | Outside the app |
| **Submission** of student recordings | **Outside the app, over ordinary channels** — this is what keeps **D26 (no microphone in Release 1) intact** |
| Appointment (a date you hold with a human), calendar, replay, Caderno entry (recorded as event, never attainment — R18) | In-app **thin surfaces only** |
| The sale | Membership **from day one**, on Pix (S3) + store billing (D37) |
| The invitation | Shot at M0, **price-free and product-free** (R53) |

The prior (v2.0/M3) cycle was **asynchronous**: the call → two-week practice window → the response, with a **quarterly live roda framed as a gift** so missing it churns nobody. How D81's monthly live form relates to it (replaces / precedes / becomes) is **unstated** — routed to INPUT-82 "format". Risk #29: a monthly live event breaks the founder's one-obligation-at-a-time rule; format may start as small as one hour. D81 spends against INPUT-12's cycle-listening budget before that budget exists, and puts a recurring membership on store billing at Release 1 against D15 (web rail only at M3). The Release-1 membership has **no contribution figure and no price** — both wait on INPUT-82; the R$77k floor-case line is not costed for a monthly live commitment.

**M1 measures** a product **with** the core game (echo loop D74, repertoire arc D75, honest drum D77, fade-and-rejoin D78, post-round facts + personal best D79 RATIFIED/RULED) **and** the appointment, but **without** the extrinsic toolkit (streaks, XP, goal-setting, celebration-as-schedule — barred at the free door by G15/D66). R81: label that baseline, dated, before the numbers exist. Headline numbers: first-session completion, day-7 return.

---

## 2 · The Standard (publication workstream, D82 under G22)

**What it is as an artefact.** A **notation standard for teaching Afro-Brazilian percussion**, published openly as a text/spec document; Opanijé repositions as a music-education company. Publication is a **strategic** act replacing the prior defensive posture. **The frame is published; the corpus is never.**

**What it notates.** The **solfejo (vocalization/syllable) system**: spoken/sung syllables that encode **both rhythm and stroke simultaneously** (G3/ledger row 40 — FOUNDER-FACT, true of most masters). Under **G2/D53 vocalization replaces Western notation product-wide** — no tab, no staff, no rhythm grid, no piano-roll on any surface. In this product **notation, teaching and input are one object**: the same syllable system displays the music, teaches it, and is what the student produces.

**Concrete spec content the estate actually fixes:**
- **Stroke vocabulary, per instrument class (G14/D65):** hand instruments = **three zones — slap, tone, bass**; stick instruments = **two zones — rim, skin**. Which instrument takes which vocabulary is INPUT-77; the reference instrument may need its own.
- **Reference dialect:** Junior's syllable set is fixed as the reference for the material he teaches — fixed by **what is recorded at M0**, not by a written table. Publication *describes what was shot*.
- **Frame's second half:** the frame lets other masters/traditions carry **their own dialects** under the same structure (how red line #1 scales to future benches — no master's syllables imposed on another's tradition).
- **A standard for speech does not abolish accents** — one form is named as reference; others stay legible.

**No symbol table, grammar, file format, or machine encoding exists anywhere in the estate.** The syllable inventory itself is defined only by Junior's recorded performance. Where the publishable *structure* ends and the never-publishable *pedagogical sequence* begins is **undrawn** — INPUT-83's first job.

| Object | Published? |
|---|---|
| Syllable system's **structure / frame** | **YES — this is the publication** |
| Recordings, **stems** + stem architecture, **renders**, catalog, Junior's partition, pedagogical sequence | **NEVER** — the priced scarcity |
| The base game mechanic (R39) | Yes, separately — defensive prior art, timed **after** the GUI design filing |

**Publishing forfeits nothing:** LPI art. 10 categorically excludes game rules (VII), programs as such (V), educational methods (III), presentation of information (VI) — the frame was never patentable. Protectable instead: code, artwork, audio, text under direito autoral (Lei 9.610/98), arising on creation; Biblioteca Nacional deposit declaratory (R38). The published standard is itself a text asset.

**Conditions and gaps.** FF1 — a named better-connected incumbent (owns Timbalada, intimate with candomblé percussionists) could reproduce a provenance register at will — flips sign: an incumbent **adopting** a standard Opanijé publishes *and stewards* strengthens the position, **provided stewardship is designed**. It is not: no steward, instrument, governance, or dialect-admission process exists anywhere, and no ledger row instruments adoption (risk #28: the standard outruns the corpus). **The standard must never be a credential** — no certification, grades, levels, or assertion about a person (A14 + red line #2). Trademark: "Opanijé" is the *toque* of Obaluaiê/Omolu (FF4); LPI art. 124, III bars signs offending religious worship; INPI *Manual de Marcas* §5.08 tests the sign **and** the connotation from the goods designated. RULED sequence **INPUT-32 (Junior's ruling) → INPUT-31 (clearance) → any filing or further public use** — publishing under the name *is* further public use; R43's house/product-mark split held ready. Positioning conflict unresolved: P1 "platform for verified oral-tradition transmission, not pure EdTech" (RULED) vs G22 "music-education company" (later governs).

**Sequencing.** Nothing publishes before INPUT-83 returns. **The GUI industrial-design filing (R37) must precede any screen going public** — novelty dies on disclosure; grace-period terms at INPUT-35; INPUT-51 decides lock-and-file (R49) vs private beta. A mockup shown to Junior is not public; one in a pitch, store listing, press item or adopter's hands is.

---

## 3 · The M0 shoot

The production sprint — one day, cameras on Junior, ≈R$8–10k. **The estate's only hard deadline, and it is irrecoverability not calendar:** you cannot extract isolated strokes from a performance, cannot lock standalone solfejo to a battery afterwards, cannot re-consent a master from a weak position. Everything shot at M0 is ONE-WAY. Two standing rules: no recording ships without an executed consent instrument (red line #6); no recording names a price or product (R53).

**Capture inventory:**

| Item | Detail |
|---|---|
| Consent instruments | Executed **before cameras roll**, in the teller's own voice, **interactive and game use inside licensed scope** (INPUT-22). Rank 1 |
| **Isolated stems, per instrument** | One isolated stem per instrument across the battery. **The subtraction ladder is rendered from them and cannot exist without them.** Vanderson's stems shot regardless of whether his material ships. Rank 3 (INPUT-23, INPUT-55) |
| **Twelve drum passes** | 4 parts × 3 speeds, **Junior plays every drum himself, layered** (S6/D38) ≈12 passes per rhythm before any count-in |
| **Eight solfejo passes** | Every part × slow + normal (8 of 12 possible; top speed dropped — nobody on the on-ramp is there). Recorded **with the battery in his headphones, locked to the grid, never standalone** (R63/D57): standalone is derivable from locked; locked is never derivable from standalone |
| **Stroke sample library** (D58) | Every instrument in the free rhythm's battery; every stroke the solfejo names — **3 strokes on hand instruments (slap/tone/bass), 2 on stick (rim/skin)**; **several velocity layers per stroke, several takes each; isolated one-shots, clean, no room bleed**. ≈20–40 min, mechanical, no take direction. Not derivable from stems. Justified by D77 — the drum always sounds, so out-of-window and wrong-zone strikes fire real one-shots (INPUT-70, INPUT-76) |
| **Count-in / spoken-moment bank** | **10–12 variants**, including ≥2 non-interchangeable — one longer, one reading as **return after absence** (the only asset behind R66's musical streak repair). Synthetic substitutes barred by red line #4, so wear-out is unrecoverable (INPUT-74) |
| Entrance calls + count-ins | Per rhythm, per incoming part: cycle finishes, master calls the next player in and counts, battery resumes bigger (E1). **Tempo-locked to the speed recorded** |
| **The welcome** | One, durable, seconds not minutes, price-free/product-free. Most-viewed asset in the estate |
| **The next-step invitation** | Two versions — domestic (the caixa, or Vanderson's toque) and Salvador; both price-free/product-free; now also carries the cycle (needs INPUT-82 first) |
| **Narrated video, per catalog item** | Master tells what the toque is, where it sits, what it is for (E14). Most subtitle-dense content that exists |
| **Five-value partition, item by item** | playable-inside · gamifiable (recognition/vocalization only) · teachable-but-not-gamifiable · archive-only · **unrecordable** — captured on every item, playable and narrated alike, vocalization tier live (INPUT-21; INPUT-52 for the free rhythm separately) |
| **Commons rhythms at on-ramp depth (R88, NEW)** | **2–3 rhythms × 1–2 parts × slow + normal ⇒ ≈4–12 passes.** Candidates: Ijexá, afoxé, samba de roda, samba-reggae and siblings. Funded by the ~12 break passes freed by G24/D72. ONE-WAY twice (shot at M0 + given to free tier) |
| Photography | **One person, in the room he plays in.** Portrait stills of a full battery removed (S6/D38). Play-screen imagery unresolved (INPUT-60) |
| The standing room | Fixed camera mount, proper mic + interface, wired ethernet, 4G backup, docked tablet, one-tap join. TWO-WAY but load-bearing for the monthly live event and the 1:1 line (INPUT-15) |
| English subtitling | Post-production on narration + welcome + invitation; language follows the phone with manual override (E11). TWO-WAY, but a Release 1 blocker (D31) |
| **Echo-loop states** | **Zero new capture** — voice together → voice withdraws → student alone with battery continuing → voice returns. Entirely **render-time muting of solfejo already recorded locked to the battery** (D74) |
| Answers gathered in the room | INPUT-16, INPUT-20 |

**Removed:** ~12 break/turnaround passes (G24/D72 — Fork C deferred to "later", ledger row 47); dropout variants (G12/D62 — no app-fired dropout in Release 1; support is removed only where the music itself calls for it); full-battery portrait stills (S6/D38).

**Shoot-day gaps:** the specific **three-step tempo ladder is unconfirmed** (R82/INPUT-59) though "slowing a toque is normal" is confirmed in general — 12 drum passes, 8 solfejo passes and every count-in lock to whatever speeds are chosen. E2 (named-presence lamp) declared **void** by D38 yet Addendum 04 builds E21 on it as live — decides whether anything but one man is photographed.

---

## 4 · Numbered-ID index

**Decisions (D).** D1 Track B starts immediately · D3 immersion runway opens at M1 · D4 async cycle shape · D6 free course + Room free set are one door · D10 upside recorded never counted · D13 (no-commerce clause superseded by D37) · D15 M3 on web rail only — conflicts with D81/D37 · D16 infrastructure ruling · D26 **no microphone in Release 1** · D31 subtitling a Release-1 blocker · D32/D33 narrated video + partition widening · D36 mockup before shoot · D37 Release 1 sells in-app, store billing on top of web rail · D38 battery is Junior layered; E2 void · D39 Junior recorded as co-founder · D42 returns INPUT-9 + store-tax re-verification to Release 1 · D53 vocalization replaces Western notation · D57 eight solfejo passes locked to battery · D58 stroke sample library · D60 scheduled playback · D61 D57/D58 decided (closes C21) · D62 no dropout variants · D65 3-zone hand / 2-zone stick stroke vocabulary · D66 no engagement mechanics at the free door · D67 count-in fires every session start ⇒ variant bank required · D69 no social video (Fork F closed) · D71 pedagogical tempo half MASTER-CONFIRMED subject to R82 · D72 break passes leave the day · D73 **commons free, scarcity priced** · D74 echo loop · D75 repertoire arc · D76 grading constitution · D77 the drum always sounds · D78 fade-and-rejoin · D79 post-round facts + personal best (RATIFIED, RULED) · D81 **cycle enters Release 1 as operations** · D82 **standard-publication workstream opens** · D83 register discipline + the one-way door list.

**Recommendations (R).** R3 cycle sells no content · R4 Confirmed carries no payment link · R6/R25 the ring-fence · R7/R32 international funnel · R13 server-validated entitlements · R16/R31 stems untouched · R18 Caderno records events not attainment · R29 entitlement rail rewrite · R30 free permanent set fixed pre-public · R34 name clearance · R35 Junior's ruling first · R37 GUI industrial-design filing · R38 Biblioteca Nacional deposit · R39 defensive publication of base mechanic · R40 conjunto-imagem discipline · R43 house-mark/product-mark separation · R48 old free-set shape (superseded by D73) · R49 lock-and-file · R53 **no price/product in any master recording** · R56 state the rail mix · R63 solfejo never standalone · R64 vocalization tier has a product behind it · R66 musical streak repair · R72→R79 count-in bank sizing (10–12) · R76 rough prototype recording before mockup · R78 one combined counsel brief · R80 kept library in scope · R81 label M1's baseline before the numbers exist · R82 confirm the tempo ladder first-hand · R86 vocabulary sheet · R88 **commons rhythms at on-ramp depth**.

**Founder rulings / gates (G).** G1 ≥R$120k cumulative · G2 cycle retention ≥70% · G3 immersion ≥60% capacity · G4 first institutional evidence · G12 no dropout variants · G14 the stroke set wanted · G15 no extrinsic toolkit at the free door · G16 count-in opens every day · G18 no social video · G19 D57/D58 decided · G22 **publish the notation openly as a standard; position as music-education company** · G23 Junior records any Bahian rhythm he is authorised to teach · G24 break passes removed · G25 rhythms readily available online are free · G26 the screen drum may resemble a real drum from above.

**Experience (E).** E1 level change as a musical event in the master's voice · E2 named presence (VOID, unreplaced) · E7/E10 the ending's invitation · E11 subtitles follow phone language, manual override · E13 the free student's room, forever unchanged · E14 narrated video per catalog item · E15 no 1:1 in Release 1 (its stated forcing reason is void) · E17 the free rhythm is **Junior's** · E21 presence lamp (built on void E2).

**Sessions (S).** S1 deferral (reversed for S8) · S3 Pix live before Release 1 · S4 Release 1 sells inside the app · S5 website stays the priority funnel · S6 Junior plays every drum, layered · S7 Junior a co-founder · S8 store accounts under the CNPJ immediately.

**INPUTs.** 2 M0 scope + quotes · 3 master terms as agreed · 4/4a fixed costs / founder draw · 5 immersion window+capacity · 6 B2B pipeline · 7 grant calendar · 8 treasury figure · 9 anti-steering per jurisdiction · 10 price parity across rails · 11 1:1 prices both worlds · 12 three-way monthly hours budget · 14 English subtitling in scope? · 15 standing room in scope? · 16 does the async cycle work as a roda? · 20 assent to Reading A (rhythm-as-musical-object outside red line #1) · 21 five-value partition item by item · 22 do consents license interactive/game use? · 23 isolated stems in scope? (plan requires yes) · 27 free tier's permanent set (ANSWERED in principle by D73) · 31 INPI search + counsel opinion · 32 is marking the name acceptable to Junior? · 33 Marco Legal dos Games applicability · 35 design-filing grace period · 40 Apple/Google accounts under CNPJ (D-U-N-S) · 41 fixed subtraction ladder vs live part-by-part muting · 42 payment architecture · 44 escrow/backup/second machine · 48 storage, bandwidth, CDN plan (**M1 cannot be costed until it returns**) · 51 lock-and-file vs private beta · 52 the free rhythm's own partition value · 53 which toque is the free rhythm · 55 does Vanderson appear in Release 1? · 57 will Junior play every part layered, ~12 passes? · 58 break passes (answered by G24) · 59 tempo steps · 60 what goes on the play screen now E2 is void · 61 Junior's co-founder terms vs INPUT-3's instrument · 62 assent to engagement layer past the door · 67 **fix Junior's syllable set as reference dialect** (reframed, confirmation still owed) · 68 what the hand does while the mouth does the part · 69 assent to the screen drum · 70 which drums/strokes may be isolated-sampled under the partition · 71 may people post video of themselves playing? · 72 who may hear the rough prototype audio · 74 how many count-in variants, of what kinds · 76 does the library stay in the shoot? (answered in substance by D77, never formally closed) · 77 which instruments take 3-zone vs 2-zone vocabulary · 78 classroom transcription (the echo loop's real specification) · 79 assent to the rendered echo · 80 **the commons list** (founder names, Junior confirms availability + teaching order) · 81 vocabulary sheet approval · 82 **the cycle: go/no-go, format, submission channel, price** (founder AND Junior; blocks the mockup's ending and the M0 invitation) · 83 **publication scope, licence, timing vs the design filing and R39, positioning's trademark effect + stewardship design** (founder + counsel) · 84 does G15 bar only the extrinsic toolkit, not the game's own legibility?

---

## 5 · Constraints binding anything built from these assets

1. **No microphone / no capture in Release 1 (D26).** No pitch or timing analysis of the student's voice or hands. Submissions leave through channels outside the app. Any "did you hold it" judgement must come from touch input on the screen drum, not from audio.
2. **No Western notation on any surface (G2/D53)** — no tab, staff, grid, or piano-roll. The only notation is spoken/sung syllables.
3. **Solfejo audio exists only locked to the battery.** Solo-voice playback must be derived by muting; the reverse is impossible. The echo loop is render-time muting, nothing more.
4. **The subtraction ladder can only be rendered from isolated per-instrument stems** — if stems are missed at M0 there is no ladder.
5. **Stroke interaction is bounded by the sampled set**: 3 zones on hand drums, 2 on stick drums, several velocity layers, one-shots only. Every strike must sound — including out-of-window and wrong-zone (D77).
6. **Tempo is fixed at capture**: three speeds, but only slow + normal have solfejo; entrance calls and count-ins are locked to their recorded speed. No arbitrary tempo slider.
7. **Free tier is permanent and irrevocable** (red line #5) — anything shipped free can never be paywalled later.
8. **No engagement toolkit at the free door** (G15/D66): no streaks, XP, goal-setting, or scheduled celebration; the core game (echo loop, repertoire arc, honest drum, fade-and-rejoin, post-round facts, personal best) is allowed.
9. **No standing, grades, levels, certification or ranking anywhere** — the Caderno records events, never attainment; Confirmed is human-allocated and carries no payment link.
10. **No price or product name inside any master recording**; no master's voice in a promo or upsell moment.
11. **Entitlements are server-authoritative**; the app never reads a store receipt.
12. **No social/UGC video** (Fork F closed).
13. **Screens must not go public before the GUI design filing** — mockups may be shown to Junior only.
14. **Content ceiling:** 2–3 commons rhythms × 1–2 parts × 2 speeds free; one deep rhythm at 4 parts × 3 speeds; every drum is one man layered; one photographed person, one room. Design must not assume an ensemble, a large catalog, or breaks/turnarounds (deferred).
15. **A monthly appointment is a thin in-app surface only** — date, calendar, replay, Caderno entry. No submission UI, no age gate, no capture stack.
