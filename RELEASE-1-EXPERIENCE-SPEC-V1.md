# Opanijé — Release 1 Experience Spec v1.0

**What this file is.** The student-facing experience of Release 1, as conceptualized with the
founder on 2026-07-31. It is subordinate to `PRODUCT-GOALS-VNEXT-CONSOLIDATED-V2.md` and changes
nothing in it; where this session's decisions diverge from v2.0, the divergences are gathered
separately in `PLAN-AMENDMENTS-FOR-V2.1.md` and none is operative until ratified there.

**Status of everything below.** FOUNDER-DECIDED where the founder chose it in session;
PM-RECOMMENDED where I proposed it and it is not yet chosen; DERIVED where it follows necessarily
from a founder decision and is stated so the consequence is visible rather than discovered.

**Scope boundary.** This describes the student app only (§4.6 surface 1). The master's standing
room and the operator console are untouched. Nothing here concerns the build; technical resolution
sits on the build side and surfaces here only where it changes what the student experiences.

---

## 1 · The decisions, gathered

| # | Decision | Status |
|---|---|---|
| E1 | A level change is a **clean break**: the cycle finishes, the master calls the next player in with a count-in, the battery resumes with the new part | FOUNDER-DECIDED |
| E2 | The screen during play shows **named presence** — the real musicians, lighting up as each joins. Video appears only at the call | FOUNDER-DECIDED |
| E3 | The phone is **propped up and glanced at**. One lever, arm's length, no menus mid-session | FOUNDER-DECIDED |
| E4 | The door is **presentation → OAuth → a short welcome from the master → choose your part → the call → play → first entry** | FOUNDER-DECIDED |
| E5 | The **first Caderno entry is earned by the first real practice**, not by answering the call | FOUNDER-DECIDED |
| E6 | The home screen leads with **today's session, with the rhythm and your distance through it beneath it**, plus a Caderno card | FOUNDER-DECIDED |
| E7 | At the end of the free rhythm, **the master offers the next step** — not the app, not an offer | FOUNDER-DECIDED |
| E8 | Parts are **switchable freely**, in both directions, at any time | FOUNDER-DECIDED |
| E9 | A session closes with **a quiet count of what you did** | FOUNDER-DECIDED |
| E10 | Salvador appears **at the ending**, not as a permanent surface | FOUNDER-DECIDED |
| E11 | Language **follows the phone**, with a manual override | FOUNDER-DECIDED |
| E12 | Nudges are **opt-in**, asked for after the first entry is written | FOUNDER-DECIDED |
| E13 | The free student keeps **the room, forever, unchanged** | FOUNDER-DECIDED |
| E14 | A bought course is **lessons, rooms, and narrated video** together | FOUNDER-DECIDED |
| E15 | The **1:1 is absent from Release 1** — it stays hand-booked through Track B | FOUNDER-DECIDED (and forced by §4.1's zero-commerce ruling) |
| E16 | On connection loss the **loop continues; the lever fails gracefully**; facts buffer and sync | PM-RECOMMENDED, founder leaning yes |
| E17 | The free rhythm is **Junior's** | FOUNDER-DECIDED |
| E18 | The Room is **unnamed** — it is simply where you play | FOUNDER-DECIDED |
| E19 | The door asks **one plain question — "do you have an instrument with you?"** — to route between palmas-and-voice and agogô | PM-RECOMMENDED; founder chose agogô-first with switching (E8), this is the open sub-fork |

---

## 2 · The student's path, end to end

**Arrival.** A presentation — what this is, whose it is, what happens here. Then Google sign-in.
Nothing is audible before this point; the presentation therefore carries the whole conversion and
is the highest-stakes screen in Release 1.

**Welcome.** Junior, recorded once, speaking to a person who has just arrived. Seconds, not
minutes. This becomes the single most-viewed asset in the estate and should be shot accordingly.

**Choosing.** The student picks their part. Under E19 this is preceded by one plain question about
whether they have an instrument to hand; under E8 whatever they pick is reversible at any moment,
in either direction. Nobody is ever stuck on a part that is too hard, and nobody discovers the
easier path only after failing.

**The call.** The Primeira Chamada. The battery is there, the student's part is theirs, and the
first level begins.

**Playing.** The agogô and the student's own part. The screen shows who is in the room — names and
faces, present, not moving. The phone is propped up; the student's hands are busy. Nothing on
screen asks for attention.

**Rising.** When the student decides they have it — never when the app decides (D28/R51) — they
pull the lever. The cycle finishes. The master calls the next player in and counts. The caixa
enters, and the room is bigger than it was.

**Closing.** The student stops. A quiet count: minutes, cycles, the level reached. No target, no
comparison, no verdict.

**The first entry.** After the first real practice, the Caderno's card on the home screen stops
being empty. It says what happened and when, and it says who was in the room.

**Being asked back.** Only after that first entry does the app ask whether the student wants to be
called back — in the master's framing, not the system's.

**Returning.** Today's session at the top of the home screen. The rhythm and how far through it
they are beneath. The Caderno card, now with something in it.

**The ending.** When the free rhythm is finished, the master speaks again — not to sell, but to say
what comes next. For a Portuguese-language student that is the caixa, or Vanderson's toque. For an
English-language student it is the room in Salvador. Neither recording names a price.

**Staying free.** The student who never buys keeps the room exactly as it was, permanently, with
nothing withdrawn, degraded, or nagged.

---

## 3 · The invariants

These hold on every surface in Release 1 and are the operating form of rulings already made.

1. **Facts, never verdicts.** The app counts; it never judges. This is §3.3, and it reaches further
   than scoring — a progress bar filling toward a goal is a verdict wearing a different costume.
2. **Counts, never targets.** "12 cycles," never "12 of 20."
3. **No streaks and no reproach.** §3.3 puts retention on an appointment with a named human. An
   opt-in nudge is an invitation; nothing in Release 1 may tell a student they have fallen behind.
4. **The student pulls every lever.** D28. The app never advances anyone.
5. **The master offers the path; the app handles the price.** Every recording of a master must be
   free of prices, product names, and anything else that expires. Pricing is the founder's and
   moves (§12); a recording that names a figure dies the day it does.
6. **A rule may be stated; a person may not be measured.** An empty Caderno card may say what earns
   an entry. It may not say how close you are.
7. **A cache is not a library.** Ephemeral, invisible, OS-evicted, with no user-facing list. The
   moment a copy becomes durable and visible it is a download, and INPUT-47 returns to the critical
   path. The session survives a tunnel; nobody acquires a permanent copy.
8. **Facts survive the network.** Counts buffer locally and sync on return. A tunnel must not cost
   someone their first entry, and must not undercount M1's exit evidence in exactly the
   low-connectivity population M1 needs to measure.
9. **Nothing is taken back.** Red line #5, in operating form: the free room is unchanged forever.
   Conversion runs on desire, never on deprivation.

---

## 4 · What this adds to the M0 shoot

All four are near-zero cost while the cameras are already rolling and **unrecoverable afterwards**,
which places them on the pre-shoot list beside the stems (§7.2, D14).

| Recording | Why | Volume |
|---|---|---|
| **Entrance calls and count-ins** | E1 makes the level change a musical event in the master's voice rather than a gap | Per rhythm, per incoming part |
| **The welcome** | E4's door. Most-viewed asset in the estate | One, durable |
| **The next-step invitation** | E7. Two versions — domestic path and Salvador — both price-free and product-free | Two, durable |
| **Narrated video** | E14. The master telling: what the toque is, where it sits, what it is for | Per catalog item |

**Two consequences that reach past the shoot.**

- **Narration carries liturgical meaning more directly than playing does.** Junior's five partition
  values (§3.5) were captured with playable items in mind; under E14 they must be captured on
  narration items too, item by item, at the same shoot (INPUT-21).
- **Narration is the most subtitle-dense content that exists.** Combined with E11, this is the
  second thing in this session that enlarges INPUT-14.

---

## 5 · What is deliberately absent from Release 1

Stated so nobody reintroduces them by accident.

- **No microphone** (D26) — no capture, no local self-recording, no listening of any kind.
- **No commerce** (§4.1) — no purchase screen, no price shown anywhere in the app.
- **No 1:1 booking** (E15) — hand-booked through Track B for the whole of M1.
- **No permanent Salvador surface** (E10) — it lives behind the master's invitation.
- **No download library** (D27) — Release 1 streams, and §3's invariant 7 draws the line.
- **No streaks, targets, scores, or verdicts** (§3.3) — structurally, not by restraint.
- **No name for the Room** (E18).

---

## 6 · Open items

**Founder**

- **E19's sub-fork.** Agogô-first with switching is chosen; whether the door asks about instrument
  ownership before routing is open. My recommendation stands: FF3 says the true on-ramp needs no
  instrument, and a beginner who fails a part he has no instrument for churns inside first-session
  completion — M1's headline number — before ever discovering the fallback.
- **Which of Junior's toques** is the free rhythm (extends INPUT-27; the free set's stems are shot
  at M0, so this is pre-shoot).
