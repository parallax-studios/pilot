# PILOT -- Game Design Document

**Author**: REED (Game Designer)
**Version**: 1.0
**Date**: 2026-02-07
**Status**: Complete First Pass -- Ready for Playtest Planning

---

> "A game is its loop. If the 30-second experience isn't compelling, no amount of content saves it."

I have read the pitch. I know what this game wants to be -- a television development sim where taste is the mechanic, every greenlight is a gamble, and the golden age of TV is yours to build or botch. Now let me tell you what it *is*. Mechanically. Systemically. Down to the numbers.

Every section here answers the same question I ask of every design: **what's the loop, where's the depth, and does this hold up at hour 20?**

No placeholders. No "TBD." No "we'll figure out the fun later." If something is in this document, it is implementable. If something is not in this document, it is a conscious cut.

Let's find the fun.

---

## 1. PLAYER FANTASY STATEMENT

**"I am the person who decides what America watches -- the gatekeeper between a brilliant script and the 20 million people who might never see it -- and every show that reaches the screen bears the fingerprints of my taste, my courage, and my compromises."**

That is the fantasy. Not "I run a television network." Not "I manage a content pipeline." The fantasy is *creative authority in an industry that rewards cowardice*. The player wants to feel what every real development executive has felt: the terror of greenlighting something nobody has seen before. The sick thrill when the pilot dailies come in and the show is alive. The hollow reckoning when you kill something beautiful because the numbers say you must.

Every system in this game must serve that fantasy. If a mechanic does not create, heighten, or resolve the tension between creative vision and commercial survival, it does not belong. That is the filter. That is the north star. The player's verb is not MANAGE. The player's verb is TASTE.

---

## 2. CORE LOOP

### 2.1 The 30-Second Loop: Read, Triage, Decide

A script lands on the desk. The player scans the coverage sheet -- logline, genre tag, reader's grade, talent attachments, blind-spot indicators. They make a gut call: **PASS**, **CONSIDER**, or **PRIORITY**. Every script has a ticking clock; leave it in the pile too long and a rival network grabs it. The cycle takes 15-30 seconds of active decision-making.

The feel is a card-evaluation game under information scarcity. You never have time to deep-read everything. Your instincts matter as much as your analysis. The tension is in the gap between what the coverage tells you and what the coverage misses. A C+ script from a first-time writer with no attachments might be The Wire. An A- script from a proven showrunner might be a paint-by-numbers procedural. The desk teaches you to distrust surfaces.

### 2.2 The 5-Minute Loop: Develop a Pilot

A prioritized script enters the development pipeline. Over 4-6 minutes of real time, the player:

1. **Attaches a Showrunner** (45 sec) -- Each has stats, tendencies, ego, creative vision. Some mesh with the material, some clash.
2. **Negotiates Casting** (45 sec) -- Star power vs. budget vs. artistic fit. The perfect actor costs too much. The cheap actor is wrong but the showrunner loves them.
3. **Gives Notes** (90-120 sec) -- The soul of the game. Specific creative dilemmas that nudge the pilot along axes of commercial viability vs. artistic integrity.
4. **Allocates Production Budget** (30 sec) -- A zero-sum puzzle across production categories.
5. **Reviews the Rough Cut** (30-60 sec) -- The pilot's qualities crystallize. Test audience data arrives. The final greenlight/kill decision looms.

This is the heartbeat. Each pilot is a self-contained dramatic arc. If this loop is not satisfying on its own, the game fails. No amount of industry simulation saves a broken 5-minute loop. I learned that the hard way.

### 2.3 The Meta Loop: The Development Season

A full development season is one session (45-90 minutes). The season structures long-term decision-making:

- **Fall (Pitch Season)**: 15-20 scripts arrive on the desk. Triage aggressively. Select 8-12 for development. The rest go to competitors. This is the intake funnel -- the quality of your raw material.
- **Winter (Development)**: Pipeline management. Attach showrunners, negotiate casting, give notes. 8-12 projects in simultaneous development. Budget allocation across the slate.
- **Spring (Pilot Production)**: 4-6 projects receive pilot orders. Production budgets lock. Pilots shoot. Rough cuts arrive. Test audience data trickles in. The gut-check period.
- **Early Summer (The Upfronts)**: The climax. You stand before advertisers and present your slate. 2-4 pilots go to series. The rest die. Your selections define next fall's schedule. Ad revenue commits based on your presentation.
- **Fall-Spring (The Season)**: Your series air. Weekly ratings arrive. Mid-season decisions -- renew the struggling show? Cancel the creative darling? Adjust the schedule? Your reputation updates. Your budget for next season adjusts.

### 2.4 Core Loop Diagram

```
                    +-----------+
                    |  SCRIPTS  |
                    |  ARRIVE   |
                    +-----+-----+
                          |
                          v
                    +-----+-----+
                    |   DESK    |
                    |  TRIAGE   |----> [PASS] (script gone)
                    +-----+-----+----> [CONSIDER] (hold pile, clock ticking)
                          |
                          | [PRIORITY]
                          v
              +-----------+-----------+
              |   DEVELOPMENT PIPELINE |
              |  Showrunner + Cast +   |
              |  Notes + Budget        |
              +-----------+-----------+
                          |
                          v
                    +-----+-----+
                    |   PILOT   |
                    | PRODUCTION|
                    +-----+-----+
                          |
                          v
                    +-----+-----+
                    |  ROUGH CUT |
                    |  + TEST    |
                    |  AUDIENCE  |
                    +-----+-----+
                          |
                +---------+---------+
                |                   |
                v                   v
         [GO TO SERIES]       [KILLED]
                |                   |
                v                   v
         +------+------+    +------+------+
         |  UPFRONTS   |    | REPUTATION  |
         | PRESENTATION|    |   SHIFT     |
         +------+------+    +-------------+
                |
                v
         +------+------+
         |   SEASON    |
         |   RATINGS   |----> Weekly viewership, demo shares, critical response
         +------+------+
                |
                v
         +------+------+
         |  METRICS    |----> Network Brand / Budget / Reputation / Talent Pool
         |  UPDATE     |
         +------+------+
                |
                v
         +------+------+
         | NEXT SEASON |
         | NEW SCRIPTS |
         +-------------+
```

The loop feeds itself: better reputation attracts better scripts and better showrunners. A stronger brand identity attracts scripts that fit your network's voice. Higher ratings generate more ad revenue which funds more ambitious pilots. The player spirals upward in complexity, not just difficulty. That is the difference between a treadmill and a growth curve.

How does this feel at hour 20? At hour 20, you are not reading coverage anymore -- you are reading the *industry*. You know that serialized dramas are trending upward but the ad market has not caught up yet. You know showrunner X delivers on time but plays it safe, while showrunner Y is a nightmare to manage but might make something transcendent. You have developed an aesthetic identity for your network -- and now the game is about whether you double down on that identity or chase the trend. The early game is about picking good scripts. The mid-game is about building a slate. The late game is about defining an era.

---

## 3. CORE MECHANICS

### 3.1 Script Triage / The Desk

**Player Verb**: READ, EVALUATE, DECIDE

**System Description**: The desk is the hub interface. Scripts arrive as physical document objects with coverage sheets attached. Each script has the following parameters:

| Parameter | Range | Example |
|---|---|---|
| **Logline** | Authored text, 1-2 sentences | "A high school chemistry teacher diagnosed with cancer turns to manufacturing meth." |
| **Genre Tag** | 8 types (see below) | "Serialized Drama" |
| **Reader's Grade** | C+ through A | B+ |
| **Talent Attachments** | 0-2 showrunner/actor names | "Attached: David Chase-archetype showrunner" |
| **Blind-Spot Indicators** | 0-2 flags noting what coverage might miss | "Reader note: may skew too dark for broadcast" |
| **Expiration Clock** | 3-7 in-game days | 5 days |
| **Origin** | Spec script, pitch, adaptation, returning creator | "Spec from unknown writer" |
| **Hidden Quality Variance** | +/- 0-20 from Reader's Grade | +12 (coverage underrates it) |

**Genre Tags** (8 total):
1. **Procedural Drama** -- Case-of-the-week. Reliable ratings floor, low prestige ceiling. CSI, Law & Order territory.
2. **Serialized Drama** -- Continuous narrative. High prestige ceiling, volatile ratings. Sopranos, Lost territory.
3. **Workplace Comedy** -- Ensemble, setting-driven humor. Moderate ratings, moderate prestige. The Office territory.
4. **Family Sitcom** -- Multi-camera, broad humor. High ratings floor, low prestige ceiling. Everybody Loves Raymond territory.
5. **Prestige Limited** -- Short-run, event television. Very high prestige, very uncertain ratings. Band of Brothers territory.
6. **Sci-Fi/Fantasy** -- Genre fiction. Massive hit potential, massive flop potential. Lost, Battlestar territory.
7. **Reality/Unscripted** -- Cheap to produce, unpredictable cultural footprint. Survivor, American Idol territory.
8. **Dramedy** -- Tone-hybrid. Hard to market, loved by critics. Ally McBeal, Desperate Housewives territory.

