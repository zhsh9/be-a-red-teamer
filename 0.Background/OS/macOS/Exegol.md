# Installation

Refs:
- [Official Document](https://exegol.readthedocs.io/)

```bash
# 1. install pre-requisites.
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew install git
brew install --cask docker
brew install --cask miniconda # brew install --cask anaconda
brew install --cask xquartz

# 2. config xquatz and docker.
# The XQuartz config Allow connections from network clients must be set to true
# Docker Desktop must be configured with default File Sharing (see screenshot below)
#   /tmp, /Users, /Volumes, /private, /var/folders

# 3. install exegol and add it into PATH.
python3 -m pip install exegol
## Using Exegol auto-completion.
## fish
register-python-argcomplete --no-defaults --shell fish exegol | source
register-python-argcomplete --no-defaults --shell fish exegol > ~/.config/fish/completions/exegol.fish
## zsh
##   activate:
autoload -U bashcompinit
bashcompinit
##   enable completion by adding the following command in ~/.zshrc config:
eval "$(register-python-argcomplete --no-defaults exegol)" >> ~/.zshrc
## bash
##   add the following command in ~/.bashrc config:
eval "$(register-python-argcomplete --no-defaults exegol)" >> ~/.bashrc
```

# Usage

Wrapper actions:
- install
    ```bash
    exegol install
    exegol install full
    exegol install myimage
    #Build the myimage image based on the full profile and log the operation
    exegol install myimage full --build-log "/tmp/build.log"
    ```
- start
    ```bash
    # Start interactively a container
    exegol start
    # Create a demo container using full image
    exegol start demo full
    # Spawn a shell from demo container
    exegol start demo
    # Create a container test with a custom shared workspace
    exegol start test full -w "./project/pentest/"
    # Create a container test sharing the current working directory
    exegol start test full -cwd
    # Create a container htb with a VPN
    exegol start htb full --vpn "~/vpn/lab_Dramelac.ovpn"
    # Create a container app with custom volume
    exegol start app full -V "/var/app/:/app/"
    # Get a shell based on tmux
    exegol start --shell tmux
    ```
- info
- exec
- update
- stop
- restart
- remove
- uninstall
- version
    ```bash
    exegol version -vvv
    ```