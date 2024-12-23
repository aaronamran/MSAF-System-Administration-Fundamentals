# Deploy A GPO On A Single Machine To Enable And Securely Configure Windows Remote Management (WinRM) To Enable Safe Remote Administration Of The System
Windows Remote Management (WinRM)31 is the Microsoft implementation of the WS-Management Protocol32 which was developed as a public standard for remotely exchanging management data between devices that implement the protocol. If appropriate authentication and encryption is not implemented for this protocol, traffic may be subject to inception by an adversary. To reduce this risk, Windows Remote Management should be securely configured


## References
- [WinRM QuickConfig, HowTo Enable via GPO or Remotely on All Servers](https://www.websentra.com/winrm-quickconfig-remotely-configure-and-enable/) by Marc Wilson on Websentra


## Tasks
- Set the setting 'WinRM Client -> Allow Basic authentication' to 'Disabled'
- Set the setting 'WinRM Client -> Allow unencrypted traffic' to 'Disabled'
- Set the setting 'WinRM Client -> Disallow Digest authentication' to 'Enabled'
- Set the setting 'WinRM Service -> Allow Basic authentication' to 'Disabled'
- Set the setting 'WinRM Service -> Allow unencrypted traffic' to 'Disabled'
- Set the setting 'WinRM Service -> Disallow WinRM from storing RunAs credentials' to 'Enabled'


## Benchmarks
- Demonstrate that Windows Remote Management is securely configured with the above settings


## Practical Approach
1. In a Windows 10 Pro VM, press `Win + R` and enter `gpedit.msc` to open the Local Group Policy Editor
2. To configure WinRM Client settings, navigate to `Computer Configuration > Administrative Templates > Windows Components > Windows Remote Management (WinRM) > WinRM Client`
3. Disable `Allow Basic authentication` and `Allow unencrypted traffic`. Enable `Disallow Digest authentication` <br/>
   ![image](https://github.com/user-attachments/assets/0b145a7b-f594-4960-b420-5d1d2b007cc5)

4. To configure WinRM Service settings, navigate to `Computer Configuration > Administrative Templates > Windows Components > Windows Remote Management (WinRM) > WinRM Service`
5. Disable `Allow Basic authentication` and `Allow unencrypted traffic`. Enable `Disallow WinRM from storing RunAs credentials` <br/>
   ![image](https://github.com/user-attachments/assets/198945e3-1bcd-47e9-bc1c-ecc505ce78aa)

6. To apply the group policy, open cmd as admin and run the command
   ```
   gpupdate /force
   ```
7. To verify that WinRM is securely configured, run the command
   ```
   winrm get winrm/config
   ```
   The output should reflect the settings confgured <br/>
   ![image](https://github.com/user-attachments/assets/5c3e4648-a2d1-41ee-90cb-acb068f00a97)

8. Attempt to access the machine remotely using WinRM with basic or unencrypted traffic to test if the connections are blocked <br/>
   ![image](https://github.com/user-attachments/assets/f2e2f61a-420f-4f35-a941-bb4c63c31c1e)

   
