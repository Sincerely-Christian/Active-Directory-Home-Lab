# Troubleshooting and Lessons Learned

## Overview

While building this Active Directory environment, several issues were encountered that required investigation, testing, and remediation. The purpose of this document is to record those challenges, their root causes, and the solutions implemented.

---

# Issue 1: Adapting a VirtualBox Lab to Parallels Desktop

## Problem

The original lab design was based on Oracle VirtualBox networking. This project was implemented using Parallels Desktop on macOS, which uses different networking terminology and adapter configurations.

## Impact

Several tutorial steps could not be followed directly because VirtualBox Internal Networks and Host-Only Networks behave differently from Parallels networking options.

## Resolution

A two-network design was implemented:

### External Adapter

Used for internet access.

```text
Network Type: Shared / NAT
Address Assignment: DHCP
```

### Internal Adapter

Used for Active Directory communication.

```text
Network Type: Host-Only / Internal Network
Network: 172.16.0.0/24
```

This provided separation between the internal domain environment and the external internet connection.

---

# Issue 2: DNS Validation During AD DS Deployment

## Problem

During Active Directory Domain Services installation, DNS validation warnings and configuration errors were encountered.

## Impact

DNS is a critical dependency for Active Directory. Incorrect DNS configuration can prevent domain services from functioning properly.

## Investigation

The server's internal adapter configuration and DNS settings were reviewed.

The following were verified:

* Static IP configuration
* DNS service installation
* Forward Lookup Zone creation
* Domain name resolution

## Resolution

The Domain Controller was configured with a static internal address and DNS services were verified before completing Active Directory deployment.

Result:

```text
Active Directory installation completed successfully.
Domain name resolution functioned correctly.
```

---

# Issue 3: Internal Adapter Addressing Problems

## Problem

The internal network adapter experienced addressing inconsistencies during initial configuration.

## Impact

Clients could not consistently communicate with the Domain Controller.

## Investigation

Adapter settings were reviewed using:

```powershell
ipconfig /all
```

Network assignments and static configuration were validated.

## Resolution

The internal adapter was assigned:

```text
IP Address: 172.16.0.1
Subnet Mask: 255.255.255.0
Gateway: None
```

The adapter was isolated from internet routing and dedicated exclusively to internal Active Directory services.

---

# Issue 4: RRAS and NAT Configuration

## Problem

Domain clients initially received addresses but were unable to access external internet resources.

## Impact

Clients could authenticate to the domain but could not reach external websites.

## Investigation

Routing and Remote Access Services configuration was reviewed.

The relationship between:

* Internal Interface
* External Interface
* NAT Configuration

was verified.

## Resolution

RRAS was configured with:

```text
External Interface = Public
Internal Interface = Private
NAT Enabled
```

Result:

```text
Domain clients successfully accessed internet resources.
Internal DNS resolution continued functioning correctly.
```

---

# Issue 5: DHCP Scope Configuration

## Problem

Proper DHCP configuration was required to automatically provision domain clients.

## Resolution

A DHCP scope was created using:

```text
Network: 172.16.0.0/24
Range: 172.16.0.100 - 172.16.0.200
Gateway: 172.16.0.1
DNS Server: 172.16.0.1
```

Result:

```text
Clients automatically received valid network configuration.
```

---

# Issue 6: Windows Server 2025 ARM Deployment

## Problem

Most publicly available Active Directory tutorials use:

* Windows Server 2019
* Windows Server 2022
* x86 Virtual Machines

This project was completed using:

```text
Windows Server 2025 ARM
Parallels Desktop
macOS Host
```

## Impact

Documentation and screenshots often differed from the actual environment.

## Resolution

Core Active Directory concepts remained unchanged.

Services successfully deployed:

* Active Directory Domain Services
* DNS
* DHCP
* RRAS/NAT
* Group Policy
* PowerShell Administration

This demonstrated the ability to adapt enterprise infrastructure concepts to newer platforms rather than relying on a tutorial's exact configuration.

---

# Security Controls Implemented

The following security-related configurations were implemented during the project:

## Account Lockout Policy

Configured through Group Policy Management.

```text
Account Lockout Threshold: 5 invalid logon attempts
Lockout Duration: 15 minutes
Reset Counter After: 10 minutes
```

Purpose:

* Mitigate brute-force attacks
* Reduce password spraying risk
* Demonstrate domain-level security policy management

---

# Key Lessons Learned

* Active Directory depends heavily on proper DNS configuration.
* Network troubleshooting is often the most time-consuming portion of deployment.
* Virtualization platforms implement networking differently.
* RRAS/NAT configuration requires careful interface assignment.
* Infrastructure deployment requires adaptation when documentation and environments differ.
* Troubleshooting and validation are as important as installation itself.

---

# Final Outcome

The completed environment successfully provides:

* Active Directory Domain Services
* DNS
* DHCP
* Group Policy Management
* PowerShell Administration
* RRAS/NAT Routing
* Windows 11 Domain Client Integration
