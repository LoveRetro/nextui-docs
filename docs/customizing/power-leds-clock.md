# LEDs, Power, Sleep, and Clock

NextUI includes power, sleep, LED, battery, and clock features, but not every feature works the same on every device.

## LED support

All supported devices have configurable LEDs. Use the LED Control app from Tools.

| Device | LED zones | Settings file |
|---|---|---|
| Trimui Brick | F1 key, F2 key, top bar, L/R trigger LEDs | `.userdata/shared/ledsettings_brick.txt` |
| Trimui Smart Pro | Left stick, right stick, TrimUI logo | `.userdata/shared/ledsettings.txt` |
| Trimui Smart Pro S | Left stick, right stick, TrimUI logo | `.userdata/shared/ledsettings.txt` |

## LED Control app

On the home screen:

1. Open `Tools`.
2. Launch `LedControl`.
3. Use the app to choose LED, effect, color, speed, and brightness.

### LED Selection

**Trimui Brick** has the following configurable LEDs:

- Two LEDs on the front of the device for each function button (F1 & F2)
- L/R trigger LEDs, controlled as one zone
- One LED bar on the top of the device

**Trimui Smart Pro and Smart Pro S** have the following configurable LEDs:

- Left stick LED
- Right stick LED
- TrimUI logo LED

When in the LED Control App you can use `Left Trigger` and `Right Trigger` to cycle between these LEDs.

### Effects

Each LED can be configured with the following effects.

| Effect Name | Description |
|---|---|
| Static | Keep the LED(s) on and static |
| Blink 1 | Quickly blink 1 time |
| Blink 2 | Quickly blink 2 times |
| Linear | Slowly increase the brightness and then fall back to off |
| Breathe | Slowly increase the brightness and slowly decrease the brightness |
| Interval Breathe | Slowly increase the brightness and slowly decrease the brightness, with a longer pause between "breaths" |

### Color

The color of LEDs. Use `Left` and `Right` on the `D-Pad` to cycle through the colors.

### Speed

The speed of breathing effect in milliseconds.

### Brightness

The brightness level of the LEDs. Setting this to `0` will turn the LED off.

### Info Brightness

The brightness of LED when informing you about something.

Currently, this is only supported by:

- Power Button turning red alerting for low battery
- Front Function Button LED blinking when entering sleep

Setting brightness to `0` will turn the LED off.

### Ambient Mode

!!! info "Only supported by certain emulator cores"

    Ambient light effects are only supported by the built in Libretro cores.

Ambient light mode makes your LEDs change color to match the dominant color on screen during gameplay.

To enable ambient mode (in a supported emulator) follow these steps:

1. While in game, press the `Menu` button
2. Select `Options`
3. Select `Frontend`
4. Scroll down to the Ambient Mode line and turn it on. You can select to use all LEDs or just a specific one.

!!! info "Ambient mode sets the LED Brightness to Maximum"

    We found that lower brightness levels will result in displaying an incorrect color.

## Sleep behavior

When the device is idle, NextUI first turns the screen off and may pulse LEDs. By default, `Screen timeout` is 60 seconds and `Suspend timeout` is 30 seconds after screen-off. Both values can be changed in Settings.

If a standalone emulator Pak wakes to a black screen or audio-only state, quit and relaunch the game. Standalone Paks may not resume as reliably as built-in emulators.

## FN / mute switch

NextUI supports configurable FN/mute switch behavior on devices that have the switch.

Known uses include:

- toggling a night-mode style display profile;
- toggling D-pad/analog behavior;
- toggling turbo behavior.

If volume buttons appear locked or the FN switch does more than you expect, check Settings for FN-switch options. Setting `Volume when toggled` to `unchanged` is a common fix if the FN switch is muting volume unexpectedly.

## Clock, RTC, and NTP

NextUI supports real-time clock behavior and automatic NTP time synchronization.

The clock can be updated:

- manually through a Clock Pak where available;
- automatically over Wi-Fi with NTP when enabled and connected.

Use Settings to configure time-related options such as timezone when available.

## Battery tracking

NextUI tracks battery history and estimated time remaining.

Battery tracking data is stored in:

```text
.userdata/shared/battery_logs.sqlite
```
