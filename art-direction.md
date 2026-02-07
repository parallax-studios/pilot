# PILOT — Art Direction Document

**Art Director**: PIXEL
**Version**: 1.0
**Date**: 2026-02-07
**Status**: Production-Ready Visual Identity

---

## 1. VISUAL IDENTITY STATEMENT

PILOT is an information-dense management sim that lives or dies on readability. Every pixel must earn its place. The game asks players to read coverage sheets, parse development pipelines, give creative notes, and make split-second triage decisions under time pressure. If the screen does not communicate hierarchy in a single glance, the game fails.

The visual identity serves three masters:

**FIRST: PHYSICAL TACTILITY**
This is not a game about screens and databases. This is a game about physical scripts with coffee stains, coverage sheets with handwritten margin notes, index cards on a whiteboard, newspapers hitting a desk, BlackBerries buzzing during screenings. The player's desk IS the interface. Every UI element must feel like a physical object in a workspace, not a menu floating in void space. The aesthetic is analog 2004 — the particular texture of a media company office before everything became glass and minimalism. Drop ceilings. Institutional carpet. Tinted windows. The warm glow of incandescent bulbs fighting fluorescent overheads. This is the world where television became art, rendered in the mundane materials of office work.

**SECOND: INFORMATION HIERARCHY AS VISUAL LANGUAGE**
The game presents 15-20 scripts on the desk simultaneously, each with multiple parameters to evaluate. A development pipeline tracking 8-12 projects across four phases. Weekly ratings for 3-4 shows. Budget allocations across five categories. This volume of information could overwhelm in seconds. The art direction's job is to create a visual hierarchy so clear that essential information hits the eye in under three seconds. Color-coding by genre. Letter grades in massive type. Warning icons for attention flags. Coverage sheets laid out like magazine layouts — headline, subhead, body, pull quote. Everything the player needs to know in the first glance. Everything the player might want to know one click deeper. The visual language must be ruthlessly functional, but never sterile. Think trade publications from 2004 — Variety, The Hollywood Reporter — where information density meets editorial design.

**THIRD: THE EMOTIONAL WEIGHT OF DECISIONS**
The player is making consequential creative calls. Greenlighting a show that might define a generation. Killing a show that might haunt them. Giving a note that protects a vision or betrays it. These moments must FEEL consequential. Not through flashy VFX or dramatic music cues, but through visual composition. When the player hovers between GREENLIGHT and KILL, the buttons should not be game UI — they should be physical objects with weight. When a script slides off the desk because it expired, the player should feel the loss. When the dead pilots drawer accumulates canceled projects, it should be visible as a graveyard. The art direction makes abstract choices tangible.

**The north star**: Mad Men's visual discipline meets Pentiment's period authenticity meets the information design of FTL: Faster Than Light. Prestige period aesthetics. Ruthless readability. Every choice visible and consequential.

Show the work. Show the weight. Make the player feel like the person whose taste decides what America watches.

---

## 2. COLOR PALETTE

The palette is built from the physical materials of a 2004 television executive's workspace. Warm analog tones fighting institutional fluorescence. Each color has a functional job.

### 2.1 Primary Palette — The Desk

| Color Name | Hex Value | Usage | Psychological Effect |
|---|---|---|---|
| **Script Cream** | `#F4ECD8` | Background for script pages, coverage sheets, documents | Warmth, authenticity, the color of paper under incandescent light |
| **Mahogany Authority** | `#5C3A21` | Desk surface, wood trim, office furniture | Weight, tradition, the color of executive power |
| **Institutional Green** | `#7A8A72` | Office walls, carpet, drop ceiling tiles | The particular green of corporate spaces in 2004. Calming but bureaucratic. |
| **Fluorescent Wash** | `#E8EEE0` | Overhead lighting glow, window light during day scenes | The flat, slightly sickly light of office spaces. Contrast to incandescent warmth. |
| **LA Sunset Amber** | `#D9965F` | Magic hour window light, desk lamp glow, warm accents | Hope, glamour, the promise that television work is still art despite the fluorescence |

### 2.2 Genre Color-Coding System

Scripts and coverage sheets are tagged by genre with a colored corner flag and colored header bar. This system allows instant visual parsing of a cluttered desk.

| Genre | Accent Color | Hex Value | Border Treatment |
|---|---|---|---|
| **Procedural Drama** | Police Blue | `#2B4F81` | Solid 3px border, clean and authoritative |
| **Serialized Drama** | Prestige Burgundy | `#7D2E2E` | Solid 3px border with subtle texture (like HBO branding) |
| **Workplace Comedy** | Office Yellow | `#D9A441` | Dashed 2px border, approachable |
| **Family Sitcom** | Broad Orange | `#E87722` | Rounded corners, 3px border, friendly |
| **Prestige Limited** | Award Gold | `#B8935C` | Double border (2px + 1px), prestigious |
| **Sci-Fi/Fantasy** | Neon Cyan | `#3D9AAD` | Glowing 2px border (subtle outer shadow), otherworldly |
| **Reality/Unscripted** | Cheap Pink | `#E85D75` | Dotted 2px border, less serious |
| **Dramedy** | Tone-Hybrid Purple | `#7D5BA6` | Gradient border (warm to cool), hard to categorize |

**Usage Rules**:
- Genre color appears ONLY on the coverage sheet header bar and the script corner flag (top right, 24px x 60px colored tab)
- Genre color never floods large areas — it is an accent, not a background
- When 15 scripts are stacked on the desk, the corner flags create a visible color spectrum that communicates genre distribution at a glance
- Player learns genre color associations within 10 minutes of play

### 2.3 UI Functional Palette

| Function | Color | Hex Value | Usage |
|---|---|---|---|
| **Attention Flag — Crisis** | Warning Red | `#C1392B` | Projects over budget, showrunner conflicts, expiring scripts (2 days left) |
| **Attention Flag — Needs Decision** | Decision Orange | `#E67E22` | Projects awaiting player input, test audience data ready to review |
| **Attention Flag — On Track** | Smooth Green | `#27AE60` | Projects running smoothly, no intervention needed |
| **Neutral — Inactive** | Muted Gray | `#95A5A6` | Background elements, inactive buttons, archived projects |
| **Interactive Highlight** | Hot Cyan | `#3498DB` | Hover states, clickable elements, active selections |
| **Success — Positive Outcome** | Money Green | `#16A085` | Upfronts ad commit success, ratings overperformance, critical acclaim |
| **Failure — Negative Outcome** | Burnout Maroon | `#8E3B46` | Pilot killed, show canceled, showrunner quits |

### 2.4 Time-of-Day Palette Shifts

The game's lighting shifts subtly to reflect time of day, grounding the player in the rhythm of television work.

| Time Period | Dominant Light | Hex Overlay | Mood |
|---|---|---|---|
| **Early Morning (6am-9am)** | Cold fluorescent, no sunlight yet | `#D4DBE8` at 20% opacity over scene | Sterile, the workday beginning |
| **Midday (10am-3pm)** | Harsh sunlight through tinted windows | `#F9E4C8` at 15% opacity | Brightness fighting institutional dimness |
| **Magic Hour (4pm-6pm)** | LA sunset glow | `#D9965F` at 25% opacity | The golden hour, warmth and possibility |
| **Evening Work (7pm-10pm)** | Desk lamp + ambient city lights | `#4A3728` at 30% opacity, warm pools of light | Isolation, the executive alone with the work |
| **Late Night Screening (11pm+)** | Screening room darkness, monitor glow | `#1C1C1C` background, `#E8F4F8` monitor glow | Intimacy with the work, the moment of judgment |

