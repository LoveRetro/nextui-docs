# File Transfer

You do not always need to remove the SD card to add ROMs, BIOS files, artwork, logs, or screenshots. NextUI users commonly use Web Dashboard, Central Scrutinizer, FTP/HTTP Paks, or a normal SD-card reader.

## Option 1: Web Dashboard over USB

Use the Web Dashboard for fast USB file management:

1. Open `https://dashboard.loveretro.games/` on your computer.
2. Connect the device to your computer with a USB cable.
3. Use the **bottom USB port** on the device.
4. Follow the dashboard prompts.
5. Add ROMs, BIOS files, artwork, or download logs.

This is usually the fastest option when you do not want to remove the SD card.

## Option 2: Central Scrutinizer over Wi-Fi

Central Scrutinizer is a community Pak for browser-based device management over Wi-Fi.

1. Connect the device to Wi-Fi.
2. Open `Tools`.
3. Launch `Pak Store`.
4. Install `Central Scrutinizer`.
5. Launch Central Scrutinizer and follow its on-screen instructions.
6. Open the shown address on a phone or computer on the same network.

Central Scrutinizer can help add ROMs, BIOS files, and artwork. It can also be useful from a phone.

## Option 3: FTP or HTTP Paks

FTP and HTTP file-transfer Paks can expose the SD card over the network.

General flow:

1. Install the FTP or HTTP Pak from Pak Store.
2. Launch the Pak from Tools.
3. Note the IP address and port shown by the Pak.
4. Connect from your computer or phone with an FTP client or browser.
5. Copy files to the correct folder.

FTP is useful for repeated smaller transfers. For very large ROM sets, removing the SD card may still be faster.

## Option 4: Remove the SD card

A normal SD-card reader is still the simplest and most reliable option for large transfers.

Always:

- power down the device first;
- safely eject/unmount the card from your computer;
- avoid removing the card while files are being written.

## Which option should I use?

| Task | Best option |
|---|---|
| Add a few ROMs | Web Dashboard, Central Scrutinizer, FTP, or SD reader |
| Add a large ROM library | SD reader |
| Add BIOS files during setup | Web Dashboard or SD reader |
| Pull logs for support | Web Dashboard, Central Scrutinizer, or SD reader |
| Manage files from a phone | Central Scrutinizer or HTTP/FTP Pak |
| Avoid removing the SD card | Web Dashboard over USB |

## Troubleshooting transfer problems

If Web Dashboard does not connect:

- use the bottom USB port;
- try another USB cable that supports data, not only charging;
- try another browser;
- close other tools that may be using the device connection.

If Wi-Fi tools do not connect:

- make sure the device and computer/phone are on the same network;
- update the Pak;
- check the IP address and port;
- temporarily disable VPNs or firewall rules that block local network access.