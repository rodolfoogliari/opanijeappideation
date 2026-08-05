# Opanijé — Plan of Record (compacted from Consolidated v2.0, 2026-07-30)

Mobile app for learning Afro-Brazilian percussion. Bootstrap, pre-revenue. Nothing MEASURED yet.

## Position, people, money

- Platform for verified oral-tradition transmission (P1 RULED). One house forming, Salvador da Bahia.
- Founder: production, pricing, brand, sales. **Junior** = decision-making master, rules all sacred
  material. **Vanderson "Macumbinha"** = content/delivery, **not** a decision participant (A12).
- Not SaaS, not a marketplace, not a credentialing standard. Provenance register examined, **rejected**.
- Treasury ≈R$20k: R$8–10k earmarked M0 (scope movable, A10), R$10–12k free, **reserve floor R$5,000
  = automatic hold**. Modeled stand-up R$60–120k → staged from own cash.
- **Founder rule: one new standing obligation at a time.**

## One law + six red lines (charter, RULED, unamendable)

**Access is bought; standing is only earned.**
1. Sacred boundary governed by the tradition's named authority (Ketu Candomblé = Junior). No game
   mechanics on sacred material unless that authority designs the form. No sacred iconography in art
   without approval.
2. Standing never purchasable — no entry, passage, honour, acknowledgment.
3. Supply curated: vouched invitation via a bench, **no self-serve door**.
4. **No synthetic voice ever.** No cloned masters, no machine-composed calls "in his style."
5. Free tier's permanent-access promise holds, incl. the Room's free set — a **one-way door**.
6. Consent + credit structural: withdrawal takes material down, credit permanent, price worlds never
   cross-wire. **No operating form exists** — no cross-system takedown anywhere (row 30 FALSIFIED).

## Founder facts (FF)

**FF1** Carlinhos Brown (Timbalada; intimate with candomblé percussionists) could reproduce a
provenance register at will → register can't be the moat. **FF2** A record of past events makes no
weekly habit; capoeira's corda marks progress *in* the game. **FF3** Both must play day one (the
acceptance test): single-player users who never interact with others; beginners who can't play to a
metronome (= most beginners). **FF4** "Opanijé" is the *toque* of Obaluaiê/Omolu.

## The Room — the mechanic

- **Student plays their own part inside the master's actual recorded battery** — alone, daily, other
  parts played by real named musicians. Isolated per-instrument stems = the product's **existence
  condition** (R16/R31), hence M0 rank 3.
- **App today has no audio layer**: no audio library, one opaque media reference per lesson, no mic,
  no filesystem. Separate players drift audibly in seconds. True multi-track needs a native engine
  (AVAudioEngine / AAudio-Oboe / shared C++ mixer) on both platforms + schema change so an item owns
  a *set* of files. No in-house mobile-audio experience.
- **R1 solution = pre-rendered subtraction ladder.** Fixed levels, not free part-muting → each level
  pre-renders server-side as **one stereo file** on the existing player. Zero engineering, best
  possible offline-rendered quality; **no mid-play mute/unmute** (a level change is a transition),
  **fixed tempo steps only**; storage = levels × tempos × part choices. Sizing: 4 parts × 4 levels ×
  ~4 tempos ≈64 files/rhythm × 2.5–3 MB (3 min stereo AAC) ≈180 MB/rhythm → 10-rhythm catalog
  1.5–2.5 GB. Stems still shot at M0 and rendered *from*; native engine still open for R2 (INPUT-41).
- **Subtraction, not simplification**: start agogô + student's own part, add parts back as they hold.
  True on-ramp needs no instrument — **palmas + the sung part**. Tier 1 recognition and tier 2
  vocalization live *inside* one room; **tier 3 is the base** (D7).
- **D28/R51 — the student pulls the lever.** The app never judges a part "held."
- **R15** reference pulse is an instrument of the tradition, **never a metronome**.
- **R17** one catalog with a per-item treatment field, not two tradition-scoped products. **A13**
  catalog is not secular-only — candomblé rhythms circulate secularly, are game material.
- **A15** tier 4 (peer/ensemble: ensemble stacking, entrada/steal, call-and-response) kept but **not
  the base**; if built, **turn-based** (R10 — latency/codecs destroy synchronous musical interaction;
  asynchrony is what lets a Bahian and a Berliner play at all, A3).

## Nothing scores the player (R28)

- **Layer 1 — facts about own play**: minutes, cycles held, parts attempted, levels reached
  (+"their take beside the master's" in R2). Uncapped, automatable; makes a student visible, **never
  entitles**.
- **Layer 2 — human attestation**: a master's judgment, capped by his hours, never computed; monthly,
  public, by name.