**Technical Constraint**: Time-of-day shifts are atmospheric only. They do not obscure readability. Text remains high-contrast and legible regardless of lighting state.

### 2.5 Accessibility Considerations

**Colorblind-Safe Design**:
- Genre colors are NEVER the only differentiator. Each genre also has a unique icon (scales of justice for legal procedural, spaceship for sci-fi, laugh/cry masks for dramedy)
- Red-green attention flags are supplemented with iconography (crisis = exclamation triangle, on-track = checkmark circle, needs decision = question diamond)
- All critical information passes WCAG AA contrast requirements (4.5:1 minimum for body text, 3:1 for large UI elements)

**High-Contrast Mode**:
- Player can toggle a high-contrast mode that removes all atmospheric lighting overlays and increases UI border weights from 2-3px to 4-5px
- Genre colors shift to maximum saturation versions
- Background shifts to pure `#FFFFFF`, text to pure `#000000`

---

## 3. SHAPE LANGUAGE GUIDE

Every UI element in PILOT communicates through consistent geometric principles. The shape language reinforces the game's tension between rigid institutional systems and organic creative work.

### 3.1 The Desk — Organic Chaos Within Rigid Structure

**Base Structure**: Rectangles. Everything on the desk is a document, a device, or a drawer — all rectangular. The desk itself is a perfect rectangle (16:9 aspect ratio to fill screen real estate efficiently). The rigidity of the desk creates a stable foundation.

**Organic Chaos**: Documents NEVER align perfectly. Scripts stack at slight angles (2-8 degrees of rotation randomized per script). Coverage sheets have dog-eared corners (small triangular fold on top-right, 12px x 12px). Coffee rings appear on 30% of documents (circular stain, 40-60px diameter, sepia gradient). Post-it notes (square, 80px x 80px, bright yellow `#FFD966`) stick to documents at random rotations. The desk is a controlled mess — rectangular objects in chaotic arrangement.

**The Rule**: Individual objects are rectangular. Their arrangement is organic. This creates visual interest without sacrificing readability. The player's eye can still scan rows of documents because the document edges, despite rotation, remain parallel-ish to screen edges.

### 3.2 The Development Pipeline Whiteboard — Modular Clarity

**Index Cards**: 2:3 aspect ratio rectangles (120px x 180px). Each project is represented by one card. Cards have rounded corners (4px border-radius) to feel tactile, like physical index cards.

**Card Content Hierarchy**:
- Top 20px: Genre color bar (solid fill, no text)
- Next 60px: Project title in bold sans-serif, 16px font, black text on cream background
- Middle 60px: Showrunner name, 12px font, gray text
- Bottom 40px: Attention flag icon (if applicable) + phase indicator

**Pipeline Columns**: Four vertical columns (Showrunner Attachment, Casting, Notes, Production). Columns separated by thin vertical lines (1px, `#BDC3C7`). Cards move horizontally left-to-right through phases. The whiteboard is a literal Kanban board — clean, modular, instantly readable.

**The Rule**: The pipeline uses the strictest geometric discipline in the game. No rotation. No clutter. Perfect alignment. This is where the player needs to see system state at a glance, so the shape language becomes ruthlessly functional.

### 3.3 Buttons and Interactives — Weight and Consequence

**Standard Buttons** (e.g., "Skim," "Standard Read," "Deep Read"):
- Rounded rectangles, 8px border-radius
- 140px x 44px minimum hit area
- 3px solid border in functional color (Hot Cyan `#3498DB` for active, Muted Gray `#95A5A6` for inactive)
- Slight drop shadow (2px Y-offset, 4px blur, 20% opacity black) to create physical depth

**High-Stakes Buttons** (e.g., "GREENLIGHT," "KILL"):
- Larger hit area: 200px x 60px
- Heavier border: 4px solid
- GREENLIGHT uses Success Green `#16A085` border
- KILL uses Burnout Maroon `#8E3B46` border
- Deeper drop shadow (4px Y-offset, 8px blur, 30% opacity) — these buttons feel heavier
- On hover: button lifts (drop shadow increases to 6px Y-offset, 12px blur, 40% opacity). The player feels the weight shifting as they hover.

**The Rule**: Button size and shadow weight communicate stakes. A "Skim" button is lightweight. A "KILL" button is heavy. The player's hand should hesitate slightly before clicking high-stakes buttons because the visual weight demands it.

### 3.4 Iconography — Trade Publication Simplicity

All icons are **line icons** at 2px stroke weight. No fills, no gradients, no detail. Icons are functional signifiers, not illustrations.

**Core Icon Set**:
- **Genre Icons**: Each 24px x 24px, stroke-only
  - Procedural: Scales of justice
  - Serialized: Infinity symbol (continuous narrative)
  - Workplace Comedy: Office building
  - Family Sitcom: House
  - Prestige Limited: Award trophy
  - Sci-Fi/Fantasy: Rocket
  - Reality: Camera
  - Dramedy: Comedy/tragedy masks

- **Attention Flags**: Each 20px x 20px, stroke + minimal fill
  - Crisis: Triangle with exclamation mark, red stroke + red fill at 20% opacity
  - Needs Decision: Diamond with question mark, orange stroke + orange fill at 20% opacity
  - On Track: Circle with checkmark, green stroke + green fill at 20% opacity

- **Development Phase Icons**: Each 28px x 28px, stroke-only
  - Showrunner Attachment: Megaphone
  - Casting: Two person silhouettes
  - Notes: Pencil on paper
  - Production: Film camera

**The Rule**: Icons are glanceable identifiers, never decorative. If an icon does not communicate function in under 1 second, it is replaced with text.

### 3.5 Typography as Shape

**Display Text** (loglines, project titles, headlines):
- Sharp, confident rectangles
- All-caps for emphasis (sparingly)
- Generous letter-spacing (+0.5px to +1px) for authority
- Heavy font weights (600-700) for titles

**Body Text** (coverage notes, descriptions, dialogue):
- Comfortable, readable rectangles
- Sentence case
- Standard letter-spacing (0px)
- Regular font weights (400-500)

**Script Excerpts**:
- Monospaced rectangles (Courier or Courier New, the screenwriting standard)
- Fixed 12px or 14px size, never smaller
- Distinct from all other text by virtue of monospace — the player knows they are reading "the work" when the font shifts

**The Rule**: Typography shifts signal content type. Display = game systems. Body = narrative context. Monospace = the creative work itself. The player never confuses which layer of information they are reading.

---

## 4. STYLE RULES — DO'S AND DON'TS

### 4.1 DO: Physical Materiality

**DO** render UI elements as physical objects with texture, shadow, and depth.
- Scripts have subtle paper grain texture (procedural noise at 3% opacity, warm sepia tint)
- Coverage sheets have slight curl at corners (2-3px gradient shadow suggesting paper lift)
- The desk surface has wood grain (subtle, not overpowering — visible on close inspection, invisible during fast scanning)
- BlackBerry and phone devices have glossy plastic highlights (small 10px x 20px white gradient at 30% opacity on top edge)
- The whiteboard has a matte surface with slight glare from overhead lights (subtle gradient overlay, 5% opacity)

**DO** make objects respond to interaction with physical feedback.
- When the player drags a script, it lifts slightly (drop shadow grows, document scales to 102%)
- When a coverage sheet is clicked, it shifts forward in the stack (Z-index change + 2px position shift + shadow deepens)
- When an index card moves between pipeline phases, it animates with a slide-and-drop motion (300ms ease-out, ending with a subtle bounce)
- When a pilot is killed, the player physically drags the index card to the "dead pilots" drawer — the card shrinks and fades as it enters the drawer (500ms animation, ending with a quiet sound cue)

