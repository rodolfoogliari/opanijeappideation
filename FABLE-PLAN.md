# FABLE PLAN — Opanijé: from estate to instrument

**Author:** Lead product designer / technical strategist (Fable), 2026-08-05.
**Status:** PROPOSED plan of execution. Everything here respects the Charter verbatim; where it
contradicts a non-charter register entry, it says so and why. Nothing here upgrades any ledger
label. This document exists to produce the estate's first MEASURED rows.

---

## 1 · The verdict — what Opanijé should actually be

Opanijé, at its best, is **a real master's battery in your pocket, free forever, that you can play
inside within ninety seconds of opening it** — and behind that free instrument, a narrow, human,
expensive path to Salvador: a paid course, a private hour with Junior, a seat in the immersion. The
app is the instrument and the funnel. The business is the human layer.

**The thesis survives — but only in a reduced form.** The estate's thesis is that intrinsic
motivation anchored to real named masters can outperform extrinsic mechanics. As a claim about
*design*, it is defensible and the research compaction supports it: groove is its own reward, this
product needs less extrinsic scaffolding than a language app, and reproach mechanics correlate with
quitting. As a claim about *this company right now*, it is untested and — this is the hard part —
**currently untestable**, because there is nobody to test it on. 33 YouTube subscribers, 12 leads,
5 orders none completed. The thesis does not fail on contact with the audience; it fails to make
contact at all. So the thesis must shrink from "intrinsic motivation retains students" to
"**a free instrument that is genuinely fun in the first ninety seconds gets shared, and sharing is
the only distribution this company can afford.**" That version is testable with the assets on hand,
and everything in this plan serves it.

