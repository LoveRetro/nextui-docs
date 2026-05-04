# PortMaster on NextUI

PortMaster support on NextUI is community-provided through Paks.

NextUI maintainers do not maintain PortMaster, PortMaster runtimes, individual ports, port scripts, or port compatibility. For PortMaster help, use the Discord community Pak or PortMaster channels and include logs.

## Compatibility limits

Running PortMaster on TrimUI Brick and TrimUI Smart Pro is challenging because those devices use the Allwinner A133P chipset. Smart Pro S has the same class of issue on the Allwinner A523. These devices do not have the native 32-bit driver support that many PortMaster ports expect, so compatibility is limited even when the Pak installs correctly.

NextUI install docs recommend FAT32 or exFAT. These filesystems do not support Unix symlinks. Ports or fixes that rely on symlinks need a NextUI-compatible workaround.

## What PortMaster is for

PortMaster does not run Windows x86 games. Most supported ports are native Linux/ARM ports, wrapper scripts, or ports that need files from a game you legally own.

In many cases, PortMaster installs the launcher and patching logic, but you must still provide commercial game data.

## Install flow

1. Connect to Wi-Fi.
2. Open `Tools`.
3. Launch `Pak Store`.
4. Install the PortMaster-related Pak available for your device.
5. Launch PortMaster.
6. Follow the PortMaster and individual port instructions.
7. Copy required game data if the port requires it.

## Getting help

Before asking for PortMaster help:

- update Pak Store;
- update the PortMaster Pak;
- update the installed port;
- confirm required game files are present;
- check logs under `.userdata/<platform>/logs/`.

Ask in the Discord community Pak or PortMaster channels with:

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
