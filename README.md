# Active Directory Home Lab

## Project Overview

This project demonstrates the deployment and administration of a Windows Active Directory environment using Windows Server 2025 ARM and Windows 11 virtual machines hosted on Parallels Desktop for macOS.

The lab was designed to simulate a small enterprise environment and includes Active Directory Domain Services (AD DS), DNS, DHCP, RRAS/NAT, Group Policy, and PowerShell automation.

---

## Architecture

![Architecture Diagram](<img width="1536" height="1024" alt="ActiveDirectoryLabDiagram" src="https://github.com/user-attachments/assets/420162ac-1368-43e4-8853-9f0810ee3a61" />
)

---

## Technologies Used

| Technology                               | Purpose                 |
| ---------------------------------------- | ----------------------- |
| Windows Server 2025 ARM                  | Domain Controller       |
| Windows 11 Enterprise                    | Domain Client           |
| Active Directory Domain Services (AD DS) | Identity Management     |
| DNS                                      | Name Resolution         |
| DHCP                                     | IP Address Assignment   |
| RRAS/NAT                                 | Internet Routing        |
| PowerShell                               | User Automation         |
| Parallels Desktop                        | Virtualization Platform |
| macOS                                    | Host Operating System   |

---

## Network Configuration

### Domain Controller

| Setting      | Value                      |
| ------------ | -------------------------- |
| Internal IP  | 172.16.0.1                 |
| Subnet Mask  | 255.255.255.0              |
| External NIC | DHCP                       |
| Services     | AD DS, DNS, DHCP, RRAS/NAT |

### DHCP Scope

| Setting     | Value         |
| ----------- | ------------- |
| Network     | 172.16.0.0/24 |
| Range Start | 172.16.0.100  |
| Range End   | 172.16.0.200  |
| Gateway     | 172.16.0.1    |
| DNS Server  | 172.16.0.1    |

---

## Implemented Services

* Active Directory Domain Services (AD DS)
* DNS Server
* DHCP Server
* RRAS/NAT
* Group Policy Management
* PowerShell User Provisioning
* Domain Join Operations
* Internal Network Routing

---

## Architecture Diagram

This environment was built using Parallels Desktop on macOS with a Windows Server 2025 ARM Domain Controller and a Windows 11 client connected through an isolated internal network.

### Environment Flow

```text
Internet
    │
    ▼
Parallels Shared/NAT Network
    │
    ▼
Windows Server 2025 ARM
├── AD DS
├── DNS
├── DHCP
└── RRAS/NAT
    │
    ▼
172.16.0.0/24 Internal Network
    │
    ▼
Windows 11 Client
```

---

## Screenshots

### Server Manager

![Server Manager](screenshots/01-server-manager.png)

Displays installed server roles including AD DS, DNS, DHCP, and Remote Access.

---

### Active Directory Users and Computers

![ADUC](screenshots/02-active-directory-users-and-computers.png)

Demonstrates Active Directory deployment and organizational structure.

---

### DNS Manager

![DNS Manager](screenshots/03-dns-manager.png)

Shows Forward Lookup Zones and domain name resolution configuration.

---

### DHCP Scope Configuration

![DHCP](screenshots/04-dhcp-scope.png)

Displays DHCP scope settings and address allocation.

---

### RRAS/NAT Configuration

![RRAS](screenshots/05-rras-nat.png)

Shows NAT configuration providing internet access to internal clients.

---

### PowerShell User Provisioning

![PowerShell](screenshots/06-powershell-user-creation.png)

Demonstrates automation using PowerShell for Active Directory administration.

---

### Group Policy Management

![GPO](screenshots/07-group-policy-management.png)

Shows Group Policy administration within the domain.

---

### Windows 11 Domain Join

![Domain Join](screenshots/08-windows11-domain-join.png)

Demonstrates successful integration of a Windows 11 client into the Active Directory domain.

---

### Client Network Configuration

![IPConfig](screenshots/09-ipconfig-all.png)

Displays DHCP-assigned addressing and DNS configuration.

---

### Connectivity Testing

![Ping Test](screenshots/10-ping-test.png)

Verifies internal communication, DNS functionality, and internet connectivity through RRAS/NAT.

---

## PowerShell Automation

This lab includes PowerShell-based administrative automation for Active Directory management.

Example capabilities:

* Bulk user creation
* User account management
* Organizational Unit (OU) creation
* Password administration
* User provisioning automation

Scripts are stored in the `/scripts` directory.

---

## Skills Demonstrated

### Systems Administration

* Windows Server Administration
* Active Directory Administration
* DNS Configuration
* DHCP Configuration
* Group Policy Management

### Networking

* TCP/IP Configuration
* NAT Routing
* Network Troubleshooting
* DNS Resolution
* DHCP Scope Management

### Security & Identity

* Identity and Access Management (IAM)
* Active Directory User Management
* Domain Authentication
* Administrative Privilege Management

### Automation

* PowerShell Scripting
* User Provisioning Automation
* Administrative Task Automation

### Virtualization

* Parallels Desktop
* Multi-VM Lab Deployment
* Virtual Network Configuration

---

## Challenges and Troubleshooting

Several technical challenges were encountered during the deployment process:

### Networking Configuration

* Configured internal and external virtual network adapters using Parallels Desktop.
* Adapted networking concepts from VirtualBox-based tutorials to the Parallels environment.

### DNS Validation Issues

* Resolved DNS validation errors encountered during Active Directory Domain Services deployment.
* Verified proper DNS registration and domain resolution.

### Internal Adapter Configuration

* Diagnosed and corrected internal network adapter addressing issues.
* Configured a static IP address for the Domain Controller.

### RRAS/NAT Deployment

* Configured Routing and Remote Access Services (RRAS).
* Implemented NAT to provide internet access to internal domain clients.

### Windows Server 2025 ARM Adaptation

* Successfully completed the lab using Windows Server 2025 ARM instead of the original Windows Server 2019 environment.
* Adjusted configurations where necessary to accommodate platform differences.

Additional troubleshooting documentation can be found in:

```text
/docs/troubleshooting.md
```

---

## Future Improvements

Planned enhancements include:

* Additional domain-joined client systems
* Security Group management
* Group Policy hardening
* Windows Server Certificate Services (AD CS)
* Windows Server Update Services (WSUS)
* File Server deployment
* SIEM integration (Wazuh or Splunk)
* Vulnerability Management using Nessus
* Microsoft Defender administration

---

## Repository Structure

```text
Active-Directory-Home-Lab/
│
├── README.md
│
├── diagrams/
│   └── ad-home-lab-architecture.png
│
├── screenshots/
│   ├── 01-server-manager.png
│   ├── 02-active-directory-users-and-computers.png
│   ├── 03-dns-manager.png
│   ├── 04-dhcp-scope.png
│   ├── 05-rras-nat.png
│   ├── 06-powershell-user-creation.png
│   ├── 07-group-policy-management.png
│   ├── 08-windows11-domain-join.png
│   ├── 09-ipconfig-all.png
│   └── 10-ping-test.png
│
├── scripts/
│   └── create-users.ps1
│
└── docs/
    └── troubleshooting.md
```

---

## Author

**Christian Szadolc**

Cybersecurity Graduate
Western Governors University

This project was created to develop hands-on experience with enterprise Windows infrastructure, identity management, networking, and automation in preparation for cybersecurity and security engineering roles.
