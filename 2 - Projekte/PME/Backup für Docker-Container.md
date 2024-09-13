---
modified: 2024-09-06T16:00:07+02:00
---
https://www.augmentedmind.de/2023/08/20/backup-docker-volumes/
## Anforderungen

- backup-share mounten: \\zameit.intra\Backup , user: svc_backup
- data-volume in Archiv exportieren
- bei db-containern container beenden und nach dem backup wieder starten
- docker-compose file bekommen und mit dazu backuen
- beenden