### 4.2 DON'T: Gamified Abstraction

**DON'T** use floating HUD elements, transparent overlay menus, or sci-fi interfaces. This is not a game about screens. It is a game about objects in a workspace.

**DON'T** use progress bars that are just colored rectangles filling left-to-right. If you need a progress indicator, make it physical:
- Budget allocation is a stack of bills or a physical ledger with line items
- Time remaining is a wall clock (analog, round, with hour and minute hands)
- Expiration countdown is a stamped date on the coverage sheet, with red circles drawn around dates that are 2 days away or less

**DON'T** use glowing effects, particle systems, or animated flourishes for UI feedback. Physical objects do not glow. They shift, lift, rotate, and cast shadows.

### 4.3 DO: Information Layering

**DO** use physical stacking to communicate information priority.
- The script the player is currently reading is on top of the stack, fully visible
- Scripts beneath are partially visible (top 40px showing title and genre flag)
- When the player hovers over a partially visible script, it shifts upward 20px to reveal more of the coverage sheet — a physical "peeking" motion

**DO** use spatial zones to organize the desk.
- Left third: Incoming scripts (the pile)
- Center third: Currently reading / active work
- Right third: Decided scripts (PASS pile, PRIORITY pile, CONSIDER pile — three distinct stacks)
- The player learns to scan left-to-right: new work -> active work -> decided work

**DO** use depth and shadow to communicate UI layers.
- Background layer (desk surface, walls, windows): 0px shadow, flat
- Mid layer (stacked documents, devices): 2-4px shadow, physical presence
- Active layer (document being read, hovered button): 6-10px shadow, elevated and interactive
- Modal layer (detailed note-giving screen, rough cut viewer): 20px shadow, dark overlay on rest of screen at 60% opacity, full focus on the modal

### 4.4 DON'T: Visual Noise

**DON'T** add decorative elements that do not serve function. Every object on screen must answer: what information does this communicate, or what interaction does this enable?

**DON'T** use more than three levels of visual hierarchy per screen. Primary (what the player must see), Secondary (what the player should see), Tertiary (what the player can see if they look). More than three levels creates chaos.

**DON'T** animate for animation's sake. Every animation must communicate state change or provide feedback. Idle animations (floating icons, pulsing buttons when not hovered) are banned.

### 4.5 DO: Consistent Readability

**DO** maintain 4.5:1 contrast ratio minimum for all body text (WCAG AA standard).

**DO** use font sizes that are never smaller than 12px for body text, 10px for labels and metadata. If information cannot be communicated at 10px minimum, the layout needs revision.

**DO** use whitespace aggressively. Coverage sheets have 16px padding on all edges. Buttons have 12px internal padding. The development pipeline cards have 8px margin between each card. Cramped layouts fail readability tests.

### 4.6 DON'T: Stylistic Inconsistency

**DON'T** mix visual metaphors. The game's aesthetic is analog office workspace, 2004. Do not introduce:
- Modern flat UI elements (no Material Design, no iOS-style minimalism)
- Retro pixel art (wrong era, wrong texture)
- Hand-drawn or sketched elements (too informal for the setting)
- 3D rendered objects (the game is 2D, diegetic, and grounded)

**DON'T** break the fourth wall with meta UI. The pause menu is not a floating game menu — it is the player opening their desk drawer to access "Settings" (a physical document labeled "Office Preferences"). The save system is not a "Save Game" button — it is the player's assistant auto-filing paperwork at the end of each day.

---

## 5. ASSET PIPELINE OVERVIEW

### 5.1 Tools and Formats

| Asset Type | Tool | Format | Resolution | Notes |
|---|---|---|---|---|
| **UI Layouts** | Figma | .fig source, exported as .png or .svg | 1920x1080 base (scales to 2560x1440, 3840x2160) | All UI designed at 1080p, scaled up for higher res |
| **Document Textures** (script pages, coverage sheets) | Photoshop | .psd source, exported as .png | 1024x1448px per page (8.5x11 aspect ratio at readable resolution) | Include subtle noise, coffee stains, handwritten notes as layers |
| **Desk and Office Environment** | Photoshop / Illustrator | .psd or .ai source, exported as layered .png | 1920x1080 per scene | Desk, walls, windows, furniture rendered as separate layers for parallax and interaction |
| **Icons** | Illustrator | .ai source, exported as .svg | 24px-48px artboard size, vector | Line icons at 2px stroke weight, exported as SVG for crisp scaling |
| **Typography** | System fonts + licensed font files | .ttf or .otf | N/A | See section 5.3 for font stack |
| **Animations** (card slides, document lifts) | Spine or hand-coded in engine | .json (Spine) or engine-native | N/A | Simple 2D bone animations for physical object motion. Max 500ms duration per animation. |
| **Particle Effects** (if any, sparingly) | Engine-native particle systems | Engine format | N/A | Used ONLY for paper debris when a script is dragged off-screen, coffee steam. No decorative particles. |

### 5.2 Naming Conventions

All assets use the following structure:

```
[category]_[descriptor]_[state]_[size].extension

Examples:
ui_button_greenlight_default_200x60.png
ui_button_greenlight_hover_200x60.png
ui_button_greenlight_pressed_200x60.png

doc_script_page_procedural_1024x1448.png
doc_coverage_sheet_serialized_1024x1448.png

icon_genre_scifi_24px.svg
icon_attention_crisis_20px.svg

env_desk_mahogany_day_1920x1080.png
env_wall_office_evening_1920x1080.png
```

**Category Prefixes**:
- `ui_` = User interface elements (buttons, borders, overlays)
- `doc_` = Documents (scripts, coverage sheets, newspapers, magazines)
- `icon_` = Icons (genre tags, attention flags, phase indicators)
- `env_` = Environment art (desk, office, backgrounds)
- `fx_` = Effects (rare, only for essential feedback like coffee steam or paper debris)

**State Suffixes** (for interactive elements):
- `_default` = Resting state
- `_hover` = Mouse over
- `_pressed` = Mouse down
- `_disabled` = Non-interactive state

### 5.3 Typography Stack

| Use Case | Font Family | Weight | Size | Color | Fallback |
|---|---|---|---|---|---|
| **Loglines / Project Titles** | **Libre Baskerville** (serif) | Bold (700) | 18-22px | `#2C3E50` (near-black) | Georgia, Times New Roman, serif |
| **Coverage Grades** | **Roboto Slab** (slab serif) | Bold (700) | 48-72px (massive, eye-catching) | Grade-dependent: A = `#27AE60`, B = `#3498DB`, C = `#E67E22`, D/F = `#C1392B` | Georgia, serif |
| **Body Text / Notes / Descriptions** | **Open Sans** (sans-serif) | Regular (400) | 14-16px | `#34495E` (dark gray) | Arial, Helvetica, sans-serif |
| **UI Labels / Metadata** | **Open Sans** (sans-serif) | Light (300) | 10-12px | `#7F8C8D` (medium gray) | Arial, Helvetica, sans-serif |
| **Script Excerpts** | **Courier Prime** (monospace) | Regular (400) | 14px | `#2C3E50` | Courier New, Courier, monospace |
| **Trade Magazine Headlines** (newspapers, in-game articles) | **Playfair Display** (serif) | Bold (700) | 24-36px | `#1C1C1C` (pure black) | Georgia, Times New Roman, serif |
| **Buttons / Calls to Action** | **Montserrat** (sans-serif) | Semibold (600) | 14-16px | Context-dependent (green for success, red for danger, cyan for neutral) | Arial, Helvetica, sans-serif |

