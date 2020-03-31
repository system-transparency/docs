# provisioning-servers.json

This file resides on the data partition of the host and contains a list of servers the stboot bootloader will use to download the [bootball](stboot.ball.md). Put the servers into a JSON array like this:

```text
[
    "https://my-provisioning-server.com",
    "https://my-other-provisioning-server.com"
]
```

