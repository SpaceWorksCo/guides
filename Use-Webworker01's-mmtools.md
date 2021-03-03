# Use Webworker01's mmtools

This guide will teach you how to use mmtools by Webworker01.

## Table of Contents

  - [Background Information](#Background-Information)
  - [Please Note](#Please-Note)
  - [Instructions](#Instructions)

### Background Information

mmtools provides commands for building, setting up, running, and interacting with mm2.

### Please Note

This guide is intended for Ubuntu (Debian).

### Instructions

1. Open the Terminal or SSH into your server.

2. Clone the mmtools repository:

    `cd && git clone https://github.com/webworker01/mmtools`

3. Enter the mmtools directory:

    `cd mmtools`

4. Build and Setup mm2:

    `./init`

    Init will help create a config file and ask if you want to generate a random wallet passphrase and userpass. If you do not want to use this, cancel the init script with `Ctrl` + `c` and first set up your own and run init again.

    To setup your own config file do:

    ```
    #edit the config file with your wallet passphrase and rpc password
    cp config.example config
    nano config
    ```

5. Start a screen to run mm2 in:

    `screen -S mm2`

6. Start mm2:

    `./start`

7. Use `Ctrl + A` + `Ctrl + D` to exit the screen.

    You can return to it at any point with `screen -r mm2`.

8. Start the coins you'd like to use:

    `./electrum SPACE` - to start Spacecoin.

    `./electrum KMD` - to start Komodo.

9. View the orderbook.

    `./orderbook SPACE KMD` - to show the SPACE/KMD orderbook.

10. Use any of the available commands to interact with mm2. You can see them all with:

    `ls -al`

    Running any of the commands will output the correct syntax for use and the other required data it needs.

mm2 is now built, setup, running, and ready for trading!
