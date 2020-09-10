# Check If You Are Staking

This guide will teach you how to check to see if you are staking.

It is assumed you are already running Spacecoin-QT. If not download it [here](https://spaceworks.co/spacecoin/wallets#spacecoin-qt).

## Table of Contents

- [Instructions](#Instructions)
- [Please Note](#Please-Note)

### Instructions

1. Select `Help` in the top menu bar.

2. Select `Debug window` from the menu.

3. Select the `Console` tab.

4. Enter the command `getgenerate`.

If you are staking you will see:
```
{
  "staking": true,
  "generate": false,
  "numthreads": 0
}
```

If you see `"staking": false,` then you are not mining. Enable staking by entering the command `setgenerate true 0` in the console.


### Please Note

For staking to work, Spacecoin-QT needs to be unlocked. If you encrypted your wallet you will need to unlock it with the command `walletpassphrase`.

Example: `walletpassphrase "your passphrase" 3600`

`3600` is the time in seconds the wallet will stay unlocked before locking again. This means you will need to keep unlocking it to continue staking.
