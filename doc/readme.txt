Version: 1.0.4-snapshot (xlibs 1.10.1, demonized latest)
Changelog: https://github.com/damiansirbu-stalker/AlifeCompanions/blob/main/doc/changelog
Health: https://damiansirbu-stalker.github.io/AlifeCompanions/health/
JitProfiler: https://damiansirbu-stalker.github.io/AlifeCompanions/jitprofiler/
Bugs: https://github.com/damiansirbu-stalker/AlifeCompanions/issues
Russian / На русском: https://github.com/damiansirbu-stalker/AlifeCompanions/blob/main/doc/readme_ru.txt

---
Alife mods:
  AlifePlus: https://www.moddb.com/mods/stalker-anomaly/addons/alifeplus-v1-0-01
  AlifeTactics: https://www.moddb.com/mods/stalker-anomaly/addons/alifetactics
  AlifeBalance: https://www.moddb.com/mods/stalker-anomaly/addons/alifebalance
  AlifeGuard: https://www.moddb.com/mods/stalker-anomaly/addons/alifeguard-1001
Diegetic mods:
  DiegeticControl: https://www.moddb.com/mods/stalker-anomaly/addons/diegeticcontrol
  DiegeticAmbience
  DiegeticDread
Tools:
  JitProfiler: https://www.moddb.com/mods/stalker-anomaly/addons/jitprofiler
Libraries:
  xlibs: https://www.moddb.com/mods/stalker-anomaly/addons/xlibs-1001
Engines:
  X-Ray Monolith: https://github.com/themrdemonized/xray-monolith/pulls?q=is%3Apr+author%3Adamiansirbu+is%3Amerged
  OpenXRay: https://github.com/OpenXRay/xray-16/pulls?q=is%3Apr+author%3Adamiansirbu+is%3Amerged
  IX-Ray: https://github.com/ixray-team/ixray-1.6-stcop/commits/develop?author=damiansirbu
Dependents:
  COMPASS: https://github.com/Crimento/COMPASS
  Nemesis Spawn System: https://github.com/SirEndet/Nemesis-Spawn-System
  Word of Mouth: https://www.moddb.com/mods/stalker-anomaly/addons/word-of-mouth
Integrations:
  Warfare (erepb): https://www.moddb.com/mods/stalker-anomaly/addons/warfare-alife-overhaul-new
  Homestead: https://www.moddb.com/mods/stalker-anomaly/addons/homestead-stalker-settlement-builder
  Stealth Overhaul: https://github.com/Alex-leon1594/Stealth_Overhaul_Reworked
  TALKER: https://www.moddb.com/mods/stalker-anomaly/addons/talker-ai-powered-npc-dialogue-beta
  Factions of the Zone: https://github.com/devinhorowitz/factionsofthezone
  Anomaly Radios Extended: https://www.moddb.com/mods/stalker-anomaly/addons/anomaly-radios-extended-full-remaster-152
Collaborations:
  xAGNA: https://www.moddb.com/mods/stalker-anomaly/addons/xagna

My work is free and open source, ships in most modpacks, and integrates with established projects.
An organized group copies my work, defames, impersonates and review-bombs me across platforms.
You can help with a review, a rating, a proper bug report, or a coffee on Ko-fi: https://ko-fi.com/damiansirbu

No quest requirements. Talk and recruit. Each companion has their own personality, location, and recruitment method. Permadeath is real. If they die, they stay dead.

Anna is Duty. Find her at Rostok Bar. Earn 2000+ Duty goodwill or join Duty, then talk to her. She joins as a standard companion with full Anomaly companion controls.

Mila is a mercenary. Find her at Dead City. Pay 100,000 rubles. Business is business.

Both companions auto-spawn at their default locations on game load.
MCM gives full control over spawn, teleport, and permadeath reset.

Features:

Companions:
  Anna (Duty)       Rostok Bar. Requires 2000+ Duty goodwill or Duty membership.
  Mila (Mercenary)  Dead City. Costs 100,000 rubles to hire.

