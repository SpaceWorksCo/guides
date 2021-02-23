# Build Spacecoin-QT From Source

This guide will teach you how to build [Spacecoin-QT](https://github.com/spaceworksco/spaceocean) source code.

## Table of Contents

  - [Please Note](#Please-Note)
  - [Linux](#Linux)
  - [Mac](#Mac)
  - [Windows](#Windows)

### Please Note

Instructions vary based on your operating system.

The Windows instructions are intended for Ubuntu to cross compile for Windows.

There are binaries available if you don't wish to build from source.

### Linux

Open the Terminal.

Install dependencies:

`sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl`

Clone the SpaceOcean repository:

`git clone https://github.com/SpaceWorksCo/SpaceOcean --branch static-spacecoin --single-branch`

Enter the SpaceOcean directory:

`cd SpaceOcean`

Fetch the zcash paramaters:

`./zcutil/fetch-params.sh`

Build Spacecoin-QT: (Replace -j4 with the number of cores you'd like to use.)

`./zcutil/build-linux.sh -j4`

### Mac

Open the Terminal.

Install brew:

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

Install Xcode: (A pop-up window will open to install CLT without installing the entire Xcode package.)

`xcode-select --install`

Update brew:

`brew update`

Upgrade brew:

`brew upgrade`

Install dependencies:

```
brew tap discoteq/discoteq; brew install flock
brew install autoconf autogen automake
brew install gcc@6
brew install binutils
brew install protobuf
brew install coreutils
brew install wget
```

Clone the SpaceOcean repository:

`git clone https://github.com/SpaceWorksCo/SpaceOcean --branch static-spacecoin --single-branch`

Enter the SpaceOcean directory:

`cd SpaceOcean`

Fetch the zcash paramaters:

`./zcutil/fetch-params.sh`

Build Spacecoin-QT: (Replace -j4 with the number of cores you'd like to use.)

`./zcutil/build-mac.sh -j4`


### Windows

Open the Terminal.

Install dependencies:

`sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl cmake mingw-w64`

Install rust targeting x86_64-pc-windows:

```
curl https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env
rustup target add x86_64-pc-windows-gnu
```

Configure to use POSIX variants:

```
sudo update-alternatives --config x86_64-w64-mingw32-gcc
sudo update-alternatives --config x86_64-w64-mingw32-g++
```

Clone the SpaceOcean repository:

`git clone https://github.com/SpaceWorksCo/SpaceOcean --branch static-spacecoin --single-branch`

Enter the SpaceOcean directory:

`cd SpaceOcean`

Build Spacecoin-QT: (Replace -j4 with the number of cores you'd like to use.)

`./zcutil/build-win.sh -j4`
