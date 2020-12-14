# Build From Source

This guide will teach you how to build [Spacecoin (SPACE)](https://spaceworks.co/spacecoin) source code and run.

## Table of Contents

- [Build Spacecoin](#Build-Spacecoin)
  - [Linux](#Linux)
  - [Mac](#Mac)
  - [Windows](#Windows)
- [Run Spacecoin](#Run-Spacecoin)


### Build Spacecoin

SSH into your machine or open a terminal.

#### Linux
```shell
#Install dependencies:
sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl libsodium-dev
# Clone the spacecoin repo
git clone https://github.com/SpaceWorksCo/spacecoin --branch master --single-branch
# Change master branch to other branch you wish to compile
cd spacecoin
./zcutil/fetch-params.sh
./zcutil/build.sh -j4
# Change -j4 to specify the number of cores to use. ex: -j2
# This can take some time.
```

#### Mac
Ensure you have [brew](https://brew.sh) and Command Line Tools installed.
```shell
# Install brew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
# Install Xcode, opens a pop-up window to install CLT without installing the entire Xcode package
xcode-select --install
# Update brew and install dependencies
brew update
brew upgrade
brew tap discoteq/discoteq; brew install flock
brew install autoconf autogen automake
brew update && brew install gcc@8
brew install binutils
brew install protobuf
brew install coreutils
brew install wget
# Clone the spacecoin repo
git clone https://github.com/SpaceWorksCo/spacecoin --branch master --single-branch
# Change master branch to other branch you wish to compile
cd spacecoin
./zcutil/fetch-params.sh
./zcutil/build-mac.sh -j$(expr $(sysctl -n hw.ncpu) - 1)
# This can take some time.
```

#### Windows
Use a debian cross-compilation setup with mingw for windows and run:
```shell
#Install dependencies:
sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl cmake mingw-w64 libsodium-dev libevent-dev
#Install rust targeting x86_64-pc-windows
curl https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env
rustup target add x86_64-pc-windows-gnu

sudo update-alternatives --config x86_64-w64-mingw32-gcc
# (configure to use POSIX variant)
sudo update-alternatives --config x86_64-w64-mingw32-g++
# (configure to use POSIX variant)

#Clone the spacecoin repo
git clone https://github.com/SpaceWorksCo/spacecoin --branch master --single-branch
# Change master branch to other branch you wish to compile
cd spacecoin
./zcutil/fetch-params.sh
./zcutil/build-win.sh -j$(expr $(nproc) - 1)
#This can take some time.
```

### Run Spacecoin

Navigate to the spacecoin/src directory:

`cd spacecoin/src`

Start a new screen for spacecoin:

`screen -S spacecoin`

Start spacecoin:

`./spacecoind`

Here you will see all of the output from spacecoind as spacecoin starts up and syncs.

Use `Ctrl + A` + `Ctrl + D` to exit the screen. (you can return to it at any point with `screen -r spacecoin`)
