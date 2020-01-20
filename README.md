---
description: Welcome to System Transparency!
---

# Getting Started

{% embed url="https://asciinema.org/a/294267" %}

### What is System Transparency?

Learn more about system transparency with the [manifest](overview/manifest/).

### Where to start?

{% tabs %}
{% tab title="Operator" %}
To administrate all components of System Transparency check out the tooling repository.

```text
git clone https://github.com/system-transparency/system-transparency.git
```

Then go ahead to the [operator guide](operator-guide/get-system-transparency-up-and-running.md). Also refer to the documentation at the [tooling repository](https://github.com/system-transparency/system-transparency#system-transparency-tooling).
{% endtab %}

{% tab title="Developer" %}
The System Transparency bootloader is part of the u-root project. Check out the repository and switch to the development branch. 

```text
git clone https://github.com/u-root/u-root.git
git checkout stboot
```

Broes the code at `cmds/bootstboot` , `tools/stconfig` and `pkg/boot/stboot`. Learn about the concept pointed out in the [manifest](overview/manifest/)
{% endtab %}
{% endtabs %}

### Media / Talks

1. **System Transparency is the future** - [https://mullvad.net/en/blog/2019/6/3/system-transparency-future/](https://mullvad.net/en/blog/2019/6/3/system-transparency-future/) 
2. **Coreboot ported to our first target platform** - [https://9esec.io/blog/first-modern-coreboot-server-platform/](https://9esec.io/blog/first-modern-coreboot-server-platform/)

