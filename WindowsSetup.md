# Setup for Windows

## Windows Apps

### Chocolatey
```shell
# Install with cmd.exe as Admin
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
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
## Ubuntu on Windows Subsystem for Linux (WSL)
1. Install Ubuntu via [Windows Store](https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6)
1. Open PowerShell as an Administrator and run:
    ```
    Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform
    ```

### fish (shell)
```shell
sudo apt-add-repository ppa:fish-shell/release-3
sudo apt-get update
sudo apt-get install fish
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
