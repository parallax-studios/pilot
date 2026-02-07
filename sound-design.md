# PILOT — Sound Design Document

**Audio Director**: ECHO
**Version**: 1.0
**Date**: 2026-02-07
**Status**: Production-Ready Sound Design Specification

---

Close your eyes — what do you hear?

A BlackBerry vibrating against a mahogany desk. The particular silence of a screening room after the lights go down. The rustle of a script page turning, coffee-stained and dog-eared. The institutional hum of fluorescent lights and HVAC in a media company office at 6 PM when everyone else has gone home and you are still reading coverage. The sound of a phone ringing — landline, not cell, the tone that meant *someone important is calling* in 2004. The creak of a leather chair when you lean back to think about whether to kill something beautiful.

These are not sound effects. These are the frequencies of decision-making under pressure. This is the soundscape of creative authority wielded in an industry that rewards cowardice.

Audio IS game feel. In PILOT, every greenlight is a gamble. Audio makes the player's body respond to that risk before their mind catches up. The moment before the desk phone rings. The silence after test audience data arrives. The held breath during the upfronts presentation when Ad Buyer Confidence ticks upward or stalls. That is where I work. The space between heartbeats.

This document specifies the complete audio design for PILOT — sonic identity, every sound effect organized by category and implementation context, music system architecture, adaptive audio design, mix hierarchy, implementation plan, and the deliberate silences that create impact. Every section is production-ready. No placeholders. No "we will figure out the vibe later." The sonic palette is defined. The frequency of this game's emotion is mapped.

Let us listen.

---

## 1. SONIC IDENTITY STATEMENT

**PILOT sounds like the weight of taste being tested against the machinery of commerce.**

The game's audio is **warm analog grain meeting institutional sterility**. Organic textures — paper, wood, human breath, the mechanical precision of early-2000s office technology — layered against the cold efficiency of systems designed to reduce art to numbers. The soundscape is intimate and isolating simultaneously. You are surrounded by the evidence of creative work — scripts, rough cuts, showrunner voices — but you make decisions alone.

The emotional frequency is **controlled tension with periodic release**. Not constant stress, but the slow accumulation of pressure across a development season, punctuated by moments of catharsis (the upfronts presentation, the moment a pilot clicks, the relief of a hit) and moments of hollow quiet (killing a show, watching something you believed in fail). The audio breathes. It knows when to press and when to give space.

The keynote — the ever-present background tone that defines the world — is **the hum of institutional infrastructure**. HVAC, distant elevator mechanisms, the ambient electrical noise of an office building after 5 PM. It is the sound of a machine that is always running, indifferent to whether you succeed or fail. Against that hum, every human sound — a script page turning, a voice on the phone, a sigh — becomes more present, more weighted. Silence is not the absence of sound. Silence is the absence of human presence in a space designed for human work.

The signal — the sound that cuts through the keynote and demands attention — is **communication technology**. Phone rings, email arrival chimes, the buzz of a pager or early BlackBerry. These sounds mean *someone wants something from you*. They are interruptions, demands, pressure. The player will learn to associate these frequencies with decision points. By hour 20, the sound of a phone ringing should trigger a micro-adrenaline response.

**Sonic Thesis**: PILOT does not sound like excitement or spectacle. It sounds like concentration, consequence, and the particular loneliness of being the person who decides.

---

## 2. SONIC PALETTE DESCRIPTION

### 2.1 Tonal Profile

**Temperature**: WARM. Not cold corporate minimalism. The player's office is a creative space, not a boardroom. Wood desk, paper scripts, analog warmth. The sonic palette leans into mid-frequencies — the body of a room, the presence of materials. Bass is restrained (institutional architecture has low bass rumble, but it is felt more than heard). Highs are soft, not brittle. Think the difference between a vinyl record and a CD. PILOT sounds like vinyl.

**Texture**: LAYERED and DETAILED. Every surface in the game world makes a sound. Paper has grain. Desks have resonance. Chairs creak with specific timbres based on material. The sonic world rewards attention. A player who listens closely hears the difference between a cheap script printed on standard paper and an expensive script on premium stock. The texture is storytelling.

**Density**: SPARSE to MEDIUM. Not sonic wallpaper. Every sound has space around it. When the player is at the desk alone, the soundscape is minimal — the hum, the occasional environmental punctuation (distant traffic through a window, a door closing down the hall). When the player is in a meeting or at the upfronts, the soundscape densifies with human presence — voices, movement, the rustle of an audience. The audio expands and contracts with the social density of the moment.

**Fidelity**: ANALOG WARMTH with DIGITAL PRECISION. The game is set in the early-to-mid 2000s, a transitional era. Office technology is digital (computers, email, early smartphones) but the creative work is still analog (printed scripts, physical screening rooms, face-to-face notes sessions). The audio reflects this hybridity. Digital sounds (email chimes, computer UI) have slight analog degradation — the warmth of a speaker, the grain of a recording. Analog sounds (paper, wood, voices) are recorded with precision but mixed with warmth. Nothing sounds sterile. Nothing sounds lo-fi. Everything sounds *present*.

### 2.2 Reference Tracks and Sonic Touchstones

**Reference Albums/Scores** (for music composition tone):
- Thomas Newman — *American Beauty* OST. Sparse piano motifs, warm orchestral textures, melancholy without sentimentality. The sound of suburban institutional loneliness.
- Jon Brion — *Punch-Drunk Love* OST. Odd timbres, emotional restraint, sudden dynamic shifts. The sound of pressure building and releasing.
- Trent Reznor & Atticus Ross — *The Social Network* OST. Analog synths, precise percussion, cold ambition with warm human undertones. The sound of creative work as high-stakes competition.
- Ólafur Arnalds — *re:member*. Piano with subtle electronic processing, string textures, the intersection of organic and synthetic. The sound of something intimate being observed from a distance.

**Reference Films/TV** (for soundscape design texture):
- *Mad Men* (2007-2015). Office soundscapes of the mid-century but tonally applicable. The sound of work as ritual, the creak of chairs, the pour of a drink, the strike of a typewriter (replaced in PILOT with keyboard clicks and script pages).
- *The Social Network* (2010). Conference rooms, late-night offices, the hum of early tech-era infrastructure. The sound of ambition in fluorescent-lit rooms.
- *Up in the Air* (2009). Airports, hotels, impersonal professional spaces rendered with warmth. The sound of a life lived in transit between decisions.
- *Margin Call* (2011). Office building at night, the tension of institutional crisis, people realizing something is ending. The sound of watching the machinery break.

**Reference Games** (for UI/feedback audio):
- *Pentiment* (2022). UI sounds that feel period-appropriate without being literal. The sound of parchment, ink, the physicality of medieval text. PILOT takes the same philosophy for early-2000s office materiality.
- *Return of the Obra Dinn* (2018). Detailed environmental audio where every surface and object has a distinct sound. The soundscape rewards close listening.
- *Disco Elysium* (2019). UI sounds that are textured, tactile, never generic. The sound of thought as a physical process.

**Non-Musical Sonic References** (textures and tone):
- ASMR office ambience recordings — the unintentional sonic pleasure of work environments (keyboard typing, paper shuffling, pen clicks). PILOT uses these textures but recontextualizes them as decision-making pressure.
- NPR / public radio production aesthetic. Warm, intimate voice recording. The sound of someone speaking directly to you in a quiet room, even when the content is high-stakes.
- Vinyl record surface noise and warm analog hiss. Not as literal effects, but as a tonal principle — audio that has *body* and *grain*, not clinical digital silence between sounds.

### 2.3 What This Palette AVOIDS

**No**: Generic corporate stock music. Motivational synth pads. Upbeat indie folk. Whimsical UI blips and bloops. Aggressive orchestral stabs. Anything that suggests *excitement* as the primary emotion. PILOT is not exciting. PILOT is *consequential*.

**No**: Overly literal period signifiers. No gratuitous "here is a 2000s pop song to remind you what year it is." The period is established through technology sounds (flip phone, BlackBerry, dial-up modem at one point) and design, not through needle drops. The music is timeless in its melancholy.

**No**: Constant musical presence. This is not a game that scores every moment. Music is reserved for emotional peaks and contextual locations. Much of the game plays in near-silence with environmental sound only. Silence is a sound design choice.

---

## 3. SFX LIBRARY — ORGANIZED BY CATEGORY

Every sound effect listed below is specified with:
- **Context**: When/where the sound plays
- **Tonal Description**: How it should feel
- **Implementation Notes**: Triggering conditions, variations, adaptive behavior

