# Interact with Spacecoin

This guide will teach you how to interact with the spacecoin daemon.

## Table of Contents

  - [Please Note](#Please-Note)
  - [Instructions](#Instructions)

### Please Note

It is assumed you have already have spacecoin running.

If it is not, you can:
  - [Build Spacecoin From Source](Build-Spacecoin-From-Source.md) / [Run Spacecoin](Run-Spacecoin.md)
  - [Run Spacecoin with Komodo](Run-Spacecoin-With-Komodo.md)
  - [Run Spacecoin with Docker](Run-Spacecoin-With-Docker.md).

### Instructions

1. Open a Terminal.

2. Navigate to the spacecoin/src directory:

    `cd spacecoin/src`

Here you will find `spacecoin-cli`, which you can use to enter commands.

To get info about Spacecoin:

`./spacecoin-cli getinfo`

To get a Spacecoin address:

`./spacecoin-cli getnewaddress`

To get a Spacecoin private address:

`./spacecoin-cli z_getnewaddress`

To enable staking:

`./spacecoin-cli setgenerate true 0`

To see all of the commands available use `./spacecoin-cli help` or visit the [Spacecoin RPC Docs](https://spacecoin-rpc.spaceworks.co).