- **"Cycles held" = stayed in the loop for N cycles** — a playback fact counted without listening.
- → No machine verdicts anywhere; no peer voting/harassment surface; latency blocks nothing (binds
  scoring, not playing along); retention runs on an appointment with a named human, not a streak.

## Caderno (R18, demoted)

What the Room writes, not what the product is built around: transmission ledger = match history with
provenance. Records **events, never attainment**: *Received* (genuinely transmitted, incl. via a paid
private lesson), optional *Heard* (a master listened and responded publicly by name), *Confirmed*
(**Junior alone**, A5, non-purchasable). Invariants at the API contract layer: **R4 no link to any
payment record** (G0 audits as a query); **no user-claimed entries ever**; visibility governed by the
partition; **withdrawal-proof** (entry survives the material's removal); **record day one, present
later** — R1 shows the first entry, full surface in Release 3.

## Sacred partition (R20/R21) — per-item field, set by Junior

Values: `playable-inside · gamifiable (recognition/vocalization only) · teachable-but-not-gamifiable ·
archive-only · unrecordable`.
- **D17** enforced at the **API contract layer, validated on read, no client override** — holds only
  while every read path goes through the API. WP post meta is schemaless → **not a DB guarantee**.
- Captured **item-by-item at the M0 shoot** (INPUT-21). **R46** offline availability becomes a
  function of the partition value (sacred streams only, secular downloadable).
- **Fork INPUT-20**: Reading A — the rhythm as musical object is outside red line #1 (founder designs
  form), the liturgical layer (orixá association, ceremonial function, ceremony-only variants, songs,
  language, drum consecration) stays inside; Reading B — whole item inside. **Plan assumes A pending
  Junior.** Rule either way: **gamify the secular, archive the sacred**; mitigation structural —
  Junior's first-person authorship visible, his name on the partition, in his voice.

## Architecture and entitlement

- RULED: **A1** thin shell per milestone (paid-course delivery already built); **A2 app-first** (web =
  marketing); **A3 one app, both audiences** (BRL practitioner / USD immersion); **A4 dual purchase
  rails** in-app + web — ruled, **scheduled later** (D15).
- **R13** app asks the backend what an account owns, **never reads a local store receipt** → rails
  interchangeable. **R29 the Room is an instrument, not a catalog: it plays whatever the account
  owns.** Free tier owns a small fixed permanent set; course buyers own their course; members buy the
  **cycle** — the recurring line sells no content (R3).
- Audit: `GET /wp-json/opanije-mobile/v1/entitlements` live, returns **503 `service_disabled`** — R13
  exists, off by a constant, but **capped at two purchasable courses and one purchase shape**.
  Rewrite now at zero rows/zero users.
