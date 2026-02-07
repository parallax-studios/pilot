# PILOT — Technical Architecture Document

**Author**: BYTE (Lead Programmer)
**Version**: 1.0
**Date**: 2026-02-07
**Status**: Production-Ready Architecture

---

## 0. EXECUTIVE SUMMARY

PILOT is a management sim where taste is the mechanic. 8-season campaign. 45-90 minute sessions. Text-heavy, data-driven, narrative-focused. The game is built on three technical pillars:

1. **Data-driven content pipeline** — 80 pilot concepts, 200+ creative dilemmas, all authored JSON. No procedural generation. Content is king.
2. **State machine architecture** — Every system is a state machine. Scripts flow through states. Pilots flow through states. Seasons flow through states. This is not an ECS game. This is a workflow sim.
3. **Immediate-mode UI with physical metaphor** — The desk, the whiteboard, the screening room. The UI is not chrome around the game. The UI is the game.

Target platform: PC/Mac first. Switch port feasible. Mobile is not the play — too much text, too much complexity, wrong audience.

Engine recommendation: **Unity 2022 LTS**. Not because it's the best engine. Because it ships. Godot is tempting but the UI tools are not mature enough for a text-heavy interface game. Unreal is overkill and the build times would murder iteration speed. Unity's UI Toolkit (the new one, not UGUI) handles complex layouts, the C# tooling is mature, and the build pipeline to Mac/PC/Switch is proven.

Performance budget: This is not a GPU-bound game. This is a data-processing and UI-rendering game. Target 60fps on a 2019 MacBook Pro. If we can't hit that, we have architectural problems, not content problems.

Core technical risk: **Authored content volume**. The game needs 80 pilots × 6 dilemmas each × 3 options each = 1,440 authored decision nodes, plus loglines, excerpts, showrunner bios, event text. That is 150,000-200,000 words of authored content. The content pipeline must be clean, testable, and moddable or we drown in JSON files.

Ship date math: 18-24 months for a solo or two-person team. Core loop prototype in 3 months. Vertical slice (one full season) in 6 months. Content authoring is the long tail. The systems are not complex. The content volume is the constraint.

This document covers what to build, how to build it, and what breaks if we get it wrong. No placeholders. No "TBD." If it is in this doc, it is buildable.

---

## 1. ENGINE & FRAMEWORK RECOMMENDATION

### 1.1 Engine: Unity 2022 LTS

**Why Unity:**

- **UI Toolkit** — The new USS/UXML system is designed for complex editor-like interfaces. This game is a workspace sim. UI Toolkit gives us flexbox-style layout, CSS-like styling, and runtime performance that UGUI cannot match for a screen full of dynamic text elements. The desk interface alone has 15+ script cards updating in real time. UGUI would choke. UI Toolkit will not.

- **C# + modern tooling** — LINQ for data queries, async/await for content loading, robust serialization (JSON.NET or Unity's new JsonUtility). The game is 90% data processing and 10% rendering. C#'s tooling advantage over GDScript or C++ is massive for a data-heavy game.

- **Cross-platform proven** — PC/Mac/Switch. One codebase. Minimal platform-specific code. The game has no physics, no complex rendering, no multiplayer. Unity's cross-platform story is mature for this use case.

- **Asset Store ecosystem** — We will need a dialogue system (Yarn Spinner or Ink integration), a save system (Easy Save or custom), and possibly a localization framework (Unity Localization Package). These exist and are battle-tested on Unity.

- **Build times** — Unity's incremental build pipeline is fast for non-asset-heavy games. Full rebuild under 2 minutes on modern hardware. Iteration speed is job #1.

**Why not Godot:**

Godot 4's UI system is powerful but immature. The game's desk interface — draggable script cards, expiring timers, layered coverage sheets, physical paper metaphor — requires pixel-perfect layout control and complex input handling. Godot's Control node system can do it, but the tooling and community knowledge for complex UI is thin. Unity's UI Toolkit has more battle-tested patterns for this exact use case. If this were a 2D platformer, Godot would win. This is a text-heavy data-driven sim. Unity's C# advantage is decisive.

**Why not Unreal:**

Overkill. Unreal's rendering power is wasted. UMG (the UI system) is capable but the engine's compile times and asset pipeline are built for 3D action games. The game has no 3D models, no real-time lighting, no complex shaders. Unreal's advantages do not apply. Its disadvantages (build times, engine complexity, Blueprint vs C++ friction) are deal-breakers for a small team.

**Why not custom engine:**

I have built custom engines. They take longer than the game. For a management sim with no novel rendering requirements, a custom engine is ego, not engineering. Ship the game, not the tech.

### 1.2 Core Libraries & Plugins

| Library | Purpose | Rationale |
|---|---|---|
| **Unity UI Toolkit** | All UI rendering | Built-in. Modern. Performant. No UGUI. |
| **Newtonsoft JSON.NET** | Data serialization | Industry standard. Better than Unity's JsonUtility for complex nested data. |
| **Ink (inkle)** | Narrative scripting | Proven narrative middleware. The game has event text, dilemma text, rough cut descriptions. Ink handles branching text with minimal code. Alternative: Yarn Spinner. Either works. |
| **DOTween** | UI animation | Desk card shuffling, whiteboard transitions, upfronts presentation. Smooth tweens without hand-rolling lerp code. |
| **NUnit / Unity Test Framework** | Unit testing | The game's simulation logic (ratings calculation, budget math, trend vectors) must be unit tested. No excuses. |
| **Easy Save 3** (optional) | Save system | If we do not want to hand-roll save serialization. Handles versioning and corruption gracefully. Alternative: custom JSON save system. |

**External Dependencies:**

None. The game is single-player, offline, no analytics, no telemetry, no server. The only external dependency is the OS filesystem for saves. Intentional. Fewer dependencies = fewer points of failure.

### 1.3 Version Control & Build Pipeline

**Git + LFS**. Standard. The repo is mostly code and JSON, not binary assets, so diff/merge works. LFS for any image assets (UI sprites, key art). `.gitignore` the Unity Library folder and Temp folder. Commit everything else.

**CI/CD:** GitHub Actions or GitLab CI. Automate:
- Unit tests on every push (must pass before merge)
- Build for PC/Mac on every tag (automated release builds)
- Content validation scripts (check for orphaned dilemma IDs, missing localization keys, invalid stat ranges)

The game's content volume makes manual QA insufficient. Automated content validation is not optional.

---

## 2. CORE ARCHITECTURE

### 2.1 High-Level System Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                        GAME MANAGER                          │
│  (Singleton, owns game state, coordinates systems)           │
└─────────────────┬───────────────────────────────────────────┘
                  │
      ┌───────────┼───────────┬───────────┬───────────────┐
      │           │           │           │               │
      ▼           ▼           ▼           ▼               ▼
┌──────────┐ ┌─────────┐ ┌─────────┐ ┌──────────┐ ┌────────────┐
│  DESK    │ │PIPELINE │ │  NOTES  │ │ UPFRONTS │ │  SEASON    │
│  SYSTEM  │ │ SYSTEM  │ │ SYSTEM  │ │  SYSTEM  │ │  SYSTEM    │
└────┬─────┘ └────┬────┘ └────┬────┘ └────┬─────┘ └─────┬──────┘
     │            │           │           │              │
     └────────────┴───────────┴───────────┴──────────────┘
                            │
                ┌───────────┴───────────┐
                ▼                       ▼
         ┌─────────────┐         ┌─────────────┐
         │  LANDSCAPE  │         │   NETWORK   │
         │  SIMULATION │         │   BRAND     │
         └─────────────┘         └─────────────┘
                │                       │
                └───────────┬───────────┘
                            ▼
                    ┌──────────────┐
                    │  DATA LAYER  │
                    │ (ScriptDB,   │
                    │ ShowrunnerDB,│
                    │ DilemmaDB)   │
                    └──────────────┘
```

### 2.2 Data Flow: Script to Series

This is the golden path. Every script flows through this pipeline.

```
1. SCRIPT ARRIVAL
   - ScriptData instantiated from ScriptDB
   - Added to DeskSystem.incomingQueue
   - Expiration timer starts

2. DESK TRIAGE
   - Player reads coverage (skims or deep-reads)
   - Player decision: PASS / CONSIDER / PRIORITY
   - PRIORITY -> moves to PipelineSystem.developmentQueue
   - PASS -> destroyed
   - CONSIDER -> stays in incomingQueue until revisited or expired

3. DEVELOPMENT PHASE
   - PipelineSystem assigns showrunner (player choice)
   - PipelineSystem assigns cast (player choice)
   - PipelineSystem allocates budget (player input)
   - NotesSystem triggers (Early Notes phase)
     - 2-3 dilemmas presented
     - Player choices modify PilotData.qualityCeiling, .commercialFloor, showrunnerTrust
   - PilotData state: IN_DEVELOPMENT -> PILOT_ORDERED

4. PILOT PRODUCTION
   - Time passes (simulated)
   - Rough cut generated (quality calculated from all inputs)
   - Test audience simulation runs
   - NotesSystem triggers (Final Notes phase)
     - 2-3 dilemmas presented
     - Player final adjustments
   - PilotData state: PILOT_ORDERED -> AWAITING_GREENLIGHT

5. UPFRONTS
   - Player selects 2-4 pilots for series order
   - UpfrontsSystem presents each pilot
   - Ad buyer confidence calculated
   - Ad revenue committed
   - Selected pilots -> SeriesData, state: GREENLIT
   - Rejected pilots -> state: KILLED

