---
title: Readme.4D03
date: 2016-10-09 10:05:01
tags:
  - D03
categories:
  - Estuary
  - Documents
---

This is the readme file for D03 platform
<!--more-->

After you executed
```bash
./estuary/build.sh --file=./estuary/estuarycfg.json --builddir=./workspace
```
for D03, all targets files will be produced. they are:

### UEFI_D03.fd

**description**: `UEFI_D03.fd` is the UEFI bios for D03 platform.  
**target**: `<project root>/workspace/binary/D03/UEFI_D03.fd`  
**source**: `<project root>/uefi`

build commands(supposedly, you are in `<project root>` currently):
```bash
./estuary/submodules/build-uefi.sh --platform=D03 --output=workspace
```

### grubaa64.efi

**description**: `grubaa64.efi` is used to load kernel image and dtb files from SATA, SAS, USB Disk, or NFS into RAM and start the kernel.  
**target**: `<project root>/workspace/binary/arm64/grubaa64.efi`  
**source**: `<project root>/grub`

build commands(supposedly, you are in `<project root>` currently):
```bash
./estuary/submodules/build-grub.sh --output=./workspace
```
if your host is not arm architecture, please execute
```bash
./estuary/submodules/build-grub.sh --output=./workspace --cross=aarch64-linux-gnu-
```
Note: more details about how to install `gcc-linaro-aarch64-linux-gnu-4.9-2014.09_linux`, please refer to <https://github.com/open-estuary/estuary/blob/master/doc/Toolchains_Guide.4All.md>.

### Image & hip06-d03.dtb

**descriptions**: `Image` is the kernel executable program, and `hip06-d03.dtb` is the device tree binary.  
**target**:
`Image` in `<project root>/workspace/binary/arm64/Image`  
`hip06-d03.dtb` in `<project root>/workspace/binary/D03/hip06-d03.dtb`  
**source**: `<project root>/kernel`

build commands(supposedly, you are in `<project root>` currently):
```bash
./estuary/submodules/build-kernel.sh --platform=D03 --output=workspace
```
if your host is not arm architecture, please execute
```bash
./estuary/submodules/build-kernel.sh --platform=D03 --output=workspace --cross=aarch64-linux-gnu-
```
Note: more details about how to install `gcc-linaro-aarch64-linux-gnu-4.9-2014.09_linux`, please refer to <https://github.com/open-estuary/estuary/blob/master/doc/Toolchains_Guide.4All.md>.

More detail about distributions, please refer to [Distributions_Guide.md](https://github.com/open-estuary/estuary/blob/master/doc/Distributions_Guide.4All.md).

More detail about toolchains, please refer to [Toolchains_Guide.md](https://github.com/open-estuary/estuary/blob/master/doc/Toolchains_Guide.4All.md).

More detail about how to deploy target system into D03 board, please refer to [Deployment_Manual.md](https://github.com/open-estuary/estuary/blob/master/doc/Deploy_Manual.4D03.md).

More detail about how to debug, analyse, diagnose system, please refer to [Armor_Manual.md](https://github.com/open-estuary/estuary/blob/master/doc/Armor_Manual.4All.md).

More detail about how to benchmark system, please refer to [Caliper_Manual.md](https://github.com/open-estuary/estuary/blob/master/doc/Caliper_Manual.4All.md).

More detail about how to access remote boards in OpenLab, please refer to [Boards_in_OpenLab](http://open-estuary.org/accessing-boards-in-open-lab/).
