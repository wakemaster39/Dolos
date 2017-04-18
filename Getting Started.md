# Getting Started

Before attempting to follow this guide, you will need to confirm you meet the minimum requirements as well as have a couple of files downloaded and ready to go. This will hopefully save you from throwing anything in frustration when you can't get your system to boot.

## Minumum System Requirements
* A cpu and motherboard that support virtualization. This is relatively self explainitory that your system you are trying to virtualize supports it. Determining if your supports it is another story.
  * Intel based systems: [Intel Ark](https://ark.intel.com/) is a great solution. Find your search and find you CPU and ensure it supports Intel® Virtualization Technology for Directed I/O (VT-d). *Note: VT-d and VT-x are no the same thing, ensure if supports VT-d*
  * Amd based systems: Find your product using AMDs [search](http://products.amd.com/en-us/search). Once you have found your product, verify it supports AMD Virtualization.
  * Any System Running Linux: If your system is running linux, you can run the following command to determine if your cpu support virtualization `grep "vmx\|svm" /proc/cpuinfo` if there is any output, then you are good to go. If the return is blank, then your system does not support it
* 6 GB of ram: This gives 2 gb of ram to the host and 4 GB to the guest. This is about as limited as you can get and your system will not be running at optimal efficency. 16 GB is the minimum recommended to proceed with this setup.
* 256 GB of free disk space:

## Recommended Minimum System Specs 
* 16 GB of ram: Web browsers are memory hungry, operating systems are memmory hungry. Just about everything you will do will want and benefit from more memmory. 16GB allows 4GB to the host and 12 to the VMs. Under certian work loads this will still be a bottle neck, but nothing that isn't managable. 
* CPU with 4 cores minimum: More CPUs the better. With two operating systems running, you have more overhead to manage and the ex
* CPU with hyperthreading: A CPU such as an i5-6600K is a great CPU for pure gaming. But when multiple operating systems are involved that are not communicating when scheduling tasks and which processes should take CPU priority, having those extra logical threads will make a bigger difference than you would think.
* Two storage devices: The ability to delete a hard drive freely and not care about any of the data on it or if you mess it up is really a large asset. This will let you experiment freely knowing that if you mess up, it costs you nothing and you don't need to be careful fixing it.
* A second internet connected device with a screen big enough to comfortably read and ~100 MB of free storage space: While not a requirement you will want this. Reading this guide, googling solutions are incredibly difficult to do while your system is in a broken state. Having a second device handy will relieve a lot of frustration. It also has the added benefit that you can install the host on a second drive before you delete your currently working operating system. 
* Two monitors: While not nessecary, it is nice to be able to have you host and your guest visualized on two seperate screens side by side. This is especially useful if you plan on doing GPU passthrough.

## Recommended System Specs
* 32 GB of Ram: Allows of plenty of ram for the host, main guest and multiple other little systems you will likely spin up as you start playing more.
* 6 or 8 core CPU: This allows giving 2 cores and 2 logical hyperthreaded to the host and have less resource sharing between the host and the VMs.
* 2 NVME or VNAND SSD drives: The performance benefits of a good SSD are hard to ignore. You will be much happier with your overall performance if you can keep all OS data on a SSD based storage device.


## Before you Start
Before you start this process, you will need to make your you have the following ready to go:
* A working and tested system: You will want to make sure your system currently boots and is working order. Finding out you had faulty hardware after days or search for why your system won't post or boot and blaming this guide the entire time is a sure way to never want to attempt it again.
* A copy of your motherboard manual: Either downloaded to the second device or a physical copy. Search where BIOS options is always easier in a manual than aimlessly clicking different menus and hoping you stupid across it.
* If second device is battery powered, a full battery and some entertainmenet downloaded: A device shutting down at an inconvient moment really sucks and there will be some down time as different operating systems install and allocate resources.
* License keys or method to access them to all programs you wish to install: Being able to install your software on your new virtualized system is always nice and if you just wiped your existing working system then it will be rather difficult to recover those keys again.
* This guide downloaded to your second device: If you are following this, might be helpful to read it when you run into trouble
* No forseeable reason to need your computer for the next week: This process is not gaurenteed or straight forward. If you start down this path thinking it will take an afternoon and you have a important test, work project or life issue that you can't do without a working system, you might want to wait until your schedule is clear. Murphy's law will very much gaurentee that everything will go wrong in this situation.