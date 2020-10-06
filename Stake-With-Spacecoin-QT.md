# Stake With Spacecoin-QT

This guide will teach you how to start staking with Spacecoin-QT.

## Table of Contents

- [Please Note](#Please-Note)
- [Option 1](#Option-1)
- [Option 2](#Option-2)

### Please Note

With Spacecoin-QT the commands will need to be entered in the console. This is accessible at `Help -> Debug Window -> Console`.

For staking to work the wallet needs to be unlocked. If you encrypted your wallet you will need to unlock it with the command `walletpassphrase`.

Example: `walletpassphrase "your passphrase" 3600`

`3600` is the time in seconds the wallet will stay unlocked before locking again. This means you will need to unlock it again after this amount of time to continue staking.

### Option 1

1. Enter your `spacecoin-qt` folder.

2. Run `spacecoin-qt` and let the blockchain fully sync.

3. Send coins to your wallet if you do not have any in your wallet already.

4. Click on the `stake` file in your `spacecoin-qt` folder.

It will open and command prompt/terminal screen and then close.

You can check to make sure you are staking with the [Check If You Are Staking](https://github.com/SpaceWorksCo/guides/blob/master/Check-If-You-Are-Staking.md) guide.

### Option 2

1. Enter your `spacecoin-qt` folder.

2. Run `spacecoin-qt` and let the blockchain fully sync.

3. Send coins to your wallet if you do not have any in your wallet already.

4. Navigate to the `Console`.

5. Enter the command `setgenerate true 0`.

You can check to make sure you are staking with the [Check If You Are Staking](https://github.com/SpaceWorksCo/guides/blob/master/Check-If-You-Are-Staking.md) guide.
