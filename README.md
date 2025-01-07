# Office Network Simulation

Welcome to the **Office Network Simulation** project! This project demonstrates a network design for a mid-sized office using Cisco Packet Tracer. The network ensures efficient connectivity, segmentation, and security for different departments, with essential services such as DHCP, DNS, VLANs, and inter-VLAN routing.

---

## 📝 Project Overview

This simulation features:
- Segmented departments with VLANs:
  - **Admin**: `192.168.10.0/24`
  - **HR**: `192.168.20.0/24`
  - **IT**: `192.168.30.0/24`
  - **Finance**: `192.168.40.0/24`
- Centralized inter-VLAN routing using a router.
- DHCP and DNS servers for automated IP management and name resolution.
- Internet access for all devices through NAT.
- Secure wireless connectivity with WPA2 encryption.
- Basic security measures using Access Control Lists (ACLs).

---

## 🛠️ Technologies Used

- **Cisco Packet Tracer**: For designing and simulating the network.
- **Networking Devices**: 
  - Cisco 2911 Router
  - Cisco 2960 Switches
  - Cisco Aironet Access Point
- **Networking Protocols**:
  - VLANs, DHCP, DNS, NAT
  - Inter-VLAN Routing
- **Security**: WPA2, ACLs, and Port Security.

---

## 🌐 Network Topology

### Diagram Highlights:
1. **Router**: Connects the office network to the internet and facilitates inter-VLAN routing.
2. **Switches**: Core and access switches for wired connectivity.
3. **Wireless Access Point**: Provides secure wireless access for mobile devices.
4. **Servers**: DHCP and DNS servers to support the network's functionality.
5. **End Devices**: PCs, laptops, and printers assigned to specific departments.

---

## 📋 Device Configurations

Below are the configurations for each major device in the network.  

### **1. Router (Cisco 2911)**
#### VLAN Sub-Interfaces for Inter-VLAN Routing:
```bash
enable
configure terminal
interface gigabitEthernet 0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
exit

interface gigabitEthernet 0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
exit

interface gigabitEthernet 0/0.30
encapsulation dot1Q 30
ip address 192.168.30.1 255.255.255.0
exit

interface gigabitEthernet 0/0.40
encapsulation dot1Q 40
ip address 192.168.40.1 255.255.255.0
exit


NAT for Internet Access:
ip nat inside source list 1 interface gigabitEthernet 0/1 overload
access-list 1 permit 192.168.0.0 0.0.255.255

interface gigabitEthernet 0/0
ip nat inside

interface gigabitEthernet 0/1
ip nat outside


Switches (Cisco 2960)
VLAN Creation:
enable
configure terminal
vlan 10
name Admin
vlan 20
name HR
vlan 30
name IT
vlan 40
name Finance
exit


Assigning VLANs to Ports:
interface range fastEthernet 0/1-10
switchport mode access
switchport access vlan 10

interface range fastEthernet 0/11-20
switchport mode access
switchport access vlan 20

interface range fastEthernet 0/21-30
switchport mode access
switchport access vlan 30

interface range fastEthernet 0/31-40
switchport mode access
switchport access vlan 40


Configuring Trunk Ports:
interface gigabitEthernet 0/1
switchport mode trunk
exit


DHCP Server Configuration
DHCP Pool Setup:
enable
configure terminal
ip dhcp pool Admin
network 192.168.10.0 255.255.255.0
default-router 192.168.10.1
dns-server 8.8.8.8
exit

ip dhcp pool HR
network 192.168.20.0 255.255.255.0
default-router 192.168.20.1
dns-server 8.8.8.8
exit

ip dhcp pool IT
network 192.168.30.0 255.255.255.0
default-router 192.168.30.1
dns-server 8.8.8.8
exit

ip dhcp pool Finance
network 192.168.40.0 255.255.255.0
default-router 192.168.40.1
dns-server 8.8.8.8
exit



Wireless Access Point
Basic Setup with WPA2 Encryption:
Open the configuration panel for the Access Point in Packet Tracer.
Set the SSID to OfficeWiFi.
Configure the security settings:
Security Mode: WPA2
Passphrase: SecureOffice2025

🚀 How to Use
Download the Project File:
Open Cisco Packet Tracer.
Load the .pkt file.
Explore the Topology:
Examine the connections between devices.
View the configurations on routers, switches, and servers.

Test the Network:
Use the ping and tracert tools from PCs to verify connectivity.
Access DNS-resolved websites or external IPs to test internet access.
Modify the Network:
Add more devices, configure additional services, or enhance security measures.

📂 File Structure
OfficeNetwork.pkt: The Cisco Packet Tracer project file.
README.md: This documentation file.
Optional: Add any other files or scripts you used (e.g., configs, diagrams).

🔍 Future Improvements
Integrate a firewall for enhanced security.
Configure SNMP for network monitoring.
Add VoIP to simulate office communication systems.
Test failover mechanisms for redundancy.

🤝 Contributing
Contributions are welcome! Feel free to:

Suggest enhancements.
Report issues.
Share your modified versions of this project.
📧 Contact
For questions or support, reach out to:

Email: joseph.mtakai@outlook.com
LinkedIn: https://www.linkedin.com/in/joseph-n-mtakai-b6b94a76/

✨ Happy Networking!

Feel free to test and refine this configuration! Let me know if you'd like any further changes or additions.
