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

Keep MySQL Server & Cluster selected and press Enter to save changes.
Select your desired MySQL server version. For example, mysql-8.0 and press Enter to apply the version repository information.
Press Down on your keyboard, select OK and press Enter to apply the MySQL repository information on your server.
