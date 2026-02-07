# PILOT — QA Plan

**Author**: CRASH (QA Lead)
**Version**: 1.0
**Date**: 2026-02-07
**Status**: Pre-Production QA Planning

---

## 0. EXECUTIVE SUMMARY

Define "works."

PILOT is a management sim where the player is a TV network executive developing pilots, giving creative notes, and building a slate across 8 seasons spanning 2002-2010. The game is text-heavy, data-driven, and narrative-focused. The entire experience is 6-12 hours. The target platform is PC/Mac, eventual Switch port.

This is not a real-time action game. This is a decision-heavy workflow sim. The bugs will be systemic: broken state machines, incorrect stat calculations, save corruption, UI layout disasters, and — most critically — authored content that contradicts itself or makes the player feel stupid. Every bug has a player on the other end. Every missed bug is a 1-star review.

**The QA challenge**:
- 200 authored dilemmas × 3 options each = 600 decision nodes
- 80 pilot concepts with branching outcomes
- 8 seasons × 8-12 pilots per season = 64-96 pilot development cycles per playthrough
- 4-axis network brand system that compounds over hundreds of decisions
- Dynamic landscape simulation with rival networks and trend vectors
- Multi-layered economy (development budget, ad revenue, syndication, reputation currencies)

This is not a game you QA by clicking through once. This is a game you QA by running 20+ full playthroughs with different strategies, tracking every stat, logging every contradiction, and building regression test matrices that map content dependencies. The complexity is in the emergent interactions between systems, not the individual systems themselves.

**My job**: Find every edge case before the player does. Build a test plan that assumes the player will do the dumbest, weirdest, most adversarial thing possible. Test the happy path. Test the sad path. Test the evil path. Then test the path nobody thought to test.

---

## 1. SCOPE & PRIORITIES

### 1.1 P0: Critical Path — Game Must Be Completable

The player must be able to:
1. Start a new game
2. Complete all 8 seasons without crashes or soft locks
3. Reach the end-of-career retrospective
4. Save and load at any point without data corruption

If the critical path is broken, nothing else matters. This is table stakes.

### 1.2 P1: Core Gameplay Loops

The three core loops must function correctly:
1. **30-second loop**: Script triage (Pass/Consider/Priority, time token consumption, expiration)
2. **5-minute loop**: Pilot development (showrunner attachment, casting, notes, budget allocation, rough cut)
3. **Session loop (45-90 min)**: Full development season (desk -> pipeline -> upfronts -> broadcast -> metrics update)

If any of these loops feels broken, players disengage. These are the mechanical pillars.

### 1.3 P2: Systemic Simulation

The interlocking systems must produce coherent, believable outcomes:
- Ratings calculations (do high-quality shows with star power actually rate well?)
- Budget economy (can the player go bankrupt? Can they print infinite money?)
- Network brand accumulation (do 100 small decisions create a visible identity?)
- Landscape trends (do rival hits actually shift audience appetite?)
- Showrunner relationships (does trust decay and recovery feel earned?)

If the simulation produces nonsensical results, the fantasy breaks. The player stops trusting the game.

### 1.4 P3: Content Integrity

The authored content (dilemmas, scripts, events) must be internally consistent:
- Dilemmas must present genuine trade-offs (no obvious "correct" options)
- Stat deltas must be balanced (no single note giving +50 quality)
- Character voices must be consistent across multiple appearances
- Historical events must arrive in logical sequence

If content contradicts itself, immersion dies. The player sees the seams.

### 1.5 P4: UI/UX & Polish

The interface must communicate state clearly:
- The desk must be legible with 15+ scripts stacked
- The whiteboard pipeline must surface attention flags correctly
- The upfronts presentation must feel climactic, not perfunctory
- All critical information must be readable at 1080p (and legible at 720p for Switch)

If the UI lies to the player or hides critical information, the player makes uninformed decisions and blames the game.

---

## 2. TEST PLAN BY FEATURE AREA

### 2.1 DESK SYSTEM (Script Triage)

**What This Is**: The information-management layer. 15-20 scripts arrive over 4-5 days. Player triages under time pressure. Scripts expire if ignored.

**Happy Path Tests**:
- [ ] Spawn 15 scripts at start of pitch season
- [ ] Skim a script (5 sec, see logline/genre/grade)
- [ ] Standard read a script (15 sec, see blind-spot indicators)
- [ ] Deep read a script (30 sec, consumes 1 time token, reveals hidden quality variance and notes preview)
- [ ] Pass a script (removed from desk, rival may pick it up)
- [ ] Consider a script (moved to hold pile, clock still ticking)
- [ ] Priority a script (moves to development pipeline)
- [ ] Scripts expire after countdown reaches 0 (notification displays, rival network picks it up)
- [ ] Time tokens replenish daily (3 per day)
- [ ] Desk interface correctly displays 15 scripts without layout collapse

**Sad Path Tests** (Things Go Wrong):
- [ ] Attempt deep read with 0 time tokens (should be blocked, show "Out of time tokens" message)
- [ ] Let all 15 scripts expire without action (rivals grab everything, desk empties, player gets scolded by President)
- [ ] Priority 12 scripts in one day (pipeline should warn about capacity, or throttle intake)
- [ ] Spam-click Pass on all scripts (test that removal from queue is immediate and does not cause index-out-of-bounds)
- [ ] Save game mid-triage with 8 scripts on desk, load save, verify all 8 scripts restore with correct expiration timers
- [ ] Script with expiration timer = 1 day: advance 1 day, verify it expires before new scripts arrive

**Evil Path Tests** (Player Is Adversarial):
- [ ] Deep read the same script 3 times (should not consume 3 tokens or provide new info — idempotent)
- [ ] Priority a script, then try to Pass it from the pipeline (should not be possible — script is no longer on desk)
- [ ] Load a save from Season 2 while in Season 5 (test save slot isolation — should not corrupt Season 5 state)
- [ ] Fill the Consider pile with 10 scripts, let them all expire simultaneously (test batch expiration handling)
- [ ] Alt-tab away during script reading (test that timers do not tick while game is paused/backgrounded)

**Edge Cases**:
- [ ] Script with hiddenQualityVariance = +20 (coverage grade C+, actual quality A-). Deep read reveals it. Verify player sees the upward revision.
- [ ] Script with hiddenQualityVariance = -15 (coverage grade A, actual quality B). Deep read reveals it. Verify player sees the downward revision.
- [ ] Script expires on the SAME turn that player tries to Priority it (race condition). Which action wins? Document behavior.
- [ ] Rival network picks up a script player passed. That script becomes a hit on rival network. Player sees headline. Verify headline fires and references correct script logline.
- [ ] Desk UI with 20 scripts (max capacity). Spawn 21st script. What happens? Overflow handling or queue cap?

**Performance Tests**:
- [ ] Desk with 20 scripts, drag all 20 around rapidly. Measure frame time. Should stay above 60fps on target hardware (2019 MacBook Pro).
- [ ] Desk with 20 scripts, spam Pass button on all 20 as fast as possible. Verify no UI stutter or hangs.

**Regression Checklist** (Post-Fix Verification):
- [ ] After any desk UI change, re-run all Happy Path tests
- [ ] After any script data structure change, verify save/load still works
- [ ] After any expiration timer change, verify race conditions do not reappear

---

### 2.2 DEVELOPMENT PIPELINE SYSTEM

**What This Is**: 8-12 simultaneous pilots moving through phases: Showrunner Attachment -> Casting -> Notes -> Production -> Greenlight Decision. Attention flags surface projects that need player decisions.

**Happy Path Tests**:
- [ ] Priority a script from desk, verify it appears in pipeline as new project
- [ ] Assign showrunner to project (from list of 3-5 available showrunners)
- [ ] View showrunner fit score (0-100). Verify score calculation matches design spec (sum of tonal axis diffs × 5, clamped 0-100).
- [ ] Assign cast to project (1-3 casting slots, each with 3-4 actor options)
- [ ] Allocate production budget across 5 categories (Writing Room, Production Design, Directing, Post, Marketing). Verify sum = 100%.
- [ ] Enter Notes phase. Receive 2-3 dilemmas. Make choices. Verify deltas apply to pilot's qualityCeiling, commercialFloor, showrunner trust.
- [ ] Advance to Pilot Production. Rough cut generates. Test audience simulation runs. Verify test scores appear.
- [ ] Enter Final Notes phase. Receive 2-3 more dilemmas. Make choices. Verify deltas stack with Early Notes deltas.
- [ ] Pilot reaches AWAITING_GREENLIGHT state. Verify it appears in upfronts selection pool.
- [ ] Successfully shepherd 8 pilots through pipeline in one season without crashes.

