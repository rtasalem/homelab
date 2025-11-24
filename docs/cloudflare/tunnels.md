# Tunnels

Cloudflare tunnels are a free, simple, secure way to expose self-hosted applications. This guide goes through creating and running tunnels via the `cloudflared` CLI. A separate document exists for adding policies on top of self-hosted applications. This guide is heavily based on the YouTube tutorial, [_Cloudflare Tunnel Setup Guide - Self-hosting for EVERYONE_](https://www.youtube.com/watch?v=hrwoKO7LMzk) created by [Raid Owl](https://www.youtube.com/@RaidOwl).

## Install cloudflared

As the homelab runs on Arch Linux, `cloudflared` must be installed via `yay`:

```
yay -S cloudflared-bin
```
For all prompts concerning diffs or build files, select `a` for `[A]ll` (this will initiate cleaning up of old build files). Run `cloudflared --version` to verify the installation was successful.

## Authenticate Cloudflare

The connection to the homelab domain must be authenticated:

```
cloudflared tunnel login
```

The browser should automatically open and direct to the Cloudflare authentication page (if not, copy and paste the provided URL in the terminal output into a new browser window). Once authenticated, select the domain that tunnels will be created on. Successful authorisation is confirmed when the terminal output states the path to the `cert.pem` file. Take note of the path.

## Create a tunnel

Create a tunnel for the chosen domain:

```
cloudflared tunnel create <tunnel-name>
```

Successful tunnel creation is confirmed when the terminal output shows the path to the credentials file for the tunnel itself. Note the name of the credentials file will be the same as the tunnel ID e.g. `<tunnel-ID>.json`. This will likely be stored in the same path as the `cert.pem`.

## Configuration file

In the same directory as where the `cert.pem` and tunnel credentials file is stored, create the config file:

```
touch config.yaml
```

Update the configuration file:

```
tunnel: <tunnel-ID>
credentials-file: /path/to/credentials/file/<tunnel-ID>.json
ingress:
  - hostname: <app-name>.<domain>.com
    service: http://localhost:<port>
  - service: http_status:404
```

Example hostname: `portainer.myhomelab.com`

## Run tunnel

Once all configuration is in place, run the tunnel:

```
cloudflared tunnel run <tunnel-name>
```
