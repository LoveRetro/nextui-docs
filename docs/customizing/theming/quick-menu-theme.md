## Adding Quick Menu Png's 

Custom backgrounds for the Quick Menu are loaded from `mnt/SDCARD/.media/quick_<settings>.png` with the following valid names.

### Quick Menu Background PNG Directory Structure

```
SD_CARD
├─ .media/
│  ├─ quick_Collections.png                    *Collections List background
│  ├─ quick_Games.png			       *Games List background
│  ├─ quick_Poweroff.png		       *System Power Off background
│  ├─ quick_Reboot.png			       *System Reboot background
│  ├─ quick_Settings.png		       *Settings background
│  ├─ quick_Sleep.png			       *Deep Sleep background
│  ├─ quick_Tools.png			       *Tools list background
│  ├─ quick_Wifi.png			       * Toggle Wifi OFF background (Shown if Wifi is currently ON)
│  ├─ quick_Wifi_off.png		       *Toggle Wifi ON background (Shown if Wifi is currently OFF)
│  ├─ quick_Recents.png  		       *Recently Played List background
│  ├─ quick_Pak Store.png		       *Pak Store background
│  ├─ quick.png				       *Generic fallback background for all slots
```

### Additional Customization notes

Icon assets (small and big) can be replaced as usual in `.system/res`. Please note that these are present in multiple sizes, e.g. "3x" for Brick and "2x" for TSP.
The option to completely hide the UI elements of the quick switcher and build your own UI (with just the background images) is located in Appearance Settings.
Also note that the Pak Store and Collections background will only appear if each are present.
