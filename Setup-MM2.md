# Setup MM2

This guide will teach you how to setup mm2.

## Table of Contents

  - [Please Note](#Please-Note)
  - [Instructions](#Instructions)
      - [Coins File](#Coins-File)
      - [Userpass](#Userpass)
      - [Seed](#Seed)

### Please Note

It is assumed you already built or downloaded `mm2` on your system.

### Instructions

1. Open a Terminal.

2. Navigate to the directory with mm2.

    In this case, we'll assume you followed the [Build MM2 on Ubuntu](Build-MM2-On-Ubuntu.md) guide:

    `cd atomicDEX-API/target/release`

#### Coins File

1. Download the coins file:

    `wget https://raw.githubusercontent.com/KomodoPlatform/coins/master/coins`

#### Userpass

When setting up a userpass, make it something safe so others can't access your mm2.

1. Use nano to create the userpass file:

    `nano userpass`

2. Enter the following, replacing `<yourUserpass>` with a userpass you choose yourself.

    `export userpass="<yourUserpass>"`

3. Use `Ctrl` + `X` to exit.

4. Press `y` to save the file.

5. Press enter to keep the name the same.

#### Seed

Create a seed for your AtomicDEX account.

Make sure to keep it somewhere safe and don't share with anyone else. The seed holds access to your coins.

You can use `AtomicDEX-Desktop` to get a seed or use a tool such as [dogeseed.com](dogeseed.com).

------

You are now ready to [Run MM2](Run-MM2.md).
