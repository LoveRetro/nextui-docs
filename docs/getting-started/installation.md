### Installation Instructions

!!! warning "Formatting will erase all data from the SD card"
    Back up anything important before formatting or repartitioning the card.

!!! warning "Do not unzip `MinUI.zip`"
    The release archive must be extracted on your computer, but the `MinUI.zip` file inside that archive must be copied to the SD-card root as a zip file. Do not extract `MinUI.zip`.

## What you need

- A supported device: a TrimUI Brick, Brick Pro, Smart Pro, or Smart Pro S, or an Anbernic RG XX (H700) device. See [Prerequisites](index.md) for the full list.
- A microSD card formatted as FAT32 or exFAT.
- A Master Boot Record partition table.
- The latest NextUI release archive ending in `-base.zip` or `-all.zip`.
- Your own ROM and BIOS files. NextUI does not include games or copyrighted BIOS files.

## Fresh install

1. Insert the microSD card into your computer.
2. Format the card as FAT32 or exFAT.
3. Make sure the card uses the **Master Boot Record (MBR)** partition scheme.
4. Download the latest NextUI release archive from [GitHub]({{ urls.github }}/releases).
    - Use the archive ending in `-base.zip` for a normal installation.
    - Use the archive ending in `-all.zip` if you also want the extra emulator/tool folders included.
5. Extract the release archive on your computer.
6. Open the extracted folder.
7. Copy the contents of the extracted folder to the root of your SD card.
8. Confirm that `MinUI.zip` is on the SD-card root and is still zipped.
9. Safely eject the SD card.
10. Insert the SD card into your device.
11. Power on the device.
12. Wait while the NextUI installation screen runs. Do not power off the device during installation.
13. When installation is complete, the device can shut down. Power it on again.

## Anbernic RG XX (H700) devices

The base steps above apply, but Anbernic devices do not use the `trimui/` folder. Instead:

1. Copy `MinUI.zip` (still zipped) to the root of the SD card.
2. Copy the `dmenu.bin` file from the `h700` folder of the release to the root of the **ROMS partition** of your stock OS card.
3. In the stock OS, set the user interface theme to **old style** (the default). NextUI will not start with "MU style 1" or "MU style 2".

To uninstall NextUI and return to the stock OS, delete `dmenu.bin` again.

## What the SD-card root should look like

The important part is that the release contents are copied directly to the card root, not inside another folder.

For `NextUI-20260407-0-base.zip`, the card root on a TrimUI device should include:

```text
SDCARD_ROOT/
├── Bios/
├── Cheats/
├── MinUI.zip
├── Overlays/
├── README.txt
├── Roms/
├── Saves/
├── Shaders/
├── nextui.pak_store.pakz
├── nextui.updater.pakz
├── nextui.upgrade_bluez.tg5040.pakz
└── trimui/
```

The `-all.zip` release includes the same root files plus:

```text
SDCARD_ROOT/
├── Emus/
└── Tools/
```

The `-extras.zip` archive contains extra content folders only. It does not replace the base archive for a fresh install.

Wrong:

```text
SDCARD_ROOT/
└── NextUI-v6.10.0-base/
    ├── MinUI.zip
    └── trimui/
```

If your card looks like the wrong example, move the files out of the extracted release folder and onto the SD-card root.

## Linux formatting example

Most users should use a graphical formatter. Advanced Linux users can create a compatible single-partition FAT32 card like this:

```bash
sudo parted -s /dev/sdX mklabel msdos mkpart primary fat32 1MiB 100%
sudo mkfs.vfat -F 32 -n NEXTUI /dev/sdX1
```

Replace `/dev/sdX` with the actual SD-card device. Be careful: using the wrong disk name can erase another drive.

This creates an MBR partition table, starts the first partition at 1 MiB, uses the rest of the card, and formats the partition as FAT32.

## If the device boots stock OS instead of NextUI

Check these first:

- The card is MBR, not GPT.
- `MinUI.zip` is on the SD-card root and is still zipped.
- TrimUI: the `trimui/` folder from the release is on the SD-card root.
- Anbernic: `dmenu.bin` is on the ROMS partition of the stock OS card, and the stock OS theme is set to "old style".
- The release files are not nested inside an extra folder.
- You safely ejected the card after copying files.
- Try a different SD card if settings are not saving or files keep corrupting.

See [Troubleshooting](../support/troubleshooting.md) for a full decision tree.
