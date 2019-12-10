# STConfig Tool

The STConfig Tool provided by the u-root project enables the generation of a BootBall by a given stconfig.json.

If you already downloaded the u-root git repository and system-transparency git repository, you only need to run the the following:

```text
./system-transparency/stconfig/install_stconfig.sh
```

When installed the tool supports the following functionality:

```text
stconfig create <path/to/stconfig.json> [-o filename.ball]
```

This creates a unsigned BootBall from a given STconfig.json

```text
stconfig sign <path/to/stboot.ball> <path/to/rsa-public-key> <path/to/rsa-cert>
```

Sign signs a given BootBall cryptographically with the given key and certificate.

```text
stconfig unpack <path/to/stboot.ball>
```

Unpack takes a given BootBall and unpacks it to a directory and tells you the path of the directory

