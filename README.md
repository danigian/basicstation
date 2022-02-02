# LoRa Basics™ Station for USB-FTDI mPCIe RAK833 board

[Basic Station](https://doc.sm.tc/station) is a LoRaWAN Gateway implementation.
This fork of the official Basic Station (v2.0.6) repository is allowing usage of USB-FTDI mPCIe RAK833 board. 

## Prerequisites

Building the Station binary from source, requires

* gcc (C11 with GNU extensions)
* GNU make
* git
* bash
* libftdi-dev

## Build

#### Step 1: Cloning the Station Repository

``` sourceCode
git clone https://github.com/danigian/basicstation.git
```

#### Step 2: Compiling the Station Binary

Depending on whether you are running on x64 or ARM, you have two platform to choose within (rak833x64 or rak833arm)

``` sourceCode
cd basicstation
sudo make platform=rak833arm variant=std
```

The build process consists of the following steps:

*  Fetch and build dependencies, namely [mbedTLS](https://github.com/ARMmbed/mbedtls), [libloragw](https://github.com/Lora-net/lora_gateway) and [libmpsse](https://github.com/devttys0/libmpsse)
*  Setup build environment within subdirectory `build-$platform-$variant/`
*  Compile station source files into executable `build-$platform-$variant/bin/station`

#### Step 3: Running the Example Configuration on a Raspberry Pi

``` sourceCode
cd examples/live-s2.sm.tc
RADIODEV=/dev/ttyUSB0 ../../build-rak833arm-std/bin/station
```