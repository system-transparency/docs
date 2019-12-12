# Packing and Signing BootBall

### Prerequisites

* Cloned system-transparency and u-root repository
* Golang v 1.12 \(see [install Go](https://golang.org/doc/install#install)\)
  * make sure to also create a workspace at `$HOME/go` \(see [test Go](https://golang.org/doc/install#testing)\)
  * make sure `$HOME/go/bin` and `/usr/local/go/bin` or '/usr/bin/go are added to `PATH` environment variable
* u-root and stconfig-tool must be installed.

### Pack it, sign it, push it!

We gathered everything necessary to build the BootBall. Here is what you have to do next.

#### Pack it!

Now you'll need the STConfig-Tool. If you haven't installed it yet, do so with the provided script.

```text
./system-transparency/stconfig/install_stconfig.sh
```

The STConfig-Tool has a subcommand called "create". It takes the path to the STConfig.json.

```text
stconfig create <path/to/STConfig.json>
```

This will generate a Boot.ball file in the same directory.

#### Sign it!

Next you have to sign the Boot.ball file. This is also done with a subcommand of STConfig-Tool.

```text
stconfig sign <path/to/boot.ball> <path/to/your/privkey.key> <path/to/your/key.cert>
```

At the moment, you need to sign the boot.ball with THREE valid and distinct keys. So repeat the process with other keys and certs generated earlier.

#### Push it!

Your Boot.ball is ready for deployment. Push it to your provisioning server.

