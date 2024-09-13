---
summary: 
attendees:
  - "[[Phil-Gordon-Zameit]]"
  - "[[Lutz Thies]]"
tags:
  - meeting
created: 2024-09-06 10:49
"": 
modified: 2024-09-08T12:35:13+02:00
---
## ℹ TOPs
1. nextcloud - fileserver [[Lutz Thies]] noch weiter dokumentieren 

##  📝 Notes

## Docker backup

portainer volume mit docker-compose
docker image inspect für Metadaten

backup Schritt

```shell
`# Define the name of your volume, on macOS/Linux VOLUME="replace with the name of your volume"`

# backup
`docker run --rm -v "${VOLUME}:/data" -v "${PWD}:/backup-dir" ubuntu tar cvzf /backup-dir/backup.tar.gz /data`

# Restore
docker run --rm -v "${VOLUME}:/data" -v "${PWD}:/backup-dir" ubuntu bash -c "rm -rf /data/{*,.*}; cd /data && tar xvzf /backup-dir/backup.tar.gz --strip 1"`
```

