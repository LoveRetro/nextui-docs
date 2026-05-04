## Managing Cheats

NextUI supports RetroArch `.cht` cheat files for compatible libretro cores.

!!! info
    Cheats are not supported by every core. A cheat file can be in the right place and still not work if the selected emulator core does not support that cheat format.

## Cheat file location

Cheat files go in:

```text
SDCARD_ROOT/Cheats/<TAG>/
```

The filename must match the ROM filename, including the ROM extension, with `.cht` added at the end.

Example:

```text
ROM:
SDCARD_ROOT/Roms/Game Boy (GB)/Super Mario Land (World).zip

Cheat file:
SDCARD_ROOT/Cheats/GB/Super Mario Land (World).zip.cht
```

The `<TAG>` is the tag in the ROM folder name. For `Game Boy (GB)`, the tag is `GB`.

## When cheats appear but do not work

Try these checks:

1. Confirm the cheat filename exactly matches the ROM filename, including `.zip`, `.gba`, `.gb`, or other extension.
2. Confirm the cheat is for the same region and revision as your ROM.
3. Try another cheat source or downloader.
4. Try another core if the system has multiple cores.
5. Remove the cheat file and test the game without cheats if launching crashes.

## Manual `.cht` example

A `.cht` file is a text file. A simple example looks like this:

```text
cheats = 1

cheat0_desc = "Example cheat"
cheat0_code = "000-000-000"
cheat0_enable = false
```

The exact code format depends on the emulator core and game. If a manually edited cheat crashes or exits the game, remove the file and test again.

For a database of cheat files, see the [libretro cheats repository](https://github.com/libretro/libretro-database/tree/master/cht).