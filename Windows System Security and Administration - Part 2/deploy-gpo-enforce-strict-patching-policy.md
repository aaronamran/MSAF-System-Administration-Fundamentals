# Deploy A GPO On A Single Machine To Enforce A Strict Operating System Patching Policy That Will Defend The System Against The Latest Vulnerabilities


## Tasks
- Set the policy 'Allow Automatic Updates immediate installation' to 'Enabled'
- Set the policy 'Configure Automatic Updates' to 'Enabled'
- Set the policy 'Do not include drivers with Windows Updates' to 'Disabled'
- Set the policy 'No auto-restart with logged on users for scheduled automatic updates installations' to 'Enabled'
- Set the policy 'Remove access to use all Windows Update features' to 'Disabled'
- Set the policy 'Turn on recommended updates via Automatic Updates' to 'Enabled'


## Practical Approach
1. Press `Win + R` key and enter `gpedit.msc` to open the Local Group Policy Editor
2. Navigate to `Computer Configuration > Administrative Templates > Windows Components > Windows Update`
3. Set the policies required to their corresponding settings
4. Open cmd as admin and update the group policy
   ```
   gpupdate /force
   ```
