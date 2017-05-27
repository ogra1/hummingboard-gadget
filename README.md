# SolidRun Hummingboard Gadget Snap

This repository contains the source for an Ubuntu Core gadget snap
for the SolidRun Hummingboard. Building it with snapcraft will
automatically pull, configure, patch and build the git.denx.de/u-boot.git
upstream source for `mx6cuboxi_defconfig` at release v2017.01 and produce
a bootable gadget snap with the resulting binaries.

## Gadget Snaps

Gadget snaps are a special type of snaps that contain device specific support
code and data. You can read more about them in the snapd wiki
https://github.com/snapcore/snapd/wiki/Gadget-snap

## Building

### Natively on armhf

To build the gadget snap locally on a native armhf system just run `snapcraft`
in the toplevel of the tree.

### Cross on x86 systems

Make sure to have the arm cross compiler installed on the host system

```
sudo apt install gcc-arm-linux-gnueabi
```

Add the following to snapcraft.yaml to run make with a cross compilation setup

```
    build: |
        CROSS_COMPILE=arm-linux-gnueabi- make
```

### Rebuilding the uboot environment

The default boot environment is shipped in the uboot.env.in file.
To re-create the binary uboot.env file manually, make edits in
the uboot.env.in file and use the mkenvimage tool to create a 128k
sized redundant environment binary.
(note that size and redundancy are a hard requirement for proper
operation of the resulting UbuntuCore image)

```
sudo apt install u-boot-tools
mkenvimage -r -s 131072  -o uboot.env uboot.env.in
```
