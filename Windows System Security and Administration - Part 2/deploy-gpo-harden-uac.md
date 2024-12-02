# Deploy A GPO On A Single Machine To Harden UAC
Microsoft Windows provides the ability to require confirmation from users, via the User Access Control (UAC) feature, before any sensitive actions are performed. The default settings allow privileged users to perform sensitive actions without first providing credentials and require standard users (with local admin privileges) to confirm the action via the UAC prompt. To reduce this risk, UAC functionality should be hardened to ensure all sensitive actions require authorization by providing credentials via the "Secure Desktop" prompt


## References
- [User Account Control settings and configuration](https://learn.microsoft.com/en-us/windows/security/application-security/application-control/user-account-control/settings-and-configuration?tabs=intune) by Microsoft


## Tasks
- Set the setting 'User Access Control: Admin approval mode for the Built-in Administrator account' to 'Enabled'
- Set the setting 'User Access Control: Allow UIAccess applications to prompt for elevation without using the secure desktop' to 'Disabled'
- Set the setting 'User Account Control: Behavior of the elevation prompt for administrators in Admin Approval Mode' to 'Prompt for credentials on the secure desktop'
- Set the setting 'User Account Control: Behavior of the elevation prompt for standard users' to 'Prompt for credentials on the secure desktop'
- Set the setting 'User Account Control: Detect application installations and prompt for elevation' to 'Enabled'
- Set the setting 'User Account Control: Run all administrators in Admin Approval Mode' to 'Enabled'
- Set the setting 'User Account Control: Switch to the secure desktop when prompting for elevation' to 'Enabled'


## Benchmarks
- Run any application with local administrator privileges and demonstrate that it prompts for credentials on the secure desktop


## Practical Approach
1. Press `Win + R` and open `gpedit.msc` to open the Local Group Policy Editor
2. Navigate to `Computer Configuration > Windows Settings > Security Settings > Local Policies > Security Options` to configure the UAC settings
3. Set 'User Account Control: Admin approval mode for the Built-in Administrator account' to 'Enabled'
4. Set 'User Account Control: Allow UIAccess applications to prompt for elevation without using the secure desktop' to 'Disabled'
5. Set 'User Account Control: Behavior of the elevation prompt for administrators in Admin Approval Mode' to 'Prompt for credentials on the secure desktop'
6. Set 'User Account Control: Behavior of the elevation prompt for standard users' to 'Prompt for credentials on the secure desktop'
7. Set 'User Account Control: Detect application installations and prompt for elevation' to 'Enabled'
8. Set 'User Account Control: Run all administrators in Admin Approval Mode' to 'Enabled'
9. Set 'User Account Control: Switch to the secure desktop when prompting for elevation' to 'Enabled'
10. To apply the policy, run the following command in cmd with admin privileges
    ```
    gpupdate /force
    ```
11. To test the UAC settings, run a program as administrator. It should prompt for credentials
