# Stake With Spacecoind

This guide will teach you how to stake with Spacecoind.

## Table of Contents

- [Please Note](#Please-Note)
- [Instructions](#Instructions)

### Please Note

With Spacecoind the commands will need to be used with `spacecoin-cli`.

For staking to work the wallet needs to be unlocked. If you encrypted your wallet you will need to unlock it with the command `walletpassphrase`.

Example: `spacecoin-cli walletpassphrase "your passphrase" 3600`

`3600` is the time in seconds the wallet will stay unlocked before locking again. This means you will need to unlock it again after this specified amount of time to continue staking.

The wallet must stay open and online to be able to stake.

### Instructions

1. Run `spacecoind` and let the blockchain fully sync.

2. Send coins to your wallet if you do not have any in your wallet already.

3. Run `spacecoin-cli setgenerate true 0`.

You can check to make sure you are staking with `spacecoin-cli getgenerate`. [(Guide)](Check-If-You-Are-Staking.md)