- Gaps → R1 scope: **no accounts in the app**; self-registration disabled on both WordPress installs;
  sign-in designed **Google OIDC only** (Apple likely needs an equivalent privacy-preserving option);
  **no in-app account deletion** (store requirement + LGPD + red line #6, INPUT-46); **two WordPress
  installs = two user tables = no single identity**.

### Release 1 — the door and the Room (D13, D26, D27)
Job: convert ledger rows 6 (list is an asset) and 24 (Room creates a practice habit); open M4 runway.
**Ships:** free course folded in, permanent promise intact; the **Primeira Chamada** (mestre's
recorded call) closing into the first Caderno entry, shown — free course + free set are **one door**
(D6); Room as pre-rendered ladder on the existing player; Layer-1 facts, no scoring; in-app account
creation, sign-in **and deletion**; entitlement rail rewritten and switched on (free set + owned
courses, no ceiling); existing course catalog folded in as owned rooms where migration is cheap (the
"Netflix clone" becomes a shelf); **immersion trust surface** — the actual named battery you'd sit
inside in Salvador + consultation booking, **no checkout**; **cross-system takedown** (short-lived
signed tokens, CDN asset removal, entitlement revocation) proven by a **drill**; instrumentation +
crash reporting; operator catalog surface in wp-admin; replacement privacy policy (LGPD-aligned,
bilingual, controller named) + Play Data Safety + Apple privacy labels. **Zero commerce surface.**
**Deferred to R2:** capture-for-submission + age gate; native engine if needed; the offer engine
(server-driven offers by locale and declared intent); full catalog migration; the Heard tier.
**D26 no microphone anywhere in R1**, incl. local self-recording — costs the "their take beside the
master's" half of Layer 1; buys no mic permission, no mic disclosure, no minors interaction surface,
no filesystem work.
**D27 offline deferred to R2** — costs poor-connectivity users; buys takedown by streaming revocation
alone, no crown jewels in a device sandbox, INPUT-47 off the critical path, encryption-at-rest +
per-session keys designed once. Mitigation: 2.5–3 MB files → aggressive HTTP caching. Reverse if the
founder judges offline essential to the Bahian practitioner.
**R48 free set** (list = INPUT-27, founder's): **one rhythm fully laddered**, **two paths only**
(palmas+voice needing no instrument; agogô), **4 levels × 3 tempos = 24 renders ≈60–70 MB**, plus the
Primeira Chamada and first Caderno entry. Paid line then sells *more rhythms and more parts*. Must be
shot at M0.

### Release 2 / Release 3
**R2:** submissions machinery serving two products with one build (monthly cycle + private-class
pre-submission); capture + age gate; offline, encrypted at rest, partition-gated; in-app
private-class booking bounded by the ring-fenced calendar; native engine if INPUT-41 requires; Heard
tier; offer engine. **R3:** Caderno's full public surface; international cycle; in-app subscription
rail if M4 funded it; tier-4 mechanics if selected.

### The cycle — Roda restructured (R2/R5; assent INPUT-16)
Monthly, replacing the weekly live circle: **the call** (master records one rhythm, one lesson,
released as a piece) → **practice window** (two weeks; members work in the Room, log, submit) → **the
response** (he listens to a selection, corrects **publicly, by name, recorded**). Keeps the roda's
shape (one in the centre, the circle learning from one correction), drops only simultaneity; bounds
the master to 2 sessions/month, kills time zones, yields ≈24 reusable archive assets/yr. **Quarterly
real live roda**, Bahia evening, recorded for everyone else, framed as a **gift** so missing it churns
nobody. Domestic, Portuguese, BRL first (A7); international cycle after M4 (R8). Precondition:
`opanije_course/_module/_lesson` post types register only when the dormant rail is enabled → **no
screen exists on which to manage a course**; **"founder publishes the monthly call alone in wp-admin
without an engineer" is an explicit R1 acceptance criterion** (row 31).

### Three surfaces (R47) and instrumentation (R50)
Student app · **master's standing room** (docked tablet, one-tap join, **zero decisions**: no
accounts, no troubleshooting, no choices; carries cycle + 1:1 permanently) · **operator console**
(partition tagging, catalog ingestion, publishing the call, triaging submissions, entitlement admin —
**R1 needs only the catalog surface, in wp-admin**).
Instrumentation: the app records session started, 6 loops played, level 2 reached, day-7 return. Not
optional — M1's exit evidence *is* those numbers; cheap because it is a **byproduct of Layer 1**.
**First-party events into our own backend, no third-party analytics SDK at R1**, **plus a crash
reporter**. Collection must match store declarations.

## Estate (verified 2026-07-30)

One Hetzner VPS (2 vCPU, ~7 GB RAM, 38 GB disk, **73% full**), Ashburn VA: both WordPress installs,
both DBs, CRM, autonomous build loop. On it and nowhere else: WP secrets, Cloudflare Stream token,
GitHub token, Borg backup key export, **Android signing keystore**. Daily restore-tested BorgBase
backups but **passphrase deliberately removed** → archives readable by anyone with repo access. No
standby by operator ruling (**risk 16**). Media must move to object storage + CDN regardless of audio
path (INPUT-48). **CI advisory** — no branch protection, failing checks don't block merges, a merge to
`main` hard-resets and rebuilds the live tree. **Privacy fails store review:** Termly policy published
2021-04-15/modified 2022-03-14, cites GDPR+CCPA, **LGPD zero mentions**, no CNPJ seller named, **no
Portuguese version**, no retention schedule, no age gating, no deletion path; never submitted → no
content ratings, no Data Safety, no Apple labels; data residency (BR controller, US infra) never
considered. **No app-store accounts exist**; bundle id `com.opanije.course.debug.preview`; open in the
**company's CNPJ name, never personal** — Apple org enrolment needs **D-U-N-S**. **~2,600 lines of
orphaned course code** in the live store call deleted functions (latent fatal on the purchase path;
remove before M2). ACF Pro = per-site licence on two installs, seat count unconfirmed.

## Business model — seven lines, never cross-wired

Course R$297 one-time (≈R$184 contribution/sale; M2) · cycle membership R$59/mo, sells no content
(≈R$42/member/mo; M3) · **private 1:1 (A8), per session, both price worlds — IAP-exempt,
highest-margin digital line, the immersion's feeder** · immersion USD $2,500–4,000,
consultation-closed, **adult-only**, per-house profit engine (M4) · institutional licensing "Memória
Viva" US$500–2,000/yr + per-project, 6–18-month fuse (G4) · B2B bookings quoted via existing console ·
goods store attached to each line's instruments.
- **Payment reality (row 29 FALSIFIED):** payment only in `/shop` — PayPal live + manual bank
  transfer; Stripe and Mercado Pago installed but **inactive**; **no Pix**; store in **USD** while the
  course rail was designed BRL; main site's course rail has **no live payment path**; **no
  subscription capability anywhere**. → R1 no commerce; **Pix a hard M2 precondition** (INPUT-42);
  **M3 web-rail only** (D15); manual gateway's payee is an individual with a US phone/personal email,
  not the CNPJ seller of record.
- **Store tax (Apple 3.1.3(d), verified 2026-07-29; COVID deferral expired 30 Jun 2022):** realtime
  experiences between **two** individuals may use non-IAP (tutoring named first); one-to-few and
  one-to-many must use IAP. 1:1 **exempt** · cycle 15–30% · course 15–30% · live group session 15–30%
  · immersion none. R$400 class at 70% master share ≈R$120 via Pix vs ≈R$60 via IAP. Anti-steering
  varies by jurisdiction (Epic injunction, EU DMA) = INPUT-9, deferred to M2.
- **Capped vs uncapped:** confirmed track bounded by the master's listening hours (≈100–200 concurrent
  students); scarcity makes acknowledgment worth holding. Scalable: Room, cycle, archive, course.
  Cycle modeled at **150 members ≈R$77k/yr**; 300 (≈R$151k)/500 (≈R$252k) **upside, never counted**.