6. SEASON BROADCAST
   - SeasonSystem simulates weekly ratings
   - Episode viewership calculated from commercialFloor + quality + trends
   - Mid-season decisions: renewal, cancellation, schedule adjustment
   - End-of-season: metrics update (revenue, reputation, brand axes)

7. NEXT SEASON
   - Loop back to step 1 with new scripts
```

Every system is a state transition. Scripts have states. Pilots have states. The season has states. The GameManager orchestrates state transitions. No system directly calls another system's methods. All communication is through events or the GameManager.

### 2.3 Core Architecture Pattern: State Machines + Event Bus

**Why State Machines:**

This game is a workflow. Scripts arrive, move through phases, exit. Pilots develop, produce, greenlight or die. The season progresses through fixed stages. State machines model workflows cleanly. Each entity (Script, Pilot, Season) is a state machine. Each system (Desk, Pipeline, Notes, Upfronts, Season) manages state transitions for its entities.

**Why Event Bus:**

Systems do not talk to each other directly. When a script is prioritized, DeskSystem fires a `ScriptPrioritized` event. PipelineSystem listens and adds the script to its queue. When a note is given, NotesSystem fires a `NoteGiven` event. NetworkBrand listens and adjusts axes. Event-driven architecture decouples systems. We can add, remove, or replace systems without refactoring the entire codebase.

**Implementation:**

```csharp
// Simple event bus
public class EventBus {
    private Dictionary<Type, List<Delegate>> listeners = new();

    public void Subscribe<T>(Action<T> listener) {
        if (!listeners.ContainsKey(typeof(T))) listeners[typeof(T)] = new List<Delegate>();
        listeners[typeof(T)].Add(listener);
    }

    public void Publish<T>(T eventData) {
        if (listeners.ContainsKey(typeof(T))) {
            foreach (var listener in listeners[typeof(T)]) {
                ((Action<T>)listener)(eventData);
            }
        }
    }
}

// Usage example
EventBus.Subscribe<ScriptPrioritized>(OnScriptPrioritized);
EventBus.Publish(new ScriptPrioritized { scriptID = "pilot_001" });
```

No Unity-specific event system. Custom event bus. 50 lines of code. Zero dependencies. Fast. Testable.

### 2.4 Save System Architecture

**Save Format:** JSON. One save file per playthrough. Saved to platform-appropriate persistent storage (AppData on Windows, ~/Library/Application Support on Mac, /sdcard on Switch).

**What Gets Saved:**

```json
{
  "version": "1.0",
  "timestamp": "2026-02-07T14:32:00Z",
  "currentSeason": 3,
  "networkState": {
    "budget": 12500000,
    "reputation": 67,
    "brandAxes": { "prestige": 58, "riskTaking": 72, "auteur": 55, "serialized": 63 },
    "presidentPatience": 54
  },
  "landscapeState": {
    "serializationAppetite": 48,
    "antiHeroTolerance": 35,
    "genreAcceptance": 30,
    "realitySaturation": 52,
    "cablePrestigeThreat": 38,
    "dvrAdoption": 20
  },
  "scripts": [
    { "id": "script_034", "state": "IN_CONSIDERATION", "expirationTurnsLeft": 2, ... }
  ],
  "pilots": [
    { "id": "pilot_012", "state": "IN_DEVELOPMENT", "showrunnerID": "sr_008", "qualityCeiling": 78, ... }
  ],
  "series": [
    { "id": "series_003", "currentEpisode": 8, "totalViewership": 145000000, ... }
  ],
  "showrunners": [
    { "id": "sr_008", "trust": 65, "heatLevel": 7, "lastProjectID": "pilot_012", ... }
  ],
  "history": [
    { "season": 1, "eventType": "GREENLIGHT", "pilotID": "pilot_001", ... },
    { "season": 2, "eventType": "CANCELLATION", "seriesID": "series_002", ... }
  ]
}
```

**Save Timing:** Autosave at the end of every season. Manual save available at any time. One autosave slot, three manual save slots. No cloud saves at launch (PC filesystem only). Cloud saves can be post-launch DLC if demand exists.

**Versioning Strategy:** `version` field in save file. If save version < current game version, run migration scripts. Migration scripts are code, not data. Example:

```csharp
if (saveData.version == "1.0" && CURRENT_VERSION == "1.1") {
    // Migrate: v1.1 added "culturalFootprint" to networkState
    saveData.networkState.culturalFootprint = CalculateLegacyCulturalFootprint(saveData);
    saveData.version = "1.1";
}
```

Breaking changes to save format are acceptable in Early Access. Post-1.0, save compatibility is law. Plan the schema carefully.

---

## 3. KEY GAMEPLAY SYSTEMS: TECHNICAL DESIGN

### 3.1 Desk System (Script Triage)

**Responsibilities:**
- Manage incoming script queue
- Handle player triage actions (pass/consider/priority)
- Tick expiration timers
- Surface scripts to UI

**Core Data Structure:**

```csharp
public class ScriptData {
    public string id;
    public string logline;
    public GenreTag genre;
    public CoverageGrade readerGrade;         // C+ through A
    public List<string> talentAttachments;    // Showrunner/actor IDs
    public List<string> blindSpotIndicators;  // Text hints about hidden qualities
    public int expirationTurns;               // Countdown timer
    public ScriptOrigin origin;               // Spec, pitch, adaptation, returning creator
    public int hiddenQualityVariance;         // +/- 0-20, revealed on deep read
    public TonalProfile tonalProfile;         // 4-axis profile for showrunner fit
    public List<string> dilemmaIDs;           // References to DilemmaDB entries
}

public enum GenreTag { ProceduralDrama, SerializedDrama, WorkplaceComedy, FamilySitcom, PrestigeLimited, SciFiFantasy, Reality, Dramedy }
public enum CoverageGrade { CPlus, B, BPlus, AMinus, A }
public enum ScriptOrigin { Spec, Pitch, Adaptation, ReturningCreator }
```

**Triage Actions:**

```csharp
public class DeskSystem {
    private List<ScriptData> incomingQueue = new();
    private List<ScriptData> considerPile = new();
    private int dailyTimeTokens = 3;

    public void OnTurnStart() {
        // Spawn new scripts (2-4 per turn in pitch season)
        // Tick expiration timers on all scripts
        // Expire scripts and notify player
    }

    public void PassScript(string scriptID) {
        // Remove from queue, fire ScriptPassed event
        // Rival networks may pick it up (LandscapeSystem handles)
    }

    public void ConsiderScript(string scriptID) {
        // Move to consider pile, clock still ticking
    }

    public void PriorityScript(string scriptID) {
        // Fire ScriptPrioritized event
        // PipelineSystem picks it up
    }

    public void DeepRead(string scriptID) {
        if (dailyTimeTokens <= 0) return; // Player out of tokens
        dailyTimeTokens--;
        // Reveal hiddenQualityVariance
        // Reveal notes preview (first dilemma from dilemmaIDs)
    }
}
```

**UI Integration:**

The desk UI is a UI Toolkit-based interface with:
- Script cards as `VisualElement` instances styled as physical paper
- Draggable via `PointerDownEvent` / `PointerMoveEvent` / `PointerUpEvent` manipulation
- Each card binds to a ScriptData instance
- Expiration timer displayed as red-stamped date, updates every turn
- Deep Read button consumes a time token, triggers modal with full script info

**Performance Consideration:**

Max 20 scripts in queue at once. Each script is a single UI element. Rendering 20 text-heavy cards at 60fps is trivial for UI Toolkit. If we see frame drops, the issue is layout recalculation. Solution: cache layout, only recalc on add/remove, not on every frame.

### 3.2 Development Pipeline System

**Responsibilities:**
- Track pilots in development
- Handle showrunner/casting/budget allocation
- Surface attention flags (projects needing player decisions)
- Trigger state transitions (IN_DEVELOPMENT -> PILOT_ORDERED -> AWAITING_GREENLIGHT)

**Core Data Structure:**

```csharp
public class PilotData {
    public string id;
    public string scriptID;                 // Source script reference
    public PilotState state;
    public string showrunnerID;
    public List<string> castIDs;
    public BudgetAllocation budget;
    public float qualityCeiling;            // 0-100, modified by notes
    public float commercialFloor;           // 0-100, modified by notes + casting
    public float roughCutQuality;           // Final calculated quality post-production
    public int testAudienceScore;           // 0-100
    public List<string> completedDilemmaIDs; // Track which notes have been given
    public AttentionFlag attentionFlag;     // NONE, BUDGET_OVERRUN, SHOWRUNNER_CONFLICT, CASTING_ISSUE
}

public enum PilotState { IN_DEVELOPMENT, PILOT_ORDERED, ROUGH_CUT_READY, AWAITING_GREENLIGHT, GREENLIT, KILLED }
public enum AttentionFlag { NONE, BUDGET_OVERRUN, SHOWRUNNER_CONFLICT, CASTING_ISSUE, TEST_SCORE_CATASTROPHIC }

