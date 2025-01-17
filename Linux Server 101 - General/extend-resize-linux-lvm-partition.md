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
1. Using Lubuntu VM installed in VirtualBox, launch a terminal. Identify the logical volume using the command
   ```
   df -h
   ```
   Identify the mount point for `/home/` and note its current size and usage
2. Verify the available space in volume group by using
   ```
   sudo vgdisplay
   ```
   Look for the Free PE / Size field under the volume group details. Ensure there’s at least 2GB of free space. If there isn’t, you will need to add a new physical volume (not covered here)
3. Extend the size of the logical volume `/home/` partition by 2GB
   ```
   sudo lvextend -L+2G /dev/mapper/<vg-name>-<lv-name>
   ```
   Replace `<vg-name>` and `<lv-name>` with the respective volume group and logical volume names for `/home/`. Use `lsblk` or `lvdisplay` to identify the correct paths
4. Verify the logical volume size has been extended
   ```
   sudo lvdisplay
   ```
   Look for the `LV Size` to confirm addition of 2GB
5. Resize the file system to utilize the newly extended logical volume
   ```
   sudo resize2fs /dev/mapper/<vg-name>-<lv-name>
   ```
   Replace `<vg-name>` and `<lv-name>` with the appropriate names for the `/home/` logical volume
6. Verify the updated disk usage of the `/home/` partition
   ```
   df -h
   ```
   Ensure the size of /home/ has increased by 2GB
