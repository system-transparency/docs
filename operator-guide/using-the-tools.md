---
description: Description of the workflow
---

# Using the Tools

Set up System Transparency includes the following steps:

1. Generate signing keys and for all involved system administrators along with a corresponding  root certificate.
2. Prepare the firmware for the provisioning server. Depending on the [scenario](../overview/scenarios.md) this comes in different flavors.
3. Create a [configuration file](../usage/hostvars.json.md) for the hosts.
4. Build a reproducible Operating system with every user space program needed to be packed into the kernel and initramfs respectively.
5. Build the `u-root` command.
6. Build the [stconfig tool](../usage/stconfig-tool.md).
7. Use `u-root` to build an initramfs including the [stboot bootloader](../usage/stboot.md) . This becomes the initramfs of [linuxboot](../overview/components/bootloader.md) for the host firmware.
8. Include this initramfs into the host firmware.
9. Use `stconfig` to crate a [stboot.ball](../usage/stboot.ball.md) from the operating system files.
10. Upload `stboot.ball` to the provisioning server.
11. Deploy the firmware to the host or test it with QEMU.

You can discover this workflow with example data with the [tooling repository](https://github.com/system-transparency/system-transparency#system-transparency-tooling). Refer to the documentation there for further information.

Every of the above step will be performed interactively:

```text
./run.sh
```



