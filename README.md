# 目录

- [目录](#目录)
- [0. 前置知识 Background](#0-前置知识-background)
  - [0.1 操作系统使用](#01-操作系统使用)
  - [0.2 Shell使用](#02-shell使用)
  - [0.3 Web三剑客](#03-web三剑客)
  - [0.4 编程语言](#04-编程语言)
  - [0.5 数据库](#05-数据库)
  - [0.6 协议](#06-协议)
- [1. 信息收集 Reconnaissance](#1-信息收集-reconnaissance)
- [2. 漏洞挖掘 Vulnerabilities](#2-漏洞挖掘-vulnerabilities)
  - [2.1 SQLi](#21-sqli)
  - [2.2 File Upload](#22-file-upload)
  - [2.3 XSS](#23-xss)
  - [2.4 CSRF](#24-csrf)
  - [2.5 Deserialization](#25-deserialization)
  - [2.6 Payment](#26-payment)
  - [2.7 WAF \& Bypass](#27-waf--bypass)
  - [2.8 White box (Code Audit)](#28-white-box-code-audit)
- [3. 权限提升 Privilege Escalation](#3-权限提升-privilege-escalation)
  - [3.1 提权原理总结](#31-提权原理总结)
  - [3.2 手工枚举](#32-手工枚举)
  - [3.3 自动枚举](#33-自动枚举)
- [4. 后渗透期 PostPentest](#4-后渗透期-postpentest)
- [5. 对抗攻防 AWD](#5-对抗攻防-awd)
- [5. 社会工程 Social Engeering](#5-社会工程-social-engeering)
- [6. 软件开发 Software Engeering](#6-软件开发-software-engeering)
- [Appendix. 靶场](#appendix-靶场)
- [Appendix. 书籍](#appendix-书籍)
- [Appendix. 学习资料](#appendix-学习资料)

---

# 0. 前置知识 Background

## 0.1 操作系统使用

- Linux
    - Black Arch Linux
    - Kali Linux
    - Parrot OS
- Windows
    - Win Servers
    - Win7
    - Win10
    - Win11
- macOS

## 0.2 Shell使用

- bash
- zsh
- fish

## 0.3 Web三剑客

- HTML
- CSS
- JS

## 0.4 编程语言

主流:
- Python
- Golang
- Java
- C
- C++

其他:
- Lua
- Perl
- Ruby

## 0.5 数据库

- SQL
  - MySQL
  - MSSQL
  - Oracle SQL
- NoSQL
  - Redis
  - MongoDB
  - ElasticSearch

## 0.6 协议

- HTTP
- HTTPS
- DHCP
- DNS
- SSH
- ARP
- SMB
- Socks5
- VPN
- FTP
- ...

# 1. 信息收集 Reconnaissance


# 2. 漏洞挖掘 Vulnerabilities

## 2.1 SQLi

## 2.2 File Upload

## 2.3 XSS

## 2.4 CSRF

## 2.5 Deserialization

## 2.6 Payment

## 2.7 WAF & Bypass

## 2.8 White box (Code Audit)

# 3. 权限提升 Privilege Escalation

主流
- UGO
- SUID, SGID
- Capabilities
- AppArmor, Selinux
- ACL

其他
- Grsecurity
- Pax
- ExecShield
- ASLR
- TOMOYO Linux
- SMACK
- Yama
- CGroups
- Linux Namespaces
- StackGuard
- Proplice
- seccomp
- ptrace
- capsicum
- Mprotect
- chroot
- firejail

## 3.1 提权原理总结

1. 低权限可以修改可执行文件or脚本，再以高权限身份运行；
2. 低权限的运维人员也会记录、输入备份程序，以备使用高权限的时候完成操作（用户行为）；
3. 在权限体系的上层捕捉、拦截、修改凭据信息or权限信息。

## 3.2 手工枚举

- 系统枚举
  - 用户信息
    - whoami
    - id
    - who
    - w
    - last
  - 系统信息
    - uname -a
    - lsb_release -a
    - cat /proc/version
    - cat /etc/issue
    - hostnamectl
- 网络枚举
  - ifconfig
  - ip
    - ip a
    - ip route
    - ip neigh
  - netstat
    - netstat -a
    - netstat -at (-au)
    - netstat -l
    - netstat -s
    - netstat -ano
- 权限枚举
  - sudo -l
- getcap -r 2>/dev/null
- ls -liah
- history
- cat /etc/passwd
- cat /etc/crontab
- echo $PATH
- env
- 进程枚举
  - ps -ef, ps aux
  - ps axjf
  - top -n 1
- find / -perm -u=s -type f 2>/dev/null
- which awk (perl, python, ruby, gcc, vi, vim, nmap, find, netcat, nc, wget, tftp, ftp, tmux, screen ...) 2>/dev/null
- cat /etc/fstab 磁盘挂载情况

## 3.3 自动枚举

工具列表
- [https://github.com/carlospolop/PEASS-ng](https://github.com/carlospolop/PEASS-ng)
- [https://github.com/rebootuser/LinEnum](https://github.com/rebootuser/LinEnum)
- [https://github.com/diego-treitos/linux-smart-enumeration](https://github.com/diego-treitos/linux-smart-enumeration)
- [https://github.com/The-Z-Labs/linux-exploit-suggester](https://github.com/The-Z-Labs/linux-exploit-suggester)
- [https://github.com/sleventyeleven/linuxprivchecker](https://github.com/sleventyeleven/linuxprivchecker)
- [https://github.com/pentestmonkey/unix-privesc-check](https://github.com/pentestmonkey/unix-privesc-check)

工具使用  
[👉🏻GO](./3.PrivilegeEscalation/UsageOfTools.md)

# 4. 后渗透期 PostPentest


# 5. 对抗攻防 AWD


# 5. 社会工程 Social Engeering


# 6. 软件开发 Software Engeering


# Appendix. 靶场

- [OSCP](https://docs.google.com/spreadsheets/d/1dwSMIAPIam0PuRBkCiDI88pU3yzrqqHkDtBngUHNCw8/edit#gid=0)
- VulnHub
- HackTheBox
- TryHackMe
- DVWA

# Appendix. 书籍

- 《OWASP权威指南》

# Appendix. 学习资料
