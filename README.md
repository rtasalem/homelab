# Homelab Wiki

This [wiki](https://homelab.ranasalem.io) is for documenting *every single step* I am taking in setting up my own homelab so that it can be replicated if required. It's worth noting that there are a couple sections in this wiki that are not strictly to do with homelabbing, but nonetheless has been a valuable lesson I've learned in the process.

## Scripts

To run any of the services listed under this homelab project, [`start`](./start) and [`stop`](./stop) scripts have been configured to start either all or specified services.

### Usage

To start or stop all services:
```
./start all
./stop all
```

To start or stop specific services:

```
./start portainer grafana
./stop portainer grafana
```
