# Dual boot with macOS

[Offical Guide](https://www.kali.org/docs/installation/dual-boot-kali-with-mac/)

# Installation

- full-tool version

```bash
sudo apt update
sudo apt install -y kali-linux-everything
```

- i3

```bash
sudo apt install kali-desktop-i3
```

- [JetBrains Mono](https://github.com/JetBrains/JetBrainsMono)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/JetBrains/JetBrainsMono/master/install_manual.sh)"
```

- [Fira Code](https://github.com/tonsky/FiraCode)

```bash
sudo apt install fonts-firacode
```

- [Monoid](https://github.com/larsenwork/monoid)

```bash
# /usr/share/fonts, /usr/local/share/fonts, and ~/.fonts
curl -O https://cdn.jsdelivr.net/gh/larsenwork/monoid@2db2d289f4e61010dd3f44e09918d9bb32fb96fd/Monoid.zip
unzip Monoid.zip
cp Monoid-*.ttf ~/.fonts
sudo fc-cache
```