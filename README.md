# Stratagem Extra Pairs v1.1.1

**STAY IN YOUR SHIP UNTIL THE MENU SAYS READY OR STATUS.txt SAYS APPLIED.**

**Scanning can take several minutes. Select your loadout only after completion.**

By Miker and ChatGPT/Codex.

Configure up to **16 Source → Extra pairs** for several loadouts. Each selected Source grants one Extra. Selecting four configured Sources can provide eight stratagems; the other pairs are available for later loadout changes. Eagle strikes are supported as extras, with their built-in Rearm links preserved.

## Optional in-game status

With Bingus Mod Options Menu enabled (included as an option in Vanilla Plus Megapack v40), open the pause menu's MODS tab and select **Stratagem Extra Pairs**. Its **Startup status** row updates within about one second while game updates run:

- Waiting: initial 15-second delay.
- Scanning: looking for all required definitions.
- Validating: checking links before applying (may pass too quickly to see).
- Ready: every configured Source link was applied and verified.
- Failed - check LOG.txt: configuration, scan, validation or application failed.
- Disabled: all pairs are None.

The row uses a choice widget because this menu has no read-only text widget. It is informational: applying a manual change resets it to the actual status and never starts a scan or edits gameplay. Below the status, each enabled INI pair has an informational row: **Pair NN: Source** on the left and **Extra** on the right. Disabled/omitted pairs are hidden; original INI slot numbers are preserved. All 16 enabled pairs plus status use 17 rows. These rows display the configuration loaded at startup, even if scanning fails; only Ready confirms application. The menu requires two choices, so both positions deliberately show the same Extra and do not change settings. No editable pair selectors, popup or sound are included.

**Mod Options Menu and the Megapack are optional.** Without them, this mod works normally; use LOG.txt/STATUS.txt. Menu API errors are isolated from scanning/application. Late-loaded menus are detected. This release uses its own scanner; HD2 Scanner is not required. Miker confirmed the status display and configured-pair rows work in game.

Replace the previous Extra Pairs package; keep only one version enabled, then Purge / Deploy. Existing INI settings are preserved. This release supports up to 16 pairs, with slots 5–16 optional. The v1.0.1 failed-search-read fix is included.

Miker reported successful in-game testing of the menu builds. Offline tests cover menu absence, late loading, API errors, displayed pairs, 16-pair application, rollback and existing scan regressions. Individual catalogue entries and every possible loadout combination are not universally verified. For problems, send LOG.txt and a screenshot of the menu.

## Alternative loadouts

Slots **1–16** are supported. Existing four-pair INIs work without edits; optional slots 5–16 can be omitted entirely. New default INIs include slots 5–16 set to None. Each provided slot needs both Source and Extra.

To test a second loadout while keeping the original four default pairs, append these lines under your existing [Links] section. If those slots already exist, edit them instead of adding duplicate keys:

```ini
Source5=OrbitalNapalmBarrage
Extra5=EagleAirstrike
Source6=Cremator
Extra6=EagleGasStrike
Source7=HMG_Emplacement
Extra7=HoverPack
Source8=LaserCannon
Extra8=MaelstromTank
```

These are example choices, not a universally tested combination. Replace them with your preferred supported names. All Sources and Extras must be distinct across the full configuration: a name cannot appear as both a Source and an Extra, or twice as an Extra.

After restarting and waiting for APPLIED, test your original loadout. Return to the ship and choose the alternative Sources for another mission **without restarting or editing the INI**. Verify their Extras appear and deploy. These links are defined per stratagem, not per faction; you can mix Sources from either loadout.

## Scan time

All enabled pairs are prepared once at startup, whether or not you select their Sources immediately. Extra pairs add signature comparisons and validation; a later required definition can extend the scan. There is still **one scan**, with an early stop once all required definitions are found. Omitted or None pairs add no definitions. The 15-second delay is unchanged.

The actual timing increase needs in-game measurement; it is not multiplied by the number of loadouts. Logs report scan and total startup time. Wait for **Ready in the menu or APPLIED in STATUS.txt**, however long scanning takes. A missing/incompatible definition in any enabled pair blocks the complete configuration; disable that pair or correct it before restarting.

## Install or update

1. Close Helldivers 2.
2. Import this ZIP into Arsenal, replacing the previous Extra Pairs version. Enable it alongside **Bingus Shared Loader v15+ / API 1**. Disable earlier link/chain tests and probes; keep only one Extra Pairs version enabled.
3. **Purge / Deploy**, then launch the game.
4. **Wait aboard your ship until Ready/APPLIED**, then select your configured Source stratagems and start a mission.

The addon starts scanning after **15 seconds**, stops once all required definitions are found, revalidates them, and applies automatically. No hotkeys are needed. STATUS.txt must say **APPLIED: CONFIGURED LINKS VERIFIED** before selecting your loadout. Loading time varies between PCs; there is no fixed completion time.

## Configure your pairs

After the first launch, close the game and open this location with Win+R:

`%LOCALAPPDATA%\CowboyBingus\Helldivers2\StratagemExtraPairs\settings.ini`

