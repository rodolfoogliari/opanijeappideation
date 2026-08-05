# VERIFICATION — design plan claims vs. actual code

**Date:** 2026-08-05
**Method:** read-only inspection. No file modified.
**Primary tree:** `/home/james/opanije-gate4` — git worktree, branch `fix/room-guided-progression`, HEAD `4dde6752`, working tree **clean**.

## Scope correction that affects everything below

`/home/james/opanije-gate4` is a **sparse checkout**. Its sparse spec
(`/mnt/i/opanije-pr1081/.git/worktrees/opanije-gate4/info/sparse-checkout`) admits only:

```
/apps/opanije-room/
/docs/
```

So `apps/opanije-mobile` and the whole WordPress side (`public_html/`) **are not present in this
worktree**, although they do exist in the repository (`git ls-tree origin/main` shows
`apps/opanije-mobile`, `public_html`, `scripts`, `tools`, `.github`).

Claims 9, 11, 12 and 13 were therefore verified against the full clone
**`/home/james/work/opanije`** (branch `main`, HEAD `99991cef`). That HEAD is three commits behind
gate4's branch tip; all three are Room/docs commits, so the mobile and WordPress evidence is
current.

---

## Claim 1 — Room exists, Expo/RN, ~24,000 lines, ~493 tests

**PARTIAL.** Existence and framework: TRUE. Line count: TRUE only if tests are counted as source.
Test count: **understated by ~26%**.

- `/home/james/opanije-gate4/apps/opanije-room/package.json:3` — `"main": "expo-router/entry"`;
  deps `expo 57.0.7`, `react-native 0.86.0`, `react 19.2.3`, `expo-router 57.0.7`. Expo/RN: TRUE.
- **Lines in `src/` (.ts/.tsx), everything:** **24,066** across 145 files. Matches "~24,000" exactly.
- **Lines excluding tests:** **12,443**. So barely half of the "24,000 lines of source" is
  implementation; the rest is test code.
- **Test files:** 55 (`npx jest --listTests` → 55).
- **Actual test count:** `npx jest` reports **621 total — 612 passed, 8 todo, 1 failed** in 10.3 s.
  Raw `it(`/`test(` occurrences in test files: 472 (the gap is `test.each` expansion).
- The claimed **493** matches neither figure. The real number is **621**.

### The one failing test — and why it is not a code defect

```
● native app configuration › executes the generated verifier task with real Gradle
  Expected substring: "BUILD SUCCESSFUL"
  Received string:    "ERROR: JAVA_HOME is not set and no 'java' command could be found in your PATH."
```
`/home/james/opanije-gate4/apps/opanije-room/src/__tests__/appConfig.test.ts:154`

The test has a skip-guard at lines 142–152 that catches the *Gradle-daemon-unreachable* case, but
**not** the *no-JDK* case. Re-run after `. ~/box/mobile-env.sh` (`JAVA_HOME=/home/james/android-toolchain/jdk-17.0.19+10`):
**11/11 pass**. So the suite is **621/621 green with the toolchain env sourced, and red without it.**

---

## Claim 2 — ~13 screens, bilingual PT/EN

**TRUE.**

Expo Router, file-based, under `/home/james/opanije-gate4/apps/opanije-room/src/app/`.
**Exactly 13 route files** plus `_layout.tsx` (not a screen):

| Group | Routes |
|---|---|
| Signed-out (`_layout.tsx:31-34`) | `index.tsx`, `signin.tsx` |
| Signed-in (`_layout.tsx:35-45`) | `intention.tsx`, `welcome.tsx`, `choose-part.tsx`, `room.tsx`, `drum.tsx`, `closing.tsx`, `ending.tsx`, `home.tsx`, `caderno.tsx` |
| Demo-only (`_layout.tsx:46-52`) | `review.tsx`, `past-the-door.tsx` |

Guarding is real `<Stack.Protected>`; the demo group is gated on
`demonstrationSurfacesEnabled(__DEV__, process.env.EXPO_PUBLIC_ROOM_DEMO) && process.env.NODE_ENV !== 'test'`.
Route names mirrored in `src/runtime/routeTree.ts:2-8` and asserted against the filesystem in
`src/__tests__/route-boundary.test.ts:6-20`.

**i18n:** a single hand-written table, `/home/james/opanije-gate4/apps/opanije-room/src/i18n/strings.ts`
(713 lines). No i18next / no `Intl` library. `interface Strings` (lines 21-239, 18 nested groups,
~154 leaf fields), then two full literals — `const pt: Strings` at **line 240**, `const en: Strings`
at **line 436** — joined by `const TABLES: Readonly<Record<Locale, Strings>> = { pt, en }` (line 632),
read via `stringsFor(locale)` (635-637). **Both locales genuinely populated: 172 key-lines each.**
Neither is a stub. Enforced structurally by `src/__tests__/i18n.test.ts:48-59` (key equality across
tables + non-empty `/\S/u` on every leaf). Locale resolution at `strings.ts:665-670` (`pt*` → pt,
else en) with a persisted override `LOCALE_OVERRIDE_KEY = 'opanije.locale-override.v1'` (line 679)
surfaced by `src/components/LocaleControl.tsx`. Separate timed-subtitle path in `src/i18n/subtitles.ts`.

---

## Claim 3 — the five mechanics

### 3a. Landscape screen drum with zones — **TRUE** (one precision caveat)

Orientation lock, `/home/james/opanije-gate4/apps/opanije-room/src/app/drum.tsx:67-80`:

```ts
void ScreenOrientation.getOrientationLockAsync().then((lock) => {
    previousLock = lock;
    return mounted
        ? ScreenOrientation.lockAsync(ScreenOrientation.OrientationLock.LANDSCAPE)
        : ScreenOrientation.lockAsync(lock);
}).catch(() => setOrientationError(true));
```

Prior lock restored on unmount (`drum.tsx:78`); user-visible recovery if the lock throws
(`drum.tsx:156-177`). `app.json:6` sets global `"orientation": "default"`, plugin
`expo-screen-orientation` at `app.json:26`; `/drum` is the only landscape surface — `ScreenOrientation`
appears in no other source file.

Zone surface, `/home/james/opanije-gate4/apps/opanije-room/src/components/ZoneField.tsx:86-148` —
flex container, one `<Pressable style={{ flex: 1, minHeight: 64 }}>` per zone, each firing
`onStrike(index, event?.nativeEvent.timestamp ?? Date.now())` (109-111). Visual gaps drawn on an
inner `pointerEvents="none"` View (91-99, 115-131) so gaps create no dead hit area.
Zone inventory is real domain logic: `src/domain/zones.ts:19-30` `zonesForDial(part, dialStop)`
clamps to 3 hand syllables (Pá/Tum/Dum) or 2 stick (Ti/Tá), wired live to a dial at `drum.tsx:139-155`.

**Caveat:** there is no *geometric* hit-testing — no `locationX/locationY` math, no zone rect table.
Zones are proportional flex children. Functionally equivalent for a divided surface, but "zone
hit-testing code" in the coordinate sense does not exist.

### 3b. Echo loop — voice withdraws and returns — **TRUE as logic, OFF in a student build**

`/home/james/opanije-gate4/apps/opanije-room/src/domain/ladder.ts:9-14`:
```ts
export type GuidedRehearsalPhase = 'learner-alone' | 'voice-return';
```
Transition chain, `ladder.ts:119-125`:
```ts
if (state.phase === 'voice-over') return state.guidedRehearsal ? 'learner-alone' : 'battery';
if (state.phase === 'learner-alone') return 'voice-return';
if (state.phase === 'voice-return') return 'battery';
```
The withdrawal/return is a real asset swap — `renderEntryState()` at `ladder.ts:79-83` maps
`'learner-alone' → 'battery'` (render **without** voice) and `'voice-return' → 'voice-over'`
(render **with** voice); `playRung` (85-117) resolves a different URI per phase. Re-entry via
`'request-rehearsal'` (195-208, 257-267), surfaced as a replay button at `src/app/room.tsx:296-317`.
Bilingual copy at `strings.ts:288-289` (`learnerAlone: 'Sua vez'`, `voiceReturn: 'Juntos outra vez'`)
and `:484-485`.

**Gate:** `guidedRehearsal` is set from `playLayerEnabled` (`src/runtime/useRoomSession.ts:173, 688, 903`),
and `playLayerEnabled` is false in any ordinary build — `src/runtime/AppRuntime.tsx:239-242`:
```ts
const playLayerEnabled = demonstrationEnabled ?? (
  process.env.NODE_ENV !== 'test'
  && demonstrationSurfacesEnabled(__DEV__, process.env.EXPO_PUBLIC_ROOM_DEMO));
```
In a student build the loop is `voice-alone → voice-over → battery` with no withdraw/return.

