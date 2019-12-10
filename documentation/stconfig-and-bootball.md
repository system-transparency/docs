---
description: Documentation about STConfig in relation to BootBall
---

# STConfig & BootBall

## What is a STConfig?

Simply put, a STConfig is a json file which is used to create a BootBall. The Bootball will be uploaded to the provisioning server and downloaded from there by STBoot for executing on the production server. Syntax of the file looks like this:

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
      },
      {
        "name": "Multiboot Configuration 2", 
        "multiboot_kernel": "kernels/multibootkernel.vmlinuz",
        "multiboot_args": "-a -b -c mulitboot_arg2",
        "multiboot_modules": ["modules/mod1", "modules/mod2", "modules/mod3"]
      },
      {
        "name": "Minimal Configuration 3", 
        "kernel": "kernels/kernel2.vmlinuz",
        "devicetree": "devtrees/tree"
      }
    ], 
    "root_cert": "signing/root.cert" 
  }
```

The structure of a boot configuration is part of the u-root project. We simply built a wrapper, which utilizes the given structure for the creation of our boot configuration. At this moment STBoot only uses the first boot configuration given in a stconfig file and multiboot capability is not implemented yet. Therefore we suggest refraining from the use of multiboot related arguments.   
  
For a successful boot process you have to provide a kernel, the kernel arguments and an initramfs image for the given kernel.



