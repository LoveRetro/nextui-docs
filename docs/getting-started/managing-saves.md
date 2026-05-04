## Managing Saves

NextUI uses more than one location for game data. In-game saves, save states, settings, and tracking databases are not all the same thing.

## In-game saves

Normal in-game saves live in:

```text
Saves/<TAG>/
```

The `<TAG>` matches the emulator tag in the ROM folder name.

Examples:

```text
Saves/GB/
Saves/GBC/
Saves/GBA/
Saves/MGBA/
Saves/PS/
```

These are the safest files to move between devices and emulators.

## RetroArch `.srm` support

By default, NextUI uses the MinUI save format. RetroArch-style `.srm` save support can be enabled in Settings.

Changing the save format changes the filename NextUI reads and writes. Existing saves must be renamed or copied to the configured format before NextUI sees them.

Formats:

```text
MinUI default:  Game.gba.sav
RetroArch:     Game.srm
Generic:       Game.sav
```

!!! warning
    Rename saves only after making a backup.

## Save states and quicksaves

Save states are different from in-game saves. They are emulator snapshots and are more sensitive to emulator version, core, and settings.

Save-state payloads are stored in hidden `.userdata` folders under:

```text
.userdata/shared/<TAG>-<core>/
```

Examples:

| Core | Save state dir | Config dir |
|---|---|---|
| FC (fceumm) | `.userdata/shared/FC-fceumm` | `.userdata/<platform>/FC-fceumm` |
| GB (gambatte) | `.userdata/shared/GB-gambatte` | `.userdata/<platform>/GB-gambatte` |
| GBA (gpsp) | `.userdata/shared/GBA-gpsp` | `.userdata/<platform>/GBA-gpsp` |
| GBC (gambatte) | `.userdata/shared/GBC-gambatte` | `.userdata/<platform>/GBC-gambatte` |
| MD (picodrive) | `.userdata/shared/MD-picodrive` | `.userdata/<platform>/MD-picodrive` |
| PS (pcsx_rearmed) | `.userdata/shared/PS-pcsx_rearmed` | `.userdata/<platform>/PS-pcsx_rearmed` |
| SFC (snes9x) | `.userdata/shared/SFC-snes9x` | `.userdata/<platform>/SFC-snes9x` |
| MGBA (mgba) | `.userdata/shared/MGBA-mgba` | `.userdata/<platform>/MGBA-mgba` |
| FBN (fbneo) | `.userdata/shared/FBN-fbneo` | `.userdata/<platform>/FBN-fbneo` |
| SUPA (mednafen_supafaust) | `.userdata/shared/SUPA-mednafen_supafaust` | `.userdata/<platform>/SUPA-mednafen_supafaust` |
| PCE (mednafen_pce_fast) | `.userdata/shared/PCE-mednafen_pce_fast` | `.userdata/<platform>/PCE-mednafen_pce_fast` |

Replace `<platform>` with `tg5040` for Trimui Brick / Smart Pro, or `tg5050` for Smart Pro S.

NextUI also stores launcher resume metadata and preview images under:

```text
.userdata/shared/.minui/<EMU>/
```

That `.minui` folder is not the actual save-state payload. It stores the slot marker and preview data used by the launcher and game switcher.

Quicksave and auto-resume use the same save-state system. Before sleep or power-off, integrated NextUI emulators write SRAM, RTC data, an autosave state, and an auto-resume marker. This depends on the emulator core supporting serialization. Standalone community emulator Paks can have different behavior.

## Migrating to a new SD card

To move to a new SD card:

1. Back up the old card.
2. Install NextUI on the new card following the [Installation](installation.md) instructions.
3. Copy your personal folders back.
4. Safely eject the card before putting it in the device.

Back up at least:

```text
Roms/
Bios/
Saves/
Collections/
Overlays/
Shaders/
Tools/        # if you installed custom Tool Paks
Emus/         # if you installed custom Emulator Paks
Cheats/
.userdata/    # settings, save states, recents, tracker databases
```

Also back up `.media` folders inside ROM folders if you added artwork manually.

## Fresh install while keeping saves and settings

For a fresh install, copy these folders somewhere safe first:

```text
Roms/
Bios/
Saves/
.userdata/
```

After reinstalling, copy them back.

If you are troubleshooting a corrupted setting, do not copy all of `.userdata` back immediately. Restore `Saves/` first, then restore only the specific hidden files you need.

## Game Tracker data

Game-time tracking data is stored in:

```text
.userdata/shared/game_logs.sqlite
```

To reset the Game Tracker, back up the file first, then delete or rename it.

Battery tracking data is stored in:

```text
.userdata/shared/battery_logs.sqlite
```

## Recents and launcher settings

Recent games are stored under:

```text
.userdata/shared/.minui/recent.txt
```

Settings from the Settings app are stored in:

```text
.userdata/shared/minuisettings.txt
```

If your menu settings are badly broken, deleting `minuisettings.txt` may reset Settings-app preferences.

## Sync tools

Syncthing and similar sync tools are community Paks, not part of base NextUI. See [Paks](../paks.md#save-sync-paks) for guidance before syncing saves between devices.

## Hidden files on your computer

Directories and files that start with a period are hidden by default.

Windows:

1. Open File Explorer.
2. Select View.
3. Enable hidden items.

macOS:

- Press `Command + Shift + .` in Finder to toggle hidden files.

Linux:

- Press `Ctrl + H` in many file managers, or use `ls -la` in a terminal.
