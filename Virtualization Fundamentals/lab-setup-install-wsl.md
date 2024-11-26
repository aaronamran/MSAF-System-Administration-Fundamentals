# Lab Setup: Install Windows Subsystem For Linux
Windows Subsystem for Linux (WSL) is a compatibility layer for running Linux binary executables on a Windows operating system.

## References
- [How to install Linux on Windows with WSL](https://learn.microsoft.com/en-us/windows/wsl/install) by Microsoft

## Tasks
- Enable 'Windows Subsystem for Linux' on your Windows 10 machine
- Install Ubuntu via Microsoft Store
- Demonstrate that you can access Ubuntu shell and can create a new file in the 'home' directory


## Practical Approach
1. In a Windows 10 VM, open PowerShell as admin and run the following command to enable WSL:
   ```
   dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
   ```
   If WSL 2 is intended for usage, also enable the Virtual Machine Platform:
   ```
   dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
   ```
2. Restart the VM to apply the changes. An optional step is to set WSL 2 as Default:
   ```
   wsl --set-default-version 2
   ```
3. To install Ubuntu via Microsoft Store, search for Ubuntu (e.g. Ubuntu 22.04 LTS) and click Get or Install
4. Once installed, click launch or search for Ubuntu in the Start Menu and open it
5. On first launch, a user account and password will be created
6. The default directory is the `home` directory. Create a test file using
   ```
   touch testfile.txt
   ```
   Verify it is created using the `ls` command
