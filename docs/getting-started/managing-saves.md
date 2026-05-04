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

By default, NextUI uses the emulator's default save file format. RetroArch-style `.srm` save support can be enabled in Settings.

After changing this setting, existing save files may need to be renamed before NextUI sees them.

Example:

```text
Old file: Pokemon Crystal.sav
New file: Pokemon Crystal.srm
```

!!! warning
    Rename saves only after making a backup.

## Save states and quicksaves

Save states are different from in-game saves. They are emulator snapshots and are more sensitive to emulator version, core, and settings.

Save states are stored in the hidden `.userdata` folder, usually under:

```text
.userdata/shared/<TAG>-<core>/
```

Common save-state folders:

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

## Syncing saves with Syncthing or another sync tool

For syncing between devices, in-game saves are safer than save states.

Recommended:

- Sync `Saves/`.
- Use `.srm` saves if you also sync with RetroArch devices.
- Avoid syncing a game while it is running.
- Be careful with PlayStation folder names; another device may use `psx` while NextUI uses `PS`.

Use caution:

- Syncing `.userdata/shared/` can copy save states, settings, and databases that may not be compatible between devices.
- Save states can crash if they came from a different emulator, different core version, or different save-state format.
- FAT32 and exFAT do not support Unix symlinks. Some advanced sync or PortMaster workflows that expect symlinks may not work on a standard NextUI card.

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