# Deploy A GPO On A Single Machine To Apply And Configure User Rights Policies
By failing to comprehensively specify user rights policies, an adversary may be able to exploit weaknesses in a workstation's Group Policy settings to gain access to sensitive information. To reduce this risk, user rights policies should be comprehensively specified



## References
- [User Rights Assignment](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/security-policy-settings/user-rights-assignment) by Microsoft


## Tasks
- Set the policy 'Allow log on locally' to 'Administrators' and 'Users'
- Set the policy 'Create a pagefile' to 'Administrators'
- Set the policy 'Create symbolic links' to 'Administrators'
- Set the policy 'Debug programs' to 'Administrators'
- Set the policy 'Force shutdown from a remote system' to 'Administrators'
- Set the policy 'Load and unload device drivers' to 'Administrators'
- Set the policy 'Profile single process' to 'Administrators'
- Set the policy 'Take ownership of files or other objects' to 'Administrators'


## Practical Approach
1. In a Windows 10 Pro VM, open the Local Group Policy Editor
2. Navigate to `Computer Configuration > Windows Settings > Security Settings > Local Policies > User Rights Assignment`
3. To set the policies required, click Add User or Group on each policy and add Administrators or Users depending on the requirements <br/>
   ![image](https://github.com/user-attachments/assets/3f7503de-dc62-4eab-9bce-6b4ecd96bc7c)

4. Open cmd as admin and update the group policies using the command
   ```
   gpupdate /force
   ```
