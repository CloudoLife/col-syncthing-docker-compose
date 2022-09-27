
col-syncthing-docker-compose is an example to use Docker Compose to run Syncthing with Docker Container.

## Usages

```shell
git clone git@github.com:CloudoLife/col-syncthing-docker-compose.git

cd col-syncthing-docker-compose

# Run Syncthing
docker-compose up
```

## Configuration

### Docker Compose Configuration

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

### Environment Variable Configuration

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
docker-compose stop
```

Down Syncthing.

```shell
docker-compose down
```

## Advanced Usages

See [docker-compose.override.yaml.exmaple](./docker-compose.override.yaml.exmaple) to learn more.
### Mount Host dir

```yaml
# docker-compose.yaml

    volumes:
      - "/:/Docker_Host/"
```

### Use custom network

```shell
docker network create -d bridge bridge-local
```

```yaml
# docker-compose.yaml

# docker network create -d bridge bridge-local
networks:
  default:
    name: bridge-local
    external: true
```

## References

[1] [syncthing/syncthing - Docker Image | Docker Hub - https://hub.docker.com/r/syncthing/syncthing](https://hub.docker.com/r/syncthing/syncthing)

[2] [Syncthing - https://syncthing.net/](https://syncthing.net/)

[3] [Overview | Docker Documentation - https://docs.docker.com/compose/](https://docs.docker.com/compose/)

[4] [Home - Docker - https://www.docker.com/](https://www.docker.com/)