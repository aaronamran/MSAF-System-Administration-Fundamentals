# Deploy A GPO On A Single Machine That Defends The System Against Unauthorised Anonymous Connections
An adversary can use anonymous connections to gather valuable information about the state of a workstation including, but not limited to:
- Lists of users and groups
- SIDs of accounts
- List of available file shares
- Workstation policies
- OS version
To reduce this risk, anonymous connections to workstations should be disabled



## Tasks
- Set the setting 'Enable insecure guest logons' to 'Disabled'
- Set the setting 'Network access: Allow anonymous SID/Name translation' to 'Disabled'
- Set the setting 'Network access: Do not allow anonymous enumeration of SAM accounts' to 'Enabled'
- Set the setting 'Network access: Do not allow anonymous enumeration of SAM accounts' and shares to 'Enabled'
- Set the setting 'Network access: Let Everyone permissions apply to anonymous users' to 'Disabled'
- Set the setting 'Network access: Restrict anonymous access to Named Pipes and Shares to 'Enabled'
- Set the setting 'Network security: Allow Local System to use computer identity for NTLM' to 'Enabled'
- Set the setting 'Network security: Allow Local System NULL session fallback' to 'Disabled'
- Set the setting 'Deny access to this computer from the network' to 'NT AUTHORITY\Local Account'


## Benchmarks
- Validate that the Anonymous Connections is disabled and configured with the rules listed above


## Practical Approach
1. In a Windows 10 Pro VM, Open the Local Group Policy Editor by entering `Win + R` and `gpedit.msc`
2. Navigate to `Computer Configuration > Administrative Templates > Network > Lanman Workstation`. Disable `Enable insecure guest logons` <br/>
   ![image](https://github.com/user-attachments/assets/11cf602c-ed94-4996-9f2f-e97bc2b20e3c)

3. Then navigate to `Computer Configuration > Windows Settings > Security Settings > Local Policies > Security Options` <br/>
   ![image](https://github.com/user-attachments/assets/6a79bb24-9b81-42d0-b25b-01d0e60a885d)

4. Locate `Network access: Allow anonymous SID/Name translation`. Double-click it and set it to Disabled. Click Apply and OK
5. Find `Network access: Do not allow anonymous enumeration of SAM accounts`. Double-click it and set it to Enabled. Click Apply and OK
6. Locate `Network access: Do not allow anonymous enumeration of SAM accounts and shares`. Double-click it and set it to Enabled. Click Apply and OK
7. Locate `Network access: Let Everyone permissions apply to anonymous users`. Double-click it and set it to Disabled. Click Apply and OK
8. Find `Network access: Restrict anonymous access to Named Pipes and Shares`. Double-click it and set it to Enabled. Click Apply and OK
9. Locate `Network security: Allow Local System to use computer identity for NTLM`. Double-click it and set it to Enabled. Click Apply and OK
10. Locate `Network security: Allow Local System NULL session fallback`. Double-click it and set it to Disabled. Click Apply and OK <br7>
    ![image](https://github.com/user-attachments/assets/7326b14e-0211-4e11-94cc-989f5e0e5070)

11. Navigate to `Computer Configuration > Windows Settings > Security Settings > Local Policies > User Rights Assignment` and locate `Deny access to this computer from the network`. Double-click it and add `NT AUTHORITY\Local Account`. Click Apply and OK <br/>
    ![image](https://github.com/user-attachments/assets/1430d92f-4ac0-432a-9403-8f2175cc1838)

12. To validate configuration, open PowerShell as admin and use the following commands to generate a file to be viewed in the browser
    ```
    gpresult /h gpresult.html
    ```
13. Test the disabled SMB guest access by connecting to the system from another machine using a guest or anonymous account to verify access is denied. In the Windows 10 VM, create a test shared folder called 'SharedFolder'. Right-click on this folder and select Properties. Go to the Sharing tab and click Advanced Sharing. Share this folder and give it a name. In Permissions, ensure Everyone has at least Read permissions and save the settings <br/>
    ![image](https://github.com/user-attachments/assets/1876a3bb-1c16-4003-b4e4-61c5985be4ad)

14. From the other machine, open cmd or PowerShell with admin privileges. Run the following to attempt accessing a shared folder on the target machine without providing credentials
    ```
    net use \\192.168.1.8\SharedFolder
    ```
15. If guest logons are disabled, an Access Denied error or a prompt for credentials should appear <br/>
    ![image](https://github.com/user-attachments/assets/a5bd9830-609c-402f-aca1-88805250144b)