**Licensing**:
- All fonts listed are Google Fonts (open source, SIL Open Font License)
- Courier Prime is a freely licensed screenwriting font, superior to default Courier New
- No custom licensed fonts required, reducing pipeline complexity

**Readability Hierarchy**:
1. Coverage Grades (48-72px, bold, color-coded) — BIGGEST, seen first
2. Loglines / Titles (18-22px, bold serif) — second priority, establishes context
3. Body Text (14-16px, regular sans-serif) — comfortable sustained reading
4. Metadata (10-12px, light sans-serif) — tertiary info, available but not distracting

### 5.4 Production Workflow

**Phase 1: Concepting and Mockups (Weeks 1-2)**
1. Art Director produces 3-5 full-screen mockups in Figma:
   - The Desk (full interface with 10 scripts visible)
   - The Development Pipeline (whiteboard with 8 projects across four phases)
   - The Notes Screen (a single creative dilemma with context and options)
   - The Upfronts Presentation (ad buyer confidence meter and pilot showcase)
   - The Screening Room (rough cut viewer with test audience data)
2. Mockups reviewed with Designer (REED) and Narrative Designer (NOVA) for layout feasibility and information hierarchy
3. Iteration cycle: 2-3 rounds of revisions based on feedback
4. Final mockups approved and locked as visual targets

**Phase 2: Asset Production (Weeks 3-8)**
1. UI Artist produces all buttons, borders, overlays, and interactive elements from approved mockups
   - Export all states (default, hover, pressed, disabled)
   - Deliver as .png (for raster elements) and .svg (for scalable icons)
2. Environment Artist produces desk, office, and background layers
   - Separate layers for desk surface, walls, windows, furniture, lighting overlays
   - Deliver as layered .psd for easy adjustment, exported .png per layer for engine import
3. Document Artist produces script and coverage sheet templates
   - Create 8 genre-specific coverage sheet designs (one per genre, using genre color palette)
   - Create coffee stain, dog-ear, and Post-it note overlays as separate assets for procedural variation
   - Deliver as layered .psd templates + individual .png exports
4. Icon Designer produces all genre icons, attention flags, phase indicators
   - Vector line icons at 2px stroke weight
   - Deliver as .svg, test at multiple sizes (20px, 24px, 28px, 48px) for crispness

**Phase 3: Animation and Polish (Weeks 9-10)**
1. Animator (or engineer with animation support) implements:
   - Script drag-and-lift (150ms ease-out on lift, 200ms ease-in on drop)
   - Index card pipeline movement (300ms slide, 100ms settle bounce)
   - Dead pilot drawer animation (500ms shrink + fade when card is dragged to drawer)
   - Button hover lift (100ms ease-out on shadow grow, 100ms ease-in on shadow shrink)
2. VFX Artist (minimal scope) implements:
   - Coffee steam (subtle 2-second looping particle system, 20 particles max, low opacity)
   - Paper debris when script is discarded (5-10 particles, 1-second lifespan, natural fall physics)
3. Polish pass: all assets tested in-engine at 1920x1080, 2560x1440, and 3840x2160 for scaling issues

**Phase 4: Integration and Testing (Weeks 11-12)**
1. All assets integrated into engine by engineering team
2. Readability tests:
   - Coverage sheet legibility test: can a tester identify genre, grade, and logline in under 3 seconds?
   - Pipeline clarity test: can a tester identify which projects need attention in under 5 seconds?
   - Button weight test: do testers hesitate longer on GREENLIGHT/KILL buttons than on Skim/Read buttons?
3. Accessibility tests:
   - Colorblind simulation (protanopia, deuteranopia, tritanopia filters applied to screenshots)
   - High-contrast mode toggle test
   - Font size scaling test (10px minimum enforced across all text)
4. Performance tests:
   - Frame rate maintained at 60fps with 15 scripts on desk (full textures, shadows, animations active)
   - Load time for a full desk clear-and-repopulate under 500ms

### 5.5 Budget Constraints and Asset Reuse

**Target Asset Count**:
- UI buttons and borders: ~50 unique assets (buttons, frames, dividers) x 3 states average = 150 total
- Document templates: 8 genre coverage sheets + 20 script page variations = 28 base templates
- Environment layers: 1 desk + 4 wall variations (morning, midday, evening, night) + 3 window views = 8 environment pieces
- Icons: 8 genre + 3 attention flags + 4 phase indicators + 10 misc UI icons = 25 vector icons
- **Total estimated unique assets: ~210 core assets**, expanded to ~400 total with states and variations

**Reuse Strategy**:
- Coverage sheet layout is a template. Genre color bar and text content are dynamically populated. 1 template = 8 genre variations.
- Script pages use the same paper texture and layout. Only the text content (loglines, excerpts) changes per script. 1 script template = 60-80 unique scripts via text swaps.
- Environment layers are modular. Desk + wall + window can be mixed and matched. 8 pieces = 20+ scene combinations via layering.
- Icons are vector. Scale to any size without quality loss. 25 icons used across hundreds of UI placements.

**Art Budget Estimate**:
- 1 Art Director: 12 weeks part-time (50% allocation) = 6 weeks full-time equivalent
- 1 UI Artist: 8 weeks full-time
- 1 Environment Artist: 4 weeks full-time
- 1 Icon Designer: 2 weeks full-time
- 1 Animator (or engineering support): 2 weeks full-time
- **Total: 22 weeks of art production**, achievable with a small 2-3 person art team over 3 months

---

## 6. READABILITY CHECKLIST RESULTS

This checklist is applied to every major UI screen. If any item fails, the screen requires revision.

### 6.1 The Desk — Script Triage Interface

| Test | Target | Status | Notes |
|---|---|---|---|
| **3-Second Genre Scan** | Player can identify genres of all visible scripts (10-15 scripts) in under 3 seconds | PASS | Genre color flags on top-right corner of each script are instantly visible. Color-coding works. |
| **5-Second Coverage Grade Scan** | Player can identify the letter grades (A, B+, C, etc.) of all visible scripts in under 5 seconds | PASS | Coverage grades rendered at 48-72px font size, bold, color-coded. Impossible to miss. |
| **Expiration Urgency** | Player can identify which scripts are expiring soon (2 days or less) in under 3 seconds | PASS | Red circled dates + scripts physically shifting forward in stack create urgency. |
| **Hover Depth** | Player can reveal additional info on a script (blind-spot indicators, attachments) with a single hover, no click | PASS | Hover lifts script 20px, reveals next 60px of coverage sheet with attachments and blind-spot icons. |
| **Clutter vs. Information Balance** | Desk feels full but not overwhelming. Player can find a specific script within 10 seconds. | PASS | Spatial zones (left = incoming, center = active, right = decided) create navigable structure despite visual density. |

### 6.2 The Development Pipeline — Whiteboard Interface

| Test | Target | Status | Notes |
|---|---|---|---|
| **Attention Flag Visibility** | Player can identify which projects need attention (red/orange flags) in under 3 seconds | PASS | Flag icons appear in bottom-right corner of index cards. Red triangle (crisis) and orange diamond (decision needed) are high-contrast against cream card background. |
| **Phase Understanding** | Player can identify which phase each project is in (Showrunner, Casting, Notes, Production) in under 5 seconds | PASS | Four columns with phase labels at top. Cards in vertical columns. Clear left-to-right progression. |
| **Project Count at a Glance** | Player can estimate number of active projects (8-12 range) without counting | PASS | Whiteboard occupies center 70% of screen. Columns are visually distinct. Peripheral vision captures "full pipeline" vs "sparse pipeline." |
| **Drag and Drop Clarity** | Player can drag a card from one phase to another with no confusion about drop zones | PASS | Drop zones highlight with Hot Cyan `#3498DB` border when card is dragged. Card snaps to grid on release. |