### 3c. Fade / thinning when unfed — **PARTIAL**

Real attenuation exists, per authored cycle — `/home/james/opanije-gate4/apps/opanije-room/src/runtime/useRoomSession.ts:335-349`:
```ts
const fed = tapRef.current?.completeCycle(cycleIndex);
if (fed === undefined || !playLayerEnabled) return;
if (presenceArmedRef.current) {
    const nextPresence: SelectedPartPresence = participatedInCycleRef.current ? 'full' : 'thin';
    ...
    audio.setSelectedPartPresence(nextPresence);
```
Backed by real audio gain — `src/audio/engine.ts:256-259` `SELECTED_PART_VOLUMES = { full: 0.6, thin: 0.2 }`,
applied at `engine.ts:442-448` — and real visual thinning (`ZoneField.tsx:122-127`).

Why only PARTIAL — five material gaps:
1. **Binary, not a decay curve.** Two states only, recovering fully on the very next cycle.
2. **No cross-session "unfed" decay at all.** Nothing stores a last-practice timestamp and thins over
   hours or days. `tap.ts:92-94 isKeepAliveActive` uses a 2-second window and is not used for presence.
3. Attenuates **only the selected-part companion**, never the authored battery — forbidden by design
   (`useRoomSession.ts:8-13`).
4. Same demo gate as 3b (`!playLayerEnabled` → early return at line 336).
5. **The feeding measure is computed and discarded.** `tap.ts:82-83` computes
   `PROVISIONAL_FED_CYCLE_PROPORTION = 0.5` of grid positions landed, but line 337 uses `fed` only as
   an `undefined` guard — presence is decided by raw "did you touch anything at all".

### 3d. Post-round closing: three facts + personal best — **TRUE, demo-gated**

`/home/james/opanije-gate4/apps/opanije-room/src/app/closing.tsx:238-286` renders exactly three fact
tiles — `cyclesWithYou` (245-252), `longestHold` (253-262), `setting` (263-272) — plus a fourth
`best` tile (273-285). `settingDescription` at `closing.tsx:54-66` composes part · N drums · BPM · zones.

Personal best is genuinely persisted and monotonic: `src/domain/playLayer.ts:346-369`
(`recordClosedSession` advances per-setting bests, marks `best` only when
`segment.longestHold >= previous`), stored under `opanije.play-ledger.v1` (playLayer.ts:82, 433-440),
with an at-most-once celebration claim `consumeCloseCelebration` (390-410) driving a
`personal-best.wav` one-shot (closing.tsx:172-219).

**Gate:** `closing.tsx:151` — `const closeResult = currentFacts !== null && runtime.playLayerEnabled ? … : null`.
In a student build Closing shows only a title and a Done button. Its own test asserts this:
`src/__tests__/screens/closing.test.tsx:234` expects `cyclesWithYou` to be null.

### 3e. Caderno — **TRUE, fully real, ungated**

- Route `/home/james/opanije-gate4/apps/opanije-room/src/app/caderno.tsx:91,137`.
- Persistence `src/domain/caderno.ts:74` — `CADERNO_ENTRIES_KEY = 'opanije.caderno-entries.v2'`,
  written at `:194`, crash-repair journal at `:262-271`, read back at `:257-260`.
- Real device storage: `src/platform/storage.ts:1-24` (AsyncStorage).
- Forgery resistance is designed in: `caderno.ts:29-42` issues an opaque `HumanPracticeToken` only
  past `DEFAULT_CADERNO_ENTRY_THRESHOLD = { completedCycles: 3 }` (`:12-14`); `writeCadernoEntry`
  (53-71) rejects any id ≠ `practice-${evidence.sessionId}`; `commit()` throws
  `'Caderno credit requires observed authored playback.'` (`caderno.ts:176`) unless the private
  `#checkpointObservedPlayback` has run.
- Bilingual entry text at `strings.ts:640-655`.

---

## Claim 4 — `createFakeRoomAudio()` importable from production, forging a Caderno entry

**PARTIAL — the import is real and it does ship, but nothing at runtime selects it.**

**Where defined:** `/home/james/opanije-gate4/apps/opanije-room/src/audio/engine.ts:107`
```ts
export function createFakeRoomAudio(): FakeRoomAudio {
```
in a **non-test** module (`engine.ts` also holds the real `createRoomAudio` at `:273`). The
`FakeRoomAudio` interface (`:95-105`) exposes `advance(ms)`, `completeOneShot()`, `log`,
`observerCount()` — i.e. it can fabricate playback time.

**The import chain into production:**
1. `src/audio/engine.ts:107` — exported from production module.
2. `src/runtime/AppRuntime.tsx:25` — **module-scope import in a production file**:
   `import { createFakeRoomAudio, type RoomAudio } from '@/audio/engine';`
3. `src/runtime/AppRuntime.tsx:245` — **live fallback**:
   ```ts
   const [roomAudio] = useState<RoomAudio>(() => audio ?? createFakeRoomAudio());
   ```
4. `src/app/_layout.tsx:70-73` — the only production caller of `AppRuntimeProvider`, and it
   **always** supplies the real adapter:
   ```ts
   const audio = useMemo(() => createRoomAudio({ createAudioPlayer, setAudioModeAsync: … }), []);
   ```
   passed at `_layout.tsx:78`.

**Verdict detail:**
- **Importable from production code: TRUE.** Steps 1–2 are unambiguous. Because Metro/Hermes does not
  tree-shake by default, `createFakeRoomAudio` is **in the shipped bundle**.
- **A dead-code fallback exists: TRUE** (step 3). It is not merely a type.
- **Reachable at runtime: FALSE.** There is no env var, debug menu, deep link or config switch that
  substitutes the fake. Grep confirms `AppRuntimeProvider` has exactly one production call site.
  Reaching the fake requires **editing `_layout.tsx`** — i.e. a source change, not an exploit.
- **Forgery consequence, if the fake were substituted: REAL.** `useRoomSession` derives session
  evidence from whatever `RoomAudio` it is handed; the fake's `advance()` can mint cycle boundaries.
  The Caderno's defences (`caderno.ts:176`, the private `#checkpointObservedPlayback`, the
  `observedRoom()` closure at `:145-158`) all guard against *exported callers manufacturing evidence* —
  they do **not** authenticate the audio engine itself. So the trust boundary really does sit at the
  `audio` injection point.

Net: the plan identifies a genuine architectural weak point and a genuine production import, but
overstates it as an available path. It is a source-edit-away hazard, not a live one.

---

## Claim 5 — `verify-apk.sh` guards only `assemble*`; an AAB escapes

**TRUE.**

`/home/james/opanije-gate4/apps/opanije-room/scripts/verify-apk.sh` (3,825 bytes) itself just takes an
APK path and runs `aapt2 dump permissions`, checking `RECORD_AUDIO`, `CAPTURE_AUDIO_OUTPUT`, `CAMERA`,
`ACCESS_FINE_LOCATION`, `ACCESS_COARSE_LOCATION` are absent plus `assets/index.android.bundle` present.

The **enforcement wiring** is the Expo config plugin
`/home/james/opanije-gate4/apps/opanije-room/plugins/with-verified-apk.js`, whose injected Gradle
block ends:

```groovy
tasks.configureEach { task ->
    if (task.name.startsWith("assemble") && task.name != "assemble") {
        task.finalizedBy(verifyOpanijeApks)
    }
}
```

Only `assemble*` is finalized. `bundleRelease` / `bundleDebug` (the AAB tasks Play Store submission
uses) are **not** matched, so an AAB is produced with no permission check. The verifier also only
scans `layout.buildDirectory.dir("outputs/apk")` — AABs land in `outputs/bundle/`, so even a manual
invocation would find nothing.

Two further gaps the script's own header admits:
- A stale generated `android/` tree made before the plugin existed is not covered until regenerated.
- The verifier enforces only the five listed red lines; `SYSTEM_ALERT_WINDOW` and legacy-storage
  declarations are printed for human review, not failed.

And one portability defect: `verify-apk.sh` sources `"$HOME/box/mobile-env.sh"` unconditionally when
`OPANIJE_MOBILE_ENV` is unset — a workstation-specific absolute path baked into a repo script.

---

## Claim 6 — build script and a recently built ~98 MB APK

**TRUE.**

**Build script:** `/home/james/opanije-gate4/apps/opanije-room/scripts/build-room-apk.sh` (6,941 bytes,
executable, mtime 2026-08-04 10:44). It computes `GRADLE_TASK="assemble${Variant}"` (line 59), runs
`npm run bundle` (line 92), embeds a production Hermes bundle for debug variants (99-109), invokes
Gradle at line 141 and calls `verify-apk.sh` at line 146. Notes at 37-53 explain that debug variants
skip JS bundling, hence the manual embed. `ROOM_VARIANT` selects `release` (Gradle bundles JS) or
`debug` (default). Companion notes at `scripts/build-apk-notes.md`.

