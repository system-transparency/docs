---
description: A short introduction about server-side requirements
---

# The Provisioning Server

## Requirements

* A host with a static ipv4/ipv6 address or similar setup
* The host should run a Linux distribution
* A DNS provider with API access

## Goals

Assuming the server is reachable under the domain `st-provisioning.com`, then the following must be given:

1. Support HTTPS at `st-provisioning.com`
2. Listen on port 80  on every subdomain `*.st-provisioning.com` and `*.*.stprovisioning.com`
3. Forward `*.st-provisioning.com` to `st-provisioning.com/*` and `*.*.st-provisioning.com` to `st-provisioning.com/*/*` respectively

 2. and 3. are important steps for the CT log feature, which is currently under development. It enables the tooling to  request a certificate for a unique subdomain at a Certificate Authority like [Let's Encrypt](https://letsencrypt.org/docs/ct-logs/).

