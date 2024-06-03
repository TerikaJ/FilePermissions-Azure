<h1>File Permissions Configuration and Management</h1>

![ga-security-risks-of-file-transfers-850x330](https://github.com/TerikaJ/FilePermissions-Azure/assets/136477450/334719c6-0040-40bd-8ffa-7940752e80f8)

This lab focuses on file permissions and shares within an Active Directory domain, essential components in a business environment to ensure users have the appropriate access to the files they need. Building on our previous Active Directory lab where **Client-01** was joined to the domain **`mydomain.com`** on **DC-01**, I am logged in as an administrator (**mydomain.com\jane_admin**) on the **DC_01** VM and as a normal user on the **Client-01** VM. This project will demonstrate the practical steps to configure and manage file permissions and shares, highlighting their importance in maintaining a secure and efficient domain environment.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022 (Domain Controller - **DC-01**)
- Windows 10 Pro (21H2) (Client - **Client-01**)

<h2>File Permission Configuration Steps</h2>

① While logged in to the domain controller VM as an admin, create the folders on the C:\ drive.

② Ensure you have created 4 appropriately named folders for setting permissions.

③ To share a folder and assign permissions, open the folder's Properties and click on Share under the Sharing tab.

④ Specify people on the network to share with and assign appropriate permissions.

⑤ Set the following permissions for the folders:
    - Domain Users can Read the read-access folder and have Read/Write permissions on the write-access folder.
    - Domain Admins have Read/Write access to the no-access folder.

⑥ On the client VM, navigate to the shared folders through the following path in File Explorer: \\dc-1.

⑦ Notice how some folders only allow you to view files, while one doesn't allow access at all.

⑧ This is because as a Domain User, permissions for the folder are tied to the respective Security Group and the folder's own set permissions for users within that Security Group.


<img src="https://i.imgur.com/bUjobDC.png" height="80%" width="80%" alt="Permissions Steps"/>
<img src="https://i.imgur.com/lz1DMos.png" height="80%" width="80%" alt="Permissions Steps"/>



<img src="https://i.imgur.com/kWrpLFE.png" height="80%" width="80%" alt="Permissions Steps"/>


<img src="https://i.imgur.com/NgM0CcI.png" height="80%" width="80%" alt="Permissions Steps"/>
<img src="https://i.imgur.com/I4k9T2J.png" height="80%" width="80%" alt="Permissions Steps"/>

<h2>Management Steps</h2>

① On the domain controller, open the Active Directory Users and Computers panel.

② Create a new Group called ACCOUNTANTS.

③ After creating the new Group, go to the accounting folder and assign permissions to the folder so the ACCOUNTANTS Group has Read/Write permissions.

④ The user cannot access the accounting folder because they are not part of the ACCOUNTANTS Security Group.

⑤ Log off the client so that the permissions are in place by the time the client is logged into again.

⑥ On the domain controller, open the ACCOUNTANTS Properties on Active Directory Users and Computers.

⑦ In the Members tab, add the respective user.

⑧ In your case, it is bon.rovej.

⑨ Upon logging into the client, bon.rovej is now able to open the accounting folder because they are part of ACCOUNTANTS.


<img src="https://i.imgur.com/xev1Svv.png" height="80%" width="80%" alt="Permissions Steps"/>
<img src="https://i.imgur.com/SHotVB2.png" height="80%" width="80%" alt="Permissions Steps"/>




<h2>Conclusion</h2>

This project has provided hands-on experience in configuring file permissions and shares within an Active Directory domain environment. By creating folders, setting permissions, and managing security groups, we have demonstrated the importance of access control in maintaining a secure and efficient network infrastructure. Through practical exercises and step-by-step configurations, we have gained valuable insights into managing file access and ensuring appropriate permissions for users and groups. Overall, this project highlights the critical role of file permissions and shares in maintaining data integrity and security within an organization's network environment.
