
So when u start the computer, the processor immediately looks at a physical address 0xFFFFFFF0 for the bios code. This BIOS code is on a read-only memory in the firmware rom on the motherboard.

The BIOS then performs POSTs, looks for acceptable bootable media. The first 512 bytes is called the boot sector of a media, if this specific sector of the media is readable, then it is deemed as a bootable device. THIS IS GENERALLY THE MASTER BOOT PARTITION WORKS.

These 512 bytes contain the information about the computer's bios, and the last two bytes is 0x55AA, which is generally called the boot signature of the device. This number verifies that the boot sector is a "Valid boot sector". This allows the bios to find and execute boot code within it to initialize the booting process of the operating system. 

The bios then loads the 512 bytes in the memory address 0x007C00, and transfers program control to this address with a jump instruction to the processor

MASTER BOOT RECORD(MBR):

* **Boot Code(primary bootloader)**: The first 446 bytes are an executable program, whose sole purpose is to locate an active bootable partition on the hard drive and then load the volume boot record from the partition into the memory.

* **Partition Table**: The next 64 bytes consist of the partition table, which is basically the map of the hard disk, this tells you details about how your disk is partitioned 

The 446 bytes look for a special flag inside MBR's own partition table, basically the executable program scans the boot partition table of each media. There are basically boot indicators in partition table entries 



**REAL MODE**: All x86 architecture systems have an operating mode called the real address mode. The addresses in the real mode always correspond to real memory locations.

**PROTECTED MODE**: also called the protected virtual address mode, allows the OS to use features such as segmentation, virtual memory, paging, safe multitasking, designed to increase and operating system's control over an application software. The cpu generally runs on the protected mode in the process of general computation  



```text
Memory Map (x86 Real Mode)
Address       | Purpose
------------- | ---------------------------------------------
0x000000      | BIOS use only
0x000600      | Typically used by MBR
0x000800      | Reserved for MBR/BIOS
0x001000      | Boot loader             <- Boot sector entry point 0000:7C00
0x010000      | Protected-mode kernel  <- Bulk of kernel image
0x090000      | Kernel boot sector     <- Legacy boot sector
0x090200      | Kernel setup           <- Kernel real-mode code
0x098000      | Command line / Stack / Heap  <- For kernel real-mode use
0x09A000      | Reserved for BIOS EBDA
0x0A0000      | Reserved for BIOS
```

**0x000000** - Stores the codes for hardware initialization, BIOS variables and tables
BIOS variables are memory values that describe the hardware state or configuration. Examples would include ==memory size, system timer or clock data, and interrupt vectors( basically pointers to routines for hardware interrupts )==
**Interrupt vectors** are also called IVT( interrupt vector table ), and are located in the first 1kb memory(0x000-0x03FF).

**BIOS TABLES** - are structured memory areas that store hardware and boot info