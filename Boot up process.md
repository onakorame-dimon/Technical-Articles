# System Boot up Process

Power-On and CPU Reset
When you press the power button, the power supply (PSU) energizes the system.
The CPU receives power and resets itself.
Upon reset, the CPU starts execution at a fixed memory address called the reset vector.
The CPU always starts execution from a predefined memory address called the reset vector. 


BIOS/UEFI Execution
When the CPU powers on or resets, it does not know anything — not even where RAM is or where the OS is.
It’s hardwired to start executing code at a specific address, the reset vector.

The memory address the CPU jumps to after reset (the reset vector) is mapped to a location in the BIOS firmware. 
So the CPU starts executing BIOS instructions from there.

The BIOS/UEFI is firmware stored in non-volatile memory (ROM/flash) on the motherboard.

The CPU begins executing BIOS instructions:
Runs POST (Power-On Self-Test) to check RAM, CPU, GPU, etc.
Initializes low-level hardware including I/O devices (keyboard), storage devices (disks), processor settings (CPU),  chipset, buses, and most importantly, system memory (RAM).
Enumerates bootable devices (HDD, SSD, USB, etc.)
Loads bootloader code from the configured boot device 

BIOS: usually reads the first 512 bytes of the boot device — the MBR (Master Boot Record) — into RAM at a known location (like 0x7C00).

UEFI: reads the EFI bootloader file (like \EFI\BOOT\bootx64.efi) from the EFI System Partition (ESP), and loads it into RAM using UEFI runtime services.

Bootloader Phase
The CPU reads the instruction on BIOS/UEFI to load the bootloader (like GRUB on Linux systems) into RAM.

The bootloader runs and:
Loads the Linux kernel (and optional initramfs) from disk into RAM.
Prepares the kernel command line (parameters).
Switches the CPU from real mode to protected mode (or long mode on x86\_64). For more advanced CPU stuffs
Passes control to the kernel entry point.

Kernel Initialization
The Linux kernel starts executing and it:
Initializes hardware drivers.
Mounts the root filesystem.
Starts the first user-space process which is  responsible for starting all other processes. (e.g., SysVinit or systemd).

Init System and User Space
 The init system (e.g., systemd) launches:
	Essential services (networking, login, etc.)
	User-defined services
	
At this stage of the boot process, the system enters a fully operational multi-user state, where core services are running and user interaction is enabled — either through command-line terminals or a graphical interface. 
This marks the system’s readiness for general use.
