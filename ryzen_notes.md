```
E: Package 'libvirt-bin' has no installation candidate
```
For me at least 'libvirt-bin' has been split into two packages on Debian Stretch.
https://lists.debian.org/debian-user/2016/11/msg00518.html
```
libvirt-daemon-system
libvirt-clients
```


Ryzen will need one of the later Linux kernels for best results.
I used the latest from https://www.kernel.org/ 4.11-rc7 

You will probably also need the ACS patch. This will depend on your kernel version but if the patch applies then it should work.

[ACS Patch](https://level1techs.com/sites/default/files/f/a.patch)
[How to patch your kernel](https://superuser.com/questions/324968/how-do-i-apply-a-patch-to-my-linux-kernel)

