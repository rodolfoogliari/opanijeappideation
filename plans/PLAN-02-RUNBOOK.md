# Opanijé — The First Ten Days


> ### ⚠️ Amended 2026-08-05 by the founder's ratification
>
> Put to the founder as `PLAN-00-DECISIONS.md` §8 and returned the same day. **Seventeen decisions
> RATIFIED, D96 REJECTED, D98 DEFERRED, D94 PENDING.** A physical-device test the same day returned
> **0/10** and is recorded as **ledger row 59 — FALSIFIED, MEASURED**, the first measured row in the
> company's history. The full record is `../BUILD-LOG.md`; the registers are updated.
>
> Passages superseded by that ruling are marked **AMENDED** inline. Where this document and
> `../BUILD-LOG.md` disagree, **`BUILD-LOG.md` governs.**

**Who this is for.** You, at 09:00, alone, with a terminal and Claude Code open. You are not an
engineer and you do not need to be. Every command below is real and was checked against the actual
repo on this machine. Every Claude prompt is copy-pasteable.

**The rule for the whole ten days:** when something breaks, paste the entire error into Claude and
say what you were trying to do. Do not try to understand it first. Do not edit a file by hand
because it looks like a one-line fix. Your job is direction and judgement; the machine's job is
syntax.

---

## Before Day 1 — the two-minute setup

Everything in this runbook assumes you have run this first, every session, in every new terminal:

```bash
source ~/box/mobile-env.sh
```

**This matters more than it looks.** Without it, the suite fails on a missing `JAVA_HOME`
(`appConfig.test.ts:154`) and you will spend an hour debugging a test suite that is actually green.
With it, verified on 2026-08-05: **55 suites, 613 passed, 8 todo, 0 failures, in 10 seconds.** If you
ever see a mysterious failure, the first question is always *"did I source mobile-env?"*

**Where the code is — and the trap between the two copies.**

| Path | What it is | Has `node_modules`? |
|---|---|---|
| `/home/james/work/opanije` | The **full** clone, on `main` — WordPress, the mu-plugins, both apps | **No** |
| `/home/james/opanije-gate4` | A **sparse** worktree — only `apps/opanije-room` and `docs` | **Yes**, 677 packages |

**Neither one is ready as it stands, and this will bite you on Day 2.** The full clone has
everything except the installed dependencies, so `npm test` there dies with *"Preset jest-expo not
found."* The worktree has the dependencies but is sparse — from inside it, the WordPress estate and
`opanije-mobile` appear not to exist at all, which would quietly break Days 5 and 6.

**The fix, once, before Day 2** — work in the full clone and install into it:

```bash
cd /home/james/work/opanije
git log HEAD..origin/main --oneline    # ALWAYS run this before your first edit
git checkout -b build/stage-0-hygiene origin/main
cd apps/opanije-room && npm ci          # a few minutes, once
```

That `git log` line is not ceremony — branching from a stale branch silently discards everything
merged since, and the worktree you already have is sitting on a different branch
(`fix/room-guided-progression`).

Then confirm you are set up correctly before spending a day on it:

```bash
source ~/box/mobile-env.sh
npm test        # expect: 55 suites, 613 passed, 8 todo, 0 failed
```

If that shows 0 failures, everything else in this runbook will work.

---

# Day 1 — Stop the total-loss risk, and send the one message

> **AMENDED 2026-08-05 — D98 DEFERRED. Do not generate the production keystore today.** The founder
> deferred it. What remains true and unaffected: one machine still holds everything, a disk failure
> this afternoon still ends the company, and **the D16 credential and backup-key escrow is a separate
> item that D98's deferral did not touch.** The prompt below is kept in full so it is ready when the
> founder closes INPUT-91; if you run it today, run parts (2) and (3) only and skip the keystore.

**Morning: escrow.** Today, one machine holds the code, every credential, the backup key, and the
signing key, with no standby. A disk failure this afternoon ends the company. This has been the
estate's top overdue item for weeks (D16) and it takes hours, not days.

Ask Claude, exactly:

> I need to escrow our credentials off this machine. Walk me through, one step at a time: (1)
> generating a **production** Android release keystore for the app `com.opanije.room`, (2) copying it
> and the Borg backup repo key to two separate off-box locations, (3) restoring the backup passphrase
> and verifying a test restore actually works. Critical constraint: **never print, log, or echo any
> secret, passphrase, or key material to the terminal or to any file I might commit.** Tell me what
> to type; where a secret is involved, tell me to type it myself and don't ask me to show you.

