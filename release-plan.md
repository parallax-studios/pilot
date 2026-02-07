# PILOT — Release Plan

**Author**: SHIP (Release Manager)
**Version**: 1.0
**Date**: 2026-02-07
**Status**: Production-Ready Release Blueprint

---

## 0. EXECUTIVE SUMMARY

This is the release plan for PILOT, a single-player management sim targeting PC/Mac on Steam. 8-season campaign. Text-heavy, data-driven. No multiplayer, no live service, no server dependencies. The entire game ships in the build. Platform strategy: Steam primary, Mac day-one parity, Switch 6-8 months post-launch if the game hits 50K sales.

Target launch date: **18-24 months from greenlight** (per technical architecture). This document assumes we are at **Month 16** (post-beta, entering final polish). Launch window: **8 weeks from code freeze to public launch**.

Core release philosophy: **Make launch day boring.** If nothing goes wrong, I did my job. This plan covers:

1. Master launch checklist (build, platform, store, post-launch)
2. Build pipeline documentation (steps, tools, automation)
3. Platform configuration (Steamworks, age ratings, regional considerations)
4. Rollback and hotfix procedures
5. Launch day timeline (hour-by-hour)
6. Post-launch monitoring plan (what to watch, when to act)

No surprises. No "we'll figure it out later." Every step is defined. Every risk has a mitigation. If it is not on the checklist, it does not happen.

---

## 1. MASTER LAUNCH CHECKLIST

### 1.1 Build Readiness (Weeks -8 to -4)

**Code Freeze & Gold Master**

- [ ] **Week -8: Code Freeze** — No new features. Bug fixes only. Branch `release/1.0` created from `main`.
- [ ] All critical bugs closed (P0: crashes, progression blockers, save corruption).
- [ ] All high-priority bugs closed or deferred to post-launch patch (P1: major balance issues, UI jank).
- [ ] Unit tests pass (target: 80% code coverage for simulation logic).
- [ ] Content validation pipeline passes (no orphaned dilemma IDs, no invalid stat ranges, no missing localization keys).
- [ ] Full 8-season playthrough completed by QA with no critical issues (estimated 12-15 hours playtime).
- [ ] Save/load tested across all 8 seasons (no corruption, no migration failures).
- [ ] Performance targets met: 60fps on 2019 MacBook Pro at 1920x1080.
- [ ] Memory footprint verified under 500MB during full 8-season run.
- [ ] **Week -6: Gold Master Build** — Final candidate build created. Version number locked: `1.0.0`.
- [ ] Gold master tested on clean machines (Windows 10, Windows 11, macOS Monterey, macOS Ventura).
- [ ] Gold master passes full regression suite (QA runs 8-season playthrough again on gold build).
- [ ] Gold master approved by lead developer and QA lead. Build hash recorded. This is the build that ships.

**Build Artifacts**

- [ ] Windows x64 build (Standalone, 64-bit, compressed).
- [ ] macOS Universal build (Intel + Apple Silicon, .app bundle, code-signed with Apple Developer cert).
- [ ] Linux build (optional, only if demand exists — defer to post-launch if team is small).
- [ ] All builds uploaded to secure storage (Google Drive, AWS S3, or Steam partner backend).
- [ ] Build hashes (SHA256) recorded in release notes spreadsheet.

**Clean Machine Testing**

- [ ] Install Windows 10 Pro (fresh VM or physical machine). Install Steam. Download gold build. Launch. Play 30 minutes. No crashes.
- [ ] Install Windows 11 (fresh VM or physical machine). Install Steam. Download gold build. Launch. Play 30 minutes. No crashes.
- [ ] Install macOS Monterey (Intel Mac). Install Steam. Download gold build. Launch. Play 30 minutes. No crashes.
- [ ] Install macOS Ventura (Apple Silicon Mac). Install Steam. Download gold build. Launch. Play 30 minutes. No crashes.
- [ ] Test on minimum spec hardware: 2019 MacBook Pro (i5, integrated GPU). Verify 60fps at 1920x1080.

If the build works on a clean machine, it will work for customers. If it does not work on a clean machine, it does NOT ship.

---

### 1.2 Platform Configuration: Steamworks (Weeks -6 to -4)

**Steam Partner Account Setup**

- [ ] Steamworks partner account active. App ID assigned (e.g., `123456`).
- [ ] Developer/publisher company information verified (bank details, tax forms submitted to Valve).
- [ ] Contact emails configured (support email, press email, technical contact).
- [ ] Steam Direct fee paid ($100 per app, one-time, non-refundable).

**Store Page Configuration**

- [ ] **App Name**: "PILOT" (verify no trademark conflicts — search USPTO, EU trademarks).
- [ ] **Short Description** (300 characters max): "You decide what America watches. Build a television network in the golden age of TV. Greenlight shows, manage showrunners, give notes that shape the product. Every decision is a bet. Every cancellation is a scar. Your taste is the mechanic."
- [ ] **About This Game** (long description, ~500 words): Authored by HYPE (Marketing). Includes:
  - Elevator pitch
  - Core loop description (desk triage, development, notes, upfronts)
  - Key features (80 pilot concepts, 200+ creative dilemmas, 8-season campaign, emergent showrunner relationships)
  - Target audience hint ("For fans of Game Dev Tycoon, Football Manager, and prestige television")
  - "No microtransactions. No DLC at launch. One purchase, full game."
- [ ] **Genre Tags** (select up to 20): Simulation, Management, Strategy, Singleplayer, Story Rich, Choices Matter, 2000s, Television, Indie, Atmospheric, Drama, Replay Value, Resource Management, Economy, Character-Driven.
- [ ] **Supported Languages**: English (UI and audio). Optional: Localization for French, German, Spanish (defer to post-launch if budget tight).
- [ ] **System Requirements**:

**Minimum (Windows):**
- OS: Windows 10 64-bit
- Processor: Intel Core i5-4460 or equivalent
- Memory: 4 GB RAM
- Graphics: Integrated GPU (Intel HD 4000 or better)
- Storage: 500 MB available space

**Recommended (Windows):**
- OS: Windows 10/11 64-bit
- Processor: Intel Core i5-8400 or equivalent
- Memory: 8 GB RAM
- Graphics: Any dedicated GPU
- Storage: 1 GB available space

**Minimum (macOS):**
- OS: macOS 10.15 (Catalina) or later
- Processor: Intel Core i5 or Apple M1
- Memory: 4 GB RAM
- Graphics: Integrated GPU
- Storage: 500 MB available space

**Recommended (macOS):**
- OS: macOS 12 (Monterey) or later
- Processor: Apple M1/M2 or Intel i7
- Memory: 8 GB RAM
- Graphics: Any dedicated GPU or M1/M2 integrated
- Storage: 1 GB available space

- [ ] **Release Date**: Set to "Coming Soon" until Week -2. Update to exact launch date (e.g., "March 15, 2026") at Week -2.
- [ ] **Pricing**: $19.99 USD base price. Regional pricing set via Steam's auto-conversion (verify it does not round to ugly numbers like $20.47 — manually adjust if needed). Launch discount: NO. Launch at full price. Discounts start 3 months post-launch.
- [ ] **Age Rating**: ESRB E10+ (Everyone 10+) or PEGI 12. Justification: Mild thematic elements (corporate pressure, creative conflict), no violence, no sexual content, no profanity. See Section 3 for full age rating process.

**Store Page Assets**

- [ ] **Header Capsule** (460x215): Key art showing the desk, scripts, rough cut monitor. Must read at thumbnail size.
- [ ] **Main Capsule** (616x353): Same key art, higher resolution.
- [ ] **Small Capsule** (231x87): Simplified version of key art (logo + tagline only).
- [ ] **Hero Capsule** (1920x620 with logo overlay): Wide desk shot, scripts, LA office window view at golden hour.
- [ ] **Screenshots** (minimum 5, recommended 10):
  1. The Desk (script triage interface, 15 scripts visible)
  2. Development Pipeline (whiteboard with 8 pilots in various stages)
  3. Notes System (a creative dilemma with 3 options visible, full context text)
  4. Upfronts Presentation (ad buyer confidence meter, pilot being pitched)
  5. Network Brand Radar Chart (4-axis chart showing Prestige/Risk/Auteur/Serialized)
  6. Season Ratings Screen (weekly viewership graph, headlines)
  7. Showrunner Profile (character card with stats, trust meter, project history)
  8. Rough Cut Feedback (test audience scores, demographic breakdown, authored comments)
  9. Landscape Dashboard (trend vectors, industry signals, rival network activity)
  10. End-of-Career Retrospective (narrator text, legacy summary)
