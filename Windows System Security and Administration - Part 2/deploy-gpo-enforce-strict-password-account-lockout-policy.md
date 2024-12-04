# Deploy A GPO On A Single Machine To Enforce A Strict Password And Account Lockout Policy That Will Defend The System Against Password Guessing Attacks


## Tasks
- Disable convenience PIN sign-in
- Limit remembered passwords to 5
- Force user to change password every 90 days
- A user can only change their password after 24 hours
- Set minimum password length to 10 characters
- Passwords must meet complexity requirements
- Disable reversible encryption for passwords
- Set a maximum of 5 failed logon attempts
- Reset account lockout after 15 minutes
- If an account is locked out, the user must wait 15 minutes for the lockout feature to reset or have an administrator to reset the password


## Practical Approach
1. Open the Local Group Policy Editor by pressing `Win + R` and entering `gpedit.msc`
2. To disable convenience PIN Sign-in, navigate to `Computer Configuration > Administrative Templates > System > Logon`
3. Double-click on Turn on convenience PIN sign-in, choose Disabled, and click OK <br/>
   ![image](https://github.com/user-attachments/assets/e63820f7-4fc2-4897-a7d7-ec8105653bae)

4. To configure Password Policy, navigate to `Computer Configuration > Windows Settings > Security Settings > Account Policies > Password Policy`
5. Configure the following policies:
   - Enforce password history: Double-click and set it to 5 passwords remembered. Click OK
   - Maximum password age: Double-click and set it to 90 days. Click OK
   - Minimum password age: Double-click and set it to 1 day (24 hours). Click OK
   - Minimum password length: Double-click and set it to 10 characters. Click OK
   - Passwords must meet complexity requirements: Double-click, choose Enabled, and click OK
   - Store passwords using reversible encryption: Double-click, choose Disabled, and click OK <br/>
   ![image](https://github.com/user-attachments/assets/e094d151-ce59-4214-af5d-ed3da4a8624c)

6. To configure Account Lockout Policy, navigate to `Computer Configuration > Windows Settings > Security Settings > Account Policies > Account Lockout Policy`
   - Account lockout threshold: Double-click and set it to 5 invalid logon attempts. Click OK
   - Account lockout duration: Double-click and set it to 15 minutes, click OK
   - Reset account lockout counter after: Double-click and set it to 15 minutes. Click OK <br/>
   ![image](https://github.com/user-attachments/assets/af5904f7-1340-434b-aa4d-be2bc4566409)

7. To test the policy, log in as a standard user and try password changes, invalid logons, and PIN sign-in
