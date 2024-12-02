# Deploy A GPO On A Single Machine To Ensure Credentials Are Entered In A Secure Manner
When users enter their credentials on a workstation it provides an opportunity for malicious code, such as a key logging application, to capture the credentials. To reduce this risk, users should be authenticated by using a trusted path to enter their credentials on the Secure Desktop



## Tasks
- Set the policy 'Computer Configuration\Policies\Administrative Templates\System\Logon\Do not display network selection UI' to 'Enabled'
- Set the policy 'Computer Configuration\Policies\Administrative Templates\System\Logon\Enumerate local users on domain-joined computers' to 'Disabled'
- Set the policy 'Computer Configuration\Policies\Administrative Templates\Windows Components\Credential User Interface\Do not display the password reveal button' to 'Enabled'
- Set the policy 'Computer Configuration\Policies\Administrative Templates\Windows Components\Credential User Interface\Enumerate administrator accounts on elevation' to 'Disabled'
- Set the policy 'Computer Configuration\Policies\Administrative Templates\Windows Components\Credential User Interface\Require trusted path for credential entry' to 'Enabled'
- Set the policy 'Computer Configuration\Policies\Administrative Templates\Windows Components\Windows Logon Options\Disable or enable software Secure Attention Sequence' to 'Disabled'
- Set the policy 'Computer Configuration\Policies\Administrative Templates\Windows Components\Windows Logon Options\Sign-in last interactive user automatically after a system-initiated restart' to 'Disabled'
- Set the policy 'Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Interactive logon: Do not require CTRL+ALT+DEL' to 'Disabled'
- Set the policy 'Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Interactive logon: Don't display username at sign-in' to 'Enabled'


## Practical Approach
1. Press `Win + R` and open `gpedit.msc` to open the Local Group Policy Editor
2. To configure policies, navigate to `Computer Configuration\Policies\Administrative Templates\System\Logon` and double-click `Do not display network selection UI` and enable it. Click Apply and then OK
3. In the same Logon folder, double-click on `Enumerate local users on domain-joined computers` and select Disabled. Click Apply and then OK
4. Then navigate to `Computer Configuration\Policies\Administrative Templates\Windows Components\Credential User Interface` and double-click on `Do not display the password reveal button` and enable it. Click Apply and then OK
5. In the same folder, double-click on `Enumerate administrator accounts on elevation`. Disable it and apply the changes
6. Also in the same folder, double-click on `Require trusted path for credential entry`. Enable it and apply the changes
7. Navigate to `Computer Configuration\Policies\Administrative Templates\Windows Components\Windows Logon Options` and double-click on `Disable or enable software Secure Attention Sequence`. Disable it and apply it
8. In the same folder, double-click on `Sign-in last interactive user automatically after a system-initiated restart`. Disable and apply the changes
9. Navigate to `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options`. Double-click on `Interactive logon: Do not require CTRL+ALT+DEL`. Disable it and apply the changes
10. In the same folder, double-click on `Interactive logon: Don't display username at sign-in`. Enable it and apply the changes
11. Open cmd as admin, and run the following command to update policies on the system
    ```
    gpupdate /force
    ```


