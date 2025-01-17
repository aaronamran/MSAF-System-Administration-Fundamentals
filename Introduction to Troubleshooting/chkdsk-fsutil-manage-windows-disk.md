# Use 'chkdsk' And 'fsutil' To Manage The Disk On A Windows Computer
System administrators must monitor the health and performance of disks on a computer. This may involve performing activities like routine disk scans, repairing file system errors, check disk integrity, etc.
<br>
The goal is to use native command-line tools on a Windows computer for disk management. Tools like 'chkdsk' and 'fsutil' will be used to manage the disk on a VM and a USB.

## Tasks
- Lab Setup
  - Set up a Windows VM
  - Create a local user and add the user to the 'local administrator' group
  - Format a USB drive with NTFS. Add and delete some files from the USB after formatting it
  - Connect the USB to the VM
- Use 'chkdsk'
  - Check the disks for errors
  - Display the name of each file on disk as the scan progresses. You can also store the output in a log file
  - Fix the errors present on the disk, if any
- Use 'fsutil'
  - List all the volumes on a system
  - List a volume's storage allocation information
  - Display information about the file system on a volume
  - List and view information about the different drives on the VM
  - Query the status of the self-healing state on the VM's disk and USB
  - Enumerate the entries in a volume's corruption log
  - Query the status of the dirty bit on the VM's disk
  - Query the status of the dirty bit on the USB
  - Query the status of the USN journal on the VM's disk
  - Query the status of the USN journal on the USB
  - If the USN journal is active, perform the following task: make some changes to a text file and view the USN data for it


## Benchmarks
- Show the results obtained using 'chkdsk' and its command switches, for the VM disk and USB
- Show that you have identified disk errors and fixed them
- Show that you can view the names of each checked file
- Show the results obtained using 'fsutil' and its command switches
- Show that you can view information about the volume and file system on the VM disk and USB
- Show that you can view information about the file system journal, state of the dirty bit and status of self-healing property



## Practical Approach
1. 
