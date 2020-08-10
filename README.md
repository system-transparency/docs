---
description: Welcome to System Transparency!
---

# Getting Started

System transparency is aimed at facilitating trust for the components of a system by giving every server a unique identity, limiting the attack surface and mutable state in the firmware and allowing both owners and users to verify all software running on a platform starting from the first instruction executed after power on. System Transparency accomplishes these goals by the seven principles listed in the manifest.

{% embed url="https://asciinema.org/a/294267" %}

### What is System Transparency?

Learn more about System Transparency with a [talk about the basic idea](https://media.ccc.de/v/36c3-139-system-transparency) and the [manifest](overview/manifest.md).

### Join the community!

We are using our own Slack chat. [Join us!](https://communityinviter.com/apps/system-transparency/join)

### Where to start?

{% tabs %}
{% tab title="Operator" %}
To administrate all components of System Transparency check out the tooling repository. This is still under development.

```text
git clone https://github.com/system-transparency/system-transparency.git
```
{% endtab %}

{% tab title="Developer" %}
The System Transparency bootloader is part of the u-root project. Check out the repository and switch to the development branch. 

```text
git clone https://github.com/u-root/u-root.git
git checkout stboot
```

Browse the code at `cmds/bootstboot` , `tools/stconfig` and `pkg/boot/stboot`. Learn about the concept pointed out in the [manifest](overview/manifest.md)
{% endtab %}
{% endtabs %}

### Media / Talks

1. **System Transparency is the future** - [https://mullvad.net/en/blog/2019/6/3/system-transparency-future/](https://mullvad.net/en/blog/2019/6/3/system-transparency-future/) 
2. **Coreboot ported to our first target platform** - [https://9esec.io/blog/first-modern-coreboot-server-platform/](https://9esec.io/blog/first-modern-coreboot-server-platform/)
3. **System Transparency at the 36c3** - [https://media.ccc.de/v/36c3-139-system-transparency](https://media.ccc.de/v/36c3-139-system-transparency)

