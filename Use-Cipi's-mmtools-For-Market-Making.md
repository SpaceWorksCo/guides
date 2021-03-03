# Use Cipi's mmtools For Market Making

This guide will teach you how to use mmtools by cipi for marketmaking.

## Table of Contents

  - [Background Information](#Background-Information)
  - [Please Note](#Please-Note)
  - [Instructions](#Instructions)

### Background Information

mmtools connects to mm2 and places marketmaking orders based on prices from CoinGecko.

25% of the `24h_price_change` is added to the spread of the involved coins. So if `24h_price_change` is 10%, it will add 2.5% to both bid and ask. This is done to protect from prices that go crazy on illiquid coins. For big coins this may be too much, for small coins not enough, but you can set different spreads for different coins in the config.

If BTC or ETH/ERC20 is involved, it will set a `min_volume` for the order. Basically `get_trade_fee * 15`. 1/15 = 6% This is done because of the spread. With a 2% spread and 4% payed for fees you would not make money if your bid/ask was set at 3%.

### Please Note

This guide is intended for Ubuntu (Debian).

It is assumed you already have already [built](Build-MM2-On-Ubuntu.md) or [downloaded](Download-MM2-Binary.md), [setup](Setup-MM2.md), and are [running](Run-MM2.md) mm2.

The coins you wish to use should be enabled in mm2. (Guide coming soon)

### Instructions

1. Open the Terminal or SSH into your server.

    ![terminal](/images/mpm_1.png)

2. Update the system:

    `sudo apt-get update`

    ![update](/images/mpm_2.png)

3. Install dependencies:

    `sudo apt-get install jq libdatetime-perl libdatetime-format-strptime-perl libjson-perl libjson-rpc-perl libfile-slurp-perl liblwp-protocol-https-perl`

    ![dependencies](/images/mpm_3.png)

4. Clone the mmtools repository:

    `cd && git clone https://github.com/cipig/mmtools`

    ![clone](/images/mpm_4.png)

5. Enter the mmtools directory:

    `cd mmtools`

    ![enter](/images/mpm_5.png)

6. Determine the base coin you'll use. (BTC, KMD, BCH, LTC, DOGE) In this case we'll be using Komodo.

7. Open the config file for editing. Replace KMD with whatever base coin you choose.

    `nano mpm/mpm.conf.dex.KMD`

    ![edit](/images/mpm_7.png)

8. Set the `bidmargin` and `askmargin` for each coin to whatever margin you'd like. The margin number is the % below (bid) or above (ask) market price.

    ![set](/images/mpm_8.png)

9. Use `Ctrl` + `x` to exit nano.

    ![exit](/images/mpm_9.png)

10. Press `y` to save your changes.

    ![save](/images/mpm_10.png)

11. Press `enter` to keep the name of the file the same.

    ![enter](/images/mpm_11.png)

12. Start mpm with CoinGecko prices. Replace KMD with whatever base coin you choose.

    `stdbuf -oL nohup ~/mmtools/mpm/mpm.sh.dex_gecko KMD > /tmp/mpm.log.dex.kmd &`

    ![start](/images/mpm_12.png)

MPM is now running and placing orders for the coins you have enabled in mm2.

To see mpm output do: `tail -f /tmp/mpm.log.dex.kmd`