### 3.1 DESK / WORKSPACE INTERFACE

The desk is the hub. Its sounds are the most frequently heard in the game. They must be satisfying, detailed, and varied enough to avoid fatigue over 40-60 hours of play.

#### Paper & Script Sounds

**Script Lands on Desk**
- Context: A new script arrives in the triage pile.
- Tonal Description: A soft, substantial *thud* with paper rustle overtones. Weight without aggression. The sound of *another decision to make*.
- Variations: 8 variations varying paper thickness, landing position (center desk, edge, on top of another script). Heavier scripts (prestigious material, established showrunners) have deeper resonance. Cheap spec scripts have lighter, thinner impact.
- Implementation: Randomized variation selection, with script origin metadata influencing which variation pool is used.

**Script Page Turn**
- Context: Player deep-reads a script, advancing through text.
- Tonal Description: Crisp, intimate, close-mic'd. The sound of attention. Single page turn, clean separation, slight finger friction against paper grain.
- Variations: 12 variations (pages stick slightly, pages turn smoothly, pages are dog-eared). Variation selection is semi-random with slight weighting toward "stickier" turns on older scripts or scripts that have been read multiple times.
- Implementation: Triggered on text advance input. Slight randomized pitch variation (-3% to +2%) to avoid repetition fatigue.

**Coverage Sheet Attach/Detach**
- Context: Player picks up a script to read the coverage sheet, or sets the coverage aside to read the script itself.
- Tonal Description: Paperclip slide or slight staple flex. Metallic micro-detail over paper rustle. The sound of separating *data* from *art*.
- Variations: 6 variations.
- Implementation: Triggered when player toggles between coverage view and script view.

**Script Slide Across Desk**
- Context: Player drags a script into PASS, CONSIDER, or PRIORITY piles.
- Tonal Description: Paper friction against wood surface. The sound of triage — decisive, physical, final.
- Variations: 10 variations based on slide distance and desk surface material. Longer slides have extended friction tails. Scripts landing in PRIORITY have slightly heavier impact than PASS.
- Implementation: Sound length and pitch scale with drag distance. Endpoint impact sound varies by destination pile.

**Script Expires / Slides Off Desk**
- Context: A script's expiration timer runs out; it physically slides off the desk edge.
- Tonal Description: Accelerating paper slide, slight tumble, off-screen impact (paper hitting floor, muffled and distant). The sound of *loss* — something you did not choose, chose itself.
- Variations: 4 variations.
- Implementation: Triggered when expiration timer hits zero. Followed 2 seconds later by a subtle "missed opportunity" notification sound (see UI Feedback).

**Stack Shuffle / Rearrange**
- Context: Player manually reorders scripts in the CONSIDER pile.
- Tonal Description: Multiple pages riffling together, slight compression of the stack. The sound of *prioritizing within the already prioritized*.
- Variations: 5 variations based on stack size (3-5 scripts = light riffle, 8-12 scripts = heavier shuffle).
- Implementation: Triggered on manual reorder input.

#### Desk Surface Interaction

**Coffee Mug Set Down**
- Context: Ambient environmental detail. The player's coffee mug is occasionally set down on the desk (automated at scene transitions, or player can interact).
- Tonal Description: Ceramic on wood, slight liquid slosh inside. Warm, grounding. The sound of a human presence in a work environment.
- Variations: 6 variations (mug is full = more slosh, mug is near-empty = less slosh, mug is set carefully vs. set with fatigue-induced carelessness).
- Implementation: Ambient trigger every 3-8 minutes during desk work sessions. Variation selected based on time of day in-game (morning = full, late night = empty) and current stress level (low stress = careful placement, high stress = careless).

**Pen Click / Tap**
- Context: Ambient fidget sound when the player is idle at the desk for more than 10 seconds, or during moments of decision hesitation (e.g., hovering over a script without committing to a choice).
- Tonal Description: Ballpoint pen click, or pen tapping against desk surface. Nervous energy, thought process, the sound of *hesitation*.
- Variations: 8 variations (single click, double click, rhythmic tap, pen roll).
- Implementation: Triggered on idle state. Frequency increases if player hovers over a high-stakes decision (e.g., PASS vs. PRIORITY on a script with blind-spot indicators) for more than 5 seconds.

**Desk Drawer Open/Close**
- Context: Player accesses archived scripts, budget documents, or the "dead pilots" drawer.
- Tonal Description: Wood-on-wood slide with slight resistance. Metal handle rattle. The sound of *excavation* — retrieving something filed away.
- Variations: 4 variations (smooth open, sticky drawer that requires extra pull, slow careful close, quick frustrated close).
- Implementation: Triggered on drawer UI interaction. "Dead pilots" drawer has a distinct, heavier, slower variation with more resonance — this drawer contains ghosts.

**Post-It Note Placement**
- Context: Player adds a note or reminder to a script or project card.
- Tonal Description: Slight adhesive peel, paper flutter, soft press onto surface. The sound of *annotation* — making the work your own.
- Variations: 5 variations.
- Implementation: Triggered on note/reminder UI action.

**Desk Lamp Switch**
- Context: Transition between day and night work sessions. The desk lamp toggles on as ambient light fades.
- Tonal Description: Mechanical switch click (vintage pull-chain or rotary switch, not modern toggle), followed by a very soft electrical hum from the bulb warming up.
- Variations: 2 variations (pull-chain, rotary switch).
- Implementation: Triggered automatically at day-to-night transitions, or player can toggle manually.

#### Desk Technology (Early 2000s Period-Specific)

**Landline Phone Ring**
- Context: Incoming call from network president, showrunner, agent, or industry contact.
- Tonal Description: Classic desk phone ring — analog bell mechanism, mid-frequency, insistent but not shrill. The sound that means *someone wants a decision from you*. By hour 20, this sound should be Pavlovian.
- Variations: 3 variations (standard double-ring, longer ring for high-priority calls, slightly muffled ring if the phone is under a stack of scripts).
- Implementation: Priority-based variation selection. High-priority calls (network president during a crisis, showrunner threatening to walk) use a longer, more insistent ring pattern.

**Phone Receiver Pickup / Hangup**
- Context: Player answers or ends a call.
- Tonal Description: Handset lift from cradle (mechanical click, slight cord rustle), and handset return to cradle (heavier click, definitive). Pickup is the sound of *engagement*. Hangup is the sound of *finality*.
- Variations: 4 variations for pickup (calm, hurried, reluctant, eager), 3 for hangup (gentle, firm, frustrated slam).
- Implementation: Variation selected based on call context metadata (e.g., "network president low-patience call" = reluctant pickup, frustrated hangup).

**BlackBerry / Early Smartphone Buzz**
- Context: Email or urgent message arrives.
- Tonal Description: Vibration motor against wood desk surface — buzzy, rattling, mechanical. Less pleasant than a ring. The sound of *intrusion*.
- Variations: 3 variations (single buzz, double buzz, extended buzz for high-priority message).
- Implementation: Email notifications use single buzz. Urgent in-season updates (ratings reports, crisis alerts) use extended buzz.

**Computer Keyboard Typing**
- Context: Player is composing an email response, writing notes, or inputting data.
- Tonal Description: Mechanical keyboard from the early 2000s — clacky, tactile, each keystroke distinct. Not the mushy silence of a modern laptop keyboard. The sound of *work being done*.
- Variations: 15+ individual key sounds, randomized per keystroke to avoid machine-gun repetition.
- Implementation: Triggered on text input. Typing rhythm varies based on input speed (slow deliberate typing for difficult emails, fast typing for routine tasks).

**Computer Mouse Click**
- Context: UI interaction — selecting options, clicking through menus.
- Tonal Description: Vintage two-button mouse click — mechanical, satisfying, with slight plastic housing resonance. Not the soft modern click. The sound of *committing to a choice*.
- Variations: 6 variations (left click, right click, double-click, click-and-hold).
- Implementation: Mapped to corresponding input actions.

**Email Arrival Chime**
- Context: New email arrives in inbox.
- Tonal Description: Early-2000s OS email notification sound — simple, digital, slightly musical but not cheerful. Two-tone chime, major interval but soft attack. The sound of *new information*.
- Variations: 2 variations (standard priority, high priority — high-priority emails have a slightly sharper, more attention-grabbing chime).
- Implementation: Triggered on email event. Player can check email at will, or emails arrive on story/mechanic schedule.

