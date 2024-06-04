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

① While logged in to the **DC-01** VM as an admin (this example uses: **mydomain.com/jane_admin**), create the following folders on the C:\ drive:

    READ-ACCESS
    WRITE-ACCESS
    NO-ACCESS
    ACCOUNTING

<img width="350" alt="1  C DRIVE FOLDERS" src="https://github.com/TerikaJ/FilePermissions-Azure/assets/136477450/38b0fa0b-1032-4d15-9f8e-427c806e7e3c">

② To share a folder and assign permissions, open the folder's Properties and click on **Share** under the Sharing tab.

<img width="350" alt="1a  Sharing" src="https://github.com/TerikaJ/FilePermissions-Azure/assets/136477450/ce51936d-d1b1-46dc-8d33-cdc280eb5086">

③ Specify **domain users** and **domain admins** on the network to share folders with and assign appropriate permissions.

<img width="350" alt="1b  " src="https://github.com/TerikaJ/FilePermissions-Azure/assets/136477450/43c2579c-318a-4771-9e31-3af109838888">


④ Set the following permissions for the folders:
**Domain Users:**  

    - Grant "Read" permissions to the "READ-ACCESS" folder 
    - Grant "Read/Write" permissions on the "WRITE-ACCESS" folder

<img width="550" alt="2  Domain Users read" src="https://github.com/TerikaJ/FilePermissions-Azure/assets/136477450/2d2fbb02-bd06-491c-a48a-0ba8da245950">

<img width="550" alt="3  Domain users read:write" src="https://github.com/TerikaJ/FilePermissions-Azure/assets/136477450/80ef8d98-55a6-465b-b409-eb22a4b79edc">


**Domain Admins:** 

    - Grant "Read/Write" access to the "NO-ACCESS" folder.


<img width="550" alt="4  Domain admins read:write" src="https://github.com/TerikaJ/FilePermissions-Azure/assets/136477450/1488b346-c2eb-4b06-86da-1bc22cd565a5">

⑤ Log into **Client-01** VM as a normal user from one of the accounts we created during the active directory lab. This example uses: **bon.horo**
Navigate to the shared folders through the following path in File Explorer: **\\dc-01**

<img width="375" alt="9  Bon Horo log in" src="https://github.com/TerikaJ/FilePermissions-Azure/assets/136477450/09ce742c-a3f8-4f89-82dd-1a7a3b5431a2">


⑥ Observe how some folders only allow you to **"view"** files, while others do not allow access at all. This is occurs because the **"Domain User"** permissions for the specific folder are linked to the respective **Security Group** and set permissions for **users** within that Security Group. 

<img width="550" alt="5  Client dc-01" src="https://github.com/TerikaJ/FilePermissions-Azure/assets/136477450/7a02ac33-de0c-49fb-ac95-a2f99e9050a7">




<img src="https://i.imgur.com/bUjobDC.png" height="80%" width="80%" alt="Permissions Steps"/>
<img src="https://i.imgur.com/lz1DMos.png" height="80%" width="80%" alt="Permissions Steps"/>



<img src="https://i.imgur.com/kWrpLFE.png" height="80%" width="80%" alt="Permissions Steps"/>


<img src="https://i.imgur.com/NgM0CcI.png" height="80%" width="80%" alt="Permissions Steps"/>
<img src="https://i.imgur.com/I4k9T2J.png" height="80%" width="80%" alt="Permissions Steps"/>

<h2>Management Steps</h2>

① On **DC-01**, open the Active Directory **"Users and Computers panel"** under **Tools**.

② Create a New **Organizational Unit** called **"SECURITY GROUPS"**. Then create a New Group within the **Organizational Unit** called **ACCOUNTANTS**.

<img width="550" alt="6  AD ACCOUNTANTS" src="https://github.com/TerikaJ/FilePermissions-Azure/assets/136477450/3279d002-c0b1-48da-a005-458dd9835168">

③ After creating the New Group, go to the accounting folder and assign permissions to the folder so the **ACCOUNTANTS** Group has "Read/Write" permissions.

<img width="550" alt="7  ACCOUNTING FOLDER" src="https://github.com/TerikaJ/FilePermissions-Azure/assets/136477450/89be3087-2a76-4fe8-9aa6-3e65c4968c2d">

④ Return to the **Client-01** VM. You can observe the user cannot access the "ACCOUNTING" folder because they are not part of the **ACCOUNTANTS** Security Group.

⑤ Log off **Client-01** to apply new permissions 

⑥ On the domain controller, open the ACCOUNTANTS Properties on Active Directory Users and Computers.

⑦ In the Members tab, add the respective user. This example uses: **bon.horo**

⑧ After logging back into **Client-01**, **bon.horo** is now able to open the accounting folder because they are part of the **ACCOUNTANTS** security group



<img src="https://i.imgur.com/xev1Svv.png" height="80%" width="80%" alt="Permissions Steps"/>
<img src="https://i.imgur.com/SHotVB2.png" height="80%" width="80%" alt="Permissions Steps"/>




<h2>Conclusion</h2>

This project has provided hands-on experience in configuring file permissions and shares within an Active Directory domain environment. By creating folders, setting permissions, and managing security groups, we have demonstrated the importance of access control in maintaining a secure and efficient network infrastructure. Through practical exercises and step-by-step configurations, we have gained valuable insights into managing file access and ensuring appropriate permissions for users and groups. Overall, this project highlights the critical role of file permissions and shares in maintaining data integrity and security within an organization's network environment.
