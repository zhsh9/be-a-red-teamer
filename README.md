# Inventory

![License](https://img.shields.io/github/license/zhsh9/be-a-red-teamer)
![Repo Size](https://img.shields.io/github/repo-size/zhsh9/be-a-red-teamer?color=green)
![Activity](https://img.shields.io/github/commit-activity/w/zhsh9/be-a-red-teamer?color=orange)
![zhsh9](https://img.shields.io/github/followers/zhsh9?style=social)
![GitHub stars](https://img.shields.io/github/stars/zhsh9/be-a-red-teamer?style=social)

- [Inventory](#inventory)
- [0. 前置知识 Background](#0-前置知识-background)
  - [0.1 操作系统使用](#01-操作系统使用)
  - [0.2 Shell使用](#02-shell使用)
  - [0.3 Web三剑客](#03-web三剑客)
  - [0.4 编程语言](#04-编程语言)
  - [0.5 数据库](#05-数据库)
  - [0.6 协议](#06-协议)
  - [0.7 二进制](#07-二进制)
  - [0.8 效率工具](#08-效率工具)
  - [0.9 渗透工具](#09-渗透工具)
- [1. 信息收集 Reconnaissance](#1-信息收集-reconnaissance)
  - [Social Engineer](#social-engineer)
  - [Scan Methods](#scan-methods)
  - [Host and Port](#host-and-port)
  - [IPv6 Scan](#ipv6-scan)
  - [OS](#os)
  - [Database](#database)
  - [Directory](#directory)
  - [DNS](#dns)
  - [CDN](#cdn)
  - [WAF](#waf)
  - [Web源码](#web源码)
  - [Subdomain](#subdomain)
  - [站点搭建](#站点搭建)
  - [资产收集](#资产收集)
- [2. 漏洞挖掘 Vulnerabilities](#2-漏洞挖掘-vulnerabilities)
  - [Command Injection](#command-injection)
  - [SQLi](#sqli)
  - [File Upload](#file-upload)
  - [XSS](#xss)
  - [CSRF](#csrf)
  - [Deserialization](#deserialization)
  - [Payment](#payment)
  - [WAF \& Bypass](#waf--bypass)
  - [Code Audit](#code-audit)
- [3. 权限提升 Privilege Escalation](#3-权限提升-privilege-escalation)
  - [3.0 Shells](#30-shells)
  - [3.1 提权原理总结](#31-提权原理总结)
  - [3.2 手工枚举](#32-手工枚举)
  - [3.3 自动枚举](#33-自动枚举)
- [4. 后渗透期 Post Pentest](#4-后渗透期-post-pentest)
- [5. 对抗攻防 AWD](#5-对抗攻防-awd)
- [5. 社会工程 Social Engeering](#5-社会工程-social-engeering)
- [6. 软件开发 Software Engeering](#6-软件开发-software-engeering)
- [Appendix. 链接](#appendix-链接)
- [Appendix. 靶场](#appendix-靶场)
- [Appendix. 书籍](#appendix-书籍)
- [Appendix. 学习资料](#appendix-学习资料)

Red Team Kill Chain:

```
┌────────────────┐
│                │
│   Initial      │
│   Recon        │
│                │
└────────┬───────┘
         │
         │
┌────────▼───────┐
│                │
│   Initial      │
│   Compromise   │
│                │
└────────┬───────┘
         │
         │
┌────────▼───────┐
│                │
│   Establish    │
│   Foothold     │
│                │
└────────┬───────┘
         │
         │
┌────────▼───────┐      ┌────────────────┐
│                │      │                │
│   Escalte      ◄──────┤   Maintain     │
│   Privileges   │      │   Presence     │
│                │      │                │
└────────┬───────┘      └────────▲───────┘
         │                       │
         │                       │
┌────────▼───────┐      ┌────────┴───────┐
│                │      │                │
│   Internal     │      │   Move         │
│   Recon        ├──────►   Laterally    │
│                │      │                │
└────────┬───────┘      └────────────────┘
         │
         │
┌────────▼───────┐
│                │
│   Complete     │
│   Mission      │
│                │
└────────────────┘
```

# 0. 前置知识 Background

## 0.1 操作系统使用

OS:
- Linux
    - Black Arch Linux
    - Kali Linux, <u>[*👉🏻GO*](./0.Background/OS/Kali-Linux/README.md)</u>
    - Parrot OS
- Windows
    - Win Servers
    - Win7
    - Win10
    - Win11
- macOS

Integrated Pentest Environment:
- Exegol on macOS, <u>[*👉🏻GO*](./0.Background/OS/macOS/Exegol.md)</u>
- Kali Linux VM, PD on macOS
- Kali Linux VM, OrbStack on macOS

## 0.2 Shell使用

- bash, <u>[*👉🏻GO*](./0.Background/OS/Linux/bash/README.md)</u>
- zsh
- fish
- powershell

## 0.3 Web三剑客

- HTML
- CSS
- JS

## 0.4 编程语言

主流:
- Python, <u>[*👉🏻Go*](./0.Background/Language/Python/README.md)</u>
- PHP, <u>[*👉🏻Go*](./0.Background/Language/PHP/README.md)</u>
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
  - MySQL, <u>[*👉🏻Go*](./0.Background/Database/MySQL/README.md)</u>
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

## 0.7 二进制

- Assembly, <u>[*👉🏻Go*](./0.Background/Binary/Assembly/README.md)</u>
- Reverse Engineering, x86_64
  - Basic: C/C++
  - Windows Platform
  - Linux PLatform

## 0.8 效率工具

- tmux, <u>[*👉🏻Go*](./0.Background/Tool/tmux.md)</u>
- vim, <u>[*👉🏻Go*](./0.Background/Tool/vim.md)</u>
- ranger
- entr, watchdog
- zsh, fish
- curl

## 0.9 渗透工具

- Burp Suite Pro, <u>[*👉🏻Go*](./0.Background/Tool/BurpSuitePro.md)</u>
- [arsenal](https://github.com/Orange-Cyberdefense/arsenal)
- [Bug-bounty checklist](https://github.com/sehno/Bug-bounty)
- [goby](https://github.com/gobysec/Goby)
- [LadonGo](https://github.com/k8gege/LadonGo)

# 1. 信息收集 Reconnaissance

```
      subdomain  top-domain-level    signifies query
        ───        ───                   ──
https://sub.domain.com/blog/article/search?param=1
──────      ──────     ─────────────────── ───────
scheme      domain      path or location   parameter(s)
                             of contents
```

## Social Engineer

Generate word list:

- [cewl](https://github.com/digininja/CeWL)

## Scan Methods

- [nmap](https://github.com/nmap/nmap)
```bash
# 扫描端口，然后探测版本（用默认的脚本）
nmap -n -v -Pn -sS -p- $IP --max-retries=0
nmap -n -v -sC -sV -p$PORTS $IP
# 
nmap -sn $IP/24                   # 寻找IP
nmap -sT --min-rate 10000 -p- $IP
nmap -sU --min-rate 10000 -p- $IP # TCP|UDP扫描全端口
nmap -sT -sV -sC -O -p$PORTS $IP  # TCP使用默认脚本扫描全端口+版本+OS信息
nmap --script-vuln -p$PORTS $IP   # 漏洞脚本扫描
# 一句话全模式扫描开放端口
nmap -A $IP -oA nmap/all -p`nmap -sS -sU -Pn -p- $IP --min-rate 10000 | grep '/tcp\|/udp' | awk -F '/' '{print $1}' | sort -u | tr '\n' ','`
```
- [AutoRecon](https://github.com/Tib3rius/AutoRecon)
- [RustScan](https://github.com/RustScan/RustScan)

## Host and Port

- nmap
```bash
nmap -sn $IP/24
nmap -sU --min-rate 10000 -p- $IP
nmap -sT -sC -sV -O --min-rate 10000 -p- $IP
nmap --script=vuln -p$PORTS $IP
```
- ping 主机发现
```bash
ping -c 3 -W 1 $IP
for i in {1..254}; do ping -c 1 -W 1 $sub_IP.$i | grep from; done
```
- nc 端口扫描
```bash
nc.traditional -vv -z $IP 1-65535 2>&1 | grep -v refused
```
- /dev/tcp/xxx/nnn 端口扫描
```bash
IP=xxx.xxx.xxx.xxx
for i in {1..65535}
do
    (echo < /dev/tcp/$IP/$i) &>/dev/null && printf "\n[+] Open port: %d\n" "$i" || printf "."
done
```

## IPv6 Scan

- nmap
```bash
nmap -6 --min-rate 10000 -p- $IPv6
```
- [IOXIDResolver](https://github.com/mubix/IOXIDResolver)
```bash
python IOXIDResolver.py -t $IP
```
- [snmpwalk](http://www.net-snmp.org/docs/man/snmpwalk.html)
```bash
snmpwalk -v2c -c public $IP
```

## OS

- 有web端：
  - Windows大小写不敏感
  - 工具识别
- 没有web：
  - nmap -O
- TTL（不准确的方式）：
```
1、WINDOWS NT/2000   TTL：128
2、WINDOWS 95/98     TTL：32
3、UNIX              TTL：255
4、LINUX             TTL：64
5、WIN7         	    TTL：64
```
- 特殊端口：22, 139, 445, 1433, 3389

## Database

数据库不同表示的结构也是不同、写法结构也不同，因此产生的漏洞也不一样。不同的数据库的攻击方式也不完全一样。

- default pair
  1. asp + access/mssql
  2. php + mysql
  3. aspx + mssql
  4. jsp + mysql/oracle
  5. python + mongodb
- common port
  - SQL
    - mysql, 3306
    - sqlserver, 1433
    - oracle, 1521
    - postgresql, 5432
  - NoSQL
    - mongodb, 27017
    - redis, 6379
    - memcached, 11211

## Directory

wordlist:

- [SecLists](https://github.com/danielmiessler/SecLists)
- common used:
  - /path/to/wordlists/dirb/common.txt
  - /path/to/seclists/Discovery/Web-Content/common.txt
- fzf-wordlists
```bash
find /usr/share/seclists /usr/share/wordlists /usr/share/wfuzz /usr/share/dirb -type f | fzf
```

operation:

- [dirb](https://www.kali.org/tools/dirb/)
```bash
dirb "http://$TARGET" /usr/share/seclists/Discovery/Web-Content/common.txt
```
- [ffuf](https://github.com/ffuf/ffuf)
```bash
ffuf -fs 185 -c -w \$(fzf-wordlists) -H 'Host: FUZZ.org' -u "http://$TARGET/"
ffuf -w /usr/share/dirb/wordlists/common.txt -fc 403,404 -fs 185 -u "http://$TARGET/FUZZ" -p 1
```

## DNS

- dig
- nslookup
- whois
```bash
dig axfr mydomain.local @IP_ADRESS
nslookup -type=any $DOMAIN_NAME
whois $DOMAIN_NAME
```

- [theHaverster - OSINT](https://github.com/laramies/theHarvester.git)
  - email
  - subdomain
  - name
```bash
theHarvester -d $DOMAIN_NAME -b google
```

- [Certificate Search](https://crt.sh/)

## CDN

CDN: Content Dilivery Network

- online ping
  - http://ping.chinaz.com/
  - http://ping.aizhan.com/
  - http://ce.cloud.360.cn/
  - https://ip.tool.chinaz.com/
  - https://get-site-ip.com/
  - https://tools.ipip.net/cdn.php/
- no effect
  - sqli
  - xss
- bypass (maybe combined with se)
  - 子域名查询：主站有CDN但是子站没有
  - 邮件服务查询：邮件大部分是内部人员访问，量少无CDN
  - 国外ping出IP地址：企业一般未在国外部署CDN
  - 遗留文件、扫描全网：例如PHPInfo信息中会遗留出IP地址
  - 特殊搜索引擎：fofa, shodan, zoomeye, censys, [谛听](https://www.ditecting.com/index.php/home/Index/index)
  - 工具：fackcdn, w8fuckcdn, zmap
- Usage
  - 获取真实IP之后，更改本地Hosts文件绑定解析内容

## WAF

WAF: Web Application Firewall

- objective
  - 没有识别WAF直接扫描可能导致IP黑名单
  - 识别完具体的WAF可以有针对性的bypass
- recognize WAF
  - [waf00f](https://github.com/EnableSecurity/wafw00f)
  - [identYwaf](https://github.com/stamparm/identywaf)
  - nmap
    - nmap --script=http-waf-fingerprint
    - nmap --script=http-waf-detec
  - 有些Web站点会在GET Header中遗留WAF相关信息

## Web源码

- 目录结构
  - 后台目录
  - 模板目录
  - 数据库目录
  - 数据库配置文件
- 脚本类型
  - asp
  - php
  - jsp
  - java
- 应用分类
  - 门户
  - 电商
  - 论坛
  - 博客
- 其他补充
  - 框架or非框架
  - CMS识别
  - 开源or闭源
  - 源码获取

## Subdomain

- gobuster
```bash
# fzf-wordlists
/usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt
# gobuster
gobuster vhost -u <http://example.com> -w /path/to/wordlist.txt --append-domain -t $THREAD_NUM
```

## 站点搭建

1. 目录型站点（例如，www.xxx.com/bbs）
   - 主站的漏洞
   - 子站的漏洞
2. 端口类站点，shodan扫描
3. 子域名站点（子域名和域名可能不在一个服务器上）
4. 类似域名站点（原有域名弃用，但是还能访问；二级or顶级域名更换，旧域名找到突破口）
   - 社工方式找到相关域名信息
5. 旁注，C段站点（在线工具：https://www.webscan.cc/）
   1. 旁注：同一个服务器上面存在多个站点、但是你要攻击的是A网站由于各种原因不能完成安全测试。就通过测试B网站进入服务器然后在攻击A网站最终实现目的。
   2. C段：不同的服务器上面存在不同的网站，通过扫描发现与你渗透测试的是同一个网段最终拿下服务器、然后通过内网渗透的方式拿下渗透服务器。
6. 搭建软件特征站点
   - 有的网站是借助于第三方的集成搭建工具实现例如：PHPstudy、宝塔等环境这样的集成环境搭建的危害就是泄露了详细的版本信息。
   - phpstudy搭建了之后在默认的站点安装了phpmyadmin有的网站没有做安全性直接可以通过用户名：root密码：root 登录进入

## 资产收集

- GitHub
- 搜集：子域名、DNS、备案、证书、全球节点请求CDN
- 搜索引擎：fofa, shodan, zoomeye

# 2. 漏洞挖掘 Vulnerabilities

## Command Injection

## SQLi

## File Upload

## XSS

## CSRF

## Deserialization

## Payment

## WAF & Bypass

## Code Audit

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

靠山吃山，靠水吃水
- [GTFOBins](https://gtfobins.github.io/)

## 3.0 Shells

- better shell, <u>[*👉🏻GO*](./3.Privilege-Escalation/Linux/Better-Shell.md)</u>
- reverse shell, <u>[*👉🏻GO*](./3.Privilege-Escalation/Linux/Reverse-Shell.md)</u>

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

工具使用, <u>[*👉🏻GO*](./3.Privilege-Escalation/Linux/UsageOfTools.md)</u>

# 4. 后渗透期 Post Pentest


# 5. 对抗攻防 AWD


# 5. 社会工程 Social Engeering


# 6. 软件开发 Software Engeering


# Appendix. 链接

<u>[*👉🏻GO*](./Links.md)</u>

# Appendix. 靶场

- [OSCP](https://docs.google.com/spreadsheets/d/1dwSMIAPIam0PuRBkCiDI88pU3yzrqqHkDtBngUHNCw8/edit#gid=0)
- VulnHub
- HackTheBox
- TryHackMe
- DVWA

# Appendix. 书籍

- Computer Science
  - *CSAPP*
  - *Linux Basics for Hacker*
- Computer Languages
  - Python
    - *Fluent Python*
  - Go
    - *Black Hat Go*
- Pentest
  - *Penetration Testing with Kali Linux*
  - *Kali Linux Penetration Testing Bible*
  - *Google Hacking*
  - *OWASP权威指南*
- Binary
  - *Intel® 64 and IA-32 Architectures Software Developer’s Manual*
  - *The IDA Pro Book*
  - *The Ghidra Book*

# Appendix. 学习资料

- YouTube
  - [ ] [Adversary Emulation with Caldera \| Red Team Series 1-13](https://www.youtube.com/watch?v=Vdd4lRXB7zE&list=PLTnRtjQN5iea6dLA_4i3qFFX0kwvdL0bL)
  - [x] NTUSTISC - Penetration Test: [0x01](https://www.youtube.com/watch?v=D8Usq_BCW2Y), [0x02](https://www.youtube.com/watch?v=9p57TntyqFU)
  - [ ] [Beginner to Advanced Bug Bounty Hunting Course](https://www.youtube.com/watch?v=Rp69edBmFFo)
- Bilibili
  - Vulnerable Environments Practice
    - [ ] [OSCP 推荐靶场](https://space.bilibili.com/102541140/channel/collectiondetail?sid=1397293&ctype=0)
    - [ ] [渗透测试OSCP备考必刷！HACK THE BOX靶机渗透测试](https://space.bilibili.com/353221990/channel/collectiondetail?sid=297479&ctype=0)
  - Linux Privilege Escalation
    - [ ] [Linux提权精讲：原理和枚举](https://www.bilibili.com/video/BV1Wh4y1H7LK)
    - [ ] [Linux提权精讲：演示1 - 服务漏洞利用提权](https://www.bilibili.com/video/BV19s4y1D7Mt)
    - [ ] [Linux提权精讲：演示2 - 20种Linux渗透测试提权演示精讲](https://www.bilibili.com/video/BV1Es4y1M7ZL)
    - [ ] [Linux提权精讲：Sudo风暴全70讲](https://www.bilibili.com/video/BV1DV4y1U7bT)
- Article
  - [ ] [小迪安全](https://www.yuque.com/weiker/xiaodi)
  - [ ] [HackTricks](https://book.hacktricks.xyz/welcome/readme)
  - [ ] [How DNS works](https://howdns.works/)
- Course
  - [ ] [2021 交大程式安全 binary exploit 課程](https://github.com/u1f383/Software-Security-2021-2022)
- Workshop
  - [ ] [pwn.college](https://pwn.college/)
  - [ ] [MADWeb, Workshop on Measurements, Attacks, and Defenses for the Web](https://madweb.work/)
