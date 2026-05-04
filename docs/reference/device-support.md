# Device Support

NextUI is built for specific handhelds. Device support matters because each device can have different boot files, internal platform folders, buttons, LEDs, toolchains, and Pak compatibility.

## Officially supported devices

| Device | Support status | Platform | Bootstrap folder | Notes |
|---|---|---|---|---|
| Trimui Brick | Supported | `tg5040` | `trimui` | Main NextUI target. Many device-specific features, such as LED controls, were first built around this device. |
| Trimui Smart Pro | Supported | `tg5040` | `trimui` | Shares the same platform and most Paks with the Brick. |
| Trimui Smart Pro S | Supported | `tg5050` | `trimui` | Uses a separate platform. Some community Paks may not appear until they add Smart Pro S support. |
| Trimui Brick Hammer | Supported (same as Brick) | `tg5040` | `trimui` | The Brick Hammer is functionally identical to the Trimui Brick. Use the same SD card and Paks. |

If a device is not listed above, do not assume a NextUI release for it is supported.

## Can I share one SD card between devices?

You can usually share a NextUI SD card between closely related supported Trimui devices, but the second device still needs the correct boot/bootstrap folder from a recent release.

A safe workflow is:

1. Back up the SD card first.
2. Download the latest NextUI release archive ending in `-base.zip` or `-all.zip`.
3. Extract the archive on your computer.
4. Copy the device bootstrap folder, such as `trimui/`, from the extracted release to the SD-card root.
5. Keep `MinUI.zip` at the SD-card root.
6. Insert the card into the second device and let the install/update hook run.

!!! warning
    Do not copy only your ROM folders to a second device and expect the boot hook to install itself. The platform bootstrap folder from the release is what lets the stock firmware start NextUI.

## Pak compatibility by device

Paks are platform-specific. If a Pak is missing from Pak Store, does not appear after installation, or launches back to the menu, check whether it supports your device/platform.

For Smart Pro S users, this is especially important because older Paks may only support the `tg5040` platform. Use the Pak Store platform filter when available.

| Device | Platform | Tool Paks | Emulator Paks |
|---|---|---|---|
| Trimui Brick | `tg5040` | `Tools/tg5040/` | `Emus/tg5040/` |
| Trimui Smart Pro | `tg5040` | `Tools/tg5040/` | `Emus/tg5040/` |
| Trimui Smart Pro S | `tg5050` | `Tools/tg5050/` | `Emus/tg5050/` |
| Trimui Brick Hammer | `tg5040` | `Tools/tg5040/` | `Emus/tg5040/` |