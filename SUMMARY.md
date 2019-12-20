# Table of contents

* [Getting Started](README.md)

## Tech Stack Overview <a id="overview"></a>

* [Concept and Use Cases](overview/concept-and-ideas.md)
* [Manifest](overview/manifest/README.md)
  * [Provisioning Ritual](overview/manifest/1.-provisioning-ritual.md)
  * [Tamper Resistance](overview/manifest/3.-tamper-resistance.md)
  * [Integrity Protected Firmware](overview/manifest/2.-integrity-protected-firmware.md)
  * [Reproducible Builds](overview/manifest/4.-reproducible-builds.md)
  * [Platform Attestation](overview/manifest/5.-platform-attestation.md)
  * [Immutable Infrastructure](overview/manifest/6.-immutable-infrastructure-optional.md)
  * [Binary Transparency](overview/manifest/7.-certificate-transparency-optional.md)
* [Components](overview/components/README.md)
  * [BIOS firmware](overview/components/bios-firmware.md)
  * [Bootloader](overview/components/bootloader.md)
  * [Operating Systems](overview/components/operating-system.md)

## Operator guide

* [Building a BootBall](operator-guide/building-a-bootball/README.md)
  * [Building Kernel and Initramfs](operator-guide/building-a-bootball/building-kernel-and-initramfs-for-bootball.md)
  * [Writing STconfig.json](operator-guide/building-a-bootball/writing-the-stconfig.json.md)
  * [Packing and Signing BootBall](operator-guide/building-a-bootball/packing-and-signing-bootball.md)
* [How to set up qemu image for testing](operator-guide/how-to-set-up-qemu-image-for-testing.md)
* [How to set up production server](operator-guide/how-to-set-up-production-server.md)
* [How to set up the netboot server?](operator-guide/how-to-set-up-the-netboot-server.md)

## Tooling & Usage <a id="usage"></a>

* [STBoot](usage/stboot.md)
* [STConfig Tool](usage/stconfig-tool.md)
* [STConfig & BootBall](usage/stconfig-and-bootball.md)

