# Run Spacecoin

This guide will teach you how to run spacecoin.

## Table of Contents

  - [Please Note](#Please-Note)
  - [Instructions](#Instructions)

### Please Note

It is assumed you have already [built spacecoin from source](Build-Spacecoin-From-Source.md).

The instructions use the program `screen` to keep the process running in the background.

### Instructions

Open a Terminal.

Navigate to the spacecoin/src directory:

`cd spacecoin/src`

Start a new screen for spacecoin:

`screen -S spacecoin`

Start spacecoin:

`./spacecoind`

Here you will see all of the output from spacecoind as it starts up and syncs.

Use `Ctrl + A` + `Ctrl + D` to exit the screen. (you can return to it at any point with `screen -r spacecoin`)

You can now use `spacecoin-cli` to interact with the daemon.
