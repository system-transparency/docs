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

![](../.gitbook/assets/netboot%20%281%29.png)



 

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

If you add more artifacts just match more domain names. The LE certificate for bundling it with the bootball can be found in the certs directory.

{% code title="LE certificate for ST" %}
```text
Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            03:d2:6f:77:7f:82:f8:b2:b8:18:77:a5:d9:70:94:db:50:2f
    Signature Algorithm: sha256WithRSAEncryption
        Issuer: C = US, O = Let's Encrypt, CN = Let's Encrypt Authority X3
        Validity
            Not Before: Dec 10 15:05:49 2019 GMT
            Not After : Mar  9 15:05:49 2020 GMT
        Subject: CN = test.dev
        Subject Public Key Info:
            Public Key Algorithm: id-ecPublicKey
                Public-Key: (384 bit)
                pub:
                    04:dc:7b:3a:22:25:92:be:a8:03:33:bf:fe:33:99:
                    97:f7:c6:92:98:b0:96:db:86:e0:e9:60:ba:6c:5a:
                    1c:64:70:27:69:81:df:b5:43:e2:5c:99:56:d1:b7:
                    01:2f:ad:b4:a1:28:2f:50:37:9d:57:b0:2d:b4:f5:
                    c2:d4:dc:7a:45:59:fd:16:a6:bf:ef:a7:47:3b:92:
                    07:88:a5:ec:b7:86:fd:8c:b4:7d:64:57:6e:e0:45:
                    16:fe:21:3f:de:8a:e8
                ASN1 OID: secp384r1
                NIST CURVE: P-384
        X509v3 extensions:
            X509v3 Key Usage: critical
                Digital Signature
            X509v3 Extended Key Usage: 
                TLS Web Server Authentication, TLS Web Client Authentication
            X509v3 Basic Constraints: critical
                CA:FALSE
            X509v3 Subject Key Identifier: 
                CE:CB:A5:D6:93:43:A6:3C:D4:8B:3F:4C:1C:CF:3F:A2:7F:D6:78:C8
            X509v3 Authority Key Identifier: 
                keyid:A8:4A:6A:63:04:7D:DD:BA:E6:D1:39:B7:A6:45:65:EF:F3:A8:EC:A1

            Authority Information Access: 
                OCSP - URI:http://ocsp.int-x3.letsencrypt.org
                CA Issuers - URI:http://cert.int-x3.letsencrypt.org/

            X509v3 Subject Alternative Name: 
                DNS:03b650a736663896177551f961dca548.79efd480cb8717f0a35637b863930a77.test.dev, DNS:test.dev
            X509v3 Certificate Policies: 
                Policy: 2.23.140.1.2.1
                Policy: 1.3.6.1.4.1.44947.1.1.1
                  CPS: http://cps.letsencrypt.org

            CT Precertificate SCTs: 
                Signed Certificate Timestamp:
                    Version   : v1 (0x0)
                    Log ID    : B2:1E:05:CC:8B:A2:CD:8A:20:4E:87:66:F9:2B:B9:8A:
                                25:20:67:6B:DA:FA:70:E7:B2:49:53:2D:EF:8B:90:5E
                    Timestamp : Dec 10 16:05:49.167 2019 GMT
                    Extensions: none
                    Signature : ecdsa-with-SHA256
                                30:45:02:21:00:BA:D6:79:0F:9A:01:4B:DE:9B:20:5E:
                                94:45:AF:F3:7B:7D:4F:12:85:9A:B8:F3:58:73:F7:2E:
                                25:CE:83:52:DD:02:20:36:C5:9A:DA:49:36:1C:FB:56:
                                61:69:F3:01:25:12:62:08:DD:EC:1C:CF:79:62:24:FF:
                                22:34:CB:01:DE:0C:BF
                Signed Certificate Timestamp:
                    Version   : v1 (0x0)
                    Log ID    : 6F:53:76:AC:31:F0:31:19:D8:99:00:A4:51:15:FF:77:
                                15:1C:11:D9:02:C1:00:29:06:8D:B2:08:9A:37:D9:13
                    Timestamp : Dec 10 16:05:49.271 2019 GMT
                    Extensions: none
                    Signature : ecdsa-with-SHA256
                                30:45:02:21:00:E8:CD:EB:8F:47:2E:2E:02:67:2F:C9:
                                E3:F4:0D:18:57:3E:2B:8C:E2:D1:46:A5:4D:AB:ED:04:
                                C0:20:39:73:49:02:20:31:38:EB:C9:6E:D7:38:61:14:
                                51:7A:68:03:82:B7:29:BD:A5:D0:17:91:00:DA:C3:3E:
                                C4:3D:8A:86:84:D3:D4
    Signature Algorithm: sha256WithRSAEncryption
         5c:7c:29:5e:ea:8c:98:1a:05:27:1d:60:a4:37:f5:e1:e0:c7:
         4e:15:a3:f0:47:b8:89:ac:0a:14:69:61:c1:c8:59:ab:ed:71:
         e5:ac:02:1b:cd:39:83:00:68:22:48:1b:3c:f2:3e:c9:13:8f:
         94:8e:d8:92:1f:67:9f:3a:9a:78:aa:a4:7a:16:9c:7d:5f:29:
         46:c1:5a:ba:fc:89:89:14:59:1a:81:70:e5:b8:25:78:c8:d7:
         fb:4c:d1:37:52:89:9c:e6:a5:e2:52:93:1c:db:c3:e6:a5:b4:
         88:e1:69:c5:fa:50:6a:c7:4d:4f:32:3f:ae:fe:c0:a6:38:3a:
         60:84:1d:8b:1f:27:36:36:6f:20:6d:06:64:97:68:4c:b5:2a:
         27:99:19:ae:73:f6:3e:4b:65:f1:30:1f:45:ef:99:66:4a:c3:
         44:e7:3a:d7:82:31:56:d7:2f:ff:e1:c8:05:82:2b:ab:50:48:
         a1:c2:58:72:ea:90:f2:be:54:b9:c4:b8:0f:3f:29:99:7f:08:
         f1:2e:dd:ee:a0:3d:22:a7:e6:df:1d:c9:4a:2d:ea:b0:bc:45:
         29:82:d6:52:e9:32:a9:b6:c0:8f:a4:31:87:d3:51:f5:08:d9:
         be:ef:99:a5:4f:1e:fe:cf:dc:cf:33:a6:e1:71:70:a2:f9:35:
         cb:97:83:4c
-----BEGIN CERTIFICATE-----
```
{% endcode %}

