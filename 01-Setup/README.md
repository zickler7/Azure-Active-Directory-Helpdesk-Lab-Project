# Azure Helpdesk Lab

A hands-on IT service desk lab built in Microsoft Azure. I built it to practise the day-to-day skills of a 1st line support role: managing users in Active Directory, scripting repetitive admin tasks, troubleshooting faults and writing clear documentation.

## Environment

- Windows Server virtual machine (`dc01`) hosted in Azure, UK South
- Active Directory Domain Services and DNS, domain `lab.local`
- Managed from a MacBook over Remote Desktop
- PowerShell for administration

## Skills demonstrated

- Deploying and securing a cloud VM (network security group rules, restricted RDP access)
- Promoting a server to a domain controller
- Creating and managing AD users, groups and OUs with PowerShell
- Diagnosing and fixing connectivity problems
- Writing step-by-step technical documentation

## Contents

| Section | Description | Status |
|---|---|---|
| [01-Setup](01-Setup/README.md) | Deploying the VM, installing AD DS and DNS, promoting the DC | In progress |
| 02-onboarding-offboarding | PowerShell user onboarding and offboarding | In progress |
| 03-troubleshooting-log | Faults I hit and how I fixed them | Planned |
| 04-knowledge-base | How-to articles for common helpdesk requests | Planned |

## Example from the troubleshooting log

**Symptom:** Remote Desktop failed with error 0x704 when connecting to the VM.
**Diagnosis:** The network security group only allowed RDP (port 3389) from my previous IP address.
**Fix:** Updated the inbound rule to my current public IP with a /32 mask, rather than opening the port to the whole internet.

## Security notes

No credentials, subscription IDs or public IP addresses are stored in this repo. The VM is deallocated when not in use to avoid unnecessary cost.
