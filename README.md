# azure-on-prem-ad
<p align="center">
<img src="https://i.imgur.com/9Fezpa3.png" alt="osTicket logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

 <h2>Environments and Technologies Used</h2>

 - Microsoft Azure (Virtual Machines/Compute)
 - Remote Desktop
- Active Directory Domain Services 

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Windows Server 2022

<h2>High-Level Deployment and Configuration Steps</h2>

- Deploy a Domain Controller VM and Client VM
- Install Active Directory
- Create Admin/User Accounts in Active Directory
- Join Client VM to newly created Domain
- Allow Remote Desktop for non-admin users on Client VM
- Test User Account and Account Configuration

 <h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/ZnqSSGH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/DB18ams.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 1:

- Create a new Virtual Machine (VM) in Azure.
- Select "Windows Server 2022" as the operating system.
- Name the VM "DC-1" and place it in a resource group named "RG-AD".
- Configure the VM with 2vcpus and 16 GiB of memory.
- Create a new "Virtual network" named "RG-AD-vnet" under the "Networking" tab.
- Complete the VM creation process.
</p>
<br />

<p>
<img src="https://i.imgur.com/MTjgDmh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/uvsByEc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 2:

- Access the DC-1 VM in Azure.
- Navigate to the "Networking" tab.
- Click on "Network Interface" and go to the "IP configurations" tab.
- Set "Allocation" to "Static" for "ipconfig1" and save the settings.
</p>
<br />

<p>
<img src="https://i.imgur.com/GoCepp3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/UX2wJqH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 3:

- Create a new Client VM in Azure.
- Choose "Windows 10 Pro, version 22H2" as the operating system.
- Name the VM "Client-1" and place it in the "RG-AD" resource group.
- Configure the VM with 2vcpus and 16 GiB of memory.
- Ensure the VM is placed in the "RG-AD-vnet" Virtual network.
- Complete the VM creation process.
</p>
<br />

<p>
<img src="https://i.imgur.com/mOnHaSc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
  <p>
<img src="https://i.imgur.com/3QedF5p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/PCeVpFC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/CVXMpvb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/ZDBGhZt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
Step 4:

- Log in to the DC-1 VM.
- Open the "Service Manager" application.
- Click on "Add roles and features" under "Configure this local server".
- Select "Active Directory Domain Services" in the setup wizard and proceed with the installation.
- After installation, click on the flag icon and select "Promote this server to a domain controller".
</p>
<br />

<p>
<img src="https://i.imgur.com/NiwheBJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/3Ext0r5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/C0cs299.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 5:

- In the configuration wizard, choose "Add a new forest" and enter "mydomain.com" as the domain name.
- Set the password to "Labpassword1" and complete the installation process.
- Wait for the VM to restart.
</p>
<br />

<p>
<img src="https://i.imgur.com/FCAgaWI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/CfiP5Dt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/X3ccqC9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Step 6:

- Log back into DC-1 and open "Server Manager".
- Navigate to "Tools" and click on "Active Directory Users and Computers".
</p>
<br />

<p>
<img src="https://i.imgur.com/ElTZqtj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/cvxO6O7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/DQ8yGMo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 7:

- Create two new Organizational Units (OUs) named "_EMPLOYEES" and "_ADMINS" under "mydomain.com".
</p>
<br />

<p>
<img src="https://i.imgur.com/tHVDWVj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/CHr8BlZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/28aJKoc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
 <p>
<img src="https://i.imgur.com/yHG8tOo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 8:

- Inside the "_ADMINS" (OU), create a new user named "Jane Doe" with the username "jane_admin" and password "Labpassword1".
</p>
<br />

<p>
<img src="https://i.imgur.com/C5e9QsE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/UUXJqh9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/y10Y1ev.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
 <p>
<img src="https://i.imgur.com/ZZrexBx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
 <p>
<img src="https://i.imgur.com/YNFkboN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 9:

- Make "Jane Doe" a member of the "Domain Admins" group.
- Log out of DC-1 and log back in with the "jane_admin" account.
</p>
<br />

<p>
<img src="https://i.imgur.com/MwJK0tM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/YB71A0Z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/tPq5ppr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
 <p>
<img src="https://i.imgur.com/XMUgpz5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 10:

- Copy the private IP of DC-1 from the Azure portal.
- Navigate to Client-1's VM page and configure the DNS server settings to point to DC-1's private IP.
- Restart the Client-1 VM.
</p>
<br />

<p>
<img src="https://i.imgur.com/iPtDmMi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/97AQmav.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/NtdhRPA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Step 11:

- Log in to Client-1 and join it to the "mydomain.com" domain using the "jane_admin" account.
- Wait for the domain join process to complete.
</p>
<br />

<p>
<img src="https://i.imgur.com/gBhL4LS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/0nVMANH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/GANULBT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 12:

- Log in to Client-1 as "mydomain.com\jane_admin" and configure remote desktop access for "Domain Users".
</p>
<br />

<p>
 <p>
<img src="https://i.imgur.com/3QedF5p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/ONvzHgl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/rZTAvT6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/dO9BLy1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/W7Vv6hx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 13:

- Log back into DC-1 and create a new user in the "_EMPLOYEES" folder following the same steps as for "Jane Doe".
</p>
<br />

<p>
<img src="https://i.imgur.com/a3FrGkD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/ZxnmKS0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 14:

- Log in to Client-1 with the newly created user account "kayla.mann".
- Confirm the ability to create and configure admins and users within Active Directory.
</p>
<br />
