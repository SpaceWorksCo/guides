# Transfer Tokens

This guide will teach you how to transfer tokens on the SPACE blockchain.

Tokens are available with [Spacecoind](https://github.com/spaceworksco/spacecoin) or [Spacecoin-QT](https://spaceworks.co/spacecoin/wallets#spacecoin-qt).

## Table of Contents

- [Please Note](#Please-Note)
- [Background Information](#Background-Information)
- [Instructions](#Instructions)


### Please Note

Tokens require you to be using a pubkey. For more information see [Pubkey Information](https://github.com/SpaceWorksCo/guides/blob/master/Pubkey-Information.md).

You will need SPACE in your wallet. `1 SPACE` should be enough.

With Spacecoin-QT the commands will need to be entered in the console. This is accessible at `Help -> Debug Window -> Console`.

All of the token methods can be viewed by running `help` or visiting the [Spacecoin RPC Docs](http://spacecoin-rpc.spaceworks.co).

### Background Information

You will need to specify the `tokenid` of the token you wish to transfer.
Example: `e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b`

Tokens are transffered to a `pubkey` instead of a traditional SPACE address.
Example: `039e1f9a06d9d41981d0cc1c380d0965e82250d436523e18b42832b1e41f037e00`

### Instructions

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `tokentransfer tokenid destpubkey amount` replacing the fields with your desired information.

  Example: `tokentransfer e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b 039e1f9a06d9d41981d0cc1c380d0965e82250d436523e18b42832b1e41f037e00 9`

  This will transfer `9 SWTT` tokens to `039e1f9a06d9d41981d0cc1c380d0965e82250d436523e18b42832b1e41f037e00`.

  `tokentransfer` will return a hex-encoded transaction that needs to be broadcast to the network with `sendrawtransaction`.

3. Enter the command `sendrawtransaction hexFromTokenTransfer`

  Example: `sendrawtransaction 0400008085202f890241cb874176d7da36516dde8d65dc42b9d6d96a66e50d4088eeda523577c9c6330200000048473044022017b5a27ab39af78c96422d81b18715fcaae0cb66ece3f37b207b4f139654621702204f3b4d83071faf692acabe2c07f08595cf584b9e028693c612623c3b379c9f6101ffffffff41cb874176d7da36516dde8d65dc42b9d6d96a66e50d4088eeda523577c9c633010000007b4c79a276a072a26ba067a56580210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1ed81408e95b70ce527d4625760c2bdf6c2eaef3a3d8a58c14d4a0f8ee96651d5342e744d60b819932f2e9fe0273c61dce10f4deaf7cdf4f8bfbc9230bed558635082c8a100af038001f2a10001ffffffff040900000000000000302ea22c8020546e056a6d3eba52ac5371bcc5ed114555a430ed9ad424a559c4bfab4a0242ff8103120c008203000401ccd996040000000000302ea22c8020dc90537730533ea80e29564d98be37ae2da447c977a64373328480417cfefcfc8103120c008203000401cc10395c050000000023210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1edac0000000000000000476a45f274e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b0121039e1f9a06d9d41981d0cc1c380d0965e82250d436523e18b42832b1e41f037e00000000009b0f01000000000000000000000000`

  This returns a Transaction ID (txid).
