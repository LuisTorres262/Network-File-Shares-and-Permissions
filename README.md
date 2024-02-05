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
1. On the DC-1 VM, open up File Explorer.
</p>
<br />

<p>
<img src="https://i.imgur.com/TfvrCK0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
2. Go to the C:\ drive.
</p>
<br />

<p>
<img src="https://i.imgur.com/ZCrSD5e.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
3. Create 4 folders with the names, "read-access", "write-access", "no-access", and "accounting"
</p>
<br />


<p>
<img src="https://i.imgur.com/HgTp2PH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
4. Share the "read-access" folder with the "Domain Users" group. 
</p>
<br />


<p>
<img src="https://i.imgur.com/VEeVnly.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
5. Set the permission of the "read-access" folder to read-only. 
</p>
<br />


<p>
<img src="https://i.imgur.com/uOkJdpy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
6. Share the "write-access" folder with the "Domain users" group. Then set the permissions to "Read/Write".
</p>
<br />


<p>
<img src="https://i.imgur.com/VlzOtuQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
7. Share the "no-access" folder with the "Domain Admins" group. Then set the permissions to "Read/Write". Skip the "accounting" folder for now.
</p>
<br />


<p>
<img src="https://i.imgur.com/Ksv2EXK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
8. Go into the Client-1 Virtual Machine and navigate over to the shared folders in the C:\ drive.
<br />


<p>
<img src="https://i.imgur.com/eFMB9JR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
9. Try to access the folders you just created. Which folders can you access? Which ones can you create stuff in?
</p>
<br />


<p>
<img src="https://i.imgur.com/gJMdzb5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
10. Try to add a text document to the "read-access" folder, what do you think will happen?
</p>
<br />


<p>
<img src="https://i.imgur.com/HEDpOCQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
11. If you guessed you'd be denied access then you would be right! You only have read access so you can't add text documents. Try playing around with the other folders and see what you can and can't do.
</p>
<br />


<p>
<img src="https://i.imgur.com/BvydJ6W.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
12. Return to the DC-1 VM in Active Directory and create a security group. 
</p>
<br />


<p>
<img src="https://i.imgur.com/oZGHKd4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
13. Name the security group "ACCOUNTANTS".
</p>
<br />


<p>
<img src="https://i.imgur.com/AYTDGaQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
14. Go to the "accounting" folder you created earlier. Share the folder with the "ACCOUNTANTS" group and set the permissions to "Read/Write".
</p>
<br />


<p>
<img src="https://i.imgur.com/L04j2lu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
15. Go back to the Client-1 VM and try to access the "accounting" folder. What do you think will happen?
</p>
<br />


<p>
<img src="https://i.imgur.com/UMAbGL6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
16. It failed when you tried to access it. That is because the user on our Client-1 VM is not a part of the "ACCOUNTANTS" group which is the only group that has access to this folder. Go ahead and log out of Client-1.
</p>
<br />


<p>
<img src="https://i.imgur.com/ERscq2T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
17. Add your user to the members of the "ACCOUNTANTS" group. I am just going to add all Domain Users to the group for this example which will also add the user we are using on Client-1. 
</p>
<br />


<p>
<img src="https://i.imgur.com/swCfJkx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
18. Sign back into Client-1 and try to access the "accounting" folder. Does it work now?
</p>
<br />


<p>
<img src="https://i.imgur.com/4obOlnu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
19. It lets us open it! This tutorial is a way to show how the permissions we set on DC-1 affect how Client-1 can interact with the shared folders. You can now delete your VMs. This is the end of the tutorial.
</p>
<br />


