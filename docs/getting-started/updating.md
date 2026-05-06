### Updating an Existing Installation

!!! warning "Back up first"
    Updating should not delete your ROMs, saves, BIOS files, artwork, or Paks, but you should still back up the card before updating.

!!! warning "Do not unzip `MinUI.zip`"
    Copy `MinUI.zip` to the SD-card root as a zip file. Do not extract it.

## Normal update

For a normal update on an SD card that already runs NextUI, you only need to copy `MinUI.zip` back to the card root.

1. Power off the device.
2. Eject the NextUI SD card and insert it into your computer.
3. Download the latest release archive ending in `-base.zip` from the [GitHub Releases page]({{ urls.github }}/releases).
4. Extract the release archive on your computer.
5. Open the extracted folder.
6. Copy `MinUI.zip` to the **root** of your SD card.
7. Safely eject the SD card.
8. Insert the card into your device.
9. Power on the device.
10. Wait while the NextUI update screen runs. Do not power off the device during the update.
11. When the update completes, the device can shut down. Power it on again.

## When you also need to recopy the `trimui/` folder

Most normal updates do **not** require recopying `trimui/`. Copy the current release's `trimui/` folder back to the SD-card root only when:

- you are doing a fresh install on a new or reformatted card;
- the device boots to the stock TrimUI OS instead of NextUI;
- the stock firmware was updated or reflashed;
- you are moving a NextUI SD card to another supported TrimUI device for the first time.

If unsure, copying both `MinUI.zip` and the current release's `trimui/` folder is a safe repair approach. The installer will behave like an update if the bootstrap pieces are already in place.

## Moving an existing card to another supported device

Settings, saves, ROMs, BIOS files, artwork, and Paks live on the SD card. Device-specific settings and logs live under platform-specific `.userdata/<platform>/` folders, such as:

```text
.userdata/tg5040/
.userdata/tg5050/
```

When first using the card on another supported TrimUI device, copy the current release's `trimui/` folder to the SD-card root and keep `MinUI.zip` available so the installer can perform a repair/update pass.
