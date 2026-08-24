AlifeCompanions: Custom companions for STALKER Anomaly, by Damian
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

Performance:
Performance comes first, ahead of any feature. When a feature cannot fit the budget it is reworked, replaced, or removed with an X-Ray engine modification rather than allowed to slow the game. Measured on the engine built from the latest source with no multithreading and no optimizations, so the timings are worst-case; the optimized multithreaded build you run is always faster.

Compatibility:
Requires xlibs.
Runs on themrdemonized modded exes 2025.9.10 or newer, or AOEngine v0.55 or newer.
The full feature set needs the latest demonized build. A feature that needs a newer build stays inactive on older exes.
Uses standard Anomaly companion system (axr_companions). Compatible with GAMMA and other companion mods. Does not modify base scripts.

FAQ:
Do I need modded exes?
  Yes. AlifeCompanions needs themrdemonized modded exes (2025.9.10 or newer) or AOEngine (v0.55 or newer). Vanilla Anomaly does not expose the APIs it relies on.

Credits:
Altogolik - support, ideas, source materials

Development:
Written against X-Ray Monolith engine source, Demonized exes source code, and Anomaly 1.5.3 unpacked gamedata.
Code patterns and engine usage validated against established work by reputable GAMMA modders (Demonized, Vintar0, RavenAscendant, xcvb).
The code is validated in real time by a multi-stage pipeline: luacheck, selene, tree-sitter AST analysis, contract rules, cross-file dependency resolution, cyclomatic complexity analysis, crash and vulnerability pattern detection, lua54 integration testing with X-Ray engine stubs, gitleaks secret scanning.
Full report in doc/test-report.log.

Usage and License:
  Modpacks: allowed and encouraged. Keep the readme and license files.
  Addons, patches, integrations: allowed. Credit "AlifeCompanions by Damian Sirbu" visibly on your mod page.
  Reproducing the implementation in other software: not allowed, even with credit.
  Full license in LICENSE file and on GitHub.

Reporting issues and suggestions
Open a report at https://github.com/damiansirbu-stalker/AlifeCompanions/issues/new/choose, or ask on the GAMMA, EFP, Anomaly, and Zona Discord servers. Read this readme and the MCM options first.

Include: exact repro steps (new game or named save, expected vs actual), engine build, modlist, load order, xray.log, and the mod debug log. With hundreds of mods loaded, only the log shows whether this one was involved.

The debug log is required, so set the MCM log level to DEBUG, reproduce, then set it back to WARN. DEBUG is not free: it writes a line for every event and can hitch a single-threaded exe.
