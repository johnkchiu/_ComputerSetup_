# Setup for asuswrt-merlin
https://github.com/RMerl/asuswrt-merlin

## General Setup
* Force AiMesh Wired (Network Map -> AiMesh Node -> (Select Node) -> More COnfig -> Connection Priority => Ethernet)
* Enable SSH (Administration -> System -> Enable SSH => Yes)
* Set Timezone (Administration -> System -> Time Zone)
* Custom DNS via Google DNS (WAN -> Internet Connection -> WAN DNS Setting)
  * Connect to DNS Server automatically => No
  * DNS Server1 => 8.8.8.8
  * DNS Server => 8.8.4.4
  * DNS Privacy Protocol => DNS-over-TLS (DOT)
  * Preset servers: Google 8.8.8.8, Google 8.8.4.4

### Entware
```bash
# ssh to router
entware-setup.sh
```

### Git
Create `$HOME/.gitssh.sh` file
```bash
#!/bin/sh
dbclient -y -i ~/.ssh/id_rsa $*
```

```bash
# install via entware
opkg install git
# create ssh keys
dropbearkey -t rsa -f "~/.ssh/id_rsa"
dropbearkey -y -f "~/.ssh/id_rsa" | grep "^ssh-rsa " > "~/.ssh/id_rsa.pub"
# export GIT_SSH
export GIT_SSH=$HOME/.gitssh.sh
```

### Fish shell
Create `/jffs/configs/profile.add`
```bash
[ -f /opt/bin/fish ] && exec /opt/bin/fish
```

```bash
# install fish
opkg install fish bc
```

### Transmission
```bash
# install packages
opkg install transmission-web transmission-daemon-openssl
opkg install ca-bundle ca-certificates

# stop and modify configs
/opt/etc/init.d/S88transmission stop
vi /opt/etc/transmission/settings.json
```

Create `/jffs/scripts/firewall-start`
```bash
#!/bin/sh
iptables -I INPUT -p tcp --destination-port 51413 -j ACCEPT
iptables -I INPUT -p udp --destination-port 51413 -j ACCEPT
```

```bash
/jffs/scripts/firewall-start
/opt/etc/init.d/S88transmission start
```

### Duck DNS
* Enable custom scripts (Administration -> System -> Enable JFFS custom scripts and configs	=> Yes)
* Create `/jffs/scripts/ddns-start` using sample [Duck DNS Sample script](https://github.com/RMerl/asuswrt-merlin/wiki/DDNS-Sample-Scripts#duck-dns)
* Set DDNS to custom (WAN -> DDNS -> DDNS Service -> Server => Customer)
