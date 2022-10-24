# LEVEL05

Quand on se connecte en **ssh** nous pouvont voir ce message : 

```
level05@192.168.56.103's password: 
You have new mail.
```

Nous pouvons faire un echo $MAIL pour trouver le fichier local des mails (*/var/mail/level05*)

```
*/2 * * * * su -c "sh /usr/sbin/openarenaserver" - flag05
```

Le fichier level05 est un cronjob, il est éxécuté toutes les 30 secondes.

fichier **openarenaserver** :

```
#!/bin/sh

for i in /opt/openarenaserver/* ; do
	(ulimit -t 5; bash -x "$i")
	rm -f "$i"
done
```

Nous pouvons voir qu'il parcours tous les fichiers dans /opt/openarenaserver et les exécutera dans un shell bash.
Nous devons créer un script pour éxécuter la commande `getflag` 

```
#!/bin/sh

getflag > /tmp/flag05
```

Check flag.Here is your token : viuaaale9huek52boumoomioc

