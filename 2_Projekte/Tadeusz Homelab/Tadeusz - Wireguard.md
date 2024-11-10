---
modified: 2024-10-07T06:36:10+02:00
---

Um Wireguard nutzen zu können, brauchen wir eine[[Tadeusz - DDNS| dynamische Adresse]].

Installation in `System > Paketverwaltung`:
- `luci-proto-wireguard`
- `curl`
- `qrencode`
- `knot-host`

Reboot damit wir das Wireguard-Interface sehen können.

Interface hinzufügen: Now, login to the LuCI web interface and go to **Network** > **Interfaces**. Click on **Add new interface...**, type `wg0` (or whatever you prefer) in the name field and choose **WireGuard VPN** as the protocol. Click on **Create interface**.

![[Pasted image 20241007062656.png]]

Edit the newly created interface and click on **Generate new keypair**. This will generate a private and public key for the VPN server.

Also set the **Listen port** to **51820** (or whatever you prefer).

For the **IP Addresses** field, enter the subnet you want to use for the VPN clients. For example, `192.168.100.1/24`.

![[Pasted image 20241007062754.png]]



Firewall-Zone hinzufügen: Ich habe eine Zone mit dem Namen `vpn` angelegt.

Bei `Covered Networks` muss man das Wireguard Interface anlegen `wg0`.

Allow forwards so wie im Screenshot.

![[Pasted image 20241007062917.png]]


![[Pasted image 20241007062942.png]]

Nachdem man die Zone angelegt hat, nochmal zurück zum Netzwerk Interface und das Interface von `lan` nach `vpn` bewegen

![[Pasted image 20241007063207.png]]

Peers anlegen:

In Interfaces > wg0 > Peers auf `Add Peer` klicken

![[Pasted image 20241007063311.png]]

Folgendes eintragen:

- Name für das Profil in `Description` eintragen.
- Auf `Generate new key pair` um Schlüssel für den peer zu erzeugen
- in `Allowed IPs` eine ungenutzte IP aus dem VPN IP Bereich wählen, z.B. 192.168.100.10/32
- Persistent Keep Alive auf 25 setzen

und dann mit `Generate configuration` eine Konfig / QRCode erzeugen.

![[Pasted image 20241007063623.png]]