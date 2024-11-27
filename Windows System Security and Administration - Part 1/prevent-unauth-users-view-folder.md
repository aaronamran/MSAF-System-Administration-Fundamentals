# Use Access Permissions And Rights To Prevent Unauthorized Users From Viewing A Folder That Contains Sensitive Materials
A Windows computer can support multiple users, each with dedicated local accounts. Users can log in remotely simultaneously or locally at different times. Access control restrictions for each user account can be configured using the Group Policy Editor. 

On a standalone machine, the Local Group Policy Editor is used for this purpose. For domain-level management, Group Policy settings are configured on the domain controller


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


## Benchmarks
- Local administrator can access the 'C:\Confidential' folder and open powershell.exe
- 'user1' can access the 'C:\Confidential' folder but cannot open powershell.exe
- 'user2' cannot access the 'C:\Confidential' folder and cannot open powershell.exe


## Practical Approach
1. 
