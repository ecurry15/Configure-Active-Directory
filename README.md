<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

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
1. The first thing we are going to do is set up the Domain Controller which is a Windows 2022 server. In Azure create a VM with the "Windows 2022 datacenter server" as the operating system and name it DC-1. Set the region to where ever is closest to you. Lastly, make sure your VM has at least 2 virtual CPUs, create a username and password, and press create.
</p>
<br />

<p>
<img src="https://i.ibb.co/jkNDbqV/step2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
2. Next, we need to make DC-1's NIC Private IP address static rather than dynamic. Click the "Networking" tab in Dc-1, click the network interface number, click IP configurations, click the private IP address, then switch from dynamic to static.
</p>
<br />

<p>
<img src="https://i.ibb.co/x5LySmf/step4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
3. Now we will install Active Directory on DC-1. Login to Dc-1 with remote desktop. Inside of DC-1, go to server manager and click "add roles and features". Install "Active Directory Domain Services".
</p>
<br />

<p>
<img src="https://i.ibb.co/HCPz08j/step5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
4. Once Active Directory is installed, look in the top right corner for a yellow exclamation mark notification. Click it, then press "Promote this server to a domain controller". Next, click add a new forest, then create a domain. My domain is "campbell.com" which is my last name. After DC-1 restarts, log back in using your domain name and login user name. Example: "labuser@campbell.com" or "campbell.com\labuser".
</p>
<br />

<p>
<img src="https://i.ibb.co/j5pBbqq/step6.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.ibb.co/GddHrzW/step7.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.ibb.co/qgbLLnZ/step9.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
5. Now that Active Directory is set up, we are going to create a few users. Go to "Active Directory Users and Computers" and create an Organizational Unit called "_EMPLOYEES". Inside the _Employees folder create an employee with your name and username as "yourname.admin". Example: "edward.admin". Next, add that employee to the "Domain Admins" security group. Now you should be able to log back into DC-1 with that admin account.
</p>
<br />

<p>
<img src="https://i.ibb.co/wyd5BkF/step3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.ibb.co/QNj3tP8/step10.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
6. Now let's create some non-Admin employees using the admin account. Once done, create a new VM in Azure with windows 10 as the operating system. Make sure the VM is in the same resource group and Vnet as DC-1. Name the VM client-1. Once the VM is created, in Azure, set Client-1's DNS settings to DC-1's Private IP address. Go to client-1's network interface settings, click "DNS Severs", click custom, then enter DC-1's private IP.
</p>
<br />

<p>
<img src="https://i.ibb.co/gz6pFch/step11.png" height="50%" width="50%"    alt="Disk Sanitization Steps"/>
</p>
<p>
7. Now we need to join client-1 to the domain we created (campbell.com). This will allow our created users/employees to login using client-1. Login to client-1, go to system, then click "Rename This PC(Advanced)", next click change, and enter the domain(campbell.com) you created in the domain field. You will need to enter the admin credentials we created on DC-1, Example(edward.admin@campbell.com). If done correctly, you should get a welcome to this domain pop-up message and a prompt to restart the VM.
</p>
<br />

<p>
<img src="https://i.ibb.co/SVtKZqF/step12.png" height="50%" width="50%"    alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.ibb.co/HDbyM42/step13.png" height="50%" width="50%"    alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.ibb.co/B2XGJ1v/step14.png" height="50%" width="50%"    alt="Disk Sanitization Steps"/>
</p>
<p>
8. Lastly, we need to allow non-Admin users access to remote desktop. login to client-1 using the admin account. Next, go to system, then click "remote desktop", then allow "domain users". The Active Directory is now completely set up and users can login remotly using client-1.
</p>
<br />
