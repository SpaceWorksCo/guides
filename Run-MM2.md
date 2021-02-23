# Run MM2

This guide will teach you how to run mm2.

## Table of Contents

  - [Please Note](#Please-Note)
  - [Instructions](#Instructions)
      - [Coins File](#Coins-File)
      - [Userpass](#Userpass)
      - [Seed](#Seed)
      - [Start](#Start)

### Please Note

It is assumed you already have already [Setup MM2](Setup-MM2.md).

The instructions use the program `screen` to keep the process running in the background.

### Instructions

Open a Terminal.

Navigate to the directory with mm2. In this case, we'll assume you followed the [Build MM2 on Ubuntu](Build-MM2-On-Ubuntu.md) guide:

`cd atomicDEX-API/target/release`

Source the userpass file:

`source userpass`

Start a screen to run mm2 in:

`screen -S mm2`

Start mm2 with the following command, replacing ``<yourSeed>`` with your seed:

`./mm2 "{\"netid\":7777, \"userhome\":\"/${HOME#"/"}\", \"passphrase\":\"<yourSeed>\", \"rpc_password\":\"$userpass\"}" &`

Use `Ctrl + A` + `Ctrl + D` to exit the screen. (you can return to it at any point with `screen -r mm2`)

You can now to interact with `mm2` with any of the available methods: [docs.komodoplatform.com/basic-docs/atomicdex/atomicdex-api](https://docs.komodoplatform.com/basic-docs/atomicdex/atomicdex-api.html)