**Computer Startup / Shutdown**
- Context: Session start (player sits down at desk for a new day) and session end (player leaves the office for the day/night).
- Tonal Description: Startup — vintage Windows XP-era startup sound (warm, optimistic, institutional). Shutdown — shorter, descending tone, the sound of *task complete*.
- Variations: 1 each.
- Implementation: Triggered at session bookends.

**Dot Matrix / Laser Printer**
- Context: Printing a document — coverage reports, budget sheets, rough cut notes.
- Tonal Description: Mechanical printer sounds — laser printer warm-up hum, paper feed mechanism, the rhythmic clunk of printing. The sound of *making the ephemeral permanent*.
- Variations: 3 variations based on document length (single page, multi-page, large document stack).
- Implementation: Triggered when player generates reports.

### 3.2 WHITEBOARD / DEVELOPMENT PIPELINE INTERFACE

The whiteboard is the strategic interface. Its sounds are tactile, physical, and satisfying — the sound of moving pieces in a high-stakes game.

**Index Card Pickup**
- Context: Player selects a pilot project card to view details or move between pipeline phases.
- Tonal Description: Cardstock slide against whiteboard surface, slight magnetic release (if using magnetic whiteboard) or thumbtack displacement (if using cork/pin board). Light, crisp. The sound of *isolating a single element*.
- Variations: 5 variations.
- Implementation: Triggered on card selection.

**Index Card Drag**
- Context: Player moves a project card between development phases (Showrunner Attachment → Casting → Notes → Pilot Production).
- Tonal Description: Continuous cardstock slide with slight friction variance based on drag speed. The sound of *progress*.
- Variations: Friction texture varies with drag distance and speed.
- Implementation: Sound plays continuously during drag, pitch/speed modulates based on input velocity.

**Index Card Place / Drop**
- Context: Player releases a project card into a new pipeline phase.
- Tonal Description: Cardstock impact on whiteboard, with magnetic snap or pin placement click. Decisive, satisfying. The sound of *commitment*.
- Variations: 4 variations based on drop firmness (gentle placement, firm drop).
- Implementation: Firmness variation based on input release velocity.

**Index Card Flip**
- Context: Player flips a project card to view notes or details on the reverse.
- Tonal Description: Quick cardstock flip, air whoosh, slight flutter. The sound of *revealing hidden information*.
- Variations: 3 variations.
- Implementation: Triggered on detail-view toggle.

**Dry-Erase Marker Write**
- Context: Player annotates the whiteboard — adding notes to a project, updating status, writing reminders.
- Tonal Description: Squeaky marker-on-whiteboard friction, slight chemical solvent smell (implied sonically through high-frequency detail). The sound of *real-time thinking*.
- Variations: 8 variations (short stroke, long stroke, circling, underlining).
- Implementation: Triggered on annotation input. Stroke length/type determines variation.

**Dry-Erase Marker Cap On/Off**
- Context: Player begins or ends an annotation session.
- Tonal Description: Plastic cap pull (slight suction release) and cap press (snap closure). The sound of *preparation* and *completion*.
- Variations: 2 variations (cap off, cap on).
- Implementation: Triggered at annotation session start/end.

**Whiteboard Erase**
- Context: Player removes a note or clears a completed project card from the board.
- Tonal Description: Eraser swipe across whiteboard surface — friction, squeak, the ghostly residue of what was there. The sound of *making space for what is next*.
- Variations: 5 variations based on erase area size.
- Implementation: Triggered on delete/clear actions.

**Project Card Flag Attach**
- Context: Player or system adds an "Attention Flag" to a troubled project (over-budget, showrunner conflict, casting delay).
- Tonal Description: Small flag or pin attachment — metal pin press into board, or adhesive flag stick. Sharp, attention-grabbing. The sound of *warning*.
- Variations: 3 variations (yellow flag = caution, red flag = crisis).
- Implementation: Triggered when a project enters a troubled state. Flag color/type determines variation.

**Dead Pilots Drawer Slide**
- Context: A killed pilot card is dragged to the "dead pilots" drawer — a graveyard for cancelled projects.
- Tonal Description: Heavier, slower drawer slide than standard desk drawer. Wood grain friction, slight groan of resistance. The drawer does not want to open because it contains *regret*.
- Variations: 2 variations (drawer open, drawer close). Close has a heavier, more final thud.
- Implementation: Triggered when a pilot is killed at upfronts or in development. The sound of the drawer closing is followed by 2 seconds of silence — no music, no ambient sound. Just the weight of the decision.

### 3.3 SCREENING ROOM

The screening room is a sacred space. Its soundscape is distinct from the office — darker, quieter, more focused. The player is alone with the work.

**Screening Room Door Open/Close**
- Context: Player enters or exits the screening room to watch a rough cut.
- Tonal Description: Heavy soundproof door — thick, solid, with a soft pneumatic hiss on close. The sound of *entering a liminal space*. Outside the door is the office. Inside is the art.
- Variations: 2 variations (door open, door close).
- Implementation: Triggered on scene transition to/from screening room.

**Theater Seat Settle**
- Context: Player sits in the screening room chair.
- Tonal Description: Leather/fabric seat compression, slight creak, the rustle of clothing against upholstery. The sound of *preparation to witness*.
- Variations: 3 variations.
- Implementation: Triggered as player settles into screening room scene.

**Lights Dim**
- Context: Lights go down before the rough cut begins.
- Tonal Description: Smooth dimmer switch descent — electrical hum fading, mechanical relay click at full-off. The sound of *focus narrowing*.
- Variations: 1 variation.
- Implementation: Triggered automatically before rough cut playback.

**Projector / Monitor Power On**
- Context: The screening display (projector or large monitor, period-appropriate) powers on.
- Tonal Description: CRT monitor degauss (if period monitor) or digital projector fan spin-up (if projector). Warm-up hum. The sound of *the work about to appear*.
- Variations: 2 variations (CRT monitor, digital projector).
- Implementation: Period-appropriate tech based on season year.

**Film/Video Playback Start**
- Context: The rough cut begins.
- Tonal Description: For early seasons (film-based rough cuts): slight film transport mechanism, sprocket gentle clicking. For later seasons (digital rough cuts): soft media player interface beep. The sound of *the pilot speaking for itself*.
- Variations: 2 variations (film, digital).
- Implementation: Period-based variation.

**Legal Pad Page Turn**
- Context: Player takes notes during the rough cut screening.
- Tonal Description: Paper page turn, pencil scratch against paper grain. Quieter and more intimate than desk script turns — this is note-taking in a dark room.
- Variations: 4 variations.
- Implementation: Triggered when player advances through rough cut scenes or takes notes.

**Pencil Write on Paper**
- Context: Player annotates notes during screening.
- Tonal Description: Graphite friction on paper — scratchy, textured, the sound of *critical observation*. Not smooth ink flow. This is rough, working notation.
- Variations: 6 variations (short note, long note, underline, circle).
- Implementation: Triggered on note-taking input.

**Playback Pause / Resume**
- Context: Player pauses the rough cut to take a longer note or reflect.
- Tonal Description: Soft digital beep (pause), resumption of playback hum (resume). The sound of *stopping to think*.
- Variations: 2 variations (pause, resume).
- Implementation: Triggered on playback controls.

**Rough Cut End / Silence**
- Context: The rough cut finishes. The screen goes black.
- Tonal Description: Playback mechanism stops. Projector/monitor hum continues. 3 seconds of silence before any UI or prompt appears. The sound of *sitting with what you just saw*. The player is alone with their judgment.
- Variations: 1 variation.
- Implementation: Hard-coded 3-second silence after rough cut completion before any system sounds or music resume.

**Lights Raise**
- Context: Screening ends, lights come back up.
- Tonal Description: Dimmer switch ascent, electrical hum rising, the return of ambient room tone. The sound of *returning to the world where decisions must be made*.
- Variations: 1 variation.
- Implementation: Triggered after rough cut evaluation UI is dismissed.

### 3.4 MEETINGS & UPFRONTS

Social spaces have denser soundscapes. Multiple people, movement, the ambient noise of human presence.

**Conference Room Door Open/Close**
- Context: Entering or exiting a development meeting or upfronts prep session.
- Tonal Description: Standard office door — lighter than screening room door, standard handle turn and latch click. The sound of *entering the social/political arena*.
- Variations: 2 variations (open, close).
- Implementation: Triggered on meeting scene transitions.

