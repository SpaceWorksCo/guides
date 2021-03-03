# Get Coin Supply

This guide will teach you how to get the coin supply of the SPACE blockchain.

Coin supply is available with [Spacecoind](https://github.com/spaceworksco/spacecoin) or [Spacecoin-QT](https://spaceworks.co/spacecoin/wallets#spacecoin-qt).

## Table of Contents

- [Please Note](#Please-Note)
- [Instructions](#Instructions)


### Please Note

You may specify a block height to retrieve the supply at that block or leave it blank for the current supply.

`coinsupply` has to scan the entire blockchain up to the current or specified block. The response can take some time on slower systems.

This returns a response with the block height, transparent balance (supply), shielded balance (zfunds), and total.

With Spacecoin-QT the command will need to be entered in the console. This is accessible at `Help -> Debug Window -> Console`.


### Instructions

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `coinsupply`. Returns the current block height.

    ```
    {
      "result": "success",
      "coin": "SPACE",
      "height": 322929,
      "supply": 11609278.62399449,
      "zfunds": 15953.03406643,
      "sprout": 0.00000000,
      "total": 11625231.65806092
    }
    ```

3. (Optional) Enter the command: `coinsupply 313131` Returns the specified block height.

    ```
    {
      "result": "success",
      "coin": "SPACE",
      "height": 313131,
      "supply": 11255371.62389449,
      "zfunds": 17132.03416643,
      "sprout": 0.00000000,
      "total": 11272503.65806092
    }
    ```
