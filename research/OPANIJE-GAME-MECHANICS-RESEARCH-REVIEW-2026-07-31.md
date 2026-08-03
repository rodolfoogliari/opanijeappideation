# Opanijé — Game Mechanics Research Review and Revised Product Direction

**Date:** 2026-07-31  
**Status:** Product-brainstorming review; evidence-backed direction, not an approved experience specification  
**Purpose:** Audit the first game-mechanics proposal, correct its evidentiary overreach, and define a stronger testable game architecture for Opanijé.

---

## 1. Executive verdict

The first proposal was directionally right on one central point: Opanijé should not be a percussion course covered with points, streaks, and a map. The reward should come primarily from playing inside the master's real battery, while external gamification serves only as a return scaffold.

However, the proposal needs four material corrections:

1. **It generalized educational gamification findings too far.** The result that `Rules/Goals + Challenge + Mystery` was the strongest combination came from student learning outcomes, not adult percussion retention or gaming addiction. It is a useful design prior, not a proven formula for Opanijé.
2. **It was still too close to the existing Room concept.** It elaborated “choose the room” instead of fully reopening the game space.
3. **It did not make the win/feedback event explicit enough.** A player can choose difficulty and experience surprise without yet having a complete game. Competence requires an intelligible relationship between action and result.
4. **Several recommendations were hypotheses presented too confidently.** A weekly practice pulse, a discovery atlas, prerecorded-master relatedness, and a strong musical ending are plausible; none is directly established as a retention mechanism for this product.

The revised product thesis is:

> **The core game is holding a musical relationship through a master-authored perturbation and discovering, at re-entry, whether the player stayed with it.**

The simplest atomic mechanic is:

> **Lock in → support disappears or the form changes → the player continues → the reference returns → the result becomes audible.**

This is a genuine feedback loop without a microphone. The recording does not grade the person; it reveals the musical relationship.

Internal working label: **Hold & Rejoin**. This is not proposed product copy and does not rename the Room.

---

## 2. Scope and method

This review used Google Scholar-indexed literature as discovery and followed records to publisher, DOI, university, PubMed, or open-access full-text pages. Priority order was:

1. Meta-analyses and systematic/scoping reviews.
2. Controlled or experimental studies.
3. Domain-specific music-practice studies.
4. Neuroscience used only to explain plausible mechanisms, never as proof of product retention.

Vendor retention claims, design folklore, and “dopamine hit” explanations were not treated as evidence.

### Evidence labels used below

| Label | Meaning |
|---|---|
| **DIRECT-ADJACENT** | Games or instrumental music practice, but not this exact product or tradition |
| **TRANSFER** | Educational, consumer-behavior, habit, or general psychology evidence being transferred into this context |
| **MECHANISTIC** | Laboratory/neuroscience evidence that explains a possible process but does not predict product behavior |
| **HYPOTHESIS** | Product reasoning that must be tested in Opanijé |

