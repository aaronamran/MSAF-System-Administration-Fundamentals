# Harden A Windows Machine Using A GPO That Restricts Control Application Installations

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
1. Use a Windows 10 Pro VM. Ensure the `gpedit.msc` is installed and open it with `Win + R`
2. To configure Windows Defender SmartScreen, navigate to `Computer Configuration > Administrative Templates > Windows Components > File Explorer` and double-click `Configure Windows Defender SmartScreen`. Set it to Enabled. In the dropdown, select `Warn and prevent bypass` and click OK.
3. Then navigate to `Computer Configuration > Administrative Templates > Windows Components > Windows Defender SmartScreen > Explorer` and double-click `Configure Windows Defender SmartScreen` and enable it. In the dropdown, select `Warn and prevent bypass`
4. To configure Windows Installer Policies, navigate to `Computer Configuration > Administrative Templates > Windows Components > Windows Installer` and double-click `Allow user control over installs`. Set it to Disabled and click OK. Double-click `Always install with elevated privileges` and also set it to Disabled
5. Then navigate to `User Configuration > Administrative Templates > Windows Components > Windows Installer` and double-click `Always install with elevated privileges` and disable it
6. Open cmd as admin and run the following command to ensure policy changes are applied immediately
   ```
   gpupdate /force
   ```
7. To test the hardening, download a harmless test malware, such as the EICAR test file which simulates a malware file from [https://www.eicar.org/download-anti-malware-testfile/](https://www.eicar.org/download-anti-malware-testfile/)
