# 🖧 Enterprise VLAN Network with Router-on-a-Stick & Windows Server 2008

## 📌 Overview
This project presents the design, implementation, and validation of an **enterprise-scale VLAN-based network infrastructure** integrated with **Windows Server 2008 Active Directory services**.  

The goal of this project is to demonstrate how a real-world organization can:
- Segment departments securely using VLANs  
- Enable controlled inter-VLAN communication via **Router-on-a-Stick (ROAS)**  
- Centralize authentication, authorization, and policy enforcement using **Active Directory, DNS, and Group Policy**  
- Support scalability, fault tolerance, and future growth  

The implementation was performed using **actual Cisco networking hardware** combined with **virtualized Windows Server environments**.

## 🏗️ Network Architecture

### 🔹 Topology Design
The network uses a **hybrid topology** combining:
- **Star topology** within departments
- **Mesh topology** between departmental switches  

Each department connects to a central access switch, while switches interconnect redundantly to improve reliability and fault tolerance.

**Key benefits:**
- Organized traffic flow  
- High availability  
- Scalability  
- Reduced broadcast traffic  

## 🧩 VLAN Segmentation

Each department is isolated using VLANs, creating independent broadcast domains while allowing controlled communication through routing.

| VLAN ID | Department | Network | CIDR |
|-------|-----------|--------|------|
| 10 | Servers | 192.168.100.240 | /29 |
| 20 | Engineering | 192.168.100.0 | /26 |
| 30 | Sales | 192.168.100.64 | /26 |
| 40 | Administration | 192.168.100.128 | /27 |
| 50 | IT Support | 192.168.100.160 | /27 |
| 60 | Finance | 192.168.100.224 | /28 |
| 15 | Network Infrastructure | 192.168.100.192 | /27 |

Subnet sizes were calculated with a **20% growth allowance** to support future expansion.

## 🔀 Inter-VLAN Routing (Router-on-a-Stick)

Inter-VLAN communication is achieved using **Router-on-a-Stick (ROAS)**.

### Hardware Used
- **Cisco Catalyst 2960** (Layer 2 switch)
- **Cisco 2900 Series Router**

### Implementation Details
- Single trunk link between switch and router
- IEEE 802.1Q encapsulation
- One router sub-interface per VLAN
- Each sub-interface acts as the default gateway for its VLAN

### Supported VLANs on Trunk
10, 20, 30, 40, 50, 60
This design minimizes hardware usage while maintaining full inter-VLAN routing capability.


## 🖥️ Server Infrastructure

### Windows Server 2008 Deployment
The server environment was implemented using virtual machines and includes:

- Primary Domain Controller (DC1)
- Backup / Additional Domain Controller
- Integrated DNS Server
- Active Directory Forest

**Domain Name:** `finalvision.com`

## 🧠 Active Directory Design

### Organizational Units (OUs)
- Employees  
- Desktops  
- Laptops  
- Servers  
- Groups  
- Admins  

### User & Group Management
- Manual and automated user creation
- Security groups per department
- Delegation of administrative tasks
- ACL-based file and resource access

### Automation Tools Used
- `CSVDE`
- `LDIFDE`
- `dsadd`
- PowerShell
- VBScript

Bulk user and group provisioning was implemented to simulate enterprise-scale environments.

## 🛡️ Group Policy & Security

### Implemented Group Policies
- Password and account lockout policies
- Desktop customization (wallpapers, restrictions)
- Logon hour restrictions
- Software deployment and updates
- Restricted Groups for admin delegation

### Auditing & Monitoring
- Authentication auditing
- File access auditing
- Active Directory object change tracking

Security policies were validated using event logs and Resultant Set of Policy (RSoP).

## 🌐 DNS & Domain Services

- Integrated DNS with Active Directory
- Multi-domain forest configuration
- Child domains and domain tree setup
- GlobalNames zone for single-label name resolution
- DNS zone delegation and hardening

## 🧪 Testing & Validation

### Connectivity Testing
- Intra-VLAN ping tests
- Inter-VLAN routing verification
- Server-to-client and client-to-server communication
- ARP and MAC address table verification

### Results
All departments successfully communicated **only through routed paths**, confirming:
- VLAN isolation
- Correct trunk configuration
- Proper gateway assignment
- Functional inter-VLAN routing

## 📦 Backup & Automation

- Automated daily, weekly, and monthly backups
- Script-based scheduling
- Verification through server logs and task execution

## 🎯 Key Outcomes

✔ Secure VLAN-based segmentation  
✔ Scalable IP addressing design  
✔ Centralized identity and access management  
✔ Enterprise-grade policy enforcement  
✔ Real hardware and VM integration  
✔ Fully documented and tested deployment  

## 🚀 Use Cases

- Network Administration laboratories  
- Enterprise network design demonstrations  
- VLAN and routing training environments  
- Active Directory and Group Policy practice  
- Cisco Router-on-a-Stick reference implementation  

## 📚 Course Information
**Course:** CMPE 351 – Network Administration    
**Date:** January 2026  

---

## 📄 License
This project is for **educational and academic purposes**.

