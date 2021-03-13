# Run MM2

This guide will teach you how to run mm2.

## Table of Contents

  - [Please Note](#Please-Note)
  - [Instructions](#Instructions)

### Please Note

It is assumed you already have already [Setup MM2](Setup-MM2.md).

If you'd like to simplify this process, [use MMTools](Use-MMTools.md).

The instructions use the program `screen` to keep the process running in the background.

### Instructions

1. Open a Terminal.

2. Navigate to the directory with mm2.

    In this case, we'll assume you followed the [Build MM2 on Ubuntu](Build-MM2-On-Ubuntu.md) guide:

    `cd atomicDEX-API/target/release`

3. Source the userpass file:

    `source userpass`

4. Start a screen to run mm2 in:

    `screen -S mm2`

5. Start mm2 with the following command, replacing ``<yourSeed>`` with your seed:

    `./mm2 "{\"netid\":7777, \"userhome\":\"/${HOME#"/"}\", \"passphrase\":\"<yourSeed>\", \"rpc_password\":\"$userpass\"}" &`

6. Use `Ctrl + A` + `Ctrl + D` to exit the screen.

    You can return to it at any point with `screen -r mm2`.

You can now start [using MM2](Use-MM2.md).