**The estate is over-designed relative to what it can ship, and the ratio must be inverted.**
145,680 words of ideation; 244 numbered decisions; 88 recommendations; 84 reserved inputs; **zero
seconds of instructional audio under Opanijé's control**. The single most consequential sentence in
both recon reports is this one: *"The uploads directory contains zero instructional video or audio."*
Every register, every fork, every delta is downstream of recordings that do not exist. The Charter
itself is excellent — two pages, genuinely constitutional, and this plan treats it as physics. But
the apparatus around it has been producing governance faster than product, and for a solo
non-engineer that apparatus is now the main schedule risk (risk #21 names this exactly: "the failure
mode is not a bad Release 1, it is no Release 1").

**What I am cutting, said once, here:**

1. **The monthly cycle (D81) is out of Release 1.** It strains the one-obligation rule (risk #29,
   the estate's own flag), it has no price, no format, no audience, and it spends Junior's scarcest
   resource on an appointment almost nobody will attend. Junior's monthly hours go to Track B
   private classes instead, which produce MEASURED revenue evidence. The cycle returns when there
   are 100 weekly-active students to attend it. D81 is ADOPTED-contingent-on-INPUT-82; I am
   answering INPUT-82's go/no-go as **no-go for now** on the founder's behalf-to-ratify.
2. **The standard publication (D82/G22) is frozen, not cancelled.** Publishing a notation standard
   with no users and no steward is planting a flag on an empty field, and risk #28 (the standard
   outruns the corpus) is guaranteed at current corpus size: zero. The frame stays drafted, in the
   drawer, until the free instrument has users.
3. **The full R$8–10k M0 production shoot is deferred; a lean Capture Day replaces it** (§5). The
   irrecoverability logic that makes M0 the governing deadline applies to *what is shot*, not to
   *when the big shoot happens*. A lean day that honours every one-way door — consent scope with
   interactive/game use, isolated stems, partition captured item-by-item, solfejo locked to the
   battery — loses nothing that a later professional shoot cannot add.
4. **In-app commerce (D37/S4) is out.** The app sells nothing and links to no checkout. Purchases
   happen on the web (Pix via the already-built Mercado Pago rail); the app asks the server what an
   account owns (R13, already the architecture). This removes Google Play billing integration, the
   15–30% tax question, and the anti-steering brief from the critical path in one move. D15's
   web-rail-only instinct was right the first time.
5. **The register apparatus goes into maintenance mode** (§7). The Charter stays alive; almost
   everything else freezes.

What remains after the cuts is small, and that is the point: a free instrument, one paid course,
a private-class pilot, and an immersion funnel — built on two half-finished apps that are, together,
about 80% of the product.

---

## 2 · The salvage assessment

The recon verdict — "combine, don't restart" — is correct, and I am making it specific.

### Kept, and promoted to *the* product

**`apps/opanije-room` is the product base.** 24,066 lines, 493 tests, 13 bilingual screens, a
working APK, and — decisively — the only artifact on earth that implements the estate's actual
inventions: the conducted echo loop, the landscape screen drum with syllable zones, fade-and-rejoin,
the three-facts-plus-best closing, the Caderno. This is where all future work lands. The production
bundle ID becomes `com.opanije.room` (decide once, now; the mockup ID `com.opanije.room.mockup` and
the parked `com.opanije.course.debug.preview` both retire).

**`apps/opanije-mobile` is the parts donor.** It is not merged wholesale; four modules are lifted
into Room, then the repo is archived with a README pointer (not deleted — its iOS project is the
only iOS asset in the estate and costs nothing to keep):

| Lift into Room | Why |
|---|---|
| The OAuth adapter + transaction store (`src/platform/` auth code) and `/auth-return` route | Room's sign-in is fake; this is the real one, already written against `opanije-mobile-api.php`'s native OAuth bridge |
| `expo-secure-store` session handling | Sessions do not belong in AsyncStorage |
| The repository factory (`mock-repository` / `http-repository` / `repository-factory`) | Room's `src/data/api.ts` seam gets a real implementation behind a config switch; mock mode remains the dev default |
| `expo-video` + the signed-playback pattern | For the paid course stage (§5, Stage 4) |

**The dormant course rail is the backend, unchanged in architecture.** The ~270 KB of merged
mu-plugin PHP — `opanije-course-pay-mercadopago.php`, `opanije-course-access.php`,
`opanije-course-native-identity.php`, `opanije-course-catalog.php`, `opanije-mobile-api.php`,
`opanije-course-stream.php` — is the single most under-valued asset in the estate. It is a
designed, deployed, versioned REST contract with fixtures and a closed JSON schema that the
TypeScript side already tests against. Nobody gets to propose a new backend. The VPS hosts it today
at ~0.04 load; it will host it at 1,000 users without noticing.

**The build infrastructure is kept whole:** `build-room-apk.sh`, `verify-apk.sh` (the RECORD_AUDIO
tripwire is load-bearing — it is red line enforcement in CI form), `with-verified-apk`, the netrun
workaround, the emulator smoke harness, `npm run gate`. One amendment before any Play submission:
**extend `verify-apk.sh` to `bundle*` tasks**, closing the documented AAB escape.

**The website is kept as the funnel and the app's content spine.** Specifically kept: the
`/wp-json/opanije/v1/facts` feed (becomes the app's remote config/catalog seed), the bilingual
translator layer, the legal pages, the 15 vertical hero clips (onboarding media, already cut), the
brand tokens (`#B7780D`/`#F4EEE1`), the PWA scaffolding, and the WooCommerce `/shop` for immersion
USD sales exactly as it is. The outreach CRM is kept and gets a real job in §4.

### Merged

**Room's screens onto Mobile's spine** is the only integration project in the plan, and it is
bounded: wire `http-repository` to `opanije-mobile-api/v1`, wire the OAuth adapter to the identity
plugin, keep everything else local-first. Estimated three to four careful vibecoding weeks, and it
is Stage 4 work, not Stage 1 — **the free instrument ships before any of it**, in mock/local mode,
because the free instrument needs no account (a design gift: sign-in gates nothing free — E13 makes
the free room permanent anyway, so requiring login for it would be pure friction).

### Deleted — each one earned

1. **`createFakeRoomAudio()`'s production import path.** Room's own review found it: production code
   can forge a permanent Caderno entry. The function moves under `__tests__/`/dev-flag guard. This
   is a half-day and it is defect #1 in the plan.
2. **Room's process ceremony — the source-seal, the GATES register as a live process, the
   adversarial-round machinery.** These were correct for a mockup whose job was to not overclaim.
   Carried into a shipping app run by one non-engineer they are friction that will silently eat the
   calendar. `GATES.md` is frozen into a static appendix; unanswered gates that still matter are
   re-homed as the short question list in §7. The source-seal test is deleted (its purpose —
   proving no hidden native edits — is served by the permission verifier and by Expo prebuild being
   deterministic). One review round per stage replaces the eight-round protocol, run by an
   independent model, briefed with the Charter's §9 prohibition list.
3. **Website legacy surface:** `/final37/`, `/legacy1/`, `/3323-2/` (untitled, indexed, embarrassing
   in a store-review context), `/camp-options/` (superseded by `/camp-options-final/`), `/plans/`
   (2021-era sales page contradicting current positioning). `/blog/` merges into `/journal/`.
   Justification: every one of these is reachable from a store reviewer's or a prospective
   student's browser, and each contradicts the brand the app will carry.
4. **The stale LearnPress options and the committed `node_modules`** in the live theme — hygiene
   deletions, zero risk.
5. **Junior's three inconsistent origin stories** (age five / age fourteen / began 1996 with
   Timbalada) are reconciled to one canonical bio in the facts feed, with Junior, in one WhatsApp
   exchange. The app syndicates the feed; it must not syndicate the contradiction.

### Explicitly not built new

No new backend framework, no new design system (the tokens exist), no new CMS (the wp-admin catalog
authoring surface exists), no new notation renderer (G2: the solfejo *is* the notation and it is
audio), no iOS anything.

---

## 3 · The modern core — four product concepts

What "modern in 2026" means for *this* builder: not on-device ML for its own sake — the Charter
forecloses the two obvious ML moves (voice assessment, generated audio), and that is a feature, not
a bug, because it forces the modernity somewhere a solo builder can actually win: **scheduled-audio
architecture that makes latency irrelevant, local-first design that makes the backend optional,
link-first distribution that makes the app store optional, and an agentic content pipeline that
turns one recording day into a season of product.** Every concept below is buildable by Rodolfo
with Claude Code on the proven toolchain.

---

### Concept A — **O Instrumento Livre** (The Free Instrument)

**What it is.** Room finished and shipped with real audio: one commons rhythm (Ijexá — the estate's
own named example), played by Junior, as a free, permanent, account-free instrument — the echo loop,
the screen drum, fade-and-rejoin, the quiet count — delivered *both* as an Android APK/Play listing
*and* as a link-playable web room at `opanije.com/toca` (Room is react-native-web already; the web
export has run in headless Chrome across every route). One tap from an Instagram reel to playing
inside Junior's battery, no install, no sign-in.

**What the student does.** Opens a link or the app; hears Junior count in; voices the part with the
solfejo; the voice withdraws; they hold the part alone on the screen drum while the battery
continues; the voice returns and they hear whether they held. Three facts and a personal best. Ninety
seconds to two minutes, then again if they want.

**Why it is modern.** (1) *Scheduled, not triggered audio* (G10/D60) is the architecturally modern
move — it converts the hardest mobile-audio problem (latency) into a non-problem, using nothing but
`expo-audio` and pre-rendered files, and the timing grid read from the authored render (R73) means
zero DSP. (2) *Local-first*: everything — facts, bests, Caderno — lives on-device and needs no
server, which is both the 2026 sync-engine posture and the cheapest possible ops. (3) *Web-first
distribution*: the same codebase ships as a URL, which is the only distribution mechanism that works
at 800 followers. (4) *Agentic content pipeline*: the ladder renders, the timing JSON, and the
per-level mixes are produced from Junior's stems by a Claude-written ffmpeg pipeline extending the
existing `scripts/audio-spec.json` machinery — content production becomes a script, not a project.

**Cost.** 4–6 vibecoding weeks from today's Room (real audio integration, web deploy, defect fixes,
polish). **Junior:** one recording day (~6–8 hours) plus one hour reviewing the built screens
(INPUT-69, -79).

