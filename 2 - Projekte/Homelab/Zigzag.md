---
description: Synology NAS 2TB (RAID-0 SSD), 1*8TB external HDD
roles:
  - nas
  - container-host
os: qnap
status: active
created: 2023-08-02
modified: 2024-09-30T15:40:16+02:00
---
## Maintenance

I have a script running (`crontab -l`), that moves daily photos from the Camera Syncthing folder *DCIM* to Plump's  Photo folder.

To alter crontabs you need to do it as su, as the others get kicked out.

```bash fold
# Define source and destination directories
SOURCE_DIR="/share/Sync/DCIM/Camera/"
DEST_DIR="/share/Plumps/Bilder/Fotos/unsortiert/"

# Run rsync with options and redirect output to /dev/null
rsync -vaP "$SOURCE_DIR" "$DEST_DIR" > /dev/null 2>&1

# Check if rsync was successful
if [ $? -eq 0 ]; then
  echo "Rsync completed successfully."
  
  # Remove all files in the source directory
  rm -rf "$SOURCE_DIR"*

  echo "All files in the source directory have been removed."
else
  echo "Rsync encountered an error. Check the logs for details."
fi

```

## Docker

To ease my life, I installed Portainer on the QNAP Nas

```shell
# ssh onto the nas ssh zigzag.villa -l plumps
docker volume create portainer-data

docker run -d -p 11001:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:2.21.1
```

Then you can [log into your portainer UI](http://zigzag.villa:9000/) and create everything you need.

### LogitechMediaServer

For LMS I had to create a network that works with the IPs of the same subnet as the QNAP Nas itself. There is a special driver called `qnet` for that.

Look at the docker compose file, how to assign a static ip using this network.

> [!ERROR] Problems with Spotty plugin
> Without setting the environment variables The spotty plugin for LMS was not running properly. Songs just kept on skipping and  I had `code (425)` issues. 

```yaml fold title:"docker-compose.yml for lms" hl:15-17,28-30 hlalt:6-8
services:
  lms:
    container_name: lms
    image: lmscommunity/logitechmediaserver:9.0.0
    environment:
      - PUID=1001 # Your user ID
      - PGID=100 # Your group ID
      - TZ=Europe/Berlin
    volumes:
      - lms-data:/config:rw
      - /share/CACHEDEV1_DATA/Multimedia/Music:/music:ro
      - /share/CACHEDEV1_DATA/Playlists:/playlist:rw
      - /etc/localtime:/etc/localtime:ro
      - /etc/TZ:/etc/timezone:ro
    networks:
      qnet-static-eth0-1:
        ipv4_address: 192.168.1.10
    ports:
      - 9000:9000/tcp
      - 9090:9090/tcp
      - 3483:3483/tcp
      - 3483:3483/udp
    restart: unless-stopped

volumes:
  lms-data:

networks:
  qnet-static-eth0-1:
    external: true
```

### Syncthing
```yaml fold title:"docker-compose.yml for syncthing"
services:
  syncthing:
    image: lscr.io/linuxserver/syncthing:1.27.12
    hostname: zigzag #optional
    environment:
      - PUID=1002
      - PGID=1000
      - TZ=Etc/UTC
    volumes:
      - /share/Container/syncthing/config:/config
      - /share/Sync:/sync
    ports:
      - 8384:8384
      - 22000:22000/tcp
      - 22000:22000/udp
      - 21027:21027/udp
    restart: unless-stopped
```