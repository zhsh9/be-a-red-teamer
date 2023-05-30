# SUID

- SUID = Set User ID
- 出现在文件拥有者的执行位上，like `ls -l: -r-sr-xr-x`
- 执行时让使用者暂时获得文件拥有者的权限
- 查询SUID可执行文件
  - `find / -perm -u=s -type f 2>/dev/null`