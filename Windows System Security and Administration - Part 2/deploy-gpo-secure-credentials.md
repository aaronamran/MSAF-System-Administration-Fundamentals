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
1. 
