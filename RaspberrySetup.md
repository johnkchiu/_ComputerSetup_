# Setup for Raspberry Pi

## ssh
```shell
sudo raspi-config
# enable "Interfacing Options" -> "SSH" 
```

## vnc server (RealVNC)
```shell
sudo raspi-config
# enable "Interfacing Options" -> "VNC" 
# set "Advanced Options" -> "Resolution" to "1920x1080"
# reboot
```

## fish shell
```shell
sudo apt-get install fish
chsh -s $(which fish)

```

## zsh / oh-my-zsh
```shell
sudo apt-get update # optional
sudo apt-get install zsh
chsh -s $(which zsh)
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
