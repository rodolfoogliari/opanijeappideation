# H — Live site recon: opanije.com

Recon date: 2026-08-05. All facts below were observed directly (HTTP fetch of the live site, the
site's own JSON feeds, and read-only inspection of the production VPS). Nothing on the VPS was
modified. Where something could not be reached, it is marked as such.

---

## What opanije.com is today

**Stack.** WordPress **6.9**, self-hosted on the Hetzner VPS `178.156.171.106`
(`/var/www/opanije/public_html`), behind nginx + Cloudflare. Custom first-party theme `opanije`
(React 19 + Vite + Tailwind build pipeline, ACF Pro, `page-templates/*.php` per page). Rank Math SEO.
Redis object cache. UpdraftPlus backups. Intercom, Google Site Kit, Jetpack, WPForms Lite installed.
The deployed tree is git-managed (`/root/repos/opanije` → `public_html`).

A **second, separate WordPress + WooCommerce install** lives at `/shop` (not multisite — it is a
distinct WP instance under the same domain).

**Apparent purpose.** A Bahian percussion school and cultural-immersion operator, positioning
Salvador (Bahia, Brazil) Afro-Brazilian percussion for an international audience. Its own
machine-readable `llms.txt` states it plainly:

> "Bahian percussion school bridging Salvador, Brazil and the world: a cultural immersion in Bahia
> (Nov–Feb season), in-person percussion classes in Salvador with true mestres, and a free online
> percussion course."

**Languages.** Bilingual and deliberately so. **English at the root**, **Portuguese under `/pt/`**,
with an `EN | PT` switcher in the header and a custom `class-opanije-translator.php` in the theme.
The `/pt/` tree mirrors the English tree (18 PT routes confirmed live). One PT-only route exists:
`/pt/curso-de-percussao/`.

**How current it looks.** Very current, and actively worked on. Main-site pages were last modified
July 2026; theme files carry Aug 2–4 2026 timestamps; the facts feed regenerates hourly
(`generated_at: 2026-08-05T03:47Z`). The 2026 redesign (`home-2026.php`, `camp-final.php`,
`percussion-course.php`) is what is live. **The `/shop` subsite is stale by contrast** — its
products were last touched 2026-07-19 and its sitemaps date to Jan 2023.

---

## Site map

### Main site — pages (28 published, from `/wp-json/wp/v2/pages` and `page-sitemap.xml`)

| Route | Description |
|---|---|
| `/` | Home. 2026 redesign. Hero video loop, three entry points (Salvador class / free course / immersion). |
| `/camp/` | **Flagship.** The Salvador cultural immersion — 7 or 12 days, Nov 9 2026 – Feb 13 2027 season. |
| `/camp-options/` | Older camp package/tier comparison page. |
| `/camp-options-final/` | Later revision of the same. |
| `/classes/` | In-person percussion classes in Salvador — group and private, WhatsApp booking. |
| `/percussion-course/` | The **paid** online Bahian percussion course, R$297. |
| `/pt/curso-de-percussao/` | Portuguese twin of the above. PT-only route. |
| `/percussion/` | The **free** email percussion course — delivered via Google Classroom. |
| `/plans/` | Legacy sales page ("Learning Traditional Arts And Culture At Opanije!"). |
| `/about/` | Team and story — Junior and Rodolfo/Visconde. |
| `/contact/` | WhatsApp, Calendly consult, email. |
| `/press/` | Media & press kit page — awards, festivals, partnerships. |
| `/journal/` | Editorial index for the 2026 cultural guides. |
| `/blog/` | Older blog index (2022 era). |
| `/thank-you/` · `/obrigado/` | Post-signup confirmation pages, EN and PT. |
| `/brazilian-drums/` | "Brazilian Drums and Instruments List" (2023 SEO page). |
| `/brazilian-instruments/` | "Brazilian Instruments" (2022–23 SEO page). |
| `/brazilian-rhythms/` | "The 1# Definite Guide to Brazilian Rhythms" (2022). |
| `/what-is-samba/` | "Definite Samba Guide — Brazilian History and Culture". |
| `/what-is-candomble/` | "What is Candomble" (2022). |
| `/what-are-traditional-arts/` | "What are Traditional Arts in Brazil and African Diaspora?" |
| `/learning-percussion-instruments/` | "6 Steps to Learning Percussion" (2022). |
| `/best-percussion-rhythms-and-traditions/` | Africa & diaspora rhythms roundup (2022). |
| `/final37/` · `/legacy1/` · `/3323-2/` | Untitled internal/legacy landing-page drafts, still published. |
| `/privacy-policy/` · `/terms-of-service/` · `/cookies-policy/` | Legal. |

### Main site — posts (6, all 2026, the "Journal")

| Route | Description |
|---|---|
| `/what-is-samba-reggae/` | The Salvador-born rhythm behind Olodum and the blocos afro. |
| `/drums-of-bahia/` | Field guide to surdo, timbau, repique, caixa, agogô. |
| `/percussion-and-candomble/` | How sacred Afro-Brazilian rhythm shaped Bahian music. |
| `/salvador-culturally-curious/` | How to experience the real rhythms and heritage of the city. |
| `/rhythms-of-brazil/` | From Samba de Roda to samba-reggae. |
| `/learn-brazilian-percussion/` | "Six Steps That Actually Work". |

### `/shop` subsite (separate WooCommerce install)

`/shop/` · `/shop/store/` · `/shop/cart/` · `/shop/checkout/` · `/shop/my-account/` ·
`/shop/about-us/` · `/shop/home/` · `/shop/auto-cart/` (an "Auto Cart Handler" page) ·
`/shop/product/<slug>/` × 57 published products (65 including drafts).

### Machine-readable endpoints

- `/llms.txt` — hand-written LLM-facing site summary.
- `/wp-json/opanije/v1/facts` — custom JSON feed: identity, team bios, contacts, full 50-item
  catalog with prices, season calendar. Regenerated hourly.
- `/sitemap_index.xml` (Rank Math), `/shop/sitemap_index.xml`.
- `/wp-content/themes/opanije/pwa/manifest-main.webmanifest` and `manifest-shop.webmanifest`.

---

## Commercial surface

**Three offers, only one of which can actually be bought online.**

### 1. The Bahia immersion / "Africa Bahia Summer Camp" — the real revenue product

48 SKUs in WooCommerce, **priced in USD**, generated as a matrix of
`single|couple` × `7|12 days` × `Essential|Bahia Plus|VIP Immersion` × `Nov|Dec|Jan|Feb`.

| Tier | Range (USD) |
|---|---|
| Single 7 days | $800 (Nov) – $1,400 (VIP) |
| Single 12 days | $1,400 – $2,500 |
| Couple 7 days | $1,500 – $2,700 |
| Couple 12 days | $2,600 – **$4,800** (VIP) |

Season: **2026-11-09 → 2027-02-13**. Prices step up month by month within the Essential tier
(Nov cheapest, Feb dearest); Plus and VIP are flat across months.

The `/camp/` page itself shows **no prices** — it routes to a free 30-minute Calendly consult, a
WhatsApp thread, or an email itinerary capture. Pricing lives only in `/shop`.

### 2. The paid online course — R$297, **but with no working checkout**

`/percussion-course/` and `/pt/curso-de-percussao/` advertise "R$ 297", "Pagamento único · Garantia
de 7 dias · Sem mensalidade", and payment by **Pix or credit card**. This is the one place BRL
appears — it is a Brazil-domestic offer.

**There is no checkout.** Every primary CTA ("Join the course" / "Quero entrar no curso") resolves
to `https://wa.me/5571981843221?…[course-paid]`. The only `<form>` on the page posts to
`admin-post.php` and is a lead/sample-lesson email capture. **The paid course is sold by hand over
WhatsApp.**

### 3. The free email course — the top-of-funnel

`/percussion/`: single email field → a permanent **Google Classroom** link with all modules.
Free, self-paced, lifetime access. Upsells a Calendly consult for the immersion on completion.

### Payment rail

WooCommerce on `/shop`, store currency **USD**. Enabled gateways: **Stripe (yes)**,
**PayPal Payments / `ppcp-gateway` (yes)**, **BACS / direct bank transfer (yes)**; legacy PayPal
Standard is disabled (registered to `rodolfoogliari@gmail.com`). **No Pix/Mercado Pago/PagSeguro
gateway is installed** — so the advertised Pix payment has no technical implementation on the site.

### Actual transaction volume

**5 orders total, all in status `wc-on-hold`, spanning 2025-10-28 to 2026-07-19.** None completed.
Two legacy 2023 products — "Candomblé Nation Percussion Course" and "Afro-Bahia Percussion Course" —
are priced at **0 USD**.

**Lead capture:** the theme registers an `opanije_lead` custom post type with an admin console, mail
notifier and spam filter. **12 leads recorded.**

**Plain summary:** the site is a fully built storefront with live payment gateways, but essentially
nothing has been sold through it. Commerce today is conversational — WhatsApp
(`+55 71 98184-3221`) and a Calendly 30-minute consult.

---

## Brand and voice

**Name.** "Opanijé" with the acute accent, consistently. The brand explains itself on the homepage:
Opanijé is the *toque* (rhythm) of the orixá Omolú — the brand is named after a Candomblé rhythm and
says so.

**Tone.** Warm, concrete, sensory, anti-hype. Short declaratives. Heavy use of *mestre*, *toque*,
*suingue*, *terreiro*, *bloco afro*, *Recôncavo* — untranslated Portuguese terms carried into the
English copy as texture. It repeatedly sells *access to people* rather than curriculum. Notably it
avoids exoticism and avoids "spiritual tourism" framing; Candomblé is handled respectfully and
plainly (its own llms.txt says "respectful, plain-language").

**Imagery themes.** Hands on drums (the hero is a looping close-up of hands on a drum head), street
cortejos, Pelourinho and Salvador streetscapes, small circles of students, the sea. Palette from the
PWA manifest: **`#B7780D`** (burnt amber/gold) on **`#F4EEE1`** (warm bone).

**Audience.** Two distinct ones, split by language. **English:** culturally curious international
travellers and drummers who will fly to Salvador — the $800–$4,800 immersion. **Portuguese:**
Brazilian learners buying a R$297 online course. The PT site is not a translation of a tourism
pitch; it is a differently-weighted funnel.

**Verbatim lines** (extracted from raw HTML, not paraphrased):

> "Live the rhythm of Bahia where the drums still speak."  — homepage hero

> "A cultural immersion in Salvador — percussion, dance, and the living heritage of the Recôncavo,
> guided by the mestres who keep it alive."  — homepage subhead

> "Play the drums of Bahia with a mestre who came up in the blocos."  — `/classes/`

> "Opanijé is the rhythm of Omolú. To learn a rhythm from here is to learn the history it carries."
> — `/percussion-course/`

> "Percussion Course with Junior 'Pai de Santo' free, forever. Learn the beats that move Bahia
> straight from a true master."  — `/percussion/`

> "Viva o ritmo da Bahia onde o tambor ainda fala."  — `/pt/` (the PT rendering of the hero)

> "OPANIJÉ /ô-pa-ni-jé/ — um toque tradicional afro-brasileiro. Tudo o que a gente faz leva o nome
> desse toque."  — `/pt/`

Trust markers repeated across pages: "Taught by mestres", "Small groups", "Rooted since 1996",
"1,000+ students taught", "No deposit to talk", "A real person answers — no bots."

---

## The masters

**Adson Vasconcelos dos Santos Junior — "Pai de Santo"** — the face of the teaching brand, named on
almost every page.
- Titled "Bahian mestre · lead teacher" on `/about/`; "Lead Instructor & Percussionist" in the facts feed.
- Bio (facts feed, verbatim): *"Began his career in 1996 with Timbalada in Salvador; has played
  alongside Carlinhos Brown, Marisa Monte and Olodum, touring Europe and Asia with Brazilian dance
  companies. Has trained more than 1,000 students."*
- `/about/` adds: *"On the drum since age five."* `/camp/` says he began at fourteen and has toured
  20+ countries. **These three origin details are mutually inconsistent across pages** — worth
  reconciling before any app reuses the bio copy.
- He is the named instructor of both the free and the paid online courses, and of the in-person classes.

**Vanderson "Macumbinha"** — appears on `/camp/` as a second immersion teacher: a percussionist from
the **Federação** neighbourhood who plays with **Timbalada** and teaches through the **Dendê
Project**. He is *not* on `/about/` and *not* in the facts feed. (Note the spelling on the site is
"Macumbinha", not "Macumbinho".)

**Kalaban** — mentioned only inside the founder's bio in the facts feed, as a long-time collaborator.
No page of his own.

**Rodolfo Celliert Ogliari — "Meu Velho Visconde"** — the founder and operator. Titled "Founder ·
Cultural producer & audiovisual direction" on `/about/`, "Producer, Percussionist & Translator" in
the facts feed. Described as raised in his family's Samba de Roda tradition, bridging Brazil and West
Africa, and as having partnered/played/travelled for over ten years with Junior, Macumbinha and
Kalaban, providing musical support, production and translation.

**Framing.** Masters are presented as living carriers of a lineage, not as celebrity instructors.
The pitch is proximity — learning *from* them, in the communities where the toques were born.

---

## External presence

Every page footer links exactly three accounts and nothing else.

| Channel | URL | Observed |
|---|---|---|
| Instagram | `instagram.com/opanijeworld/` | **798 followers**, 153 following. Bio: *"Traditional Arts Platform / Afro-Brazilian Culture / Percussion course with Junior 'Pai de Santo' out now!"* Link in bio → opanije.com. (A search snippet reported 833 followers; treat ~800 as the figure.) |
| YouTube | `youtube.com/@opanijeworld` | **33 subscribers, 15 videos.** Extracted from the channel HTML; the rendered video list is JS-only, so titles and view counts could not be read. |
| Facebook | `facebook.com/opanijeworld` | Live. A second, older page `facebook.com/OpanijeOficial/` also exists in search results. Follower counts not retrievable without login. |

A second Instagram handle `@opanije` exists in search results but is **not** linked from the site.

**Press and institutional credits** (from `/press/`, unverified externally): Prêmio Cultura Viva for
"Tudo Começa no Tambor"; a partnership with **IPHAN** (Brazil's national heritage institute);
performance at the **20th Festival Sur le Niger**, Ségou, Mali; ongoing Brazil–Ghana cultural
exchange. The page offers a press kit (hi-res photos, EN/PT bio and fact sheet, ZIP on request).

**No third-party press article about opanije.com surfaced in search.** Search for "Opanijé" mostly
returns academic and liturgical material about the Omolú rhythm itself, plus an unrelated Salvador
organisation "Organização Popular Africana Negros Invertendo o Jogo Excludente" (founded 2005) that
shares the name. **Organic discoverability of the brand is effectively nil.**

---

## What is live on the VPS

`/var/www/opanije/public_html` — WordPress 6.9, owner root/www-data, git-tracked, deployed from
`/root/repos/opanije`. `wp-config.php` is mode 640 and there is a separate `/var/www/opanije-secrets`
directory. The `/shop` WooCommerce install sits inside it as a subdirectory.

Also on the box: `/var/www/outreach` — a large first-party PHP outreach/CRM system owned by
`outreach-svc` (leads, email, invoices, finance, deliverability, cron, insights), with its own
`CLAUDE.md`/`AGENTS.md`. It is **not** the public site and is not linked from opanije.com. Plus
`/var/www/letsencrypt` and `/var/www/html`.

**Site vs deployment — the notable divergences:**

1. **A PWA already ships.** `wp-content/themes/opanije/pwa/` contains `sw.js` (a real service
   worker), `manifest-main.webmanifest` + `manifest-shop.webmanifest`, 192/512 icons including
   maskable variants, and **separate offline pages for EN and PT-BR** (`offline-en.html`,
   `offline-pt-br.html`). The site is already installable to a phone home screen. Nothing in the
   public copy mentions this.
2. **A course-player app already exists in the theme, unreferenced by the public site.**
   `page-templates/course-app.php` is documented as the *"Internal paid-course application
   template"*. It renders a **library screen, a continue-watching row, a course detail, a lesson
   player, and per-lesson progress bars**, driven by a view model with `progress_url`, `lesson_url`
   and a REST nonce — i.e. there are already REST endpoints for lesson delivery and progress
   tracking. This is a working LMS shell that no public route currently exposes.
3. **The `/shop` subsite is a separate, older WordPress** with its own theme, sitemap (2023) and
   About page — a visible seam between the 2026 marketing site and the 2023 store.
4. **Legacy pages are still published and in the sitemap**: `/final37/`, `/legacy1/`, `/3323-2/`
   (all untitled), plus `/camp-options/`, `/camp-options-final/`, `/plans/`, `/blog/`.
5. A `LearnPress` LMS was installed at some point — its options (`learn_press_courses_page_id` etc.)
   are still in the database, though the plugin is no longer in `wp-content/plugins`.
6. A previous theme is retained as `themes/opanije-backup-20251111-125303`.
7. `node_modules` and `package-lock.json` are **committed into the live theme directory** — the
   build tree ships to production.

---

## Assets that already exist and could be reused by a mobile app

**Brand system.** Complete and current. Name with correct diacritic, the Omolú-rhythm etymology as a
brand story, colour tokens (`#B7780D` / `#F4EEE1`), a full Tailwind config (`tailwind.config.js`,
20 KB), app icons already cut at 192/512 plus maskable, and an existing PWA manifest with
`display: standalone`. A mobile app can adopt the visual identity on day one.

**Copy.** Substantial and unusually good. ~28 pages plus 6 long-form journal articles, **fully
bilingual EN/PT** with a first-party translator layer and `languages/` directory. Course curriculum
copy already exists in four blocks (Foundation / Toques / Instruments / Swing). Legal copy (privacy,
terms, cookies) exists in both languages and is app-store-submittable.

**Structured data — the single most valuable asset.** `/wp-json/opanije/v1/facts` is a live,
hourly-regenerated JSON feed containing identity, team bios, contacts, the full 50-item catalog with
prices and currency, and the season calendar. An app can consume this directly as a config/catalog
endpoint with zero new backend work. `inc/poi-data.php` (20 KB) additionally holds Salvador
points-of-interest data.

**A working LMS shell.** `course-app.php` plus its REST progress/lesson endpoints already implement
library → course → lesson → player → progress. A mobile app could wrap or mirror this rather than
designing course structure from scratch.

**Imagery.** ~1.1 GB of uploads: **1,458 JPG, 917 AVIF, 680 WebP, 281 PNG, 117 JPEG** — already
served in modern formats via Optimole/CompressX/webp-uploads. More than enough for an app's visual
layer.

**Video.** 15 short hero/teaser clips from Dec 2025, professionally cut and encoded in **three codecs
(AV1, H.265, H.264) at both horizontal and vertical aspect ratios** — the vertical variants are
directly usable as mobile onboarding/hero media, which is rare to find already done.

**Payment integration.** WooCommerce with **Stripe and PayPal Payments already enabled and
configured**, USD store currency, and 57 published SKUs with real prices. An app can transact against
an existing rail.

**Domain, hosting, infrastructure.** Owned VPS, nginx, Cloudflare, Let's Encrypt, Redis, UpdraftPlus
backups, git-based deploy, plus a substantial in-house outreach/CRM system at `/var/www/outreach`
already handling leads, email and invoicing.

**Distribution.** WhatsApp Business number (`+55 71 98184-3221`) with per-page pre-filled,
UTM-tagged message templates; a Calendly consult funnel; `contact@opanije.com`; Intercom installed.

**Content pipeline.** A YouTube channel with 15 videos, and a live Google Classroom already carrying
the free course's modules — real lesson content exists, just not on the site's own infrastructure.

---

## Gaps

**Audience.** This is the binding one. ~800 Instagram followers, **33 YouTube subscribers**, **12
captured leads**, **5 orders — all still `on-hold`, none completed**. There is no mailing list of
meaningful size, no proven customer base, and no organic search presence for the brand name. A mobile
app would launch to essentially no installed audience. Any app plan that assumes an existing base to
convert is assuming something that is not there.

**No mailing list infrastructure.** No Mailchimp/ConvertKit/Klaviyo/Brevo integration exists. Email
capture writes to a WordPress custom post type and fires `wp_mail`. The "free email course" is not an
automated sequence — it sends one Google Classroom link. There is no drip engine, no segmentation,
and no list to import into an app.

**No lesson media under Opanijé's control.** The uploads directory contains **zero instructional
video or audio** — only marketing teasers. The actual teaching content lives on **YouTube and Google
Classroom**, third-party platforms with no API contract here. An app cannot ship offline lessons,
practice loops, or per-instrument stems today because those files do not exist as owned assets. This
is the largest content gap: a percussion app needs **isolated audio** (tempo-mapped loops, individual
surdo/repique/timbau/caixa/agogô tracks, click tracks) and none of it exists.

**No user accounts, no identity.** The main site has no login, no membership, no student area, and no
purchaser→content entitlement link. `daggerhart-openid-connect-generic` is installed but unused for
students. WooCommerce `my-account` exists only on the disconnected `/shop` subsite. The `course-app`
template has progress endpoints but nothing establishes *who* a user is. An app needs an auth and
entitlement layer built from zero.

**The paid course has no checkout.** R$297 is advertised with Pix and card, but the CTA is a WhatsApp
link and **no Pix or Brazilian gateway is installed**. Selling a course in-app to a Brazilian
audience requires a BRL rail (Pix, Mercado Pago, or Stripe BRL) that does not exist yet.

**The two currencies do not meet.** The store transacts USD; the course is priced BRL. There is no
multi-currency handling. An app serving both audiences needs a currency and pricing strategy that the
site has never had to resolve.

**No structured curriculum data.** Course "modules" exist as marketing prose in PHP templates, not as
data — no lesson list, no ordering, no durations, no rhythm/instrument taxonomy, no notation or
tablature. The `course-app` view model expects such data; nothing populates it.

**No analytics on learning.** Site Kit and Jetpack track pageviews. Nothing measures practice,
retention, or completion — the metrics a learning app is judged on.

**No app-store presence.** No developer accounts, bundle identifiers, store listings, screenshots, or
privacy-nutrition-label disclosures. The PWA icons exist but no native app scaffolding does.

**Content inconsistency to resolve first.** Junior's origin is stated three different ways across
`/about/`, `/camp/` and the facts feed (age five / age fourteen / career began 1996). Vanderson
"Macumbinha" appears on the camp page but is absent from `/about/` and the facts feed. Legacy
untitled pages (`/final37/`, `/legacy1/`, `/3323-2/`) are still published and indexed. Any app that
syndicates this copy will syndicate the contradictions.

---

## Reach limitations

- **YouTube video titles and view counts** could not be read — the channel's video grid is
  JavaScript-rendered and no `channelId` was exposed in the served HTML, so the RSS feed could not be
  derived. Subscriber (33) and video (15) counts *were* recovered from the page markup.
- **Facebook follower counts** are behind a login wall and were not retrieved.
- **Instagram post count** was not exposed; follower (798) and following (153) were.
- **Press claims** (Prêmio Cultura Viva, IPHAN, Festival Sur le Niger, Ghana exchange) are taken from
  the site's own `/press/` page and were **not** independently corroborated by any external source.
- The WordPress database was queried only via read-only `wp-cli` counts; no lead or customer personal
  data was read or recorded.
