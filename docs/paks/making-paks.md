# Making Paks

A Pak is a folder ending in `.pak` that contains a launcher script named `launch.sh`.

Paks can be tools or emulators:

```text
Tools/<platform>/My Tool.pak/launch.sh
Emus/<platform>/MYEMU.pak/launch.sh
```

Paks are platform-specific. Use the platform folders from the current extras bundle or current release as the source of truth.

| Device | Platform | Tool Paks | Emulator Paks |
|---|---|---|---|
| Trimui Brick | `tg5040` | `Tools/tg5040/` | `Emus/tg5040/` |
| Trimui Smart Pro | `tg5040` | `Tools/tg5040/` | `Emus/tg5040/` |
| Trimui Smart Pro S | `tg5050` | `Tools/tg5050/` | `Emus/tg5050/` |

!!! warning
    Do not place community or custom Paks in `.system/`. That folder is replaced during updates.

## Emulator Pak folder tags

NextUI maps ROMs to emulator Paks using the tag in the ROM folder name.

Example:

```text
Roms/Game Boy (GB)/Dr. Mario (World).gb
```

This launches the `GB.pak` emulator Pak.

When naming an emulator Pak:

- use an uppercase tag;
- prefer common emulator/frontend abbreviations;
- avoid conflicting with existing tags;
- keep the user-facing folder name clear.

## Basic libretro Pak launcher

Draft example:

```sh
#!/bin/sh
EMU_EXE=picodrive

###############################
EMU_TAG=$(basename "$(dirname "$0")" .pak)
ROM="$1"

mkdir -p "$BIOS_PATH/$EMU_TAG"
mkdir -p "$SAVES_PATH/$EMU_TAG"
mkdir -p "$CHEATS_PATH/$EMU_TAG"

HOME="$USERDATA_PATH"
cd "$HOME"
minarch.elf "$CORES_PATH/${EMU_EXE}_libretro.so" "$ROM" &> "$LOGS_PATH/$EMU_TAG.txt"
```

If the core is bundled inside your Pak, set `CORES_PATH` to the Pak folder.

## Available environment variables

Pak launch scripts receive these environment variables:

| Variable | Description |
|---|---|
| `$PLATFORM` | Device platform, e.g. `tg5040` or `tg5050` |
| `$DEVICE` | Device identifier |
| `$SDCARD_PATH` | Path to SD card root |
| `$LOGS_PATH` | Path to log directory |
| `$EMU_TAG` | Emulator tag from folder name |
| `$ROM` | Path to the ROM file |
| `$BIOS_PATH` | Path to BIOS directory |
| `$SAVES_PATH` | Path to saves directory |
| `$CHEATS_PATH` | Path to cheats directory |
| `$CORES_PATH` | Path to libretro cores |
| `$USERDATA_PATH` | Path to user data directory |

## Logs

Write logs to:

```text
$LOGS_PATH/<TAG>.txt
```

Users will usually find those logs under:

```text
.userdata/<platform>/logs/
```

## Standalone emulator warning

Standalone emulator Paks should be a last resort because they may not integrate with NextUI's normal features.

Tell users clearly if your Pak does not support:

- resume from menu;
- quicksave and auto-resume;
- NextUI in-game menu;
- Menu or Power button behavior.

## Brightness and volume

Some standalone programs reset brightness or volume. NextUI includes `syncsettings.elf` for Pak authors who need to restore global settings around a launched binary.

Interested in making a Pak? Community member Jose Diaz-Gonzalez has put together a [fantastic guide](https://josediazgonzalez.com/2025/06/16/writing-a-pak-for-the-minui-and-nextui-launchers/).