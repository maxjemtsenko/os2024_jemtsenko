# Praktikum12 - Skriptimine Linuxis
Praktikumis õppisime skriptide kirjutamise põhitõdesid, muutujate, juhtkonstruktsioonide ja funktsioonide kasutamist koos näidetega praktiliseks tööks.

**Ülesanne 3:** 
```
#!/bin/sh
echo "Sisesta nimi:"
read nimi
echo "Sisesta eriala:"
read eriala
echo "Sisesta matriklinumber:"
read number
echo "$nimi, $eriala, $number"
```
**Ülesanne 4:**
```
#!/bin/bash
A=$1
B=$2

valjund=$(ls)
for i in $valjund
do
    if [ ${i##*.} = $A ]
    then
        echo "$i"
        mv $i $(echo $i | sed -e s/$A/$B/g)
    fi
done

echo "muutunud"

valjund=$(ls)
for i in $valjund
do
    if [ ${i##*.} = $B ]
    then
        echo "$i"
    fi
done
```
**Ülesanne 5:**
```
#!/bin/bash
protsess=$1
IFS=$'\n'
for i in $(ps -A)
do
	tuhikuta=$(echo $i | tr -s ' ')
	pid=$(echo "$tuhikuta" | cut -d ' ' -f2)
	name=$(echo "$tuhikuta" | cut -d ' ' -f5)
	if [ "$name" == "$protsess" ]
	then
		echo "$name, $pid"
	fi
done
```
**Ülesanne 6:**
```
#!/bin/bash

astendamine () {
	b=$1
	a=1
	while [ $a -lt $2 ]
	do
		b=$(($b*$1))
		a=$(($a+1))
	done
	echo $b
}
vastus=$( astendamine 9 4)
echo $vastus
```
![praktikum12](./pildid/praks12_3.png)
![praktikum12](./pildid/praks12_4.png)
![praktikum12](./pildid/praks12_5.png)
![praktikum12](./pildid/praks12_6.png)
![praktikum12](./pildid/praks12_7.1.png)
![praktikum12](./pildid/praks12_7.2.png)