public struct BudgetAllocation {
    public float writingRoom;        // 0-1 percentage
    public float productionDesign;   // 0-1
    public float directing;          // 0-1
    public float postProduction;     // 0-1
    public float marketing;          // 0-1
    // Sum must equal 1.0
}
```

**Showrunner Fit Calculation:**

```csharp
public int CalculateShowrunnerFit(ShowrunnerData showrunner, ScriptData script) {
    // Each axis: 1-10 scale
    int darkLightDiff = Mathf.Abs(showrunner.tonalPreference.darkLight - script.tonalProfile.darkLight);
    int serialEpisodicDiff = Mathf.Abs(showrunner.tonalPreference.serialEpisodic - script.tonalProfile.serialEpisodic);
    int characterPlotDiff = Mathf.Abs(showrunner.tonalPreference.characterPlot - script.tonalProfile.characterPlot);
    int intimateEpicDiff = Mathf.Abs(showrunner.tonalPreference.intimateEpic - script.tonalProfile.intimateEpic);

    int totalDiff = darkLightDiff + serialEpisodicDiff + characterPlotDiff + intimateEpicDiff;
    int fitScore = 100 - (totalDiff * 5);
    return Mathf.Clamp(fitScore, 0, 100);
}
```

**Attention Flag Logic:**

```csharp
public void UpdateAttentionFlags() {
    foreach (var pilot in activePilots) {
        if (pilot.budget.TotalSpent > pilot.budget.TotalAllocated * 1.15f) {
            pilot.attentionFlag = AttentionFlag.BUDGET_OVERRUN;
        } else if (pilot.showrunner.trust < 30) {
            pilot.attentionFlag = AttentionFlag.SHOWRUNNER_CONFLICT;
        } else if (pilot.testAudienceScore < 35) {
            pilot.attentionFlag = AttentionFlag.TEST_SCORE_CATASTROPHIC;
        } else {
            pilot.attentionFlag = AttentionFlag.NONE;
        }
    }
}
```

Pilots with `NONE` flag do not demand UI attention. Pilots with flags are surfaced prominently. This keeps the pipeline from feeling like micro-management.

**UI Integration:**

Whiteboard interface. Each pilot is an index card (UI element) on a horizontal track with phases: Showrunner -> Casting -> Notes -> Production -> Greenlight. Cards move left-to-right as states advance. Cards with attention flags get red corner markers. Player drags cards manually (reinforces physicality) or clicks "Advance" button (for players who want speed over tactility — support both).

### 3.3 Notes System (Creative Dilemmas)

**Responsibilities:**
- Present creative dilemmas at two stages: Early Notes (post-showrunner) and Final Notes (post-rough-cut)
- Apply player choices to pilot stats (qualityCeiling, commercialFloor, showrunner trust)
- Track cumulative brand axis shifts
- Fire events for other systems (NetworkBrand, ShowrunnerRelationships)

**Core Data Structure:**

```csharp
public class DilemmaData {
    public string id;
    public string contextText;              // The setup paragraph
    public List<DilemmaOption> options;     // 2-3 choices
    public List<GenreTag> applicableGenres; // Which genres this dilemma works for
    public List<string> requiredTags;       // e.g., "antihero", "expensive-shot", "test-audience-problem"
}

public class DilemmaOption {
    public string text;                     // The choice text
    public float qualityCeilingDelta;       // +/- to pilot's quality ceiling
    public float commercialFloorDelta;      // +/- to pilot's commercial floor
    public int showrunnerTrustDelta;        // +/- to showrunner relationship
    public int presidentTrustDelta;         // +/- to network president patience
    public BrandAxisShift brandShift;       // Which axes move and by how much
    public string flavorText;               // Immediate feedback shown to player post-choice
}

public struct BrandAxisShift {
    public int prestige;      // +/- shift on Prestige axis
    public int riskTaking;    // +/- shift on RiskTaking axis
    public int auteur;        // +/- shift on Auteur axis
    public int serialized;    // +/- shift on Serialized axis
}
```

**Dilemma Selection Logic:**

```csharp
public List<DilemmaData> SelectDilemmasForPilot(PilotData pilot, DilemmaPhase phase) {
    // Filter dilemmas by genre
    var pool = DilemmaDB.GetByGenre(pilot.scriptGenre);

    // Filter by phase (some dilemmas are early-notes-only, some are final-notes-only)
    pool = pool.Where(d => d.phase == phase).ToList();

    // Filter by tags (e.g., if pilot has expensive shot in script excerpt, include "expensive-shot" dilemmas)
    pool = pool.Where(d => d.requiredTags.All(tag => pilot.scriptTags.Contains(tag))).ToList();

    // Exclude already-used dilemmas for this pilot
    pool = pool.Where(d => !pilot.completedDilemmaIDs.Contains(d.id)).ToList();

    // Randomly select 2-3 dilemmas
    return pool.OrderBy(_ => Random.value).Take(Random.Range(2, 4)).ToList();
}
```

**Applying Player Choice:**

```csharp
public void ApplyNoteChoice(PilotData pilot, DilemmaOption choice) {
    pilot.qualityCeiling += choice.qualityCeilingDelta;
    pilot.commercialFloor += choice.commercialFloorDelta;

    var showrunner = ShowrunnerDB.Get(pilot.showrunnerID);
    showrunner.trust += choice.showrunnerTrustDelta;

    GameState.presidentPatience += choice.presidentTrustDelta;

    // Brand axis shifts
    NetworkBrand.AdjustAxis(BrandAxis.Prestige, choice.brandShift.prestige);
    NetworkBrand.AdjustAxis(BrandAxis.RiskTaking, choice.brandShift.riskTaking);
    NetworkBrand.AdjustAxis(BrandAxis.Auteur, choice.brandShift.auteur);
    NetworkBrand.AdjustAxis(BrandAxis.Serialized, choice.brandShift.serialized);

    // Fire event for other systems to react
    EventBus.Publish(new NoteGiven { pilotID = pilot.id, dilemmaID = choice.parentDilemmaID, optionIndex = choice.index });

    // Show flavor text to player
    UI.ShowNoteFeedback(choice.flavorText);
}
```

**Content Authoring Workflow:**

Dilemmas are JSON files. Example:

```json
{
  "id": "dilemma_antihero_001",
  "contextText": "The showrunner's pilot script features a protagonist who is a corrupt police detective. In the current draft, the character is magnetic but genuinely reprehensible...",
  "options": [
    {
      "text": "Protect the vision.",
      "qualityCeilingDelta": 5,
      "commercialFloorDelta": -8,
      "showrunnerTrustDelta": 10,
      "presidentTrustDelta": -5,
      "brandShift": { "prestige": 3, "riskTaking": 2, "auteur": 0, "serialized": 0 },
      "flavorText": "The showrunner nods, relieved. The script stays dark."
    },
    {
      "text": "Add one humanizing scene.",
      "qualityCeilingDelta": -2,
      "commercialFloorDelta": 5,
      "showrunnerTrustDelta": -3,
      "presidentTrustDelta": 3,
      "brandShift": { "prestige": 0, "riskTaking": 0, "auteur": 0, "serialized": 0 },
      "flavorText": "The showrunner agrees, grudgingly. 'One scene. That's it.'"
    },
    {
      "text": "Mandate a redemption arc.",
      "qualityCeilingDelta": -12,
      "commercialFloorDelta": 10,
      "showrunnerTrustDelta": -15,
      "presidentTrustDelta": 8,
      "brandShift": { "prestige": -4, "riskTaking": -3, "auteur": 0, "serialized": 0 },
      "flavorText": "The showrunner's face hardens. You've made an enemy."
    }
  ],
  "applicableGenres": ["ProceduralDrama", "SerializedDrama"],
  "requiredTags": ["antihero"],
  "phase": "EARLY_NOTES"
}
```

Writers author dilemmas in JSON. Designers balance the deltas. We build a simple Unity Editor tool to preview dilemmas and validate that delta ranges are sane (no single option giving +50 quality — that is broken).

**Technical Risk Mitigation:**

The content volume is the risk. 200 dilemmas × 3 options = 600 option objects to author and balance. Workflow:
1. Writer drafts 10 dilemmas in Google Docs
2. Designer reviews, assigns deltas
3. Converted to JSON, committed to repo
4. CI pipeline validates JSON schema (catches typos, missing fields)
5. In-game preview tool (Unity Editor) lets designer playthrough a dilemma in isolation

Iteration speed is critical. If dilemma authoring takes more than 30 minutes per dilemma (draft + balance + QA), we will not hit 200. Target: 15 minutes per dilemma once the workflow is smooth.

### 3.4 Landscape Simulation System

**Responsibilities:**
- Track audience trend vectors (6 trends, 0-100 scale each)
- Shift trends each season based on historical events + rival network actions + randomness
- Surface "Industry Signals" (text snippets hinting at trend shifts)
- Simulate rival networks (3 AI rivals, each developing their own slate)

**Core Data Structure:**

```csharp
public class LandscapeState {
    public int serializationAppetite;     // 0-100
    public int antiHeroTolerance;         // 0-100
    public int genreAcceptance;           // 0-100
    public int realitySaturation;         // 0-100
    public int cablePrestigeThreat;       // 0-100
    public int dvrAdoption;               // 0-100

    public List<IndustrySignal> recentSignals;
    public List<RivalNetwork> rivals;
    public int currentSeason;
}

public class IndustrySignal {
    public string headlineText;           // "HBO's new drama draws record 14M for season finale"
    public TrendType affectedTrend;       // Which trend this hints at
    public int projectedShift;            // Hidden from player, but used for actual shift
}

