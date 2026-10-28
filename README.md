# Azure-Active-Directory-Helpdesk-Lab-Project

# 01 - Setup: Domain controller in Azure

Built a Windows Server VM in Azure and turned it into an Active Directory domain controller for a practice helpdesk environment.

## 1. Deploy the VM
- Created a resource group (`rg-helpdesk-lab`) in UK South
- Deployed a Windows Server VM named `dc01` (Standard D2als v6)
- Connected with Remote Desktop from a MacBook

<img width="1436" height="757" alt="Screenshot 2026-10-28 at 04 39 40" src="https://github.com/user-attachments/assets/377c778c-bbe8-47c4-be01-af0433259955" />


## 2. Allow secure remote access
RDP failed with error 0x704 because the network security group only allowed my old IP. I updated the inbound rule for port 3389 to my current IP (/32) instead of opening it to the internet. Full details in the troubleshooting log.

![NSG inbound rules](images/01-nsg-rules.png)

## 3. Install the roles
Installed Active Directory Domain Services, DNS and File and Storage Services using Server Manager.

![Server Manager showing roles](images/01-server-manager-roles.png)

## 4. Promote to a domain controller
Promoted the server with a new forest, `lab.local`, and confirmed it with PowerShell:

`Get-ADDomain`

<img width="1440" height="900" alt="Screenshot 2026-10-27 at 04 57 27" src="https://github.com/user-attachments/assets/a0b41ad6-a907-4956-86c7-96458a1edafc" />


## Result
`dc01.lab.local` is a working domain controller, ready for user and group management.
