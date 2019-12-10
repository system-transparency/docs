# STBoot

## What is STBoot

STBoot is a custom bootloader provided by the u-root project. Its purpose is to be part of the firmware for the production server either deployed as payload for coreboot or as part of the image which will be deployed over dd-command on the server.

STBoot will be executed automatically and starts configuring the network interface of the server with a provided IP address or DHCP. After that the lastest BootBall from the provisioning server will be downloaded, unpacked and checked for validity. If all this is successful STBoot will execute the provided kernel from the BootBall with its kernel arguments and initramfs.