**Sad Path Tests**:
- [ ] Assign showrunner with Ego 9 to a project. Give note that drops showrunner trust below 20. Verify showrunner conflict fires (attention flag, possible walkout).
- [ ] Allocate budget 40/30/20/5/5 (valid). Then try to allocate 50/30/30/10/10 (sums to 130%). Verify validation error.
- [ ] Production goes over budget (low Reliability showrunner). Verify budget overrun attention flag fires.
- [ ] Test audience score comes back at 28 (catastrophic). Verify attention flag fires, player gets mid-development decision prompt.
- [ ] Showrunner with trust < 30 receives a commercial note. Verify resistance: note effect reduced by X% (design spec says 30% reduction).
- [ ] Kill a pilot mid-development (player chooses to cancel before rough cut). Verify project moves to "dead pilots" drawer, budget is partially refunded, showrunner trust takes hit.
- [ ] Pilot with perfect Synergy (fit score 95+) but showrunner Vision 3. Verify quality ceiling is mediocre despite perfect fit.

**Evil Path Tests**:
- [ ] Develop 12 pilots simultaneously (max capacity). Attempt to Priority a 13th script. What happens? Queue full? Denial message?
- [ ] Assign a showrunner to Project A. Before Project A completes, try to assign the same showrunner to Project B. Should be blocked (showrunner is unavailable).
- [ ] Showrunner completes Project A (success). Immediately assign them to Project B in the same season. Verify showrunner is available (no cooldown) and trust carries over.
- [ ] Give 10 commercial notes in a row (across multiple pilots). Verify network brand shifts toward Populist/Safe. Then give 10 auteur notes. Verify brand shifts back toward Prestige/Risk-Taking. Test axis swing range.
- [ ] Save game mid-pipeline with 6 pilots in various states (2 in casting, 3 in notes, 1 awaiting greenlight). Load save. Verify all 6 pilots restore to correct states.
- [ ] Showrunner with Loyalty 2 completes a hit show (10M viewers, quality 75). Next season, check if showrunner is still available or defected to cable. Verify cable poaching logic.

**Edge Cases**:
- [ ] Pilot with showrunner fit score 25 (Mismatch). Design spec says 30% chance showrunner walks. Run this scenario 10 times. Verify walkout occurs ~3/10 times. Verify a replacement showrunner is auto-assigned with reduced stats.
- [ ] Pilot with showrunner fit score 25, but also "creative friction breakthrough" (20% chance). Verify breakthrough can fire and raises quality ceiling by +20.
- [ ] Pilot with qualityCeiling 90 after notes. Budget allocation heavily skewed to Marketing (30%). Verify Marketing does not affect quality, only affects upfronts presentation.
- [ ] Pilot with commercialFloor 30, qualityCeiling 85. Test audience simulation: overall score 42, but 18-34 demo score 78. Verify demo breakdown displays correctly and player sees the split.
- [ ] Attention flag priority: pilot has BUDGET_OVERRUN and SHOWRUNNER_CONFLICT simultaneously. Verify UI surfaces both flags, does not drop one.

**Performance Tests**:
- [ ] Pipeline with 10 simultaneous pilots. Drag all 10 index cards around whiteboard rapidly. Measure frame time. Should stay 60fps.
- [ ] Pipeline with 10 pilots. Spam "Advance Phase" button on all 10. Verify state transitions complete without hangs.

**Regression Checklist**:
- [ ] After any showrunner fit calculation change, re-run all fit score tests
- [ ] After any budget allocation change, verify percentage validation still works
- [ ] After any attention flag logic change, verify flags fire correctly in isolation and in combination

---

### 2.3 NOTES SYSTEM (Creative Dilemmas)

**What This Is**: The soul of the game. Player is presented with 2-4 specific creative dilemmas per pilot. Each dilemma has 2-3 options. Options modify pilot stats, showrunner trust, network brand axes.

**Happy Path Tests**:
- [ ] Trigger Early Notes phase on a pilot. Verify 2-3 dilemmas appear.
- [ ] Read dilemma context text. Select Option A. Verify deltas apply (qualityCeiling, commercialFloor, showrunner trust, brand axes).
- [ ] Read dilemma. Select Option B. Verify different deltas apply.
- [ ] Complete all dilemmas in Early Notes. Verify pilot advances to next phase.
- [ ] Trigger Final Notes phase (post-rough-cut). Verify 2-3 NEW dilemmas appear (not repeats from Early Notes).
- [ ] Complete Final Notes. Verify all deltas from Early + Final Notes have compounded correctly on pilot.
- [ ] Verify flavor text appears after each note choice ("The showrunner nods, relieved" / "The showrunner's face hardens").

**Sad Path Tests**:
- [ ] Dilemma with missing option delta (qualityCeilingDelta field is null). Should not crash. Log error, use default delta 0.
- [ ] Dilemma references a pilot tag that does not exist ("antihero" tag, but pilot has no antihero). Verify dilemma does not appear in selection pool.
- [ ] Pilot has 6 dilemmas assigned in scriptData, but only 3 are valid for current genre. Verify selection logic filters correctly and presents 2-3 valid dilemmas, not 6.
- [ ] Player gives a note that drops showrunner trust from 50 to 35. Same pilot, next notes phase, player gives another harsh note. Verify trust continues dropping (no floor except 0).
- [ ] Player gives a note that shifts Prestige axis from 50 to 53. Next note shifts it to 56. Repeat 50 times. Verify axis caps at 100, does not overflow.

**Evil Path Tests**:
- [ ] Save game mid-dilemma (player has read context text but not selected an option). Load save. Verify dilemma re-appears, player can still choose.
- [ ] Select Option A on Dilemma 1. Immediately alt-tab and force-quit game before delta applies. Restart game. Load autosave. Verify choice was either committed or rolled back (not in inconsistent state).
- [ ] Give 20 notes in a row that all shift Prestige +3. Verify brand axis reaches 100 and stops (does not overflow to negative via integer wrap).
- [ ] Give 20 notes in a row that all shift Prestige -3. Verify brand axis reaches 0 and stops.
- [ ] Pilot with 8 dilemmas assigned in scriptData. Early Notes presents 3. Final Notes presents 3 more. Verify the same dilemma never appears twice for the same pilot.
- [ ] Pilot A and Pilot B both use Dilemma ID "dilemma_antihero_001" because both have antihero protagonists. Verify this is allowed (dilemmas are reusable across pilots).

**Edge Cases**:
- [ ] Dilemma with Option A giving qualityCeiling +15, Option B giving +0, Option C giving -12. Player chooses Option A on a pilot with qualityCeiling 88. New ceiling: 103. Verify game clamps to 100, does not allow >100.
- [ ] Dilemma with Option A giving showrunner trust +10, but showrunner already has trust 95. New trust: 105. Verify clamps to 100.
- [ ] Dilemma with Option A giving presidentTrustDelta -20, but president patience is currently 15. New patience: -5. Verify clamps to 0 and triggers GAME OVER if patience hits 0.
- [ ] Pilot with qualityCeiling 50, commercialFloor 60 (commercial floor higher than ceiling — edge case but possible if player gives ONLY commercial notes). Verify ratings calculation does not break (use max of floor and ceiling, or handle gracefully).
- [ ] Dilemma text contains a character name ("Tommy Morell") that is also a recurring showrunner character. Verify name consistency across all appearances.

**Content-Specific Tests** (Sample 10 Dilemmas Deeply):
- [ ] Dilemma: "The Antihero Question" (protect vision vs. add humanizing scene vs. mandate redemption arc). Verify each option produces meaningfully different outcomes in test audience scores and ratings.
- [ ] Dilemma: "The Expensive Shot" (protect $1.2M tracking shot vs. compromise at $600K vs. cut it). Verify budget allocation reflects choice, visual quality stat reflects choice.
- [ ] Dilemma: "The Test Audience Problem" (trust 18-34 demo vs. hybrid re-edit vs. linear re-edit). Verify overall test score changes based on choice, demo breakdown changes.
- [ ] Dilemma: "The Love Triangle" (no love triangle vs. subtle tension vs. mandate triangle). Verify showrunner trust delta, verify "showrunner may walk" event fires if Option C chosen and trust < 40.
- [ ] Verify that no dilemma has an option that is ALWAYS optimal (i.e., "+10 quality, +10 commercial, +10 trust, no downside"). Flag for rebalance.
- [ ] Verify that every dilemma has at least one option with a trade-off (something goes up, something else goes down).
- [ ] Check all 200 dilemmas for typos, formatting errors, missing fields.
- [ ] Check all 200 dilemmas for tone consistency (no joke dilemmas in a serious game, no anachronisms like "went viral" in 2003).
- [ ] Verify all flavor text is authored and contextually appropriate (not placeholder text like "The showrunner reacts").
- [ ] Cross-check dilemma IDs referenced in scriptData against DilemmaDB. No orphaned IDs.

