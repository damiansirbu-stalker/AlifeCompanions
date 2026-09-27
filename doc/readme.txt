Version: 1.0.4-snapshot (xlibs 1.5.1, demonized 20250908)
Changelog: https://github.com/damiansirbu-stalker/AlifeCompanions/blob/main/doc/changelog
Health: https://damiansirbu-stalker.github.io/AlifeCompanions/health/
JitProfiler: https://damiansirbu-stalker.github.io/AlifeCompanions/jitprofiler/
Bugs: https://github.com/damiansirbu-stalker/AlifeCompanions/issues
Russian / На русском: https://github.com/damiansirbu-stalker/AlifeCompanions/blob/main/doc/readme_ru.txt

My work:
GitHub: https://github.com/orgs/damiansirbu-stalker/repositories
ModDB: https://www.moddb.com/members/damian-sirbu/addons
Nexus: https://www.nexusmods.com/profile/damiansirbu/mods

My contributions:
X-Ray Monolith: https://github.com/themrdemonized/xray-monolith

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
Modded exes: themrdemonized 20250908 or newer, or AOEngine v0.55 or newer. The full feature set needs the latest demonized build. A feature that needs a newer one stays inactive on older exes.
xlibs (https://www.moddb.com/mods/stalker-anomaly/addons/xlibs-1001)
MCM

Configuration:
All settings in MCM under AlifeCompanions. Per-companion tabs for individual control. Companions are enabled with auto-spawn by default.

Compatibility:
Depends only on xlibs. Install and uninstall mid-save work. Tested: Anomaly 1.5.3, GAMMA, EFP, Zona, Forgotten Zone.
It coexists with everything else.

How It's Built:

The code and patterns are original, built on best practices from the best STALKER modders and hands-on reverse-engineering of X-Ray.
The design stays engine-native and minimal, with event-native pub/sub over polling, work spread across frames through deferred queues and rate limiters, and per-level caches that replace world scans.
The raycasting and range math are hand-written and load-tested live, following the engine's own standards and flags.
Where scripting hits an engine limit, the fix is made in X-Ray itself, in the modded exes.
Performance is the first invariant, so every flow stays under 2ms or the build rewrites or drops it, profiled continuously with JitProfiler and hand-tested on unoptimized, single-threaded exes.
Every mod carries OpenTelemetry-style tracing and performance monitoring, spanning world events and every flow, gated by the log level so it costs nothing when off.
Every commit runs the full pipeline locally and in CI, with luacheck, a custom STALKER selene build, and a load test on engine stubs.
Rule layers then check Lua practice, engine truth, conventions, contracts, release, security, and docs.
Every rate, threshold, and toggle is exposed through MCM or LTX with nothing left hard-coded, and it writes no engine values, keeping its state within engine bounds so a save can never corrupt.
It runs on one xlibs rulebook shared across the whole mod family, the same protection, distances, faction logic, and combat reads in every mod.
It depends on no other mod, not even the author's own, and needs only X-Ray and xlibs beneath it.
See the Health and JitProfiler links up top for every test and smoke result, and the mod's real CPU and allocation cost.

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
First rule this mod out: reproduce with it off, then on. The cleanest test is this mod alone on vanilla and xlibs.
Send the traces on the Anomaly Discord, or file a defect on GitHub with the same information.
Attach xray.log, the mod log, the engine build, the modlist, and the load order.
For deep technical details and mechanisms, check the architecture docs on GitHub.

Tags: alife, companions, permadeath, no-quest-gates, recruitment, engine-native, performance, save-safe, reverse-engineering