There is almost no high-quality evidence for an adult, single-player, no-microphone, culturally governed percussion practice product. A 2024 systematic review found only 15 empirical studies of digital game-based learning in music education from 2011–2023 and called for stronger experimental comparisons and broader outcome measures. Therefore, evidence can narrow the design space, but it cannot choose the product for us. [Weatherly, Wright, & Lee 2024](https://doi.org/10.1177/1321103X241270819)

---

## 3. Binding context preserved

The brainstorming reopened the game, not the product constitution. These remain binding:

- Adult practitioners only in the current product plan.
- Each tradition's named authority governs its sacred boundary; Junior governs the relevant Ketu Candomblé material.
- The app does not issue a machine verdict on musicianship.
- Release 1 has no microphone.
- The play layer is loud, resettable, behavioral, and structurally separate from the quiet, permanent Caderno/standing layer.
- Play-layer progress can never confer, accelerate, purchase, or imply standing.
- The free room remains available permanently; no hearts, lives, energy, or withdrawal of what was given.
- No synthetic voice.
- Master recordings never name a price or product.
- Sacred-adjacent game form requires the named authority's design or assent.
- The real, layered master battery and usable stems are product-existence conditions.
- The student can freely move between parts and challenge states, even if behavioral facts also open new variations.
- During play, the phone is propped up, the player's hands are busy, and there should be no menu work mid-round.

The superseding engagement mandate does permit streaks, goals, XP, levels, celebration, loss aversion, notifications, unlockables, and behavior-based auto-advancement in the play layer. Permission does not establish that these mechanics are effective or appropriate; this review evaluates them anew.

---

## 4. Audit of the first proposal

| Earlier statement or decision | Review | Corrected position |
|---|---|---|
| There is no scientifically valid universal ranking of “most addictive mechanics.” | **Retain.** Gaming-disorder research is interactionist and largely associative. The 2024 SHARP-G Delphi instrument is provisional, not a causal league table. | Describe **risk clusters**, not a universal addiction ranking. [Saini et al. 2024](https://doi.org/10.1556/2006.2024.00026), [Rehbein et al. 2021](https://doi.org/10.1007/s40429-021-00367-7) |
| `Rules/Goals + Challenge + Mystery` is the strongest sustainable game spine. | **Overstated.** It was the highest-performing combination in a 2025 meta-analysis of 37 randomized or quasi-randomized educational trials and 182 effect sizes. The dependent variable was learning outcome, not retention, enjoyment, or addiction. | Use it as a **TRANSFER design prior**. It supports clear missions, selectable challenge, and musically lawful uncertainty, but makes no retention guarantee. [Dai, Xu, & Xing 2025](https://doi.org/10.1007/s11423-025-10493-y) |
| Autonomy, competence, and relatedness are the motivational chassis. | **Retain with nuance.** Four game studies linked these needs to enjoyment and intended future play. Music-practice studies found autonomy-supportive environments and autonomous motivation associated with more or better practice. These are not randomized product tests. | Design explicitly for meaningful choice, intelligible feedback, and human connection; measure whether players actually experience them. [Ryan, Rigby, & Przybylski 2006](https://doi.org/10.1007/s11031-006-9051-8), [Evans & Bonneville-Roussy 2016](https://doi.org/10.1177/0305735615610926), [Bonneville-Roussy & Evans 2025](https://doi.org/10.1177/03057356241296109) |
| A real named master in a recording satisfies relatedness. | **Unsupported as written.** A real performer provides authenticity, presence, and possible parasocial connection, but prerecorded presence cannot be assumed to equal reciprocal human relatedness. | Treat **recorded-master relatedness as a product hypothesis**. Periodic real human recognition or appointment is a separate and likely stronger mechanism, but it is outside the Release 1 core loop. |
| Groove and musical uncertainty should be the reward. | **Retain with a boundary.** Groove research supports pleasurable movement and a balance between predictability and complexity; musical uncertainty and surprise can influence pleasure. These studies concern listening or movement, not app return. | Preserve the authentic groove and use lawful calls, dropouts, and re-entry as play events. **Do not alter a toque's syncopation to optimize engagement.** [Witek et al. 2014](https://doi.org/10.1371/journal.pone.0094446), [Stupacher et al. 2022](https://pmc.ncbi.nlm.nih.gov/articles/PMC9396343/), [Cheung et al. 2019](https://doi.org/10.1016/j.cub.2019.09.067) |
| A strong musical peak and ending should improve return. | **Too strong.** Peak–end evidence robustly concerns retrospective evaluation. Game-specific evidence found reliable effects on remembered challenge but mixed effects on enjoyment and repeat preference. | Use a clean peak and ending to improve session coherence and memory. Treat any effect on D7 return as **HYPOTHESIS**, not established fact. [Alaybek et al. 2022](https://doi.org/10.1016/j.obhdp.2022.104149), [Gutwin et al. 2016](https://doi.org/10.1145/2858036.2858419) |
| Streaks have strong short-term pull and should be softened or repaired. | **Mostly correct, insufficiently scoped.** Seven consumer studies show intact logged streaks increase the next behavior relative to broken streaks, and repair attenuates the break effect. A 2025 work-task study found streak incentives increased persistence through greater goal commitment. Neither establishes durable music practice or wellbeing. | Streaks are a credible persistence lever and a credible confound. Test them separately from the core game; measure return after a break, not only D7 while intact. [Silverman & Barasch 2023](https://doi.org/10.1093/jcr/ucac029), [Mehr et al. 2025](https://doi.org/10.1016/j.obhdp.2025.104391) |
| A rolling weekly practice pulse is preferable to a hard daily streak. | **Unproven.** This was a design proposal, not a finding. Habit evidence favors repetition in a stable context and shows that one missed opportunity need not materially impair habit formation, but it does not establish a three-of-seven mechanic. | Label a rolling pulse as an **experimental arm**, not the default scientific answer. [Lally et al. 2010](https://doi.org/10.1002/ejsp.674), [Singh et al. 2024](https://pmc.ncbi.nlm.nih.gov/articles/PMC11641623/) |
| Points, XP, levels, and leaderboards are mostly unsuitable. | **Needs nuance.** Points/levels/leaderboards can increase output without reliably increasing intrinsic motivation. Other experiments show that specific configurations can support competence or meaningfulness. Public absolute leaderboards can reduce perceived competence among weaker learners. | Do not treat these elements as intrinsically harmful. Exclude public ranking initially because it is a weak fit for beginner-first practice and can resemble standing. Use numbers only where they communicate behavioral facts or choices. [Mekler et al. 2017](https://doi.org/10.1016/j.chb.2015.08.048), [Sailer et al. 2017](https://doi.org/10.1016/j.chb.2016.12.033), [Li, Hew, & Du 2024](https://link.springer.com/article/10.1007/s11423-023-10337-7) |
| Variable rewards and near-misses are the most compulsive mechanics. | **Directionally responsible, scientifically overcompressed.** Reward-uncertainty evidence includes primate dopamine studies; near-miss evidence comes from gambling tasks; loot-box evidence is correlational. None yields an exact addictive-pull ranking for ordinary game mechanics. | Treat paid/random rewards, engineered near-misses, and gambling-like reinforcement as a **high-risk excluded class**, without claiming a universal causal magnitude. [Fiorillo et al. 2003](https://doi.org/10.1126/science.1077349), [Clark et al. 2009](https://doi.org/10.1016/j.neuron.2008.12.031), [Garea et al. 2021](https://doi.org/10.1080/14459795.2021.1914705) |
| The Listening Round was already a complete core game. | **Not yet.** It had goals, choices, difficulty, uncertainty, and an ending, but the action–result feedback was still too implicit. Without a legible result, “competence” may remain aspiration rather than experience. | Make **dropout/re-entry or call/response reveal** the atomic feedback event. The player must be able to hear what their action meant without the app declaring success. |

### General evidence caution

Gamification effects are positive on average but heterogeneous and often small. Sailer and Homner found small effects on cognitive, motivational, and behavioral learning outcomes, but only the cognitive effect remained robust in the high-methodological-rigor subset. A later meta-analysis of 35 interventions found only a small average effect on intrinsic motivation (`g = .257`), high heterogeneity, minimal average impact on competence, and heavy reliance on self-report. [Sailer & Homner 2020](https://doi.org/10.1007/s10648-019-09498-w), [Li, Hew, & Du 2024](https://link.springer.com/article/10.1007/s11423-023-10337-7)

This means Opanijé should not copy a mechanic because it “works in the literature.” It should use research to form precise hypotheses and then measure free-choice behavior in the actual product.

---

## 5. Revised game thesis: Hold & Rejoin

### 5.1 The atomic loop

1. **Lock in.** The player chooses a part and settles into the complete or supported battery.
2. **Perturb.** A master-authored musical condition changes: the reference part drops, density rises, a call occurs, the form turns, or the player is called into another seat.
3. **Hold or respond.** The player continues the pattern or follows the cue.
4. **Rejoin.** The reference stem or full battery returns at a musically valid boundary.
5. **Hear the result.** Alignment or misalignment becomes audible to the player. No microphone, score, or verdict is required.
6. **Choose.** Repeat, reduce support, increase masking, change tempo, add a form event, or switch part.

The crucial advance over the first proposal is step 5. Re-entry is not merely a dramatic ending; it is the feedback reveal.

### 5.2 Why this is closer to a real game

The loop contains:

- A clear local objective.
- A consequential action performed by the player.
- Uncertainty about whether the relationship will hold.
- A legible reveal.
- An adjustable challenge.
- Meaningful choice about the next attempt.
- A bounded round with an end.

The player, not the app, interprets the result. That preserves the difference between **musical feedback** and **institutional judgment**.

### 5.3 Difficulty is a state space, not a ladder

| Axis | Lower challenge state | Higher challenge state | What it trains or changes |
|---|---|---|---|
| **Reference support** | Student's/reference part audible throughout | Reference fades or disappears | Internal pulse and pattern continuity |
| **Dropout length** | One short gap | Several cycles without reference | Temporal maintenance and recovery |
| **Auditory density** | Few surrounding stems | Dense battery and masking | Auditory segregation |
| **Tempo** | Slower master-approved performance | Faster master-approved performance | Motor demand and processing speed |
| **Form volatility** | Stable loop | Entrances, calls, breaks, turnarounds | Prediction and form recognition |
| **Role stability** | One part throughout | Part change after a call/count-in | Memory, flexibility, and orientation |

No axis is universally “better” or “more advanced.” More density can be harder to hear and easier to hide inside. Less density can be clearer and more exposing. The player must be able to move in all directions.

Challenge–skill balance has a moderate relationship with flow across domains, but it is not a guaranteed or singular cause of engagement; player-selected difficulty remains preferable here because the app cannot assess musical skill and autonomy is itself valuable. [Fong, Zaleski, & Leach 2015](https://doi.org/10.1080/17439760.2014.967799)

### 5.4 Authorship rule

The system must not splice sacred or tradition-governed material into arbitrary procedural arrangements. “Variable” means one of several **complete, master-designed and authority-approved scripts**, or parameter changes that Junior explicitly recognizes as musically valid.

The mystery is: *which lawful event, and can I stay with it?* It is not: *what random prize will I receive?*

---

## 6. A broader game space

The first proposal prematurely converged. These are the independent game forms worth considering:

| Game form | Player action and reveal | Objective feedback without grading drumming? | Release 1 fit | Evidence status | Main risk |
|---|---|---:|---:|---|---|
| **Hold & Rejoin** | Maintain the part through dropout; reference returns | **Yes, audible self-feedback** | **High** if stems permit approved fades/dropouts | HYPOTHESIS grounded in groove, competence, and feedback research | Dropout may be musically invalid for some material |
| **Call Hunter** | Hear a real call/lead signal and follow the form change | **Yes, the battery reveals the expected change** | Medium; depends entirely on the toque and recording plan | HYPOTHESIS grounded in musical expectation/curiosity | Inventing calls or flattening their meaning |
| **Battery Detective** | Hear a short mixture and identify the missing, entering, or changed part | **Yes, app can verify listening perception** | High; stems already exist | HYPOTHESIS; clear competence feedback, but little direct percussion-practice evidence | Becoming a screen quiz instead of embodied practice |
| **Seat Switch** | Change part after a count-in and stay oriented | Partly; player hears the fit | Medium/low for beginners | HYPOTHESIS | Cognitive overload and excess recording complexity |
| **Route Composer** | Choose the order of support, density, tempo, and form states for a personal round | No quality verdict; choices visibly change the arrangement | Medium | HYPOTHESIS supporting autonomy | Configuration may replace actual playing |
| **Collective Battery** | Two or more real players occupy complementary parts | Human musical feedback | Low for Release 1; strong later possibility | Social interaction is promising but product-specific evidence absent | Network dependency, social pressure, empty-room problem |

### Recommended combination

For the first product test:

- **Primary embodied game:** Hold & Rejoin.
- **Conditional extension:** Call Hunter, only if Junior confirms authentic calls/turnarounds in the chosen material.
- **Optional 15–30 second prelude:** one Battery Detective question that tells the player what to listen for in the body round.

The listening microgame may provide the explicit, externally verifiable competence signal that the body game deliberately refuses to score. The two ledgers must remain distinct:

- The app may verify **what the player identified on screen**.
- Only the player experiences **whether the played part held**.
- Neither result creates standing or enters the Caderno.

---

## 7. Session architecture

### 7.1 Moment-to-moment loop

`entrain → anticipate → perturb → maintain/respond → re-entry reveal`

The perturbation should be knowable enough to invite prediction and uncertain enough to require attention. Curiosity research generally supports learning when an information gap feels resolvable; impossible or arbitrary mystery does not offer the same value. This is further reason to use a small grammar of understandable musical events rather than random surprises. [Gruber & Ranganath 2019](https://pmc.ncbi.nlm.nih.gov/articles/PMC6891259/)

### 7.2 One sitting

A first-session round should be finite and musically shaped:

1. **Arrival:** stable support, rapid entry into groove.
2. **First reveal:** one short dropout and re-entry.
3. **Chosen branch:** player selects more exposure, more density, or another tempo.
4. **Peak event:** longer dropout or authentic call/turnaround.
5. **Resolution:** a complete, clean battery return and ending.

The peak/end shape is justified as an experience-quality hypothesis, not a proven retention device.

### 7.3 Between rounds

Only after the musical ending does the screen ask for input. Large, arm's-length choices:

- Again.
- Less support.
- More instruments.
- Another tempo.
- Add a call/change.
- Change part.
- Finish.

An optional private self-assessment can be phrased as a routing choice rather than a grade:

- “Again as it was.”
- “Give me more support.”
- “Take more support away.”

Music self-assessment can promote reflection and self-direction, but the quality of self-assessment varies; it should help choose the next condition, not manufacture a credential. [Valle et al. 2016](https://doi.org/10.1177/0027432116644652)

---

## 8. The long loop and engagement layer

### 8.1 What should carry return

Return should be distributed across four different mechanisms instead of asking one counter to do everything:

1. **Unfinished musical competence:** wanting to hold the next perturbation.
2. **Autonomous choice:** a personally selected next condition.
3. **Stable life cue:** an opt-in “when/where” practice plan.
4. **Human appointment:** when operationally possible, a real scheduled master or community event.

Implementation intentions and progress monitoring have strong general goal-attainment evidence, but the estimated effects cannot be imported as predicted product lifts. They support asking the player to choose a stable cue and showing neutral behavioral history. [Gollwitzer & Sheeran 2006](https://doi.org/10.1016/S0065-2601(06)38002-1), [Harkin et al. 2016](https://doi.org/10.1037/bul0000025)

### 8.2 Streak decision

The engagement mandate currently recommends a daily streak for Release 1. Research makes that defensible as a **persistence experiment**, not as a settled product truth.

Do not put the daily streak into the first experiment intended to prove the game. If both change at once, D7 cannot tell us whether players returned for the musical loop or to protect a counter.

After the core-loop test, randomize or stage:

| Arm | Mechanic | What it tests |
|---|---|---|
| **A — neutral history** | Days and completed rounds, no continuity asset | Baseline voluntary return |
| **B — repairable daily streak** | Visible intact streak, at least one non-monetized repair/grace mechanism | Maximum short-horizon continuity pressure with reduced break penalty |
| **C — rolling cadence** | Example: player-chosen weekly frequency | Whether flexibility outperforms a daily asset; **pure product hypothesis** |

Measure not only D7, but:

- Return after the first broken or missed intended day.
- D14 and D30.
- Full musical rounds, not notification opens.
- Self-reported pressure or guilt.
- Whether the player voluntarily plays after the counter is no longer salient.

### 8.3 Map and collection

A personal map can support curiosity and progress monitoring, but it also creates personal investment—a category included in addiction-risk frameworks. Use it as a bounded record of **encounters**, not a sacred collection or proof of mastery.

Recommended initial representation:

- Show states the player has visited.
- Do not imply that unvisited states are deficiencies.
- Never attach titles, authority, lineage, or master acknowledgment.
- Keep the play map resettable.
- Instrument versions with and without totals before assuming that completion pressure helps durable practice.

### 8.4 Celebration

The strongest celebration candidate remains musical resolution: re-entry, the full battery, and a real count-in. But calling the count-in “the strongest reward object” is a product hypothesis, not a research result.

Test at least two endings:

- Musical re-entry and clean close only.
- The same close plus a louder visual/play-layer celebration.

Junior must see and assent to any version that turns his voice or sacred-adjacent material into a repeated reward cue.

---

## 9. Release 1 proof slice

### 9.1 Minimum content

One rhythm and one beginner-accessible part are enough to test the atomic game. The prototype needs several complete, authority-approved arrangements rather than a large catalog:

1. Stable supported loop.
2. One-cycle reference dropout and re-entry.
3. Longer reference dropout and re-entry.
4. Increased auditory density while reference remains.
5. Increased density plus dropout.
6. Authentic call/turnaround and full return, only if musically applicable.

Use rough prototype audio only with the already-required consent hygiene. The shipped object still requires production-quality stems.

### 9.2 Control condition

The control must use:

- The same rhythm.
- The same master.
- The same total duration.
- The same interface quality.
- The same outer retention layer.

Its only difference is a stable play-along without authored perturbation/re-entry challenges. Otherwise the test confounds content quality, master presence, and interface novelty with the game mechanic.

### 9.3 First pilot

Use a small adult-practitioner usability/experience pilot before a retention test. The purpose is not statistical proof; it is to answer:

- Does the player understand the local objective without explanation?
- Is re-entry experienced as feedback or merely as audio change?
- Can a beginner hear alignment after the reference returns?
- Does dropout create useful exposure or simple confusion?
- Which challenge choice has meaning from arm's length?
- Does the player voluntarily start another round?
- Does any language feel like a verdict or borrowed authority?

### 9.4 Randomized product test

Hold notifications, streaks, map treatment, and onboarding constant while testing:

- **Control:** stable play-along.
- **Game:** mission + chosen challenge + perturbation + re-entry reveal + bounded ending.

Primary measures:

1. Voluntary second full round during the first session.
2. First-round and first-session completion.
3. D1, D3, D7, and D14 return.
4. Return after the first missed intended session.
5. Number of previously experienced rounds voluntarily replayed.

Secondary measures:

- Enjoyment.
- Perceived competence.
- Perceived autonomy.
- Pressure/guilt.
- Clarity of the musical objective.
- Desire to try a specific next condition.

The 2024 intrinsic-motivation meta-analysis noted that the underlying literature relied heavily on self-report and did not measure free-choice re-engagement. Opanijé should therefore make voluntary second-round choice a headline signal rather than using only a survey. [Li, Hew, & Du 2024](https://link.springer.com/article/10.1007/s11423-023-10337-7)

### 9.5 Learning claims

Product telemetry can establish behavior and reported experience. It cannot establish improved musicianship.

A learning-efficacy claim requires a separate, consented study with human pre/post assessment, blinded or standardized where feasible. That research record must stay outside the play ledger and Caderno unless the governing authority explicitly creates a valid recognition process.

---

## 10. Explicit exclusions and guardrails

Research review and product constitution converge on excluding:

- Paid or purchasable random rewards.
- Loot-box structures and engineered near-misses.
- Hearts, lives, energy, or timers that withdraw access.
- Endless-session defaults without a visible finish.
- False or simulated social presence.
- Synthetic master voice.
- Machine claims about timing quality, correctness, readiness, or mastery.
- Public rank that resembles standing.
- Badges or titles that look like master acknowledgment.
- Master voice attached to an upsell or price.
- Algorithmic rearrangement of governed material without authority-approved musical grammar.
- Manipulating the tradition's rhythm or syncopation because a laboratory groove study found another pattern pleasurable.
- Any game result writing into the Caderno.

---

## 11. Product decisions now required

The next decision is not “XP or streak?” It is whether the chosen musical material can support a self-validating perturbation loop.

### Question for Junior

Show, do not merely describe, three audio mockups:

1. Reference part disappears and returns after one cycle.
2. Reference part disappears while the rest of the battery continues.
3. An authentic call/turnaround produces a coordinated change and return.

Ask:

- Is each form musically real for this toque?
- Does any edit falsify how the part is learned or carried?
- Which instrument may function as the reference without becoming a generic metronome?
- How long can support disappear before the exercise ceases to represent the music?
- May these events be varied between complete recorded scripts?
- What must never be turned into a repeated challenge or celebration?

### Decision rule

- **If dropout/re-entry is valid:** build Hold & Rejoin as the primary Release 1 game.
- **If only calls/turnarounds are valid:** build Call Hunter around complete authored forms.
- **If neither is valid:** do not force the body recording into a game. Use the Room as an intrinsically rewarding play-along, and put the explicit game in Battery Detective/listening perception while keeping practice and game connected but distinct.

---

## 12. Final recommendation

Opanijé should aim for **harmonious engagement**: the player wants to return because the musical relationship is becoming more intelligible and inhabitable. Research distinguishes this from compelled play driven by pressure or unmet psychological needs. [Przybylski et al. 2009](https://doi.org/10.1089/cpb.2009.0083)

The revised hierarchy is:

1. **Core game:** Hold & Rejoin—master-authored perturbation with audible self-feedback.
2. **Optional cognitive hook:** Battery Detective or Call Hunter.
3. **Session shape:** rapid groove, one clear challenge, musical reveal, bounded resolution.
4. **Long loop:** chosen next condition, neutral encounter history, stable practice cue.
5. **Engagement experiments:** streak, rolling cadence, map totals, and celebration tested separately and instrumented per mechanic.
6. **Authority boundary:** Junior designs or assents to every sacred-adjacent musical transformation.

The central product bet becomes precise and falsifiable:

> **Players will voluntarily replay and return because they want to hold the relationship through the next lawful musical change—not merely because they fear losing a counter.**

---

## 13. Selected research base

### Gamification and game motivation

- Dai, W.-A., Xu, W., & Xing, Q.-W. (2025). *Gamified learning impact: a meta-analysis of game element combinations on students' learning outcomes.* [https://doi.org/10.1007/s11423-025-10493-y](https://doi.org/10.1007/s11423-025-10493-y)
- Li, L., Hew, K. F., & Du, J. (2024). *Gamification enhances student intrinsic motivation, perceptions of autonomy and relatedness, but minimal impact on competency.* [https://doi.org/10.1007/s11423-023-10337-7](https://doi.org/10.1007/s11423-023-10337-7)
- Mekler, E. D., Brühlmann, F., Tuch, A. N., & Opwis, K. (2017). *Towards understanding the effects of individual gamification elements on intrinsic motivation and performance.* [https://doi.org/10.1016/j.chb.2015.08.048](https://doi.org/10.1016/j.chb.2015.08.048)
- Ryan, R. M., Rigby, C. S., & Przybylski, A. (2006). *The motivational pull of video games: A self-determination theory approach.* [https://doi.org/10.1007/s11031-006-9051-8](https://doi.org/10.1007/s11031-006-9051-8)
- Sailer, M., & Homner, L. (2020). *The gamification of learning: A meta-analysis.* [https://doi.org/10.1007/s10648-019-09498-w](https://doi.org/10.1007/s10648-019-09498-w)

### Music, groove, and practice

- Bonneville-Roussy, A., & Evans, P. (2025). *The support of autonomy, motivation, and music practice in university music students.* [https://doi.org/10.1177/03057356241296109](https://doi.org/10.1177/03057356241296109)
- Cheung, V. K. M., et al. (2019). *Uncertainty and surprise jointly predict musical pleasure and amygdala, hippocampus, and auditory cortex activity.* [https://doi.org/10.1016/j.cub.2019.09.067](https://doi.org/10.1016/j.cub.2019.09.067)
- Evans, P., & Bonneville-Roussy, A. (2016). *Self-determined motivation for practice in university music students.* [https://doi.org/10.1177/0305735615610926](https://doi.org/10.1177/0305735615610926)
- Stupacher, J., et al. (2022). *Musical groove in brain, body, and social interactions.* [https://pmc.ncbi.nlm.nih.gov/articles/PMC9396343/](https://pmc.ncbi.nlm.nih.gov/articles/PMC9396343/)
- Valle, C., Andrade, H., Palma, M., & Hefferen, J. (2016). *Applications of peer and self-assessment in music education.* [https://doi.org/10.1177/0027432116644652](https://doi.org/10.1177/0027432116644652)
- Weatherly, K. I. C. H., Wright, B., & Lee, E. Y. (2024). *Digital game-based learning in music education: A systematic review from 2011 to 2023.* [https://doi.org/10.1177/1321103X241270819](https://doi.org/10.1177/1321103X241270819)
- Witek, M. A. G., et al. (2014). *Syncopation, body-movement and pleasure in groove music.* [https://doi.org/10.1371/journal.pone.0094446](https://doi.org/10.1371/journal.pone.0094446)

### Return, goals, and experience shape

- Alaybek, B., et al. (2022). *All's well that ends (and peaks) well? A meta-analysis of the peak-end rule and duration neglect.* [https://doi.org/10.1016/j.obhdp.2022.104149](https://doi.org/10.1016/j.obhdp.2022.104149)
- Gollwitzer, P. M., & Sheeran, P. (2006). *Implementation intentions and goal achievement: A meta-analysis of effects and processes.* [https://doi.org/10.1016/S0065-2601(06)38002-1](https://doi.org/10.1016/S0065-2601(06)38002-1)
- Harkin, B., et al. (2016). *Does monitoring goal progress promote goal attainment?* [https://doi.org/10.1037/bul0000025](https://doi.org/10.1037/bul0000025)
- Lally, P., et al. (2010). *How are habits formed: Modelling habit formation in the real world.* [https://doi.org/10.1002/ejsp.674](https://doi.org/10.1002/ejsp.674)
- Mehr, K. S., et al. (2025). *The motivating power of streaks: Increasing persistence is as easy as 1, 2, 3.* [https://doi.org/10.1016/j.obhdp.2025.104391](https://doi.org/10.1016/j.obhdp.2025.104391)
- Silverman, J., & Barasch, A. (2023). *On or off track: How (broken) streaks affect consumer decisions.* [https://doi.org/10.1093/jcr/ucac029](https://doi.org/10.1093/jcr/ucac029)

### Dysregulated play and gambling-like mechanics

- Clark, L., et al. (2009). *Gambling near-misses enhance motivation to gamble and recruit win-related brain circuitry.* [https://doi.org/10.1016/j.neuron.2008.12.031](https://doi.org/10.1016/j.neuron.2008.12.031)
- Garea, S. S., et al. (2021). *Meta-analysis of the relationship between problem gambling, excessive gaming and loot box spending.* [https://doi.org/10.1080/14459795.2021.1914705](https://doi.org/10.1080/14459795.2021.1914705)
- Rehbein, F., et al. (2021). *Contribution of game genre and structural game characteristics to the risk of problem gaming and gaming disorder.* [https://doi.org/10.1007/s40429-021-00367-7](https://doi.org/10.1007/s40429-021-00367-7)
- Saini, N., & Hodgins, D. C. (2023). *Investigating gaming structural features associated with gaming disorder and proposing a revised taxonomical model.* [https://pmc.ncbi.nlm.nih.gov/articles/PMC10316166/](https://pmc.ncbi.nlm.nih.gov/articles/PMC10316166/)
- Saini, N., et al. (2024). *Development of the Saini-Hodgins Addiction Risk Potential of Games (SHARP-G) Scale.* [https://doi.org/10.1556/2006.2024.00026](https://doi.org/10.1556/2006.2024.00026)
