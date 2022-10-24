# LEVEL02


#### Download file level02.pcap

```
scp -P 4242 level02@192.168.56.103:/home/user/level02/level02.pcap /mnt/nfs/homes/jereligi/Desktop/42Snow-crash/level02/Ressources
```

#### Analysez les trames réseaux avec WireShark

``` 
0000   00 24 1d 0f 00 ad 08 00 27 cc 8a 1e 08 00 45 00   .$......'.....E.
0010   00 41 d4 b3 40 00 40 06 16 77 3b e9 eb df 3b e9   .A..@.@..w;...;.
0020   eb da 2f 59 99 4f ba a8 fb 18 9d 18 15 7b 80 18   ../Y.O.......{..
0030   01 c5 27 9d 00 00 01 01 08 0a 02 c2 3c 62 01 1b   ..'.........<b..
0040   b9 87 00 0d 0a 50 61 73 73 77 6f 72 64 3a 20      .....Password:


0000   00 24 1d 0f 00 ad 08 00 27 cc 8a 1e 08 00 45 00   .$......'.....E.
0010   00 57 d4 cb 40 00 40 06 16 49 3b e9 eb df 3b e9   .W..@.@..I;...;.
0020   eb da 2f 59 99 4f ba a8 fb 29 9d 18 15 90 80 18   ../Y.O...)......
0030   01 c5 dd 9c 00 00 01 01 08 0a 02 c2 52 7d 01 1b   ............R}..
0040   c2 5e 00 0d 0a 4c 6f 67 69 6e 20 69 6e 63 6f 72   .^...Login incor
0050   72 65 63 74 0d 0a 77 77 77 62 75 67 73 20 6c 6f   rect..wwwbugs lo
0060   67 69 6e 3a 20                                    gin:
```

#### Récupération des conversations

- Onglet statistics
- Conversations
- TCP
- Follow Stream

```
Linux 2.6.38-8-generic-pae (::ffff:10.1.1.2) (pts/10)

..wwwbugs login: l.le.ev.ve.el.lX.X
..
Password: ft_wandr...NDRel.L0L
.
..
Login incorrect
wwwbugs login: 
```

#### Analyze appronfondi des packets

`ft_wandr...NDRel.L0L`

Les `.` sont des caractères non imprimables (7f) qui est le caractère DEL


password : ft_waNDReL0L

getflag : kooda2puivaav1idi4f57q8iq
