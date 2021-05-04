# Write A Key Value Pair

This guide will teach you how to write a key value pair to the SPACE blockchain.

KV is available with [Spacecoind](https://github.com/spaceworksco/spacecoin) or [Spacecoin-QT](https://spacecoin.network/#wallets).

## Table of Contents

- [Please Note](#Please-Note)
- [Background Information](#Background-Information)
- [Instructions](#Instructions)

### Please Note

With Spacecoin-QT the commands will need to be entered in the console. This is accessible at `Help -> Debug Window -> Console`.

### Background Information

Key Value pairs expire after a specified amount of days.

The days are based on KMD's 1440 blocks per day. Decide how many days you want and multiply by 2 because SPACE has 2880 blocks per day.  

If your KV pair is going to expire you can follow the same steps to update it.

### Instructions

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `kvupdate key "value" days*2 passphrase`.

    Example: `kvupdate testing "This is my kv test value" 400 mytestingpassphrase`

    This will output the KV entry with all of the relevant information.

    ```
{
  "coin": "tSPACE",
  "height": 153,
  "expiration": 145593,
  "flags": 401,
  "key": "testing",
  "keylen": 7,
  "value": "This is my kv test value",
  "valuesize": 24,
  "fee": 0.0017776,
  "txid": "55c037b75d548324e24da24cceb8353012b546d3d93cb03de34f837e82cf85a6"
}
```

You can now [read this KV pair](Read-A-Key-Value-Pair.md) from the blockchain.
