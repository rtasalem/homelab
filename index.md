This wiki is for documenting *every single step* taken in setting up my own homelab. There are a couple sections in this wiki that are not strictly to do with homelabbing or self-hosting, but nonetheless are valuable lessons I've learned in the process.

## Contents (A-Z)

[Cloudflare](/docs/cloudflare/README.md)  
[Docker](/docs/docker/README.md)  
[Network](./docs/network/README.md)

## Scripts

To run any of the services listed under this homelab project, [`start`](./start) and [`stop`](./stop) scripts have been configured to start either all or specified services.

### Usage

To start specific services or all services:

```bash
./start cloudflared portainer
./start all
```

To strop specific services or all services:

```bash
./stop cloudflared portainer
./stop portainer -v
./stop all
```
