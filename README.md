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
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
