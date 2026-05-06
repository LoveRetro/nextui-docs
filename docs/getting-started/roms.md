## Adding ROMs

NextUI creates a `Roms` folder at the SD Card Root containing folders for each console currently supported.

You can rename these folders as you like; however, you must keep the uppercase tag name in parentheses in order to retain the mapping to the correct emulator.

!!! example "Example: Nintendo Entertainment System (FC) can be renamed to Nintendo (FC) or NES (FC) or Famicom (FC)"

If multiple folders share the same name, eg. `Game Boy Advance (GBA)` and `Game Boy Advance (MGBA)`, they will be combined into a single menu item containing the ROMs from both folders.

A ROM selected from this combined menu item will launch using the emulator in the tag of the folder it lives in.

---

## Multiple folders for the same system

If two folders have the same visible name but different tags, NextUI shows one menu item and launches each game with the emulator implied by the folder it came from.

```text
Roms/Game Boy Advance (GBA)/
Roms/Game Boy Advance (MGBA)/
```

Both can appear as "Game Boy Advance" in the menu, but games in `(GBA)` launch with the GBA pak/core and games in `(MGBA)` launch with mGBA.

This is useful when one core is faster and another core is more compatible.

---

### Multi-disc games and m3u

To streamline launching single-disc games with multiple files, place your BIN / CUE files in a folder with the same name as the CUE file.

NextUI will automatically launch the CUE file instead of navigating into the folder when selected.

```
Tony Hawk's Pro Skater 2 (USA)/
  Tony Hawk's Pro Skater 2 (USA).bin
  Tony Hawk's Pro Skater 2 (USA).cue
```

An `.m3u` file is a plain-text playlist that lists each disc file. NextUI uses it so all discs share one memory card and one save-state slot, and so you can swap discs in-game from the NextUI menu with `left` or `right` on the D-Pad.

For multi-disc games, follow these steps.

1. Create a folder for your disc files.
2. Put all the disc files into this folder.
3. Create a `.m3u` file that matches the name of the folder created in step one.
4. Edit the `.m3u` file and add the relative path to each disc's .cue file, one file per line.

NextUI will automatically launch the `.m3u` file instead of navigating into the folder when selected.

Here are a few example layouts:

**PlayStation - Final Fantasy VII**

```text
Roms/PlayStation (PS)/Final Fantasy VII (USA)/
  Final Fantasy VII (USA).m3u
  Final Fantasy VII (USA) (Disc 1).bin
  Final Fantasy VII (USA) (Disc 1).cue
  Final Fantasy VII (USA) (Disc 2).bin
  Final Fantasy VII (USA) (Disc 2).cue
  Final Fantasy VII (USA) (Disc 3).bin
  Final Fantasy VII (USA) (Disc 3).cue
```

`Final Fantasy VII (USA).m3u`

```text
Final Fantasy VII (USA) (Disc 1).cue
Final Fantasy VII (USA) (Disc 2).cue
Final Fantasy VII (USA) (Disc 3).cue
```

**Sega CD - Example 2-disc game**

```text
Roms/Sega CD (SEGACD)/Example Sega CD Game (USA)/
  Example Sega CD Game (USA).m3u
  Example Sega CD Game (USA) (Disc 1).bin
  Example Sega CD Game (USA) (Disc 1).cue
  Example Sega CD Game (USA) (Disc 2).bin
  Example Sega CD Game (USA) (Disc 2).cue
```

`Example Sega CD Game (USA).m3u`

```text
Example Sega CD Game (USA) (Disc 1).cue
Example Sega CD Game (USA) (Disc 2).cue
```

NextUI also supports `.chd` files and `.pbp` files under 2GB.

!!! info "Multi-disc games share the same memory card and save state slots across all discs when launched through the same `.m3u`."

---

### Collections

A collection is just a text file containing an ordered list of full paths to rom, cue, or m3u files. These text files live in the "Collections" folder at the root of your SD card, eg. `SDCARD_ROOT/Collections/Metroid series.txt` might look like this:

```
/Roms/GBA/Metroid Zero Mission.gba
/Roms/GB/Metroid II.gb
/Roms/SNES (SFC)/Super Metroid.sfc
/Roms/GBA/Metroid Fusion.gba
```

If you disable all visible folders under 'Roms', the 'Collections' folders contents will populate the main menu instead of being nested in the 'Collections' folder in the UI.

---

### Display names with `map.txt`

