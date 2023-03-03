<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This post outlines the steps I took to create and run an open source ticketing system. This section will demonstrate the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

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
I created a virtual machine in Azure running windows 10 with 2-4 Virtual CPUs. I named it VM-osTicket. I created some credentials to allow me to use the virtual machine through Microsoft Remote Desktop. When creating the virtual machine, I allowed it to create a new Virtual Network (Vnet). 
</p>
<br />

<p>
<img src="https://i.imgur.com/X1JDDyu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once that was created, I logged into the VM in remote desktop using the VM's public IP address and the credentials used when creating the VM in Azure. 
</p>
<br />

<p>
<img src="https://i.imgur.com/2qwhB0C.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
IIS (internet information services) is a web server that will allow your computer to serve up websites. Since OsTicket runs out of a website I needed to set up and configure IIS with CGI to run osTicket. CGI needs to be installed with IIS because CGI allows you to install PHPManager, which is a back-end web programming language that osTicket runs off of.
</p>
<br />

<p>
<img src="https://i.imgur.com/5pWrqcY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
download and install PHPManager
</p>
<br />
<p>
<img src="https://i.imgur.com/YhobHlJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
download and install rewrite
</p>
<br />
<p>
<img src="https://i.imgur.com/XdYsaWl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create the directory C:\PHP
</p>
<br />
<p>
<img src="https://i.imgur.com/6MBfS3u.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
download and install PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip)
</p>
<br />
<p>
<img src="https://i.imgur.com/MMJD8Tm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 unzip the contents into C:\PHP
</p>
<br />
<p>
<img src="https://i.imgur.com/Y69JWBX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
download and install VC_redist
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/POE0XJN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
download and install MySQL
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/BYiWO74.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open IIS as an Admin.
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/E03KBEN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Register PHP from within IIS. Reload IIS (Open IIS, Stop and Start the server)
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
Extract and copy “upload” folder to c:\inetpub\wwwroot. Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/ldWADHk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to sites -> Default -> osTicket
On the right, click “Browse *:80”
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/pwriF0s.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once I saw this screen, I knew osTicket was working. Now I need to enable some things in IIS to make some of those red "X"s work.
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/kw5kUgP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
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
disable inheritance
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/ljkXtee.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
edit permisions
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