Recruitment:
  Dialog-based with faction goodwill or money checks
  Standard Anomaly companion system (full companion controls after recruitment)

Permadeath:
  Companions stay dead when killed
  Reset via MCM debug option

MCM (per companion):
  Enable or disable the companion
  Toggle auto-spawn at the default location on game load
  Teleport the companion to the player
  Teleport the player to the companion (cross-level supported)
  Reset the death status (debug)

Requirements:
Anomaly 1.5.3
Modded exes: themrdemonized 20250908 or newer, or AOEngine v0.5.2 or newer. The full feature set needs the latest demonized build. A feature needing a newer one is inactive or reduced on older exes.
xlibs (https://www.moddb.com/mods/stalker-anomaly/addons/xlibs-1001)
MCM

Configuration:
All settings in MCM under AlifeCompanions. Per-companion tabs for individual control. Companions are enabled with auto-spawn by default.

Compatibility:
Depends only on xlibs. Install and uninstall mid-save work. Tested: Anomaly 1.5.3, GAMMA, EFP, Zona, Forgotten Zone.
Drop:
- Duty Expansion (GhenTuong) - it defines the same stalker_duty_girl NPC section as the companion Anna, and the game stops at load on the duplicate section.
Everything else coexists, as long as it extends X-Ray and Anomaly and never overrides them.

How It's Built:

The code and patterns are original, built on best practices from the best STALKER modders and on hands-on reverse-engineering of X-Ray and the Anomaly scripts.
The design stays engine-native and minimal, with event-native pub/sub not polling, work spread across frames via deferred queues and rate limiters, and per-level caches replacing world scans.
Raycasting and range math are hand-written and load-tested live, on X-Ray's standards and flags.
Where scripting hits an engine limit, the fix is made in X-Ray itself, in the modded exes.
Performance is the first invariant. Every flow stays under 2ms or the build rewrites or drops it, profiled continuously with JitProfiler and hand-tested on unoptimized, single-threaded exes.
Each mod carries OpenTelemetry-style tracing and performance monitoring, spanning world events and every flow, gated by the log level, which skips the tracing work when it is off.
Every commit runs the full pipeline locally and in CI, with luacheck, a custom STALKER selene build, and a load test that runs every script on engine stubs.
Rule layers then check Lua practice, engine truth, conventions, contracts, release, security and docs, and a grade gate fails the build on any code or security finding.
Every rate, threshold and toggle sits in MCM or LTX with nothing hard-coded, and any engine value a mod writes stays within engine bounds, which keeps every save loadable.
It needs only X-Ray and the shared xlibs rulebook beneath it, which gives every mod in the family the same protection, distances, faction logic and combat reads.
It depends on no other mod, the author's other mods included.
See the Health and JitProfiler links up top for every test and smoke result, and for the mod's real CPU and allocation cost, measured in a live game session.

Credits:
Altogolik provided support, ideas, and source materials.

Usage and License:
  Modpacks: allowed and encouraged. Keep the readme and license files.
  Addons, patches, integrations: allowed. Credit "AlifeCompanions by Damian Sirbu" visibly on your mod page.
  Reproducing the implementation in other software: not allowed, even with credit.
  The full license is in the LICENSE file and on GitHub.

Diagnostics and reporting:
Every release goes through careful engineering and testing, but bugs can still slip through.
To report one, reproduce with debug logging on, and the world log where the mod has one.
First rule this mod out: reproduce with it off, then on.
The cleanest test is this mod alone on vanilla and xlibs.
Send the traces to my Anomaly Discord thread: https://discord.com/channels/456765861953536020/1512539453791670402
Join the server first through the Anomaly Discord invite: https://discord.gg/c4RuJNs
Or file a defect with the same information on GitHub: https://github.com/damiansirbu-stalker/AlifeCompanions/issues
Attach xray.log, the mod log, the engine build, the modlist, and the load order.
For deep technical details and mechanisms, check the architecture docs on GitHub.

Tags: alife, companions, permadeath, no-quest-gates, recruitment, engine-native, performance, save-safe, reverse-engineering
