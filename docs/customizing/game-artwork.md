## Game Artwork

NextUI looks for artwork in a `.media` folder inside each ROM folder.

Example ROM:

```text
Roms/Super Nintendo (SFC)/Super Mario World.sfc
```

Matching artwork:

```text
Roms/Super Nintendo (SFC)/.media/Super Mario World.png
```

The image must be PNG. The name must match the ROM filename without the ROM extension.

## ZIP example

For a zipped ROM:

```text
Roms/Game Boy (GB)/Tetris (World).zip
```

Use:

```text
Roms/Game Boy (GB)/.media/Tetris (World).png
```

Do not name the artwork `Tetris (World).zip.png`.

## Adding artwork manually

1. Open the ROM folder.
2. Create `.media` if it does not exist.
3. Add a PNG image with the matching name.
4. Safely eject the SD card.
5. Restart or refresh the menu if needed.

## Using scrapers

Community tools such as [Artwork Scraper](https://github.com/josegonzalez/minui-artwork-scraper-pak/), the Web Dashboard, or PC tools like Skraper can help download artwork.

If a scraper creates a `media` folder or `gamelist.xml`, NextUI may not use that structure directly. Move or copy the PNG artwork into the `.media` folder expected by NextUI.

Example conversion:

```text
# Scraper output
Roms/Game Boy Advance (GBA)/media/Metroid Fusion.png
Roms/Game Boy Advance (GBA)/gamelist.xml

# NextUI artwork location
Roms/Game Boy Advance (GBA)/.media/Metroid Fusion.png
```

The `gamelist.xml` file is not required for NextUI artwork display.

## Artwork for merged folders

If you use multiple emulator folders with the same visible name, each physical ROM folder can have its own `.media` folder.

Example:

```text
Roms/Game Boy Advance (GBA)/.media/
Roms/Game Boy Advance (MGBA)/.media/
```

Put the artwork beside the ROM in the same physical folder.