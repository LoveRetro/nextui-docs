# Paks

Paks are optional packages that add tools, emulators, ports, file-transfer utilities, save-sync tools, and other community features to NextUI.

The NextUI release includes Pak Store so you can browse and install compatible Paks on the device. The store itself lives at [Pak Store](pak-store.md).

## What is a Pak?

A Pak is a folder ending in `.pak` with a launcher script. Tool Paks appear in `Tools`; emulator Paks appear as game systems when their matching ROM folder exists.

Paks can be built by NextUI contributors or by community members. Check the Pak's own notes for device compatibility, required files, and support boundaries.

## Common Pak categories

- File-transfer Paks, such as FTP, HTTP file browsers, and Central Scrutinizer.
- Save-sync or backup Paks, such as Syncthing and cloud-backup tools.
- Standalone emulator Paks for systems that are not built into the base firmware.
- PortMaster Paks for native game ports.
- Scrapers, collection managers, artwork tools, and other library utilities.

## Save-sync Paks

Syncthing and similar sync tools are community Paks. They can be useful, but they are not part of base NextUI and can copy files that are sensitive to emulator version, save-state format, or device-specific settings.

For syncing between devices:

- Sync `Saves/` first. In-game saves are the safest files to move between devices and emulators.
- Use RetroArch `.srm` saves if you also sync with RetroArch devices, and rename or copy existing saves to the format NextUI is configured to use.
- Avoid syncing a game while it is running.
- Check PlayStation folder names carefully. NextUI uses `PS`; another device can use a different tag.
- Treat `.userdata/` as advanced. It contains save states, launcher metadata, settings, recents, and tracking databases.

Do not sync save states across different cores or emulator versions unless you are prepared to test and recover from broken states.

## More Pak topics

- [Pak Store](pak-store.md) - browse and install Paks on the device.
- [File Transfer](paks/file-transfer.md) - add files without removing the SD card.
- [PortMaster](paks/portmaster.md) - run supported native game ports.
- [Pak Troubleshooting](paks/troubleshooting.md) - common Pak issues.
- [Making Paks](paks/making-paks.md) - create your own Pak.