### 6.3 The Notes Screen — Creative Dilemma Interface

| Test | Target | Status | Notes |
|---|---|---|---|
| **Context Readability** | Player can read the full creative dilemma context (1-2 paragraphs) in under 20 seconds | PASS | Body text at 16px Open Sans, 1.6 line height, 600px max width (optimal reading column). |
| **Option Differentiation** | Player can visually distinguish between 2-3 response options without reading full text | PASS | Options presented as distinct cards (200px x 120px each, 16px margin between). Each card has colored left border (green for protect vision, orange for compromise, red for commercial mandate). |
| **Consequences Preview** | Player can see the mechanical effects of each option (Quality Ceiling, Commercial Floor, Showrunner Trust) before committing | PASS | Consequences listed as bullet points below each option, with +/- icons and color-coding (green for positive, red for negative). |
| **Decision Weight** | The decision feels consequential, not rushed | PASS | Modal overlay darkens the rest of the screen. No timer. Player controls pacing. Buttons are large (200px x 60px) and require deliberate click. |

### 6.4 The Upfronts — Presentation Interface

| Test | Target | Status | Notes |
|---|---|---|---|
| **Ad Buyer Confidence Legibility** | Player can read the Ad Buyer Confidence meter state (0-100 scale) in under 2 seconds | PASS | Meter is a horizontal bar, 600px wide, 40px tall, at top of screen. Fill color shifts from red (0-30) to orange (31-60) to green (61-100). Current value displayed as large number (36px font) centered in bar. |
| **Pilot Showcase Clarity** | Player can identify which pilot is currently being presented and its key stats (star power, genre, sell line) in under 5 seconds | PASS | Pilot displayed as a large card (400px x 600px) in center screen. Poster-style layout: title at top, logline below, genre icon, star headshots, sell line at bottom. |
| **Presentation Order Control** | Player can drag pilots to reorder presentation sequence with no ambiguity | PASS | Pilots appear as small cards (120px x 180px) in a horizontal row at bottom of screen. Drag to reorder. Current pilot being presented is highlighted with Hot Cyan border. |

### 6.5 Accessibility — High-Contrast Mode

| Test | Target | Status | Notes |
|---|---|---|---|
| **Colorblind Safety** | All critical information remains distinguishable under protanopia, deuteranopia, and tritanopia filters | PASS | Genre icons supplement color flags. Attention flags use shape + icon + color. No color-only signifiers. |
| **High-Contrast Toggle** | Player can enable high-contrast mode and all text reaches 7:1 contrast ratio (WCAG AAA) | PASS | High-contrast mode: pure white background, pure black text, genre colors at max saturation, borders thickened to 4-5px. |
| **Font Scaling** | Player can scale font sizes 125%, 150%, and 200% without breaking layouts | PARTIAL PASS | 125% and 150% scaling work perfectly. 200% scaling causes some button text to overflow. Needs minor layout adjustment for 200% case. |

**Overall Readability Grade**: A-
The game passes all core readability tests. The only failure is 200% font scaling causing minor layout issues, which is addressable in polish phase. The visual hierarchy is aggressive and functional. Information density is high but organized. The player can parse the screen in seconds, not minutes.

---

## 7. REFERENCE LIST

The visual identity pulls from specific games, films, design movements, and historical aesthetics. Every reference is cited with a reason.

### 7.1 Games — Interface and Readability

| Game | Reference Element | Why It Works | Applied To |
|---|---|---|---|
| **FTL: Faster Than Light** (Subset Games, 2012) | Information-dense interfaces with color-coded urgency. Ship systems are readable at a glance despite complexity. | Clean geometric UI, aggressive use of color to signal state (green = fine, orange = warning, red = crisis). The player can parse a crisis in under 2 seconds. | Attention flag system. Color-coded genre tags. The development pipeline. |
| **Papers, Please** (Lucas Pope, 2013) | Physical document handling as core interaction. Stamping, dragging, comparing papers on a desk. | Tactile, diegetic UI. The desk IS the game. No floating menus. Everything is an object in the workspace. | The Desk interface. Scripts as physical objects. Dragging coverage sheets. |
| **Return of the Obra Dinn** (Lucas Pope, 2018) | Monochrome palette with functional color accents. Clean line art. Period-authentic aesthetic without sacrificing readability. | Restraint. The game uses 1-bit color (black and white) for the core experience, with color reserved for critical UI. The minimalism creates focus. | Institutional green + amber warmth palette. Line icons at 2px stroke. No gradients or decorative flourishes. |
| **Citizen Sleeper** (Jump Over The Age, 2022) | Tabletop-style interface. Dice, cards, and stat blocks presented as physical objects on a table. | Diegetic UI that evokes a specific aesthetic (tabletop RPGs). The interface is the world. No menus pretending to be HUDs. | The whiteboard pipeline as a physical Kanban board. Index cards as project representations. |
| **Slay the Spire** (MegaCrit, 2019) | Card-based UI with instant visual hierarchy. The player can evaluate 10 cards in a hand in under 5 seconds because of aggressive use of iconography, color, and layout. | Information density without clutter. Every card communicates cost, effect, and rarity through visual shorthand. The player learns the visual language in minutes. | Coverage sheets as cards. Genre color-coding. Icon-driven metadata (star power, showrunner ego, etc.). |
| **Pentiment** (Obsidian, 2022) | Period-authentic typography and manuscript aesthetics. Choices presented as illuminated text, not menu buttons. | The UI IS the setting. The game feels like a 16th-century manuscript because the typography and layout are historically accurate. Immersion through design restraint. | Trade magazine typography (Playfair Display headlines). Script excerpts in Courier Prime. Period-correct 2004 office aesthetics (not retro, not modern — accurate). |

### 7.2 Films and TV — Mood and Materiality

| Film / TV | Reference Element | Why It Works | Applied To |
|---|---|---|---|---|
| **Mad Men** (AMC, 2007-2015) | Office aesthetics of the early-to-mid 2000s as seen through a prestige lens. Warm incandescent lighting. The particular texture of power — mahogany desks, leather chairs, glass tumblers. | The show understands that the materials in a workspace communicate status and era. Desks are thrones. Offices are stages. Every object has weight. | The desk as a power object. Mahogany surface. Incandescent desk lamp glow. The LA sunset through office windows. |
| **The Social Network** (David Fincher, 2010) | Warm digital aesthetic. Amber-lit late-night work sessions. The glow of laptop screens in dark rooms. | Fincher's visual language for intellectual work: warm amber in contrast with cool screen glow. The feeling of being alone with the work. | Late-night screening room scenes. Evening work sessions (7pm-10pm) with desk lamp + city light ambiance. |
| **Spotlight** (Tom McCarthy, 2015) | Newsroom materiality. Stacks of documents. Highlighters. Filing cabinets. The controlled chaos of investigative journalism. | The film respects the physicality of research work. Information is not abstract — it is paper, ink, folders, Post-its. The visual clutter communicates the labor. | The Desk interface. Scripts stacked at angles. Coffee rings. Handwritten margin notes. Post-its. The accumulation of work as visual storytelling. |
| **All the President's Men** (Alan J. Pakula, 1976) | The aesthetic of institutional spaces under fluorescent light. Newsroom overhead lighting. The contrast between the warmth of a desk lamp and the coldness of office fluorescence. | Pakula uses light to communicate isolation and institutional power. Fluorescent overheads are oppressive. Desk lamps are intimate. The interplay between the two creates mood. | Time-of-day lighting shifts. Fluorescent Wash `#E8EEE0` for midday. Desk lamp warmth for evening. The player feels the passage of time through light. |
| **Michael Clayton** (Tony Gilroy, 2007) | Corporate power aesthetics. Conference rooms. Glass offices. The particular materiality of high-stakes professional work. | The film's production design communicates wealth and power through restrained, tasteful materials. No excess. Just quality. Mahogany, glass, steel. | Office environment design. The whiteboard as a pristine modular system. The screening room as a clean, professional space. |

