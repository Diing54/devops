
2025-02-16 16:51

Level : 

Tags :[[linux]]

# linux boot process

## Intro
When you turn on a computer or restart it, it must load an operating system. This process is called the boot process.
## BIOS
In the past before transitioning into boot loaders, BIOS (Basic Input and Output Service), was being used. This was a code that was stored in a non-volatile memory such as ROM, EEPROM or flash memory. When a PC is turned on, this code is executed and performs a power on self test (POST) to check the machine. This code also determines the boot drive from the available removable/fixed storage and loads the first sector from the Master Boot Record (MBR) on that drive eg hard drive/ ssd or usb stick or DVD/CD


## 1. BIOS/UEFI Initialization
- The computer's firmware (BIOS or UEFI) performs a Power-On Self Test (POST) to check hardware (RAM, CPU etc)
- BIOS/UEFI locates the boot loader from the disk defined in the boot order 
## 2. Bootloader (GRUB) Execution
- This is located in the MBR (Master Boot Record) for BIOS or EFI System Partition for UEFI.
- The common boot loader is GRUB
- A boot menu is then displayed if configured allowing the user to select different kernels or OS
- A Linux kernel is loaded into memory if selected
- The kernel parameters are passed from its configuration file
## 3. Linux kernel Initialization
- After the kernel which is a compressed image is loaded into memory, It extracts itself and initializes hardware drivers like CPU,memory 
- Then the root filesystem is mounted from the partition specified by the bootloader
- The init process (PID 1) starts from the initial RAM disk
## 4. initrd or initramfs (Initial RAM Disk)
- Temporary filesystem is loaded into RAM
- Once the root filesystem is accessible, the real root is mounted and the temporary one is discarded



## References
