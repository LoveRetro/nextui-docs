## Optional BIOS

Some emulators require or perform better with the official BIOS.

NextUI does not include copyrighted BIOS files and cannot provide download links. Use your own files from legal sources.

!!! warning "BIOS file names are case-sensitive"
    `gba_bios.bin` and `GBA_BIOS.BIN` are different filenames. Use the exact filename shown in the table.

## Where BIOS files go

Most BIOS files go under:

```text
SDCARD_ROOT/Bios/<TAG>/
```

Example:

```text
SDCARD_ROOT/Bios/GBA/gba_bios.bin
SDCARD_ROOT/Bios/PS/psxonpsp660.bin
SDCARD_ROOT/Bios/PCE/syscard3.pce
```

The `<TAG>` usually matches the emulator tag in the ROM folder name.

## Dashboard hash warnings

The Web Dashboard and support tools may compare BIOS files against known hashes. A bad hash warning means the file does not match the known reference hash.

A hash warning is important, but it does not always prove the file can never work. Some systems have multiple compatible BIOS revisions. If a game works, the warning may simply mean your file is not the exact reference file the checker expected.

If a game does not work, replace the BIOS with the exact expected filename and a known-good dump from your own legal source.

## Arcade and Neo Geo BIOS exception

Arcade systems can be unusual. For FBNeo Neo Geo games, keep `neogeo.zip` in the same ROM folder as the game ZIPs, such as:

```text
Roms/Neo Geo (FBN)/neogeo.zip
Roms/Arcade (FBN)/neogeo.zip
```

This is different from most BIOS files. See [Arcade and FBNeo](roms.md#arcade-and-fbneo).

---

## BIOS reference table

| System | Tag | File Name(s) | BIOS Directory |
|---|---|---|---|
| Doom | PRBOOM | prboom.wad, doom.wad, doom2.wad, doomu.wad, plutonia.wad, tnt.wad, freedoom.wad, freedoom1.wad, freedoom2.wad | SDCARD_ROOT/Bios/PRBOOM/prboom.wad, SDCARD_ROOT/Bios/PRBOOM/doom/doom.wad, SDCARD_ROOT/Bios/PRBOOM/doom2/doom2.wad, SDCARD_ROOT/Bios/PRBOOM/doom-ultimate/doomu.wad, SDCARD_ROOT/Bios/PRBOOM/plutonia/plutonia.wad, SDCARD_ROOT/Bios/PRBOOM/tnt/tnt.wad, SDCARD_ROOT/Bios/PRBOOM/freedoom/freedoom.wad, SDCARD_ROOT/Bios/PRBOOM/freedoom1/freedoom1.wad, SDCARD_ROOT/Bios/PRBOOM/freedoom2/freedoom2.wad |
| Famicom Disk System | FC | disksys.rom | SDCARD_ROOT/Bios/FC/disksys.rom |
| Game Boy | GB | gb_bios.bin | SDCARD_ROOT/Bios/GB/gb_bios.bin |
| Game Boy Color | GBC | gbc_bios.bin | SDCARD_ROOT/Bios/GBC/gbc_bios.bin |
| Game Boy Advance | GBA | gba_bios.bin | SDCARD_ROOT/Bios/GBA/gba_bios.bin |
| Game Boy Advance | MGBA | gba_bios.bin | SDCARD_ROOT/Bios/MGBA/gba_bios.bin |
| Sega CD / Mega-CD | SEGACD | bios_CD_E.bin, bios_CD_J.bin, bios_CD_U.bin | SDCARD_ROOT/Bios/SEGACD/bios_CD_E.bin, SDCARD_ROOT/Bios/SEGACD/bios_CD_J.bin, SDCARD_ROOT/Bios/SEGACD/bios_CD_U.bin |
| Amiga | PUAE | kick33180.A500, kick34005.A500, kick34005.CDTV, kick37175.A500, kick37350.A600, kick39106.A1200, kick39106.A4000, kick40060.CD32, kick40060.CD32.ext, kick40063.A600, kick40068.A1200, kick40068.A4000 | SDCARD_ROOT/Bios/PUAE/kick33180.A500, SDCARD_ROOT/Bios/PUAE/kick34005.A500, SDCARD_ROOT/Bios/PUAE/kick34005.CDTV, SDCARD_ROOT/Bios/PUAE/kick37175.A500, SDCARD_ROOT/Bios/PUAE/kick37350.A600, SDCARD_ROOT/Bios/PUAE/kick39106.A1200, SDCARD_ROOT/Bios/PUAE/kick39106.A4000, SDCARD_ROOT/Bios/PUAE/kick40060.CD32, SDCARD_ROOT/Bios/PUAE/kick40060.CD32.ext, SDCARD_ROOT/Bios/PUAE/kick40063.A600, SDCARD_ROOT/Bios/PUAE/kick40068.A1200, SDCARD_ROOT/Bios/PUAE/kick40068.A4000 |
| PC Engine | PCE | syscard3.pce | SDCARD_ROOT/Bios/PCE/syscard3.pce |
| Pokémon Mini | PKM | bios.min | SDCARD_ROOT/Bios/PKM/bios.min |
| Sony PlayStation | PS | psxonpsp660.bin | SDCARD_ROOT/Bios/PS/psxonpsp660.bin |
| Super Game Boy | SGB | sgb.bios | SDCARD_ROOT/Bios/SGB/sgb.bios |