**Conference Room Ambience**
- Context: Background sound layer for meeting scenes.
- Tonal Description: Low-level room tone with subtle human presence — slight chair creaks, paper rustle, the occasional cleared throat or distant cough. HVAC hum is present but softer than in the office. The sound of *people waiting, listening, judging*.
- Variations: 3 variations based on meeting size (2-3 people = sparse, 5+ people = denser).
- Implementation: Plays as ambient loop during meeting scenes.

**Chair Pull-Out / Sit**
- Context: Player or NPC sits at the conference table.
- Tonal Description: Office chair roll on carpet or hard floor, slight scrape, seat compression. The sound of *taking a position*.
- Variations: 4 variations.
- Implementation: Triggered at meeting start or when NPCs enter.

**Binder / Document Folder Open**
- Context: Presenting materials in a meeting — opening a pilot proposal binder, a budget report, etc.
- Tonal Description: Three-ring binder snap open, pages settle. Heavier and more formal than script sounds. The sound of *official presentation*.
- Variations: 3 variations.
- Implementation: Triggered when player presents materials.

**Slide Advance / Projector Clicker**
- Context: Advancing through upfronts presentation slides.
- Tonal Description: Wireless presentation clicker — soft plastic button click, slight electronic beep. The sound of *controlling the narrative*.
- Variations: 2 variations.
- Implementation: Triggered on presentation advance input.

**Upfronts Presentation Hall Ambience**
- Context: Background sound layer for the upfronts presentation scene.
- Tonal Description: Large room tone — 50-100 people present. Gentle audience murmur before presentation begins, near-silence during presentation (with occasional cough, chair shift, whispered comment), rising murmur during strong moments, dead silence during weak moments. The sound of *your work being evaluated by people who only care about money*.
- Variations: 5 variations based on presentation moment (pre-show, strong moment, weak moment, transition, end).
- Implementation: Adaptive layer that responds to Ad Buyer Confidence meter movement during upfronts.

**Audience Reaction Sounds**
- Context: Discrete reactions to individual pilot presentations during upfronts.
- Tonal Description:
  - Positive: Interested murmur, slight forward lean rustle, pen-on-paper note-taking increase.
  - Neutral: Silence, the absence of reaction. The sound of *indifference*.
  - Negative: Skeptical murmur, phone activity increase (tapping, buzzing), chair shifts indicating disengagement.
- Variations: 8 variations across positive/neutral/negative valence.
- Implementation: Triggered based on Ad Buyer Confidence movement during each pilot presentation. Positive reactions when confidence rises, negative when it stalls or drops.

**Applause (Rare)**
- Context: End of a strong upfronts presentation, or a particularly bold/well-presented pilot.
- Tonal Description: Polite industry applause — not enthusiastic, but present. Mid-tempo clapping, professional. The sound of *approval, measured and conditional*.
- Variations: 2 variations (moderate applause, strong applause).
- Implementation: Triggered if final Ad Buyer Confidence for the season exceeds threshold (e.g., 75+).

**Upfronts Stage Footsteps**
- Context: Player walks to podium to begin presentation.
- Tonal Description: Dress shoes on stage floor — confident stride, measured pace. The sound of *walking into the spotlight*.
- Variations: 3 variations.
- Implementation: Plays as player enters upfronts presentation sequence.

**Podium Microphone Adjust**
- Context: Player adjusts microphone before speaking at upfronts.
- Tonal Description: Microphone stand adjustment — metal slide, slight feedback squeal (quickly suppressed), the sound of *preparing to speak to power*.
- Variations: 2 variations.
- Implementation: Triggered at upfronts presentation start.

### 3.5 UI FEEDBACK & SYSTEM NOTIFICATIONS

UI sounds must be informative without being intrusive, tactile without being obnoxious. Every UI sound should feel like an extension of the physical workspace, not a video game overlay.

**Button Hover**
- Context: Cursor hovers over an interactive UI element (button, script, project card).
- Tonal Description: Extremely subtle paper rustle or soft creak — the sound of *potential interaction*. Barely audible, just enough to register subconsciously.
- Variations: 4 variations.
- Implementation: Triggered on hover state. Volume: -18dB relative to primary SFX.

**Button Click / Confirm**
- Context: Player confirms a choice — greenlighting a pilot, giving a note, finalizing budget allocation.
- Tonal Description: Satisfying, tactile click — combination of mouse click and a subtle mechanical snap, like a high-quality pen click. The sound of *decision locked in*.
- Variations: 5 variations based on decision weight (minor decision = softer click, major decision = sharper, more resonant click).
- Implementation: Decision weight metadata determines variation.

**Button Cancel / Back**
- Context: Player cancels or backs out of a decision.
- Tonal Description: Softer, descending click — less satisfying than confirm. The sound of *retreating from commitment*.
- Variations: 3 variations.
- Implementation: Triggered on cancel/back input.

**Notification Appear**
- Context: System notification appears (new script arrival, ratings report, industry signal, etc.).
- Tonal Description: Soft two-tone chime — digital but warm, attention-grabbing without being alarming. The sound of *new information requiring attention*.
- Variations: 3 variations based on notification priority (low = single soft tone, medium = two-tone chime, high = slightly sharper two-tone with subtle urgency).
- Implementation: Priority-based variation selection.

**Notification Dismiss**
- Context: Player dismisses a notification.
- Tonal Description: Soft descending tone, or subtle paper-slide-away sound. The sound of *acknowledged and filed*.
- Variations: 2 variations.
- Implementation: Triggered on notification close.

**Positive Feedback (Success)**
- Context: A show performs well, a pilot tests positively, an upfronts presentation exceeds expectations.
- Tonal Description: Warm, ascending three-note chime — major key, optimistic but restrained. Not triumphant, just *good news*.
- Variations: 2 variations.
- Implementation: Triggered on positive outcome reveals (ratings above projection, test scores high, etc.).

**Negative Feedback (Failure)**
- Context: A show underperforms, a pilot tests poorly, a showrunner walks.
- Tonal Description: Descending two-note tone — minor interval, somber but not harsh. The sound of *bad news delivered professionally*.
- Variations: 2 variations.
- Implementation: Triggered on negative outcome reveals.

**Warning / Alert**
- Context: Budget overrun, project in crisis, expiration clock nearing zero, Network President patience dropping.
- Tonal Description: Slightly sharper two-tone chime with urgency — not alarm, but *pay attention now*. Higher frequency, faster attack.
- Variations: 2 variations (warning, critical alert).
- Implementation: Triggered on warning states. Critical alerts (e.g., President patience below 25, imminent firing) use sharper variation.

**Time Passage / Day Advance**
- Context: In-game day transitions, week advances, season progresses.
- Tonal Description: Soft clock tick or page-turn sound, depending on context. The sound of *time moving forward, with or without you*.
- Variations: 3 variations (day advance, week advance, season transition).
- Implementation: Triggered on time progression.

**Season Transition**
- Context: Transitioning from one development season to the next.
- Tonal Description: Longer, more significant sound event — combination of page turn, ambient fade-out/fade-in, and a soft musical sting (see Music section). The sound of *the cycle renewing*.
- Variations: 1 variation.
- Implementation: Triggered at season end after final evaluations.

**Menu Open / Close**
- Context: Player opens settings, budget reports, industry reports, or other meta-menus.
- Tonal Description: Soft folder open/close or binder snap. The sound of *accessing reference material*.
- Variations: 2 variations (open, close).
- Implementation: Triggered on menu state changes.

**Tooltip Appear**
- Context: Hover tooltip with additional information appears.
- Tonal Description: Extremely subtle soft tone or paper rustle — quieter than button hover. The sound of *clarification available*.
- Variations: 2 variations.
- Implementation: Triggered on tooltip display. Volume: -20dB.

### 3.6 ENVIRONMENTAL / AMBIENT LAYERS

Environmental sound establishes place, time, and mood. These are looping ambient beds that play continuously in each location, with adaptive variations based on time of day, season, and player state.

**Office — Daytime Ambience**
- Context: Office workspace during business hours.
- Tonal Description: HVAC hum (low, constant), distant office sounds (muffled voices down the hall, elevator ding, phone ringing in another office), occasional traffic through window. The sound of *the workday in progress around you*.
- Variations: 3 variations based on time of day (morning = more activity, midday = peak activity, late afternoon = activity winding down).
- Implementation: Looping ambient bed, crossfades between variations based on in-game time.

