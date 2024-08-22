---
Date: 2024-08-20T00:00:00.000+02:00
modified: 2024-08-22T13:05:29+02:00
created: 2024-08-20T13:37:56+02:00
tags:
  - baumert/nextcloud
done: true
---

[[2024-08-20]] 07:11 hat mir [[Sven Baumert|Sven]]  geschrieben, dass er die [cloud.ladenbau-baumert.de](https://cloud.ladenbau-baumert.de/) nicht erreichen kann. 
> [!example|gallery] Svens Screenshots via Whatsapp
> ![[baumert_cloud_1.jpg]]
> ![[baumert_cloud_2.jpg]]
> ![[baumert_cloud_3.jpg]]


[[2024-08-20]] 09:11 bekomme ich die Nachricht von [[Sven Baumert|Sven]], dass [[Chris Schnabel]] sagt, dass es seit der Migration zu diesen Ausfällen kommt 🤮
> [!example|gallery] Svens Screenshots via Whatsapp
> ![[baumert_cloud_4.jpg]]

[[2024-08-20]] 09:13 Nachgestellt, dass es die `mariadb` am 19.8. **22:14:56**aufgrund von `OOM` (out of memory) vom Kernel gestoppt wurde und von Hand am 20.8. **08:38** neugestartet wurde. Der Ram war zu dem Zeitpunkt 99% gefüllt.
> [!example|gallery] Screenshots vom System
> ![[Bildschirmfoto 2024-08-20 um 09.28.01.png]]

[[2024-08-20]] 15:25 hat sich das ganze wiederholt. Jetzt wurde die `php-fpm` Konfiguration angepasst und neugstartet, das System hat jetzt nur eine Ram-Auslastung von `<10%`
> [!example|gallery] Screenshots vom System
> ![[Bildschirmfoto 2024-08-20 um 16.27.44.png]]