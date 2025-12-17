# Homelab Wiki

This [wiki](https://homelab.ranasalem.io) is for documenting *every single step* taken in setting up my own homelab. There are a couple sections in this wiki that are not strictly to do with homelabbing or self-hosting, but nonetheless are valuable lessons I've learned in the process.

## Contents (A-Z)

[Cloudflare](/docs/cloudflare/README.md)  
[Docker](/docs/docker/README.md)  
[Network](./docs/network/README.md)

## Available services (A-Z)

[Bin It!](./compose.bin-it.yaml) - Custom Python application I built to automate email reminders for my bin collection days.  
[Cloudflared](./compose.cloudflared.yaml) - A.k.a. the Cloudflare daemon to support the use of Cloudflare tunnels.  
[Portainer](./compose.portainer.yaml) - GUI for managing container environments, specifically Docker containers.  

## Environment variables

Please use the [`.env.example`](./.env.example) file as a reference for what variables need to be present in the `.env` file (which should be located at the root of the project). 

## Scripts

To run any of the services listed under this homelab project, [`start`](./start) and [`stop`](./stop) scripts have been configured to start either all or specified services.

### Usage

To start specific services or all services:

```bash
./start cloudflared portainer
./start all
```

> Note: Services will start in `detached` (`-d`) mode as monitoring can be done via available services including Portainer or Grafana.

To strop specific services or all services:

```bash
./stop cloudflared portainer
./stop portainer -v
./stop all
```
