<!--suppress HtmlUnknownTarget -->
<img src="../_inc/images/brick-nextui-animated-black.webp" alt="NextUI Animated on TrimUI Brick" class="docs-logo docs-logo-light" />
<img src="../_inc/images/brick-nextui-animated-white.webp" alt="NextUI Animated on TrimUI Brick" class="docs-logo docs-logo-dark" />

# **Welcome to the NextUI Docs!**

NextUI is a custom firmware for the Trimui Brick, Trimui Smart Pro, and Trimui Smart Pro S retro handhelds. It keeps the simple launcher style of MinUI while adding device-specific features such as Wi-Fi, game artwork, shaders, overlays, LED controls, a game switcher, game-time tracking, Paks, and RetroAchievements.

[Installation Instructions](getting-started/installation.md){ .md-button .md-button--primary }

---

## Start here

New to NextUI? Start with these pages:

- [Installation](getting-started/installation.md) for fresh SD-card setup.
- [Updating](getting-started/updating.md) for existing cards.
- [ROMs, BIOS, and Arcade](getting-started/roms.md) for exact folder names and file-placement rules.
- [Troubleshooting](support/troubleshooting.md) if the device boots to stock OS, only shows Tools, or a game will not launch.
- [Pak Store](pak-store.md) for optional tools, emulators, PortMaster, and file-transfer options.

---

## Supported devices

NextUI currently supports:

| Device | Status | Platform | Notes |
|---|---|---|---|
| Trimui Brick | Supported | `tg5040` | Main NextUI target. Many device-specific features were first built around this device. |
| Trimui Smart Pro | Supported | `tg5040` | Shares the same platform and most Paks with the Brick. |
| Trimui Smart Pro S | Supported | `tg5050` | Some community Paks may need explicit Smart Pro S support before they appear or work. |
| Trimui Brick Hammer | Supported (same as Brick) | `tg5040` | The Brick Hammer is functionally identical to the Trimui Brick. Use the same SD card and Paks. |

For other devices, check the project status before installing. Experimental ports may exist but should not be treated as supported unless they are listed here.

---

## What NextUI adds

NextUI focuses on a fast, simple handheld experience. Features include:

- rebuilt emulation engine work to reduce tearing and sync stutter;
- low-latency audio and video behavior;
- a game switcher menu;
- Wi-Fi support for updates, Pak Store, RetroAchievements, and network tools;
- game artwork and media support;
- shaders and overlays;
- cheat-file support for compatible libretro cores;
- optional community Paks for extra emulators, tools, PortMaster, file transfer, and more;
- configurable display settings, color temperature, and brightness;
- configurable LED behavior on supported devices;
- game-time and battery tracking;
- RTC and NTP time synchronization;
- deep sleep behavior designed for quick resume.

---

## Community Paks

Paks are optional add-ons. They can add tools, extra emulators, PortMaster support, file transfer, scrapers, and other community features. Paks are powerful, but they are also platform-specific. A Pak that works on one supported device may not work on another until the Pak author adds support for that platform.

See [Pak Store](pak-store.md) for installation and troubleshooting.

---

## Need help?

Most setup issues are caused by one of these: SD-card formatting, files copied to the wrong level, missing ROMs, missing BIOS files, or using a ROM set that does not match the selected emulator.

Start with [Troubleshooting](support/troubleshooting.md). If you still need help, include your device, NextUI version, SD-card format, exact folder path, exact filename, and any log files when asking in [Discord :simple-discord:]({{ urls.discord }}).

---

## About NextUI

NextUI was started by [@ro8inmorgan](https://github.com/ro8inmorgan) as a fork of the popular MinUI CFW by [@shauninman](https://github.com/shauninman/MinUI).

Many community members have contributed Paks, overlays, themes, and support. Special thanks to [@frysee](https://github.com/frysee) for ongoing improvements.