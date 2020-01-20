---
description: How to use System Transparency in the real world?
---

# Scenarios

We defined three real world scenarios which should at least support a high chance that we have covered a lot hardware systems. We categorized the scenarios based on the firmware with levels. With the lowest firmware level it is possible make the whole system stack transparent.

### FL3: Mixed firmware

Your hardware runs closed source firmware in legacy CSM mode or the firmware itself is a BIOS. Most systems nowadays already runs UEFI firmware. Please check if the CSM mode in your BIOS settings is enabled if you want to use this scenario.

Execution flow: MBR is executed

Bootloaders: Syslinux, ST provides harddrive image

Requirements: CSM mode or BIOS

### FL2: UEFI firmware

Your hardware runs closed source firmware UEFI firmware with the CSM mode disabled in the firmware settings. **This mode is currently not support by System Transparency**. Feel free to do a pull request and help us out!

Execution flow: GPT, efi partition, UEFI application

Bootloaders: None, stboot can be packed with Linux kernel as EFI application

Requirements: Secure Boot user mode or OEM keys support stboot

### FL1: Open Source firmware

Your hardware runs open source firmware. This can be [coreboot](www.coreboot.org), [TianoCore](www.tianocore.org), [slimmbootloader](https://slimbootloader.github.io/) or [u-boot](http://www.denx.de/wiki/U-Boot). System Transparency has specific [firmware requirements](../components/bios-firmware.md#what-has-the-firmware-todo-with-system-transparency). As far we know only coreboot is able to satisfy these requirements. That is why we only support coreboot firmware at the moment.

Execution flow: Payload is executed in firmware

Bootloaders: None, stboot and Linux kernel are part of coreboot payload

Requirements: coreboot capable hardware with 12MB BIOS flash