**Balance Tests**:
- [ ] Run 10 full playthroughs. In each playthrough, give ONLY commercial notes (always pick the option with highest commercialFloor delta). Track final network brand, final revenue, final president patience. Verify this strategy produces: High Populist/Safe brand, high revenue, low prestige, low industry reputation. Should be viable but not dominant.
- [ ] Run 10 full playthroughs. Give ONLY auteur notes (always pick highest qualityCeiling delta). Track outcomes. Verify: High Prestige/Risk-Taking brand, low revenue, high industry reputation, possible budget crisis by Season 5-6.
- [ ] Run 10 full playthroughs with MIXED strategy (alternate commercial and auteur notes). Track outcomes. Verify: Balanced brand, moderate revenue, moderate reputation. Should be the most forgiving strategy.
- [ ] Flag any dilemma where one option is chosen >70% of the time across all playthroughs. Investigate why. Is it overpowered? Rebalance.

**Regression Checklist**:
- [ ] After any dilemma delta change, re-run all balance tests
- [ ] After any dilemma text edit, verify no new typos introduced
- [ ] After any brand axis logic change, verify notes still shift axes correctly

---

### 2.4 UPFRONTS SYSTEM

**What This Is**: The seasonal climax. Player selects 2-4 pilots to greenlight, arranges presentation order, assigns sell lines, presents to advertisers. Ad buyer confidence determines ad revenue.

**Happy Path Tests**:
- [ ] Reach upfronts with 6 pilots in AWAITING_GREENLIGHT state.
- [ ] Select 3 pilots for series order.
- [ ] Arrange presentation order (drag to reorder).
- [ ] Assign sell line to each pilot (Prestige Play / Demo Magnet / Conversation Starter).
- [ ] Start presentation. Watch ad buyer confidence meter fill for each pilot.
- [ ] Complete presentation. View ad revenue commit summary.
- [ ] Verify selected pilots transition to GREENLIT state, series data created.
- [ ] Verify rejected pilots transition to KILLED state, move to dead pilots drawer.
- [ ] Verify total ad revenue matches sum of per-pilot revenue calculations.

**Sad Path Tests**:
- [ ] Reach upfronts with only 1 pilot available (player killed most projects mid-development). Verify player can still present 1 pilot, upfronts does not break.
- [ ] Reach upfronts with 0 pilots available (player killed ALL projects). What happens? Game over? President fires you? Document behavior.
- [ ] Select 4 pilots. Assign sell line "Prestige Play" to a pilot with qualityCeiling 45 (low quality). Design spec says this risks backlash. Verify ad confidence is LOW (not high).
- [ ] Assign sell line "Conversation Starter" to a pilot on a network with culturalFootprint 30 (low). Design spec says bonus is 0. Verify no bonus applied.
- [ ] Present pilots in order: Weak -> Weak -> Strong. Verify ad buyer confidence is low for first two, high for third. Verify presentation order matters.
- [ ] Save game mid-upfronts (after selecting pilots but before presentation). Load save. Verify presentation restarts correctly.

**Evil Path Tests**:
- [ ] Select 3 pilots for greenlight. Force-quit game before presentation completes. Restart game, load autosave. Verify greenlight decisions are either committed or rolled back (not in inconsistent state).
- [ ] Present the same pilot twice (should not be possible, but test). Verify UI prevents duplicate selection.
- [ ] Select 0 pilots, attempt to advance to season broadcast. Verify error handling (cannot advance with 0 greenlights).
- [ ] Select 4 pilots, all with commercialFloor < 30 (all weak). Present them. Verify ad revenue is low across the board, president patience drops significantly.

**Edge Cases**:
- [ ] Pilot with commercialFloor 80, qualityCeiling 90, Star Power 8, presented in slot 1 (lead position), sell line "Demo Magnet". Calculate expected ad confidence. Verify actual ad confidence matches formula from tech doc.
- [ ] Pilot with commercialFloor 30, qualityCeiling 85, Star Power 2, sell line "Prestige Play". Verify ad confidence is LOWER than if sell line were "Demo Magnet" (risky sell line on low commercial floor).
- [ ] Pilot presented in Thursday 9pm slot. Verify slot multiplier is 1.3× (per tech spec). Compare revenue to same pilot in Friday 10pm slot (0.7× multiplier). Difference should be ~85%.
- [ ] Upfronts with 6 pilots, player selects 4 (the max). Verify UI correctly handles max capacity, does not allow 5th selection.
- [ ] Upfronts with 2 pilots (low development throughput). Verify presentation still feels complete, does not feel truncated or broken.

**Performance Tests**:
- [ ] Upfronts presentation sequence with 4 pilots. Measure total time. Should complete in 5-7 minutes (design target). If <3 minutes, too fast (not climactic). If >10 minutes, too slow (drags).
- [ ] Upfronts with 4 pilots, rapidly click through presentation. Verify no animation skips, no UI glitches.

**Regression Checklist**:
- [ ] After any ad confidence formula change, re-run all edge case calculations
- [ ] After any upfronts UI change, verify pilot selection and reordering still works
- [ ] After any revenue calculation change, verify revenue matches expected values

---

### 2.5 SEASON BROADCAST & RATINGS SYSTEM

**What This Is**: Greenlit series air weekly. Ratings calculated from commercialFloor + quality + trends + variance. Mid-season decisions: renewal, cancellation, schedule moves. End-of-season metrics update.

**Happy Path Tests**:
- [ ] Greenlight 3 series. Season starts. Verify weekly ratings appear for all 3 series.
- [ ] Series with high quality (75+) and strong star power. Verify ratings are HIGH (8M+ viewers).
- [ ] Series with low quality (50) and weak star power. Verify ratings are LOW (3M viewers).
- [ ] Reach episode 6 of a series. Trigger mid-season decision (extend episode order / cancel / schedule move).
- [ ] Complete full 13-episode season for a series. Verify total viewership accumulates correctly.
- [ ] Reach end of season. Verify metrics update: revenue calculated, president patience adjusted, industry reputation adjusted, budget for next season updated.

**Sad Path Tests**:
- [ ] Series with commercialFloor 40, qualityCeiling 80. Week 1 rating: 6M. Week 2: 5M (dropoff). Week 3: 4.8M (continued decline). Verify natural audience erosion for struggling shows.
- [ ] Series ratings fall below projections by 30%. Verify mid-season cancellation option appears.
- [ ] Cancel series mid-season. Verify showrunner trust drops, dead series moves to history log.
- [ ] Series over-performs (ratings 30% above projection). Verify mid-season episode extension option appears.
- [ ] Extend episode order from 13 to 22. Verify budget cost increases by $2-4M, verify additional episodes air.
- [ ] Season ends with operating deficit (total costs > total revenue). Verify budget for next season is reduced, president patience drops.

**Evil Path Tests**:
- [ ] Run 8 full seasons giving ONLY terrible notes (always pick lowest qualityCeiling option). Verify all shows flop, revenue crashes, president patience hits 0 by Season 4-5, game over triggers.
- [ ] Run 8 full seasons giving ONLY perfect notes. Verify player can build a sustainable, profitable network with minimal failures.
- [ ] Greenlight 4 series, all expensive ($4M/episode production cost). Verify budget strain is SEVERE. Verify player cannot sustain 4 expensive shows simultaneously without high ad revenue.
- [ ] Greenlight 4 series, all cheap ($1.5M/episode). Verify player has budget surplus but lower quality/ratings ceiling.
- [ ] Cancel all 3 series mid-season in the same week. Verify network slate is empty for remainder of season, ad revenue plummets, president patience craters.

**Edge Cases**:
- [ ] Series with qualityCeiling 75, commercialFloor 50, genre SerializedDrama. Landscape serializationAppetite = 70 (high). Verify trend alignment bonus applies (+5-8M viewers).
- [ ] Same series, same stats, but serializationAppetite = 30 (low). Verify trend alignment bonus is 0 or negative.
- [ ] Series airs on Thursday 9pm (premium slot). Verify time slot bonus is +3M viewers (per ratings formula).
- [ ] Same series moved mid-season to Friday 10pm (death slot). Verify time slot bonus becomes -2M viewers.
- [ ] Series with DVR-heavy audience (serialized drama in 2006, dvrAdoption = 30%). Verify DVR time-shift bonus applies, but advertisers pay less (CPM reduced).
- [ ] Series runs for 4 seasons, becomes eligible for syndication. Verify syndication revenue appears in end-of-season summary. Verify episodic shows get +30% syndication value vs. serialized shows.

**Ratings Formula Validation** (Critical):
- [ ] Manually calculate expected viewership for a test series using formula from tech doc:
  ```
  Viewership = commercialFloor + (quality * 0.15) + (starPower * 0.3) + slotValue + trendBonus + random(-1.5, +1.5)
  ```
  Compare expected vs. actual. Variance should be within random range. If delta > 2M, formula is broken.
- [ ] Run ratings calculation 1000 times for same series. Verify variance stays within [-1.5, +1.5] range. Verify no outliers (e.g., 20M viewers on a show with commercialFloor 40).

