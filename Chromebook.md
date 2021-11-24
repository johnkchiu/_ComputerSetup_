# Setup for Chromebook 

## fish shell
```shell
sudo apt-get install fish
sudo chsh -s $(which fish) $(whoami)
# install fisher + fzf
curl -sL https://git.io/fisher | source && fisher install jorgebucaran/fisher
sudo apt-get install fzf
fisher install jethrokuan/fzf
```

## Visual Studio Code
```shell
sudo apt-get update
sudo apt-get install -y gnome-keyring
# download correct deb pkg via https://code.visualstudio.com/download
dpkg --print-architecture
```

## KeePassXC
```shell
sudo apt-get install keepassxc
```