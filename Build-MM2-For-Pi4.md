# Build MM2 for Pi4 -- WIP

This guide will teach you how to build mm2 for Pi4.

## Table of Contents

- [Please Note](#Please-Note)
- [Instructions](#Instructions)

### Please Note

AtomicDEX-API produces a binary called `mm2`.

This guide is cross-compiling `mm2` binary on one machine, to allow for copying to pi4.

### Instructions

1. Open the Terminal.

2. Install Rustup:

    `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`

3. Install the Standard library for Pi4:

    `rustup target add armv7-unknown-linux-gnueabihf`

4. Install latest nightly toolchain:

    `rustup install nightly`

5. Make it the default:

    `rustup default nightly`

6. Install cross:

    `cargo install cross`

7. Build the Docker image for cross compilation:

    `docker build -f Dockerfile.armv7-unknown-linux-gnueabihf -t mm2-armv7-unknown-linux-gnueabihf`

8. Build mm2:

    `cross build --features native --target armv7-unknown-linux-gnueabihf --release`

You now have mm2 built.

The binary will be located at: `target/armv7-unknown-linux-gnueabihf/release/mm2`

You can copy it to your Pi and [setup mm2](Setup-MM2.md).
