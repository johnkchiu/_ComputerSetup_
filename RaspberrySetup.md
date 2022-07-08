# Setup for Raspberry P

## fish shell
```shell
sudo apt-get install fish
chsh -s $(which fish)
# install fisher + fzf (using fish shell)
curl -sL https://git.io/fisher | source && fisher install jorgebucaran/fisher
sudo apt-get install fzf
fisher install jethrokuan/fzf
```

## mount nfs / samba
```shell
# manually for nfs
sudo mkdir /mnt/Shared
sudo mount -t nfs 10.10.0.10:/Shared /mnt/Shared

# automatically for nfs
sudo mkdir /mnt/Shared
sudo vi /etc/fstab
# <file system> <dir> <type> <options> <dump> <pass>
# 10.10.0.10:/Shared /mnt/Shared nfs defaults 0 0
sudo mount -a

# manual mount for samba/cifs
sudo mkdir /mnt/Shared
# uid=$(id =u)
# gid=$(id -g)
sudo mount -t cifs -o username=user,password=password,uid=1000,gid=1000,file_mode=0777,dir_mode=0777,vers=2.0 //10.10.0.10/Shared /mnt/Shared

# automatically for samba/cifs
sudo mkdir /mnt/Shared
sudo vi /etc/fstab
# <file system> <dir> <type> <options> <dump> <pass>
# //10.10.0.10/Shared /mnt/Shared cifs username=user,password=password,uid=1000,gid=1000,file_mode=0777,dir_mode=0777,vers=2.0 0 0
sudo mount -a
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

## transmission
```shell
sudo apt install transmission-daemon

# edit configs
sudo systemctl stop transmission-daemon
sudo vi /etc/transmission-daemon/settings.json
# blocklist-url = http://list.iblocklist.com/?list=bt_level1
# rpc-authentication-required = false

# add permissions (user == pi)
sudo usermod -aG debian-transmission pi
sudo systemctl daemon-reload

# change 

# start
sudo systemctl start transmission-daemon

```

## vnc server (RealVNC)
```shell
sudo raspi-config
# enable "Interfacing Options" -> "VNC" 
# set "Advanced Options" -> "Resolution" to "1920x1080"
# reboot
```

## dig
```shell
sudo apt-get install dnsutils
# check for external ip
dig +short myip.opendns.com @resolver1.opendns.com
```

