# Import A Private Key

This guide will teach you how to import a private key.

This is available with [Spacecoind](https://github.com/spaceworksco/spacecoin) or [Spacecoin-QT](https://spaceworks.co/spacecoin/wallets#spacecoin-qt).

## Table of Contents

- [Please Note](#Please-Note)
- [Instructions](#Instructions)

### Please Note

With Spacecoin-QT the commands will need to be entered in the console. This is accessible at `Help -> Debug Window -> Console`.

Be very careful with the private key. If anyone gains access to it, they gain access to the coins in the associated address.

Each address in your wallet has its own private key.

### Instructions

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `importprivkey yourPrivKey`.

It will return the address of the private key.
