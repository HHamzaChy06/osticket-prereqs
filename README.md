<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- An Azure account with an active subscription.
- Azure Virtual Machine with Windows 10, vCPUs with 2+ cores
- A Remote Desktop Client
  

<h2>Installation Steps</h2>

### Step 1: Create and Configure the Azure Virtual Machine and Download and Install the necessary files 
[Download Files](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)

1. Create a Resource Group in Azure portal.

2. Deploy a Windows 10 Pro (22H2) VM, 2+ vCPUs, and a strong admin username/password.

3. Wait for deployment to complete.

4. Grab the VM’s public IP from the Azure Overview panel and log in via Remote Desktop Connection, using the VM credentials


1. Enable IIS and CGI

    -   Open Control Panel → Programs → Turn Windows features on or off.
  
    -   Check Internet Information Services (IIS).
  
    -   Expand IIS → World Wide Web Services → Application Development Features.
  
    -   Enable CGI (needed for PHP to work with IIS).

    -   Click OK to install.

2. Install PHP Manager for IIS

    -  Download and install PHP Manager for IIS to easily configure PHP with IIS.

3. Install URL Rewrite Module

    -  Download and install the URL Rewrite Module for proper URL routing in osTicket.

4. Extract PHP

    -  Download PHP 7.3.8.

    -  Extract the files into the C:\PHP directory (create the folder if it doesn’t exist).

5. Verify PHP with IIS

    -  Open IIS Manager and ensure PHP is recognized and linked to the C:\PHP directory.
  
