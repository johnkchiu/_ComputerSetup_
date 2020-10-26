# Setup for Windows
## Windows Apps

### Chocolatey
```shell
# Install via Windows PowerShell as Admin
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

### Android
```shell
# ANDROID_HOME = C:\Users\johnkchiu\AppData\Local\Android\Sdk

# Setup for Windows Subsystem for Linux (Ubuntu)

## Install Windows Subsystem for Linux (WSL)
* https://docs.microsoft.com/en-us/windows/wsl/install-win10
```

### Visual Studio Code (cli)
```shell
sudo ln -s "/mnt/c/Users/$USER/AppData/Local/Programs/Microsoft VS Code/Code.exe" /usr/local/bin/code
```

## Ubuntu on Windows Subsystem for Linux (WSL 2)

### Ubuntu Install
1. Open PowerShell as an Administrator and run:
    ```
    dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
    wsl --set-default-version 2
    ```
1. Install Ubuntu via [Windows Store](https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6)

### Ubuntu update / upgrade
```
sudo apt-get update
sudo apt-get upgrade
sudo apt dist-upgrade
do-release-upgrade -d
```

### fish (shell)
```shell
# install fish
sudo apt-add-repository ppa:fish-shell/release-3
sudo apt-get update
sudo apt-get install fish
# install fisher (package manager)
curl https://git.io/fisher --create-dirs -sLo ~/.config/fish/functions/fisher.fish
sudo apt install fzf
fisher add jethrokuan/fzf
# change default shell
chsh -s /usr/bin/fish
```

### java
```bash
# requires zip
sudo apt-get install zip unzip
# install sdkman for fish
fisher add reitzig/sdkman-for-fish@v1.4.0
# install java (will prompt to install sdkman)
sdk install java
```

### git
```shell
sudo apt install git
```

### zsh + oh-my-zsh + antigen
```shell
# zsh
sudo apt-get install zsh

# oh-my-zsh - http://ohmyz.sh/
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

# antigen
curl -L git.io/antigen > .antigen.zsh
# Setup .zshrc, .antigenrc, .personal, etc
```

### node.js / npm / nvm
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
