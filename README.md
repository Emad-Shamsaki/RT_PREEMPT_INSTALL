# RT_PREEMPT_INSTALL
RT_PREEMPT_INSTALL
Check the kernel to be preempt-rt:

```bash
uname -v
```
    
if not preempt-rt:

Step 1: Prepare Your System
1.	Update Your System:
```bash

sudo apt update && sudo apt upgrade -y
```

3.	Install Required Packages: Install necessary build tools and dependencies:

```bash
sudo apt install build-essential libncurses-dev bison flex libssl-dev libelf-dev git
```
________________________________________
Step 2: Download the Kernel Source
1.	Navigate to a directory where you want to download the kernel sources:
```bash
mkdir ~/kernel-rt && cd ~/kernel-rt
```
3.	Download the Linux kernel source:
```bash
wget https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.5.tar.xz
```
5.	Extract the kernel source:
```bash
tar -xvf linux-6.5.tar.xz
cd linux-6.5
```
________________________________________
Step 3: Download and Apply the PREEMPT-RT Patch
1.	Find the corresponding PREEMPT-RT patch version for your kernel: Visit the PREEMPT-RT Patch repository and choose the correct patch for your kernel version.
2.	Download the PREEMPT-RT patch:
```bash
wget https://mirrors.edge.kernel.org/pub/linux/kernel/projects/rt/6.5/patch-6.5.2-rt8.patch.xz
```
4.	Apply the patch:
```bash
xzcat patch-6.5.2-rt8.patch.xz | patch -p1
```
________________________________________
Step 4: Configure the Kernel
1.	Load the default configuration:
```bash
make olddefconfig
```
3.	Enable PREEMPT-RT: Open the kernel configuration menu:
```bash
make menuconfig
```
  Navigate to "General setup" → "Preemption Model".
  Select "Fully Preemptible Kernel (RT)".
________________________________________
 step 5 .  Dependencies
Ensure required dependencies are installed:
•	Tools like gcc, make, libncurses-dev, and patch must be available.
•	Install these with your package manager:
```bash  
sudo apt-get install build-essential libncurses-dev bc
```
________________________________________

step 6. Build and Install the Kernel
After configuring:
```bash  
make -j$(nproc)
sudo make modules_install
sudo make install
```
________________________________________

Step 7: Update Bootloader
1.	Update the GRUB configuration:

```bash  
sudo update-grub
```
3.	Reboot your system:

 ```bash   
 sudo reboot
```
_____________________________________
Step 8: Verify Installation
1.	After reboot, check the kernel to ensure you’re running the PREEMPT-RT kernel: 

 ```bash   
uname -v
```
check the version

 ```bash   
 uname -r
```
