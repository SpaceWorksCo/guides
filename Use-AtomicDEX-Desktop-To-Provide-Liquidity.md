# Use AtomicDEX-Desktop To Provide Liquidity

This guide will teach you how to use AtomicDEX-Desktop to create liquidity for a desired pair.

## Table of Contents

- [Please Note](#Please-Note)
- [Instructions](#Instructions)

### Please Note

AtomicDEX is a multicoin lite wallet, as well as a decentralized exchange that utilizes atomic swaps.

For legal reasons, the DEX function in the official version is unavailable to users in `USA, Canada, Hong Kong, Israel, Singapore, Sudan, Austria, and Iran`. There is a version that removes this geoblock that is maintained at [github.com/marmarachain/atomicdex-desktop](https://github.com/marmarachain/atomicdex-desktop/releases).

It is assumed that you have already [setup AtomicDEX-Desktop](Setup-AtomicDEX-Desktop.md) and have coins in your [wallet](Use-AtomicDEX-Desktop-As-A-Wallet.md) to trade.

For your orders to remain in the orderbook and available to others, AtomicDEX must remain running.

### Instructions

1. Open AtomicDEX-Desktop and login to your wallet.

    ![Login](/images/atomicdex_login.png)

2. Click on the `Wallet` page from the menu on the left side.

    ![Wallet](/images/atomicdex_wallet.png)

3. Click on the `+` button to open the coin list.

    ![Add Coin](/images/atomicdex_add_coin.png)

4. Select the coins you would like to trade and click `Enable`.

    ![Enable](/images/atomicdex_enable.png)

5. Click on the `DEX` page from the menu on the left side.

    ![DEX](/images/atomicdex_dex.png)

6. Select the 2 coins you would like to provide liquidity for.

  All pairs are possible and need liquidity.
`SPACE/BTC`, `SPACE/KMD`, `KMD/BTC`, `KMD/ZEC`, `DOGE/DASH` etc.

    ![Coins](/images/atomicdex_coins.png)

7. Input your `Price` and `Volume` values on the right side.

    In the screenshot, `Price` is the price in KMD for 1 SPACE and `Volume` is the amount of SPACE to sell.

    ![Order](/images/atomicdex_order2.png)

8. Click on `Start Swap` to place your order.

    ![Swap](/images/atomicdex_swap2.png)

Your order is now providing liquidity on AtomicDEX!

Leave AtomicDEX running to keep your orders in the orderbook.

You can continue to place more orders.

Check on your orders by clicking on the `Orders` tab at the top of the DEX page.