~~Do the release keystore in this same session (D98).~~ **Deferred 2026-08-05.** The APK you have
today is a release variant signed with the **debug** key (`build-room-apk.sh:46`) — fine for handing
to testers, impossible to submit to Play. That remains the state of things until INPUT-91 is answered,
and it means **Stage 3's store upload is blocked, not merely unscheduled.** If you lose the production
key after publishing, the app can never be updated again — which is why deferring its creation is
cheap and deferring its escrow, once it exists, would not be.

**Afternoon: one WhatsApp message to Junior.** One, not three over three weeks. Draft it with Claude
in warm Brazilian Portuguese:

> Draft a WhatsApp message to Junior — my co-founder, a master percussionist, warm and direct
> register, Brazilian Portuguese, not corporate. Three things: (1) invite him to a recording day at
> my place, offer two dates in two weeks, explain it's simple — his drums, headphones, a few hours;
> (2) ask him to send a voice note describing how a first lesson with a total beginner actually runs,
> minute by minute; (3) ask whether he's OK with me using rough phone-quality audio of him internally
> while we build, nothing public. Keep it short enough to read on a phone.

**Then start the two slow clocks.** Nothing can compress these later:

- The Google Play developer account under the CNPJ (INPUT-40).
- One email to counsel commissioning a **single combined brief**: the replacement bilingual privacy
  policy, the Capture Day consent instrument, **and the GPL v3 question** (INPUT-85 — the repo is
  GPL v3 repo-wide and nobody in 145,680 words of estate noticed). One commission, three answers.

**End of day:** Junior has one message. Two clocks are running. **Keys do not yet survive a house
fire** — that was D98's job and it is deferred (risk #37, INPUT-91).

---

# Day 2 — Make the codebase the product's, and become the first human to hear it

```bash
source ~/box/mobile-env.sh
cd /home/james/work/opanije/apps/opanije-room
npm run gate          # lint + typecheck + test; expect 613 passed, 8 todo, 0 failed
```

Then, one prompt at a time — never all four at once:

> In `apps/opanije-room`: `createFakeRoomAudio()` is defined at `src/audio/engine.ts:107` and
> imported by production code at `src/app/AppRuntime.tsx:25`, used as a fallback `?? createFakeRoomAudio()`
> at line 245. Move it behind a test/dev-only guard so production code cannot reach it, and add a test
> that fails if it ever becomes reachable from production again. Then run `npm run gate`.

> `plugins/with-verified-apk.js` only guards Gradle tasks starting with `assemble`, and
> `scripts/verify-apk.sh` only scans `outputs/apk`. Google Play requires an AAB, built by `bundle*`
> tasks — so our RECORD_AUDIO permission check doesn't run on the artifact we'd actually ship. Extend
> both to cover `bundle*` and `outputs/bundle`. Also make `verify-apk.sh` not depend on the absolute
> path `$HOME/box/mobile-env.sh` so it could run in CI.

> Change the app's bundle identifier from `com.opanije.room.mockup` to `com.opanije.room`. Find
> every place it appears — app config, any keychain service string, deep links, test fixtures — and
> tell me what else the rename touches before you change anything.

> Run `node scripts/check-gates.mjs` and give me an inventory of every `GATE:` marker in non-test
> `src/`. Group them by who owns the decision — founder, counsel, or Junior — and for each, say in
> one plain sentence what is actually being asked.

**Then build it and put it on your phone:**

```bash
cd /home/james/work/opanije/apps/opanije-room
ROOM_VARIANT=release ./scripts/build-room-apk.sh
```

**Two traps in that one line, both of which will cost you an afternoon if you miss them.**

*Trap one: the wrong script.* `~/box/build-apk.sh` builds **`opanije-mobile`** — the *other*,
parked app. Room has its own script at `apps/opanije-room/scripts/build-room-apk.sh`. They are not
interchangeable and the failure is confusing rather than loud.

*Trap two: the default variant does not run.* `ROOM_VARIANT` defaults to `debug`, and React
Native's Gradle plugin **skips bundling the JavaScript for debug variants** — so a debug APK looks
for Metro on `localhost:8081` and dies with "Unable to load script" on a phone with no cable.
Fine at a desk, useless for a handset. **`ROOM_VARIANT=release` is what you want**, and in this Expo
template it is signed with the debug keystore, so it sideloads without any signing decision. (For
the emulator instead, add `ROOM_ABIS=all` — the default builds `arm64-v8a` only.)

The script also runs `npm run audio` and `npm run media` first and does an `expo prebuild`, so the
first build is slow and the `android/` tree it creates is generated output, not source. Never
hand-edit anything inside it.

