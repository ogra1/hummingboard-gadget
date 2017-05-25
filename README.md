# SolidRun Hummingboard Gadget Snap

This repository contains an Ubuntu Core gadget snap for the SolidRun
Hummingboard

## Gadget Snaps

Gadget snaps are a special type of snaps that contain device specific support
code and data. You can read more about them in the snapd wiki
https://github.com/snapcore/snapd/wiki/Gadget-snap

## Building

To build the gadget snap locally please use `snapcraft`.

In case you need to rebuild u-boot, the steps are

```
sudo apt install gcc-arm-linux-gnueabi
export CROSS_COMPILE=arm-linux-gnueabi-
git clone git://git.denx.de/u-boot.git
cd u-boot; git checkout v2017.01
git apply uboot.patch
make mx6cuboxi_defconfig
make -j8
```

You want the SPL and u-boot.img files this build produced and put them
into the prebuilt/ subdir of this tree

Building the uboot environment

```
mkenvimage -r -s 131072  -o prebuilt/uboot.env uboot.env.in
```
