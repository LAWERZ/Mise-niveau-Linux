 **Partie 0**
 
🌞 Boom ça commence direct : je veux l'état initial du firewall
 ```

[lawerz@localhost ~]$ systemctl status firewalld
● firewalld.service - firewalld - dynamic firewall daemon
     Loaded: loaded (/usr/lib/systemd/system/firewalld.service; enabled; preset: enabled)
     Active: active (running) since Sat 2024-09-14 08:24:19 CEST; 7min ago
       Docs: man:firewalld(1)
   Main PID: 671 (firewalld)
      Tasks: 4 (limit: 11100)
     Memory: 45.6M
        CPU: 1.523s
     CGroup: /system.slice/firewalld.service
             └─671 /usr/bin/python3 -s /usr/sbin/firewalld --nofork --nopid

Sep 14 08:24:18 localhost systemd[1]: Starting firewalld - dynamic firewall daemon...
Sep 14 08:24:19 localhost systemd[1]: Started firewalld - dynamic firewall daemon.
``` 