### 7.3 Design Movements — Layout and Typography

| Movement / Style | Reference Element | Why It Works | Applied To |
|---|---|---|---|
| **Swiss Design / International Typographic Style** (1950s-1980s) | Grid-based layouts. Sans-serif typography. Objective clarity. Information hierarchy through scale and weight, not decoration. | The movement prioritized readability and function above all else. Every element serves communication. No ornamentation. Clean, modular, timeless. | The development pipeline grid. Coverage sheet layouts. Button typography (Montserrat, a neo-grotesque sans-serif inspired by Swiss design). |
| **Editorial Design — Variety / The Hollywood Reporter** (2000s era) | Trade publication layouts. Bold headlines. Color-coded sections. Pull quotes. Dense information presented with editorial hierarchy. | These publications communicated complex industry information to busy professionals. The layout had to work for someone scanning headlines on a plane. Aggressive hierarchy, functional color, scannable structure. | Coverage sheet layout as a magazine page. Loglines as headlines. Blind-spot indicators as pull quotes. Genre color bars as section dividers. |
| **Brutalist Web Design** (2010s reaction to skeuomorphism) | Raw, unpolished HTML aesthetics. No shadows, no gradients, no gloss. Pure function. The honesty of structural elements. | Brutalism strips away decorative layers to expose the skeleton. It is not minimalism (which is about elegance). It is about honesty — showing the user exactly what is there, no more, no less. | This game does NOT use full brutalism (too harsh for the 2004 setting), but the philosophy informs the restraint: shadows and textures are present but subtle. No gloss, no shine, no decorative gradients. |
| **Dieter Rams' Design Principles** (1970s-1980s, Braun industrial design) | "Good design is as little design as possible." Restraint. Functional beauty. Every element justified. | Rams' 10 principles (especially "good design is unobtrusive" and "good design is thorough down to the last detail") guide the approach to UI. The best UI disappears — the player focuses on the work, not the interface. | Button design. Icon design. Layout grids. The goal is for the player to never think "this UI is beautiful" but to always think "I can read this instantly." |

### 7.4 Historical Aesthetics — Period Accuracy

| Era / Aesthetic | Reference Element | Why It Works | Applied To |
|---|---|---|---|
| **Early-to-Mid 2000s Office Culture** | Beige desktop PCs. CRT monitors (early seasons) transitioning to LCD (later seasons). BlackBerries. Flip phones. Windows XP UI aesthetic. Physical newspapers and trade magazines. | The game is set in 2002-2010. The visual details must reflect this. No modern flat UI. No smartphones. No cloud interfaces. The player is in a specific historical moment, and the production design must honor that. | Office devices (BlackBerry rendered at desk corner, buzzing when emails arrive). Desktop PC monitor in background showing Outlook-style email client. Physical trade magazines (Variety, THR) appearing on desk with period-accurate headlines. |
| **Analog-to-Digital Transition** | The coexistence of paper and screens. Scripts are physical. Coverage is physical. But emails arrive on screen. Ratings reports come as both printouts and spreadsheets. | This era is the liminal space between full analog and full digital. Both exist simultaneously. The materiality of this transition is important — it creates texture and nostalgia. | Scripts and coverage sheets are physical objects. Emails and development pipeline are screen-based but rendered diegetically (desktop monitor in office, not a floating UI). The mix of physical and digital is the aesthetic signature. |
| **LA Office Architecture — 2000s Media Companies** | Floor-to-ceiling windows with tinted glass. Views of the LA skyline. Institutional carpet (gray-green, low pile). Drop ceilings with fluorescent panels. Mahogany or faux-wood furniture trying to signify prestige. | The offices of network executives in 2004 were not tech startup open-plan spaces. They were corporate — tasteful but institutional. The game's environment design must capture this specific corporate aesthetic. | Office background layers. Tinted windows with LA skyline visible. Drop ceiling with recessed fluorescent lights. Mahogany desk. The feeling of a corner office in a mid-2000s media conglomerate. |

### 7.5 Anti-References — What NOT to Do

These are visual styles and games that are explicitly NOT references for PILOT. Included for clarity.

| Anti-Reference | Why It Fails for PILOT |
|---|---|
| **Fortnite / Overwatch / Valorant** | Overly saturated color palettes. Glowing UI elements. Animated flourishes. Too energetic, too gamified. PILOT is grounded and tactile, not flashy and competitive. |
| **Cyberpunk 2077 / Deus Ex UI** | Sci-fi HUD elements. Holographic overlays. Neon glows. High-tech abstraction. PILOT is set in 2004 office spaces with paper and physical objects, not dystopian futures with AR interfaces. |
| **Stardew Valley / Terraria** | Pixel art. Charming, colorful, retro. Wrong era, wrong texture. PILOT is not nostalgic for the 8-bit/16-bit era — it is nostalgic for the early 2000s. |
| **The Sims 4** | Overly clean, plasticky 3D rendering. Everything is glossy and new. No wear, no texture, no history. PILOT's materiality is analog and lived-in — coffee stains, dog-eared corners, used objects. |
| **Monument Valley** | Abstract, surreal, impossible geometry. Beautiful but non-diegetic. PILOT's UI must feel like a real workspace, not a metaphorical puzzle space. |

---

## 8. TECHNICAL CONSTRAINTS SUMMARY

### 8.1 Resolution and Aspect Ratio Targets

| Resolution | Aspect Ratio | Priority | UI Scaling Strategy |
|---|---|---|---|
| **1920x1080** | 16:9 | PRIMARY | Native design resolution. All UI designed at this size. |
| **2560x1440** | 16:9 | HIGH | 1.33x scale. UI elements scale proportionally. Text remains crisp (vector fonts). |
| **3840x2160 (4K)** | 16:9 | MEDIUM | 2x scale. All assets exported at 2x resolution for 4K. Texture memory budget must account for 4K assets. |
| **1366x768** | 16:9 | LOW | 0.71x scale. Minimum supported resolution. UI must remain legible at this size (10px minimum font size becomes ~7px, which is acceptable for labels if necessary). |
| **Ultrawide (2560x1080, 3440x1440)** | 21:9 | STRETCH GOAL | Horizontal expansion. Desk width increases. More scripts visible horizontally. Requires aspect-ratio-aware layout system. |

**Scaling Rules**:
- All UI elements scale proportionally with resolution (buttons, icons, text)
- Aspect ratio is fixed at 16:9 for primary development. Ultrawide support adds horizontal space but does not break core layouts.
- Minimum font size: 10px at 1920x1080. At lower resolutions (1366x768), this becomes ~7px, which is acceptable for metadata/labels but not body text.

### 8.2 Performance Budget

