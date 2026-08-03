# Opanijé — Release 1 Addendum, second session of 2026-07-31

**What this file is.** Everything decided in the second conceptualization session of 2026-07-31,
plus the game thinking that came out of it. It sits beside `RELEASE-1-EXPERIENCE-SPEC-V1.md` and
`PLAN-AMENDMENTS-FOR-V2_1.md` and under `PRODUCT-GOALS-VNEXT-CONSOLIDATED-V2.md`.

**Nothing here is operative until ratified.** Proposed deltas are gathered in §8. Nothing here
touches a red line.

**Numbering continues the estate.** Deltas from D36 (v2.1's proposals end at D35). Inputs from
INPUT-57 (v2.1 ends at INPUT-56). Recommendations from R55 (v2.1 ends at R54). Ledger rows from 36
(v2.1 offers 34–35).

**§7 is written to be read on its own,** because the game is being taken to a separate conversation.

---

## 1 · What was decided

| # | Decision | Status |
|---|---|---|
| S1 | Build the mockup and the basic functionality **first**. The shoot, and the lawyer, wait for it — because the mockup changes what we need from both | FOUNDER-DECIDED |
| S2 | **Design is the exception** and runs in parallel, in Claude Design, as its own tool and its own track | FOUNDER-DECIDED |
| S3 | The Brazilian payment rail (Pix) is **live before Release 1**, not at M2 | FOUNDER-DECIDED |
| S4 | Release 1 **sells inside the app** — full store billing, on top of the web rail, not instead of it | FOUNDER-DECIDED |
| S5 | **The website stays the priority funnel.** Most buyers come through the site at full margin; the in-app rail is additive | FOUNDER-DECIDED |
| S6 | **Junior plays every drum himself**, layered. There is no ensemble at this point | FOUNDER-DECIDED |
| S7 | **Junior is a co-founder of the app.** Standing rule: always choose cheaper in people, more expensive in Junior's hours | FOUNDER-DECIDED |
| S8 | Store account enrolment (Apple, Google) moves to **immediate**, reversing S1's deferral for this item alone | FOUNDER-DECIDED |
| S9 | The game's direction is **not decided here** — it moves to its own conversation, seeded by §7 | FOUNDER-DECIDED |

---

## 2 · The sequencing, as it now stands

v2.0 §7.4 put four things first because they were "other people's clocks": store enrolment,
counsel, INPUT-41, and the escrow. S1 reorders that. The reason is sound and worth stating plainly,
because it will be questioned later: **the mockup is what tells us what to film and what to ask.**
Film first and we film the wrong tempos; ask the lawyer first and we ask about an app that does not
exist yet.

**What moved behind the mockup**

- The M0 shoot. Nothing the student sees exists before it, but what it must contain is not yet
  known.
- INPUT-41 (is a fixed ladder good enough teaching). The mockup is the cheapest possible way to put
  a real answer in front of Junior instead of a description.
- Most of the counsel brief — privacy, data collected, deletion paths. All of it describes an app
  whose shape is still moving.

**What did not move, and must not**

- **Design (S2).** Runs now, in parallel. R49's lock-and-file means design freeze → industrial
  design filing → only then may a screen be public. A design that does not exist cannot be filed,
  and the filing sits on the critical path.
- **Store enrolment (S8).** Nothing in the mockup changes the paperwork, and under S4 it now stands
  between Junior's closing invitation and money arriving. See §3.
- **The escrow (v2.0 §7.0).** Still first. It protects the code estate and the Android signing key,
  both of which matter before any recording exists.

**What is unruled, and I am flagging rather than assuming**

Four items inside the counsel brief are **not** mockup-dependent and cost nothing to start now:

| Item | Why it does not need the mockup |
|---|---|
| INPUT-32 — is marking the name acceptable to Junior at all | A question about the name, asked of a person. Prior to and independent of legality |
| INPUT-22 — do the consent instruments license game use | About paper already drafted. v2.0 calls it the cheapest irreversible item in the estate |
| INPUT-45 — repository migration to a company organisation | Pure hygiene, unrelated to product shape |
| INPUT-31 — name clearance | Sequenced after INPUT-32, but the brief can be written now |

**Recommendation (R57): let these four proceed.** Deferring them buys nothing.

---

## 3 · Operator tasks — start now

| # | Task | Why immediate |
|---|---|---|
| O1 | **Open the Apple Developer and Google Play accounts in the company's name (CNPJ).** Apple's organisation route needs a D-U-N-S number, which has real lead time for a Brazilian entity | S8. Under S4 there is no in-app sale without it. Free, slow, unaffected by anything the mockup decides. INPUT-40 |
| O2 | **At enrolment, apply for both small-business commission programmes** (Apple App Store Small Business Program, Google Play's reduced service fee) | The difference is 15% versus 30% of every in-app sale. It is an application, not an automatic grant, and it should be done at signup rather than discovered later. Verify current terms at enrolment — v2.0 §19 flags the store terms as unverified |
| O3 | **Stand up the Pix / BRL rail on the web** | S3. Also the rail Salvador and Junior's private classes must use, since neither can go through store billing |
| O4 | **Reconcile the seller of record** — the manual-transfer gateway currently names an individual with a US phone number, not the CNPJ entity | INPUT-42. A store account in the company's name over a payee that is a person is a mismatch that surfaces at the worst time |
| O5 | **Escrow the signing key and the backup key; restore the backup passphrase** | v2.0 §7.0, unchanged. Also a store-submission dependency — the Android signing key is the account's identity |
| O6 | **Migrate the repositories to a company organisation** | INPUT-45. Zero cost, and personal-account ownership is what diligence flags |

---

## 4 · Selling inside the app — what it costs, and the correction

**The founder's correction is recorded and it matters.** I framed the store tax as though it applied
to every sale. It does not. The site is the priority funnel (S5), the web rail carries full margin,
and the store's cut only touches the share of buyers who happen to buy inside the app.

**The arithmetic, per R$297 course.** All figures ASSUMPTION — master share is INPUT-3 and has not
landed. The model follows v2.0 in treating both the fee and the master share as percentages of list
price; INPUT-3 will settle whether the share sits on gross or net.

| Route | Fee | What is left after the master's share | Sales to recover R$10k |
|---|---|---|---|
| **Web + Pix** | ~1% | **≈ R$205** | ≈ 49 |
| Web, as v2.0 modelled it (PayPal-shaped, ~8%) | ~8% | ≈ R$184 | ≈ 55 |
| In-app, small-business rate | 15% | ≈ R$163 | ≈ 61 |
| In-app, standard rate | 30% | ≈ R$119 | ≈ 84 |

**Two things fall out of that table.**

1. **Pix makes the web rail better than the plan assumed, not just possible.** v2.0's R$184 was
   built on an ~8% fee. Pix is close to free. S3 quietly improves the base case for every sale that
   comes through the site — which under S5 is most of them.
2. **O2 is worth real money.** The gap between the two in-app rates is R$44 a sale. Over a hundred
   in-app sales that is a shoot's worth of budget, decided by whether someone filled in a form at
   signup.

**What S4 pulls back into Release 1 from M2**

- **INPUT-9** (how loudly the app may point at the web rail) and v2.0 §4.5's re-verification. Both
  were deferred to M2 on the grounds that Release 1 sells nothing. It sells now. These are the one
  genuinely mockup-independent piece of the counsel brief that S4 creates, and they should join the
  brief when it is written.
- **Store billing as a build item.** Two platforms, two billing systems, from zero. This is real
  engineering that Release 1 did not previously carry.
- **Price parity across rails** (INPUT-10) stops being theoretical the moment both rails are live.

**One piece of good news.** R13's architecture survives untouched. The app still never reads a
receipt to decide what someone owns: the store's receipt goes to our server, our server validates it
and writes the entitlement, and the app asks the server the same question it always asked. The rail
being rewritten while it has zero rows is exactly the moment to add this.

---

## 5 · One master, every drum

**What it buys.** One person to schedule, one consent instrument, one set of terms, no new names to
credit permanently. Under S7 this is the correct trade every time. And it makes a sentence true that
no competitor can copy: *every drum in this room is him.*

**What it costs, and it is not money.** The cost lands entirely on Junior's hours. On the free
rhythm's recommended shape alone — four parts, three speeds — that is around twelve passes, before a
single count-in is recorded. Cheaper shoot, much longer day. **INPUT-57 asks him whether he wants to
work that way.** S7 says spend his hours rather than other people's; it does not say spend them
without asking.

**What breaks.** E2 — "the real musicians, lighting up as each one joins" — cannot work with one
man recorded four times. The play screen needs something else on it. That is INPUT-61 and it is a
conceptual question, not a build one; I will bring options.

**What this resolves.** The portrait stills of a full battery, which I flagged as an unlisted shoot
item, are no longer needed. One person, photographed properly, in the room he plays in.

**What it leaves open.** INPUT-55 — whether Vanderson appears in Release 1 at all — narrows but does
not close. The free rhythm is Junior's (E17) and the battery is Junior's (S6). Whether Vanderson has
his own rhythm in Release 1 is still unruled, and his stems are shot at M0 either way.

---

## 6 · Junior as co-founder

**Recorded as founder-asserted fact.** Junior is a co-founder of the app, not a contracted master.

**The standing rule that follows (S7):** always choose the option that is cheaper in people and more
expensive in Junior's own hours.

**What it touches in the plan**

- **INPUT-3 (master terms).** A co-founder's terms are a different instrument from a revenue share.
  This should be said out loud before the cash model is built on placeholders.
- **Ledger row 18** ("master economics make joining rational") and note C11, which worried that a
  master who does not rule on product form has shown less commitment than the row assumes.
  Co-founder status is a stronger commitment signal than the row was written against. It does not
  upgrade the row — nothing here is measured — but the row's premise improves.
- **R11's no-digital-skill reading** is unaffected. Being a co-founder does not make someone want to
  troubleshoot a dropped connection.

**What it explicitly does not touch.** Red line #1 and v2.0 §12: sacred material sits under the named
authority of its tradition, and a charter red line cannot be narrowed from one side. S7 is a rule
about how we spend hours. It is not a rule about whose ruling stands on partition values, on marking
the name, or on whether a form of play is acceptable. Those stay exactly where the charter puts
them.

---

## 7 · The game — seed for the next conversation

*This section is written to be read cold, without the rest of the file.*

### 7.1 · The box we are in

Rules already made, none of them up for renegotiation:

- **The app cannot hear you.** No microphone anywhere in Release 1.
- **The app cannot judge you.** It counts facts; it never returns a verdict.
- **No targets.** "12 cycles," never "12 of 20." A progress bar filling toward a goal is a verdict in
  a costume.
- **No streaks, no reproach.** Nothing may tell a student they have fallen behind.
- **The student pulls every lever.** The app never advances anyone.
- **Nothing is taken back.** The free room stays exactly as it was, forever.
- **No recording of a master may name a price or a product**, so nothing he says can expire.

### 7.2 · The reframe that unlocked it

We kept saying: no judging, so no game. That is wrong, and here is why.

**Something in the room already judges you — the agogô, and your own ears.** Percussion tells on you
instantly. If you are off, you know it before anyone says so. This is why the plan insists the
reference pulse is an instrument of the tradition and never a metronome.

**So the app was never going to be the referee.** Its job is to hand you the right room at the right
moment. **The game is in choosing the room.**

### 7.3 · What we already have, seen properly

We have been calling it a ladder — level 1 up to level 4, easy to hard. It is not a ladder.

- **Fewer drums** is easier to follow and much scarier to play. You are exposed.
- **More drums** is harder to track and much easier to hide inside. You are carried.
- **Speed** is a third thing entirely, unrelated to either.

Those are three different feelings, not one line from easy to hard. **The same twelve recordings,
described as a small room you move around in rather than a ladder you climb, stop being progress and
start being choice.** Going from four drums back to two becomes a move, not a retreat — and naming it
that way is a design decision we have not made yet.

### 7.4 · The reward object we already own and have not noticed

E1 already makes the level change a musical event: the cycle finishes, **the master calls the next
player in and counts**, the battery resumes bigger than it was. That count-in is the strongest reward
object in the estate — it is a human voice, it is his, it cannot be cloned, and **it is already being
filmed.** Whatever the game turns out to be, it should be built around that moment rather than
around anything we would have to invent.

### 7.5 · A guess that needs Junior

In percussion there are usually **breaks and turnarounds** — the lead drum signals, everyone changes
together. Learning to hear the signal coming and change with it is a real skill, practiceable alone,
and **the app never has to grade it**: the break happens, and you know whether you caught it. That
would be a whole game running on the student's ears and on nothing we build.

**I do not know whether these toques work that way. That is Junior's answer, not mine.** INPUT-58.

### 7.6 · The fork that was not answered

Where should the pull come from in Release 1?

| Direction | What it means | Cheap now? | Cheap later? |
|---|---|---|---|
| **More to hear** | More rooms, more speeds, more rhythms, a map that fills in | Yes — it is mostly audio we are already shooting | **No.** Every new thing is another day of Junior's time |
| **More to do** | Things that happen inside the room you are already in — breaks to catch, parts to swap mid-session, the room reacting | **No** — real design and real build | Yes. It multiplies everything we ever film |
| **More to look back on** | The record is the pull — the quiet count, the Caderno, "fourteen times in this room; the first time you lasted three minutes" | **Cheapest of the three** | Yes — but slowest to bite |

### 7.7 · Other threads worth picking up in that conversation

- **A session has no natural end.** Practice loops forever. If the app may not set a target, something
  else must punctuate the sitting. Right now the only punctuation is the closing count. The game may
  turn out to live in the **shape of a single sitting**, not in the shape of progress across weeks.
- **The Caderno entry is the only real unlock in the product**, and it is written by a human-shaped
  event — the first real practice. Worth asking what else deserves that treatment, and what
  definitely does not.
- **The map's danger.** If we ever show the grid of rooms, it must show what is lit and never a
  fraction and never a total. "12 of 36" is the exact failure mode.
- **Two numbers judge everything.** M1's headline evidence is first-session completion and day-7
  return. Any game element should be argued against those two, not against whether it is fun.

### 7.8 · What must not be built, in one place

Progress bars. Percentages. Streaks. Badges that touch standing. Leaderboards. Anything that
compares one student to another. Anything that tells someone they are behind. Any recording of a
master that names a price.

---

## 8 · Proposed deltas (continuing v2.1's, which end at D35)

| # | Delta | Was | Now |
|---|---|---|---|
| D36 | Sequencing inverted — mockup and core functionality before the shoot and before most of the counsel brief | §7.4's build order, external clocks first | §2 |
| D37 | **Release 1 ships commerce** — Pix live before Release 1, plus in-app purchase | §4.1: "ships with no commerce surface at all"; D13; INPUT-42 as an M2 precondition | §4 |
| D38 | The battery is Junior alone, layered; E2's named presence is void and needs a replacement | E2, multiple named musicians lighting up | §5 |
| D39 | Junior recorded as co-founder; standing rule of cheaper in people, more expensive in Junior | Master under A12, terms at INPUT-3 | §6 |
| D40 | Tempo steps become a pre-shoot decision, because E1's count-ins are tempo-locked | Tempo as a rendering parameter | §7.4, INPUT-59 |
| D41 | Design runs in parallel in a separate tool from the start | R54, a recommendation | S2 |
| D42 | INPUT-9 and §4.5's store re-verification return from M2 to Release 1 | Deferred to M2 on the grounds that Release 1 sells nothing | §4 |

---

## 9 · Register additions (continuing v2.1's, which end at INPUT-56)

- **INPUT-57 · Junior — will he play every part himself**, layered, at roughly twelve passes per
  rhythm plus count-ins? S6's precondition. Cheap to ask, expensive to assume.
- **INPUT-58 · Junior — do these toques carry breaks and turnarounds** (a signal from the lead drum,
  everyone changes together)? Structural to the game, and it changes what is filmed. See §7.5.
- **INPUT-59 · Founder — the tempo steps.** How many, and at what speeds. Pre-shoot, because the
  count-ins are locked to whatever speed they were recorded at. Informed by the mockup.
- **INPUT-60 · Founder — what goes on the play screen** now that there is one musician and E2 is
  void.
- **INPUT-61 · Founder — Junior's co-founder terms.** Does S7 change INPUT-3's instrument? Flagged
  before the cash model is built on placeholders.

**Two existing items change date rather than content:** INPUT-9 and INPUT-42 move from M2 to
Release 1 under D37. **One narrows:** INPUT-55 (does Vanderson appear in Release 1) is now only
about whether he has his own rhythm, not about the battery.

---

## 10 · Recommendations issued (continuing v2.1's, which end at R54)

| # | Recommendation | Status |
|---|---|---|
| R55 | The mockup runs on rough phone recordings of Junior — prototype only, never shipped, deleted once real material exists. Get a one-line written OK from him first; he is a co-founder and it is trivial, but the estate's whole discipline is that no recording of a master exists without paper | Build-side, flagged for consent hygiene |
| R56 | State the rail mix in the monthly cash model — what share of sales is expected through the site versus in-app — so the blended margin is a number rather than a surprise | Recommendation |
| R57 | Let the four mockup-independent items proceed now: INPUT-32, INPUT-22, INPUT-45, and drafting INPUT-31. Deferring them buys nothing | Recommendation |
| R58 | Describe the ladder as a room, not a rungs. Fewer drums is exposure, more drums is shelter, speed is separate. Moving down is a move, not a retreat | Recommendation → the game conversation |

---

## 11 · Ledger implications (continuing v2.1's, which end at row 35)

No existing row's status changes. Two candidates, offered rather than asserted:

| # | Claim | Status | Converts at | Required evidence |
|---|---|---|---|---|
| 36 | In-app purchase converts well enough to justify the store's cut on the share of buyers who use it | HYPOTHESIS | M2 | Rail mix, conversion by rail, blended contribution per sale |
| 37 | A battery played entirely by one master is as compelling to a student as one played by an ensemble | HYPOTHESIS | M1 | First-session completion, day-7 return, session length |

---

*Second session of 2026-07-31. Companion to `RELEASE-1-EXPERIENCE-SPEC-V1.md` and
`PLAN-AMENDMENTS-FOR-V2_1.md`. Nothing here is measured evidence, nothing here is operative until
ratified, and nothing here touches a red line. §7 is the seed for a separate conversation on the
game and is written to be read on its own.*
