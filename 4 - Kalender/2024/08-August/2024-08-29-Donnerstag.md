---
tags:
  - daily
created: 2024-08-29 01:07
modified: 2024-08-30 11:07
---
<< [[4 - Kalender/2024/08-August/2024-08-28-Mittwoch|gestern]]  | [[4 - Kalender/2024/08-August/2024-08-30-Freitag|morgen]] >>

# 📋 Tasks
_Backlog: Google [Tasks](https://calendar.google.com/calendar/u/0/r/tasks)_

```dataview
TASK from "4 - Kalender/Tasks"
```

# 📝 Notes

## Meeting mit Gordan

- "Die AFD hat das Ziel 33% zu schaffen, da damit verfassungsändernde Möglichkeiten nicht mehr möglich sind. Sie halten defakto eine Sperr-Minorität."
- Fachliche Reflektion des QM-Prozesses mit [[Phil-Gordon-Zameit]]
- AP GPU Test setup
- outline muss noch neu deployed werden mit besseren Secrets

## AP
- Server installieren mit **GPU**
- 

## Wordpress upload limit

Die Versuche die `php.ini` zu editieren sind alle gescheitert, da die `.htaccess` Vorrang hat. In der `/var/www/.htaccess` habe ich folgende Änderungen vorgenommen:

```shell
# END WordPress
php_value upload_max_filesize 128M
php_value post_max_size 128M
php_value memory_limit 256M
php_value max_execution_time 300
php_value max_input_time 300
```

## WOW Brunch Impulsvortrag

"In zehn Jahren werden nur noch *nachhaltige Marken* erfolgreich sind." Axel Berger (Podcast, Brand Eins)

**Marke**
- Identität und Werte (Emotionen, Assoziationen, Wahrnehmungen)
- Die Produkte und Logos sind noch keine Marke
- Konsistenz: Kommunikation, Produkte, Verhalten 
- Relevanz: Bedürfnisse, Wünsche 
- Transparenz
- Innovation (20%), z. B. Produkte, Leistungen 

---
### Notes last touched today
```dataview
List FROM "" WHERE file.mday = date("2024-08-29") SORT file.mtime asc
```