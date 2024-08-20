---
created: 2024-07-29
tags:
---
## Protokoll


- Profil für cloud.baumert-montage.de (ftp) und cloud.ladenbau-bauemert.de (scp) in Cyberduck angelegt
- Maintenance Mode an: `sudo -u www-data /var/www/nextcloud/occ maintenance:mode --on
- Testweise Dateien in Christins Verzeichnis rüberkopiert
	- Berechtigungen korrigiert (http-server läuft mit www-data)
	- Nextcloud File scanner laufen lassen `sudo -u www-data /var/www/nextcloud/occ files:scan --all`
- Dateien müssen komplett heruntergeladen werden, da eine direkte Verbindung von Server zu Server über FTP fehlschlägt (eine Shell gibt es auf der alten Nextcloud-Instanz nicht) --> long transfer times 🥱
- file scanner funktioniert nur wenn der maintenance mode off ist
- Freigaben müssen neu gesetzt werden, dafür habe ich noch zwei Gruppen angelegt *manager* und *mitarbeiter*
- Daten zwischen `sven.baumert` und `cloudadmin` sind inkosistent, da sie teilmigriert und unbenannt wurden, Freigaben werden aktualisiert wenn das behoben wurde
- Passwörter werden nochmal neu vergeben


![[Benutzer neue Nextcloud.docx]]