- **Master economics:** revenue share on his own line, fee per confirmation, cycle-listening comp, 1:1
  share per session, booking fees, permanent structural credit, production done for him. **R11 narrow
  no-digital-skill reading:** *no accounts, no decisions, no troubleshooting* — one button on a docked
  tablet isn't digital skill, diagnosing a dropped connection is.
- **Ring-fence (R6+R25):** confirmations, cycle listening and 1:1 draw the same scarce ear and one
  pays immediately → **Junior sets a three-way monthly hours budget** (INPUT-12): confirmation hours
  (not sellable, never surfaced as inventory) · cycle-listening · private-class. Availability is only
  what the budget grants — a **hard constraint on the booking calendar**.
- **Funnel (A6 RULED: the Roda does NOT feed the international immersion).** Domestic: list → free
  door → paid course → cycle. International: subtitled free tier → the actual named battery you'd sit
  inside in Salvador → **paid 1:1 with that named master** (pre-submission recorded outside the app
  until R2) → consultation → season; the 1:1 is the only mechanism manufacturing the relationship a
  trust-sold product needs (R7/R32). Institutional: long fuse, outreach from M3, labor only. Immersion
  runway opens at **M1** (D3).

## Milestone ladder

- **§7.0 precondition (D16, risk 16) — today, before everything:** escrow the Android signing keystore
  and Borg repo key off-box; restore a backup passphrase. Hours, near-zero cost.
- **Track B — private-class pilot (D1, immediate):** ten sessions across Junior and Vanderson, to the
  free list + performance network, both price worlds, booking/payment by hand; founder hosts all,
  logged at replacement cost. **R10 format:** student submits a recording 24h ahead → master listens
  beforehand (paid prep) → the live hour is correction, not diagnosis (sequential call-and-response).
  Cash ≈R$0. Exit = first MEASURED candidates: master payout, WTP at two price points, list
  conversion, founder-hour cost/sale, honest verdict on screen teaching, master's appetite for a second.
- **M0 — production sprint R$8–10k, ranked by irrecoverability:** 1 consent scope licensing
  **interactive/game use** (R19/INPUT-22); 2 Junior's ruling on marking the name (R35/INPUT-32);
  3 **isolated per-instrument stems** (INPUT-23) — impossible without re-recording; 4 five-value
  partition per item at the shoot (INPUT-21); 5 **standing room** (INPUT-15: fixed-mount camera, mic +
  interface, wired ethernet, 4G backup, docked tablet, one-tap join) — recoverable at a premium,
  recommended in scope; 6 English subtitling (INPUT-14) — schedule constraint only. Gather at the
  shoot: INPUT-16, -20, **-41**. Pre-shoot list (D14): escrow, -22, -23, **-27**, -21, -15/-14 budget
  calls, -44. **Hold: any recording without an executed consent instrument does not ship.** Exit:
  assets delivered, instruments executed with game-use scope, stems in the can, partition captured,
  **production cost per asset recorded**.
