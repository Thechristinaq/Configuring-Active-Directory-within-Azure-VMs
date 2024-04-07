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

![image](https://github.com/thechristinaq/Implementing-Active-Directory-within-Azure-VMs/assets/165831241/3fd0733a-de31-44df-ae92-62ca67a129fa)

- Click into DC-1 VM, network settings, network interface/ IP configuration and set DC-1's NIC private IP address to be static and click save 

![image](https://github.com/thechristinaq/Implementing-Active-Directory-within-Azure-VMs/assets/165831241/7207c049-f8e7-4d3b-a7d4-2c1e9086a64d)

![image](https://github.com/thechristinaq/Implementing-Active-Directory-within-Azure-VMs/assets/165831241/1d2f917e-aaf2-4949-bab3-2e0a4fb96181)

- Ensure that both VM's are in the same Vnet

![image](https://github.com/thechristinaq/Implementing-Active-Directory-within-Azure-VMs/assets/165831241/b291bf82-9f92-4c8a-98e5-3647b554c444)


Step 2: Ensure Connectivity between VMs
- Log into Client-1 with remote desktop and ping DC-1's private address using perperpetual ping (ping -t "ip address") you will notice that the request is timed out 

![image](https://github.com/thechristinaq/Implementing-Active-Directory-within-Azure-VMs/assets/165831241/8a45f1cb-f2e5-4741-90ee-47b380eea905)

- Log into DC-1 with another remote desktop window and enable ICMPv4 on the local windows firewall, in the start menu, type wf.msc or firewall, click inbound rules, sort by protocol and find ICMP v4 and right click to enable rule for both ICMPs, you should see a green checkmark next to the name when you have enabled the rule 

![image](https://github.com/thechristinaq/Implementing-Active-Directory-within-Azure-VMs/assets/165831241/b0ced543-023a-40c3-b3f3-45f13d1d3361)

![image](https://github.com/thechristinaq/Implementing-Active-Directory-within-Azure-VMs/assets/165831241/148fd30f-1f05-419a-8e0e-8e966e3852bd)

- Check back in Client-1 to see if the ping had suceeded after the changes 

![image](https://github.com/thechristinaq/Implementing-Active-Directory-within-Azure-VMs/assets/165831241/76aac162-9b85-417a-9166-cda24e08b86a)


Step 3: Install Active Directory Domain
-In DC-1, you will install Active Directory using the Server Manager, click add roles and features, follow the prompt by pressing next until you reach server roles, make sure you check the box for Active Directory Domain Services, continue clicking next then install  

![image](https://github.com/thechristinaq/Implementing-Active-Directory-within-Azure-VMs/assets/165831241/8359c491-2b61-424a-a726-5925dc5bde5c)

