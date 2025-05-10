# Setup for Ubuntu

## Development Tools

### curl
```bash
sudo snap install curl
```

### git
```bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt update; sudo apt install git
```

### Visual Studio Code
```bash
sudo snap install --classic code
```

### fish + fzf + eza + starship
```bash
sudo apt-get install fish
chsh -s /usr/bin/fish
# install fisher + fzf
curl -sL https://raw.githubusercontent.com/jorgebucaran/fisher/main/functions/fisher.fish | source && fisher install jorgebucaran/fisher
sudo apt install fzf
fisher install jethrokuan/fzf
# install eza
sudo apt install -y eza
# install starship
curl -sS https://starship.rs/install.sh | sh
```

### Nerd Font (Caskaydia Cove Nerd Font)
```bash
mkdir ~/.local/share/fonts
cd ~/.local/share/fonts 
wget https://github.com/ryanoasis/nerd-fonts/releases/download/v3.3.0/CascadiaCode.zip
unzip CascadiaCode.zip 
rm CascadiaCode.zip 
fc-cache -fv
```

### Docker
```bash
# Follow instructions from https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository

# Add Docker's official GPG key: (Run in bash)
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

# Install
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### mount nfs / samba
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

### openvpn
```shell
# copy ovpn file to /etc/openvpn/client
sudo cp [*.vpn] /etc/openvpn/client
# start
sudo openvpn --config /etc/openvpn/client/[*.ovpn] --daemon
# shutdown
sudo killall -SIGINT openvpn
```

### transmission (via Docker)
```shell
# see https://hub.docker.com/r/linuxserver/transmission
sudo docker run -d \
  --name=transmission \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=America/Los_Angeles \
  -p 9091:9091 \
  -p 51413:51413 \
  -p 51413:51413/udp \
  -v /mnt/Shared/downloads:/downloads \
  --restart unless-stopped \
  lscr.io/linuxserver/transmission:latest
# Go to https://<host>:9091 and edit configs
# 1. Remove "complete" from Download to.
# 2. Turn off: Use temporary folder
# 3. Stop seeding at ratio: 0.0001
# 4. Enable blocklist - http://list.iblocklist.com/?list=bt_level1

# stop 
sudo docker stop transmission
```

### Enable sudo for Remote Desktop (rdp)
```bash
sudo tee /etc/polkit-1/rules.d/50-allow-remote-admin.rules << EOF
polkit.addRule(function(action, subject) {
  if (subject.isInGroup("sudo")) {
    return polkit.Result.AUTH_ADMIN_KEEP;
  }
});
EOF
```

### Enable "Allow Locked Remote Desktop" Gnome Extension
1. Install Chrome Extension - [GNOME Shell integration](https://chromewebstore.google.com/detail/gnome-shell-integration/gphhapmejobijbbhgpjhcjognlahblep).
1. Install the GNOME Shell Host Connector
    ```
    # On Ubuntu 23.04 or newer
    sudo apt install gnome-browser-connector
    ```
1. Enable Gnome Extension - [Allow Locked Remote Desktop](https://extensions.gnome.org/extension/4338/allow-locked-remote-desktop/)
1. Open https://extensions.gnome.org/local/ to see installed Gnome Extensions.


### Enable ssh server
```bash
# install openssh-server
sudo apt install openssh-server
# Enable via Settings -> System -> Secure Shell
```