- **Pre-public checkpoint (D23), nine items:** CNPJ store accounts/D-U-N-S · **one combined counsel
  brief** (INPUT-37, -38, -39, -46, -47, -31, -35) · name clearance after Junior's -32 · **GUI
  industrial-design filing before any screen is public** · build-order ruling (R49/INPUT-51) ·
  house-mark/product-mark separation held ready (R43) · free set fixed (R30/INPUT-27) · repo migration
  + ACF seats (INPUT-45) · replacement privacy policy live.
- **M1 — Release 1 live (D21 cash-in is NOT ≈R$0; D22 sequenced).** Unquoted: object storage + CDN
  (**M1 uncostable until INPUT-48 returns a number**), counsel, store fees, contingent audio
  specialist (INPUT-43); all else pipeline/founder labour **logged at replacement cost, never zero**.
  Order: (1) other people's clocks — store enrolment, counsel brief, INPUT-41, repo migration, escrow;
  (2) entitlement rewrite + accounts/sign-in/deletion while rows are zero; (3) infra — object
  storage/CDN, branch protection, crash reporting; (4) product — render the ladder from M0 stems, the
  Room, Layer-1 + instrumentation, door + first Caderno entry, trust surface, wp-admin catalog;
  (5) takedown proven by drill; (6) design freeze → design filing → policy + store declarations →
  submission. **Critical path is not the code:** D-U-N-S, counsel turnaround, INPUT-41. Exit: list
  size, open/click/enrollment, free-door completion, First Call answer rate, **Room activation**
  (first-session completion, D7 return, minutes/user), takedown drill, row 31. Holds: list <500 → M2
  extends, audience-building becomes an M2 task; **if INPUT-41 forbids the ladder and the specialist
  quote would breach the R$5k floor, M1 ships without the Room** (door, Caderno entry, trust surface).
- **M2 — first paid cohort.** R$297 course; ≈55 sales recovers R$10k. Preconditions: **Pix live**;
  orphaned 2,600 lines removed. Targets ≥20 sales/30 days, ≥55/90 days; measure refunds, completion,
  Room usage of purchased content, founder selling hours. **CAC unmeasured, never "zero."** Hold: <20
  at day 90 → **hold the ladder**, diagnose list/offer/price before further spend.
- **M3 — the cycle stands (D4, D15).** Needs R2 machinery, INPUT-16, the wp-admin catalog surface.
  **Web rail only.** Targets ≥50 members by month 3; **month-3 cohort retention ≥70%** (the single most
  important number in the recurring model); attendance/submission/response-inclusion rates; master
  listening hours vs INPUT-12. Hold: retention <50% → the recurring model is wrong; fix cadence and
  format before any marketing spend.
- **M4 — immersion season (recapitalization).** ≥6 students (capacity INPUT-5) at ≈R$8–9k margin
  ≈R$48–54k. **Working-capital rule (RULED):** deposits collected ahead of supplier commitments,
  supplier timing scheduled against deposits monthly, refund/cancellation reserve held, **never below
  R$5k even in full cancellation**. Hold: <4 confirmed by the go/no-go date → postpone.
- **M5.** Cumulative contribution **≥R$120k within 12 months of M1**; one paid institutional pilot
  signed (any value); term-license substitution rights + withdrawal carve-outs drafted first; **IP
  portfolio filed** (R38 software registration, conditional on INPUT-37, + copyright deposits; R39
  defensive publication after the design filing).
- **Track A grants:** enter the cash model **only when awarded and unrestricted** (INPUT-7).

## Gate (month 12 from M1)

**G0** zero red-line violations, consent/rights archive audited clean incl. game-use scope, partition
enforced at the API contract layer, R4's no-payment-link invariant run as a query · **G1** cumulative
contribution ≥R$120k (stretch R$180k), per-line normalized margins · **G2** cycle month-3 retention
≥70%, churn curve known · **G3** one season at ≥60% capacity, margin/student in band, working-capital
timing recorded · **G4** one paid institutional pilot signed, carve-outs executed · **G5** funnel
measured end to end (list → free door → first entry → paid → cross-product), founder-labor CAC priced ·
**G6** adjacency dossier for both candidate houses, house-#2 choice ratified *at* the Gate · **G7**
brand/title clean — Junior's name ruling recorded, name cleared or product-mark separation executed,
chain-of-title complete with **two** findings (no third-party claim; machine authorship resolved or
explicitly accepted as unresolved). Outcomes: exercise the venture option (red lines in the documents
before the first check); continue bootstrapped to house #2 at one per year; or hold at one house.

## Floor case and venture arithmetic (ASSUMPTION, R$5.50/USD)