public class RivalNetwork {
    public string name;
    public BrandProfile brandProfile;     // Prestige/Populist, etc.
    public List<RivalSeries> currentSlate;
    public AIStrategy strategy;           // SAFE, AGGRESSIVE, REACTIVE
}
```

**Trend Shift Logic:**

```csharp
public void AdvanceSeason() {
    // Historical events (fixed per season)
    ApplyHistoricalEvent(currentSeason);

    // Rival network influence (dynamic)
    foreach (var rival in rivals) {
        if (rival.currentSlate.Any(s => s.ratings > 15M && s.genre == GenreTag.SerializedDrama)) {
            serializationAppetite += Random.Range(3, 6); // Rival hit boosts trend
        }
    }

    // Random drift (small variance to avoid determinism)
    serializationAppetite += Random.Range(-2, 3);
    antiHeroTolerance += Random.Range(-2, 3);
    // ... repeat for all trends

    // Clamp all trends to 0-100
    serializationAppetite = Mathf.Clamp(serializationAppetite, 0, 100);
    // ...

    // Generate industry signals for next season (probabilistic hints)
    GenerateIndustrySignals();

    currentSeason++;
}

private void ApplyHistoricalEvent(int season) {
    switch (season) {
        case 1:
            cablePrestigeThreat += 8;
            recentSignals.Add(new IndustrySignal { headlineText = "Cable drama wins first major Emmy", ... });
            break;
        case 3:
            serializationAppetite += 20;
            genreAcceptance += 15;
            recentSignals.Add(new IndustrySignal { headlineText = "Serialized mystery becomes #1 show in America", ... });
            break;
        // ... events for seasons 4, 5, 6 (Writers' Strike), 7, 8
    }
}
```

**Rival Network AI:**

Simple strategy-driven AI. Each rival has a strategy (SAFE, AGGRESSIVE, REACTIVE).

```csharp
public class RivalNetworkAI {
    public void DevelopSlate(RivalNetwork rival, List<ScriptData> availableScripts) {
        switch (rival.strategy) {
            case AIStrategy.SAFE:
                // Pick highest commercialFloor scripts, avoid high-risk genres
                var safeScripts = availableScripts.OrderByDescending(s => s.baseCommercialFloor).Take(3);
                rival.Greenlight(safeScripts);
                break;

            case AIStrategy.AGGRESSIVE:
                // Pick highest qualityCeiling scripts, embrace risk
                var boldScripts = availableScripts.OrderByDescending(s => s.qualityCeiling).Take(3);
                rival.Greenlight(boldScripts);
                break;

            case AIStrategy.REACTIVE:
                // Copy whatever worked last season (look at player's hits or other rivals' hits)
                var trendingGenre = DetermineTrendingGenre();
                var copycat = availableScripts.Where(s => s.genre == trendingGenre).Take(3);
                rival.Greenlight(copycat);
                break;
        }
    }
}
```

Rivals do not run full development pipelines (too expensive to simulate 3 × 8 pilots each). Rivals pick 3 scripts, simulate simplified development (no notes, just stat-based outcomes), greenlight 2-3 series, generate ratings. The player sees rival slate announcements and rival ratings, but not rival decision-making. This maintains competitive pressure without exploding simulation cost.

**Performance Consideration:**

Landscape simulation runs once per season (not per frame). The entire `AdvanceSeason()` call completes in <1ms. Trend shifts are simple addition. Rival AI is ~10 conditionals and a sort. No pathfinding, no physics, no complex math. This is not a performance-critical system.

### 3.5 Upfronts System

**Responsibilities:**
- Present player's slate to advertisers (the set-piece climax of each season)
- Calculate ad buyer confidence for each show
- Generate ad revenue commitments
- Handle presentation order and sell line choices

**Core Data Structure:**

```csharp
public class UpfrontsPresentation {
    public List<PilotData> selectedPilots;    // 2-4 pilots player is greenlighting
    public int[] presentationOrder;           // Player-chosen order
    public Dictionary<string, SellLine> sellLines; // pilotID -> sell line choice
}

public enum SellLine { PRESTIGE_PLAY, DEMO_MAGNET, CONVERSATION_STARTER }

public class AdBuyerConfidence {
    public float baseConfidence;              // 0-100, driven by pilot's commercialFloor
    public float presentationBonus;           // +/- based on presentation order and sell line
    public float finalConfidence;             // base + bonus, clamped 0-100
}
```

**Ad Confidence Calculation:**

```csharp
public float CalculateAdConfidence(PilotData pilot, int positionInPresentation, SellLine sellLine) {
    float base = pilot.commercialFloor;

    // Position bonus: leading strong or closing strong both good, middle is neutral
    float positionBonus = 0;
    if (positionInPresentation == 0) positionBonus = 5;  // Lead with strength
    if (positionInPresentation == selectedPilots.Count - 1) positionBonus = 5; // Close strong
    // Middle slots: no bonus

    // Sell line modifier
    float sellLineBonus = 0;
    switch (sellLine) {
        case SellLine.PRESTIGE_PLAY:
            sellLineBonus = pilot.qualityCeiling > 70 ? 8 : -5; // Risky: works if quality is high
            break;
        case SellLine.DEMO_MAGNET:
            sellLineBonus = 3; // Safe, always slight positive
            break;
        case SellLine.CONVERSATION_STARTER:
            sellLineBonus = NetworkBrand.culturalFootprint > 60 ? 10 : 0; // Works if brand supports it
            break;
    }

    // Star power bonus
    float starBonus = pilot.cast.Sum(c => c.starPower) * 0.5f;

    float final = base + positionBonus + sellLineBonus + starBonus;
    return Mathf.Clamp(final, 0, 100);
}
```

**Ad Revenue Calculation:**

```csharp
public float CalculateAdRevenue(PilotData pilot, float adConfidence, TimeSlot slot) {
    float baseRate = 80000f; // $80K per 30-second spot, 2002 dollars
    baseRate *= (1 + (currentSeason * 0.03f)); // 3% inflation per season

    float demoMultiplier = pilot.demo1849Strength > 70 ? 1.5f : (pilot.demo1849Strength > 50 ? 1.2f : 0.9f);
    float slotMultiplier = slot == TimeSlot.Thursday9pm ? 1.3f : (slot == TimeSlot.Friday10pm ? 0.7f : 1.0f);

    float revenuePerEpisode = baseRate * (1 + adConfidence / 100f) * demoMultiplier * slotMultiplier * 14; // 14 ad slots per hour

    return revenuePerEpisode;
}
```

**UI Integration:**

The upfronts are a modal, full-screen sequence. Player sees:
1. **Slate Assembly Screen** — Drag pilots into presentation order, assign sell lines (dropdown per pilot)
2. **Presentation Sequence** — Each pilot presented one at a time. Animated "ad buyer" portrait icons react (interested, skeptical, excited). Ad confidence meter fills. Visual feedback is critical — this is the payoff moment.
3. **Ad Commit Summary** — Total revenue locked in, broken down per show. Player sees the financial consequences of their slate.

The upfronts take 5-7 minutes. No skipping. This is the season finale. Make it feel important.

### 3.6 Season Broadcast & Ratings System

**Responsibilities:**
- Simulate weekly ratings for all greenlit series
- Calculate viewership from commercialFloor + quality + trends + random variance
- Generate mid-season decision points (renewal, cancellation, schedule adjustments)
- Update reputation, revenue, and brand metrics

**Ratings Calculation:**

```csharp
public float CalculateEpisodeViewership(SeriesData series, int episodeNumber) {
    float base = series.commercialFloor; // In millions

    // Quality contribution (quality ceiling from pilot × retention factor)
    float qualityBonus = series.qualityCeiling * 0.15f * GetRetentionFactor(episodeNumber, series.qualityCeiling);

    // Star power contribution
    float starBonus = series.cast.Sum(c => c.starPower) * 0.3f;

    // Time slot value
    float slotBonus = GetTimeSlotBonus(series.timeSlot);

    // Trend alignment (how well does this show fit current audience appetite?)
    float trendBonus = CalculateTrendAlignment(series);

    // Random variance (simulate weekly fluctuations)
    float variance = Random.Range(-1.5f, 1.5f);

    float viewership = base + qualityBonus + starBonus + slotBonus + trendBonus + variance;
    return Mathf.Max(viewership, 0); // Never negative viewership
}

private float GetRetentionFactor(int episode, float quality) {
    if (episode == 1) return 1.0f; // Pilot has full quality impact
    if (episode == 2) return 0.85f; // Natural dropoff
    // Gradually recover if quality > 60
    return quality > 60 ? Mathf.Lerp(0.85f, 0.95f, (episode - 2) / 10f) : 0.85f;
}

