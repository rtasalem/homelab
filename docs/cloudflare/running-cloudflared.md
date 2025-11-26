# Running Cloudflared as a self-hosted service using Docker

Cloudflared can be easily spun up as a service by self-hosting using Docker. By running Cloudflared as a service, users eliminate the need to manually start up and monitor their Cloudflare tunnels.

## Establish the Docker network

In order for Cloudflared to properly assign any self-hosted application that also runs in Docker to an existing tunnel, both Cloudflared and the application must exist in the same Docker network. For example, if we want to self-host [Portainer](https://www.portainer.io) on a subdomain e.g. `portainer.mydomain.com` via a Cloudflare tunnel, then the Docker compose file should contain a declared network:

```yaml
services:
  portainer:
    image: portainer/portainer-ce:latest
    container_name: homelab-portainer
    restart: always
    ports:
      - 8000:8000
      - 3000:9000
    volumes:
      - portainer_data:/data
      - /var/run/docker.sock:/var/run/docker.sock
    networks:
      - homelab-net # declare the network to be used for all applications

volumes:
  portainer_data:

networks:
  homelab-net:
    driver: bridge
    name: homelab-net # define the network
```

In the Docker Compose file for the Cloudflared service, we would have the same set up for the Docker network:

```yaml
services:
  cloudflared:
    image: cloudflare/cloudflared:latest
    container_name: homelab-cloudflared
    restart: unless-stopped
    volumes: 
      - ${CLOUDFLARED_PATH}:/etc/cloudflared
    command: tunnel --config /etc/cloudflared/config.yaml run
    networks:
      - homelab-net # declare the network to be used for all applications

networks:
  homelab-net:
    driver: bridge
    name: homelab-net # define the network
```

This is _mandatory_ to enable the Cloudflared container to communicate and reach any application to assign it to a tunnel.

## Docker Compose configuration

Below is the Docker Compose file for running Cloudflared:

```yaml
services:
  cloudflared:
    image: cloudflare/cloudflared:latest
    container_name: homelab-cloudflared
    restart: unless-stopped
    volumes: 
      - ${CLOUDFLARED_PATH}:/etc/cloudflared
    command: tunnel --config /etc/cloudflared/config.yaml run
    networks:
      - homelab-net

networks:
  homelab-net:
    driver: bridge
    name: homelab-net
```

The path of the `.cloudflared` directory on the server (host machine) should be declared in the `.env` file under `CLOUDFLARED_PATH`.

## Updating the tunnel config

Initially the user learns to run Cloudflare tunnels manually where all references to the Cloudflared directory path and the service refer to what's true for the server. Therefore the configuration must be updated to look for the paths and services that run inside the Docker container. When mounting the `CLOUDFLARED_PATH` as a volume inside the container, the following files should be present: `<tunnel-ID>.json`, `config.yaml`, and `cert.pem`.