Immersions +R$264k · course +R$156k · cycle (150) +R$77k · archive USD + institutional + B2B +R$85k ·
ops −R$60k = **≈+R$520k (~USD 95k)** designed target, not fact; ops excludes object storage/CDN
(INPUT-48); 1:1 unmodeled until Track B. **P3 RULED:** ops excludes the founder — his modest draw
(INPUT-4a) is a fixed cost in the monthly model, market-rate replacement comp in the normalized P&L
with the delta disclosed. Venture: 10 mature houses ≈R$5.2M; a US$500M fund return needs ≈US$2.5B exit
at 20%/$3.33B at 15%/$5.0B at 10%, implying ~1,754–2,632 houses — **linear house-stacking is not the
venture case**. The case is the cross-house exponent, six HYPOTHESES: within-house retention from the
accumulating record; **trained-ear portability** (candomblé-trained listener warm on capoeira day one
— compounds with houses, not players); institutional catalog expansion; brand-driven CAC decline;
shared rails and playbook (**cheap only once they are rails, not one machine in Virginia**);
portadores/referral loops. **Refusals of scale (RULED, part of the asset):** invitation-only supply, no
self-serve door, standing never purchasable, no machine verdict advances anyone, growth house by house.

## IP and defensibility

- **Moat = catalog + provenance**, not network effect, not a register: the archive, consent-and-credit
  architecture, Junior's partition, the stem library, the pedagogical sequence, the named masters, the
  mark, the expressive content — protected by **contract, exclusivity, discipline**, not registration.
  **A14 RULED: the differentiator is Opanijé's own gamified product, not a lineage register.**
- **Threat model:** the clone books a studio and records his own battery; stolen stems have little
  market without the rights architecture, partition, pedagogy and names. **The realistic loss is a
  hobbyist remix posted publicly — a red-line-#1 problem, not a revenue one** → protection points at
  the partition, not DRM.
- **Unownable:** game mechanics categorically unpatentable in Brazil (LPI art.10 excludes rules of
  games VII, programs as such V, educational methods III, presentation of information VI); US practice
  agrees (Compendium §910, *Baker v. Selden*). **Locating uniqueness in the mechanic builds the moat
  on the only thing nobody can own.**
- **The name (FF4):** LPI 124,III bars signs offending religious worship; INPI *Manual de Marcas*
  §5.08 tests the sign **and the connotation from the goods designated** — the toque's name on an
  *archive* reads differently than on a *game*. Exposures: examination risk; **red line #1 — nobody
  has asked Junior whether marking it is acceptable at all** (INPUT-32, prior to and independent of
  legality); "we trademarked the name of Omolu's toque" is screenshot-shaped. **Sequence RULED: R35 →
  R34 → any filing or further public use**, with **R43** house-mark/product-mark separation held ready.
- **Portfolio:** marca (classes 9/41/42 + retail, blocked pending above) · **direito autoral** (Lei
  9.610/98 — where the real asset lives: master recordings, phonograms, calls, stems, audiovisual
  identity, rules-as-text; Biblioteca Nacional deposit = declaratory dated evidence) · **registro de
  programa de computador** (cheap, declaratory, **conditional on INPUT-37**) · **desenho industrial**
  (LPI 95ff, most under-used instrument; INPI admits static **or dynamic** GUI — closest thing to
  protecting the mechanic in motion; **novelty dies on public disclosure → file before screens are
  public**, R37) · **Marco Legal dos Games** (Lei 14.852/2024, unregulated, INPI rito 1H 2027; keep a
  dated dossier; INPUT-33) · **conjunto-imagem/trade dress — the real anti-clone remedy** (no
  registration; unfair competition LPI 195/209; **a consistent, documented, distinctive audiovisual
  identity is itself the legal asset** — design consistency from R1 + a dated design record are legal
  work, R40) · patents **declined**.
- **FTO:** **defensive publication of the base mechanic, after the design filing** (R39). Publish the
  mechanic; **never publish the catalog, partition, stem architecture, or pedagogical sequence**.
- **Chain of title (D12):** no third party ever had access; all code and describing documents are
  **machine-written by AI agents** on the VPS, founder-directed; only human-authored material is the
  main-site English article copy. **Row 21a no third-party claim (evidenced); row 21b machine-authored
  code may have no human author — what is filed, by whom, copyrightable at all? UNRESOLVED**, bounded
  to R38. Repos sit on the **personal GitHub account** (migrate, INPUT-45); `opanije` declares
  **GPL-3.0** over GPLv2-or-later WordPress core *and* a proprietary React Native app (INPUT-38).
- **TCE (R44):** no binding international instrument (WIPO IGC 53, Sept 2026); nobody can block
  Opanijé and Opanijé cannot invoke one — the traditional material isn't the asset, **the consented
  recordings are**.

## Governance

