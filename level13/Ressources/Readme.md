# LEVEL13

ls -la :

```
-rwsr-sr-x 1 flag13  level13 7303 Aug 30  2015 level13
```

https://beta.hackndo.com/assembly-basics/

(gdb) info variables
(gdb) info variables start
(gdb) disass main

```
(gdb) disass main
Dump of assembler code for function main:
   0x0804858c <+0>:	push   %ebp
   0x0804858d <+1>:	mov    %esp,%ebp
   0x0804858f <+3>:	and    $0xfffffff0,%esp
   0x08048592 <+6>:	sub    $0x10,%esp
   0x08048595 <+9>:	call   0x8048380 <getuid@plt>
   0x0804859a <+14>:	cmp    $0x1092,%eax
   0x0804859f <+19>:	je     0x80485cb <main+63>
   0x080485a1 <+21>:	call   0x8048380 <getuid@plt>
   0x080485a6 <+26>:	mov    $0x80486c8,%edx
   0x080485ab <+31>:	movl   $0x1092,0x8(%esp)
   0x080485b3 <+39>:	mov    %eax,0x4(%esp)
   0x080485b7 <+43>:	mov    %edx,(%esp)
   0x080485ba <+46>:	call   0x8048360 <printf@plt>
   0x080485bf <+51>:	movl   $0x1,(%esp)
   0x080485c6 <+58>:	call   0x80483a0 <exit@plt>
   0x080485cb <+63>:	movl   $0x80486ef,(%esp)
   0x080485d2 <+70>:	call   0x8048474 <ft_des>
   0x080485d7 <+75>:	mov    $0x8048709,%edx
   0x080485dc <+80>:	mov    %eax,0x4(%esp)
   0x080485e0 <+84>:	mov    %edx,(%esp)
   0x080485e3 <+87>:	call   0x8048360 <printf@plt>
   0x080485e8 <+92>:	leave  
   0x080485e9 <+93>:	ret    
End of assembler dump.
```

```
(gdb) break *main+14
Note: breakpoint 1 also set at pc 0x804859a.
Breakpoint 3 at 0x804859a
(gdb) p $eax
$3 = 40
(gdb) run
The program being debugged has been started already.
Start it from the beginning? (y or n) y

Starting program: /home/user/level13/level13 

Breakpoint 1, 0x0804859a in main ()
(gdb) p $eax
$4 = 2013
(gdb) set $eax=4242
(gdb) p $eax
$5 = 4242
(gdb) next
Single stepping until exit from function main,
which has no line number information.
your token is 2A31L79asukciNyi8uppkEuSx

Breakpoint 2, 0x080485e8 in main ()
(gdb) 
```

