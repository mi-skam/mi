---
modified: 2024-10-06T14:47:04+02:00
---
Es ist zwar nicht empfehlenswert WLAN als Hauptnetzwerkdevice für einen Hypervisor zu verwenden, aber wir nutzen es als Übergangslösung bis die Ethernetverbindung steht.

Installation der Pakete (Debian):
```shell
apt update -y
apt install wpasupplicant iw wireless-tools
```

Anzeige des Devices
```shell
ip a s # device name
iw dev # wlan specific infos
ip link set wlps120 up # wlan dev aktivieren
```

Netzwerk-Konfiguration

*/etc/network/interfaces*
```shell
allow-hotplug wlp12s0
iface wlp12s0 inet dhcp
        wpa-ssid YAWLANTUR
        wpa-psk K.EWTH2GQ6uV-wmH3!Dz8U7Y86ueRzGzWh74yAV.
```