**Founder holds (RULED):** every price, product name, brand and voice, which shape leads, which
traditions and masters are invited, every business term, form decisions on secular material.
**Benches hold (RULED):** everything sacred under the tradition's named authority — lineage language,
the partition item by item, standing per-episode archive review, INPUT-16/20/32/41, Confirmed
allocation (A5). **A charter red line cannot be narrowed from one side.** Master succession: recording
preserves knowledge but doesn't replace a live authority; named delegation is revocable; each house
charter defines incapacity, death, withdrawal, dispute, suspension, successor selection, status of
student records and licensed material, continuity of circles and institutional commitments.
**R11 operator staging:** founder hosts sessions 1–20 as measurement → standing room → operating hire
(funded from M4). Technical succession today: **nobody, and nobody could.**

## Risks (21)

1 key-person: the masters ARE the product · **2 gamification read as commodifying the sacred (most
exposed)** · 3 treasury thinness (+storage/CDN, counsel, store fees, contingent audio specialist) ·
4 unmeasured demand on every line · 5 federation execution · 6 founder bandwidth · 7 teller withdrawal
vs institutional licence · 8 membership churn · 9 working capital on the long fuse · 10 FX/
multi-currency (USD store vs BRL rail; payee ≠ seller) · 11 adjacent incumbent (FF1) · 12 brand-name
failure (refusal; authority objection) · 13 minors and children's data (D26 removes capture, age gate,
under-18 submissions from R1; INPUT-39 still answers age rating) · 14 craft risk of screen teaching ·
15 chain of title · **16 single point of total loss (severe, immediate)** · 17 machine authorship ·
18 no in-house mobile-audio capability · 19 privacy/store compliance · 20 deployment without a brake ·
**21 R1 scope and schedule — the failure mode is not a bad Release 1, it is no Release 1 with M0's
cash spent and nothing measured.**

## Evidence ledger (33 rows)

**No row upgrades without a dated measurement; no successor document may cite a row above its status;
falsified rows retained with the work that makes them true.** RULED 1–3. VERIFIED-INTERNAL: 5 (AI
pipeline — 14 CI workflows, 175 test files, 31 merges/24h; cost log owed), 21a, 28 (entitlement
architecture exists, dormant, two-course cap). **FALSIFIED 2026-07-30:** 27 (app can play the battery
as separated parts), 29 (can sell in BRL), 30 (can honour red line #6). **UNRESOLVED:** 20 (marking
the name), 21b, 31 (founder runs the cadence without an engineer), **32 (fixed ladder pedagogically
adequate)**. HYPOTHESIS: 6, 8, 12–18, 23–26, **33 (R1 activation without self-recording)**.
ASSUMPTION: 7, 9, 10, 11, 19, 22. UNMEASURED: 17 (CAC).

## Open inputs (INPUT-1…51; blocking in bold)