Install the APK. **Play a full session.** The audio is synthetic placeholder — 72 generated WAVs
standing in for Junior — and it will sound thin and wrong. Play it anyway, twice.

**You are the first human being to ever hear this app.** `ACCEPTANCE.md:29` has carried criterion 1
as *"BLOCKED — owner: operator … NOT VERIFIED ON A DEVICE"* this entire time. Write down, dated, in
`BUILD-LOG.md`, what it actually felt like in your hands. That note is the ledger's first primary
evidence and nobody else can produce it.

> **AMENDED 2026-08-05 — you are no longer the first.** A tester already played this on a device and
> scored it **0/10**: did not know what to do, saw no game mechanic, could not work out how to
> interact (ledger row 59). Your Day 2 note is still the founder's own primary evidence and still
> worth writing — but write it knowing what to look for, and write down specifically **what you had
> to already know in order to play it at all.** That list is the door redesign's specification.

**One thing you will notice, and it is the point of Day 3.** The echo loop, the fade, and the closing
screen probably will not appear. They are gated behind `playLayerEnabled`, false unless
`EXPO_PUBLIC_ROOM_DEMO` is set. To see the actual product:

```bash
EXPO_PUBLIC_ROOM_DEMO=1 ROOM_VARIANT=release ./scripts/build-room-apk.sh
```

Build it both ways and play both. **The difference between those two builds is the difference between
a drum toy and Opanijé.**

---

# Day 3 — Turn the product on, and order the kit

> **AMENDED 2026-08-05 — D94 is PENDING. Do not make this change yet.** The founder held it for a
> fuller account before ruling. The prompt below is correct and ready; it runs the day D94 is
> ratified and not before. If D94 is rejected, Day 3's morning is spent on the door redesign instead
> (INPUT-92), which the 0/10 makes the more urgent work either way.

This is D94, the heaviest decision in the block, and today is when it becomes code.

> `playLayerEnabled` in `src/app/AppRuntime.tsx:239-242` is false unless `__DEV__` or
> `EXPO_PUBLIC_ROOM_DEMO`. It gates the echo loop, the fade/thinning model, and the three-facts
> closing screen — which are the actual product. I want the play layer ON in production builds.
> Before you change anything: list every test that asserts the play layer is absent by default
> (`src/app/__tests__/closing.test.tsx:234` is one), and every route that is demo-only. Then make the
> change and flip those tests to assert presence. Run `npm run gate`.

Build, install, play. **This is the first time the game exists on a phone.**

**Also today:** draft the consent instrument with Claude and send it to counsel alongside the privacy
brief — interactive and game use licensed, isolated stems and one-shot sampling in scope, broad the
first time, bilingual, to be recorded in Junior's own voice and signed on paper *before cameras roll*.
This is INPUT-89/INPUT-22, **rank 1 of the estate's six irrecoverable items.** Nothing else in these
ten days is as unrecoverable as getting this wrong.

**And order the kit** — USB interface, two mics, stands, headphones, ~R$2–3k, inside the existing M0
earmark. It has to arrive before Day 8.

---

# Day 4 — Ratify the free set, then build the pipeline against fakes

**Morning, founder hat on, one hour not one week.** Ratify the free set (INPUT-80/INPUT-86). This
plan's recommendation: **Ijexá, two parts (agogô + one drum part), two speeds, with the play layer
on.** Write one line in `BUILD-LOG.md`.

Take the hour seriously: red line #5 means **anything given free is given permanently.** You are
deciding what Opanijé gives away forever. But take one hour, not one week — the estate's failure mode
is deliberation, not haste.

**Afternoon: the pipeline, built before the recording day, against fake stems.** This is the most
important sequencing call in the whole plan.

> I need a pipeline that turns raw recorded stems into what the app consumes. Read
> `apps/opanije-room/scripts/audio-spec.json`, `scripts/make-placeholder-audio.py`, and
> `scripts/publish-manifest.mjs` first, and explain to me in plain language what the app expects and
> how the existing placeholder generator produces it.
>
> Then build a script that takes N real stem WAVs plus a timing spec and emits the same ladder mixes
> and `AUTHORED-TIMING` grids the app already consumes. Two hard constraints: (1)
> `make-placeholder-audio.py:287-289` hard-fails while an arrangement gate is unresolved — tell me
> exactly what decision that gate is waiting on so I can settle it; (2) `assets.test.ts:490-523`
> enforces a sha256 provenance chain that fails closed when assets change, so the pipeline must end
> by regenerating the manifest. **Never disable that test to make a build pass.**
>
> Prove the whole thing end to end using fake stems — I'll record myself clapping four separate
> tracks.