**The artifact:**

| Path | Size | Date |
|---|---|---|
| `/home/james/opanije-gate4/apps/opanije-room/android/app/build/outputs/apk/release/app-release.apk` | **102,984,846 B = 98.2 MiB** | **2026-08-04 17:44** |

`output-metadata.json` alongside it: `applicationId "com.opanije.room.mockup"`, `variantName "release"`,
`versionCode 1`, `versionName "0.1.0"`, `minSdkVersionForDexing 24`, with baseline profiles for
minApi 28-30 and 31+.

A copy of the same build sits at `/mnt/f/downloads/opanije-room-mockup-dev.apk`
(102,983,822 B, 2026-08-04 17:12). Older Room APKs: `/mnt/f/claude-temp/opanije-room-pass2-release.apk`
(94.9 MB, 08-03), `opanije-room-pass2.apk` (135.6 MB, 08-03), `opanije-room-mockup-31880b69.apk`
(94.9 MB, 08-02), `/home/james/scratch/opj-frontend-final/opanije-room-mockup-dev.apk`
(119.0 MB, 08-02).

Two things a plan should note: it is the **release** variant (not debug), and per `build-room-apk.sh:46`
"in this Expo template, [release] is signed with the debug" keystore — so it is **not** a
store-signable artifact. `android/` is gitignored, so the APK is untracked build output.

---

## Claim 7 — react-native-web capable, web export has been run

**TRUE.**

- `package.json`: `"react-native-web": "0.21.0"`, `"react-dom": "19.2.3"`.
- Two scripts run a real web export:
  - `scripts/walk-web-routes.sh:50` — `npx expo export --platform web --output-dir "${export_dir}"`
  - `scripts/capture-web-widths.sh:45` — same
- **Evidence it has actually executed** — `docs/ACCEPTANCE.md:29`: "The production web export has also
  **EXECUTED IN A BROWSER**: every unauthenticated route reached the signed-out guard, `/review` was
  absent from the production route set, and Chrome reported no uncaught JavaScript error."
  Corroborated at `docs/ROUTE-TO-DONE.md:78` (checked box), `docs/DEVICE-NOTES.md:25-27`,
  `docs/DEVELOPING.md:91`, `README.md:127`.

**Caveats:** the export dir is a `mktemp -d` and is cleaned up, so **no web export output persists on
disk**. The committed `dist/` (45 MB, 129 assets) is an **Android** export — `dist/metadata.json`
begins `{"version":0,"bundler":"metro","fileMetadata":{"android":{"bundle":"_expo/static/js/android/entry-….hbc"…`
with no `web` key, and `npm run build` is `expo export --platform android`. The walk script's own
header (lines 4-11) warns it proves only that the export *executes* and routes — "nothing about
Android, audio, layout, accessibility, lifecycle, input, GPU, or device performance" — and it drives
Chrome on the Windows side via `/mnt/c/Program Files/Google/Chrome/Application/chrome.exe`.

---

## Claim 8 — scheduled-not-triggered audio from pre-rendered files; 72 synthetic placeholders

**PARTIAL — the count is exactly right; "not triggered" is too absolute.**

**Library:** `expo-audio ^57.0.0` (`package.json:14`). No `expo-av`, no `react-native-sound`.
**Engine:** `/home/james/opanije-gate4/apps/opanije-room/src/audio/engine.ts` (523 lines), two
implementations behind one `RoomAudio` interface — `createFakeRoomAudio()` (:107) and
`createRoomAudio(api)` (:273). `allowsRecording: false` is hard-coded at `engine.ts:302-304` and the
interface has **no capture method**.

**Scheduled path (the music) — TRUE.** `playLoop`/`swapLoop` (`engine.ts:392`, `:416`) set
`player.loop = true`, `seekTo(0)`, `play()`. Cycle boundaries are **observed, not timed** —
`observeLoop` (`:341-389`) subscribes to `playbackStatusUpdate` and reconstructs elapsed media time
from `status.currentTime`, `playbackRate` and `didJustFinish`, with a wrap-tolerance check (`:366-374`)
so an arbitrary seek cannot mint a false cycle. Tap judgement is grid-relative:
`useRoomSession.ts:753` → `src/domain/tap.ts:101-122` `nearestGridStrike` compares tap time against
`authoredCycle * cycleMs + gridStrike.atMs`, ±150 ms (`tap.ts:3`). Level change is a whole-file swap
at the cycle boundary (`useRoomSession.ts:433-435`), never a runtime mute.

Precision: there is **no `setTimeout` scheduler and no seek-to-offset in a long file.** Each render is
one authored cycle, looped natively; "scheduled" means pre-rendered material plays continuously and
the app *reads back* phase.

**Triggered path — REAL and bounded (four sites).** The engine's own docblock (`engine.ts:6-10`) says
one-shots are bounded to the count-in, a D77 real-strike sample, and a post-ending cue. In practice:
1. **Wrong-zone / outside-window strike** — `useRoomSession.ts:221-234`:
   ```ts
   const sampleUri = `assets/audio/stroke-${zone.syllable.stroke}.wav`;
   …
   await audio.playOneShot(source);
   ```
   This *is* per-tap sample triggering, gated by `tap.ts:48,56` to fire only when the tap misses or
   the zone mismatches. A correct in-window tap plays nothing — the physical drum supplies it.
2. Count-in — `useRoomSession.ts:423-424`.
3. UI control click — `src/components/AudiblePressable.tsx:8,14`.
4. D80 personal-best cue — `src/app/closing.tsx:210`.

The accurate statement is: **the music is never triggered per tap; a miss is.**

**Timing files — TRUE and better than claimed.**
- `/home/james/opanije-gate4/apps/opanije-room/assets/audio/AUTHORED-TIMING.json` (1,884 B) — the grid.
  Schema `rhythmId` / `timingByPart` (part → array indexed by tempo step) / `fullBatteryCloseTiming`:
  ```json
  "part-hand": [ { "cycleMs": 8000,
    "gridOffsetsMs": [0,1000,2000,3000,4000,5000,6000,7000] }, … ]
  ```
  Three tempo steps per part: `cycleMs` 8000 / 6000 / 4800, 8 evenly-spaced offsets.
  Consumed at `src/data/catalog.ts:25,86`, validated into rungs at `src/domain/manifest.ts:125-177`.
  Generator comment `make-placeholder-audio.py:299-300`: "BPM remains metadata; application timing is
  loaded only from this authored artifact" — confirmed, the grid derives from sample-domain render
  positions, not from BPM at runtime.
- `/home/james/opanije-gate4/apps/opanije-room/scripts/audio-spec.json` (1,174 B) — generation input +
  provenance: `provenanceVersion 1`, `synthesisAllowlist: ["sine-oscillator","seeded-white-noise",
  "one-pole-low-pass","exponential-envelope"]`, `expectedAssetSetSha256`, `generatorSha256`,
  `rhythmId "toque-livre"`, `beatsPerCycle 8`, `tempoStepsBpm [60,80,100]`, `levels [1,2,3,4]`, and an
  explicitly **unresolved** `supportArrangement` gate.
- `/home/james/opanije-gate4/apps/opanije-room/assets/audio/GENERATED.json` (31,530 B) — 72 file
  entries with per-file sha256, 58 compositions, `specSha256`, `generatorSha256`, and the honest
  string `"evidence": "allowlisted deterministic synthesis inputs; not acoustic proof"`.
- `/home/james/opanije-gate4/apps/opanije-room/src/data/audioAssets.ts` — generated `require()` map.

**Assets — exactly 72, 100% synthetic. TRUE.**

Location: `assets/audio/` (9 files) + `assets/audio/toque-livre/` (63 files). Count confirmed three
ways: `find -name '*.wav' | wc -l` = 72; `GENERATED.json.files.length` = 72; test assertion
`src/__tests__/assets.test.ts:490` `expect(generated.files).toHaveLength(72)`.

Breakdown: 24 ladder renders (2 parts × 4 levels × 3 tempos), 24 `voice-over-*`, 6 `voice-alone-*`,
6 `selected-part-*`, 3 `full-battery-tempo-*`, 3 `countin-*`, 5 `stroke-*`, 1 `personal-best.wav`.

**Format:** all identical — `RIFF … WAVE audio, Microsoft PCM, 16 bit, stereo 22050 Hz`
(`SAMPLE_RATE = 22050`, `CHANNELS = 2`, `SAMPLE_WIDTH = 2`, `make-placeholder-audio.py:58-60`;
deterministic dual mono — both channels carry the same bytes).

**Sizes — uniformity is the synthetic tell:**

