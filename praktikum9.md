# Praktikum 9 - ressursihaldus
|  Küsimus  |  Linux  |  Windows  |  Linuxis kasutatud käsklus  |  Windowsis kasutatud tööriist  |
|  ---  |  ---  |  ---  |  ---  |  ---  |
|  Mitu protsessi kokku arvutis käib?  |  225  |  299  |  ps -aux \| wc -l  |  Task Manager -> Performance -> Processes |
|  Milline on kõige esimesena käivitatud protsess?  | /sbin/init splash | Secure System | ps axo pid,cmd,comm,etime; ps -eo pid,args | Process Explorer -> Start Time |
| Milliste kasutajate protsesse arvutis käib? | avahi, colord, kernoops, maksim, messagebus, root, rtkit, syslog, systemd-oom, systemd-resolve, systemd-timesyns | UMFD-0, UMFD-6, maksi, nx, LOCAL SERVICE, NETWORK SERVICE, SYSTEM, DWM-6 | ps -eo user \| sort \| uniq | Process Explorer -> User Name |
|  Kui kaua on arvuti järjest töötanud (up time)? (Alternatiivselt võib vastata ka, millal (kuupäev ja kellaaeg) arvuti viimati käima pandi.)  |  15:21:54 up 7 min  |  0:23:24:20  |  uptime  |  Task Manager -> Performance -> Up time  |
|  Milline protsess käivitati kõige hiljem (viimasena)? (Mitte võtta arvesse programmi, millega seda infot otsida.)  |  4220   00:07 [kworker/u5:0]  |  CreationDate=20241119153508.518921+120 Name=chrome.exe  |  ps -eo pid,etime,cmd --sort=-etime  |  Process Explorer -> Start Time  |
|  Milline on kõige rohkem protsessoriaega võttev protsess ja kui mitu protsenti protsessoriajast ta tarbib?  |  /usr/bin/gnome-shell - 7.9%  |  Task Manager - 4.2%  |  htop  |  Task Manager -> Processes -> CPU  |
|  Milline on kõige rohkem virtuaalmälu (aadressiruumi, commit, Virtual Size) võttev protsess?  |  /usr/bin/gnome-shell - 4527M  |  chrome.exe - 3 432 750 972 K  |  htop -> VIRT  |  Process Explorer -> Virtual Size  |
|  Milline on kõige rohkem füüsilist mälu (working set) võttev protsess?  |   /usr/bin/gnome-shell - 15,4%  |  VirtualBox Virtual Machine - 2893.7 MB  |  htop -> MEM  |  Task Manager -> Processes -> Memory  |
|  Kui palju füüsilisest mälust (Physical Memory) on vaba ja kui palju hõivatud?  |  Vaba - 237 Mi, hõivatud - 943 Mi  |  Vaba - 3.1 GB, hõivatud - 12,3 GB  |  free -h  |  Task Manager -> Performance -> Memory  |
|  Kui palju on põhikettal (C:, /) vaba ruumi mahult (GB) ja protsentuaalselt?  |  Vaba - 24 G (49%)  |  Vaba ruumi - 233 GB (49.16%)  |  df -h  |  File explorer -> Thic PC -> C: Properties -> General  |
