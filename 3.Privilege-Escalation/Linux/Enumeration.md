# Information Gathering

- OS Version
```bash
uname -a
cat /etc/*-release
```

- running processes + ports
```bash
ps aux
ps aux | grep LISTEN
netstat -tulpn
```