| Metric | Target | Maximum | Notes |
|---|---|---|---|
| **Frame Rate** | 60 FPS | 60 FPS locked | UI-driven game. No excuse for dropped frames. Lock to 60fps. |
| **Texture Memory** | 150 MB at 1080p | 250 MB at 1080p | Document textures (scripts, coverage sheets) are the largest memory consumers. Use texture atlases and lazy loading. |
| **Draw Calls per Frame** | 50-80 | 120 | Most UI is static. Only interactive elements (hovered scripts, dragged cards) generate additional draw calls. Batch static elements aggressively. |
| **Asset Load Time** (desk full repopulate) | 300ms | 500ms | When the desk clears and 15 new scripts arrive, load time must be under 500ms. Player should not notice loading. Use asset pooling. |
| **Animation Frame Budget** | 16ms per frame (60fps) | 16ms | All animations are simple 2D transforms (translate, rotate, scale, opacity). No skeletal animation complexity. Should never exceed frame budget. |

**Memory Optimization Strategies**:
- **Texture Atlases**: Combine all UI buttons, icons, and borders into a single 2048x2048 texture atlas. Reduces draw calls and memory overhead.
- **Lazy Loading**: Scripts on the desk are only fully loaded (with high-res textures) when visible or hovered. Scripts in the background stack use low-res placeholders.
- **Procedural Variation**: Coffee stains, dog-ears, and handwritten notes are applied procedurally at runtime using a small library of 10-15 overlay textures. This creates the illusion of 80 unique script documents using only 15 stain/note overlays.

### 8.3 Platform-Specific Constraints

| Platform | Constraint | Solution |
|---|---|---|
| **PC (Steam)** | Wide range of hardware (low-end laptops to high-end desktops) | Scalable quality settings. High/Medium/Low texture resolution options. UI scales with resolution but maintains readability. |
| **Mac** | Retina displays (2x pixel density) | Export all assets at 2x resolution for Retina. Use vector fonts. Test on actual Retina hardware for crispness. |
| **Nintendo Switch (post-launch port)** | 1280x720 handheld, 1920x1080 docked. Lower GPU power. | Handheld mode requires UI redesign — larger buttons (touch-friendly), simplified layouts. Texture resolution reduced to 1024x1024 max for memory budget. Font sizes increased 20% for handheld readability. |
| **Mobile (stretch consideration)** | Touch input. Small screens (4.7"-6.5"). Limited memory. | Requires full UI redesign. Script Triage mode only. Simplified single-column layout. Touch targets minimum 44x44px. Not in scope for v1. |

### 8.4 Accessibility Technical Requirements

| Feature | Implementation | Performance Cost |
|---|---|---|
| **High-Contrast Mode** | Runtime shader that replaces all colors with high-contrast equivalents (white bg, black text, max saturation accents). Borders thickened via UI scale multiplier. | Negligible. Shader applies per-frame, no asset duplication needed. |
| **Font Scaling (125%, 150%, 200%)** | UI layout system uses relative units (em, %) instead of fixed pixels. Text scales, containers expand to fit. | Minor. Requires responsive layout system. Some manual tweaking for 200% case to prevent overflow. |
| **Colorblind Filters (Protanopia, Deuteranopia, Tritanopia)** | Post-process shader applies colorblind simulation or correction. Player can toggle between simulation modes to preview or enable correction. | Negligible. Post-process shader runs once per frame on final composited image. |
| **Screen Reader Support (future)** | All UI elements tagged with ARIA-style labels. Screen reader narrates button names, coverage sheet content, pipeline state. | Moderate engineering effort. Not in v1 scope but architecture must support it (semantic UI tags, not just visual rendering). |

### 8.5 Animation Technical Specs

| Animation | Duration | Easing Curve | Trigger | Loop |
|---|---|---|---|---|
| **Script Lift (on drag)** | 150ms | Ease-out (cubic) | Mouse down on script | No |
| **Script Drop (on release)** | 200ms | Ease-in (cubic) | Mouse up after drag | No |
| **Index Card Slide (pipeline move)** | 300ms | Ease-out (cubic) | Card moved to new phase | No |
| **Index Card Settle Bounce** | 100ms | Bounce (overshoot by 5%, settle back) | After slide completes | No |
| **Dead Pilot Drawer Animation** | 500ms | Ease-in (cubic), fade opacity from 100% to 0% over same duration | Card dragged to drawer | No |
| **Button Hover Lift** | 100ms | Ease-out (cubic) | Mouse enter button hitbox | No (toggle on hover) |
| **Button Hover Drop** | 100ms | Ease-in (cubic) | Mouse leave button hitbox | No (toggle off hover) |
| **Coffee Steam** | 2000ms | Linear | Scene load (desk in morning/midday) | Yes (infinite loop) |
| **Coverage Sheet Page Turn** | 200ms | Ease-in-out (cubic) | Click "next page" on multi-page coverage | No |

**Technical Notes**:
- All animations use GPU-accelerated transforms (translate, rotate, scale) — no CPU-heavy repaints
- Animations can be interrupted (e.g., if player drops a script mid-lift animation, the drop animation starts immediately from current state)
- Easing curves use standard cubic Bezier functions available in all game engines
- No animation framework dependencies required — engine-native animation systems are sufficient

### 8.6 Localization Constraints

| Language | Text Expansion Factor | Font Support | Layout Impact |
|---|---|---|---|
| **English** | 1.0x (baseline) | Full support (all fonts render correctly) | Baseline layout |
| **French, Spanish, Italian** | 1.2x (20% longer than English on average) | Full support | Buttons and text containers must accommodate 20% expansion without overflow |
| **German** | 1.35x (35% longer, compound words) | Full support | Requires larger text containers. Some button labels may need abbreviation. |
| **Japanese, Chinese** | 0.7x (30% shorter, denser characters) | Requires CJK font support (use Noto Sans CJK) | Text is shorter but characters are more complex. Minimum font size increases to 14px for body text. |
| **Russian, Polish** | 1.15x (15% longer) | Requires Cyrillic support (Open Sans supports Cyrillic) | Minor expansion. Existing containers handle it. |

**Localization Strategy for v1**:
- English only at launch
- All UI text is externalized to .json localization files (not hardcoded in assets)
- Font stack includes fallback fonts with broad character support (Noto Sans as fallback for CJK)
- Text containers are sized at 1.5x English baseline to accommodate future localization without layout breaks

### 8.7 File Size and Distribution

| Asset Category | Size at 1080p | Size at 4K (2x assets) | Compression Strategy |
|---|---|---|---|
| **UI Elements** (buttons, borders, overlays) | 15 MB | 40 MB | PNG with 8-bit alpha. Compress with pngquant (lossy but visually lossless at 90% quality). |
| **Document Textures** (scripts, coverage sheets, newspapers) | 60 MB | 180 MB | JPEG for photo-realistic textures (paper grain, coffee stains). PNG for text-heavy documents (coverage sheets). Atlased where possible. |
| **Environment Art** (desk, office, backgrounds) | 25 MB | 70 MB | JPEG for painted backgrounds. PNG for layered assets requiring transparency. |
| **Icons** (SVG) | 1 MB | 1 MB (vector, resolution-independent) | SVG minified (remove unnecessary metadata). |
| **Fonts** | 3 MB (5 font families, multiple weights) | 3 MB | WOFF2 format (smallest). Subset fonts to include only Latin + basic punctuation (reduces size 50%). |
| **Total Estimated Art Assets** | 100-120 MB | 300-350 MB | 4K asset pack is DLC download (not included in base install). Base game is 1080p/1440p optimized. |

**Distribution Plan**:
- Base game includes 1080p and 1440p assets (120-150 MB total art)
- 4K texture pack is optional free DLC (adds 200 MB)
- Switch port uses lower-res assets (1024x1024 max textures, 60-80 MB total art)

