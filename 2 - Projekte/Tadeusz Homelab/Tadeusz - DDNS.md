---
modified: 2024-10-07T06:23:43+02:00
---
Installation:

- `luci-app-ddns`
- `ddns-scripts` 
- `curl`
- `knot-host`


## grafisch (teilweise broken)
Dann in folgendes Menü gehen: 

![[Pasted image 20241006145728.png]]


## cli 
DNS-Howto für **ipv64**: https://ipv64.net/dyndns_helper#openwrt-dyndns-howto
[OpenWRT DDNS Documentation](https://openwrt.org/docs/guide-user/services/ddns/client?s[]=ddns)

```shell
$ ssh root@turris.local

root@turris:~# vi /etc/config/ddns

config ddns 'global'
        option ddns_dateformat '%F %R'
        option ddns_loglines '250'
        option ddns_rundir '/var/run/ddns'
        option ddns_logdir '/var/log/ddns'

config service 'myddns_ipv4'
        option interface 'wan'
        option ip_source 'network'
        option ip_network 'wan'
        option use_ipv6 '0'
        option force_unit 'minutes'
        option check_unit 'minutes'
        option domain 'tadda-lab.ipv64.net'
        option username 'none'
        option retry_unit 'seconds'
        option enabled '1'
        option use_syslog '2'
        option lookup_host 'tadda-lab.ipv64.net'
        option update_url 'https://ipv64.net/update.php?domain=[DOMAIN]&key=[PASSWORD]&ip=[IP]'
        option password 'jVc3gE0wI8kZpPXiA7hRTL6fMBSJqY1H'

config service 'myddns_ipv6'
        option interface 'wan6'
        option ip_source 'network'
        option ip_network 'wan6'
        option use_ipv6 '1'
        option force_unit 'minutes'
        option check_unit 'minutes'
        option domain 'tadda-lab.ipv64.net'
        option username 'none'
        option retry_unit 'seconds'
        option enabled '1'
        option use_syslog '2'
        option lookup_host 'tadda-lab.ipv64.net'
        option update_url 'https://ipv64.net/update.php?domain=[DOMAIN]&key=[PASSWORD]&ip=[IP]'
        option password 'jVc3gE0wI8kZpPXiA7hRTL6fMBSJqY1H'

uci commit
/etc/init.d/ddns restart
```