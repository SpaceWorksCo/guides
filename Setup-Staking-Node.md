# Spacecoin Staking Node

This guide will teach you how to setup a setup a proper Spacecoin staking node utilizing all of the 64 segID addresses.

## Table of Contents

- [Requirements](#Requirements)
- [Install Spacecoin](#Install-Spacecoin)
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


### Install Spacecoin

1. SSH into your sever or open Terminal on your machine.

2. Install the needed dependencies:

    `sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl libsodium-dev`

3. Clone and build spacecoin:

    ```shell
    git clone https://github.com/SpaceWorksCo/spacecoin --branch master --single-branch
    cd spacecoin
    ./zcutil/fetch-params.sh
    ./zcutil/build.sh -j4
    # Change -j4 to specify the number of cores to use. ex: -j2
    cd
    ```

### Setup Spacecoin

1. Navigate to the spacecoin/src directory:

    `cd spacecoin/src`

2. Start a new screen for spacecoin:

    `screen -S spacecoin`

3. Start spacecoin:

    `./spacecoind`

Here you will see all of the output from spacecoind as spacecoin starts up and syncs.

4. Use `Ctrl + A` + `Ctrl + D` to exit the screen. (you can return to it at any point with `screen -r spacecoin`)

5. Use `./spacecoin-cli getnewaddress` to get a new Spacecoin address.

6. Fund your staking node by sending SPACE to this address.

7. Use `./spacecoin-cli getinfo` to check info from the spacecoin daemon.

When `blocks` is equal to `longestchain` the blockchain is fully synced.

Also check `balance` is greater than 0.


### Install pos64staker

1. Install the needed dependencies:

    ```shell
    cd
    sudo apt-get install python3-dev
    sudo apt-get install python3 libgnutls28-dev libssl-dev
    sudo apt-get install python3-pip
    pip3 install setuptools
    pip3 install wheel
    pip3 install base58 slick-bitcoinrpc
    ```

2. Clone pos64staker and enter the directory:

    ```shell
    git clone https://github.com/KMDLabs/pos64staker
    cd pos64staker
    ```

### Setup pos64staker

1. Run the genaddresses script to create your 64 addresses:

    `./genaddresses.py`

2. It will ask you to specify which chain. Tell it `SPACE` for spacecoin:

    `Please specify chain:SPACE`

This will create a `list.json` file in the current directory (/home/pos64staker).

**THIS FILE CONTAINS PRIVATE KEYS. KEEP IT SAFE. DO NOT SHARE**

3. Copy the `list.json` file to the directory `spacecoind` is located:

    `cp list.json ~/spacecoin/src/list.json`

4. Open the `list.json` file so you can get your pubkey.

    `nano list.json`

5. Copy/paste the pubkey of the first segID to a txt file so you can use it later.

    Example of Pubkey: `039e1f9a06d9d41981d0cc1c380d0965e82250d436523e18b42832b1e41f037e00`

6. Use `Ctrl + X` to exit the file.

7. Distribute your Spacecoin to all 64 addresses:

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

1. Return to the `spacecoin/src` directory:

    `cd && cd spacecoin/src`

2. Stop the running spacecoin daemon:

    `./spacecoin-cli stop`

3. Resume the spacecoin screen:

    `screen -r spacecoin`

4. Restart the spacecoin chain with `-pubkey` and `-blocknotify` parameters:

    `./spacecoind -pubkey=<pubkey_from_list.json> '-blocknotify=/<path_to>/pos64staker/staker.py %s SPACE'`

    Make sure to replace `<pubkey_from_list.json>` with the pubkey you copied earlier from the list.json file.
    Example: `03edad710b86de3815c45cb16b152ae0c0f8d995f78dfbeca77e5201defde307dc`

    Make sure to replace `<path_to>` in `-blocknotify=` with the correct path to the staker.py script.
    Example: `/home/$USER/pos64staker/staker.py`

5. Use `Ctrl + A` + `Ctrl + D` to exit the screen.

6. Enable staking:

    `./spacecoin-cli setgenerate true 0`


### Finish

At this point your spacecoin staking node should be setup and staking.

1. To verify you are staking do:

    `./spacecoin-cli getgenerate`

    look for: `"staking": true,`

2. For more staking info use:

    `./spacecoin-cli getbalance64`

3. After some time of staking check your balance and you'll see it starting to grow:

    `./spacecoin-cli getinfo`

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
