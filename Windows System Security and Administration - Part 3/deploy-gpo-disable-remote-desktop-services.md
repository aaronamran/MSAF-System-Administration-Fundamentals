# Deploy A GPO On A Single Machine That Disables Remote Desktop Services To Prevent Unauthorised Remote Access
While remote desktop access may be convenient for legitimate users to access workstations across a network, it also allows an adversary to access other workstations once they have compromised an initial workstation and user's credentials. To reduce this risk, Remote Desktop Services should be disabled



## References
- [Deny log on through Remote Desktop Services](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/security-policy-settings/deny-log-on-through-remote-desktop-services) by Microsoft


## Tasks
- Install a Windows VM and show that you can connect to it remotely via Remote Desktop Services
- Set the policy 'Allow users to connect remotely by using Remote Desktop Services' to 'Disabled'
- Set the policy 'Deny log on through Remote Desktop Services' to 'Administrators'


## Benchmarks
- Validate that you cannot connect to the machine via Remote Desktop Services


## Practical Approach
1. In a Windows 10 Pro VM, open the Local Group Policy Editor by pressing `Win + R` and entering `gpedit.msc`
2. To disable Remote Desktop Services, navigate to `Computer Configuration > Administrative Templates > Windows Components > Remote Desktop Services > Remote Desktop Session Host > Connections`
3. Locate the policy `Allow users to connect remotely using Remote Desktop Services`. Double-click it, set it to Disabled, and click OK
4. To restrict Login Access via Remote Desktop, navigate to `Computer Configuration > Windows Settings > Security Settings > Local Policies > User Rights Assignment`
5. Locate `Deny log on through Remote Desktop Services`. Double-click it. Add the Administrators group. Click Apply and OK
6. Open cmd as admin and run the command below to apply Group Policy changes. Then restart the machine
   ```
   gpupdate /force
   ```
7. To test the remote desktop connection, use a second Windows machine to RDP into the Windows 10 VM