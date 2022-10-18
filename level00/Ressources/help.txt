# LEVEL00


#### FIND the first file who can run only as flag00...

Utiliser la commande `find` pour trouver les fichiers du groupe ou user **flag00**

- find / -group flag00
- find / -user flag00

#### Resultat

```
/usr/sbin/john
/rofs/usr/sbin/john
```

#### Verification des droits

```
----r--r-- 1 flag00 flag00 15 Mar  5  2016 john
```

#### cat du fichier

`cdiiddwpgswtgt`

#### Utilisation du site 
https://www.dcode.fr/identification-chiffrement

Chiffrement ROT (Rotation)
ROT+15

#### message decode
`nottoohardhere`

#### getflag
Check flag.Here is your token : x24ti5gi3x0ol2eh4esiuxias
