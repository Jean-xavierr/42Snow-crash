# LEVEL14

`gdb getflag`

```
   0x08048b48 <+514>:	jmp    0x8048e06 <main+1216>
   0x08048b4d <+519>:	cmp    eax,0xbbc
   0x08048b52 <+524>:	je     0x8048c83 <main+829>
   0x08048b58 <+530>:	cmp    eax,0xbbc
   0x08048b5d <+535>:	ja     0x8048ca7 <main+865>
   0x08048b63 <+541>:	jmp    0x8048c5f <main+793>
   0x08048b68 <+546>:	cmp    eax,0xbc2
   0x08048b6d <+551>:	je     0x8048d5b <main+1045>
   0x08048b73 <+557>:	cmp    eax,0xbc2
   0x08048b78 <+562>:	ja     0x8048b95 <main+591>
   0x08048b7a <+564>:	cmp    eax,0xbc0
   0x08048b7f <+569>:	je     0x8048d13 <main+973>
   0x08048b85 <+575>:	cmp    eax,0xbc0
   0x08048b8a <+580>:	ja     0x8048d37 <main+1009>
   0x08048b90 <+586>:	jmp    0x8048cef <main+937>
   0x08048b95 <+591>:	cmp    eax,0xbc4
   0x08048b9a <+596>:	je     0x8048da3 <main+1117>
   0x08048ba0 <+602>:	cmp    eax,0xbc4
   0x08048ba5 <+607>:	jb     0x8048d7f <main+1081>
   0x08048bab <+613>:	cmp    eax,0xbc5
   0x08048bb0 <+618>:	je     0x8048dc4 <main+1150>
   0x08048bb6 <+624>:	cmp    eax,0xbc6
   0x08048bbb <+629>:	je     0x8048de5 <main+1183>
   0x08048bc1 <+635>:	jmp    0x8048e06 <main+1216>
   0x08048bc6 <+640>:	mov    eax,ds:0x804b060
```

Il faut trouver la fonction qui donne le flag14, en regardant les registres on peu tomber sur un registre qui contient le numéro de group du flag14 3014 :

```
(gdb) p 0xbc6
$1 = 3014

(gdb) break main
Breakpoint 1 at 0x804894a
(gdb) run
Starting program: /bin/getflag
(gdb) jump *0x8048de5
Continuing at 0x8048de5.
7QiHafiNa3HVozsaXkawuYrTstxbpABHD8CPnHJ
*** stack smashing detected ***: /bin/getflag terminated

```


