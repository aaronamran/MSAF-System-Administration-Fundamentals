# Use Access Permissions And Rights To Prevent Unauthorized Users From Viewing A Folder That Contains Sensitive Materials
A Windows computer can support multiple users, each with dedicated local accounts. Users can log in remotely simultaneously or locally at different times. Access control restrictions for each user account can be configured using the Group Policy Editor. On a standalone machine, the Local Group Policy Editor is used for this purpose. For domain-level management, Group Policy settings are configured on the domain controller


## References
- [How to apply Local Group Policy settings to specific users on Windows 10](https://www.windowscentral.com/how-apply-local-group-policy-settings-specific-users-windows-10) by Mauro Huculak on Windows Central

## Tasks
- Set up a Windows 10 VM (Pro or Enterprise version)
- Create the different user groups
  - Login as the local administrator to create users and groups
  - Create a new user 'user1' and add them to the 'Finance' group
  - Create a new user 'user2' and add them to the 'Human Resources' group
  - Create a new folder named 'Confidential' in the C:\ drive
- Modify the access control settings for the 'C:\Confidential' folder
  - Only users of the 'Finance' group can access the 'Confidential' folder. Users of the 'Human Resources' group must not have access to the 'Confidential' folder
- Modify access control settings for powershell.exe
  - In the Windows Search bar, search 'gpedit.msc' to open the Local Group Policy Editor
  - In the Local Group Policy, find the folder 'Additional Rules'
  - In this folder, create a policy to disallow access to powershell.exe for users of 'Finance' and 'Human Resources' groups
- Test the settings
  - Login as the local administrator. Attempt to access the 'C:\Confidential' folder and open powershell.exe
  - Login as 'user1' of the 'Finance' group. Attempt to access the 'C:\Confidential' folder and open powershell.exe
  - Login as 'user2' of the 'Human Resources group. Attempt to access the 'C:\Confidential' folder and open powershell.exe
- Validatiom
  - Local administrator can access the 'C:\Confidential' folder and open powershell.exe
  - 'user1' can access the 'C:\Confidential' folder but cannot open powershell.exe
  - 'user2' cannot access the 'C:\Confidential' folder and cannot open powershell.exe

## Benchmarks
- Login as the local administrator
- Show the user accounts and groups on the machine
- Show that the local administrator can access the 'C:\Confidential' folder and open powershell.exe
- Show the security settings on the 'C:\Confidential' folder
- Show the access control settings in the local group policy editor for powershell.exe
- Login as 'user1'
- Show that 'user1' can access the 'C:\Confidential' folder but cannot open powershell.exe
- Login as 'user2'
- Show that 'user2' cannot access the 'C:\Confidential' folder and cannot open powershell.exe

|User           |C:/Confidential|PowerShell|
|---------------|---------------|----------|
|Local Admin    |Accessible     |Accessible|
|user1 (Finance)|Accessible     |Blocked   |
|user2 (HR)     |Denied         |Blocked   |


## Practical Approach
1. Login to the Windows 10 VM using the local admin account
2. To create groups, open `Computer Management` by pressing `Windows Key + X` and select `Computer Management`. Navigate to `Local Users and Groups > Groups`. Then create two groups: `Finance` and `Human Resources`
3. To create users, navigate to `Local Users and Groups > Users`. Then, create two users and add them to each group: `user1` (add to the Finance group) and `user2` (add to the Human Resources group)
   ![image](https://github.com/user-attachments/assets/241dbbd0-f5aa-4305-b7f9-688919592ad0)
4. To configure folder permissions, create a folder named `Confidential` in the `C:/` drive
5. Right-click on the `Confidential folder > Properties > Security tab`. Remove `Users and Authenticated Users` from the access list. Add the `Finance` group and grant `Full Control` to the `Finance` group. Add the `Human Resources` group and deny `Read & Execute` permissions for the `Human Resources` group
   ![image](https://github.com/user-attachments/assets/b6cfad18-4714-4a33-b854-a77f441e85ab)
   <br/>
   ![image](https://github.com/user-attachments/assets/7fe95534-29ba-49f9-b23a-89bfa4fa5631)

6. The typical method of restricting access to PowerShell, using `gpedit.msc` to use Local Group Policy Editor and going to: `Computer Configuration > Windows Settings > Security Settings > Software Restriction Policies` and right-clicking `Software Restriction Policies > Create New Policies` will restrict everyone including the admins from using PowerShell
   ![image](https://github.com/user-attachments/assets/9254db14-3e62-4474-9d1e-ead92cd44fe9)

7. To specifically restrict access only for users, press `Win + R` and enter `mmc.exe` to open Microsoft Management Console. Then click on `File > Add/Remove Snap-in...`. Select Group Policy Object Editor and click Add
   ![image](https://github.com/user-attachments/assets/9bc70442-2e62-40dc-a69a-081959b74f89)
   The Select Group Policy Object window will open <br/>
   ![image](https://github.com/user-attachments/assets/ec850248-a921-4896-822e-f0df133a61fc)
   <br/>
   Click Browse and select the Users tab. Select the user that requires the PowerShell restriction. Then click Finish and OK <br/>
   ![image](https://github.com/user-attachments/assets/6ac8b9b6-8cf5-41fd-ba09-5fea65b42de4)

9. Expand `Local Computer\user2 Policy > User Configuration > Windows Settings > Security Settings > Software Restriction Policies`.  Click `New Software Restriction Policies` and navigating to `Additional Rules`. Right-click > New Path Rule. Set the path: `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe` and Security Level: Disallowed. Click Apply and OK
   ![image](https://github.com/user-attachments/assets/a127dbf6-0e62-4c57-9819-27c147058e9b)

10. To test the settings, first login as the local admin. Confirm that `C:/Confidential` can be opened and `powershell.exe` can be launched successfully
   ![image](https://github.com/user-attachments/assets/f3da55ae-24bc-463c-9f8b-99bf7b17deb6)

11. Then login as `user1` and confirm that `C:/Confidential` can be opened. However, opening `powershell.exe` should not be successful
    ![image](https://github.com/user-attachments/assets/8c488b2e-94cc-4760-9760-6dc70b15d07d)

12. Then login as `user2` and confirm that access to `C:/Confidential` and `powershell.exe` are denied
    ![image](https://github.com/user-attachments/assets/ec8b69e7-7168-421d-99cb-0091d3ae82fb)


