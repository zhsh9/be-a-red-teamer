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

# i3 config

- [Official i3-dotfiles](https://gitlab.com/Arszilla/i3-dotfiles)
- [Customized i3-dotfiles]()

## prl-tools

REFs:
- [prl-tools description](https://git.sr.ht/~dcao/dotfiles/commit/master)
- [Parallels Tools Overview](https://download.parallels.com/desktop/v12/docs/en_US/Parallels%20Desktop%20User's%20Guide/32789.htm)

- prlcc
- prlcp
- prldnd
- prlfsmountd
- prlhosttime
- prlimit
- prlsga
- prl_showvmcfg
- prlshprint
- prlshprof
- prltimesync
- prltoolsd
- prlusmd

Important Changing:
```bash
# Enable parallels desktop tools.
# When on xfce-desktop, run `ps aux | grep prl`:
##/usr/bin/prlcc
##/usr/bin/prlcp
##/usr/bin/prldnd
##/usr/bin/prlsga
##/usr/bin/prlsshprof
##/usr/bin/prltimesync
##/usr/bin/prlusmd
##/usr/bin/prltoolsd -p /var/run/prltoolsd.pid
# So, we know xfce executes some tools inside /usr/bin, like /usr/bin/prl*
# Do the same thing on i3.
# /home/kali/.config/i3/config.d/execs.conf

## (1) Start vmware-user-suid-wrapper to enable copy/paste between host and guest: (on VMware)
exec --no-startup-id /usr/bin/vmware-user-suid-wrapper

## (2) Start vmware-user-suid-wrapper to enable copy/paste between host and guest: (on Parallels)
###Some toosl are disabled, because not knowing what these tools are used for.
###Parallels Desktop
exec --no-startup-id /usr/bin/prltoolsd -f -p /var/run/prltoolsd.pid
#exec --no-startup-id /usr/bin/prlcc
#exec --no-startup-id /usr/bin/prldnd
exec --no-startup-id /usr/bin/prlcp
#exec --no-startup-id /usr/bin/prlsga
#exec --no-startup-id /usr/bin/prlsshprof
#exec --no-startup-id /usr/bin/prltimesync
#exec --no-startup-id /usr/bin/prlusmd
```