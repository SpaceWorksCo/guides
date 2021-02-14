# Build AtomicDEX-API for Pi4

This guide will teach you how to build AtomicDEX-API for Pi4.

## Table of Contents

- [Please Note](#Please-Note)
- [Instructions](#Instructions)

### Please Note



### Instructions

1. Open Terminal.

2. Install Rustup by entering: `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`

3. Install the Standard library for Pi4: `rustup target add armv7-unknown-linux-gnueabihf`

3. Install latest nightly toolchain: `rustup install nightly`

4. Make it the default: `rustup default nightly`

5. Install cross: `cargo install cross`

6. Build the Docker image for cross compilation: `docker build -f Dockerfile.armv7-unknown-linux-gnueabihf -t mm2-armv7-unknown-linux-gnueabihf`

7. Build AtomicDEX-API: `cross build --features native --target armv7-unknown-linux-gnueabihf`

8. The mm2 binary will be located at: `target/armv7-unknown-linux-gnueabihf/debug/mm2`

You now have mm2 built. You can copy it to your Pi, run it, and start trading.
