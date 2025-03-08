# Setup for Windows

## Windows Apps

### Windows PowerShell
```bash
# install latest PowerShell
winget install --id Microsoft.PowerShell
# install starship
winget install --id Starship.Starship
# setup PowerShell config
Set-ExecutionPolicy RemoteSigned -scope CurrentUser
code $PROFILE
# add 'Invoke-Expression (&starship init powershell)'
```

### Git for Windows
```bash
winget install --id Git.Git
```

### Android Studio
```bash
winget install --id=Google.AndroidStudio
```

## Android

## Google Play Games on PC Developer Emulator 
```bash
# Install Google Play Games (Developer Emulator Beta) via https://developer.android.com/games/playgames/emulator
# Install Google Platform Tools (adb)
winget install Google.PlatformTools 
```

## Ubuntu on Windows Subsystem for Linux (WSL2)

### Ubuntu install
```bash
# Install via Windows PowerShell as Admin
wsl --install
# Needs to restart
```

### Ubuntu update / upgrade
```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt dist-upgrade
do-release-upgrade -d
```

### fish (shell)
```bash
# install fish
sudo apt-add-repository ppa:fish-shell/release-3
sudo apt-get update
sudo apt-get install fish
# install peco
sudo apt install peco
# install exa (via CRust's cargo)
sudo apt install cargo
cargo install exa
# install starship
curl -sS https://starship.rs/install.sh | sh
# install fisher (package manager)
fish
curl https://git.io/fisher --create-dirs -sLo ~/.config/fish/functions/fisher.fish
sudo apt install fzf
fisher install jethrokuan/fzf
# change default shell
chsh -s /usr/bin/fish
```

### java
```bash
# requires zip
sudo apt-get install zip unzip
# install sdkman for fish
fisher install reitzig/sdkman-for-fish@v1.4.0
# install sdkman
sdk
# install java (restart terminal)
sdk install java
```

### git
```bash
sudo apt install git
```

### node.js / npm / nvm
```bash
# install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
# (for fish)
fisher install FabioAntunes/fish-nvm
fisher install edc/bass
# install latest node.js
nvm install node
```

### python
```bash
# python3 already installed
sudo apt install -y python3-pip
fish_add_path -m ~/.local/bin
```

### rust
```bash
# install rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
# for fish shell, add:
# fish_add_path $HOME/.cargo/bin
```

### Android
```bash
sudo apt-get install android-tools-adb
```

### aws-cli
```bash
#  install aws-cli
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```
