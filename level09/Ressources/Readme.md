# LEVEL09

ls -la : 

```
-rwsr-sr-x 1 flag09  level09 7640 Mar  5  2016 level09
----r--r-- 1 flag09  level09   26 Mar  5  2016 token
```

```
level09@SnowCrash:~$ cat token 
f4kmm6p|=�p�n��DB�Du{��
```

ltrace ./level09 token :

```
level09@SnowCrash:~$ ltrace ./level09 token
__libc_start_main(0x80487ce, 2, 0xbffff7d4, 0x8048aa0, 0x8048b10 <unfinished ...>
ptrace(0, 0, 1, 0, 0xb7e2fe38)       = -1
puts("You should not reverse this"You should not reverse this
)  = 28
+++ exited (status 1) +++
```

Test de plusieurs argument différent au serveur : 


```
level09@SnowCrash:~$ ./level09 /tmp/test
/uos3ykz|

level09@SnowCrash:~$ ./level09 /tmp/abc
/uos3fhj

level09@SnowCrash:~$ ./level09 "Hello World"
Hfnos%]vzun

level09@SnowCrash:~$ ./level09 "hello"
hfnos

```

On peut voir que chaque lettre du mot et remplacé par son nombre ascii + son index dans la chaine.

exemple :

```
level09@SnowCrash:~$ ./level09 "hello"
hfnos

h + 0 = h
e + 1 = f
l + 2 = n
l + 3 = o
o + 4 = s
```

Nous allons faire un script python qui prend une chaine encrypter et qui applique l'algorythme inverse, qui remplace la lettre du mot par son nombre ascii - son index dans la chaine. 

```py
import sys

str_decrypt = []
for i, c in enumerate(sys.argv[1]):
        str_decrypt.append(chr(ord(c) - i))
print("".join(str_decrypt))
```


level09@SnowCrash:~$ python /tmp/decrypt.py "$(cat token)"
f3iji1ju5yuevaus41q1afiuq



