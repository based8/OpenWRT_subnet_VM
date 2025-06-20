# OpenWRT_subnet_VM
--------------------------------------------------------------------
### OpenWRT VM to create a subnet for you VMs
This is a guide how to create a subnet for your VMs that passes through a OpenWRT VM.
This is good if you are doing alot of networking in your VMs or if you want to have more control
over your VM network.

This is all done on Linux using KVM/QEMU with virt-manager so i will be showing screenshots of it.
What you need:
- working internet connecting.
- Machine with KVM supported and setup
- a Guest OS for testing

Unzip and convert OpenWrt image to qcow2
```bash
$ gunzip openwrt-x86-64-generic-ext4-combined.img.gz
$ qemu-img convert -f raw -O qcow2 openwrt-*.img openwrt.qcow2
```

Change the routing address for virbr1 to allow host access to router panel
```bash
$ sudo ip addr add 192.168.1.10/24 dev virbr1
$ sudo ip addr del 192.168.100.1/24 dev virbr1
```
