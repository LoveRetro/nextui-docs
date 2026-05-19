# Pak Troubleshooting

Paks are optional add-ons. They can be built by different community members and may have different support levels.

## Pak does not appear in Pak Store

Check:

- Wi-Fi is connected.
- Pak Store has been updated.
- Type filter is not hiding it.
- Category filter is not hiding it.
- Platform filter matches your device.
- The Pak supports your device.

If the Pak does not support your device, it will not work until the Pak author adds support.

Smart Pro S users should check compatibility carefully because older Paks can support only earlier TrimUI devices.

## Tool Pak installed but does not appear

Tool Paks should be installed under the root-level `Tools/` folder in the correct platform folder.

Do not put custom Tool Paks in `.system/` because `.system/` is replaced during updates.

Tool Paks for each device:

| Device | Tool Paks folder |
|---|---|
| Trimui Smart Pro / Brick | `Tools/tg5040/` |
| Trimui Smart Pro S | `Tools/tg5050/` |

## Emulator Pak installed but no games show

Emulator Paks need a matching ROM folder tag.

Example:

```text
Emus/<platform>/NDS.pak/
Roms/Nintendo DS (NDS)/Example.nds
```

The folder tag is what matters. `Nintendo DS (NDS)` and `NDS (NDS)` both use the `NDS` Pak.

## Pak launches then returns to menu

Common causes:

- Pak does not support your device.
- Pak is outdated.
- NextUI is outdated.
- Required BIOS, runtime, or game data is missing.
- Stale `.userdata` files are breaking the Pak.
- The Pak uses a standalone emulator with different behavior than built-in emulators.

Try:

1. Update Pak Store.
2. Update the Pak.
3. Confirm the Pak supports your device.
4. Confirm required files are present.
5. Check logs in `.userdata/<platform>/logs/`.
6. Remove stale Pak userdata for that Pak only, then reinstall.

Check logs:

```text
.userdata/<platform>/logs/
```

## Stale Pak userdata

Some Paks store settings or states in `.userdata/shared/`. If a Pak worked before and now fails after an update, stale userdata can be a cause.

Do not delete all of `.userdata` unless you have a backup. Delete only the folder for the affected Pak after confirming the exact path.

## Standalone emulator caveats

Standalone emulator Paks may not support standard NextUI features:

- resume from menu;
- quicksave and auto-resume;
- consistent in-game menus;
- Menu button behavior;
- Power button behavior.

This does not always mean the Pak is broken. Check the Pak's own documentation.