Record yourself clapping four parts. Run the pipeline. Build. **Hear your own claps come out of the
app as a battery.** When that works, Capture Day has somewhere to land.

That gate the generator is waiting on is **INPUT-87**. Settle it this week — with Junior by voice
note if it is a form question. If it is not settled, Day 9 does not happen.

---

# Day 5 — ~~The web room~~ **Withdrawn: D96 REJECTED**

> **AMENDED 2026-08-05.** The founder rejected D96. The web room is not the iOS strategy and not the
> primary distribution surface, so this day's justification is gone. **Do not spend Day 5 deploying
> `/toca`.**
>
> **What to do with the day instead, in priority order:**
>
> 1. **The door redesign** (INPUT-92, ledger row 59, risk #35). This is the only measured failure in
>    the estate and it is the thing standing between you and Stage 2. It is a better use of a day
>    than any surface question.
> 2. **Answer INPUT-90** — with D96 rejected, Release 1 has no iOS path and no no-install
>    tap-to-play surface, and Junior's voice note has nothing to point at that does not require an
>    Android install. That question should be settled before Stage 3 is planned, not during it.
>
> The original day is preserved below because the ruling was against the web room as *strategy*, not
> against the web export as an artifact. If INPUT-90's answer brings it back in some other role, the
> instructions still work.

## Original Day 5, retained for reference

The single highest-leverage build day in the ten, because the web room is how anyone will ever find
this (D96).

> Room uses `react-native-web` 0.21.0 and `expo export --platform web` has been run before —
> `ACCEPTANCE.md:29` records it. Export it to web, then deploy the static bundle behind
> `opanije.com/toca` on the VPS. Our nginx config is version-controlled in the `nginx` repo and
> deploys by PR merge — follow that path, do not hand-edit the live tree. Then walk every route in a
> browser and fix what breaks. I expect at least: audio needing a user gesture to unlock on first
> tap, a landscape prompt for the drum, and touch targets sized for a phone.

By end of day, a link you can send to anyone plays a session with placeholder audio.

**Do not publicize it.** Screens stay out of public marketing until the GUI design filing decision at
Stage 3. This is plumbing-proof, not a launch.

---

# Day 6 — Lift the spine (dormant)

> `apps/opanije-mobile` in this repo is formally parked (`SITE-SSOT.md:228`, DN-3 "do not build
> against it"), its CI was disabled after 30 consecutive typecheck failures, and its `node_modules`
> is absent — so treat it as a **reference implementation, not working code.** Read these four things
> and port them into `apps/opanije-room` behind config flags, all dormant, with mock mode staying the
> default: (1) the hand-rolled PKCE Google auth flow — note there is no OAuth SDK, it's built on
> `expo-web-browser` + `expo-crypto`; (2) `expo-secure-store` session handling; (3) the repository
> factory (mock / http / factory); (4) the `expo-video` signed-playback pattern. Add the
> `/auth-return` route. If any one of them fights you for more than two days, tell me and we write it
> fresh against Room's conventions instead.

Then archive `opanije-mobile` with a README pointing at Room. Do **not** delete it — its iOS project
is the estate's only iOS asset and costs nothing to keep.

```bash
npm run gate
ROOM_VARIANT=release ./scripts/build-room-apk.sh
```

The APK must still verify clean — no new permissions. If `RECORD_AUDIO` ever appears, the build is
supposed to fail. That tripwire is red line #4 in CI form.

---

# Day 7 — Capture Day rehearsal, alone

Every problem you find today is a problem Junior never sits through. His hours are the scarcest
resource in the company; yours are not.

Rig the kit exactly as it will be on the day. Record yourself layering claps over a reference in
headphones — four separate parts, isolated, the way Junior will. Run them through Day 4's pipeline.
Render. Build. **Hear it in the app the same afternoon.** If any link in that chain breaks, today is
the day it costs nothing.

Then, with Claude, produce the run-sheet from `PLAN-01-BUILD.md` Stage 1's capture manifest — every
pass, every count-in, the partition questions written out as plain questions in Portuguese, the reel
shot list. Print two copies of the consent instrument. Charge everything. Clear the memory cards.

---

# Day 8 — Capture Day

**Consent first. On paper, and in his own voice, before anything rolls.** Not after the first take
because the room felt good. This is rank 1 of six by irrecoverability and it is not recoverable later
without re-consenting a master and reopening commercial terms from a weak position.

Then the run-sheet, in order: reference pulse → isolated per-part stems (layered to headphones, never
a mixed performance you plan to separate later) → four solfejo passes locked to the battery → the
stroke one-shot library with velocity layers → 10–12 count-ins including the return-after-absence
variant → the welcome → the two next-step invitations, **price-free** → three seeded Perguntas
answers → the partition item by item, written down in his words as he speaks it → a dozen 30-second
reel clips last, while the room is warm.

Those reel clips are Stage 3's entire content calendar and they cost twenty minutes at the end of a
day that is already set up. Do not skip them because you are tired.

**Back up every file to two locations before dinner.** Not tomorrow morning.

---

# Day 9 — Junior's battery, in your hands

Run the pipeline on the real stems. Replace the 72 synthetic placeholders. Regenerate the manifest.

```bash
source ~/box/mobile-env.sh
cd /home/james/work/opanije/apps/opanije-room
npm run publish:manifest
npm run gate
ROOM_VARIANT=release ./scripts/build-room-apk.sh
```

The provenance test will fail until the manifest is regenerated. That is correct behaviour — it is
the mechanism proving the audio in the build is the audio Junior consented to. Regenerate; never
disable.

Install. Play.

**Somewhere around mid-afternoon, the app plays Junior's actual battery and your finger keeps his
groove alive.** That is the moment this company has been walking toward for 145,680 words.

Send it to nobody yet. First, write the dated note — **row 54**, the plan's riskiest hypothesis:

> Does scheduled audio feel like *playing*, or does it feel like miming along to a recording?

Answer honestly, in writing, dated. An honest no here is worth more than a hopeful yes, because it is
cheap to act on today and ruinous to discover at Stage 3.

---

# Day 10 — Junior meets the product, and the pilot is loaded

Sit with him — in person if you can, on a call with the APK installed if you cannot. He sees the
drum, the echo loop, the fade, the closing screen, on a real phone, with his own sound coming out of
it.

**Charter §9 item 10 makes this a gate, not a courtesy:** no screen-drum surface ships without Junior
having seen it. And under D94 what he is approving is the *game*, not a drum.

Gather in this one sitting, around this one object, what the estate has had open for weeks — write
his answers in **his words**, not your paraphrase:

| Input | The question, in plain language |
|---|---|
| **INPUT-69** | Does this look like his teaching? |
| **INPUT-79** | Is the rendered echo a form he sanctions? |
| **INPUT-41** | Is the fixed ladder of speeds musically acceptable? |
| **INPUT-62** | Are the engagement surfaces in a form he approves? |
| **INPUT-88** | With the battery being him layered four times, what should the presence surface show? (C23) |
| **Row 52** | Does the play layer read as *musical information*, or as a *verdict on the player*? |

That last one is the whole grading constitution, asked of the one person whose answer counts.

**Then recruit the ten testers** from his network and yours, and schedule them across the following
week. End the day by writing the ledger's first dated rows and the week-3 plan.

---

## Where you are, ten days in

- Keys that cannot be lost, and a production keystore that can actually ship to a store.
- A codebase with one owner, one bundle ID, and the product switched **on**.
- **Owned instructional audio, for the first time in the company's existence.**
- A working instrument on two phones. ~~and a URL~~ — **no URL: D96 REJECTED.**
- The master's assent gathered around a real object instead of a document.
- Ten humans booked.
- Two ledger rows with dates on them — more measured evidence than the previous 145,680 words
  produced.

Every red line intact.

---

## The three ways these ten days fail

**1. You start reading the estate again.** 145,680 words is a comfortable place to hide from a
terminal. The Charter is two pages and it is the only document you need open. Everything else is
frozen for a reason (D88).

**2. You wait for Junior.** His latency is uncontrolled and yours is not. Every ask is front-loaded
to Day 1 precisely so that no build day is ever blocked on a reply. If he goes quiet, keep building —
Days 2 through 7 need nothing from him.

**4. You spend the ten days on the product and none of them on the door.** Added 2026-08-05. The
only measured fact about this app is that a first-time user could not work out how to use it. Every
day above assumes the door works. It does not.

**3. You try to fix the audio engine.** The moment you find yourself reading about buffer sizes,
AAudio, Oboe, or latency calibration, **stop and reread the never-attempt table in
`PLAN-01-BUILD.md`.** The answer to every audio problem in this architecture is another pre-rendered
file. That constraint is not a limitation you are working around — it is the design decision that
makes this product buildable by one person.
