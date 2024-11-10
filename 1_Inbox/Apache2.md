---
created: 2024-08-29 15:15
modified: 2024-09-03T18:49:23+02:00
---

To reload the config of a running Apache process, use the `apachectl` utility
```shell
apachectl configtest # tests the config
apachectl -k graceful # restarts the process
```