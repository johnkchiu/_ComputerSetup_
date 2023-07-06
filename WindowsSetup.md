# Setup for Windows
## Windows Apps

### Chocolatey

```bash
# Install via Windows PowerShell as Admin
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

### Windows PowerShell
```bash
# run PowerShell as admin
# install starship
choco install starship
# setup PowerShell config
Set-ExecutionPolicy RemoteSigned -scope CurrentUser
code $PROFILE
# add 'Invoke-Expression (&starship init powershell)'
```

### Git for Windows
```bash
winget install --id Git.Git
```


## Ubuntu on Windows Subsystem for Linux (WSL 2)

### Ubuntu Install
# Install via Windows PowerShell as Admin
```bash
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

