## Getting Started

!!! warning "Read before continuing!"

    NextUI **officially supports** the TrimUI Brick, TrimUI Smart Pro, TrimUI Smart Pro S, and the TrimUI Brick Hammer (which is functionally the same as the TrimUI Brick).

    The steps outlined here only apply to these supported devices running the stock operating system.

    If you are planning to install NextUI after using a different custom firmware on your device,
    we recommend to first reinstall the TrimUI stock OS to revert any changes that might have been
    made without your knowledge. The only exception is MinUI.



### What You Will Need

- A supported device running the stock operating system.
- A fresh micro SD card from a reputable vendor (SanDisk, Samsung, etc.)
    - The size of the card depends on the size of the ROMs you plan to play
- Software on your computer to format the SD Card
    - On macOS, use built-in Disk Utility application
    - On Windows, use [Rufus](https://rufus.ie/en/)
    - On Linux, create an MBR/msdos partition table, start the first partition at `1MiB`, use the rest of the card, then format that partition as FAT32 or exFAT. For command-line users, the partition step is `sudo parted -s /dev/sdX mklabel msdos mkpart primary fat32 1MiB 100%`; replace `/dev/sdX` with the actual SD-card device before formatting `/dev/sdX1`.
- The latest release of NextUI from the [GitHub Repo :simple-github:]({{ urls.github }}/releases).
    - At minimum, you will need the archive ending in `-base.zip`.
    - If you want additional content, download the archive ending in `-all.zip` or the `-extras.zip`.
- Your own ROM and BIOS files. NextUI does not include copyrighted games or BIOS files.
