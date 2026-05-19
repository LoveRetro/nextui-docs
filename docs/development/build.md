# Building NextUI

NextUI has two useful build paths:

- **Handheld builds** use the Docker toolchain images and produce release/update archives for devices.
- **Desktop builds** use the native `desktop` platform and are useful for faster UI/debug work on your host computer.

The top-level Makefile chooses the path from the target platform: `desktop` uses `makefile.native`; handheld platforms use `makefile.toolchain`.

## Platform targets

| Platform | Devices |
|---|---|
| `tg5040` | Trimui Smart Pro / Brick |
| `tg5050` | Trimui Smart Pro S |
| `desktop` | Native host debug build |

## Host requirements

- Git, Make, `zip`, and `zipmerge`
- At least 10 GB free disk space, more if building emulator cores
- Docker for handheld builds
- Native SDL, SDL_image, SDL_ttf, SQLite, libzip, and libsamplerate libraries for `desktop` builds

Apple Silicon Macs and other arm64 hosts are currently the least painful hosts for full handheld builds. x86_64 hosts have historically hit cross-architecture toolchain dependency issues; if you run into missing arm64 libraries in Docker, use an arm64 host or runner.

## macOS setup

Install Homebrew packages:

```shell
brew install gcc make sdl2_image sdl2_ttf sqlite libzip libsamplerate
```

For handheld builds, also install Docker Desktop and make sure it is running.

For native `desktop` builds, the current Makefiles expect suffix-less GCC tool names in `/usr/local/bin`. The repo includes a helper for that:

```shell
sudo ./workspace/desktop/macos_create_gcc_symlinks.sh
```

Inspect the helper before running it if you use `/usr/local/bin` for other local tools.

## Linux setup

Install host tools and desktop dependencies:

```shell
sudo apt-get update
sudo apt-get install build-essential zip zipmerge docker.io \
  libsqlite3-dev libzip-dev libsdl2-dev libsdl2-image-dev libsdl2-ttf-dev \
  libsamplerate0-dev
```

Make sure your user can run Docker, then restart your shell if needed.

## Get the source

```shell
git clone https://github.com/LoveRetro/NextUI.git
cd NextUI
```

## Build for handhelds

The default handheld build covers `tg5040` and `tg5050`:

```shell
make all COMPILE_CORES=true
```

Building cores is slow and usually only needed for the first full build or when core changes are required. For later firmware-only builds:

```shell
make all
```

To build one platform:

```shell
make all PLATFORMS=tg5040 COMPILE_CORES=true
make all PLATFORMS=tg5050 COMPILE_CORES=true
```

Output archives are written to `releases/`.

## Build the desktop target

Use the native desktop target for local debugging:

```shell
make setup common PLATFORM=desktop
```

The repo includes VS Code launch configs in `.vscode/launch.json` that can be copied or adjusted for local debugging.

## Deploy to a device

If your device is connected over USB and visible to ADB:

```shell
adb devices
make deploy
```

This pushes `build/BASE/MinUI.zip` and reboots the device, equivalent to a quick OTA update of the base UI.
