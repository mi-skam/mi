---
description:
  - TP-Link Router, Access Point, OpenWRT
roles:
  - router, ap
os: openwrt
ip: 192.168.178.1
status: active
created:
  - - 2023-08-02
tags: []
modified: 2024-09-12T09:26:07+02:00
---
## Firmware upgrade

To update the firmware via cli, you need to setup the openssh server (enable it, configure ssh pub keys)

1. Get the [sysupgrade image for Archer C2600](https://firmware-selector.openwrt.org/?version=23.05.4&target=ipq806x%2Fgeneric&id=tplink_c2600)
2. Download it to `/tmp`
3. Upgrade the firmware `sysupgrade -v /tmp/<firmware>`
 
## Log

villa's dsl router and ap
common

0029846855485510108157660001@t-online.de
77163167


```shell

opkg update
opkg install mailsend # dependency von /root/update-notification
cat > /root/update-notification <<EOF
#!/bin/sh

opkg update 
opkg list-upgradable > updates.txt

if [ -s updates.txt ] 
then 
   mailsend -smtp smtp.gmail.com -port 465 -t maksim@miskam.xyz -f maksim+it@miskam.xyz -sub 'Common: OpenWrt-Updates' -ssl -auth -user maksim@miskam.xyz -pass "tsbjdjyqgiiofvwg" -mime-type "text/plain" -msg-body "updates.txt" 
fi 
rm updates.txt
EOF
chmod +x /root/update-notification

```

### Cron
Im Webinterface `System -> Scheduled Tasks` kann das Skript anschließend zu einem beliebigen Zeitpunkt ausgeführt werden:

```crontab
# 6 Uhr  
# Update list of available packages | Send notification mail
45 06 * * * /root/update-notification
```

### ~/.profile
```shell
#!/bin/sh

opkgInstalled="$(opkg list-installed 2> /dev/null | wc -l)" #silencing error output
opkgUpgradable="$(opkg list-upgradable 2> /dev/null | wc -l)" #silencing error output

echo "$opkgInstalled packages are installed." && echo "$opkgUpgradable packages can be upgraded." && echo
echo "Upgrade commands:"
echo "List available updates: opkg list-upgradable"
echo "Upgrade package: upgrade <PACKAGE>"
echo "Upgrade all packages: opkg list-upgradable | cut -f 1 -d ' ' | xargs opkg upgrade" && echo
```