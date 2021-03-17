# Read A Key Value Pair

This guide will teach you how to read a key value pair from the SPACE blockchain.

KV is available with [Spacecoind](https://github.com/spaceworksco/spacecoin) or [Spacecoin-QT](https://spaceworks.co/spacecoin/wallets#spacecoin-qt).

## Table of Contents

- [Please Note](#Please-Note)
- [Background Information](#Background-Information)
- [Instructions](#Instructions)

### Please Note

With Spacecoin-QT the commands will need to be entered in the console. This is accessible at `Help -> Debug Window -> Console`.

### Background Information

Anyone can read KV data from the blockchain by search for a key.

### Instructions

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `kvsearch key`.

    Example: `kvsearch testing`

    This will return information about the `testing` key value pair.

    ```
    {
      "coin": "tSPACE",
      "currentheight": 154,
      "key": "testing",
      "keylen": 7,
      "owner": "5977102975eb8ce29ccb4d551a3192a200b7f40dcba0b5b10048adecc6ab3fdd",
      "height": 153,
      "expiration": 1593,
      "flags": 0,
      "value": "This is my kv test value",
      "valuesize": 24
    }
    ```