private float CalculateTrendAlignment(SeriesData series) {
    float bonus = 0;
    if (series.genre == GenreTag.SerializedDrama) bonus += LandscapeState.serializationAppetite * 0.05f;
    if (series.hasAntiHero) bonus += LandscapeState.antiHeroTolerance * 0.04f;
    // ... check other trend alignments
    return Mathf.Clamp(bonus, 0, 8); // Max +8M from trend alignment
}
```

**Mid-Season Decisions:**

```csharp
public void TriggerMidSeasonDecision(SeriesData series) {
    if (series.currentEpisode == 6) { // Mid-season checkpoint
        if (series.averageViewership < series.projectedViewership * 0.7f) {
            // Show is underperforming
            UI.ShowMidSeasonChoice(series, new[] {
                "Move to a different time slot (credibility cost, might save show)",
                "Grant full-season order anyway (confidence signal, financial risk)",
                "Cancel mid-season (save budget, damage showrunner trust)"
            });
        } else if (series.averageViewership > series.projectedViewership * 1.3f) {
            // Show is overperforming
            UI.ShowMidSeasonChoice(series, new[] {
                "Extend episode order (+$2M cost, capitalize on momentum)",
                "Hold at original order (safe, but might leave money on table)"
            });
        }
    }
}
```

**End-of-Season Metrics Update:**

```csharp
public void EndOfSeasonUpdate() {
    // Calculate total ad revenue from all series
    float totalRevenue = series.Sum(s => s.episodeCount * s.adRevenuePerEpisode);

    // Calculate total production costs
    float totalCosts = series.Sum(s => s.episodeCount * s.productionCostPerEpisode) + developmentOverhead;

    // Operating surplus/deficit
    float surplus = totalRevenue - totalCosts;
    GameState.budget += surplus * 0.5f; // Half goes to next season budget, half to corporate

    // Update President Patience
    float expectedRevenue = GameState.projectedRevenue;
    float revenuePerformance = (totalRevenue - expectedRevenue) / expectedRevenue;
    GameState.presidentPatience += (int)(revenuePerformance * 50);

    // Update Industry Reputation (driven by show quality and critical acclaim)
    float avgQuality = series.Average(s => s.qualityCeiling);
    GameState.industryReputation += (avgQuality > 70 ? 5 : (avgQuality < 50 ? -3 : 0));

    // Update Cultural Footprint (driven by shows that "define the conversation")
    int conversationShows = series.Count(s => s.qualityCeiling > 75 || s.viewership > 12M);
    GameState.culturalFootprint += conversationShows * 3;

    // Clamp all reputation stats to 0-100
    GameState.industryReputation = Mathf.Clamp(GameState.industryReputation, 0, 100);
    GameState.culturalFootprint = Mathf.Clamp(GameState.culturalFootprint, 0, 100);
    GameState.presidentPatience = Mathf.Clamp(GameState.presidentPatience, 0, 100);

    // Check for game over (President Patience <= 0)
    if (GameState.presidentPatience <= 0) {
        TriggerGameOver();
    }
}
```

**Performance Consideration:**

Ratings calculation runs once per episode per series. At peak, the player might have 4 series × 22 episodes = 88 rating calculations per season. Each calculation is ~20 floating-point operations. Total: 1,760 ops, completes in microseconds. Not a bottleneck.

---

## 4. AI/SIMULATION SYSTEMS

### 4.1 Showrunner Relationship Simulation

Showrunners are not dumb NPCs. They remember how the player treated them. Trust accumulates or erodes over multiple projects.

**Core Data:**

```csharp
public class ShowrunnerData {
    public string id;
    public string name;
    public int vision;           // 1-10
    public int craft;            // 1-10
    public int heat;             // 1-10, decays 10% per season without a hit
    public int ego;              // 1-10
    public int reliability;      // 1-10
    public int loyalty;          // 1-10
    public int trust;            // 0-100, player-specific relationship stat

    public TonalPreference tonalPreference; // 4-axis creative preference
    public List<string> projectHistory;     // IDs of pilots/series they've worked on
    public ShowrunnerState state;           // AVAILABLE, ON_PROJECT, BURNED_OUT, DEFECTED_TO_CABLE
}

public enum ShowrunnerState { AVAILABLE, ON_PROJECT, BURNED_OUT, DEFECTED_TO_CABLE }
```

**Trust System:**

Every note the player gives affects trust. Trust affects:
- **Note compliance** — Low-trust showrunners ignore 30% of player notes (the note's effect is reduced)
- **Return probability** — Showrunners with trust > 70 are 80% likely to return with their next project. Trust < 30 = 10% return chance.
- **Public conflicts** — If trust drops below 20 during development, showrunner may publicly clash (generates negative press, hurts network reputation)

**Career Arcs:**

Showrunners evolve over time. After each project:

```csharp
public void UpdateShowrunnerCareer(ShowrunnerData showrunner, SeriesData series) {
    if (series.averageViewership > 10M && series.qualityCeiling > 70) {
        // Hit show: Heat rises, Ego rises
        showrunner.heat = Mathf.Min(showrunner.heat + 2, 10);
        showrunner.ego = Mathf.Min(showrunner.ego + 1, 10);
    } else if (series.averageViewership < 4M) {
        // Flop: Heat drops
        showrunner.heat = Mathf.Max(showrunner.heat - 2, 1);
    }

    // Burnout risk for high-Ego showrunners after 3+ consecutive projects
    if (showrunner.ego > 7 && showrunner.projectHistory.Count >= 3) {
        if (Random.value < 0.2f) {
            showrunner.state = ShowrunnerState.BURNED_OUT;
            showrunner.vision -= 3;
            showrunner.reliability -= 2;
        }
    }

    // Cable poaching (high-Vision showrunners may leave for cable if landscape.cablePrestigeThreat > 60)
    if (showrunner.vision > 8 && LandscapeState.cablePrestigeThreat > 60 && showrunner.loyalty < 5) {
        if (Random.value < 0.25f) {
            showrunner.state = ShowrunnerState.DEFECTED_TO_CABLE;
            // Lost to cable. No longer available.
        }
    }

    // Heat decay (all showrunners lose 10% heat per season without a project)
    if (showrunner.state == ShowrunnerState.AVAILABLE) {
        showrunner.heat = Mathf.Max(showrunner.heat * 0.9f, 1);
    }
}
```

This creates emergent narratives: a trusted showrunner delivers three hits, their Ego spikes, they burn out. The player must decide whether to give them a break or push them into another project. A rising-star showrunner with Vision 9 gets poached by cable. The player feels the loss.

### 4.2 Test Audience Simulation

Test audiences are not just a random number. They are a demographic model.

```csharp
public struct TestAudienceResult {
    public int overallScore;      // 0-100
    public int demo1834Score;     // 0-100
    public int demo3549Score;     // 0-100
    public int demo50PlusScore;   // 0-100
    public List<string> topComments; // Authored flavor text, selected based on score ranges
}

public TestAudienceResult SimulateTestAudience(PilotData pilot) {
    // Overall score driven by commercialFloor + quality, with variance
    int overall = (int)(pilot.commercialFloor * 0.4f + pilot.qualityCeiling * 0.5f + Random.Range(-10, 10));

    // Demo-specific scores (younger demos prefer serialized/risky, older demos prefer episodic/safe)
    int demo1834 = overall;
    if (pilot.genre == GenreTag.SerializedDrama || pilot.genre == GenreTag.SciFiFantasy) demo1834 += 15;
    if (pilot.genre == GenreTag.FamilySitcom || pilot.genre == GenreTag.ProceduralDrama) demo1834 -= 10;

    int demo3549 = overall; // Middle demo: neutral

    int demo50Plus = overall;
    if (pilot.genre == GenreTag.ProceduralDrama || pilot.genre == GenreTag.FamilySitcom) demo50Plus += 10;
    if (pilot.genre == GenreTag.SerializedDrama || pilot.genre == GenreTag.Dramedy) demo50Plus -= 10;

    // Select authored comments based on score
    var comments = new List<string>();
    if (overall < 40) comments.Add("Confusing and slow.");
    if (overall > 70) comments.Add("Best pilot I've seen in years.");
    if (demo1834 > 70 && overall < 50) comments.Add("Finally something that doesn't treat me like I'm stupid.");
    // ... more authored comments

    return new TestAudienceResult {
        overallScore = Mathf.Clamp(overall, 0, 100),
        demo1834Score = Mathf.Clamp(demo1834, 0, 100),
        demo3549Score = Mathf.Clamp(demo3549, 0, 100),
        demo50PlusScore = Mathf.Clamp(demo50Plus, 0, 100),
        topComments = comments
    };
}
```

Test audience results are not deterministic. Same pilot tested twice might score 42 and 48 (variance simulates small sample size). This forces the player to make judgment calls: do I trust a 38 overall when the 18-34 demo scored 71? The game rewards reading the data, not optimizing a single number.

---

## 5. NETWORK BRAND SYSTEM

The player's cumulative decisions create a network identity. Brand is not a cosmetic label. Brand has mechanical weight.

**Core Data:**

```csharp
public class NetworkBrand {
    public int prestige;        // 0-100, starts at 50
    public int riskTaking;      // 0-100, starts at 50
    public int auteur;          // 0-100, starts at 50
    public int serialized;      // 0-100, starts at 50

