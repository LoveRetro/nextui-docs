# PortMaster on NextUI

PortMaster lets supported handhelds run many native Linux game ports. On NextUI, PortMaster support is provided through community Paks and may have different compatibility than other firmware.

## What PortMaster is for

PortMaster does not run Windows x86 games. Most supported ports are native Linux/ARM ports, wrapper scripts, or ports that need files from a game you legally own.

In many cases, PortMaster installs the launcher and patching logic, but you must still provide commercial game data.

## Install flow

1. Connect to Wi-Fi.
2. Open `Tools`.
3. Launch `Pak Store`.
4. Install the PortMaster-related Pak available for your device.
5. Launch PortMaster.
6. Update PortMaster if prompted.
7. Install a port.
8. Read the port's instructions.
9. Copy required game data if the port requires it.
10. Launch the game from the appropriate Ports folder/menu.

## Why only some ports are visible

Port availability depends on your device, platform support, runtime support, and PortMaster's filters.

If you only see a small number of ports:

- update PortMaster;
- check filters;
- allow experimental ports only if you understand they may fail;
- install/update runtimes if the PortMaster UI offers them;
- confirm your device is supported by the port.

Smart Pro S and experimental devices may have fewer working Paks or ports until maintainers and Pak authors add support.

## Required game files

Many ports require files from a legally owned copy of the game.

Common symptoms of missing or wrong game data:

- the port launches then immediately exits;
- a patcher runs and fails;
- the game reaches a splash screen and crashes;
- logs mention missing files.

NextUI docs do not provide copyrighted game files or links to them.

## Filesystem limitations

NextUI install docs recommend FAT32 or exFAT. These filesystems do not support Unix symlinks.

Some advanced PortMaster instructions or community fixes may assume symlink support. If a port requires symlinks, it may need a specific NextUI-compatible patch or may not work from a standard FAT32/exFAT card.

## When a PortMaster game returns to the menu

Try this checklist:

1. Update NextUI.
2. Update Pak Store.
3. Update the PortMaster Pak.
4. Update the installed port.
5. Confirm required game files are present.
6. Confirm the port supports your device.
7. Install runtimes if PortMaster offers them.
8. Check logs under `.userdata/<platform>/logs/`.
9. Ask in the PortMaster/community Pak support channel with the log file.

## Support boundaries

NextUI maintainers may not be able to support every third-party PortMaster port. When asking for help, include:

```text
Device:
NextUI version:
PortMaster Pak version:
Port name:
How it was installed:
Required files copied:
What happens on launch:
Log file:
```