## 283 Assignment 1

System 1: MacBook Air 2020 with an M1 chip
Failed trials: As stated in the video, I went ahead with the combination of GCP, Nomachine without much experience or proper research. Assigned 4 GB RAM, 20GB HDD space to save the costs. Then, realized there are no ways to implement nested virtualization in this(there might be a way that I’m not aware of).  

System 2, successful installation: 
As the VirtualBox, VMware Fusion, does not yet possess standard versions for the M1 chip model. I opted to find a Windows 10 device with Intel core i5 processor and to use VMWare Workstation 16.0. 

Steps: 
1. Download Ubuntu 21.10 and set it up with as much as RAM, Storage. I could assign only 3 GB Ram and 128 GB HDD memory. 

2. As the linux source code is used in every module, I forked the source code from the provided link.
https://github.com/torvalds/linux

3. Then, moved the cmpe283-1.c , Makefile into the Linux source folder. Created a 283_File just to be on the safer side and not confuse.

4. Building the kernel/make, ran into numerous errors for not having the required libraries: Bison, Flex, libssl-dev,, libelg-dev, etc, which are resolved using 
 - sudo apt-get install python-pip python-dev libffi-dev libssl-dev libxml2-dev libxslt1-dev libjpeg8-dev zlib1g-dev
 - Sudo apt-get install libncurses-dev
 - Sudo apt-get install libssl-dev

5. Resolving all these issues, checked the menuconfig and the relevant version match. 
- make modules
- sudo make install

6. Resolve the License error with MODULE_LICENSE("GPL v2"); 
and then
- make

7. Loading the module inside the kernel
- sudo insmod cmpe283-1.ko

8. Check if kernel module is loaded properly
- lsmod | grep cmpe283-1

9. Finally, check for the execution and the print
- dmesg

