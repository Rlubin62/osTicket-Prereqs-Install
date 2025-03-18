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

<img width="680" alt="image" src="https://github.com/user-attachments/assets/3b0aea6f-3d9c-48e7-9bc0-5d7e3ade39e2" />

<img width="549" alt="image" src="https://github.com/user-attachments/assets/c1cad519-ceed-459e-8a98-2e663be6d39d" />


7.) INSTALL MYSQL

-From the osTicket-Installation-Files folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi).

-Select Typical Setup.

-Launch the Configuration Wizard:
Standard Configuration

-Enter a username and password

![Screenshot 2025-03-18 085705](https://github.com/user-attachments/assets/8ea6ac20-0f87-4ab0-8c05-a20d5fddfe38)



8.) IIS CONFIGURE IIS

Open IIS as an administrator.

Register PHP:

Go to PHP Manager -> Register PHP path -> C:\PHP\php-cgi.exe.

Reload IIS (Stop and Start the server).

![image](https://github.com/user-attachments/assets/c5f11930-9860-4370-b351-a6ea71541394)


9.) INSTALL OsTICKET

-From the osTicket-Installation-Files folder:
Unzip osTicket-v1.15.8.zip.

-Copy the upload folder into C:\inetpub\wwwroot.

-Rename the upload folder to osTicket.

-Reload IIS (Stop and Start the server).

![image](https://github.com/user-attachments/assets/7c7a3147-4843-4e4b-baea-586d12c8cc48)

![image](https://github.com/user-attachments/assets/6be48f9b-debb-4f17-9ae6-79958e4aa2ff)


10.) Configure osTicket

-Open IIS:

-Navigate to Sites -> Default -> osTicket.

-On the right, click *Browse :80.

![image](https://github.com/user-attachments/assets/5de2509b-c4af-4132-83a7-ee4916e84206)

<img width="519" alt="image" src="https://github.com/user-attachments/assets/e2e3cbf3-b007-40ee-9a90-b5bed0c4871b" />

Note extensions that are not enabled. Go back to IIS:

-Navigate to Sites -> Default -> osTicket.

-Double-click PHP Manager -> Click Enable or disable an extension.

-Enable the following extensions:

php_imap.dll

php_intl.dll

php_opcache.dll

<img width="651" alt="image" src="https://github.com/user-attachments/assets/91c6faea-eccf-402c-a1c4-ec1e0509eaf2" />


11.) Update Configuration Files

Rename ost-config.php:

From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php

To: C:\inetpub\wwwroot\osTicket\include\ost-config.php.

Assign Permissions:

Disable inheritance -> Remove all permissions.

Add new permissions -> Everyone -> Full control.

<img width="641" alt="image" src="https://github.com/user-attachments/assets/aa8836eb-f9be-4a60-b5f8-8375339c8f75" />

<img width="545" alt="image" src="https://github.com/user-attachments/assets/733c487a-9ca9-42ae-9582-12870011b500" />


12.) COMPLETE OsTICKET SETUP

In the browser, continue the osTicket setup:

-Set Helpdesk Name.

-Set Default email (receives emails from customers).

<img width="552" alt="image" src="https://github.com/user-attachments/assets/67126cae-6538-4ebe-bf80-005202f56d59" />



13.) Install HeidiSQL and Configure Database

From the osTicket-Installation-Files folder, install HeidiSQL.

Open HeidiSQL:

-Create a new session: Username: root / Password: root.

-Connect to the session.

-Create a database named osTicket.

<img width="721" alt="image" src="https://github.com/user-attachments/assets/17539cdf-e4dc-4c0e-a0ee-9a34330e9f19" />

![image](https://github.com/user-attachments/assets/70a51ca5-51f0-410b-86d0-4d3d74172956)


14.) Finalize osTicket Installation

In the browser, complete the setup:

-MySQL Database: osTicket

-MySQL Username: root

-MySQL Password: root

Click Install Now!

<img width="378" alt="image" src="https://github.com/user-attachments/assets/4d4921ec-4f22-4c6b-8c85-46a3f1716ea9" />


15.) Verify Installation

Access your help desk login page: http://localhost/osTicket/scp/login.php.

![image](https://github.com/user-attachments/assets/d3212c12-1baf-47dd-9867-bb25a4af3b58)


Conclusion
Installation and configuration of osTicket on the virtual machine is successful. Your help desk system is now ready.
