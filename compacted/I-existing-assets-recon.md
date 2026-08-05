# I — Existing assets recon

Read-only survey, 2026-08-05. Nothing was modified anywhere.

---

## Repo inventory

| Path | What it is | Stack | Size | Live? | Deploy target |
|---|---|---|---|---|---|
| `/home/james/work/opanije` | The estate monorepo: WordPress main site + WooCommerce `/shop`, **plus both mobile apps under `apps/`** | WordPress (2 independent installs) + WooCommerce; custom Opanijé theme (parent) + `opanije-shop` child; Bootstrap/React/Tailwind, Vite build; PHP 8.3-FPM | 21,544 tracked files, 395 MB packfile | **YES — real site, real payments** | `/var/www/opanije/public_html` (2.1 GB live) and its `shop/` subtree, via GitHub Actions on merge to `main` |
| `/home/james/work/opanije-outreach` | Outreach CRM / "cultural-producer engine" — cold-email loop, lead vetting, EPK/quote/invoice *preparation* (never transacts), two markets EN-GLOBAL / PT-BR | Zero-dependency PHP 8.3 + SQLite (no Composer, no Docker); Gmail API for all mail egress; Node 22 only for dashboard checks | 395 tracked files, 44 MB | **YES**, but the legacy conductor is deliberately **disabled** ("fleet hold"); fleet-off is the safe state | `/var/www/outreach` (public root `/var/www/outreach/public`), OS user `outreach-svc`, FPM socket `php8.3-fpm-outreach.sock` |
| `/home/james/work/nginx` | Source of truth for `/etc/nginx` — edge/TLS for main, shop, CRM, outreach, n8n vhosts. FastCGI micro-caching, Brotli/gzip, HTTP/3, rate limiting, security headers | nginx config | 97 tracked files, 878 KB | **YES** | `/etc/nginx` via `.github/workflows/deploy.yml` — rsync, backup, guarded `nginx -t`, auto-rollback, graceful reload |
| `/home/james/opanije-gate4` | **Not a separate repo** — a git *worktree* of `opanije` (gitdir on `/mnt/i/opanije-pr1081`), branch `fix/room-guided-progression`, HEAD `4dde6752` dated **2026-08-05** (today). Working tree clean. | — | — | No | — |

All three ship by their own branch + PR. The canonical checkouts live on the VPS at `/root/repos/{opanije,nginx,opanije-outreach}`; the local `~/work` clones are convenience mirrors. **Deploys go through the VPS, never from here.** Cross-tenant paths between `opanije` and `opanije-outreach` are closed by decision except two ratified read-only feeds (DR-50 facts, DR-51 leads).

---

## The prior mobile app attempt(s)

There are **two**, not one. This matters — the recon prompt assumed one.

### A. `apps/opanije-room` — "Opanijé Room", the mockup (in `opanije-gate4`, and on `main`)

**Framework.** Expo SDK **57.0.7**, React Native **0.86.0**, React **19.2.3**, expo-router 57, TypeScript **6.0.3**, New Architecture enabled. Node pinned 22.21.0, npm 11.6.4. Android package `com.opanije.room.mockup`, version 0.1.0.

**Dependencies (deliberately small):** expo-audio, expo-font (+ Google Fonts Lato/Montserrat), expo-localization, expo-screen-orientation, expo-keep-awake, AsyncStorage, gesture-handler, safe-area-context, screens, react-native-web. Custom config plugin `./plugins/with-verified-apk`. **No video, no networking library, no auth SDK, no payments SDK.**

**Size.** 144 TS/TSX files, **24,066 lines**. **493 test cases** across ~40 suites. 35 MB of assets, including **72 generated `.wav` files** (synthetic, deliberately non-vocal placeholders regenerated from `scripts/audio-spec.json`).

**Screens implemented** (13 routes, PT/EN bilingual throughout):

