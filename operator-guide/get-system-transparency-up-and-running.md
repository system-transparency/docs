---
description: System Overview
---

# Get System Transparency up and running

![](../.gitbook/assets/stcomponents.svg)

Since _System Transparency_ is distributed to multiple [components](../overview/components/) on different hardware, setting up the system involves:

1. Firmware deployment including [stboot bootloader](../usage/stboot.md) to the hosts.
2. Configure a provisioning server and upload a [boot ball](../usage/stboot.ball.md) containing the operating system.

The hosts will download the operating system during start up.

The operator's machine should run Linux in order to use all the tooling required. On Debian-based systems you'll need the following packages:

```text
apt install golang docker.io openssl git qemu-system-x86 wget sudo bison flex pkg-config libelf-dev libssl-dev bc libc6-i386 gcc-8 g++-8
```

The tooling is hosted at [https://github.com/system-transparency/system-transparency](https://github.com/system-transparency/system-transparency). The following pages will guide you through the process of setting up _System Transparency_.