**Performance Tests**:
- [ ] Season with 4 series, 22 episodes each = 88 rating calculations. Verify all calculations complete in <10ms total (per tech doc estimate: ~1760 float ops).
- [ ] Season with 4 series, advance week by week 22 times. Verify no frame drops, no UI hangs.

**Regression Checklist**:
- [ ] After any ratings formula change, re-validate all edge cases
- [ ] After any mid-season decision logic change, verify triggers fire correctly
- [ ] After any metrics update logic change, verify end-of-season budget/reputation calculations match design

---

### 2.6 NETWORK BRAND SYSTEM

**What This Is**: Player's cumulative decisions create a 4-axis brand identity (Prestige/Populist, Risk-Taking/Safe, Auteur/Producer, Serialized/Episodic). Brand has mechanical effects.

**Happy Path Tests**:
- [ ] Start new game. Verify all 4 axes start at 50 (neutral).
- [ ] Give 10 notes that shift Prestige +3 each. Verify Prestige axis is now 80.
- [ ] Give 10 notes that shift RiskTaking +2 each. Verify RiskTaking axis is now 70.
- [ ] Check network persona label. Should read "Prestige Risk-Taker" (per persona logic in tech doc).
- [ ] Verify brand effects apply: +20% chance to attract high-Vision showrunners, +5 critical score bonus, advertisers pay 10% less.
- [ ] View radar chart in office. Verify chart updates at end of season, all 4 axes visible.

**Sad Path Tests**:
- [ ] Brand with Prestige 75, RiskTaking 80. Season ends with 2 expensive flops. Verify budget crisis triggers (per design: High Risk + failures = budget squeeze).
- [ ] Brand with Prestige 25 (High Populist). Check incoming script pool next season. Verify high-Vision showrunners are 30% less likely to submit (per brand effects).
- [ ] Brand with RiskTaking 25 (High Safe). Check qualityCeiling for all pilots. Verify ceiling is capped at 80 (per design: safe networks never produce masterpieces).
- [ ] Brand with Auteur 75 (High Auteur). Develop 3 pilots with high-Ego showrunners. Verify budget overrun risk is +15% across all 3.
- [ ] Brand with Serialized 75. Launch 2 serialized shows. Verify casualViewerAcquisition is -20%, but DVR time-shift bonus is +10%.

**Evil Path Tests**:
- [ ] Force Prestige axis to 100 by giving 20 prestige notes. Verify axis caps at 100. Give 5 more prestige notes. Verify axis stays at 100 (does not overflow).
- [ ] Force Prestige axis to 0 by giving 20 populist notes. Verify axis floors at 0. Give 5 more populist notes. Verify axis stays at 0 (does not underflow).
- [ ] Swing Prestige axis from 0 to 100 over 8 seasons (oscillate between extreme prestige and extreme populist notes). Verify persona label updates correctly at each extreme.
- [ ] Brand with all 4 axes at 50 (perfectly balanced). Check persona label. Should read "Balanced Network". Verify no special modifiers apply (neutral state).

**Edge Cases**:
- [ ] Brand crosses Prestige threshold from 69 to 71 (enters High Prestige). Verify brand effects activate: showrunner attraction bonus, critical score bonus, advertiser pay penalty.
- [ ] Brand crosses Prestige threshold from 71 to 69 (exits High Prestige). Verify brand effects deactivate.
- [ ] Brand with Prestige 70, RiskTaking 70, Auteur 70, Serialized 70 (all high). Check persona label. Multiple possible labels apply. Verify game picks one consistently (per persona priority logic).
- [ ] Brand persona "Prestige Risk-Taker" in Season 3. Check trade magazine headlines. Verify headline references brand ("Is [Network] Becoming Too Prestige for Its Own Good?").
- [ ] Brand shifts significantly (any axis moves 15+ points in one season). Verify trade magazine headline fires, player is notified of brand shift.

**Content Validation**:
- [ ] Check all 200 dilemmas. Verify every dilemma that modifies brand axes specifies which axis and by how much (no "mystery modifiers").
- [ ] Verify brandShift deltas are reasonable: typical range should be +/-1 to +/-4 per note. Flag any dilemma with +/-10 or more (likely balance issue).
- [ ] Cross-check brand effects in code against design doc. Verify High Prestige = advertiser pay 0.9×, not 0.8× or 1.1×. Verify all effects match spec exactly.

**Regression Checklist**:
- [ ] After any brand axis logic change, re-run all threshold tests
- [ ] After any persona label logic change, verify labels match design intent
- [ ] After any brand effects change, verify effects apply correctly at gameplay level

---

### 2.7 LANDSCAPE SIMULATION SYSTEM

**What This Is**: 6 trend vectors shift each season (serializationAppetite, antiHeroTolerance, genreAcceptance, realitySaturation, cablePrestigeThreat, dvrAdoption). Historical events arrive at fixed seasons. Rival networks develop their own slates.

