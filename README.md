# SolidRun Hummingboard Gadget Snap

This repository contains the source for an Ubuntu Core gadget snap
for the SolidRun Hummingboard. Building it with snapcraft will
automatically pull, configure, patch and build the git.denx.de/u-boot.git
upstream source for `mx6cuboxi_defconfig` at release `v2017.01` and produce
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

Copy the crossbuild-snapcraft.yaml over snapcraft.yaml and run `snapcraft`

```
cp crossbuild-snapcraft.yaml snapcraft.yaml
snapcraft
```
## Splash screen

The splashscreen has been created from a jpeg with the following line:

```
jpegtopnm splash.jpg | ppmquant 256 | ppmtobmp -bpp 8 >splash.bmp
```

See https://www.denx.de/wiki/DULG/UBootBitmapSupport for more info.
