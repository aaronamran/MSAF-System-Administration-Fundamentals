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
1. Use a Windows 10 Pro VM as the target machine for this task. Open PowerShell as admin and run the following commands to enable remote connection from another machine (host machine)
   ```
   winrm quickconfig -Force
   Enable-PSRemoting -Force
   Set-Item WSMan:\localhost\Client\TrustedHosts -Value "the_other_Windows_IP_Address"
   ```
2. In the host machine open PowerShell as admin and run the commands above too. Then remote connect into the Windows 10 VM using
   ```
   Enter-PSSession -ComputerName the_other_Windows_IP_Address -Authentication Basic -Credential (Get-Credential)
   ```
   ![image](https://github.com/user-attachments/assets/bc441385-3abd-40a1-8bf3-f07c48f03a1f)

3. Windows 10 Pro VM, open the Local Group Policy Editor by pressing `Win + R` and entering `gpedit.msc`
4. To disable Remote Desktop Services, navigate to `Computer Configuration > Administrative Templates > Windows Components > Remote Desktop Services > Remote Desktop Session Host > Connections`
5. Locate the policy `Allow users to connect remotely using Remote Desktop Services`. Double-click it, set it to Disabled, and click OK <br/>
   ![image](https://github.com/user-attachments/assets/db2b07b6-31ec-4994-8fa9-01ffe263af8d)

6. To restrict Login Access via Remote Desktop, navigate to `Computer Configuration > Windows Settings > Security Settings > Local Policies > User Rights Assignment`
7. Locate `Deny log on through Remote Desktop Services`. Double-click it. Add the Administrators group. Click Apply and OK <br/>
   ![image](https://github.com/user-attachments/assets/8eadeb03-a889-4f70-b7d0-5054d954a275)

8. Open cmd as admin and run the command below to apply Group Policy changes
   ```
   gpupdate /force
   ```
9. To test the remote desktop connection, use the other Windows machine to RDP into the Windows 10 VM <br/>
   ![image](https://github.com/user-attachments/assets/bca8deac-603f-409b-aef2-da0842d3090d)

