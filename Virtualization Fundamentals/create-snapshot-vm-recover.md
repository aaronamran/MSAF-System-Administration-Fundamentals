# Create A Snapshot Of A Virtual Machine To Recover The OS To A Safe State
Snapshots allow virtual machines (VMs) to revert to a previously saved state, making them invaluable for saving time. They are particularly useful during testing that might harm the VM or involve extensive configuration changes

## References
- [How to use snapshots in VirtualBox](https://www.techrepublic.com/article/how-to-use-snapshots-in-virtualbox/) by Jack Wallen on TechRepublic


## Tasks
- Deploy a virtual machine in VirtualBox or VmWare
- Take a snapshot of the VM
- Validate that you can successfully take the VM snapshot


## Practical Approach
1. Deploy a VM in VirtualBox. For the sake of this task, a Windows 7 VM would suffice
2. The VM snapshot can be created when the VM is either on, saved, or off.
3. In VirtualBox by default, the details of each VM are shown
   ![image](https://github.com/user-attachments/assets/118ea796-5c6b-407a-8fe4-7fde9585973b)
4. To go to snapshots, click on the details icon on a selected VM, and click Snapshots
   ![image](https://github.com/user-attachments/assets/bdfde373-f188-487f-9d9d-9afe2920cba2)
5. Click Take (camera icon) and name the snapshot and give some descriptions
6. To validate the snapshot, modify the VM by making a noticeable change, like creating a file on the desktop or installing any software
   ![image](https://github.com/user-attachments/assets/d8a89ae8-03fb-4fc0-8bb8-fdecd2c701ff)
7. To restore the snapshot, power off the VM and in the Snapshots tab, select the snapshot and click Restore
8. Start the VM after restoring the snapshot. The VM should return to its earlier state, and any changes made after the snapshot should be reverted
