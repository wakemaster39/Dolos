virtualization setup:

https://bbs.archlinux.org/viewtopic.php?id=220862
http://unix.stackexchange.com/questions/152291/can-i-move-a-running-application-to-a-different-x-server

https://scottlinux.com/2016/08/28/gpu-passthrough-with-kvm-and-debian-linux/
https://scottlinux.com/2016/03/21/enable-hyper-v-enlightenments-in-kvm-for-better-windows-vm-performance/
https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=597158
http://blog.vmsplice.net/2011/04/how-to-pass-qemu-command-line-options.html
https://www.reddit.com/r/VFIO/comments/4kuvxs/setting_up_a_kvmqemu_vga_passthrough_gaming_vm/

update-grub2 instead of update-grub	

<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
<qemu:commandline>
<qemu:arg value='-cpu'/> 
<qemu:arg value='host,kvm=off,hv_relaxed,hv_spinlocks=0x1fff,hv_vapic,hv_time,hv_vendor_id=whatever'/>
</qemu:commandline>

Nvidia graphics: [10de:1b80]
Nvidia audio: [10de:10f0]

have to manually patch synergy to make it work with OPENSSL 1.1.0 as of version 1.8.8 stable
Synegry pull request #5746


outstanding issues:
- Multiple CPUs are not being used in windows VM
    Need to fix topology and move all cores from sockets to core
- Audio needs to be passed from VM to host to output
- Logitech drivers for keyboard/mouse/headset
- benchmark


If Audio Delay:
https://lists.gnu.org/archive/html/qemu-devel/2015-09/msg03336.html

possible audio outputs:
https://bbs.archlinux.org/viewtopic.php?id=215098
https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF#Passing_VM_audio_to_host_via_PulseAudio

Problem: Getting Audio to Work Getting audio in your virtual machine to work is tricky. The easy way, for me, was to put my USB DAC/Amp (audio card) on the USB switcher hub I purchased. However, this meant I could only listen to the audio from my Linux host or my Windows VM. Unsatisfied, I decided to get the virtual sound card working. Windows 10 audio output works very well with the Intel HDA audio card (listed as ich9 in virt-manager). However, pulseaudio does not work well with virt-manager. By default, virt-manager runs VMs as the root user; thus it attempts to send the audio from the VM to the root user's pulseaudio server, which shouldn't ever exist unless you're mad. We have to tell libvirt to use our user's pulseaudio server and to use pulseaudio. To do this, manually edit your domain using sudo virsh edit [name of win10 vm]. Add the xmlns tag to the <domain> tag and add the appropriate environment variables:
<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'\>
...
<qemu:commandline>
<qemu:env name='QEMU_AUDIO_DRV' value='pa'/>
<qemu:env name='QEMU_PA_SERVER' value='/run/user/1000/pulse/native'/>
</qemu:commandline>
</domain>
If your UID is not 1000, (IE you are not the only user on the system), change that number to your UID. After that, you need to double check that your pulseaudio server is always running as your user. An easy way to make sure of this is to run systemctl --user enable pulseaudio.


Huge Pages
http://lifeisabug.com/kvm-virtualization-arch-linux-host-system-qemu-virtio-hugepages-systemd/


Windows 10 License Key Extraction:
http://www.techrepublic.com/article/how-to-install-windows-10-in-a-vm-on-a-linux-machine/


Best Practices:
https://www.ibm.com/support/knowledgecenter/linuxonibm/liaat/liaatbpkickoff.htm

Pulse audio anonymous feed
https://www.evonide.com/non-root-gpu-passthrough-setup/#Permissions_for_non-root_GPU_passthrough

