# Frequently Asked Questions

Here are answers to common NextUI setup and support questions.

---

## Where Can I Download NextUI?

Download the latest release from the [NextUI GitHub releases page]({{ urls.github }}/releases).

Use the archive ending in `-base.zip` for normal install/update. Use the archive ending in `-all.zip` if you want the extra emulator/tool folders included.

---

## How Do I Install / Update?

For a fresh install, follow [Installation](../getting-started/installation.md).

For an existing card, follow [Updating](../getting-started/updating.md).

Important: copy `MinUI.zip` to the SD-card root as a zip file. Do not unzip `MinUI.zip`.

---

## Which devices are supported?

NextUI supports:

- Trimui Brick
- Trimui Smart Pro
- Trimui Smart Pro S
- Trimui Brick Hammer (same as Brick)

Do not install builds for experimental devices unless maintainers have published instructions for that device.

See [Device Support](../reference/device-support.md) for details.

---

## I am currently using classic MinUI, how can I migrate?

Since MinUI and NextUI share a lot of DNA, you can just install NextUI over an existing MinUI installation.

There is no need to format your existing card, just follow the [installation guide](../getting-started/installation.md) from step 4, using the `-all.zip` archive from the latest NextUI release.

!!! note "While this is a pretty straightforward process, it never hurts to have a backup of your savegames."

---

## Why Am I Only Seeing Tools?

NextUI only shows systems that have visible games unless empty systems are enabled.

Make sure you have a `Roms` folder at the SD-card root and at least one supported ROM inside a tagged system folder.

Example:

```text
Roms/Game Boy (GB)/Tetris (World).gb
```

See [Adding ROMs](../getting-started/roms.md).

---

## Can I use one SD card on more than one supported device?

Usually, but the card still needs the correct bootstrap folder from a recent release for the other device.

Back up the card, extract the latest release, and copy the release's `trimui/` folder to the SD-card root along with `MinUI.zip`.

---

## Which release file should I download?

Use the latest release archive ending in `-base.zip` for normal installation/update. Use `-all.zip` if you also want the extra emulator/tool folders included in the archive. After extracting the archive on your computer, copy `MinUI.zip` and the platform bootstrap folder, such as `trimui/`, to the SD-card root. Do not unzip `MinUI.zip`.

---

## Where do logs live?

Logs are stored in hidden `.userdata` folders:

```text
SDCARD_ROOT/.userdata/<platform>/logs/
```

Examples:

```text
.userdata/tg5040/logs/SFC.txt
.userdata/tg5050/logs/PS.txt
```

The exact `<platform>` folder depends on your device. Enable hidden files on your computer or use the Files tool/Web Dashboard to access them.

---

## Where do BIOS files go?

Most BIOS files go under:

```text
Bios/<TAG>/
```

Example:

```text
Bios/GBA/gba_bios.bin
Bios/PS/psxonpsp660.bin
Bios/PCE/syscard3.pce
```

BIOS filenames are case-sensitive. See [BIOS files](../getting-started/bios.md).

---

## Why do my arcade or Neo Geo games say "unknown romset"?

Arcade emulators require ROM ZIPs from a matching ROM set. The folder can be correct while the ROM itself is still wrong for the emulator.

For FBNeo:

- use a folder ending in `(FBN)`;
- do not rename arcade ZIPs;
- use `map.txt` for display names;
- put `neogeo.zip` beside Neo Geo game ZIPs when using FBNeo.

Example:

```text
Roms/Neo Geo (FBN)/neogeo.zip
Roms/Neo Geo (FBN)/mslug.zip
```

---

## Where do FBNeo samples go?

Sample files go under:

```text
Bios/FBN/fbneo/samples/dkong.zip
```

The path uses uppercase `Bios` matching the NextUI convention.

---

## Where are saves and save states?

In-game saves live in:

```text
Saves/<TAG>/
```

Save states and quicksaves usually live in hidden folders under:

```text
.userdata/shared/<TAG>-<core>/
```

Game Tracker data lives in:

```text
.userdata/shared/game_logs.sqlite
```

