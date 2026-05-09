# Network Design and ACL Security Implementation

## Project Overview

This project demonstrates the design and implementation of a secure enterprise-style network using Cisco Packet Tracer. The network was created for an organization with two departments — Human Resources (HR) and Finance — with controlled access to shared resources using Extended Access Control Lists (ACLs).

The project focuses on:

- Network topology design
- Router and switch configuration
- DHCP implementation
- DNS configuration
- File/Web server deployment
- Extended ACL security policies
- Network connectivity testing

The main objective of this project was to allow only the HR department to access the internal file server while preventing access from the Finance department.

---

# Network Topology

The network topology was designed using a centralized router architecture where:

- Each department connects to its own switch.
- Both switches connect to a central router.
- Shared services such as DHCP, DNS, and File/Web Server are hosted within the HR network.
- ACLs are used to enforce access restrictions.

# Technologies Used

- Cisco Packet Tracer
- Cisco 1941 Router
- Cisco 2960 Switches
- DHCP
- DNS
- Extended ACLs
- IP Addressing & Subnetting
- Routing and Switching

---

# Devices Used

| Device | Quantity | Purpose |
|---|---|---|
| Cisco 1941 Router | 1 | Inter-network routing |
| Cisco 2960 Switch | 2 | Departmental switching |
| PCs | 4 | End-user devices |
| DHCP Server | 1 | Automatic IP assignment |
| DNS Server | 1 | Hostname resolution |
| File/Web Server | 1 | Shared organizational resource |
| Printer | 1 | Shared printing resource |

---

# Network Addressing Scheme

| Network Segment | IP Address |
|---|---|
| Finance Network | 192.168.1.0/24 |
| HR Network | 192.168.2.0/24 |
| Finance Gateway | 192.168.1.1 |
| HR Gateway | 192.168.2.1 |
| DHCP Server | 192.168.2.5 |
| DNS Server | 192.168.2.6 |
| File/Web Server | 192.168.2.7 |

---

# Department Structure

## Finance Department

Devices connected:

- Finance PC 1
- Finance PC 2
- Network Printer
- Finance Switch

## HR Department

Devices connected:

- HR PC 1
- HR PC 2
- DHCP Server
- DNS Server
- File/Web Server
- HR Switch

---

# Router Configuration

The router was configured to:

- Route traffic between departments
- Serve as the default gateway
- Enforce ACL policies

## Router Interfaces

| Interface | IP Address |
|---|---|
| GigabitEthernet0/0 | 192.168.1.1 |
| GigabitEthernet0/1 | 192.168.2.1 |

## Sample Configuration

```bash
interface GigabitEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown

interface GigabitEthernet0/1
 ip address 192.168.2.1 255.255.255.0
 no shutdown
```

---

# DHCP Configuration

DHCP was configured to automatically assign:

- IP addresses
- Subnet masks
- Default gateways
- DNS server addresses

## DHCP Configuration Example

```bash
ip dhcp pool FINANCE
 network 192.168.1.0 255.255.255.0
 default-router 192.168.1.1
 dns-server 192.168.2.6

ip dhcp pool HR
 network 192.168.2.0 255.255.255.0
 default-router 192.168.2.1
 dns-server 192.168.2.6
```

---

# DNS Configuration

The DNS server was configured with a static IP address:

```text
192.168.2.6
```

The DNS service allowed devices to resolve domain names successfully across the network.

---

# File/Web Server Configuration

The File/Web Server was configured with:

- Static IP addressing
- HTTP service
- HTTPS service

## Server Configuration

| Parameter | Value |
|---|---|
| IP Address | 192.168.2.7 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 192.168.2.1 |

---

# Extended ACL Implementation

An Extended Access Control List (ACL) was configured to enforce security requirements.

## Security Policy

- HR users are allowed access to the File/Web Server.
- Finance users are denied access to the File/Web Server.
- All other traffic is permitted.

## ACL Configuration

```bash
access-list 101 deny tcp 192.168.1.0 0.0.0.255 host 192.168.2.7 eq 80
access-list 101 deny tcp 192.168.1.0 0.0.0.255 host 192.168.2.7 eq 443
access-list 101 permit ip any any
```

## Applying ACL to Interface

```bash
interface GigabitEthernet0/0
 ip access-group 101 in
```

---

# Testing and Verification

## DHCP Testing

- All PCs received IP addresses automatically.
- Default gateway and DNS settings were assigned correctly.

## Connectivity Testing

- Successful ping between devices
- Successful inter-network communication
- Proper routing verification

## DNS Testing

- Domain names resolved correctly
- Devices communicated using hostnames

## ACL Testing

### Successful Results

✅ HR PCs accessed the File/Web Server successfully.

❌ Finance PCs were denied access to the File/Web Server.

✅ Other network services continued functioning normally.

---

# Project Outcomes

This project successfully demonstrated:

- Enterprise network design
- Routing and switching concepts
- DHCP and DNS deployment
- Server configuration
- Extended ACL implementation
- Network security enforcement
- Connectivity troubleshooting

The final network achieved secure communication while protecting sensitive organizational resources from unauthorized departmental access.

---

# Skills Demonstrated

- Cisco Packet Tracer Simulation
- Network Design
- IP Addressing & Subnetting
- Routing & Switching
- DHCP Configuration
- DNS Services
- Extended ACL Security
- Network Troubleshooting
- Enterprise Network Security

---

# Conclusion

This project provided hands-on experience in designing and securing a small enterprise network. Through subnetting, routing, DHCP, DNS, and ACL implementation, the network successfully enforced departmental security policies while maintaining proper communication across the organization. The implementation reflects real-world networking and cybersecurity administration practices commonly used in enterprise environments.

[Read Report](https://drive.google.com/file/d/1bUZ2nL590RxxLR9JrOUyedw3LV854Y0S/view?usp=sharing)
---

# Author

**Iyabo Uwadiae**

Cybersecurity & Networking Enthusiast

