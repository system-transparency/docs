# How to set up qemu image for testing

## Prerequisites

* Linux system \(tested with Ubuntu 18.04.2 LTS \(Bionic Beaver\) / Kernel 4.15.0-47-generic
* Golang v 1.12 \(see [install Go](https://golang.org/doc/install#install)
  * make sure to also create a workspace at `$HOME/go` \(see [test Go](https://golang.org/doc/install#testing)\)
  * make sure `$HOME/go/bin` and `/usr/local/go/bin` or '/usr/bin/go are added to `PATH` environment variable
* clone of u-root and system-transparency repository
* u-root must be installed
* QEMU emulator \(tested with version 2.11.1\)
* Provisioning server with https-request capability
* ssh access to [root@yourserver.test](mailto:root@yourserver.test) \(your 'provisioning server'\)

## Idea

This tutorial is just for the sake of testing the boot process of your BootBall. QEMU is utilized to simulate your production server. A SysLinux image with u-root initramfs and stboot bootloader is loaded inside QEMU. Here it will be shown how to build the SysLinux image and u-root initramfs with stboot bootloader. 

### Step by step

#### 1.

At first we want to build the SysLinux image. For that, system-transparency provides a script:

```text
./system-transparency/deploy/image/create_image.sh
```

#### 2.

Second step is to build the initramfs with u-root. Make sure u-root is installed, otherwise run:

```text
./system-transparency/stboot/install-u-root.sh
```

#### 3.

Now u-root with stboot support should be installed. Create the initramfs for the QEMU image with:

```text
./system-transparency/stboot/make_initramfs.sh
```

4.

Your "production server" or in this case you QEMU image needs an IP configuration. For this purpose we generate a file called hostvars.json. We do so by using a script:

```text
./system-transparency/stboot/create_hostvars.sh
```

This file needs to me moved in the SysLinux image as well. And system-transparency provide a script for that as well:

```text
./system-transparency/deploy/image/mv_hostvars_to_image.sh
```

5.

Before executing QEMU we need to merge the initramfs into the SysLinux image. Worry not, system-transparency repository provides a script for that as well:

```text
./system-transparecy/deploy/image/mv_initrd_to_image.sh
```



