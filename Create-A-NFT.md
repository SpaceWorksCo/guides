# Create A NFT

This guide will teach you how to create a Non Fungible Token (NFT) on the SPACE blockchain.

Tokens are available with [Spacecoind](https://github.com/spaceworksco/spacecoin) or [Spacecoin-QT](https://spaceworks.co/spacecoin/wallets#spacecoin-qt).

## Table of Contents

- [Please Note](#Please-Note)
- [Background Information](#Background-Information)
- [Instructions](#Instructions)


### Please Note

Tokens require you to be using a pubkey. For more information see [Pubkey Information](Pubkey-Information.md).

You will need SPACE in your wallet. `1 SPACE` will be more than enough.

With Spacecoin-QT the commands will need to be entered in the console. This is accessible at `Help -> Debug Window -> Console`.

All of the token methods can be viewed by running `help` or visiting the [Spacecoin RPC Docs](https://docs.spacecoin.network).

### Background Information

Determine the `name` and `description` for your NFT.

The `supply` for NFT's will always be 1 satoshi (0.00000001 SPACE).

### Instructions

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `tokencreate name supply description` replacing the fields with your desired information.

    Example: `tokencreate SATELITE123 0.00000001 "Satelite 123"`. This will create a NFT named `SATELITE123`.

    `tokencreate` will return a hex-encoded transaction that needs to be broadcast to the network with `sendrawtransaction`.

3. Enter the command `sendrawtransaction hexFromTokenCreate`

    Example: `sendrawtransaction 0400008085202f890141cb874176d7da36516dde8d65dc42b9d6d96a66e50d4088eeda523577c9c6330200000048473044022029a2a8f917583a3df1f820ea0523756c9e79d1a1223b2b153246514c2983cf11022013f537c51b3e4aae33ee5a7a4ba7c92b1fad45e7d626e547e368ba5878289c0f01ffffffff041027000000000000302ea22c8020432de388aabcb6b4e3326351d1d815cee8be9a8d37b055cd1c0cf8782e5c50c08103120c008203000401cc8901000000000000302ea22c8020dc90537730533ea80e29564d98be37ae2da447c977a64373328480417cfefcfc8103120c008203000401cc77105c050000000023210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1edac0000000000000000386a36f263210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1ed0754455354494e47097465737420636f696e00000000340f01000000000000000000000000`

    This returns a Transaction ID (txid). This txid is also your tokenid.
