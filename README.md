<img width="700" height="200" alt="image" src="https://github.com/user-attachments/assets/f070aab3-bb56-442b-b29e-497bf8637e9e" />

# osTicket – Prerequisites and Installation on Azure VM

This guide covers installing all required components and configuring **osTicket** on a Windows Azure Virtual Machine.<br>
Guide to setup the Azure Virtual Machine: [Azure Setup](https://github.com/HHamzaChy06/azure-setup) <br>
You can find all the necessary installation files for this project here: [Download Files](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)
---

## Step 1: Connect to the VM
1. Get the **Public IP** of your VM from the Azure Portal.
2. Use **Remote Desktop Connection (RDP)** to log in with your VM credentials.

<img width="412" height="258" alt="image" src="https://github.com/user-attachments/assets/f48d3be2-60d9-48a1-8341-264a3de226f3" />

---

## Step 2: Install IIS and Required Features
1. On the VM, Open Control Panel -> Programs -> Turn Windows features on or off.

2. Enable:
   - **Internet Information Services (IIS)**
   - **CGI** under Application Development
   - All **Common HTTP Features**
   - **IIS Management Console**

<img width="588" height="558" alt="image" src="https://github.com/user-attachments/assets/7bc545ae-06b5-4162-9c0b-c607c88b7224" />
<img width="592" height="546" alt="image" src="https://github.com/user-attachments/assets/e61344df-1f10-4ba6-95f7-d450df5c0cee" />

---

## Step 3: Install PHP and PHP Manager
1. Install:
   - **PHP Manager for IIS**
   - **IIS URL Rewrite Module**
   - **Microsoft Visual C++ Redistributable (x86)**
2. Create a folder with the name of `PHP` in the C drive and extract **PHP 7.3.8** inside `C:\PHP`.

<img width="380" alt="Screenshot 2025-01-22 at 7 42 50 PM" src="https://github.com/user-attachments/assets/50bd067d-1759-4d5c-b181-9ec0e61b0707" />
<img width="347" alt="Screenshot 2025-01-22 at 7 44 02 PM" src="https://github.com/user-attachments/assets/787882bb-ce07-406e-b96b-fc0e120cbb54" />
<img width="349" alt="Screenshot 2025-01-22 at 7 44 35 PM" src="https://github.com/user-attachments/assets/9416dd52-867f-4f50-9b1b-cf0cfb7a5561" />
<img width="467" alt="Screenshot 2025-01-22 at 7 58 00 PM" src="https://github.com/user-attachments/assets/ee996992-16f9-4918-bd4e-37cd4ebd32a3" />
<img width="437" alt="Screenshot 2025-01-22 at 7 59 01 PM" src="https://github.com/user-attachments/assets/9d4bd23c-2136-4492-a91a-2546ea40a2c3" />
<img width="332" alt="Screenshot 2025-01-22 at 8 00 16 PM" src="https://github.com/user-attachments/assets/18b0c4ea-ae28-4718-88e7-7223a6c5ca2b" />

---

### Step 4: Install MySQL
1. Install **MySQL 5.5.62** (`mysql-5.5.62-win32.msi`) with the following configuration:
   - Choose **Typical Setup**.
   - Launch the **Configuration Wizard** after installation.
   - Select **Standard Configuration**.
   - Set MySQL credentials:
     - Username: `root`
     - Password: `root`

<img width="344" alt="Screenshot 2025-01-22 at 8 01 27 PM" src="https://github.com/user-attachments/assets/8a1173f9-c0d3-4f02-80c6-9491937ac9ba" />
<img width="350" alt="Screenshot 2025-01-22 at 8 01 49 PM" src="https://github.com/user-attachments/assets/6d87cbe5-a84f-4bdb-af66-39aa97df30ba" />
<img width="346" alt="Screenshot 2025-01-22 at 8 02 18 PM" src="https://github.com/user-attachments/assets/3fcb3ea5-598d-4d2c-86b8-6e6441e35e53" />
<img width="345" alt="Screenshot 2025-01-22 at 8 31 39 PM" src="https://github.com/user-attachments/assets/4897dc06-4ddb-4ed9-a6bb-fa52c0476753" />

### Step 5: Configure IIS
1. Open IIS as an Administrator.
2. Register PHP:
   - Open **PHP Manager** in IIS.
   - Register `C:\PHP\php-cgi.exe`.
3. Reload IIS:
   - Open IIS.
   - Stop and Start the server.

<img width="361" alt="Screenshot 2025-01-22 at 8 32 16 PM" src="https://github.com/user-attachments/assets/3ccc1788-ef42-4eb4-8a75-4862708ad59a" />
<img width="597" alt="Screenshot 2025-01-22 at 8 35 06 PM" src="https://github.com/user-attachments/assets/066e5a27-205e-4c05-90d7-632eb086f4ef" />

### Step 6: Install osTicket
1. Extract `osTicket v1.15.8` (`osTicket-v1.15.8.zip`) from the `osTicket-Installation-Files` folder.
2. Copy the `upload` folder to `C:\inetpub\wwwroot`.
3. Rename the folder from `upload` to `osTicket`.
4. Reload IIS.
5. In IIS:
   - Navigate to **Sites** -> **Default** -> **osTicket**.
   - On the right-hand side, click **Browse *:80**.
6. Address missing extensions:
   - Navigate to **PHP Manager** in IIS.
   - Enable the following extensions:
     - `php_imap.dll`
     - `php_intl.dll`
     - `php_opcache.dll`
7. Refresh the osTicket site in your browser.

<img width="402" alt="Screenshot 2025-01-22 at 8 38 43 PM" src="https://github.com/user-attachments/assets/157b498a-7103-41c2-a11b-19fb3c5dee69" />
<img width="662" alt="Screenshot 2025-01-22 at 8 40 09 PM" src="https://github.com/user-attachments/assets/10d91596-f9c1-4f7b-a150-65ddce4b2dea" />
<img width="419" alt="Screenshot 2025-01-22 at 8 40 38 PM" src="https://github.com/user-attachments/assets/5d02eda5-8cc0-4ba0-9e31-c8ea6082ce4d" /> 
<img width="414" alt="Screenshot 2025-01-22 at 8 40 57 PM" src="https://github.com/user-attachments/assets/a6fcb525-6ba8-4420-bd06-c2375d9b24dc" />
<img width="631" alt="Screenshot 2025-01-22 at 8 43 19 PM" src="https://github.com/user-attachments/assets/5bcb8bde-955b-44ba-8361-947dfa4d94d8" />
<img width="596" alt="Screenshot 2025-01-22 at 8 43 30 PM" src="https://github.com/user-attachments/assets/80441b7a-70b7-46da-ba2c-cf194f176e34" />
<img width="557" alt="Screenshot 2025-01-22 at 8 54 35 PM" src="https://github.com/user-attachments/assets/8aa5a966-b5cf-4285-be21-480fec91f593" />
<img width="606" alt="Screenshot 2025-01-22 at 8 54 48 PM" src="https://github.com/user-attachments/assets/360e1162-bcfd-4843-8783-1ab8f67fbafb" />

### Step 7: Configure osTicket
1. Rename `ost-config.php`:
   - From: `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`
   - To: `C:\inetpub\wwwroot\osTicket\include\ost-config.php`
2. Assign permissions to `ost-config.php`:
   - Disable inheritance -> Remove all permissions.
   - Add new permissions: `Everyone -> Full Control`.
3. Continue setup in the browser:
   - Name your help desk.
   - Set a default email for receiving customer emails.
  
<img width="494" alt="Screenshot 2025-01-22 at 8 55 53 PM" src="https://github.com/user-attachments/assets/b2a66cbb-bada-4031-8445-9d2e38c84897" />
<img width="346" alt="Screenshot 2025-01-22 at 8 56 16 PM" src="https://github.com/user-attachments/assets/2a361498-b828-4fd1-93e3-88f0384427e0" />
<img width="577" alt="Screenshot 2025-01-22 at 8 57 11 PM" src="https://github.com/user-attachments/assets/5525f530-b204-4472-906d-ff326056ecdc" />
<img width="415" alt="Screenshot 2025-01-22 at 8 57 44 PM" src="https://github.com/user-attachments/assets/9421699b-142a-49da-9abf-43f523954ac3" />
<img width="415" alt="Screenshot 2025-01-22 at 8 58 46 PM" src="https://github.com/user-attachments/assets/d5e062b6-e77a-4cba-bb1c-0d8af4b17e23" />

### Step 8: Set Up the Database
1. Install **HeidiSQL** from the `osTicket-Installation-Files` folder.
2. Open HeidiSQL and create a new session:
   - Username: `root`
   - Password: `root`
3. Create a database named `osTicket`.
4. Complete the setup in the browser:
   - MySQL Database: `osTicket`
   - MySQL Username: `root`
   - MySQL Password: `root`
   - Click **Install Now!**

<img width="413" alt="Screenshot 2025-01-22 at 9 00 07 PM" src="https://github.com/user-attachments/assets/2bcbebe8-8fb2-467e-b880-d055a461df7e" />
<img width="473" alt="Screenshot 2025-01-22 at 9 05 34 PM" src="https://github.com/user-attachments/assets/c33af950-e50a-4b8b-adb4-4fff4c6f2a90" />
<img width="625" alt="Screenshot 2025-01-22 at 9 05 49 PM" src="https://github.com/user-attachments/assets/c8fcfd0a-9528-4eba-b768-b4e23027912f" />
<img width="500" alt="Screenshot 2025-01-22 at 9 06 11 PM" src="https://github.com/user-attachments/assets/728f3790-c646-49d4-93d1-f71b82e372ea" />
<img width="536" alt="Screenshot 2025-01-22 at 9 06 30 PM" src="https://github.com/user-attachments/assets/89ab1176-e1c9-4724-ae6a-1461dbfdb155" />
<img width="612" alt="Screenshot 2025-01-22 at 9 06 47 PM" src="https://github.com/user-attachments/assets/386abce2-b4d4-4484-bdfb-8a4f1aff1f85" />

### Step 9: Post-Installation Cleanup
1. Delete the `C:\inetpub\wwwroot\osTicket\setup` folder.
2. Set `C:\inetpub\wwwroot\osTicket\include\ost-config.php` to **Read-only** permissions.

### Step 10: Access osTicket
- Admin Panel: [http://localhost/osTicket/scp/login.php](http://localhost/osTicket/scp/login.php)
- End-User Portal: [http://localhost/osTicket/](http://localhost/osTicket/)

## Conclusion
You should bow have a fully functional osTicket. Enjoy managing your help desk with osTicket!
