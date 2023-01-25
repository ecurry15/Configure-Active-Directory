<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used</h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1  - Setup Azure Domain Controller (windows server) and Azure Client (Windows 10) VMs.
- Step 2  - Install Active Directory in the Domain Controller.
- Step 3  - Join Client VM to the Active Directory Domain.
- Step 4  - Setup remote desktop login for Admin and non-Admin users/ create user accounts.

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.ibb.co/jJKvbqb/step1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The first thing we are going to do is setup the Domain Contoller which is a Windows 2022 server. In Azure create a VM with the "Windows 2022 datacenter server" as the operating system and name it DC-1. Set the region to where ever is closest to you. Lastly, make sure your VM has at least 2 virtual CPUs, create a username and password, and press create.
</p>
<br />

<p>
<img src="https://i.ibb.co/jkNDbqV/step2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, we need to make DC-1's NIC Private IP address static rather than dynamic. Click the "Networking" tab in Dc-1, click the network interface number, click IP configurations, click the private IP address, then switch from dynamic to static.
</p>
<br />

<p>
<img src="https://i.ibb.co/x5LySmf/step4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we will install Active Directory on DC-1. Login to Dc-1 with remote desktop. Inside of DC-1, go to server manager and click "add roles and features". Install "Active Directory Domain Services".
</p>
<br />

<p>
<img src="https://i.ibb.co/HCPz08j/step5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once Active Directory is installed, look in the top right corner for a yellow exclamation mark notification. Click it, then press "Promote this server to a domain controller. Next, click add a new forest, then create a domain. My domain is "campbell.com" which is my last name. After DC-1 restarts, log back in using your domain name and login user name. Example: "labuser@campbell.com" or "campbell.com\labuser".
</p>
<br />

<p>
<img src="https://i.ibb.co/j5pBbqq/step6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.ibb.co/GddHrzW/step7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now that Active Directory is setup we are going to create a few users. Go to "Active Directory Users and Computers" and create an Organizational Unit called "_EMPLOYEES". Inside the employees folder create an employee with your name and username as "yourname.admin". Example: "edward.admin". Next add that employee to the "Domain Admins" security group.
</p>
<br />