**Red lines touched.** #5 — this is the permanent free set, so its contents are a one-way door:
deliberately one rhythm, two parts, two speeds (the founder ratifies the list, INPUT-80, before
anything ships). #1 — Junior sees every surface before it is public, and the partition value of the
free rhythm (INPUT-52) is captured on the recording day. #4 — the 72 synthetic placeholder renders
are replaced by real strokes before ship; nothing synthetic voices anything. The grading
constitution is already implemented in Room's closing screen. No mic exists; the build fails if
RECORD_AUDIO appears.

**Honest failure mode.** Nobody shares it. A free instrument with no audience is a tree falling in
an empty forest; the concept's success is 100% coupled to §4 being executed, not just the build.
Second failure mode: ledger row 45 — scheduled audio reads as miming, not playing — which is why the
first ten humans (Stage 2) are asked exactly that before anything else is built.

---

### Concept B — **A Cidade dos Toques** (The City of Rhythms)

**What it is.** The repertoire map (D75) grown into a narrated cultural atlas: each rhythm-room
carries Junior's recorded narration — what this toque is, where it lives, what it is for — woven
with the estate's existing riches: 3,400 images, the Salvador POI dataset (`inc/poi-data.php`), the
journal articles, the vertical hero clips. Free rooms are playable (Concept A); locked rooms are
audible as narration and openable by purchase. The map ends where the map should: Salvador itself —
the immersion as the last room in the city.

**What the student does.** Wanders. Listens to Junior tell them what Ijexá carries before playing
it; reads where samba-reggae was born while standing, virtually, on the street it was born on;
discovers that the city is bigger than the free room; meets the immersion not as an ad but as the
place the map has been pointing the whole time (E10's instinct, generalized).

**Why it is modern.** This is the *agentic pipeline* concept: Claude assembles rooms from existing
assets — transcribing Junior's narration (his voice, his consent; the student's voice is never
touched), subtitling EN/PT, selecting imagery, generating the room metadata against
`catalogSchema.ts` — so a room costs Junior fifteen minutes of talking into a phone and costs
Rodolfo one pipeline run. Content velocity without content burden.

**Cost.** 2–3 vibecoding weeks on top of Concept A (the map exists in Room in demo mode; this is
data plus a narration player). **Junior:** ~15 minutes of voice memo per rhythm; 10 rhythms ≈ 3
hours, recordable on his sofa.

**Red lines touched.** #1 — narration is sacred-adjacent per item; the partition (D33 extends it to
narration) is captured per recording, and anything Junior marks archive-only or unrecordable simply
isn't in the atlas. R53 — no narration names a price or product; the immersion room is reached by
the map, described by the app's own copy, never sold in Junior's voice.

**Honest failure mode.** It becomes a museum — beautiful, respectful, unvisited. Media apps without
a practice loop have no retention; this only works bolted to Concept A, never instead of it.

---

### Concept C — **Perguntas ao Mestre** (Ask the Master)

**What it is.** The human layer at sustainable cost: students send questions through ordinary
channels (WhatsApp — the estate's own sanctioned outside-the-app submission path, keeping D26
pristine), and Junior answers a curated handful **in recorded voice, by name**, monthly-ish. Each
answer becomes a permanent, indexed, bilingual entry in the app — a growing library of the master's
actual voice answering actual students.

**What the student does.** Asks. Hears their own name in Junior's voice a week later. Browses two
years of accumulated answers the way one browses a master's memory.