**Office — Evening/Night Ambience**
- Context: Office workspace after hours, late-night work sessions.
- Tonal Description: HVAC hum (slightly more prominent in the quiet), building settling creaks, very distant sounds (cleaning crew, security guard footsteps far away), the absence of daytime activity. The sound of *working alone when everyone else has left*.
- Variations: 2 variations (early evening = some distant activity, late night = near-total isolation).
- Implementation: Looping ambient bed, crossfades based on in-game time.

**Office — Window Ambience**
- Context: Ambient layer of exterior sound bleeding through office windows.
- Tonal Description: Distant LA traffic (gentle, not intrusive), occasional siren (far away), wind against building. The sound of *the city continuing outside while you work inside*.
- Variations: 4 variations based on time of day (morning rush, midday steady, evening rush, night quiet).
- Implementation: Looping layer mixed underneath primary office ambience.

**Screening Room Ambience**
- Context: Ambient layer in the screening room.
- Tonal Description: Near-silence. Very low HVAC hum, projector/monitor fan hum (when active), the sound of *negative space designed for focus*.
- Variations: 2 variations (projector on, projector off).
- Implementation: Looping ambient bed.

**Conference Room Ambience**
- Context: Ambient layer in meeting spaces (covered partially in Meetings section, expanded here).
- Tonal Description: Room tone with very subtle human presence indicators (breath, fabric rustle), HVAC slightly more present than office (conference rooms are often colder/more sterile). The sound of *professional space designed for group decisions*.
- Variations: 2 variations (meeting in progress, empty conference room).
- Implementation: Looping ambient bed.

**Upfronts Hall Ambience**
- Context: Ambient layer in the large presentation hall.
- Tonal Description: Large room tone, high ceiling acoustics, audience murmur (pre/post presentation), stage lighting hum. The sound of *a space designed for spectacle and judgment*.
- Variations: 5 variations (pre-show, during presentation, strong moment, weak moment, post-show).
- Implementation: Adaptive looping bed that responds to upfronts presentation state.

**Elevator Ambience**
- Context: Transition between floors (office to conference room, office to screening room, office to parking/exit).
- Tonal Description: Elevator mechanism hum, cable tension, gentle sway, floor indicator ding. Muzak plays softly (see Music section). The sound of *transition between spaces*.
- Variations: 2 variations (ascending, descending).
- Implementation: Plays during elevator transition scenes.

**Parking Garage / Exit Ambience**
- Context: End-of-day scenes where player leaves the office.
- Tonal Description: Concrete acoustics, car engine distant, footsteps with hard-surface echo, fluorescent light buzz. The sound of *leaving the work behind, for now*.
- Variations: 2 variations (evening, late night).
- Implementation: Plays during exit sequences.

### 3.7 SHOWRUNNER & NPC VOICES

Showrunners and NPCs (network president, agents, talent) speak to the player during meetings, phone calls, and notes sessions. All dialogue is text-based (no voice acting), but vocal presence is suggested through environmental sounds and text delivery pacing.

**Phone Call — Voice Filter**
- Context: When a character speaks on the phone, their text delivery is accompanied by a subtle "phone line" audio filter on ambient sound.
- Tonal Description: Slight band-pass filter on room tone, very subtle analog phone line noise (gentle hiss, occasional crackle). The sound of *mediated communication*.
- Variations: 2 variations (landline, cell phone).
- Implementation: Applied as audio filter during phone call scenes.

**Meeting — Character Presence Sounds**
- Context: When an NPC is speaking in a meeting, their presence is suggested through micro-sounds.
- Tonal Description: Slight chair shift, breath, paper rustle as they reference notes, pen tap for emphasis. The sound of *someone across the table from you*.
- Variations: 6 variations per character archetype (e.g., confident showrunner = minimal fidgeting, nervous first-timer = more fidgeting).
- Implementation: Triggered at dialogue beat markers.

**Showrunner Emotion Indicators**
- Context: During notes sessions, showrunner reactions to player notes are suggested through sound.
- Tonal Description:
  - Agreement/Trust: Soft affirmative hum, pen-on-paper note-taking, forward lean.
  - Disagreement/Resistance: Slight sigh, chair lean-back, silence.
  - Anger/Frustration: Sharp exhale, paper slap on table, chair scrape.
  - Enthusiasm: Quick speech rhythm indicator (faster ambient typing/paper rustle).
- Variations: 8 variations across emotional valence.
- Implementation: Triggered based on showrunner trust level and note type.

### 3.8 RATINGS & RESULTS

The reveal of ratings and performance data is a high-stakes moment. Audio must heighten the tension and payoff.

**Ratings Envelope Open**
- Context: Weekly ratings arrive as a physical document (early seasons) or email (later seasons).
- Tonal Description: Paper envelope tear (early seasons) or email notification chime (later seasons). The sound of *results about to be revealed*.
- Variations: 2 variations (physical, digital).
- Implementation: Period-based variation.

**Ratings Number Reveal — Ticker/Counter**
- Context: Viewership numbers are revealed on-screen, counting up from zero to final number.
- Tonal Description: Mechanical counter tick or digital increment beep — rhythmic, building tension as the number climbs. The sound of *quantification of success or failure*.
- Variations: 2 variations (analog ticker, digital counter).
- Implementation: Sound loops as number animates, stops at final value.

