# Frequently Asked Questions

Short answers to the setup and support questions people ask most often.

---

## Which release file should I use?

Use the archive ending in `-base.zip` for a normal install or update. Use `-all.zip` if you also want the extra emulator and tool folders included.

The `-extras.zip` archive adds extra folders only. It does not replace the base archive for a fresh install.

After extracting the release archive on your computer, copy the release contents to the SD-card root. Keep `MinUI.zip` zipped.

See [Installation](../getting-started/installation.md) and [Updating](../getting-started/updating.md).

---

## When should I add `MinUI.zip` or the `trimui` folder back to my SD card?

NextUI uses two different items on the root of the SD card:

* `MinUI.zip` is the installer, updater, and repair archive. Do **not** unzip it. It lives in the `-base.zip` and `-all.zip` releases.
* The `trimui` folder contains the Trimui-side launch files that let the stock firmware start NextUI.

Use this guide:

| Situation                                                                               | Add `MinUI.zip`? |           Add `trimui` folder? |
| --------------------------------------------------------------------------------------- | ---------------: | -----------------------------: |
| Fresh NextUI install on a new or reformatted SD card                                    |              Yes |                            Yes |
| Moving an existing NextUI SD card to another supported Trimui device for the first time |              No  |                            Yes |
| Manual NextUI update from a downloaded release                                          |              Yes |                     Usually no |
| Repairing an install that no longer boots correctly                                     |              Yes |                            Yes |
| Device boots to the stock Trimui OS instead of NextUI                                   |              Yes |                            Yes |
| Stock Trimui firmware was updated or reflashed                                          |              Yes |                            Yes |

To install, update, or repair NextUI, download the latest NextUI release and copy the needed files to the **root of the SD card**.

For a normal NextUI update you only need to copy `MinUI.zip`. You do not need to replace the `trimui` folder unless:

- the device is booting the stock TrimUI OS instead of NextUI;
- the stock firmware was reflashed or updated;
- you are moving the card to another supported TrimUI device for the first time.

After a successful install or update, `MinUI.zip` will be removed automatically. That is normal. Adding `MinUI.zip` or the `trimui` folder again should not delete your ROMs, saves, BIOS files, artwork, or Paks; it only restores the launch files used to start NextUI.

---

## I am currently using classic MinUI. How can I migrate?

You can install NextUI over an existing MinUI card. Back up your saves first, then follow the [installation guide](../getting-started/installation.md) using the latest `-all.zip` release if you want the full NextUI folder set.

---

## Why am I only seeing Tools?

NextUI only shows systems that have visible games unless empty systems are enabled.

Put ROMs inside a tagged folder under `Roms/`, for example:

```text
Roms/Game Boy (GB)/Tetris (World).gb
```

See [ROMs, BIOS, and Arcade](../getting-started/roms.md) and [Troubleshooting](troubleshooting.md#the-menu-only-shows-tools).

---

## Can I use one SD card on more than one supported device?

Yes, for supported TrimUI devices. Back up the card first, then copy the current release's `trimui/` folder and keep `MinUI.zip` at the SD-card root before using the card in another supported device.

---

## Why do my arcade or Neo Geo games say "unknown romset"?

Arcade emulators require ROM ZIPs from a matching ROM set. The folder can be correct while the ROM itself is still wrong for the emulator.

For FBNeo, use a folder ending in `(FBN)`, keep arcade ZIP filenames unchanged, and put `neogeo.zip` beside Neo Geo game ZIPs.

See [Arcade and FBNeo](../getting-started/roms.md#arcade-and-fbneo).

---

## Does NextUI support PortMaster?

PortMaster on NextUI is community-provided through Paks. NextUI maintainers do not maintain PortMaster, PortMaster runtimes, individual ports, or port compatibility.

Compatibility is limited by the device hardware, PortMaster support, required game data, runtimes, and SD-card filesystem constraints. Use the community Discord and PortMaster/Pak channels for support.

See [PortMaster on NextUI](../paks/portmaster.md).

---

## My Wi-Fi password keeps disappearing. What should I check?

A wrong Wi-Fi password is not saved. If the password is correct but NextUI keeps asking again, check whether the SD card is writable and healthy.

If Wi-Fi settings, menu settings, or boot behavior fail to persist, try another SD card or check the card for filesystem errors.

---

## Where should I ask for help?

For NextUI setup and base firmware issues, ask in [Discord]({{ urls.discord }}) or GitHub with your device, NextUI version, SD-card format, exact path, exact filename, and logs.

For community Paks, PortMaster, and individual ports, use the Discord community Pak or PortMaster channels. Do not file PortMaster compatibility issues as NextUI maintainer support requests.

Do not share copyrighted ROM or BIOS files.
