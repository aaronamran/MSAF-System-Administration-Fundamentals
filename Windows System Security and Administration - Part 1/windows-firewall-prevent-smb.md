# Turn On Windows Firewall And Create A Sample Firewall Rule To Prevent SMB Access To The Machine
Windows Firewall filters information coming in/out of your system from the Internet, and blocks malicious connections and/or programs

## Tasks
- Turn on Windows firewall with all three profiles: domain, private and public
- Create a firewall rule to block inbound connections to ports 21, 80, 139, 443 and 445
- Create a firewall rule to block all the outbound connections
- Create a firewall rule to block incoming RDP connections


## Practical Approach
1. Use a Windows 10 VM for this exercise. Open PowerShell as Administrator
2. Enable Windows Firewall for All Profiles:
   ```
   Set-NetFirewallProfile -Profile Domain,Private,Public -Enabled True
   ```
3. Create a firewall rule to block inbound connections to ports 21, 80, 139, 443, and 445:
   ```
   New-NetFirewallRule -DisplayName "Block Inbound Ports 21,80,139,443,445" -Direction Inbound -Protocol TCP -LocalPort 21,80,139,443,445 -Action Block
   ```
4. Create a firewall rule to block all outbound traffic:
   ```
   New-NetFirewallRule -DisplayName "Block All Outbound Traffic" -Direction Outbound -Action Block
   ```
5. Create a firewall rule to block incoming RDP (port 3389):
   ```
   New-NetFirewallRule -DisplayName "Block Inbound RDP" -Direction Inbound -Protocol TCP -LocalPort 3389 -Action Block
   ```
6. List all firewall rules to confirm:
   ```
   Get-NetFirewallRule | Format-Table -Property Name, DisplayName, Direction, Action
   ```
7. Check specific rules:
   ```
   Get-NetFirewallRule -DisplayName "Block Inbound Ports 21,80,139,443,445"
   Get-NetFirewallRule -DisplayName "Block All Outbound Traffic"
   Get-NetFirewallRule -DisplayName "Block Inbound RDP"
   ```
8. To test the rules, use `Test-NetConnection` to confirm the ports are blocked:
   Example for port 80
   ```
   Test-NetConnection -ComputerName localhost -Port 80
   ```
   The result should show `TcpTestSucceeded: False`
9. Verify that outbound connections are restricted by attempting to ping or access external websites and confirm the traffic is blocked
10. Test RDP by trying to connect to the machine remotely (it should fail)
    ![image](https://github.com/user-attachments/assets/58e8250c-1b3a-4c60-9cb4-d46e19dbf127)

