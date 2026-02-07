# PILOT -- Level Design Document

**Author**: GRID (Level Designer)
**Version**: 1.0
**Date**: 2026-02-07
**Status**: Pre-Production Framework

---

> "A level isn't geometry. It's a guided experience that feels like freedom. Every space teaches something. Every flow path is pacing. Where does the player look? That's the question."

I have read REED's systems. I have read NOVA's world. Now let me tell you how those systems are STAGED. Where the player's eyes go. How information flows through space. What the pacing curve feels like across a season, across a career, across the moment-to-moment rhythm of reading a script on a desk that is slowly drowning in paper.

PILOT is not a game about spaces in the traditional sense -- there are no dungeons, no combat arenas, no parkour courses. But every management sim is a level design problem. The desk is a level. The development pipeline is a level. The upfronts are a boss fight rendered in presentation software and advertiser confidence meters. My job is to make sure the player always knows where to look, what matters NOW, and how to navigate complexity without drowning in it.

Let me show you the flow.

---

## 1. CORE SPATIAL METAPHOR: THE OFFICE AS NAVIGABLE PSYCHOLOGY

### 1.1 The Design Challenge

PILOT takes place almost entirely inside offices, screening rooms, and conference spaces. There is no traditional level geometry. No combat spaces. No traversal challenges. The player does not jump, climb, or shoot. The player READS, DECIDES, and NAVIGATES INFORMATION.

This means the level design challenge is: **how do you create spatial flow, pacing, and breadcrumbing in a UI-driven management sim?**

Answer: The office is not a background. The office is the level. The player's desk, their walls, their windows, their physical space -- these are the geometry. The flow is not the player moving through space. The flow is INFORMATION moving through the player's attention. Level design in PILOT is attention architecture.

### 1.2 The Player's Spatial Anchor: The Desk

The desk is the hub. The desk is always visible. The desk is where the 30-second loop happens. When the player is overwhelmed, they can look at the desk and know: this is the core verb. Read. Triage. Decide.

**Desk Layout (Top-Down View)**:

```
              WINDOW (west-facing, late afternoon light)
     +--------------------------------------------------+
     |                                                  |
     |                 [WALL SPACE]                     |
     |   [Network Identity Chart]  [Corkboard: Industry |
     |                              Signals]            |
     +--------------------------------------------------+
                              |
         [DESK -- Player's Territory]

    LEFT ZONE                CENTER ZONE              RIGHT ZONE
  (Input/Intake)           (Decision Space)         (Output/Status)

  - Script pile         - Active script          - Development
    (new arrivals)        (open for reading)       pipeline whiteboard
                                                     (index cards)
  - Coverage sheets     - Legal pad
    (stacked)             (notes)                - Trade magazines
                                                   (industry feedback)
  - Phone               - BlackBerry
    (incoming calls)      (messages/alerts)      - Monitor
                                                   (rough cuts,
  - Post-it notes       - Coffee mug               emails)
    (reminders)           (persistent)

         [CHAIR -- Player POV]
```

**Spatial Logic**:

- **LEFT = INPUT.** New information arrives here. Scripts, coverage sheets, phone calls. The left side of the desk is the world asking for the player's attention.
- **CENTER = DECISION.** The active script sits here. The legal pad is here. This is where the player's cursor/attention rests when making a choice. The center is clarity.
- **RIGHT = OUTPUT.** The development pipeline, the status monitors, the trade magazine headlines reflecting the player's decisions. The right side is the consequence zone.

This left-to-right flow mirrors reading direction (in English/Western contexts). The player's eye naturally moves from intake (left) to decision (center) to consequence (right). The desk is not random clutter. The desk is a pacing diagram rendered in office supplies.

**Feedback Through Environmental Change**:

- During **pitch season** (Fall), the left side script pile grows taller each day. Visually oppressive. The player SEES the time pressure as a growing stack.
- During **development** (Winter), the center zone is active -- scripts open, legal pads filled with notes. The right zone (pipeline whiteboard) is dense with index cards.
- During **production** (Spring), the left zone is calm (no new scripts arriving). The center is mostly empty. The right zone is tense -- test audience data, rough cuts queued.
- During **upfronts prep** (Early Summer), the whiteboard on the right becomes the dominant visual -- the player is looking at their slate, deciding what lives and dies.
- During **the season** (Fall-Spring), trade magazines pile up on the right. Ratings headlines. The desk becomes a chronicle of the player's wins and losses.

The desk is a pacing curve you can see. Where the visual density sits tells the player what phase of the loop they are in.

---

## 2. LEVEL BREAKDOWN: THE DEVELOPMENT SEASON AS SPATIAL SEQUENCE

### 2.1 Overview

A single development season (one session, 45-90 minutes) is structured as a spatial sequence across five distinct "levels" -- five phases with different spatial focuses, different pacing, different player attention targets.

Each level has:
- A **PURPOSE** (what the player learns or tests here)
- A **SPATIAL FOCUS** (where does the player look?)
- A **PACING TARGET** (how long does this phase last? what is the tension rhythm?)
- A **BREADCRUMB STRATEGY** (how does the game guide the player to the next phase without hand-holding?)
- A **EXIT CONDITION** (how does the player know this phase is complete?)

### 2.2 LEVEL 1: THE DESK (Pitch Season / Fall)

**Purpose Statement**: Teach the player to triage under information scarcity and time pressure. The player learns that not every script can be read deeply, that the desk rewards pattern recognition, and that every pass/consider/priority decision is a bet with incomplete information.

**Emotional Beat**: Controlled overwhelm. The thrill of possibility mixed with the anxiety of missing something great.

---

**FLOW DIAGRAM (ASCII Top-Down)**:

```
  PHASE START: 15-20 scripts arrive over 4-5 in-game days
  Player has 3 Time Tokens per day (for deep reads)

  DAY 1:
  [Script A] [Script B] [Script C] [Script D] -- arrive on desk (left zone)
      |          |          |          |
      v          v          v          v
  SKIM(5s) / STANDARD(15s) / DEEP READ(30s, costs token)
      |          |          |          |
      v          v          v          v
  PASS / CONSIDER (hold pile) / PRIORITY (enters pipeline)

  Scripts that are PASSED: physically slide off desk (gone forever)
  Scripts in CONSIDER pile: stack in mid-left, expiration clock ticking
  Scripts marked PRIORITY: move to pipeline whiteboard (right zone)

  DAY 2-5: More scripts arrive. Hold pile grows. Expiration clocks pressure.

  PHASE END: Player has selected 8-12 scripts for development.
             Remaining scripts expire or are passed.
```

