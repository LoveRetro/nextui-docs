# Emulator Notes

This page collects common emulator-specific notes. It is not a complete compatibility list.

## Game Boy Advance: GBA vs MGBA

NextUI can expose more than one GBA core.

Use the default GBA core when you want performance. Try MGBA when a game has compatibility issues or needs behavior closer to mGBA.

Example folder layout:

```text
Roms/Game Boy Advance (GBA)/
Roms/Game Boy Advance (MGBA)/
```

If both folders share the same visible name, NextUI can combine them in the menu while still launching each game with the tag of its physical folder.

Saves are separated by tag/core, so check the matching `Saves/` and `.userdata/shared/` folders when switching cores.

## Super Nintendo: SNES9x vs Supafaust

SNES9x is the safer default for broad compatibility and RetroAchievements.

Supafaust may be useful for performance or specific behavior. Not all games or cores are eligible for RetroAchievements.

## PlayStation

PlayStation games are commonly stored as `.cue/.bin`, `.chd`, `.pbp`, or `.m3u` for multi-disc games.

Use an `.m3u` file for multi-disc games so discs share memory card and save-state slots.

BIOS file:

```text
Bios/PS/psxonpsp660.bin
```

If a game runs slowly:

- disable heavy shaders;
- check emulator options;
- test `.chd` vs `.cue/.bin` only if you suspect a bad conversion;
- check logs for missing BIOS or state restore errors.

## PC Engine / TurboGrafx-CD

PC Engine CD games require the syscard BIOS:

```text
Bios/PCE/syscard3.pce
```

## Arcade / FBNeo / Neo Geo

Arcade ROMs are set-specific. Do not rename arcade ZIPs.

Use:

```text
Roms/Arcade (FBN)/
Roms/Neo Geo (FBN)/
```

For Neo Geo through FBNeo, put `neogeo.zip` beside the game ZIPs.

Use `map.txt` for display names.

See [ROMs, BIOS, and Arcade](../getting-started/roms.md#arcade-and-fbneo) for detailed arcade and Neo Geo instructions.

## Nintendo DS

Nintendo DS support is provided by community Paks such as DraStic-based Paks, not by the base CFW.

Standalone NDS Paks may not support all NextUI integrated behavior such as normal quicksave/resume or menu shortcuts.

If NDS suddenly fails after updates, check Pak updates and stale Pak userdata.

## Dreamcast, PSP, N64, DOSBox, and ScummVM

These are generally optional/community Pak systems, not base CFW promises.

Expect compatibility and performance to vary. When asking for help, include the Pak name, device, NextUI version, and logs.

## PortMaster

See [PortMaster](../paks/portmaster.md). PortMaster compatibility depends on the port, required game data, runtimes, filesystem expectations, and device support.