**Source** is the stratagem you select in your loadout. **Extra** is the additional stratagem it grants. Save your changes and restart the game.

Default active pairs (slots 5–16 are disabled):

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

For example, change `Extra4=FlameSentry` to `Extra4=EagleAirstrike` to have MG Sentry grant Eagle Airstrike.

**Updating preserves your existing settings.** The settings.ini inside the ZIP is a reference copy; it does not overwrite the active file. Existing comments are also preserved. Refer to the bundled file for the latest name list, or copy its catalogue comments into your active INI without replacing your pairs.

## Eagle extras

**Eagles can be Extras, never Sources.** Their existing Rearm links remain intact. The mod rejects an Eagle used as a Source before scanning or writing. Rearm itself is not configurable.

| Exact INI name | Eagle strike |
|---|---|
| EagleAirstrike | Airstrike |
| EagleStrafingRun | Strafing Run |
| EagleBomb | 500kg Bomb |
| Eagle110mmRocket | 110mm Rocket Pods |
| EagleAirstrikeNapalm | Napalm Airstrike |
| EagleClusterbombs | Cluster Bomb |
| EagleAirstrikeSmoke | Smoke Strike |
| EagleGasStrike | Gas Strike |

You can assign different Eagles to multiple Extras. Select the Sources rather than equipping those Extras separately. Miker reported successful in-game Eagle testing, including Airstrike and Napalm Airstrike alongside the other call-ins. This does not certify every possible loadout combination.

## Names and rules

The bundled INI lists **94 names**: 86 non-Eagle entries plus eight Eagle extras, including **MaelstromTank**. Some export entries may be unreleased, unused or unavailable in your game; catalogue inclusion is not proof that every entry works. Choose stratagems you own and can normally select.

- Names are case-sensitive; copy them exactly from the catalogue.
- Up to 16 pair slots. Set both Source and Extra to `None` to disable a pair. Slots 1–4 remain required for compatibility; both keys may be omitted for optional slots 5–16.
- No duplicate sources, duplicate extras, self-links or configured chains/cycles.
- Built-in Eagle-to-Rearm links are preserved and validated.
- Mission utilities, tutorial/reward variants and the previously removed incompatible entry remain excluded.
- Invalid names or malformed settings stop the attempt; they do not silently fall back to defaults.

## Status, troubleshooting and removal

Logs are in timestamped folders under:

`%LOCALAPPDATA%\CowboyBingus\Helldivers2\StratagemExtraPairs\`

Check **STATUS.txt** for progress and **LOG.txt** for details. If you see CONFIG ERROR, close the game, fix the INI and restart. For a scan refusal or unexpected gameplay behavior, send LOG.txt with your pairs and what happened.

To remove the effect, close the game, disable the addon, Purge / Deploy and restart. To recreate default settings, rename your active settings.ini before launching again; retain the old copy if you want your custom pairs.

## Technical notes

Supports up to 16 configured pairs. Scanning, validation and application cover all enabled pairs. Only the four Sources selected for a mission grant their associated Extras; other configured Sources remain available for alternative loadouts.

Scanning begins 15 seconds after addon load and stops after processing every hit in the chunk containing the final required definition. Encountered duplicates block application; remaining memory is not scanned for additional copies. Identity, package, code, original-link and source-protection checks run before writes. Each write is verified; a failure triggers guarded rollback and requires a restart. Native game threads can race these checks; multiple writes are not atomic.

Airstrike and Strafing Run also serve as validation anchors. They reuse a single definition when selected as Extras. All eight Eagle signatures match prior captured records. Offline coverage includes configuration parsing, Eagle source restrictions, preserved Rearm links, one/four Eagle extras, incorrect-link rejection, the startup timer, early stopping, existing four-pair INI preservation, optional/sparse slots, all 16 pairs, cross-slot restrictions, default pairs, write verification and rollback after a failure on the 16th write.

Only additional-stratagem links on configured Sources are edited. Cooldown values, use counts, input codes and payloads are not directly modified. No automatic retries or continuous rewriting occur after startup completes.

Catalogue: Darctor/Helldivers2_RawData, September 22, 2026 / game 1.007.100, commit `52056ecb5637bf8d71481a724b019a6bd3b0e9ea`. Runtime type numbers are resolved dynamically. Memory reader adapted from the supplied M6C addon and our earlier probes. Source/tests are under Source/stratagem-extra-pairs-v111; run tests from Source.

If you enjoy my mods and would like to support my work, consider buying me a coffee on Ko-fi! Any support is greatly appreciated, but all my mods will remain completely free. [❤️](https://cdn.jsdelivr.net/joypixels/assets/8.0/png/unicode/64/2764.png)
[https://ko-fi.com/mikerbiker](https://ko-fi.com/mikerbiker)

## Scan completion fix

Unreadable broad-search chunks no longer cause refusal by themselves when every required definition has a unique validated match. Required records and code arrays are re-read before writes. Missing or ambiguous definitions still block application. Skipped/unscanned memory is not checked for duplicate copies. Two minutes is not a completion guarantee: wait for Ready/APPLIED.
