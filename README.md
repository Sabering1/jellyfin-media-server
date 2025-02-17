# Media Management Docker Compose

This Docker Compose configuration bundles Jellyfin, Jellyseerr, Radarr, Sonarr, Prowlarr, and qBittorrent into a single deployment for seamless media management, downloading, and streaming.

## Setup Instructions

Before running the containers, make sure to update the following placeholders in the `docker-compose.yml` file:

- **Network settings**
  - Update `JELLYFIN_PublishedServerUrl` with your actual local server IP (e.g., `http://192.168.1.100`).
  
- **Volume paths**
  - Ensure that `/docker/` paths match your actual file system structure.
  - If your media is stored elsewhere, adjust the `/docker/data` volume accordingly.
  
- **User and group IDs**
  - Modify `PUID` and `PGID` to match your system user (default is `1000:1000`).
  
- **Ports**
  - Change the exposed ports if they conflict with other services on your system.

## Running the Stack


Download the docker-compose.yml file, and edit it with nano or vim to change the defaults

```sh
curl -o docker-compose.yml https://raw.githubusercontent.com/Sabering1/jellyfin-media-server/main/docker-compose.yml
```


Once you have modified the necessary values, deploy the stack with:

```sh
docker-compose up -d
```

To stop and remove the containers:

```sh
docker-compose down
```

## Notes
- if you cant access qbittorrent with default password and username add this line under [Preferences], in the config file, for setting the default password manually to: adminadmin
```
WebUI\Password_PBKDF2="@ByteArray(ARQ77eY1NUZaQsuDHbIMCA==:0WMRkYTUWVT9wVvdDtHAjU9b3b7uB8NR1Gur2hmQCvCDpm39Q+PsJRJPaCU51dEiz+dTzh8qbPsL8WkFljQYFQ==)"
```
- Ensure that you have the required directories created before running the containers, if not docker compose will probably create them for you.
- You may need to adjust firewall settings if running on a remote machine.
- If using a reverse proxy, update the configurations accordingly.

## License

This project is licensed under the AGPL License. See the `LICENSE` file for details.

