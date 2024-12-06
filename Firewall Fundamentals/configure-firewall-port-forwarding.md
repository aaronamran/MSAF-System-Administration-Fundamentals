# Configure Port Forwarding On The Firewall
Port forwarding allows external devices access to computer services on private networks. It does this by mapping an external port to an internal IP address and port. Port forwarding is also a technique that set up web servers and exposes them to the Internet


## References
- [Download Latest Stable Version](https://www.pfsense.org/download/) by pfsense
- [How to Set Up Port Forwarding](https://www.lifewire.com/how-to-port-forward-4163829) by Tim Fisher on Lifewire
- [Port Forwards](https://docs.netgate.com/pfsense/en/latest/nat/port-forwards.html) by Netgate Docs


## Tasks
- Install pfSense in VirtualBox
- Setup a web server in another VM
- Configure pfSense and the web server in a bridged network connection
- Login to your home router as admin and setup port forwarding for the pfSense internal IP address
- Login to your pfSense firewall and setup another port forwarding rule to your web server


## Benchmarks
- Demonstrate that you can access your web server from its internal IP address
- Demonstrate that you can access your web server from your external IP address


## Practical Approach
1. 
