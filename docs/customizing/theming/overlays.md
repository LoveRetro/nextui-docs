## Emulator Overlays

!!! info "Overlays are only supported by libretro emulators"
    Standalone emulators installed via Paks do not support NextUI overlays.

NextUI looks for accompanying media for each emulator under the `/Overlays/[System]` folder.
The `System` corresponds to the name of the Emu Pak specified in your Emulator folder name within parenthesis.
In this folder you can add as many overlay PNGs as you want!

For example:
```
# For /Roms/Game Boy Advance (GBA)
/Overlays/GBA/overlay1.png
/Overlays/GBA/overlay2.png
/Overlays/GBA/overlay3.png
/Overlays/GBA/overlay4.png
/Overlays/GBA/overlay5.png

You do not need to follow this naming convention. You can name your overlay image files however you'd like.
```

When in game, hit the `Menu` button and navigate to `Options -> Frontend`. Scroll to the `Overlay` setting and pick from the ones you added to the corresponding system's folder.