| bytes | count | duration | what |
|---|---|---|---|
| 705,644 | 21 | 8.00 s | tempo-0 renders |
| 529,244 | 21 | 6.00 s | tempo-1 renders |
| 423,404 | 21 | 4.80 s | tempo-2 renders |
| 352,844 | 3 | 4.00 s | count-ins |
| 26,504 | 1 | 0.30 s | personal-best |
| 6,216–16,800 | 5 | 0.07–0.19 s | strokes |

Total wav bytes **35,962,740 (~34.3 MiB)**; directory 35,996,154 B. Three distinct byte sizes across
63 loop files is not how recorded audio behaves. **Every wav mtime is 2026-08-04 17:42:19–17:42:21** —
a ~2-second window, i.e. one generator run.

**Generator:** `/home/james/opanije-gate4/apps/opanije-room/scripts/make-placeholder-audio.py`
(516 lines, stdlib only), run by `npm run audio`. The entire sound source is one `math.sin` plus
seeded noise through a one-pole low-pass, lines 82-97:
```python
sample = math.sin(2 * math.pi * freq * t)
if noise > 0.0:
    white = rng.uniform(-1.0, 1.0)
    last = last + 0.22 * (white - last)   # one-pole low-pass
    sample = (1.0 - noise) * sample + noise * last * 3.0
out.append(sample * _envelope(i, length))
```
Fixed timbre table at `:131-151`: reference pulse 98 Hz; support 196/277/370 Hz; strokes bass 110,
tone 245, slap 430, skin 300, rim 720 Hz. Loop-seamlessness via wrap-around mixing (`mix_into`, `:100-107`).

**Provenance independently verified:** all 72 on-disk sha256 match `GENERATED.json` (0 mismatches);
`sha256(make-placeholder-audio.py)` = `687f1642…e55a` = `audio-spec.json.generatorSha256`;
`sha256(audio-spec.json)` = `42abd7a2…4011` = `GENERATED.json.specSha256`; recomputing the set digest
with the test's recipe (`assets.test.ts:516-523`) yields
`41d80e59efc9d90e0e267e78ffb5d260f179ed00e774e1ca8d471d3b4fb62708` = `expectedAssetSetSha256`.

**"voice-*" filenames contain no speech**, deliberately. `render_syllable_line` (`:221-230`) emits
pitched sine blips as a stand-in for the human solfejo; `assets.test.ts:479-486` enforces this
structurally (asserts the `blip` body contains exactly one `math.sin(` and no
`harmonic|formant|resonator`). `README.md:96` states `npm run audio` "does not create or imitate
Junior's voice".

**Git:** committed, not ignored. `git check-ignore` → rc 1;
`git ls-files apps/opanije-room/assets/audio | wc -l` → **74** (72 wav + 2 JSON). **~34 MB of
synthesised wav is tracked in the repository.**

**No real audio exists anywhere in the repo.** A repo-wide search for
`*.wav|mp3|m4a|aac|ogg|flac|caf` outside `assets/audio/` returned zero files. No audio-specific
licence or attribution file exists — defensible only because nothing is third-party.

---

## Claim 9 — `apps/opanije-mobile`: Google OAuth adapter, expo-secure-store, repository factory, expo-video

**TRUE on all four, with one correction on the OAuth library.**
(Verified in `/home/james/work/opanije` — absent from the gate4 sparse worktree.)

**(a) Google OAuth adapter — REAL.**
`/home/james/work/opanije/apps/opanije-mobile/src/platform/oauth.ts` (218 lines). `OAuthAdapter`
interface L24-28; `SystemBrowserOAuthAdapter` L84-159 with `providers = { google: 'system-browser',
apple: 'disabled' }` (L85). Full PKCE: `transactionMaterial()` L34-45 generates a 64-byte verifier +
32-byte state via `Crypto.getRandomBytes`, SHA-256 digest base64url-encoded (L43); calls
`repository.startOAuth`, validates state + expiry (L103-105), persists the pending transaction to
SecureStore, then `WebBrowser.openAuthSessionAsync(start.authorizationUrl,
'https://opanije.com/mobile/auth/return', { showInRecents: false })` (L113-117). `callbackMaterial()`
L51-82 enforces https-only, host `opanije.com`, no port/userinfo/hash, exact path
`/mobile/auth/return`, exactly 2 query keys, state regex `^[A-Za-z0-9._~-]{43,128}$`. Cold/warm return
handling with single-flight dedupe at L125-158. `MockOAuthAdapter` at L161-218.
Transaction store: `src/platform/oauth-transaction.ts` (129 lines) — SecureStore-backed, 180 s max
lifetime, 4096-byte cap, selector schema validation L25-43.
Wired at `src/runtime/app-runtime.tsx:63-64` from `bundle.config.repositoryMode`.
Server counterpart: `public_html/wp-content/mu-plugins/opanije-mobile-api.php:1392-1403` registers
`/oauth/{op}`; the Google redirect itself lives in `opanije-course-native-identity.php:566`.

**CORRECTION:** the library is **not** `expo-auth-session` and **not** `@react-native-google-signin`.
Neither is in `package.json`. It is a **hand-rolled PKCE flow on `expo-web-browser` + `expo-crypto`**.
The app never holds a Google client ID — that lives server-side.

**(b) expo-secure-store session handling — REAL.**
`/home/james/work/opanije/apps/opanije-mobile/src/platform/secure-session.ts` (87 lines).
`NativeSessionVault implements SessionVault` L34-69; options L35-38
(`keychainAccessible: SecureStore.WHEN_UNLOCKED_THIS_DEVICE_ONLY`,
`keychainService: 'com.opanije.course.debug.preview.session.v1'`). `read()` L40-57 with an 8192-byte
guard, schema+TTL validation, self-healing delete on corruption. `isSession()` L15-32 enforces exactly
3 keys, token regex `^[A-Za-z0-9._~-]{43,2048}$`, 900 s access TTL / 30-day refresh window.
`MemorySessionVault` L71-87. Also used by `oauth-transaction.ts:1` and `purchase.ts:2`.

**(c) Repository factory + mock + http — REAL.**
- Factory `/home/james/work/opanije/apps/opanije-mobile/src/data/repository-factory.ts` (21 lines):
  `createRepositoryBundle()` L12-21 → `MockCourseRepository` for `mock`, `HttpCourseRepository(null)`
  for `production-disabled`/missing URL, `HttpCourseRepository(config.apiBaseUrl)` for production.
- `/home/james/work/opanije/apps/opanije-mobile/src/data/http-repository.ts` — **644 lines**, all 15
  `CourseRepository` methods (L425-644). AbortController + 15 s timeout (L342-368), AES-GCM-encrypted
  AsyncStorage response cache with namespace/context/path domain separation (L44-47),
  401 → single-flight refresh → retry (L400-415), lifecycle-epoch guards, strict `exactKeys` response
  validation.
- `/home/james/work/opanije/apps/opanije-mobile/src/data/mock-repository.ts` (324 lines) — same 15
  methods over `src/data/mock-catalog.v1.json`, AsyncStorage progress, idempotent operation IDs,
  `authScenario: 'success' | 'failure' | 'link-required'`.

**(d) expo-video — REAL.**
`/home/james/work/opanije/apps/opanije-mobile/src/components/native-video-player.tsx` (111 lines).
L2 imports `useVideoPlayer, VideoView, SubtitleTrack, VideoPlayer, VideoSource`. Player config L37-42
(`timeUpdateEventInterval`, `allowsExternalPlayback: false`, `staysActiveInBackground: false`);
five `useEvent` subs L43-49; four `useEventListener` handlers L51-61 incl. resume-seek clamping and
progress persistence; `<VideoView>` L75-83 with `nativeControls`/`buttonOptions`/`fullscreenOptions`;
rate selector 0.75/1/1.25/1.5 L89; subtitle radiogroup L90-99; error retry via `player.replaceAsync`
L71. Consumed at `src/app/lesson/[courseId]/[lessonId].tsx:7,146`.

**Versions** (`/home/james/work/opanije/apps/opanije-mobile/package.json`): `expo 57.0.7`,
`expo-secure-store 57.0.1`, `expo-video 57.0.1`, `expo-web-browser 57.0.1`, `expo-crypto 57.0.1`,
`expo-router 57.0.7`, `react-native 0.86.0`, `react 19.2.3`, `typescript 6.0.3`, `jest/jest-expo
29.7.0 / 57.0.2`.