**Reading Depth**: The player has three triage options:

- **Skim** (5 seconds): See logline, genre, reader's grade, and attachments only. Fast. Risky. Hidden Quality Variance stays hidden.
- **Standard Read** (15 seconds): See everything above plus blind-spot indicators and a partial quality reveal (Hidden Quality Variance narrowed to +/- 10). The default.
- **Deep Read** (30 seconds, costs 1 Time Token per day -- player gets 3 Time Tokens): Full quality reveal. Hidden Quality Variance exposed. Also reveals a "Notes Preview" -- a glimpse of what creative dilemmas will emerge in development. The expensive but safe option.

**Time Tokens per day**: 3. Replenished daily. A typical pitch season delivers 3-5 scripts per day over 4-5 days. The player physically cannot deep-read everything. The math is intentional. Triage is about managing information scarcity, not eliminating it.

**Feedback**: Scripts stack on the desk physically. The pile grows. Coverage sheets have coffee rings, highlighter marks, handwritten margin notes from the reader. The expiration clock appears as a date stamped in red -- scripts close to expiring have the date circled aggressively. When a script expires, it physically slides off the desk and a notification reads: "[Network rival] picked up [logline]." If that script later becomes a hit on a rival network, the player sees a headline about it. The desk punishes inaction.

**Depth**: At hour 1, the player reads coverage grades and picks the highest numbers. At hour 20, the player reads blind-spot indicators, cross-references genre trends with their network brand, estimates whether a C+ from a conservative reader might be a hidden A- for a challenging concept, and factors in showrunner availability before committing a priority slot. The desk rewards pattern recognition, industry knowledge, and the courage to trust a hunch over a grade. The player who always picks the safe A- procedural builds a mediocre network. The player who learns to read between the lines of coverage finds the masterpieces.

---

### 3.2 The Development Pipeline

**Player Verb**: ASSEMBLE, ALLOCATE, SHAPE

**System Description**: Once a script is prioritized, it enters the development pipeline. The pipeline tracks 8-12 simultaneous projects across four development phases: Showrunner Attachment, Casting, Notes, and Pilot Production. Each project is visualized as an index card on a physical whiteboard, moving left to right through the phases.

**Showrunner Attachment**: Each showrunner is a character with six stats rated 1-10:

| Stat | Effect on Pilot | Effect on Process |
|---|---|---|
| **Vision** | Raises Quality Ceiling of the pilot | High-Vision showrunners resist commercial notes |
| **Craft** | Raises Quality Floor -- consistent, polished output | High-Craft showrunners are slow but reliable |
| **Heat** | Industry buzz; attracts better cast, higher ad interest | Heat decays 10% per season without a hit |
| **Ego** | Increases Quality Ceiling but also increases variance | Ego > 7: may ignore notes. Ego > 9: may publicly clash with the network |
| **Reliability** | On-time, on-budget production | Low Reliability risks budget overruns (cost +10-30%) and production delays |
| **Loyalty** | Willingness to stay at your network for future projects | Low-Loyalty showrunners leave after 1 project. High-Loyalty become franchise assets |

**Material-Showrunner Fit**: Each script has a tonal profile (dark-light, serialized-episodic, character-plot, intimate-epic). Each showrunner has a creative preference across these same axes. Fit is calculated as:

```
Fit Score = 100 - (Sum of absolute differences across 4 axes * 5)
```

Where each axis ranges 1-10. Perfect alignment = 100. Maximum misalignment = 100 - (9*4*5) = -80, clamped to 0.

| Fit Score | Effect |
|---|---|
| 80-100 (Synergy) | Quality Ceiling +15. Showrunner Ego effectively -2 for notes compliance. |
| 50-79 (Workable) | No modifier. Standard development. |
| 25-49 (Tension) | Quality Ceiling -10. Showrunner Ego effectively +2. But: 20% chance of "creative friction breakthrough" -- a random quality spike of +20. |
| 0-24 (Mismatch) | Quality Ceiling -25. Showrunner may demand script rewrites that cost time and money. 30% chance showrunner walks off the project entirely. |

The expert player does not always seek Synergy. A Tension pairing with a volatile genius on the right material can produce a breakthrough that a safe Synergy pairing never reaches. Engineering productive friction is an advanced strategy.

**Casting**: Each pilot has 1-3 casting slots. For each slot, the player chooses from 3-4 available actors:

| Actor Attribute | Range | Effect |
|---|---|---|
| **Star Power** | 1-10 | Raises pilot's commercial floor. Each point of Star Power = +2 to Ratings Floor. |
| **Talent** | 1-10 | Raises pilot's quality ceiling. Each point of Talent = +1.5 to Quality Ceiling. |
| **Salary Demand** | $50K-$500K per episode | Directly impacts production budget |
| **Range** | Narrow / Moderate / Wide | Narrow actors in mismatched roles: -15 quality. Wide actors adapt to anything. |
| **Showrunner Chemistry** | -10 to +10 per specific showrunner | Pre-set relationships. Some actors and showrunners have history. |

The casting tension: the affordable unknown with high Talent but zero Star Power, or the expensive star whose name guarantees a certain ratings floor but whose salary starves the production budget? Every casting choice is a resource allocation problem and a creative bet.

**Production Budget Allocation**: The pilot production budget (ranging from $2M-$8M based on network resources and project priority) is distributed across five categories:

| Category | What It Affects | Diminishing Returns Above |
|---|---|---|
| **Writing Room** | Script Quality +2 per 5% allocated. Reduces "unforced error" risk. | 30% |
| **Production Design** | Visual Quality +2 per 5%. Sets the pilot's visual identity. | 30% |
| **Directing/Cinematography** | Visual Quality +1.5, Emotional Impact +1 per 5%. | 35% |
| **Post-Production** | Polish +2 per 5%. Fixes problems, but cannot create quality that was not shot. | 25% |
| **Marketing/Screener** | No quality effect. Increases Test Audience sample size and Upfronts presentation impact by +3 per 5%. | 20% |

**Feedback**: The whiteboard pipeline is the central strategic interface. Index cards are color-coded by genre. Cards in trouble (over-budget, showrunner conflict, casting delays) get red corner flags. Cards on track get green. The player drags cards between phases manually, reinforcing the physical, tactile feel. When a project is killed, the player drags the card to a "dead pilots" drawer -- and that drawer stays visible all season, a graveyard of might-have-beens.

**Depth**: At hour 1, the pipeline is a staffing exercise -- put the best people on the best scripts. At hour 20, it is a portfolio optimization problem. The player balances their slate across risk profiles: two safe procedurals to keep the lights on, one expensive prestige swing for brand-building, one mid-budget genre play that could break out, one cheap dark horse that is either genius or garbage. The pipeline is where strategic thinking meets creative instinct. The player who treats every project identically -- same budget split, same safe showrunner choice -- gets a mediocre slate. The player who differentiates their portfolio gets the upside variance that builds a network.

---

### 3.3 The Notes System

**Player Verb**: SHAPE, DEFEND, COMPROMISE

This is the soul of the game. Let me be precise about how it works, because if this mechanic does not land, nothing else matters.

**Structure**: At two points during development -- once after showrunner attachment (Early Notes) and once after rough cut screening (Final Notes) -- the player is presented with 2-4 **Creative Dilemmas** per pilot. Each dilemma is a specific, authored creative decision with 2-3 response options. No abstractions. No sliders. Concrete choices about the work.

**Creative Dilemma Anatomy**:

Each dilemma has:
- **Context**: A paragraph describing the creative situation -- what the showrunner wants, what the material demands, what the market suggests.
- **Options**: 2-3 responses, each with visible immediate effects and hidden long-term consequences.
- **Axis Impact**: Each option nudges the pilot along 1-2 of the four creative axes (see Network Identity, section 3.4).
- **Relationship Impact**: Each option affects your relationship with the showrunner, the cast, and/or the network president.

**Concrete Examples**:

