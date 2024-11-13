# Praktikum 9 - ressursihaldus
|  Küsimus  |  Linux  |  Windows  |  Linuxis kasutatud käsklus  |  Windowsis kasutatud tööriist  |
|  ---  |  ---  |  ---  |  ---  |  ---  |
|  Mitu protsessi kokku arvutis käib?  |  225  |  299  |  ps -aux \| wc -l  |  Task Manager -> Performance  |
|  Milline on kõige esimesena käivitatud protsess?  | /sbin/init splash | Secure System | ps axo pid,cmd,comm,etime; ps -eo pid,args | Process Explorer -> Start Time |
| Milliste kasutajate protsesse arvutis käib? | avahi, colord, kernoops, maksim, messagebus, root, rtkit, syslog, systemd-oom, systemd-resolve, systemd-timesyns | UMFD-0, UMFD-6, maksi, nx, LOCAL SERVICE, NETWORK SERVICE, SYSTEM, DWM-6 | ps -eo user \| sort \| uniq | Process Explorer -> User Name |
