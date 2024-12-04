# Deploy A GPO On A Single Machine To Apply Best Hardening Practices For Windows Defender


## References
- [Use Group Policy settings to configure and manage Microsoft Defender Antivirus](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus) by Microsoft


## Tasks
- Set the policy 'Turn off Windows Defender Antivirus' to 'Disabled'
- Set the policy 'Configure removal of items from Quarantine folder' to 'Disabled'
- Set the policy 'Scan all downloaded files and attachments' to 'Enabled'
- Set the policy 'Turn off real-time protection' to 'Disabled'
- Set the policy 'Turn on behavior monitoring' to 'Enabled'
- Set the policy 'Turn on process scanning whenever real-time protection is enabled' to 'Enabled'
- Set the policy 'Allow users to pause scan' to 'Disabled'
- Set the policy 'Scan archive files' to 'Enabled'
- Set the policy 'Scan packed executables' to 'Enabled'
- Set the policy 'Scan removable drives' to 'Enabled'
- Set the policy 'Turn on e-mail scanning' to 'Enabled'



## Benchmarks
- Validate that standard user cannot disable Windows Defender Antivirus


## Practical Approach
1. Open the Local Group Policy Editor by pressing `Win + R` and entering `gpedit.msc`
2. To configure the required Windows Defender policies, navigate to `Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus`
3. Set the policies as required either in the Microsoft Defender Antivirus, Scan or Real-time Protection folder
4. Open cmd as admin and apply the group policy
   ```
   gpupdate /force
   ```
