# Spacecoin Build From Source

This guide will teach you how to run spacecoin by building from source.

This guide is intended for Ubuntu 16.04/18.04.

## Table of Contents

- [Install Spacecoin](#Install-Spacecoin)
- [Run Spacecoin](#Run-Spacecoin)


### Install Spacecoin

SSH into your sever or open Terminal on your machine.

Install the needed dependencies:

`sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool libncurses-dev unzip git python zlib1g-dev wget bsdmainutils automake libboost-all-dev libssl-dev libprotobuf-dev protobuf-compiler libqrencode-dev libdb++-dev ntp ntpdate nano software-properties-common curl libevent-dev libcurl4-gnutls-dev cmake clang libsodium-dev -y``

Clone and build spacecoin:

```shell
git clone https://github.com/SpaceWorksCo/spacecoin --branch master --single-branch
cd spacecoin
./zcutil/fetch-params.sh
./zcutil/build.sh -j4
# Change -j4 to specify the number of cores to use. ex: -j2
cd
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
