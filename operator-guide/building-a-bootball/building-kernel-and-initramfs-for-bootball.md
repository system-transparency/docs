# Building Kernel and Initramfs

## Prerequisites

* Linux system \(tested with Ubuntu 18.04.2 LTS \(Bionic Beaver\) / Kernel 4.15.0-47-generic
* docker for building the reproducible debian buster kernel and initramfs.
* Clone of system-transparency repository

##  Building debian kernel and initramfs with docker

Inside the system-transparency repository you'll find a folder called:

```text
/remote-os/debian
```

There is the script called run-docker.sh. Run it:

```text
./run-docker.sh
```

If you want to find out what it does, just look at it. Its no magic :\)  
Next step will be [writing STconfig.json](writing-the-stconfig.json.md)

