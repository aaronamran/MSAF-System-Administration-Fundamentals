# Protect Sensitive Folders And Files On Windows 10 By Deploying A GPO That Enforces Controlled Folder Access
Controlled Folder Access is a security feature in Microsoft Windows that forms part of Windows Defender Exploit Guard. It is designed to combat the threat of ransomware. In order to use Controlled Folder Access, Windows Defender Antivirus must be configured as the primary real-time antivirus scanning engine on workstations


## Tasks
- Set the policy 'Computer Configuration\Policies\Administrative Templates\Windows Components\Windows Defender Antivirus\Windows Defender Exploit Guard\Controlled Folder Access\Configure allowed applications' to 'Enabled' and enter the application that should be trusted
- Set the policy 'Computer Configuration\Policies\Administrative Templates\Windows Components\Windows Defender Antivirus\Windows Defender Exploit Guard\Controlled Folder Access\Configure Controlled folder access' to 'Enabled' and configure folders feature to 'Block'
- Set the policy 'Computer Configuration\Policies\Administrative Templates\Windows Components\Windows Defender Antivirus\Windows Defender Exploit Guard\Controlled Folder Access\Configure protected folders' to 'Enabled' and enter the folders that should be guarded


## Benchmarks
- Demonstrate that an untrusted application is blocked from making changes to protected folders



## Practical Approach
1. In Windows 10 Pro VM, verify Windows Defender is the primary antivirus. Ensure that no third-party antivirus is active or set as the default real-time antivirus.
Open Windows Security > Virus & threat protection > Manage settings and confirm that real-time protection is enabled
2. Enable Controlled Folder Access manually (optional for testing): Open Windows Security > Virus & threat protection > Manage ransomware protection. Toggle Controlled Folder Access to On. This confirms that the feature is supported and functioning
3. Press `Win + R` and run `gpedit.msc`.
4. To configure allowed applications, navigate to `Computer Configuration > Policies > Administrative Templates > Windows Components > Windows Defender Antivirus > Windows Defender Exploit Guard > Controlled Folder Access > Configure allowed applications` and set the policy to Enabled. Click Show to add the full paths of trusted applications
5. To enable controlled folder access, navigate to `Computer Configuration > Policies > Administrative Templates > Windows Components > Windows Defender Antivirus > Windows Defender Exploit Guard > Controlled Folder Access > Configure Controlled folder access` and set the policy to Enabled. Under Options, set the feature to Block and click OK
6. To protect specific folders, navigate to `Computer Configuration > Policies > Administrative Templates > Windows Components > Windows Defender Antivirus > Windows Defender Exploit Guard > Controlled Folder Access > Configure protected folders` and set the policy to Enabled. Click Show to add the paths of folders you want to protect and click OK
7. Apply and test the GPO by running the following command in cmd with admin privileges
   ```
   gpupdate /force
   ```
8. Run an untrusted application
