AlifeCompanions: Custom companions for STALKER Anomaly, by Damian
Version: next (xlibs 1.5.1, demonized 20250908)
Changelog: https://github.com/damiansirbu-stalker/AlifeCompanions/blob/main/doc/changelog

My work:
GitHub: https://github.com/orgs/damiansirbu-stalker/repositories
ModDB: https://www.moddb.com/members/damian-sirbu/addons
Nexus: https://www.nexusmods.com/profile/damiansirbu/mods

My contributions:
X-Ray Monolith: https://github.com/themrdemonized/xray-monolith

No quest requirements. Just talk and recruit. Each companion has their own personality, location, and recruitment method. Permadeath keeps it real - if they die, they stay dead.

Anna is Duty. Find her at Rostok Bar. Earn 2000+ Duty goodwill or join Duty, then talk to her. She joins as a standard companion with full Anomaly companion controls.

Mila is a mercenary. Find her at Dead City. Pay 100,000 rubles. Business is business.

Both companions auto-spawn at their default locations on game load. MCM gives full control: enable/disable each companion, toggle auto-spawn, teleport them to you or yourself to them. Debug options let you reset permadeath if needed.

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
  Enable/Disable companion
  Auto-spawn at default location on game load
  Teleport companion to player
  Teleport player to companion (cross-level supported)
  Reset death status (debug)

Requirements:
Anomaly 1.5.3
Modded exes: themrdemonized 20250908 or newer, or AOEngine v0.55 or newer. The full feature set needs the latest demonized build. A feature that needs a newer one stays inactive on older exes.
xlibs (https://www.moddb.com/mods/stalker-anomaly/addons/xlibs-1001)
MCM

Install (MO2):
1. Install xlibs
2. Install AlifeCompanions
3. Load order does not matter
4. Configure via MCM

Uninstall (MO2):
Disable or remove in MO2.

Configuration:
All settings in MCM under AlifeCompanions. Per-companion tabs for individual control. Companions are enabled with auto-spawn by default.

Compatibility:
Coexists with other companion mods; it uses the standard Anomaly companion system (axr_companions).

How It's Built:

Although it started from work by Demonized, Alundaio, and Tronex, the current code and patterns are original, learned through reverse-engineering X-Ray, load testing, and custom X-Ray changes.
The design favors the engine's own mechanisms and minimal intervention, with event-native pub/sub over polling.
Work spreads across frames through deferred queues and rate limiters, while per-level caches replace world scans.
The raycasting and range math are hand-written and tested live, and the code follows the engine's own standards and flags.
Performance is the first invariant. Every flow stays under 2ms, and the build rewrites or drops anything that misses.
Profiled continuously with JitProfiler, an engine-native scientific tool. Manual tests run on unoptimized, single-threaded exes.
The code carries tracing and monitoring from the ground up, with every flow timed off the log level.
Every commit runs the full pipeline locally and in CI: luacheck, a Selene build compiled for STALKER with flags the public build lacks, and a load test that runs every script against engine stubs.
Rule layers then check crash safety, hotpath cost, engine correctness, complexity, architecture contracts, security, and the docs.
Every mod is configurable through MCM or LTX, down to each rate, threshold, and toggle, with nothing tunable left hard-coded.
The mod avoids writing engine values, holding its own state in parallel. Any value it must change stays inside the engine's own bounds, so save corruption is impossible.
It depends on no other mod, not even my own. The only shared layers are X-Ray and xlibs.

[Screenshot: AlifeCompanions under JitProfiler, a live CPU and allocation capture]
Project Health: https://damiansirbu-stalker.github.io/AlifeCompanions/

Credits:
Altogolik - support, ideas, source materials

Usage and License:
  Modpacks: allowed and encouraged. Keep the readme and license files.
  Addons, patches, integrations: allowed. Credit "AlifeCompanions by Damian Sirbu" visibly on your mod page.
  Reproducing the implementation in other software: not allowed, even with credit.
  Full license in LICENSE file and on GitHub.

Diagnostics and reporting:
General > Debug log: turn on, reproduce, then off. Writes the debug log.
Report at https://github.com/damiansirbu-stalker/AlifeCompanions/issues/new/choose or the EFP, Anomaly, and Zona Discord. Include repro steps, engine build, modlist, load order, xray.log, and the debug log.
