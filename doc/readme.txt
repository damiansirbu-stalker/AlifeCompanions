AlifeCompanions: Custom companions for STALKER Anomaly, by Damian
Version: next (xlibs 1.5.1, demonized 20250908)
GitHub: https://github.com/damiansirbu-stalker/AlifeCompanions
Changelog: https://github.com/damiansirbu-stalker/AlifeCompanions/blob/main/doc/changelog

Alife Collection:
AlifeAmbience: https://github.com/damiansirbu-stalker/AlifeAmbience
AlifeBalance: https://www.moddb.com/mods/stalker-anomaly/addons/alifebalance
AlifeCompanions: https://github.com/damiansirbu-stalker/AlifeCompanions
AlifeDiegetic: https://www.moddb.com/mods/stalker-anomaly/addons/diegetic-audio-control-100
AlifeGuard: https://www.moddb.com/mods/stalker-anomaly/addons/alifeguard-1001
AlifePlus: https://www.moddb.com/mods/stalker-anomaly/addons/alifeplus-v1-0-01
AlifeSpooks: https://github.com/damiansirbu-stalker/AlifeSpooks
AlifeTactics: https://www.moddb.com/mods/stalker-anomaly/addons/alifetactics
FurnitureFuel: https://github.com/damiansirbu-stalker/FurnitureFuel
JitProfiler: https://github.com/damiansirbu-stalker/JitProfiler
TestZone: https://github.com/damiansirbu-stalker/TestZone
xlibs: https://www.moddb.com/mods/stalker-anomaly/addons/xlibs-1001

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
Modded exes: themrdemonized or AOEngine v0.55 or newer. The full feature set needs the latest demonized build; a feature that needs a newer one stays inactive on older exes.
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

Performance and Infrastructure:
Performance comes first, ahead of any feature. When a feature cannot fit the budget it is reworked, replaced, or removed with an X-Ray engine modification rather than allowed to slow the game.
Built from the X-Ray engine source by reverse engineering, with targeted engine changes of my own for performance, precision, and accuracy.
Heavy work spreads across frames, paced by rate limiters and staggered, deferred queues, with the math to keep cost bounded at any entity count.
A layered validator runs on every change, locally and in CI, and blocks the build on any crash, unsafe engine call, performance regression, style break, failed smoke load, or leaked secret.
Profiled with JitProfiler, an engine-native, scientific profiler.
Timings are worst-case, from a build with no multithreading or optimizations, so yours runs faster.
Project Health: https://damiansirbu-stalker.github.io/AlifeCompanions/
[JitProfiler: AlifeCompanions under CPU and allocation capture]

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
