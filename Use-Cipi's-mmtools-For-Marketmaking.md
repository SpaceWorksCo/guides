# Use Cipi's mmtools For Marketmaking

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

It is assumed you already have already [built](Build-MM2-On-Ubuntu.md) or [downloaded](Download-MM2-Binary.md) mm2, [Setup MM2](Setup-MM2.md) and are [running mm2](Run-MM2.md).

The coins you wish to use should be enabled in mm2. (Guide coming soon)

### Instructions

1. Open the Terminal or SSH into your server.

2. Update the system:

    `sudo apt-get update`

3. Install dependencies:

    `sudo apt-get install jq libdatetime-perl libdatetime-format-strptime-perl libjson-perl libjson-rpc-perl libfile-slurp-perl liblwp-protocol-https-perl`

4. Clone the mmtools repository:

    `cd && git clone https://github.com/cipig/mmtools`

5. Determine the base coin/coins you'll use. (BTC, KMD, BCH, LTC, DOGE) In this case we'll be using Komodo.

6. Open the config file for editing. Replace KMD with whatever base coin you choose.

    `nano mpm/mpm.conf.dex.KMD`

7. Set the `bidmargin` and `askmargin` for each coin to whatever margin you'd like. The margin number is the % below (bid) or above (ask) market price.

8. Use `Ctrl` + `x` to exit nano.

9. Press `y` to save your changes.

10. Start mpm with CoinGecko prices. Replace KMD with whatever base coin you choose.

    `stdbuf -oL nohup ~/mpm/mpm.sh.dex_gecko KMD > /tmp/mpm.log.dex.kmd &`

MPM is now running and placing orders for the coins in the config that are enabled in mm2.

To see mpm output do: `tail -f /tmp/mpm.log.dex.kmd`
