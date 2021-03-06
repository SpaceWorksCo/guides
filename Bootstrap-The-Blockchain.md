# Bootstrap The Blockchain

This guide will teach you how to bootstrap the SPACE blockchain for a faster sync.

This is intended for [Spacecoind](https://github.com/spaceworksco/spacecoin) or [Spacecoin-QT](https://spacecoin.network/#wallets).

## Table of Contents

- [Please Note](#Please-Note)
- [Instructions](#Instructions)

### Please Note

If Spacecoind or Spacecoin-QT is already running, stop it before continuing.

### Instructions

1. Download the SPACE blockchain bootstrap from [Dexstats.info](https://dexstats.info/bootstrap.php). [Direct Link](https://eu.bootstrap.dexstats.info/SPACE-bootstrap.tar.gz)

2. Extract `SPACE-bootstrap.tar.gz`.

3. Enter the extracted folder and copy the `blocks` and `chainstate` folders.

4. Navigate to your SPACE [data directory](Find-Data-Directory.md).

5. Paste the folders in the data directory, replacing the existing `blocks` and `chainstate` folders.

6. Start [Spacecoind](https://github.com/spaceworksco/spacecoin) or [Spacecoin-QT](https://spacecoin.network/#wallets).

Your SPACE daemon should now finish syncing very quickly.

If you found the bootstrap helpful, please consider donating to Dexstats at `RQFwNuhJ5HP1QbfU2wLj8ZUse43LSKrzei`.
