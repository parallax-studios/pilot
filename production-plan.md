# PILOT -- Production Plan

**Written by CLOCK, Producer**
**Version**: 1.0
**Date**: 2026-02-07
**Status**: Pre-Production Blueprint

---

> "Cut scope, not corners. A shipped game beats a perfect concept."

I have read the pitch, the design document, and the narrative bible. I know what this game wants to be. Now let me tell you what it will take to make it real.

This is the production plan for PILOT — a television development sim where taste is the mechanic and every greenlight is a gamble. The plan spans pre-production through gold master, with clear milestones, task breakdowns, risk mitigation, and the hard conversations about scope that nobody wants to have but everyone needs to hear.

Let me be direct: this game has three critical path items that make or break everything — the Notes System, the Desk interface, and the authored content library. If any of those fail, the game fails. Everything else serves those three pillars. That is our north star. That is where the budget and the schedule bend.

---

## PROJECT OVERVIEW

### Scope Statement

**What We Are Building**: A single-player management simulation where the player is a television network executive developing pilots and building a slate across eight seasons (2002-2010). The core experience is creative decision-making through a notes system, portfolio management through a development pipeline, and emergent narrative through network identity.

**What We Are NOT Building**:
- Multiplayer or competitive modes
- Real licensed television properties
- Procedurally generated scripts (all content is authored)
- Playable production sequences (no set management, no directing minigames)
- Voice acting
- Post-2010 eras at launch (streaming wars are expansion territory)
- Console versions at launch (PC/Mac only, Switch is post-launch)

**Target Platform**: PC (Steam primary) and Mac (day-one parity)

**Target Playtime**: 15-25 hours for a single 8-season campaign. High replay value through branching development choices and emergent network identities.

**Genre**: Management Sim, Narrative, Strategy

**Comparable Scope**: Pentiment (15-20 hour authored narrative experience), Game Dev Tycoon (management loop with authored content), Hardspace Shipbreaker (work sim that becomes meditative).

---

### Team Structure

This is the minimum viable team to ship PILOT at the quality bar the design demands:

| Role | Headcount | Primary Responsibility |
|---|---|---|
| **Game Designer** | 1 (REED) | Systems design, balance, playtesting, iteration |
| **Narrative Designer** | 1 (NOVA) | Authored content (scripts, dilemmas, characters), dialogue, world-building |
| **Producer** | 1 (CLOCK) | Schedule, scope, budget, milestone management, risk mitigation |
| **Lead Programmer** | 1 (BYTE) | Core systems, pipeline architecture, UI engineering |
| **UI/UX Designer** | 1 | Interface design, information hierarchy, usability |
| **Visual Artist** | 1 (PIXEL) | Key art, UI art, iconography, environmental art (desk, office) |
| **Writer/Content Author** | 1-2 (can be NOVA + freelancer) | Script loglines, pilot excerpts, creative dilemma authoring (200+ dilemmas) |
| **QA Lead** | 1 (CRASH) | Test plan, bug tracking, balance validation, edge-case hunting |
| **Composer/Sound Designer** | 0.5 (ECHO, part-time/contract) | Ambient score, UI audio, environmental sound |

**Total Core Team**: 8.5-9.5 FTE

**Development Duration**: 18 months from prototyping kickoff to gold master.

**Budget Range Estimate**: $800K-$1.2M (assuming mid-level salaries, contractor rates, tooling, and Steam/platform fees).

---

### Success Criteria

What does success look like? Define it now or argue about it forever.

**Critical Success Factors**:
1. **The Notes System Lands**: Playtesters must report that creative dilemmas feel like genuine choices, not optimization puzzles. Target: no single note option chosen more than 60% of the time across playtests.
2. **The Desk Feels Good**: Script triage at the desk must be fast, tactile, and satisfying within the first 15 minutes of gameplay. Target: players intuitively understand the triage loop without tutorial handholding.
3. **Attachment to Shows**: Players must care about the pilots they develop. Target: playtest exit surveys show 70%+ of players can name at least two shows they greenlit and explain why they mattered.
4. **Session Length Sweet Spot**: A single development season (45-90 minutes) must feel complete and satisfying. Target: 80%+ of playtesters finish a full season in one sitting.
5. **"One More Season" Compulsion**: The game must create the management sim compulsion loop. Target: 60%+ of playtesters voluntarily continue to a second season without prompting.

**Commercial Success Targets**:
- **Wishlist Goal (Pre-Launch)**: 25K-40K Steam wishlists (mid-sized narrative/management sim benchmark)
- **Launch Week Sales**: 5K-10K units at $24.99 price point
- **Year One Target**: 40K-60K units across PC/Mac (assumes strong word-of-mouth, press coverage from TV industry, and management sim audience crossover)
- **Critical Reception**: 75+ Metacritic / "Very Positive" Steam rating (quality bar for prestige indie management sims)

---

## MILESTONE STRUCTURE

The production timeline is divided into six major milestones, each with clear entry criteria, deliverables, and exit criteria.

---

### Milestone 1: PROTOTYPE (Months 1-3)

**Goal**: Prove the core loop works. Build the 30-second and 5-minute loops in playable form. Validate or invalidate the Notes System as the emotional center of the game.

