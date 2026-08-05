# Opanijé — As Built

**What actually exists, verified 2026-08-05.** Everything below was observed directly: read-only
inspection of the code, HTTP fetch of the live site and its JSON feeds, and read-only inspection of
the production VPS. Nothing was modified anywhere. Where something could not be reached, it says so.

**Why this file exists.** The estate is a record of what was *decided*. This is the record of what
was *built* — and the two had drifted far enough apart that a design plan written from the estate
alone got nine of its seventeen load-bearing claims wrong. Read this before planning anything.

**What it replaces.** This document compacts the 2026-08-05 recon and verification set —
`VERIFICATION.md`, `MASTER-BRIEF.md`, `FABLE-PLAN.md` and `compacted/A`–`I` — into one file, and
those twelve were removed once it existed. They were 96,089 words, of which the great majority was
a compaction of documents that were already in this repository. They remain recoverable from git
history at commit **`e38917a`**.

**An honest limit on that claim.** A first pass of this file *did* drop material, and an audit
comparing every distinctive identifier and figure in the deleted set against the surviving tree found
it. The load-bearing losses were restored — Room's documentation inventory, the VPS capacity envelope
and what it can and cannot host, the salvage verdict, and the site's deployment debris. What remains
dropped is deliberate: exact byte sizes of individual plugin files, theme filenames, the full
immersion price matrix, and workstation build-trap detail that lives in the machine's own
`CLAUDE.md`. **If a number is load-bearing and you cannot find it here, check `e38917a` before
assuming it never existed.**

**Status and provenance, stated precisely because the line references are the point.**

- **Facts about `apps/opanije-room`** were read in a **sparse** worktree at HEAD **`4dde6752`**, whose
  sparse spec admits only `/apps/opanije-room/` and `/docs/`. Status **VERIFIED-INTERNAL**
  (`METHOD.md` §1) — self-audit by inspection, not independent audit.
- **Facts about `apps/opanije-mobile` and the WordPress estate** (§2 and §3 below) could not be read
  there at all and were read in the full clone at HEAD **`99991cef`**. Same status. **Roughly half the
  line citations on this page belong to that second tree, not the first** — check the right one.
- **Facts about the live site and external channels** (§4, and the reach figures in particular) are
  **VERIFIED-EXTERNAL** (`METHOD.md` §1) and carry their own re-verification requirement: follower
  counts, search results and press claims drift, and the press claims were never independently
  corroborated at all.

---

# 1 · `apps/opanije-room` — the product

**This is the app.** It is the only artifact implementing the estate's actual inventions, and under
**D89** all future work lands here. It is not a mockup any more.

| | |
|---|---|
| Stack | Expo SDK 57.0.7, React Native 0.86.0, React 19.2.3, expo-router 57, TypeScript 6.0.3, New Architecture on. Node pinned 22.21.0 |
| Size | **12,443 lines of implementation**, 11,623 lines of test, 144 TS/TSX files |
| Tests | **621 tests / 55 suites.** 613 pass, 8 todo, 0 fail, in 10 seconds — *after* `source ~/box/mobile-env.sh` |
| Routes | 13, bilingual PT/EN throughout |
| Artifact | 98.2 MiB release APK, 2026-08-04, `com.opanije.room.mockup`, two-ABI (`arm64-v8a`, `x86_64`) |
| Dependencies | Deliberately small. **No video, no networking library, no auth SDK, no payments SDK** |

**The APK is a *release* variant signed with the *debug* key** (`build-room-apk.sh:46`). Fine for
sideloading, **not store-submittable**. `android/` is gitignored, so it is untracked build output.

### What is real and ungated

- **The screen drum** (`drum.tsx`, `ZoneField.tsx`). Landscape lock with the prior lock restored on
  unmount and user-visible recovery if it throws. Zones are proportional flex children with one
  `Pressable` each, gaps drawn on a `pointerEvents="none"` layer so they create no dead hit area.
  `zonesForDial()` clamps to 3 hand syllables (Pá/Tum/Dum) or 2 stick (Ti/Tá). **There is no
  geometric hit-testing** — no coordinate math, no zone rect table. Functionally equivalent for a
  divided surface, but "zone hit-testing" in the coordinate sense does not exist.
- **The Caderno** (`caderno.ts`, `caderno.tsx`). Fully real, ungated, on-device. Forgery resistance is
  designed in: an opaque token only past 3 completed cycles, ids rejected unless
  `practice-${sessionId}`, and `commit()` throws *"Caderno credit requires observed authored
  playback"* unless a private checkpoint has run.
- **The audio engine** (`engine.ts`, 523 lines). `allowsRecording: false` is hard-coded and the
  interface has **no capture method** — red line #4 enforced in the type system.
- Navigation, on-device persistence, PT/EN i18n, adaptive layout, large-text and reduced-motion
  handling, a takedown drill.

### The 13 routes — the surface Stage R is redesigning

| Route | State |
|---|---|
| `/` presentation | Explains the ~5-minute session, offers PT/EN. Silent by design |
| `/signin` | **Stub.** Looks like Google, grants a local session only. Authenticates nothing |
| `/intention` | Stores morning/afternoon/evening locally. **Schedules no actual notification** |
| `/welcome` | Placeholder for Junior's future talking-head. Synthetic image, click sound. **No video, no real voice** |
| `/choose-part` | One placeholder rhythm ("O toque livre"), Hand vs Stick, 3 provisional tempos |
| `/room` | **The core loop.** Auto-conducts listen → together → your turn → together again → beat. The app keeps time; **it does not listen to or grade the user** |
| `/drum` | Landscape, tappable zones with syllables, a lever changes zone count. **No mic, no correction, no scoring** |
| `/closing` | Session facts only. No ranking |
| `/ending` | Only after the final round. PT = invitation to next session; EN can open Salvador contact. **No price, no checkout** |
| `/caderno` | Read-only automatic journal, persisted on device |
| `/home` | Today's session, Caderno preview, rhythm map |
| `/review`, `/past-the-door` | **Demo-only**, gated behind the build flag |

