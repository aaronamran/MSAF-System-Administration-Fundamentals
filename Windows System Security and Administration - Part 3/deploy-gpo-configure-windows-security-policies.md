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
2. To enable `Turn off multicast name resolution`, navigate to `Computer Configuration > Administrative Templates > Network > DNS Client` <br/>
   ![image](https://github.com/user-attachments/assets/e5def11e-891c-400b-9461-9477b1f92a45)

3. To disable `Turn off heap termination on corruption`, navigate to `Computer Configuration > Administrative Templates > Windows Components > File Explorer` <br/>
   ![image](https://github.com/user-attachments/assets/e8d16b88-efb9-42ca-aaa2-866bf1664aac)

4. Then navigate to `Computer Configuration > Windows Settings > Security Settings > Local Policies > Security Options`
5. Set the rest of the policies as required <br/>
   ![image](https://github.com/user-attachments/assets/d164c57d-359e-4fc5-9118-fc7b8767148c) <br/>
   ![image](https://github.com/user-attachments/assets/e849a8fd-330f-4bed-a9a5-ff5c8b326815) <br/>
   ![image](https://github.com/user-attachments/assets/36479eec-dcc5-455d-abfa-c2ddda4bad2e) <br/>
   ![image](https://github.com/user-attachments/assets/fe413f38-24ca-4fc8-9d4a-af5026556da3) <br/>
   ![image](https://github.com/user-attachments/assets/f1cdfc49-d565-4f35-a84c-0b0859146328)



7. Open cmd as admin and run the following command to update Group Policy
   ```
   gpupdate /force
   ```
