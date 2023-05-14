# Setup for asuswrt-merlin
https://github.com/RMerl/asuswrt-merlin

## General Setup
* Router Host Name (LAN -> LAN IP -> Host Name)
* Router IP Address (LAN -> LAN IP -> IP Address => 192.168.1.1)
* DHCP IP Pool Address (LAN -> DHCP Server -> IP Pool Starting Address => 192.168.1.21)
* Ethernet Backhual Mode (AiMesh -> System Settings -> Ethernet Backhual Mode => On)
* Enable SSH (Administration -> System -> Enable SSH => LAN Only)
* Set Timezone (Administration -> System -> Time Zone)
* Custom DNS (WAN -> Internet Connection -> WAN DNS Setting)
  * DNS Server -> Assign:
    * DNS Server1 => 1.1.1.1
    * DNS Server3 => 8.8.8.8
  * DNS Privacy Protocol => DNS-over-TLS (DOT)
  * Preset servers: Cloudflare 1 (1.1.1.1 cloudfare-dns.com), Google 1 (8.8.8.8 dns.google)

### Format USB Drive

See [Disk formatting](https://github.com/RMerl/asuswrt-merlin.ng/wiki/Disk-formatting) instructions.

* Less than 2 TB drive, use [amtm](https://diversion.ch/amtm.html).
* Greater than 2 TB drive
  1. Plug USB drive to Linux computer (e.g Raspberry Pi), and `fdisk` to GPT partition like [Repartition disk](https://github.com/RMerl/asuswrt-merlin.ng/wiki/Disk-formatting#7-repartition-disk) instructions.
  2. Plug USB drive to router, and format like [Format and adjust filesystem features](https://github.com/RMerl/asuswrt-merlin.ng/wiki/Disk-formatting#8-format-and-adjust-filesystem-features) instructions.

### USB Application

* Samba - Simpler share naming (USB Application -> Network Place (Samba) -> Simpler share naming ==> Yes )

### Create Swap file

Use [amtm](https://diversion.ch/amtm.html).

### Entware

Use [amtm](https://diversion.ch/amtm.html).

### Diversion, uiDivStats

* Use [amtm](https://diversion.ch/amtm.html) to install Diversion.
* Use custom hosted [allowlist](https://raw.githubusercontent.com/johnkchiu/allowlist/master/domains/_full-list.txt).
* Use [amtm](https://diversion.ch/amtm.html) to install uiDivStats.

### Git
Create `$HOME/.gitssh.sh` file
```bash
#!/bin/sh
dbclient -y -i ~/.ssh/id_rsa $*
```

```bash
# install via entware
opkg install git
opkg install git-http
# create ssh keys
dropbearkey -t rsa -f ~/.ssh/id_rsa
dropbearkey -y -f ~/.ssh/id_rsa | grep "^ssh-rsa " > ~/.ssh/id_rsa.pub
# export GIT_SSH
export GIT_SSH=$HOME/.gitssh.sh
```

### Fish shell
```bash
# install fish
opkg install fish bc
curl https://git.io/fisher --create-dirs -sLo ~/.config/fish/functions/fisher.fish
```

Create `/jffs/configs/profile.add`
```bash
[ -f /opt/bin/fish ] && exec /opt/bin/fish
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
* Create `/jffs/scripts/ddns-start` using sample [Duck DNS Sample script](https://github.com/RMerl/asuswrt-merlin.ng/wiki/DDNS-Sample-Scripts#duck-dns)
* Set DDNS to custom (WAN -> DDNS -> DDNS Service -> Server => Custom)

### Enable Samba Share / Cloud Disk
* USB Application -> Network Place (Samba) Share / Cloud Disk:
  * Enable Shared => On
  * Turn off Simpler share naming *(without the disk name)* => Yes
	
