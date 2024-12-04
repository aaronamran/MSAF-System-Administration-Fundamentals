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
1. Open the Local Group Policy Editor by entering `Win + R` and `gpedit.msc`
2. Navigate to `Computer Configuration > Administrative Templates > Network > Lanman Workstation`
3. Locate `Network access: Allow anonymous SID/Name translation`. Double-click it and set it to Disabled. Click Apply and OK
4. Find `Network access: Do not allow anonymous enumeration of SAM accounts`. Double-click it and set it to Enabled. Click Apply and OK
5. Locate `Network access: Do not allow anonymous enumeration of SAM accounts and shares`. Double-click it and set it to Enabled. Click Apply and OK
6. Locate `Network access: Let Everyone permissions apply to anonymous users`. Double-click it and set it to Disabled. Click Apply and OK
7. Find `Network access: Restrict anonymous access to Named Pipes and Shares`. Double-click it and set it to Enabled. Click Apply and OK
8. Locate `Network security: Allow Local System to use computer identity for NTLM`. Double-click it and set it to Enabled. Click Apply and OK
9. Locate `Network security: Allow Local System NULL session fallback`. Double-click it and set it to Disabled. Click Apply and OK
10. Navigate to `Computer Configuration > Windows Settings > Security Settings > Local Policies > User Rights Assignment` and locate `Deny access to this computer from the network`. Double-click it and add `NT AUTHORITY\Local Account`. Click Apply and OK
11. To validate configuration, open PowerShell as admin and use the following commands to generate a file to be viewed in the browser
    ```
    gpresult /h gpresult.html
    ```
12. Test the disabled SMB guest access by connecting to the system from another machine using a guest or anonymous account to verify access is denied
