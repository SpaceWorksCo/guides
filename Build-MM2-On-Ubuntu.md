# Build MM2 On Ubuntu

This guide will teach you how to build mm2 on Ubuntu.

## Table of Contents

- [Please Note](#Please-Note)
- [Instructions](#Instructions)

### Please Note

AtomicDEX-API produces a binary called `mm2`.

If you'd like to simplify this process, [use MMTools](Use-MMTools.md).

### Instructions

1. Open the Terminal or SSH into your server.

2. Update the system:

    `sudo apt-get update`

3. Install dependencies:

    `sudo apt-get install build-essential cmake libtool autotools-dev automake autoconf pkg-config libssl-dev clang libclang-dev`

4. Install Rustup:

    `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`

5. Install specific rustup nightly:

    `rustup install nightly-2020-10-25`

6. Make it the default:

    `rustup default nightly-2020-10-25`

7. Add rustfmt-preview:

    `rustup component add rustfmt-preview`

8. Clone AtomicDEX-API:

    `git clone https://github.com/KomodoPlatform/atomicDEX-API`

9. Enter the AtomicDEX-API directory:

    `cd atomicDEX-API`

10. Build AtomicDEX-API:

    `cargo build --features native --release`

You have now built mm2.

The mm2 binary will be located : `target/release`

You can now [setup mm2](Setup-MM2.md).
