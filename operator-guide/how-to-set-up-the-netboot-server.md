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



 

* [ ] Create a hash of the bootball artifact which we will use as domain name hash.

```bash
$ openssl dgst -sha256 -hex $artifact | awk '{print $2}'
```

{% hint style="danger" %}
Because of a 64byte domain name length restriction by let's encrypt we are using a shorter domain pointing to the same A record IP address in the certificate.
{% endhint %}

* [ ] Add an A record to your target host inside by using the domain name hash as subdomain.

{% code title="DNS records" %}
```bash
A    st.test.dev    X.X.X.X
A    03b650a736663896177551f961dca54879efd480cb8717f0a35637b863930a77.test.dev    X.X.X.X
```
{% endcode %}

* [ ] Download your let's encrypt tooling + webserver your choice and set it up as file server for the bootball artifacts. In our example we make use of [caddy v2](https://github.com/caddyserver/caddy) file server module + https. 

{% code title="Execute on host with running caddy v2" %}
```bash
$ curl -X POST "http://localhost:2019/load" \
    -H "Content-Type: application/json" \
    -d @- << EOF
    {
			"apps": {
				"http": {
					"servers": {
						"myserver": {
							"listen": [":443"],
							"routes": [
								{
									"match": [{"host": ["st.test.dev", "03b650a736663896177551f961dca54879efd480cb8717f0a35637b863930a77.test.dev"]}],
									"handle": [{
										"handler": "file_server",
										"root": "/var/www"
									}]
								}
							]
						}
					}
				}
			}
		}
EOF
```
{% endcode %}

If you add more artifacts just match more domain names.

