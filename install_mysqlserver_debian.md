1. Download repository Package
```console
$  wget https://dev.mysql.com/get/mysql-apt-config_0.8.30-1_all.deb
```

2. Install repository information
```console
$  sudo dpkg -i mysql-apt-config_0.8.30-1_all.deb
```
after the install the configuration Managerstarts

```
┌────────────────┤ Configuring mysql-apt-config ├─────────────────┐
│ Which MySQL product do you wish to configure?                   │
│                                                                 │
│     MySQL Server & Cluster (Currently selected: mysql-8.0)      │
│     MySQL Tools & Connectors (Currently selected: Enabled)      │
│     MySQL Preview Packages (Currently selected: Disabled)       │
│     Ok                                                          │
│                                                                 │
│                                                                 │
│                             <Ok>                                │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

- Keep MySQL Server & Cluster selected and press Enter to save changes.
- Select your desired MySQL server version. For example, mysql-8.0 and press Enter to apply the version repository information.
- Press Down on your keyboard, select OK and press Enter to apply the MySQL repository information on your server.

3. Update the server's package index to apply the new MySQL repository information.

```console
$   sudo apt update
```
4. Install the MySQL database server package.
```console
$   sudo apt install mysql-server -y
```

```console
Enter root password:
```
- Enter a new root database user password when prompted and press Enter.


```console
Re-enter root password:
```
- Enter the password again and press Enter to apply changes.

```console
Use Strong Password Encryption (RECOMMENDED)
Use Legacy Authentication Method (Retain MySQL 5.x Compatibility)
```
- Keep Use Strong Password Encryption (RECOMMENDED) selected and press Enter to enable password authentication for all database users on the server.


5. View the installed MySQL version on your server.
```console
$   mysql --version
```

Output
```console
mysql  Ver 8.0.38 for Linux on x86_64 (MySQL Community Server - GPL)
```


## Manage the MySQL System Service
MySQL uses the mysqld system service to manage the database server runtime processes through the systemd daemon. Follow the steps below to manage the MySQL system service and enable the database server to automatically start at boot time.

1. Enable the MySQL database server to automatically start at boot time.
```console
$   sudo systemctl enable mysql
```

2. Start the MySQL database server.
```console
$   sudo systemctl start mysql
```

3. View the MySQL system service status and verify that it's running.
```console
$   sudo systemctl status mysql
```

## Secure the MySQL Database Server
The MySQL root database user is actively secure on your server with the password you set earlier during the installation process. MySQL includes additional insecure defaults such as test databases and remote access to the root database user on your server. Follow the steps below to disable all insecure default configurations and secure the MySQL database server.

1. Run the MySQL secure installation.
```console
$   sudo mysql_secure_installation
```

Reply to the following MySQL prompts to secure your database server.
- Enter the root database user to start the secure installation script and modify the database server configuration.
```console
Securing the MySQL server deployment.

Enter password for user root:
```

- Enter Y and press Enter to enable the VALIDATE PASSWORD COMPONENT and ensure strict password security policies.

```console
Would you like to setup VALIDATE PASSWORD component?

Press y|Y for Yes, any other key for No:
```

- Set your desired MySQL database server password strength policy. For example, enter 2 and press Enter to enable the use of strong passwords on your server.

```console
LOW    Length >= 8
MEDIUM Length >= 8, numeric, mixed case, and special characters
STRONG Length >= 8, numeric, mixed case, special characters and dictionary file

Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG: 2
```

- Enter N when prompted to change the root database user password, or enter Y to change the password.

```console
Change the password for root ? ((Press y|Y for Yes, any other key for No) :
```

- Enter Y and press Enter when prompted to remove anonymous users on the database server.
```console
Remove anonymous users? (Press y|Y for Yes, any other key for No) :
```

- Enter Y and press Enter to disable remote access to the root database user.
```console
Disallow root login remotely? (Press y|Y for Yes, any other key for No) :
```

- Enter Y and press Enter to remove the test database on your server.
```console
Remove test database and access to it? (Press y|Y for Yes, any other key for No) :
```

- Enter Y and press Enter to update the MySQL privileges table and apply your configuration changes.

```console
Reload privilege tables now? (Press y|Y for Yes, any other key for No) :
```

Output:

```console
Success.

All done!
```