Some cores (especially arcade) require ROMs to use arcane filenames. NextUI lets you override the **display name** shown in the menu without renaming the file on disk by adding a `map.txt` file.

#### Format

`map.txt` is a plain-text file. Each line is one mapping:

```
filename.ext<TAB>Display Name
```

- The two columns are separated by a single tab character (not spaces).
- Empty lines are ignored.
- A display name beginning with `.` hides the entry from the menu (useful for BIOS files such as `neogeo.zip`).
- The mapping changes only what the menu shows; the file on disk keeps its original filename, which is what the emulator actually loads.

Example contents of a `map.txt` placed inside an arcade ROM folder:

```
neogeo.zip	.Neo Geo Bios
mslug.zip	Metal Slug
sf2.zip	Street Fighter II
```

#### Where `map.txt` is read from

NextUI looks for `map.txt` in three different locations, depending on what you want to rename:

| Location | What it renames |
|---|---|
| `Roms/<System Folder>/map.txt` | Individual ROM files inside that system folder. |
| `Collections/map.txt` | The collection text files listed in the Collections menu. |
| `Roms/map.txt` | The top-level system folders themselves (the entries that show up on the home screen). |

The `Roms/<System Folder>/map.txt` form is the most common. The Collections form is needed if you want to rename or hide entries shown in the Collections list. The `Roms/map.txt` form lets you customize the names of the system entries on the main menu without renaming the underlying folders (which would break the emulator tag mapping).

#### Example: hide Neo Geo BIOS from the arcade menu

```text
Roms/Arcade (FBN)/
├── map.txt
├── neogeo.zip
├── mslug.zip
└── sf2.zip
```

`Roms/Arcade (FBN)/map.txt`:

```
neogeo.zip	.Neo Geo Bios
mslug.zip	Metal Slug
sf2.zip	Street Fighter II
```

#### Example: customize the home-screen system names

```
Game Boy Advance (GBA)	GBA
Super Nintendo Entertainment System (SFC)	SNES
Sony PlayStation (PS)	PlayStation
```

Place this file at `Roms/map.txt`. The folders on disk keep their `(GBA)`, `(SFC)`, and `(PS)` tags, so the emulator mapping is preserved.

---

## Arcade and FBNeo

Arcade emulation requires ROM ZIPs with exact filenames and matching internal files from the correct ROM set.

For FBNeo:

* Use a folder ending in `(FBN)`, such as `Roms/Arcade (FBN)/` or `Roms/Neo Geo (FBN)/`.
* Keep arcade ZIP filenames unchanged, such as `mslug.zip`.
* Do not rename ZIPs for readability; use `map.txt` for display names.
* Use ROMs from a set that matches the FBNeo version included with NextUI.
* If FBNeo reports an unknown or wrong ROM set, the folder may be correct but the ROM set may not match.

Example layout:

```text
Roms/Arcade (FBN)/
├── map.txt
├── neogeo.zip
├── mslug.zip
└── sf2.zip
```

Neo Geo games should also use FBNeo on NextUI. You can place them in their own folder:

```text
Roms/Neo Geo (FBN)/
├── map.txt
├── neogeo.zip
├── mslug.zip
└── kof98.zip
```

Or combine them with other arcade games in `Roms/Arcade (FBN)/`.

`neogeo.zip` is required for many Neo Geo games and should be kept in the same folder as the Neo Geo game ZIPs. Use `map.txt` to hide `neogeo.zip` from the menu if needed. Prefer `Neo Geo (FBN)` over `Neo Geo (NEOGEO)`, since current NextUI uses FBNeo and does not include a `NEOGEO.pak`.

Some arcade games require sample ZIPs for sound effects. Place samples here:

```text
Bios/FBN/fbneo/samples/dkong.zip
```

## Games not showing

If a system folder does not show up:

1. Confirm the game is inside `Roms/`.
2. Confirm the parent folder has a recognized uppercase tag in parentheses, such as `Game Boy Advance (GBA)` or `Arcade (FBN)`.
3. If you renamed a folder, keep the tag. `NES (FC)` works; `NES` alone does not.
4. If all ROM folders are hidden/disabled, only Collections may show.
5. If only Tools appears, add ROMs under a tagged folder.

---

## Games not launching

If a game appears but returns to the menu or errors:

1. Check the folder tag.
2. Check the ROM extension is supported by that emulator/core.
3. Check whether required BIOS files are present and case-sensitive.
4. For arcade/Neo Geo, confirm the ZIP belongs to the expected FBNeo romset and has not been renamed.
5. Check logs under `.userdata/<platform>/logs/`.

Examples:

```text
.userdata/tg5040/logs/SFC.txt
.userdata/tg5050/logs/PS.txt
```

The exact filename usually matches the folder tag, such as `FC.txt`, `GBA.txt`, `MGBA.txt`, `FBN.txt`, or `PS.txt`.

6. If the game is launched by a community Pak, update that Pak and check its docs/known issues.

---

### Doom PWADs

!!! warning

    The PrBoom core _requires_ the `prboom.wad` IWAD file - which is treated as a Bios file - and that file is available for download [here](https://github.com/libretro/libretro-prboom/blob/master/prboom.wad).
    It can be placed in `/Bios/PRBOOM`.

NextUI supports Doom via the [PrBoom Libretro Core](https://docs.libretro.com/library/prboom/), and loads Doom PWAD - or patch wad - files as its game format. It also uses IWADs (internal Doom WADs) as the Bios files.

!!! note

    The following documentation will use the fictional `NextUI Doom.wad` (Doom 1) and `NextUI Doom 2.wad` (`Doom 2) as the PWADs Megawads being loaded.

To setup a PWAD, place it in the `/Roms/Doom (PRBOOM)` folder on your SD Card.

```
/Roms/Doom (PRBOOM)/NextUI Doom.wad
```

PWADs all depend on a particular IWAD as the base for running the PWAD. IWADs are placed in the `/Bios/PRBOOM` folder, and a list of them is available in the [BIOS reference table](bios.md). If all your PWADs use the same IWAD - for instance, `doom1.wad` then the IWAD can be placed directly in the `/Bios/PRBOOM` folder, and PrBoom will load the PWADs as expected.

```
/Bios/PRBOOM/doom1.wad
```

!!! note

    All IWADs must be named using lowercase characters, including for the file extension.

In many cases, you will want to load specific PWADs with specific IWADs. Due to how PrBoom detects IWADs and lacking information about which IWAD is required by a PWAD, PrBoom may load the incorrect IWAD for your PWAD. To combat this, NextUI supports using a `doom.version` file to specify the correct `/Bios/PRBOOM` subdirectory to reference. Omitting a `doom.version` text file will result in the default PrBoom using the default IWAD detection algorithm. It is recommended to use a `doom.version` text file in conjunction with the `m3u` text file format commonly used for [Multi-disc games and m3u](#multi-disc-games-and-m3u) to tie PWADs to have a clean directory structure.

Using `NextUI Doom.wad` as an example, we would have the following directory structure in our Roms folder:

```
/Roms/Doom (PRBOOM)/NextUI Doom/NextUI Doom.wad
/Roms/Doom (PRBOOM)/NextUI Doom/NextUI Doom.m3u
/Roms/Doom (PRBOOM)/NextUI Doom/doom.version
```

The contents of the newly created `NextUI Doom.m3u` text would contain:

```
NextUI Doom.wad
```

While the newly created `doom.version` text file would contain the following:

```
doom1
```

The `doom.version` text file maps to a subfolder in the `/Bios/PRBOOM` folder that should be used to load dependencies, such as the IWAD or custom mp3 files. In the case of Doom 1 (Commercial), the commercial IWAD would be placed on the disk like so:

```
/Bios/PRBOOM/doom1/doom1.wad
```

Music for particular IWADs can also be customized by placing the [correctly named files](https://docs.libretro.com/library/prboom/#music) into the correct `/Bios/PRBOOM` subdirectory:

```
/Bios/PRBOOM/doom1/intro.mp3
/Bios/PRBOOM/doom1/e1m1.mp3
```

To load our `NextUI Doom 2.wad` megawad with only the title music changing, the following would be a sample file structure:

```
/Roms/Doom (PRBOOM)/NextUI Doom/NextUI Doom 2.wad
/Roms/Doom (PRBOOM)/NextUI Doom/NextUI Doom 2.m3u
/Roms/Doom (PRBOOM)/NextUI Doom/doom.version
/Bios/PRBOOM/doom2/doom1.wad
/Bios/PRBOOM/doom2/dm2ttl.mp3
```

The contents of `NextUI Doom 2.m3u` text file would be:

```
NextUI Doom 2.wad
```

And the `doom.version` text file would have the following as its contents:

```
doom2
```