- [ ] **Trailer** (1-2 minutes, 1080p, upload to Steam and YouTube):
  - 0:00-0:10: Hook. "You decide what America watches."
  - 0:10-0:30: Desk montage. Scripts piling up, ticking clocks, triage decisions.
  - 0:30-0:50: Development. Showrunner attachments, casting, budget allocation.
  - 0:50-1:10: Notes System. Creative dilemmas, player hovering between options. "Protect the vision or chase the ratings?"
  - 1:10-1:30: Upfronts. Presentation sequence, ad buyer reactions, revenue commits.
  - 1:30-1:50: Season outcomes. Ratings headlines, critical acclaim, cancellations.
  - 1:50-2:00: End card. Logo, tagline ("Your taste is the mechanic"), release date, wishlist call-to-action.
- [ ] Trailer uploaded to Steam, set as primary video.
- [ ] Trailer uploaded to YouTube (unlisted or public, depending on pre-launch marketing strategy).

**Steamworks Features Configuration**

- [ ] **Achievements** (optional but recommended, target 20-30):
  - "First Greenlight" — Greenlight your first series.
  - "The Hit" — A series averages 15M+ viewers for a full season.
  - "Critical Darling" — A series scores 80+ with critics despite sub-5M ratings.
  - "The Flop" — Cancel a series after 3 episodes due to catastrophic ratings.
  - "Trust Issues" — Drop a showrunner's trust below 10.
  - "Loyal Partner" — Keep a showrunner's trust above 80 for 3 consecutive projects.
  - "Prestige Network" — Reach Prestige axis score of 80+.
  - "Mass Market" — Reach Populist axis score of 80+ (Prestige below 30).
  - "Risk-Taker" — Reach Risk-Taking axis score of 80+.
  - "The Strike Survivor" — Complete Season 6 (Writers' Strike) without going into budget crisis.
  - "8 Seasons" — Complete the full campaign.
  - "Legacy: Prestige Boutique" — End with Prestige persona.
  - "Legacy: Mass-Market Juggernaut" — End with Populist persona.
  - "The Perfectionist" — Complete a season with 4 greenlit series all scoring 70+ quality.
  - "Budget Hawk" — Complete a season with zero budget overruns.
  - Achievement icons designed (64x64, simple, readable at small size).
  - Achievements implemented in-game (trigger events on EventBus).
  - Achievements tested on Steam backend (use Steamworks test account).

- [ ] **Trading Cards** (optional, requires 5 card designs + badges + emoticons):
  - Defer to post-launch unless marketing believes it drives wishlists. Trading cards are cosmetic fluff. Focus on core game launch first.

- [ ] **Cloud Saves** (optional, recommended for player convenience):
  - Defer to post-launch (per technical architecture doc). Launch with local saves only. Cloud saves are 2 days of work, low risk, can be patched in Week 2 post-launch if demand exists.

- [ ] **Steam Input API** (controller support):
  - Not required at launch (game is mouse/keyboard primary). If we support controllers, this is post-launch work.

- [ ] **Steam Leaderboards** (optional, not recommended for this game):
  - No competitive element. No leaderboards. The game is about personal creative expression, not high scores.

**Build Upload to Steam**

- [ ] **Week -4: Upload Gold Master to Steam** via Steamworks SDK or SteamPipe GUI.
  - Depot configuration: `depot_windows` (Windows build), `depot_macos` (macOS build).
  - Upload Windows build to `depot_windows`. Verify file size (~180MB compressed).
  - Upload macOS build to `depot_macos`. Verify file size (~180MB compressed).
  - Set default branch to `default` (public launch branch).
  - Create `beta` branch for pre-launch testing (closed beta keys distributed to testers).
- [ ] Generate 50 beta keys. Distribute to trusted testers (friends, community, press under embargo).
- [ ] Beta testers play for 1 week. Collect feedback. If critical bugs found, generate Patch 1.0.1 build and re-upload to `beta` branch. Re-test. Do NOT push broken build to `default`.
- [ ] **Week -2: Move Gold Master (or patched 1.0.1) to `default` branch.** This is the build that goes live at launch.
- [ ] Set store page to "Coming Soon" with exact release date visible. Wishlist button active.

---

### 1.3 Store & Marketing Readiness (Weeks -6 to 0)

**Press & Influencer Outreach**

- [ ] **Press Kit Prepared** (hosted on itch.io presskit() or Google Drive):
  - Fact sheet (game title, genre, platform, release date, price, key features, team info)
  - Key art (header capsule, logo PNG with transparency, hero image)
  - Screenshots (all 10, high-res, no watermarks)
  - Trailer (downloadable MP4 + YouTube link)
  - Developer bios (short paragraph per team member)
  - Contact info (press email, Twitter, Discord if applicable)
- [ ] **Press List Compiled** (target: 50-100 outlets):
  - Tier 1: PC Gamer, Rock Paper Shotgun, Eurogamer, IGN Indie, Polygon
  - Tier 2: Destructoid, Siliconera, Indie Games Plus, Escapist Magazine
  - Tier 3: YouTube influencers (SplatterCat, Wanderbots, Retromation — anyone who covers management sims)
  - Niche: TV industry press (Variety, Hollywood Reporter, Deadline — long shot but worth a try. Real showrunners tweeting about the game is free marketing.)
- [ ] **Press Embargo Set**: Review copies distributed 2 weeks before launch (Week -2). Embargo lifts 3 days before launch (Thursday before Monday launch). Outlets publish reviews over the weekend, building momentum into launch day.
- [ ] Press keys generated (100 Steam keys reserved for press/influencers).
- [ ] Outreach emails sent. Template:
  - Subject: "PILOT — TV Development Sim Launching [Date]"
  - Body: Elevator pitch, key features, "You're the exec who decides what America watches," link to press kit, review key offer, embargo date, contact info.
  - Personalize each email (no mass BCC — journalists hate that).
- [ ] Track responses. Follow up 1 week before embargo lift if no response.

**Community Building**

- [ ] **Steam Community Hub Active**:
  - Discussions enabled. Pin a "Welcome" post with game overview, links to Discord/Twitter, FAQ.
  - Announcements enabled. First announcement: "Wishlist Now, Launch Date Announced."
- [ ] **Discord Server** (optional but recommended):
  - If team has bandwidth, launch a Discord 4 weeks before release. Channels: #announcements, #general, #feedback, #bug-reports.
  - Seed with beta testers. Let them build community pre-launch.
  - Defer if team is solo/small. Discord moderation is time-intensive.
- [ ] **Twitter/Social Media**:
  - Weekly updates leading to launch: screenshots, dev diary snippets, GIFs of key mechanics (the desk, a dilemma choice, the upfronts).
  - Hashtags: #PILOT, #indiegame, #gamedev, #managementsim, #PrestigeTV.
  - Engage with TV writers, showrunners, critics. Tag them in posts. "Hey [showrunner], we made a game about your job." If one showrunner with a following retweets, reach explodes.
- [ ] **Reddit**:
  - Post announcement to /r/IndieGaming, /r/pcgaming, /r/Games (follow subreddit rules — some require mod approval for self-promo).
  - Post to /r/television (high risk, high reward — they might love it or ignore it. Worth a shot.).
  - AMA (Ask Me Anything) on /r/Games or /r/IndieGaming 1 week before launch. "I made a management sim about TV development. AMA."

**Steam Visibility Events**

- [ ] **Wishlist Campaign**: Start 8 weeks before launch. Goal: 5,000+ wishlists by launch day. Wishlists drive Steam algorithm visibility on launch day.
  - Post announcement trailer.
  - Weekly updates on dev progress (build hype without overpromising).
  - Run small paid ads if budget allows (Reddit ads targeting /r/gaming, /r/indiegaming, /r/television — budget $200-$500).
- [ ] **Steam Next Fest Participation** (if timing aligns):
  - Next Fest happens 3 times per year (February, June, October). If launch is near a Next Fest window, submit a demo (single development season, 20-30 minute playtime).
  - Next Fest drives massive wishlist spikes. Worth delaying launch 1 month to hit a Next Fest window if close.
  - Demo must be polished. A broken demo kills wishlists.
- [ ] **Launch Visibility Round**: Steam gives every game a visibility boost on launch day. Maximize it:
  - Launch on a Monday or Tuesday (avoid Friday — weekend launches get buried by AAA releases).
  - No major AAA launches the same week (check Steam release calendar, avoid launching same day as Call of Duty or Elden Ring DLC).
  - Post launch announcement on all channels simultaneously (Steam, Twitter, Reddit, Discord).

---

### 1.4 Age Ratings & Regional Compliance (Weeks -8 to -4)

**ESRB (North America)**

- [ ] Submit game for ESRB rating via IARC (International Age Rating Coalition) — free, automated process via Steam.
- [ ] Fill out IARC questionnaire:
  - Violence: None
  - Sexual content: None
  - Language: Mild (occasional use of words like "hell," "damn" in dialogue — check authored content for profanity)
  - Controlled substances: None
  - Gambling: None
  - User-generated content: None
  - Location sharing: None
  - Unrestricted internet access: None
- [ ] Expected rating: **E10+ (Everyone 10+)** or **T (Teen)**.
  - E10+ if no profanity, no adult themes. T if there is workplace tension, mild language, or thematic elements around creative conflict/corporate pressure.
- [ ] IARC auto-generates ESRB rating. No manual review required unless flagged.
- [ ] Display ESRB rating on Steam store page, marketing materials, and in-game legal screen.

**PEGI (Europe)**

- [ ] IARC also generates PEGI rating simultaneously.
- [ ] Expected rating: **PEGI 12** (mild thematic elements, no violence, no explicit content).
- [ ] Display PEGI rating on Steam store page (required for EU sales).

**USK (Germany)**

- [ ] IARC generates USK rating.
- [ ] Expected rating: **USK 6** or **USK 12**.
- [ ] No special compliance needed (game has no banned symbols, no Nazi imagery, no extreme violence).

**ACB (Australia)**

- [ ] IARC generates ACB rating.
- [ ] Expected rating: **G (General)** or **PG (Parental Guidance)**.
- [ ] If IARC auto-assigns higher rating (M or MA15+), review authored content for unexpected flags (profanity, adult themes). Sanitize if necessary to avoid RC (Refused Classification) — though this game has zero risk of RC.

**Other Regions**

- [ ] Steam handles regional ratings for most other markets via IARC.
- [ ] **China**: Not targeting China at launch (requires separate publisher, government approval, content censorship). Defer to post-launch if demand exists.
- [ ] **South Korea**: IARC covers GRAC rating. Expected: **All Ages** or **12+**.

**Regional Pricing**

- [ ] Use Steam's recommended regional pricing tool (auto-converts USD to local currencies based on purchasing power parity).
- [ ] Manually review pricing in key markets:
  - US: $19.99 USD
  - EU: €18.99 EUR (verify not auto-rounded to €20.49 — adjust manually if needed)
  - UK: £16.99 GBP
  - Canada: $24.99 CAD
  - Australia: $28.99 AUD
  - Japan: ¥2,200 JPY
  - Russia: 799 RUB (verify not sanctioned by Valve — adjust if geopolitical situation changes)
  - Brazil: R$ 37,99 BRL
  - India: ₹499 INR (critical — India is price-sensitive, set low to maximize sales)
- [ ] Avoid pricing at psychological barriers (e.g., $20.00 feels expensive vs. $19.99).

**Legal Compliance**

- [ ] **Privacy Policy**: Not required (game has no analytics, no telemetry, no data collection). If post-launch we add analytics, add privacy policy link to store page and in-game.
- [ ] **EULA**: Optional. Steam's default Subscriber Agreement covers most cases. If we have custom EULA (e.g., modding restrictions, anti-cheat), display it at first launch. Defer to post-launch unless legal counsel advises otherwise.
- [ ] **Credits Screen**: Legal requirement in some jurisdictions to credit middleware (Unity, DOTween, Newtonsoft JSON, Ink). Add credits screen accessible from main menu. Include:
  - Team names and roles
  - Middleware licenses (Unity, DOTween, JSON.NET, Ink — all permissive licenses, no legal risk)
  - Font licenses (if using licensed fonts)
  - Music composer credit (if external contractor)
  - Playtester credits (optional but nice)
  - Special thanks

---

### 1.5 Post-Launch Monitoring & Support (Weeks 0 to +4)

**Launch Day Monitoring**

- [ ] **Launch Day Timeline** (see Section 5 for hour-by-hour breakdown).
- [ ] Monitor Steam reviews every 2 hours. Respond to critical bugs flagged in reviews within 4 hours.
- [ ] Monitor Twitter mentions, Reddit threads, Discord (if active). Look for common pain points.
- [ ] Track crash reports (if using Unity Analytics or Sentry.io — optional, not required at launch). If crash rate > 1%, investigate immediately.

**Hotfix Readiness**

- [ ] **Hotfix Build Pipeline Tested** (see Section 4). Can we build, test, and deploy a patch in under 4 hours? Dry-run this process Week -2.
- [ ] Critical bug triage process defined:
  - P0 (Progression blocker, save corruption, crash on launch): Hotfix within 24 hours.
  - P1 (Major bug, game playable but degraded): Patch within 1 week.
  - P2 (Minor bug, cosmetic, balance issue): Patch within 2-4 weeks or defer to larger update.
- [ ] Rollback plan: If hotfix introduces new critical bug, revert to previous build on Steam (see Section 4.3).

**Community Management**

- [ ] Assign one team member as "Community Manager" (even if solo dev, this is YOU). Responsibilities:
  - Respond to Steam forum threads (critical bugs, common questions).
  - Aggregate bug reports into tracker (Trello, Notion, GitHub Issues).
  - Post weekly dev update for first 4 weeks post-launch ("We're aware of X bug, patch coming Y date").
  - Thank players for positive reviews. Engage with constructive criticism.
- [ ] **First Week Post-Launch**: Post a "Thank You" announcement on Steam. "PILOT launched 1 week ago. Thank you to everyone who played. Here's what we're working on: [list top 3 bugs being fixed, ETA for Patch 1.1]."

**Metrics Tracking**

- [ ] Sales tracking (Steam partner dashboard updates daily). Track:
  - Units sold (day 1, week 1, month 1)
  - Revenue (after Steam's 30% cut)
  - Refund rate (target < 5% — if > 10%, something is fundamentally broken)
  - Wishlist conversion rate (wishlists at launch vs. sales in week 1 — healthy conversion is 20-30%)
- [ ] Review score tracking (Steam recent/all-time). Target: "Very Positive" (80%+ positive reviews). If score drops below 70%, investigate common complaints.
- [ ] Player retention (if we add optional telemetry post-launch): How many players complete Season 1? Season 4? Season 8? If < 50% finish Season 1, pacing is broken.

**Patch Cadence**

- [ ] **Patch 1.1** (Week +1 post-launch): Critical bug fixes only. No new features. Small download size (<10MB).
- [ ] **Patch 1.2** (Week +2-3 post-launch): Balance adjustments, QOL improvements (based on player feedback — faster text skip, better tooltips, UI tweaks).
- [ ] **Patch 1.3** (Month +2 post-launch): Larger balance pass, content fixes (if specific dilemmas are broken or exploitable).
- [ ] **Post-Launch Roadmap** (Month +3 onward): Announce post-launch content plans (if game sells well). Possible DLC: "The Streaming Wars" expansion (Seasons 9-12, 2011-2015 era). Cloud saves, controller support, additional QOL features.

---

## 2. BUILD PIPELINE DOCUMENTATION

### 2.1 Build Tools & Environment

**Build Machine Specs**

- OS: Windows 10/11 Pro or macOS Monterey/Ventura
- Unity 2022 LTS installed (exact version locked: `2022.3.X` — never upgrade mid-release)
- Steamworks SDK installed (latest stable, downloaded from Steamworks partner site)
- Git + LFS installed
- Build scripts repository cloned

**Build Script (Automated)**

```bash
#!/bin/bash
# build.sh — Automated build script for PILOT

set -e  # Exit on error

# Configuration
UNITY_PATH="/Applications/Unity/Hub/Editor/2022.3.X/Unity.app/Contents/MacOS/Unity"
PROJECT_PATH="/Users/dev/PILOT"
BUILD_PATH="/Users/dev/PILOT/Builds"
VERSION="1.0.0"

echo "Building PILOT v${VERSION}..."

# Clean previous builds
rm -rf ${BUILD_PATH}/*

# Build Windows x64
echo "Building Windows x64..."
${UNITY_PATH} -quit -batchmode -projectPath ${PROJECT_PATH} \
  -buildTarget Win64 \
  -buildPath ${BUILD_PATH}/Windows/PILOT.exe \
  -logFile ${BUILD_PATH}/build_win.log

# Build macOS Universal
echo "Building macOS Universal..."
${UNITY_PATH} -quit -batchmode -projectPath ${PROJECT_PATH} \
  -buildTarget OSXUniversal \
  -buildPath ${BUILD_PATH}/macOS/PILOT.app \
  -logFile ${BUILD_PATH}/build_mac.log

# Verify builds exist
if [ ! -f "${BUILD_PATH}/Windows/PILOT.exe" ]; then
  echo "ERROR: Windows build failed!"
  exit 1
fi

if [ ! -d "${BUILD_PATH}/macOS/PILOT.app" ]; then
  echo "ERROR: macOS build failed!"
  exit 1
fi

# Generate SHA256 hashes
echo "Generating build hashes..."
shasum -a 256 ${BUILD_PATH}/Windows/PILOT.exe > ${BUILD_PATH}/Windows/PILOT.exe.sha256
shasum -a 256 ${BUILD_PATH}/macOS/PILOT.app > ${BUILD_PATH}/macOS/PILOT.app.sha256

echo "Build complete! Builds located in ${BUILD_PATH}"
echo "Windows: ${BUILD_PATH}/Windows/PILOT.exe"
echo "macOS: ${BUILD_PATH}/macOS/PILOT.app"
```

**Manual Build Steps (if automation fails)**

1. Open Unity 2022 LTS.
2. Open project at `/Users/dev/PILOT`.
3. File > Build Settings.
4. Select Platform: PC, Mac & Linux Standalone.
5. Target Platform: Windows, Architecture: x86_64.
6. Build. Output: `Builds/Windows/PILOT.exe`.
7. Select Platform: macOS, Architecture: Universal (Intel + Apple Silicon).
8. Build. Output: `Builds/macOS/PILOT.app`.
9. Verify both builds launch on clean machines.

**Code Signing (macOS)**

- [ ] macOS builds must be code-signed with Apple Developer certificate (required for Gatekeeper, otherwise users get "unidentified developer" warning).
- [ ] Sign the .app bundle:

```bash
codesign --deep --force --verify --verbose --sign "Developer ID Application: YourName (TeamID)" Builds/macOS/PILOT.app
```

- [ ] Verify signature:

```bash
codesign --verify --deep --strict --verbose=2 Builds/macOS/PILOT.app
```

- [ ] Notarize the .app with Apple (required for macOS 10.15+):

```bash
# Create a ZIP of the .app
ditto -c -k --keepParent Builds/macOS/PILOT.app Builds/macOS/PILOT.zip

# Submit to Apple notarization service
xcrun altool --notarize-app --primary-bundle-id "com.yourcompany.pilot" \
  --username "your-apple-id@example.com" \
  --password "app-specific-password" \
  --file Builds/macOS/PILOT.zip

# Wait for email from Apple (15-60 minutes). Check status:
xcrun altool --notarization-info <RequestUUID> \
  --username "your-apple-id@example.com" \
  --password "app-specific-password"

# Staple the notarization ticket to the .app
xcrun stapler staple Builds/macOS/PILOT.app
```

- [ ] If team does not have Apple Developer account ($99/year), defer macOS release or launch without code signing (users will need to right-click > Open to bypass Gatekeeper — not ideal but functional).

**Build Versioning**

- Version number format: `MAJOR.MINOR.PATCH` (e.g., `1.0.0`, `1.0.1`, `1.1.0`).
- MAJOR = breaking changes (rarely incremented).
- MINOR = new features, content updates.
- PATCH = bug fixes, balance tweaks.
- Version number displayed in main menu, settings screen, and save file metadata.

---

### 2.2 Steam Build Upload Process

**Using SteamPipe (Command-Line)**

1. Install Steamworks SDK.
2. Navigate to `steamworks_sdk/tools/ContentBuilder/`.
3. Create app build script: `app_build_123456.vdf` (replace `123456` with your App ID).

```vdf
"AppBuild"
{
  "AppID" "123456"  // Your App ID from Steamworks
  "Desc" "PILOT v1.0.0 — Gold Master"
  "BuildOutput" "output/"
  "ContentRoot" "/Users/dev/PILOT/Builds/"
  "SetLive" "default"  // Push to 'default' branch (public launch)
  "Depots"
  {
    "123457"  // Depot ID for Windows (from Steamworks)
    {
      "FileMapping"
      {
        "LocalPath" "Windows/*"
        "DepotPath" "."
      }
    }
    "123458"  // Depot ID for macOS (from Steamworks)
    {
      "FileMapping"
      {
        "LocalPath" "macOS/*"
        "DepotPath" "."
      }
    }
  }
}
```

4. Run SteamPipe builder:

```bash
steamcmd +login <your_steam_username> +run_app_build /path/to/app_build_123456.vdf +quit
```

5. Enter Steam Guard code when prompted.
6. Wait for upload to complete (10-30 minutes depending on build size and upload speed).
7. Verify build on Steamworks partner site: Builds tab should show new build with timestamp.
8. Set build to `default` branch (public) or `beta` branch (pre-launch testing).

**Using Steam Partner Web Interface (GUI Alternative)**

1. Log in to Steamworks partner site.
2. Navigate to App Admin > Builds.
3. Upload depot files manually via web interface (slower, only use if SteamPipe fails).
4. Set branch to `default` or `beta`.

---

### 2.3 Build Verification Checklist

After uploading to Steam, verify the build before going live:

- [ ] Download build from Steam (via `beta` branch if pre-launch, `default` if post-launch).
- [ ] Install on clean Windows 10 machine. Launch. Play 15 minutes. No crashes.
- [ ] Install on clean macOS machine. Launch. Play 15 minutes. No crashes.
- [ ] Verify save/load works (start game, play 10 minutes, save, quit, relaunch, load save — save file intact).
- [ ] Verify version number displayed in main menu matches expected version (e.g., `1.0.0`).
- [ ] Verify no debug UI visible (console logs, FPS counter, dev cheats disabled).
- [ ] Verify achievements trigger correctly (if implemented).
- [ ] Verify fullscreen/windowed mode toggle works.
- [ ] Verify graphics settings save and persist across sessions.
- [ ] Verify audio settings save and persist across sessions.

If any item fails, DO NOT push to `default` branch. Fix, rebuild, re-upload, re-test.

---

## 3. PLATFORM CONFIGURATION DETAILS

### 3.1 Steamworks Configuration Checklist

**App Settings**

- [ ] App Type: Game
- [ ] Release State: Coming Soon (switch to Released on launch day)
- [ ] Visibility: Public (unlisted or hidden for closed testing, public for launch)
- [ ] Controller Support: Partial Controller Support (if we add controller input post-launch; otherwise "None")
- [ ] VR Support: None
- [ ] Languages: English (interface and audio). Add localized languages post-launch if demand exists.

**DLC & In-App Purchases**

- [ ] No DLC at launch. Defer to post-launch (Month +3 or later).
- [ ] No microtransactions. One-time purchase, full game.

**Community Features**

- [ ] Discussions: Enabled
- [ ] Screenshots: Enabled
- [ ] Workshop: Disabled (no modding support at launch — defer to post-launch if community demands it)
- [ ] Broadcasts: Enabled (players can stream via Steam Broadcasting)
- [ ] Guides: Enabled (community-generated guides welcome)

**Store Page Legal**

- [ ] Terms of Service: Default Steam Subscriber Agreement (no custom EULA at launch)
- [ ] Privacy Policy: None required (no data collection). Add if we implement analytics post-launch.
- [ ] Content Warnings: None (game has no violence, sexual content, or disturbing imagery). If ESRB/PEGI flags "Mild Themes," add descriptor: "This game contains mild thematic elements related to workplace pressure and creative conflict."

---

### 3.2 Age Rating Details

**IARC Submission (via Steam)**

1. Log in to Steamworks partner site.
2. Navigate to App Admin > Age Ratings.
3. Click "Get Rating via IARC."
4. Fill out questionnaire (5-10 minutes). Questions:
   - Does your game contain violence? **No**
   - Does your game contain blood or gore? **No**
   - Does your game contain sexual content? **No**
   - Does your game contain nudity? **No**
   - Does your game contain strong language? **No** (or **Mild** if authored content has occasional "damn" or "hell" — audit content first)
   - Does your game contain references to drugs or alcohol? **No**
   - Does your game contain gambling? **No**
   - Does your game allow users to interact with each other? **No** (single-player only)
   - Does your game share user location? **No**
   - Does your game allow unrestricted internet access? **No**
5. Submit. IARC auto-generates ratings:
   - ESRB: E10+ or T
   - PEGI: 12
   - USK: 6 or 12
   - ACB: G or PG
   - GRAC: All Ages or 12+
6. Display ratings on Steam store page (automatic once IARC completes).

**Manual ESRB Submission (if IARC flags unexpected rating)**

- If IARC assigns T (Teen) and we believe the game should be E10+, appeal via ESRB.org.
- Submit gameplay footage (30 minutes, showing all potentially flagged content).
- ESRB reviews manually (2-3 weeks, costs $0 for digital-only indie games under IARC).
- Accept final ESRB decision. Adjust marketing materials if needed.

---

### 3.3 Regional Considerations

**European Union (GDPR Compliance)**

- Game does not collect user data. No GDPR obligations at launch.
- If post-launch we add analytics (e.g., Unity Analytics, Google Analytics), add:
  - Privacy policy (hosted on website or displayed in-game)
  - Opt-in consent for analytics (required under GDPR)
  - Data deletion request process (email address for players to request data deletion)

**China**

- Not targeting China at launch (requires government approval, licensed publisher, content censorship).
- If post-launch demand exists, partner with Chinese publisher (e.g., Gamera Game, indienova). They handle compliance.

**Australia**

- No special compliance (game has zero risk of RC rating).
- Price game appropriately for Australian market (AUD pricing via Steam regional pricing tool).

**Japan**

- CERO rating not required for digital-only Steam releases.
- IARC covers GRAC (South Korea) but not CERO (Japan).
- If we pursue Japanese localization post-launch, submit to CERO (costs ~$500, takes 4-6 weeks).

---

## 4. ROLLBACK & HOTFIX PROCEDURES

### 4.1 Hotfix Pipeline (Critical Bug Response)

**Scenario**: Critical bug discovered post-launch (e.g., crash on launch for Windows 11 users, save corruption in Season 5).

**Hotfix Timeline**: 4-24 hours from bug report to live patch.

**Steps**:

1. **Triage** (0-1 hour):
   - Verify bug is reproducible (team member or trusted community member confirms).
   - Severity assessment: P0 (progression blocker, crash, save corruption) = immediate hotfix. P1 = patch within 1 week. P2 = defer to larger update.
   - If P0, proceed to Step 2. If P1/P2, add to backlog.

2. **Fix** (1-4 hours):
   - Developer identifies root cause (code review, Unity profiler, crash logs).
   - Implement fix in `release/1.0` branch (NOT `main` — keep release branch isolated).
   - Write unit test for the bug (if applicable) to prevent regression.
   - Commit fix with clear message: `HOTFIX: Fix crash on launch for Windows 11 (Issue #123)`.

3. **Build** (0.5-1 hour):
   - Increment version to `1.0.1` (patch version bump).
   - Build Windows and macOS binaries via automated script.
   - Run build verification checklist (Section 2.3) — abbreviated version for hotfix (test only the affected system).

4. **Test** (1-2 hours):
   - QA tests the specific bug fix on affected platform (Windows 11, or whatever platform was affected).
   - QA runs quick regression test (launch game, load save, play 10 minutes, verify no new issues).
   - If test passes, proceed to Step 5. If new issues found, return to Step 2.

5. **Deploy** (0.5-1 hour):
   - Upload hotfix build to Steam via SteamPipe (Section 2.2).
   - Set build to `default` branch (public).
   - Steam auto-pushes update to all players (downloads happen automatically next time they launch Steam).

6. **Announce** (0.5 hour):
   - Post announcement on Steam: "Hotfix 1.0.1 is now live. Fixed: [brief description of bug]. Thank you for your patience."
   - Post on Twitter, Discord (if active).
   - Respond to affected players' bug reports: "This is fixed in 1.0.1. Please restart Steam to download the update."

**Total Time**: 4-8 hours for critical hotfix. 12-24 hours if fix is complex or testing reveals new issues.

---

### 4.2 Patch Cadence (Non-Critical Updates)

**Patch 1.1** (Week +1 post-launch):
- Target: Critical bugs only (P0 issues found in first week).
- Example fixes: Save corruption, crashes, progression blockers.
- No balance changes. No new features.
- Download size: <10MB.

**Patch 1.2** (Week +2-3 post-launch):
- Target: Balance adjustments, QOL improvements.
- Example fixes: Adjust dilemma deltas if one strategy is too dominant. Add "Skip Text" hotkey. Improve tooltip clarity.
- Small features allowed (e.g., UI tweaks, faster animations).
- Download size: <50MB.

**Patch 1.3** (Month +2 post-launch):
- Target: Larger balance pass, content fixes.
- Example fixes: Rebalance showrunner stats if specific showrunners are never chosen. Fix authored content errors (typos in dilemmas, stat inconsistencies).
- Medium features allowed (e.g., new keyboard shortcuts, accessibility options).
- Download size: <100MB.

**Post-1.3**: Monthly or bi-monthly patches as needed. No fixed schedule. Patch when there is meaningful content to ship.

---

### 4.3 Rollback Procedure (Emergency: Hotfix Breaks Game)

**Scenario**: Hotfix 1.0.1 is deployed. Players report new critical bug introduced by the hotfix (e.g., hotfix fixes Windows 11 crash but breaks macOS launch).

**Rollback Timeline**: 1 hour from detection to rollback.

**Steps**:

1. **Detect** (0-15 minutes):
   - Monitor Steam reviews, Discord, Twitter for reports of new issues post-hotfix.
   - If multiple reports of same new critical bug, proceed to rollback.

2. **Rollback Build** (15-30 minutes):
   - Log in to Steamworks partner site.
   - Navigate to Builds tab.
   - Identify previous stable build (e.g., `1.0.0`).
   - Set previous build to `default` branch (this reverts all players to pre-hotfix version).
   - Steam auto-pushes the rollback (players download the older build next time they launch).

3. **Announce** (15-30 minutes):
   - Post announcement on Steam: "We've temporarily rolled back to version 1.0.0 due to issues with the 1.0.1 hotfix. We're working on a fix and will re-deploy as soon as possible. Apologies for the disruption."
   - Post on Twitter, Discord.
   - Acknowledge affected players' reports: "Thank you for reporting this. We've rolled back to 1.0.0 while we investigate."

4. **Fix & Re-Deploy** (2-8 hours):
   - Investigate why hotfix broke (code review, testing on affected platform).
   - Implement corrected fix.
   - Increment version to `1.0.2` (skip 1.0.1 — that version is now "cursed").
   - Build, test, deploy via normal hotfix pipeline (Section 4.1).
   - Announce: "Version 1.0.2 is now live. This resolves the issues from 1.0.1 and includes the original fix for [bug]. Thank you for your patience."

**Rollback is a nuclear option.** Only use if hotfix introduces critical bug worse than the original bug. If hotfix introduces minor bug (P1 or P2), do NOT rollback — fix forward with next patch.

---

## 5. LAUNCH DAY TIMELINE (Hour-by-Hour)

**Launch Day**: Monday, 10:00 AM PST (chosen to maximize US/EU overlap, avoid weekend burial).

**Pre-Launch (Week -1 to Day 0)**

- [ ] **Friday (Week -1, 5:00 PM PST)**: Final build (`1.0.0` or `1.0.1` if hotfix was needed during beta) set to `default` branch on Steam. Build is LIVE but store page still shows "Coming Soon." Only people with direct link can purchase (used for final testing by team/trusted community).
- [ ] **Saturday-Sunday (Week -1)**: Team tests live build. If critical bug found, hotfix immediately (this is the last chance before public launch). If no issues, proceed.
- [ ] **Sunday (Day -1, 8:00 PM PST)**: Social media pre-launch hype posts. "24 hours until launch. Wishlists convert to purchases tomorrow at 10 AM PST." Final reminder to press under embargo (reviews go live Monday morning).
- [ ] **Monday (Day 0, 12:00 AM PST)**: Embargo lifts for press. Reviews published overnight (IGN, PC Gamer, etc. post reviews between 12 AM - 8 AM). Community wakes up to reviews, builds hype into launch.

**Launch Day Timeline**

**9:00 AM PST** (1 hour before launch):
- [ ] Team online. War room open (Discord voice channel or Slack). All hands on deck (even if solo dev, you are ON for the next 12 hours).
- [ ] Final check: Steam store page live? Pricing correct? Build on `default` branch? Achievements working?
- [ ] Queue launch announcement posts (Twitter, Reddit, Steam) to go live at 10:00 AM.

**10:00 AM PST** (LAUNCH):
- [ ] Click "Release" button on Steamworks partner site. Store page goes from "Coming Soon" to "Available Now."
- [ ] Wishlists convert to purchases. Steam sends email to all wishlisters: "PILOT is now available."
- [ ] Post launch announcement on Steam: "PILOT is now live! Thank you to everyone who wishlisted. Your taste is the mechanic. Build your network. Link: [store page]."
- [ ] Post on Twitter: "PILOT is live on Steam! You decide what America watches. Greenlight shows, give notes, build a network in the golden age of TV. [store link] [trailer link] #PILOT #indiegame #PrestigeTV"
- [ ] Post on Reddit (/r/IndieGaming, /r/pcgaming, /r/Games — check subreddit rules first).
- [ ] Pin launch announcement in Discord (if active).

**10:30 AM PST** (+30 minutes):
- [ ] Monitor Steam partner dashboard. Sales ticking up? Verify purchases are processing correctly.
- [ ] Monitor Steam reviews. First reviews posted yet? If first review is negative, respond professionally: "Thank you for your feedback. We're sorry the game didn't meet your expectations. Can you share more details so we can improve?"
- [ ] Monitor Twitter mentions. Retweet positive mentions. Engage with questions.

**11:00 AM PST** (+1 hour):
- [ ] Check for critical bug reports. Any crashes reported? Any progression blockers? If yes, begin hotfix triage (Section 4.1).
- [ ] Check refund rate on Steam dashboard. If > 5% in first hour, investigate (common issue causing refunds? Bug? Misleading store page?).
- [ ] Post "thank you" tweet: "PILOT has been live for 1 hour. Thank you to everyone playing. We're monitoring feedback and will patch any issues ASAP."

**12:00 PM PST** (+2 hours):
- [ ] Lunch break for team (if critical bugs found, skip lunch — fix bugs first).
- [ ] Continue monitoring reviews, sales, bug reports.

**2:00 PM PST** (+4 hours):
- [ ] Post mid-day update on social media: "PILOT has been live for 4 hours. Seeing great feedback. Thank you! If you encounter any issues, please report them on our Steam forum or Discord."
- [ ] Aggregate common bug reports. If same bug reported 3+ times, begin hotfix process.

**5:00 PM PST** (+7 hours):
- [ ] End of US work day. Sales should be peaking (US players buying after work). Monitor sales dashboard.
- [ ] Post evening update: "Day 1 of PILOT is almost done. Thank you to everyone who played today. We're working on [list any known bugs]. Patch ETA: [date]."

**8:00 PM PST** (+10 hours):
- [ ] EU players asleep. US players still active. Monitor reviews, respond to questions.
- [ ] If no critical bugs found, team can stand down. One person on-call overnight (monitor Discord/Steam for emergencies).

**Day +1 (Tuesday Morning)**:
- [ ] Review Day 1 sales, review scores, refund rate.
- [ ] Post "Day 1 Recap" on Steam: "PILOT Day 1: [X units sold], [Y reviews, Z% positive]. Thank you! Here's what we're working on: [list top 3 bugs, ETA for fixes]."
- [ ] Continue monitoring. Respond to reviews. Triage bugs for Patch 1.1 (target: Friday, Day +5).

**Day +2 to Day +7**:
- [ ] Daily check-ins: Sales, reviews, bug reports.
- [ ] Patch 1.1 prep (if critical bugs found). Deploy Friday, Day +5.
- [ ] Post weekly dev update (Friday): "PILOT Week 1: Thank you for playing. Patch 1.1 is live [or coming Monday]. Fixes: [list]. What's next: [roadmap teaser if any]."

---

## 6. POST-LAUNCH MONITORING PLAN

### 6.1 Metrics to Track

**Sales & Revenue**

- [ ] Daily sales (units sold) — Track for first 7 days, then weekly.
- [ ] Revenue (after Steam's 30% cut) — Track daily for first week, then weekly.
- [ ] Refund rate — Target < 5%. If > 10%, investigate (broken game? misleading marketing? too niche?).
- [ ] Regional breakdown — Which countries are buying? If 80% sales from US/EU, pricing is correct. If unexpected regions dominate (e.g., 50% from Brazil), consider regional pricing adjustments.

**Steam Reviews**

- [ ] Review score (recent / all-time) — Target: "Very Positive" (80%+ positive).
- [ ] Total review count — More reviews = better Steam algorithm visibility.
- [ ] Common complaints — Track themes (e.g., "too text-heavy," "dilemmas feel repetitive," "crashes on Windows 11"). Prioritize fixes.
- [ ] Review response rate — Respond to at least 20% of negative reviews (shows players you care). Respond to ALL reviews flagging critical bugs.

**Bug Reports**

- [ ] Track all bug reports (Steam forum, Discord, Reddit, Twitter).
- [ ] Aggregate into bug tracker (Trello, Notion, GitHub Issues).
- [ ] Triage by severity (P0 / P1 / P2).
- [ ] P0 bugs = hotfix within 24 hours. P1 bugs = patch within 1 week. P2 bugs = patch within 1 month or defer.

**Player Engagement (Optional, requires telemetry)**

- [ ] If we add Unity Analytics or Sentry.io post-launch, track:
  - Session length (how long do players play per session?).
  - Retention (how many players return Day 2? Day 7? Day 30?).
  - Completion rate (how many players finish Season 1? Season 8?).
  - Feature usage (how often do players deep-read scripts? How often do they use notes system?).
- [ ] Use this data to inform post-launch patches (e.g., if 70% of players quit after Season 3, pacing is broken — rebalance Season 4 difficulty).

---

### 6.2 What to Watch For (Red Flags)

**Critical Red Flags (Act Immediately)**

- [ ] **Refund rate > 10%** in first week. Investigate: Why are players refunding? Bug? Misleading store page? Game too niche?
- [ ] **Review score < 70%** in first week. Investigate: Common complaints? Critical bug? Negative press review tanking score?
- [ ] **Crash reports from > 5% of players**. Investigate: Platform-specific bug (Windows 11? macOS Ventura?)? Unity engine issue? Deploy hotfix ASAP.
- [ ] **Sales stagnate after Day 3** (no weekend sales bump). Investigate: Marketing failure? Store page not converting? Negative word-of-mouth?

**Warning Flags (Monitor, Act if Trend Continues)**

- [ ] **Refund rate 5-10%**. Monitor. If it stays at 7-8%, acceptable for indie game. If it climbs to 10%+, investigate.
- [ ] **Review score 70-80%** ("Mostly Positive"). Acceptable but not great. Read negative reviews, identify patterns. Patch common complaints in next update.
- [ ] **Sales drop 80% after Week 1**. Normal for indie games (launch week spike, then long tail). If sales drop to zero after Week 2, marketing failed or game is too niche.

**Green Flags (You're Doing Great)**

- [ ] **Refund rate < 5%**. Players are keeping the game. Good sign.
- [ ] **Review score > 80%** ("Very Positive" or "Overwhelmingly Positive"). You nailed it.
- [ ] **Sales sustain at 10-20% of Day 1 sales for weeks 2-4**. Healthy long tail (word-of-mouth, press coverage driving steady sales).
- [ ] **Players posting screenshots of network brand profiles on Twitter/Reddit**. Organic marketing. Amplify it (retweet, share).

---

### 6.3 Community Communication Plan

**First Week Post-Launch**

- [ ] **Daily Steam Announcements** (Days 1-3): "Day 1 Recap: Thank you!" / "Day 2: Known Issues" / "Day 3: Patch 1.1 Coming Friday."
- [ ] **Day 7 Recap**: "PILOT Week 1: [X units sold], [Y% positive reviews]. Thank you! Patch 1.1 is live. What's next: [roadmap teaser]."

**Weeks 2-4 Post-Launch**

- [ ] **Weekly Dev Update** (every Friday): Brief post on Steam / Twitter. "This week: Fixed [bugs]. Next week: Working on [features]. Thank you for playing!"
- [ ] Engage with community: Respond to Steam forum threads, retweet fan art, share player stories.

**Month 2+ Post-Launch**

- [ ] **Monthly Dev Update**: "PILOT Month 2: [sales milestone if any, e.g., '10K copies sold!']. Patch 1.3 is live. Features: [list]. Roadmap: [DLC teaser if any]."
- [ ] Reduce communication cadence (monthly instead of weekly) unless major update.

**Post-Launch Roadmap Transparency**

- [ ] If game sells well (> 20K copies in first month), announce post-launch plans: "Thank you for making PILOT a success. We're working on: [Cloud saves, controller support, QOL features, potential DLC]. Stay tuned."
- [ ] If game underperforms (< 5K copies in first month), acknowledge: "Thank you to everyone who played PILOT. Sales are modest, but we're committed to supporting the game. Patch schedule: [monthly bug fixes, no DLC planned]."

Transparency builds trust. Players respect honesty more than empty promises.

---

## 7. AGE RATINGS & CONTENT COMPLIANCE DETAILS

### 7.1 IARC Questionnaire Preparation

Before submitting to IARC, audit all authored content for flaggable material:

**Language Audit**

- [ ] Search all authored text (dilemmas, events, rough cut descriptions, showrunner bios) for profanity.
- [ ] Acceptable for E10+: "hell," "damn," "crap" (mild language).
- [ ] NOT acceptable for E10+: "fuck," "shit," "bitch," "ass" (moderate to strong language — triggers T rating).
- [ ] If moderate language found, sanitize OR accept T rating. Decision: Team preference. T rating is not bad (most management sim players are 18+). E10+ is slightly broader audience.

**Thematic Elements Audit**

- [ ] Game's themes: Corporate pressure, creative conflict, workplace tension, moral ambiguity (greenlighting a flawed show vs. killing a brilliant one).
- [ ] ESRB considers these "Mild Themes." Acceptable for E10+.
- [ ] PEGI considers these "Themes suitable for 12+." Acceptable for PEGI 12.

**Violence/Gore**

- [ ] None in game. No violence, no blood, no combat.

**Sexual Content/Nudity**

- [ ] None in game. No sexual content, no nudity, no romance beyond mild workplace subtext (e.g., "add a love triangle" dilemma — but no explicit content).

**Substances**

- [ ] Audit for alcohol references (e.g., "showrunner shows up drunk to set"). If present, flag as "Alcohol Reference" (acceptable for E10+). If none, skip.

**Gambling**

- [ ] No gambling mechanics.

**User Interaction**

- [ ] Single-player only. No online interaction.

**Final IARC Answers**

- Violence: **No**
- Sexual Content: **No**
- Language: **Mild** (if "hell"/"damn" present) or **No** (if sanitized)
- Substances: **No** (or **Alcohol Reference** if present in content)
- Gambling: **No**
- User Interaction: **No**
- Sharing Location: **No**
- Unrestricted Internet: **No**

**Expected Ratings**:
- ESRB: **E10+** (if Mild Language) or **E** (if no language flags)
- PEGI: **12** (thematic elements)
- USK: **6** or **12**
- ACB: **G** or **PG**

---

### 7.2 Regional Pricing Strategy

**Pricing Philosophy**: Price for perceived value, not cost. PILOT is an 8-season, 12-15 hour campaign. Comparable games (Game Dev Tycoon: $9.99, Football Manager: $49.99). Sweet spot: **$19.99 USD**.

**Regional Price Targets** (via Steam's recommended pricing tool):

| Region | Price | Notes |
|---|---|---|
| United States | $19.99 USD | Base price. |
| European Union | €18.99 EUR | Slightly lower than 1:1 conversion (avoids €20.99 psychological barrier). |
| United Kingdom | £16.99 GBP | Avoids £19.99 barrier. |
| Canada | $24.99 CAD | Reflects CAD/USD exchange rate. |
| Australia | $28.99 AUD | Reflects AUD/USD exchange rate. |
| Japan | ¥2,200 JPY | Standard pricing for indie game in Japan. |
| Russia | 799 RUB | Adjusted for purchasing power parity. Verify sanctions status before launch. |
| Brazil | R$ 37,99 BRL | Critical — Brazil is price-sensitive. Too high = zero sales. |
| India | ₹499 INR | Critical — India is extremely price-sensitive. ₹999 would kill sales. |
| China | N/A | Not targeting China at launch. |
| South Korea | ₩22,000 KRW | Standard indie pricing. |
| Mexico | $399 MXN | Adjusted for purchasing power. |
| Argentina | $3,999 ARS | Adjusted for inflation + purchasing power (Argentina's economy is volatile — monitor exchange rate). |

**Launch Discount**: NO. Launch at full price. Running a launch discount (e.g., 10% off) trains players to wait for sales. Launch at $19.99, hold for 3 months, then first sale (20% off during Steam Summer/Winter sale).

---

## 8. RISK MITIGATION & CONTINGENCY PLANS

### 8.1 Pre-Launch Risks

**Risk: Gold Master Has Critical Bug**

- **Mitigation**: Beta testing (Week -4 to Week -2). 50 beta testers play full game. If critical bug found, hotfix before moving to `default` branch.
- **Contingency**: If critical bug found Week -1 (too late to fix before launch), delay launch by 1 week. Better to delay than launch broken.

**Risk: Store Page Rejected by Steam**

- **Mitigation**: Submit store page 8 weeks before launch. Valve reviews within 1-2 weeks. If rejected, time to fix.
- **Contingency**: If Valve flags issue (e.g., inappropriate content, misleading claims), fix immediately. If unfixable, pivot store messaging or delay.

**Risk: Code Signing Fails (macOS)**

- **Mitigation**: Test code signing + notarization Week -6. Verify signed build launches on macOS 10.15+ without Gatekeeper warning.
- **Contingency**: If notarization fails, launch without code signing. Users get Gatekeeper warning but can bypass (right-click > Open). Not ideal but game still playable. Fix post-launch.

---

### 8.2 Launch Day Risks

**Risk: Steam Servers Down**

- **Probability**: Low (Steam downtime is rare, usually Christmas Day).
- **Mitigation**: Launch on Monday (not Friday or weekend when Steam traffic peaks). Avoid launching same day as major AAA release (e.g., Call of Duty).
- **Contingency**: If Steam down at launch time, delay announcement posts by 2 hours. Wait for Steam to recover. Launch when servers stable.

**Risk: Critical Bug Discovered in First Hour**

- **Probability**: Medium (beta testing reduces this, but edge cases happen).
- **Mitigation**: War room active for 12 hours post-launch. Team ready to hotfix.
- **Contingency**: If crash-on-launch bug found, deploy hotfix within 4 hours (Section 4.1). Post announcement: "We're aware of [bug]. Hotfix deploying now. ETA: 2 hours."

**Risk: Negative Review Bomb**

- **Probability**: Low (game is not controversial, no political themes, no DRM beyond Steam).
- **Mitigation**: Quality game, honest marketing, no misleading store page. If game is good, positive reviews outnumber negative.
- **Contingency**: If review bombed (coordinated negative reviews from trolls or competitors), report to Steam (Valve can flag off-topic reviews). Respond professionally to legitimate negative reviews. Ignore troll reviews.

**Risk: Sales Flop (< 500 units Day 1)**

- **Probability**: Low if marketing done right (wishlists, press coverage, community building).
- **Mitigation**: 5,000+ wishlists before launch. Press embargo lifts Day 0 (reviews build hype). Trailer on frontpage of /r/IndieGaming.
- **Contingency**: If sales flop, double down on community engagement. AMA on Reddit. Reach out to YouTubers for coverage. Long tail is real — many indie games sell 80% of lifetime units after Week 1.

---

### 8.3 Post-Launch Risks

**Risk: Hotfix Introduces New Bug**

- **Mitigation**: Test hotfix on clean machines before deploying. Run abbreviated regression test.
- **Contingency**: Rollback to previous build (Section 4.3). Fix forward with corrected patch.

**Risk: Players Discover Exploits (Game-Breaking Strategies)**

- **Probability**: Medium (complex simulation games often have balance exploits).
- **Mitigation**: Beta testing flags obvious exploits. Community reports post-launch.
- **Contingency**: If exploit found (e.g., "spam procedural pilots, never take risks, print money with zero effort"), patch in Week 2. Announce: "We've rebalanced [system] to prevent degenerate strategies. Save files remain compatible." Do NOT ban players for using exploits (it is our fault, not theirs). Fix the game.

**Risk: Content Runs Out (Players Report Repetitive Dilemmas)**

- **Probability**: Medium if content pool too small. Low if we hit 200 dilemmas as planned.
- **Mitigation**: Playtest tracks dilemma repetition. If testers see same dilemma twice in one 8-season run, expand pool.
- **Contingency**: If players report repetition post-launch, add 50 more dilemmas in Patch 1.3 (Month +2). Free content update builds goodwill.

---

## 9. POST-LAUNCH SUPPORT ROADMAP

### 9.1 Month 1 Post-Launch

**Focus**: Stability, bug fixes, community engagement.

**Deliverables**:
- [ ] Patch 1.1 (Week +1): Critical bug fixes.
- [ ] Patch 1.2 (Week +3): Balance adjustments, QOL improvements.
- [ ] Daily community engagement (respond to reviews, Steam forum, Discord).
- [ ] Week 1 recap post. Week 4 recap post.

**Metrics Targets**:
- Sales: 5,000+ units (break-even for small team).
- Review score: 75%+ positive ("Mostly Positive" or better).
- Refund rate: < 5%.

---

### 9.2 Month 2-3 Post-Launch

**Focus**: Balance polish, QOL features, post-launch content planning.

**Deliverables**:
- [ ] Patch 1.3 (Month +2): Larger balance pass, content fixes, new QOL features (e.g., keyboard shortcuts, accessibility options).
- [ ] Community feature requests (aggregate top 10 requests, implement 3-5 in Patch 1.3).
- [ ] Optional: Cloud saves (2 days of work, high player demand).
- [ ] Optional: Controller support (1 week of work, medium player demand).

**Metrics Targets**:
- Sales: 10,000+ units (profitable for indie team).
- Review score: 80%+ positive ("Very Positive").
- Long-tail sales sustaining at 50-100 units/week (healthy word-of-mouth).

---

### 9.3 Month 4-6 Post-Launch (DLC Planning)

**Focus**: Post-launch content expansion (if game sells well).

**Potential DLC**:

**"The Streaming Wars" Expansion** (Seasons 9-12, 2011-2015 era):
- New mechanics: Binge-release strategy (release all episodes at once vs. weekly). International markets (Netflix expands globally). Shorter seasons (10-13 episodes vs. 22). Prestige talent migration (movie stars doing TV).
- New landscape pressures: Cable cord-cutting. Peak TV glut. Original content arms race.
- New dilemmas: "Do you release the entire season at once or weekly?" "Do you pursue international co-production deals?" "Do you poach a showrunner from a rival streamer?"
- Pricing: $9.99 USD. 4 additional seasons (4-6 hours playtime).
- Dev time: 3-4 months (new content authoring, minimal systems work).

**"The Golden Age" Scenario** (Alternate Start):
- Start in 1999 instead of 2002. Play through Sopranos era, Lost era, Breaking Bad era, into streaming wars.
- New historical events: Sopranos premiere (1999), Survivor launch (2000), Lost finale (2010).
- Pricing: $4.99 USD. Alternate starting point, same 8-season structure.
- Dev time: 2 months (content authoring only, reuse all systems).

**Modding Support**:
- Expose content JSON files. Document schema. Allow players to author custom dilemmas, pilots, showrunners.
- Free update (builds community, extends game lifespan indefinitely).
- Dev time: 1 month (tooling, documentation, Steam Workshop integration).

**Decision Point**: If game sells > 20K units by Month 3, greenlight DLC. If < 10K units, focus on bug fixes and move on to next project.

---

### 9.4 Month 6-8 Post-Launch (Switch Port)

**Focus**: Platform expansion (if PC version successful).

**Switch Port Feasibility**: High (per technical architecture). Game is not GPU/CPU heavy. Unity exports to Switch with minimal platform-specific code.

**Switch Port Scope**:
- Controller input (required — no mouse on Switch). Cursor emulation OR grid-based UI redesign.
- Performance tuning (target 60fps in docked mode, 30fps acceptable in handheld).
- Text scaling (readable at 720p in handheld).
- Nintendo certification (2-4 weeks).

**Pricing**: $19.99 USD (same as PC). No "Switch tax."

**Dev time**: 1-2 months (controller input, performance tuning, certification).

**Decision Point**: If PC version sells > 50K units, greenlight Switch port. If < 50K, defer indefinitely.

---

## 10. FINAL PRE-LAUNCH CHECKLIST (Week -1)

Walk through this checklist 1 week before launch. Every item must be checked. If any item is unchecked, delay launch.

**Build Readiness**

- [ ] Gold master build approved (version `1.0.0` or `1.0.1`).
- [ ] Gold master tested on clean Windows 10, Windows 11, macOS Monterey, macOS Ventura.
- [ ] No critical bugs (P0: crashes, progression blockers, save corruption).
- [ ] Performance targets met (60fps on 2019 MacBook Pro).
- [ ] Build uploaded to Steam, set to `default` branch.
- [ ] Build hash (SHA256) recorded.

**Store Page**

- [ ] Store page live on Steam (shows "Coming Soon" with exact release date).
- [ ] All assets uploaded (capsules, screenshots, trailer).
- [ ] Store description finalized (no typos, no misleading claims).
- [ ] Pricing set ($19.99 USD, regional pricing configured).
- [ ] Age rating displayed (ESRB E10+ or T, PEGI 12).
- [ ] Release date set (Monday, 10:00 AM PST).

**Marketing**

- [ ] Press embargo set (lifts 3 days before launch).
- [ ] 50+ press outlets contacted, 20+ confirmed review coverage.
- [ ] Trailer live on YouTube (public or unlisted).
- [ ] Social media accounts active (Twitter, Discord if applicable).
- [ ] Launch announcement posts queued (ready to post at 10:00 AM PST launch day).

**Community**

- [ ] Steam discussions enabled, pinned welcome post.
- [ ] Discord server active (if applicable).
- [ ] Support email configured (for refund requests, bug reports).

**Team Readiness**

- [ ] War room scheduled (team online 9:00 AM - 9:00 PM PST on launch day).
- [ ] Hotfix pipeline tested (can deploy patch in 4 hours if critical bug found).
- [ ] Rollback procedure tested (can revert to previous build in 1 hour if needed).
- [ ] On-call schedule (who monitors overnight after launch day?).

**Legal**

- [ ] Age ratings submitted (IARC completed, ESRB/PEGI displayed).
- [ ] Credits screen complete (team, middleware, fonts, music).
- [ ] Privacy policy (N/A at launch, add if analytics implemented).

**Final Sanity Check**

- [ ] Launch the game on a clean machine. Play for 30 minutes. No crashes, no bugs, no jank.
- [ ] Load a save file. Save file loads correctly.
- [ ] Complete one full season (60 minutes). No progression blockers.
- [ ] Quit and relaunch. Game persists settings, save file intact.

If every item is checked, you are ready to launch.

If any item is unchecked, fix it before launch. There are no second chances for first impressions.

---

## 11. CLOSING NOTES

This release plan is a blueprint, not a bible. Things will go wrong. A bug will slip through testing. A press outlet will miss the embargo. Steam will have a hiccup. That is launch day. The goal is not perfection. The goal is preparation.

Every step in this plan exists because I have seen launch days go wrong. Builds that worked locally but crashed on customer machines. Store pages rejected by Valve 24 hours before launch. Hotfixes that introduced new bugs. Review bombs from coordinated trolls. Sales that flatlined after Day 3 because nobody knew the game existed.

This plan mitigates those risks. It does not eliminate them. But if you follow this checklist — if you test on clean machines, if you set up the hotfix pipeline, if you build community before launch, if you monitor reviews and respond to players — you give yourself the best chance of a smooth launch.

Launch day is not the finish line. It is the starting line. The game ships. Players buy it. Some love it, some refund it, some find bugs you never imagined. You fix the bugs. You patch the balance. You engage the community. You support the game for months, maybe years.

The work does not end at launch. The work changes. From "build the game" to "support the game." From "will it work?" to "how do we make it better?"

But first, you have to launch. And if you follow this plan, you will.

Make launch day boring. If nothing goes wrong, I did my job.

Now go ship the game.

-- SHIP
