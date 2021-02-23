# Run Spacecoin With Docker

This guide will teach you how to run spacecoin with docker.

## Table of Contents

  - [Please Note](#Please-Note)
  - [Instructions](#Instructions)

### Please Note

It is assumed you have already docker installed on your machine.

### Instructions

Open a Terminal.

Build Spacecoin:

`docker build -t spaceworksco/spacecoin . --file Dockerfile`

Run Spacecoin:

`docker run -it -v ~/.SPACE:/root/.komodo/SPACE spaceworksco/spacecoin`

Spacecoin is now running.
