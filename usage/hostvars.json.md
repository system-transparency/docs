# hostvars.json

This json is included in the firmware and stores data needed by the bootloader. If no network configuration is provided, the stboot bootloader will configure via DHCP.

```text
{
      "host_ip":"",
      "netmask":"",
      "gateway":"",
      "dns":"",
      "bootstrap_url":"https://provisioning-server.com",
      "minimal_signatures_match": 3
}

```

