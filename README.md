# osTicket
How to install and setup a help desk ticketing system



How to Install osTicket
This is an easy guide to installing a help desk ticketing system called osTicket.
Files You Need to Download
Download Now 📁
Software & Technologies Used
Windows 10 (Build 19044)

Microsoft Azure (Virtual Machines)

Remote Desktop (RDP)

Internet Information Services (IIS)

Prerequisites
Create a Virtual Machine in Azure

Install osTicket v1.15.8

Install HeidiSQL

Install MySQL

Install PHP

install Microsoft Visual C++ Redistributable

Steps
Create Virtual Machine in Azure

First, start by creating a Resource Group inside Azure.



Now, create a Windows 10 Virtual Machine (VM), typically with 2-4 Virtual CPUs. For username and password, it can be anything as we'll be using this info to remote in with our main computer. When creating the Virtual Machine (VM), allow Azure to create a new Virtual Network (Vnet):





Open your Remote Desktop Connection app on your computer and connect to your Virtual Machine that was created in Azure.





Now we need to install / Enable IIS in Windows. Go to your Search Bar > Type "Control Panel" > Click "Programs" > "Turn Windows features on or off" > Scroll down to "Internet Information Services (IIS).





Once clicked, find the "Internet Information Services" expand it and then expand the "World Wide Web" tab. Afterward, expand the application Developer tab. Finally check the "CGI" button & press Ok. You will need CGI to download the PHP Manager. The PHP manager is a back-end web programming language that allows osTicket to run off a web browser.




Install PHP Manager

Download the PHP manager file, and agree with all the terms. We've now downloaded the PHP manager into our operating system.



Install Rewrite Module

Download the Rewrite Module file, agree with all the terms and it should now be installed onto the Computer.



CREATE DIRECTORY C:\PHP

Open File Explorer, type, "C:\" in the search bar, Right-click and create a new folder called, "PHP". Download php-7.3.8-nts-Win32-VC15-x86.zip from Files You Need to Download, Extract it by going to where you download the file, Right-click the PHP 7.3.8 file and press extract to the PHP Folder you just created.



VC_REDIST DOWNLOAD

Download and install VC_Redist, Agree with any terms and agreements and finish installing.



DOWNLOAD MySQL
Download and install MySQL, Agree with any terms and agreements up until you get to the password portion. Here you can create a username and password for the database that you'll be using to store the Ticket Information used in osTicket.




Install osTicket v1.15.8

Download osTicket (download from within lab files: link).

Extract and copy the “upload” folder INTO c:\inetpub\wwwroot:





Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”:





Reload IIS (Open IIS, Stop and Start the server)

Go to sites -> Default -> osTicket:



On the right, click “Browse *:80”:





Enable Extensions in IIS: Note that some extensions are not enabled

Go back to IIS, sites -> Default -> osTicket.

Double-click PHP Manager:



Click “Enable or disable an extension”.

Enable: php_imap.dll.

Enable: php_intl.dll.

Enable: php_opcache.dll:





Refresh the osTicket site in your browser, observe the changes





Rename

From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php.

To: C:\inetpub\wwwroot\osTicket\include\ost-config.php:





Assign Permissions: ost-config.php

Disable inheritance -> Remove All:



New Permissions -> Everyone -> All:







Continue Setting up osTicket in the browser (click Continue)

Name Helpdesk.

Default email (receives email from customers):

 



Download and Install HeidiSQL



Create a new session, root/Password1.

Connect to the session:



Create a database called “osTicket”:





Continue Setting up osTicket in the browser

MySQL Database: osTicket

MySQL Username: root

MySQL Password: Password1:



Click “Install Now!”

Congratulations, hopefully it is installed with no errors!





Clean up

Delete: C:\inetpub\wwwroot\osTicket\setup:



Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php:





Login to the osTicket Admin Panel (http://localhost/osTicket/scp/login.php)





Congrats, You've Finished Installing osTicket.
