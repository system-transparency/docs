---
description: A short introduction about server-side requirements
---

# How to set up the netboot server?

## Requirements

1. A host with a static ipv4/ipv6 address or similar setup.
2. The host should run a Linux distribution.
3. A dns provider with API access is required.

## Goals

* Set up a netboot server which is ready for system transparency.
* Bootball artifacts have to be sealed against a new domain name hash.
* Bootball artifacts can be downloaded and verified through the let's encrypt transparency log with stboot bootloader in the datacenter.

## How to deploy?

![](../.gitbook/assets/netboot%20%282%29.png)



 

Create a hash of the bootball artifact by using bootball config tool and split it after 32 bytes with a dot. 

{% hint style="success" %}
03b650a736663896177551f961dca548.79efd480cb8717f0a35637b863930a77
{% endhint %}

{% hint style="danger" %}
Because of a 63 byte CN and sub-domain name length restriction by let's encrypt we are using a shorter domain pointing to the same A record IP address in the certificate. Also we split up the hash after the 32 byte with a dot.
{% endhint %}

Add an A record to your target host inside by using the domain name hash as subdomain.

{% code title="DNS records" %}
```bash
A    st.test.dev    X.X.X.X
A    03b650a736663896177551f961dca548.79efd480cb8717f0a35637b863930a77.test.dev    X.X.X.X
```
{% endcode %}

Download your let's encrypt tooling for the bootball artifacts. In our example we make use of [LEGO](https://github.com/go-acme/lego/releases) to generate a certificate based on:

#### Common Name: test.dev

#### DNS Name: 03b650a736663896177551f961dca548.79efd480cb8717f0a35637b863930a77.test.dev

{% code title="Run lego" %}
```bash
lego -d test.dev -d 03b650a736663896177551f961dca548.79efd480cb8717f0a35637b863930a77.test.dev -a -m your@email.com --pem --path certs --http run
```
{% endcode %}

If you add more artifacts just match more domain names. The certificates can be found in the certs directory.

