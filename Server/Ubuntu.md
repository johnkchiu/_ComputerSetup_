# Setup for Ubuntu Server

### Add user
```bash
# add user
sudo adduser new_user
# add user to sudo group
sudo adduser new_user sudo
# add user to docker group
sudo usermod -aG docker $USER
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

### Install Chrome
```bash
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo apt install ./google-chrome*.deb
```
