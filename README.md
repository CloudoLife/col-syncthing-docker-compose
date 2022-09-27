
col-syncthing-docker-compose is an example to use Docker Compose to run Syncthing with Docker Container.

## Usages

```shell
git clone git@github.com:CloudoLife/col-syncthing-docker-compose.git

cd col-syncthing-docker-compose

cp .env.example .env

# Run Syncthing
docker-compose up
```

## Configuration

```yaml
# docker-compose.yaml

version: '3'

services:

  syncthing:
    image: syncthing/syncthing
    # privileged: true
    restart: always
    ports:
      - "${LISTENER_IP}:${GUI_PORT}:8384"
      - "${SYNC_PORT}:22000"
      - "${DISCOVERY_PORT}:21027/udp"
    volumes:
      - "./runtime/syncthing/var/syncthing:/var/syncthing"
```

```ini
# .env


PUID=1000
PGID=1000

LISTENER_IP=127.0.0.1
# LISTENER_IP=0.0.0.0

# Ports
GUI_PORT=8443
SYNC_PORT=22000
DISCOVERY_PORT=21027

# Time Zone
TZ=Europe/London
```

## Run and Down

Run Syncthing.

```shell
docker-compose up
```

Stop Syncthing.

```shell
docker-compose down
```