**Partie 2**

🌞 Créer un service efrei_server.service

```
[Unit]
Description=Super serveur EFREI

[Service]
Type=daemon
ExecStart=/usr/local/bin/efrei_server
Environment=LISTEN_ADDRESS=10.0.2.15
```
🌞 Exécuter la commande systemctl status efrei_server
```
[lawerz@localhost bin]$ sudo systemctl status efrei_server
● efrei_server.service - Super serveur EFREI
     Loaded: loaded (/etc/systemd/system/efrei_server.service; static)
     Active: active (running) since Tue 2024-09-10 14:07:09 CEST; 3s ago
   Main PID: 12179 (efrei_server)
      Tasks: 2 (limit: 11100)
     Memory: 32.5M
        CPU: 163ms
     CGroup: /system.slice/efrei_server.service
             ├─12179 /usr/local/bin/efrei_server
             └─12180 /usr/local/bin/efrei_server

Sep 10 14:07:09 efrei-localhost.campus.villejuif systemd[1]: Started Super serveur EFREI.
```
```
[lawerz@localhost bin]$ sudo systemctl daemon-reload
[lawerz@localhost bin]$ sudo systemctl start efrei_server
[lawerz@localhost bin]$ sudo systemctl status efrei_server
```
```
[lawerz@localhost bin]$ ss -tuln | grep 8888
tcp   LISTEN 0      100    10.0.2.15:8888      0.0.0.0:
```
```
PS /Users/MBP-2015> ncat 10.O.2.15 8888
Hello ! Tu veux des infos sur quoi ?
1) cpu
2) ram
3) disk
4) ls un dossier

Ton choix (1, 2, 3 ou 4) :
```








