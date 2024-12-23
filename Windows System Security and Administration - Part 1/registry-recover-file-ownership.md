# Use The Windows Registry To Recover The Ownership Of Files
In Windows, file permissions can restrict access to specific files and folders, preventing one account from accessing another account's data. However, if you need to access files or folders that you lack permission to open, and your account has administrative privileges, you can 'Take Ownership' of the file or folder. This action grants you full access


## References
- [takeown](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/takeown) by Microsoft


## Tasks
- In a Windows VM, create two user accounts, both with local administrator privileges
- Using account 1, create a text file in a folder on the C: drive
- From an elevated command prompt, use takeown.exe to take ownership of the file
- Login using account 2 and try to access the file



## Practical Approach
1. In Windows 10 VM, open command prompt as admin and use the following commands to create 2 accounts with local admin privileges
   ```
   net user account1 pw123 /add
   net user account2 pw123 /add
   net localgroup administrators account1 /add
   net localgroup administrators account2 /add
   ```
2. Logout from the current account and login with `account1`. Create a `testfolder` on the C: drive. Then create `sample.txt` in that folder
3. Use the `takeown` command to take ownership of the `sample.txt` file
   ```
   takeown /f "C:\testfolder\sample.txt"
   ```
   The `/f` flag specifies the file or folder to take ownership of. A confirmation message should appear after command execution
   ![image](https://github.com/user-attachments/assets/094c7e5b-a6bc-4244-a1ca-377e8ea2b927)

4. Logout and login as `account2` and try opening `sample.txt`. By default, `takeown` changes ownership but does not automatically grant permissions. So `account2` might not be able to access or modify the file unless it explicitly has permissions. However in this case, `account2` has permissions to access it, despite it belonging to `account1`
5. To take ownership of the file, run the same command while being logged in as `account2`
   ![image](https://github.com/user-attachments/assets/b3f32e1f-e70f-4276-beeb-937d8d4a322b)

   
   
   

