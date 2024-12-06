# Use PFSense To Monitor Network Traffic
A firewall provides vital network security, but advanced threats can bypass it. An IDS is a passive monitoring device that detects threats and generates alerts. This enables incident responders to investigate and respond to potential incidents. They are a valuable component of any organization's cybersecurity deployment. PfSense is a versatile open-source network firewall and router that can be installed on a physical machine or a virtual machine. It has many software packages, including IDS software like Snort, that you can use to monitor network traffic



## References
- [Configuring the Snort Package](https://docs.netgate.com/pfsense/en/latest/packages/snort/setup.html) by Netgate Docs


## Tasks
- Install PfSense, Windows 7, Kali Linux on VM each. ALl the machines should be present on the same subnet on the virtual network
- Configure PfSense to monitor virtual network traffic
- Install Snort IDS package on PfSense to alert when abnormal traffic is detected on the network
- Navigate to the PfSense web console
- To simulate abnormal network traffic, use the Kali VM (that has Metasploit installed) to exploit the 'Eternal Blue' vulnerability on the Windows 7 VM
- Once the exploit is successful, view the alerts on PfSense indicating the presence of abnormal traffic on the network


## Benchmarks
- Validate that PfSense is installed and configured to monitor traffic on the network
- Validate that Snort IDS is configured on PfSense
- Validate that you can access the PfSense web console
- Validate that you have exploited the Windows 7 'Eternal Blue' vulnerability using the Kali VM
- Validate that you can view abnormal network traffic relevant to the exploit on PfSense


## Practical Approach
1. 
