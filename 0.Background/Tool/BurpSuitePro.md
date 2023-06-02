# BurpSuite Pro Init

- [BurpSuite Pro Download]()
- [Burp Loader Keygen](https://github.com/h3110w0r1d-y/BurpLoaderKeygen)
- [MacOS安装破解 BurpSuite 2023.4.2【持续更新】](https://www.lzskyline.com/index.php/archives/121/)

# Linux

Config BurpSuite Pro 2023.5.2 on Kali Linux 2023.2

```bash
curl -O https://github.com/h3110w0r1d-y/BurpLoaderKeygen/releases/download/1.14/BurpLoaderKeygen.jar
java -jar ./BurpLoaderKeygen.jar
```

Create and change ~/BurpSuitePro/user.vmoptions
```
-Xmx1024m
--add-opens=java.base/java.lang=ALL-UNNAMED
--add-opens=java.base/jdk.internal.org.objectweb.asm=ALL-UNNAMED
--add-opens=java.base/jdk.internal.org.objectweb.asm.tree=ALL-UNNAMED
--add-opens=java.base/jdk.internal.org.objectweb.asm.Opcodes=ALL-UNNAMED
-javaagent:BurpLoaderKeygen.jar
-noverify
```

# macOS