---
modified: 2024-10-07T14:42:14+02:00
---
Cobot URL: [world-of-work.cobot.me](world-of-work.cobot.me)
## Debug

Debug radius with radclient:

```
echo "User-Name = <username>,User-Password = <password>" | radclient -x -s <RADIUS_SERVER:PORT> auth <shared_secret>
```

Had to install the freeradius-client: `sudo apt install -t bullseye-backports freeradius-utis`

```shell
echo "User-Name = gast,User-Password = gast.1234" | radclient -x -s 130.211.107.8:26813 auth vJAcaQiCS6O0yr3Z
Sent Access-Request Id 201 from 0.0.0.0:49831 to 130.211.107.8:26813 length 44
	User-Name = "gast"
	User-Password = "gast.1234"
	Cleartext-Password = "gast.1234"
Received Access-Accept Id 201 from 130.211.107.8:26813 to 92.79.55.46:49831 length 123
	Session-Timeout = 63787
	Class = 0x69726f6e776966693a3461663162313933333037643830376464643832316461353463313731313639
	Chargeable-User-Identity = 0x35303765353238633834643365623535663035363562653865373763386561373532616363636561
	Acct-Interim-Interval = 3600
	Idle-Timeout = 3600
Packet summary:
	Accepted      : 1
	Rejected      : 0
	Lost          : 0
	Passed filter : 1
	Failed filter : 0
```
 
## WLAN-Integration

Tasks:
- [x] WLAN-Integration in Cobot freischalten ✅ 2024-10-07 #baumert 
- [x] User in Cobot backend anlegen #baumert ✅ 2024-10-09
- [x] Ubiquity Radius Client mit Zugangsdaten von "IronWifi" [verknüpfen](https://helpcenter.cobot.me/de/articles/4872927-radius-einrichten) ✅ 2024-10-07 #baumert 
- [x] WLAN neu konfigurieren ✅ 2024-10-09
	- [x] **WPA2 Enterprise / IEEE 802.1X** parallel zu WPA2/3 ? ✅ 2024-10-07 #baumert 
	- [x] neuer Zuschnitt, was passiert mit den alten "WLANs" (ESSIDs)? #baumert ✅ 2024-10-09


## Datev-Integration
- [ ] Integration von Datev  #baumert 

## Dormakaba-Integration
- [ ] Integration von [Dormakaba Exivo](https://dooraccess.apps.cobot.me/dormakaba) #baumert 

## Kalender-Integration
- [ ] Integration von [Google Calendar](https://google-calendar.apps.cobot.me/) #baumert 