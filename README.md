<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Azure
- Install Active Directory
- Create an Admin and Normal User Account
- Join Client-1 to domain
- Create additional users and log in

<h2>Setup Resources in Azure</h2>

<p>
<img src="https://i.imgur.com/3HsTGy9.png" height="80%" width="80%" alt="DC-1 virtual machine created"/>
<img src="https://i.imgur.com/d0uezQZ.png" height="80%" width="80%" alt="perpetual ping"/>
</p>
<p>
I created virtual machines for Domain Controller (DC-1) and Client using the same resource group and Vnet. After logging in to each virtual machine, I ensured the connection with a perpetual ping to DC-1's private ip address from Client.
</p>
<br />

<p>
<img src="https://i.imgur.com/VACXY17.png" height="80%" width="80%" alt="new foreest and organizational units"/>
</p>
<p>
From DC-1, I set up a new forest as mydomain.com. Then, within Active Directory Users and Computers, I created organizational units named _EMPLOYEES and _ADMINS to host my additional users I later created. Next, I created a new employee with the username jane_admin and added this user to the "Domain Admins" security group. 

</p>
<br />

<p>
<img src="https://i.imgur.com/u738g5Q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After I set Client-1's DNS settings to the private IP address of DC-1 I logged in as Jane Doe under mydomain.com to give the option of remote desktop to the domain users. 
<img src="https://i.imgur.com/wkdo76u.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
  
</p>
Then I logged in to DC-1 as Jane Doe, opened Powershell as an administrator and ran a script that created thousands of random user accounts.
<p>
<img src="https://i.imgur.com/5HtgtHQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Finally, to test the script I logged in as one of the random users.  
<br />
