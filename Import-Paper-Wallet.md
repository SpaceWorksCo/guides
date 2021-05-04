# Import Paper Wallet

This guide will teach you how to import a paper wallet to spend funds.

This is available with [Spacecoind](https://github.com/spaceworksco/spacecoin) or [Spacecoin-QT](https://spacecoin.network/#wallets).

## Table of Contents

- [Please Note](#Please-Note)
- [Instructions](#Instructions)

### Please Note

With Spacecoin-QT the commands will need to be entered in the console. This is accessible at `Help -> Debug Window -> Console`.

Once a paper wallet is imported into Spacecoind or Spacecoin-QT, best practice is to not use the paper wallet again.

### Instructions

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `importprivkey YourPaperWalletPrivateKey`.

    The wallet will start a rescan. This could take some time.

    When complete the output will show the address imported.
