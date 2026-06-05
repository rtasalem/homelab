# Creating a new admin

After tearing down the Navidrome Docker container with the `-v` flag:

```
docker compose -f compose.navidrome.yaml down -v
```

It is reasonable to expect that after starting up the container, you would be met with the Create Admin User page. However this may not be the case if the `navidrome.db` file is still present inside the `data` directory (one of the volume needed for Navidrome). If you wish to completely tear down the Navidrome container and then spin it back up to start the journey from the very beginning where you create an admin user, delete the `navidrome.db` file, _then_ start the container.
