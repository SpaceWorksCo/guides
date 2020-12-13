# Check If You Are Staking

This guide will teach you how to check to see if you are staking.

Staking is available with [Spacecoind](https://github.com/spaceworksco/spacecoin) or [Spacecoin-QT](https://spaceworks.co/spacecoin/wallets#spacecoin-qt).

## Table of Contents

- [Please Note](#Please-Note)
- [Instructions](#Instructions)

### Please Note

With Spacecoin-QT the commands will need to be entered in the console. This is accessible at `Help -> Debug Window -> Console`.

For staking to work the wallet needs to be unlocked. If you encrypted your wallet you will need to unlock it with the command `walletpassphrase`.

Example: `walletpassphrase "your passphrase" 3600`

`3600` is the time in seconds the wallet will stay unlocked before locking again. This means you will need to unlock it again after this amount of time to continue staking.

### Instructions

1. Navigate to `spacecoin-cli` or `Console` depending on your wallet.

2. Enter the command `getgenerate`.

It will return:
```
{
  "staking": true,
  "generate": false,
  "numthreads": 0
}
```

If you see `"staking": true,` then you are staking!

If you see `"staking": false,` then you are not staking. Enable staking by entering the command `setgenerate true 0`.
