# Use The Windows Registry To Restrict The Permissions Of Untrusted User Accounts
Windows contains numerous, powerful utilities used regularly by system administrators, which are also commonly used maliciously by adversaries to reduce the likelihood of detection. To prevent Living-off-the-Land (LOTL) attacks, it is common practice to prevent regular user accounts from being able to execute critical utilities. One method of doing this is by utilizing the 'DisallowRun' registry key


## References
- [Block Applications ( Programs ) from running using the registry - Windows Tutorial](https://www.youtube.com/watch?v=l6-Suw2RNv8) by XunileConsulting on YouTube


## Tasks
- Set up a local administrator account and a user account on the VM
- Use the 'Registry Editor' application on the Windows VM (this is installed by default on Windows)
- Research and identify the path for the 'DisallowRun' registry key (you may need to create it if it does not exist)
- Prevent the usage of cscript.exe
- Prevent the usage of wscript.exe
- Prevent the usage of mshta.exe
- Prevent the usage of cmd.exe
- Prevent the usage of powershell.exe


## Benchmarks
- Validate that the local administrator account can use cscript.exe, wscript.exe, mshta.exe, cmd.exe, powershell.exe
- Validate that the standard user account cannot use cscript.exe, wscript.exe, mshta.exe, cmd.exe, powershell.exe


## Practical Approach
1. Create a standard user account on a Windows 10 VM. Run the following commands in Command Prompt with admin privileges
   ```
   net user StandardUser pw123 /add
   ```
   By default, newly created accounts are standard users and added to the Users group. Verify the new account is created using
   ```
   net localgroup Users
   ```
2. Editing the registry requires admin privileges. If the user is logged in as the StandardUser, editing the registry would then prompt the user for the admin password, and any changes to the registry would then by default fall under the admin account and not the StandardUser's account. To solve this, open PowerShell and run
   ```
   whoami /user
   ```
   This will show the SID of the currently logged in user. Alternatively, the following command can be used to view all the users' SID
   ```
   Get-LocalUser | Select-Object Name,SID
   ```
   ![image](https://github.com/user-attachments/assets/ebc81933-2c29-4582-ba33-eba0d844a851)

3. Open the Registry Editor and navigate to `HKEY_USERS`. Look for the StandardUser's SID (without the `_Classes` ending), and navigate to `Software\Microsoft\Windows\CurrentVersion\Policies`. If the `Explorer` key does not exist, right-click on `Policies`, select `New > Key`, and name it `Explorer`
4. To create the `DisallowRun` key, right-click on the Explorer key, select `New > Key`, and name it `DisallowRun`. Go back to the `Explorer` key. Right-click in the right-hand pane, select `New > DWORD (32-bit) Value`, and name it `DisallowRun`. Double-click on `DisallowRun` and set its value to 1
   ![image](https://github.com/user-attachments/assets/2d2eab72-6faa-4e8b-82fe-279008d1b839)

5. To add applications to be blocked, Navigate back to the `DisallowRun` key you created. Right-click in the right-hand pane, select `New > String Value`, and name it 1. Double-click 1 and enter the name of the first application to block (cscript.exe). Repeat this process for the following applications: wscript.exe, mshta.exe, cmd.exe, powershell.exe. Each application should have its own string value (e.g., 2, 3, 4, etc.).
   ![image](https://github.com/user-attachments/assets/ef0d779d-629a-482e-8711-3e704ed4c292)

6. To validate the proper access, login as the local admin and attempt to execute each application (cscript.exe, wscript.exe, mshta.exe, cmd.exe, powershell.exe) using `Win + R` and inputting the names of each application without the .exe extension
7. Then login as the StandardUser and execute each application (cscript.exe, wscript.exe, mshta.exe, cmd.exe, powershell.exe). All access should be denied
   ![image](https://github.com/user-attachments/assets/5edc7382-9b8b-431a-b662-9a32bbc70d44)
