<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This post outlines the steps to create and run an open source ticketing system. This section will demonstrate the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Installation Files


<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites (in Azure)</h2>

<p>
<img src="https://i.imgur.com/on9Y0Ku.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/ax6OTTI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a virtual machine in Azure running windows 10 with 2-4 Virtual CPUs. I named it VM-osTicket. I created some credentials to allow me to use the virtual machine through Microsoft Remote Desktop. When creating the virtual machine, allow it to create a new Virtual Network (Vnet). 
</p>
<br />

<p>
<img src="https://i.imgur.com/X1JDDyu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once that is created, log into the VM in remote desktop using the VM's public IP address and the credentials used when creating the VM in Azure. 
</p>
<br />

<p>
<img src="https://i.imgur.com/2qwhB0C.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
IIS (internet information services) is a web server that will allow your computer to serve up websites. Since OsTicket runs out of a website IIS needs to be set up and configured with CGI to run osTicket. CGI needs to be installed with IIS because CGI allows you to install PHPManager, which is a back-end web programming language that osTicket runs off of.
 
Right click Windows start menu > Run > type "control panel" > Programs > Turn Windows features on or off > Internet Information services > World Wide Web Services > Application Development Features > CGI
</p>
<br />

<p>
<img src="https://i.imgur.com/5pWrqcY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open the Installation Files under "Environments and Technologies Used" header of this post. Download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
</p>
<br />
<p>
<img src="https://i.imgur.com/YhobHlJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)
</p>
<br />
<p>
<img src="https://i.imgur.com/XdYsaWl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create the directory C:\PHP
 
 Open the local drive > This PC > Windows (C:) > Right click > New > Folder > Name it "PHP"
</p>
<br />
<p>
<img src="https://i.imgur.com/6MBfS3u.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip)
</p>
<br />
<p>
<img src="https://i.imgur.com/MMJD8Tm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 Unzip the contents of PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into C:\PHP
 
 Right click PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) > Extract All > Browse > This PC > Windows (C:) > PHP > Select Folder > Extract
</p>
<br />
<p>
<img src="https://i.imgur.com/Y69JWBX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Installation Files, download and install VC_redist.x86.exe
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/POE0XJN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
 
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Password1
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/BYiWO74.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open IIS as an Admin.
 
 Click on start > type "IIS" > right click > Run as administrator
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/E03KBEN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Register PHP from within IIS.
 
 Double click PHP Manager > Register new PHP version > click " ... " to browse > This PC > Windows (C:) > PHP > php.cgi > OK
 
 Reload IIS (Open IIS, Stop and Start the server)
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/gEPzU96.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>Download osTicket from the Installation Files Folder.
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/yCYBEVv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Extract and copy “upload” folder to c:\inetpub\wwwroot. 
 
Open downlods folder > osTicket-v1.15.8 > drag and drop "upload" folder into "wwwroot" folder. To find the wwwroot folder: This PC > Windows (C:) > inetpub > wwwroot
 
 Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”
 
 Reload IIS (Open IIS, Stop and Start the server)
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/ldWADHk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Within IIS, go to sites -> Default -> osTicket
On the right, click “Browse *:80 (http)”
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/pwriF0s.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
"Browse *80 (http)" will direct you to this webpage. This shows that osTicket is working. Now some things in IIS need to be enabled to make some of those red "X"s work.
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/xffqXpF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browser.
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/4qVkXq3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Notice how some extensions are now enabled.
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/xSKx4Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, 
 Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/IjGrz0c.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Assign Permissions

Right click ost-config,php > Properties > Security > Advanced > Disable inheritance > Remove all inherited permissions from this object > Add > Select a principle > type "everyone" > Check Names > OK > Full control > OK > Apply > OK > OK
</p>
<br />
</p>
<br />
<p>
<img src="blob:https://imgur.com/d26ac64d-6a69-4f5f-a406-0c53ad3f89fa" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/0MXE6Fy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Download and install Heidi SQL.
Create a new session by clicking the green "new" button on the bottom left, root/Password1
Connect to the session
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/kWnMgHD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Right click on "Unnamed" and create a database called “osTicket”
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/qwLcscM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Continue Setting up osticket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: Password1
Click “Install Now!”
</p>
<br />
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/qdtLhIA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Congratulations, hopefully it is installed with no errors!
</p>
<br />
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/DiBwyw7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Clena up: delete "setup" folder in C:\inetpub\wwwroot\osTicket\setup
</p>
<br />
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/XkztDLz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>
<br />
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/DiBwyw7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Clena up: delete "setup" folder in C:\inetpub\wwwroot\osTicket\setup
</p>
<br />
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/q4FRyuM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/5VBaLoN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/XUYFuYy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

 End Users osTicket URL: http://localhost/osTicket/ 
<br />
</p>
<br />
</p>
<br />
<p>
