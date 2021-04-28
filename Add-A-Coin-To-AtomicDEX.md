# Add A Coin To AtomicDEX

This guide will teach you how to get a new coin added to AtomicDEX.

## Table of Contents

- [Please Note](#please-note)
- [Background Information](#background-information)
- [Instructions](#instructions)

### Please Note

AtomicDEX supports UTXO coins, Komodo Smartchains, and ERC-20/BEP-20/QRC-20 tokens.

Coins with non-standard RPC would require changes to AtomicDEX-API.

To complete the following it will require experience with github and CLI as well as 2 machines to complete the test swap.

### Background Information

Adding a coin or token to AtomicDEX is comprised of multiple parts.

  1. [Coins File](#coins-file)
  2. [AtomicDEX-Desktop](#atomicdex-desktop)
  3. [AtomicDEX-Mobile](#atomicdex-mobile)

### Instructions

#### Coins File

1. Read the requirements for your coin type:

    [UTXO coin](https://github.com/komodoplatform/coins#example-1-utxo-coin), [smartchain](https://github.com/komodoplatform/coins#example-2-kmd-smartchain), [ERC-20](https://github.com/komodoplatform/coins#example-3-erc20-token), [BEP-20](https://github.com/komodoplatform/coins#example-4-bep20-token), [QRC-20](https://github.com/komodoplatform/coins#example-5-qrc20-token).

2. Clone [github.com/komodoplatform/coins](https://github.com/komodoplatform/coins)

3. Add the coin or token to the `coins` file.

4. Add a 82x82 png logo in `/icons` named `ticker.png`.

5. Add an explorer file in `/explorers` named `TICKER` with the coin's explorer.

6. Add an electrum file in `/electrums` named `TICKER` with the coin's electrum servers.

7. Install and setup [AtomicDEX-API](https://github.com/komodoplatform/atomicDEX-API).

    The easiest solution is to [Use MMTools](Use-MMTools.md).

8. Perform a swap with the coin or token with another coin.

9. Add a swap file in `/swaps` with explorer links to the TXIDs.

10. Submit a pull request with your changes.

#### AtomicDEX-Desktop

1. Clone [github.com/komodoplatform/atomicDEX-Desktop](https://github.com/komodoplatform/atomicDEX-Desktop).

2. Add your coin to the coins file at `/assets/config/<version>-coins.json`.

3. Add a 82x82 png logo in `/atomic_defi_design/assets/images/coins` named `ticker.png`.

4. Add the logo file path in the `qml.qrc` file.

5. Submit a pull request with your changes.

#### AtomicDEX-Mobile

1. Contact the Komodo Team for arrangements. This requires a listing fee.
