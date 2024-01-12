### Design and Implementation of Network Infrastructure

## Overview
This project focuses on creating a robust, secure, and highly available network infrastructure across multiple sites, integrating cutting-edge technologies and best practices. Explore the technical intricacies of each component and configuration as we delve into the world of network implementation.


![Picture1](https://github.com/MeselhyAbdallah/NetworkingProject/assets/156363787/77da274a-ecd6-4ee2-afb4-5b2f9f2856bf)

## Table of Contents
- [Project Title](#project-title)
- [Project Description](#project-description)
- [Tools Used](#tools-used)
  - [GNS3](#gns3)
  - [VMware Workstation](#vmware-workstation)
  - [Emulated Devices](#emulated-devices)
- [Cairo Site Networking Configuration](#cairo-site)
- [Alex Site Networking Configuration](#alex-site)
- [DC Site and Services](#dc-site--services)
  - [DC-GW-3 Configuration](#dc-gw-3-configuration)
  - [ASA-Firewall Configuration](#asa-firewall-configuration)
  - [Domain Controller and DHCP Server Configuration](#domain-controller-and-dhcp-server-configuration)
  - [Sophos-UTM Integration and Web-Filter Configuration on Cairo-Site](#sophos-utm-integration-and-web-filter-configuration-on-cairo-site)
  - [ACS-Server Configuration](#acs-server-configuration)
  - [CME and CUCM Server Configuration](#cme-and-cucm-server-configuration)
- [GRE DMVPN Configuration Tasks](#gre-dmvpn-configuration-tasks)
  - [Internet Connectivity Configuration](#internet-connectivity-configuration)
    - [ISP Configuration](#isp-configuration)
    - [Cairo-Site Configuration](#cairo-site-configuration)
    - [Alex-Site Configuration](#alex-site-configuration)
    - [DC-Site Configuration](#dc-site-configuration)
  - [GRE DMVPN Configuration](#gre-dmvpn-configuration)
  - [Technical Summary](#technical-summary)
    - [Connectivity](#connectivity)
    - [Network Segmentation](#network-segmentation)
    - [Security Measures](#security-measures)
    - [Data Center Services](#data-center-services)
    - [Communication Systems](#communication-systems)
    - [Key Focus](#key-focus)

# Project Title
Design and Implementation Network Infrastructure Model

# Project Description
Welcome to our network implementation project! This endeavor focuses on creating a robust, secure, and highly available network infrastructure. By integrating cutting-edge technologies and best practices, we aim to achieve seamless connectivity, enhanced security, and optimal performance across multiple sites.

## Key Objectives
- Establish efficient inter-site communication using advanced protocols like GRE Tunneling and DMVPN.
- Implement network segmentation for improved privacy and streamlined management of departmental resources.
- Prioritize security through the deployment of Firewalls, ACS Server, and a Domain Controller.
- Optimize data center services, including DHCP, Domain Controller, and Backup Server functionalities.
- Integrate CUCM and CME for advanced IP-based communication, elevating the quality of our phone services.

## Tools Used

### GNS3
GNS3 is a network simulator that allows the emulation of complex networks. It provides a graphical user interface for designing and testing network configurations.

### VMware Workstation
VMware Workstation is a virtualization platform that enables the creation and management of virtual machines. It serves as the underlying virtualization environment for running network simulations.

### Emulated Devices
1. **Cisco 7200 (Dynamips)**
   - Description: Cisco 7200 routers emulated using Dynamips for routing tasks.

2. **IOU L3**
   - Description: Layer 3 (routing) functionality emulated using IOU (IOS on UNIX).

3. **IOU L2**
   - Description: Layer 2 (switching) functionality emulated using IOU (IOS on UNIX).

4. **Sophos**
   - Description: Sophos firewall emulated using the Sophos ISO for testing network security.

5. **Cisco ASA**
   - Description: Cisco Adaptive Security Appliance emulated using the ASA ISO for comprehensive security features.

6. **Windows Server**
   - Description: Windows Server emulated for testing network configurations in a Windows environment.

7. **ACS Server**
   - Description: Access Control Server emulated for authentication, authorization, and accounting.

8. **CUCM (Cisco Unified Communications Manager)**
   - Description: Cisco Unified Communications Manager emulated for testing voice and IP telephony.

# Cairo Site
## Cairo-Site Networking Configuration
[![CairoSite](https://github.com/MeselhyAbdallah/NetworkingProject/assets/156363787/d652b223-356c-4b74-8905-923b14cdd197)](https://github.com/MeselhyAbdallah/NetworkingProject/assets/156363787/d652b223-356c-4b74-8905-923b14cdd197)

### Core and Distribution Switch Configuration:
1. **Layer 3 Connectivity:**
   - Establish Layer 3 links between Cairo-Core-1, Cairo-Core-2, Cairo-DSW-1, and Cairo-DSW-2 for efficient communication.
2. **OSPF Implementation:**
   - Implement OSPF across the core and distribution switches, optimizing routing within the network.
## Trunk and VTP Configuration:
3. **Trunk Ports Setup:**
   - Configure trunk ports on relevant switches for efficient data transfer.
4. **VTP Version 3 Configuration:**
   - Set up VTP version 3 with appropriate authentication keys for consistent VLAN management.
## VLAN and Default Gateway Configuration:
5. **VLAN Creation:**
   - Create VLANs on Cairo-DSW-1.
   - Create VLANs on Cairo-DSW-2.
6. **Default Gateway Assignment:**
   - Designate Cairo-DSW-1 as the default-gateway for VLANs 30 and 40.
   - Designate Cairo-DSW-2 as the default-gateway for VLANs 10 and 20.
## DHCP and Access Port Configuration:
7. **Helper-Address Configuration:**
   - Configure helper-address on Cairo-DSW-1 and Cairo-DSW-2 for DHCP services.
8. **Access Port Setup:**
   - Set up access ports on Cairo-Access switches.
## VLAN Trunking Security:
9. **Trunk Security Measures:**
   - Permit only VLAN 10, 20, 30, and 40 to traverse trunk ports.
## Sophos-UTM Configuration:
10. **Interfaces and OSPF Configuration:**
    - Configure interfaces and OSPF on Sophos-UTM.
11. **Default-Route and Load-Balancing:**
    - Set up a default-route and implement load-balancing between eth1 and eth2 on Sophos-UTM for optimized traffic distribution.
## ISP and Cairo-GW Configuration:
12. **Internet Connectivity Setup:**
    - Configure interfaces IP on ISP for internet connectivity.
13. **Cairo-Site Internet Connectivity:**
    - Set up NAT, OSPF, and default route configuration on Cairo-GW for Cairo-Site internet access.

# Alex Site
## Alex-Site Networking Configuration
[![Alex](https://github.com/MeselhyAbdallah/NetworkingProject/assets/156363787/dc781222-66f9-4451-ba95-2d288c21aacf)](https://github.com/MeselhyAbdallah/NetworkingProject/assets/156363787/dc781222-66f9-4451-ba95-2d288c21aacf)

### VLAN and Gateway Configuration:
1. **VLAN Creation:**
   - Create VLANs 10 and 20.
2. **Interface IP Configuration:**
   - Configure IP addresses on interfaces of Alex-Master-GW for VLAN 10 with OSPF and VRRP.
   - Configure IP addresses on interfaces of Alex-Backup-GW for VLAN 20 with OSPF and VRRP.
3. **Helper-Address Configuration:**
   - Configure helper-address on Alex-Master-GW and Alex-Backup-GW for DHCP services.
## Trunk and VTP Configuration:
4. **Trunk Ports Setup:**
   - Configure trunk ports on Alex-Core, Alex-Access-1, and Alex-Access-2 for efficient data transfer.
5. **VTP Version 3 Configuration:**
   - Set up VTP version 3 on Alex-Core as the primary server with an authentication key.
   - Set up VTP version 3 on Alex-Access-1 and Alex-Access-2 as clients with an authentication key.
## Port-Channel and Access Port Configuration:
6. **Port-Channel Setup:**
   - Implement Port-Channel on Alex-Core, Alex-Access-1, and Alex-Access-2 using PAgP.
7. **Access-Ports Configuration:**
   - Configure access-ports on Alex-Access-1 and Alex-Access-2 for end devices.
## Gateway Redundancy Configuration:
8. **VRRP Configuration:**
   - Configure VRRP on Alex-Master-GW for VLAN 10 and backup for VLAN 20.
   - Configure VRRP on Alex-Backup-GW for VLAN 20 and backup for VLAN 10.
9. **Priority Adjustment:**
   - Adjust priority dynamically by reducing Alex Master-GW priority by 60 if the uplink is down, giving priority to Alex Backup-GW using a track object.
10. **Authentication Setup:**
    - Implement MD5 authentication with the key string "cisco123" for VRRP.
## OSPF Configuration:
11. **OSPF Configuration:**
    - Apply OSPF on Alex-Master-GW for efficient routing within the network.

# DC Site & Services
## DC-Site , Services
[![DC](https://github.com/MeselhyAbdallah/NetworkingProject/assets/156363787/dba4a870-8357-4c99-bda7-19bfce515e2e)](https://github.com/MeselhyAbdallah/NetworkingProject/assets/156363787/dba4a870-8357-4c99-bda7-19bfce515e2e)

## DC-GW-3 Configuration
- Configure IP addresses on interfaces of DC-GW-3.
- Implement RIPv2 on DC-GW-3.

## ASA-Firewall Configuration
- Inject ASDM on ASA-Firewall.
- Configure IP addresses on ASA-Firewall interfaces.
- Set security level to 100 for all ASA-Firewall interfaces.
- Enable ICMP on ASA-Firewall.
- Configure RIPv2 on ASA-Firewall with the inside interface set as a passive interface.

## Domain Controller and DHCP Server Configuration
- Configure domain controller on D.C+DHCP Server.
- Set up DHCP pools for all VLANs on the other two sites.
- Configure backup domain controller on Backup D.C+DHCP Server.
- Set up backup DHCP pools for all VLANs on the other two sites.
- Create Organizational Units (OUs) for each site and VLANs on Active Directory.
- Implement group policies on DC-Site to deny access for USB ports, CD-Room, and the control panel for each VLAN.

## Sophos-UTM Integration and Web-Filter Configuration on Cairo-Site
- Add the domain controller in the Sophos-UTM as an authentication server.
- Synchronize Sophos-UTM with Active Directory.
- Enable web-filter for each VLAN on Cairo-Site:
  - VLAN 10 can't access any website without authenticating.
  - VLAN 20 can't access only to www.example1.com.
  - VLAN 30 can't access only to www.example2.com.
  - VLAN 40 can't access any HTTP/HTTPs website.

## ACS-Server Configuration
- Configure ACS-Server to be a TACACS+ authenticator.
- Implement AAA model on Cairo-GW, Alex-GW, Alex-Master-W, Alex-Backup-GW, DC-GW-1, DC-GW-2, and DC-GW-3 for console access authentication via ACS-Server or local password access.

## CME and CUCM Server Configuration
- Configure CME-Server to be a call-manager for VLAN 10, VLAN 20, VLAN 30, and VLAN 40 on Cairo-Site.
- Configure CUCM-Server to be a call-manager on DC-Site.
- Configure dial-peer between CME-Server and CUCM-Server for inter-site phone communication.

# GRE DMVPN Configuration Tasks
## Internet Connectivity Configuration
### ISP Configuration
- Configure IP addresses on ISP interfaces.
- Set up NAT configuration on ISP.
- Configure default route on ISP to allow any site to connect to the internet.
### Cairo-Site Configuration
- Configure IP addresses on Cairo-GW interfaces.
- Set up NAT configuration on Cairo-GW.
- Implement OSPF configuration on Cairo-GW.
- Configure default route on Cairo-GW for internet access.
### Alex-Site Configuration
- Configure IP addresses on Alex-GW interfaces.
- Set up NAT configuration on Alex-GW.
- Implement OSPF configuration on Alex-GW.
- Configure default route on Alex-GW for internet access.
### DC-Site Configuration
- Configure IP addresses on DC-GW-1 and DC-GW-2 interfaces.
- Set up NAT configuration on DC-GW-1 and DC-GW-2.
- Implement RIPv2 configuration on DC-GW-1 and DC-GW-2.
- Configure default route on DC-GW-1 and DC-GW-2 for internet access.
## GRE DMVPN Configuration
- Configure GRE+DMVPN on Cairo-GW, Alex-GW, DC-GW-1, and DC-GW-2 to connect ALEX-Site, Cairo-Site, and DC-Site together.
- Implement EIGRP over DMVPN network between Alex-Site, Cairo-Site, and DC-Site.


### Technical Summary

## Connectivity
- Utilizes Routing Protocols, GRE Tunneling, and DMVPN for inter-site communication.
- High Availability design with redundancy through Load Balancing, STP, FHRP, and EtherChannel.
  
## Network Segmentation
- Departments isolated in dedicated VLANs for privacy and efficient management.
- Individual user authentication ensures secure access to the domain.
  
## Security Measures
- Firewalls, ACS Server, and Domain Controller enhance network security.

## Data Center Services
- Core services include DHCP, Domain Controller, and Backup Server.

## Communication Systems
- Integrated CUCM and CME for IP-based communication, optimizing phone call functionality.

## Key Focus
- Prioritizes security, redundancy, and quality of service for a robust network infrastructure.



