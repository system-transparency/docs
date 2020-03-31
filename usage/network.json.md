# network.json

This file stores the network configuration for the host and resides on the data partition of the host. The data is provided as a JSON object.

A valid configuration requires `host_ip` and `gateway` to be set in the form `<ip>/<netmask>`, `dns` is optional. If all values are set to `""`, DHCP is used for network configuration.

```text
{
   "host_ip":"10.0.2.15/24",
   "gateway":"10.0.2.2/24",
   "dns":""
}
```

The example above will work with QEMU.

