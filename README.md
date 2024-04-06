<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Implementing Active Directory within Azure VMs </h1>
This tutorial outlines the implementation of configuring Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Setup Resources in Azure
- Step 2: Ensure Connectivity between VMs
- Step 3: Install Active Directory Domain
- Step 4: Creating Organizational Units (OU)
- Step 5: Connecting to the Domain
- Step 6: Setup Remote Desktop for Non-Admin Users
- step 7: Testing New User Accounts  

<h2>Deployment and Configuration Steps</h2>

Step 1: Setup Resources in Azure
- Create a Domain Controller VM (DC-1) in Windows Server 2022, then create another VM in Windows 10 (Client-1) using the same resource group and Vnet
- Set DC-1's NIC private IP address to be static
- Ensure that both VM's are in the same Vnet 
