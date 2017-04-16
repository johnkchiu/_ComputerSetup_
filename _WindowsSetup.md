# Setup for Windows Cmd

## Chocolatey
```shell
# Run as Admin
@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

## git
```shell
# Run as Admin
choco install git
```

# Setup for Windows Bash

## git
```shell
sudo apt-get install git
```

## zsh + oh-my-zsh + antigen
```shell
# zsh
sudo apt-get install zsh
# setup zsh as shell
vi ~/.bashrc
# Add following to start
# -------------------------
# if [ -t 1 ]; then
#     exec zsh
# fi
# -------------------------
# oh-my-zsh - http://ohmyz.sh/
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
# antigen
curl -L git.io/antigen > .antigen.zsh
# Setup .zshrc, .antigenrc, .personal, etc
```

## node.js / npm / nvm
```shell
# install nvm
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
# setup nvm path
vi ~/.zshrc
# Add the follow to end
# -------------------------
# export NVM_DIR="$HOME/.nvm"
# [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
# nvm use --silent node
# -------------------------
# install latest node.js
nvm install node
```