- **INPUT-14**, now structural rather than budgetary — see the amendments file.

**Junior**

- **The free rhythm's partition value** (within INPUT-21). Under E17 the free door is built on
  Junior's material, which makes this the highest-exposure single item in the catalog — see §2 of
  the amendments file.
- INPUT-41 unchanged and unaffected by anything here: E1's clean break is the ladder's own
  transition, so the pedagogical question stands exactly as posed.

**Counsel**

- Whether a session-scoped cache constitutes a copy for red line #6's purposes (extends INPUT-47).

**Build side, mine**

- The entry threshold for "first real practice" — set low enough to land inside the first session,
  expressed in countable facts, informed by Junior but not a founder question.
- Audio continuity when the screen dims; the lever's reachability with sticks in hand; pre-account
  event attribution and its LGPD treatment; locale branching for E10's two invitations.
- **A design language for a propped-up practice screen.** The estate's Design System 2.0 is
  web-shaped — light surfaces, Heritage Gold, Montserrat and Lato, conversion-optimized. A screen
  glanced at from arm's length in a practice room is a different problem. R49's lock-and-file
  cannot proceed against a design that does not exist yet, and this is on the Release 1 critical
  path through the industrial-design filing.

---

*v1.0, 2026-07-31. Conceptualized with the founder; nothing here is measured evidence and nothing
here overrides `PRODUCT-GOALS-VNEXT-CONSOLIDATED-V2.md`. Divergences from v2.0 are gathered in
`PLAN-AMENDMENTS-FOR-V2.1.md` and are inoperative until ratified there.*
