# Praktikum 9 - ressursihaldus
|  Küsimus  |  Linux  |  Windows  |  Linuxis kasutatud käsklus  |  Windowsis kasutatud tööriist  |
|  ---  |  ---  |  ---  |  ---  |  ---  |
|  Mitu protsessi kokku arvutis käib?  |  225  |  299  |  ps -aux \| wc -l  |  Task Manager -> Performance  |
|  Milline on kõige esimesena käivitatud protsess?  | /sbin/init splash |  | ps axo pid,cmd,comm,etime; ps -eo pid,args |  |
