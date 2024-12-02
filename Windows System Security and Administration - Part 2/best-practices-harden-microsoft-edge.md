# Apply Best Practices To Harden Microsoft Edge Against Known Weaknesses
Microsoft Edge is a web browser that was first introduced in Microsoft Windows 10 to replace Internet Explorer. Microsoft Edge contains significant security enhancements over Internet Explorer and should be used wherever possible


## Tasks
- Set the policy 'Allow Adobe Flash' to 'Disabled'
- Set the policy 'Allow Developer Tools' to 'Disabled'
- Set the policy 'Configure Do Not Track' to 'Enabled'
- Set the policy 'Configure Password Manager' to 'Disabled'
- Set the policy 'Configure Pop-up Blocker' to 'Enabled'
- Set the policy 'Configure Windows Defender SmartScreen' to 'Enabled'
- Set the policy 'Prevent access to the about:flags page in Microsoft Edge' to 'Enabled'
- Set the policy 'Prevent bypassing Windows Defender SmartScreen prompts for files' to 'Enabled'
- Set the policy 'Prevent users and apps from accessing dangerous websites' to 'Enabled' and 'Block'


## Benchmarks
- Open Microsoft Edge and demonstrate that Windows Defender SmartScreen is configured
- Try to download a known malicious application from Microsoft Edge and demonstrate that the Windows Defender SmartScreen prevents it


## Practical Approach
1. Open Local Group Policy Editor by pressing `Win + R` and entering `gpedit.msc`
2. Navigate to the following path `Computer Configuration -> Administrative Templates -> Microsoft Edge` 
3. Set the policies as required, then run `gpupdate /force` in cmd with admin privileges
4. To check Edge settings, go to `edge://settings` and confirm the policies are in effect (look for "Managed by your organization" or specific policy settings)
5. Attempt to access edge://flags to verify access is blocked
6. Navigate to `edge://settings/privacy` and ensure Microsoft Defender SmartScreen is toggled ON under "Security"
7. To download a malicious test file, use EICAR test files
