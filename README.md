# Raspbery Pi USB Gadget Image Builder

A script to add USB Ethernet Gadget configuration to a standard Raspbian Lite SD Card image. 
This should work with Raspberry Pi Zero, Zero W and 4.

This is a fork of https://github.com/hardillb/rpi-gadget-image-creator

Currently only tested on Linux, but should also run with Docker Desktop + WSL on Windows 10 and on OSx 

There are options to set the hostname, password, use localaddons file and include backup.tgz.

## Requirements

 - Docker
 - expect

## Install

In terminal, clone the repo:

```
git clone https://github.com/ftrojahn/rpi-gadget-image-creator
```

Download e.g. latest zip from https://downloads.raspberrypi.org/raspios_lite_arm64/images/

Unzip and copy the raspbian lite image into the `rpi-gadget-image-creator`  directory. If you rename it, make sure to include the "arm64" string if it is the 64bit image.

In terminal, cd to `rpi-gadget-image-creator`.

## Running

```
./create-image <filename> <hostname> [optional password] [optional backup url]

# example

./create-image 2022-01-28-raspios-bullseye-arm64-lite my-hostname CHANGEME http://localhost/mybackup.tgz 2>&1 | tee /tmp/2022-01-31-create-image-log.txt
```

Once complete you can write the image file to a SD Card with any of the usual tools e.g. `dd` or `balena-etch`.
You can find instructions on the Raspberry Pi website [here](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)

## TODO

Look at repackaging everything into an extention to DockerPi so the whole thing runs in the container.