**Dilemma: "The Antihero Question"**
> *Context*: The showrunner's pilot script features a protagonist who is a corrupt police detective. In the current draft, the character is magnetic but genuinely reprehensible -- no redeeming speech, no secret heart of gold. The showrunner insists this is the point. Your test audience data shows that 62% of viewers rated the protagonist "unlikeable" and 34% said they would not watch a second episode. The network president has been asking about "rootable characters" in every meeting this month.

- **Option A: "Protect the vision."** No notes on the character. Quality Ceiling +5, Commercial Floor -8. Showrunner Trust +10. Network President Trust -5. Axis push: Prestige +3, Risk-Taking +2.

- **Option B: "Add one humanizing scene."** Note the showrunner to add a single scene -- maybe the detective visits his dying mother, maybe he mentors a young cop -- that gives the audience a handhold without gutting the concept. Quality Ceiling -2, Commercial Floor +5. Showrunner Trust -3 (they will feel the note but accept it). Network President Trust +3. Axis push: no significant shift -- this is the centrist play.

- **Option C: "Mandate a redemption arc."** Tell the showrunner the character needs to evolve toward heroism by mid-season. Quality Ceiling -12, Commercial Floor +10. Showrunner Trust -15 (they may become adversarial for the rest of development). Network President Trust +8. Axis push: Populist +4, Safe +3.

**Dilemma: "The Expensive Shot"**
> *Context*: The pilot script for a political thriller opens with a seven-minute tracking shot through the West Wing -- characters moving through rooms, conversations overlapping, the camera never cutting. The showrunner says this shot establishes the show's visual identity and separates it from every other DC drama. Your line producer estimates the shot will cost $1.2M -- roughly 20% of the entire pilot budget -- and may require 3 days of shooting for a single sequence. Cutting it and using standard coverage would save $900K.

- **Option A: "Protect the shot."** Allocate the budget. Visual Quality +12. Budget strain: remaining categories each lose 5% effectiveness. Showrunner Trust +8. Industry Reputation +3 (word gets around that your network supports ambition). Axis push: Risk-Taking +3, Auteur-Driven +2.

- **Option B: "Negotiate a compromise."** Ask the showrunner to achieve the same feel in a 3-minute tracking shot -- still ambitious, but at $600K instead of $1.2M. Visual Quality +6. Budget strain: reduced. Showrunner Trust +2 (they respect the effort to find middle ground). Axis push: slight Auteur-Driven +1.

- **Option C: "Cut the shot."** Standard coverage. Save $900K. Visual Quality -5 (the opening now looks like every other drama). Showrunner Trust -10. Budget freed for other pilots. Axis push: Safe +2, Producer-Driven +2.

**Dilemma: "The Test Audience Problem"**
> *Context*: Your sci-fi drama pilot used a non-linear structure -- the story jumps between three timelines, converging in the final act. Test audience scores: Overall 38/100. "Confusing" was the #1 audience comment. BUT: the 18-34 demographic scored it 71/100, and the open-ended comments from that segment include "best pilot I've seen in years" and "finally something that doesn't treat me like I'm stupid." The network president wants a linear re-edit. The showrunner says a linear version would "gut the entire point."

- **Option A: "Trust the young demo."** No re-edit. Overall Test Score remains 38, but the show launches targeting 18-34 aggressively. Ratings Floor is low but the ceiling with that demo is very high. Showrunner Trust +12. Network President Trust -10. Axis push: Risk-Taking +4, Prestige +2.

- **Option B: "Hybrid re-edit."** Keep the non-linear structure but add brief title cards ("Six Months Earlier," "Present Day") to orient casual viewers. Test Score projected to rise to 52. Showrunner Trust -5 (they see title cards as hand-holding). Network President Trust +5. A genuine compromise that might actually work. Axis push: minimal shift.

- **Option C: "Linear re-edit."** Mandate the re-edit. Test Score projected to rise to 61. Showrunner Trust -20 (relationship may be irrecoverable). Network President Trust +10. The show becomes more accessible and less distinctive. Axis push: Populist +3, Safe +3.

**Dilemma: "The Love Triangle"**
> *Context*: Your workplace drama is a sharp, ensemble-driven show about a failing newspaper. The showrunner has deliberately avoided romantic subplots, arguing that the show is about professional identity, not personal relationships. The network's research department has flagged that the 18-49 female demo -- your weakest segment -- responds strongly to romantic tension in workplace settings. Adding a love triangle between the editor, a reporter, and a rival journalist would likely boost the demo by 15-20%. The showrunner has said, in a meeting your assistant relayed to you, "If they make me add a love triangle, I'm walking."

- **Option A: "No love triangle."** Respect the showrunner's vision. Demo weakness persists. Showrunner Trust +15. Quality Ceiling +3 (the show stays focused). Commercial Floor -5. Axis push: Auteur-Driven +3, Prestige +1.

- **Option B: "Suggest romantic tension, not a love triangle."** Ask for subtle, unresolved chemistry between two characters -- no triangle, no plot arc, just subtext. Showrunner Trust -2 (they will eye-roll but comply). Demo boost: +8% instead of +20%. Quality Ceiling +0. A soft middle path. Axis push: minimal.

- **Option C: "Mandate the love triangle."** Overrule the showrunner. Demo boost: +18%. Showrunner Trust -25. 40% chance the showrunner walks (if they walk, a replacement showrunner with -3 Vision takes over). Quality Ceiling -8. The show becomes more conventional. Axis push: Populist +4, Producer-Driven +3.

**Notes System Resolution**: Every note the player gives adjusts four outputs:

1. **Quality Ceiling** -- the maximum quality the pilot can achieve under ideal conditions.
2. **Commercial Floor** -- the minimum audience the pilot will attract regardless of quality.
3. **Showrunner Trust** -- the showrunner's willingness to collaborate, which affects future note compliance and their likelihood of returning for future projects.
4. **Network Brand Axes** -- cumulative shifts to the network's identity (see 3.4).

**Depth**: At hour 1, the Notes System presents interesting story choices. At hour 20, it is a multi-variable optimization puzzle. The expert player reads each dilemma and calculates: what does this pilot need to survive the upfronts? Is this a show that lives or dies on critical acclaim (protect Quality Ceiling) or on ratings (raise Commercial Floor)? Will this showrunner come back with something better next year if I protect their vision now (long-term Showrunner Trust investment)? Does my network brand need a Prestige push or a Populist correction this season?

The mastery is learning which battles to fight and which to concede. A network that gives zero commercial notes builds a slate of brilliant shows that nobody watches. A network that gives only commercial notes builds a slate of forgettable shows that rate adequately and then die. The sweet spot -- the hard, expert-level sweet spot -- is knowing WHICH note to give on WHICH pilot for WHICH strategic reason. That is taste as a mechanical input.

---

### 3.4 Network Identity / The Brand

**Player Verb**: DEFINE (emergently, through accumulated decisions)

**System Description**: The player's network identity is tracked across four axes, each a spectrum from 0 to 100:

| Axis | Low End (0-30) | Mid (31-69) | High End (70-100) |
|---|---|---|---|
| **Prestige <-> Populist** | Award-bait, small-audience, culturally significant | Balanced | Mass-market, big-audience, crowd-pleasing |
| **Risk-Taking <-> Safe** | Bold swings, frequent failures, occasional transcendence | Moderate risk | Reliable, predictable, few surprises |
| **Auteur-Driven <-> Producer-Driven** | Showrunner is king, network defers to creative vision | Collaborative | Network controls the product, showrunners are interchangeable |
| **Serialized <-> Episodic** | Continuous narratives, demanding viewer commitment | Mixed slate | Stand-alone episodes, casual-friendly, easy to join mid-season |

Each axis starts at 50 (neutral). Every note, every greenlight, every cancellation nudges axes by 1-5 points. The shifts are small per decision but compound over seasons. By season 3, the network has a visible profile.

**Brand Effects**:

| Brand Profile | Mechanical Consequence |
|---|---|
| High Prestige (70+) | +20% chance of attracting high-Vision showrunners. Critics review your shows more favorably (+5 to critical score). Advertisers pay 10% less (prestige audiences are smaller). |
| High Populist (70+) | +20% Ratings Floor on all shows. Advertisers pay 15% premium. High-Vision showrunners are 30% less likely to pitch you. |
| High Risk-Taking (70+) | Quality Ceiling variance increases by +/-10 on all pilots. You get first-look on "unmarketable" specs that other networks pass on. Network President patience decreases (see 3.6). |
| High Safe (70+) | Quality Ceiling capped at 80 (you never produce a masterpiece, but you never produce a disaster). Ratings Floor +5 on all shows. Creative talent pool shrinks by 20%. |
| High Auteur-Driven (70+) | Showrunner Trust starts 15 points higher on all projects. Showrunners resist your notes 20% more aggressively. Budget overrun risk +15%. |
| High Producer-Driven (70+) | Budget overruns reduced 25%. Showrunners comply with all notes but Vision-stat contribution to Quality Ceiling is halved. You control the product but the product has a ceiling. |
| High Serialized (70+) | Critical scores +8. Casual viewer acquisition -20%. DVR/time-shift bonus +10% (serialized audiences record and rewatch). |
| High Episodic (70+) | Casual viewer acquisition +25%. Critical scores -5. Repeat/syndication value +30%. |

