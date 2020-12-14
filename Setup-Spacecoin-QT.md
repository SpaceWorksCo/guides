# Setup Spacecoin-QT

This guide will teach you how to setup the Spacecoin-QT wallet for your desired platform.

## Table of Contents

- [Please Note](#Please-Note)
- [Instructions](#Instructions)

### Please Note

Spacecoin-QT is a full node wallet, meaning it will need to download the entire blockchain before being used to send transactions or stake.

To speed up the blockchain sync time, you can use the [Blockchain Boostrap Guide](https://github.com/SpaceWorksCo/guides/blob/master/Bootstrap-The-Blockchain.md#bootstrap-the-blockchain).

If you're looking for a lite wallet without the blockchain download, try [Spacecoin Electrum](https://spaceworks.co/spacecoin/wallets/#spacecoin-electrum).

### Instructions

Download Spacecoin-QT for you desired platform from [spaceworks.co/spacecoin/wallets](https://spaceworks.co/spacecoin/wallets/#spacecoin-qt) or [github](https://github.com/spaceworksco/spaceocean/releases/latest).

Extract the downloaded file and enter the folder.

Run the `fetch-params` file to download the necessary proving keys. (Only necessary to do once. If you've downloaded them previously then this step can be skipped)

Run `spacecoin-qt` to start the wallet.

Let the wallet sync the entire blockchain before using. You can see the progress in the bottom right corner by hovering your mouse over the spinning arrows.

Start sending and receiving SPACE, and staking!
