# Troubleshooting

Most NextUI problems come down to one of these areas:

- SD card formatting or file placement;
- missing ROMs or wrong folder tags;
- missing BIOS files;
- arcade ROM sets that do not match the emulator;
- Paks that are missing, outdated, or not built for your device;
- hidden `.userdata` settings or save states.

Start with the symptom that matches your problem.

---

## The device boots stock OS instead of NextUI

Check:

1. The SD card uses Master Boot Record (MBR), not GPT.
2. The card is FAT32 or exFAT.
3. `MinUI.zip` is on the SD-card root and is still zipped.
4. The `trimui/` folder from the release is on the SD-card root.
5. You did not copy the release folder one level too deep.
6. The SD card was safely ejected after copying files.
7. Try a different SD card if settings are not saving or files keep corrupting.

Good root layout:

```text
SDCARD_ROOT/
├── MinUI.zip
├── trimui/
├── Roms/
├── Bios/
└── Saves/
```

Bad root layout:

```text
SDCARD_ROOT/
└── NextUI-v6.10.0-base/
    ├── MinUI.zip
    └── trimui/
```

## The menu only shows Tools

NextUI only shows systems that have visible games unless empty systems are enabled.

Check:

1. `Roms/` exists at the SD-card root.
2. Your ROMs are inside system folders under `Roms/`.
3. The system folder has a valid tag in parentheses, such as `Game Boy (GB)`.
4. At least one supported ROM file is inside the folder.
5. If you intentionally want to manage empty systems, enable the setting that shows empty consoles.

Example:

```text
Roms/Game Boy (GB)/Tetris (World).gb
```

## A system folder does not appear

Check:

- The folder is inside `Roms/`.
- The folder tag matches an installed emulator Pak.
- The ROM extension is supported by that emulator.
- The emulator is installed if it is an optional/community Pak.
- You did not disable or hide the system in menu settings.

For arcade and Neo Geo, use `(FBN)` unless maintainers document another supported Pak.

## A game appears but returns to the menu

Check:

1. Does that system require a BIOS file?
2. Does the ROM match the emulator?
3. If it is arcade/Neo Geo, is it an FBNeo-compatible ROM set?
4. If it is a PortMaster game, did you add the required commercial game data?
5. If it is a community Pak, does the Pak support your device?
6. Update NextUI and update the Pak.
7. Check logs.

Logs are in hidden platform folders:

```text
SDCARD_ROOT/.userdata/<platform>/logs/
```

For emulator Paks, logs often use the emulator tag:

```text
.userdata/tg5040/logs/FBN.txt
.userdata/tg5050/logs/PS.txt
```

## Wi-Fi password keeps asking again

First check that the password is correct. A wrong Wi-Fi password should not be saved.

If the password is definitely correct but NextUI keeps forgetting it, especially together with other symptoms such as boot problems or settings not saving, suspect SD-card write problems.

Try:

- safely ejecting the card and trying again;
- checking the card for filesystem errors;
- using a simpler Wi-Fi password temporarily to rule out unusual characters;
- trying another SD card.

## Files disappeared or the computer says the card must be formatted

Stop writing to the card and make a backup if possible.

On Windows, `chkdsk` may be able to repair filesystem errors:

```bat
chkdsk X: /f /r
```

Replace `X:` with the SD-card drive letter.

!!! warning
    Filesystem repair can recover a card, but it is not a substitute for backups. If corruption repeats, replace the SD card.

## A Pak is missing from Pak Store

Paks are platform-specific. Use the platform filter in Pak Store. If a Pak is not listed for your device, it may not support your device yet.

For Smart Pro S, this is a common cause of missing or non-working Paks because older Paks may only support earlier Trimui platforms.

## A Pak launches and immediately exits

Try:

1. Update Pak Store.
2. Update the Pak.
3. Confirm the Pak supports your device.
4. Check whether the Pak requires files you must provide.
5. Check logs in `.userdata/<platform>/logs/`.
6. Remove stale Pak userdata for that Pak only, then reinstall.

## Save states crash after importing

Use in-game saves when moving between systems. Save states are emulator snapshots and often fail across different cores, different emulator versions, or different save-state formats.

If you imported a RetroArch `.state.auto` or `.state1` file and it appears but crashes, it may not be compatible with NextUI's current core.

## Before asking for help

Include this information:

```text
Device:
NextUI version:
Stock firmware version, if known:
SD card brand/size:
FAT32 or exFAT:
MBR or GPT:
Fresh install or update:
Exact path of the file:
Exact filename:
What you expected:
What happened instead:
Log file, if available:
```

For ROM problems, include the folder path and filename. For arcade problems, include the exact ZIP filename but do not share copyrighted ROM files.