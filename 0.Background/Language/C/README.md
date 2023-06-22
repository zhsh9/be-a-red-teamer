# Reference

...

# Standard C edition

1. 1978, K&R
2. 1989, C88/C90
3. 1999, C99
4. 2011, C11

# Compiler

- gcc/g++
- msvc

# A binary program

```bash
# 预处理
gcc -E a.c -o a.i
# 编译
gcc -S a.i -o a.s
# 汇编
gcc -c a.s -o a.o
# 链接
gcc a.o -o a.out
```

# Main function

```c
int main();

int main(int argc, char* argv[]);
int main(int argc, char** argv);

int main(int argc, char* argv[], char* envp[]);
int main(int agrc, char** argv, char** envp);
```

# 进制和位

进制：

- bianry
- octal
- decimal
- heximal

位：

- bit, 1
- byte, 8
- word, 16
- dword, 32
- fword, 48
- qword, 64

# 基本数据类型

1. 整数
   - short, 2B
   - int, 4B
   - long, 4B(x86) 8B(x64)
   - long long, 8B
2. 浮点数
   - float, 4B
   - double, 8B
3. 字符 字符串
   - char, 1B
   - wchar_t, 2B
4. 结构
   - struct
   - union
   - enum
5. 特殊类型
   - auto
   - void
   - []
   - *
6. 类型修饰
  - static
  - signed
  - unsigned
  - const