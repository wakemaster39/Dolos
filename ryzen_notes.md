## Common Issues


```
E: Package 'libvirt-bin' has no installation candidate
```
For me at least 'libvirt-bin' has been split into two packages on Debian Stretch.
https://lists.debian.org/debian-user/2016/11/msg00518.html
```
libvirt-daemon-system
libvirt-clients
```

```
Error starting domain: Requested operation is not valid: network 'default' is not active
```
In virtual machine manager, Edit>Connection Details>Default>Autostart[x]
Reboot

## IOMMU Stuff

Ryzen will need one of the later Linux kernels for best results.
I used the latest from https://www.kernel.org/ 4.11-rc7 

You will probably also need the ACS patch. This will depend on your kernel version but if the patch applies then it should work.

* [ACS Patch](https://level1techs.com/sites/default/files/f/a.patch)
* [How to patch your kernel](https://superuser.com/questions/324968/how-do-i-apply-a-patch-to-my-linux-kernel)
* [If you’re using Debian use this guide](https://www.debian.org/releases/jessie/i386/ch08s06.html.en)
* [How to use multiple cores while compiling Kernels in Debian](https://itbusters.wordpress.com/2013/02/07/how-to-build-debian-kernel-using-multiple-cores/)

If your IOMMU groups look this this then you need the ACS patch or to move your GPU to another slot.  Radeon R9 290/290X is the GPU I want to use for my gaming VM, 
```
IOMMU group 2
	00:03.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1452]
	00:03.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:1453]
	00:03.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:1453]
	09:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP107 [GeForce GTX 1050] [10de:1c81] (rev a1)
	09:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fb9] (rev a1)
	0a:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii XT / Grenada XT [Radeon R9 290X/390X] [1002:67b0]
	0a:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii HDMI Audio [Radeon R9 290/290X / 390/390X] [1002:aac8]
```

This is what you want it to look like.

```
IOMMU group 15
	0a:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii XT / Grenada XT [Radeon R9 290X/390X] [1002:67b0]
	0a:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii HDMI Audio [Radeon R9 290/290X / 390/390X] [1002:aac8]
```

## ACS Override Patch Notes
[Resource #1](http://vfio.blogspot.com/2014/08/vfiovga-faq.html)


After you apply the ACS Override Patch you'll need to update your GRUB. To include pcie_acs_override=downstream.

AMD Example
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet amd_iommu=on pcie_acs_override=downstream"
```

You then need to updade your grub again.
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

Then reboot.

