---
description: What System Transparency is about
---

# Manifest

[Mullvad wrote up a paper](%20https://mullvad.net/media/system-transparency-rev5.pdf) on what they call System Transparency.

### Provisioning Ritual

A key ceremony of each server to bind the servers unique identity with a difficult to forge physical artifact like a video.

### Tamper Resistance

Tamper resistance. Attackers cannot be stopped from changing the content of the firmware flash by replacing the actual chip. So, violations of the physical integrity of the server hardware need to be detectable.

### Integrity Protected Firmware

Physical write-protection of the firmware. Writable code sections are a mutable state so System Transparency limits the possible changes to this critical piece of code. Read-only code also serves as a root of trust for all other software-enforced security mechanisms.

### Reproducible Builds

Reproducible builds. Ensures that if a binary artifact is built once, it can be built again and again and produce the same artifact. This establishes a verifiable link between the human-readable code and the binary that was attested using the measured boot mechanism.

### Platform Attestation

Measured boot. System Transparency has the goal to give all parties insight into what code was run as part of the system boot. A measured boot in combination with remote attestation allows third parties to acquire a cryptographic log of the boot.

### Immutable Infrastructure

Immutable infrastructure. System transparency only works when changes to the operating system are limited. Allowing somebody to log into the system and make arbitrary changes invalidates all guarantees of a measured boot.

### Binary Transparency

Binary transparency log. All firmware and OS images that can be booted on a system are signed by the system's owner and are inserted into a public, append-only log. Users of the system can monitor this log for new entries and catch malicious system owners booting backdoored firmware on new servers.



