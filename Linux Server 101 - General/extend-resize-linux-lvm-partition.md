# Extend And Resize LVM Partition In Linux
Resizing the file system size is an important task of the Linux administrator. Logical Volume Manager (LVM) helps to increase and reduce the file system size


## References
- [How to Extend LVM Partition with lvextend Command in Linux](https://www.linuxtechi.com/extend-lvm-partitions/) by Pradeep Kumar on LinuxTechi


## Tasks
- Use 'df' command to determine the used and available disk space for '/home/' partition
- Check if free space is available in the volume group using 'vgdisplay' command
- Use 'lvextend' command to increase the size of '/home/' partition by 2GB
- Resize the '/home/' partition size using 'resize2fs' command


## Benchmarks
- Use 'df' command and verify the size of '/home/' is extended by 2 GB


## Practical Approach
1. 
