# How to set up qemu image for testing

## Prerequisites

* Linux system \(tested with Ubuntu 18.04.2 LTS \(Bionic Beaver\) / Kernel 4.15.0-47-generic
* Golang v 1.12 \(see [install Go](https://golang.org/doc/install#install)
  * make sure to also create a workspace at `$HOME/go` \(see [test Go](https://golang.org/doc/install#testing)\)
  * make sure `$HOME/go/bin` and `/usr/local/go/bin` or '/usr/bin/go are added to `PATH` environment variable
* QEMU emulator \(tested with version 2.11.1\)
* Provisioning server with https-request capability
* ssh access to [root@yourserver.test](mailto:root@yourserver.test) \(your 'provisioning server'\)



