---
in: "[[Best-Practices]]"
up: 
related: 
created: 2024-05-31
tags:
  - best-practices
languages: powershell
---
Add this to `$PROFILE`

```powershell
$ProfileRoot = (Split-Path -Parent $MyInvocation.MyCommand.Path)
$env:path += ";$ProfileRoot"
```


---
[[Best-Practices]]