**Spatial Focus**: The desk, specifically the left and center zones. The player's eye moves from the script pile (left) to the active reading area (center) to the decision (pass/consider/priority).

**Pacing Target**:
- **Length**: 8-12 minutes
- **Rhythm**: Fast-fast-fast-PAUSE-fast-fast-fast. Each script triage is 15-30 seconds (fast). But 2-3 times per pitch season, a script arrives that makes the player PAUSE -- a B+ with an intriguing blind-spot indicator, or an A- from a rookie writer with no attachments but a killer logline. Those pauses are the breath. Without them, the desk is frantic. With them, the desk is a rhythm game with moments of genuine choice.

**Breadcrumbing Strategy**:
- **Visual**: The pipeline whiteboard (right zone) starts empty. As the player marks scripts PRIORITY, index cards appear on the whiteboard. The whiteboard filling up is the visual breadcrumb: "You are making progress toward the next phase."
- **Audio**: A subtle "card placed" sound when a script moves to the pipeline. The sound accumulates -- by the end of pitch season, the player has heard that sound 8-12 times, and it becomes Pavlovian. That sound = commitment.
- **Temporal**: The in-game calendar (visible in the HUD) shows the current week and the upcoming "Development Begins" milestone. As pitch season progresses, the milestone date approaches. The player sees the next phase coming.
- **Feedback Loop**: If the player has selected fewer than 6 scripts by Day 4, the phone rings. It is Richard (the network president). He does not mandate anything, but he says: "Just checking in. How's the desk looking?" The subtext: you need more in the pipeline. This is a gentle nudge, not a hard gate.

**Encounter Breakdown**:

| Encounter Type | Frequency | What It Tests | Example |
|---|---|---|---|
| **The Obvious Pass** | 4-6 per season | Pattern recognition speed | D+ coverage, generic logline, no attachments. Easy no. |
| **The Obvious Priority** | 2-3 per season | Confidence in good material | A coverage, proven showrunner attached, timely concept. Easy yes. |
| **The Hidden Gem** | 1-2 per season | Deep reading pays off | C+ coverage with blind-spot indicator: "Reader may have underrated due to tonal complexity." Deep read reveals brilliance. |
| **The Trap** | 1-2 per season | Trust your instincts, not grades | A- coverage, big-name attachment, but the logline is derivative and the excerpt is flat. Looks great on paper, hollow underneath. |
| **The Expiring Dilemma** | 2-3 per season | Time pressure forces choice | A script in the CONSIDER pile is about to expire. You have not deep-read it. Rival network wants it. Do you commit without full information or let it go? |

**Difficulty Considerations**:
- **Season 1 (Tutorial)**: 10 scripts total. 7 in-game days. Generous expiration clocks. The player cannot fail -- there is always enough time to read everything at standard depth. The goal is teaching the verbs.
- **Season 2-3 (Ramp)**: 12-15 scripts. 5 days. Tighter clocks. The player must choose between deep-reading fewer scripts and skimming more. The hidden gem / trap ratio increases.
- **Season 4+ (Mastery)**: 18-20 scripts. 4 days. Aggressive expiration. Rivals are actively competing for the same scripts (if the player delays, a competitor grabs it). The player must rely on pattern recognition and risk tolerance, not exhaustive analysis.

**Exit Condition**: The calendar advances to "Development Begins," OR the player has manually marked 8-12 scripts as PRIORITY and chooses to advance early. The desk phase ends when the player has committed to their raw material.

---

### 2.3 LEVEL 2: THE PIPELINE (Development / Winter)

**Purpose Statement**: Teach the player strategic resource allocation, showrunner-material fit, and the art of the creative note. The player learns that not all projects deserve equal attention, that synergy is valuable but friction can create breakthroughs, and that notes are not optimizations -- they are conversations.

**Emotional Beat**: Controlled complexity. The satisfaction of assembling the right pieces mixed with the tension of too many projects and not enough budget/time.

---

**FLOW DIAGRAM (Whiteboard Pipeline as Spatial Map)**:

```
   DEVELOPMENT PIPELINE WHITEBOARD (right zone of desk, but expands to fill screen when active)

   Columns (left to right):

   [ SCRIPT ]  -->  [ SHOWRUNNER ]  -->  [ CASTING ]  -->  [ NOTES ]  -->  [ PRODUCTION ]

   Each project = an index card that moves left-to-right through the columns.

   Example (3 simultaneous projects visualized):

   PROJECT A: [Crime Drama] --> [Tommy Morell attached] --> [Casting: 2/3 slots filled] --> [NEEDS ATTENTION: Notes due]
   PROJECT B: [Workplace Comedy] --> [Sandra Okonkwo attached] --> [Casting complete] --> [On track (autopilot)]
   PROJECT C: [Sci-Fi Pilot] --> [Showrunner search] --> [Waiting] --> [Waiting]

   Cards with RED CORNERS = need immediate player attention (conflict, delay, over-budget, note deadline)
   Cards with GREEN CORNERS = on track, running smooth
   Cards with YELLOW CORNERS = minor issue, check when you have time

   Player clicks a card --> expands to detail view for that project
   Player can drag cards between phases manually (when a phase is complete)
```

**Spatial Focus**: The pipeline whiteboard becomes the dominant visual space. The desk recedes into the background (still visible, but de-emphasized). The player is now navigating a horizontal flow of simultaneous projects.

**Pacing Target**:
- **Length**: 20-30 minutes
- **Rhythm**: Burst-sustain-burst-sustain. The player addresses an urgent issue on one project (burst of 2-3 minutes), then that project stabilizes and they move to the next. The rhythm is sequential attention management. The player is NOT clicking through every project every cycle. The player is responding to Attention Flags (red corners) and letting stable projects (green corners) run.

**Breadcrumbing Strategy**:
- **Visual**: Red corner flags on index cards. The player's eye is drawn to red. Red cards demand attention. Green cards are visual relief -- they say "you don't need to look here."
- **Audio**: A soft "alert" tone when a card's status changes (green to yellow, yellow to red). Not intrusive, but noticeable. The player learns to listen for the alert.
- **Narrative**: The phone rings. It is Joel (the agent). "We need to talk about Project A's casting situation." The phone call directs the player's attention to a specific project. The narrative breadcrumb works because the player cares about Joel's tone -- if Joel sounds annoyed, the situation is serious. If Joel sounds amused, it is manageable.
- **Progress Bar**: Each project has a visual progress indicator -- a thin bar at the bottom of its index card showing how far through development it is (0% = just entered pipeline, 100% = pilot ready to shoot). The bars filling up is the visual reward loop.

**Encounter Breakdown**:

| Encounter Type | Frequency | What It Tests | Example |
|---|---|---|---|
| **Synergy Match** | 2-3 per season | Pattern recognition (fit assessment) | The player sees a gritty crime script and a showrunner with high Vision/Craft who loves dark material. Attaching them is obvious and generates immediate green-corner stability. |
| **Tension Pairing** | 1-2 per season | Risk tolerance | A showrunner with Ego 8 on a script that needs commercial compromises. The fit is bad on paper, but 20% chance of breakthrough. Do you risk it? |
| **Casting Crisis** | 2-3 per season | Resource allocation under constraint | The perfect actor wants $400K/episode. Your budget is $3M total. Casting them starves the production design budget. Do you pay the star or distribute the money? |
| **The Notes Dilemma** | 4-8 per season (the CORE encounter) | Creative taste + strategic positioning | See section 3 for full Notes System flow. Each note is its own micro-level. |
| **Budget Overrun** | 1-2 per season | Crisis management | A showrunner's pilot is $800K over budget. Do you: (A) cut the budget and force compromises, (B) find the money elsewhere (hurts other projects), (C) kill the project and eat the sunk cost? |
| **Showrunner Conflict** | 1 per season | Relationship management | A showrunner is clashing with the lead actor. The showrunner wants to recast. The actor's agent (Joel) is threatening to pull the actor from all future projects if you let the showrunner fire them. Choose sides. |