    public string persona;      // Derived label: "Prestige Boutique", "Mass-Market Juggernaut", etc.
}
```

**Brand Effects on Gameplay:**

```csharp
public class BrandEffects {
    public void ApplyBrandModifiers(NetworkBrand brand, GameState state) {
        // High Prestige (70+)
        if (brand.prestige >= 70) {
            state.highVisionShowrunnerAttractionBonus = 0.2f; // +20% chance to attract Vision 8+ showrunners
            state.criticalScoreBonus = 5;                     // Critics review more favorably
            state.advertiserPayMultiplier = 0.9f;             // Advertisers pay 10% less (prestige = smaller audiences)
        }

        // High Populist (prestige < 30)
        if (brand.prestige <= 30) {
            state.ratingsFloorBonus = 5;                      // +5M floor on all shows
            state.advertiserPayMultiplier = 1.15f;            // Advertisers pay 15% more
            state.highVisionShowrunnerAttractionBonus = -0.3f; // -30% chance to attract top talent
        }

        // High Risk-Taking (70+)
        if (brand.riskTaking >= 70) {
            state.qualityCeilingVariance = 10;                // Quality ceiling +/- 10 variance
            state.firstLookUnmarketableSpecs = true;          // Get access to "unmarketable" specs other networks pass on
            state.presidentPatienceDecayRate = 1.2f;          // President gets nervous faster
        }

        // High Safe (riskTaking < 30)
        if (brand.riskTaking <= 30) {
            state.qualityCeilingCap = 80;                     // Never produce a masterpiece, never produce a disaster
            state.ratingsFloorBonus = 5;
            state.creativeTalentPoolShrink = 0.2f;            // 20% fewer high-Vision showrunners submit
        }

        // High Auteur-Driven (70+)
        if (brand.auteur >= 70) {
            state.showrunnerTrustStartBonus = 15;             // All showrunner relationships start +15 trust
            state.noteResistanceRate = 1.2f;                  // Showrunners resist notes 20% more
            state.budgetOverrunRisk = 1.15f;                  // +15% budget overrun risk
        }

        // High Producer-Driven (auteur < 30)
        if (brand.auteur <= 30) {
            state.budgetOverrunRisk = 0.75f;                  // -25% budget overrun risk
            state.showrunnerVisionContribution = 0.5f;        // Showrunner Vision stat contributes half as much
            // You control the product, but the product has a ceiling
        }

        // High Serialized (70+)
        if (brand.serialized >= 70) {
            state.criticalScoreBonus = 8;
            state.casualViewerAcquisition = 0.8f;             // -20% casual viewer acquisition
            state.dvrTimeshiftBonus = 1.1f;                   // +10% DVR/time-shift viewership
        }

        // High Episodic (serialized < 30)
        if (brand.serialized <= 30) {
            state.casualViewerAcquisition = 1.25f;            // +25% casual viewer acquisition
            state.criticalScoreBonus = -5;
            state.syndicationValue = 1.3f;                    // +30% syndication revenue
        }
    }
}
```

**Brand Persona Labels:**

```csharp
public string DeterminePersona(NetworkBrand brand) {
    if (brand.prestige > 70 && brand.riskTaking > 70) return "Prestige Risk-Taker";
    if (brand.prestige > 70 && brand.auteur > 70) return "Auteur's Haven";
    if (brand.prestige > 70) return "Prestige Boutique";
    if (brand.prestige < 30 && brand.riskTaking < 30) return "Safe Harbor";
    if (brand.prestige < 30 && brand.serialized < 30) return "Mass-Market Juggernaut";
    if (brand.riskTaking > 70 && brand.auteur > 70) return "Bold Auteur Network";
    if (brand.riskTaking > 70) return "High-Wire Act";
    return "Balanced Network"; // Neutral brand
}
```

**UI Visualization:**

Four-axis radar chart displayed in the player's office. Updates at the end of each season. Axes labeled clearly. The chart is not just data viz — it is the player's strategic compass. Players will screenshot this and post it online ("Look at my network's brand profile after 8 seasons").

---

## 6. SAVE SYSTEM DESIGN

### 6.1 Save File Structure

Already covered in Section 2.4. Reiterate key points:

- **One JSON file per playthrough**
- **Version field for migration**
- **Human-readable** (players can examine their save file, modders can edit it)
- **Autosave at end of season** + **3 manual save slots**
- **Corruption handling**: If save fails to load, offer "Load Last Autosave" or "Start New Game." Never crash.

### 6.2 Save Compatibility Strategy

**Pre-1.0 (Early Access):** Breaking changes allowed. Warn players in patch notes.

**Post-1.0:** Save compatibility is law. Every update must support saves from the previous version. Migration scripts handle schema changes.

**Example Migration:**

Version 1.0 saves do not have `culturalFootprint` stat. Version 1.1 adds it. Migration:

```csharp
if (save.version == "1.0") {
    save.networkState.culturalFootprint = CalculateLegacyCulturalFootprint(save.history);
    save.version = "1.1";
}
```

The migration function looks at the player's history (which shows they greenlit, which series were hits) and back-calculates a reasonable culturalFootprint value. The player's progress is preserved.

### 6.3 Cloud Saves (Post-Launch Feature)

Not at launch. Steam Cloud API integration is straightforward but adds complexity. Post-launch, if players request it, add Steam Cloud support. The save system is already file-based, so integrating Steam Cloud is a matter of pointing the save path to Steam's cloud folder. Two days of work, max.

---

## 7. PERFORMANCE BUDGET & OPTIMIZATION STRATEGY

### 7.1 Target Performance

- **60fps on 2019 MacBook Pro** (Intel i5, integrated GPU)
- **1920×1080 resolution**, scalable to 4K
- **Load times < 3 seconds** (save load, scene transition)
- **Memory footprint < 500MB** (this is a text game, not a 3D game)

### 7.2 Performance Profile

This is not a GPU-bound game. This is a CPU-bound data-processing and UI-rendering game.

**CPU Hotspots:**
1. **UI Toolkit layout recalculation** — When 20 script cards update simultaneously, layout recalc can spike. Mitigation: Batch updates, dirty flag layout recalc, avoid per-frame layout changes.
2. **Dilemma selection logic** — Filtering 200 dilemmas by genre/tags/phase. Mitigation: Pre-index dilemmas by genre in a dictionary. O(1) lookup, not O(n) scan.
3. **Ratings simulation** — 88 episode ratings per season. Mitigation: This is 1,760 float ops, completes in microseconds. Not a real bottleneck unless we screw up the math.

**Memory Hotspots:**
1. **Authored content (JSON)** — 200 dilemmas × 1KB each = 200KB. 80 scripts × 2KB each = 160KB. Total authored content: <5MB. Loaded once at startup. No streaming needed.
2. **UI texture atlases** — Script card backgrounds, UI sprites. Target: <20MB total. Use texture atlases to minimize draw calls.
3. **Save files** — Largest save file (season 8, full history) is ~500KB JSON. Compresses to ~50KB gzipped if we want to shrink it.

**GPU Hotspots:**

None. The game is 2D UI. No real-time lighting, no post-processing, no particle effects. The GPU is bored. If we see GPU bottlenecks, something is catastrophically broken.

### 7.3 Optimization Strategy

**Premature optimization is evil. Profile before optimizing.**

Optimization pass happens after vertical slice (month 6). Steps:

1. **Profile the desk interface** — Spawn 20 scripts, drag them around, measure frame time. If frame time spikes above 16ms (below 60fps), identify the cause. Likely culprit: layout recalc. Fix: batch layout updates.

2. **Profile dilemma selection** — Run `SelectDilemmasForPilot()` 1,000 times, measure total time. If total > 100ms, the indexing is broken. Fix: pre-index dilemmas by genre.

3. **Profile save load** — Load a season 8 save 100 times, measure average load time. If average > 3 seconds, JSON deserialization is the bottleneck. Fix: Use Newtonsoft JSON's faster deserializer settings, or cache deserialized data.

4. **Memory profiler** — Run the game for 8 full seasons, check memory usage. If memory grows unbounded, we have a leak. Fix: Hunt down the leak (likely event listeners not unsubscribed).

**Optimization is reactive, not proactive.** Build clean systems first. Profile. Fix what is actually slow. Do not optimize code that runs once per season.

### 7.4 Build Size Budget

Target: <200MB installed size.

Breakdown:
- Engine binaries: ~100MB (Unity runtime)
- Authored content (JSON, text): <5MB
- UI assets (sprites, fonts): <20MB
- Audio (UI sounds, score): <50MB (compressed OGG)
- Code (managed DLLs): <5MB

Total: ~180MB. Comfortable margin under 200MB.

If build size exceeds 250MB, we are doing something wrong (likely uncompressed audio or massive texture atlases). Fix: compress audio, optimize atlases.

---

## 8. PLATFORM CONSIDERATIONS

### 8.1 PC (Windows/Mac/Linux)

**Primary platform.** All development happens here.

**Input:** Mouse + keyboard. The desk interface is designed for mouse drag. Keyboard shortcuts for power users (hotkeys for Pass/Consider/Priority, spacebar to advance text, etc.).

**Resolution scaling:** Support 1920×1080 through 3840×2160. UI Toolkit scales cleanly. Test at 1080p, 1440p, 4K.

**Platform-specific code:** Minimal. Save file path differs (AppData on Windows, ~/Library on Mac, ~/.local on Linux). Unity handles this via `Application.persistentDataPath`. No custom code needed.

### 8.2 Nintendo Switch (Post-Launch Port)

**Feasibility:** High. The game has no complex rendering, no physics, no multiplayer. Switch ports for UI-heavy games are straightforward.

**Input adaptation:** Switch has no mouse. The desk interface must support controller input. Solution: Cursor emulation (left stick moves cursor, A button = click). Not ideal, but functional. Alternatively, redesign the desk for controller (grid-based card selection, D-pad navigation). More work, better UX.

**Performance:** Switch CPU is weaker than a modern PC, but the game is not CPU-heavy. Target 60fps is achievable. If we hit performance issues, reduce particle effects (if any) and simplify UI animations.

**Text rendering:** Switch screen is 720p in handheld mode. The game is text-heavy. Font sizes must be tested on actual hardware. If text is unreadable in handheld, increase base font size and reduce text density per screen.

**Build pipeline:** Unity's Switch export requires a Nintendo dev license. Once we have the license, Switch builds are automated via Unity Cloud Build or local builds.

**Timeline:** Switch port is 1-2 months of work post-PC launch. Not a launch priority. Get the PC version right first.

### 8.3 Mobile (Not Recommended)

The pitch document mentions mobile as "stretch consideration only." I agree. The game is too text-heavy, too complex, and too mouse-centric for mobile. A mobile port would require:

- Complete UI redesign (no mouse, everything touch-based)
- Reduced content density (phone screens are small)
- Simplified systems (mobile players expect shorter sessions)

This is not a port. This is a different game. Do not do this unless the PC version is a breakout hit and a publisher is funding the mobile redesign. Focus on PC/Mac first. Switch second. Mobile never, unless money is on the table.

---

## 9. BUILD PIPELINE & TOOLS

### 9.1 Development Tools

**Unity Editor Extensions:**

1. **Dilemma Authoring Tool** — Custom editor window for previewing and editing dilemmas. Allows designers to:
   - View dilemma text
   - Edit option deltas (quality, commercial, trust, brand axes)
   - Validate delta ranges (flag options with extreme values)
   - Playtest a single dilemma in isolation (mock pilot data)

2. **Script Database Viewer** — Custom editor window for browsing all 80 pilot concepts. View logline, genre, tonal profile, assigned dilemmas. Allows designers to spot gaps (e.g., "We have 12 procedural pilots but only 3 prestige limited series").

3. **Content Validation Tool** — Runs on every build. Checks:
   - All dilemma IDs referenced in scripts exist in DilemmaDB
   - All showrunner IDs referenced in scripts exist in ShowrunnerDB
   - All stat ranges are valid (qualityCeiling 0-100, etc.)
   - No duplicate IDs
   - No orphaned content (dilemmas that are never referenced)

Output: Build fails if validation fails. Forces content hygiene.

**External Tools:**

- **Google Sheets** — Writers draft dilemma text in Google Sheets (easier collaboration than JSON files). Sheets export to CSV, CSV converted to JSON via Python script.
- **Ink Editor** — For event text and rough cut descriptions. Ink's editor is clean and supports branching text well.

### 9.2 Build Pipeline

**Local Builds:**

```bash
# Build PC (Windows x64)
unity -quit -batchmode -projectPath . -buildTarget Win64 -buildPath ./Builds/PC/PILOT.exe

