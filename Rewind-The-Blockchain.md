# Rewind The Blockchain

This guide will teach you how to rewind the SPACE blockchain.

This applies to both [Spacecoind](https://github.com/spaceworksco/spacecoin) and [Spacecoin-QT](https://spaceworks.co/spacecoin/wallets#spacecoin-qt).

## Table of Contents

- [Please Note](#Please-Note)
- [Instructions](#Instructions)

### Please Note

When rewinding, make sure you choose a block a bit before the block when your error occurred.

Certain times a rewind will fail and you will need to [resync the blockchain](Resync-The-Blockchain.md).

### Instructions

1. Close/stop your spacecoin wallet.

2. Navigate to the spacecoin-qt/spacecoin folder.

3. Run `spacecoin-qt`/`spacecoind` with the option `-rewind=xxxxxx`. xxxxxx is the block height it will rewind to.
Ex: `spacecoin-qt -rewind=313131`

On windows, go to your `spacecoin-qt` file, right click and select `Create Shortcut`.
Then right click on the shortcut and select `Properties`
Then go to the `Target` field on the Shortcut page of the Properties screen.
Add `-rewind=xxxxxxx` directly after spacecoin-qt.exe

4. Let the blockchain rewind to the specified block and then sync to the latest block.