**Size:** non-test source **4,439 lines / 32 files**; tests **4,082 lines / 28 files**; 161 literal
`test(`/`it(` plus 15 `test.each` blocks. Router: **Expo Router 57**, file-based, `typedRoutes: true`,
single `<Stack>` at `src/app/_layout.tsx:20-33`. **13 route files**: `index`, `library`, `continue`,
`account`, `editorial`, `offline`, `service-error`, `sign-in` (modal), `auth-return` (modal),
`checkout-return` (modal), `course/[courseId]`, `lesson/[courseId]/[lessonId]`, plus
`+native-intent.tsx` and `_layout.tsx`.
**Bundle IDs:** android `package` and ios `bundleIdentifier` both `com.opanije.course.debug.preview`
(versionCode 5 / buildNumber "5"); scheme `opanijepreview`; `applinks:opanije.com`.
`extra`: `preview: true`, `repositoryMode: "mock"`, `apiBaseUrl: null`, `purchaseMode: "disabled"`.
No blocking TODO/FIXME anywhere in `src/`. Source seal consistent
(`node scripts/native-source-seal.mjs` → `OPANIJE_SOURCE_SEAL_1b12921a…` = `src/config/source-seal.ts:3`).

---

## Claim 10 — data seam `src/data/api.ts`, `docs/SERVER-CONTRACT.md`, `src/data/commerce.ts`

**TRUE — all three exist. All three are unwired seams.**

- `/home/james/opanije-gate4/apps/opanije-room/src/data/api.ts` (166 lines, 6,820 B).
  `CatalogTransport` (30-33) and `RoomApi` (36-43) are injectable interfaces. Validation is genuine:
  `validateRows` deep-freezes and partition-checks (50-57, 85-96); `validatePlayableRows` rejects rows
  without a server-resolved `entitlement.grant` of `permanent-free`/`owned-course-line` (59-77);
  `assertAuthenticated` rejects empty `accountId`/`accessToken` (79-83).
  **`createRoomApi(transport)` (103-124) is never called in app code** — only in `api.test.ts`.
  What runs is `bundledMockupRoomApi` (163-166), a synchronous hardcoded single row from
  `MOCKUP_CATALOG_TRANSPORT` (140-149), consumed at `AppRuntime.tsx:249`.
  `catalogForPublishing()` (152-157) unconditionally throws — a deliberate publication tripwire.
- `/home/james/opanije-gate4/apps/opanije-room/docs/SERVER-CONTRACT.md` — 284 lines, 6 sections,
  proposed endpoints only (`GET /v1/me/entitlements`, `POST /v1/store-transactions/validate`,
  `GET /v1/me/room-items`, `/narration`, `/{itemId}/manifest`, `POST /v1/operator/render-jobs`,
  `POST /v1/me/assets/{assetId}/token`, `POST /v1/me/facts/batch`, `POST /v1/me/caderno/entries`,
  `POST /v1/operator/items/{itemId}/takedown`). Line 5: "Endpoint names are proposed shapes for the
  missing implementation, not evidence of a deployed API." Nothing in `src/` references these paths.
- `/home/james/opanije-gate4/apps/opanije-room/src/data/commerce.ts` (124 lines, 4,754 B) — pure, no
  billing SDK. `createCommercePlanner(clock)` (82-105) returns `{ intend }` producing a
  `CheckoutIntention`/`ConsultationIntention` object and nothing else; doc comment at line 53:
  "performs no billing or network operation". Guards `assertNoStandingFields` (60-65),
  `assertValidPrice` (68-75), `assertNoCommerceOnFreeSurface` (116-124) are real.
  **`createCommercePlanner` is referenced only by `commerce.ts` and `commerce.test.ts` — no screen
  imports it.**

---

## Claim 11 — six mu-plugins and `OPANIJE_COURSE_ACCESS_MODE = 'dormant'`

**TRUE — and there are 13 mu-plugins, not 6.**

Real tree: `/home/james/work/opanije/public_html/wp-content/mu-plugins/`.
(`public_html/shop/wp-content/mu-plugins/` is a **separate full second WordPress install**, not a
symlink; it holds exactly one file, `opanije-mail.php`, byte-identical to the main one — both md5
`58ade6f9533847459cb8dfb6bacb0a91`, 2,973 B. The course rail knows about the split:
`opanije-course-access.php:559-575` documents that `WPMU_PLUGIN_DIR` resolves wrongly under `/shop`,
and `opanije-mobile-api.php:9` bails on any non-main install.)

| File | Bytes | Lines |
|---|---|---|
| `opanije-course-access.php` | 60,015 | 1,732 |
| `opanije-course-app-preview.php` | 9,246 | 291 |
| `opanije-course-app-shell-copy.php` | 1,793 | 61 |
| `opanije-course-app.php` | 42,559 | 1,046 |
| `opanije-course-catalog.php` | 56,398 | 1,501 |
| `opanije-course-native-adapters.php` | 30,129 | 765 |
| `opanije-course-native-identity.php` | 26,572 | 596 |
| `opanije-course-native-product-map.php` | 1,966 | 68 |
| `opanije-course-pay-mercadopago.php` | 49,677 | 1,323 |
| `opanije-course-stream.php` | 6,456 | 187 |
| `opanije-lang-routing.php` | 18,254 | 448 |
| `opanije-mail.php` | 2,973 | 90 |
| `opanije-mobile-api.php` | 57,640 | 1,407 |

All six named files exist under exactly the claimed names. Plus subdirs `opanije-course-app/`
(`catalog.php`, `contracts.php`, `preview-catalog.php`, `shell-copy.php`) and `tests/`.

**`OPANIJE_COURSE_ACCESS_MODE` — DEFINED once**,
`/home/james/work/opanije/public_html/wp-content/mu-plugins/opanije-course-access.php:20`:
```php
const OPANIJE_COURSE_ACCESS_MODE = 'dormant';
```
Line 19: `/* This git-owned literal is the sole mode switch: dormant, enabled, or fail-closed. */`

**READ at** (all under `.../wp-content/mu-plugins/`):
- `opanije-course-access.php:67` — the `?course_preview=1` admin escape hatch.
- `opanije-course-access.php:267-269` — **the master gate**:
  `if ( 'dormant' === OPANIJE_COURSE_ACCESS_MODE && ! opanije_course_access_is_preview_request() ) { return; }`
  — the entire remainder of the file (**~1,460 lines**: OIDC adapter, ledger, REST receiver) is never
  parsed into scope.
- `opanije-course-access.php:574` — OIDC adapter registered only when `'enabled'`.
- `opanije-course-access.php:1671` — `fail-closed` branch → empty non-cacheable 503.
- `opanije-course-app.php:9, :174`; `opanije-course-app-shell-copy.php:9, :12`.
- `opanije-course-catalog.php:17-21, :24, :514-515` — three-way (`enabled` / `locked` ∈
  {`enabled`,`fail-closed`}). **The one deliberate exception: the wp-admin authoring UI loads while
  dormant.**
- `opanije-course-native-identity.php:25-26` — requires `'enabled'` AND `OPANIJE_COURSE_NATIVE_ENABLED
  === true` AND main install.