| Route | State |
|---|---|
| `/` presentation | Works. Explains the ~5-min session, offers PT/EN, silent by design. |
| `/signin` | **Fake.** Button looks like Google; grants a local session only. No real OAuth. |
| `/intention` | Stores morning/afternoon/evening locally. **Schedules no actual notification.** |
| `/welcome` | Placeholder for Junior's future talking-head. Synthetic image, click sound only. **No video, no real voice.** |
| `/choose-part` | Works. One placeholder rhythm ("O toque livre"), Hand vs Stick, 3 provisional tempos. |
| `/room` | **The core loop, and it works.** Auto-conducts listen → together → your turn → together again → beat. Live switching of round/tempo/part. App keeps time; **it does not listen to or grade the user.** |
| `/drum` | Works. Rotates to landscape, tappable zones with syllables, a lever changes zone count. **No mic, no correction, no scoring.** |
| `/closing` | Works. Session facts only; optional streak/personal-best, no ranking. |
| `/ending` | Works. Only appears after the final round. PT = invitation to next session; EN can open Salvador contact. **No price, no checkout.** |
| `/caderno` | Works. Read-only automatic journal — rhythm, part, timestamp, persisted on device. |
| `/home` | Works. Today's session, Caderno preview, rhythm map in demo mode. |
| `/review`, `/past-the-door` | Hidden demo surfaces, gated behind a dev/demo build flag. |

**What works:** navigation, playback of local audio, the screen drum, on-device persistence, PT/EN i18n, adaptive layout/large-text/reduced-motion handling, a takedown drill, a commerce *seam* (types only).

**What does not:** login (no identity provider), backend/catalog (no server at all), notifications, production media, video, Pix, store billing, receipt validation, CDN/object storage, scoring/mic.

