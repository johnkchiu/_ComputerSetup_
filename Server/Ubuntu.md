# Setup for Ubuntu Server

### Add user
```bash
# add user
sudo adduser new_user
# add user to Sudo group
sudo adduser new_user sudo
```

### Enable Remote Desktop
```bash
# update server:
sudo apt-get update -y
# install xrdp 
sudo apt-get install xrdp -y
# install Xfce display manager
sudo apt install xfce4 xfce4-goodies xorg dbus-x11 x11-xserver-utils
```