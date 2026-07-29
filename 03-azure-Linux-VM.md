# Part 3 - Linux Management Server Deployment 

## Objective 

Deploy the first enterprise Linux management server into the Azure lab environment 
This VM will serve the admin server for future cloud projects including:

-Azure CLI administration
-Linux system admin
-Wazuh Agent 
-Azure Monitor Agent 
-SSH administration 
-Automation with Bash 
-Terraform (future)[

# Enterprise Architecture

Internet 
    |
    | SSH (TCP 22)
    ▼
Azure Public IP
    |
    ▼
vm-linux-mgmt-lab-eus-01
    |
    ▼
snet-management-lab-eus-01
    |
    ▼
vnet-azsec-lab-eus-01
    |
    ▼
Azure Subscription


---

# Why this Server Exist 

From my research an enterprise enviorment administrator rarely log direcrtly into production servers. Instead organization usally have dedicated management systems that are  used to:

-administer infrastructure 
-run scripts 
-deploy updates 
-investigate incidennts 
-perform threat hunting 
-manage Azure resources 

This VM represents that management system 

---

# Resoureces Created 

## Compute 

vm-linux-mgmt-lab-eus-01

OS -> Ubuntu Server 24.04 LTS

Architecture -> x64

VM Size -> Standard D2as_v7

Pricing Model -> Azure Spot 

Eviction Policy -> Stop / Deallocate

---

## Storage 

OS Disk -> Standard SSD LRS

Delete with VM -> Enabled 

Managed Disk -> Yes 

--- 

## Networking 

Virtual Network -> vnet-azsec-lab-eus-01

Subnet -> snet-management-lab-eus-01

Public IP -> vm-linux-mgmt-lab-eus-01-ip

NIC NSG -> None 

Subnet NSG -> nsg-management-lab-eus-01

Accelerated Networking -> Enabled 

--- 

## Security

Trusted Launch -> Enabled

Secure Boot -> Enabled

vTPM -> Enabled

System Managed Identity -> Enabled

SSH Authentication -> Enabled

Password Authentication -> Disabled

---

## Monitoring

Boot Diagnostics -> Enabled

Guest Diagnostics -> Disabled

Alerts -> Disabled

Backup -> Disabled

Auto Shutdown -> Enabled

---

# Cost Consideration 

This VM is deployed using Azure Spot pricing.

Advantages 

- significantly lower compute cost 
- excellent for labs
- fits within Azure Free trial credit

Disadvantages

- Azure may reclaim the VM
-no production SLA
-not appropriate for production servers

Additional costs include:

- Managed OS Disk
- Public IP
- Network traffic (if applicable)

The VM should be stopped (deallocated) after each lab session to minimize compute charges.

---

# Security Decisions

## SSH Keys

SSH Public Key Authentication

Benefits 

- resistant to password guessing 
- more secure 
-enterprise best practice 

--- 

## Trusted Launch

Enabled:

- Secure Boot
- vTPM

---
 
## Network Security

The VM does not have its own NSG.

Instead it inherits security policies from:

nsg-management-lab-eus-01

This simplifies management while ensuring consistent security across the management subnet.

---

### Problems 

During this part of the Lab was trying to figure out the best way to budget $200 free credits while picking a good VM. Also creating the virtual machine needs to be in the same region as the NSG after finding this out I changed all the rg's and nsg's to US east. 




 