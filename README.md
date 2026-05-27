# Homelab Wiki

This [wiki](https://homelab.ranasalem.io) is for documenting *every single step* taken in setting up my own homelab. There are a couple sections in this wiki that are not strictly to do with homelabbing or self-hosting, but nonetheless are valuable lessons I've learned in the process.

## Contents (A-Z)

[Cloudflare](/docs/cloudflare/README.md)  
[Docker](/docs/docker/README.md)  
[Navidrome](/docs/navidrome/README.md)  
[Network](./docs/network/README.md)

## Arch Linux

The primary hardware (at the time of writing) used to host and run this homelab is a [Lenovo ThinkPad T480](https://www.lenovo.com/gb/outletgb/en/p/laptops/thinkpad/thinkpadt/thinkpad-t480/22tp2tt4800?orgRef=https%253A%252F%252Fwww.google.com%252F&utm_content=Thinkpad&utm_term=Laptops&utm_source=Google&utm_campaign=G-UK-SEM-COMMERCIAL-PUBLIC-LF-Search-Commercial-Laptops-ThinkPad&gclsrc=aw.ds&gad_source=1&gad_campaignid=12650344200&gclid=CjwKCAjwrNrQBhBjEiwAoR4VO_ADL6m-9zSCaKfInPE8aWdtH8rOQzhoxanCG_Tap1ZMXZscVoA59RoCdGQQAvD_BwE). Arch Linux is the OS of choice. See my [dotfiles](https://github.com/rtasalem/dotfiles/blob/main/arch/README.md) for full details on my Arch config.

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
