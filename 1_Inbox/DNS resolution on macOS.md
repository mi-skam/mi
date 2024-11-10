---
created: 2024-08-28T07:11:14+02:00
modified: 2024-08-28T07:16:54+02:00
---

To change the entries in macos you need to edit `/etc/hosts` which is a link to `/etc/private/hosts`

> [!code]+ */etc/hosts*
> ```shell
> 127.0.0.1 localhost
>127.0.0.1 local.dev
> ```

## Flush the cache

```shell
sudo dscacheutil -flushcache # not sure if actually needed
sudo killall -HUP mDNSResponder
```
## Block domains system wide

We block `example.com` for _ipv4_ and _ipv6_ in this example:

> [!code]+ */etc/hosts*
> ```shell
>127.0.0.1 
>127.0.0.1 example.com
>::1 example.com
> ```
