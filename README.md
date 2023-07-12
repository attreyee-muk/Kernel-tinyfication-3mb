# Kernel-tinyfication-3mb 

![boot up gif](https://media.giphy.com/media/3o7btTODQcZhN6eLQs/giphy.gif)

Many developers and users of Linux Operating System sometimes look for small sized kernels which can boot up properly in their systems and also not hamper their work. 
Many embedded devices also need to be booted up using a kernel which takes minimal space and does all the functionalities since there is a memory constraint in these devices.

Linux Kernel provides us with a feature of customizing our own kernels the way we want to. 
The kernel which comes with Ubuntu installation is mostly of the size 9.9mb. Looking properly at it’s config file and the modules installed, we might find out that most of the memory is being filled up with modules and object files which we do not require at all. For example, we might not require driver modules for wireless devices which we do not use. 
We can very well not include these types of  driver modules in our kernel compilation and hence bring down the kernel size altogether.
Sometimes users or developers might also not need debugging facilities which are otherwise provided by the kernel. Debugging symbols, modules etc take up a lot of kernel space which can be simply avoided by the related options. 

I had been working on this project for six months and I have tried to bring down the Linux Kernel size from 9.9mb to 3mb. 
I downloaded the Kernel from https://www.kernel.org/ - version 6.1.2 stable release. 

While not many options have been changed in the ‘General Setup’ since most of them are required to boot up the OS, many options in Processor type and features have been decided upon. 
Since I have an AMD machine, most of the options of Intel processor support have been disabled except for those which are required by my computer.
Options like late microcode loading,MPS table support, cluster scheduler support,  5 level page table support etc which my machine does not need neither for better performance nor for general working has been disabled.
In memory management options, since I won’t need extra cpu performance with less number of tlb misses and huge tlb transparency , options concerned with those have also been disabled along with many other options.
Since I don’t plan on using Virtual Machines on my machine, I have also not included the option for VMs and virtio devices. 
My customized kernel doesn’t have support for those devices which I do not have and do not plan on getting. PCI devices , USB devices, SCSI support needed for particular machines can be found out using 
` lspci ` , `lsusb` and `lsscsi` commands. 
Looking at the outputs of these commands, most of the options given in the Device Drivers have been decided on. 
Since I believe that I won’t be doing some tasks which need high security, I have disabled the option given for Mitigating Speculative Execution Vulnerabilities , securityfs file system, different security models, support for calculating Diffie-Hellman public keys and other kernel hardening options. 
As I do not plan on doing kernel debugging using this particular kernel, I have disabled most of the kernel debugging options like Tracers, support for KASAN, fuzzing , debugfs, Stack backtrace support etc. 
While I only need support for etx4 file system, I have disabled all the other file system options. I do not plan on ext4 debugging and hence that option has also been disabled. 
For networking support, since I do not want to work much on networking and security using this kernel, many of the options are disabled here except for those which are necessary like wireless support and support for its networking stack and configuration API. 
These were the major areas where I focused on. Apart from these, there are many other options which also have been changed by me. 
