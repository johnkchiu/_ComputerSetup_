# Setup for Raspberry P

## fish shell
```shell
sudo apt-get install fish
chsh -s $(which fish)

```

# mount nfs
```shell
# manually
sudo mkdir /var/backups
sudo mount -t nfs 10.10.0.10:/backups /var/backups

# automatically
sudo mkdir /var/backups
sudo vi /etc/fstab
# <file system>       <dir>         <type>   <options>   <dump> <pass>
# 10.10.0.10:/backups /var/backups  nfs      defaults    0      0\
sudo mount /var/backups
```

## openvpn
```shell
sudo apt-get install openvpn
sudo cd /etc/openvpn
sudo cp [*.ovpn] .
# start
sudo openvpn --config [*.ovpn] --daemon
# shutdown
sudo killall -SIGINT openvpn
```

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

## zsh / oh-my-zsh
```shell
sudo apt-get update # optional
sudo apt-get install zsh
chsh -s $(which zsh)
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