See [Saves and Migration](../getting-started/managing-saves.md).

---

## Can I sync saves with Syncthing?

Yes, but sync in-game saves first. They are safer than save states.

Recommended:

```text
Saves/
```

Be careful syncing `.userdata/`, because it contains save states, settings, recents, and tracking databases that may not be portable across devices or emulator versions.

---

## Why is a Pak missing on Smart Pro S?

Paks are platform-specific. A Pak may need explicit Smart Pro S support before it appears or works.

Use the Pak Store platform filter. If the Pak is not listed for your device, it may not be compatible yet.

---

## Why does a PortMaster game launch then return to the menu?

Common causes:

- required game data was not copied;
- the port needs runtimes or an update;
- the port does not support your device;
- the game expects filesystems or features not available on FAT32/exFAT;
- the port is broken or not yet supported by the NextUI Pak.

Update PortMaster, update the port, confirm required files, and check logs.

See [PortMaster](../paks/portmaster.md) for detailed troubleshooting.

---

## Does NextUI support RetroAchievements?

Yes. RetroAchievements support was added in NextUI v6.9.0.

Log in through Settings. RetroAchievements require Wi-Fi and a game that can be identified by hash.

Standard RetroAchievements are supported. Hardcore mode is not currently available in NextUI.

See [RetroAchievements](../reference/retroachievements.md).

---

## Where do custom shaders go?

Loose `.glsl` shader files can be placed in:

```text
Shaders/
```

Or in:

```text
Shaders/glsl/
```

NextUI v6.10.0 added support for loading shader parameter values from `.cfg` preset files. `.glsp` preset files are not supported.

See [Shaders](../shaders/index.md) for the preset layout and troubleshooting.

---

## How do I take screenshots?

Screenshots are saved to:

```text
Screenshots/<rom_name>.<YYYY-MM-DD-HH-MM-SS>.png
```

The `Screenshots/` folder is created automatically. To take a screenshot, open the in-game menu with `Menu`, navigate to Controls or Shortcuts, and map a screenshot shortcut.

---

## My Wi-Fi password keeps disappearing. What should I check?

A wrong Wi-Fi password should not be saved. If the password is correct but it keeps asking again, check whether the SD card is writable and healthy.

If Wi-Fi settings, menu settings, or boot behavior fail to persist, try another SD card.

---

## What Systems are Supported?

### Included in the Base CFW

* Game Boy (gambatte)
* Game Boy Color (gambatte)
* Game Boy Advance (gbsp, mgba)
* Nintendo Entertainment System (fceumm)
* Sega 32X (picodrive)
* Sega CD (picodrive)
* Sega Game Gear (picodrive)
* Sega Genesis (picodrive)
* Sega Master System (picodrive)
* Sega SG-1000 (picodrive)
* Sony PlayStation (pcsx_rearmed)
* Super Nintendo Entertainment System (snes9x, mednafen_supafaust)
* Super Game Boy (mgba)

### Additional emulators (extra.zip)

* Amiga (puae2021)
* Amstrad CPC (cap32)
* Arcade (CPS, MAME, etc - fbneo)
* Atari 2600 (stella2014)
* Atari 5200 (a5200)
* Atari 7800 (prosystem)
* Colecovidion (gearcoleco)
* Commodore 64 (vice_x64)
* Commodore 128 (vice_x128)
* Commodore PET (vice_xpet)
* Commodore Plus4 (vice_xplus4)
* Commodore VIC20 (vice_xvic)
* Doom (prboom)
* Microsoft MSX/MSX2 (bluemsx)
* Neo Geo Pocket/Color (race)
* Pico-8 (fake08)
* Pokémon mini (pokemini)
* TurboGrafx-16/TurboGrafx-CD (mednafen_pce_fast)
* Virtual Boy (mednafen_vb)

### Available as community paks

* DOS (dosbox)
* Nintendo 64 (mupen64plus)
* Nintendo DS (DraStic)
* ScummVM
* Sega Dreamcast (flycast)
* Sony PlayStation Portable (PPSSPP)
* Portmaster
* Wonderswan (mednafen_wonderswan)