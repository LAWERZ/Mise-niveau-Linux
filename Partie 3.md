**PARTIE 3**

🌞 Ajoutez une clause dans le fichier efrei_server.service pour le restart automatique

```
[Unit]
Description=Super serveur EFREI

[Service]
Type=daemon
ExecStart=/usr/local/bin/efrei_server
Environment=LISTEN_ADDRESS=10.0.2.15
Restart=always
```
```
[lawerz@localhost bin]$ sudo useradd -m -d /home/lawerz -s /bin/bash lawerz
[sudo] password for lawerz:
[lawerz@localhost bin]$ sudo passwd lawerz
Changing password for user lawerz.
New password:
Retype new password:
passwd: all authentication tokens updated successfully.
[lawerz@localhost bin]$ sudo nano /etc/systemd/system/efrei_server.service
```
```
[Unit]
Description=Super serveur EFREI

[Service]
ExecStart=/usr/local/bin/efrei_server
Environment=LOG_DIR=/var/log/efrei_server
Environment=LISTEN_ADDRESS=10.0.2.15
Restart=always
User=lawerz
Group=lawerz
```
```
sudo chown lawerz:lawerz /var/log/server_efrei
sudo chmod 700 /var/log/server_efrei
```
```
[Unit]
Description=Super serveur EFREI

[Service]
ExecStart=/usr/local/bin/efrei_server
Environment=LOG_DIR=/var/log/efrei_server
Environment=LISTEN_ADDRESS=10.0.2.15
Restart=always
User=lawerz
Group=lawerz


ProtectSystem=full
ProtectHome=yes
NoNewPrivileges=true
ReadOnlyPaths=/usr
PrivateTmp=true
RestrictAddressFamilies=AF_INET AF_INET6
ProtectKernelModules=true
RestrictSUIDSGID=true
ProtectKernelLogs=true
LockPersonality=true
PrivateDevices=true
ProtectControlGroups=true
MemoryDenyWriteExecute=true
ProtectProc=invisible
RestrictRealtime=true
SystemCallFilter=@system-service
```
