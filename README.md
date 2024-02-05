# Network-File-Shares-and-Permissions

<p align="center">
<img src="https://i.imgur.com/qkiZUmM.png" alt="osTicket logo"/>
</p>

<h1>Network File Shares and Permissions walkthrough</h1>
In this tutorial, we will be sharing out resources over the network and creating file shares to allow read, write, or deny access to individual users or groups.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Windows Server 2022</b> (21H2)


<h2>Prerequesites</h2>

You will need to create 2 virtual machines in Azure. One will be the domain controller (DC-1) which will be using Windows Server 2022 and will have Active Directory running. The other will be the user end (Client-1) that will be running Windows 10 and will need to be joined to the domain of DC-1. We will be switching between both virtual machines. 

<h2>Tutorial Steps</h2>

<p>
<img src="https://i.imgur.com/KlOFvtb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On the DC-1 VM, open up File Explorer.
</p>
<br />

<p>
<img src="https://i.imgur.com/TfvrCK0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to the C:\ drive.
</p>
<br />

<p>
<img src="https://i.imgur.com/ZCrSD5e.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create 4 folders with the names, "read-access", "write-access", "no-access", and "accounting"
</p>
<br />


<p>
<img src="https://i.imgur.com/HgTp2PH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Share the "read-access" folder with the "Domain Users" group. 
</p>
<br />


<p>
<img src="https://i.imgur.com/VEeVnly.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Set the permission of the "read-access" folder to read-only. 
</p>
<br />


<p>
<img src="https://i.imgur.com/uOkJdpy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Share the "write-access" folder with the "Domain users" group. Then set the permissions to "Read/Write".
</p>
<br />


<p>
<img src="https://i.imgur.com/VlzOtuQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Share the "no-access" folder with the "Domain Admins" group. Then set the permissions to "Read/Write". Skip the "accounting" folder for now.
</p>
<br />


<p>
<img src="https://i.imgur.com/Ksv2EXK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go into the Client-1 Virtual Machine and navigate over to the shared folders in the C:\ drive.
<br />


<p>
<img src="https://i.imgur.com/eFMB9JR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Try to access the folders you just created. Which folders can you access? Which ones can you create stuff in?
</p>
<br />


<p>
<img src="https://i.imgur.com/gJMdzb5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Try to add a text document to the "read-access" folder, what do you think will happen?
</p>
<br />


<p>
<img src="https://i.imgur.com/HEDpOCQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
If you guessed you'd be denied access then you would be right! You only have read access so you can't add text documents. Try playing around with the other folders and see what you can and can't do. This is a way to see how the permissions we set on DC-1 affect how Client-1 can interact with the shared folders.
</p>
<br />


<p>
<img src="https://i.imgur.com/BvydJ6W.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Return to the DC-1 VM in Active Directory and create a security group. 
</p>
<br />


<p>
<img src="https://i.imgur.com/oZGHKd4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Name the security group "ACCOUNTANTS".
</p>
<br />


<p>
<img src="https://i.imgur.com/AYTDGaQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to the "accounting" folder you created earlier. Share the folder with the "ACCOUNTANTS" group and set the permissions to "Read/Write".
</p>
<br />


<p>
<img src="https://i.imgur.com/L04j2lu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to the Client-1 VM and try to access the "accounting" folder. What do you think will happen?
</p>
<br />


<p>
<img src="https://i.imgur.com/UMAbGL6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
It failed when you tried to access it. That is because the user on our Client-1 VM is not a part of the "ACCOUNTANTS" group which is the only group that has access to this folder. Go ahead and log out of Client-1.
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
