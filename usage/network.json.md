# network.json

This file stores the network configuration for the host and resides on the data partition of the host. The data is provided as a JSON object.

IP addresses must be in the form `<ip>/<netmask>` , a valid configuration requires `host_ip` and `gateway` to be set, `dns` is optional. If all values are set to `""`, DHCP is used for network configuration.

```text
{
   "host_ip":"10.0.2.15/24",
   "gateway":"10.0.2.2/24",
   "dns":""
}
```

The example above will work with QEMU.

