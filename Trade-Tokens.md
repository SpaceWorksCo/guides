# Trade Tokens

This guide will teach you how to trade tokens on the SPACE blockchain.

Tokens are available with [Spacecoind](https://github.com/spaceworksco/spacecoin) or [Spacecoin-QT](https://spaceworks.co/spacecoin/wallets#spacecoin-qt).

## Table of Contents

- [Please Note](#Please-Note)
- [Background Information](#Background-Information)
- [View Orders](#View-Orders)
- [View My Orders](#View-My-Orders)
- [Place A Buy Order](#Place-A-Buy-Order)
- [Place A Sell Order](#Place-A-Sell-Order)
- [Cancel A Buy Order](#Cancel-A-Buy-Order)
- [Cancel A Sell Order](#Cancel-A-Sell-Order)
- [Buy Tokens](#Buy-Tokens)
- [Sell Tokens](#Sell-Tokens)


### Please Note

Tokens require you to be using a pubkey. For more information see [Pubkey Information](https://github.com/SpaceWorksCo/guides/blob/master/Pubkey-Information.md).

You will need SPACE in your wallet.

With Spacecoin-QT the commands will need to be entered in the console. This is accessible at `Help -> Debug Window -> Console`.

All of the token methods can be viewed by running `help` or visiting the [Spacecoin RPC Docs](http://spacecoin-rpc.spaceworks.co).

### Background Information

To place buy/sell orders use `ask` and `bid`.

To cancel an open order use `cancelask` and `cancelbid`.

To buy/sell tokens use `fillask` and `fillbid`.

To see all orders for a token use `tokenorders`

### View Orders

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `tokenorders [tokenid]` replacing the fields with your desired information.

  Example: `tokenorders e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b`
  This will return all orders for token `e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b`.

  Example: `tokenorders`
  This will return all orders for all tokens.

### View My Orders

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `mytokenorders`.

  This will return all of your pubkeys open orders for all tokens.

### Place A Buy Order

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `tokenbid numtokens tokenid price` replacing the fields with your desired information.

  Example: `tokenbid 393 e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b 0.1`
  This will place a buy order for `393` of `e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b` tokens with a price of `0.1 SPACE`.

  `tokenbid` will return a hex-encoded transaction that needs to be broadcast to the network with `sendrawtransaction`.

3. Enter the command `sendrawtransaction hexFromTokenBid`

  Example: `sendrawtransaction 0400008085202f890141cb874176d7da36516dde8d65dc42b9d6d96a66e50d4088eeda523577c9c6330200000048473044022029a2a8f917583a3df1f820ea0523756c9e79d1a1223b2b153246514c2983cf11022013f537c51b3e4aae33ee5a7a4ba7c92b1fad45e7d626e547e368ba5878289c0f01ffffffff041027000000000000302ea22c8020432de388aabcb6b4e3326351d1d815cee8be9a8d37b055cd1c0cf8782e5c50c08103120c008203000401cc8901000000000000302ea22c8020dc90537730533ea80e29564d98be37ae2da447c977a64373328480417cfefcfc8103120c008203000401cc77105c050000000023210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1edac0000000000000000386a36f263210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1ed0754455354494e47097465737420636f696e00000000340f01000000000000000000000000`

  This returns a Transaction ID (txid).

### Place A Sell Order

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `tokenask numtokens tokenid price` replacing the fields with your desired information.

  Example: `tokenask 393 e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b 1`
  This will place a sell order for `393` of `e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b` tokens with a price of `1 SPACE`.

  `tokenask` will return a hex-encoded transaction that needs to be broadcast to the network with `sendrawtransaction`.

3. Enter the command `sendrawtransaction hexFromTokenAsk`

  Example: `sendrawtransaction 0400008085202f890141cb874176d7da36516dde8d65dc42b9d6d96a66e50d4088eeda523577c9c6330200000048473044022029a2a8f917583a3df1f820ea0523756c9e79d1a1223b2b153246514c2983cf11022013f537c51b3e4aae33ee5a7a4ba7c92b1fad45e7d626e547e368ba5878289c0f01ffffffff041027000000000000302ea22c8020432de388aabcb6b4e3326351d1d815cee8be9a8d37b055cd1c0cf8782e5c50c08103120c008203000401cc8901000000000000302ea22c8020dc90537730533ea80e29564d98be37ae2da447c977a64373328480417cfefcfc8103120c008203000401cc77105c050000000023210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1edac0000000000000000386a36f263210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1ed0754455354494e47097465737420636f696e00000000340f01000000000000000000000000`

  This returns a Transaction ID (txid).

### Cancel A Buy Order

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `tokencancelbid tokenid bidtxid` replacing the fields with your desired information.

    Example: `tokencancelbid e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b 6053e01d5e19d2270148213542779ab78837cd9026048e6d6c51b5861a8f18fb`
    This will cancel buy order `6053e01d5e19d2270148213542779ab78837cd9026048e6d6c51b5861a8f18fb` for token `e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b`.

    `tokencancelbid` will return a hex-encoded transaction that needs to be broadcast to the network with `sendrawtransaction`.

3. Enter the command `sendrawtransaction hexFromTokenCancelBid`

    Example: `sendrawtransaction 0400008085202f890141cb874176d7da36516dde8d65dc42b9d6d96a66e50d4088eeda523577c9c6330200000048473044022029a2a8f917583a3df1f820ea0523756c9e79d1a1223b2b153246514c2983cf11022013f537c51b3e4aae33ee5a7a4ba7c92b1fad45e7d626e547e368ba5878289c0f01ffffffff041027000000000000302ea22c8020432de388aabcb6b4e3326351d1d815cee8be9a8d37b055cd1c0cf8782e5c50c08103120c008203000401cc8901000000000000302ea22c8020dc90537730533ea80e29564d98be37ae2da447c977a64373328480417cfefcfc8103120c008203000401cc77105c050000000023210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1edac0000000000000000386a36f263210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1ed0754455354494e47097465737420636f696e00000000340f01000000000000000000000000`

    This returns a Transaction ID (txid).

### Cancel A Sell Order

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `tokencancelask tokenid asktxid` replacing the fields with your desired information.

    Example: `tokencancelask e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b 6053e01d5e19d2270148213542779ab78837cd9026048e6d6c51b5861a8f18fb`
    This will cancel sell order `6053e01d5e19d2270148213542779ab78837cd9026048e6d6c51b5861a8f18fb` for token `e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b`.

    `tokencancelask` will return a hex-encoded transaction that needs to be broadcast to the network with `sendrawtransaction`.

3. Enter the command `sendrawtransaction hexFromTokenCancelAsk`

    Example: `sendrawtransaction 0400008085202f890141cb874176d7da36516dde8d65dc42b9d6d96a66e50d4088eeda523577c9c6330200000048473044022029a2a8f917583a3df1f820ea0523756c9e79d1a1223b2b153246514c2983cf11022013f537c51b3e4aae33ee5a7a4ba7c92b1fad45e7d626e547e368ba5878289c0f01ffffffff041027000000000000302ea22c8020432de388aabcb6b4e3326351d1d815cee8be9a8d37b055cd1c0cf8782e5c50c08103120c008203000401cc8901000000000000302ea22c8020dc90537730533ea80e29564d98be37ae2da447c977a64373328480417cfefcfc8103120c008203000401cc77105c050000000023210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1edac0000000000000000386a36f263210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1ed0754455354494e47097465737420636f696e00000000340f01000000000000000000000000`

    This returns a Transaction ID (txid).

### Buy Tokens

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `tokenfillask tokenid asktxid fillunits` replacing the fields with your desired information.

  Example: `tokenfillask e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b 6053e01d5e19d2270148213542779ab78837cd9026048e6d6c51b5861a8f18fb 93`
  This will buy `93 e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b` tokens from order `6053e01d5e19d2270148213542779ab78837cd9026048e6d6c51b5861a8f18fb`.

  `tokenfillask` will return a hex-encoded transaction that needs to be broadcast to the network with `sendrawtransaction`.

3. Enter the command `sendrawtransaction hexFromTokenFillAsk`

    Example: `sendrawtransaction 0400008085202f890141cb874176d7da36516dde8d65dc42b9d6d96a66e50d4088eeda523577c9c6330200000048473044022029a2a8f917583a3df1f820ea0523756c9e79d1a1223b2b153246514c2983cf11022013f537c51b3e4aae33ee5a7a4ba7c92b1fad45e7d626e547e368ba5878289c0f01ffffffff041027000000000000302ea22c8020432de388aabcb6b4e3326351d1d815cee8be9a8d37b055cd1c0cf8782e5c50c08103120c008203000401cc8901000000000000302ea22c8020dc90537730533ea80e29564d98be37ae2da447c977a64373328480417cfefcfc8103120c008203000401cc77105c050000000023210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1edac0000000000000000386a36f263210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1ed0754455354494e47097465737420636f696e00000000340f01000000000000000000000000`

      This returns a Transaction ID (txid).

### Sell Tokens

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `tokenfillbid tokenid bidtxid fillunits` replacing the fields with your desired information.

  Example: `tokenfillbid e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b 6053e01d5e19d2270148213542779ab78837cd9026048e6d6c51b5861a8f18fb 93`
  This will sell `93 e6f7accda67f906f4e45449c44a28e968ceead98b7d7a8a22cda9282e73c782b` tokens to order `6053e01d5e19d2270148213542779ab78837cd9026048e6d6c51b5861a8f18fb`.

  `tokenfillbid` will return a hex-encoded transaction that needs to be broadcast to the network with `sendrawtransaction`.

3. Enter the command `sendrawtransaction hexFromTokenFillBid`

  Example: `sendrawtransaction 0400008085202f890141cb874176d7da36516dde8d65dc42b9d6d96a66e50d4088eeda523577c9c6330200000048473044022029a2a8f917583a3df1f820ea0523756c9e79d1a1223b2b153246514c2983cf11022013f537c51b3e4aae33ee5a7a4ba7c92b1fad45e7d626e547e368ba5878289c0f01ffffffff041027000000000000302ea22c8020432de388aabcb6b4e3326351d1d815cee8be9a8d37b055cd1c0cf8782e5c50c08103120c008203000401cc8901000000000000302ea22c8020dc90537730533ea80e29564d98be37ae2da447c977a64373328480417cfefcfc8103120c008203000401cc77105c050000000023210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1edac0000000000000000386a36f263210251731f82671b78bd32a60faddc1ec4909903d889f23831736c32d9784dacb1ed0754455354494e47097465737420636f696e00000000340f01000000000000000000000000`

  This returns a Transaction ID (txid).
