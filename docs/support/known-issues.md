# Known Issues

This page lists known issues that have been verified against current or recent NextUI releases.

If an issue is not listed here, check [Troubleshooting](troubleshooting.md) and the latest GitHub release notes.

## Documentation issues

These are docs issues, not firmware issues:

- Some older docs referred to `minui.zip` or `miniui.zip`. The correct filename is `MinUI.zip`.
- Some older docs listed RetroAchievements as future work. RetroAchievements was added in NextUI v6.9.0.
- Some older docs under-described Smart Pro S support. Smart Pro S is listed as a supported device in the current public README.
- Some older LED docs said LED Controls only support Brick. LedControl is available for all supported devices.

## RetroAchievements

Standard RetroAchievements are supported in NextUI v6.9.0 and later. Hardcore mode is not currently available.

## Shader presets

NextUI v6.10.0 added support for loading shader parameter values from `.cfg` preset files. The older `.glsp` preset format is not supported.

See [Shaders](../shaders/index.md) for the correct layout.

## Smart Pro S Pak availability

Some community Paks do not appear on Smart Pro S until the Pak author adds Smart Pro S support. This is a compatibility filter, not a firmware bug.

## PortMaster compatibility

PortMaster on NextUI has limited compatibility. Public support reports show that PortMaster on the Trimui Brick is limited: some ports work, many do not. Treat PortMaster as optional and community-supported.

See [PortMaster](../paks/portmaster.md) for details.
