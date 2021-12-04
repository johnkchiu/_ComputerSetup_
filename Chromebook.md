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

### java / scala / sbt / gradle / groovy / kotlin
```bash
# install zip
sudo apt-get install zip
# install sdkman + modify .bashrc/.zshrc
curl -s "https://get.sdkman.io" | bash
# (for fish)
fisher install reitzig/sdkman-for-fish
# install java
sdk install java
# install gradle
sdk install gradle
# install kotlin
sdk install kotlin
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