# Deploy A GPO On A Single Machine To Set Session Locks
Lock screens regulate access to devices by requiring the user to perform an action to log in. These actions include entering passwords, or using swipe cards. Setting a lock screen GPO in an environment will bolster the security posture of any company



## References
- [Interactive logon: Machine inactivity limit](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/security-policy-settings/interactive-logon-machine-inactivity-limit)


## Tasks
- Set the policy 'Interactive logon: Machine inactivity limit' to lock the machine after 15 seconds

## Benchmarks
- Demonstrate that the machine locks automatically after being idle for 15 seconds


## Practical Approach
1. In a Windows 10 Pro VM, press `Win + R` and enter `gpedit.msc` to open the Local Group Policy Editor
2. Navigate to `Computer Configuration > Windows Settings > Security Settings > Local Policies > Security Options` and locate the policy `Interactive logon: Machine inactivity limit`
3. Double-click on the policy, set the time to 15 seconds and save the changes
   ![image](https://github.com/user-attachments/assets/bd2c2652-9849-4fde-9eb0-480c85dda9f8)

4. Open cmd as admin and update the group policy using
   ```
   gpupdate /force
   ```
   Then restart the machine
5. To validate the compliance, leave the machine idle and it will lock after 15 seconds. The machine requires the user to log back in to continue the session
