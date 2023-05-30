# File descriptor

File descriptors are a fundamental concept in Unix-like operating systems, including Linux and macOS. They are used to identify and manipulate input/output (I/O) resources such as `files`, `pipes`, `sockets`, and `devices`.

In Unix systems, everything is treated as a file, including hardware devices and network sockets. Each file has a unique file descriptor associated with it, which is a non-negative integer used to identify the file in the system. The first three file descriptors, 0, 1, and 2, are reserved for standard input (`stdin`), standard output (`stdout`), and standard error (`stderr`), respectively.

The file descriptor mechanism allows processes to read from or write to files or other I/O resources using a common set of system calls, such as `open()`, `read()`, `write()`, and `close()`. By using file descriptors, processes can easily redirect their input or output to other files or pipes, or even across a network to other machines.

All in all, file descriptors play a crucial role in the Unix philosophy of treating everything as a file, and provide a unified and flexible way for processes to access and manipulate I/O resources in a consistent manner.



# Shell Redirection

- `>, >>, <`
- `n>, n>>`
- `&>, >& target` = `1> target 2>&1`; `&>>`
- `|`
- `tee`

Exploration:

```bash
strace -f bash -c 'bash -i /dev/tcp/127.0.0.1/4444 0>&1' > strace.out
cat strace.out | grep -n '127.0.0.1'

# Output(version 2018):
199: [pid  5106] socket(AF_INET, SOCK_STREAM, IPPROTO_TCP) = 3
200: [pid  5106] connect(3, {sa_family=AF_INET, sin_port=htons(4444), sin_addr=inet_addr("127.0.0.1")}, 16) = 0
201: [pid  5106] dup2(3, 1)                  = 1
202: [pid  5106] close(3)                    = 0
203: [pid  5106] dup2(1, 2)                  = 2
204: [pid  5106] dup2(1, 0)                  = 0
205: [pid  5106] fcntl(1, F_GETFD)           = 0
206: [pid  5106] execve("/bin/bash", ["bash", "-i"], 0x2485008 /* 57 vars */) = 0
```

Using redictions is not like connecting tubes, while `>` and `<` are value assignments. When `ls -l > dir.list`, it is not "sending" the output of ls to the dir.list file. It is actually assigning the dir.list file to the standard output of ls.

- `>` checks if a target is available for writing
- `<` checks if a target is available for reading



# sh vs. bash vs. zsh

1. /bin/sh is /bin/bash ?

   - If bash is invoked with the name sh, it tries to mimic the startup behavior of historical  versions of sh as closely as possible, while conforming to the POSIX standard as well.  

   - When invoked as an interactive login  shell,  or  a  non-interactive shell  with the --login option, it first attempts to read and execute commands from `/etc/profile`, `~/.profile`, `~/.bashrc` and etc, in that order. The --noprofile option may be used  to inhibit this behavior. 

   - When invoked as an interactive shell with the name sh, bash looks for the variable ENV, expands its value  if  it  is  defined,  and  uses  the expanded value as the name of a file to read and execute.  Since a shell invoked as sh does not attempt to read and execute commands from any other startup files,  the --rcfile  option  has  no effect.  A non-interactive shell invoked with the name sh does not attempt to read any other startup files.  When invoked as sh, bash  enters posix mode after the startup files are read.


2. Why `/dev/tcp/host/port` not works in zsh and fish:

   - The feature is a bashism, meaning it is not a standard feature of all shells.

   - Bash implements this feature by creating a socket file descriptor and redirecting it to the standard input, output, or error streams of a command. However, other shells like zsh and fish do not support this feature.

   - If you need to use `/dev/tcp/host/port` in zsh or fish, you can try using the `nc` or `socat` command instead.


```bash
# bash
echo hello,world > /dev/tcp/127.0.0.1/4444
# other shells:
echo "hello" | nc 127.0.0.1 4444 # zsh
echo "hello" | nc -c 127.0.0.1 4444 # fish
echo "hello" | socat - TCP4:127.0.0.1:4444
```



# Interactive Shell

Here, we mainly talk about bash. According to the Bash man page (`man bash`), option `-i` means starting an *interactive shell*.

- In interactive mode, when Bash shell is started with the `-i` option, it sets the standard input to a terminal device (usually a terminal window) and sets the shell to read and execute commands entered by the user. This allows the user to interact with the shell and run commands in the shell, just like in a terminal window.

- In non-interactive mode, Bash shell is typically used for batch processing tasks or automation scripts. In this mode, the shell does not wait for user input but reads commands from a script or standard input. In this case, the shell usually does not have a terminal device available and cannot perform interactive operations.