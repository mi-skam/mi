---
created: 2023-10-02
modified: 2024-09-03T16:42:24+02:00
---
To disable the usage of SMB1 on macOS, you need to setup the following configuaration.

```shell
cat ~/Library/Preferences/nsmb.conf
# Configuration file for foo.bar
  [default]
  smb_neg=smb2_only
```
