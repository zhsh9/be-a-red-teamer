# 如何修改Windows的DNS文件

Hosts文件的作用：

- hosts文件是一个用于储存计算机网络中各节点信息的计算机文件
- 将一些常用的网址域名与其对应的IP地址建立一个关联“数据库”，当用户在浏览器中输入一个需要登录的网址时，系统会首先自动从Hosts文件中寻找对应的IP地址
- 加快域名解析
- 构建映射关系
- 屏蔽网站or广告
- 调试和测试

更改Windows下Hosts文件的操作步骤：

1. Hosts文件所在地址：C:\Windows\System32\drivers\etc
2. 修改后需刷新DNS缓存：
   - ipconfig/flushdns on cmd
