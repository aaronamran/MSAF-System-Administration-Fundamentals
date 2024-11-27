# Use The Windows Registry To Restrict The Permissions Of Untrusted User Accounts
Windows contains numerous, powerful utilities used regularly by system administrators, which are also commonly used maliciously by adversaries to reduce the likelihood of detection. To prevent Living-off-the-Land (LOTL) attacks, it is common practice to prevent regular user accounts from being able to execute critical utilities. One method of doing this is by utilizing the 'DisallowRun' registry key


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
2. Login as the StandardUser, open the Registry Editor and navigate to `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies`. If the `Explorer` key does not exist, right-click on `Policies`, select `New > Key`, and name it `Explorer`
3. To create the `DisallowRun` key, right-click on the Explorer key, select `New > Key`, and name it `DisallowRun`. Go back to the `Explorer` key. Right-click in the right-hand pane, select `New > DWORD (32-bit) Value`, and name it `DisallowRun`. Double-click on `DisallowRun` and set its value to 1
4. To add applications to be blocked, Navigate back to the `DisallowRun` key you created. Right-click in the right-hand pane, select `New > String Value`, and name it 1. Double-click 1 and enter the name of the first application to block (cscript.exe). Repeat this process for the following applications: wscript.exe, mshta.exe, cmd.exe, powershell.exe. Each application should have its own string value (e.g., 2, 3, 4, etc.).
5. To validate the proper access, login as the local admin and attempt to execute each application (cscript.exe, wscript.exe, mshta.exe, cmd.exe, powershell.exe) using `Win + R` and inputting the names of each application without the .exe extension
6. Then login as the StandardUser and execute each application (cscript.exe, wscript.exe, mshta.exe, cmd.exe, powershell.exe). All access should be denied