**Entry Criteria**:
- Full design document approved (REED's GDD is the baseline)
- Narrative bible approved (NOVA's character/world work is the baseline)
- Production plan approved (this document)
- Team assembled and onboarded
- Development environment and repository established

**Key Deliverables**:

1. **The Desk (Prototype)** -- A functional interface where 10 scripts appear with coverage sheets. Player can skim, standard read, or deep read. Player can PASS, CONSIDER, or PRIORITY. Expiration clocks tick. Visual hierarchy must communicate essential information in 5 seconds. Target: triage 10 scripts in under 5 minutes.

2. **The Development Pipeline (Greybox)** -- A whiteboard-style interface tracking 4 pilot projects through showrunner attachment, casting, and budget allocation. No notes system yet. Just the flow. Target: player can assemble a pilot's team in under 2 minutes.

3. **The Notes System (Prototype)** -- 10 authored creative dilemmas across 3 pilot concepts. Each dilemma has 2-3 options with visible consequences (Quality Ceiling, Commercial Floor, Showrunner Trust, Network Brand shift). Present dilemmas to the player. Track their choices. Display outcomes. Target: player spends 90-120 seconds per dilemma and feels torn about the choice.

4. **Network Identity Tracker (Greybox)** -- A four-axis radar chart (Prestige/Populist, Risk/Safe, Auteur/Producer, Serialized/Episodic) that updates based on player notes. Display shifts visually. Target: player can glance at the chart and understand their network's identity.

5. **Rough Cut Viewer (Stub)** -- A placeholder interface where the player "watches" a rough cut (text description + stat summary + test audience data). No video or animation. Just the information layer. Target: player receives enough context to make a greenlight/kill decision.

**Playtesting Focus**:
- Does the desk triage feel overwhelming or satisfying?
- Does the Notes System feel like creative engagement or spreadsheet optimization?
- Can players articulate why they made a specific note choice?
- Does the 5-minute loop (develop one pilot) feel complete?

**Exit Criteria**:
- Playtesters successfully triage 10 scripts without confusion
- Playtesters report at least 2 of the 10 note dilemmas felt like "hard choices"
- No single note option is chosen more than 70% of the time (balance check)
- Producer sign-off that the core loop is worth building on
- Design sign-off that the systems interact as intended

**Critical Path Dependencies**: The Notes System is the highest-risk item. If it does not land by the end of Month 3, we pause and iterate. Do not proceed to Vertical Slice until the Notes System works.

**Duration**: 3 months

---

### Milestone 2: VERTICAL SLICE (Months 4-6)

**Goal**: Build one complete development season (fall through upfronts) with full feature parity. This is the demo. This is the proof that the game works end-to-end.

**Entry Criteria**:
- Prototype milestone exit criteria met
- Playtesting validates core loop satisfaction
- Art direction locked (PIXEL's style guide approved)
- Audio direction locked (ECHO's sonic palette approved)
- Content authoring process established (NOVA's pipeline for dilemmas, scripts, showrunners)

**Key Deliverables**:

1. **One Full Season (Season 1, 2002-03)** -- The player experiences:
   - Script triage (15 scripts arrive over 4 in-game weeks)
   - Development pipeline (select 8 scripts, develop 6, pilot 4)
   - Showrunner attachment (6 characterized showrunners with stats and fit scores)
   - Casting (12 actors across 4 pilots, each with star power/talent/salary)
   - Notes System (20 authored dilemmas across 4 pilots, 2 note sessions per pilot)
   - Budget allocation (pilot production budget split across 5 categories)
   - Rough cut screening (4 rough cuts with test audience data)
   - Upfronts presentation (select 2-3 pilots to greenlight, arrange slate, present to advertisers)
   - Series launch (2 series air, weekly ratings arrive over 8 weeks)
   - Season-end evaluation (Network President feedback, budget update, reputation shift)

2. **Full UI Suite (Visual Design)** -- Desk interface, whiteboard pipeline, notes interface, rough cut viewer, upfronts presentation, season calendar. Physical, tactile aesthetic. Script pages as documents. Coverage sheets as colored paper. Whiteboard as physical index cards. 2000s office texture (wood grain, teal carpet, institutional lighting).

3. **Network Identity System (Full)** -- Four-axis radar chart updates with every note. Brand profile label ("Prestige Boutique," "Safe Harbor," "Auteur's Haven") appears below chart. Trade magazine headline appears when axes cross thresholds (30 or 70).

4. **Authored Content Library (Batch 1)** -- 15 pilot concepts (loglines, genre tags, script excerpts), 20 creative dilemmas, 6 showrunner profiles, 12 actor profiles, 5 trade magazine headline templates, 3 rough cut description templates.

5. **Network President Character (Prototype)** -- Richard Kessler appears in 3 key scenes: opening briefing (sets expectations), mid-season check-in (reacts to development choices), post-upfronts evaluation (adjusts Patience stat, sets next season's budget). Text-based dialogue, character portrait.

6. **Audio/Music Integration** -- Ambient office soundscape (HVAC hum, distant phones, keyboard clicks). Subtle piano score for upfronts presentation. UI audio (paper shuffle, pen scratch, phone ring).

**Playtesting Focus**:
- Does a full season (45-90 minutes) feel complete and satisfying?
- Do players want to continue to Season 2 immediately?
- Are players emotionally attached to at least one pilot they developed?
- Does the upfronts presentation feel climactic or anticlimactic?
- Is information density at the desk/pipeline overwhelming or manageable?

**Exit Criteria**:
- 80%+ of playtesters complete the full season in one sitting
- 60%+ of playtesters express desire to play Season 2
- No critical bugs (game-breaking, progression-blocking, data corruption)
- Performance targets met (60fps at 1080p on target spec)
- Producer and Design sign-off that the vertical slice is demo-ready

**Steam Page**: The vertical slice is the moment the Steam page goes live. Key art, GIF of the desk interface, GIF of a note dilemma, description emphasizing "your taste is the mechanic," wishlist campaign begins.

**Duration**: 3 months

---

### Milestone 3: ALPHA (Months 7-10)

**Goal**: All systems implemented. All 8 seasons playable start to finish. Content complete at "first draft" level (subject to revision). Feature-complete but not polish-complete.

**Entry Criteria**:
- Vertical Slice milestone exit criteria met
- Vertical Slice playtest data reviewed and design adjustments made
- Content authoring pipeline validated (NOVA can produce dilemmas at required velocity)
- Steam wishlist tracking established (target: 1K wishlists by Alpha start)

**Key Deliverables**:

1. **8 Full Seasons Playable** -- Each season introduces complexity as specified in REED's progression design:
   - Season 1: Tutorial season, forgiving President Patience
   - Season 2: Network Brand becomes visible, Showrunner Trust introduced, rivals activate
   - Season 3: Serialization Appetite spikes, genre gold rush, mid-season replacements
   - Season 4: DVR disruption, budget squeeze, showrunner poaching
   - Season 5: Full complexity, network brand has strategic weight
   - Season 6: Writers' Strike event (development halts for one cycle)
   - Season 7: Audience fragmentation, no single dominant strategy
   - Season 8: Legacy season, retrospective narrator, career evaluation

2. **Landscape System (Full)** -- Audience Trend Vectors (6 trends tracked on 0-100 scales), Industry Signals (2-3 per season, authored events that hint at trend shifts), Historical Inflection Points (7 major events tied to specific seasons), Rival Networks (3 AI opponents with visible strategies and slates).

3. **Showrunner Career Arcs** -- 12 characterized showrunners, each with stat progression over 8 seasons. Showrunners can rise (Heat increases), decline (Vision/Reliability drops), burn out (leave for cable), or become franchise assets (high Loyalty, return for multiple projects).

4. **Authored Content Library (Complete First Draft)** -- 80 pilot concepts, 200 unique creative dilemmas (each dilemma usable across 2-3 genre contexts for variety), 12 showrunner profiles, 30 actor profiles, 40 trade magazine headlines, 20 rough cut description templates, 15 Industry Signal events, 7 Historical Inflection Point scripts.

5. **Economy System (Full)** -- Revenue sources (upfronts ad commits, in-season ad revenue, syndication, critical acclaim bonus), expense tracking (script options, showrunner deals, casting costs, pilot production, series production, overhead), budget calculation and carryover, Cash Crisis triggers.

6. **Network President Dynamic Pressure** -- Richard Kessler's Patience stat (0-100) adjusts based on season performance. Patience thresholds impose constraints: low Patience reduces budget, mandates genre quotas, blocks risky greenlights. High Patience grants creative freedom and budget expansion.

7. **Rival Executive (Diane Valdez)** -- Visible throughout the game. Her network's slate appears in trade headlines. Her development choices create competitive pressure. 2-3 scripted intersections where the player and Diane compete for the same showrunner or time slot.

8. **Upfronts Presentation (Full)** -- Slate assembly, pilot ordering, Sell Line selection per show ("The next great American drama" vs. "18-49 demo magnet" vs. "The conversation starter"), Ad Buyer Confidence meter, real-time advertiser reactions, ad commit calculation, post-upfronts budget update.

**Playtesting Focus**:
- Can players complete an 8-season campaign (15-20 hours)?
- Does difficulty escalate appropriately? Is Season 1 forgiving and Season 6 pressurized?
- Do the Historical Inflection Points (cable prestige threat, DVR disruption, Writers' Strike) feel like dramatic moments or just stat changes?
- Does the authored content library feel repetitive by Season 6-8?
- Is the economy balanced? Can a player who swings too boldly or too safely still survive to Season 8, or does the game punish single strategies too harshly?

**Exit Criteria**:
- All 8 seasons completable without progression blockers
- All core systems (desk, pipeline, notes, landscape, brand, upfronts, economy, President) functionally complete
- Content library first draft complete (subject to revision in Beta)
- Performance stable (no crashes, no major memory leaks)
- Producer and Design sign-off that Alpha represents feature lock

**Feature Lock**: Alpha is feature lock. No new systems after this milestone. Beta is for polish, balance, bug fixing, and content revision only.

**Duration**: 4 months

---

### Milestone 4: BETA (Months 11-14)

**Goal**: Polish, balance, bug fixing, and content revision. The game is playable and complete; now make it good. Address all feedback from Alpha playtests. Prepare for external beta testing.

**Entry Criteria**:
- Alpha milestone exit criteria met
- Alpha playtest data compiled and prioritized
- Feature lock in effect (no new systems)
- QA test plan established (CRASH's coverage matrix)

**Key Deliverables**:

1. **Balance Pass** -- Notes System dilemma rebalancing (ensure no option is dominant across contexts), Showrunner stat tuning (ensure no single showrunner profile is always optimal), Economy balance (ensure Prestige-heavy and Populist-heavy strategies are both viable), Landscape Trend tuning (ensure trends telegraph clearly but remain uncertain), Difficulty curve smoothing (ensure Season 3-4 spike is challenging but not punishing).

2. **Content Revision Pass** -- Review all 200 dilemmas for clarity, drama, and mechanical balance. Revise 20-30% based on playtesting ("this dilemma was confusing," "this option was obviously bad," "this framing was too abstract"). Add variety to rough cut descriptions and trade headlines. Ensure no repeated phrases or templated language breaks immersion.

3. **UI Polish** -- Visual refinement of all interfaces (anti-aliasing, contrast adjustments, readability at 1080p and 1440p), Animation polish (scripts sliding onto desk, coverage sheets flipping, whiteboard cards moving smoothly), Transition polish (screen fades, scene changes, upfronts presentation pacing), Iconography consistency (ensure all genre tags, blind-spot indicators, and attention flags are visually distinct).

4. **Audio/Music Expansion** -- Full ambient office soundscape (20+ environmental sounds, randomized timing), Upfronts presentation music (building tension, celebratory or somber resolution), Screening room silence (emphasize the weight of watching a rough cut), Phone ring variations (different tones for Joel, Richard, Diane), BlackBerry vibration buzz (period-accurate).

5. **Narrative Passes** -- Character dialogue revision (ensure Richard, Diane, Tommy, Sandra, Joel, Martin all have distinct voices), Showrunner personality depth (add recurring dialogue lines, verbal tics, character consistency), Trade magazine headline variety (ensure headlines reflect specific player choices, not templated responses), Retrospective narrator script (Season 8 ending sequence, 3-5 minutes of career summary).

6. **Bug Fixing (Systematic)** -- QA generates bug database. Team prioritizes P0 (crashes, blockers), P1 (major functionality broken), P2 (minor bugs, edge cases), P3 (polish, nice-to-have). Target: zero P0/P1 bugs by Beta exit, P2 bugs reduced by 80%.

7. **External Beta Test** -- Recruit 30-50 external playtesters (mix of management sim fans, TV industry professionals, narrative game players). Distribute Beta build via Steam Playtest or itch.io. Collect telemetry (session length, completion rate, note choices, network identity distribution). Exit surveys (satisfaction, confusion points, favorite/least favorite systems).

**Playtesting Focus**:
- Are there any remaining "obvious optimal strategies" that collapse strategic depth?
- Do late-game seasons (6-8) maintain engagement or feel like a grind?
- Are there any dilemmas where playtesters consistently report "I didn't understand what this choice meant"?
- Does the Season 8 retrospective feel emotionally satisfying or anticlimactic?
- What is the crash/bug rate in external beta? (Target: less than 5% of sessions encounter a crash)

**Exit Criteria**:
- Zero P0 bugs, fewer than 10 P1 bugs
- External beta playtest completion rate above 60% (60% of testers finish at least 4 seasons)
- External beta satisfaction rating above 7/10
- Performance optimized (consistent 60fps, load times under 5 seconds for scene transitions)
- All content revised based on playtesting clarity feedback
- Producer and QA sign-off that the game is ready for Release Candidate

**Duration**: 4 months

---

### Milestone 5: RELEASE CANDIDATE (Months 15-16)

**Goal**: Final bug fixing, certification prep, launch readiness. The game is done. Now make sure it ships cleanly.

**Entry Criteria**:
- Beta milestone exit criteria met
- External beta feedback integrated
- Steam store page finalized (description, screenshots, trailer)
- Marketing plan locked (HYPE's launch strategy)

**Key Deliverables**:

1. **Final Bug Sweep** -- Address all remaining P1 bugs, prioritize P2 bugs by player impact, accept remaining P3 bugs as "known shippable" issues. Target: zero crashes in 100 consecutive hours of playtesting.

2. **Performance Optimization** -- Profile CPU/GPU usage, optimize hotspots, reduce memory footprint, ensure smooth performance on minimum spec (Intel i5-8400, GTX 1050, 8GB RAM). Target: 60fps stable at 1080p on min spec.

3. **Localization Prep (Text Only)** -- Extract all UI text, dialogue, and content into localization files. Prepare for post-launch translation (Spanish, French, German as first languages). No day-one translation, but files must be structured for ease of localization later.

4. **Steam Build Pipeline** -- Configure Steam depots for PC/Mac, test Steam achievements (20-25 achievements tied to creative milestones, network identity profiles, and campaign completion), test Steam Cloud saves, test Steam Workshop integration (none at launch, but consider post-launch modding support for custom pilot scripts).

5. **Trailer and Marketing Assets** -- Launch trailer (90 seconds: desk montage, note dilemma closeup, upfronts presentation, trade headlines reacting to player choices, end card: "What gets made is up to you"), Screenshot suite (desk interface, notes dilemma, upfronts presentation, network identity chart, rough cut viewer), GIF suite for social media (script sliding onto desk, coverage sheet flip, note dilemma hover states).

6. **Press Outreach** -- Target press: PC Gamer, Rock Paper Shotgun, Eurogamer (management sim coverage), Polygon, Kotaku (narrative game coverage), Variety, The Hollywood Reporter (TV industry angle, potential viral press hook). Press kit: trailer, screenshots, Steam key, fact sheet, developer quote from REED/NOVA/CLOCK about creative vision.

7. **Day-One Patch Prep** -- Identify any bugs discovered during RC that miss the certification cutoff. Prepare day-one patch for Steam (fast turnaround, no certification delay). Mac build parity check.

**Exit Criteria**:
- Zero P0 bugs, fewer than 5 P1 bugs
- 100 consecutive hours of crash-free playtesting
- Steam build uploaded and tested on minimum spec hardware
- Marketing assets finalized and approved
- Press embargo dates set (review codes sent 1 week before launch)
- Producer, QA, and Design sign-off that the game is shippable

**Go/No-Go Decision Point**: One week before planned launch, team conducts Go/No-Go review. If any P0 bug exists or if external factors (major competing release, catastrophic press preview) suggest delay is wise, delay by 2-4 weeks. Do not ship broken. Do not ship into a hurricane.

**Duration**: 2 months

---

### Milestone 6: GOLD MASTER & LAUNCH (Month 17-18)

**Goal**: Ship the game. Support launch week. Monitor player feedback and prepare for post-launch support.

**Entry Criteria**:
- Release Candidate milestone exit criteria met
- Go/No-Go decision is GO
- Steam store page live and wishlist count tracked (target: 25K+ wishlists at launch)

**Key Deliverables**:

1. **Gold Master Build** -- Final build submitted to Steam. Version 1.0.0. No known P0 or P1 bugs. Mac build submitted simultaneously.

2. **Launch Day (Week 1)** -- Monitor Steam reviews, monitor crash reports (telemetry if enabled), monitor social media conversation, respond to critical bugs within 24 hours. Day-one patch deployed if necessary.

3. **Community Management** -- Establish Steam discussion forum presence, respond to player questions about mechanics, collect feedback on balance and difficulty, identify common confusion points for post-launch tutorial improvements.

4. **Post-Launch Patch 1.1 (Week 2-4)** -- Address any emergent bugs from launch week, balance adjustments based on player data (if 80% of players choose the same note option consistently, rebalance that dilemma), UI clarity improvements based on player feedback, minor quality-of-life features (skip cutscenes, faster text speed, save slot management).

5. **Sales Tracking and Performance Review** -- Track daily sales, Steam ranking, review score, refund rate. Compare to success targets. Identify any press coverage gaps or marketing opportunities. Adjust post-launch marketing spend based on early performance.

6. **Retrospective (Internal)** -- Team debrief. What went well? What went wrong? What would we do differently on the next project? Document lessons learned. Celebrate the ship.

**Exit Criteria**:
- Game shipped on Steam and Mac
- Launch week player sentiment positive (Steam reviews "Very Positive" or better)
- No P0 bugs in launch build
- Sales tracking shows path to Year One target (40K-60K units)
- Team morale intact (no burnout casualties, no crunch debt)

**Duration**: 2 months (launch month + 1 month post-launch support)

---

## SPRINT PLAN (SAMPLE: PROTOTYPE MILESTONE)

This is a detailed sprint breakdown for Milestone 1 (Prototype). Other milestones follow similar cadence but are not fully detailed here to avoid document bloat. Adjust sprint length and task granularity based on team velocity after Sprint 1.

### Sprint 1 (Weeks 1-2): Desk Foundation

**Goal**: Build the script triage interface. Scripts appear, player can read coverage, player can make pass/consider/priority decisions.

| Task | Owner | Estimate | Dependency | Priority |
|---|---|---|---|---|
| Design desk UI layout (wireframes, information hierarchy) | UI/UX Designer | 3 days | None | P0 |
| Implement script data structure (logline, genre, grade, attachments, clock) | Lead Programmer | 2 days | None | P0 |
| Create script coverage sheet asset (visual design) | Visual Artist | 2 days | UI layout approved | P0 |
| Implement script spawn system (10 scripts appear over time) | Lead Programmer | 3 days | Script data structure | P0 |
| Implement triage verbs (pass, consider, priority) | Lead Programmer | 2 days | Script spawn system | P0 |
| Implement expiration clock (scripts expire after N days) | Lead Programmer | 2 days | Triage verbs | P1 |
| Author 10 pilot loglines + coverage sheets | Narrative Designer | 3 days | None | P0 |
| Playtest: Can player triage 10 scripts in under 5 minutes? | QA Lead | 1 day | All above complete | P0 |
| Iterate on desk UI based on playtest feedback | UI/UX Designer + Lead Programmer | 2 days | Playtest complete | P1 |

**Sprint Retrospective**: Did the desk interface feel tactile and satisfying, or overwhelming and spreadsheet-like? If playtesters report information overload, adjust visual hierarchy in Sprint 2.

---

### Sprint 2 (Weeks 3-4): Notes System Prototype

**Goal**: Build the creative dilemma interface. Present 10 authored dilemmas, track player choices, display consequences.

| Task | Owner | Estimate | Dependency | Priority |
|---|---|---|---|---|
| Design notes interface (dilemma presentation, option layout) | UI/UX Designer | 2 days | None | P0 |
| Implement dilemma data structure (context, options, consequences) | Lead Programmer | 2 days | None | P0 |
| Implement notes session flow (dilemmas appear sequentially) | Lead Programmer | 3 days | Dilemma data structure | P0 |
| Implement consequence tracking (Quality Ceiling, Commercial Floor, Trust, Brand) | Lead Programmer | 3 days | Notes session flow | P0 |
| Author 10 creative dilemmas across 3 pilot concepts | Narrative Designer | 5 days | None | P0 |
| Create consequence feedback UI (show shifts after each note) | UI/UX Designer + Lead Programmer | 2 days | Consequence tracking | P1 |
| Playtest: Do dilemmas feel like hard choices or obvious optimization? | QA Lead | 1 day | All above complete | P0 |
| Analyze playtest data: which options chosen most frequently? | Game Designer | 1 day | Playtest complete | P0 |
| Rebalance dilemmas based on playtest data (adjust consequence values) | Game Designer + Narrative Designer | 2 days | Analysis complete | P1 |

**Sprint Retrospective**: Did any dilemma have a single option chosen more than 70% of the time? If yes, rewrite the dilemma framing or adjust mechanical consequences. The Notes System MUST feel like taste expression, not math.

---

### Sprint 3 (Weeks 5-6): Pipeline and Network Identity

**Goal**: Build the development pipeline greybox and the network identity tracker.

| Task | Owner | Estimate | Dependency | Priority |
|---|---|---|---|---|
| Design pipeline whiteboard interface (index cards, phases) | UI/UX Designer | 2 days | None | P0 |
| Implement pipeline data structure (projects, showrunners, cast, budget) | Lead Programmer | 3 days | None | P0 |
| Implement showrunner attachment (6 showrunners with stats and fit scores) | Lead Programmer | 3 days | Pipeline data structure | P0 |
| Implement casting (12 actors with star power/talent/salary) | Lead Programmer | 3 days | Showrunner attachment | P0 |
| Implement budget allocation (split $3M pilot budget across 5 categories) | Lead Programmer | 2 days | Casting | P1 |
| Design network identity radar chart (4 axes, visual layout) | UI/UX Designer | 2 days | None | P1 |
| Implement network identity tracker (axes update based on note choices) | Lead Programmer | 3 days | Notes System complete | P1 |
| Author 6 showrunner profiles (stats, tendencies, personality snippets) | Narrative Designer | 3 days | None | P1 |
| Playtest: Can player assemble a pilot team in under 2 minutes? | QA Lead | 1 day | All above complete | P0 |
| Playtest: Does network identity chart reflect player choices legibly? | Game Designer | 1 day | Playtest complete | P1 |

**Sprint Retrospective**: Did the pipeline feel like strategic decision-making or busywork? If players report "I'm just clicking through menus," simplify the interface or add attention flags to surface only projects that need intervention.

---

### Sprint 4 (Weeks 7-8): Rough Cut and Prototype Integration

**Goal**: Connect all prototype systems into one flow. Player triages scripts → develops pilots → gives notes → views rough cut → makes greenlight decision.

| Task | Owner | Estimate | Dependency | Priority |
|---|---|---|---|---|
| Implement rough cut viewer (text description + stats + test audience data) | Lead Programmer | 3 days | Pipeline complete | P0 |
| Author 4 rough cut descriptions (varied tone, quality, test audience reactions) | Narrative Designer | 2 days | None | P0 |
| Connect desk → pipeline flow (prioritized scripts enter pipeline) | Lead Programmer | 2 days | Desk and pipeline complete | P0 |
| Connect notes → rough cut flow (notes affect rough cut stats) | Lead Programmer | 3 days | Notes system and rough cut complete | P0 |
| Implement greenlight/kill decision at rough cut stage | Lead Programmer | 2 days | Rough cut viewer | P0 |
| Add consequence feedback for greenlight/kill (budget impact, reputation shift) | Lead Programmer | 2 days | Greenlight/kill decision | P1 |
| Playtest: Full prototype loop (desk → pipeline → notes → rough cut) | QA Lead | 2 days | All above complete | P0 |
| Playtest: Does the 5-minute loop feel satisfying? | Game Designer | 1 day | Playtest complete | P0 |
| Bug fixing and polish (prototype stability) | Lead Programmer | 3 days | Playtest feedback | P1 |

**Sprint Retrospective**: Prototype milestone exit criteria review. Is the Notes System working? Is the desk satisfying? Can we proceed to Vertical Slice with confidence? If not, extend Prototype phase by 2-4 weeks and iterate.

---

## RISK REGISTER

Every project has risks. The difference between a professional producer and an amateur is that the professional names them, tracks them, and mitigates them before they explode.

---

### Risk 1: The Notes System Fails to Land Emotionally

**Likelihood**: MEDIUM
**Impact**: CRITICAL
**Severity**: HIGH

**Description**: The Notes System is the emotional core of the game. If players perceive note dilemmas as optimization puzzles rather than creative choices, the entire fantasy collapses. The game becomes a spreadsheet manager instead of a taste simulator.

**Indicators**:
- Playtesters choose the same note option more than 60% of the time across all contexts
- Playtesters describe their decision-making process in terms of "maximizing stats" rather than "protecting the vision" or "making it commercial"
- Exit surveys show low emotional attachment to pilots developed

**Mitigation**:
- Prototype the Notes System first (Sprint 2). Do not proceed to Vertical Slice until playtest data validates that dilemmas feel like genuine choices.
- Author dilemmas with a human writer (NOVA), not an algorithm. Every dilemma must be framed as a creative conversation, not a stat adjustment.
- Playtest dilemmas in multiple strategic contexts (Prestige network, Populist network, budget crisis, high President Patience). Ensure no single option is dominant across all contexts.
- If a dilemma consistently shows one option chosen 70%+ of the time, rewrite the framing or rebalance the mechanical consequences.

**Contingency**:
- If Notes System playtesting fails in Prototype (Month 3), extend Prototype phase by 4-6 weeks. Redesign dilemma structure. Test alternate framings (e.g., present dilemmas as dialogue with showrunner NPCs, present dilemmas as internal monologue, present dilemmas as trade-offs with visible second-order effects).
- If Notes System still fails after extended iteration, escalate to design pivot: reduce Notes System to secondary mechanic, elevate another system (e.g., Showrunner relationship management, Upfronts presentation strategy) to primary emotional engagement layer. This is a last resort and represents a major scope/vision change.

---

### Risk 2: Authored Content Volume Exceeds Team Capacity

**Likelihood**: HIGH
**Impact**: HIGH
**Severity**: HIGH

**Description**: The game requires 80 pilot concepts, 200 creative dilemmas, 12 showrunner profiles, 30 actor profiles, 40 trade headlines, 20 rough cut descriptions, and 15 Industry Signal events. All authored. All written by humans. This is 6-9 months of content writing for one narrative designer, assuming no other duties. If content production falls behind, the game either ships with repetitive content (breaking immersion) or delays.

**Indicators**:
- Content authoring velocity falls below 3 dilemmas per day (target: 200 dilemmas over 60 working days = 3.3 dilemmas/day)
- Narrative Designer reports burnout or quality degradation
- Playtesters report seeing repeated phrases, templated language, or dilemmas that feel "samey"

**Mitigation**:
- Hire a second writer or contract a freelance narrative designer for content authoring support (budgeted as 0.5-1 FTE for Months 7-10, Alpha phase).
- Build modular content: dilemmas are tagged by creative axis (e.g., "antihero question," "expensive shot," "test audience problem," "love triangle pressure") and can be contextually applied to multiple pilot concepts. This allows 200 unique dilemmas to generate 400-600 dilemma appearances across 80 pilots.
- Establish content pipeline early (Month 4, Vertical Slice start): dilemma template, style guide, mechanical consequence ranges, review process. Every dilemma follows the same structure (context paragraph, 2-3 options, visible consequences, hidden long-term effects).
- Track content production velocity weekly. If velocity drops below 3 dilemmas/day for 2 consecutive weeks, escalate immediately.

**Contingency**:
- If content production falls 20% behind schedule by Month 8 (mid-Alpha), reduce authored content scope: 60 pilot concepts instead of 80 (cut 20 lower-priority genres), 150 dilemmas instead of 200 (accept some repetition in late-game seasons). Playtest tolerance for repetition and adjust cut depth accordingly.
- If content production falls 40% behind schedule, delay Alpha exit by 4 weeks to allow content catch-up. Do not proceed to Beta with incomplete content library.

---

### Risk 3: The Desk Interface Overwhelms Players

**Likelihood**: MEDIUM
**Impact**: MEDIUM-HIGH
**Severity**: MEDIUM

**Description**: The desk triage system presents 15-20 scripts with multiple parameters (logline, genre, grade, attachments, blind-spots, expiration clock). If the visual hierarchy and information density are not tuned correctly, players experience cognitive overload in the first 15 minutes and bounce.

**Indicators**:
- Playtesters take longer than 10 minutes to triage 15 scripts (target: 5-8 minutes)
- Playtesters consistently miss critical information (e.g., expiration clocks, blind-spot indicators)
- Playtesters report feeling "lost" or "don't know what to prioritize"
- Tutorial skip rate above 40% (players skip tutorial because they assume they understand, then get overwhelmed)

**Mitigation**:
- Design for 5-second glanceability: genre color-coding, letter grade in large font, logline bolded, attachments as name badges, blind-spots as small warning icons.
- Prototype desk interface in Sprint 1 (Week 1-2) and playtest immediately. Do not wait until Vertical Slice to validate information hierarchy.
- Implement progressive disclosure: Season 1 presents fewer scripts (10 instead of 15) with generous expiration clocks (7 days instead of 3-4). Complexity ramps in Season 2-3.
- Add optional "desk assistant" tutorial mode: first 3 scripts in Season 1 have pop-up tooltips explaining each parameter. Can be disabled by experienced players.

**Contingency**:
- If desk playtesting shows consistent overload, reduce script volume per season: 10 scripts instead of 15, 6 developments instead of 8, 3 pilots instead of 4. Compress the pipeline to reduce decision density.
- If information density is the problem, remove or consolidate parameters: eliminate "blind-spot indicators" as a separate UI element, bake that information into the logline text itself. Simplify genre tags from 8 to 5.

---

### Risk 4: Late-Game Seasons (6-8) Feel Like a Grind

**Likelihood**: MEDIUM
**Impact**: MEDIUM
**Severity**: MEDIUM

**Description**: Management sims often suffer from late-game stagnation. By Season 6, players may have "solved" the systems and are executing optimal strategies on autopilot. Seasons 6-8 feel like obligation rather than engagement.

**Indicators**:
- Playtest completion rate drops below 50% after Season 5 (half of players abandon before finishing the campaign)
- Playtesters report "I was just going through the motions" or "I stopped caring about the pilots"
- Playtesters spend less time on note dilemmas in Season 6-8 (indicator: average time per dilemma drops below 45 seconds, suggesting disengagement)

**Mitigation**:
- Season 6 introduces a major disruption (Writers' Strike) that invalidates stockpiled strategies. This is a deliberate reset to force adaptation.
- Season 7 introduces audience fragmentation: no single strategy (Prestige, Populist, Risk-Taking) dominates. The landscape itself becomes uncertain, requiring player to read signals and adapt.
- Season 8 shifts the player's motivation from "optimize" to "reflect": the retrospective narrator begins commenting on the player's career mid-season, creating a narrative frame that elevates the final decisions from tactical to existential.
- Introduce late-game emergent drama: trusted showrunners burn out, rivals poach talent, President Patience becomes volatile. The systems create new challenges even if the player has mastered the verbs.

**Contingency**:
- If late-game playtesting shows completion rates below 50%, compress the campaign: 6 seasons instead of 8. Cut Seasons 7-8, move the Writers' Strike to Season 5, end with retrospective in Season 6. A tighter, more intense campaign is better than a campaign that outstays its welcome.
- If compression is insufficient, add late-game "what-if" scenarios: optional challenge seasons where the player inherits a failing network, or a scenario where the player's best showrunner leaves and they must rebuild. These are high-stakes variants that reignite engagement without extending the critical path.

---

### Risk 5: The Upfronts Presentation Feels Anticlimactic

**Likelihood**: MEDIUM
**Impact**: MEDIUM
**Severity**: MEDIUM

**Description**: The upfronts are the seasonal climax. If the presentation sequence feels like "click through a menu and watch a number go up," the dramatic payoff fails. Players should feel the tension of presenting their slate to a room full of skeptics.

**Indicators**:
- Playtesters describe the upfronts as "boring" or "just waiting for the result"
- Playtesters skip through upfronts presentation after the first season (indicator: average time spent on upfronts drops below 2 minutes, target is 5-7 minutes)
- Playtesters report no emotional response to ad buyer reactions (no tension, no relief)

**Mitigation**:
- Upfronts must be a performance, not a menu. Presentation order matters. Sell Line choice matters. Ad Buyer Confidence meter must be visible and responsive in real-time.
- Add specific ad buyer reactions: individual buyers (represented as portrait icons) react to each show. One buyer loves the crime drama, another is cold. The player reads the room.
- Add consequence weight: if the player overpromises in the Sell Line ("the next great American drama") and the show underperforms, the backlash is visible (trade headlines, President Patience drop, reduced ad rates next season).
- Audio/music design is critical here: build tension with a subtle score, payoff with applause or silence based on performance.

**Contingency**:
- If upfronts playtesting shows disengagement, add a risk/reward layer: the player can choose to "oversell" a pilot (boosts ad commit by 20% but increases expectations, raising the ratings threshold for renewal) or "undersell" (conservative ad commit but lower expectations, easier to exceed). This transforms the upfronts from a reporting event to a strategic gamble.
- If presentation pacing is the problem, allow player to fast-forward through upfronts after the first season but display a summary screen with key decisions and outcomes. Respect the player's time if they have seen the sequence before.

---

### Risk 6: Network President (Richard Kessler) Feels Like an Obstacle, Not a Character

**Likelihood**: MEDIUM
**Impact**: LOW-MEDIUM
**Severity**: LOW

**Description**: Richard Kessler is the player's boss and primary constraint. If he is characterized only as a mechanical pressure system (Patience stat, budget adjustments), he feels like a punitive algorithm rather than a human with fears and motivations. Players resent him instead of understanding him.

**Indicators**:
- Playtesters describe Richard as "annoying" or "just getting in the way"
- Playtesters express no empathy for Richard's position
- Playtesters skip Richard's dialogue after Season 2 (indicator: dialogue skip rate above 60%)

**Mitigation**:
- Richard must have a visible arc. He starts as an obstacle (risk-averse, demanding hits) but can evolve into an ally if the player earns his trust by delivering results. Late-game Richard, if the relationship is strong, defends the player's bold choices in conversations with the corporate parent.
- Richard's dialogue must reveal his wound: he was a genius in the '90s, his instincts stopped working, he is terrified of another public failure. This context reframes his caution as fear, not malice.
- Give Richard moments of vulnerability: a late-season conversation where he admits he does not understand the new television landscape, or a moment where he confesses that the board is pressuring him. These moments humanize him.

**Contingency**:
- If Richard playtesting shows consistent resentment, reduce his presence: fewer dialogue scenes, more mechanical pressure (Patience stat adjustments without lengthy conversations). Some players do not want their boss to be a character; they want the boss to be a system they navigate around. Respect that player type.
- Alternatively, add a dialogue option layer: the player can choose how to respond to Richard (deferential, defensive, honest). Responses affect Richard's trust and the player's latitude. This gives players agency in the relationship rather than forcing them to endure Richard passively.

---

### Risk 7: The Game Is Perceived as "Just for TV Industry Insiders"

**Likelihood**: MEDIUM
**Impact**: MEDIUM
**Severity**: MEDIUM

**Description**: The game's setting (2000s television development) and vocabulary (18-49 demo, upfronts, DVR adoption, serialization appetite) could alienate players who are not TV obsessives. If the game feels like it requires industry knowledge to understand, the audience shrinks to a niche.

**Indicators**:
- Playtesters outside the TV industry report confusion about terminology or systems
- Steam reviews include phrases like "too much jargon" or "I didn't understand what I was supposed to do"
- Wishlists underperform target (below 20K at launch), suggesting audience is narrower than expected

**Mitigation**:
- Industry jargon is always used in context. Never explain a term explicitly; let the player infer meaning through usage. "We need a bump in the 18-49 demo" is self-explanatory in the context of a ratings discussion.
- Tutorial is embedded in Season 1 gameplay, not a separate mode. The player learns by doing, and the game's systems are forgiving in the early season.
- Marketing emphasizes the universal fantasy ("you decide what gets made") rather than the industry-specific setting. Lead with the decision fantasy, not the period detail.
- Playtesting must include non-TV-industry players. Target: 50% of playtesters have no professional connection to entertainment industry. If they understand the game, the general audience will.

**Contingency**:
- If external beta playtest shows consistent confusion among non-industry players, add an optional glossary (accessible from pause menu) that defines key terms (demo, upfronts, pilot, syndication, etc.). Glossary is opt-in, never forced.
- If confusion persists, simplify terminology: replace "18-49 demo" with "key audience," replace "upfronts" with "advertiser presentation," replace "DVR adoption" with "time-shifted viewing." The game loses some period flavor but gains accessibility.

---

## CRITICAL PATH

The critical path is the sequence of tasks that, if delayed, delay the entire project. Everything else is parallel or secondary.

### Critical Path: Prototype to Launch

```
MONTH 1-3: PROTOTYPE
  └─> Desk Interface (Sprint 1) [2 weeks]
       └─> Notes System (Sprint 2) [2 weeks]
            └─> Pipeline Greybox (Sprint 3) [2 weeks]
                 └─> Integration & Playtest (Sprint 4) [2 weeks]
                      └─> DECISION POINT: Notes System works?
                           ├─> YES: Proceed to Vertical Slice
                           └─> NO: Extend Prototype 4-6 weeks, iterate Notes System

MONTH 4-6: VERTICAL SLICE
  └─> One Full Season Playable [8 weeks]
       └─> UI Suite Visual Design [parallel, 6 weeks]
            └─> Authored Content Batch 1 (20 dilemmas, 15 pilots) [parallel, 8 weeks]
                 └─> Playtest Vertical Slice [2 weeks]
                      └─> DECISION POINT: Vertical Slice demo-ready?
                           ├─> YES: Lock Steam page, begin wishlist campaign, proceed to Alpha
                           └─> NO: Extend Vertical Slice 2-4 weeks, address critical playtest feedback

MONTH 7-10: ALPHA
  └─> 8 Seasons Playable [10 weeks]
       └─> Authored Content Library Complete (200 dilemmas, 80 pilots) [CRITICAL PATH, parallel, 12 weeks]
            └─> Landscape System Full Implementation [parallel, 8 weeks]
                 └─> Economy System Full Implementation [parallel, 6 weeks]
                      └─> FEATURE LOCK at Alpha Exit
                           └─> DECISION POINT: All systems complete and interacting?
                                ├─> YES: Proceed to Beta
                                └─> NO: Delay Alpha exit 2-4 weeks, finish incomplete systems

MONTH 11-14: BETA
  └─> Balance Pass (Notes System, Economy, Difficulty) [6 weeks]
       └─> Content Revision Pass (20-30% of dilemmas revised) [parallel, 6 weeks]
            └─> Bug Fixing Systematic (QA database, prioritization) [parallel, 8 weeks]
                 └─> External Beta Test [4 weeks]
                      └─> DECISION POINT: External beta satisfaction above 7/10?
                           ├─> YES: Proceed to Release Candidate
                           └─> NO: Extend Beta 2-4 weeks, address critical feedback

MONTH 15-16: RELEASE CANDIDATE
  └─> Final Bug Sweep (zero P0, fewer than 5 P1) [4 weeks]
       └─> Performance Optimization (60fps stable on min spec) [parallel, 4 weeks]
            └─> Marketing Assets (trailer, screenshots, press kit) [parallel, 4 weeks]
                 └─> GO/NO-GO DECISION (1 week before launch)
                      ├─> GO: Proceed to launch
                      └─> NO-GO: Delay 2-4 weeks, fix critical issue

MONTH 17-18: GOLD MASTER & LAUNCH
  └─> Launch Day [Week 1]
       └─> Monitor reviews, crash reports, player feedback [Week 1]
            └─> Post-Launch Patch 1.1 [Week 2-4]
                 └─> PROJECT COMPLETE
```

**Critical Path Bottlenecks**:
1. **Notes System validation (Month 3)** -- If this fails, the entire project is at risk.
2. **Authored content production (Month 7-10)** -- 200 dilemmas must be written on schedule or content quality degrades.
3. **External beta satisfaction (Month 14)** -- If external playtesters do not enjoy the game, launch reviews will be harsh.

**Buffer**: The 18-month timeline includes approximately 6-8 weeks of buffer distributed across milestones. If any milestone slips by more than 2 weeks, escalate immediately and reassess scope or timeline.

---

## SCOPE MANAGEMENT

Scope creep kills more games than bad design. Here is what we are NOT building, and why.

### In Scope (Non-Negotiable, Core to Vision)
- The Desk triage system
- The Notes System (authored dilemmas)
- The Development Pipeline (showrunner attachment, casting, budget allocation)
- Network Identity (4-axis radar chart, brand emergence)
- Upfronts presentation sequence
- 8-season campaign (2002-2010)
- Historical inflection points (cable prestige threat, DVR disruption, Writers' Strike)
- Rival networks (3 AI opponents with visible strategies)
- Network President character (Richard Kessler, Patience stat, relationship arc)
- Rival executive character (Diane Valdez, competitive pressure)
- Key showrunner characters (Tommy Morell, Sandra Okonkwo, at minimum)
- Authored content library (80 pilots, 200 dilemmas, 12 showrunners, 30 actors)
- Economy system (revenue sources, expenses, budget carryover, Cash Crisis triggers)
- Season 8 retrospective (career evaluation, prestige television historian narrator)

### Stretch Goals (Post-Launch DLC / Expansion Candidates)
- **The Writers' Room** (deeper layer, sit in on episode arcs) -- This is a full expansion. 6-9 months of additional development. Do not scope into base game.
- **Talent Career Arcs** (showrunners evolve, burn out, have late-career renaissances) -- Partially implemented in base game (showrunner stat progression). Full characterization (dialogue scenes, relationship arcs) is expansion material.
- **The Screening Room** (stylized rough cut sequences, storyboard aesthetic) -- This is a visual-heavy feature that dramatically increases art production cost. Do not scope into base game. If the game succeeds commercially, this is the premium expansion.
- **Awards Season** (Emmy campaigns, critical year-end lists) -- Adds 2-3 months to Alpha phase. Defer to post-launch content update or DLC.
- **The Rival Executive (Diane) as Playable Character** -- Alternate campaign mode. This is a full expansion (8-9 months of additional writing and balancing).

### Cut List (Not in v1, Not in Expansions, Not Ever)
- **Playable show production** (directing episodes, managing sets) -- This is a different game. The player is the executive, not the showrunner.
- **Real licensed TV shows** (recreating The Sopranos, The Wire, Lost) -- Legal nightmare. Expensive. Unnecessary. The game's fictional shows evoke the archetypes without IP exposure.
- **Multiplayer / competitive** -- Dilutes the power fantasy. The fantasy is singular: you are THE exec. Multiplayer is not who this game is for.
- **Procedural script generation** -- Destroys the Notes System's specificity. The game needs authored content, not algorithms.
- **Voiced dialogue** -- Budget sink. The game is text-driven. Voice work costs $50K-$150K for full voice cast and eats budget that should go to authored content.
- **Console versions at launch** -- PC/Mac only. Switch port is post-launch (requires UI rescaling work, 2-3 months). PlayStation/Xbox ports require certification, QA overhead, and audience validation that PC launch will provide.
- **VR mode** -- No.

### Scope Change Protocol

If anyone (designer, programmer, narrative designer, external playtester) proposes a new feature after Alpha feature lock, the following process applies:

1. **Proposal Documentation**: Write a one-page brief describing the feature, why it is necessary, what problem it solves, and what it costs (time, budget, risk).
2. **Cost-Benefit Analysis**: Producer evaluates cost (dev time, content authoring, QA overhead) vs. benefit (player satisfaction impact, critical path risk).
3. **Team Review**: Producer, Designer, and Lead Programmer review together. Unanimous approval required to proceed.
4. **Scope Trade**: If the new feature is approved, an existing feature of equal cost must be cut or deferred. No scope addition without scope subtraction.
5. **Milestone Impact Assessment**: If the feature affects the critical path or pushes a milestone exit by more than 1 week, escalate to executive decision (studio leadership, if external funding is involved).

**Default Answer to Scope Creep**: No. The game we scoped is the game we are building. Ship it, then iterate in post-launch updates if the feature is genuinely valuable.

---

## DEPENDENCIES AND BLOCKERS

### External Dependencies
- **Steam Platform**: Steam SDK integration, Steam achievements, Steam Cloud saves. Steam Developer account must be established by Month 4 (Vertical Slice start). Steam build pipeline must be tested by Month 15 (Release Candidate).
- **Mac Build Tools**: Xcode, Mac hardware for testing. If Mac build is delayed, do not delay PC launch. Ship PC first, Mac follows 2-4 weeks later if necessary.
- **Freelance Writers** (if content production falls behind): Budget allocated for 0.5-1 FTE contract writer in Months 7-10. Contracts must be negotiated by Month 6 to avoid content bottleneck.
- **Composer/Sound Designer** (ECHO): Part-time/contract. Music and sound design are not critical path but are necessary for polish. Audio delivery must be complete by Month 14 (Beta exit) to allow integration and bug fixing in Release Candidate phase.

### Internal Dependencies
- **Authored Content Library**: NOVA (Narrative Designer) is the single point of failure for content production. If NOVA is unavailable for more than 2 weeks during Alpha phase (illness, emergency, burnout), content production falls behind schedule. Mitigation: cross-train a second team member (Game Designer or Producer) to write dilemmas in NOVA's style, or have freelance writer on standby.
- **Notes System Implementation**: Lead Programmer owns Notes System engineering. This is the highest-risk technical dependency. If Notes System implementation is delayed or technically unstable, the entire Prototype phase is at risk. Mitigation: prioritize Notes System in Sprint 2, allocate additional programming time if needed.
- **UI/UX Design**: The desk interface, notes interface, and upfronts presentation are UI-driven experiences. If UI/UX Designer is unavailable or if designs require multiple iterations, visual design becomes a bottleneck. Mitigation: involve UI/UX Designer in wireframing during pre-production (before Month 1), lock visual style guide by Month 4 (Vertical Slice start).

### Blocker Escalation Protocol
If any task is blocked for more than 3 business days, the task owner must escalate to Producer immediately. Producer assesses blocker severity:
- **P0 Blocker** (blocks critical path): Drop everything, resolve immediately. Reassign resources if necessary.
- **P1 Blocker** (blocks milestone deliverable): Resolve within 1 week. Adjust sprint schedule if necessary.
- **P2 Blocker** (blocks secondary feature): Resolve within 2 weeks or defer feature to next milestone.

---

## BUDGET ESTIMATE (High-Level)

This is a rough-order-of-magnitude budget for an 18-month development cycle with a 9-person team.

| Category | Cost | Notes |
|---|---|---|
| **Salaries (Core Team)** | $650K-$900K | 9 FTE x $60K-$90K average annual salary (mid-level game dev rates) x 1.5 years |
| **Freelance/Contract (Writer, Composer)** | $40K-$60K | 1 contract writer (0.5 FTE, 4 months) + composer/sound designer (part-time, 6 months) |
| **Software/Tools** | $10K-$15K | Unity (free for small teams), Adobe CC, Spine (2D animation), FMOD (audio), GitHub, Trello/Jira, Slack |
| **Hardware** | $15K-$20K | Workstations for team (laptops, monitors), Mac hardware for testing, external drives, peripherals |
| **Marketing** | $30K-$50K | Steam store assets, trailer production, press kit, social media ads, influencer outreach |
| **Platform Fees** | $10K-$15K | Steam Direct fee ($100), revenue share (30%, but post-launch), localization prep |
| **Miscellaneous** | $20K-$30K | Office space (if not remote), internet, cloud storage, legal (contracts, IP protection), buffer for unexpected costs |
| **TOTAL** | **$775K-$1.09M** | Assumes no external funding, bootstrapped or small indie publisher deal |

**Funding Models**:
- **Bootstrapped/Self-Funded**: Founder equity, personal savings. High risk, full creative control.
- **Publisher Deal**: Small indie publisher advances $500K-$800K against future revenue. Publisher takes 30-50% of revenue share post-recoup. Publisher provides marketing support and platform relationships.
- **Crowdfunding** (Kickstarter, Fig): Target $300K-$500K raise to cover 40-60% of budget. Requires strong pitch video, demo (Vertical Slice), and community building pre-campaign. Risk: campaign fails, project is underfunded.

**Recommendation**: Pursue small indie publisher deal. The authored content volume and 18-month timeline make this too expensive for pure bootstrapping unless founder has significant capital reserves. A publisher deal provides financial runway and marketing expertise (critical for a niche management sim without built-in brand recognition).

---

## FINAL NOTES

This is the production plan. It is not a wish list. It is not a dream document. It is the roadmap to shipping PILOT in 18 months with a team of 9 people and a budget under $1.1M.

Here is what I need every person on this team to understand:

1. **The Notes System is the game**. If it does not work by Month 3, we stop and fix it. No exceptions. Every other system is in service of the Notes System. Protect it. Playtest it. Iterate it until it sings.

2. **Authored content is the soul**. 200 dilemmas. 80 pilots. Every single one written by a human who cares. This is not a procedural generation project. This is a craft project. Respect the craft. Protect the writers. If content production falls behind, hire help immediately.

3. **Scope is locked at Alpha**. Feature lock is not a suggestion. It is a line in the sand. After Month 10, we are polishing, balancing, and bug fixing. We are not adding systems. If someone pitches a "quick feature" in Beta, the answer is no. Ship the game we scoped, then iterate in post-launch if the feature is valuable.

4. **The critical path is sacred**. Desk → Notes → Content Library → Beta Satisfaction. If any of those four fails, the project is at risk. Everything else is parallel or secondary. Protect the critical path. If a task is not on the critical path and it is pulling resources from a task that is, cut the non-critical task.

5. **This game is not for everyone, and that is okay**. PILOT is a management sim for TV obsessives, strategy players, and narrative game fans who want to feel the weight of creative decisions. It is not a mass-market game. It is not a viral sensation. It is a 40K-60K unit indie success that builds a passionate community and sustains a small team. Do not chase the wrong audience. Build for the audience that will love this game for what it is.

6. **Ship something real**. A shipped game beats a perfect concept. The game we ship in Month 18 will not be perfect. It will have rough edges. Some dilemmas will be better than others. Some systems will feel more polished than others. That is okay. The game we ship will be complete, playable, emotionally engaging, and worth the player's $25. That is the bar. Ship it, learn from it, and make the next one better.

What is the MVP? The MVP is the Notes System working, the Desk feeling good, and one full season that makes a player care about a pilot they developed. If we have those three things by Month 6, we have a game. Everything else is polish, content volume, and endgame depth.

What is the critical path? Prototype (validate Notes System) → Vertical Slice (prove one full season works) → Alpha (all 8 seasons playable, content library complete) → Beta (balance, polish, bug fixing) → Release Candidate (final sweep, launch prep) → Gold Master (ship it).

What could kill this project? Three things: Notes System fails to land emotionally (mitigation: playtest early and often, iterate until it works). Authored content production falls behind schedule (mitigation: hire contract writer, reduce content scope if necessary). Late-game stagnation causes playtest abandonment (mitigation: Season 6 disruption, Season 7 fragmentation, Season 8 retrospective shifts motivation from optimize to reflect).

What is success? 40K-60K units in Year One. "Very Positive" Steam reviews. A community of players who finish the campaign and immediately want to play again with a different creative philosophy. Press coverage from TV industry outlets (Variety, Hollywood Reporter) calling the game "surprisingly authentic." Management sim players adding PILOT to the canon alongside Game Dev Tycoon and Football Manager.

This is the plan. Now let us build the game.

-- CLOCK
