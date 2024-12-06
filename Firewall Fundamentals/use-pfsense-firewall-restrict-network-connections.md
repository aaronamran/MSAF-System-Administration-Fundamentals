# Restrict Network Connections To Two VirtualBox Machines Using A PFSense Firewall
A firewall is a network system that prevents unauthorized access to a network. It inspects incoming and outgoing traffic using a set of rules to identify and block threats. pfSense is a free and open-source firewall and router, managed by a web interface



## References
- [Download Latest Stable Version](https://www.pfsense.org/download/) by pfsense

## Tasks
- Download and install pfSense in VirtualBox
- Create a WAN interface in pfSense and configure it with DHCP
- Create a LAN interface in pfSense and configure it as the default network interface
- Setup a Windows VM and configure it on the same network as pfSense
- Route Windows VM traffic through your pfSense firewall


## Benchmarks
- Demonstrate pfSense can reach the Internet by using the 'ping' command
- Run 'ipconfig' on your Windows VM to show your default gateway is configured with pfSense


## Practical Approach
1. 