**Founder:** 1 list stats · **2 M0 scope + per-item quotes** (blocks the shoot) · **3 master terms as
agreed** (blocks the cash model) · 4/4a fixed costs + founder draw · 5 immersion window, capacity,
supplier cost/payment structure · 6 B2B pipeline · 7 grant calendar · 8 exact treasury · 10 price
parity across rails · 11 1:1 prices both worlds + never-cross-wire implementation · 14 subtitling in
M0? · 15 standing room in M0? (recommended yes) · 19 ratify narrow R11 · 24 ratify tier 3 as base ·
26 Vanderson's role per A12 · **27 the free tier's permanent set** (blocks the M0 shoot) · 28 reading
of A14 · **40 CNPJ store accounts / D-U-N-S** (longest lead time) · **42 payment architecture:
Pix/Mercado Pago, BRL vs USD, payee↔CNPJ** (blocks M2) · 43 audio-specialist budget (only if -41
forbids the ladder) · **44 infrastructure ruling: escrow, passphrase, does "no second machine" survive
M0's recordings** (blocks M0 delivery) · 45 repo migration + ACF seats · **48 storage/bandwidth/CDN
plan** (M1 uncostable without it) · **51 build order: lock-and-file vs private beta**.
**Junior (± Vanderson):** **12 three-way monthly hours budget** (blocks 1:1 scale-up + M3) · **16 is
the async monthly cycle acceptable as a roda** (blocks M3) · 17 private self-facing timing feedback
(deferred) · 18 does a "Witnessed" tier exist · **20 Reading A assent** (decides how much catalog the
game gets) · **21 five-value partition per item at the shoot** · 30 part-subtraction pedagogy ·
**32 is marking the name acceptable under red line #1** (blocks any filing) · 36 secular/liturgical
continuum + vocalization as the tradition's teaching method · **41 is a fixed ladder pedagogically
adequate, or is live part-by-part muting required — the single highest-leverage schedule question in
the estate**; tempo half reported closed (Junior: slowing a toque is normal), confirm the relay.
**Counsel:** 9 anti-steering BR/US/EU (deferred to M2) · 25 what is protectable (after registrability)
· **31 INPI search + opinion on 124 III/VI by class** · 33 does audio-first meet Lei 14.852 art.5,I ·
34 independent confirmation of 21a + the 21b question · **35 design grace period + whether prior
disclosure occurred** · **37 machine authorship** (blocks R38) · 38 repo licence inconsistency ·
**39 privacy instruction — LGPD policy, Portuguese version, named controller, retention schedule, data
residency, minors and age rating, store disclosure forms** (blocks Release 1; absorbs INPUT-13) ·
46 in-app deletion + LGPD deletion path across two installs and the CRM · **47 must withdrawal reach
already-downloaded copies, or is loss of access from the next session faithful discharge?** (off R1's
path under D27; blocks R2's offline design).
**Production, before the cameras roll:** **22 do the consent instruments license interactive/game
use?** (cheapest irreversible item in the estate) · **23 are isolated per-instrument stems in M0
scope?** (plan requires yes).
**Issued by this plan:** 49 does the app ever listen — A no ears (recommended) / B ears, description
only, never gating / C ears that gate (advised against) · 50 offline protection posture · 51 build
order. **INPUT-13 absorbed into -39. INPUT-29 does not exist in the register** (flagged, not invented).

## Deltas awaiting ratification (D1–D28)

D1 Track B starts immediately, pre-M0 · D2 M0 re-ranked by irrecoverability · D3 immersion runway
opens at M1 not M3 · D4 M3 = monthly cycle + quarterly live gift · D5 G0 expanded, G7 added · D6 free
course and Room free set are one door · D7 tier 3 base, tiers 1–2 on-ramp · D8/D18 ledger → v0.4, 33
rows · D9 M5 exit adds IP filings · D10 floor case annotated · D11 VERIFIED-INTERNAL label added ·
D12 chain of title reframed, row 21 split · D13 Release 1 re-scoped · D14 pre-shoot list gains escrow
+ INPUT-27 · D15 M3 web-rail only · D16 escrow elevated to ladder precondition · D17 "data layer" →
"API contract layer, validated on read, no client override" · D19 risks 16–20 added, 3 amended ·
D20 FALSIFIED declared a ledger status · D21 M1 cash-in restated: not ≈R$0 · D22 R1 sequenced with a
named critical path + door-only hold condition · D23 pre-public checkpoint merged into one nine-item
gate · D24 free-set shape recommended · D25 carry-ins recorded as recommendations not rulings ·
**D26 no microphone anywhere in Release 1** · **D27 offline deferred to Release 2** · **D28 the
student pulls the ladder lever.**

## Recommendations (R45–R51) and cash discipline

R45 Option A (no ears) for R1; if it ever listens, Option B (description, never gating), never C →
INPUT-49 · R46 offline encrypted at rest, per-session keys, owned material only, availability a
function of the partition value, **no platform DRM** → INPUT-50/-47 · R47 three surfaces named and
budgeted (ADOPTED) · R48 free-set shape → INPUT-27 · R49 lock-and-file the design before any tester
sees a screen → INPUT-51 · R50 instrumentation as a Layer-1 byproduct, no third-party SDK, plus crash
reporter (ADOPTED) · R51 the student pulls the lever (ADOPTED).
**Cash discipline:** floor R$5,000, automatic hold; committed (M0) vs free, all else spends only
against a milestone's stated purpose; **no pre-counting** — unawarded grants, unsigned pilots,
unclosed B2B, unmeasured 1:1 sit in the pipeline, never the cash model; recapitalization = Track B
measures free → M2 returns production spend → M4 lifts treasury into the stand-up envelope. Derived
artifacts in order: monthly 12-month cash model (the day INPUT-3, -4, -8, -48 land); first
measured-quarter update writing ASSUMPTION→MEASURED conversions with dates; post-Gate only,
replication and cross-house models, governance/succession matrix, raise materials.
**Re-verify:** store 3.1.3 + anti-steering at M2 before purchase screens · LPI 124,III practice and
filing classes before any filing or further public use of the name · GUI design practice before filing
· Marco Legal regulation quarterly · TCE after WIPO IGC 53 · **the estate's technical state before
Release 1 scope freezes** (it changes daily under an autonomous build loop) · Apple login-services
requirement before sign-in is designed · store deletion requirements before submission · D-U-N-S and
store fee amounts immediately · audio source-separation state of the art before the stem-exclusivity
argument is used externally · independent chain of title at INPUT-34.
