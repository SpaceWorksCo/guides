# Use MPM

This guide will teach you how to use [mpm](https://github.com/cipig/mmtools) by cipi for market making on atomicDEX.

## Table of Contents

  - [Background Information](#Background-Information)
  - [Please Note](#Please-Note)
  - [Instructions](#Instructions)
      - [MMTools](#MMTools)
      - [Standalone](#Standalone)

### Background Information

mpm connects to mm2 and places market making orders based on prices from CoinGecko and margins you set.

25% of the `24h_price_change` is added to the spread of the involved coins. So if `24h_price_change` is 10%, it will add 2.5% to both bid and ask. This is done to protect from prices that go crazy on illiquid coins. For big coins this may be too much, for small coins not enough, but you can set different spreads for different coins in the config.

If BTC or ETH/ERC20 is involved, it will set a `min_volume` for the order. Basically `get_trade_fee * 15`. 1/15 = 6% This is done because of the spread. With a 2% spread and 4% payed for fees you would not make money if your bid/ask was set at 3%.

### Please Note

This guide is intended for Ubuntu.

It is assumed you are either:
    - [Using mmtools](Use-MMTools.md)
    - Have [built](Build-MM2-On-Ubuntu.md)/[downloaded](Download-MM2-Binary.md), [setup](Setup-MM2.md), and are [running](Run-MM2.md) mm2 with [coins started](Use-MM2.md) that you'd like to trade.

You will need to decide what base coin you'd like to use.

  - BTC, KMD, BCH, LTC, and DOGE are available.
  - For example: SPACE/KMD, CHIPS/KMD, WSB/KMD, VRSC/KMD

### Instructions

You can choose to use MPM with MMTools (easiest solution) or in a Standalone setup running MM2 and MPM manually.

#### MMTools

0. [Use MMTools to install MPM.](Use-MMTools.md) Start MM2, and enable coins.

1. Enter the mmtools directory:

    `cd && cd mmtools`

2. Configure the margins for coins you'd like mpm to place orders with:

    Remove coins you don't wish to trade or you'll see errors in MPM TV.

    Replace KMD with whatever base coin you choose.

    `./mpm_config KMD`

3. Use `Ctrl` + `x` to exit the config file.

4. Press `y` to save your changes.

5. Press `enter` to keep the name of the file the same.

6. Start MPM:

    `./mpm_start KMD`

**MPM is now running and placing orders**

To see MPM output run:

`./mpm_tv`

To stop MPM run:

`./mpm_stop`


#### Standalone

1. Open the Terminal or SSH into your server.

    ![terminal](/images/mpm_1.png)

2. Update the system:

    `sudo apt-get update`

    ![update](/images/mpm_2.png)

3. Install dependencies:

    `sudo apt-get install git jq libdatetime-perl libdatetime-format-strptime-perl libjson-perl libjson-rpc-perl libfile-slurp-perl liblwp-protocol-https-perl`

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

12. Start mpm with CoinGecko prices. Replace `KMD` and `komodo` with whatever base coin you choose.

    `stdbuf -oL nohup ~/mmtools/mpm/mpm.sh.dex_gecko KMD komodo > /tmp/mpm.log.dex.kmd &`

    ![start](/images/mpm_12.png)

MPM is now running and placing orders for the coins you have enabled in mm2.

To see mpm output do: `tail -f /tmp/mpm.log.dex.kmd`
