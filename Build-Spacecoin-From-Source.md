# Build Spacecoin From Source

This guide will teach you how to build [Spacecoin](https://github.com/spaceworksco/spacecoin) source code.

## Table of Contents

  - [Please Note](#Please-Note)
  - [Linux](#Linux)
  - [Mac](#Mac)
  - [Windows](#Windows)

### Please Note

Instructions vary based on your operating system.

The Windows instructions are intended for Ubuntu to cross compile for Windows.

### Linux

1. Open the Terminal.

2. Install dependencies:

    `sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl libsodium-dev`

3. Clone the Spacecoin repository:

    `git clone https://github.com/SpaceWorksCo/spacecoin`

4. Enter the Spacecoin directory:

    `cd spacecoin`

5. Fetch the zcash paramaters:

    `./zcutil/fetch-params.sh`

6. Build Spacecoin: (Replace -j4 with the number of cores you'd like to use.)

    `./zcutil/build.sh -j4`

Spacecoin is built and ready to run.

### Mac

1. Open the Terminal.

2. Install brew:

    `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

3. Install Xcode: (A pop-up window will open to install CLT without installing the entire Xcode package.)

    `xcode-select --install`

4. Update brew:

    `brew update`

5. Upgrade brew:

    `brew upgrade`

6. Install dependencies:

    ```
    brew tap discoteq/discoteq; brew install flock
    brew install autoconf autogen automake
    brew install gcc@8
    brew install binutils
    brew install protobuf
    brew install coreutils
    brew install wget
    ```

7. Clone the Spacecoin repository:

    `git clone https://github.com/SpaceWorksCo/spacecoin`

8. Enter the Spacecoin directory:

    `cd spacecoin`

9. Fetch the zcash paramaters:

    `./zcutil/fetch-params.sh`

10. Build Spacecoin: (Replace -j4 with the number of cores you'd like to use.)

    `./zcutil/build-mac.sh -j4`

Spacecoin is built and ready to run.

### Windows

1. Open the Terminal.

2. Install dependencies:

    `sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl cmake mingw-w64 libsodium-dev libevent-dev`

3. Install rust targeting x86_64-pc-windows:

    ```
    curl https://sh.rustup.rs -sSf | sh
    source $HOME/.cargo/env
    rustup target add x86_64-pc-windows-gnu
    ```

4. Configure to use POSIX variants:

    ```
    sudo update-alternatives --config x86_64-w64-mingw32-gcc
    sudo update-alternatives --config x86_64-w64-mingw32-g++
    ```

5. Clone the Spacecoin repository:

    `git clone https://github.com/SpaceWorksCo/spacecoin`

6. Enter the Spacecoin directory:

    `cd spacecoin`

7. Build Spacecoin: (Replace -j4 with the number of cores you'd like to use.)

    `./zcutil/build-win.sh -j4`

Spacecoin is built and ready to run.
