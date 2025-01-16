# Create A Disk Partition In Linux
System administrators have to deal with a plethora of issues when managing disks. By understanding the filesystem, you will have increased control over your environment


## References
- [How to Grow an ext2/3/4 File System with resize2fs](https://access.redhat.com/articles/1196353) by Red Hat Customer Portal


## Tasks
- Setup a Linux VM
- Create a disk partition using commandline utilities
- Mount the newly created disk partition
- Resize a disk partition
- Delete a disk partition


## Practical Approach
1. In this task, Lubuntu VM in VirtualBox is used
2. It is recommended to add a new virtual hard disk in Lubuntu rather than use the existing one to avoid disk issues. First, open the Settings of the Lubuntu VM <br>
   ![image](https://github.com/user-attachments/assets/7be78c34-90df-454d-8e25-9a3feb69eefa)
3. Click the Add Hard Disk icon and select Create a new disk <br>
   ![image](https://github.com/user-attachments/assets/770bc331-4077-4530-ad77-8f07196470b1)
  
4. Select the disk file type as VDI (VirtualBox Disk Image) and click Next <br>
   ![image](https://github.com/user-attachments/assets/6614f6be-9f67-4730-9ec4-e5e658672e78)

5. Choose the disk size and click Create <br>
   ![image](https://github.com/user-attachments/assets/1d3067a7-a0e5-4b79-885b-8b7b837db204)
   <br>
   ![image](https://github.com/user-attachments/assets/8d6515e5-d9a7-44cf-923c-9a45b61f8fd6)
   <br>
   The new virtual hard disk can be used for this partitioning task without affecting the main disk

6. To create a disk partition in CLI, start Lubuntu VM and open a terminal. Then identify the new disk using
   ```
   sudo fdisk -l
   ```
   Look for the newly added disk (e.g., `/dev/sdb`)
7. Start the `fdisk` utility for the disk
   ```
   sudo fdisk /dev/sdb
   ```
   Enter `n` to create a new partition, select `primary` or `default` options. Press Enter for default sector values, and enter `w` to write changes to disk and exit
8. Format the partition as ext4
   ```
   sudo mkfs.ext4 /dev/sdb1
   ```
9. To mount the newly created disk partition, first create a mount point by creating a directory to mount the partition
   ```
   sudo mkdir /mnt/newdisk
   ```
10. Mount the new partition to the directory
    ```
    sudo mount /dev/sdb1 /mnt/newdisk
    ```
11. Verify the mount by checking if the partition is mounted
    ```
    df -h
    ```
12. (Optional) The mount can be made persistent by editing the `/etc/fstab` file
    ```
    sudo nano /etc/fstab
    ```
    Add the following line, then save and exit the editor
    ```
    /dev/sdb1 /mnt/newdisk ext4 defaults 0 0
    ```
13. To resize the disk partition, unmount the partition if it is mounted
    ```
    sudo umount /mnt/newdisk
    ```
14. Then start `fdisk`
    ```
    sudo fdisk /dev/sdb
    ```
    To delete the partition, press `d` to select the partition (e.g., `/dev/sdb1`) and confirm. To recreate the partition with a larger size, press `n` and adjust the size as required. Then press `w` to write changes
15. Resize the ext4 filesystem using
    ```
    sudo resize2fs /dev/sdb1
    ```
16. To delete a disk partition, unmount it first if it is mounted
    ```
    sudo umount /mnt/newdisk
    ```
17. Start `fdisk`
    ```
    sudo fdisk /dev/sdb
    ```
    To delete the partition, press `d` and select the partition (e.g., `/dev/sdb1`). Then write changes by pressing `w`
18. Verify the deletion by listing the partitions to confirm
    ```
    sudo fdisk -l
    ```


