It is strongly advised that you build NextUI via Docker instead of using a direct build.  By using Docker, you significantly
reduce the number of differences between your system and the system that developers are building on which reduces issues
where the system builds fine for one person while failing for another. If you need any help, please use this setup - otherwise
you are on your own.

## System requirements
- Linux Operating System capable of running docker
- At least 10 GB of available disk space

## Step 1: Install development-related helper tools
```shell
sudo apt-get install build-essential zip zipmerge
```

## Step 2: Install Docker

| Docker Version | Instructions |
|-|-|
| Docker Engine Only (Does not include Docker Desktop) |[https://docs.docker.com/engine/install/](https://docs.docker.com/engine/install/) |
| Docker Desktop (Also includes Docker Engine) | [https://docs.docker.com/desktop/setup/install/linux/](https://docs.docker.com/desktop/setup/install/linux/) | 

## Step 3: Grab the latest source code
```shell
git clone https://github.com/LoveRetro/NextUI.git
cd NextUI
```

## Step 4: Build the complete package with emulators from source
This is not required on every build.  In fact, you can normally skip this step if you've done it already.

This will grab the latest revisions of all included emulators and build them from scratch. Depending on your 
system, this will take a good amount of time. After completeing this once, it is generally fine to build without
emulator cores (unless you want to pull in the latest and greatest changes).
```shell
make all COMPILE_CORES=true
```

For followup builds with cores in place:
```shell
make all
```

## Step 5: Deploy to your device
If your device is connected via USB, you can deploy your build straight away, without any manual copying.
First, make sure your device is actually discoverable:
```shell
adb devices
```

To deploy your build and install it:
```shell
make deploy
```

This is equivalent to a "quick update" via OTA, i.e. it only deploys the MinUI.zip to update the base UI.
