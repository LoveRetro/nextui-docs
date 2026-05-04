### Updating an Existing Installation

!!! warning "Back up first"
    Updating should not delete your ROMs, saves, BIOS files, or artwork, but you should still back up the card before updating.

!!! warning "Do not unzip `MinUI.zip`"
    Copy `MinUI.zip` to the SD-card root as a zip file. Do not extract it.

## Normal update

1. Power off the device.
2. Eject the NextUI SD card and insert it into your computer.
3. Download the latest release archive ending in `-base.zip` from the [GitHub Releases page]({{ urls.github }}/releases).
4. Extract the release archive on your computer.
5. Open the extracted folder.
6. Copy `MinUI.zip` and the `trimui/` folder to the root of your SD card.
7. Allow your computer to merge or replace the existing `trimui/` folder.
8. Safely eject the SD card.
9. Insert the card into your device.
10. Power on the device.
11. Wait while the NextUI update screen runs. Do not power off the device during the update.
12. The device may shut down when the update completes. Power it on again.

## What is safe to keep?

These folders normally contain your personal data and should be kept when updating:

```text
Roms/
Bios/
Saves/
Collections/
Overlays/
Shaders/
Tools/            # if you installed custom Tool Paks
Emus/             # if you installed custom Emulator Paks
Cheats/
.userdata/
.media folders inside Roms/
```

Copying an empty folder from the release over an existing folder should not remove existing files, but a full backup is still the safest option.

## Custom files that updates may replace

The hidden `.system/` folder is replaced during updates. Do not store custom Paks or user files in `.system/`.

Put optional Paks in root-level `Tools/` or `Emus/` platform folders instead.

## Updating a card used on another supported device

If you move the same SD card to another supported Trimui device, make sure the card also has the platform bootstrap folder from a recent release. For current Trimui releases, that means copying the `trimui/` folder from the release to the SD-card root.

Settings, saves, ROMs, BIOS files, artwork, and Paks live on the SD card, but device-specific settings and logs may be stored under different `.userdata/<platform>/` folders such as `.userdata/tg5040/` and `.userdata/tg5050/`.