- `opanije-course-native-adapters.php:760-761`; `opanije-course-pay-mercadopago.php:172-173`
  (comment at `:165-168`: "no set of Mercado Pago constants can make the adapter ready on a
  non-enabled install"); `opanije-course-stream.php:23-24, :90-91, :183-184`.

**Effect of `'dormant'`:** no hook, REST route, redirect or DB write is registered anywhere. The only
loaded surfaces are the wp-admin catalog authoring UI and the administrator `?course_preview=1` mock.

`opanije-mobile-api.php` does **not** read the constant directly — it gates on
`OPANIJE_COURSE_MOBILE_API_ENABLED` (`:27-30`) and install (`:9`), reaching the mode indirectly.

---

## Claim 12 — versioned REST contract `opanije-mobile/v1`, fixtures + schema tested by BOTH PHP and TS

**PARTIAL. The namespace and fixtures are shared. The JSON schema is NOT — only PHP reads it.**

**Namespace** — `/home/james/work/opanije/public_html/wp-content/mu-plugins/opanije-mobile-api.php:13-14`:
```php
const OPANIJE_MOBILE_API_VERSION   = 'opanije-mobile/v1';
const OPANIJE_MOBILE_API_NAMESPACE = 'opanije-mobile/v1';
```
15 `register_rest_route` calls at `:1382-1405` (11 literal + 4 generated in the
`oauth/{start,exchange,refresh,logout}` loop at `:1391-1403`), all on `$namespace` (`:1381`).

**Files:**
- `/home/james/work/opanije/scripts/fixtures/mobile-api-v1.json` — 8,576 B
- `/home/james/work/opanije/scripts/fixtures/mobile-api-v1.schema.json` — 17,083 B

**PHP side** — `/home/james/work/opanije/scripts/tests/mobile-api-fixtures.php` (541 lines), loading
**both** at `:345-346`. It hand-rolls a Draft-2020-12 validator (`mobile_schema_validate`,
`mobile_schema_objects_are_closed`), asserts every object is closed (`additionalProperties: false`),
validates the fixture against the schema (`:350`), asserts negative cases (`:351-356`), then `require`s
the real plugin (`:373`) and compares live handler output to the fixture (`:379, :412, :416`, …).
Related: `scripts/tests/course-mobile-stack-fixtures.php`, `scripts/tests/rest-route-allowlist.php`.

**TS side** — `/home/james/work/opanije/apps/opanije-mobile/src/__tests__/wire-contract.test.ts:36-38`:
```ts
const fixture = JSON.parse(
  readFileSync(resolve(process.cwd(), '../../scripts/fixtures/mobile-api-v1.json'), 'utf8'),
) as WireFixture;
```
→ the same `/home/james/work/opanije/scripts/fixtures/mobile-api-v1.json`. Drives
`test.each(fixture.errors)` at L122. Namespace pinned at `src/domain/contracts.ts:1`
(`export const API_VERSION = 'opanije-mobile/v1'`), used to build URLs at `http-repository.ts:355`.

**Where the claim breaks:** `mobile-api-v1.schema.json` has **exactly one reader in the entire repo** —
the PHP test at `mobile-api-fixtures.php:346`. There is no `ajv`, no schema import, no schema read
anywhere in `apps/opanije-mobile`. The TS side instead **re-declares the shape by hand** as
`interface WireFixture` (`wire-contract.test.ts:20-34`) — a parallel transcription that can drift from
the schema with no test failing. Same fixture: yes. Same schema: no.

CI binding: `/home/james/work/opanije/.github/workflows/mobile-api-contract.yml` triggers on both files.

---

## Claim 13 — per-course entitlement defect (scalar product ID / boolean library / hard-coded 297.00)

**FALSE at HEAD.** The defect was real historically and has been fixed. Entitlement is **per-course
keyed** on a string `course_key`.

The decisive code —
`/home/james/work/opanije/public_html/wp-content/mu-plugins/opanije-course-access.php:1511-1546`:
```php
function opanije_course_access_subject_holds_course( $subject, $course_key ) {
    ...
    $ledger = get_option( 'opanije_course_ledger_' . $identity, array() );
    foreach ( $ledger as $node ) {
        $entry = $node[ $course_key ] ?? null;
        if ( is_array( $entry )
            && 'active' === ( $entry['state'] ?? '' )
            && $course_key === ( $entry['course_key'] ?? '' ) ) {
            return true;
        }
    }
    return false;
}
```
The ledger is two-level — `$ledger[$purchase_id][$course_key]`, written at `:1352-1355` and `:1386-1388` —
and the stored `course_key` is re-verified against the lookup key.

Admission and read permission are deliberately separate:
- `opanije-course-access.php:1614-1616` — `opanije_course_access_has_entitlement()` is boolean, but its
  docblock (`:1606-1611`) states it "never decides which course they may read."
- `opanije-course-access.php:1572-1580` — `opanije_course_access_has_course_entitlement( $user_id, $course_key )`.
- `opanije-course-app.php:305-307` — `opanije_course_app_user_may_read()` ends in
  `return opanije_course_access_has_course_entitlement( $user_id, $course );`. Its docblock at
  `:284-289` names **exactly this claim's failure mode** as the thing it exists to prevent:
  *"A learner who bought the primary course is authorized (they hold something) but may not read the
  upsell — resolving only the first question is the revenue leak this rail exists to close."*
- Other per-course callers: `opanije-course-pay-mercadopago.php:463`,
  `opanije-course-native-adapters.php:138,142`.

**No scalar product ID.** `opanije-course-native-product-map.php` requires a **map**
`course_key => int product_id` (`:28-38`), with a note at `:16-19`: "There is deliberately no ACF,
option, or single-product fallback."

**No hard-coded 297.00.** All five hits on `297` in the mu-plugins tree are inside *comments* in
`opanije-course-pay-mercadopago.php` (lines 92, 677, 682, 684, 685) explaining why money is compared as
strings. Actual prices come from the operator map `OPANIJE_COURSE_MP_PRICES` (`:99-117`), keyed per
course, regex-validated `/\A(?:0|[1-9][0-9]{0,5})\.[0-9]{2}\z/`.

**The defect WAS real — and is dated.** Commit `4252113d` ("Add dormant paid course access
foundation") had:
```php
function opanije_course_access_product_id() {
    return defined( 'OPANIJE_COURSE_ACCESS_PRODUCT_ID' ) ? (int) OPANIJE_COURSE_ACCESS_PRODUCT_ID : ...
```
with a flat single-level ledger returning a bare boolean — exactly the described defect. Closed by
`94a2a0dd` "feat(course): per-product entitlement for the two-SKU course rail" and `694da476`
"refactor(course): stand the course rail up on its own OAuth + payment rail" (which also replaced the
WooCommerce `order_id`/`product_id` event schema 1 with the `course_key`-based schema 2 — see
`opanije-course-access.php:22-32`). A tombstone comment survives at `:1602-1605`.

**A second course is already anticipated, not blocked:** `OPANIJE_COURSE_ACCESS_MAX_COURSES = 2`
(`opanije-course-access.php:44`), and the test fixtures already run two keys —
`array( 'afro-bahia', 'candomble-nation' )` at `scripts/tests/course-access-fixtures.php:76` and
`scripts/tests/course-pay-mercadopago-fixtures.php:18`.

**The plan is describing a state of the code that no longer exists.**

---

## Claim 14 — Room's bundle ID; is `com.opanije.room` taken?

**TRUE that `com.opanije.room` is free.**

- Room in use: `com.opanije.room.mockup` —
  `/home/james/opanije-gate4/apps/opanije-room/app.json:11` (`"android": { "package": "com.opanije.room.mockup" }`),
  confirmed in the built artifact's
  `android/app/build/outputs/apk/release/output-metadata.json` → `"applicationId": "com.opanije.room.mockup"`.
- **`com.opanije.room` itself is unused** anywhere in the config — the `.mockup` suffix is on every
  occurrence. It is free to claim.
- No iOS `bundleIdentifier` is declared in Room's `app.json` at all.
- For contrast, the mobile app uses `com.opanije.course.debug.preview` (android + ios).
- Neither app currently carries a production-shaped identifier: one says `.mockup`, the other says
  `.debug.preview`.

---

## Claim 15 — `npm run gate`

**TRUE.** `/home/james/opanije-gate4/apps/opanije-room/package.json`:

```json
"gate": "npm run lint && npm run typecheck && npm run test"
```

which expands to:
- `lint` → `eslint .` (eslint 9.39.5, `eslint-config-expo` 57.0.0, flat config `eslint.config.js`)
- `typecheck` → `tsc --noEmit` (typescript 6.0.3)
- `test` → `jest` (jest 29.7.0 / jest-expo 57.0.2)

Other scripts, for completeness: `start`, `android` (`expo run:android && ./scripts/verify-apk.sh`),
`publish:manifest`, `build` (= `publish:manifest` + `expo export --platform android`),
`bundle` (= `build`), `audio`, `media`. There is a separate `scripts/check-gates.mjs` (3,074 B) not
wired into `gate`.

**Gotcha:** `npm run gate` is **red in a bare shell** — see Claim 1. The Gradle-verifier test needs
`JAVA_HOME`; source `~/box/mobile-env.sh` first and it is 621/621 green.

---

## Claim 16 — does Room have sign-in / account code, or is it fully local?

**PARTIAL — a sign-in screen exists, but it is a pure local stub. Runtime behaviour is fully local
and offline.**

**Sign-in screen exists.** `/home/james/opanije-gate4/apps/opanije-room/src/app/signin.tsx:33-38`:
```ts
function continueWithStubAccount(): void {
    click();
    auth.signIn();
    router.replace('/intention');
}
```
`auth` comes from `DoorAuthContext` (`signin.tsx:14-23`), whose only provider is a `useState(false)`
in `_layout.tsx:22-26`. **No credential, no token, no provider SDK, no persistence of signed-in
state** — a fresh launch is signed out again. The screen's own comment at `signin.tsx:26` says
"Counsel owns identity... before real Google OIDC wiring", and it carries `GATE: INPUT-39`.
`_layout.tsx:31-45` does use it for a real `Stack.Protected` route guard, so the door is structurally
wired even though it authenticates nothing.

**Account code is types + pure helpers only.** `src/domain/account.ts` declares
`AuthenticatedAccount { accountId, accessToken }` (9-12) and
`AccountIdentityPort { createOrSignIn, linkPreAccount, deleteAccount }` (25-32) — **no implementation
anywhere in `src/`**; grep finds `AccountIdentityPort` only at its declaration.

**Network: essentially zero.** A full-source grep for `fetch(|axios|XMLHttpRequest|WebSocket|https?://`
outside tests returns three hits:
- `src/media/renderSource.ts:19` — `interface RenderTransport { fetch(...) }`, plus `RemoteRenderSource`
  (62-71) which is **never instantiated** in app code. Runtime default is `BundledRenderSource`
  (local `require()` assets), selected at `AppRuntime.tsx:246`.
- `src/app/ending.tsx:124` — `void Linking.openURL('https://opanije.com/contato/')`, the only outbound
  action, and it just hands a URL to the OS browser.
- No `axios` and no HTTP client in `package.json` at all.

`FactsSync` (`src/runtime/factsSync.ts`) is a durable offline queue, but its transmitter is
deliberately unconfigured — `AppRuntime.tsx:287`:
`factSender ?? (async () => { throw new Error('First-party fact sender is not configured.'); })`,
with a no-op network watcher default at `:290`. Everything durable goes to AsyncStorage:
`opanije.caderno-entries.v2`, `opanije.completed-sessions.v2`, `opanije.play-ledger.v1`,
`opanije.locale-override.v1`.

---

## Claim 17 — git state

**Reported.**

- **Worktree:** `/home/james/opanije-gate4`, gitdir `/mnt/i/opanije-pr1081/.git/worktrees/opanije-gate4`.
- **Branch:** `fix/room-guided-progression`
- **Tree:** **clean** — `git status --porcelain` returns 0 lines.
- **Sparse checkout:** enabled (`core.sparseCheckout=true`); only `/apps/opanije-room/` and `/docs/`.

Last 10 commits:

| SHA | Date | Subject |
|---|---|---|
| `4dde6752` | 2026-08-05 | docs(room): explain current app and KISS next step |
| `07d0e70f` | 2026-08-04 | docs(room): record r8 emulator regression evidence |
| `3e2541dd` | 2026-08-04 | fix(room): keep rehearsal progression visible |
| `99991cef` | 2026-08-04 | Merge pull request #1082 from rodolfoogliari/fix/room-current-estate-reconciliation |
| `b32a9706` | 2026-08-04 | docs(room): record private rehearsal authority and r7 evidence |
| `e073aae7` | 2026-08-04 | feat(room): add guided echo rehearsal prototype |
| `eb5c7516` | 2026-08-04 | feat(room): add live compact session controls |
| `64872c5c` | 2026-08-04 | feat(room): reconcile mockup with current product estate |
| `8c72a5db` | 2026-08-04 | Merge pull request #1081 from rodolfoogliari/build/room-mockup-pass2-on-main |
| `7867516a` | 2026-08-04 | Merge pull request #1083 from rodolfoogliari/docs/agents-contract-20260804 |

Other worktree: `/mnt/i/opanije-pr1081` at `45a26d19` (detached HEAD).
Full non-sparse clone used for mobile/WordPress verification: `/home/james/work/opanije`, branch
`main`, HEAD `99991cef` (2026-08-04).

---

# Claims that are wrong or overstated

Ordered by how much a build plan would suffer from believing them.

### 1. Claim 13 is FALSE — the entitlement defect does not exist at HEAD

This is the most consequential error. The plan asserts a live revenue leak. In fact
`opanije_course_access_subject_holds_course()` (`opanije-course-access.php:1511-1546`) keys on
`course_key` in a two-level ledger and re-verifies the stored key; `opanije_course_app_user_may_read()`
(`opanije-course-app.php:305-307`) routes through the per-course check; the product map is a map, not
a scalar (`opanije-course-native-product-map.php:28-38`); and there is no hard-coded 297.00 outside
comments. The defect existed in `4252113d` and was closed by `94a2a0dd` and `694da476`. Worse for the
plan's framing: `OPANIJE_COURSE_ACCESS_MAX_COURSES = 2` and the tests already exercise two course keys.
**Any remediation work scheduled against this claim is wasted work.**

### 2. Claim 12 overstates schema sharing

The fixture *is* shared (both sides read
`/home/james/work/opanije/scripts/fixtures/mobile-api-v1.json`). The **schema is not** —
`mobile-api-v1.schema.json` has exactly one reader in the repo, the PHP test. The TS side
hand-transcribes the shape as `interface WireFixture` (`wire-contract.test.ts:20-34`). The claim
implies a stronger guarantee than exists, and it hides a real drift risk.

### 3. Claim 1 gets the test count wrong by 26% and the line count is half implementation

Actual: **621 tests** (612 pass / 8 todo / 1 env-conditional fail), not ~493. And "24,000 lines of
source" is true only counting test code — implementation is **12,443** lines, tests are 11,623.

### 4. Claim 4 overstates reachability

The function is genuinely exported from a production module and genuinely imported at module scope by
`AppRuntime.tsx:25` with a live `?? createFakeRoomAudio()` fallback at `:245` — so it ships in the
bundle. But **no runtime path selects it**: `_layout.tsx:70-78` always injects the real
`createRoomAudio`, and there is no env var, debug menu or deep link that substitutes the fake.
Exploiting it requires editing source. "A path by which a Caderno entry could be forged" is true of the
*architecture* (the trust boundary sits at the audio injection point, and the Caderno's defences guard
against exported callers, not against a substituted engine) but not of the *shipped app*.

### 5. Claim 8's "scheduled, not triggered" is too absolute

There is a real, intentional per-tap trigger path: `useRoomSession.ts:221-234` fires
`playOneShot('assets/audio/stroke-<stroke>.wav')` on a **missed or wrong-zone** strike, plus count-in,
UI click and the personal-best cue. The accurate statement is "the music is never triggered per tap; a
miss is." Separately, "scheduled" should not be read as a `setTimeout` timeline or a seek-into-a-long-file:
it is native looping of one-cycle pre-renders with phase *observed* from `playbackStatusUpdate`.
(The "72 synthetic placeholder renders" figure is **exactly right** and hash-verifiable.)

### 6. Claim 9's OAuth library attribution is wrong

Neither `expo-auth-session` nor `@react-native-google-signin` is in `package.json`. The Google flow is
a **hand-rolled PKCE implementation on `expo-web-browser` + `expo-crypto`**
(`src/platform/oauth.ts:34-159`), with the client ID held server-side. Anyone planning "swap the OAuth
library" work will find no library to swap.

### 7. Claim 3c ("fade/thinning model when unfed") is materially thinner than described

It is a **binary** `full`(0.6)/`thin`(0.2) toggle recomputed every authored cycle, applied only to the
selected-part companion, recovering fully on the very next cycle. There is **no decay curve** and — the
important part — **no cross-session unfed decay at all**: nothing records a last-practice timestamp.
And the real feeding measure (`tap.ts:82-83`, 50% of grid positions) is **computed and then discarded**;
presence is decided by "did you touch anything at all" (`useRoomSession.ts:337-339`).

### 8. Claim 11 undercounts by more than half

There are **13** opanije mu-plugins, not 6 — the six named ones plus `opanije-course-app.php` (1,046 lines),
`opanije-course-native-adapters.php` (765), `opanije-course-app-preview.php`, `opanije-course-native-product-map.php`,
`opanije-course-app-shell-copy.php`, `opanije-lang-routing.php`, `opanije-mail.php`. Roughly 360 KB /
9,600 lines of PHP total. Sizing any WordPress work off "six files" underestimates by ~2×.

### 9. Claim 16's "fully local" needs the sign-in caveat

Room **does** have `src/app/signin.tsx` and a `DoorAuthContext`, and `_layout.tsx` uses it for real
`Stack.Protected` route guarding. It authenticates nothing and persists nothing — but the door is
structurally wired, which changes the shape of "add real auth" work (it is a swap, not a greenfield).

### 10. Claim 6 — the artifact is a *release* APK signed with the debug key

98.2 MiB and 2026-08-04 are correct. But it is `variantName: "release"`, and per
`build-room-apk.sh:46` the release variant "in this Expo template, is signed with the debug"
keystore. It is not store-submittable, and `android/` is gitignored so it is untracked build output.

---

# Things the plan missed that matter

### A. The repository is GPL v3

`/home/james/opanije-gate4/LICENSE.txt` is the **GNU General Public License v3**, repo-wide. Both apps
live inside it. For a paid, closed-source mobile app distributed through the App Store — whose terms
have a long-standing conflict with GPLv3's anti-tivoization and installation-information clauses —
this is a first-order question that has to be settled before any store submission, not after.
No per-directory licence override exists.

### B. `npm run gate` is red on a bare shell — and the skip-guard has a hole

`src/__tests__/appConfig.test.ts:154` fails with `ERROR: JAVA_HOME is not set`. Its skip-guard at
`:142-152` catches "Gradle daemon unreachable" (the documented WSL loopback trap) but **not** "no JDK
installed". Source `~/box/mobile-env.sh` first → 621/621 green. Any CI runner or fresh clone without a
JDK will see a red gate and misread it as a code defect.

### C. Most of the interesting mechanics do NOT appear in a student build

This is the single biggest gap between "what the code contains" and "what a user would see". The echo
loop (3b), the fade/thinning (3c), and the three-facts + personal-best closing (3d) are **all** gated
behind `playLayerEnabled`, which is false unless `__DEV__` or `EXPO_PUBLIC_ROOM_DEMO`
(`AppRuntime.tsx:239-242`; `useRoomSession.ts:173`; `closing.tsx:151`). Plus two whole routes
(`review`, `past-the-door`) are demo-only (`_layout.tsx:46-52`). A plan that treats these as shipped
features is planning against a demo build. The tests encode the gating deliberately —
`closing.test.tsx:234` asserts the facts are *absent* by default.

### D. Room has never run on a real handset — and that is a named, operator-owned blocker

`apps/opanije-room/docs/ACCEPTANCE.md:29` marks criterion 1 **"BLOCKED — owner: operator"** and
**"NOT VERIFIED ON A DEVICE"**: the current APK has not been installed or run on a handset, nobody has
heard the emulator audio, and there is no handset, iOS, real-touch, TalkBack, responsive-layout,
native-lifecycle, timing-under-load, real-latency or low-tier evidence. Everything green is simulation
plus a headless-emulator smoke pass on a *dated ancestor*.

### E. Shipping is blocked on named human consent, not on engineering

`ACCEPTANCE.md:29`: "Junior INPUT-69 separately blocks shipping." `ACCEPTANCE.md:39` (criterion 11):
"Junior has not seen a device run and no assent in his words exists. INPUT-78, INPUT-79, INPUT-69 and
JUNIOR-SUPPORT-ARRANGEMENT remain open; founder/build authorization to prototype does not satisfy
them." There are **56 `GATE:` markers** in non-test `src/` — founder-, counsel- or Junior-owned open
decisions embedded in the code (identity/privacy treatment at `signin.tsx:26`, Apple sign-in
equivalence, account-deletion scope at `domain/account.ts:67`, the tempo ladder, the syllable standard,
the free-rhythm partition). Several are load-bearing. These are not engineering tasks and no amount of
build capacity closes them.

### F. The audio generator refuses to run if the arrangement gate is closed

`scripts/audio-spec.json` carries `JUNIOR-SUPPORT-ARRANGEMENT` with `"status": "unresolved"` and "not
approved for publication", and `make-placeholder-audio.py:287-289` **hard-fails** if that gate is
closed. Regenerating audio is coupled to an unresolved human decision.

### G. ~34 MB of synthesised WAV is committed to git, and there is no real audio anywhere

`git ls-files apps/opanije-room/assets/audio` → 74 tracked files (72 wav + 2 JSON), 35,962,740 bytes of
wav. All 72 are `math.sin` + seeded noise from a 516-line Python script; a repo-wide search finds
**zero** audio files of any format outside that directory. Replacing placeholders with real recordings
means (i) a shoot (`docs/SHOOT-LIST.md` exists), (ii) re-deriving `AUTHORED-TIMING.json` from real
renders, and (iii) dealing with 34 MB of tracked binary history. The provenance chain
(`expectedAssetSetSha256` / `generatorSha256` / `specSha256`, all verified to match, enforced by
`assets.test.ts:490-523`) will fail closed the moment assets change without a regenerated manifest —
by design, but it is a step a plan must include.

### H. The native mobile app is formally PARKED, and its CI is switched off

`/home/james/work/opanije/docs/SITE-SSOT.md:228` (**DN-3**): "Park native; ship web-only for launch… it
already ships dormant/disabled… **Do not build against it or let it accrete scope**."
`.github/workflows/native-mobile.yml` was reduced to `workflow_dispatch:`-only on 2026-07-31
(`edf5b4be`); its header records that the job "had failed **30 consecutive times** on 'Typecheck the
shared application'". The `android-preview-artifact` job was retired 2026-07-29. `apps/opanije-mobile/node_modules`
does not exist, so **current typecheck/test status is unverified** — the last three mobile commits
(2026-07-29/30) were typecheck repairs made *before* the workflow was disabled and no CI run has
exercised them since. A plan that treats the mobile app as a working base is treating an unverified,
explicitly-parked codebase as one.

Its full gate sequence, if revived: `npm ci` → `source:validate` → `contract:check` (needs PHP 8.3) →
`video:generate` (needs ffmpeg) → `typecheck` → `lint --max-warnings 0` → `test:ci`. Node pinned
22.21.0, npm 11.6.4.

### I. The mobile app ships entirely on mocks

`apps/opanije-mobile/app.json` `extra`: `preview: true`, `repositoryMode: "mock"`, `apiBaseUrl: null`,
`purchaseMode: "disabled"`. `repository-factory.ts:12-21` therefore returns `MockCourseRepository`.
The 644-line `HttpCourseRepository` exists and is sophisticated, but nothing in the shipped config
reaches it.

### J. The whole WordPress course rail is dormant behind one literal

`opanije-course-access.php:20` — `const OPANIJE_COURSE_ACCESS_MODE = 'dormant';` — and the master gate
at `:267-269` means ~1,460 lines (OIDC adapter, ledger, REST receiver) are never even parsed into
scope. Flipping to `'enabled'` is a one-token change that activates roughly 9,600 lines of PHP,
Mercado Pago payment handling, an OAuth server and REST routes that have **never run in production**.
That is a very large, very sudden surface change and needs its own staged plan.

### K. There are two separate WordPress installs under `public_html`

`public_html/` and `public_html/shop/` are **independent full installs** (the latter has its own
`wp-admin/`, `wp-includes/`, `wp-config.php`), not a symlinked share. `opanije-mail.php` is duplicated
byte-for-byte between them. The course rail explicitly compensates
(`opanije-course-access.php:559-575` on `WPMU_PLUGIN_DIR` resolving wrongly under `/shop`;
`opanije-mobile-api.php:9` bailing on non-main installs). Any WordPress work must decide which install
it targets.

### L. Room's outward-facing seams are all designed and none are wired

`src/data/api.ts` (`createRoomApi` never called — only `bundledMockupRoomApi`, a hardcoded single row),
`src/data/commerce.ts` (`createCommercePlanner` imported by no screen), `RemoteRenderSource`
(`renderSource.ts:62-71`, never instantiated), `AccountIdentityPort` (`domain/account.ts:25-32`, no
implementation), `factSender` (`AppRuntime.tsx:287`, throws by default), and the 284-line
`docs/SERVER-CONTRACT.md` whose own line 5 says the endpoints are "proposed shapes for the missing
implementation, not evidence of a deployed API". `api.ts:152-157 catalogForPublishing()`
unconditionally throws as a publication tripwire. The *design* work for going online is done; **none of
the implementation is**. That is the actual size of "connect Room to a server".

### M. `verify-apk.sh` is not portable and has three coverage holes

Beyond the AAB gap (Claim 5): it sources `"$HOME/box/mobile-env.sh"` when `OPANIJE_MOBILE_ENV` is unset
— a **workstation-specific absolute path baked into a repo script**, so it cannot run in CI as written.
Its own header notes a stale generated `android/` tree predating the plugin is uncovered until
regenerated. And it enforces only five permission red lines; `SYSTEM_ALERT_WINDOW` and legacy-storage
declarations are printed for human review, not failed.

### N. Neither app has a production bundle identifier

Room: `com.opanije.room.mockup` (no iOS identifier declared at all). Mobile:
`com.opanije.course.debug.preview` for both platforms, with keychain service
`com.opanije.course.debug.preview.session.v1` and scheme `opanijepreview`. Renaming to production IDs
touches app config, the keychain service string (which will orphan existing sessions), deep-link
intent filters and `applinks:` associations — and for the mobile app also the source seal
(`src/config/source-seal.ts`, verified by `scripts/native-source-seal.mjs`, which hashes the whole
`android/` tree).

### O. The committed `dist/` is an Android export, and no web export persists

`dist/metadata.json` has only an `android` key; `npm run build` is `expo export --platform android`.
The web export scripts (`walk-web-routes.sh:50`, `capture-web-widths.sh:45`) export into a `mktemp -d`
that is then cleaned up, and drive Chrome on the *Windows* side
(`/mnt/c/Program Files/Google/Chrome/Application/chrome.exe`) with a Windows-local `--user-data-dir`.
Reproducing that evidence requires this specific WSL+Windows setup. `walk-web-routes.sh:4-11` also
warns its output proves only that the export executes and routes — "nothing about Android, audio,
layout, accessibility, lifecycle, input, GPU, or device performance."

### P. The verification worktree itself is sparse

`/home/james/opanije-gate4` shows only `apps/opanije-room/` and `docs/`. Anyone planning from that
directory will conclude the mobile app and the entire WordPress estate do not exist. Use
`/home/james/work/opanije` for anything estate-wide.
