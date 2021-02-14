# Use The Faucet

This guide will teach you how to receive coins from the on-chain SPACE faucet.

The faucet is available with [Spacecoind](https://github.com/spaceworksco/spacecoin) or [Spacecoin-QT](https://spaceworks.co/spacecoin/wallets#spacecoin-qt).

## Table of Contents

- [Please Note](#Please-Note)
- [Background Information](#Background-Information)
- [Instructions](#Instructions)


### Please Note

The faucet requires you to be using a pubkey. For more information see [Pubkey Information](Pubkey-Information.md).

With Spacecoin-QT the commands will need to be entered in the console. This is accessible at `Help -> Debug Window -> Console`.


### Background Information

To receive coins your public address must satisfy a few constraints. The wallet's pubkey (corresponding to the address) must have no history of funds or transactions, and can claim faucet funds only once.

The call also requires the wallet to perform a small PoW calculation. This requires about 30 seconds of CPU time and is done to deter leeching.

When `faucetget` is executed, the on-chain faucet sends 0.1 SPACE to the address that corresponds to the wallet's pubkey. This is enough SPACE to start testing and even [create a token](Create-A-Token.md)


### Instructions

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `faucetget`.

This will return a hex-encoded transaction that needs to be broadcast to the network with `sendrawtransaction`.

3. Enter the command `sendrawtransaction hexFromFaucetGet`

  Example: `sendrawtransaction 0400008085202f89018cc8564e8eab3c702731b319ca93863225b5f8feb3106a5ab5854791b589ae48010000006b483045022100aa4c5f97fdfa05402e26db6951bd9b7611a7022d1f0b555d4ed8ed75c465f5d00220217ce6dcbea90366845326453e242f4b95bea5f0184d32af8a3f43f385ae36d4012103f6f64dff7bc20d882b369f7bfbd63d423a09f8e908f441bef4f5b425727832e1ffffffff02005ed0b200000000302ea22c8020e029c511da55523565835887e412e5a0c9b920801b007000df45e545f25028248103120c008203000401ccf0c1a43500000000232103f6f64dff7bc20d882b369f7bfbd63d423a09f8e908f441bef4f5b425727832e1ac000000006e7301000000000000000000000000`

  This returns a Transaction ID (txid). You can view this transaction on the [explorer](https://explorer.spaceworks.co).
