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


<h2>Installation Steps</h2>

![Screenshot 2024-11-13 141242](https://github.com/user-attachments/assets/9eee9eec-440a-42ad-a3c7-f0e932f4e9a6)


<p>

![Screenshot 2024-11-13 141520](https://github.com/user-attachments/assets/1ee15508-a19f-4452-9b32-51be6ecd36a0)

</p>
<p>
Within the VM (osticket-vm), download the osTicket-Installation-Files.zip and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”
We will use the files in this folder to install osTicket and some of the dependencies.

</p>
<br />

<p>

![Screenshot 2024-11-13 142224](https://github.com/user-attachments/assets/f6f31051-3863-4339-8540-38d99aa82f7a)

</p>
<p>
Install / Enable IIS in Windows WITH CGI
World Wide Web Services -> Application Development Features -> [X] CGI

</p>
<br />

<p>

![Screenshot 2024-11-13 142720](https://github.com/user-attachments/assets/9955dc27-091c-4333-9be1-5d8a40e4a2f2)

</p>
<p>
From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
</p>
<br />

<p>

![Screenshot 2024-11-13 143122](https://github.com/user-attachments/assets/a1c02aba-e973-4e20-8293-4247ef154aee)

</p>
<p>
From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi)
</p>

Create the directory C:\PHP

<br />

<p>

![Screenshot 2024-11-13 143609](https://github.com/user-attachments/assets/a0609daa-2f2e-40e0-a43c-26ad9729bea2)

</p>
<p>
From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
</p>
<br />

<p>

![Screenshot 2024-11-13 143848](https://github.com/user-attachments/assets/fbd81b05-d091-4883-bfbd-a68d38aedb57)

</p>
<p>From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
</p>
<br />

<p>

![Screenshot 2024-11-13 144050](https://github.com/user-attachments/assets/b617ffa4-a43f-47de-8974-a9d2d9e3a2c9)

</p>
<p>From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
</p>
<br />

<p>

![Screenshot 2024-11-13 144328](https://github.com/user-attachments/assets/dd07a01a-dd96-450a-a7d0-3f69725b7667)

</p>
<p>
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->

Username: root

Password: root

</p>
<br />
OPEN IIS AS AN ADMIN

<p>

![Screenshot 2024-11-13 144807](https://github.com/user-attachments/assets/7f065526-301a-49e7-acaf-e69f89534f08)

</p>
<p>
Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)

</p>
<br />
RELOAD IIS FOR CHANGES TO TAKE PLACE


<p>

![Screenshot 2024-11-13 145334](https://github.com/user-attachments/assets/d86aa602-2ff0-4df1-8dc9-ee4087916089)

</p>
<p>
Install osTicket v1.15.8
From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”
</p>
<br />

RELOAD IIS AGAIN FOR THE CHANGES TO TAKE PLACE

NOTICE SOME EXTENSIONS ON OSTICKET WEBPAGE WILL NOT BE ALLOWED

<p>

![Screenshot 2024-11-13 150559](https://github.com/user-attachments/assets/6c01698d-7b5d-4824-9d36-644d34a7ed15)

</p>
<p>
Go back to IIS, sites -> Default -> osTicket

Double-click PHP Manager

Click “Enable or disable an extension”

Enable: php_imap.dll

Enable: php_intl.dll

Enable: php_opcache.dll

Refresh the osTicket site in your browser, observe the changes

</p>
<br />

<p>

![Screenshot 2024-11-13 151000](https://github.com/user-attachments/assets/a08bfb93-bcf6-49c1-a0aa-c8c6fcad5e72)

</p>
<p>
Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

</p>
<br />

<p>

![Screenshot 2024-11-13 151215](https://github.com/user-attachments/assets/c9158b89-afc4-4503-aac4-18d36c150ebf)

</p>
<p>
Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

</p>
<br />

<p>

![Screenshot 2024-11-13 151456](https://github.com/user-attachments/assets/834bc477-f242-43f3-974e-1a96131fb607)

</p>
<p>
Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)

</p>
<br />

<p>
  
![Screenshot 2024-11-13 151656](https://github.com/user-attachments/assets/0c4370a6-02d8-42f0-a31f-93ea2588896c)

![Screenshot 2024-11-13 151816](https://github.com/user-attachments/assets/8df1efad-1110-4b13-a893-76fa174fd835)

![Screenshot 2024-11-13 151903](https://github.com/user-attachments/assets/548af911-1c33-4138-8675-9a33c757a5f9)

</p>
<p>
From the “osTicket-Installation-Files” folder, install HeidiSQL.

Open Heidi SQL

Create a new session, root/root

Connect to the session

Create a database called “osTicket”

</p>
<br />
<p>

![Screenshot 2024-11-13 154759](https://github.com/user-attachments/assets/b42ea21e-3ba5-4acd-897a-41085607af34)

</p>
<p>
Continue Setting up osTicket in the browser

MySQL Database: osTicket

MySQL Username: root

MySQL Password: root

Click “Install Now!”






CONGRATULATIONS YOU ARE DONE INSTALLING OSTICKET

