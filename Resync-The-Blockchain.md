# Resync The Blockchain

This guide will teach you how to resync the SPACE blockchain from scratch.

This applies to both [Spacecoind](https://github.com/spaceworksco/spacecoin) and [Spacecoin-QT](https://spaceworks.co/spacecoin/wallets#spacecoin-qt).

## Table of Contents

- [Please Note](#Please-Note)
- [Instructions](#Instructions)

### Please Note

A full resync can take some time to download and process all of the blocks.

Never delete the `wallet.dat` file when deleting blockchain files.

The `wallet.dat` holds all of your addresses and private keys.

For a faster resync, take a look at the [Bootstrap The Blockchain](Bootstrap-The-Blockchain.md) guide.

### Instructions

1. Close/stop your spacecoin wallet.

2. Navigate to the spacecoin [data directory](Find-Data-Directory.md).

3. Delete the `blocks` and `chainstate` folders.

4. Open/start your spacecoin wallet.

5. Let the blockchain sync.
