# Setup for Self Hosting


### Pangolin
```bash
# follow https://docs.fossorial.io/Getting%20Started/quick-install instructions
wget -O installer "https://github.com/fosrl/pangolin/releases/download/1.4.0/installer_linux_$(uname -m | sed 's/x86_64/amd64/;s/aarch64/arm64/')" && chmod +x ./installer
# as root user
./installer

# configure resource and run newt on resource, example:
docker run -d --restart unless-stopped fosrl/newt --id <id> --secret <secret> --endpoint <endpoint>
```

#### Update Pangolin
See https://docs.pangolin.net/self-host/how-to-update
```bash
# Shutdown
sudo docker compose down

# Backup
sudo cp -a config config.backup.`date "+%Y.%m.%d"`
cp docker-compose.yml docker-compose.yml.backup.`date "+%Y.%m.%d"`

# Edit your docker-compose.yml
wget https://raw.githubusercontent.com/fosrl/pangolin/refs/heads/main/docker-compose.example.yml
diff docker-compose.yml docker-compose.example.yml
# Increase version #'s by minor version (e.g. X.X)
sudo docker compose pull
sudo docker compose up -d

# Verify logs
sudo docker compose logs -f

# Clean up images
sudo docker image prune -a
```

### Portainer (via Docker)
```bash
# create volume
docker volume create portainer_data
# install 
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:lts
```

#### Update Portainer (via Docker)
See https://docs.portainer.io/start/upgrade
```bash
# Stop, update, and run
docker stop portainer
docker rm portainer
docker pull portainer/portainer-ce:lts
docker run -d -p 8000:8000 -p 9443:9443 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:lts

# Clean up images
sudo docker image prune -a
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

# update docker-compose.yml (complete), start quacd & guacamole
docker compose up -d
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


### Home Assistant (via Docker)
See https://www.home-assistant.io/installation/linux/#docker-compose
```bash
# Create docker-compose.yml and run
docker compose up -d

# Edit configuration.yaml for Pangolin forward-proxy

# Allows proxy traffic from Pangolin-Newt.  See Home Assistant logs for IPs.
http:
  use_x_forwarded_for: true
  trusted_proxies:
    - 172.17.0.2
    - 172.17.0.3
```

#### Upgrade Home Assistant (via Docker)
```bash
# Stop, update, and run
docker compose down
docker compose pull && docker compose up -d

# Clean up images
sudo docker image prune -a
```