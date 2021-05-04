# Get Info About A Fund

This guide will teach you how to get information about a fund.

The heir module is available with [Spacecoind](https://github.com/spaceworksco/spacecoin) or [Spacecoin-QT](https://spacecoin.network/#wallets).

## Table of Contents

- [Please Note](#Please-Note)
- [Background Information](#Background-Information)
- [Instructions](#Instructions)

### Please Note

The Heir module requires you to be using a pubkey. For more information see [Pubkey Information](Pubkey-Information.md).

With Spacecoin-QT the commands will need to be entered in the console. This is accessible at `Help -> Debug Window -> Console`.

### Background Information

To get information about a fund, it must have already been created with [heirfund](Create-A-Fund.md).

You will need to fill in:

  - `fundingtxid` - the txid of the heir fund you want info on.

If you don't know the `fundingtxid` you can use the command `heirlist` to see all of the `fundingtxid` of all the funds available.

### Instructions

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command: `heirinfo fundingtxid`

    Example: `heirinfo 8c692a88942da92e926a778eca7c0a996c7294bd29f7cb92607bbaa4854b10a5`

    This will return all information about the fund.

    ```
    {
      "fundingtxid": "8c692a88942da92e926a778eca7c0a996c7294bd29f7cb92607bbaa4854b10a5",
      "name": "Son",
      "owner": "0322e7941d70b43697d7b402d7f66bc4eb512dc97c0f338c3172f29181260af076",
      "heir": "0347da1a89a90b0b62178abcb2f4d8c64b1ec3fee28c9350aa9ab48804e8455df5",
      "type": "coins",
      "lifetime": "0.10000000",
      "available": "0.10000000",
      "InactivityTimeSetting": "60",
      "IsHeirSpendingAllowed": "true",
      "memo": "Spacecoin Funds for my son",
      "result": "success"
    }
    ```
