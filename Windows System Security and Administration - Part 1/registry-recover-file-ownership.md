# Use The Windows Registry To Recover The Ownership Of Files
In Windows, file permissions can restrict access to specific files and folders, preventing one account from accessing another account's data. However, if you need to access files or folders that you lack permission to open, and your account has administrative privileges, you can 'Take Ownership' of the file or folder. This action grants you full access


## Tasks
- In a Windows VM, create two user accounts, both with local administrator privileges
- Using account 1, create a text file in a folder on the C: drive
- From an elevated command prompt, use takeown.exe to take ownership of the file
- Login using account 2 and try to access the file



## Practical Approach
1. 
