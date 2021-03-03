# Run Spacecoin With Docker

This guide will teach you how to run spacecoin with docker.

## Table of Contents

  - [Please Note](#Please-Note)
  - [Instructions](#Instructions)

### Please Note

It is assumed you have already docker installed on your machine.

### Instructions

1. Open a Terminal.

2. Build Spacecoin:

    `docker build -t spaceworksco/spacecoin . --file Dockerfile`

3. Run Spacecoin:

    `docker run -it -v ~/.SPACE:/root/.komodo/SPACE spaceworksco/spacecoin`

Spacecoin is now running.
