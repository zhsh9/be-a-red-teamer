Online Refs:
- [https://www.gnu.org/software/findutils/](https://www.gnu.org/software/findutils/)
- [https://www.gnu.org/software/findutils/manual/html_mono/find.html](https://www.gnu.org/software/findutils/manual/html_mono/find.html)

Common Usage:
```bash
find / -perm -type f -u=s 2>/dev/null

find . -type f -name "*" | xargs grep "192.168.1.1"

find . -name ".txt" -o -name ".log"

find . -regex ".*\(\.txt\|\.log\)$"
find . -iregex ".*\(\.txt\|\.log\)$"

find . ! -name "*.log"

find . -type f -atime -10
find . -type f -atime +10

find . -type f -name "*.txt" -atime +10 -delete

find . -type f -perm 777
find . -type f -user zhsh9
find . -type f -group zhsh9

find . -type f -user root -exec chown zhsh9 {} \;
find . -name "*.log" -exec rm {} \;
find . -name "*.log" -exec cat {} \; > /zhsh9.log
find . -name "*.log" -exec printf "File: %s\n" {} \;

find . -type f -size +500M -print0 | xargs -0 ls -l
find . -type f -size +500M -print0 | xargs -0 du -h | sort -nr

find . -type f -print0 | xargs -0 du -h | sort -rh | head -n 5
```

Manual:
```bash
man 1 find
```

```
$ find --help
Usage: find [-H] [-L] [-P] [-Olevel] [-D debugopts] [path...] [expression]

Default path is the current directory; default expression is -print.
Expression may consist of: operators, options, tests, and actions.

Operators (decreasing precedence; -and is implicit where no others are given):
      ( EXPR )   ! EXPR   -not EXPR   EXPR1 -a EXPR2   EXPR1 -and EXPR2
      EXPR1 -o EXPR2   EXPR1 -or EXPR2   EXPR1 , EXPR2

Positional options (always true):
      -daystart -follow -nowarn -regextype -warn

Normal options (always true, specified before other expressions):
      -depth -files0-from FILE -maxdepth LEVELS -mindepth LEVELS
      -mount -noleaf -xdev -ignore_readdir_race -noignore_readdir_race

Tests (N can be +N or -N or N):
      -amin N -anewer FILE -atime N -cmin N -cnewer FILE -context CONTEXT
      -ctime N -empty -false -fstype TYPE -gid N -group NAME -ilname PATTERN
      -iname PATTERN -inum N -iwholename PATTERN -iregex PATTERN
      -links N -lname PATTERN -mmin N -mtime N -name PATTERN -newer FILE
      -nouser -nogroup -path PATTERN -perm [-/]MODE -regex PATTERN
      -readable -writable -executable
      -wholename PATTERN -size N[bcwkMG] -true -type [bcdpflsD] -uid N
      -used N -user NAME -xtype [bcdpfls]

Actions:
      -delete -print0 -printf FORMAT -fprintf FILE FORMAT -print
      -fprint0 FILE -fprint FILE -ls -fls FILE -prune -quit
      -exec COMMAND ; -exec COMMAND {} + -ok COMMAND ;
      -execdir COMMAND ; -execdir COMMAND {} + -okdir COMMAND ;

Other common options:
      --help                   display this help and exit
      --version                output version information and exit

Valid arguments for -D:
exec, opt, rates, search, stat, time, tree, all, help
Use '-D help' for a description of the options, or see find(1)

Please see also the documentation at https://www.gnu.org/software/findutils/.
```

Backgroud:
- Linux file type
```
f # 普通文件：进行编辑、查看等
l # 软连接：约等于快捷方式
d # 目录：文件夹
c # 字符设备：所有IO设备（键盘、鼠标、显示器等）
b # 块设备：所有存储设备（磁盘、光盘、U盘等）
s # 套接字：进程间通信的一种方式
p # 管道：进程间通信的一种方式
```
- Linux timestamp
```
访问时间(-atime, -amin): 文件最后一次被访问的时间
修改时间(-mtime, -mmin): 文件最后一次被修改的时间
变化时间(-ctime, -cmin): 文件最后一次元数据被修改的时间
```