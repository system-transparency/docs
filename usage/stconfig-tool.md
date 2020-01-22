# stconfig tool

The `stconfig` tool provides functionality to create and manipulate a [boot ball](stboot.ball.md) based on a [~~configuration~~]().

Since the toole works closely with the [stboot bootloader](), its sources are hostet at the [u-root project](https://github.com/u-root/u-root/tree/stboot) \(stboot branch\)

If you already downloaded the [u-root git repository](https://github.com/u-root/u-root/tree/stboot) and [system-transparency git repository](https://github.com/system-transparency/system-transparency), you only need to run the the following inside system-transparency:

```text
./system-transparency/stconfig/install_stconfig.sh
```

When installed the tool supports the following functionality:

```text
stconfig create <path/to/stconfig.json> [-o filename.ball]
```

This creates a unsigned `stboot.ball` from a given `stconfig.json`

```text
stconfig sign <path/to/stboot.ball> <path/to/rsa-public-key> <path/to/rsa-cert>
```

Sign signs a given `stboot.ball`cryptographically with the given key and certificate.

```text
stconfig unpack <path/to/stboot.ball>
```

Unpack takes a given `stboot.ball` and unpacks it to a directory and tells you the path of the directory. It can be used to insept the `stboot.ball`

