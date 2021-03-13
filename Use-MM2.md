# Use MM2

This guide will teach you how to use mm2.

## Table of Contents

  - [Please Note](#Please-Note)
  - [Instructions](#Instructions)

### Please Note

It is assumed you already have already [setup](Setup-MM2.md) and are [running](Run-MM2.md) mm2.

You can interact with `mm2` using any of the available API methods: [docs.komodoplatform.com/basic-docs/atomicdex/atomicdex-api](https://docs.komodoplatform.com/basic-docs/atomicdex/atomicdex-api.html)

Each curl command requires replacing certain information with the coin/information you need.

If you'd like to simplify this process, [use MMTools](Use-MMTools.md).

### Instructions

1. Open a Terminal.

2. Start the coins you'd like to use:

    In this case, we'll use `electrum` rather than `enable`. Enable requires a native coin daemon to be running and importing the private key for your seed into the daemon's wallet.

    `curl --url "http://127.0.0.1:7783" --data "{\"userpass\":\"$userpass\",\"method\":\"electrum\",\"coin\":\"HELLOWORLD\",\"servers\":[{\"url\":\"localhost:20025\",\"protocol\":\"SSL\",\"disable_cert_verification\":true},{\"url\":\"localhost:10025\"}]}"`

    Replace `HELLOWORLD` with the coin symbol for the coin you'd like to start. Ex: SPACE, KMD, or BTC

    Replace both url's with the electrum servers ip addresses/domain names for the coin you're starting. Electrum server information can be found in the [KomodoPlatform/Coins](https://github.com/KomodoPlatform/Coins) repository.

    You must start more than 1 coin to be able to do any trades.

3. Send coins to your AtomicDEX address. Each coin's address is shown in the output after starting it.

4. View the orderbook by running:

    `curl --url "http://127.0.0.1:7783" --data "{\"userpass\":\"$userpass\",\"method\":\"orderbook\",\"base\":\"HELLO\",\"rel\":\"WORLD\"}"`

    Replace `HELLO` and `WORLD` with the coins you'd like to see orders for.

    The coins must be already running.

5. Start trading with the following commands, replacing the placeholders with the coins/prices/volume you wish:

    Buy:

    `curl --url "http://127.0.0.1:7783" --data "{\"userpass\":\"$userpass\",\"method\":\"buy\",\"base\":\"HELLO\",\"rel\":\"WORLD\",\"volume\":"\"1\"",\"price\":"\"1\""}"`

    Sell:

    `curl --url "http://127.0.0.1:7783" --data "{\"userpass\":\"$userpass\",\"method\":\"sell\",\"base\":\"HELLO\",\"rel\":\"WORLD\",\"volume\":"\"1\"",\"price\":"\"1\""}"`

    Setprice:

    `curl --url "http://127.0.0.1:7783" --data "{\"userpass\":\"$userpass\",\"method\":\"setprice\",\"base\":\"BASE\",\"rel\":\"REL\",\"price\":\"0.9\",\"volume\":\"1\"}"`

Refer the [AtomicDEX docs](https://developers.komodoplatform.com/basic-docs/atomicdex/atomicdex-api.html) for more methods. They are all used in the same fashion.
