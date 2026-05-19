# Emulator Overlays

!!! info "Overlays are only supported by libretro emulators"
    Standalone emulators installed via Paks do not support NextUI overlays.

NextUI looks for overlay images under:

```text
SDCARD_ROOT/Overlays/<TAG>/
```

The `<TAG>` matches the tag in the ROM folder name.

Example:

```text
Roms/Game Boy Advance (GBA)/Metroid Fusion.gba
Overlays/GBA/gba-grid.png
Overlays/GBA/gba-border.png
```

When in game:

1. Press `Menu`.
2. Go to `Options`.
3. Go to `Frontend`.
4. Choose an overlay.

## Overlay does not appear

Check:

- The overlay is a PNG.
- The overlay is in `Overlays/<TAG>/`.
- The game is using a libretro emulator, not a standalone emulator.
- The tag matches the ROM folder tag.
- Filename case is correct.

## Overlay cuts off the game

Overlays are designed for specific screen sizes, systems, and scaling settings. If an overlay cuts off part of the game:

1. Change Screen Scaling between Native, Aspect, and Fullscreen.
2. Try a different overlay made for your device.
3. Disable integer scaling or shader scaling experiments that conflict with the overlay.
4. Test without shaders to confirm whether the overlay or shader chain is causing the issue.

Community overlay packs may be designed for one device and look wrong on another.