# Spacecoin Build From Source

This guide will teach you how to run spacecoin by building from source.

This guide is intended for Ubuntu 16.04/18.04.

## Table of Contents

- [Install Komodo](#Install-Komodo)
- [Run Spacecoin](#Run-Spacecoin)


### Install Komodo

SSH into your sever or open Terminal on your machine.

Install the needed dependencies:

`sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl libsodium-dev`

Clone and build komodo:

```shell
git clone https://github.com/komodoplatform/komodo --branch master --single-branch
cd komodo
./zcutil/fetch-params.sh
./zcutil/build.sh -j$(expr $(nproc) - 1)
cd
```

### Run Spacecoin

Navigate to the komodo/src directory:

`cd komodo/src`

Start a new screen for spacecoin:

`screen -S spacecoin`

Start spacecoin:

`./komodod -ac_name=SPACE -ac_supply=0 -ac_eras=6 -ac_reward=3600000000,2700000000,1800000000,900000000,600000000,300000000 -ac_end=939393,3757572,12212109,325343422,638474735,951606048 -ac_blocktime=30 -ac_staked=50 -ac_cbmaturity=1 -ac_cc=939 -ac_sapling=1 -addnode=165.227.35.158 -addnode=167.172.39.135`

Here you will see all of the output from komodod as spacecoin starts up and syncs.

Use `Ctrl + A` + `Ctrl + D` to exit the screen. (you can return to it at any point with `screen -r spacecoin`)