**Difficulty Considerations**:
- **Season 1**: 6 projects in pipeline. Conflicts are rare and clearly telegraphed. Notes are presented one at a time, giving the player time to read and consider. The phase feels like learning a new language.
- **Season 2-3**: 8-10 projects. Conflicts overlap -- two projects need attention simultaneously, forcing the player to prioritize. Notes arrive in batches (2-3 dilemmas per project).
- **Season 4+**: 10-12 projects. Conflicts cascade -- fixing one project creates a problem in another (e.g., pulling budget from Project B to save Project A makes Project B's showrunner unhappy, lowering trust). The player is managing a system, not individual tasks.

**Exit Condition**: All projects have completed development and entered production (all cards have reached the rightmost column: PRODUCTION). The calendar advances to "Pilot Production Complete." The pipeline phase ends when the rough cuts are ready to screen.

---

### 2.4 LEVEL 3: THE SCREENING ROOM (Pilot Review / Spring)

**Purpose Statement**: Teach the player to evaluate creative work under uncertainty. The player learns that test audience data is unreliable, that their own taste is a signal they must learn to trust, and that the greenlight/kill decision is not an optimization -- it is a bet.

**Emotional Beat**: Intimacy and weight. The screening room is quiet, dark, singular. Every rough cut is a moment of truth.

---

**FLOW DIAGRAM (Screening Room Sequence)**:

```
  SCREENING ROOM INTERFACE (full-screen, desk/pipeline hidden)

  [Dark theater seats, empty except for player's seat (front row, center)]
  [Screen shows: "ROUGH CUT -- [Project Name]"]

  PHASE 1: WATCH (30-60 seconds)
  - The player "watches" the rough cut. The game presents this as:
    Option A: Stylized storyboard panels (3-5 key moments from pilot)
    Option B: Text description of key scenes with emotional beats
    Option C: A montage of coverage-style notes: "The opening is electric. The second act drags. The finale either lands or collapses depending on the viewer."

  - During the watch, the player takes notes on a legal pad (optional but encouraged). Notes affect nothing mechanically but reinforce the fantasy.

  PHASE 2: DATA ARRIVES (15 seconds)
  - Test Audience Score: [Number / 100]
  - Demographic Breakdown: 18-34 [Number], 35-49 [Number], 50+ [Number]
  - Sample Comments: 3-4 real audience quotes (mix of positive/negative/confused)

  PHASE 3: DECIDE (player choice, no time limit)
  - GREENLIGHT (commit to series order, allocate series budget)
  - HOLD (request reshoots, re-edits, additional notes -- costs time/money)
  - KILL (cancel project, showrunner relationship damaged, sunk cost)

  The decision is NOT gated. The player can greenlight a pilot with a test score of 38 if they believe in it. The player can kill a pilot with a test score of 72 if they think it is soulless.

  REPEAT for all pilots in the development slate (4-6 pilots per season).
```

**Spatial Focus**: The screening room is the most focused spatial environment in the game. The desk is gone. The pipeline is gone. There is only the screen, the darkness, and the decision. The spatial simplicity creates emotional intensity -- nothing to distract from the weight of the choice.

**Pacing Target**:
- **Length**: 10-15 minutes total (2-3 minutes per pilot)
- **Rhythm**: Slow-fast-slow. SLOW = watching the rough cut (player is absorbing). FAST = data arrives (sudden spike of information). SLOW = decision (player sits with the choice, no timer). The pacing mirrors the real experience of watching a pilot and deciding its fate.

**Breadcrumbing Strategy**:
- **Sequential Structure**: The game presents pilots one at a time. The player cannot skip ahead. This enforces pacing -- the player must sit with each decision before moving to the next.
- **Contrast**: After the player makes a decision on Pilot 1, the game transitions to Pilot 2 with a brief "next screening" interstitial (lights come up briefly, then dim again). The interstitial is a breath. The player is not machine-gunned with decisions.
- **Stakes Preview**: Before the screening room phase begins, the game shows the player a quick overview: "You have 5 pilots to review. You can greenlight 2-4 to series. The rest will be killed." The player knows the constraint going in, which frames every decision as part of a portfolio.

**Encounter Breakdown**:

| Encounter Type | Frequency | What It Tests | Example |
|---|---|---|---|
| **The Sure Thing** | 1 per season | Confidence baseline | Test score 68, solid across all demos, well-crafted, no surprises. Safe greenlight. Establishes the player's commercial floor. |
| **The Divisive Masterpiece** | 1 per season | Courage to trust your taste | Test score 41 overall, but 18-34 demo scored it 76. The comments are either "brilliant" or "unwatchable." Your gut says it is special. Do you bet your career on it? |
| **The Polished Mediocrity** | 1 per season | Recognizing the trap | Test score 64. Showrunner delivered exactly what was asked for. It is competent, castable, safe, and utterly forgettable. Do you greenlight it because it will rate adequately, or kill it because your network does not need more beige? |
| **The Broken Ambition** | 1 per season | Triage under heartbreak | Test score 33. The pilot is a mess -- overstuffed, tonally confused, technically troubled. BUT: there are three scenes in it that are better than anything else you watched today. Can it be saved with reshoots? Or is it a sunk cost? |
| **The Surprise** | 1 per season | Humility | A pilot you did not believe in during development -- maybe you gave too many commercial notes, maybe the showrunner was difficult -- comes back better than expected. Test score 59, but the rough cut has life. Do you greenlight it and admit you were wrong to doubt it? |

**Difficulty Considerations**:
- **Season 1**: The pilots are legible. Quality and test scores are reasonably aligned. The player can trust the data and their gut because both point in the same direction most of the time.
- **Season 2-3**: The alignment breaks. A pilot the player loves tests poorly. A pilot the player thinks is mediocre tests well. The player must decide which signal to trust.
- **Season 4+**: The landscape context matters more than the pilot's intrinsic quality. A serialized drama that would have been a tough sell in Season 2 is now perfectly timed for a landscape where Serialization Appetite has spiked. The player is evaluating pilots relative to a shifting market, not in a vacuum.

**Exit Condition**: All pilots have been evaluated. The player has selected 2-4 for series orders. The rest are killed. The game transitions to the upfronts.

---

### 2.5 LEVEL 4: THE UPFRONTS (Presentation / Early Summer)

**Purpose Statement**: Teach the player that execution matters as much as quality. The player learns that the order of presentation, the framing of each show, and the ability to read the room are skills distinct from creative taste. This is the only "performance" level in the game -- the player is on stage.

**Emotional Beat**: High-stakes theater. The player has built something. Now they must sell it. The weight of eyes on you.

---

**FLOW DIAGRAM (Upfronts as Staged Performance)**:

```
  UPFRONTS VENUE: Carnegie Hall (or similar prestige theater)

  SETUP PHASE (2-3 minutes):

  Backstage interface. The player sees:
  - Their 2-4 greenlit series as cards
  - Presentation order slots: [1] [2] [3] [4]
  - Sell Line options for each show (choose 1 per show):
      Option A: "The next great American drama" (prestige pitch)
      Option B: "18-49 demo magnet" (commercial pitch)
      Option C: "The conversation starter" (cultural pitch)

  The player drags shows into presentation order.
  The player assigns a Sell Line to each show.

  PRESENTATION PHASE (5-7 minutes):

  The player is no longer backstage. The camera is now IN THE THEATER.

  - Richard Kessler (network president) is at the podium. He introduces the slate.
  - Each show is presented in sequence:
      1. Richard reads the Sell Line.
      2. A sizzle reel plays (15-20 second montage of pilot highlights, presented as text + key visual moments).
      3. AD BUYER CONFIDENCE METER (visible on HUD) responds in real-time:
         - Meter fills if: show's Commercial Floor is high, Star Power is visible, Sell Line aligns with ad market preferences
         - Meter drains if: show's Commercial Floor is low, concept is risky, Sell Line overpromises

  - AUDIENCE REACTION (visual feedback):
      - Interested: Buyers lean forward, take notes
      - Skeptical: Buyers lean back, phones come out
      - Excited: Applause (rare, only for a show that truly lands)

  - After all shows are presented, the FINAL AD COMMIT number is calculated:
      Total Ad Revenue = sum of (each show's ad commit based on Confidence Meter performance)

  POST-PRESENTATION (1 minute):

  Backstage. Richard approaches. His reaction depends on the Ad Commit result:
  - Strong commit: "We did it." (relief, pride)
  - Weak commit: "We need to talk." (tension, warning)

  The player sees the final number: "Season Ad Revenue: $XX million."
  This number determines next season's development budget.
```

**Spatial Focus**: The theater. The player is seeing their work from the AUDIENCE perspective for the first time. The spatial shift (from backstage prep to onstage presentation to audience reaction) mirrors the psychological shift from creator to seller to evaluated.

**Pacing Target**:
- **Length**: 8-10 minutes
- **Rhythm**: Anticipation-release-anticipation-release. The SETUP phase is anticipation (the player arranging the deck). Each show's presentation is a release (the player watches the reaction). The final ad commit is the ultimate release -- the number appears, and the player either exhales or tenses.

**Breadcrumbing Strategy**:
- **Meter as Guide**: The Ad Buyer Confidence Meter is the primary breadcrumb. It gives the player immediate feedback on whether a show is landing. If the meter is draining, the player knows the pitch is not working -- but they cannot change it mid-presentation. The meter creates tension (you are watching a plan succeed or fail in real-time) and learning (for next season, the player will remember which pitches worked and which did not).
- **Audience Micro-Reactions**: Small visual tells. A specific buyer's face lights up during the crime drama pitch. Another buyer checks their phone during the sci-fi pitch. The player learns to read the room, even though they cannot act on it in the moment.

**Encounter Breakdown**:

| Encounter Type | What It Tests | Example |
|---|---|---|
| **The Strong Opener** | Presentation order strategy | Do you lead with your safest show (build confidence early) or your best show (make a statement)? |
| **The Risky Closer** | Risk tolerance + showmanship | Do you save your most ambitious show for last (go out on a high note if it lands, or end on a flop if it doesn't)? |
| **The Overpromise** | Honesty vs. salesmanship | Do you pitch a low-Commercial-Floor show as "the next big thing" (raise ad commit now, risk backlash later if it underperforms) or undersell it (leave money on the table but avoid expectations trap)? |
| **The Undersell** | Recognizing hidden value | A show you are uncertain about lands better with the audience than you expected. Do you lean into the surprise or stick with your conservative Sell Line? |

**Difficulty Considerations**:
- **Season 1**: The upfronts are forgiving. Ad buyers are receptive. The Confidence Meter is easy to fill. The player learns the rhythm without high stakes.
- **Season 2-3**: Ad buyers are more skeptical. A mediocre slate generates weak commits. The player feels the economic pressure -- a bad upfronts means a smaller budget next season.
- **Season 4+**: The landscape affects ad buyer preferences. In a season where serialized dramas are hot, pitching a procedural gets muted response even if the procedural is well-made. The player must align their slate with the market zeitgeist OR pitch against it with enough confidence to convince the room.

**Exit Condition**: All shows have been presented. The ad commit number is locked. The game transitions to the season ratings phase.

---

### 2.6 LEVEL 5: THE SEASON (Ratings & Reflection / Fall-Spring)

**Purpose Statement**: Teach the player that launch is not the end -- it is the beginning. The player learns that shows evolve, that mid-season decisions matter, and that the gap between expectation and outcome is where the grief lives.

**Emotional Beat**: Sustained tension with punctuated releases. Each weekly ratings report is a small verdict. The cumulative arc of a show's season is the larger story.

---

**FLOW DIAGRAM (The Season as Temporal Map)**:

```
  THE SEASON CALENDAR (Sept - May, condensed to 8-12 "week" beats in gameplay)

  Each WEEK:

  1. RATINGS ARRIVE (trade magazine headline on desk):
     "[Show Name] draws X.X million viewers, up/down X% from last week"
     "Demo breakdown: 18-49: X.X rating"

  2. PLAYER PROCESSES:
     - Shows performing above expectations: green headline
     - Shows performing at expectations: neutral headline
     - Shows underperforming: red headline

  3. MID-SEASON DECISION POINTS (triggered by thresholds):

     WEEK 3: "Early Ratings Check-In"
     - If a show is underperforming badly, Richard calls: "We need to talk about [Show Name]."
       Player options:
         - STAY THE COURSE (trust the show, ask for patience)
         - SCHEDULE MOVE (shift to a different time slot, risky but might help)
         - CANCEL (cut losses, brutal but economically rational)

     WEEK 6: "Mid-Season Slate Adjustment"
     - If a show is overperforming, player can:
         - EXTEND ORDER (grant additional episodes, costs budget but signals confidence)
         - HOLD STEADY (wait and see)
     - If a slot has opened (due to cancellation), player can:
         - SLOT MIDSEASON REPLACEMENT (a held-back pilot from development)

     WEEK 10: "Endgame"
     - Final ratings trajectories lock.
     - Player makes RENEWAL / CANCELLATION decisions for next season.

  4. NARRATIVE EVENTS (scattered across the season):
     - A showrunner calls to thank you for protecting their vision.
     - A critic's review drops (Martin Scheer's take on one of your shows).
     - A rival network's show becomes a breakout hit (landscape shift).
     - An actor on one of your shows becomes a tabloid story (affects show perception).
```

**Spatial Focus**: The desk returns. Trade magazines pile up on the right zone. Each magazine is a week. The visual accumulation of magazines is the season's progress bar. The player's office changes subtly based on performance (a struggling network's office feels dimmer, a thriving network's office has better light).

**Pacing Target**:
- **Length**: 10-15 minutes
- **Rhythm**: Breath-breath-breath-SPIKE. Most weeks are quiet updates (ratings arrive, player reads, game continues). But 3-4 times per season, a SPIKE happens -- a major decision point, a crisis, a breakout. The rhythm is mostly calm with punctuated drama, mirroring the real experience of running a season (weeks of waiting, then a moment where everything hinges on one choice).

**Breadcrumbing Strategy**:
- **Color-Coded Headlines**: Green = good news, red = bad news, neutral = steady. The player scans the right zone of the desk and immediately knows the week's vibe by color. No need to read every headline closely unless a color catches their eye.
- **Calendar Milestones**: The in-game calendar shows upcoming decision points ("Mid-Season Check-In: Week 6"). The player knows when the spikes are coming and can prepare mentally.
- **Relationship Callbacks**: If the player protected a showrunner's vision during development, and that show is now succeeding, the showrunner sends an email or calls. The narrative breadcrumb reinforces that earlier decisions matter. If the player compromised a showrunner's vision and the show is now failing, the showrunner's silence is its own breadcrumb.

**Encounter Breakdown**:

| Encounter Type | Frequency | What It Tests | Example |
|---|---|---|---|
| **The Grower** | 1 per season | Patience + long-term thinking | A show starts weak (4.2M viewers week 1) but grows slowly (4.8M by week 6). Do you cancel it for underperforming early, or trust the trajectory? |
| **The Disappointment** | 1 per season | Accepting failure | A show you loved, that you fought for, that tested well, launches to 3.1M viewers and bleeds audience weekly. It is not coming back. Do you cancel it quickly (minimize losses) or let it finish its run (honor the creative team)? |
| **The Surprise Hit** | 1 per 2-3 seasons (rare) | Capitalizing on success | A mid-tier pilot you greenlit almost as an afterthought becomes a breakout (12M viewers, strong demo). Do you extend the episode order, promote it heavily, build next season's slate around it? |
| **The Mid-Season Gamble** | 1 per season | Crisis decision-making | A show is dying in a bad time slot (Friday 10pm). Do you move it to a better slot (Thursday 9pm) and displace another show, risking two failures instead of one? |

**Difficulty Considerations**:
- **Season 1**: Ratings are relatively stable. The player's shows perform close to their projected Commercial Floor. Variance is low. The season is a victory lap or a controlled disappointment.
- **Season 2-3**: Variance increases. A show can overperform or underperform by 20-30% relative to projections. The player must react to surprises.
- **Season 4+**: External factors (rival shows, landscape trends, DVR adoption) create unpredictable swings. A show that would have succeeded in Season 2 fails in Season 5 because the landscape shifted. The player must adapt strategies season-over-season.

**Exit Condition**: The season calendar reaches May. All shows have aired their finales (or been cancelled mid-season). The player makes renewal/cancellation decisions. The game displays a season summary: total viewership, total ad revenue, critical response, network brand shifts. The summary screen transitions to "Next Season" or, if this was Season 8, to the Retrospective.

---

## 3. THE NOTES SYSTEM AS MICRO-LEVEL DESIGN

### 3.1 The Challenge

The Notes System is PILOT's unique mechanic -- the moment where the player shapes creative work through editorial feedback. REED has designed it as a branching choice tree (see GDD section 3.3). My job as level designer is to make sure each note feels like a SPACE the player navigates, not a menu they click through.

### 3.2 Notes Interface as Spatial Experience

When the player gives notes on a pilot, the game shifts to the **NOTES ROOM** -- a dedicated interface that isolates the player from the desk/pipeline.

**NOTES ROOM LAYOUT**:

```
  Full-screen interface (desk hidden)

  LEFT HALF: CONTEXT ZONE
  - Pilot script excerpt (the scene/moment the note concerns)
  - Showrunner's creative intention (quoted)
  - Test audience feedback (if available)
  - Relevant network brand / landscape context

  RIGHT HALF: DECISION ZONE
  - The creative dilemma question (authored text, 2-3 sentences)
  - 2-3 response options (each option is 3-4 sentences describing the note and its rationale)
  - Visible immediate effects (Quality Ceiling, Commercial Floor, Showrunner Trust shifts)
  - Hidden long-term consequences (not shown until later)

  BOTTOM: REFLECTION SPACE
  - Legal pad texture (the player can write a note to themselves -- optional, no mechanical effect, pure fantasy)
```

**Spatial Logic**:

The left-to-right flow mirrors the decision process:
1. LEFT = Context. The player reads the situation. Understands the creative stakes.
2. RIGHT = Choice. The player evaluates options. Sees the mechanical trade-offs.
3. BOTTOM = Reflection. The player (optionally) articulates their reasoning, reinforcing the fantasy that this is an editorial conversation, not a stat adjustment.

The Notes Room is SLOW. There is no timer. The player can sit here as long as they want. The pacing is contemplative, which contrasts with the frantic desk triage and the high-stakes upfronts. The Notes Room is where the player breathes and thinks.

### 3.3 Breadcrumbing Within a Note

Each note option includes a **TELLS** -- a small narrative detail that hints at the long-term consequence without spelling it out.

Example:

**Dilemma**: "The showrunner wants the pilot to open with a 10-minute tracking shot that will cost $1.2M."

**Option A: "Protect the shot."**
- Immediate effects: Visual Quality +12, Budget strain on other categories, Showrunner Trust +8.
- **TELL** (embedded in the option text): "The showrunner's eyes light up when you say yes. This is the moment they will remember for the rest of their career."
  - The TELL hints that protecting this shot will deepen the relationship long-term, possibly bringing the showrunner back for future projects.

**Option B: "Cut the shot."**
- Immediate effects: Visual Quality -5, Budget freed, Showrunner Trust -10.
- **TELL**: "The showrunner nods, but their face goes blank. You have seen that look before. It is the look of someone deciding how much they are willing to fight for the next note."
  - The TELL hints that the relationship is now adversarial. Future notes will be harder.

The TELL is the breadcrumb. It does not explain the mechanic. It gives the player a narrative clue about what this choice MEANS beyond the numbers.

---

## 4. PACING CURVES

### 4.1 Single-Session Pacing (One Development Season)

```
  INTENSITY (player attention demand)
    ^
    |
  9 |                                    UPFRONTS
    |                                   /        \
  8 |                                  /          \
    |                        SCREENING ROOM        \___
  7 |                       /                           \
    |                      /                             \
  6 |        PIPELINE    /                                \
    |       /          /                                   \
  5 |      / NOTES   /                                      SEASON
    |     /        /                                       /      \
  4 |    /       /                                        /        \
    |   /      /                                         /          \
  3 | DESK   /                                          /            \
    | /     /                                          /              \
  2 |/     /                                          /                \
    |     /                                          /                  \
  1 |____/                                          /                    \____
    |
    +---------------------------------------------------------------------->
      0    10    20    30    40    50    60    70    80    90   TIME (min)

      DESK  PIPELINE       SCREENING  UPFRONTS      SEASON
            + NOTES          ROOM
```

**Key Beats**:

- **0-12 min (Desk)**: Intensity ramps from calm to controlled frenzy. The script pile grows. The player is learning the rhythm.
- **12-35 min (Pipeline + Notes)**: Sustained moderate-high intensity. The player is juggling simultaneous projects. Notes create intensity spikes within this phase (each note is a 2-3 minute peak).
- **35-50 min (Screening Room)**: Intensity drops slightly (fewer inputs, singular focus) but emotional weight increases. The quiet intensity of watching and judging.
- **50-60 min (Upfronts)**: Sharp intensity spike. This is the climax. The player is performing. The meter is responding. The stakes are highest.
- **60-90 min (Season)**: Gradual decline in intensity. Weeks pass. Ratings arrive. Decisions are spaced out. The player is watching consequences unfold. The intensity spikes briefly at mid-season decision points, then declines to a reflective low at season end.

The curve is a crescendo (Desk -> Pipeline -> Upfronts) followed by a long denouement (Season). The upfronts are the peak. The season is the aftermath. The player feels the shape of the season as a dramatic arc.

### 4.2 Campaign Pacing (8-Season Career)

```
  COMPLEXITY (systems depth + player mastery required)
    ^
    |
  10|                                                    SEASON 8
    |                                                   (LEGACY)
  9 |                                              SEASON 7
    |                                             (ADAPTATION)
  8 |                                        SEASON 6
    |                                       (STRIKE)
  7 |                                 SEASON 5
    |                               (RECKONING)
  6 |                         SEASON 4
    |                        (SQUEEZE)
  5 |                  SEASON 3
    |                (GOLD RUSH)
  4 |          SEASON 2
    |        (VOICE)
  3 |   SEASON 1
    | (NEW JOB)
  2 |
    |
  1 |_______________________________________________________________>
      1    2    3    4    5    6    7    8    SEASON

  EXPAND phases: New mechanics introduced (steps up)
  TEST phases: Landscape shifts pressure existing mastery (difficulty spikes within each plateau)
```

**Seasons 1-2**: Learning curve. The player is acquiring verbs (triage, development, notes, upfronts, season management). Complexity is LOW but rising. The game is teaching.

**Seasons 3-5**: Mastery plateau. The player has the tools. Now the game tests depth. Landscape shifts (serialization boom, DVR disruption, prestige cable pressure) force the player to adapt strategies. Complexity is MODERATE-HIGH and stable. The game is challenging.

**Season 6**: Disruption. The Writers' Strike breaks the rhythm. Complexity SPIKES not because new mechanics are introduced, but because the player's established systems are invalidated. The strike is a difficulty wall that forces reinvention.

**Seasons 7-8**: Endgame. Complexity remains high but the focus shifts from optimization to curation. The player is no longer learning or adapting -- they are defining. Season 8 introduces the Retrospective (a new narrative frame), making the player's relationship with their decisions the final challenge. Complexity is EMOTIONAL rather than mechanical.

The 8-season curve is a ramp that plateaus, disrupts, and then shifts from systemic challenge to existential challenge. The game gets harder by changing the question, not by adding more tasks.

---

## 5. DIFFICULTY VARIANTS

### 5.1 Difficulty as Constraint, Not Punishment

PILOT's difficulty settings should not be "enemies have more HP" -- there are no enemies. Difficulty in PILOT is about **how much margin for error the player has** and **how aggressively the landscape shifts**.

### 5.2 Three Difficulty Modes

| Mode | Target Player | Key Changes |
|---|---|---|
| **STANDARD** (default) | First-time players, TV industry enthusiasts | Forgiving President Patience (starts 60, decays slowly). Generous script expiration timers. Landscape shifts are telegraphed clearly (Industry Signals are unambiguous). Showrunner conflicts are rare in early seasons. The player can make mistakes and recover. |
| **RUTHLESS** (hard mode) | Experienced management sim players, masochists | President Patience starts at 50, decays faster. Script expiration timers are tight (3-4 days always). Landscape shifts are less telegraphed (Industry Signals are ambiguous or contradictory). Showrunner conflicts are frequent. Budget crises trigger more easily. The player must optimize or die. |
| **AUTEUR** (creative mode) | Players who want to build a prestige network without economic punishment | President Patience is locked at 70 (never drops below, rarely pressures player). Development budget is generous and grows regardless of performance. The player is free to chase creative excellence without commercial compromise. The challenge is: can you build something great when survival is not the constraint? |

### 5.3 Accessibility: "Story Mode" Option

For players who want to experience NOVA's narrative and characters without the management challenge:

**STORY MODE**:
- Automated desk triage (scripts are pre-selected for the player, but the player can override).
- Simplified pipeline (projects advance automatically unless flagged for player attention).
- Notes System is preserved (this is the soul of the game, cannot be automated without destroying the fantasy).
- Upfronts are non-interactive (Richard presents, ad commit is always adequate).
- Season ratings are stable (no mid-season crises).

The goal: players who are here for the creative conversations (the Notes System) and the characters (Tommy, Sandra, Joel, Martin) can experience those without drowning in resource management.

---

## 6. PLAYTESTING METRICS

### 6.1 What to Measure

| Metric | What It Tells Us | Target Value | Red Flag Value |
|---|---|---|---|
| **Time to First Priority Decision** | How long before the player commits their first script to development. Measures tutorial clarity. | 2-4 minutes | >6 minutes (player is lost or paralyzed) |
| **Scripts Deep-Read vs. Skimmed** | Player engagement with the triage depth mechanic. | 30-50% deep-read in Season 1, dropping to 15-25% by Season 4 (mastery = efficiency) | >70% deep-read in late seasons (player does not trust pattern recognition) OR <10% deep-read in Season 1 (player is not engaging) |
| **Notes Decision Time** | Average time spent on each creative dilemma. | 45-90 seconds per note | <20 seconds (player is not reading context, treating notes as quiz) OR >3 minutes (analysis paralysis, too much text) |
| **Upfronts Presentation Variance** | How much do players change their presentation order between attempts (in playtests where we allow retries)? | 60%+ change their order on second attempt | <30% change (presentation order feels meaningless) |
| **Season Engagement Drop-off** | Do players disengage during the Season phase (weeks of ratings updates)? | <10% alt-tab / reduced input during Season phase | >30% drop-off (Season phase is boring) |
| **Pipeline Attention Distribution** | What percentage of pipeline projects does the player actively click on vs. let run on autopilot? | 40-60% active clicks (player is prioritizing) | >80% active clicks (Attention Flag system is not working, player feels compelled to micro-manage everything) |
| **Career Completion Rate** | What percentage of playtesters finish all 8 seasons? | >60% in a controlled playtest | <40% (late-game stagnation or difficulty wall) |
| **Retrospective Watch Rate** | Do players watch the full Season 8 retrospective, or skip it? | >70% watch to completion | <40% watch (ending is not satisfying) |

### 6.2 Qualitative Playtest Questions

After each session, ask:

1. "What was the hardest decision you made this session?" (Tests whether the Notes System is creating genuine dilemmas.)
2. "Did you feel overwhelmed at any point? When?" (Identifies pacing/complexity spikes that need smoothing.)
3. "Did you feel bored at any point? When?" (Identifies pacing valleys that need compression or tension injection.)
4. "Which showrunner/character did you care most about? Why?" (Tests character investment.)
5. "Can you describe your network's identity in 2-3 sentences?" (Tests whether the Network Brand system is legible and emergent.)
6. "If you could redo one decision, what would it be?" (Tests regret mechanics -- healthy regret means stakes are real.)
7. "Did you understand why [specific pilot] succeeded or failed?" (Tests feedback clarity on the ratings/consequences layer.)

---

## 7. ENCOUNTER DESIGN PRINCIPLES

### 7.1 Every Encounter Teaches or Tests

An encounter is any moment where the player makes a decision under constraint. In PILOT, encounters are:
- Triaging a script with an expiring clock
- Choosing a showrunner for a mismatched project
- Giving a note that pits commerce vs. art
- Deciding whether to cancel a struggling show mid-season

Every encounter must either TEACH a concept (early game) or TEST mastery of that concept (late game). No encounter should be filler.

**Example (Teaching Encounter -- Season 1, Desk Phase)**:

The player's first "Hidden Gem" script arrives. Coverage grade: C+. Logline: compelling but strange. Blind-spot indicator: "Reader may be underrating this due to unfamiliarity with the genre."

The encounter teaches: **coverage grades are fallible. Blind-spot indicators are signal. Deep reading is sometimes worth the Time Token cost.**

The player who deep-reads discovers the script is actually a B+ or A-. The player who skims or passes misses it. The next day, if the player passed, a headline appears: "Rival network greenlights [logline]." The player feels the sting of the miss.

**Example (Testing Encounter -- Season 4, Notes Phase)**:

The player is giving notes on a serialized drama. The showrunner (Tommy Morell, high Ego, high Vision) has written a protagonist with zero redemption arc. Test audience hates the character. Network president wants the character softened.

The encounter tests: **Can the player navigate a three-way tension (showrunner vision, audience data, boss pressure) and make a choice they can defend?**

There is no right answer. Protecting Tommy's vision risks commercial failure but deepens trust. Mandating a redemption arc ensures mediocrity but appeases Richard. The test is whether the player has developed a strategic framework (does my network prioritize creative relationships or short-term ratings?) and the courage to execute it.

### 7.2 Difficulty Curves Within Encounters

Even a single note (a single encounter) has an internal difficulty curve:

**EASY NOTE**: Clear trade-off. Two options, both viable in different contexts. Mechanical effects are visible and intuitive.

**MODERATE NOTE**: Three options, each with hidden consequences. The player must consider not just this pilot, but their network brand and their relationship with the showrunner.

**HARD NOTE**: Four options, or two options with cascading consequences that affect other projects. The player is managing a system, not an isolated decision.

The game should mix difficulty within each session. Not every note is hard. Not every note is easy. The rhythm is EASY-EASY-HARD-EASY-MODERATE-HARD. The player gets breathing room between the difficult calls.

---

## 8. ENVIRONMENTAL STORYTELLING & VISUAL BREADCRUMBS

### 8.1 The Office as Character

The player's office is not static. It evolves based on the player's status and choices.

**Season 1 Office**:
- Small window, partial skyline view
- Desk is tidy at the start, becomes cluttered by mid-season
- No personal items yet (the player is new)
- Walls are bare except for a generic motivational poster the previous exec left behind

**Season 3 Office (if player is succeeding)**:
- Larger office, better view
- Framed poster of the network's first hit show (one the player greenlit)
- The desk has accumulated personal touches (a photo, a memento)
- Post-it notes on the monitor: reminders from showrunners ("Thanks for believing in the show - Tommy")

**Season 3 Office (if player is struggling)**:
- Same office (no promotion)
- The script pile is taller, more oppressive
- Trade magazine headlines are increasingly critical
- The light from the window is dimmer (subtle color grading shift toward cooler tones)

**Season 6 Office (post-Strike)**:
- Sparse. The desk is almost empty (no development happening during the strike).
- A single script sits in the center, isolated.
- The screening room is dark (no pilots to watch).
- The emptiness is eerie. The player FEELS the strike as spatial absence.

**Season 8 Office (final season)**:
- The walls are covered in memories: posters, framed reviews, photos of showrunners and casts.
- The desk has 8 years of accumulation: coffee mug stains, a worn legal pad, old Post-its that were never removed.
- The office is a scrapbook of the player's career. Looking at it is the game's version of a "photo mode."

The office tells the story of the player's journey without a single line of dialogue.

### 8.2 The Corkboard: Industry Signals as Spatial Clues

The corkboard on the player's wall displays **Industry Signals** -- trade magazine clippings, Nielsen reports, memos from the president. These are the breadcrumbs for the Landscape simulation.

**Visual Hierarchy**:
- **Red pushpins** = urgent signals (major industry events, immediate threats)
- **Yellow pushpins** = trends to watch (gradual shifts, 2-3 season horizon)
- **Green pushpins** = opportunities (new talent available, genre shifts in the player's favor)

The player glances at the corkboard and immediately knows the industry's temperature by the color distribution. A board covered in red pins = crisis season (Season 6, the Strike). A board with mostly green pins = opportunity season (Season 3, the Serialization Boom).

The corkboard updates automatically each week during the Season phase. New clippings appear. Old ones are moved to the edges or removed. The corkboard is a living document.

### 8.3 The Dead Pilots Drawer

When the player kills a pilot at the upfronts, the pilot's index card is dragged to a drawer at the bottom of the pipeline whiteboard. The drawer is labeled "Dead Pilots."

The drawer stays visible. It accumulates. By Season 8, the player has killed 30-50 pilots. The drawer is full.

The player can open the drawer and see all the pilots they killed. Each card shows:
- Pilot name
- Showrunner
- Why it was killed (test score, budget, strategic fit)
- A "What If" button

Clicking "What If" shows a brief speculative text: "If you had greenlit this, critics estimate it would have drawn 5.2M viewers and run for 2 seasons. The showrunner never worked in television again."

The Dead Pilots Drawer is a graveyard. It is the game's memento mori. It says: every choice has a cost. Every greenlight is also a cancellation of something else.

---

## 9. FINAL THOUGHTS: WHAT MAKES A GREAT "LEVEL" IN PILOT

A great level in a traditional game teaches the player a concept, tests their mastery, and creates a memorable moment. PILOT has no traditional levels, but the principles hold:

**The Desk TEACHES**: Triage under pressure. Pattern recognition. Information scarcity.

**The Pipeline TESTS**: Resource allocation. Multi-variable optimization. Strategic thinking.

**The Notes System CREATES MEMORABLE MOMENTS**: The player gives a note that protects a showrunner's vision against all commercial logic, and that show becomes a masterpiece. Or: the player gives a note that guts a pilot to chase ratings, and the showrunner walks, and the player thinks about it for the rest of the campaign. Those moments are PILOT's equivalent of "I jumped the gap" or "I beat the boss." They are the stories the player tells.

**The Upfronts IS THE BOSS FIGHT**: High stakes, performance pressure, real-time feedback, a clear win/lose state (the ad commit number).

**The Season IS THE AFTERMATH**: The player watches their decisions unfold in slow motion, makes corrections mid-flight, and sits with the consequences.

Where does the player LOOK? At the desk when they need grounding. At the pipeline when they need strategy. At the screening room when they need to judge. At the upfronts stage when they need to sell. At the trade headlines when they need to know how the world sees them.

Every space has a purpose. Every flow path has pacing. Every breadcrumb is a question the player must answer.

That is level design. Not corridors and sightlines. Attention and meaning.

Build the desk. Build the pipeline. Build the room where the player sits alone and watches a rough cut and decides whether to bet their career on it.

Build the spaces where taste becomes a verb.

-- GRID

---

## APPENDIX A: LEVEL PURPOSE SUMMARY TABLE

| Level (Phase) | Purpose | Player Learns/Tests | Emotional Beat | Duration |
|---|---|---|---|---|
| **DESK** | Triage | Information scarcity, pattern recognition, risk tolerance | Controlled overwhelm | 8-12 min |
| **PIPELINE** | Development | Resource allocation, showrunner fit, portfolio strategy | Controlled complexity | 20-30 min |
| **NOTES** | Creative Shaping | Taste as mechanic, compromise navigation, relationship management | Intimacy and weight | 5-10 min (distributed across pipeline) |
| **SCREENING ROOM** | Evaluation | Trusting your taste vs. trusting data, portfolio selection | Quiet tension | 10-15 min |
| **UPFRONTS** | Presentation | Performance, framing, reading the room | High-stakes theater | 8-10 min |
| **SEASON** | Consequence | Patience, mid-season adaptation, acceptance of outcomes | Sustained tension + reflection | 10-15 min |

**Total Session Length**: 61-92 minutes. Target sweet spot: 75 minutes.

---

## APPENDIX B: KEY METRICS TO TRACK IN PLAYTESTING

1. Desk Phase:
   - Average scripts per minute triaged
   - Deep read usage rate (should decline over seasons as mastery increases)
   - Priority selection distribution (are players picking 6? 10? 15? Too few = timid, too many = no prioritization)

2. Pipeline Phase:
   - Projects flagged for attention vs. projects on autopilot (target: 40-60% active)
   - Average time per note decision (target: 45-90 seconds)
   - Showrunner Trust distribution by end of development (are players burning relationships or building them?)

3. Screening Room:
   - Greenlight rate (target: 40-60% of pilots go to series)
   - Alignment between player's greenlight choices and test scores (low alignment = player is trusting taste over data, which is GOOD)

4. Upfronts:
   - Presentation order variance between attempts (if players replay)
   - Ad Commit satisfaction (do players feel the upfronts mattered?)

5. Season:
   - Mid-season cancellation rate (target: 10-20% of shows cancelled before finale)
   - Engagement during weekly ratings (are players alt-tabbing or staying present?)

6. Campaign:
   - Season completion rate (target: >60% finish all 8 seasons)
   - Retrospective engagement (target: >70% watch full retrospective)

---

*Where does the player look? What's the sightline? Where's the breadcrumb? Those are the questions. Every space is a lesson. Every flow path is pacing. Build the desk. Build the trust. Build the moment where the player hovers the cursor over GREENLIGHT and KILL and hesitates. That hesitation is the level. That hesitation is everything.*
