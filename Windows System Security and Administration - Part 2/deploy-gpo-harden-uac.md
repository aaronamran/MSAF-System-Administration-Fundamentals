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
2. Navigate to `Computer Configuration > Windows Settings > Security Settings > Local Policies > Security Options` to configure the UAC settings <br/>
   ![image](https://github.com/user-attachments/assets/02f9041b-b398-4c08-b915-6b6c83418a82) <br/>
   ![image](https://github.com/user-attachments/assets/ad362b8f-2651-4163-ae27-4de9c0280773)

3. Set 'User Account Control: Admin approval mode for the Built-in Administrator account' to 'Enabled'
   ![image](https://github.com/user-attachments/assets/5f047004-609c-425d-8f19-b253a74941c4)

4. Set 'User Account Control: Allow UIAccess applications to prompt for elevation without using the secure desktop' to 'Disabled'
   ![image](https://github.com/user-attachments/assets/951264ba-76b2-4f1c-8eba-4d3f5e6ab673)

5. Set 'User Account Control: Behavior of the elevation prompt for administrators in Admin Approval Mode' to 'Prompt for credentials on the secure desktop'
   ![image](https://github.com/user-attachments/assets/df006a96-61b4-49f6-b956-b331eef12689)

6. Set 'User Account Control: Behavior of the elevation prompt for standard users' to 'Prompt for credentials on the secure desktop'
   ![image](https://github.com/user-attachments/assets/e6577ebb-4def-4da5-80b8-072ac3a2f5f6)

7. Set 'User Account Control: Detect application installations and prompt for elevation' to 'Enabled'
   ![image](https://github.com/user-attachments/assets/256b3c09-29a4-4f9d-8a9e-39c7f0b61f14)

8. Set 'User Account Control: Run all administrators in Admin Approval Mode' to 'Enabled'
   ![image](https://github.com/user-attachments/assets/4e6fb23f-b3e1-4db6-890f-fdc42dccc492)

9. Set 'User Account Control: Switch to the secure desktop when prompting for elevation' to 'Enabled'
   ![image](https://github.com/user-attachments/assets/a9bb26e6-1217-48d3-89bb-f36706c00d81)

10. To apply the policy, run the following command in cmd with admin privileges
    ```
    gpupdate /force
    ```
11. To test the UAC settings, run a program as administrator. It should prompt for credentials
    ![image](https://github.com/user-attachments/assets/0848181b-b8ee-4154-b52c-b6550af55387)
