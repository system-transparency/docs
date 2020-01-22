---
description: The bootloader of a System Transparency host
---

# stboot bootloader

## What is STBoot

STBoot is a custom bootloader provided by the u-root project. Its purpose is to be part of the firmware for the hosts. Depending on the [scenario](../overview/scenarios.md) it either deployed as part of a disk image, as a UEFI application or as a coreboot payload.

## How does it work

STBoot will be executed automatically and starts configuring the network interface of the server.  After downloading `stboot.ball` from the provisioning server, several validation checks will be made. If successful, stboot will execute the boot configuration including the final operating system. 

![](../.gitbook/assets/stboot-1.svg)

