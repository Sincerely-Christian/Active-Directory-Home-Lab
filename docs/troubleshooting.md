# Troubleshooting and Lessons Learned

## Overview

This project involved deploying a Windows Active Directory environment using Windows Server 2025 ARM and Windows 11 virtual machines hosted on Parallels Desktop for macOS.

While building the environment, several technical challenges were encountered involving operating system deployment, networking, Active Directory services, and routing configuration. Resolving these issues provided valuable hands-on experience with enterprise Windows infrastructure.

---

## Challenge 1: Obtaining a Compatible Windows Server 2025 ARM Installation Image

### Problem

The original lab environment was designed around Windows Server 2019 running on x86 hardware. Because the lab was built on an Apple Silicon Mac using Parallels Desktop, a compatible ARM version of Windows Server was required.

### Investigation

Microsoft does not currently provide a standard Windows Server ARM ISO through the same channels used for traditional x86 deployments. Research was conducted to identify a compatible ARM-based installation source that could be deployed within Parallels Desktop.

### Resolution

A Windows Server 2025 ARM installation image was successfully obtained and deployed. This allowed the Domain Controller to run natively on Apple Silicon while maintaining compatibility with Active Directory, DNS, DHCP, RRAS, and Group Policy services.

### Lesson Learned

Modern virtualization platforms increasingly require consideration of processor architecture compatibility. Understanding the differences between ARM and x86 deployments is becoming an important infrastructure skill.

---

## Challenge 2: Internal Network Adapter Configuration

### Problem

The Domain Controller required both an external interface for internet access and an internal interface for domain services. Initial network configuration issues prevented proper communication between services.

### Investigation

Network settings were reviewed using:

* ipconfig /all
* Network Connections
* DNS Manager
* DHCP Manager

The issue was traced to internal adapter configuration and addressing inconsistencies.

### Resolution

The internal adapter was configured with a static address:

* IP Address: 172.16.0.1
* Subnet Mask: 255.255.255.0

This provided a stable foundation for Active Directory, DNS, and DHCP services.

### Lesson Learned

Active Directory environments depend heavily on proper network planning and static infrastructure addressing.

---

## Challenge 3: DNS Validation During Active Directory Deployment

### Problem

DNS validation errors occurred during the Domain Controller promotion process.

### Investigation

DNS configuration was reviewed to verify:

* DNS role installation
* Forward Lookup Zones
* Domain registration
* Adapter DNS settings

### Resolution

DNS services were configured and validated prior to completing Active Directory promotion. After correction, domain records registered successfully and Active Directory deployment completed without further issues.

### Lesson Learned

DNS is a foundational dependency for Active Directory. Proper DNS configuration should always be verified before troubleshooting higher-level directory services.

---

## Challenge 4: RRAS and NAT Configuration

### Problem

The Windows 11 client successfully joined the domain but initially lacked internet access.

### Investigation

Connectivity testing was performed using:

* ping
* ipconfig
* nslookup

RRAS configuration was reviewed to verify public and private interface assignments.

### Resolution

RRAS was configured with:

* External NIC designated as the public interface
* Internal NIC designated as the private interface
* NAT enabled on the public interface

After configuration, domain clients successfully accessed external resources through the Domain Controller.

### Lesson Learned

Routing services must be configured carefully in multi-homed server environments. Understanding traffic flow between public and private interfaces is critical for successful network design.

---

## Key Takeaways

This project provided practical experience in:

* Active Directory Administration
* DNS Infrastructure
* DHCP Management
* RRAS/NAT Configuration
* Group Policy Administration
* Windows Server Troubleshooting
* Network Segmentation
* PowerShell Administration
* Virtualized Infrastructure Deployment

The project reinforced the importance of structured troubleshooting, service dependency awareness, and network design when deploying enterprise Windows infrastructure.
