# Spacecoin Staking Node

This guide will teach you how to setup a setup a proper Spacecoin staking node utilizing all of the 64 segID addresses.

## Table of Contents

- [Requirements](#Requirements)
- [Install Komodo](#Install-Komodo)
- [Setup Spacecoin](#Setup-Spacecoin)
- [Install pos64staker](#Install-pos64staker)
- [Setup pos64staker](#Setup-pos64staker)
- [Launch Spacecoin](#Launch-Spacecoin)
- [Finish](#Finish)
- [Next Time](#Next-Time)
- [Withdraw](#Withdraw)

### Requirements

- Machine: You need a machine to run Spacecoin and pos64staker, preferably a linux server that can stay running 24/7. This guide is intended for ubuntu 16.04/18.04 but can be adapted to other platforms.

- Coins: You need Spacecoin to be able to stake. Mine or buy some so that you have a balance. Preferably in a wallet other than the staking node. We will send them to the staking node during setup.

- Security: Since your node will be holding coins make sure it's secure. Here's an initial server setup for ubuntu 16.04 (do the recommended steps 4 and 5): https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04

- CLI Background: While we tried to make the guide as easy as possible, it's good to have an understanding of how the command line works and what you're actually entering.

**Consider using small amounts of coins if it's your first time doing this process or using CLI commands.**


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

### Setup Spacecoin

Navigate to the komodo/src directory:

`cd komodo/src`

Start a new screen for spacecoin:

`screen -S spacecoin`

Start spacecoin:

`./komodod -ac_name=SPACE -ac_supply=0 -ac_eras=6 -ac_reward=3600000000,2700000000,1800000000,900000000,600000000,300000000 -ac_end=939393,3757572,12212109,325343422,638474735,951606048 -ac_blocktime=30 -ac_staked=50 -ac_cbmaturity=1 -ac_cc=939 -ac_sapling=1 -addnode=165.227.35.158 -addnode=167.172.39.135`

Here you will see all of the output from komodod as spacecoin starts up and syncs.

Use `Ctrl + A` + `Ctrl + D` to exit the screen. (you can return to it at any point with `screen -r spacecoin`)

Use `./komodo-cli -ac_name=SPACE getnewaddress` to get a new Spacecoin address.

Fund your staking node by sending SPACE to this address.

Use `./komodo-cli -ac_name=SPACE getinfo` to check info from the spacecoin daemon.

When `blocks` is equal to `longestchain` the blockchain is fully synced.

Also check `balance` is greater than 0.


### Install pos64staker

Install the needed dependencies:

```shell
cd
sudo apt-get install python3-dev
sudo apt-get install python3 libgnutls28-dev libssl-dev
sudo apt-get install python3-pip
pip3 install setuptools
pip3 install wheel
pip3 install base58 slick-bitcoinrpc
```

Clone pos64staker and enter the directory:

```shell
git clone https://github.com/KMDLabs/pos64staker
cd pos64staker
```

### Setup pos64staker

Run the genaddresses script to create your 64 addresses:

`./genaddresses.py`

It will ask you to specify which chain. Tell it `SPACE` for spacecoin:

`Please specify chain:SPACE`

This will create a `list.json` file in the current directory (/home/pos64staker).

**THIS FILE CONTAINS PRIVATE KEYS. KEEP IT SAFE. DO NOT SHARE**

Copy the `list.json` file to the directory `komodod` is located:

`cp list.json ~/komodo/src/list.json`

Open the `list.json` file so you can get your pubkey.

`nano list.json`

Copy/paste the pubkey of the first segID to a txt file so you can use it later.

Use `Ctrl + X` to exit the file.

Distribute your Spacecoin to all 64 addresses:

`./sendmany64.py`

Specify `SPACE` as your chain and decide on the size and amount of UTXOS to send.

Ideally you'd like to try to use the entire balance on you sent to the node.

```shell
Please specify chain:SPACE
Balance:1200
Please specify the size of UTXOs:9
Please specify the amount of UTXOs to send to each segID:2
```
Please take note of what this is actually asking for:

The above example will send 1152 coins total. It will send 18 coins in 2 UTXOs (9 each) to each of your 64 addresses (segIDs).      ((9 * 2) * 64) = 1152

It will give an error if your entered amounts are more than your balance. It will tell you how much available you have for each segID.


### Launch Spacecoin

Return to the `komodo/src` directory:

`cd && cd komodo/src`

Stop the running spacecoin daemon:

`./komodo-cli -ac_name=SPACE stop`

Resume the spacecoin screen:

`screen -r spacecoin`

Restart the spacecoin chain with `-pubkey` and `-blocknotify` parameters:

`./komodod -pubkey=<pubkey_from_list.json> -ac_name=SPACE -ac_supply=0 -ac_eras=6 -ac_reward=3600000000,2700000000,1800000000,900000000,600000000,300000000 -ac_end=939393,3757572,12212109,325343422,638474735,951606048 -ac_blocktime=30 -ac_staked=50 -ac_cbmaturity=1 -ac_cc=939 -ac_sapling=1 -addnode=165.227.35.158 -addnode=167.172.39.135 '-blocknotify=/<path_to>/pos64staker/staker.py %s SPACE'`

Make sure to replace `<pubkey_from_list.json>` with the pubkey you copied earlier from the list.json file.
Example: `03edad710b86de3815c45cb16b152ae0c0f8d995f78dfbeca77e5201defde307dc`

Make sure to replace `<path_to>` in `-blocknotify=` with the correct path to the staker.py script.
Example: `/home/$USER/pos64staker/staker.py`

Use `Ctrl + A` + `Ctrl + D` to exit the screen.

Now, you just need to enable staking:

`./komodo-cli -ac_name=SPACE setgenerate true 0`


### Finish

At this point your spacecoin staking node should be setup and staking.

To verify you are staking do:

`./komodo-cli -ac_name=SPACE getgenerate`

look for: `"staking": true,`

For more staking info use:

`./komodo-cli -ac_name=SPACE getbalance64`

After some time of staking check your balance and you'll see it starting to grow:

`./komodo-cli -ac_name=SPACE getinfo`

As you stake blocks and earn more coins, pos64staker will distribute the new coins each of your 64 segID addresses.


### Next Time

If you stop spacecoin at all for updates, machine reboot, etc. simply follow the steps from [Launch Spacecoin](#Launch-Spacecoin) to start staking again!


### Withdraw

If you'd like to withdraw funds from a staking node without messing up the 64 segID distribution, do:

```shell
cd && cd pos64staker
./withdraw.py
```

It will walk you through the withdraw process.
