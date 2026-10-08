INSANE! 8 Stratagems? HOW?
I found the value that adds the additional stratagem "Rearm eagle" and CHANGED IT! I linked the value "Additional_stratagem" to any other stratagem from any stratagem. So I linked the MG sentry to the Flame Sentry and dropped with 5 stratagem. I tested with a full loadout with links and they all worked...

I invite other modders to download this mod and build on it, make it better! Make a menu out of it, make a chain links of stratagems to prepare them ALL in one mission, the possibilities are insane!

OBVIOUSLY DON'T USE THIS IN A PUBLIC LOBBY! THIS IS VERY VISIBLE AND UNBALANCED!

DO NOT USE EAGLES OR SEAF SQUAD STRATAGEMS, IT MAY CRASH. Stay tuned for further updates that aims to solve these problems.

# Stratagem Extra Pairs v0.5.0 — Configurable Test

**WAIT 5 MINUTES IN YOUR SHIP WHEN STARTING THE GAME.**

**SELECT YOUR LOADOUT AFTER THE WAIT. NO HOTKEYS ARE REQUIRED.**

By Miker and ChatGPT/Codex.

## Install

Close the game. Import this ZIP in Arsenal or HD2 ModManager, enable with Bingus Shared Loader v15+ / API 1 and Purge / Deploy. No HD2Runtime or Mod Options Menu is required.

On first launch, the addon creates settings.ini with the proven four pairs and a commented catalogue. It waits 60 seconds after loading, scans the required definitions, and applies automatically if all checks pass. Wait five minutes on your ship before selecting stratagems. If STATUS.txt still says SCANNING, keep waiting. The addon cannot detect whether you are on your ship.

## Edit the active INI

`%LOCALAPPDATA%\CowboyBingus\Helldivers2\StratagemExtraPairs\settings.ini`

Open this location through Win+R. The file is created when the addon first loads. **Close the game before editing, save the file, then restart.** The file is read once per launch; edits are not applied live. Existing settings are preserved. The settings.ini bundled in this ZIP is a reference/default copy; it does not override the active file automatically.

```ini
[Links]
Source1=OrbitalPrecisionStrike
Extra1=OrbitalGasStrike
Source2=OrbitalGatlingBarrage
Extra2=OrbitalEMSStrike
Source3=OrbitalAirburstStrike
Extra3=GatlingSentry
Source4=MachineGunSentry
Extra4=FlameSentry
```

A Source is a stratagem you select in your loadout; its Extra becomes an additional call-in. The default four pairs produced eight working call-ins in previous tests. Choose the four sources after startup completes; do not equip the extras directly for verification.

## Names and rules

The INI comments list **86 enabled/selectable non-Eagle entries from the August 12, 2026 data export**, grouped into backpacks, emplacements, orbitals, support weapons, sentries and vehicles. Each includes its exact key and export description. Names are case-sensitive. Some names are developer labels rather than polished in-game names.

**This is a data catalogue, not a claim that all 86 entries are released or gameplay-tested.** It can include unused/unreleased variants. The default eight are verified; other choices require testing. Runtime identity validation confirms matching data, not ownership, public availability or full gameplay compatibility. If an entry is unavailable or incompatible, application may be refused. Future stratagems absent from this export are not included.

Eagles, Rearm, mission utilities, tutorial and reward variants cannot be configured. Eagle records are only read as internal layout checks, never offered as sources/targets or edited.

- Four pair slots, each with one Source and one Extra.
- Set both names in a pair to **None** to disable it. All four disabled means no scan or writes.
- No duplicate sources or duplicate extras.
- No self-links, chains or cycles: a name cannot be both a source and an extra in this four-pair version.
- Unknown/misspelled names, missing keys, extra keys or malformed settings stop the attempt before scanning or writing. They do not silently fall back to defaults.
- `;` and `#` begin comments. Windows CRLF line endings and a UTF-8 BOM are accepted.

## Status and reset

Logs are in timestamped subfolders of:

`%LOCALAPPDATA%\CowboyBingus\Helldivers2\StratagemExtraPairs\`

STATUS.txt shows the latest event; LOG.txt retains the full record, including the configured pairs. **APPLIED: CONFIGURED LINKS VERIFIED** means all enabled pair edits completed in memory. If it reports CONFIG ERROR, correct settings.ini and restart. For other refusals/failures, send LOG.txt. There are no automatic retries or continuous rewriting.

To remove the effect, close the game, disable the addon and redeploy, then restart. To restore default configuration, close the game and rename the active settings.ini; the next launch creates a fresh default file. Keep your renamed copy if you want to reuse it.

## Validation and limits

The working automatic startup and guarded four-byte link edits are retained. Only configured definitions plus three Eagle/Rearm layout anchors are searched, not the entire catalogue. Definitions must match known IDs, package hashes and code data. Current runtime types are resolved dynamically, so users never enter enum numbers. Nonempty existing links, ambiguous matches, incomplete scans, failed reads and unexpected record/protection changes refuse application.

Each edit and the final values are verified. A write failure triggers guarded rollback and requires a restart, even if rollback succeeds. Native game threads can race validation; multiple writes are not atomic. Cooldowns, charges, codes, payloads, executable code and page protections are not modified. The addon does not intentionally edit account progression.

The timer uses Windows monotonic uptime. Scanning runs through game updates, above 2 GiB in committed readable private/mapped memory, with a reusable 256 KiB buffer and approximate 1.5 ms per-update budget. Individual calls can exceed the budget. After the attempt, addon processing stops. The five-minute ship wait is a practical allowance, not a guaranteed deadline on every machine.

Offline tests cover INI parsing and rejected configurations, all-disabled behavior, default-file creation, preservation of an existing custom file, a custom MG -> AMR configuration, automatic startup, callback returns, exact writes and rollback failures. The configurable INI build still needs in-game verification. The earlier Eagle Rearm display observation remains unresolved; use an Eagle-free solo mission for the initial test.

Memory reader adapted from the supplied M6C addon, our Dagger experiment and Jump Pack/Stratagem probes. Source and offline tests are included under Source/stratagem-config-test. Run tests from Source. No Quad Drop or Infinite Stratagems code is included.

If you enjoy my mods and would like to support my work, consider buying me a coffee on Ko-fi! Any support is greatly appreciated, but all my mods will remain completely free. ❤️
https://ko-fi.com/mikerbiker
