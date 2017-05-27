# Linux Installation and Initial Configuration

### Steps of Installing the Linux Software
1. Reparetition your hard drives in order to allocate space for Linux
2. Boot the linux installation medium, e.g. a bootable CD-ROM
3. Run **fdisk** under Linux to create Linux partitions
4. Run **mkswap** to Swap Spaces
4. Run **mke2fs** to create Linux filesystems
5. Install the Linux software and configure it
6. Either install the *LILO bootloader* on your hard drive, or ceate a boot floppy in order to boot you new Linux system.

Most of the steps are likely to be automated for you by the installation procedure (or at least integrated into it)

### Drives and Partitions Under Linux
1. Windows drives and partitions
    - Floppy drives aer referred to as A: and B:
    - hard-drive partitions are named C:, D:, etc.
2. Linux Drives and partitions
    - The naming convention is quite different
    - Linux device drives found in the directory */dev*
    - Linux device drives are used to communicate with devices on your system, e.g. hard drives, mice, etc. If you have a mouse on your system, you might access it through the driver */dev/mouse*
    - */dev/hda1* ~ */dev/hda4* : Most systems, of course do not have four primary partitions, but the names */dev/hda1* ~ */dev/hda4* are still reserved for these partitions, they cannot be used to name logical partitions.
    - logical partitions can be named consecutively starting with */dev/hda5*

### Creating Linux Partitions with the command *fdisk*
1. In general, you need to create at least one partition for the Linux software itself and another partition for swap space.
2. *fdisk drive* : *drive* is the Linux device name of the drive to which you plan to add partitions. The default drive if you don't specify one is */dev/had* (the first IDE drive)
    - e.g. # fdisk /dev/sda: means you want to run *fdisk* on th efirst SCSI disk in your system
3. After running *fdisk drive*, *fdisk* will wait for you to input a command, the list of the options include:
    - *a*: toggle a bootable flag
    - *d*: delete a partition
    - *l*: list know partition types
    - *m*: print this menu
    - *n*: add a new partition
    - *p*: print the partition table
    - *q*: quit without saving changes
    - *t*: change a partition's system id
    - *u*: change display/entry units
    - *v*: verify the partition table
    - *w*: write table to disk and exit
    - *x*: extra functionality (experts only)

### Creating Swap Space
1. **mkswap -c name-of-swap-partition** : used to prepare a swap partition, *-c* option tells *mkswap* to check for bad blocks on the partition when creating the swap space.
2. **swapon name-of-swap-partition** : after formating the swap space, you need to enable it for use by the system.

### Create the Filesystems
1. Before you can use you Linux partitions to store files, you must create filesystems on them. (similar to formatting a partition in Windows)
2. Several types of filesystems are available for Linux, eash filesystem type has its own format and set of characteristics (such as filename length, maximum file size, etc.)
    - Second Extended FileSystem (**ext2fs**): the most common used filesystem type
    - **mke2fs -c name-of-partition** : create an **ext2fs** filesystem on the partition

### Install the Linux software
1. Many distributions have a self-contained program that steps you through the installation
2. on other distributions, you have to **mount** your filesystem in a certain subdirectory ( e.g. */mnt*) and copy the software to them by hand. 


### Creating the Boot Floppy or Installing LILO
1. Boot Floppy
    - Every distribution provides some means of booting your new Linux system after you have installed the software
    - In many cases, the installation preocedure suggests you create a boot floppy, which contains a linux kernel configured to use your newly created root system.
    - in order to boot Linux, you could boot from this floppy, control in transferred to your hard drive after you boot.
    - on other distributions, this boot floppy is the installation floppy itself.
2. LILO
    - LILO is a program that resides on your drive's master boot record, it boots a number of operating systems, including Windows and Linux, and allows you to select to which boot at startup time. 

### Post-installation Procedures
1. creating a user account
2. getting online help
3. editing **/etc/fstab**,  which describes your filesystem. Edit this file to sepecify the direction **/** is mounted to which partition.
4. Shutting Down the system
    - You should never reboot or shut down your linux system by pressing the reset switch or simply turn off the power, as with most unit systems, linux caches disk writes in memory, therefore, if you suddenly reboots the system without shutting down cleanly, you can corrupt the data on your drives. 
    - To shut down the system from a terminal session, sign in or **su** to the "root" account. Then type **/sbin/shutdown -r now**. It may take several moments for all processes to be terminated, and then Linux will shut down. The computer will reboot itself.