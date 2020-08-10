---
description: System Overview
---

# Get System Transparency up and running

![](../.gitbook/assets/stcomponents.svg)

Since _System Transparency_ is distributed to multiple [components](../overview/components/) on different hardware, setting up the system involves:

1. Firmware deployment including stboot bootloader to the hosts.
2. Configure a provisioning server and upload a boot ball containing the operating system in case stboot is configured for netbooting.

The hosts will download the operating system during start up.

The operator's machine should run Linux in order to use all the tooling required.

The tooling is hosted at [https://github.com/system-transparency/system-transparency](https://github.com/system-transparency/system-transparency).