**Why it is modern.** The pipeline again: Claude transcribes, translates, subtitles, and indexes
each voice note into a searchable library entry; the marginal cost of an answer approaches the cost
of Junior saying it. And it is the *ethical* modern answer to parasocial design: instead of
simulating relationship with an AI persona (foreclosed by red line #4, and rightly), it amortizes a
real relationship across the whole student body — the research compaction's own conclusion that
relatedness must come from the real human, delivered at a cost the ring-fence (R6/R25) can afford.

**Cost.** 1–2 vibecoding weeks (a list screen, an audio player, a WhatsApp deep link — mostly
existing patterns). **Junior:** ~1 hour per month, from anywhere, no camera, no appointment. This
is the cycle's soul at a tenth of the cycle's obligation, and it can *become* the cycle later.

**Red lines touched.** #2 — being answered by name must never be purchasable or read as standing;
selection is Junior's whim, the library entry records an event (a question answered), never an
acknowledgment, and the Caderno is untouched. #6 — every answer is a master recording inside the
takedown perimeter; entries come down if material comes down.

**Honest failure mode.** No questions arrive (audience again), or Junior's cadence lapses and the
surface reads abandoned. Mitigation: the surface ships with three seeded answers recorded on
Capture Day, and displays no cadence promise whatsoever — it is a library, not a subscription.

---

### Concept D — **O Curso, Aberto no Quarto** (The Course, in the Room)

**What it is.** The R$297 course made real and connected: activate the dormant Mercado Pago rail
(Pix/card/installments) on the web, put the course's video into Cloudflare Stream behind the
existing signed-playback adapter, and let the app play what the account owns — narrated lessons
(E14) plus deeper rooms of the paid rhythm. The first revenue line with an actual checkout in
company history.

**What the student does.** Finishes the free rhythm; hears Junior offer the next step (E7 — shot on
Capture Day, price-free); finds the course on the web; pays with Pix; opens the app and the city has
new lit rooms.

**Why it is modern.** Honestly, it is not — and that is its virtue. It is the disciplined
activation of 270 KB of already-merged payment code, a provisioned Cloudflare Stream account, and a
versioned REST contract, i.e. the thing a 2026 solo builder does *instead of* building infrastructure:
switch on what exists. The one genuinely modern element is entitlement-aware local-first sync —
owned content plays from the same scheduled-audio engine, streamed with aggressive HTTP caching
(D27's mitigation), no download library, no DRM.

**Cost.** 3–4 vibecoding weeks (OAuth integration, `http-repository`, entitlement reads, video
player) **plus the operator-gated activation** — real-payment evidence, the razão social and counsel
confirmations, and the `OPANIJE_COURSE_ACCESS_MODE` flip, which are founder-time and calendar, not
code. Single product only (1049) until the `W1-CL-ENTITLE` per-course-grant defect is fixed;
product 1050 stays unpublished exactly as the SSOT warns. **Junior:** the course content exists
(Google Classroom); call it one day of re-recording the weakest lessons properly, deferrable.

**Red lines touched.** The one law, centrally: access is bought, and only access. R4's
no-payment-link invariant is already in the rail's architecture. The app never shows a price and
never links a checkout (this also keeps Google Play policy simple: entitlements bought elsewhere,
app sells nothing).

**Honest failure mode.** M2's own hold condition: fewer than 20 sales in 30 days against a list
that doesn't exist yet. Which is why this is Stage 4, sequenced *after* the free instrument has
demonstrated any pull at all — a checkout without a funnel is furniture.

---

### The ranking, and the pick

**1. Concept A — O Instrumento Livre.** ← **the recommendation**
**2. Concept D — the course rail activation** (first money; second in sequence, close behind)
**3. Concept C — Perguntas ao Mestre** (cheapest durable differentiation; slots into any stage)
**4. Concept B — A Cidade dos Toques** (grows the surface once A retains anyone)

**Why A wins:** it is the only concept that converts the estate's central invention into a testable
object; it is the furthest along (the code exists, the APK exists, only the audio is missing); it
is the only one that works with zero audience *and* is itself the audience strategy (D73's own
logic: giving the instrument away *is* the distribution); every other concept compounds on it and
none substitutes for it. It also carries the plan's largest honest risk (row 45, playing-vs-miming)
— and a plan should put its riskiest load-bearing hypothesis first, where failing is cheapest.

The four concepts are not alternatives; they are a sequence (§5). The ranking exists so that when
time runs short — it will — the cut order is already decided: B first, then C, never A or D.

---

## 4 · The audience problem

Distribution is the product's binding constraint, and I will not romanticize it: **~800 Instagram
followers, 33 YouTube subscribers, 12 leads, and no mailing list infrastructure.** Any plan that
says "launch and they will come" is fiction. Here is the unromantic version.

**Say the quiet part: the app is a lead magnet before it is a business.** The immersion runs
$800–$4,800 per head at ≈R$8–9k margin per student. One immersion sale equals thirty-plus course
sales. The app's first commercial job is to be the most credible, most shareable proof-of-mastery
artifact the immersion funnel has ever had — "play inside the actual battery you'd sit in at
Salvador" is a better trust surface than any brochure. The R$297 course is the second job. A
standalone app business is the third job, and it is a year away at best. Sequencing money this way
is not a retreat from the estate; A6/A7 and the funnel design already point here.

**First 100 users — hand to hand, Portuguese first, WhatsApp native.**

1. **Junior's own 1,000+ former students** are the entire seed strategy. They are real, they are
   his, they are in Salvador and in WhatsApp groups. One voice note from Junior — his voice, his
   framing, R53-clean — with the web-room link, forwarded into his network. If 5% touch it, the
   first 50 users cost nothing and arrive pre-trusting. This is the single highest-leverage
   distribution act available to this company and it costs one voice note.
2. **The web room makes sharing possible at all.** Nobody installs an APK from a stranger; everyone
   taps a link. Every reel, every bio, every WhatsApp forward points at `opanije.com/toca`, which
   offers the Play listing only *after* someone has played. Install is the second date.
3. **Reels with a playable punchline.** The content format is fixed and repeatable: 20–30 seconds
   of Junior playing (shot on Capture Day — a dozen of these are a side product of the day),
   captioned EN/PT, ending on "toca esse toque agora — link na bio." One per week is sustainable;
   the pipeline (§3) subtitles them. 800 followers is small but it is not zero, and the format is
   built for forwarding, which is where Brazilian reach actually happens.
4. **Track B is also distribution.** The ten hand-booked private classes (D1 — kept, unchanged) put
   ten real students in a room with Junior and the app; each is a measurement *and* a testimonial
   *and* a WhatsApp node.

**First 1,000 — communities that already exist, reached by the tool that already exists.**

5. **The world is full of batucada.** Samba schools, blocos, capoeira academies, university
   percussion ensembles across Europe, North America and Japan — hundreds of organizations whose
   members are precisely "adults who cannot play to a metronome but love this music" (FF3). The
   **outreach CRM at `/var/www/outreach` is a working cold-outreach engine with two market lanes
   (EN-GLOBAL / PT-BR) and it is idle.** Point it at a hand-built list of 200 such groups with a
   non-commercial offer: a free instrument their members can practice with between rehearsals,
   played by a Timbalada-lineage mestre. Ask for nothing but a forward. This is the one channel
   where 200 emails can produce 1,000 users, because each recipient is a multiplier, not a user.
6. **Search, not subscribers, on YouTube.** 33 subscribers is irrelevant; "how to play ijexá" /
   "toque ijexá tutorial" search volume is not. The journal articles show the SEO instinct already
   exists in text. The video version: Capture Day's teaching passes, lightly cut, titled for
   search, description linking the web room. Evergreen, compounding, zero marginal cost.
7. **Rebuild the free-course funnel as the app.** Today the "free email course" sends one Google
   Classroom link and has captured 12 leads. The free course *becomes* the free instrument plus an
   actual email sequence (the CRM can send it). The permanent-access promise carries over intact —
   nothing given is taken; it is given again, better.

**What I am not proposing:** paid acquisition (no budget, CAC unmeasured, and G5 would rightly
flag it), press (no story yet — "app launches" is not news; "the first MEASURED cohort playing
Candomblé rhythms" might be), influencer outreach (nothing to trade), and any growth mechanic
inside the app (share/export is closed by G18/D69 and red line #6 — distribution happens *to* the
app, not *through* it, until INPUT-71 is answered).

**The number that governs continuation:** 100 people who played twice. Not installs, not follows —
returns. If six months of the above cannot produce 100 second sessions, the app is not a business
and should settle honestly into being the immersion's trust surface — which is still worth having
built, at roughly the cost this plan spends.

---

## 5 · The build sequence

Five stages. Each names what ships, what it proves, the vibecoding weeks, Junior's hours, and the
single measured number that decides continuation — with the ledger row it converts. The estate has
never had a MEASURED row; this sequence manufactures them in order of cheapness.

### Stage 0 — Hygiene and the ask (week 0; runs during week 1's days too)

**Ships:** nothing public. Escrow the signing keystore and Borg key off-box with a restored
passphrase (D16 — hours of work, outranks everything, still not done). Fix defect #1
(`createFakeRoomAudio()` out of production reach). Extend `verify-apk.sh` to `bundle*`. Lift the
OAuth/SecureStore modules from `opanije-mobile` into Room's tree (dormant). Send Junior the one
message that starts everything: the classroom transcription ask (INPUT-78), rough-audio permission
(INPUT-72), and the Capture Day date.
**Proves:** the company can no longer be destroyed by one disk failure.
**Junior:** 0 recorded hours; one WhatsApp reply.
**Continue when:** keys verified restorable from the second location. (No ledger row; this is the
precondition for having a ledger at all.)

### Stage 1 — Capture Day and the pipeline (weeks 1–3)

**Ships:** internally — one commons rhythm (Ijexá, pending founder ratification of INPUT-80 and
Junior's availability confirmation), captured properly on a lean rig: consent instrument with
interactive/game-use scope **signed before anything rolls** (INPUT-22, rank 1, non-negotiable),
isolated per-part stems (Junior layered over the agogô reference in headphones — S6's method at
kitchen-table scale), four solfejo passes locked to the battery (two parts × two speeds), the
stroke one-shot library for the free battery's instruments, 10–12 count-ins including the
return-after-absence variant (R79), the welcome, the two next-step invitations (price-free), three
seeded Perguntas answers, a dozen 30-second reel clips, and the five-value partition captured
item-by-item on the day (INPUT-21), including the free rhythm's own value (INPUT-52). Then the
agentic render pipeline: stems → ladder renders + `AUTHORED-TIMING` grids, replacing all 72
synthetic placeholders.
**Spend:** the one operator consent this plan needs — a modest capture kit (USB interface + two
mics + stands), inside the existing M0 earmark, roughly R$2–3k. Everything else is labour.
**Proves:** Opanijé owns instructional audio for the first time in its history.
**Junior:** one day (6–8 h) + the sofa narrations for three atlas rooms if energy allows.
**Continue when:** stems render into the app and a full session plays end-to-end with real audio on
the founder's own phone. **First MEASURED row: row 44/45 prototype half** — one session, one real
device, does scheduled audio feel like playing (a written, dated, honest answer from the first two
humans: Rodolfo and Junior).

### Stage 2 — Ten humans (weeks 3–5)

**Ships:** the APK to ten hand-picked testers (private sideload — pre-store, satisfying
lock-and-file caution by keeping screens out of public marketing), Junior first: he sees the drum,
the echo, the engagement surfaces on a working phone, discharging INPUT-69, -79, -62, -41 in one
sitting with one object (the estate's own "gather five inputs in one mockup sitting" plan,
executed). Then the nine-question pilot (R87).
**Proves:** the pedagogy carries through glass.
**Junior:** 2 hours (the sitting) + his form verdicts.
**Continue when — the stage's single number:** **row 46 MEASURED** (a beginner goes voice → screen
drum in one sitting: yes/no per tester, target ≥7/10), with rows 48 and 50 (echo reads as teaching;
fade reads as information) answered alongside. If row 46 fails, stop and redesign the door — do not
proceed to distribution with a broken first session.

### Stage 3 — Public: the free instrument (weeks 5–8)

**Ships:** the web room at `opanije.com/toca`; the Play Store listing (CNPJ developer account —
INPUT-40 started in week 1 because its lead time is the critical path; replacement bilingual
privacy policy live; Data Safety honest: no mic, first-party analytics only per R50); first-party
event instrumentation (session started, first session completed, D7 return — the byproduct-of-facts
design already specified); the GUI design filing executed in the same week the listing goes public,
per R37's ordering, at whatever counsel quotes — if the quote breaches the R$5k floor, the founder
decides between delaying the listing and accepting the risk, and this plan recommends **accepting
the risk**: a design registration protecting a product with no users protects nothing worth its
floor-breach. Distribution acts 1–3 from §4 begin the same week.
**Proves:** whether anyone outside the family plays.
**Junior:** one voice note to his network (the seed act), ~1 h/month of Perguntas.
**Continue when:** **row 41 and row 24's first half MEASURED** — first-session completion rate and
D7 return, the estate's own two headline numbers, now with real values and dates. Gate to Stage 4:
**100 completed first sessions**, any D7 value (the number is a baseline, not a bar — R81's
label-it-first discipline applies).

### Stage 4 — First money (weeks 8–14)

**Ships:** accounts (Google OAuth, in-app deletion — store requirement), the `http-repository`
against `opanije-mobile-api/v1`, entitlement reads, the course's video in Cloudflare Stream behind
signed playback, and — operator-gated, with counsel's razão-social confirmations and a real-payment
drill — the Mercado Pago rail flipped from `dormant` to `enabled` on the web. Single product. The
takedown drill runs here too: red line #6's operating form (signed-URL expiry + entitlement
revocation + cache behaviour) proven before any paid consented material ships — converting **row 30
from FALSIFIED**.
**Proves:** the one law works as machinery: access is bought.
**Junior:** 0 required (course content exists); optionally one re-record day.
**Continue when:** **row 7 MEASURED** — course sales at R$297 against the funnel's real size. Hold
condition inherited from M2 unchanged: <20 sales in 30 days → hold the ladder, diagnose
list/offer/price before any further spend. **Row 25 MEASURED in parallel** via Track B's ten
private classes, which have been running hand-booked throughout.

### Stage 5 — Compound (month 4+, shaped by the numbers)

Atlas rooms (Concept B) if D7 return holds; the full professional M0 shoot **only now**, sized by
what retention proves worth deepening; the cycle (D81) revisited when 100 weekly actives exist;
the standard (D82) revisited when there is a corpus for it not to outrun. Each is a decision the
first MEASURED quarter gets to make with numbers the estate has never had.

**Total to first money: roughly 14 vibecoding weeks and two to three days of Junior's recorded
time.** Every week of it runs on machinery already proven on this workstation.

---

## 6 · What the vibecoder must never attempt

These are the holes that eat weeks silently. Each comes with the substitute that buys ~85% of the
value at ~10% of the risk. Print this list.

1. **Real-time audio DSP or a native low-latency engine** (Oboe, AAudio, AVAudioEngine, any
   "just a small C++ mixer"). This is the single most dangerous attraction in the estate. Nobody
   on this team can debug a buffer underrun, and the estate already found the escape: **scheduled
   pre-rendered audio with the grid read from the authored render** (G10/D60/R73). If a feature
   seems to need live mixing, the answer is another pre-rendered file. If INPUT-41 ever truly
   forbids the fixed ladder, that is a budget-and-specialist decision for the founder (INPUT-43),
   never a vibecoding project.
2. **Custom native modules / ejecting from Expo.** The moment `android/` stops being disposable
   prebuild output, every upgrade becomes an archaeology project. Substitute: Expo config plugins
   (the pattern `with-verified-apk` already proves), and if a capability truly isn't reachable in
   managed Expo, the feature is redesigned until it is.
3. **iOS, in any form, including "just checking if it builds."** No Mac, no Xcode, no signing
   identity — infeasible, permanently, from this machine. Substitute: **the web room is the iPhone
   version.** It reaches every iOS user with zero store risk, and it is already built.
4. **A new backend, a Node server, a "proper" API, or any second server stack on the VPS.**
   Substitute: the existing mu-plugin PHP + `opanije-mobile-api/v1`. Every server-side feature is a
   new endpoint in that contract, tested against its JSON schema, deployed by the existing CI.
5. **Subscriptions, renewals, dunning — any recurring billing.** The estate confirms none exists;
   building it is a company-sized project. Substitute: one-time purchases only. If the cycle ever
   sells, it sells as a manually-renewed season pass until real subscription demand is MEASURED.
6. **Google Play billing / in-app purchase integration.** Weeks of integration, 15–30% margin, and
   an anti-steering compliance brief — for a store with no audience. Substitute: web checkout (Pix),
   server-side entitlements, an app that sells nothing and links to no checkout.
7. **Per-device latency calibration or any timing-accuracy readout.** Barred by the Charter
   *and* technically unsound (the offset is unknowable — the estate's own analysis). Substitute:
   the generous binary window, and `R75`: log the two Android latency flags from day one so the
   real device distribution is known for free.
8. **Audio source-separation, stem extraction, or AI audio cleanup on Junior's recordings.** It
   will not produce clean stems (the estate is right that strokes cannot be extracted from a
   performance), it wastes the one recording day's authority, and generated audio drifts toward
   red line #4. Substitute: capture stems and one-shots *as stems and one-shots* on Capture Day —
   the microphone does what the model cannot.
9. **A custom sync engine or offline-download library.** Conflict resolution is a graveyard.
   Substitute: local-first AsyncStorage for everything free; idempotent progress writes (the
   operation-ID pattern already in `opanije-course-native-adapters.php`) for everything owned;
   streaming with HTTP caching per D27. Facts survive the network (E16); nothing else syncs.
10. **Device-farm QA, or pretending emulator evidence is device evidence.** Substitute: the
    emulator harness for regressions + **two physical phones** (one low-tier Android bought used —
    the one hardware purchase this plan endorses, ~R$400) + the ten Stage-2 humans as the real
    test lab. The two things only a human can verify — speaker audio feel and touch latency — are
    founder-time, scheduled, not hoped for.
11. **Multi-product entitlements before `W1-CL-ENTITLE` is fixed.** The rail grants the whole
    library for one purchase if a second product is wired to the same constant. One product until
    the per-course grant is built and proven with a test purchase.

---

## 7 · The governance dividend

244 decisions are an asset exactly insofar as they are *spent* — cited to end a discussion in five
seconds — and a liability insofar as they generate process. The estate was built by a PM-and-founder
dialogue that no longer exists day-to-day; a solo builder needs the Charter as **a pre-answered
question bank, consulted at design time, not a review gate passed at ship time.**

**Keep alive (the working set, four documents):**

- **`CHARTER.md`** — read before any design session, unchanged, sovereign.
- **The vocabulary sheet** (METHOD §5) — pinned next to the string files; every user-facing string
  passes the sentence test at the moment it is written. This is where classification leaks in, so
  this is the one live review.
- **The prohibition list** (Charter §9) — the brief handed to any independent review model each
  stage: "find violations of these fifteen lines," which turns the Charter into automated review
  fuel rather than ceremony.
- **`LEDGER.md`** — the only register this plan *adds* to. Every stage's exit number is written in
  as a dated MEASURED row. The ledger is the estate's conscience and it finally gets fed.

**Freeze (history, not process):** `DELTAS.md`, `RECOMMENDATIONS.md`, `CONTRADICTIONS.md`,
`FORKS.md`, `sessions/`, Room's `GATES.md` and review archive. Frozen means: read-only, cited when
useful, never extended. A build decision that once would have been a numbered delta becomes one
line in a plain `BUILD-LOG.md` — date, decision, door label if one-way. If the founder ever wants
to re-open the monthly decision hour, the frozen registers are all still there.

**Collapse the 40+ open INPUTs to the eight that gate this plan**, each discharged at a named
moment: INPUT-22 (consent scope — Capture Day morning, before anything rolls), INPUT-80/-52 (the
free set — founder ratifies this week), INPUT-21/-70 (partition + sampling permissions — on Capture
Day, with Junior, item by item), INPUT-78/-79/-69/-41/-62 (the echo, the drum, the ladder, the
engagement form — one Stage-2 sitting with a working phone), INPUT-40 (store accounts — started
week 1 for lead time), INPUT-39 (the counsel privacy brief — commissioned once, week 1, as the one
combined brief R78 wanted). Everything else is answered by default ("the plan's position stands
unless contradicted"), logged in BUILD-LOG, reversible. The estate's own door rule already licenses
exactly this: *two-way doors are decided by default; only one-way doors get the formal treatment.*
This plan just enforces the rule the estate wrote and then didn't follow.

**The one new ritual:** a weekly thirty-minute WhatsApp exchange with Junior — this week's screens
or clips, next week's asks. Red line #1 as a habit instead of a gate queue. His formal assents get
gathered in working sittings around real objects, which the estate itself concluded is how he
actually answers.

---

## 8 · The first two weeks

Ten working days. Written to be started tomorrow at 09:00. Each day assumes Claude Code open on the
WSL machine; Junior-dependent items are front-loaded as *asks* so his latency never blocks a build
day (the estate's own sequencing wisdom: his latency is uncontrolled, yours is not).

**Day 1 — Stop the total-loss risk; send the ask.**
Morning: escrow. Copy the Android signing keystore and Borg repo key to two off-box locations
(encrypted USB + a second cloud location), restore a backup passphrase, verify a test restore.
Have Claude walk every step; do not print any secret to any log.
Afternoon: one WhatsApp message to Junior (draft it with Claude, in Portuguese, warm): the Capture
Day invitation with two candidate dates in week 2, the classroom-transcription ask (INPUT-78 — "tell
me, voice note is fine, how a first lesson with a total beginner actually runs, minute by minute"),
and rough-audio permission (INPUT-72). Then start the two slow clocks: Google Play developer account
under the CNPJ (INPUT-40) and the counsel email commissioning the combined privacy brief (INPUT-39).

**Day 2 — Make the codebase the product's.**
In `apps/opanije-room`: fix `createFakeRoomAudio()` (move behind test/dev guard; add a test that
fails if production code can reach it). Extend `verify-apk.sh` to `bundle*` tasks. Change the
bundle ID to `com.opanije.room`. Run `npm run gate`; build the APK with `~/box/build-apk.sh`;
install it on your own phone. **Play a full session with the synthetic audio. You are the first
human to ever hear this app. Write down, dated, what it felt like** — that note is the ledger's
first primary evidence.

**Day 3 — The consent instrument and the kit.**
With Claude, draft the Capture Day consent instrument: interactive and game use licensed, isolated
stems and one-shot sampling in scope, broad the first time (R19), bilingual, to be recorded in
Junior's own voice and signed on paper before cameras roll. Send it to counsel for a same-week
review alongside the privacy brief. Order the capture kit (USB interface, two mics, stands,
headphones — operator spend, ~R$2–3k, inside the M0 earmark). Draft the Capture Day run-sheet from
§5 Stage 1's inventory: every pass, every count-in, the partition questions, the reel clips.

**Day 4 — The free set, ratified; the pipeline, started.**
Morning, founder hat on: ratify the free set (INPUT-80) — this plan's recommendation: **Ijexá, two
parts (agogô + one drum part), two speeds** — and write the one-line ratification in BUILD-LOG. It
is a one-way door; take an hour, not a week. Afternoon: have Claude build the stem→render pipeline
against synthetic stand-ins — a script that takes N stem WAVs plus a timing spec and emits the
ladder mixes and `AUTHORED-TIMING` grids that Room already consumes. Prove it end-to-end with fake
stems so Capture Day's output drops into a working machine.

**Day 5 — The web room, proven.**
Export Room to web; deploy behind `opanije.com/toca` on the VPS (nginx location + static bundle —
the deploy rail exists). Fix what breaks (audio unlock on first tap, landscape prompt, touch
targets). By end of day a link you can send anyone plays a session with placeholder audio. Do not
publicize; this is plumbing-proof, and screens stay out of public marketing until Stage 3's filing
decision.

**Day 6 — Lift the spine.**
Bring `opanije-mobile`'s OAuth adapter, SecureStore session handling, and repository factory into
Room's tree behind config flags, all dormant (mock mode remains the default). Add the
`/auth-return` route. Archive `opanije-mobile` with a README pointing here. Run the gate; build;
confirm the APK still verifies clean (no new permissions).

**Day 7 — Capture Day rehearsal.**
Full dry run alone: rig the kit, record yourself layering claps over a reference into the pipeline,
render, hear it in the app the same afternoon. Every problem found today is a problem Junior never
sits through. Finalize the run-sheet; print two copies of the consent instrument; charge
everything. Cut the day's reel-shot list.

**Day 8 — Capture Day** (or its scheduled date — the rehearsal and run-sheet make the day
Junior-shaped, not tech-shaped).
Consent first, on paper and in his voice, before anything rolls. Then the run-sheet: reference
pulse, layered parts to headphones, solfejo locked to the battery, one-shots, count-in bank,
welcome, the two invitations, three Perguntas answers, partition questions item-by-item written
down as he speaks them, reel clips last while the room is warm. Back up every file to two
locations **before dinner**.

**Day 9 — Real audio in the instrument.**
Run the pipeline on the real stems. Replace the synthetic renders. Build; install; play. Somewhere
around mid-afternoon, for the first time, **the app plays Junior's actual battery and your finger
keeps his groove alive.** Send the APK link and the web link to nobody yet — first write the dated
note: does scheduled audio feel like playing? (Row 45's first evidence, from human #1.)

**Day 10 — Junior meets the product; the pilot is loaded.**
Sit with Junior (or ship him the APK with a call): the drum, the echo, the fade, the closing screen,
on a real phone with his own sound. Gather, in one sitting, INPUT-69, -79, -41, -62 — his form
verdicts, written down in his words. Recruit the ten Stage-2 testers from his network and yours;
schedule them across the following week. End the day by writing the ledger's first two dated rows
and the week-3 plan.

Ten days in, Opanijé has: keys that can't be lost, a codebase with one owner, owned instructional
audio for the first time in its existence, a working instrument on two phones and a URL, the
master's assent gathered around a real object, and ten humans booked. That is more shipped product
than the previous 145,680 words produced — with every red line intact.

---

*Filed to the estate as a PROPOSED plan. The founder ratifies §1's five cuts (one line each in
BUILD-LOG suffices); Junior's gates are gathered where the plan says, around working objects. The
first MEASURED row lands on Day 9.*
