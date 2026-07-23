# Active Directory Home Lab

**Skills:** Active Directory • Windows Server • DNS • DHCP • PowerShell • Oracle VirtualBox • Active Directory Users and Computers (ADUC) • Routing and Remote Access (RRAS) • Windows Administration • Network Troubleshooting

A virtualized Active Directory environment built from scratch to simulate a small enterprise Windows domain. This project demonstrates deploying a Windows Server 2019 Domain Controller, configuring Active Directory Domain Services (AD DS), DNS, DHCP, Routing and Remote Access (RRAS), automating user creation with PowerShell, and joining a Windows 10 client to the domain.

---

# Languages & Utilities Used

- PowerShell
- PowerShell ISE
- Active Directory Users and Computers (ADUC)
- DHCP Management Console
- DNS Manager
- Routing and Remote Access (RRAS)
- Oracle VirtualBox

---

# Environments Used

- Windows Server 2019
- Windows 10
- Oracle VirtualBox

---

# Project Walkthrough

## 1. Configure the Domain Controller Virtual Machine

Configured a Windows Server 2019 virtual machine in Oracle VirtualBox with dual network adapters (NAT + Internal Network), 4 GB RAM, 4 virtual CPUs, and a 50 GB virtual disk.

![1](images/1__VM_Setup.png)

---

## 2. Install Windows Server 2019

Completed the Windows Server installation and verified the initial Server Manager dashboard after first boot.

![2](images/2__First_Wind_Loadup.png)

---

## 3. Configure a Static IP Address

Assigned a static IP address (172.16.0.1/24) to the internal network adapter and configured the server to use itself as the DNS server.

![3](images/3__ipv4_setup.png)

---

## 4. Rename the Server to DC

Renamed the server to **DC** and verified the hostname before promoting it to a domain controller.

![4](images/4__Server_Renamed.png)

---

## 5. Install Active Directory Domain Services

Installed the Active Directory Domain Services (AD DS) and DNS roles and promoted the server to a domain controller for **mydomain.com**.

![5](images/5__Active_direcory_installed.png)

---

## 6. Configure Routing and Remote Access (RRAS)

Installed and enabled Routing and Remote Access (RRAS) as part of the domain controller's network services.

![6](images/6__routing-and-remote-access-configured.png)

---

## 7. Verify Installed Server Roles

Verified that the required Windows Server roles were successfully installed and operational.

- Active Directory Domain Services
- DNS
- DHCP
- Remote Access

![7](images/7__remote_access_roles_installed.png)

---

## 8. Configure a DHCP Scope

Created a DHCP scope (172.16.0.100 – 172.16.0.200) to automatically assign IP addresses to client computers joining the internal network.

![8](images/8__dhcp_scope_configured.png)

---

## 9. Automate User Creation with PowerShell

Executed a PowerShell script that automatically generated multiple Active Directory user accounts inside the `_USERS` organizational unit.

![9](images/9__Powershell_user_creation.png)

---

## 10. Verify Active Directory User Accounts

Verified that the PowerShell script successfully created the user accounts within Active Directory Users and Computers.

![10](images/10__Active_directory_users.png)

---

## 11. Verify Client Network Connectivity

Confirmed the Windows 10 client successfully received a DHCP lease, resolved DNS, and accessed the internet through the domain controller.

![11](images/11__Client_network_connectivity.png)

---

## 12. Join the Windows Client to the Domain

Joined the Windows 10 client (**CLIENT1**) to **mydomain.com** and verified successful domain membership.

![12](images/12__Client_joined_domain.png)

---

## 13. Verify DHCP Address Lease

Confirmed the domain controller successfully issued a DHCP lease to CLIENT1.

![13](images/13__DHCP_Address_Leases.png)

---

## 14. Verify Active Directory Computer Object

Verified that CLIENT1 automatically appeared as a computer object within Active Directory Users and Computers after joining the domain.

![14](images/14__Client_1_in_active_directory.png)

---

## 15. Verify the Completed Lab Environment

Verified both the Domain Controller and Windows 10 client running simultaneously inside Oracle VirtualBox.

![15](images/15__Virtual_box_overview.png)

---

# Skills Demonstrated

- Built a Windows Server 2019 Domain Controller from scratch
- Installed and configured Active Directory Domain Services (AD DS)
- Configured DNS for Active Directory name resolution
- Configured DHCP for automatic IP address assignment
- Configured Routing and Remote Access (RRAS) as part of the server's network services
- Automated Active Directory user provisioning using PowerShell
- Joined Windows clients to an Active Directory domain
- Verified DHCP leasing, DNS resolution, and domain authentication
- Managed users and computers through Active Directory Users and Computers (ADUC)
- Built and administered a multi-machine virtual enterprise lab using Oracle VirtualBox

---

# Future Improvements

- Configure Group Policy Objects (GPOs) for password policies and security settings
- Add additional Windows clients to simulate a larger enterprise environment
- Create file shares and configure NTFS permissions
- Configure roaming profiles and folder redirection
- Integrate Sysmon and Microsoft Sentinel or Splunk for centralized logging and monitoring

---

# Credits

This project was built by following and expanding upon Josh Madakor's Active Directory Home Lab. The environment was configured independently and documented using my own implementation, screenshots, and project documentation.
