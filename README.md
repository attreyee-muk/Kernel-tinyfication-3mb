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

