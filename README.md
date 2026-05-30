# Active Directory Home Lab

## Project Overview

This project demonstrates the deployment and administration of a Windows Active Directory environment using Windows Server 2025 ARM and Windows 11 virtual machines hosted on Parallels Desktop for macOS.

The lab was designed to simulate a small enterprise environment and includes Active Directory Domain Services (AD DS), DNS, DHCP, RRAS/NAT, Group Policy, and PowerShell automation.

---

## Architecture Diagram
<img width="1536" height="1024" alt="ActiveDirectoryLabDiagram" src="https://github.com/user-attachments/assets/420162ac-1368-43e4-8853-9f0810ee3a61" />


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

<img width="1728" height="1117" alt="Screenshot 2026-05-29 at 6 04 53 PM" src="https://github.com/user-attachments/assets/8f7ce295-4c79-47d4-9d8d-179340d0394f" />


Displays installed server roles including AD DS, DNS, DHCP, and Remote Access.

---

### Active Directory Users and Computers

<img width="1728" height="1117" alt="Screenshot 2026-05-29 at 6 10 44 PM" src="https://github.com/user-attachments/assets/bfccbb10-f394-40c0-9d99-720f6f5843ac" />


Demonstrates Active Directory deployment and organizational structure.

---

### DNS Manager

<img width="1728" height="1117" alt="Screenshot 2026-05-29 at 6 14 19 PM" src="https://github.com/user-attachments/assets/894a99d3-491c-41e5-9f89-7f480857274b" />


Shows Forward Lookup Zones and domain name resolution configuration.

---

### DHCP Scope Configuration

<img width="1728" height="1117" alt="Screenshot 2026-05-29 at 6 18 51 PM" src="https://github.com/user-attachments/assets/5f44c19f-db96-4e0c-9ae0-66ab28fa9bb8" />


Displays DHCP scope settings and address allocation.

---

### RRAS/NAT Configuration

<img width="1728" height="1117" alt="Screenshot 2026-05-29 at 6 32 29 PM" src="https://github.com/user-attachments/assets/a8b9fa42-7afa-4518-9bbf-57a0f81e60c9" />


Shows NAT configuration providing internet access to internal clients.

---

### PowerShell User Provisioning

<img width="1728" height="1117" alt="Screenshot 2026-05-29 at 6 41 18 PM" src="https://github.com/user-attachments/assets/edf226db-9718-4a5b-a2b1-ef43c6999149" />


Demonstrates automation using PowerShell for Active Directory administration.

---

### Group Policy Management

<img width="1728" height="1117" alt="Screenshot 2026-05-29 at 7 58 52 PM" src="https://github.com/user-attachments/assets/1f11d9b3-ab2b-4b35-9fd8-2de3c53527b3" />


Implemented a domain-wide account lockout policy to help mitigate brute-force and password spraying attacks.

---

### Windows 11 Domain Join

<img width="1728" height="1117" alt="Screenshot 2026-05-29 at 6 47 55 PM" src="https://github.com/user-attachments/assets/d910d66e-e7d7-4849-b485-24be7c8c4667" />


Demonstrates successful integration of a Windows 11 client into the Active Directory domain.

---

### Client Network Configuration

<img width="1728" height="1117" alt="Screenshot 2026-05-29 at 6 51 20 PM" src="https://github.com/user-attachments/assets/bf748938-5f92-4a63-842a-2fd5cfb23468" />


Displays DHCP-assigned addressing and DNS configuration.

---

### Connectivity Testing

<img width="1728" height="1117" alt="Screenshot 2026-05-29 at 6 52 29 PM" src="https://github.com/user-attachments/assets/542cf5d5-2fc7-414b-a840-26d618a925f2" />


Verifies internal communication, DNS functionality, and internet connectivity through RRAS/NAT.

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

## Author

**Christian Szadolc**

Cybersecurity Graduate
Western Governors University

This project was created to develop hands-on experience with enterprise Windows infrastructure, identity management, networking, and automation in preparation for cybersecurity and security engineering roles.
