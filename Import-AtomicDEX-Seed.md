# Import AtomicDEX Seed

This guide will teach you how to import an address generated with AtomicDEX seed.

This is available with [Spacecoind](https://github.com/spaceworksco/spacecoin) or [Spacecoin-QT](https://spaceworks.co/spacecoin/wallets#spacecoin-qt).

## Table of Contents

- [Please Note](#Please-Note)
- [Instructions](#Instructions)

### Please Note

With Spacecoin-QT the commands will need to be entered in the console. This is accessible at `Help -> Debug Window -> Console`.

### Instructions

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `convertpassphrase "your long and secure seed generated with atomicDEX"`.

The output will display the Address and Private Keys associated with your seed.

Ex: ```{
  "agamapassphrase": "your long and secure seed generated with atomicDEX",
  "address": "RTCqmfQr3e5csyPpRNnLZLbzMcHmcngiSb",
  "pubkey": "03b22eeb6cf6408607fddd770abb2ba3bbb64b112a3c626a8e8ac5fb090287c710",
  "privkey": "c88ec5711d611f4c2b53597352d60e58fa77e2ca0580386f71b7867147a5d250",
  "wif": "UvjQFXKynQ2LSMtXeWnHdE79mtXZ7nyGqKwStWxygSyg9EecvRLm"
}```

3. Enter the command `importprivkey wifFromConvertPassphraseOutput`

Ex: `importprivkey UvjQFXKynQ2LSMtXeWnHdE79mtXZ7nyGqKwStWxygSyg9EecvRLm`

This will add the associated address to the wallet and rescan to look for transactions.
