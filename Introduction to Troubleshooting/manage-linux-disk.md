# Manage The Disk On A Linux Computer
System administrators must be proficient in managing storage media using a variety of tools, GUI and command-line. Some minimal OS installations lack a graphical user interface. In that case, command-line tools can be used. Typically, disk management tools are installed by default


## Tasks
- Lab Setup
  - Set up a Linux VM
  - Create a user and include them to the sudoers group
  - Disable the media auto-mount feature. When a USB is attached to the VM, it must be mounted manually for use
- Manage disk using GUI tools (Manage the storage area of a USB. Create and format two small partitions)
  - Open the disk management utility available on your Linux VM (for example: 'disk utility' on Ubuntu, 'gparted' on Kali)ä
  - Ensure that you can view your USB on the disk management utility
  - Create a 1GB partition and format it as EXT4
  - Create another 1GB partition and format it as FAT
  - Mount both partitions
  - View both partitions on the File Browser and add some files to it
- Manage disk using CLI tools (Use either 'fdisk' or 'gdisk' for this task)
  - List the volumes attached to the VM
  - List the partitions on the USB
  - View the types of the partitions on the USB
  - Identify the mount points of the two USB partitions
  - View the files present in both partitions
  - Use 'mkfs' utility to format the FAT partition as EXT4. May need to unmount the partition for this task
  - List all the partitions on the USB
  - View the types of the partitions
  - Use 'mount' command to mount the USB partitions
  - In a USB partition, create a simple script file and modify the permissions to make it an executable
  - Unmount the USB, and mount it again as read-only
  - Attempt to modify the script file. You will be prevented from performing this task
  - Execute the script
  - Unmount the USB, and mount it again with the 'noexec' option
  - Attempt to execute the script. You will be prevented from performing this task
 
## Benchmarks
- Show the partitions created using a GUI tool
- Show that you can view the volumes on a VM, and existing partitions on a USB using command-line tools
- Show that you can reformat the file-system on a partition using command-line tools
- Show that you can mount a partition using various mount options (default, read-only, noexec) and manage the files on it
- Show all the executed commands and the results obtained


## Practical Approach
1. 