**Bilingual by hand, not by library.** `strings.ts` is one hand-written table of ~713 lines — **no
i18next, no ICU, no runtime translation layer** — with ~172 key-lines per locale and PT/EN key
equality enforced structurally by `i18n.test.ts:48-59`. **Every user-facing string Stage R touches
lives in that one file and must be added in both languages or the suite fails.** It is also where the
Charter's vocabulary rule (METHOD §5) is enforced in practice.

### What is gated OFF in every ordinary build — the largest gap between code and product

Three of the five mechanics are behind `playLayerEnabled` (`AppRuntime.tsx:239-242`), false unless
`__DEV__` or `EXPO_PUBLIC_ROOM_DEMO`:

- **The echo loop.** With it on, a session runs `voice-over → learner-alone ("Sua vez") →
  voice-return ("Juntos outra vez") → battery`. The withdrawal is a **real asset swap**, not a volume
  trick — `renderEntryState()` resolves a different render per phase. Off, it is
  `voice-alone → voice-over → battery` with no withdraw and no return.
- **The fade.** Binary `full` (0.6) / `thin` (0.2) on the selected-part companion only, never the
  authored battery, recomputed per authored cycle, recovering fully the next one. **No decay curve.
  No cross-session decay at all** — nothing stores a last-practice timestamp. And **the feeding
  measure is computed and discarded**: `tap.ts:82-83` computes a 50%-of-grid-positions proportion,
  but presence is decided by raw "did you touch anything at all".
- **The closing screen.** On: three fact tiles (cycles with you · longest hold · setting) plus a
  persisted, monotonic personal best with a one-shot cue. Off: **a title and a Done button.**

Two whole routes are demo-only as well: `review` and `past-the-door` (`_layout.tsx:46-52`).

**The tests encode the gating deliberately** — `closing.test.tsx:234` asserts the facts are *absent*
by default. A plan that treats these as shipped features is planning against a demo build.

> **This is what ledger row 59 measured.** The tester who scored the app 0/10 and reported *"there
> was no gamified mechanic"* was describing this gate accurately. See `BUILD-LOG.md`.

### One flag, two jobs — a trap

`EXPO_PUBLIC_ROOM_DEMO` sets **both** `playLayerEnabled` (`AppRuntime.tsx:241`) **and** the
demonstration route tree `REVIEW_ROUTE_TREE = ['review','past-the-door']` (`_layout.tsx:48`,
`routeTree.ts:8`). `build-room-apk.sh:63-64` states the constraint itself: those surfaces *"must stay
that way in anything a student could receive."* **A demo build therefore hands a tester the play
layer and `/review` together.** Separating the two gates is D94a's scope.

### Audio — 72 synthetic files, and swapping them is a pipeline project

All 72 `.wav` are `math.sin` plus seeded noise through a one-pole low-pass, from a 516-line stdlib
Python generator. Identical format throughout (PCM 16-bit stereo 22050 Hz). Three distinct byte sizes
across 63 loop files, every mtime inside a 2-second window — one generator run. ~34.3 MiB, **committed
to git** (74 tracked files including 2 JSON). A repo-wide search finds **zero** audio of any format
outside that directory. `"voice-*"` files contain no speech by design, enforced structurally by a test.

Timing is authored, not derived: `AUTHORED-TIMING.json` carries `cycleMs` 8000/6000/4800 with 8 evenly
spaced offsets per part. **BPM is metadata only** — application timing loads solely from that artifact.

