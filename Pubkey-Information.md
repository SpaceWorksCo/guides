# Pubkey Information

This guide will teach you how to use pubkeys with SPACE.

## Table of Contents

- [Please Note](#Please-Note)
- [Find a Pubkey](#Find-A-Pubkey)
- [Make a new Pubkey](#Make-A-New-Pubkey)
- [Using a Pubkey](Using-A-Pubkey)

### Please Note

With Spacecoin-QT the commands will need to be entered in the console. This is accessible at `Help -> Debug Window -> Console`.

Pubkeys are necessary when using CryptoConditons modules such as Tokens.

A wallet with a set pubkey will send change from transactions to the address of that pubkey.

### Find A Pubkey

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `validateaddress yourSpacecoinAddress`.

Example: `validateaddress RC7X8pGZ5GJH5hCHFb6skbsrfg5oEHjc2y`

It will return:
```
{
  "isvalid": true,
  "address": "RC7X8pGZ5GJH5hCHFb6skbsrfg5oEHjc2y",
  "scriptPubKey": "76a9141f142028ff5ef909dd52cba1d920a212c3132ce588ac",
  "segid": 63,
  "ismine": true,
  "iswatchonly": false,
  "isscript": false,
  "pubkey": "039e1f9a06d9d41981d0cc1c380d0965e82250d436523e18b42832b1e41f037e00",
  "iscompressed": true,
  "account": "Example Address"
}
```

In the returned output, `039e1f9a06d9d41981d0cc1c380d0965e82250d436523e18b42832b1e41f037e00` is your pubkey!

The pubkey field will only be returned if `"ismine": true`. Your wallet must own the address.

### Make A New Pubkey

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `getnewaddress`.

It will return a new address. Example: `RC7X8pGZ5GJH5hCHFb6skbsrfg5oEHjc2y`

3. Enter the command `validateaddress yourNewSpacecoinAddress`.

Example: `validateaddress RC7X8pGZ5GJH5hCHFb6skbsrfg5oEHjc2y`

It will return:
```
{
  "isvalid": true,
  "address": "RC7X8pGZ5GJH5hCHFb6skbsrfg5oEHjc2y",
  "scriptPubKey": "76a9141f142028ff5ef909dd52cba1d920a212c3132ce588ac",
  "segid": 63,
  "ismine": true,
  "iswatchonly": false,
  "isscript": false,
  "pubkey": "039e1f9a06d9d41981d0cc1c380d0965e82250d436523e18b42832b1e41f037e00",
  "iscompressed": true,
  "account": "Example Address"
}
```

In the returned output, `039e1f9a06d9d41981d0cc1c380d0965e82250d436523e18b42832b1e41f037e00` is your pubkey!

### Using A Pubkey

There are 2 ways to tell a wallet to use a pubkey.

[Setpubkey Command](Setpubkey-Command) or [Start Wallet with Pubkey](Start-Wallet-With-Pubkey)

##### Setpubkey Command

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `setpubkey YourPubkey`.

Example `setpubkey 039e1f9a06d9d41981d0cc1c380d0965e82250d436523e18b42832b1e41f037e00`

##### Start Wallet With Pubkey

1. Start the wallet with the `-pubkey=YourPubkey` command line option.

Example for Spacecoind: `./spacecoind -pubkey=039e1f9a06d9d41981d0cc1c380d0965e82250d436523e18b42832b1e41f037e00`

Example for Spacecoin-QT: `./spacecoin-qt -pubkey=039e1f9a06d9d41981d0cc1c380d0965e82250d436523e18b42832b1e41f037e00`

Example for Spacecoin-QT (windows): Create a shortcut of `spacecoin-qt.exe`. Right click on the shortcut and select Properties. Then add your pubkey to the end of the target field. `spacecoin-qt.exe -pubkey=039e1f9a06d9d41981d0cc1c380d0965e82250d436523e18b42832b1e41f037e00`
