# Deploy A GPO On A Single Machine To Apply And Configure In-Built Windows Security Policies
By failing to comprehensively specify security policies, an adversary may be able to exploit weaknesses in a workstation's Group Policy settings to gain access to sensitive information. To reduce this risk, security policies should be comprehensively specified



## References
- [Security Options](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/security-policy-settings/security-options) by Microsoft


## Tasks
- Set the policy 'Turn off multicast name resolution' to 'Enabled'
- Set the policy 'Turn off heap termination on corruption' to 'Disabled'
- Set the policy 'Domain member: Disable machine account password changes' to 'Disabled'
- Set the policy 'Domain member: Maximum machine account password age' to '30 days'
- Set the policy 'Network security: Force logoff when logon hours expire' to 'Enabled'
- Set the policy 'System objects: Strengthen default permissions of internal system objects (e.g. Symbolic Links)' to 'Enabled'


## Practical Approach
1. In a Windows 10 Pro VM, open the Local Group Policy Editor by pressing `Win + R` and entering `gpedit.msc`
2. To turn off multicast name resolution, navigate to `Computer Configuration > Administrative Templates > Network > DNS Client`
3. Locate the policy `Turn off multicast name resolution`. Double-click the policy, select Enabled, and click OK
4. Then navigate to `Computer Configuration > Windows Settings > Security Settings > Local Policies > Security Options`
5. Set the rest of the policies as required
6. Open cmd as admin and run the following command to update Group Policy
   ```
   gpupdate /force
   ```
