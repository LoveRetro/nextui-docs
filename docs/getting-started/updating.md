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
12. When the update completes, the device can shut down. Power it on again.

## Updating a card used on another supported device

If you move the same SD card to another supported TrimUI device, make sure the card has the current release's `trimui/` folder at the SD-card root.

Settings, saves, ROMs, BIOS files, artwork, and Paks live on the SD card, but device-specific settings and logs may be stored under different `.userdata/<platform>/` folders such as `.userdata/tg5040/` and `.userdata/tg5050/`.
