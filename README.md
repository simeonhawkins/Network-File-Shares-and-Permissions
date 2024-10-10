<p align="center">
<img src="https://github.com/user-attachments/assets/ae64f2c3-0754-4a6f-8e8d-c3a837b42cdd" alt="osTicket logo"/>
</p>


# Network File Shares and Permissions

In this tutorial, we will configure shared network files and set appropriate permissions for various folders on Azure Virtual Machines.

<h2>Environments and Technologies Used</h2>

	•	Microsoft Azure (Virtual Machines/Domain Controller/Client Machine)
	•	Remote Desktop
	•	Shared Network Files

<h2>Operating Systems Used</h2>

	•	Windows 10 (21H2)

<h2>Lab Overview</h2>

In this lab, we will create shared network folders on the DC-1 virtual machine and assign specific permissions to each folder. The objective is to allow or restrict access based on user roles and security groups. Only designated users will be able to view or modify certain files.

Step 1: Create Network Folders on DC-1

	1.	Log in to the DC-1 Virtual Machine.
	2.	Navigate to the C: drive.
	3.	Create four folders:
	•	read-access
	•	read-write-access
	•	no-access
	•	accounting

<p align="center">
<img src="https://i.imgur.com/k70dozS.png" height="80%" width="80%" alt="Creating Folders on DC-1"/>
</p>


Step 2: Configure Sharing and Permissions

	•	Share each folder on the network and set the following permissions:

	1.	read-access:
	•	Permissions: Read-only access for Domain Users.
	2.	read-write-access:
	•	Permissions: Read/Write access for Domain Users.
	3.	no-access:
	•	Permissions: Read/Write access for Domain Admins only.

<p align="center">
<img src="https://i.imgur.com/wcpB5Ex.png" height="80%" width="80%" alt="Setting Permissions"/>
</p>


	•	Ensure that the correct permissions are applied to each folder to limit access based on user roles.

<p align="center">
<img src="https://i.imgur.com/hku11Pt.png" height="80%" width="80%" alt="Configuring Folder Access"/>
</p>


Step 3: Test Folder Permissions on Client Machine

	•	Log in to the Client-1 machine using a normal user account.
	•	Try accessing each of the shared folders:
	1.	read-access: The user should have read-only access.
	2.	read-write-access: The user should be able to read and modify files.
	3.	no-access: The user should be denied access.

<p align="center">
<img src="https://i.imgur.com/CGQ8yaO.png" height="80%" width="80%" alt="Testing Permissions on Client Machine"/>
<img src="https://i.imgur.com/f9TldBO.png" height="80%" width="80%" alt="Access Denied for No-Access Folder"/>
</p>


Step 4: Create a Security Group for the “Accountants” Folder

	•	Go back to the DC-1 VM.
	•	Open Active Directory Users and Computers.
	•	Create a new security group named Accountants.

	1.	Accounting Folder:
	•	Share the accounting folder with Accountants security group only.
	•	Remove access for other users.
	2.	Add Users to the Group:
	•	Assign the appropriate users to the Accountants group.
	•	Only users in this group will have access to the accounting folder.

<p align="center">
<img src="https://i.imgur.com/QADy92Z.png" height="80%" width="80%" alt="Creating Accountants Security Group"/>
<img src="https://i.imgur.com/BUm3L2Q.png" height="80%" width="80%" alt="Configuring Security Group Permissions"/>
</p>


Step 5: Verify Access for the Accounting Folder

	•	Log in to Client-1 with a normal user account and attempt to access the accounting folder.
	•	You should receive an access denied message unless the user is part of the Accountants security group.
	•	Test with an Accountants Group Member:
	•	Log in with an account that is a member of the Accountants group.
	•	The user should be able to access the accounting folder successfully.

<p align="center">
<img src="https://i.imgur.com/fH8fU7b.png" height="80%" width="80%" alt="Verifying Access for Accounting Folder"/>
</p>


<h2>Summary</h2>

	•	We set up shared network folders on the DC-1 server and configured specific permissions.
	•	Different users and security groups were tested to verify access based on the permissions set.
	•	This lab provided hands-on experience in configuring and managing network file shares and access permissions in a domain environment.

This setup helps maintain a secure and organized file-sharing environment, ensuring that sensitive data is accessible only to authorized personnel. Let me know if you have any questions or need further adjustments!
