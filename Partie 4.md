**PARTIE 4**

🌞 Configurer de façon robuste le firewall
```
[lawerz@localhost ~]$ sudo firewall-cmd --permanent --policy myOutputPolicy --add-ingress-zone HOST
success
[lawerz@localhost ~]$ sudo firewall-cmd --permanent --policy myOutputPolicy --add-egress-zone ANY
success
[lawerz@localhost ~]$ sudo firewall-cmd --permanent --policy myOutputPolicy --set-target DROP
success
[lawerz@localhost ~]$ sudo firewall-cmd --reload
success
```
```
[lawerz@localhost ~]$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 3089ms
```
```
[lawerz@localhost ~]$ sudo firewall-cmd --list-all
public (active)
  target: DROP
  icmp-block-inversion: no
  interfaces: enp0s3 enp0s8
  sources:
  services: ssh
  ports: 8888/tcp
  protocols:
  forward: yes
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
```
```
[lawerz@localhost ~]$ sudo systemctl start fail2ban
[lawerz@localhost ~]$ sudo systemctl status fail2ban
● fail2ban.service - Fail2Ban Service
     Loaded: loaded (/usr/lib/systemd/system/fail2ban.service; disabled; preset: disabled)
     Active: active (running) since Tue 2024-09-10 17:14:22 CEST; 7s ago
       Docs: man:fail2ban(1)
    Process: 14788 ExecStartPre=/bin/mkdir -p /run/fail2ban (code=exited, status=0/SUCCESS)
   Main PID: 14789 (fail2ban-server)
      Tasks: 3 (limit: 11100)
     Memory: 12.2M
        CPU: 141ms
     CGroup: /system.slice/fail2ban.service
             └─14789 /usr/bin/python3 -s /usr/bin/fail2ban-server -xf start
```
```
[efrei_server]
enabled  = true
port     = 8888
filter   = efrei_server
logpath  = /var/log/efrei_server/server.log
maxretry = 5
findtime = 10m
bantime  = 10m
```

```
[lawerz@localhost fail2ban]$ sudo fail2ban-client status
Status
|- Number of jail:      1
`- Jail list:   efrei_server
[lawerz@localhost fail2ban]$ sudo fail2ban-client status efrei_server
Status for the jail: efrei_server
|- Filter
|  |- Currently failed: 0
|  |- Total failed:     0
|  `- File list:        /var/log/efrei_server/server.log
`- Actions
   |- Currently banned: 0
   |- Total banned:     0
   `- Banned IP list:
```
```
[lawerz@localhost fail2ban]$ sudo fail2ban-client status
Status
|- Number of jail:      1
`- Jail list:   efrei_server
[lawerz@localhost fail2ban]$ sudo fail2ban-client status efrei_server
Status for the jail: efrei_server
|- Filter
|  |- Currently failed: 5
|  |- Total failed:     5
|  `- File list:        /var/log/efrei_server/server.log
`- Actions
   |- Currently banned: 1
   |- Total banned:     1
   `- Banned IP list: 10.0.2.16
```
```
[lawerz@localhost ~]$ ncat 192.168.56.101 8888
Ncat: Connection refused.
```




