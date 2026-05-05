# Controls and Shortcuts

This page lists common NextUI controls. Some shortcuts can be changed per emulator from the in-game menu.

## In the main menu

| Action | Shortcut |
|---|---|
| Adjust brightness | Hold `Start` and press `Volume Up` or `Volume Down` |
| Adjust color temperature | Hold `Select` and press `Volume Up` or `Volume Down` |
| Open game switcher | Short press `Select` |

## In game

| Action | Shortcut |
|---|---|
| Open in-game options | Press `Menu` |
| Open game switcher | Hold `Menu` and `Select` together |

The in-game options menu is where you change frontend options, emulator options, controls, scaling, shaders, overlays, and shortcuts for compatible emulators.

## Save states and quick actions

Open the in-game menu with `Menu` to manage save states, load states, emulator options, and shortcuts.

## Screenshots

NextUI supports screenshot notifications and in-game screenshot behavior. Screenshots are saved to:

```text
Screenshots/<rom_name>.<YYYY-MM-DD-HH-MM-SS>.png
```

The `Screenshots/` folder is created automatically.

To take a screenshot, open the in-game menu with `Menu`, navigate to Controls or Shortcuts, and map a screenshot shortcut if one is not already bound. By default, the screenshot shortcut is unbound.

## FN / mute switch

NextUI supports configurable FN/mute switch behavior on devices that have the switch.

Known uses include:

- toggling a night-mode style display profile;
- toggling D-pad/analog behavior;
- toggling turbo behavior.

If volume buttons appear locked or the FN switch does more than you expect, check Settings for FN-switch options. Setting `Volume when toggled` to `unchanged` is a common fix if the FN switch is muting volume unexpectedly.

## Sleep behavior

When the device is idle, NextUI first turns the screen off and may pulse LEDs. By default, `Screen timeout` is 60 seconds and `Suspend timeout` is 30 seconds after screen-off. Both values can be changed in Settings.

Standalone emulator Paks may not resume from sleep as reliably as built-in emulators.

## SD card eject

The microSD slot is spring-loaded. Press the card inward gently to release it. Do not confuse the reset button with the SD eject mechanism.
