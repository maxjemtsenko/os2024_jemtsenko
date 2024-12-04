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
echo "Sisesta laiend A:"
read A
echo "Sisesta laiend B:"
read B

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
