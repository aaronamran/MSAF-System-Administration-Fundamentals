# Harden A Windows Machine Using A Gpo That Restricts Control Application Installations

## Tasks
- Use a Windows VM for this task
- Set the policy 'Computer Configuration\Policies\Administrative Templates\Windows Components\File Explorer\Configure Windows Defender SmartScreen' to 'Enabled' and select 'Warn and prevent bypass'
- Set the policy 'Computer Configuration\Policies\Administrative Templates\Windows Components\Windows Defender SmartScreen\Explorer\Configure Windows Defender SmartScreen' to 'Enabled' and select 'Warn and prevent bypass'
- Set the policy 'Computer Configuration\Policies\Administrative Templates\Windows Components\Windows Installer\Allow user control over installs' to 'Disabled'
- Set the policy 'Computer Configuration\Policies\Administrative Templates\Windows Components\Windows Installer\Always install with elevated privileges' to 'Disabled'
- Set the policy 'User Configuration\Policies\Administrative Templates\Windows Components\Windows Installer\Always install with elevated privileges' to 'Disabled'



## Benchmarks
- Download a malicious application from the Internet and show that a standard user cannot run it (Make sure you are running this inside a virtual machine, if the GPO is not applied correctly you do not want to infect your machine.)



## Practical Approach
1. 