**Build story — this is the strongest part.** `scripts/build-room-apk.sh` runs audio gen → lint/typecheck/jest gate → bundle → prebuild → assemble → **`verify-apk.sh`**, which fails the build if RECORD_AUDIO / camera / location permissions appear (expo-audio's plugin adds RECORD_AUDIO by default, so this check is load-bearing). A **~98 MB release APK exists on disk** (`android/app/build/outputs/apk/release/app-release.apk`, built 2026-08-04), standalone, two-ABI (`arm64-v8a,x86_64`), debug-key signed for private sideloading. It has been run in a **bounded headless emulator regression** (API-36 x86_64) and the web export has **executed in headless Chrome** across every route. Honest gaps, documented by the project itself: never run on a real handset, nobody has heard the audio, no TalkBack, no iOS, no real-latency or low-tier evidence.

**Git recency: today.** Last five room commits are 2026-08-04/05. This is the currently-active line of work, not an abandoned one. It has been through **8 numbered adversarial review rounds** (r1–r8) with a `docs/review/` folder of ~11 review documents and a remediation plan.

**Documentation:** 21 docs including `ARCHITECTURE.md`, `SERVER-CONTRACT.md` (the production services assumed but not built), `GATES.md` (the single operative authority index, with `GATE:` markers in code naming who owns each unanswered question), `ROUTE-TO-DONE.md`, `ACCEPTANCE.md`, `SPEC-COVERAGE.md`, `PRIVACY-NOTES.md`, `MOCKUP-QUESTIONS.md`.

### B. `apps/opanije-mobile` — "Opanijé Native Preview" (the *real* app skeleton, parked)

Same Expo 57 / RN 0.86 / React 19 base, version **0.5.0**, package `com.opanije.course.debug.preview`. **61 files, 8,521 lines.** Crucially it has the pieces Room lacks: `expo-secure-store` (Keystore/Keychain session storage), `expo-web-browser` + a full **OAuth adapter** with a transaction store, `expo-video` (native player), `expo-crypto`, `expo-network`, WebView, Reanimated, **and both an iOS and an Android native project**.

Screens: index, sign-in, auth-return, library, editorial, continue, account, checkout-return, offline, service-error. Data layer is a clean **repository abstraction** — `mock-repository` / `http-repository` / `repository-factory` — so mock vs production is a config injection, plus a `source-seal` integrity mechanism and a design-token theme layer.

**Status: deliberately parked.** Operator decision **DN-3 (2026-07-22): "Park native; ship web-only for launch."** It ships dormant/disabled (mock repository, purchases off). Last commits 2026-07-30. Its committed APK was **untracked on 2026-07-29** because the source-seal contract could never be satisfied — the estate box has no JDK and no Android SDK. That constraint has since been removed on *this* workstation (see Infrastructure).

### Verdict: SALVAGEABLE — and restarting would be an expensive mistake

Not one base, but **two complementary ones**, and the right move is to combine rather than restart.

- **`opanije-room` is the product, and it is real.** It is the only artifact that contains the actual pedagogical invention — the conducted listen/echo loop, the screen drum, the Caderno, the bilingual voice, the whole feel. That is 24k lines, 493 tests, 8 review rounds, and a working APK. It is also the only place the founder's domain expert (Junior) has anything to react to. Throwing it away throws away the product, not the code.
- **`opanije-mobile` is the plumbing**, and it is exactly the plumbing Room is missing: OAuth, SecureStore, video, a repository seam, an iOS project, a checkout return path. It is 8.5k lines of the boring, hard, easy-to-get-wrong parts.
- **The real app is Room's screens on Mobile's spine.** Room already declares that seam: `src/data/api.ts`, `src/data/commerce.ts` (types `'web-pix' | 'in-app-store'` with a pure intention planner and no integration), `src/data/catalogSchema.ts`, and `docs/SERVER-CONTRACT.md`. The gap is integration work, not invention.
- **The honest counter-argument:** Room carries heavy process weight — a GATES register, an authority-pin system, adversarial review rounds, prohibition tests, a source-seal. That machinery was appropriate for a mockup guarding against overclaiming; carried into a shipping app run by one non-engineer it becomes friction. **Salvage the code and the audio; drop most of the ceremony.** Room's own README already argues this ("O estado atual é pequeno de propósito", the KISS framing added today).
- **Two things must be fixed before ship, both already written down by the project:** (1) `createFakeRoomAudio()` is importable from production code and could forge a permanent Caderno entry; (2) the APK permission verifier only covers `assemble*` tasks, so an AAB or a rename escapes it — and AAB is what Play Store requires.

**Do not restart.** Restarting buys a cleaner history and costs the product.

---

## The mockup screens

`/mnt/c/Users/James/room-mockup-screens` — **9 PNG files, 776 KB total**, all dated 2026-08-03, numbered in journey order:

| File | Size | Maps to route |
|---|---|---|
| `01-presentation.png` | 87 KB | `/` |
| `02-signin.png` | 60 KB | `/signin` |
| `03-intention.png` | 85 KB | `/intention` |
| `04-home.png` | 87 KB | `/home` |
| `05-room.png` | 94 KB | `/room` |
| `06-tap-door.png` | 96 KB | `/past-the-door` |
| `07-drum.png` | 71 KB | `/drum` |
| `08-caderno.png` | 94 KB | `/caderno` |
| `09-drum.png` → `09-ending.png` | 103 KB | `/ending` |

These correspond 1:1 to implemented routes, so they are almost certainly **captures of the built app**, not design comps drawn ahead of it. Useful as a visual baseline and for showing Junior/testers; not a source of unbuilt design.

---

## Infrastructure

### The VPS (`ssh vps` → `root@178.156.171.106`, Hetzner `ubuntu-2gb-ash-1`, Ashburn)

**The "2GB" in the hostname is stale — it has been resized.** Measured today:

| Resource | Actual | Headroom |
|---|---|---|
| RAM | **7.6 GiB** total | 2.4 GiB used, **5.2 GiB available**, 5.4 GiB in cache |
| Swap | 2.0 GiB | essentially untouched (512 KiB) |
| CPU | **2 cores** | load average **0.04** — effectively idle |
| Disk | 38 GB `/dev/sda1` | 28 GB used, **8.6 GB free (77% full)** |
| Uptime | 2 days 14 h | — |

**Running:** nginx (80/443, IPv4+IPv6), MySQL 8 (localhost only), PHP 8.3-FPM, Redis (localhost), an "OmniRoute AI Router" on localhost ports 20128/20131/20132, tailscaled, cron, atd, unattended-upgrades, qemu-guest-agent. Only **22, 80, 443** are exposed.

**Deployed:** `/var/www/opanije/public_html` (2.1 GB — main WP + `/shop` WooCommerce), `/var/www/outreach`, `/var/www/letsencrypt`, `/var/www/opanije-secrets` (secrets live here, `www-data:www-data 600`, never in git), `/etc/nginx`. Three canonical repo checkouts under `/root/repos`, plus an orchestration hub at `/root/orchestration` (a git repo with **no remote** — local history only) running an unattended `loop.py` that opens PRs by itself and never merges them.

**Could host:** a small first-party API for the app (PHP-FPM behind the existing nginx, SQLite or the existing MySQL), auth callbacks, entitlement checks, a webhook receiver, progress sync. The rail for exactly this already exists (see below).

**Could NOT host:** video. Lesson video is already ruled out onto **Cloudflare Stream** (DN-2), correctly — 8.6 GB free and 2 cores cannot serve HLS. Also could not host: any Android/iOS build (no JDK, no Android SDK — this is precisely why the mobile APK was untracked from git), a heavy Node runtime alongside the existing stack, or anything memory-hungry. Disk at 77% is the nearest wall; treat ~8 GB as the working budget and do not stage media there.

### The Windows/WSL dev machine

**Android builds work here, and this is a hard-won asset.** `~/box/build-apk.sh` produces a debug APK in ~6 min cold / ~20 s incremental, running jest first. Toolchain at `~/android-toolchain` (~7 GB): Temurin JDK 17.0.19+10, Node 22.21.0, SDK platforms 35+36, build-tools 35.0.0+36.0.0, platform-tools r37, **NDK 27.1.12297006**, CMake 3.22.1. Env in `~/box/mobile-env.sh`.

**The critical trap, already solved:** loopback delivery to JVM listening sockets is broken on this WSL guest, so Gradle cannot reach its own daemon. `wsl --shutdown` does not fix it — it is a standing property. The fix is **`~/box/netrun.sh`**, which runs the build in a private netns with a `slirp4netns` uplink. The **Android emulator has the same problem** and must run inside the same netrun namespace (adb too); it boots in ~50 s there. A reusable 10-check emulator smoke harness exists at `~/scratch/room-avd-smoke`.

Three build traps to respect: never create `android/local.properties` (breaks the source seal); pin `ANDROID_USER_HOME`; clear `$GRADLE_USER_HOME/daemon` between runs.

**Capacity limits.** Disk is fine — `/` (WSL ext4, now backed by F:) has ~899 GB, `/mnt/f` ~135 GB, but they are the **same physical disk**, so filling one starves the other. **RAM is the binding constraint: 17.56 GiB guest ceiling, 4 GiB swap.** `claude` runs under a systemd scope capped at `MemoryMax=12G`, with `earlyoom` as a VM-wide backstop. Subagents run **in-process**, so a fan-out workflow is bounded by this ceiling — one Workflow at a time, prefer pipelines over parallel barriers. A 43-agent overlap OOMed the box on 2026-07-31 and lost ~58 minutes of work.

**No iOS path exists.** `opanije-mobile` has an iOS project, but macOS/Xcode signing and physical-iPhone evidence are external gates. `opanije-room` has no iOS script at all. **iOS is not reachable from this machine.**

---

## Commerce integration that exists

This is the most under-appreciated asset in the estate. **A real, merged, deployed paid-course payment rail already exists — it is switched off, not unbuilt.**

**Live on the VPS**, in `/var/www/opanije/public_html/wp-content/mu-plugins/`:

| File | Size | What it is |
|---|---|---|
| `opanije-course-pay-mercadopago.php` | **49.7 KB** | First-party Mercado Pago adapter — **Pix + card + installments** |
| `opanije-course-access.php` | 60 KB | Entitlement gate. `const OPANIJE_COURSE_ACCESS_MODE = 'dormant'` — **one git-owned literal, three states (`dormant` / `enabled` / `fail-closed`)** |
| `opanije-course-native-identity.php` | 26.6 KB | Google OAuth identity (OAuth-only, no passwords — anti-piracy ruling) |
| `opanije-course-catalog.php` | 56.4 KB | Course/module/lesson hierarchy + wp-admin authoring surface |
| `opanije-course-app.php` | 42.6 KB | `/course/` members-area renderer |
| `opanije-mobile-api.php` | — | **Versioned `opanije-mobile/v1` REST contract for a native client** — bootstrap, EN/PT catalog DTOs, account/entitlement/playback/progress, native OAuth bridge, one-time checkout handoff |
| `opanije-course-native-adapters.php` | 30 KB | Progress records with operation-ID idempotency, playback authorization |
| `opanije-course-native-product-map.php` | 2 KB | Course-key → product-ID validator |
| `opanije-course-stream.php` | 6.5 KB | Cloudflare Stream signed-playback adapter → short-lived same-origin `/stream/<code>.m3u8` handoff |

Plus `scripts/fixtures/mobile-api-v1.json` and a **closed Draft 2020-12 JSON schema** (`mobile-api-v1.schema.json`, 17 KB) that the PHP fixture and the TypeScript repository both execute against.

**Ratified commercial decisions already made** (`docs/SITE-SSOT.md`, SD-42 / SD-44 / DN-1 / DN-2 / DN-3):
- Rail: **Mercado Pago, Pix + card + installments**. Price **R$297**. Relocated OFF `/shop` WooCommerce onto the **main install** (SD-44, PRs #921/#925, merged 2026-07-26). Schema-2 per-course entitlements, no Woo order on the rail.
- Delivery: first-party `/course/` members area, **Google OAuth only, no passwords**.
- Video: **Cloudflare Stream ratified**, account provisioned, embed host `customer-8mfjqskempcr62uf.cloudflarestream.com` (public); account ID and API token are secrets in `/var/www/opanije-secrets/main.php`.
- Seller of record: **CNPJ 41.926.927/0001-34** (operator, 2026-07-26). Blocked on the razão social + counsel confirmations before the ToS identity slot can be filled.
- Two products: **1049 Afro-Bahia primary**, **1050 Candomblé Nation as upsell**. **Known build gap `W1-CL-ENTITLE` (Risk-C):** the merged rail is single-product *by construction* — scalar product ID, whole-library boolean entitlement, cart pinned to one row at hard-coded 297.00. **Wiring a second product to the same constant would grant the whole library for one purchase.** 1050 must not be published until per-course grants are proven.

**Separately, live WooCommerce on `/shop`** (real payments, real orders) has installed: `woocommerce-gateway-stripe`, `checkout-plugins-stripe-woo`, `woocommerce-mercadopago`, `woocommerce-payments`, `woocommerce-paypal-payments`, plus `woo-cart-abandonment-recovery`, Facebook/TikTok/Pinterest/Google feeds. This is the tourism/immersion commerce, on the USD base currency — **not** the course rail.

**In the apps:** nothing wired. `opanije-room/src/data/commerce.ts` is a **pure type-level seam** — `CommerceRail = 'web-pix' | 'in-app-store'`, a `CommercePlanner` that produces `CheckoutIntention` / `ConsultationIntention` objects and performs no billing or network call. `opanije-mobile` has `src/platform/purchase.ts` and a `/checkout-return` route, both disabled by config. **No Hotmart, no Kiwify anywhere.**

**Net:** the hard commerce thinking, the legal identity work, the gateway choice, the API contract, and roughly 270 KB of working PHP are already done. What is missing is activation, real-payment evidence, per-course entitlements, and a client that calls it.

---

## Skills and capacity reality

The founder is not a software engineer and will build through Claude Code alone. Stated plainly:

**Cheap.**
- *More of what already exists.* Another screen in Room, another rhythm, another PT/EN string, another test — the patterns are established, typed, and covered by 493 tests. This is the cheapest work available and it should be the default shape of any plan.
- *Copy, i18n, and content changes.* Bilingual infrastructure is built; adding or fixing text is near-free.
- *Local-only features.* Anything that reads and writes AsyncStorage and needs no server: journal, streaks, preferences, offline behaviour.
- *Building and inspecting an APK.* The script, the netrun workaround, the permission verifier and the emulator harness all exist and are proven. What was a multi-day trap is now one command.
- *Audio asset generation.* `npm run audio` regenerates all 72 placeholder renders from a spec.
- *Reading and reasoning across the estate.* The documentation is unusually thorough — SSOT registers, decision logs, gate registers, architecture docs. Claude can orient quickly here, which is exactly what a non-engineer needs.

**Expensive.**
- *Anything requiring a device in a human's hands.* Nobody has heard the app's audio. No handset run, no TalkBack, no real latency. Claude cannot do this at all — it is founder-time, and it is the single largest verification debt.
- *Activating the payment rail.* Flipping `OPANIJE_COURSE_ACCESS_MODE` to `enabled` requires exact-SHA deploy, real-payment evidence, and touches live money. Correctly operator-gated. Also blocked on the razão social and counsel confirmations.
- *`W1-CL-ENTITLE` — per-course entitlements.* Explicitly Risk-C, touches money and access, and getting it wrong gives the library away.
- *Joining Room's UI to Mobile's spine.* Genuine integration engineering across two codebases, with auth and persistence in the middle. Doable via Claude Code, but it will take several careful sessions, not one.
- *Video.* Even the modest KISS experiment Room's README proposes (one approved clip + a player + captions) needs Junior's authorized footage, Cloudflare Stream wiring, and CSP changes.
- *Store submission.* Signing identity, privacy policy, store listing, review. Room additionally sits behind an explicit Phase-5 gate: design freeze → GUI industrial-design filing → live privacy policy → submission.

**Infeasible.**
- **iOS.** No macOS, no Xcode, no signing. Not reachable from this machine at any effort level. Android-first is not a preference, it is the only option.
- **Real-device QA at scale.** One founder, presumably one or two phones. Low-tier Android performance, speaker sound, and real-world latency will remain untested.
- **Anything needing a real backend team.** Streaming infrastructure, a CDN pipeline, DRM, server-side receipt validation across both stores, an abuse/takedown system — `docs/SERVER-CONTRACT.md` lists these as assumed-but-not-implemented, and they stay that way.
- **Mic capture / AI grading of playing.** Room's build actively *forbids* RECORD_AUDIO and fails the build if it appears. Adding listening-and-scoring is a new product with new privacy obligations, not a feature.
- **Large parallel agent fan-outs.** RAM-bounded, and a violation kills the whole session. Sequential is not conservatism here, it is the machine's actual limit.

**The honest framing:** the founder can go remarkably far building *forward* from what exists, and will hit a wall the moment the work is *activation* (money, legal, store) or *verification on real hardware*. A plan should front-load the cheap column and schedule the expensive column around founder-time, not agent-time.

---

## Reusable asset list

Things that already exist and would not need building again:

**Product / app**
1. `apps/opanije-room` — 13 bilingual screens, 24k lines, 493 tests. The conducted listen/echo session loop, the landscape screen drum with syllable zones, the Caderno journal, the closing summary, the final invitation.
2. `apps/opanije-mobile` — OAuth adapter + transaction store, SecureStore session handling, `expo-video` native player, mock/http repository factory, design-token theme layer, an **iOS project** (for whenever a Mac exists), `/checkout-return` and `/auth-return` deep-link routes, source-seal integrity check.
3. 72 generated `.wav` audio renders + `AUTHORED-TIMING.json` (exact cycle/strike timing) + `GENERATED.json` inventory, all regenerable from `scripts/audio-spec.json`.
4. 9 PNG screen captures at `/mnt/c/Users/James/room-mockup-screens`.
5. Adaptive-layout / large-text / reduced-motion handling, already tested.
6. `src/data/commerce.ts`, `src/data/api.ts`, `src/data/catalogSchema.ts` — the client-side seams, typed and tested, waiting for an implementation.

**Build & test infrastructure**
7. `~/box/build-apk.sh` + `~/box/netrun.sh` + `~/box/mobile-env.sh` — the working Android build, with the WSL loopback trap already solved.
8. `scripts/build-room-apk.sh`, `scripts/verify-apk.sh` (permission enforcement), `plugins/with-verified-apk` (Gradle finalizer).
9. `~/scratch/room-avd-smoke` — reusable 10-check emulator harness; `scripts/walk-web-routes.sh` and `capture-web-widths.sh` for browser smoke tests.
10. `npm run gate` — lint + strict typecheck + jest, one command.
11. `~/android-toolchain` — 7 GB of installed, working SDK/NDK/JDK.

**Backend / commerce**
12. The entire main-install course rail: Mercado Pago adapter (Pix/card/installments), Google OAuth identity, entitlement gate with a three-state kill switch, course catalog **with a wp-admin authoring surface**, `/course/` renderer, Cloudflare Stream signed-playback adapter. ~270 KB of merged, deployed PHP.
13. `opanije-mobile-api.php` — a versioned REST contract designed for exactly this native client, with `mobile-api-v1.json` fixtures and a closed JSON schema both sides test against.
14. Live WooCommerce with Stripe, Mercado Pago, PayPal and WooPayments installed (tourism/immersion side).
15. Cloudflare Stream account, provisioned, embed host known.

**Decisions and documents (worth more than they look)**
16. Ratified: gateway, price (R$297), delivery surface, OAuth-only login, video provider, seller-of-record CNPJ, two-product structure, park-native-ship-web-first.
17. `docs/SERVER-CONTRACT.md` — a written specification of every production service the app assumes.
18. `docs/GATES.md` + in-code `GATE:` markers — every unanswered question, its owner, and the safe temporary behaviour.
19. `docs/MOCKUP-QUESTIONS.md` — the 12-step script for the session with Junior.
20. `docs/review/` — 11 review documents and a remediation plan from 8 adversarial rounds.

**Estate infrastructure**
21. Production VPS with nginx/MySQL/Redis/PHP-8.3-FPM, TLS, HTTP/3, micro-caching, CI/CD with auto-rollback, and ~5 GB RAM headroom on an idle 2-core box.
22. The outreach CRM — separate concern, but a working lead/contact engine if the app ever needs a marketing arm.
