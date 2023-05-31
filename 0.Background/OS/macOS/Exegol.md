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
- info
- exec
- update
- stop
- restart
- remove
- uninstall
- version