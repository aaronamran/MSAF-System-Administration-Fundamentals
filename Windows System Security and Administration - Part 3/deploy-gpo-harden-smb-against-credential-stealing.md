# Deploy A GPO On A Single Machine To Harden SMB Against Known Credential Stealing Attack Techniques And Tools
An adversary that has access to network communications may attempt to use session hijacking tools to interrupt, terminate or steal a Server Message Block (SMB) session. To reduce this risk, all communications between SMB clients and servers should be signed, with any passwords used appropriately encrypted


## References
- [Microsoft network server: Amount of idle time required before suspending session](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/security-policy-settings/microsoft-network-server-amount-of-idle-time-required-before-suspending-session) by Microsoft


## Tasks
- In the Windows Registry 'Disable' SMBv1 server
- Set the policy 'Microsoft network client: Digitally sign communications (always)' to 'Enabled'
- Set the policy 'Microsoft network client: Digitally sign communications (if server agrees)' to 'Enabled'
- Set the policy 'Microsoft network client: Send unencrypted password to third-party SMB servers' to 'Disabled'
- Set the policy 'Microsoft network server: Amount of idle time required before suspending session' to '15 minutes'
- Set the policy 'Microsoft network server: Digitally sign communications (always)' to 'Enabled'
- Set the policy 'Microsoft network server: Digitally sign communications (if client agrees)' to 'Enabled'


## Practical Approach
1. In a Windows 10 Pro VM, press `Win + R` and enter `regedit` to open the Registry Editor
2. Navigate to `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters` and create or modify the DWORD (32-bit) Value with the name `SMB1`. Set the value to 0 to disable SMBv1 server <br/>
   ![image](https://github.com/user-attachments/assets/95aae1eb-86e9-4049-8c42-4400198c7708)

3. Restart the VM to apply registry changes
4. Press `Win + R` and enter `gpedit.msc` to open the Local Group Policy Editor
5. Navigate to `Computer Configuration > Windows Settings > Security Settings > Local Policies > Security Options`
6. Modify the following policies as specified:
   - Microsoft network client policies:
     - Digitally sign communications (always): Set to Enabled
     - Digitally sign communications (if server agrees): Set to Enabled
     - Send unencrypted password to third-party SMB servers: Set to Disabled
   - Microsoft network server policies:
     - Amount of idle time required before suspending session: Set to 15 minutes
     - Digitally sign communications (always): Set to Enabled
     - Digitally sign communications (if client agrees): Set to Enabled
   
   ![image](https://github.com/user-attachments/assets/6cdd8dd8-30fc-4dea-9a2a-87fb28994472)

7. Open PowerShell as admin and run the command to enforce policy changes
   ```
   gpupdate /force
   ```
8. To verify SMBv1 is disabled, run the command to check its status
   ```
   Get-WindowsOptionalFeature -Online -FeatureName SMB1Protocol
   ```
   The State should show Disabled <br/>
   ![image](https://github.com/user-attachments/assets/184c58ba-7123-4f1a-97b9-f129df7a4ade)