**Brand Legibility**: The network identity is displayed as a four-axis radar chart on the player's office wall -- a framed graphic that updates seasonally. The player sees their brand evolving in real time. Below the chart, a "Network Persona" label updates based on the profile: "Prestige Boutique," "Mass-Market Juggernaut," "Auteur's Haven," "Safe Harbor," or hybrid labels like "Populist Risk-Taker" or "Prestige Machine."

**Feedback**: When the player's brand shifts significantly (any axis crossing a 30 or 70 threshold), a trade magazine headline appears: "Is [Network] Becoming Too Prestige for Its Own Good?" or "[Network] Bets Big on Auteur Vision -- Will It Pay Off?" These headlines are flavor, but they also telegraph to the player that the industry has noticed their direction. The brand is not a hidden stat. The brand is the player's public identity, and the world reacts to it.

**Depth**: The brand system has no dominant strategy. High Prestige attracts the best creative talent but scares advertisers. High Populist prints money but bleeds cultural relevance. High Risk-Taking produces the occasional masterpiece but also produces expensive failures that threaten your job. The player must decide what kind of network they are building -- and then live with the consequences of that identity in a shifting landscape. The brand is not a score to optimize. It is a strategic position to defend.

---

### 3.5 The Landscape / Industry Simulation

**Player Verb**: READ, ANTICIPATE, POSITION

**System Description**: The television industry around the player is alive and evolving. The Landscape is modeled as a set of dynamic variables that shift each season:

**Audience Trend Vectors** (each shifts 1-5 points per season on a 0-100 scale):

| Trend | What It Tracks | Starting Value (2002) |
|---|---|---|
| **Serialization Appetite** | Audience willingness to commit to continuous narratives | 35 (low, but rising) |
| **Anti-Hero Tolerance** | Audience acceptance of morally grey protagonists | 30 (Sopranos has cracked the door) |
| **Genre Acceptance** | Audience willingness to watch sci-fi/fantasy on broadcast | 25 (pre-Lost) |
| **Reality Saturation** | How oversaturated the reality market is | 40 (Survivor boom, not yet peaked) |
| **Cable Prestige Threat** | How much cable is eating broadcast's prestige audience | 30 (HBO ascendant but not dominant) |
| **DVR Adoption** | Percentage of audience time-shifting | 15 (early adopters only) |

**Trend Telegraphing**: Trends do not shift invisibly. Each season, the player receives 2-3 "Industry Signals" -- trade magazine articles, ratings reports from rival networks, cultural events -- that hint at which trends are moving and in what direction. Example signals:

- "HBO's new drama draws record 14 million for season finale" -> Cable Prestige Threat likely rising.
- "Nielsen reports 22% of 18-34 viewers own a DVR" -> DVR Adoption accelerating.
- "Third reality competition series cancelled this month" -> Reality Saturation peaking.

Signals are probabilistic, not deterministic. A signal that cable prestige is rising does not guarantee a 5-point jump -- it might be 2 points or 4. The player must read signals as probabilities, not certainties. The Landscape rewards educated guessing, not perfect information.

**Rival Networks**: Three AI-controlled rival networks operate in parallel, each with their own brand profile and development strategy:

| Rival | Starting Brand | Strategy Tendency |
|---|---|---|
| **Titan Broadcasting** | Populist / Safe / Episodic | Chases proven formats. High ratings floor, low ceiling. The safe money. |
| **Sterling Network** | Prestige / Risk-Taking / Serialized | Chases critical acclaim. Volatile ratings. Attracts top talent. |
| **Pacific Channel** | Balanced / Producer-Driven | Reactive. Copies whatever worked last season. Dangerous because they adapt. |

