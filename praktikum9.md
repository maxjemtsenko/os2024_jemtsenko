# Praktikum 9 - ressursihaldus
|  Küsimus  |  Linux  |  Windows  |  Linuxis kasutatud käsklus  |  Windowsis kasutatud tööriist  |
|  ---  |  ---  |  ---  |  ---  |  ---  |
|  Mitu protsessi kokku arvutis käib?  |  225  |  299  |  ps -aux \| wc -l  |  Task Manager -> Performance  |
|  Milline on kõige esimesena käivitatud protsess?  | /sbin/init splash | Secure System | ps axo pid,cmd,comm,etime; ps -eo pid,args | Process Explorer -> Start Time |
| Milliste kasutajate protsesse arvutis käib? | avahi, colord, kernoops, maksim, messagebus, root, rtkit, syslog, systemd-oom, systemd-resolve, systemd-timesyns | UMFD-0, UMFD-6, maksi, nx, LOCAL SERVICE, NETWORK SERVICE, SYSTEM, DWM-6 | ps -eo user \| sort \| uniq | Process Explorer -> User Name |
|  Kui kaua on arvuti järjest töötanud (up time)? (Alternatiivselt võib vastata ka, millal (kuupäev ja kellaaeg) arvuti viimati käima pandi.)  |  15:21:54 up 7 min  |  0:23:24:20  |  uptime  |  Task Manager -> Performance  |
|  Milline protsess käivitati kõige hiljem (viimasena)? (Mitte võtta arvesse programmi, millega seda infot otsida.)  |  4220       00:07 [kworker/u5:0]  |  CreationDate=20241119153508.518921+120
Name=chrome.exe  |  ps -eo pid,etime,cmd --sort=-etime  |  CMD -> wmic process get Name,CreationDate /format:list  |
