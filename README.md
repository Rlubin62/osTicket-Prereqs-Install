# osTicket-Prereqs-Install

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

-Microsoft Azure account
-Basic knowledge of IIS
-Remote Desktop access
-osTicket installation files
-HeidiSQL

Installation Steps

1.) CREATE A VIRTUAL MACHINE

In Microsoft Azure, we will create a VM and add it to a new Resource Group, titled "osTicket".

VM Name: osticket-vm

Image: Windows 10 Pro, version 22H2 - x64 Gen2

Size: 2 vCPUs, 8 GiB memory


Check the licensing box and review & create the VM. No changes are needed for management, disks, or networking sections.

![image](https://github.com/user-attachments/assets/b048f5a7-52df-4d23-af27-575bb3880ea5)

![image](https://github.com/user-attachments/assets/2e7f942c-1169-48df-8e85-8b0f0f6609e9)


2.) ACCESSING THE VIRTUAL MACHINE

-Log into the VM using Remote Desktop with the credentials created during the VM setup.
<img width="617" alt="image" src="https://github.com/user-attachments/assets/6d2c956b-4444-4dbc-ade1-815bd452835c" />


3.) DOWNLOAD AND PREPARE INSTALLATION FILES 

-Within the VM, download the osTicket-Installation-Files.zip and unzip it to your desktop. The folder should be named osTicket-Installation-Files.

![image](https://github.com/user-attachments/assets/c78dac96-3a79-4035-b0e8-57b456a9e05b)

<img width="619" alt="image" src="https://github.com/user-attachments/assets/7ba75b1f-8e61-44d9-9352-447b5b660de9" />

4.) INSTALL IIS ENABLE REQUIRED FEATURES 

Open Control Panel -> Programs -> Turn Windows features on or off.

Install/enable IIS with the following features:

World Wide Web Services -> Application Development Features -> [X] CGI

<img width="461" alt="image" src="https://github.com/user-attachments/assets/1bbdd7aa-c7d0-4357-b94e-bdb777d65a77" />

<img width="407" alt="image" src="https://github.com/user-attachments/assets/09993189-137c-4c2f-b869-1fafa428f6fc" />

<img width="409" alt="image" src="https://github.com/user-attachments/assets/8e781b83-3c79-4bc8-8ab0-d1dd7abfc1ab" />

<img width="411" alt="image" src="https://github.com/user-attachments/assets/0b69a212-6e37-414f-a14c-9439c84f1adc" />


5.) INSTALL REQUIRED COMPONENTS

From the osTicket-Installation-Files folder:

Install PHP Manager for IIS: PHPManagerForIIS_V1.5.0.msi.

Install Rewrite Module: rewrite_amd64_en-US.msi.

<img width="580" alt="image" src="https://github.com/user-attachments/assets/bc25ebde-2d9c-4f65-893d-879f01db1657" />


6.) Setup PHP

Create the directory C:\PHP.

Unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the C:\PHP folder.

Install VC_redist.x86.exe.




7.) Install MySQL
From the osTicket-Installation-Files folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi).
Select Typical Setup.
Launch the Configuration Wizard:
Standard Configuration
Input a username and password, don't forget this!
Step 1 Lab 3

8.) Configure IIS
Open IIS as an administrator.
Register PHP:
Go to PHP Manager -> Register PHP path -> C:\PHP\php-cgi.exe.
Reload IIS (Stop and Start the server).
Step 1 Lab 3

Step 1 Lab 3

9.) Install osTicket
From the osTicket-Installation-Files folder:
Unzip osTicket-v1.15.8.zip.
Copy the upload folder into C:\inetpub\wwwroot.
Rename the upload folder to osTicket.
Reload IIS (Stop and Start the server).
Step 1 Lab 3

Step 1 Lab 3

10.) Configure osTicket
Open IIS:
Navigate to Sites -> Default -> osTicket.
On the right, click *Browse :80.
Step 1 Lab 3

Step 1 Lab 3

Note extensions that are not enabled. Go back to IIS:
Navigate to Sites -> Default -> osTicket.
Double-click PHP Manager -> Click Enable or disable an extension.
Enable the following extensions:
php_imap.dll
php_intl.dll
php_opcache.dll
Step 1 Lab 3

11.) Update Configuration Files
Rename ost-config.php:
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php.
Assign Permissions:
Disable inheritance -> Remove all permissions.
Add new permissions -> Everyone -> Full control.
Step 1 Lab 3

Step 1 Lab 3

12.) Complete osTicket Setup
In the browser, continue the osTicket setup:
Set Helpdesk Name.
Set Default email (receives emails from customers).
Step 1 Lab 3

13.) Install HeidiSQL and Configure Database
From the osTicket-Installation-Files folder, install HeidiSQL.
Open HeidiSQL:
Create a new session: Username: root / Password: root.
Connect to the session.
Create a database named osTicket.
Step 1 Lab 3

Step 1 Lab 3

14.) Finalize osTicket Installation
In the browser, complete the setup:
MySQL Database: osTicket
MySQL Username: root
MySQL Password: root
Click Install Now!
Step 1 Lab 3

15.) Verify Installation
Access your help desk login page: http://localhost/osTicket/scp/login.php.
Step 1 Lab 3

Conclusion
Congratulations! You have successfully installed and configured osTicket on your virtual machine. Your help desk system is now ready to use!