**Happy Path Tests**:
- [ ] Start Season 1 (2002). Verify starting trend values: serializationAppetite 35, antiHeroTolerance 30, genreAcceptance 25, realitySaturation 40, cablePrestigeThreat 30, dvrAdoption 15 (per tech doc).
- [ ] Complete Season 1. Historical event: "Cable drama wins first major Emmy". Verify cablePrestigeThreat increases by 8.
- [ ] Complete Season 3. Historical event: "Serialized mystery becomes #1 show". Verify serializationAppetite increases by 20, genreAcceptance increases by 15.
- [ ] Complete Season 6. Historical event: "Writers' Strike". Verify all development halts for 1 cycle (player cannot prioritize new scripts during strike).
- [ ] Verify industry signals appear before major trend shifts (trade headlines hint at what's coming).

**Sad Path Tests**:
- [ ] Player ignores serializationAppetite trend. Develops only procedurals. Season 3 hits, serializationAppetite spikes to 55. Verify player's procedurals do NOT benefit from trend, ratings stagnate.
- [ ] Player bets heavily on serialized dramas in Season 2 (serializationAppetite still low at 35). Verify shows struggle initially (low trend alignment bonus).
- [ ] Rival network launches a breakout serialized hit in Season 2. Verify serializationAppetite increases by 3-6 (rival success accelerates trend).
- [ ] Rival network launches an expensive serialized flop. Verify no trend boost (failures do not shift trends).

**Evil Path Tests**:
- [ ] Writers' Strike in Season 6. Player has 10 pilots in pre-production (high pipeline load). Verify strike shuts down pipeline, costs are sunk, player has nothing to air. Verify budget crisis is severe.
- [ ] Writers' Strike in Season 6. Player has 3 series already in production. Verify those series continue airing (pre-strike content), player survives the gap.
- [ ] Force all 6 trends to 100 (via external save file edit). Verify game does not break. Verify trends still produce coherent gameplay effects.
- [ ] Force all 6 trends to 0. Verify game does not break. Verify neutral/negative trend state is playable.

**Rival Network AI Tests**:
- [ ] Rival "Titan Broadcasting" has SAFE strategy. Check their slate over 3 seasons. Verify they pick high-commercialFloor scripts, avoid risky genres (SciFi, SerializedDrama).
- [ ] Rival "Sterling Network" has AGGRESSIVE strategy. Check their slate. Verify they pick high-qualityCeiling scripts, embrace risk (SerializedDrama, PrestigeLimited).
- [ ] Rival "Pacific Channel" has REACTIVE strategy. Player launches a hit WorkplaceComedy. Next season, check Pacific's slate. Verify they develop WorkplaceComedy (copycat behavior).
- [ ] Rival greenlights a script player passed on. That show becomes a hit (10M+ viewers). Verify player sees trade headline: "[Rival] Hits Big with [Logline Player Passed On]". Verify player feels regret (this is a design goal).
- [ ] Rival greenlights a script player passed on. That show flops (3M viewers). Verify player does NOT see a headline (flops are not newsworthy).

**Edge Cases**:
- [ ] Season 3 event: serializationAppetite +20. Current value: 48. New value: 68. Plus random drift +2. Final value: 70. Verify calculation is correct, not 48+20+2 = 70 (check for rounding errors).
- [ ] Trend reaches 100. Historical event tries to increase it by 8. Verify trend caps at 100, does not overflow to 8.
- [ ] Trend is at 5. Random drift is -3. New value would be 2. Verify trend floors at 0, not negative.
- [ ] Industry signal: "Nielsen reports 22% of 18-34 viewers own a DVR". Next season, dvrAdoption increases. Verify signal probability (signal hints but does not guarantee exact shift).
- [ ] Run 10 playthroughs. Track historical events. Verify events fire at fixed seasons (Season 1 = cable Emmy, Season 3 = serialized hit, Season 6 = strike). Verify event magnitude varies slightly (+/-2 points) but event always occurs.

**Performance Tests**:
- [ ] Landscape simulation runs once per season. Verify `AdvanceSeason()` completes in <1ms (per tech doc).
- [ ] Rival AI for 3 networks, each developing 3 pilots. Verify total AI simulation time <5ms per season.

**Regression Checklist**:
- [ ] After any trend shift logic change, re-validate all historical events
- [ ] After any rival AI change, verify SAFE/AGGRESSIVE/REACTIVE strategies still produce distinct behaviors
- [ ] After any event text change, verify text is typo-free and contextually accurate

---

### 2.8 SHOWRUNNER RELATIONSHIP SYSTEM

**What This Is**: Showrunners have stats (Vision, Craft, Heat, Ego, Reliability, Loyalty) and a trust relationship (0-100) with the player. Trust affects note compliance, return probability, and public conflicts. Showrunners evolve over time: burnout, cable poaching, heat decay.

**Happy Path Tests**:
- [ ] Assign showrunner to pilot. Initial trust: 50 (neutral).
- [ ] Give 3 notes that increase trust (+5, +8, +10). New trust: 73. Verify trust accumulates correctly.
- [ ] Complete pilot successfully. Showrunner has trust 73. Next season, check if showrunner returns with new project. Design spec: trust >70 = 80% return chance. Run this 10 times, verify ~8/10 returns.
- [ ] Showrunner completes hit show (10M viewers, quality 75). Check showrunner stats next season. Verify Heat +2, Ego +1.
- [ ] Showrunner completes flop (3M viewers). Check stats. Verify Heat -2.

**Sad Path Tests**:
- [ ] Give 5 harsh notes to showrunner (trust drops from 50 to 20). Verify showrunner becomes adversarial: note compliance reduced by 30% (note effects are weaker).
- [ ] Trust drops below 20 during development. Verify public conflict event fires: trade headline, network reputation takes hit.
- [ ] Showrunner with trust 15 completes project. Next season, check return probability. Design spec: trust <30 = 10% return chance. Run this 10 times, verify ~1/10 returns.
- [ ] Showrunner with Ego 9 completes 3 consecutive projects. Design spec: 20% burnout risk. Run this 10 times, verify ~2/10 burn out. If burnout occurs, verify Vision -3, Reliability -2.
- [ ] Showrunner with Vision 9, Loyalty 2. Landscape cablePrestigeThreat >60. Design spec: 25% chance of cable defection. Run this 10 times, verify ~2-3/10 defect. If defection occurs, verify showrunner is no longer available.

**Evil Path Tests**:
- [ ] Give 30 harsh notes across multiple pilots over 8 seasons. Verify trust can drop to 0 (floor) and does not underflow to negative.
- [ ] Give 30 supportive notes. Verify trust can reach 100 (cap) and does not overflow.
- [ ] Showrunner with trust 100, Loyalty 10. Player mistreats them on one project (trust drops to 60). Next season, check if they return. Verify past trust history matters (Loyalty stat should increase return chance even if current trust is moderate).
- [ ] Showrunner burns out (Vision drops from 9 to 6). Next project, check qualityCeiling contribution. Verify burned-out showrunner produces lower-quality pilots.
- [ ] Showrunner defects to cable. Verify they disappear from available showrunner pool. Check dead pilots drawer / career retrospective. Verify defection is logged.

**Edge Cases**:
- [ ] Showrunner with Ego 9, trust 85. Give a note that drops trust to 83. Design spec: Ego >7 showrunners resist notes aggressively. Verify note effect is reduced, but not blocked entirely (resistance is partial, not total).
- [ ] Showrunner with Vision 10, Craft 10, Heat 10 (perfect stats). Complete a hit show. Check stats next season. Verify Heat caps at 10 (does not go to 12).
- [ ] Showrunner with Heat 8, no projects for 2 seasons. Design spec: heat decays 10% per season. After 2 seasons, Heat should be ~6.5. Verify decay calculation.
- [ ] Showrunner with Reliability 3 (low). Verify budget overrun risk is HIGH. Pilot goes 20% over budget. Verify this is expected behavior, not a bug.
- [ ] Showrunner with Loyalty 10, trust 90. Cable tries to poach. Verify Loyalty stat reduces poaching probability (high-Loyalty showrunners are more resistant).

**Content Validation**:
- [ ] Check all showrunner bios. Verify names are unique (no duplicate IDs).
- [ ] Verify all showrunners have valid stat ranges (1-10 for each stat, not 0 or 11).
- [ ] Check showrunner tonal preferences. Verify all 4 axes (darkLight, serialEpisodic, characterPlot, intimateEpic) are set to 1-10 range.
- [ ] Cross-check showrunner IDs referenced in scripts against ShowrunnerDB. No orphaned IDs.

**Regression Checklist**:
- [ ] After any trust logic change, re-run all trust accumulation tests
- [ ] After any career arc logic change (burnout, poaching, heat decay), verify outcomes match design probabilities
- [ ] After any showrunner fit calculation change, verify fit scores still produce correct Synergy/Tension/Mismatch ranges

---

### 2.9 SAVE/LOAD SYSTEM

**What This Is**: Player can save at any time. Autosave at end of each season. 3 manual save slots + 1 autosave slot. Saves are JSON files. Must handle versioning and corruption gracefully.

**Happy Path Tests**:
- [ ] Start new game. Immediately save to Slot 1. Load Slot 1. Verify game restores to Season 1, Turn 1.
- [ ] Play through Season 1. Save mid-season (desk has 5 scripts, pipeline has 3 pilots). Load save. Verify all 5 scripts restore with correct expiration timers, all 3 pilots restore with correct states.
- [ ] Complete Season 1. Autosave triggers. Load autosave. Verify game restores to start of Season 2.
- [ ] Play through 8 seasons. Save at Season 8. Load save. Verify all history (greenlit shows, killed shows, showrunner relationships, brand axes) restores correctly.
- [ ] Save to Slot 1. Save to Slot 2. Load Slot 1. Verify Slot 1 data loads (not Slot 2). Save slots are isolated.

**Sad Path Tests**:
- [ ] Manually corrupt a save file (delete a JSON field, e.g., remove "currentSeason"). Attempt to load. Verify graceful error: "Save file corrupted. Load last autosave?" Does not crash.
- [ ] Manually corrupt a save file (change "version" field from "1.0" to "999.0"). Attempt to load. Verify error: "Save file version not supported."
- [ ] Delete autosave file from disk. Launch game. Verify game detects missing autosave, does not crash, offers "Start New Game."
- [ ] Save game on PC. Copy save file to Mac. Load on Mac. Verify cross-platform compatibility (JSON is platform-agnostic, should work).
- [ ] Save during Writers' Strike (Season 6, development halted). Load save. Verify strike state restores, player cannot prioritize scripts until strike ends.

**Evil Path Tests**:
- [ ] Save game. Force-quit game during save write (simulate power loss). Restart game. Verify save file is either complete (atomic write succeeded) or absent (atomic write failed cleanly). Save file should NEVER be half-written (corrupted).
- [ ] Fill all 3 manual save slots. Save to Slot 1 (overwrite oldest save). Verify overwrite succeeds, no data corruption.
- [ ] Save game at Season 8, end of career retrospective. Load save. Verify retrospective replays (or player is returned to post-retrospective state — document behavior).
- [ ] Hex-edit a save file: change network budget from $10M to $999M. Load save. Verify game loads (no validation prevents this), but player now has infinite money. Document: save editing is possible, but unsupported.
- [ ] Hex-edit a save file: change presidentPatience from 50 to -10. Load save. Verify game either clamps to 0 and triggers game over, or detects invalid value and rejects save.

**Versioning Tests** (Critical for Post-Launch):
- [ ] Create a save file in version 1.0. Update game to version 1.1 (which adds a new field: "culturalFootprint"). Load 1.0 save in 1.1 game. Verify migration script runs, calculates culturalFootprint from history, updates save version to 1.1.
- [ ] Create a save file in version 1.1. Attempt to load in version 1.0 (downgrade). Verify error: "Save file version too new."
- [ ] Simulate 5 version updates (1.0 -> 1.1 -> 1.2 -> 1.3 -> 1.4 -> 1.5). Load a 1.0 save in 1.5. Verify migration chain runs (1.0->1.1->1.2->1.3->1.4->1.5), all fields migrate correctly.

**Performance Tests**:
- [ ] Save a Season 8 game (max data: 64 pilots developed, 20+ series in history, 8 seasons of events). Measure save write time. Should be <1 second.
- [ ] Load a Season 8 save. Measure load time. Should be <3 seconds (design target per tech doc).
- [ ] Save and load 100 times in a loop. Verify no memory leaks (memory usage should not grow unbounded).

**Edge Cases**:
- [ ] Save file size: Largest possible save (Season 8, max history). Check file size. Per tech doc estimate: ~500KB JSON. If >1MB, investigate (possible data bloat).
- [ ] Save file with 0 history (player at Season 1, Turn 1). Check file size. Should be <10KB (minimal data).
- [ ] Autosave triggers at end of Season 4. Player manually saves to Slot 1 at same moment. Verify no race condition (one write completes before the other starts).
- [ ] Save game on a read-only filesystem (simulate permission error). Verify error message: "Cannot write save file. Check permissions."

**Regression Checklist**:
- [ ] After any save schema change, verify old saves still load via migration scripts
- [ ] After any core game state change (new system added), verify save/load includes new state
- [ ] After any corruption handling change, verify corrupted saves still fail gracefully (no crashes)

---

## 3. EDGE CASE TESTING (The Evil Path, Refined)

These are the scenarios that break games. The player who saves and loads 50 times per hour. The player who tries to game the system. The player who finds the one interaction you did not test. This is where QA earns its keep.

### 3.1 The Degenerate Strategies

**Goal**: Find gameplay loops that trivialize the game or produce absurd outcomes.

- [ ] **The Reset Scum**: Player saves before every dilemma, tries all 3 options, reloads to pick the best outcome. Verify: Does the game allow this? (It should — single-player game, player agency.) Does it break immersion? Does it make the game trivial? Document. Consider: Should RNG seed be fixed per dilemma to prevent outcome shopping?
- [ ] **The Budget Exploit**: Player discovers that killing pilots mid-development refunds 50% of budget. Player develops 20 pilots, kills 18, keeps 2, accumulates massive budget surplus. Verify: Is this possible? Does it break economy? If yes, adjust refund percentage or cap refunds per season.
- [ ] **The Prestige Grind**: Player gives ONLY prestige notes for 8 seasons. Verify: Do they go bankrupt by Season 6? (Design intent: yes, high prestige should strain finances.) If player survives to Season 8 with high prestige and profit, economy is too forgiving.
- [ ] **The Populist Money Printer**: Player gives ONLY commercial notes. Verify: Do they print infinite money? Do they lose access to high-Vision showrunners? If player can run a profitable populist network for 8 seasons with zero creative ambition, is the game still interesting? (This is a design question, not a bug, but QA should flag it.)
- [ ] **The All-In Bet**: Player develops 1 pilot per season (minimum viable slate). Gives it perfect notes, maximum budget. Greenlights only that 1 show. Verify: Is this viable? Or does President fire player for insufficient slate size? Document.

### 3.2 The State Machine Breakers

**Goal**: Find race conditions, orphaned states, and impossible transitions.

- [ ] **Priority a script, then immediately Pass it before it enters pipeline.** Should not be possible (script is already committed), but test. Verify error handling.
- [ ] **Kill a pilot mid-development, then try to give it notes.** Pilot is dead, notes UI should not appear. Verify.
- [ ] **Greenlight a pilot at upfronts, then try to kill it before season starts.** Should not be possible (already committed). Verify.
- [ ] **Cancel a series mid-season, then try to view its ratings.** Series is cancelled, ratings should stop updating. Verify UI handles this gracefully (shows "CANCELLED" instead of rating numbers, or greys out series).
- [ ] **Save during a state transition (e.g., pilot moving from IN_DEVELOPMENT to PILOT_ORDERED).** Load save. Verify pilot is in one state or the other, not stuck between states.

### 3.3 The UI Stress Tests

**Goal**: Break the interface with extreme inputs.

- [ ] **Desk with 20 scripts.** Drag all 20 around. Spam Pass on all 20. Verify no layout explosion, no index errors.
- [ ] **Pipeline with 12 pilots.** All 12 have attention flags (all are in crisis simultaneously). Verify UI can display 12 flagged cards without overlap or clipping.
- [ ] **Upfronts with 1 pilot.** Verify presentation does not look broken or empty (UI is designed for 2-4 pilots).
- [ ] **Season with 4 series, all titled "Untitled Drama" (duplicate names).** Verify UI can distinguish them (by ID, not by name).
- [ ] **Showrunner name is 50 characters long.** Verify name does not overflow UI elements, is truncated gracefully.
- [ ] **Dilemma context text is 500 words long.** Verify text box is scrollable, does not break layout.
- [ ] **Flavor text after note choice is 1 sentence vs. 5 paragraphs.** Verify UI adapts to variable text length.

### 3.4 The Economic Exploits

**Goal**: Find ways to generate infinite money or break the budget system.

- [ ] **Player develops cheap pilots ($2M each), greenlights them, they all flop (3M viewers).** Verify player loses money (ad revenue < production cost). Verify deficit reduces next season's budget.
- [ ] **Player develops expensive pilots ($8M each), greenlights them, they all hit (15M viewers).** Verify player makes massive profit. Verify surplus increases next season's budget. Verify there is a cap (budget does not grow to $100M).
- [ ] **Player cancels all shows mid-season.** Verify remaining episode budgets are not refunded (production costs are sunk). Verify player's finances are devastated.
- [ ] **Player extends episode orders on 3 shows (+$2M each).** Verify cost is deducted immediately. Verify player cannot extend orders if budget is insufficient.
- [ ] **Syndication revenue from a long-running procedural.** Verify player receives syndication income. Verify syndication value scales with number of seasons (more seasons = more syndication money).
- [ ] **Player has $500K budget remaining at end of season.** Verify carryover calculation: 50% goes to next season, 50% goes to corporate. Next season budget should be base allocation + $250K.

### 3.5 The Content Contradictions

**Goal**: Find dilemmas, scripts, or events that contradict each other or produce nonsensical outcomes.

- [ ] **Dilemma 1 on Pilot A: "Add a humanizing scene" (Option B). Dilemma 2 on same pilot: "The protagonist is too sympathetic, make them darker."** These contradict. Verify both dilemmas do not appear on the same pilot. If they do, flag for content revision.
- [ ] **Script logline: "A high school teacher manufactures meth."** Genre tag: "Family Sitcom." These do not match. Verify content validation catches genre mismatches.
- [ ] **Showrunner bio says they are "known for dark procedurals."** Tonal preference: darkLight = 2 (prefers light content). Contradiction. Verify content validation flags mismatches between bio text and stats.
- [ ] **Historical event in Season 3: "Serialized mystery becomes #1 show."** Player's slate has 0 serialized shows. Event text references "the success of serialized dramas" as if player participated. Text should be context-aware or generic. Flag if text assumes player behavior.
- [ ] **Dilemma flavor text: "The showrunner agrees, reluctantly."** But player's choice was Option A (protect vision), which should make showrunner HAPPY. Flavor text contradicts choice outcome. Flag for rewrite.

---

## 4. RISK ASSESSMENT

What could make this unfun?

### 4.1 CRITICAL RISKS

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| **Notes System feels like a quiz (obvious "correct" answers)** | HIGH | CRITICAL | Extensive playtesting. If >60% of playtesters pick same option, rebalance dilemma. Every option must have situational value. |
| **Save corruption destroys 8-hour playthrough** | MEDIUM | CRITICAL | Robust save system with atomic writes, validation, corruption detection. Autosave every season. Test corruption scenarios exhaustively. |
| **Ratings calculation produces nonsensical results** | MEDIUM | HIGH | Unit test all ratings formulas. Run 1000 simulations, verify no outliers. Compare expected vs. actual for 20 test cases. |
| **Desk UI overwhelms player (15 scripts = information overload)** | HIGH | HIGH | Visual hierarchy. Skim-speed defaults. Playtest time-to-triage. If >5 minutes for 15 scripts, simplify. |
| **Upfronts feel anticlimactic (just a menu, not a moment)** | MEDIUM | HIGH | Animated presentation. Ad buyer reactions. Tension-building. Playtest upfronts in isolation. If playtesters say "that's it?", redesign. |
| **Economy is broken (player prints infinite money or goes bankrupt by Season 3)** | MEDIUM | HIGH | Balance testing. Run 20 playthroughs with varied strategies. Track budget curve. Flag exploits. Adjust revenue/cost formulas. |
| **Content volume is insufficient (dilemmas repeat, players notice)** | HIGH | MEDIUM | 200 dilemmas minimum. Modular design (dilemmas reusable across genres). Track dilemma repetition in playtests. If player sees same dilemma twice in one playthrough, content pool is too small. |
| **Late-game stagnation (Seasons 6-8 feel like autopilot)** | MEDIUM | MEDIUM | Season 6 disruption (Writers' Strike). Showrunner career arcs. Landscape fragmentation. Playtest late game separately. Measure engagement in Seasons 6-8 vs. Seasons 2-4. |

### 4.2 MEDIUM RISKS

| Risk | Mitigation |
|---|---|
| **Rival AI is too passive (rivals never threaten player)** | Playtest rival competitiveness. If player never loses a script to a rival, or rival hits never shift landscape, AI needs tuning. |
| **Showrunner relationships feel arbitrary (trust math is opaque)** | Surface trust changes clearly in UI. After every note, show "+10 trust" or "-5 trust" as feedback. Player should understand cause and effect. |
| **Network brand feels cosmetic (no mechanical weight)** | Verify brand effects are visible and impactful. High Prestige should attract better showrunners AND reduce ad revenue. Player should feel trade-offs. |
| **Test audience scores are misleading (high score = flop, low score = hit)** | Test audience is intentionally unreliable (design choice), but player must understand this. Tutorial or early-game event should teach "test scores are not destiny, especially for risky shows." |
| **Pipeline micro-management (player clicks through 10 pilots with no interesting decisions)** | Attention Flag system. Only surface projects with problems. Stable projects run on autopilot. Playtest: if player feels bored managing pipeline, flag system is not working. |

### 4.3 LOW RISKS (But Still Test)

- Performance issues (frame drops, slow loads) — Game is not GPU/CPU heavy, but test on min spec hardware (2019 MacBook Pro). Profile at month 6.
- Platform-specific bugs (Mac vs. Windows save path issues) — Test cross-platform saves. Verify Unity's `Application.persistentDataPath` works on both.
- Localization issues (if localizing) — Not in scope for base game, but if added post-launch, test string tables, text overflow, font support.
- Accessibility (colorblind mode, font size) — Not P0, but test readability at 1080p and 720p (for Switch). Verify desk UI is legible.

---

## 5. QUALITY GATES

What must pass before we ship?

### 5.1 ALPHA GATE (Month 12)

**Criteria**:
- [ ] 4 seasons playable start to finish without crashes
- [ ] Core loops (desk, pipeline, notes, upfronts, season) are complete and functional
- [ ] 40 pilots authored, 100 dilemmas authored
- [ ] Save/load works for all core systems
- [ ] No P0 bugs (crashes, soft locks, data corruption)
- [ ] Playtester feedback: "The notes feel like creative decisions, not a quiz"

**Blocker Bugs** (Cannot pass Alpha if any exist):
- Crash on startup
- Crash during save/load
- Soft lock (game becomes unresponsive, player cannot progress)
- Save corruption (data loss)
- Critical path broken (cannot complete 4 seasons)

### 5.2 BETA GATE (Month 18)

**Criteria**:
- [ ] 8 seasons playable start to finish
- [ ] All content authored (80 pilots, 200 dilemmas)
- [ ] All systems complete (landscape, brand, showrunner arcs, rivals)
- [ ] End-of-career retrospective implemented
- [ ] Audio implemented (UI sounds, ambient, score)
- [ ] Polish pass complete (UI animations, transitions)
- [ ] No P0 or P1 bugs
- [ ] Balance tested: no dominant strategy, no economic exploits
- [ ] Playtester feedback: "The game feels polished and complete"

**Blocker Bugs**:
- Any P0 bug (crash, soft lock, corruption)
- Ratings calculation produces nonsensical results
- Economy is broken (infinite money or guaranteed bankruptcy)
- Upfronts presentation feels anticlimactic
- Brand system feels cosmetic (no mechanical impact)
- Content contradictions (dilemmas contradict each other)

### 5.3 LAUNCH GATE (Month 24)

**Criteria**:
- [ ] All Beta Gate criteria met
- [ ] No P0, P1, or P2 bugs in main path
- [ ] Performance target met (60fps on 2019 MacBook Pro)
- [ ] Steam store page ready (screenshots, trailer, description)
- [ ] Press kit ready
- [ ] Day-one patch readiness (critical bug fix pipeline in place)
- [ ] Legal/compliance (ESRB rating if applicable, GDPR compliance if collecting data)
- [ ] Final playtester feedback: "I would recommend this game"

**Blocker Bugs**:
- Any crash or data corruption
- Any bug that prevents 8-season completion
- Performance below 30fps on target hardware (unplayable)
- Save system fails on any supported platform
- UI is unreadable at 1080p

**Known Shippable** (Acceptable at Launch):
- Minor text typos (can be patched)
- Rare edge-case bugs with <1% repro rate (document, patch post-launch)
- Balance issues (e.g., one dilemma is slightly overpowered) — can be tuned post-launch
- Switch port not ready (PC/Mac launch first, Switch follows)

---

## 6. REGRESSION TEST MATRIX

When you fix a bug, you might break something else. This matrix tracks which systems interact, so you know what to re-test after a change.

| Change Area | Must Re-Test |
|---|---|
| **Desk UI** | Script triage, expiration timers, save/load (desk state), time token consumption |
| **Pipeline logic** | Showrunner fit calculation, casting, budget allocation, attention flags, save/load (pilot state) |
| **Notes System** | Dilemma selection, delta application, brand axis shifts, showrunner trust, save/load (pilot deltas) |
| **Upfronts** | Ad confidence calculation, revenue calculation, pilot greenlight/kill, save/load (upfronts state) |
| **Ratings formula** | Season broadcast, weekly viewership, mid-season decisions, trend alignment, save/load (series state) |
| **Network brand** | Brand effects (showrunner attraction, ad revenue, quality ceilings), persona labels, save/load (brand state) |
| **Landscape** | Trend shifts, historical events, rival AI, industry signals, save/load (landscape state) |
| **Showrunner system** | Trust accumulation, career arcs (burnout, poaching, heat decay), return probability, save/load (showrunner state) |
| **Economy** | Budget calculations, revenue calculations, deficit/surplus, president patience, save/load (financial state) |
| **Save system** | All systems (save touches everything), corruption handling, versioning, cross-platform |

**Example**: If we change the ratings formula, we must re-test:
- Season broadcast (does viewership display correctly?)
- Mid-season decisions (do triggers still fire at correct thresholds?)
- Trend alignment (does bonus still apply?)
- Economy (does ad revenue calculation still work?)
- Save/load (do series ratings restore correctly?)

---

## 7. PLAYTESTING PROTOCOL

QA is not the same as playtesting. QA finds bugs. Playtesting finds design problems. Both are necessary.

### 7.1 Internal Playtesting (Dev Team)

**When**: Weekly, starting Week 1.

**Focus**: Does the core loop feel good? Are we building the right thing?

**Protocol**:
1. Play the latest build for 30-60 minutes
2. Log bugs in tracker (Jira, Linear, Notion, whatever)
3. Log design feedback separately ("Notes feel like a quiz" is not a bug, it is a design issue)
4. Weekly meeting: review blockers, prioritize fixes

### 7.2 External Playtesting (Small Group, Month 3)

**When**: After core loop prototype is complete.

**Who**: 5-10 players (friends, indie dev community, not random public).

**Focus**: Is the 5-minute loop satisfying?

**Protocol**:
1. Give playtesters a build with 1 development season (desk -> pipeline -> upfronts)
2. Ask: "Did the notes feel like creative decisions or like a quiz?"
3. Ask: "Did the desk feel overwhelming or manageable?"
4. Ask: "Did the upfronts feel climactic?"
5. Log feedback. Iterate.

### 7.3 Vertical Slice Playtesting (Medium Group, Month 6)

**When**: After 1 full season is playable.

**Who**: 20-30 players (broader indie community, genre fans).

**Focus**: Does one full season hold attention for 60+ minutes?

**Protocol**:
1. Give playtesters a build with 1 full season
2. Ask: "Did you complete the season? If not, where did you stop and why?"
3. Ask: "Did your network brand feel like it reflected your decisions?"
4. Ask: "Did you see your choices matter?"
5. Track completion rate. If <50% complete the season, pacing is broken.

### 7.4 Alpha Playtesting (Large Group, Month 12)

**When**: After 4 seasons are playable, 50% content authored.

**Who**: 100+ players (Steam closed beta, wishlist invites).

**Focus**: Content variety, balance, pacing over multiple seasons.

**Protocol**:
1. Give playtesters a build with 4 seasons
2. Ask: "Did dilemmas feel repetitive?"
3. Ask: "Did you discover a dominant strategy?"
4. Ask: "Did the landscape shifts feel meaningful?"
5. Track playtime. Median should be 3-4 hours (4 seasons × 45-90 min). If median is <2 hours, players are disengaging early.

### 7.5 Beta Playtesting (Public, Month 18)

**When**: After 8 seasons are playable, 100% content authored.

**Who**: Open to all Steam wishlisters.

**Focus**: Polish, bugs, final balance.

**Protocol**:
1. Give playtesters full build
2. Collect crash logs, bug reports via automated reporting tool
3. Ask: "Would you recommend this game?"
4. Track completion rate for 8 seasons. Target: >30% complete all 8 seasons (6-12 hour game, expect dropoff).
5. Monitor Steam forums, Discord for emergent issues.

---

## 8. BUG TRIAGE & PRIORITIZATION

Not all bugs are created equal. This is how we decide what to fix and when.

### 8.1 Bug Severity Levels

**P0 (CRITICAL — Fix Immediately)**:
- Crash on startup
- Crash during normal gameplay
- Soft lock (game becomes unresponsive)
- Save corruption (data loss)
- Critical path broken (cannot progress)
- Game-breaking exploit (infinite money, guaranteed win)

**P1 (HIGH — Fix Before Next Milestone)**:
- Feature does not work as designed (e.g., notes do not apply deltas)
- Major UI issue (unreadable text, broken layout)
- Significant balance issue (one strategy dominates all others)
- Ratings calculation produces nonsensical results
- Economy is broken (bankruptcy guaranteed or impossible)

**P2 (MEDIUM — Fix Before Launch)**:
- Minor feature issue (works mostly, but edge case fails)
- Minor UI issue (visual glitch, but information is still visible)
- Content contradiction (two dilemmas contradict)
- Rare crash (<5% repro rate)
- Performance issue (frame drops in specific scenario)

**P3 (LOW — Patch Post-Launch)**:
- Cosmetic issue (typo, misaligned UI element)
- Very rare edge case (<1% repro rate)
- Minor balance issue (one dilemma is slightly weak/strong)
- Quality-of-life missing feature (no keyboard shortcut for X)

**P4 (NICE TO HAVE — Maybe Never Fix)**:
- Feature request (not a bug)
- Known limitation (engine constraint, not fixable)
- Extremely rare edge case (requires 10-step repro, affects <0.1% of players)

### 8.2 Bug Triage Process

1. **Reporter logs bug** (QA, playtester, dev) with:
   - Repro steps (exact steps to reproduce)
   - Expected result
   - Actual result
   - Severity (P0-P4)
   - Platform (PC, Mac, Switch)
   - Screenshot/video if applicable

2. **QA Lead reviews** (that's me, CRASH):
   - Verify repro (can I reproduce the bug?)
   - Adjust severity if needed (reporter said P1, but it is actually P3)
   - Assign to dev

3. **Dev fixes**:
   - Fix the bug
   - Write a unit test (if applicable) so regression does not happen
   - Mark bug as "Fixed, needs verification"

4. **QA verifies**:
   - Re-test the bug (is it actually fixed?)
   - Run regression tests (did the fix break something else?)
   - If fixed: close bug
   - If not fixed or regression occurred: reopen, send back to dev

---

## 9. TESTING TOOLS & AUTOMATION

Manual testing is necessary, but automation saves time. Here's what we build.

### 9.1 Unit Tests (Code-Level)

**What**: Automated tests for all simulation logic (ratings calculation, budget math, trend shifts, showrunner fit, brand effects).

**Tool**: Unity Test Framework (NUnit).

**Coverage Target**: 80% code coverage for all simulation systems. UI code is not unit tested (too much Unity-specific state).

**Example Tests**:
```csharp
[Test]
public void TestRatingsCalculation() {
    var series = new SeriesData { commercialFloor = 5, qualityCeiling = 70, ... };
    float viewership = RatingsSystem.CalculateEpisodeViewership(series, 1);
    Assert.IsTrue(viewership > 5 && viewership < 20); // Sanity check range
}

[Test]
public void TestBrandAxisClamping() {
    NetworkBrand brand = new NetworkBrand { prestige = 95 };
    brand.AdjustAxis(BrandAxis.Prestige, +10);
    Assert.AreEqual(100, brand.prestige); // Should clamp at 100, not overflow
}
```

**CI Integration**: Unit tests run on every commit. Build fails if tests fail. No exceptions.

### 9.2 Content Validation Scripts

**What**: Automated checks for authored content integrity (dilemmas, scripts, showrunners).

**Tool**: Python script, runs pre-build.

**Checks**:
- All dilemma IDs referenced in scripts exist in DilemmaDB
- All showrunner IDs referenced in scripts exist in ShowrunnerDB
- All stat ranges are valid (qualityCeiling 0-100, showrunner stats 1-10)
- No duplicate IDs
- No orphaned content (dilemmas never referenced by any script)
- No typos in critical fields (genre tags, state enums)

**CI Integration**: Content validation runs on every build. Build fails if validation fails.

### 9.3 Automated Playthroughs (Smoke Tests)

**What**: Scripted playthroughs that simulate a full game (8 seasons, random decisions).

**Tool**: Unity Playmode tests with simulated input.

**Purpose**: Catch crashes and soft locks that only appear after hours of gameplay.

**Protocol**:
1. Start new game
2. For each season:
   - Triage 15 scripts (random Pass/Consider/Priority)
   - Develop 8 pilots (random showrunner/cast choices)
   - Give notes (random option selection)
   - Greenlight 3 pilots at upfronts
   - Simulate season broadcast
3. Complete 8 seasons
4. If crash or soft lock occurs, test fails, log repro steps

**Run Frequency**: Nightly builds. Catches regressions overnight.

### 9.4 Dilemma Balance Analyzer

**What**: Tool that parses all 200 dilemmas, tracks delta distributions, flags outliers.

**Purpose**: Find dilemmas with broken balance (e.g., one option gives +50 quality, others give +5).

**Output**:
- List of dilemmas where one option is significantly stronger than others
- List of dilemmas with no trade-offs (all deltas are positive)
- List of dilemmas with extreme deltas (>15 quality, >20 commercial, >30 trust)

**Run Frequency**: Weekly during content authoring phase.

---

## 10. POST-LAUNCH QA PLAN

Shipping is not the end. Bugs will emerge when 10,000 players hit the game simultaneously.

### 10.1 Day-One Priorities

**Focus**: Crash bugs, save corruption, progression blockers.

**Protocol**:
1. Monitor crash logs (automated crash reporter uploads logs to server)
2. Monitor Steam forums, Discord, Reddit for "Cannot progress past Season X" posts
3. Monitor save corruption reports
4. Hotfix pipeline: P0 bugs are fixed within 24 hours, patch deployed within 48 hours

**Team**: QA Lead (me) + 1 programmer on-call for emergency fixes.

### 10.2 Week-One Patch (Patch 1.1)

**Focus**: Critical bugs that were not caught in beta.

**Candidates**:
- Crashes with >1% occurrence rate
- Save corruption (any occurrence rate — zero tolerance)
- Progression blockers (any occurrence rate)
- Game-breaking exploits (if community finds one)

**Timeline**: Deployed by Day 7.

### 10.3 Month-One Patch (Patch 1.2)

**Focus**: Balance adjustments, quality-of-life improvements.

**Candidates**:
- Dilemmas where one option is chosen >80% of the time (rebalance)
- Economy exploits (if any emerge)
- UI issues (text overflow, layout bugs on specific resolutions)
- Minor crashes (<1% rate but still annoying)

**Timeline**: Deployed by Day 30.

### 10.4 Ongoing Support (Months 2-6)

**Focus**: Long-tail bugs, mod support, feature requests.

**Protocol**:
- Monthly patch cycle
- Monitor community feedback (Steam reviews, forums, Discord)
- Prioritize based on impact (how many players affected?) and severity

---

## 11. TESTING SCHEDULE (INTEGRATED WITH DEV MILESTONES)

| Milestone | Month | QA Focus | Deliverables |
|---|---|---|---|
| **Core Loop Prototype** | 1-3 | Desk UI, triage actions, 5 dilemmas, notes delta application | Bug tracker setup, repro docs for desk bugs |
| **Vertical Slice** | 4-6 | Full season loop, upfronts, ratings, brand tracking, save/load | External playtest (20-30 testers), feedback report |
| **Alpha** | 7-12 | 4 seasons, content variety, balance, rival AI, showrunner arcs | Alpha playtest (100+ testers), balance report, regression matrix |
| **Beta** | 13-18 | 8 seasons, full content, polish, performance, final balance | Beta playtest (open to wishlisters), launch readiness checklist |
| **Launch Prep** | 19-24 | Final bug sweep, performance profiling, platform testing, day-one patch prep | Launch gate verification, hotfix pipeline tested |
| **Post-Launch** | 24+ | Crash monitoring, community feedback, patch planning | Patch 1.1 (Week 1), Patch 1.2 (Month 1), ongoing support |

---

## 12. FINAL WORD

This is not a game you test once and call it done. This is a game with 200 authored dilemmas, 80 pilot concepts, 8 seasons of compounding decisions, 6 interlocking systems, and emergent narratives that arise from the interaction of all of the above. The bugs will be subtle. The balance issues will be invisible until hour 6. The edge cases will require 10-step repros.

My job is to find them before the player does. Every bug I miss is a player who refunds, a player who writes a 1-star review, a player who tells their friends "Don't buy this, it's broken."

I have seen save-corruption bugs destroy launch weeks. I have seen balance exploits trivialize entire games. I have seen UI disasters make brilliant designs unplayable. I learned the hard way that you cannot patch your way out of a broken launch. You ship it right, or you ship it never.

This QA plan is not optional. This is the difference between "Overwhelmingly Positive" and "Mixed" on Steam. This is the difference between a game that finds its audience and a game that dies in obscurity because nobody could finish it.

Test the happy path. Test the sad path. Test the evil path. Test the path nobody thought to test. Break everything. Fix everything. Break it again. Document every edge case. Build the regression matrix. Run the automated tests. Run the manual tests. Playtest with 5 people, then 50, then 500. Watch them play. Watch where they get stuck. Watch where they quit.

And when you think you are done, test it one more time. Because the bug you did not find is the bug that ships.

Define "works." Then prove it.

-- CRASH