# Build Mac (Intel + Apple Silicon universal binary)
unity -quit -batchmode -projectPath . -buildTarget OSXUniversal -buildPath ./Builds/Mac/PILOT.app
```

**CI/CD (GitHub Actions):**

```yaml
name: Build and Test

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run Unity Tests
        uses: game-ci/unity-test-runner@v2
        with:
          projectPath: .
          testMode: playmode

  build:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Build for PC
        uses: game-ci/unity-builder@v2
        with:
          targetPlatform: StandaloneWindows64
      - name: Upload Build Artifact
        uses: actions/upload-artifact@v2
        with:
          name: PILOT-PC
          path: ./Builds/PC
```

Every push triggers tests. Every tag triggers a full build. Automated. No manual build process.

### 9.3 QA & Testing Strategy

**Unit Tests:**

All simulation logic (ratings calculation, budget math, trend shifts, showrunner fit) is unit tested. Example:

```csharp
[Test]
public void TestRatingsCalculation() {
    var series = new SeriesData { commercialFloor = 5, qualityCeiling = 70, ... };
    float viewership = RatingsSystem.CalculateEpisodeViewership(series, episodeNumber: 1);
    Assert.IsTrue(viewership > 5 && viewership < 20); // Sanity check range
}

[Test]
public void TestShowrunnerFit() {
    var showrunner = new ShowrunnerData { tonalPreference = new TonalProfile { darkLight = 8, ... } };
    var script = new ScriptData { tonalProfile = new TonalProfile { darkLight = 8, ... } };
    int fit = PipelineSystem.CalculateShowrunnerFit(showrunner, script);
    Assert.AreEqual(100, fit); // Perfect fit
}
```

Target: 80% code coverage for all simulation logic. UI code is not unit tested (too much Unity-specific state). Simulation logic is pure C# and must be tested.

**Playtesting:**

- **Week 1-2:** Core loop prototype. Internal playtest (dev team only). Focus: Does the desk feel good?
- **Month 3:** First external playtest (5-10 players). Focus: Is the 5-minute development loop satisfying?
- **Month 6:** Vertical slice playtest (20-30 players). Focus: Does one full season hold attention for 60+ minutes?
- **Month 12:** Alpha playtest (100+ players, Steam closed beta). Focus: Content variety, balance, pacing over 8 seasons.
- **Month 18:** Beta playtest (open to all Steam wishlisters). Focus: Polish, bug squashing, final balance pass.

Playtesting is not QA. Playtesting is design validation. QA (bug hunting) happens in parallel starting at month 9.

---

## 10. TECHNICAL RISK ASSESSMENT

### 10.1 High-Risk Areas

| Risk | Severity | Mitigation |
|---|---|---|
| **Notes System feels like multiple-choice test** | CRITICAL | Authored content quality + playtesting. If playtesters optimize instead of feeling torn, rebalance dilemmas. |
| **Authored content volume** (200 dilemmas, 80 pilots) | HIGH | Modular content pipeline. Writers draft in Sheets, export to JSON. Content validation tools catch errors early. |
| **Desk UI overwhelm** | HIGH | Visual hierarchy design. Skim-speed defaults. Deep info on opt-in. Playtest with 15-20 scripts, measure time-to-triage. |
| **Pipeline micro-management tedium** | HIGH | Attention Flag system. Only surface projects that need decisions. Let stable projects run on autopilot. |
| **Upfronts anticlimactic** | MEDIUM | Make it a performance. Animated reactions, tension-building presentation sequence. Playtest upfronts in isolation. |
| **Late-game stagnation** | MEDIUM | Season 6 (strike) disrupts patterns. Season 7 (fragmentation) kills dominant strategies. Showrunner career arcs create emergent drama. |
| **Save file corruption** | LOW | Robust error handling. JSON schema validation on load. Offer "Load Last Autosave" fallback. |
| **Performance issues** | LOW | Game is not GPU/CPU heavy. Profile at month 6. Fix actual bottlenecks, not imagined ones. |

### 10.2 Risk Prioritization

**Address these in order:**

1. **Notes System** — Core mechanic. Must work. Prototype early (month 1). Playtest dilemmas in isolation. Iterate based on feedback.
2. **Content Pipeline** — The game needs 150K-200K words of authored content. Get the pipeline right early or drown in JSON hell. Build authoring tools by month 2.
3. **Desk UI** — The 30-second loop. Must feel good. Prototype by week 4. Iterate until triage is fast and satisfying.
4. **Pipeline Management** — The 5-minute loop. Prototype by month 3. Test attention flag system to avoid busywork.
5. **Upfronts** — The season climax. Prototype by month 4. Needs to feel like a set-piece moment, not a menu.

Everything else is lower risk or mitigated by profiling and iteration.

---

## 11. DEVELOPMENT MILESTONES (TECHNICAL)

### 11.1 Milestone 1: Core Loop Prototype (Month 1-3)

**Goal:** Prove the 30-second and 5-minute loops work.

**Deliverables:**
- Desk UI with 10 dummy scripts
- Triage actions (Pass/Consider/Priority) functional
- Basic development pipeline (assign showrunner, cast, give 1 note)
- 5 authored dilemmas (real content, not placeholders)
- Pilot quality calculation (simple formula)

**Tech Milestones:**
- Unity project setup (UI Toolkit, input system, event bus)
- Data layer (ScriptData, PilotData, DilemmaData structures)
- Save/load basic state (scripts + pilots only)

**Success Criteria:**
- Playtester can triage 10 scripts in <3 minutes
- Playtester can develop 1 pilot from script to rough cut in <5 minutes
- Playtester reports the notes feel like creative decisions, not stat optimization

### 11.2 Milestone 2: Vertical Slice (Month 4-6)

**Goal:** One full playable season. Desk -> Development -> Upfronts -> Season Broadcast -> Metrics Update.

**Deliverables:**
- Desk with 15 scripts per pitch season
- Pipeline with 8 simultaneous pilots in development
- 20 authored dilemmas
- Upfronts presentation sequence (full UI, ad confidence, revenue calculation)
- Season broadcast (weekly ratings for 2 series, 13 episodes each)
- Network brand system (4 axes tracked, radar chart displayed)
- Landscape simulation (3 trend vectors active, 1 historical event)

**Tech Milestones:**
- Full state machine implementation (scripts -> pilots -> series)
- Upfronts mini-game (presentation order, sell lines, ad buyer reactions)
- Ratings simulation (weekly viewership calculation, mid-season decisions)
- Save/load full season state

**Success Criteria:**
- Playtester completes 1 full season in 60 minutes
- Playtester reports the upfronts feel climactic
- Playtester sees their network brand shift based on decisions
- No critical bugs (crashes, soft locks, data corruption)

### 11.3 Milestone 3: Alpha Build (Month 7-12)

**Goal:** 4 seasons playable. Core systems complete. Content library 50% filled.

**Deliverables:**
- 40 pilot concepts authored
- 100 dilemmas authored
- 4 seasons of landscape events
- Rival network AI (3 rivals, simplified development)
- Showrunner career arcs (trust system, poaching, burnout)
- Test audience simulation (demographic breakdown, authored comments)
- Mid-season decisions (renewal, cancellation, schedule moves)

**Tech Milestones:**
- Content authoring tools (dilemma editor, script database viewer)
- Content validation pipeline (CI checks for orphaned IDs, invalid stats)
- Showrunner relationship system
- AI rivals (simplified slate generation)
- Full save/load (all systems)

**Success Criteria:**
- Playtester completes 4 seasons without major bugs
- Playtester reports content variety (dilemmas do not feel repetitive)
- Playtester sees emergent stories (showrunner burnout, rival hits, landscape shifts)
- Unit tests pass (80% code coverage for simulation logic)

### 11.4 Milestone 4: Beta Build (Month 13-18)

**Goal:** 8 seasons playable. Content library 100% filled. Polish pass.

**Deliverables:**
- 80 pilot concepts authored
- 200 dilemmas authored
- 8 seasons of landscape events (including Writers' Strike, streaming whispers)
- End-of-career retrospective (narrator summarizes player's legacy)
- Audio implementation (UI sounds, ambient office audio, score)
- Juice pass (UI animations, transitions, polish)

**Tech Milestones:**
- Audio integration (DOTween for UI animations, Unity Audio for sound)
- Retrospective system (career evaluation, "where are they now" for shows/showrunners)
- Final balance pass (ratings formulas, budget economy, trend vectors)
- Localization prep (string tables, if we are localizing)

**Success Criteria:**
- Playtester completes 8 seasons, reports satisfying ending
- Playtester reports the game feels polished (no janky UI, smooth transitions)
- No critical bugs. No save corruption. No balance exploits.
- Steam closed beta (100+ testers) reports positive overall experience

### 11.5 Milestone 5: Ship (Month 19-24)

**Goal:** Launch on Steam (PC/Mac).

**Deliverables:**
- Final bug fixes
- Steam store page (screenshots, trailer, description)
- Press kit (key art, GIFs, fact sheet)
- Day-one patch readiness (if critical bugs found post-launch)

**Tech Milestones:**
- Final performance pass (profile, optimize hotspots)
- Build pipeline hardened (automated Steam upload via Steamworks SDK)
- Analytics integration (optional, only if we want usage data — not required)

**Success Criteria:**
- Game ships on Steam
- No launch-day crashes
- Metacritic user score >7.0 (if applicable)
- Players post screenshots of their network brand profiles on social media (free marketing)

---

## 12. POST-LAUNCH TECHNICAL ROADMAP

### 12.1 Post-Launch Support (Month 1-3 Post-Ship)

**Focus:** Bug fixes, balance patches, QOL improvements.

**Deliverables:**
- Patch 1.1: Critical bug fixes (anything that blocks progression)
- Patch 1.2: Balance adjustments (if specific strategies are too dominant)
- Patch 1.3: QOL improvements (based on player feedback — faster text skip, better tooltips, etc.)

### 12.2 Post-Launch Content (Month 4-6 Post-Ship)

**Focus:** New content (if the game sells well).

**Potential DLC:**
- **"The Streaming Wars" expansion** — Seasons 9-12, set in 2011-2015. Streaming disrupts everything. New mechanics: binge-release strategy, international markets, shorter seasons.
- **"The Golden Age" scenario** — Alternate start in 1999, play through the entire 2000s-2010s arc with different historical events.
- **Modding support** — Expose content JSON files, allow players to author custom dilemmas and pilots. Community-generated content extends the game's lifespan.

### 12.3 Switch Port (Month 6-8 Post-Ship)

If the game sells >50K copies on PC, greenlight the Switch port. 1-2 months of work (controller input, performance tuning, certification).

---

## 13. TEAM & RESOURCE REQUIREMENTS

### 13.1 Minimum Viable Team

**Solo dev:** Possible, but 24+ months. You are the programmer, designer, writer, and QA. Brutal but doable.

**Two-person team (recommended):**
- **Programmer/Designer** — Systems implementation, gameplay design, tools development
- **Writer/Designer** — Content authoring (dilemmas, scripts, events), narrative design, playtesting

**Three-person team (comfortable):**
- **Programmer** — Systems implementation, tools, build pipeline
- **Designer** — Gameplay design, balance, playtesting coordination
- **Writer** — Content authoring (200 dilemmas, 80 pilots, event text)

**Four-person team (ideal):**
- Add a **UI/UX Designer** — The game lives or dies on the desk UI and whiteboard interfaces. A dedicated UI designer speeds up iteration.

### 13.2 External Contractors (As Needed)

- **Audio designer** — UI sounds, ambient audio, score. Budget: $3K-$8K for full audio package.
- **Key artist** — Hero image, Steam capsule art. Budget: $1K-$3K.
- **QA testers** — 2-3 testers for final beta pass. Budget: $2K-$5K.

### 13.3 Budget Estimate (Indie Scale)

**Full development cost (18-24 months, 2-person team):**

- Salaries: $120K-$200K (depends on location, self-funded vs. salary)
- Tools/software: $1K (Unity, Photoshop, Ink, misc licenses)
- Audio: $5K
- Art: $3K
- QA: $3K
- Marketing (Steam ads, trailer production): $5K
- **Total: $137K-$216K**

If self-funded and living lean, this is doable. If seeking publisher funding, this is a mid-tier indie budget.

---

## 14. CLOSING TECHNICAL NOTES

### 14.1 What Could Go Wrong

**The Notes System does not land.** If players optimize instead of feeling the weight of creative decisions, the game is a spreadsheet, not an experience. Mitigation: Authored content quality is non-negotiable. Every dilemma must be written by someone who understands the dramatic stakes. Playtesting is the only way to validate this. If early playtesters report the notes feel like a quiz, iterate until they do not.

**Content authoring takes longer than expected.** 200 dilemmas is a lot of writing. If the content pipeline is clunky, authoring will bottleneck development. Mitigation: Build the tools early. The Dilemma Authoring Tool and content validation scripts are not optional. They are the difference between shipping on time and drowning in JSON hell.

**The game is too niche.** A text-heavy management sim about TV development is not a mass-market product. Mitigation: Embrace the niche. The TV-industry audience is passionate and vocal. Market to them directly (Twitter, Reddit, TV podcasts). The game does not need to sell 500K copies to succeed. 20K-50K copies at $20 is a profitable indie game.

### 14.2 What Could Go Right

**The TV-industry audience amplifies the game.** If real showrunners, writers, and development execs play the game and tweet about it, the marketing reach explodes. Mitigation: Seed early builds to TV industry folks. A single tweet from a showrunner with 50K followers is worth $10K in marketing spend.

**The Notes System becomes the GIF.** If the moment of hovering over a dilemma — torn between protecting creative vision and chasing commercial viability — resonates, players will screenshot it and share it. The game's marketing writes itself. Mitigation: Make the UI screenshottable. The desk, the whiteboard, the radar chart — these are share-worthy images.

**The game becomes a modding platform.** If we expose the content JSON and allow players to author custom dilemmas, the community extends the game's lifespan indefinitely. Mitigation: Plan for moddability from day one. Keep content in external JSON files, not embedded in code. Document the data schema. A modding community is free DLC.

### 14.3 Final Architecture Validation Checklist

Before starting implementation, validate:

- [ ] The core loop (triage -> develop -> notes -> upfronts -> season) is fully specified with no "TBD" gaps.
- [ ] The data structures (ScriptData, PilotData, DilemmaData, etc.) are defined and can represent all required gameplay states.
- [ ] The event bus architecture is agreed upon and understood by the team.
- [ ] The save system can serialize/deserialize the full game state without data loss.
- [ ] The content authoring pipeline (Google Sheets -> JSON -> Unity) is tested and works.
- [ ] The performance budget (60fps on 2019 MacBook Pro) is realistic given the UI complexity.
- [ ] The team has the skills to implement this (C#, Unity UI Toolkit, JSON serialization).
- [ ] The budget and timeline (18-24 months) are realistic given the team size.

If any item is unchecked, address it before writing code. Architecture mistakes compound. Get it right on paper first.

---

## 15. IMPLEMENTATION PRIORITY

Day 1, start here:

1. **Set up Unity project** — UI Toolkit, input system, folder structure.
2. **Build the event bus** — 50 lines of code. Foundation of the architecture.
3. **Prototype the desk UI** — 5 script cards, draggable, triage buttons. Get the feel right.
4. **Author 3 dilemmas** — Real content, not placeholders. Test the Notes System concept.
5. **Build the dilemma presentation UI** — Show context text, 3 options, apply deltas on click.

These 5 tasks prove the game can work. If the desk feels good and the dilemmas feel like real choices, the game is viable. Everything else is iteration.

---

## FINAL WORD

This game is shippable. The systems are not novel — state machines, event buses, data-driven content. The complexity is in the authored content volume and the UI design. The technical architecture is straightforward. The design risk is whether the Notes System lands emotionally. That is a playtesting problem, not a technical problem.

Build the desk. Build the notes. Build the pipeline. Profile. Optimize what is actually slow. Ship the game.

The hardest part is not the code. The hardest part is writing 200 dilemmas that make players feel the weight of being a gatekeeper. If you can do that, the game works. If you cannot, no amount of clean architecture saves it.

Now go build it.

-- BYTE
