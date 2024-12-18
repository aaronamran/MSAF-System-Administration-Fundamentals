# Task 1 - Install And Configure An Exchange Server And Connect It To An Active Directory Domain
Microsoft Exchange Server is Microsoft's email, calendaring, contact, scheduling, and collaboration platform. It uses the Windows Server operating system (OS) for business use. It gives users access to the email platform from mobiles, desktops and browsers. Typically, organizations will sync on-prem domain controllers with O365. This is known as AD sync as it enables you to create users in Active Directory which will sync over to O365. Since we are not using O365, we will have to configure it using a domain trust and exchange federation


## References
- [Verify Exchange Server installatios](https://learn.microsoft.com/en-us/exchange/plan-and-deploy/post-installation-tasks/verify-installation?view=exchserver-2019) by Microsoft
- [Configure a federation trust](https://learn.microsoft.com/en-us/exchange/configure-a-federation-trust-exchange-2013-help) by Microsoft


## Tasks
- Install a Windows 2012/16 Server
- Setup an Active Directory (AD) on the server and configure it as Domain Controller (DC)
- Setup a single (1) Windows 10 workstation and connect it to the Active Directory (AD) domain
- Setup a Microsoft Windows Exchange Server and connect it to the Active Directory (AD) domain
- Install the Exchange Mailbox server role
- Use the 'Get-ExchangeServer' command to verify that the Exchange Server installed successfully
- Sync the Exchange server with Active Directory using a Domain trust and Exchange federation


## Benchmarks
- Validate successful login into the Exchange Admin Interface


## Practical Approach
1. 
