# Writing STconfig.json

## Prerequisites

* Cloned system-transparency and u-root repository
* Golang v 1.12 \(see [install Go](https://golang.org/doc/install#install)\)
  * make sure to also create a workspace at `$HOME/go` \(see [test Go](https://golang.org/doc/install#testing)\)
  * make sure `$HOME/go/bin` and `/usr/local/go/bin` or '/usr/bin/go are added to `PATH` environment variable

### Structure of STConfig.json

See [STConfig & BootBall](../../usage/stconfig-and-bootball.md)

### **Where to place STConfig.json**

Inside system-transparency repository you'll find the directory "configs". There you have to make a new subdirectory and name it as you like. You have to place your STConfig.json inside your subfolder.

```text
system-transparency/configs/<yourdir>/STConfig.json                                       
```

Now you also have to copy the kernel and initramfs from the previous step \([Building Kernel and Initramfs for BootBall](building-kernel-and-initramfs-for-bootball.md)\) in subdirectories named kernels and initrds. Usually you find these  in:

```text
system-transparency/remote-os/debian/out
```

### Generate signing keys and root certificate

This step is only necessary if you're just testing and playing around.   
The proper handling of signing keys and certificates is essential for using system-transparency in production.   
  
Use the script provided with the system-transparency repository:

```text
system-transparency/keys/generate-keys-and-certs.sh
```

 Copy the generated root.cert in your subdirectory. The keys will be used in [Packing and Signing the BootBall.](packing-and-signing-bootball.md)

The last step is including the paths of your kernel, initramfs and root certifcate in your STConfig.json.  
Here is an example:

```text
{  
    "boot_configs": [ 
      { 
        "name": "Standard Configuration 1", 
        "kernel": "kernels/kernel1.vmlinuz", 
        "kernel_args": "-a -b -c arg1",  
        "initramfs": "initrds/initramfs.cpio",
        "devicetree": "",
        "multiboot_kernel": "",
        "multiboot_args": "",
        "multiboot_modules": ["", "", ""]
      }
    ], 
    "root_cert": "root.cert" 
  }
```

Now lets move on to [Packing and Signing the BootBall](packing-and-signing-bootball.md).