**Ratings Result — Success**
- Context: Ratings exceed projections or hit a milestone (e.g., #1 show, breakout hit).
- Tonal Description: Warm chime or subtle triumphant sting (musical, see Music section). The sound of *validation*.
- Variations: 2 variations (moderate success, major success).
- Implementation: Triggered based on performance threshold.

**Ratings Result — Failure**
- Context: Ratings fall below projections or trigger cancellation threshold.
- Tonal Description: Descending tone or muted musical sting. The sound of *loss*.
- Variations: 2 variations (underperformance, disaster).
- Implementation: Triggered based on performance threshold.

**Industry Headline Appear**
- Context: Trade publication headline appears on-screen (Variety, Hollywood Reporter).
- Tonal Description: Newspaper printing press sound (brief, subtle) or page-turn. The sound of *public record*.
- Variations: 3 variations.
- Implementation: Triggered when headlines display.

### 3.9 SPECIAL EVENTS & NARRATIVE MOMENTS

**Writers' Strike Announcement**
- Context: Season 6 — the Writers' Strike begins. Development halts.
- Tonal Description: Sudden ambient silence. Office sounds cut out. A single phone ring, distant. Then: picket chant ambience (distant, muffled through windows). The sound of *the machinery stopping*.
- Variations: 1 variation.
- Implementation: Hard-coded event trigger, overrides normal ambient layers.

**Network President — Low Patience Warning**
- Context: President patience drops below 25. The player is in danger.
- Tonal Description: Phone ring with increased urgency (faster ring pattern), or the sound of the President's office door opening (heavy door, authoritative). The sound of *being summoned*.
- Variations: 2 variations.
- Implementation: Triggered when patience crosses threshold.

**Showrunner Walk / Project Collapse**
- Context: A showrunner walks off a project due to creative conflict.
- Tonal Description: Sudden silence in the meeting ambience. A chair scrapes back sharply. Footsteps walking away. Door close. The sound of *rupture*.
- Variations: 1 variation.
- Implementation: Triggered on showrunner walk event.

**Career Retrospective — Final Sequence**
- Context: End of Season 8, career retrospective plays.
- Tonal Description: Ambient office sounds fade into distant memory — voices, phone rings, script pages all become ghostly, reverb-heavy, distant. The sound of *looking back*.
- Variations: 1 variation.
- Implementation: Applied as audio processing during retrospective sequence.

---

## 4. MUSIC SYSTEM

Music in PILOT is sparse, contextual, and emotionally restrained. It is not a constant presence. Music arrives at emotional peaks, location-specific contexts, and moments of reflection. The score is adaptive, responding to player state, narrative tension, and seasonal arc.

### 4.1 Musical Style & Instrumentation

**Primary Palette**:
- Piano (primary melodic voice — warm, intimate, slightly melancholy)
- Strings (sustain, emotional swell, used sparingly for high-stakes moments)
- Analog synthesizers (textural pads, subtle progression, the sound of institutional modernity)
- Prepared piano / textural piano (percussive, rhythmic, the sound of thought process)
- Minimal percussion (brushes on snare, soft mallets, felt bass drum — rhythm without aggression)

**Avoided**:
- Guitars (too Americana, too indie)
- Brass (too triumphant, too cinematic)
- Orchestral bombast
- Electronic beats (too propulsive, too game-y)

**Reference Tone**: If Thomas Newman scored a game about the loneliness of creative decision-making in fluorescent-lit rooms, this is that score.

### 4.2 Music Cues — Organized by Context

#### Location Themes (Ambient, Looping)

**Office — Daytime Theme**
- Context: Plays quietly underneath office ambience during low-stress desk work.
- Instrumentation: Solo piano, minimal synth pad.
- Tempo: Slow (60-70 BPM).
- Mood: Contemplative, warm but not sentimental. The sound of *work as ritual*.
- Adaptive Behavior: Volume ducks when player is actively reading scripts or making decisions (the music respects focus). Volume rises slightly during idle moments.
- Length: 4-minute loop with variation.

**Office — Late Night Theme**
- Context: Plays during late-night work sessions (after hours).
- Instrumentation: Piano with more reverb, darker synth pad, very subtle string sustain.
- Tempo: Slower (55-65 BPM).
- Mood: Isolation, determination, melancholy. The sound of *working alone when you should be home*.
- Adaptive Behavior: Intensity increases if player has been working for extended session (2+ hours real-time). Fatigue is audible.
- Length: 5-minute loop with variation.

**Screening Room Theme**
- Context: Plays softly during rough cut screenings, underlying the pilot audio.
- Instrumentation: Ambient synth pad only, no melody. Textural, not musical.
- Tempo: N/A (atmospheric).
- Mood: Focus, anticipation, the sound of *bearing witness*.
- Adaptive Behavior: Fades to near-silence during critical rough cut moments (final scenes, emotional peaks). Allows the work to speak.
- Length: Generative ambient bed, no fixed loop.

**Elevator Muzak**
- Context: Plays during elevator transitions.
- Instrumentation: Cheesy period-appropriate elevator music — soft strings, bland melody, overcompressed. Slightly ironic.
- Tempo: Mid-tempo (90-100 BPM).
- Mood: Banal corporate comfort. The sound of *in-between spaces*.
- Adaptive Behavior: None. Muzak is indifferent.
- Length: 2-minute loop.

#### Emotional / Narrative Cues

**Upfronts — Pre-Show**
- Context: Plays as player prepares for upfronts presentation, assembles slate, writes pitch lines.
- Instrumentation: Piano + subtle strings + soft prepared piano rhythm.
- Tempo: Moderate (75-85 BPM).
- Mood: Anticipation, controlled nerves, the sound of *preparing to defend your taste*.
- Adaptive Behavior: None (linear cue).
- Length: 3 minutes, loops if player takes longer than expected.

**Upfronts — Presentation (Adaptive)**
- Context: Plays during upfronts presentation. This is the game's most complex adaptive music cue.
- Instrumentation: Full ensemble — piano, strings, synth, minimal percussion.
- Tempo: Starts moderate (80 BPM), can accelerate or slow based on presentation success.
- Mood: HIGH-STAKES. The sound of *your entire season being judged in real time*.
- Adaptive Behavior:
  - **Baseline Layer**: Piano + synth pad (always present).
  - **Confidence Rising Layer**: Strings enter and swell as Ad Buyer Confidence increases. Melody ascends.
  - **Confidence Stalling Layer**: Strings pull back, percussion drops out, piano becomes sparser. Tension held.
  - **Confidence Dropping Layer**: Descending bass notes, minor key shift, the sound of *losing the room*.
  - **Final Commit**: Full ensemble swell (if successful presentation) or quiet piano resolution (if weak presentation).
- Length: 7-10 minutes, dynamically composed based on presentation flow.

**Ratings Reveal — Tension**
- Context: Plays as ratings data is loading/being revealed.
- Instrumentation: Synth pulse, soft string tremolo, piano sparsely.
- Tempo: Slow, rhythmic (60 BPM pulse).
- Mood: Suspense, the sound of *waiting to learn if you were right*.
- Adaptive Behavior: Crescendos as numbers tick upward, holds tension if numbers are ambiguous.
- Length: 30-60 seconds (varies with reveal pacing).

**Ratings Reveal — Success**
- Context: Plays when ratings exceed expectations or a show becomes a hit.
- Instrumentation: Piano melody (major key), warm strings, subtle synth swell.
- Tempo: Moderate (80 BPM).
- Mood: Validation, relief, quiet triumph. Not celebration — *acknowledgment*.
- Adaptive Behavior: None (linear cue).
- Length: 45 seconds, fades to ambient.

**Ratings Reveal — Failure**
- Context: Plays when ratings fall below threshold or a show is cancelled.
- Instrumentation: Piano (minor key, descending), soft string sustain, no rhythm.
- Tempo: Slow (55 BPM).
- Mood: Loss, regret, the sound of *something ending*.
- Adaptive Behavior: None (linear cue).
- Length: 1 minute, fades to silence.

**Showrunner Trust — Bond Moment**
- Context: Plays when player earns significant trust with a key showrunner (e.g., protecting their vision against network pressure, successful collaboration).
- Instrumentation: Solo piano, warm and intimate.
- Tempo: Slow (60 BPM).
- Mood: Connection, mutual respect, the sound of *finding an ally*.
- Adaptive Behavior: None (linear cue).
- Length: 1 minute.

**Showrunner Trust — Rupture Moment**
- Context: Plays when a showrunner walks or trust is irrevocably damaged.
- Instrumentation: Dissonant piano chord, held; soft distorted synth.
- Tempo: N/A (sustained).
- Mood: Fracture, the sound of *a relationship ending*.
- Adaptive Behavior: None (linear cue).
- Length: 20 seconds, fades to silence.

**Season Transition Sting**
- Context: Plays as one season ends and the next begins.
- Instrumentation: Piano + strings, brief melodic phrase (unresolved harmony).
- Tempo: Free tempo.
- Mood: Reflection and continuation. The sound of *the cycle renewing, lessons unlearned or learned*.
- Adaptive Behavior: Harmony resolves major if previous season was successful, minor if previous season struggled.
- Length: 15 seconds.

**Writers' Strike — Crisis**
- Context: Plays during the Writers' Strike event (Season 6).
- Instrumentation: Sparse piano, distorted synth drone, no rhythm.
- Tempo: Very slow (40 BPM feel).
- Mood: Disruption, uncertainty, the sound of *the machinery breaking*.
- Adaptive Behavior: None (linear cue).
- Length: 2 minutes, fades to silence.

**Career Retrospective — Endgame**
- Context: Plays during the final career retrospective at the end of Season 8.
- Instrumentation: Full ensemble — piano (primary melody), strings (emotional core), synth (texture), soft percussion.
- Tempo: Slow, reflective (55-65 BPM).
- Mood: Legacy, reckoning, melancholy, the sound of *looking back at a body of work and asking if it mattered*.
- Adaptive Behavior: Melodic content and harmonic resolution vary based on player's career outcomes:
  - **High Prestige / Cultural Footprint**: Major key resolution, strings swell with pride.
  - **High Commercial Success / Low Prestige**: Ambiguous harmony, the sound of *money earned, meaning questioned*.
  - **Mixed / Balanced Career**: Bittersweet resolution, major-minor oscillation.
  - **Failure / Low Scores**: Minor key, unresolved harmony, the sound of *regret*.
- Length: 3-4 minutes.

#### UI Music (Minimal)

**Main Menu Theme**
- Context: Title screen / main menu.
- Instrumentation: Solo piano, very minimal.
- Tempo: Slow (60 BPM).
- Mood: Invitation, the sound of *potential*.
- Length: 2-minute loop.

**Credits Theme**
- Context: End credits after career retrospective.
- Instrumentation: Piano + strings, fuller than main menu but still restrained.
- Tempo: Moderate (70 BPM).
- Mood: Closure, gratitude, the sound of *the story ending*.
- Length: 3-4 minutes.

### 4.3 Adaptive Music System Architecture

**Layered Stems**: Key adaptive cues (Office themes, Upfronts Presentation, Ratings Reveal) are composed as multi-stem layers that can be mixed in real-time based on game state.

**Example — Upfronts Presentation Stems**:
1. Baseline (Piano + Synth Pad) — always playing
2. Confidence Rising (Strings, ascending melody)
3. Confidence Stalling (Sparse piano, tension sustain)
4. Confidence Dropping (Bass descent, minor shift)
5. Percussion (enters during strong moments, exits during weak)

The audio engine crossfades between stems based on Ad Buyer Confidence movement. Transitions are smooth (2-4 second crossfade) to avoid jarring shifts.

**Dynamic Mixing**: Music volume ducks dynamically:
- When player is reading text (script, coverage, notes): music volume -6dB.
- When SFX events occur (phone ring, notification): music ducks -3dB for duration of SFX.
- During critical silence moments (post-rough-cut, post-kill decision): music fades to silence entirely.

**Silence as Music**: The score respects silence. Many high-stakes moments (killing a pilot, a showrunner walking, firing) are followed by 5-10 seconds of complete musical silence. The absence of music is an active compositional choice.

---

## 5. ADAPTIVE AUDIO SYSTEM DESIGN

PILOT's audio responds to player state, narrative tension, seasonal progression, and emotional arc. The soundscape is not static. It listens to the player and reacts.

### 5.1 Player State Reactivity

**Stress Level Tracking**:
The game tracks player stress based on:
- Number of unresolved decisions (scripts in CONSIDER pile, projects flagged for attention)
- Proximity to deadlines (expiration clocks, upfronts date)
- Network President patience level
- Budget pressure (operating deficit, cash crisis)

Stress level (0-100) modulates:
- **Ambient sound density**: Higher stress = denser office ambience (more distant phones, more HVAC presence).
- **Fidget sound frequency**: Pen taps, chair creaks increase at high stress.
- **Music intensity**: Office themes gain subtle tension layers (string sustain, faster piano rhythm) at stress > 60.

**Focus State Detection**:
When player is deep-reading a script or watching a rough cut (sustained attention on single task for 60+ seconds), the soundscape simplifies:
- Ambient layers reduce in volume (-4dB).
- Music (if playing) reduces to minimal texture.
- No notification sounds interrupt (queued for after focus state ends).

This respects player concentration. Audio creates space for thought.

### 5.2 Seasonal Arc Modulation

Each season (1-8) has a distinct sonic identity that reflects the industry landscape and narrative stakes.

**Season 1-2 (Learning, Optimism)**:
- Office ambience: Lighter, more daytime activity.
- Music: Major key bias, hopeful piano melodies.
- Phone rings: Standard urgency.

**Season 3-4 (Gold Rush, Pressure)**:
- Office ambience: Denser, more phones ringing (opportunity and chaos).
- Music: Increased tempo, more rhythmic drive.
- Phone rings: More frequent, higher urgency.

**Season 5-6 (Reckoning, Crisis)**:
- Office ambience: Sparser (people leaving for cable), more late-night sessions.
- Music: Minor key shift, darker piano tones, string tension.
- Phone rings: Fewer but more consequential (every call is high-stakes).

**Season 6 (Writers' Strike)**:
- Office ambience: Disrupted. Distant picket chants. Phones silent.
- Music: Minimal, dissonant.
- Special soundscape override for strike duration.

**Season 7-8 (Fragmentation, Legacy)**:
- Office ambience: Reflective. More silence, less institutional noise (the era is ending).
- Music: Retrospective themes, unresolved harmonies.
- Phone rings: Rare. The industry has moved on.

### 5.3 Relationship-Responsive Audio

**Showrunner Trust Levels**:
During notes sessions and meetings with showrunners, ambient sound reacts to trust level:
- **High Trust (70+)**: Collaborative sounds — mutual note-taking, affirmative hums, forward-leaning chair creaks.
- **Medium Trust (40-69)**: Neutral sounds — standard meeting ambience.
- **Low Trust (< 40)**: Tension sounds — silences, resistant chair lean-backs, paper slaps.

**Network President Patience**:
Presidential meeting ambience changes with patience level:
- **High Patience (70+)**: Relaxed tone, casual chair sounds, the President's dialogue is punctuated with warm sounds.
- **Low Patience (< 30)**: Cold silence between dialogue beats, no ambient warmth, the sound of *being evaluated*.

### 5.4 Contextual Audio Layers

**Time-of-Day System**:
Office ambience, window sounds, and music themes shift based on in-game time:
- **Morning (6am-12pm)**: Rising activity, traffic, energetic ambience.
- **Afternoon (12pm-6pm)**: Peak activity, steady hum.
- **Evening (6pm-10pm)**: Declining activity, more isolation.
- **Night (10pm-6am)**: Near-silence, lone worker sounds, the hum of the building.

**Weather System (Subtle)**:
Occasional weather variation affects window ambience:
- Rain: Soft rain against window, distant thunder (rare).
- Wind: Increased wind noise, building creak.
- Clear: Standard traffic, distant city hum.

Weather is not a gameplay mechanic, but it adds emotional texture. A late-night work session during a rainstorm sounds different from a clear night.

---

## 6. MIX HIERARCHY

Audio information must be prioritized. The player needs to hear what matters. The mix hierarchy defines what takes precedence in the frequency spectrum and dynamic range.

### 6.1 Priority Tiers (Highest to Lowest)

**TIER 1 — CRITICAL INFORMATION (Always Audible)**:
- Phone rings (incoming calls)
- Urgent notifications (warnings, alerts, critical decisions)
- Showrunner/NPC dialogue text delivery sounds (presence indicators)
- Upfronts audience reaction (during presentation)

These sounds duck all other layers by -6dB when active. They cannot be missed.

**TIER 2 — PRIMARY INTERACTION FEEDBACK**:
- Script interactions (page turns, desk slides, triage actions)
- UI button clicks and confirmations
- Whiteboard/pipeline interactions
- Ratings reveals

These sounds duck ambient and music by -3dB when active.

**TIER 3 — ENVIRONMENTAL PRESENCE**:
- Office ambience layers
- Screening room ambience
- Meeting room ambience

These establish place but never compete with interaction sounds. They sit in the low-mid frequency range (100-500 Hz for HVAC, 500-2kHz for room tone) and avoid frequency clashes with higher-priority sounds.

**TIER 4 — MUSIC**:
- All music cues

Music is the lowest priority. It supports emotion but never obscures information. Music occupies the mid-high frequency range (piano 200-4kHz, strings 300-8kHz) and is mixed to sit *under* dialogue and SFX, not over them.

**TIER 5 — SUBTLE DETAILS (Flavor, Not Function)**:
- Pen taps, coffee mug sounds, fidget sounds
- Distant office sounds (elevator dings, doors closing)
- Weather ambience

These add texture but are barely audible (mixed at -12 to -18dB relative to primary SFX). They reward close listening but are not essential.

### 6.2 Frequency Allocation

**Low (20-200 Hz)**:
- HVAC hum, building rumble, bass elements of music (rare).
- Restrained use. PILOT is not a bass-heavy game. Low frequencies should be *felt* more than heard.

**Low-Mid (200-500 Hz)**:
- Room tone, ambient presence, wood desk resonance, chair creaks.
- The body of the soundscape.

**Mid (500-2kHz)**:
- Paper sounds, voice presence (phone calls, meeting ambience), piano (fundamental).
- The core frequency range for interaction sounds.

**High-Mid (2-6kHz)**:
- Clarity and detail layer. Phone rings, notification chimes, keyboard clicks, paper rustle overtones.
- Where attention-grabbing sounds live.

**High (6-20kHz)**:
- Air, space, analog warmth overtones, string harmonics.
- Textural layer. Adds dimension without occupying foreground.

**Frequency Ducking**:
When a Tier 1 sound plays (e.g., phone ring at 2-4kHz), a dynamic EQ dips other sounds in the 1.5-5kHz range by 3-6dB, creating space for the critical sound.

### 6.3 Dynamic Range Philosophy

**Target Dynamic Range**: -40dB (quietest sound) to -6dB (loudest sound), with -12dB as the comfortable average playback level.

PILOT is not a loud game. The mix is quiet, intimate, detailed. The player should be able to hear the grain of paper and the creak of a chair. This requires:
- **Controlled peaks**: No sudden loud sounds (except rare critical alerts).
- **Detailed quiet**: The lowest sounds (ambient details, fidget sounds) are still audible and textured, not lost in noise floor.
- **Headphone-optimized mix**: The game is designed for headphone listening. Stereo field is wide but not exaggerated. Panning is subtle (scripts sliding left/right on desk, spatial positioning in meetings).

**Loudness Standard**: -16 LUFS (integrated loudness) across a full session. Quieter than most games, intentionally. The player leans in to listen.

---

## 7. IMPLEMENTATION PLAN & TECHNICAL REQUIREMENTS

### 7.1 Audio Middleware

**Recommended Platform**: FMOD Studio or Wwise.

**Rationale**: PILOT requires:
- Adaptive music (layered stems, real-time crossfading based on game state).
- Dynamic mixing (ducking, priority-based attenuation).
- Randomized variation pools (script sounds, ambient details).
- Parameter-driven audio (stress level, trust level, seasonal modulation).
- 3D spatial audio (minimal, for meeting/upfronts scenes).

Both FMOD and Wwise support these features. FMOD has a gentler learning curve for a small team. Wwise has deeper parameter control for complex adaptive systems. Either works.

### 7.2 Audio Asset Specifications

**Sample Rate**: 48kHz (industry standard for games).
**Bit Depth**: 24-bit for source assets, 16-bit for final compressed delivery.
**File Format**: WAV (source), Ogg Vorbis or MP3 (compressed delivery, quality setting: Q8 for Ogg, 192kbps for MP3).

**Asset Count Estimate**:
- SFX: ~600-800 individual sound files (including variations).
- Music: ~25-30 cues/stems, totaling ~60-90 minutes of composed music.
- Ambience: ~15-20 looping beds.

**Total Audio Footprint (Compressed)**: ~400-600 MB.

### 7.3 Implementation Priorities (Phased Development)

**Phase 1 — Core Loop Audio (Prototype/Vertical Slice)**:
- Desk interface SFX (script sounds, UI clicks, paper interactions).
- Office daytime ambience.
- Basic UI feedback sounds.
- One adaptive music cue (Office theme).

**Deliverable**: The 30-second loop (triage at desk) sounds and feels complete.

**Phase 2 — Development Pipeline & Notes**:
- Whiteboard/pipeline SFX.
- Meeting ambience and NPC presence sounds.
- Notes session adaptive audio (showrunner trust reactivity).
- Screening room ambience and rough cut playback sounds.

**Deliverable**: The 5-minute loop (develop a pilot) is fully audio-designed.

**Phase 3 — Upfronts & Seasonal Flow**:
- Upfronts presentation adaptive music system.
- Audience reaction sounds.
- Ratings reveal SFX and music.
- Season transition sounds.
- Full ambient system (time-of-day, seasonal variations).

**Deliverable**: A complete development season (45-90 minutes) has full audio coverage.

**Phase 4 — Depth & Polish**:
- All subtle detail sounds (fidget, environmental flavor).
- Showrunner/NPC character-specific presence sounds.
- Special event audio (Writers' Strike, career retrospective).
- Final music cues (all emotional beats, endgame).
- Mix polish and mastering.

**Deliverable**: 8-season campaign is fully scored and sound-designed.

### 7.4 Audio Parameters (Game State to Audio Middleware)

The game engine must expose the following parameters to the audio middleware for adaptive behavior:

| Parameter | Type | Range | Affects |
|---|---|---|---|
| Player Stress Level | Float | 0.0 - 1.0 | Ambient density, fidget frequency, music tension |
| Network President Patience | Float | 0.0 - 1.0 | Meeting ambience tone, phone ring urgency |
| Showrunner Trust (per character) | Float | 0.0 - 1.0 | Notes session sounds, meeting presence |
| Season Number | Int | 1 - 8 | Ambient tone, music theme selection |
| Time of Day | Int | 0-23 (hour) | Ambient layers, music theme, window sounds |
| Focus State | Bool | True/False | Ambient volume, notification suppression |
| Ad Buyer Confidence (Upfronts) | Float | 0.0 - 1.0 | Music stem mixing, audience reaction |
| Ratings Performance | Float | -1.0 (disaster) to 1.0 (hit) | Music cue selection, result sound |
| Script Quality Variance | Float | -1.0 to 1.0 | Script landing sound weight (subtle) |
| Location | Enum | Office / Screening / Meeting / Upfronts / Elevator / Exit | Ambience bed selection |

### 7.5 Audio Team Structure (Recommended)

For a game of PILOT's scope:
- **1 Audio Director / Composer** (ECHO): Overall sonic vision, music composition, sound design direction.
- **1 Sound Designer**: SFX creation and implementation, FMOD/Wwise event scripting.
- **1 Audio Implementer / Technical Sound Designer** (can be same as Sound Designer): Middleware integration, parameter scripting, adaptive system design.
- **Contract Foley Artist** (2-3 sessions): Record high-quality paper, desk, office, and wardrobe foley. PILOT's tactile feel depends on detailed, well-recorded foley.
- **Mixing Engineer** (final phase): Final mix pass, loudness mastering, QA.

**Timeline Estimate**: 6-9 months for full audio production (from Phase 1 to final delivery), depending on team availability and iteration cycles.

---

## 8. SILENCE MAP — WHERE AND WHY SILENCE IS USED

Silence is not the absence of sound. Silence is a sound design choice. In PILOT, silence creates weight, emphasizes consequence, and respects the player's emotional state.

### 8.1 Mandatory Silence Moments

**After Killing a Pilot (Dead Pilots Drawer Close)**:
- Duration: 3 seconds.
- What is Silent: Music, ambient details (pen taps, distant office sounds). Only core room tone (HVAC hum) remains.
- Why: The player has just ended something. That ending deserves space. The silence is the game acknowledging: *this mattered*.

**After Rough Cut Ends (Before Evaluation UI)**:
- Duration: 3 seconds.
- What is Silent: Everything except screening room projector/monitor hum.
- Why: The player sits in the dark, processing what they just watched. The work speaks. The game does not interrupt.

**Showrunner Walks (After Rupture Moment)**:
- Duration: 5 seconds.
- What is Silent: Music, meeting ambience. Only distant building sounds remain.
- Why: A relationship has ended. The silence is the absence of that person. It feels empty because it is.

**Firing / Game Over (Network President Dismissal)**:
- Duration: 8 seconds.
- What is Silent: Everything. Complete silence.
- Why: The player's tenure is over. The machinery continues without them, but in this moment, there is nothing. The silence is existential.

**Pre-Upfronts (Player Alone Before Presentation)**:
- Duration: 4 seconds.
- What is Silent: Music fades out. Only breathing room tone. The player is about to walk on stage.
- Why: The held breath before the dive. Silence is anticipation.

**Career Retrospective Transition (End of Season 8 Gameplay)**:
- Duration: 6 seconds.
- What is Silent: All gameplay sounds cease. Silence before retrospective music begins.
- Why: The game is over. The player's work is done. The silence is the boundary between play and reflection.

### 8.2 Dynamic Silence (Context-Dependent)

**Focus State Silence**:
- When player is deep-reading or watching a rough cut, all non-essential sounds suppress. Music fades to near-silence (-12dB or more). Notifications queue instead of playing. The soundscape creates a bubble of concentration.

**Late Night Office Silence**:
- After 10 PM in-game time, ambient office sounds reduce to minimal. No distant phones, no elevator dings. The building is empty. The soundscape reflects isolation.

**Budget Crisis Silence**:
- When player enters a cash crisis (development budget halved), office ambience thins noticeably. Fewer scripts arrive (fewer script-landing sounds). The sonic world reflects scarcity.

**High Trust Showrunner Moments**:
- During notes sessions with a high-trust showrunner, there are deliberate pauses — 1-2 second silences — where neither party speaks, just thinks. The silence is collaborative, not tense. Two people who respect each other do not need to fill every gap.

### 8.3 Silence as Contrast

Silence is most powerful in contrast to density. The Upfronts presentation is dense — music, audience, spatial sound. When the presentation ends and the player returns to their empty office, the silence (or near-silence) feels vast. The game uses silence to punctuate transitions from public to private, from noise to stillness.

---

## CLOSING NOTE

Audio IS game feel.

Every script that lands on the desk, every page turned, every note given, every pilot killed — these are not abstractions. They are physical, textured, consequential. The player must *feel* the weight of paper, the resonance of a decision, the silence after something ends.

PILOT does not sound like excitement. It sounds like concentration. It sounds like taste being tested against machinery. It sounds like the particular loneliness of being the person who decides. The frequency of this game's emotion is controlled tension with periodic release — the slow accumulation of pressure, the catharsis of a hit, the hollow quiet of a failure.

Listen to the space between heartbeats. That is where PILOT lives.

The sonic palette is warm analog grain meeting institutional sterility. The music is sparse, arriving only when silence is no longer enough. The soundscape is detailed, rewarding close listening, punishing inattention. The mix hierarchy ensures the player hears what matters. The adaptive systems respond to stress, to trust, to the passage of seasons and the weight of legacy.

This document is production-ready. Every sound is specified. Every system is mapped. The silence is intentional.

Now: build it, and listen.

— ECHO