**Provenance is a closed chain and it fails shut.** All 72 on-disk sha256 match `GENERATED.json`;
`sha256(generator)` matches `audio-spec.json.generatorSha256`; `sha256(spec)` matches
`GENERATED.json.specSha256`; the recomputed set digest matches `expectedAssetSetSha256`. Enforced by
`assets.test.ts:490-523`. **Never disable it to make a build pass — regenerate** (D100). And the
generator itself **hard-fails while `JUNIOR-SUPPORT-ARRANGEMENT` is unresolved**
(`make-placeholder-audio.py:287-289`), so regenerating audio is coupled to a decision only Junior can
give (INPUT-87, risk #32).

### Scheduled, not triggered — with four real exceptions

Cycle boundaries are **observed, not timed**: `observeLoop` subscribes to `playbackStatusUpdate` and
reconstructs elapsed media time, with a wrap-tolerance check so an arbitrary seek cannot mint a false
cycle. There is **no `setTimeout` scheduler and no seek-into-a-long-file** — each render is one
authored cycle, looped natively. Tap judgement is grid-relative, ±150 ms. Level change is a whole-file
swap at the cycle boundary, never a runtime mute.

Four bounded one-shot paths exist: a **wrong-zone or outside-window strike** fires
`stroke-<syllable>.wav`, plus the count-in, the UI click, and the personal-best cue. **The accurate
statement is: the music is never triggered per tap; a miss is.** A correct in-window tap plays
nothing — the physical drum supplies it (D77).

### The seams — all designed, none wired

This is the true size of "connect Room to a server", and it is greenfield behind an interface:

| Seam | State |
|---|---|
| `createRoomApi` (`api.ts:103-124`) | **Never called** in app code. What runs is `bundledMockupRoomApi` — a hardcoded single row |
| `catalogForPublishing()` (`api.ts:152-157`) | Throws unconditionally — a deliberate publication tripwire |
| `createCommercePlanner` (`commerce.ts:82-105`) | Imported by **no screen**. Produces intention objects and performs no billing or network call |
| `RemoteRenderSource` (`renderSource.ts:62-71`) | Never instantiated |
| `AccountIdentityPort` (`account.ts:25-32`) | No implementation |
| `factSender` (`AppRuntime.tsx:287`) | Throws by default |
| `docs/SERVER-CONTRACT.md` | 284 lines of **proposed** endpoints. Its own line 5: *"proposed shapes for the missing implementation, not evidence of a deployed API."* Nothing in `src/` references these paths |

Validation inside the seams is genuine — `validatePlayableRows` rejects rows without a server-resolved
grant of `permanent-free`/`owned-course-line`; deep-freeze and partition checks are real. **The design
work for going online is done; none of the implementation is.** Budget 5–7 vibecoding weeks (D93).

### The web export — what was actually proven, and what was not

`react-native-web` 0.21.0 is a real dependency and `expo export --platform web` **has executed**:
`ACCEPTANCE.md:29` records every unauthenticated route reaching the signed-out guard, `/review`
absent from the production route set, and Chrome reporting no uncaught JavaScript error.

**But three caveats decide what that evidence is worth, and D96's rejection makes them live —
INPUT-90 asks what replaces the web room, and this is the evidence about what the web room *is*:**

1. **No web export persists on disk.** Both export scripts write into a `mktemp -d` that is cleaned
   up. There is nothing to inspect or deploy right now.
2. **The committed `dist/` is an Android export, not a web one** — its metadata carries an `android`
   key and no `web` key, and `npm run build` is `expo export --platform android`.
3. **The proof is workstation-shaped.** The walk script drives Chrome on the Windows side through a
   `/mnt/c/...` path, and its own header warns it proves only that the export executes and routes —
   *"nothing about Android, audio, layout, accessibility, lifecycle, input, GPU, or device
   performance."*

**So "the web room works" is true only in the sense that the bundle builds and the routes resolve.**
Nobody has played a session in a browser.

### Sign-in exists and authenticates nothing

`signin.tsx` plus a `DoorAuthContext`, and `_layout.tsx` uses it for real `Stack.Protected` route
guarding. It authenticates nothing and persists nothing — but **the door is structurally wired**,
which makes "add real auth" a swap rather than a greenfield.

### Build and verification machinery — the strongest part of the repo

`scripts/build-room-apk.sh` runs audio gen → `npm run gate` (lint + strict typecheck + jest) → bundle
→ prebuild → assemble → `verify-apk.sh`, which fails the build if `RECORD_AUDIO`,
`CAPTURE_AUDIO_OUTPUT`, `CAMERA` or location permissions appear. **expo-audio's plugin adds
RECORD_AUDIO by default, so that check is load-bearing** — it is red line #4 in CI form.

**Three defects in it, all ratified for repair:**

1. **The tripwire does not fire on the artifact Play requires.** `with-verified-apk.js` finalizes only
   `assemble*`; `bundleRelease`/`bundleDebug` are unmatched, and the verifier scans only
   `outputs/apk` while AABs land in `outputs/bundle/`. (D102)
2. **It is not CI-portable** — it sources the workstation-absolute `$HOME/box/mobile-env.sh`.
3. A stale generated `android/` tree predating the plugin is uncovered until regenerated, and only
   five permission red lines are enforced; `SYSTEM_ALERT_WINDOW` and legacy storage are printed for
   human review, not failed.

**`npm run gate` is red on a bare shell.** `appConfig.test.ts:154` fails with `JAVA_HOME is not set`;
its skip-guard catches the documented WSL Gradle-daemon trap but **not** "no JDK installed". Source
`~/box/mobile-env.sh` first. Any CI runner or fresh clone will otherwise see red and misread it as a
code defect.

### `createFakeRoomAudio()` — a hazard, not a hole

Exported from the production module `engine.ts:107`, imported at module scope by `AppRuntime.tsx:25`,
live as `?? createFakeRoomAudio()` at `:245`, and **in the shipped bundle** (Metro/Hermes does not
tree-shake by default). But `_layout.tsx:70-78` **always** injects the real engine and there is no env
var, debug menu or deep link that substitutes the fake — reaching it requires editing source.

The consequence *if* substituted is real: the fake's `advance()` can mint cycle boundaries, and the
Caderno's defences guard against **exported callers manufacturing evidence**, not against a
substituted engine. **The trust boundary sits at the audio injection point.** (D101)

### Never run on a handset — the named blocker

`ACCEPTANCE.md:29` carries criterion 1 as **"BLOCKED — owner: operator … NOT VERIFIED ON A DEVICE"**.
Everything green is simulation plus a headless-emulator smoke pass on a dated ancestor. No TalkBack,
no iOS, no real-latency, no low-tier evidence.

*(As of 2026-08-05 this is partly discharged: a device test has been run. It returned 0/10 — ledger
row 59, FALSIFIED. See `BUILD-LOG.md`.)*

### Its own documentation — 21 files, two of which matter for what comes next

`apps/opanije-room/docs/` carries 21 documents. Beyond `SERVER-CONTRACT.md`, `ACCEPTANCE.md` and
`GATES.md` cited above: `ARCHITECTURE.md`, `ROUTE-TO-DONE.md`, `SPEC-COVERAGE.md`,
`PRIVACY-NOTES.md`, `DEVICE-NOTES.md`, `SHOOT-LIST.md`, `DEVELOPING.md`.

**Two are directly relevant to the surface redesign (Stage R) and should not be rediscovered:**

- **`docs/MOCKUP-QUESTIONS.md`** — a **12-step script for the session with Junior**. It already exists.
  Stage R needs exactly this and should start from it rather than writing another one.
- **`docs/review/`** — ~11 review documents and a remediation plan from **8 numbered adversarial
  review rounds (r1–r8)**. The app has already been reviewed hard, repeatedly. Anything Stage R is
  about to "discover" about the code should be checked against these first.

**Git recency: this is the active line of work, not an abandoned one** — the last Room commits are
2026-08-04/05.

### 56 `GATE:` markers in shipping code

Non-test `src/` carries 56 `GATE:` markers — founder-, counsel- or Junior-owned open decisions
embedded directly in code: identity/privacy treatment, Apple sign-in equivalence, account-deletion
scope, the tempo ladder, the syllable standard, the free-rhythm partition. Several are load-bearing.
**These are not engineering tasks and no amount of build capacity closes them.** D88 requires one
sweep — close, convert to a `BUILD-LOG` line, or defer with a date — before `GATES.md` freezes.

---

# 2 · `apps/opanije-mobile` — the parked spine

**Do not build against it. Treat it as a reference implementation, not working code.**

Same Expo 57 / RN 0.86 base, version 0.5.0, `com.opanije.course.debug.preview`. Non-test source
**4,439 lines / 32 files**, tests 4,082 lines. 13 routes. It has exactly the plumbing Room lacks:

- **Google OAuth** — a **hand-rolled PKCE flow on `expo-web-browser` + `expo-crypto`**. Not
  `expo-auth-session`, not `@react-native-google-signin`; **neither is in `package.json`, so there is
  no library to swap.** 64-byte verifier, SHA-256 challenge, https-only callback validation pinned to
  host `opanije.com` and exact path, cold/warm return with single-flight dedupe. **The app never holds
  a Google client ID** — it lives server-side.
- **`expo-secure-store` sessions** — `WHEN_UNLOCKED_THIS_DEVICE_ONLY`, 8192-byte guard, schema + TTL
  validation, self-healing delete on corruption, 900 s access / 30-day refresh.
- **A repository factory** — mock / http / production-disabled by config injection. The
  `HttpCourseRepository` is 644 lines: AbortController with 15 s timeout, AES-GCM-encrypted response
  cache with namespace separation, 401 → single-flight refresh → retry, strict `exactKeys` validation.
- **`expo-video`** — a real native player with rate selection, subtitle tracks, resume-seek clamping
  and progress persistence.
- **An iOS project** — the estate's only iOS asset.

**Why it is parked (DN-3, `SITE-SSOT.md:228`):** *"Park native; ship web-only for launch… Do not build
against it or let it accrete scope."* Its CI was reduced to `workflow_dispatch` on 2026-07-31 after
**30 consecutive failures** on "Typecheck the shared application". **`node_modules` does not exist, so
its current status is unverified** — the last commits were typecheck repairs made *before* the
workflow was disabled, and no CI run has exercised them since.

It ships entirely on mocks: `repositoryMode: "mock"`, `apiBaseUrl: null`, `purchaseMode: "disabled"`.

**Under D90 it is a parts donor, then archived — not deleted.** Budget a week per module, not a day,
and if one resists for more than two days write it fresh against Room's conventions (risk #33).

### The salvage verdict, carried forward verbatim because it is a standing instruction

The recon that produced D89 and D90 reached one conclusion above the others, and it is worth having in
front of anyone who is about to redesign a surface:

> **Do not restart. Restarting buys a cleaner history and costs the product.**

Not one base but two complementary ones. **Room is the product** — the only artifact containing the
pedagogical invention, and the only thing Junior has ever had to react to. **Mobile is the plumbing**
Room lacks. The real app is Room's screens on Mobile's spine, and Room already declares that seam.
**The gap is integration work, not invention.**

The honest counter-argument, also carried: Room brings heavy process weight — a gates register, an
authority-pin system, adversarial review rounds, prohibition tests, a source seal. That machinery was
right for a mockup guarding against overclaiming; carried into a shipping app run by one non-engineer
it becomes friction. **Salvage the code and the audio; drop most of the ceremony.**

---

# 3 · The backend — built, deployed, and switched off

**The most under-appreciated asset in the estate. A real paid-course payment rail already exists; it
is dormant, not unbuilt.** Under **D91** this is the backend, forever, absent a founder ruling.

**13 mu-plugins, not 6** — roughly 360 KB / 9,600 lines of PHP, live at
`/var/www/opanije/public_html/wp-content/mu-plugins/`. Sizing WordPress work off "six files"
underestimates by ~2×.

| File | Lines | What |
|---|---|---|
| `opanije-course-access.php` | 1,732 | Entitlement gate + the kill switch |
| `opanije-mobile-api.php` | 1,407 | The versioned `opanije-mobile/v1` REST contract for a native client |
| `opanije-course-catalog.php` | 1,501 | Course/module/lesson hierarchy + wp-admin authoring surface |
| `opanije-course-pay-mercadopago.php` | 1,323 | Mercado Pago — **Pix + card + installments** |
| `opanije-course-app.php` | 1,046 | `/course/` members-area renderer |
| `opanije-course-native-adapters.php` | 765 | Progress with operation-ID idempotency, playback authorization |
| `opanije-course-native-identity.php` | 596 | Google OAuth identity — OAuth only, no passwords |
| `opanije-lang-routing.php` | 448 | EN/PT routing |
| `opanije-course-stream.php` | 187 | Cloudflare Stream signed playback → short-lived same-origin `.m3u8` |
| + `opanije-course-app-preview`, `-shell-copy`, `-native-product-map`, `opanije-mail` | | |

**The whole rail is dormant behind one literal.** `opanije-course-access.php:20` —
`const OPANIJE_COURSE_ACCESS_MODE = 'dormant'` — with the master gate at `:267-269` meaning ~1,460
lines are never even parsed into scope. **Flipping to `'enabled'` is a one-token change that activates
~9,600 lines of PHP, Mercado Pago payment handling, an OAuth server and REST routes that have never
run in production.** That needs its own staged activation, not a deploy.

**Ratified commercial decisions already in place, with their provenance ids** — cite these rather
than re-deciding: rail **Mercado Pago** (Pix + card + installments) and price **R$297** (**SD-42**);
relocated off `/shop` WooCommerce onto the main install with **Schema-2 per-course entitlements and
no Woo order on the rail** (**SD-44**, PRs **#921**/**#925**, merged 2026-07-26); first-party
`/course/` members area with **Google OAuth only, no passwords** (**DN-1**, an anti-piracy ruling);
video on **Cloudflare Stream** (**DN-2**), account provisioned, embed host
`customer-8mfjqskempcr62uf.cloudflarestream.com` — **a CSP entry the app will need**, with the account
id and API token held as secrets in `/var/www/opanije-secrets/main.php`; native parked in favour of
web for launch (**DN-3**); seller of record **CNPJ 41.926.927/0001-34**, blocked on the razão social
plus counsel confirmations before the ToS identity slot can be filled; two products — **1049**
Afro-Bahia primary, **1050** Candomblé Nation upsell.

Room additionally sits behind an explicit **Phase-5 gate**: design freeze → GUI industrial-design
filing → live privacy policy → store submission.

**Two legacy 2023 WooCommerce products priced at 0 USD** share names with the two ratified SKUs —
"Candomblé Nation Percussion Course" and "Afro-Bahia Percussion Course". Anything matching courses by
title will collide with them.

> **The `W1-CL-ENTITLE` per-course-entitlement defect does not exist at HEAD, and remediation
> scheduled against it is wasted work.** `opanije_course_access_subject_holds_course()`
> (`opanije-course-access.php:1511-1546`) keys on `course_key` in a two-level ledger and re-verifies
> the stored key; the product map is a map, not a scalar; there is no hard-coded 297.00 outside
> comments; `OPANIJE_COURSE_ACCESS_MAX_COURSES = 2` and the tests exercise two course keys. It
> existed at `4252113d` and was closed by `94a2a0dd` and `694da476`. Confirm with one live test
> purchase at activation and move on. (D97)

**The contract is shared; the schema is not.** Both PHP and TS read the same fixture
(`scripts/fixtures/mobile-api-v1.json`), but `mobile-api-v1.schema.json` has exactly **one** reader —
the PHP test. The TS side hand-transcribes the shape as `interface WireFixture`. That is a real drift
risk and it is weaker than "both sides test against the schema".

**Two separate WordPress installs.** `public_html/` and `public_html/shop/` are independent full
installs, not a symlinked share — the latter has its own `wp-admin/`, `wp-includes/`, `wp-config.php`.
`opanije-mail.php` is duplicated byte-for-byte. The course rail explicitly compensates
(`opanije-course-access.php:559-575`; `opanije-mobile-api.php:9` bails on non-main installs).
**Any WordPress work must decide which install it targets.**

---

# 4 · opanije.com — what the business looks like today

WordPress 6.9 on the Hetzner VPS behind nginx + Cloudflare, custom first-party theme (React 19 + Vite
+ Tailwind, ACF Pro), Redis object cache, git-managed deploy. **Bilingual by design: English at the
root, Portuguese under `/pt/`**, 18 PT routes live, one PT-only route (`/pt/curso-de-percussao/`).

Very current — main pages modified July 2026, theme files 2–4 Aug 2026, the facts feed regenerates
hourly. The 2026 redesign is what is live. **`/shop` is stale by contrast** — products last touched
2026-07-19, sitemaps dating to Jan 2023.

**28 published pages + 6 journal posts + a `/shop` of 57 published products (65 including drafts).**
*(Three different counts circulate and they measure different things: **57** published shop products,
**48** immersion SKUs — a subset, the camp matrix — and the **50-item** catalog exposed by the facts
feed. They are not inconsistent; they are different sets.)* Legacy pages are still published and
indexed: `/final37/`, `/legacy1/`, `/3323-2/` (all untitled), plus `/camp-options/`, `/plans/`, `/blog/`.

### Three offers; only one is buyable online

1. **The Bahia immersion — the real revenue product.** 48 WooCommerce SKUs priced in **USD**, a matrix
   of `single|couple` × `7|12 days` × `Essential|Bahia Plus|VIP` × `Nov|Dec|Jan|Feb`:

   | Band | Range (USD) |
   |---|---|
   | Single, 7 days | $800 (Nov) – $1,400 (VIP) |
   | Single, 12 days | $1,400 – $2,500 |
   | Couple, 7 days | $1,500 – $2,700 |
   | Couple, 12 days | $2,600 – **$4,800** (VIP) |

   **Essential steps up month by month** (Nov cheapest, Feb dearest); **Plus and VIP are flat across
   months.**
   Season 2026-11-09 → 2027-02-13. `/camp/` itself **shows no prices** — it routes to a Calendly
   consult, WhatsApp, or email capture. Pricing lives only in `/shop`.
2. **The paid online course — R$297, with no working checkout.** Advertised with Pix and card, but
   every primary CTA resolves to a WhatsApp link. **The paid course is sold by hand over WhatsApp.**

   **Be precise about the gateway — the two WordPress installs differ, and it changes what "activate
   Pix" costs.** The **main** install has no site-level Pix gateway; its Mercado Pago rail is the
   *mu-plugin* one in §3, deployed and dormant. **`/shop`** has `woocommerce-mercadopago`
   **installed** and inactive, alongside Stripe, WooPayments and PayPal. So: **a Mercado Pago
   integration already exists on this estate in two different forms and neither is transacting.**
   Nothing needs procuring — this is activation work, not integration work.
3. **The free email course** — one email field → a permanent **Google Classroom** link. Not a drip
   sequence; one link.

**Payment rail on `/shop`:** Stripe, PayPal Payments and BACS enabled, store currency USD.
**Transaction volume: 5 orders total, all `wc-on-hold`, none completed**, spanning 2025-10 to 2026-07.
**12 leads captured.** The site is a fully built storefront through which essentially nothing has sold.
Commerce today is conversational — WhatsApp and a 30-minute Calendly consult.

### Brand and voice

**"Opanijé"** with the acute accent, consistently — named after the *toque* of the orixá Omolú, and
the homepage says so. Tone is warm, concrete, sensory, anti-hype; short declaratives; untranslated
Portuguese (*mestre*, *toque*, *suingue*, *terreiro*, *bloco afro*, *Recôncavo*) carried into the
English as texture. **It sells access to people rather than curriculum**, and it avoids exoticism and
spiritual-tourism framing. Palette `#B7780D` burnt amber on `#F4EEE1` warm bone.

Two audiences split by language: **EN** = culturally curious international travellers buying an
$800–$4,800 immersion; **PT** = Brazilian learners buying a R$297 course. The PT site is not a
translation of a tourism pitch, it is a differently-weighted funnel.

> "Live the rhythm of Bahia where the drums still speak." — homepage hero
> "Opanijé is the rhythm of Omolú. To learn a rhythm from here is to learn the history it carries."
> "Percussion Course with Junior 'Pai de Santo' free, forever."

### The people, as the site presents them

**Adson Vasconcelos dos Santos Junior — "Pai de Santo"**, the face of the teaching brand: began 1996
with Timbalada, played alongside Carlinhos Brown, Marisa Monte and Olodum, toured Europe and Asia,
**trained 1,000+ students**. **His origin is stated three inconsistent ways across the site** — on the
drum at age five (`/about/`), began at fourteen (`/camp/`), career began 1996 (facts feed). **Any app
that syndicates this copy syndicates the contradiction.** Reconcile before reuse.

**Vanderson "Macumbinha"** appears on `/camp/` only — absent from `/about/` and the facts feed. The
site is the only external evidence about him: a percussionist from the **Federação** neighbourhood
who plays with **Timbalada** and teaches through the **Dendê Project**. (Site spelling is
"Macumbinha", not "Macumbinho".) **This matters because INPUT-26 and INPUT-55 are open about him and
this is all the estate has.**

**Kalaban** — named only inside the founder's bio in the facts feed as a long-time collaborator. No
page of his own. A third named person the estate carries almost nothing about.

**Rodolfo Celliert Ogliari — "Meu Velho Visconde"**, founder and operator.

### Reach — the binding gap

| Channel | Observed |
|---|---|
| Instagram `@opanijeworld` | **798 followers** |
| YouTube `@opanijeworld` | **33 subscribers**, 15 videos |
| Facebook | Live; counts behind a login wall |

**No third-party press article surfaced in search.** Searching "Opanijé" mostly returns academic and
liturgical material about the Omolú rhythm itself, plus an unrelated Salvador organisation sharing the
name. **Organic discoverability of the brand is effectively nil.** Press claims on `/press/` (Prêmio
Cultura Viva, IPHAN partnership, Festival Sur le Niger, Brazil–Ghana exchange) are the site's own and
were **not** independently corroborated.

### Deployment debris on the live site — small, real, and cheap to fix

Recorded because each one will otherwise be rediscovered as a surprise:

- **`node_modules` and `package-lock.json` are committed into the live theme directory** — the build
  tree ships to production.
- A **LearnPress LMS** was installed at some point; its options remain in the database though the
  plugin is gone from `wp-content/plugins`.
- A previous theme is retained in-tree as `themes/opanije-backup-20251111-125303`.
- `/shop` is a **separate, older WordPress** with its own theme and 2023 sitemap — a visible seam
  between the 2026 marketing site and the 2023 store.

---

# 5 · Where it can run — the VPS envelope

`root@178.156.171.106`, Hetzner `ubuntu-2gb-ash-1`, Ashburn. **The "2GB" in the hostname is stale.**

| Resource | Actual | Headroom |
|---|---|---|
| RAM | 7.6 GiB | 5.2 GiB available |
| CPU | **2 cores** | load average **0.04** — effectively idle |
| Disk | 38 GB | 28 GB used, **8.6 GB free (77% full)** — the nearest wall |

> **Supersedes a stale figure that survives in four places.** `plan/PRODUCT-GOALS-VNEXT-CONSOLIDATED-V2.md`
> carries **73% full** at four separate lines. **77% / 8.6 GB free, measured 2026-08-05, is the
> current number.** `plan/` is history and was not rewritten; use this page for the VPS envelope.

Running: nginx (80/443), MySQL 8 and Redis (both localhost only), PHP 8.3-FPM, an OmniRoute AI router
on localhost, tailscaled, cron, unattended-upgrades. **Only 22, 80 and 443 are exposed.** Secrets live
at `/var/www/opanije-secrets` (`600`, never in git). Three canonical repo checkouts under
`/root/repos`, plus an orchestration hub at `/root/orchestration` running an unattended worker that
opens PRs and never merges them.

**It could host** a small first-party API for the app behind the existing nginx — auth callbacks,
entitlement checks, a webhook receiver, progress sync. **The rail for exactly that already exists.**

**It could not host** video — lesson video is already correctly ruled onto **Cloudflare Stream**
(DN-2); *8.6 GB free and 2 cores cannot serve HLS*. Nor any Android or iOS build (no JDK, no Android
SDK — which is precisely why the mobile APK was untracked from git), nor a heavy Node runtime
alongside the existing stack. **Treat ~8 GB as the working budget and do not stage media there.**

**The tenancy boundary is closed by decision, with exactly two exceptions.** Cross-tenant paths
between `opanije` and `opanije-outreach` are shut except two ratified read-only feeds: **DR-50** (the
facts feed) and **DR-51** (leads). Anything proposing a third path is proposing a new decision.

**Two sibling repos deploy to the same box** and are separate concerns, not part of the app:
`opanije-outreach` (a zero-dependency PHP + SQLite cold-outreach and lead engine at `/var/www/outreach`,
deliberately held in a fleet-off state, which is its safe state) and `nginx` (source of truth for
`/etc/nginx`, deployed by PR with a guarded `nginx -t` and auto-rollback). **Deploys go through the
VPS, never from a workstation.**

---

# 6 · Assets that exist and would not need building again

**Two things already ship that nothing in the public copy mentions.** A **real PWA** — service worker,
both manifests, 192/512 icons including maskable, separate EN and PT-BR offline pages; the site is
already installable to a home screen. And **a working LMS shell**: `page-templates/course-app.php`
renders library → course detail → lesson player → per-lesson progress, driven by a view model with
`progress_url`, `lesson_url` and a REST nonce — i.e. lesson-delivery and progress endpoints already
exist. **No public route exposes it.**

- **Brand system**, complete and current: correct diacritic, the Omolú etymology as brand story, colour
  tokens, a 20 KB Tailwind config, app icons already cut.
- **Copy**: ~28 pages + 6 long-form articles, **fully bilingual** with a first-party translator layer.
  Course curriculum copy in four blocks. **Legal copy (privacy, terms, cookies) in both languages** —
  though the privacy policy is four years stale and needs replacing before store submission.
- **`/wp-json/opanije/v1/facts`** — a live, hourly-regenerated JSON feed with identity, team bios,
  contacts, the full 50-item catalog with prices, and the season calendar. **An app can consume this
  directly as a config/catalog endpoint with zero new backend work.** Plus `inc/poi-data.php`, 20 KB
  of Salvador points-of-interest data.
- **Imagery**: ~1.1 GB — 1,458 JPG, 917 AVIF, 680 WebP, 281 PNG — already served in modern formats.
- **Video**: 15 professionally cut hero clips in **three codecs (AV1, H.265, H.264) at both horizontal
  and vertical aspect ratios**. The vertical variants are directly usable as mobile onboarding media,
  which is rare to find already done.
- **9 PNG screen captures** of the built app at `/mnt/c/Users/James/room-mockup-screens`, journey-ordered.
  Captures of the built app, not design comps — a visual baseline, not a source of unbuilt design.
- **Build infrastructure**: `~/box/build-apk.sh`, `netrun.sh`, `mobile-env.sh`,
  `scripts/build-room-apk.sh`, `verify-apk.sh`, `~/scratch/room-avd-smoke` (a 10-check emulator
  harness), `~/android-toolchain` (7 GB of working SDK/NDK/JDK).
- **Distribution plumbing**: WhatsApp Business (`+55 71 98184-3221`) with per-page pre-filled UTM-tagged
  templates, a Calendly funnel, Intercom.

---

# 7 · What constrains what can be built

**This section is a synthesis, not an observation** — it is the one part of this page that is not a
measurement. It is carried because it existed nowhere else and a planner needs it before proposing
anything. Each item names the decisions that bind it; those live in `registers/DECISIONS.md` and
`registers/DELTAS.md`.

### The fifteen decisions that most constrain what can be built

1. **G2/D53 — vocalization replaces Western notation product-wide.** No tab, staff, grid or
   piano-roll on any surface; every rhythm representation must be syllables.
2. **D76 — the grading constitution.** Facts may drive sound but never a sentence: sustain visible,
   precision audible, judgment human.
3. **G9 as amended by D79.** Per-strike feedback is binary, generous and audible-only; only a
   post-round aggregate is visible; **accuracy readouts are barred everywhere.**
4. **G10/D60 with D77/D78 — scheduled, not triggered, and no fail state.** An in-window strike keeps
   the part alive, it fades when unfed and returns when fed, and **the drum always sounds.**
5. **E13 and red line #5 — the free tier is permanent.** Every free-tier inclusion is a one-way door.
6. **G13/E20/D63–D64 — the first session runs the whole instrument at its simplest setting**, screen
   drum included, which permanently places the advanced surface on the free tier.
7. **G5/D55 — tap-along is the door and the app never measures the voice.**
8. **R28 (narrowed) — nothing scores the player.** Layer 1 counts facts about your own play and never
   entitles; Layer 2 is human attestation only.
9. **A5 with D44 and R59 — Junior alone confers standing**, and the play layer must be a resettable
   subsystem that never writes into Caderno tables.
10. **G14/D65 — the stroke set is fixed at three zones (hand) and two (stick)**, labelled with
    Junior's syllables and never English words. **This bounds the screen drum's entire interaction
    vocabulary — and therefore bounds Stage R.**
11. **G25/D73 with E17 — the commons is free, scarcity is priced.**
12. **G15/D66 — no engagement mechanics on the free tier in Release 1**, with the
    extrinsic-vs-legibility reading unconfirmed at INPUT-84.
13. **G16/D67 with D80 — the count-in fires at every session start**, and the celebration object is
    the new personal best, expressed in sound and light, not voice.
14. **G1/D52 with E8 — the app opens rooms but never moves the student into one**, and parts stay
    freely switchable in both directions at any time.
15. **G6 with red line #1 — the screen drum cannot ship unshown to Junior.** G26 confirms it may
    resemble a real drum seen from above; mockup assent (INPUT-69) is still outstanding.

**Two open hazards carried with them.** **C23** — E2's named on-screen presence was voided by D38
(the battery is Junior alone, layered) yet the presence lamp (E21) builds on it; whoever answers
INPUT-88/INPUT-60 decides whether the lamp is one slot or the screen names musicians. **E15** stands
while its justification — that Release 1 sells nothing — was removed by D37.

### What is blocked on whom

Reproduced because it is the fastest way to see that most open work waits on **one of two people**,
not on engineering.

| Blocked work | Waits on | Human |
|---|---|---|
| Capture Day | INPUT-21, -22, -23, -57, -59, -70, -74, -77, -80; R82; R88 | Junior + founder |
| Those assets surviving at all | INPUT-44 escrow (risk #16, and D98 deferred it) | Founder |
| R1's shape and its largest engineering item | INPUT-41; rows 27, 32; C17 | Junior (+ Vanderson) |
| The echo loop's design | INPUT-78, then assent at INPUT-79 | Junior |
| Shipping the screen drum (Charter §9 item 10) | INPUT-69, shown as a working object | Junior |
| The usability pilot → rows 46, 48, 49, 50 | INPUT-72 | Junior |
| The permanent free tier | INPUT-80 *(answered 2026-08-05)*, -52, -53 | Founder + Junior |
| The play screen; C23 | INPUT-60 / INPUT-88 | Founder |
| The grading layer at the free door | INPUT-84 | Founder |
| Any filing or public use of the name | INPUT-32 first, then -31, -35 | Junior, then counsel |
| Both store submissions | INPUT-39; INPUT-40 | Counsel; founder |
| Publishing the standard | INPUT-83, -67 | Founder + counsel; Junior |
| Any share surface | INPUT-71 | Founder + counsel |
| Every play-layer string | INPUT-81 | Founder |
| R1 shipping any consented material | The cross-system takedown (row 30, FALSIFIED) | Build side |

**One finding sizes the whole standard workstream (D82/D85), and it is easy to miss:** *"No symbol
table, grammar, file format, or machine encoding exists anywhere in the estate."* The syllable
inventory is defined only by Junior's recorded performance. Where the publishable *structure* ends
and the never-publishable *pedagogical sequence* begins is **undrawn** — INPUT-83's first job. D85
froze publication, which is why this is background rather than urgent.

---

# 8 · The gaps that bind

Ordered by how much they constrain a plan.

**1 · There is no audience.** ~800 Instagram followers, 33 YouTube subscribers, 12 leads, 5 orders none
completed, no mailing list of meaningful size, no organic search presence. **An app would launch to
essentially no installed audience. Any plan that assumes an existing base to convert is assuming
something that is not there.**

**2 · There is no owned lesson media.** The uploads directory contains **zero instructional video or
audio** — only marketing teasers. The actual teaching content lives on YouTube and Google Classroom,
third-party platforms with no API contract here. A percussion app needs isolated tempo-mapped stems
per instrument and **none of it exists as an owned asset.**

**3 · No user accounts anywhere the student can reach.** The main site has no login, no membership, no
student area, no purchaser→content entitlement link. The `course-app` template has progress endpoints
but nothing establishes *who* a user is.

**4 · No mailing-list infrastructure.** No Mailchimp/ConvertKit/Klaviyo/Brevo. Email capture writes to
a WP custom post type and fires `wp_mail`. There is no drip engine, no segmentation, and no list to
import.

**5 · The two currencies do not meet.** The store transacts USD; the course is priced BRL. There is no
multi-currency handling and the site has never had to resolve it.

**6 · No structured curriculum data.** Course "modules" exist as marketing prose in PHP templates, not
as data — no lesson list, no ordering, no durations, no rhythm/instrument taxonomy. The `course-app`
view model expects such data; nothing populates it.

**7 · No analytics on learning.** Site Kit and Jetpack track pageviews. Nothing measures practice,
retention or completion — the metrics a learning app is judged on.

**8 · The repository is GPL v3**, repo-wide (`LICENSE.txt`), covering both apps, with no per-directory
override. For a paid closed-source app distributed through app stores this is a first-order question
that must be settled **before** submission. **Nobody in 145,680 words of estate noticed it.**
(INPUT-85, risk #31.)

**9 · No app-store presence.** No developer accounts, bundle identifiers, listings, screenshots or
privacy-nutrition disclosures.

---

# 9 · Capacity — what is cheap, expensive, and impossible

The founder is not a software engineer and builds through Claude Code alone.

**Cheap.** More of what exists — another screen, rhythm, string, test; the patterns are established
and covered. Copy and i18n. Anything local-only (AsyncStorage: journal, streaks, preferences,
offline). Building and inspecting an APK — the script, the netrun workaround, the permission verifier
and the emulator harness all exist and are proven. Regenerating audio from spec.

**Expensive.** Anything requiring a device in a human's hands — **Claude cannot do this at all, and it
is the single largest verification debt.** Activating the payment rail (real money, exact-SHA deploy,
blocked on razão social + counsel). Joining Room's UI to Mobile's spine — genuine integration
engineering across two codebases with auth and persistence in the middle. Video. Store submission.

**Infeasible.** **iOS** — no macOS, no Xcode, no signing; not reachable from this machine at any
effort level. **Android-first is not a preference, it is the only option.** Real-device QA at scale.
Anything needing a backend team (streaming infra, CDN pipeline, DRM, server-side receipt validation).
**Mic capture or AI grading of playing** — the build actively forbids `RECORD_AUDIO` and fails if it
appears; adding it is a new product with new privacy obligations, not a feature.

**The honest framing:** the founder can go remarkably far building *forward* from what exists, and will
hit a wall the moment the work is *activation* (money, legal, store) or *verification on real
hardware*. Front-load the cheap column; schedule the expensive column around founder-time.

---

# 10 · Nine claims that were wrong — recorded so nobody re-derives them

A design plan written from the estate alone made seventeen load-bearing claims about the code. **Nine
were wrong or overstated.** They are listed here because the cost of each is real work scheduled
against a thing that is not true.

| # | The claim | What is actually true |
|---|---|---|
| 1 | A live per-course entitlement revenue leak exists | **FALSE at HEAD.** Fixed two commits after it was introduced. *Any remediation scheduled against this is wasted work* |
| 2 | PHP and TS both test against the shared JSON schema | Only the **fixture** is shared. The schema has one reader (PHP); TS hand-transcribes the shape. A real drift risk hidden by a stronger-sounding claim |
| 3 | ~493 tests, ~24,000 lines of source | **621 tests.** 24k lines counts test code — implementation is **12,443**, tests 11,623 |
| 4 | `createFakeRoomAudio()` gives a path to forge a Caderno entry | True of the **architecture**, false of the **shipped app** — no runtime path selects it; it takes a source edit |
| 5 | Audio is "scheduled, not triggered" | Too absolute. A **missed or wrong-zone strike** genuinely triggers a sample. The music is never triggered per tap; a miss is |
| 6 | The Google OAuth uses `expo-auth-session` / `@react-native-google-signin` | **Neither is in `package.json`.** It is hand-rolled PKCE on `expo-web-browser` + `expo-crypto` — there is no library to swap |
| 7 | The fade is a decay model that thins when unfed | **Binary on/off**, per cycle, recovering the next one. No curve, **no cross-session decay at all**, and the real feeding measure is computed then discarded |
| 8 | Six mu-plugins | **Thirteen.** ~2× the WordPress surface |
| 9 | Room is "fully local" | Runtime behaviour is, but a sign-in screen and real route guarding exist — "add auth" is a swap, not a greenfield |

**The lesson, which is worth more than the list:** the estate's confidence about the code was
uncorrelated with the code. Verify before scheduling.

---

# 11 · What could not be reached

Recorded rather than glossed, because an unmarked gap reads as a finding.

- **YouTube video titles and view counts** — the channel's video grid is JavaScript-rendered and no
  `channelId` was exposed in the served HTML. Subscriber (33) and video (15) counts *were* recovered.
- **Facebook follower counts** — behind a login wall.
- **Instagram post count** — not exposed; followers (798) and following (153) were.
- **`/press/` claims** — taken from the site's own page, **not** independently corroborated.
- **`apps/opanije-mobile`'s current typecheck/test status** — `node_modules` absent, CI disabled. Its
  state is genuinely unknown, not assumed good.
- **The WordPress database** — queried only via read-only `wp-cli` counts. No lead or customer personal
  data was read or recorded.

---

*As-built record, 2026-08-05. Compacted from the recon and verification set of the same date; the
originals are recoverable from git history at `e38917a`. Under D88 this file is not a register and
takes no numbered rows — corrections to it are one line in `BUILD-LOG.md`.*
