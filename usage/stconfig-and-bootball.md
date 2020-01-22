# stconfig.json

This configuration file is the template for the `stboot.ball`. It can contain multiple boot configurations. This file must be passed to the [stconfig tool](stconfig-tool.md).

The syntax of the file looks like this:

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

The structure of the items of `boot_configs` is part of the u-root project. We simply built a wrapper, which utilizes the given structure for the creation of our boot configuration. At the moment only  the first boot configuration will be used and multiboot capability is not fully supported.   
For a successful boot process you have to provide a kernel, the kernel arguments and an initramfs.