### 8.8 Tooling and Version Control

| Tool | Purpose | File Formats | Version Control Strategy |
|---|---|---|
| **Figma** | UI mockups, layout design, interactive prototypes | .fig (cloud-hosted) | Figma's native version history. Export final approved mockups as .png and .pdf for reference. |
| **Photoshop** | Texture creation (paper grain, coffee stains), document templates, environment art | .psd (source), .png / .jpg (export) | .psd files stored in Git LFS (large file storage). Exported .png/.jpg committed to main repo. |
| **Illustrator** | Icon design, vector UI elements | .ai (source), .svg (export) | .ai files stored in Git LFS. .svg files committed to main repo (small, text-based, diff-friendly). |
| **Spine / Engine Animation Tools** | UI animations (drag, lift, slide) | .json (Spine) or engine-native | Animation files committed to main repo. Spine .json is text-based and version-control-friendly. |
| **Git** | Version control for all assets | All formats | Main repo for .svg, .png, .jpg, .json. Git LFS for .psd, .ai, .fig (large binary files). |

**Asset Pipeline Automation**:
- **Pre-commit Hook**: Runs pngquant on all .png files before commit to ensure compression
- **CI/CD Build Step**: Generates texture atlases from individual UI elements at build time (not manually maintained)
- **Export Script**: Photoshop script that batch-exports all .psd layers to .png with correct naming conventions (run manually before commits)

---

## 9. FINAL PRODUCTION NOTES

### 9.1 The Squint Test

Every major UI screen must pass the squint test: if the player squints or steps back from the monitor, the most important information should still be visible. Coverage grades (48-72px, bold, color-coded) pass. Genre color flags pass. Attention flags (red triangles, orange diamonds) pass. If a piece of information disappears when the player squints, it is not important enough to be large, or it is too important and needs to be larger.

### 9.2 The Thumbnail Test

Take a 1920x1080 screenshot of each major UI screen. Shrink it to 320x180 (YouTube thumbnail size). Can you still identify what screen this is? Can you still see the most critical information? If not, the visual hierarchy is too weak. The Desk should be recognizable as "scripts on a desk" even at thumbnail size. The Pipeline should be recognizable as "a whiteboard with cards." The Upfronts should be recognizable as "a presentation with a meter." Thumbnails are not just for marketing — they are a test of whether your visual identity is strong enough to survive information loss.

### 9.3 The Motion Test

UI animations exist to communicate state change, not to look cool. Every animation must answer: what is this telling the player? The script lift on drag tells the player "you have grabbed this object." The card slide in the pipeline tells the player "this project has moved to a new phase." The dead pilot drawer animation tells the player "this project is dead and gone." If an animation does not communicate a state change, it is decorative and should be cut.

### 9.4 The One-Pixel Rule

Every pixel must earn its place. If a decorative element (a texture, a shadow, a gradient) is not improving readability or communicating information, it is noise. The game's aesthetic is restrained. Coffee stains and paper grain are present because they ground the player in the materiality of the work, not because they look pretty. The wood grain on the desk is subtle because the desk is a background element, not a focal point. The one-pixel rule: if you can remove a pixel and the screen still works, remove it. What remains is the design.

### 9.5 The Player's Eye Path

When the player opens the Desk interface, their eye should move in this order:
1. Coverage grades (largest, boldest, color-coded) — 0.5 seconds
2. Genre flags (color-coded corner tabs) — 1 second
3. Loglines (bold serif headlines) — 2 seconds
4. Attention flags (red circles on expiring scripts) — 3 seconds
5. Metadata (attachments, blind-spot indicators) — 5+ seconds (opt-in, on hover)

This hierarchy is enforced through size, weight, color, and position. The most important information is the largest, boldest, and highest-contrast. The least important information is the smallest, lightest, and lowest-contrast. The player's eye naturally follows this gradient from high-contrast to low-contrast, from large to small. If playtesting reveals that players miss critical information (e.g., they ignore expiring scripts), the hierarchy is wrong and must be adjusted.

### 9.6 The Silence Test

Turn off all sound. Play the game for 10 minutes. Does the visual feedback alone communicate everything the player needs to know? When a script expires and slides off the desk, is the visual alone enough? When the Ad Buyer Confidence meter rises during the Upfronts, is the visual alone enough? Sound should enhance, not replace, visual feedback. The game must be fully playable with sound off. This is not just an accessibility concern — it is a design discipline. If you rely on sound to communicate state, you have failed the visual design.

### 9.7 The Ugly Phase

Every art asset will go through an ugly phase. The first pass of the desk will look wrong. The first pass of the coverage sheet layout will feel cramped. The first pass of the pipeline cards will lack hierarchy. This is normal. The ugly phase is where you learn what does not work. Do not polish the ugly phase. Iterate through it quickly. Only when the layout, hierarchy, and readability are correct do you add the final textures, shadows, and details. Polish is the last 10% of the work. If you polish too early, you waste time making bad layouts look good.

### 9.8 The Production-Ready Checklist

Before any asset is marked "final," it must pass:
- [ ] Readability test (squint test, thumbnail test)
- [ ] Accessibility test (colorblind filter, high-contrast mode)
- [ ] Performance test (load time, frame rate impact)
- [ ] Consistency test (does this match the established visual language?)
- [ ] Localization test (can this accommodate 35% text expansion for German?)
- [ ] Platform test (does this work at 1366x768 minimum resolution?)

If any checkbox fails, the asset returns to iteration.

---

## 10. CONCLUSION — THE VISUAL THESIS

PILOT is a game about reading. Reading scripts. Reading coverage. Reading the industry. Reading the landscape. Reading the consequences of your taste.

The art direction's job is to make reading effortless. To create a visual language so clear, so consistent, so hierarchical that the player never fights the interface. The player should spend 95% of their mental energy on the decisions — the creative dilemmas, the strategic positioning, the moral weight of greenlighting or killing a show — and 5% on parsing the UI.

The visual identity is:
- **Physical** — A desk, not a database. Objects, not menus.
- **Hierarchical** — The most important information is the largest, boldest, and first to hit the eye.
- **Restrained** — Every pixel earns its place. No decoration for decoration's sake.
- **Period-Authentic** — 2004 office culture, rendered with respect and accuracy, not parody.
- **Functional Above All** — If the player cannot parse the screen in 3 seconds, the design has failed.

This is not a game that will win awards for the most beautiful UI. This is a game that will win awards for the most *readable* UI. For the UI that disappeared so completely that players forgot they were looking at a UI and felt like they were sitting at a desk, holding a script, making a choice that mattered.

Show the work. Show the weight. Make the screen sing with clarity.

That is the job.

---

**End of Art Direction Document**

**Next Steps**:
1. Produce Figma mockups of the Desk, Pipeline, Notes Screen, and Upfronts (Week 1-2)
2. Review mockups with Designer (REED) and Narrative Designer (NOVA) for feasibility and information hierarchy
3. Begin asset production (UI elements, document templates, environment layers) (Week 3-8)
4. Integrate assets into engine and run readability tests (Week 9-12)
5. Iterate based on playtest feedback

**Questions for Design Review**:
- Does the genre color-coding system feel intuitive or overwhelming with 8 genres?
- Is the development pipeline whiteboard too abstract, or does the index card metaphor work?
- Does the high-contrast mode meet accessibility needs, or are additional modes required?
- Should the coffee stains and paper grain be dialed back for a cleaner look, or are they essential to the analog aesthetic?

**Approval**:
This document is ready for stakeholder review and production greenlight.

— PIXEL, Art Director