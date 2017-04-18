# Introduction

If you made it to this page, it is likely fair to say you have some idea what you are about to get into but likely don't have everything sorted out already. Maybe you were given this link by a friend and said you should check it out, or the SEO gods have blessed us and you found it by your favourite search engine. Either way, this is a good spot to lay everything out in the open. Lets talk about what this guide aiming to give you at the end, why you might want to do this and define a number of things so we can all speak and understand these concepts at the same level. 

## Definitions:
* Computer: We start easy here and hit the dictionary: a programmable usually electronic device that can store, retrieve, and process data (https://www.merriam-webster.com/dictionary/computer). For us, a computer is your collection of hardware. Your CPU, hard drives, motherboard. All that physical stuff you spent your hard earned money on.
* Operating System: Windows, iOS, Android, Debian. These are collections of software that are packaged together to provide a user with the ability to interact with the computer and a mechanism to interact with the computer hardware.
* Kernel
* Emulation
* MORE DEFINITIONS
* pass through
* native performace
* Metal: When we discuss metal, we will be talking about installing an operating system directly on the hardware. Your systems kernel will interact directly with the hardware.
* Virtual Machine: A virtual machine is an emulated set of computer hardware with an operating system installed on it. The end goal on this guide is to give you, the user, a mechanism to create and manage virtual machines in an easy and straight forward manner. 

## What to expect at the end

Assuming you have the minimum specifications (more on this later, but the key one here is 2 monitors and 2 graphics outputs (integrated GPU and dedicated GPU)), this guide will give you (most importantly) a working system. It will provide you with the means to quickly and easily create, modify and delete virtual machine. Pass specific devices to specific virtual machines and seamlessly interact between guest operating system and the host. 

Below is an image of one of the systems this guide was written around. On the left, you will see a host operating system running (at the time of writing) a testing version of Debian. On the right, is a virtualized windows 10 instance with a GPU passthrough to give native graphics performance. This layout is designed around giving optimal performance for gaming experiences while also having the advantages of a virtualized system to easily seperate different software into their own machines. Using [Syngery]()https://github.com/symless/synergy (more discussed later), the move and keyboard are easily able to traverse between the guest and host without. Copying and pasting the clipboard between the operating systems is supports and hopefully in the near future drag and dropping files between the different systems will also be enabled. 

** INSERT IMAGE HERE **

This is not the only layout possible, and infact is one of the easier ones. But it is also one of the most common layouts. This is a great building point to allow you to continue modifications and make your system suit your needs more completely.

## Relative Performance

This is one of those topics that will likely push peoples buttons and cause debate.This will continuously be changing as drivers are updated, modifications and improvements are introduced and new hardware is created. When the guide was being started, it was found that most sources (usually form posts) suggested that the performance impact would be negligible. Depending on what you care about, are interested in measuring and how much time you are willing to put into optimizing your system, you can likely make this true. As a general rule, assume you will take about a 10% performance hit over metal. This is assuming you follow everything laid out in the guide. 

There a plenty of reasons why you will take a 10% performance hit, but in general it will boil down to this: All design decisions and configuration settings are selected based on user experience and configuration difficultly. It may be possible to pull an extra 2-3% by extensive testing and changes, but the general user really won't notice if you are loosing a couple FPS while gaming or an operation takes an extra couple seconds to complete. As improved best practices are found that do not increase complexity, they will be incorporated into this guide. But it should be noted, you will never reach full native performace on a virtualized setup. If benchmark breaking results is your goal, it is suggested that you look elsewhere for a solution for that. 