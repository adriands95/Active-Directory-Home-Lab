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

![VM Setup](images/vm-setup.png)

---

## 2. Install Windows Server 2019

Completed the Windows Server installation and verified the initial Server Manager dashboard after first boot.

![Windows Server Install](images/windows-server-install.png)

---

## 3. Configure a Static IP Address

Assigned a static IP address (172.16.0.1/24) to the internal network adapter and configured the server to use itself as the DNS server.

![IPv4 Configuration](images/ipv4-configuration.png)

---

## 4. Rename the Server to DC

Renamed the server to **DC** and verified the hostname before promoting it to a domain controller.

![Server Renamed](images/server-renamed.png)

---

## 5. Install Active Directory Domain Services

Installed the Active Directory Domain Services (AD DS) and DNS roles and promoted the server to a domain controller for **mydomain.com**.

![Active Directory Installed](images/active-directory-installed.png)

---

## 6. Configure Routing and Remote Access (RRAS)

Installed and enabled Routing and Remote Access (RRAS) as part of the domain controller's network services.

![RRAS Configured](images/rras-configured.png)

---

## 7. Verify Installed Server Roles

Verified that the required Windows Server roles were successfully installed and operational.

- Active Directory Domain Services
- DNS
- DHCP
- Remote Access

![Server Roles Installed](images/server-roles-installed.png)

---

## 8. Configure a DHCP Scope

Created a DHCP scope (172.16.0.100 – 172.16.0.200) to automatically assign IP addresses to client computers joining the internal network.

![DHCP Scope Configured](images/dhcp-scope-configured.png)

---

## 9. Automate User Creation with PowerShell

Executed a PowerShell script that automatically generated multiple Active Directory user accounts inside the `_USERS` organizational unit.

![PowerShell User Creation](images/powershell-user-creation.png)

---

## 10. Verify Active Directory User Accounts

Verified that the PowerShell script successfully created the user accounts within Active Directory Users and Computers.

![Active Directory Users](images/active-directory-users.png)

---

## 11. Verify Client Network Connectivity

Confirmed the Windows 10 client successfully received a DHCP lease, resolved DNS, and accessed the internet through the domain controller.

![Client Network Connectivity](images/client-network-connectivity.png)

---

## 12. Join the Windows Client to the Domain

Joined the Windows 10 client (**CLIENT1**) to **mydomain.com** and verified successful domain membership.

![Client Joined Domain](images/client-joined-domain.png)

---

## 13. Verify DHCP Address Lease

Confirmed the domain controller successfully issued a DHCP lease to CLIENT1.

![DHCP Address Leases](images/dhcp-address-leases.png)

---

## 14. Verify Active Directory Computer Object

Verified that CLIENT1 automatically appeared as a computer object within Active Directory Users and Computers after joining the domain.

![Client in Active Directory](images/client-in-active-directory.png)

---

## 15. Verify the Completed Lab Environment

Verified both the Domain Controller and Windows 10 client running simultaneously inside Oracle VirtualBox.

![VirtualBox Overview](images/virtualbox-overview.png)

---

## 16. Review Default Password and Account Lockout Policy

Reviewed the default Password Policy and Account Lockout Policy settings within the Default Domain Policy to establish a baseline before applying changes.

![Password Policy Before](images/01_password-policy-before.png)
![Account Lockout Policy Before](images/03_account-lockout-before.png)

---

## 17. Configure Password and Account Lockout Policy

Configured the Default Domain Policy to enforce a 12-character minimum password length and a 5-attempt account lockout threshold with a 10-minute lockout duration.

![Password Policy After](images/02_password-policy-after.png)
![Account Lockout Policy After](images/04_account-lockout-after.png)

---

## 18. Verify Password Policy on the Client

Ran `gpupdate /force` on the domain-joined Windows 10 client and confirmed the updated password and lockout policy using `net accounts`.

![Client Password Policy Verification](images/05_client-net-accounts-proof.png)

---

## 19. Create and Link a Control Panel Restriction GPO

Created a new GPO scoped to the `_USERS` organizational unit to restrict standard users from accessing Control Panel and PC settings.

![GPOs Linked to _USERS](images/10_gpo-mapdrive-linked.png)

---

## 20. Configure the Control Panel Restriction Policy

Reviewed the default (Not Configured) state of the Control Panel policy settings, then enabled "Prohibit access to Control Panel and PC settings."

![Control Panel Setting Before](images/07_controlpanel-setting-before.png)
![Control Panel Setting After](images/08_controlpanel-setting-after.png)

---

## 21. Verify Control Panel Restriction on the Client

Logged in as a standard domain user in the `_USERS` OU and confirmed Control Panel access was successfully blocked.

![Control Panel Blocked](images/09_controlpanel-blocked-proof.png)

---

## 22. Create a Shared Folder and Configure Drive Mapping GPO

Created and shared a folder (`CompanyShare`) on the domain controller, then configured a GPO Preference to automatically map it as a network drive for users in the `_USERS` OU.

![Drive Maps Before](images/11_drivemaps-before.png)
![Drive Maps After](images/12_drivemaps-after.png)

---

## 23. Verify Mapped Network Drive on the Client

Confirmed the mapped network drive appeared automatically under "This PC" after logging in as a domain user in the `_USERS` OU.

![Mapped Drive Verified](images/13_client-mapped-drive-proof.png)

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
- Configured Group Policy Objects (GPOs) to enforce domain-wide password and account lockout policies
- Applied OU-scoped GPOs to restrict user access and automate network drive mapping
- Verified Group Policy application on a domain-joined client using `gpupdate` and `net accounts`
---

# Future Improvements

- Add additional Windows clients to simulate a larger enterprise environment
- Create file shares and configure NTFS permissions
- Configure roaming profiles and folder redirection
- Integrate Sysmon and Microsoft Sentinel or Splunk for centralized logging and monitoring

---

# Credits

This project was built by following and expanding upon Josh Madakor's Active Directory Home Lab. The environment was configured independently and documented using my own implementation, screenshots, and project documentation.
