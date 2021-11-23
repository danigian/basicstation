# LoRa Basics™ Station for USB SX1302 board

[Basic Station](https://doc.sm.tc/station) is a LoRaWAN Gateway implementation.
This fork of the official Basic Station repository is allowing usage of USB SX1302 board.

## Prerequisites

Building the Station binary from source, requires

* gcc (C11 with GNU extensions)
* GNU make
* git
* bash

## Build

#### Step 1: Cloning the Station Repository

``` sourceCode
git clone https://github.com/danigian/basicstation.git
git checkout corecell
```

#### Step 2: Compiling the Station Binary

``` sourceCode
cd basicstation
sudo make platform=corecell variant=std
```

The build process consists of the following steps:

*  Fetch and build dependencies, namely [mbedTLS](https://github.com/ARMmbed/mbedtls), [sx1302_hal v2.1.0](https://github.com/Lora-net/sx1302_hal)
*  Setup build environment within subdirectory `build-$platform-$variant/`
*  Compile station source files into executable `build-$platform-$variant/bin/station`

#### Step 3: Running the Example Configuration on a Raspberry Pi

``` sourceCode
cd examples/usbcorecell
vi station.conf #for editing RADIODEV
vi tc.uri #for editing lns endpoint uri
../../build-corecell-std/bin/station
```
