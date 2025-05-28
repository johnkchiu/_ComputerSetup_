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

### Install Pangolin
```bash
# follow https://docs.fossorial.io/Getting%20Started/quick-install instructions
wget -O installer "https://github.com/fosrl/pangolin/releases/download/1.4.0/installer_linux_$(uname -m | sed 's/x86_64/amd64/;s/aarch64/arm64/')" && chmod +x ./installer
# as root user
./installer

# configure resource and run newt on resource, example:
docker run -d --restart unless-stopped fosrl/newt --id <id> --secret <secret> --endpoint <endpoint>
```

### Portainer (via Docker)
```bash
# create volume
docker volume create portainer_data
# install 
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:lts
```

### Apache Guacamole (via Docker)
Follow guide from https://krdesigns.com/articles/how-to-install-guacamole-using-docker-step-by-step and https://guacamole.apache.org/doc/gug/guacamole-docker.html
```bash
# get latest
docker pull guacamole/guacamole
docker pull guacamole/guacd
docker pull mariadb

# generate db config
docker run --rm guacamole/guacamole /opt/guacamole/bin/initdb.sh --mysql > initdb.sql

# create docker-compose.yml (partial), start db container, and init db
docker compose up -d
docker cp initdb.sql guacamoledb:/initdb.sql
docker exec -it guacamoledb bash
cat /initdb.sql | mysql -u root -p guacamole_db
exit

# stop db container
docker compose down

```

`docker-compose.yml` (partial with DB only)
```yaml
version: '3'
services:
  guacdb:
    container_name: guacamoledb
    image: mariadb
    restart: unless-stopped
    environment:
      MYSQL_ROOT_PASSWORD: 'MariaDBRootPass'
      MYSQL_DATABASE: 'guacamole_db'
      MYSQL_USER: 'guacamole_user'
      MYSQL_PASSWORD: 'MariaDBUserPass'
    volumes:
      - './db-data:/var/lib/mysql'
volumes:
  db-data:
```

`docker-compose.yml` (complete)
```yaml
version: '3'
services:
  guacdb:
    container_name: guacamoledb
    image: mariadb
    restart: unless-stopped
    environment:
      MYSQL_ROOT_PASSWORD: 'MariaDBRootPass'
      MYSQL_DATABASE: 'guacamole_db'
      MYSQL_USER: 'guacamole_user'
      MYSQL_PASSWORD: 'MariaDBUserPass'
    volumes:
      - './db-data:/var/lib/mysql'
  guacd:
    container_name: guacd
    image: guacamole/guacd
    restart: unless-stopped
  guacamole:
    container_name: guacamole
    image: guacamole/guacamole
    restart: unless-stopped
    ports:
      - 8080:8080
    environment:
      GUACD_HOSTNAME: "guacd"
      MYSQL_HOSTNAME: "guacdb"
      MYSQL_DATABASE: "guacamole_db"
      MYSQL_USER: "guacamole_user"
      MYSQL_PASSWORD: "MariaDBUserPass"
      TOTP_ENABLED: "true"
    depends_on:
      - guacdb
      - guacd
volumes:
  db-data:
```
