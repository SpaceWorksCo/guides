# Add To A Fund

This guide will teach you how to add Spacecoin or tokens to a fund.

The heir module is available with [Spacecoind](https://github.com/spaceworksco/spacecoin) or [Spacecoin-QT](https://spaceworks.co/spacecoin/wallets#spacecoin-qt).

## Table of Contents

- [Please Note](#Please-Note)
- [Background Information](#Background-Information)
- [Instructions](#Instructions)

### Please Note

The Heir module requires you to be using a pubkey. For more information see [Pubkey Information](Pubkey-Information.md).

With Spacecoin-QT the commands will need to be entered in the console. This is accessible at `Help -> Debug Window -> Console`.

### Background Information

To add Spacecoin or tokens to a fund, it must have already been created with [heirfund](Create-A-Fund.md).

When the owner of the fund adds Spacecoin or tokens, the inactivity time is reset. If anyone else adds funds, it is considered a donation and the inactivity period continues.

You will need to fill in:

  - `amount` - is the number of coins or tokens to claim (spend).

  - `fundingtxid` - the txid of the heir fund you're adding to.

### Instructions

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command: `heiradd amount fundingtxid`

    Example: `heiradd 1000 c5889a3b42544fe7c71be6cd3020a983d6f590972dc4936bcfd717f968f1d995`

    This will return a hex-encoded transaction that needs to be broadcast to the network with `sendrawtransaction`.

3. Enter the command `sendrawtransaction hexFromHeirAdd`

    Example: `sendrawtransaction 0400008085202f89018cc8564e8eab3c702731b319ca93863225b5f8feb3106a5ab5854791b589ae48010000006b483045022100aa4c5f97fdfa05402e26db6951bd9b7611a7022d1f0b555d4ed8ed75c465f5d00220217ce6dcbea90366845326453e242f4b95bea5f0184d32af8a3f43f385ae36d4012103f6f64dff7bc20d882b369f7bfbd63d423a09f8e908f441bef4f5b425727832e1ffffffff02005ed0b200000000302ea22c8020e029c511da55523565835887e412e5a0c9b920801b007000df45e545f25028248103120c008203000401ccf0c1a43500000000232103f6f64dff7bc20d882b369f7bfbd63d423a09f8e908f441bef4f5b425727832e1ac000000006e7301000000000000000000000000`

    This returns a Transaction ID (txid). You can view this transaction on the [explorer](https://explorer.spaceworks.co).