Rivals affect the player in concrete ways:
- They grab scripts the player passes on (or lets expire on the desk).
- They compete for showrunners and actors.
- Their hits shift audience trends (a rival's breakout serialized drama pushes Serialization Appetite up faster).
- Their failures create openings (a rival's expensive flop makes advertisers nervous about that genre).

**Historical Inflection Points**: Pre-authored events arrive at fixed season intervals, modeling the real seismic shifts of the era:

| Season | Event | Mechanical Effect |
|---|---|---|
| Season 1 (2002-03) | "Cable drama wins first major Emmy" | Cable Prestige Threat +8. Prestige-axis networks gain. |
| Season 2 (2003-04) | "Reality mega-hit reshapes primetime" | Reality Saturation +15. Cheap reality scripts flood the desk. |
| Season 3 (2004-05) | "Serialized mystery becomes #1 show in America" | Serialization Appetite +20. Genre Acceptance +15. A gold rush begins. |
| Season 4 (2005-06) | "DVR adoption hits 30%. Advertisers panic." | DVR Adoption +20. Ad revenue per viewer drops 8% across the industry. |
| Season 5 (2006-07) | "Basic cable launches prestige originals" | Cable Prestige Threat +15. Mid-tier showrunners start preferring cable. |
| Season 6 (2007-08) | "The Writers' Strike" | All development halts for one cycle. Unscripted content surges. Returning series that were in production gain a massive ratings advantage. The player's pre-strike decisions determine their survival. |
| Season 7 (2008-09) | "Streaming service announces first original content" | The first whisper. No immediate mechanical effect, but the player sees the future. Serialization Appetite +5. |
| Season 8 (2009-10) | "The landscape fragments" | Audience trends accelerate in all directions simultaneously. No single strategy dominates. The endgame. |

**Feedback**: The Landscape is displayed as an "Industry Report" -- a trade publication-styled dashboard the player can open at any time. Trend vectors are shown as line graphs over time. Rival network slates are visible (you can see what they greenlit, though not their development details). Industry Signals arrive as physical newspaper clippings pinned to a corkboard in the player's office.

**Depth**: The Landscape transforms the game from a self-contained optimization puzzle into a strategic positioning game. The player who reads the landscape three seasons ahead -- who develops a serialized drama in season 2 knowing that Serialization Appetite will spike in season 3 -- reaps enormous rewards. The player who chases the current trend is always one season behind. The expert player develops material for the audience that will exist when the show airs, not the audience that exists today. That is the deepest strategic layer in the game.

---

### 3.6 Seasonal Rhythm & The Upfronts

**Player Verb**: PRESENT, COMMIT, SURVIVE

**System Description**: The seasonal rhythm provides the structural backbone for pacing and dramatic tension.

**The Network President**: An ever-present NPC who sets the player's operating constraints. The President has a **Patience** stat (0-100, starts at 60) that decreases when the network underperforms and increases when it overperforms:

```
Patience Shift = (Actual Season Revenue - Expected Season Revenue) / Expected Season Revenue * 50
```

If the network earns 20% more than expected, Patience rises by 10. If the network earns 15% less than expected, Patience drops by 7.5.

| Patience | Effect |
|---|---|
| 80-100 (Thriving) | Player gets +15% development budget. President stops attending development meetings (creative freedom). |
| 50-79 (Stable) | Standard operations. President makes occasional "suggestions" (ignorable). |
| 25-49 (Warning) | Development budget cut 10%. President mandates at least one procedural in the slate. |
| 1-24 (Final Warning) | Development budget cut 25%. President mandates genre quotas. Player cannot greenlight any pilot with a Commercial Floor below 40. |
| 0 (Fired) | Game over. Career retrospective plays. |

The President is the game's difficulty governor. A player who swings too boldly without commercial results faces increasing constraints that limit their creative freedom. A player who delivers hits earns the freedom to take bigger creative risks. This models the real dynamic: network executives earn creative latitude through commercial success.

**The Upfronts Sequence**: The annual climax. The player selects 2-4 pilots from their development slate to present to advertisers. The upfronts are a presentation mini-game:

1. **Slate Assembly** (2-3 minutes): Choose which pilots go to series and which die. Arrange them in presentation order. Each pilot has a "Pitch Profile" -- its strongest selling points for advertisers (star power, genre, demo appeal, brand fit).

2. **The Presentation** (3-5 minutes): Each pilot is presented in sequence. The player sees advertiser reaction in real-time -- an "Ad Buyer Confidence" meter that rises or falls based on the pilot's Commercial Floor, Star Power, and alignment with current ad market preferences. The player can add a **Sell Line** for each show -- a one-sentence pitch emphasizing different qualities:
   - "The next great American drama" (emphasizes Quality Ceiling -- risky but high-reward if the show delivers)
   - "18-49 demo magnet" (emphasizes Commercial Floor -- safe, but caps ad buy at market rate)
   - "The conversation starter" (emphasizes cultural potential -- attracts premium advertisers but scares commodity advertisers)

3. **The Ad Commit** (1-2 minutes): Based on the presentation, advertisers commit to ad buys at negotiated rates. Higher confidence = higher rates. The total ad commit determines the network's revenue for the season, which feeds directly into next year's development budget.

**Ad Revenue Calculation**:

```
Per-Show Ad Revenue = Base Rate * (1 + Ad Buyer Confidence / 100) * Demo Multiplier * Time Slot Multiplier
Base Rate = $80K per 30-second spot (2002 dollars, scales 3% per season for inflation)
Demo Multiplier = 0.8 (weak demo) to 1.5 (18-49 powerhouse)
Time Slot Multiplier = 0.7 (Friday 10pm) to 1.3 (Thursday 9pm)
```

A strong slate with high Ad Buyer Confidence in premium time slots generates $2-4M per episode in ad revenue. A weak slate in bad slots generates $800K-$1.5M. The difference is the player's operating budget for next season. The upfronts are not cosmetic. They are the single most consequential economic event in the game.

**Post-Upfronts: The Season**: Once shows launch, ratings arrive weekly. Each episode generates:

```
Episode Rating = Commercial Floor + (Quality * Audience Retention Factor) + Trend Alignment Bonus + random(-5, +5)
Audience Retention Factor = 0.85 for episode 2 (natural dropoff), rising to 0.95 by episode 6 if Quality > 60
Trend Alignment Bonus = (Show Genre alignment with current Audience Trend Vectors) * 0.1, range 0-8
```

The player makes mid-season decisions:
- **Schedule Adjustment**: Move a struggling show to a different time slot (costs credibility, might save the show).
- **Episode Order Extension**: Grant a full-season order to a show that premiered well (+$2-4M cost, signals confidence).
- **Cancellation**: Kill a show mid-season. Frees budget but damages Showrunner Trust and may trigger a public backlash that affects your network brand.
- **Midseason Replacement**: Slot in a held-back pilot from development. High-risk, high-reward -- midseason entries have lower awareness but face lower expectations.

**Feedback**: The upfronts sequence is presented as a staged event -- the player at a podium, advertiser faces in the audience rendered as simple portrait icons with expression states (interested, skeptical, excited, bored). The Ad Buyer Confidence meter is a large, visible bar that the entire presentation builds toward. When a show lands well, the audience leans forward. When a show falls flat, phones come out. The weekly ratings during the season arrive as physical newspapers on the desk -- headlines celebrating or mourning each show's performance.

---

## 4. SYSTEMS INTERACTION MAP

This is where the game transcends its individual parts. Let me map every feedback loop.

### 4.1 Positive Feedback Loops (Snowball Effects)

**The Prestige Spiral**: Protect creative vision (Notes) -> Quality Ceiling rises -> Show wins critical acclaim -> Network Brand shifts toward Prestige -> Higher-Vision showrunners seek you out -> Better scripts arrive on the desk -> More opportunities to protect creative vision. This models how real networks build creative reputations. HBO did not happen by accident. It happened because each bold greenlight attracted the next bold showrunner.

**The Commercial Engine**: Give commercial notes -> Commercial Floor rises -> Show rates well -> Ad revenue increases -> Development budget grows -> More pilots in the pipeline -> More shots on goal -> More hits -> More ad revenue. This is the broadcast network survival loop. It keeps the lights on. Without it, the Prestige Spiral has nothing to power.

**The Talent Magnet**: Build Showrunner Trust with a high-value creator -> They return with their next project (first-look deal) -> Their next project arrives on your desk before anyone else sees it -> You develop it with established trust -> The development is smoother, the notes are better received -> The show succeeds -> Showrunner Trust deepens. Loyalty compounds. A network that treats showrunners well builds a roster of returning creators that competitors cannot poach.

**The Brand Flywheel**: Accumulated brand identity -> Scripts that match your brand arrive more frequently (agents submit material to networks whose brand fits the project) -> Better material-brand fit -> Shows feel cohesive on the network -> Audience develops network loyalty -> Ratings stabilize -> Brand reinforces. A clear brand identity is self-selecting. It filters the noise.

### 4.2 Negative Feedback Loops (Balance Mechanisms)

**The Prestige Tax**: High Prestige brand -> Advertisers pay less (smaller audiences) -> Less ad revenue -> Smaller development budget -> Fewer pilots -> Less margin for error -> One expensive flop can trigger a budget crisis. The player who chases prestige without commercial grounding runs out of money. Art needs commerce to survive. The system enforces this.

**The Safety Trap**: High Safe brand -> Creative talent pool shrinks -> Quality Ceiling of incoming scripts decreases -> Shows become generic -> Audience erodes slowly (safe shows do not create new viewers, they only retain existing ones) -> Ratings decline imperceptibly over 3-4 seasons -> By the time the player notices, the network is irrelevant. Safety is a slow poison. The system does not punish it immediately. It punishes it inevitably.

**The Ego Reckoning**: High Auteur-Driven brand -> Showrunners resist notes -> Budget overruns increase -> Some projects spiral out of control -> The player must choose between killing an expensive project (wasting the investment) or letting a showrunner's indulgence air (risking a self-indulgent failure). Creative freedom has a cost. The system makes the player pay it.

**Network President Pressure**: Risk-Taking generates variance. Variance means some seasons underperform. Underperformance drops the President's Patience. Low Patience constrains future risk-taking. The player who swings bold must also deliver hits -- or face institutional retaliation. This is the central tension of the game: the courage to be bold and the skill to make bold work.

### 4.3 Cross-System Interactions

| System A | Feeds Into | System B | How |
|---|---|---|---|
| **Desk Triage** | determines raw material quality for | **Development Pipeline** | Better triage = better scripts entering development |
| **Development Pipeline** | determines pilot DNA via | **Notes System** | Showrunner + casting choices define the creative context for notes |
| **Notes System** | shapes | **Network Brand** | Every note shifts brand axes |
| **Network Brand** | filters | **Desk Triage** | Brand identity affects which scripts agents submit to you |
| **Landscape** | creates context for | **Notes System** | Audience trends inform whether a commercial or auteur note is strategically correct |
| **Landscape** | pressures | **Network Brand** | Industry shifts may render your brand obsolete, forcing reinvention |
| **Upfronts** | converts | **Development Pipeline output into Revenue** | Presentation quality determines ad commit |
| **Revenue** | funds | **Development Pipeline** | Next season's budget comes from this season's performance |
| **Showrunner Trust** | modifies | **Notes System** | High-trust showrunners accept notes more gracefully; low-trust showrunners fight every note |
| **Season Ratings** | adjust | **Network President Patience** | Hits buy freedom; flops buy constraints |

Every system feeds every other system. There are no islands. No mechanic exists in isolation. That is how you build depth -- not by adding more systems, but by making the systems you have talk to each other.

### 4.4 Emergent Possibilities

These are moments the systems create that no designer explicitly scripted:

- **The Long Game**: A player develops a serialized drama in season 2, knowing Serialization Appetite is only at 40. The show launches to mediocre ratings. The player shields it from cancellation, burning President Patience. In season 3, when a rival's serialized hit pushes Serialization Appetite to 60, the player's show -- already established, already renewed -- rides the wave. Year-over-year ratings double. The player's patience becomes prophecy.

- **The Poisoned Gift**: A legendary showrunner with Ego 9 and Vision 10 pitches a sprawling, expensive limited series. The player greenlights it. The showrunner ignores every note. The pilot goes $3M over budget. The rough cut is either brilliant or incomprehensible -- the player genuinely cannot tell. The test audience scores 28. The critics who see early screeners call it "the most ambitious pilot in a decade." The Upfronts are in two weeks. Does it go to series?

- **The Identity Crisis**: By season 4, the player has built a Prestige/Risk-Taking/Auteur-Driven network. Cable Prestige Threat hits 70. Their niche is being eaten. Their best showrunner is being courted by cable, which offers more creative freedom and shorter seasons. The player must either double down on a shrinking position or pivot toward Populist -- abandoning the brand they spent four seasons building. There is no right answer. There is only the answer the player can live with.

- **The Writers' Strike Gambit**: In season 6, the Writers' Strike halts all new development. The player who invested heavily in a deep development pipeline last season has shows in production that continue airing. The player who spread thin has nothing. The strike rewards strategic depth over tactical breadth -- but only a player who read the industry signals (rising labor tensions, guild negotiations) saw it coming.

These emerge from the system. I did not script them. The systems create them. That is how you know the design works.

---

## 5. PROGRESSION DESIGN

### 5.1 The 8-Season Campaign

The game spans 8 development seasons (2002-2010), each representing one session of 45-90 minutes. The campaign has a clear arc of escalating complexity, shifting landscape, and deepening stakes.

| Season | Year | Theme | New Mechanics / Pressures | Landscape State |
|---|---|---|---|---|
| **1** | 2002-03 | "The New Job" | Learn the loop. 10 scripts, 6 in development, 2-3 to series. Forgiving President (Patience 60+). | Broadcast dominance. Cable is niche. Procedurals reign. |
| **2** | 2003-04 | "Finding Your Voice" | Network Brand becomes visible. Showrunner Trust introduced. Rival networks become active. 12 scripts. | Reality boom begins. First prestige cable pressure. |
| **3** | 2004-05 | "The Gold Rush" | Serialization Appetite spikes. Genre Acceptance rises. The desk floods with ambitious specs. Budget competition intensifies. Mid-season replacements introduced. | Post-Lost gold rush. Everyone chases serialized. |
| **4** | 2005-06 | "The Squeeze" | DVR disrupts ad model. Revenue per viewer drops. Budget tightens. Showrunner poaching begins (rivals steal your talent). President Patience becomes volatile. | Ad market uncertainty. Cable ascendant. |
| **5** | 2006-07 | "The Reckoning" | Network Brand has real weight. Your identity either serves you or constrains you. Showrunners have career arcs now -- some burn out, some level up. Full complexity. | Basic cable prestige launches. Broadcast identity crisis. |
| **6** | 2007-08 | "The Strike" | Writers' Strike halts development for one cycle. Only pre-strike shows air. Unscripted content surges. The player's pre-strike portfolio determines survival. | Industry upheaval. Business model questioned. |
| **7** | 2008-09 | "The New World" | Streaming whispers. Audience fragmentation accelerates. No single strategy dominates. The player must adapt or die. Legacy decisions from early seasons compound. | Fragmentation. Old rules dissolve. |
| **8** | 2009-10 | "Legacy" | Final season. The player's choices culminate. Retrospective narrator begins commenting on the player's career. The question is no longer "what do I greenlight" but "what have I built?" | The era ends. What comes next is not your story. |

### 5.2 What Mastery Looks Like at Each Stage

**Season 1 Mastery**: The player picks the scripts with the best coverage grades, attaches available showrunners without thinking deeply about fit, gives notes based on instinct, and gets a functional if unremarkable slate. A competent start. The player understands the verbs.

**Season 2 Mastery**: The player starts reading blind-spot indicators and discovers that coverage grades are unreliable. They develop preferences -- "I like serialized dramas, I want my network to be known for bold work" -- and begin making triage decisions based on identity, not just grades. They notice that Showrunner Trust matters. They give their first bold note.

**Season 3 Mastery**: The player reads the landscape. They see Serialization Appetite spiking and have material in the pipeline to catch the wave. They understand the difference between a show that rates well at launch and a show that grows over a season. They start managing their slate as a portfolio -- some safe bets, some swings. They give notes that serve strategic goals, not just instinct.

**Season 4 Mastery**: The player navigates economic pressure. The DVR disruption forces hard choices -- which shows justify their cost, which are dead weight? The player begins to think about efficiency: a cheap show with a loyal niche audience might be more valuable than an expensive show with soft mass appeal. Showrunner relationships become a strategic asset. The player defends their best talent from poaching.

**Season 5 Mastery**: The player's network has an identity. That identity either opens doors or closes them. The expert player recognizes when their brand needs a correction -- when a Prestige network needs a populist hit to fund the next season of ambitious work, or when a Populist network needs a prestige play to attract better scripts. Brand management becomes a conscious, active discipline.

**Season 6 Mastery**: The player survives the Writers' Strike because they saw it coming. They stockpiled development. They have shows in production that ride out the gap. They emerge from the strike with a competitive advantage while rivals scramble. Crisis preparedness is the mark of a master.

**Season 7-8 Mastery**: The player is not optimizing anymore. They are curating. The expert player in the endgame has a clear creative philosophy, a roster of trusted showrunners, a brand that the industry recognizes, and a body of work they can be proud of. The final evaluation is not "did you make the most money" but "did you build something that mattered?" Mastery at the end is *coherence* -- the ability to look at eight seasons of decisions and see a vision, not a series of reactions.

### 5.3 Difficulty Curve

The difficulty curve is **stepped and landscape-driven**. New mechanics arrive in EXPAND phases. Landscape shifts arrive in TEST phases.

```
Season 1: EXPAND (learn loop)           -> TEST (first full slate)
Season 2: EXPAND (brand, trust, rivals) -> TEST (balance creative vs commercial)
Season 3: EXPAND (mid-season, genre)    -> TEST (gold rush pressure)
Season 4: EXPAND (DVR, poaching)        -> TEST (economic squeeze)
Season 5: EXPAND (career arcs, full)    -> TEST (brand reckoning)
Season 6: STRIKE (crisis survival)      -> RECOVERY (rebuild from disruption)
Season 7: ADAPT (fragmentation)         -> TEST (no dominant strategy)
Season 8: LEGACY (culmination)          -> EVALUATION (retrospective)
```

Each EXPAND phase gives the player one "grace period" -- a few in-game weeks where the new mechanic is introduced in isolation before it interacts with the full system. The player is never overwhelmed because each system is introduced before it is tested.

---

## 6. ECONOMY DESIGN

### 6.1 Revenue Sources

| Source | Amount | Frequency | Notes |
|---|---|---|---|
| **Upfronts Ad Commit** | $5M-$25M per season (total across all series) | Annual, post-upfronts | Primary revenue. Determined by slate quality and presentation. |
| **In-Season Ad Revenue** | $800K-$4M per episode per series | Weekly during season | Adjusts based on actual ratings vs. projected. Overperformance = bonus revenue. |
| **Syndication Deals** | $500K-$5M per series | After 4+ seasons of a series | Long-running episodic shows are syndication goldmines. Serialized shows syndicate poorly. |
| **Critical Acclaim Bonus** | $200K-$1M per award nomination/win | Annual, awards season | Small but meaningful. Models the indirect revenue of prestige (talent attraction, network cachet). |
| **Network President Budget Allocation** | $8M-$20M development budget per season | Annual | The baseline. Scales with President Patience and previous season performance. |

### 6.2 Expenses

| Expense | Cost | Frequency | Notes |
|---|---|---|---|
| **Script Option Fees** | $25K-$150K per script | Per priority script | Cheap for unknown writers, expensive for proven talent. |
| **Showrunner Deals** | $100K-$500K per pilot | Per development project | Top showrunners demand top dollar. |
| **Casting Costs** | $50K-$500K per episode per actor | Per series, ongoing | Star casting is an ongoing budget commitment, not a one-time cost. |
| **Pilot Production** | $2M-$8M per pilot | Per pilot order | The big line item. More pilots = more lottery tickets = more cost. |
| **Series Production** | $1.5M-$5M per episode | Per episode per series | The ongoing cost of a greenlit show. 13-episode order = $20-65M commitment. |
| **Development Overhead** | $500K per season | Fixed | Office, staff, readers, travel, meals. The baseline cost of doing business. |
| **Showrunner Retention** | $200K-$1M per season | Per returning showrunner | Keeping your best talent costs money. Losing them costs more. |

### 6.3 The Budget Equation

```
Available Development Budget = Network President Allocation + Carryover from Last Season
Operating Surplus/Deficit = (Total Ad Revenue + Syndication + Acclaim Bonus) - (Total Series Production Costs + Development Costs + Overhead)
Carryover = Operating Surplus * 0.5 (the network keeps half; the other half goes to corporate)
```

**Target Economy Balance**:

- **Season 1**: Budget allows 6 developments, 3 pilot orders, 2 series orders. Tight but manageable. No room for two expensive pilots.
- **Season 3**: Budget allows 8-10 developments, 4-5 pilot orders, 3-4 series orders. The player starts feeling like they have resources -- which is when the expensive choices begin tempting them.
- **Season 5**: DVR disruption has reduced per-viewer ad revenue by 12-18%. Budget tightens even as the player's ambitions grow. The squeeze is real.
- **Season 8**: The player should be operating at either comfortable surplus (if they navigated well) or desperate deficit (if they chased prestige without commercial grounding). The economy creates divergent late-game experiences based on early strategic choices.

**Cash Crisis Triggers**: The player enters a Cash Crisis (development budget halved for one season) if:
- Two expensive pilots ($6M+) fail in the same season (no series order)
- A flagship series collapses in ratings mid-season (renewal expected, cancellation forced)
- The Writers' Strike catches them with too many projects in pre-production (costs incurred, no content to show for it)

Target: 1-2 Cash Crises per 8-season career. The player should face genuine financial pressure 2-3 times but never feel like the economy is a constant grind. The budget should feel like a constraint that makes decisions interesting, not a punishment that makes decisions miserable.

### 6.4 Ratings-to-Revenue Conversion

```
Episode Viewership (millions) = Commercial Floor + (Quality * 0.15) + (Star Power * 0.3) + Time Slot Value + Trend Bonus + random(-1.5, +1.5)

Where:
  Commercial Floor = Base from genre (Procedural: 6M, Sitcom: 7M, Serialized: 4M, Sci-Fi: 3M, Reality: 5M)
                     + casting Star Power bonus + network Populist brand bonus
  Quality = pilot Quality Ceiling, modified by notes and production
  Time Slot Value = -2M (Friday 10pm) to +3M (Thursday 9pm)
  Trend Bonus = alignment with current Audience Trend Vectors, 0 to +3M

Ad Revenue per Episode = Viewership * CPM * 14 ad slots per hour
  Where CPM (cost per thousand viewers) = $25 base, modified by:
    +$5 if 18-49 demo skews strong
    +$3 if advertiser-friendly content (low controversy)
    -$5 if DVR-heavy audience (advertisers pay less for time-shifted viewing)
    +$8 for Thursday slot (premium pricing)
```

Example: A serialized drama with 8M viewers, strong 18-49, on Thursday 9pm, in 2005:
- CPM = $25 + $5 (demo) + $8 (Thursday) = $38
- Revenue per episode = 8,000 * $38 * 14 = $4.256M
- For a 22-episode season: $93.6M gross revenue against ~$66M production cost (at $3M/episode) = $27.6M margin.

That is a hit. The player can feel the math working. Conversely, a serialized drama with 3.5M viewers on Friday at 10pm:
- CPM = $25 - $5 (DVR heavy) = $20
- Revenue per episode = 3,500 * $20 * 14 = $980K
- For a 13-episode order: $12.7M gross against $39M production cost = -$26.3M loss.

That is a prestige money pit. The player can feel that math too. The economy makes commercial consequences legible without requiring the player to run spreadsheets.

### 6.5 Reputation Currencies

The game tracks three non-financial reputation currencies that do not convert directly to dollars but shape the player's strategic position:

| Currency | Driven By | Affects |
|---|---|---|
| **Industry Reputation** (0-100) | Show quality, critical acclaim, bold creative choices, showrunner relationships | Which showrunners want to work with you, which scripts arrive first on your desk, how the trade press covers you |
| **Network President Trust** (0-100, same as Patience) | Ratings performance, budget discipline, revenue growth | Development budget size, creative freedom, job security |
| **Cultural Footprint** (0-100) | Shows that define the conversation -- hits AND brilliant failures that people talk about | Whether your network is part of the cultural moment. High Cultural Footprint attracts 18-34 demo. Low Cultural Footprint means irrelevance. |

```
Overall Career Score = (Industry Reputation * 0.30) + (Network President Trust * 0.25) + (Cultural Footprint * 0.25) + (Financial Performance * 0.20)
```

The weighting is intentional: the game values creative and cultural impact slightly more than financial performance. A player who makes the most money but builds nothing culturally significant scores lower than a player who builds a cultural institution with solid (not spectacular) finances. This reflects the game's thesis: the job is not just to survive. The job is to build something that matters.

---

## 7. RISK ASSESSMENT

I have shipped a game with a broken core loop. I know what kills fun. Here is everything that could go wrong with PILOT and what we do about it.

### 7.1 Risk: The Notes System Feels Like a Multiple-Choice Test

**Severity**: CRITICAL. If the player reads a creative dilemma, identifies the "correct" answer based on stat optimization, and clicks without feeling torn, the entire game collapses. The Notes System IS the game. It must feel like a genuine creative dilemma, not a quiz.

**Mitigation**: Every note option must have legitimate strategic merit in at least one plausible context. Option A is never "the good option" and Option C is never "the bad option." Option A might be optimal for a Prestige network in season 5 but catastrophic for a Populist network in season 2. The strategic value of each option must shift based on the player's brand, their current landscape, their relationship with the showrunner, and their economic position. If playtesting reveals that one option is chosen more than 60% of the time across all contexts, the dilemma needs rebalancing.

Additionally: authored content, not procedural. Each dilemma must be written by a human who understands dramatic stakes. "Do you add a love triangle?" is a creative question. "Do you increase Commercial Floor by 5?" is a spreadsheet question. The dilemmas must always be framed as creative conversations, with the mechanical effects visible but secondary to the dramatic framing.

**Playtest Priority**: #1. Build 10 dilemmas. Present them to playtesters in different strategic contexts (early game Populist network, late game Prestige network, mid-game under budget pressure). If playtesters disagree with each other about the right choice, the system works. If they all pick the same option, it does not.

### 7.2 Risk: Information Overload at the Desk

**Severity**: HIGH. 15-20 scripts arriving with ticking clocks, each with multiple parameters to evaluate, could overwhelm the player. If the desk feels like homework instead of a fast-paced triage game, players disengage.

**Mitigation**: Visual hierarchy is the answer. The coverage sheet must communicate essential information in a 5-second glance: genre color, letter grade in large font, logline in bold, talent attachments as recognizable name badges, blind-spot indicators as small warning icons. The deep information (Hidden Quality Variance, Notes Preview) is available on click-through but never forced. The default experience is skim-speed. The deep experience is opt-in. Also: the expiration clock should be generous in season 1 (7 days per script) and tighten in later seasons (3-4 days). Let the player learn the desk at a comfortable pace before the pressure mounts.

**Playtest Priority**: #2. Build the desk interface. Populate it with 15 scripts. Time how long players take to triage all 15. If average exceeds 8 minutes, the information density is too high. If players consistently miss the same information (e.g., never reading blind-spot indicators), the visual hierarchy needs adjustment.

### 7.3 Risk: The Development Pipeline Becomes Plate-Spinning Tedium

**Severity**: HIGH. Managing 8-12 simultaneous projects -- each with a showrunner, cast, notes, and budget -- could make the pipeline feel like administrative busywork rather than strategic decision-making. If the player is clicking through menus rather than making interesting choices, the 5-minute loop drags.

**Mitigation**: Not all projects demand equal attention. The pipeline must surface **Attention Flags** -- projects that need a decision NOW -- while letting stable projects run on autopilot. A pilot in Synergy with its showrunner, on budget, with no casting conflicts, should not require player interaction until the rough cut. A pilot where the showrunner is clashing with the lead actor, the production is $500K over budget, and a test screening just scored 31 should demand immediate attention. The pipeline is an attention-management system, not a micro-management system. The player's job is to identify which projects need them and let the rest run.

**Playtest Priority**: #3. Run a full development season with 10 simultaneous projects. Track how many "unnecessary clicks" the player makes -- interactions with projects that were running fine without intervention. If the player feels compelled to check every project every cycle, the Attention Flag system is not working.

### 7.4 Risk: The Landscape Feels Deterministic

**Severity**: MEDIUM-HIGH. If the player learns that the serialized drama boom always happens in season 3 and the Writers' Strike always happens in season 6, the historical events become a solved puzzle rather than a dramatic challenge. The player optimizes against known events rather than navigating uncertainty.

**Mitigation**: Historical inflection points arrive at fixed seasons (they are the era's story, and the game should tell that story faithfully), but their magnitude and secondary effects vary between playthroughs. The serialized boom in season 3 always happens, but the size of the Serialization Appetite jump varies (15-25 points). The Writers' Strike always happens in season 6, but its duration varies (1-2 development cycles halted). The DVR disruption timeline has a 1-season variance window. The player knows WHAT is coming but not exactly HOW HARD it hits. Additionally, rival network behavior introduces genuine uncertainty -- a rival's breakout hit or spectacular flop creates ripple effects the player cannot predict.

**Playtest Priority**: #4. Run two playthroughs with identical player decisions through season 3. If the outcomes are more than 80% identical, the landscape needs more variance injection.

### 7.5 Risk: The Upfronts Are Anticlimactic

**Severity**: HIGH. The upfronts are the season's climax. If they feel like "pick your top 3 pilots and watch a number go up," the dramatic payoff fails. The player should feel like they are presenting to a room full of skeptics and believers, defending their taste before the people who write the checks.

**Mitigation**: The upfronts must be a performance. Presentation order matters (lead with your strongest show to build confidence, or save it for the closer?). Sell Lines matter (overpromise and risk backlash if the show underperforms, or undersell and leave ad revenue on the table?). The ad buyer reactions must be specific and varied -- one buyer loves the crime drama, another is cold on it. The player reads the room and adjusts. The upfronts should take 5-7 minutes and feel like the longest 5-7 minutes of the season. If the player's hands are slightly tense during the presentation, we have succeeded.

**Playtest Priority**: #5. Build the upfronts as a vertical slice. Three pilots. Full presentation sequence. Full ad commit. If playtesters want to re-do the presentation with different choices, the climax works.

### 7.6 Risk: Late-Game Stagnation (Seasons 6-8)

**Severity**: MEDIUM. By season 6, the player may have "solved" the systems. Optimal showrunner pairings, reliable note strategies, predictable landscape evolution. The game could feel automated.

**Mitigation**: Season 6 (the Writers' Strike) is a deliberate disruption. It invalidates stockpiled strategies and forces adaptation. Season 7 introduces audience fragmentation -- no single strategy dominates because the audience itself is splintering. Season 8 introduces the Legacy frame, which shifts the player's motivation from "optimize" to "reflect." The late game does not ask the player to do the same thing better. It asks the player to do something different. If the early game is "learn the verbs," and the mid-game is "master the systems," the late game is "decide what it was all for."

Additionally: showrunner career arcs create emergent late-game drama. A trusted showrunner who has delivered three hits may burn out (Vision drops, Reliability drops) or leave for cable. The player must develop new relationships while their established ones erode. The late game models institutional entropy -- the constant effort required to sustain excellence.

**Playtest Priority**: #6. Accelerated late-game test. Start playtesters at season 5 with an established network. Track engagement metrics in seasons 6-8. If engagement drops more than 20% compared to seasons 3-4, the late-game pressures need sharpening.

### 7.7 Risk: The Authored Content Runs Out

**Severity**: HIGH. The Notes System requires authored creative dilemmas. The game spans 8 seasons with 8-12 pilots per season. That is 64-96 pilots, each needing 4-8 authored notes. That is 256-768 authored creative dilemmas, plus loglines, script excerpts, and showrunner profiles.

**Mitigation**: The content library must be modular. A core set of 80 pilot concepts, each with a full dilemma tree, covers the base game. Dilemmas are tagged by genre, tone, and creative axis so they can be contextually assigned to different pilot concepts. A "dark antihero" dilemma works for a crime drama or a legal thriller or a medical drama -- the context changes but the creative tension is the same. The authored core can serve multiple pilot concepts through recombination. Target: 80 pilot concepts, 200 unique dilemmas, with each dilemma usable across 2-3 genre contexts = 400-600 effective dilemma appearances. Across 8 seasons, this provides enough variety that repetition is rare.

**Playtest Priority**: #7. Track dilemma repetition across two full 8-season playthroughs. If a playtester recognizes a repeated dilemma within a single playthrough, the content pool needs expansion. If they recognize it across two playthroughs, that is acceptable.

### 7.8 Risk: The Player Feels Like a Bureaucrat, Not an Artist

**Severity**: CRITICAL. If the game's systems reduce the player to a stat optimizer -- someone who picks the highest numbers and gives the notes that maximize Quality Ceiling -- the creative fantasy dies. The player must feel like a person with taste, not a human calculator.

**Mitigation**: The game must always present information as narrative, not numbers. The rough cut is not "Quality: 73." It is "the performances are magnetic, the pacing drags in the second act, and the final scene either lands like a thunderbolt or a pretentious thud depending on who's watching." The test audience data is not "Score: 42." It is "42 overall, but the 18-34 demo scored it 71, and someone wrote 'best thing I've seen all year' in the comment card." The numbers exist under the hood. The player sees stories, reactions, and human responses. If the player ever says "I greenlit that because the Quality Ceiling was 78," we have failed. If the player says "I greenlit that because the rough cut gave me chills even though the test audience hated it," we have succeeded.

**Playtest Priority**: Ongoing. Every playtest session should include the question: "Why did you make that choice?" If the answer is a number, the presentation layer needs more narrative wrapping. If the answer is a story, we have the game.

---

## 8. OPEN QUESTIONS FOR PLAYTESTING

These are the questions that only playtesting can answer. I have opinions. Playtesters have data. Data wins.

1. **Script Excerpt Length**: How much script text does the player actually read? The deep-read option should reveal enough to make the player feel they are engaging with the work, not scanning a stat sheet. Current target: 1 paragraph (3-5 sentences) for a skim, 1 page (8-12 sentences) for a deep read. Is this enough for the fantasy? Too much for the pacing?

2. **Notes Per Pilot**: 2-4 dilemmas per pilot, across two notes sessions. Is 4 too many for a single pilot? Does the player develop notes fatigue? Should the number scale with how much the player has invested in the project (more notes for priority projects, fewer for secondary ones)?

3. **Showrunner Personality Depth**: How much characterization does a showrunner need before the player cares about their trust relationship? A name and stats? A biography paragraph? Recurring dialogue lines that reflect their personality? The character investment threshold determines content scope.

4. **Rough Cut Presentation**: The pitch describes "watching" a rough cut. What does the player actually see? A written scene description? A storyboard panel? A stat summary with narrative color? The answer determines the game's production ambition and the player's emotional connection to the shows they develop.

5. **Season Length Calibration**: Is 45-90 minutes the right session length? If players disengage at 60 minutes, compress the season. If players want more time with their slate, expand it. Measure where attention drops and where it peaks.

6. **Kill Decision Weight**: When the player kills a pilot at the upfronts, does it feel consequential? The dead pilots drawer is a visual memorial, but is it enough? Should the killed pilot's showrunner have a reaction scene? Should a montage show "what might have been" for the killed show? Or does that slow the upfronts pacing?

7. **Rival Network Visibility**: How much should the player see of rival network operations? Too much and the player games the AI. Too little and the rivals feel like background noise. The sweet spot is probably "you see their slate announcements and their ratings, but not their development process."

8. **Brand Axis Count**: Four axes (Prestige/Populist, Risk/Safe, Auteur/Producer, Serialized/Episodic). Is four the right number? Three might be cleaner. Five might capture more nuance. Four is the hypothesis. Test it.

9. **Network President Personality**: Is the President a characterized NPC with dialogue and a relationship arc, or a system that applies pressure through mechanics alone? A characterized President is more narratively satisfying but risks becoming an annoyance if the player disagrees with their taste. A mechanical President is cleaner but less emotionally engaging.

10. **Endgame Retrospective**: The career retrospective at the end of season 8 -- is it a narrator summarizing the player's career, a montage of key moments, a "where are they now" for the player's shows and showrunners, or all three? How long should it last? Too short and the ending feels abrupt. Too long and the player is watching a cutscene instead of playing a game. Target: 3-5 minutes of retrospective content. Test whether players watch it all or skip.

---

## CLOSING NOTE

This document is a first pass. Design is iteration, and iteration requires playtesting. But every system here is connected. The Desk feeds the Pipeline feeds the Notes feed the Brand feeds the Upfronts feed the Revenue feed the next season's Desk. The loop is closed. The systems talk. The depth is real.

The question this game asks -- **is it possible to be a gatekeeper and still have a soul?** -- is embedded in every mechanic. The Notes System makes you feel it. The Brand System makes you own it. The Landscape makes you confront it in a world that is changing whether you are ready or not. The Upfronts make you defend it before an audience that only cares about the money. That is not a theme pasted onto a spreadsheet. That is a theme expressed through systems.

How does this feel at hour 20? At hour 20, the player is not clicking buttons. They are a television executive with a philosophy, a track record, a network they built from nothing, and a list of shows they greenlit and killed that they think about when the game is off. They have a showrunner they trust, a rival they resent, and a President whose patience they have learned to manage. They are looking at a script on their desk -- coverage grade B+, blind-spot indicator that says "may be ahead of its time" -- and they are deciding whether to bet their career on it. That hesitation, that weight, that feeling of *this matters* -- that is the game.

Find the desk. Find the notes. Find the fun. Build from there.

-- REED
