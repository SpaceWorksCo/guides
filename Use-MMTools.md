# Use MMTools

This guide will teach you how to use [mmtools](https://github.com/webworker01/mmtools) by webworker01 for using atomicDEX-API.

## Table of Contents

  - [Background Information](#Background-Information)
  - [Please Note](#Please-Note)
  - [Instructions](#Instructions)
  - [Extra Information](#Extra Information)

### Background Information

mmtools has commands for building, setting up, running, and interacting with mm2.

If you already setup mm2 manually, you can specify its directory and rpc password in the `config` file.

During setup you will be asked if you'd like to install mpm by cipi. mpm is a market making tool that places orders based on prices from CoinGecko and margins you set.

### Please Note

This guide is intended for Ubuntu.

### Instructions

1. Open the Terminal or SSH into your server.

    ![Terminal](/images/mmtools_1.png)

2. Update the system:

    `sudo apt-get update`

    ![Update](/images/mmtools_2.png)

3. Install git, curl, and screen:

    `sudo apt-get install -y git curl screen`

    ![Install](/images/mmtools_3.png)

4. Clone the mmtools repository:

    `cd && git clone https://github.com/webworker01/mmtools`

    ![Clone](/images/mmtools_4.png)

5. Enter the mmtools directory:

    `cd mmtools`

    ![Enter](/images/mmtools_5.png)

6. Build and Setup mm2:

    Use Init to do everything for you.

    `./init`

    ![Init](/images/mmtools_6.png)

    Enter `y`for yes to each of the questions.

7. Start a screen to run mm2 in:

    `screen -S mm2`

    ![Screen](/images/mmtools_7.png)

8. Start mm2:

    `./start`

    ![Start](/images/mmtools_8.png)

9. Use `Ctrl + A` + `Ctrl + D` to exit the screen.

    ![Exit](/images/mmtools_9.png)

    You can return to it at any point with `screen -r mm2`.

10. Start the coins you'd like to use:

    `./electrum SPACE` - to start Spacecoin.

    `./electrum KMD` - to start Komodo.

    ![Electrum](/images/mmtools_10.png)

11. View the orderbook.

    `./orderbook SPACE KMD` - to show the SPACE/KMD orderbook.

    ![Orderbook](/images/mmtools_11.png)

12. Use any of the available commands to interact with mm2.

    `./buy`, `./sell`, `./setprice`, `./my_balance`, and more.

    You can see them all with:

    `ls -al`

    ![All](/images/mmtools_12.png)

    Running any of the commands will output the correct syntax for use and the other required info it expects.

**MM2 is now built, setup, running, and ready for trading!**

At this point you could [Use MPM](Use-MPM.md) for market making with MM2.


#### Extra Information

**Setting Up your own config file:**

*This is only necessary if you answered no to the config question or want to modify your setup.*

Copy the example config file to a real config file:

`cp config.example config`

Open the config file:

`nano config`

Input your desired information and then exit:

`ctrl + x` to close nano. `y` to say yes to changes. Press `enter` to confirm the name.
